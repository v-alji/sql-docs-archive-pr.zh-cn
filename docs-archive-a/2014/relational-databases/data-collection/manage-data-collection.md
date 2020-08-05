---
title: 管理数据收集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collection [SQL Server]
- data collector [SQL Server], Transact-SQL
- data collector [SQL Server], SQL Server Management Studio
ms.assetid: bc137daa-9f37-4c01-9766-8b7350c75af8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0a7d88923bc41939541bedeed2d40908e454e9c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580298"
---
# <a name="manage-data-collection"></a><span data-ttu-id="4359f-102">管理数据收集</span><span class="sxs-lookup"><span data-stu-id="4359f-102">Manage Data Collection</span></span>
  <span data-ttu-id="4359f-103">可使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程和功能来管理数据收集的各个方面，例如启用或禁用数据收集、更改收集组配置或查看管理数据仓库中的数据。</span><span class="sxs-lookup"><span data-stu-id="4359f-103">You can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures and functions to manage different aspects of data collection, such as enabling or disabling data collection, changing a collection set configuration, or viewing data in the management data warehouse.</span></span>  
  
## <a name="manage-data-collection-by-using-sql-server-management-studio"></a><span data-ttu-id="4359f-104">使用 SQL Server Management Studio 管理数据收集</span><span class="sxs-lookup"><span data-stu-id="4359f-104">Manage Data Collection by Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="4359f-105">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的对象资源管理器可以执行以下与数据收集器相关的任务：</span><span class="sxs-lookup"><span data-stu-id="4359f-105">You can perform the following data collector-related tasks by using Object Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]:</span></span>  
  
-   [<span data-ttu-id="4359f-106">配置管理数据仓库 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="4359f-106">Configure the Management Data Warehouse &#40;SQL Server Management Studio&#41;</span></span>](configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="4359f-107">配置数据收集器的属性</span><span class="sxs-lookup"><span data-stu-id="4359f-107">Configure Properties of a Data Collector</span></span>](configure-properties-of-a-data-collector.md)  
  
-   [<span data-ttu-id="4359f-108">启用或禁用数据收集</span><span class="sxs-lookup"><span data-stu-id="4359f-108">Enable or Disable Data Collection</span></span>](data-collection.md)  
  
-   [<span data-ttu-id="4359f-109">启动或停止收集组</span><span class="sxs-lookup"><span data-stu-id="4359f-109">Start or Stop a Collection Set</span></span>](start-or-stop-a-collection-set.md)  
  
-   [<span data-ttu-id="4359f-110">使用 SQL Server Profiler 创建 SQL 跟踪收集组 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="4359f-110">Use SQL Server Profiler to Create a SQL Trace Collection Set &#40;SQL Server Management Studio&#41;</span></span>](use-sql-server-profiler-to-create-a-sql-trace-collection-set.md)  
  
-   [<span data-ttu-id="4359f-111">查看收集组日志 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="4359f-111">View Collection Set Logs &#40;SQL Server Management Studio&#41;</span></span>](view-collection-set-logs-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="4359f-112">查看或更改收集组计划 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="4359f-112">View or Change Collection Set Schedules &#40;SQL Server Management Studio&#41;</span></span>](view-or-change-collection-set-schedules-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="4359f-113">查看收集组报表 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="4359f-113">View a Collection Set Report &#40;SQL Server Management Studio&#41;</span></span>](view-a-collection-set-report-sql-server-management-studio.md)  
  
## <a name="manage-data-collection-by-using-transact-sql"></a><span data-ttu-id="4359f-114">使用 Transact-SQL 管理数据收集</span><span class="sxs-lookup"><span data-stu-id="4359f-114">Manage Data Collection by Using Transact-SQL</span></span>  
 <span data-ttu-id="4359f-115">数据收集器提供了一系列内容丰富的存储过程，这些过程可用于执行任何与数据收集器相关的任务。</span><span class="sxs-lookup"><span data-stu-id="4359f-115">The data collector provides an extensive collection of stored procedures that you can use to perform any data-collector related task.</span></span> <span data-ttu-id="4359f-116">例如，可使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="4359f-116">For example, by using [!INCLUDE[tsql](../../includes/tsql-md.md)], you can perform the following tasks:</span></span>  
  
-   [<span data-ttu-id="4359f-117">配置数据收集参数 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-117">Configure Data Collection Parameters &#40;Transact-SQL&#41;</span></span>](configure-data-collection-parameters-transact-sql.md)  
  
-   [<span data-ttu-id="4359f-118">启用或禁用数据收集</span><span class="sxs-lookup"><span data-stu-id="4359f-118">Enable or Disable Data Collection</span></span>](data-collection.md)  
  
-   [<span data-ttu-id="4359f-119">启动或停止收集组</span><span class="sxs-lookup"><span data-stu-id="4359f-119">Start or Stop a Collection Set</span></span>](start-or-stop-a-collection-set.md)  
  
-   [<span data-ttu-id="4359f-120">创建使用一般 T-SQL 查询收集器类型的自定义收集组 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-120">Create a Custom Collection Set That Uses the Generic T-SQL Query Collector Type &#40;Transact-SQL&#41;</span></span>](create-custom-collection-set-generic-t-sql-query-collector-type.md)  
  
-   [<span data-ttu-id="4359f-121">将收集项添加到收集组中 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-121">Add a Collection Item to a Collection Set &#40;Transact-SQL&#41;</span></span>](add-a-collection-item-to-a-collection-set-transact-sql.md)  
  
 <span data-ttu-id="4359f-122">另外，它还包括一些函数和视图，这些函数和视图可用来获取 msdb 数据库和管理数据仓库数据库的配置数据、执行日志数据和存储在管理数据仓库中的数据。</span><span class="sxs-lookup"><span data-stu-id="4359f-122">In addition, there are functions and views that you can use to get configuration data for the msdb and management data warehouse databases, execution log data, and data that is stored in the management data warehouse.</span></span>  
  
 <span data-ttu-id="4359f-123">您可使用提供的存储过程、函数和视图来创建自己的端到端数据收集方案。</span><span class="sxs-lookup"><span data-stu-id="4359f-123">You can use the stored procedures, functions, and views that are provided to create your own end-to-end data collection scenarios.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4359f-124">与常规存储过程不同的是，数据收集器存储过程使用严格类型化的参数，不支持自动的数据类型转换。</span><span class="sxs-lookup"><span data-stu-id="4359f-124">Unlike regular stored procedures, the data collector stored procedures use strictly typed parameters and do not support automatic data type conversion.</span></span> <span data-ttu-id="4359f-125">如果这些参数不是使用正确的输入参数数据类型（正如参数说明中指定的一样）调用的，则存储过程会返回错误。</span><span class="sxs-lookup"><span data-stu-id="4359f-125">If these parameters are not called with the correct input parameter data types, as specified in the argument description, the stored procedure returns an error.</span></span>  
  
 <span data-ttu-id="4359f-126">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 来创建和执行提供的代码示例。</span><span class="sxs-lookup"><span data-stu-id="4359f-126">You can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to create and execute the provided code samples.</span></span> <span data-ttu-id="4359f-127">有关详细信息，请参阅 [对象资源管理器](../../ssms/object/object-explorer.md)。</span><span class="sxs-lookup"><span data-stu-id="4359f-127">For more information, see [Object Explorer](../../ssms/object/object-explorer.md).</span></span> <span data-ttu-id="4359f-128">或者，您可在任何编辑器中创建查询并将其保存为文件扩展名为 .sql 的文本文件。</span><span class="sxs-lookup"><span data-stu-id="4359f-128">As an alternative you can create the query in any editor and save it in a text file that has a .sql file name extension.</span></span> <span data-ttu-id="4359f-129">您可以从 Windows 命令提示符处使用 `sqlcmd` 实用程序执行查询。</span><span class="sxs-lookup"><span data-stu-id="4359f-129">You can execute the query from the Windows command prompt using the `sqlcmd` utility.</span></span> <span data-ttu-id="4359f-130">有关详细信息，请参阅 [使用 sqlcmd 实用工具](../scripting/sqlcmd-use-the-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="4359f-130">For more information, see [Use the sqlcmd Utility](../scripting/sqlcmd-use-the-utility.md).</span></span>  
  
### <a name="stored-procedures-and-views"></a><span data-ttu-id="4359f-131">存储过程和视图</span><span class="sxs-lookup"><span data-stu-id="4359f-131">Stored Procedures and Views</span></span>  
 <span data-ttu-id="4359f-132">**使用数据收集器**</span><span class="sxs-lookup"><span data-stu-id="4359f-132">**Working with the data collector**</span></span>  
  
 <span data-ttu-id="4359f-133">下表介绍了使用数据收集器时可以使用的存储过程。</span><span class="sxs-lookup"><span data-stu-id="4359f-133">The following table describes the stored procedures that you can use to work with the data collector.</span></span>  
  
|<span data-ttu-id="4359f-134">过程名称</span><span class="sxs-lookup"><span data-stu-id="4359f-134">Procedure name</span></span>|<span data-ttu-id="4359f-135">说明</span><span class="sxs-lookup"><span data-stu-id="4359f-135">Description</span></span>|  
|--------------------|-----------------|  
|[<span data-ttu-id="4359f-136">sp_syscollector_enable_collector</span><span class="sxs-lookup"><span data-stu-id="4359f-136">sp_syscollector_enable_collector</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql)|<span data-ttu-id="4359f-137">启用数据收集器。</span><span class="sxs-lookup"><span data-stu-id="4359f-137">Enable the data collector.</span></span>|  
|[<span data-ttu-id="4359f-138">sp_syscollector_disable_collector</span><span class="sxs-lookup"><span data-stu-id="4359f-138">sp_syscollector_disable_collector</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql)|<span data-ttu-id="4359f-139">禁用数据收集器。</span><span class="sxs-lookup"><span data-stu-id="4359f-139">Disable the data collector.</span></span>|  
  
 <span data-ttu-id="4359f-140">**使用收集组**</span><span class="sxs-lookup"><span data-stu-id="4359f-140">**Working with collection sets**</span></span>  
  
 <span data-ttu-id="4359f-141">下表介绍了使用收集组时可以使用的存储过程。</span><span class="sxs-lookup"><span data-stu-id="4359f-141">The following table describes the stored procedures that you can use to work with collection sets.</span></span>  
  
|<span data-ttu-id="4359f-142">过程名称</span><span class="sxs-lookup"><span data-stu-id="4359f-142">Procedure name</span></span>|<span data-ttu-id="4359f-143">说明</span><span class="sxs-lookup"><span data-stu-id="4359f-143">Description</span></span>|  
|--------------------|-----------------|  
|[<span data-ttu-id="4359f-144">sp_syscollector_run_collection_set (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-144">sp_syscollector_run_collection_set &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-run-collection-set-transact-sql)|<span data-ttu-id="4359f-145">按需运行收集组。</span><span class="sxs-lookup"><span data-stu-id="4359f-145">Run a collection set on demand.</span></span>|  
|[<span data-ttu-id="4359f-146">sp_syscollector_start_collection_set (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-146">sp_syscollector_start_collection_set &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-start-collection-set-transact-sql)|<span data-ttu-id="4359f-147">启动收集组。</span><span class="sxs-lookup"><span data-stu-id="4359f-147">Start a collection set.</span></span>|  
|[<span data-ttu-id="4359f-148">sp_syscollector_stop_collection_set (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-148">sp_syscollector_stop_collection_set &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-stop-collection-set-transact-sql)|<span data-ttu-id="4359f-149">停止收集组。</span><span class="sxs-lookup"><span data-stu-id="4359f-149">Stop a collection set.</span></span>|  
|[<span data-ttu-id="4359f-150">sp_syscollector_create_collection_set (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-150">sp_syscollector_create_collection_set &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql)|<span data-ttu-id="4359f-151">创建收集组。</span><span class="sxs-lookup"><span data-stu-id="4359f-151">Create a collection set.</span></span>|  
|[<span data-ttu-id="4359f-152">sp_syscollector_delete_collection_set (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-152">sp_syscollector_delete_collection_set &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-delete-collection-set-transact-sql)|<span data-ttu-id="4359f-153">删除收集组。</span><span class="sxs-lookup"><span data-stu-id="4359f-153">Delete a collection set.</span></span>|  
|[<span data-ttu-id="4359f-154">sp_syscollector_update_collection_set (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-154">sp_syscollector_update_collection_set &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-update-collection-set-transact-sql)|<span data-ttu-id="4359f-155">更改收集组的配置</span><span class="sxs-lookup"><span data-stu-id="4359f-155">Change a collection set configuration.</span></span>|  
|[<span data-ttu-id="4359f-156">sp_syscollector_upload_collection_set (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-156">sp_syscollector_upload_collection_set &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-upload-collection-set-transact-sql)|<span data-ttu-id="4359f-157">将收集组数据上载到管理数据仓库。</span><span class="sxs-lookup"><span data-stu-id="4359f-157">Upload collection set data to the management data warehouse.</span></span> <span data-ttu-id="4359f-158">实际上，这是一种按需进行的上载。</span><span class="sxs-lookup"><span data-stu-id="4359f-158">This is effectively an on-demand upload.</span></span>|  
  
 <span data-ttu-id="4359f-159">**使用收集项**</span><span class="sxs-lookup"><span data-stu-id="4359f-159">**Working with collection items**</span></span>  
  
 <span data-ttu-id="4359f-160">下表介绍了使用收集项时可以使用的存储过程。</span><span class="sxs-lookup"><span data-stu-id="4359f-160">The following table describes the stored procedures that you can use to work with collection items.</span></span>  
  
|<span data-ttu-id="4359f-161">过程名称</span><span class="sxs-lookup"><span data-stu-id="4359f-161">Procedure name</span></span>|<span data-ttu-id="4359f-162">说明</span><span class="sxs-lookup"><span data-stu-id="4359f-162">Description</span></span>|  
|--------------------|-----------------|  
|[<span data-ttu-id="4359f-163">sp_syscollector_create_collection_item (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-163">sp_syscollector_create_collection_item &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-create-collection-item-transact-sql)|<span data-ttu-id="4359f-164">创建收集项。</span><span class="sxs-lookup"><span data-stu-id="4359f-164">Create a collection item.</span></span>|  
|[<span data-ttu-id="4359f-165">sp_syscollector_delete_collection_item (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-165">sp_syscollector_delete_collection_item &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-delete-collection-item-transact-sql)|<span data-ttu-id="4359f-166">删除收集项。</span><span class="sxs-lookup"><span data-stu-id="4359f-166">Delete a collection item.</span></span>|  
|[<span data-ttu-id="4359f-167">sp_syscollector_update_collection_item (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-167">sp_syscollector_update_collection_item &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-update-collection-item-transact-sql)|<span data-ttu-id="4359f-168">更新收集项。</span><span class="sxs-lookup"><span data-stu-id="4359f-168">Update a collection item.</span></span>|  
  
 <span data-ttu-id="4359f-169">**使用收集器类型**</span><span class="sxs-lookup"><span data-stu-id="4359f-169">**Working with collector types**</span></span>  
  
 <span data-ttu-id="4359f-170">下表介绍了使用收集器类型时可以使用的存储过程。</span><span class="sxs-lookup"><span data-stu-id="4359f-170">The following table describes the stored procedures that you can use to work with collector types.</span></span>  
  
|<span data-ttu-id="4359f-171">过程名称</span><span class="sxs-lookup"><span data-stu-id="4359f-171">Procedure name</span></span>|<span data-ttu-id="4359f-172">说明</span><span class="sxs-lookup"><span data-stu-id="4359f-172">Description</span></span>|  
|--------------------|-----------------|  
|[<span data-ttu-id="4359f-173">sp_syscollector_create_collector_type (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-173">sp_syscollector_create_collector_type &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-create-collector-type-transact-sql)|<span data-ttu-id="4359f-174">创建收集器类型。</span><span class="sxs-lookup"><span data-stu-id="4359f-174">Create a collector type.</span></span>|  
|[<span data-ttu-id="4359f-175">sp_syscollector_update_collector_type (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-175">sp_syscollector_update_collector_type &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-update-collector-type-transact-sql)|<span data-ttu-id="4359f-176">更新收集器类型。</span><span class="sxs-lookup"><span data-stu-id="4359f-176">Update a collector type.</span></span>|  
|[<span data-ttu-id="4359f-177">sp_syscollector_delete_collector_type (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-177">sp_syscollector_delete_collector_type &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-delete-collector-type-transact-sql)|<span data-ttu-id="4359f-178">删除收集器类型。</span><span class="sxs-lookup"><span data-stu-id="4359f-178">Delete a collector type.</span></span>|  
  
 <span data-ttu-id="4359f-179">**获取配置信息**</span><span class="sxs-lookup"><span data-stu-id="4359f-179">**Getting configuration information**</span></span>  
  
 <span data-ttu-id="4359f-180">下表介绍了可用于获取配置信息和执行日志数据的视图。</span><span class="sxs-lookup"><span data-stu-id="4359f-180">The following table describes the views that you can use for getting configuration information and execution log data.</span></span>  
  
|<span data-ttu-id="4359f-181">视图名称</span><span class="sxs-lookup"><span data-stu-id="4359f-181">View name</span></span>|<span data-ttu-id="4359f-182">说明</span><span class="sxs-lookup"><span data-stu-id="4359f-182">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="4359f-183">syscollector_config_store (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-183">syscollector_config_store &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/syscollector-config-store-transact-sql)|<span data-ttu-id="4359f-184">获取数据收集器的配置。</span><span class="sxs-lookup"><span data-stu-id="4359f-184">Get data collector configuration.</span></span>|  
|[<span data-ttu-id="4359f-185">syscollector_collection_items (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-185">syscollector_collection_items &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/syscollector-collection-items-transact-sql)|<span data-ttu-id="4359f-186">获取收集项信息。</span><span class="sxs-lookup"><span data-stu-id="4359f-186">Get collection item information.</span></span>|  
|[<span data-ttu-id="4359f-187">syscollector_collection_sets (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-187">syscollector_collection_sets &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql)|<span data-ttu-id="4359f-188">获取收集组信息。</span><span class="sxs-lookup"><span data-stu-id="4359f-188">Get collection set information.</span></span>|  
|[<span data-ttu-id="4359f-189">syscollector_collector_types (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-189">syscollector_collector_types &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/syscollector-collector-types-transact-sql)|<span data-ttu-id="4359f-190">获取收集器类型信息。</span><span class="sxs-lookup"><span data-stu-id="4359f-190">Get collector type information.</span></span>|  
|[<span data-ttu-id="4359f-191">syscollector_execution_log (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-191">syscollector_execution_log &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/syscollector-execution-log-transact-sql)|<span data-ttu-id="4359f-192">获取有关收集组和包执行的信息。</span><span class="sxs-lookup"><span data-stu-id="4359f-192">Get information about collection set and package execution.</span></span>|  
|[<span data-ttu-id="4359f-193">syscollector_execution_stats (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-193">syscollector_execution_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/syscollector-execution-stats-transact-sql)|<span data-ttu-id="4359f-194">获取有关任务执行的信息。</span><span class="sxs-lookup"><span data-stu-id="4359f-194">Get information about task execution.</span></span>|  
|[<span data-ttu-id="4359f-195">syscollector_execution_log_full (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-195">syscollector_execution_log_full &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/syscollector-execution-log-full-transact-sql)|<span data-ttu-id="4359f-196">当执行日志已满时获取信息。</span><span class="sxs-lookup"><span data-stu-id="4359f-196">Get information when the execution log is full.</span></span>|  
  
 <span data-ttu-id="4359f-197">**配置访问管理数据仓库的权限**</span><span class="sxs-lookup"><span data-stu-id="4359f-197">**Configuring access to the management data warehouse**</span></span>  
  
 <span data-ttu-id="4359f-198">下表介绍了可用于配置访问管理数据仓库的权限的存储过程。</span><span class="sxs-lookup"><span data-stu-id="4359f-198">The following table describes the stored procedures that you can use to configure access to the management data warehouse.</span></span>  
  
|<span data-ttu-id="4359f-199">过程名称</span><span class="sxs-lookup"><span data-stu-id="4359f-199">Procedure name</span></span>|<span data-ttu-id="4359f-200">说明</span><span class="sxs-lookup"><span data-stu-id="4359f-200">Description</span></span>|  
|--------------------|-----------------|  
|[<span data-ttu-id="4359f-201">sp_syscollector_set_warehouse_database_name (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-201">sp_syscollector_set_warehouse_database_name &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-set-warehouse-database-name-transact-sql)|<span data-ttu-id="4359f-202">指定在连接字符串中为管理数据仓库定义的数据库名称。</span><span class="sxs-lookup"><span data-stu-id="4359f-202">Specify the database name defined in the connection string for the management data warehouse.</span></span>|  
|[<span data-ttu-id="4359f-203">sp_syscollector_set_warehouse_instance_name (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-203">sp_syscollector_set_warehouse_instance_name &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-set-warehouse-instance-name-transact-sql)|<span data-ttu-id="4359f-204">指定在连接字符串中为管理数据仓库定义的实例。</span><span class="sxs-lookup"><span data-stu-id="4359f-204">Specify the instance defined in the connection string for the management data warehouse.</span></span>|  
  
 <span data-ttu-id="4359f-205">**配置管理数据仓库**</span><span class="sxs-lookup"><span data-stu-id="4359f-205">**Configuring the management data warehouse**</span></span>  
  
 <span data-ttu-id="4359f-206">下表介绍了使用管理数据仓库配置时可以使用的存储过程。</span><span class="sxs-lookup"><span data-stu-id="4359f-206">The following table describes the stored procedures that you can use to work with the management data warehouse configuration.</span></span>  
  
|<span data-ttu-id="4359f-207">过程名称</span><span class="sxs-lookup"><span data-stu-id="4359f-207">Procedure name</span></span>|<span data-ttu-id="4359f-208">说明</span><span class="sxs-lookup"><span data-stu-id="4359f-208">Description</span></span>|  
|--------------------|-----------------|  
|[<span data-ttu-id="4359f-209">core.sp_create_snapshot (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-209">core.sp_create_snapshot &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/core-sp-create-snapshot-transact-sql)|<span data-ttu-id="4359f-210">在管理数据仓库中创建一个收集快照。</span><span class="sxs-lookup"><span data-stu-id="4359f-210">Create a collection snapshot in the management data warehouse.</span></span>|  
|[<span data-ttu-id="4359f-211">core.sp_update_data_source (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-211">core.sp_update_data_source &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/core-sp-update-data-source-transact-sql)|<span data-ttu-id="4359f-212">为数据收集更新数据源。</span><span class="sxs-lookup"><span data-stu-id="4359f-212">Update the data source for data collection.</span></span>|  
|[<span data-ttu-id="4359f-213">core.sp_add_collector_type (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-213">core.sp_add_collector_type &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/core-sp-add-collector-type-transact-sql)|<span data-ttu-id="4359f-214">将收集器类型添加到管理数据仓库。</span><span class="sxs-lookup"><span data-stu-id="4359f-214">Add a collector type to the management data warehouse.</span></span>|  
|[<span data-ttu-id="4359f-215">core.sp_remove_collector_type (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-215">core.sp_remove_collector_type &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/core-sp-remove-collector-type-transact-sql)|<span data-ttu-id="4359f-216">从管理数据仓库中删除收集器类型。</span><span class="sxs-lookup"><span data-stu-id="4359f-216">Remove a collector type from the management data warehouse.</span></span>|  
|[<span data-ttu-id="4359f-217">core.sp_purge_data (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-217">core.sp_purge_data &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/core-sp-purge-data-transact-sql)|<span data-ttu-id="4359f-218">从管理数据仓库中删除数据。</span><span class="sxs-lookup"><span data-stu-id="4359f-218">Delete data from the management data warehouse.</span></span>|  
  
 <span data-ttu-id="4359f-219">**使用上载包**</span><span class="sxs-lookup"><span data-stu-id="4359f-219">**Working with upload packages**</span></span>  
  
 <span data-ttu-id="4359f-220">下表介绍了使用上载包时可以使用的存储过程。</span><span class="sxs-lookup"><span data-stu-id="4359f-220">The following table describes the stored procedures that you can use to work with upload packages.</span></span>  
  
|<span data-ttu-id="4359f-221">过程名称</span><span class="sxs-lookup"><span data-stu-id="4359f-221">Procedure name</span></span>|<span data-ttu-id="4359f-222">说明</span><span class="sxs-lookup"><span data-stu-id="4359f-222">Description</span></span>|  
|--------------------|-----------------|  
|[<span data-ttu-id="4359f-223">sp_syscollector_set_cache_window (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-223">sp_syscollector_set_cache_window &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-set-cache-window-transact-sql)|<span data-ttu-id="4359f-224">配置数据上载重试的次数。</span><span class="sxs-lookup"><span data-stu-id="4359f-224">Configure the number of data upload retries.</span></span>|  
|[<span data-ttu-id="4359f-225">sp_syscollector_set_cache_directory (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-225">sp_syscollector_set_cache_directory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-set-cache-directory-transact-sql)|<span data-ttu-id="4359f-226">指定在两次上载重试之间数据的临时存储区。</span><span class="sxs-lookup"><span data-stu-id="4359f-226">Specify temporary storage for data between upload retries.</span></span>|  
  
 <span data-ttu-id="4359f-227">**使用数据收集执行日志**</span><span class="sxs-lookup"><span data-stu-id="4359f-227">**Working with the data collection execution log**</span></span>  
  
 <span data-ttu-id="4359f-228">下表介绍了使用数据收集执行日志时可以使用的存储过程。</span><span class="sxs-lookup"><span data-stu-id="4359f-228">The following table describes the stored procedures that you can use to work with the data collection execution log.</span></span>  
  
|<span data-ttu-id="4359f-229">过程名称</span><span class="sxs-lookup"><span data-stu-id="4359f-229">Procedure name</span></span>|<span data-ttu-id="4359f-230">说明</span><span class="sxs-lookup"><span data-stu-id="4359f-230">Description</span></span>|  
|--------------------|-----------------|  
|[<span data-ttu-id="4359f-231">sp_syscollector_delete_execution_log_tree (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-231">sp_syscollector_delete_execution_log_tree &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-delete-execution-log-tree-transact-sql)|<span data-ttu-id="4359f-232">从执行日志删除收集组条目。</span><span class="sxs-lookup"><span data-stu-id="4359f-232">Delete collection set entries from the execution log.</span></span>|  
  
### <a name="functions"></a><span data-ttu-id="4359f-233">函数</span><span class="sxs-lookup"><span data-stu-id="4359f-233">Functions</span></span>  
 <span data-ttu-id="4359f-234">下表介绍了可用于获取执行和跟踪信息的函数。</span><span class="sxs-lookup"><span data-stu-id="4359f-234">The following table describes the functions that you can use to obtain execution and trace information.</span></span>  
  
|<span data-ttu-id="4359f-235">函数名称</span><span class="sxs-lookup"><span data-stu-id="4359f-235">Function name</span></span>|<span data-ttu-id="4359f-236">说明</span><span class="sxs-lookup"><span data-stu-id="4359f-236">Description</span></span>|  
|-------------------|-----------------|  
|[<span data-ttu-id="4359f-237">fn_syscollector_get_execution_details (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-237">fn_syscollector_get_execution_details &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/fn-syscollector-get-execution-details-transact-sql)|<span data-ttu-id="4359f-238">为特定包获取 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 执行日志数据。</span><span class="sxs-lookup"><span data-stu-id="4359f-238">Get [!INCLUDE[ssIS](../../includes/ssis-md.md)] execution log data for a specific package.</span></span>|  
|[<span data-ttu-id="4359f-239">fn_syscollector_get_execution_stats (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-239">fn_syscollector_get_execution_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/fn-syscollector-get-execution-stats-transact-sql)|<span data-ttu-id="4359f-240">为收集组或包获取执行统计信息。</span><span class="sxs-lookup"><span data-stu-id="4359f-240">Get execution statistics for a collection set or package.</span></span> <span data-ttu-id="4359f-241">此信息包含所记录的错误。</span><span class="sxs-lookup"><span data-stu-id="4359f-241">This information includes errors that are logged.</span></span>|  
|[<span data-ttu-id="4359f-242">snapshots.fn_trace_getdata (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4359f-242">snapshots.fn_trace_getdata &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/snapshots-fn-trace-getdata-transact-sql)|<span data-ttu-id="4359f-243">获取使用一般 SQL Trace 收集器类型收集数据时记录的事件。</span><span class="sxs-lookup"><span data-stu-id="4359f-243">Get the events that are logged when the Generic SQL Trace collector type is used to collect data.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4359f-244">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4359f-244">See Also</span></span>  
 <span data-ttu-id="4359f-245">[执行存储过程](../stored-procedures/execute-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="4359f-245">[Execute a Stored Procedure](../stored-procedures/execute-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="4359f-246">[使用 SQL Server Management Studio](../../database-engine/use-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="4359f-246">[Use SQL Server Management Studio](../../database-engine/use-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="4359f-247">“数据收集”</span><span class="sxs-lookup"><span data-stu-id="4359f-247">Data Collection</span></span>](data-collection.md)  
  
  
