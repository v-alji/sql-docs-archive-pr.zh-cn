---
title: 利润图 (SQL Server 数据挖掘外接程序) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- accuracy chart
- profit chart
- mining models, charting
- mining models, testing
ms.assetid: 5c902543-4da9-4db3-99d5-4ce04c43d7ef
author: minewiskan
ms.author: owend
ms.openlocfilehash: 030e511047b816543c12c81bdab307e599bbc5d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586996"
---
# <a name="profit-chart-sql-server-data-mining-add-ins"></a><span data-ttu-id="a5ec2-102">利润图（SQL Server 数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="a5ec2-102">Profit Chart (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="a5ec2-103">![“数据挖掘”功能区中的“利润图”按钮](media/dmc-profitchart.gif "“数据挖掘”功能区中的“利润图”按钮")</span><span class="sxs-lookup"><span data-stu-id="a5ec2-103">![Profit Chart button in Data Mining ribbon](media/dmc-profitchart.gif "Profit Chart button in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="a5ec2-104">利润图显示与使用挖掘模型相关联的预计利润增长，以确定公司应在业务方案中联系的客户。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-104">A profit chart displays the estimated profit increase that is associated with using a mining model to determine which customers a company should contact in a business scenario.</span></span> <span data-ttu-id="a5ec2-105">图表的 Y 轴表示利润，而 X 轴表示公司所联系总体的百分比。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-105">The Y-axis of the chart represents the profit, while the X-axis represents the percentage of the population that the company contacted.</span></span> <span data-ttu-id="a5ec2-106">典型的利润图显示利润增长到一个最高点，利润在达到该点后将随所联系总体的增大而减少。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-106">A typical profit chart shows an increase in profits up to a point, after which profits decrease as more of the population is contacted.</span></span>  
  
## <a name="configuring-the-profit-chart"></a><span data-ttu-id="a5ec2-107">配置利润图</span><span class="sxs-lookup"><span data-stu-id="a5ec2-107">Configuring the Profit Chart</span></span>  
 <span data-ttu-id="a5ec2-108">准确性图表仅对预测正确与否的概率进行评估，但利润图则同时包含有关根据预测采取措施的结果的现实认知。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-108">Whereas the accuracy chart assesses only the probability that predictions are right or wrong, the profit chart incorporates real-world knowledge about the consequences of taking action on a prediction.</span></span> <span data-ttu-id="a5ec2-109">为此，运行向导时您要考虑指定下列因素：</span><span class="sxs-lookup"><span data-stu-id="a5ec2-109">This is achieved by taking into account the following factors, which you specify when you run the wizard:</span></span>  
  
-   <span data-ttu-id="a5ec2-110">**总数**</span><span class="sxs-lookup"><span data-stu-id="a5ec2-110">**Population**</span></span>  
  
     <span data-ttu-id="a5ec2-111">数据集中用于创建提升图的事例数。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-111">The number of cases in the dataset that is being used to create the lift chart.</span></span> <span data-ttu-id="a5ec2-112">例如，潜在客户数。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-112">For example, the number of potential customers.</span></span>  
  
-   <span data-ttu-id="a5ec2-113">**固定成本**</span><span class="sxs-lookup"><span data-stu-id="a5ec2-113">**Fixed Cost**</span></span>  
  
     <span data-ttu-id="a5ec2-114">与业务问题关联的固定成本。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-114">The fixed cost that is associated with the business problem.</span></span> <span data-ttu-id="a5ec2-115">如果此参数用于目标邮件解决方案，则该成本不依赖于所拨打的销售电话数或所发送的促销邮件数等变量。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-115">If this were for a targeted mailing solution, the cost would not depend on variables such as the number of telephone calls made or the number of promotional mailings sent.</span></span>  
  
-   <span data-ttu-id="a5ec2-116">**单项成本**</span><span class="sxs-lookup"><span data-stu-id="a5ec2-116">**Individual Cost**</span></span>  
  
     <span data-ttu-id="a5ec2-117">除固定成本之外的成本，可以与每个客户联系相关联。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-117">Costs that are in addition to the fixed cost, that can be associated with each customer contact.</span></span> <span data-ttu-id="a5ec2-118">例如，促销邮件或销售电话。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-118">For example, promotional mailings or telephone calls.</span></span>  
  
-   <span data-ttu-id="a5ec2-119">**每个人收入**</span><span class="sxs-lookup"><span data-stu-id="a5ec2-119">**Revenue Per Individual**</span></span>  
  
     <span data-ttu-id="a5ec2-120">与每个成功销售相关联的收入金额。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-120">The amount of revenue that is associated with each successful sale.</span></span>  
  
## <a name="using-the-profit-chart-wizard"></a><span data-ttu-id="a5ec2-121">使用利润图向导</span><span class="sxs-lookup"><span data-stu-id="a5ec2-121">Using the Profit Chart Wizard</span></span>  
 <span data-ttu-id="a5ec2-122">若要创建利润图，必须参考现有数据挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-122">To create a profit chart, you must reference an existing data mining model.</span></span> <span data-ttu-id="a5ec2-123">您可以通过单击 "**管理模型**" 或 "**浏览**" 来浏览模型，查找与数据匹配的模型，以查看有关已使用的算法和挖掘模型中的列的详细信息。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-123">You can browse models to find a model that matches your data by clicking **Manage Models** or **Browse** to see details about the algorithm that was used and the columns in the mining model.</span></span>  
  
 <span data-ttu-id="a5ec2-124">有关详细信息，请参阅[在 Excel 中浏览模型 &#40;SQL Server 数据挖掘外接程序&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)和[管理模型 &#40;SQL Server 数据挖掘外接程序&#41;](manage-models-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-124">For more information, see [Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md) and [Manage Models &#40;SQL Server Data Mining Add-ins&#41;](manage-models-sql-server-data-mining-add-ins.md).</span></span>  
  
#### <a name="to-create-a-profit-chart"></a><span data-ttu-id="a5ec2-125">创建利润图</span><span class="sxs-lookup"><span data-stu-id="a5ec2-125">To create a profit chart</span></span>  
  
1.  <span data-ttu-id="a5ec2-126">选择一个现有模型。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-126">Select an existing model.</span></span>  
  
2.  <span data-ttu-id="a5ec2-127">指定要预测的列，如果需要，还请指定目标值。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-127">Specify the column that you want to predict, and a target value, if appropriate.</span></span>  
  
3.  <span data-ttu-id="a5ec2-128">选择源数据，这意味着数据将传递给模型来创建预测。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-128">Select the source data, which means the data you will pass through the model in order to create a prediction.</span></span> <span data-ttu-id="a5ec2-129">此数据应不同于创建模型所用的数据。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-129">This should not be the same data that you used to create the model.</span></span>  
  
4.  <span data-ttu-id="a5ec2-130">将新（源）日期中的列映射到数据挖掘模型中所用的列。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-130">Map the columns in the new (source) date to the columns used in the data mining model.</span></span> <span data-ttu-id="a5ec2-131">如果列名称类似，向导将自动映射它们。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-131">If the column names are similar, the wizard will automatically map them.</span></span>  
  
5.  <span data-ttu-id="a5ec2-132">输入向导所需的开销信息：固定成本、单项成本、总体以及预期收入。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-132">Enter the cost information required by the wizard: the fixed cost, individual cost, the population, and the revenue expected.</span></span>  
  
6.  <span data-ttu-id="a5ec2-133">或者，您可以输入一系列渐变的成本 (单击 "浏览\*\* ( ... ) \*\* ") 。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-133">Optionally, you can enter a graduated series of costs (click the browse **(...)** button).</span></span> <span data-ttu-id="a5ec2-134">例如，增加发送的邮件数量时，发送一封邮件的成本可能会降低，因此，您可以根据邮件数量输入不同成本，向导将自动调整每个样本大小的成本。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-134">For example, a mailing might become cheaper as you increase the number of items that are sent, so you can enter a different cost depending on the number of items, and the wizard will automatically adjust the costs for each sample size.</span></span>  
  
7.  <span data-ttu-id="a5ec2-135">向导将创建包含针对该模型的成本收益分析的图表。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-135">The wizard creates a chart that includes the cost-benefit analysis for the model.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="a5ec2-136">要求</span><span class="sxs-lookup"><span data-stu-id="a5ec2-136">Requirements</span></span>  
 <span data-ttu-id="a5ec2-137">如果预测的是离散数值，则必须选择要预测的精确目标值。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-137">If you are predicting a discrete numeric value, you must select the exact target value to predict.</span></span>  
  
## <a name="understanding-the-profit-chart"></a><span data-ttu-id="a5ec2-138">了解利润图</span><span class="sxs-lookup"><span data-stu-id="a5ec2-138">Understanding the Profit Chart</span></span>  
 <span data-ttu-id="a5ec2-139">利润图包含一条灰色竖线，单击该图表中的某一位置可以移动该竖线。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-139">The profit chart contains a gray vertical line, which you can move by clicking a location in the chart.</span></span> <span data-ttu-id="a5ec2-140">"**挖掘图例**" 显示与图表上的灰色线条位置相关联的分数、总体正确和预测概率。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-140">The **Mining Legend** displays a score, the population correct, and the predict probability that are associated with the location of the gray line on the chart.</span></span> <span data-ttu-id="a5ec2-141">如果通过使用灰线选择了图表中的最大利润点，可以使用预测概率值确定联系客户的概率阈值。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-141">If you select the maximum point of profits in the chart by using the gray line, you can use the predict probability value to determine a probability threshold for contacting a customer.</span></span>  
  
 <span data-ttu-id="a5ec2-142">例如，如果利润曲线的峰值位于总体的 55% 处，并且相关联的预测概率为 20%，这表明，若要获取最大利润，应只联系其答复概率被预测为 20% 或更高的客户。</span><span class="sxs-lookup"><span data-stu-id="a5ec2-142">For example, if the peak of the profit curve is at 55 percent of the population and the associated predict probability is 20 percent, this indicates that to achieve maximum profits you should only contact those customers whose response is predicted with a 20 percent or greater probability.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5ec2-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a5ec2-143">See Also</span></span>  
 [<span data-ttu-id="a5ec2-144">验证模型和使用模型进行预测 &#40;Excel 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="a5ec2-144">Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;</span></span>](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
  
