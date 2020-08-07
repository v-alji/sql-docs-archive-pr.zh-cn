---
title: 维护计划 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- SQL12.AG.MAINTPLAN.LEGACY.F1
helpviewer_keywords:
- maintenance plans [SQL Server], about database maintenance plans
- maintenance plans [SQL Server], database compatibility level displayed in designer
- maintenance plans [SQL Server]
ms.assetid: 5982ca65-74fe-44e3-aef9-00a65a0db169
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2f614e2cfad78cb1efddc49cc897ca57087fec68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576747"
---
# <a name="maintenance-plans"></a><span data-ttu-id="3e8d7-102">维护计划</span><span class="sxs-lookup"><span data-stu-id="3e8d7-102">Maintenance Plans</span></span>
  <span data-ttu-id="3e8d7-103">维护计划可创建所需的任务工作流，以确保优化数据库、定期进行备份并确保数据库一致。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-103">Maintenance plans create a workflow of the tasks required to make sure that your database is optimized, regularly backed up, and free of inconsistencies.</span></span> <span data-ttu-id="3e8d7-104">维护计划向导还可创建核心维护计划，但手动创建计划具有更大的灵活性。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-104">The Maintenance Plan Wizard also creates core maintenance plans, but creating plans manually gives you much more flexibility.</span></span>  
  
## <a name="benefits-of-maintenance-plans"></a><span data-ttu-id="3e8d7-105">维护计划的优点</span><span class="sxs-lookup"><span data-stu-id="3e8d7-105">Benefits of Maintenance Plans</span></span>  
 <span data-ttu-id="3e8d7-106">在 [!INCLUDE[ssDECurrent](../../includes/ssdecurrent-md.md)]中，维护计划将创建由 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 代理作业运行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-106">In [!INCLUDE[ssDECurrent](../../includes/ssdecurrent-md.md)], maintenance plans create an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package, which is run by a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span> <span data-ttu-id="3e8d7-107">可以按预订的时间间隔手动或自动运行维护计划。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-107">Maintenance plans can be run manually or automatically at scheduled intervals.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="3e8d7-108">维护计划可提供以下功能：</span><span class="sxs-lookup"><span data-stu-id="3e8d7-108">maintenance plans provide the following features:</span></span>  
  
-   <span data-ttu-id="3e8d7-109">使用各种典型维护任务创建工作流的功能。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-109">Workflow creation using a variety of typical maintenance tasks.</span></span> <span data-ttu-id="3e8d7-110">此外，还可以创建自己的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-110">You can also create your own custom [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts.</span></span>  
  
-   <span data-ttu-id="3e8d7-111">概念性层次结构。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-111">Conceptual hierarchies.</span></span> <span data-ttu-id="3e8d7-112">使用每个计划可创建或编辑任务工作流。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-112">Each plan lets you create or edit task workflows.</span></span> <span data-ttu-id="3e8d7-113">每个计划的任务可分组到子计划中，可以安排这些子计划在不同时间运行。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-113">Tasks in each plan can be grouped into subplans, which can be scheduled to run at different times.</span></span>  
  
-   <span data-ttu-id="3e8d7-114">支持可以用于主服务器/目标服务器环境中的多服务器计划。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-114">Support for multiserver plans that can be used in master server/target server environments.</span></span>  
  
-   <span data-ttu-id="3e8d7-115">支持在远程服务器上记录计划历史记录。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-115">Support for logging plan history to remote servers.</span></span>  
  
-   <span data-ttu-id="3e8d7-116">支持 Windows 身份验证和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-116">Support for Windows Authentication and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
## <a name="maintenace-plan-functionality"></a><span data-ttu-id="3e8d7-117">维护计划功能</span><span class="sxs-lookup"><span data-stu-id="3e8d7-117">Maintenace Plan Functionality</span></span>  
 <span data-ttu-id="3e8d7-118">可以创建维护计划来执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="3e8d7-118">Maintenance plans can be created to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="3e8d7-119">用新填充因子重新生成索引来重新组织数据和索引页上的数据。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-119">Reorganize the data on the data and index pages by rebuilding indexes with a new fill factor.</span></span> <span data-ttu-id="3e8d7-120">用新填充因子重新生成索引会确保数据库页中包含的数据量和可用空间的平均分布。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-120">Rebuilding indexes with a new fill factor makes sure that database pages contain an equally distributed amount of data and free space.</span></span> <span data-ttu-id="3e8d7-121">还使得以后能够更快地增长。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-121">It also enables faster growth in the future.</span></span> <span data-ttu-id="3e8d7-122">有关详细信息，请参阅 [为索引指定填充因子](../indexes/specify-fill-factor-for-an-index.md)。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-122">For more information, see [Specify Fill Factor for an Index](../indexes/specify-fill-factor-for-an-index.md).</span></span>  
  
-   <span data-ttu-id="3e8d7-123">通过删除空数据库页压缩数据文件。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-123">Compress data files by removing empty database pages.</span></span>  
  
-   <span data-ttu-id="3e8d7-124">更新索引统计信息，确保查询优化器含有关于表中数据值分布的最新信息。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-124">Update index statistics to make sure the query optimizer has current information about the distribution of data values in the tables.</span></span> <span data-ttu-id="3e8d7-125">这使得查询优化器能够更好地确定访问数据的最佳方法，因为可以获得数据库中存储数据的详细信息。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-125">This enables the query optimizer to make better judgments about the best way to access data, because it has more information about the data stored in the database.</span></span> <span data-ttu-id="3e8d7-126">虽然 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会定期自动更新索引统计信息，但是此选项可以对统计信息立即进行强制更新。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-126">Although index statistics are automatically updated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] periodically, this option can force the statistics to update immediately.</span></span>  
  
-   <span data-ttu-id="3e8d7-127">对数据库内的数据和数据页执行内部一致性检查，确保系统或软件故障没有损坏数据。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-127">Perform internal consistency checks of the data and data pages within the database to make sure that a system or software problem has not damaged data.</span></span>  
  
-   <span data-ttu-id="3e8d7-128">备份数据库和事务日志文件。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-128">Back up the database and transaction log files.</span></span> <span data-ttu-id="3e8d7-129">数据库和日志备份可以保留一段指定时间。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-129">Database and log backups can be retained for a specified period.</span></span> <span data-ttu-id="3e8d7-130">这样，您就可以为备份创建一份历史记录，以便在需要将数据库还原到早于上一次数据库备份的时间的时候使用。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-130">This lets you create a history of backups to be used if you have to restore the database to a time earlier than the last database backup.</span></span> <span data-ttu-id="3e8d7-131">还可以执行差异备份。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-131">You can also perform differential backups.</span></span>  
  
-   <span data-ttu-id="3e8d7-132">运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-132">Run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span> <span data-ttu-id="3e8d7-133">这可以用来创建可执行各种操作的作业以及运行这些作业的维护计划。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-133">This can be used to create jobs that perform a variety of actions and the maintenance plans to run those jobs.</span></span>  
  
 <span data-ttu-id="3e8d7-134">维护任务生成的结果可以作为报表写入文本文件，或写入 `sysmaintplan_log` 中的维护计划表（`sysmaintplan_logdetail` 和 `msdb`）。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-134">The results generated by the maintenance tasks can be written as a report to a text file or to the maintenance plan tables (`sysmaintplan_log` and `sysmaintplan_logdetail`) in `msdb`.</span></span> <span data-ttu-id="3e8d7-135">若要在日志文件查看器中查看结果，请右键单击“维护计划”，再单击“查看历史记录”。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-135">To view the results in the log file viewer, right-click **Maintenance Plans**, and then click **View History**.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="3e8d7-136">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="3e8d7-136">Related Tasks</span></span>  
 <span data-ttu-id="3e8d7-137">参考以下主题以开始使用维护计划。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-137">Use the following topics to get started with maintenance plans.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3e8d7-138">**说明**</span><span class="sxs-lookup"><span data-stu-id="3e8d7-138">**Description**</span></span>|<span data-ttu-id="3e8d7-139">**主题**</span><span class="sxs-lookup"><span data-stu-id="3e8d7-139">**Topic**</span></span>|  
|<span data-ttu-id="3e8d7-140">说明如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 创建维护计划。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-140">Describes how to create a maintenance plan by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>|[<span data-ttu-id="3e8d7-141">创建维护计划</span><span class="sxs-lookup"><span data-stu-id="3e8d7-141">Create a Maintenance Plan</span></span>](create-a-maintenance-plan.md)|  
|<span data-ttu-id="3e8d7-142">说明如何使用维护计划设计图面创建维护计划。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-142">Describes how to create a maintenance plan by using the Maintenance Plan Design Surface.</span></span>|[<span data-ttu-id="3e8d7-143">创建维护计划（维护计划设计图面）</span><span class="sxs-lookup"><span data-stu-id="3e8d7-143">Create a Maintenance Plan &#40;Maintenance Plan Design Surface&#41;</span></span>](create-a-maintenance-plan-maintenance-plan-design-surface.md)|  
|<span data-ttu-id="3e8d7-144">对象资源管理器中可用的文档维护计划功能。</span><span class="sxs-lookup"><span data-stu-id="3e8d7-144">Documents maintenance plan functionality available in Object Explorer.</span></span>|[<span data-ttu-id="3e8d7-145">维护计划节点（对象资源管理器）</span><span class="sxs-lookup"><span data-stu-id="3e8d7-145">Maintenance Plans Node &#40;Object Explorer&#41;</span></span>](../../ssms/object/object-explorer.md)|  
  
  
