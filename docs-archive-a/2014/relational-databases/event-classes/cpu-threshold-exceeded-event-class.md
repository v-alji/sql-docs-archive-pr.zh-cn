---
title: CPU Threshold Exceeded 事件类 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- CPU Threshold Exceeded Event Class
ms.assetid: eb106f7d-baa3-4a2b-96b2-f9fe0844057d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 07b51e1a6f08f48c601b00d2dcb67bc6d09006f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578246"
---
# <a name="cpu-threshold-exceeded-event-class"></a><span data-ttu-id="e7efa-102">CPU Threshold Exceeded 事件类</span><span class="sxs-lookup"><span data-stu-id="e7efa-102">CPU Threshold Exceeded Event Class</span></span>
  <span data-ttu-id="e7efa-103">CPU Threshold Exceeded 事件类指示资源调控器检测到超出为 REQUEST_MAX_CPU_TIME_SEC 指定的 CPU 阈值的查询。</span><span class="sxs-lookup"><span data-stu-id="e7efa-103">The CPU Threshold Exceeded event class indicates that Resource Governor detects a query that exceeds the CPU threshold specified for REQUEST_MAX_CPU_TIME_SEC.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7efa-104">此事件的检测时间间隔为五秒。</span><span class="sxs-lookup"><span data-stu-id="e7efa-104">The detection interval for this event is five seconds.</span></span> <span data-ttu-id="e7efa-105">这就保证如果查询超出指定的限制至少五秒，将生成事件。</span><span class="sxs-lookup"><span data-stu-id="e7efa-105">It is guaranteed that an event will be generated if a query exceeds the specified limit by at least five seconds.</span></span> <span data-ttu-id="e7efa-106">然而，如果查询超出指定的阈值少于五秒，则其检测可能会丢失，具体取决于查询计时和上次检测清扫的时间。</span><span class="sxs-lookup"><span data-stu-id="e7efa-106">However, if a query exceeds the specified threshold by less than five seconds, its detection might be missed depending on the timing of the query and the time of last detection sweep.</span></span>  
  
## <a name="cpu-threshold-exceeded-data-columns"></a><span data-ttu-id="e7efa-107">CPU Threshold Exceeded 数据列</span><span class="sxs-lookup"><span data-stu-id="e7efa-107">CPU Threshold Exceeded Data Columns</span></span>  
  
|<span data-ttu-id="e7efa-108">数据列名称</span><span class="sxs-lookup"><span data-stu-id="e7efa-108">Data column name</span></span>|<span data-ttu-id="e7efa-109">数据类型</span><span class="sxs-lookup"><span data-stu-id="e7efa-109">Data type</span></span>|<span data-ttu-id="e7efa-110">说明</span><span class="sxs-lookup"><span data-stu-id="e7efa-110">Description</span></span>|<span data-ttu-id="e7efa-111">列 ID</span><span class="sxs-lookup"><span data-stu-id="e7efa-111">Column ID</span></span>|<span data-ttu-id="e7efa-112">可筛选</span><span class="sxs-lookup"><span data-stu-id="e7efa-112">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="e7efa-113">CPU</span><span class="sxs-lookup"><span data-stu-id="e7efa-113">CPU</span></span>|`int`|<span data-ttu-id="e7efa-114">CPU 使用率，以毫秒为单位。</span><span class="sxs-lookup"><span data-stu-id="e7efa-114">CPU usage in milliseconds.</span></span>|<span data-ttu-id="e7efa-115">18</span><span class="sxs-lookup"><span data-stu-id="e7efa-115">18</span></span>|<span data-ttu-id="e7efa-116">是</span><span class="sxs-lookup"><span data-stu-id="e7efa-116">Yes</span></span>|  
|<span data-ttu-id="e7efa-117">EventClass</span><span class="sxs-lookup"><span data-stu-id="e7efa-117">EventClass</span></span>|`int`|<span data-ttu-id="e7efa-118">214</span><span class="sxs-lookup"><span data-stu-id="e7efa-118">214</span></span>|<span data-ttu-id="e7efa-119">27</span><span class="sxs-lookup"><span data-stu-id="e7efa-119">27</span></span>|<span data-ttu-id="e7efa-120">否</span><span class="sxs-lookup"><span data-stu-id="e7efa-120">No</span></span>|  
|<span data-ttu-id="e7efa-121">EventSubClass</span><span class="sxs-lookup"><span data-stu-id="e7efa-121">EventSubClass</span></span>|`int`|<span data-ttu-id="e7efa-122">CPU 限制冲突。</span><span class="sxs-lookup"><span data-stu-id="e7efa-122">CPU limit violation.</span></span>|<span data-ttu-id="e7efa-123">21</span><span class="sxs-lookup"><span data-stu-id="e7efa-123">21</span></span>|<span data-ttu-id="e7efa-124">是</span><span class="sxs-lookup"><span data-stu-id="e7efa-124">Yes</span></span>|  
|<span data-ttu-id="e7efa-125">GroupID</span><span class="sxs-lookup"><span data-stu-id="e7efa-125">GroupID</span></span>|`int`|<span data-ttu-id="e7efa-126">发生冲突的组 ID。</span><span class="sxs-lookup"><span data-stu-id="e7efa-126">Group ID where the violation occurred.</span></span>|<span data-ttu-id="e7efa-127">66</span><span class="sxs-lookup"><span data-stu-id="e7efa-127">66</span></span>|<span data-ttu-id="e7efa-128">是</span><span class="sxs-lookup"><span data-stu-id="e7efa-128">Yes</span></span>|  
|<span data-ttu-id="e7efa-129">OwnerID</span><span class="sxs-lookup"><span data-stu-id="e7efa-129">OwnerID</span></span>|`int`|<span data-ttu-id="e7efa-130">导致冲突的进程的 SPID。</span><span class="sxs-lookup"><span data-stu-id="e7efa-130">SPID of the process that caused the violation.</span></span>|<span data-ttu-id="e7efa-131">58</span><span class="sxs-lookup"><span data-stu-id="e7efa-131">58</span></span>|<span data-ttu-id="e7efa-132">是</span><span class="sxs-lookup"><span data-stu-id="e7efa-132">Yes</span></span>|  
|<span data-ttu-id="e7efa-133">SPID</span><span class="sxs-lookup"><span data-stu-id="e7efa-133">SPID</span></span>|`int`|<span data-ttu-id="e7efa-134">激发此事件的服务器进程的 ID。</span><span class="sxs-lookup"><span data-stu-id="e7efa-134">ID of the server process that fires this event.</span></span><br /><br /> <span data-ttu-id="e7efa-135">注意：如果系统线程将验证 CPU 使用率作为后台任务，则此 ID 可能与实际用户的 SPID 不同。</span><span class="sxs-lookup"><span data-stu-id="e7efa-135">Note: This can differ from the actual user SPID if a system thread validates CPU usage as a background task.</span></span>|<span data-ttu-id="e7efa-136">12</span><span class="sxs-lookup"><span data-stu-id="e7efa-136">12</span></span>|<span data-ttu-id="e7efa-137">是</span><span class="sxs-lookup"><span data-stu-id="e7efa-137">Yes</span></span>|  
|<span data-ttu-id="e7efa-138">StartTime</span><span class="sxs-lookup"><span data-stu-id="e7efa-138">StartTime</span></span>|`datetime`|<span data-ttu-id="e7efa-139">此事件的激发时间。</span><span class="sxs-lookup"><span data-stu-id="e7efa-139">The time when this event fired.</span></span>|<span data-ttu-id="e7efa-140">14</span><span class="sxs-lookup"><span data-stu-id="e7efa-140">14</span></span>|<span data-ttu-id="e7efa-141">是</span><span class="sxs-lookup"><span data-stu-id="e7efa-141">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7efa-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7efa-142">See Also</span></span>  
 [<span data-ttu-id="e7efa-143">sp_trace_setevent (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e7efa-143">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
