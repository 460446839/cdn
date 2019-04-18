# Type 3: On-demand video/audio acceleration {#concept_oxm_q2f_xdb .concept}

## Scenarios {#section_rzd_2fk_xdb .section}

All kinds of video/audio websites, such as video websites for films and TV dramas, video websites for online education, video websites for news, short video-featured social websites, and audio websites and applications.

## Procedure {#section_hlr_mfk_xdb .section}

1.  Add CDN domains.

    See [Quick Start](../../../../intl.en-US/Quick Start/Quick start.md#). Make sure you select **Acceleration of on-demand video/audio** for the business type.

2.  Domain configuration

    After the domains are added, use the appropriate feature to configure the CDN domains based on your business needs. All domain configurations are optional. The following configurations are recommended for the **Acceleration of on-demand video/audio**.

    Recommended configurations

    -   [HTTPS Secure Acceleration](intl.en-US/User Guide/Domain Names/HTTPS Acceleration/HTTPS Secure Acceleration.md#): You only need to enable the secure acceleration mode and then upload the certificate and the private key for the CDN domains. You can also view, disable, enable and edit the certificate. For more information, see [Certificate format instructions](intl.en-US/User Guide/Domain Names/HTTPS Acceleration/Certificate Format.md#).
    -   [Cache configuration](intl.en-US/User Guide/Domain Names/Node Cache Settings/Cache Configuration.md#): This feature can be used to set the actions of a cache server against resources in different **directory paths** or with different **file name suffixes**. You can customize cache expiration rules for specified resources.
    -   Access control settings: ensure the security of the distributed content, and prevent unnecessary traffic losses from leeching or malicious requests.
        -   [Authentication configuration](intl.en-US/User Guide/Domain Names/Access Control Settings/Authentication configuration.md#): The URL authentication feature is implemented by collaboration between the Alibaba Cloud CDN nodes and client resource sites to provide a more secure and reliable way to protect origin server resources from theft.
        -   [efer anti-leech protection](intl.en-US/User Guide/Domain Names/Access Control Settings/Anti-leech.md#)
        -   [IP blacklist](intl.en-US/User Guide/Domain Names/Access Control Settings/IP Blacklist and Whitelist.md#)
    -   [Range back-to-origin](intl.en-US/User Guide/Domain Names/Video Service Configuration/Back-to-origin of range.md#): This feature can be used for reduced consumption of back-to-origin traffic and improved resource response time.
    -   [Drag/drop playback](intl.en-US/User Guide/Domain Names/Video Service Configuration/Drag__Drop Playback.md#): Enables random drag/drop playback in a video/audio on demand scenario.
    -   [URL prefetch](intl.en-US/User Guide/Refresh and Preload.md#): Proactively prefetches the content from the origin server to the L2 Cache node. You can directly hit the cache at the first visit to help relieve pressure on the origin server.
    -   For more features, see [Overview of domain configuration](intl.en-US/User Guide/Function overview.md#).

