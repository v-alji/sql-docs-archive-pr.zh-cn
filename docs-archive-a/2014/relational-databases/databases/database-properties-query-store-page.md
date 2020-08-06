---
title: 数据库属性（“查询存储”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql13.swb.databaseproperties.querystore.f1
ms.assetid: da47d75e-291a-4305-acef-4b0aaf5215da
author: stevestein
ms.author: sstein
ms.openlocfilehash: bab0d9b697e9ad9ec4b27f320d26b9b9edb5944e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690636"
---
# <a name="database-properties-query-store-page"></a><span data-ttu-id="77052-102">数据库属性（查询存储页）</span><span class="sxs-lookup"><span data-stu-id="77052-102">Database Properties (Query Store Page)</span></span>
  <span data-ttu-id="77052-103">从主体数据库访问此页面，并用它来配置和修改数据库查询存储的属性。</span><span class="sxs-lookup"><span data-stu-id="77052-103">Access this page from the principal database, and use it to configure and to modify the properties of the database query store.</span></span> <span data-ttu-id="77052-104">这些选项也可使用 [ALTER DATABASE SET 选项](/sql/t-sql/statements/alter-database-transact-sql-set-options)进行更改。</span><span class="sxs-lookup"><span data-stu-id="77052-104">These options can also be configure by using the [ALTER DATABASE SET options](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span> <span data-ttu-id="77052-105">有关查询存储的信息，请参阅 [Monitoring Performance By Using the Query Store](../performance/monitoring-performance-by-using-the-query-store.md)。</span><span class="sxs-lookup"><span data-stu-id="77052-105">For information about the query store, see [Monitoring Performance By Using the Query Store](../performance/monitoring-performance-by-using-the-query-store.md).</span></span>  
  
||  
|-|  
|<span data-ttu-id="77052-106">**适用于**： [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="77052-106">**Applies to**: [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].</span></span>|  
  
## <a name="options"></a><span data-ttu-id="77052-107">选项</span><span class="sxs-lookup"><span data-stu-id="77052-107">Options</span></span>  
 <span data-ttu-id="77052-108">启用</span><span class="sxs-lookup"><span data-stu-id="77052-108">Enable</span></span>  
 <span data-ttu-id="77052-109">启用和禁用查询存储。</span><span class="sxs-lookup"><span data-stu-id="77052-109">Enables and disables the query store.</span></span>  
  
 <span data-ttu-id="77052-110">操作模式</span><span class="sxs-lookup"><span data-stu-id="77052-110">Operation Mode</span></span>  
 <span data-ttu-id="77052-111">有效值为 READ_ONLY 和 READ_WRITE。</span><span class="sxs-lookup"><span data-stu-id="77052-111">Valid values are READ_ONLY and READ_WRITE.</span></span> <span data-ttu-id="77052-112">在 READ_WRITE 模式下，查询存储将收集并保留查询计划和运行时执行统计信息。</span><span class="sxs-lookup"><span data-stu-id="77052-112">In READ_WRITE mode, the query store collects and persists query plan and runtime execution statistics information.</span></span> <span data-ttu-id="77052-113">在 READ_ONLY 模式下，可以从查询存储读取信息，但不会添加新信息。</span><span class="sxs-lookup"><span data-stu-id="77052-113">In READ_ONLY mode, information can be read from the query store, but new information is not added.</span></span> <span data-ttu-id="77052-114">如果已用尽查询存储的最大分配空间，查询存储的操作模式将更改为 READ_ONLY。</span><span class="sxs-lookup"><span data-stu-id="77052-114">If the maximum allocated space of the query store has been exhausted, the query store will change its operation mode to READ_ONLY.</span></span>  
  
 <span data-ttu-id="77052-115">操作模式（实际）</span><span class="sxs-lookup"><span data-stu-id="77052-115">Operation Mode (Actual)</span></span>  
 <span data-ttu-id="77052-116">获取查询存储的实际操作模式。</span><span class="sxs-lookup"><span data-stu-id="77052-116">Gets the actual operation mode of the query store.</span></span>  
  
 <span data-ttu-id="77052-117">操作模式（按请求）</span><span class="sxs-lookup"><span data-stu-id="77052-117">Operation Mode (Requested)</span></span>  
 <span data-ttu-id="77052-118">获取和设置查询存储的所需操作模式。</span><span class="sxs-lookup"><span data-stu-id="77052-118">Gets and sets the desired operation mode of the query store.</span></span>  
  
 <span data-ttu-id="77052-119">数据刷新间隔（分钟）</span><span class="sxs-lookup"><span data-stu-id="77052-119">Data Flush Interval (Minutes)</span></span>  
 <span data-ttu-id="77052-120">确定写入到查询存储的数据保留到磁盘的频率。</span><span class="sxs-lookup"><span data-stu-id="77052-120">Determines the frequency at which data written to the query store is persisted to disk.</span></span> <span data-ttu-id="77052-121">为了优化性能，由查询存储收集的数据应以异步方式写入到磁盘。</span><span class="sxs-lookup"><span data-stu-id="77052-121">To optimize for performance, data collected by the query store is asynchronously written to the disk.</span></span> <span data-ttu-id="77052-122">所配置的此异步传输发生的频率。</span><span class="sxs-lookup"><span data-stu-id="77052-122">The frequency at which this asynchronous transfer occurs is configured.</span></span>  
  
 <span data-ttu-id="77052-123">统计信息收集间隔</span><span class="sxs-lookup"><span data-stu-id="77052-123">Statistics Collection Interval</span></span>  
 <span data-ttu-id="77052-124">获取和设置统计信息收集间隔值。</span><span class="sxs-lookup"><span data-stu-id="77052-124">Gets and sets the statistics collection interval value.</span></span>  
  
 <span data-ttu-id="77052-125">最大大小 (MB)</span><span class="sxs-lookup"><span data-stu-id="77052-125">Max Size (MB)</span></span>  
 <span data-ttu-id="77052-126">获取和设置分配给查询存储的总空间。</span><span class="sxs-lookup"><span data-stu-id="77052-126">Gets and sets the total space allocated to the query store.</span></span>  
  
 <span data-ttu-id="77052-127">过时查询阙值（天）</span><span class="sxs-lookup"><span data-stu-id="77052-127">Stale Query Threshold (Days)</span></span>  
 <span data-ttu-id="77052-128">获取和设置过时查询阙值。</span><span class="sxs-lookup"><span data-stu-id="77052-128">Gets and sets the stale query threshold.</span></span> <span data-ttu-id="77052-129">配置 STALE_QUERY_THRESHOLD_DAYS 参数，以指定数据在查询存储保留的天数。</span><span class="sxs-lookup"><span data-stu-id="77052-129">Configure the STALE_QUERY_THRESHOLD_DAYS argument to specify the number of days to retain data in the query store.</span></span>  
  
 <span data-ttu-id="77052-130">清除查询数据</span><span class="sxs-lookup"><span data-stu-id="77052-130">Purge Query Data</span></span>  
 <span data-ttu-id="77052-131">删除查询存储的内容。</span><span class="sxs-lookup"><span data-stu-id="77052-131">Removes the contents of the query store.</span></span>  
  
 <span data-ttu-id="77052-132">饼图</span><span class="sxs-lookup"><span data-stu-id="77052-132">Pie Charts</span></span>  
 <span data-ttu-id="77052-133">左侧图表显示了磁盘上的数据库文件总占用量，以及哪部分的文件填充了查询存储数据。</span><span class="sxs-lookup"><span data-stu-id="77052-133">The left chart shows the total database file consumption on the disk, and the portion of the file which is filled with the query store data.</span></span>  
  
 <span data-ttu-id="77052-134">右侧图表显示了目前已占用了哪部分的查询存储配额。</span><span class="sxs-lookup"><span data-stu-id="77052-134">The right chart shows the portion of the query store quota which is currently used up.</span></span> <span data-ttu-id="77052-135">请注意，左侧图表未显示配额。</span><span class="sxs-lookup"><span data-stu-id="77052-135">Note that the quota is not shown in the left chart.</span></span> <span data-ttu-id="77052-136">配额可能超过数据库的当前大小。</span><span class="sxs-lookup"><span data-stu-id="77052-136">The quota may exceed the current size of the database.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77052-137">备注</span><span class="sxs-lookup"><span data-stu-id="77052-137">Remarks</span></span>  
 <span data-ttu-id="77052-138">查询存储功能让 DBA 可以探查查询计划选项和性能。</span><span class="sxs-lookup"><span data-stu-id="77052-138">The query store feature provides DBAs with insight on query plan choice and performance.</span></span> <span data-ttu-id="77052-139">它让你可以快速找到查询计划中的更改所造成的性能差异，从而简化了性能疑难解答。</span><span class="sxs-lookup"><span data-stu-id="77052-139">It simplifies performance troubleshooting by enabling you to quickly find performance differences caused by changes in query plans.</span></span> <span data-ttu-id="77052-140">这一性能会自动捕获查询、计划和运行时统计信息的历史记录，并将其保留以供你查看。</span><span class="sxs-lookup"><span data-stu-id="77052-140">The feature automatically captures a history of queries, plans, and runtime statistics, and retains these for your review.</span></span> <span data-ttu-id="77052-141">它按时间窗口将数据分割开来，使你可以查看数据库使用情况模式并了解服务器上何时发生了查询计划更改。</span><span class="sxs-lookup"><span data-stu-id="77052-141">It separates data by time windows, allowing you to see database usage patterns and understand when query plan changes happened on the server.</span></span> <span data-ttu-id="77052-142">可使用此查询存储数据库属性页面，或者使用 [ALTER DATABASE SET](/sql/t-sql/statements/alter-database-transact-sql-set-options) 选项来配置查询存储。</span><span class="sxs-lookup"><span data-stu-id="77052-142">The query store can be configured by using this query store database property page, or by using the [ALTER DATABASE SET](/sql/t-sql/statements/alter-database-transact-sql-set-options) option.</span></span> <span data-ttu-id="77052-143">查询存储通过使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 对话框来呈现信息。</span><span class="sxs-lookup"><span data-stu-id="77052-143">The query store presents information by using a [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] dialog box.</span></span> <span data-ttu-id="77052-144">有关查询存储的详细信息，请参阅 [Monitoring Performance By Using the Query Store](../performance/monitoring-performance-by-using-the-query-store.md)。</span><span class="sxs-lookup"><span data-stu-id="77052-144">For more information about query store, see [Monitoring Performance By Using the Query Store](../performance/monitoring-performance-by-using-the-query-store.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77052-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="77052-145">See Also</span></span>  
 <span data-ttu-id="77052-146">[查询存储存储过程 (Transact-SQL)](/sql/relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="77052-146">[Query Store Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql) </span></span>  
 [<span data-ttu-id="77052-147">查询存储目录视图 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="77052-147">Query Store Catalog Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/query-store-catalog-views-transact-sql)  
  
  
