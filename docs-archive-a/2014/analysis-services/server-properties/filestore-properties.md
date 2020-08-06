---
title: "\"%0\" 属性 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Income property
- InitialBonus property
- PercentScanPerPrice property
- FileStore properties
- BackgroundTrimCost property
- Tax property
- PerformanceTrace property
- MinimumBalance property
- UnbufferedThreshold property
- BackgroundTrimAmount property
- MaximumBalance property
- MemoryLimitMin property
- MemoryLimit property
ms.assetid: 580cf0aa-7425-4d48-aa8d-128f5b488fcd
author: minewiskan
ms.author: owend
ms.openlocfilehash: cc81273b55dea5820ef80f34c22d293492eb8055
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694588"
---
# <a name="filestore-properties"></a><span data-ttu-id="6099f-102">FileStore 属性</span><span class="sxs-lookup"><span data-stu-id="6099f-102">Filestore Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="6099f-103">支持下列各表中列出的文件存储服务器属性。</span><span class="sxs-lookup"><span data-stu-id="6099f-103">supports the filestore server properties listed in the following tables.</span></span> <span data-ttu-id="6099f-104">这些属性都是高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改这些属性。</span><span class="sxs-lookup"><span data-stu-id="6099f-104">These are all advanced properties that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span> <span data-ttu-id="6099f-105">有关更多服务器属性以及如何设置这些属性的详细信息，请参阅 [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="6099f-105">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="6099f-106">**适用于：** 多维和表格服务器模式</span><span class="sxs-lookup"><span data-stu-id="6099f-106">**Applies to:** Multidimensional and Tabular server mode</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6099f-107">属性</span><span class="sxs-lookup"><span data-stu-id="6099f-107">Properties</span></span>  
 `MemoryLimit`  
 <span data-ttu-id="6099f-108">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="6099f-108">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MemoryLimitMin`  
 <span data-ttu-id="6099f-109">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="6099f-109">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `PercentScanPerPrice`  
 <span data-ttu-id="6099f-110">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="6099f-110">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `PerformanceTrace`  
 <span data-ttu-id="6099f-111">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="6099f-111">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `RandomFileAccessMode`  
 <span data-ttu-id="6099f-112">这是一项布尔属性，指示是否在随机文件访问模式下访问数据库文件和缓存文件。</span><span class="sxs-lookup"><span data-stu-id="6099f-112">A Boolean property that indicates whether database files and cached files are accessed in random file access mode.</span></span> <span data-ttu-id="6099f-113">默认情况下禁用此属性。</span><span class="sxs-lookup"><span data-stu-id="6099f-113">This property is off by default.</span></span> <span data-ttu-id="6099f-114">默认情况下，在打开分区数据文件以便进行读访问时，Analysis Services 不设置随机文件访问标志。</span><span class="sxs-lookup"><span data-stu-id="6099f-114">By default, Analysis Services does not set the random file access flag when opening partition data files for read access.</span></span>  
  
 <span data-ttu-id="6099f-115">在高端系统上，特别是在具有大型内存资源和多个 NUMA 节点的系统上，使用随机文件访问可能会给您带来好处。</span><span class="sxs-lookup"><span data-stu-id="6099f-115">On high-end systems, particularly those with large memory resources and multiple NUMA nodes, it can be advantageous to use random file access.</span></span> <span data-ttu-id="6099f-116">在随机访问模式中，Windows 会绕过将数据从磁盘读入系统文件缓存的页映射操作，因此会降低对缓存的争用。</span><span class="sxs-lookup"><span data-stu-id="6099f-116">In random access mode, Windows bypasses page mapping operations that read data from disk into the system file cache, thereby lowering contention on the cache.</span></span>  
  
 <span data-ttu-id="6099f-117">您将需要执行比较测试，以便确定查询性能是否由于更改此属性而得到改善。</span><span class="sxs-lookup"><span data-stu-id="6099f-117">You will need to run comparison tests to determine whether query performance is improved as the result of changing this property.</span></span> <span data-ttu-id="6099f-118">有关执行比较测试的最佳做法，包括清除缓存和避免常见错误，请参阅 [SQL Server 2008 R2 Analysis Services 操作指南](https://go.microsoft.com/fwlink/?LinkID=225539)。</span><span class="sxs-lookup"><span data-stu-id="6099f-118">For best practices on running comparison tests, including clearing the cache and avoiding common mistakes, see the [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span> <span data-ttu-id="6099f-119">有关使用此属性的折衷的其他信息，请参阅 [https://support.microsoft.com/kb/2549369](https://support.microsoft.com/kb/2549369) 。</span><span class="sxs-lookup"><span data-stu-id="6099f-119">For additional information on the tradeoffs of using this property, see [https://support.microsoft.com/kb/2549369](https://support.microsoft.com/kb/2549369).</span></span>  
  
 <span data-ttu-id="6099f-120">若要在 Management Studio 中查看或修改此属性，请在服务器属性页中启用高级属性列表。</span><span class="sxs-lookup"><span data-stu-id="6099f-120">To view or modify this property in Management Studio, enable the advanced properties list in the server properties page.</span></span> <span data-ttu-id="6099f-121">您也可以在 msmdsrv.ini 文件中更改该属性。</span><span class="sxs-lookup"><span data-stu-id="6099f-121">You can also change the property in the msmdsrv.ini file.</span></span> <span data-ttu-id="6099f-122">建议在设置该属性后重新启动服务器；否则，将会继续在之前的模式下访问已打开的文件。</span><span class="sxs-lookup"><span data-stu-id="6099f-122">Restarting the server is recommended after setting this property; otherwise files that are already open will continue to be accessed in the previous mode.</span></span>  
  
 `UnbufferedThreshold`  
 <span data-ttu-id="6099f-123">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="6099f-123">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="memory-model-category"></a><span data-ttu-id="6099f-124">内存模型类别</span><span class="sxs-lookup"><span data-stu-id="6099f-124">Memory Model Category</span></span>  
 `MemoryModel\Tax`  
 <span data-ttu-id="6099f-125">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="6099f-125">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MemoryModel\Income`  
 <span data-ttu-id="6099f-126">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="6099f-126">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MemoryModel\MaximumBalance`  
 <span data-ttu-id="6099f-127">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="6099f-127">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MemoryModel\MinimumBalance`  
 <span data-ttu-id="6099f-128">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="6099f-128">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MemoryModel\InitialBonus`  
 <span data-ttu-id="6099f-129">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="6099f-129">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6099f-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6099f-130">See Also</span></span>  
 <span data-ttu-id="6099f-131">[在 Analysis Services 中配置服务器属性](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="6099f-131">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="6099f-132">确定 Analysis Services 实例的服务器模式</span><span class="sxs-lookup"><span data-stu-id="6099f-132">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
