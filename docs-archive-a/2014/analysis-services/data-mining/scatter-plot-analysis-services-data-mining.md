---
title: 散点图 (Analysis Services 数据挖掘) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- charts [Analysis Services]
- mining models [Analysis Services], validating
- scatter charts
- regression algorithms [Analysis Services]
ms.assetid: 166812ec-fd1c-47c8-88db-d5041142be91
author: minewiskan
ms.author: owend
ms.openlocfilehash: b584be18618e6b046a27e40d0707609c3e02c45c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591648"
---
# <a name="scatter-plot-analysis-services---data-mining"></a><span data-ttu-id="b1c3c-102">散点图（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="b1c3c-102">Scatter Plot (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="b1c3c-103">“散点图” \*\* 以图形方式对照显示数据中的实际值与模型预测的值。</span><span class="sxs-lookup"><span data-stu-id="b1c3c-103">A *scatter plot* graphs the actual values in your data against the values predicted by the model.</span></span> <span data-ttu-id="b1c3c-104">其沿 X 轴显示实际值，沿 Y 轴显示预测值。</span><span class="sxs-lookup"><span data-stu-id="b1c3c-104">The scatter plot displays the actual values along the X-axis, and displays the predicted values along the Y-axis.</span></span> <span data-ttu-id="b1c3c-105">该图还显示一条显示完美预测的线，在这条线上预测值和实际值完全匹配。</span><span class="sxs-lookup"><span data-stu-id="b1c3c-105">It also displays a line that illustrates the perfect prediction, where the predicted value exactly matches the actual value.</span></span> <span data-ttu-id="b1c3c-106">某个点与该条理想 45 度角线的距离指示进行的预测的准确程度。</span><span class="sxs-lookup"><span data-stu-id="b1c3c-106">The distance of a point from this ideal 45-degree angle line indicates how well or how poorly the prediction performed.</span></span>

## <a name="understanding-the-scatter-plot"></a><span data-ttu-id="b1c3c-107">了解散点图</span><span class="sxs-lookup"><span data-stu-id="b1c3c-107">Understanding the Scatter Plot</span></span>
 <span data-ttu-id="b1c3c-108">考虑下面这个模型：公司的市场部根据其在促销电子邮件中发送的链接的点击数来预测日销售额。</span><span class="sxs-lookup"><span data-stu-id="b1c3c-108">Consider a model in which the marketing department predicts daily sales based on the number of clicks on a link sent in a promotional e-mail.</span></span> <span data-ttu-id="b1c3c-109">由于点击数和销售额均为连续数值，因此，可以以图形方式将点击数显示为独立变量，将销售额显示为依赖变量。</span><span class="sxs-lookup"><span data-stu-id="b1c3c-109">Because both the number of clicks and the amount of sales are continuous numeric values, you can graph the number of clicks as the independent variable and the sales as the dependent variable.</span></span> <span data-ttu-id="b1c3c-110">这样，图中的直线显示预期线性关系，而散布在该直线周围的点显示实际数据偏离预期值的程度。</span><span class="sxs-lookup"><span data-stu-id="b1c3c-110">When you do so, the straight line shows the expected linear relationship, and the points scattered around that line show how the actual data diverges from the expected.</span></span> <span data-ttu-id="b1c3c-111">一目了然，该分析指出一组结果与某个特定输入相关联的紧密程度，以及所生成的模型与理想模型之间有多大差异</span><span class="sxs-lookup"><span data-stu-id="b1c3c-111">This analysis tells you at a glance how closely a set of results is correlated with a particular input, and how much variation there is from the ideal model</span></span>

## <a name="interpreting-the-results"></a><span data-ttu-id="b1c3c-112">解释结果</span><span class="sxs-lookup"><span data-stu-id="b1c3c-112">Interpreting the Results</span></span>
 <span data-ttu-id="b1c3c-113">下面的关系图显示散点图的一个示例，该图是为刚刚说明的应用场景而创建的。</span><span class="sxs-lookup"><span data-stu-id="b1c3c-113">The following diagram shows an example of a scatter plot, created for the scenario just described.</span></span>

 <span data-ttu-id="b1c3c-114">![线性回归的散点图示例](../media/scatterplot-callctr.gif "线性回归的散点图示例")</span><span class="sxs-lookup"><span data-stu-id="b1c3c-114">![example of a scatter plot for linear regression](../media/scatterplot-callctr.gif "example of a scatter plot for linear regression")</span></span>

 <span data-ttu-id="b1c3c-115">将鼠标悬停在散布在该直线周围的任一点上方即可在工具提示中查看预测值和实际值。</span><span class="sxs-lookup"><span data-stu-id="b1c3c-115">You can pause the mouse on any point scattered around the line to view the predicted and actual values in a tooltip.</span></span> <span data-ttu-id="b1c3c-116">散点图没有 **“挖掘图例”** ，但该图表本身包含一个显示与该模型关联的分数的图例。</span><span class="sxs-lookup"><span data-stu-id="b1c3c-116">There is no **Mining Legend** for a scatter plot; however, the chart itself contains a legend that displays the score associated with the model.</span></span> <span data-ttu-id="b1c3c-117">有关解释分数的详细信息，请参阅[线性回归模型的挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="b1c3c-117">For more information about interpreting the score, see [Mining Model Content for Linear Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md).</span></span>

 <span data-ttu-id="b1c3c-118">可以将该图表的可视表示复制到剪贴板，但无法复制基础数据或公式。</span><span class="sxs-lookup"><span data-stu-id="b1c3c-118">You can copy the visual representation of the chart to the Clipboard, but not the underlying data or the formula.</span></span> <span data-ttu-id="b1c3c-119">如果希望查看对应于此条线的回归公式，则可以对该模型创建内容查询。</span><span class="sxs-lookup"><span data-stu-id="b1c3c-119">If you want to view the regression formula for the line, you can create a content query against the model.</span></span> <span data-ttu-id="b1c3c-120">有关详细信息，请参阅 [线性回归模型查询示例](linear-regression-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="b1c3c-120">For more information, see [Linear Regression Model Query Examples](linear-regression-model-query-examples.md).</span></span>

## <a name="restrictions-on-scatter-plots"></a><span data-ttu-id="b1c3c-121">针对散点图的限制</span><span class="sxs-lookup"><span data-stu-id="b1c3c-121">Restrictions on Scatter Plots</span></span>
 <span data-ttu-id="b1c3c-122">如果在 **“输入选择”** 选项卡上选择的模型包含连续可预测属性，则只能创建散点图。</span><span class="sxs-lookup"><span data-stu-id="b1c3c-122">A scatter plot can only be created if the model that you choose on the **Input Selection** tab contains a continuous predictable attribute.</span></span> <span data-ttu-id="b1c3c-123">不必进行其他选择；基于模型和属性类型在 **“提升图”** 选项卡中自动显示散点图图表类型。</span><span class="sxs-lookup"><span data-stu-id="b1c3c-123">You do not have to make any additional selections; the scatter plot chart type is automatically displayed in the **Lift Chart** tab based on model and attribute type.</span></span>

 <span data-ttu-id="b1c3c-124">尽管时序模型预测连续数值，但是您不能使用散点图度量时序模型的准确性。</span><span class="sxs-lookup"><span data-stu-id="b1c3c-124">Although time series models predict continuous numbers, you cannot measure the accuracy of a time series model by using a scatter plot.</span></span> <span data-ttu-id="b1c3c-125">可以使用其他方法，例如保留一部分历史记录数据。</span><span class="sxs-lookup"><span data-stu-id="b1c3c-125">There are other methods that you can use, such as reserving a portion of the historical data.</span></span> <span data-ttu-id="b1c3c-126">有关详细信息，请参阅[时序模型查询示例](time-series-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="b1c3c-126">For more information, see [Time Series Model Query Examples](time-series-model-query-examples.md).</span></span>

## <a name="related-content"></a><span data-ttu-id="b1c3c-127">相关内容</span><span class="sxs-lookup"><span data-stu-id="b1c3c-127">Related Content</span></span>
 <span data-ttu-id="b1c3c-128">下列主题包含有关如何生成和使用散点图以及相关准确性图表的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b1c3c-128">The following topics contain more information about how you can build and use scatter plots and related accuracy charts.</span></span>

|<span data-ttu-id="b1c3c-129">主题</span><span class="sxs-lookup"><span data-stu-id="b1c3c-129">Topics</span></span>|<span data-ttu-id="b1c3c-130">链接</span><span class="sxs-lookup"><span data-stu-id="b1c3c-130">Links</span></span>|
|------------|-----------|
|<span data-ttu-id="b1c3c-131">提供如何创建目标邮递模型的提升图的演练。</span><span class="sxs-lookup"><span data-stu-id="b1c3c-131">Provides a walkthrough of how to create a lift chart for the Targeted Mailing model.</span></span>|[<span data-ttu-id="b1c3c-132">数据挖掘基础教程</span><span class="sxs-lookup"><span data-stu-id="b1c3c-132">Basic Data Mining Tutorial</span></span>](../../tutorials/basic-data-mining-tutorial.md)<br /><br /> [<span data-ttu-id="b1c3c-133">测试提升图的准确性（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="b1c3c-133">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)|
|<span data-ttu-id="b1c3c-134">说明相关的图表类型。</span><span class="sxs-lookup"><span data-stu-id="b1c3c-134">Explains related chart types.</span></span>|[<span data-ttu-id="b1c3c-135">提升图（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="b1c3c-135">Lift Chart &#40;Analysis Services - Data Mining&#41;</span></span>](lift-chart-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="b1c3c-136">利润图（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="b1c3c-136">Profit Chart &#40;Analysis Services - Data Mining&#41;</span></span>](profit-chart-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="b1c3c-137">分类矩阵（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="b1c3c-137">Classification Matrix &#40;Analysis Services - Data Mining&#41;</span></span>](classification-matrix-analysis-services-data-mining.md)|
|<span data-ttu-id="b1c3c-138">说明如何将交叉验证用于挖掘模型和挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="b1c3c-138">Describes uses of cross-validation for mining models and mining structures.</span></span>|[<span data-ttu-id="b1c3c-139">交叉验证（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="b1c3c-139">Cross-Validation &#40;Analysis Services - Data Mining&#41;</span></span>](cross-validation-analysis-services-data-mining.md)|
|<span data-ttu-id="b1c3c-140">说明用于创建提升图和其他准确性图表的步骤。</span><span class="sxs-lookup"><span data-stu-id="b1c3c-140">Describes steps for creating lift charts and other accuracy charts.</span></span>|[<span data-ttu-id="b1c3c-141">测试和验证任务和操作指南（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="b1c3c-141">Testing and Validation Tasks and How-tos &#40;Data Mining&#41;</span></span>](testing-and-validation-tasks-and-how-tos-data-mining.md)|

## <a name="see-also"></a><span data-ttu-id="b1c3c-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b1c3c-142">See Also</span></span>
 [<span data-ttu-id="b1c3c-143">测试和验证（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="b1c3c-143">Testing and Validation &#40;Data Mining&#41;</span></span>](testing-and-validation-data-mining.md)


