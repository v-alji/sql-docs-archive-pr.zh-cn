---
title: SQL Server - Latches 对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Latches object
- SQLServer:Latches
ms.assetid: 2393ea1c-2bf3-41c3-9f37-b9761144eeca
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6f49ac00114065e971c0893f9217ab883eb2d7f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578826"
---
# <a name="sql-server-latches-object"></a><span data-ttu-id="78ca5-102">SQL Server Latches 对象</span><span class="sxs-lookup"><span data-stu-id="78ca5-102">SQL Server, Latches Object</span></span>
  <span data-ttu-id="78ca5-103">Microsoft **中的** SQLServer:Latches [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象提供计数器来监视称为闩锁的内部 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 资源锁。</span><span class="sxs-lookup"><span data-stu-id="78ca5-103">The **SQLServer:Latches** object in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides counters to monitor internal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource locks called latches.</span></span> <span data-ttu-id="78ca5-104">通过监视闩锁来确定用户活动和资源使用情况，将有助于查明性能瓶颈。</span><span class="sxs-lookup"><span data-stu-id="78ca5-104">Monitoring the latches to determine user activity and resource usage can help you to identify performance bottlenecks.</span></span>  
  
 <span data-ttu-id="78ca5-105">下表介绍了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Latches** 计数器。</span><span class="sxs-lookup"><span data-stu-id="78ca5-105">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Latches** counters.</span></span>  
  
|<span data-ttu-id="78ca5-106">SQL Server Latches 计数器</span><span class="sxs-lookup"><span data-stu-id="78ca5-106">SQL Server Latches counters</span></span>|<span data-ttu-id="78ca5-107">说明</span><span class="sxs-lookup"><span data-stu-id="78ca5-107">Description</span></span>|  
|---------------------------------|-----------------|  
|<span data-ttu-id="78ca5-108">**Average Latch Wait Time (ms)**</span><span class="sxs-lookup"><span data-stu-id="78ca5-108">**Average Latch Wait Time (ms)**</span></span>|<span data-ttu-id="78ca5-109">必须等待授予的闩锁请求的平均等待时间（毫秒）。</span><span class="sxs-lookup"><span data-stu-id="78ca5-109">Average latch wait time (in milliseconds) for latch requests that had to wait.</span></span>|  
|<span data-ttu-id="78ca5-110">**Latch Waits/sec**</span><span class="sxs-lookup"><span data-stu-id="78ca5-110">**Latch Waits/sec**</span></span>|<span data-ttu-id="78ca5-111">未能立即授予的闩锁请求数。</span><span class="sxs-lookup"><span data-stu-id="78ca5-111">Number of latch requests that could not be granted immediately.</span></span>|  
|<span data-ttu-id="78ca5-112">**Number of SuperLatches**</span><span class="sxs-lookup"><span data-stu-id="78ca5-112">**Number of SuperLatches**</span></span>|<span data-ttu-id="78ca5-113">目前是 SuperLatch 的闩锁数。</span><span class="sxs-lookup"><span data-stu-id="78ca5-113">Number of latches that are currently SuperLatches.</span></span>|  
|<span data-ttu-id="78ca5-114">**SuperLatch Demotions/sec**</span><span class="sxs-lookup"><span data-stu-id="78ca5-114">**SuperLatch Demotions/sec**</span></span>|<span data-ttu-id="78ca5-115">在上一秒钟内已降级为常规闩锁的 SuperLatch 数。</span><span class="sxs-lookup"><span data-stu-id="78ca5-115">Number of SuperLatches that have been demoted to regular latches in the last second.</span></span>|  
|<span data-ttu-id="78ca5-116">**SuperLatch Promotions/sec**</span><span class="sxs-lookup"><span data-stu-id="78ca5-116">**SuperLatch Promotions/sec**</span></span>|<span data-ttu-id="78ca5-117">在上一秒钟内已提升为 SuperLatch 的闩锁数。</span><span class="sxs-lookup"><span data-stu-id="78ca5-117">Number of latches that have been promoted to SuperLatches in the last second.</span></span>|  
|<span data-ttu-id="78ca5-118">**Total Latch Wait Time (ms)**</span><span class="sxs-lookup"><span data-stu-id="78ca5-118">**Total Latch Wait Time (ms)**</span></span>|<span data-ttu-id="78ca5-119">上一秒钟内的闩锁请求的总等待时间（毫秒）。</span><span class="sxs-lookup"><span data-stu-id="78ca5-119">Total latch wait time (in milliseconds) for latch requests in the last second.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="78ca5-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="78ca5-120">See Also</span></span>  
 [<span data-ttu-id="78ca5-121">监视资源使用情况（系统监视器）</span><span class="sxs-lookup"><span data-stu-id="78ca5-121">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
