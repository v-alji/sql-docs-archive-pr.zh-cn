---
title: 定义多对多关系 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7bebb174-148c-4cbb-a285-2f6d536a16d5
author: minewiskan
ms.author: owend
ms.openlocfilehash: fb4e18831ae23b8cf1f0702b357672f7520478a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689109"
---
# <a name="defining-a-many-to-many-relationship"></a><span data-ttu-id="6766e-102">定义多对多关系</span><span class="sxs-lookup"><span data-stu-id="6766e-102">Defining a Many-to-Many Relationship</span></span>
  <span data-ttu-id="6766e-103">在定义维度时，通常每个事实联接且仅联接到一个维度成员，而一个维度成员可以与许多不同的事实相关联。</span><span class="sxs-lookup"><span data-stu-id="6766e-103">When you define a dimension, typically each fact joins to one and only one dimension member, whereas a single dimension member can be associated with many different facts.</span></span> <span data-ttu-id="6766e-104">例如，每个客户可以具有很多订单，但每个订单只属于一个客户。</span><span class="sxs-lookup"><span data-stu-id="6766e-104">For example, each customer can have many orders but each order belongs to a single customer.</span></span> <span data-ttu-id="6766e-105">在关系数据库术语中，这称为 "一对多*关系*"。</span><span class="sxs-lookup"><span data-stu-id="6766e-105">In relational database terminology, this is referred to as a *one-to-many relationship*.</span></span> <span data-ttu-id="6766e-106">但有时一个事实可联接多个维度成员。</span><span class="sxs-lookup"><span data-stu-id="6766e-106">However, sometimes a single fact can join to multiple dimension members.</span></span> <span data-ttu-id="6766e-107">在关系数据库术语中，这称为“多对多关系”\*\*。</span><span class="sxs-lookup"><span data-stu-id="6766e-107">In relational database terminology, this is referred to as a *many-to-many relationship*.</span></span> <span data-ttu-id="6766e-108">例如，一个客户进行采购的原因可以有多个，而一个采购原因可以与多个采购相关联。</span><span class="sxs-lookup"><span data-stu-id="6766e-108">For example, a customer may have multiple reasons for making a purchase, and a purchase reason can be associated with multiple purchases.</span></span> <span data-ttu-id="6766e-109">联接表用于定义与每个采购相关的销售原因。</span><span class="sxs-lookup"><span data-stu-id="6766e-109">A join table is used to define the sales reasons that relate to each purchase.</span></span> <span data-ttu-id="6766e-110">在由此类关系构建的 Sales Reason 维度中，将有多个成员与一个销售事务相关联。</span><span class="sxs-lookup"><span data-stu-id="6766e-110">A Sales Reason dimension constructed from such relationships would then have multiple members that relate to a single sales transaction.</span></span> <span data-ttu-id="6766e-111">多对多维度可将维度模型扩展到经典星型架构范围之外，并在维度不直接与事实数据表相关联的情况下支持复杂分析。</span><span class="sxs-lookup"><span data-stu-id="6766e-111">Many-to-many dimensions expand the dimensional model beyond the classic star schema and support complex analytics when dimensions are not directly related to a fact table.</span></span>

 <span data-ttu-id="6766e-112">在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]中，通过指定联接到维度表的中间事实数据表，可以定义维度和度量值组之间的多对多关系。</span><span class="sxs-lookup"><span data-stu-id="6766e-112">In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], you define a many-to-many relationship between a dimension and a measure group by specifying an intermediate fact table that is joined to the dimension table.</span></span> <span data-ttu-id="6766e-113">中间事实数据表又与该事实数据表所联接到的中间维度表联接。</span><span class="sxs-lookup"><span data-stu-id="6766e-113">An intermediate fact table is joined, in turn, to an intermediate dimension table to which the fact table is joined.</span></span> <span data-ttu-id="6766e-114">中间事实数据表与该关系中的维度表和中间维度之间的多对多关系便创建了主维度的成员与由该关系指定的度量值组中的度量值之间的多对多关系。</span><span class="sxs-lookup"><span data-stu-id="6766e-114">The many-to-many relationships between the intermediate fact table and both the dimension tables in the relationship and the intermediate dimension creates the many-to-many relationships between members of the primary dimension and measures in the measure group that is specified by the relationship.</span></span> <span data-ttu-id="6766e-115">为了通过中间度量值组定义维度和度量值组之间的多对多关系，中间度量值组必须与原始度量值组共享一个或多个维度。</span><span class="sxs-lookup"><span data-stu-id="6766e-115">In order to define a many-to-many relationship between a dimension and a measure group through an intermediate measure group, the intermediate measure group must share one or more dimensions with the original measure group.</span></span>

 <span data-ttu-id="6766e-116">利用多对多维度，可通过不同方式对值进行合计，这意味着这些值不能对“所有”成员多次聚合。</span><span class="sxs-lookup"><span data-stu-id="6766e-116">With a many-to-many dimension, values are distinct summed, which means that they do not aggregate more than once to the All member.</span></span>

> [!NOTE]
>  <span data-ttu-id="6766e-117">为了支持多对多维度关系，必须在所涉及的所有表之间的数据源视图中定义主键-外键关系。</span><span class="sxs-lookup"><span data-stu-id="6766e-117">In order to support a many-to-many dimension relationship, a primary key-foreign key relationship must be defined in the data source view between all the tables that are involved.</span></span> <span data-ttu-id="6766e-118">否则，在“多维数据集设计器”的“维度用法”\*\*\*\* 选项卡中建立关系时，无法选择正确的中间度量值组。</span><span class="sxs-lookup"><span data-stu-id="6766e-118">Otherwise, you will not be able to select the correct intermediate measure group when you establish the relationship in the **Dimension Usage** tab of Cube Designer.</span></span>

 <span data-ttu-id="6766e-119">有关详细信息，请参阅 [维度关系](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)和 [定义多对多关系和多对多关系属性](multidimensional-models/define-a-many-to-many-relationship-and-many-to-many-relationship-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6766e-119">For more information, see [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md), and [Define a Many-to-Many Relationship and Many-to-Many Relationship Properties](multidimensional-models/define-a-many-to-many-relationship-and-many-to-many-relationship-properties.md).</span></span>

 <span data-ttu-id="6766e-120">在本主题的任务中，将定义“销售原因”维度和“销售原因”度量值组，并通过“销售原因”度量值组定义“销售原因”维度与“Internet 销售”度量值组之间的多对多关系。</span><span class="sxs-lookup"><span data-stu-id="6766e-120">In the tasks in this topic, you define the Sales Reasons dimension and the Sales Reasons measure group, and you define a many-to-many relationship between the Sales Reasons dimension and the Internet Sales measure group through the Sales Reasons measure group.</span></span>

## <a name="adding-required-tables-to-the-data-source-view"></a><span data-ttu-id="6766e-121">向数据源视图添加所需的表</span><span class="sxs-lookup"><span data-stu-id="6766e-121">Adding Required Tables to the Data Source View</span></span>

1.  <span data-ttu-id="6766e-122">打开 **Adventure Works DW 2012** 数据源视图的数据源视图设计器。</span><span class="sxs-lookup"><span data-stu-id="6766e-122">Open Data Source View Designer for the **Adventure Works DW 2012** data source view.</span></span>

2.  <span data-ttu-id="6766e-123">右键单击 "**关系图组织**程序" 窗格中的任意位置，单击 "**新建关系图**"，并 `Internet Sales Order Reasons` 将指定为此新关系图的名称。</span><span class="sxs-lookup"><span data-stu-id="6766e-123">Right-click anywhere in the **Diagram Organizer** pane, click **New Diagram**, and specify `Internet Sales Order Reasons` as the name for this new diagram.</span></span>

3.  <span data-ttu-id="6766e-124">将 **InternetSales** 表从“表”\*\*\*\* 窗格拖动到“关系图”\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="6766e-124">Drag the **InternetSales** table to the **Diagram** pane from the **Tables** pane.</span></span>

4.  <span data-ttu-id="6766e-125">右键单击“关系图”\*\*\*\* 窗格中的任意位置，然后单击“添加/删除表”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6766e-125">Right-click anywhere in the **Diagram** pane, and then click **Add/Remove Tables**.</span></span>

5.  <span data-ttu-id="6766e-126">在“添加/删除表”\*\*\*\* 对话框中，将 **DimSalesReason** 表和 **FactInternetSalesReason** 表添加到“包含的对象”\*\*\*\* 列表中，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6766e-126">In the **Add/Remove Tables** dialog box, add the **DimSalesReason** table and the **FactInternetSalesReason** table to the **Included objects** list, and then click **OK**.</span></span>

     <span data-ttu-id="6766e-127">请注意，所涉及的表之间的主键-外键关系会自动建立，因为这些关系是在基础关系数据库中定义的。</span><span class="sxs-lookup"><span data-stu-id="6766e-127">Notice that the primary key-foreign key relationships between the tables that are involved are established automatically because those relationships are defined in the underlying relational database.</span></span> <span data-ttu-id="6766e-128">如果未在基础关系数据库中定义这些关系，则必须在数据源视图中对其进行定义。</span><span class="sxs-lookup"><span data-stu-id="6766e-128">If these relationships were not defined in the underlying relational database, you would have to define them in the data source view.</span></span>

6.  <span data-ttu-id="6766e-129">在“格式”\*\*\*\* 菜单上，指向“自动布局”\*\*\*\*，再单击“关系图”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6766e-129">On the **Format** menu, point to **Auto Layout**, and then click **Diagram**.</span></span>

7.  <span data-ttu-id="6766e-130">在属性窗口中，将**DimSalesReason**表的**friendlyname**属性更改为 `SalesReason` ，然后将**FactInternetSalesReason**表的**friendlyname**属性更改为 `InternetSalesReason` 。</span><span class="sxs-lookup"><span data-stu-id="6766e-130">In the Properties window, change the **FriendlyName** property of the **DimSalesReason** table to `SalesReason`, and then change the **FriendlyName** property of the **FactInternetSalesReason** table to `InternetSalesReason`.</span></span>

8.  <span data-ttu-id="6766e-131">在“表”\*\*\*\* 窗格中，展开“InternetSalesReason (dbo.FactInternetSalesReason)”\*\*\*\*，单击“SalesOrderNumber”\*\*\*\*，然后在“属性”窗口中查看此数据列的“DataType”\*\*\*\* 属性。</span><span class="sxs-lookup"><span data-stu-id="6766e-131">In the **Tables** pane, expand **InternetSalesReason (dbo.FactInternetSalesReason)**, click **SalesOrderNumber**, and then review the **DataType** property for this data column in the Properties window.</span></span>

     <span data-ttu-id="6766e-132">注意，“SalesOrderNumber”\*\*\*\* 列的数据类型为字符串数据类型。</span><span class="sxs-lookup"><span data-stu-id="6766e-132">Notice that the data type for the **SalesOrderNumber** column is a string data type.</span></span>

9. <span data-ttu-id="6766e-133">查看表中其他列的数据类型 `InternetSalesReason` 。</span><span class="sxs-lookup"><span data-stu-id="6766e-133">Review the data types for the other columns in the `InternetSalesReason` table.</span></span>

     <span data-ttu-id="6766e-134">您会看到此表中其他两列的数据类型为数值数据类型。</span><span class="sxs-lookup"><span data-stu-id="6766e-134">Notice that the data types for the other two columns in this table are numeric data types.</span></span>

10. <span data-ttu-id="6766e-135">在“表”\*\*\*\* 窗格中，右键单击“InternetSalesReason (dbo.FactInternetSalesReason)”\*\*\*\*，然后单击“浏览数据”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6766e-135">In the **Tables** pane, right-click **InternetSalesReason (dbo.FactInternetSalesReason)**, and then click **Explore Data**.</span></span>

     <span data-ttu-id="6766e-136">您会看到对于每个订单内的每个行号，均有一个键值标识采购该行中项的销售原因，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="6766e-136">Notice that, for each line number within each order, a key value identifies the sales reason for the purchase of that line item, as shown in the following image.</span></span>

     <span data-ttu-id="6766e-137">![用于标识购买的销售原因的键值](../../2014/tutorials/media/l5-many-to-many-1.gif "用于标识购买的销售原因的键值")</span><span class="sxs-lookup"><span data-stu-id="6766e-137">![Key value to identify sales reason for purchases](../../2014/tutorials/media/l5-many-to-many-1.gif "Key value to identify sales reason for purchases")</span></span>

## <a name="defining-the-intermediate-measure-group"></a><span data-ttu-id="6766e-138">定义中间度量值组</span><span class="sxs-lookup"><span data-stu-id="6766e-138">Defining the Intermediate Measure Group</span></span>

1.  <span data-ttu-id="6766e-139">切换到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集的“多维数据集设计器”，再单击“多维数据集结构”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="6766e-139">Switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Cube Structure** tab.</span></span>

2.  <span data-ttu-id="6766e-140">右键单击“度量值”\*\*\*\* 窗格中的任意位置，然后单击“新建度量值组”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6766e-140">Right-click anywhere in the **Measures** pane, and then click **New Measure Group**.</span></span> <span data-ttu-id="6766e-141">有关详细信息。请参阅 [在多维模型中创建度量值和度量值组](multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md)。</span><span class="sxs-lookup"><span data-stu-id="6766e-141">For more information, see [Create Measures and Measure Groups in Multidimensional Models](multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md).</span></span>

3.  <span data-ttu-id="6766e-142">在 "**新建度量值组**" 对话框中，在 `InternetSalesReason` "**从数据源视图中选择一个表**" 列表中选择，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="6766e-142">In the **New Measure Group** dialog box, select `InternetSalesReason` in the **Select a table from the data source view** list, and then click **OK**.</span></span>

     <span data-ttu-id="6766e-143">请注意，“Internet 销售原因”\*\*\*\* 度量值组现在显示在“度量值”\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="6766e-143">Notice that the **Internet Sales Reason** measure group now appears in the **Measures** pane.</span></span>

4.  <span data-ttu-id="6766e-144">展开“Internet 销售原因”\*\*\*\* 度量值组。</span><span class="sxs-lookup"><span data-stu-id="6766e-144">Expand the **Internet Sales Reason** measure group.</span></span>

     <span data-ttu-id="6766e-145">请注意，仅为此新度量值组定义了一个度量值，即“Internet 销售原因记数”\*\*\*\* 度量值。</span><span class="sxs-lookup"><span data-stu-id="6766e-145">Notice that only a single measure is defined for this new measure group, the **Internet Sales Reason Count** measure.</span></span>

5.  <span data-ttu-id="6766e-146">选择“Internet 销售原因记数”\*\*\*\*，然后在“属性”窗口中查看此度量值的属性。</span><span class="sxs-lookup"><span data-stu-id="6766e-146">Select **Internet Sales Reason Count** and review the properties of this measure in the Properties window.</span></span>

     <span data-ttu-id="6766e-147">请注意，此度量值的“AggregateFunction”\*\*\*\* 属性定义为“Count”\*\*\*\*，而不是“Sum”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6766e-147">Notice that the **AggregateFunction** property for this measure is defined as **Count** instead of **Sum**.</span></span> [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]<span data-ttu-id="6766e-148">由于基础数据类型是字符串数据类型，因此选择 "**计数**"。</span><span class="sxs-lookup"><span data-stu-id="6766e-148">chose **Count** because the underlying data type is a string data type.</span></span> <span data-ttu-id="6766e-149">由于 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将基础事实数据表中的其他两列检测为数字键而非实际度量值，因此未将这两列选作度量值。</span><span class="sxs-lookup"><span data-stu-id="6766e-149">The other two columns in the underlying fact table were not selected as measures because [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] detected them as numeric keys instead of as actual measures.</span></span> <span data-ttu-id="6766e-150">有关详细信息，请参阅 [定义半累加行为](multidimensional-models/define-semiadditive-behavior.md)。</span><span class="sxs-lookup"><span data-stu-id="6766e-150">For more information, see [Define Semiadditive Behavior](multidimensional-models/define-semiadditive-behavior.md).</span></span>

6.  <span data-ttu-id="6766e-151">在“属性”窗口中，将“Internet Sales Reason Count”\*\*\*\* 度量值的“Visible”\*\*\*\* 属性更改为“False”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6766e-151">In the Properties window, change the **Visible** property of the **Internet Sales Reason Count** measure to **False**.</span></span>

     <span data-ttu-id="6766e-152">此度量值将只用于联接将在“Internet 销售”度量值组旁边定义的“销售原因”维度。</span><span class="sxs-lookup"><span data-stu-id="6766e-152">This measure will only be used to join the Sales Reason dimension that you will define next to the Internet Sales measure group.</span></span> <span data-ttu-id="6766e-153">用户将不能直接浏览此度量值。</span><span class="sxs-lookup"><span data-stu-id="6766e-153">Users will not browse this measure directly.</span></span>

     <span data-ttu-id="6766e-154">下图显示了“Internet 销售原因计数”\*\*\*\* 度量值的属性。</span><span class="sxs-lookup"><span data-stu-id="6766e-154">The following image shows the properties for the **Internet Sales Reason Count** measure.</span></span>

     <span data-ttu-id="6766e-155">![“Internet 销售原因计数”度量值的属性](../../2014/tutorials/media/l5-many-to-many-2.gif "“Internet 销售原因计数”度量值的属性")</span><span class="sxs-lookup"><span data-stu-id="6766e-155">![Properties for Internet Sales Reason Count measure](../../2014/tutorials/media/l5-many-to-many-2.gif "Properties for Internet Sales Reason Count measure")</span></span>

## <a name="defining-the-many-to-many-dimension"></a><span data-ttu-id="6766e-156">定义多对多维度</span><span class="sxs-lookup"><span data-stu-id="6766e-156">Defining the Many-to-Many Dimension</span></span>

1.  <span data-ttu-id="6766e-157">在“解决方案资源管理器”中，右键单击“维度”\*\*\*\*，然后单击“新建维度”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6766e-157">In Solution Explorer, right-click **Dimensions**, and then click **New Dimension**.</span></span>

2.  <span data-ttu-id="6766e-158">在“欢迎使用维度向导”\*\*\*\* 页上，单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6766e-158">On the **Welcome to the Dimension Wizard** page, click **Next**.</span></span>

3.  <span data-ttu-id="6766e-159">在“选择创建方法”\*\*\*\* 页上，确保选中“使用现有表”\*\*\*\* 选项，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6766e-159">On the **Select Creation Method** page, verify that the **Use an existing table** option is selected, and then click **Next**.</span></span>

4.  <span data-ttu-id="6766e-160">在“指定源信息”\*\*\*\* 页上，确保选中 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012 数据源视图。</span><span class="sxs-lookup"><span data-stu-id="6766e-160">On the **Specify Source Information** page, verify that the [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012 data source view is selected.</span></span>

5.  <span data-ttu-id="6766e-161">在 "**主表**" 列表中，选择 `SalesReason` 。</span><span class="sxs-lookup"><span data-stu-id="6766e-161">In the **Main table** list, select `SalesReason`.</span></span>

6.  <span data-ttu-id="6766e-162">在“键列”\*\*\*\* 列表中，确保列出了“SalesReasonKey”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6766e-162">In the **Key columns** list, verify that **SalesReasonKey** is listed.</span></span>

7.  <span data-ttu-id="6766e-163">在“名称列”\*\*\*\* 列表中，选择“SalesReasonName”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6766e-163">In the **Name column** list, select **SalesReasonName**.</span></span>

8.  <span data-ttu-id="6766e-164">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="6766e-164">Click **Next**.</span></span>

9. <span data-ttu-id="6766e-165">在“选择维度属性”\*\*\*\* 页上，由于“销售原因键”\*\*\*\* 属性是键属性，因此它将自动处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="6766e-165">On the **Select Dimension Attributes** page, the **Sales Reason Key** attribute is automatically selected because it is the key attribute.</span></span> <span data-ttu-id="6766e-166">选中 "**销售原因原因类型**" 属性旁边的复选框，将其名称更改为 `Sales Reason Type` ，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="6766e-166">Select the check box beside the **Sales Reason Reason Type** attribute, change its name to `Sales Reason Type`, and then click **Next**.</span></span>

10. <span data-ttu-id="6766e-167">在“完成向导”\*\*\*\* 页上，单击“完成”\*\*\*\* 创建“销售原因”维度。</span><span class="sxs-lookup"><span data-stu-id="6766e-167">On the **Completing the Wizard** page, click **Finish** to create the Sales Reason dimension.</span></span>

11. <span data-ttu-id="6766e-168">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="6766e-168">On the **File** menu, click **Save All**.</span></span>

12. <span data-ttu-id="6766e-169">在 "**销售原因**" 维度的 "维度设计器" 的 "**属性**" 窗格中，选择 "**销售原因键**"，然后将属性窗口中的 "**名称**" 属性更改为。`Sales Reason.`</span><span class="sxs-lookup"><span data-stu-id="6766e-169">In the **Attributes** pane of the Dimension Designer for the **Sales Reason** dimension, select **Sales Reason Key**, and then change the **Name** property in the Properties window to `Sales Reason.`</span></span>

13. <span data-ttu-id="6766e-170">在维度设计器的 "**层次结构**" 窗格中，以该顺序创建包含 "级别" 和 "销售原因" 级别的 "**销售原因**" 用户层次结构 `Sales Reason Type` **Sales Reason** 。</span><span class="sxs-lookup"><span data-stu-id="6766e-170">In the **Hierarchies** pane of the Dimension Designer, create a **Sales Reasons** user hierarchy that contains the `Sales Reason Type` level and the **Sales Reason** level, in that order.</span></span>

14. <span data-ttu-id="6766e-171">在属性窗口中，将定义 `All Sales Reasons` 为 "销售原因" 层次结构的 " **AllMemberName** " 属性的值。</span><span class="sxs-lookup"><span data-stu-id="6766e-171">In the Properties window, define `All Sales Reasons` as the value for the **AllMemberName** property of the Sales Reasons hierarchy.</span></span>

15. <span data-ttu-id="6766e-172">`All Sales Reasons`将定义为 "销售原因" 维度的 " **AttributeAllMemberName** " 属性的值。</span><span class="sxs-lookup"><span data-stu-id="6766e-172">Define `All Sales Reasons` as the value for **AttributeAllMemberName** property of the Sales Reason dimension.</span></span>

16. <span data-ttu-id="6766e-173">若要将新建的维度作为多维数据集维度添加到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 多维数据集，请切换到“多维数据集设计器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6766e-173">To add the newly created dimension to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube as a cube dimension, switch to **Cube Designer**.</span></span> <span data-ttu-id="6766e-174">在“多维数据集结构”\*\*\*\* 选项卡上，右键单击“维度”\*\*\*\* 窗格，并选择“添加多维数据集维度”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6766e-174">On the **Cube Structure** tab, right-click in the **Dimensions** pane and select **Add Cube Dimension**.</span></span>

17. <span data-ttu-id="6766e-175">在“添加多维数据集维度”\*\*\*\* 对话框中，选择“销售原因”\*\*\*\*，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6766e-175">In the **Add Cube Dimension** dialog box, select **Sales Reason** and then click **OK**.</span></span>

18. <span data-ttu-id="6766e-176">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="6766e-176">On the **File** menu, click **Save All**.</span></span>

## <a name="defining-the-many-to-many-relationship"></a><span data-ttu-id="6766e-177">定义多对多关系</span><span class="sxs-lookup"><span data-stu-id="6766e-177">Defining the Many to Many Relationship</span></span>

1.  <span data-ttu-id="6766e-178">切换到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集的“多维数据集设计器”，再单击“维度用法”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="6766e-178">Switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Dimension Usage** tab.</span></span>

     <span data-ttu-id="6766e-179">请注意，“销售原因”\*\*\*\* 维度定义了与“Internet 销售原因”\*\*\*\* 度量值组的常规关系，但没有定义与“Internet 销售”\*\*\*\* 或“分销商销售”\*\*\*\* 度量值组之间的关系。</span><span class="sxs-lookup"><span data-stu-id="6766e-179">Notice that the **Sales Reason** dimension has a regular relationship defined with the **Internet Sales Reason** measure group, but has no relationship defined with the **Internet Sales** or **Reseller Sales** measure groups.</span></span> <span data-ttu-id="6766e-180">另注意，“Internet 销售订单详细信息”\*\*\*\* 维度定义了与“Internet 销售原因”\*\*\*\* 度量值组的常规关系，后者与“Internet 销售”\*\*\*\* 度量值组具有**事实关系**。</span><span class="sxs-lookup"><span data-stu-id="6766e-180">Notice also that the **Internet Sales Order Details** dimension has a regular relationship defined with the **Internet Sales Reason** dimension, which in turn has a **Fact Relationship** with the **Internet Sales** measure group.</span></span> <span data-ttu-id="6766e-181">如果不存在此维度（或不存在与“Internet 销售原因”\*\*\*\* 和“Internet 销售”\*\*\*\* 度量值组具有关系的其他维度），则无法定义多对多关系。</span><span class="sxs-lookup"><span data-stu-id="6766e-181">If this dimension was not present (or another dimension with a relationship with both the **Internet Sales Reason** and the **Internet Sales** measure group were not present), you would not be able to define the many-to-many relationship.</span></span>

2.  <span data-ttu-id="6766e-182">单击“Internet 销售”\*\*\*\* 度量值组和“销售原因”\*\*\*\* 维度相交处的单元，然后单击浏览按钮 (**...**)。</span><span class="sxs-lookup"><span data-stu-id="6766e-182">Click the cell at the intersection of the **Internet Sales** measure group and the **Sales Reason** dimension and then click the browse button (**...**).</span></span>

3.  <span data-ttu-id="6766e-183">在“定义关系”\*\*\*\* 对话框的“选择关系类型”\*\*\*\* 列表中，选择“多对多”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6766e-183">In the **Define Relationship** dialog box, select **Many-to-Many** in the **Select relationship type** list.</span></span>

     <span data-ttu-id="6766e-184">必须定义将“销售原因”维度连接到“Internet 销售”度量值组的中间度量值组。</span><span class="sxs-lookup"><span data-stu-id="6766e-184">You have to define the intermediate measure group that connects the Sales Reason dimension to the Internet Sales measure group.</span></span>

4.  <span data-ttu-id="6766e-185">在“中间度量值组”\*\*\*\* 列表中，选择“Internet 销售原因”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6766e-185">In the **Intermediate measure group** list, select **Internet Sales Reason**.</span></span>

     <span data-ttu-id="6766e-186">下图显示了“定义关系”\*\*\*\* 对话框中的更改。</span><span class="sxs-lookup"><span data-stu-id="6766e-186">The following image shows the changes in the **Define Relationship** dialog box.</span></span>

     <span data-ttu-id="6766e-187">!["定义关系" 对话框](../../2014/tutorials/media/l5-many-to-many-3.gif "“定义关系”对话框")</span><span class="sxs-lookup"><span data-stu-id="6766e-187">![Define Relationship dialog box](../../2014/tutorials/media/l5-many-to-many-3.gif "Define Relationship dialog box")</span></span>

5.  <span data-ttu-id="6766e-188">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="6766e-188">Click **OK**.</span></span>

     <span data-ttu-id="6766e-189">您将看到表示“销售原因”维度和“Internet 销售”度量值组之间关系的多对多图标。</span><span class="sxs-lookup"><span data-stu-id="6766e-189">Notice the many-to-many icon that represents the relationship between the Sales Reason dimension and the Internet Sales measure group.</span></span>

## <a name="browsing-the-cube-and-the-many-to-many-dimension"></a><span data-ttu-id="6766e-190">浏览多维数据集和多对多维度</span><span class="sxs-lookup"><span data-stu-id="6766e-190">Browsing the Cube and the Many-to-Many Dimension</span></span>

1.  <span data-ttu-id="6766e-191">在“生成”\*\*\*\* 菜单上，单击“部署 Analysis Services 教程”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6766e-191">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>

2.  <span data-ttu-id="6766e-192">成功完成部署后，切换到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集的“多维数据集设计器”中的“浏览器”\*\*\*\* 选项卡，然后单击“重新连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6766e-192">When deployment has successfully completed, switch to the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click **Reconnect**.</span></span>

3.  <span data-ttu-id="6766e-193">将“Internet 销售-销售额”\*\*\*\* 度量值添加到数据窗格的数据区域。</span><span class="sxs-lookup"><span data-stu-id="6766e-193">Add the **Internet Sales-Sales Amount** measure to the data area of the data pane.</span></span>

4.  <span data-ttu-id="6766e-194">将“销售原因”\*\*\*\* 维度的“销售原因”\*\*\*\* 用户定义层次结构添加到数据窗格的行区域。</span><span class="sxs-lookup"><span data-stu-id="6766e-194">Add the **Sales Reasons** user-defined hierarchy from the **Sales Reason** dimension to the row area of the data pane.</span></span>

5.  <span data-ttu-id="6766e-195">在元数据窗格中，依次展开“客户”\*\*\*\*、“位置”\*\*\*\*、“客户所在地域”\*\*\*\*、“成员”\*\*\*\*、“所有客户”\*\*\*\*、“澳大利亚”\*\*\*\*，然后右键单击“Queensland”\*\*\*\*，再单击“添加到筛选器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6766e-195">In the metadata pane, expand **Customer**, expand **Location**, expand **Customer Geography**, expand **Members**, expand **All Customers**, expand **Australia**, right-click **Queensland**, and then click **Add to Filter**.</span></span>

6.  <span data-ttu-id="6766e-196">展开级别的每个成员 `Sales Reason Type` ，以查看与 Queensland 中的客户为其通过 Internet 购买产品的每个原因相关联的美元值 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6766e-196">Expand each member of the `Sales Reason Type` level to review the dollar values that are associated with each reason a customer in Queensland gave for their purchase of an [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] product over the Internet.</span></span>

     <span data-ttu-id="6766e-197">您会看到与所有销售原因相关联的合计超过了销售总额。</span><span class="sxs-lookup"><span data-stu-id="6766e-197">Notice that the totals that are associated with each sales reason add up to more than the total sales.</span></span> <span data-ttu-id="6766e-198">这是因为某些客户为其采购陈述了多个原因。</span><span class="sxs-lookup"><span data-stu-id="6766e-198">This is because some customers cited multiple reasons for their purchase.</span></span>

     <span data-ttu-id="6766e-199">下图显示了“多维数据集设计器”的“筛选器”\*\*\*\* 窗格和“数据”\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="6766e-199">The following image shows the **Filter** pane and **Data** pane of Cube Designer.</span></span>

     <span data-ttu-id="6766e-200">![多维数据集设计器的“筛选器”窗格和“数据”窗格](../../2014/tutorials/media/l5-many-to-many-5.gif "多维数据集设计器的“筛选器”窗格和“数据”窗格")</span><span class="sxs-lookup"><span data-stu-id="6766e-200">![Filter and Data panes of Cube Designer](../../2014/tutorials/media/l5-many-to-many-5.gif "Filter and Data panes of Cube Designer")</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="6766e-201">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="6766e-201">Next Task in Lesson</span></span>
 [<span data-ttu-id="6766e-202">定义度量值组中的维度粒度</span><span class="sxs-lookup"><span data-stu-id="6766e-202">Defining Dimension Granularity within a Measure Group</span></span>](lesson-5-4-defining-dimension-granularity-within-a-measure-group.md)

## <a name="see-also"></a><span data-ttu-id="6766e-203">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6766e-203">See Also</span></span>
 <span data-ttu-id="6766e-204">[使用数据源视图设计器中的关系图 &#40;Analysis Services&#41;](multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md) [维度关系](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)[定义多对多关系和多对多关系属性](multidimensional-models/define-a-many-to-many-relationship-and-many-to-many-relationship-properties.md)</span><span class="sxs-lookup"><span data-stu-id="6766e-204">[Work with Diagrams in Data Source View Designer &#40;Analysis Services&#41;](multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md) [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) [Define a Many-to-Many Relationship and Many-to-Many Relationship Properties](multidimensional-models/define-a-many-to-many-relationship-and-many-to-many-relationship-properties.md)</span></span>


