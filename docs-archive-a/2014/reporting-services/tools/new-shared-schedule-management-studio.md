---
title: 新建共享计划 (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.newschedule.f1
ms.assetid: b2c69586-d98e-4933-827d-f5e6c15c5203
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6afd406730f815d3ab61e59cdebd21d564daa74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579990"
---
# <a name="new-shared-schedule-management-studio"></a><span data-ttu-id="69aef-102">新建共享计划 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="69aef-102">New Shared Schedule (Management Studio)</span></span>
  <span data-ttu-id="69aef-103">使用此页可以创建一个共享计划来运行已发布的报表和订阅。</span><span class="sxs-lookup"><span data-stu-id="69aef-103">Use this page to create a shared schedule to run published reports and subscriptions.</span></span> <span data-ttu-id="69aef-104">共享计划可以用于替代报表特定计划或订阅特定计划。</span><span class="sxs-lookup"><span data-stu-id="69aef-104">Shared schedules can be used in place of report-specific or subscription-specific schedules.</span></span> <span data-ttu-id="69aef-105">集中的计划信息与能够暂停和恢复计划操作的功能是共享计划区别于项特定计划的两个关键功能。</span><span class="sxs-lookup"><span data-stu-id="69aef-105">Centralized schedule information and the ability to pause and resume scheduled operations are two key features that distinguish shared schedules from item-specific schedules.</span></span>  
  
 <span data-ttu-id="69aef-106">在一个计划中无法支持所有形式的频率组合。</span><span class="sxs-lookup"><span data-stu-id="69aef-106">Not all frequency combinations can be supported in a single schedule.</span></span> <span data-ttu-id="69aef-107">例如，如果要在每周五的中午 12:00</span><span class="sxs-lookup"><span data-stu-id="69aef-107">For example, if you want to run a report at 12:00 P.M.</span></span> <span data-ttu-id="69aef-108">和下午 4:00</span><span class="sxs-lookup"><span data-stu-id="69aef-108">and 4:00 P.M.</span></span> <span data-ttu-id="69aef-109">运行报表，那么您必须创建两个每日计划，并指定运行日期为星期五，一个计划的开始时间为中午 12:00，</span><span class="sxs-lookup"><span data-stu-id="69aef-109">every Friday, you must create two daily schedules that specify a Friday run date, one with a start time of 12:00 P.M.</span></span> <span data-ttu-id="69aef-110">另一个计划的开始时间为下午 4:00。</span><span class="sxs-lookup"><span data-stu-id="69aef-110">and another with a start time of 4:00 P.M.</span></span>  
  
 <span data-ttu-id="69aef-111">计划处理过程以承载和处理计划的报表服务器的本地时间为准。</span><span class="sxs-lookup"><span data-stu-id="69aef-111">Schedule processing is based on the local time of the report server that hosts and processes the schedule.</span></span>  
  
 <span data-ttu-id="69aef-112">若要打开此页，请启动 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，连接到报表服务器，右键单击“共享计划”  ，然后选择“新建计划”  。</span><span class="sxs-lookup"><span data-stu-id="69aef-112">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server, right-click **Shared Schedule**, and select **New Schedule**.</span></span> <span data-ttu-id="69aef-113">若要保存计划，必须运行 SQL Server 代理服务。</span><span class="sxs-lookup"><span data-stu-id="69aef-113">To save the schedule, SQL Server Agent service must be running.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="69aef-114">并非在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的每个版本中均提供此功能。</span><span class="sxs-lookup"><span data-stu-id="69aef-114">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="69aef-115">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]各版本支持的功能列表，请参阅 [SQL Server 2012 各个版本支持的功能](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473) 。</span><span class="sxs-lookup"><span data-stu-id="69aef-115">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
## <a name="options"></a><span data-ttu-id="69aef-116">选项</span><span class="sxs-lookup"><span data-stu-id="69aef-116">Options</span></span>  
 <span data-ttu-id="69aef-117">**名称**</span><span class="sxs-lookup"><span data-stu-id="69aef-117">**Name**</span></span>  
 <span data-ttu-id="69aef-118">键入共享计划的名称。</span><span class="sxs-lookup"><span data-stu-id="69aef-118">Type a name for the shared schedule.</span></span> <span data-ttu-id="69aef-119">当用户为报表和订阅选择共享计划时，此名称会出现在下拉列表中。</span><span class="sxs-lookup"><span data-stu-id="69aef-119">This name appears in drop-down lists when users select a shared schedule for reports and subscriptions.</span></span> <span data-ttu-id="69aef-120">请确保提供能够很方便地适合列表并能够轻松地区分不同共享计划的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="69aef-120">Be sure to provide a descriptive name that fits easily within a list and that easily distinguishes one shared schedule from another.</span></span> <span data-ttu-id="69aef-121">名称必须至少包含一个字母数字字符。</span><span class="sxs-lookup"><span data-stu-id="69aef-121">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="69aef-122">还可以包含空格和某些符号。</span><span class="sxs-lookup"><span data-stu-id="69aef-122">It can also include spaces and some symbols.</span></span> <span data-ttu-id="69aef-123">在指定名称时请不要使用以下字符：</span><span class="sxs-lookup"><span data-stu-id="69aef-123">Do not use the following characters when specifying a name:</span></span>  
  
 <span data-ttu-id="69aef-124">; ?</span><span class="sxs-lookup"><span data-stu-id="69aef-124">; ?</span></span> <span data-ttu-id="69aef-125">： \@ & = +，$/\*\< ></span><span class="sxs-lookup"><span data-stu-id="69aef-125">: \@ & = + , $ / \* \< ></span></span>  
  
 <span data-ttu-id="69aef-126">" /</span><span class="sxs-lookup"><span data-stu-id="69aef-126">" /</span></span>  
  
 <span data-ttu-id="69aef-127">**运行此计划的开始日期**</span><span class="sxs-lookup"><span data-stu-id="69aef-127">**Begin running this schedule on**</span></span>  
 <span data-ttu-id="69aef-128">指定此计划的开始日期。</span><span class="sxs-lookup"><span data-stu-id="69aef-128">Specify a start date for this schedule.</span></span>  
  
 <span data-ttu-id="69aef-129">**此计划的结束日期**</span><span class="sxs-lookup"><span data-stu-id="69aef-129">**Stop this schedule on**</span></span>  
 <span data-ttu-id="69aef-130">指定此计划的过期日期。</span><span class="sxs-lookup"><span data-stu-id="69aef-130">Specify an expiration date for this schedule.</span></span>  
  
 <span data-ttu-id="69aef-131">类型 </span><span class="sxs-lookup"><span data-stu-id="69aef-131">**Type**</span></span>  
 <span data-ttu-id="69aef-132">指定重复执行模式是主要基于小时、天、周还是月。</span><span class="sxs-lookup"><span data-stu-id="69aef-132">Specifies whether the recurrence pattern is based primarily on hours, days, weeks, or months.</span></span>  
  
 <span data-ttu-id="69aef-133">**小时(重复执行模式)**</span><span class="sxs-lookup"><span data-stu-id="69aef-133">**Hour (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="69aef-134">选择相应的选项，以小时为间隔运行计划的操作（例如，每 6 小时运行一次报表）。</span><span class="sxs-lookup"><span data-stu-id="69aef-134">Select options to run a scheduled operation in intervals of an hour (for example, to run a report every 6 hours).</span></span> <span data-ttu-id="69aef-135">可以按小时和分钟指定时间间隔。</span><span class="sxs-lookup"><span data-stu-id="69aef-135">You can specify the interval in hours and minutes.</span></span>  
  
 <span data-ttu-id="69aef-136">**天(重复执行模式)**</span><span class="sxs-lookup"><span data-stu-id="69aef-136">**Day (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="69aef-137">选择相应的选项，以天为间隔运行计划的操作（例如，每 2 天运行一次报表）。</span><span class="sxs-lookup"><span data-stu-id="69aef-137">Select options to run a scheduled operation in intervals of days (for example, to run a report every 2 days).</span></span> <span data-ttu-id="69aef-138">可以按天指定时间间隔，并指定希望计划运行的具体时间（小时和分钟）。</span><span class="sxs-lookup"><span data-stu-id="69aef-138">You can specify the interval in days and at the hour and minute you want the schedule to run.</span></span>  
  
 <span data-ttu-id="69aef-139">**周(重复执行模式)**</span><span class="sxs-lookup"><span data-stu-id="69aef-139">**Week (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="69aef-140">选择相应的选项，以周为间隔运行计划的操作或者需要按周重复执行操作（例如，每隔一周运行一次报表）。</span><span class="sxs-lookup"><span data-stu-id="69aef-140">Select options to run a scheduled operation in intervals of a week or when the pattern that you want to repeat is based on weeks (for example, to run a report every other week).</span></span> <span data-ttu-id="69aef-141">可以指定每周计划，并指定希望计划运行的具体日期和时间（天、小时和分钟）。</span><span class="sxs-lookup"><span data-stu-id="69aef-141">You can specify a weekly schedule to the day, hour, and minute that you want the schedule to run.</span></span>  
  
 <span data-ttu-id="69aef-142">**月(重复执行模式)**</span><span class="sxs-lookup"><span data-stu-id="69aef-142">**Month (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="69aef-143">选择相应的选项，以月为间隔运行计划的操作或者需要按月重复执行操作。</span><span class="sxs-lookup"><span data-stu-id="69aef-143">Select options to run a scheduled operation in intervals of a month or when the pattern that you want to repeat is based on months.</span></span> <span data-ttu-id="69aef-144">可以指定每月计划，并指定希望计划运行的具体日期和时间（天、小时和分钟）。</span><span class="sxs-lookup"><span data-stu-id="69aef-144">You can specify a monthly schedule to the day, hour, and minute that you want the schedule to run.</span></span> <span data-ttu-id="69aef-145">可以在计划中忽略特定的月份。</span><span class="sxs-lookup"><span data-stu-id="69aef-145">You can omit specific months from the schedule.</span></span>  
  
 <span data-ttu-id="69aef-146">**一次**</span><span class="sxs-lookup"><span data-stu-id="69aef-146">**Once**</span></span>  
 <span data-ttu-id="69aef-147">选择此选项可以创建只在特定日期和时间运行一次的计划。</span><span class="sxs-lookup"><span data-stu-id="69aef-147">Select this option to create a schedule that runs only once, on a specific date and time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69aef-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="69aef-148">See Also</span></span>  
 <span data-ttu-id="69aef-149">[Management Studio 中报表服务器的 F1 帮助](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="69aef-149">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="69aef-150">[在 Management Studio 中连接到报表服务器](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="69aef-150">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="69aef-151">[创建、修改和删除计划](../subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="69aef-151">[Create, Modify, and Delete Schedules](../subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 <span data-ttu-id="69aef-152">[“计划”](../subscriptions/schedules.md) </span><span class="sxs-lookup"><span data-stu-id="69aef-152">[Schedules](../subscriptions/schedules.md) </span></span>  
 [<span data-ttu-id="69aef-153">Management Studio 中报表服务器的 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="69aef-153">Report Server in Management Studio F1 Help</span></span>](report-server-in-management-studio-f1-help.md)  
  
  
