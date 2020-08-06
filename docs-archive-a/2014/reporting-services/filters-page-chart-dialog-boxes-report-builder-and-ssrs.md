---
title: "\"筛选器\" 页、\"图表\" 对话框 (报表生成器和 SSRS) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.categorygroupproperties.filters.f1
- "10409"
- sql12.rtp.rptdesigner.seriesgroupproperties.filters.f1
- "10401"
- sql12.rtp.rptdesigner.chartproperties.filters.f1
- "10165"
ms.assetid: fab97b2f-d53f-42f2-900c-c159653d89ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 01d5054ce7d0c3e02d960885f149bd0ef209dc34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689796"
---
# <a name="filters-page-chart-dialog-boxes-report-builder-and-ssrs"></a><span data-ttu-id="22766-102">“筛选器”页 -&gt;“图表”对话框（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="22766-102">Filters page, Chart Dialog Boxes (Report Builder and SSRS)</span></span>
  <span data-ttu-id="22766-103">在以下对话框中单击 **“筛选器”** ：</span><span class="sxs-lookup"><span data-stu-id="22766-103">Click **Filters** in the:</span></span>  
  
-   <span data-ttu-id="22766-104">**“类别组属性”** 对话框：可以对已按类别分组的序列中的数据点进行筛选。</span><span class="sxs-lookup"><span data-stu-id="22766-104">**Category Group Properties** dialog box to filter data points in a series that has been grouped by category.</span></span>  
  
-   <span data-ttu-id="22766-105">**“图表属性”** 对话框：可以定义图表的筛选选项。</span><span class="sxs-lookup"><span data-stu-id="22766-105">**Chart Properties** dialog box to define filtering options for the chart.</span></span>  
  
-   <span data-ttu-id="22766-106">**“序列组属性”** 对话框：可以限制所选组中的序列数。</span><span class="sxs-lookup"><span data-stu-id="22766-106">**Series Group Properties** dialog box to limit the number of series in the selected group.</span></span>  
  
## <a name="options"></a><span data-ttu-id="22766-107">选项</span><span class="sxs-lookup"><span data-stu-id="22766-107">Options</span></span>  
 <span data-ttu-id="22766-108">**添加**</span><span class="sxs-lookup"><span data-stu-id="22766-108">**Add**</span></span>  
 <span data-ttu-id="22766-109">单击此选项可向列表中添加新的筛选子句。</span><span class="sxs-lookup"><span data-stu-id="22766-109">Click to add a new filter clause to the list.</span></span>  
  
 <span data-ttu-id="22766-110">**删除**</span><span class="sxs-lookup"><span data-stu-id="22766-110">**Delete**</span></span>  
 <span data-ttu-id="22766-111">单击此选项可从列表中删除选定的筛选子句。</span><span class="sxs-lookup"><span data-stu-id="22766-111">Click to delete the selected filter clause from the list.</span></span>  
  
 <span data-ttu-id="22766-112">**向上键**</span><span class="sxs-lookup"><span data-stu-id="22766-112">**Up arrow**</span></span>  
 <span data-ttu-id="22766-113">单击此选项可在列表中向上移动所选的筛选器。</span><span class="sxs-lookup"><span data-stu-id="22766-113">Click to move the selected filter up in the list.</span></span>  
  
 <span data-ttu-id="22766-114">**向下键**</span><span class="sxs-lookup"><span data-stu-id="22766-114">**Down arrow**</span></span>  
 <span data-ttu-id="22766-115">单击此选项可在列表中向下移动所选的筛选器。</span><span class="sxs-lookup"><span data-stu-id="22766-115">Click to move the selected filter down in the list.</span></span>  
  
 <span data-ttu-id="22766-116">**表达式**</span><span class="sxs-lookup"><span data-stu-id="22766-116">**Expression**</span></span>  
 <span data-ttu-id="22766-117">键入或选择要对其应用筛选器的表达式。</span><span class="sxs-lookup"><span data-stu-id="22766-117">Type or choose the expression to which you want to apply a filter.</span></span> <span data-ttu-id="22766-118">单击“表达式” (**fx**) 按钮可编辑表达式。</span><span class="sxs-lookup"><span data-stu-id="22766-118">Click the Expression (**fx**) button to edit the expression.</span></span>  
  
 <span data-ttu-id="22766-119">**Data type**</span><span class="sxs-lookup"><span data-stu-id="22766-119">**Data type**</span></span>  
 <span data-ttu-id="22766-120">为“值”\*\*\*\* 选择数据类型。</span><span class="sxs-lookup"><span data-stu-id="22766-120">Choose the data type for **Value**.</span></span> <span data-ttu-id="22766-121">如果可能，请选择与 **“表达式”** 的数据类型匹配的数据类型。</span><span class="sxs-lookup"><span data-stu-id="22766-121">When possible, choose a data type that matches the data type for **Expression**.</span></span>  
  
 <span data-ttu-id="22766-122">**“表达式”** 和 **“值”** 中的值的计算结果必须属于同一数据类型。</span><span class="sxs-lookup"><span data-stu-id="22766-122">The values in **Expression** and **Value** must evaluate to the same data type.</span></span> <span data-ttu-id="22766-123">例如，如果“表达式”设置为具有数据类型 System.Int32 的字段并且“值”设置为 7，则从下拉列表中选择 **Integer**。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="22766-123">For example, if **Expression** is set to a field that has the data type System.Int32 and **Value** is set to 7, from the drop-down list, choose **Integer**.</span></span>  
  
 <span data-ttu-id="22766-124">如果您需要的数据类型选项不在下拉列表中，请编写表达式将该值转换成正确的数据类型。</span><span class="sxs-lookup"><span data-stu-id="22766-124">If the data type option you need is not in the drop-down list, write an expression to convert the value to the correct data type.</span></span> <span data-ttu-id="22766-125">有关详细信息，请参阅[筛选器公式示例（报表生成器和 SSRS）](report-design/filter-equation-examples-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="22766-125">For more information, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](report-design/filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="22766-126">**“运算符”**</span><span class="sxs-lookup"><span data-stu-id="22766-126">**Operator**</span></span>  
 <span data-ttu-id="22766-127">选择要用于比较表达式和值的运算符。</span><span class="sxs-lookup"><span data-stu-id="22766-127">Choose the operator to use to compare the expression and the value.</span></span>  
  
 <span data-ttu-id="22766-128">**值**</span><span class="sxs-lookup"><span data-stu-id="22766-128">**Value**</span></span>  
 <span data-ttu-id="22766-129">键入对“表达式”中的表达式进行计算时所依据的表达式或值。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="22766-129">Type the expression or value against which to evaluate the expression in **Expression**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22766-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="22766-130">See Also</span></span>  
 <span data-ttu-id="22766-131">[添加数据集筛选器、数据区域筛选器和组筛选器 &#40;报表生成器和 SSRS&#41;](report-design/add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="22766-131">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](report-design/add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="22766-132">[表达式示例（报表生成器和 SSRS）](report-design/expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="22766-132">[Expression Examples &#40;Report Builder and SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="22766-133">[表达式（报表生成器和 SSRS）](report-design/expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="22766-133">[Expressions &#40;Report Builder and SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="22766-134">对数据进行筛选、分组和排序（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="22766-134">Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;</span></span>](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
