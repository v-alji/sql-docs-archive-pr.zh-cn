---
title: SQL Server - Broker TO Statistics 对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Broker Transmission Object object
- 'SQL Server: Broker Transmission Object'
ms.assetid: b5bc5dde-e540-4848-8aa3-5735c51df2fb
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 93d9c24a175dedfee171eccfccb34673501660ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589515"
---
# <a name="sql-server-broker-to-statistics-object"></a><span data-ttu-id="072c8-102">SQL Server Broker TO Statistics 对象</span><span class="sxs-lookup"><span data-stu-id="072c8-102">SQL Server, Broker TO Statistics Object</span></span>
  <span data-ttu-id="072c8-103">SQLServer:Broker TO Statistics 性能对象报告有关 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 对话框请求传输对象的次数以及传输对象写入 tempdb 中的频率的信息。</span><span class="sxs-lookup"><span data-stu-id="072c8-103">The SQLServer:Broker TO Statistics performance object reports information about how many times [!INCLUDE[ssSB](../../includes/sssb-md.md)] dialogs request transmission objects, and how often transmission objects are written to **tempdb**.</span></span>  
  
 <span data-ttu-id="072c8-104">传输对象记录 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 对话框的消息传输状态。</span><span class="sxs-lookup"><span data-stu-id="072c8-104">Transmission objects record the state of message transmissions for a [!INCLUDE[ssSB](../../includes/sssb-md.md)] dialog.</span></span> <span data-ttu-id="072c8-105">这些对象存储在内存中。</span><span class="sxs-lookup"><span data-stu-id="072c8-105">They are stored in memory.</span></span> <span data-ttu-id="072c8-106">为了释放内存， [!INCLUDE[ssSB](../../includes/sssb-md.md)] 会定期将各批非活动传输对象写入 **tempdb**的工作表中。</span><span class="sxs-lookup"><span data-stu-id="072c8-106">To free memory, [!INCLUDE[ssSB](../../includes/sssb-md.md)] periodically writes batches of inactive transmission objects to work tables in **tempdb**.</span></span>  
  
 <span data-ttu-id="072c8-107">下表列出了此对象包含的计数器。</span><span class="sxs-lookup"><span data-stu-id="072c8-107">The following table lists the counters that this object contains.</span></span>  
  
|<span data-ttu-id="072c8-108">SQL Server Broker TO Statistics 计数器</span><span class="sxs-lookup"><span data-stu-id="072c8-108">SQL Server Broker TO Statistics counters</span></span>|<span data-ttu-id="072c8-109">说明</span><span class="sxs-lookup"><span data-stu-id="072c8-109">Description</span></span>|  
|----------------------------------------------|-----------------|  
|<span data-ttu-id="072c8-110">**页的Length of Batched Writes**</span><span class="sxs-lookup"><span data-stu-id="072c8-110">**Avg. Length of Batched Writes**</span></span>|<span data-ttu-id="072c8-111">保存在一个批次中的传输对象平均数。</span><span class="sxs-lookup"><span data-stu-id="072c8-111">The average number of transmission objects saved in a batch.</span></span>|  
|<span data-ttu-id="072c8-112">**页的Time To Write Batch (ms)**</span><span class="sxs-lookup"><span data-stu-id="072c8-112">**Avg. Time To Write Batch (ms)**</span></span>|<span data-ttu-id="072c8-113">保存一批传输对象所需的平均毫秒数。</span><span class="sxs-lookup"><span data-stu-id="072c8-113">The average number of milliseconds required to save a batch of transmission objects.</span></span>|  
|<span data-ttu-id="072c8-114">**页的Time Between Batches (ms)**</span><span class="sxs-lookup"><span data-stu-id="072c8-114">**Avg. Time Between Batches (ms)**</span></span>|<span data-ttu-id="072c8-115">不同传输对象批次写入之间间隔的平均毫秒数。</span><span class="sxs-lookup"><span data-stu-id="072c8-115">The average number of milliseconds between writes of transmission object batches.</span></span>|  
|<span data-ttu-id="072c8-116">**Tran Object Gets/sec**</span><span class="sxs-lookup"><span data-stu-id="072c8-116">**Tran Object Gets/sec**</span></span>|<span data-ttu-id="072c8-117">对话框每秒请求传输对象的次数。</span><span class="sxs-lookup"><span data-stu-id="072c8-117">The number of times per second that dialogs requested transmission objects.</span></span>|  
|<span data-ttu-id="072c8-118">**Tran Objects Marked Dirty/sec**</span><span class="sxs-lookup"><span data-stu-id="072c8-118">**Tran Objects Marked Dirty/sec**</span></span>|<span data-ttu-id="072c8-119">传输对象每秒标记为“脏”的次数。</span><span class="sxs-lookup"><span data-stu-id="072c8-119">The number of times per second that transmission objects were marked as dirty.</span></span> <span data-ttu-id="072c8-120">当第一次出现导致内存中的副本不同于存储在 **tempdb**中的副本的修改时，传输对象会被其标记为“脏”。</span><span class="sxs-lookup"><span data-stu-id="072c8-120">Transmission objects are marked as dirty by the first modification that causes the in-memory copy to differ from the copy stored in **tempdb**.</span></span> <span data-ttu-id="072c8-121">当 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 必须在对话框的消息传输状态下记录更改时，将会修改传输对象。</span><span class="sxs-lookup"><span data-stu-id="072c8-121">Transmission objects are modified when [!INCLUDE[ssSB](../../includes/sssb-md.md)] has to record a change in the state of message transmissions for the dialog.</span></span>|  
|<span data-ttu-id="072c8-122">**Tran Object Writes/sec**</span><span class="sxs-lookup"><span data-stu-id="072c8-122">**Tran Object Writes/sec**</span></span>|<span data-ttu-id="072c8-123">每秒将各批传输对象写入 **tempdb** 工作表的次数。</span><span class="sxs-lookup"><span data-stu-id="072c8-123">The number of times per second that a batch of transmission objects were written to **tempdb** work tables.</span></span> <span data-ttu-id="072c8-124">大量写入可表明 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内存正在承受很大的压力。</span><span class="sxs-lookup"><span data-stu-id="072c8-124">Large numbers of writes could indicate that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory is being stressed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="072c8-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="072c8-125">See Also</span></span>  
 <span data-ttu-id="072c8-126">[SQL Server Access Methods 对象](sql-server-access-methods-object.md) </span><span class="sxs-lookup"><span data-stu-id="072c8-126">[SQL Server, Access Methods Object](sql-server-access-methods-object.md) </span></span>  
 <span data-ttu-id="072c8-127">[SQL Server Memory Manager 对象](sql-server-memory-manager-object.md) </span><span class="sxs-lookup"><span data-stu-id="072c8-127">[SQL Server, Memory Manager Object](sql-server-memory-manager-object.md) </span></span>  
 [<span data-ttu-id="072c8-128">监视资源使用情况（系统监视器）</span><span class="sxs-lookup"><span data-stu-id="072c8-128">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
