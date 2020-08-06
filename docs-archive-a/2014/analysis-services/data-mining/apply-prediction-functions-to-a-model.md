---
title: 将预测函数应用于模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Model Prediction [Analysis Services], selecting mining models
ms.assetid: cf9a97e2-c249-441b-af12-c977c1a91c44
author: minewiskan
ms.author: owend
ms.openlocfilehash: fde9de00adaa1712a9db6e18aabc6a83dd660efb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577924"
---
# <a name="apply-prediction-functions-to-a-model"></a><span data-ttu-id="ac068-102">将预测函数应用于模型</span><span class="sxs-lookup"><span data-stu-id="ac068-102">Apply Prediction Functions to a Model</span></span>
  <span data-ttu-id="ac068-103">若要创建预测查询，必须先选择查询基于的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="ac068-103">To create a prediction query, you must first select the mining model on which the query will be based.</span></span> <span data-ttu-id="ac068-104">可以选择当前项目中存在的任何挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="ac068-104">You can select any mining model that exists in the current project.</span></span>  
  
 <span data-ttu-id="ac068-105">选择模型后，可向查询添加 *预测函数* 。</span><span class="sxs-lookup"><span data-stu-id="ac068-105">After you have selected a model, add a *prediction function* to the query.</span></span> <span data-ttu-id="ac068-106">导入是为了理解预测函数用于许多用途-是的，你可以预测值，但也可以获取相关的统计信息，以及在生成预测时使用的信息。</span><span class="sxs-lookup"><span data-stu-id="ac068-106">It is import to understand that prediction functions are used for many purposes-yes, you can predict values, but you can also get related statistics, as well as information that was used in generating the prediction.</span></span> <span data-ttu-id="ac068-107">预测函数可返回以下类型的值：</span><span class="sxs-lookup"><span data-stu-id="ac068-107">Prediction functions can return the following types of values:</span></span>  
  
-   <span data-ttu-id="ac068-108">可预测属性的名称和预测到的值。</span><span class="sxs-lookup"><span data-stu-id="ac068-108">The name of the predictable attribute, and the value that is predicted.</span></span>  
  
-   <span data-ttu-id="ac068-109">有关预测值的分布和方差的统计信息。</span><span class="sxs-lookup"><span data-stu-id="ac068-109">Statistics about the distribution and variance of the predicted values.</span></span>  
  
-   <span data-ttu-id="ac068-110">指定结果或所有可能结果的概率。</span><span class="sxs-lookup"><span data-stu-id="ac068-110">The probability of a specified outcome, or of all possible outcomes.</span></span>  
  
-   <span data-ttu-id="ac068-111">探顶分数或探底分数，探顶值或探底值。</span><span class="sxs-lookup"><span data-stu-id="ac068-111">The top or bottom scores or values.</span></span>  
  
-   <span data-ttu-id="ac068-112">与指定节点、对象或属性关联的值。</span><span class="sxs-lookup"><span data-stu-id="ac068-112">Values associated with a specified node, object, or attribute.</span></span>  
  
 <span data-ttu-id="ac068-113">虽然有多种预测函数可供您使用，但您必须选择适用于您创建的模型类型的函数。</span><span class="sxs-lookup"><span data-stu-id="ac068-113">There is a wide variety of prediction functions that you can use, but you must choose the function that suits the type of model you created.</span></span> <span data-ttu-id="ac068-114">此选择一般取决于创建模型所用的算法。</span><span class="sxs-lookup"><span data-stu-id="ac068-114">Usually this choice depends on the algorithm used to create the model.</span></span>  
  
-   <span data-ttu-id="ac068-115">有关几乎所有模型类型都支持的预测函数的列表，请参阅[通用预测函数 (DMX)](/sql/dmx/general-prediction-functions-dmx)。</span><span class="sxs-lookup"><span data-stu-id="ac068-115">For a list of the prediction functions that are supported for almost all model types, see [General Prediction Functions &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx).</span></span>  
  
-   <span data-ttu-id="ac068-116">此外，各算法还支持多种专用函数。</span><span class="sxs-lookup"><span data-stu-id="ac068-116">Additionally, individual algorithms support a variety of specialized functions.</span></span> <span data-ttu-id="ac068-117">例如，如果基于 Microsoft 聚类分析算法创建了挖掘模型，则可以使用专门的预测函数来查找有关群集的信息，如从数据值到群集形心的距离。</span><span class="sxs-lookup"><span data-stu-id="ac068-117">For example, if you create a mining model based on the Microsoft Clustering algorithm, you can use specialized prediction functions to find information about the clusters, such as the distance from a data value to the cluster centroid.</span></span>  
  
     <span data-ttu-id="ac068-118">有关如何查询特定类型的挖掘模型的示例，请参阅[数据挖掘算法（Analysis Services - 数据挖掘）](data-mining-algorithms-analysis-services-data-mining.md)中的算法参考主题。</span><span class="sxs-lookup"><span data-stu-id="ac068-118">For examples of how to query a specific type of mining model, see the algorithm reference topic, in [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span>  
  
### <a name="choose-a-mining-model-to-use-for-prediction"></a><span data-ttu-id="ac068-119">选择用于预测的挖掘模型</span><span class="sxs-lookup"><span data-stu-id="ac068-119">Choose a mining model to use for prediction</span></span>  
  
1.  <span data-ttu-id="ac068-120">从 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，右键单击模型，然后选择“生成预测查询”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ac068-120">From [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click the model, and select **Build Prediction Query**.</span></span>  
  
     <span data-ttu-id="ac068-121">-- 或者 --</span><span class="sxs-lookup"><span data-stu-id="ac068-121">--OR --</span></span>  
  
     <span data-ttu-id="ac068-122">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，单击选项卡 **“挖掘模型预测”**，然后单击 **“挖掘模型”** 表中的  **“选择模型”** 。</span><span class="sxs-lookup"><span data-stu-id="ac068-122">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the tab, **Mining Model Prediction**, and then click **Select Model** in the  **Mining Model** table.</span></span>  
  
2.  <span data-ttu-id="ac068-123">在 **“选择挖掘模型”** 对话框中，选择挖掘模型，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="ac068-123">In the **Select Mining Model** dialog box, select a mining model, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ac068-124">您可以选择当前 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库中的任何模型。</span><span class="sxs-lookup"><span data-stu-id="ac068-124">You can choose any model within the current [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="ac068-125">若要使用其他数据库中的模型创建查询，则必须在该数据库的上下文中打开新查询窗口，或打开包含该模型的解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="ac068-125">To create a query using a model in a different database, you must either open a new query window in the context of that database, or open the solution file that contains that model.</span></span>  
  
### <a name="add-prediction-functions-to-a-query"></a><span data-ttu-id="ac068-126">向查询添加预测函数</span><span class="sxs-lookup"><span data-stu-id="ac068-126">Add prediction functions to a query</span></span>  
  
1.  <span data-ttu-id="ac068-127">在 **“预测查询生成器”** 中，通过在 **“单独查询输入”** 对话框中提供值或将模型映射到外部数据源来配置用于预测的输入数据。</span><span class="sxs-lookup"><span data-stu-id="ac068-127">In the **Prediction Query Builder**, configure the input data used for prediction, either by providing values in the **Singleton Query Input** dialog box, or by mapping the model to an external data source.</span></span>  
  
     <span data-ttu-id="ac068-128">有关详细信息，请参阅 [为预测查询选择和映射输入数据](choose-and-map-input-data-for-a-prediction-query.md)。</span><span class="sxs-lookup"><span data-stu-id="ac068-128">For more information, see [Choose and Map Input Data for a Prediction Query](choose-and-map-input-data-for-a-prediction-query.md).</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="ac068-129">无需提供用于生成预测的输入。</span><span class="sxs-lookup"><span data-stu-id="ac068-129">It is not required that you provide inputs to generate predictions.</span></span> <span data-ttu-id="ac068-130">当没有输入时，算法通常将返回所有可能的输入中可能性最大的预测值。</span><span class="sxs-lookup"><span data-stu-id="ac068-130">When there is no input, the algorithm will typically return the mostly likely predicted value across all possible inputs.</span></span>  
  
2.  <span data-ttu-id="ac068-131">单击 **“源”** 列，然后从列表中选择一个值：</span><span class="sxs-lookup"><span data-stu-id="ac068-131">Click the **Source** column, and choose a value from the list:</span></span>  
  
    |||  
    |-|-|  
    |**\<model name>**|<span data-ttu-id="ac068-132">选择此选项将在输出中包含挖掘模型的值。</span><span class="sxs-lookup"><span data-stu-id="ac068-132">Select this option to include values from the mining model in the output.</span></span> <span data-ttu-id="ac068-133">只能添加可预测的列。</span><span class="sxs-lookup"><span data-stu-id="ac068-133">You can only add predictable columns.</span></span><br /><br /> <span data-ttu-id="ac068-134">从模型添加列时，返回的结果是该列中值的重复列表。</span><span class="sxs-lookup"><span data-stu-id="ac068-134">When you add a column from the model, the result returned is the non-distinct list of values in that column.</span></span><br /><br /> <span data-ttu-id="ac068-135">使用此选项添加的列将包含在生成的 DMX 语句的 SELECT 部分。</span><span class="sxs-lookup"><span data-stu-id="ac068-135">The columns that you add with this option are included in the SELECT portion of the resulting DMX statement.</span></span>|  
    |<span data-ttu-id="ac068-136">**Prediction Function**</span><span class="sxs-lookup"><span data-stu-id="ac068-136">**Prediction Function**</span></span>|<span data-ttu-id="ac068-137">选择此选项将浏览预测函数的列表。</span><span class="sxs-lookup"><span data-stu-id="ac068-137">Select this option to browse a list of prediction functions.</span></span><br /><br /> <span data-ttu-id="ac068-138">您选择的值或函数将添加到生成的 DMX 语句的 SELECT 部分。</span><span class="sxs-lookup"><span data-stu-id="ac068-138">The values or functions you select are added to the SELECT portion of the resulting DMX statement.</span></span><br /><br /> <span data-ttu-id="ac068-139">已选择的模型的类型不会筛选或约束预测函数的列表。</span><span class="sxs-lookup"><span data-stu-id="ac068-139">The list of prediction functions is not filtered or constrained by the type of model you have selected.</span></span> <span data-ttu-id="ac068-140">因此，如果对当前模型类型是否支持该函数有任何疑问，则可以只将函数添加到列表并查看是否出错。</span><span class="sxs-lookup"><span data-stu-id="ac068-140">Therefore, if you have any doubt about whether the function is supported for the current model type, you can just add the function to the list and see if there is an error.</span></span><br /><br /> <span data-ttu-id="ac068-141">前置有 $ 的列表项（如 $AdjustedProbability）表示您使用函数 `PredictHistogram` 时输出的嵌套表中的列。</span><span class="sxs-lookup"><span data-stu-id="ac068-141">List items that are preceded by $ (such as $AdjustedProbability) represent columns from the nested table that is output when you use the function, `PredictHistogram`.</span></span> <span data-ttu-id="ac068-142">这些是可用于返回单个列而不返回嵌套表的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="ac068-142">These are shortcuts that you can use to return a single column and not a nested table.</span></span>|  
    |<span data-ttu-id="ac068-143">**自定义表达式**</span><span class="sxs-lookup"><span data-stu-id="ac068-143">**Custom Expression**</span></span>|<span data-ttu-id="ac068-144">选择此选项将键入自定义表达式然后向输出分配别名。</span><span class="sxs-lookup"><span data-stu-id="ac068-144">Select this option to type a custom expression and then assign an alias to the output.</span></span><br /><br /> <span data-ttu-id="ac068-145">自定义表达式将添加到生成的 DMX 预测查询的 SELECT 部分。</span><span class="sxs-lookup"><span data-stu-id="ac068-145">The custom expression is added to the SELECT portion of the resulting DMX prediction query.</span></span><br /><br /> <span data-ttu-id="ac068-146">如果要为每行的输出添加文本、调用 VB 函数或调用自定义存储过程，则此选项会很有用。</span><span class="sxs-lookup"><span data-stu-id="ac068-146">This option is useful if you want to add text for output with each row, to call VB functions, or to call custom stored procedures.</span></span><br /><br /> <span data-ttu-id="ac068-147">有关使用 DMX 中的 VBA 和 Excel 函数的信息，请参阅 [MDX 和 DAX 中的 VBA 函数](/sql/mdx/vba-functions-in-mdx-and-dax)。</span><span class="sxs-lookup"><span data-stu-id="ac068-147">For information about using VBA and Excel functions from DMX, see [VBA functions in MDX and DAX](/sql/mdx/vba-functions-in-mdx-and-dax).</span></span>|  
  
3.  <span data-ttu-id="ac068-148">在添加每个函数或表达式后，切换到 DMX 视图可查看该函数在 DMX 语句中的添加方式。</span><span class="sxs-lookup"><span data-stu-id="ac068-148">After adding each function or expression, switch to DMX view to see how the function is added within the DMX statement.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="ac068-149">在您单击 **“结果”** 之前，预测查询生成器不会验证 DMX。</span><span class="sxs-lookup"><span data-stu-id="ac068-149">The Prediction Query Builder does not validate the DMX until you click **Results**.</span></span> <span data-ttu-id="ac068-150">通常，您会发现查询生成器所生成的表达式不是有效 DMX。</span><span class="sxs-lookup"><span data-stu-id="ac068-150">Often, you will find that the expression that is produced by the query builder is not valid DMX.</span></span> <span data-ttu-id="ac068-151">典型的原因是，引用的列与可预测列不相关或尝试预测嵌套表中的列（这需要嵌套 SELECT 语句）。</span><span class="sxs-lookup"><span data-stu-id="ac068-151">Typical causes are referencing a column that is not related to the predictable column, or trying to predict a column in a nested table, which requires a sub-SELECT statement.</span></span> <span data-ttu-id="ac068-152">此时，您可以切换到 DMX 视图并继续编辑该语句。</span><span class="sxs-lookup"><span data-stu-id="ac068-152">At this point, you can switch to DMX view and continue editing the statement.</span></span>  
  
### <a name="example-create-a-query-on-a-clustering-model"></a><span data-ttu-id="ac068-153">示例：创建对聚类分析模型的查询</span><span class="sxs-lookup"><span data-stu-id="ac068-153">Example: Create a query on a clustering model</span></span>  
  
1.  <span data-ttu-id="ac068-154">如果没有可用于生成此示例查询的聚类分析模型，请使用 [数据挖掘基础教程](../../tutorials/basic-data-mining-tutorial.md)创建 [TM_Clustering] 模型。</span><span class="sxs-lookup"><span data-stu-id="ac068-154">If you do not have a clustering model available for building this sample query, create the model, [TM_Clustering], using the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span>  
  
2.  <span data-ttu-id="ac068-155">从 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，右键单击模型 [TM_Clustering]，然后选择“生成预测查询”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ac068-155">From [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click the model, [TM_Clustering], and select **Build Prediction Query**.</span></span>  
  
3.  <span data-ttu-id="ac068-156">从 **“挖掘模型”** 菜单中选择 **“单独查询”**。</span><span class="sxs-lookup"><span data-stu-id="ac068-156">From the **Mining Model** menu, select **Singleton Query**.</span></span>  
  
4.  <span data-ttu-id="ac068-157">在 **“单独查询输入”** 对话框中，将以下值设置为输入：</span><span class="sxs-lookup"><span data-stu-id="ac068-157">In the **Singleton Query Input** dialog box, set the following values as inputs:</span></span>  
  
    -   <span data-ttu-id="ac068-158">Gender = M</span><span class="sxs-lookup"><span data-stu-id="ac068-158">Gender = M</span></span>  
  
    -   <span data-ttu-id="ac068-159">Commute Distance = 5-10 miles</span><span class="sxs-lookup"><span data-stu-id="ac068-159">Commute Distance = 5-10 miles</span></span>  
  
5.  <span data-ttu-id="ac068-160">在查询网格中，为“源”\*\*\*\* 选择 TM_Clustering 挖掘模型并添加列 [Bike Buyer]。</span><span class="sxs-lookup"><span data-stu-id="ac068-160">In the query grid, for **Source**, select TM_Clustering mining model, and add the column, [Bike Buyer].</span></span>  
  
6.  <span data-ttu-id="ac068-161">对于 "**源**"，选择 "**预测函数**" 并添加函数 `Cluster` 。</span><span class="sxs-lookup"><span data-stu-id="ac068-161">For **Source**, select **Prediction Function**, and add the function, `Cluster`.</span></span>  
  
7.  <span data-ttu-id="ac068-162">对于 "**源**"，选择 "**预测函数**"，添加函数， `PredictSupport` 并将 "模型" 列 [自行车买家] 拖到 "**条件/参数**" 框中。</span><span class="sxs-lookup"><span data-stu-id="ac068-162">For **Source**, select **Prediction Function**, add the function, `PredictSupport`, and drag the model column [Bike Buyer] into the **Criteria/Argument** box.</span></span> <span data-ttu-id="ac068-163">在“别名”列中键入 **Support** 。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="ac068-163">Type **Support** in the **Alias** column.</span></span>  
  
     <span data-ttu-id="ac068-164">从“条件/参数”\*\*\*\* 框复制表示预测函数和列引用的表达式。</span><span class="sxs-lookup"><span data-stu-id="ac068-164">Copy the expression representing the prediction function and column reference from the **Criteria/Argument** box.</span></span>  
  
8.  <span data-ttu-id="ac068-165">为 **“源”** 选择 **“自定义表达式”**，键入别名，然后使用以下语法引用 Excel CEILING 函数：</span><span class="sxs-lookup"><span data-stu-id="ac068-165">For **Source**, select **Custom Expression**, type an alias, and then reference the Excel CEILING function by using the following syntax:</span></span>  
  
    ```  
    Excel![CEILING](<arguments) as <return type>  
    ```  
  
     <span data-ttu-id="ac068-166">将列引用作为该函数的参数粘贴。</span><span class="sxs-lookup"><span data-stu-id="ac068-166">Paste the column reference in as the argument to the function.</span></span>  
  
     <span data-ttu-id="ac068-167">例如，下面的表达式返回支持值的 CEILING：</span><span class="sxs-lookup"><span data-stu-id="ac068-167">For example, the following expression returns the CEILING of the support value:</span></span>  
  
    ```  
    EXCEL!CEILING(PredictSupport([TM_Clustering].[Bike Buyer]),2)  
    ```  
  
     <span data-ttu-id="ac068-168">在 **“别名”** 列中键入 CEILING。</span><span class="sxs-lookup"><span data-stu-id="ac068-168">Type CEILING in the **Alias** column.</span></span>  
  
9. <span data-ttu-id="ac068-169">单击 **“切换到查询文本视图”** 检查生成的 DMX 语句，然后单击 **“切换到查询结果视图”** 查看预测查询输出的列。</span><span class="sxs-lookup"><span data-stu-id="ac068-169">Click **Switch to query text view** to review the DMX statement that was generated, and then click **Switch to query result view** to see the columns output by the prediction query.</span></span>  
  
     <span data-ttu-id="ac068-170">下表显示了预期的结果：</span><span class="sxs-lookup"><span data-stu-id="ac068-170">The following table shows the expected results:</span></span>  
  
    |<span data-ttu-id="ac068-171">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="ac068-171">Bike Buyer</span></span>|<span data-ttu-id="ac068-172">$Cluster</span><span class="sxs-lookup"><span data-stu-id="ac068-172">$Cluster</span></span>|<span data-ttu-id="ac068-173">Support</span><span class="sxs-lookup"><span data-stu-id="ac068-173">SUPPORT</span></span>|<span data-ttu-id="ac068-174">CEILING</span><span class="sxs-lookup"><span data-stu-id="ac068-174">CEILING</span></span>|  
    |----------------|--------------|-------------|-------------|  
    |<span data-ttu-id="ac068-175">0</span><span class="sxs-lookup"><span data-stu-id="ac068-175">0</span></span>|<span data-ttu-id="ac068-176">群集 8</span><span class="sxs-lookup"><span data-stu-id="ac068-176">Cluster 8</span></span>|<span data-ttu-id="ac068-177">954</span><span class="sxs-lookup"><span data-stu-id="ac068-177">954</span></span>|<span data-ttu-id="ac068-178">953.948638926372</span><span class="sxs-lookup"><span data-stu-id="ac068-178">953.948638926372</span></span>|  
  
 <span data-ttu-id="ac068-179">如果要在语句中的其他位置添加其他子句（例如，如果要添加 WHERE 子句），则无法使用网格添加该子句;必须先切换到 DMX 视图。</span><span class="sxs-lookup"><span data-stu-id="ac068-179">If you want to add other clauses elsewhere in the statement-for example, if you want to add a WHERE clause-you cannot add it by using the grid; you must switch to DMX view first.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac068-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ac068-180">See Also</span></span>  
 [<span data-ttu-id="ac068-181">数据挖掘查询</span><span class="sxs-lookup"><span data-stu-id="ac068-181">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
