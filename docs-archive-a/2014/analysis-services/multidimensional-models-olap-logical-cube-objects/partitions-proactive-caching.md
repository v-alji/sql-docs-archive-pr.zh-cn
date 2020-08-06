---
title: 主动缓存 (分区) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- hybrid OLAP
- partitions [Analysis Services], proactive caching
- relational OLAP
- multidimensional OLAP
- MOLAP
- proactive caching [Analysis Services]
- ROLAP
- cache [Analysis Services]
ms.assetid: 422660b2-4d80-4165-b1c9-3963bcde556b
author: minewiskan
ms.author: owend
ms.openlocfilehash: a903d73394b191dbfe96dea710fb2c6c86165402
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591619"
---
# <a name="proactive-caching-partitions"></a><span data-ttu-id="d188c-102">主动缓存（分区）</span><span class="sxs-lookup"><span data-stu-id="d188c-102">Proactive Caching (Partitions)</span></span>
  <span data-ttu-id="d188c-103">可以利用主动缓存自动创建 MOLAP 缓存以及管理 OLAP 对象。</span><span class="sxs-lookup"><span data-stu-id="d188c-103">Proactive caching provides automatic MOLAP cache creation and management for OLAP objects.</span></span> <span data-ttu-id="d188c-104">多维数据集可利用收自数据库的通知，立即合并对数据库中数据所做的更改。</span><span class="sxs-lookup"><span data-stu-id="d188c-104">The cubes immediately incorporate changes that are made to the data in the database, based upon notifications received from the database.</span></span> <span data-ttu-id="d188c-105">主动缓存的目标是提供传统 MOLAP 所具有的性能，并同时保持使用 ROLAP 进行管理所具有的方便和快捷。</span><span class="sxs-lookup"><span data-stu-id="d188c-105">The goal of proactive caching is to provide the performance of traditional MOLAP, while retaining the immediacy and ease of management offered by ROLAP.</span></span>  
  
 <span data-ttu-id="d188c-106">简单 <xref:Microsoft.AnalysisServices.ProactiveCaching> 对象由计时规范和表通知组成。</span><span class="sxs-lookup"><span data-stu-id="d188c-106">A simple <xref:Microsoft.AnalysisServices.ProactiveCaching> object is composed of: timing specification, and table notification.</span></span> <span data-ttu-id="d188c-107">计时规范定义收到更改通知后更新缓存的时间范围。</span><span class="sxs-lookup"><span data-stu-id="d188c-107">The timing specification defines the timeframe for updating the cache after a change notification has been received.</span></span> <span data-ttu-id="d188c-108">表通知定义数据表和 <xref:Microsoft.AnalysisServices.ProactiveCaching> 对象之间的通知架构。</span><span class="sxs-lookup"><span data-stu-id="d188c-108">The table notification defines the notification schema between the data table and the <xref:Microsoft.AnalysisServices.ProactiveCaching> object.</span></span>  
  
 <span data-ttu-id="d188c-109">多维 OLAP (MOLAP) 存储提供最佳的查询响应，但是其不足之处是存在一些数据滞后时间。</span><span class="sxs-lookup"><span data-stu-id="d188c-109">Multidimensional OLAP (MOLAP) storage provides the best query response, but with a penalty of some data latency.</span></span> <span data-ttu-id="d188c-110">实时关系 OLAP (ROLAP) 存储可使用户迅速浏览数据源中的最新更改，但是不足之处是较多维 OLAP (MOLAP) 存储的性能相差甚远，这是因为没有对数据进行预计算汇总，并且关系存储没有针对 OLAP 样式的查询进行优化。</span><span class="sxs-lookup"><span data-stu-id="d188c-110">Real-time relational OLAP (ROLAP) storage lets users immediately browse the most recent changes in a data source, but at the penalty of significantly poorer performance than multidimensional OLAP (MOLAP) storage because of the absence of precalculated summaries of data and because relational storage is not optimized for OLAP-style queries.</span></span> <span data-ttu-id="d188c-111">如果用户需要在您的应用程序中查看最新数据，而您也希望利用 MOLAP 存储的性能优点，则 SQL Server Analysis Services 提供的主动缓存选项可满足这些应用需求，尤其是与分区组合使用时，更是如此。</span><span class="sxs-lookup"><span data-stu-id="d188c-111">If you have applications in which your users need to see recent data and you also want the performance advantages of MOLAP storage, SQL Server Analysis Services offers the option of proactive caching to address this scenario, particularly in combination with the use of partitions.</span></span> <span data-ttu-id="d188c-112">主动缓存按分区和维度来设置。</span><span class="sxs-lookup"><span data-stu-id="d188c-112">Proactive caching is set on a per partition and per dimension basis.</span></span> <span data-ttu-id="d188c-113">主动缓存选项使得能够在 MOLAP 存储的增强性能和 ROLAP 存储的即时性之间达成平衡，并且还在基础数据更改时提供自动的分区处理或者按照设置计划进行处理。</span><span class="sxs-lookup"><span data-stu-id="d188c-113">Proactive caching options can provide a balance between the enhanced performance of MOLAP storage and the immediacy of ROLAP storage, and provide automatic partition processing when underlying data changes or on a set schedule.</span></span>  
  
## <a name="proactive-caching-configuration-options"></a><span data-ttu-id="d188c-114">主动缓存配置选项</span><span class="sxs-lookup"><span data-stu-id="d188c-114">Proactive Caching Configuration Options</span></span>  
 <span data-ttu-id="d188c-115">SQL Server Analysis Services 提供了多个主动缓存配置选项，您可以利用它们来最大化性能，最小化滞后时间以及安排处理。</span><span class="sxs-lookup"><span data-stu-id="d188c-115">SQL Server Analysis Services provides several proactive caching configuration options that enable you to maximize performance, minimize latency, and schedule processing.</span></span> <span data-ttu-id="d188c-116">主动缓存功能可以简化管理数据过时的进程。</span><span class="sxs-lookup"><span data-stu-id="d188c-116">Proactive caching features simplify the process of managing data obsolescence.</span></span> <span data-ttu-id="d188c-117">主动缓存设置确定多维 OLAP 结构（也称为 MOLAP 缓存）重新生成的频率，是否在重新生成缓存时对过时的 MOLAP 存储或基础 ROLAP 数据源进行查询，以及缓存是按计划重新生成还是根据数据库中的更改重新生成。</span><span class="sxs-lookup"><span data-stu-id="d188c-117">The proactive caching settings determine how frequently the multidimensional OLAP structure, also called the MOLAP cache, is rebuilt, whether the outdated MOLAP storage is queried while the cache is rebuilt or the underlying ROLAP data source, and whether the cache is rebuilt on a schedule or based on changes in the database.</span></span>  
  
### <a name="minimizing-latency"></a><span data-ttu-id="d188c-118">最小化延迟</span><span class="sxs-lookup"><span data-stu-id="d188c-118">Minimizing Latency</span></span>  
 <span data-ttu-id="d188c-119">将主动缓存设置为最小化滞后时间之后，用户会对 ROLAP 存储或 MOLAP 存储执行 OLAP 对象查询，具体取决于数据是否发生了最新更改以及主动缓存的配置方式。</span><span class="sxs-lookup"><span data-stu-id="d188c-119">With proactive caching set to minimize latency, user queries against an OLAP object are made against either ROLAP storage or MOLAP storage, depending whether recent changes have occurred to the data and how proactive caching is configured.</span></span> <span data-ttu-id="d188c-120">查询引擎会将查询导向 MOLAP 存储中的源数据，直至数据源发生更改为止。</span><span class="sxs-lookup"><span data-stu-id="d188c-120">The query engine directs queries against source data in MOLAP storage until changes occur in the data source.</span></span> <span data-ttu-id="d188c-121">若要最小化滞后时间，数据源发生更改后，可以删除已缓存的 MOLAP 对象，并当 MOLAP 对象在缓存中重新生成期间将查询切换到 ROLAP 存储。</span><span class="sxs-lookup"><span data-stu-id="d188c-121">To minimize latency, after changes occur in a data source, cached MOLAP objects can be dropped and querying switched to ROLAP storage while the MOLAP objects are rebuilt in cache.</span></span> <span data-ttu-id="d188c-122">在 MOLAP 对象重新生成和处理完毕之后，查询会自动切换到 MOLAP 存储。</span><span class="sxs-lookup"><span data-stu-id="d188c-122">After the MOLAP objects are rebuilt and processed, queries are automatically switched to the MOLAP storage.</span></span> <span data-ttu-id="d188c-123">对于小分区（例如当前分区）而言，缓存的刷新速度非常快，仅在当天便可进行刷新。</span><span class="sxs-lookup"><span data-stu-id="d188c-123">The cache refresh can occur extremely quickly for a small partition, such as the current partition - which can be as small as the current day.</span></span>  
  
### <a name="maximizing-performance"></a><span data-ttu-id="d188c-124">最大化性能</span><span class="sxs-lookup"><span data-stu-id="d188c-124">Maximizing Performance</span></span>  
 <span data-ttu-id="d188c-125">若要最大化性能同时缩短滞留时间，还可以使用缓存，而无需删除当前 MOLAP 对象。</span><span class="sxs-lookup"><span data-stu-id="d188c-125">To maximize performance while also reducing latency, caching can also be used without dropping the current MOLAP objects.</span></span> <span data-ttu-id="d188c-126">然后，在数据读入新缓存并在其中处理时，继续对 MOLAP 对象进行查询。</span><span class="sxs-lookup"><span data-stu-id="d188c-126">Queries then continue against the MOLAP objects while data is read into and processed in a new cache.</span></span> <span data-ttu-id="d188c-127">该方法可提供更好的性能，但是会导致在生成新缓存时查询返回旧数据。</span><span class="sxs-lookup"><span data-stu-id="d188c-127">This method provides better performance but may result in queries returning old data while the new cache is being built.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d188c-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d188c-128">See Also</span></span>  
 <span data-ttu-id="d188c-129">[维度存储](../multidimensional-models-olap-logical-dimension-objects/dimensions-storage.md) </span><span class="sxs-lookup"><span data-stu-id="d188c-129">[Dimension Storage](../multidimensional-models-olap-logical-dimension-objects/dimensions-storage.md) </span></span>  
 [<span data-ttu-id="d188c-130">设置分区存储（Analysis Services - 多维）</span><span class="sxs-lookup"><span data-stu-id="d188c-130">Set Partition Storage &#40;Analysis Services - Multidimensional&#41;</span></span>](../multidimensional-models/set-partition-storage-analysis-services-multidimensional.md)  
  
  
