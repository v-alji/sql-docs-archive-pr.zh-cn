---
title: 第 5 课：设置报表格式 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ae46efa9-6e04-48ec-afb4-5a2314dcb05a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 00f0d780e957fd9ff995fefb1d033275a7da428d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590578"
---
# <a name="lesson-5-formatting-a-report-reporting-services"></a><span data-ttu-id="36ff2-102">Lesson 5: Formatting a Report (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="36ff2-102">Lesson 5: Formatting a Report (Reporting Services)</span></span>
  <span data-ttu-id="36ff2-103">既然您已经向 Sales Orders 报表添加了一个数据区域和一些字段，那么您就可以设置日期和货币字段以及列标题的格式。</span><span class="sxs-lookup"><span data-stu-id="36ff2-103">Now that you've added a data region and some fields to the Sales Orders report, you can format the date and currency fields and the column headers.</span></span>  
  
 <span data-ttu-id="36ff2-104">本主题内容：</span><span class="sxs-lookup"><span data-stu-id="36ff2-104">In this topic:</span></span>  
  
-   [<span data-ttu-id="36ff2-105">设置日期格式</span><span class="sxs-lookup"><span data-stu-id="36ff2-105">Format the Date</span></span>](#bkmk_format_date)  
  
-   [<span data-ttu-id="36ff2-106">设置货币格式</span><span class="sxs-lookup"><span data-stu-id="36ff2-106">Format the Currency</span></span>](#bkmk_format_currency)  
  
-   [<span data-ttu-id="36ff2-107">更改文本样式和列宽</span><span class="sxs-lookup"><span data-stu-id="36ff2-107">Change Text Style and Column Widths</span></span>](#bkmk_change_textstyle)  
  
##  <a name="format-the-date"></a><a name="bkmk_format_date"></a><span data-ttu-id="36ff2-108">设置日期格式</span><span class="sxs-lookup"><span data-stu-id="36ff2-108">Format the Date</span></span>  
 <span data-ttu-id="36ff2-109">默认情况下，Date 字段显示日期和时间信息。</span><span class="sxs-lookup"><span data-stu-id="36ff2-109">The Date field displays date and time information by default.</span></span> <span data-ttu-id="36ff2-110">您可以设置其格式，使其只显示日期。</span><span class="sxs-lookup"><span data-stu-id="36ff2-110">You can format it to display only the date.</span></span>  
  
#### <a name="to-format-a-date-field"></a><span data-ttu-id="36ff2-111">设置日期字段格式</span><span class="sxs-lookup"><span data-stu-id="36ff2-111">To format a date field</span></span>  
  
1.  <span data-ttu-id="36ff2-112">单击 **“设计”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="36ff2-112">Click the **Design** tab.</span></span>  
  
2.  <span data-ttu-id="36ff2-113">右键单击带有 `[Date]` 字段表达式的单元格，然后单击“文本框属性”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="36ff2-113">Right-click the cell with the `[Date]` field expression and then click **Text Box Properties**.</span></span>  
  
3.  <span data-ttu-id="36ff2-114">单击 "**数字**"，然后在 "**类别**" 字段中选择 `Date` 。</span><span class="sxs-lookup"><span data-stu-id="36ff2-114">Click **Number**, and then in the **Category** field, select `Date`.</span></span>  
  
4.  <span data-ttu-id="36ff2-115">在 **“类型”** 框中，选择 **“2000 年 1 月 31 日”**。</span><span class="sxs-lookup"><span data-stu-id="36ff2-115">In the **Type** box, select **January 31, 2000**.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="36ff2-116">预览报表以查看对 `[Date]` 字段的更改，然后更改回设计视图。</span><span class="sxs-lookup"><span data-stu-id="36ff2-116">Preview the report to see the change to the `[Date]` field and then change back to design view.</span></span>  
  
##  <a name="format-the-currency"></a><a name="bkmk_format_currency"></a><span data-ttu-id="36ff2-117">设置货币格式</span><span class="sxs-lookup"><span data-stu-id="36ff2-117">Format the Currency</span></span>  
 <span data-ttu-id="36ff2-118">LineTotal 字段显示常规数字。</span><span class="sxs-lookup"><span data-stu-id="36ff2-118">The LineTotal field displays a general number.</span></span> <span data-ttu-id="36ff2-119">请设置其格式，以使其显示货币形式的数字。</span><span class="sxs-lookup"><span data-stu-id="36ff2-119">Format it to display the number as currency.</span></span>  
  
#### <a name="to-format-a-currency-field"></a><span data-ttu-id="36ff2-120">设置货币字段格式</span><span class="sxs-lookup"><span data-stu-id="36ff2-120">To format a currency field</span></span>  
  
1.  <span data-ttu-id="36ff2-121">右键单击带有 `[LineTotal]` 字段表达式的单元格，然后单击“文本框属性”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="36ff2-121">Right-click the cell with the `[LineTotal]` field expression and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="36ff2-122">单击 **“数字”**，然后在 **“类别”** 字段中，选择 **“货币”**。</span><span class="sxs-lookup"><span data-stu-id="36ff2-122">Click **Number**, and in the **Category** field, select **Currency**.</span></span>  
  
3.  <span data-ttu-id="36ff2-123">如果区域设置为“英语(美国)”，则默认设置应为：</span><span class="sxs-lookup"><span data-stu-id="36ff2-123">If your regional setting is English (United States), the defaults should be:</span></span>  
  
    -   <span data-ttu-id="36ff2-124">**小数位数：2**</span><span class="sxs-lookup"><span data-stu-id="36ff2-124">**Decimal places: 2**</span></span>  
  
    -   <span data-ttu-id="36ff2-125">**负数：($12345.00)**</span><span class="sxs-lookup"><span data-stu-id="36ff2-125">**Negative numbers: ($12345.00)**</span></span>  
  
    -   <span data-ttu-id="36ff2-126">**符号：$ 英语(美国)**</span><span class="sxs-lookup"><span data-stu-id="36ff2-126">**Symbol: $ English (United States)**</span></span>  
  
4.  <span data-ttu-id="36ff2-127">选择“使用千位分隔符(,)”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="36ff2-127">Select **Use 1000 separator (,)**.</span></span>  
  
     <span data-ttu-id="36ff2-128">如果示例文本为 **$12,345.00**，则说明您的设置是正确的。</span><span class="sxs-lookup"><span data-stu-id="36ff2-128">If the sample text is:**$12,345.00**, then your settings are correct.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="36ff2-129">预览报表以查看对 `[LineTotal]` 字段的更改，然后更改回设计视图。</span><span class="sxs-lookup"><span data-stu-id="36ff2-129">Preview the report to see the change to the `[LineTotal]` field and then change back to design view.</span></span>  
  
##  <a name="change-text-style-and-column-widths"></a><a name="bkmk_change_textstyle"></a><span data-ttu-id="36ff2-130">更改文本样式和列宽</span><span class="sxs-lookup"><span data-stu-id="36ff2-130">Change Text Style and Column Widths</span></span>  
 <span data-ttu-id="36ff2-131">还可以更改标题行的格式设置，以使其与报表中的数据行区分开来。</span><span class="sxs-lookup"><span data-stu-id="36ff2-131">You can also change the formatting of the header row to differentiate it from the rows of data in the report.</span></span> <span data-ttu-id="36ff2-132">最后，您将调整列的宽度。</span><span class="sxs-lookup"><span data-stu-id="36ff2-132">Lastly, you will adjust the widths of the columns.</span></span>  
  
#### <a name="to-format-header-rows-and-table-columns"></a><span data-ttu-id="36ff2-133">设置标题行和表列的格式</span><span class="sxs-lookup"><span data-stu-id="36ff2-133">To format header rows and table columns</span></span>  
  
1.  <span data-ttu-id="36ff2-134">单击表，以便在此表的上方和旁边显示列控点和行控点。</span><span class="sxs-lookup"><span data-stu-id="36ff2-134">Click the table so that column and row handles appear above and next to the table.</span></span>  
  
     <span data-ttu-id="36ff2-135">![设计，带有标题行和详细信息行的表](../../2014/tutorials/media/rs-basictabledetailsdesign.gif "设计，带有标题行和详细信息行的表")</span><span class="sxs-lookup"><span data-stu-id="36ff2-135">![Design, Table with header row and detail row](../../2014/tutorials/media/rs-basictabledetailsdesign.gif "Design, Table with header row and detail row")</span></span>  
  
     <span data-ttu-id="36ff2-136">沿此表的上方和一侧显示的灰色条状物就是列控点和行控点。</span><span class="sxs-lookup"><span data-stu-id="36ff2-136">The gray bars along the top and side of the table are the column and row handles.</span></span>  
  
2.  <span data-ttu-id="36ff2-137">指向列控点之间的行，使光标变为双箭头。</span><span class="sxs-lookup"><span data-stu-id="36ff2-137">Point to the line between column handles so that the cursor changes into a double arrow.</span></span> <span data-ttu-id="36ff2-138">拖动列，调整到所需大小。</span><span class="sxs-lookup"><span data-stu-id="36ff2-138">Drag the columns to the size you want.</span></span>  
  
3.  <span data-ttu-id="36ff2-139">选择包含列标题标签的行，从 **“格式”** 菜单中，指向 **“字体”** ，然后单击 **“加粗”**。</span><span class="sxs-lookup"><span data-stu-id="36ff2-139">Select the row containing column header labels and from the **Format** menu, point to **Font** and then click **Bold**.</span></span>  
  
4.  <span data-ttu-id="36ff2-140">若要预览报表，请单击 "**预览**" 选项卡。其外观应如下所示：</span><span class="sxs-lookup"><span data-stu-id="36ff2-140">To preview your report, click the **Preview** tab. It should look something like this:</span></span>  
  
     <span data-ttu-id="36ff2-141">![带有以粗体显示的列标题的表预览](../../2014/tutorials/media/rs-basictabledetailsformattedpreview.gif "带有以粗体显示的列标题的表预览")</span><span class="sxs-lookup"><span data-stu-id="36ff2-141">![Preview of table with bold column headers](../../2014/tutorials/media/rs-basictabledetailsformattedpreview.gif "Preview of table with bold column headers")</span></span>  
  
5.  <span data-ttu-id="36ff2-142">在 **“文件”** 菜单上单击 **“全部保存”** 可保存报表。</span><span class="sxs-lookup"><span data-stu-id="36ff2-142">On the **File** menu, click **Save All** to save the report.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="36ff2-143">后续步骤</span><span class="sxs-lookup"><span data-stu-id="36ff2-143">Next Steps</span></span>  
 <span data-ttu-id="36ff2-144">您已成功地设置了列标题以及日期和货币值的格式。</span><span class="sxs-lookup"><span data-stu-id="36ff2-144">You have successfully formatted column headers and date and currency values.</span></span> <span data-ttu-id="36ff2-145">接下来，您将向报表中添加分组和总计。</span><span class="sxs-lookup"><span data-stu-id="36ff2-145">Next, you will add grouping and totals to your report.</span></span> <span data-ttu-id="36ff2-146">请参阅[第 6 课：添加分组和总计 (Reporting Services)](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="36ff2-146">See [Lesson 6: Adding Grouping and Totals &#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36ff2-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="36ff2-147">See Also</span></span>  
 <span data-ttu-id="36ff2-148">[设置数字和日期格式 &#40;报表生成器和 SSRS&#41;](report-design/formatting-numbers-and-dates-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="36ff2-148">[Formatting Numbers and Dates &#40;Report Builder and SSRS&#41;](report-design/formatting-numbers-and-dates-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="36ff2-149">呈现行为（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="36ff2-149">Rendering Behaviors &#40;Report Builder  and SSRS&#41;</span></span>](report-design/rendering-behaviors-report-builder-and-ssrs.md)  
  
  
