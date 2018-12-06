# DescribeDomainSrcBpsData {#reference_ldq_2vl_vdb .reference}

获取加速域名的回源带宽监控数据，单位：bit/second。

-   不指定StartTime和EndTime时，默认读取过去24小时的数据，同时支持按指定的起止时间查询，两者需要同时指定。
-   支持批量域名查询，多个域名用逗号（半角）分隔。
-   最多可获取最近90天的数据。

## 请求参数 {#section_ijp_tnm_vdb .section}

|参数|类型|是否必选|示例值|描述|
|Action|String|是|DescribeDomainSrcBpsData|系统规定参数。取值：DescribeDomainSrcBpsData|
|DomainName|String|否|www.yourdomain.com| -   若参数为空，默认返回所有加速域名合并后数据。
-   可输入需要查询的加速域名。
-   支持批量域名查询，多个域名用逗号（半角）分隔。

 |
|EndTime|String|否|2017-12-12T20:00Z| -   结束时间需大于起始时间。
-   获日期格式按照ISO8601表示法，并使用UTC时间。
-   格式为：YYYY-MM-DDThh:mmZ。

 |
|FixTimeGap|String|否|false|下载时补零。|
|Interval|String|否|300|时间间隔。|
|StartTime|String|否|2017-12-10T20:00Z| -   获取数据起始时间点。
-   日期格式按照ISO8601表示法，并使用UTC时间。
-   格式为：YYYY-MM-DDThh:mmZ。
-   最小数据粒度为5分钟。
-   不写默认读取过去24小时数据。

 |
|TimeMerge|String|否|on| 取值范围：

 -   on：默认值，每条记录的时间间隔会根据时间跨度做合并。
-   off：返回5分钟粒度数据，最大时间跨度为31天。

 |
|Version|String|否|2014-11-11|API版本号。|

## 返回参数 {#section_dyz_24m_vdb .section}

|参数|类型|示例值|描述|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。|
|DomainName|String|yourdomain.com|加速域名信息。|
|StartTime|String|2017-12-10T20:00Z|开始时间。|
|EndTime|String|2017-12-12T20:00Z|结束时间。|
|DataInterval|String|300|每条记录的时间间隔，以秒为单位。|
|SrcBpsDataPerInterval| | |每个时间间隔的回源带宽数据。|
|  └TimeStamp|String|2017-12-10T20:45:00Z|时间片起始时刻。|
|  └Value|String|500|详细使用数据。|

## 示例 {#section_zmh_wnf_vdb .section}

**请求示例**

```

http://cdn.aliyuncs.com?Action=DescribeDomainSrcBpsData&DomainName=test.com
&StartTime=2017-12-10T20:00Z
&EndTime=2017-12-10T21:00Z
&公共请求参数
```

**正常返回示例**

-   JSON格式

    ```
    {
        "DataInterval":"300",
        "DomainName":"test.com",
        "EndTime":"2017-12-10T21:00Z",
        "RequestId":"7CBCD6AD-B016-42E5-AE0B-B3731DE8F755",
        "SrcBpsDataPerInterval":{
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
                    "Value":"821"
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
        "StartTime":"2017-12-10T20:00Z"
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


