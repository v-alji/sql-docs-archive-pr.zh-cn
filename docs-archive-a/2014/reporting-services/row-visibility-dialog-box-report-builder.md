---
title: "\"行可见性\" 对话框 (报表生成器) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10126"
ms.assetid: 117fb20c-2fda-437e-bcc5-9010d6d4b53b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 748cf1612f04e02a90a5d8579b56d3856dea0388
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579473"
---
# <a name="row-visibility-dialog-box-report-builder"></a><span data-ttu-id="1991d-102">“行可见性”对话框（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="1991d-102">Row Visibility Dialog Box (Report Builder)</span></span>
  <span data-ttu-id="1991d-103">在报表首次运行时可使用 **“行可见性”** 对话框来显示或隐藏选中的行，其他时候可通过此对话框使用另一报表项来切换该行的可见性。</span><span class="sxs-lookup"><span data-stu-id="1991d-103">Use the **Row Visibility** dialog box to show or hide the selected row when the report is first run or to use another report item to toggle the visibility of the row.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1991d-104">选项</span><span class="sxs-lookup"><span data-stu-id="1991d-104">Options</span></span>  
 <span data-ttu-id="1991d-105">**在报表最初运行时**</span><span class="sxs-lookup"><span data-stu-id="1991d-105">**When the report is initially run**</span></span>  
 <span data-ttu-id="1991d-106">选择一个选项以指示行在报表中的初始显示方式。</span><span class="sxs-lookup"><span data-stu-id="1991d-106">Select an option to indicate how the row is initially displayed in the report.</span></span>  
  
 <span data-ttu-id="1991d-107">**显示**</span><span class="sxs-lookup"><span data-stu-id="1991d-107">**Show**</span></span>  
 <span data-ttu-id="1991d-108">选择此选项以显示该行。</span><span class="sxs-lookup"><span data-stu-id="1991d-108">Select this option to show the row.</span></span>  
  
 <span data-ttu-id="1991d-109">**Hide**</span><span class="sxs-lookup"><span data-stu-id="1991d-109">**Hide**</span></span>  
 <span data-ttu-id="1991d-110">选择此选项以隐藏该行。</span><span class="sxs-lookup"><span data-stu-id="1991d-110">Select this option to hide the row.</span></span>  
  
 <span data-ttu-id="1991d-111">**基于表达式显示或隐藏**</span><span class="sxs-lookup"><span data-stu-id="1991d-111">**Show or hide based on an expression**</span></span>  
 <span data-ttu-id="1991d-112">选择此选项可以利用表达式来使初始可见性具有可变性。</span><span class="sxs-lookup"><span data-stu-id="1991d-112">Select this option to vary the initial visibility using an expression.</span></span>  
  
 <span data-ttu-id="1991d-113">键入计算结果为 `Boolean` 值的表达式，值为 `True` 时表示隐藏该项，值为 `False` 时表示显示该项。</span><span class="sxs-lookup"><span data-stu-id="1991d-113">Type an expression that evaluates to a `Boolean` value of `True` to hide the item and `False` to show the item.</span></span> <span data-ttu-id="1991d-114">单击“表达式”\*\*\*\* (*fx*) 按钮可编辑表达式。</span><span class="sxs-lookup"><span data-stu-id="1991d-114">Click the **Expression** (*fx*) button to edit the expression.</span></span>  
  
 <span data-ttu-id="1991d-115">**可以通过此报表项切换显示**</span><span class="sxs-lookup"><span data-stu-id="1991d-115">**Display can be toggled by this report item**</span></span>  
 <span data-ttu-id="1991d-116">选择此选项可以显示一个切换图像，用户可以使用该图像在 HTML 报表查看器中显示或隐藏此行。</span><span class="sxs-lookup"><span data-stu-id="1991d-116">Choose this option to display a toggle image that enables the user to show or hide this row in an HTML report viewer.</span></span>  
  
 <span data-ttu-id="1991d-117">您需要键入或选择报表中要用来显示切换图像的文本框的名称；例如，Textbox1。</span><span class="sxs-lookup"><span data-stu-id="1991d-117">Type or select the name of a text box in the report in which to display a toggle image; for example, Textbox1.</span></span> <span data-ttu-id="1991d-118">所选择的文本框必须在此报表项的当前或包含作用域中。</span><span class="sxs-lookup"><span data-stu-id="1991d-118">The text box that you choose must be in the current or containing scope for this report item.</span></span> <span data-ttu-id="1991d-119">例如，若要切换与子组关联的行的可见性，请在与父组关联的行中选择一个文本框。</span><span class="sxs-lookup"><span data-stu-id="1991d-119">For example, to toggle visibility of rows associated with a child group, select a text box in a row associated with the parent group.</span></span> <span data-ttu-id="1991d-120">若要切换图表的可见性，请选择一个与该图表位于同一包含作用域中的文本框；例如，表体或矩形。</span><span class="sxs-lookup"><span data-stu-id="1991d-120">To toggle visibility of a chart, select a text box that is in the same containing scope as the chart; for example, the report body or a rectangle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1991d-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1991d-121">See Also</span></span>  
 <span data-ttu-id="1991d-122">[表达式示例（报表生成器和 SSRS）](report-design/expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1991d-122">[Expression Examples &#40;Report Builder and SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1991d-123">[向项 &#40;报表生成器和 SSRS 添加展开或折叠操作&#41;](report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1991d-123">[Add an Expand or Collapse Action to an Item &#40;Report Builder and SSRS&#41;](report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1991d-124">[映像 &#40;报表生成器和 SSRS&#41;](report-design/images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1991d-124">[Images &#40;Report Builder and SSRS&#41;](report-design/images-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1991d-125">[报表生成器对话框、窗格和向导的帮助](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="1991d-125">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 [<span data-ttu-id="1991d-126">“图像属性”对话框 ->“常规”（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="1991d-126">Image Properties Dialog Box, General &#40;Report Builder and SSRS&#41;</span></span>](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
