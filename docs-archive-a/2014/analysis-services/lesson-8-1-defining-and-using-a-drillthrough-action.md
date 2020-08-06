---
title: 定义和使用钻取操作 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 3765f865-2b93-44be-b290-28e3815d5ecb
author: minewiskan
ms.author: owend
ms.openlocfilehash: ea19a9721d87936bc88b5401c71ee550a47bc1ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689086"
---
# <a name="defining-and-using-a-drillthrough-action"></a><span data-ttu-id="d1def-102">定义和使用钻取操作</span><span class="sxs-lookup"><span data-stu-id="d1def-102">Defining and Using a Drillthrough Action</span></span>
  <span data-ttu-id="d1def-103">如果按事实维度来维度化事实数据，而不正确筛选查询返回的数据，则可能导致查询速度变慢。</span><span class="sxs-lookup"><span data-stu-id="d1def-103">Dimensioning fact data by a fact dimension without correctly filtering the data that the query returns can cause slow query performance.</span></span> <span data-ttu-id="d1def-104">若要避免出现这种情况，可以定义对返回的总行数进行限制的钻取操作。</span><span class="sxs-lookup"><span data-stu-id="d1def-104">To avoid this, you can define a drillthrough action that restricts the total number of rows that are returned.</span></span> <span data-ttu-id="d1def-105">这将极大地提高查询性能。</span><span class="sxs-lookup"><span data-stu-id="d1def-105">This will significantly improve query performance.</span></span>  
  
 <span data-ttu-id="d1def-106">在本主题的任务中，将定义钻取操作，以返回通过 Internet 对客户进行销售的订单详细信息。</span><span class="sxs-lookup"><span data-stu-id="d1def-106">In the tasks in this topic, you define a drillthrough action to return order detail information for sales to customers over the Internet.</span></span>  
  
## <a name="defining-the-drillthrough-action-properties"></a><span data-ttu-id="d1def-107">定义钻取操作属性</span><span class="sxs-lookup"><span data-stu-id="d1def-107">Defining the Drillthrough Action Properties</span></span>  
  
1.  <span data-ttu-id="d1def-108">在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集的多维数据集设计器中，单击“操作”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="d1def-108">In Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, click the **Actions** tab.</span></span>  
  
     <span data-ttu-id="d1def-109">“操作”\*\*\*\* 选项卡中包括几个窗格。</span><span class="sxs-lookup"><span data-stu-id="d1def-109">The **Actions** tab includes several panes.</span></span> <span data-ttu-id="d1def-110">在选项卡的左侧是“操作组织程序”\*\*\*\* 窗格和“计算工具”\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="d1def-110">On the left side of the tab are the **Action Organizer** pane and the **Calculation Tools** pane.</span></span> <span data-ttu-id="d1def-111">这两个窗格的右侧是“显示”\*\*\*\* 窗格，其中可以显示“操作组织程序”\*\*\*\* 窗格中所选操作的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d1def-111">The pane to the right of these two panes is the **Display** pane, which contains the details of the action that is selected in the **Action Organizer** pane.</span></span>  
  
     <span data-ttu-id="d1def-112">下图显示了多维数据集设计器的“操作”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="d1def-112">The following image shows the **Actions** tab of Cube Designer.</span></span>  
  
     <span data-ttu-id="d1def-113">![多维数据集设计器的“操作”选项卡](../../2014/tutorials/media/l8-action1.gif "多维数据集设计器的“操作”选项卡")</span><span class="sxs-lookup"><span data-stu-id="d1def-113">![Actions tab of Cube Designer](../../2014/tutorials/media/l8-action1.gif "Actions tab of Cube Designer")</span></span>  
  
2.  <span data-ttu-id="d1def-114">在“操作”\*\*\*\* 选项卡的工具栏上，单击“新建钻取操作”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="d1def-114">On the toolbar of the **Actions** tab, click the **New Drillthrough Action** button.</span></span>  
  
     <span data-ttu-id="d1def-115">“显示”窗格中将出现空白操作模板。</span><span class="sxs-lookup"><span data-stu-id="d1def-115">A blank action template appears in the display pane.</span></span>  
  
     <span data-ttu-id="d1def-116">![显示窗格中的空白操作模板](../../2014/tutorials/media/l8-action2.gif "显示窗格中的空白操作模板")</span><span class="sxs-lookup"><span data-stu-id="d1def-116">![Blank Action template in the display pane](../../2014/tutorials/media/l8-action2.gif "Blank Action template in the display pane")</span></span>  
  
3.  <span data-ttu-id="d1def-117">在 "**名称**" 框中，将此操作的名称更改为 `Internet Sales Details Drillthrough Action` 。</span><span class="sxs-lookup"><span data-stu-id="d1def-117">In the **Name** box, change the name of this action to `Internet Sales Details Drillthrough Action`.</span></span>  
  
4.  <span data-ttu-id="d1def-118">在“度量值组成员”\*\*\*\* 列表中，选择“Internet 销售”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d1def-118">In the **Measure group members** list, select **Internet Sales**.</span></span>  
  
5.  <span data-ttu-id="d1def-119">在“钻取列”\*\*\*\* 框中，选择“维度”\*\*\*\* 列表中的“Internet 销售订单详细信息”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d1def-119">In the **Drillthrough Columns** box, select **Internet Sales Order Details** in the **Dimensions** list.</span></span>  
  
6.  <span data-ttu-id="d1def-120">在“返回列”\*\*\*\* 列表中，选中“项说明”\*\*\*\* 和“订单编号”\*\*\*\* 复选框，再单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d1def-120">In the **Return Columns** list, select the **Item Description** and the **Order Number** check boxes, and then click **OK**.</span></span> <span data-ttu-id="d1def-121">下图显示至此在该操作过程中操作模板的应有外观。</span><span class="sxs-lookup"><span data-stu-id="d1def-121">The following image shows the Action template as it should appear at this point in this procedure.</span></span>  
  
     <span data-ttu-id="d1def-122">![“钻取列”框](../../2014/tutorials/media/l8-action3.gif "“钻取列”框")</span><span class="sxs-lookup"><span data-stu-id="d1def-122">![Drillthrough Columns box](../../2014/tutorials/media/l8-action3.gif "Drillthrough Columns box")</span></span>  
  
7.  <span data-ttu-id="d1def-123">展开“附加属性”\*\*\*\* 框，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="d1def-123">Expand the **Additional Properties** box, as shown in the following image.</span></span>  
  
     <span data-ttu-id="d1def-124">![“附加属性”框](../../2014/tutorials/media/l8-action4.gif "“附加属性”框")</span><span class="sxs-lookup"><span data-stu-id="d1def-124">![Additional Properties box](../../2014/tutorials/media/l8-action4.gif "Additional Properties box")</span></span>  
  
8.  <span data-ttu-id="d1def-125">在 "**最大行数**" 框中，键入 `10` 。</span><span class="sxs-lookup"><span data-stu-id="d1def-125">In the **Maximum Rows** box, type `10`.</span></span>  
  
9. <span data-ttu-id="d1def-126">在 "**标题**" 框中，键入 `Drillthrough to Order Details...` 。</span><span class="sxs-lookup"><span data-stu-id="d1def-126">In the **Caption** box, type `Drillthrough to Order Details...`.</span></span>  
  
     <span data-ttu-id="d1def-127">这些设置将限制返回的行数，并指定在客户端应用程序菜单中将出现的标题。</span><span class="sxs-lookup"><span data-stu-id="d1def-127">These settings limit the number of rows returned and specify the caption that appears in the client application menu.</span></span> <span data-ttu-id="d1def-128">下图显示了“附加属性”\*\*\*\* 框中的这些设置。</span><span class="sxs-lookup"><span data-stu-id="d1def-128">The following image shows these settings in the **AdditionalProperties** box.</span></span>  
  
     <span data-ttu-id="d1def-129">![“附加属性”框](../../2014/tutorials/media/l8-action5.gif "“附加属性”框")</span><span class="sxs-lookup"><span data-stu-id="d1def-129">![Additional Properties box](../../2014/tutorials/media/l8-action5.gif "Additional Properties box")</span></span>  
  
## <a name="using-the-drillthrough-action"></a><span data-ttu-id="d1def-130">使用钻取操作</span><span class="sxs-lookup"><span data-stu-id="d1def-130">Using the Drillthrough Action</span></span>  
  
1.  <span data-ttu-id="d1def-131">在“生成”\*\*\*\* 菜单上，单击“部署 Analysis Services 教程”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d1def-131">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="d1def-132">在部署成功完成后，在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集的多维数据集设计器中单击“浏览器”\*\*\*\* 选项卡，再单击“重新连接”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="d1def-132">When deployment has successfully completed, click the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Reconnect** button.</span></span>  
  
3.  <span data-ttu-id="d1def-133">启动 Excel。</span><span class="sxs-lookup"><span data-stu-id="d1def-133">Start Excel.</span></span>  
  
4.  <span data-ttu-id="d1def-134">将“Internet 销售 - 销售额”\*\*\*\* 度量值添加到“值”区域。</span><span class="sxs-lookup"><span data-stu-id="d1def-134">Add the **Internet Sales-Sales Amount** measure to the Values area.</span></span>  
  
5.  <span data-ttu-id="d1def-135">将“客户所在地域”\*\*\*\* 用户定义层次结构从“客户”\*\*\*\* 维度的“位置”\*\*\*\* 文件夹添加到“报表筛选器”\*\*\*\* 区域。</span><span class="sxs-lookup"><span data-stu-id="d1def-135">Add the **Customer Geography** user-defined hierarchy from the **Location** folder in the **Customer** dimension to the **Report Filter** area.</span></span>  
  
6.  <span data-ttu-id="d1def-136">在数据透视表上的“客户所在地域”\*\*\*\* 中，添加选择单个客户的筛选器。</span><span class="sxs-lookup"><span data-stu-id="d1def-136">On the PivotTable, in **Customer Geography**, add a filter that selects a single customer.</span></span> <span data-ttu-id="d1def-137">依次展开“全部客户”\*\*\*\*、**Australia**、**Queensland**、**Brisbane**、**4000**，然后选中“Adam Powell”\*\*\*\* 复选框，再单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d1def-137">Expand **All Customers**, expand **Australia**, expand **Queensland**, expand **Brisbane**, expand **4000**, select the check box for **Adam Powell**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="d1def-138">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 对 Adam Powell 的产品销售总额显示在数据区域中。</span><span class="sxs-lookup"><span data-stu-id="d1def-138">The total sales of products by [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] to Adam Powell are displayed in the data area.</span></span>  
  
7.  <span data-ttu-id="d1def-139">右键单击销售额，指向“其他操作”\*\*\*\*，然后单击“钻取订单详细信息”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d1def-139">Right-click on the sales amount, point to **Additional Actions**, and then click **Drillthrough to Order Details**.</span></span>  
  
     <span data-ttu-id="d1def-140">交付给 Adam Powell 的订单的详细信息将显示在“数据示例查看器”\*\*\*\* 中，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="d1def-140">The details of the orders that were shipped to Adam Powell are displayed in the **Data Sample Viewer**, as shown in the following image.</span></span> <span data-ttu-id="d1def-141">但是，某些其他详细信息也会是有用的，如订单日期、截止日期和发运日期。</span><span class="sxs-lookup"><span data-stu-id="d1def-141">However, some additional details would also be useful, such as the order date, due date, and ship date.</span></span> <span data-ttu-id="d1def-142">在下一个过程中，您将添加这些其他详细信息。</span><span class="sxs-lookup"><span data-stu-id="d1def-142">In the next procedure, you will add these additional details.</span></span>  
  
     <span data-ttu-id="d1def-143">![发送给 Adam Powell 的订单](../../2014/tutorials/media/l8-action6.gif "发送给 Adam Powell 的订单")</span><span class="sxs-lookup"><span data-stu-id="d1def-143">![Orders shipped to Adam Powell](../../2014/tutorials/media/l8-action6.gif "Orders shipped to Adam Powell")</span></span>  
  
8.  <span data-ttu-id="d1def-144">关闭 Excel/</span><span class="sxs-lookup"><span data-stu-id="d1def-144">Close Excel/</span></span>  
  
## <a name="modifying-the-drillthrough-action"></a><span data-ttu-id="d1def-145">修改钻取操作</span><span class="sxs-lookup"><span data-stu-id="d1def-145">Modifying the Drillthrough Action</span></span>  
  
1.  <span data-ttu-id="d1def-146">打开“Internet 销售订单详细信息”\*\*\*\* 维度的维度设计器。</span><span class="sxs-lookup"><span data-stu-id="d1def-146">Open Dimension Designer for the **Internet Sales Order Details** dimension.</span></span>  
  
     <span data-ttu-id="d1def-147">注意，仅为此维度定义了三个属性。</span><span class="sxs-lookup"><span data-stu-id="d1def-147">Notice that only three attributes have been defined for this dimension.</span></span>  
  
2.  <span data-ttu-id="d1def-148">在“数据源视图”\*\*\*\* 窗格中，右键单击空白的区域，再单击“显示所有表”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d1def-148">In the **Data Source View** pane, right-click an open area, and then click **Show All Tables**.</span></span>  
  
3.  <span data-ttu-id="d1def-149">在“格式”\*\*\*\* 菜单上，指向“自动版式”\*\*\*\*，然后单击“关系图”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d1def-149">On the **Format** menu, point to **Autolayout** and then click **Diagram**.</span></span>  
  
4.  <span data-ttu-id="d1def-150">通过右键单击“数据源视图”\*\*\*\* 窗格中的空白区域来查找 **InternetSales (dbo.FactInternetSales)** 表。</span><span class="sxs-lookup"><span data-stu-id="d1def-150">Locate the **InternetSales (dbo.FactInternetSales)** table by right-clicking in an open area of the **Data Source View** pane.</span></span> <span data-ttu-id="d1def-151">然后单击“查找表”\*\*\*\*，并单击“InternetSales”\*\*\*\*，再单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d1def-151">Then click **Find Table,** click **InternetSales,** and click **OK**.</span></span>  
  
5.  <span data-ttu-id="d1def-152">基于以下列创建新属性：</span><span class="sxs-lookup"><span data-stu-id="d1def-152">Create new attributes based on the following columns:</span></span>  
  
    -   <span data-ttu-id="d1def-153">OrderDateKey</span><span class="sxs-lookup"><span data-stu-id="d1def-153">OrderDateKey</span></span>  
  
    -   <span data-ttu-id="d1def-154">DueDateKey</span><span class="sxs-lookup"><span data-stu-id="d1def-154">DueDateKey</span></span>  
  
    -   <span data-ttu-id="d1def-155">ShipDateKey</span><span class="sxs-lookup"><span data-stu-id="d1def-155">ShipDateKey</span></span>  
  
6.  <span data-ttu-id="d1def-156">将 "**订单日期键**" 特性的 "**名称**" 属性更改为 `Order Date` ，然后单击 "**名称列**" 属性的 "浏览" 按钮，然后在 "**名称列**" 对话框中，选择 "**日期**" 作为源表，并选择 SimpleDate 作为源列。</span><span class="sxs-lookup"><span data-stu-id="d1def-156">Change the **Name** property for the **Order Date Key** attribute to `Order Date` Then, click the browse button for the **Name Column** property, and in the **Name Column** dialog box, select **Date** as the source table and select SimpleDate as the source column.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="d1def-157">将 "**截止日期键**" 特性的 "**名称**" 属性更改为 `Due Date` ，然后通过使用与 "**订单日期键**" 特性相同的方法，将此特性的 "**名称列**" 属性更改为 " \*\*SimpleDate (WChar) \*\*。</span><span class="sxs-lookup"><span data-stu-id="d1def-157">Change the **Name** property for the **Due Date Key** attribute to `Due Date`, and then, by using the same method as the **Order Date Key** attribute, change the **Name Column** property for this attribute to **Date.SimpleDate (WChar)**.</span></span>  
  
8.  <span data-ttu-id="d1def-158">将 "**发货日期键**" 特性的 "**名称**" 属性更改为 `Ship Date` ，然后将此属性的 "**名称列**" 属性更改为 " \*\*SimpleDate (WChar) \*\*。</span><span class="sxs-lookup"><span data-stu-id="d1def-158">Change the **Name** property for the **Ship Date Key** attribute to `Ship Date`, and then change the **Name Column** property for this attribute to **Date.SimpleDate (WChar)**.</span></span>  
  
9. <span data-ttu-id="d1def-159">切换到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集的多维数据集设计器的“操作”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="d1def-159">Switch to the **Actions** tab of Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>  
  
10. <span data-ttu-id="d1def-160">在“钻取列”\*\*\*\* 框中，选择各复选框以将以下列添加到“返回列”\*\*\*\* 列表，再单击“确定”\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="d1def-160">In the **Drillthrough Columns** box, select the check boxes to add the following columns to the **Return Columns** list, and then click **OK**:</span></span>  
  
    -   <span data-ttu-id="d1def-161">Order Date</span><span class="sxs-lookup"><span data-stu-id="d1def-161">Order Date</span></span>  
  
    -   <span data-ttu-id="d1def-162">Due Date</span><span class="sxs-lookup"><span data-stu-id="d1def-162">Due Date</span></span>  
  
    -   <span data-ttu-id="d1def-163">Ship Date</span><span class="sxs-lookup"><span data-stu-id="d1def-163">Ship Date</span></span>  
  
     <span data-ttu-id="d1def-164">下图显示了这些所选列。</span><span class="sxs-lookup"><span data-stu-id="d1def-164">The following image shows these columns selected.</span></span>  
  
     <span data-ttu-id="d1def-165">![“钻取列”框](../../2014/tutorials/media/l8-action7.gif "“钻取列”框")</span><span class="sxs-lookup"><span data-stu-id="d1def-165">![Drillthrough Columns box](../../2014/tutorials/media/l8-action7.gif "Drillthrough Columns box")</span></span>  
  
## <a name="reviewing-the-modified-drillthrough-action"></a><span data-ttu-id="d1def-166">检查修改后的钻取操作</span><span class="sxs-lookup"><span data-stu-id="d1def-166">Reviewing the Modified Drillthrough Action</span></span>  
  
1.  <span data-ttu-id="d1def-167">在“生成”\*\*\*\* 菜单上，单击“部署 Analysis Services 教程”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d1def-167">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="d1def-168">在成功完成部署后，切换到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集的多维数据集设计器中的“浏览器”\*\*\*\* 选项卡，然后单击“重新连接”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="d1def-168">When deployment has successfully completed, switch to the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Reconnect** button.</span></span>  
  
3.  <span data-ttu-id="d1def-169">启动 Excel。</span><span class="sxs-lookup"><span data-stu-id="d1def-169">Start Excel.</span></span>  
  
4.  <span data-ttu-id="d1def-170">通过在“值”区域中使用“Internet 销售-销售额”\*\*\*\* 以及在报表筛选器中使用“客户所在地域”\*\*\*\*，重新创建数据透视表。</span><span class="sxs-lookup"><span data-stu-id="d1def-170">Recreate the PivotTable using **Internet Sales-Sales Amount** in the Values area and **Customer Geography** in the Report Filter.</span></span>  
  
     <span data-ttu-id="d1def-171">添加一个从“所有客户”\*\*\*\*、**Australia**、**Queensland**、**Brisbane**、**4000**、**Adam Powell** 进行选择的筛选器。</span><span class="sxs-lookup"><span data-stu-id="d1def-171">Add a filter that selects from **All Customers**, **Australia**, **Queensland**, **Brisbane**, **4000**, **Adam Powell**.</span></span>  
  
5.  <span data-ttu-id="d1def-172">单击“Internet 销售-销售额”\*\*\*\* 数据单元，指向“其他操作”\*\*\*\*，然后单击“钻取订单详细信息”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d1def-172">Click the **Internet Sales-Sales Amount** data cell, point to **Additional Actions**, and then click **Drillthrough to Order Details**.</span></span>  
  
     <span data-ttu-id="d1def-173">在临时电子表格中将显示交付给 Adam Powell 的这些订单的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d1def-173">The details of these orders shipped to Adam Powell are displayed in a temporary worksheet.</span></span> <span data-ttu-id="d1def-174">这包括项说明、订单号、订单日期、截止日期和发运日期信息，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="d1def-174">This includes item description, order number, order date, due date, and ship date information, as shown in the following image.</span></span>  
  
     <span data-ttu-id="d1def-175">![发送给 Adam Powell 的订单](../../2014/tutorials/media/l8-action8.gif "发送给 Adam Powell 的订单")</span><span class="sxs-lookup"><span data-stu-id="d1def-175">![Orders shipped to Adam Powell](../../2014/tutorials/media/l8-action8.gif "Orders shipped to Adam Powell")</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="d1def-176">下一课</span><span class="sxs-lookup"><span data-stu-id="d1def-176">Next Lesson</span></span>  
 [<span data-ttu-id="d1def-177">第 9 课：定义透视和翻译</span><span class="sxs-lookup"><span data-stu-id="d1def-177">Lesson 9: Defining Perspectives and Translations</span></span>](lesson-9-defining-perspectives-and-translations.md)  
  
## <a name="see-also"></a><span data-ttu-id="d1def-178">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d1def-178">See Also</span></span>  
 <span data-ttu-id="d1def-179">[Analysis Services 多维数据 &#40;操作&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="d1def-179">[Actions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="d1def-180">[多维模型中的操作](multidimensional-models/actions-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="d1def-180">[Actions in Multidimensional Models](multidimensional-models/actions-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="d1def-181">[维度关系](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span><span class="sxs-lookup"><span data-stu-id="d1def-181">[Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span></span>  
 <span data-ttu-id="d1def-182">[定义事实关系](lesson-5-2-defining-a-fact-relationship.md) </span><span class="sxs-lookup"><span data-stu-id="d1def-182">[Defining a Fact Relationship](lesson-5-2-defining-a-fact-relationship.md) </span></span>  
 [<span data-ttu-id="d1def-183">定义事实关系和事实关系属性</span><span class="sxs-lookup"><span data-stu-id="d1def-183">Define a Fact Relationship and Fact Relationship Properties</span></span>](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md)  
  
  
