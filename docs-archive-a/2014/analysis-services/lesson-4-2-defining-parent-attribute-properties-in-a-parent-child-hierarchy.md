---
title: 在父子层次结构中定义父特性属性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2d78fa73-a13b-4e12-bbd0-43e5307f760c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1dfa4340bdc161809cf3821e5cb1f0609399e1d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588120"
---
# <a name="defining-parent-attribute-properties-in-a-parent-child-hierarchy"></a><span data-ttu-id="a26fc-102">定义父子层次结构中的父特性属性</span><span class="sxs-lookup"><span data-stu-id="a26fc-102">Defining Parent Attribute Properties in a Parent-Child Hierarchy</span></span>
  <span data-ttu-id="a26fc-103">父子层次结构是基于两个表列的维度中的层次结构。</span><span class="sxs-lookup"><span data-stu-id="a26fc-103">A parent-child hierarchy is a hierarchy in a dimension that is based on two table columns.</span></span> <span data-ttu-id="a26fc-104">这两个表列一起定义维度成员之间的层次结构关系。</span><span class="sxs-lookup"><span data-stu-id="a26fc-104">Together, these columns define the hierarchical relationships among the members of the dimension.</span></span> <span data-ttu-id="a26fc-105">第一列称为“成员键列”\*\*，用于标识每个维度成员。</span><span class="sxs-lookup"><span data-stu-id="a26fc-105">The first column, called the *member key column*, identifies each dimension member.</span></span> <span data-ttu-id="a26fc-106">另一列称为“父列”\*\*，用于标识每个维度成员的父项。</span><span class="sxs-lookup"><span data-stu-id="a26fc-106">The other column, called the *parent column*, identifies the parent of each dimension member.</span></span> <span data-ttu-id="a26fc-107">父特性的“NamingTemplate”\*\*\*\* 属性决定父子层次结构中的每个级别的名称，而“MembersWithData”\*\*\*\* 属性则决定是否应显示父成员的数据。</span><span class="sxs-lookup"><span data-stu-id="a26fc-107">The **NamingTemplate** property of a parent attribute determines the name of each level in the parent-child hierarchy, and the **MembersWithData** property determines whether data for parent members should be displayed.</span></span>

 <span data-ttu-id="a26fc-108">有关详细信息，请参阅父子[层次结构](multidimensional-models/parent-child-dimension.md)中的属性和父子层次[结构中的属性](multidimensional-models/parent-child-dimension-attributes.md)</span><span class="sxs-lookup"><span data-stu-id="a26fc-108">For more information, see [Parent-Child Hierarchy](multidimensional-models/parent-child-dimension.md), [Attributes in Parent-Child Hierarchies](multidimensional-models/parent-child-dimension-attributes.md)</span></span>

> [!NOTE]
>  <span data-ttu-id="a26fc-109">使用维度向导创建维度时，向导将识别哪些表具有父子关系，并自动定义父子层次结构。</span><span class="sxs-lookup"><span data-stu-id="a26fc-109">When you use the Dimension Wizard to create a dimension, the wizard recognizes the tables that have parent-child relationships and automatically defines the parent-child hierarchy for you.</span></span>

 <span data-ttu-id="a26fc-110">在本主题的任务中，将创建命名模板，以定义“雇员”\*\*\*\* 维度中父子层次结构内的每个级别的名称。</span><span class="sxs-lookup"><span data-stu-id="a26fc-110">In the tasks in this topic, you will create a naming template that defines the name for each level in the parent-child hierarchy in the **Employee** dimension.</span></span> <span data-ttu-id="a26fc-111">然后，将配置该父属性以隐藏所有父数据，以便只显示叶级成员的销售额。</span><span class="sxs-lookup"><span data-stu-id="a26fc-111">You will then configure the parent attribute to hide all parent data, so that only the sales for leaf-level members are displayed.</span></span>

## <a name="browsing-the-employee-dimension"></a><span data-ttu-id="a26fc-112">浏览“雇员”维度</span><span class="sxs-lookup"><span data-stu-id="a26fc-112">Browsing the Employee Dimension</span></span>

1.  <span data-ttu-id="a26fc-113">在解决方案资源管理器中，双击“维度”\*\*\*\* 文件夹中的“Employee.dim”\*\*\*\* 来打开“雇员”维度的维度设计器。</span><span class="sxs-lookup"><span data-stu-id="a26fc-113">In Solution Explorer, double-click **Employee.dim** in the **Dimensions** folder to open Dimension Designer for the Employee dimension.</span></span>

2.  <span data-ttu-id="a26fc-114">单击“浏览器”\*\*\*\* 选项卡，验证已在“层次结构”\*\*\*\* 列表中选中了“雇员”\*\*\*\*，再展开“所有雇员”\*\*\*\* 成员。</span><span class="sxs-lookup"><span data-stu-id="a26fc-114">Click the **Browser** tab, verify that **Employees** is selected in the **Hierarchy** list, and then expand the **All Employees** member.</span></span>

     <span data-ttu-id="a26fc-115">请注意，“Ken J. Sánchez”\*\*\*\* 是该父子层次结构中最高级别的经理。</span><span class="sxs-lookup"><span data-stu-id="a26fc-115">Notice that **Ken J. Sánchez** is the top-level manager in this parent-child hierarchy.</span></span>

3.  <span data-ttu-id="a26fc-116">选择“Ken J. Sánchez”\*\*\*\* 成员。</span><span class="sxs-lookup"><span data-stu-id="a26fc-116">Select the **Ken J. Sánchez** member.</span></span>

     <span data-ttu-id="a26fc-117">注意该成员的级别名称是“级别 02”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a26fc-117">Notice that the level name for this member is **Level 02**.</span></span> <span data-ttu-id="a26fc-118"> (级别名称将显示在 "**当前级别**" 之后：紧靠在 "**所有雇员**" 成员的上方。 ) 在下一任务中，你将为每个级别定义更多描述性名称。</span><span class="sxs-lookup"><span data-stu-id="a26fc-118">(The level name appears after **Current level:** immediately above the **All Employees** member.) In the next task, you will define more descriptive names for each level.</span></span>

4.  <span data-ttu-id="a26fc-119">展开“Ken J. Sánchez”\*\*\*\*，以查看该经理所管辖的雇员的名称，再选择“Brian S. Welcker”\*\*\*\* 以查看该级别的名称。</span><span class="sxs-lookup"><span data-stu-id="a26fc-119">Expand **Ken J. Sánchez** to view the names of the employees who report to this manager, and then select **Brian S. Welcker** to view the name of this level.</span></span>

     <span data-ttu-id="a26fc-120">注意该成员的级别名称是“级别 03”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a26fc-120">Notice that the level name for this member is **Level 03**.</span></span>

5.  <span data-ttu-id="a26fc-121">在解决方案资源管理器中，双击“多维数据集”\*\*\*\* 文件夹中的 **Analysis Services Tutorial.cube**，以打开 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集的多维数据集设计器。</span><span class="sxs-lookup"><span data-stu-id="a26fc-121">In Solution Explorer, double-click **Analysis Services Tutorial.cube** in the **Cubes** folder to open Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>

6.  <span data-ttu-id="a26fc-122">单击 **“浏览器”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="a26fc-122">Click the **Browser** tab.</span></span>

7.  <span data-ttu-id="a26fc-123">单击 Excel 图标，然后在系统提示启用连接时单击“启用”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a26fc-123">Click the Excel icon, and then click **Enable** when prompted to enable connections.</span></span>

8.  <span data-ttu-id="a26fc-124">在数据透视表字段列表中，展开“分销商销售”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a26fc-124">In the PivotTable Field List, expand **Reseller Sales**.</span></span> <span data-ttu-id="a26fc-125">将“分销商销售-销售额”\*\*\*\* 拖到“值”区域。</span><span class="sxs-lookup"><span data-stu-id="a26fc-125">Drag **Reseller Sales-Sales Amount** to the Values area.</span></span>

9. <span data-ttu-id="a26fc-126">在数据透视表字段列表中，展开“雇员”\*\*\*\*，然后将“雇员”\*\*\*\* 层次结构拖到“行”\*\*\*\* 区域。</span><span class="sxs-lookup"><span data-stu-id="a26fc-126">In the PivotTable Field List, expand **Employee**, and then drag the **Employees** hierarchy to the **Rows** area.</span></span>

     <span data-ttu-id="a26fc-127">“雇员”层次结构的所有成员都将添加到数据透视表的 A 列。</span><span class="sxs-lookup"><span data-stu-id="a26fc-127">All the members of the Employees hierarchy are added to column A of the PivotTable report.</span></span>

     <span data-ttu-id="a26fc-128">下图显示展开的“雇员”层次结构。</span><span class="sxs-lookup"><span data-stu-id="a26fc-128">The following image shows the Employees hierarchy expanded.</span></span>

10. <span data-ttu-id="a26fc-129">![显示“雇员”层次结构的数据透视表](../../2014/tutorials/media/l4-employee-1.gif "显示“雇员”层次结构的数据透视表")</span><span class="sxs-lookup"><span data-stu-id="a26fc-129">![PivotTable showing Employees hierarchy](../../2014/tutorials/media/l4-employee-1.gif "PivotTable showing Employees hierarchy")</span></span>

     <span data-ttu-id="a26fc-130">请注意，级别 03 中每个经理的销售额也会显示在级别 04 中。</span><span class="sxs-lookup"><span data-stu-id="a26fc-130">Notice that the sales made by each manager in Level 03 are also displayed in Level 04.</span></span> <span data-ttu-id="a26fc-131">这是因为每个经理也是其他经理的雇员。</span><span class="sxs-lookup"><span data-stu-id="a26fc-131">This is because each manager is also an employee of another manager.</span></span> <span data-ttu-id="a26fc-132">在下一个任务中，将隐藏这些销售额。</span><span class="sxs-lookup"><span data-stu-id="a26fc-132">In the next task, you will hide these sale amounts.</span></span>

## <a name="modifying-parent-attribute-properties-in-the-employee-dimension"></a><span data-ttu-id="a26fc-133">修改“雇员”维度中的父特性属性</span><span class="sxs-lookup"><span data-stu-id="a26fc-133">Modifying Parent Attribute Properties in the Employee Dimension</span></span>

1.  <span data-ttu-id="a26fc-134">切换到“雇员”\*\*\*\* 维度的维度设计器。</span><span class="sxs-lookup"><span data-stu-id="a26fc-134">Switch to Dimension Designer for the **Employee** dimension.</span></span>

2.  <span data-ttu-id="a26fc-135">单击“维度结构”\*\*\*\* 选项卡，再在“属性”\*\*\*\* 窗格中选择“雇员”\*\*\*\* 属性层次结构。</span><span class="sxs-lookup"><span data-stu-id="a26fc-135">Click the **Dimension Structure** tab, and then select the **Employees** attribute hierarchy in the **Attributes** pane.</span></span>

     <span data-ttu-id="a26fc-136">注意该属性的唯一图标。</span><span class="sxs-lookup"><span data-stu-id="a26fc-136">Notice the unique icon for this attribute.</span></span> <span data-ttu-id="a26fc-137">该图标表示该属性是父子层次结构中的父键。</span><span class="sxs-lookup"><span data-stu-id="a26fc-137">This icon signifies that the attribute is the parent key in a parent-child hierarchy.</span></span> <span data-ttu-id="a26fc-138">还要注意的是，在“属性”窗口中，该特性的“用法”\*\*\*\* 属性被定义为“父级”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a26fc-138">Notice also, in the Properties window, that the **Usage** property for the attribute is defined as **Parent**.</span></span> <span data-ttu-id="a26fc-139">该属性是在设计维度时由维度向导设置的。</span><span class="sxs-lookup"><span data-stu-id="a26fc-139">This property was set by the Dimension Wizard when the dimension was designed.</span></span> <span data-ttu-id="a26fc-140">此向导自动检测到了父子关系。</span><span class="sxs-lookup"><span data-stu-id="a26fc-140">The wizard automatically detected the parent-child relationship.</span></span>

3.  <span data-ttu-id="a26fc-141">在“属性”窗口中，单击“NamingTemplate”\*\*\*\* 属性单元中的省略号按钮 (**...**)。</span><span class="sxs-lookup"><span data-stu-id="a26fc-141">In the Properties window, click the ellipsis button (**...**) in the **NamingTemplate** property cell.</span></span>

     <span data-ttu-id="a26fc-142">在“级别命名模板”\*\*\*\* 对话框中，将定义用于确定父子层次结构中的级别名称的级别命名模板，用户在浏览多维数据集时将显示级别名称。</span><span class="sxs-lookup"><span data-stu-id="a26fc-142">In the **Level Naming Template** dialog box, you define the level naming template that determines the level names in the parent-child hierarchy that are displayed to users as they browse cubes.</span></span>

4.  <span data-ttu-id="a26fc-143">在第二行中，在 " **\*** **名称**" 列中键入**Employee \* Level** ，然后单击第三行。</span><span class="sxs-lookup"><span data-stu-id="a26fc-143">In the second row, the **\*** row, type **Employee Level \*** in the **Name** column, and then click the third row.</span></span>

     <span data-ttu-id="a26fc-144">注意，在“结果”\*\*\*\* 下面，每个级别现在将命名为“雇员级别”，并且后跟按顺序增加的数字。</span><span class="sxs-lookup"><span data-stu-id="a26fc-144">Notice under **Result** that each level will now be named "Employee Level" followed by a sequentially increasing number.</span></span>

     <span data-ttu-id="a26fc-145">下图显示了在“级别命名模板”\*\*\*\* 对话框中的更改。</span><span class="sxs-lookup"><span data-stu-id="a26fc-145">The following image shows the changes in the **Level Naming Template** dialog box.</span></span>

     <span data-ttu-id="a26fc-146">!["级别命名模板" 对话框](../../2014/tutorials/media/l4-namingtemplate.gif "“级别命名模板”对话框")</span><span class="sxs-lookup"><span data-stu-id="a26fc-146">![Level Naming Template dialog box](../../2014/tutorials/media/l4-namingtemplate.gif "Level Naming Template dialog box")</span></span>

5.  <span data-ttu-id="a26fc-147">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="a26fc-147">Click **OK**.</span></span>

6.  <span data-ttu-id="a26fc-148">在“雇员”\*\*\*\* 特性的“属性”窗口中，选择“MembersWithData”\*\*\*\* 属性单元中的“NonLeafDataHidden”\*\*\*\*，以便为“雇员”\*\*\*\* 特性更改此值。</span><span class="sxs-lookup"><span data-stu-id="a26fc-148">In the Properties window for the **Employees** attribute, in the **MembersWithData** property cell, select **NonLeafDataHidden** to change this value for the **Employees** attribute.</span></span>

     <span data-ttu-id="a26fc-149">这将在父子层次结构中隐藏与非叶级成员相关的数据。</span><span class="sxs-lookup"><span data-stu-id="a26fc-149">This will cause data that is related to non-leaf level members in the parent-child hierarchy to be hidden.</span></span>

## <a name="browsing-the-employee-dimension-with-the-modified-attributes"></a><span data-ttu-id="a26fc-150">浏览修改属性后的“雇员”维度</span><span class="sxs-lookup"><span data-stu-id="a26fc-150">Browsing the Employee Dimension with the Modified Attributes</span></span>

1.  <span data-ttu-id="a26fc-151">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的“生成”菜单上，单击“部署 Analysis Services 教程”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a26fc-151">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>

2.  <span data-ttu-id="a26fc-152">成功完成部署后，切换到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集的多维数据集设计器，再单击“浏览器”\*\*\*\* 选项卡的工具栏上的“重新连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a26fc-152">When deployment has successfully completed, switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click **Reconnect** on the toolbar of the **Browser** tab.</span></span>

3.  <span data-ttu-id="a26fc-153">单击 Excel 图标，然后单击“启用”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a26fc-153">Click the Excel icon, and then click **Enable**.</span></span>

4.  <span data-ttu-id="a26fc-154">将“分销商销售-销售额”\*\*\*\* 拖到“值”区域。</span><span class="sxs-lookup"><span data-stu-id="a26fc-154">Drag **Reseller Sales-Sales Amount** to the Values area.</span></span>

5.  <span data-ttu-id="a26fc-155">将“雇员”\*\*\*\* 层次结构拖到“行标签”区域。</span><span class="sxs-lookup"><span data-stu-id="a26fc-155">Drag the **Employees** hierarchy to the Row Labels area.</span></span>

     <span data-ttu-id="a26fc-156">下图显示对“雇员”层次结构所做的更改。</span><span class="sxs-lookup"><span data-stu-id="a26fc-156">The following image shows the changes that you made to the Employees hierarchy.</span></span> <span data-ttu-id="a26fc-157">请注意 Stephen Y. Jiang 不再显示为自己的雇员。</span><span class="sxs-lookup"><span data-stu-id="a26fc-157">Notice that Stephen Y. Jiang no longer appears as an employee of himself.</span></span>

     <span data-ttu-id="a26fc-158">![修改后的“雇员”层次结构](../../2014/tutorials/media/l4-employee-2.png "修改后的“雇员”层次结构")</span><span class="sxs-lookup"><span data-stu-id="a26fc-158">![Modified Employees hierarchy](../../2014/tutorials/media/l4-employee-2.png "Modified Employees hierarchy")</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="a26fc-159">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="a26fc-159">Next Task in Lesson</span></span>
 [<span data-ttu-id="a26fc-160">自动将属性成员分组</span><span class="sxs-lookup"><span data-stu-id="a26fc-160">Automatically Grouping Attribute Members</span></span>](lesson-4-3-automatically-grouping-attribute-members.md)

## <a name="see-also"></a><span data-ttu-id="a26fc-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a26fc-161">See Also</span></span>
 <span data-ttu-id="a26fc-162">父子层次结构中的[父子层次结构](multidimensional-models/parent-child-dimension.md)[属性](multidimensional-models/parent-child-dimension-attributes.md)</span><span class="sxs-lookup"><span data-stu-id="a26fc-162">[Parent-Child Hierarchy](multidimensional-models/parent-child-dimension.md) [Attributes in Parent-Child Hierarchies](multidimensional-models/parent-child-dimension-attributes.md)</span></span>


