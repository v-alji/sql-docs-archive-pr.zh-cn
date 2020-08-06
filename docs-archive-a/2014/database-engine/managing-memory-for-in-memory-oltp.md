---
title: 管理内存中 OLTP 的内存 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: d82f21fa-6be1-4723-a72e-f2526fafd1b6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 90f9b638697d59a0a573a9a31c0a5faade23e870
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692508"
---
# <a name="managing-memory-for-in-memory-oltp"></a><span data-ttu-id="f08ae-102">管理内存中 OLTP 的内存</span><span class="sxs-lookup"><span data-stu-id="f08ae-102">Managing Memory for In-Memory OLTP</span></span>
  <span data-ttu-id="f08ae-103">内存优化表要求存在足够的内存，以便将所有行和索引保留在内存中。</span><span class="sxs-lookup"><span data-stu-id="f08ae-103">Memory-optimized tables require that sufficient memory exist to keep all of the rows and indexes in memory.</span></span> <span data-ttu-id="f08ae-104">因为内存是有限的资源，所以了解和管理系统的内存使用情况非常重要。</span><span class="sxs-lookup"><span data-stu-id="f08ae-104">Because memory is a finite resource, it is important that you understand and manage memory usage on your system.</span></span> <span data-ttu-id="f08ae-105">本节中的主题介绍一些常见的内存使用和管理方案。</span><span class="sxs-lookup"><span data-stu-id="f08ae-105">The topics in this section cover common memory use and management scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f08ae-106">本部分内容</span><span class="sxs-lookup"><span data-stu-id="f08ae-106">In this section</span></span>  
  
|<span data-ttu-id="f08ae-107">部分</span><span class="sxs-lookup"><span data-stu-id="f08ae-107">Section</span></span>|<span data-ttu-id="f08ae-108">说明</span><span class="sxs-lookup"><span data-stu-id="f08ae-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f08ae-109">估算内存优化表的内存需求</span><span class="sxs-lookup"><span data-stu-id="f08ae-109">Estimate Memory Requirements for Memory-Optimized Tables</span></span>](../relational-databases/in-memory-oltp/memory-optimized-tables.md)|<span data-ttu-id="f08ae-110">估计表的内存需求。</span><span class="sxs-lookup"><span data-stu-id="f08ae-110">Estimate a table's memory needs.</span></span>|  
|[<span data-ttu-id="f08ae-111">将具有内存优化表的数据库绑定至资源池</span><span class="sxs-lookup"><span data-stu-id="f08ae-111">Bind a Database with Memory-Optimized Tables to a Resource Pool</span></span>](../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)|<span data-ttu-id="f08ae-112">将数据库与资源池绑定的分步演练。</span><span class="sxs-lookup"><span data-stu-id="f08ae-112">Step by step walkthrough to bind a database with a resource pool.</span></span>|  
|[<span data-ttu-id="f08ae-113">内存使用情况的监视和故障排除</span><span class="sxs-lookup"><span data-stu-id="f08ae-113">Monitor and Troubleshoot Memory Usage</span></span>](../relational-databases/in-memory-oltp/monitor-and-troubleshoot-memory-usage.md)|<span data-ttu-id="f08ae-114">可用于监视内存使用情况的工具。</span><span class="sxs-lookup"><span data-stu-id="f08ae-114">Tools you can use to monitor your memory usage.</span></span> <span data-ttu-id="f08ae-115">另外介绍内存使用量过高时的故障排除。</span><span class="sxs-lookup"><span data-stu-id="f08ae-115">Also covers troubleshooting if memory usage gets too high.</span></span>|  
|[<span data-ttu-id="f08ae-116">解决内存不足问题</span><span class="sxs-lookup"><span data-stu-id="f08ae-116">Resolve Out Of Memory Issues</span></span>](../relational-databases/in-memory-oltp/resolve-out-of-memory-issues.md)|<span data-ttu-id="f08ae-117">从 OOM（内存不足）情况恢复的步骤。</span><span class="sxs-lookup"><span data-stu-id="f08ae-117">Steps to recover from an OOM (Out of Memory) situation.</span></span>|  
|[<span data-ttu-id="f08ae-118">还原数据库并将它绑定到资源池</span><span class="sxs-lookup"><span data-stu-id="f08ae-118">Restore a Database and Bind it to a Resource Pool</span></span>](../relational-databases/in-memory-oltp/restore-a-database-and-bind-it-to-a-resource-pool.md)|<span data-ttu-id="f08ae-119">还原 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 数据库并将其绑定到指定资源池的步骤。</span><span class="sxs-lookup"><span data-stu-id="f08ae-119">Steps to restore an [!INCLUDE[hek_2](../includes/hek-2-md.md)] database and bind it to a named resource pool.</span></span>|  
|[<span data-ttu-id="f08ae-120">内存中 OLTP 垃圾回收</span><span class="sxs-lookup"><span data-stu-id="f08ae-120">In-Memory OLTP Garbage Collection</span></span>](../relational-databases/in-memory-oltp/in-memory-oltp-garbage-collection.md)|<span data-ttu-id="f08ae-121">理解如何对已删除的行运行垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="f08ae-121">Understand how garbage collection operates on deleted rows.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f08ae-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f08ae-122">See Also</span></span>  
 [<span data-ttu-id="f08ae-123">内存中 OLTP（内存中优化）</span><span class="sxs-lookup"><span data-stu-id="f08ae-123">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
