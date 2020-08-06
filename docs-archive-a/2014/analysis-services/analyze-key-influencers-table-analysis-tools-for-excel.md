---
title: 分析) Excel (表分析工具的关键影响因素 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- key influencers
- factor analysis
ms.assetid: 54d7b4ce-7b79-407a-985c-aa655ad19280
author: minewiskan
ms.author: owend
ms.openlocfilehash: f60eb5144059b0976d52eec2329f27553132146c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579377"
---
# <a name="analyze-key-influencers-table-analysis-tools-for-excel"></a><span data-ttu-id="27d75-102">分析关键影响因素（Excel 表分析工具）</span><span class="sxs-lookup"><span data-stu-id="27d75-102">Analyze Key Influencers (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="27d75-103">![功能区中的“分析关键影响因素”按钮](media/tat-aki.gif "功能区中的“分析关键影响因素”按钮")</span><span class="sxs-lookup"><span data-stu-id="27d75-103">![Analyze Key Influencers button in ribbon](media/tat-aki.gif "Analyze Key Influencers button in ribbon")</span></span>  
  
 <span data-ttu-id="27d75-104">使用 "**分析关键影响因素**" 工具，可以选择包含目标结果的列，而算法将确定哪些因素对结果的影响最强。</span><span class="sxs-lookup"><span data-stu-id="27d75-104">With the **Analyze Key Influencers** tool, you choose a column that contains a target outcome, and the algorithm determines which factors had the strongest influence on the outcome.</span></span>  
  
 <span data-ttu-id="27d75-105">该工具可创建若干新数据表，这些表将报告与每个结果相关联的因素，并以图形方式显示它们之间存在关系的概率。</span><span class="sxs-lookup"><span data-stu-id="27d75-105">The tool creates new data tables that report the factors associated with each outcome and graphically displays the probability of the relationship.</span></span> <span data-ttu-id="27d75-106">可以基于不同因素和结果对这些表进行筛选，以更深入地研究结果。</span><span class="sxs-lookup"><span data-stu-id="27d75-106">You can filter the tables by different factors and outcomes to explore the results in more depth.</span></span>  
  
 <span data-ttu-id="27d75-107">还可选择可能得到的一对结果并对它们进行比较。</span><span class="sxs-lookup"><span data-stu-id="27d75-107">You can also select a pair of possible outcomes and compare them.</span></span> <span data-ttu-id="27d75-108">例如，您可以比较不同的使用者组来确定可能影响决策的因素。</span><span class="sxs-lookup"><span data-stu-id="27d75-108">For example, you might compare different groups of consumers to determine possible decision-making factors.</span></span>  
  
## <a name="using-the-analyze-key-influencers-tool"></a><span data-ttu-id="27d75-109">使用“分析关键影响因素”工具</span><span class="sxs-lookup"><span data-stu-id="27d75-109">Using the Analyze Key Influencers Tool</span></span>  
  
1.  <span data-ttu-id="27d75-110">打开 Excel 数据表。</span><span class="sxs-lookup"><span data-stu-id="27d75-110">Open an Excel data table.</span></span>  
  
2.  <span data-ttu-id="27d75-111">在 "**表工具**" 中的 "**分析**" 功能区上，单击 "**分析关键影响因素"。**</span><span class="sxs-lookup"><span data-stu-id="27d75-111">In **Table Tools**, on the **Analyze** ribbon, click **Analyze Key Influencers.**</span></span>  
  
3.  <span data-ttu-id="27d75-112">选择单个列作为分析目标。</span><span class="sxs-lookup"><span data-stu-id="27d75-112">Select the single column that is the target of analysis.</span></span>  
  
4.  <span data-ttu-id="27d75-113">（可选）单击 "**选择要用于分析的列**"。</span><span class="sxs-lookup"><span data-stu-id="27d75-113">Optionally, click **Choose columns to be used for analysis**.</span></span> <span data-ttu-id="27d75-114">在 "**高级列选择**" 对话框中，选择最有可能包含相关数据的列。</span><span class="sxs-lookup"><span data-stu-id="27d75-114">In the **Advanced Columns Selection** dialog box, choose the columns that are most likely to contain relevant data.</span></span> <span data-ttu-id="27d75-115">若要改进性能和精确性，请取消选择诸如 ID 或名称等对模式分析不重要的列。</span><span class="sxs-lookup"><span data-stu-id="27d75-115">To improve performance and accuracy, deselect columns such as ID or name that are unimportant for pattern analysis.</span></span> <span data-ttu-id="27d75-116">单击 **"确定"** 关闭 "**高级列选择**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="27d75-116">Click **OK** to close the **Advanced Columns Selection** dialog box.</span></span>  
  
5.  <span data-ttu-id="27d75-117">单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="27d75-117">Click **Run**.</span></span>  
  
     <span data-ttu-id="27d75-118">"**分析关键影响因素**" 工具可对数据进行分析，以确定最佳设置，并自动设置所有参数。</span><span class="sxs-lookup"><span data-stu-id="27d75-118">The **Analyze Key Influencers** tool conducts an analysis of the data to determine the optimum settings, and sets all parameters automatically.</span></span>  
  
6.  <span data-ttu-id="27d75-119">如果未检测到模式，该向导会创建一个新工作表，该表含有对问题的说明。</span><span class="sxs-lookup"><span data-stu-id="27d75-119">If no patterns were detected, the wizard creates a new worksheet that contains a description of the problem.</span></span>  
  
7.  <span data-ttu-id="27d75-120">如果检测到模式，则向导将在新的工作表中创建一个报表以显示这些模式。</span><span class="sxs-lookup"><span data-stu-id="27d75-120">If patterns are detected, the wizard creates a report on a new worksheet that shows the patterns.</span></span> <span data-ttu-id="27d75-121">报表为**的 \<column> 关键影响因素**。</span><span class="sxs-lookup"><span data-stu-id="27d75-121">The report is named **Key Influencers for \<column>**.</span></span> <span data-ttu-id="27d75-122">可以按照以下步骤所述自定义该报表。</span><span class="sxs-lookup"><span data-stu-id="27d75-122">You can customize the report as described in the following procedure.</span></span>  
  
#### <a name="create-a-custom-report"></a><span data-ttu-id="27d75-123">创建自定义报表</span><span class="sxs-lookup"><span data-stu-id="27d75-123">Create a custom report</span></span>  
  
1.  <span data-ttu-id="27d75-124">在 "**基于关键影响因素的对比**" 对话框中，从 "**值 1** " 和 "**值 2** " 下拉列表中选择要进行比较的两个值。</span><span class="sxs-lookup"><span data-stu-id="27d75-124">In the **Discrimination based on key influencers** dialog box, choose the two values that you want to compare by selecting them from the **Value 1** and **Value 2** dropdown lists.</span></span> <span data-ttu-id="27d75-125">例如，您可以将购买者与非购买者进行比较。</span><span class="sxs-lookup"><span data-stu-id="27d75-125">For example, you might compare buyers to non-buyers.</span></span>  
  
2.  <span data-ttu-id="27d75-126">单击 "**添加报表**"。</span><span class="sxs-lookup"><span data-stu-id="27d75-126">Click **Add Report**.</span></span>  
  
     <span data-ttu-id="27d75-127">该向导将创建新工作表，并为每对关键因素比较添加一个表。</span><span class="sxs-lookup"><span data-stu-id="27d75-127">The wizard creates a new worksheet and adds a table for each pair of key factor comparisons.</span></span>  
  
3.  <span data-ttu-id="27d75-128">完成比较后，请单击 "**关闭**"。</span><span class="sxs-lookup"><span data-stu-id="27d75-128">When you are done making comparisons, click **Close**.</span></span>  
  
## <a name="understanding-the-key-influencers-report"></a><span data-ttu-id="27d75-129">了解关键影响因素报表</span><span class="sxs-lookup"><span data-stu-id="27d75-129">Understanding the Key Influencers Report</span></span>  
 <span data-ttu-id="27d75-130">创建数据模型后，"**分析关键影响因素**" 工具会创建帮助您探索和比较关键影响因素的报表。</span><span class="sxs-lookup"><span data-stu-id="27d75-130">After the data model has been created, the **Analyze Key Influencers** tool creates reports that help you explore and compare key influencers.</span></span>  
  
-   <span data-ttu-id="27d75-131">左侧的报表是默认情况下生成的一个报表。</span><span class="sxs-lookup"><span data-stu-id="27d75-131">The report on the left side is the one generated by default.</span></span> <span data-ttu-id="27d75-132">其中显示对于结果列（因变量）影响最大的预测因子。</span><span class="sxs-lookup"><span data-stu-id="27d75-132">It shows the strongest predictors of the outcome column (the dependent variable).</span></span>  
  
-   <span data-ttu-id="27d75-133">右侧的报表是可选报表，可通过比较两个特定的结果值创建该报表。</span><span class="sxs-lookup"><span data-stu-id="27d75-133">The report on the right side is optional, which you can create by comparing two specific outcome values.</span></span> <span data-ttu-id="27d75-134">此报表将比较购买者与非购买者。</span><span class="sxs-lookup"><span data-stu-id="27d75-134">This report compares buyers and non-buyers.</span></span>  
  
-   <span data-ttu-id="27d75-135">注意，对于所创建的每个报表都会添加一个新的工作表。</span><span class="sxs-lookup"><span data-stu-id="27d75-135">Note that a new worksheet is added for each report that you create.</span></span> <span data-ttu-id="27d75-136">在创建表后，可移动这些表；我们将这些表并行放在一起进行比较。</span><span class="sxs-lookup"><span data-stu-id="27d75-136">You can move the tables after they are created; we placed them side by side for comparison.</span></span>  
  
 <span data-ttu-id="27d75-137">![DM13](media/dm13-tat-aki-report.gif "DM13")</span><span class="sxs-lookup"><span data-stu-id="27d75-137">![DM13](media/dm13-tat-aki-report.gif "DM13")</span></span>  
  
 <span data-ttu-id="27d75-138">**相对影响**</span><span class="sxs-lookup"><span data-stu-id="27d75-138">**Relative Impact**</span></span>  
 <span data-ttu-id="27d75-139">第一个报表中的阴影条指示此属性与结果的关联强度。</span><span class="sxs-lookup"><span data-stu-id="27d75-139">The shaded bar in the first report indicates the strength of the association of this attribute with the outcome.</span></span>  
  
 <span data-ttu-id="27d75-140">色条长度指示该因素影响结果的概率；因此，阴影条越长，关联性越强。</span><span class="sxs-lookup"><span data-stu-id="27d75-140">The length of the bar indicates the probability that the factor contributes to the outcome; therefore, the longer the shaded bar, the stronger the association.</span></span>  
  
 <span data-ttu-id="27d75-141">**倾向于**</span><span class="sxs-lookup"><span data-stu-id="27d75-141">**Favors**</span></span>  
 <span data-ttu-id="27d75-142">第二个报表中，在两列中列出所比较的目标值，其中按置信度降序列出相关因素。</span><span class="sxs-lookup"><span data-stu-id="27d75-142">In the second report, the target values that you compare are listed in two columns, with the related factors listed in order of descending confidence.</span></span>  
  
-   <span data-ttu-id="27d75-143">**蓝**条显示了导致结果的属性 "No" (= 未) 购买。</span><span class="sxs-lookup"><span data-stu-id="27d75-143">The **blue** bar shows attributes contributing to the outcome, "No" (=did not purchase).</span></span>  
  
-   <span data-ttu-id="27d75-144">**红色**条显示了导致结果的属性 "是" (= 购买自行车) 。</span><span class="sxs-lookup"><span data-stu-id="27d75-144">The **red** bar shows attributes contributing to the outcome, "Yes" (=purchased a bike).</span></span>  
  
 <span data-ttu-id="27d75-145">阴影条的颜色是任意的，</span><span class="sxs-lookup"><span data-stu-id="27d75-145">The colors in the shading bar are arbitrary.</span></span> <span data-ttu-id="27d75-146">在 Excel 中设置表设计选项即可更改这些颜色。</span><span class="sxs-lookup"><span data-stu-id="27d75-146">You can change these colors by setting the options for table design in Excel.</span></span>  
  
 <span data-ttu-id="27d75-147">在比较两个值的报表中，第二个报表根据对目标值的影响程度为关键影响因素排名。</span><span class="sxs-lookup"><span data-stu-id="27d75-147">In a report that contrasts two values, the second report ranks the key influencers by the amount of impact on the target values.</span></span>  
  
 <span data-ttu-id="27d75-148">由于所有图表都基于 Excel 表，因此可进行筛选和排序，重点关注特定的因素或结果。</span><span class="sxs-lookup"><span data-stu-id="27d75-148">Because all the charts are based on Excel tables, you can filter and sort to focus on specific factors or outcomes.</span></span>  
  
## <a name="more-about-the-analyze-key-influencers-tool"></a><span data-ttu-id="27d75-149">有关“分析关键影响因素”工具的详细信息</span><span class="sxs-lookup"><span data-stu-id="27d75-149">More About the Analyze Key Influencers Tool</span></span>  
 <span data-ttu-id="27d75-150">当 "**分析关键影响因素**" 工具分析你的数据时，它会执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="27d75-150">When the **Analyze Key Influencers** tool analyzes your data, it does the following:</span></span>  
  
-   <span data-ttu-id="27d75-151">创建一个数据结构，其中存储有关数据分布的关键信息。</span><span class="sxs-lookup"><span data-stu-id="27d75-151">Creates a data structure that stores key information about the distribution of your data.</span></span>  
  
-   <span data-ttu-id="27d75-152">使用 Microsoft Naïve Bayes 算法创建一个模型。</span><span class="sxs-lookup"><span data-stu-id="27d75-152">Creates a model using the Microsoft Naïve Bayes algorithm.</span></span>  
  
-   <span data-ttu-id="27d75-153">创建将每列数据与指定结果关联起来的预测。</span><span class="sxs-lookup"><span data-stu-id="27d75-153">Creates predictions that correlates each column of data with the specified outcome.</span></span>  
  
-   <span data-ttu-id="27d75-154">使用每个预测的置信度分数找出对产生目标结果影响最大的因素。</span><span class="sxs-lookup"><span data-stu-id="27d75-154">Uses the confidence score for each of the predictions to identify the factors that are the most influential in producing the targeted outcome.</span></span>  
  
-   <span data-ttu-id="27d75-155">创建一个报表，其中描述按置信度得分排序的关键影响因素。</span><span class="sxs-lookup"><span data-stu-id="27d75-155">Creates a report describing the key influencers, ordered by confidence scores.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="27d75-156">要求</span><span class="sxs-lookup"><span data-stu-id="27d75-156">Requirements</span></span>  
 <span data-ttu-id="27d75-157">如果目标列包含连续数值，该工具会自动将这些数值分组。</span><span class="sxs-lookup"><span data-stu-id="27d75-157">If the target column contains continuous numeric values, the tool automatically segments the numeric values into groups.</span></span> <span data-ttu-id="27d75-158">这些分组表示具有相似特征的事例的分类。</span><span class="sxs-lookup"><span data-stu-id="27d75-158">These groupings represent clusters of cases that have similar characteristics.</span></span> <span data-ttu-id="27d75-159">但该工具可能不会将这些数值分成用户友好组。</span><span class="sxs-lookup"><span data-stu-id="27d75-159">However, numeric values might not be divided into user-friendly groups.</span></span> <span data-ttu-id="27d75-160">例如，报表可能包含诸如 "12.85701" 之类的分组 \< ，而报表用户通常想要查看使用整数的分组，如10-19、20-29 等。</span><span class="sxs-lookup"><span data-stu-id="27d75-160">For example, the report might contain a grouping such as "\<12.85701", whereas report users typically like to see groupings that use whole numbers, such as 10-19, 20-29, and so on.</span></span>  
  
 <span data-ttu-id="27d75-161">如果希望以其他方式对数值数据分组，必须在创建分析之前以希望的方式拆分这些数据。</span><span class="sxs-lookup"><span data-stu-id="27d75-161">If you want to group numeric data in a different way, you must segment the data the way you want before creating the analysis.</span></span> <span data-ttu-id="27d75-162">例如，您可以使用 Excel 数据挖掘客户端中的 "重新[标记](relabel-sql-server-data-mining-add-ins.md)" 工具在单独的列中创建新的分组标签，然后仅在分析中使用这一新列。</span><span class="sxs-lookup"><span data-stu-id="27d75-162">For example, you can use the [Relabel](relabel-sql-server-data-mining-add-ins.md) tool in the Data Mining Client for Excel to create a new grouping label in a separate column, and then use only that new column in analysis.</span></span>  
  
### <a name="related-tools"></a><span data-ttu-id="27d75-163">相关工具</span><span class="sxs-lookup"><span data-stu-id="27d75-163">Related Tools</span></span>  
 <span data-ttu-id="27d75-164">"**数据挖掘**" 功能区提供了更高级的工具，包括自定义数据挖掘模型的功能</span><span class="sxs-lookup"><span data-stu-id="27d75-164">The **Data Mining** ribbon provides more advanced tools, including the ability to customize data mining models</span></span>  
  
 <span data-ttu-id="27d75-165">如果使用 "**分析关键影响因素**" 工具保存模型，则可以使用数据挖掘客户端浏览模型并更详细地浏览关系。</span><span class="sxs-lookup"><span data-stu-id="27d75-165">If you save your model by using the **Analyze Key Influencers** tool, you can use the Data Mining Client to browse the model and explore relationships in more detail.</span></span> <span data-ttu-id="27d75-166">有关信息，请参阅[在 Excel 中浏览模型 &#40;SQL Server 数据挖掘外接程序&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="27d75-166">For information, see [Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md).</span></span> <span data-ttu-id="27d75-167">还可以使用 Microsoft Office Visio 创建图表和关系图，将关系显示为分类或依赖关系网络。</span><span class="sxs-lookup"><span data-stu-id="27d75-167">You can also use Microsoft Office Visio to create charts and diagrams that display the relationships as cluster or as dependency networks.</span></span> <span data-ttu-id="27d75-168">有关详细信息，请参阅[解决 Visio 数据挖掘关系图 &#40;SQL Server 数据挖掘外接程序&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="27d75-168">For more information, see [Troubleshooting Visio Data Mining Diagrams &#40;SQL Server Data Mining Add-ins&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="27d75-169">在关闭工作表或终止与 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 服务器的连接时，将删除使用表分析工具创建的模型。</span><span class="sxs-lookup"><span data-stu-id="27d75-169">The models that are created when you use the Table Analysis Tools are deleted when you close your worksheet or terminate the connection with the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server.</span></span> <span data-ttu-id="27d75-170">因此，只有在连接处于打开状态时才能浏览模型。</span><span class="sxs-lookup"><span data-stu-id="27d75-170">Therefore, you can only browse the models as long as the connection remains open.</span></span> <span data-ttu-id="27d75-171">如果关闭连接或关闭工作表，则无法在 Visio 中呈现模型。</span><span class="sxs-lookup"><span data-stu-id="27d75-171">You cannot render the models in Visio if you close the connection or close the worksheet.</span></span>  
  
 <span data-ttu-id="27d75-172">有关 "**分析关键影响因素**" 工具使用的算法的详细信息，请参阅 SQL Server 联机丛书中的 "Microsoft Bayes 算法"。</span><span class="sxs-lookup"><span data-stu-id="27d75-172">For more information about the algorithm used by the **Analyze Key Influencers** tool, see "Microsoft Naïve Bayes Algorithm" in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27d75-173">另请参阅</span><span class="sxs-lookup"><span data-stu-id="27d75-173">See Also</span></span>  
 <span data-ttu-id="27d75-174">[用于 Excel 的表分析工具](table-analysis-tools-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="27d75-174">[Table Analysis Tools for Excel](table-analysis-tools-for-excel.md) </span></span>  
 [<span data-ttu-id="27d75-175">创建数据挖掘模型</span><span class="sxs-lookup"><span data-stu-id="27d75-175">Creating a Data Mining Model</span></span>](creating-a-data-mining-model.md)  
  
  
