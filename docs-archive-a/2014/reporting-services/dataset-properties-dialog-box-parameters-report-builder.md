---
title: "\"数据集属性\" 对话框-\"参数\" (报表生成器) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10023"
ms.assetid: 3a0672ad-c969-455b-b952-585164ce1dda
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ef038e7cbf113556b11af9a0e6c59aa190b2400b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591141"
---
# <a name="dataset-properties-dialog-box-parameters-report-builder"></a><span data-ttu-id="3f7b9-102">“数据集属性”对话框 -&gt;“参数”（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="3f7b9-102">Dataset Properties Dialog Box, Parameters (Report Builder)</span></span>
  <span data-ttu-id="3f7b9-103">选择 "**数据集属性**" 对话框中的 "**参数**" 可以添加、更改和删除查询参数。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-103">Select **Parameters** on the **Dataset Properties** dialog box to add, change, and delete query parameters.</span></span>  
  
 <span data-ttu-id="3f7b9-104">对于嵌入数据集，选项应用于报表定义中的数据集。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-104">For an embedded dataset, options apply to the dataset in the report definition.</span></span>  
  
 <span data-ttu-id="3f7b9-105">对于共享数据集，选项应用于报表服务器上的共享数据集定义。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-105">For a shared dataset, options apply to the shared dataset definition on the report server.</span></span>  
  
 <span data-ttu-id="3f7b9-106">有关详细信息，请参阅[嵌入数据集和共享数据集（报表生成器和 SSRS）](report-data/embedded-and-shared-datasets-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-106">For more information, see [Embedded and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/embedded-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="3f7b9-107">选项</span><span class="sxs-lookup"><span data-stu-id="3f7b9-107">Options</span></span>  
 <span data-ttu-id="3f7b9-108">**添加**</span><span class="sxs-lookup"><span data-stu-id="3f7b9-108">**Add**</span></span>  
 <span data-ttu-id="3f7b9-109">将新的参数添加到列表。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-109">Add a new parameter to the list.</span></span>  
  
 <span data-ttu-id="3f7b9-110">**删除**</span><span class="sxs-lookup"><span data-stu-id="3f7b9-110">**Delete**</span></span>  
 <span data-ttu-id="3f7b9-111">从列表中删除所选参数。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-111">Remove the selected parameter from the list.</span></span>  
  
 <span data-ttu-id="3f7b9-112">**向上键**</span><span class="sxs-lookup"><span data-stu-id="3f7b9-112">**Up arrow**</span></span>  
 <span data-ttu-id="3f7b9-113">在列表中向上移动所选的参数。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-113">Move the selected parameter up in the list.</span></span>  
  
 <span data-ttu-id="3f7b9-114">**向下键**</span><span class="sxs-lookup"><span data-stu-id="3f7b9-114">**Down arrow**</span></span>  
 <span data-ttu-id="3f7b9-115">在列表中向下移动所选的参数。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-115">Move the selected parameter down in the list.</span></span>  
  
 <span data-ttu-id="3f7b9-116">**参数名称**</span><span class="sxs-lookup"><span data-stu-id="3f7b9-116">**Parameter name**</span></span>  
 <span data-ttu-id="3f7b9-117">键入添加到“数据集属性”\*\*\*\* 对话框“查询”\*\*\*\* 选项卡上数据集中的查询参数的名称。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-117">Type the name of a query parameter that you added to the dataset on the **Query** tab of the **Dataset Properties** dialog box.</span></span>  
  
 <span data-ttu-id="3f7b9-118">**参数值**</span><span class="sxs-lookup"><span data-stu-id="3f7b9-118">**Parameter value**</span></span>  
 <span data-ttu-id="3f7b9-119">仅限嵌入数据集。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-119">For embedded datasets only.</span></span>  
  
 <span data-ttu-id="3f7b9-120">输入查询参数的值。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-120">Enter a value for the query parameter.</span></span> <span data-ttu-id="3f7b9-121">此值既可以是静态值，也可以是引用报表内对象的表达式（但不能引用任何报表项或字段）。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-121">This can be a static value or an expression that refers to an object within the report, but it cannot refer to any report items or fields.</span></span> <span data-ttu-id="3f7b9-122">默认情况下， **“值”** 中包含指向报表参数的表达式。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-122">By default, **Value** contains an expression that points to a report parameter.</span></span>  
  
 <span data-ttu-id="3f7b9-123">**默认值**</span><span class="sxs-lookup"><span data-stu-id="3f7b9-123">**Default value**</span></span>  
 <span data-ttu-id="3f7b9-124">仅限共享数据集。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-124">For shared datasets only.</span></span>  
  
 <span data-ttu-id="3f7b9-125">选中此复选框可以指定默认值。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-125">Select the check box to specify a default value.</span></span>  
  
 <span data-ttu-id="3f7b9-126">输入默认值。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-126">Enter a default value.</span></span> <span data-ttu-id="3f7b9-127">该值可以是静态值或引用报表中的对象的表达式。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-127">This can be a static value or an expression that refers to an object within the report.</span></span> <span data-ttu-id="3f7b9-128">该表达式不能引用报表项、报表参数或字段。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-128">The expression cannot refer to report items, report parameters, or fields.</span></span>  
  
 <span data-ttu-id="3f7b9-129">若要指定空白，请将文本框保留为空。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-129">To specify a blank, leave the text box empty.</span></span>  
  
 <span data-ttu-id="3f7b9-130">若要指定 Null，请选择“可以为 Null”选项。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-130">To specify a null, select the Nullable option.</span></span>  
  
 <span data-ttu-id="3f7b9-131">**只读**</span><span class="sxs-lookup"><span data-stu-id="3f7b9-131">**Read Only**</span></span>  
 <span data-ttu-id="3f7b9-132">仅限共享数据集。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-132">For shared datasets only.</span></span>  
  
 <span data-ttu-id="3f7b9-133">选择此选项可在共享数据集定义中将此参数标记为只读。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-133">Select this option to mark this parameter read only in the shared dataset definition.</span></span> <span data-ttu-id="3f7b9-134">在将共享数据集添加到报表时，该参数不出现在属性中。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-134">When the shared dataset is added to a report, the parameter does not appear in the properties.</span></span> <span data-ttu-id="3f7b9-135">在报表服务器上缓存共享数据集时，不能更改该值。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-135">When the shared dataset is cached on the report server, the value cannot be changed.</span></span>  
  
 <span data-ttu-id="3f7b9-136">**可以为 Null**</span><span class="sxs-lookup"><span data-stu-id="3f7b9-136">**Nullable**</span></span>  
 <span data-ttu-id="3f7b9-137">仅限共享数据集。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-137">For shared datasets only.</span></span>  
  
 <span data-ttu-id="3f7b9-138">选择此选项可允许 Null 值。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-138">Select this option to allow a null value.</span></span>  
  
 <span data-ttu-id="3f7b9-139">**从查询中省略**</span><span class="sxs-lookup"><span data-stu-id="3f7b9-139">**Omit From Query**</span></span>  
 <span data-ttu-id="3f7b9-140">仅限共享数据集。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-140">For shared datasets only.</span></span>  
  
 <span data-ttu-id="3f7b9-141">当对报表参数的引用位于共享数据集筛选器的表达式中而非查询中时，选择此选项。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-141">Select this option when a reference to a report parameter is in an expression in the shared dataset filter and not in the query.</span></span> <span data-ttu-id="3f7b9-142">在您选择此选项后，无需在查询运行时为此参数指定默认值。</span><span class="sxs-lookup"><span data-stu-id="3f7b9-142">When you select this option, you do not need to specify a default value for this parameter when the query runs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f7b9-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3f7b9-143">See Also</span></span>  
 <span data-ttu-id="3f7b9-144">[报表生成器对话框、窗格和向导的帮助](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="3f7b9-144">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="3f7b9-145">["数据集属性" 对话框-> "查询 &#40;报表生成器&#41;](report-data/dataset-properties-dialog-box-query-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="3f7b9-145">[Dataset Properties Dialog Box, Query &#40;Report Builder&#41;](report-data/dataset-properties-dialog-box-query-report-builder.md) </span></span>  
 <span data-ttu-id="3f7b9-146">[表达式（报表生成器和 SSRS）](report-design/expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3f7b9-146">[Expressions &#40;Report Builder and SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3f7b9-147">[教程：向报表添加参数 &#40;报表生成器&#41;](tutorial-add-a-parameter-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="3f7b9-147">[Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](tutorial-add-a-parameter-to-your-report-report-builder.md) </span></span>  
 <span data-ttu-id="3f7b9-148">[报表参数 &#40;报表生成器和报表设计器&#41;](report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="3f7b9-148">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="3f7b9-149">[报表嵌入数据集和共享数据集 &#40;报表生成器和 SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3f7b9-149">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3f7b9-150">[查询设计器 &#40;报表生成器&#41;](../../2014/reporting-services/query-designers-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="3f7b9-150">[Query Designers &#40;Report Builder&#41;](../../2014/reporting-services/query-designers-report-builder.md) </span></span>  
 <span data-ttu-id="3f7b9-151">[报表嵌入数据集和共享数据集 &#40;报表生成器和 SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3f7b9-151">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="3f7b9-152">创建共享数据集或嵌入数据集（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="3f7b9-152">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
  
