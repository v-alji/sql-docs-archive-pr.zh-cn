---
title: 添加、更改或删除报表参数的可用值 (报表生成器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.reportparameters.availablevalues.f1
- "10455"
- "10071"
ms.assetid: 0e03264c-523f-4c59-b71b-ceef600f75f6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 985ab3e8dc1d74f94e7242ff57f46ffe4fba9586
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586454"
---
# <a name="add-change-or-delete-available-values-for-a-report-parameter-report-builder-and-ssrs"></a><span data-ttu-id="75608-102">为报表参数添加、更改或删除可用值（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="75608-102">Add, Change, or Delete Available Values for a Report Parameter (Report Builder and SSRS)</span></span>
  <span data-ttu-id="75608-103">创建报表参数后，可以指定向用户显示的可用值列表。</span><span class="sxs-lookup"><span data-stu-id="75608-103">After you create a report parameter, you can specify a list of available values to display to the user.</span></span> <span data-ttu-id="75608-104">可用值列表将限制用户只能选择参数的有效值。</span><span class="sxs-lookup"><span data-stu-id="75608-104">An available values list limits the choices a user can make to only valid values for the parameter.</span></span>  
  
 <span data-ttu-id="75608-105">报表运行时，可用值会显示在工具栏中报表参数旁的下拉列表中。</span><span class="sxs-lookup"><span data-stu-id="75608-105">Available values appear in a drop-down list next to the report parameter on the toolbar when the report runs.</span></span> <span data-ttu-id="75608-106">报表参数可以是单值参数或多值参数。</span><span class="sxs-lookup"><span data-stu-id="75608-106">Report parameters can represent one value or multiple values.</span></span> <span data-ttu-id="75608-107">对于多值参数，列表的顶部具有一个 **“全选”** 功能，因此用户只需一次单击即可选中或取消选中所有值。</span><span class="sxs-lookup"><span data-stu-id="75608-107">For multiple values, the top of list begins with a **Select All** feature so the user can select or clear all values with a single click.</span></span>  
  
 <span data-ttu-id="75608-108">您可以提供静态值列表或来自报表数据集的值列表。</span><span class="sxs-lookup"><span data-stu-id="75608-108">You can provide a static list of values or a list from a report dataset.</span></span> <span data-ttu-id="75608-109">还可以通过指定标签字段为这些值提供友好名称。</span><span class="sxs-lookup"><span data-stu-id="75608-109">You can optionally provide a friendly name for values by specifying a label field.</span></span> <span data-ttu-id="75608-110">例如，对于基于 `ProductID` 字段的参数，可以在参数标签中显示 `ProductName` 字段。</span><span class="sxs-lookup"><span data-stu-id="75608-110">For example, for a parameter based on a `ProductID` field, you can display the `ProductName` field in the parameter label.</span></span> <span data-ttu-id="75608-111">报表运行时，用户可以从产品名称中进行选择，但是实际选定的值为相应的 `ProductID`。</span><span class="sxs-lookup"><span data-stu-id="75608-111">When the report runs, the user can choose from the product names, but the actual chosen value is the corresponding `ProductID`.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="75608-112">在您发布某一报表后，您可以通过对报表服务器设置参数属性值，在报表创作工具中覆盖在报表中定义的可用值。</span><span class="sxs-lookup"><span data-stu-id="75608-112">After you publish a report, you can override the available values that you define in the report in the report authoring tool, by setting parameter property values on the report server.</span></span> <span data-ttu-id="75608-113">有关详细信息，请参阅 [报表参数（报表生成器和报表设计器）](report-parameters-report-builder-and-report-designer.md)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="75608-113">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md).</span></span>  
  
### <a name="to-add-or-change-the-available-values-for-a-report-parameter"></a><span data-ttu-id="75608-114">添加或更改报表参数的可用值</span><span class="sxs-lookup"><span data-stu-id="75608-114">To add or change the available values for a report parameter</span></span>  
  
1.  <span data-ttu-id="75608-115">在“报表数据”窗格中，展开“参数”节点。</span><span class="sxs-lookup"><span data-stu-id="75608-115">In the Report Data pane, expand the Parameters node.</span></span> <span data-ttu-id="75608-116">右键单击该参数，然后单击“参数属性”  。</span><span class="sxs-lookup"><span data-stu-id="75608-116">Right-click the parameter and click **Parameter Properties**.</span></span> <span data-ttu-id="75608-117">此时将打开 **“报表参数属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="75608-117">The **Report Parameter Properties** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="75608-118">如果“报表数据”窗格不可见，请单击“视图”，然后单击“报表数据”   。</span><span class="sxs-lookup"><span data-stu-id="75608-118">If the Report Data pane is not visible, click **View** and then click **Report Data**.</span></span>  
  
2.  <span data-ttu-id="75608-119">单击 **“可用值”** 。</span><span class="sxs-lookup"><span data-stu-id="75608-119">Click **Available Values**.</span></span> <span data-ttu-id="75608-120">选择可用值选项：</span><span class="sxs-lookup"><span data-stu-id="75608-120">Select an available values option:</span></span>  
  
    -   <span data-ttu-id="75608-121">单击“指定值”可手动提供值列表，还可以为值提供友好名称（标签）  。</span><span class="sxs-lookup"><span data-stu-id="75608-121">Click **Specify values** to manually provide a list of values, and optionally, friendly names (the labels) for the values.</span></span>  
  
         <span data-ttu-id="75608-122">单击 **“添加”** ，然后在 **“值”** 文本框中输入值，或在 **“标签”** 文本框中输入标签。</span><span class="sxs-lookup"><span data-stu-id="75608-122">Click **Add** and then enter the value in the **Value** text box, and optionally, the label in the **Label** text box.</span></span> <span data-ttu-id="75608-123">如果不提供标签，将使用输入的值。</span><span class="sxs-lookup"><span data-stu-id="75608-123">If you do not provide a label, the value is used.</span></span> <span data-ttu-id="75608-124">您可以为值编写表达式。</span><span class="sxs-lookup"><span data-stu-id="75608-124">You can write an expression for a value.</span></span> <span data-ttu-id="75608-125">数据类型必须与参数的数据类型相匹配。</span><span class="sxs-lookup"><span data-stu-id="75608-125">The data type must match the data type of the parameter.</span></span> <span data-ttu-id="75608-126">字段名称不能用于参数的表达式中。</span><span class="sxs-lookup"><span data-stu-id="75608-126">Field names cannot be used in an expression for a parameter.</span></span> <span data-ttu-id="75608-127">有关示例，请参阅[常用筛选器（报表生成器和 SSRS）](commonly-used-filters-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="75608-127">For examples, see [Commonly Used Filters &#40;Report Builder and SSRS&#41;](commonly-used-filters-report-builder-and-ssrs.md).</span></span>  
  
         <span data-ttu-id="75608-128">为要提供的每个值重复此步骤。</span><span class="sxs-lookup"><span data-stu-id="75608-128">Repeat this step for as many values as you want to provide.</span></span> <span data-ttu-id="75608-129">您在此列表中看到的项的顺序将决定用户在下拉列表中看到这些项的顺序。</span><span class="sxs-lookup"><span data-stu-id="75608-129">The order of items you see in this list determines the order that the user sees them in the drop-down list.</span></span> <span data-ttu-id="75608-130">若要更改列表中某一项的顺序，请单击 **“值”** 或 **“标签”** 文本框选择该项，然后使用向上箭头或向下箭头按钮在列表中上下移动该项。</span><span class="sxs-lookup"><span data-stu-id="75608-130">To change the order of an item in the list, click a **Value** or **Label** text box to select the item, and then use the up and down arrow buttons to move the item higher or lower in the list.</span></span>  
  
    -   <span data-ttu-id="75608-131">单击 **“从查询中获取值”** 可提供检索此参数的值或友好名称的现有数据集的名称。</span><span class="sxs-lookup"><span data-stu-id="75608-131">Click **Get values from a query** to provide the name of an existing dataset that retrieves the values, and optionally, the friendly names for this parameter.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="75608-132">如果相同数据集包含该报表参数的对应查询参数，则该报表会在您尝试运行它时显示错误消息。</span><span class="sxs-lookup"><span data-stu-id="75608-132">If the same dataset contains the corresponding query parameter for the report parameter, the report will display an error message when you try to run it.</span></span> <span data-ttu-id="75608-133">您可使用不同的数据集检索值，从而解决此错误。</span><span class="sxs-lookup"><span data-stu-id="75608-133">You resolve this error by using a different dataset to retrieve the values.</span></span>  
  
         <span data-ttu-id="75608-134">在 **“数据集”** 中，选择该数据集的名称。</span><span class="sxs-lookup"><span data-stu-id="75608-134">In **Dataset**, choose the name of the dataset.</span></span>  
  
         <span data-ttu-id="75608-135">在 **“值字段”** 中，选择提供参数值的字段的名称。</span><span class="sxs-lookup"><span data-stu-id="75608-135">In **Value field**, choose the name of the field that provides parameter values.</span></span>  
  
         <span data-ttu-id="75608-136">在 **“标签字段”** 中，选择提供参数友好名称的字段的名称。</span><span class="sxs-lookup"><span data-stu-id="75608-136">In **Label field**, choose the name of the field that provides the friendly names for the parameter.</span></span> <span data-ttu-id="75608-137">如果友好名称没有单独的字段，则为其选择与 **“值”** 字段相同的字段。</span><span class="sxs-lookup"><span data-stu-id="75608-137">If there is no separate field for friendly names, choose the same field as you chose for the **Value** field.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="75608-138">预览该报表时，将看到参数的可用值下拉列表。</span><span class="sxs-lookup"><span data-stu-id="75608-138">When you preview the report, you see a drop-down list of available values for the parameter.</span></span>  
  
### <a name="to-remove-the-available-values-for-a-report-parameter"></a><span data-ttu-id="75608-139">删除报表参数的可用值</span><span class="sxs-lookup"><span data-stu-id="75608-139">To remove the available values for a report parameter</span></span>  
  
1.  <span data-ttu-id="75608-140">在“报表数据”窗格中，展开“参数”节点。</span><span class="sxs-lookup"><span data-stu-id="75608-140">In the Report Data pane, expand the Parameters node.</span></span> <span data-ttu-id="75608-141">右键单击该参数，然后单击“参数属性”  。</span><span class="sxs-lookup"><span data-stu-id="75608-141">Right-click the parameter and click **Parameter Properties**.</span></span> <span data-ttu-id="75608-142">将打开 **“Report Parameters”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="75608-142">The **Report Parameters** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="75608-143">单击 **“可用值”** 。</span><span class="sxs-lookup"><span data-stu-id="75608-143">Click **Available Values**.</span></span>  
  
3.  <span data-ttu-id="75608-144">在 **“选择以下选项之一”** 中，单击 **“无”** 。</span><span class="sxs-lookup"><span data-stu-id="75608-144">In **Select from one of the following options**, click **None**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="75608-145">预览该报表时，将不再显示参数的可用值下拉列表。</span><span class="sxs-lookup"><span data-stu-id="75608-145">When you preview the report, you the drop-down list of available values for the parameter no longer appears.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75608-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="75608-146">See Also</span></span>  
 <span data-ttu-id="75608-147">[更改报表参数的顺序（报表生成器和 SSRS）](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="75608-147">[Change the Order of a Report Parameter &#40;Report Builder and SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="75608-148">[添加、更改或删除报表参数（报表生成器和 SSRS）](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="75608-148">[Add, Change, or Delete a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="75608-149">[向报表添加级联参数（报表生成器和 SSRS）](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="75608-149">[Add Cascading Parameters to a Report &#40;Report Builder and SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="75608-150">[为报表参数添加、更改或删除默认值（报表生成器和 SSRS）](add-change-or-delete-default-values-for-a-report-parameter.md) </span><span class="sxs-lookup"><span data-stu-id="75608-150">[Add, Change, or Delete Default Values for a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-default-values-for-a-report-parameter.md) </span></span>  
 <span data-ttu-id="75608-151">[参数集合引用（报表生成器和 SSRS）](built-in-collections-parameters-collection-references-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="75608-151">[Parameters Collection References &#40;Report Builder and SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md) </span></span>  
 <span data-ttu-id="75608-152">[教程：向报表添加参数（报表生成器）](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="75608-152">[Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span></span>  
 [<span data-ttu-id="75608-153">表达式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="75608-153">Expressions &#40;Report Builder and SSRS&#41;</span></span>](expressions-report-builder-and-ssrs.md)  
  
  
