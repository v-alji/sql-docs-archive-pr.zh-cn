---
title: 添加、更改或删除报表参数 (报表生成器和 SSRS) 的默认值 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10460"
- sql12.rtp.rptdesigner.reportparameters.defaultvalues.f1
- "10072"
ms.assetid: 6a87e069-b3a9-47b6-bcec-afcdd8aff65f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1d50fdbbe42a656ef839785c0968b36c8c829e11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586460"
---
# <a name="add-change-or-delete-default-values-for-a-report-parameter-report-builder-and-ssrs"></a><span data-ttu-id="7ce0a-102">为报表参数添加、更改或删除默认值（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="7ce0a-102">Add, Change, or Delete Default Values for a Report Parameter (Report Builder and SSRS)</span></span>
  <span data-ttu-id="7ce0a-103">创建报表参数后，您可以提供一个默认值列表。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-103">After you create a report parameter, you can provide a list of default values.</span></span> <span data-ttu-id="7ce0a-104">如果所有参数都有有效默认值，报表会在您第一次查看或预览它时自动运行。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-104">If all parameters have a valid default value, the report runs automatically when you first view or preview it.</span></span>  
  
 <span data-ttu-id="7ce0a-105">报表参数可以是单值参数或多值参数。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-105">Report parameters can represent one value or multiple values.</span></span> <span data-ttu-id="7ce0a-106">对于单值参数，可以提供一个文字或表达式。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-106">For single values, you can provide a literal or expression.</span></span> <span data-ttu-id="7ce0a-107">对于多值参数，可以提供静态值列表或者来自报表数据集的列表。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-107">For multiple values, you can provide a static list or a list from a report dataset.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="7ce0a-108">在您发布某一报表后，您可以通过对报表服务器设置参数属性值，在报表创作工具中覆盖在报表中定义的默认值。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-108">After you publish a report, you can override the default values that you define in the report in the report authoring tool, by setting parameter property values on the report server.</span></span> <span data-ttu-id="7ce0a-109">您还可以通过创建链接报表，提供多组默认参数值。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-109">You can also provide multiple sets of default parameter values by creating linked reports.</span></span> <span data-ttu-id="7ce0a-110">有关详细信息，请参阅  [报表参数（报表生成器和报表设计器）](report-parameters-report-builder-and-report-designer.md)</span><span class="sxs-lookup"><span data-stu-id="7ce0a-110">For more information, see  [Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md)</span></span>  
  
### <a name="to-add-or-change-the-default-values-for-a-report-parameter"></a><span data-ttu-id="7ce0a-111">添加或更改报表参数的默认值</span><span class="sxs-lookup"><span data-stu-id="7ce0a-111">To add or change the default values for a report parameter</span></span>  
  
1.  <span data-ttu-id="7ce0a-112">在“报表数据”窗格中，展开 **“参数”** 节点。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-112">In the Report Data pane, expand the **Parameters** node.</span></span> <span data-ttu-id="7ce0a-113">右键单击该参数，然后单击“编辑”  。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-113">Right-click the parameter and click **Edit**.</span></span> <span data-ttu-id="7ce0a-114">此时将打开 **“报表参数属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-114">The **Report Parameter Properties** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7ce0a-115">如果“报表数据”窗格不可见，请单击“视图”，然后单击“报表数据”   。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-115">If the Report Data pane is not visible, click **View** and then click **Report Data**.</span></span>  
  
2.  <span data-ttu-id="7ce0a-116">单击 **“默认值”** 。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-116">Click **Default Values**.</span></span>  
  
3.  <span data-ttu-id="7ce0a-117">选择一个默认选项：</span><span class="sxs-lookup"><span data-stu-id="7ce0a-117">Select a default option:</span></span>  
  
    -   <span data-ttu-id="7ce0a-118">若要手动提供一个值或值列表，请单击 **“指定值”** 。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-118">To manually provide a value or list of values, click **Specify values**.</span></span> <span data-ttu-id="7ce0a-119">单击 **“添加”** ，然后在 **“值”** 文本框中输入值。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-119">Click **Add** and then enter the value in the **Value** text box.</span></span> <span data-ttu-id="7ce0a-120">您可以为值编写表达式。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-120">You can write an expression for a value.</span></span> <span data-ttu-id="7ce0a-121">数据类型必须与参数的数据类型相匹配。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-121">The data type must match the data type of the parameter.</span></span> <span data-ttu-id="7ce0a-122">字段名称不能用于参数的表达式中。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-122">Field names cannot be used in an expression for a parameter.</span></span>  
  
         <span data-ttu-id="7ce0a-123">对于多值参数，对每个要提供的值重复此步骤。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-123">For multivalue parameters, repeat this step for as many values as you want to provide.</span></span> <span data-ttu-id="7ce0a-124">您在此列表中看到的项的顺序将决定用户在下拉列表中看到这些项的顺序。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-124">The order of items you see in this list determines the order that the user sees them in the drop-down list.</span></span> <span data-ttu-id="7ce0a-125">若要更改列表中某一项的顺序，单击 **“值”** 文本框选择该项，然后使用上箭头或下箭头按钮在列表中上下移动该项。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-125">To change the order of an item in the list, click the **Value** text box to select the item, and then use the up and down arrow buttons to move the item higher or lower in the list.</span></span>  
  
    -   <span data-ttu-id="7ce0a-126">若要提供检索值的现有数据集的名称，请单击 **“从查询中获取值”** 。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-126">To provide the name of an existing dataset that retrieves the values, click **Get values from a query**.</span></span> <span data-ttu-id="7ce0a-127">在 **“数据集”** 中，选择该数据集的名称。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-127">In **Dataset**, choose the name of the dataset.</span></span>  
  
         <span data-ttu-id="7ce0a-128">在 **“值字段”** 中，选择提供参数值的字段的名称。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-128">In **Value field**, choose the name of the field that provides parameter values.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-remove-the-default-values-for-a-report-parameter"></a><span data-ttu-id="7ce0a-129">删除报表参数的默认值</span><span class="sxs-lookup"><span data-stu-id="7ce0a-129">To remove the default values for a report parameter</span></span>  
  
1.  <span data-ttu-id="7ce0a-130">在“报表数据”窗格中，展开 **“参数”** 节点。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-130">In the Report Data pane, expand the **Parameters** node.</span></span> <span data-ttu-id="7ce0a-131">右键单击该参数，然后单击“编辑”  。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-131">Right-click the parameter and click **Edit**.</span></span> <span data-ttu-id="7ce0a-132">此时将打开 **“报表参数属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-132">The **Report Parameter Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="7ce0a-133">单击 **“默认值”** 。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-133">Click **Default Values**.</span></span>  
  
3.  <span data-ttu-id="7ce0a-134">在 **“选择以下选项之一”** 中，单击 **“无默认值”** 。</span><span class="sxs-lookup"><span data-stu-id="7ce0a-134">In **Select from one of the following options**, click **No default value**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7ce0a-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7ce0a-135">See Also</span></span>  
 <span data-ttu-id="7ce0a-136">[报表参数（报表生成器和报表设计器）](report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="7ce0a-136">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="7ce0a-137">[向报表添加级联参数（报表生成器和 SSRS）](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7ce0a-137">[Add Cascading Parameters to a Report &#40;Report Builder and SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7ce0a-138">[教程：向报表添加参数（报表生成器）](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="7ce0a-138">[Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span></span>  
 <span data-ttu-id="7ce0a-139">[添加数据集筛选器、数据区域筛选器和组筛选器（报表生成器和 SSRS）](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="7ce0a-139">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="7ce0a-140">[参数集合引用（报表生成器和 SSRS）](built-in-collections-parameters-collection-references-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="7ce0a-140">[Parameters Collection References &#40;Report Builder and SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md) </span></span>  
 <span data-ttu-id="7ce0a-141">[更改报表参数的顺序（报表生成器和 SSRS）](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7ce0a-141">[Change the Order of a Report Parameter &#40;Report Builder and SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7ce0a-142">[添加、更改或删除报表参数（报表生成器和 SSRS）](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7ce0a-142">[Add, Change, or Delete a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="7ce0a-143">表达式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="7ce0a-143">Expressions &#40;Report Builder and SSRS&#41;</span></span>](expressions-report-builder-and-ssrs.md)  
  
  
