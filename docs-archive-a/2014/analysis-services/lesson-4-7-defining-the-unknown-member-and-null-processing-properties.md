---
title: 定义未知成员和 Null 处理属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d9abb09c-9bfa-4e32-b530-8590e4383566
author: minewiskan
ms.author: owend
ms.openlocfilehash: cdd6504bec4f129f64d9bef6f6b0138e917888e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581008"
---
# <a name="defining-the-unknown-member-and-null-processing-properties"></a><span data-ttu-id="96512-102">定义未知成员和 Null 处理属性</span><span class="sxs-lookup"><span data-stu-id="96512-102">Defining the Unknown Member and Null Processing Properties</span></span>
  <span data-ttu-id="96512-103">当 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 处理某个维度时，将使用数据源视图中的表或视图的基础列中的所有非重复值填充该维度中的属性。</span><span class="sxs-lookup"><span data-stu-id="96512-103">When [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] processes a dimension, all the distinct values from the underlying columns in the tables, or views in the data source view, populate the attributes in the dimension.</span></span> <span data-ttu-id="96512-104">如果 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 在处理过程中遇到 Null 值，默认情况下，它会将此 Null 值转换为零（对于数值列）或空字符串（对于字符串列）。</span><span class="sxs-lookup"><span data-stu-id="96512-104">If [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] encounters a null value during processing, by default, it converts this null to a zero for numeric columns or to an empty string for string columns.</span></span> <span data-ttu-id="96512-105">你可以在基础关系数据仓库的提取、转换和加载过程（如果有）中修改默认设置或转换 Null 值。</span><span class="sxs-lookup"><span data-stu-id="96512-105">You can modify the default settings or convert null values in your extract, transform, and load process (if any) of the underlying relational data warehouse.</span></span> <span data-ttu-id="96512-106">另外，还可以通过配置以下三个属性使 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将 Null 值转换为指定值：用于维度的 **UnknownMember** 和 **UnknownMemberName** 属性以及用于维度键特性的 **NullProcessing** 属性。</span><span class="sxs-lookup"><span data-stu-id="96512-106">Additionally, you can have [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] convert the null value to a designated value by configuring three properties: the **UnknownMember** and **UnknownMemberName** properties for the dimension, and the **NullProcessing** property for the dimension's key attribute.</span></span>

 <span data-ttu-id="96512-107">根据维度的键属性是否可为 Null 或者雪花型维度的根特性是否基于可以为 Null 的列，维度向导和多维数据集向导将启用这些属性。</span><span class="sxs-lookup"><span data-stu-id="96512-107">The Dimension Wizard and the Cube Wizard will enable these properties for you based on whether the key attribute of a dimension is nullable or the root attribute of a snowflake dimension is based on a nullable column.</span></span> <span data-ttu-id="96512-108">在这些情况下，键特性的 **NullProcessing** 属性将设置为 **UnknownMember** ，而 **UnknownMember** 属性将设置为 **Visible**。</span><span class="sxs-lookup"><span data-stu-id="96512-108">In these cases, the **NullProcessing** property of the key attribute will be set to **UnknownMember** and the **UnknownMember** property will be set to **Visible**.</span></span>

 <span data-ttu-id="96512-109">但是，当以增量方式（也就是我们在本教程中处理“产品”维度的方式）生成雪花型维度时，或使用“维度设计器”定义维度然后将这些现有维度合并到多维数据集内时，可能需要手动设置 **UnknownMember** 和 **NullProcessing** 属性。</span><span class="sxs-lookup"><span data-stu-id="96512-109">However, when you build snowflaked dimensions incrementally, as we are doing with the Product dimension in this tutorial, or when you define dimensions using Dimension Designer and then incorporate these existing dimensions into a cube, the **UnknownMember** and **NullProcessing** properties might need to be set manually.</span></span>

 <span data-ttu-id="96512-110">在本主题的各项任务中，将在雪花状表的“产品”维度中添加产品类别和产品子类别属性，这些雪花表将被添加到 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 数据源视图中。</span><span class="sxs-lookup"><span data-stu-id="96512-110">In the tasks in this topic, you will add the product category and product subcategory attributes to the Product dimension from snowflaked tables that you will add to the [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW data source view.</span></span> <span data-ttu-id="96512-111">然后，将启用 "产品" 维度的 " **UnknownMember** " 属性，将 " `Assembly Components` **UnknownMemberName** " 属性的值指定为 " `Subcategory` 产品名称" 属性，然后 `Category` 为链接雪花状表的成员键属性定义自定义错误处理。</span><span class="sxs-lookup"><span data-stu-id="96512-111">You will then enable the **UnknownMember** property for the Product dimension, specify `Assembly Components` as the value for the **UnknownMemberName** property, relate the `Subcategory` and `Category` attributes to the product name attribute, and then define custom error handling for the member key attribute that links the snowflaked tables.</span></span>

> [!NOTE]
>  <span data-ttu-id="96512-112">如果在最初使用多维数据集向导定义 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 多维数据集时添加了“子类别”和“类别”属性，则将自动执行这些步骤。</span><span class="sxs-lookup"><span data-stu-id="96512-112">If you have added the Subcategory and Category attributes when you originally defined the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube using the Cube Wizard, these steps would have been performed for you automatically.</span></span>

## <a name="reviewing-error-handling-and-unknown-member-properties-in-the-product-dimension"></a><span data-ttu-id="96512-113">查看“产品”维度中的错误处理和未知成员属性</span><span class="sxs-lookup"><span data-stu-id="96512-113">Reviewing Error Handling and Unknown Member Properties in the Product Dimension</span></span>

1.  <span data-ttu-id="96512-114">切换到“产品”\*\*\*\* 维度的维度设计器，单击“维度结构”\*\*\*\* 选项卡，然后在“属性”\*\*\*\* 窗格中选择“产品”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96512-114">Switch to Dimension Designer for the **Product** dimension, click the **Dimension Structure** tab, and then select **Product** in the **Attributes** pane.</span></span>

     <span data-ttu-id="96512-115">此时，您可以查看和修改该维度自身的属性。</span><span class="sxs-lookup"><span data-stu-id="96512-115">This enables you to view and modify the properties of the dimension itself.</span></span>

2.  <span data-ttu-id="96512-116">在“属性”窗口中，查看 **UnknownMember** 和 **UnknownMemberName** 属性。</span><span class="sxs-lookup"><span data-stu-id="96512-116">In the Properties window, review the **UnknownMember** and **UnknownMemberName** properties.</span></span>

     <span data-ttu-id="96512-117">注意， **UnknownMember** 属性未被启用，因为该属性的值设置为 **None** 而不是 **Visible** 或 **Hidden**，并且没有为 **UnknownMemberName** 属性指定名称。</span><span class="sxs-lookup"><span data-stu-id="96512-117">Notice that the **UnknownMember** property is not enabled, because its value is set to **None** instead of **Visible** or **Hidden**, and that no name is specified for the **UnknownMemberName** property.</span></span>

3.  <span data-ttu-id="96512-118">在“属性”窗口的 **ErrorConfiguration** 属性单元中，选择“(自定义)”\*\*\*\*，再展开 **ErrorConfiguration** 属性集合。</span><span class="sxs-lookup"><span data-stu-id="96512-118">In the Properties window, select **(custom)** in the **ErrorConfiguration** property cell, and then expand the **ErrorConfiguration** properties collection.</span></span>

     <span data-ttu-id="96512-119">将“ErrorConfiguration”\*\*\*\* 属性设置为“(自定义)”\*\*\*\* 允许你查看默认错误配置设置，此操作不会更改任何设置。</span><span class="sxs-lookup"><span data-stu-id="96512-119">Setting the **ErrorConfiguration** property to **(custom)** allows you to view the default error configuration settings - it does not change any settings.</span></span>

4.  <span data-ttu-id="96512-120">检查键和空键错误配置属性，但不进行任何更改。</span><span class="sxs-lookup"><span data-stu-id="96512-120">Review the key and null key error configuration properties, but do not make any changes.</span></span>

     <span data-ttu-id="96512-121">注意，默认情况下，如果空键被转换为未知成员，则将忽略与此转换相关联的处理错误。</span><span class="sxs-lookup"><span data-stu-id="96512-121">Notice that, by default, when null keys are converted to the unknown member and the processing error associated with this conversion is ignored.</span></span>

     <span data-ttu-id="96512-122">下图显示了 **ErrorConfiguration** 属性集合的属性设置。</span><span class="sxs-lookup"><span data-stu-id="96512-122">The following image shows the property settings for the **ErrorConfiguration** properties collection.</span></span>

     <span data-ttu-id="96512-123">![ErrorConfiguration 属性集合](../../2014/tutorials/media/l4-productdimensionerrorconfig-1.gif "ErrorConfiguration 属性集合")</span><span class="sxs-lookup"><span data-stu-id="96512-123">![ErrorConfiguration property collection](../../2014/tutorials/media/l4-productdimensionerrorconfig-1.gif "ErrorConfiguration property collection")</span></span>

5.  <span data-ttu-id="96512-124">单击 "**浏览器**" 选项卡，验证是否在 "**层次结构**" 列表中选择了 "**产品型号系列**"，然后展开 "" `All Products` 。</span><span class="sxs-lookup"><span data-stu-id="96512-124">Click the **Browser** tab, verify that **Product Model Lines** is selected in the **Hierarchy** list, and then expand `All Products`.</span></span>

     <span data-ttu-id="96512-125">注意“产品系列”级别的五个成员。</span><span class="sxs-lookup"><span data-stu-id="96512-125">Notice the five members of the Product Line level.</span></span>

6.  <span data-ttu-id="96512-126">展开“组件”\*\*\*\*，再展开“型号名称”\*\*\*\* 级别的未标记成员。</span><span class="sxs-lookup"><span data-stu-id="96512-126">Expand **Components**, and then expand the unlabeled member of the **Model Name** level.</span></span>

     <span data-ttu-id="96512-127">此级别包含生成其他组件时使用的部件组件（从 **Adjustable Race** 产品开始），如下图所示。</span><span class="sxs-lookup"><span data-stu-id="96512-127">This level contains the assembly components that are used when building other components, starting with the **Adjustable Race** product, as shown in the following image.</span></span>

     <span data-ttu-id="96512-128">![用于生成其他组件的程序集组件](../../2014/tutorials/media/l4-productdimensionerrorconfig-2.gif "用于生成其他组件的程序集组件")</span><span class="sxs-lookup"><span data-stu-id="96512-128">![Assembly components used to build other components](../../2014/tutorials/media/l4-productdimensionerrorconfig-2.gif "Assembly components used to build other components")</span></span>

## <a name="defining-attributes-from-snowflaked-tables-and-a-product-category-user-defined-hierarchy"></a><span data-ttu-id="96512-129">从雪花状表和“产品类别”用户定义层次结构定义属性</span><span class="sxs-lookup"><span data-stu-id="96512-129">Defining Attributes from Snowflaked Tables and a Product Category User-Defined Hierarchy</span></span>

1.  <span data-ttu-id="96512-130">打开 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 数据源视图的数据源视图设计器，在“关系图组织程序”\*\*\*\* 窗格中选择“分销商销售”\*\*\*\*，再在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的“数据源视图”\*\*\*\* 菜单上单击“添加/删除对象”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96512-130">Open Data Source View Designer for the [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW data source view, select **Reseller Sales** in the **Diagram Organizer** pane, and then click **Add/Remove Objects** on the **Data Source View** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>

     <span data-ttu-id="96512-131">此时将打开“添加/删除表”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="96512-131">The **Add/Remove Tables** dialog box opens.</span></span>

2.  <span data-ttu-id="96512-132">在“包含的对象”\*\*\*\* 列表中，选择 **DimProduct (dbo)**，再单击“添加相关表”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96512-132">In the **Included objects** list, select **DimProduct (dbo)**, and then click **Add Related Tables**.</span></span>

     <span data-ttu-id="96512-133">**DimProductSubcategory (dbo)** 和 **FactProductInventory (dbo)** 都将被添加。</span><span class="sxs-lookup"><span data-stu-id="96512-133">Both **DimProductSubcategory (dbo)** and **FactProductInventory (dbo)** are added.</span></span> <span data-ttu-id="96512-134">删除 **FactProductInventory (dbo)**，这样，只有 **DimProductSubcategory (dbo)** 表将添加到“包含的对象”\*\*\*\* 列表中。</span><span class="sxs-lookup"><span data-stu-id="96512-134">Remove **FactProductInventory (dbo)** so that just the **DimProductSubcategory (dbo)** table is added to the **Included objects** list.</span></span>

3.  <span data-ttu-id="96512-135">在 **DimProductSubcategory (dbo)** 表被默认选定为最新添加的表的情况下，再次单击“添加相关表”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96512-135">With the **DimProductSubcategory (dbo)** table selected by default as the table most recently added, click **Add Related Tables** again.</span></span>

     <span data-ttu-id="96512-136">**DimProductCategory (dbo)** 表即被添加到“包含的对象”\*\*\*\* 列表中。</span><span class="sxs-lookup"><span data-stu-id="96512-136">The **DimProductCategory (dbo)** table is added to the **Included objects** list.</span></span>

4.  <span data-ttu-id="96512-137">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="96512-137">Click **OK**.</span></span>

5.  <span data-ttu-id="96512-138">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 的“格式”\*\*\*\* 菜单上，指向“自动布局”\*\*\*\*，再单击“关系图”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96512-138">On the **Format** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], point to **Auto Layout**, and then click **Diagram**.</span></span>

     <span data-ttu-id="96512-139">请注意， **DimProductSubcategory (dbo)** 表和 **DimProductCategory (dbo)** 表互相链接，并且还通过 **Product** 表链接到 **ResellerSales** 表。</span><span class="sxs-lookup"><span data-stu-id="96512-139">Notice that the **DimProductSubcategory (dbo)** table and **DimProductCategory (dbo)** table are linked to each other, and also to the **ResellerSales** table through the **Product** table.</span></span>

6.  <span data-ttu-id="96512-140">切换到“产品”\*\*\*\* 维度的维度设计器，再单击“维度结构”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="96512-140">Switch to Dimension Designer for the **Product** dimension, and then click the **Dimension Structure** tab.</span></span>

7.  <span data-ttu-id="96512-141">右键单击“数据源视图”\*\*\*\* 窗格中的任意位置，再单击“显示所有表”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96512-141">Right-click anywhere in the **Data Source View** pane, and then click **Show All Tables**.</span></span>

8.  <span data-ttu-id="96512-142">在“数据源视图”\*\*\*\* 窗格中，找到 **DimProductCategory** 表，右键单击该表中的 **ProductCategoryKey**，再单击“从列新建属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96512-142">In the **Data Source View** pane, locate the **DimProductCategory** table, right-click **ProductCategoryKey** in that table, and then click **New Attribute from Column**.</span></span>

9. <span data-ttu-id="96512-143">在 "**属性**" 窗格中，将此新属性的名称更改为 `Category` 。</span><span class="sxs-lookup"><span data-stu-id="96512-143">In the **Attributes** pane, change the name of this new attribute to `Category`.</span></span>

10. <span data-ttu-id="96512-144">在属性窗口中，单击 " **NameColumn** " 属性字段，然后单击 "浏览 (**...** ") 按钮，以打开 "**名称列**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="96512-144">In the Properties window, click in the **NameColumn** property field and then click the browse (**...**) button to open the **Name Column** dialog box.</span></span>

11. <span data-ttu-id="96512-145">选择“源列”\*\*\*\* 列表中的 **EnglishProductCategoryName**，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96512-145">Select **EnglishProductCategoryName** in the **Source column** list and then click **OK**.</span></span>

12. <span data-ttu-id="96512-146">在“数据源视图”\*\*\*\* 窗格中，找到 **DimProductSubcategory** 表，右键单击该表中的 **ProductSubcategoryKey**，再单击“从列新建属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96512-146">In the **Data Source View** pane, locate the **DimProductSubcategory** table, right-click **ProductSubcategoryKey** in that table, and then click **New Attribute from Column**.</span></span>

13. <span data-ttu-id="96512-147">在 "**属性**" 窗格中，将此新属性的名称更改为 `Subcategory` 。</span><span class="sxs-lookup"><span data-stu-id="96512-147">In the **Attributes** pane, change the name of this new attribute to `Subcategory`.</span></span>

14. <span data-ttu-id="96512-148">在属性窗口中，单击 " **NameColumn** " 属性字段，然后单击 "浏览\*\* ( ..." ) **按钮，以打开 "**名称列\*\*" 对话框。</span><span class="sxs-lookup"><span data-stu-id="96512-148">In the Properties window, click in the **NameColumn** property field and then click the browse **(...)** button to open the **Name Column** dialog box.</span></span>

15. <span data-ttu-id="96512-149">选择“源列”\*\*\*\* 列表中的 **EnglishProductSubcategoryName**，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96512-149">Select **EnglishProductSubcategoryName** in the **Source column** list and then click **OK**.</span></span>

16. <span data-ttu-id="96512-150">按从上到下的顺序，创建名为 "**产品类别**" 的新用户定义层次结构： `Category` 、 `Subcategory` 和**产品名称**。</span><span class="sxs-lookup"><span data-stu-id="96512-150">Create a new user-defined hierarchy called **Product Categories** with the following levels, in order from top to bottom: `Category`, `Subcategory`, and **Product Name**.</span></span>

17. <span data-ttu-id="96512-151">指定 `All Products` 作为 "产品类别" 用户定义层次结构的 " **AllMemberName** " 属性的值。</span><span class="sxs-lookup"><span data-stu-id="96512-151">Specify `All Products` as the value for the **AllMemberName** property of the Product Categories user-defined hierarchy.</span></span>

## <a name="browsing-the-user-defined-hierarchies-in-the-product-dimension"></a><span data-ttu-id="96512-152">浏览“产品”维度中的用户定义层次结构</span><span class="sxs-lookup"><span data-stu-id="96512-152">Browsing the User-Defined Hierarchies in the Product Dimension</span></span>

1.  <span data-ttu-id="96512-153">在“产品”\*\*\*\* 维度的“维度设计器”\*\*\*\* 的“维度结构”\*\*\*\* 选项卡工具栏上，单击“处理”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96512-153">On the toolbar of the **Dimension Structure** tab of **Dimension Designer** for the **Product** dimension, click **Process**.</span></span>

2.  <span data-ttu-id="96512-154">单击“是”\*\*\*\* 以生成并部署项目，再单击“运行”\*\*\*\* 来处理“产品”\*\*\*\* 维度。</span><span class="sxs-lookup"><span data-stu-id="96512-154">Click **Yes** to build and deploy the project, and then click **Run** to process the **Product** dimension.</span></span>

3.  <span data-ttu-id="96512-155">成功处理后，在“处理进度”\*\*\*\* 对话框中展开“处理维度‘产品’已成功完成”\*\*\*\*，展开“处理维度属性‘产品名称’已完成”\*\*\*\*，再展开“SQL 查询 1”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96512-155">When processing has succeeded, expand **Processing Dimension 'Product' completed successfully** in the **Process Progress** dialog box, expand **Processing Dimension Attribute 'Product Name' completed**, and then expand **SQL queries 1**.</span></span>

4.  <span data-ttu-id="96512-156">单击 SELECT DISTINCT 查询，再单击“查看详细信息”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96512-156">Click the SELECT DISTINCT query and then click **View Details**.</span></span>

     <span data-ttu-id="96512-157">注意，WHERE 子句已添加到 SELECT DISTINCT 子句中，这将删除 ProductSubcategoryKey 列中不包含值的那些产品，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="96512-157">Notice that a WHERE clause has been added to the SELECT DISTINCT clause that removes those products that have no value in the ProductSubcategoryKey column, as shown in the following image.</span></span>

     <span data-ttu-id="96512-158">![显示 WHERE 子句的 SELECT DISTINCT 子句](../../2014/tutorials/media/l4-productnametraceline-1.gif "显示 WHERE 子句的 SELECT DISTINCT 子句")</span><span class="sxs-lookup"><span data-stu-id="96512-158">![SELECT DISTINCT clause showing WHERE clause](../../2014/tutorials/media/l4-productnametraceline-1.gif "SELECT DISTINCT clause showing WHERE clause")</span></span>

5.  <span data-ttu-id="96512-159">依次单击“关闭”\*\*\*\* 三次，关闭所有处理对话框。</span><span class="sxs-lookup"><span data-stu-id="96512-159">Click **Close** three times to close all processing dialog boxes.</span></span>

6.  <span data-ttu-id="96512-160">单击“产品”\*\*\*\* 维度的维度设计器中的“浏览器”\*\*\*\* 选项卡，再单击“重新连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96512-160">Click the **Browser** tab in Dimension Designer for the **Product** dimension, and then click **Reconnect**.</span></span>

7.  <span data-ttu-id="96512-161">验证 "**层次结构**" 列表中是否显示了 "**产品型号" 行**，展开 `All Products` "组件"，然后展开 "**组件**"。</span><span class="sxs-lookup"><span data-stu-id="96512-161">Verify that **Product Model Lines** appears in the **Hierarchy** list, expand `All Products`, and then expand **Components**.</span></span>

8.  <span data-ttu-id="96512-162">在**层次结构**列表中选择 "**产品类别**"，展开 `All Products` ，然后展开 "**组件**"。</span><span class="sxs-lookup"><span data-stu-id="96512-162">Select **Product Categories** in the **Hierarchy** list, expand `All Products`, and then expand **Components**.</span></span>

     <span data-ttu-id="96512-163">注意，没有显示部件组件。</span><span class="sxs-lookup"><span data-stu-id="96512-163">Notice that none of the assembly components appear.</span></span>

 <span data-ttu-id="96512-164">若要修改上一个任务中所述的行为，您将启用 "产品" 维度的**UnknownMember**属性，为 " **UnknownMemberName** " 属性设置一个值，将 "模型名称" 属性的**NullProcessing**属性设置 `Subcategory` 为 " **UnknownMember**"，将该属性定义**Model Name** `Category` 为该属性的相关属性 `Subcategory` ，然后将 "**产品系列**" 属性定义为 "**模型名称**" 属性的相关属性。</span><span class="sxs-lookup"><span data-stu-id="96512-164">To modify the behavior mentioned in the previous task, you will enable the **UnknownMember** property of the Products dimension, set a value for the **UnknownMemberName** property, set the **NullProcessing** property for the `Subcategory` and **Model Name** attributes to **UnknownMember**, define the `Category` attribute as a related attribute of the `Subcategory` attribute, and then define the **Product Line** attribute as a related attribute of the **Model Name** attribute.</span></span> <span data-ttu-id="96512-165">以上步骤将使 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对在 **SubcategoryKey** 列中不包含值的每个产品使用未知成员名称值，如以下任务所示。</span><span class="sxs-lookup"><span data-stu-id="96512-165">These steps will cause [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to use the unknown member name value for each product that does not have a value for the **SubcategoryKey** column, as you will see in the following task.</span></span>

## <a name="enabling-the-unknown-member-defining-attribute-relationships-and-specifying-custom-processing-properties-for-nulls"></a><span data-ttu-id="96512-166">启用未知成员，定义属性关系，并指定 Null 的自定义处理属性</span><span class="sxs-lookup"><span data-stu-id="96512-166">Enabling the Unknown Member, Defining Attribute Relationships, and Specifying Custom Processing Properties for Nulls</span></span>

1.  <span data-ttu-id="96512-167">在“产品”\*\*\*\* 维度的维度设计器中，单击“维度结构”\*\*\*\* 选项卡，然后在“属性”\*\*\*\* 窗格中选择“产品”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96512-167">Click the **Dimension Structure** tab in Dimension Designer for the **Product** dimension, and then select **Product** in the **Attributes** pane.</span></span>

2.  <span data-ttu-id="96512-168">在 "**属性**" 窗口中，将**UnknownMember**属性更改为**Visible**，再将**UnknownMemberName**属性的值更改为 `Assembly Components` 。</span><span class="sxs-lookup"><span data-stu-id="96512-168">In the **Properties** window, change the **UnknownMember** property to **Visible**, and then change the value for the **UnknownMemberName** property to `Assembly Components`.</span></span>

     <span data-ttu-id="96512-169">将 **UnknownMember** 属性更改为 **Visible** 或 **Hidden** 后，就会启用该维度的 **UnknownMember** 属性。</span><span class="sxs-lookup"><span data-stu-id="96512-169">Changing the **UnknownMember** property to either **Visible** or **Hidden** enables the **UnknownMember** property for the dimension.</span></span>

3.  <span data-ttu-id="96512-170">单击 **“属性关系”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="96512-170">Click the **Attribute Relationships** tab.</span></span>

4.  <span data-ttu-id="96512-171">在关系图中，右键单击 `Subcategory` 属性，然后选择 "**新建属性关系**"。</span><span class="sxs-lookup"><span data-stu-id="96512-171">In the diagram, right-click the `Subcategory` attribute and then select **New Attribute Relationship**.</span></span>

5.  <span data-ttu-id="96512-172">在 "**创建属性关系**" 对话框中，"**源属性**" 为 `Subcategory` 。</span><span class="sxs-lookup"><span data-stu-id="96512-172">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is `Subcategory`.</span></span> <span data-ttu-id="96512-173">将**相关属性**设置为 `Category` 。</span><span class="sxs-lookup"><span data-stu-id="96512-173">Set the **Related Attribute** to `Category`.</span></span> <span data-ttu-id="96512-174">将关系类型保留为“柔性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96512-174">Leave the relationship type set to **Flexible**.</span></span>

6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

7.  <span data-ttu-id="96512-175">在“属性”\*\*\*\* 窗格中，选择“子类别”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96512-175">In the **Attributes** pane, select **Subcategory.**</span></span>

8.  <span data-ttu-id="96512-176">在“属性”窗口中，展开 **KeyColumns** 属性，然后展开 **DimProductSubcategory.ProductSubcategoryKey (Integer)** 属性。</span><span class="sxs-lookup"><span data-stu-id="96512-176">In the Properties window, expand the **KeyColumns** property and then expand the **DimProductSubcategory.ProductSubcategoryKey (Integer)** property.</span></span>

9. <span data-ttu-id="96512-177">将 **NullProcessing** 属性更改为 **UnknownMember**。</span><span class="sxs-lookup"><span data-stu-id="96512-177">Change the **NullProcessing** property to **UnknownMember**.</span></span>

10. <span data-ttu-id="96512-178">在“属性”\*\*\*\* 窗格中，选择“型号名称”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96512-178">In the **Attributes** pane, select **Model Name**.</span></span>

11. <span data-ttu-id="96512-179">在“属性”窗口中，展开 **KeyColumns** 属性，然后展开 **Product.ModelName (WChar)** 属性。</span><span class="sxs-lookup"><span data-stu-id="96512-179">In the Properties window, expand the **KeyColumns** property and then expand the **Product.ModelName (WChar)** property.</span></span>

12. <span data-ttu-id="96512-180">将 **NullProcessing** 属性更改为 **UnknownMember**。</span><span class="sxs-lookup"><span data-stu-id="96512-180">Change the **NullProcessing** property to **UnknownMember**.</span></span>

     <span data-ttu-id="96512-181">由于这些更改，当在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] `Subcategory` 处理过程中遇到属性的 null 值或**模型名称**特性时，未知成员值将替换为键值，并且将正确构造用户定义的层次结构。</span><span class="sxs-lookup"><span data-stu-id="96512-181">Because of these changes, when [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] encounters a null value for the `Subcategory` attribute or the **Model Name** attribute during processing, the unknown member value will be substituted as the key value, and the user-defined hierarchies will be constructed correctly.</span></span>

## <a name="browsing-the-product-dimension-again"></a><span data-ttu-id="96512-182">再次浏览“产品”维度</span><span class="sxs-lookup"><span data-stu-id="96512-182">Browsing the Product Dimension Again</span></span>

1.  <span data-ttu-id="96512-183">在“生成”\*\*\*\* 菜单上，单击“部署 Analysis Services 教程”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96512-183">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>

2.  <span data-ttu-id="96512-184">成功完成部署后，单击“产品”\*\*\*\* 维度的维度设计器中的“浏览器”\*\*\*\* 选项卡，再单击“重新连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96512-184">When deployment has successfully completed, click the **Browser** tab in Dimension Designer for the **Product** dimension, and then click **Reconnect**.</span></span>

3.  <span data-ttu-id="96512-185">验证在 "**层次结构**" 列表中选择了 "**产品类别**"，然后展开 "" `All Products` 。</span><span class="sxs-lookup"><span data-stu-id="96512-185">Verify that **Product Categories** is selected in the **Hierarchy** list, and then expand `All Products`.</span></span>

     <span data-ttu-id="96512-186">注意，“程序集组件”已显示为“类别”级别的新成员。</span><span class="sxs-lookup"><span data-stu-id="96512-186">Notice that Assembly Components appears as a new member of the Category level.</span></span>

4.  <span data-ttu-id="96512-187">展开 `Assembly Components` 级别的成员 `Category` ，然后展开级别的 `Assembly Components` 成员 `Subcategory` 。</span><span class="sxs-lookup"><span data-stu-id="96512-187">Expand the `Assembly Components` member of the `Category` level and then expand the `Assembly Components` member of the `Subcategory` level.</span></span>

     <span data-ttu-id="96512-188">请注意，在“产品名称”\*\*\*\* 级别上显示了所有程序集组件，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="96512-188">Notice that all the assembly components now appear at the **Product Name** level, as shown in the following image.</span></span>

     <span data-ttu-id="96512-189">![显示程序集组件的“产品名称”级别](../../2014/tutorials/media/l4-assemblycomponents-1.gif "显示程序集组件的“产品名称”级别")</span><span class="sxs-lookup"><span data-stu-id="96512-189">![Product Name level showing assembly components](../../2014/tutorials/media/l4-assemblycomponents-1.gif "Product Name level showing assembly components")</span></span>

## <a name="next-lesson"></a><span data-ttu-id="96512-190">下一课</span><span class="sxs-lookup"><span data-stu-id="96512-190">Next Lesson</span></span>
 [<span data-ttu-id="96512-191">第 5 课：定义维度和度量值组之间的关系</span><span class="sxs-lookup"><span data-stu-id="96512-191">Lesson 5: Defining Relationships Between Dimensions and Measure Groups</span></span>](lesson-5-defining-relationships-between-dimensions-and-measure-groups.md)


