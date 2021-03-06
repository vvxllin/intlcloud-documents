## 概述

本文将为您介绍请求出错时返回的错误码和对应错误信息。

## 错误响应

Content-Type：application/xml

对应 HTTP 状态码：3XX，4XX，5XX。特别的，对于 [PUT Object - Copy](https://intl.cloud.tencent.com/document/product/436/10881) 接口，即使 HTTP 状态码为200也有可能在响应体中包含错误。

#### 响应体

```xml
<?xml version='1.0' encoding='utf-8' ?>
<Error>
	<Code>string</Code>
	<Message>string</Message>
	<Resource>string</Resource>
	<RequestId>string</RequestId>
	<TraceId>string</TraceId>
</Error>
```

具体的节点描述如下：

节点名称（关键字）|父节点|描述|类型
---|---|---|---
Error|无|包含所有的错误信息|Container

**Container 节点 Error 的内容：**

节点名称（关键字）|父节点|描述|类型
---|---|---|---
Code|Error|错误码，用来定位唯一的错误条件和确定错误场景，具体错误码见下文|string
Message|Error|具体的错误信息|string
Resource|Error|请求的资源，存储桶地址或对象地址|string
RequestId|Error|每次请求发送时，服务端将会自动为请求生成一个 ID，遇到问题时，该 ID 能更快地协助 COS 定位问题|string
TraceId|Error|每次请求出错时，服务端将会自动为这个错误生成一个ID，遇到问题时，该 ID 能更快地协助 COS 定位问题|string

## 错误码列表

**3XX 类型错误**

| 错误码            | 描述                                                         | HTTP 状态码           |
| ----------------- | ------------------------------------------------------------ | --------------------- |
| PermanentRedirect | 该资源已经被永久改变了位置，请利用 HTTP Location 响应头部来重定向到正确的新位置 | 301 Moved Permanently |
| TemporaryRedirect | 该资源已经被临时改变了位置，请利用 HTTP Location 响应头部来重定向到正确的新位置 | 302 Moved Temporarily |
| Redirect          | 临时重定向                                                   | 307 Moved Temporarily |
| TemporaryRedirect | 在 DNS 更新期间，您将被临时重定向                            | 307 Moved Temporarily |

**4XX 类型错误**

| 错误码                              | 描述                                                         | HTTP 状态码                         |
| ----------------------------------- | ------------------------------------------------------------ | ----------------------------------- |
| AppendPositionErr                   | Append 操作时，对象长度和 Position 不一致                    | 400 Bad Request                     |
| AttachmentFull                      | ACL 和 Policy 数量到达上限                                   | 400 Bad Request                     |
| BadDigest                           | 提供的 Content-MD5 值与服务端收到的请求体的 MD5 哈希值不一致 | 400 Bad Request                     |
| EntityTooLarge                      | 上传的对象大小超过规定的最大值                               | 400 Bad Request                     |
| EntityTooSmall                      | 上传的对象大小不足规定的最小值，常见于分块上传               | 400 Bad Request                     |
| IncorrectNumberOfFilesInPostRequest | POST 请求每次只允许上传一个对象                              | 400 Bad Request                     |
| InvalidArgument                     | 请求参数不合法                                               | 400 Bad Request                     |
| InvalidBucketName                   | 存储桶名称不合法                                             | 400 Bad Request                     |
| InvalidCopySource                   | 不合法的复制对象源                                           | 400 Bad Request                     |
| InvalidDigest                       | 给定的 Content-MD5 值不合法                                  | 400 Bad Request                     |
| InvalidPart                         | 分块缺失                                                     | 400 Bad Request                     |
| InvalidPartOrder                    | 分块上传编号不连续                                           | 400 Bad Request                     |
| InvalidRegionName                   | 不合法的地域名                                               | 400 Bad Request                     |
| InvalidRequest                      | 请求不合法                                                   | 400 Bad Request                     |
| InvalidSHA1Digest                   | 请求内容 SHA1 校验不合法                                     | 400 Bad Request                     |
| InvalidURI                          | URI 不合法                                                   | 400 Bad Request                     |
| KeyTooLong                          | 对象键过长                                                   | 400 Bad Request                     |
| LifeCycleIdNotUnique                | 生命周期 ID 不唯一                                           | 400 Bad Request                     |
| LifeCycleRuleConflicted             | 生命周期设置存在冲突                                         | 400 Bad Request                     |
| MalformedPOSTRequest                | 该 POST 请求的请求体内容不合法                               | 400 Bad Request                     |
| MalformedXML                        | 请求体的 XML 格式不符合 XML 语法                             | 400 Bad Request                     |
| MissingAppid                        | 请求头中缺少 APPID                                           | 400 Bad Request                     |
| MissingContentMD5                   | 请求头中缺少 Content-MD5                                     | 400 Bad Request                     |
| MissingHost                         | 请求头中缺少 Host                                            | 400 Bad Request                     |
| MissingRequestBodyError             | 请求体缺失                                                   | 400 Bad Request                     |
| MultiBucketNotSupport               | 跨地域复制只能设置一个目的存储桶                             | 400 Bad Request                     |
| NoSuchVersion                       | 指定版本不存在                                               | 400 Bad Request                     |
| NotSupportedStorageClass            | 指定的存储类型不支持                                         | 400 Bad Request                     |
| ObjectNotAppendable                 | 指定的对象不能追加                                           | 400 Bad Request                     |
| PolicyFull                          | ACL 和 Policy 数量到达上限                                   | 400 Bad Request                     |
| RequestTimeOut                      | 读取数据超时，检查网络是否过慢或上传并发数过大               | 400 Bad Request                     |
| TooManyBuckets                      | 存储桶数目达到上限200                                       | 400 Bad Request                     |
| UnexpectedContent                   | 请求不支持相关内容                                           | 400 Bad Request                     |
| VerifyAlgorithmNotSupported         | 校验算法不支持                                               | 400 Bad Request                     |
| WebsiteURLInvalid                   | 自定义域名 URL 不合法                                        | 400 Bad Request                     |
| XMLSizeLimit                        | XML 长度超过限制                                             | 400 Bad Request                     |
| AccessDenied                        | 签名或者权限不正确，拒绝访问                                 | 403 Forbidden                       |
| ExpiredToken                        | 签名串已过期                                                 | 403 Forbidden                       |
| InvalidAccessKeyId                  | SecretID 不存在                                              | 403 Forbidden                       |
| InvalidObjectState                  | 请求内容与对象属性相冲突                                     | 403 Forbidden                       |
| InvalidObjectStorage                | 不合法的存储类型                                             | 403 Forbidden                       |
| RequestTimeTooSkewed                | 本地时间与服务器时间相差过大，超过15分钟                   | 403 Forbidden                       |
| SignatureDoesNotMatch               | 客户端计算的签名与 COS 服务端计算的签名不一致                | 403 Forbidden                       |
| NoSuchBucket                        | 指定的存储桶不存在                                           | 404 Not Found                       |
| NoSuchCopySource                    | 复制对象源不存在                                             | 404 Not Found                       |
| NoSuchCORSConfiguration             | 指定的跨域资源共享设置不存在                                 | 404 Not Found                       |
| NoSuchKey                           | 指定的对象键不存在                                           | 404 Not Found                       |
| NoSuchLifecycleConfiguration        | 指定的生命周期设置不存在                                     | 404 Not Found                       |
| NoSuchTagSet                        | 指定的标签集合不存在                                         | 404 Not Found                       |
| NoSuchUpload                        | 分块上传时指定的 UploadId 不存在                             | 404 Not Found                       |
| NoSuchWebsiteConfiguration          | 静态网站配置不存在                                           | 404 Not Found                       |
| MethodNotAllowed                    | 此资源不支持该 HTTP 方法                                     | 405 Method Not Allowed              |
| RestoreNonArchiveObject             | 不允许对非归档对象进行回热                                   | 405 Method Not Allowed              |
| BucketAlreadyExists                 | 指定的存储桶已存在                                           | 409 Conflict                        |
| BucketAlreadyOwnedByYou             | 指定的存储桶已存在且由当前帐户创建                           | 409 Conflict                        |
| BucketNotEmpty                      | 存储桶不为空                                                 | 409 Conflict                        |
| InvalidBucketState                  | 存储桶状态与操作请求冲突，例如版本控制管理与跨地域复制的冲突   | 409 Conflict                        |
| PathConflict                        | 存在同名对象的毫秒级并发冲突                                 | 409 Conflict                        |
| RestoreAlreadyInProgress            | 该对象正在回热中                                             | 409 Conflict                        |
| MissingContentLength                | Content-Length 请求头部缺失                                  | 411 Length Required                 |
| PreconditionFailed                  | 前置条件匹配失败                                             | 412 Precondition                    |
| InvalidRange                        | 请求的对象范围不合法                                         | 416 Requested Range Not Satisfiable |
| UnavailableForLegalReasons          | 因法律原因不可用                                             | 451 Unavailable For Legal Reasons   |

**5XX 类型错误**

| 错误码             | 描述                       | HTTP 状态码             |
| ------------------ | -------------------------- | ----------------------- |
| InternalErrror     | 服务端内部错误             | 500 Internal Server     |
| 403 Forbidden                       | Request has expired                   | 发起请求的时间超过了签名的有效时间，或者本地系统时间和所在时区的时间不一致。详情请参见 [常见问题](https://intl.cloud.tencent.com/zh/document/product/436/10687#.E8.B0.83.E7.94.A8-api-.E6.8E.A5.E5.8F.A3.E6.97.B6.EF.BC.8C.E5.87.BA.E7.8E.B0.E2.80.9Crequest-has-expired.E2.80.9D.E7.AD.89.E9.94.99.E8.AF.AF.E4.BF.A1.E6.81.AF.EF.BC.8C.E8.AF.A5.E5.A6.82.E4.BD.95.E5.A4.84.E7.90.86.EF.BC.9F) |
| NotImplemented     | 请求尚未实现               | 501 Not Implemented     |
| ServiceUnavailable | 服务暂不可用，请重试       | 503 Service Unavailable |
| SlowDown           | 请降低访问频率             | 503 Slow Down           |
