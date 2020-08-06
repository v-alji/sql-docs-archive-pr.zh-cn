---
title: SQL Server 数据挖掘外接 () 离群值 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- exceptions [data mining]
- data preparation
- outliers [data mining]
- data cleaning
ms.assetid: e6fa7c62-4005-4792-9211-3b699377a517
author: minewiskan
ms.author: owend
ms.openlocfilehash: 92dddf3338d15e700576a13476ee364696bfd274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694605"
---
# <a name="outliers-sql-server-data-mining-add-ins"></a><span data-ttu-id="c4eee-102">离群值（SQL Server 数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="c4eee-102">Outliers (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="c4eee-103">![“数据挖掘”功能区中的离群值向导](media/dmc-outliers.gif "“数据挖掘”功能区中的离群值向导")</span><span class="sxs-lookup"><span data-stu-id="c4eee-103">![Outliers wizard in Data Mining ribbon](media/dmc-outliers.gif "Outliers wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="c4eee-104">*离群*值是指由于以下任一原因而出现问题的数据值：</span><span class="sxs-lookup"><span data-stu-id="c4eee-104">An *outlier* means a data value that is problematic for any one of the following reasons:</span></span>  
  
-   <span data-ttu-id="c4eee-105">值超出预期的范围。</span><span class="sxs-lookup"><span data-stu-id="c4eee-105">Value is outside the expected range.</span></span>  
  
-   <span data-ttu-id="c4eee-106">数据输入可能有误。</span><span class="sxs-lookup"><span data-stu-id="c4eee-106">Data might have been entered incorrectly.</span></span>  
  
-   <span data-ttu-id="c4eee-107">缺少值。</span><span class="sxs-lookup"><span data-stu-id="c4eee-107">Value is missing.</span></span>  
  
-   <span data-ttu-id="c4eee-108">数据包含空格或其他 Null 字符串。</span><span class="sxs-lookup"><span data-stu-id="c4eee-108">Data consists of a space or other null string.</span></span>  
  
-   <span data-ttu-id="c4eee-109">值是准确的，但与分布范围相距甚远，以致无法显著影响模型。</span><span class="sxs-lookup"><span data-stu-id="c4eee-109">Value is accurate, but is so far outside the distribution that it can significantly affect the model.</span></span>  
  
 <span data-ttu-id="c4eee-110">Excel 数据挖掘客户端能帮助您检测这种数据，然后更新值或取消值。</span><span class="sxs-lookup"><span data-stu-id="c4eee-110">The Data Mining Client for Excel helps you detect this data, and then update the values or suppress them.</span></span> <span data-ttu-id="c4eee-111">例如，可将离群值替换为算术平均值，也可删除可能有错的值所在的行。</span><span class="sxs-lookup"><span data-stu-id="c4eee-111">For example, you can replace outliers with an arithmetic mean, or you can delete rows that contain potentially wrong values.</span></span>  
  
## <a name="handling-outliers"></a><span data-ttu-id="c4eee-112">处理离群值</span><span class="sxs-lookup"><span data-stu-id="c4eee-112">Handling Outliers</span></span>  
 <span data-ttu-id="c4eee-113">"**删除离群**值" 向导提供了几种适当处理离群值的工具：</span><span class="sxs-lookup"><span data-stu-id="c4eee-113">The **Remove Outliers** wizard gives you several tools to handle outliers appropriately:</span></span>  
  
-   <span data-ttu-id="c4eee-114">首先，可以浏览数据以便更好了解值的分布以及离群值与其他数据之间的关系。</span><span class="sxs-lookup"><span data-stu-id="c4eee-114">First, you can explore the data to better understand the distribution of values and the relationship of the outliers to other data.</span></span>  
  
     <span data-ttu-id="c4eee-115">例如，您可以使用 "**浏览数据**" 任务来查看和修复这些值。</span><span class="sxs-lookup"><span data-stu-id="c4eee-115">For example, you can use the **Explore Data** task to review and fix the values.</span></span> <span data-ttu-id="c4eee-116">"**删除离群**值" 向导还会显示一个图表，该图可以是线条图或条形图，以帮助你了解所有值的分布情况。</span><span class="sxs-lookup"><span data-stu-id="c4eee-116">The **Remove Outliers** wizard also displays a graph, either a line or a bar chart, to help you understand the distribution of all values.</span></span>  
  
-   <span data-ttu-id="c4eee-117">接下来，可以使用**离群**值向导删除或更改离群值。</span><span class="sxs-lookup"><span data-stu-id="c4eee-117">Next, you can use the **Outliers** wizard to remove or change outliers.</span></span> <span data-ttu-id="c4eee-118">使用的方法取决于值是离散的还是连续的。</span><span class="sxs-lookup"><span data-stu-id="c4eee-118">The method that you use depends on whether the values are discrete or continuous.</span></span>  
  
     <span data-ttu-id="c4eee-119">该向导在条形图中显示离散值，其中的每个条都表示一个特定的值，条的高度指示每个值的事例数。</span><span class="sxs-lookup"><span data-stu-id="c4eee-119">The wizard displays discrete values in a bar chart, where each bar represents a specific value, and the height of the bar indicates the number of cases for each value.</span></span> <span data-ttu-id="c4eee-120">对于表示远离分布中心的值组或可能错误的值组的条，可通过滑动条形图上的阈值控件来切断这些条。</span><span class="sxs-lookup"><span data-stu-id="c4eee-120">By sliding the threshold control on the chart, you can cut off bars that represent groups of extreme or potentially bad values.</span></span>  
  
-   <span data-ttu-id="c4eee-121">该向导在条形图或折线图上显示连续值。</span><span class="sxs-lookup"><span data-stu-id="c4eee-121">The wizard displays continuous values either on a bar chart or line chart.</span></span> <span data-ttu-id="c4eee-122">在折线图中，值在 X 轴上表示，值的计数在 Y 轴上表示。</span><span class="sxs-lookup"><span data-stu-id="c4eee-122">On the line chart, the value is represented on the x-axis and the count of values on the y-axis.</span></span>  
  
     <span data-ttu-id="c4eee-123">您可以通过更改**最小**值和最大值，或滑动条形，来控制是在图表的低端和**最大**端删除还是保留值。</span><span class="sxs-lookup"><span data-stu-id="c4eee-123">You can control whether to remove or keep values at the low and high ends of the chart by changing the **Minimum** and **Maximum** values, or sliding the bars.</span></span> <span data-ttu-id="c4eee-124">更改最小值和最大值设置时，要被取消的数据在图表中以阴影显示。</span><span class="sxs-lookup"><span data-stu-id="c4eee-124">As you change the minimum and maximum value settings, the data that will be suppressed is shown by shading in the graph.</span></span>  
  
 <span data-ttu-id="c4eee-125">选择了要处理的离群值之后，可以设置向导如何处理这些离群值。</span><span class="sxs-lookup"><span data-stu-id="c4eee-125">After you have selected which outliers to work with, you tell the wizard how to handle the outliers.</span></span> <span data-ttu-id="c4eee-126">您可以删除包含离群值的行，或者指定替换值，例如平均值、Null 或其他选择值。</span><span class="sxs-lookup"><span data-stu-id="c4eee-126">You can either delete the rows that contain the outlier values, or you can specify a replacement value, such as a mean, a null, or another value of your choice.</span></span>  
  
 <span data-ttu-id="c4eee-127">最后，向导为您提供多种显示新数据的方式。</span><span class="sxs-lookup"><span data-stu-id="c4eee-127">Finally, the wizard gives you some options for displaying the new data.</span></span> <span data-ttu-id="c4eee-128">您可以将原始数据替换为新值，在表中添加包含新值的新列，或者创建包含更新数据的新工作表。</span><span class="sxs-lookup"><span data-stu-id="c4eee-128">You can replace the original data with the new values, add a new column to the table that contains the new values, or create a new worksheet that contains the updated data.</span></span>  
  
### <a name="using-the-outlier-wizard"></a><span data-ttu-id="c4eee-129">使用离群值向导</span><span class="sxs-lookup"><span data-stu-id="c4eee-129">Using the Outlier Wizard</span></span>  
  
1.  <span data-ttu-id="c4eee-130">在 "**数据挖掘**" 功能区中，单击 "**清理数据**"，然后选择**离群**值。</span><span class="sxs-lookup"><span data-stu-id="c4eee-130">In the **Data Mining** ribbon, click **Clean Data**, and select **Outliers**.</span></span>  
  
2.  <span data-ttu-id="c4eee-131">在 "**选择源数据**" 对话框中，选择一个 Excel 数据表或一系列单元格，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="c4eee-131">In the **Select Source Data** dialog box, select an Excel data table, or a range of cells, and click **Next**.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="c4eee-132">不能对外部数据使用**离群**值向导，除非先将该数据复制到 Excel。</span><span class="sxs-lookup"><span data-stu-id="c4eee-132">You cannot use the **Outliers** wizard on external data, unless you copy it to Excel first.</span></span>  
  
3.  <span data-ttu-id="c4eee-133">在 "**选择列**" 对话框中，选择**单个**列。</span><span class="sxs-lookup"><span data-stu-id="c4eee-133">In the **Select Column** dialog box, select a **single** column.</span></span>  
  
     <span data-ttu-id="c4eee-134">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="c4eee-134">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="c4eee-135">在 "**指定阈值**" 对话框中，查看数据的分布情况。</span><span class="sxs-lookup"><span data-stu-id="c4eee-135">In the **Specify Thresholds** dialog box, review the distribution of data.</span></span>  
  
    -   <span data-ttu-id="c4eee-136">如果该列含有离散值，则向导显示一个直方图，其中含有每个离散值的数量。</span><span class="sxs-lookup"><span data-stu-id="c4eee-136">If the column contains discrete values, the wizard displays a histogram containing the count for each discrete value.</span></span>  
  
         <span data-ttu-id="c4eee-137">假设离群值为罕见值，则可以通过更改 "**最小**值" 来筛选它们。</span><span class="sxs-lookup"><span data-stu-id="c4eee-137">Assuming that outliers are rare values, you can filter them out by changing the **Minimum** value.</span></span>  
  
    -   <span data-ttu-id="c4eee-138">如果列中包含数值数据，则可以在条形图或折线图中，单击 "**以离散形式显示视图**" 或 "**按数值显示视图**"，以在查看条形图或折线图中的值之间进行切换。</span><span class="sxs-lookup"><span data-stu-id="c4eee-138">If the column contains numeric data, you can click the **View as Discrete** button or the **View as Numeric** button to toggle between viewing the values in a bar chart or line chart.</span></span>  
  
5.  <span data-ttu-id="c4eee-139">在 "**指定阈值**" 对话框中，通过键入最小值和最大值，或者通过拖动滑块来选择想要保留的数据的范围。</span><span class="sxs-lookup"><span data-stu-id="c4eee-139">In the **Specify Thresholds** dialog box, choose the range of data you want to keep by typing a minimum and maximum value, or by dragging the slider bars.</span></span> <span data-ttu-id="c4eee-140">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="c4eee-140">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="c4eee-141">在 "**离群处理**" 对话框中，指定是否要删除或替换值，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="c4eee-141">In the **Outlier Handling** dialog box, specify whether you want the values to be deleted or replaced, and click **Next**.</span></span>  
  
7.  <span data-ttu-id="c4eee-142">在 "**选择目标**" 对话框中，指定要保存新数据的位置。</span><span class="sxs-lookup"><span data-stu-id="c4eee-142">In the **Select Destination** dialog box, specify where you want the new data to be saved.</span></span>  
  
### <a name="related-options"></a><span data-ttu-id="c4eee-143">相关选项</span><span class="sxs-lookup"><span data-stu-id="c4eee-143">Related Options</span></span>  
 <span data-ttu-id="c4eee-144">该向导提供以下选项：</span><span class="sxs-lookup"><span data-stu-id="c4eee-144">The wizard provides these options:</span></span>  
  
|<span data-ttu-id="c4eee-145">**选项**</span><span class="sxs-lookup"><span data-stu-id="c4eee-145">**Options**</span></span>|<span data-ttu-id="c4eee-146">**注释**</span><span class="sxs-lookup"><span data-stu-id="c4eee-146">**Comment**</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="c4eee-147">**选择列**</span><span class="sxs-lookup"><span data-stu-id="c4eee-147">**Select Column**</span></span>|<span data-ttu-id="c4eee-148">一次只能处理一列。</span><span class="sxs-lookup"><span data-stu-id="c4eee-148">You can work with only one column at a time.</span></span>|  
|<span data-ttu-id="c4eee-149">**指定阈值处理**</span><span class="sxs-lookup"><span data-stu-id="c4eee-149">**Specify Thresholds Handling**</span></span>|<span data-ttu-id="c4eee-150">使用 "**最小**值" 设置阈值以排除比阈值更少的行中发现的值。</span><span class="sxs-lookup"><span data-stu-id="c4eee-150">Set a threshold using **Minimum** to exclude values that are found in fewer rows than the threshold value.</span></span><br /><br /> <span data-ttu-id="c4eee-151">最初，**最小**值等于最小行数的值，并且不能使小于该值的最小值。</span><span class="sxs-lookup"><span data-stu-id="c4eee-151">Initially the value in **Minimum** is equal to the value with the fewest rows, and you cannot make the minimum lower than that value.</span></span>|  
|<span data-ttu-id="c4eee-152">**离群值处理**</span><span class="sxs-lookup"><span data-stu-id="c4eee-152">**Outlier Handling**</span></span>|<span data-ttu-id="c4eee-153">如果决定删除离群值，则可更改当前工作表中的数据，也可在新工作表中创建数据的副本。</span><span class="sxs-lookup"><span data-stu-id="c4eee-153">If you decide to delete outliers, you can either change the data in the current worksheet, or create a copy of the data in a new worksheet.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c4eee-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c4eee-154">See Also</span></span>  
 [<span data-ttu-id="c4eee-155">浏览数据挖掘外接 &#40;SQL Server 数据&#41;</span><span class="sxs-lookup"><span data-stu-id="c4eee-155">Explore Data &#40;SQL Server Data Mining Add-ins&#41;</span></span>](explore-data-sql-server-data-mining-add-ins.md)  
  
  
