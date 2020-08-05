---
title: MSSQLSERVER_32042 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 32042 (Database Engine error)
ms.assetid: 53a51c7a-dcd4-4c15-b4d2-6aaa9dce76da
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bd959d84da2c54310dea5156b1a45b73490211a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581268"
---
# <a name="mssqlserver_32042"></a><span data-ttu-id="29bdf-102">MSSQLSERVER_32042</span><span class="sxs-lookup"><span data-stu-id="29bdf-102">MSSQLSERVER_32042</span></span>
    
## <a name="details"></a><span data-ttu-id="29bdf-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="29bdf-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="29bdf-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="29bdf-104">Product Name</span></span>|<span data-ttu-id="29bdf-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="29bdf-105">SQL Server</span></span>|  
|<span data-ttu-id="29bdf-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="29bdf-106">Event ID</span></span>|<span data-ttu-id="29bdf-107">32042</span><span class="sxs-lookup"><span data-stu-id="29bdf-107">32042</span></span>|  
|<span data-ttu-id="29bdf-108">事件源</span><span class="sxs-lookup"><span data-stu-id="29bdf-108">Event Source</span></span>|<span data-ttu-id="29bdf-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="29bdf-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="29bdf-110">组件</span><span class="sxs-lookup"><span data-stu-id="29bdf-110">Component</span></span>|<span data-ttu-id="29bdf-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="29bdf-111">SQLEngine</span></span>|  
|<span data-ttu-id="29bdf-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="29bdf-112">Symbolic Name</span></span>|<span data-ttu-id="29bdf-113">SQLErrorNum32042</span><span class="sxs-lookup"><span data-stu-id="29bdf-113">SQLErrorNum32042</span></span>|  
|<span data-ttu-id="29bdf-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="29bdf-114">Message Text</span></span>|<span data-ttu-id="29bdf-115">引发了 '未发送日志' 警报。</span><span class="sxs-lookup"><span data-stu-id="29bdf-115">The alert for 'unsent log' has been raised.</span></span> <span data-ttu-id="29bdf-116">'%d' 的当前值超出了阈值 '%d'。</span><span class="sxs-lookup"><span data-stu-id="29bdf-116">The current value of '%d' surpasses the threshold '%d'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="29bdf-117">说明</span><span class="sxs-lookup"><span data-stu-id="29bdf-117">Explanation</span></span>  
 <span data-ttu-id="29bdf-118">对主体服务器实例发出此数据库镜像事件，表明未发送日志的量达到了用户指定的阈值。</span><span class="sxs-lookup"><span data-stu-id="29bdf-118">This database mirroring event is issued on the principal server instance to indicate that the amount of unsent log has reached a user-specified threshold value.</span></span> <span data-ttu-id="29bdf-119">通常，发生该事件是由于系统的性能已发生变化。</span><span class="sxs-lookup"><span data-stu-id="29bdf-119">Typically, this event occurs because the performance of the system has changed.</span></span> <span data-ttu-id="29bdf-120">两个系统间的带宽减小或负载增加。</span><span class="sxs-lookup"><span data-stu-id="29bdf-120">Either the bandwidth between the two systems has decreased, or the load has increased.</span></span>  
  
 <span data-ttu-id="29bdf-121">未发送日志的量（以 KB 计）是一个性能指标，可帮助您计算数据丢失的可能性。</span><span class="sxs-lookup"><span data-stu-id="29bdf-121">The amount of unsent log is a performance metric that can help you evaluate the potential for data loss in terms of the number of kilobytes (KB) of unsent log.</span></span> <span data-ttu-id="29bdf-122">此指标尤其适用于高性能模式会话。</span><span class="sxs-lookup"><span data-stu-id="29bdf-122">This metric is particularly relevant for high-performance mode sessions.</span></span> <span data-ttu-id="29bdf-123">但是，当镜像因伙伴断开连接而暂停或挂起时，此指标也适用于高安全模式会话。</span><span class="sxs-lookup"><span data-stu-id="29bdf-123">However, this metric is also a relevant for high-safety mode session when mirroring is paused or suspended because the partners become disconnected.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="29bdf-124">用户操作</span><span class="sxs-lookup"><span data-stu-id="29bdf-124">User Action</span></span>  
 <span data-ttu-id="29bdf-125">检查主体服务器实例和镜像服务器实例上的负荷及其网络连接以查找原因。</span><span class="sxs-lookup"><span data-stu-id="29bdf-125">Check the loads on the principal and mirror server instances and their network connection for the cause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29bdf-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="29bdf-126">See Also</span></span>  
 <span data-ttu-id="29bdf-127">[数据库镜像 (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="29bdf-127">[Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="29bdf-128">使用镜像性能度量的警告阈值和警报 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="29bdf-128">Use Warning Thresholds and Alerts on Mirroring Performance Metrics &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
  
