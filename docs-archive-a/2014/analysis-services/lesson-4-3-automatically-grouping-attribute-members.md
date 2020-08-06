---
title: 自动将属性成员分组 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9fb2cda3-a122-4a4c-82e0-3454865eef04
author: minewiskan
ms.author: owend
ms.openlocfilehash: 820231263362a92584a15556e999d69f286349b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694164"
---
# <a name="automatically-grouping-attribute-members"></a><span data-ttu-id="a1561-102">自动将属性成员分组</span><span class="sxs-lookup"><span data-stu-id="a1561-102">Automatically Grouping Attribute Members</span></span>
  <span data-ttu-id="a1561-103">在浏览多维数据集时，通常根据一个属性层次结构的成员来确定另一个属性层次结构的成员的维度。</span><span class="sxs-lookup"><span data-stu-id="a1561-103">When you browse a cube, you typically dimension the members of one attribute hierarchy by the members of another attribute hierarchy.</span></span> <span data-ttu-id="a1561-104">例如，可以按城市、购买的产品或性别将客户销售分组。</span><span class="sxs-lookup"><span data-stu-id="a1561-104">For example, you might group customer sales by city, by product purchased, or by gender.</span></span> <span data-ttu-id="a1561-105">但是，对于某些类型的属性， [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 根据属性层次结构中的成员分布自动创建属性成员的分组非常有用。</span><span class="sxs-lookup"><span data-stu-id="a1561-105">However, with certain types of attributes, it is useful to have [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] automatically create groupings of attribute members based on the distribution of the members within an attribute hierarchy.</span></span> <span data-ttu-id="a1561-106">例如，可以让 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 创建客户的年收入值组。</span><span class="sxs-lookup"><span data-stu-id="a1561-106">For example, you can have [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] create groups of yearly income values for customers.</span></span> <span data-ttu-id="a1561-107">进行此操作时，浏览属性层次结构的用户将看到组的名称和值，而不是成员本身。</span><span class="sxs-lookup"><span data-stu-id="a1561-107">When you do this, users who browse the attribute hierarchy will see the names and values of the groups instead of the members themselves.</span></span> <span data-ttu-id="a1561-108">这就限制了向用户显示的级别的数量，从而更有助于进行分析。</span><span class="sxs-lookup"><span data-stu-id="a1561-108">This limits the number of levels that are presented to users, which can be more useful for analysis.</span></span>

 <span data-ttu-id="a1561-109">**DiscretizationMethod** 属性可以确定 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 是否创建分组，并可确定要执行的分组类型。</span><span class="sxs-lookup"><span data-stu-id="a1561-109">The **DiscretizationMethod** property determines whether [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] creates groupings, and determines the type of grouping that is performed.</span></span> <span data-ttu-id="a1561-110">默认情况下， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 不执行任何分组。</span><span class="sxs-lookup"><span data-stu-id="a1561-110">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] does not perform any groupings.</span></span> <span data-ttu-id="a1561-111">如果启用了自动分组，则可以让 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 根据属性的结构自动确定最佳分组方法，也可以选择下面列表中的一个分组算法来指定分组方法：</span><span class="sxs-lookup"><span data-stu-id="a1561-111">When you enable automatic groupings, you can allow [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to automatically determine the best grouping method based on the structure of the attribute, or you can choose one of the grouping algorithms in the following list to specify the grouping method:</span></span>

 <span data-ttu-id="a1561-112">**EqualAreas** [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]创建组范围，以便在各个组之间平均分配维度成员的总体人口数。</span><span class="sxs-lookup"><span data-stu-id="a1561-112">**EqualAreas** [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] creates group ranges so that the total population of dimension members is distributed equally across the groups.</span></span>

 <span data-ttu-id="a1561-113">**群集** [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]通过对输入值执行一维聚类分析，通过将 K 平均值聚类分析方法与高斯分布结合使用来创建组。</span><span class="sxs-lookup"><span data-stu-id="a1561-113">**Clusters** [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] creates groups by performing single-dimensional clustering on the input values by using the K-Means clustering method with Gaussian distributions.</span></span> <span data-ttu-id="a1561-114">此选项只对数值列有效。</span><span class="sxs-lookup"><span data-stu-id="a1561-114">This option is valid only for numeric columns.</span></span>

 <span data-ttu-id="a1561-115">指定了一种分组方法后，必须使用 **DiscretizationBucketCount** 属性指定分组的数量。</span><span class="sxs-lookup"><span data-stu-id="a1561-115">After you specify a grouping method, you must specify the number of groups, by using the **DiscretizationBucketCount** property.</span></span> <span data-ttu-id="a1561-116">有关详细信息，请参阅[组属性成员 &#40;离散化&#41;](multidimensional-models/attribute-properties-group-attribute-members.md)</span><span class="sxs-lookup"><span data-stu-id="a1561-116">For more information, see [Group Attribute Members &#40;Discretization&#41;](multidimensional-models/attribute-properties-group-attribute-members.md)</span></span>

 <span data-ttu-id="a1561-117">在本主题的任务中，将对以下对象启用不同类型的分组： **客户** 维度中的年度收入值； **雇员** 维度中的雇员病假时数； **雇员** 维度中的雇员休假时数。</span><span class="sxs-lookup"><span data-stu-id="a1561-117">In the tasks in this topic, you will enable different types of groupings for the following: the yearly income values in the **Customer** dimension; the number of employee sick leave hours in the **Employees** dimension; and the number of employee vacation hours in the **Employees** dimension.</span></span> <span data-ttu-id="a1561-118">然后，处理并浏览 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 多维数据集，以此查看各成员组的情况。</span><span class="sxs-lookup"><span data-stu-id="a1561-118">You will then process and browse the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube to view the effect of the member groups.</span></span> <span data-ttu-id="a1561-119">最后，修改成员组的参数，查看组类型更改的效果。</span><span class="sxs-lookup"><span data-stu-id="a1561-119">Finally, you will modify the member group properties to see the effect of the change in grouping type.</span></span>

## <a name="grouping-attribute-hierarchy-members-in-the-customer-dimension"></a><span data-ttu-id="a1561-120">为“客户”维度中的属性层次结构成员分组</span><span class="sxs-lookup"><span data-stu-id="a1561-120">Grouping Attribute Hierarchy Members in the Customer Dimension</span></span>

1.  <span data-ttu-id="a1561-121">在解决方案资源管理器中，双击“维度”文件夹中的“客户”，打开“客户”维度的维度设计器。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a1561-121">In Solution Explorer, double-click **Customer** in the **Dimensions** folder to open Dimension Designer for the Customer dimension.</span></span>

2.  <span data-ttu-id="a1561-122">在“数据源视图”窗格中，右键单击 Customer 表，再单击“浏览数据”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a1561-122">In the **Data Source View** pane, right-click the **Customer** table, and then click **Explore Data**.</span></span>

     <span data-ttu-id="a1561-123">注意， **YearlyIncome** 列的值的范围。</span><span class="sxs-lookup"><span data-stu-id="a1561-123">Notice the range of values for the **YearlyIncome** column.</span></span> <span data-ttu-id="a1561-124">如果未启用成员分组，这些值将成为 **年收入** 属性层次结构的成员。</span><span class="sxs-lookup"><span data-stu-id="a1561-124">These values become the members of the **Yearly Income** attribute hierarchy, unless you enable member grouping.</span></span>

3.  <span data-ttu-id="a1561-125">关闭“浏览 Customer 表”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="a1561-125">Close the **Explore Customer Table** tab.</span></span>

4.  <span data-ttu-id="a1561-126">在“属性”\*\*\*\* 窗格中，选择“年收入”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a1561-126">In the **Attributes** pane, select **Yearly Income**.</span></span>

5.  <span data-ttu-id="a1561-127">在属性窗口中，将**DiscretizationMethod**属性的值更改为 "**自动**"，并将 " **DiscretizationBucketCount** " 属性的值更改为 `5` 。</span><span class="sxs-lookup"><span data-stu-id="a1561-127">In the Properties window, change the value for the **DiscretizationMethod** property to **Automatic** and change the value for the **DiscretizationBucketCount** property to `5`.</span></span>

     <span data-ttu-id="a1561-128">下图显示了修改后的“年收入”\*\*\*\* 属性。</span><span class="sxs-lookup"><span data-stu-id="a1561-128">The following image shows the modified properties for **Yearly Income**.</span></span>

     <span data-ttu-id="a1561-129">![修改后的“年收入”属性](../../2014/tutorials/media/l4-discretizationmethod-1.gif "修改后的“年收入”属性")</span><span class="sxs-lookup"><span data-stu-id="a1561-129">![Modified properties for Yearly Income](../../2014/tutorials/media/l4-discretizationmethod-1.gif "Modified properties for Yearly Income")</span></span>

## <a name="grouping-attribute-hierarchy-members-in-the-employee-dimension"></a><span data-ttu-id="a1561-130">为“雇员”维度中的属性层次结构成员分组</span><span class="sxs-lookup"><span data-stu-id="a1561-130">Grouping Attribute Hierarchy Members in the Employee Dimension</span></span>

1.  <span data-ttu-id="a1561-131">切换到“雇员”维度的维度设计器。</span><span class="sxs-lookup"><span data-stu-id="a1561-131">Switch to Dimension Designer for the Employee dimension.</span></span>

2.  <span data-ttu-id="a1561-132">在“数据源视图”\*\*\*\* 窗格中，右键单击 **Employee** 表，再单击“浏览数据”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a1561-132">In the **Data Source View** pane, right-click the **Employee** table, and then click **Explore Data**.</span></span>

     <span data-ttu-id="a1561-133">注意 **SickLeaveHours** 列和 **VacationHours** 列的值。</span><span class="sxs-lookup"><span data-stu-id="a1561-133">Notice the values for the **SickLeaveHours** column and the **VacationHours** column.</span></span>

3.  <span data-ttu-id="a1561-134">关闭“浏览 Employee 表”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="a1561-134">Close the **Explore Employee Table** tab.</span></span>

4.  <span data-ttu-id="a1561-135">在“属性”\*\*\*\* 窗格中，选择“病假时间”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a1561-135">In the **Attributes** pane, select **Sick Leave Hours**.</span></span>

5.  <span data-ttu-id="a1561-136">在属性窗口中，将**DiscretizationMethod**属性的值更改为 "**分类**"，并将 " **DiscretizationBucketCount** " 属性的值更改为 "" `5` 。</span><span class="sxs-lookup"><span data-stu-id="a1561-136">In the Properties window, change the value for the **DiscretizationMethod** property to **Clusters** and change the value for the **DiscretizationBucketCount** property to `5`.</span></span>

6.  <span data-ttu-id="a1561-137">在“属性”窗格中，选择“休假时间”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a1561-137">In the **Attributes** pane, select **Vacation Hours**.</span></span>

7.  <span data-ttu-id="a1561-138">在属性窗口中，将**DiscretizationMethod**属性的值更改为**相等的区域**，并将**DiscretizationBucketCount**属性的值更改为 `5` 。</span><span class="sxs-lookup"><span data-stu-id="a1561-138">In the Properties window, change the value for the **DiscretizationMethod** property to **Equal Areas** and change the value for the **DiscretizationBucketCount** property to `5`.</span></span>

## <a name="browsing-the-modified-attribute-hierarchies"></a><span data-ttu-id="a1561-139">浏览已修改的属性层次结构</span><span class="sxs-lookup"><span data-stu-id="a1561-139">Browsing the Modified Attribute Hierarchies</span></span>

1.  <span data-ttu-id="a1561-140">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的“生成”菜单上，单击“部署 Analysis Services 教程”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a1561-140">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>

2.  <span data-ttu-id="a1561-141">成功完成部署后，切换到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集的多维数据集设计器，然后单击“浏览”\*\*\*\* 选项卡上的“重新连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a1561-141">When deployment has successfully completed, switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click **Reconnect** on the **Browser** tab.</span></span>

3.  <span data-ttu-id="a1561-142">单击 Excel 图标，然后单击“启用”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a1561-142">Click the Excel icon, and then click **Enable**.</span></span>

4.  <span data-ttu-id="a1561-143">将“Internet 销售-销售额”\*\*\*\* 度量值拖到数据透视表字段列表的“值”区域。</span><span class="sxs-lookup"><span data-stu-id="a1561-143">Drag the **Internet Sales-Sales Amount** measure to the Values area of the PivotTable Field List.</span></span>

5.  <span data-ttu-id="a1561-144">在字段列表中，展开“产品”\*\*\*\* 维度，再将“产品型号系列”\*\*\*\* 用户层次结构拖到字段列表的“行标签”\*\*\*\* 区域。</span><span class="sxs-lookup"><span data-stu-id="a1561-144">In the field list, expand the **Product** dimension, and then drag the **Product Model Lines** user hierarchy to the **Row Labels** area of the field list.</span></span>

6.  <span data-ttu-id="a1561-145">展开字段列表的“客户”\*\*\*\* 维度，再展开“人口统计”\*\*\*\* 显示文件夹，然后将“年收入”\*\*\*\* 属性层次结构拖到“列标签”\*\*\*\* 区域。</span><span class="sxs-lookup"><span data-stu-id="a1561-145">Expand the **Customer** dimension in the field list, expand the **Demographic** display folder, and then drag the **Yearly Income** attribute hierarchy to the **Column Labels** area.</span></span>

     <span data-ttu-id="a1561-146">“年收入”\*\*\*\* 属性层次结构的成员现在已分为六个存储桶，其中包括一个用于年收入未知的客户的销量的存储桶。</span><span class="sxs-lookup"><span data-stu-id="a1561-146">The members of the **Yearly Income** attribute hierarchy are now grouped into six buckets, including a bucket for sales to customers whose yearly income is unknown.</span></span> <span data-ttu-id="a1561-147">并非所有的存储桶都会显示出来。</span><span class="sxs-lookup"><span data-stu-id="a1561-147">Not all buckets are displayed.</span></span>

7.  <span data-ttu-id="a1561-148">从列区域删除“年收入”\*\*\*\* 属性层次结构，从“值”\*\*\*\* 区域中删除“Internet 销售-销售额”\*\*\*\* 度量值。</span><span class="sxs-lookup"><span data-stu-id="a1561-148">Remove the **Yearly Income** attribute hierarchy from the columns area and remove the **Internet Sales-Sales Amount** measure from the **Values** area.</span></span>

8.  <span data-ttu-id="a1561-149">将“分销商销售-销售额”\*\*\*\* 度量值添加到数据区域。</span><span class="sxs-lookup"><span data-stu-id="a1561-149">Add the **Reseller Sales-Sales Amount** measure to the data area.</span></span>

9. <span data-ttu-id="a1561-150">在字段列表中，展开“雇员”\*\*\*\* 维度，展开“组织”\*\*\*\*，然后将“病假时间”\*\*\*\* 拖到“列标签”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a1561-150">In the field list, expand the **Employee** dimension, expand **Organization**, then drag **Sick Leave Hours** to **Column Labels**.</span></span>

     <span data-ttu-id="a1561-151">注意，所有销售是由两个组中的其中一个组的雇员完成的。</span><span class="sxs-lookup"><span data-stu-id="a1561-151">Notice that all sales are made by employees within one of two groups.</span></span> <span data-ttu-id="a1561-152">另注意，病假时数为 32 - 42 小时的雇员完成的销售比病假时间为 20 - 31 小时的雇员完成的销售多得多。</span><span class="sxs-lookup"><span data-stu-id="a1561-152">Notice also that the employees with 32 - 42 sick leave hours made significantly more sales than employees with 20 - 31 sick leave hours.</span></span>

     <span data-ttu-id="a1561-153">下图显示了按雇员病假时数确定维度的销售。</span><span class="sxs-lookup"><span data-stu-id="a1561-153">The following image shows sales dimensioned by employee sick leave hours.</span></span>

     <span data-ttu-id="a1561-154">![按雇员病假时间划分维度的“销售额”](../../2014/tutorials/media/l4-discretizationmethod-2.gif "按雇员病假时间划分维度的“销售额”")</span><span class="sxs-lookup"><span data-stu-id="a1561-154">![Sales dimensioned by employee sick leave hours](../../2014/tutorials/media/l4-discretizationmethod-2.gif "Sales dimensioned by employee sick leave hours")</span></span>

10. <span data-ttu-id="a1561-155">从“数据”\*\*\*\* 窗格的列区域删除“病假时间”\*\*\*\* 属性层次结构。</span><span class="sxs-lookup"><span data-stu-id="a1561-155">Remove the **Sick Leave Hours** attribute hierarchy from the column area of the **Data** pane.</span></span>

11. <span data-ttu-id="a1561-156">将“休假时间”\*\*\*\* 添加到“数据”\*\*\*\* 窗格的列区域。</span><span class="sxs-lookup"><span data-stu-id="a1561-156">Add **Vacation Hours** to the column area of the **Data** pane.</span></span>

     <span data-ttu-id="a1561-157">注意，根据等区域分组方法，显示了两个组。</span><span class="sxs-lookup"><span data-stu-id="a1561-157">Notice that two groups appear, based on the equal areas grouping method.</span></span> <span data-ttu-id="a1561-158">其他三个组因不包含数据值而被隐藏。</span><span class="sxs-lookup"><span data-stu-id="a1561-158">Three other groups are hidden because they contain no data values.</span></span>

## <a name="modifying-grouping-properties-and-reviewing-the-effect-of-the-changes"></a><span data-ttu-id="a1561-159">修改分组属性并检查更改的效果</span><span class="sxs-lookup"><span data-stu-id="a1561-159">Modifying Grouping Properties and Reviewing the Effect of the Changes</span></span>

1.  <span data-ttu-id="a1561-160">切换到“雇员”\*\*\*\* 维度的维度设计器，然后在“属性”\*\*\*\* 窗格中选择“休假时间”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a1561-160">Switch to Dimension Designer for the **Employee** dimension, and then select **Vacation Hours** in the **Attributes** pane.</span></span>

2.  <span data-ttu-id="a1561-161">在“属性”窗口中，将 **DiscretizationBucketCount** 属性值更改为 **10**。</span><span class="sxs-lookup"><span data-stu-id="a1561-161">In the Properties window, change the value of the **DiscretizationBucketCount** property to **10.**</span></span>

3.  <span data-ttu-id="a1561-162">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 的“生成”菜单上，单击“部署 Analysis Services 教程”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a1561-162">On the **Build** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>

4.  <span data-ttu-id="a1561-163">成功完成部署后，切换回 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 多维数据集的多维数据集设计器。</span><span class="sxs-lookup"><span data-stu-id="a1561-163">When deployment has successfully completed, switch back to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>

5.  <span data-ttu-id="a1561-164">在“浏览器”\*\*\*\* 选项卡上单击“重新连接”\*\*\*\*，单击 Excel 图标，然后重新构建数据透视表，以便可以查看对分组方法的更改的效果：</span><span class="sxs-lookup"><span data-stu-id="a1561-164">Click **Reconnect** on the **Browser** tab, click the Excel icon, and then reconstruct the PivotTable so that you can view the effect of the change to the grouping method:</span></span>

    1.  <span data-ttu-id="a1561-165">将“分销商销售-销售额”拖到值</span><span class="sxs-lookup"><span data-stu-id="a1561-165">Drag Reseller Sales-Sales Amount to Values</span></span>

    2.  <span data-ttu-id="a1561-166">将休假时间（在“雇员组织”文件夹中）拖到列</span><span class="sxs-lookup"><span data-stu-id="a1561-166">Drag Vacation Hours (in the Employees Organization folder) to Columns</span></span>

    3.  <span data-ttu-id="a1561-167">将产品型号系列拖到行</span><span class="sxs-lookup"><span data-stu-id="a1561-167">Drag Product Model Lines to Rows</span></span>

     <span data-ttu-id="a1561-168">请注意，现在有三组具有“休假时间”\*\*\*\* 属性的成员，这些成员都有产品销售值。</span><span class="sxs-lookup"><span data-stu-id="a1561-168">Notice that there are now three groups of members of the **Vacation Hours** attribute that have sales values for products.</span></span> <span data-ttu-id="a1561-169">（其他七个组包含没有销售数据的成员。）</span><span class="sxs-lookup"><span data-stu-id="a1561-169">(The other seven groups contain members with no sales data.)</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="a1561-170">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="a1561-170">Next Task in Lesson</span></span>
 [<span data-ttu-id="a1561-171">隐藏和禁用属性层次结构</span><span class="sxs-lookup"><span data-stu-id="a1561-171">Hiding and Disabling Attribute Hierarchies</span></span>](lesson-4-4-hiding-and-disabling-attribute-hierarchies.md)

## <a name="see-also"></a><span data-ttu-id="a1561-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a1561-172">See Also</span></span>
 [<span data-ttu-id="a1561-173">对属性成员进行分组（离散化）</span><span class="sxs-lookup"><span data-stu-id="a1561-173">Group Attribute Members &#40;Discretization&#41;</span></span>](multidimensional-models/attribute-properties-group-attribute-members.md)


