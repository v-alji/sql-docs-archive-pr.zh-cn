---
title: 利润图 (Analysis Services 数据挖掘) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- accuracy, charting
- revenue, estimating
- benefits, estimating
- charts [Analysis Services]
- profit charts [Analysis Services]
ms.assetid: 760ee051-6fd8-48e3-8d2e-82db3ab45e45
author: minewiskan
ms.author: owend
ms.openlocfilehash: a38a1d5062f53de4be9129c2305d8d3c84593f9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690872"
---
# <a name="profit-chart-analysis-services---data-mining"></a><span data-ttu-id="559b1-102">利润图（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="559b1-102">Profit Chart (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="559b1-103">利润图显示与使用挖掘模型相关联的估计利润。</span><span class="sxs-lookup"><span data-stu-id="559b1-103">A profit chart displays the estimated profitability associated with using a mining model.</span></span> <span data-ttu-id="559b1-104">例如，假设您的模型预测公司应在业务方案中联系哪些客户。</span><span class="sxs-lookup"><span data-stu-id="559b1-104">For example, let's assume your model predicts which customers a company should contact in a business scenario.</span></span> <span data-ttu-id="559b1-105">在该情形下，您要向利润图添加与目标邮递活动的成本有关的信息。</span><span class="sxs-lookup"><span data-stu-id="559b1-105">In that case, you would add to the profit chart information about the cost of conducting the targeted mailing campaign.</span></span> <span data-ttu-id="559b1-106">然后，在已完成的利润图中，您可以看到与随机联系客户相比，正确定位客户情况下的估计的利润。</span><span class="sxs-lookup"><span data-stu-id="559b1-106">Then, in the completed chart, you can see the estimated profit if customers are correctly targeted, as compared to randomly contacting customers.</span></span>  
  
## <a name="build-a-profit-chart"></a><span data-ttu-id="559b1-107">构建利润图</span><span class="sxs-lookup"><span data-stu-id="559b1-107">Build a Profit Chart</span></span>  
 <span data-ttu-id="559b1-108">利润图类似于提升图。</span><span class="sxs-lookup"><span data-stu-id="559b1-108">A profit chart is similar to a lift chart.</span></span> <span data-ttu-id="559b1-109">您从创建一个提升图开始，然后加入成本和利润信息。</span><span class="sxs-lookup"><span data-stu-id="559b1-109">You start by creating a lift chart, and then add in the cost and profit information.</span></span>  
  
 <span data-ttu-id="559b1-110">若要构建利润图，必须具有现有模型。</span><span class="sxs-lookup"><span data-stu-id="559b1-110">To build a profit chart, you must have an existing model.</span></span>  
  
 <span data-ttu-id="559b1-111">对于此示例，我们使用了 Targeted Mailing 决策树模型。</span><span class="sxs-lookup"><span data-stu-id="559b1-111">For this example, we used the Targeted Mailing decision tree model.</span></span> <span data-ttu-id="559b1-112">该模型标识可能要购买自行车的客户。</span><span class="sxs-lookup"><span data-stu-id="559b1-112">The model identifies customers who are likely to buy a bike.</span></span> <span data-ttu-id="559b1-113">您可以应用 **“利润图”** 来确定您的目标用户有多少，以便将您的利润最大化。</span><span class="sxs-lookup"><span data-stu-id="559b1-113">You can apply the **Profit Chart** to determine how many of your customers to target to maximize your profit.</span></span>  
  
 <span data-ttu-id="559b1-114">如果没有示例模型，则可以使用[数据挖掘基础教程](../../tutorials/basic-data-mining-tutorial.md)来创建它。</span><span class="sxs-lookup"><span data-stu-id="559b1-114">If you don't have the sample model, you can create it using the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span>  
  
1.  <span data-ttu-id="559b1-115">打开挖掘准确性图表生成器。</span><span class="sxs-lookup"><span data-stu-id="559b1-115">Open the mining accuracy chart builder.</span></span>  
  
    -   <span data-ttu-id="559b1-116">在 SQL Server Management Studio 中，右键单击该模型，然后选择“查看提升图”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="559b1-116">In SQL Server Management Studio, right-click the model, and select **View Lift Chart**.</span></span>  
  
    -   <span data-ttu-id="559b1-117">在 SQL Server Data Tools 中，打开在其中创建了该模型的项目，然后单击 **“挖掘准确性图表”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="559b1-117">In SQL Server Data Tools, open the project in which you created the model, and click the **Mining Accuracy Chart** tab.</span></span>  
  
2.  <span data-ttu-id="559b1-118">在 **“输入选择”** 选项卡中，选择该模型并且选择可预测属性值。</span><span class="sxs-lookup"><span data-stu-id="559b1-118">In **the Input Selection** tab, select the model and choose the predictable attribute value.</span></span>  
  
     <span data-ttu-id="559b1-119">对于此特殊情形，您只对精确预测一个值的盈利能力感兴趣：[Bike Buyer] =1。</span><span class="sxs-lookup"><span data-stu-id="559b1-119">For this particular scenario, you are interested only in the profitability of accurately predicting one value: [Bike Buyer] =1.</span></span>  
  
     <span data-ttu-id="559b1-120">但是，还有您同样对正确预测假值感兴趣的其他情形。</span><span class="sxs-lookup"><span data-stu-id="559b1-120">However, there are other scenarios in which you are equally interested in predicting false values correctly.</span></span> <span data-ttu-id="559b1-121">例如，有关医疗诊断测试的假正的成本可能很高，因此在预测的盈利能力中需要考虑，假负的成本也同样需要考虑。</span><span class="sxs-lookup"><span data-stu-id="559b1-121">For example, the cost of a false positive on a medical diagnostic test can be significant and needs to be factored into the profitability of the prediction, as does the cost of false negatives.</span></span> <span data-ttu-id="559b1-122">在此类情形下，您要衡量所有结果。</span><span class="sxs-lookup"><span data-stu-id="559b1-122">In such scenarios, you would measure all outcomes.</span></span>  
  
3.  <span data-ttu-id="559b1-123">选择用于测试的数据集。</span><span class="sxs-lookup"><span data-stu-id="559b1-123">Select a data set for testing.</span></span> <span data-ttu-id="559b1-124">对于此示例，选择测试数据集。</span><span class="sxs-lookup"><span data-stu-id="559b1-124">For this example, select the testing data set.</span></span>  
  
4.  <span data-ttu-id="559b1-125">现在单击 **“提升图”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="559b1-125">Now click the **Lift Chart** tab.</span></span>  
  
     <span data-ttu-id="559b1-126">将自动生成一个提升图。</span><span class="sxs-lookup"><span data-stu-id="559b1-126">A lift chart is automatically generated.</span></span>  
  
5.  <span data-ttu-id="559b1-127">若要将该提升图更改为某一利润图，请从 **“图表类型”** 列表中选择 **“利润图”** 。</span><span class="sxs-lookup"><span data-stu-id="559b1-127">To change this to a profit chart, select **Profit Chart** from the **Chart type** list.</span></span>  
  
6.  <span data-ttu-id="559b1-128">选择利润图作为图表类型后，将自动打开 **“利润图设置”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="559b1-128">As soon as you choose profit chart as the chart type, the **Profit Chart Setting** dialog box automatically opens.</span></span>  
  
     <span data-ttu-id="559b1-129">此对话框帮助您指定与目标邮递活动关联的成本和收益。</span><span class="sxs-lookup"><span data-stu-id="559b1-129">This dialog box helps you specify the costs and benefits associated with a targeted mailing campaign.</span></span> <span data-ttu-id="559b1-130">对于这些示例中所示的图表，我们使用了以下值：</span><span class="sxs-lookup"><span data-stu-id="559b1-130">For the chart shown in these examples, we used the following values:</span></span>  
  
    |<span data-ttu-id="559b1-131">设置</span><span class="sxs-lookup"><span data-stu-id="559b1-131">Setting</span></span>|<span data-ttu-id="559b1-132">值</span><span class="sxs-lookup"><span data-stu-id="559b1-132">Value</span></span>|<span data-ttu-id="559b1-133">注释</span><span class="sxs-lookup"><span data-stu-id="559b1-133">Comments</span></span>|  
    |-------------|-----------|--------------|  
    |<span data-ttu-id="559b1-134">**总数**</span><span class="sxs-lookup"><span data-stu-id="559b1-134">**Population**</span></span>|<span data-ttu-id="559b1-135">20,000</span><span class="sxs-lookup"><span data-stu-id="559b1-135">20,000</span></span>|<span data-ttu-id="559b1-136">设置总目标人数的值</span><span class="sxs-lookup"><span data-stu-id="559b1-136">Set the value for the total target population</span></span><br /><br /> <span data-ttu-id="559b1-137">您的数据库可能包含很多客户，但是为了节省邮递开支，您可能选择仅对最有可能回复的前 20,000 个客户发邮件。</span><span class="sxs-lookup"><span data-stu-id="559b1-137">Your database might contain many customers, but to save on mailing expenses you might choose to target only the 20,000 customers who are most likely to respond.</span></span> <span data-ttu-id="559b1-138">您可以通过运行预测查询并且由预测模型按概率输出排序，获得此列表。</span><span class="sxs-lookup"><span data-stu-id="559b1-138">You can get this list by running a prediction query and sorting by the probability output by the predictive model.</span></span>|  
    |<span data-ttu-id="559b1-139">**固定成本**</span><span class="sxs-lookup"><span data-stu-id="559b1-139">**Fixed cost**</span></span>|<span data-ttu-id="559b1-140">500</span><span class="sxs-lookup"><span data-stu-id="559b1-140">500</span></span>|<span data-ttu-id="559b1-141">输入为 20,000 人设置目标邮递活动的一次性成本。</span><span class="sxs-lookup"><span data-stu-id="559b1-141">Enter the one-time cost of setting up a targeted mailing campaign for 20,000 people.</span></span> <span data-ttu-id="559b1-142">这可能包括印刷成本或者设置电子邮件活动的成本。</span><span class="sxs-lookup"><span data-stu-id="559b1-142">This might include printing, or the cost of setting up an e-mail campaign.</span></span>|  
    |<span data-ttu-id="559b1-143">**单项成本**</span><span class="sxs-lookup"><span data-stu-id="559b1-143">**Individual cost**</span></span>|<span data-ttu-id="559b1-144">3</span><span class="sxs-lookup"><span data-stu-id="559b1-144">3</span></span>|<span data-ttu-id="559b1-145">输入目标邮递活动的单位成本。</span><span class="sxs-lookup"><span data-stu-id="559b1-145">Enter the per-unit cost for the targeted mailing campaign.</span></span><br /><br /> <span data-ttu-id="559b1-146">该金额将乘以一个等于或小于 20,000 的数，具体数字取决于模型预测的客户中有多少个是合适的潜在客户。</span><span class="sxs-lookup"><span data-stu-id="559b1-146">This amount will be multiplied by a number equal to or less than 20000, depending on how many customers the model predicts are good prospects.</span></span>|  
    |<span data-ttu-id="559b1-147">**单项收入**</span><span class="sxs-lookup"><span data-stu-id="559b1-147">**Revenue per individual**</span></span>|<span data-ttu-id="559b1-148">400</span><span class="sxs-lookup"><span data-stu-id="559b1-148">400</span></span>|<span data-ttu-id="559b1-149">输入一个值，该值表示可以从成功结果获得利润或收入的金额。</span><span class="sxs-lookup"><span data-stu-id="559b1-149">Enter a value that represents the amount of profit or income that can be expected from a successful result.</span></span> <span data-ttu-id="559b1-150">在这种情况下，我们假设邮寄目录会导致购买附件或自行车平均 $400。</span><span class="sxs-lookup"><span data-stu-id="559b1-150">In this case, we'll assume that mailing a catalog results in purchase of accessories or bikes averaging $400.</span></span><br /><br /> <span data-ttu-id="559b1-151">该金额将用于预计与高概率事例关联的总利润。</span><span class="sxs-lookup"><span data-stu-id="559b1-151">This amount will be used to project the total profit associated with high probability cases.</span></span>|  
  
7.  <span data-ttu-id="559b1-152">在您设置了所需参数后，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="559b1-152">After you have set the required parameters, click **OK**.</span></span>  
  
8.  <span data-ttu-id="559b1-153">该图表将更新以显示利润曲线。</span><span class="sxs-lookup"><span data-stu-id="559b1-153">The chart updates to show the profit curve.</span></span>  
  
## <a name="understanding-the-profit-chart"></a><span data-ttu-id="559b1-154">了解利润图</span><span class="sxs-lookup"><span data-stu-id="559b1-154">Understanding the Profit Chart</span></span>  
 <span data-ttu-id="559b1-155">下图显示基于这些参数的图表。</span><span class="sxs-lookup"><span data-stu-id="559b1-155">The following diagram shows the chart that was based on these parameters.</span></span> <span data-ttu-id="559b1-156">图表的 Y 轴表示利润，而 X 轴表示目标邮寄活动联系的客户的百分比。</span><span class="sxs-lookup"><span data-stu-id="559b1-156">The Y-axis of the chart represents the profit, while the X-axis represents the percentage of the customers who were contacted by the targeted mailing campaign.</span></span>  
  
 <span data-ttu-id="559b1-157">如下所示，可以使用利润图比较多个模型，只要它们都预测同一离散属性。</span><span class="sxs-lookup"><span data-stu-id="559b1-157">As shown here, you can use a profit chart to compare multiple models, as long as they all predict the same discrete attribute.</span></span>  
  
 <span data-ttu-id="559b1-158">![与三种模型对比的利润图](../media/dm14-profitchartupdated.gif "与三种模型对比的利润图")</span><span class="sxs-lookup"><span data-stu-id="559b1-158">![a profit chart comparing three models](../media/dm14-profitchartupdated.gif "a profit chart comparing three models")</span></span>  
  
 <span data-ttu-id="559b1-159">请注意图表中的灰色竖线。</span><span class="sxs-lookup"><span data-stu-id="559b1-159">Notice the gray vertical line in the chart.</span></span> <span data-ttu-id="559b1-160">在您单击并拖动该竖线时，工具提示将显示在该点的曲线下包括的目标人口的百分比。</span><span class="sxs-lookup"><span data-stu-id="559b1-160">As you click and drag the line, the ToolTip display the percentage of the target population that is included under the curve at that point.</span></span>  
  
 <span data-ttu-id="559b1-161">在您移动该线时， **“挖掘图例”** 还会更新，以便显示百分比值、利润得分和与灰色竖线上的总人口百分比关联的预测概率。</span><span class="sxs-lookup"><span data-stu-id="559b1-161">The **Mining Legend** is also updated as you drag the line, to display the percentage value, a profit score, and the predict probability that is associated with the population percentage at the vertical gray line.</span></span>  
  
 <span data-ttu-id="559b1-162">例如，如果您在使用该模型确定要将您的促销材料发送给谁，可以基于预测概率确定针对 25% 的人口。但是，在图表的利润曲线下的区域是最大的，介于 40% 到 70% 之间，指示通过邮寄给更多的人，可以令您的回报最大化，即使只有较小的整体百分比响应。</span><span class="sxs-lookup"><span data-stu-id="559b1-162">For example, if you were using this model to decide who to send your promotional material to, you might decide to target 25% of the population, based on the predict probabilities, However, the area under the profit curve of the chart is greatest between 40 and 70 percent, indicating that by mailing to more people, you can maximize your return, even if a smaller overall percentage responds.</span></span>  
  
## <a name="saving-charts"></a><span data-ttu-id="559b1-163">保存图表</span><span class="sxs-lookup"><span data-stu-id="559b1-163">Saving Charts</span></span>  
 <span data-ttu-id="559b1-164">在您创建准确性图表或利润图时，在服务器上将不会创建任何对象。</span><span class="sxs-lookup"><span data-stu-id="559b1-164">When you create an accuracy chart or profit chart, no objects are created on the server.</span></span> <span data-ttu-id="559b1-165">而是对现有模型执行查询，并且结果将呈现在查看器中。</span><span class="sxs-lookup"><span data-stu-id="559b1-165">Instead, queries are executed against an existing model and the results are rendered in the viewer.</span></span> <span data-ttu-id="559b1-166">如果您需要保存结果，则必须将图表或结果保存到 Excel 或其他文件中。</span><span class="sxs-lookup"><span data-stu-id="559b1-166">If you need to save the results, you must copy either the chart or the results to Excel or another file.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="559b1-167">相关内容</span><span class="sxs-lookup"><span data-stu-id="559b1-167">Related Content</span></span>  
 <span data-ttu-id="559b1-168">下列主题包含有关如何生成和使用准确性图表的详细信息。</span><span class="sxs-lookup"><span data-stu-id="559b1-168">The following topics contain more information about how you can build and use accuracy charts.</span></span>  
  
|<span data-ttu-id="559b1-169">主题</span><span class="sxs-lookup"><span data-stu-id="559b1-169">Topics</span></span>|<span data-ttu-id="559b1-170">链接</span><span class="sxs-lookup"><span data-stu-id="559b1-170">Links</span></span>|  
|------------|-----------|  
|<span data-ttu-id="559b1-171">提供如何创建目标邮递模型的提升图的演练。</span><span class="sxs-lookup"><span data-stu-id="559b1-171">Provides a walkthrough of how to create a lift chart for the Targeted Mailing model.</span></span>|[<span data-ttu-id="559b1-172">数据挖掘基础教程</span><span class="sxs-lookup"><span data-stu-id="559b1-172">Basic Data Mining Tutorial</span></span>](../../tutorials/basic-data-mining-tutorial.md)<br /><br /> [<span data-ttu-id="559b1-173">测试提升图的准确性（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="559b1-173">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)|  
|<span data-ttu-id="559b1-174">说明相关的图表类型。</span><span class="sxs-lookup"><span data-stu-id="559b1-174">Explains related chart types.</span></span>|[<span data-ttu-id="559b1-175">提升图（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="559b1-175">Lift Chart &#40;Analysis Services - Data Mining&#41;</span></span>](lift-chart-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="559b1-176">分类矩阵（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="559b1-176">Classification Matrix &#40;Analysis Services - Data Mining&#41;</span></span>](classification-matrix-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="559b1-177">散点图（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="559b1-177">Scatter Plot &#40;Analysis Services - Data Mining&#41;</span></span>](scatter-plot-analysis-services-data-mining.md)|  
|<span data-ttu-id="559b1-178">说明挖掘模型和挖掘结构的交叉验证。</span><span class="sxs-lookup"><span data-stu-id="559b1-178">Describes cross-validation for mining models and mining structures.</span></span>|[<span data-ttu-id="559b1-179">交叉验证（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="559b1-179">Cross-Validation &#40;Analysis Services - Data Mining&#41;</span></span>](cross-validation-analysis-services-data-mining.md)|  
|<span data-ttu-id="559b1-180">说明用于创建提升图和其他准确性图表的步骤。</span><span class="sxs-lookup"><span data-stu-id="559b1-180">Describes steps for creating lift charts and other accuracy charts.</span></span>|[<span data-ttu-id="559b1-181">测试和验证任务和操作指南（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="559b1-181">Testing and Validation Tasks and How-tos &#40;Data Mining&#41;</span></span>](testing-and-validation-tasks-and-how-tos-data-mining.md)|  
  
## <a name="see-also"></a><span data-ttu-id="559b1-182">另请参阅</span><span class="sxs-lookup"><span data-stu-id="559b1-182">See Also</span></span>  
 <span data-ttu-id="559b1-183">[测试和验证 &#40;数据挖掘&#41;](testing-and-validation-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="559b1-183">[Testing and Validation &#40;Data Mining&#41;](testing-and-validation-data-mining.md) </span></span>  
 [<span data-ttu-id="559b1-184">测试提升图的准确性（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="559b1-184">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
  
