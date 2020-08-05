---
title: MSSQLSERVER_701 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 701 (Database Engine error)
ms.assetid: 3b975000-63a1-43c2-a40f-89d0a8a36bef
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 542535223d3e394c72079092411add143de61545
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580276"
---
# <a name="mssqlserver_701"></a><span data-ttu-id="de4b0-102">MSSQLSERVER_701</span><span class="sxs-lookup"><span data-stu-id="de4b0-102">MSSQLSERVER_701</span></span>
    
## <a name="details"></a><span data-ttu-id="de4b0-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="de4b0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="de4b0-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="de4b0-104">Product Name</span></span>|<span data-ttu-id="de4b0-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="de4b0-105">SQL Server</span></span>|  
|<span data-ttu-id="de4b0-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="de4b0-106">Event ID</span></span>|<span data-ttu-id="de4b0-107">701</span><span class="sxs-lookup"><span data-stu-id="de4b0-107">701</span></span>|  
|<span data-ttu-id="de4b0-108">事件源</span><span class="sxs-lookup"><span data-stu-id="de4b0-108">Event Source</span></span>|<span data-ttu-id="de4b0-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="de4b0-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="de4b0-110">组件</span><span class="sxs-lookup"><span data-stu-id="de4b0-110">Component</span></span>|<span data-ttu-id="de4b0-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="de4b0-111">SQLEngine</span></span>|  
|<span data-ttu-id="de4b0-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="de4b0-112">Symbolic Name</span></span>|<span data-ttu-id="de4b0-113">NOSYSMEM</span><span class="sxs-lookup"><span data-stu-id="de4b0-113">NOSYSMEM</span></span>|  
|<span data-ttu-id="de4b0-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="de4b0-114">Message Text</span></span>|<span data-ttu-id="de4b0-115">系统内存不足，无法运行此查询。</span><span class="sxs-lookup"><span data-stu-id="de4b0-115">There is insufficient system memory to run this query.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="de4b0-116">说明</span><span class="sxs-lookup"><span data-stu-id="de4b0-116">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="de4b0-117">无法分配足够的内存来运行查询。</span><span class="sxs-lookup"><span data-stu-id="de4b0-117">has failed to allocate sufficient memory to run the query.</span></span> <span data-ttu-id="de4b0-118">这可能是由多种原因造成的，包括操作系统设置，物理内存可用性或当前工作负载的内存限制。</span><span class="sxs-lookup"><span data-stu-id="de4b0-118">This can be caused by a variety of reasons including operating system settings, physical memory availability, or memory limits on the current workload.</span></span> <span data-ttu-id="de4b0-119">在大多数情况下，失败的事务不是此错误的原因。</span><span class="sxs-lookup"><span data-stu-id="de4b0-119">In most cases, the transaction that failed is not the cause of this error.</span></span>  
  
 <span data-ttu-id="de4b0-120">由于服务器没有足够的内存，诊断查询（如 DBCC 语句）可能失败。</span><span class="sxs-lookup"><span data-stu-id="de4b0-120">Diagnostic queries, such as DBCC statements, may fail because server the does not have sufficient memory.</span></span>  
  
 <span data-ttu-id="de4b0-121">等待资源池“default”中的内存资源来执行该查询时发生超时。</span><span class="sxs-lookup"><span data-stu-id="de4b0-121">A timeout occurred while waiting for memory resources to execute the query in the resource pool 'default'.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="de4b0-122">用户操作</span><span class="sxs-lookup"><span data-stu-id="de4b0-122">User Action</span></span>  
 <span data-ttu-id="de4b0-123">如果您未在使用资源调控器，我们建议您对整个服务器状态或负荷进行验证，或者检查资源池或工作负荷组设置。</span><span class="sxs-lookup"><span data-stu-id="de4b0-123">If you are not using Resource Governor, we recommend that you verify the overall server state and load, or check the resource pool or workload group settings.</span></span>  
  
 <span data-ttu-id="de4b0-124">下面的列表概述了有助于解决内存错误的一般步骤：</span><span class="sxs-lookup"><span data-stu-id="de4b0-124">The following list outlines general steps that will help in troubleshooting memory errors:</span></span>  
  
1.  <span data-ttu-id="de4b0-125">验证其他应用程序或服务是否占用此服务器上的内存。</span><span class="sxs-lookup"><span data-stu-id="de4b0-125">Verify whether other applications or services are consuming memory on this server.</span></span> <span data-ttu-id="de4b0-126">重新配置不太重要的应用程序或服务，使其占用更少的内存。</span><span class="sxs-lookup"><span data-stu-id="de4b0-126">Reconfigure less critical applications or services to consume less memory.</span></span>  
  
2.  <span data-ttu-id="de4b0-127">开始收集以下内容的性能监视器计数器：[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **:Buffer Manager**、 **SQL Server:Memory Manager**。</span><span class="sxs-lookup"><span data-stu-id="de4b0-127">Start collecting performance monitor counters for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**: Buffer Manager**, **SQL Server: Memory Manager**.</span></span>  
  
3.  <span data-ttu-id="de4b0-128">检查以下 SQL Server 内存配置参数：</span><span class="sxs-lookup"><span data-stu-id="de4b0-128">Check the following SQL Server memory configuration parameters:</span></span>  
  
    -   <span data-ttu-id="de4b0-129">**max server memory**</span><span class="sxs-lookup"><span data-stu-id="de4b0-129">**max server memory**</span></span>  
  
    -   <span data-ttu-id="de4b0-130">**min server memory**</span><span class="sxs-lookup"><span data-stu-id="de4b0-130">**min server memory**</span></span>  
  
    -   <span data-ttu-id="de4b0-131">**min memory per query**</span><span class="sxs-lookup"><span data-stu-id="de4b0-131">**min memory per query**</span></span>  
  
     <span data-ttu-id="de4b0-132">注意不正常的设置。</span><span class="sxs-lookup"><span data-stu-id="de4b0-132">Notice unusual settings.</span></span> <span data-ttu-id="de4b0-133">根据需要更正它们。</span><span class="sxs-lookup"><span data-stu-id="de4b0-133">Correct them as necessary.</span></span> <span data-ttu-id="de4b0-134">满足更高内存要求。</span><span class="sxs-lookup"><span data-stu-id="de4b0-134">Account for increased memory requirements.</span></span> <span data-ttu-id="de4b0-135">SQL Server 联机丛书的“设置服务器配置选项”中列出了默认设置。</span><span class="sxs-lookup"><span data-stu-id="de4b0-135">Default settings are listed in "Setting Server Configuration Options" in SQL Server Books Online.</span></span>  
  
4.  <span data-ttu-id="de4b0-136">在您看到这些错误消息时，观察 DBCC MEMORYSTATUS 输出及其变化情况。</span><span class="sxs-lookup"><span data-stu-id="de4b0-136">Observe DBCC MEMORYSTATUS output and the way it changes when you see these error messages.</span></span>  
  
5.  <span data-ttu-id="de4b0-137">检查工作负荷（例如，并发会话数，当前执行的查询）。</span><span class="sxs-lookup"><span data-stu-id="de4b0-137">Check the workload (for example, number of concurrent sessions, currently executing queries).</span></span>  
  
 <span data-ttu-id="de4b0-138">以下操作可能会为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供更多内存：</span><span class="sxs-lookup"><span data-stu-id="de4b0-138">The following actions may make more memory available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="de4b0-139">如果除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 外的应用程序正在占用资源，请尝试停止运行这些应用程序，或者考虑在单独的服务器上运行它们。</span><span class="sxs-lookup"><span data-stu-id="de4b0-139">If applications besides [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are consuming resources, try stopping running these applications or consider running them on a separate server.</span></span> <span data-ttu-id="de4b0-140">这样做将消除外部内存压力。</span><span class="sxs-lookup"><span data-stu-id="de4b0-140">This will remove external memory pressure.</span></span>  
  
-   <span data-ttu-id="de4b0-141">如果已配置 **max server memory**，请增大其设置。</span><span class="sxs-lookup"><span data-stu-id="de4b0-141">If you have configured **max server memory,** increase its setting.</span></span>  
  
 <span data-ttu-id="de4b0-142">运行以下 DBCC 命令以释放一些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内存缓存。</span><span class="sxs-lookup"><span data-stu-id="de4b0-142">Run the following DBCC commands to free several [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory caches.</span></span>  
  
-   <span data-ttu-id="de4b0-143">DBCC FREESYSTEMCACHE</span><span class="sxs-lookup"><span data-stu-id="de4b0-143">DBCC FREESYSTEMCACHE</span></span>  
  
-   <span data-ttu-id="de4b0-144">DBCC FREESESSIONCACHE</span><span class="sxs-lookup"><span data-stu-id="de4b0-144">DBCC FREESESSIONCACHE</span></span>  
  
-   <span data-ttu-id="de4b0-145">DBCC FREEPROCCACHE</span><span class="sxs-lookup"><span data-stu-id="de4b0-145">DBCC FREEPROCCACHE</span></span>  
  
 <span data-ttu-id="de4b0-146">如果问题仍存在，则您将需要进一步调查，可能需要减小工作负荷。</span><span class="sxs-lookup"><span data-stu-id="de4b0-146">If the problem continues, you will need to investigate further and possibly reduce workload.</span></span>  
  
  
