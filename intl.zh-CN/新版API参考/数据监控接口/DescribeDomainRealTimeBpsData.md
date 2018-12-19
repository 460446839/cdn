# DescribeDomainRealTimeBpsData {#reference1833 .reference}

获取域名1分钟粒度带宽数据。

**说明：** 

-   可以查询7天内的数据，单次查询StartTime和EndTime跨度不能超过24小时。
-   如果StartTime和EndTime均未指定，默认返回当前时间起一小时内的数据。

## 请求参数 { .section}

|参数|类型|是否必需|描述|
|--|--|----|--|
|Action|String|是|操作接口名，系统规定参数，取值：DescribeDomainRealTimeBpsData|
|DomainName|String|是|域名|
|StartTime|String|是|起始时间。-   日期格式按照ISO8601表示法，并使用UTC时间。
-   例如：2016-10-20T04:00:00Z。
-   不填默认查询从EndTime起一小时内的数据。

|
|EndTime|String|是|结束时间。-   日期格式按照ISO8601表示法，并使用UTC时间。
-   例如：2016-10-20T04:00:00Z.2016-10-20T04:00:00Z。
-   不填默认查询从StartTime起一小时内的数据。

|
|IspNameEn|String|是|运营商英文名，通过DescribeCdnRegionAndIsp接口获得，不传为所有运营商。|
|LocationNameEn|String|是|区域英文名，通过DescribeCdnRegionAndIsp接口获得，不传为所有区域。|

## 返回参数 { .section}

|名称|类型|描述|
|--|--|--|
|RequestId|String|请求Id|
|TimeStamp|String|数据时间戳。-   日期格式按照ISO8601表示法，并使用UTC时间。
-   例如：2016-10-20T04:00:00Z。

|
|Bps|Float|带宽数据，单位是bit/second。|

## 示例 { .section}

请求示例

```
https://cdn.aliyuncs.com/?Action=DescribeDomainRealTimeBpsData&DomainName=example.com&EndTime=2018-01-02T11%3A05%3A37Z&IspNameEn=telecom&LocationNameEn=beijing<公共请求参数>
```

返回示例

```language-json
{
   "Data":{
      "BpsModel":[
         {
            "TimeStamp":"2018-01-02T11:05:00Z",
            "Bps":16710625.733333332
         },
         {
            "TimeStamp":"2018-01-02T11:04:00Z",
            "Bps":59392614.8
         }
      ]
   },
   "RequestId":"B49E6DDA-F413-422B-B58E-2FA23F286726"
}

```

## 错误码 { .section}

|错误代码|错误信息|HTTP 状态码|描述|
|----|----|--------|--|
|InvalidTime.Malformed|时间参数格式不正确|400|时间参数不正确|
|InvalidDomainName.Malformed|域名参数未提供或找不到域名|400|域名参数不正确|

