## 操作场景
本文档主要指导您在游戏服务器队列进行容灾操作。


## 准备工作 
- 已集成 [ServerSDK 的代码包](https://intl.cloud.tencent.com/document/product/1055/36674)，您也可以 [使用示范包](https://intl.cloud.tencent.com/document/product/1055/36678)。
- 已创建服务器舰队1（上海地区）。
- 已创建服务器舰队2（美国地区）。



## 操作步骤
### 创建游戏服务器队列
1. 登录 [游戏服务器引擎控制台](https://console.cloud.tencent.com/gse)，单击左侧菜单【游戏服务器队列】。
2. 选择刚创建的服务器舰队，并将上海-服务器舰队1和美国-服务器舰队2加入至队列。
3. 进入服务器舰队详情页，修改延迟策略：延时设置在150ms内：


### 请求服务端地址
使用开始放置游戏服务器会话，除了在代码里集成 SDK 调用云 API，您还可以通过 [云 API 调试](https://console.cloud.tencent.com/api/explorer?Product=gse) 快捷创建。

**输入参数**：
- player1 至上海的延时100ms，至硅谷的延时50ms。
- player2 至上海的延时60ms，至硅谷的延时80ms。



因为延迟策略配置查找所有玩家延时在150ms内的区域的服务器，硅谷和上海都满足要求，所以，游戏服务器会话自动创建于优先级高的上海-服务器舰队1上。

### 自动容灾

假设现在上海出现了故障，上海的速度将无法测出。

**输入参数**：  


游戏服务器会话自动创建于优先级高的硅谷-服务器舰队2上。


### 手动容灾
如果某一区域出现故障，从游戏服务器会话队列中的目标列表，踢出该故障区域的 fleet。
