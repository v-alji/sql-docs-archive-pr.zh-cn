---
title: 数据挖掘)  (钻取查询 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- AllowDrillThrough property
- drillthrough [Analysis Services]
- drillthrough [DMX]
ms.assetid: 246c784b-1b0c-4f0b-96f7-3af265e67051
author: minewiskan
ms.author: owend
ms.openlocfilehash: 21e8c6f7cb6938e629be9d252c208c61c04d17d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589370"
---
# <a name="drillthrough-queries-data-mining"></a><span data-ttu-id="edc4d-102">钻取查询（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="edc4d-102">Drillthrough Queries (Data Mining)</span></span>
  <span data-ttu-id="edc4d-103">“钻取查询” \*\* 让您通过将查询发送到挖掘模型，检索基础事例或结构数据中的详细信息。</span><span class="sxs-lookup"><span data-stu-id="edc4d-103">A *drillthrough query* lets you retrieve details from the underlying cases or structure data, by sending a query to the mining model.</span></span> <span data-ttu-id="edc4d-104">如果您希望查看用来为模型定型的事例以及用来测试模型的事例，或者如果您希望查看事例数据的详细信息，则钻取会非常有用。</span><span class="sxs-lookup"><span data-stu-id="edc4d-104">Drillthrough is useful if you want to view the cases that were used to train the model, versus the cases that are used to test the model, or if you want to see additional details from the case data.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="edc4d-105">数据挖掘提供了两种不同的钻取选项：</span><span class="sxs-lookup"><span data-stu-id="edc4d-105">Data Mining provides two different options for drillthrough:</span></span>  
  
-   <span data-ttu-id="edc4d-106">钻取到 **模型事例**</span><span class="sxs-lookup"><span data-stu-id="edc4d-106">Drilling through to the **model cases**</span></span>  
  
     <span data-ttu-id="edc4d-107">当您希望从模型中的特定模式（如群集或决策树的分支）进行时，可以使用钻取到模型事例，并查看有关单个事例的详细信息。</span><span class="sxs-lookup"><span data-stu-id="edc4d-107">Drillthrough to model cases is used when you want to go from a specific pattern in the model-such as a cluster or branch of a decision tree-and view details about the individual cases.</span></span>  
  
-   <span data-ttu-id="edc4d-108">钻取到 **结构事例**</span><span class="sxs-lookup"><span data-stu-id="edc4d-108">Drilling through to the **structure cases**</span></span>  
  
     <span data-ttu-id="edc4d-109">如果结构中包含模型中可能不可用的信息，则使用钻取到结构事例。</span><span class="sxs-lookup"><span data-stu-id="edc4d-109">Drillthrough to structure cases is used when the structure contains information that might not be available in the model.</span></span> <span data-ttu-id="edc4d-110">例如，即使结构中包括客户联系信息，也不在聚类分析模型中使用该数据。</span><span class="sxs-lookup"><span data-stu-id="edc4d-110">For example, you would not use customer contact information in a clustering model, even if the data was included in the structure.</span></span> <span data-ttu-id="edc4d-111">但是，在创建聚类分析模型之后，您可能希望检索那些分组到特定分类中的客户的联系信息。</span><span class="sxs-lookup"><span data-stu-id="edc4d-111">However, after you create the model, you might want to retrieve contact information for customers who are grouped into a particular cluster.</span></span>  
  
 <span data-ttu-id="edc4d-112">本节提供有关如何创建这些查询的示例。</span><span class="sxs-lookup"><span data-stu-id="edc4d-112">This section provides examples of how you can create these queries.</span></span>  
  
 [<span data-ttu-id="edc4d-113">在数据挖掘设计器中使用钻取</span><span class="sxs-lookup"><span data-stu-id="edc4d-113">Using Drillthrough in Data Mining Designer</span></span>](#bkmk_Designer)  
  
 [<span data-ttu-id="edc4d-114">使用 DMX 来创建钻取查询</span><span class="sxs-lookup"><span data-stu-id="edc4d-114">Creating Drillthrough Queries using DMX</span></span>](#bkmk_DMX)  
  
 [<span data-ttu-id="edc4d-115">使用钻取功能时的注意事项</span><span class="sxs-lookup"><span data-stu-id="edc4d-115">Considerations When Using Drillthrough</span></span>](#bkmk_Considerations)  
  
-   [<span data-ttu-id="edc4d-116">安全问题</span><span class="sxs-lookup"><span data-stu-id="edc4d-116">Security Issues</span></span>](#bkmk_Security)  
  
-   [<span data-ttu-id="edc4d-117">限制</span><span class="sxs-lookup"><span data-stu-id="edc4d-117">Limitations</span></span>](#bkmk_Limits)  
  
##  <a name="using-drillthrough-in-data-mining-designer"></a><a name="bkmk_Designer"></a><span data-ttu-id="edc4d-118">在数据挖掘设计器中使用钻取</span><span class="sxs-lookup"><span data-stu-id="edc4d-118">Using Drillthrough in Data Mining Designer</span></span>  
 <span data-ttu-id="edc4d-119">如果挖掘模型已经配置为允许进行钻取，而且如果您具有适当的权限，那么，当您浏览模型时，可以在相应的查看器中单击某个节点，并检索有关该特定节点中各个事例的详细信息。</span><span class="sxs-lookup"><span data-stu-id="edc4d-119">If a mining model has been configured to allow drillthrough, and if you have the appropriate permissions, when you browse the model, you can click on a node in the appropriate viewer and retrieve detailed information about the cases in that particular node.</span></span>  
  
 <span data-ttu-id="edc4d-120">[从挖掘模型钻取到事例数据](drill-through-to-case-data-from-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="edc4d-120">[Drill Through to Case Data from a Mining Model](drill-through-to-case-data-from-a-mining-model.md).</span></span>  
  
 <span data-ttu-id="edc4d-121">如果处理挖掘结构时缓存了定型事例，并且您具有必要的权限，则您可以从模型事例和挖掘结构返回信息（包括挖掘模型中没有的列）。</span><span class="sxs-lookup"><span data-stu-id="edc4d-121">If the training cases were cached when you processed the mining structure, and you have the necessary permissions, you can return information from the model cases and from the mining structure, including columns that were not included in the mining model.</span></span>  
  
##  <a name="creating-drillthrough-queries-using-dmx"></a><a name="bkmk_DMX"></a><span data-ttu-id="edc4d-122">使用 DMX 创建钻取查询</span><span class="sxs-lookup"><span data-stu-id="edc4d-122">Creating Drillthrough Queries using DMX</span></span>  
 <span data-ttu-id="edc4d-123">如果您对模型或结构具有权限，则可以通过创建 DMX 查询来钻取到事例数据。</span><span class="sxs-lookup"><span data-stu-id="edc4d-123">You can drill through to case data by creating a DMX query, if you have permissions on the model or on the structure.</span></span> <span data-ttu-id="edc4d-124">有关在 DMX 中创建钻取查询的语法的示例，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="edc4d-124">For examples of the syntax for creating drillthrough queries in DMX, see the following topic:</span></span>  
  
 [<span data-ttu-id="edc4d-125">使用 DMX 来创建钻取查询</span><span class="sxs-lookup"><span data-stu-id="edc4d-125">Create Drillthrough Queries using DMX</span></span>](create-drillthrough-queries-using-dmx.md)  
  
##  <a name="considerations-when-using-drillthrough"></a><a name="bkmk_Considerations"></a><span data-ttu-id="edc4d-126">使用钻取时的注意事项</span><span class="sxs-lookup"><span data-stu-id="edc4d-126">Considerations When Using Drillthrough</span></span>  
  
-   <span data-ttu-id="edc4d-127">如果使用数据挖掘向导，则用以对模型事例启用钻取的选项位于向导的最后一页。</span><span class="sxs-lookup"><span data-stu-id="edc4d-127">If you use the Data Mining Wizard, the option to enable drillthrough to the model cases is on the final page of the wizard.</span></span> <span data-ttu-id="edc4d-128">默认情况下，钻取功能处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="edc4d-128">Drillthrough is disabled by default.</span></span> <span data-ttu-id="edc4d-129">有关详细信息，请参阅[完成向导（数据挖掘向导）](../completing-the-wizard-data-mining-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="edc4d-129">For more information, see [Completing the Wizard &#40;Data Mining Wizard&#41;](../completing-the-wizard-data-mining-wizard.md).</span></span>  
  
-   <span data-ttu-id="edc4d-130">您可以向现有的挖掘模型中添加钻取功能，但是，如果这样做，必须重新处理该模型，才能钻取到所需的数据。</span><span class="sxs-lookup"><span data-stu-id="edc4d-130">You can add the ability to drill through on an existing mining model, but if you do, the model must be reprocessed before you can drill through to the data.</span></span>  
  
-   <span data-ttu-id="edc4d-131">钻取就是检索在处理挖掘结构时缓存的定型事例的相关信息。</span><span class="sxs-lookup"><span data-stu-id="edc4d-131">Drillthrough works by retrieving information about the training cases that was cached when you processed the mining structure.</span></span> <span data-ttu-id="edc4d-132">因此，如果在结构处理完毕后，通过将 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> 属性更改为 `ClearAfterProcessing`，清除了缓存的数据，则钻取功能将无法正常工作。</span><span class="sxs-lookup"><span data-stu-id="edc4d-132">Therefore, if you cleared the cached data after processing the structure by changing the <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> property to `ClearAfterProcessing`, drillthrough will not work.</span></span> <span data-ttu-id="edc4d-133">若要对结构列启用钻取，则必须将 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> 属性更改为 `KeepTrainingCases`，然后重新处理结构。</span><span class="sxs-lookup"><span data-stu-id="edc4d-133">To enable drillthrough to structure columns, you must change the <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> property to `KeepTrainingCases` and then reprocess the structure.</span></span>  
  
-   <span data-ttu-id="edc4d-134">如果挖掘结构不允许进行钻取，但是挖掘模型允许进行钻取，则只能查看模型事例中的信息，而不能查看挖掘结构中的信息。</span><span class="sxs-lookup"><span data-stu-id="edc4d-134">If the mining structure does not allow drillthrough but the mining model does, you can view information only from the model cases, and not from the mining structure.</span></span>  
  
###  <a name="security-issues-for-drillthrough"></a><a name="bkmk_Security"></a><span data-ttu-id="edc4d-135">钻取的安全问题</span><span class="sxs-lookup"><span data-stu-id="edc4d-135">Security Issues for Drillthrough</span></span>  
 <span data-ttu-id="edc4d-136">如果要从模型钻取到结构事例，则必须确认挖掘结构和挖掘模型都已将[AllowDrillThrough](https://docs.microsoft.com/bi-reference/assl/properties/allowdrillthrough-element-assl)属性设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="edc4d-136">If you want to drill through to structure cases from the model, you must verify that both the mining structure and the mining model have the [AllowDrillThrough](https://docs.microsoft.com/bi-reference/assl/properties/allowdrillthrough-element-assl) property set to `True`.</span></span> <span data-ttu-id="edc4d-137">而且，您必须是对挖掘结构和挖掘模型都具有钻取权限的角色的成员。</span><span class="sxs-lookup"><span data-stu-id="edc4d-137">Moreover, you must be a member of a role that has drillthrough permissions on both the structure and the model.</span></span> <span data-ttu-id="edc4d-138">有关如何创建角色的信息，请参阅[角色设计器（Analysis Services - 多维数据）](https://msdn.microsoft.com/library/ms189696(v=sql.120).aspx)。</span><span class="sxs-lookup"><span data-stu-id="edc4d-138">For information about how to create roles, see [Role Designer &#40;Analysis Services - Multidimensional Data&#41;](https://msdn.microsoft.com/library/ms189696(v=sql.120).aspx).</span></span> <span data-ttu-id="edc4d-139">请参阅。</span><span class="sxs-lookup"><span data-stu-id="edc4d-139">see.</span></span>  
  
 <span data-ttu-id="edc4d-140">挖掘结构和挖掘模型的钻取权限是分开设置的。</span><span class="sxs-lookup"><span data-stu-id="edc4d-140">Drillthrough permissions are set separately on the structure and model.</span></span> <span data-ttu-id="edc4d-141">即使不具有结构的钻取权限，模型的钻取权限也会允许您从模型进行钻取。</span><span class="sxs-lookup"><span data-stu-id="edc4d-141">The model permission lets you drill through from the model, even if you do not have permissions on the structure.</span></span> <span data-ttu-id="edc4d-142">如果拥有结构的钻取权限，则可通过使用 [StructureColumn (DMX)](/sql/dmx/structurecolumn-dmx) 函数，将结构列包含到模型钻取查询中。</span><span class="sxs-lookup"><span data-stu-id="edc4d-142">Drillthrough permissions on the structure provide the additional ability to include structure columns in drillthrough queries from the model, by using the [StructureColumn &#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) function.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="edc4d-143">如果对挖掘结构和挖掘模型都启用了钻取，则只要用户是拥有挖掘模型的钻取权限的角色成员，就可以查看挖掘结构中的列，即使这些列并未包含在挖掘模型中，也是如此。</span><span class="sxs-lookup"><span data-stu-id="edc4d-143">If you enable drillthrough on both the mining structure and the mining model, any user who is a member of a role that has drillthrough permissions on the mining model can also view columns in the mining structure, even if those columns are not included in the mining model.</span></span> <span data-ttu-id="edc4d-144">因此，为了保护敏感数据，应设置数据源视图来屏蔽个人信息，并且仅在需要时才允许对挖掘结构进行钻取访问。</span><span class="sxs-lookup"><span data-stu-id="edc4d-144">Therefore, to protect sensitive data, you should set up the data source view to mask personal information, and allow drillthrough access on the mining structure only when necessary.</span></span>  
  
###  <a name="limitations-on-drillthrough"></a><a name="bkmk_Limits"></a><span data-ttu-id="edc4d-145">钻取限制</span><span class="sxs-lookup"><span data-stu-id="edc4d-145">Limitations on Drillthrough</span></span>  
  
-   <span data-ttu-id="edc4d-146">下面的限制适用于针对模型的钻取操作，具体情况取决于用来创建模型的算法：</span><span class="sxs-lookup"><span data-stu-id="edc4d-146">The following limitations apply to drillthrough operations on a model, depending on the algorithm that was used to create the model:</span></span>  
  
|<span data-ttu-id="edc4d-147">算法名称</span><span class="sxs-lookup"><span data-stu-id="edc4d-147">Algorithm name</span></span>|<span data-ttu-id="edc4d-148">问题</span><span class="sxs-lookup"><span data-stu-id="edc4d-148">Issue</span></span>|  
|--------------------|-----------|  
|<span data-ttu-id="edc4d-149">Microsoft Naïve Bayes 算法</span><span class="sxs-lookup"><span data-stu-id="edc4d-149">Microsoft Naïve Bayes algorithm</span></span>|<span data-ttu-id="edc4d-150">不支持。</span><span class="sxs-lookup"><span data-stu-id="edc4d-150">Not supported.</span></span> <span data-ttu-id="edc4d-151">这些算法不为内容中的特定节点分配事例。</span><span class="sxs-lookup"><span data-stu-id="edc4d-151">These algorithms do not assign cases to specific nodes in the content.</span></span>|  
|<span data-ttu-id="edc4d-152">Microsoft 神经网络算法</span><span class="sxs-lookup"><span data-stu-id="edc4d-152">Microsoft Neural Network algorithm</span></span>|<span data-ttu-id="edc4d-153">不支持。</span><span class="sxs-lookup"><span data-stu-id="edc4d-153">Not supported.</span></span> <span data-ttu-id="edc4d-154">这些算法不为内容中的特定节点分配事例。</span><span class="sxs-lookup"><span data-stu-id="edc4d-154">These algorithms do not assign cases to specific nodes in the content.</span></span>|  
|<span data-ttu-id="edc4d-155">Microsoft 逻辑回归算法</span><span class="sxs-lookup"><span data-stu-id="edc4d-155">Microsoft Logistic Regression algorithm</span></span>|<span data-ttu-id="edc4d-156">不支持。</span><span class="sxs-lookup"><span data-stu-id="edc4d-156">Not supported.</span></span> <span data-ttu-id="edc4d-157">这些算法不为内容中的特定节点分配事例。</span><span class="sxs-lookup"><span data-stu-id="edc4d-157">These algorithms do not assign cases to specific nodes in the content.</span></span>|  
|<span data-ttu-id="edc4d-158">Microsoft 线性回归算法</span><span class="sxs-lookup"><span data-stu-id="edc4d-158">Microsoft Linear Regression algorithm</span></span>|<span data-ttu-id="edc4d-159">。</span><span class="sxs-lookup"><span data-stu-id="edc4d-159">Supported.</span></span> <span data-ttu-id="edc4d-160">但是，由于该模型创建一个节点 (`All`)，因此钻取时会返回该模型的所有定型事例。</span><span class="sxs-lookup"><span data-stu-id="edc4d-160">However, because the model creates a single node, `All`, drilling through returns all the training cases for the model.</span></span> <span data-ttu-id="edc4d-161">如果定型集非常大，则加载结果可能会需要很长时间。</span><span class="sxs-lookup"><span data-stu-id="edc4d-161">If the training set is large, loading the results may take a very long time.</span></span>|  
|<span data-ttu-id="edc4d-162">Microsoft 时序算法</span><span class="sxs-lookup"><span data-stu-id="edc4d-162">Microsoft Time Series algorithm</span></span>|<span data-ttu-id="edc4d-163">。</span><span class="sxs-lookup"><span data-stu-id="edc4d-163">Supported.</span></span> <span data-ttu-id="edc4d-164">但是，不能通过使用数据挖掘设计器的 **“挖掘模型查看器”** 来钻取到结构或事例数据，</span><span class="sxs-lookup"><span data-stu-id="edc4d-164">However, you cannot drill through to structure or case data by using the **Mining Model Viewer** in Data Mining Designer.</span></span> <span data-ttu-id="edc4d-165">而必须创建一个 DMX 查询。</span><span class="sxs-lookup"><span data-stu-id="edc4d-165">You must create a DMX query instead.</span></span><br /><br /> <span data-ttu-id="edc4d-166">同样，不能钻取到特定节点，也不能编写一个 DMX 查询来检索时序模型内特定节点中的事例。</span><span class="sxs-lookup"><span data-stu-id="edc4d-166">Also, you cannot drill through to specific nodes, or write a DMX query to retrieve cases in specific nodes of a time series model.</span></span> <span data-ttu-id="edc4d-167">可以通过使用其他条件（如日期或属性值）来从模型或结构中检索事例数据。</span><span class="sxs-lookup"><span data-stu-id="edc4d-167">You can retrieve case data from either the model or the structure by using other criteria, such as date or attribute values.</span></span><br /><br /> <span data-ttu-id="edc4d-168">还可使用 [Lag (DMX)](/sql/dmx/lag-dmx) 函数，从模型中的事例返回日期。</span><span class="sxs-lookup"><span data-stu-id="edc4d-168">You can also return the dates from the cases in the model, by using the [Lag &#40;DMX&#41;](/sql/dmx/lag-dmx) function.</span></span><br /><br /> <span data-ttu-id="edc4d-169">如果希望查看由 Microsoft 时序算法创建的 ARTXP 和 ARIMA 节点的详细信息，则可使用 [Microsoft 一般内容树查看器（数据挖掘）](../microsoft-generic-content-tree-viewer-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="edc4d-169">If you wish to view details of the ARTXP and ARIMA nodes created by the Microsoft Time Series algorithm, you can use the [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>|  
  
##  <a name="related-tasks"></a><a name="bkmk_Tasks"></a> <span data-ttu-id="edc4d-170">相关任务</span><span class="sxs-lookup"><span data-stu-id="edc4d-170">Related Tasks</span></span>  
 <span data-ttu-id="edc4d-171">通过以下链接在特定方案中使用钻取。</span><span class="sxs-lookup"><span data-stu-id="edc4d-171">Use the following links to work with drillthrough in specific scenarios.</span></span>  
  
|<span data-ttu-id="edc4d-172">任务</span><span class="sxs-lookup"><span data-stu-id="edc4d-172">Task</span></span>|<span data-ttu-id="edc4d-173">链接</span><span class="sxs-lookup"><span data-stu-id="edc4d-173">Link</span></span>|  
|----------|----------|  
|<span data-ttu-id="edc4d-174">描述在数据挖掘设计器中使用钻取的过程</span><span class="sxs-lookup"><span data-stu-id="edc4d-174">Procedure describing use of drillthrough in the Data Mining Designer</span></span>|[<span data-ttu-id="edc4d-175">从挖掘模型钻取到事例数据</span><span class="sxs-lookup"><span data-stu-id="edc4d-175">Drill Through to Case Data from a Mining Model</span></span>](drill-through-to-case-data-from-a-mining-model.md)|  
|<span data-ttu-id="edc4d-176">改变现有的挖掘模型以允许钻取</span><span class="sxs-lookup"><span data-stu-id="edc4d-176">To alter an existing mining model to allow drillthrough</span></span>|[<span data-ttu-id="edc4d-177">对挖掘模型启用钻取</span><span class="sxs-lookup"><span data-stu-id="edc4d-177">Enable Drillthrough for a Mining Model</span></span>](enable-drillthrough-for-a-mining-model.md)|  
|<span data-ttu-id="edc4d-178">使用 DMX WITH DRILLTHROUGH 子句对挖掘模型启用钻取。</span><span class="sxs-lookup"><span data-stu-id="edc4d-178">Enabling drillthrough on a mining structure by using the DMX WITH DRILLTHROUGH clause</span></span>|[<span data-ttu-id="edc4d-179">CREATE MINING STRUCTURE (DMX)</span><span class="sxs-lookup"><span data-stu-id="edc4d-179">CREATE MINING STRUCTURE &#40;DMX&#41;</span></span>](/sql/dmx/create-mining-structure-dmx)|  
|<span data-ttu-id="edc4d-180">有关分配适用于对挖掘结构和挖掘模型进行钻取的权限的信息</span><span class="sxs-lookup"><span data-stu-id="edc4d-180">For information about assigning permissions that apply to drillthrough on mining structures and mining models</span></span>|[<span data-ttu-id="edc4d-181">授予数据挖掘结构和模型的权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="edc4d-181">Grant permissions on data mining structures and models &#40;Analysis Services&#41;</span></span>](../multidimensional-models/grant-permissions-on-data-mining-structures-and-models-analysis-services.md)|  
  
## <a name="see-also"></a><span data-ttu-id="edc4d-182">另请参阅</span><span class="sxs-lookup"><span data-stu-id="edc4d-182">See Also</span></span>  
 <span data-ttu-id="edc4d-183">[数据挖掘模型查看器](data-mining-model-viewers.md) </span><span class="sxs-lookup"><span data-stu-id="edc4d-183">[Data Mining Model Viewers](data-mining-model-viewers.md) </span></span>  
 [<span data-ttu-id="edc4d-184">数据挖掘查询</span><span class="sxs-lookup"><span data-stu-id="edc4d-184">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
