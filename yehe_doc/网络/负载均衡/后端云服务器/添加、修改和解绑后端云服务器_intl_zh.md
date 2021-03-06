负载均衡将请求路由至运行正常的后端云服务器实例，首次使用负载均衡或根据业务需求，需要增删后端服务器数量时，可按照下文指引进行操作。

>
>- 解绑后端服务器会解除负载均衡实例与云服务器实例的关联关系，且负载均衡会立即停止对其的请求转发。
>- 解绑后端服务器不会对云服务器的生命周期产生任何影响，您也可以再次将它添加至后端服务器集群中。
>- 如果负载均衡实例与某个弹性伸缩组关联，则该组中的云服务器会自动添加至负载均衡后端云服务器，从弹性伸缩组移除的云服务器实例会自动从负载均衡后端云服务器中删除。

## 负载均衡
### 添加负载均衡后端云服务器
1. 登录 [负载均衡控制台](https://console.cloud.tencent.com/loadbalance)，在列表中，单击相应的负载均衡实例 ID，进入负载均衡详情页。
2. 在实例对应的监听器中，添加相应的后端云服务器。
 - **TCP/UDP 监听器**
 添加后端云服务器时，在图左所示的列表中，选中需要绑定的监听器，单击【绑定】，弹出框中详细操作，请参见下一步说明。
![](https://main.qcloudimg.com/raw/64a10e9154b135dfd37e74365cbd4442.png)
 - **HTTP/HTTPS 监听器**
 添加后端云服务器时，在下图左侧所示的列表中，选中需要绑定的监听器与规则，单击【绑定】，弹出框中详细操作，请参见下一步说明。
![](https://main.qcloudimg.com/raw/347bc0cbe6afa7314ac7572d8722d145.png)
3. 在弹出框中，选择需要关联的云服务器，填写相关云服务器需要被转发的端口与权重，单击【确定】，即可完成云服务器与负载均衡关联操作。
>弹出框中仅展示同地域、相同网络环境、未被隔离、未过期、带宽（峰值）不为0的可选云服务器。
>
 ![](https://main.qcloudimg.com/raw/99ff99e6001cab18a259f5147df5fcbe.png)
4. 如果需要批量绑定服务器且预设端口值一致时，可先在“默认端口”处输入预设端口值、再勾选相关服务器并设定权重值，单击【确定】，即可完成绑定。
![](https://main.qcloudimg.com/raw/7c2191001d1edb0b66e4251c55179aea.png)
>如需使用 API 添加负载均衡后端服务器，请参考 [RegisterInstancesWithLoadBalancer 接口](https://intl.cloud.tencent.com/document/api/214/1265) 说明。

### 修改负载均衡后端服务器权重
后端服务器权重决定了云服务器被转发的请求相对数量，在绑定后端云服务器时，需要预设权重信息，后续如需修改权重，可请参考下文指引。有关负载均衡后端服务器权重的更多信息，请参见 [负载均衡轮询方式](/doc/product/214/6153)。
1. 登录 [负载均衡控制台](https://console.cloud.tencent.com/loadbalance)，在列表中，单击相应的负载均衡实例 ID，进入负载均衡详情页。
2. 选中实例与监听器规则后，在服务器列表中，选择相关服务器，单击【编辑】，输入修改后的权重值，单击【提交】，即可完成对该台服务器权重的修改。
3. 如需批量修改，选择所有相关服务器后，单击【修改权重】，输入修改后的权重值，单击【提交】，即可完成批量修改。
![](https://main.qcloudimg.com/raw/e08f226ba159369524c098f285768717.png)

>如需使用 API 修改负载均衡后端服务器权重，请参见 [ModifyLoadBalancerBackends 接口](https://intl.cloud.tencent.com/document/api/214/1264) 说明。

### 修改负载均衡后端服务器端口
1. 登录 [负载均衡控制台](https://console.cloud.tencent.com/loadbalance)，在列表中，单击相应的负载均衡实例 ID，进入负载均衡详情页。
2. 选中实例与监听器规则后，在服务器列表中，选择相关服务器，单击【编辑】，输入修改后的端口值，单击【提交】，即可完成对该台服务器端口的修改。
3. 如需批量修改，选择所有相关服务器后，单击【修改端口】，输入修改后的端口，单击【提交】，即可完成批量修改。
![](https://main.qcloudimg.com/raw/c1fe26d1bcd8ecdfa69349c2ed985c6c.png)

>如需使用 API 修改负载均衡后端服务器端口，请参见 [ModifyTargetPort](https://intl.cloud.tencent.com/document/product/214/33812) 说明。

### 解绑负载均衡后端服务器
1. 登录 [负载均衡控制台](https://console.cloud.tencent.com/loadbalance)，在列表中，单击相应的负载均衡实例 ID，进入负载均衡详情页。
2. 选中监听器与规则后，在右端云服务器列表中，选择需要解绑的云服务器，单击【解绑】，在弹出框中，单击【提交】即可。
3. 如果需要批量解绑，选中所有需要解绑的云服务器，单击【解绑】，在弹出框中，单击【提交】即可。
![](https://main.qcloudimg.com/raw/6bf6671605ce6e04387bb54bc573e348.png)

>如需使用 API 解绑负载均衡后端服务器，请参见 [DeregisterTargets 接口](https://intl.cloud.tencent.com/document/product/214/33832) 说明。

## 传统型负载均衡
### 添加负载均衡后端服务器
1. 登录 [负载均衡控制台](https://console.cloud.tencent.com/loadbalance)，在列表中，单击相应的负载均衡实例 ID，进入负载均衡详情页。
2. 绑定后端服务器前，传统型负载均衡需要在**创建监听器阶段**指定后端服务器的端口，单击【新建】，在“后端端口”处设置端口，单击【下一步】继续完成配置。
![](https://main.qcloudimg.com/raw/f8f36253ef0c86108a189180c4a9b5a8.png)
3. 单击【绑定】，勾选需要绑定的云服务器，在“权重”处填写权重信息，单击【确定】，即可完成绑定。
>弹出框中仅展示同地域、相同网络环境、未被隔离、未过期、带宽（峰值）不为0的可选云服务器。
>
![](https://main.qcloudimg.com/raw/a285308e527df5c435fcdc1c949313a3.png)
 
>如需使用 API 添加后端服务器，请参考 [RegisterTargetsWithClassicalLB 接口](https://intl.cloud.tencent.com/document/product/214/33802) 说明。

### 修改负载均衡后端服务器权重
1. 登录 [负载均衡控制台](https://console.cloud.tencent.com/loadbalance)，在列表中，单击相应的负载均衡实例 ID，进入负载均衡详情页。
2. 在监听器下方的服务器列表中，勾选相关服务器，单击【编辑】，输入修改后的权重值，单击【提交】，即可完成对该台服务器权重的修改。
3. 如需批量修改，选择所有相关服务器后，单击【修改权重】，输入修改后的权重值，单击【提交】，即可完成批量修改。
![](https://main.qcloudimg.com/raw/5311658177f3302780f62a50718007cc.png)

>暂不支持使用 API 修改后端服务器权重。

### 解绑负载均衡后端服务器
1. 登录 [负载均衡控制台](https://console.cloud.tencent.com/loadbalance)，在列表中，单击相应的负载均衡实例 ID，进入负载均衡详情页。
2. 解绑服务器时，在监听器列表下方的服务器列表中，选择相关服务器，单击【解绑】，在弹出框中，单击【提交】即可。
3. 如需批量解绑，选择所有相关服务器后，单击【解绑】，在弹出框中，单击【提交】，即可完成批量解绑。
![](https://main.qcloudimg.com/raw/0d84fadaaf9dc0ac4310c0e0ba6a1bac.png)

>如需使用 API 解绑后端服务器，请参考 [DeregisterTargetsFromClassicalLB 接口](https://intl.cloud.tencent.com/document/product/214/33807) 说明。
