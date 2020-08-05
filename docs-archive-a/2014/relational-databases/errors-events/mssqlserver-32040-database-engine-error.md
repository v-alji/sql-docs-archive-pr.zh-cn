---
title: MSSQLSERVER_32040 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 32040 (Database Engine error)
ms.assetid: 709219b1-f8b2-4696-8923-dd2e91492eb8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 05692e2f20b0719c1ca8f48282c3b7aaed8e2341
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581269"
---
# <a name="mssqlserver_32040"></a><span data-ttu-id="21ba4-102">MSSQLSERVER_32040</span><span class="sxs-lookup"><span data-stu-id="21ba4-102">MSSQLSERVER_32040</span></span>
    
## <a name="details"></a><span data-ttu-id="21ba4-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="21ba4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="21ba4-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="21ba4-104">Product Name</span></span>|<span data-ttu-id="21ba4-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="21ba4-105">SQL Server</span></span>|  
|<span data-ttu-id="21ba4-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="21ba4-106">Event ID</span></span>|<span data-ttu-id="21ba4-107">32040</span><span class="sxs-lookup"><span data-stu-id="21ba4-107">32040</span></span>|  
|<span data-ttu-id="21ba4-108">事件源</span><span class="sxs-lookup"><span data-stu-id="21ba4-108">Event Source</span></span>|<span data-ttu-id="21ba4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="21ba4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="21ba4-110">组件</span><span class="sxs-lookup"><span data-stu-id="21ba4-110">Component</span></span>|<span data-ttu-id="21ba4-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="21ba4-111">SQLEngine</span></span>|  
|<span data-ttu-id="21ba4-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="21ba4-112">Symbolic Name</span></span>|<span data-ttu-id="21ba4-113">SQLErrorNum32040</span><span class="sxs-lookup"><span data-stu-id="21ba4-113">SQLErrorNum32040</span></span>|  
|<span data-ttu-id="21ba4-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="21ba4-114">Message Text</span></span>|<span data-ttu-id="21ba4-115">引发了 '最早的未发送事务' 警报。</span><span class="sxs-lookup"><span data-stu-id="21ba4-115">The alert for 'oldest unsent transaction' has been raised.</span></span> <span data-ttu-id="21ba4-116">'%d' 的当前值超出了阈值 '%d'。</span><span class="sxs-lookup"><span data-stu-id="21ba4-116">The current value of '%d' surpasses the threshold '%d'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="21ba4-117">说明</span><span class="sxs-lookup"><span data-stu-id="21ba4-117">Explanation</span></span>  
 <span data-ttu-id="21ba4-118">此数据库镜像事件是对主体服务器实例发出的，指示最早的未发送事务的保留时间已达到了用户指定的阈值。</span><span class="sxs-lookup"><span data-stu-id="21ba4-118">This database mirroring event is issued on the principal server instance to indicate that the age of the oldest unsent transaction has reached a user-specified threshold value.</span></span> <span data-ttu-id="21ba4-119">通常，发生该事件是由于系统的性能已发生变化。</span><span class="sxs-lookup"><span data-stu-id="21ba4-119">Typically, this event occurs because the performance of the system has changed.</span></span> <span data-ttu-id="21ba4-120">两个系统间的带宽减小或负载增加。</span><span class="sxs-lookup"><span data-stu-id="21ba4-120">Either the bandwidth between the two systems has decreased, or the load has increased.</span></span>  
  
 <span data-ttu-id="21ba4-121">最早的未发送事务的保留时间是一种性能指标，有助于您估算数据丢失的可能性（以未发送事务的分钟数来衡量）。</span><span class="sxs-lookup"><span data-stu-id="21ba4-121">The age of the oldest unsent transaction is a performance metric that can help you evaluate the potential for data loss as measured by the number of minutes of unsent transactions.</span></span> <span data-ttu-id="21ba4-122">此指标特别适用于高性能模式会话。</span><span class="sxs-lookup"><span data-stu-id="21ba4-122">This metric is especially relevant for high-performance mode sessions.</span></span> <span data-ttu-id="21ba4-123">但是，当镜像因伙伴断开连接而暂停或挂起时，该指标也适用于高安全模式会话。</span><span class="sxs-lookup"><span data-stu-id="21ba4-123">However, this metric is also relevant for high-safety mode session when mirroring is paused or suspended because the partners become disconnected.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="21ba4-124">用户操作</span><span class="sxs-lookup"><span data-stu-id="21ba4-124">User Action</span></span>  
 <span data-ttu-id="21ba4-125">检查主体服务器实例和镜像服务器实例上的负荷及其网络连接以查找原因。</span><span class="sxs-lookup"><span data-stu-id="21ba4-125">Check the loads on the principal and mirror server instances and their network connection for the cause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21ba4-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="21ba4-126">See Also</span></span>  
 <span data-ttu-id="21ba4-127">[数据库镜像 (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="21ba4-127">[Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="21ba4-128">使用镜像性能度量的警告阈值和警报 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="21ba4-128">Use Warning Thresholds and Alerts on Mirroring Performance Metrics &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
  
