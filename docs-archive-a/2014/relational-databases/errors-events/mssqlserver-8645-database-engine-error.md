---
title: MSSQLSERVER_8645 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8645 (Database Engine error)
ms.assetid: 63d6d6d7-3850-4061-8e96-b1fa665e3180
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7be9774452e2008c34ecb52d228a0123992c5368
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588553"
---
# <a name="mssqlserver_8645"></a><span data-ttu-id="28e4c-102">MSSQLSERVER_8645</span><span class="sxs-lookup"><span data-stu-id="28e4c-102">MSSQLSERVER_8645</span></span>
    
## <a name="details"></a><span data-ttu-id="28e4c-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="28e4c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="28e4c-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="28e4c-104">Product Name</span></span>|<span data-ttu-id="28e4c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="28e4c-105">SQL Server</span></span>|  
|<span data-ttu-id="28e4c-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="28e4c-106">Event ID</span></span>|<span data-ttu-id="28e4c-107">8645</span><span class="sxs-lookup"><span data-stu-id="28e4c-107">8645</span></span>|  
|<span data-ttu-id="28e4c-108">事件源</span><span class="sxs-lookup"><span data-stu-id="28e4c-108">Event Source</span></span>|<span data-ttu-id="28e4c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="28e4c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="28e4c-110">组件</span><span class="sxs-lookup"><span data-stu-id="28e4c-110">Component</span></span>|<span data-ttu-id="28e4c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="28e4c-111">SQLEngine</span></span>|  
|<span data-ttu-id="28e4c-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="28e4c-112">Symbolic Name</span></span>|<span data-ttu-id="28e4c-113">MEMTIMEDOUT_ERR</span><span class="sxs-lookup"><span data-stu-id="28e4c-113">MEMTIMEDOUT_ERR</span></span>|  
|<span data-ttu-id="28e4c-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="28e4c-114">Message Text</span></span>|<span data-ttu-id="28e4c-115">等待内存资源来执行该查询时发生超时。</span><span class="sxs-lookup"><span data-stu-id="28e4c-115">A time out occurred while waiting for memory resources to execute the query.</span></span> <span data-ttu-id="28e4c-116">请重新运行查询。</span><span class="sxs-lookup"><span data-stu-id="28e4c-116">Rerun the query.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="28e4c-117">说明</span><span class="sxs-lookup"><span data-stu-id="28e4c-117">Explanation</span></span>  
 <span data-ttu-id="28e4c-118">等待资源池“default”中的内存资源来执行该查询时发生超时。</span><span class="sxs-lookup"><span data-stu-id="28e4c-118">A timeout occurred while waiting for memory resources to execute the query in the resource pool 'default'.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="28e4c-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="28e4c-119">User Action</span></span>  
 <span data-ttu-id="28e4c-120">如果您未在使用资源调控器，我们建议您对整个服务器状态或负荷进行验证，或者检查资源池或工作负荷组设置。</span><span class="sxs-lookup"><span data-stu-id="28e4c-120">If you are not using Resource Governor, we recommend that you verify the overall server state and load, or check the resource pool or workload group settings.</span></span>  
  
 <span data-ttu-id="28e4c-121">下面的列表概述了有助于解决内存错误的一般步骤：</span><span class="sxs-lookup"><span data-stu-id="28e4c-121">The following list outlines general steps that will help in troubleshooting memory errors:</span></span>  
  
1.  <span data-ttu-id="28e4c-122">验证其他应用程序或服务是否占用此服务器上的内存。</span><span class="sxs-lookup"><span data-stu-id="28e4c-122">Verify whether other applications or services are consuming memory on this server.</span></span> <span data-ttu-id="28e4c-123">重新配置不太重要的应用程序或服务，使其占用更少的内存。</span><span class="sxs-lookup"><span data-stu-id="28e4c-123">Reconfigure less critical applications or services to consume less memory.</span></span>  
  
2.  <span data-ttu-id="28e4c-124">开始收集以下内容的性能监视器计数器：**SQL Server:Buffer Manager**、**SQL Server:Memory Manager**。</span><span class="sxs-lookup"><span data-stu-id="28e4c-124">Start collecting performance monitor counters for **SQL Server: Buffer Manager**, **SQL Server: Memory Manager**.</span></span>  
  
3.  <span data-ttu-id="28e4c-125">检查以下 SQL Server 内存配置参数：</span><span class="sxs-lookup"><span data-stu-id="28e4c-125">Check the following SQL Server memory configuration parameters:</span></span>  
  
    -   <span data-ttu-id="28e4c-126">**max server memory**</span><span class="sxs-lookup"><span data-stu-id="28e4c-126">**max server memory**</span></span>  
  
    -   <span data-ttu-id="28e4c-127">**min server memory**</span><span class="sxs-lookup"><span data-stu-id="28e4c-127">**min server memory**</span></span>  
  
    -   <span data-ttu-id="28e4c-128">**min memory per query**</span><span class="sxs-lookup"><span data-stu-id="28e4c-128">**min memory per query**</span></span>  
  
     <span data-ttu-id="28e4c-129">注意不正常的设置。</span><span class="sxs-lookup"><span data-stu-id="28e4c-129">Notice unusual settings.</span></span> <span data-ttu-id="28e4c-130">根据需要更正它们。</span><span class="sxs-lookup"><span data-stu-id="28e4c-130">Correct them as necessary.</span></span> <span data-ttu-id="28e4c-131">满足 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的更高内存要求。</span><span class="sxs-lookup"><span data-stu-id="28e4c-131">Account for increased memory requirements for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="28e4c-132">SQL Server 联机丛书的“设置服务器配置选项”中列出了默认设置。</span><span class="sxs-lookup"><span data-stu-id="28e4c-132">Default settings are listed in "Setting Server Configuration Options" in SQL Server Books Online.</span></span>  
  
4.  <span data-ttu-id="28e4c-133">在您看到这些错误消息时，观察 DBCC MEMORYSTATUS 输出及其变化情况。</span><span class="sxs-lookup"><span data-stu-id="28e4c-133">Observe DBCC MEMORYSTATUS output and the way it changes when you see these error messages.</span></span>  
  
5.  <span data-ttu-id="28e4c-134">检查工作负荷（例如，并发会话数，当前执行的查询）。</span><span class="sxs-lookup"><span data-stu-id="28e4c-134">Check the workload (for example, number of concurrent sessions, currently executing queries).</span></span>  
  
 <span data-ttu-id="28e4c-135">以下操作可能会为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供更多内存：</span><span class="sxs-lookup"><span data-stu-id="28e4c-135">The following actions may make more memory available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="28e4c-136">如果除 SQL Server 外的应用程序正在占用资源，请尝试停止运行这些应用程序，或者考虑在单独的服务器上运行它们。</span><span class="sxs-lookup"><span data-stu-id="28e4c-136">If applications besides SQL Server are consuming resources, try stopping running these applications or consider running them on a separate server.</span></span> <span data-ttu-id="28e4c-137">这样做将消除外部内存压力。</span><span class="sxs-lookup"><span data-stu-id="28e4c-137">This will remove external memory pressure.</span></span>  
  
-   <span data-ttu-id="28e4c-138">如果已配置 **max server memory**，请增大其设置。</span><span class="sxs-lookup"><span data-stu-id="28e4c-138">If you have configured **max server memory,** increase its setting.</span></span>  
  
 <span data-ttu-id="28e4c-139">运行以下 DBCC 命令以释放几个 SQL Server 内存缓存。</span><span class="sxs-lookup"><span data-stu-id="28e4c-139">Run the following DBCC commands to free several SQL Server memory caches.</span></span>  
  
-   <span data-ttu-id="28e4c-140">DBCC FREESYSTEMCACHE</span><span class="sxs-lookup"><span data-stu-id="28e4c-140">DBCC FREESYSTEMCACHE</span></span>  
  
-   <span data-ttu-id="28e4c-141">DBCC FREESESSIONCACHE</span><span class="sxs-lookup"><span data-stu-id="28e4c-141">DBCC FREESESSIONCACHE</span></span>  
  
-   <span data-ttu-id="28e4c-142">DBCC FREEPROCCACHE</span><span class="sxs-lookup"><span data-stu-id="28e4c-142">DBCC FREEPROCCACHE</span></span>  
  
 <span data-ttu-id="28e4c-143">如果问题仍存在，则您将需要进一步调查，可能需要减小工作负荷。</span><span class="sxs-lookup"><span data-stu-id="28e4c-143">If the problem continues, you will need to investigate further and possibly reduce workload.</span></span>  
  
  
