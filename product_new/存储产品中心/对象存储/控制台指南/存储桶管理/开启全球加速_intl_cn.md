## 简介

您可以通过 COS 控制台为您的存储桶开启全球加速功能，实现全球各地用户快速访问您的存储桶，提升您的业务访问成功率和业务稳定性。关于全球加速的更多信息，请参见 [全球加速概述](https://intl.cloud.tencent.com/document/product/436/33409)。

## 操作步骤

1. 登录 [对象存储控制台](https://console.cloud.tencent.com/cos5) ，单击左侧菜单栏【存储桶列表】，选择单击需要配置全球加速功能的存储桶，进入存储桶详情界面。
![存储桶列表页](https://main.qcloudimg.com/raw/01045b0ada6a9c72b55bf090d14fc193.png)
2. 单击左侧的【高级配置】，进入存储桶的高级配置页，向下找到【全球加速】管理项，单击【编辑】进入修改状态。
![](https://main.qcloudimg.com/raw/e26fe8fd79c9bbc0d0ad1f9fe9088169.png)
3. 打开当前状态的“开启”按钮并保存，即可启用存储桶的全球加速功能。
![](https://main.qcloudimg.com/raw/1c6a7197c77a1555a91ad83fd29c8264.png)
4. 开启了全球加速功能后，您只需要通过全球加速域名访问存储桶，即可实现快速访问数据，全球加速域名格式如`<BucketName-APPID>.cos.accelerate.myqcloud.com`。
>开启全球加速功能，不会影响原有的存储桶默认域名，您仍然可以正常使用。
