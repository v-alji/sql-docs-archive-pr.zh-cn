---
title: XTP 游标 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 84bf4654-3ef7-4d7f-a269-c8bb4ed4acad
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 217a1196717492cb92adb24eaf7c06c8867abc2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691181"
---
# <a name="xtp-cursors"></a><span data-ttu-id="e7667-102">XTP 游标</span><span class="sxs-lookup"><span data-stu-id="e7667-102">XTP Cursors</span></span>
  <span data-ttu-id="e7667-103">XTP 游标性能对象包含与内部 XTP 引擎游标相关的计数器。</span><span class="sxs-lookup"><span data-stu-id="e7667-103">The XTP Cursors performance object contains counters related to internal XTP engine cursors.</span></span> <span data-ttu-id="e7667-104">游标是 XTP 引擎用于处理 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询的低级构建基块。</span><span class="sxs-lookup"><span data-stu-id="e7667-104">Cursors are the low-level building blocks the XTP engine uses to process [!INCLUDE[tsql](../../includes/tsql-md.md)] queries.</span></span> <span data-ttu-id="e7667-105">因此，您通常不能直接控制游标。</span><span class="sxs-lookup"><span data-stu-id="e7667-105">As such, you do not typically have direct control over them.</span></span>  
  
 <span data-ttu-id="e7667-106">下表介绍了**XTP 游标**计数器。</span><span class="sxs-lookup"><span data-stu-id="e7667-106">This table describes the **XTP Cursors** counters.</span></span>  
  
|<span data-ttu-id="e7667-107">计数器</span><span class="sxs-lookup"><span data-stu-id="e7667-107">Counter</span></span>|<span data-ttu-id="e7667-108">说明</span><span class="sxs-lookup"><span data-stu-id="e7667-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e7667-109">**游标删除数/秒**</span><span class="sxs-lookup"><span data-stu-id="e7667-109">**Cursor deletes/sec**</span></span>|<span data-ttu-id="e7667-110">每秒游标删除数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="e7667-110">The number of cursor deletes (on average), per second.</span></span>|  
|<span data-ttu-id="e7667-111">**游标插入数/秒**</span><span class="sxs-lookup"><span data-stu-id="e7667-111">**Cursor inserts/sec**</span></span>|<span data-ttu-id="e7667-112">每秒游标插入数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="e7667-112">The number of cursor inserts (on average), per second.</span></span>|  
|<span data-ttu-id="e7667-113">**启动的游标扫描数/秒**</span><span class="sxs-lookup"><span data-stu-id="e7667-113">**Cursor scans started /sec**</span></span>|<span data-ttu-id="e7667-114">每秒启动的游标扫描数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="e7667-114">The number of cursor scans started (on average), per second.</span></span>|  
|<span data-ttu-id="e7667-115">**游标唯一冲突数/秒**</span><span class="sxs-lookup"><span data-stu-id="e7667-115">**Cursor unique violations/sec**</span></span>|<span data-ttu-id="e7667-116">每秒唯一约束冲突数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="e7667-116">The number of unique-constraint violations (on average), per second.</span></span>|  
|<span data-ttu-id="e7667-117">**游标更新数/秒**</span><span class="sxs-lookup"><span data-stu-id="e7667-117">**Cursor updates/sec**</span></span>|<span data-ttu-id="e7667-118">每秒游标更新数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="e7667-118">The number of cursor updates (on average), per second.</span></span>|  
|<span data-ttu-id="e7667-119">**游标写冲突数/秒**</span><span class="sxs-lookup"><span data-stu-id="e7667-119">**Cursor write   conflicts/sec**</span></span>|<span data-ttu-id="e7667-120">同一行版本每秒发生的写/写冲突数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="e7667-120">The number of write-write conflicts to the same row version (on average), per second.</span></span>|  
|<span data-ttu-id="e7667-121">**灰尘角扫描重试次数/秒（用户发出）**</span><span class="sxs-lookup"><span data-stu-id="e7667-121">**Dusty corner scan retries/sec (user-issued)**</span></span>|<span data-ttu-id="e7667-122">在用户全表扫描发出的灰尘角扫描期间，由于写冲突而进行的每秒扫描重试次数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="e7667-122">The number of scan retries due to write conflicts during dusty corner sweeps issued by a user's full-table scan (on average), per second.</span></span> <span data-ttu-id="e7667-123">此为非常低级的计数器，不适合客户使用。</span><span class="sxs-lookup"><span data-stu-id="e7667-123">This is a very low-level counter, not intended for customer use.</span></span>|  
|<span data-ttu-id="e7667-124">**删除的过期行数/秒**</span><span class="sxs-lookup"><span data-stu-id="e7667-124">**Expired rows removed/sec**</span></span>|<span data-ttu-id="e7667-125">游标每秒删除的过期行数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="e7667-125">The number of expired rows removed by cursors (on average), per second.</span></span>|  
|<span data-ttu-id="e7667-126">**接触的过期行数/秒**</span><span class="sxs-lookup"><span data-stu-id="e7667-126">**Expired rows touched/sec**</span></span>|<span data-ttu-id="e7667-127">游标每秒接触的过期行数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="e7667-127">The number of expired rows touched by cursors (on average), per second.</span></span>|  
|<span data-ttu-id="e7667-128">**返回的行数/秒**</span><span class="sxs-lookup"><span data-stu-id="e7667-128">**Rows returned/sec**</span></span>|<span data-ttu-id="e7667-129">游标每秒返回的行数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="e7667-129">The number of rows returned by cursors (on average), per second.</span></span>|  
|<span data-ttu-id="e7667-130">**接触的行数/秒**</span><span class="sxs-lookup"><span data-stu-id="e7667-130">**Rows touched/sec**</span></span>|<span data-ttu-id="e7667-131">游标每秒接触的行数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="e7667-131">The number of rows touched by cursors (on average), per second.</span></span>|  
|<span data-ttu-id="e7667-132">**接触的临时删除行数/秒**</span><span class="sxs-lookup"><span data-stu-id="e7667-132">**Tentatively-deleted rows touched/sec**</span></span>|<span data-ttu-id="e7667-133">游标每秒接触的即将到期的行数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="e7667-133">The number of expiring rows touched by cursors (on average), per second.</span></span> <span data-ttu-id="e7667-134">如果删除行的事务仍处于活动状态（即尚未提交或中止），则此行即将到期。</span><span class="sxs-lookup"><span data-stu-id="e7667-134">A row is expiring if the transaction that deleted it is still active (i.e. has not yet committed or aborted.)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7667-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7667-135">See Also</span></span>  
 [<span data-ttu-id="e7667-136">XTP &#40;内存中 OLTP&#41; 性能计数器</span><span class="sxs-lookup"><span data-stu-id="e7667-136">XTP &#40;In-Memory OLTP&#41; Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)  
  
  
