# DescribeDomainPathData {#reference_cqp_j3n_vdb .reference}

获取加速域名路径级别的5分钟维度的监控数据，包括流量和访问次数。

**说明：** 域名带宽峰值10G以上，或GC6、GC7客户，可以通过工单或者服务经理申请使用。

-   不指定StartTime和EndTime时，默认读取过去24小时的数据，同时支持按指定的起止时间查询，两者需要同时指定。
-   不支持批量域名查询。
-   最多可获取最近30天的数据。
-   路径信息不支持模糊匹配。

## 请求参数 {#section_ujn_t3n_vdb .section}

|参数|类型|是否必选|示例值|描述|
|Action|String|是|DescribeDomainPathData|系统规定参数。取值：DescribeDomainPathData|
|DomainName|String|是|test.test.com|加速域名。|
|EndTime|String|否|2016-10-20T04:00:00Z| 结束时间。

 -   日期格式按照ISO8601表示法，并使用UTC时间。
-   起止时间和结束时间，间隔小于30天。
-   例如：2016-10-20T04:00:00Z。

 |
|PageNumber|Integer|否|1|页号，从1开始。|
|PageSize|Integer|否|20|每页大小，不超过1000。|
|Path|String|否|/path/| 路径，以/开头。

 -   不填表示查询所有路径。
-   如果路径是目录，需要以/结尾。

 |
|StartTime|String|否|2016-10-20T04:00:00Z| 开始时间。

 -   日期格式按照ISO8601表示法，并使用UTC时间。
-   例如：2016-10-20T04:00:00Z。

 |
|Version|String|否|2014-11-11|API版本。|

## 返回参数 {#section_gjg_z3n_vdb .section}

|参数|类型|示例值|描述|
|DomainName|String|test.test.com|加速域名。|
|StartTime|String|2017-09-30T17:00:00Z|起始时间。|
|EndTime|String|2017-09-30T17:00:00Z|结束时间。|
|PageSize|Integer|20|页大小。|
|PageNumber|Integer|1|当前页码，从1开始计数。|
|DataInterval|String|300| 时间间隔。

 单位：秒

 |
|TotalCount|Integer|2|路径带宽数据条数。|
|PathDataPerInterval| | |路径带宽数据列表。|
|  └Traffic|Integer|346|流量\(B\)。|
|  └Acc|Integer|10|访问次数。|
|  └Path|String|/path/|路径。|
|  └Time|String|2017-09-30T16:00:00Z|时间点。|

## 示例 {#section_uz2_x1n_vdb .section}

**请求示例**

```

 https://cdn.aliyuncs.com?Action=DescribeDomainPathData&DomainName=<DomainName>&PageNumber=1&PageSize=20
```

**正常返回示例**

-   JSON格式

    ```
    {
        "DataInterval":300,
        "EndTime":"2017-09-30T17:00:00Z",
        "PageNumber":1,
        "PageSize":20,
        "PathDataPerInterval":{
            "UsageData":[
                {
                    "Acc":10,
                    "Path":"/path/",
                    "Time":"2017-09-30T16:00:00Z",
                    "Traffic":346
                },
                {
                    "Acc":12,
                    "Path":"/path/",
                    "Time":"2017-09-30T16:05:00Z",
                    "Traffic":400
                }
            ]
        },
        "StartTime":"2017-09-30T16:00:00Z",
        "TotalCount":2
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


