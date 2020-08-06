---
title: " (报表管理器) 的 \"新建订阅\" 或 \"编辑订阅\" 页 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e02d6529-ce67-4305-b7f0-433997e99c21
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d74f5bf9bee537522d625f37d6b077fdfed5b2ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578692"
---
# <a name="new-subscription-or-edit-subscription-page-report-manager"></a><span data-ttu-id="b1a2b-102">“新建订阅”或“编辑订阅”页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="b1a2b-102">New Subscription or Edit Subscription Page (Report Manager)</span></span>
  <span data-ttu-id="b1a2b-103">使用“新建订阅”或“编辑订阅”页，可为报表创建新订阅或修改报表的现有订阅。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-103">Use the New Subscription or Edit Subscription page to create a new subscription or modify an existing subscription to a report.</span></span> <span data-ttu-id="b1a2b-104">此页包含的选项取决于您的角色分配。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-104">The options on this page vary depending on your role assignment.</span></span> <span data-ttu-id="b1a2b-105">具有高级权限的用户可以使用附加选项。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-105">Users with advanced permissions can work with additional options.</span></span>  
  
 <span data-ttu-id="b1a2b-106">以无人参与的方式运行的报表支持订阅。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-106">Subscriptions are supported for reports that can run unattended.</span></span> <span data-ttu-id="b1a2b-107">报表必须最起码使用已存储的凭据或不使用凭据。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-107">At a minimum, the report must use stored or no credentials.</span></span> <span data-ttu-id="b1a2b-108">如果报表使用参数，则必须指定默认值。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-108">If the report uses parameters, a default value must be specified.</span></span> <span data-ttu-id="b1a2b-109">如果更改报表执行设置或删除参数属性使用的默认值，订阅可能进入非活动状态。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-109">Subscriptions may become inactive if you change report execution settings or remove the default values used by parameter properties.</span></span> <span data-ttu-id="b1a2b-110">有关详细信息，请参阅 [创建和管理本机模式报表服务器的订阅](../../2014/reporting-services/create-manage-subscriptions-native-mode-report-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-110">For more information, see [Create and Manage Subscriptions for Native Mode Report Servers](../../2014/reporting-services/create-manage-subscriptions-native-mode-report-servers.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b1a2b-111">并非在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的每个版本中均提供此功能。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-111">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b1a2b-112">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-112">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="b1a2b-113">导航</span><span class="sxs-lookup"><span data-stu-id="b1a2b-113">Navigation</span></span>  
 <span data-ttu-id="b1a2b-114">使用以下过程导航到用户界面 (UI) 中的这一位置。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-114">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-new-subscription-or-edit-subscription-page"></a><span data-ttu-id="b1a2b-115">打开“新建订阅”或“编辑订阅”页</span><span class="sxs-lookup"><span data-stu-id="b1a2b-115">To open the New Subscription or Edit Subscription page</span></span>  
  
1.  <span data-ttu-id="b1a2b-116">打开报表管理器，找到要添加订阅的报表。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-116">Open Report Manager, and locate the report for which you want to add a subscription.</span></span>  
  
2.  <span data-ttu-id="b1a2b-117">悬停在该报表之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-117">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="b1a2b-118">在下拉菜单中，执行以下步骤之一：</span><span class="sxs-lookup"><span data-stu-id="b1a2b-118">In the drop-down menu, do one of the following:</span></span>  
  
    -   <span data-ttu-id="b1a2b-119">单击“管理”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="b1a2b-119">Click **Manage**.</span></span> <span data-ttu-id="b1a2b-120">这会打开该报表的“常规”属性页。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-120">This opens the General properties page for the report.</span></span> <span data-ttu-id="b1a2b-121">然后选择 "**订阅**" 选项卡。在工具栏中，单击 "**新建订阅**"，或选择现有订阅并单击 "**编辑**"。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-121">Then select the **Subscriptions** tab. In the toolbar, click **New Subscription**, or select an existing subscription and click **Edit**.</span></span>  
  
    -   <span data-ttu-id="b1a2b-122">单击 **“订阅”**。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-122">Click **Subscribe**.</span></span> <span data-ttu-id="b1a2b-123">这会打开该报表的 **“新建订阅”** 页。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-123">This opens the **New Subscription** page for the report.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b1a2b-124">选项</span><span class="sxs-lookup"><span data-stu-id="b1a2b-124">Options</span></span>  
 <span data-ttu-id="b1a2b-125">**传递者**</span><span class="sxs-lookup"><span data-stu-id="b1a2b-125">**Delivered by**</span></span>  
 <span data-ttu-id="b1a2b-126">选择用于分发报表的传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-126">Select the delivery extension to use to distribute the report.</span></span> <span data-ttu-id="b1a2b-127">根据选定的传递扩展插件，会显示下列设置：</span><span class="sxs-lookup"><span data-stu-id="b1a2b-127">Depending on the delivery extension you select, the following settings appear:</span></span>  
  
-   <span data-ttu-id="b1a2b-128">电子邮件订阅提供了电子邮件用户所熟悉的字段 (例如，"**目标**"、"**主题**" 和 "**优先级**" 字段) 。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-128">E-mail subscriptions provide fields that are familiar to e-mail users (for example, **To**, **Subject**, and **Priority** fields).</span></span> <span data-ttu-id="b1a2b-129">指定 **“包括报表”** 可以嵌入或附加报表，而指定 **“包括链接”** 可以将 URL 包括在报表中。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-129">Specify **Include Report** to embed or attach the report, or **Include Link** to include a URL to the report.</span></span> <span data-ttu-id="b1a2b-130">指定 **“呈现格式”** 可以选择附加报表或嵌入报表的显示格式。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-130">Specify **Render Format** to choose a presentation format for the attached or embedded report.</span></span>  
  
-   <span data-ttu-id="b1a2b-131">文件共享订阅提供了允许您指定目标位置的字段。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-131">File share subscriptions provide fields that allow you to specify a target location.</span></span> <span data-ttu-id="b1a2b-132">您可以将任何报表传递到文件共享位置。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-132">You can deliver any report to a file share.</span></span> <span data-ttu-id="b1a2b-133">但是，支持交互式功能的报表（包括支持深化以及支持行和列的矩阵报表）将以静态文件的形式呈现。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-133">However, reports that support interactive features (including matrix reports that support drill-down to supporting rows and columns) are rendered as static files.</span></span> <span data-ttu-id="b1a2b-134">无法查看静态文件中的深化行和深化列。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-134">You cannot view drill-down rows and columns in a static file.</span></span> <span data-ttu-id="b1a2b-135">文件共享名称必须以统一命名约定 (UNC) 格式指定 (例如， \\ \mycomputer\public\myreportfiles) 。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-135">The file share name must be specified in Uniform Naming Convention (UNC) format (for example, \\\mycomputer\public\myreportfiles).</span></span> <span data-ttu-id="b1a2b-136">不能在路径名的末尾包含反斜杠。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-136">Do not include a trailing backslash in the path name.</span></span> <span data-ttu-id="b1a2b-137">报表文件将以基于呈现格式的文件格式进行传递（例如，如果选择 **Excel**，则报表以 .xls 文件格式进行传递）。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-137">The report file will be delivered in a file format that is based on the render format (for example, if you choose **Excel**, the report is delivered as an .xls file).</span></span>  
  
 <span data-ttu-id="b1a2b-138">传递扩展插件的可用性取决于其是否在报表服务器上进行了安装和配置。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-138">The availability of a delivery extension depends on whether it is installed and configured on the report server.</span></span> <span data-ttu-id="b1a2b-139">报表服务器电子邮件是默认的传递扩展插件，但是使用前必须先行配置。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-139">Report Server E-mail is the default delivery extension, but it must be configured before you can use it.</span></span> <span data-ttu-id="b1a2b-140">文件共享传递不需要配置，但是使用前必须定义一个共享文件夹。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-140">File Share delivery does not require configuration, but you must define a shared folder before you can use it.</span></span>  
  
## <a name="subscription-processing-options"></a><span data-ttu-id="b1a2b-141">订阅处理选项</span><span class="sxs-lookup"><span data-stu-id="b1a2b-141">Subscription Processing Options</span></span>  
 <span data-ttu-id="b1a2b-142">使用这些设置可以定义导致处理订阅的条件。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-142">Use these settings to define the conditions that cause a subscription to process.</span></span> <span data-ttu-id="b1a2b-143">某些选项仅可用于使用参数的报表或作为报表执行快照运行的报表。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-143">Some of the options are only available for reports that use parameters or that run as report execution snapshots.</span></span>  
  
 <span data-ttu-id="b1a2b-144">**刷新报表内容时**</span><span class="sxs-lookup"><span data-stu-id="b1a2b-144">**When the report content is refreshed**</span></span>  
 <span data-ttu-id="b1a2b-145">选择此选项可以订阅定期刷新的报表快照。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-145">Select this option to subscribe to a report snapshot that is refreshed on a scheduled basis.</span></span> <span data-ttu-id="b1a2b-146">只有在订阅作为报表执行快照运行的报表时才显示此选项。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-146">This option is visible only when you are subscribing to a report that runs as a report execution snapshot.</span></span> <span data-ttu-id="b1a2b-147">报表执行快照的内容通常定期刷新。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-147">The content for a report execution snapshot is typically refreshed on a schedule.</span></span> <span data-ttu-id="b1a2b-148">对于以此模式运行的报表，可以定义在刷新快照时进行订阅。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-148">For reports that run in this mode, you can define a subscription to occur when the snapshot is refreshed.</span></span>  
  
 <span data-ttu-id="b1a2b-149">**预定报表运行完成时**</span><span class="sxs-lookup"><span data-stu-id="b1a2b-149">**When the scheduled report run is complete**</span></span>  
 <span data-ttu-id="b1a2b-150">创建计划以确定何时处理订阅。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-150">Create a schedule that determines when the subscription is processed.</span></span>  
  
 <span data-ttu-id="b1a2b-151">**根据共享计划**</span><span class="sxs-lookup"><span data-stu-id="b1a2b-151">**On a shared schedule**</span></span>  
 <span data-ttu-id="b1a2b-152">选择处理订阅的预定义计划。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-152">Select a predefined schedule to process the subscription.</span></span>  
  
 <span data-ttu-id="b1a2b-153">**输入参数值**</span><span class="sxs-lookup"><span data-stu-id="b1a2b-153">**Enter parameter values**</span></span>  
 <span data-ttu-id="b1a2b-154">如果订阅具有参数的报表，请使用此选项。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-154">Use this option when you are subscribing to a report that has parameters.</span></span> <span data-ttu-id="b1a2b-155">此选项仅可用于参数化报表。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-155">This option is available only for parameterized reports.</span></span> <span data-ttu-id="b1a2b-156">订阅参数化报表时，可以指定一些参数值，用于创建通过订阅传递的报表版本。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-156">When subscribing to a parameterized report, you can specify the parameter values that are used to create the version of the report that is delivered through the subscription.</span></span> <span data-ttu-id="b1a2b-157">例如，您可以指定区域代码以选择特定区域的销售数据。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-157">For example, you can specify a region code to select sales data for a particular region.</span></span> <span data-ttu-id="b1a2b-158">如果不指定值，将使用默认值。</span><span class="sxs-lookup"><span data-stu-id="b1a2b-158">If you do not specify a value, the default value is used.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1a2b-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b1a2b-159">See Also</span></span>  
 <span data-ttu-id="b1a2b-160">[配置报表服务器，以便 &#40;SSRS Configuration Manager 发送电子邮件&#41;](../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="b1a2b-160">[Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="b1a2b-161">[报表管理器（SSRS 本机模式）](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="b1a2b-161">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="b1a2b-162">[创建、修改和删除计划](subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="b1a2b-162">[Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 [<span data-ttu-id="b1a2b-163">报表管理器的 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="b1a2b-163">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
