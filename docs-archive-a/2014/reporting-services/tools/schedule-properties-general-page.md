---
title: 计划属性（“常规”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.scheduleproperties.general.f1
ms.assetid: 20e43966-6caf-4972-a2e2-0d9131ac8f51
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a61837cd977526021be948d8c74a93eba6506e67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580560"
---
# <a name="schedule-properties-general-page"></a><span data-ttu-id="f0d96-102">计划属性（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="f0d96-102">Schedule Properties (General Page)</span></span>
  <span data-ttu-id="f0d96-103">使用此页可查看或修改共享计划。</span><span class="sxs-lookup"><span data-stu-id="f0d96-103">Use this page to view or modify a shared schedule.</span></span> <span data-ttu-id="f0d96-104">共享计划可以用于替代报表特定计划或订阅特定计划。</span><span class="sxs-lookup"><span data-stu-id="f0d96-104">Shared schedules can be used in place of report-specific or subscription-specific schedules.</span></span> <span data-ttu-id="f0d96-105">将在保存计划之后应用对计划进行的更改。</span><span class="sxs-lookup"><span data-stu-id="f0d96-105">Changes to the schedule are applied after you save the schedule.</span></span> <span data-ttu-id="f0d96-106">对计划进行编辑不会影响当前正在进行的作业。</span><span class="sxs-lookup"><span data-stu-id="f0d96-106">Editing a schedule has no effect on jobs that are currently in progress.</span></span> <span data-ttu-id="f0d96-107">如果要编辑正在使用的计划，则将允许完成从该计划触发的、当前正在处理的所有报表和订阅。</span><span class="sxs-lookup"><span data-stu-id="f0d96-107">If you edit a schedule while it is being used, all currently processing reports and subscriptions triggered from that schedule will be allowed to finish.</span></span>  
  
 <span data-ttu-id="f0d96-108">在一个计划中无法支持所有形式的频率组合。</span><span class="sxs-lookup"><span data-stu-id="f0d96-108">Not all frequency combinations can be supported in a single schedule.</span></span> <span data-ttu-id="f0d96-109">例如，如果要在每周五的中午 12:00</span><span class="sxs-lookup"><span data-stu-id="f0d96-109">For example, if you want to run a report at 12:00 P.M.</span></span> <span data-ttu-id="f0d96-110">和下午 4:00</span><span class="sxs-lookup"><span data-stu-id="f0d96-110">and 4:00 P.M.</span></span> <span data-ttu-id="f0d96-111">运行报表，那么您必须创建两个每日计划，并指定运行日期为星期五，一个计划的开始时间为中午 12:00，</span><span class="sxs-lookup"><span data-stu-id="f0d96-111">every Friday, you must create two daily schedules that specify a Friday run date, one with a start time of 12:00 P.M.</span></span> <span data-ttu-id="f0d96-112">另一个计划的开始时间为下午 4:00。</span><span class="sxs-lookup"><span data-stu-id="f0d96-112">and another with a start time of 4:00 P.M.</span></span>  
  
 <span data-ttu-id="f0d96-113">计划处理过程以承载和处理计划的报表服务器的本地时间为准。</span><span class="sxs-lookup"><span data-stu-id="f0d96-113">Schedule processing is based on the local time of the report server that hosts and processes the schedule.</span></span>  
  
 <span data-ttu-id="f0d96-114">若要打开此页，请启动 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，连接到 Report Server，打开 "**共享**计划" 文件夹，右键单击共享计划，然后选择 **"属性**"。</span><span class="sxs-lookup"><span data-stu-id="f0d96-114">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server, open the **Shared Schedules** folder, right-click a shared schedule, and select **Properties**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f0d96-115">并非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的每个版本均提供此功能；并且在运行不具有此功能的版本时，此页将不会出现。</span><span class="sxs-lookup"><span data-stu-id="f0d96-115">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and this page does not appear when you are running an edition which does not have this feature.</span></span> <span data-ttu-id="f0d96-116">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅[SQL Server 2012 (版本支持的功能](https://go.microsoft.com/fwlink/?linkid=232473) https://go.microsoft.com/fwlink/?linkid=232473) 。</span><span class="sxs-lookup"><span data-stu-id="f0d96-116">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
## <a name="options"></a><span data-ttu-id="f0d96-117">选项</span><span class="sxs-lookup"><span data-stu-id="f0d96-117">Options</span></span>  
 <span data-ttu-id="f0d96-118">**名称**</span><span class="sxs-lookup"><span data-stu-id="f0d96-118">**Name**</span></span>  
 <span data-ttu-id="f0d96-119">为该共享计划指定名称。</span><span class="sxs-lookup"><span data-stu-id="f0d96-119">Specifies the name for the shared schedule.</span></span>  
  
 <span data-ttu-id="f0d96-120">**运行此计划的开始日期**</span><span class="sxs-lookup"><span data-stu-id="f0d96-120">**Begin running this schedule on**</span></span>  
 <span data-ttu-id="f0d96-121">为此计划指定开始日期。</span><span class="sxs-lookup"><span data-stu-id="f0d96-121">Specifies a start date for this schedule.</span></span>  
  
 <span data-ttu-id="f0d96-122">**此计划的结束日期**</span><span class="sxs-lookup"><span data-stu-id="f0d96-122">**Stop this schedule on**</span></span>  
 <span data-ttu-id="f0d96-123">为此计划指定过期日期。</span><span class="sxs-lookup"><span data-stu-id="f0d96-123">Specifies an expiration date for this schedule.</span></span>  
  
 <span data-ttu-id="f0d96-124">**Type**</span><span class="sxs-lookup"><span data-stu-id="f0d96-124">**Type**</span></span>  
 <span data-ttu-id="f0d96-125">指定重复执行模式是主要基于小时、天、周、月还是仅运行一次。</span><span class="sxs-lookup"><span data-stu-id="f0d96-125">Specifies whether the recurrence pattern is based primarily on hours, days, weeks, months, or only runs once.</span></span>  
  
 <span data-ttu-id="f0d96-126">**小时(重复执行模式)**</span><span class="sxs-lookup"><span data-stu-id="f0d96-126">**Hour (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="f0d96-127">指定用于以小时为间隔运行计划操作（例如，每 6 小时运行一次报表）的选项。</span><span class="sxs-lookup"><span data-stu-id="f0d96-127">Specifies options for running a scheduled operation in intervals of an hour (for example, to run a report every 6 hours).</span></span> <span data-ttu-id="f0d96-128">可以按小时和分钟指定时间间隔。</span><span class="sxs-lookup"><span data-stu-id="f0d96-128">You can specify the interval in hours and minutes.</span></span>  
  
 <span data-ttu-id="f0d96-129">**天(重复执行模式)**</span><span class="sxs-lookup"><span data-stu-id="f0d96-129">**Day (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="f0d96-130">指定用于以天为间隔运行计划操作（例如，每 2 天运行一次报表）的选项。</span><span class="sxs-lookup"><span data-stu-id="f0d96-130">Specifies options for running a scheduled operation in intervals of days (for example, to run a report every 2 days).</span></span> <span data-ttu-id="f0d96-131">可以按天指定时间间隔，并指定希望计划运行的具体时间（小时和分钟）。</span><span class="sxs-lookup"><span data-stu-id="f0d96-131">You can specify the interval in days and at the hour and minute you want the schedule to run.</span></span>  
  
 <span data-ttu-id="f0d96-132">**周(重复执行模式)**</span><span class="sxs-lookup"><span data-stu-id="f0d96-132">**Week (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="f0d96-133">指定用于以周为间隔运行计划操作或需要按周重复执行操作时（例如，每隔一周运行一次报表）的选项。</span><span class="sxs-lookup"><span data-stu-id="f0d96-133">Specifies options for running a scheduled operation in intervals of a week or when the pattern that you want to repeat is based on weeks (for example, to run a report every other week).</span></span> <span data-ttu-id="f0d96-134">可以指定每周计划，并指定希望计划运行的具体日期和时间（天、小时和分钟）。</span><span class="sxs-lookup"><span data-stu-id="f0d96-134">You can specify a weekly schedule to the day, hour, and minute that you want the schedule to run.</span></span>  
  
 <span data-ttu-id="f0d96-135">**月(重复执行模式)**</span><span class="sxs-lookup"><span data-stu-id="f0d96-135">**Month (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="f0d96-136">指定用于以月为间隔运行计划操作或需要按月重复执行操作时的选项。</span><span class="sxs-lookup"><span data-stu-id="f0d96-136">Specifies options for running a scheduled operation in intervals of a month or when the pattern that you want to repeat is based on months.</span></span> <span data-ttu-id="f0d96-137">可以指定每月计划，并指定希望计划运行的具体日期和时间（天、小时和分钟）。</span><span class="sxs-lookup"><span data-stu-id="f0d96-137">You can specify a monthly schedule to the day, hour, and minute that you want the schedule to run.</span></span> <span data-ttu-id="f0d96-138">可以在计划中忽略特定的月份。</span><span class="sxs-lookup"><span data-stu-id="f0d96-138">You can omit specific months from the schedule.</span></span>  
  
 <span data-ttu-id="f0d96-139">**曾经**</span><span class="sxs-lookup"><span data-stu-id="f0d96-139">**Once**</span></span>  
 <span data-ttu-id="f0d96-140">指定只在特定的日期和时间运行一次的计划。</span><span class="sxs-lookup"><span data-stu-id="f0d96-140">Specifies a schedule that runs only once, on a specific date and time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0d96-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f0d96-141">See Also</span></span>  
 <span data-ttu-id="f0d96-142">[Management Studio F1 帮助中的报表服务器](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="f0d96-142">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="f0d96-143">[在 Management Studio 中连接到报表服务器](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="f0d96-143">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="f0d96-144">[创建、修改和删除计划](../subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="f0d96-144">[Create, Modify, and Delete Schedules](../subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 [<span data-ttu-id="f0d96-145">计划</span><span class="sxs-lookup"><span data-stu-id="f0d96-145">Schedules</span></span>](../subscriptions/schedules.md)  
  
  
