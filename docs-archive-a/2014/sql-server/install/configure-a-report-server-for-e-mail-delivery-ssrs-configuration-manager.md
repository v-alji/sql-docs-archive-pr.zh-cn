---
title: 将报表服务器配置为电子邮件传递 (SSRS Configuration Manager) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], distributing
- report servers [Reporting Services], e-mail delivery
- remote SMTP service [Reporting Services]
- distributing reports [Reporting Services], e-mail
- CDO
- Collaboration Data Objects
- SMTP settings [Reporting Services]
- e-mail [Reporting Services]
- sending reports
- mail [Reporting Services]
- local SMTP service [Reporting Services]
ms.assetid: b838f970-d11a-4239-b164-8d11f4581d83
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3122dbbb5debc90afa73ca0f8ab0d8e23d38a0ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588262"
---
# <a name="configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager"></a><span data-ttu-id="804d6-102">针对电子邮件传递配置报表服务器（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="804d6-102">Configure a Report Server for E-Mail Delivery (SSRS Configuration Manager)</span></span>


  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="804d6-103">包括电子邮件传递扩展插件，以便可以通过电子邮件分发报表。</span><span class="sxs-lookup"><span data-stu-id="804d6-103">includes an e-mail delivery extension so that you can distribute reports through e-mail.</span></span> <span data-ttu-id="804d6-104">根据定义电子邮件订阅的方式，传递可能由通知、链接、附件或嵌入报表组成。</span><span class="sxs-lookup"><span data-stu-id="804d6-104">Depending on how you define the e-mail subscription, a delivery might consist of a notification, link, attachment, or embedded report.</span></span> <span data-ttu-id="804d6-105">电子邮件传递扩展插件可与现有的邮件服务器技术一起使用。</span><span class="sxs-lookup"><span data-stu-id="804d6-105">The e-mail delivery extension works with your existing mail server technology.</span></span> <span data-ttu-id="804d6-106">邮件服务器必须是 SMTP 服务器或转发器。</span><span class="sxs-lookup"><span data-stu-id="804d6-106">The mail server must be an SMTP server or forwarder.</span></span> <span data-ttu-id="804d6-107">报表服务器通过操作系统提供的协作数据对象 (CDO) 库 (cdosys.dll) 连接到 SMTP 服务器。</span><span class="sxs-lookup"><span data-stu-id="804d6-107">The report server connects to an SMTP server through Collaboration Data Objects (CDO) libraries (cdosys.dll) that are provided by the operating system.</span></span>  
  
 <span data-ttu-id="804d6-108">默认情况下，未配置报表服务器电子邮件传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="804d6-108">The report server e-mail delivery extension is not configured by default.</span></span> <span data-ttu-id="804d6-109">必须使用 Reporting Services 配置管理器最低配置此扩展插件。</span><span class="sxs-lookup"><span data-stu-id="804d6-109">You must use the Reporting Services Configuration Manager to minimally configure the extension.</span></span> <span data-ttu-id="804d6-110">若要设置高级属性，必须编辑 `RSReportServer.config` 文件。</span><span class="sxs-lookup"><span data-stu-id="804d6-110">To set advanced properties, you must edit the `RSReportServer.config` file.</span></span> <span data-ttu-id="804d6-111">如果无法将报表服务器配置为使用此扩展插件，则可以将报表传递到共享文件夹。</span><span class="sxs-lookup"><span data-stu-id="804d6-111">If you cannot configure the report server to use this extension, you can deliver reports to a shared folder instead.</span></span> <span data-ttu-id="804d6-112">有关详细信息，请参阅 [File Share Delivery in Reporting Services](../../reporting-services/subscriptions/file-share-delivery-in-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="804d6-112">For more information, see [File Share Delivery in Reporting Services](../../reporting-services/subscriptions/file-share-delivery-in-reporting-services.md).</span></span>  
  
||  
|-|  
|[!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="804d6-113">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]本机模式</span><span class="sxs-lookup"><span data-stu-id="804d6-113">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode</span></span>|  
  
 
  
##  <a name="configuration-requirements"></a><a name="bkmk_configuration_requirements"></a><span data-ttu-id="804d6-114">配置要求</span><span class="sxs-lookup"><span data-stu-id="804d6-114">Configuration Requirements</span></span>  
  
-   <span data-ttu-id="804d6-115">报表服务器电子邮件传递在协作数据对象 (CDO) 上实现，且需要本地或远程的简单邮件传输协议 (SMTP) 服务器或 SMTP 转发器。</span><span class="sxs-lookup"><span data-stu-id="804d6-115">Report server e-mail delivery is implemented on Collaboration Data Objects (CDO) and requires a local or remote Simple Mail Transfer Protocol (SMTP) server or SMTP forwarder.</span></span> <span data-ttu-id="804d6-116">所有 Windows 操作系统都不支持 SMTP。</span><span class="sxs-lookup"><span data-stu-id="804d6-116">SMTP is not supported on all Windows operating systems.</span></span> <span data-ttu-id="804d6-117">如果使用的是基于 Itanium 的 Windows Server 2008 版本，则也不支持 SMTP。</span><span class="sxs-lookup"><span data-stu-id="804d6-117">If you are using the Itanium-based edition of Windows Server 2008, SMTP is not supported.</span></span> <span data-ttu-id="804d6-118">有关通过 CDO 提供的配置选项的详细信息，请参阅 MSDN 上的 [Configuration CoClass](https://go.microsoft.com/fwlink/?LinkId=98237) （配置 CoClass）。</span><span class="sxs-lookup"><span data-stu-id="804d6-118">For more information about configuration options provided through CDO, see [Configuration CoClass](https://go.microsoft.com/fwlink/?LinkId=98237) on MSDN.</span></span>  
  
-   <span data-ttu-id="804d6-119">报表服务器服务帐户必须对 SMTP 服务器拥有权限才能发送邮件。</span><span class="sxs-lookup"><span data-stu-id="804d6-119">The Report Server service account must have permission on the SMTP server to send mail.</span></span>  
  
-   <span data-ttu-id="804d6-120">电子邮件传递扩展插件在电子邮件附件中使用 UTF-8 编码。</span><span class="sxs-lookup"><span data-stu-id="804d6-120">The e-mail delivery extension uses UTF-8 encoding in e-mail attachments.</span></span> <span data-ttu-id="804d6-121">您无法修改此编码；HTML 呈现扩展插件仅支持 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="804d6-121">You cannot modify the encoding; the HTML rendering extension only supports UTF-8.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="804d6-122">默认电子邮件传递扩展插件不支持给待发邮件进行数字签名或加密。</span><span class="sxs-lookup"><span data-stu-id="804d6-122">The default e-mail delivery extension does not provide support for digitally signing or encrypting outgoing mail messages.</span></span>  
  
 
  
##  <a name="configuring-a-report-server-for-local-or-remote-smtp-service"></a><a name="bkmk_configure_for_local_or_remote_SMTP"></a><span data-ttu-id="804d6-123">为本地或远程 SMTP 服务配置报表服务器</span><span class="sxs-lookup"><span data-stu-id="804d6-123">Configuring a Report Server for Local or Remote SMTP Service</span></span>  
 <span data-ttu-id="804d6-124">可以使用本地 SMTP 服务或远程 SMTP 服务器或转发器来支持电子邮件传递。</span><span class="sxs-lookup"><span data-stu-id="804d6-124">You can use a local SMTP service or a remote SMTP server or forwarder to support e-mail delivery.</span></span> <span data-ttu-id="804d6-125">如果具有现有远程 SMTP 服务器的访问权限，则应该考虑使用该服务器。</span><span class="sxs-lookup"><span data-stu-id="804d6-125">If you have access to an existing remote SMTP server, you should consider using it.</span></span> <span data-ttu-id="804d6-126">若没有可用的 SMTP 服务器或随后由于计算机连接失败而遇到报表传递错误，则应该进行切换以使用本地 SMTP 服务。</span><span class="sxs-lookup"><span data-stu-id="804d6-126">If there is no SMTP server available or if you subsequently encounter report delivery errors that can be attributed to computer connection failures, you should switch to using a local SMTP service.</span></span> <span data-ttu-id="804d6-127">有关如何为本地或远程服务配置报表服务器的详细信息，将稍后在本主题中进一步说明。</span><span class="sxs-lookup"><span data-stu-id="804d6-127">Details about how to configure a report server for local or remote service are provided further on in this topic.</span></span>  
  
  
  
##  <a name="setting-configuration-options-for-e-mail-delivery"></a><a name="bkmk_setting_email_delivery"></a><span data-ttu-id="804d6-128">为电子邮件传递设置配置选项</span><span class="sxs-lookup"><span data-stu-id="804d6-128">Setting Configuration Options for E-Mail Delivery</span></span>  
 <span data-ttu-id="804d6-129">必须先设置确定使用哪一个 SMTP 服务器的配置值，才能使用报表服务器电子邮件传递。</span><span class="sxs-lookup"><span data-stu-id="804d6-129">Before you can use Report Server e-mail delivery, you must set configuration values that provide information about which SMTP server to use.</span></span>  
  
 <span data-ttu-id="804d6-130">若要针对电子邮件传递配置报表服务器，请执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="804d6-130">To configure a report server for e-mail delivery, do the following:</span></span>  
  
-   <span data-ttu-id="804d6-131">如果要仅指定一个 SMTP 服务器和一个具有发送电子邮件权限的用户帐户，则使用 Reporting Services 配置管理器。</span><span class="sxs-lookup"><span data-stu-id="804d6-131">Use the Reporting Services Configuration Manager if you are specifying just an SMTP server and a user account that has permission to send e-mail.</span></span> <span data-ttu-id="804d6-132">以下是配置报表服务器电子邮件传递扩展插件所需的最低设置。</span><span class="sxs-lookup"><span data-stu-id="804d6-132">These are the minimum settings that are required for configuring the Report Server e-mail delivery extension.</span></span> <span data-ttu-id="804d6-133">有关详细信息，请参阅[电子邮件设置-Configuration Manager &#40;SSRS 本机模式&#41;](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md)和[Reporting Services 中的电子邮件传递](../../reporting-services/subscriptions/e-mail-delivery-in-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="804d6-133">For more information, see [E-mail Settings - Configuration Manager &#40;SSRS Native Mode&#41;](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md) and [E-Mail Delivery in Reporting Services](../../reporting-services/subscriptions/e-mail-delivery-in-reporting-services.md).</span></span>  
  
-   <span data-ttu-id="804d6-134">（可选）使用文本编辑器在 RSreportserver.config 文件中指定其他设置。</span><span class="sxs-lookup"><span data-stu-id="804d6-134">(Optionally) Use a text editor to specify additional settings in the RSreportserver.config file.</span></span> <span data-ttu-id="804d6-135">此文件包含报表服务器电子邮件传递的所有配置设置。</span><span class="sxs-lookup"><span data-stu-id="804d6-135">This file contains all of the configuration settings for Report Server e-mail delivery.</span></span> <span data-ttu-id="804d6-136">如果要使用本地 SMTP 服务器或将电子邮件限定传递到特定主机，则需要在这些文件中指定其他设置。</span><span class="sxs-lookup"><span data-stu-id="804d6-136">Specifying additional settings in these files is required if you are using a local SMTP server or if you are restricting e-mail delivery to specific hosts.</span></span> <span data-ttu-id="804d6-137">有关查找和修改配置文件的详细信息，请参阅 SQL Server 联机丛书中[的 &#40;RSreportserver.config&#41;修改 Reporting Services 配置文件](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)。</span><span class="sxs-lookup"><span data-stu-id="804d6-137">For more information about finding and modifying configuration files, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) in SQL Server Books Online.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="804d6-138">报表服务器电子邮件设置都是基于 CDO。</span><span class="sxs-lookup"><span data-stu-id="804d6-138">Report server e-mail settings are based on CDO.</span></span> <span data-ttu-id="804d6-139">若要了解有关特定设置的更多详细信息，可以参考 CDO 产品文档。</span><span class="sxs-lookup"><span data-stu-id="804d6-139">If you want more detail about specific settings, you can refer to the CDO production documentation.</span></span>  
  

  
##  <a name="example-report-server-e-mail-configuration"></a><a name="bkmk_example_config_file"></a><span data-ttu-id="804d6-140">报表服务器电子邮件配置示例</span><span class="sxs-lookup"><span data-stu-id="804d6-140">Example Report Server E-Mail Configuration</span></span>  
 <span data-ttu-id="804d6-141">下面的示例说明了远程 SMTP 服务器的 RSreportserver.config 文件中的设置：</span><span class="sxs-lookup"><span data-stu-id="804d6-141">The following example illustrates the settings in the RSreportserver.config file for a remote SMTP server.</span></span> <span data-ttu-id="804d6-142">若要了解设置说明及有效值，请参阅 [ssNoVersion](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) 联机丛书中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Onl联机丛书中的e or the CDO product documentation.</span><span class="sxs-lookup"><span data-stu-id="804d6-142">To read about the setting descriptions and valid values, see [RSReportServer Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online or the CDO product documentation.</span></span>  
  
```  
<RSEmailDPConfiguration>  
     <SMTPServer>mySMTPServer.Adventure-Works.com</SMTPServer>  
     <SMTPServerPort></SMTPServerPort>  
     <SMTPAccountName></SMTPAccountName>  
     <SMTPConnectionTimeout></SMTPConnectionTimeout>  
     <SMTPServerPickupDirectory></SMTPServerPickupDirectory>  
     <SMTPUseSSL></SMTPUseSSL>  
     <SendUsing>2</SendUsing>  
     <SMTPAuthenticate></SMTPAuthenticate>  
     <From>my-rs-email-account@Adventure-Works.com</From>  
     <EmbeddedRenderFormats>  
          <RenderingExtension>MHTML</RenderingExtension>  
     </EmbeddedRenderFormats>  
     <PrivilegedUserRenderFormats></PrivilegedUserRenderFormats>  
     <ExcludedRenderFormats>  
          <RenderingExtension>HTMLOWC</RenderingExtension>  
          <RenderingExtension>NULL</RenderingExtension>  
     </ExcludedRenderFormats>  
     <SendEmailToUserAlias>True</SendEmailToUserAlias>  
     <DefaultHostName></DefaultHostName>  
     <PermittedHosts>  
          <HostName>Adventure-Works.com</HostName>  
          <HostName>hotmail.com</HostName>  
     </PermittedHosts>  
</RSEmailDPConfiguration>  
```  
  

  
##  <a name="configuration-options-for-setting-the-to-field-in-a-message"></a><a name="bkmk_setting_TO_field"></a><span data-ttu-id="804d6-143">用于在消息中设置 "到：" 字段的配置选项</span><span class="sxs-lookup"><span data-stu-id="804d6-143">Configuration Options for Setting the To: Field in a Message</span></span>  
 <span data-ttu-id="804d6-144">根据 "**管理单独的订阅**" 任务授予的权限创建的用户定义订阅包含基于域用户帐户的预设用户名。</span><span class="sxs-lookup"><span data-stu-id="804d6-144">User-defined subscriptions that are created according to the permissions granted by the **Manage individual subscriptions** task contain a pre-set user name that is based on the domain user account.</span></span> <span data-ttu-id="804d6-145">用户创建订阅时，“收件人:” \*\*\*\* 字段中的收件人姓名会使用创建该订阅的人员的域用户帐户自行转换为地址。</span><span class="sxs-lookup"><span data-stu-id="804d6-145">When the user creates the subscription, the recipient name in the **To:** field is self-addressed using the domain user account of the person creating the subscription.</span></span>  
  
 <span data-ttu-id="804d6-146">如果您所用的 SMTP 服务器或转发器使用了不同于域用户帐户的电子邮件帐户，则 SMTP 服务器尝试将报表传递给该用户时，报表传递会失败。</span><span class="sxs-lookup"><span data-stu-id="804d6-146">If you are using an SMTP server or forwarder that uses e-mail accounts that are different from the domain user account, the report delivery will fail when the SMTP server tries to deliver the report to that user.</span></span>  
  
 <span data-ttu-id="804d6-147">若要解决该问题，可以修改允许用户在“收件人:” \*\*\*\* 字段中输入名称的配置设置：</span><span class="sxs-lookup"><span data-stu-id="804d6-147">To workaround this issue, you can modify configuration settings that allow users to enter a name in the **To:** field:</span></span>  
  
1.  <span data-ttu-id="804d6-148">使用文本编辑器打开 RSReportServer.config。</span><span class="sxs-lookup"><span data-stu-id="804d6-148">Open RSReportServer.config with a text editor.</span></span>  
  
2.  <span data-ttu-id="804d6-149">将 `SendEmailToUserAlias` 设置为 `False`。</span><span class="sxs-lookup"><span data-stu-id="804d6-149">Set `SendEmailToUserAlias` to `False`.</span></span>  
  
3.  <span data-ttu-id="804d6-150">将 `DefaultHostName` 设置为 SMTP 服务器或转发器的域名系统 (DNS) 名称或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="804d6-150">Set `DefaultHostName` to the Domain Name System (DNS) name or IP address of the SMTP server or forwarder.</span></span>  
  
4.  <span data-ttu-id="804d6-151">保存文件。</span><span class="sxs-lookup"><span data-stu-id="804d6-151">Save the file.</span></span>  
  
  
  
##  <a name="configuration-options-for-remote-smtp-service"></a><a name="bkmk_options_remote_SMTP"></a><span data-ttu-id="804d6-152">远程 SMTP 服务的配置选项</span><span class="sxs-lookup"><span data-stu-id="804d6-152">Configuration Options for Remote SMTP Service</span></span>  
 <span data-ttu-id="804d6-153">报表服务器与 SMTP 服务器或转发器之间的连接是由下列配置设置决定的：</span><span class="sxs-lookup"><span data-stu-id="804d6-153">The connection between the report server and an SMTP server or forwarder is determined by the following configuration settings:</span></span>  
  
-   <span data-ttu-id="804d6-154">`SendUsing` 指定发送消息的方法。</span><span class="sxs-lookup"><span data-stu-id="804d6-154">`SendUsing` specifies a method for sending messages.</span></span> <span data-ttu-id="804d6-155">您可以选择网络 SMTP 服务或本地 SMTP 服务拾取目录。</span><span class="sxs-lookup"><span data-stu-id="804d6-155">You can choose between a network SMTP service or a local SMTP service pickup directory.</span></span> <span data-ttu-id="804d6-156">若要使用远程 SMTP 服务，必须在 RSReportServer.config 文件中将此值设置为 **2** 。</span><span class="sxs-lookup"><span data-stu-id="804d6-156">To use a remote SMTP service, this value must be set to **2** in the RSReportServer.config file.</span></span>  
  
-   <span data-ttu-id="804d6-157">`SMTPServer` 指定远程 SMTP 服务器或转发器。</span><span class="sxs-lookup"><span data-stu-id="804d6-157">`SMTPServer` specifies the remote SMTP server or forwarder.</span></span> <span data-ttu-id="804d6-158">如果使用远程 SMTP 服务器或转发器，则必须指定此值。</span><span class="sxs-lookup"><span data-stu-id="804d6-158">This value is a required value if you are using a remote SMTP server or forwarder.</span></span>  
  
-   <span data-ttu-id="804d6-159">`From`设置显示在电子邮件的 "**发件人：** " 行中的值。</span><span class="sxs-lookup"><span data-stu-id="804d6-159">`From` sets the value that appears in the **From:** line of an e-mail message.</span></span> <span data-ttu-id="804d6-160">如果使用远程 SMTP 服务器或转发器，则必须指定此值。</span><span class="sxs-lookup"><span data-stu-id="804d6-160">This value is a required value if you are using a remote SMTP server or forwarder.</span></span>  
  
 <span data-ttu-id="804d6-161">其他用于远程 SMTP 服务的值包括以下值（请注意，除非您要覆盖默认值，否则无需指定这些值）：</span><span class="sxs-lookup"><span data-stu-id="804d6-161">Other values that are used for remote SMTP service include the following (note that you do not need to specify these values unless you want to override the default values).</span></span>  
  
-   <span data-ttu-id="804d6-162">**SMTPServerPort** 配置为端口 25。</span><span class="sxs-lookup"><span data-stu-id="804d6-162">**SMTPServerPort** is configured for port 25.</span></span>  
  
-   <span data-ttu-id="804d6-163">“”\*\*\*\* 指定如何将报表服务器连接到远程 SMTP 服务器。</span><span class="sxs-lookup"><span data-stu-id="804d6-163">**SMTPAuthenticate** specifies how the report server connects to the remote SMTP server.</span></span> <span data-ttu-id="804d6-164">默认值为 0（或不进行身份验证）。</span><span class="sxs-lookup"><span data-stu-id="804d6-164">The default value is 0 (or no authentication).</span></span> <span data-ttu-id="804d6-165">这种情况下，将通过匿名访问创建连接。</span><span class="sxs-lookup"><span data-stu-id="804d6-165">In this case, the connection is made through Anonymous access.</span></span> <span data-ttu-id="804d6-166">报表服务器和 SMTP 服务器可能需要成为同一域的成员，这取决于域配置。</span><span class="sxs-lookup"><span data-stu-id="804d6-166">Depending on your domain configuration, the report server and the SMTP server may need to be members of the same domain.</span></span>  
  
     <span data-ttu-id="804d6-167">若要向受限制的通讯组列表发送电子邮件（例如，只接受经过身份验证的帐户发来的邮件的通讯组列表），则将 **“SMTPAuthenticate”** 设置为 **“2”**。</span><span class="sxs-lookup"><span data-stu-id="804d6-167">To send e-mail to restricted distribution lists (for example, distribution lists that accept incoming messages only from authenticated accounts), set **SMTPAuthenticate** to **2**.</span></span>  
  

  
##  <a name="configuration-options-for-local-smtp-service"></a><a name="bkmk_options_local_SMTP"></a><span data-ttu-id="804d6-168">本地 SMTP 服务的配置选项</span><span class="sxs-lookup"><span data-stu-id="804d6-168">Configuration Options for Local SMTP Service</span></span>  
 <span data-ttu-id="804d6-169">若要测试报表服务器电子邮件传递或解决所遇到的疑难问题，则配置本地 SMTP 服务会很有用。</span><span class="sxs-lookup"><span data-stu-id="804d6-169">Configuring a local SMTP service is useful if you are testing or troubleshooting report server e-mail delivery.</span></span> <span data-ttu-id="804d6-170">默认情况下，不启用本地 SMTP 服务。</span><span class="sxs-lookup"><span data-stu-id="804d6-170">The local SMTP service is not enabled by default.</span></span> <span data-ttu-id="804d6-171">有关如何启用它的说明，请参阅[为电子邮件传递配置报表服务器 (ssrs Configuration Manager) ](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)和[电子邮件设置-Configuration Manager &#40;ssrs 本机模式&#41;](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="804d6-171">For instructions on how to enable it, see [Configure a Report Server for E-Mail Delivery (SSRS Configuration Manager)](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) and [E-mail Settings - Configuration Manager &#40;SSRS Native Mode&#41;](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="804d6-172">报表服务器与本地 SMTP 服务器或转发器之间的连接是由下列配置设置决定的：</span><span class="sxs-lookup"><span data-stu-id="804d6-172">The connection between the report server and a local SMTP server or forwarder is determined by the following configuration settings:</span></span>  
  
-   <span data-ttu-id="804d6-173">`SendUsing` 设置为 1。</span><span class="sxs-lookup"><span data-stu-id="804d6-173">`SendUsing` is set to **1**.</span></span>  
  
-   <span data-ttu-id="804d6-174">将**SMTPServerPickupDirectory** 设置为本地驱动器中的文件夹。</span><span class="sxs-lookup"><span data-stu-id="804d6-174">**SMTPServerPickupDirectory** is set to a folder on the local drive.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="804d6-175">`SMTPServer`如果使用的是本地 SMTP 服务器，请确保不设置。</span><span class="sxs-lookup"><span data-stu-id="804d6-175">Be sure that you do not set `SMTPServer` if you are using a local SMTP server.</span></span>  
  
-   <span data-ttu-id="804d6-176">`From`设置显示在电子邮件的 "**发件人：** " 行中的值。</span><span class="sxs-lookup"><span data-stu-id="804d6-176">`From` sets the value that appears in the **From:** line of an e-mail message.</span></span> <span data-ttu-id="804d6-177">此值是必需的。</span><span class="sxs-lookup"><span data-stu-id="804d6-177">This value is required.</span></span>  
  
 
  
##  <a name="to-configure-report-server-e-mail-using-the-reporting-services-configuration-manager"></a><a name="bkmk_use_configuration_manager"></a><span data-ttu-id="804d6-178">使用 Reporting Services 配置管理器配置 Report Server 电子邮件</span><span class="sxs-lookup"><span data-stu-id="804d6-178">To configure report server e-mail using the Reporting Services Configuration Manager</span></span>  
  
1.  <span data-ttu-id="804d6-179">请验证报表服务器 Windows 服务是否对 SMTP 服务器拥有 `Send As` 权限。</span><span class="sxs-lookup"><span data-stu-id="804d6-179">Verify that the Report Server Windows service has `Send As` permissions on the SMTP server.</span></span>  
  
2.  <span data-ttu-id="804d6-180">启动 Reporting Services 配置管理器，然后连接到报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="804d6-180">Start the Reporting Services Configuration Manager and connect to the report server instance.</span></span>  
  
3.  <span data-ttu-id="804d6-181">在“电子邮件设置”页上，输入 SMTP 服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="804d6-181">On the Email Settings page, enter the name of the SMTP server.</span></span> <span data-ttu-id="804d6-182">此值可以是 IP 地址、企业 Intranet 上计算机的 UNC 名称或者完全限定域名。</span><span class="sxs-lookup"><span data-stu-id="804d6-182">This value can be an IP address, a UNC name of a computer on your corporate intranet, or a fully qualified domain name.</span></span>  
  
4.  <span data-ttu-id="804d6-183">在 **“发件人地址”** 中，输入有权从 SMTP 服务器发送电子邮件的帐户的名称。</span><span class="sxs-lookup"><span data-stu-id="804d6-183">In **Sender Address**, enter the name an account that has permission to send e-mail from the SMTP server.</span></span>  
  
5.  <span data-ttu-id="804d6-184">单击“**应用**”。</span><span class="sxs-lookup"><span data-stu-id="804d6-184">Click **Apply**.</span></span>  
  

  
##  <a name="to-configure-a-remote-smtp-service-for-the-report-server"></a><a name="bkmk_confiugre_remote_SMTP"></a><span data-ttu-id="804d6-185">为 Report Server 配置远程 SMTP 服务</span><span class="sxs-lookup"><span data-stu-id="804d6-185">To configure a remote SMTP Service for the report server</span></span>  
  
1.  <span data-ttu-id="804d6-186">请验证报表服务器 Windows 服务是否对 SMTP 服务器拥有 `Send As` 权限。</span><span class="sxs-lookup"><span data-stu-id="804d6-186">Verify that the Report Server Windows service has `Send As` permissions on the SMTP server.</span></span>  
  
2.  <span data-ttu-id="804d6-187">在文本编辑器中打开 RSReportServer.config 文件。</span><span class="sxs-lookup"><span data-stu-id="804d6-187">Open the RSReportServer.config file in a text editor.</span></span>  
  
3.  <span data-ttu-id="804d6-188">验证 <`UrlRoot`> 设置为 REPORT SERVER URL 地址。</span><span class="sxs-lookup"><span data-stu-id="804d6-188">Verify that <`UrlRoot`> is set to the report server URL address.</span></span> <span data-ttu-id="804d6-189">此值是在您配置报表服务器时设置的，应该已经填写。</span><span class="sxs-lookup"><span data-stu-id="804d6-189">This value is set when you configure the report server and it should be filled in already.</span></span> <span data-ttu-id="804d6-190">如果未设置此值，则请键入报表服务器 URL 地址。</span><span class="sxs-lookup"><span data-stu-id="804d6-190">If it is not set, type the report server URL address.</span></span>  
  
4.  <span data-ttu-id="804d6-191">在 "传递" 部分中，查找 <`ReportServerEmail`>。</span><span class="sxs-lookup"><span data-stu-id="804d6-191">In the Delivery section, find <`ReportServerEmail`>.</span></span>  
  
5.  <span data-ttu-id="804d6-192">在 <`SMTPServer`> 中，键入 SMTP 服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="804d6-192">In <`SMTPServer`>, type the name of the SMTP server.</span></span> <span data-ttu-id="804d6-193">此值可以是 IP 地址、企业 Intranet 上计算机的 UNC 名称或者完全限定域名。</span><span class="sxs-lookup"><span data-stu-id="804d6-193">This value can be an IP address, a UNC name of a computer on your corporate intranet, or a fully qualified domain name.</span></span>  
  
6.  <span data-ttu-id="804d6-194">确认 <`SendUsing`> 设置为2。</span><span class="sxs-lookup"><span data-stu-id="804d6-194">Verify that <`SendUsing`> is set to 2.</span></span> <span data-ttu-id="804d6-195">如果将其设置为其他值，则报表服务器无法配置为使用远程 SMTP 服务。</span><span class="sxs-lookup"><span data-stu-id="804d6-195">If it is set another value, the report server is not configured to use a remote SMTP service.</span></span>  
  
7.  <span data-ttu-id="804d6-196">在 <`From`> 中，键入有权从 SMTP 服务器发送电子邮件的帐户的名称。</span><span class="sxs-lookup"><span data-stu-id="804d6-196">In <`From`>, type the name an account that has permission to send e-mail from the SMTP server.</span></span>  
  
8.  <span data-ttu-id="804d6-197">保存文件。</span><span class="sxs-lookup"><span data-stu-id="804d6-197">Save the file.</span></span>  
  
     <span data-ttu-id="804d6-198">报表服务器将自动使用新的设置；不需要重新启动该服务。</span><span class="sxs-lookup"><span data-stu-id="804d6-198">The report server will use the new settings automatically; you do not need to restart the service.</span></span> <span data-ttu-id="804d6-199">您可以指定其他 SMTP 设置，以进一步配置如何将 SMTP 服务器用于报表服务器电子邮件传递。</span><span class="sxs-lookup"><span data-stu-id="804d6-199">You can specify additional SMTP settings to further configure how the SMTP server is used for report server e-mail delivery.</span></span> <span data-ttu-id="804d6-200">有关详细信息，请参阅 [ssNoVersion](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) 和 [ssNoVersion](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) 联机丛书中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Onl联机丛书中的e.</span><span class="sxs-lookup"><span data-stu-id="804d6-200">For more information, see [Configuring a Report Server for E-Mail Delivery](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) and [RSReportServer Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  

  
##  <a name="to-configure-a-local-smtp-service-for-the-report-server"></a><a name="bkmk_confiugre_local_SMTP"></a><span data-ttu-id="804d6-201">为 Report Server 配置本地 SMTP 服务</span><span class="sxs-lookup"><span data-stu-id="804d6-201">To configure a local SMTP Service for the report server</span></span>  
  
1.  <span data-ttu-id="804d6-202">在“控制面板”中，单击“**添加或删除程序**”。</span><span class="sxs-lookup"><span data-stu-id="804d6-202">In Control Panel, click **Add or Remove Programs**.</span></span>  
  
2.  <span data-ttu-id="804d6-203">单击 **“添加/删除 Windows 组件”** 启动 Windows 组件向导。</span><span class="sxs-lookup"><span data-stu-id="804d6-203">Click **Add/Remove Windows Components** to start the Windows Component Wizard.</span></span>  
  
3.  <span data-ttu-id="804d6-204">选择 **“应用程序服务器”** ，然后单击 **“详细信息”**。</span><span class="sxs-lookup"><span data-stu-id="804d6-204">Select **Application Server** and click **Details**.</span></span>  
  
4.  <span data-ttu-id="804d6-205">选择 **“Internet 信息服务 (IIS)”** ，然后单击 **“详细信息”**。</span><span class="sxs-lookup"><span data-stu-id="804d6-205">Select **Internet Information Services (IIS)** and click **Details**.</span></span>  
  
5.  <span data-ttu-id="804d6-206">选中 **“SMTP 服务”** 复选框，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="804d6-206">Select the **SMTP Service** checkbox and click **OK**.</span></span>  
  
6.  <span data-ttu-id="804d6-207">在 Windows 组件向导中，单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="804d6-207">On the Windows Component Wizard, click **Next**.</span></span> <span data-ttu-id="804d6-208">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="804d6-208">Click **Finish**.</span></span>  
  
7.  <span data-ttu-id="804d6-209">验证服务是否正在 **“服务”** 控制台上运行。</span><span class="sxs-lookup"><span data-stu-id="804d6-209">Verify that the service is running in the **Services** console.</span></span>  
  
8.  <span data-ttu-id="804d6-210">在文本编辑器中打开**RSReportServer.config**文件。</span><span class="sxs-lookup"><span data-stu-id="804d6-210">Open the **RSReportServer.config** file in a text editor.</span></span>  
  
9. <span data-ttu-id="804d6-211">请验证是否将 `<UrlRoot>` 设置为报表服务器 URL 地址。</span><span class="sxs-lookup"><span data-stu-id="804d6-211">Verify that `<UrlRoot>` is set to the report server URL address.</span></span> <span data-ttu-id="804d6-212">此值是在您配置报表服务器时设置的，应该已经填写。</span><span class="sxs-lookup"><span data-stu-id="804d6-212">This value is set when you configure the report server and it should be filled in already.</span></span> <span data-ttu-id="804d6-213">如果未设置此值，则请键入报表服务器 URL 地址。</span><span class="sxs-lookup"><span data-stu-id="804d6-213">If it is not set, type the report server URL address.</span></span>  
  
10. <span data-ttu-id="804d6-214">在“传递”部分中，查找 `<ReportServerEmail>.`。</span><span class="sxs-lookup"><span data-stu-id="804d6-214">In the Delivery section, find `<ReportServerEmail>.`</span></span>  
  
11. <span data-ttu-id="804d6-215">在 `<SMTPServer>`中，清除此设置的所有值，但不要删除标记。</span><span class="sxs-lookup"><span data-stu-id="804d6-215">In `<SMTPServer>`, clear any values for this setting, but do not delete the tags.</span></span>  
  
12. <span data-ttu-id="804d6-216">将 `<SendUsing>` 设置为 1。</span><span class="sxs-lookup"><span data-stu-id="804d6-216">Set `<SendUsing>` to 1.</span></span> <span data-ttu-id="804d6-217">如果将其设置为其他值，则无法将报表服务器配置为使用本地 SMTP 服务。</span><span class="sxs-lookup"><span data-stu-id="804d6-217">If it is set another value, the report server is not configured to use a local SMTP service.</span></span>  
  
13. <span data-ttu-id="804d6-218">将 `<SMTPServerPickupDirectory>` 设置为本地驱动器上的文件夹。</span><span class="sxs-lookup"><span data-stu-id="804d6-218">Set `<SMTPServerPickupDirectory>` to a folder on the local drive.</span></span>  
  
14. <span data-ttu-id="804d6-219">将 `<From>` 设置为有权从 SMTP 服务器发送电子邮件的帐户。</span><span class="sxs-lookup"><span data-stu-id="804d6-219">Set `<From>` to an account that has permission to send e-mail from the SMTP server.</span></span>  
  
15. <span data-ttu-id="804d6-220">保存文件。</span><span class="sxs-lookup"><span data-stu-id="804d6-220">Save the file.</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="804d6-221">另请参阅</span><span class="sxs-lookup"><span data-stu-id="804d6-221">See Also</span></span>  
 [<span data-ttu-id="804d6-222">Reporting Services Configuration Manager（本机模式）</span><span class="sxs-lookup"><span data-stu-id="804d6-222">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
