# PushObjectCache {#reference_xv3_mpz_5db .reference}

将源站的内容主动预热到L2 Cache节点上，用户首次访问可直接命中缓存，缓解源站压力。

支持post请求，参数用form表单。

限制条件：

-   同一个 ID 每天最多提交刷新预热类请求数量为URL：2000条。

    **说明：** 目前不支持目录级别的预热。

-   刷新预热类接口包含 RefreshObjectCaches 刷新接口和 PushObjectCache 预热接口。

## 请求参数 {#section_t2d_2qz_5db .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|PushObjectCache| 系统规定参数。取值：

 PushObjectCache

 |
|ObjectPath|String|是|abc.com/image/1.png| 输入示例：abc.com/image/1.png，多个URL之间需要用换行符（\\n或\\r\\n）分隔。

 |
|Area|String|否|domestic|预热区域，取值：domestic、overseas|

## 返回参数 {#section_pvn_qqz_5db .section}

|参数|类型|示例值|描述|
|:-|:-|:--|:-|
|PushTaskId|String|95248880| 预热返回的任务ID，多个任务ID用逗号（半角）分隔。

 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8| 请求ID。

 |

## 示例 {#section_add_xqz_5db .section}

**请求示例**

```
https://cdn.aliyuncs.com?&Action=PushObjectCache&ObjectPath=test.test.com/test.txt&ObjectType=File&公共请求参数
```

**正常返回示例**

-   JSON格式

    ```
    {
        "PushTaskId":"95248880",
        "RequestId":"E5BD4B50-7A02-493A-AE0B-97B9024B4135"
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


