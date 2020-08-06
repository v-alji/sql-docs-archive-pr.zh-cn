---
title: 创建、修改和删除计划 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report-specific schedules [Reporting Services]
- shared schedules [Reporting Services]
- modifying schedules
- removing schedules
- shared schedules [Reporting Services], creating
- shared schedules [Reporting Services], modifying
- schedules [Reporting Services], deleting
- deleting schedules
- schedules [Reporting Services], creating
- schedules [Reporting Services], modifying
- shared schedules [Reporting Services], deleting
ms.assetid: 05da5f3d-9222-43a9-893b-aa10f0f690f8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ec235126caee5acd0d5c79958528565d917bf522
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589427"
---
# <a name="create-modify-and-delete-schedules"></a><span data-ttu-id="9a155-102">Create, Modify, and Delete Schedules</span><span class="sxs-lookup"><span data-stu-id="9a155-102">Create, Modify, and Delete Schedules</span></span>
  <span data-ttu-id="9a155-103">通过本主题，您可以了解有关创建、修改和删除计划的信息。</span><span class="sxs-lookup"><span data-stu-id="9a155-103">Use this topic to learn about how to create, modify, and delete schedules.</span></span>  
  
 <span data-ttu-id="9a155-104">本主题内容：</span><span class="sxs-lookup"><span data-stu-id="9a155-104">In this topic:</span></span>  
  
-   [<span data-ttu-id="9a155-105">管理共享计划概述</span><span class="sxs-lookup"><span data-stu-id="9a155-105">Overview of Managing Shared Schedules</span></span>](#bkmk_overview)  
  
-   [<span data-ttu-id="9a155-106"> (SharePoint 模式下创建和管理共享计划) </span><span class="sxs-lookup"><span data-stu-id="9a155-106">Create and Manage Shared Schedules (SharePoint Mode)</span></span>](#bkmk_sharepoint)  
  
-   [<span data-ttu-id="9a155-107">创建和管理共享计划（本机模式）</span><span class="sxs-lookup"><span data-stu-id="9a155-107">Create and Manage Shared Schedules (Native Mode)</span></span>](#bkmk_native)  
  
##  <a name="overview-of-managing-shared-schedules"></a><a name="bkmk_overview"></a><span data-ttu-id="9a155-108">管理共享计划概述</span><span class="sxs-lookup"><span data-stu-id="9a155-108">Overview of Managing Shared Schedules</span></span>  
 <span data-ttu-id="9a155-109">若要在本机模式下管理共享计划，请使用报表管理器中的“计划”页或 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的“共享计划”文件夹。</span><span class="sxs-lookup"><span data-stu-id="9a155-109">To manage shared schedules for native mode, use the Schedules page in Report Manager or the Shared Schedules folder in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="9a155-110">对于 SharePoint 模式，请使用针对 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序的管理页。</span><span class="sxs-lookup"><span data-stu-id="9a155-110">For SharePoint mode use, the management pages for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
 <span data-ttu-id="9a155-111">您可以查看为报表服务器定义的所有共享计划、暂停和恢复计划（仅限在报表管理器上），还可以选择要修改或删除的计划。</span><span class="sxs-lookup"><span data-stu-id="9a155-111">You can view all the shared schedules that are defined for the report server, pause and resume schedules (on Report Manager only), and select schedules to modify or delete.</span></span> <span data-ttu-id="9a155-112">“共享计划”页汇总了每个计划的状态的以下相关信息：频率、所有者、过期日期和状态。</span><span class="sxs-lookup"><span data-stu-id="9a155-112">The Shared Schedules page summarizes the following information about the state of each schedule: frequency, owner, expiration date, and status.</span></span>  
  
 <span data-ttu-id="9a155-113">通过执行以下操作可以判断共享计划的使用是否频繁：</span><span class="sxs-lookup"><span data-stu-id="9a155-113">You can tell whether a shared schedule is actively used by:</span></span>  
  
-   <span data-ttu-id="9a155-114">查看“共享计划”页上的“上次运行时间”日期、“下次运行时间”日期和“状态”字段中的值。</span><span class="sxs-lookup"><span data-stu-id="9a155-114">Inspecting the values in the Last Run date, Next Run date, and Status fields on the Shared Schedules page.</span></span> <span data-ttu-id="9a155-115">如果某个计划由于过期而不再运行，其“状态”字段中将会显示过期日期。</span><span class="sxs-lookup"><span data-stu-id="9a155-115">If a schedule no longer runs because it has expired, the expiration date appears in the Status field.</span></span>  
  
-   <span data-ttu-id="9a155-116">查看给定共享计划的“报表”页。</span><span class="sxs-lookup"><span data-stu-id="9a155-116">Viewing the Reports page of a given Shared Schedule.</span></span> <span data-ttu-id="9a155-117">此页列出了使用该共享计划的所有报表和共享数据集。</span><span class="sxs-lookup"><span data-stu-id="9a155-117">This page lists all reports and shared datasets that use the shared schedule.</span></span>  
  
-   <span data-ttu-id="9a155-118">查看报表执行日志文件或跟踪日志来确定报表是否已按照计划指定的时间运行。</span><span class="sxs-lookup"><span data-stu-id="9a155-118">Viewing the report execution log files or trace logs to determine whether reports have been run at the times specified by the schedule.</span></span> <span data-ttu-id="9a155-119">有关详细信息，请参阅 [Reporting Services 日志文件和源](../report-server/reporting-services-log-files-and-sources.md)。</span><span class="sxs-lookup"><span data-stu-id="9a155-119">For more information, see [Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md).</span></span>  
  
##  <a name="create-and-manage-shared-schedules-sharepoint-mode"></a><a name="bkmk_sharepoint"></a> <span data-ttu-id="9a155-120">(SharePoint 模式下创建和管理共享计划) </span><span class="sxs-lookup"><span data-stu-id="9a155-120">Create and Manage Shared Schedules (SharePoint Mode)</span></span>  
 <span data-ttu-id="9a155-121">共享计划是向任意数目的报表或订阅提供可以使用的计划信息的多用途计划。</span><span class="sxs-lookup"><span data-stu-id="9a155-121">A shared schedule is a multipurpose schedule that provides ready-to-use schedule information to any number of reports or subscriptions.</span></span> <span data-ttu-id="9a155-122">您只需创建一次共享计划，然后即可在需要用到计划信息时，在订阅或属性页中引用该共享计划。</span><span class="sxs-lookup"><span data-stu-id="9a155-122">You create a shared schedule once, and then reference it in a subscription or property page when you need schedule information.</span></span> <span data-ttu-id="9a155-123">共享计划可以集中管理、暂停和恢复。</span><span class="sxs-lookup"><span data-stu-id="9a155-123">Shared schedules can be centrally managed, paused, and resumed.</span></span> <span data-ttu-id="9a155-124">与此对比，您必须手动编辑自定义计划，才能阻止报表或订阅运行。</span><span class="sxs-lookup"><span data-stu-id="9a155-124">In contrast, you must edit a custom schedule manually to prevent a report or subscription from running.</span></span>  
  
 <span data-ttu-id="9a155-125">若要在 SharePoint 站点上创建、修改或删除共享计划，您必须为站点管理员。</span><span class="sxs-lookup"><span data-stu-id="9a155-125">You must be a site administrator to create, modify, or delete shared schedules on a SharePoint site.</span></span>  
  
 <span data-ttu-id="9a155-126">您可以用描述性名称标识特定计划。</span><span class="sxs-lookup"><span data-stu-id="9a155-126">You can identify a specific schedule by its descriptive name.</span></span> <span data-ttu-id="9a155-127">如果未指定名称，将根据有关计划的事实数据（例如计划的重复执行模式或其运行日期和时间）创建一个默认名称。</span><span class="sxs-lookup"><span data-stu-id="9a155-127">If a name is not specified, a default name is created based on facts about the schedule, such as its recurrence pattern or dates and times when it runs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9a155-128">创建共享计划需要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务。</span><span class="sxs-lookup"><span data-stu-id="9a155-128">Creating shared schedules requires [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
### <a name="create-shared-schedules-sharepoint"></a><span data-ttu-id="9a155-129">创建共享计划 (SharePoint)</span><span class="sxs-lookup"><span data-stu-id="9a155-129">Create Shared Schedules (SharePoint)</span></span>  
  
##### <a name="to-create-shared-schedules"></a><span data-ttu-id="9a155-130">创建共享计划</span><span class="sxs-lookup"><span data-stu-id="9a155-130">To create shared schedules</span></span>  
  
1.  <span data-ttu-id="9a155-131">单击 **“网站操作”** 。</span><span class="sxs-lookup"><span data-stu-id="9a155-131">Click **Site Actions**.</span></span>  
  
2.  <span data-ttu-id="9a155-132">单击 **“网站设置”** 。</span><span class="sxs-lookup"><span data-stu-id="9a155-132">Click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="9a155-133">在 Reporting Services 部分中，单击 **“管理共享计划”** 。</span><span class="sxs-lookup"><span data-stu-id="9a155-133">In the Reporting Services section, click **Manage Shared Schedules**.</span></span>  
  
4.  <span data-ttu-id="9a155-134">单击 **“添加计划”** 以打开“计划属性”页。</span><span class="sxs-lookup"><span data-stu-id="9a155-134">Click **Add Schedule** to open the Schedule Properties page.</span></span>  
  
5.  <span data-ttu-id="9a155-135">为计划输入描述性名称。</span><span class="sxs-lookup"><span data-stu-id="9a155-135">Enter a descriptive name for the schedule.</span></span> <span data-ttu-id="9a155-136">在用来处理 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表的应用程序页中，此名称将显示在整个站点的计划定义页的下拉列表中。</span><span class="sxs-lookup"><span data-stu-id="9a155-136">On the application pages used to work with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] reports, this name will appear in drop-down lists in schedule definition pages throughout the site.</span></span> <span data-ttu-id="9a155-137">避免使用冗长难读的名称。</span><span class="sxs-lookup"><span data-stu-id="9a155-137">Avoid long names that are hard to read.</span></span> <span data-ttu-id="9a155-138">请遵循将大多数说明信息放在名称开头的命名约定。</span><span class="sxs-lookup"><span data-stu-id="9a155-138">Do follow a naming convention that puts the most description information at the beginning of the name.</span></span>  
  
6.  <span data-ttu-id="9a155-139">选择频率。</span><span class="sxs-lookup"><span data-stu-id="9a155-139">Choose a frequency.</span></span> <span data-ttu-id="9a155-140">根据选择的频率，该页中显示的计划选项可能会发生更改以支持该频率（例如，如果选择“月”，该页中显示每个月的名称  ）。</span><span class="sxs-lookup"><span data-stu-id="9a155-140">Depending on the frequency you choose, the schedule options that appear on the page might change to support that frequency (for example, if you choose **Month**, the name of each month will appear on the page).</span></span>  
  
7.  <span data-ttu-id="9a155-141">定义计划。</span><span class="sxs-lookup"><span data-stu-id="9a155-141">Define the schedule.</span></span> <span data-ttu-id="9a155-142">在一个计划中无法支持所有形式的计划组合。</span><span class="sxs-lookup"><span data-stu-id="9a155-142">Not all schedule combinations can be supported in a single schedule.</span></span>  
  
8.  <span data-ttu-id="9a155-143">设置开始和结束日期。</span><span class="sxs-lookup"><span data-stu-id="9a155-143">Set a start and end date.</span></span>  
  
9. <span data-ttu-id="9a155-144">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="9a155-144">Click **OK**.</span></span>  
  
### <a name="delete-shared-schedules-sharepoint"></a><span data-ttu-id="9a155-145">删除共享计划 (SharePoint)</span><span class="sxs-lookup"><span data-stu-id="9a155-145">Delete Shared Schedules (SharePoint)</span></span>  
 <span data-ttu-id="9a155-146">所有计划都必须以手动方式删除，无论是共享计划还是报表特定计划。</span><span class="sxs-lookup"><span data-stu-id="9a155-146">All schedules, whether shared or report specific, must be deleted manually.</span></span> <span data-ttu-id="9a155-147">如果删除某个正在使用中的共享计划，则对该计划的所有引用将替换为未指定的自定义计划（也就是说，不包含日期或时间信息的自定义计划）。</span><span class="sxs-lookup"><span data-stu-id="9a155-147">If you delete a shared schedule that is in use, all references to it are replaced with unspecified custom schedules (that is, a custom schedule that does not have date or time information).</span></span>  
  
 <span data-ttu-id="9a155-148">删除计划和使计划过期是有区别的。</span><span class="sxs-lookup"><span data-stu-id="9a155-148">Deleting a schedule and causing it to expire are different.</span></span> <span data-ttu-id="9a155-149">过期日期用于停止计划，但不会删除计划。</span><span class="sxs-lookup"><span data-stu-id="9a155-149">An expiration date is used to stop a schedule but does not delete it.</span></span> <span data-ttu-id="9a155-150">因为计划用于自动执行报表服务器操作，所以从不会自动删除。</span><span class="sxs-lookup"><span data-stu-id="9a155-150">Because schedules are used to automate report server operations, they are never deleted automatically.</span></span> <span data-ttu-id="9a155-151">通过过期计划，报表服务器管理员可以查明某个自动执行的过程突然停止的原因。</span><span class="sxs-lookup"><span data-stu-id="9a155-151">Expired schedules provide evidence to report server administrators as to why an automated process has suddenly stopped.</span></span> <span data-ttu-id="9a155-152">如果没有过期计划，报表服务器管理员可能会错误地诊断问题，或花费不必要的时间对运行完全正常的过程进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="9a155-152">Without the presence of the expired schedule, a report server administrator might misdiagnose the problem or spend unnecessary time trying to troubleshoot a fully functional process.</span></span>  
  
 <span data-ttu-id="9a155-153">过期的自定义计划仍会附加到报表。</span><span class="sxs-lookup"><span data-stu-id="9a155-153">A custom schedule that has expired remains attached to the report.</span></span> <span data-ttu-id="9a155-154">您可以通过检查计划的结束日期来确定计划是否已过期。</span><span class="sxs-lookup"><span data-stu-id="9a155-154">You can determine if a schedule has expired by checking its end date.</span></span> <span data-ttu-id="9a155-155">过期的共享计划仍会保留在“共享计划”列表中。</span><span class="sxs-lookup"><span data-stu-id="9a155-155">An expired shared schedule remains in the Shared Schedules list.</span></span> <span data-ttu-id="9a155-156">“状态”字段指示计划是否已过期。</span><span class="sxs-lookup"><span data-stu-id="9a155-156">The Status field indicates whether the schedule has expired.</span></span> <span data-ttu-id="9a155-157">您可以通过延长结束日期来恢复计划，也可以在不再需要计划时删除计划引用。</span><span class="sxs-lookup"><span data-stu-id="9a155-157">You can reinstate the schedule by extending the end date, or you can remove the schedule reference if you no longer need it.</span></span>  
  
##### <a name="to-delete-a-shared-schedule"></a><span data-ttu-id="9a155-158">删除共享计划</span><span class="sxs-lookup"><span data-stu-id="9a155-158">To delete a shared schedule</span></span>  
  
1.  <span data-ttu-id="9a155-159">单击 **“网站操作”** 。</span><span class="sxs-lookup"><span data-stu-id="9a155-159">Click **Site Actions**.</span></span>  
  
2.  <span data-ttu-id="9a155-160">单击 **“网站设置”** 。</span><span class="sxs-lookup"><span data-stu-id="9a155-160">Click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="9a155-161">在 Reporting Services 部分中，单击 **“管理共享计划”** 。</span><span class="sxs-lookup"><span data-stu-id="9a155-161">In the Reporting Services section, click **Manage Shared Schedules**.</span></span>  
  
4.  <span data-ttu-id="9a155-162">选择计划，并单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="9a155-162">Select the schedule, and click **Delete**.</span></span>  
  
##  <a name="create-and-manage-shared-schedules-native-mode"></a><a name="bkmk_native"></a> <span data-ttu-id="9a155-163">(本机模式下创建和管理共享计划) </span><span class="sxs-lookup"><span data-stu-id="9a155-163">Create and Manage Shared Schedules (Native Mode)</span></span>  
 <span data-ttu-id="9a155-164">必须使用报表管理器中的“计划”页或 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的“共享计划”文件夹来手动删除共享计划。</span><span class="sxs-lookup"><span data-stu-id="9a155-164">Shared schedules must be deleted manually using the Schedules page in Report Manager or the Shared Schedules folder in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="9a155-165">如果您删除使用中的共享计划，则报表特定计划将替换对该计划的所有引用。</span><span class="sxs-lookup"><span data-stu-id="9a155-165">If you delete a shared schedule that is in use, all references to it are replaced with report-specific schedules.</span></span>  
  
 <span data-ttu-id="9a155-166">删除报表或订阅时或者选择不同的报表或订阅运行方式时，将删除报表特定计划和订阅特定计划。</span><span class="sxs-lookup"><span data-stu-id="9a155-166">Report and subscription-specific schedules are deleted when you delete the report or subscription, or when you choose a different approach to run the report or subscription.</span></span> <span data-ttu-id="9a155-167">例如，选择“始终用最新数据运行此报表”可删除所创建的报表特定计划，该计划将报表作为报表执行快照运行  。</span><span class="sxs-lookup"><span data-stu-id="9a155-167">For example, choosing **Always run this report with the most recent data** will delete a report-specific schedule that you created to run a report as a report execution snapshot.</span></span>  
  
 <span data-ttu-id="9a155-168">删除计划和使计划过期是有区别的。</span><span class="sxs-lookup"><span data-stu-id="9a155-168">Deleting a schedule and causing it to expire are different.</span></span> <span data-ttu-id="9a155-169">过期日期用于停止计划，但不会删除计划。</span><span class="sxs-lookup"><span data-stu-id="9a155-169">An expiration date is used to stop a schedule but does not delete it.</span></span> <span data-ttu-id="9a155-170">因为计划用于自动执行许多功能，所以从不会自动进行删除。</span><span class="sxs-lookup"><span data-stu-id="9a155-170">Because schedules are used to automate so many features, they are never deleted automatically.</span></span> <span data-ttu-id="9a155-171">通过过期计划，报表服务器管理员可以查明某个自动执行的过程突然停止的原因。</span><span class="sxs-lookup"><span data-stu-id="9a155-171">Expired schedules provide evidence to report server administrators as to why an automated process has suddenly stopped.</span></span> <span data-ttu-id="9a155-172">如果没有过期计划，报表服务器管理员可能会错误地诊断问题，或花费不必要的时间，对运行完全正常的过程进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="9a155-172">Without the presence of the expired schedule, a report server administrator can misdiagnose the problem or spend unnecessary time trying to troubleshoot a fully functional process.</span></span>  
  
 <span data-ttu-id="9a155-173">过期的报表特定计划仍会附加到报表。</span><span class="sxs-lookup"><span data-stu-id="9a155-173">A report-specific schedule that has expired remains attached to the report.</span></span> <span data-ttu-id="9a155-174">您可以通过检查计划的结束日期来确定计划是否已过期。</span><span class="sxs-lookup"><span data-stu-id="9a155-174">You can determine if a schedule has expired by checking its end date.</span></span> <span data-ttu-id="9a155-175">过期的共享计划仍会保留在“共享计划”列表中。</span><span class="sxs-lookup"><span data-stu-id="9a155-175">An expired shared schedules remains in the Shared Schedules list.</span></span> <span data-ttu-id="9a155-176">“状态”字段指示计划是否已过期。</span><span class="sxs-lookup"><span data-stu-id="9a155-176">The Status field indicates whether the schedule has expired.</span></span> <span data-ttu-id="9a155-177">您可以通过延长结束日期来恢复计划，也可以在不再需要计划时删除计划引用。</span><span class="sxs-lookup"><span data-stu-id="9a155-177">You can reinstate the schedule by extending the end date, or you can remove the schedule reference if you no longer need it.</span></span>  
  
### <a name="create-delete-or-modify-a-shared-schedule-report-manager"></a><span data-ttu-id="9a155-178">创建、删除或修改共享计划（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="9a155-178">Create, Delete, or Modify a Shared Schedule (Report Manager)</span></span>  
 <span data-ttu-id="9a155-179">创建和修改计划包括设置确定计划运行时间的频率选项。</span><span class="sxs-lookup"><span data-stu-id="9a155-179">Creating and modifying a schedule consists of setting frequency options that determine when the schedule runs.</span></span>  
  
-   <span data-ttu-id="9a155-180">共享计划作为单独的项创建。</span><span class="sxs-lookup"><span data-stu-id="9a155-180">Shared schedules are created as separate items.</span></span> <span data-ttu-id="9a155-181">创建共享计划后，您就可以在定义订阅或其他某个计划操作时引用它们。</span><span class="sxs-lookup"><span data-stu-id="9a155-181">After they are created, you reference them when defining a subscription or some other scheduled operation.</span></span>  
  
-   <span data-ttu-id="9a155-182">当您定义订阅或设置报表执行属性时，将创建报表特定计划；在定义订阅或设置属性的过程中需要填写计划信息。</span><span class="sxs-lookup"><span data-stu-id="9a155-182">Report-specific schedules are created when you define a subscription or set report execution properties; filling out schedule information is part of defining a subscription or setting properties.</span></span> <span data-ttu-id="9a155-183">若要定义报表特定计划，请打开使用该计划的报表或订阅。</span><span class="sxs-lookup"><span data-stu-id="9a155-183">To define a report-specific schedule, you open the report or subscription that uses it.</span></span>  
  
 <span data-ttu-id="9a155-184">共享计划包含的计划和重复执行信息可供 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表服务器上运行的任意数量的已发布报表和订阅使用。</span><span class="sxs-lookup"><span data-stu-id="9a155-184">A shared schedule contains schedule and recurrence information that can be used by any number of published reports and subscriptions that run on a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="9a155-185">如果有多个同时运行的报表和订阅，则可为这些作业创建共享计划。</span><span class="sxs-lookup"><span data-stu-id="9a155-185">If you have many reports and subscriptions that run at the same time, you can create a shared schedule for those jobs.</span></span> <span data-ttu-id="9a155-186">如果随后想要更改重复执行模式或结束日期，可以在一个位置进行更改。</span><span class="sxs-lookup"><span data-stu-id="9a155-186">If you want to subsequently change the recurrence pattern or the end date, you can make the change in one place.</span></span>  
  
 <span data-ttu-id="9a155-187">共享计划易于维护，并且在管理计划操作方面为您提供了更多的灵活性。</span><span class="sxs-lookup"><span data-stu-id="9a155-187">Shared schedules are easier to maintain and give you more flexibility in managing scheduled operations.</span></span> <span data-ttu-id="9a155-188">例如，您可以暂停和恢复共享计划。</span><span class="sxs-lookup"><span data-stu-id="9a155-188">For example, you can pause and resume shared schedules.</span></span> <span data-ttu-id="9a155-189">此外，如果您发现同时运行的计划操作过多，还可以创建多个在不同时间运行的共享计划，然后调整计划信息直到整个报表服务器上的处理负荷分布均匀。</span><span class="sxs-lookup"><span data-stu-id="9a155-189">Also, if you find that too many scheduled operations are running at the same time, you can create multiple shared schedules that run at different times and then adjust the schedule information until the processing load evens out across the report server.</span></span>  
  
 <span data-ttu-id="9a155-190">您可以在任何时候创建或修改计划。</span><span class="sxs-lookup"><span data-stu-id="9a155-190">You can create or modify a schedule at any time.</span></span> <span data-ttu-id="9a155-191">但是，如果计划在您完成修改之前已经开始运行，则使用计划的修改前版本。</span><span class="sxs-lookup"><span data-stu-id="9a155-191">However, if a schedule starts to run before you have completed your modifications, the earlier version of the schedule is used.</span></span> <span data-ttu-id="9a155-192">修改的计划必须在保存后才能生效。</span><span class="sxs-lookup"><span data-stu-id="9a155-192">The revised schedule does not take effect until you save it.</span></span>  
  
 <span data-ttu-id="9a155-193">如果您正在修改某个共享计划，可以在进行更改前将其暂停。</span><span class="sxs-lookup"><span data-stu-id="9a155-193">If you are modifying a shared schedule, you can pause it before you make changes.</span></span> <span data-ttu-id="9a155-194">当您恢复该计划时，更改立即生效。</span><span class="sxs-lookup"><span data-stu-id="9a155-194">The changes take effect when you resume the schedule.</span></span>  
  
##### <a name="to-create-or-modify-a-shared-schedule-report-manager"></a><span data-ttu-id="9a155-195">创建或修改共享计划（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="9a155-195">To create or modify a shared schedule (Report Manager)</span></span>  
  
1.  <span data-ttu-id="9a155-196">启动 [报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="9a155-196">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="9a155-197">在报表管理器中，单击全局工具栏上的“站点设置” **“网站设置”**。</span><span class="sxs-lookup"><span data-stu-id="9a155-197">In Report Manager, click **Site Settings**on the global toolbar.</span></span>  
  
3.  <span data-ttu-id="9a155-198">单击 "**计划**"。</span><span class="sxs-lookup"><span data-stu-id="9a155-198">Click **schedules**.</span></span>  
  
4.  <span data-ttu-id="9a155-199">单击 **“新建计划”**。</span><span class="sxs-lookup"><span data-stu-id="9a155-199">Click **New Schedule**.</span></span> <span data-ttu-id="9a155-200">若要修改现有计划，请单击计划的名称。</span><span class="sxs-lookup"><span data-stu-id="9a155-200">To modify an existing schedule, click the name of the schedule.</span></span>  
  
5.  <span data-ttu-id="9a155-201">为计划键入说明性名称。</span><span class="sxs-lookup"><span data-stu-id="9a155-201">Type a descriptive name for the schedule.</span></span>  
  
6.  <span data-ttu-id="9a155-202">选择 **“时”** 、 **“天”** 、 **“周”** 或 **“月”** 。</span><span class="sxs-lookup"><span data-stu-id="9a155-202">Select **Hour**, **Day**, **Week**, or **Month**.</span></span> <span data-ttu-id="9a155-203">单击 **“一次”** 可以创建仅运行一次的计划。</span><span class="sxs-lookup"><span data-stu-id="9a155-203">Click **Once** to create a schedule that runs one time only.</span></span> <span data-ttu-id="9a155-204">指定计划的上述基本设置之后，页面上将会显示其他选项。</span><span class="sxs-lookup"><span data-stu-id="9a155-204">Additional options appear when you specify the basis of your schedule.</span></span>  
  
7.  <span data-ttu-id="9a155-205">根据需要，可以选择开始计划的日期。</span><span class="sxs-lookup"><span data-stu-id="9a155-205">Optionally select a date to start the schedule.</span></span> <span data-ttu-id="9a155-206">默认值为当天。</span><span class="sxs-lookup"><span data-stu-id="9a155-206">The default is the current day.</span></span> <span data-ttu-id="9a155-207">选择以后的某一天可以推迟计划的开始时间。</span><span class="sxs-lookup"><span data-stu-id="9a155-207">You can postpone the schedule start time by choosing a later date.</span></span>  
  
8.  <span data-ttu-id="9a155-208">根据需要，可以选择结束计划的日期。</span><span class="sxs-lookup"><span data-stu-id="9a155-208">Optionally, select a date to end the schedule.</span></span> <span data-ttu-id="9a155-209">计划将在此日期停止运行，但不会删除。</span><span class="sxs-lookup"><span data-stu-id="9a155-209">The schedule stops running on this date, but is not deleted.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##### <a name="to-delete-a-shared-schedule-report-manager"></a><span data-ttu-id="9a155-210">删除共享计划（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="9a155-210">To delete a shared schedule (Report Manager)</span></span>  
  
1.  <span data-ttu-id="9a155-211">在报表管理器中，单击全局工具栏上的“站点设置” **“网站设置”**。</span><span class="sxs-lookup"><span data-stu-id="9a155-211">In Report Manager, click **Site Settings**on the global toolbar.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9a155-212"> 如果 **“站点设置”** 不可用，则说明您没有访问站点设置的权限。</span><span class="sxs-lookup"><span data-stu-id="9a155-212">If **Site Settings** is not available, you do not have permission to access site settings.</span></span>  
  
2.  <span data-ttu-id="9a155-213">在该页的 **“其他”** 部分中，单击 **“管理共享计划”**。</span><span class="sxs-lookup"><span data-stu-id="9a155-213">In the **Other** section on the page, click **Manage shared schedules**.</span></span>  
  
3.  <span data-ttu-id="9a155-214">选中要删除的计划旁边的复选框，再单击 **“删除”**。</span><span class="sxs-lookup"><span data-stu-id="9a155-214">Select the check box next to the schedule you want to delete, and then click **Delete**.</span></span>  
  
 <span data-ttu-id="9a155-215">如果删除由多个报表和订阅使用的共享计划，报表服务器将为以前使用该共享计划的每个报表和订阅都创建一个计划。</span><span class="sxs-lookup"><span data-stu-id="9a155-215">If you delete a shared schedule that is used by multiple reports and subscriptions, the report server will create individual schedules for each report and subscription that previously used the shared schedule.</span></span> <span data-ttu-id="9a155-216">每个新计划都将包含已在共享计划中指定的日期、时间和重复执行模式。</span><span class="sxs-lookup"><span data-stu-id="9a155-216">Each new individual schedule will contain the date, time, and recurrence pattern that was specified in the shared schedule.</span></span> <span data-ttu-id="9a155-217">请注意， [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 不提供对于各个计划的集中管理。</span><span class="sxs-lookup"><span data-stu-id="9a155-217">Note that [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] does not provide central management of individual schedules.</span></span> <span data-ttu-id="9a155-218">如果删除共享计划，则需要为各项单独维护计划信息。</span><span class="sxs-lookup"><span data-stu-id="9a155-218">If you delete a shared schedule, you will now have to maintain the schedule information for each individual item.</span></span>  
  
 <span data-ttu-id="9a155-219">如果您不确定是否用过共享计划，请考虑在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中删除共享计划。</span><span class="sxs-lookup"><span data-stu-id="9a155-219">If you are not sure whether a shared schedule is used, consider deleting it in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] instead.</span></span> [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="9a155-220">提供的共享计划管理功能与报表管理器相同，不过它还提供了可以显示使用该计划的各个报表名称的“报表”页。</span><span class="sxs-lookup"><span data-stu-id="9a155-220">provides the same shared schedule management features as Report Manager, but it provides an additional Reports page that shows you the name of each report that uses the schedule.</span></span>  
  
### <a name="create-delete-or-modify-a-shared-schedule-management-studio"></a><span data-ttu-id="9a155-221">创建、删除或修改共享计划 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="9a155-221">Create, Delete, or Modify a Shared Schedule (Management Studio)</span></span>  
 <span data-ttu-id="9a155-222">共享计划包含的计划和重复执行信息可供 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表服务器上运行的任意数量的已发布报表和订阅使用。</span><span class="sxs-lookup"><span data-stu-id="9a155-222">A shared schedule contains schedule and recurrence information that can be used by any number of published reports and subscriptions that run on a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="9a155-223">如果有多个同时运行的报表和订阅，则可为这些作业创建共享计划。</span><span class="sxs-lookup"><span data-stu-id="9a155-223">If you have many reports and subscriptions that run at the same time, you can create a shared schedule for those jobs.</span></span> <span data-ttu-id="9a155-224">如果随后想要更改重复执行模式或结束日期，可以在一个位置进行更改。</span><span class="sxs-lookup"><span data-stu-id="9a155-224">If you want to subsequently change the recurrence pattern or the end date, you can make the change in one place.</span></span>  
  
 <span data-ttu-id="9a155-225">共享计划易于维护，并且在管理计划操作方面为您提供了更多的灵活性。</span><span class="sxs-lookup"><span data-stu-id="9a155-225">Shared schedules are easier to maintain and give you more flexibility in managing scheduled operations.</span></span> <span data-ttu-id="9a155-226">例如，您可以暂停和恢复共享计划。</span><span class="sxs-lookup"><span data-stu-id="9a155-226">For example, you can pause and resume shared schedules.</span></span> <span data-ttu-id="9a155-227">此外，如果您发现同时运行的计划操作过多，还可以创建多个在不同时间运行的共享计划，然后调整计划信息直到整个报表服务器上的处理负荷分布均匀。</span><span class="sxs-lookup"><span data-stu-id="9a155-227">Also, if you find that too many scheduled operations are running at the same time, you can create multiple shared schedules that run at different times and then adjust the schedule information until the processing load evens out across the report server.</span></span>  
  
##### <a name="to-create-or-modify-a-shared-schedule-management-studio"></a><span data-ttu-id="9a155-228">创建或修改共享计划 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="9a155-228">To create or modify a shared schedule (Management Studio)</span></span>  
  
1.  <span data-ttu-id="9a155-229">启动 SQL Server Management Studio 并连接到报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="9a155-229">Start SQL Server Management Studio and connect to a report server instance.</span></span>  
  
2.  <span data-ttu-id="9a155-230">在对象资源管理器中，展开报表服务器节点。</span><span class="sxs-lookup"><span data-stu-id="9a155-230">In Object Explorer, expand a report server node.</span></span>  
  
3.  <span data-ttu-id="9a155-231">右键单击 "共享计划" 文件夹，然后单击 "**新建计划**"。</span><span class="sxs-lookup"><span data-stu-id="9a155-231">Right-click the Shared Schedules folder, and then click **New Schedule**.</span></span> <span data-ttu-id="9a155-232">将显示 **“新建共享计划”** 对话框的“常规”页。</span><span class="sxs-lookup"><span data-stu-id="9a155-232">The General page of the **New Shared Schedule** dialog box is displayed.</span></span>  
  
     <span data-ttu-id="9a155-233">要修改现有共享的计划，请展开“共享的计划”文件夹，右键单击要修改的计划，然后单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="9a155-233">To modify an existing shared schedule, expand the Shared Schedules folder, right-click the schedule you want to modify, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="9a155-234">为计划键入说明性名称。</span><span class="sxs-lookup"><span data-stu-id="9a155-234">Type a descriptive name for the schedule.</span></span>  
  
5.  <span data-ttu-id="9a155-235">根据需要，可以选择开始计划的日期。</span><span class="sxs-lookup"><span data-stu-id="9a155-235">Optionally select a date to start the schedule.</span></span> <span data-ttu-id="9a155-236">默认值为当天。</span><span class="sxs-lookup"><span data-stu-id="9a155-236">The default is the current day.</span></span>  
  
6.  <span data-ttu-id="9a155-237">根据需要，可以选择结束计划的日期。</span><span class="sxs-lookup"><span data-stu-id="9a155-237">Optionally select a date to end the schedule.</span></span> <span data-ttu-id="9a155-238">计划将在此日期停止运行，但不会删除。</span><span class="sxs-lookup"><span data-stu-id="9a155-238">The schedule stops running on this date, but is not deleted.</span></span>  
  
7.  <span data-ttu-id="9a155-239">若要配置重复执行的计划，请选择 **“小时”** 、 **“天”** 、 **“周”** 或 **“月”** 。</span><span class="sxs-lookup"><span data-stu-id="9a155-239">To configure a recurring schedule, select **Hour**, **Day**, **Week**, or **Month**.</span></span> <span data-ttu-id="9a155-240">此时，将显示其他选项。</span><span class="sxs-lookup"><span data-stu-id="9a155-240">Additional options are displayed.</span></span> <span data-ttu-id="9a155-241">使用这些附加选项可以根据前面选择的小时、天、周或月来配置计划频率。</span><span class="sxs-lookup"><span data-stu-id="9a155-241">Use these additional options to configure schedule frequency, based on your preferred hour, day, week, or month.</span></span>  
  
     <span data-ttu-id="9a155-242">或者，若要指定一次性（不重复执行）计划，请选择“一次”，然后指定“开始时间”   。</span><span class="sxs-lookup"><span data-stu-id="9a155-242">Or, to specify a one-time (non-recurring) schedule, select **Once**, and then specify a **Start time**.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##### <a name="to-delete-a-shared-schedule-management-studio"></a><span data-ttu-id="9a155-243">删除共享计划 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="9a155-243">To delete a shared schedule (Management Studio)</span></span>  
  
1.  <span data-ttu-id="9a155-244">在对象资源管理器中，展开报表服务器节点。</span><span class="sxs-lookup"><span data-stu-id="9a155-244">In Object Explorer, expand a report server node.</span></span>  
  
2.  <span data-ttu-id="9a155-245">展开“共享的计划”文件夹，右键单击要删除的计划，然后单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="9a155-245">Expand the Shared Schedules folder, right-click the schedule you want to delete, and then click **Delete**.</span></span> <span data-ttu-id="9a155-246">将显示 **“删除目录项”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="9a155-246">The **Delete Catalog Items** dialog box appears.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="9a155-247">如果删除由多个报表和订阅使用的共享计划，报表服务器将为以前使用该共享计划的每个报表和订阅都创建一个计划。</span><span class="sxs-lookup"><span data-stu-id="9a155-247">If you delete a shared schedule that is used by multiple reports and subscriptions, the report server will create individual schedules for each report and subscription that previously used the shared schedule.</span></span> <span data-ttu-id="9a155-248">每个新计划都将包含已在共享计划中指定的日期、时间和重复执行模式。</span><span class="sxs-lookup"><span data-stu-id="9a155-248">Each new individual schedule will contain the date, time, and recurrence pattern that was specified in the shared schedule.</span></span> <span data-ttu-id="9a155-249">请注意， [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 不提供对于各个计划的集中管理。</span><span class="sxs-lookup"><span data-stu-id="9a155-249">Note that [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] does not provide central management of individual schedules.</span></span> <span data-ttu-id="9a155-250">如果删除共享计划，则需要为各项单独维护计划信息。</span><span class="sxs-lookup"><span data-stu-id="9a155-250">If you delete a shared schedule, you will now have to maintain the schedule information for each individual item.</span></span> <span data-ttu-id="9a155-251">在删除某个共享计划之前，请使用 [“报表”页](../tools/schedule-properties-reports-page.md) 来确定哪些报表当前正在使用该共享计划。</span><span class="sxs-lookup"><span data-stu-id="9a155-251">Before deleting a shared schedule, use the [Reports Page](../tools/schedule-properties-reports-page.md) to determine which reports are currently using the shared schedule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a155-252">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9a155-252">See Also</span></span>  
 <span data-ttu-id="9a155-253">[“计划”](schedules.md) </span><span class="sxs-lookup"><span data-stu-id="9a155-253">[Schedules](schedules.md) </span></span>  
 <span data-ttu-id="9a155-254">[暂停和恢复共享计划](pause-and-resume-shared-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="9a155-254">[Pause and Resume Shared Schedules](pause-and-resume-shared-schedules.md) </span></span>  
 <span data-ttu-id="9a155-255">[&#40;报表管理器缓存报表&#41;](../report-server/cache-a-report-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="9a155-255">[Cache a Report &#40;Report Manager&#41;](../report-server/cache-a-report-report-manager.md) </span></span>  
 [<span data-ttu-id="9a155-256">向报表历史记录添加快照（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="9a155-256">Add a Snapshot to Report History &#40;Report Manager&#41;</span></span>](../report-server/add-a-snapshot-to-report-history-report-manager.md)  
  
  
