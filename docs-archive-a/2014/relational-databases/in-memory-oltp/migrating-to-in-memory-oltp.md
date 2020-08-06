---
title: 迁移到内存中 OLTP | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 405cdac5-a0d4-47a4-9180-82876b773b82
author: rothja
ms.author: jroth
ms.openlocfilehash: ed764ce52d41d76667213b846cec51b26f634a27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693884"
---
# <a name="migrating-to-in-memory-oltp"></a><span data-ttu-id="466fa-102">迁移到内存中 OLTP</span><span class="sxs-lookup"><span data-stu-id="466fa-102">Migrating to In-Memory OLTP</span></span>
  <span data-ttu-id="466fa-103">本节论述如何迁移数据库对象以便使用内存中 OLTP。</span><span class="sxs-lookup"><span data-stu-id="466fa-103">This section discusses how to migrate database objects to use In-Memory OLTP.</span></span>  
  
-   [<span data-ttu-id="466fa-104">确定表或存储过程是否应移植到内存中 OLTP</span><span class="sxs-lookup"><span data-stu-id="466fa-104">Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP</span></span>](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)  
  
-   [<span data-ttu-id="466fa-105">内存优化顾问</span><span class="sxs-lookup"><span data-stu-id="466fa-105">Memory Optimization Advisor</span></span>](memory-optimization-advisor.md)  
  
-   [<span data-ttu-id="466fa-106">本机编译顾问</span><span class="sxs-lookup"><span data-stu-id="466fa-106">Native Compilation Advisor</span></span>](native-compilation-advisor.md)  
  
-   [<span data-ttu-id="466fa-107">内存中 OLTP 不支持的 Transact-SQL 构造</span><span class="sxs-lookup"><span data-stu-id="466fa-107">Transact-SQL Constructs Not Supported by In-Memory OLTP</span></span>](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
-   [<span data-ttu-id="466fa-108">在内存优化的表中实现 LOB 列</span><span class="sxs-lookup"><span data-stu-id="466fa-108">Implementing LOB Columns in a Memory-Optimized Table</span></span>](../../database-engine/implementing-lob-columns-in-a-memory-optimized-table.md)  
  
-   [<span data-ttu-id="466fa-109">在内存优化的表中实现 SQL_VARIANT</span><span class="sxs-lookup"><span data-stu-id="466fa-109">Implementing SQL_VARIANT in a Memory-Optimized Table</span></span>](implementing-sql-variant-in-a-memory-optimized-table.md)  
  
-   [<span data-ttu-id="466fa-110">本机编译存储过程的迁移问题</span><span class="sxs-lookup"><span data-stu-id="466fa-110">Migration Issues for Natively Compiled Stored Procedures</span></span>](migration-issues-for-natively-compiled-stored-procedures.md)  
  
-   [<span data-ttu-id="466fa-111">迁移计算列</span><span class="sxs-lookup"><span data-stu-id="466fa-111">Migrating Computed Columns</span></span>](migrating-computed-columns.md)  
  
-   [<span data-ttu-id="466fa-112">迁移触发器</span><span class="sxs-lookup"><span data-stu-id="466fa-112">Migrating Triggers</span></span>](migrating-triggers.md)  
  
-   [<span data-ttu-id="466fa-113">跨数据库查询</span><span class="sxs-lookup"><span data-stu-id="466fa-113">Cross-Database Queries</span></span>](cross-database-queries.md)  
  
-   [<span data-ttu-id="466fa-114">迁移检查约束和外键约束</span><span class="sxs-lookup"><span data-stu-id="466fa-114">Migrating Check and Foreign Key Constraints</span></span>](../../database-engine/migrating-check-and-foreign-key-constraints.md)  
  
-   [<span data-ttu-id="466fa-115">在内存优化的表中实现 IDENTITY</span><span class="sxs-lookup"><span data-stu-id="466fa-115">Implementing IDENTITY in a Memory-Optimized Table</span></span>](implementing-identity-in-a-memory-optimized-table.md)  
  
 <span data-ttu-id="466fa-116">有关迁移方法的信息，请参阅 [内存中 OLTP - 常见的工作负荷模式和迁移注意事项](https://msdn.microsoft.com/library/dn673538.aspx)。</span><span class="sxs-lookup"><span data-stu-id="466fa-116">For information about migration methodologies, see [In-Memory OLTP - Common Workload Patterns and Migration Considerations](https://msdn.microsoft.com/library/dn673538.aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="466fa-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="466fa-117">See Also</span></span>  
 <span data-ttu-id="466fa-118">[内存中 OLTP（内存中优化）](in-memory-oltp-in-memory-optimization.md) </span><span class="sxs-lookup"><span data-stu-id="466fa-118">[In-Memory OLTP &#40;In-Memory Optimization&#41;](in-memory-oltp-in-memory-optimization.md) </span></span>  
 [<span data-ttu-id="466fa-119">估算内存优化表的内存需求</span><span class="sxs-lookup"><span data-stu-id="466fa-119">Estimate Memory Requirements for Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
  
