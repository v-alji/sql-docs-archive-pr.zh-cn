---
title: 清除 "Analysis Services 缓存 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6bf66fdd-6a03-4cea-b7e2-eb676ff276ff
author: minewiskan
ms.author: owend
ms.openlocfilehash: e4890dd322406dcf48bc6b8eca89f292cfe132a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688364"
---
# <a name="clear-the-analysis-services-caches"></a><span data-ttu-id="cf1a3-102">清除 Analysis Services 缓存</span><span class="sxs-lookup"><span data-stu-id="cf1a3-102">Clear the Analysis Services Caches</span></span>
  <span data-ttu-id="cf1a3-103">Analysis Services 通过缓存数据来提高查询性能。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-103">Analysis Services caches data to boost query performance.</span></span> <span data-ttu-id="cf1a3-104">本主题提供关于使用 XMLA ClearCache 命令来清除为响应 MDX 查询而创建的缓存的建议。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-104">This topic provides recommendations for using the XMLA ClearCache command to clear caches that were created in response to an MDX query.</span></span> <span data-ttu-id="cf1a3-105">根据您使用的表格模型还是多维模型，运行 ClearCache 的影响有所不同。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-105">The effects of running ClearCache vary depending on whether you are using a tabular or multidimensional model.</span></span>  
  
 <span data-ttu-id="cf1a3-106">**何时清除多维模型的缓存**</span><span class="sxs-lookup"><span data-stu-id="cf1a3-106">**When to clear the cache for multidimensional models**</span></span>  
  
 <span data-ttu-id="cf1a3-107">对于多维数据库，在对计算求值时 Analysis Services 会在公式引擎中生成缓存，并在存储引擎中为维度查询和度量值组查询的结果生成缓存。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-107">For multidimensional databases, Analysis Services builds caches in the formula engine when evaluating a calculation, and in the storage engine for the results of dimension queries and measure group queries.</span></span> <span data-ttu-id="cf1a3-108">当公式引擎需要单元坐标或子多维数据集的度量值数据时，就会发生度量值组查询。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-108">Measure group queries occur when the formula engine needs measure data for a cell coordinate or subcube.</span></span> <span data-ttu-id="cf1a3-109">当查询非自然层次结构以及应用 autoexists 时，就会发生维度查询。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-109">Dimension queries occur when querying unnatural hierarchies and when applying autoexists.</span></span>  
  
 <span data-ttu-id="cf1a3-110">在执行性能测试时，建议清除缓存。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-110">Clearing the cache is recommended when conducting performance testing.</span></span> <span data-ttu-id="cf1a3-111">通过在运行的各次测试之间清除缓存，您可以确保缓存不会影响用来测量查询设计更改的影响的任何测试结果。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-111">By clearing the cache between test runs, you ensure that caching does not skew any test results that measure the impact of a query design change.</span></span>  
  
 <span data-ttu-id="cf1a3-112">**何时清除表格模型的缓存**</span><span class="sxs-lookup"><span data-stu-id="cf1a3-112">**When to clear the cache for tabular models**</span></span>  
  
 <span data-ttu-id="cf1a3-113">表格模型通常存储在内存中，执行查询时会在内存中执行聚合和其他计算。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-113">Tabular models are generally stored in memory, where aggregations and other calculations are performed at the time a query is executed.</span></span> <span data-ttu-id="cf1a3-114">因此，ClearCache 命令对表格模型影响有限。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-114">As such, the ClearCache command has a limited effect on tabular models.</span></span> <span data-ttu-id="cf1a3-115">对于表格模型，如果对数据运行 MDX 查询，则可以将这些数据添加到 Analysis Services 缓存中。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-115">For a tabular model, data may be added to the Analysis Services caches if MDX queries are run against it.</span></span> <span data-ttu-id="cf1a3-116">特别是，MDX 和 autoexists 操作引用的 DAX 度量值可分别将结果缓存在公式缓存和维度缓存中。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-116">In particular, DAX measures referenced by MDX and autoexists operations can cache results in the formula cache and dimension cache respectively.</span></span> <span data-ttu-id="cf1a3-117">但是请注意，非自然层次结构和度量值组查询不在存储引擎中缓存结果。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-117">Note however, that unnatural hierarchies and measure group queries do not cache results in the storage engine.</span></span> <span data-ttu-id="cf1a3-118">此外，必须认识到 DAX 查询不在公式和存储引擎中缓存结果。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-118">Additionally, it is important to recognize that DAX queries do not cache results in the formula and storage engine.</span></span> <span data-ttu-id="cf1a3-119">如果将缓存引申为是 MDX 查询的结果，对表格模型运行 ClearCache 将使系统中的所有缓存数据失效。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-119">To the extent that caches exist as a result of MDX queries, running ClearCache against a tabular model will invalidate any cached data from the system.</span></span>  
  
 <span data-ttu-id="cf1a3-120">运行 ClearCache 也将清除 xVelocity 内存中分析引擎 (VertiPaq) 中的内存中缓存。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-120">Running ClearCache will also clear in-memory caches in the xVelocity in-memory analytics engine (VertiPaq).</span></span> <span data-ttu-id="cf1a3-121">xVelocity 引擎保持着较小的一组缓存结果。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-121">The xVelocity engine maintains a small set of cached results.</span></span> <span data-ttu-id="cf1a3-122">运行 ClearCache 将使 xVelocity 引擎中的这些缓存失效。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-122">Running ClearCache will invalidate these caches in the xVelocity engine.</span></span>  
  
 <span data-ttu-id="cf1a3-123">最后，运行 ClearCache 还将删除为 `DirectQuery` 模式重新配置表格模型时残留在内存中的数据。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-123">Finally, running ClearCache will also remove residual data that is left in memory when a tabular model is reconfigured for `DirectQuery` mode.</span></span> <span data-ttu-id="cf1a3-124">这在模型包含需要严格控制的敏感数据时尤为重要。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-124">This is particularly important if the model contains sensitive data that is subject to tight controls.</span></span> <span data-ttu-id="cf1a3-125">在这种情况下，运行 ClearCache 是一项预防措施，可确保敏感数据不会存放在不当位置。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-125">In this case, running ClearCache is a precautionary action that you can take to ensure that sensitive data exists only where you expect it to be.</span></span> <span data-ttu-id="cf1a3-126">如果正在使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 部署模型并更改查询模式，则必须手动清除缓存。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-126">Clearing the cache manually is necessary if you are using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to deploy the model and change the query mode.</span></span> <span data-ttu-id="cf1a3-127">相反，若使用 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 对模型和分区指定 `DirectQuery`，则可以在将模型切换为使用该查询模式时自动清除缓存。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-127">In contrast, using [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] to specify `DirectQuery` on the model and partitions will automatically clear the cache when you switch the model to use that query mode.</span></span>  
  
 <span data-ttu-id="cf1a3-128">与清除性能测试期间的多维模型缓存的建议相比，清除表格模型缓存并没有更多的建议。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-128">Compared with recommendations for clearing multidimensional model caches during performance testing, there is no broad recommendation for clearing tabular model caches.</span></span> <span data-ttu-id="cf1a3-129">如果并未管理包含敏感数据的表格模型的部署，则不需要执行特定的管理任务来调用清除缓存操作。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-129">If you are not managing the deployment of a tabular model that contains sensitive data, there is no specific administrative task that calls for clearing the cache.</span></span>  
  
## <a name="clear-the-cache-for-analysis-services-models"></a><span data-ttu-id="cf1a3-130">清除 Analysis Services 模型的缓存</span><span class="sxs-lookup"><span data-stu-id="cf1a3-130">Clear the cache for Analysis Services models</span></span>  
 <span data-ttu-id="cf1a3-131">若要清除缓存，请使用 XMLA 和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-131">To clear the cache, use XMLA and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="cf1a3-132">您可以在数据库、多维数据集、维度/表或度量值组级别清除缓存。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-132">You can clear the cache at the database, cube, dimension or table, or measure group level.</span></span> <span data-ttu-id="cf1a3-133">以下用于在数据库级别清除缓存的步骤同时适用于多维模型和表格模型。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-133">The following steps for clearing the cache at the database level apply to both multidimensional models and tabular models.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cf1a3-134">严格的性能测试可能要求更全面的方法来清除缓存。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-134">Rigorous performance testing might require a more comprehensive approach to clearing the cache.</span></span> <span data-ttu-id="cf1a3-135">有关如何刷新 Analysis Services 和文件系统缓存的说明，请参阅 [SQL Server 2008 R2 Analysis Services 操作指南](https://go.microsoft.com/fwlink/?linkID=https://go.microsoft.com/fwlink/?LinkID=225539)中关于清除缓存的一节。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-135">For instructions on how to flush Analysis Services and file system caches, see the section on clearing caches in the [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?linkID=https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
 <span data-ttu-id="cf1a3-136">对于多维和表格模型，清除某些缓存可以遵循一个两步过程，首先是在执行 ClearCache 时使缓存失效，然后在收到下一个查询时清空该缓存。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-136">For both multidimensional and tabular models, clearing some of these caches can be a two-step process that consists of invalidating the cache when ClearCache executes, followed by emptying the cache when the next query is received.</span></span> <span data-ttu-id="cf1a3-137">只有在真正清空缓存后，才会明显减少内存占用。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-137">A reduction in memory consumption will be evident only after the cache is actually emptied.</span></span>  
  
 <span data-ttu-id="cf1a3-138">清除缓存要求您向 XMLA 查询中的 `ClearCache` 语句提供对象标识符。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-138">Clearing the cache requires that you provide an object identifier to the `ClearCache` statement in an XMLA query.</span></span> <span data-ttu-id="cf1a3-139">本主题中的第一步解释如何获取对象标识符。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-139">The first step in this topic explains how to get an object identifier.</span></span>  
  
#### <a name="step-1-get-the-object-identifier"></a><span data-ttu-id="cf1a3-140">第 1 步：获取对象标识符</span><span class="sxs-lookup"><span data-stu-id="cf1a3-140">Step 1: Get the object identifier</span></span>  
  
1.  <span data-ttu-id="cf1a3-141">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中，右键单击某个对象，选择“属性”，然后复制“属性”窗格中 ID 属性的值\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-141">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], right-click an object, select **Properties**, and copy the value from the ID property in the **Properties** pane.</span></span> <span data-ttu-id="cf1a3-142">这种方法适用于数据库、多维数据集、维度或表。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-142">This approach works for the database, cube, dimension, or table.</span></span>  
  
2.  <span data-ttu-id="cf1a3-143">若要获取度量值组 ID，请右键单击该度量值组并选择“编写度量值组脚本为”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-143">To get the measure group ID, right-click the measure group and select **Script Measure Group As**.</span></span> <span data-ttu-id="cf1a3-144">选择 **“创建”** 或 **“更改”**，并将查询发送到一个窗口。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-144">Choose either **Create** or **Alter**, and send the query to a window.</span></span> <span data-ttu-id="cf1a3-145">度量值组的 ID 将在对象定义中可见。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-145">The ID of the measure group will be visible in the object definition.</span></span> <span data-ttu-id="cf1a3-146">复制对象定义的 ID。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-146">Copy the ID of the object definition.</span></span>  
  
#### <a name="step-2-run-the-query"></a><span data-ttu-id="cf1a3-147">第 2 步：运行查询</span><span class="sxs-lookup"><span data-stu-id="cf1a3-147">Step 2: Run the query</span></span>  
  
1.  <span data-ttu-id="cf1a3-148">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中，右键单击某个数据库，指向“新建查询”，然后选择 XMLA\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-148">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], right-click a database, point to **New Query**, and select **XMLA**.</span></span>  
  
2.  <span data-ttu-id="cf1a3-149">将以下代码示例复制到 XMLA 查询窗口中。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-149">Copy the following code example into the XMLA query window.</span></span> <span data-ttu-id="cf1a3-150">将 `DatabaseID` 更改为当前连接的数据库的 ID。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-150">Change `DatabaseID` to the ID of the database on the current connection.</span></span>  
  
    ```  
    <ClearCache xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
      <Object>  
        <DatabaseID> Adventure Works DW Multidimensional</DatabaseID>  
      </Object>  
    </ClearCache>  
  
    ```  
  
     <span data-ttu-id="cf1a3-151">或者，您可以指定子对象（如度量值组）的路径，以便仅清除该对象的缓存。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-151">Alternatively, you can specify a path of a child object, such as a measure group, to clear the cache for just that object.</span></span>  
  
    ```  
    <ClearCache xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
      <Object>  
        <DatabaseID>Adventure Works DW Multidimensional</DatabaseID>  
            <CubeID>Adventure Works</CubeID>  
            <MeasureGroupID>Fact Currency Rate</MeasureGroupID>  
      </Object>  
    </ClearCache>  
    ```  
  
3.  <span data-ttu-id="cf1a3-152">按 F5 执行该查询。</span><span class="sxs-lookup"><span data-stu-id="cf1a3-152">Press F5 to execute the query.</span></span> <span data-ttu-id="cf1a3-153">应该会看到以下结果：</span><span class="sxs-lookup"><span data-stu-id="cf1a3-153">You should see the following result:</span></span>  
  
    ```  
    <return xmlns="urn:schemas-microsoft-com:xml-analysis">  
      <root xmlns="urn:schemas-microsoft-com:xml-analysis:empty" />  
    </return>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cf1a3-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cf1a3-154">See Also</span></span>  
 <span data-ttu-id="cf1a3-155">[在 Analysis Services 中编写管理任务脚本](../script-administrative-tasks-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="cf1a3-155">[Script Administrative Tasks in Analysis Services](../script-administrative-tasks-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="cf1a3-156">监视 Analysis Services 实例</span><span class="sxs-lookup"><span data-stu-id="cf1a3-156">Monitor an Analysis Services Instance</span></span>](monitor-an-analysis-services-instance.md)  
  
  
