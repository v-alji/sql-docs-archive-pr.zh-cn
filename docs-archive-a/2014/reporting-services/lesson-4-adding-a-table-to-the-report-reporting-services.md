---
title: 第 4 课：向报表添加表 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ddf2914-bcdd-427d-8cba-0ccb8342f819
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 52694168bd60b8e3807db6204f33a89815573093
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578711"
---
# <a name="lesson-4-adding-a-table-to-the-report-reporting-services"></a><span data-ttu-id="88336-102">第 4 课：向报表添加表 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="88336-102">Lesson 4: Adding a Table to the Report (Reporting Services)</span></span>
  <span data-ttu-id="88336-103">定义数据集后，您可以开始定义报表。</span><span class="sxs-lookup"><span data-stu-id="88336-103">After the dataset is defined, you can start designing the report.</span></span> <span data-ttu-id="88336-104">将要纳入报表的数据区域、文本框、图像和其他项拖放到设计图面上来创建报表布局。</span><span class="sxs-lookup"><span data-stu-id="88336-104">You create a report layout by dragging and dropping data regions, text boxes, images, and other items that you want to include in your report to the design surface.</span></span>  
  
 <span data-ttu-id="88336-105">包含基础数据集中重复数据行的项称为“数据区域”\*\*。</span><span class="sxs-lookup"><span data-stu-id="88336-105">Items that contain repeated rows of data from underlying datasets are called *data regions*.</span></span> <span data-ttu-id="88336-106">基本报表将只有一个数据区域，但是对于要将图表添加到表格报表等情况，则可以添加多个数据区域。</span><span class="sxs-lookup"><span data-stu-id="88336-106">A basic report will have only one data region, but you can add more, for example, if you want to add a chart to your tabular report.</span></span> <span data-ttu-id="88336-107">添加数据区域之后，可以向该数据区域添加字段。</span><span class="sxs-lookup"><span data-stu-id="88336-107">After you add a data region, you can add fields to the data region.</span></span>  
  
### <a name="to-add-a-table-data-region-and-fields-to-a-report-layout"></a><span data-ttu-id="88336-108">向报表布局中添加表数据区域和字段</span><span class="sxs-lookup"><span data-stu-id="88336-108">To add a Table data region and fields to a report layout</span></span>  
  
1.  <span data-ttu-id="88336-109">在“工具箱”中，单击“表”，然后单击设计图面并拖动鼠标”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="88336-109">In the **Toolbox**, click **Table**, and then click on the design surface and drag the mouse.</span></span> <span data-ttu-id="88336-110">报表设计器将在设计图面中心绘制一个具有三列的数据区域。</span><span class="sxs-lookup"><span data-stu-id="88336-110">Report Designer draws a table data region with three columns in the center of the design surface.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="88336-111">“工具箱”可能显示为“报表数据”窗格左侧的一个选项卡\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="88336-111">The **Toolbox** may appear as a tab on the left side of the **Report Data** pane.</span></span> <span data-ttu-id="88336-112">若要打开 "**工具箱**"，请将指针移到 "**工具箱**" 选项卡上。如果**工具箱**不可见，请在 "**视图**" 菜单中单击 **"工具箱**"。</span><span class="sxs-lookup"><span data-stu-id="88336-112">To open the **Toolbox**, move the pointer over the **Toolbox** tab. If the **Toolbox** is not visible, from the **View** menu, click **Toolbox**.</span></span>  
  
2.  <span data-ttu-id="88336-113">在 "**报表数据**" 窗格中，展开**AdventureWorksDataset**数据集以显示字段。</span><span class="sxs-lookup"><span data-stu-id="88336-113">In the **Report Data** pane, expand the **AdventureWorksDataset** dataset to display the fields.</span></span>  
  
3.  <span data-ttu-id="88336-114">将 Date 字段从“报表数据”窗格拖到表的第一列中\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="88336-114">Drag the Date field from the **Report Data** pane to the first column in the table.</span></span>  
  
     <span data-ttu-id="88336-115">将字段拖到第一列中时，会发生两件事。</span><span class="sxs-lookup"><span data-stu-id="88336-115">When you drop the field into the first column, two things happen.</span></span> <span data-ttu-id="88336-116">首先，数据单元将在方括号中显示字段名称，也称为“字段表达式”\*\*：`[Date]`。</span><span class="sxs-lookup"><span data-stu-id="88336-116">First, the data cell will display the field name, known as the *field expression*, in brackets: `[Date]`.</span></span> <span data-ttu-id="88336-117">其次，列标题值自动添加到紧邻字段表达式上面的标题行。</span><span class="sxs-lookup"><span data-stu-id="88336-117">Second, a column header value is automatically added to Header row, just above the field expression.</span></span> <span data-ttu-id="88336-118">默认情况下，该列是字段的名称。</span><span class="sxs-lookup"><span data-stu-id="88336-118">By default, the column is the name of the field.</span></span> <span data-ttu-id="88336-119">您可以选中标题行文本，然后键入一个新名称。</span><span class="sxs-lookup"><span data-stu-id="88336-119">You can select the Header row text and type a new name.</span></span>  
  
4.  <span data-ttu-id="88336-120">将 Order 字段从“报表数据”窗格拖到表的第二列中\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="88336-120">Drag the Order field from the **Report Data** pane to the second column in the table.</span></span>  
  
5.  <span data-ttu-id="88336-121">将 Product 字段从“报表数据”窗格拖到表的第三列中\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="88336-121">Drag the Product field from the **Report Data** pane to the third column in the table.</span></span>  
  
6.  <span data-ttu-id="88336-122">将 Qty 字段拖到第三列的右边缘，直到显示一个垂直光标且鼠标指针带有加号 [+] 为止。</span><span class="sxs-lookup"><span data-stu-id="88336-122">Drag the Qty field to the right edge of the third column until you get a vertical cursor and the mouse pointer has a plus sign [+].</span></span> <span data-ttu-id="88336-123">释放鼠标按钮后，将为 `[Qty]`创建第四列。</span><span class="sxs-lookup"><span data-stu-id="88336-123">When you release the mouse button, a fourth column is created for `[Qty]`.</span></span>  
  
7.  <span data-ttu-id="88336-124">请以相同方式添加 LineTotal 字段，并创建第五列。</span><span class="sxs-lookup"><span data-stu-id="88336-124">Add the LineTotal field in the same way, creating a fifth column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="88336-125">列标题是 Line Total。</span><span class="sxs-lookup"><span data-stu-id="88336-125">The column header is Line Total.</span></span> <span data-ttu-id="88336-126">报表设计器通过将 LineTotal 拆分为两个单词，自动创建该列的友好名称。</span><span class="sxs-lookup"><span data-stu-id="88336-126">Report Designer automatically creates a friendly name for the column by splitting LineTotal into two words.</span></span>  
  
     <span data-ttu-id="88336-127">以下关系图显示已由下列字段填充的表数据区域：Date、Order、Product、Qty 和 Line Total。</span><span class="sxs-lookup"><span data-stu-id="88336-127">The following diagram shows a table data region that has been populated with these fields: Date, Order, Product, Qty, and Line Total.</span></span>  
  
     <span data-ttu-id="88336-128">![设计，带有标题行和详细信息行的表](../../2014/tutorials/media/rs-basictabledetailsdesign.gif "设计，带有标题行和详细信息行的表")</span><span class="sxs-lookup"><span data-stu-id="88336-128">![Design, Table with header row and detail row](../../2014/tutorials/media/rs-basictabledetailsdesign.gif "Design, Table with header row and detail row")</span></span>  
  
## <a name="preview-your-report"></a><span data-ttu-id="88336-129">预览报表</span><span class="sxs-lookup"><span data-stu-id="88336-129">Preview Your Report</span></span>  
 <span data-ttu-id="88336-130">通过预览报表，您可以不必先将报表发布到报表服务器，即可查看呈现的报表。</span><span class="sxs-lookup"><span data-stu-id="88336-130">Previewing a report enables you to view the rendered report without having to first publish it to a report server.</span></span> <span data-ttu-id="88336-131">您可能希望在设计时频繁预览报表。</span><span class="sxs-lookup"><span data-stu-id="88336-131">You will probably want to preview your report frequently during design time.</span></span> <span data-ttu-id="88336-132">预览报表还将对设计和数据连接进行验证，以便您可以在将报表发布到报表服务器之前更正错误和问题。</span><span class="sxs-lookup"><span data-stu-id="88336-132">Previewing the report will also run validation on the design and data connections so you can correct errors and issues before publishing the report to a report server.</span></span>  
  
#### <a name="to-preview-a-report"></a><span data-ttu-id="88336-133">预览报表</span><span class="sxs-lookup"><span data-stu-id="88336-133">To preview a report</span></span>  
  
-   <span data-ttu-id="88336-134">单击 "**预览**" 选项卡。报表设计器运行报表并将其显示在 "预览" 视图中。</span><span class="sxs-lookup"><span data-stu-id="88336-134">Click the **Preview** tab. Report Designer runs the report and displays it in Preview view.</span></span>  
  
     <span data-ttu-id="88336-135">下图显示了“预览”视图中的部分报表。</span><span class="sxs-lookup"><span data-stu-id="88336-135">The following diagram shows part of the report in Preview view.</span></span>  
  
     <span data-ttu-id="88336-136">![具有 5 列的表的详细信息行预览](../../2014/tutorials/media/rs-basictabledetailspreview.gif "具有 5 列的表的详细信息行预览")</span><span class="sxs-lookup"><span data-stu-id="88336-136">![Preview, Detail rows of table with 5 columns](../../2014/tutorials/media/rs-basictabledetailspreview.gif "Preview, Detail rows of table with 5 columns")</span></span>  
  
     <span data-ttu-id="88336-137">请注意，Line Total 列中货币的小数点后面有六个小数位，并且日期包含时间戳。</span><span class="sxs-lookup"><span data-stu-id="88336-137">Notice that the currency (in the Line Total column) has six places after the decimal, and the date has includes a time stamp.</span></span> <span data-ttu-id="88336-138">此格式问题将在下一课中进行修复。</span><span class="sxs-lookup"><span data-stu-id="88336-138">You're going to fix that formatting in the next lesson.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="88336-139">在 **“文件”** 菜单上单击 **“全部保存”** 可保存报表。</span><span class="sxs-lookup"><span data-stu-id="88336-139">On the **File** menu, click **Save All** to save the report.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="88336-140">后续步骤</span><span class="sxs-lookup"><span data-stu-id="88336-140">Next Steps</span></span>  
 <span data-ttu-id="88336-141">您已成功地向报表添加了表数据区域、向数据区域添加了字段，并成功地预览了报表。</span><span class="sxs-lookup"><span data-stu-id="88336-141">You have successfully added a Table data region to your report, added fields to the data region, and previewed your report.</span></span> <span data-ttu-id="88336-142">接下来，将设置列标题以及日期和货币值的格式。</span><span class="sxs-lookup"><span data-stu-id="88336-142">Next, you will format column headers and date and currency values.</span></span> <span data-ttu-id="88336-143">请参阅[第 5 课：设置报表格式 (Reporting Services)](../reporting-services/lesson-5-formatting-a-report-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="88336-143">See [Lesson 5: Formatting a Report &#40;Reporting Services&#41;](../reporting-services/lesson-5-formatting-a-report-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88336-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="88336-144">See Also</span></span>  
 <span data-ttu-id="88336-145">[表 &#40;报表生成器和 SSRS&#41;](report-design/tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="88336-145">[Tables &#40;Report Builder  and SSRS&#41;](report-design/tables-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="88336-146">数据集字段集合（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="88336-146">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
  
  
