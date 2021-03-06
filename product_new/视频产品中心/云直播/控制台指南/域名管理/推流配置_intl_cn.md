## 操作场景
通过推流配置可以生成您在对应推流域名下的推流地址，往推流地址进行推流实现直播流传输到云直播服务，即实现直播视频上传。

## 前提条件
 已登录 [云直播控制台](https://console.cloud.tencent.com/live)。

## 操作步骤
1. 选择左侧菜单栏【域名管理】，单击【管理】或需配置的推流域名进入域名管理。
 ![](https://main.qcloudimg.com/raw/a86ae59e0ce542aeba330f9a4a169d49.png)
2. 在【推流配置】菜单下，提供了推流地址的生成工具，您仅须填入 StreamName（流 ID）后，单击【生成推流地址】，系统将生成带着 StreamName 的 rtmp 推流地址。生成的推流地址格式为 `rtmp://domain/live/StreamName?txSecret=xxx&txTime=xxx`。其中，`domain`：直播推流域名；`AppName`：应用名称，默认为 live，若要自定义须提交工单配置；`StreamName`：流名称，用户自定义，用于标识直播流；`txSecret`：开启推流鉴权后生成的鉴权串；`txTime`：推流地址设置的时间戳，是控制台推流地址的有效时间。生成的推流地址可以在 [流管理]( https://cloud.tencent.com/document/product/267/20380) 中测试、禁用和删除。
 ![](https://main.qcloudimg.com/raw/492323e1c0c08bb822f3b61e4f9a61e4.png)
我们还提供了 PHP 和 Java 的推流地址示例代码供参考，可以直接参考示例代码完成推流地址的接入。
![](https://main.qcloudimg.com/raw/42f7d41c548d2aa0b101735296ccc818.png)

>? 生成的推流地址在设定的过期时间内均可使用，过期后可以重新生成新的推流地址。
