## 功能介绍
实例信息是记录用户 EMR 集群的基本信息，用户可以在实例信息页查看集群的基础配置、软件信息和硬件信息。
- 基础配置显示了集群基本信息，例如网络信息、创建时间、安全组、是否开启高可用等。
- 软件信息显示了集群类型、安装软件、版本号，以及是否开启对象存储（COS）和是否启用 Kerberos 模式。
- 硬件配置展示了各节点类型的数量信息。

本文为您介绍如何通过控制台查看集群实例信息。

## 操作步骤
1. 集群创建成功后，登录 [EMR 控制台](https://console.cloud.tencent.com/emr)，在【集群列表】页面单击需要管理的集群【ID/名称】或【详情】。
![](https://main.qcloudimg.com/raw/8c9a4b3fddd3ab79cbb6a8df6cf24ec4.png)
2. 若当前集群未开启对象存储，由于业务需要开启对象存储时，可单击【设置】，按要求填写测试验证地址、SecretID 和 SecretKey。
>为验证后开启 COS 生效，请确保 SecretID 和 SecretKey 对应的访问域名一致，以便于验证。具体操作可见 [控制台自助开启 COS](https://intl.cloud.tencent.com/document/product/1026/34570)。
>
![](https://main.qcloudimg.com/raw/80d243b3b4cdfea22930db19f9d4bca8.png)
