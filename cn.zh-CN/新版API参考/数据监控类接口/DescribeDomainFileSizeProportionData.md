# DescribeDomainFileSizeProportionData {#doc_api_Cdn_DescribeDomainFileSizeProportionData .reference}

调用DescribeDomainFileSizeProportionData获取加速域名最小1小时粒度的文件大小占比统计。

 **调用该接口前，请您注意：** 

-   不指定StartTime和EndTime时，默认读取过去24小时的数据；同时指定StartTime和EndTime时，按指定的起止时间查询。
-   只支持获取一个域名或当前用户下所有域名的数据。
-   最多可获取最近90天的数据。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Cdn&api=DescribeDomainFileSizeProportionData&type=RPC&version=2018-05-10)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeDomainFileSizeProportionData|操作接口名，系统规定参数。取值：**DescribeDomainFileSizeProportionData**。

 |
|DomainName|String|是|test.test.com|需要查询的加速域名，只支持一个域名。

 如果参数为空，查询当前用户下所有域名。

 |
|EndTime|String|否|2015-11-30T05:40Z|获取数据结束时间点。

 -   结束时间需大于起始时间。
-   日期格式按照ISO8601表示法，并使用UTC时间。
-   格式为：YYYY-MM-DDThh:mm:ssZ。

 |
|StartTime|String|否|2015-11-30T01:33Z|获取数据起始时间点，不写默认读取过去24小时数据。

 -   日期格式按照ISO8601表示法，并使用UTC时间。
-   格式为：YYYY-MM-DDThh:mm:ssZ。
-   最小数据粒度为1小时。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|DataInterval|String|3600|每条记录的时间间隔，单位为秒，固定值1小时（3600秒）或1天（86400秒）。

 |
|DomainName|String|test.test.com|加速域名。

 |
|EndTime|String|2015-11-30T05:40Z|获取数据结束时间点。

 |
|FileSizeProportionDataInterval| | |每个时间间隔的每秒访问数据。

 |
|UsageData| | |每个时间间隔的每秒访问数据。

 |
|TimeStamp|String|2015-11-30T03:00:00Z|时间片起始时刻。

 |
|Value| | |各文件大小占比数据list。

 |
|FileSizeProportionData| | |各文件大小占比数据list。

 |
|FileSize|String|<50K|文件大小类型。

 |
|Proportion|String|0.01|占比使用数据。

 |
|RequestId|String|23ACE7E2-2302-42E3-98F8-E5E697FD86C3|请求ID。

 |
|StartTime|String|2015-11-30T01:33Z|获取数据起始时间点。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}
http://cdn.aliyuncs.com?Action=DescribeDomainFileSizeProportionData
&DomainName=test.com
&StartTime=2015-11-30T01:33Z
&EndTime=2015-11-30T05:40Z
&<公共请求参数>
```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeDomainFileSizeProportionDataResponse>
	  <DataInterval>3600</DataInterval>
	  <RequestId>23ACE7E2-2302-42E3-98F8-E5E697FD86C3</RequestId>
	  <FileSizeProportionDataInterval>
		    <UsageData>
			      <Value>
				        <FileSizeProportionData>
					          <FileSize>&lt;1M</FileSize>
					          <Proportion>7.91</Proportion>
				        </FileSizeProportionData>
				        <FileSizeProportionData>
					          <FileSize>&lt;20K</FileSize>
					          <Proportion>0.137</Proportion>
				        </FileSizeProportionData>
				        <FileSizeProportionData>
					          <FileSize>&lt;5K</FileSize>
					          <Proportion>64.544</Proportion>
				        </FileSizeProportionData>
				        <FileSizeProportionData>
					          <FileSize>&gt;1M</FileSize>
					          <Proportion>21.334</Proportion>
				        </FileSizeProportionData>
				        <FileSizeProportionData>
					          <FileSize>&lt;10K</FileSize>
					          <Proportion>0.01</Proportion>
				        </FileSizeProportionData>
				        <FileSizeProportionData>
					          <FileSize>&lt;50K</FileSize>
					          <Proportion>0.02</Proportion>
				        </FileSizeProportionData>
				        <FileSizeProportionData>
					          <FileSize>&lt;100K</FileSize>
					          <Proportion>6.046</Proportion>
				        </FileSizeProportionData>
			      </Value>
			      <TimeStamp>2015-11-30T03:00:00Z</TimeStamp>
		    </UsageData>
		    <UsageData>
			      <Value>
				        <FileSizeProportionData>
					          <FileSize>&lt;1M</FileSize>
					          <Proportion>4.564</Proportion>
				        </FileSizeProportionData>
				        <FileSizeProportionData>
					          <FileSize>&lt;20K</FileSize>
					          <Proportion>0.645</Proportion>
				        </FileSizeProportionData>
				        <FileSizeProportionData>
					          <FileSize>&lt;5K</FileSize>
					          <Proportion>69.746</Proportion>
				        </FileSizeProportionData>
				        <FileSizeProportionData>
					          <FileSize>&gt;1M</FileSize>
					          <Proportion>18.534</Proportion>
				        </FileSizeProportionData>
				        <FileSizeProportionData>
					          <FileSize>&lt;10K</FileSize>
					          <Proportion>0.01</Proportion>
				        </FileSizeProportionData>
				        <FileSizeProportionData>
					          <FileSize>&lt;50K</FileSize>
					          <Proportion>0.068</Proportion>
				        </FileSizeProportionData>
				        <FileSizeProportionData>
					          <FileSize>&lt;100K</FileSize>
					          <Proportion>6.432</Proportion>
				        </FileSizeProportionData>
			      </Value>
			      <TimeStamp>2015-11-30T04:00:00Z</TimeStamp>
		    </UsageData>
		    <UsageData>
			      <Value>
				        <FileSizeProportionData>
					          <FileSize>&lt;1M</FileSize>
					          <Proportion>16.066</Proportion>
				        </FileSizeProportionData>
				        <FileSizeProportionData>
					          <FileSize>&lt;20K</FileSize>
					          <Proportion>0.07</Proportion>
				        </FileSizeProportionData>
				        <FileSizeProportionData>
					          <FileSize>&lt;5K</FileSize>
					          <Proportion>52.842</Proportion>
				        </FileSizeProportionData>
				        <FileSizeProportionData>
					          <FileSize>&gt;1M</FileSize>
					          <Proportion>26.43</Proportion>
				        </FileSizeProportionData>
				        <FileSizeProportionData>
					          <FileSize>&lt;10K</FileSize>
					          <Proportion>0.018</Proportion>
				        </FileSizeProportionData>
				        <FileSizeProportionData>
					          <FileSize>&lt;50K</FileSize>
					          <Proportion>0.026</Proportion>
				        </FileSizeProportionData>
				        <FileSizeProportionData>
					          <FileSize>&lt;100K</FileSize>
					          <Proportion>4.547</Proportion>
				        </FileSizeProportionData>
			      </Value>
			      <TimeStamp>2015-11-30T02:00:00Z</TimeStamp>
		    </UsageData>
		    <UsageData>
			      <Value>
				        <FileSizeProportionData>
					          <FileSize>&lt;1M</FileSize>
					          <Proportion>4.521</Proportion>
				        </FileSizeProportionData>
				        <FileSizeProportionData>
					          <FileSize>&lt;20K</FileSize>
					          <Proportion>1.551</Proportion>
				        </FileSizeProportionData>
				        <FileSizeProportionData>
					          <FileSize>&lt;5K</FileSize>
					          <Proportion>68.254</Proportion>
				        </FileSizeProportionData>
				        <FileSizeProportionData>
					          <FileSize>&gt;1M</FileSize>
					          <Proportion>18.625</Proportion>
				        </FileSizeProportionData>
				        <FileSizeProportionData>
					          <FileSize>&lt;10K</FileSize>
					          <Proportion>0.631</Proportion>
				        </FileSizeProportionData>
				        <FileSizeProportionData>
					          <FileSize>&lt;50K</FileSize>
					          <Proportion>0.026</Proportion>
				        </FileSizeProportionData>
				        <FileSizeProportionData>
					          <FileSize>&lt;100K</FileSize>
					          <Proportion>6.392</Proportion>
				        </FileSizeProportionData>
			      </Value>
			      <TimeStamp>2015-11-30T05:00:00Z</TimeStamp>
		    </UsageData>
	  </FileSizeProportionDataInterval>
	  <DomainName>test.com</DomainName>
	  <EndTime>2015-11-30T05:40Z</EndTime>
	  <StartTime>2015-11-30T01:33Z</StartTime>
</DescribeDomainFileSizeProportionDataResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"DataInterval":"3600",
	"RequestId":"23ACE7E2-2302-42E3-98F8-E5E697FD86C3",
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
	"DomainName":"test.com",
	"EndTime":"2015-11-30T05:40Z",
	"StartTime":"2015-11-30T01:33Z"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|MissingParameter|StartTime and EndTime can not be single.|开始时间与结束时间均为必填。|
|400|InvalidStartTime.Malformed|Specified StartTime is malformed.|起始时间格式错误。日期格式请参考所调用API的帮助文档说明。|
|400|InvalidEndTime.Malformed|Specified EndTime is malformed.|结束时间格式错误。日期格式请参考所调用API的帮助文档说明。|
|400|InvalidEndTime.Mismatch|Specified EndTime does not math the specified start time.|请检查时间设置是否正确，结束时间不能小于或等于开始时间。|
|400|InvalidStartTime.ValueNotSupported|The specified value of parameter StartTime is not supported.|开始时间设置错误，请检查更新后重试。|
|400|InvalidDomainName.ValueNotSupported|The specified value of parameter DomainName only support one or empty value.|参数DomainName可以为空或最多1个域名。|

访问[错误中心](https://error-center.aliyun.com/status/product/Cdn)查看更多错误码。

