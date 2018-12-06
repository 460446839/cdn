# ListDomainsByLogConfigId {#reference_ffg_skf_vdb .reference}

查询应用某自定义日志格式的所有域名列表。

## 请求参数 {#section_w3c_qmf_vdb .section}

|参数|类型|是否必选|示例值|描述|
|Action|String|是|ListDomainsByLogConfigId|系统规定参数。取值：ListDomainsByLogConfigId|
|ConfigId|String|是|123|自定义配置ID。|
|Version|String|否|2014-11-11|API版本号。|

## 返回参数 {#section_wpp_xmf_vdb .section}

|参数|类型|示例值|描述|
|RequestId|String|94E3559F-7B6A-4A5E-AFFD-44E2A208A249|请求ID。|
|Domains|String|\[ “abc.com”, “a.b.c.com” \]|域名列表。|

## 示例 {#section_gmk_1nf_vdb .section}

**请求示例**

```
https://cdn.aliyuncs.com?Action=ListDomainsByLogConfigId&ConfigId=9732E117-8A37-49FD-A36F-ABBB87556CA7&公共请求参数
```

**正常返回示例**

-   JSON格式

    ```
    {
        "Domains":{
            "Domain":[
                "abc.com",
                "a.b.c.com"
            ]
        },
        "RequestId":"9732E117-8A37-49FD-A36F-ABBB87556CA7"
    }
    ```


**异常返回示例**

-   JSON格式

    ```
    {
        "Domains":{
            "Domain":[
                "abc.com",
                "a.b.c.com"
            ]
        },
        "RequestId":"9732E117-8A37-49FD-A36F-ABBB87556CA7"
    }
    ```


