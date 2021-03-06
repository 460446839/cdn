# 配置CNAME域名解析

您可以通过阅读本文，了解域名解析和配置CNAME域名解析。

域名添加成功后，阿里云CDN会分配对应的CNAME地址。如果您想启用CDN加速服务，则需要将加速域名的DNS解析记录指向CNAME地址，访问加速域名的请求才能转发到CDN节点上，达到加速效果。（注意：由于Local DNS的解析记录存在缓存时间，因此配置了域名的CNAME解析记录之后CDN平台大约会延迟10分才会显示CNAME解析记录配置成功）

## 什么是域名解析

如果您是初次接触域名解析，您可能会有一些疑问，如“什么是域名解析”、“为什么要解析域名”、“如何进行域名解析”、“什么是A记录”、“什么是CNAME记录”、“CNAME记录与A记录的差别”。如果有这些疑问，请您参见[域名解析帮助文档](https://help.aliyun.com/document_detail/137913.html?spm=a2c6h.12873639.0.0.630d3022IYv3pG)。这篇文档对这些问题有很好的解释，建议您仔细阅读。

## 如何配置CDN的CNAME解析

如果您的域名是在阿里云/万网，请参见以下域名解析文档：[阿里云/万网配置流程](https://help.aliyun.com/document_detail/27144.html?spm=a2c4g.11186623.6.581.6eec4c07iOVflK)。

如果您的域名是在腾讯云（原DNSPod），请参见以下域名解析文档：[DNSPod配置流程](https://help.aliyun.com/document_detail/27145.html?spm=a2c6h.12873639.0.0.630d3022WAHNMm)。

如果您的域名是在新网，请参见以下域名解析文档：[新网配置流程](https://help.aliyun.com/document_detail/27146.html?spm=a2c4g.11186623.6.583.29d11fecNnxGbz)。

## 域名解析冲突

很多用户在配置CNAME记录的时候，出现了域名解析冲突的情况，这是因为在同一个域名解析服务商下，域名解析是存在冲突规则的，比如A记录和CNAME记录冲突，MX记录和CNAME记录冲突等，具体可以参见[域名解析记录冲突规则](https://help.aliyun.com/knowledge_detail/39787.html?spm=5176.11065259.1996646101.searchclickresult.33c240b5OixaWW)

|-|NS|CNAME|A|URL|MX|TXT|AAA|SRV|CAA|
|--|--|-----|--|---|--|---|---|---|---|
|NS|可重复|冲突|冲突|冲突|冲突|冲突|冲突|冲突|冲突|
|CNAME|冲突|可重复|冲突|冲突|冲突|冲突|冲突|冲突|冲突|
|A|冲突|冲突|可重复|冲突|不冲突|不冲突|不冲突|不冲突|不冲突|
|URL|冲突|冲突|冲突|冲突|不冲突|不冲突|冲突|不冲突|不冲突|
|MX|冲突|冲突|不冲突|不冲突|可重复|不冲突|不冲突|不冲突|不冲突|
|TXT|冲突|冲突|不冲突|不冲突|不冲突|可重复|不冲突|不冲突|不冲突|
|AAA|冲突|冲突|不冲突|冲突|不冲突|不冲突|可重复|不冲突|不冲突|
|SRV|冲突|冲突|不冲突|不冲突|不冲突|不冲突|不冲突|可重复|不冲突|
|CAA|冲突|冲突|不冲突|不冲突|不冲突|不冲突|不冲突|不冲突|可重复|

配置CNAME记录的过程中，常见的解析记录冲突有以下两种：

1.  CNAME记录和A记录冲突
    -   Q.如何处理

        需要删除A记录，然后再去配置CNAME记录。

    -   Q.删除A记录是否无法访问网站

        只要配置了CNAME记录以后，客户端的请求会请求到CDN上，然后CDN再去访问源站服务器，因此就没必要再配置A记录了。CNAME在CDN加速中的原理，请参见[工作原理](https://help.aliyun.com/document_detail/122172.html?spm=a2c4g.11186623.2.16.6eec4c07nNAfgE#concept-678821)。

2.  CNAME记录和MX记录冲突

    请参见[CNAME和MX冲突的解决方法](https://help.aliyun.com/knowledge_detail/39787.html?spm=5176.11065259.1996646101.searchclickresult.33c240b5OixaWW)。


## 验证CDN是否生效

按照[如何配置CDN的CNAME解析](#section_93d_04p_to2)中正确的步骤操作CNAME解析，如果CNAME解析正确，则CDN控制台会显示正常的”✅”符号。也可以参见[如何验证CDN节点是否生效](https://help.aliyun.com/knowledge_detail/40173.html)[如何通过浏览器的审查元素判断CDN缓存是否成功](https://help.aliyun.com/knowledge_detail/40193.html)

总览信息包括以下内容：

-   有感叹号表示未正常解析（图示中①）
-   有打钩符表示正常解析（图示中②）

![域名管理](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/2072367951/p132031.png)

如果控制台显示不正常的解析，则可能有以下几种原因：

-   确认配置的CNAME解析的记录值是否和CDN控制台获取的记录值一致，如不一致则解析失败。
-   配置完域名解析以后，运营商DNS的TTL还未更新，则需要耐心等待下，一般情况下TTL时间为10分钟，具体以解析配置的时候选择的TTL为准。
-   CDN服务会去全网检查加速域名是否解析到CDN，如果大部分区域已经解析，但是还是有个别地区没有解析的话，也会显示感叹号，需要全网解析生效以后才会显示正常。
-   有一种特殊情况是，用户配置域名解析的时候设置了解析路线，需求部分地区不走CDN加速。比如国内的解析路线是解析到CDN，海外的解析路线是A解析到服务器，这种情况下，因为海外没有解析到CDN，因此控制台没显示正常，但在这种需求场景下，不影响用户实际使用，如下图：

    ![解析路径](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/2072367951/p132035.png)


