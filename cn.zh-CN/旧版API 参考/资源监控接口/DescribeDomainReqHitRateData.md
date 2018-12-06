# DescribeDomainReqHitRateData {#reference_x2l_hsm_vdb .reference}

获取加速域名的请求命中率（命中请求百分比）。

-   不指定StartTime和EndTime时，默认读取过去24小时的数据，同时支持按指定的起止时间查询，两者需要同时指定。
-   支持批量域名查询，多个域名可用逗号（半角）分隔。
-   最多可获取最近90天的数据。

## 请求参数 {#section_ijs_nsm_vdb .section}

|参数|类型|是否必选|示例值|描述|
|Action|String|是|DescribeDomainReqHitRateData|系统规定参数。取值：DescribeDomainReqHitRateData|
|DomainName|String|否|www.yourdomain.com|需要查询的加速域名，支持多个域名，不写代表所有。|
|EndTime|String|否|2017-12-22T08:00:00:00Z| -   结束时间需大于起始时间。
-   获日期格式按照ISO8601表示法，并使用UTC时间。
-   格式为：YYYY-MM-DDThh:mmZ。

 |
|Interval|String|否|300| -   查询数据的时间粒度。
-   支持300, 3600, 14400, 28800和86400秒。
-   不传和传的值不支持时，使用默认值300秒。

 |
|StartTime|String|否|2017-12-21T08:00:00:00Z| -   获取数据起始时间点。
-   日期格式按照ISO8601表示法，并使用UTC时间。
-   格式为：YYYY-MM-DDThh:mmZ。
-   最小数据粒度为5分钟。
-   不写默认读取过去24小时数据。

 |

## 返回参数 {#section_sb5_wsm_vdb .section}

|参数|类型|示例值|描述|
|DomainName|String|test.com|加速域名信息。|
|DataInterval|String|300|每条记录的时间间隔，以秒为单位。|
|StartTime|String|2015-12-10T20:00Z|开始时间。|
|EndTime|String|2015-12-10T21:00Z|结束时间。|
|ReqHitRateInterval| | |每个时间间隔的请求命中百分占比。|
|  └TimeStamp|String|2017-12-22T08:00:00:00Z|时间片起始时刻。|
|  └Value|String|100.0|详细使用数据。|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。|

## 示例 {#section_zmh_wnf_vdb .section}

**请求示例**

```

http://cdn.aliyuncs.com?Action=DescribeDomainReqHitRateData&DomainName=test.com
&StartTime=2015-12-10T20:00Z
&EndTime=2015-12-10T21:00Z
&公共请求参数
```

**正常返回示例**

-   JSON格式

    ```
    {
        "DataInterval":"300",
        "DomainName":"test.com",
        "EndTime":"2015-12-10T21:00Z",
        "ReqHitRateInterval":{
            "DataModule":[
                {
                    "TimeStamp":"2015-12-10T21:00:00Z",
                    "Value":"100.0"
                },
                {
                    "TimeStamp":"2015-12-10T20:35:00Z",
                    "Value":"100.0"
                },
                {
                    "TimeStamp":"2015-12-10T20:50:00Z",
                    "Value":"99.99932881437826"
                },
                {
                    "TimeStamp":"2015-12-10T20:05:00Z",
                    "Value":"100.0"
                },
                {
                    "TimeStamp":"2015-12-10T20:10:00Z",
                    "Value":"100.0"
                },
                {
                    "TimeStamp":"2015-12-10T20:55:00Z",
                    "Value":"100.0"
                },
                {
                    "TimeStamp":"2015-12-10T20:30:00Z",
                    "Value":"100.0"
                },
                {
                    "TimeStamp":"2015-12-10T20:25:00Z",
                    "Value":"100.0"
                },
                {
                    "TimeStamp":"2015-12-10T20:00:00Z",
                    "Value":"100.0"
                },
                {
                    "TimeStamp":"2015-12-10T20:40:00Z",
                    "Value":"100.0"
                },
                {
                    "TimeStamp":"2015-12-10T20:15:00Z",
                    "Value":"100.0"
                },
                {
                    "TimeStamp":"2015-12-10T20:45:00Z",
                    "Value":"100.0"
                },
                {
                    "TimeStamp":"2015-12-10T20:20:00Z",
                    "Value":"100.0"
                }
            ]
        },
        "RequestId":"5ADA5190-EE5B-4EF2-BE00-DC441B8D81DD",
        "StartTime":"2015-12-10T20:00Z"
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


