---
title: 添加、移动或删除表、矩阵或列表（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4b97c470-cde0-4bb1-a46e-5f5f5553feaa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 43941639a41c897a49cd34662b74de26a27e3f07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692730"
---
# <a name="add-move-or-delete-a-table-matrix-or-list-report-builder-and-ssrs"></a><span data-ttu-id="4a26f-102">添加、移动或删除表、矩阵或列表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4a26f-102">Add, Move, or Delete a Table, Matrix, or List (Report Builder and SSRS)</span></span>
  <span data-ttu-id="4a26f-103">数据区域可显示来自报表数据集的数据。</span><span class="sxs-lookup"><span data-stu-id="4a26f-103">A data region displays data from a report dataset.</span></span> <span data-ttu-id="4a26f-104">数据区域包括表、矩阵、列表、图表和仪表。</span><span class="sxs-lookup"><span data-stu-id="4a26f-104">Data regions include table, matrix, list, chart, and gauge.</span></span> <span data-ttu-id="4a26f-105">若要将一个数据区域嵌套到另一个数据区域中，请分别添加每个数据区域，然后将子数据区域拖到父数据区域中。</span><span class="sxs-lookup"><span data-stu-id="4a26f-105">To nest one data region inside another, add each data region separately, and then drag the child data region onto the parent data region.</span></span>  
  
 <span data-ttu-id="4a26f-106">将表或矩阵数据区域添加到报表中的最简单方式是运行新建表或新建矩阵向导。</span><span class="sxs-lookup"><span data-stu-id="4a26f-106">The simplest way to add a table or matrix data region to your report is to run the New Table or New Matrix Wizard.</span></span> <span data-ttu-id="4a26f-107">这些向导将引导您完成选择数据源的连接、安排字段以及选择布局和样式的过程。</span><span class="sxs-lookup"><span data-stu-id="4a26f-107">These wizards will guide you through the process of choosing a connection to a data source, arranging fields, and choosing the layout and style.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4a26f-108">向导仅在报表生成器中可用。</span><span class="sxs-lookup"><span data-stu-id="4a26f-108">The wizard is available only in Report Builder.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-table-or-matrix-to-a-report-by-using-the-new-table-or-new-matrix-wizard"></a><span data-ttu-id="4a26f-109">通过使用新建表或新建矩阵向导，将表或矩阵添加到报表</span><span class="sxs-lookup"><span data-stu-id="4a26f-109">To add a table or matrix to a report by using the New Table or New Matrix Wizard</span></span>  
  
1.  <span data-ttu-id="4a26f-110">在 **“插入”** 选项卡上，单击 **“表”** 或 **“矩阵”** ，然后单击 **“表向导”** 或 **“矩阵向导”** 。</span><span class="sxs-lookup"><span data-stu-id="4a26f-110">On the **Insert** tab, click **Table** or **Matrix**, and then click **Table Wizard** or **Matrix Wizard**.</span></span>  
  
2.  <span data-ttu-id="4a26f-111">按照 " **NewTable** " 或 "**新建矩阵**" 向导中的步骤进行操作。</span><span class="sxs-lookup"><span data-stu-id="4a26f-111">Follow the steps in the **NewTable** or **New Matrix** wizard.</span></span>  
  
3.  <span data-ttu-id="4a26f-112">在 **“主文件夹”** 选项卡上，单击 **“运行”** ，以查看所呈现的报表。</span><span class="sxs-lookup"><span data-stu-id="4a26f-112">On the **Home** tab, click **Run** to see the rendered report.</span></span>  
  
4.  <span data-ttu-id="4a26f-113">在 **“运行”** 选项卡上，单击 **“设计”** 以继续处理报表。</span><span class="sxs-lookup"><span data-stu-id="4a26f-113">On the **Run** tab, click **Design** to continue working on the report.</span></span>  
  
### <a name="to-add-a-data-region"></a><span data-ttu-id="4a26f-114">添加数据区域</span><span class="sxs-lookup"><span data-stu-id="4a26f-114">To add a data region</span></span>  
  
1.  <span data-ttu-id="4a26f-115">在 **“功能区”** 上的 **“数据区域”** 组中，单击要添加的数据区域。</span><span class="sxs-lookup"><span data-stu-id="4a26f-115">On the **Ribbon**, in the **Data Regions** group, click the data region to add.</span></span>  
  
2.  <span data-ttu-id="4a26f-116">单击设计图面，然后拖动鼠标根据所需数据区域的大小创建一个框。</span><span class="sxs-lookup"><span data-stu-id="4a26f-116">Click the design surface, and then drag to create a box that is the desired size of the data region.</span></span>  
  
3.  <span data-ttu-id="4a26f-117">在“报表数据”窗格中，将报表数据集字段从“报表数据”窗格拖放至数据区域单元中。</span><span class="sxs-lookup"><span data-stu-id="4a26f-117">Drag a report dataset field from the Report Data pane onto a data region cell.</span></span> <span data-ttu-id="4a26f-118">该数据区域现已绑定到报表数据集的数据。</span><span class="sxs-lookup"><span data-stu-id="4a26f-118">The data region is now bound to data from the report dataset.</span></span>  
  
### <a name="to-select-a-data-region"></a><span data-ttu-id="4a26f-119">选择数据区域</span><span class="sxs-lookup"><span data-stu-id="4a26f-119">To select a data region</span></span>  
  
-   <span data-ttu-id="4a26f-120">对于 tablix 数据区域，右键单击角部控点。</span><span class="sxs-lookup"><span data-stu-id="4a26f-120">For a tablix data region, right-click the corner handle.</span></span> <span data-ttu-id="4a26f-121">对于图表或仪表数据区域，单击数据区域。</span><span class="sxs-lookup"><span data-stu-id="4a26f-121">For a chart or gauge data region, click in the data region.</span></span>  
  
     <span data-ttu-id="4a26f-122">随即显示一个选择控点和八个大小调整控点。</span><span class="sxs-lookup"><span data-stu-id="4a26f-122">A selection handle and eight resizing handles appear.</span></span>  
  
     <span data-ttu-id="4a26f-123">对于嵌套数据区域，在该嵌套数据区域中右键单击，再单击“选择”，然后选择所需的报表项  。</span><span class="sxs-lookup"><span data-stu-id="4a26f-123">For nested data regions, right-click in the nested data region, click **Select**, and then select the report item you want.</span></span> <span data-ttu-id="4a26f-124">若要验证所选择的报表项，请使用“属性”窗格。</span><span class="sxs-lookup"><span data-stu-id="4a26f-124">To verify which report item is selected, use the Properties pane.</span></span> <span data-ttu-id="4a26f-125">设计图面上所选项的名称显示在“属性”窗格的工具栏中。</span><span class="sxs-lookup"><span data-stu-id="4a26f-125">The name of the selected item on the design surface appears in the toolbar of the Properties pane.</span></span>  
  
### <a name="to-move-a-data-region"></a><span data-ttu-id="4a26f-126">移动数据区域</span><span class="sxs-lookup"><span data-stu-id="4a26f-126">To move a data region</span></span>  
  
-   <span data-ttu-id="4a26f-127">若要移动数据区域，请单击数据区域的选择控点，然后拖动该数据区域。</span><span class="sxs-lookup"><span data-stu-id="4a26f-127">To move a data region, click the selection handle of the data region and drag it.</span></span> <span data-ttu-id="4a26f-128">使用对齐线可以将该数据区域与现有报表项对齐。</span><span class="sxs-lookup"><span data-stu-id="4a26f-128">Use snaplines to align it to existing report items.</span></span>  
  
     <span data-ttu-id="4a26f-129">如果标尺不可见，请单击“视图”选项卡并选择 **“标尺”** 选项。</span><span class="sxs-lookup"><span data-stu-id="4a26f-129">If the ruler is not visible, click the View tab and select the **Ruler** option.</span></span>  
  
     <span data-ttu-id="4a26f-130">此外，也可以使用箭头键在设计图面上移动所选数据区域。</span><span class="sxs-lookup"><span data-stu-id="4a26f-130">Alternatively, use the arrow keys to move the selected data region on the design surface.</span></span>  
  
### <a name="to-delete-a-data-region"></a><span data-ttu-id="4a26f-131">删除数据区域</span><span class="sxs-lookup"><span data-stu-id="4a26f-131">To delete a data region</span></span>  
  
-   <span data-ttu-id="4a26f-132">选择数据区域，在该数据区域中右键单击，然后单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="4a26f-132">Select the data region, right-click in the data region, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a26f-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4a26f-133">See Also</span></span>  
 <span data-ttu-id="4a26f-134">[Tablix 数据区域（报表生成器和 SSRS）](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4a26f-134">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4a26f-135">[表 &#40;报表生成器和 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4a26f-135">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4a26f-136">[矩阵 &#40;报表生成器和 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4a26f-136">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4a26f-137">[列出 &#40;报表生成器和 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4a26f-137">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="4a26f-138">表、矩阵和列表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4a26f-138">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
