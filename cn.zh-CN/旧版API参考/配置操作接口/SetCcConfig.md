# SetCcConfig {#doc_api_Cdn_SetCcConfig .reference}

调用SetCcConfig接口设置加速域名的CC防护功能、IP黑白名单设置。

**说明：** 

-   黑名单和白名单可同时支持。
-   IP黑名单当前支持IP网段添加。例如：127.0.0.1/24 24表示采用子网掩码中的前24位为有效位，即用32-24 = 8 bit来表示主机号，该子网可以容纳2^8-2 = 254 台主机。故127.0.0.1/24 表示的IP网段范围是：127.0.0.1~127.0.0.255。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Cdn&api=SetCcConfig)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetCcConfig|操作接口名，系统规定参数。取值：**SetCcConfig**。

 |
|DomainName|String|是|example.com|您的加速域名。

 |
|AllowIps|String|否|10.0.0.1%2F24%2C127.0.0.1%2F24|CC防护IP白名单。表示此IP列表不受限制，可以正常访问。

 |
|BlockIps|String|否|192.168.0.1%2F24|CC防护IP黑名单。表示此IP列表禁止访问，依赖CC功能开启。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|4C8BC316-91DA-4E99-93B1-65C311BFFB75|请求ID

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://cdn.aliyuncs.com?Action=SetCcConfig
&DomainName=example.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<APINAMEResponse>
  <RequestId>4C8BC316-91DA-4E99-93B1-65C311BFFB75</RequestId>
  <HostId>cdn.aliyuncs.com</HostId>
  <Code>InvalidDomain.NotFound</Code>
  <Message>The domain provided does not belong to you.</Message>
</APINAMEResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Message":"The domain provided does not belong to you.",
	"RequestId":"4C8BC316-91DA-4E99-93B1-65C311BFFB75",
	"HostId":"cdn.aliyuncs.com",
	"Code":"InvalidDomain.NotFound"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Cdn)

