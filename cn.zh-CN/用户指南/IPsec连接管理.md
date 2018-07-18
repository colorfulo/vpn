# IPsec连接管理 {#concept_hpr_byc_xdb .concept}

创建IPsec VPN网关和用户网关后，可以创建IPsec连接建立加密通信通道。

## 创建IPsec连接 {#section_mxd_fyc_xdb .section}

完成以下操作，创建IPsec连接：

1.  登录VPC管理控制台。
2.  在左侧导航栏，单击**VPN** \> **IPSec连接**。
3.  在IPsec连接页面，选择IPsec连接的地域。
4.  单击**创建IPsec连接**。
5.  根据以下信息配置IPsec连接，单击**确定**。

    |配置|说明|
    |:-|:-|
    |名称| IPsec连接的名称。

 名称在2-128个字符之间，以英文字母或中文开始，可包含数字，连字符（-）和下划线（\_）。

 |
    |VPN网关|选择待连接的VPN网关。|
    |用户网关|选择待连接的用户网关。|
    |本端网段|输入需要和本地IDC互连的VPC侧的网段，用于第二阶段协商。可以填写多个网段，网段之间用逗号分隔，例如192.168.1.0/24,192.168.2.0/24。**说明：** 只有IKE V2版本下才可以配置多网段。

|
    |对端网段|输入需要和VPC互连的本地IDC侧的网段，用于第二阶段协商。可以填写多个网段，网段之间用逗号分隔，例如172.10.1.0/24,172.10.2.0/24。**说明：** 只有IKE V2版本下才可以配置多网段。

|
    |是否立即生效|选择是否删除当前已协商成功的IPsec隧道并重新发起协商。    -   是：配置完成后立即进行协商。
    -   否：当有流量进入时进行协商。
|
    |高级配置：IKE配置|
    |预共享密钥|用于IPsec VPN网关与用户网关之间的身份认证。默认情况下会随机生成，也可以手动指定密钥。|
    |版本|选择IKE协议的版本。目前支持IKE V1和IKE V2，相对于IKE V1版本，IKE V2版本简化了SA的协商过程并且对于多网段的场景提供了更好的支持，所以建议选择IKE V2版本。|
    |协商模式|选择IKE V1版本的协商模式。    -   主模式（main）：协商过程安全性高。
    -   野蛮模式（aggressive）：协商快速且协商成功率高。
协商成功后两种模式的信息传输安全性相同。|
    |加密算法|选择第一阶段协商使用的的加密算法。支持aes、aes192、aes256、des和3des。|
    |认证算法|第一阶段协商使用的认证算法。支持sha1和md5。|
    |DH分组|选择第一阶段协商使用的的Diffie-Hellman密钥交换算法。|
    |SA生存周期（秒）|设置第一阶段协商出的SA的生存周期。默认值为86400秒。|
    |LocalId|作为IPsec VPN网关的标识，用于第一阶段的协商。默认值为VPN网关的公网IP地址。如果手动设置LocalId为FQDN格式，建议将协商模式改为野蛮模式（aggressive）。|
    |RemoteId|作为用户网关的标识，用于第一阶段的协商。默认值为用户网关的公网IP地址。如果手动设置RemoteId为FQDN格式，建议将协商模式改为野蛮模式（aggressive）。|
    |高级配置：IPSEC配置|
    |加密算法|选择第二阶段协商的加密算法。支持aes、aes192、aes256、des和3des。|
    |认证算法|选择第二阶段协商的认证算法。支持sha1和md5。|
    |DH分组|选择第二阶段协商的Diffie-Hellman密钥交换算法。|
    |SA生存周期（秒）|设置第二阶段协商出的SA的生存周期。默认值为86400秒。|


## 下载配置 {#section_ayd_fyc_xdb .section}

配置IPsec连接并协商成功后，您可以下载IPsec连接配置，将该配置加载到本地网关设备中。详情参见[本地网关配置](https://help.aliyun.com/document_detail/60045.html)。

完成以下操作，下载IPsec连接配置：

1.  登录VPC管理控制台。
2.  在左侧导航栏，单击**VPN** \> **IPSec连接**。
3.  在IPsec连接页面，选择IPsec连接的地域。
4.  单击目标IPsec连接**操作**列下的**下载配置**。

    下载配置中的RemotSubnet和LocalSubnet与创建IPsec连接时的本端网段和对端网段正好是相反的。因为从阿里云VPN网关的角度看，对端是本地IDC的网段，本端是阿里云侧的VPC网段；而从本地IDC的网关设备角度看，LocalSubnet就是指本地IDC的网段，RemotSubnet则是指阿里云VPC的网段。

    比如您在配置IPsec连接时，输入的本端网段为192.168.0.0/16，对端网段为172.16.0.0/12，下载的IPsec连接配置如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13351/3317_zh-CN.png)


## 编辑IPsec连接配置 {#section_eyd_fyc_xdb .section}

完成以下操作，编辑IPsec连接配置：

1.  登录VPC管理控制台。
2.  在左侧导航栏，单击**VPN** \> **IPSec连接**。
3.  在IPsec连接页面，选择IPsec连接的地域。
4.  单击目标IPsec连接**操作**列下的**编辑**。

## 删除IPsec连接 {#section_gyd_fyc_xdb .section}

完成以下操作，删除IPsec连接：

1.  登录VPC管理控制台。
2.  在左侧导航栏，单击**VPN** \> **IPSec连接**。
3.  在IPsec连接页面，选择IPsec连接的地域。
4.  单击目标IPsec连接**操作**列下的**删除**。
5.  在弹出的对话框，单击**确认**。

## 查看IPsec连接日志 {#section_jyd_fyc_xdb .section}

您可以查看仅一个月内的IPsec连接日志，通过日志信息排查IPsec连接过程中的问题。日志查询的时间周期为10分钟。

完成以下操作，查看IPsec连接日志：

1.  登录VPC管理控制台。
2.  在左侧导航栏，单击**VPN** \> **IPSec连接**。
3.  在IPsec连接页面，选择IPsec连接的地域。
4.  单击目标IPsec连接**操作**列下的**查看日志**。
5.  在弹出的页面，设置要查看的日志的时间，查看日志。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13359/3342_zh-CN.png)


