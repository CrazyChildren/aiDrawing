# 使用不同模型

由于AI模型是从训练集中“学习”数据样本特征，所以不同模型因为数据集的不同会学到不同的风格、质量等特征。

现在市面上会有很多不同模型供人使用，当然这里也有一些细节需要我们注意

## 需要注意的细节

### 支持的图片分辨率是多少

有的模型是在512x512的训练的，所以对512x512图片支持最好，有的是在768x768上训练的，所以对这个像素比较亲和，在使用模型前需要先了解最适合这个模型的分辨率是多少

### 支持的图片尺寸比例是多少

有的模型在训练时使用了暴力裁切的方法将大的图片缩放到512x512的分辨率上，这容易导致只适合512x512这样的正方形图片，如果改成了长方形的，容易出现一部分（特别是头和腿）被裁切掉的情况。当然有的模型在训练时采用了如[Aspect Ratio Bucketing](https://z28pynubvc.feishu.cn/wiki/wikcnwE9Ma5JVIUOgOei9a9CUVc) 之类的技术，在长方形图片上也能生成完整的内容

所以在使用模型时，也要注意这个模型对长方形图片的支持如何

### 模型版权信息

现在的模型通常都附带着一个版权信息，标识这个模型及其后续衍生模型的版权，比如现在所有的模型都是从StabilityAI基础模型上衍生出来的，而StabilityAI的模型采用了[OpenRAIL++-M License](https://www.ykilcher.com/license)，**允许免费使用，也允许商用，**但是dreamlike这个模型就**不允许私自商用**

所以在下载模型时需要先看清楚模型版权信息

## 怎么使用不同模型

### 下载模型

首先可以去civitai.com或者[Models - Hugging Face](https://huggingface.co/models)(这里面只有部分是webui可用模型)查看他人上传的模型

比如打开civitai，我们需要选择checkpoint类型的模型，可以使用筛选功能查看这类型模型

{% hint style="info" %}
civitai网站含有18禁信息，未登录情况下会过滤NSFW内容，登录态下默认模糊处理，未满18岁用户请勿使用，同时此网站可能包含其他不符合法律法规的内容，请谨慎访问！任何因此导致问题与本教程无关！
{% endhint %}

![](<../.gitbook/assets/image (9).png>)

点击进入模型详情页，可以查看用这个模型的版权信息、提示信息以及别人的示例图片。这里我们点击右边的下载来下载模型，可以看到一个模型通常在3\~7GB左右，还是很大的（如果是云端部署，也可以右键下载链接在终端里用wget/curl等命令下载）。

![](<../.gitbook/assets/image (2).png>)

{% hint style="info" %}
有的模型有特性prompt和尺寸要求
{% endhint %}

### 加载模型

1. 将下载好的模型，通常是.ckpt和.safetensor结尾的文件放到Stable Diffusion WebUI项目的`models/Stable-diffusion`路径下（云端部署可以直接用wget/curl命令下载到此路径里）

![](<../.gitbook/assets/image (10).png>)



2. 在界面上刷新模型列表或者重启 Stable Diffusion Web UI

![](<../.gitbook/assets/image (4).png>)

3. 选择新的模型进行使用

![](<../.gitbook/assets/image (11).png>)

4. 开始创作炫酷的图片吧！

## 模型文件里包含哪些内容

一个分享的模型文件可能只包含Unet模块，也可能包含了VAE和其他组件，所以使用这部分模型会自动更新使用的VAE

## 模型不同名字都有什么含义

有的模型名字中间有Fp32，有的是Fp16，有的带有pruned等等，现在就来说说这些名字含义是什么:

* Fp32：意味着模型使用32位浮点数(float point)储存值，是模型的原始保存值
* Fp16：意味模型用16位浮点数存，相对于Fp32更小更快，但是无法用于CPU，因为有的半浮点精度运算在CPU上不支持。通常为了更快的运算，在GPU上我们也会将Fp32转换成Fp16，这个可以在设置里配置。
* pruned：意味对模型参数进行了修剪，以达到更快的运行速度（也就是丢了一些参数），感兴趣的参考：[pruning-in-deep-learning-models](https://medium.com/@souvik.paul01/pruning-in-deep-learning-models-1067a19acd89)
* ema：ema(Exponential Moving Average指数移动均值)是一个技术用来抵抗波动以得到更好的结果，比如小明多次最后一次考试考砸了，这不能反映他的水平，取多次平均才能更好地表达他水平。感兴趣的参考：[What is EMA?](https://www.investopedia.com/terms/e/ema.asp)
* .ckpt和.safetensor：.ckpt会把网络结构一起保存下来，如果有人在其中加入了病毒代码，也会直接运行！而safetensor只带了网络模型的参数值，而不带结构，所以加载比.ckpt安全

## StabilityAI基础模型区别

### SDv1和SDv2区别

SDv2更新了CLIP模型到OpenAI公司开源的更大的、参数更多的OpenCLIP模型，可以更好地理解人类语言，所以效果比SDv1好。而且SDv2移除了NSFW检测器，数据集更多，效果也更好一点，但是相对的可以生成NSFW内容，请各位不要用来生成违法内容！

### Inpainting, UnCLIP, upscaler, depth模型区别

这几个都是StabilityAI官方推出的在基础模型上微调得到的模型，分别在不同领域有更好的表现

* Inpainting: 在蒙版局部重绘时融合效果更好
* UnCLIP: 23年3月24发布的新模型，使用了类似DALLE2的CLIP算法，能够实现图片变种，得到更多可能性，在[Stable Diffusion reimagine](https://clipdrop.co/stable-diffusion-reimagine)这里可以尝试demo
  * ![](<../.gitbook/assets/image (8).png>)
*   upscaler：专门用来提升精度的超分模型，可以提升x4精度

    ![](<../.gitbook/assets/image (12).png>)
* depth：类似controlNet的深度控制
  * ![](<../.gitbook/assets/image (5).png>)

## 接下来

可以了解更多技术使用如：[使用插件](https://z28pynubvc.feishu.cn/wiki/wikcnqBdyaUblEPDc9dcreFMaZH)[使用lora](https://z28pynubvc.feishu.cn/wiki/wikcnQswCAJG85SDltwOXWRuVYb)[使用ControlNet](https://z28pynubvc.feishu.cn/wiki/wikcndXUjEUkWJvEOWQ8aQeUwxQ)[使用cutoff](https://z28pynubvc.feishu.cn/wiki/wikcn0R1teu7iP5sJlszrvnIFVd)
