# DescribeDomainFileSizeProportionData {#reference_mxw_wdn_vdb .reference}

获取加速域名最小1小时粒度的文件大小占比统计。

-   不指定StartTime和EndTime时，默认读取过去24小时的数据，同时支持按指定的起止时间查询，两者需要同时指定。
-   只支持一个域名，或当前用户下所有域名。
-   最多可获取最近90天的数据。

## 请求参数 {#section_nnl_b2n_vdb .section}

|参数|类型|是否必选|示例值|描述|
|Action|String|是|DescribeDomainFileSizeProportionData|系统规定参数。取值：DescribeDomainFileSizeProportionData|
|DomainName|String|否|test.test.com|需要查询的加速域名，只支持一个域名，不写代表当前用户下所有域名。|
|EndTime|String|否|2015-11-30T05:40Z| -   结束时间需大于起始时间。
-   获日期格式按照ISO8601表示法，并使用UTC时间。
-   格式为：YYYY-MM-DDThh:mmZ。

 |
|StartTime|String|否|2015-11-30T01:33Z| 获取数据起始时间点。

 -   日期格式按照ISO8601表示法，并使用UTC时间。
-   格式为：YYYY-MM-DDThh:mmZ。
-   最小数据粒度为1小时。
-   不写默认读取过去24小时数据。

 |

## 返回参数 {#section_s1w_g2n_vdb .section}

|参数|类型|示例值|描述|
|RequestId|String|23ACE7E2-2302-42E3-98F8-E5E697FD86C3|请求ID。|
|DomainName|String|test.test.com|加速域名。|
|DataInterval|String|3600|每条记录的时间间隔，固定值1小时或1天。|
|StartTime|String|2015-11-30T01:33Z|获取数据起始时间点。|
|EndTime|String|2015-11-30T05:40Z|获取数据结束时间点。|
|FileSizeProportionDataInterval| | |每个时间间隔的每秒访问数据。|
|  └TimeStamp|String|2015-11-30T03:00:00Z|时间片起始时刻。|
|  └Value| | |各文件大小占比数据list。|
|    └FileSize|String|<50K|文件大小。|
|    └Proportion|String|0.01|比例。|

## 示例 {#section_uz2_x1n_vdb .section}

**请求示例**

```

http://cdn.aliyuncs.com?Action=DescribeDomainFileSizeProportionData&DomainName=test.com
&StartTime=2015-11-30T01:33Z
&EndTime=2015-11-30T05:40Z
&公共请求参数
```

**正常返回示例**

-   JSON格式

    ```
    {
        "DataInterval":"3600",
        "DomainName":"test.com",
        "EndTime":"2015-11-30T05:40Z",
        "FileSizeProportionDataInterval":{
            "UsageData":[
                {
                    "TimeStamp":"2015-11-30T03:00:00Z",
                    "Value":{
                        "FileSizeProportionData":[
                            {
                                "FileSize":"<1M",
                                "Proportion":"7.91"
                            },
                            {
                                "FileSize":"<20K",
                                "Proportion":"0.137"
                            },
                            {
                                "FileSize":"<5K",
                                "Proportion":"64.544"
                            },
                            {
                                "FileSize":">1M",
                                "Proportion":"21.334"
                            },
                            {
                                "FileSize":"<10K",
                                "Proportion":"0.01"
                            },
                            {
                                "FileSize":"<50K",
                                "Proportion":"0.02"
                            },
                            {
                                "FileSize":"<100K",
                                "Proportion":"6.046"
                            }
                        ]
                    }
                },
                {
                    "TimeStamp":"2015-11-30T04:00:00Z",
                    "Value":{
                        "FileSizeProportionData":[
                            {
                                "FileSize":"<1M",
                                "Proportion":"4.564"
                            },
                            {
                                "FileSize":"<20K",
                                "Proportion":"0.645"
                            },
                            {
                                "FileSize":"<5K",
                                "Proportion":"69.746"
                            },
                            {
                                "FileSize":">1M",
                                "Proportion":"18.534"
                            },
                            {
                                "FileSize":"<10K",
                                "Proportion":"0.01"
                            },
                            {
                                "FileSize":"<50K",
                                "Proportion":"0.068"
                            },
                            {
                                "FileSize":"<100K",
                                "Proportion":"6.432"
                            }
                        ]
                    }
                },
                {
                    "TimeStamp":"2015-11-30T02:00:00Z",
                    "Value":{
                        "FileSizeProportionData":[
                            {
                                "FileSize":"<1M",
                                "Proportion":"16.066"
                            },
                            {
                                "FileSize":"<20K",
                                "Proportion":"0.07"
                            },
                            {
                                "FileSize":"<5K",
                                "Proportion":"52.842"
                            },
                            {
                                "FileSize":">1M",
                                "Proportion":"26.43"
                            },
                            {
                                "FileSize":"<10K",
                                "Proportion":"0.018"
                            },
                            {
                                "FileSize":"<50K",
                                "Proportion":"0.026"
                            },
                            {
                                "FileSize":"<100K",
                                "Proportion":"4.547"
                            }
                        ]
                    }
                },
                {
                    "TimeStamp":"2015-11-30T05:00:00Z",
                    "Value":{
                        "FileSizeProportionData":[
                            {
                                "FileSize":"<1M",
                                "Proportion":"4.521"
                            },
                            {
                                "FileSize":"<20K",
                                "Proportion":"1.551"
                            },
                            {
                                "FileSize":"<5K",
                                "Proportion":"68.254"
                            },
                            {
                                "FileSize":">1M",
                                "Proportion":"18.625"
                            },
                            {
                                "FileSize":"<10K",
                                "Proportion":"0.631"
                            },
                            {
                                "FileSize":"<50K",
                                "Proportion":"0.026"
                            },
                            {
                                "FileSize":"<100K",
                                "Proportion":"6.392"
                            }
                        ]
                    }
                }
            ]
        },
        "RequestId":"23ACE7E2-2302-42E3-98F8-E5E697FD86C3",
        "StartTime":"2015-11-30T01:33Z"
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


