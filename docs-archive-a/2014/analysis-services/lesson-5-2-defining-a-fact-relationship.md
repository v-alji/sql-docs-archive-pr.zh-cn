---
title: 定义事实关系 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4b49a078-6848-4286-bc71-cf4862d29064
author: minewiskan
ms.author: owend
ms.openlocfilehash: 26f8068301c424d5aea9f54e882ceb8a4dc72806
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590958"
---
# <a name="defining-a-fact-relationship"></a><span data-ttu-id="e4351-102">定义事实关系</span><span class="sxs-lookup"><span data-stu-id="e4351-102">Defining a Fact Relationship</span></span>
  <span data-ttu-id="e4351-103">用户有时需要按事实数据表中的数据项定义度量值的维度，或者查询事实数据表中其他特定的相关信息，例如与特定销售情况有关的发票号或采购订单号。</span><span class="sxs-lookup"><span data-stu-id="e4351-103">Users sometimes want to be able to dimension measures by data items that are in the fact table or to query the fact table for specific additional related information, such as invoice numbers or purchase order numbers related to specific sales facts.</span></span> <span data-ttu-id="e4351-104">当根据此类事实数据表项定义维度时，则将该维度称为“事实维度”\*\*。</span><span class="sxs-lookup"><span data-stu-id="e4351-104">When you define a dimension based on such a fact table item, the dimension is called a *fact dimension*.</span></span> <span data-ttu-id="e4351-105">事实维度也称为退化维度。</span><span class="sxs-lookup"><span data-stu-id="e4351-105">Fact dimensions are also known as degenerate dimensions.</span></span> <span data-ttu-id="e4351-106">若要将相关的事实数据表行（例如所有与特定发票号有关的行）组合在一起，事实维度将非常有用。</span><span class="sxs-lookup"><span data-stu-id="e4351-106">Fact dimensions are useful for grouping together related fact table rows, such as all the rows that are related to a particular invoice number.</span></span> <span data-ttu-id="e4351-107">尽管可以将此信息置于关系数据库中一个单独的维度表内，但为此信息创建单独的维度表没有任何益处，因为维度表与事实数据表按照同一速度增长，只会创建重复的数据并增加不必要的复杂性。</span><span class="sxs-lookup"><span data-stu-id="e4351-107">Although you can put this information in a separate dimension table in the relational database, creating a separate dimension table for the information provides no benefit because the dimension table would grow at the same rate as the fact table, and would just create duplicate data and unnecessary complexity.</span></span>

 <span data-ttu-id="e4351-108">在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]内，您可以确定是否在 MOLAP 维度结构中复制事实维度数据以提高查询性能，或者是否将事实维度定义为 ROLAP 维度，以节省存储空间，但要牺牲查询性能。</span><span class="sxs-lookup"><span data-stu-id="e4351-108">Within [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], you can determine whether to duplicate the fact dimension data in a MOLAP dimension structure for increased query performance, or whether to define the fact dimension as a ROLAP dimension to save storage space at the expense of query performance.</span></span> <span data-ttu-id="e4351-109">以 MOLAP 存储模式存储维度时，除了在度量值组的分区中存储维度成员外，所有维度成员还都存储在高度压缩的 MOLAP 结构的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例内。</span><span class="sxs-lookup"><span data-stu-id="e4351-109">When you store a dimension with the MOLAP storage mode, all the dimension members are stored in the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] in a highly compressed MOLAP structure, in addition to being stored in the measure group's partitions.</span></span> <span data-ttu-id="e4351-110">当您使用 ROLAP 存储模式存储维度时，只有维度定义存储在 MOLAP 结构中，维度成员本身在查询时从基础关系事实数据表中查询。</span><span class="sxs-lookup"><span data-stu-id="e4351-110">When you store a dimension with the ROLAP storage mode, only the dimension definition is stored in the MOLAP structure-the dimension members themselves are queried from the underlying relational fact table at query time.</span></span> <span data-ttu-id="e4351-111">可以根据事实维度的查询频率、典型查询返回的行数、查询的性能以及处理成本来确定适当的存储模式。</span><span class="sxs-lookup"><span data-stu-id="e4351-111">You decide the appropriate storage mode based on how frequently the fact dimension is queried, the number of rows returned by a typical query, the performance of the query, and the processing cost.</span></span> <span data-ttu-id="e4351-112">将维度定义为 ROLAP 时，并不要求使用该维度的所有多维数据集也以 ROLAP 存储模式进行存储。</span><span class="sxs-lookup"><span data-stu-id="e4351-112">Defining a dimension as ROLAP does not require that all cubes that use the dimension also be stored with the ROLAP storage mode.</span></span> <span data-ttu-id="e4351-113">可以对每个维度的存储模式单独进行配置。</span><span class="sxs-lookup"><span data-stu-id="e4351-113">The storage mode for each dimension can be configured independently.</span></span>

 <span data-ttu-id="e4351-114">定义事实维度时，可以将事实维度和度量值组之间的关系定义为事实关系。</span><span class="sxs-lookup"><span data-stu-id="e4351-114">When you define a fact dimension, you can define the relationship between the fact dimension and the measure group as a fact relationship.</span></span> <span data-ttu-id="e4351-115">以下约束适用于事实关系：</span><span class="sxs-lookup"><span data-stu-id="e4351-115">The following constraints apply to fact relationships:</span></span>

-   <span data-ttu-id="e4351-116">粒度属性必须是维度的键列，该键列将在维度和事实数据表中的事实之间创建一对一关系。</span><span class="sxs-lookup"><span data-stu-id="e4351-116">The granularity attribute must be the key column for the dimension, which creates a one-to-one relationship between the dimension and the facts in the fact table.</span></span>

-   <span data-ttu-id="e4351-117">一个维度只能与一个单一的度量值组具有一种事实关系。</span><span class="sxs-lookup"><span data-stu-id="e4351-117">A dimension can have a fact relationship with only a single measure group.</span></span>

> [!NOTE]
>  <span data-ttu-id="e4351-118">在每次对事实关系所引用的度量值组进行更新后，事实维度必须进行增量更新。</span><span class="sxs-lookup"><span data-stu-id="e4351-118">Fact dimensions must be incrementally updated after every update to the measure group that the fact relationship references.</span></span>

 <span data-ttu-id="e4351-119">有关详细信息，请参阅 [维度关系](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)和 [定义事实关系和事实关系属性](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="e4351-119">For more information, see [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md), and [Define a Fact Relationship and Fact Relationship Properties](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md).</span></span>

 <span data-ttu-id="e4351-120">在本主题的各任务中，你将根据“CustomerPONumber”\*\*\*\* 列在“FactInternetSales”\*\*\*\* 事实数据表中添加新的多维数据集维度。</span><span class="sxs-lookup"><span data-stu-id="e4351-120">In the tasks in this topic, you add a new cube dimension based on the **CustomerPONumber** column in the **FactInternetSales** fact table.</span></span> <span data-ttu-id="e4351-121">然后将此新增多维数据集维度和“Internet 销售”\*\*\*\* 度量值组之间的关系定义为事实关系。</span><span class="sxs-lookup"><span data-stu-id="e4351-121">You then define the relationship between this new cube dimension and the **Internet Sales** measure group as a fact relationship.</span></span>

## <a name="defining-the-internet-sales-orders-fact-dimension"></a><span data-ttu-id="e4351-122">定义“Internet 销售订单”事实维度</span><span class="sxs-lookup"><span data-stu-id="e4351-122">Defining the Internet Sales Orders Fact Dimension</span></span>

1.  <span data-ttu-id="e4351-123">在“解决方案资源管理器”中，右键单击“维度”\*\*\*\*，然后单击“新建维度”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e4351-123">In Solution Explorer, right-click **Dimensions**, and then click **New Dimension**.</span></span>

2.  <span data-ttu-id="e4351-124">在“欢迎使用维度向导”\*\*\*\* 页上，单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e4351-124">On the **Welcome to the Dimension Wizard** page, click **Next**.</span></span>

3.  <span data-ttu-id="e4351-125">在“选择创建方法”\*\*\*\* 页上，确保选中“使用现有表”\*\*\*\* 选项，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e4351-125">On the **Select Creation Method** page, verify that the **Use an existing table** option is selected, and then click **Next**.</span></span>

4.  <span data-ttu-id="e4351-126">在“指定源信息”\*\*\*\* 页上，确保选中“Adventure Works DW 2012”\*\*\*\* 数据源视图。</span><span class="sxs-lookup"><span data-stu-id="e4351-126">On the **Specify Source Information** page, verify that the **Adventure Works DW 2012** data source view is selected.</span></span>

5.  <span data-ttu-id="e4351-127">在“主表”\*\*\*\* 列表中，选择“InternetSales”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e4351-127">In the **Main table** list, select **InternetSales**.</span></span>

6.  <span data-ttu-id="e4351-128">在“键列”\*\*\*\* 列表中，确保列出了“SalesOrderNumber”\*\*\*\* 和“SalesOrderLineNumber”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e4351-128">In the **Key columns** list, verify that **SalesOrderNumber** and **SalesOrderLineNumber** are listed.</span></span>

7.  <span data-ttu-id="e4351-129">在“名称列”\*\*\*\* 列表中，选择“SalesOrderLineNumber”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e4351-129">In the **Name column** list, select **SalesOrderLineNumber**.</span></span>

8.  <span data-ttu-id="e4351-130">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="e4351-130">Click **Next**.</span></span>

9. <span data-ttu-id="e4351-131">在“选择相关表”\*\*\*\* 页面上，清除所有表旁边的复选框，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e4351-131">On the **Select Related Tables** page, clear the check boxes beside all of the tables, and then click **Next**.</span></span>

10. <span data-ttu-id="e4351-132">在“选择维度属性”\*\*\*\* 页面上，请单击页眉内的复选框两次，以清除所有复选框。</span><span class="sxs-lookup"><span data-stu-id="e4351-132">On the **Select Dimension Attributes** page, click the check box in the header twice to clear all of the check boxes.</span></span> <span data-ttu-id="e4351-133">“销售订单号”\*\*\*\* 属性将保持选中状态，因为它是键属性。</span><span class="sxs-lookup"><span data-stu-id="e4351-133">The **Sales Order Number** attribute will remain selected because it is the key attribute.</span></span>

11. <span data-ttu-id="e4351-134">选择“客户 PO 编号”\*\*\*\* 属性，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e4351-134">Select the **Customer PO Number** attribute, and then click **Next**.</span></span>

12. <span data-ttu-id="e4351-135">在“完成向导”\*\*\*\* 页上，将名称更改为“Internet 销售订单详细信息”\*\*\*\*，然后单击“完成”\*\*\*\* 来完成向导。</span><span class="sxs-lookup"><span data-stu-id="e4351-135">On the **Completing the Wizard** page, change the name to **Internet Sales Order Details** and then click **Finish** to complete the wizard.</span></span>

13. <span data-ttu-id="e4351-136">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="e4351-136">On the **File** menu, click **Save All**.</span></span>

14. <span data-ttu-id="e4351-137">在 " **Internet 销售订单详细信息**" 维度的 "维度设计器" 的 "**属性**" 窗格中，选择 "**销售订单号**"，然后将 "属性窗口中的"**名称**"属性更改为`Item Description.`</span><span class="sxs-lookup"><span data-stu-id="e4351-137">In the **Attributes** pane of the Dimension Designer for the **Internet Sales Order Details** dimension, select **Sales Order Number**, and then change the **Name** property in the Properties window to `Item Description.`</span></span>

15. <span data-ttu-id="e4351-138">在**NameColumn**属性单元中，单击 "浏览" 按钮\*\* ( ... ") **。在 "**名称列**" 对话框中，从 "**源表**" 列表中选择 "**产品**"，选择 " **EnglishProductName** " 作为 "**源" 列\*\*，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="e4351-138">In the **NameColumn** property cell, click the browse button **(...)**. In the **Name Column** dialog box, select **Product** from the **Source table** list, select **EnglishProductName** for the **Source column**, and then click **OK**.</span></span>

16. <span data-ttu-id="e4351-139">将“数据源视图”\*\*\*\* 窗格中“InternetSales”\*\*\*\* 表内的“SalesOrderNumber”\*\*\*\* 列拖到“特性”\*\*\*\* 窗格，以将“销售订单编号”\*\*\*\* 属性添加到维度中。</span><span class="sxs-lookup"><span data-stu-id="e4351-139">Add the **Sales Order Number** attribute to the dimension by dragging the **SalesOrderNumber** column from the **InternetSales** table in the **Data Source View** pane to the **Attributes** pane.</span></span>

17. <span data-ttu-id="e4351-140">将新的 "**销售订单编号**" 属性的 "**名称**" 属性更改为 `Order Number` ，并将 " **OrderBy** " 属性更改为 "**键**"。</span><span class="sxs-lookup"><span data-stu-id="e4351-140">Change the **Name** property of the new **Sales Order Number** attribute to `Order Number`, and change the **OrderBy** property to **Key**.</span></span>

18. <span data-ttu-id="e4351-141">在 "**层次结构**" 窗格中，按顺序创建包含和项说明级别的 " **Internet 销售订单**" 用户层次结构 `Order Number` 。 **Item Description**</span><span class="sxs-lookup"><span data-stu-id="e4351-141">In the **Hierarchies** pane, create an **Internet Sales Orders** user hierarchy that contains the `Order Number` and **Item Description** levels, in that order.</span></span>

19. <span data-ttu-id="e4351-142">在 **“特性”** 窗格中，选择 **“Internet 销售订单详细信息”**，然后查看“属性”窗口中 **StorageMode** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="e4351-142">In the **Attributes** pane, select **Internet Sales Order Details**, and then review the value for the **StorageMode** property in the Properties window.</span></span>

     <span data-ttu-id="e4351-143">注意，该维度默认存储为 MOLAP 维度。</span><span class="sxs-lookup"><span data-stu-id="e4351-143">Notice that, by default, this dimension is stored as a MOLAP dimension.</span></span> <span data-ttu-id="e4351-144">尽管将存储模式更改为 ROLAP 可以节省处理时间和存储空间，但这样做将降低查询性能。</span><span class="sxs-lookup"><span data-stu-id="e4351-144">Although changing the storage mode to ROLAP will save processing time and storage space, it occurs at the expense of query performance.</span></span> <span data-ttu-id="e4351-145">为了实现本教程教学目的，您将使用 MOLAP 作为存储模式。</span><span class="sxs-lookup"><span data-stu-id="e4351-145">For the purposes of this tutorial, you will use MOLAP as the storage mode.</span></span>

20. <span data-ttu-id="e4351-146">若要将新建的维度作为多维数据集维度添加到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 多维数据集，请切换到“多维数据集设计器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e4351-146">To add the newly created dimension to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube as a cube dimension, switch to **Cube Designer**.</span></span> <span data-ttu-id="e4351-147">在“多维数据集结构”\*\*\*\* 选项卡上，右键单击“维度”\*\*\*\* 窗格，并选择“添加多维数据集维度”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e4351-147">On the **Cube Structure** tab, right-click in the **Dimensions** pane and select **Add Cube Dimension**.</span></span>

21. <span data-ttu-id="e4351-148">在“添加多维数据集维度”\*\*\*\* 对话框中，选择“Internet 销售订单详细信息”\*\*\*\*，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e4351-148">In the **Add Cube Dimension**.dialog box, select **Internet Sales Order Details** and then click **OK**.</span></span>

## <a name="defining-a-fact-relationship-for-the-fact-dimension"></a><span data-ttu-id="e4351-149">定义事实维度的事实关系</span><span class="sxs-lookup"><span data-stu-id="e4351-149">Defining a Fact Relationship for the Fact Dimension</span></span>

1.  <span data-ttu-id="e4351-150">在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集的多维数据集设计器中，单击“维度用法”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="e4351-150">In the Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, click the **Dimension Usage** tab.</span></span>

     <span data-ttu-id="e4351-151">注意，“Internet 销售订单详细信息”\*\*\*\* 多维数据集维度自动配置为具有事实关系，如唯一图标所示。</span><span class="sxs-lookup"><span data-stu-id="e4351-151">Notice that the **Internet Sales Order Details** cube dimension is automatically configured as having a fact relationship, as shown by the unique icon.</span></span>

2.  <span data-ttu-id="e4351-152">在 " **Internet 销售**" 度量值组和 " **Internet 销售订单详细信息**" 维度相交处的 "**项说明**" 单元中，单击 "浏览" 按钮 () **...** "，以查看事实关系属性。</span><span class="sxs-lookup"><span data-stu-id="e4351-152">Click the browse button (**...**) in the **Item Description** cell, at the intersection of the **Internet Sales** measure group and the **Internet Sales Order Details** dimension, to review the fact relationship properties.</span></span>

     <span data-ttu-id="e4351-153">将打开“定义关系”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="e4351-153">The **Define Relationship** dialog box opens.</span></span> <span data-ttu-id="e4351-154">注意，您无法配置任何一种属性。</span><span class="sxs-lookup"><span data-stu-id="e4351-154">Notice that you cannot configure any of the properties.</span></span>

     <span data-ttu-id="e4351-155">下图显示了“定义关系”\*\*\*\* 对话框中的事实关系属性。</span><span class="sxs-lookup"><span data-stu-id="e4351-155">The following image shows the fact relationship properties in the **Define Relationship** dialog box.</span></span>

     <span data-ttu-id="e4351-156">!["定义关系" 对话框](../../2014/tutorials/media/l5-factrelationship-2.gif "“定义关系”对话框")</span><span class="sxs-lookup"><span data-stu-id="e4351-156">![Define Relationship dialog box](../../2014/tutorials/media/l5-factrelationship-2.gif "Define Relationship dialog box")</span></span>

3.  <span data-ttu-id="e4351-157">单击“取消” 。</span><span class="sxs-lookup"><span data-stu-id="e4351-157">Click **Cancel**.</span></span>

## <a name="browsing-the-cube-by-using-the-fact-dimension"></a><span data-ttu-id="e4351-158">使用事实维度浏览多维数据集</span><span class="sxs-lookup"><span data-stu-id="e4351-158">Browsing the Cube by Using the Fact Dimension</span></span>

1.  <span data-ttu-id="e4351-159">在“生成”\*\*\*\* 菜单上，单击“部署 Analysis Services 教程”\*\*\*\*，以将更改部署到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 的实例中，并处理数据库。</span><span class="sxs-lookup"><span data-stu-id="e4351-159">On the **Build** menu, click **Deploy Analysis Services Tutorial** to deploy the changes to the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and process the database.</span></span>

2.  <span data-ttu-id="e4351-160">在部署成功完成时，在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集的多维数据集设计器中单击“浏览器”\*\*\*\* 选项卡，再单击“重新连接”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="e4351-160">After deployment has successfully completed, click the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Reconnect** button.</span></span>

3.  <span data-ttu-id="e4351-161">清除“数据”窗格中的所有度量值和层次结构，然后将“Internet 销售-销售额”\*\*\*\* 度量值添加到“数据”窗格的数据区域。</span><span class="sxs-lookup"><span data-stu-id="e4351-161">Clear all measures and hierarchies from the data pane, and then add the **Internet Sales-Sales Amount** measure to the data area of the data pane.</span></span>

4.  <span data-ttu-id="e4351-162">在“元数据”窗格中，依次展开“客户”\*\*\*\*、“位置”\*\*\*\*、“客户所在地域”\*\*\*\*、“成员”\*\*\*\*、“所有客户”\*\*\*\*、“Australia”\*\*\*\*、“Queensland”\*\*\*\*、“Brisbane”\*\*\*\*、“4000”\*\*\*\*，右键单击“Adam Powell”\*\*\*\*，然后单击“添加到筛选器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e4351-162">In the metadata pane, expand **Customer**, expand **Location**, expand **Customer Geography**, expand **Members**, expand **All Customers**, expand **Australia**, expand **Queensland**, expand **Brisbane**, expand **4000**, right-click **Adam Powell**, and then click **Add to Filter**.</span></span>

     <span data-ttu-id="e4351-163">通过筛选将销售订单限制为返回给单个客户的销售订单，可使用户深入了解大型事实数据表中的基础细节，而不会显著降低查询性能。</span><span class="sxs-lookup"><span data-stu-id="e4351-163">Filtering to limit the sales orders returned to a single customer lets the user drill down to the underlying detail in a large fact table without suffering a significant loss in query performance.</span></span>

5.  <span data-ttu-id="e4351-164">将“Internet 销售订单详细信息”\*\*\*\* 维度的“Internet 销售订单”\*\*\*\* 用户定义层次结构添加到“数据”窗格的行区域。</span><span class="sxs-lookup"><span data-stu-id="e4351-164">Add the **Internet Sales Orders** user-defined hierarchy from the **Internet Sales Order Details** dimension to the row area of the data pane.</span></span>

     <span data-ttu-id="e4351-165">注意，Adam Powell 的销售订单号和对应的 Internet 销售量将出现在“数据”窗格中。</span><span class="sxs-lookup"><span data-stu-id="e4351-165">Notice that the sales order numbers and the corresponding Internet sales amounts for Adam Powell appear in the data pane.</span></span>

     <span data-ttu-id="e4351-166">下图显示了上述步骤的结果。</span><span class="sxs-lookup"><span data-stu-id="e4351-166">The following image shows the result of the previous steps.</span></span>

     <span data-ttu-id="e4351-167">![“Internet 销售-销售额”的维度划分](../../2014/tutorials/media/l5-factrelationship-3.gif "“Internet 销售-销售额”的维度划分")</span><span class="sxs-lookup"><span data-stu-id="e4351-167">![Dimensioning of Internet Sales-Sales Amount](../../2014/tutorials/media/l5-factrelationship-3.gif "Dimensioning of Internet Sales-Sales Amount")</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="e4351-168">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="e4351-168">Next Task in Lesson</span></span>
 [<span data-ttu-id="e4351-169">定义多对多关系</span><span class="sxs-lookup"><span data-stu-id="e4351-169">Defining a Many-to-Many Relationship</span></span>](lesson-5-3-defining-a-many-to-many-relationship.md)

## <a name="see-also"></a><span data-ttu-id="e4351-170">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e4351-170">See Also</span></span>
 <span data-ttu-id="e4351-171">[维度关系](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)[定义事实关系和事实关系属性](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md)</span><span class="sxs-lookup"><span data-stu-id="e4351-171">[Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) [Define a Fact Relationship and Fact Relationship Properties](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md)</span></span>


