# colab部署

{% hint style="info" %}
colab需要代理使用，并且如果长时间没使用会自动中断，且每日有限额点击[Stable diffusion webui](https://colab.research.google.com/drive/1lSXd7Z3ElxNgmQVfwRUqhawiWMqTjWXr#scrollTo=kKQcBysS2tQo)打开colab页面，如果你没有google账户，需要注册一个。接着完成如下操作:
{% endhint %}

1. 点击 代码执行程序 -> 更改运行时类型 -> GPU -> 保存

![](https://z28pynubvc.feishu.cn/space/api/box/stream/download/asynccode/?code=NTkyNThjMTc1MzBhZTQzMjhkYjFjYzAzM2E5MDY0NjVfcEVnWHJYeWVMSHcxbXk2ZjVpd09adXRHT3I4bVdJY0ZfVG9rZW46R2RVTGJxb1Nvb1NNM1l4Rm93OWNSYUI5bnRmXzE2ODM2MjU0ODI6MTY4MzYyOTA4Ml9WNA)![](https://z28pynubvc.feishu.cn/space/api/box/stream/download/asynccode/?code=MmZkNDFiNzNiMGFhYWZkMWE1ZDg4NDI5NDZlYmQwZTlfTDlES1paSlMwd0lkR1hIeHlQS0xQZFFHOUNUNUp5RVpfVG9rZW46WHdocWJSSDVSb2pQVnd4VWdKRGNBbE5KbnljXzE2ODM2MjU0ODI6MTY4MzYyOTA4Ml9WNA)

2. 点击 代码执行程序 -> 全部运行，接下来等待程序下载依赖并启动即可，中间会弹出窗口让你授权谷歌网盘，确认即可。

![](https://z28pynubvc.feishu.cn/space/api/box/stream/download/asynccode/?code=MjRmYjBiNDI1YjVlMmE5Yzc1MmRiYjVmOTdhNTY4NTVfcWpHeHREaERrM3FCYzZqdGlaMVoxakRYTEFqeHJYU0tfVG9rZW46Q2RkOGJvOFpKbzZydXB4QzVyb2NkTUdrbm1HXzE2ODM2MjU0OTc6MTY4MzYyOTA5N19WNA)![](https://z28pynubvc.feishu.cn/space/api/box/stream/download/asynccode/?code=ZTY1YjUyMDliMTYyYzVhN2ZiMTM5ZWRkNDFjY2NjMzdfUnlDTm00T2hhUkxVdjQyRUhvQXlyVExadmdSYkwydjhfVG9rZW46QXNqemJOQkQ1b1VzaHp4V1p0bGNXbmo0bkZmXzE2ODM2MjU0OTc6MTY4MzYyOTA5N19WNA)![](https://z28pynubvc.feishu.cn/space/api/box/stream/download/asynccode/?code=OWZjODhhZmY4NzA3NTJlMDhjYzBmZmZiODRhY2UxNzNfaTBHWjMwRDVuakg5bERxVEM5QldPb0xJZnFZWlNzU01fVG9rZW46UEpsZWI1Ump1b2xrODB4T2liTGNoeUVMbk5lXzE2ODM2MjU0OTc6MTY4MzYyOTA5N19WNA)![](https://z28pynubvc.feishu.cn/space/api/box/stream/download/asynccode/?code=ZDE2MzkwNTI0MjE1MzQwOWE4NDA4ZmFiN2U1ODkzMGFfTkpzeWY3ME12bnh3OEc4ZjAydVROeWNnOEtQY1Z1Q3pfVG9rZW46V3lRZWJZTm5rb1JhR2x4YjB2aWNCOWxMbldoXzE2ODM2MjU0OTc6MTY4MzYyOTA5N19WNA)

3. 点击服务的网址，现在可以开始绘图啦！

<figure><img src="https://z28pynubvc.feishu.cn/space/api/box/stream/download/asynccode/?code=MTNlMzgwNjU3MDIxNzc0MDAwYjlmYjE0YzNiYjQ1NzFfNVhSSmJvdXUwWVFmcG5oY3R4UUVWSmRyWUtab2tFcWpfVG9rZW46U24wQmJqYTJGb2Z4d0d4VU1aUmN0Q3ZLbllkXzE2ODM2MjU1MDU6MTY4MzYyOTEwNV9WNA" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
这个脚本会用谷歌云盘保存你下来的模型、插件等内容，如果如果模型下太多会超出免费版空间，你可以购买空间，或者在“1.2简历云端资料夹”中把`sd_no_link_mode`勾选不使用云盘，**但这样每次都会重新下载模型**
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>
