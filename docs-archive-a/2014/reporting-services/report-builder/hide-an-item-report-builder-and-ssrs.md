---
title: 隐藏项（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.shared.visibility.f1
- "10503"
ms.assetid: 9d78f8de-959b-456f-8947-687fa6e2ba91
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 56e834204698369687528c622cf6167a492766f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580030"
---
# <a name="hide-an-item-report-builder-and-ssrs"></a><span data-ttu-id="23ff4-102">隐藏项（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="23ff4-102">Hide an Item (Report Builder and SSRS)</span></span>
  <span data-ttu-id="23ff4-103">如果希望基于报表参数或指定的某个其他表达式来有条件地隐藏项，则可以设置报表项的可见性。</span><span class="sxs-lookup"><span data-stu-id="23ff4-103">Set the visibility of a report item when you want to conditionally hide an item based on a report parameter or some other expression that you specify.</span></span>

 <span data-ttu-id="23ff4-104">还可以设计报表（如明细报表），使用户通过单击报表中的文本框即可切换报表项的可见性。</span><span class="sxs-lookup"><span data-stu-id="23ff4-104">You can also design a report to allow the user to toggle the visibility of report items based on clicking text boxes in the report, for example, for a drilldown report.</span></span> <span data-ttu-id="23ff4-105">有关详细信息，请参阅 [为项添加展开或折叠操作（报表生成器和 SSRS）](../report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="23ff4-105">For more information, see [Add an Expand or Collapse Action to an Item &#40;Report Builder and SSRS&#41;](../report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md).</span></span>

 <span data-ttu-id="23ff4-106">下面的过程介绍了如何基于常量或表达式，显示或隐藏呈现报表中的报表项。</span><span class="sxs-lookup"><span data-stu-id="23ff4-106">The following procedures describe how to show or hide a report item in a rendered report based on a constant or an expression.</span></span>

> [!NOTE]
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]

### <a name="to-hide-a-report-item"></a><span data-ttu-id="23ff4-107">隐藏报表项</span><span class="sxs-lookup"><span data-stu-id="23ff4-107">To hide a report item</span></span>

1.  <span data-ttu-id="23ff4-108">在报表设计视图中，右键单击相应的报表项并打开其“属性”页\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="23ff4-108">In report design view, right-click the report item and open its **Properties** page.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="23ff4-109">要选择整个表或矩阵数据区域，请在数据区域内单击以将其选定，再右键单击某个行控点、列控点或角控点，然后单击“Tablix 属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="23ff4-109">To select an entire table or matrix data region, click in the data region to select it, right-click a row, column, or corner handle, and then click **Tablix Properties**.</span></span>

2.  <span data-ttu-id="23ff4-110">单击 "**可见性"。**</span><span class="sxs-lookup"><span data-stu-id="23ff4-110">Click **Visibility.**</span></span>

3.  <span data-ttu-id="23ff4-111">在 **“在报表最初运行时”** 中，指定是否要在第一次查看报表时隐藏该项：</span><span class="sxs-lookup"><span data-stu-id="23ff4-111">In **When the report is initially run**, specify whether to hide the item when you first view the report:</span></span>

    -   <span data-ttu-id="23ff4-112">若要显示项，请单击 **“显示”**。</span><span class="sxs-lookup"><span data-stu-id="23ff4-112">To display the item, click **Show**.</span></span>

    -   <span data-ttu-id="23ff4-113">若要隐藏项，请单击 **“隐藏”**。</span><span class="sxs-lookup"><span data-stu-id="23ff4-113">To hide the item, click **Hide**.</span></span>

    -   <span data-ttu-id="23ff4-114">要指定运行时计算的表达式，请单击“基于表达式显示或隐藏”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="23ff4-114">To specify an expression that is evaluated at run-time, click **Show or hide based on an expression**.</span></span> <span data-ttu-id="23ff4-115">键入表达式或单击表达式 (fx) 按钮，以便在“表达式”对话框中创建该表达式\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="23ff4-115">Type the expression or click the expression (**fx**) button to create the expression in the **Expression** dialog box.</span></span>

        > [!NOTE]
        >  <span data-ttu-id="23ff4-116">为可见性指定表达式时，需要设置报表项的 Hidden 属性，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="23ff4-116">When you specify an expression for visibility, you are setting the Hidden property of the report item, as shown in the following image.</span></span> <span data-ttu-id="23ff4-117">当表达式的计算结果值为 False 时，将显示报表项；当该值为 True 时，将隐藏报表项。</span><span class="sxs-lookup"><span data-stu-id="23ff4-117">The evaluated expression shows the report item when the value is False, and hides the report item when the value is True.</span></span> 
        > <span data-ttu-id="23ff4-118">![Properties_Visibility 对话框和 Hidden 属性](../media/hiddenproperty-propertiesvisibility.png "Properties_Visibility 对话框和 Hidden 属性")</span><span class="sxs-lookup"><span data-stu-id="23ff4-118">![Properties_Visibility dialog and Hidden property](../media/hiddenproperty-propertiesvisibility.png "Properties_Visibility dialog and Hidden property")</span></span>

4.  <span data-ttu-id="23ff4-119">单击“确定”两次\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="23ff4-119">Click **OK** twice.</span></span>

### <a name="to-hide-static-rows-in-a-table-matrix-or-list"></a><span data-ttu-id="23ff4-120">隐藏表、矩阵或列表中的静态行</span><span class="sxs-lookup"><span data-stu-id="23ff4-120">To hide static rows in a table, matrix, or list</span></span>

1.  <span data-ttu-id="23ff4-121">在报表设计视图中，单击表、矩阵或列表以显示行控点和列控点。</span><span class="sxs-lookup"><span data-stu-id="23ff4-121">In report design view, click the table, matrix, or list to display the row and column handles.</span></span>

2.  <span data-ttu-id="23ff4-122">右键单击行控点，然后单击“行可见性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="23ff4-122">Right-click the row handle, and then click **Row Visibility**.</span></span> <span data-ttu-id="23ff4-123">将打开 **“行可见性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="23ff4-123">The **Row Visibility** dialog box opens.</span></span>

3.  <span data-ttu-id="23ff4-124">若要设置可见性，请执行第一个过程中的步骤 3 和 4。</span><span class="sxs-lookup"><span data-stu-id="23ff4-124">To set the visibility, follow steps 3 and 4 in the first procedure.</span></span>

### <a name="to-hide-static-columns-in-a-table-matrix-or-list"></a><span data-ttu-id="23ff4-125">隐藏表、矩阵或列表中的静态列</span><span class="sxs-lookup"><span data-stu-id="23ff4-125">To hide static columns in a table, matrix, or list</span></span>

1.  <span data-ttu-id="23ff4-126">在“设计”视图中，选择表、矩阵或列表以显示行控点和列控点。</span><span class="sxs-lookup"><span data-stu-id="23ff4-126">In Design view, select the table, matrix, or list to display the row and column handles.</span></span>

2.  <span data-ttu-id="23ff4-127">右键单击列控点，然后单击“列可见性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="23ff4-127">Right-click the column handle, and then click **Column Visibility**.</span></span>

3.  <span data-ttu-id="23ff4-128">在 **“列可见性”** 对话框中，执行第一个过程中的步骤 3 和 4。</span><span class="sxs-lookup"><span data-stu-id="23ff4-128">In the **Column Visibility** dialog box, follow steps 3 and 4 in the first procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="23ff4-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="23ff4-129">See Also</span></span>
 <span data-ttu-id="23ff4-130">[深化操作 &#40;报表生成器和 ssrs&#41;](../report-design/drilldown-action-report-builder-and-ssrs.md) [向项添加展开或折叠操作 &#40;报表生成器和](../report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)ssrs&#41;[表达式示例 &#40;报表生成器和 ssrs&#41;](../report-design/expression-examples-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="23ff4-130">[Drilldown Action &#40;Report Builder and SSRS&#41;](../report-design/drilldown-action-report-builder-and-ssrs.md) [Add an Expand or Collapse Action to an Item &#40;Report Builder and SSRS&#41;](../report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md) [Expression Examples &#40;Report Builder and SSRS&#41;](../report-design/expression-examples-report-builder-and-ssrs.md)</span></span>


