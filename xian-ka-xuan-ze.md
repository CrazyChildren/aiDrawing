# 显卡选择

深度学习、游戏渲染都需要大量运算，越好的显卡运算速度越快，出图就越快。这篇文章就来介绍下怎么选择显卡

## GPU是什么

GPU全称是_Graphics processing unit_图形计算单元，是专门为了加速浮点计算而设计的。它在底层硬件上就针对计算提供了优化，所以单纯计算操作相比CPU快上许多，也就是说GPU是为了计算加减乘除这些运算而生的。

在硬件上就进行优化的操作很常见，效果也很好。比如Mac的M系列芯片在硬件上专门针对编码解码器做了优化，所以剪视频时候会快许多。

## 与CPU的区别

CPU主要被设计于多核多线程的调度任务，所以可以良好掌控多个任务并发运行，而不是专门用来计算加减乘除的，所以我们的Windows、Mac系统都运行在CPU里。

虽然CPU也有针对运算优化，如 Intel® OpenMP and Intel® Extension for PyTorch\*这些软件就是用来加速深度学习运算的，但是效率上还是不如GPU直接在硬件里优化

所以在Mac上或者在有显卡的机器上直接用CPU运行AI绘图速度出一张需要的时间就久许多。

{% hint style="info" %}
苹果的M系列芯片里是有集成显卡的，所以可以利用Pytorch MPS加速的，相比单纯cpu运行会快2倍左右
{% endhint %}

## 显卡型号、参数怎么看

显卡和手机一样有很多品牌、经销商、型号。

### 参数

显卡最重要的参数有两个

* 算力
* 内存大小

#### 算力

算力是衡量运算速度的参数，算力越高运算越快，如下左图就是各个芯片算力天梯图，越高算力越大。右图是具体算力对比。可以从右图看到4090（100）比3080（54）高了一倍左右，这意味着如果3080要画4s跑一张图，4090只需要2s左右。

![](https://z28pynubvc.feishu.cn/space/api/box/stream/download/asynccode/?code=NWE5MjEyZjFlNGYzMzM0ZmNjMDcyMDg2ZmE2ZjRiYjVfV3hXbVdKUFJiT3ZLYUxsN3RvR0haSERPQUJPMFdqdWVfVG9rZW46UFFHYmJqSnNnb1d3NkZ4MEJmMmNFV3Z2bnhnXzE2ODM2MTkxMTE6MTY4MzYyMjcxMV9WNA)![](https://z28pynubvc.feishu.cn/space/api/box/stream/download/asynccode/?code=MjgwN2JmN2UzOTk2MWViNzNjMWQ2Y2FmOWEwNjAyYWJfYVZaY25kNnRTVm9TajhKV250Y1hrcGlNcjZ4aHRvWjhfVG9rZW46QUI3N2JFVEdDb0pVazF4UzU5amNndkoybnRYXzE2ODM2MTkxMTE6MTY4MzYyMjcxMV9WNA)

#### 内存大小（显存）

内存大小（或称为显存）则是和电脑内存一个意思，就能能存的东西有多少。在进行运算时，需要将模型加载进显卡的内存里，然后才能计算。

如果内存不够大，可以采取运行时不断加载需要的部分，但是这样速度**就会下降许多**，或者直接无法运行。所以选择显卡时尽量选择大内存显卡。

通常来说运行stable diffusion webui只需要4GB内存即可运行（12GB以下速度都会有损失，内存越小损失越大），但是如果需要训练Lora，则至少需要8GB的内存

### 品牌

现在主流的显卡品牌有两个：英伟达NVIDIA和ATI（被AMD收购），所以分别称为N卡和A卡。因为英伟达多年来一直运营着显卡驱动cuda，所以深度学习对N卡支持都比较好，一般推荐购买N卡。这里的型号也以N卡为例。

### 型号

显卡的型号标识着显卡的能力，比如`NVIDIA GeForce RTX 3080Ti 12G`其中

* `NVIDIA`表示这张显卡是英伟达品牌，是N卡
* `GeForce`系列表示这是张消费级显卡，此外还有`Tesla`系列就是专用级显卡
* `RTX`表示支持光追(Ray Tracing)，除此外还有`GTX`。`RTX`系列显卡比`GTX`更晚面世，所以新显卡都是`RTX`系列，这两个可以理解为升级了。
* `3080`是显卡的真正型号，`30`表示这是30系显卡，这个数字表示是第几代显卡，比如之前的显卡就是`9xx, 10xx, 20xx`，这个数字相当于iphone14中的14
  * &#x20; 在每一代显卡中都有不同级别40/50/60/70/80/90，`60`表示甜品，`80`表示专业，`90`表示极致，相当于iphone, pro, max这样的分级区别
* 3080后面的`Ti`表示加强版，是在3080基础上增强了性能
* `12G`表示这张显卡内存有12GB大小，一个型号的显卡可能有两个内存大小的版本，比如3060就有8GB和12GB两个版本，就行iphone可以选不同内存。但是通常来说一个型号的显卡只有一个内存大小可选，像3060这样有多个可选的比较少。市面上也有一些魔改版本内存，如2080Ti 22G，但是这种魔改版本可能有很多坑，不推荐购买。

前面说了我们主要关心的是显卡的`算力`和`内存`大小，所以在型号里主要关注`3080Ti`和`12G`这两个参数，3080Ti决定了算力，12G决定了内存大小。在选择显卡时主要就是根据型号购买适合的算力和内存即可。

{% hint style="info" %}
不是新一版的显卡算力一定更强，比如2080的算力就比3060的强。但是通常来说，同级别的显卡，新一代都比旧一代强，如2080和3080的对比。但是更高的算力通常需要更大的功率，也更费电，而且电源可能不兼容，比如3060这种甜品级显卡只要400W额定功率的电源，但是3080这种专业级显卡需要额定功率至少500W。
{% endhint %}

### 经销商是什么

就像电脑市场里，Intel负责生产芯片，但是不直接组装成电脑销售，这时就有戴尔、华为、苹果、联想等组装厂会采购合适的组件，然后调教成最合适的状态出售

显卡也一样，不同经销商用料（如散热装置）和调教都不一样，所以最后的性能发挥等也不相同，通常来说购买华硕/ASUS、影驰、七彩虹/Colorful、技嘉/GIGABYTE、微星这些大牌的即可

### 怎么挑选适合自己的显卡

除了算力和内存，对于我们购买者来说，最重要的就是价格了。显卡只有最合适，没有最完美。

如果你是不缺钱的，那尽管上4090，当然大部分用户都需要在一定的价格区间里选择最适合自己的显卡

如果把价格当成横轴，算力当成纵轴，那么就可以画出价格 vs 算力图表，并依据此挑选预算内的显卡，比如下图就是23年5月二手显卡价格-算力图，可以发现3050这张卡在1100\~1300价格区间里算力完全不行，性价比极低。同样的2080Ti在差不多价格时算力甚至比3060Ti还要好。

所以好好利用下图可以很好地挑选显卡，这张图片也是从 [【4K】二手显卡选购指南，2023/5月 (价格篇)](https://b23.tv/kpu1a1W)这个视频中截取出来的，但这是二手显卡的价格-算力对比图，推荐大家还是购买全新显卡。

<figure><img src="https://z28pynubvc.feishu.cn/space/api/box/stream/download/asynccode/?code=YTE0ZTEyMTBhNGY3NTEzNjk5NzEwYThjOTg1MjgyMTFfVUE1YkFxSjltYzZDTEQyRzc5YUdneTkxQ3lHMlFrc1JfVG9rZW46WDZyQWJWR01Hb1V6TjV4Sms4cmNZaTZabnZkXzE2ODM2MTkxMTE6MTY4MzYyMjcxMV9WNA" alt=""><figcaption></figcaption></figure>

如果需要本文来了解显卡，那么不推荐购买二手显卡，二手显卡经过虚拟货币狂潮后水很深，小白别轻易碰。

## 推荐显卡

20系显卡推荐2080及以上

30系显卡推荐3060及以上，其中3060 12G如果你有训练需求，预算又不够高，是个不错选择

40系显卡推荐4060及以上
