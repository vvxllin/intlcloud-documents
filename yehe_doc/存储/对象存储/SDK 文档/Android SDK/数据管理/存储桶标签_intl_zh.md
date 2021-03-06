

## 简介

本文档提供关于存储桶标签的 API 概览以及 SDK 示例代码。

| API                                                          | 操作名         | 操作描述                         |
| ------------------------------------------------------------ | -------------- | -------------------------------- |
| [PUT Bucket tagging](https://intl.cloud.tencent.com/document/product/436/8281) | 设置存储桶标签 | 为已存在的存储桶设置标签         |
| [GET Bucket tagging](https://intl.cloud.tencent.com/document/product/436/8277) | 查询存储桶标签 | 查询指定存储桶下已有的存储桶标签 |
| [DELETE Bucket tagging](https://intl.cloud.tencent.com/document/product/436/8286) | 删除存储桶标签 | 删除指定的存储桶标签             |

## 设置存储桶标签

#### 功能说明

PUT Bucket tagging 用于为已存在的存储桶设置标签。

#### 方法原型

```
PutBucketTaggingResult putBucketTagging(PutBucketTaggingRequest request)throws CosXmlClientException, CosXmlServiceException;

void putBucketTaggingAsync(PutBucketTaggingRequest request, CosXmlResultListener cosXmlResultListener);
```

#### 请求示例

```
String bucket = "examplebucket-1250000000"; //格式：BucketName-APPID
PutBucketTaggingRequest putBucketTaggingRequest = new PutBucketTaggingRequest(bucket);
putBucketTaggingRequest.addTag("key", "value");
putBucketTaggingRequest.addTag("hello", "world");

// 使用同步方法
try {
    PutBucketTaggingResult putBucketTaggingResult = cosXmlService.putBucketTagging(putBucketTaggingRequest);
} catch (CosXmlClientException e) {
    e.printStackTrace();
} catch (CosXmlServiceException e) {
    e.printStackTrace();
}

// 使用异步回调请求
cosXmlService.putBucketTaggingAsync(putBucketTaggingRequest, new CosXmlResultListener() {
    @Override
    public void onSuccess(CosXmlRequest request, CosXmlResult result) {
        PutBucketTaggingResult putBucketTaggingResult = (PutBucketTaggingResult) result;
    }

    @Override
    public void onFail(CosXmlRequest cosXmlRequest, CosXmlClientException clientException, CosXmlServiceException serviceException)  {
    }
});
```

#### 参数说明

| 参数名称 | 描述                                                         | 类型   |
| -------- | ------------------------------------------------------------ | ------ |
| bucket   | 设置标签的存储桶，格式为 BucketName-APPID ，详情请参见 [命名规范](https://intl.cloud.tencent.com/document/product/436/13312) | String |
| key      | 标签的 Key，长度不超过128字节，支持英文字母、数字、空格、加号、减号、下划线、等号、点号、冒号、斜线 | String |
| value    | 标签的 Value，长度不超过256字节，支持英文字母、数字、空格、加号、减号、下划线、等号、点号、冒号、斜线 | String |

#### 返回结果说明

| 成员变量 | 描述                                                     | 类型 |
| -------- | -------------------------------------------------------- | ---- |
| httpCode | HTTP Code， [200, 300)之间表示操作成功，否则表示操作失败 | int  |

## 查询存储桶标签

#### 功能说明

GET Bucket tagging 用于查询指定存储桶下已有的存储桶标签。

#### 方法原型

```
GetBucketTaggingResult getBucketTagging(GetBucketTaggingRequest request)throws CosXmlClientException, CosXmlServiceException;

void getBucketTaggingAsync(GetBucketTaggingRequest request, CosXmlResultListener cosXmlResultListener);
```

#### 请求示例

```
String bucket = "examplebucket-1250000000"; //格式：BucketName-APPID
GetBucketTaggingRequest getBucketTaggingRequest = new GetBucketTaggingRequest(bucket);
//设置签名校验 Host, 默认校验所有 Header
Set<String> headerKeys = new HashSet<>();
headerKeys.add("Host");
getBucketTaggingRequest.setSignParamsAndHeaders(null, headerKeys);
// 使用同步方法
try {
    GetBucketTaggingResult getBucketTaggingResult = cosXmlService.getBucketTagging(getBucketTaggingRequest);
} catch (CosXmlClientException e) {
    e.printStackTrace();
} catch (CosXmlServiceException e) {
    e.printStackTrace();
}

// 使用异步回调请求
cosXmlService.getBucketTaggingAsync(getBucketTaggingRequest, new CosXmlResultListener() {
    @Override
    public void onSuccess(CosXmlRequest request, CosXmlResult result) {
        GetBucketTaggingResult getBucketTaggingResult = (GetBucketTaggingResult)result;
    }

    @Override
    public void onFail(CosXmlRequest cosXmlRequest, CosXmlClientException clientException, CosXmlServiceException serviceException)  {
    }
});
```

#### 参数说明

| 参数名称 | 描述                                                         | 类型   |
| -------- | ------------------------------------------------------------ | ------ |
| bucket   | 查询标签的存储桶，格式为 BucketName-APPID ，详情请参见 [命名规范](https://intl.cloud.tencent.com/document/product/436/13312) | String |

#### 返回结果说明

| 成员变量 | 描述                                                     | 类型    |
| -------- | -------------------------------------------------------- | ------- |
| httpCode | HTTP Code， [200, 300)之间表示操作成功，否则表示操作失败 | int     |
| tagging  | 返回 Bucket 对象 Tagging 信息                            | Tagging |

## 删除存储桶标签

#### 功能说明

DELETE Bucket tagging 用于删除指定存储桶下已有的存储桶标签。

#### 方法原型

```
DeleteBucketTaggingResult deleteBucketTagging(DeleteBucketTaggingRequest request)throws CosXmlClientException, CosXmlServiceException;

void deleteBucketTaggingAsync(DeleteBucketTaggingRequest request, CosXmlResultListener cosXmlResultListener);

```

#### 请求示例

```
String bucket = "examplebucket-1250000000"; //格式：BucketName-APPID
DeleteBucketTaggingRequest deleteBucketTaggingRequest = new DeleteBucketTaggingRequest(bucket);
//设置签名校验 Host, 默认校验所有 Header
Set<String> headerKeys = new HashSet<>();
headerKeys.add("Host");
deleteBucketTaggingRequest.setSignParamsAndHeaders(null, headerKeys);
// 使用同步方法
try {
    DeleteBucketTaggingResult deleteBucketTaggingResult = cosXmlService.deleteBucketTagging(deleteBucketTaggingRequest);
} catch (CosXmlClientException e) {
    e.printStackTrace();
} catch (CosXmlServiceException e) {
    e.printStackTrace();
}

// 使用异步回调请求
cosXmlService.deleteBucketTaggingAsync(deleteBucketTaggingRequest, new CosXmlResultListener() {
    @Override
    public void onSuccess(CosXmlRequest request, CosXmlResult result) {
        DeleteBucketTaggingResult getBucketTaggingResult = (DeleteBucketTaggingResult)result;
    }

    @Override
    public void onFail(CosXmlRequest cosXmlRequest, CosXmlClientException clientException, CosXmlServiceException serviceException)  {

    }
});
```

#### 参数说明

| 参数名称 | 描述                                                         | 类型   |
| -------- | ------------------------------------------------------------ | ------ |
| bucket   | 被删除标签的存储桶，格式为 BucketName-APPID ，详情请参见 [命名规范](https://intl.cloud.tencent.com/document/product/436/13312) | String |

#### 返回结果说明

| 成员变量 | 类型 | 描述                                                     |
| -------- | ---- | -------------------------------------------------------- |
| httpCode | int  | HTTP Code， [200, 300)之间表示操作成功，否则表示操作失败 |
