随着厂商通道推送额度和推送频率的限制逐步收紧，push 推送的抵达率和下发速度也受到对应程度的限制。具体限制可参阅：
- [厂商通道限额说明](https://intl.cloud.tencent.com/document/product/1024/35829)
- [厂商通道QPS限制说明](https://intl.cloud.tencent.com/document/product/1024/35247)

腾讯移动推送提供「智能分配」和「自定义」两种通道分配策略，可在厂商通道限制下提升推送的综合抵达率和抵达速度。
## 通道策略概览
<span id="zhineng"></span>
### 智能分配
TPNS会结合设备状态、人群活跃状态和推送通道状态，智能为每个设备分配最佳的下发通道，以此达到以下效果：
1. 提升推送综合抵达率
2. 提高推送综合抵达速度
3. 节省部分厂商通道可用额度

<span id="zidingyi"></span>
### 自定义
目前小米、OPPO、vivo三个厂商通道限制每日推送额度，您可根据业务需求，选择某条推送任务可以通过哪些通道下发，个性化地调整 push 通道下发策略，以节省厂商通道资源，实现推送的价值最大化。
自定义策略详细下发规则见下表：

| 通道 | 开启 | 关闭 |
|---------|---------|---------|
| 华为 | <li>在线：优先走厂商通道，失败走 TPNS 通道补推 <li>离线：优先走厂商通道，失败走 TPNS 通道补推| <li>在线：TPNS 通道 <li>离线：TPNS 通道 |
| 魅族 | <li>在线：优先走厂商通道，失败走 TPNS 通道补推 <li>离线：优先走厂商通道，失败走 TPNS 通道补推|<li>在线：TPNS 通道 <li>离线：TPNS 通道 |
| FCM | <li>在线：优先走厂商通道，失败走 TPNS 通道补推 <li>离线：优先走厂商通道，失败走 TPNS 通道补推| <li>在线：TPNS 通道 <li>离线：TPNS 通道 |
| 小米 |  <li>在线：优先走 TPNS 通道 <li>离线：优先走厂商通道，失败走 TPNS 通道补推| <li>在线：TPNS 通道 <li>离线：TPNS 通道 |
| OPPO |<li>在线：优先走 TPNS 通道 <li>离线：优先走厂商通道，失败走 TPNS 通道补推| <li>在线：TPNS 通道 <li>离线：TPNS 通道 |
| vivo | <li>在线：优先走 TPNS 通道 <li>离线：优先走厂商通道，失败走 TPNS 通道补推|<li>在线：TPNS 通道 <li>离线：TPNS 通道 |
| 其他 |  <li>在线：TPNS 通道 <li>离线：TPNS 通道离线队列| <li>在线：TPNS 通道 <li>离线：TPNS 通道 |

## 开始使用
### 控制台使用
您可在控制台创建推送时选择该条推送的通道策略，具体路径如下：
控制台 > 消息推送 > 新建推送 > 高级设置 > 通道策略
#### 智能分配
选择【智能分配】，系统会智能分配每个设备的下发通道，详见 [智能分配](#zhineng) 的规则。
![](https://main.qcloudimg.com/raw/b53a8b8e21b37aefea81fe7c8c7553c4.png)

#### 自定义
选择【自定义】，点击【查看详情】可以查看详细的厂商额度信息。
![](https://main.qcloudimg.com/raw/a28f612612f856e05bd8e0758805500b.png)
可以根据当前厂商通道剩余配额，以及推送任务的优先级，自定义选择需要推送的通道，详见 [自定义](#zidingyi) 的规则。
![](https://main.qcloudimg.com/raw/7b314d96f64fe63dd36b5a1e512389a8.png)

>TPNS 通道不可关闭。

### Rest API 使用
在 Rest API 可选参数中设置channel_rules参数，可参考 PushAPI 文档中的 [channel_rules 参数说明](https://intl.cloud.tencent.com/document/product/1024/33764)。
推送示例如下：
```json
{
    "audience_type": "token",
    "token_list": [
        "05da87c0ae*************8d884aada5bb2"
    ],
    "message_type": "notify",
    "channel_rules": [
        {
            "channel": "mz",
            "disable": true
        },
        {
            "channel": "xm",
            "disable": false
        }
    ],
    "message": {
        "title": "推送标题",
        "content": "推送内容",
        "android": {
             "custom_content":"{\"key\":\"value\"}"
        }
    }
}
```
