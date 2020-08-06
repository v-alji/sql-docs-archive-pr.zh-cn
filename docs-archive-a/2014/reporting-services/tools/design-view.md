---
title: “设计”视图 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.layoutview.f1
helpviewer_keywords:
- Layout View dialog box
ms.assetid: 6fa378aa-442f-4d2f-beab-02a0fb5cd3ce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e4f8f3639318062bb36d650a57f63f9033a2ae73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689758"
---
# <a name="design-view"></a><span data-ttu-id="aa0f7-102">设计视图</span><span class="sxs-lookup"><span data-stu-id="aa0f7-102">Design View</span></span>
  <span data-ttu-id="aa0f7-103">使用“设计”视图可以排列报表中的报表项。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-103">Use Design view to arrange report items in the report.</span></span> <span data-ttu-id="aa0f7-104">设计视图有时称为设计图面或布局视图。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-104">Design view is sometimes called the design surface or layout view.</span></span>  
  
## <a name="report-design-surface"></a><span data-ttu-id="aa0f7-105">报表设计图面</span><span class="sxs-lookup"><span data-stu-id="aa0f7-105">Report Design Surface</span></span>  
 <span data-ttu-id="aa0f7-106">设计图面由三个部分组成：表体、页眉和页脚。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-106">The design surface consists of three sections: report body, page header, and page footer.</span></span> <span data-ttu-id="aa0f7-107">使用工具箱可以选择要放置在这三个部分的任一部分中的项。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-107">Use the Toolbox to select items to place in any of these three sections.</span></span> <span data-ttu-id="aa0f7-108">使用“报表数据”窗格可以查看图像、参数、数据源以及数据集（包括数据集查询和字段列表）。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-108">Use the Report Data pane to view images, parameters, data sources, and datasets, including dataset queries and field lists.</span></span> <span data-ttu-id="aa0f7-109">将报表项添加到设计图面后，请将数据集字段从 **“报表数据”** 窗格拖至数据区域（如表、矩阵或列表）。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-109">After you add report items to the design surface, drag dataset fields from the **Report Data** pane onto data regions such as table, matrix, or list.</span></span> <span data-ttu-id="aa0f7-110">报表设计图面上的每一项都包含属性，这些属性可以通过使用属性对话框或“属性”窗格进行管理。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-110">Each item on the report design surface contains properties that can be managed using a properties dialog box or the Properties pane.</span></span>  
  
## <a name="toolbox"></a><span data-ttu-id="aa0f7-111">工具箱</span><span class="sxs-lookup"><span data-stu-id="aa0f7-111">Toolbox</span></span>  
 <span data-ttu-id="aa0f7-112">工具箱列出了可用于报表的数据区域和其他报表项。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-112">The Toolbox lists data regions and other report items that are available for your report.</span></span> <span data-ttu-id="aa0f7-113">若要从工具箱添加报表项，请双击该报表项或将其拖至设计图面。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-113">To add report items from the Toolbox, double-click the item or drag it to the design surface.</span></span> <span data-ttu-id="aa0f7-114">然后使用对象控点可以更改报表项的形状和大小。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-114">You can then change the shape and size by using the object handles.</span></span>  
  
## <a name="report-data-pane"></a><span data-ttu-id="aa0f7-115">“报表数据”窗格</span><span class="sxs-lookup"><span data-stu-id="aa0f7-115">Report Data Pane</span></span>  
 <span data-ttu-id="aa0f7-116">若要查看“报表数据”窗格，请在 **“视图”** 菜单上单击 **“报表数据”**。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-116">To view the Report Data pane, on the **View** menu, click **Report Data**.</span></span> <span data-ttu-id="aa0f7-117">使用此窗格可以定义参数、图像、数据源以及数据集，还可以引用内置字段（如 ReportName）。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-117">Use this pane to define parameters, images, data sources, and datasets, and to reference built-in fields such as ReportName.</span></span> <span data-ttu-id="aa0f7-118">若要添加新项，请单击 **“新建”** 菜单，然后选择一项。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-118">To add a new item, click the **New** menu and select an item.</span></span> <span data-ttu-id="aa0f7-119">若要将计算字段添加到现有数据集，请单击 **“数据集”**，然后在 **“数据集属性”** 对话框中，选择 **“字段”**。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-119">To add calculated fields to an existing dataset, click **Dataset**, and in the **Dataset Properties** dialog box, select **Fields**.</span></span> <span data-ttu-id="aa0f7-120">选择一项，然后单击 **“编辑”** 打开 **“属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-120">Select an item and click **Edit** to open the **Properties** dialog box.</span></span> <span data-ttu-id="aa0f7-121">还可以在“报表数据”窗格中，右键单击项以添加项或更新项的属性。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-121">You can also right-click items in the Report Data pane to add items or update their properties.</span></span>  
  
 <span data-ttu-id="aa0f7-122">将项从“报表数据”窗格拖至设计图面上的数据区域和文本框可将数据和图像添加到报表中。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-122">Drag items from the Report Data pane to data regions and text boxes on the design surface to add data and images to a report.</span></span>  
  
 <span data-ttu-id="aa0f7-123">有关详细信息，请参阅 [Report Data Pane](../report-data/report-data-pane.md)。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-123">For more information, see [Report Data Pane](../report-data/report-data-pane.md).</span></span>  
  
## <a name="grouping-pane"></a><span data-ttu-id="aa0f7-124">“分组”窗格</span><span class="sxs-lookup"><span data-stu-id="aa0f7-124">Grouping Pane</span></span>  
 <span data-ttu-id="aa0f7-125">使用组可以将报表数据组织成可视层次结构，也可以计算总计。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-125">Groups are used to organize your report data into a visual hierarchy and to calculate totals.</span></span> <span data-ttu-id="aa0f7-126">使用“分组”窗格可以查看为表、矩阵或列表数据区域定义的组。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-126">Use the Grouping pane to view the groups defined for a table, matrix, or list data region.</span></span> <span data-ttu-id="aa0f7-127">默认情况下，“分组”窗格将所选数据区域的所有组显示为一个平展列表。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-127">By default, the Grouping pane displays all the groups for the selected data region as a flattened list.</span></span> <span data-ttu-id="aa0f7-128">对图表和仪表数据区域禁用“分组”窗格。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-128">The Grouping pane is disabled for Chart and Gauge data regions.</span></span>  
  
 <span data-ttu-id="aa0f7-129">若要查看各组彼此之间的关系，请将“分组”窗格切换为高级模式。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-129">To see the groups in relationship to one another, toggle the Grouping pane to Advanced mode.</span></span> <span data-ttu-id="aa0f7-130">此模式显示了组成员的层次结构，并以可视方式显示了与每个组对应的数据区域中的单元。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-130">This mode displays the hierarchy of group members, a visual display of cells in the data region that correspond to each group.</span></span>  
  
 <span data-ttu-id="aa0f7-131">有关详细信息，请参阅 [Grouping Pane](grouping-pane.md)。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-131">For more information, see [Grouping Pane](grouping-pane.md).</span></span>  
  
## <a name="page-header-and-page-footer"></a><span data-ttu-id="aa0f7-132">页眉和页脚</span><span class="sxs-lookup"><span data-stu-id="aa0f7-132">Page Header and Page Footer</span></span>  
 <span data-ttu-id="aa0f7-133">页眉和页脚分别位于每一页的顶部和底部。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-133">A page header and page footer run along the top and bottom of each page, respectively.</span></span> <span data-ttu-id="aa0f7-134">页眉和页脚可以包含静态文本、图像、线条、矩形、边框、背景色和背景图像。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-134">Headers and footers can contain static text, images, lines, rectangles, borders, background color, and background images.</span></span> <span data-ttu-id="aa0f7-135">若要将报表项添加到页眉和页脚，请右键单击设计图面，然后选择“页眉”或“页脚”。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-135">To add report items to the header or footer, right-click the design surface and select Header or Footer.</span></span> <span data-ttu-id="aa0f7-136">页眉和页脚部分将显示在设计图面上。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-136">Header and footer sections appear on the design surface.</span></span>  
  
## <a name="properties-pane"></a><span data-ttu-id="aa0f7-137">“属性”窗格</span><span class="sxs-lookup"><span data-stu-id="aa0f7-137">Properties Pane</span></span>  
 <span data-ttu-id="aa0f7-138">使用“属性”窗格可以查看设计图面上当前所选的报表项或“分组”窗格中的当前所选组。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-138">Use the Properties pane to view properties for the currently selected report item on the design surface or the currently selected group in the Grouping pane.</span></span> <span data-ttu-id="aa0f7-139">另外，也可以右键单击所选报表项或组，然后单击“属性”打开报表项或组的相应“属性”对话框\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aa0f7-139">Alternatively, you can right-click on a selected report item or group and then click **Properties** to open the corresponding **Properties** dialog box for the report item or group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa0f7-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aa0f7-140">See Also</span></span>  
 <span data-ttu-id="aa0f7-141">[页眉和页脚 &#40;报表生成器和 SSRS&#41;](../report-design/page-headers-and-footers-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="aa0f7-141">[Page Headers and Footers &#40;Report Builder and SSRS&#41;](../report-design/page-headers-and-footers-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="aa0f7-142">报表设计提示（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="aa0f7-142">Report Design Tips &#40;Report Builder and SSRS&#41;</span></span>](../report-design/report-design-tips-report-builder-and-ssrs.md)  
  
  
