---
title: Reporting Services 中的电子邮件传递 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], e-mail
- e-mail [Reporting Services]
- mail [Reporting Services]
ms.assetid: fda2f130-97b9-4258-9dbb-e93a70f4d08a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9780a47b8e11f831f3a390829acdbd8ae935cf2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587164"
---
# <a name="e-mail-delivery-in-reporting-services"></a><span data-ttu-id="ddbf8-102">Reporting Services 中的电子邮件传递</span><span class="sxs-lookup"><span data-stu-id="ddbf8-102">E-Mail Delivery in Reporting Services</span></span>
  <span data-ttu-id="ddbf8-103">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中包含电子邮件传递扩展插件，该插件提供了通过电子邮件将报表发送到单个用户或组的方式。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-103">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] includes an e-mail delivery extension that provides a way to e-mail a report to individual users or groups.</span></span> <span data-ttu-id="ddbf8-104">电子邮件传递扩展插件是通过 Reporting Services 配置管理器并编辑 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置文件进行配置的。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-104">The e-mail delivery extension is configured through the Reporting Services Configuration Manager and by editing the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] configuration files.</span></span>  
  
 <span data-ttu-id="ddbf8-105">若要通过电子邮件分发或接收报表，请定义标准订阅或数据驱动订阅。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-105">To distribute or receive a report by e-mail, you define either a standard subscription or a data-driven subscription.</span></span> <span data-ttu-id="ddbf8-106">您一次只能订阅或分发一个报表。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-106">You can subscribe to or distribute only one report at a time.</span></span> <span data-ttu-id="ddbf8-107">您不能创建在一个电子邮件中传递多个报表的订阅。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-107">You cannot create a subscription that delivers multiple reports in a single e-mail message.</span></span> <span data-ttu-id="ddbf8-108">有关订阅的详细信息，请参阅[创建、修改和删除纯模式&#41;中 &#40;Reporting Services 的标准订阅](create-and-manage-subscriptions-for-native-mode-report-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-108">For more information about subscriptions, see [Create, Modify, and Delete Standard Subscriptions &#40;Reporting Services in Native Mode&#41;](create-and-manage-subscriptions-for-native-mode-report-servers.md).</span></span>  
  
||  
|-|  
|<span data-ttu-id="ddbf8-109">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Sharepoint 模式 &#124; SharePoint 2010 和 SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="ddbf8-109">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode &#124; SharePoint 2010 and SharePoint 2013</span></span><br /><br /> <span data-ttu-id="ddbf8-110">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 本机模式</span><span class="sxs-lookup"><span data-stu-id="ddbf8-110">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode</span></span>|  
  
## <a name="e-mail-delivery-options"></a><span data-ttu-id="ddbf8-111">电子邮件传递选项</span><span class="sxs-lookup"><span data-stu-id="ddbf8-111">E-Mail Delivery Options</span></span>  
 <span data-ttu-id="ddbf8-112">报表服务器电子邮件传递可以通过以下方式传递报表：</span><span class="sxs-lookup"><span data-stu-id="ddbf8-112">Report server e-mail delivery can deliver reports in the following ways:</span></span>  
  
-   <span data-ttu-id="ddbf8-113">将通知和超链接发送到所生成的报表。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-113">Send a notification and a hyperlink to the generated report.</span></span>  
  
-   <span data-ttu-id="ddbf8-114">在电子邮件的“主题:”行中发送通知。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-114">Send a notification in the Subject: line of an e-mail message.</span></span> <span data-ttu-id="ddbf8-115">默认情况下，订阅定义中的“主题:”行包含以下变量（这些变量将在处理订阅时替换为报表特定的信息）：</span><span class="sxs-lookup"><span data-stu-id="ddbf8-115">By default, the Subject: line in the subscription definition includes the following variables that are replaced by report-specific information when the subscription is processed:</span></span>  
  
     <span data-ttu-id="ddbf8-116">**@ReportName**指定报表的名称。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-116">**@ReportName** specifies the name of the report.</span></span>  
  
     <span data-ttu-id="ddbf8-117">**@ExecutionTime**指定报表的执行时间。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-117">**@ExecutionTime** specifies when the report was executed.</span></span>  
  
     <span data-ttu-id="ddbf8-118">您可以将这些变量与静态文本组合在一起，也可以修改每个订阅的“主题:”行中的文本。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-118">You can combine these variables with static text or modify the text in the Subject: line for each subscription.</span></span>  
  
-   <span data-ttu-id="ddbf8-119">发送嵌入或作为附件的报表。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-119">Send an embedded or attached report.</span></span> <span data-ttu-id="ddbf8-120">呈现格式和浏览器决定了报表是嵌入的还是作为附件发送。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-120">The rendering format and browser determine whether the report is embedded or attached.</span></span>  
  
     <span data-ttu-id="ddbf8-121">如果您的浏览器支持 HTML 4.0 和 MHTML，并且您选择了 Web 存档呈现格式，那么报表将嵌入为邮件的一部分。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-121">If your browser supports HTML 4.0 and MHTML, and you choose the Web archive rendering format, the report is embedded as part of the message.</span></span> <span data-ttu-id="ddbf8-122">其他所有呈现格式（CSV、PDF 等）都将报表作为附件进行传递。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-122">All other rendering formats (CSV, PDF, and so on) deliver reports as attachments.</span></span> <span data-ttu-id="ddbf8-123">您可以在 RSReportServer 配置文件中禁用此功能。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-123">You can disable this functionality in the RSReportServer configuration file.</span></span>  
  
     [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="ddbf8-124">不会检查附件或邮件的大小。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-124">does not check the size of the attachment or message before sending the report.</span></span> <span data-ttu-id="ddbf8-125">如果附件或邮件的大小超出邮件服务器允许的最大限制，则无法传递报表。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-125">If the attachment or message exceeds the maximum limit allowed by your mail server, the report is not delivered.</span></span> <span data-ttu-id="ddbf8-126">如果是大型报表，请选择其他传递选项（例如 URL 或通知）。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-126">Choose one of the other delivery options (such as URL or notification) if for large reports.</span></span>  
  
 <span data-ttu-id="ddbf8-127">在您创建订阅时，将设置确定报表传递方式的传递选项。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-127">You set delivery options that determine how a report is delivered when you create the subscription.</span></span> <span data-ttu-id="ddbf8-128">例如，如果选择在订阅中“包含链接”，电子邮件将包含一个指向该报表的超链接  。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-128">For example, if you select **Include Link** in the subscription, the e-mail message includes a hyperlink to the report.</span></span>  
  
## <a name="role-based-e-mail-settings"></a><span data-ttu-id="ddbf8-129">基于角色的电子邮件设置</span><span class="sxs-lookup"><span data-stu-id="ddbf8-129">Role-based E-Mail Settings</span></span>  
 <span data-ttu-id="ddbf8-130">订阅报表时，根据您的角色中包含的是“管理单独的订阅”任务，还是“管理所有订阅”任务，您所使用的电子邮件传递设置将有所不同。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-130">When you subscribe to a report, the e-mail delivery settings you work with vary depending on whether your role includes the "Manage individual subscriptions" task or the "Manage all subscriptions" task.</span></span>  
  
|<span data-ttu-id="ddbf8-131">任务</span><span class="sxs-lookup"><span data-stu-id="ddbf8-131">Task</span></span>|<span data-ttu-id="ddbf8-132">可用设置</span><span class="sxs-lookup"><span data-stu-id="ddbf8-132">Available settings</span></span>|  
|----------|------------------------|  
|<span data-ttu-id="ddbf8-133">管理单独的订阅</span><span class="sxs-lookup"><span data-stu-id="ddbf8-133">Manage individual subscriptions</span></span>|<span data-ttu-id="ddbf8-134">显示使用户能够向自己自动传递报表的字段。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-134">Shows fields that enable a user to automate and deliver a report to himself or herself.</span></span> <span data-ttu-id="ddbf8-135">在此模式下，接受电子邮件别名的字段不可用。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-135">In this mode, fields that accept e-mail aliases are not available.</span></span>|  
|<span data-ttu-id="ddbf8-136">管理所有订阅</span><span class="sxs-lookup"><span data-stu-id="ddbf8-136">Manage all subscriptions</span></span>|<span data-ttu-id="ddbf8-137">显示支持更大分发范围的字段，包括“收件人:”字段、“抄送:”字段、“密件抄送:”字段和“答复:”字段，从而提供了另外一些向更多订阅者发送报表的方法。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-137">Shows fields that support wider distribution, including To:, Cc:, Bcc:, and Reply-To: fields, providing more ways to route a report to more subscribers.</span></span> <span data-ttu-id="ddbf8-138">电子邮件别名字段的可用性是通过 RSReportServer 配置文件设置进行定义的。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-138">The availability of e-mail alias fields is defined through the RSReportServer configuration file settings.</span></span>|  
  
## <a name="specifying-e-mail-addresses-in-a-subscription"></a><span data-ttu-id="ddbf8-139">在订阅中指定电子邮件地址</span><span class="sxs-lookup"><span data-stu-id="ddbf8-139">Specifying E-Mail Addresses in a Subscription</span></span>  
 <span data-ttu-id="ddbf8-140">如果您是在 Intranet 内分发报表，并且使用的是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Exchange 服务器的 SMTP 网关，则键入电子邮件别名（就像给同事发送电子邮件一样）。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-140">If you are distributing reports within an intranet and you are using an SMTP gateway to a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Exchange server, type the e-mail alias (as if you were sending e-mail to a coworker).</span></span> <span data-ttu-id="ddbf8-141">如果传递的目标是外部电子邮件帐户，则键入完整的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-141">If delivery is to an external e-mail account, type the full e-mail address.</span></span> <span data-ttu-id="ddbf8-142">如果您指定更多电子邮件地址，以便将其他人添加到订阅中，则这些订阅者将获得与从该订阅生成的报表完全相同的副本。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-142">If you specify more e-mail addresses to add others to your subscription, subscribers get an exact copy of the report that is produced from this subscription.</span></span>  
  
 <span data-ttu-id="ddbf8-143">报表服务器不验证电子邮件地址或从电子邮件服务器获得电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-143">The report server does not validate e-mail addresses or obtain e-mail addresses from an e-mail server.</span></span> <span data-ttu-id="ddbf8-144">您事先必须知道要使用哪些电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-144">You must know in advance which e-mail addresses you want to use.</span></span> <span data-ttu-id="ddbf8-145">默认情况下，您可以通过电子邮件将报表发送到组织内外任何有效的电子邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-145">By default, you can e-mail reports to any valid e-mail account within or outside of your organization.</span></span> <span data-ttu-id="ddbf8-146">不过，您可以使用配置设置限制将电子邮件传递到通过名称标识的特定邮件服务器主机。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-146">Configuration settings can be used, however, to restrict e-mail delivery to mail server hosts that you identify by name.</span></span> <span data-ttu-id="ddbf8-147">如果您希望支持以电子邮件方式向组织外的人员传递报表，则可以指定其他主机。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-147">You can specify additional hosts if you want to support e-mail delivery to people that are not members of your organization.</span></span>  
  
 <span data-ttu-id="ddbf8-148">必须通过在电子邮件服务器上定义的电子邮件帐户来发送用于传递报表的电子邮件。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-148">The e-mail message used to deliver the report must be sent from an e-mail account that is defined on the e-mail server.</span></span> <span data-ttu-id="ddbf8-149">其中一项配置设置指定此电子邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-149">A configuration setting specifies the e-mail account.</span></span> <span data-ttu-id="ddbf8-150">该电子邮件帐户适用于通过电子邮件传递扩展插件传递的所有报表；您不能指定多个帐户或针对单个报表更改这一帐户。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-150">The e-mail account is used for all reports delivered by the e-mail delivery extension; you cannot specify multiple accounts or vary the account for individual reports.</span></span>  
  
## <a name="e-mail-server-configuration"></a><span data-ttu-id="ddbf8-151">电子邮件服务器配置</span><span class="sxs-lookup"><span data-stu-id="ddbf8-151">E-Mail Server Configuration</span></span>  
 <span data-ttu-id="ddbf8-152">报表服务器通过标准连接与电子邮件服务器相连。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-152">The report server connects with an e-mail server through a standard connection.</span></span> <span data-ttu-id="ddbf8-153">它不使用通过安全套接字层 (SSL) 进行加密的通信。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-153">It does not use communication that has been encrypted using Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="ddbf8-154">电子邮件服务器必须是与报表服务器位于同一网络上的远程或本地简单邮件传输协议 (SMTP) 服务器。</span><span class="sxs-lookup"><span data-stu-id="ddbf8-154">The e-mail server must be a remote or local Simple Mail Transport Protocol (SMTP) server on the same network as the report server.</span></span>  
  
 <span data-ttu-id="ddbf8-155">有关如何配置本机模式报表服务器的信息，请参阅以下内容：</span><span class="sxs-lookup"><span data-stu-id="ddbf8-155">For information on how to configure a native mode report server, see the following:</span></span>  
  
-   [<span data-ttu-id="ddbf8-156">配置报表服务器，以便 &#40;SSRS Configuration Manager 发送电子邮件&#41;</span><span class="sxs-lookup"><span data-stu-id="ddbf8-156">Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
  
-   [<span data-ttu-id="ddbf8-157">电子邮件设置-Configuration Manager &#40;SSRS 本机模式下&#41;</span><span class="sxs-lookup"><span data-stu-id="ddbf8-157">E-mail Settings - Configuration Manager &#40;SSRS Native Mode&#41;</span></span>](../install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md)  
  
 <span data-ttu-id="ddbf8-158">有关如何配置 SharePoint 模式报表服务器的信息，请参阅以下内容：</span><span class="sxs-lookup"><span data-stu-id="ddbf8-158">For information on how to configure a SharePoint mode report server, see the following:</span></span>  
  
-   [<span data-ttu-id="ddbf8-159">为 Reporting Services 服务应用程序配置电子邮件（SharePoint 2010 和 SharePoint 2013）</span><span class="sxs-lookup"><span data-stu-id="ddbf8-159">Configure E-mail for a Reporting Services Service Application &#40;SharePoint 2010 and SharePoint 2013&#41;</span></span>](../install-windows/configure-e-mail-for-a-reporting-services-service-application.md)  
  
## <a name="see-also"></a><span data-ttu-id="ddbf8-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ddbf8-160">See Also</span></span>  
 <span data-ttu-id="ddbf8-161">[任务和权限](../security/tasks-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="ddbf8-161">[Tasks and Permissions](../security/tasks-and-permissions.md) </span></span>  
 <span data-ttu-id="ddbf8-162">[订阅和传递 (Reporting Services)](subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="ddbf8-162">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span></span>  
 <span data-ttu-id="ddbf8-163">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="ddbf8-163">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span></span>  
 [<span data-ttu-id="ddbf8-164">角色分配</span><span class="sxs-lookup"><span data-stu-id="ddbf8-164">Role Assignments</span></span>](../security/role-assignments.md)  
  
  
