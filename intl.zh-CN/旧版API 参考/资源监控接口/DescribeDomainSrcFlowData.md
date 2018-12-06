# DescribeDomainSrcFlowData {#reference_ihj_44m_vdb .reference}

获取加速域名的回源流量监控数据，单位：bits。

-   不指定StartTime和EndTime时，默认读取过去24小时的数据，同时支持按指定的起止时间查询，两者需要同时指定。
-   支持批量域名查询，多个域名可用逗号（半角）分隔。
-   最多可获取最近90天的数据。

## 请求参数 {#section_w3t_tqm_vdb .section}

|参数|类型|是否必选|示例值|描述|
|Action|String|是|DescribeDomainSrcFlowData|系统规定参数。取值：DescribeDomainSrcFlowData|
|DomainName|String|否|www.yourdomain.com| -   若参数为空，默认返回所有加速域名合并后数据。
-   可输入需要查询的加速域名。
-   支持批量域名查询，多个域名用逗号（半角）分隔。

 |
|EndTime|String|否|2017-12-22T08:00:00:00Z| -   结束时间需大于起始时间。
-   获日期格式按照ISO8601表示法，并使用UTC时间。
-   格式为：YYYY-MM-DDThh:mmZ。

 |
|FixTimeGap|String|否|false|是否补零。|
|Interval|String|否|300|时间间隔。|
|StartTime|String|否|2017-12-21T08:00:00:00Z| -   获取数据起始时间点。
-   日期格式按照ISO8601表示法，并使用UTC时间。
-   格式为：YYYY-MM-DDThh:mmZ。
-   最小数据粒度为5分钟。
-   不写默认读取过去24小时数据。

 |
|TimeMerge|String|否|true|是否时间合并。|
|Version|String|否|2014-11-11|API版本。|

## 返回参数 {#section_wgn_2rm_vdb .section}

|参数|类型|示例值|描述|
|DomainName|String|test.com|加速域名信息。|
|DataInterval|String|300|每条记录的时间间隔，以秒为单位。|
|StartTime|String|2015-12-10T20:00Z|开始时间。|
|EndTime|String|2015-12-10T21:00Z|结束时间。|
|SrcFlowDataPerInterval| | |每个时间间隔的回源流量数据。|
|  └TimeStamp|String|2017-12-22T08:00:00:00Z|时间片起始时刻。|
|  └Value|String|0|详细使用数据。|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。|

## 示例 {#section_zmh_wnf_vdb .section}

**请求示例**

```

http://cdn.aliyuncs.com?Action=DescribeDomainSrcFlowData&DomainName=test.com
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
        "RequestId":"A666D44F-19D6-490E-97CF-1A64AB962C57",
        "SrcFlowDataPerInterval":{
            "DataModule":[
                {
                    "TimeStamp":"2015-12-10T21:00:00Z",
                    "Value":"0"
                },
                {
                    "TimeStamp":"2015-12-10T20:35:00Z",
                    "Value":"0"
                },
                {
                    "TimeStamp":"2015-12-10T20:50:00Z",
                    "Value":"33886"
                },
                {
                    "TimeStamp":"2015-12-10T20:05:00Z",
                    "Value":"0"
                },
                {
                    "TimeStamp":"2015-12-10T20:10:00Z",
                    "Value":"0"
                },
                {
                    "TimeStamp":"2015-12-10T20:55:00Z",
                    "Value":"0"
                },
                {
                    "TimeStamp":"2015-12-10T20:30:00Z",
                    "Value":"0"
                },
                {
                    "TimeStamp":"2015-12-10T20:25:00Z",
                    "Value":"0"
                },
                {
                    "TimeStamp":"2015-12-10T20:00:00Z",
                    "Value":"0"
                },
                {
                    "TimeStamp":"2015-12-10T20:40:00Z",
                    "Value":"0"
                },
                {
                    "TimeStamp":"2015-12-10T20:15:00Z",
                    "Value":"0"
                },
                {
                    "TimeStamp":"2015-12-10T20:45:00Z",
                    "Value":"0"
                },
                {
                    "TimeStamp":"2015-12-10T20:20:00Z",
                    "Value":"0"
                }
            ]
        },
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


