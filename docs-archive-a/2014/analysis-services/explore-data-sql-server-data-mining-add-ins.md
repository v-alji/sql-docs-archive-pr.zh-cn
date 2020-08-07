---
title: 浏览数据 (SQL Server 数据挖掘外接程序) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data preparation
- histogram [data mining]
- data visualization
ms.assetid: 714845a9-4c27-461a-9ba3-149e1e818386
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2572c11e92dcf99dfa3adf661603e8f65f05116e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690853"
---
# <a name="explore-data-sql-server-data-mining-add-ins"></a><span data-ttu-id="741b2-102">浏览数据（SQL Server 数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="741b2-102">Explore Data (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="741b2-103">![浏览数据向导](media/dmc-explore.gif "浏览数据向导")</span><span class="sxs-lookup"><span data-stu-id="741b2-103">![Explore Data wizard](media/dmc-explore.gif "Explore Data wizard")</span></span>  
  
 <span data-ttu-id="741b2-104">"**浏览数据**" 向导可帮助您了解数据表中数据的类型和数量。</span><span class="sxs-lookup"><span data-stu-id="741b2-104">The **Explore Data** wizard helps you understand the type and amount of data in your data table.</span></span> <span data-ttu-id="741b2-105">向导会将所选列的分布和值图形，一次一列。</span><span class="sxs-lookup"><span data-stu-id="741b2-105">The wizard graphs the distribution and values for the selected columns, one column at a time.</span></span> <span data-ttu-id="741b2-106">然后，您可尝试更改数据的分组方式，或将显示相应内容的图表复制到 Excel 工作簿中进行查看。</span><span class="sxs-lookup"><span data-stu-id="741b2-106">You can then experiment with changing the way that data is grouped, or copy the chart that shows the content to an Excel workbook for review.</span></span>  
  
 <span data-ttu-id="741b2-107">如果数据包含连续数值数据，可以在下面两种视图间切换：</span><span class="sxs-lookup"><span data-stu-id="741b2-107">If your data contains continuous numeric data, you can toggle between these two views:</span></span>  
  
-   <span data-ttu-id="741b2-108">**线图。**</span><span class="sxs-lookup"><span data-stu-id="741b2-108">**Line graph.**</span></span> <span data-ttu-id="741b2-109">此图对 X 轴上的数据值和 y 轴上的事例数进行了图表绘制。</span><span class="sxs-lookup"><span data-stu-id="741b2-109">This graph charts the data values on the X-axis and the number of cases on the y-axis.</span></span>  
  
-   <span data-ttu-id="741b2-110">**条形图。**</span><span class="sxs-lookup"><span data-stu-id="741b2-110">**Bar chart.**</span></span> <span data-ttu-id="741b2-111">条形图将值按照每个值的事例数进行分组。</span><span class="sxs-lookup"><span data-stu-id="741b2-111">This graph groups values by the number of cases for each value.</span></span>  
  
 <span data-ttu-id="741b2-112">当向导在数据中找到组时，它使用数据值的实际分布。</span><span class="sxs-lookup"><span data-stu-id="741b2-112">When the wizard finds groups in the data, it uses the actual distribution of data values.</span></span> <span data-ttu-id="741b2-113">因此，条形图不显示典型的整数数值轴标记，如 10 或 100。</span><span class="sxs-lookup"><span data-stu-id="741b2-113">Therefore, the bar chart does not show typical whole-number numeric axis markers such as 10 or 100.</span></span> <span data-ttu-id="741b2-114">条形图中所显示的范围可能会像 43521-55603 这样（对于“收入”列）。</span><span class="sxs-lookup"><span data-stu-id="741b2-114">Instead, the ranges shown in the bar chart might be something like 43521-55603 (for the Income column).</span></span>  
  
 <span data-ttu-id="741b2-115">如果要按其他范围分组数据，则应当在分析数据前在 Excel 中执行此操作。</span><span class="sxs-lookup"><span data-stu-id="741b2-115">If you want to group your data into other ranges, you should do this in Excel before analyzing the data.</span></span> <span data-ttu-id="741b2-116">或者，您可以使用重新[标记](relabel-sql-server-data-mining-add-ins.md)向导重新标记数据。</span><span class="sxs-lookup"><span data-stu-id="741b2-116">Or, you can relabel the data by using the [Relabel](relabel-sql-server-data-mining-add-ins.md) wizard.</span></span>  
  
## <a name="using-the-explore-data-wizard"></a><span data-ttu-id="741b2-117">使用浏览数据向导</span><span class="sxs-lookup"><span data-stu-id="741b2-117">Using the Explore Data Wizard</span></span>  
  
1.  <span data-ttu-id="741b2-118">在 "**数据挖掘**" 功能区中，单击 "**浏览数据**"。</span><span class="sxs-lookup"><span data-stu-id="741b2-118">In the **Data Mining** ribbon, click **Explore Data**.</span></span>  
  
2.  <span data-ttu-id="741b2-119">在 "**选择源**" 对话框中，选择包含您的数据的一个或一系列单元。</span><span class="sxs-lookup"><span data-stu-id="741b2-119">In the **Select Source** dialog box, select the table or range of cells that contains your data.</span></span>  
  
3.  <span data-ttu-id="741b2-120">在 "**选择列**" 对话框中，从窗格中显示的示例数据中选择要分析的列。</span><span class="sxs-lookup"><span data-stu-id="741b2-120">In the **Select Column** dialog box, choose the column to analyze, from the sample data displayed in the pane.</span></span>  
  
4.  <span data-ttu-id="741b2-121">在 "**浏览数据**" 对话框中，选择用于显示数据分布的图表类型。</span><span class="sxs-lookup"><span data-stu-id="741b2-121">In the **Explore Data** dialog box, choose the chart types for displaying the distribution of data.</span></span>  
  
5.  <span data-ttu-id="741b2-122">此外，可以向数据中添加新列、更改数据分段方式，或将图表复制到 Excel。</span><span class="sxs-lookup"><span data-stu-id="741b2-122">Optionally, you can add new columns to the data, change the way that the data is segmented, or copy the chart to Excel.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="741b2-123">要求</span><span class="sxs-lookup"><span data-stu-id="741b2-123">Requirements</span></span>  
 <span data-ttu-id="741b2-124">若要使用**浏览数据**向导，您的数据必须位于 Excel 数据表中。</span><span class="sxs-lookup"><span data-stu-id="741b2-124">To use the **Explore Data** wizard, your data must be in an Excel data table.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="741b2-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="741b2-125">See Also</span></span>  
 [<span data-ttu-id="741b2-126">数据挖掘准备清单</span><span class="sxs-lookup"><span data-stu-id="741b2-126">Checklist of Preparation for Data Mining</span></span>](checklist-of-preparation-for-data-mining.md)  
  
  
