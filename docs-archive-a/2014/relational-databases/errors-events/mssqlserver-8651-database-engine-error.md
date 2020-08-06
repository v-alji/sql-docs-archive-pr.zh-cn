---
title: MSSQLSERVER_8651 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8651 (Database Engine error)
ms.assetid: 4cc3498d-5449-4c4e-b1f9-3271831c725a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 43a385350a05edee3759ab83d318e365f5b4f3e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688922"
---
# <a name="mssqlserver_8651"></a><span data-ttu-id="32bee-102">MSSQLSERVER_8651</span><span class="sxs-lookup"><span data-stu-id="32bee-102">MSSQLSERVER_8651</span></span>
    
## <a name="details"></a><span data-ttu-id="32bee-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="32bee-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="32bee-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="32bee-104">Product Name</span></span>|<span data-ttu-id="32bee-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="32bee-105">SQL Server</span></span>|  
|<span data-ttu-id="32bee-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="32bee-106">Event ID</span></span>|<span data-ttu-id="32bee-107">8651</span><span class="sxs-lookup"><span data-stu-id="32bee-107">8651</span></span>|  
|<span data-ttu-id="32bee-108">事件源</span><span class="sxs-lookup"><span data-stu-id="32bee-108">Event Source</span></span>|<span data-ttu-id="32bee-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="32bee-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="32bee-110">组件</span><span class="sxs-lookup"><span data-stu-id="32bee-110">Component</span></span>|<span data-ttu-id="32bee-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="32bee-111">SQLEngine</span></span>|  
|<span data-ttu-id="32bee-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="32bee-112">Symbolic Name</span></span>|<span data-ttu-id="32bee-113">MEMGRANT_ERR</span><span class="sxs-lookup"><span data-stu-id="32bee-113">MEMGRANT_ERR</span></span>|  
|<span data-ttu-id="32bee-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="32bee-114">Message Text</span></span>|<span data-ttu-id="32bee-115">未能执行所请求的操作，因为可用内存少于最小查询内存。</span><span class="sxs-lookup"><span data-stu-id="32bee-115">Could not perform the requested operation because the minimum query memory is not available.</span></span> <span data-ttu-id="32bee-116">请减小“每次查询占用的最小内存”服务器配置选项的配置值。</span><span class="sxs-lookup"><span data-stu-id="32bee-116">Decrease the configured value for the 'min memory per query' server configuration option.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="32bee-117">说明</span><span class="sxs-lookup"><span data-stu-id="32bee-117">Explanation</span></span>  
 <span data-ttu-id="32bee-118">其他进程正在占用服务器内存（在服务器中施加内存压力）。</span><span class="sxs-lookup"><span data-stu-id="32bee-118">Other processes are consuming server memory (exerting memory pressure in the server).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="32bee-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="32bee-119">User Action</span></span>  
 <span data-ttu-id="32bee-120">减小“每次查询占用的最小内存”服务器配置选项的配置值，或者减少服务器的查询负载。</span><span class="sxs-lookup"><span data-stu-id="32bee-120">Either decrease the configured value for the min memory per query' server configuration option or reduce the query load to the server.</span></span>  
  
 <span data-ttu-id="32bee-121">下面的列表概述了有助于解决内存错误的一般步骤：</span><span class="sxs-lookup"><span data-stu-id="32bee-121">The following list outlines general steps that will help in troubleshooting memory errors:</span></span>  
  
1.  <span data-ttu-id="32bee-122">验证其他应用程序或服务是否占用此服务器上的内存。</span><span class="sxs-lookup"><span data-stu-id="32bee-122">Verify whether other applications or services are consuming memory on this server.</span></span> <span data-ttu-id="32bee-123">重新配置不太重要的应用程序或服务，使其占用更少的内存。</span><span class="sxs-lookup"><span data-stu-id="32bee-123">Reconfigure less critical applications or services to consume less memory.</span></span>  
  
2.  <span data-ttu-id="32bee-124">开始收集以下内容的性能监视器计数器：**SQL Server:Buffer Manager**、**SQL Server:Memory Manager**。</span><span class="sxs-lookup"><span data-stu-id="32bee-124">Start collecting performance monitor counters for **SQL Server: Buffer Manager**, **SQL Server: Memory Manager**.</span></span>  
  
3.  <span data-ttu-id="32bee-125">检查下面的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内存配置参数：</span><span class="sxs-lookup"><span data-stu-id="32bee-125">Check the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory configuration parameters:</span></span>  
  
    -   <span data-ttu-id="32bee-126">**max server memory**</span><span class="sxs-lookup"><span data-stu-id="32bee-126">**max server memory**</span></span>  
  
    -   <span data-ttu-id="32bee-127">**min server memory**</span><span class="sxs-lookup"><span data-stu-id="32bee-127">**min server memory**</span></span>  
  
    -   <span data-ttu-id="32bee-128">**min memory per query**</span><span class="sxs-lookup"><span data-stu-id="32bee-128">**min memory per query**</span></span>  
  
     <span data-ttu-id="32bee-129">注意不正常的设置。</span><span class="sxs-lookup"><span data-stu-id="32bee-129">Notice unusual settings.</span></span> <span data-ttu-id="32bee-130">根据需要更正它们。</span><span class="sxs-lookup"><span data-stu-id="32bee-130">Correct them as necessary.</span></span> <span data-ttu-id="32bee-131">SQL Server 联机丛书的“设置服务器配置选项”中列出了默认设置。</span><span class="sxs-lookup"><span data-stu-id="32bee-131">Default settings are listed in "Setting Server Configuration Options" in SQL Server Books Online.</span></span>  
  
4.  <span data-ttu-id="32bee-132">检查工作负荷（例如，并发会话数，当前执行的查询）。</span><span class="sxs-lookup"><span data-stu-id="32bee-132">Check the workload (for example, number of concurrent sessions, currently executing queries).</span></span>  
  
 <span data-ttu-id="32bee-133">以下操作可能会为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供更多内存：</span><span class="sxs-lookup"><span data-stu-id="32bee-133">The following actions may make more memory available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="32bee-134">如果除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 外的应用程序正在占用资源，请尝试停止运行这些应用程序，或者考虑在单独的服务器上运行它们。</span><span class="sxs-lookup"><span data-stu-id="32bee-134">If applications besides [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are consuming resources, try stopping running these applications or consider running them on a separate server.</span></span> <span data-ttu-id="32bee-135">这样做将消除外部内存压力。</span><span class="sxs-lookup"><span data-stu-id="32bee-135">This will remove external memory pressure.</span></span>  
  
-   <span data-ttu-id="32bee-136">如果已配置 **max server memory**，请增大其设置。</span><span class="sxs-lookup"><span data-stu-id="32bee-136">If you have configured **max server memory,** increase its setting.</span></span>  
  
 <span data-ttu-id="32bee-137">运行以下 DBCC 命令以释放一些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内存缓存。</span><span class="sxs-lookup"><span data-stu-id="32bee-137">Run the following DBCC commands to free several [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory caches.</span></span>  
  
-   <span data-ttu-id="32bee-138">DBCC FREESYSTEMCACHE</span><span class="sxs-lookup"><span data-stu-id="32bee-138">DBCC FREESYSTEMCACHE</span></span>  
  
-   <span data-ttu-id="32bee-139">DBCC FREESESSIONCACHE</span><span class="sxs-lookup"><span data-stu-id="32bee-139">DBCC FREESESSIONCACHE</span></span>  
  
-   <span data-ttu-id="32bee-140">DBCC FREEPROCCACHE</span><span class="sxs-lookup"><span data-stu-id="32bee-140">DBCC FREEPROCCACHE</span></span>  
  
 <span data-ttu-id="32bee-141">如果问题仍存在，则您将需要进一步调查，可能需要减小工作负荷。</span><span class="sxs-lookup"><span data-stu-id="32bee-141">If the problem continues, you will need to investigate further and possibly reduce workload.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32bee-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="32bee-142">See Also</span></span>  
 <span data-ttu-id="32bee-143">[DBCC FREESYSTEMCACHE &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-freesystemcache-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="32bee-143">[DBCC FREESYSTEMCACHE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-freesystemcache-transact-sql) </span></span>  
 <span data-ttu-id="32bee-144">[DBCC FREESESSIONCACHE &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-freesessioncache-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="32bee-144">[DBCC FREESESSIONCACHE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-freesessioncache-transact-sql) </span></span>  
 <span data-ttu-id="32bee-145">[DBCC FREEPROCCACHE &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-freeproccache-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="32bee-145">[DBCC FREEPROCCACHE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-freeproccache-transact-sql) </span></span>  
 <span data-ttu-id="32bee-146">[服务器配置选项 (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="32bee-146">[Server Configuration Options &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="32bee-147">[SQL Server Buffer Manager 对象](../performance-monitor/sql-server-buffer-manager-object.md) </span><span class="sxs-lookup"><span data-stu-id="32bee-147">[SQL Server, Buffer Manager Object](../performance-monitor/sql-server-buffer-manager-object.md) </span></span>  
 [<span data-ttu-id="32bee-148">SQL Server - Memory Manager 对象</span><span class="sxs-lookup"><span data-stu-id="32bee-148">SQL Server, Memory Manager Object</span></span>](../performance-monitor/sql-server-memory-manager-object.md)  
  
  
