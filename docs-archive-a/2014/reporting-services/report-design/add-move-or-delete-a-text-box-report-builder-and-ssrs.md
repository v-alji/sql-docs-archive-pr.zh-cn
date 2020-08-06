---
title: 添加、移动或删除文本框（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f042cf81-d933-4ac7-9287-c074a46bde98
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cd85415fd2f0bac2a37b3fbda06795e10f351b19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692729"
---
# <a name="add-move-or-delete-a-text-box-report-builder-and-ssrs"></a><span data-ttu-id="821b0-102">添加、移动或删除文本框（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="821b0-102">Add, Move, or Delete a Text Box (Report Builder and SSRS)</span></span>
  <span data-ttu-id="821b0-103">文本框是报表中最常用的报表项。</span><span class="sxs-lookup"><span data-stu-id="821b0-103">Text boxes are the most commonly used report item in reports.</span></span> <span data-ttu-id="821b0-104">您可以向表体添加文本框以显示诸如标题、参数选择、内置字段以及日期之类的信息。</span><span class="sxs-lookup"><span data-stu-id="821b0-104">You can add a text box to the report body to display information such as titles, parameter choices, built-in fields, and dates.</span></span>  
  
 <span data-ttu-id="821b0-105">表或矩阵中的每个单元其实都是一个文本框。</span><span class="sxs-lookup"><span data-stu-id="821b0-105">Every cell in a table or matrix is really a text box.</span></span> <span data-ttu-id="821b0-106">报表中通过表和矩阵显示的所有报表数据几乎都是报表处理器计算报表中每个文本框的内容的结果。</span><span class="sxs-lookup"><span data-stu-id="821b0-106">Almost all report data displayed in a report with tables and matrices is the result of the report processor evaluating the contents of each text box in the report.</span></span> <span data-ttu-id="821b0-107">因而，可以用与设置数据区域外其他文本框的格式相同的方式设置单元格式。</span><span class="sxs-lookup"><span data-stu-id="821b0-107">As such, you can format cells in the same way you would format other text boxes outside the data region.</span></span>  
  
 <span data-ttu-id="821b0-108">若要向列表数据区域中添加文本框，必须先添加文本框，然后将其拖至列表中。</span><span class="sxs-lookup"><span data-stu-id="821b0-108">To add a text box to a list data region, you must first add the text box and then drag it into the list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="821b0-109">单击文本框后，便可立即编辑文本框中的文本。</span><span class="sxs-lookup"><span data-stu-id="821b0-109">When you click a text box, you're immediately editing the text in the text box.</span></span> <span data-ttu-id="821b0-110">若要选择文本框本身而不是文本框内的文本，请按 ESC。</span><span class="sxs-lookup"><span data-stu-id="821b0-110">To select the text box itself, not the text in it, press ESC.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-text-box"></a><span data-ttu-id="821b0-111">添加文本框</span><span class="sxs-lookup"><span data-stu-id="821b0-111">To add a text box</span></span>  
  
1.  <span data-ttu-id="821b0-112">在“设计”视图的 **“插入”** 选项卡上，单击 **“文本框”** 。</span><span class="sxs-lookup"><span data-stu-id="821b0-112">On the **Insert** tab in Design view, click **Text Box**.</span></span>  
  
2.  <span data-ttu-id="821b0-113">在设计图面上，单击并拖动一个框以将其调整到所需文本框大小。</span><span class="sxs-lookup"><span data-stu-id="821b0-113">On the design surface, click and then drag a box to the desired size of the text box.</span></span> <span data-ttu-id="821b0-114">此外，也可以单击设计图面以创建默认大小的文本框。</span><span class="sxs-lookup"><span data-stu-id="821b0-114">Alternatively, click the design surface to create a text box of default size.</span></span>  
  
### <a name="to-add-a-text-box-in-a-list"></a><span data-ttu-id="821b0-115">向列表中添加文本框</span><span class="sxs-lookup"><span data-stu-id="821b0-115">To add a text box in a list</span></span>  
  
1.  <span data-ttu-id="821b0-116">在报表设计视图的 **“插入”** 选项卡上，单击 **“列表”**。</span><span class="sxs-lookup"><span data-stu-id="821b0-116">On the **Insert** tab in report design view, click **List**.</span></span>  
  
2.  <span data-ttu-id="821b0-117">在设计图面上，单击并拖动一个框以将其调整到所需列表大小。</span><span class="sxs-lookup"><span data-stu-id="821b0-117">On the design surface, click and then drag a box to the desired size of the list.</span></span> <span data-ttu-id="821b0-118">此外，也可以单击设计图面来创建默认大小的列表。</span><span class="sxs-lookup"><span data-stu-id="821b0-118">Alternatively, click the design surface to create a list of default size.</span></span>  
  
3.  <span data-ttu-id="821b0-119">在 **“插入”** 选项卡上，单击 **“文本框”**。</span><span class="sxs-lookup"><span data-stu-id="821b0-119">On the **Insert** tab, click **Text Box**.</span></span>  
  
4.  <span data-ttu-id="821b0-120">在设计图面上，在步骤 1 中添加的列表的内部，单击一个框，然后将该框调整为所需文本框大小。</span><span class="sxs-lookup"><span data-stu-id="821b0-120">On the design surface, click and then drag a box to the desired size of the text box inside the list you added in step 1.</span></span> <span data-ttu-id="821b0-121">此外，也可以在设计图面上单击列表内部，以创建默认大小的文本框。</span><span class="sxs-lookup"><span data-stu-id="821b0-121">Alternatively, click the design surface inside the list to create a text box of default size.</span></span>  
  
5.  <span data-ttu-id="821b0-122">若要确认该文本框已正确嵌套到列表内，请选择该文本框。</span><span class="sxs-lookup"><span data-stu-id="821b0-122">To confirm the text box is correctly nested inside the list, select the text box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="821b0-123">如果在文本框中单击并处于编辑模式，请按 ESC 以选择文本框。</span><span class="sxs-lookup"><span data-stu-id="821b0-123">If you click in the text box and are in edit mode, press ESC to select the text box.</span></span>  
  
6.  <span data-ttu-id="821b0-124">在“属性”窗格中，验证 **Parent** 属性是否为自动添加到列表数据区域的矩形。</span><span class="sxs-lookup"><span data-stu-id="821b0-124">In the Properties pane, verify that the **Parent** property is the rectangle that was automatically added to the list data region.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="821b0-125">如果“属性”窗格不可见，请选中“视图”\*\*\*\* 选项卡上的“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="821b0-125">If the Properties pane is not visible, check **Properties** on the **View** tab.</span></span>  
  
### <a name="to-move-a-text-box"></a><span data-ttu-id="821b0-126">移动文本框</span><span class="sxs-lookup"><span data-stu-id="821b0-126">To move a text box</span></span>  
  
1.  <span data-ttu-id="821b0-127">在报表设计视图中，单击文本框内的任意空白区域以选中文本框。</span><span class="sxs-lookup"><span data-stu-id="821b0-127">In report design view, click any empty space within the text box to select the text box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="821b0-128">如果在文本框中单击并处于编辑模式，请按 ESC 以选择文本框。</span><span class="sxs-lookup"><span data-stu-id="821b0-128">If you click in the text box and are in edit mode, press ESC to select the text box.</span></span>  
  
2.  <span data-ttu-id="821b0-129">单击文本框控点，然后将该文本框拖至新位置。</span><span class="sxs-lookup"><span data-stu-id="821b0-129">Click the text box handle and drag the text box to the new location.</span></span> <span data-ttu-id="821b0-130">此外，也可以使用箭头键，水平或垂直移动所选文本框。</span><span class="sxs-lookup"><span data-stu-id="821b0-130">Alternatively, you can use the arrow keys to move a selected text box horizontally or vertically.</span></span> <span data-ttu-id="821b0-131">若要在设计图面上以较小增量移动文本框，请同时按住 Ctrl 键和箭头键。</span><span class="sxs-lookup"><span data-stu-id="821b0-131">To move the text box in smaller increments on the design surface, hold down CTRL plus the arrow keys.</span></span>  
  
### <a name="to-delete-a-text-box"></a><span data-ttu-id="821b0-132">删除文本框</span><span class="sxs-lookup"><span data-stu-id="821b0-132">To delete a text box</span></span>  
  
1.  <span data-ttu-id="821b0-133">在报表设计视图中，右键单击文本框内的任意空白区域以选中该文本框，然后单击“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="821b0-133">In report design view, right-click any empty space within the text box to select it, and then click **Delete**.</span></span> <span data-ttu-id="821b0-134">此外，也可以单击文本框内的任意空白区域，再按 Delete。</span><span class="sxs-lookup"><span data-stu-id="821b0-134">Alternatively, click any empty space within the text box, and then press DELETE.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="821b0-135">如果在文本框中单击并处于编辑模式，请按 ESC 以选择文本框。</span><span class="sxs-lookup"><span data-stu-id="821b0-135">If you click in the text box and are in edit mode, press ESC to select the text box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="821b0-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="821b0-136">See Also</span></span>  
 <span data-ttu-id="821b0-137">[文本框 &#40;报表生成器和 SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="821b0-137">[Text Boxes &#40;Report Builder and SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="821b0-138">[表达式（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="821b0-138">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="821b0-139">键盘快捷键（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="821b0-139">Keyboard Shortcuts &#40;Report Builder&#41;</span></span>](../report-builder/keyboard-shortcuts-report-builder.md)  
  
  
