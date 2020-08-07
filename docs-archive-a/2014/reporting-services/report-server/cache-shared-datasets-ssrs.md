---
title: 缓存共享数据集 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4acb1bbe-1c04-4979-b893-dc1b1c5039b6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5b08149b075ae3fd267baf2dad0ca342457958c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588312"
---
# <a name="cache-shared-datasets-ssrs"></a><span data-ttu-id="fb532-102">缓存共享数据集 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="fb532-102">Cache Shared Datasets (SSRS)</span></span>
  <span data-ttu-id="fb532-103">可以将用于共享数据集的查询结果复制到缓存，以便为多个报表提供一致的数据并且缩短数据集查询的响应时间。</span><span class="sxs-lookup"><span data-stu-id="fb532-103">Query results for a shared dataset can be copied to a cache to provide consistent data for multiple reports and to improve response time for the dataset query.</span></span> <span data-ttu-id="fb532-104">与报表类似，您可以在首次使用时或通过指定一个计划，将共享数据集配置为存入缓存。</span><span class="sxs-lookup"><span data-stu-id="fb532-104">Like reports, you can configure a shared dataset to be cached on first use or by specifying a schedule.</span></span>  
  
 <span data-ttu-id="fb532-105">一个共享数据集可以包含在多个报表中或作为组件定义的一部分。</span><span class="sxs-lookup"><span data-stu-id="fb532-105">A shared dataset can be included in multiple reports or as part of component definitions.</span></span> <span data-ttu-id="fb532-106">通过缓存该共享数据集，可为使用它的所有报表提供一组一致的数据，还可以减少数据集查询对外部数据源的运行次数。</span><span class="sxs-lookup"><span data-stu-id="fb532-106">By caching the shared dataset, you provide a consistent set of data for all reports that use it, and also reduce the number of times that the dataset query runs against the external data source.</span></span>  
  
 <span data-ttu-id="fb532-107">下面的列表提供了何时缓存共享数据集的示例：</span><span class="sxs-lookup"><span data-stu-id="fb532-107">The following list provides examples of when to cache a shared dataset:</span></span>  
  
-   <span data-ttu-id="fb532-108">查询需要很长的时间运行。</span><span class="sxs-lookup"><span data-stu-id="fb532-108">The query takes a substantial amount of time to run.</span></span>  
  
-   <span data-ttu-id="fb532-109">查询采用参数，但在大多数时间，参数组合的数目较小。</span><span class="sxs-lookup"><span data-stu-id="fb532-109">The query takes parameters, but most of the time, the number of parameter combinations is small.</span></span> <span data-ttu-id="fb532-110">每个组合都产生缓存的查询结果。</span><span class="sxs-lookup"><span data-stu-id="fb532-110">Each combination creates cached query results.</span></span>  
  
-   <span data-ttu-id="fb532-111">查询在可预测的时间（日期、星期或月份）运行。</span><span class="sxs-lookup"><span data-stu-id="fb532-111">The query runs at predictable times of the day, week, or month.</span></span>  
  
-   <span data-ttu-id="fb532-112">查询作为报表中通过电子邮件传递的共享数据集引用的结果运行，其中，在很短的时间段中可能会有许多人单击该链接。</span><span class="sxs-lookup"><span data-stu-id="fb532-112">The query runs as the result of a shared dataset reference in a report that is delivered via e-mail, where a large number of people are likely to click the link in a short span of time.</span></span>  
  
-   <span data-ttu-id="fb532-113">下面的列表提供了何时不缓存共享数据集的示例：</span><span class="sxs-lookup"><span data-stu-id="fb532-113">The following list provides examples of when not to cache a shared dataset:</span></span>  
  
-   <span data-ttu-id="fb532-114">查询结果必须总是包含最新的数据。</span><span class="sxs-lookup"><span data-stu-id="fb532-114">The query results must always include the most recent data.</span></span>  
  
-   <span data-ttu-id="fb532-115">查询快速运行。</span><span class="sxs-lookup"><span data-stu-id="fb532-115">The query runs quickly.</span></span>  
  
-   <span data-ttu-id="fb532-116">查询很少运行。</span><span class="sxs-lookup"><span data-stu-id="fb532-116">The query runs infrequently.</span></span>  
  
-   <span data-ttu-id="fb532-117">查询采用参数，参数组合的数目较大，并且没有组合的情况比其他组合更有可能发生。</span><span class="sxs-lookup"><span data-stu-id="fb532-117">The query takes parameters, the number of parameter combinations is large, and no combination is more likely than another.</span></span>  
  
-   <span data-ttu-id="fb532-118">共享数据集所基于的数据源具有提示或 Windows 集成凭据。</span><span class="sxs-lookup"><span data-stu-id="fb532-118">The data source that the shared dataset is based on has Prompt or Windows Integrated credentials.</span></span>  
  
-   <span data-ttu-id="fb532-119">共享数据集筛选器或查询中包含的表达式具有对“用户”全局集合的引用。</span><span class="sxs-lookup"><span data-stu-id="fb532-119">The shared dataset filter or the query contains an expression with a reference to the global collection User.</span></span>  
  
 <span data-ttu-id="fb532-120">如果用户选择的报表参数值不同于为缓存的结果集指定的默认值，则数据集查询将主动运行，并且缓存的结果不用于该查询。</span><span class="sxs-lookup"><span data-stu-id="fb532-120">If a user chooses report parameter values that differ from the default values that are specified for the cached result set, the dataset query runs actively and the cached results are not used for that query.</span></span>  
  
## <a name="caching-shared-datasets"></a><span data-ttu-id="fb532-121">缓存共享数据集</span><span class="sxs-lookup"><span data-stu-id="fb532-121">Caching Shared Datasets</span></span>  
 <span data-ttu-id="fb532-122">若要为某一共享数据集启用缓存，您必须对该共享数据集选择缓存选项。</span><span class="sxs-lookup"><span data-stu-id="fb532-122">To enable caching for a shared dataset, you must select the cache option on the shared dataset.</span></span> <span data-ttu-id="fb532-123">启用缓存后，共享数据集的查询结果将在首次使用时复制到缓存中。</span><span class="sxs-lookup"><span data-stu-id="fb532-123">After caching is enabled, the query results for a shared dataset are copied to the cache on first use.</span></span> <span data-ttu-id="fb532-124">如果该共享数据集具有参数，则参数的每个组合将在缓存中创建一个新条目。</span><span class="sxs-lookup"><span data-stu-id="fb532-124">If the shared dataset has parameters, each combination of parameters creates a new entry in the cache.</span></span>  
  
 <span data-ttu-id="fb532-125">在特定参数组合的查询结果处于缓存中时，为进行处理而启动且包括对使用这些参数值的共享数据集的引用的每个报表都将使用缓存的数据。</span><span class="sxs-lookup"><span data-stu-id="fb532-125">While the query results for a specific parameter combination are in the cache, each report that is launched for processing and that includes a reference to the shared dataset with those parameter values will use the cached data.</span></span>  
  
 <span data-ttu-id="fb532-126">你可以指定数据在缓存中保留多长时间后过期。</span><span class="sxs-lookup"><span data-stu-id="fb532-126">You can specify how long to keep data in the cache before it expires.</span></span> <span data-ttu-id="fb532-127">有关详细信息，请参阅[共享数据集的“缓存”属性页（报表管理器）](../caching-page-shared-datasets-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="fb532-127">For more information, see [Caching Page, Shared Datasets &#40;Report Manager&#41;](../caching-page-shared-datasets-report-manager.md).</span></span>  
  
## <a name="preloading-the-cache"></a><span data-ttu-id="fb532-128">预加载缓存</span><span class="sxs-lookup"><span data-stu-id="fb532-128">Preloading the Cache</span></span>  
 <span data-ttu-id="fb532-129">您可以通过创建缓存刷新计划预加载缓存。</span><span class="sxs-lookup"><span data-stu-id="fb532-129">You can preload the cache by creating a cache refresh plan.</span></span> <span data-ttu-id="fb532-130">使用刷新计划，您可以通过特定于项的计划或共享计划来指定刷新缓存的频率。</span><span class="sxs-lookup"><span data-stu-id="fb532-130">With a refresh plan, you can specify how often to refresh the cache by using an item-specific schedule or a shared schedule.</span></span> <span data-ttu-id="fb532-131">为了避免同一项有多个缓存条目，您指定的计划应该允许有足够的时间来对外部数据源执行查询处理。</span><span class="sxs-lookup"><span data-stu-id="fb532-131">To avoid multiple cache entries for the same item, the schedule that you specify should allow enough time for query processing on the external data source.</span></span> <span data-ttu-id="fb532-132">例如，如果查询需要 20 分钟来运行，则刷新计划应大于 20 分钟。</span><span class="sxs-lookup"><span data-stu-id="fb532-132">For example, if the query takes 20 minutes to run, the refresh schedule should be greater than 20 minutes.</span></span> <span data-ttu-id="fb532-133">有关更多信息，请参见 [Schedules](../subscriptions/schedules.md)。</span><span class="sxs-lookup"><span data-stu-id="fb532-133">For more information, see [Schedules](../subscriptions/schedules.md).</span></span>  
  
 <span data-ttu-id="fb532-134">若要为共享数据集创建缓存刷新计划，以下条件适用。</span><span class="sxs-lookup"><span data-stu-id="fb532-134">To create a cache refresh plan for a shared dataset, the following conditions apply.</span></span>  
  
-   <span data-ttu-id="fb532-135">该共享数据集必须支持缓存。</span><span class="sxs-lookup"><span data-stu-id="fb532-135">The shared dataset must be enabled for caching.</span></span>  
  
-   <span data-ttu-id="fb532-136">共享数据集所依赖的共享数据源不能使用提示或 Windows 集成凭据。</span><span class="sxs-lookup"><span data-stu-id="fb532-136">The shared data source that the shared dataset depends on cannot use Prompt or Windows Integrated credentials.</span></span>  
  
-   <span data-ttu-id="fb532-137">如果共享数据集具有参数，则必须指定为没有标记为只读的每个参数都指定静态默认值。</span><span class="sxs-lookup"><span data-stu-id="fb532-137">If the shared dataset has parameters, you must specify static default values for each parameter that is not marked read-only.</span></span> <span data-ttu-id="fb532-138">只读参数将始终使用默认值。</span><span class="sxs-lookup"><span data-stu-id="fb532-138">Read-only parameters will always use the default value.</span></span> <span data-ttu-id="fb532-139">若要为参数的多个组合缓存共享数据集，则必须为值的每个组合都创建单独的缓存刷新计划。</span><span class="sxs-lookup"><span data-stu-id="fb532-139">To cache a shared dataset for multiple combinations of parameters, you must create a separate cache refresh plan for each combination of values.</span></span> <span data-ttu-id="fb532-140">参数不能包含对其他数据集的引用。</span><span class="sxs-lookup"><span data-stu-id="fb532-140">Parameters cannot contain references to other datasets.</span></span>  
  
-   <span data-ttu-id="fb532-141">每个缓存刷新计划都仅与一个共享数据集或报表相关联。</span><span class="sxs-lookup"><span data-stu-id="fb532-141">Each cache refresh plan is associated with only one shared dataset or report.</span></span>  
  
-   <span data-ttu-id="fb532-142">对于共享数据集，您必须具有 ReadPolicy 和 UpdatePolicy 权限。</span><span class="sxs-lookup"><span data-stu-id="fb532-142">You must have ReadPolicy and UpdatePolicy permissions on the shared dataset.</span></span>  
  
 <span data-ttu-id="fb532-143">缓存刷新计划同时应用于共享数据集和报表。</span><span class="sxs-lookup"><span data-stu-id="fb532-143">Cache refresh plans apply to both shared datasets and reports.</span></span> <span data-ttu-id="fb532-144">有关详细信息，请参阅[缓存刷新选项（报表管理器）](../cache-refresh-options-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="fb532-144">For more information, see [Cache Refresh Options &#40;Report Manager&#41;](../cache-refresh-options-report-manager.md).</span></span>  
  
## <a name="conditions-that-cause-cache-expiration"></a><span data-ttu-id="fb532-145">导致缓存过期的条件</span><span class="sxs-lookup"><span data-stu-id="fb532-145">Conditions that Cause Cache Expiration</span></span>  
 <span data-ttu-id="fb532-146">以下条件可能导致共享数据集缓存失效。</span><span class="sxs-lookup"><span data-stu-id="fb532-146">The following conditions can cause a shared dataset cache to become not valid.</span></span>  
  
-   <span data-ttu-id="fb532-147">计划条件到期。</span><span class="sxs-lookup"><span data-stu-id="fb532-147">A schedule condition expires.</span></span> <span data-ttu-id="fb532-148">缓存超时或者已到到期时间。</span><span class="sxs-lookup"><span data-stu-id="fb532-148">The cache times out or the expiration time occurs.</span></span>  
  
-   <span data-ttu-id="fb532-149">共享计划被删除。</span><span class="sxs-lookup"><span data-stu-id="fb532-149">A shared schedule is deleted.</span></span>  
  
-   <span data-ttu-id="fb532-150">对共享计划进行了更改。</span><span class="sxs-lookup"><span data-stu-id="fb532-150">Changes to a shared schedule.</span></span> <span data-ttu-id="fb532-151">共享计划可被暂停，这也会影响缓存到期时间。</span><span class="sxs-lookup"><span data-stu-id="fb532-151">Shared schedules can be paused, which also affects when a cache expires.</span></span>  
  
-   <span data-ttu-id="fb532-152">共享数据集的查询定义发生了更改。</span><span class="sxs-lookup"><span data-stu-id="fb532-152">The query definition for the shared dataset changes.</span></span>  
  
-   <span data-ttu-id="fb532-153">共享数据集所依赖的共享数据源的凭据发生了更改。</span><span class="sxs-lookup"><span data-stu-id="fb532-153">The credentials for the shared data source that the shared dataset depends on change.</span></span>  
  
-   <span data-ttu-id="fb532-154">共享数据集的缓存选项发生了更改。</span><span class="sxs-lookup"><span data-stu-id="fb532-154">The cache options for the shared dataset change.</span></span>  
  
-   <span data-ttu-id="fb532-155">共享数据集的只读参数的默认值发生了更改。</span><span class="sxs-lookup"><span data-stu-id="fb532-155">The default values for read-only parameters for the shared dataset change.</span></span>  
  
-   <span data-ttu-id="fb532-156">作为共享数据集定义一部分的筛选器发生了更改。</span><span class="sxs-lookup"><span data-stu-id="fb532-156">The filters that are part of the shared dataset definition change.</span></span>  
  
-   <span data-ttu-id="fb532-157">共享数据集已从报表服务器中删除。</span><span class="sxs-lookup"><span data-stu-id="fb532-157">The shared dataset is deleted from the report server.</span></span> <span data-ttu-id="fb532-158">在删除某一共享数据集时，关联的缓存副本和缓存刷新计划也将删除。</span><span class="sxs-lookup"><span data-stu-id="fb532-158">When a shared dataset is deleted, associated cached copies and cache refresh plans are also deleted.</span></span>  
  
 <span data-ttu-id="fb532-159">对共享数据集的缓存刷新计划的更新不会影响已在处理的报表。</span><span class="sxs-lookup"><span data-stu-id="fb532-159">Updates to cache refresh plans for shared datasets do not affect reports that are already being processed.</span></span> <span data-ttu-id="fb532-160">更新缓存刷新计划仅影响引用共享数据集的报表的将来启动。</span><span class="sxs-lookup"><span data-stu-id="fb532-160">Updating a cache refresh plan affects only future launches of reports that reference the shared dataset.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb532-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fb532-161">See Also</span></span>  
 [<span data-ttu-id="fb532-162">管理共享数据集</span><span class="sxs-lookup"><span data-stu-id="fb532-162">Manage Shared Datasets</span></span>](../report-data/manage-shared-datasets.md)  
  
  
