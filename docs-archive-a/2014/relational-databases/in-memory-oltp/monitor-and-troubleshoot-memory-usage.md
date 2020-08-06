---
title: 内存使用情况的监视和故障排除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 7a458b9c-3423-4e24-823d-99573544c877
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5805ed06ad78040dbdf6c8557e5f548ad57f618b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693877"
---
# <a name="monitor-and-troubleshoot-memory-usage"></a><span data-ttu-id="c9d56-102">内存使用情况的监视和故障排除</span><span class="sxs-lookup"><span data-stu-id="c9d56-102">Monitor and Troubleshoot Memory Usage</span></span>
  [!INCLUDE[hek_1](../../includes/hek-1-md.md)] <span data-ttu-id="c9d56-103">使用内存的模式与针对基于磁盘的表的模式不同。</span><span class="sxs-lookup"><span data-stu-id="c9d56-103">consumes memory in different patterns than disk-based tables.</span></span> <span data-ttu-id="c9d56-104">您可以使用为内存和垃圾回收子系统提供的 DMV 或性能计数器，监视数据库中内存优化表和索引分配和使用的内存量。</span><span class="sxs-lookup"><span data-stu-id="c9d56-104">You can monitor the amount of memory allocated and used by memory-optimized tables and indexes in your database using the DMVs or performance counters provided for memory and the garbage collection subsystem.</span></span>  <span data-ttu-id="c9d56-105">这使您在系统和数据库级别都获得可见性，并允许防止由于内存用尽而导致的问题。</span><span class="sxs-lookup"><span data-stu-id="c9d56-105">This gives you visibility at both the system and database level and lets you prevent problems due to memory exhaustion.</span></span>

 <span data-ttu-id="c9d56-106">本主题介绍如何监视 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 内存使用量。</span><span class="sxs-lookup"><span data-stu-id="c9d56-106">This topic covers monitoring your [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] memory usage.</span></span>


##  <a name="create-a-sample-database-with-memory-optimized-tables"></a><a name="bkmk_CreateDB"></a> <span data-ttu-id="c9d56-107">使用内存优化表创建示例数据库</span><span class="sxs-lookup"><span data-stu-id="c9d56-107">Create a sample database with memory-optimized tables</span></span>
 <span data-ttu-id="c9d56-108">如果您已具有含内存优化表的数据库，则可以跳过此部分。</span><span class="sxs-lookup"><span data-stu-id="c9d56-108">You can skip this section if you already have a database with memory-optimized tables.</span></span>

 <span data-ttu-id="c9d56-109">以下步骤将创建一个数据库，其中包含您可在本主题的其余部分中使用的三个内存优化表。</span><span class="sxs-lookup"><span data-stu-id="c9d56-109">The following steps create a database with three memory-optimized tables that you can use in the remainder of this topic.</span></span> <span data-ttu-id="c9d56-110">在该示例中，我们将该数据库映射到了一个资源池，以便我们可以控制内存优化表可使用的内存量。</span><span class="sxs-lookup"><span data-stu-id="c9d56-110">In the example, we mapped the database to a resource pool so that we can control how much memory can be taken by memory-optimized tables.</span></span>

1.  <span data-ttu-id="c9d56-111">启动 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c9d56-111">Launch [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>

2.  <span data-ttu-id="c9d56-112">单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="c9d56-112">Click **New Query**.</span></span>

3.  <span data-ttu-id="c9d56-113">将此代码粘贴到新查询窗口中并执行各部分。</span><span class="sxs-lookup"><span data-stu-id="c9d56-113">Paste this code into the new query window and execute each section.</span></span>

    ```
    -- create a database to be used
    CREATE DATABASE IMOLTP_DB
    GO

    ALTER DATABASE IMOLTP_DB ADD FILEGROUP IMOLTP_DB_xtp_fg CONTAINS MEMORY_OPTIMIZED_DATA
    ALTER DATABASE IMOLTP_DB ADD FILE( NAME = 'IMOLTP_DB_xtp' , FILENAME = 'C:\Data\IMOLTP_DB_xtp') TO FILEGROUP IMOLTP_DB_xtp_fg;
    GO

    USE IMOLTP_DB
    GO

    -- create the resoure pool
    CREATE RESOURCE POOL PoolIMOLTP WITH (MAX_MEMORY_PERCENT = 60);
    ALTER RESOURCE GOVERNOR RECONFIGURE;
    GO

    -- bind the database to a resource pool
    EXEC sp_xtp_bind_db_resource_pool 'IMOLTP_DB', 'PoolIMOLTP'

    -- you can query the binding using the catalog view as described here
    SELECT d.database_id
         , d.name
         , d.resource_pool_id
    FROM sys.databases d
    GO

    -- take database offline/online to finalize the binding to the resource pool
    USE master
    GO

    ALTER DATABASE IMOLTP_DB SET OFFLINE
    GO
    ALTER DATABASE IMOLTP_DB SET ONLINE
    GO

    -- create some tables
    USE IMOLTP_DB
    GO

    -- create table t1
    CREATE TABLE dbo.t1 (
           c1 int NOT NULL CONSTRAINT [pk_t1_c1] PRIMARY KEY NONCLUSTERED
         , c2 char(40) NOT NULL
         , c3 char(8000) NOT NULL
         ) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)
    GO

    -- load t1 150K rows
    DECLARE @i int = 0
    BEGIN TRAN
    WHILE (@i <= 150000)
       BEGIN
          INSERT t1 VALUES (@i, 'a', replicate ('b', 8000))
          SET @i += 1;
       END
    Commit
    GO

    -- Create another table, t2
    CREATE TABLE dbo.t2 (
           c1 int NOT NULL CONSTRAINT [pk_t2_c1] PRIMARY KEY NONCLUSTERED
         , c2 char(40) NOT NULL
         , c3 char(8000) NOT NULL
         ) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)
    GO

    -- Create another table, t3 
    CREATE TABLE dbo.t3 (
           c1 int NOT NULL CONSTRAINT [pk_t3_c1] PRIMARY KEY NONCLUSTERED HASH (c1) WITH (BUCKET_COUNT = 1000000)
         , c2 char(40) NOT NULL
         , c3 char(8000) NOT NULL
         ) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)
    GO
    ```

##  <a name="monitoring-memory-usage"></a><span data-ttu-id="c9d56-114">监视内存使用量</span><span class="sxs-lookup"><span data-stu-id="c9d56-114">Monitoring Memory Usage</span></span>

###  <a name="using-ssmanstudiofull"></a><span data-ttu-id="c9d56-115">使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9d56-115">Using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]</span></span>
 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="c9d56-116">附随内置的标准报表，以便监视内存中表使用的内存。</span><span class="sxs-lookup"><span data-stu-id="c9d56-116">ships with built-in standard reports to monitor the memory consumed by in-memory tables.</span></span> <span data-ttu-id="c9d56-117">可以使用对象资源管理器访问这些报表。</span><span class="sxs-lookup"><span data-stu-id="c9d56-117">You can access these reports using Object Explorer.</span></span> <span data-ttu-id="c9d56-118">还可使用对象资源管理器监视单独的内存优化表占用的内存。</span><span class="sxs-lookup"><span data-stu-id="c9d56-118">You can also use the object explorer to monitor memory consumed by individual memory-optimized tables.</span></span>

#### <a name="consumption-at-the-database-level"></a><span data-ttu-id="c9d56-119">数据库级别的内存使用情况</span><span class="sxs-lookup"><span data-stu-id="c9d56-119">Consumption at the database level</span></span>
 <span data-ttu-id="c9d56-120">您可以按如下所示在数据库级别监视内存使用情况。</span><span class="sxs-lookup"><span data-stu-id="c9d56-120">You can monitor memory use at the database level as follows.</span></span>

1.  <span data-ttu-id="c9d56-121">启动 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 事件探查器，然后连接到某个服务器。</span><span class="sxs-lookup"><span data-stu-id="c9d56-121">Launch [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and connect to a server.</span></span>

2.  <span data-ttu-id="c9d56-122">在对象资源管理器中，右键单击您要报告的数据库。</span><span class="sxs-lookup"><span data-stu-id="c9d56-122">In Object Explorer, right-click the database you want reports on.</span></span>

3.  <span data-ttu-id="c9d56-123">在上下文菜单中，选择“报表” -> “标准报表” -> “内存优化对象的内存使用情况”</span><span class="sxs-lookup"><span data-stu-id="c9d56-123">In the context menu select, **Reports** -> **Standard Reports** -> **Memory Usage By Memory Optimized Objects**</span></span>

 <span data-ttu-id="c9d56-124">![HK_MM_SSMS](../../database-engine/media/hk-mm-ssms-stdrpt-memuse.gif "HK_MM_SSMS")</span><span class="sxs-lookup"><span data-stu-id="c9d56-124">![HK_MM_SSMS](../../database-engine/media/hk-mm-ssms-stdrpt-memuse.gif "HK_MM_SSMS")</span></span>

 <span data-ttu-id="c9d56-125">此报表显示我们在上面创建的数据库的内存使用情况。</span><span class="sxs-lookup"><span data-stu-id="c9d56-125">This report shows memory consumption by the database we created above.</span></span>

 <span data-ttu-id="c9d56-126">![HK_MM_SSMS](../../database-engine/media/hk-mm-ssms-stdrpt-memuserpt.gif "HK_MM_SSMS")</span><span class="sxs-lookup"><span data-stu-id="c9d56-126">![HK_MM_SSMS](../../database-engine/media/hk-mm-ssms-stdrpt-memuserpt.gif "HK_MM_SSMS")</span></span>

###  <a name="using-dmvs"></a><span data-ttu-id="c9d56-127">使用 DMV</span><span class="sxs-lookup"><span data-stu-id="c9d56-127">Using DMVs</span></span>
 <span data-ttu-id="c9d56-128">有许多 DMV 可用于监视由内存优化表、索引、系统对象和运行时结构使用的内存。</span><span class="sxs-lookup"><span data-stu-id="c9d56-128">There are a number of DMVs available to monitor memory consumed by memory-optimized tables, indexes, system objects, and by run-time structures.</span></span>

#### <a name="memory-consumption-by-memory-optimized-tables-and-indexes"></a><span data-ttu-id="c9d56-129">内存优化表和索引的内存使用情况</span><span class="sxs-lookup"><span data-stu-id="c9d56-129">Memory consumption by memory-optimized tables and indexes</span></span>
 <span data-ttu-id="c9d56-130">您可以通过按如下所示查询 `sys.dm_db_xtp_table_memory_stats` ，查找所有用户表、索引和系统对象的内存使用情况。</span><span class="sxs-lookup"><span data-stu-id="c9d56-130">You can find memory consumption for all user tables, indexes, and system objects by querying `sys.dm_db_xtp_table_memory_stats` as shown here.</span></span>

```sql
SELECT object_name(object_id) AS Name
     , *
   FROM sys.dm_db_xtp_table_memory_stats
```

 <span data-ttu-id="c9d56-131">**示例输出**</span><span class="sxs-lookup"><span data-stu-id="c9d56-131">**Sample Output**</span></span>

```
Name       object_id   memory_allocated_for_table_kb memory_used_by_table_kb memory_allocated_for_indexes_kb memory_used_by_indexes_kb
---------- ----------- ----------------------------- ----------------------- ------------------------------- -------------------------
t3         629577281   0                             0                       128                             0
t1         565577053   1372928                       1200008                 7872                            1942
t2         597577167   0                             0                       128                             0
NULL       -6          0                             0                       2                               2
NULL       -5          0                             0                       24                              24
NULL       -4          0                             0                       2                               2
NULL       -3          0                             0                       2                               2
NULL       -2          192                           25                      16                              16
```

 <span data-ttu-id="c9d56-132">有关详细信息，请参阅[sys. dm_db_xtp_table_memory_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-table-memory-stats-transact-sql?view=sql-server-2016)。</span><span class="sxs-lookup"><span data-stu-id="c9d56-132">For more information, see [sys.dm_db_xtp_table_memory_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-table-memory-stats-transact-sql?view=sql-server-2016).</span></span>

#### <a name="memory-consumption-by-internal-system-structures"></a><span data-ttu-id="c9d56-133">内部系统结构的内存使用情况</span><span class="sxs-lookup"><span data-stu-id="c9d56-133">Memory consumption by internal system structures</span></span>
 <span data-ttu-id="c9d56-134">系统对象也会使用内存，例如事务结构、针对数据和差异文件的缓冲区以及垃圾回收结构等。</span><span class="sxs-lookup"><span data-stu-id="c9d56-134">Memory is also consumed by system objects, such as, transactional structures, buffers for data and delta files, garbage collection structures, and more.</span></span> <span data-ttu-id="c9d56-135">您可以通过按如下所示查询 `sys.dm_xtp_system_memory_consumers` ，查找用于这些系统对象的内存。</span><span class="sxs-lookup"><span data-stu-id="c9d56-135">You can find the memory used for these system objects by querying `sys.dm_xtp_system_memory_consumers` as shown here.</span></span>

```sql
SELECT memory_consumer_desc
     , allocated_bytes/1024 AS allocated_bytes_kb
     , used_bytes/1024 AS used_bytes_kb
     , allocation_count
   FROM sys.dm_xtp_system_memory_consumers
```

 <span data-ttu-id="c9d56-136">**示例输出**</span><span class="sxs-lookup"><span data-stu-id="c9d56-136">**Sample Output**</span></span>

```
memory_consumer_ desc allocated_bytes_kb   used_bytes_kb        allocation_count
------------------------- -------------------- -------------------- ----------------
VARHEAP                   0                    0                    0
VARHEAP                   384                  0                    0
DBG_GC_OUTSTANDING_T      64                   64                   910
ACTIVE_TX_MAP_LOOKAS      0                    0                    0
RECOVERY_TABLE_CACHE      0                    0                    0
RECENTLY_USED_ROWS_L      192                  192                  261
RANGE_CURSOR_LOOKSID      0                    0                    0
HASH_CURSOR_LOOKASID      128                  128                  455
SAVEPOINT_LOOKASIDE       0                    0                    0
PARTIAL_INSERT_SET_L      192                  192                  351
CONSTRAINT_SET_LOOKA      192                  192                  646
SAVEPOINT_SET_LOOKAS      0                    0                    0
WRITE_SET_LOOKASIDE       192                  192                  183
SCAN_SET_LOOKASIDE        64                   64                   31
READ_SET_LOOKASIDE        0                    0                    0
TRANSACTION_LOOKASID      448                  448                  156
PGPOOL:256K               768                  768                  3
PGPOOL: 64K               0                    0                    0
PGPOOL:  4K               0                    0                    0
```

 <span data-ttu-id="c9d56-137">有关详细信息，请参阅 [sys.dm_xtp_system_memory_consumers (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-table-memory-stats-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c9d56-137">For more information see [sys.dm_xtp_system_memory_consumers &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-table-memory-stats-transact-sql).</span></span>


#### <a name="memory-consumption-at-run-time-when-accessing-memory-optimized-tables"></a><span data-ttu-id="c9d56-138">访问内存优化表时在运行时的内存使用情况</span><span class="sxs-lookup"><span data-stu-id="c9d56-138">Memory consumption at run-time when accessing memory-optimized tables</span></span>
 <span data-ttu-id="c9d56-139">您可以确定运行时结构使用的内存，例如使用以下查询确定过程缓存使用的内存：运行此查询可获取运行时结构（例如用于过程缓存的运行时结构）使用的内存。</span><span class="sxs-lookup"><span data-stu-id="c9d56-139">You can determine the memory consumed by run time structures, such as the procedure cache with the following query: run this query to get the memory used by run-time structures such as for the procedure cache.</span></span> <span data-ttu-id="c9d56-140">所有运行时结构都用 XTP 进行标记。</span><span class="sxs-lookup"><span data-stu-id="c9d56-140">All run-time structures are tagged with XTP.</span></span>

```sql
SELECT memory_object_address
     , pages_in_bytes
     , bytes_used
     , type
   FROM sys.dm_os_memory_objects WHERE type LIKE '%xtp%'
```

 <span data-ttu-id="c9d56-141">**示例输出**</span><span class="sxs-lookup"><span data-stu-id="c9d56-141">**Sample Output**</span></span>

```
memory_object_address pages_ in_bytes bytes_used type
--------------------- ------------------- ---------- ----
0x00000001F1EA8040    507904              NULL       MEMOBJ_XTPDB
0x00000001F1EAA040    68337664            NULL       MEMOBJ_XTPDB
0x00000001FD67A040    16384               NULL       MEMOBJ_XTPPROCCACHE
0x00000001FD68C040    16384               NULL       MEMOBJ_XTPPROCPARTITIONEDHEAP
0x00000001FD284040    16384               NULL       MEMOBJ_XTPPROCPARTITIONEDHEAP
0x00000001FD302040    16384               NULL       MEMOBJ_XTPPROCPARTITIONEDHEAP
0x00000001FD382040    16384               NULL       MEMOBJ_XTPPROCPARTITIONEDHEAP
0x00000001FD402040    16384               NULL       MEMOBJ_XTPPROCPARTITIONEDHEAP
0x00000001FD482040    16384               NULL       MEMOBJ_XTPPROCPARTITIONEDHEAP
0x00000001FD502040    16384               NULL       MEMOBJ_XTPPROCPARTITIONEDHEAP
0x00000001FD67E040    16384               NULL       MEMOBJ_XTPPROCPARTITIONEDHEAP
0x00000001F813C040    8192                NULL       MEMOBJ_XTPBLOCKALLOC
0x00000001F813E040    16842752            NULL       MEMOBJ_XTPBLOCKALLOC
```

 <span data-ttu-id="c9d56-142">有关详细信息，请参阅[sys.databases) dm_os_memory_objects (](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c9d56-142">For more information, see [sys.dm_os_memory_objects (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql).</span></span>

#### <a name="memory-consumed-by-hek_2-engine-across-the-instance"></a><span data-ttu-id="c9d56-143">跨实例的 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 引擎使用的内存</span><span class="sxs-lookup"><span data-stu-id="c9d56-143">Memory consumed by [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] engine across the instance</span></span>
 <span data-ttu-id="c9d56-144">管理分配给 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 引擎和内存优化对象的内存的方式与管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例内任何其他内存消耗者的方式完全相同。</span><span class="sxs-lookup"><span data-stu-id="c9d56-144">Memory allocated to the [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] engine and the memory-optimized objects is managed the same way as any other memory consumer within a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="c9d56-145">MEMORYCLERK_XTP 类型的内存分配器计算分配给 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 引擎的所有内存。</span><span class="sxs-lookup"><span data-stu-id="c9d56-145">The clerks of type MEMORYCLERK_XTP accounts for all the memory allocated to [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] engine.</span></span> <span data-ttu-id="c9d56-146">使用下面的查询可查找 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 引擎使用的所有内存。</span><span class="sxs-lookup"><span data-stu-id="c9d56-146">Use the following query to find all the memory used by the [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] engine.</span></span>

```sql
-- this DMV accounts for all memory used by the hek_2 engine
SELECT type
     , name
     , memory_node_id
     , pages_kb/1024 AS pages_MB 
   FROM sys.dm_os_memory_clerks WHERE type LIKE '%xtp%'
```

 <span data-ttu-id="c9d56-147">此示例输出显示，分配的总内存为 18 MB（系统级内存占用）和 1358MB（分配给数据库 ID 5）。</span><span class="sxs-lookup"><span data-stu-id="c9d56-147">The sample output shows that the total memory allocated is 18 MB system-level memory consumption and 1358MB allocated to database id of 5.</span></span> <span data-ttu-id="c9d56-148">此数据库映射到一个专用资源池，因此这些内存仅用于该资源池。</span><span class="sxs-lookup"><span data-stu-id="c9d56-148">Since this database is mapped to a dedicated resource pool, this memory is accounted for in that resource pool.</span></span>

 <span data-ttu-id="c9d56-149">**示例输出**</span><span class="sxs-lookup"><span data-stu-id="c9d56-149">**Sample Output**</span></span>

```
type                 name       memory_node_id pages_MB
-------------------- ---------- -------------- --------------------
MEMORYCLERK_XTP      Default    0              18
MEMORYCLERK_XTP      DB_ID_5    0              1358
MEMORYCLERK_XTP      Default    64             0
```

 <span data-ttu-id="c9d56-150">有关详细信息，请参阅[sys.databases) dm_os_memory_clerks (](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c9d56-150">For more information, see [sys.dm_os_memory_clerks (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql).</span></span>

##   <a name="managing-memory-consumed-by-memory-optimized-objects"></a><span data-ttu-id="c9d56-151">管理内存优化对象使用的内存</span><span class="sxs-lookup"><span data-stu-id="c9d56-151">Managing memory consumed by memory-optimized objects</span></span>
 <span data-ttu-id="c9d56-152">你可以按主题 [将具有内存优化表的数据库绑定至资源池](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)中所述，通过将内存优化表绑定到一个命名的资源池，控制内存优化表所占用的总内存。</span><span class="sxs-lookup"><span data-stu-id="c9d56-152">You can control the total memory consumed by memory-optimized tables by binding it to a named resource pool as described in the topic [Bind a Database with Memory-Optimized Tables to a Resource Pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md).</span></span>

##  <a name="troubleshooting-memory-issues"></a><span data-ttu-id="c9d56-153">排除内存问题</span><span class="sxs-lookup"><span data-stu-id="c9d56-153">Troubleshooting Memory Issues</span></span>
 <span data-ttu-id="c9d56-154">排除内存问题是一个由三个步骤构成的过程：</span><span class="sxs-lookup"><span data-stu-id="c9d56-154">Troubleshooting memory issues is a three step process:</span></span>

1.  <span data-ttu-id="c9d56-155">标识您的数据库或实例中对象所使用的内存量。</span><span class="sxs-lookup"><span data-stu-id="c9d56-155">Identify how much memory is being consumed by the objects in your database or instance.</span></span> <span data-ttu-id="c9d56-156">您可以使用上文中所述的可用于内存优化表的多种监视工具。</span><span class="sxs-lookup"><span data-stu-id="c9d56-156">You can use a rich set of monitoring tools available for memory-optimized tables as described earlier.</span></span>  <span data-ttu-id="c9d56-157">例如 DMV `sys.dm_db_xtp_table_memory_stats` 或 `sys.dm_os_memory_clerks`。</span><span class="sxs-lookup"><span data-stu-id="c9d56-157">For example the DMVs `sys.dm_db_xtp_table_memory_stats` or `sys.dm_os_memory_clerks`.</span></span>

2.  <span data-ttu-id="c9d56-158">确定内存使用的增长方式以及保留多少空间。</span><span class="sxs-lookup"><span data-stu-id="c9d56-158">Determine how memory consumption is growing and how much head room you have left.</span></span> <span data-ttu-id="c9d56-159">通过定期监视内存使用情况，可以知道内存使用的增长方式。</span><span class="sxs-lookup"><span data-stu-id="c9d56-159">By monitoring the memory consumption periodically, you can know how the memory use is growing.</span></span> <span data-ttu-id="c9d56-160">例如，如果您将数据库映射到了某一命名资源池，则可以监视性能计数器 Used Memory (KB) 来查看内存使用情况的增长方式。</span><span class="sxs-lookup"><span data-stu-id="c9d56-160">For example, if you have mapped the database to a named resource pool, you can monitor the performance counter Used Memory (KB) to see how memory usage is growing.</span></span>

3.  <span data-ttu-id="c9d56-161">可采取相应措施来缓解潜在的内存问题。</span><span class="sxs-lookup"><span data-stu-id="c9d56-161">Take action to mitigate the potential memory issues.</span></span> <span data-ttu-id="c9d56-162">有关详细信息，请参阅[解决内存不足问题](resolve-out-of-memory-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="c9d56-162">For more information, see [Resolve Out Of Memory Issues](resolve-out-of-memory-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c9d56-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c9d56-163">See Also</span></span>
 <span data-ttu-id="c9d56-164">将[具有内存优化表的数据库绑定到资源池](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)[更改 MIN_MEMORY_PERCENT 并在现有池中 MAX_MEMORY_PERCENT](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool)</span><span class="sxs-lookup"><span data-stu-id="c9d56-164">[Bind a Database with Memory-Optimized Tables to a Resource Pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) [Change MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT on an existing pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool)</span></span>


