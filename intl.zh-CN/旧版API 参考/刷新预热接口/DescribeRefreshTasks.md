# DescribeRefreshTasks {#reference_fx1_lrz_5db .reference}

查询刷新、预热状态，是否在全网生效。

-   支持根据任务ID查询、URL查询。
-   taskid与objectpath都不指定，默认查3天内，第一页的数据（20条）。
-   Taskid与objectpath可以同时指定，逻辑与的关系。
-   只可查询3天内的数据。

## 请求参数 {#section_tbg_trz_5db .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|DescribeRefreshTasks| 系统规定参数。取值：

 DescribeRefreshTasks

 |
|DomainName|String|否|www.yourdomain.com| 域名。

 |
|EndTime|String|否|2017-12-22T08:00:00:00Z| 结束时间，格式例如：2017-01-01T12:12:20Z。

 |
|ObjectPath|String|否|[http://aaa.com/1.txt](http://aaa.com/1.txt)| 按路径查询，准确匹配。

 |
|ObjectType|String|否|file| 任务类型。

-   file
-   path
-   preload

当指定DomainName或TaskStatus时，该项为必填。

 |
|PageNumber|Integer|否|1| 取得第几页。

 取值范围：1~100000

 |
|PageSize|Integer|否|20| 分页大小。最大值：50

 取值范围：1~50之前的任意整数。：

 默认值：20

 |
|ResourceGroupId|String|否|your resourceGroupId|资源组ID。|
|StartTime|String|否|2017-12-21T08:00:00:00Z| 开始时间，格式例如：2017-01-01T12:12:20Z。

 |
|Status|String|否|Complete| 任务状态。

-   Complete（完成）
-   Refreshing（刷新中）
-   Failed（刷新失败）

 |
|TaskId|String|否|1234321| 按任务ID查询刷新状态。

 |

## 返回参数 {#section_svv_htz_5db .section}

|参数|类型|示例值|描述|
|:-|:-|:--|:-|
|Tasks| | | TaskItem组成的Task任务列表。

 |
|└TaskId|String|704225667| 任务ID。

 |
|└ObjectPath|String|[http://aaa.com/1.txt](http://aaa.com/1.txt)| 刷新对象路径。

 |
| └Status|String|Complete| 状态。取值：

-   Complete（完成）
-   Refreshing（刷新中）
-   Failed（刷新失败）
-   Pending（等待刷新）

 |
|└Process|String|100%| 进度百分比。

 |
| └ObjectType|String|file| 任务类型。

-   file
-   path
-   preload

 |
|└CreationTime|String|2014-11-27T08:23:22Z| 任务对象创建时间，UTC时间。

 |
| └Description|String|Internal Error| 刷新预热失败返回错误描述，目前包含三种错误：

-   Internal Error
-   Origin Timeout
-   Origin Return StatusCode 5XX

 |
|PageSize|Long|1| 整页大小。

 |
|PageNumber|Long|10| 页码。

 |
|TotalCount|Long|2| 总条数。

 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8| 请求ID。

 |

## 示例 {#section_ugl_x5z_5db .section}

**请求示例**

```
https://cdn.aliyuncs.com?&Action=DescribeRefreshTasks&ObjectPath=&PageNumber=1&PageSize=10&公共请求参数
```

**正常返回示例**

-   JSON格式

    ```
    {
        "PageNumber":1,
        "PageSize":10,
        "RequestId":"174F6032-AA26-470D-B90E-36F0EB205BEE",
        "Tasks":{
            "CDNTask":[
                {
                    "CreationTime":"2014-11-27T08:23:22Z",
                    "ObjectPath":"http://aaa.com/1.txt",
                    "ObjectType":"file",
                    "Process":"100%",
                    "Status":"Complete",
                    "TaskId":"704225667"
                },
                {
                    "CreationTime":"2014-11-27T08:18:38Z",
                    "ObjectPath":"http://bbb.com/1.txt",
                    "ObjectType":"file",
                    "Process":"100%",
                    "Status":"Complete",
                    "TaskId":"704222904"
                }
            ]
        },
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


