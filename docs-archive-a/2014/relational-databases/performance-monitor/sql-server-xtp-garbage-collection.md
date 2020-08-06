---
title: XTP 垃圾回收 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 64ae91e5-b420-44b4-af1a-f8bca83d7f41
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 341a45c1c103f154672bb01a0648339562ee9750
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688864"
---
# <a name="xtp-garbage-collection"></a><span data-ttu-id="66dff-102">XTP 垃圾收集</span><span class="sxs-lookup"><span data-stu-id="66dff-102">XTP Garbage Collection</span></span>
  <span data-ttu-id="66dff-103">XTP 垃圾收集性能对象包含与 XTP 引擎的垃圾收集器相关的计数器。</span><span class="sxs-lookup"><span data-stu-id="66dff-103">The XTP Garbage Collection performance object contains counters related to the XTP engine's garbage collector.</span></span>  
  
 <span data-ttu-id="66dff-104">下表介绍了**XTP 垃圾回收**计数器。</span><span class="sxs-lookup"><span data-stu-id="66dff-104">This table describes the **XTP garbage Collection** counters.</span></span>  
  
|<span data-ttu-id="66dff-105">计数器</span><span class="sxs-lookup"><span data-stu-id="66dff-105">Counter</span></span>|<span data-ttu-id="66dff-106">说明</span><span class="sxs-lookup"><span data-stu-id="66dff-106">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="66dff-107">**灰尘角扫描重试次数/秒（垃圾收集器发出）**</span><span class="sxs-lookup"><span data-stu-id="66dff-107">**Dusty corner scan retries/sec (GC-issued)**</span></span>|<span data-ttu-id="66dff-108">在垃圾收集器发出的灰尘角扫描期间，由于写冲突而进行的每秒扫描重试次数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="66dff-108">The number of scan retries due to write conflicts during dusty corner sweeps issued by the garbage collector (on average), per second.</span></span> <span data-ttu-id="66dff-109">此为非常低级的计数器，不适合客户使用。</span><span class="sxs-lookup"><span data-stu-id="66dff-109">This is a very low-level counter, not intended for customer use.</span></span>|  
|<span data-ttu-id="66dff-110">**主垃圾收集器工作项数/秒**</span><span class="sxs-lookup"><span data-stu-id="66dff-110">**Main GC work items/sec**</span></span>|<span data-ttu-id="66dff-111">主垃圾收集器线程处理的工作项数。</span><span class="sxs-lookup"><span data-stu-id="66dff-111">The number of work items processed by the main GC thread.</span></span>|  
|<span data-ttu-id="66dff-112">**并行垃圾收集器工作项数/秒**</span><span class="sxs-lookup"><span data-stu-id="66dff-112">**Parallel GC work item/sec**</span></span>|<span data-ttu-id="66dff-113">并行线程执行垃圾收集器工作项的次数。</span><span class="sxs-lookup"><span data-stu-id="66dff-113">The number of times a parallel thread has executed a GC work item.</span></span>|  
|<span data-ttu-id="66dff-114">**处理的行数/秒**</span><span class="sxs-lookup"><span data-stu-id="66dff-114">**Rows processed/sec**</span></span>|<span data-ttu-id="66dff-115">垃圾收集器每秒处理的行数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="66dff-115">The number of rows processed by the garbage collector (on average), per second.</span></span>|  
|<span data-ttu-id="66dff-116">**处理的行数/秒（桶中的第一行并能删除）**</span><span class="sxs-lookup"><span data-stu-id="66dff-116">**Rows processed/sec (first in bucket and removed)**</span></span>|<span data-ttu-id="66dff-117">垃圾收集器每秒处理的、在相应哈希桶中是第一行并能立即删除的行数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="66dff-117">The number of rows processed by the garbage collector that were first in the corresponding hash bucket, and were able to be removed immediately (on average), per second.</span></span>|  
|<span data-ttu-id="66dff-118">**处理的行数/秒（桶中的第一行）**</span><span class="sxs-lookup"><span data-stu-id="66dff-118">**Rows processed/sec (first in bucket)**</span></span>|<span data-ttu-id="66dff-119">垃圾收集器每秒处理的、在相应哈希桶中是第一行的行数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="66dff-119">The number of rows processed by the garbage collector that were first in the corresponding hash bucket (on average), per second.</span></span>|  
|<span data-ttu-id="66dff-120">**处理的行数/秒（标记为取消链接）**</span><span class="sxs-lookup"><span data-stu-id="66dff-120">**Rows processed/sec (marked for unlink)**</span></span>|<span data-ttu-id="66dff-121">垃圾收集器每秒处理的、已标记为取消链接的行数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="66dff-121">The number of rows processed by the garbage collector that were already marked for unlink (on average), per second.</span></span>|  
|<span data-ttu-id="66dff-122">**处理的行数/秒（无需扫描）**</span><span class="sxs-lookup"><span data-stu-id="66dff-122">**Rows processed/sec (no sweep needed)**</span></span>|<span data-ttu-id="66dff-123">垃圾收集器每秒处理的、无需灰尘角扫描的行数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="66dff-123">The number of rows processed by the garbage collector that will not require a dusty corner sweep (on average), per second.</span></span>|  
|<span data-ttu-id="66dff-124">**扫描中删除的过期行数/秒**</span><span class="sxs-lookup"><span data-stu-id="66dff-124">**Sweep expired rows removed/sec**</span></span>|<span data-ttu-id="66dff-125">灰尘角扫描期间每秒删除的过期行数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="66dff-125">The number of expired rows removed during dusty corner sweeps (on average), per second.</span></span>|  
|<span data-ttu-id="66dff-126">**扫描中接触的过期行数/秒**</span><span class="sxs-lookup"><span data-stu-id="66dff-126">**Sweep expired rows touched/sec**</span></span>|<span data-ttu-id="66dff-127">灰尘角扫描期间每秒接触的过期行数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="66dff-127">The number of expired rows touched during dusty corner sweeps (on average), per second.</span></span>|  
|<span data-ttu-id="66dff-128">**扫描中接触的即将到期的行数/秒**</span><span class="sxs-lookup"><span data-stu-id="66dff-128">**Sweep expiring rows touched/sec**</span></span>|<span data-ttu-id="66dff-129">灰尘角扫描期间每秒接触的即将到期的行数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="66dff-129">The number of expiring rows touched during dusty corner sweeps (on average), per second.</span></span>|  
|<span data-ttu-id="66dff-130">**扫描中接触的行数/秒**</span><span class="sxs-lookup"><span data-stu-id="66dff-130">**Sweep rows touched/sec**</span></span>|<span data-ttu-id="66dff-131">灰尘角扫描期间每秒接触的行数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="66dff-131">The number of rows touched during dusty corner sweeps (on average), per second.</span></span>|  
|<span data-ttu-id="66dff-132">**启动的扫描数/秒**</span><span class="sxs-lookup"><span data-stu-id="66dff-132">**Sweep scans started/sec**</span></span>|<span data-ttu-id="66dff-133">每秒启动的灰尘角扫描数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="66dff-133">The number of dusty corner sweep scans started (on average), per second.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="66dff-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="66dff-134">See Also</span></span>  
 [<span data-ttu-id="66dff-135">XTP &#40;内存中 OLTP&#41; 性能计数器</span><span class="sxs-lookup"><span data-stu-id="66dff-135">XTP &#40;In-Memory OLTP&#41; Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)  
  
  
