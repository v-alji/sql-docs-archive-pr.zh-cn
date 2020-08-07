---
title: 创建使用一般 T-sql 查询收集器类型的自定义收集组 (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- T-SQL Query collector type
- collection sets [SQL Server], creating custom
ms.assetid: 6b06db5b-cfdc-4ce0-addd-ec643460605b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ab21ad5fd65556dec639fd5ca6999d23e2de673b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588573"
---
# <a name="create-a-custom-collection-set-that-uses-the-generic-t-sql-query-collector-type-transact-sql"></a><span data-ttu-id="ea8b3-102">创建使用一般 T-SQL 查询收集器类型的自定义收集组 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ea8b3-102">Create a Custom Collection Set That Uses the Generic T-SQL Query Collector Type (Transact-SQL)</span></span>
  <span data-ttu-id="ea8b3-103">可以使用与数据收集器一起提供的存储过程创建包含使用一般 T-SQL 查询收集器类型的收集项的自定义收集组。</span><span class="sxs-lookup"><span data-stu-id="ea8b3-103">You can create a custom collection set with collection items that use the Generic T-SQL Query collector type by using the stored procedures that are provided with the data collector.</span></span> <span data-ttu-id="ea8b3-104">若要完成此任务，需使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的查询编辑器来执行以下过程：</span><span class="sxs-lookup"><span data-stu-id="ea8b3-104">Accomplishing this task involves using Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to carry out the following procedures:</span></span>  
  
-   <span data-ttu-id="ea8b3-105">配置上载计划。</span><span class="sxs-lookup"><span data-stu-id="ea8b3-105">Configure upload schedules.</span></span>  
  
-   <span data-ttu-id="ea8b3-106">定义和创建收集组。</span><span class="sxs-lookup"><span data-stu-id="ea8b3-106">Define and create the collection set.</span></span>  
  
-   <span data-ttu-id="ea8b3-107">定义和创建收集项。</span><span class="sxs-lookup"><span data-stu-id="ea8b3-107">Define and create a collection item.</span></span>  
  
-   <span data-ttu-id="ea8b3-108">验证该收集组和收集项是否存在。</span><span class="sxs-lookup"><span data-stu-id="ea8b3-108">Verify that the collection set and collection items exist.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ea8b3-109">在创建自定义收集组之前，必须配置数据收集参数。</span><span class="sxs-lookup"><span data-stu-id="ea8b3-109">Before you create a custom collection set, you must configure data collection parameters.</span></span> <span data-ttu-id="ea8b3-110">有关详细信息，请参阅[配置数据收集参数 (Transact-SQL)](configure-data-collection-parameters-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="ea8b3-110">For more information, see [Configure Data Collection Parameters &#40;Transact-SQL&#41;](configure-data-collection-parameters-transact-sql.md).</span></span>  
  
### <a name="define-and-create-the-collection-set"></a><span data-ttu-id="ea8b3-111">定义和创建收集组</span><span class="sxs-lookup"><span data-stu-id="ea8b3-111">Define and create the collection set</span></span>  
  
1.  <span data-ttu-id="ea8b3-112">使用 sp_syscollector_create_collection_set 存储过程定义一个新的收集组。</span><span class="sxs-lookup"><span data-stu-id="ea8b3-112">Define a new collection set using the sp_syscollector_create_collection_set stored procedure.</span></span>  
  
    ```  
    USE msdb;  
    DECLARE @collection_set_id int;  
    DECLARE @collection_set_uid uniqueidentifier;  
    EXEC sp_syscollector_create_collection_set   
        @name=N'DMV Test 1',   
        @collection_mode=0,   
        @description=N'This is a test collection set',   
        @logging_level=1,   
        @days_until_expiration=14,   
        @schedule_name=N'CollectorSchedule_Every_15min',   
        @collection_set_id=@collection_set_id OUTPUT,   
        @collection_set_uid=@collection_set_uid OUTPUT;  
    SELECT @collection_set_id, @collection_set_uid;  
    ```  
  
     <span data-ttu-id="ea8b3-113">收集模式可以设置为 0（缓存）或 1（非缓存）。</span><span class="sxs-lookup"><span data-stu-id="ea8b3-113">The collection mode can be set to either 0 (cached) or to 1 (non-cached).</span></span>  
  
     <span data-ttu-id="ea8b3-114">日志记录级别可以设置为 0、1 或 2。</span><span class="sxs-lookup"><span data-stu-id="ea8b3-114">The logging level can be set to 0, 1 or 2.</span></span>  
  
     <span data-ttu-id="ea8b3-115">以下预配置计划随数据收集器一起提供：</span><span class="sxs-lookup"><span data-stu-id="ea8b3-115">The following preconfigured schedules are provided with the data collector:</span></span>  
  
    -   <span data-ttu-id="ea8b3-116">CollectorSchedule_Every_5min</span><span class="sxs-lookup"><span data-stu-id="ea8b3-116">CollectorSchedule_Every_5min</span></span>  
  
    -   <span data-ttu-id="ea8b3-117">CollectorSchedule_Every_10min</span><span class="sxs-lookup"><span data-stu-id="ea8b3-117">CollectorSchedule_Every_10min</span></span>  
  
    -   <span data-ttu-id="ea8b3-118">CollectorSchedule_Every_15min</span><span class="sxs-lookup"><span data-stu-id="ea8b3-118">CollectorSchedule_Every_15min</span></span>  
  
    -   <span data-ttu-id="ea8b3-119">CollectorSchedule_Every_30min</span><span class="sxs-lookup"><span data-stu-id="ea8b3-119">CollectorSchedule_Every_30min</span></span>  
  
    -   <span data-ttu-id="ea8b3-120">CollectorSchedule_Every_60min</span><span class="sxs-lookup"><span data-stu-id="ea8b3-120">CollectorSchedule_Every_60min</span></span>  
  
    -   <span data-ttu-id="ea8b3-121">CollectorSchedule_Every_6h</span><span class="sxs-lookup"><span data-stu-id="ea8b3-121">CollectorSchedule_Every_6h</span></span>  
  
     <span data-ttu-id="ea8b3-122">如果不想使用提供的这些计划，您可以创建一个新计划，然后将其用于收集组。</span><span class="sxs-lookup"><span data-stu-id="ea8b3-122">If you do not want to use one of the schedules that are provided, you can create a new schedule and use it for the collection set.</span></span> <span data-ttu-id="ea8b3-123">有关详细信息，请参阅 [创建计划并将计划附加到作业](../../ssms/agent/create-and-attach-schedules-to-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="ea8b3-123">For more information, see [Create and Attach Schedules to Jobs](../../ssms/agent/create-and-attach-schedules-to-jobs.md).</span></span>  
  
### <a name="define-and-create-a-collection-item"></a><span data-ttu-id="ea8b3-124">定义和创建收集项</span><span class="sxs-lookup"><span data-stu-id="ea8b3-124">Define and create a collection item</span></span>  
  
1.  <span data-ttu-id="ea8b3-125">由于新的收集项基于已经安装的一般收集器类型，因此可以运行以下代码来设置 GUID，使其与一般 T-SQL 查询收集器类型相对应。</span><span class="sxs-lookup"><span data-stu-id="ea8b3-125">Because the new collection item is based on a generic collector type that is already installed, you can run the following code to set the GUID to correspond to the Generic T-SQL Query collector type.</span></span>  
  
    ```sql  
    DECLARE @collector_type_uid uniqueidentifier;  
    SELECT @collector_type_uid = collector_type_uid FROM [msdb].[dbo].[syscollector_collector_types]   
    WHERE name = N'Generic T-SQL Query Collector Type';  
    DECLARE @collection_item_id int;  
    ```  
  
2.  <span data-ttu-id="ea8b3-126">使用 sp_syscollector_create_collection_item 存储过程来创建收集项。</span><span class="sxs-lookup"><span data-stu-id="ea8b3-126">Use the sp_syscollector_create_collection_item stored procedure to create the collection item.</span></span> <span data-ttu-id="ea8b3-127">声明收集项的架构，这样它将映射到一般 T-SQL 查询收集器类型所需的架构。</span><span class="sxs-lookup"><span data-stu-id="ea8b3-127">Declare the schema for the collection item so it maps to the schema that is required for the Generic T-SQL Query collector type.</span></span>  
  
    ```sql  
    EXEC sp_syscollector_create_collection_item   
        @name=N'Query Stats - Test 1',   
        @parameters=N'  
            <ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
            <Query>  
            <Value>SELECT * FROM sys.dm_exec_query_stats</Value>  
            <OutputTable>dm_exec_query_stats</OutputTable>  
            </Query>  
            </ns:TSQLQueryCollector>',   
        @collection_item_id=@collection_item_id OUTPUT,   
        @frequency=5,   
        @collection_set_id=@collection_set_id,   
        @collector_type_uid=@collector_type_uid;  
    SELECT @collection_item_id;  
    ```  
  
### <a name="verify-that-the-new-collection-set-and-collection-item-exist"></a><span data-ttu-id="ea8b3-128">验证新的收集组和收集项是否存在</span><span class="sxs-lookup"><span data-stu-id="ea8b3-128">Verify that the new collection set and collection item exist</span></span>  
  
1.  <span data-ttu-id="ea8b3-129">在启动新的收集组之前，运行以下查询以验证新的收集组及其收集项是否已创建。</span><span class="sxs-lookup"><span data-stu-id="ea8b3-129">Before starting the new collection set, run the following query to verify that the new collection set and its collection item have been created.</span></span>  
  
    ```sql  
    USE msdb;  
    SELECT * FROM syscollector_collection_sets;  
    SELECT * FROM syscollector_collection_items;  
    GO  
    ```  
  
     <span data-ttu-id="ea8b3-130">您还可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中执行目视检查。</span><span class="sxs-lookup"><span data-stu-id="ea8b3-130">You can also do a visual check in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="ea8b3-131">在对象资源管理器中，展开 **“管理”** 节点，然后展开 **“数据收集”** 。</span><span class="sxs-lookup"><span data-stu-id="ea8b3-131">In Object Explorer, expand the **Management** node, and then expand **Data Collection**.</span></span> <span data-ttu-id="ea8b3-132">新的收集组将显示。</span><span class="sxs-lookup"><span data-stu-id="ea8b3-132">The new collection set will be displayed.</span></span> <span data-ttu-id="ea8b3-133">收集组的红色圆圈图标指示该收集组已停止。</span><span class="sxs-lookup"><span data-stu-id="ea8b3-133">The red circle icon for the collection set indicates that the collection set is stopped.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea8b3-134">示例</span><span class="sxs-lookup"><span data-stu-id="ea8b3-134">Example</span></span>  
 <span data-ttu-id="ea8b3-135">下面的代码示例汇集了上面步骤中记录的示例。</span><span class="sxs-lookup"><span data-stu-id="ea8b3-135">The following code sample combines the examples that are documented in the previous steps.</span></span> <span data-ttu-id="ea8b3-136">请注意，为收集项设置的收集频率（5 秒钟）将被忽略，因为收集组的收集模式设置为 0，即缓存模式。</span><span class="sxs-lookup"><span data-stu-id="ea8b3-136">Note that the collection frequency that is set for the collection item (5 seconds) is ignored because the collection set collection mode is set to 0, which is cached mode.</span></span> <span data-ttu-id="ea8b3-137">有关详细信息，请参阅 [Data Collection](data-collection.md)。</span><span class="sxs-lookup"><span data-stu-id="ea8b3-137">For more information, see [Data Collection](data-collection.md).</span></span>  
  
```sql  
USE msdb;  
  
DECLARE @collection_set_id int;  
DECLARE @collection_set_uid uniqueidentifier  
  
EXEC dbo.sp_syscollector_create_collection_set  
    @name = N'DMV Stats Test 1',  
    @collection_mode = 0,  
    @description = N'This is a test collection set',  
    @logging_level=1,  
    @days_until_expiration = 14,  
    @schedule_name=N'CollectorSchedule_Every_15min',  
    @collection_set_id = @collection_set_id OUTPUT,  
    @collection_set_uid = @collection_set_uid OUTPUT;  
SELECT @collection_set_id,@collection_set_uid;  
  
DECLARE @collector_type_uid uniqueidentifier;  
SELECT @collector_type_uid = collector_type_uid FROM syscollector_collector_types   
WHERE name = N'Generic T-SQL Query Collector Type';  
  
DECLARE @collection_item_id int;  
EXEC sp_syscollector_create_collection_item  
@name= N'Query Stats - Test 1',  
@parameters=N'  
<ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
<Query>  
  <Value>select * from sys.dm_exec_query_stats</Value>  
  <OutputTable>dm_exec_query_stats</OutputTable>  
</Query>  
 </ns:TSQLQueryCollector>',  
    @collection_item_id = @collection_item_id OUTPUT,  
    @frequency = 5, -- This parameter is ignored in cached mode  
    @collection_set_id = @collection_set_id,  
    @collector_type_uid = @collector_type_uid;  
SELECT @collection_item_id;  
  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="ea8b3-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ea8b3-138">See Also</span></span>  
 <span data-ttu-id="ea8b3-139">[数据收集器存储过程 (Transact-SQL)](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ea8b3-139">[Data Collector Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql) </span></span>  
 <span data-ttu-id="ea8b3-140">[管理计划](../../ssms/agent/manage-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="ea8b3-140">[Manage Schedules](../../ssms/agent/manage-schedules.md) </span></span>  
 [<span data-ttu-id="ea8b3-141">启动或停止收集组</span><span class="sxs-lookup"><span data-stu-id="ea8b3-141">Start or Stop a Collection Set</span></span>](start-or-stop-a-collection-set.md)  
  
  
