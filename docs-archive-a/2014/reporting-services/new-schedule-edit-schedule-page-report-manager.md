---
title: 新计划： "编辑计划" 页 (报表管理器) |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 52a4d250-e185-4116-a29c-d809940a00fb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 701c1729eac1c2cf683c966dca58f47b88a2dd32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692286"
---
# <a name="new-schedule-edit-schedule-page-report-manager"></a><span data-ttu-id="1b026-102">新计划： "编辑计划" 页 (报表管理器) </span><span class="sxs-lookup"><span data-stu-id="1b026-102">New Schedule: Edit Schedule Page (Report Manager)</span></span>
  <span data-ttu-id="1b026-103">使用“新建计划”/“编辑计划”页可为报表创建计划。</span><span class="sxs-lookup"><span data-stu-id="1b026-103">Use the New Schedule / Edit Schedule page to create a schedule for a report.</span></span> <span data-ttu-id="1b026-104">您可以与订阅一起使用计划，以刷新缓存的报表，以及按独立项的形式创建快照或在报表历史记录中创建快照。</span><span class="sxs-lookup"><span data-stu-id="1b026-104">Schedules are used with subscriptions, to refresh cached reports, and to create snapshots as standalone items or in report history.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1b026-105">并非在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的每个版本中均提供此功能。</span><span class="sxs-lookup"><span data-stu-id="1b026-105">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1b026-106">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="1b026-106">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="1b026-107">您只能为以无人参与的方式运行的报表创建计划。</span><span class="sxs-lookup"><span data-stu-id="1b026-107">You can create schedules only for reports that can run unattended.</span></span> <span data-ttu-id="1b026-108">若要以无人参与方式运行报表，您需要将报表数据源凭据存储到报表服务器数据库中。</span><span class="sxs-lookup"><span data-stu-id="1b026-108">Running a report unattended requires that you store report data source credentials in the report server database.</span></span> <span data-ttu-id="1b026-109">有关详细信息，请参阅 "[数据源属性" 页 &#40;报表管理器&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="1b026-109">For more information, see [Data Sources Properties Page &#40;Report Manager&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="1b026-110">在一个计划中无法支持所有形式的频率组合。</span><span class="sxs-lookup"><span data-stu-id="1b026-110">Not all frequency combinations can be supported in a single schedule.</span></span> <span data-ttu-id="1b026-111">例如，如果要在每周五的中午 12:00</span><span class="sxs-lookup"><span data-stu-id="1b026-111">For example, if you want to run a report at 12:00 P.M.</span></span> <span data-ttu-id="1b026-112">和下午 4:00</span><span class="sxs-lookup"><span data-stu-id="1b026-112">and 4:00 P.M.</span></span> <span data-ttu-id="1b026-113">运行报表，那么您必须创建两个每日计划，并指定运行日期为星期五，一个计划的开始时间为中午 12:00，</span><span class="sxs-lookup"><span data-stu-id="1b026-113">every Friday, you must create two daily schedules that specify a Friday run date, one with a start time of 12:00 P.M.</span></span> <span data-ttu-id="1b026-114">另一个计划的开始时间为下午 4:00。</span><span class="sxs-lookup"><span data-stu-id="1b026-114">and another with a start time of 4:00 P.M.</span></span>  
  
 <span data-ttu-id="1b026-115">计划处理过程以承载和处理计划的报表服务器的本地时间为准。</span><span class="sxs-lookup"><span data-stu-id="1b026-115">Schedule processing is based on the local time of the report server that hosts and processes the schedule.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="1b026-116">导航</span><span class="sxs-lookup"><span data-stu-id="1b026-116">Navigation</span></span>  
 <span data-ttu-id="1b026-117">使用以下过程导航到用户界面 (UI) 中的这一位置。</span><span class="sxs-lookup"><span data-stu-id="1b026-117">Use the following procedures to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-new-schedule-or-edit-schedule-page-from-the-execution-properties-page-of-a-report"></a><span data-ttu-id="1b026-118">从报表的“执行属性”页打开“新建计划”或“编辑计划”页</span><span class="sxs-lookup"><span data-stu-id="1b026-118">To open the New Schedule or Edit Schedule page from the Execution properties page of a report</span></span>  
  
1.  <span data-ttu-id="1b026-119">打开报表管理器，找到要配置计划的报表。</span><span class="sxs-lookup"><span data-stu-id="1b026-119">Open Report Manager, and locate the report for which you want configure a schedule.</span></span>  
  
2.  <span data-ttu-id="1b026-120">悬停在该报表之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="1b026-120">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="1b026-121">在下拉菜单中，单击 **“管理”**。</span><span class="sxs-lookup"><span data-stu-id="1b026-121">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="1b026-122">这会打开该模型的“常规属性”页。</span><span class="sxs-lookup"><span data-stu-id="1b026-122">This opens the General properties page for the model.</span></span>  
  
4.  <span data-ttu-id="1b026-123">选择 **“执行”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="1b026-123">Select the **Execution** tab.</span></span>  
  
5.  <span data-ttu-id="1b026-124">选择 **“通过报表执行快照呈现此报表”** 选项。</span><span class="sxs-lookup"><span data-stu-id="1b026-124">Select the **Render this report from a report execution snapshot option**.</span></span> <span data-ttu-id="1b026-125">然后，选择 **“使用以下计划将快照添加到报表历史记录中”**，并选择 **“报表特定计划”**。</span><span class="sxs-lookup"><span data-stu-id="1b026-125">Then select **Use the following schedule to add snapshots to report history**, and select **Report-specific schedule**.</span></span> <span data-ttu-id="1b026-126">然后，单击 **“配置”**。</span><span class="sxs-lookup"><span data-stu-id="1b026-126">Then click **Configure**.</span></span>  
  
### <a name="to-open-the-new-schedule-or-edit-schedule-page-from-the-history-properties-page-of-a-report"></a><span data-ttu-id="1b026-127">从报表的“历史记录属性”页打开“新建计划”或“编辑计划”页</span><span class="sxs-lookup"><span data-stu-id="1b026-127">To open the New Schedule or Edit Schedule page from the History properties page of a report</span></span>  
  
1.  <span data-ttu-id="1b026-128">打开报表管理器，找到要配置计划的报表。</span><span class="sxs-lookup"><span data-stu-id="1b026-128">Open Report Manager, and locate the report for which you want configure a schedule.</span></span>  
  
2.  <span data-ttu-id="1b026-129">悬停在该报表之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="1b026-129">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="1b026-130">在下拉菜单中，单击 **“管理”**。</span><span class="sxs-lookup"><span data-stu-id="1b026-130">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="1b026-131">这会打开该模型的“常规属性”页。</span><span class="sxs-lookup"><span data-stu-id="1b026-131">This opens the General properties page for the model.</span></span>  
  
4.  <span data-ttu-id="1b026-132">选择 **“历史记录”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="1b026-132">Select the **History** tab.</span></span>  
  
5.  <span data-ttu-id="1b026-133">选择 **“使用以下计划将快照添加到报表历史记录中”**，并选择 **“报表特定计划”**。</span><span class="sxs-lookup"><span data-stu-id="1b026-133">Select **Use the following schedule to add snapshots to report history**, and select **Report-specific schedule**.</span></span> <span data-ttu-id="1b026-134">然后，单击 **“配置”**。</span><span class="sxs-lookup"><span data-stu-id="1b026-134">Then click **Configure**.</span></span>  
  
### <a name="to-open-the-new-schedule-or-edit-schedule-page-from-the-subscriptions-page"></a><span data-ttu-id="1b026-135">从“订阅”页打开“新建计划”或“编辑计划”页</span><span class="sxs-lookup"><span data-stu-id="1b026-135">To open the New Schedule or Edit Schedule page from the Subscriptions page</span></span>  
  
1.  <span data-ttu-id="1b026-136">打开报表管理器，找到要配置计划的报表。</span><span class="sxs-lookup"><span data-stu-id="1b026-136">Open Report Manager, and locate the report for which you want configure a schedule.</span></span>  
  
2.  <span data-ttu-id="1b026-137">悬停在该报表之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="1b026-137">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="1b026-138">在下拉菜单中，</span><span class="sxs-lookup"><span data-stu-id="1b026-138">In the drop-down menu,</span></span>  
  
    -   <span data-ttu-id="1b026-139">单击“管理”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1b026-139">Click **Manage**.</span></span> <span data-ttu-id="1b026-140">这会打开该报表的“常规”属性页。</span><span class="sxs-lookup"><span data-stu-id="1b026-140">This opens the General properties page for the report.</span></span> <span data-ttu-id="1b026-141">然后，选择 **“订阅”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="1b026-141">Then select the **Subscriptions** tab.</span></span>  
  
    -   <span data-ttu-id="1b026-142">单击 **“订阅”**。</span><span class="sxs-lookup"><span data-stu-id="1b026-142">Click **Subscribe**.</span></span> <span data-ttu-id="1b026-143">这会打开该报表的 **“订阅”** 属性页。</span><span class="sxs-lookup"><span data-stu-id="1b026-143">This opens the **Subscriptions** properties page for the report.</span></span>  
  
4.  <span data-ttu-id="1b026-144">在工具栏中，单击 **“新建订阅”** 或选择要编辑的现有订阅。</span><span class="sxs-lookup"><span data-stu-id="1b026-144">In the toolbar, click **New Subscription** or select an existing subscription to edit.</span></span>  
  
5.  <span data-ttu-id="1b026-145">在 **“订阅处理选项”** 下，单击 **“新建计划”**。</span><span class="sxs-lookup"><span data-stu-id="1b026-145">Under **Subscription Processing Options**, click **New Schedule**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1b026-146">选项</span><span class="sxs-lookup"><span data-stu-id="1b026-146">Options</span></span>  
 <span data-ttu-id="1b026-147">**计划详细信息**</span><span class="sxs-lookup"><span data-stu-id="1b026-147">**Schedule details**</span></span>  
 <span data-ttu-id="1b026-148">选择决定运行报表的时间和频率的选项。</span><span class="sxs-lookup"><span data-stu-id="1b026-148">Select options that determine when and how often a report runs.</span></span> <span data-ttu-id="1b026-149">频率选项分为几级。</span><span class="sxs-lookup"><span data-stu-id="1b026-149">Frequency options are layered.</span></span> <span data-ttu-id="1b026-150">第一组选项指定频率的类别（每小时、每天、每周等）。</span><span class="sxs-lookup"><span data-stu-id="1b026-150">The first set of options specifies a category of frequency (hourly, daily, weekly, and so on).</span></span> <span data-ttu-id="1b026-151">第二组选项的显示由初始选择决定。</span><span class="sxs-lookup"><span data-stu-id="1b026-151">The second set of options that appears is based on your initial selection.</span></span>  
  
-   <span data-ttu-id="1b026-152">**“小时”** 可定义以每小时为间隔运行的计划。</span><span class="sxs-lookup"><span data-stu-id="1b026-152">**Hour** defines a schedule that runs at hourly intervals.</span></span> <span data-ttu-id="1b026-153">使用 **“开始日期和结束日期”** 部分可以指定运行计划的日期。</span><span class="sxs-lookup"><span data-stu-id="1b026-153">Use the **Start and end dates** section to specify the day on which to run the schedule.</span></span>  
  
-   <span data-ttu-id="1b026-154">**“天”** 可以定义在所选日的特定时分运行的计划。</span><span class="sxs-lookup"><span data-stu-id="1b026-154">**Day** defines a schedule that runs on the days you select at a specific hour and minute.</span></span> <span data-ttu-id="1b026-155">您可以按以下方式指定日期：每日 \<*day*> 、每个工作日和 \<*number*> 每天。</span><span class="sxs-lookup"><span data-stu-id="1b026-155">You can specify days in the following ways: Every \<*day*>, Every weekday, and Every \<*number*> day.</span></span> <span data-ttu-id="1b026-156">选择一个选项会禁用其他选项，即使其他天已显示为选中状态也是如此。</span><span class="sxs-lookup"><span data-stu-id="1b026-156">Choosing one approach voids the others, even if the other days appear to be selected.</span></span>  
  
-   <span data-ttu-id="1b026-157">**“周”** 可定义以每周为间隔在特定时分运行的计划。</span><span class="sxs-lookup"><span data-stu-id="1b026-157">**Week** defines a schedule that runs at weekly intervals at a specific hour and minute.</span></span> <span data-ttu-id="1b026-158">时间间隔可以是完整的周（例如，每两周）或一周中的几天。</span><span class="sxs-lookup"><span data-stu-id="1b026-158">The interval can be a complete week (for example, every two weeks), or days within a week.</span></span>  
  
-   <span data-ttu-id="1b026-159">**“月”** 可以定义每月运行的计划。</span><span class="sxs-lookup"><span data-stu-id="1b026-159">**Month** defines a schedule that runs on a monthly basis.</span></span> <span data-ttu-id="1b026-160">在一个月中，您可以基于某种模式选择一天（如每个月最后一个星期日）或选择特定日期（如 1 和 15，表示每个月的第 1 天和第 15 天）。</span><span class="sxs-lookup"><span data-stu-id="1b026-160">Within a month, you can choose a day based on a pattern (for example, the last Sunday of every month) or specific calendar dates (such as 1 and 15 to indicate the first and fifteenth day of every month).</span></span> <span data-ttu-id="1b026-161">可以通过使用逗号和连字符指定多个日期和范围，例如 1, 5, 7-12, 21。</span><span class="sxs-lookup"><span data-stu-id="1b026-161">Using commas and hyphens, you can specify multiple days and ranges, for example, 1, 5, 7-12, 21.</span></span>  
  
-   <span data-ttu-id="1b026-162">使用 **“一次”** 可以定义只运行一次的计划。</span><span class="sxs-lookup"><span data-stu-id="1b026-162">**Once** defines a schedule that runs only once.</span></span> <span data-ttu-id="1b026-163">使用 **“开始日期和结束日期”** 部分可以指定运行计划的日期。</span><span class="sxs-lookup"><span data-stu-id="1b026-163">Use the **Start and end dates** section to specify the day on which to run the schedule.</span></span> <span data-ttu-id="1b026-164">计划处理完后即过期。</span><span class="sxs-lookup"><span data-stu-id="1b026-164">This schedule expires as soon as it is processed.</span></span>  
  
 <span data-ttu-id="1b026-165">**“开始日期和结束日期”**</span><span class="sxs-lookup"><span data-stu-id="1b026-165">**Start and end dates**</span></span>  
 <span data-ttu-id="1b026-166">通过此选项可以指定开始日期（确定计划何时生效）和结束日期（确定计划何时过期）。</span><span class="sxs-lookup"><span data-stu-id="1b026-166">Specify a start date that determines when the schedule takes effect and an end date that determines when the schedule expires.</span></span>  
  
 <span data-ttu-id="1b026-167">计划过期时并无通知。</span><span class="sxs-lookup"><span data-stu-id="1b026-167">Schedules expire without notification.</span></span> <span data-ttu-id="1b026-168">结束日期后，计划将不再运行。</span><span class="sxs-lookup"><span data-stu-id="1b026-168">After the end date, they no longer run.</span></span> <span data-ttu-id="1b026-169">过期的计划不会被删除。</span><span class="sxs-lookup"><span data-stu-id="1b026-169">Expired schedules are not deleted.</span></span> <span data-ttu-id="1b026-170">只能手动删除这些计划。</span><span class="sxs-lookup"><span data-stu-id="1b026-170">Schedules can only be deleted manually.</span></span> <span data-ttu-id="1b026-171">也就是说，如果选择继续过期的计划，只需扩展结束日期即可。</span><span class="sxs-lookup"><span data-stu-id="1b026-171">That way, if you choose to continue the schedule, you can extend the end date.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b026-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1b026-172">See Also</span></span>  
 <span data-ttu-id="1b026-173">[报表管理器（SSRS 本机模式）](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="1b026-173">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="1b026-174">[创建、修改和删除计划](subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="1b026-174">[Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 [<span data-ttu-id="1b026-175">报表管理器的 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="1b026-175">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
