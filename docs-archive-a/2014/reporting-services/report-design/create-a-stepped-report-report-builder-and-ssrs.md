---
title: 创建递阶报表（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5933c4f0-c713-4ecb-b521-ff46c9c63fff
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d845993ac1462cef2d39638101e5c7b9fc314b94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580616"
---
# <a name="create-a-stepped-report-report-builder-and-ssrs"></a><span data-ttu-id="f41bf-102">创建递阶报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="f41bf-102">Create a Stepped Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f41bf-103">递阶报表可在父组下方的同一列中缩进显示详细信息行或子组，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="f41bf-103">A stepped report shows detail rows or child groups indented under a parent group in the same column, as shown in the example below:</span></span>  
  
 <span data-ttu-id="f41bf-104">![呈现的递阶报表](../media/steppedreportrendered.gif "呈现的递阶报表")</span><span class="sxs-lookup"><span data-stu-id="f41bf-104">![Rendered stepped report](../media/steppedreportrendered.gif "Rendered stepped report")</span></span>  
  
 <span data-ttu-id="f41bf-105">传统的表报表将父组放置在报表中的相邻列中。</span><span class="sxs-lookup"><span data-stu-id="f41bf-105">Traditional table reports place the parent group in an adjacent column on the report.</span></span> <span data-ttu-id="f41bf-106">利用新的 tablix 数据区域，可以向同一列添加组和详细信息行或子组。</span><span class="sxs-lookup"><span data-stu-id="f41bf-106">The new tablix data region enables you to add a group and detail rows or child groups to the same column.</span></span> <span data-ttu-id="f41bf-107">若要将组行与详细信息行或子组行区分开来，可以应用格式设置（如字体颜色）或缩进详细信息行。</span><span class="sxs-lookup"><span data-stu-id="f41bf-107">To differentiate the group rows from the detail or child group rows, you can apply formatting such as font color, or you can indent the detail rows.</span></span>  
  
 <span data-ttu-id="f41bf-108">本主题中的过程说明如何手动创建递阶报表，但您也可以使用新建表和矩阵向导。</span><span class="sxs-lookup"><span data-stu-id="f41bf-108">The procedures in this topic show you how to manually create a stepped report, but you can also use the New Table and Matrix Wizard.</span></span> <span data-ttu-id="f41bf-109">该向导为递阶报表提供布局，以便于创建递阶报表。</span><span class="sxs-lookup"><span data-stu-id="f41bf-109">It provides the layout for stepped reports, making it easy to create them.</span></span> <span data-ttu-id="f41bf-110">在完成该向导后，您可以进一步增强该报表。</span><span class="sxs-lookup"><span data-stu-id="f41bf-110">After you complete the wizard, you can further enhance the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f41bf-111">向导仅在报表生成器中可用。</span><span class="sxs-lookup"><span data-stu-id="f41bf-111">The wizard is available only in Report Builder.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-create-a-stepped-report"></a><span data-ttu-id="f41bf-112">创建递阶报表</span><span class="sxs-lookup"><span data-stu-id="f41bf-112">To create a stepped report</span></span>  
  
1.  <span data-ttu-id="f41bf-113">创建一个表报表。</span><span class="sxs-lookup"><span data-stu-id="f41bf-113">Create a table report.</span></span> <span data-ttu-id="f41bf-114">例如，插入一个 tablix 数据区域，然后向数据行中添加字段。</span><span class="sxs-lookup"><span data-stu-id="f41bf-114">For example, insert a tablix data region and add fields to the Data row.</span></span>  
  
2.  <span data-ttu-id="f41bf-115">向报表添加一个父组。</span><span class="sxs-lookup"><span data-stu-id="f41bf-115">Add a parent group to your report.</span></span>  
  
    1.  <span data-ttu-id="f41bf-116">单击表中的任意位置以选择该表。</span><span class="sxs-lookup"><span data-stu-id="f41bf-116">Click anywhere in the table to select it.</span></span> <span data-ttu-id="f41bf-117">“分组”窗格将显示“行组”窗格中的详细信息组。</span><span class="sxs-lookup"><span data-stu-id="f41bf-117">The Grouping pane displays the Details group in the Row Groups pane.</span></span>  
  
    2.  <span data-ttu-id="f41bf-118">在“分组”窗格中，右键单击“详细信息”组，指向“添加组”，然后单击“父组”   。</span><span class="sxs-lookup"><span data-stu-id="f41bf-118">In the Grouping Pane, right-click the Details Group, point to **Add Group**, and then click **Parent Group**.</span></span>  
  
    3.  <span data-ttu-id="f41bf-119">在“Tablix 组”对话框中，为该组提供一个名称，并键入或从下拉列表中选择组表达式  。</span><span class="sxs-lookup"><span data-stu-id="f41bf-119">In the **Tablix Group** dialog box, provide a name for the group and type or select a group expression from the drop-down list.</span></span> <span data-ttu-id="f41bf-120">该下拉列表显示了“报表数据”窗格中可用的简单字段表达式。</span><span class="sxs-lookup"><span data-stu-id="f41bf-120">The drop-down list displays the simple field expressions that are available in the Report Data pane.</span></span> <span data-ttu-id="f41bf-121">例如，[PostalCode] 是数据集中 PostalCode 字段的简单字段表达式。</span><span class="sxs-lookup"><span data-stu-id="f41bf-121">For example, [PostalCode] is a simple field expression for the PostalCode field in a dataset.</span></span>  
  
    4.  <span data-ttu-id="f41bf-122">选择 **“添加组头”** 。</span><span class="sxs-lookup"><span data-stu-id="f41bf-122">Select **Add group header**.</span></span> <span data-ttu-id="f41bf-123">选择此选项将向组的上方添加一个组标签和组合计的静态行。</span><span class="sxs-lookup"><span data-stu-id="f41bf-123">This option adds a static row above the group for the group label and group totals.</span></span> <span data-ttu-id="f41bf-124">同样地，可以选择 **“添加组尾”** 在组的下方添加一个静态行。</span><span class="sxs-lookup"><span data-stu-id="f41bf-124">Likewise, you can select **Add group footer** to add a static row below the group.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="f41bf-125">现在即创建了一个基本表格报表。</span><span class="sxs-lookup"><span data-stu-id="f41bf-125">You now have a basic tabular report.</span></span> <span data-ttu-id="f41bf-126">此报表呈现时，您将看到一列组实例值，以及一列或多列分组的详细信息数据。</span><span class="sxs-lookup"><span data-stu-id="f41bf-126">When it is rendered, you see one column with the group instance value, and one or more columns with grouped detail data.</span></span> <span data-ttu-id="f41bf-127">下图显示了该数据区域在设计图面上可能的外观。</span><span class="sxs-lookup"><span data-stu-id="f41bf-127">The following figure shows what the data region might look like on the design surface.</span></span>  
  
     <span data-ttu-id="f41bf-128">![带有组的表数据区域](../media/tabledataregionwithgroup.gif "带有组的表数据区域")</span><span class="sxs-lookup"><span data-stu-id="f41bf-128">![Table data region with group](../media/tabledataregionwithgroup.gif "Table data region with group")</span></span>  
  
     <span data-ttu-id="f41bf-129">下图显示了您查看报表时所呈现的数据区域可能的外观。</span><span class="sxs-lookup"><span data-stu-id="f41bf-129">The following figure shows how the rendered data region might look when you view the report.</span></span>  
  
     <span data-ttu-id="f41bf-130">![呈现的分组报表](../media/tablereportrendered.gif "呈现的分组报表")</span><span class="sxs-lookup"><span data-stu-id="f41bf-130">![Rendered grouped report](../media/tablereportrendered.gif "Rendered grouped report")</span></span>  
  
3.  <span data-ttu-id="f41bf-131">对于递阶报表，不需要用于显示组实例的第一列。</span><span class="sxs-lookup"><span data-stu-id="f41bf-131">For a stepped report, you do not need the first column that shows the group instance.</span></span> <span data-ttu-id="f41bf-132">相反，需要先复制组头单元中的值，再删除组列，然后将该值粘贴到组头行的第一个文本框中。</span><span class="sxs-lookup"><span data-stu-id="f41bf-132">Instead, copy the value in the group header cell, delete the group column, and paste in the first text box in the group header row.</span></span> <span data-ttu-id="f41bf-133">若要删除组列，请右键单击相应的组列或单元，然后单击“删除列”  。</span><span class="sxs-lookup"><span data-stu-id="f41bf-133">To remove the group column, right-click the group column or cell, and click **Delete Columns**.</span></span> <span data-ttu-id="f41bf-134">下图显示了该数据区域在设计图面上可能的外观。</span><span class="sxs-lookup"><span data-stu-id="f41bf-134">The following figure shows what the data region might look like on the design surface.</span></span>  
  
     <span data-ttu-id="f41bf-135">![带有组标头行的数据区域](../media/tabledataregiongroupheader.gif "带有组标头行的数据区域")</span><span class="sxs-lookup"><span data-stu-id="f41bf-135">![Data region with group header row](../media/tabledataregiongroupheader.gif "Data region with group header row")</span></span>  
  
4.  <span data-ttu-id="f41bf-136">若要使同一列中组头行下方的详细信息行缩进显示，请更改详细信息数据单元的空白大小。</span><span class="sxs-lookup"><span data-stu-id="f41bf-136">To indent the detail rows under the group header row in the same column, change the padding of the detail data cell.</span></span>  
  
    1.  <span data-ttu-id="f41bf-137">选择包含要缩进显示的详细信息字段的单元。</span><span class="sxs-lookup"><span data-stu-id="f41bf-137">Select the cell with the detail field that you want to indent.</span></span> <span data-ttu-id="f41bf-138">该单元的文本框属性显示在“属性”窗格中。</span><span class="sxs-lookup"><span data-stu-id="f41bf-138">The text box properties for that cell appear in the Properties pane.</span></span>  
  
    2.  <span data-ttu-id="f41bf-139">在“属性”窗格的 **“对齐”** 下，展开 **“填充”** 的属性。</span><span class="sxs-lookup"><span data-stu-id="f41bf-139">In the Properties pane, under **Alignment**, expand the properties for **Padding**.</span></span>  
  
    3.  <span data-ttu-id="f41bf-140">对于 "**左**"，键入新的填充值，如 `.5in` 。</span><span class="sxs-lookup"><span data-stu-id="f41bf-140">For **Left**, type a new padding value, such as `.5in`.</span></span> <span data-ttu-id="f41bf-141">填充会在单元中按照您指定的值缩进文本。</span><span class="sxs-lookup"><span data-stu-id="f41bf-141">Padding indents the text in the cell by the value you specify.</span></span> <span data-ttu-id="f41bf-142">默认空白大小为 2 磅。</span><span class="sxs-lookup"><span data-stu-id="f41bf-142">The default padding is 2 points.</span></span> <span data-ttu-id="f41bf-143">填充属性的有效值是零或正数，后跟一个大小指示符。</span><span class="sxs-lookup"><span data-stu-id="f41bf-143">Valid values for the Padding properties are zero or a positive number, followed by a size designator.</span></span>  
  
         <span data-ttu-id="f41bf-144">大小指示符有：</span><span class="sxs-lookup"><span data-stu-id="f41bf-144">Size designators are:</span></span>  
  
        |||  
        |-|-|  
        |`in`|<span data-ttu-id="f41bf-145">英寸（1 英寸 = 2.54 厘米）</span><span class="sxs-lookup"><span data-stu-id="f41bf-145">Inches (1 inch = 2.54 centimeters)</span></span>|  
        |`cm`|<span data-ttu-id="f41bf-146">厘米</span><span class="sxs-lookup"><span data-stu-id="f41bf-146">Centimeters</span></span>|  
        |`mm`|<span data-ttu-id="f41bf-147">毫米</span><span class="sxs-lookup"><span data-stu-id="f41bf-147">Millimeters</span></span>|  
        |`pt`|<span data-ttu-id="f41bf-148">磅（1 磅 = 1/72 英寸）</span><span class="sxs-lookup"><span data-stu-id="f41bf-148">Points (1 point = 1/72 inch)</span></span>|  
        |`pc`|<span data-ttu-id="f41bf-149">派卡（1 派卡 = 12 磅）</span><span class="sxs-lookup"><span data-stu-id="f41bf-149">Picas (1 pica = 12 points)</span></span>|  
  
     <span data-ttu-id="f41bf-150">数据区域的外观将与下例类似。</span><span class="sxs-lookup"><span data-stu-id="f41bf-150">Your data region will look similar to the following example.</span></span>  
  
     <span data-ttu-id="f41bf-151">![递阶报表的数据区域](../media/steppedreportdataregion.gif "递阶报表的数据区域")</span><span class="sxs-lookup"><span data-stu-id="f41bf-151">![Data region for stepped report](../media/steppedreportdataregion.gif "Data region for stepped report")</span></span>  
  
     <span data-ttu-id="f41bf-152">**递阶报表布局的数据区域**</span><span class="sxs-lookup"><span data-stu-id="f41bf-152">**Data Region for Stepped Report Layout**</span></span>  
  
     <span data-ttu-id="f41bf-153">在 **“主文件夹”** 选项卡上，单击 **“运行”**。</span><span class="sxs-lookup"><span data-stu-id="f41bf-153">On the **Home** tab Click **Run**.</span></span> <span data-ttu-id="f41bf-154">报表将根据子组值的缩进级别显示组。</span><span class="sxs-lookup"><span data-stu-id="f41bf-154">The report displays the group with indented levels for the child group values.</span></span>  
  
### <a name="to-create-a-stepped-report-with-multiple-groups"></a><span data-ttu-id="f41bf-155">创建包含多个组的递阶报表</span><span class="sxs-lookup"><span data-stu-id="f41bf-155">To create a stepped report with multiple groups</span></span>  
  
1.  <span data-ttu-id="f41bf-156">按照前面步骤中所述创建一个报表。</span><span class="sxs-lookup"><span data-stu-id="f41bf-156">Create a report as described in the previous procedure.</span></span>  
  
2.  <span data-ttu-id="f41bf-157">向报表添加其他组。</span><span class="sxs-lookup"><span data-stu-id="f41bf-157">Add additional groups to your report.</span></span>  
  
    1.  <span data-ttu-id="f41bf-158">在“行组”窗格中，右键单击组，再单击“添加组”，然后选择要添加的组的类型\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f41bf-158">In the Row Groups pane, right-click the group, click **Add Group**, and then choose the type of group you want to add.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="f41bf-159">可以通过若干种方式向数据区域添加组。</span><span class="sxs-lookup"><span data-stu-id="f41bf-159">There are several ways to add groups to a data region.</span></span> <span data-ttu-id="f41bf-160">有关详细信息，请参阅[在数据区域中添加或删除组 &#40;报表生成器和 SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f41bf-160">For more information, see [Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md).</span></span>  
  
    2.  <span data-ttu-id="f41bf-161">在 **“Tablix 组”** 对话框中，键入一个名称。</span><span class="sxs-lookup"><span data-stu-id="f41bf-161">In the **Tablix Group** dialog box, type a name.</span></span>  
  
    3.  <span data-ttu-id="f41bf-162">在 **“组表达式”** 中，键入一个表达式或选择要用作分组依据的数据集字段。</span><span class="sxs-lookup"><span data-stu-id="f41bf-162">In **Group expression**, type an expression or select a dataset field to group on.</span></span> <span data-ttu-id="f41bf-163">要创建表达式，请单击表达式 (fx) 按钮打开“表达式”对话框\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f41bf-163">To create an expression, click the expression (**fx**) button to open the **Expression** dialog box.</span></span>  
  
    4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
3.  <span data-ttu-id="f41bf-164">更改用于显示组数据的单元的填充值。</span><span class="sxs-lookup"><span data-stu-id="f41bf-164">Change the padding for the cell that displays the group data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f41bf-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f41bf-165">See Also</span></span>  
 <span data-ttu-id="f41bf-166">[页眉和页脚 &#40;报表生成器和 SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f41bf-166">[Page Headers and Footers &#40;Report Builder and SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f41bf-167">[&#40;报表生成器和 SSRS 的格式设置报表项&#41;](formatting-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f41bf-167">[Formatting Report Items &#40;Report Builder and SSRS&#41;](formatting-report-items-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f41bf-168">[Tablix 数据区域 &#40;报表生成器和 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f41bf-168">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f41bf-169">[表 &#40;报表生成器和 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f41bf-169">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f41bf-170">[矩阵 &#40;报表生成器和 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f41bf-170">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f41bf-171">[列出 &#40;报表生成器和 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f41bf-171">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f41bf-172">表、矩阵和列表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="f41bf-172">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
