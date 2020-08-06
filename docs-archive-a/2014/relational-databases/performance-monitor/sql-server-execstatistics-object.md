---
title: SQL Server - ExecStatistics 对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:ExecStatistics
- ExecStatistics object
ms.assetid: 4f8557a8-345f-4622-a8a5-763a0388ad94
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d1a50c97add4708a58b9edc45fd49982b97a51ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578829"
---
# <a name="sql-server-execstatistics-object"></a><span data-ttu-id="8be15-102">SQL Server ExecStatistics 对象</span><span class="sxs-lookup"><span data-stu-id="8be15-102">SQL Server, ExecStatistics Object</span></span>
  <span data-ttu-id="8be15-103">Microsoft SQL Server 中的 **SQLServer:ExecStatistics** 对象提供了用于监视各种执行的计数器。</span><span class="sxs-lookup"><span data-stu-id="8be15-103">The **SQLServer:ExecStatistics** object in Microsoft SQL Server provides counters to monitor various executions.</span></span>  
  
 <span data-ttu-id="8be15-104">下表介绍了 SQL Server **Exec Statistics** 计数器。</span><span class="sxs-lookup"><span data-stu-id="8be15-104">This table describes the SQL Server **Exec Statistics** counters.</span></span>  
  
|<span data-ttu-id="8be15-105">SQL Server Exec Statistics 计数器</span><span class="sxs-lookup"><span data-stu-id="8be15-105">SQL Server Exec Statistics counters</span></span>|<span data-ttu-id="8be15-106">说明</span><span class="sxs-lookup"><span data-stu-id="8be15-106">Description</span></span>|  
|-----------------------------------------|-----------------|  
|<span data-ttu-id="8be15-107">**Distributed Query**</span><span class="sxs-lookup"><span data-stu-id="8be15-107">**Distributed Query**</span></span>|<span data-ttu-id="8be15-108">与执行分布式查询相关的统计信息。</span><span class="sxs-lookup"><span data-stu-id="8be15-108">Statistics relevant to execution of distributed queries.</span></span>|  
|<span data-ttu-id="8be15-109">**DTC calls**</span><span class="sxs-lookup"><span data-stu-id="8be15-109">**DTC calls**</span></span>|<span data-ttu-id="8be15-110">与执行 DTC 调用相关的统计信息。</span><span class="sxs-lookup"><span data-stu-id="8be15-110">Statistics relevant to execution of DTC calls.</span></span>|  
|<span data-ttu-id="8be15-111">**Extended Procedures**</span><span class="sxs-lookup"><span data-stu-id="8be15-111">**Extended Procedures**</span></span>|<span data-ttu-id="8be15-112">与执行扩展过程相关的统计信息。</span><span class="sxs-lookup"><span data-stu-id="8be15-112">Statistics relevant to execution of extended procedures.</span></span>|  
|<span data-ttu-id="8be15-113">**OLEDB calls**</span><span class="sxs-lookup"><span data-stu-id="8be15-113">**OLEDB calls**</span></span>|<span data-ttu-id="8be15-114">与执行 OLEDB 调用相关的统计信息。</span><span class="sxs-lookup"><span data-stu-id="8be15-114">Statistics relevant to execution of OLEDB calls.</span></span>|  
  
 <span data-ttu-id="8be15-115">对象中的每个计数器均包含以下实例：</span><span class="sxs-lookup"><span data-stu-id="8be15-115">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="8be15-116">项</span><span class="sxs-lookup"><span data-stu-id="8be15-116">Item</span></span>|<span data-ttu-id="8be15-117">说明</span><span class="sxs-lookup"><span data-stu-id="8be15-117">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="8be15-118">**平均执行时间 (ms)**</span><span class="sxs-lookup"><span data-stu-id="8be15-118">**Average execution time (ms)**</span></span>|<span data-ttu-id="8be15-119">所选执行类型的平均执行时间。</span><span class="sxs-lookup"><span data-stu-id="8be15-119">Average execution time of the selected type of execution.</span></span>|  
|<span data-ttu-id="8be15-120">**每秒的累积执行时间 (ms)**</span><span class="sxs-lookup"><span data-stu-id="8be15-120">**Cumulative execution time (ms) per second**</span></span>|<span data-ttu-id="8be15-121">所选执行类型每秒的累积执行时间。</span><span class="sxs-lookup"><span data-stu-id="8be15-121">Aggregated execution time per second, of the selected type of execution.</span></span>|  
|<span data-ttu-id="8be15-122">**正在进行的执行数**</span><span class="sxs-lookup"><span data-stu-id="8be15-122">**Execs in progress**</span></span>|<span data-ttu-id="8be15-123">正在进行的所选执行类型的执行数。</span><span class="sxs-lookup"><span data-stu-id="8be15-123">Number of execs in progress of the selected type of execution.</span></span>|  
|<span data-ttu-id="8be15-124">**每秒启动的执行数**</span><span class="sxs-lookup"><span data-stu-id="8be15-124">**Exec started per second**</span></span>|<span data-ttu-id="8be15-125">每秒启动的所选执行类型的执行数。</span><span class="sxs-lookup"><span data-stu-id="8be15-125">Number of exes started per second of the selected type of execution.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8be15-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8be15-126">See Also</span></span>  
 [<span data-ttu-id="8be15-127">监视资源使用情况（系统监视器）</span><span class="sxs-lookup"><span data-stu-id="8be15-127">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
