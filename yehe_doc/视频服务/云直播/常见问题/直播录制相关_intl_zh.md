<span id="que1"></span>
###  直播录制的原理是什么？
![img](https://mc.qcloudimg.com/static/img/cbb2aae6b5e767db1d30cb51d147948d/image.png)

对于一条直播流，一旦开启录制，音视频数据就会被旁路到录制系统。主播的手机推上来的每一帧数据，都会被录制系统追加写入到录制文件中。

一旦直播流中断，接入层会立刻通知录制服务器将正在写入的文件落地，将其转存到点播系统中，并为其生成索引，这样您在点播系统中就会看到这个新生成的录制文件了。同时，如果您配置了录制事件通知，录制系统会将该文件的**索引 ID** 和**在线播放地址**等信息通知给您之前配置的服务器上。

但是，如果一个文件过大，在云端的转出和处理过程中就很容易出错，所以为了确保成功率，我们的单个录制文件最长不会超过120分钟，您可以通过 record_interval 参数指定更短的分片。

<span id="que2"></span>
###  为什么直播无法进行视频录制呢？ 
直播录制回看功能依托于腾讯云的**云点播服务**支撑，如果您想要使用录制功能，首先需要在腾讯云的管理控制台 [开通云点播服务](https://console.cloud.tencent.com/vod)。

<span id="que3"></span>
###  直播结束了要多久才能看到录制文件？ 
预计在直播完成后5分钟左右可获取录制文件，录制完成后会有事件回调，详细以收到回调时间为准，更多详情请参见 [回调配置](https://intl.cloud.tencent.com/document/product/267/31074)。

<span id="que4"></span>
### 直播录制后，如何获取录制文件？
录制文件生成后自动存储到云点播系统，需要客户开通点播服务才能存储成功。可通过以下方式获取录制文件：
- [云点播控制台](https://intl.cloud.tencent.com/document/product/267/31563)
- [录制事件通知](https://intl.cloud.tencent.com/document/product/267/31563)
- [点播 API 查询](https://intl.cloud.tencent.com/document/product/267/31563)

<span id="que5"></span>
### 直播视频能迁移吗？
目前需要您获取视频的下载地址后自己迁移。 

<span id="que6"></span>
###  如何设置视频存储时长？
云直播的视频存储目前没有时间限制，您可以通过控制台和 RSET API 接口管理视频文件。 

<span id="que7"></span>
### 一次直播录制会生成几个录制文件？
单个录制文件最长不会超过120分钟，您可以通过 [创建录制模板](https://intl.cloud.tencent.com/document/product/267/30845) 接口中的 record_interval 参数指定更短的分片。 

- 如果一次直播过程非常短暂，例如只有不到1秒钟时间，那么可能是没有录制文件的。
- 如果一次直播时间不算长（小于 record_interval），且中途没有推流中断的事情发生，那么通常只有一个文件。
- 如果一次直播时间很长（超过 record_interval ），那么会按照 record_interval 指定的时间长度进行分片，分片的原因是避免过长的文件在分布式系统中流转时间的不确定性。
- 如果一次直播过程中发生推流中断（之后 SDK 会尝试重新推流），那么每次中断均会产生一个新的分片。

<span id="que8"></span>
### 如何知道哪些文件属于某一次直播？

准确来说，作为 PAAS 的腾讯云并不清楚您的一次直播是怎么定义的，如果您的一次直播持续了20分钟，但中间有一次因为网络切换导致的断流，以及一次手动的停止和重启，那么这算是一次直播还是三次呢？

对于普通的移动直播场景，我们一般定义如下的界面之间的这段时间为一次直播：
![img](https://main.qcloudimg.com/raw/ee3c52237136eab31e0b2b65ef4d83ac.png)

所以来自 App 客户端的时间信息很重要，如果您希望定义这段时间内的录制文件都属于这次直播，那么只需要用直播码和时间信息检索收到的录制通知即可（每一条录制通知事件都会携带 stream_id、start_time 和 end_time 等信息）。

<span id="que9"></span>
### 如何把碎片拼接起来？
目前腾讯云支持使用云端 API 接口拼接视频分片。 

