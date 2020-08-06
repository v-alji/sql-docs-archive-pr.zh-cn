---
title: 了解内存优化表上的事务 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 06075248-705e-4563-9371-b64cd609793c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0671bba8b7a0bda27ea27cf059cb9e3b1bb87b2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690019"
---
# <a name="understanding-transactions-on-memory-optimized-tables"></a><span data-ttu-id="65daa-102">了解内存优化表的事务</span><span class="sxs-lookup"><span data-stu-id="65daa-102">Understanding Transactions on Memory-Optimized Tables</span></span>
  <span data-ttu-id="65daa-103">事务使用一种乐观多版本并发控制形式来访问内存优化表。</span><span class="sxs-lookup"><span data-stu-id="65daa-103">Transactions access memory-optimized tables using a form of optimistic, multi-version concurrency control.</span></span> <span data-ttu-id="65daa-104">这意味着存在不同版本的数据。</span><span class="sxs-lookup"><span data-stu-id="65daa-104">This means that there are different versions of the data.</span></span> <span data-ttu-id="65daa-105">每个事务都对自己的事务一致数据库版本进行操作（独立于其他并发运行的事务）。</span><span class="sxs-lookup"><span data-stu-id="65daa-105">Each transaction operates on its own transactionally consistent version of the database, independent from other concurrently running transactions.</span></span> <span data-ttu-id="65daa-106">此外，事务还在与其他并发事务不冲突的乐观假设下运行。</span><span class="sxs-lookup"><span data-stu-id="65daa-106">In addition, transactions operate under the optimistic assumption that there will be no conflicts with other, concurrent, transactions.</span></span> <span data-ttu-id="65daa-107">这样就无需使用锁，但需要系统检测冲突并终止冲突事务中的一个事务。</span><span class="sxs-lookup"><span data-stu-id="65daa-107">This avoids the need to use locks, but does require the system to detect conflicts and terminate one of the conflicting transactions.</span></span> <span data-ttu-id="65daa-108">仅对于写/写事务和读/写事务会发生冲突。</span><span class="sxs-lookup"><span data-stu-id="65daa-108">Conflicts can occur only for write-write transactions and for read-write transactions.</span></span> <span data-ttu-id="65daa-109">如果存在写/写冲突，则终止一个写入事务。</span><span class="sxs-lookup"><span data-stu-id="65daa-109">If there is a write-write conflict, one write transaction is terminated.</span></span>  
  
 <span data-ttu-id="65daa-110">内存优化表的并发控制与基于磁盘的表的并发控制在 READ_COMMITTED_SNAPSHOT 和 SNAPSHOT 事务隔离级别之间存在相似性。</span><span class="sxs-lookup"><span data-stu-id="65daa-110">There are similarities between the concurrency control for memory-optimized tables and the concurrency control for disk-based tables for the READ_COMMITTED_SNAPSHOT and SNAPSHOT transaction isolation levels.</span></span> <span data-ttu-id="65daa-111"> (有关基于磁盘的表的详细信息，请参阅[数据库引擎中基于行版本控制的隔离级别](https://msdn.microsoft.com/library/ms177404\(v=sql.100\).aspx)。 ) </span><span class="sxs-lookup"><span data-stu-id="65daa-111">(For more information about disk-based tables, see [Row Versioning-based Isolation Levels in the Database Engine](https://msdn.microsoft.com/library/ms177404\(v=sql.100\).aspx).)</span></span>  
  
## <a name="topics-in-this-section"></a><span data-ttu-id="65daa-112">本节中的主题</span><span class="sxs-lookup"><span data-stu-id="65daa-112">Topics in This Section</span></span>  
 <span data-ttu-id="65daa-113">本节说明了内存优化表中的事务，包含以下主题：</span><span class="sxs-lookup"><span data-stu-id="65daa-113">This section on transactions in memory-optimized tables includes the following topics:</span></span>  
  
-   [<span data-ttu-id="65daa-114">内存优化表事务隔离级别准则</span><span class="sxs-lookup"><span data-stu-id="65daa-114">Guidelines for Transaction Isolation Levels with Memory-Optimized Tables</span></span>](../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
  
-   [<span data-ttu-id="65daa-115">内存优化表事务重试逻辑准则</span><span class="sxs-lookup"><span data-stu-id="65daa-115">Guidelines for Retry Logic for Transactions on Memory-Optimized Tables</span></span>](guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md)  
  
-   [<span data-ttu-id="65daa-116">内存优化表中的事务</span><span class="sxs-lookup"><span data-stu-id="65daa-116">Transactions in Memory-Optimized Tables</span></span>](transactions-in-memory-optimized-tables.md)  
  
-   [<span data-ttu-id="65daa-117">事务隔离级别</span><span class="sxs-lookup"><span data-stu-id="65daa-117">Transaction Isolation Levels</span></span>](transaction-isolation-levels.md)  
  
-   [<span data-ttu-id="65daa-118">跨容器事务</span><span class="sxs-lookup"><span data-stu-id="65daa-118">Cross-Container Transactions</span></span>](cross-container-transactions.md)  
  
 <span data-ttu-id="65daa-119">有关详细信息，请参阅[控制事务持续性](../relational-databases/logs/control-transaction-durability.md)。</span><span class="sxs-lookup"><span data-stu-id="65daa-119">For more information, see [Control Transaction Durability](../relational-databases/logs/control-transaction-durability.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65daa-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="65daa-120">See Also</span></span>  
 [<span data-ttu-id="65daa-121">Memory-Optimized Tables</span><span class="sxs-lookup"><span data-stu-id="65daa-121">Memory-Optimized Tables</span></span>](../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
  
  
