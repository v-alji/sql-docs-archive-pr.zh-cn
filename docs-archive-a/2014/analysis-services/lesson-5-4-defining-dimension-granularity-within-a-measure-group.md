---
title: 定义度量值组中的维度粒度 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4f079485-9eb4-405c-9a20-81258298b810
author: minewiskan
ms.author: owend
ms.openlocfilehash: dd1119da70631d66debdf79ecf8c911eedd06d44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580998"
---
# <a name="defining-dimension-granularity-within-a-measure-group"></a><span data-ttu-id="27555-102">定义度量值组中的维度粒度</span><span class="sxs-lookup"><span data-stu-id="27555-102">Defining Dimension Granularity within a Measure Group</span></span>
  <span data-ttu-id="27555-103">用户可能需要针对不同目的定义不同粒度或专一性的事实数据表维度。</span><span class="sxs-lookup"><span data-stu-id="27555-103">Users will want to dimension fact data at different granularity or specificity for different purposes.</span></span> <span data-ttu-id="27555-104">例如，分销商或 Internet 销售的销售额数据可以每天记录一次，而销售配额信息则可能按月或按季度级别来记录。</span><span class="sxs-lookup"><span data-stu-id="27555-104">For example, sales data for reseller or internet sales may be recorded for each day, whereas sales quota information may only exist at the month or quarter level.</span></span> <span data-ttu-id="27555-105">在这些情况下，用户可能需要时间维度针对这些不同的事实数据表具有不同的粒度或详细程度。</span><span class="sxs-lookup"><span data-stu-id="27555-105">In these scenarios, users will want a time dimension with a different grain or level of detail for each of these different fact tables.</span></span> <span data-ttu-id="27555-106">尽管可以将新的数据库维度定义为具有这种不同粒度的时间维度，但 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]提供了更简单的方法。</span><span class="sxs-lookup"><span data-stu-id="27555-106">While you could define a new database dimension as a time dimension with this different grain, there is an easier way with [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="27555-107">默认情况下，在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]中，当在度量值组中使用维度时，该维度内的数据粒度将基于该维度的键属性。</span><span class="sxs-lookup"><span data-stu-id="27555-107">By default in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], when a dimension is used within a measure group, the grain of the data within that dimension is based on the key attribute of the dimension.</span></span> <span data-ttu-id="27555-108">例如，当度量值组中包括时间维度并且时间维度的默认粒度为每天，则度量值组中该维度的默认粒度也为每天。</span><span class="sxs-lookup"><span data-stu-id="27555-108">For example, when a time dimension is included within a measure group and the default grain of the time dimension is daily, the default grain of that dimension within the measure group is daily.</span></span> <span data-ttu-id="27555-109">多数情况下这样是合适的，例如本教程中的“Internet 销售”\*\*\*\* 和“分销商销售”\*\*\*\* 度量值组便是恰当的示例。</span><span class="sxs-lookup"><span data-stu-id="27555-109">Many times this is appropriate, such as for the **Internet Sales** and **Reseller Sales** measure groups in this tutorial.</span></span> <span data-ttu-id="27555-110">但是，当其他类型的度量值组（例如“销售配额”或“预算”度量值组）中包括此类维度时，则使用每月粒度或每季度粒度更为合适。</span><span class="sxs-lookup"><span data-stu-id="27555-110">However, when such a dimension is included in other types of measure groups, such as in a sales quota or budget measure group, a monthly or quarterly grain is generally more appropriate.</span></span>  
  
 <span data-ttu-id="27555-111">若要为多维数据集维度指定默认粒度以外的粒度，则需要在多维数据集设计器的“维度用法”\*\*\*\* 选项卡上修改特定度量值组中使用的多维数据集维度的粒度属性。</span><span class="sxs-lookup"><span data-stu-id="27555-111">To specify a grain for a cube dimension other than the default grain, you modify the granularity attribute for a cube dimension as used within a particular measure group on the **Dimension Usage** tab of Cube Designer.</span></span> <span data-ttu-id="27555-112">当您将特定度量值组中某一维度的粒度更改为该维度的键属性之外的属性时，必须保证该度量值组中的所有其他属性与这一新粒度属性直接或间接相关。</span><span class="sxs-lookup"><span data-stu-id="27555-112">When you change the grain of a dimension within a specific measure group to an attribute other than the key attribute for that dimension, you must guarantee that all other attributes in the measure group are directly or indirectly related to new granularity attribute.</span></span> <span data-ttu-id="27555-113">方法是在所有其他属性与被指定为度量值组中粒度属性的属性之间指定属性关系。</span><span class="sxs-lookup"><span data-stu-id="27555-113">You do this by specifying attribute relationships between all other attributes and the attribute that is specified as the granularity attribute in the measure group.</span></span> <span data-ttu-id="27555-114">在这种情况下，可以定义其他属性关系，而不是移动属性关系。</span><span class="sxs-lookup"><span data-stu-id="27555-114">In this case, you define additional attribute relationships rather than move attribute relationships.</span></span> <span data-ttu-id="27555-115">对于维度中的其余属性而言，有效指定为粒度属性的属性将成为度量值组中的键属性。</span><span class="sxs-lookup"><span data-stu-id="27555-115">The attribute that is specified as the granularity attribute effectively becomes the key attribute within the measure group for the remaining attributes in the dimension.</span></span> <span data-ttu-id="27555-116">如果未恰当指定属性关系，则 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将无法正确地聚合值，您在本主题的各任务中会看到这种情况。</span><span class="sxs-lookup"><span data-stu-id="27555-116">If you do not specify attribute relationships appropriately, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] will not be able to aggregate values correctly, as you will see in the tasks in this topic.</span></span>  
  
 <span data-ttu-id="27555-117">有关详细信息，请参阅 [维度关系](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)、 [定义常规关系和常规关系属性](multidimensional-models/define-a-regular-relationship-and-regular-relationship-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="27555-117">For more information, see [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md), [Define a Regular Relationship and Regular Relationship Properties](multidimensional-models/define-a-regular-relationship-and-regular-relationship-properties.md).</span></span>  
  
 <span data-ttu-id="27555-118">在本主题的任务中，您将添加“销售配额”度量值组并将该度量值组中的“日期”维度的粒度定义为每月。</span><span class="sxs-lookup"><span data-stu-id="27555-118">In the tasks in this topic, you add a Sales Quotas measure group and define the granularity of the Date dimension in this measure group to be monthly.</span></span> <span data-ttu-id="27555-119">然后定义月属性和其他维度属性之间的属性关系，以确保 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 能够正确地聚合值。</span><span class="sxs-lookup"><span data-stu-id="27555-119">You then define attribute relationships between the month attribute and other dimension attributes to ensure that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] aggregates values correctly.</span></span>  
  
## <a name="adding-tables-and-defining-the-sales-quotas-measure-group"></a><span data-ttu-id="27555-120">添加表并定义“销售配额”度量值组</span><span class="sxs-lookup"><span data-stu-id="27555-120">Adding Tables and Defining the Sales Quotas Measure Group</span></span>  
  
1.  <span data-ttu-id="27555-121">切换到 **Adventure Works DW 2012** 数据源视图。</span><span class="sxs-lookup"><span data-stu-id="27555-121">Switch to the **Adventure Works DW 2012** data source view.</span></span>  
  
2.  <span data-ttu-id="27555-122">右键单击 "**关系图组织**程序" 窗格中的任意位置，单击 "**新建关系图**"，然后命名关系图 `Sales Quotas` 。</span><span class="sxs-lookup"><span data-stu-id="27555-122">Right-click anywhere in the **Diagram Organizer** pane, click **New Diagram**, and then name the diagram `Sales Quotas`.</span></span>  
  
3.  <span data-ttu-id="27555-123">将 "**员工**"、"**销售区域**" 和 `Date` "表" 从 "**表**" 窗格拖到 "**关系图**" 窗格中。</span><span class="sxs-lookup"><span data-stu-id="27555-123">Drag the **Employee**, **Sales Territory**, and `Date` tables from the **Tables** pane to the **Diagram** pane.</span></span>  
  
4.  <span data-ttu-id="27555-124">右键单击“关系图”\*\*\*\* 窗格中的任意位置并选择“添加/删除表”\*\*\*\*，以将 **FactSalesQuota** 表添加到“关系图”\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="27555-124">Add the **FactSalesQuota** table to the **Diagram** pane by right-clicking anywhere in the **Diagram** pane and selecting **Add/Remove Tables**.</span></span>  
  
     <span data-ttu-id="27555-125">注意， **SalesTerritory** 表通过 **Employee** 表链接到 **FactSalesQuota** 表。</span><span class="sxs-lookup"><span data-stu-id="27555-125">Notice that the **SalesTerritory** table is linked to the **FactSalesQuota** table through the **Employee** table.</span></span>  
  
5.  <span data-ttu-id="27555-126">检查 **FactSalesQuota** 表中的列，然后浏览此表中的数据。</span><span class="sxs-lookup"><span data-stu-id="27555-126">Review the columns in the **FactSalesQuota** table and then explore the data in this table.</span></span>  
  
     <span data-ttu-id="27555-127">注意，此表内数据的粒度为日历季度，该粒度的详细程度处于 FactSalesQuota 表中的最低级别。</span><span class="sxs-lookup"><span data-stu-id="27555-127">Notice that the grain of the data within this table is the calendar quarter, which is the lowest level of detail in the FactSalesQuota table.</span></span>  
  
6.  <span data-ttu-id="27555-128">在数据源视图设计器中，将**FactSalesQuota**表的**FriendlyName**属性更改为 `SalesQuotas` 。</span><span class="sxs-lookup"><span data-stu-id="27555-128">In Data Source View Designer, change the **FriendlyName** property of the **FactSalesQuota** table to `SalesQuotas`.</span></span>  
  
7.  <span data-ttu-id="27555-129">切换到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 多维数据集，再单击“多维数据集结构”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="27555-129">Switch to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Cube Structure** tab.</span></span>  
  
8.  <span data-ttu-id="27555-130">右键单击 "**度量值**" 窗格中的任意位置，单击 "**新建度量值组**"，单击 `SalesQuotas` "**新建度量值组**" 对话框，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="27555-130">Right-click anywhere in the **Measures** pane, click **New Measure Group**, click `SalesQuotas` in the **New Measure Group** dialog box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="27555-131">`Sales Quotas`度量值组将出现在 "**度量值**" 窗格中。</span><span class="sxs-lookup"><span data-stu-id="27555-131">The `Sales Quotas` measure group appears in the **Measures** pane.</span></span> <span data-ttu-id="27555-132">在 "**维度**" 窗格中，请注意， `Date` 基于数据库维度也定义了新的多维数据集维度 `Date` 。</span><span class="sxs-lookup"><span data-stu-id="27555-132">In the **Dimensions** pane, notice that a new `Date` cube dimension is also defined, based on the `Date` database dimension.</span></span> <span data-ttu-id="27555-133">因为 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 不了解与时间相关的哪个现有多维数据集维度与“销售配额”度量值组下面的 **FactSalesQuota** 事实数据表中的 **DateKey** 列相关，所以定义了与时间相关的新的多维数据集维度。</span><span class="sxs-lookup"><span data-stu-id="27555-133">A new time-related cube dimension is defined because [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] does not know which of the existing time-related cube dimensions to relate to the **DateKey** column in the **FactSalesQuota** fact table that underlies the Sales Quotas measure group.</span></span> <span data-ttu-id="27555-134">以后在本主题的其他任务中，您可以对此进行更改。</span><span class="sxs-lookup"><span data-stu-id="27555-134">You will change this later in another task in this topic.</span></span>  
  
9. <span data-ttu-id="27555-135">展开 `Sales Quotas` 度量值组。</span><span class="sxs-lookup"><span data-stu-id="27555-135">Expand the `Sales Quotas` measure group.</span></span>  
  
10. <span data-ttu-id="27555-136">在“度量值”\*\*\*\* 窗格中，选择“销售额配额”\*\*\*\*，然后在“属性”窗口中将 **FormatString** 属性的值设置为 **Currency**。</span><span class="sxs-lookup"><span data-stu-id="27555-136">In the **Measures** pane, select **Sales Amount Quota**, and then set the value for the **FormatString** property to **Currency** in the Properties window.</span></span>  
  
11. <span data-ttu-id="27555-137">选择 "**销售配额计数**" 度量值，然后在 `#,#` "属性窗口中键入作为"**格式字符串**"属性的值。</span><span class="sxs-lookup"><span data-stu-id="27555-137">Select the **Sales Quotas Count** measure, and then type `#,#` as the value for the **FormatString** property in the Properties window.</span></span>  
  
12. <span data-ttu-id="27555-138">从度量值组中删除 "**日历季度**" 度量值 `Sales Quotas` 。</span><span class="sxs-lookup"><span data-stu-id="27555-138">Delete the **Calendar Quarter** measure from the `Sales Quotas` measure group.</span></span>  
  
     [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="27555-139">检测出“日历季度”度量值下的列是包含度量值的列。</span><span class="sxs-lookup"><span data-stu-id="27555-139">detected the column that underlies the Calendar Quarter measure as a column that contains measures.</span></span> <span data-ttu-id="27555-140">但是，在本主题后面部分，您将使用该列和 CalendarYear 列包含的值将“销售配额”度量值组链接到“日期”维度。</span><span class="sxs-lookup"><span data-stu-id="27555-140">However, this column and the CalendarYear column contain the values that you will use to link the Sales Quotas measure group to the Date dimension later in this topic.</span></span>  
  
13. <span data-ttu-id="27555-141">在 "**度量**值" 窗格中，右键单击 `Sales Quotas` 度量值组，然后单击 "**新建度量值**"。</span><span class="sxs-lookup"><span data-stu-id="27555-141">In the **Measures** pane, right-click the `Sales Quotas` measure group, and then click **New Measure**.</span></span>  
  
     <span data-ttu-id="27555-142">将打开“新建度量值”\*\*\*\* 对话框，其中包含使用类型为 **Sum** 的度量值的可用源列。</span><span class="sxs-lookup"><span data-stu-id="27555-142">The **New Measure** dialog box opens, containing the available source columns for a measure with a usage type of **Sum**.</span></span>  
  
14. <span data-ttu-id="27555-143">在 "**新建度量值**" 对话框中，选择 "**使用情况**" 列表中的 "**非重复计数**"，确认在 `SalesQuotas` "**源表**" 列表中选择 "EmployeeKey"，在 "**源列**" 列表中选择 " **EmployeeKey** "，然后单击 **"确定"**</span><span class="sxs-lookup"><span data-stu-id="27555-143">In the **New Measure** dialog box, select **Distinct count** in the **Usage** list, verify that `SalesQuotas` is selected in the **Source table** list, select **EmployeeKey** in the **Source column** list, and then click **OK**.</span></span>  
  
     <span data-ttu-id="27555-144">注意，将在名为“销售配额 1”\*\*\*\* 的新度量值组中创建该度量值。</span><span class="sxs-lookup"><span data-stu-id="27555-144">Notice that the measure is created in a new measure group named **Sales Quotas 1**.</span></span> <span data-ttu-id="27555-145">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中的非重复计数度量值在它们自己的度量值组中创建，以最大程度地提高处理性能。</span><span class="sxs-lookup"><span data-stu-id="27555-145">Distinct count measures in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] are created in their own measure groups to maximize processing performance.</span></span>  
  
15. <span data-ttu-id="27555-146">将 "**员工密钥非重复计数**度量值" 的 "**名称**" 属性的值更改为 `Sales Person Count` ，然后键入 `#,#` 作为 "**格式字符串**" 属性的值。</span><span class="sxs-lookup"><span data-stu-id="27555-146">Change the value for the **Name** property for the **Employee Key Distinct Count** measure to `Sales Person Count`, and then type `#,#` as the value for the **FormatString** property.</span></span>  
  
## <a name="browsing-the-measures-in-the-sales-quota-measure-group-by-date"></a><span data-ttu-id="27555-147">按日期浏览“销售配额”度量值组中的度量值</span><span class="sxs-lookup"><span data-stu-id="27555-147">Browsing the Measures in the Sales Quota Measure Group by Date</span></span>  
  
1.  <span data-ttu-id="27555-148">在“生成”\*\*\*\* 菜单上，单击“部署 Analysis Services 教程”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27555-148">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="27555-149">在部署成功完成后，在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集的多维数据集设计器中单击“浏览器”\*\*\*\* 选项卡，再单击“重新连接”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="27555-149">When deployment has successfully completed, click the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Reconnect** button.</span></span>  
  
3.  <span data-ttu-id="27555-150">单击 Excel 快捷方式，然后单击“启用”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27555-150">Click the Excel shortcut, and then click **Enable**.</span></span>  
  
4.  <span data-ttu-id="27555-151">在 "数据透视表字段列表" 中，展开 `Sales Quotas` 度量值组，然后将 "**销售配额**" 度量值拖到 "值" 区域。</span><span class="sxs-lookup"><span data-stu-id="27555-151">In the PivotTable Field List, expand the `Sales Quotas` measure group, and then drag the **Sales Amount Quota** measure to the Values area.</span></span>  
  
5.  <span data-ttu-id="27555-152">展开“销售区域”\*\*\*\* 维度，然后将“销售区域”\*\*\*\* 用户定义层次结构添加到行标签。</span><span class="sxs-lookup"><span data-stu-id="27555-152">Expand the **Sales Territory** dimension, and then drag the **Sales Territories** user-defined hierarchy to Row Labels.</span></span>  
  
     <span data-ttu-id="27555-153">注意，“销售区域”多维数据集维度没有与 Fact Sales Quota 表直接或间接相关，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="27555-153">Notice that the Sales Territory cube dimension is not related, directly or indirectly, to the Fact Sales Quota table, as shown in the following image.</span></span>  
  
     <span data-ttu-id="27555-154">!["销售区域" 多维数据集维度](../../2014/tutorials/media/l5-granularity-2.gif "“销售区域”多维数据集维度")</span><span class="sxs-lookup"><span data-stu-id="27555-154">![Sales Territory cube dimension](../../2014/tutorials/media/l5-granularity-2.gif "Sales Territory cube dimension")</span></span>  
  
     <span data-ttu-id="27555-155">在本主题的下一系列步骤中，您将在该维度和该事实数据表之间定义引用维度关系。</span><span class="sxs-lookup"><span data-stu-id="27555-155">In the next series of steps in this topic you will define a reference dimension relationship between this dimension and this fact table.</span></span>  
  
6.  <span data-ttu-id="27555-156">将“销售区域”\*\*\*\* 用户层次结构从“行标签”区域移到“列标签”区域。</span><span class="sxs-lookup"><span data-stu-id="27555-156">Move the **Sales Territories** user hierarchy from the Rows Labels area to the Column Labels area.</span></span>  
  
7.  <span data-ttu-id="27555-157">在数据透视表字段列表中，选择“销售区域”\*\*\*\* 用户层次结构，然后单击右侧的向下箭头。</span><span class="sxs-lookup"><span data-stu-id="27555-157">In the PivotTable Field list, select the **Sales Territories** user-defined hierarchy, and then click the down arrow to the right.</span></span>  
  
     <span data-ttu-id="27555-158">![字段列表中的销售区域层次结构](../../2014/tutorials/media/l5-granularity-1a.png "字段列表中的销售区域层次结构")</span><span class="sxs-lookup"><span data-stu-id="27555-158">![Sales Territories hierarchy in the field list](../../2014/tutorials/media/l5-granularity-1a.png "Sales Territories hierarchy in the field list")</span></span>  
  
8.  <span data-ttu-id="27555-159">在筛选器中，单击“全选”复选框以取消选中所有选择，然后仅选择 **North America**。</span><span class="sxs-lookup"><span data-stu-id="27555-159">In the filter, click the Select All checkbox to clear all the selections, and then choose just **North America**.</span></span>  
  
     <span data-ttu-id="27555-160">![用于选择“北美”的“筛选”窗格](../../2014/tutorials/media/l5-granularity-1b.png "用于选择“北美”的“筛选”窗格")</span><span class="sxs-lookup"><span data-stu-id="27555-160">![Filter pane for selecting North America](../../2014/tutorials/media/l5-granularity-1b.png "Filter pane for selecting North America")</span></span>  
  
9. <span data-ttu-id="27555-161">在 "数据透视表字段列表" 中，展开 `Date` 。</span><span class="sxs-lookup"><span data-stu-id="27555-161">In the PivotTable Field List, expand `Date`.</span></span>  
  
10. <span data-ttu-id="27555-162">将 **Date.Fiscal Date** 用户层次结构拖到行标签</span><span class="sxs-lookup"><span data-stu-id="27555-162">Drag the **Date.Fiscal Date** user hierarchy to Row Labels</span></span>  
  
11. <span data-ttu-id="27555-163">在数据透视表中，单击“行标签”旁的向下箭头。</span><span class="sxs-lookup"><span data-stu-id="27555-163">On the PivotTable, click the down arrow next to Row Labels.</span></span> <span data-ttu-id="27555-164">取消选中除 **FY 2008**之外的所有年份。</span><span class="sxs-lookup"><span data-stu-id="27555-164">Clear all of the years except for **FY 2008**.</span></span>  
  
     <span data-ttu-id="27555-165">请注意，只有**月**级别的**2007 年7月**的成员显示，而不是显示**月**、 **2007**、 **8 月、2007**、9月和9月的**2007**成员，并且只显示该级别的**年7月 2007 1**日， `Date` 而不是所有31天。</span><span class="sxs-lookup"><span data-stu-id="27555-165">Notice that only the **July 2007** member of the **Month** level appears, instead of the **July, 2007**, **August, 2007**, and **September, 2007** members of **Month** level, and that only the **July 1, 2007** member of the `Date` level appears, instead of all 31 days.</span></span> <span data-ttu-id="27555-166">出现此行为是因为事实数据表中数据的粒度处于季度级别，维度的粒度 `Date` 为每日级别。</span><span class="sxs-lookup"><span data-stu-id="27555-166">This behavior occurs because the grain of the data in the fact table is at the quarter level and the grain of the `Date` dimension is the daily level.</span></span> <span data-ttu-id="27555-167">在本主题的下一个任务中，您可以对此行为进行更改。</span><span class="sxs-lookup"><span data-stu-id="27555-167">You will change this behavior in the next task in this topic.</span></span>  
  
     <span data-ttu-id="27555-168">另注意，月份级别和日级别以及季度级别的“销售额配额”\*\*\*\* 值相同，都为 $13,733,000.00。</span><span class="sxs-lookup"><span data-stu-id="27555-168">Notice also that the **Sales Amount Quota** value for the month and day levels is the same value as for the quarter level, $13,733,000.00.</span></span> <span data-ttu-id="27555-169">这是因为“销售配额”度量值组中最低的数据级别为季度级别。</span><span class="sxs-lookup"><span data-stu-id="27555-169">This is because the lowest level of data in the Sales Quotas measure group is at the quarter level.</span></span> <span data-ttu-id="27555-170">你可以在第 6 课中更改此行为。</span><span class="sxs-lookup"><span data-stu-id="27555-170">You will change this behavior in Lesson 6.</span></span>  
  
     <span data-ttu-id="27555-171">下图显示了“销售额配额”\*\*\*\* 的值。</span><span class="sxs-lookup"><span data-stu-id="27555-171">The following image shows the values for **Sales Amount Quota**.</span></span>  
  
     <span data-ttu-id="27555-172">![“销售配额”的值](../../2014/tutorials/media/l5-granularity-3.png "“销售配额”的值")</span><span class="sxs-lookup"><span data-stu-id="27555-172">![Values for Sales Amount Quota](../../2014/tutorials/media/l5-granularity-3.png "Values for Sales Amount Quota")</span></span>  
  
## <a name="defining-dimension-usage-properties-for-the-sales-quotas-measure-group"></a><span data-ttu-id="27555-173">定义“销售配额”度量值组的维度用法属性</span><span class="sxs-lookup"><span data-stu-id="27555-173">Defining Dimension Usage Properties for the Sales Quotas Measure Group</span></span>  
  
1.  <span data-ttu-id="27555-174">打开“雇员”\*\*\*\* 维度的维度设计器，右键单击“数据源视图”\*\*\*\* 窗格中的 **SalesTerritoryKey**，然后单击“从列新建属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27555-174">Open Dimension Designer for the **Employee** dimension, right-click **SalesTerritoryKey** in the **Data Source View** pane, and then click **New Attribute from Column**.</span></span>  
  
2.  <span data-ttu-id="27555-175">在“属性”\*\*\*\* 窗格中，选择 **SalesTerritoryKey**，然后在“属性”窗口中，将 **AttributeHierarchyVisible** 属性设置为 **False**，将 **AttributeHierarchyOptimizedState** 属性设置为 **NotOptimized**，并将 **AttributeHierarchyOrdered** 属性设置为 **False**。</span><span class="sxs-lookup"><span data-stu-id="27555-175">In the **Attributes** pane, select **SalesTerritoryKey**, and then set the **AttributeHierarchyVisible** property to **False** in the Properties window, set the **AttributeHierarchyOptimizedState** property to **NotOptimized**, and set the **AttributeHierarchyOrdered** property to **False**.</span></span>  
  
     <span data-ttu-id="27555-176">需要此属性将 "**销售区域**" 维度链接到 " `Sales Quotas` **销售配额 1** " 度量值组，并将其作为引用的维度。</span><span class="sxs-lookup"><span data-stu-id="27555-176">This attribute is required to link the **Sales Territory** dimension to the `Sales Quotas` and **Sales Quotas 1** measure groups as a referenced dimension.</span></span>  
  
3.  <span data-ttu-id="27555-177">在 "教程" 多维数据集的多维数据集设计器中 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，单击 "**维度用法**" 选项卡，然后查看 " `Sales Quotas` 和**销售配额 1** " 度量值组中的维度用法。</span><span class="sxs-lookup"><span data-stu-id="27555-177">In Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, click the **Dimension Usage** tab, and then review the dimension usage within the `Sales Quotas` and **Sales Quotas 1** measure groups.</span></span>  
  
     <span data-ttu-id="27555-178">请注意，**员工** `Date` 维度和多维数据集维度通过常规关系链接到 "**销售 Quotasand 销售配额 1** " 度量值组。</span><span class="sxs-lookup"><span data-stu-id="27555-178">Notice that the **Employee** and `Date` cube dimensions are linked to the **Sales Quotasand Sales Quotas 1** measure groups through regular relationships.</span></span> <span data-ttu-id="27555-179">另外注意，“销售区域”\*\*\*\* 多维数据集维度未链接到这些度量值组中的任何一组。</span><span class="sxs-lookup"><span data-stu-id="27555-179">Notice also that the **Sales Territory** cube dimension is not linked to either of these measure groups.</span></span>  
  
4.  <span data-ttu-id="27555-180">单击 "**销售区域**" 维度和 "度量值" 组相交处的单元 `Sales Quotas` ，然后单击 "浏览" **...** 按钮 (") "。此时将打开 "**定义关系**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="27555-180">Click the cell at the intersection of the **Sales Territory** dimension and the `Sales Quotas` measure group and then click the browse button (**...**). The **Define Relationship** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="27555-181">在“选择关系类型”\*\*\*\* 列表中，选择“被引用的”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27555-181">In the **Select relationship type** list, select **Referenced**.</span></span>  
  
6.  <span data-ttu-id="27555-182">在“中间维度”\*\*\*\* 列表中，选择“雇员”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27555-182">In the **Intermediate dimension** list, select **Employee**.</span></span>  
  
7.  <span data-ttu-id="27555-183">在“引用维度属性”\*\*\*\* 列表中，选择“销售区域所属地区”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27555-183">In the **Reference dimension attribute** list, select **Sales Territory Region.**</span></span>  
  
8.  <span data-ttu-id="27555-184">在“中间维度属性”\*\*\*\* 列表中，选择“销售区域关键字”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27555-184">In the **Intermediate dimension attribute** list, select **Sales Territory Key**.</span></span> <span data-ttu-id="27555-185">（“销售区域所属地区”属性的键列为 SalesTerritoryKey 列。）</span><span class="sxs-lookup"><span data-stu-id="27555-185">(The key column for the Sales Territory Region attribute is the SalesTerritoryKey column.)</span></span>  
  
9. <span data-ttu-id="27555-186">验证是否选中了“具体化”\*\*\*\* 复选框。</span><span class="sxs-lookup"><span data-stu-id="27555-186">Verify that the **Materialize** check box is selected.</span></span>  
  
10. <span data-ttu-id="27555-187">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="27555-187">Click **OK**.</span></span>  
  
11. <span data-ttu-id="27555-188">单击 "**销售区域**" 维度和 "**销售配额 1** " 度量值组相交处的单元，然后单击 "浏览"**按钮 (") "。** 此时将打开 "**定义关系**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="27555-188">Click the cell at the intersection of the **Sales Territory** dimension and the **Sales Quotas 1** measure group and then click the browse button (**...**). The **Define Relationship** dialog box opens.</span></span>  
  
12. <span data-ttu-id="27555-189">在“选择关系类型”\*\*\*\* 列表中，选择“被引用的”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27555-189">In the **Select relationship type** list, select **Referenced**.</span></span>  
  
13. <span data-ttu-id="27555-190">在“中间维度”\*\*\*\* 列表中，选择“雇员”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27555-190">In the **Intermediate dimension** list, select **Employee**.</span></span>  
  
14. <span data-ttu-id="27555-191">在“引用维度属性”\*\*\*\* 列表中，选择“销售区域所属地区”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27555-191">In the **Reference dimension attribute** list, select **Sales Territory Region.**</span></span>  
  
15. <span data-ttu-id="27555-192">在“中间维度属性”\*\*\*\* 列表中，选择“销售区域关键字”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27555-192">In the **Intermediate dimension attribute** list, select **Sales Territory Key**.</span></span> <span data-ttu-id="27555-193">（“销售区域所属地区”属性的键列为 SalesTerritoryKey 列。）</span><span class="sxs-lookup"><span data-stu-id="27555-193">(The key column for the Sales Territory Region attribute is the SalesTerritoryKey column.)</span></span>  
  
16. <span data-ttu-id="27555-194">验证是否选中了“具体化”\*\*\*\* 复选框。</span><span class="sxs-lookup"><span data-stu-id="27555-194">Verify that the **Materialize** check box is selected.</span></span>  
  
17. <span data-ttu-id="27555-195">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="27555-195">Click **OK**.</span></span>  
  
18. <span data-ttu-id="27555-196">删除 `Date` 多维数据集维度。</span><span class="sxs-lookup"><span data-stu-id="27555-196">Delete the `Date` cube dimension.</span></span>  
  
     <span data-ttu-id="27555-197">您将使用度量值组中的 "**订单日期**" 多维数据集维度 `Sales Quotas` 作为销售配额的标注日期，而不是使用四个与时间相关的多维数据集维度。</span><span class="sxs-lookup"><span data-stu-id="27555-197">Instead of having four time-related cube dimensions, you will use the **Order Date** cube dimension in the `Sales Quotas` measure group as the date against which sales quotas will be dimensioned.</span></span> <span data-ttu-id="27555-198">还会将此多维数据集维度用作多维数据集中的主日期维度。</span><span class="sxs-lookup"><span data-stu-id="27555-198">You will also use this cube dimension as the primary date dimension in the cube.</span></span>  
  
19. <span data-ttu-id="27555-199">在 "**维度**" 列表中，将 "**订单日期**" 多维数据集维度重命名为 `Date` 。</span><span class="sxs-lookup"><span data-stu-id="27555-199">In the **Dimensions** list, rename the **Order Date** cube dimension to `Date`.</span></span>  
  
     <span data-ttu-id="27555-200">通过重命名 "**订单日期**" 多维数据集维度， `Date` 用户可以更轻松地了解作为此多维数据集中的主日期维度的角色。</span><span class="sxs-lookup"><span data-stu-id="27555-200">Renaming the **Order Date** cube dimension to `Date` makes it easier for users to understand its role as the primary date dimension in this cube.</span></span>  
  
20. <span data-ttu-id="27555-201">在 **...** `Sales Quotas` 度量值组和维度相交处的单元中，单击 "浏览" 按钮 (... ") `Date` 。</span><span class="sxs-lookup"><span data-stu-id="27555-201">Click the browse button (**...**) in the cell at the intersection of the `Sales Quotas` measure group and the `Date` dimension.</span></span>  
  
21. <span data-ttu-id="27555-202">在“定义关系”\*\*\*\* 对话框中，选择“选择关系类型”\*\*\*\* 列表中的“常规”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27555-202">In the **Define Relationship** dialog box, select **Regular** in the **Select relationship type** list.</span></span>  
  
22. <span data-ttu-id="27555-203">在“粒度属性”\*\*\*\* 列表中，选择“日历季度”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27555-203">In the **Granularity attribute** list, select **Calendar Quarter**.</span></span>  
  
     <span data-ttu-id="27555-204">注意此时会出现一个警告，它指出由于已选择非键属性作为粒度属性，所以必须通过将所有其他属性指定为成员属性来确保它们与粒度属性直接或间接相关。</span><span class="sxs-lookup"><span data-stu-id="27555-204">Notice that a warning appears to notify you that because you have selected a non-key attribute as the granularity attribute, you must make sure that all other attributes are directly or indirectly related to the granularity attribute by specifying them as member properties.</span></span>  
  
23. <span data-ttu-id="27555-205">在“定义关系”\*\*\*\* 对话框的“关系”\*\*\*\* 区域中，将“日期”多维数据集维度下面表中的 **CalendarYear** 和 **CalendarQuarter** 维度列链接到“销售配额”度量值组下面表中的 **CalendarYear** 和 **CalendarQuarter** 列，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27555-205">In the **Relationship** area of the **Define Relationship** dialog box, link the **CalendarYear** and **CalendarQuarter** dimension columns from the table that underlies the Date cube dimension to the **CalendarYear** and **CalendarQuarter** columns in the table that underlies the Sales Quota measure group, and then click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="27555-206">“日历季度”定义为“销售配额”度量值组中“日期”多维数据集维度的粒度属性，但“日期”属性仍作为“Internet 销售”和“分销商”度量值组的粒度属性。</span><span class="sxs-lookup"><span data-stu-id="27555-206">The Calendar Quarter is defined as the granularity attribute for the Date cube dimension in the Sales Quotas measure group, but the Date attribute continues to be the granularity attribute for the Internet Sales and Reseller Sales measure groups.</span></span>  
  
24. <span data-ttu-id="27555-207">对 **Sales Quotas 1** 度量值组重复前面的四个步骤。</span><span class="sxs-lookup"><span data-stu-id="27555-207">Repeat the previous four steps for the **Sales Quotas 1** measure group.</span></span>  
  
## <a name="defining-attribute-relationships-between-the-calendar-quarter-attribute-and-the-other-dimension-attributes-in-the-date-dimension"></a><span data-ttu-id="27555-208">定义“日期”维度中“日历季度”属性和其他维度属性之间的属性关系</span><span class="sxs-lookup"><span data-stu-id="27555-208">Defining Attribute Relationships Between the Calendar Quarter Attribute and the Other Dimension Attributes in the Date Dimension</span></span>  
  
1.  <span data-ttu-id="27555-209">切换到维度的**维度设计器** `Date` ，然后单击 "**属性关系**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="27555-209">Switch to **Dimension Designer** for the `Date` dimension, and then click the **Attribute Relationships** tab.</span></span>  
  
     <span data-ttu-id="27555-210">请注意，尽管 "日历**年**" 通过 "**日历半期**" 属性链接到 "**日历季度**"，但是会计日历属性只相互链接;它们不会链接到 "**日历季度**" 属性，因此不会在 `Sales Quotas` 度量值组中正确聚合。</span><span class="sxs-lookup"><span data-stu-id="27555-210">Notice that although **Calendar Year** is linked to **Calendar Quarter** through the **Calendar Semester** attribute, the fiscal calendar attributes are linked only to one another; they are not linked to the **Calendar Quarter** attribute and therefore will not aggregate correctly in the `Sales Quotas` measure group.</span></span>  
  
2.  <span data-ttu-id="27555-211">在关系图中，右键单击“日历季度”属性，然后选择“新建属性关系”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27555-211">In the diagram, right-click the **Calendar Quarter** attribute and then select **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="27555-212">在“创建属性关系”对话框中，“源属性”是“日历季度”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27555-212">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Calendar Quarter**.</span></span> <span data-ttu-id="27555-213">将“相关属性”设置为“会计季度”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27555-213">Set the **Related Attribute** to **Fiscal Quarter**.</span></span>  
  
4.  <span data-ttu-id="27555-214">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="27555-214">Click **OK**.</span></span>  
  
     <span data-ttu-id="27555-215">请注意，将出现一条警告消息，指出该 `Date` 维度包含一个或多个冗余属性关系，在将非键属性用作粒度属性时，可能会导致数据无法聚合。</span><span class="sxs-lookup"><span data-stu-id="27555-215">Notice that a warning message appears stating that the `Date` dimension contains one or more redundant attribute relationships that may prevent data from being aggregated when a non-key attribute is used as a granularity attribute.</span></span>  
  
5.  <span data-ttu-id="27555-216">请删除“月份名称”\*\*\*\* 属性和“会计季度”\*\*\*\* 属性之间的属性关系。</span><span class="sxs-lookup"><span data-stu-id="27555-216">Delete the attribute relationship between the **Month Name** attribute and the **Fiscal Quarter** attribute.</span></span>  
  
6.  <span data-ttu-id="27555-217">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="27555-217">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="browsing-the-measures-in-the-sales-quota-measure-group-by-date"></a><span data-ttu-id="27555-218">按日期浏览“销售配额”度量值组中的度量值</span><span class="sxs-lookup"><span data-stu-id="27555-218">Browsing the Measures in the Sales Quota Measure Group by Date</span></span>  
  
1.  <span data-ttu-id="27555-219">在“生成”\*\*\*\* 菜单上，单击“部署 Analysis Services 教程”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27555-219">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="27555-220">部署成功完成后，在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集的多维数据集设计器中单击“浏览器”\*\*\*\* 选项卡，再单击“重新连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27555-220">When deployment has successfully completed, click the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click **Reconnect**.</span></span>  
  
3.  <span data-ttu-id="27555-221">单击 Excel 快捷方式，然后单击“启用”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27555-221">Click the Excel shortcut, and then click **Enable**.</span></span>  
  
4.  <span data-ttu-id="27555-222">将“销售配额”\*\*\*\* 度量值拖到“值”区域。</span><span class="sxs-lookup"><span data-stu-id="27555-222">Drag the **Sales Amount Quota** measure to the Values area.</span></span>  
  
5.  <span data-ttu-id="27555-223">将“销售区域”\*\*\*\* 用户层次结构拖到列标签，然后筛选 **North America**。</span><span class="sxs-lookup"><span data-stu-id="27555-223">Drag the **Sales Territories** user hierarchy to the Column Labels, and then filter on **North America**.</span></span>  
  
6.  <span data-ttu-id="27555-224">将 **Date.FiscalDate** 用户层次结构拖到行标签，然后在数据透视表上单击“行标签”\*\*\*\* 旁的向下箭头，并且取消选中除了 **FY 2008** 之外的所有复选框，以便只显示会计年度 2008。</span><span class="sxs-lookup"><span data-stu-id="27555-224">Drag the **Date.FiscalDate** user hierarchy to the Row Labels, and then click the down arrow next to **Row Labels** on the PivotTable, and clear all check boxes other than **FY 2008**, to display only fiscal year 2008.</span></span>  
  
7.  <span data-ttu-id="27555-225">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="27555-225">Click OK.</span></span>  
  
8.  <span data-ttu-id="27555-226">依次展开 **FY 2008**、 **H1 FY 2008**以及 **Q1 FY 2008**。</span><span class="sxs-lookup"><span data-stu-id="27555-226">Expand **FY 2008**, expand **H1 FY 2008**, and then expand **Q1 FY 2008**.</span></span>  
  
     <span data-ttu-id="27555-227">下图显示了 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 多维数据集的数据透视表，其中正确定义了“销售配额”度量值组维度。</span><span class="sxs-lookup"><span data-stu-id="27555-227">The following image shows a PivotTable for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, with the Sales Quota measure group dimensioned correctly.</span></span>  
  
     <span data-ttu-id="27555-228">请注意，会计季度级别的每个成员都具有与季度级别相同的值。</span><span class="sxs-lookup"><span data-stu-id="27555-228">Notice that each member of the fiscal quarter level has the same value as the quarter level.</span></span> <span data-ttu-id="27555-229">以 **Q1 FY 2008** 为例， **Q1 FY 2008** 的 $9,180,000.00 的配额也是其每个成员的值。</span><span class="sxs-lookup"><span data-stu-id="27555-229">Using **Q1 FY 2008** as an example, the quota of $9,180,000.00 for **Q1 FY 2008** is also the value for each of its members.</span></span> <span data-ttu-id="27555-230">出现此行为是因为事实数据表中数据的粒度属于季度级别，“日期”维度的粒度也属于季度级别。</span><span class="sxs-lookup"><span data-stu-id="27555-230">This behavior occurs because the grain of the data in the fact table is at the quarter level and the grain of the Date dimension is also at the quarter level.</span></span> <span data-ttu-id="27555-231">在第 6 课中，你将了解如何按比例将季度量分配到每个月。</span><span class="sxs-lookup"><span data-stu-id="27555-231">In Lesson 6, you will learn how to allocate the quarterly amount proportionally to each month.</span></span>  
  
     <span data-ttu-id="27555-232">![正确划分维度的“销售配额”度量值组](../../2014/tutorials/media/l5-granularity-7.gif "正确划分维度的“销售配额”度量值组")</span><span class="sxs-lookup"><span data-stu-id="27555-232">![Sales Quota measure group dimensioned correctly](../../2014/tutorials/media/l5-granularity-7.gif "Sales Quota measure group dimensioned correctly")</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="27555-233">下一课</span><span class="sxs-lookup"><span data-stu-id="27555-233">Next Lesson</span></span>  
 [<span data-ttu-id="27555-234">第 6 课：定义计算</span><span class="sxs-lookup"><span data-stu-id="27555-234">Lesson 6: Defining Calculations</span></span>](lesson-6-defining-calculations.md)  
  
## <a name="see-also"></a><span data-ttu-id="27555-235">另请参阅</span><span class="sxs-lookup"><span data-stu-id="27555-235">See Also</span></span>  
 <span data-ttu-id="27555-236">[维度关系](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span><span class="sxs-lookup"><span data-stu-id="27555-236">[Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span></span>  
 <span data-ttu-id="27555-237">[定义常规关系和常规关系属性](multidimensional-models/define-a-regular-relationship-and-regular-relationship-properties.md) </span><span class="sxs-lookup"><span data-stu-id="27555-237">[Define a Regular Relationship and Regular Relationship Properties](multidimensional-models/define-a-regular-relationship-and-regular-relationship-properties.md) </span></span>  
 [<span data-ttu-id="27555-238">使用数据源视图设计器中的关系图 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="27555-238">Work with Diagrams in Data Source View Designer &#40;Analysis Services&#41;</span></span>](multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
  
