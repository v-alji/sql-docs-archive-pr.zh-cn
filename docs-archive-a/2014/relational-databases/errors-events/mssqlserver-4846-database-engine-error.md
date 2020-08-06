---
title: MSSQLSERVER_4846 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 4846 (Database Engine error)
ms.assetid: a455e809-1883-4c7d-b3e3-835ee5bfe258
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 923137645aae72476fb4b2ae33f0cbbf3e81c2a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688925"
---
# <a name="mssqlserver_4846"></a><span data-ttu-id="dd3f6-102">MSSQLSERVER_4846</span><span class="sxs-lookup"><span data-stu-id="dd3f6-102">MSSQLSERVER_4846</span></span>
    
## <a name="details"></a><span data-ttu-id="dd3f6-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="dd3f6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dd3f6-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="dd3f6-104">Product Name</span></span>|<span data-ttu-id="dd3f6-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="dd3f6-105">SQL Server</span></span>|  
|<span data-ttu-id="dd3f6-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="dd3f6-106">Event ID</span></span>|<span data-ttu-id="dd3f6-107">4846</span><span class="sxs-lookup"><span data-stu-id="dd3f6-107">4846</span></span>|  
|<span data-ttu-id="dd3f6-108">事件源</span><span class="sxs-lookup"><span data-stu-id="dd3f6-108">Event Source</span></span>|<span data-ttu-id="dd3f6-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="dd3f6-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="dd3f6-110">组件</span><span class="sxs-lookup"><span data-stu-id="dd3f6-110">Component</span></span>|<span data-ttu-id="dd3f6-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="dd3f6-111">SQLEngine</span></span>|  
|<span data-ttu-id="dd3f6-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="dd3f6-112">Symbolic Name</span></span>|<span data-ttu-id="dd3f6-113">BULKPROV_MEMORY</span><span class="sxs-lookup"><span data-stu-id="dd3f6-113">BULKPROV_MEMORY</span></span>|  
|<span data-ttu-id="dd3f6-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="dd3f6-114">Message Text</span></span>|<span data-ttu-id="dd3f6-115">大容量数据提供程序分配内存失败。</span><span class="sxs-lookup"><span data-stu-id="dd3f6-115">The bulk data provider failed to allocate memory.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="dd3f6-116">说明</span><span class="sxs-lookup"><span data-stu-id="dd3f6-116">Explanation</span></span>  
 <span data-ttu-id="dd3f6-117">内存分配失败。</span><span class="sxs-lookup"><span data-stu-id="dd3f6-117">Memory allocation failed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dd3f6-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="dd3f6-118">User Action</span></span>  
 <span data-ttu-id="dd3f6-119">执行以下一般步骤以解决内存错误：</span><span class="sxs-lookup"><span data-stu-id="dd3f6-119">Follow these general steps to troubleshoot memory errors:</span></span>  
  
1.  <span data-ttu-id="dd3f6-120">验证其他应用程序或服务是否占用此服务器上的内存。</span><span class="sxs-lookup"><span data-stu-id="dd3f6-120">Verify whether other applications or services are consuming memory on this server.</span></span> <span data-ttu-id="dd3f6-121">重新配置不太重要的应用程序或服务，使其占用更少的内存。</span><span class="sxs-lookup"><span data-stu-id="dd3f6-121">Reconfigure less critical applications or services to consume less memory.</span></span>  
  
2.  <span data-ttu-id="dd3f6-122">开始收集以下内容的性能监视器计数器：**SQL Server:Buffer Manager**、**SQL Server:Memory Manager**。</span><span class="sxs-lookup"><span data-stu-id="dd3f6-122">Start collecting performance monitor counters for **SQL Server: Buffer Manager**, **SQL Server: Memory Manager**.</span></span>  
  
3.  <span data-ttu-id="dd3f6-123">检查以下 SQL Server 内存配置参数：</span><span class="sxs-lookup"><span data-stu-id="dd3f6-123">Check the following SQL Server memory configuration parameters:</span></span>  
  
    -   <span data-ttu-id="dd3f6-124">**max server memory**</span><span class="sxs-lookup"><span data-stu-id="dd3f6-124">**max server memory**</span></span>  
  
    -   <span data-ttu-id="dd3f6-125">**min server memory**</span><span class="sxs-lookup"><span data-stu-id="dd3f6-125">**min server memory**</span></span>  
  
    -   <span data-ttu-id="dd3f6-126">**min memory per query**</span><span class="sxs-lookup"><span data-stu-id="dd3f6-126">**min memory per query**</span></span>  
  
     <span data-ttu-id="dd3f6-127">注意任何不寻常的设置。</span><span class="sxs-lookup"><span data-stu-id="dd3f6-127">Notice any unusual settings.</span></span> <span data-ttu-id="dd3f6-128">根据需要更正它们。</span><span class="sxs-lookup"><span data-stu-id="dd3f6-128">Correct them as necessary.</span></span> <span data-ttu-id="dd3f6-129">满足 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的内存要求。</span><span class="sxs-lookup"><span data-stu-id="dd3f6-129">Account for memory requirements for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="dd3f6-130">SQL Server 联机丛书的“设置服务器配置选项”中列出了默认设置。</span><span class="sxs-lookup"><span data-stu-id="dd3f6-130">Default settings are listed in "Setting Server Configuration Options" in SQL Server Books Online.</span></span>  
  
4.  <span data-ttu-id="dd3f6-131">在您看到这些错误消息时，观察 DBCC MEMORYSTATUS 输出及其变化情况。</span><span class="sxs-lookup"><span data-stu-id="dd3f6-131">Observe DBCC MEMORYSTATUS output and the way it changes when you see these error messages.</span></span>  
  
5.  <span data-ttu-id="dd3f6-132">检查工作负荷（例如，并发会话数，当前执行的查询）。</span><span class="sxs-lookup"><span data-stu-id="dd3f6-132">Check the workload (for example, number of concurrent sessions, currently executing queries).</span></span>  
  
 <span data-ttu-id="dd3f6-133">以下操作可能会为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供更多内存：</span><span class="sxs-lookup"><span data-stu-id="dd3f6-133">The following actions may make more memory available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="dd3f6-134">如果除 SQL Server 外的应用程序正在占用资源，请尝试停止运行这些应用程序，或者考虑在单独的服务器上运行它们。</span><span class="sxs-lookup"><span data-stu-id="dd3f6-134">If applications besides SQL Server are consuming resources, try stopping running these applications or consider running them on a separate server.</span></span> <span data-ttu-id="dd3f6-135">这样做将消除外部内存压力。</span><span class="sxs-lookup"><span data-stu-id="dd3f6-135">This will remove external memory pressure.</span></span>  
  
-   <span data-ttu-id="dd3f6-136">如果已配置 **max server memory**，请增大其设置。</span><span class="sxs-lookup"><span data-stu-id="dd3f6-136">If you have configured **max server memory,** increase its setting.</span></span>  
  
 <span data-ttu-id="dd3f6-137">运行以下 DBCC 命令以释放一些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内存缓存。</span><span class="sxs-lookup"><span data-stu-id="dd3f6-137">Run the following DBCC commands to free several [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory caches.</span></span>  
  
-   <span data-ttu-id="dd3f6-138">DBCC FREESYSTEMCACHE</span><span class="sxs-lookup"><span data-stu-id="dd3f6-138">DBCC FREESYSTEMCACHE</span></span>  
  
-   <span data-ttu-id="dd3f6-139">DBCC FREESESSIONCACHE</span><span class="sxs-lookup"><span data-stu-id="dd3f6-139">DBCC FREESESSIONCACHE</span></span>  
  
-   <span data-ttu-id="dd3f6-140">DBCC FREEPROCCACHE</span><span class="sxs-lookup"><span data-stu-id="dd3f6-140">DBCC FREEPROCCACHE</span></span>  
  
 <span data-ttu-id="dd3f6-141">如果问题仍存在，则您将需要进一步调查，可能需要减小工作负荷。</span><span class="sxs-lookup"><span data-stu-id="dd3f6-141">If the problem continues, you will need to investigate further and possibly reduce workload.</span></span>  
  
  
