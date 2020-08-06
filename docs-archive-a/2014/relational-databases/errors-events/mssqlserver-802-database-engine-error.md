---
title: MSSQLSERVER_802 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 802 (Database Engine error)
ms.assetid: 5892ed24-4dcb-4bf9-a8a4-a7ca898832d5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9edcdda1410d7651f7c7531ef98c64c85741f15a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591911"
---
# <a name="mssqlserver_802"></a><span data-ttu-id="1b5df-102">MSSQLSERVER_802</span><span class="sxs-lookup"><span data-stu-id="1b5df-102">MSSQLSERVER_802</span></span>
    
## <a name="details"></a><span data-ttu-id="1b5df-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="1b5df-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1b5df-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="1b5df-104">Product Name</span></span>|<span data-ttu-id="1b5df-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1b5df-105">SQL Server</span></span>|  
|<span data-ttu-id="1b5df-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="1b5df-106">Event ID</span></span>|<span data-ttu-id="1b5df-107">802</span><span class="sxs-lookup"><span data-stu-id="1b5df-107">802</span></span>|  
|<span data-ttu-id="1b5df-108">事件源</span><span class="sxs-lookup"><span data-stu-id="1b5df-108">Event Source</span></span>|<span data-ttu-id="1b5df-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1b5df-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1b5df-110">组件</span><span class="sxs-lookup"><span data-stu-id="1b5df-110">Component</span></span>|<span data-ttu-id="1b5df-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1b5df-111">SQLEngine</span></span>|  
|<span data-ttu-id="1b5df-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="1b5df-112">Symbolic Name</span></span>|<span data-ttu-id="1b5df-113">NO_BUFS</span><span class="sxs-lookup"><span data-stu-id="1b5df-113">NO_BUFS</span></span>|  
|<span data-ttu-id="1b5df-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="1b5df-114">Message Text</span></span>|<span data-ttu-id="1b5df-115">缓冲池中的可用内存不足。</span><span class="sxs-lookup"><span data-stu-id="1b5df-115">There is insufficient memory available in the buffer pool.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1b5df-116">说明</span><span class="sxs-lookup"><span data-stu-id="1b5df-116">Explanation</span></span>  
 <span data-ttu-id="1b5df-117">当缓冲池已满且缓冲池无法再增大时，会导致此错误。</span><span class="sxs-lookup"><span data-stu-id="1b5df-117">This is caused when the buffer pool is full and the buffer pool can not grow any larger.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1b5df-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="1b5df-118">User Action</span></span>  
 <span data-ttu-id="1b5df-119">下面的列表概述了有助于解决内存错误的一般步骤：</span><span class="sxs-lookup"><span data-stu-id="1b5df-119">The following list outlines general steps that will help in troubleshooting memory errors:</span></span>  
  
1.  <span data-ttu-id="1b5df-120">验证其他应用程序或服务是否占用此服务器上的内存。</span><span class="sxs-lookup"><span data-stu-id="1b5df-120">Verify whether other applications or services are consuming memory on this server.</span></span> <span data-ttu-id="1b5df-121">重新配置不太重要的应用程序或服务，使其占用更少的内存。</span><span class="sxs-lookup"><span data-stu-id="1b5df-121">Reconfigure less critical applications or services to consume less memory.</span></span>  
  
2.  <span data-ttu-id="1b5df-122">开始收集以下内容的性能监视器计数器：[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **:Buffer Manager**、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **:Memory Manager**。</span><span class="sxs-lookup"><span data-stu-id="1b5df-122">Start collecting performance monitor counters for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**: Buffer Manager**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**: Memory Manager**.</span></span>  
  
3.  <span data-ttu-id="1b5df-123">检查下面的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内存配置参数：</span><span class="sxs-lookup"><span data-stu-id="1b5df-123">Check the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory configuration parameters:</span></span>  
  
    -   <span data-ttu-id="1b5df-124">**max server memory**</span><span class="sxs-lookup"><span data-stu-id="1b5df-124">**max server memory**</span></span>  
  
    -   <span data-ttu-id="1b5df-125">**min server memory**</span><span class="sxs-lookup"><span data-stu-id="1b5df-125">**min server memory**</span></span>  
  
    -   <span data-ttu-id="1b5df-126">**min memory per query**</span><span class="sxs-lookup"><span data-stu-id="1b5df-126">**min memory per query**</span></span>  
  
     <span data-ttu-id="1b5df-127">注意任何不寻常的设置，并根据需要更正它们。</span><span class="sxs-lookup"><span data-stu-id="1b5df-127">Notice any unusual settings and correct them as necessary.</span></span> <span data-ttu-id="1b5df-128">满足 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的更高内存要求。</span><span class="sxs-lookup"><span data-stu-id="1b5df-128">Account for increased memory requirements for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1b5df-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书的“设置服务器配置选项”中列出了默认设置。</span><span class="sxs-lookup"><span data-stu-id="1b5df-129">Default settings are listed in "Setting Server Configuration Options" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
4.  <span data-ttu-id="1b5df-130">在您看到这些错误消息时，观察 DBCC MEMORYSTATUS 输出及其变化情况。</span><span class="sxs-lookup"><span data-stu-id="1b5df-130">Observe DBCC MEMORYSTATUS output and the way it changes when you see these error messages.</span></span>  
  
5.  <span data-ttu-id="1b5df-131">检查工作负荷（并发会话数、当前执行的查询）。</span><span class="sxs-lookup"><span data-stu-id="1b5df-131">Check the workload (number of concurrent sessions, currently executing queries).</span></span>  
  
 <span data-ttu-id="1b5df-132">以下操作可能会为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供更多内存：</span><span class="sxs-lookup"><span data-stu-id="1b5df-132">The following actions may make more memory available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="1b5df-133">如果除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 外的应用程序正在占用资源，请尝试停止这些应用程序，或者在单独的服务器上运行它们。</span><span class="sxs-lookup"><span data-stu-id="1b5df-133">If applications besides [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are consuming resources, try stopping these applications or running them on a separate server.</span></span>  
  
-   <span data-ttu-id="1b5df-134">如果已配置 **max server memory**，请增大该设置。</span><span class="sxs-lookup"><span data-stu-id="1b5df-134">If you have configured **max server memory,** increase the setting.</span></span>  
  
 <span data-ttu-id="1b5df-135">运行以下 DBCC 命令以释放一些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内存缓存。</span><span class="sxs-lookup"><span data-stu-id="1b5df-135">Run the following DBCC commands to free several [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory caches.</span></span>  
  
-   <span data-ttu-id="1b5df-136">DBCC FREESYSTEMCACHE</span><span class="sxs-lookup"><span data-stu-id="1b5df-136">DBCC FREESYSTEMCACHE</span></span>  
  
-   <span data-ttu-id="1b5df-137">DBCC FREESESSIONCACHE</span><span class="sxs-lookup"><span data-stu-id="1b5df-137">DBCC FREESESSIONCACHE</span></span>  
  
-   <span data-ttu-id="1b5df-138">DBCC FREEPROCCACHE</span><span class="sxs-lookup"><span data-stu-id="1b5df-138">DBCC FREEPROCCACHE</span></span>  
  
 <span data-ttu-id="1b5df-139">如果问题仍存在，则您将需要进一步调查，可能需要减小工作负荷。</span><span class="sxs-lookup"><span data-stu-id="1b5df-139">If the problem continues, you will need to investigate further and possibly reduce workload.</span></span>  
  
  
