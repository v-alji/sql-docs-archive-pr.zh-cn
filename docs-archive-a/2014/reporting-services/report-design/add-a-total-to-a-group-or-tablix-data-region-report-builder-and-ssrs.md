---
title: 向组或 Tablix 数据区域添加总计（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: cf1b96c3-7f0f-4c94-ad08-5239c77ccfe4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f626621a37a327ae32664ab9444e72ce4931ac0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577283"
---
# <a name="add-a-total-to-a-group-or-tablix-data-region-report-builder-and-ssrs"></a><span data-ttu-id="9da51-102">向组或 Tablix 数据区域添加总计（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="9da51-102">Add a Total to a Group or Tablix Data Region (Report Builder and SSRS)</span></span>
  <span data-ttu-id="9da51-103">可以在 Tablix 数据区域中为组或整个数据区域添加总计。</span><span class="sxs-lookup"><span data-stu-id="9da51-103">You can add totals in a tablix data region for a group or for the entire data region.</span></span> <span data-ttu-id="9da51-104">默认情况下，总计是在应用筛选器之后组或数据区域中的非 Null 数值数据之和。</span><span class="sxs-lookup"><span data-stu-id="9da51-104">By default, a total is the sum of the numeric, non-null data in a group or in the data region, after filters are applied.</span></span> <span data-ttu-id="9da51-105">若要为组添加总计，请在“分组”窗格中单击组快捷菜单上的 **“添加总计”** 。</span><span class="sxs-lookup"><span data-stu-id="9da51-105">To add totals for a group, click **Add Total** on the shortcut menu for the group in the Grouping pane.</span></span> <span data-ttu-id="9da51-106">若要为 Tablix 正文区中的各个单元添加总计，请单击单元快捷菜单上的 **“添加总计”** 。</span><span class="sxs-lookup"><span data-stu-id="9da51-106">To add totals for an individual cell in the tablix body area, click **Add Total** on the shortcut menu for the cell.</span></span> <span data-ttu-id="9da51-107">“添加总计”命令与上下文相关，并且仅支持数字字段\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9da51-107">The **Add Total** command is context-sensitive and enabled only for numeric fields.</span></span> <span data-ttu-id="9da51-108">根据选择的 Tablix 单元，您可以通过选择 Tablix 正文区中的单元为一个单元添加总计，也可以通过选择 Tablix 行组区或 Tablix 列组区中的单元为整个组添加总计。</span><span class="sxs-lookup"><span data-stu-id="9da51-108">Depending on the tablix cell that you select, you can add a total for a single cell by selecting a cell in the tablix body area or for the entire group by selecting a cell in the tablix row group area or the tablix column group area.</span></span> <span data-ttu-id="9da51-109">有关 Tablix 区域的详细信息，请参阅 [Tablix 数据区域（报表生成器和 SSRS）](../tablix-data-region-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="9da51-109">For more information about tablix areas, see [Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="9da51-110">添加总计之后，可以将默认函数 Sum 更改为内置报表函数列表中的不同聚合函数。</span><span class="sxs-lookup"><span data-stu-id="9da51-110">After you add a total, you can change the default function Sum to a different aggregate function from the list of built-in report functions.</span></span> <span data-ttu-id="9da51-111">有关详细信息，请参阅[聚合函数引用 &#40;报表生成器和 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)。[!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9da51-111">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).[!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]</span></span>  
  
### <a name="to-add-a-total-for-an-individual-value-in-the-tablix-body-area"></a><span data-ttu-id="9da51-112">为 Tablix 正文区中的单个值添加总计</span><span class="sxs-lookup"><span data-stu-id="9da51-112">To add a total for an individual value in the tablix body area</span></span>  
  
-   <span data-ttu-id="9da51-113">在 Tablix 数据区域正文区中，右键单击要在其中添加总计的单元。</span><span class="sxs-lookup"><span data-stu-id="9da51-113">In the tablix data region body area, right-click the cell where you want to add the total.</span></span> <span data-ttu-id="9da51-114">该单元必须包含数字字段。</span><span class="sxs-lookup"><span data-stu-id="9da51-114">The cell must contain a numeric field.</span></span> <span data-ttu-id="9da51-115">指向 **“添加总计”**，然后单击 **“行”** 或 **“列”**。</span><span class="sxs-lookup"><span data-stu-id="9da51-115">Point to **Add Total**, and then click **Row** or **Column**.</span></span>  
  
     <span data-ttu-id="9da51-116">将在数据区域的当前组之外添加一个新行或列，以及已单击单元中的字段的默认总计。</span><span class="sxs-lookup"><span data-stu-id="9da51-116">A new row or column outside the current group is added to the data region, with a default total for the field in the cell you clicked.</span></span>  
  
     <span data-ttu-id="9da51-117">如果 Tablix 数据区域是一个表，则自动添加一行。</span><span class="sxs-lookup"><span data-stu-id="9da51-117">If the tablix data region is a table, a row is automatically added.</span></span>  
  
### <a name="to-add-totals-for-a-row-group"></a><span data-ttu-id="9da51-118">添加行组的总计</span><span class="sxs-lookup"><span data-stu-id="9da51-118">To add totals for a row group</span></span>  
  
-   <span data-ttu-id="9da51-119">在 Tablix 数据区域行组区中，右键单击要汇总的行组区中的单元，指向“添加总计”，然后单击“之前”或“之后”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9da51-119">In the tablix data region row group area, right-click a cell in the row group area for which you want totals, point to **Add Total**, and then click **Before** or **After**.</span></span>  
  
     <span data-ttu-id="9da51-120">将在数据区域的当前组之外添加一个新行，然后在该行中为每个数字字段添加默认总计。</span><span class="sxs-lookup"><span data-stu-id="9da51-120">A new row outside the current group is added to the data region, and then a default total is added for each numeric field in the row.</span></span>  
  
### <a name="to-add-totals-for-a-column-group"></a><span data-ttu-id="9da51-121">添加列组的总计</span><span class="sxs-lookup"><span data-stu-id="9da51-121">To add totals for a column group</span></span>  
  
-   <span data-ttu-id="9da51-122">在 Tablix 数据区域行组区中，右键单击要汇总的列组区中的单元，然后指向“添加总计”，并单击“之前”或“之后”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9da51-122">In the tablix data region row group area, right-click a cell in the column group area for which you want totals, then point to **Add Total**, and click **Before** or **After**.</span></span>  
  
     <span data-ttu-id="9da51-123">将在数据区域的当前组之外添加一个新列，然后在该列中为每个数字字段添加默认总计。</span><span class="sxs-lookup"><span data-stu-id="9da51-123">A new column outside the current group is added to the data region, and then a default total is added for each numeric field in the column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9da51-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9da51-124">See Also</span></span>  
 <span data-ttu-id="9da51-125">[总计、聚合和内置集合的表达式作用域 &#40;报表生成器和 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md) </span><span class="sxs-lookup"><span data-stu-id="9da51-125">[Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md) </span></span>  
 <span data-ttu-id="9da51-126">[Tablix 数据区域 &#40;报表生成器和 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9da51-126">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9da51-127">[表 &#40;报表生成器和 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9da51-127">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9da51-128">[矩阵 &#40;报表生成器和 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9da51-128">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9da51-129">[列出 &#40;报表生成器和 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9da51-129">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="9da51-130">表、矩阵和列表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="9da51-130">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
