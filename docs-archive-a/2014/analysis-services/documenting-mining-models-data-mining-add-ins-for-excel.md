---
title: 记录挖掘模型 (Excel 数据挖掘外接程序) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- documenting models
- mining structures, managing
- mining models, managing
- model properties
ms.assetid: 0a663e11-e40c-4708-ad18-fabb6c976fa4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 00d84f7ff1dc27d19d497dd11315d3efde603f60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589949"
---
# <a name="documenting-mining-models-data-mining-add-ins-for-excel"></a><span data-ttu-id="5ca44-102">记录挖掘模型（Excel 数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="5ca44-102">Documenting Mining Models (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="5ca44-103">![“数据挖掘”功能区中的“文档模型”按钮](media/dmc-docmodel.gif "“数据挖掘”功能区中的“文档模型”按钮")</span><span class="sxs-lookup"><span data-stu-id="5ca44-103">![Document Model button, Data Mining ribbon](media/dmc-docmodel.gif "Document Model button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="5ca44-104">**文档模型**向导将创建一个报表，该报表提供有关已创建的挖掘模型的有用信息。</span><span class="sxs-lookup"><span data-stu-id="5ca44-104">The **Document Model** wizard creates a report that provides useful information about the mining models that you have created.</span></span> <span data-ttu-id="5ca44-105">通过记录创建的模型，不但可以跟踪用于生成模型的数据的源，获取有关模型处理时间的其他信息，还可以跟踪影响模型结果的参数更改。</span><span class="sxs-lookup"><span data-stu-id="5ca44-105">By documenting the models that you create, you can track the source of the data used to generate a model, get additional information about when the model was processed, and track parameter changes that affect the results of the model.</span></span>  
  
## <a name="using-the-document-model-wizard"></a><span data-ttu-id="5ca44-106">使用文档模型向导</span><span class="sxs-lookup"><span data-stu-id="5ca44-106">Using the Document Model Wizard</span></span>  
  
1.  <span data-ttu-id="5ca44-107">单击 "**数据挖掘**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="5ca44-107">Click the **Data Mining** tab.</span></span>  
  
2.  <span data-ttu-id="5ca44-108">在 "**模型用法**" 组中，单击 "**文档模型**"。</span><span class="sxs-lookup"><span data-stu-id="5ca44-108">In the **Model Usage** group, click **Document Model**.</span></span>  
  
3.  <span data-ttu-id="5ca44-109">在 "**选择模型**" 对话框中，选择要报告的模型，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="5ca44-109">In the **Select Model** dialog box, select the model on which to report, and then click **Next**.</span></span> <span data-ttu-id="5ca44-110">您必须为要记录的每个模型单独运行**文档模型**向导。</span><span class="sxs-lookup"><span data-stu-id="5ca44-110">You must run the **Document Model** wizard separately for each model that you want to document.</span></span>  
  
4.  <span data-ttu-id="5ca44-111">在 "**选择文档详细信息**" 对话框中，选择以下两个选项之一：**完整信息**或**摘要信息**。</span><span class="sxs-lookup"><span data-stu-id="5ca44-111">In the **Select documentation details** dialog box, choose one of two options: **Complete information** or **Summary information**.</span></span>  
  
5.  <span data-ttu-id="5ca44-112">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="5ca44-112">Click **Finish**.</span></span>  
  
6.  <span data-ttu-id="5ca44-113">向导将自动创建一个新的工作表，其中包含名为**Model 文档**的指定报表</span><span class="sxs-lookup"><span data-stu-id="5ca44-113">The wizard automatically creates a new worksheet that contains the specified report, titled **Model Documentation**,</span></span>  
  
## <a name="understanding-the-report"></a><span data-ttu-id="5ca44-114">了解报表</span><span class="sxs-lookup"><span data-stu-id="5ca44-114">Understanding the Report</span></span>  
 <span data-ttu-id="5ca44-115">创建记录数据挖掘模型的报表时，可以创建包含基本信息（模型的名称和说明）的摘要，或者也可以创建包含基础结构详细信息和挖掘模型高级信息的完整报表。</span><span class="sxs-lookup"><span data-stu-id="5ca44-115">When you create a report that documents a data mining model, you can create a summary,which contains basic information containing the name and description of the model, or a complete report, which contains details about the underlying structure and advanced information about the mining model.</span></span>  
  
 <span data-ttu-id="5ca44-116">会根据创建模型所使用的算法，提供有不同类型的信息。</span><span class="sxs-lookup"><span data-stu-id="5ca44-116">Depending on the algorithm that was used to create the model, different types of information is provided.</span></span> <span data-ttu-id="5ca44-117">例如，在关联模型中，您可能对了解生成的项集数和规则数更感兴趣。</span><span class="sxs-lookup"><span data-stu-id="5ca44-117">For example, in an association model, you are more interested in knowing the number of itemsets and rules that were generated.</span></span> <span data-ttu-id="5ca44-118">在聚类分析模型中，可能会对分类数更感兴趣。</span><span class="sxs-lookup"><span data-stu-id="5ca44-118">For a clustering model, the number of clusters is more interesting.</span></span>  
  
 <span data-ttu-id="5ca44-119">下表列出了各选项以及报表中提供的每个选项的信息。</span><span class="sxs-lookup"><span data-stu-id="5ca44-119">The following table lists the options and the information that is provided in the report for each option.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5ca44-120">默认情况下，该报表中的列设置为特定大小。</span><span class="sxs-lookup"><span data-stu-id="5ca44-120">The columns in the report are set to a particular size by default.</span></span> <span data-ttu-id="5ca44-121">因此，如果列名或值很长，则在 Excel 中有可能不可见或显示为 ###。</span><span class="sxs-lookup"><span data-stu-id="5ca44-121">Therefore, if any columns names or values are very long, they might not be visible, or might appear as ### in Excel.</span></span> <span data-ttu-id="5ca44-122">您可以调整行的大小使值可见。</span><span class="sxs-lookup"><span data-stu-id="5ca44-122">To make the values visible, you can resize the row.</span></span> <span data-ttu-id="5ca44-123">如果选择了单元格，则可以单击并拖动编辑栏右端的双箭头，以显示完整的值或字符串。</span><span class="sxs-lookup"><span data-stu-id="5ca44-123">If the cell is selected, you can click and drag the double arrows at the right end of the formula bar to show the complete value or string.</span></span>  
  
### <a name="summary-report"></a><span data-ttu-id="5ca44-124">摘要报表</span><span class="sxs-lookup"><span data-stu-id="5ca44-124">Summary Report</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="5ca44-125">Metadata</span><span class="sxs-lookup"><span data-stu-id="5ca44-125">**Metadata**</span></span>|<span data-ttu-id="5ca44-126">模型名称</span><span class="sxs-lookup"><span data-stu-id="5ca44-126">Model name</span></span><br /><br /> <span data-ttu-id="5ca44-127">模型说明</span><span class="sxs-lookup"><span data-stu-id="5ca44-127">Model description</span></span><br /><br /> <span data-ttu-id="5ca44-128">算法名称</span><span class="sxs-lookup"><span data-stu-id="5ca44-128">Algorithm name</span></span><br /><br /> <span data-ttu-id="5ca44-129">上次处理日期</span><span class="sxs-lookup"><span data-stu-id="5ca44-129">Date last processed</span></span>||  
|<span data-ttu-id="5ca44-130">**模型结果**</span><span class="sxs-lookup"><span data-stu-id="5ca44-130">**Model results**</span></span>|<span data-ttu-id="5ca44-131">关联</span><span class="sxs-lookup"><span data-stu-id="5ca44-131">Association</span></span>|<span data-ttu-id="5ca44-132">项集计数</span><span class="sxs-lookup"><span data-stu-id="5ca44-132">Count of itemsets</span></span><br /><br /> <span data-ttu-id="5ca44-133">规则计数</span><span class="sxs-lookup"><span data-stu-id="5ca44-133">Count of rules</span></span>|  
||<span data-ttu-id="5ca44-134">群集</span><span class="sxs-lookup"><span data-stu-id="5ca44-134">Clustering</span></span>|<span data-ttu-id="5ca44-135">分类计数</span><span class="sxs-lookup"><span data-stu-id="5ca44-135">Count of clusters</span></span><br /><br /> <span data-ttu-id="5ca44-136">对每个分类的支持</span><span class="sxs-lookup"><span data-stu-id="5ca44-136">Support for each cluster</span></span>|  
||<span data-ttu-id="5ca44-137">决策树</span><span class="sxs-lookup"><span data-stu-id="5ca44-137">Decision tree</span></span>|<span data-ttu-id="5ca44-138">树数</span><span class="sxs-lookup"><span data-stu-id="5ca44-138">Number of trees</span></span><br /><br /> <span data-ttu-id="5ca44-139">每个树中的节点数</span><span class="sxs-lookup"><span data-stu-id="5ca44-139">Number of nodes in each tree</span></span>|  
||<span data-ttu-id="5ca44-140">线性回归</span><span class="sxs-lookup"><span data-stu-id="5ca44-140">Linear regression</span></span>|<span data-ttu-id="5ca44-141">树数（始终为 1）</span><span class="sxs-lookup"><span data-stu-id="5ca44-141">Number of trees (always 1)</span></span><br /><br /> <span data-ttu-id="5ca44-142">节点数（始终为 1）</span><span class="sxs-lookup"><span data-stu-id="5ca44-142">Number of nodes (always 1)</span></span>|  
||<span data-ttu-id="5ca44-143">Naïve Bayes</span><span class="sxs-lookup"><span data-stu-id="5ca44-143">Naïve Bayes</span></span>|<span data-ttu-id="5ca44-144">重要属性</span><span class="sxs-lookup"><span data-stu-id="5ca44-144">Important attributes</span></span>|  
||<span data-ttu-id="5ca44-145">神经网络</span><span class="sxs-lookup"><span data-stu-id="5ca44-145">Neural network</span></span>|<span data-ttu-id="5ca44-146">输入节点数</span><span class="sxs-lookup"><span data-stu-id="5ca44-146">Number of input nodes</span></span><br /><br /> <span data-ttu-id="5ca44-147">输出节点数</span><span class="sxs-lookup"><span data-stu-id="5ca44-147">Number of output nodes</span></span><br /><br /> <span data-ttu-id="5ca44-148">隐藏节点数</span><span class="sxs-lookup"><span data-stu-id="5ca44-148">Number of hidden nodes</span></span>|  
||<span data-ttu-id="5ca44-149">顺序分析和聚类分析</span><span class="sxs-lookup"><span data-stu-id="5ca44-149">Sequence clustering</span></span>|<span data-ttu-id="5ca44-150">分类数</span><span class="sxs-lookup"><span data-stu-id="5ca44-150">Number of clusters</span></span>|  
  
### <a name="complete-report"></a><span data-ttu-id="5ca44-151">完整报表</span><span class="sxs-lookup"><span data-stu-id="5ca44-151">Complete Report</span></span>  
 <span data-ttu-id="5ca44-152">完整报表包含摘要报表中的所有内容，此外还有模型中使用的数据列的详细信息以及分析的结果：</span><span class="sxs-lookup"><span data-stu-id="5ca44-152">The complete report contains everything that is in the summary report, plus  detailed information about the columns of data used in the model and the results of analysis:</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="5ca44-153">Metadata</span><span class="sxs-lookup"><span data-stu-id="5ca44-153">**Metadata**</span></span>|<span data-ttu-id="5ca44-154">模型元数据</span><span class="sxs-lookup"><span data-stu-id="5ca44-154">Model metadata</span></span>|<span data-ttu-id="5ca44-155">算法参数和值</span><span class="sxs-lookup"><span data-stu-id="5ca44-155">Algorithm parameters and values</span></span>|  
||<span data-ttu-id="5ca44-156">列元数据</span><span class="sxs-lookup"><span data-stu-id="5ca44-156">Column metadata</span></span>|<span data-ttu-id="5ca44-157">列名称</span><span class="sxs-lookup"><span data-stu-id="5ca44-157">Column name</span></span><br /><br /> <span data-ttu-id="5ca44-158">使用情况</span><span class="sxs-lookup"><span data-stu-id="5ca44-158">Usage</span></span><br /><br /> <span data-ttu-id="5ca44-159">数据类型</span><span class="sxs-lookup"><span data-stu-id="5ca44-159">Data type</span></span><br /><br /> <span data-ttu-id="5ca44-160">内容类型</span><span class="sxs-lookup"><span data-stu-id="5ca44-160">Content type</span></span><br /><br /> <span data-ttu-id="5ca44-161">值（离散值的列表或值的范围）</span><span class="sxs-lookup"><span data-stu-id="5ca44-161">Values (list of discrete values, or range of values)</span></span>|  
|<span data-ttu-id="5ca44-162">**模型统计信息**</span><span class="sxs-lookup"><span data-stu-id="5ca44-162">**Model statistics**</span></span>|<span data-ttu-id="5ca44-163">连续列</span><span class="sxs-lookup"><span data-stu-id="5ca44-163">Continuous columns</span></span>|<span data-ttu-id="5ca44-164">平均值</span><span class="sxs-lookup"><span data-stu-id="5ca44-164">Mean value</span></span><br /><br /> <span data-ttu-id="5ca44-165">最小值</span><span class="sxs-lookup"><span data-stu-id="5ca44-165">Minimum value</span></span><br /><br /> <span data-ttu-id="5ca44-166">最大值</span><span class="sxs-lookup"><span data-stu-id="5ca44-166">Maximum value</span></span><br /><br /> <span data-ttu-id="5ca44-167">均方根误差</span><span class="sxs-lookup"><span data-stu-id="5ca44-167">Root mean square error</span></span><br /><br /> <span data-ttu-id="5ca44-168">平均绝对误差</span><span class="sxs-lookup"><span data-stu-id="5ca44-168">Mean absolute error</span></span><br /><br /> <span data-ttu-id="5ca44-169">对数评分</span><span class="sxs-lookup"><span data-stu-id="5ca44-169">Log score</span></span><br /><br /> <span data-ttu-id="5ca44-170">回归公式（仅用于线性回归模型）</span><span class="sxs-lookup"><span data-stu-id="5ca44-170">Regression formula (for linear regression models only)</span></span>|  
||<span data-ttu-id="5ca44-171">离散列</span><span class="sxs-lookup"><span data-stu-id="5ca44-171">Discrete columns</span></span>|<span data-ttu-id="5ca44-172">传递计数</span><span class="sxs-lookup"><span data-stu-id="5ca44-172">Count of passing</span></span><br /><br /> <span data-ttu-id="5ca44-173">失败计数</span><span class="sxs-lookup"><span data-stu-id="5ca44-173">Count of failing</span></span><br /><br /> <span data-ttu-id="5ca44-174">对数评分</span><span class="sxs-lookup"><span data-stu-id="5ca44-174">Log score</span></span><br /><br /> <span data-ttu-id="5ca44-175">提升</span><span class="sxs-lookup"><span data-stu-id="5ca44-175">Lift</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="5ca44-176">您可以记录 SQL Server Analysis Services 支持的任何模型类型。</span><span class="sxs-lookup"><span data-stu-id="5ca44-176">You can document any model type that is supported by SQL Server Analysis Services.</span></span> <span data-ttu-id="5ca44-177">因此，该表列出了使用表分析工具或数据挖掘客户端中的向导无法创建的某些模型类型。</span><span class="sxs-lookup"><span data-stu-id="5ca44-177">Therefore, the table lists some model types that cannot be created by using the Table Analysis Tools or by using the wizards in the Data Mining Client.</span></span> <span data-ttu-id="5ca44-178">不过，您可以使用**高级数据挖掘查询编辑器**创建所有模型类型。</span><span class="sxs-lookup"><span data-stu-id="5ca44-178">However, you can create all model types by using the **Advanced Data Mining Query Editor**.</span></span> <span data-ttu-id="5ca44-179">有关详细信息，请参阅[查询 &#40;SQL Server 数据挖掘外接程序&#41;](query-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="5ca44-179">For more information, see [Query &#40;SQL Server Data Mining Add-ins&#41;](query-sql-server-data-mining-add-ins.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ca44-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5ca44-180">See Also</span></span>  
 [<span data-ttu-id="5ca44-181">&#40;Excel 数据挖掘外接程序部署和缩放挖掘模型&#41;</span><span class="sxs-lookup"><span data-stu-id="5ca44-181">Deploying and Scaling Mining Models &#40;Data Mining Add-ins for Excel&#41;</span></span>](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
