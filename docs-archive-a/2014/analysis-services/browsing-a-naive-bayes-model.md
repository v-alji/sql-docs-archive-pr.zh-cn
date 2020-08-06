---
title: 浏览 Naive Bayes 模型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f9160b48-3beb-439c-9694-f084e1afa625
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3b0d18cd74e71f1ef18bffd6b0998e0b326e887a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579303"
---
# <a name="browsing-a-naive-bayes-model"></a><span data-ttu-id="9ae47-102">浏览 Naive Bayes 模型</span><span class="sxs-lookup"><span data-stu-id="9ae47-102">Browsing a Naive Bayes Model</span></span>
  <span data-ttu-id="9ae47-103">使用 "**浏览**" 打开一个简单的 Bayes 模型时，该模型将显示在具有四个不同窗格的交互式查看器中。</span><span class="sxs-lookup"><span data-stu-id="9ae47-103">When you open a Naïve Bayes model using **Browse**, the model is displayed in an interactive viewer with four different panes.</span></span> <span data-ttu-id="9ae47-104">使用该查看器，可以探索相关性，获取有关模型和基础数据的信息。</span><span class="sxs-lookup"><span data-stu-id="9ae47-104">Use the viewer to explore correlations, and get information about the model and the underlying data.</span></span>  
  
-   [<span data-ttu-id="9ae47-105">依赖关系网络</span><span class="sxs-lookup"><span data-stu-id="9ae47-105">Dependency Network</span></span>](#bkmk_DepNet)  
  
-   [<span data-ttu-id="9ae47-106">属性配置文件</span><span class="sxs-lookup"><span data-stu-id="9ae47-106">Attribute Profiles</span></span>](#bkmk_AttProf)  
  
-   [<span data-ttu-id="9ae47-107">属性特征</span><span class="sxs-lookup"><span data-stu-id="9ae47-107">Attribute Characteristics</span></span>](#bkmk_AttChar)  
  
-   [<span data-ttu-id="9ae47-108">属性对比</span><span class="sxs-lookup"><span data-stu-id="9ae47-108">Attribute Discrimination</span></span>](#bkmk_AttDisc)  
  
##  <a name="explore-the-model"></a><a name="BKMK_Tabs"></a><span data-ttu-id="9ae47-109">浏览模型</span><span class="sxs-lookup"><span data-stu-id="9ae47-109">Explore the Model</span></span>  
 <span data-ttu-id="9ae47-110">该查看器可以帮助您探索由 [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes 模型发现的输入与输出属性（输入和依赖变量）之间的交互。</span><span class="sxs-lookup"><span data-stu-id="9ae47-110">The purpose of the viewer is to help you explore the interaction between input and output attributes (inputs and dependent variables) that were discovered by the [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes model.</span></span>  
  
 <span data-ttu-id="9ae47-111">如果想要试验 Bayes 查看器，请使用 "[分类向导" &#40;&#41;Excel 数据挖掘外接程序](classify-wizard-data-mining-add-ins-for-excel.md)"向导中的" 数据挖掘 "功能区中，单击"**高级**"选项，然后将算法更改为使用" Bayes "算法</span><span class="sxs-lookup"><span data-stu-id="9ae47-111">If you want to experiment with the Naïve Bayes viewer, use the [Classify Wizard &#40;Data Mining Add-ins for Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md) wizard in the Data Mining ribbon, click the **Advanced** option, and change the algorithm to use the Naïve Bayes algorithm</span></span>  
  
 <span data-ttu-id="9ae47-112">在这些示例中，我们使用了示例工作簿中的源数据，并按从**极低**到**非常高**的顺序将列、**年收入**分组到五个收入组。</span><span class="sxs-lookup"><span data-stu-id="9ae47-112">For these examples, we used the Source data in the sample workbook, and grouped the column, **Yearly Income**, into five income groups, from **Very Low** to **Very High**.</span></span> <span data-ttu-id="9ae47-113">然后 Naïve Bayes 模型分析与每个收入类别相关的因素。</span><span class="sxs-lookup"><span data-stu-id="9ae47-113">The Naïve Bayes model then analyzed the factors correlated with each income category.</span></span>  
  
###  <a name="dependency-network"></a><a name="bkmk_DepNet"></a><span data-ttu-id="9ae47-114">依赖关系网络</span><span class="sxs-lookup"><span data-stu-id="9ae47-114">Dependency Network</span></span>  
 <span data-ttu-id="9ae47-115">您将使用的第一个窗口是**依赖关系网络**。</span><span class="sxs-lookup"><span data-stu-id="9ae47-115">The first window you'll use is the **Dependency Network**.</span></span> <span data-ttu-id="9ae47-116">它一目了然地显示哪些输入与选定结果紧密相关。</span><span class="sxs-lookup"><span data-stu-id="9ae47-116">It shows you at a glance which inputs are closely correlated to the selected outcome.</span></span>  
  
 <span data-ttu-id="9ae47-117">![Naive Bayes 查看器中的依赖关系网络](media/dm13-nb.gif "Naive Bayes 查看器中的依赖关系网络")</span><span class="sxs-lookup"><span data-stu-id="9ae47-117">![dependency network in Naive Bayes viewer](media/dm13-nb.gif "dependency network in Naive Bayes viewer")</span></span>  
  
##### <a name="explore-the-dependency-network"></a><span data-ttu-id="9ae47-118">探索依赖关系网络</span><span class="sxs-lookup"><span data-stu-id="9ae47-118">Explore the dependency network</span></span>  
  
1.  <span data-ttu-id="9ae47-119">首先，单击目标结果 "**年收入**"，它表示为图形中的一个节点。</span><span class="sxs-lookup"><span data-stu-id="9ae47-119">First, click the target outcome, **Yearly Income**, which is represented as a node in the graph.</span></span>  
  
     <span data-ttu-id="9ae47-120">目标变量周围突出显示的节点在统计上与此结果相关。</span><span class="sxs-lookup"><span data-stu-id="9ae47-120">The highlighted nodes surrounding the target variable are those that are statistically correlated with this outcome.</span></span> <span data-ttu-id="9ae47-121">使用查看器底部的图例可了解关系的性质。</span><span class="sxs-lookup"><span data-stu-id="9ae47-121">Use the legend at the bottom of the viewer to understand the nature of the relationship.</span></span>  
  
2.  <span data-ttu-id="9ae47-122">单击查看器左侧的滑块并向下拖动。</span><span class="sxs-lookup"><span data-stu-id="9ae47-122">Click the slider at the left of the viewer and drag it downward.</span></span>  
  
     <span data-ttu-id="9ae47-123">此控件根据依赖关系强度筛选独立变量。</span><span class="sxs-lookup"><span data-stu-id="9ae47-123">This control filters the independent variables, based on the strengths of the dependencies.</span></span> <span data-ttu-id="9ae47-124">向下拖动滑块时，只有最强链接保留在图形中。</span><span class="sxs-lookup"><span data-stu-id="9ae47-124">When you drag the slider down, only the strongest links remain in the graph.</span></span>  
  
3.  <span data-ttu-id="9ae47-125">对图形进行筛选后，请单击按钮 "**复制图形视图**"。</span><span class="sxs-lookup"><span data-stu-id="9ae47-125">After you have filtered the graph, click the button, **Copy Graph View**.</span></span> <span data-ttu-id="9ae47-126">然后在 Excel 中选择工作表并按 Ctrl+V。</span><span class="sxs-lookup"><span data-stu-id="9ae47-126">Then select a worksheet in Excel, and press Ctrl+V.</span></span>  
  
     <span data-ttu-id="9ae47-127">此选项可复制所选视图，包括筛选器和突出显示。</span><span class="sxs-lookup"><span data-stu-id="9ae47-127">This option copies the view that you have selected, including filters and highlighting.</span></span>  
  
 [<span data-ttu-id="9ae47-128">返回页首</span><span class="sxs-lookup"><span data-stu-id="9ae47-128">Back To Top</span></span>](#BKMK_Tabs)  
  
###  <a name="attribute-profiles"></a><a name="bkmk_AttProf"></a><span data-ttu-id="9ae47-129">属性配置文件</span><span class="sxs-lookup"><span data-stu-id="9ae47-129">Attribute Profiles</span></span>  
 <span data-ttu-id="9ae47-130">"**属性配置文件**" 窗口可让你直观地指示所有其他变量与各个结果之间的关系。</span><span class="sxs-lookup"><span data-stu-id="9ae47-130">The **Attribute Profiles** windows gives you a visual indication of how all other variables are related to the individual outcomes.</span></span>  
  
##### <a name="explore-the-profiles"></a><span data-ttu-id="9ae47-131">探索剖面图</span><span class="sxs-lookup"><span data-stu-id="9ae47-131">Explore the profiles</span></span>  
  
1.  <span data-ttu-id="9ae47-132">若要隐藏部分值以便于比较结果，请单击列标题并将其拖至另一列下。</span><span class="sxs-lookup"><span data-stu-id="9ae47-132">To hide some values so that you can more easily compare outcomes, click the column heading and drag it under another column.</span></span>  
  
     <span data-ttu-id="9ae47-133">![Naive Bayes 查看器中的属性配置文件](media/dm13-nb-attprof.gif "Naive Bayes 查看器中的属性配置文件")</span><span class="sxs-lookup"><span data-stu-id="9ae47-133">![attribute profiles in Naive Bayes viewer](media/dm13-nb-attprof.gif "attribute profiles in Naive Bayes viewer")</span></span>  
  
2.  <span data-ttu-id="9ae47-134">单击任意单元可以查看 "**挖掘图例**" 中的值的分布。</span><span class="sxs-lookup"><span data-stu-id="9ae47-134">Click in any cell to view the distribution of values in the **Mining Legend**.</span></span>  
  
     <span data-ttu-id="9ae47-135">因为将显示与不同结果关联的属性，所以很容易找到令人感兴趣的相关性，例如，收入是如何按地区分布的。</span><span class="sxs-lookup"><span data-stu-id="9ae47-135">Because the attributes associated with different outcomes are displayed visually, it is easy to spot interesting correlations, such as how incomes are distributed by region.</span></span>  
  
3.  <span data-ttu-id="9ae47-136">若要获取此视图的基础数据，请单击 "**复制到 Excel**"。</span><span class="sxs-lookup"><span data-stu-id="9ae47-136">To obtain the data underlying this view, click **Copy to Excel**.</span></span> <span data-ttu-id="9ae47-137">将在一个新工作表中生成一个表，其中显示了各个属性和结果之间的相关性。</span><span class="sxs-lookup"><span data-stu-id="9ae47-137">A table is generated in a new worksheet that shows the correlations among individual attributes and outcomes.</span></span> <span data-ttu-id="9ae47-138">在此 Excel 表中，您可以轻松地隐藏或筛选列。</span><span class="sxs-lookup"><span data-stu-id="9ae47-138">In this Excel table you can easily hide or filter columns.</span></span>  
  
 [<span data-ttu-id="9ae47-139">返回页首</span><span class="sxs-lookup"><span data-stu-id="9ae47-139">Back To Top</span></span>](#BKMK_Tabs)  
  
###  <a name="attribute-characteristics"></a><a name="bkmk_AttChar"></a><span data-ttu-id="9ae47-140">属性特征</span><span class="sxs-lookup"><span data-stu-id="9ae47-140">Attribute Characteristics</span></span>  
 <span data-ttu-id="9ae47-141">"**属性特征**" 视图可用于对特定结果变量的深度检查和相关因素。</span><span class="sxs-lookup"><span data-stu-id="9ae47-141">The **Attribute Characteristics** view is useful for in-depth examination of a particular outcome variable and the contributing factors.</span></span>  
  
 <span data-ttu-id="9ae47-142">![Naive Bayes 查看器中的属性特征](media/dm13-nb-viewer.gif "Naive Bayes 查看器中的属性特征")</span><span class="sxs-lookup"><span data-stu-id="9ae47-142">![attribute characteristics in Naive Bayes viewer](media/dm13-nb-viewer.gif "attribute characteristics in Naive Bayes viewer")</span></span>  
  
##### <a name="explore-the-attribute-characteristics"></a><span data-ttu-id="9ae47-143">探索属性特征</span><span class="sxs-lookup"><span data-stu-id="9ae47-143">Explore the attribute characteristics</span></span>  
  
1.  <span data-ttu-id="9ae47-144">单击 "**值**"，然后从**值**中选择一个项。</span><span class="sxs-lookup"><span data-stu-id="9ae47-144">Click **Value** and select an item from the **Value**.</span></span>  
  
     <span data-ttu-id="9ae47-145">在选择目标结果时，图形会更新以显示与该结果关联性最强的因素，并按重要性排序。</span><span class="sxs-lookup"><span data-stu-id="9ae47-145">As you select a target outcome, the graph updates to show the factors that are most strongly associated with the outcome, sorted by importance.</span></span>  
  
     <span data-ttu-id="9ae47-146">请注意，如果使用 "[分析关键影响因素" &#40;表分析工具 "Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md) " 选项创建模型，则可以创建具有多个可预测属性的模型。</span><span class="sxs-lookup"><span data-stu-id="9ae47-146">Note that if you create a model using the [Analyze Key Influencers &#40;Table Analysis Tools for Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md) option, you can create models that have more than one predictable attribute.</span></span> <span data-ttu-id="9ae47-147">但是，数据挖掘外接程序中的所有其他向导会限制为一个可预测属性。</span><span class="sxs-lookup"><span data-stu-id="9ae47-147">However, all other wizards in the Data Mining add-ins limit you to one predictable attribute.</span></span>  
  
2.  <span data-ttu-id="9ae47-148">单击 "**复制到 Excel** " 以在新工作表中创建一个表，其中列出了与所选目标结果相关的所有属性的分数。</span><span class="sxs-lookup"><span data-stu-id="9ae47-148">Click **Copy to Excel** to create a table, in a new worksheet, listing the scores for all attributes that are related to the selected target outcome.</span></span>  
  
 [<span data-ttu-id="9ae47-149">返回页首</span><span class="sxs-lookup"><span data-stu-id="9ae47-149">Back To Top</span></span>](#BKMK_Tabs)  
  
###  <a name="attribute-discrimination"></a><a name="bkmk_AttDisc"></a><span data-ttu-id="9ae47-150">属性对比</span><span class="sxs-lookup"><span data-stu-id="9ae47-150">Attribute Discrimination</span></span>  
 <span data-ttu-id="9ae47-151">"**属性对比**" 视图有助于比较两个结果或一个结果与所有其他结果。</span><span class="sxs-lookup"><span data-stu-id="9ae47-151">The **Attribute Discrimination** view helps compare two outcomes, or one outcome vs. all other outcomes.</span></span>  
  
 <span data-ttu-id="9ae47-152">![Naive Bayes 查看器中的属性对比](media/dm13-nb-attdisc.gif "Naive Bayes 查看器中的属性对比")</span><span class="sxs-lookup"><span data-stu-id="9ae47-152">![attribute discrimination in Naive Bayes viewer](media/dm13-nb-attdisc.gif "attribute discrimination in Naive Bayes viewer")</span></span>  
  
##### <a name="explore-attribute-discrimination"></a><span data-ttu-id="9ae47-153">探索属性对比</span><span class="sxs-lookup"><span data-stu-id="9ae47-153">Explore attribute discrimination</span></span>  
  
1.  <span data-ttu-id="9ae47-154">使用控件 "**值 1** " 和 "**值 2**" 选择要比较的结果。</span><span class="sxs-lookup"><span data-stu-id="9ae47-154">Use the controls, **Value 1** and **Value 2**, to select the outcomes that you want to compare.</span></span>  
  
     <span data-ttu-id="9ae47-155">例如，在此模型中，低收入组中有一些有趣的属性，因此我们在第一个下拉列表中选择了最低的收入组，并选择了第二个下拉列表中的**所有其他状态**。</span><span class="sxs-lookup"><span data-stu-id="9ae47-155">For example, in this model there were some interesting attributes in the low income group, so we chose the lowest income group in the first dropdown list, and chose **All other states** in the second dropdown list.</span></span>  
  
     <span data-ttu-id="9ae47-156">属性按重要程度排序（根据定型数据计算）。</span><span class="sxs-lookup"><span data-stu-id="9ae47-156">The attributes are sorted by order of importance (calculated based on the training data).</span></span> <span data-ttu-id="9ae47-157">因此，职业是与收入关联最密切的因素（至少对于此目标组来说是这样）。</span><span class="sxs-lookup"><span data-stu-id="9ae47-157">Therefore, occupation is the factor most closely correlated with income (for this target group, at least),</span></span>  
  
     <span data-ttu-id="9ae47-158">若要查看准确的数字，请单击彩色条并查看 "**挖掘图例**"。</span><span class="sxs-lookup"><span data-stu-id="9ae47-158">To see the exact figures, click the colored bar and view the **Mining Legend**.</span></span>  
  
2.  <span data-ttu-id="9ae47-159">请注意，低收入还与欧洲地区相关。</span><span class="sxs-lookup"><span data-stu-id="9ae47-159">Note that lower incomes are also correlated with the Europe region.</span></span>  
  
     <span data-ttu-id="9ae47-160">Naïve Bayes 模型不支持深化；但是，如果要调查与此结果组关联的情况，可以使用查询。</span><span class="sxs-lookup"><span data-stu-id="9ae47-160">The Naïve Bayes model does not support drilldown; however, if you wanted to investigate the cases associated with this outcome group, you could use a query.</span></span> <span data-ttu-id="9ae47-161">有关此类模型的查询的信息，请参阅[Naive Bayes Model Query 示例](data-mining/naive-bayes-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="9ae47-161">For information about queries on this type of model, see [Naive Bayes Model Query Examples](data-mining/naive-bayes-model-query-examples.md).</span></span>  
  
 [<span data-ttu-id="9ae47-162">返回页首</span><span class="sxs-lookup"><span data-stu-id="9ae47-162">Back To Top</span></span>](#BKMK_Tabs)  
  
## <a name="see-also"></a><span data-ttu-id="9ae47-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9ae47-163">See Also</span></span>  
 [<span data-ttu-id="9ae47-164">在 Excel 中浏览模型 &#40;SQL Server 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="9ae47-164">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
