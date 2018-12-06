# DeleteCdnDomain {#reference_tw3_cly_5db .reference}

删除已添加的加速域名。

**说明：** 

-   请慎重操作（建议在进行域名删除前到域名解析服务商处恢复域名A记录），以免导致删除操作后此域名不可访问。
-   DeleteCdnDomain调用成功后将删除本条加速域名的全部相关记录，对于仅需要暂停使用该加速域名，推荐StopCdnDomain接口。

## 请求参数 {#section_f3c_4ly_5db .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|DeleteCdnDomain|系统规定参数。取值：

DeleteCdnDomain|
|DomainName|String|是|www.yourdomain.com| 要删除的CDN的域名。

 |
|ResourceGroupId|String|否|your resourceGroupId| 资源组ID。

 |

## 返回参数 {#section_pqc_xly_5db .section}

|参数|类型|示例值|描述|
|:-|:-|:--|:-|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID|

## 示例 {#section_tgd_fmy_5db .section}

**请求示例**

```
http://cdn.aliyuncs.com?Action=DeleteDomain&DomainName=test.com&公共请求参数
```

**正常返回示例**

-   JSON格式

    ```
    {
        "RequestId":"94E3559F-7B6A-4A5E-AFFD-44E2A208A249"
    }
    ```


**异常返回示例**

-   JSON格式

    ```
    {
        "Code":"InternalError",
        "HostId":"cdn.aliyuncs.com",
        "Message":"The request processing has failed due to some unknown error.",
        "RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
    }
    ```


