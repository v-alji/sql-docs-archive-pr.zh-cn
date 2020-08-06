---
title: MSSQLSERVER_32043 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 32043 (Database Engine error)
ms.assetid: a0c48ae3-4c8c-419c-afb5-579fcefac01d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2febc7173c8144451c7a9b0576f2293d5594c6df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577717"
---
# <a name="mssqlserver_32043"></a><span data-ttu-id="467ca-102">MSSQLSERVER_32043</span><span class="sxs-lookup"><span data-stu-id="467ca-102">MSSQLSERVER_32043</span></span>
    
## <a name="details"></a><span data-ttu-id="467ca-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="467ca-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="467ca-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="467ca-104">Product Name</span></span>|<span data-ttu-id="467ca-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="467ca-105">SQL Server</span></span>|  
|<span data-ttu-id="467ca-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="467ca-106">Event ID</span></span>|<span data-ttu-id="467ca-107">32043</span><span class="sxs-lookup"><span data-stu-id="467ca-107">32043</span></span>|  
|<span data-ttu-id="467ca-108">事件源</span><span class="sxs-lookup"><span data-stu-id="467ca-108">Event Source</span></span>|<span data-ttu-id="467ca-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="467ca-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="467ca-110">组件</span><span class="sxs-lookup"><span data-stu-id="467ca-110">Component</span></span>|<span data-ttu-id="467ca-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="467ca-111">SQLEngine</span></span>|  
|<span data-ttu-id="467ca-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="467ca-112">Symbolic Name</span></span>|<span data-ttu-id="467ca-113">SQLErrorNum32043</span><span class="sxs-lookup"><span data-stu-id="467ca-113">SQLErrorNum32043</span></span>|  
|<span data-ttu-id="467ca-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="467ca-114">Message Text</span></span>|<span data-ttu-id="467ca-115">引发了 '未还原日志' 警报。</span><span class="sxs-lookup"><span data-stu-id="467ca-115">The alert for 'unrestored log' has been raised.</span></span> <span data-ttu-id="467ca-116">'%d' 的当前值超出了阈值 '%d'。</span><span class="sxs-lookup"><span data-stu-id="467ca-116">The current value of '%d' surpasses the threshold '%d'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="467ca-117">说明</span><span class="sxs-lookup"><span data-stu-id="467ca-117">Explanation</span></span>  
 <span data-ttu-id="467ca-118">此数据库镜像事件是对镜像服务器实例发出的，指示未还原日志量已达到了用户指定的阈值。</span><span class="sxs-lookup"><span data-stu-id="467ca-118">This database mirroring event is issued on the mirror server instance to indicate that the amount of unrestored log reached a user-specified threshold value.</span></span> <span data-ttu-id="467ca-119">通常，发生该事件是由于系统的性能已发生变化。</span><span class="sxs-lookup"><span data-stu-id="467ca-119">Typically, this event occurs because the performance of the system has changed.</span></span> <span data-ttu-id="467ca-120">两个系统间的带宽减小或负载增加。</span><span class="sxs-lookup"><span data-stu-id="467ca-120">Either the bandwidth between the two systems has decreased, or the load has increased.</span></span>  
  
 <span data-ttu-id="467ca-121">未还原日志是镜像服务器实例已接收并已写入磁盘但等待还原到镜像数据库的日志。</span><span class="sxs-lookup"><span data-stu-id="467ca-121">An unrestored log is a log that has been received by the mirror server instance and written to disk but is waiting to be restored to the mirror database.</span></span> <span data-ttu-id="467ca-122">未还原日志量（以 KB 为单位）是一种性能指标，有助于您计算当前故障转移时间。</span><span class="sxs-lookup"><span data-stu-id="467ca-122">The amount of unrestored log in kilobytes (KB) is a performance metric that can help you evaluate the current failover time.</span></span> <span data-ttu-id="467ca-123">应用未还原日志所需的时间是构成故障转移时间的主要部分，另外还包括恢复数据库并使之在线所需的额外短暂时间。</span><span class="sxs-lookup"><span data-stu-id="467ca-123">The time that is required to apply the unrestored log is the main factor in failover time, along with a short additional time that is required to recover the database and bring it online.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="467ca-124">对于自动故障转移，系统识别故障所需的时间与故障转移时间无关。</span><span class="sxs-lookup"><span data-stu-id="467ca-124">For an automatic failover, the time for the system to notice the failure is independent of the failover time.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="467ca-125">用户操作</span><span class="sxs-lookup"><span data-stu-id="467ca-125">User Action</span></span>  
 <span data-ttu-id="467ca-126">检查主体服务器实例和镜像服务器实例上的负荷及其网络连接以查找原因。</span><span class="sxs-lookup"><span data-stu-id="467ca-126">Check the loads on the principal and mirror server instances and their network connection for the cause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="467ca-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="467ca-127">See Also</span></span>  
 <span data-ttu-id="467ca-128">[数据库镜像 (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="467ca-128">[Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="467ca-129">使用镜像性能度量的警告阈值和警报 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="467ca-129">Use Warning Thresholds and Alerts on Mirroring Performance Metrics &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
  
