---
title: SQL Server - Cursor Manager by Type 对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Cursor Manager by Type object
- SQLServer:Cursor Manager by Type
ms.assetid: d67fbd8a-7554-4a16-96f1-d9ee857a95e3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7bee15aa2917f7b8890e6c1d3f26cc0e210208a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578839"
---
# <a name="sql-server-cursor-manager-by-type-object"></a><span data-ttu-id="ff822-102">SQL Server Cursor Manager by Type 对象</span><span class="sxs-lookup"><span data-stu-id="ff822-102">SQL Server, Cursor Manager by Type Object</span></span>
  <span data-ttu-id="ff822-103">**SQLServer:Cursor Manager by Type** 对象提供计数器（按类型分组）来监视游标。</span><span class="sxs-lookup"><span data-stu-id="ff822-103">The **SQLServer:Cursor Manager by Type** object provides counters to monitor cursors, grouped by type.</span></span>  
  
 <span data-ttu-id="ff822-104">此表介绍了 SQL Server **Cursor Manager by Type** 计数器。</span><span class="sxs-lookup"><span data-stu-id="ff822-104">This table describes the SQL Server **Cursor Manager by Type** counters.</span></span>  
  
|<span data-ttu-id="ff822-105">Cursor Manager by Type 计数器</span><span class="sxs-lookup"><span data-stu-id="ff822-105">Cursor Manager by Type counters</span></span>|<span data-ttu-id="ff822-106">说明</span><span class="sxs-lookup"><span data-stu-id="ff822-106">Description</span></span>|  
|-------------------------------------|-----------------|  
|<span data-ttu-id="ff822-107">**Active cursors**</span><span class="sxs-lookup"><span data-stu-id="ff822-107">**Active cursors**</span></span>|<span data-ttu-id="ff822-108">活动游标数。</span><span class="sxs-lookup"><span data-stu-id="ff822-108">Number of active cursors.</span></span>|  
|<span data-ttu-id="ff822-109">**Cache Hit Ratio**</span><span class="sxs-lookup"><span data-stu-id="ff822-109">**Cache Hit Ratio**</span></span>|<span data-ttu-id="ff822-110">高速缓存命中次数和查找次数的比率。</span><span class="sxs-lookup"><span data-stu-id="ff822-110">Ratio between cache hits and lookups.</span></span>|  
|<span data-ttu-id="ff822-111">**Cached Cursor Counts**</span><span class="sxs-lookup"><span data-stu-id="ff822-111">**Cached Cursor Counts**</span></span>|<span data-ttu-id="ff822-112">缓存中给定类型的游标数。</span><span class="sxs-lookup"><span data-stu-id="ff822-112">Number of cursors of a given type in the cache.</span></span>|  
|<span data-ttu-id="ff822-113">**Cursor Cache Use Count/sec**</span><span class="sxs-lookup"><span data-stu-id="ff822-113">**Cursor Cache Use Count/sec**</span></span>|<span data-ttu-id="ff822-114">每种缓存的游标的使用次数。</span><span class="sxs-lookup"><span data-stu-id="ff822-114">Times each type of cached cursor has been used.</span></span>|  
|<span data-ttu-id="ff822-115">**Cursor memory usage**</span><span class="sxs-lookup"><span data-stu-id="ff822-115">**Cursor memory usage**</span></span>|<span data-ttu-id="ff822-116">游标占用的内存量 (KB)。</span><span class="sxs-lookup"><span data-stu-id="ff822-116">Amount of memory consumed by cursors in kilobytes (KB).</span></span>|  
|<span data-ttu-id="ff822-117">**Cursor Requests/sec**</span><span class="sxs-lookup"><span data-stu-id="ff822-117">**Cursor Requests/sec**</span></span>|<span data-ttu-id="ff822-118">服务器收到的 SQL 游标请求数。</span><span class="sxs-lookup"><span data-stu-id="ff822-118">Number of SQL cursor requests received by server.</span></span>|  
|<span data-ttu-id="ff822-119">**Cursor worktable usage**</span><span class="sxs-lookup"><span data-stu-id="ff822-119">**Cursor worktable usage**</span></span>|<span data-ttu-id="ff822-120">游标使用的工作表数。</span><span class="sxs-lookup"><span data-stu-id="ff822-120">Number of worktables used by cursors.</span></span>|  
|<span data-ttu-id="ff822-121">**Number of active cursor plans**</span><span class="sxs-lookup"><span data-stu-id="ff822-121">**Number of active cursor plans**</span></span>|<span data-ttu-id="ff822-122">游标计划数。</span><span class="sxs-lookup"><span data-stu-id="ff822-122">Number of cursor plans.</span></span>|  
  
 <span data-ttu-id="ff822-123">对象中的每个计数器均包含以下实例：</span><span class="sxs-lookup"><span data-stu-id="ff822-123">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="ff822-124">Cursor Manager 实例</span><span class="sxs-lookup"><span data-stu-id="ff822-124">Cursor Manager instance</span></span>|<span data-ttu-id="ff822-125">说明</span><span class="sxs-lookup"><span data-stu-id="ff822-125">Description</span></span>|  
|-----------------------------|-----------------|  
|<span data-ttu-id="ff822-126">**_Total**</span><span class="sxs-lookup"><span data-stu-id="ff822-126">**_Total**</span></span>|<span data-ttu-id="ff822-127">所有游标的信息。</span><span class="sxs-lookup"><span data-stu-id="ff822-127">Information for all cursors.</span></span>|  
|<span data-ttu-id="ff822-128">**API 游标**</span><span class="sxs-lookup"><span data-stu-id="ff822-128">**API Cursor**</span></span>|<span data-ttu-id="ff822-129">仅 API 游标信息。</span><span class="sxs-lookup"><span data-stu-id="ff822-129">Only the API cursor information.</span></span>|  
|<span data-ttu-id="ff822-130">**TSQL 全局游标**</span><span class="sxs-lookup"><span data-stu-id="ff822-130">**TSQL Global Cursor**</span></span>|<span data-ttu-id="ff822-131">仅 [!INCLUDE[tsql](../../includes/tsql-md.md)] 全局游标信息。</span><span class="sxs-lookup"><span data-stu-id="ff822-131">Only the [!INCLUDE[tsql](../../includes/tsql-md.md)] global cursor information.</span></span>|  
|<span data-ttu-id="ff822-132">**TSQL 局部游标**</span><span class="sxs-lookup"><span data-stu-id="ff822-132">**TSQL Local Cursor**</span></span>|<span data-ttu-id="ff822-133">仅 [!INCLUDE[tsql](../../includes/tsql-md.md)] 局部游标信息。</span><span class="sxs-lookup"><span data-stu-id="ff822-133">Only the [!INCLUDE[tsql](../../includes/tsql-md.md)] local cursor information.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff822-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ff822-134">See Also</span></span>  
 [<span data-ttu-id="ff822-135">监视资源使用情况（系统监视器）</span><span class="sxs-lookup"><span data-stu-id="ff822-135">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
