---
title: "\"数据集属性\" 对话框-> \"筛选器\" (报表生成器) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10025"
ms.assetid: 933a6f44-4eb7-4e73-9c40-ac0fd17b23d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7bc13b0eeff1eaf27fb0ec0c4279ff00d0809e4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578728"
---
# <a name="dataset-properties-dialog-box-filters-report-builder"></a><span data-ttu-id="47f68-102">“数据集属性”对话框 -&gt;“筛选器”（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="47f68-102">Dataset Properties Dialog Box, Filters (Report Builder)</span></span>
  <span data-ttu-id="47f68-103">在 **“数据集属性”** 对话框中选择 **“筛选器”** 可创建数据集的筛选器。</span><span class="sxs-lookup"><span data-stu-id="47f68-103">Select **Filters** on the **Dataset Properties** dialog box to create filters for the dataset.</span></span>  
  
 <span data-ttu-id="47f68-104">作为报表服务器上共享数据集定义一部分的筛选器会影响使用此共享数据集的所有报表。</span><span class="sxs-lookup"><span data-stu-id="47f68-104">Filters that are part of a shared dataset definition on the report server affect all reports that use the shared dataset.</span></span> <span data-ttu-id="47f68-105">在将共享数据集添加到报表后，可以为其指定其他筛选器。</span><span class="sxs-lookup"><span data-stu-id="47f68-105">Additional filters for the shared dataset can be specified after it is added to a report.</span></span> <span data-ttu-id="47f68-106">这些筛选器只会影响在其中定义它们的报表。</span><span class="sxs-lookup"><span data-stu-id="47f68-106">These filters affect only the report in which they are defined.</span></span>  
  
 <span data-ttu-id="47f68-107">嵌入数据集的筛选器只会影响在其中定义它们的报表。</span><span class="sxs-lookup"><span data-stu-id="47f68-107">Filters for an embedded dataset affect only the report in which they are defined.</span></span>  
  
 <span data-ttu-id="47f68-108">有关详细信息，请参阅 [对数据进行筛选、分组和排序（报表生成器和 SSRS）](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="47f68-108">For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="47f68-109">选项</span><span class="sxs-lookup"><span data-stu-id="47f68-109">Options</span></span>  
 <span data-ttu-id="47f68-110">**添加**</span><span class="sxs-lookup"><span data-stu-id="47f68-110">**Add**</span></span>  
 <span data-ttu-id="47f68-111">向列表中添加新的筛选子句。</span><span class="sxs-lookup"><span data-stu-id="47f68-111">Add a new filter clause to the list.</span></span>  
  
 <span data-ttu-id="47f68-112">**删除**</span><span class="sxs-lookup"><span data-stu-id="47f68-112">**Delete**</span></span>  
 <span data-ttu-id="47f68-113">从列表中删除选定的筛选子句。</span><span class="sxs-lookup"><span data-stu-id="47f68-113">Delete the selected filter clause from the list.</span></span>  
  
 <span data-ttu-id="47f68-114">**向上键**</span><span class="sxs-lookup"><span data-stu-id="47f68-114">**Up arrow**</span></span>  
 <span data-ttu-id="47f68-115">在列表中向上移动所选的筛选器。</span><span class="sxs-lookup"><span data-stu-id="47f68-115">Move the selected filter up in the list.</span></span>  
  
 <span data-ttu-id="47f68-116">**向下键**</span><span class="sxs-lookup"><span data-stu-id="47f68-116">**Down arrow**</span></span>  
 <span data-ttu-id="47f68-117">在列表中向下移动所选的筛选器。</span><span class="sxs-lookup"><span data-stu-id="47f68-117">Move the selected filter down in the list</span></span>  
  
 <span data-ttu-id="47f68-118">**表达式**</span><span class="sxs-lookup"><span data-stu-id="47f68-118">**Expression**</span></span>  
 <span data-ttu-id="47f68-119">键入或选择要对其应用筛选器的表达式。</span><span class="sxs-lookup"><span data-stu-id="47f68-119">Type or choose the expression to which you want to apply a filter.</span></span> <span data-ttu-id="47f68-120">单击“表达式” (**fx**) 按钮可编辑表达式。</span><span class="sxs-lookup"><span data-stu-id="47f68-120">Click the Expression (**fx**) button to edit the expression.</span></span>  
  
 <span data-ttu-id="47f68-121">**Data type**</span><span class="sxs-lookup"><span data-stu-id="47f68-121">**Data type**</span></span>  
 <span data-ttu-id="47f68-122">为“值”\*\*\*\* 选择数据类型。</span><span class="sxs-lookup"><span data-stu-id="47f68-122">Choose the data type for **Value**.</span></span> <span data-ttu-id="47f68-123">如果可能，请选择与 **“表达式”** 的数据类型匹配的数据类型。</span><span class="sxs-lookup"><span data-stu-id="47f68-123">When possible, choose a data type that matches the data type for **Expression**.</span></span>  
  
 <span data-ttu-id="47f68-124">**“表达式”** 和 **“值”** 中的值的计算结果必须属于同一数据类型。</span><span class="sxs-lookup"><span data-stu-id="47f68-124">The values in **Expression** and **Value** must evaluate to the same data type.</span></span> <span data-ttu-id="47f68-125">例如，如果“表达式”设置为具有数据类型 System.Int32 的字段并且“值”设置为 7，则从下拉列表中选择 **Integer**。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="47f68-125">For example, if **Expression** is set to a field that has the data type System.Int32 and **Value** is set to 7, from the drop-down list, choose **Integer**.</span></span>  
  
 <span data-ttu-id="47f68-126">如果您需要的数据类型选项不在下拉列表中，请编写表达式将该值转换成正确的数据类型。</span><span class="sxs-lookup"><span data-stu-id="47f68-126">If the data type option you need is not in the drop-down list, write an expression to convert the value to the correct data type.</span></span> <span data-ttu-id="47f68-127">有关详细信息，请参阅[筛选器公式示例（报表生成器和 SSRS）](report-design/filter-equation-examples-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="47f68-127">For more information, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](report-design/filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="47f68-128">**“运算符”**</span><span class="sxs-lookup"><span data-stu-id="47f68-128">**Operator**</span></span>  
 <span data-ttu-id="47f68-129">选择要用于比较表达式和值的运算符。</span><span class="sxs-lookup"><span data-stu-id="47f68-129">Choose the operator to use to compare the expression and the value.</span></span>  
  
 <span data-ttu-id="47f68-130">**值**</span><span class="sxs-lookup"><span data-stu-id="47f68-130">**Value**</span></span>  
 <span data-ttu-id="47f68-131">键入在计算“表达式”\*\*\*\* 框中所指定的表达式时要使用的表达式或值。</span><span class="sxs-lookup"><span data-stu-id="47f68-131">Type the expression or value to use when evaluating the expression specified in the **Expression** box.</span></span> <span data-ttu-id="47f68-132">单击“表达式” (**fx**) 按钮可编辑表达式。</span><span class="sxs-lookup"><span data-stu-id="47f68-132">Click the Expression (**fx**) button to edit the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47f68-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="47f68-133">See Also</span></span>  
 <span data-ttu-id="47f68-134">[报表嵌入数据集和共享数据集 &#40;报表生成器和 SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="47f68-134">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="47f68-135">[报表参数 &#40;报表生成器和报表设计器&#41;](report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="47f68-135">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="47f68-136">[向数据集添加筛选器 &#40;报表生成器和 SSRS&#41;](report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="47f68-136">[Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;](report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="47f68-137">在报表中使用表达式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="47f68-137">Expression Uses in Reports &#40;Report Builder and SSRS&#41;</span></span>](report-design/expression-uses-in-reports-report-builder-and-ssrs.md)  
  
  
