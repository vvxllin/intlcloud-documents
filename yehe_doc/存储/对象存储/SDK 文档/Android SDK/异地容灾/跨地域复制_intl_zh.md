## 简介

本文档提供关于跨地域复制的 API 概览以及 SDK 示例代码。

| API                                                          | 操作名         | 操作描述                   |
| ------------------------------------------------------------ | -------------- | -------------------------- |
| [PUT Bucket replication](https://intl.cloud.tencent.com/document/product/436/19223) | 设置跨地域复制 | 设置存储桶的跨地域复制规则 |
| [GET Bucket replication](https://intl.cloud.tencent.com/document/product/436/19222) | 查询跨地域复制 | 查询存储桶的跨地域复制规则 |
| [DELETE Bucket replication](https://intl.cloud.tencent.com/document/product/436/19221) | 删除跨地域复制 | 删除存储桶的跨地域复制规则 |

## 设置跨地域复制

#### 功能说明

设置指定存储桶的跨地域复制规则。

#### 方法原型
```java
PutBucketReplicationResult putBucketReplication(PutBucketReplicationRequest request)throws CosXmlClientException, CosXmlServiceException;
void putBucketReplicationAsync(PutBucketReplicationRequest request, CosXmlResultListener cosXmlResultListener);
```

#### 请求示例

[//]: # (.cssg-snippet-put-bucket-replication)
```java
String bucket = "examplebucket-1250000000"; //格式：BucketName-APPID
String ownerUin = "100000000001"; //发起者身份标示：OwnerUin
String subUin = "100000000001"; //发起者身份标示：SubUin
PutBucketReplicationRequest putBucketReplicationRequest = new PutBucketReplicationRequest(bucket);
putBucketReplicationRequest.setReplicationConfigurationWithRole(ownerUin, subUin);
PutBucketReplicationRequest.RuleStruct ruleStruct = new PutBucketReplicationRequest.RuleStruct();
ruleStruct.id = "replication_01"; //用来标注具体 Rule 的名称
ruleStruct.isEnable = true; //标识 Rule 是否生效。true：生效；false：不生效
ruleStruct.region = "ap-beijing"; //目标存储桶地域信息
ruleStruct.bucket = "destinationbucket-1250000000";  // 目标存储桶
ruleStruct.prefix = "34"; //前缀匹配策略，
putBucketReplicationRequest.setReplicationConfigurationWithRule(ruleStruct);
// 设置签名校验 Host，默认校验所有 Header
Set<String> headerKeys = new HashSet<>();
headerKeys.add("Host");
putBucketReplicationRequest.setSignParamsAndHeaders(null, headerKeys);
// 使用同步方法
try {
    PutBucketReplicationResult putBucketReplicationResult = cosXmlService.putBucketReplication(putBucketReplicationRequest);
} catch (CosXmlClientException e) {
    e.printStackTrace();
} catch (CosXmlServiceException e) {
    e.printStackTrace();
}
// 使用异步回调请求
cosXmlService.putBucketReplicationAsync(putBucketReplicationRequest, new CosXmlResultListener() {
    @Override
    public void onSuccess(CosXmlRequest request, CosXmlResult result) {
        PutBucketReplicationResult putBucketReplicationResult = (PutBucketReplicationResult) result;
    }

    @Override
    public void onFail(CosXmlRequest cosXmlRequest, CosXmlClientException clientException, CosXmlServiceException serviceException) {
        // todo PUT Bucket replication failed because of CosXmlClientException or CosXmlServiceException...
    }
});
```

#### 参数说明
| 参数名称| 描述  | 类型  |
| ----| ---- | ---- |
| bucket  | 源存储桶，格式：BucketName-APPID，详情请参见 [命名规范](https://intl.cloud.tencent.com/document/product/436/13312) | String                         |
| ownerUin  |发起者身份标示：OwnerUin  | String |
| subUin  |发起者身份标示：SubUin    | String |
| ruleStruct  |签名是否校验请求 url 中查询参数    | RuleStruct |
| queryParameterKeys  |签名是否校验请求 url 中查询参数    | `Set<String>` |
| headerKeys          |  签名是否校验 header                | `Set<String>` |
| cosXmlResultListener      | 结果回调        | CosXmlResultListener   |


#### 返回结果说明
通过 PutBucketReplicationResult 返回请求结果。

| 成员变量 | 类型 | 描述                                                     |
| -------- | ---- | -------------------------------------------------------- |
| httpCode | int  | HTTP Code， [200，300)之间表示操作成功，否则表示操作失败 |

>操作失败时，SDK 将抛出 [CosXmlClientException](https://intl.cloud.tencent.com/document/product/436/31517) 或 [CosXmlServiceException](https://intl.cloud.tencent.com/document/product/436/31517) 异常。




## 查询跨地域复制

#### 功能说明

查询指定存储桶的跨地域复制规则。

#### 方法原型
```java
GetBucketReplicationResult getBucketReplication(GetBucketReplicationRequest request)throws CosXmlClientException, CosXmlServiceException;
void getBucketReplicationAsync(GetBucketReplicationRequest request, CosXmlResultListener cosXmlResultListener);
```

#### 请求示例

[//]: # (.cssg-snippet-get-bucket-replication)
```java
String bucket = "examplebucket-1250000000"; //格式：BucketName-APPID
GetBucketReplicationRequest getBucketReplicationRequest = new GetBucketReplicationRequest(bucket);
//设置签名校验 Host，默认校验所有 Header
Set<String> headerKeys = new HashSet<>();
headerKeys.add("Host");
getBucketReplicationRequest.setSignParamsAndHeaders(null, headerKeys);
// 使用同步方法
try {
    GetBucketReplicationResult getBucketReplicationResult = cosXmlService.getBucketReplication(getBucketReplicationRequest);
} catch (CosXmlClientException e) {
    e.printStackTrace();
} catch (CosXmlServiceException e) {
    e.printStackTrace();
}
// 使用异步回调请求
cosXmlService.getBucketReplicationAsync(getBucketReplicationRequest, new CosXmlResultListener() {
    @Override
    public void onSuccess(CosXmlRequest request, CosXmlResult result) {
        GetBucketReplicationResult getBucketReplicationResult = (GetBucketReplicationResult) result;
    }

    @Override
    public void onFail(CosXmlRequest cosXmlRequest, CosXmlClientException clientException, CosXmlServiceException serviceException) {
        // todo GET Bucket replication failed because of CosXmlClientException or CosXmlServiceException...
    }
});
```

#### 参数说明

| 参数名称| 描述  | 类型  |
| ----| ---- | ---- |
| bucket  | 查询跨地域复制的存储桶，格式：BucketName-APPID，详情请参见 [命名规范](https://intl.cloud.tencent.com/document/product/436/13312) | String                         |
| headerKeys          |  签名是否校验 header                | `Set<String>` |
| cosXmlResultListener      | 结果回调        | CosXmlResultListener   |

#### 返回结果说明

通过 GetBucketReplicationResult 返回请求结果。

| 成员变量 | 类型 | 描述                                                     |
| -------- | ---- | -------------------------------------------------------- |
| httpCode | int  | HTTP Code， [200，300)之间表示操作成功，否则表示操作失败 |
| replicationConfiguration | [ReplicationConfiguration](https://github.com/tencentyun/qcloud-sdk-android/blob/master/QCloudCosXml/cosxml/src/normal/java/com/tencent/cos/xml/model/tag/ReplicationConfiguration.java) | 返回指定账号下的存储桶的跨地域复制配置信息                         |

>操作失败时，SDK 将抛出 [CosXmlClientException](https://intl.cloud.tencent.com/document/product/436/31517) 或 [CosXmlServiceException](https://intl.cloud.tencent.com/document/product/436/31517) 异常。


## 删除跨地域复制

#### 功能说明

删除指定存储桶的跨地域复制规则。

#### 方法原型
```java
DeleteBucketReplicationResult deleteBucketReplication(DeleteBucketReplicationRequest request)throws CosXmlClientException, CosXmlServiceException;
void deleteBucketReplicationAsync(DeleteBucketReplicationRequest request, CosXmlResultListener cosXmlResultListener);
```

#### 请求示例

[//]: # (.cssg-snippet-delete-bucket-replication)
```java
String bucket = "examplebucket-1250000000"; //格式：BucketName-APPID
DeleteBucketReplicationRequest deleteBucketReplicationRequest = new DeleteBucketReplicationRequest(bucket);
// 设置签名校验 Host，默认校验所有 Header
Set<String> headerKeys = new HashSet<>();
headerKeys.add("Host");
deleteBucketReplicationRequest.setSignParamsAndHeaders(null, headerKeys);
// 使用同步方法
try {
    DeleteBucketReplicationResult deleteBucketReplicationResult = cosXmlService.deleteBucketReplication(deleteBucketReplicationRequest);
} catch (CosXmlClientException e) {
    e.printStackTrace();
} catch (CosXmlServiceException e) {
    e.printStackTrace();
}
// 使用异步回调请求
cosXmlService.deleteBucketReplicationAsync(deleteBucketReplicationRequest, new CosXmlResultListener() {
    @Override
    public void onSuccess(CosXmlRequest request, CosXmlResult result) {
        DeleteBucketReplicationResult deleteBucketReplicationResult = (DeleteBucketReplicationResult) result;
    }

    @Override
    public void onFail(CosXmlRequest cosXmlRequest, CosXmlClientException clientException, CosXmlServiceException serviceException) {
        // todo DELETE Bucket replication failed because of CosXmlClientException or CosXmlServiceException...
    }
});
```

#### 参数说明

| 参数名称| 描述  | 类型  |
| ----| ---- | ---- |
| bucket  | 删除跨地域复制的存储桶，格式：BucketName-APPID，详情请参见 [命名规范](https://intl.cloud.tencent.com/document/product/436/13312) | String                         |
| headerKeys          |  签名是否校验 header                | `Set<String>` |
| cosXmlResultListener      | 结果回调        | CosXmlResultListener   |


#### 返回结果说明

通过 DeleteBucketReplicationResult 返回请求结果。

| 成员变量 | 类型 | 描述                                                     |
| -------- | ---- | -------------------------------------------------------- |
| httpCode | int  | HTTP Code， [200，300)之间表示操作成功，否则表示操作失败 |

>操作失败时，SDK 将抛出 [CosXmlClientException](https://intl.cloud.tencent.com/document/product/436/31517) 或 [CosXmlServiceException](https://intl.cloud.tencent.com/document/product/436/31517) 异常。

