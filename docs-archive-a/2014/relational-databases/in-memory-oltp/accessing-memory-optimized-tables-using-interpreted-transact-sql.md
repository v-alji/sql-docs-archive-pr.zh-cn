---
title: 使用解释型 Transact-SQL 访问内存优化表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 92a44d4d-0e53-4fb0-b890-de264c65c95a
author: rothja
ms.author: jroth
ms.openlocfilehash: af4b3ca7731e7ca13e697f43e76ac3cc3cacb4f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589562"
---
# <a name="accessing-memory-optimized-tables-using-interpreted-transact-sql"></a><span data-ttu-id="63963-102">使用解释型 Transact-SQL 访问内存优化表</span><span class="sxs-lookup"><span data-stu-id="63963-102">Accessing Memory-Optimized Tables Using Interpreted Transact-SQL</span></span>
  <span data-ttu-id="63963-103">除了少数例外情况，可以使用任何 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询或 DML 操作（SELECT、INSERT、UPDATE 或 DELETE）、即席批处理和 SQL 模块（如存储过程、表值函数、触发器和视图）来访问内存优化表。</span><span class="sxs-lookup"><span data-stu-id="63963-103">With only a few exceptions, you can access memory-optimized tables using any [!INCLUDE[tsql](../../includes/tsql-md.md)] query or DML operation (SELECT, INSERT, UPDATE, or DELETE), ad hoc batches, and SQL modules such as stored procedures, table-value functions, triggers, and views.</span></span>  
  
 <span data-ttu-id="63963-104">解释型 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批处理或是非本机编译的存储过程的存储过程。</span><span class="sxs-lookup"><span data-stu-id="63963-104">Interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] refers to [!INCLUDE[tsql](../../includes/tsql-md.md)] batches or stored procedures other than a natively compiled stored procedure.</span></span> <span data-ttu-id="63963-105">对内存优化表的解释型 [!INCLUDE[tsql](../../includes/tsql-md.md)] 访问称为互操作访问。</span><span class="sxs-lookup"><span data-stu-id="63963-105">Interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] access to memory-optimized tables is referred to as interop access.</span></span>  
  
 <span data-ttu-id="63963-106">内存优化表还可使用本机编译的存储过程访问。</span><span class="sxs-lookup"><span data-stu-id="63963-106">Memory-optimized tables can also be accessed using a natively compiled stored procedure.</span></span> <span data-ttu-id="63963-107">建议将本机编译的存储过程用于对性能至关重要的 OLTP 操作。</span><span class="sxs-lookup"><span data-stu-id="63963-107">Natively compiled stored procedures are recommended for performance-critical OLTP operations.</span></span>  
  
 <span data-ttu-id="63963-108">建议将解释型 [!INCLUDE[tsql](../../includes/tsql-md.md)] 访问用于以下情况：</span><span class="sxs-lookup"><span data-stu-id="63963-108">Interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] access is recommended for these scenarios:</span></span>  
  
-   <span data-ttu-id="63963-109">即席查询和管理任务。</span><span class="sxs-lookup"><span data-stu-id="63963-109">Ad hoc queries and administrative tasks.</span></span>  
  
-   <span data-ttu-id="63963-110">报表查询，通常使用本机编译的存储过程中不可用的构造（如窗口函数)。</span><span class="sxs-lookup"><span data-stu-id="63963-110">Reporting queries, which typically use constructs not available in natively compiled stored procedures (such as window functions).</span></span>  
  
-   <span data-ttu-id="63963-111">要将应用程序中对性能至关重要的部分迁移到内存优化表，只需极少的应用程序代码更改（或无需更改）。</span><span class="sxs-lookup"><span data-stu-id="63963-111">To migrate performance-critical parts of your application to memory-optimized tables, with minimal (or no) application code changes.</span></span> <span data-ttu-id="63963-112">通过迁移表可能会提高性能。</span><span class="sxs-lookup"><span data-stu-id="63963-112">You can potentially see performance improvements from migrating tables.</span></span> <span data-ttu-id="63963-113">如果随后将存储过程迁移到本机编译的存储过程，则可以进一步提高性能。</span><span class="sxs-lookup"><span data-stu-id="63963-113">If you then migrate stored procedures to natively compiled stored procedures, you may see further performance improvement.</span></span>  
  
-   <span data-ttu-id="63963-114">当 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句不可用于本机编译的存储过程时。</span><span class="sxs-lookup"><span data-stu-id="63963-114">When a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is not available for natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="63963-115">访问内存优化表中的数据的解释型 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程中不支持以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 构造。</span><span class="sxs-lookup"><span data-stu-id="63963-115">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] constructs are not supported in interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures that access data in a memory-optimized table.</span></span>  
  
|<span data-ttu-id="63963-116">区域</span><span class="sxs-lookup"><span data-stu-id="63963-116">Area</span></span>|<span data-ttu-id="63963-117">不支持</span><span class="sxs-lookup"><span data-stu-id="63963-117">Unsupported</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="63963-118">访问表</span><span class="sxs-lookup"><span data-stu-id="63963-118">Access to tables</span></span>|<span data-ttu-id="63963-119">TRUNCATE TABLE</span><span class="sxs-lookup"><span data-stu-id="63963-119">TRUNCATE TABLE</span></span><br /><br /> <span data-ttu-id="63963-120">MERGE（使用内存优化的表作为目标）</span><span class="sxs-lookup"><span data-stu-id="63963-120">MERGE (memory-optimized table as target)</span></span><br /><br /> <span data-ttu-id="63963-121">动态和键集游标（这些会自动降级为静态）。</span><span class="sxs-lookup"><span data-stu-id="63963-121">Dynamic and keyset cursors (these automatically degrade to static).</span></span><br /><br /> <span data-ttu-id="63963-122">使用上下文连接从 CLR 模块访问。</span><span class="sxs-lookup"><span data-stu-id="63963-122">Access from CLR modules, using the context connection.</span></span><br /><br /> <span data-ttu-id="63963-123">从索引视图引用内存优化表。</span><span class="sxs-lookup"><span data-stu-id="63963-123">Referencing a memory-optimized table from an indexed view.</span></span>|  
|<span data-ttu-id="63963-124">跨数据库</span><span class="sxs-lookup"><span data-stu-id="63963-124">Cross-database</span></span>|<span data-ttu-id="63963-125">跨数据库查询</span><span class="sxs-lookup"><span data-stu-id="63963-125">Cross-database queries</span></span><br /><br /> <span data-ttu-id="63963-126">跨数据库事务</span><span class="sxs-lookup"><span data-stu-id="63963-126">Cross-database transactions</span></span><br /><br /> <span data-ttu-id="63963-127">链接服务器</span><span class="sxs-lookup"><span data-stu-id="63963-127">Linked servers</span></span>|  
  
## <a name="table-hints"></a><span data-ttu-id="63963-128">表提示</span><span class="sxs-lookup"><span data-stu-id="63963-128">Table Hints</span></span>  
 <span data-ttu-id="63963-129">有关表提示的详细信息，请参阅。</span><span class="sxs-lookup"><span data-stu-id="63963-129">For more information about table hints, see.</span></span> <span data-ttu-id="63963-130">[表提示 (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-table)。</span><span class="sxs-lookup"><span data-stu-id="63963-130">[Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table).</span></span> <span data-ttu-id="63963-131">添加了 SNAPSHOT 隔离来支持 [!INCLUDE[hek_2](../../includes/hek-2-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="63963-131">SNAPSHOT isolation was added to support [!INCLUDE[hek_2](../../includes/hek-2-md.md)].</span></span>  
  
 <span data-ttu-id="63963-132">使用解释型 [!INCLUDE[tsql](../../includes/tsql-md.md)]访问内存优化表时，不支持以下表提示。</span><span class="sxs-lookup"><span data-stu-id="63963-132">The following table hints are not supported when accessing a memory-optimized table using interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="63963-133">HOLDLOCK</span><span class="sxs-lookup"><span data-stu-id="63963-133">HOLDLOCK</span></span>|<span data-ttu-id="63963-134">IGNORE_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="63963-134">IGNORE_CONSTRAINTS</span></span>|<span data-ttu-id="63963-135">IGNORE_TRIGGERS</span><span class="sxs-lookup"><span data-stu-id="63963-135">IGNORE_TRIGGERS</span></span>|<span data-ttu-id="63963-136">NOWAIT</span><span class="sxs-lookup"><span data-stu-id="63963-136">NOWAIT</span></span>|  
|<span data-ttu-id="63963-137">PAGLOCK</span><span class="sxs-lookup"><span data-stu-id="63963-137">PAGLOCK</span></span>|<span data-ttu-id="63963-138">READCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="63963-138">READCOMMITTED</span></span>|<span data-ttu-id="63963-139">READCOMMITTEDLOCK</span><span class="sxs-lookup"><span data-stu-id="63963-139">READCOMMITTEDLOCK</span></span>|<span data-ttu-id="63963-140">READPAST</span><span class="sxs-lookup"><span data-stu-id="63963-140">READPAST</span></span>|  
|<span data-ttu-id="63963-141">READUNCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="63963-141">READUNCOMMITTED</span></span>|<span data-ttu-id="63963-142">ROWLOCK</span><span class="sxs-lookup"><span data-stu-id="63963-142">ROWLOCK</span></span>|<span data-ttu-id="63963-143">SPATIAL_WINDOW_MAX_CELLS = *integer*</span><span class="sxs-lookup"><span data-stu-id="63963-143">SPATIAL_WINDOW_MAX_CELLS = *integer*</span></span>|<span data-ttu-id="63963-144">TABLOCK</span><span class="sxs-lookup"><span data-stu-id="63963-144">TABLOCK</span></span>|  
|<span data-ttu-id="63963-145">TABLOCKXX</span><span class="sxs-lookup"><span data-stu-id="63963-145">TABLOCKXX</span></span>|<span data-ttu-id="63963-146">UPDLOCK</span><span class="sxs-lookup"><span data-stu-id="63963-146">UPDLOCK</span></span>|<span data-ttu-id="63963-147">XLOCK</span><span class="sxs-lookup"><span data-stu-id="63963-147">XLOCK</span></span>||  
  
 <span data-ttu-id="63963-148">当使用解释型 [!INCLUDE[tsql](../../includes/tsql-md.md)] 从显式或隐式事务访问内存优化表时，必须包含隔离级别表提示（如 SNAPSHOT、REPEATABLEREAD 或 SERIALIZABLE），也可以使用 MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT。</span><span class="sxs-lookup"><span data-stu-id="63963-148">When accessing a memory-optimized table from an explicit or implicit transaction using interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] you must include either an isolation level table hint such as SNAPSHOT, REPEATABLEREAD, or SERIALIZABLE, or you can use MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT.</span></span> <span data-ttu-id="63963-149">有关详细信息，请参阅[带有内存优化表的事务隔离级别的准则](memory-optimized-tables.md)和[ALTER database SET 选项 &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)。</span><span class="sxs-lookup"><span data-stu-id="63963-149">For more information, see [Guidelines for Transaction Isolation Levels with Memory-Optimized Tables](memory-optimized-tables.md) and [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63963-150">由在自动提交模式下运行的查询访问的内存优化表不需要隔离级别表提示。</span><span class="sxs-lookup"><span data-stu-id="63963-150">An isolation level table hint is not required for memory-optimized tables accessed by queries running in auto-commit mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63963-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="63963-151">See Also</span></span>  
 <span data-ttu-id="63963-152">[对内存中 OLTP 的 Transact-SQL 支持](transact-sql-support-for-in-memory-oltp.md) </span><span class="sxs-lookup"><span data-stu-id="63963-152">[Transact-SQL Support for In-Memory OLTP](transact-sql-support-for-in-memory-oltp.md) </span></span>  
 [<span data-ttu-id="63963-153">迁移到内存中 OLTP</span><span class="sxs-lookup"><span data-stu-id="63963-153">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
