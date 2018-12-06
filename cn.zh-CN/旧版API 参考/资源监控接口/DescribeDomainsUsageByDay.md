# DescribeDomainsUsageByDay {#reference_p5q_dvm_vdb .reference}

获取加速域名天粒度监控统计数据。

-   不指定StartTime和EndTime时，默认读取过去7的数据，同时支持按指定的起止时间查询，两者需要同时指定。
-   只支持一个域名，或当前用户下所有域名。
-   最多可获取最近90天的数据。

## 请求参数 {#section_zyh_vvm_vdb .section}

|参数|类型|是否必选|示例值|描述|
|Action|String|是|DescribeDomainsUsageByDay|系统规定参数。取值：DescribeDomainsUsageByDay|
|DomainName|String|否|www.yourdomain.com|需要查询的加速域名，只支持一个域名，不写代表当前用户下所有域名。|
|EndTime|String|否|2017-12-22T08:00:00:00Z| -   结束时间需大于起始时间。
-   使用北京时间。
-   格式为：YYYY-MM-DD。

 |
|StartTime|String|否|2017-12-21T08:00:00:00Z| -   获取数据起始时间点。
-   使用北京时间。
-   格式为：YYYY-MM-DD。

 |

## 返回参数 {#section_jgt_1wm_vdb .section}

|参数|类型|示例值|描述|
|RequestId|String|C88EF8ED-72F0-45EA-9E86-95114E224FC5|请求ID。|
|DomainName|String|test.com|加速域名信息。|
|DataInterval|String|86400|每条记录的时间间隔，固定值1天。|
|StartTime|String|2015-12-01|开始时间。|
|EndTime|String|2015-12-02|结束时间。|
|UsageByDays| | |每个时间间隔统计数据。|
|  └TimeStamp|String|2017-12-22T08:00:00:00Z|时间片起始时刻。|
|  └BytesHitRate|String|97.46250599529726|命中率。|
|  └Qps|String|7.466354166666667|每秒访问量。|
|  └RequestHitRate|String|70.24770071912111|请求命中率。|
|  └MaxBps|String|1.050307709E8|带宽峰值。|
|  └MaxBpsTime|String|2015-12-01 01:20|带宽峰值时刻。|
|  └MaxSrcBps|String|2015-12-01 22:30|回源带宽峰值。|
|  └TotalAccess|String|645093|总访问量。|
|  └MaxSrcBpsTime|String|2015-12-01 22:30|回源带宽峰值时刻。|
|  └TotalTraffic|String|564300099309|总流量。|
|UsageTotal| | |汇总数据。|
|  └BytesHitRate|String|97.03110726801242|命中率。|
|  └RequestHitRate|String|69.92610837438424|请求命中率。|
|  └MaxBps|String|1.0747912780000001E8|带宽峰值。|
|  └MaxBpsTime|String|2015-12-02 23:55|带宽峰值时刻。|
|  └MaxSrcBps|String|2015-12-02 17:20|回源带宽峰值。|
|  └TotalAccess|String|1319500|总访问量。|
|  └MaxSrcBpsTime|String|2015-12-02 17:20|回源带宽峰值时刻。|
|  └TotalTraffic|String|1117711832100|总流量。|

## 示例 {#section_zmh_wnf_vdb .section}

**请求示例**

```

http://cdn.aliyuncs.com?Action=DescribeDomainsUsageByDay&DomainName=test.com
&StartTime=2015-11-29
&EndTime=2015-11-30
&公共请求参数
```

**正常返回示例**

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


