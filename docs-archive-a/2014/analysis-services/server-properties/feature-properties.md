---
title: 功能属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQMSupportEnabled property
- ComUdfEnabled property
- LinkToOtherInstanceEnabled property
- ManagedCodeEnabled property
- ConnStringEncryptionEnabled property
- LinkFromOtherInstanceEnabled property
- LinkInsideInstanceEnabled property
- UseCachedPageAllocators property
ms.assetid: a34d046a-6562-4d98-b827-37cebc6d77b4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 08001a172c1b39fb912ef042ed85effd4f8ededa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694590"
---
# <a name="feature-properties"></a><span data-ttu-id="a4155-102">功能属性</span><span class="sxs-lookup"><span data-stu-id="a4155-102">Feature Properties</span></span>
  <span data-ttu-id="a4155-103">功能属性与产品功能有关，大多数是高级属性，包括控制服务器实例之间的链接的属性。</span><span class="sxs-lookup"><span data-stu-id="a4155-103">Feature properties pertain to product features, most of them advanced, including properties that control links between server instances.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="a4155-104">支持下表中列出的服务器属性。</span><span class="sxs-lookup"><span data-stu-id="a4155-104">supports the server properties listed in the following table.</span></span> <span data-ttu-id="a4155-105">有关更多服务器属性以及如何设置这些属性的详细信息，请参阅 [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a4155-105">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="a4155-106">**适用于：** 仅限多维服务器模式</span><span class="sxs-lookup"><span data-stu-id="a4155-106">**Applies to:** Multidimensional server mode only</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a4155-107">属性</span><span class="sxs-lookup"><span data-stu-id="a4155-107">Properties</span></span>  
  
|<span data-ttu-id="a4155-108">属性</span><span class="sxs-lookup"><span data-stu-id="a4155-108">Property</span></span>|<span data-ttu-id="a4155-109">默认</span><span class="sxs-lookup"><span data-stu-id="a4155-109">Default</span></span>|<span data-ttu-id="a4155-110">说明</span><span class="sxs-lookup"><span data-stu-id="a4155-110">Description</span></span>|  
|--------------|-------------|-----------------|  
|`ManagedCodeEnabled`|<span data-ttu-id="a4155-111">1</span><span class="sxs-lookup"><span data-stu-id="a4155-111">1</span></span>|<span data-ttu-id="a4155-112">布尔值属性，指示是否启用 CLR 存储过程。</span><span class="sxs-lookup"><span data-stu-id="a4155-112">A Boolean property that indicates whether CLR storage procedures are enabled.</span></span>|  
|`LinkInsideInstanceEnabled`|<span data-ttu-id="a4155-113">1</span><span class="sxs-lookup"><span data-stu-id="a4155-113">1</span></span>|<span data-ttu-id="a4155-114">布尔值属性，指示是否可在同一个服务器实例内创建链接对象。</span><span class="sxs-lookup"><span data-stu-id="a4155-114">A Boolean property that indicates whether a linked object can be created inside the same server instance.</span></span>|  
|`LinkToOtherInstanceEnabled`|<span data-ttu-id="a4155-115">0</span><span class="sxs-lookup"><span data-stu-id="a4155-115">0</span></span>|<span data-ttu-id="a4155-116">布尔值属性，指示是否可链接到远程服务器上的对象。</span><span class="sxs-lookup"><span data-stu-id="a4155-116">A Boolean property that indicates whether objects on remote servers can be linked to.</span></span>|  
|`LinkFromOtherInstanceEnabled`|<span data-ttu-id="a4155-117">0</span><span class="sxs-lookup"><span data-stu-id="a4155-117">0</span></span>|<span data-ttu-id="a4155-118">布尔值属性，指示是否可从其他服务器实例链接到对象。</span><span class="sxs-lookup"><span data-stu-id="a4155-118">A Boolean property that indicates whether objects can be linked to from other server instances.</span></span>|  
|`ConnStringEncryptionEnabled`|<span data-ttu-id="a4155-119">1</span><span class="sxs-lookup"><span data-stu-id="a4155-119">1</span></span>|<span data-ttu-id="a4155-120">布尔值属性，指示是否在服务器配置文件中对连接字符串加密。</span><span class="sxs-lookup"><span data-stu-id="a4155-120">A Boolean property that indicates whether the connection string is encrypted in the server configuration file.</span></span>|  
|`UseCachedPageAllocators`|<span data-ttu-id="a4155-121">0</span><span class="sxs-lookup"><span data-stu-id="a4155-121">0</span></span>|<span data-ttu-id="a4155-122">布尔值属性，指示是否启用缓存页分配器。</span><span class="sxs-lookup"><span data-stu-id="a4155-122">A Boolean property that indicates whether cached page allocators are enabled.</span></span>|  
|`ComUdfEnabled`|<span data-ttu-id="a4155-123">0</span><span class="sxs-lookup"><span data-stu-id="a4155-123">0</span></span>|<span data-ttu-id="a4155-124">布尔值属性，指示是否启用定义为 COM 对象的用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="a4155-124">A Boolean property that indicates whether user-defined functions defined as COM objects are enabled.</span></span>|  
|`SQMSupportEnabled`|<span data-ttu-id="a4155-125">1</span><span class="sxs-lookup"><span data-stu-id="a4155-125">1</span></span>|<span data-ttu-id="a4155-126">布尔值属性，指示是否自动将错误和功能使用情况报告发送给 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a4155-126">A Boolean property that indicates whether error and feature usage reports are sent to [!INCLUDE[msCoName](../../includes/msconame-md.md)] automatically.</span></span>|  
|`ResourceMonitoringEnabled`|<span data-ttu-id="a4155-127">1</span><span class="sxs-lookup"><span data-stu-id="a4155-127">1</span></span>|<span data-ttu-id="a4155-128">布尔值属性，指示是否启用内部资源监视计数器。</span><span class="sxs-lookup"><span data-stu-id="a4155-128">A Boolean property that indicates whether internal resource monitoring counters are enabled.</span></span> <span data-ttu-id="a4155-129">默认情况下启用此属性。</span><span class="sxs-lookup"><span data-stu-id="a4155-129">This property is on by default.</span></span> <span data-ttu-id="a4155-130">启用时，此属性允许计数器收集有关 CPU、内存和 I/O 活动的使用情况数据。</span><span class="sxs-lookup"><span data-stu-id="a4155-130">When enabled, this property allows counters to collect usage data about CPU, memory, and I/O activity.</span></span><br /><br /> <span data-ttu-id="a4155-131">动态管理视图 (DMV) 使用内部资源监视计数器来报告资源使用情况。</span><span class="sxs-lookup"><span data-stu-id="a4155-131">Internal resource monitoring counters are used by Dynamic Management Views (DMV) that report on resource utilization.</span></span> <span data-ttu-id="a4155-132">如果您禁用此属性，DMV 查询仍然会运行，但结果集将无效。</span><span class="sxs-lookup"><span data-stu-id="a4155-132">If you disable this property, the DMV queries will still run, but the result set will be invalid.</span></span> <span data-ttu-id="a4155-133">依赖于该属性的 DMV 包括以下各项：</span><span class="sxs-lookup"><span data-stu-id="a4155-133">DMVs that depend on this property include the following:</span></span><br /><span data-ttu-id="a4155-134">**DISCOVER_OBJECT_ACTIVITY**</span><span class="sxs-lookup"><span data-stu-id="a4155-134">**DISCOVER_OBJECT_ACTIVITY**</span></span><br /><span data-ttu-id="a4155-135">**DISCOVER_COMMAND_OBJECTS**</span><span class="sxs-lookup"><span data-stu-id="a4155-135">**DISCOVER_COMMAND_OBJECTS**</span></span><br /><span data-ttu-id="a4155-136">**DISCOVER_SESSIONS** （适用于 SESSION_READS、SESSION_WRITES、SESSION_CPU_TIME_MS）</span><span class="sxs-lookup"><span data-stu-id="a4155-136">**DISCOVER_SESSIONS** (for SESSION_READS, SESSION_WRITES, SESSION_CPU_TIME_MS)</span></span><br /><br /> <br /><br /> <span data-ttu-id="a4155-137">在使用 NUMA 体系结构的多核系统上，禁用此属性可以提高查询性能，特别是对于较高的多用户工作负荷。</span><span class="sxs-lookup"><span data-stu-id="a4155-137">On a multi-core system that uses NUMA architecture, disabling this property can improve query performance, particularly for high multi-user workloads.</span></span> <span data-ttu-id="a4155-138">您将需要执行比较测试，以便确定查询性能是否由于更改此属性而得到改善。</span><span class="sxs-lookup"><span data-stu-id="a4155-138">You will need to run comparison tests to determine whether query performance is improved as the result of changing this property.</span></span> <span data-ttu-id="a4155-139">有关执行比较测试的最佳做法，包括清除缓存和避免常见错误，请参阅 [SQL Server 2008 R2 Analysis Services 操作指南](https://go.microsoft.com/fwlink/?LinkID=225539)。</span><span class="sxs-lookup"><span data-stu-id="a4155-139">For best practices on running comparison tests, including clearing the cache and avoiding common mistakes, see the [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a4155-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a4155-140">See Also</span></span>  
 <span data-ttu-id="a4155-141">[在 Analysis Services 中配置服务器属性](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="a4155-141">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 <span data-ttu-id="a4155-142">[确定 Analysis Services 实例的服务器模式](../instances/determine-the-server-mode-of-an-analysis-services-instance.md) </span><span class="sxs-lookup"><span data-stu-id="a4155-142">[Determine the Server Mode of an Analysis Services Instance](../instances/determine-the-server-mode-of-an-analysis-services-instance.md) </span></span>  
 [<span data-ttu-id="a4155-143">使用动态管理视图 (DMV) 监视 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="a4155-143">Use Dynamic Management Views &#40;DMVs&#41; to Monitor Analysis Services</span></span>](../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
