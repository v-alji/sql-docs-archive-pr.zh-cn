---
title: MSSQLSERVER_32044 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 32044 (Database Engine error)
ms.assetid: f2d073be-d9a1-4837-8a38-028d3e3403bd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 27d9655c3a908f1302f048c6f68159d4f610367a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581267"
---
# <a name="mssqlserver_32044"></a><span data-ttu-id="7dbc6-102">MSSQLSERVER_32044</span><span class="sxs-lookup"><span data-stu-id="7dbc6-102">MSSQLSERVER_32044</span></span>
    
## <a name="details"></a><span data-ttu-id="7dbc6-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="7dbc6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7dbc6-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="7dbc6-104">Product Name</span></span>|<span data-ttu-id="7dbc6-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="7dbc6-105">SQL Server</span></span>|  
|<span data-ttu-id="7dbc6-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="7dbc6-106">Event ID</span></span>|<span data-ttu-id="7dbc6-107">32044</span><span class="sxs-lookup"><span data-stu-id="7dbc6-107">32044</span></span>|  
|<span data-ttu-id="7dbc6-108">事件源</span><span class="sxs-lookup"><span data-stu-id="7dbc6-108">Event Source</span></span>|<span data-ttu-id="7dbc6-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7dbc6-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7dbc6-110">组件</span><span class="sxs-lookup"><span data-stu-id="7dbc6-110">Component</span></span>|<span data-ttu-id="7dbc6-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="7dbc6-111">SQLEngine</span></span>|  
|<span data-ttu-id="7dbc6-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="7dbc6-112">Symbolic Name</span></span>|<span data-ttu-id="7dbc6-113">SQLErrorNum32044</span><span class="sxs-lookup"><span data-stu-id="7dbc6-113">SQLErrorNum32044</span></span>|  
|<span data-ttu-id="7dbc6-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="7dbc6-114">Message Text</span></span>|<span data-ttu-id="7dbc6-115">引发了 '镜像提交开销' 警报。</span><span class="sxs-lookup"><span data-stu-id="7dbc6-115">The alert for 'mirror commit overhead' has been raised.</span></span> <span data-ttu-id="7dbc6-116">'%d' 的当前值超出了阈值 '%d'。</span><span class="sxs-lookup"><span data-stu-id="7dbc6-116">The current value of '%d' surpasses the threshold '%d'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7dbc6-117">说明</span><span class="sxs-lookup"><span data-stu-id="7dbc6-117">Explanation</span></span>  
 <span data-ttu-id="7dbc6-118">对主体服务器实例发出此数据库镜像事件，表明由于数据库镜像而使提交等待总时间达到或超出了用户指定的阈值。</span><span class="sxs-lookup"><span data-stu-id="7dbc6-118">This database mirroring event is issued on the principal server instance to indicate that the aggregate commit wait time reached or exceeded a user-specified threshold value because of database mirroring.</span></span> <span data-ttu-id="7dbc6-119">等待时间是事务数与每个事务所执行时间的乘积。</span><span class="sxs-lookup"><span data-stu-id="7dbc6-119">The wait time is the product of the number of transactions and the time of each.</span></span> <span data-ttu-id="7dbc6-120">例如，以下事例都会产生 1000 毫秒的等待时间：1000 个事务 \* 1 毫秒，1 个事务 \* 1000 毫秒。</span><span class="sxs-lookup"><span data-stu-id="7dbc6-120">For example, the following cases both produce 1000 milliseconds of wait time: 1000 transactions \* 1 millisecond, and 1 transaction \* 1000 milliseconds.</span></span> <span data-ttu-id="7dbc6-121">事务计数太大、发送日志延迟时间过长或刷新镜像服务器实例上的日志的延迟时间过长，都会延长提交等待时间。</span><span class="sxs-lookup"><span data-stu-id="7dbc6-121">An increased commit wait time can be caused by a surge in the transaction count, delays in sending the log, or delays in flushing the log on the mirror server instance.</span></span>  
  
 <span data-ttu-id="7dbc6-122">镜像提交开销量是一个性能指标，可帮助您评估同步操作的当前性能影响。</span><span class="sxs-lookup"><span data-stu-id="7dbc6-122">The amount of mirror commit overhead is a performance metric that can help you evaluate the current performance impact of synchronous operation.</span></span> <span data-ttu-id="7dbc6-123">此指标只适用于高安全模式。</span><span class="sxs-lookup"><span data-stu-id="7dbc6-123">This metric is relevant only in high-safety mode.</span></span> <span data-ttu-id="7dbc6-124">高安全模式是同步模式，因此主体服务器实例将日志记录发送到镜像服务器实例之后将一直等待提交事务，直到收到镜像服务器实例已将日志记录写入磁盘的确认。</span><span class="sxs-lookup"><span data-stu-id="7dbc6-124">Because high-safety mode is synchronous, the principal server instance waits to commit the transaction after it sends a log record to the mirror server instance until it receives confirmation that the mirror server instance has written the log record to disk.</span></span> <span data-ttu-id="7dbc6-125">在日志记录等待还原到镜像数据库期间，它一直保留在镜像服务器实例的磁盘上。</span><span class="sxs-lookup"><span data-stu-id="7dbc6-125">The log record remains on disk on the mirror server instance while it waits to be restored to the mirror database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7dbc6-126">用户操作</span><span class="sxs-lookup"><span data-stu-id="7dbc6-126">User Action</span></span>  
 <span data-ttu-id="7dbc6-127">检查主体服务器实例和镜像服务器实例上的负荷及其网络连接以查找原因。</span><span class="sxs-lookup"><span data-stu-id="7dbc6-127">Check the loads on the principal and mirror server instances and their network connection for the cause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dbc6-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7dbc6-128">See Also</span></span>  
 <span data-ttu-id="7dbc6-129">[数据库镜像 (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7dbc6-129">[Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="7dbc6-130">使用镜像性能度量的警告阈值和警报 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7dbc6-130">Use Warning Thresholds and Alerts on Mirroring Performance Metrics &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
  
