# SetDomainServerCertificate {#doc_api_1013145 .reference}

调用SetDomainServerCertificate接口设置某域名下证书功能是否启用及修改证书信息。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Cdn&api=SetDomainServerCertificate)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetDomainServerCertificate|操作接口名，系统规定参数。取值：**SetDomainServerCertificate**

 |
|DomainName|String|是|www.yourdomain.com|指定证书所属加速域名，需属于https加速类型。

 |
|ServerCertificateStatus|String|是|on|HTTPS证书是否启用，取值**on**：启用；**off**：不启用，默认取值：**off**：不启用

 |
|ForceSet|String|否|1|设置为1时，忽略证书名称重复的校验，覆盖原有同名证书信息。

 |
|Region|String|否|cn-hangzhou|地区

 |
|CertName|String|否|myCert1|证书名称

 |
|ServerCertificate|String|否|xxxxxx|安全证书内容，不启用证书则无需输入，配置证书请输入证书内容。

 |
|PrivateKey|String|否|xxxxxxxx|私钥内容，不启用证书则无需输入，配置证书请输入私钥内容。

 |
|CertType|String|否|free|-   **upload**：上传证书
-   **cas**：证书中心证书
-   **free**：免费证书

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=SetDomainServerCertificate
&DomainName=www.yourdomain.com
&ServerCertificateStatus=on
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<APINAMEResponse>
  <RequestId>3DEF9962-AD9E-43A2-851B-0945684F9513</RequestId>
  <HostId>cdn.aliyuncs.com</HostId>
  <Code>InvalidDomain.NotFound</Code>
  <Message>The domain provided does not belong to you.</Message>
</APINAMEResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Message":"The domain provided does not belong to you.",
	"RequestId":"3DEF9962-AD9E-43A2-851B-0945684F9513",
	"HostId":"cdn.aliyuncs.com",
	"Code":"InvalidDomain.NotFound"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidServerCertificateStatus.ValueNotSupported|The specified value of parameter Enable is not supported.|指定的配置项值不合法，只能是on或off。|
|400|ServerCertificate.MissingParameter|An input parameter "ServerCertificate" that is mandatory for processing the request is not supplied.|参数“ServerCertificate”缺失。|
|400|PrivateKey.MissingParameter|An input parameter "PrivateKey" that is mandatory for processing the request is not supplied.|参数“PrivateKey”缺失。|
|400|InvalidCertificate|The Certificate you provided is malformed!|证书格式不正确。|
|400|InvalidPrivateKey|The Private Key you provided is malformed!|私钥格式不正确。|
|400|Certificate.MissMatch|The Private Key does not math the specified Certificate!|私钥不匹配该类证书。|
|400|InvalidCertificate.TooLong|The Certificate you provided is over the max length!|证书和私钥长度超出限制。|
|400|InvalidCertName.TooLong|The Certificate name you provided is over the max length 128!|证书名称不能超过128个字符.。|
|403|IllegalOperation|Illegal domain operate is not permitted.|非法操作。|
|400|Certificate.NotPermittedOff|Turn off certificate will change domain scheduling, please contact customer service|关闭证书将更改域调度，请与客服联系。|
|400|Certificate.SettedNotEffect|Certificate was successfully setted but does't take effect for protecting current service, please contact customer service|证书已成功安装但不保护当前服务生效，请联系客户服务|
|400|AuthenticationFailed|Authentication failed.|身份验证失败。|
|400|SetDomainServerCertificate.ParameterError|Parameters have error.|参数错误。|
|400|Certificate.NotFind|Not find the certificate info.|证书不存在。|
|400|Certificate.MissMatch|The certificate is not match the private key.|证书与私钥不匹配。|
|400|Certificate.StatusError|Certificate is not exist or its status is error.|证书不存在或证书状态错误。|
|400|DeleteFailed|Delete certificate is failed.|删除证书失败。|
|400|Certificate.Duplicated|The certificate name is duplicated.|证书重复。|
|400|Certificate.FormatError|The certificate format is error.|证书格式错误。|
|400|Certificate.StatusError|The certificate status is error.|证书状态错误。|
|400|Certificate.KeyNull|The private key is not null.|私钥不能为空。|
|400|Key.Malformed|The private key format is error.|私钥格式错误。|
|400|CertStorage.failed|The certificate storage failed.|证书保存失败。|
|400|CertificateContent.Duplicated|The certificate is already uploaded, please don't upload again.|证书已经上传，请不要再次上传。|
|400|Certificate.Expired|The certificate is expired.|证书过期了。|
|400|InvalidDomain.notOnline|The domain is not online, please check the domain status and try again later.|域名未在线，请检查域名状态，稍后再试。|
|400|Decode.Error|The certificate sslpub or sslpri decode error.|证书 sslpub 或 sslpri 解码错误。|
|400|sslPub.Error|The sslPub encoded failed.|sslPub 编码失败。|
|400|sslPri.Error|The sslPri encoded failed.|sslPri 编码失败。|
|400|DomainInSafeMode|This domain is in the safe mode. if you want to do this operation, please contact us!|此域名处于安全模式。如果您想做这个操作，请工单联系我们。|
|400|DomainInProtectedMode|This domain is in the protected mode. if you want to do this operation, please contact us!|此域名处于被保护模式。如果您想做这个操作，请联系我们。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Cdn)

