---
title: 第2课：向自行车购买者挖掘结构添加挖掘模型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 03fe44c5-6452-4ed0-95f6-9682670c0f52
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: de65fb7a85154f607cd8f266faec4621cdc41476
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690264"
---
# <a name="lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure"></a><span data-ttu-id="5a195-102">第 2 课：向自行车购买者挖掘结构添加挖掘模型</span><span class="sxs-lookup"><span data-stu-id="5a195-102">Lesson 2: Adding Mining Models to the Bike Buyer Mining Structure</span></span>
  <span data-ttu-id="5a195-103">在本课中，您将向创建的自行车购买者挖掘结构中添加两个挖掘模型[：第1课：创建自行车购买者挖掘结构](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="5a195-103">In this lesson, you will add two mining models to the Bike Buyer mining structure that you created [Lesson 1: Creating the Bike Buyer Mining Structure](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md).</span></span> <span data-ttu-id="5a195-104">可以使用其中的一个模型浏览数据，使用另一个模型创建预测。</span><span class="sxs-lookup"><span data-stu-id="5a195-104">These mining models will allow you to explore the data using one model, and to create predictions using another.</span></span>  
  
 <span data-ttu-id="5a195-105">要了解潜在客户如何按其特征分类，你将创建一个基于[Microsoft 聚类分析算法](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="5a195-105">To explore how potential customers can be categorized by their characteristics, you will create a mining model based on the [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md).</span></span> <span data-ttu-id="5a195-106">在下一课中，您将研究该算法如何查找具有类似特征的客户群。</span><span class="sxs-lookup"><span data-stu-id="5a195-106">In a later lesson, you will explore how this algorithm finds clusters of customers who share similar characteristics.</span></span> <span data-ttu-id="5a195-107">例如，您可能发现某些客户住得比较近，骑自行车上下班，并且具有类似的教育背景。</span><span class="sxs-lookup"><span data-stu-id="5a195-107">For example, you might find that certain customers tend to live close to each other, commute by bicycle, and have similar education backgrounds.</span></span> <span data-ttu-id="5a195-108">可以使用这些客户群更好地了解不同客户之间的关系，并使用此信息创建面向特定客户的营销策略。</span><span class="sxs-lookup"><span data-stu-id="5a195-108">You can use these clusters to better understand how different customers are related, and to use the information to create a marketing strategy that targets specific customers.</span></span>  
  
 <span data-ttu-id="5a195-109">若要预测潜在的客户是否有可能购买自行车，你将创建一个基于[Microsoft 决策树算法](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="5a195-109">To predict whether a potential customer is likely to buy a bicycle, you will create a mining model based on the [Microsoft Decision Trees Algorithm](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md).</span></span> <span data-ttu-id="5a195-110">该算法会通查与每位潜在客户关联的信息，并查找有助于预测客户是否会购买自行车的特征。</span><span class="sxs-lookup"><span data-stu-id="5a195-110">This algorithm looks through the information that is associated with each potential customer, and finds characteristics that are useful in predicting if they will buy a bicycle.</span></span> <span data-ttu-id="5a195-111">然后将先前的自行车购买者的特征值与潜在的新客户的特征值进行比较，确定潜在的新客户是否可能购买自行车。</span><span class="sxs-lookup"><span data-stu-id="5a195-111">It then compares the values of the characteristics of previous bike buyers against new potential customers to determine whether the new potential customers are likely to buy a bicycle.</span></span>  
  
## <a name="alter-mining-structure-statement"></a><span data-ttu-id="5a195-112">ALTER MINING STRUCTURE 语句</span><span class="sxs-lookup"><span data-stu-id="5a195-112">ALTER MINING STRUCTURE Statement</span></span>  
 <span data-ttu-id="5a195-113">若要将挖掘模型添加到挖掘结构，请使用[&#40;DMX&#41;语句的 ALTER 挖掘 structure](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016) 。</span><span class="sxs-lookup"><span data-stu-id="5a195-113">In order to add a mining model to the mining structure, you use the [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016) statement.</span></span> <span data-ttu-id="5a195-114">可以将语句中的代码分为下列几部分：</span><span class="sxs-lookup"><span data-stu-id="5a195-114">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="5a195-115">标识挖掘结构</span><span class="sxs-lookup"><span data-stu-id="5a195-115">Identifying the mining structure</span></span>  
  
-   <span data-ttu-id="5a195-116">命名挖掘模型</span><span class="sxs-lookup"><span data-stu-id="5a195-116">Naming the mining model</span></span>  
  
-   <span data-ttu-id="5a195-117">定义键列</span><span class="sxs-lookup"><span data-stu-id="5a195-117">Defining the key column</span></span>  
  
-   <span data-ttu-id="5a195-118">定义输入列和可预测列</span><span class="sxs-lookup"><span data-stu-id="5a195-118">Defining the input and predictable columns</span></span>  
  
-   <span data-ttu-id="5a195-119">标识算法和参数更改</span><span class="sxs-lookup"><span data-stu-id="5a195-119">Identifying the algorithm and parameter changes</span></span>  
  
 <span data-ttu-id="5a195-120">下面是 ALTER MINING MODEL 语句的一般示例：</span><span class="sxs-lookup"><span data-stu-id="5a195-120">The following is a generic example of the ALTER MINING MODEL statement:</span></span>  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
ADD MINING MODEL [<mining model name>]  
(  
    [<key column>],  
    <mining model columns>,  
) USING <algorithm name>( <algorithm parameters> )  
WITH FILTER (<expression>)  
```  
  
 <span data-ttu-id="5a195-121">代码的第一行标识将向其添加挖掘模型的现有挖掘结构：</span><span class="sxs-lookup"><span data-stu-id="5a195-121">The first line of the code identifies the existing mining structure to which the mining models will be added:</span></span>  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="5a195-122">代码的第二行对将要添加到挖掘结构中的挖掘模型进行命名：</span><span class="sxs-lookup"><span data-stu-id="5a195-122">The next line of the code names the mining model that will be added to the mining structure:</span></span>  
  
```  
ADD MINING MODEL [<mining model name>]  
```  
  
 <span data-ttu-id="5a195-123">有关在 DMX 中命名对象的信息，请参阅[标识符 &#40;DMX&#41;](/sql/dmx/identifiers-dmx)。</span><span class="sxs-lookup"><span data-stu-id="5a195-123">For information about naming an object in DMX, see [Identifiers &#40;DMX&#41;](/sql/dmx/identifiers-dmx).</span></span>  
  
 <span data-ttu-id="5a195-124">代码的接下来的各行定义挖掘结构中将由挖掘模型使用的各列：</span><span class="sxs-lookup"><span data-stu-id="5a195-124">The next lines of the code define columns from the mining structure that will be used by the mining model:</span></span>  
  
```  
[<key column>],  
<mining model columns>  
```  
  
 <span data-ttu-id="5a195-125">您只能使用挖掘结构中现有的各列，列表中的第一列必须是挖掘结构中的键列。</span><span class="sxs-lookup"><span data-stu-id="5a195-125">You can only use columns that already exist in the mining structure, and the first column in the list must be the key column from the mining structure.</span></span>  
  
 <span data-ttu-id="5a195-126">代码的下一行定义生成挖掘模型的挖掘算法以及可以对算法设置的算法参数：</span><span class="sxs-lookup"><span data-stu-id="5a195-126">The next line of the code defines the mining algorithm that generates the mining model and the algorithm parameters that you can set on the algorithm:</span></span>  
  
```  
) USING <algorithm name>( <algorithm parameters> )  
```  
  
 <span data-ttu-id="5a195-127">有关可以调整的算法参数的详细信息，请参阅[Microsoft 决策树算法](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)和[Microsoft 聚类分析算法](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)。</span><span class="sxs-lookup"><span data-stu-id="5a195-127">For more information about the algorithm parameters that you can adjust, see [Microsoft Decision Trees Algorithm](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md) and [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md).</span></span>  
  
 <span data-ttu-id="5a195-128">您可以使用以下语法指定将挖掘模型中的一列用于预测：</span><span class="sxs-lookup"><span data-stu-id="5a195-128">You can specify that a column in the mining model be used for prediction by using the following syntax:</span></span>  
  
```  
<mining model column> PREDICT  
```  
  
 <span data-ttu-id="5a195-129">代码的最后一行是可选的，用于定义在定型和测试模型时应用的筛选器。</span><span class="sxs-lookup"><span data-stu-id="5a195-129">The final line of the code, which is optional, defines a filter that is applied when training and testing the model.</span></span> <span data-ttu-id="5a195-130">有关如何将筛选器应用于挖掘模型的详细信息，请参阅[挖掘模型筛选器 &#40;Analysis Services 数据挖掘&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="5a195-130">For more information about how to apply filters to mining models, see [Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="5a195-131">课程任务</span><span class="sxs-lookup"><span data-stu-id="5a195-131">Lesson Tasks</span></span>  
 <span data-ttu-id="5a195-132">您将在本课中执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="5a195-132">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="5a195-133">使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 决策树算法向自行车购买者结构中添加决策树挖掘模型</span><span class="sxs-lookup"><span data-stu-id="5a195-133">Add a decision tree mining model to the Bike Buyer structure by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees algorithm</span></span>  
  
-   <span data-ttu-id="5a195-134">使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 聚类分析算法向自行车购买者结构中添加聚类分析挖掘模型</span><span class="sxs-lookup"><span data-stu-id="5a195-134">Add a clustering mining model to the Bike Buyer structure by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm</span></span>  
  
-   <span data-ttu-id="5a195-135">因为您想查看所有事例的结果，所以不向任何一个模型中添加筛选器。</span><span class="sxs-lookup"><span data-stu-id="5a195-135">Because you want to see results for all cases, you will not yet add a filter to either model.</span></span>  
  
## <a name="adding-a-decision-tree-mining-model-to-the-structure"></a><span data-ttu-id="5a195-136">向结构中添加决策树挖掘模型</span><span class="sxs-lookup"><span data-stu-id="5a195-136">Adding a Decision Tree Mining Model to the Structure</span></span>  
 <span data-ttu-id="5a195-137">第一步是基于 [!INCLUDE[msCoName](../includes/msconame-md.md)] 决策树算法添加挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="5a195-137">The first step is to add a mining model based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees algorithm.</span></span>  
  
#### <a name="to-add-a-decision-tree-mining-model"></a><span data-ttu-id="5a195-138">添加决策树挖掘模型</span><span class="sxs-lookup"><span data-stu-id="5a195-138">To add a decision tree mining model</span></span>  
  
1.  <span data-ttu-id="5a195-139">在**对象资源管理器**中，右键单击实例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 "**新建查询**"，然后单击 " **DMX** "，打开查询编辑器和一个新的空白查询。</span><span class="sxs-lookup"><span data-stu-id="5a195-139">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX** to open Query Editor and a new, blank query.</span></span>  
  
2.  <span data-ttu-id="5a195-140">将 ALTER MINING STRUCTURE 语句的一般示例复制到空白查询中。</span><span class="sxs-lookup"><span data-stu-id="5a195-140">Copy the generic example of the ALTER MINING STRUCTURE statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="5a195-141">将</span><span class="sxs-lookup"><span data-stu-id="5a195-141">Replace the following:</span></span>  
  
    ```  
    <mining structure name>   
    ```  
  
     <span data-ttu-id="5a195-142">替换为：</span><span class="sxs-lookup"><span data-stu-id="5a195-142">with:</span></span>  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  <span data-ttu-id="5a195-143">将</span><span class="sxs-lookup"><span data-stu-id="5a195-143">Replace the following:</span></span>  
  
    ```  
    <mining model name>   
    ```  
  
     <span data-ttu-id="5a195-144">替换为：</span><span class="sxs-lookup"><span data-stu-id="5a195-144">with:</span></span>  
  
    ```  
    Decision Tree  
    ```  
  
5.  <span data-ttu-id="5a195-145">将</span><span class="sxs-lookup"><span data-stu-id="5a195-145">Replace the following:</span></span>  
  
    ```  
    <mining model columns>,  
    ```  
  
     <span data-ttu-id="5a195-146">替换为：</span><span class="sxs-lookup"><span data-stu-id="5a195-146">with:</span></span>  
  
    ```  
    (  
       CustomerKey,  
       [Age],  
       [Bike Buyer] PREDICT,  
       [Commute Distance],  
       [Education],  
       [Gender],  
       [House Owner Flag],  
       [Marital Status],  
       [Number Cars Owned],  
       [Number Children At Home],  
       [Occupation],  
       [Region],  
       [Total Children],  
       [Yearly Income]  
    ```  
  
     <span data-ttu-id="5a195-147">在本例中，`[Bike Buyer]` 列被指定为 PREDICT 列。</span><span class="sxs-lookup"><span data-stu-id="5a195-147">In this case, the `[Bike Buyer]` column has been designated as the PREDICT column.</span></span>  
  
6.  <span data-ttu-id="5a195-148">将</span><span class="sxs-lookup"><span data-stu-id="5a195-148">Replace the following:</span></span>  
  
    ```  
    USING <algorithm name>( <algorithm parameters> )   
    ```  
  
     <span data-ttu-id="5a195-149">替换为：</span><span class="sxs-lookup"><span data-stu-id="5a195-149">with:</span></span>  
  
    ```  
    Using Microsoft_Decision_Trees  
    WITH DRILLTHROUGH  
    ```  
  
     <span data-ttu-id="5a195-150">通过 WITH DRILLTHROUGH 语句，您可以浏览用于生成挖掘模型的事例。</span><span class="sxs-lookup"><span data-stu-id="5a195-150">The WITH DRILLTHROUGH statement allows you to explore the cases that were used to build the mining model.</span></span>  
  
     <span data-ttu-id="5a195-151">现在，结果语句应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="5a195-151">The resulting statement should now be as follows:</span></span>  
  
    ```  
    ALTER MINING STRUCTURE [Bike Buyer]  
    ADD MINING MODEL [Decision Tree]  
    (  
       CustomerKey,  
       [Age],  
       [Bike Buyer] PREDICT,  
       [Commute Distance],  
       [Education],  
       [Gender],  
       [House Owner Flag],  
       [Marital Status],  
       [Number Cars Owned],  
       [Number Children At Home],  
       [Occupation],  
       [Region],  
       [Total Children],  
       [Yearly Income]  
    ) USING Microsoft_Decision_Trees  
    WITH DRILLTHROUGH  
    ```  
  
7.  <span data-ttu-id="5a195-152">在 "**文件**" 菜单上，单击 "**将 DMXQuery1 另存为**"。</span><span class="sxs-lookup"><span data-stu-id="5a195-152">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
8.  <span data-ttu-id="5a195-153">在 "**另存为**" 对话框中，浏览到相应的文件夹，并将该文件命名为 `DT_Model.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="5a195-153">In the **Save As** dialog box, browse to the appropriate folder, and name the file `DT_Model.dmx`.</span></span>  
  
9. <span data-ttu-id="5a195-154">在工具栏上，单击 "**执行**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="5a195-154">On the toolbar, click the **Execute** button.</span></span>  
  
## <a name="adding-a-clustering-mining-model-to-the-structure"></a><span data-ttu-id="5a195-155">向结构中添加聚类分析挖掘模型</span><span class="sxs-lookup"><span data-stu-id="5a195-155">Adding a Clustering Mining Model to the Structure</span></span>  
 <span data-ttu-id="5a195-156">现在可以基于 [!INCLUDE[msCoName](../includes/msconame-md.md)] 聚类分析算法向自行车购买者挖掘结构添加挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="5a195-156">You can now add a mining model to the Bike Buyer mining structure based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm.</span></span> <span data-ttu-id="5a195-157">由于聚类分析挖掘模型将使用挖掘结构中定义的所有列，因此，可以省略定义挖掘列，使用快捷方式向结构中添加模型。</span><span class="sxs-lookup"><span data-stu-id="5a195-157">Because the clustering mining model will use all the columns defined in the mining structure, you can use a shortcut to add the model to the structure by omitting the definition of the mining columns.</span></span>  
  
#### <a name="to-add-a-clustering-mining-model"></a><span data-ttu-id="5a195-158">添加聚类分析挖掘模型</span><span class="sxs-lookup"><span data-stu-id="5a195-158">To add a Clustering mining model</span></span>  
  
1.  <span data-ttu-id="5a195-159">在**对象资源管理器**中，右键单击实例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 "**新建查询**"，然后单击 " **DMX** "，打开 "查询编辑器" 并打开一个新的空白查询。</span><span class="sxs-lookup"><span data-stu-id="5a195-159">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX** to open Query Editor opens and a new, blank query.</span></span>  
  
2.  <span data-ttu-id="5a195-160">将 ALTER MINING STRUCTURE 语句的一般示例复制到空白查询中。</span><span class="sxs-lookup"><span data-stu-id="5a195-160">Copy the generic example of the ALTER MINING STRUCTURE statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="5a195-161">将</span><span class="sxs-lookup"><span data-stu-id="5a195-161">Replace the following:</span></span>  
  
    ```  
    <mining structure name>   
    ```  
  
     <span data-ttu-id="5a195-162">替换为：</span><span class="sxs-lookup"><span data-stu-id="5a195-162">with:</span></span>  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  <span data-ttu-id="5a195-163">将</span><span class="sxs-lookup"><span data-stu-id="5a195-163">Replace the following:</span></span>  
  
    ```  
    <mining model>   
    ```  
  
     <span data-ttu-id="5a195-164">替换为：</span><span class="sxs-lookup"><span data-stu-id="5a195-164">with:</span></span>  
  
    ```  
    Clustering Model  
    ```  
  
5.  <span data-ttu-id="5a195-165">删除以下内容：</span><span class="sxs-lookup"><span data-stu-id="5a195-165">Delete the following:</span></span>  
  
    ```  
    (  
        [<key column>],  
        <mining model columns>,  
    )  
    ```  
  
6.  <span data-ttu-id="5a195-166">将</span><span class="sxs-lookup"><span data-stu-id="5a195-166">Replace the following:</span></span>  
  
    ```  
    USING <algorithm name>( <algorithm parameters> )  
    ```  
  
     <span data-ttu-id="5a195-167">替换为：</span><span class="sxs-lookup"><span data-stu-id="5a195-167">with:</span></span>  
  
    ```  
    USING Microsoft_Clustering  
    ```  
  
     <span data-ttu-id="5a195-168">现在，完整的语句应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="5a195-168">The complete statement should now be as follows:</span></span>  
  
    ```  
    ALTER MINING STRUCTURE [Bike Buyer]  
    ADD MINING MODEL [Clustering]  
    USING Microsoft_Clustering   
    ```  
  
7.  <span data-ttu-id="5a195-169">在 "**文件**" 菜单上，单击 "**将 DMXQuery1 另存为**"。</span><span class="sxs-lookup"><span data-stu-id="5a195-169">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
8.  <span data-ttu-id="5a195-170">在 "**另存为**" 对话框中，浏览到相应的文件夹，并将该文件命名为 `Clustering_Model.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="5a195-170">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Clustering_Model.dmx`.</span></span>  
  
9. <span data-ttu-id="5a195-171">在工具栏上，单击 "**执行**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="5a195-171">On the toolbar, click the **Execute** button.</span></span>  
  
 <span data-ttu-id="5a195-172">在下一课中，您将处理模型和挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="5a195-172">In the next lesson, you will process the models and the mining structure.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="5a195-173">下一课</span><span class="sxs-lookup"><span data-stu-id="5a195-173">Next Lesson</span></span>  
 [<span data-ttu-id="5a195-174">第 3 课：处理自行车购买者挖掘结构</span><span class="sxs-lookup"><span data-stu-id="5a195-174">Lesson 3: Processing the Bike Buyer Mining Structure</span></span>](../../2014/tutorials/lesson-3-processing-the-bike-buyer-mining-structure.md)  
  
  
