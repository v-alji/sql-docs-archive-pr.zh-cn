---
title: 突出显示 Excel)  (表分析工具的异常 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- highlight exceptions
ms.assetid: d90a12f8-7bc3-4fdb-95a1-7c89058f0d9a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 97e8197fc76f431cf9740c5c6fbd7ac44d8204a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693143"
---
# <a name="highlight-exceptions-table-analysis-tools-for-excel"></a><span data-ttu-id="556cf-102">突出显示异常值（Excel 表分析工具）</span><span class="sxs-lookup"><span data-stu-id="556cf-102">Highlight Exceptions (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="556cf-103">![功能区中的“突出显示异常值”按钮](media/tat-highlightex.gif "功能区中的“突出显示异常值”按钮")</span><span class="sxs-lookup"><span data-stu-id="556cf-103">![Highlight Exceptions button in ribbon](media/tat-highlightex.gif "Highlight Exceptions button in ribbon")</span></span>  
  
 <span data-ttu-id="556cf-104">有时您的数据可能包含异常的值。</span><span class="sxs-lookup"><span data-stu-id="556cf-104">Sometimes your data might contain peculiar values.</span></span> <span data-ttu-id="556cf-105">例如，可能列出某位屋主的年龄为 5 岁。</span><span class="sxs-lookup"><span data-stu-id="556cf-105">For example, a homeowner's age might be listed as five years old.</span></span> <span data-ttu-id="556cf-106">这些值通常称为*离群*值，可能是因为数据输入错误，也可能表示异常趋势。</span><span class="sxs-lookup"><span data-stu-id="556cf-106">These values, often called *outliers*, might be wrong because of a data input error, or they might indicate unusual trends.</span></span> <span data-ttu-id="556cf-107">不管是哪种情况，异常值都可能影响分析的质量。</span><span class="sxs-lookup"><span data-stu-id="556cf-107">Either way, exceptions can affect the quality of your analysis.</span></span> <span data-ttu-id="556cf-108">**突出显示异常**值工具可帮助你查找这些值，并对其进行检查以便进一步操作。</span><span class="sxs-lookup"><span data-stu-id="556cf-108">The **Highlight Exceptions** tool helps you find these values and review them for further action.</span></span>  
  
 <span data-ttu-id="556cf-109">**突出显示异常**工具可用于 Excel 数据表中的整个数据区域，您也可以只选择几列。</span><span class="sxs-lookup"><span data-stu-id="556cf-109">The **Highlight Exceptions** tool can work with the entire range of data in an Excel data table, or you can select only a few columns.</span></span> <span data-ttu-id="556cf-110">您还可以调整控制数据变化范围的阈值，以找到更多或更少的异常值。</span><span class="sxs-lookup"><span data-stu-id="556cf-110">You can also adjust a threshold that controls the variability of data, to find more or fewer exceptions.</span></span>  
  
 <span data-ttu-id="556cf-111">工具完成分析时将创建一个新工作表，其中包含在所分析的各个列中找到了多少离群值的汇总报表。</span><span class="sxs-lookup"><span data-stu-id="556cf-111">When the tool completes its analysis, it creates a new worksheet that contains a summary report of how many outliers were found in each of the columns that you analyzed.</span></span> <span data-ttu-id="556cf-112">该工具还会在原始数据表中突出显示异常值。</span><span class="sxs-lookup"><span data-stu-id="556cf-112">The tool also highlights the exceptions in the original data table.</span></span> <span data-ttu-id="556cf-113">由于该工具分析的是整体趋势，因此可能会发现行中的大多数值是正常的，并将只突出显示该行中的一个单元格。</span><span class="sxs-lookup"><span data-stu-id="556cf-113">Because the tool analyzes overall trends, it might find that most of the values in a row are normal, and highlight only one cell in that row.</span></span> <span data-ttu-id="556cf-114">在上面的屋主示例中，只会突出显示**Age**列。</span><span class="sxs-lookup"><span data-stu-id="556cf-114">In the homeowner example above, only the **Age** column might be highlighted.</span></span>  
  
 <span data-ttu-id="556cf-115">您还可以在 "**摘要" 报表**中更改 "**异常阈值**"。</span><span class="sxs-lookup"><span data-stu-id="556cf-115">You can also change the **Exception threshold** value in the **Summary Report**.</span></span> <span data-ttu-id="556cf-116">此值指示特定单元格包含异常值的概率。</span><span class="sxs-lookup"><span data-stu-id="556cf-116">This value indicates the probability that a particular cell contains an abnormal value.</span></span> <span data-ttu-id="556cf-117">因此，如果您增大该值，则更少的值被突出显示为离群值。</span><span class="sxs-lookup"><span data-stu-id="556cf-117">Therefore, if you increase the value, fewer values will be highlighted as outliers.</span></span> <span data-ttu-id="556cf-118">反之，减小该值将显示更多突出显示的单元格。</span><span class="sxs-lookup"><span data-stu-id="556cf-118">Conversely, when you decrease the value, you will see more highlighted cells.</span></span>  
  
## <a name="using-the-highlight-exceptions-tool"></a><span data-ttu-id="556cf-119">使用突出显示异常工具</span><span class="sxs-lookup"><span data-stu-id="556cf-119">Using the Highlight Exceptions Tool</span></span>  
  
1.  <span data-ttu-id="556cf-120">打开 Excel 表，然后单击 "**突出显示异常**"。</span><span class="sxs-lookup"><span data-stu-id="556cf-120">Open an Excel table and click **Highlight Exceptions**.</span></span>  
  
2.  <span data-ttu-id="556cf-121">指定要分析的列。</span><span class="sxs-lookup"><span data-stu-id="556cf-121">Specify the columns to analyze.</span></span>  
  
3.  <span data-ttu-id="556cf-122">单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="556cf-122">Click **Run**.</span></span>  
  
4.  <span data-ttu-id="556cf-123">打开标题为 "离群值" 的工作表 \<table name> ，以查看找到的离群值摘要。</span><span class="sxs-lookup"><span data-stu-id="556cf-123">Open the worksheet titled \<table name> Outliers to view a summary of the outliers that were found.</span></span>  
  
5.  <span data-ttu-id="556cf-124">若要更改突出显示的数量，请单击 "**突出显示异常" 报表**的 "**异常阈值**" 行中的向上和向下箭头。</span><span class="sxs-lookup"><span data-stu-id="556cf-124">To change the number of highlights, click the up and down arrows in the **Exception Threshold** row of the **Highlight Exceptions Report**.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="556cf-125">要求</span><span class="sxs-lookup"><span data-stu-id="556cf-125">Requirements</span></span>  
 <span data-ttu-id="556cf-126">如果有些看似异常的值包含了可用于预测其他行的信息，它们不一定是错误的，您仍可以包含具有这些值的列。</span><span class="sxs-lookup"><span data-stu-id="556cf-126">You can include columns that do not contain bad values if these values contain information that might be useful in predicting other rows.</span></span> <span data-ttu-id="556cf-127">但您应该取消选择缺失了许多值或有许多零值的列。</span><span class="sxs-lookup"><span data-stu-id="556cf-127">However, you should deselect columns that have many missing or zero values.</span></span>  
  
 <span data-ttu-id="556cf-128">由于所有所选列都用于创建常规模式，因此应避免使用类似如下已知包含不良信息的输入列：</span><span class="sxs-lookup"><span data-stu-id="556cf-128">Because all of the selected columns are used to create a general pattern, you should avoid using input columns that you know to have poor information, such as the following:</span></span>  
  
-   <span data-ttu-id="556cf-129">包含唯一值（如 ID）的列。</span><span class="sxs-lookup"><span data-stu-id="556cf-129">Columns that contain unique values such as IDs.</span></span>  
  
-   <span data-ttu-id="556cf-130">包含错误值所占比率高的列。</span><span class="sxs-lookup"><span data-stu-id="556cf-130">Columns that contain a high percentage of wrong values.</span></span>  
  
-   <span data-ttu-id="556cf-131">包含多个缺失值的列。</span><span class="sxs-lookup"><span data-stu-id="556cf-131">Columns with many missing values.</span></span>  
  
     <span data-ttu-id="556cf-132">请注意，在某些情况下，需要包含具有多个缺失值的输入列。</span><span class="sxs-lookup"><span data-stu-id="556cf-132">Note that there are some cases where it is useful to include input columns that have many missing values.</span></span> <span data-ttu-id="556cf-133">例如，如果客户通过零售店购买时总是缺少地址字段的值，数据挖掘算法可以使用此信息识别其他类似的客户。</span><span class="sxs-lookup"><span data-stu-id="556cf-133">For example, if the value of the address field is always missing when the customer buys through a retailer, the data mining algorithm can use this information to identify other similar customers.</span></span> <span data-ttu-id="556cf-134">您必须基于每个案例确定缺失的数据是疏忽造成的还是“缺失”状态是有意义的。</span><span class="sxs-lookup"><span data-stu-id="556cf-134">You must determine on a case-by-case basis whether data is missing by omission or because the Missing state is meaningful.</span></span>  
  
-   <span data-ttu-id="556cf-135">创建模式时不太可能有用的列。</span><span class="sxs-lookup"><span data-stu-id="556cf-135">Columns that are unlikely to be useful in creating a pattern.</span></span> <span data-ttu-id="556cf-136">例如，每行中具有相同值的列不会添加对生成模式有用的任何信息。</span><span class="sxs-lookup"><span data-stu-id="556cf-136">For example, a column that has the same value in every row adds no information that would be useful in building patterns.</span></span>  
  
## <a name="understanding-the-highlight-exceptions-report"></a><span data-ttu-id="556cf-137">了解突出显示异常值报表</span><span class="sxs-lookup"><span data-stu-id="556cf-137">Understanding the Highlight Exceptions Report</span></span>  
 <span data-ttu-id="556cf-138">单击 "**运行**" 时，该工具将执行以下三项操作：</span><span class="sxs-lookup"><span data-stu-id="556cf-138">When you click **Run**, the tool does three things:</span></span>  
  
-   <span data-ttu-id="556cf-139">根据表中的当前数据创建数据挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="556cf-139">Creates a data mining structure based on the current data in the table.</span></span>  
  
-   <span data-ttu-id="556cf-140">使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 聚类分析算法创建新的数据挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="556cf-140">Creates a new data mining model by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm.</span></span>  
  
-   <span data-ttu-id="556cf-141">按照模式创建预测查询，以确定工作表中的任何值是否是不可能的。</span><span class="sxs-lookup"><span data-stu-id="556cf-141">Creates a prediction query based on the patterns to determine whether any values in the worksheet are improbable.</span></span>  
  
 <span data-ttu-id="556cf-142">异常阈值的初始值始终为 75，这表示算法计算的突出显示数据的有错几率为 75%。</span><span class="sxs-lookup"><span data-stu-id="556cf-142">The initial value for the exception threshold is always 75, meaning that the algorithm calculated there is a 75% chance that the highlighted data is wrong.</span></span> <span data-ttu-id="556cf-143">该工具自动设置此阈值以便能够通过初始分析，但您可以在报表中更改此值。</span><span class="sxs-lookup"><span data-stu-id="556cf-143">The tool automatically sets this threshold for the initial analysis pass, but you can change the value in the report.</span></span>  
  
 <span data-ttu-id="556cf-144">**突出显示异常**工具突出显示原始数据表中可疑的单元格。</span><span class="sxs-lookup"><span data-stu-id="556cf-144">The **Highlight Exceptions** tool highlights cells in the original data table that are suspicious.</span></span> <span data-ttu-id="556cf-145">深色突出显示表示需要注意该行。</span><span class="sxs-lookup"><span data-stu-id="556cf-145">Dark highlighting means the row needs attention.</span></span> <span data-ttu-id="556cf-146">浅色突出显示表示特定单元格中的值很可疑。</span><span class="sxs-lookup"><span data-stu-id="556cf-146">Bright highlighting means the value in that particular cell was identified as suspect.</span></span> <span data-ttu-id="556cf-147">如果更改异常的阈值，突出显示的值将相应地更改。</span><span class="sxs-lookup"><span data-stu-id="556cf-147">If you change the threshold for the exceptions, the highlighted values will change accordingly.</span></span>  
  
 <span data-ttu-id="556cf-148">摘要图表显示每列中超出异常阈值的单元格的数量。</span><span class="sxs-lookup"><span data-stu-id="556cf-148">The summary chart shows the number of cells in each column that were above the exception threshold.</span></span>  
  
## <a name="related-tools"></a><span data-ttu-id="556cf-149">相关工具</span><span class="sxs-lookup"><span data-stu-id="556cf-149">Related Tools</span></span>  
 <span data-ttu-id="556cf-150">在清除或检查数据以为数据挖掘作准备时，您还可以尝试使用 Excel 数据挖掘客户端中的数据浏览功能。</span><span class="sxs-lookup"><span data-stu-id="556cf-150">When you are cleaning or reviewing data in preparation for data mining, you might also try the data exploration features in the Data Mining Client for Excel.</span></span> <span data-ttu-id="556cf-151">此外接程序提供了更高级的工具，可以帮助您查找离散值、重新标记数据或者查看数据的分布情况。</span><span class="sxs-lookup"><span data-stu-id="556cf-151">This add-in provides more advanced tools to help you find outliers, relabel data, or view the distribution of data.</span></span> <span data-ttu-id="556cf-152">有关 Excel 数据挖掘客户端中的数据浏览工具的详细信息，请参阅[浏览和清理数据](exploring-and-cleaning-data.md)。</span><span class="sxs-lookup"><span data-stu-id="556cf-152">For more information about data exploration tools in the Data Mining Client for Excel, see [Exploring and Cleaning Data](exploring-and-cleaning-data.md).</span></span>  
  
 <span data-ttu-id="556cf-153">**突出显示异常**工具使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 聚类分析算法。</span><span class="sxs-lookup"><span data-stu-id="556cf-153">The **Highlight Exceptions** tool uses the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm.</span></span> <span data-ttu-id="556cf-154">聚类分析模型检测各组具有相似特征的行。</span><span class="sxs-lookup"><span data-stu-id="556cf-154">A clustering model detects groups of rows that share similar characteristics.</span></span> <span data-ttu-id="556cf-155">Excel 数据挖掘客户端提供一个**浏览**窗口，该窗口使用图形和特征配置文件来浏览群集所创建的数据挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="556cf-155">The Data Mining Client for Excel provides a **Browse** window that uses graphs and characteristic profiles to let you explore data mining models created by clustering.</span></span> <span data-ttu-id="556cf-156">有关如何浏览**突出显示异常**工具创建的聚类分析模型的信息，请参阅[浏览模型 (Excel 数据挖掘客户端) ](highlight-exceptions-table-analysis-tools-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="556cf-156">For information about how to browse the clustering model created by the **Highlight Exceptions** tool, see [Browse Models (Data Mining Client for Excel)](highlight-exceptions-table-analysis-tools-for-excel.md).</span></span>  
  
 <span data-ttu-id="556cf-157">有关 [!INCLUDE[msCoName](../includes/msconame-md.md)] 聚类分析算法的详细信息，请参阅 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 联机丛书中的主题“Microsoft 聚类分析算法”。</span><span class="sxs-lookup"><span data-stu-id="556cf-157">For more information about the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm, see the topic "Microsoft Clustering Algorithm" in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="556cf-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="556cf-158">See Also</span></span>  
 [<span data-ttu-id="556cf-159">Excel 表分析工具</span><span class="sxs-lookup"><span data-stu-id="556cf-159">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)  
  
  
