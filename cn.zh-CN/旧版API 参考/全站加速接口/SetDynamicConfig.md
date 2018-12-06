# SetDynamicConfig {#reference_k2m_z25_vdb .reference}

全站加速，缓存规则的配置。

## 请求参数 {#section_cmm_kh5_vdb .section}

|参数|类型|是否必选|示例值|描述|
|Action|String|是|SetDynamicConfig|系统规定参数。取值：SetDynamicConfig|
|DomainName|String|是|www.yourdomain.com|您的加速域名。|
|DynamicCacheControl|String|否|no-cache| 特殊header头设置。

 -   根据Header中的Cache-Control字段，选择是否动态加速。多个空格隔开。
-   例如：no-cache no-store private

 |
|DynamicOrigin|String|否|http| 回源路由scheme，支持http、https和follow。

 不填时，默认值为http。

 |
|StaticPath|String|否|/img| 静态加速PATH。多个空格隔开。

 例如：\#path:/path/to/no\_dynamic\_route/.*.one*

 |
|StaticType|String|否|jpg| 静态加速文件后缀。

 例如： ..\(jpg¦htmp¦txt\)$

 |
|StaticUri|String|否|/img/a.jpg| 静态加速URI。多个空格隔开。

 例如：\#uri:/yyy/gggsssssssss/cxxxxxcc/a.txt

 |

## 返回参数 {#section_bc2_nh5_vdb .section}

|参数|类型|示例值|描述|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID|

## 示例 {#section_sz4_ctt_vdb .section}

**请求示例**

```

http://cdn.aliyuncs.com/?Action=SetDynamicConfig
&DomainName=www.macaron.org.cn
&StaticType=.*\.(jpg|htmp|txt)$
&StaticUri=/ya/bc
&公共请求参数
```

**正常返回示例**

-   JSON格式

    ```
    {
        "RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368"
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


