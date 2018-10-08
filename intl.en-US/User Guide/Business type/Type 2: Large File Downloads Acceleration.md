# Type 2: Large File Downloads Acceleration {#concept_bpk_f2f_xdb .concept}

## Use cases {#section_oqv_g2f_xdb .section}

Distribution of large static website or application files, such as game installation packages `.apk`, application update files`.rar`, patch files, and audio and video files. Suitable for download sites and audio and video applications.

## Procedure {#section_wkw_h2f_xdb .section}

1.  Add CDN domains

    See [Quick Start](../../../../reseller.en-US/Quick Start/Quick start.md#). Make sure you select **Acceleration of large file downloads** for the business type.

2.  Domain configuration

    After the domains are added, use the appropriate feature to configure the CDN domains based on your business needs. All domain configurations are optional. The following configurations are recommended for the **Acceleration of large file downloads**.

    Recommended configurations

    -   [HTTPS Secure Acceleration](reseller.en-US/User Guide/Domain Names/HTTPS Acceleration/HTTPS Secure Acceleration.md#), you You only need to enable the secure acceleration mode and then upload the certificate and the private key for the CDN domains. You can also view, disable and edit the certificate. For more information, see [Certificate format instructions](reseller.en-US/User Guide/Domain Names/HTTPS Acceleration/Certificate Format.md#).
    -   [Cache configuration](reseller.en-US/User Guide/Domain Names/Node Cache Settings/Cache Configuration.md#): This feature can be used to set the actions of a cache server against resources in different **directory paths** and with different **file name suffixes**. You can customize cache expiration rules for specified resources.
    -   Access control settings: ensure the security of the distributed content, and prevent unnecessary traffic losses from leeching or malicious requests.
        -   [Refer anti-leech protection](reseller.en-US/User Guide/Domain Names/Access Control Settings/Anti-leech.md#)
        -   [IP blacklist](reseller.en-US/User Guide/Domain Names/Access Control Settings/IP Blacklist and Whitelist.md#)
    -   [Range back-to-origin](reseller.en-US/User Guide/Domain Names/Video Service Configuration/Back-to-origin of range.md#): This feature can be used for reduced consumption of back-to-origin traffic and improved resource response time.
    -   [URL prefetch](reseller.en-US/User Guide/Cache refresh.md#): Proactively prefetches the content from the origin server to the L2 Cache node. You can directly hit the cache at the first visit to help relieve pressure on the origin server.
    -   For more features, see [Overview of domain configuration](reseller.en-US/User Guide/Function overview.md#).

