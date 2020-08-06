---
title: 在纯模式下创建、修改和删除标准订阅 (Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- standard subscriptions [Reporting Services]
- subscriptions [Reporting Services], standard
ms.assetid: 5ab1c661-9bfa-434a-b315-faac34ed12b1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 035462f53e91a0ac29c756f8fcfdef7ad65cb984
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579991"
---
# <a name="create-modify-and-delete-standard-subscriptions-reporting-services-in-native-mode"></a><span data-ttu-id="45422-102">Create, Modify, and Delete Standard Subscriptions (Reporting Services in Native Mode)</span><span class="sxs-lookup"><span data-stu-id="45422-102">Create, Modify, and Delete Standard Subscriptions (Reporting Services in Native Mode)</span></span>
  <span data-ttu-id="45422-103">标准订阅是由希望通过电子邮件传递报表或将报表传递到共享文件夹的各个用户所创建的订阅。</span><span class="sxs-lookup"><span data-stu-id="45422-103">A standard subscription is one that is created by individual users who want to have a report delivered through e-mail or to a shared folder.</span></span> <span data-ttu-id="45422-104">标准订阅始终通过其所基于的报表来定义。</span><span class="sxs-lookup"><span data-stu-id="45422-104">A standard subscription is always defined through the report on which it is based.</span></span>  
  
 <span data-ttu-id="45422-105">创建订阅的用户拥有该订阅。</span><span class="sxs-lookup"><span data-stu-id="45422-105">A user who creates a subscription owns that subscription.</span></span> <span data-ttu-id="45422-106">每个用户都可以修改或删除自己所拥有的订阅。</span><span class="sxs-lookup"><span data-stu-id="45422-106">Each user can modify or delete the subscriptions that he or she owns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="45422-107">从 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 开始，你可以以编程方式传递订阅所有权。</span><span class="sxs-lookup"><span data-stu-id="45422-107">Starting with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] you can transfer the ownership of a subscription programmatically.</span></span> <span data-ttu-id="45422-108">没有可用于传递订阅所有权的用户界面。</span><span class="sxs-lookup"><span data-stu-id="45422-108">There is no user interface you can use to transfer ownership of subscriptions.</span></span> <span data-ttu-id="45422-109">有关详细信息，请参阅 <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A></span><span class="sxs-lookup"><span data-stu-id="45422-109">For more information, see <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A></span></span>  
  
 <span data-ttu-id="45422-110">根据**RSReportServer.config**配置文件设置，用户可能能够向订阅添加更多用户 (例如，经理添加其直接下属的电子邮件地址，以便每个人都接收报表) 的副本。</span><span class="sxs-lookup"><span data-stu-id="45422-110">Depending on **RSReportServer.config** configuration file settings, users may be able to add more users to a subscription (for example, a manager adds the e-mail addresses of his or her direct reports so that they each receive a copy of the report).</span></span> <span data-ttu-id="45422-111">是否支持此功能取决于在定义单独的订阅时“收件人:”字段是否可见。</span><span class="sxs-lookup"><span data-stu-id="45422-111">Whether this is supported depends on whether the To: field is visible when defining individual subscriptions.</span></span> <span data-ttu-id="45422-112">有关详细信息，请参阅[为电子邮件传递配置报表服务器 &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="45422-112">For more information, see [Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="45422-113">本主题提供了由各个用户创建和管理的标准订阅的有关信息。</span><span class="sxs-lookup"><span data-stu-id="45422-113">This topic provides information about standard subscriptions that are created and managed by individual users.</span></span> <span data-ttu-id="45422-114">而数据驱动订阅具有不同的要求和步骤，将在另一个主题中进行讨论。</span><span class="sxs-lookup"><span data-stu-id="45422-114">Data-driven subscriptions have different requirements and steps, and are discussed in a separate topic.</span></span> <span data-ttu-id="45422-115">有关详细信息，请参阅[创建、修改和删除数据驱动订阅](data-driven-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="45422-115">For more information, see [Create, Modify, and Delete a Data-Driven Subscription](data-driven-subscriptions.md).</span></span>  
  
 <span data-ttu-id="45422-116">本主题内容：</span><span class="sxs-lookup"><span data-stu-id="45422-116">In this topic:</span></span>  
  
-   [<span data-ttu-id="45422-117">创建订阅</span><span class="sxs-lookup"><span data-stu-id="45422-117">To Create a Subscription</span></span>](#bkmk_create_subscription)  
  
-   [<span data-ttu-id="45422-118">创建文件共享订阅</span><span class="sxs-lookup"><span data-stu-id="45422-118">To Create a File Share Subscription</span></span>](#bkmk_create_fileshare_subscription)  
  
-   [<span data-ttu-id="45422-119">创建电子邮件订阅</span><span class="sxs-lookup"><span data-stu-id="45422-119">To Create an E-mail Subscription</span></span>](#bkmk_create_email_subscription)  
  
-   [<span data-ttu-id="45422-120">修改订阅</span><span class="sxs-lookup"><span data-stu-id="45422-120">To Modify a Subscription</span></span>](#bkmk_modify_subscription)  
  
-   [<span data-ttu-id="45422-121">删除订阅</span><span class="sxs-lookup"><span data-stu-id="45422-121">To Delete a Subscription</span></span>](#bkmk_delete_subscription)  
  
##  <a name="to-create-a-subscription"></a><a name="bkmk_create_subscription"></a><span data-ttu-id="45422-122">创建订阅</span><span class="sxs-lookup"><span data-stu-id="45422-122">To Create a Subscription</span></span>  
 <span data-ttu-id="45422-123">若要创建订阅，请选择对您的报表服务器部署有效的工具和方法：</span><span class="sxs-lookup"><span data-stu-id="45422-123">To create a subscription, choose the tool and approach that is valid for your report server deployment:</span></span>  
  
-   <span data-ttu-id="45422-124">本主题中的内容说明如何使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表管理器在本机模式报表服务器上创建订阅。</span><span class="sxs-lookup"><span data-stu-id="45422-124">The content in this topic explains how to create subscriptions on a native mode report server using [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Report Manager.</span></span> <span data-ttu-id="45422-125">定义订阅之后，可以在报表管理器中通过“我的订阅”页或特定报表的 **“订阅”** 选项卡访问订阅。</span><span class="sxs-lookup"><span data-stu-id="45422-125">After you define a subscription, you can access it in Report Manager through the My Subscriptions page or the **Subscriptions** tab of a specific report.</span></span>  
  
-   <span data-ttu-id="45422-126">[创建和管理 Sharepoint 模式报表服务器的订阅](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md)介绍了如何使用 sharepoint 站点中的应用程序页订阅在 sharepoint 集成模式下运行的 Report Server 上的报表。</span><span class="sxs-lookup"><span data-stu-id="45422-126">[Create and Manage Subscriptions for SharePoint Mode Report Servers](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md) explains how to use the application pages in a SharePoint site to subscribe to reports on a report server that runs in SharePoint integrated mode.</span></span>  
  
 <span data-ttu-id="45422-127">本主题提供创建电子邮件订阅和文件共享传递订阅的说明。</span><span class="sxs-lookup"><span data-stu-id="45422-127">This topic provides instructions for creating an e-mail subscription and a file share delivery subscription.</span></span>  
  
-   <span data-ttu-id="45422-128">若要使用电子邮件传递，在创建订阅之前，必须为 SMTP 服务器或网关连接配置报表服务器。</span><span class="sxs-lookup"><span data-stu-id="45422-128">To use e-mail delivery, the report server must be configured for an SMTP server or gateway connection before you create the subscription.</span></span>  
  
-   <span data-ttu-id="45422-129">若要使用文件共享传递，必须先定义目标文件夹。</span><span class="sxs-lookup"><span data-stu-id="45422-129">To use file share delivery, you must have target folder already defined.</span></span> <span data-ttu-id="45422-130">有关详细信息，请参阅[为电子邮件传递配置报表服务器 &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="45422-130">For more information, see [Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="45422-131">必须先将报表数据源配置为使用存储的凭据或不使用凭据，然后才可以订阅报表。</span><span class="sxs-lookup"><span data-stu-id="45422-131">Before you can subscribe to a report, the report data source must be configured to use stored credentials or no credentials.</span></span> <span data-ttu-id="45422-132">有关详细信息，请参阅 [在 Reporting Services 数据源中存储凭据](../report-data/store-credentials-in-a-reporting-services-data-source.md)。</span><span class="sxs-lookup"><span data-stu-id="45422-132">For more information, see [Store Credentials in a Reporting Services Data Source](../report-data/store-credentials-in-a-reporting-services-data-source.md).</span></span> <span data-ttu-id="45422-133">否则， **“新建订阅”** 按钮将不可用。</span><span class="sxs-lookup"><span data-stu-id="45422-133">If it does not, the **New Subscription** button is not available.</span></span>  
  
 <span data-ttu-id="45422-134">本主题不介绍如何创建数据驱动订阅。</span><span class="sxs-lookup"><span data-stu-id="45422-134">This topic does not explain how to create a data-driven subscription.</span></span> <span data-ttu-id="45422-135">有关如何创建数据驱动的订阅的说明，请参阅[创建数据驱动订阅（SSRS 教程）](../create-a-data-driven-subscription-ssrs-tutorial.md)或在报表管理器中“创建数据驱动的订阅”页的联机帮助。</span><span class="sxs-lookup"><span data-stu-id="45422-135">For instructions on how to create a data-driven subscription, see [Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md) or the online help for the Create a Data-driven Subscription page in Report Manager.</span></span>  
  
###  <a name="to-create-a-file-share-subscription"></a><a name="bkmk_create_fileshare_subscription"></a><span data-ttu-id="45422-136">创建文件共享订阅</span><span class="sxs-lookup"><span data-stu-id="45422-136">To Create a File Share Subscription</span></span>  
  
1.  <span data-ttu-id="45422-137">启动 [报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="45422-137">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="45422-138">在报表管理器中的 **“内容”** 页上，导航到要订阅的报表。</span><span class="sxs-lookup"><span data-stu-id="45422-138">In Report Manager, on the **Contents** page, navigate to the report you want to subscribe to.</span></span> <span data-ttu-id="45422-139">单击报表以打开它。</span><span class="sxs-lookup"><span data-stu-id="45422-139">Click the report to open it.</span></span>  
  
3.  <span data-ttu-id="45422-140">单击 **“订阅”** 选项卡，再单击 **“新建订阅”**。</span><span class="sxs-lookup"><span data-stu-id="45422-140">Click the **Subscriptions** tab, and then click **New Subscription**.</span></span>  
  
4.  <span data-ttu-id="45422-141">在 **“传递者”** 中选择 **“Windows 文件共享”**。</span><span class="sxs-lookup"><span data-stu-id="45422-141">In **Delivered by**, select **Windows File Share**.</span></span>  
  
5.  <span data-ttu-id="45422-142">在 **“文件名”** 中，为报表键入文件名。</span><span class="sxs-lookup"><span data-stu-id="45422-142">In **File Name**, type a file name for the report.</span></span>  
  
6.  <span data-ttu-id="45422-143">选中 **“创建文件时添加文件扩展名”**。</span><span class="sxs-lookup"><span data-stu-id="45422-143">Select **Add a file extension when the file is created**.</span></span> <span data-ttu-id="45422-144">选择此选项，将向文件名中添加三个字符的文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="45422-144">This option adds a three-character file extension to the file name.</span></span> <span data-ttu-id="45422-145">文件扩展名由所选择的报表输出格式决定。</span><span class="sxs-lookup"><span data-stu-id="45422-145">The file extension is determined by the report output format you select.</span></span>  
  
7.  <span data-ttu-id="45422-146">在 "**路径**" 文本框中，键入要在其中传递报表的现有文件夹的通用命名约定 (UNC) 路径 (例如， \\ \\<servername \> \\<myreports \>) 。</span><span class="sxs-lookup"><span data-stu-id="45422-146">In the **Path** text box, type a Universal Naming Convention (UNC) path to an existing folder where you want to deliver the reports (for example, \\\\<servername\>\\<myreports\>).</span></span> <span data-ttu-id="45422-147">在路径开头包括双反斜杠字符。</span><span class="sxs-lookup"><span data-stu-id="45422-147">Include double backslash characters at the beginning of the path.</span></span> <span data-ttu-id="45422-148">在路径末尾不要使用反斜杠。</span><span class="sxs-lookup"><span data-stu-id="45422-148">Do not specify a trailing backslash.</span></span>  
  
8.  <span data-ttu-id="45422-149">在“呈现格式”中，为文件传递选择一种报表输出格式。</span><span class="sxs-lookup"><span data-stu-id="45422-149">In Render Format, select a report output format for file delivery.</span></span> <span data-ttu-id="45422-150">选择与要用来打开报表的桌面应用程序相对应的格式。</span><span class="sxs-lookup"><span data-stu-id="45422-150">Choose a format that corresponds to the desktop application that will be used to open the report.</span></span> <span data-ttu-id="45422-151">避免使用不以单数据流呈现报表的格式，也不要使用引入静态文件不支持的交互的格式（例如 HTML 4.0）。</span><span class="sxs-lookup"><span data-stu-id="45422-151">Avoid formats that do not render a report in a single stream or that introduce interactivity that cannot be supported in a static file (for example, HTML 4.0).</span></span>  
  
9. <span data-ttu-id="45422-152">在 "**用户名**" 和 "**密码**" 文本框中，使用用户名的格式指定访问文件共享所需的凭据 *\<domain>* \\ *\<user name>* 。</span><span class="sxs-lookup"><span data-stu-id="45422-152">In the **User name** and **Password** text boxes, specify the credentials required to access the file share, using the format *\<domain>*\\*\<user name>* for the user name.</span></span>  
  
10. <span data-ttu-id="45422-153">指定覆盖选项。</span><span class="sxs-lookup"><span data-stu-id="45422-153">Specify overwrite options.</span></span> <span data-ttu-id="45422-154">如果单击 **“如果存在旧版本，则不覆盖该文件”**，则若检测到现有文件，将不进行传递。</span><span class="sxs-lookup"><span data-stu-id="45422-154">If you click **Do not overwrite the file if a previous version exists**, the delivery will not occur if an existing file is detected.</span></span> <span data-ttu-id="45422-155">如果单击 **“添加更新的版本时文件名递增”**，则报表服务器将在文件名末尾追加数字，以便将其与现有的同名文件区分开。</span><span class="sxs-lookup"><span data-stu-id="45422-155">If you click **Increment file names as newer versions are added**, the report server appends a number to the file name to distinguish it from existing files of the same name.</span></span>  
  
11. <span data-ttu-id="45422-156">指定所需的报表传递时间：</span><span class="sxs-lookup"><span data-stu-id="45422-156">Specify when you want the report delivered:</span></span>  
  
    -   <span data-ttu-id="45422-157">若要计划传递时间，请单击 **“预定报表运行完成时”** ，再单击 **“选择计划”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="45422-157">To schedule a delivery time, click **When the scheduled report run is complete** and click the **Select Schedule** button.</span></span> <span data-ttu-id="45422-158">将打开计划页。</span><span class="sxs-lookup"><span data-stu-id="45422-158">A schedule page opens.</span></span>  
  
    -   <span data-ttu-id="45422-159">若要选择已具有要使用的日期、时间和重复信息的预定义共享计划，请单击 **“根据共享计划”**，然后选择要使用的计划。</span><span class="sxs-lookup"><span data-stu-id="45422-159">To select a predefined shared schedule that already has the date, time, and recurrence information that you want to use, click **On a shared schedule**, and then select the schedule to use.</span></span>  
  
    -   <span data-ttu-id="45422-160">若要在报表快照更新为较新版本时传递报表，请单击“刷新报表内容时”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="45422-160">To deliver the report when a report snapshot is updated with a newer version,click**When the report content is refreshed**.</span></span> <span data-ttu-id="45422-161">如果订阅的报表以预定间隔检索数据，则用于刷新数据的计划决定处理订阅的时间。</span><span class="sxs-lookup"><span data-stu-id="45422-161">If you are subscribing to a report that retrieves data at scheduled intervals, the schedule used to refresh the data determines when your subscription is processed.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="45422-162">此选项仅适用于已与更新计划相关联的快照。</span><span class="sxs-lookup"><span data-stu-id="45422-162">This option is available only for snapshots that are already associated with an update schedule.</span></span>  
  
12. <span data-ttu-id="45422-163">对于参数化报表，请指定要用于此订阅的报表的参数。</span><span class="sxs-lookup"><span data-stu-id="45422-163">For parameterized reports, specify parameters to use for the report for this subscription.</span></span> <span data-ttu-id="45422-164">这些参数可以与用于按需运行报表的参数或其他预定操作中使用的参数不同。</span><span class="sxs-lookup"><span data-stu-id="45422-164">The parameters can be different from those used to run the report on demand or in other scheduled operations.</span></span>  
  
 <span data-ttu-id="45422-165">报表作为静态文件传递。</span><span class="sxs-lookup"><span data-stu-id="45422-165">The report is delivered as a static file.</span></span> <span data-ttu-id="45422-166">如果报表包含交互功能（例如，指向其他行和列的链接），则这些功能不可用。</span><span class="sxs-lookup"><span data-stu-id="45422-166">If the report includes interactive features (for example, links to additional rows and columns), those features are not available.</span></span>  
  
###  <a name="to-create-an-e-mail-subscription"></a><a name="bkmk_create_email_subscription"></a><span data-ttu-id="45422-167">创建电子邮件订阅</span><span class="sxs-lookup"><span data-stu-id="45422-167">To Create an E-mail Subscription</span></span>  
  
1.  <span data-ttu-id="45422-168">在报表管理器中的 **“内容”** 页上，导航到要订阅的报表。</span><span class="sxs-lookup"><span data-stu-id="45422-168">In Report Manager, on the **Contents** page, navigate to the report you want to subscribe to.</span></span> <span data-ttu-id="45422-169">单击报表以打开它。</span><span class="sxs-lookup"><span data-stu-id="45422-169">Click the report to open it.</span></span>  
  
2.  <span data-ttu-id="45422-170">单击 **“订阅”** 选项卡，再单击 **“新建订阅”**。</span><span class="sxs-lookup"><span data-stu-id="45422-170">Click the **Subscriptions** tab, and then click **New Subscription**.</span></span>  
  
3.  <span data-ttu-id="45422-171">在 "**传递者**" 中选择 "**电子邮件**"。</span><span class="sxs-lookup"><span data-stu-id="45422-171">In **Delivered by**, select **E-Mail**.</span></span> <span data-ttu-id="45422-172">如果此传递类型不可用，则您尚未为电子邮件订阅配置报表服务器。</span><span class="sxs-lookup"><span data-stu-id="45422-172">If this delivery type is not available, your report server has not been configured for e-mail subscriptions.</span></span>  
  
4.  <span data-ttu-id="45422-173">在 "**收件人" 文本框中**，"收件人：" 字段中的收件人姓名使用您的域用户帐户自行寻址。</span><span class="sxs-lookup"><span data-stu-id="45422-173">In the **To** text box, the recipient name in the To: field is self-addressed using your domain user account.</span></span> <span data-ttu-id="45422-174">报表服务器配置设置决定“收件人”字段是否使用你的用户帐户自行填写地址。 </span><span class="sxs-lookup"><span data-stu-id="45422-174">Report server configuration settings determine whether the **To** field is self-addressed with your user account.</span></span> <span data-ttu-id="45422-175">有关更改配置设置电子邮件地址的详细信息，请参阅[为电子邮件传递配置报表服务器 &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="45422-175">For more information about changing the configuration settings e-mail addresses, see [Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="45422-176">根据所拥有的权限，您可能还可以键入您希望报表传递到的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="45422-176">Depending on your permissions, you might be able to type the e-mail address you want the report delivered to.</span></span> <span data-ttu-id="45422-177">若要指定多个电子邮件地址，请用分号 (;) 分隔它们。</span><span class="sxs-lookup"><span data-stu-id="45422-177">To specify multiple e-mail addresses, separate them with a semicolon (;).</span></span> <span data-ttu-id="45422-178">还可以在“抄送”、“密件抄送”和“答复”文本框中键入其他电子邮件地址    。</span><span class="sxs-lookup"><span data-stu-id="45422-178">You can also type additional e-mail addresses in the **Cc**, **Bcc**, and **Reply-To** text boxes.</span></span> <span data-ttu-id="45422-179">这要求您具有管理所有订阅的权限。</span><span class="sxs-lookup"><span data-stu-id="45422-179">This requires that you have permission to manage all subscriptions.</span></span>  
  
5.  <span data-ttu-id="45422-180">按如下说明选择传递选项：</span><span class="sxs-lookup"><span data-stu-id="45422-180">Select the delivery options as follows:</span></span>  
  
    -   <span data-ttu-id="45422-181">若要嵌入或附加报表副本，请选择 **“包括报表”**。</span><span class="sxs-lookup"><span data-stu-id="45422-181">To embed or attach a copy of the report, select **Include Report**.</span></span> <span data-ttu-id="45422-182">报表的格式由所选的呈现格式决定。</span><span class="sxs-lookup"><span data-stu-id="45422-182">The format of the report is determined by the rendering format you select.</span></span> <span data-ttu-id="45422-183">如果您认为报表大小会超过为电子邮件系统定义的限制，请不要选择此选项。</span><span class="sxs-lookup"><span data-stu-id="45422-183">Do not choose this option if you think the report size will exceed the limit defined for your e-mail system.</span></span>  
  
    -   <span data-ttu-id="45422-184">若要在电子邮件的正文中包括指向报表的 URL 链接，请选择 "**包括链接**"。</span><span class="sxs-lookup"><span data-stu-id="45422-184">To include a URL link to the report in the body of the e-mail message, select **Include Link**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="45422-185">如果清除这两个选项，则将只发送“主题”行中的通知文本。</span><span class="sxs-lookup"><span data-stu-id="45422-185">If you clear both of these options, only the notification text in the Subject line is sent.</span></span>  
  
6.  <span data-ttu-id="45422-186">从 **“呈现格式”** 列表框中选择一种呈现格式。</span><span class="sxs-lookup"><span data-stu-id="45422-186">Choose a rendering format from the **Render Format** list box.</span></span> <span data-ttu-id="45422-187">如果选择 **“包括报表”** 以嵌入或附加报表副本，则此选项可用。</span><span class="sxs-lookup"><span data-stu-id="45422-187">This option is available if you select **Include Report** to embed or attach a copy of the report.</span></span>  
  
    -   <span data-ttu-id="45422-188">若要在电子邮件正文中嵌入报表，请选择“Web 存档”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="45422-188">To embed the report in the body of the e-mail message, select **Web archive**.</span></span>  
  
    -   <span data-ttu-id="45422-189">若要将报表作为附件发送，请选择任一其他呈现格式。</span><span class="sxs-lookup"><span data-stu-id="45422-189">To send the report as an attachment, choose any of the other rendering formats.</span></span>  
  
7.  <span data-ttu-id="45422-190">从 **“优先级”** 列表框中选择优先级。</span><span class="sxs-lookup"><span data-stu-id="45422-190">Select a priority from the **Priority** list box.</span></span> <span data-ttu-id="45422-191">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Exchange 中，此设置可为电子邮件的重要性级别设置标志。</span><span class="sxs-lookup"><span data-stu-id="45422-191">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Exchange, this setting sets a flag for the importance level of the e-mail message.</span></span>  
  
8.  <span data-ttu-id="45422-192">指定所需的报表传递时间：</span><span class="sxs-lookup"><span data-stu-id="45422-192">Specify when you want the report delivered:</span></span>  
  
    -   <span data-ttu-id="45422-193">若要计划传递时间，请单击 **“预定报表运行完成时”** ，再单击 **“选择计划”**。</span><span class="sxs-lookup"><span data-stu-id="45422-193">To schedule a delivery time, click **When the scheduled report run is complete** and click **Select Schedule**.</span></span> <span data-ttu-id="45422-194">将打开计划页。</span><span class="sxs-lookup"><span data-stu-id="45422-194">A schedule page opens for you.</span></span>  
  
    -   <span data-ttu-id="45422-195">若要选择已具有要使用的日期、时间和重复信息的预定义共享计划，请单击 **“根据共享计划”**，然后选择要使用的计划。</span><span class="sxs-lookup"><span data-stu-id="45422-195">To select a predefined shared schedule that already has the date, time, and recurrence information that you want to use, click **On a shared schedule**, and then select the schedule to use.</span></span>  
  
    -   <span data-ttu-id="45422-196">若要在报表快照更新为较新版本时传递报表，请单击“刷新报表内容时”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="45422-196">To deliver the report when a report snapshot is updated with a newer version,click**When the report content is refreshed**.</span></span> <span data-ttu-id="45422-197">如果订阅的报表以预定间隔检索数据，则用于刷新数据的计划决定处理订阅的时间。</span><span class="sxs-lookup"><span data-stu-id="45422-197">If you are subscribing to a report that retrieves data at scheduled intervals, the schedule used to refresh the data determines when your subscription is processed.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="45422-198">此选项仅适用于已与更新计划相关联的快照。</span><span class="sxs-lookup"><span data-stu-id="45422-198">This option is available only for snapshots that are already associated with an update schedule.</span></span>  
  
9. <span data-ttu-id="45422-199">对于参数化报表，请指定要用于此订阅的报表的参数。</span><span class="sxs-lookup"><span data-stu-id="45422-199">For parameterized reports, specify parameters to use for the report for this subscription.</span></span> <span data-ttu-id="45422-200">这些参数可以与用于按需运行报表的参数或其他预定操作中使用的参数不同。</span><span class="sxs-lookup"><span data-stu-id="45422-200">The parameters that you specify can be different from those used to run the report on demand or in other scheduled operations.</span></span>  
  
##  <a name="to-modify-a-subscription"></a><a name="bkmk_modify_subscription"></a><span data-ttu-id="45422-201">修改订阅</span><span class="sxs-lookup"><span data-stu-id="45422-201">To Modify a Subscription</span></span>  
 <span data-ttu-id="45422-202">您可以随时修改订阅。</span><span class="sxs-lookup"><span data-stu-id="45422-202">You can modify a subscription at any time.</span></span> <span data-ttu-id="45422-203">在修改正在处理的订阅时，如果更新的设置在传递扩展插件接收订阅数据之前就已保存到报表服务器数据库中，则订阅将使用更新的设置。</span><span class="sxs-lookup"><span data-stu-id="45422-203">If you modify a subscription while it is being processed, the updated settings are used if they are saved to the report server database before the delivery extension receives the subscription data.</span></span> <span data-ttu-id="45422-204">否则，使用现有设置。</span><span class="sxs-lookup"><span data-stu-id="45422-204">Otherwise, the existing settings are used.</span></span>  
  
 <span data-ttu-id="45422-205">若要定位订阅，请使用 **“我的订阅”** 页或查看与报表关联的订阅定义。</span><span class="sxs-lookup"><span data-stu-id="45422-205">To locate a subscription, use the **My Subscriptions** page or view the subscription definitions that are associated with a report.</span></span> <span data-ttu-id="45422-206">您既不能直接搜索订阅，也不能根据所有者名称、触发器信息、状态信息等来搜索订阅。</span><span class="sxs-lookup"><span data-stu-id="45422-206">You cannot search for subscriptions directly, nor can you search for a subscription based on owner name, trigger information, status information, and so forth.</span></span>  
  
 <span data-ttu-id="45422-207">订阅还可以由报表服务器管理员来修改或删除。</span><span class="sxs-lookup"><span data-stu-id="45422-207">Subscriptions can also be modified or deleted by report server administrators.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="45422-208">报表服务器管理员无法从一个位置管理在给定的报表服务器上正在使用的所有单独的订阅。</span><span class="sxs-lookup"><span data-stu-id="45422-208">A report server administrator cannot manage from one place all the individual subscriptions that are in use on a given report server.</span></span> <span data-ttu-id="45422-209">但是，报表服务器管理员可以访问每个单独的订阅来进行修改或删除。</span><span class="sxs-lookup"><span data-stu-id="45422-209">However, report server administrators can access each individual subscription to modify or delete it.</span></span>  
  
##  <a name="to-delete-a-subscription"></a><a name="bkmk_delete_subscription"></a><span data-ttu-id="45422-210">删除订阅</span><span class="sxs-lookup"><span data-stu-id="45422-210">To Delete a Subscription</span></span>  
 <span data-ttu-id="45422-211">删除订阅”</span><span class="sxs-lookup"><span data-stu-id="45422-211">To delete a subscription"</span></span>  
  
1.  <span data-ttu-id="45422-212">启动 [报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="45422-212">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="45422-213">在报表管理器的全局工具栏上，单击 **“我的订阅”** ，并导航到要修改或删除的订阅。</span><span class="sxs-lookup"><span data-stu-id="45422-213">In Report Manager, click **My Subscriptions** on the global toolbar and navigate to the subscription you want to modify or delete.</span></span>  
  
3.  <span data-ttu-id="45422-214">或者，在打开的报表的 **“订阅”** 选项卡上找到要修改或删除的订阅。</span><span class="sxs-lookup"><span data-stu-id="45422-214">Alternatively, on the **Subscriptions** tab of an open report, find the subscription that you want to modify or delete.</span></span> <span data-ttu-id="45422-215">执行以下某种方案：</span><span class="sxs-lookup"><span data-stu-id="45422-215">Perform one of the following:</span></span>  
  
    1.  <span data-ttu-id="45422-216">若要修改订阅，请单击 **“编辑”**。</span><span class="sxs-lookup"><span data-stu-id="45422-216">To modify a subscription, click **Edit**.</span></span>  
  
    2.  <span data-ttu-id="45422-217">若要删除订阅，请选中订阅旁边的复选框，再单击 **“删除”**。</span><span class="sxs-lookup"><span data-stu-id="45422-217">To delete a subscription, select the check box next to the subscription, and then click **Delete**.</span></span>  
  
 <span data-ttu-id="45422-218">本主题不介绍如何取消报表服务器上当前正在处理的订阅。</span><span class="sxs-lookup"><span data-stu-id="45422-218">This topic does not explain how to cancel a subscription that is currently processing on the report server.</span></span> <span data-ttu-id="45422-219">有关取消订阅的详细信息，请参阅[管理运行中的进程](manage-a-running-process.md)</span><span class="sxs-lookup"><span data-stu-id="45422-219">For more information about canceling subscriptions, see [Manage a Running Process](manage-a-running-process.md)</span></span>  
  
 <span data-ttu-id="45422-220">如果您想终止某个订阅，但又无法轻松地定位该订阅，请记下正在接收的报表，然后按名称搜索该报表。</span><span class="sxs-lookup"><span data-stu-id="45422-220">If you want to end a subscription and you cannot locate the subscription easily, make a note of the report you are receiving and search for it by name.</span></span> <span data-ttu-id="45422-221">在访问该报表之后，您就可以从订阅中删除订阅本身。</span><span class="sxs-lookup"><span data-stu-id="45422-221">Once you access the report, you can remove yourself from the subscription.</span></span> <span data-ttu-id="45422-222">如果找不到该订阅，则该订阅可能是数据驱动订阅。</span><span class="sxs-lookup"><span data-stu-id="45422-222">If you cannot locate the subscription, the subscription may be a data-driven subscription.</span></span> <span data-ttu-id="45422-223">有关详细信息，请咨询报表服务器管理员。</span><span class="sxs-lookup"><span data-stu-id="45422-223">For more information, see your report server administrator.</span></span>  
  
 <span data-ttu-id="45422-224">如果删除了基础报表，则将自动删除订阅。</span><span class="sxs-lookup"><span data-stu-id="45422-224">A subscription is deleted automatically if the underlying report is deleted.</span></span> <span data-ttu-id="45422-225">在删除正在处理的订阅时，如果在传递扩展插件接收订阅数据之前执行删除操作，则该订阅将停止。</span><span class="sxs-lookup"><span data-stu-id="45422-225">If you delete a subscription while it is being processed, the subscription stops if the delete operation occurs before the delivery extension receives subscription data.</span></span> <span data-ttu-id="45422-226">否则，将继续处理该订阅。</span><span class="sxs-lookup"><span data-stu-id="45422-226">Otherwise, the subscription continues to be processed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45422-227">另请参阅</span><span class="sxs-lookup"><span data-stu-id="45422-227">See Also</span></span>  
 <span data-ttu-id="45422-228">[任务和权限](../security/tasks-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="45422-228">[Tasks and Permissions](../security/tasks-and-permissions.md) </span></span>  
 <span data-ttu-id="45422-229">[创建和管理 SharePoint 模式报表服务器的订阅](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md) </span><span class="sxs-lookup"><span data-stu-id="45422-229">[Create and Manage Subscriptions for SharePoint Mode Report Servers](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md) </span></span>  
 <span data-ttu-id="45422-230">[创建和管理本机模式报表服务器的订阅](../create-manage-subscriptions-native-mode-report-servers.md) </span><span class="sxs-lookup"><span data-stu-id="45422-230">[Create and Manage Subscriptions for Native Mode Report Servers](../create-manage-subscriptions-native-mode-report-servers.md) </span></span>  
 <span data-ttu-id="45422-231">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="45422-231">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span></span>  
 <span data-ttu-id="45422-232">[订阅和传递 (Reporting Services)](subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="45422-232">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span></span>  
 <span data-ttu-id="45422-233">[报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="45422-233">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="45422-234">使用我的订阅</span><span class="sxs-lookup"><span data-stu-id="45422-234">Use My Subscriptions</span></span>](use-my-subscriptions-native-mode-report-server.md)  
  
  
