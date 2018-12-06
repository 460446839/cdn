# DescribeUserCustomLogConfig {#reference_lyx_thf_vdb .reference}

获取用户所有自定义日志配置信息。

## 请求参数 {#section_anm_whf_vdb .section}

|参数|类型|是否必选|示例值|描述|
|Action|String|是|DescribeUserCustomLogConfig|系统规定参数。取值：DescribeUserCustomLogConfig|
|Version|String|否|2014-11-11|API版本号。|

## 返回参数 {#section_qh4_ckf_vdb .section}

|参数|类型|示例值|描述|
|RequestId|String|94E3559F-7B6A-4A5E-AFFD-44E2A208A249|请求ID。|
|ConfigIds|String|\[ “c3bb2c78-2915-4d5a-b6a1-557789255555”, “25473b84-d598-498e-b148-f23d0a255555”, “1f1e6c6e-6701-4193-ae4d-54bf3e555555” \]|日志配置ID。|

## 示例 {#section_x5y_fkf_vdb .section}

**请求示例**

```
https://cdn.aliyuncs.com?Action=DescribeUserCustomLogConfig&公共请求参数
```

**正常返回示例**

-   JSON格式

    ```
    {
        "ConfigIds":{
            "ConfigId":[
                "c3bb2c78-2915-4d5a-b6a1-557789255555",
                "25473b84-d598-498e-b148-f23d0a255555",
                "1f1e6c6e-6701-4193-ae4d-54bf3e555555"
            ]
        },
        "RequestId":"95D5B69F-8AEC-419B-8F3A-612B35032B0D"
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


