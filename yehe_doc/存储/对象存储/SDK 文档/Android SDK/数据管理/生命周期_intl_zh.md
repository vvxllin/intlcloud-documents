## 简介
本文档提供关于生命周期的 API 概览以及 SDK 示例代码。

| API                                                          | 操作名       | 操作描述                       |
| ------------------------------------------------------------ | ------------ | ------------------------------ |
| [PUT Bucket lifecycle](https://intl.cloud.tencent.com/document/product/436/8280) | 设置生命周期 | 设置存储桶的生命周期管理的配置 |
| [GET Bucket lifecycle](https://intl.cloud.tencent.com/document/product/436/8278) | 查询生命周期 | 查询存储桶生命周期管理的配置   |
| [DELETE Bucket lifecycle](https://intl.cloud.tencent.com/document/product/436/8284) | 删除生命周期 | 删除存储桶生命周期管理的配置   |

## 设置生命周期

#### 功能说明

设置指定存储桶的生命周期配置信息。

#### 方法原型
```java
PutBucketLifecycleResult putBucketLifecycle(PutBucketLifecycleRequest request) throws CosXmlClientException, CosXmlServiceException;

void putBucketLifecycleAsync(PutBucketLifecycleRequest request, CosXmlResultListener cosXmlResultListener);
```

#### 请求示例

[//]: # (.cssg-snippet-put-bucket-lifecycle)
```java
String bucket = "examplebucket-1250000000"; //格式：BucketName-APPID
PutBucketLifecycleRequest putBucketLifecycleRequest = new PutBucketLifecycleRequest(bucket);

// 声明周期配置规则信息
LifecycleConfiguration.Rule rule = new LifecycleConfiguration.Rule();
rule.id = "Lifecycle ID";
LifecycleConfiguration.Filter filter = new LifecycleConfiguration.Filter();
filter.prefix = "prefix/";
rule.filter = filter;
rule.status = "Enabled";
LifecycleConfiguration.Transition transition = new LifecycleConfiguration.Transition();
transition.days = 100;
transition.storageClass = COSStorageClass.STANDARD.getStorageClass();
rule.transition = transition;
putBucketLifecycleRequest.setRuleList(rule);
// 设置签名校验 Host，默认校验所有 Header
Set<String> headerKeys = new HashSet<>();
headerKeys.add("Host");
putBucketLifecycleRequest.setSignParamsAndHeaders(null, headerKeys);
// 使用同步方法
try {
    PutBucketLifecycleResult putBucketLifecycleResult = cosXmlService.putBucketLifecycle(putBucketLifecycleRequest);
} catch (CosXmlClientException e) {
    e.printStackTrace();
} catch (CosXmlServiceException e) {
    e.printStackTrace();
}

// 使用异步回调请求
cosXmlService.putBucketLifecycleAsync(putBucketLifecycleRequest, new CosXmlResultListener() {
    @Override
    public void onSuccess(CosXmlRequest request, CosXmlResult result) {
        PutBucketLifecycleResult putBucketLifecycleResult = (PutBucketLifecycleResult) result;
    }

    @Override
    public void onFail(CosXmlRequest cosXmlRequest, CosXmlClientException clientException, CosXmlServiceException serviceException) {
        // todo Put Bucket Lifecycle failed because of CosXmlClientException or CosXmlServiceException...
    }
});
```

>请求时，如需直接设置已计算好的签名串，则可通过调用`putBucketLifecycleRequest.setSign("已计算好的签名串")`方法设置，默认由 SDK 计算签名串。


#### 参数说明

|参数名称|设置方法|描述|类型|
|-----|-----|-----|------|
|bucket|构造方法|设置生命周期的存储桶，格式：BucketName-APPID|string|
|rule|setRuleList|设置存储桶的生命周期配置|LifecycleConfiguration.Rule|
| headerKeys          | setSignParamsAndHeaders  | 签名是否校验 header                | `Set<String>` |
| queryParameterKeys          | setSignParamsAndHeaders  | 签名是否校验请求 url 中的查询参数    | `Set<String>` |
| cosXmlResultListener      | putBucketLifecycleAsync                                                 |   结果回调    | CosXmlResultListener    |

#### 返回结果说明

通过 PutBucketLifecycleResult 返回请求结果。

|成员变量|类型|描述|
|-----|-----|----|
|httpCode|int|HTTP Code， [200, 300)之间表示操作成功，否则表示操作失败|

>操作失败时，SDK 将抛出 [CosXmlClientException](https://intl.cloud.tencent.com/document/product/436/31517) 或 [CosXmlServiceException](https://intl.cloud.tencent.com/document/product/436/31517) 异常。

## 查询生命周期

#### 功能说明

查询存储桶的生命周期管理配置。

#### 方法原型
```java
GetBucketLifecycleResult getBucketLifecycle(GetBucketLifecycleRequest request) throws CosXmlClientException, CosXmlServiceException;

void getBucketLifecycleAsync(GetBucketLifecycleRequest request, CosXmlResultListener cosXmlResultListener);
```

#### 请求示例
[//]: # (.cssg-snippet-get-bucket-lifecycle)
```java
String bucket = "examplebucket-1250000000"; //格式：BucketName-APPID
GetBucketLifecycleRequest getBucketLifecycleRequest = new GetBucketLifecycleRequest(bucket);
// 设置签名校验 Host，默认校验所有 Header
Set<String> headerKeys = new HashSet<>();
headerKeys.add("Host");
getBucketLifecycleRequest.setSignParamsAndHeaders(null, headerKeys);
// 使用同步方法
try {
    GetBucketLifecycleResult getBucketLifecycleResult = cosXmlService.getBucketLifecycle(getBucketLifecycleRequest);
} catch (CosXmlClientException e) {
    e.printStackTrace();
} catch (CosXmlServiceException e) {
    e.printStackTrace();
}

// 使用异步回调请求
cosXmlService.getBucketLifecycleAsync(getBucketLifecycleRequest, new CosXmlResultListener() {
    @Override
    public void onSuccess(CosXmlRequest request, CosXmlResult result) {
        GetBucketLifecycleResult getBucketLifecycleResult = (GetBucketLifecycleResult) result;
    }

    @Override
    public void onFail(CosXmlRequest cosXmlRequest, CosXmlClientException clientException, CosXmlServiceException serviceException) {
        // todo Get Bucket Lifecycle failed because of CosXmlClientException or CosXmlServiceException...
    }
});
```

>请求时，如需直接设置已计算好的签名串，则可通过调用`getBucketLifecycleRequest.setSign("已计算好的签名串")`方法设置，默认由 SDK 计算签名串。

#### 参数说明
|参数名称|设置方法|描述|类型|
|-----|-----|-----|------|
|bucket| 构造方法 | 查询生命周期的存储桶，格式：BucketName-APPID|string|
| headerKeys          | setSignParamsAndHeaders  | 签名是否校验 header                | `Set<String>` |
| queryParameterKeys          | setSignParamsAndHeaders  | 签名是否校验请求 url 中的查询参数    | `Set<String>` |
| cosXmlResultListener      | getBucketLifecycleAsync                                                 |      结果回调  | CosXmlResultListener    |


#### 返回结果说明
通过 GetBucketLifecycleResult 返回请求结果。

|成员变量|类型|描述|
|-----|-----|----|
|httpCode|int|HTTP Code， [200，300)之间表示操作成功，否则表示操作失败|
|lifecycleConfiguration|[LifecycleConfiguration](https://github.com/tencentyun/qcloud-sdk-android/blob/master/QCloudCosXml/cosxml/src/normal/java/com/tencent/cos/xml/model/tag/LifecycleConfiguration.java)|返回 Bucket 的生命周期配置信息|

>操作失败时，SDK 将抛出 [CosXmlClientException](https://intl.cloud.tencent.com/document/product/436/31517) 或 [CosXmlServiceException](https://intl.cloud.tencent.com/document/product/436/31517) 异常。

## 删除生命周期

#### 功能说明

删除存储桶生命周期管理的配置。

#### 方法原型
```java
DeleteBucketLifecycleResult deleteBucketLifecycle(DeleteBucketLifecycleRequest request) throws CosXmlClientException, CosXmlServiceException;

void deleteBucketLifecycleAsync(DeleteBucketLifecycleRequest request,CosXmlResultListener cosXmlResultListener);
```

#### 请求示例

[//]: # (.cssg-snippet-delete-bucket-lifecycle)
```java
String bucket = "examplebucket-1250000000"; //格式：BucketName-APPID
DeleteBucketLifecycleRequest deleteBucketLifecycleRequest = new DeleteBucketLifecycleRequest(bucket);
// 设置签名校验 Host，默认校验所有 Header
Set<String> headerKeys = new HashSet<>();
headerKeys.add("Host");
deleteBucketLifecycleRequest.setSignParamsAndHeaders(null, headerKeys);
// 使用同步方法
try {
    DeleteBucketLifecycleResult deleteBucketLifecycleResult = cosXmlService.deleteBucketLifecycle(deleteBucketLifecycleRequest);

} catch (CosXmlClientException e) {
    e.printStackTrace();
} catch (CosXmlServiceException e) {
    e.printStackTrace();
}

// 使用异步回调请求
cosXmlService.deleteBucketLifecycleAsync(deleteBucketLifecycleRequest, new CosXmlResultListener() {
    @Override
    public void onSuccess(CosXmlRequest request, CosXmlResult result) {
        DeleteBucketLifecycleResult deleteBucketLifecycleResult = (DeleteBucketLifecycleResult) result;
    }

    @Override
    public void onFail(CosXmlRequest cosXmlRequest, CosXmlClientException clientException, CosXmlServiceException serviceException) {
        // todo Delete Bucket Lifecycle failed because of CosXmlClientException or CosXmlServiceException...
    }
});
```

>请求时，如需直接设置已计算好的签名串，则可通过调用`deleteBucketLifecycleRequest.setSign("已计算好的签名串")`方法设置，默认由 SDK 计算签名串。

#### 参数说明
|参数名称|设置方法|描述|类型|
|-----|-----|-----|------|
|bucket|构造方法|被删除生命周期配置的存储桶，格式：BucketName-APPID|string|
| headerKeys          | setSignParamsAndHeaders  | 签名是否校验 header                | `Set<String>` |
| queryParameterKeys          | setSignParamsAndHeaders  | 签名是否校验请求 url 中的查询参数    | `Set<String>` |
| cosXmlResultListener      | deleteBucketLifecycleAsync                                                 |     结果回调    | CosXmlResultListener  |

#### 返回结果说明
通过 DeleteBucketLifecycleResult 返回请求结果。

|成员变量|类型|描述|
|-----|-----|----|
|httpCode|int|HTTP Code， [200，300)之间表示操作成功，否则表示操作失败|

>操作失败时，SDK 将抛出 [CosXmlClientException](https://intl.cloud.tencent.com/document/product/436/31517) 或 [CosXmlServiceException](https://intl.cloud.tencent.com/document/product/436/31517) 异常。