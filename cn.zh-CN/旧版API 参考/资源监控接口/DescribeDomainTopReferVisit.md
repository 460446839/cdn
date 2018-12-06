# DescribeDomainTopReferVisit {#reference_qls_jbn_vdb .reference}

获取加速域名某天的热门页面引用次数排名。

-   不指定StartTime时，默认读取过去1天的数据。
-   只支持一个域名，或当前用户下所有域名。
-   最多可获取最近90天的数据。

## 请求参数 {#section_nmz_kdn_vdb .section}

|参数|类型|是否必选|示例值|描述|
|Action|String|是|DescribeDomainTopReferVisit|系统规定参数。取值：DescribeDomainTopReferVisit|
|DomainName|String|否|www.yourdomain.com|只支持一个域名，若参数为空，默认返回所有加速域名合并后数据。|
|SortBy|String|否|pv| 排序方式。

 -   支持traf和pv。
-   默认值：pv

 |
|StartTime|String|否|2017-12-21T08:00:00:00Z| 获取数据起始时间点，北京时间。

 -   格式为：YYYY-MM-DD。
-   不写默认读取过去24小时数据。

 |

## 返回参数 {#section_lfx_qdn_vdb .section}

|参数|类型|示例值|描述|
|RequestId|String|95994621-8382-464B-8762-C708E73568D1|请求ID。|
|DomainName|String|test.com|加速域名信息。|
|StartTime|String|2015-11-28|查询指定日期。|
|TopReferList| | |全部热门ReferUrllist。|
|  └ReferDetail|String|live-hunantv.cdnpe.com|完整的ReferUrl地址。|
|  └VisitData|String|3|访问次数。|
|  └VisitProportion|Float|0.5|访问占比。|
|  └Flow|String|200| 流量。

 单位：byte

 |
|  └FlowProportion|Float|0.5|流量占比。|

## 示例 {#section_uz2_x1n_vdb .section}

**请求示例**

```

http://cdn.aliyuncs.com?Action=DescribeDomainTopReferVisit&DomainName=test.com
&StartTime=2015-11-28
&公共请求参数
```

**正常返回示例**

-   JSON格式

    ```
    {
        "DomainName":"test.com",
        "RequestId":"95994621-8382-464B-8762-C708E73568D1",
        "StartTime":"2015-11-28",
        "TopReferList":{
            "ReferList":[
                {
                    "ReferDetail":"-",
                    "VisitData":"229567"
                },
                {
                    "ReferDetail":"123.57.158.8",
                    "VisitData":"2496"
                },
                {
                    "ReferDetail":"live-hunantv.cdnpe.com",
                    "VisitData":"448"
                },
                {
                    "ReferDetail":"video.ccdemo.ccgslb.net",
                    "VisitData":"3"
                }
            ]
        }
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


