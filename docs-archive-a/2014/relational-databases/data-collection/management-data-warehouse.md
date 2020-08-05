---
title: 管理数据仓库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collector [SQL Server], management data warehouse
- data warehouse
- management data warehouse
ms.assetid: 9874a8b2-7ccd-494a-944c-ad33b30b5499
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 96eb26c3e273832aead4aa0421304df17dc5b8ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580296"
---
# <a name="management-data-warehouse"></a><span data-ttu-id="eaf34-102">管理数据仓库</span><span class="sxs-lookup"><span data-stu-id="eaf34-102">Management Data Warehouse</span></span>
  <span data-ttu-id="eaf34-103">管理数据仓库是一种关系数据库，其中包含从身为数据收集目标的服务器收集来的数据。</span><span class="sxs-lookup"><span data-stu-id="eaf34-103">The management data warehouse is a relational database that contains the data that is collected from a server that is a data collection target.</span></span> <span data-ttu-id="eaf34-104">此数据用于生成系统数据收集组的报表，而且还可用于创建自定义报表。</span><span class="sxs-lookup"><span data-stu-id="eaf34-104">This data is used to generate the reports for the System Data collection sets, and can also be used to create custom reports.</span></span>  
  
 <span data-ttu-id="eaf34-105">数据收集器基础结构定义了实现保留策略所需的作业和维护计划，而保留策略是由数据库管理员定义的。</span><span class="sxs-lookup"><span data-stu-id="eaf34-105">The data collector infrastructure defines the jobs and maintenance plans that are needed to implement the retention policies defined by the database administrator.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="eaf34-106">对于此版本的数据收集器，将使用简单恢复模式创建管理数据仓库以最小化日志记录。</span><span class="sxs-lookup"><span data-stu-id="eaf34-106">For this release of the data collector, the management data warehouse is created using the Simple recovery model, to minimize logging.</span></span> <span data-ttu-id="eaf34-107">您应当为自己的组织采取适当的恢复模式。</span><span class="sxs-lookup"><span data-stu-id="eaf34-107">You should implement the appropriate recovery model for your organization.</span></span>  
  
## <a name="deploying-and-using-the-data-warehouse"></a><span data-ttu-id="eaf34-108">部署和使用数据仓库</span><span class="sxs-lookup"><span data-stu-id="eaf34-108">Deploying and Using the Data Warehouse</span></span>  
 <span data-ttu-id="eaf34-109">可以将管理数据仓库安装到运行数据收集器的同一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上。</span><span class="sxs-lookup"><span data-stu-id="eaf34-109">You can install the management data warehouse on the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that runs the data collector.</span></span> <span data-ttu-id="eaf34-110">但是，如果在所监视的服务器上存在服务器资源或性能问题，则可以在另一台计算机上安装管理数据仓库。</span><span class="sxs-lookup"><span data-stu-id="eaf34-110">However, if server resources or performance is an issue on the server being monitored, you can install the management data warehouse on a different computer.</span></span>  
  
 <span data-ttu-id="eaf34-111">当您创建管理数据仓库时，将创建预定义系统收集组所需的架构及其对象。</span><span class="sxs-lookup"><span data-stu-id="eaf34-111">The required schemas and their objects for the predefined system collection sets are created when you create the management data warehouse.</span></span> <span data-ttu-id="eaf34-112">创建的架构包括核心架构和快照架构，当创建用户定义的收集组并且该收集组包含使用一般 T-SQL 查询收集器类型的收集项时，将创建第三个架构 custom_snapshots。</span><span class="sxs-lookup"><span data-stu-id="eaf34-112">The schemas that are created are core and snapshots.A third schema, custom_snapshots, is created when user-defined collection sets are created that include collection items that use the Generic T-SQL Query collector type.</span></span>  
  
###### <a name="core-schema"></a><span data-ttu-id="eaf34-113">核心架构</span><span class="sxs-lookup"><span data-stu-id="eaf34-113">Core schema</span></span>  
 <span data-ttu-id="eaf34-114">核心架构描述用于组织和标识所收集数据的表、存储过程和视图。</span><span class="sxs-lookup"><span data-stu-id="eaf34-114">The core schema describes the tables, stored procedures, and views that are used to organize and to identify collected data.</span></span> <span data-ttu-id="eaf34-115">这些表将由为各个收集器类型创建的所有数据表共享。</span><span class="sxs-lookup"><span data-stu-id="eaf34-115">These tables are shared among all the data tables created for individual collector types.</span></span> <span data-ttu-id="eaf34-116">此架构已锁定，只有管理数据仓库数据库的所有者才可以修改。</span><span class="sxs-lookup"><span data-stu-id="eaf34-116">This schema is locked and can only be modified by the owner of the management data warehouse database.</span></span> <span data-ttu-id="eaf34-117">此架构中的表的名称均包含前缀“core”。</span><span class="sxs-lookup"><span data-stu-id="eaf34-117">The names of the tables in this schema are prefixed by "core".</span></span>  
  
 <span data-ttu-id="eaf34-118">下表介绍了核心架构中的数据库表。</span><span class="sxs-lookup"><span data-stu-id="eaf34-118">The following table describes the database tables in the core schema.</span></span> <span data-ttu-id="eaf34-119">这些数据库表使得数据收集器可以跟踪数据来自何处、谁插入的数据以及数据是什么时候上载至数据仓库的。</span><span class="sxs-lookup"><span data-stu-id="eaf34-119">These database tables enable the data collector to track where the data came from, who inserted it, and when it was uploaded to the data warehouse.</span></span>  
  
|<span data-ttu-id="eaf34-120">表名称</span><span class="sxs-lookup"><span data-stu-id="eaf34-120">Table name</span></span>|<span data-ttu-id="eaf34-121">说明</span><span class="sxs-lookup"><span data-stu-id="eaf34-121">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="eaf34-122">core.performance_counter_report_group_items</span><span class="sxs-lookup"><span data-stu-id="eaf34-122">core.performance_counter_report_group_items</span></span>|<span data-ttu-id="eaf34-123">存储有关管理数据仓库报表应如何对性能计数器进行分组和聚合的信息。</span><span class="sxs-lookup"><span data-stu-id="eaf34-123">Stores information about how the management data warehouse reports should group and aggregate performance counters.</span></span>|  
|<span data-ttu-id="eaf34-124">core.snapshots_internal</span><span class="sxs-lookup"><span data-stu-id="eaf34-124">core.snapshots_internal</span></span>|<span data-ttu-id="eaf34-125">标识每个新快照。</span><span class="sxs-lookup"><span data-stu-id="eaf34-125">Identifies each new snapshot.</span></span> <span data-ttu-id="eaf34-126">只要上载包开始上载一批新数据，此表中即会插入新的一行。</span><span class="sxs-lookup"><span data-stu-id="eaf34-126">A new row is inserted into this table whenever an upload package starts uploading a new batch of data.</span></span>|  
|<span data-ttu-id="eaf34-127">core.snapshot_timetable_internal</span><span class="sxs-lookup"><span data-stu-id="eaf34-127">core.snapshot_timetable_internal</span></span>|<span data-ttu-id="eaf34-128">存储有关快照时间的信息。</span><span class="sxs-lookup"><span data-stu-id="eaf34-128">Stores information about the snapshot times.</span></span> <span data-ttu-id="eaf34-129">快照时间将存储在单独的表中，因为几乎在同一时间可产生多个快照。</span><span class="sxs-lookup"><span data-stu-id="eaf34-129">The snapshot time is stored in a separate table because many snapshots can happen at nearly the same time.</span></span>|  
|<span data-ttu-id="eaf34-130">core.source.info_internal</span><span class="sxs-lookup"><span data-stu-id="eaf34-130">core.source.info_internal</span></span>|<span data-ttu-id="eaf34-131">此表存储关于数据源的信息。</span><span class="sxs-lookup"><span data-stu-id="eaf34-131">This table stores information about the data source.</span></span> <span data-ttu-id="eaf34-132">只要新收集组开始向数据仓库上载数据，此表即会更新。</span><span class="sxs-lookup"><span data-stu-id="eaf34-132">This table is updated whenever a new collection set starts uploading data to the data warehouse.</span></span>|  
|<span data-ttu-id="eaf34-133">core.supported_collector_types_internal</span><span class="sxs-lookup"><span data-stu-id="eaf34-133">core.supported_collector_types_internal</span></span>|<span data-ttu-id="eaf34-134">包含可将数据上载到管理数据仓库的已注册收集器类型的 ID。</span><span class="sxs-lookup"><span data-stu-id="eaf34-134">Contains the IDs of registered collector types that can upload data to the management data warehouse.</span></span> <span data-ttu-id="eaf34-135">只有在更新仓库架构以支持新的收集器类型后，此表才会更新。</span><span class="sxs-lookup"><span data-stu-id="eaf34-135">This table is only updated when the schema of the warehouse is updated to support a new collector type.</span></span> <span data-ttu-id="eaf34-136">创建管理数据仓库时，将使用由数据收集器提供的收集器类型 ID 填充此表。</span><span class="sxs-lookup"><span data-stu-id="eaf34-136">When the management data warehouse is created, this table is populated with the IDs of the collector types provided by the data collector.</span></span>|  
|<span data-ttu-id="eaf34-137">core.wait_categories</span><span class="sxs-lookup"><span data-stu-id="eaf34-137">core.wait_categories</span></span>|<span data-ttu-id="eaf34-138">包含用于根据 wait_type 特征对等待类型分组的类别。</span><span class="sxs-lookup"><span data-stu-id="eaf34-138">Contains the categories used to group wait types according to wait_type characteristic.</span></span>|  
|<span data-ttu-id="eaf34-139">core.wait_types</span><span class="sxs-lookup"><span data-stu-id="eaf34-139">core.wait_types</span></span>|<span data-ttu-id="eaf34-140">包含数据收集器识别的等待类型。</span><span class="sxs-lookup"><span data-stu-id="eaf34-140">Contains the wait types recognized by the data collector.</span></span>|  
|<span data-ttu-id="eaf34-141">core.purge_info_internal</span><span class="sxs-lookup"><span data-stu-id="eaf34-141">core.purge_info_internal</span></span>|<span data-ttu-id="eaf34-142">指示已请求停止从管理数据仓库中删除数据。</span><span class="sxs-lookup"><span data-stu-id="eaf34-142">Indicates that a request has been made to stop the removal of data from the management data warehouse.</span></span>|  
  
 <span data-ttu-id="eaf34-143">上述表与收集器类型表一起使用，用于存储信息。</span><span class="sxs-lookup"><span data-stu-id="eaf34-143">The preceding tables are used with collector type tables to store information.</span></span> <span data-ttu-id="eaf34-144">例如，一般 SQL 跟踪收集器类型使用下列表存储跟踪数据：</span><span class="sxs-lookup"><span data-stu-id="eaf34-144">For example, the Generic SQL Trace collector type uses the following tables to store trace data:</span></span>  
  
-   <span data-ttu-id="eaf34-145">core.source_info_internal</span><span class="sxs-lookup"><span data-stu-id="eaf34-145">core.source_info_internal</span></span>  
  
-   <span data-ttu-id="eaf34-146">core.snapshots_internal</span><span class="sxs-lookup"><span data-stu-id="eaf34-146">core.snapshots_internal</span></span>  
  
-   <span data-ttu-id="eaf34-147">snapshots.trace_info</span><span class="sxs-lookup"><span data-stu-id="eaf34-147">snapshots.trace_info</span></span>  
  
-   <span data-ttu-id="eaf34-148">snapshots.trace_data</span><span class="sxs-lookup"><span data-stu-id="eaf34-148">snapshots.trace_data</span></span>  
  
###### <a name="snapshots-schema"></a><span data-ttu-id="eaf34-149">快照架构</span><span class="sxs-lookup"><span data-stu-id="eaf34-149">Snapshots schema</span></span>  
 <span data-ttu-id="eaf34-150">此快照架构描述了存储和维护由所提供的收集器类型收集的数据所需的对象。</span><span class="sxs-lookup"><span data-stu-id="eaf34-150">The snapshots schema describes the objects needed to store and maintain the data collected by the collector types that are provided.</span></span> <span data-ttu-id="eaf34-151">此架构中的表已固定，在收集器类型的生存期内无需更改。</span><span class="sxs-lookup"><span data-stu-id="eaf34-151">The tables in this schema are fixed and do not need to be changed during the lifetime of the collector type.</span></span> <span data-ttu-id="eaf34-152">如需更改，则此架构仅可由 mdw_admin 角色的成员进行更改。</span><span class="sxs-lookup"><span data-stu-id="eaf34-152">If changes are needed, the schema can only be changed by members of the mdw_admin role.</span></span> <span data-ttu-id="eaf34-153">这些表是为了存储由系统数据收集组收集的数据而创建。</span><span class="sxs-lookup"><span data-stu-id="eaf34-153">These tables are created to store the data collected by the System Data collection sets.</span></span>  
  
 <span data-ttu-id="eaf34-154">下表说明了“服务器活动”和“查询统计”收集组所需的管理数据仓库架构部分。</span><span class="sxs-lookup"><span data-stu-id="eaf34-154">The following tables illustrate a portion of the management data warehouse schema that is required for the Server Activity and Query Statistics collection sets.</span></span>  
  
-   <span data-ttu-id="eaf34-155">系统级资源表</span><span class="sxs-lookup"><span data-stu-id="eaf34-155">System-level resource tables</span></span>  
  
    -   <span data-ttu-id="eaf34-156">**snapshots.os_wait_stats**</span><span class="sxs-lookup"><span data-stu-id="eaf34-156">**snapshots.os_wait_stats**</span></span>  
  
    -   <span data-ttu-id="eaf34-157">**snapshots.os_latch_stats**</span><span class="sxs-lookup"><span data-stu-id="eaf34-157">**snapshots.os_latch_stats**</span></span>  
  
    -   <span data-ttu-id="eaf34-158">**snapshots.os_schedulers**</span><span class="sxs-lookup"><span data-stu-id="eaf34-158">**snapshots.os_schedulers**</span></span>  
  
    -   `snapshots.os_memory_clerks`  
  
    -   <span data-ttu-id="eaf34-159">**snapshots.os_memory_nodes**</span><span class="sxs-lookup"><span data-stu-id="eaf34-159">**snapshots.os_memory_nodes**</span></span>  
  
    -   <span data-ttu-id="eaf34-160">snapshots.sql_process_and_system_memory</span><span class="sxs-lookup"><span data-stu-id="eaf34-160">snapshots.sql_process_and_system_memory</span></span>  
  
-   <span data-ttu-id="eaf34-161">系统活动</span><span class="sxs-lookup"><span data-stu-id="eaf34-161">System activity</span></span>  
  
    -   <span data-ttu-id="eaf34-162">snapshots.active_sessions_and_requests</span><span class="sxs-lookup"><span data-stu-id="eaf34-162">snapshots.active_sessions_and_requests</span></span>  
  
-   <span data-ttu-id="eaf34-163">查询统计信息</span><span class="sxs-lookup"><span data-stu-id="eaf34-163">Query statistics</span></span>  
  
    -   <span data-ttu-id="eaf34-164">snapshots.query_stats</span><span class="sxs-lookup"><span data-stu-id="eaf34-164">snapshots.query_stats</span></span>  
  
-   <span data-ttu-id="eaf34-165">I/O 统计信息</span><span class="sxs-lookup"><span data-stu-id="eaf34-165">I/O statistics</span></span>  
  
    -   `snapshots.io_virtual_file_stats`  
  
-   <span data-ttu-id="eaf34-166">查询文本和计划</span><span class="sxs-lookup"><span data-stu-id="eaf34-166">Query text and plan</span></span>  
  
    -   <span data-ttu-id="eaf34-167">snapshots.notable_query_text</span><span class="sxs-lookup"><span data-stu-id="eaf34-167">snapshots.notable_query_text</span></span>  
  
    -   <span data-ttu-id="eaf34-168">snapshots.notable_query_plan</span><span class="sxs-lookup"><span data-stu-id="eaf34-168">snapshots.notable_query_plan</span></span>  
  
-   <span data-ttu-id="eaf34-169">规范化的查询统计信息</span><span class="sxs-lookup"><span data-stu-id="eaf34-169">Normalized query statistics</span></span>  
  
    -   <span data-ttu-id="eaf34-170">snapshots.distinct_queries</span><span class="sxs-lookup"><span data-stu-id="eaf34-170">snapshots.distinct_queries</span></span>  
  
    -   <span data-ttu-id="eaf34-171">snapshots.distinct_query_to_handle</span><span class="sxs-lookup"><span data-stu-id="eaf34-171">snapshots.distinct_query_to_handle</span></span>  
  
 <span data-ttu-id="eaf34-172">**Custom_snapshots 架构**</span><span class="sxs-lookup"><span data-stu-id="eaf34-172">**Custom_snapshots schema**</span></span>  
  
 <span data-ttu-id="eaf34-173">custom_snapshots 架构描述当标准或第三方收集器类型用于创建用户定义的收集组时所创建的新表和新视图。</span><span class="sxs-lookup"><span data-stu-id="eaf34-173">The custom_snapshots schema describes new tables and views that are created when standard or third-party collector types are used to create user-defined collection sets.</span></span> <span data-ttu-id="eaf34-174">所有要求为收集项提供新数据表的收集器类型都可在此架构中创建该表。</span><span class="sxs-lookup"><span data-stu-id="eaf34-174">Any collector type that requires a new data table for a collection item can create that table in this schema.</span></span> <span data-ttu-id="eaf34-175">在此架构中，可由 mdw_writer 角色的成员添加新表。</span><span class="sxs-lookup"><span data-stu-id="eaf34-175">New tables can be added in this schema by members of the mdw_writer role.</span></span> <span data-ttu-id="eaf34-176">对此架构的任何其他更改仅可由 mdw_admin 角色的成员执行。</span><span class="sxs-lookup"><span data-stu-id="eaf34-176">Any other changes to the schema can only be made by members of the mdw_admin role.</span></span>  
  
 <span data-ttu-id="eaf34-177">通过阅读有关各表相应的数据收集器存储过程的文档，您可获得有关数据库表列的数据类型和内容的详细信息。</span><span class="sxs-lookup"><span data-stu-id="eaf34-177">You can get detailed data type and content information for the database table columns by reading the documentation for the appropriate data collector stored procedure for each of the tables.</span></span>  
  
### <a name="best-practices"></a><span data-ttu-id="eaf34-178">最佳实践</span><span class="sxs-lookup"><span data-stu-id="eaf34-178">Best Practices</span></span>  
 <span data-ttu-id="eaf34-179">使用管理数据仓库时，建议遵循以下最佳做法：</span><span class="sxs-lookup"><span data-stu-id="eaf34-179">When working with the management data warehouse, we recommend following these best practices:</span></span>  
  
-   <span data-ttu-id="eaf34-180">除非添加新的收集器类型，否则不要更改管理数据仓库表的元数据。</span><span class="sxs-lookup"><span data-stu-id="eaf34-180">Do not modify the metadata of management data warehouse tables unless you are adding a new collector type.</span></span>  
  
-   <span data-ttu-id="eaf34-181">不要直接更改管理数据仓库中的数据。</span><span class="sxs-lookup"><span data-stu-id="eaf34-181">Do not directly modify the data in the management data warehouse.</span></span> <span data-ttu-id="eaf34-182">更改收集的数据将使所收集数据的合法性失效。</span><span class="sxs-lookup"><span data-stu-id="eaf34-182">Changing the data that you have collected invalidates the legitimacy of the collected data.</span></span>  
  
-   <span data-ttu-id="eaf34-183">不要直接使用表，而应使用随数据收集器提供的已记录的存储过程和函数来访问实例和应用程序数据。</span><span class="sxs-lookup"><span data-stu-id="eaf34-183">Instead of directly using the tables, use the documented stored procedures and functions that are provided with the data collector to access instance and application data.</span></span> <span data-ttu-id="eaf34-184">表名称和表定义可以更改，在您更新该应用程序时肯定会更改，在未来的版本中也可能更改。</span><span class="sxs-lookup"><span data-stu-id="eaf34-184">The table names and definitions can change, do change when you update the application, and might change in future releases.</span></span>  
  
## <a name="change-history"></a><span data-ttu-id="eaf34-185">更改历史记录</span><span class="sxs-lookup"><span data-stu-id="eaf34-185">Change History</span></span>  
  
|<span data-ttu-id="eaf34-186">更新的内容</span><span class="sxs-lookup"><span data-stu-id="eaf34-186">Updated content</span></span>|  
|---------------------|  
|<span data-ttu-id="eaf34-187">向“核心架构”部分增添了 core.performance_counter_report_group_items 表。</span><span class="sxs-lookup"><span data-stu-id="eaf34-187">Added the core.performance_counter_report_group_items table to the "Core schema" section.</span></span>|  
|<span data-ttu-id="eaf34-188">更新了“快照架构”部分中表的列表。</span><span class="sxs-lookup"><span data-stu-id="eaf34-188">Updated the list of tables in the "Snapshots schema" section.</span></span> <span data-ttu-id="eaf34-189">增加了 snapshots.os_memory_clerks、snapshots.sql_process_and_system_memory 和 snapshots.io_virtual_file_stats。</span><span class="sxs-lookup"><span data-stu-id="eaf34-189">Added snapshots.os_memory_clerks,snapshots.sql_process_and_system_memory, and snapshots.io_virtual_file_stats.</span></span> <span data-ttu-id="eaf34-190">删除了 snapshots.os_process_memory 和 snapshots.distinct_query_stats。</span><span class="sxs-lookup"><span data-stu-id="eaf34-190">Removedsnapshots.os_process_memory and snapshots.distinct_query_stats.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eaf34-191">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eaf34-191">See Also</span></span>  
 <span data-ttu-id="eaf34-192">[管理数据仓库存储过程 (Transact-SQL)](/sql/relational-databases/system-stored-procedures/management-data-warehouse-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eaf34-192">[Management Data Warehouse Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/management-data-warehouse-stored-procedures-transact-sql) </span></span>  
 <span data-ttu-id="eaf34-193">[数据收集器存储过程 (Transact-SQL)](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eaf34-193">[Data Collector Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql) </span></span>  
 <span data-ttu-id="eaf34-194">[数据收集](data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="eaf34-194">[Data Collection](data-collection.md) </span></span>  
 [<span data-ttu-id="eaf34-195">查看收集组报表 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="eaf34-195">View a Collection Set Report &#40;SQL Server Management Studio&#41;</span></span>](view-a-collection-set-report-sql-server-management-studio.md)  
  
  
