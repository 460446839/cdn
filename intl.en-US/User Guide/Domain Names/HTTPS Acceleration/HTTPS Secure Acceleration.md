# HTTPS Secure Acceleration {#concept_rns_qvk_xdb .concept}

## Introduction {#section_ynt_mnl_xdb .section}

HTTPS \(Hyper Text Transfer Protocol over Secure Socket Layer\) is an HTTP channel designed to ensure security. It encapsulates HTTP with the SSL/TLS protocol, so the foundation of HTTPS security is SSL/TLS protocol.

HTTPS Acceleration Advantages:

-   Encrypt important information during transmission, avoiding attack-caused information leaking, such as session ID or cookies.
-   Perform the data integrity during transmission, preventing man-in-the-middle attack \(MITM\), such as DNS or contents being hijacked by third party.

Alibaba Cloud CDN provides HTTPS Secure acceleration. When you have uploaded certificate and secret keys after enabling HTTPS, so that you can check, disable, enable and edit the certificate.

## How it works {#section_pcc_snl_xdb .section}

The HTTPS Secure Acceleration encrypts your request to Alibaba Cloud CDN nodes. And the CDN nodes still follow your origin site's configuration to access resources in the origin site. We recommend you configure and enable HTTPS on your origin site, encrypting your full-link HTTPS acceleration.

Here is the HTTPS encryption process:

1.  You start an HTTPS request.
2.  The server generates a public key and a secret key \(self-made or apply from professional organization\).
3.  The server sends the public certificate to your side.
4.  You side verify the certificate.

    -   If the certificate is correct, a random number \(private key\) is generated and encrypted with the public key, and transferred to the server.
    -   If the certificate is incorrect, the SSL handshake fails.
    **Note:** The certificate verification includes: the certificate being within the period of validity, the reliability of certificate's CA, the certificate's public key being able to encrypt the number signature of the server's issuer, and the domain name on the server's certificate being matched with its real domain name.

5.  The server uses the previous secret key to decrypt and get the random number \(private key\).
6.  The server encrypt the transmitted data by using the private key.
7.  You side decrypt the encrypted server date by using private key, and eventually get the data.

## Notes {#section_z5h_xnl_xdb .section}

**About configuration** 

-   HTTPS secure acceleration is available in the following service types: Image and Small File, Download, Video, and Live Streaming Media.
-   HTTPS acceleration for wildcard domain names is available.
-   You can **Enable** or **Disable** HTTPS acceleration:
    -   Enable: you can modify the certificate. The system is compatible with all your HTTP and HTTPS requests by default. You can also customize **Forcible redirect** for original request method.
    -   Disable: the system will neither support HTTPS request nor save the certificate or secret key's information. You need to re-upload the certificate or secret key when you reopen the certificate.
-   You can check the certificate, but cannot check the secret key due to its importance. Make sure that you have taken care of certificate information.
-   Update your certificate with caution. The update will take effect in 1 minute.

**About billing**

HTTPS Secure Acceleration is a value-added service, so that you need to pay for the HTTPS requests. For more information, see HTTPS pricing.

**Note:** You need to pay for HTTTPS requests separately. Make sure that your account balance is sufficient , otherwise it may affect your CDN service.

**About certificate**

-   To enable acceleration domain name with the **HTTPS Secure Acceleration** feature, you need to upload the certificate and secret key in the `PEM` format.

    **Note:** As Alibaba Cloud CDN only adopts Nginx-based Tengine service, only the certificate in `PEM` format is available. For more information, see [Certificate Format](intl.en-US/User Guide/Domain Names/HTTPS Acceleration/Certificate Format.md#).

-   Only SSL/TLS handshake with SNI information is available.
-   The certificate you upload should be matched with your secret key, otherwise your verification may fail.
-   Secret key with a password is unavailable.

## Procedure {#section_p3r_l4l_xdb .section}

1.  Purchase a certificate. Only when you own the certificate that is matched with your domain name can you enable HTTPS Secure Acceleration. You can easily purchase Alibaba Cloud Certificate in the [SSL Certificate console](https://yundun.console.aliyun.com/?spm=5176.2020520110.aliyun_sidebar.19.3ff6ZSicZSiceU&p=cas#/cas/home), or apply for free certificate.
2.  Log on to the [CDN console](https://cdn.console.aliyun.com), and enter the **Domain Names** page. Select the domain name, and click **Manage**.
3.  In **HTTPS Configurations** \> **HTTPS Cert**, click **Modify**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/5134/155556935811410_en-US.png)
4.  In the HTTPS Settings dialogue, enable **HTTPS Secure**.
5.  Select your certificate type. You can choose **Alibaba Cloud**, **Custom** or **Free Cert**. Currently, only the `PEM` format is available.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/5134/155556935921687_en-US.png)

    -   You can choose the Alibaba Cloud Certificate. If you have no matched certificate in your list, choose custom certificate. You need to upload the certificate contents and secret key after setting the certificate name. This certificate will be saved in your Alibaba Cloud Security. You can check in [My Certificate](https://yundunnext.console.aliyun.com/?spm=5176.2020520156.aliyun_sidebar.23.421dDbMODbMOnB&p=cas#/overview/cn-hangzhou).
    -   You can also choose free certificate, namely, Alibaba Cloud CDN Digicert DV version SSL Free certificate. This free certificate is only available for Alibaba Cloud CDN service, and it can't be managed in the SSL Certificates service of Alibaba Cloud Security. This certificate is only used to enable HTTPS Secure Acceleration in CDN, and you cannot obtain its public and private keys for other use. After you choose to use the Free Cert type, it takes about 10 minutes for the certificate to be effective.
6.  Verify whether the certificate is effective. You can access resources by using HTTPS after the certificate becomes effective \(about 1 hour\). Green HTTPS mark indicates that you have established private connection with the website, and HTTPS secure acceleration has comes into effect.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/5134/15555693593701_en-US.png)


**Note:** About replacing your certificate:

-   If you want to change your certificate to free certificate or Alibaba Cloud certificate, re-choose the target certificate \(**Free Cert** or **Alibaba Cloud Cert** \) in the HTTPS Settings page.
-   If you want to change your certificate to custom certificate, choose **Custom** in the HTTPS Settings page. Enter the target certificate name and contents to the box of the window, then deliver it.

