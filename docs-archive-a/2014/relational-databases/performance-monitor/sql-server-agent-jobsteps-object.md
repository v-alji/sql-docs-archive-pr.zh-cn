---
title: SQL Server 代理 - JobSteps 对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- JobSteps object
- SQLAgent:JobSteps
ms.assetid: 44f9983c-1753-4fe0-8475-973aa2460b3a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3759303807714e2bb7f71f59e644bc485d36cfcb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579534"
---
# <a name="sql-server-agent-jobsteps-object"></a><span data-ttu-id="1a299-102">SQL Server 代理中的 JobSteps 对象</span><span class="sxs-lookup"><span data-stu-id="1a299-102">SQL Server Agent, JobSteps Object</span></span>
  <span data-ttu-id="1a299-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理中的 **JobSteps** 性能对象包含用于报告有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业步骤的信息的性能计数器。</span><span class="sxs-lookup"><span data-stu-id="1a299-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent **JobSteps** performance object contains performance counters that report information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job steps.</span></span> <span data-ttu-id="1a299-104">下表列出了此对象包含的计数器。</span><span class="sxs-lookup"><span data-stu-id="1a299-104">The table below lists the counters that this object contains.</span></span>  
  
 <span data-ttu-id="1a299-105">下表列出了 **SQLAgent:JobSteps** 计数器。</span><span class="sxs-lookup"><span data-stu-id="1a299-105">The table below contains the **SQLAgent:JobSteps** counters.</span></span>  
  
|<span data-ttu-id="1a299-106">名称</span><span class="sxs-lookup"><span data-stu-id="1a299-106">Name</span></span>|<span data-ttu-id="1a299-107">说明</span><span class="sxs-lookup"><span data-stu-id="1a299-107">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="1a299-108">**Active steps**</span><span class="sxs-lookup"><span data-stu-id="1a299-108">**Active steps**</span></span>|<span data-ttu-id="1a299-109">此计数器报告当前运行的作业步骤数。</span><span class="sxs-lookup"><span data-stu-id="1a299-109">This counter reports the number of job steps currently running.</span></span>|  
|<span data-ttu-id="1a299-110">**Queued steps**</span><span class="sxs-lookup"><span data-stu-id="1a299-110">**Queued steps**</span></span>|<span data-ttu-id="1a299-111">此计数器报告 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理准备运行但尚未开始运行的作业步骤数。</span><span class="sxs-lookup"><span data-stu-id="1a299-111">This counter reports the number of job steps that are ready for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to run, but which have not yet started running.</span></span>|  
|<span data-ttu-id="1a299-112">**Total step retries**</span><span class="sxs-lookup"><span data-stu-id="1a299-112">**Total step retries**</span></span>|<span data-ttu-id="1a299-113">此计数器报告自上次服务器重新启动以来 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 重试某作业步骤的总次数。</span><span class="sxs-lookup"><span data-stu-id="1a299-113">This counter reports the total number of times that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has retried a job step since the last server restart.</span></span>|  
  
 <span data-ttu-id="1a299-114">对象中的每个计数器均包含以下实例：</span><span class="sxs-lookup"><span data-stu-id="1a299-114">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="1a299-115">实例</span><span class="sxs-lookup"><span data-stu-id="1a299-115">Instance</span></span>|<span data-ttu-id="1a299-116">说明</span><span class="sxs-lookup"><span data-stu-id="1a299-116">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="1a299-117">**_Total**</span><span class="sxs-lookup"><span data-stu-id="1a299-117">**_Total**</span></span>|<span data-ttu-id="1a299-118">有关所有作业步骤的信息。</span><span class="sxs-lookup"><span data-stu-id="1a299-118">Information for all job steps.</span></span>|  
|<span data-ttu-id="1a299-119">**ActiveScripting**</span><span class="sxs-lookup"><span data-stu-id="1a299-119">**ActiveScripting**</span></span>|<span data-ttu-id="1a299-120">有关使用 **ActiveScripting** 子系统的作业步骤的信息。</span><span class="sxs-lookup"><span data-stu-id="1a299-120">Information for job steps that use the **ActiveScripting** subsystem.</span></span>|  
|<span data-ttu-id="1a299-121">**ANALYSISCOMMAND**</span><span class="sxs-lookup"><span data-stu-id="1a299-121">**ANALYSISCOMMAND**</span></span>|<span data-ttu-id="1a299-122">有关使用 ANALYSISCOMMAND 子系统的作业步骤的信息。</span><span class="sxs-lookup"><span data-stu-id="1a299-122">Information for job steps that use the ANALYSISCOMMAND subsystem.</span></span>|  
|<span data-ttu-id="1a299-123">**ANALYSISQUERY**</span><span class="sxs-lookup"><span data-stu-id="1a299-123">**ANALYSISQUERY**</span></span>|<span data-ttu-id="1a299-124">有关使用 ANALYSISQUERY 子系统的作业步骤的信息。</span><span class="sxs-lookup"><span data-stu-id="1a299-124">Information for job steps that use the ANALYSISQUERY subsystem.</span></span>|  
|<span data-ttu-id="1a299-125">**CmdExec**</span><span class="sxs-lookup"><span data-stu-id="1a299-125">**CmdExec**</span></span>|<span data-ttu-id="1a299-126">有关使用 **CmdExec** 子系统的作业步骤的信息。</span><span class="sxs-lookup"><span data-stu-id="1a299-126">Information for job steps that use the **CmdExec** subsystem.</span></span>|  
|<span data-ttu-id="1a299-127">**Distribution**</span><span class="sxs-lookup"><span data-stu-id="1a299-127">**Distribution**</span></span>|<span data-ttu-id="1a299-128">有关使用 **Distribution** 子系统的作业步骤的信息。</span><span class="sxs-lookup"><span data-stu-id="1a299-128">Information for job steps that use the **Distribution** subsystem.</span></span>|  
|<span data-ttu-id="1a299-129">**Dts**</span><span class="sxs-lookup"><span data-stu-id="1a299-129">**Dts**</span></span>|<span data-ttu-id="1a299-130">有关使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 子系统的作业步骤的信息。</span><span class="sxs-lookup"><span data-stu-id="1a299-130">Information for job steps that use the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] subsystem.</span></span>|  
|<span data-ttu-id="1a299-131">**LogReader**</span><span class="sxs-lookup"><span data-stu-id="1a299-131">**LogReader**</span></span>|<span data-ttu-id="1a299-132">有关使用 **LogReader** 子系统的作业步骤的信息。</span><span class="sxs-lookup"><span data-stu-id="1a299-132">Information for job steps that use the **LogReader** subsystem.</span></span>|  
|<span data-ttu-id="1a299-133">**合并**</span><span class="sxs-lookup"><span data-stu-id="1a299-133">**Merge**</span></span>|<span data-ttu-id="1a299-134">有关使用 **Merge** 子系统的作业步骤的信息。</span><span class="sxs-lookup"><span data-stu-id="1a299-134">Information for job steps that use the **Merge** subsystem.</span></span>|  
|<span data-ttu-id="1a299-135">**PowerShell**</span><span class="sxs-lookup"><span data-stu-id="1a299-135">**PowerShell**</span></span>|<span data-ttu-id="1a299-136">有关使用 **PowerShell** 子系统的作业步骤的信息。</span><span class="sxs-lookup"><span data-stu-id="1a299-136">Information for job steps that use the **PowerShell** subsystem.</span></span>|  
|<span data-ttu-id="1a299-137">**QueueReader**</span><span class="sxs-lookup"><span data-stu-id="1a299-137">**QueueReader**</span></span>|<span data-ttu-id="1a299-138">有关使用 **QueueReader** 子系统的作业步骤的信息。</span><span class="sxs-lookup"><span data-stu-id="1a299-138">Information for job steps that use the **QueueReader** subsystem.</span></span>|  
|<span data-ttu-id="1a299-139">**快照**</span><span class="sxs-lookup"><span data-stu-id="1a299-139">**Snapshot**</span></span>|<span data-ttu-id="1a299-140">有关使用 **Snapshot** 子系统的作业步骤的信息。</span><span class="sxs-lookup"><span data-stu-id="1a299-140">Information for job steps that use the **Snapshot** subsystem.</span></span>|  
|<span data-ttu-id="1a299-141">**TSQL**</span><span class="sxs-lookup"><span data-stu-id="1a299-141">**TSQL**</span></span>|<span data-ttu-id="1a299-142">有关执行 [!INCLUDE[tsql](../../includes/tsql-md.md)]的作业步骤的信息。</span><span class="sxs-lookup"><span data-stu-id="1a299-142">Information for job steps that execute [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1a299-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1a299-143">See Also</span></span>  
 <span data-ttu-id="1a299-144">[管理作业步骤](../../ssms/agent/manage-job-steps.md) </span><span class="sxs-lookup"><span data-stu-id="1a299-144">[Manage Job Steps](../../ssms/agent/manage-job-steps.md) </span></span>  
 <span data-ttu-id="1a299-145">[使用性能对象](../../ssms/agent/use-performance-objects.md) </span><span class="sxs-lookup"><span data-stu-id="1a299-145">[Use Performance Objects](../../ssms/agent/use-performance-objects.md) </span></span>  
 [<span data-ttu-id="1a299-146">监视资源使用情况（系统监视器）</span><span class="sxs-lookup"><span data-stu-id="1a299-146">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
