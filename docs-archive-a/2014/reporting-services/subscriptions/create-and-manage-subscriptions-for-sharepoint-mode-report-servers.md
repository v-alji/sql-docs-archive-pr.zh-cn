---
title: 创建和管理 SharePoint 模式报表服务器的订阅 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], creating
- subscriptions [Reporting Services], deleting
- subscriptions [Reporting Services], managing
ms.assetid: 44be7ee2-33ce-46e4-9d1a-a20aaf43a227
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0e8798142f2284d1454b42104984424cbe7353a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589432"
---
# <a name="create-and-manage-subscriptions-for-sharepoint-mode-report-servers"></a><span data-ttu-id="48d18-102">创建和管理 SharePoint 模式报表服务器的订阅</span><span class="sxs-lookup"><span data-stu-id="48d18-102">Create and Manage Subscriptions for SharePoint Mode Report Servers</span></span>
  <span data-ttu-id="48d18-103">你可以创建 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 订阅以便从与 SharePoint 模式报表服务器集成的 SharePoint Web 应用程序传递报表。</span><span class="sxs-lookup"><span data-stu-id="48d18-103">You can create [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscriptions to deliver reports from a SharePoint Web application that is integrated with a SharePoint mode report server.</span></span> <span data-ttu-id="48d18-104">订阅可以将报表传递到文档库、文件夹或作为电子邮件传递。</span><span class="sxs-lookup"><span data-stu-id="48d18-104">Subscriptions can deliver reports to a document library, file folder, or as e-mail.</span></span> <span data-ttu-id="48d18-105">本主题概述了创建 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 订阅的要求和步骤。</span><span class="sxs-lookup"><span data-stu-id="48d18-105">This topic summarizes the requirements and steps for creating a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscription.</span></span>  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**<br /><br /> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="48d18-106">SharePoint 模式 &#124; SharePoint 2010 和 SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="48d18-106">SharePoint mode &#124; SharePoint 2010 and SharePoint 2013</span></span>|  
  
 <span data-ttu-id="48d18-107">创建订阅时，有三种方法可用于指定其传递：</span><span class="sxs-lookup"><span data-stu-id="48d18-107">When you create a subscription, there are three ways to specify its delivery:</span></span>  
  
-   <span data-ttu-id="48d18-108">**文档库**：可以创建一个订阅，用于将基于原始报表的文档传递到与原始报表位于同一 SharePoint 站点内的库。</span><span class="sxs-lookup"><span data-stu-id="48d18-108">**Document library**: You can create a subscription that delivers a document based on the original report to a library within the same SharePoint site as the original report.</span></span> <span data-ttu-id="48d18-109">不能将该文档传递到位于相同网站集内的其他服务器或其他站点。</span><span class="sxs-lookup"><span data-stu-id="48d18-109">You cannot deliver the document to a library on another server or another site within the same site collection.</span></span> <span data-ttu-id="48d18-110">若要传递此文档，您必须对该报表所传递到的库拥有“添加项”权限。</span><span class="sxs-lookup"><span data-stu-id="48d18-110">To deliver the document, you must have Add Items permission on the library to which the report is delivered.</span></span>  
  
-   <span data-ttu-id="48d18-111">**文件文件夹：** 可以将基于原始报表的文档传递到文件系统上的共享文件夹中。</span><span class="sxs-lookup"><span data-stu-id="48d18-111">**File folder:** You can deliver a document based on the original report to a shared folder on the file system.</span></span> <span data-ttu-id="48d18-112">必须选择可通过网络连接进行访问的现有文件夹。</span><span class="sxs-lookup"><span data-stu-id="48d18-112">You must select an existing folder that is accessible over a network connection.</span></span>  
  
-   <span data-ttu-id="48d18-113">**电子邮件：** 如果将报表服务器配置为使用报表服务器电子邮件传递扩展插件，则可以创建一个订阅，将报表或导出的报表文件（以输出格式保存）发送到收件箱。</span><span class="sxs-lookup"><span data-stu-id="48d18-113">**E-mail:** If the report server is configured to use the Report Server E-mail delivery extension, you can create a subscription that sends a report or an exported report file (saved in an output format) to your in-box.</span></span> <span data-ttu-id="48d18-114">若要只接收不包含报表或报表 URL 的通知，请清除 **“包含指向报表的链接”** 和 **“在邮件中显示报表”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="48d18-114">To receive just the notification without the report or report URL, clear the **Include a link to this report** and the **Show report inside message** checkboxes.</span></span>  
  
 <span data-ttu-id="48d18-115">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="48d18-115">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="48d18-116">针对订阅的一般要求</span><span class="sxs-lookup"><span data-stu-id="48d18-116">General Requirements for Subscriptions</span></span>](#bkmk_subscription_requirements)  
  
-   [<span data-ttu-id="48d18-117">创建订阅以便将报表传递到 SharePoint 库</span><span class="sxs-lookup"><span data-stu-id="48d18-117">To create a subscription to deliver a report to a SharePoint library</span></span>](#bkmk_tosharepoint_library)  
  
-   [<span data-ttu-id="48d18-118">创建订阅以便将报表传递到 SharePoint 库</span><span class="sxs-lookup"><span data-stu-id="48d18-118">To create a subscription to deliver a report to a SharePoint library</span></span>](#bkmk_tosharepoint_library)  
  
-   [<span data-ttu-id="48d18-119">为报表服务器电子邮件传递创建订阅</span><span class="sxs-lookup"><span data-stu-id="48d18-119">To create a subscription for report server e-mail delivery</span></span>](#bkmk_subscription_for_email)  
  
-   [<span data-ttu-id="48d18-120">删除或修改订阅</span><span class="sxs-lookup"><span data-stu-id="48d18-120">To view or modify a subscription</span></span>](#bkmk_to_modify_subscription)  
  
-   [<span data-ttu-id="48d18-121">删除订阅</span><span class="sxs-lookup"><span data-stu-id="48d18-121">To delete a subscription</span></span>](#bkmk_to_delete_subscription)  
  
##  <a name="general-requirements-for-subscriptions"></a><a name="bkmk_subscription_requirements"></a> <span data-ttu-id="48d18-122">针对订阅的一般要求</span><span class="sxs-lookup"><span data-stu-id="48d18-122">General Requirements for Subscriptions</span></span>  
 <span data-ttu-id="48d18-123">若要创建订阅，报表必须使用已存储凭据，并且您必须拥有查看该报表和创建警报的权限。</span><span class="sxs-lookup"><span data-stu-id="48d18-123">To create a subscription, the report must use stored credentials and you must have permission to view the report and create alerts.</span></span>  
  
 <span data-ttu-id="48d18-124">在创建订阅时，可以选择输出文件格式。</span><span class="sxs-lookup"><span data-stu-id="48d18-124">When you create a subscription, you can select an output file format.</span></span> <span data-ttu-id="48d18-125">并不是每个报表在每种格式下都能正常显示。</span><span class="sxs-lookup"><span data-stu-id="48d18-125">Not every report works well in every format.</span></span> <span data-ttu-id="48d18-126">在订阅中选择格式之前，请打开报表并将其导出为不同格式以验证是否像预期的那样显示。</span><span class="sxs-lookup"><span data-stu-id="48d18-126">Before you select a format in a subscription, open the report and export it to different formats to verify that it appears as expected.</span></span>  
  
 <span data-ttu-id="48d18-127">如果用户希望能够创建 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 订阅，则他们需要具有在 SharePoint 中“编辑项”列表的权限  。</span><span class="sxs-lookup"><span data-stu-id="48d18-127">Users require **Edit Items** list permission in SharePoint if they want to be able to create [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscriptions.</span></span> <span data-ttu-id="48d18-128">有关详细信息，请参阅 [报表服务器项的 SharePoint 站点和列表权限参考](../security/sharepoint-site-and-list-permission-reference-for-report-server-items.md)</span><span class="sxs-lookup"><span data-stu-id="48d18-128">For more information, see [SharePoint Site and List Permission Reference for Report Server Items](../security/sharepoint-site-and-list-permission-reference-for-report-server-items.md)</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="48d18-129">用来将报表传递到库或共享文件夹的订阅会创建一个基于原始报表的新静态文件，但它不是在报表查看器 Web 部件中运行的真正报表定义。</span><span class="sxs-lookup"><span data-stu-id="48d18-129">A subscription that delivers a report to a library or to a shared folder creates a new, static file that is based on the original report, but it is not a true report definition that runs in the Report Viewer Web Part.</span></span> <span data-ttu-id="48d18-130">如果原始报表具有交互功能（如钻取链接）或动态内容，则这些功能在传递到目标位置的静态文件中将不可用。</span><span class="sxs-lookup"><span data-stu-id="48d18-130">If the original report has interactive features (such as drillthrough links) or dynamic content, those features will not be available in the static file that is delivered to the target location.</span></span> <span data-ttu-id="48d18-131">如果选择“网页”，则可以保留一些交互功能，但由于该文档不是在报表查看器中运行的 .rdl 文件，因此在报表中单击浏览时将会在浏览器会话中创建一些新页，必须在这些新页中滚动才能返回站点。</span><span class="sxs-lookup"><span data-stu-id="48d18-131">If you select a "Web Page" you can preserve some interactivity, but because the document is not an .rdl file that runs in the Report Viewer, clicking through a report creates new pages in the browser session that you must scroll through to return to the site.</span></span>  
  
 <span data-ttu-id="48d18-132">无法将导出报表的文件扩展名重命名为“.rdl”并使该报表在报表查看器 Web 部件中运行。</span><span class="sxs-lookup"><span data-stu-id="48d18-132">You cannot rename the file name extension of an exported report to .rdl and have it run in the Report Viewer Web Part.</span></span> <span data-ttu-id="48d18-133">如果要创建可提供实际报表的订阅，则使用报表服务器电子邮件传递扩展插件并设置选项以包括指向报表的链接。</span><span class="sxs-lookup"><span data-stu-id="48d18-133">If you want to create a subscription that provides an actual report, use the Report Server E-mail delivery extension and set options to include a link to the report.</span></span>  
  
 <span data-ttu-id="48d18-134">包含所传递文档的库的版本设置确定每次传递是否要创建文档的新版本。</span><span class="sxs-lookup"><span data-stu-id="48d18-134">Version settings on the library that contains the delivered document determine whether a new version of the document is created with each delivery.</span></span> <span data-ttu-id="48d18-135">默认情况下，为每个库启用版本设置。</span><span class="sxs-lookup"><span data-stu-id="48d18-135">By default, version settings are enabled for each library.</span></span> <span data-ttu-id="48d18-136">除非专门选择 **“无版本控制”** ，否则传递时将为文档创建新的主版本。</span><span class="sxs-lookup"><span data-stu-id="48d18-136">Unless you specifically choose **No versioning**, a new major version of the document will be created upon delivery.</span></span> <span data-ttu-id="48d18-137">只创建文档的主版本；订阅传递从不创建次版本，即使选择了允许次版本的版本控制选项。</span><span class="sxs-lookup"><span data-stu-id="48d18-137">Only major versions of the document are created; minor versions are never created as a result of subscription delivery, even if you select a versioning option that allows minor versions.</span></span> <span data-ttu-id="48d18-138">如果您限制保留的主版本数量，则当达到最大限制值时，较早的传递将被更新的传递替代。</span><span class="sxs-lookup"><span data-stu-id="48d18-138">If you limit the number of major versions that are retained, older deliveries will be replaced by newer ones when the maximum limit is reached.</span></span>  
  
 <span data-ttu-id="48d18-139">为订阅选择的输出格式基于在报表服务器上安装的呈现扩展插件。</span><span class="sxs-lookup"><span data-stu-id="48d18-139">Output formats that you select for a subscription are based on rendering extensions that are installed on the report server.</span></span> <span data-ttu-id="48d18-140">您只能选择报表服务器上的呈现扩展插件所支持的输出格式。</span><span class="sxs-lookup"><span data-stu-id="48d18-140">You can only select output formats that are supported by the rendering extensions on the report server.</span></span>  
  
###  <a name="to-create-a-subscription-to-deliver-a-report-to-a-sharepoint-library"></a><a name="bkmk_tosharepoint_library"></a> <span data-ttu-id="48d18-141">创建订阅以便将报表传递到 SharePoint 库</span><span class="sxs-lookup"><span data-stu-id="48d18-141">To create a subscription to deliver a report to a SharePoint library</span></span>  
  
1.  <span data-ttu-id="48d18-142">浏览到包含报表的 SharePoint 库。</span><span class="sxs-lookup"><span data-stu-id="48d18-142">Browse to a SharePoint library that contains your report.</span></span>  
  
2.  <span data-ttu-id="48d18-143">单击该报表旁边的向下箭头，然后选择“管理订阅”  。</span><span class="sxs-lookup"><span data-stu-id="48d18-143">Click the down arrow next to the report and then select **Manage Subscriptions**.</span></span>  
  
3.  <span data-ttu-id="48d18-144">单击“添加订阅”  。</span><span class="sxs-lookup"><span data-stu-id="48d18-144">Click **Add Subscription**.</span></span>  
  
4.  <span data-ttu-id="48d18-145">在 **“传递扩展插件”** 中选择 **“SharePoint 文档库”** 。</span><span class="sxs-lookup"><span data-stu-id="48d18-145">In **Delivery Extension**, select **SharePoint Document Library**.</span></span>  
  
5.  <span data-ttu-id="48d18-146">在 **“文档库”** 中，选择同一站点中的库。</span><span class="sxs-lookup"><span data-stu-id="48d18-146">In **Document Library**, select a library within the same site.</span></span>  
  
6.  <span data-ttu-id="48d18-147">在 **“文件选项”** 中，为将由订阅创建的文档指定文件名和标题。</span><span class="sxs-lookup"><span data-stu-id="48d18-147">In **File Options**, specify the file name and title for the document that will be created by the subscription.</span></span>  
  
7.  <span data-ttu-id="48d18-148">在 **“输出格式”** 中，选择应用程序格式。</span><span class="sxs-lookup"><span data-stu-id="48d18-148">In **Output Format**, select the application format.</span></span>  
  
     <span data-ttu-id="48d18-149">“Web 存档 (MHTML)”是默认值，这是因为它会生成自包含的 HTML 文件，但不会保留原始报表中可能存在的交互式报表功能。</span><span class="sxs-lookup"><span data-stu-id="48d18-149">Web archive (MHTML) is the default because it produces a self-contained HTML file, but it will not preserve interactive report features that might be in the original report.</span></span>  
  
8.  <span data-ttu-id="48d18-150">在 **“覆盖选项”** 中，指定用于确定后续传递是否覆盖文件的选项。</span><span class="sxs-lookup"><span data-stu-id="48d18-150">In **Overwrite Options**, specify an option that determines whether subsequent deliveries overwrite a file.</span></span> <span data-ttu-id="48d18-151">如果要保留以前的传递，可以选择 **“使用唯一名称创建文件”** 。</span><span class="sxs-lookup"><span data-stu-id="48d18-151">If you want to preserve previous deliveries, you can select **Create a file with a unique name**.</span></span> <span data-ttu-id="48d18-152">将向新文件追加数字以创建唯一的文件名。</span><span class="sxs-lookup"><span data-stu-id="48d18-152">A number will be appended to new files to create a unique file name.</span></span>  
  
9. <span data-ttu-id="48d18-153">在 **“传递事件”** 中，指定会导致订阅运行的计划或事件。</span><span class="sxs-lookup"><span data-stu-id="48d18-153">In **Delivery Event**, specify a schedule or event that causes the subscription to run.</span></span> <span data-ttu-id="48d18-154">您可以创建自定义计划，选择共享计划（如果可用），或者在使用快照数据运行的报表的数据被刷新时运行订阅。</span><span class="sxs-lookup"><span data-stu-id="48d18-154">You can create a custom schedule, select a shared schedule if one is available, or run the subscription whenever the data is refreshed for a report that runs with snapshot data.</span></span> <span data-ttu-id="48d18-155">有关计划和数据处理的详细信息，请参阅[设置处理选项（SharePoint 集成模式下的 Reporting Services）](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="48d18-155">For more information about schedules and data processing, see [Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md).</span></span>  
  
10. <span data-ttu-id="48d18-156">在 **“参数”** 中，如果所创建的是参数化报表的订阅，请指定处理订阅时要在该报表中使用的值。</span><span class="sxs-lookup"><span data-stu-id="48d18-156">In **Parameters**, if you are creating a subscription to a parameterized report, specify the values that you want to use with the report when the subscription is processed.</span></span> <span data-ttu-id="48d18-157">如果所选报表不包含参数，则“参数”部分在此页上不可见。</span><span class="sxs-lookup"><span data-stu-id="48d18-157">The parameters section is not visible on this page if the report you select does not contain parameters.</span></span> <span data-ttu-id="48d18-158">有关参数的详细信息，请参阅[在已发布报表上设置参数（SharePoint 集成模式下的 Reporting Services）](../report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="48d18-158">For more information about parameters, see [Set Parameters on a Published Report &#40;Reporting Services in SharePoint Integrated Mode&#41;](../report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md).</span></span>  
  
###  <a name="to-create-a-subscription-for-shared-folder-delivery"></a><a name="bkmk_subscription_for_sharedfolder"></a> <span data-ttu-id="48d18-159">为共享文件夹传递创建订阅</span><span class="sxs-lookup"><span data-stu-id="48d18-159">To create a subscription for shared folder delivery</span></span>  
  
1.  <span data-ttu-id="48d18-160">浏览到包含报表的 SharePoint 库。</span><span class="sxs-lookup"><span data-stu-id="48d18-160">Browse to a SharePoint library that contains your report.</span></span>  
  
2.  <span data-ttu-id="48d18-161">单击该报表旁边的向下箭头，然后选择“管理订阅”  。</span><span class="sxs-lookup"><span data-stu-id="48d18-161">Click the down arrow next to the report and then select **Manage Subscriptions**.</span></span>  
  
3.  <span data-ttu-id="48d18-162">单击“添加订阅”  。</span><span class="sxs-lookup"><span data-stu-id="48d18-162">Click **Add Subscription**.</span></span>  
  
4.  <span data-ttu-id="48d18-163">在 **“传递扩展插件”** 中选择 **“Windows 文件共享”** 。</span><span class="sxs-lookup"><span data-stu-id="48d18-163">In **Delivery Extension**, select **Windows File Share**.</span></span>  
  
5.  <span data-ttu-id="48d18-164">在 **“文件名”** 中，输入将在共享文件夹中创建的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="48d18-164">In **File Name**, enter the name of the file that will be created in the shared folder.</span></span>  
  
6.  <span data-ttu-id="48d18-165">在“路径”中，使用包含计算机网络名称的通用命名约定 (UNC) 格式输入文件夹路径  。</span><span class="sxs-lookup"><span data-stu-id="48d18-165">In **Path**, enter a folder path in Uniform Naming Convention (UNC) format that includes the computer's network name.</span></span> <span data-ttu-id="48d18-166">不能在文件夹路径中包含尾随反斜杠。</span><span class="sxs-lookup"><span data-stu-id="48d18-166">Do not include trailing backslashes in the folder path.</span></span> <span data-ttu-id="48d18-167">示例路径可如下所示： `\\ComputerName01\Public\MyReports`，其中 Public 和 MyReports 是共享文件夹。</span><span class="sxs-lookup"><span data-stu-id="48d18-167">An example path might be `\\ComputerName01\Public\MyReports`, where Public and MyReports are shared folders.</span></span>  
  
7.  <span data-ttu-id="48d18-168">在 **“呈现格式”** 中，为该报表选择应用程序格式。</span><span class="sxs-lookup"><span data-stu-id="48d18-168">In **Render Format**, select the application format for the report.</span></span>  
  
8.  <span data-ttu-id="48d18-169">在 **“写入模式”** 中，选择 **“无”** 、 **“Autoincrement”** 或 **“覆盖”** 。</span><span class="sxs-lookup"><span data-stu-id="48d18-169">In **Write Mode**, choose between **None**, **Autoincrement**, or **Overwrite**.</span></span> <span data-ttu-id="48d18-170">这些选项将确定后续传递是否会覆盖文件。</span><span class="sxs-lookup"><span data-stu-id="48d18-170">These options determine whether subsequent deliveries overwrite a file.</span></span> <span data-ttu-id="48d18-171">如果要保留以前的传递，可以选择 **“Autoincrement”** 。</span><span class="sxs-lookup"><span data-stu-id="48d18-171">If you want to preserve previous deliveries, you can choose **Autoincrement**.</span></span> <span data-ttu-id="48d18-172">将向新文件追加数字以创建唯一的文件名。</span><span class="sxs-lookup"><span data-stu-id="48d18-172">A number will be appended to new files to create a unique file name.</span></span> <span data-ttu-id="48d18-173">如果选择 **“无”** ，当目标位置已存在具有相同名称的文件时，将不会进行传递。</span><span class="sxs-lookup"><span data-stu-id="48d18-173">If you choose **None**, no delivery will occur if a file of the same name already exists in the target location.</span></span>  
  
9. <span data-ttu-id="48d18-174">在 **“文件扩展名”** 中，选择 **True** 以添加与应用程序文件格式相对应的文件扩展名，或选择 False 以创建不具有扩展名的文件。</span><span class="sxs-lookup"><span data-stu-id="48d18-174">In **File Extension**, choose **True** to add a file name extension that corresponds to the application file format, or False to create the file without an extension.</span></span>  
  
10. <span data-ttu-id="48d18-175">在 **“用户名”** 和 **“密码”** 中，输入对共享文件夹具有写权限的凭据。</span><span class="sxs-lookup"><span data-stu-id="48d18-175">In **User Name** and **Password**, enter credentials that have write permissions on the shared folder.</span></span>  
  
11. <span data-ttu-id="48d18-176">在 **“传递事件”** 中，指定会导致订阅运行的计划或事件。</span><span class="sxs-lookup"><span data-stu-id="48d18-176">In **Delivery Event**, specify a schedule or event that causes the subscription to run.</span></span> <span data-ttu-id="48d18-177">您可以创建自定义计划，选择共享计划（如果可用），或者在使用快照数据运行的报表的数据被刷新时运行订阅。</span><span class="sxs-lookup"><span data-stu-id="48d18-177">You can create a custom schedule, select a shared schedule if one is available, or run the subscription whenever the data is refreshed for a report that runs with snapshot data.</span></span> <span data-ttu-id="48d18-178">有关计划和数据处理的详细信息，请参阅[设置处理选项（SharePoint 集成模式下的 Reporting Services）](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="48d18-178">For more information about schedules and data processing, see [Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md).</span></span>  
  
12. <span data-ttu-id="48d18-179">在 **“参数”** 中，如果所创建的是参数化报表的订阅，请指定处理订阅时要在该报表中使用的值。</span><span class="sxs-lookup"><span data-stu-id="48d18-179">In **Parameters**, if you are creating a subscription to a parameterized report, specify the values that you want to use with the report when the subscription is processed.</span></span> <span data-ttu-id="48d18-180">有关参数的详细信息，请参阅[在已发布报表上设置参数（SharePoint 集成模式下的 Reporting Services）](../report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="48d18-180">For more information about parameters, see [Set Parameters on a Published Report &#40;Reporting Services in SharePoint Integrated Mode&#41;](../report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md).</span></span>  
  
###  <a name="to-create-a-subscription-for-report-server-e-mail-delivery"></a><a name="bkmk_subscription_for_email"></a> <span data-ttu-id="48d18-181">为报表服务器电子邮件传递创建订阅</span><span class="sxs-lookup"><span data-stu-id="48d18-181">To create a subscription for report server e-mail delivery</span></span>  
  
1.  <span data-ttu-id="48d18-182">浏览到包含报表的 SharePoint 库。</span><span class="sxs-lookup"><span data-stu-id="48d18-182">Browse to a SharePoint library that contains your report.</span></span>  
  
2.  <span data-ttu-id="48d18-183">单击该报表旁边的向下箭头，然后选择“管理订阅”  。</span><span class="sxs-lookup"><span data-stu-id="48d18-183">Click the down arrow next to the report and then select **Manage Subscriptions**.</span></span>  
  
3.  <span data-ttu-id="48d18-184">单击“添加订阅”  。</span><span class="sxs-lookup"><span data-stu-id="48d18-184">Click **Add Subscription**.</span></span>  
  
4.  <span data-ttu-id="48d18-185">在“传递扩展插件”中，选择“电子邮件”   。</span><span class="sxs-lookup"><span data-stu-id="48d18-185">In **Delivery Extension**, select **E-mail**.</span></span>  
  
5.  <span data-ttu-id="48d18-186">在“传递选项”中，指定要将该报表发送到的电子邮件地址  。</span><span class="sxs-lookup"><span data-stu-id="48d18-186">In **Delivery options**, specify an e-mail address to send the report to.</span></span>  
  
6.  <span data-ttu-id="48d18-187">您也可以修改“主题”行。</span><span class="sxs-lookup"><span data-stu-id="48d18-187">Optionally, you can modify the Subject line.</span></span> <span data-ttu-id="48d18-188">“主题”行使用内置参数，这些内置参数可捕获报表的名称和处理时间。</span><span class="sxs-lookup"><span data-stu-id="48d18-188">The Subject line uses built-in parameters that capture the report name and time when it was processed.</span></span> <span data-ttu-id="48d18-189">这些是仅有的可供使用的内置参数。</span><span class="sxs-lookup"><span data-stu-id="48d18-189">These are the only built-in parameters that can be used.</span></span> <span data-ttu-id="48d18-190">参数是用于自定义在“主题”行中显示的文本的占位符，但您可以将该文本替换为静态文本。</span><span class="sxs-lookup"><span data-stu-id="48d18-190">The parameters are placeholders that customize the text that appears in the Subject line, but you can replace it with static text.</span></span>  
  
7.  <span data-ttu-id="48d18-191">要在邮件的正文中嵌入报表 URL，请选择 **“包含指向报表的链接”** 。</span><span class="sxs-lookup"><span data-stu-id="48d18-191">Choose **Include a link to this report** if you want to embed a report URL in the body of the message.</span></span>  
  
8.  <span data-ttu-id="48d18-192">在 **“报表内容”** 中，指定是否要在邮件正文嵌入实际的报表。</span><span class="sxs-lookup"><span data-stu-id="48d18-192">In **Report Contents**, specify whether you want to embed the actual report in the body of the message.</span></span>  
  
     <span data-ttu-id="48d18-193">呈现格式和浏览器决定了报表是嵌入的还是作为附件发送。</span><span class="sxs-lookup"><span data-stu-id="48d18-193">The rendering format and browser determine whether the report is embedded or attached.</span></span> <span data-ttu-id="48d18-194">如果您的浏览器支持 HTML 4.0 和 MHTML，并且您选择了 Web 存档呈现格式，那么报表将嵌入为邮件的一部分。</span><span class="sxs-lookup"><span data-stu-id="48d18-194">If your browser supports HTML 4.0 and MHTML, and you select the Web archive rendering format, the report is embedded as part of the message.</span></span> <span data-ttu-id="48d18-195">其他所有呈现格式（CSV、PDF 等）都将报表作为附件进行传递。</span><span class="sxs-lookup"><span data-stu-id="48d18-195">All other rendering formats (CSV, PDF, and so on) deliver reports as attachments.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="48d18-196">不会检查附件或邮件的大小。</span><span class="sxs-lookup"><span data-stu-id="48d18-196">does not check the size of the attachment or message before sending the report.</span></span> <span data-ttu-id="48d18-197">如果附件或邮件的大小超过了邮件服务器所允许的最大限制，则无法传递报表。</span><span class="sxs-lookup"><span data-stu-id="48d18-197">If the attachment or message exceeds the maximum limit allowed by your mail server, the report will not be delivered.</span></span> <span data-ttu-id="48d18-198">为大型报表选择其他传递选项之一（例如 URL 或通知）。</span><span class="sxs-lookup"><span data-stu-id="48d18-198">Choose one of the other delivery options (such as URL or notification) for large reports.</span></span>  
  
9. <span data-ttu-id="48d18-199">在 **“传递事件”** 中，指定会导致订阅运行的计划或事件。</span><span class="sxs-lookup"><span data-stu-id="48d18-199">In **Delivery Event**, specify a schedule or event that causes the subscription to run.</span></span> <span data-ttu-id="48d18-200">您可以创建自定义计划，选择共享计划（如果可用），或者在使用快照数据运行的报表的数据被刷新时运行订阅。</span><span class="sxs-lookup"><span data-stu-id="48d18-200">You can create a custom schedule, select a shared schedule if one is available, or run the subscription whenever the data is refreshed for a report that runs with snapshot data.</span></span> <span data-ttu-id="48d18-201">有关计划和数据处理的详细信息，请参阅[设置处理选项（SharePoint 集成模式下的 Reporting Services）](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="48d18-201">For more information about schedules and data processing, see [Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md).</span></span>  
  
10. <span data-ttu-id="48d18-202">在 **“参数”** 中，如果所创建的是参数化报表的订阅，请指定处理订阅时要在该报表中使用的值。</span><span class="sxs-lookup"><span data-stu-id="48d18-202">In **Parameters**, if you are creating a subscription to a parameterized report, specify the values that you want to use with the report when the subscription is processed.</span></span> <span data-ttu-id="48d18-203">有关参数的详细信息，请参阅[在已发布报表上设置参数（SharePoint 集成模式下的 Reporting Services）](../report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="48d18-203">For more information about parameters, see [Set Parameters on a Published Report &#40;Reporting Services in SharePoint Integrated Mode&#41;](../report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md).</span></span>  
  
###  <a name="to-view-or-modify-a-subscription"></a><a name="bkmk_to_modify_subscription"></a> <span data-ttu-id="48d18-204">删除或修改订阅</span><span class="sxs-lookup"><span data-stu-id="48d18-204">To view or modify a subscription</span></span>  
  
1.  <span data-ttu-id="48d18-205">浏览到包含报表的 SharePoint 库。</span><span class="sxs-lookup"><span data-stu-id="48d18-205">Browse to a SharePoint library that contains your report.</span></span>  
  
2.  <span data-ttu-id="48d18-206">单击该报表旁边的向下箭头，然后单击“管理订阅”  。</span><span class="sxs-lookup"><span data-stu-id="48d18-206">Click the down arrow next to the report and then click **Manage Subscriptions**.</span></span>  
  
3.  <span data-ttu-id="48d18-207">每个订阅都按照传递类型进行标识。</span><span class="sxs-lookup"><span data-stu-id="48d18-207">Each subscription is identified by the type of delivery.</span></span> <span data-ttu-id="48d18-208">单击订阅类型，以便查看和更改现有属性。</span><span class="sxs-lookup"><span data-stu-id="48d18-208">Click the subscription type to view and change the existing properties.</span></span>  
  
###  <a name="to-delete-a-subscription"></a><a name="bkmk_to_delete_subscription"></a> <span data-ttu-id="48d18-209">删除订阅</span><span class="sxs-lookup"><span data-stu-id="48d18-209">To delete a subscription</span></span>  
  
1.  <span data-ttu-id="48d18-210">浏览到包含报表的 SharePoint 库。</span><span class="sxs-lookup"><span data-stu-id="48d18-210">Browse to a SharePoint library that contains your report.</span></span>  
  
2.  <span data-ttu-id="48d18-211">单击该报表旁边的向下箭头，然后单击“管理订阅”  。</span><span class="sxs-lookup"><span data-stu-id="48d18-211">Click the down arrow next to the report and then click **Manage Subscriptions**.</span></span>  
  
3.  <span data-ttu-id="48d18-212">单击订阅旁的复选框，然后单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="48d18-212">Click the checkbox next to the subscription, and click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48d18-213">另请参阅</span><span class="sxs-lookup"><span data-stu-id="48d18-213">See Also</span></span>  
 <span data-ttu-id="48d18-214">[订阅和传递 (Reporting Services)](subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="48d18-214">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span></span>  
 <span data-ttu-id="48d18-215">[Reporting Services 中的电子邮件传递](e-mail-delivery-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="48d18-215">[E-Mail Delivery in Reporting Services](e-mail-delivery-in-reporting-services.md) </span></span>  
 <span data-ttu-id="48d18-216">[Reporting Services 中的文件共享传递](file-share-delivery-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="48d18-216">[File Share Delivery in Reporting Services](file-share-delivery-in-reporting-services.md) </span></span>  
 <span data-ttu-id="48d18-217">[Reporting Services 中的 SharePoint 库传递](sharepoint-library-delivery-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="48d18-217">[SharePoint Library Delivery in Reporting Services](sharepoint-library-delivery-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="48d18-218">配置报表服务器，以便 &#40;SSRS Configuration Manager 发送电子邮件&#41;</span><span class="sxs-lookup"><span data-stu-id="48d18-218">Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
  
  
