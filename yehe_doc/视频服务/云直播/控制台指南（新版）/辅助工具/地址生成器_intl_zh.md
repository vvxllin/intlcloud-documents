
## 操作场景
通过地址生成器，可以快速地选择已添加的推流/播放域名，生成对应的推流/播放地址。

## 前提条件
在 [云直播控制台](https://console.cloud.tencent.com/live) 的 [域名管理](https://intl.cloud.tencent.com/document/product/267/31056) 中至少有一个可用的域名。

## 操作步骤
1. 登录云直播控制台，选择【辅助工具】>[【地址生成器】](https://console.cloud.tencent.com/live/addrgenerator/addrgenerator)，进入地址生成器。
3. 在地址生成器进行如下配置：
	1. 选择生成类型为**推流域名**或**播放域名**。
	2. 选择您已添加到域名管理里对应的域名。
	3. AppName 为区分同一个域名下多个 App 的地址路径，默认为 live。
> AppName 支持自定义编辑，仅支持英文字母、数字和符号。
	4. 填写自定义的流名称 StreamName，例如：`liveteststream`。
	5. 选择地址过期时间，例如：`2019-11-30 23:59:59`。
3. 单击【生成地址】即可生成对应的域名地址。
![](https://main.qcloudimg.com/raw/1d9741fe544d1c850ab89b22134f6dc8.png)

>
>- 生成的推流/播放地址由以下4部分组成：
![](https://main.qcloudimg.com/raw/9094e537a4ae7cecc7feb9c88fb83a55.png)
>- 生成的播放地址支持 RTMP、FLV 和 HLS 协议，可以单击播放地址后的二维码，通过 精简版 Demo 扫码查看播放地址：
![](https://main.qcloudimg.com/raw/d91fe5d373cfc03df2c87562f3984858.png)
