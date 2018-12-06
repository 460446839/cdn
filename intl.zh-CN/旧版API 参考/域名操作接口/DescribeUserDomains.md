# DescribeUserDomains {#reference_vys_stw_5db .reference}

查询用户名下所有的域名与状态。支持域名模糊匹配过滤和域名状态过滤。域名状态包括：

-   运行中（表示域名服务状态正常，可以使用）
-   已停止
-   配置中
-   配置失败
-   审核中
-   审核失败

## 请求参数 {#section_prx_dxw_5db .section}

|名称|类型|是否必须|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|DescribeUserDomains| 系统规定参数。取值：

 DescribeUserDomains

 |
|CdnType|String|否|web| cdn业务类型，多个用逗号隔开。

 |
|CheckDomainShow|Boolean|否|true| 是否显示审核状态域名。

 |
|DomainName|String|否|www.yourdomain.com| 域名模糊匹配过滤。

 |
|DomainSearchType|String|否|fuzzy\_match| 域名查询类型：

-   fuzzy\_match 模糊匹配
-   pre\_match 前匹配
-   suf\_match 后匹配
-   full\_match 完全匹配

默认值：fuzzy\_match

 |
|DomainStatus|String|否|online| 域名状态过滤。

 |
|FuncFilter|String|否|config| 过滤，支持config和unconfig。

-   config是开通funcid的。
-   unconfig是没有开通funcid的。

 |
|FuncId|String|否|98| funcid，如图片鉴黄功能98。

 |
|PageNumber|Integer|否|1| 取得第几页。

 取值范围：1~100000。

 |
|PageSize|Integer|否|20| 分页大小。

 取值范围：1~50之前的任意整数。

 最大值：50

 默认值：20

 |
|ResourceGroupId|String|否|your resourceGroupId| 资源组ID。

 |
|Sources|String|否|a.b.com| 根据回源地址查询。

 |

## 返回参数 {#section_jtq_2xw_5db .section}

|参数|类型|示例值|描述|
|:-|:-|:--|:-|
|RequestId|String|AA75AADB-5E25-4970-B480-EAA1F5658483| 请求ID。

 |
|PageNumber|Long|1| 返回数据的页码。

 |
|PageSize|Long|5| 整页大小。

 |
|TotalCount|Long|16| 总条数。

 |
|Domains| | | 域名列表信息。

 |
| └DomainName|String|onlytest.cdnpe.com| 加速域名名称。

 |
|└Cname|String|onlytest.cdnpe.com.w.alikunlun.net| 加速域名对应的CNAME域名。

 |
|└CdnType|String|video| 加速业务类型。取值范围：

-   web：图片小文件加速
-   download：大文件下载加速
-   video：视音频点播加速
-   livestream：直播流媒体加速
-   httpsdelivery：HTTPS安全加速

 |
|└DomainStatus|String|online| 加速域名状态。取值意义：

-   online：启用
-   offline：停用
-   configuring：配置中
-   configure\_failed：配置失败
-   checking：正在审核
-   check\_failed：审核失败

 |
|└GmtCreated|String|2015-10-28T09:31:59Z| 加速域名创建时间。

 |
|└GmtModified|String|2015-10-28T11:05:50Z| 加速域名修改时间。

 |
|└Description|String|audit failed| 审核失败原因。

 |
| └ResourceGroupId|String|abcd1234abcd1234| 资源组ID。

 |
|└SourceType|String|oss| 源站类型。

 |
|└SslProtocol|String|on| 开关。

 |
|└Sandbox|String|（空）| 沙箱。

 |
|└Sources|String|\{ “Source”: \[ “a.b.com” \] \}| 源站信息。

 |

## 示例 {#section_mwd_pcx_5db .section}

**请求示例**

```
https://cdn.aliyuncs.com?&Action=DescribeUserDomains&PageNumber=1&PageSize=5&DomainSearchType=fuzzy_match&公共请求参数
```

**正常返回示例**

-   JSON格式

    ```
    {
        "Domains":{
            "PageData":[
                {
                    "CdnType":"download",
                    "Description":"audit failed",
                    "DomainName":"image.ddd.cdnpe.com",
                    "DomainStatus":"configure_failed",
                    "GmtCreated":"2015-10-28T09:32:51Z",
                    "GmtModified":"2015-10-28T11:05:52Z",
                    "ResourceGroupId":"abcd1234abcd1234"
                },
                {
                    "CdnType":"web",
                    "DomainName":"aadda.cdnpe.com",
                    "DomainStatus":"configure_failed",
                    "GmtCreated":"2015-10-28T09:31:59Z",
                    "GmtModified":"2015-10-28T11:05:50Z",
                    "ResourceGroupId":"abcd1234abcd1234"
                },
                {
                    "CdnType":"video",
                    "Cname":"onlytest.cdnpe.com.w.alikunlun.net",
                    "DomainName":"onlytest.cdnpe.com",
                    "DomainStatus":"online",
                    "GmtCreated":"2015-10-23T09:30:00Z",
                    "GmtModified":"2015-10-27T06:26:34Z",
                    "ResourceGroupId":"abcd1234abcd1234"
                },
                {
                    "CdnType":"video",
                    "Cname":"test11.cdnpe.com.w.kunlunAr.com",
                    "DomainName":"test11.cdnpe.com",
                    "DomainStatus":"online",
                    "GmtCreated":"2015-10-23T09:23:20Z",
                    "GmtModified":"2015-10-23T09:23:29Z",
                    "ResourceGroupId":"abcd1234abcd1234"
                },
                {
                    "CdnType":"video",
                    "Cname":"test.aliyun.com.w.alikunlun.com",
                    "DomainName":"test.aliyun.com",
                    "DomainStatus":"online",
                    "GmtCreated":"2015-10-23T09:01:57Z",
                    "GmtModified":"2015-10-23T09:02:11Z",
                    "ResourceGroupId":"abcd1234abcd1234"
                }
            ]
        },
        "PageNumber":1,
        "PageSize":5,
        "RequestId":"AA75AADB-5E25-4970-B480-EAA1F5658483",
        "TotalCount":16
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


