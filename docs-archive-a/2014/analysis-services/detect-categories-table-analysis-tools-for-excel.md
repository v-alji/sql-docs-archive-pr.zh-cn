---
title: 检测) Excel (表分析工具的类别 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- clustering [data mining]
- mining model, decision tree
- category detection
ms.assetid: 3c7e9ebb-d0c9-498e-a9ba-cc13eaa43520
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4874c85d7e4ab65716741e8ae9433406dfb08b74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692006"
---
# <a name="detect-categories-table-analysis-tools-for-excel"></a><span data-ttu-id="189bd-102">检测类别（Excel 表分析工具）</span><span class="sxs-lookup"><span data-stu-id="189bd-102">Detect Categories (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="189bd-103">![功能区中的“检测类别”按钮](media/tat-detectcat.gif "功能区中的“检测类别”按钮")</span><span class="sxs-lookup"><span data-stu-id="189bd-103">![Detect Categories button in ribbon](media/tat-detectcat.gif "Detect Categories button in ribbon")</span></span>

 <span data-ttu-id="189bd-104">"**检测类别**" 工具在表中自动查找具有类似特征的行。</span><span class="sxs-lookup"><span data-stu-id="189bd-104">The **Detect Categories** tool automatically finds rows in a table that have similar characteristics.</span></span>

 <span data-ttu-id="189bd-105">此工具完成查找后，它将创建一个报表，其中列出所找到的类别以及这些类别的区分特征。</span><span class="sxs-lookup"><span data-stu-id="189bd-105">When the tool finishes, it creates a report that lists the categories it found, together with their distinguishing characteristics.</span></span> <span data-ttu-id="189bd-106">默认情况下，它会针对每一行数据向数据表中添加一个包含所推荐类别的新列。</span><span class="sxs-lookup"><span data-stu-id="189bd-106">By default, it adds a new column to the data table that contains the proposed category for each row of your data.</span></span> <span data-ttu-id="189bd-107">然后，您可以检查这些类别并重命名它们。</span><span class="sxs-lookup"><span data-stu-id="189bd-107">You can then review the categories and rename them.</span></span>

## <a name="using-the-detect-categories-tool"></a><span data-ttu-id="189bd-108">使用检测类别工具</span><span class="sxs-lookup"><span data-stu-id="189bd-108">Using the Detect Categories Tool</span></span>

1.  <span data-ttu-id="189bd-109">打开 Excel 表。</span><span class="sxs-lookup"><span data-stu-id="189bd-109">Open an Excel table.</span></span>

2.  <span data-ttu-id="189bd-110">单击 "**检测类别**"。</span><span class="sxs-lookup"><span data-stu-id="189bd-110">Click **Detect Categories**.</span></span>

3.  <span data-ttu-id="189bd-111">指定要在分析中使用的列。</span><span class="sxs-lookup"><span data-stu-id="189bd-111">Specify the columns to use in analysis.</span></span> <span data-ttu-id="189bd-112">您可以取消选择具有非重复值（例如人名或记录 ID）的列，因为这些列对于分析来说可能无用。</span><span class="sxs-lookup"><span data-stu-id="189bd-112">You can deselect columns that have distinct values, such as personal names or record IDs, because these columns might not be useful for analysis.</span></span>

4.  <span data-ttu-id="189bd-113">您可以选择指定要创建的类别的最大数目。</span><span class="sxs-lookup"><span data-stu-id="189bd-113">Optionally, specify the maximum number of categories to create.</span></span> <span data-ttu-id="189bd-114">默认情况下，该工具找到多少个类别，就会自动创建多少个类别。</span><span class="sxs-lookup"><span data-stu-id="189bd-114">By default, the tool automatically creates as many categories as it finds.</span></span>

5.  <span data-ttu-id="189bd-115">单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="189bd-115">Click **Run**.</span></span>

6.  <span data-ttu-id="189bd-116">此工具创建一个名为“类别报表”的新工作表，其中包含类别的列表以及它们的特征。</span><span class="sxs-lookup"><span data-stu-id="189bd-116">The tool creates a new worksheet, named Categories Report, which contains the list of categories and their characteristics.</span></span>

 <span data-ttu-id="189bd-117">有关如何为该工具指定选项的详细信息，请参阅 "[检测类别" 对话框 (Excel) 的表分析工具](detect-categories-table-analysis-tools-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="189bd-117">For more information about how to specify options for the tool, see [Detect Categories Dialog Box (Table Analysis Tools for Excel)](detect-categories-table-analysis-tools-for-excel.md).</span></span>

## <a name="understanding-the-categories-report"></a><span data-ttu-id="189bd-118">了解分类报表</span><span class="sxs-lookup"><span data-stu-id="189bd-118">Understanding the Categories Report</span></span>
 <span data-ttu-id="189bd-119">"**类别" 报表**包含两个表： "**类别列表**" 和 "**类别特征**"，以及 "**类别配置文件**" 图表。</span><span class="sxs-lookup"><span data-stu-id="189bd-119">The **Categories Report** contains two tables, **Category List** and **Category Characteristics**, and a **Category Profiles** chart.</span></span>

### <a name="category-list"></a><span data-ttu-id="189bd-120">类别列表</span><span class="sxs-lookup"><span data-stu-id="189bd-120">Category List</span></span>
 <span data-ttu-id="189bd-121">第一个表列出找到的类别。</span><span class="sxs-lookup"><span data-stu-id="189bd-121">The first table lists the categories that were found.</span></span> <span data-ttu-id="189bd-122">"**行计数**" 列指示分配给每个类别的数据行数。</span><span class="sxs-lookup"><span data-stu-id="189bd-122">The **Row Count** column indicates how many rows of data were assigned to each category.</span></span>

 <span data-ttu-id="189bd-123">该模型创建每个类别的临时名称，但是您可以随意将其重命名。</span><span class="sxs-lookup"><span data-stu-id="189bd-123">The model creates temporary names for each category, but you can rename the categories as you like.</span></span> <span data-ttu-id="189bd-124">例如，在下面的示例中，第一个类别已重命名为**低收入**，因为这是群集的顶级属性。</span><span class="sxs-lookup"><span data-stu-id="189bd-124">For example, in the following example, the first category has been renamed **Low Income**, because that was the top attribute of the cluster.</span></span>

 <span data-ttu-id="189bd-125">![用“检测类别”工具创建的报告](media/dm13-tat-detectcat-report1.gif "用“检测类别”工具创建的报告")</span><span class="sxs-lookup"><span data-stu-id="189bd-125">![report created by Detect Categories tool](media/dm13-tat-detectcat-report1.gif "report created by Detect Categories tool")</span></span>

 <span data-ttu-id="189bd-126">键入新标签后，更改即传播到所有其他图表以及源数据工作表中添加的类别列表。</span><span class="sxs-lookup"><span data-stu-id="189bd-126">As soon as you type the new label, the change is propagated to all the other charts as well as to the category list added in the source data worksheet.</span></span>

### <a name="category-characteristics"></a><span data-ttu-id="189bd-127">类别特征</span><span class="sxs-lookup"><span data-stu-id="189bd-127">Category Characteristics</span></span>
 <span data-ttu-id="189bd-128">第二个表 "**类别特征**" 显示有关每个类别的构成的详细信息。</span><span class="sxs-lookup"><span data-stu-id="189bd-128">The second table, **Category Characteristics**, shows details about the makeup of each category.</span></span> <span data-ttu-id="189bd-129">单击 "**类别**" 列顶部的 "**筛选器**" 按钮，以查看焦点上的一个或多个类别。</span><span class="sxs-lookup"><span data-stu-id="189bd-129">Click the **Filter** button at the top of the **Category** column to see focus on one or just a few categories.</span></span>

 <span data-ttu-id="189bd-130">![用“检测类别”工具创建的报告](media/dm13-tat-detectcat-report2.gif "用“检测类别”工具创建的报告")</span><span class="sxs-lookup"><span data-stu-id="189bd-130">![report created by Detect Categories tool](media/dm13-tat-detectcat-report2.gif "report created by Detect Categories tool")</span></span>

 <span data-ttu-id="189bd-131">列中的底纹**相对重要性**表明，属性和值的组合是一种区分因素的重要程度。</span><span class="sxs-lookup"><span data-stu-id="189bd-131">The shading in the column, **Relative Importance**, indicates how important that combination of attribute and value is as a distinguishing factor.</span></span> <span data-ttu-id="189bd-132">该条越长，此属性越可能充分代表此类别。</span><span class="sxs-lookup"><span data-stu-id="189bd-132">The longer the bar, the more likely it is that this attribute is strongly representative of this category.</span></span>

### <a name="categories-profile-chart"></a><span data-ttu-id="189bd-133">类别分布图</span><span class="sxs-lookup"><span data-stu-id="189bd-133">Categories Profile Chart</span></span>
 <span data-ttu-id="189bd-134">"**类别报表**" 工作表中的最终图表是一个交互式**透视图** **，可**用于重新排列和隐藏字段、对值进行筛选和自定义图表的外观。</span><span class="sxs-lookup"><span data-stu-id="189bd-134">The final chart in the **Categories Report** worksheet, **Category Profiles**, is an interactive **Pivot Chart** that you can use to rearrange and hide fields, filter on values, and customize the chart's appearance.</span></span>

 <span data-ttu-id="189bd-135">Excel 2013 现在提供了设计图面中的**图表样式**和**图表元素**控件，使您可以轻松地改进图表设计。</span><span class="sxs-lookup"><span data-stu-id="189bd-135">Excel 2013 now provides **Chart Styles** and **Chart Elements** controls right in the design surface that make it easy to improve the chart design.</span></span>

 <span data-ttu-id="189bd-136">![用“检测类别”工具创建的报告](media/dm13-tat-detectcat-report3.gif "用“检测类别”工具创建的报告")</span><span class="sxs-lookup"><span data-stu-id="189bd-136">![report created by Detect Categories tool](media/dm13-tat-detectcat-report3.gif "report created by Detect Categories tool")</span></span>

## <a name="requirements"></a><span data-ttu-id="189bd-137">要求</span><span class="sxs-lookup"><span data-stu-id="189bd-137">Requirements</span></span>
 <span data-ttu-id="189bd-138">"**检测类别**" 工具不要求数据量或数据类型。</span><span class="sxs-lookup"><span data-stu-id="189bd-138">The **Detect Categories** tool has no requirements for the amount or type of data.</span></span>

> [!NOTE]
>  <span data-ttu-id="189bd-139">使用 "**检测类别**" 工具时，它会在原始数据表中创建新的列 "类别"。</span><span class="sxs-lookup"><span data-stu-id="189bd-139">When you use the **Detect Categories** tool, it creates a new column, Category, in the original data table.</span></span> <span data-ttu-id="189bd-140">如果将此列保留在数据表中，然后执行后续数据挖掘操作，则此列的存在可能会影响您的分析结果。</span><span class="sxs-lookup"><span data-stu-id="189bd-140">If you leave this column in the data table and then perform subsequent data mining operations, the presence of this column could influence your results.</span></span> <span data-ttu-id="189bd-141">为了确保这不会影响其他操作，您应制作一份不包含“类别”列的数据表副本，然后再使用其他数据挖掘工具。</span><span class="sxs-lookup"><span data-stu-id="189bd-141">To ensure that this does not affect other operations, you should make a copy of the data table without the Category column before using other data mining tools.</span></span>

## <a name="related-tools"></a><span data-ttu-id="189bd-142">相关工具</span><span class="sxs-lookup"><span data-stu-id="189bd-142">Related Tools</span></span>
 <span data-ttu-id="189bd-143">当 "**检测类别**" 工具分析您的数据时，它将使用聚类分析算法创建数据挖掘结构和数据挖掘模型 [!INCLUDE[msCoName](../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="189bd-143">When the **Detect Categories** tool analyzes your data, it creates a data mining structure and data mining model by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm.</span></span>

 <span data-ttu-id="189bd-144">使用 "**分析关键影响因素**" 工具创建数据挖掘模型之后，您可以使用 Excel 数据挖掘客户端浏览该模型并更详细地浏览关系。</span><span class="sxs-lookup"><span data-stu-id="189bd-144">After you have created a data mining model by using the **Analyze Key Influencers** tool, you can use the Data Mining Client for Excel to browse the model and explore relationships in more detail.</span></span> <span data-ttu-id="189bd-145">Excel 数据挖掘客户端是一个独立的外接程序，它提供了更多的高级数据挖掘功能。</span><span class="sxs-lookup"><span data-stu-id="189bd-145">The Data Mining Client for Excel is a separate add-in that provides more advanced data mining functionality.</span></span> <span data-ttu-id="189bd-146">有关信息，请参阅[在 Excel 中浏览模型 &#40;SQL Server 数据挖掘外接程序&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="189bd-146">For information, see [Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md).</span></span>

 <span data-ttu-id="189bd-147">有关使用 Excel 数据挖掘客户端中的数据建模功能的详细信息，请参阅[创建数据挖掘模型](creating-a-data-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="189bd-147">For more information about using the data modeling capabilities in the Data Mining Client for Excel, see [Creating a Data Mining Model](creating-a-data-mining-model.md).</span></span>

 <span data-ttu-id="189bd-148">有关 "**检测类别**" 工具使用的算法的详细信息，请参阅联机丛书中的主题 "Microsoft 聚类分析算法" [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="189bd-148">For more information about the algorithm used by the **Detect Categories** tool, see the topic "Microsoft Clustering Algorithm" in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>

## <a name="see-also"></a><span data-ttu-id="189bd-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="189bd-149">See Also</span></span>
 [<span data-ttu-id="189bd-150">Excel 表分析工具</span><span class="sxs-lookup"><span data-stu-id="189bd-150">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)


