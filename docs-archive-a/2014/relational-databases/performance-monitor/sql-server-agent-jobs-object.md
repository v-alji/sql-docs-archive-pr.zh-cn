---
title: SQL Server 代理 - Jobs 对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLAgent:Jobs
- Jobs object
ms.assetid: 225b5e2d-4a78-4178-b2b6-b419df83c4aa
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 82ee57eba20d44c08eadc125e9dfd69e73c35751
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579535"
---
# <a name="sql-server-agent-jobs-object"></a><span data-ttu-id="2cb37-102">SQL Server 代理中的 Jobs 对象</span><span class="sxs-lookup"><span data-stu-id="2cb37-102">SQL Server Agent, Jobs Object</span></span>
  <span data-ttu-id="2cb37-103">SQL Server 代理的 **Jobs** 性能对象包含的性能计数器可报告有关 SQL Server 代理作业的信息。</span><span class="sxs-lookup"><span data-stu-id="2cb37-103">The SQL Server Agent **Jobs** performance object contains performance counters that report information about SQL Server Agent jobs.</span></span> <span data-ttu-id="2cb37-104">下表列出了此对象包含的计数器。</span><span class="sxs-lookup"><span data-stu-id="2cb37-104">The table below lists the counters that this object contains.</span></span>  
  
 <span data-ttu-id="2cb37-105">下表介绍了 **SQLAgent:Jobs** 计数器。</span><span class="sxs-lookup"><span data-stu-id="2cb37-105">The table below contains the **SQLAgent:Jobs** counters.</span></span>  
  
|<span data-ttu-id="2cb37-106">名称</span><span class="sxs-lookup"><span data-stu-id="2cb37-106">Name</span></span>|<span data-ttu-id="2cb37-107">说明</span><span class="sxs-lookup"><span data-stu-id="2cb37-107">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="2cb37-108">**Active Jobs**</span><span class="sxs-lookup"><span data-stu-id="2cb37-108">**Active Jobs**</span></span>|<span data-ttu-id="2cb37-109">该计数器报告当前运行的作业数。</span><span class="sxs-lookup"><span data-stu-id="2cb37-109">This counter reports the number of jobs currently running.</span></span>|  
|<span data-ttu-id="2cb37-110">**Failed jobs**</span><span class="sxs-lookup"><span data-stu-id="2cb37-110">**Failed jobs**</span></span>|<span data-ttu-id="2cb37-111">该计数器报告失败退出的作业数。</span><span class="sxs-lookup"><span data-stu-id="2cb37-111">This counter reports the number of jobs that exited with failure.</span></span>|  
|<span data-ttu-id="2cb37-112">**Job success rate**</span><span class="sxs-lookup"><span data-stu-id="2cb37-112">**Job success rate**</span></span>|<span data-ttu-id="2cb37-113">该计数器报告所执行的作业中成功完成的百分比。</span><span class="sxs-lookup"><span data-stu-id="2cb37-113">This counter reports the percentage of executed jobs that completed successfully.</span></span>|  
|<span data-ttu-id="2cb37-114">**Jobs activated/minute**</span><span class="sxs-lookup"><span data-stu-id="2cb37-114">**Jobs activated/minute**</span></span>|<span data-ttu-id="2cb37-115">该计数器报告最后一分钟内启动的作业数。</span><span class="sxs-lookup"><span data-stu-id="2cb37-115">This counter reports the number of jobs launched within the last minute.</span></span>|  
|<span data-ttu-id="2cb37-116">**Queued jobs**</span><span class="sxs-lookup"><span data-stu-id="2cb37-116">**Queued jobs**</span></span>|<span data-ttu-id="2cb37-117">该计数器报告已准备好供 SQL Server 代理准备运行但尚未开始运行的作业数。</span><span class="sxs-lookup"><span data-stu-id="2cb37-117">This counter reports the number of jobs that are ready for SQL Server Agent to run, but which have not yet started running.</span></span>|  
|<span data-ttu-id="2cb37-118">**Successful jobs**</span><span class="sxs-lookup"><span data-stu-id="2cb37-118">**Successful jobs**</span></span>|<span data-ttu-id="2cb37-119">该计数器报告成功退出的作业数。</span><span class="sxs-lookup"><span data-stu-id="2cb37-119">This counter reports the number of jobs that exited with success.</span></span>|  
  
 <span data-ttu-id="2cb37-120">对象中的每个计数器均包含以下实例：</span><span class="sxs-lookup"><span data-stu-id="2cb37-120">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="2cb37-121">实例</span><span class="sxs-lookup"><span data-stu-id="2cb37-121">Instance</span></span>|<span data-ttu-id="2cb37-122">说明</span><span class="sxs-lookup"><span data-stu-id="2cb37-122">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="2cb37-123">**_Total**</span><span class="sxs-lookup"><span data-stu-id="2cb37-123">**_Total**</span></span>|<span data-ttu-id="2cb37-124">所有作业的信息。</span><span class="sxs-lookup"><span data-stu-id="2cb37-124">Information for all jobs.</span></span>|  
|<span data-ttu-id="2cb37-125">**警报**</span><span class="sxs-lookup"><span data-stu-id="2cb37-125">**Alerts**</span></span>|<span data-ttu-id="2cb37-126">由警报启动的作业的信息。</span><span class="sxs-lookup"><span data-stu-id="2cb37-126">Information for jobs started by alerts.</span></span>|  
|<span data-ttu-id="2cb37-127">**其他**</span><span class="sxs-lookup"><span data-stu-id="2cb37-127">**Others**</span></span>|<span data-ttu-id="2cb37-128">不是由警报或计划启动的作业的信息。</span><span class="sxs-lookup"><span data-stu-id="2cb37-128">Information for jobs that were not started by alerts or schedules.</span></span> <span data-ttu-id="2cb37-129">通常这些作业是使用 **sp_start_job**手动启动的作业。</span><span class="sxs-lookup"><span data-stu-id="2cb37-129">Typically these are jobs started manually using **sp_start_job**.</span></span>|  
|<span data-ttu-id="2cb37-130">**计划**</span><span class="sxs-lookup"><span data-stu-id="2cb37-130">**Schedules**</span></span>|<span data-ttu-id="2cb37-131">由计划启动的作业的信息。</span><span class="sxs-lookup"><span data-stu-id="2cb37-131">Information for jobs started by schedules.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2cb37-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2cb37-132">See Also</span></span>  
 <span data-ttu-id="2cb37-133">[执行作业](../../ssms/agent/implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="2cb37-133">[Implement Jobs](../../ssms/agent/implement-jobs.md) </span></span>  
 <span data-ttu-id="2cb37-134">[使用性能对象](../../ssms/agent/use-performance-objects.md) </span><span class="sxs-lookup"><span data-stu-id="2cb37-134">[Use Performance Objects](../../ssms/agent/use-performance-objects.md) </span></span>  
 [<span data-ttu-id="2cb37-135">监视资源使用情况（系统监视器）</span><span class="sxs-lookup"><span data-stu-id="2cb37-135">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
