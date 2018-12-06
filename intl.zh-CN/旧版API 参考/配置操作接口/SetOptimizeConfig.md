# SetOptimizeConfig {#reference_ar2_cvf_vdb .reference}

设置页面优化功能，开启后可以删除 html，内嵌 javascript 和 css 中的注释以及重复的空白符；这样可以有效地去除页面的冗余内容，减小文件体积，提高加速分发效率。

## 请求参数 {#section_awn_fvf_vdb .section}

|参数|类型|是否必选|示例值|描述|
|Action|String|是|SetOptimizeConfig|系统规定参数。取值：SetOptimizeConfig|
|DomainName|String|是|www.macaron.org.cn|要设置页面优化功能的加速域名。|
|Enable|String|是|On| 配置页面优化功能的开启或关闭。

 取值：On、Off

 |

## 返回参数 {#section_krq_qvf_vdb .section}

|参数|类型|示例值|描述|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID|

## 示例 {#section_sgh_cwf_vdb .section}

**请求示例**

```

http://cdn.aliyuncs.com/?Action=SetOptimizeConfig
&Enable=on
&DomainName=www.macaron.org.cn
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

