---
keyword: How it works
---

# Architecture

The topic uses an example to illustrate the architecture of how Alibaba Cloud CDN works.

In this example, your accelerated domain is `www.a.com`. The following figure shows how Alibaba Cloud CDN works after receiving an HTTP request from a user in Beijing.

![How it works](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/5098/15670481654886_en-US.png)

1.  Before the user in Beijing sends a request to query a specific resource under `www.a.com`, the user initiates a domain name resolution request to the local DNS \(LDNS\) server.
2.  The LDNS server checks whether there is a DNS record corresponding to `www.a.com` in the local cache. If yes, the LDNS server directly returns the IP address to the user. If no, the LDNS server queries the IP address from the authorized DNS server.
3.  After the authorized DNS server resolves `www.a.com`, it returns the IP address to which the canonical name \(CNAME\) `www.a.tbcdn.com` is mapped to the LDNS server.
4.  The LDNS server sends a domain name resolution request to the Alibaba Cloud DNS scheduling system. The Alibaba Cloud DNS scheduling system then returns the IP address of the optimal node to the LDNS server.
5.  The LDNS server receives the resolved IP address returned by the Alibaba Cloud DNS scheduling system.
6.  The user receives the resolved IP address.
7.  The user initiates an access request to the received IP address.
    -   If the CDN node corresponding to the IP address \(Beijing node in this example\) has cached the requested resource, the CDN node directly returns the resource to the user, as shown in steps 7 and 8 in the figure. The request then ends.
    -   If the CDN node corresponding to the IP address \(Beijing node in this example\) has not cached the resource, the CDN node retrieves the resource from the origin server. After the CDN node retrieves the resource, it automatically caches the resource according to the user-defined caching policies and also returns the resource to the user, as shown in the figure. The request then ends. For more information about how to configure a caching policy, see [Cache settings](/intl.en-US/Domain Management/Cache settings/Create a cache expiration rule.md).

