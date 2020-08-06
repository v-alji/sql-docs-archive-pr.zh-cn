---
title: 数据库引擎优化顾问 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.dta.general.f1
ms.assetid: 50dd0a0b-a407-4aeb-bc8b-b02a793aa30a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2c49b771fb5a79da36d29f52dd065ca7ca0092aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591311"
---
# <a name="database-engine-tuning-advisor"></a><span data-ttu-id="e2c2c-102">Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="e2c2c-102">Database Engine Tuning Advisor</span></span>
  <span data-ttu-id="e2c2c-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 数据库引擎优化顾问 (DTA) 分析数据库并对优化查询性能提出建议。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Database Engine Tuning Advisor (DTA) analyzes databases and makes recommendations that you can use to optimize query performance.</span></span> <span data-ttu-id="e2c2c-104">借助数据库引擎优化顾问，您不必精通数据库结构或深谙 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，即可选择和创建索引、索引视图和分区的最佳集合。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-104">You can use the Database Engine Tuning Advisor to select and create an optimal set of indexes, indexed views, or table partitions without having an expert understanding of the database structure or the internals of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e2c2c-105">使用 DTA，您可以执行以下任务。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-105">Using the DTA, you can perform the following tasks.</span></span>  
  
-   <span data-ttu-id="e2c2c-106">特定问题查询故障排除</span><span class="sxs-lookup"><span data-stu-id="e2c2c-106">Troubleshoot the performance of a specific problem query</span></span>  
  
-   <span data-ttu-id="e2c2c-107">优化跨一个或多个数据库的大型查询集</span><span class="sxs-lookup"><span data-stu-id="e2c2c-107">Tune a large set of queries across one or more databases</span></span>  
  
-   <span data-ttu-id="e2c2c-108">执行潜在物理设计更改的探索性“假设”分析</span><span class="sxs-lookup"><span data-stu-id="e2c2c-108">Perform an exploratory what-if analysis of potential physical design changes</span></span>  
  
-   <span data-ttu-id="e2c2c-109">管理存储空间</span><span class="sxs-lookup"><span data-stu-id="e2c2c-109">Manage storage space</span></span>  
  
## <a name="database-engine-tuning-advisor-benefits"></a><span data-ttu-id="e2c2c-110">数据库引擎优化顾问优点</span><span class="sxs-lookup"><span data-stu-id="e2c2c-110">Database Engine Tuning Advisor Benefits</span></span>  
 <span data-ttu-id="e2c2c-111">在未完全了解数据库结构和针对数据库运行的查询的情况下，优化查询性能较为困难。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-111">Optimizing query performance can be difficult without a full understanding the database structure and the queries that are run against the database.</span></span> <span data-ttu-id="e2c2c-112">数据库引擎优化顾问可以简化此任务，也即，分析当前查询计划缓存，或分析您创建的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询的工作负荷并提出适当的物理设计建议。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-112">The Database Engine Tuning Advisor can make this task easier by analyzing the current query plan cache or by analyzing a workload of [!INCLUDE[tsql](../../includes/tsql-md.md)] queries that you create and recommending an appropriate physical design.</span></span> <span data-ttu-id="e2c2c-113">对于更高级的数据库管理员，DTA 公开一个强大机制，用于执行不同物理设计的探索性“假设”分析。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-113">For more advanced database administrators, DTA exposes a powerful mechanism to perform exploratory what-if analysis of different physical design alternatives.</span></span> <span data-ttu-id="e2c2c-114">DTA 可以提供下列信息。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-114">The DTA can provide the following information.</span></span>  
  
-   <span data-ttu-id="e2c2c-115">通过使用查询优化器分析工作负荷中的查询，推荐数据库的最佳索引组合。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-115">Recommend the best mix of indexes for databases by using the query optimizer to analyze queries in a workload.</span></span>  
  
-   <span data-ttu-id="e2c2c-116">为工作负荷中引用的数据库推荐对齐分区或非对齐分区。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-116">Recommend aligned or non-aligned partitions for databases referenced in a workload.</span></span>  
  
-   <span data-ttu-id="e2c2c-117">推荐工作负荷中引用的数据库的索引视图。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-117">Recommend indexed views for databases referenced in a workload.</span></span>  
  
-   <span data-ttu-id="e2c2c-118">分析所建议的更改将会产生的影响，包括索引的使用，查询在表之间的分布，以及查询在工作负荷中的性能。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-118">Analyze the effects of the proposed changes, including index usage, query distribution among tables, and query performance in the workload.</span></span>  
  
-   <span data-ttu-id="e2c2c-119">推荐为执行一个小型的问题查询集而对数据库进行优化的方法。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-119">Recommend ways to tune the database for a small set of problem queries.</span></span>  
  
-   <span data-ttu-id="e2c2c-120">允许通过指定磁盘空间约束等高级选项对推荐进行自定义。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-120">Allow you to customize the recommendation by specifying advanced options such as disk space constraints.</span></span>  
  
-   <span data-ttu-id="e2c2c-121">提供对所给工作负荷的建议执行效果的汇总报告。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-121">Provide reports that summarize the effects of implementing the recommendations for a given workload.</span></span>  
  
 <span data-ttu-id="e2c2c-122">数据库引擎优化顾问旨在处理以下查询工作负荷类型。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-122">The Database Engine Tuning Advisor is designed to handle the following types of query workloads.</span></span>  
  
-   <span data-ttu-id="e2c2c-123">仅联机事务处理 (OLTP) 查询</span><span class="sxs-lookup"><span data-stu-id="e2c2c-123">Online transaction processing (OLTP) queries only</span></span>  
  
-   <span data-ttu-id="e2c2c-124">仅联机分析处理 (OLAP) 查询</span><span class="sxs-lookup"><span data-stu-id="e2c2c-124">Online analytical processing (OLAP) queries only</span></span>  
  
-   <span data-ttu-id="e2c2c-125">OLTP 和 OLAP 混合查询</span><span class="sxs-lookup"><span data-stu-id="e2c2c-125">Mixed OLTP and OLAP queries</span></span>  
  
-   <span data-ttu-id="e2c2c-126">大量查询工作负荷（查询多于数据修改）</span><span class="sxs-lookup"><span data-stu-id="e2c2c-126">Query-heavy workloads (more queries than data modifications)</span></span>  
  
-   <span data-ttu-id="e2c2c-127">大量更新工作负荷（数据修改多于查询）</span><span class="sxs-lookup"><span data-stu-id="e2c2c-127">Update-heavy workloads (more data modifications than queries)</span></span>  
  
## <a name="dta-components-and-concepts"></a><span data-ttu-id="e2c2c-128">DTA 组件和概念</span><span class="sxs-lookup"><span data-stu-id="e2c2c-128">DTA Components and Concepts</span></span>  
 <span data-ttu-id="e2c2c-129">数据库引擎优化顾问图形用户界面</span><span class="sxs-lookup"><span data-stu-id="e2c2c-129">Database Engine Tuning Advisor Graphical User Interface</span></span>  
 <span data-ttu-id="e2c2c-130">一个易于使用的界面，可用来指定工作负荷和选择各种优化选项。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-130">An easy-to-use interface in which you can specify the workload and select various tuning options.</span></span>  
  
 <span data-ttu-id="e2c2c-131">**dta** 实用工具</span><span class="sxs-lookup"><span data-stu-id="e2c2c-131">**dta** Utility</span></span>  
 <span data-ttu-id="e2c2c-132">数据库引擎优化顾问的命令提示符版本。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-132">The command prompt version of Database Engine Tuning Advisor.</span></span> <span data-ttu-id="e2c2c-133">通过 **dta** 实用工具，您可以在应用程序和脚本中使用数据库引擎优化顾问功能。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-133">The **dta** utility is designed to allow you to use Database Engine Tuning Advisor functionality in applications and scripts.</span></span>  
  
 <span data-ttu-id="e2c2c-134">workload</span><span class="sxs-lookup"><span data-stu-id="e2c2c-134">workload</span></span>  
 <span data-ttu-id="e2c2c-135">Transact-SQL 脚本文件、跟踪文件或跟踪表，包含要优化的数据库的代表性工作负荷。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-135">A Transact-SQL script file, trace file, or trace table that contains a representative workload for the databases you want to tune.</span></span> <span data-ttu-id="e2c2c-136">从 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]开始，您可以指定计划缓存作为工作负荷。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-136">Beginning with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], you can specify the plan cache as the workload.</span></span>  
  
 <span data-ttu-id="e2c2c-137">XML 输入文件</span><span class="sxs-lookup"><span data-stu-id="e2c2c-137">XML input file</span></span>  
 <span data-ttu-id="e2c2c-138">数据库引擎优化顾问可用于优化工作负荷的 XML 格式文件。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-138">An XML-formatted file that Database Engine Tuning Advisor can use to tune workloads.</span></span> <span data-ttu-id="e2c2c-139">XML 输入文件支持在 GUI 或 **dta** 实用工具中不可用的高级优化选项。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-139">The XML input file supports advanced tuning options that are not available in either the GUI or **dta** utility.</span></span>  
  
## <a name="limitations-and-restrictions"></a><span data-ttu-id="e2c2c-140">限制和局限</span><span class="sxs-lookup"><span data-stu-id="e2c2c-140">Limitations and Restrictions</span></span>  
 <span data-ttu-id="e2c2c-141">数据库引擎优化顾问具有下列限制和局限性。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-141">The Database Engine Tuning Advisor has the following limitations and restrictions.</span></span>  
  
-   <span data-ttu-id="e2c2c-142">它不能添加或删除唯一索引或强制 PRIMARY KEY 或 UNIQUE 约束的索引。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-142">It cannot add or drop unique indexes or indexes that enforce PRIMARY KEY or UNIQUE constraints.</span></span>  
  
-   <span data-ttu-id="e2c2c-143">它无法分析设置为单用户模式的数据库。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-143">It cannot analyze a database that is set to single-user mode.</span></span>  
  
-   <span data-ttu-id="e2c2c-144">如果您为优化建议指定的最大磁盘空间超过了实际可用空间，数据库引擎优化顾问将使用指定的值。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-144">If you specify a maximum disk space for tuning recommendations that exceeds the actual available space, Database Engine Tuning Advisor uses the value you specify.</span></span> <span data-ttu-id="e2c2c-145">但是，当您执行建议脚本来实施它时，如果未先添加更多磁盘空间，则脚本会失败。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-145">However, when you execute the recommendation script to implement it, the script may fail if more disk space is not added first.</span></span> <span data-ttu-id="e2c2c-146">可以使用 **dta** 实用工具的 **-B** 选项指定最大磁盘空间，也可以通过在“高级优化选项”对话框中输入值来指定最大磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-146">Maximum disk space can be specified with the **-B** option of the **dta** utility, or by entering a value in the **Advanced Tuning Options** dialog box.</span></span>  
  
-   <span data-ttu-id="e2c2c-147">为了安全起见，数据库引擎优化顾问不能优化驻留在远程服务器上的跟踪表中的工作负荷。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-147">For security reasons, Database Engine Tuning Advisor cannot tune a workload in a trace table that resides on a remote server.</span></span> <span data-ttu-id="e2c2c-148">若要消除此限制，可以使用跟踪文件替代跟踪表，或将跟踪表复制到远程服务器。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-148">To work around this limitation, you can use a trace file instead of a trace table or copy the trace table to the remote server.</span></span>  
  
-   <span data-ttu-id="e2c2c-149">当强制实施约束时，例如为优化建议指定最大磁盘空间时强制的约束（通过使用 **-B** 选项或“高级优化选项”对话框），数据库引擎优化顾问可能会被迫删除某些现有的索引。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-149">When you impose constraints, such as those imposed when you specify a maximum disk space for tuning recommendations (by using the **-B** option or the **Advanced Tuning Options** dialog box), Database Engine Tuning Advisor may be forced to drop certain existing indexes.</span></span> <span data-ttu-id="e2c2c-150">在此情况下，生成的数据库引擎优化顾问建议可能生成负的预期提高值。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-150">In this case, the resulting Database Engine Tuning Advisor recommendation may produce a negative expected improvement.</span></span>  
  
-   <span data-ttu-id="e2c2c-151">指定限制优化时间的约束时（通过使用 **dta** 实用工具的 **-A** 选项或通过选择“优化选项”选项卡上的“限制优化时间”），数据库引擎优化顾问可能超过该时间限制，以便针对到当时为止已处理的工作负荷，生成精确预期的提高值和分析报告。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-151">When you specify a constraint to limit tuning time (by using the **-A** option with the **dta** utility or by checking **Limit tuning time** on the **Tuning Options** tab), Database Engine Tuning Advisor may exceed that time limit to produce an accurate expected improvement and the analysis reports for whatever portion of the workload has been consumed so far.</span></span>  
  
-   <span data-ttu-id="e2c2c-152">数据库引擎优化顾问可能在下列情况下不提供建议：</span><span class="sxs-lookup"><span data-stu-id="e2c2c-152">Database Engine Tuning Advisor might not make recommendations under the following circumstances:</span></span>  
  
    1.  <span data-ttu-id="e2c2c-153">正在优化的表所包含的数据页数少于 10。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-153">The table being tuned contains less than 10 data pages.</span></span>  
  
    2.  <span data-ttu-id="e2c2c-154">建议的索引对当前物理数据库设计的查询性能预计带来的提高值不够。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-154">The recommended indexes would not offer enough improvement in query performance over the current physical database design.</span></span>  
  
    3.  <span data-ttu-id="e2c2c-155">运行数据库引擎优化顾问的用户不是 `db_owner` 数据库角色或 `sysadmin` 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-155">The user who runs Database Engine Tuning Advisor is not a member of the `db_owner` database role or the `sysadmin` fixed server role.</span></span> <span data-ttu-id="e2c2c-156">工作负荷中的查询在运行数据库引擎优化顾问的用户的安全上下文中进行分析。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-156">The queries in the workload are analyzed in the security context of the user who runs the Database Engine Tuning Advisor.</span></span> <span data-ttu-id="e2c2c-157">用户必须是 `db_owner` 数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-157">The user must be a member of the `db_owner` database role.</span></span>  
  
-   <span data-ttu-id="e2c2c-158">数据库引擎优化顾问将优化会话数据和其他信息存储在 `msdb` 数据库中。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-158">Database Engine Tuning Advisor stores tuning session data and other information in the `msdb` database.</span></span> <span data-ttu-id="e2c2c-159">如果对 `msdb` 数据库进行了更改，可能会有丢失优化会话数据的风险。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-159">If changes are made to the `msdb` database you may risk losing tuning session data.</span></span> <span data-ttu-id="e2c2c-160">若要消除此风险，请对 `msdb` 数据库实施适当的备份策略。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-160">To eliminate this risk, implement an appropriate backup strategy for the `msdb` database.</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="e2c2c-161">性能注意事项</span><span class="sxs-lookup"><span data-stu-id="e2c2c-161">Performance Considerations</span></span>  
 <span data-ttu-id="e2c2c-162">在分析过程中，数据库引擎优化顾问可能占用相当多的处理器及内存资源。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-162">Database Engine Tuning Advisor can consume significant processor and memory resources during analysis.</span></span> <span data-ttu-id="e2c2c-163">若要避免降低生产服务器速度，请采用下列策略之一：</span><span class="sxs-lookup"><span data-stu-id="e2c2c-163">To avoid slowing down your production server, follow one of these strategies:</span></span>  
  
-   <span data-ttu-id="e2c2c-164">在服务器空闲时优化数据库。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-164">Tune your databases when your server is free.</span></span> <span data-ttu-id="e2c2c-165">数据库引擎优化顾问可能影响维护任务性能。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-165">Database Engine Tuning Advisor can affect maintenance task performance.</span></span>  
  
-   <span data-ttu-id="e2c2c-166">使用测试服务器/生产服务器功能。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-166">Use the test server/production server feature.</span></span> <span data-ttu-id="e2c2c-167">有关详细信息，请参阅  [减轻生产服务器优化负荷](reduce-the-production-server-tuning-load.md)。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-167">For more information, see  [Reduce the Production Server Tuning Load](reduce-the-production-server-tuning-load.md).</span></span>  
  
-   <span data-ttu-id="e2c2c-168">指定数据库引擎优化顾问仅分析物理数据库设计结构。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-168">Specify only the physical database design structures you want Database Engine Tuning Advisor to analyze.</span></span> <span data-ttu-id="e2c2c-169">数据库引擎优化顾问提供许多选项，但是请仅指定所需选项。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-169">Database Engine Tuning Advisor provides many options, but specifies only those that are necessary.</span></span>  
  
## <a name="dependency-on-xp_msver-extended-stored-procedure"></a><span data-ttu-id="e2c2c-170">与 xp_msver 扩展存储过程的依赖关系</span><span class="sxs-lookup"><span data-stu-id="e2c2c-170">Dependency on xp_msver Extended Stored Procedure</span></span>  
 <span data-ttu-id="e2c2c-171">数据库引擎优化顾问需要依赖 **xp_msver** 扩展存储过程才能提供全部功能。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-171">Database Engine Tuning Advisor depends on the **xp_msver** extended stored procedure to provide full functionality.</span></span> <span data-ttu-id="e2c2c-172">该扩展存储过程默认是打开的。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-172">This extended stored procedure is turned on by default.</span></span> <span data-ttu-id="e2c2c-173">数据库引擎优化顾问使用该扩展存储过程，提取要优化的数据库所在计算机中的处理器数以及可用内存数。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-173">Database Engine Tuning Advisor uses this extended stored procedure to fetch the number of processors and available memory on the computer where the database that you are tuning resides.</span></span> <span data-ttu-id="e2c2c-174">如果 **xp_msver** 不可用，则数据库引擎优化顾问将假定正在运行数据库引擎优化顾问的计算机的硬件特征。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-174">If **xp_msver** is unavailable, Database Engine Tuning Advisor assumes the hardware characteristics of the computer where Database Engine Tuning Advisor is running.</span></span> <span data-ttu-id="e2c2c-175">如果无法获得运行数据库引擎优化顾问的计算机的硬件特征，则假设该计算机有一个处理器和 1024 MB 内存。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-175">If the hardware characteristics of the computer where Database Engine Tuning Advisor is running are not available, one processor and 1024 megabytes (MBs) of memory are assumed.</span></span>  
  
 <span data-ttu-id="e2c2c-176">该依赖关系会影响分区建议，因为推荐的分区数取决于这两个值（处理器数和可用内存）。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-176">This dependency affects partitioning recommendations because the number of partitions recommended depends on these two values (number of processors and available memory).</span></span> <span data-ttu-id="e2c2c-177">如果您使用测试服务器来优化您的生产服务器，该依赖关系还会影响优化结果。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-177">The dependency also affects your tuning results when you use a test server to tune your production server.</span></span> <span data-ttu-id="e2c2c-178">在该方案中，数据库引擎优化顾问使用 **xp_msver** 来提取生产服务器的硬件特征。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-178">In this scenario, Database Engine Tuning Advisor uses **xp_msver** to fetch hardware properties from the production server.</span></span> <span data-ttu-id="e2c2c-179">在测试服务器上的工作负荷优化之后，数据库引擎优化顾问将使用这些硬件属性来生成建议。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-179">After tuning the workload on the test server, Database Engine Tuning Advisor uses these hardware properties to generate a recommendation.</span></span> <span data-ttu-id="e2c2c-180">有关详细信息，请参阅 [xp_msver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/xp-msver-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-180">For more information, see [xp_msver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/xp-msver-transact-sql).</span></span>  
  
## <a name="database-engine-tuning-advisor-tasks"></a><span data-ttu-id="e2c2c-181">数据库引擎优化顾问任务</span><span class="sxs-lookup"><span data-stu-id="e2c2c-181">Database Engine Tuning Advisor Tasks</span></span>  
 <span data-ttu-id="e2c2c-182">下表列出了常见的数据库引擎优化顾问任务以及描述如何执行这些任务的主题。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-182">The following table lists common Database Engine Tuning Advisor tasks and the topics that describe how to perform them.</span></span>  
  
|<span data-ttu-id="e2c2c-183">数据库引擎优化顾问任务</span><span class="sxs-lookup"><span data-stu-id="e2c2c-183">Database Engine Tuning Advisor Task</span></span>|<span data-ttu-id="e2c2c-184">主题</span><span class="sxs-lookup"><span data-stu-id="e2c2c-184">Topic</span></span>|  
|-----------------------------------------|-----------|  
|<span data-ttu-id="e2c2c-185">初始化并启动数据库引擎优化顾问。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-185">Initialize and start the Database Engine Tuning Advisor.</span></span><br /><br /> <span data-ttu-id="e2c2c-186">通过指定计划缓存、创建脚本或生成跟踪文件或跟踪表来创建工作负荷。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-186">Create a workload by specifying the plan cache, by creating a script, or by generating a trace file or trace table.</span></span><br /><br /> <span data-ttu-id="e2c2c-187">通过使用数据库引擎优化顾问图形用户界面工具来优化数据库。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-187">Tune a database by using the Database Engine Tuning Advisor graphical user interface tool.</span></span><br /><br /> <span data-ttu-id="e2c2c-188">创建 XML 输入文件以优化工作负荷。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-188">Create XML input files to tune workloads.</span></span><br /><br /> <span data-ttu-id="e2c2c-189">查看数据库引擎优化顾问用户界面选项的描述。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-189">View descriptions of the Database Engine Tuning Advisor user interface options.</span></span>|[<span data-ttu-id="e2c2c-190">启动并使用数据库引擎优化顾问</span><span class="sxs-lookup"><span data-stu-id="e2c2c-190">Start and Use the Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/database-engine-tuning-advisor.md)|  
|<span data-ttu-id="e2c2c-191">查看数据库优化操作的结果。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-191">View the results of the database tuning operation.</span></span><br /><br /> <span data-ttu-id="e2c2c-192">选择并实施优化建议。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-192">Select and implement tuning recommendations.</span></span><br /><br /> <span data-ttu-id="e2c2c-193">针对工作负荷执行“假设”探索性分析。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-193">Perform what-if exploratory analysis against the workload.</span></span><br /><br /> <span data-ttu-id="e2c2c-194">检查现有优化会话，基于现有会话克隆会话</span><span class="sxs-lookup"><span data-stu-id="e2c2c-194">Review existing tuning sessions, clone sessions based on existing ones</span></span> <br /><span data-ttu-id="e2c2c-195">或编辑现有优化建议，以进一步计算和实施。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-195">or edit existing tuning recommendations for further evaluation or implementation.</span></span><br /><br /> <span data-ttu-id="e2c2c-196">查看数据库引擎优化顾问用户界面选项的描述。</span><span class="sxs-lookup"><span data-stu-id="e2c2c-196">View descriptions of the Database Engine Tuning Advisor user interface options.</span></span>|[<span data-ttu-id="e2c2c-197">查看和使用数据库引擎优化顾问的输出</span><span class="sxs-lookup"><span data-stu-id="e2c2c-197">View and Work with the Output from the Database Engine Tuning Advisor</span></span>](view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md)|  
  
  
