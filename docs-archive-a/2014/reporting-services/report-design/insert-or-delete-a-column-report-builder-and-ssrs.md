---
title: 插入或删除列（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e9db79e2-7e7d-4359-a706-cb746c94182a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9a6f782dbb6cc1024583926aafe4bab1cfe2d042
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692713"
---
# <a name="insert-or-delete-a-column-report-builder-and-ssrs"></a><span data-ttu-id="45e3c-102">插入或删除列（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="45e3c-102">Insert or Delete a Column (Report Builder and SSRS)</span></span>
  <span data-ttu-id="45e3c-103">可以在 Tablix 数据区域中添加或删除列。</span><span class="sxs-lookup"><span data-stu-id="45e3c-103">You can add or delete columns in a tablix data region.</span></span> <span data-ttu-id="45e3c-104">Tablix 数据区域可以是一个表、矩阵或列表。</span><span class="sxs-lookup"><span data-stu-id="45e3c-104">The tablix data region can be a table, a matrix, or a list.</span></span> <span data-ttu-id="45e3c-105">下面的过程不适用于图表和仪表数据区域。</span><span class="sxs-lookup"><span data-stu-id="45e3c-105">The following procedures do not apply to the chart and gauge data regions.</span></span>  
  
 <span data-ttu-id="45e3c-106">在 Tablix 数据区域中，您可以在组内添加与组相关联的列或在组外添加与组不相关联的列。</span><span class="sxs-lookup"><span data-stu-id="45e3c-106">In a tablix data region, you can add columns that are associated with a group (inside a group) or that are not associated with a group (outside a group).</span></span> <span data-ttu-id="45e3c-107">位于组内的列对于每个唯一组值只重复一次。</span><span class="sxs-lookup"><span data-stu-id="45e3c-107">A column that is inside a group repeats once per unique group value.</span></span> <span data-ttu-id="45e3c-108">例如，如果某个组基于包含颜色名称的数据列中的值，则该组中的列对于不同的颜色名称只重复一次。</span><span class="sxs-lookup"><span data-stu-id="45e3c-108">For example, a column inside a group based the value in a data column that contains color names, repeats once per distinct color name.</span></span> <span data-ttu-id="45e3c-109">对于嵌套组，列可以位于子组的外部，但需要位于父组的内部。</span><span class="sxs-lookup"><span data-stu-id="45e3c-109">For nested groups, a column can be outside the child group but inside the parent group.</span></span> <span data-ttu-id="45e3c-110">在这种情况下，行针对父组中的每个唯一值只重复一次。</span><span class="sxs-lookup"><span data-stu-id="45e3c-110">In this case, the row repeats once for each unique value in the parent group.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-select-a-data-region-so-that-the-row-and-column-handles-appear"></a><span data-ttu-id="45e3c-111">选择数据区域，以显示行控点和列控点</span><span class="sxs-lookup"><span data-stu-id="45e3c-111">To select a data region so that the row and column handles appear</span></span>  
  
-   <span data-ttu-id="45e3c-112">在“设计”视图中，单击 Tablix 数据区域的左上角，以使数据区域的上方和旁边显示列控点和行控点。</span><span class="sxs-lookup"><span data-stu-id="45e3c-112">In Design view, click the upper left corner of the tablix data region, so that column and row handles appear above and next to it.</span></span>  
  
     <span data-ttu-id="45e3c-113">有关数据区域区域的详细信息，请参阅[列出 &#40;报表生成器和 SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="45e3c-113">For more information about data region areas, see [Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md).</span></span>  
  
### <a name="to-insert-a-column-in-a-selected-data-region"></a><span data-ttu-id="45e3c-114">在所选数据区域中插入列</span><span class="sxs-lookup"><span data-stu-id="45e3c-114">To insert a column in a selected data region</span></span>  
  
-   <span data-ttu-id="45e3c-115">右键单击要插入列的位置对应的列图柄，再单击“插入列”  ，然后单击“左侧”  或“右侧”  。</span><span class="sxs-lookup"><span data-stu-id="45e3c-115">Right-click a column handle where you want to insert a column, click **Insert Column**, and then click **Left** or **Right**.</span></span>  
  
     <span data-ttu-id="45e3c-116">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="45e3c-116">-- or --</span></span>  
  
-   <span data-ttu-id="45e3c-117">右键单击要插入行的数据区域中的单元，再单击“插入列”  ，然后单击“左侧”  或“右侧”  。</span><span class="sxs-lookup"><span data-stu-id="45e3c-117">Right-click a cell in the data region where you want to insert a row, click **Insert Column**, and then click **Left** or **Right**.</span></span>  
  
### <a name="to-delete-a-column-from-a-selected-data-region"></a><span data-ttu-id="45e3c-118">删除所选数据区域中的列</span><span class="sxs-lookup"><span data-stu-id="45e3c-118">To delete a column from a selected data region</span></span>  
  
-   <span data-ttu-id="45e3c-119">选择要删除的列，右键单击任一所选列的图柄，然后单击“删除列”  。</span><span class="sxs-lookup"><span data-stu-id="45e3c-119">Select the column or columns that you want to delete, right-click the handle for one of the columns you selected, and then click **Delete Columns**.</span></span>  
  
     <span data-ttu-id="45e3c-120">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="45e3c-120">-- or --</span></span>  
  
-   <span data-ttu-id="45e3c-121">右键单击要删除的列所在的数据区域中的单元，然后单击“删除列”  。</span><span class="sxs-lookup"><span data-stu-id="45e3c-121">Right-click a cell in the data region where you want to delete a column, and then click **Delete Columns**.</span></span>  
  
### <a name="to-insert-a-column-in-a-group-in-a-selected-data-region"></a><span data-ttu-id="45e3c-122">在所选数据区域的组中插入列</span><span class="sxs-lookup"><span data-stu-id="45e3c-122">To insert a column in a group in a selected data region</span></span>  
  
-   <span data-ttu-id="45e3c-123">在要插入列的 Tablix 数据区域的列组区域中，右键单击插入位置的列组单元，再单击“插入列”  ，然后单击“左侧 - 组外部”  、“左侧 - 组内部”  、“右侧 - 组内部”  或“右侧 - 组外部”  。</span><span class="sxs-lookup"><span data-stu-id="45e3c-123">Right-click a column group cell in the column group area of a tablix data region where you want to insert a column, click **Insert Column**, and then click **Left - Outside Group**, **Left - Inside Group**, **Right - Inside Group**, or **Right - Outside Group**.</span></span>  
  
     <span data-ttu-id="45e3c-124">此时将在您单击过的列组单元所表示的组的内部或外部添加一列。</span><span class="sxs-lookup"><span data-stu-id="45e3c-124">A column is added either inside or outside the group represented by the column group cell you clicked on.</span></span>  
  
### <a name="to-delete-a-column-from-a-group-in-a-selected-data-region"></a><span data-ttu-id="45e3c-125">删除所选数据区域的组中的列</span><span class="sxs-lookup"><span data-stu-id="45e3c-125">To delete a column from a group in a selected data region</span></span>  
  
-   <span data-ttu-id="45e3c-126">右键单击要删除的列所在的 Tablix 数据区域的列组区域中的列组单元，然后单击“删除列”  。</span><span class="sxs-lookup"><span data-stu-id="45e3c-126">Right-click a column group cell in the column group area of a tablix data region where you want to delete a column, and then click **Delete Columns**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45e3c-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="45e3c-127">See Also</span></span>  
 <span data-ttu-id="45e3c-128">[了解组（报表生成器和 SSRS）](understanding-groups-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="45e3c-128">[Understanding Groups &#40;Report Builder and SSRS&#41;](understanding-groups-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="45e3c-129">[Tablix 数据区域（报表生成器和 SSRS）](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="45e3c-129">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="45e3c-130">[表（报表生成器和 SSRS）](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="45e3c-130">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="45e3c-131">[矩阵（报表生成器和 SSRS）](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="45e3c-131">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="45e3c-132">[列表（报表生成器和 SSRS）](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="45e3c-132">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="45e3c-133">列表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="45e3c-133">Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
