云数据库 MySQL 支持四种架构：高可用版、金融版、单节点高 IO 版、基础版。目前仅支持高可用版升级为金融版。

<span id = "gaokeyongban"></span>
## 高可用版
高可用版采用一主一备的高可用模式，实时热备，提供宕机自动检测和故障自动转移。覆盖游戏、互联网、物联网、零售电商、物流、保险、证券等行业应用。
特点如下：
- 主备复制方式有两种：异步（默认）、半同步，复制方式可在 [控制台](https://console.cloud.tencent.com/cdb) 的实例详情页修改。也可通过控制台升级到金融版（一主二备强同步模式）。
- 支持特性齐全，包含只读实例、灾备实例、安全组、数据迁移、多可用区部署等，具体特性请参见 [产品优势](https://intl.cloud.tencent.com/document/product/236/5148)。
- 高可用版实例可用性能够达到99.95%，具体协议请参见 [服务等级协议](https://intl.cloud.tencent.com/document/product/301/30977)。
- 数据节点部署在强大硬件之上，底层存储使用本地 NVMe SSD 硬盘，提供强大的 IO 性能，IOPS 最高可达240000（实际 IOPS 速率与配置、页面大小和业务负载有关，此数值是根据 MySQL 默认16KB分页大小测试所得，仅供参考）。

架构如下：
![Alt text](https://main.qcloudimg.com/raw/baf6c165620f79a5dd5f56b6a02d9eb0.svg)


<span id = "jrb"></span>
## 金融版
>原一主两备（即复制方式为强同步）的高可用版更名为金融版，存量的一主两备实例控制台版本显示会对应更新。
>
金融版采用一主两备三节点架构，支持强同步复制方式，通过实时热备，确保数据的强一致性，提供金融级的可靠性和高可用性。
- 主备复制方式：强同步。
- 支持特性齐全，包含只读实例、灾备实例、安全组、数据迁移、多可用区部署等，具体特性请参见 [产品优势](https://intl.cloud.tencent.com/document/product/236/5148)。
- 金融版实例可用性能够达到99.99%，具体协议请参见 [服务等级协议](https://intl.cloud.tencent.com/document/product/301/30977)。
- 数据节点部署在强大硬件之上，底层存储使用本地 NVMe SSD 硬盘，提供强大的 IO 性能，IOPS 最高可达240000（实际 IOPS 速率与配置、页面大小和业务负载有关，此数值是根据 MySQL 默认16KB分页大小测试所得，仅供参考）。

架构如下：
![](https://main.qcloudimg.com/raw/2ce86a70e71ddaf8e9337567fd00540f.png)


<span id = "danjiedian"></span>
## 单节点高 IO 版
单节点高 IO 版采用单个物理节点部署，性价比高；底层存储使用本地 NVMe SSD 硬盘，提供强大的 IO 性能。目前应用于只读实例，帮助业务分摊读压力，适用于有读写分离需求的各个行业应用。

架构如下：
![Alt text](https://main.qcloudimg.com/raw/9c18abaf213f5b2c66f36e538eb86273.svg)
>
>- 单节点部署存在单点风险，在只购买一个只读实例情况下，无法保证业务高可用，单个只读实例故障，会导致业务中断而影响客户。
>- 单个只读实例恢复时长受业务数据量大小影响，无法得到保证。因此，建议对可用性有要求的业务 [RO 组](https://intl.cloud.tencent.com/document/product/236/11361) 内至少选购两个只读实例，保证可用性。


<span id = "jichuban"></span>
## 基础版
基础版采用单个节点部署，价格低廉，性价比非常高。特点如下：
- 计算与存储分离，若计算节点故障，能够通过更换节点达到快速恢复的效果；底层数据采用云盘三副本存储，保证一定的数据可靠性，硬盘故障可通过硬盘快照模式快速恢复。
- 基础版提供针对数据库连接、访问、资源等多维度20多余项监控，并可配置对应告警策略，相较于云服务器自建，更加省心；同时兼具极大价格优势，相较于云服务器节省40%的成本开销；基础版节点部署在云服务器上，提供数据库性能比用户自建更好。
- MySQL 基础版底层存储介质使用高性能云盘，适用于90%的 I/O 场景，质优价廉，性能稳定突出；具体 IOPS 计算公式：{min 1500 + 8 * 容量，max 4500}。

架构如下：
![Alt text](https://main.qcloudimg.com/raw/2293e213a7908bd8de95fa21c141c9eb.svg)

>
> - 基础版不建议用于业务正式环境，适用于个人学习、微型网站、企业非核心小型系统以及大中型企业开发与测试环境。
> - 由于 MySQL 基础版是单节点架构，当该节点出现故障，恢复时长比云服务器故障恢复稍长（涉及实例启动与数据恢复）。建议对高可用有要求的业务，使用 MySQL 高可用版或金融版的实例。


