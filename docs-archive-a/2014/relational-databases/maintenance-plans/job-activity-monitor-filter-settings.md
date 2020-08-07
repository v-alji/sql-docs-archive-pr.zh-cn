---
title: 作业活动监视器（筛选设置）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.jobactivitymon.filter.f1
ms.assetid: 89cb0055-5262-447f-8464-7203d4caba78
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: feba7b992d5d1d375b93df12135487a092792ee1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589050"
---
# <a name="job-activity-monitor-filter-settings"></a><span data-ttu-id="6cdd9-102">作业活动监视器（筛选设置）</span><span class="sxs-lookup"><span data-stu-id="6cdd9-102">Job Activity Monitor (Filter Settings)</span></span>
  <span data-ttu-id="6cdd9-103">使用此页可以减少作业活动监视器中可见的行数。</span><span class="sxs-lookup"><span data-stu-id="6cdd9-103">Use this page to reduce the number of rows visible in the Job Activity Monitor.</span></span> <span data-ttu-id="6cdd9-104">在一个或多个可用框中输入条件，以便仅显示符合指定值的行。</span><span class="sxs-lookup"><span data-stu-id="6cdd9-104">Enter criteria in one or several of the available boxes, to show only the rows that meet the specified values.</span></span> <span data-ttu-id="6cdd9-105">其中某些框（如“状态”  或“阻塞类型”  ）通过下拉列表提供有限数量的可能值。</span><span class="sxs-lookup"><span data-stu-id="6cdd9-105">Some of the boxes, such as **Status** or **Blocking Type** offer a finite number of possible values, provided by a drop-down list.</span></span> <span data-ttu-id="6cdd9-106">其他框（如 **“应用程序”** ）则允许以逗号分隔的列表形式输入不限数量的任意值。</span><span class="sxs-lookup"><span data-stu-id="6cdd9-106">Others, such as **Application,** allow you to enter whatever value and as many values as you wish, as a comma separated list.</span></span> <span data-ttu-id="6cdd9-107">使用工具栏图标，可以按类别或按字母顺序对可用的框进行排序。</span><span class="sxs-lookup"><span data-stu-id="6cdd9-107">Toolbar icons allow you to sort the available boxes by category or alphabetically.</span></span> <span data-ttu-id="6cdd9-108">单击各个条件可以显示该条件的简短说明。</span><span class="sxs-lookup"><span data-stu-id="6cdd9-108">Click the criteria to show a short description of the each one.</span></span>  
  
 <span data-ttu-id="6cdd9-109">若要筛选作业活动监视器，请提供所需数量的筛选条件，单击 **“应用筛选器”** ，再单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="6cdd9-109">To filter the Job Activity Monitor, provide as many filter criteria as you want, click **Apply filter**, and then click **OK**.</span></span>  
  
## <a name="all-jobs"></a><span data-ttu-id="6cdd9-110">所有作业</span><span class="sxs-lookup"><span data-stu-id="6cdd9-110">All Jobs</span></span>  
 <span data-ttu-id="6cdd9-111">在筛选作业活动监视器时，可以使用这组筛选条件。</span><span class="sxs-lookup"><span data-stu-id="6cdd9-111">This group of filter criteria is available when filtering the Job Activity Monitor.</span></span>  
  
 <span data-ttu-id="6cdd9-112">**名称**</span><span class="sxs-lookup"><span data-stu-id="6cdd9-112">**Name**</span></span>  
 <span data-ttu-id="6cdd9-113">按名称筛选作业。</span><span class="sxs-lookup"><span data-stu-id="6cdd9-113">Filter jobs by name.</span></span>  
  
 <span data-ttu-id="6cdd9-114">**下次运行时间**</span><span class="sxs-lookup"><span data-stu-id="6cdd9-114">**Next Run**</span></span>  
 <span data-ttu-id="6cdd9-115">按下次计划运行的日期筛选。</span><span class="sxs-lookup"><span data-stu-id="6cdd9-115">Filter by the date next scheduled to run.</span></span>  
  
 <span data-ttu-id="6cdd9-116">**可运行**</span><span class="sxs-lookup"><span data-stu-id="6cdd9-116">**Runnable**</span></span>  
 <span data-ttu-id="6cdd9-117">查看可以运行的作业或不能运行的作业。</span><span class="sxs-lookup"><span data-stu-id="6cdd9-117">View jobs that can be run, or jobs that cannot be run.</span></span> <span data-ttu-id="6cdd9-118">选择 **“是”** 将只查看可以运行的作业，选择 **“否”** 将只查看不能运行的作业，或选择 **“全部”** 将同时查看可以运行和不能运行的作业。</span><span class="sxs-lookup"><span data-stu-id="6cdd9-118">Select **Yes** to view only jobs that can be run, select **No** to view only jobs that cannot be run, or select **All** to view both jobs that can be run and those that cannot.</span></span>  
  
 <span data-ttu-id="6cdd9-119">**上次运行时间**</span><span class="sxs-lookup"><span data-stu-id="6cdd9-119">**Last Run**</span></span>  
 <span data-ttu-id="6cdd9-120">按上次运行的日期筛选。</span><span class="sxs-lookup"><span data-stu-id="6cdd9-120">Filter by the date last run.</span></span>  
  
 <span data-ttu-id="6cdd9-121">**上次运行结果**</span><span class="sxs-lookup"><span data-stu-id="6cdd9-121">**Last Run Outcome**</span></span>  
 <span data-ttu-id="6cdd9-122">按作业上次运行的状态筛选作业。</span><span class="sxs-lookup"><span data-stu-id="6cdd9-122">Filter jobs by the status last time the jobs were run.</span></span>  
  
 <span data-ttu-id="6cdd9-123">**已启用**</span><span class="sxs-lookup"><span data-stu-id="6cdd9-123">**Enabled**</span></span>  
 <span data-ttu-id="6cdd9-124">仅查看启用或未启用的作业。</span><span class="sxs-lookup"><span data-stu-id="6cdd9-124">View only enabled or not enabled jobs</span></span>  
  
 <span data-ttu-id="6cdd9-125">**类别**</span><span class="sxs-lookup"><span data-stu-id="6cdd9-125">**Category**</span></span>  
 <span data-ttu-id="6cdd9-126">按作业类别筛选作业。</span><span class="sxs-lookup"><span data-stu-id="6cdd9-126">Filter jobs by the job category.</span></span>  
  
 <span data-ttu-id="6cdd9-127"> 计划</span><span class="sxs-lookup"><span data-stu-id="6cdd9-127">**Scheduled**</span></span>  
 <span data-ttu-id="6cdd9-128">查看所有计划或未计划的作业。</span><span class="sxs-lookup"><span data-stu-id="6cdd9-128">View all jobs with schedules, or without schedules.</span></span>  
  
 <span data-ttu-id="6cdd9-129">**Status**</span><span class="sxs-lookup"><span data-stu-id="6cdd9-129">**Status**</span></span>  
 <span data-ttu-id="6cdd9-130">按状态筛选作业。</span><span class="sxs-lookup"><span data-stu-id="6cdd9-130">Filter jobs by the status.</span></span>  
  
## <a name="description-area"></a><span data-ttu-id="6cdd9-131">说明区</span><span class="sxs-lookup"><span data-stu-id="6cdd9-131">Description Area</span></span>  
 <span data-ttu-id="6cdd9-132">**说明框**</span><span class="sxs-lookup"><span data-stu-id="6cdd9-132">**Description Box**</span></span>  
 <span data-ttu-id="6cdd9-133">选定条件后，此未命名框将提供对所选条件的简短说明。</span><span class="sxs-lookup"><span data-stu-id="6cdd9-133">This unnamed box provides a short description of the criteria as they are selected.</span></span>  
  
 <span data-ttu-id="6cdd9-134">**“应用筛选器”**</span><span class="sxs-lookup"><span data-stu-id="6cdd9-134">**Apply filter**</span></span>  
 <span data-ttu-id="6cdd9-135">若要应用筛选器，请单击 "**应用筛选器**"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="6cdd9-135">To apply the filter, click **Apply filter** and then click **OK**.</span></span> <span data-ttu-id="6cdd9-136">若要保留 "**筛选设置**" 对话框中的筛选器设置，但不应用它们，请取消选中 "**应用筛选器**"，然后单击 **"确定"** 以显示所有行。</span><span class="sxs-lookup"><span data-stu-id="6cdd9-136">To retain the filter settings in the **Filter Settings** dialog box, but not apply them, uncheck **Apply filter**, and then click **OK**, to display all rows.</span></span>  
  
 <span data-ttu-id="6cdd9-137">**Clear**</span><span class="sxs-lookup"><span data-stu-id="6cdd9-137">**Clear**</span></span>  
 <span data-ttu-id="6cdd9-138">将筛选器设置恢复为默认设置。</span><span class="sxs-lookup"><span data-stu-id="6cdd9-138">Returns the filter settings back to the default settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cdd9-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6cdd9-139">See Also</span></span>  
 [<span data-ttu-id="6cdd9-140">监视作业活动</span><span class="sxs-lookup"><span data-stu-id="6cdd9-140">Monitor Job Activity</span></span>](../../ssms/agent/monitor-job-activity.md)  
  
  
