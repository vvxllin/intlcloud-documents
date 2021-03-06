## 1. API Description
API domain name: vod.tencentcloudapi.com.  
This API categorizes media resources;
* This does not affect the existing media resource categories. If you need to modify a category, call the [media file properties modifying API](/document/product/266/31762).
* One category can have up to 4 levels.
* One category can have up to 500 sub-categories.  
Default API request rate limit: 100 requests/sec.

## 2. Input Parameters
The following parameters are required for requesting this API, including action-specific parameters and common parameters. For more information about common parameters for all requests, see [Common Request Parameters](/document/api/266/31756).

| Parameter name | Required | Type | Description |
|---------|---------|---------|---------|
| Action | Yes | String | Common parameter; the name of this API: CreateClass |
| Version | Yes | String | Common parameter; the version of this API: 2018-07-17 |
| Region | No | String | Common parameter; optional for this API |
| ParentId | Yes | Integer | Parent category ID. For a first-level category, enter -1. |
| ClassName | Yes | String | Category name. Length range: 1-64 characters. |
| SubAppId | No | Integer | ID of the VOD [sub-application](/document/product/266/14574). Input the ID of the sub-application that has the desired resources; otherwise, leave it blank. |
## 3. Output Parameters
| Parameter name | Type | Description |
|---------|---------|---------|
| ClassId | Integer | Category ID |
| RequestId | String | The ID of the request. Each request returns a unique ID. The RequestId is required to troubleshoot issues. |

## 4. Sample
### Sample 1. Creating a Video Category
#### Input Sample Code
```
https://vod.tencentcloudapi.com/?Action=CreateClass
&ParentId=-1
&ClassName=First-level Category 1
&SubAppId=1
&<Common request parameter>
```
#### Output Sample Code
```
{
  "Response": {
    "ClassId": 1,
    "RequestId": "38bac707-7f64-42fa-9369-cdddcc36550d"
  }
}
```
## 5. Developer Resources
### API Explorer
**API Explorer is a tool that provides ease of use in requesting APIs, authenticating identities, generating SDK and exploring APIs in Tencent Cloud environment.**
* [API 3.0 Explorer](https://console.cloud.tencent.com/api/explorer?Product=vod&Version=2018-07-17&Action=CreateClass)

### SDK
TencentCloud API 3.0 integrates software development toolkits (SDKs) that support various programming languages to make it easier for you to call the APIs.
* [Tencent Cloud SDK 3.0 for Python](https://github.com/TencentCloud/tencentcloud-sdk-python)
* [Tencent Cloud SDK 3.0 for Java](https://github.com/TencentCloud/tencentcloud-sdk-java)
* [Tencent Cloud SDK 3.0 for PHP](https://github.com/TencentCloud/tencentcloud-sdk-php)
* [Tencent Cloud SDK 3.0 for Go](https://github.com/TencentCloud/tencentcloud-sdk-go)
* [Tencent Cloud SDK 3.0 for NodeJS](https://github.com/TencentCloud/tencentcloud-sdk-nodejs)
* [Tencent Cloud SDK 3.0 for .NET](https://github.com/TencentCloud/tencentcloud-sdk-dotnet)

### TCCLI
* [Tencent Cloud CLI 3.0](https://cloud.tencent.com/document/product/440/6176)

## 6. Error Codes
The following error codes are API business logic-related. For other error codes, see [Common Error Codes](/document/api/267/20461#.E5.85.AC.E5.85.B1.E9.94.99.E8.AF.AF.E7.A0.81).

| Error Code | Description |
|---------|---------|
| FailedOperation.ClassLevelLimitExceeded | The operation is failed: The number of category levels exceeds the limit. |
| FailedOperation.ClassNameDuplicate | The operation is failed: The category name already exists. |
| FailedOperation.ParentIdNoFound | The operation is failed: The category does not exist. |
| FailedOperation.SubclassLimitExceeded | The operation is failed: The number of subcategories exceeds the limit. |
| InternalError | The error is caused internally. |
| InvalidParameterValue.ClassName | The name specified for the class is invalid. |
| InvalidParameterValue.ParentId | The Parent ID provided is invalid. |

