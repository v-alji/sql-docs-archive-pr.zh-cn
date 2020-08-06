---
title: 内存优化表 | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 14dddf81-b502-49dc-a6b6-d18b1ae32d2b
author: rothja
ms.author: jroth
ms.openlocfilehash: 73430505e55230daf31c492d882eadeb6d35d29f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693337"
---
# <a name="memory-optimized-tables"></a><span data-ttu-id="423ea-102">内存优化表</span><span class="sxs-lookup"><span data-stu-id="423ea-102">Memory-Optimized Tables</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="423ea-103">内存中 OLTP 通过高效的内存优化的数据访问、对业务逻辑的本机编译以及锁和闩锁释放算法帮助改进了 OLTP 应用程序的性能。</span><span class="sxs-lookup"><span data-stu-id="423ea-103">In-Memory OLTP helps improve performance of OLTP applications through efficient, memory-optimized data access, native compilation of business logic, and lock- and latch free algorithms.</span></span> <span data-ttu-id="423ea-104">内存中 OLTP 功能包括内存优化表和表类型，以及用于高效访问这些表的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程的本机编译。</span><span class="sxs-lookup"><span data-stu-id="423ea-104">The In-Memory OLTP feature includes memory-optimized tables and table types, as well as native compilation of [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures for efficient access to these tables.</span></span>  
  
 <span data-ttu-id="423ea-105">有关内存优化表的详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="423ea-105">For more information about memory-optimized tables, see:</span></span>  
  
-   [<span data-ttu-id="423ea-106">内存优化表简介</span><span class="sxs-lookup"><span data-stu-id="423ea-106">Introduction to Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
     <span data-ttu-id="423ea-107">详细介绍内存优化表的概念，并提供有关数据持久性、访问内存优化表中的数据以及性能和可伸缩性的信息。</span><span class="sxs-lookup"><span data-stu-id="423ea-107">Details what memory-optimized tables are and provides information about data durability, accessing data in memory-optimized tables, and performance and scalability.</span></span>  
  
-   [<span data-ttu-id="423ea-108">表和存储过程的本机编译</span><span class="sxs-lookup"><span data-stu-id="423ea-108">Native Compilation of Tables and Stored Procedures</span></span>](../in-memory-oltp/natively-compiled-stored-procedures.md)  
  
     <span data-ttu-id="423ea-109">详细介绍内存优化表和本机编译的存储过程如何编译为 DLL，并提供相关的安全注意事项。</span><span class="sxs-lookup"><span data-stu-id="423ea-109">Details how memory-optimized tables and natively compiled stored procedures are compiled into DLLs, and provides related security considerations.</span></span>  
  
-   [<span data-ttu-id="423ea-110">更改内存优化表</span><span class="sxs-lookup"><span data-stu-id="423ea-110">Altering Memory-Optimized Tables</span></span>](altering-memory-optimized-tables.md)  
  
     <span data-ttu-id="423ea-111">内存优化表更新准则（包括更改表列、索引和 bucket_count）。</span><span class="sxs-lookup"><span data-stu-id="423ea-111">Guidelines for updating memory-optimized tables (including changing table columns, indexes, and bucket_count).</span></span>  
  
-   [<span data-ttu-id="423ea-112">了解内存优化表的事务</span><span class="sxs-lookup"><span data-stu-id="423ea-112">Understanding Transactions on Memory-Optimized Tables</span></span>](../../database-engine/understanding-transactions-on-memory-optimized-tables.md)  
  
     <span data-ttu-id="423ea-113">本节提供有关在内存优化表上执行事务的若干主题，其中包括事务隔离级别和交叉容器事务。</span><span class="sxs-lookup"><span data-stu-id="423ea-113">This section provides several topics related to performing transactions on memory-optimized tables including transaction isolation levels, and cross-container transactions.</span></span>  
  
-   [<span data-ttu-id="423ea-114">用于对内存优化表进行分区的应用程序模式</span><span class="sxs-lookup"><span data-stu-id="423ea-114">Application Pattern for Partitioning Memory-Optimized Tables</span></span>](application-pattern-for-partitioning-memory-optimized-tables.md)  
  
     <span data-ttu-id="423ea-115">详细的代码示例，演示了如何使用内存优化表来模拟已分区表。</span><span class="sxs-lookup"><span data-stu-id="423ea-115">Detailed code sample that shows how to emulate partitioned tables when using memory-optimized tables.</span></span>  
  
-   [<span data-ttu-id="423ea-116">内存优化表的统计信息</span><span class="sxs-lookup"><span data-stu-id="423ea-116">Statistics for Memory-Optimized Tables</span></span>](statistics-for-memory-optimized-tables.md)  
  
     <span data-ttu-id="423ea-117">详细介绍如何为内存优化表编译统计信息，以及如何维护和手动更新内存优化表的统计信息。</span><span class="sxs-lookup"><span data-stu-id="423ea-117">Details how statistics are compiled for memory-optimized tables and how to maintain and manually update statistics for memory-optimized tables.</span></span>  
  
-   [<span data-ttu-id="423ea-118">排序规则和代码页</span><span class="sxs-lookup"><span data-stu-id="423ea-118">Collations and Code Pages</span></span>](../../database-engine/collations-and-code-pages.md)  
  
     <span data-ttu-id="423ea-119">详细介绍对内存优化表支持的排序规则和代码页的限制。</span><span class="sxs-lookup"><span data-stu-id="423ea-119">Details the restrictions on supported collations and code pages for memory-optimized tables.</span></span>  
  
-   [<span data-ttu-id="423ea-120">内存优化表中的表和行大小</span><span class="sxs-lookup"><span data-stu-id="423ea-120">Table and Row Size in Memory-Optimized Tables</span></span>](table-and-row-size-in-memory-optimized-tables.md)  
  
     <span data-ttu-id="423ea-121">详细介绍对内存优化表行的 8060 字节限制，并提供表和行大小计算的示例。</span><span class="sxs-lookup"><span data-stu-id="423ea-121">Details the 8060 byte limit on memory-optimized table rows, and provides an example for calculating table and row sizes.</span></span>  
  
-   [<span data-ttu-id="423ea-122">内存优化表查询处理指南</span><span class="sxs-lookup"><span data-stu-id="423ea-122">A Guide to Query Processing for Memory-Optimized Tables</span></span>](a-guide-to-query-processing-for-memory-optimized-tables.md)  
  
     <span data-ttu-id="423ea-123">简单介绍针对内存优化表和本机编译的存储过程的查询处理。</span><span class="sxs-lookup"><span data-stu-id="423ea-123">Provides an overview of query processing for both memory-optimized tables, and natively compiled stored procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="423ea-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="423ea-124">See Also</span></span>  
 [<span data-ttu-id="423ea-125">内存中 OLTP（内存中优化）</span><span class="sxs-lookup"><span data-stu-id="423ea-125">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](in-memory-oltp-in-memory-optimization.md)  
  
  
