---
title: 为项添加展开或折叠操作（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 49f07ad6-242b-4861-8fc1-91ca78c36d6c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 331c6a14a4a898ffcdf86f274c00e7ad3c801ec7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687464"
---
# <a name="add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs"></a><span data-ttu-id="2fae1-102">为项添加展开或折叠操作（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="2fae1-102">Add an Expand or Collapse Action to an Item (Report Builder and SSRS)</span></span>
  <span data-ttu-id="2fae1-103">你可以使用户实现以交互方式展开或折叠报表项，或者展开或折叠与表或矩阵的组关联的行与列。</span><span class="sxs-lookup"><span data-stu-id="2fae1-103">You can enable a user to interactively expand or collapse report items, or expand or collapse rows and columns associated with a group for a table or matrix.</span></span> <span data-ttu-id="2fae1-104">若要让用户能够展开或折叠某个项，请设置该项的可见性属性。</span><span class="sxs-lookup"><span data-stu-id="2fae1-104">To allow users to expand or collapse an item, you set the visibility properties for that item.</span></span> <span data-ttu-id="2fae1-105">设置可见性在 HTML 报表查看器中有效，有时也称为“深化” \*\* 操作。</span><span class="sxs-lookup"><span data-stu-id="2fae1-105">Setting visibility works in an HTML report viewer, and is sometimes called a *drilldown* action.</span></span>  
  
 <span data-ttu-id="2fae1-106">在报表设计视图中，可以指定要显示展开和折叠切换图标的文本框的名称。</span><span class="sxs-lookup"><span data-stu-id="2fae1-106">In report design view, you specify the name of the text box where you want to display the expand and collapse toggle icons.</span></span> <span data-ttu-id="2fae1-107">在呈现的报表中，文本框中除了内容之外，还显示加号 (+) 或减号 (-)。</span><span class="sxs-lookup"><span data-stu-id="2fae1-107">In the rendered report, the text box displays a plus (+) or minus (-) sign in addition to its contents.</span></span> <span data-ttu-id="2fae1-108">用户单击切换时，报表显示内容将相应刷新，以根据报表中各项的当前可见性设置显示或隐藏报表项。</span><span class="sxs-lookup"><span data-stu-id="2fae1-108">When the user clicks the toggle, the report display is refreshed to show or hide the report item, based on the current visibility settings for items in the report.</span></span>  
  
 <span data-ttu-id="2fae1-109">通常，展开和折叠操作的使用方式是最初仅显示摘要数据，让用户能够单击加号以显示详细信息数据。</span><span class="sxs-lookup"><span data-stu-id="2fae1-109">Typically, the expand and collapse action is used to initially display only summary data and to enable the user to click the plus sign to show detail data.</span></span> <span data-ttu-id="2fae1-110">例如，您可以一开始就隐藏显示图表的值的表，或隐藏包含嵌套行组或列组的表的子组，这与在明细报表中相同。</span><span class="sxs-lookup"><span data-stu-id="2fae1-110">For example, you can initially hide a table that displays values for a chart, or hide child groups for a table with nested row or column groups, as in a drilldown report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-expand-and-collapse-action-to-a-group"></a><span data-ttu-id="2fae1-111">为组添加展开和折叠操作</span><span class="sxs-lookup"><span data-stu-id="2fae1-111">To add expand and collapse action to a group</span></span>  
  
1.  <span data-ttu-id="2fae1-112">在报表设计视图中，单击表或矩阵将其选中。</span><span class="sxs-lookup"><span data-stu-id="2fae1-112">In report design view, click the table or matrix to select it.</span></span> <span data-ttu-id="2fae1-113">“分组”窗格随即显示行组和列组。</span><span class="sxs-lookup"><span data-stu-id="2fae1-113">The Grouping pane displays the row and column groups.</span></span>  
  
     <span data-ttu-id="2fae1-114">![“分组”窗格](../media/groupingpane.png "“分组”窗格")</span><span class="sxs-lookup"><span data-stu-id="2fae1-114">![Grouping Pane](../media/groupingpane.png "Grouping Pane")</span></span>  
  
     <span data-ttu-id="2fae1-115">如果未出现“分组”窗格，请单击 **“查看”** 菜单，然后单击 **“分组”**。</span><span class="sxs-lookup"><span data-stu-id="2fae1-115">If the Grouping pane does not appear, click the **View** menu and then click **Grouping**.</span></span>  
  
2.  <span data-ttu-id="2fae1-116">右键单击“分组”窗格标题栏中的任意位置，然后单击“高级”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2fae1-116">Right-click anywhere in the title bar of the Grouping pane, and then click **Advanced**.</span></span> <span data-ttu-id="2fae1-117">此时将切换“分组”窗格模式以便在设计图面上显示行和列的基础显示结构。</span><span class="sxs-lookup"><span data-stu-id="2fae1-117">The Grouping pane mode toggles to show the underlying display structure for rows and columns on the design surface.</span></span>  
  
     <span data-ttu-id="2fae1-118">![具有高级模式菜单的“分组”窗格](../media/groupingpane-advancedmode.png "具有高级模式菜单的“分组”窗格")</span><span class="sxs-lookup"><span data-stu-id="2fae1-118">![Grouping Pane with Advanced Mode menu](../media/groupingpane-advancedmode.png "Grouping Pane with Advanced Mode menu")</span></span>  
  
3.  <span data-ttu-id="2fae1-119">在相应的组窗格中，单击要隐藏其关联行或列的行组或列组的名称。</span><span class="sxs-lookup"><span data-stu-id="2fae1-119">In the appropriate group pane, click the name of the row group or column group for which you want to hide the associated rows or columns.</span></span> <span data-ttu-id="2fae1-120">该组即被选中，并且“属性”窗格会显示 **“Tablix 成员”** 属性。</span><span class="sxs-lookup"><span data-stu-id="2fae1-120">The group is selected and the Properties pane shows the **Tablix Member** properties.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2fae1-121"> 如果未看见“属性”窗格，请单击功能区上的 **“查看”** ，然后单击 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="2fae1-121">If you do not see the Properties pane, click **View** on the Ribbon and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="2fae1-122">在中 `Hidden` ，选择以下选项之一来设置首次运行报表时该报表项的可见性：</span><span class="sxs-lookup"><span data-stu-id="2fae1-122">In `Hidden`, choose one of the following options to set the visibility of this report item the first time you run a report:</span></span>  
  
    -   <span data-ttu-id="2fae1-123">选择 `False` 此选项可以显示报表项。</span><span class="sxs-lookup"><span data-stu-id="2fae1-123">Select `False` to display the report item.</span></span>  
  
    -   <span data-ttu-id="2fae1-124">选择 `True` 此选项可以隐藏报表项。</span><span class="sxs-lookup"><span data-stu-id="2fae1-124">Select `True` to hide the report item.</span></span>  
  
    -   <span data-ttu-id="2fae1-125">选择 **\<Expression>** 此复选框可以打开 "**表达式**" 对话框，以便创建在运行时计算的表达式来确定可见性。</span><span class="sxs-lookup"><span data-stu-id="2fae1-125">Select **\<Expression>** to open the **Expression** dialog box to create an expression that is evaluated at run time to determine the visibility.</span></span>  
  
5.  <span data-ttu-id="2fae1-126">在“切换项”\*\*\*\* 下拉框中，选择要向其添加切换图像的文本框名称。</span><span class="sxs-lookup"><span data-stu-id="2fae1-126">In **ToggleItem**, from the drop-down box, select the name of a text box to which to add the toggle image.</span></span>  
  
     <span data-ttu-id="2fae1-127">在下图中，“颜色”行组配置为可使用户展开和折叠关联行。</span><span class="sxs-lookup"><span data-stu-id="2fae1-127">In the following image, the Color row group is configured enable users to expand and collapse associated rows.</span></span>  
  
     <span data-ttu-id="2fae1-128">![配置需扩展的行组](../media/expandcollapse-confighiddentoggleitemwithnumbers.png "配置需扩展的行组")</span><span class="sxs-lookup"><span data-stu-id="2fae1-128">![Configuring a row group to be expanded](../media/expandcollapse-confighiddentoggleitemwithnumbers.png "Configuring a row group to be expanded")</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2fae1-129">包含切换图像的文本框不能是您要隐藏其关联行或列的行组或列组。</span><span class="sxs-lookup"><span data-stu-id="2fae1-129">The text box with the toggle image cannot be the row or column group for which you want to hide the associated rows or columns.</span></span> <span data-ttu-id="2fae1-130">该文本框必须在要隐藏的项所在的同一组或祖先组中。</span><span class="sxs-lookup"><span data-stu-id="2fae1-130">It must either be in the same group as the item that is being hidden or in an ancestor group.</span></span> <span data-ttu-id="2fae1-131">例如，若要切换与子组关联的行的可见性，请在与父组关联的行中选择一个文本框。</span><span class="sxs-lookup"><span data-stu-id="2fae1-131">For example, to toggle visibility of rows associated with a child group, select a text box in a row associated with the parent group.</span></span>  
  
6.  <span data-ttu-id="2fae1-132">若要测试该切换，请运行报表，然后单击带有切换图像的文本框。</span><span class="sxs-lookup"><span data-stu-id="2fae1-132">To test the toggle, run the report and click the text box with the toggle image.</span></span> <span data-ttu-id="2fae1-133">报表显示内容随即刷新，显示带有切换后的可见性的行组和列组。</span><span class="sxs-lookup"><span data-stu-id="2fae1-133">The report display refreshes to show row groups and column groups with their toggled visibility.</span></span>  
  
     <span data-ttu-id="2fae1-134">![运行具有可扩展行组的报表](../media/expandcollapse-runreport-rowgroup.png "运行具有可扩展行组的报表")</span><span class="sxs-lookup"><span data-stu-id="2fae1-134">![Running report with expandable row group](../media/expandcollapse-runreport-rowgroup.png "Running report with expandable row group")</span></span>  
  
### <a name="to-add-expand-and-collapse-action-to-a-report-item"></a><span data-ttu-id="2fae1-135">为报表项添加展开和折叠操作</span><span class="sxs-lookup"><span data-stu-id="2fae1-135">To add expand and collapse action to a report item</span></span>  
  
1.  <span data-ttu-id="2fae1-136">在报表设计视图中，右键单击要显示或隐藏的报表项，然后单击 " *\<report item>* **属性**"。</span><span class="sxs-lookup"><span data-stu-id="2fae1-136">In report design view, right-click the report item to show or hide, and then click *\<report item>* **Properties**.</span></span> <span data-ttu-id="2fae1-137">该 *\<report item>* 报表项的 "**属性**" 对话框将打开。</span><span class="sxs-lookup"><span data-stu-id="2fae1-137">The *\<report item>* **Properties** dialog box for the report item opens.</span></span>  
  
2.  <span data-ttu-id="2fae1-138">单击 **“可见性”** 。</span><span class="sxs-lookup"><span data-stu-id="2fae1-138">Click **Visibility**.</span></span>  
  
3.  <span data-ttu-id="2fae1-139">在 **“在报表最初运行时”** 中，选择以下选项之一来设置首次运行报表时该报表项的可见性：</span><span class="sxs-lookup"><span data-stu-id="2fae1-139">In **When the report is initially run**, choose one of the following options to set the visibility of this report item the first time you run a report:</span></span>  
  
    -   <span data-ttu-id="2fae1-140">选择 **“显示”** 可以显示报表项。</span><span class="sxs-lookup"><span data-stu-id="2fae1-140">Select **Show** to display the report item.</span></span>  
  
    -   <span data-ttu-id="2fae1-141">选择 **“隐藏”** 可以隐藏报表项。</span><span class="sxs-lookup"><span data-stu-id="2fae1-141">Select **Hide** to hide the report item.</span></span>  
  
    -   <span data-ttu-id="2fae1-142">选择 **“基于表达式显示或隐藏”** 可以使用在运行时计算的表达式来确定可见性。</span><span class="sxs-lookup"><span data-stu-id="2fae1-142">Select **Show or hide based on an expression** to use an expression evaluated at run time to determine the visibility.</span></span> <span data-ttu-id="2fae1-143">单击 (fx) 打开“表达式”对话框以创建表达式\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2fae1-143">Click (**fx**) to open the **Expression** dialog box to create an expression.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="2fae1-144">当指定可见性的表达式时，需要设置报表项的 Hidden 属性。</span><span class="sxs-lookup"><span data-stu-id="2fae1-144">When you specify an expression for visibility, you are setting the Hidden property of the report item.</span></span> <span data-ttu-id="2fae1-145">表达式计算结果为 `Boolean` 值，值为 `True` 时表示隐藏该项，值为 `False` 时表示显示该项。</span><span class="sxs-lookup"><span data-stu-id="2fae1-145">The expression evaluates to a `Boolean` value of `True` to hide the item and `False` to show the item.</span></span>  
  
4.  <span data-ttu-id="2fae1-146">在“可以通过此报表项切换显示”下拉框中，键入或选择要在其中显示切换图像的报表文本框的名称，例如 Textbox1\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2fae1-146">In **Display can be toggled by this report item**, from the drop-down box, type or select the name of a text box in the report in which to display a toggle image; for example, Textbox1.</span></span>  
  
     <span data-ttu-id="2fae1-147">在下图中，表配置为使用户可以展开或折叠此表。</span><span class="sxs-lookup"><span data-stu-id="2fae1-147">In the following image, the table is configured to enable users to expand and collapse it.</span></span> <span data-ttu-id="2fae1-148">表的显示通过“产品表”文本框进行切换。</span><span class="sxs-lookup"><span data-stu-id="2fae1-148">The display of the table is toggled by the Products Table text box.</span></span>  
  
     <span data-ttu-id="2fae1-149">![配置需展开的报表表格](../media/expandcollapse-reporttable.png "配置需展开的报表表格")</span><span class="sxs-lookup"><span data-stu-id="2fae1-149">![Configure a report table to be expanded](../media/expandcollapse-reporttable.png "Configure a report table to be expanded")</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2fae1-150">您选择的文本框必须位于此报表项的当前作用域或包含作用域中（上至表体）。</span><span class="sxs-lookup"><span data-stu-id="2fae1-150">The text box that you choose must be in the current or containing scope for this report item (up to and including the report body).</span></span> <span data-ttu-id="2fae1-151">例如，若要切换图表的可见性，请选择一个与该图表位于同一包含作用域中的文本框；例如，表体或矩形。</span><span class="sxs-lookup"><span data-stu-id="2fae1-151">For example, to toggle visibility of a chart, select a text box that is in the same containing scope as the chart; for example, the report body or a rectangle.</span></span> <span data-ttu-id="2fae1-152">文本框必须在同一容器层次结构或更高层次结构中。</span><span class="sxs-lookup"><span data-stu-id="2fae1-152">The text box must be in the same container hierarchy or higher.</span></span>  
  
5.  <span data-ttu-id="2fae1-153">若要测试该切换，请运行报表，然后单击带有切换图像的文本框。</span><span class="sxs-lookup"><span data-stu-id="2fae1-153">To test the toggle, run the report and click the text box with the toggle image.</span></span> <span data-ttu-id="2fae1-154">报表显示内容随即刷新，显示带有切换后的可见性的报表项。</span><span class="sxs-lookup"><span data-stu-id="2fae1-154">The report display refreshes to show report items with their toggled visibility.</span></span>  
  
     <span data-ttu-id="2fae1-155">![运行具有展开表格的报表](../media/expandcollapse-runreport-reporttable.png "运行具有展开表格的报表")</span><span class="sxs-lookup"><span data-stu-id="2fae1-155">![Running report with an expanding table](../media/expandcollapse-runreport-reporttable.png "Running report with an expanding table")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fae1-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2fae1-156">See Also</span></span>  
 <span data-ttu-id="2fae1-157">[&#40;报表生成器和 SSRS 的深化操作&#41;](drilldown-action-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2fae1-157">[Drilldown Action &#40;Report Builder and SSRS&#41;](drilldown-action-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="2fae1-158">隐藏项（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="2fae1-158">Hide an Item &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/hide-an-item-report-builder-and-ssrs.md)  
  
  
