## Scenario
After you generate a push address of a push domain name, if you want to watch the live streaming content pushed to the push address, you need to get the playback address generated by the playback domain name in the playback configuration and add the StreamName to it to associate it with the push address. In this way, you can get the playback address used to watch the live stream.

## Prerequisites
 You have logged in to the [LVB Console](https://console.cloud.tencent.com/live).

## Directions
1. Select **Domain Name Management** in the left sidebar and click **Manage** or the playback domain name to be configured to enter the domain name management page.
 ![](https://main.qcloudimg.com/raw/4c5032073fac98ce308d353c8e218cd4.png)

2. In the **Playback Configuration** tab, you can view three types of playback addresses under the domain name, i.e., RTMP, FLV, and HLS. Replace the StreamName (stream name) to associate a push address. After the association, you can play back the live stream at the playback address. To generate the push address, see [Push Configuration](https://intl.cloud.tencent.com/document/product/267/31059).
 ![](https://main.qcloudimg.com/raw/15afd6e0a641e14eca632e0df7cdbecb.png)

3. The generation rules for playback address are as follows:
        RTMP format: rtmp://domain/AppName/StreamName?txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)
        FLV format: http://domain/AppName/StreamName.flv?txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)
        M3U8 format: http://domain/AppName/StreamName.m3u8?txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)
>- domain: Your domain name for which an ICP filing has been obtained.
>- AppName: Application name which is "live" by default. If you want to customize it, you need to submit a ticket for configuration.
>- StreamName: User-defined stream name which is used to identify the live stream.
>- txSecret: Authentication string generated after playback authentication is enabled.
>- txTime: Timestamp set for the playback address which represents the validity period of the address in the console.

4. If a transcoding template is configured for the playback domain name and the transcoded live stream needs to be played back, the transcoded playback address should be spliced by adding `_transcoding template name` after the StreamName in the original playback address.
For example, if the original playback address is `http://domain/AppName/StreamName.flv?txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)` and the name of the transcoding template associated is `hd`, then the transcoded playback address is `http://domain/AppName/StreamName_hd.flv?txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)`.

5. If H.265 is used for push and H.265 live stream needs to be played back, you need to add `_265` after the playback address; otherwise, the H.264 live stream will be played back, which will incur transcoding fees.
For example, if the original playback address is `http://domain/AppName/StreamName.flv?txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)` and H.265 is used for push, then the playback address of the original stream is `http://domain/AppName/StreamName_265.flv?txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)`.
