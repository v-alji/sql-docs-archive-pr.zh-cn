---
title: 向数据集添加筛选器（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eed37e74-6a43-4d7c-9959-2d5fa6a6aba9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f51411d31d8ee29bf0f163085077dcee8fd79bdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577335"
---
# <a name="add-a-filter-to-a-dataset-report-builder-and-ssrs"></a><span data-ttu-id="7d29b-102">向数据集添加筛选器（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="7d29b-102">Add a Filter to a Dataset (Report Builder and SSRS)</span></span>
  <span data-ttu-id="7d29b-103">向数据集添加筛选器可以在从外部数据源检索数据后限制报表中的数据。</span><span class="sxs-lookup"><span data-stu-id="7d29b-103">Add a filter to a dataset to limit the data in a report after the data is retrieved from an external data source.</span></span> <span data-ttu-id="7d29b-104">在向数据集添加筛选器后，所有报表部件或数据区域将都只使用与筛选条件匹配的数据。</span><span class="sxs-lookup"><span data-stu-id="7d29b-104">When you add a filter to a dataset, all report parts or data regions use only data that matches the filter conditions.</span></span>  
  
 <span data-ttu-id="7d29b-105">对于共享数据集，应用于所有依赖项的筛选器必须是报表服务器上共享数据集定义的一部分。</span><span class="sxs-lookup"><span data-stu-id="7d29b-105">For a shared dataset, a filter that applies to all dependent items must be part of the shared dataset definition on the report server.</span></span> <span data-ttu-id="7d29b-106">包含某一共享数据集实例的报表或报表部件可以创建仅应用于该实例的其他筛选器。</span><span class="sxs-lookup"><span data-stu-id="7d29b-106">A report or report part that contains an instance of a shared dataset can create an additional filter that applies only to the instance.</span></span>  
  
 <span data-ttu-id="7d29b-107">若要添加筛选器，必须指定一个或多个作为筛选器公式的条件。</span><span class="sxs-lookup"><span data-stu-id="7d29b-107">To add a filter, you must specify one or more conditions that are filter equations.</span></span> <span data-ttu-id="7d29b-108">筛选器公式由标识了要筛选的数据的表达式、运算符和要比较的值组成。</span><span class="sxs-lookup"><span data-stu-id="7d29b-108">A filter equation consists of an expression that identifies the data that you want to filter, an operator, and the value to compare to.</span></span> <span data-ttu-id="7d29b-109">所筛选数据的数据类型和值必须匹配。</span><span class="sxs-lookup"><span data-stu-id="7d29b-109">The data types of the filtered data and the value must match.</span></span> <span data-ttu-id="7d29b-110">不支持筛选数据集的聚合值。</span><span class="sxs-lookup"><span data-stu-id="7d29b-110">Filtering on aggregate values for a dataset is not supported.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-filter-to-a-shared-dataset"></a><span data-ttu-id="7d29b-111">向共享数据集添加筛选器</span><span class="sxs-lookup"><span data-stu-id="7d29b-111">To add a filter to a shared dataset</span></span>  
  
1.  <span data-ttu-id="7d29b-112">在共享数据集模式下打开一个共享数据集。</span><span class="sxs-lookup"><span data-stu-id="7d29b-112">Open a shared dataset in shared dataset mode.</span></span>  
  
2.  <span data-ttu-id="7d29b-113">在 **“主页”** 选项卡上的 **“共享数据集”** 组中，单击“数据集”。</span><span class="sxs-lookup"><span data-stu-id="7d29b-113">On the **Home** tab, in the **Shared Datasets** group, click Datasets.</span></span> <span data-ttu-id="7d29b-114">此时将打开 **“数据集属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="7d29b-114">The **Dataset Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="7d29b-115">单击 **“筛选器”** 。</span><span class="sxs-lookup"><span data-stu-id="7d29b-115">Click **Filters**.</span></span> <span data-ttu-id="7d29b-116">此时将显示当前筛选器公式的列表。</span><span class="sxs-lookup"><span data-stu-id="7d29b-116">This displays the current list of filter equations.</span></span> <span data-ttu-id="7d29b-117">默认情况下，此列表是空的。</span><span class="sxs-lookup"><span data-stu-id="7d29b-117">By default, the list is empty.</span></span>  
  
4.  <span data-ttu-id="7d29b-118">单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="7d29b-118">Click **Add**.</span></span> <span data-ttu-id="7d29b-119">此时将显示一个新的空白筛选器公式。</span><span class="sxs-lookup"><span data-stu-id="7d29b-119">A new blank filter equation appears.</span></span>  
  
5.  <span data-ttu-id="7d29b-120">在 **“表达式”** 中，键入或选择要筛选的字段的表达式。</span><span class="sxs-lookup"><span data-stu-id="7d29b-120">In **Expression**, type or select the expression for the field to filter.</span></span> <span data-ttu-id="7d29b-121">若要编辑该表达式，请单击表达式 (*fx*) 按钮。</span><span class="sxs-lookup"><span data-stu-id="7d29b-121">To edit the expression, click the expression (*fx*) button.</span></span>  
  
6.  <span data-ttu-id="7d29b-122">从列表框中选择与您在步骤 5 中创建的表达式的数据类型相匹配的数据类型。</span><span class="sxs-lookup"><span data-stu-id="7d29b-122">From the list box, select the data type that matches the type of data in the expression you created in step 5.</span></span>  
  
7.  <span data-ttu-id="7d29b-123">在 **“运算符”** 框中，选择一个供筛选器使用的运算符，以比较 **“表达式”** 框和 **“值”** 框中的值。</span><span class="sxs-lookup"><span data-stu-id="7d29b-123">In the **Operator** box, select the operator that you want the filter to use to compare the values in the **Expression** box and the **Value** box.</span></span> <span data-ttu-id="7d29b-124">您所选择的运算符将决定下一步中使用的值数。</span><span class="sxs-lookup"><span data-stu-id="7d29b-124">The operator you choose determines the number of values that are used from the next step.</span></span>  
  
8.  <span data-ttu-id="7d29b-125">在 **“值”** 框中，键入筛选器对 **“表达式”** 中的值进行比较时的目标表达式或值。</span><span class="sxs-lookup"><span data-stu-id="7d29b-125">In the **Value** box, type the expression or value against which you want the filter to evaluate the value in **Expression**.</span></span>  
  
     <span data-ttu-id="7d29b-126">有关筛选器公式的示例，请参阅[筛选器公式示例（报表生成器和 SSRS）](../report-design/filter-equation-examples-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="7d29b-126">For examples of filter equations, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](../report-design/filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-add-a-filter-to-an-embedded-dataset-or-a-shared-dataset-instance"></a><span data-ttu-id="7d29b-127">向嵌入数据集或共享数据集实例添加筛选器</span><span class="sxs-lookup"><span data-stu-id="7d29b-127">To add a filter to an embedded dataset or a shared dataset instance</span></span>  
  
1.  <span data-ttu-id="7d29b-128">在报表设计模式下打开一个报表。</span><span class="sxs-lookup"><span data-stu-id="7d29b-128">Open a report in report design mode.</span></span>  
  
2.  <span data-ttu-id="7d29b-129">右键单击“报表数据”窗格中的数据集，然后单击“数据集属性”   。</span><span class="sxs-lookup"><span data-stu-id="7d29b-129">Right-click a dataset in the **Report Data** pane and then click **Dataset Properties**.</span></span> <span data-ttu-id="7d29b-130">此时将打开 **“数据集属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="7d29b-130">The **Dataset Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="7d29b-131">单击 **“筛选器”** 。</span><span class="sxs-lookup"><span data-stu-id="7d29b-131">Click **Filters**.</span></span> <span data-ttu-id="7d29b-132">此时将显示当前筛选器公式的列表。</span><span class="sxs-lookup"><span data-stu-id="7d29b-132">This displays the current list of filter equations.</span></span> <span data-ttu-id="7d29b-133">默认情况下，此列表是空的。</span><span class="sxs-lookup"><span data-stu-id="7d29b-133">By default, the list is empty.</span></span>  
  
4.  <span data-ttu-id="7d29b-134">单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="7d29b-134">Click **Add**.</span></span> <span data-ttu-id="7d29b-135">此时将显示一个新的空白筛选器公式。</span><span class="sxs-lookup"><span data-stu-id="7d29b-135">A new blank filter equation appears.</span></span>  
  
5.  <span data-ttu-id="7d29b-136">在 **“表达式”** 中，键入或选择要筛选的字段的表达式。</span><span class="sxs-lookup"><span data-stu-id="7d29b-136">In **Expression**, type or select the expression for the field to filter.</span></span> <span data-ttu-id="7d29b-137">若要编辑该表达式，请单击表达式 (*fx*) 按钮。</span><span class="sxs-lookup"><span data-stu-id="7d29b-137">To edit the expression, click the expression (*fx*) button.</span></span>  
  
6.  <span data-ttu-id="7d29b-138">从下拉框中选择与您在步骤 5 中创建的表达式的数据类型相匹配的数据类型。</span><span class="sxs-lookup"><span data-stu-id="7d29b-138">From the drop-down box, select the data type that matches the type of data in the expression you created in step 5.</span></span>  
  
7.  <span data-ttu-id="7d29b-139">在 **“运算符”** 框中，选择一个供筛选器使用的运算符，以比较 **“表达式”** 框和 **“值”** 框中的值。</span><span class="sxs-lookup"><span data-stu-id="7d29b-139">In the **Operator** box, select the operator that you want the filter to use to compare the values in the **Expression** box and the **Value** box.</span></span> <span data-ttu-id="7d29b-140">您所选择的运算符将决定下一步中使用的值数。</span><span class="sxs-lookup"><span data-stu-id="7d29b-140">The operator you choose determines the number of values that are used from the next step.</span></span>  
  
8.  <span data-ttu-id="7d29b-141">在 **“值”** 框中，键入筛选器对 **“表达式”** 中的值进行比较时的目标表达式或值。</span><span class="sxs-lookup"><span data-stu-id="7d29b-141">In the **Value** box, type the expression or value against which you want the filter to evaluate the value in **Expression**.</span></span>  
  
     <span data-ttu-id="7d29b-142">有关筛选器公式的示例，请参阅[筛选器公式示例（报表生成器和 SSRS）](../report-design/filter-equation-examples-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="7d29b-142">For examples of filter equations, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](../report-design/filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7d29b-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7d29b-143">See Also</span></span>  
 <span data-ttu-id="7d29b-144">[添加数据集筛选器、数据区域筛选器和组筛选器（报表生成器和 SSRS）](../report-design/add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="7d29b-144">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](../report-design/add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="7d29b-145">[表达式示例（报表生成器和 SSRS）](../report-design/expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7d29b-145">[Expression Examples &#40;Report Builder and SSRS&#41;](../report-design/expression-examples-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="7d29b-146">添加筛选器（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="7d29b-146">Add a Filter &#40;Report Builder and SSRS&#41;</span></span>](../report-design/add-a-filter-report-builder-and-ssrs.md)  
  
  
