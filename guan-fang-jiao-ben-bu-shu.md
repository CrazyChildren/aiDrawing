# 官方脚本部署

而Mac等平台需要用[官方提供的一键安装脚本](https://link.zhihu.com/?target=https%3A//github.com/AUTOMATIC1111/stable-diffusion-webui)，当然在此之前还需要先安装python和git两个软件包，这个方法也适用于windows平台。

#### 安装python3.10.6 <a href="#h_624368619_2" id="h_624368619_2"></a>

python是一个脚本编程语言，AI技术大都是在这上面编写的，所以我们需要先下载这个软件，并且记住，版本之间可能不兼容，请下载具体的3.10.6版本，下载这类软件的方法都一样，在搜索引擎上直接搜这个软件名，进官方下载页面即可。

![](https://z28pynubvc.feishu.cn/space/api/box/stream/download/asynccode/?code=MDFhOTc0NmJiMzM4YzM3ZGM4NDFhMWFmNzIwZjc1MWRfb1ZYNURkUXRDSXNZelI0RzVuSE5CVHhxcHZHeGpoZnBfVG9rZW46WU1mS2J1aFBGb2R6YjV4TzZHRWNKYmhXbktlXzE2ODM2MTg1MjA6MTY4MzYyMjEyMF9WNA)![](https://z28pynubvc.feishu.cn/space/api/box/stream/download/asynccode/?code=ZTM2OWViMjNjZDQ5YTI3OGZlNjA4NzI4MjQxYjI5NmVfRHJ3TXFXZVVZb1U1VXhmR2txT0Q1ME83NTV4UnpsTndfVG9rZW46T3ZxUWJwOThmb3RIVWZ4V3hDdmNueDR4bmRkXzE2ODM2MTg1MjA6MTY4MzYyMjEyMF9WNA)

比如python，第一个结果就是官方的，打开后拉到页面最下面file，下载自己平台的文件即可，需要注意mac和windows都有版本要求，我把要求和安装包都放下面了。windows平台最好下64位的installer，当然你的CPU架构需要是AMD64的，而不能是ARM的芯片。

| 系统      | 安装包             | 要求                          |
| ------- | --------------- | --------------------------- |
| Mac     | 暂时无法在飞书文档外展示此内容 | macOS版本号不能太低                |
| Windows | 暂时无法在飞书文档外展示此内容 | win10以上，只能用AMD64架构芯片，ARM不支持 |

点击安装包，接下来就是一路确定，然后安装就行，windows系统的记得把**python加入环境变量勾打上**

![](broken-reference)

如果安装成功，打开终端（windows打开CMD或者powershell也可以），输入

```
python --version
```

出现版本信息就代表安装成功，如果提示command not found就表示安装失败

![](https://z28pynubvc.feishu.cn/space/api/box/stream/download/asynccode/?code=NGNjMDNiZDJiZmQ2MWVjMGFmMjBhNTBkNTExNjliYWZfTzlSeW1yWjZKbFVveXpDckY2QWhDMGV2QTNsUExsNXdfVG9rZW46UHJHQWJuREhubzhLakh4d0hNMmNFcnJ5bmNnXzE2ODM2MTg2Njg6MTY4MzYyMjI2OF9WNA)

#### 2. 安装git <a href="#h_624368619_3" id="h_624368619_3"></a>

git是一个代码版本控制工具，也可以用来从网上下载代码，用git就能让你的软件保持最新并且方便下载其他插件。安装方法和前面类似，去官网下载安装包即可。

![](https://z28pynubvc.feishu.cn/space/api/box/stream/download/asynccode/?code=N2I3YjkyY2MxZjFmNWMxNjc3NGNjMDVhMjkwNzdmY2JfYkg5N0hkVXpVNVB5ZDRuaUVFTnZWdjhZcWNxdGRsUzhfVG9rZW46THpvdWJncklHb3hOTWh4Sk5oNGNkcDRJbmdjXzE2ODM2MTg2ODU6MTY4MzYyMjI4NV9WNA)![](https://z28pynubvc.feishu.cn/space/api/box/stream/download/asynccode/?code=Yzg4YjBjOTI5YzdkOTE2ZGYzZGI3NzQ0NjM4YTEyNDVfR1NTYXRXR2QxRWRlTE9lS1ozWURURTNPVzZXNzdTdWhfVG9rZW46UFV3cGJnZE5Cb3ZqM3F4anBabWNocFJwbkxjXzE2ODM2MTg2ODU6MTY4MzYyMjI4NV9WNA)![](https://z28pynubvc.feishu.cn/space/api/box/stream/download/asynccode/?code=YWUwOTE0OWRhM2U0ODZiNTRkYTFjNTNmZDlhMDczM2JfOHVSZGxVVTNiVmpWdE9aR3JvUjc5ckd4UHhPUEk0MzJfVG9rZW46TmxVdmIyVWVpb1Uzb054RzFUQWNVN0gyblh5XzE2ODM2MTg2ODU6MTY4MzYyMjI4NV9WNA)![](https://z28pynubvc.feishu.cn/space/api/box/stream/download/asynccode/?code=NDk3MWExMGQwMmY2NzcwYjdmMGVhYWY5N2U1Zjg0ZGZfQm1iYWo2bjhGZ3o1R1V5OWRQR3BnckpscTZGRmJxODNfVG9rZW46RlJHeWI2dTJpb2M4dWl4M2E5d2NiVDBwbkJmXzE2ODM2MTg2ODU6MTY4MzYyMjI4NV9WNA)

macOS用户如果安装了homebrew还可以直接用命令安装：

```
brew install git
```

| 系统      | 安装包             | 备注                 |
| ------- | --------------- | ------------------ |
| Mac     | 暂时无法在飞书文档外展示此内容 | mac用户推荐用homebrew安装 |
| Windows | 暂时无法在飞书文档外展示此内容 |                    |

和python一样，在终端输入命令检测安装，如果出现版本说明安装成功：

```
git --verison
```

安装完成后还需要设置一下git的账户名信息，这里把下面双引号里的替换成你的姓名和邮箱就行（一行一次执行,双引号要保留）

```
git config --global user.name "xxx" 
git config --global user.email "xxx@xxx.com"
```

#### 3. 启动代理（如果你有） <a href="#h_624368619_4" id="h_624368619_4"></a>

git和python的安装工具pip都要单独设置代理或者换源，这部分可以先跳过，如果后面下载东西网速很慢再回来弄也可以。

#### 4. 下载Stable Diffusion webui软件包 <a href="#h_624368619_5" id="h_624368619_5"></a>

先把终端工作目录切换到你想安装软件包的父文件夹，输入下面代码安装：

```
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git
```

1. 运行启动脚本

* windows用户直接在stable-diffusion-webui文件夹里双击`webui-user.bat`文件运行即可
* mac用户先在终端里将工作路径切换到stable-diffusion-webui文件夹里，然后先后执行下面两个命令（一行一次执行）：

```
source webui-macos-env.sh sh webui.sh
```

启动脚本就会自动下载其他依赖，然后开始运行，最后点击本地运行链接就能打开网页享受绘图啦\~

> 运行过程中不能关闭终端，否则程序会停止
