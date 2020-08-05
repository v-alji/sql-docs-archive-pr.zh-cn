---
title: 第4课：浏览自行车购买者挖掘模型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8de3c500-f881-42da-a096-b6c03300d58d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 709df371d840d4b24e420b4fcd08750fd31e8075
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581073"
---
# <a name="lesson-4-browsing-the-bike-buyer-mining-models"></a><span data-ttu-id="29f20-102">第 4 课：浏览自行车购买者挖掘模型</span><span class="sxs-lookup"><span data-stu-id="29f20-102">Lesson 4: Browsing the Bike Buyer Mining Models</span></span>
  <span data-ttu-id="29f20-103">在本课中，您将使用[SELECT (DMX) ](/sql/dmx/select-dmx)语句来浏览决策树中的内容，并对在[第2课：向预测挖掘结构中添加挖掘模型](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)中创建的挖掘模型进行聚类分析。</span><span class="sxs-lookup"><span data-stu-id="29f20-103">In this lesson, you will use the [SELECT (DMX)](/sql/dmx/select-dmx) statement to explore the content in the decision tree and clustering mining models that you created in [Lesson 2: Adding Mining Models to the Predictive Mining Structure](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md).</span></span>  
  
 <span data-ttu-id="29f20-104">挖掘模型中包含的列不是由挖掘结构定义的列，而是用于说明通过算法获得的趋势和模式的特定列集。</span><span class="sxs-lookup"><span data-stu-id="29f20-104">The columns contained in a mining model are not the columns defined by the mining structure, but instead are a specific set of columns that describe the trends and patterns that are found by the algorithm.</span></span> <span data-ttu-id="29f20-105">[DMSCHEMA_MINING_MODEL_CONTENT 行集](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset)架构行集中介绍了这些挖掘模型列。</span><span class="sxs-lookup"><span data-stu-id="29f20-105">These mining model columns are described in the [DMSCHEMA_MINING_MODEL_CONTENT Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset) schema rowset.</span></span> <span data-ttu-id="29f20-106">例如，内容架构行集中的 MODEL_NAME 列包含挖掘模型的名称。</span><span class="sxs-lookup"><span data-stu-id="29f20-106">For example, the MODEL_NAME column in the content schema rowset contains the name of the mining model.</span></span> <span data-ttu-id="29f20-107">对于聚类分析挖掘模型，NODE_CAPTION 列包含每个分类的名称，NODE_DESCRIPTION 列包含每个分类的特征说明。</span><span class="sxs-lookup"><span data-stu-id="29f20-107">For a clustering mining model, the NODE_CAPTION column contains the name of each cluster, and the NODE_DESCRIPTION column contains a description of the characteristics of each cluster.</span></span> <span data-ttu-id="29f20-108">可以使用 "选择" 浏览这些列 \<model> 。DMX 中的内容语句。</span><span class="sxs-lookup"><span data-stu-id="29f20-108">You can browse these columns by using the SELECT FROM \<model>.CONTENT statement in DMX.</span></span> <span data-ttu-id="29f20-109">也可以使用该语句浏览用于创建挖掘模型的数据。</span><span class="sxs-lookup"><span data-stu-id="29f20-109">You can also use this statement to explore the data that was used to create the mining model.</span></span> <span data-ttu-id="29f20-110">为了使用该语句，必须对挖掘结构启用钻取功能。</span><span class="sxs-lookup"><span data-stu-id="29f20-110">Drillthrough must be enabled on the mining structure in order to use this statement.</span></span> <span data-ttu-id="29f20-111">有关语句的详细信息，请参阅[SELECT FROM &#60;model&#62;。DMX&#41;&#40;事例](/sql/dmx/select-from-model-content-dmx)。</span><span class="sxs-lookup"><span data-stu-id="29f20-111">For more information about the statement, see [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx).</span></span>  
  
 <span data-ttu-id="29f20-112">也可以使用 SELECT DISTINCT 语句返回离散列的所有状态。</span><span class="sxs-lookup"><span data-stu-id="29f20-112">You can also return all the states of a discrete column by using the SELECT DISTINCT statement.</span></span> <span data-ttu-id="29f20-113">例如，如果对 gender 列执行此操作，则查询将返回 `male` 和 `female`。</span><span class="sxs-lookup"><span data-stu-id="29f20-113">For example, if you perform this operation on a gender column, the query will return `male` and `female`.</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="29f20-114">课程任务</span><span class="sxs-lookup"><span data-stu-id="29f20-114">Lesson Tasks</span></span>  
 <span data-ttu-id="29f20-115">您将在本课中执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="29f20-115">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="29f20-116">浏览挖掘模型中包含的内容</span><span class="sxs-lookup"><span data-stu-id="29f20-116">Explore the content contained within the mining models</span></span>  
  
-   <span data-ttu-id="29f20-117">返回源数据中用于为挖掘模型定型的事例</span><span class="sxs-lookup"><span data-stu-id="29f20-117">Return the cases from the source data that was used to train the mining models</span></span>  
  
-   <span data-ttu-id="29f20-118">浏览其他可用于特定离散列的状态</span><span class="sxs-lookup"><span data-stu-id="29f20-118">Explore the different states available for a specific discrete column</span></span>  
  
## <a name="returning-the-content-of-a-mining-model"></a><span data-ttu-id="29f20-119">返回挖掘模型的内容</span><span class="sxs-lookup"><span data-stu-id="29f20-119">Returning the Content of a Mining Model</span></span>  
 <span data-ttu-id="29f20-120">在本课中，您将使用 "[选择 &#60;模型"&#62;。CONTENT &#40;DMX&#41;](/sql/dmx/select-from-model-dimension-content-dmx)语句返回聚类分析模型的内容。</span><span class="sxs-lookup"><span data-stu-id="29f20-120">In this lesson, you use the [SELECT FROM &#60;model&#62;.CONTENT &#40;DMX&#41;](/sql/dmx/select-from-model-dimension-content-dmx) statement to return the contents of the clustering model.</span></span>  
  
 <span data-ttu-id="29f20-121">下面是 SELECT FROM 的一般示例 \<model> 。内容语句：</span><span class="sxs-lookup"><span data-stu-id="29f20-121">The following is a generic example of the SELECT FROM \<model>.CONTENT statement:</span></span>  
  
```  
SELECT <select list> FROM [<mining model>].CONTENT  
WHERE <where clause>  
```  
  
 <span data-ttu-id="29f20-122">代码的第一行定义各列从挖掘模型内容以及与列关联的挖掘模型中返回：</span><span class="sxs-lookup"><span data-stu-id="29f20-122">The first line of the code defines the columns to return from the mining model content, and the mining model they are associated with:</span></span>  
  
```  
SELECT <select list> FROM [<mining model].CONTENT  
```  
  
 <span data-ttu-id="29f20-123">挖掘模型名称旁边的 .CONTENT 子句指定将要返回挖掘模型的内容。</span><span class="sxs-lookup"><span data-stu-id="29f20-123">The .CONTENT clause next to the name of the mining model specifies that you are returning content from the mining model.</span></span> <span data-ttu-id="29f20-124">有关挖掘模型中包含的列的详细信息，请参阅[DMSCHEMA_MINING_MODEL_CONTENT 行集](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset)。</span><span class="sxs-lookup"><span data-stu-id="29f20-124">For more information about the columns contained in the mining model, see [DMSCHEMA_MINING_MODEL_CONTENT Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset).</span></span>  
  
 <span data-ttu-id="29f20-125">您可以选择性地使用代码的最后一行筛选该语句返回的结果：</span><span class="sxs-lookup"><span data-stu-id="29f20-125">You can optionally use the final line of the code to filter the results returned by the statement:</span></span>  
  
```  
WHERE <where clause>  
```  
  
 <span data-ttu-id="29f20-126">例如，如果要将查询结果仅限制为包含大量事例的分类，则需要将以下 WHERE 子句添加到 SELECT 语句：</span><span class="sxs-lookup"><span data-stu-id="29f20-126">For example, if you want to restrict the results of the query to only the clusters that contain a high number of cases, you can add the following WHERE clause to the SELECT statement:</span></span>  
  
```  
WHERE NODE_SUPPORT > 100  
```  
  
 <span data-ttu-id="29f20-127">有关使用 WHERE 语句的详细信息，请参阅[SELECT &#40;DMX&#41;](/sql/dmx/select-dmx)。</span><span class="sxs-lookup"><span data-stu-id="29f20-127">For more information about using the WHERE statement, see [SELECT &#40;DMX&#41;](/sql/dmx/select-dmx).</span></span>  
  
#### <a name="to-return-the-content-of-the-clustering-mining-model"></a><span data-ttu-id="29f20-128">返回聚类分析挖掘模型的内容</span><span class="sxs-lookup"><span data-stu-id="29f20-128">To return the content of the clustering mining model</span></span>  
  
1.  <span data-ttu-id="29f20-129">在**对象资源管理器**中，右键单击实例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 "**新建查询**"，然后单击 " **DMX**"。</span><span class="sxs-lookup"><span data-stu-id="29f20-129">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="29f20-130">将打开查询编辑器，其中包含一个新的空白查询。</span><span class="sxs-lookup"><span data-stu-id="29f20-130">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="29f20-131">从中复制 SELECT 的一般示例 \<model> 。内容语句插入到空白查询中。</span><span class="sxs-lookup"><span data-stu-id="29f20-131">Copy the generic example of the SELECT FROM \<model>.CONTENT statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="29f20-132">将</span><span class="sxs-lookup"><span data-stu-id="29f20-132">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="29f20-133">替换为：</span><span class="sxs-lookup"><span data-stu-id="29f20-133">with:</span></span>  
  
    ```  
    *  
    ```  
  
     <span data-ttu-id="29f20-134">你还可以使用[DMSCHEMA_MINING_MODEL_CONTENT 行集中](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset)包含的任意列的列表来替换 \*。</span><span class="sxs-lookup"><span data-stu-id="29f20-134">You can also replace \* with a list of any of the columns contained within the [DMSCHEMA_MINING_MODEL_CONTENT Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset).</span></span>  
  
4.  <span data-ttu-id="29f20-135">将</span><span class="sxs-lookup"><span data-stu-id="29f20-135">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="29f20-136">替换为：</span><span class="sxs-lookup"><span data-stu-id="29f20-136">with:</span></span>  
  
    ```  
    [Clustering]  
    ```  
  
     <span data-ttu-id="29f20-137">现在，完整的语句应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="29f20-137">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT * FROM [Clustering].CONTENT  
    ```  
  
5.  <span data-ttu-id="29f20-138">在 "**文件**" 菜单上，单击 "**将 DMXQuery1 另存为**"。</span><span class="sxs-lookup"><span data-stu-id="29f20-138">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
6.  <span data-ttu-id="29f20-139">在 "**另存为**" 对话框中，浏览到相应的文件夹，并将该文件命名为 `SELECT_CONTENT.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="29f20-139">In the **Save As** dialog box, browse to the appropriate folder, and name the file `SELECT_CONTENT.dmx`.</span></span>  
  
7.  <span data-ttu-id="29f20-140">在工具栏上，单击 "**执行**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="29f20-140">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="29f20-141">查询返回挖掘模型的内容。</span><span class="sxs-lookup"><span data-stu-id="29f20-141">The query returns the content of the mining model.</span></span>  
  
## <a name="use-drillthrough"></a><span data-ttu-id="29f20-142">使用钻取功能</span><span class="sxs-lookup"><span data-stu-id="29f20-142">Use Drillthrough</span></span>  
 <span data-ttu-id="29f20-143">下一步将使用钻取语句返回用于为决策树挖掘模型定型的事例抽样。</span><span class="sxs-lookup"><span data-stu-id="29f20-143">The next step is to use the drillthrough statement to return a sampling of the cases that were used to train the decision tree mining model.</span></span> <span data-ttu-id="29f20-144">在本课中，您将使用 "[选择 &#60;模型"&#62;。用](/sql/dmx/select-from-model-content-dmx)来返回决策树模型的内容 &#40;DMX&#41;语句的事例。</span><span class="sxs-lookup"><span data-stu-id="29f20-144">In this lesson, you use the [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx) statement to return the contents of the decision tree model.</span></span>  
  
 <span data-ttu-id="29f20-145">下面是 SELECT FROM 的一般示例 \<model> 。Case 语句：</span><span class="sxs-lookup"><span data-stu-id="29f20-145">The following is a generic example of the SELECT FROM \<model>.CASES statement:</span></span>  
  
```  
SELECT <select list>   
FROM [<mining model>].CASES  
WHERE IsInNode('<node id>')  
```  
  
 <span data-ttu-id="29f20-146">代码的第一行定义从源数据返回的列和这些列所包含的挖掘模型：</span><span class="sxs-lookup"><span data-stu-id="29f20-146">The first line of the code defines the columns to return from the source data, and the mining model they are contained within:</span></span>  
  
```  
SELECT <select list> FROM [<mining model>].CASES  
```  
  
 <span data-ttu-id="29f20-147">.CASES 子句指定您正在执行钻取查询。</span><span class="sxs-lookup"><span data-stu-id="29f20-147">The .CASES clause specifies that you are performing a drillthrough query.</span></span> <span data-ttu-id="29f20-148">为了使用钻取功能，您必须在创建挖掘模型时启用该功能。</span><span class="sxs-lookup"><span data-stu-id="29f20-148">In order to use drillthrough you must enable drillthrough when you create the mining model.</span></span>  
  
 <span data-ttu-id="29f20-149">代码的最后一行可选，该行指定了要从中请求事例的挖掘模型中的节点：</span><span class="sxs-lookup"><span data-stu-id="29f20-149">The final line of the code is optional and specifies the node in the mining model that you are requesting cases from:</span></span>  
  
```  
WHERE IsInNode('<node id>')  
```  
  
 <span data-ttu-id="29f20-150">有关结合使用 WHERE 语句和 IsInNode 的详细信息，请参阅[SELECT FROM &#60;model&#62;。DMX&#41;&#40;事例](/sql/dmx/select-from-model-content-dmx)。</span><span class="sxs-lookup"><span data-stu-id="29f20-150">For more information about using the WHERE statement with IsInNode, see [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx).</span></span>  
  
#### <a name="to-return-the-cases-that-were-used-to-train-the-mining-model"></a><span data-ttu-id="29f20-151">返回用于为挖掘模型定型的事例</span><span class="sxs-lookup"><span data-stu-id="29f20-151">To return the cases that were used to train the mining model</span></span>  
  
1.  <span data-ttu-id="29f20-152">在**对象资源管理器**中，右键单击实例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 "**新建查询**"，然后单击 " **DMX**"。</span><span class="sxs-lookup"><span data-stu-id="29f20-152">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="29f20-153">将打开查询编辑器，其中包含一个新的空白查询。</span><span class="sxs-lookup"><span data-stu-id="29f20-153">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="29f20-154">从中复制 SELECT 的一般示例 \<model> 。Case 语句插入到空白查询中。</span><span class="sxs-lookup"><span data-stu-id="29f20-154">Copy the generic example of the SELECT FROM \<model>.CASES statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="29f20-155">将</span><span class="sxs-lookup"><span data-stu-id="29f20-155">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="29f20-156">替换为：</span><span class="sxs-lookup"><span data-stu-id="29f20-156">with:</span></span>  
  
    ```  
    *  
    ```  
  
     <span data-ttu-id="29f20-157">您还可以使用源数据（如 [自行车购买者]）中包含的任意列的列表替换 \*。</span><span class="sxs-lookup"><span data-stu-id="29f20-157">You can also replace \* with a list of any of the columns contained within the source data (such as [Bike Buyer]).</span></span>  
  
4.  <span data-ttu-id="29f20-158">将</span><span class="sxs-lookup"><span data-stu-id="29f20-158">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="29f20-159">替换为：</span><span class="sxs-lookup"><span data-stu-id="29f20-159">with:</span></span>  
  
    ```  
    [Decision Tree]  
    ```  
  
     <span data-ttu-id="29f20-160">现在，完整的语句应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="29f20-160">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT *   
    FROM [Decision Tree].CASES  
    ```  
  
5.  <span data-ttu-id="29f20-161">在 "**文件**" 菜单上，单击 "**将 DMXQuery1 另存为**"。</span><span class="sxs-lookup"><span data-stu-id="29f20-161">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
6.  <span data-ttu-id="29f20-162">在 "**另存为**" 对话框中，浏览到相应的文件夹，并将该文件命名为 `SELECT_DRILLTHROUGH.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="29f20-162">In the **Save As** dialog box, browse to the appropriate folder, and name the file `SELECT_DRILLTHROUGH.dmx`.</span></span>  
  
7.  <span data-ttu-id="29f20-163">在工具栏上，单击 "**执行**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="29f20-163">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="29f20-164">查询返回用于为决策树挖掘模型定型的源数据。</span><span class="sxs-lookup"><span data-stu-id="29f20-164">The query returns the source data that was used to train the decision tree mining model.</span></span>  
  
## <a name="return-the-states-of-a-discrete-mining-model-column"></a><span data-ttu-id="29f20-165">返回离散挖掘模型列的状态</span><span class="sxs-lookup"><span data-stu-id="29f20-165">Return the States of a Discrete Mining Model Column</span></span>  
 <span data-ttu-id="29f20-166">下一步将使用 SELECT DISTINCT 语句返回指定的挖掘模型列的各种可能状态。</span><span class="sxs-lookup"><span data-stu-id="29f20-166">The next step is to use the SELECT DISTINCT statement to return the different possible states in the specified mining model column.</span></span>  
  
 <span data-ttu-id="29f20-167">下面是 SELECT DISTINCT 语句的一般示例：</span><span class="sxs-lookup"><span data-stu-id="29f20-167">The following is a generic example of the SELECT DISTINCT statement:</span></span>  
  
```  
SELECT DISTINCT [<column>]   
FROM [<mining model>]  
```  
  
 <span data-ttu-id="29f20-168">代码的第一行定义了为其返回状态的挖掘模型列：</span><span class="sxs-lookup"><span data-stu-id="29f20-168">The first line of the code defines the mining model columns for which the states are returned:</span></span>  
  
```  
SELECT DISTINCT [<column>]   
```  
  
 <span data-ttu-id="29f20-169">必须包括 DISTINCT 才能返回列的所有状态。</span><span class="sxs-lookup"><span data-stu-id="29f20-169">You must include DISTINCT in order to return all of the states of the column.</span></span> <span data-ttu-id="29f20-170">如果排除 DISTINCT，则整个语句会变为预测的快捷方式并且返回指定列最可能的状态。</span><span class="sxs-lookup"><span data-stu-id="29f20-170">If you exclude DISTINCT, then the full statement becomes a shortcut for a prediction and returns the most likely state of the specified column.</span></span> <span data-ttu-id="29f20-171">有关详细信息，请参阅 [SELECT (DMX)](/sql/dmx/select-dmx)。</span><span class="sxs-lookup"><span data-stu-id="29f20-171">For more information, see [SELECT &#40;DMX&#41;](/sql/dmx/select-dmx).</span></span>  
  
#### <a name="to-return-the-states-of-a-discrete-column"></a><span data-ttu-id="29f20-172">返回离散列的状态</span><span class="sxs-lookup"><span data-stu-id="29f20-172">To return the states of a discrete column</span></span>  
  
1.  <span data-ttu-id="29f20-173">在**对象资源管理器**中，右键单击实例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 "**新建查询**"，然后单击 " **DMX**"。</span><span class="sxs-lookup"><span data-stu-id="29f20-173">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="29f20-174">将打开查询编辑器，其中包含一个新的空白查询。</span><span class="sxs-lookup"><span data-stu-id="29f20-174">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="29f20-175">将 SELECT Distinct 语句的一般示例复制到空白查询中。</span><span class="sxs-lookup"><span data-stu-id="29f20-175">Copy the generic example of the SELECT Distinct statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="29f20-176">将</span><span class="sxs-lookup"><span data-stu-id="29f20-176">Replace the following:</span></span>  
  
    ```  
    [<column,name>   
    ```  
  
     <span data-ttu-id="29f20-177">替换为：</span><span class="sxs-lookup"><span data-stu-id="29f20-177">with:</span></span>  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  <span data-ttu-id="29f20-178">将</span><span class="sxs-lookup"><span data-stu-id="29f20-178">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="29f20-179">替换为：</span><span class="sxs-lookup"><span data-stu-id="29f20-179">with:</span></span>  
  
    ```  
    [Decision Tree]  
    ```  
  
     <span data-ttu-id="29f20-180">现在，完整的语句应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="29f20-180">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT DISTINCT [Bike Buyer]   
    FROM [Decision Tree]  
    ```  
  
5.  <span data-ttu-id="29f20-181">在 "**文件**" 菜单上，单击 "**将 DMXQuery1 另存为**"。</span><span class="sxs-lookup"><span data-stu-id="29f20-181">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
6.  <span data-ttu-id="29f20-182">在 "**另存为**" 对话框中，浏览到相应的文件夹，并将该文件命名为 `SELECT_DISCRETE.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="29f20-182">In the **Save As** dialog box, browse to the appropriate folder, and name the file `SELECT_DISCRETE.dmx`.</span></span>  
  
7.  <span data-ttu-id="29f20-183">在工具栏上，单击 "**执行**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="29f20-183">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="29f20-184">查询返回 Bike Buyer 列的可能状态。</span><span class="sxs-lookup"><span data-stu-id="29f20-184">The query returns the possible states of the Bike Buyer column.</span></span>  
  
 <span data-ttu-id="29f20-185">在下一课中，您将使用决策树挖掘模型预测潜在的客户是否为自行车购买者。</span><span class="sxs-lookup"><span data-stu-id="29f20-185">In the next lesson, you will predict whether potential customers will be bike buyers by using the decision tree mining model.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="29f20-186">下一课</span><span class="sxs-lookup"><span data-stu-id="29f20-186">Next Lesson</span></span>  
 [<span data-ttu-id="29f20-187">第 5 课：执行预测查询</span><span class="sxs-lookup"><span data-stu-id="29f20-187">Lesson 5: Executing Prediction Queries</span></span>](../../2014/tutorials/lesson-5-executing-prediction-queries.md)  
  
  
