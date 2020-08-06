---
title: 插入或删除行（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b9642af3-b3ae-4f78-b0be-8f96b79fc313
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fdec24801d1fae3b95c7d75acb5a3add650d523b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692710"
---
# <a name="insert-or-delete-a-row-report-builder-and-ssrs"></a><span data-ttu-id="4c19e-102">插入或删除行（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4c19e-102">Insert or Delete a Row (Report Builder and SSRS)</span></span>
  <span data-ttu-id="4c19e-103">可以在 Tablix 数据区域中添加或删除行。</span><span class="sxs-lookup"><span data-stu-id="4c19e-103">You can add or delete rows in a tablix data region.</span></span> <span data-ttu-id="4c19e-104">Tablix 数据区域可以是一个表、矩阵或列表。</span><span class="sxs-lookup"><span data-stu-id="4c19e-104">The tablix data region can be a table, a matrix, or a list.</span></span> <span data-ttu-id="4c19e-105">下面的过程不适用于图表和仪表数据区域。</span><span class="sxs-lookup"><span data-stu-id="4c19e-105">The following procedures do not apply to the chart and gauge data regions.</span></span>  
  
 <span data-ttu-id="4c19e-106">在 Tablix 数据区域中，您可以在组内添加与组相关联的行或在组外添加与组不相关联的行。</span><span class="sxs-lookup"><span data-stu-id="4c19e-106">In a tablix data region, you can add rows that are associated with a group (inside a group) or that are not associated with a group (outside a group).</span></span> <span data-ttu-id="4c19e-107">位于组内的行对于每个唯一组值只重复一次。</span><span class="sxs-lookup"><span data-stu-id="4c19e-107">A row that is inside a group repeats once per unique group value.</span></span> <span data-ttu-id="4c19e-108">例如，如果某个组基于包含颜色名称的数据列中的值，则该组中的行对于不同的颜色名称只重复一次。</span><span class="sxs-lookup"><span data-stu-id="4c19e-108">For example, a row inside a group based on the value in a data column that contains color names, repeats once per distinct color name.</span></span> <span data-ttu-id="4c19e-109">对于嵌套组，行可以位于子组的外部，但需要位于父组的内部。</span><span class="sxs-lookup"><span data-stu-id="4c19e-109">For nested groups, a row can be outside the child group but inside the parent group.</span></span> <span data-ttu-id="4c19e-110">在这种情况下，行针对父组中的每个唯一值只重复一次。</span><span class="sxs-lookup"><span data-stu-id="4c19e-110">In this case, the row repeats once for each unique value in the parent group.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-select-a-data-region-so-the-row-and-column-handles-appear"></a><span data-ttu-id="4c19e-111">选择数据区域，以显示行控点和列控点</span><span class="sxs-lookup"><span data-stu-id="4c19e-111">To select a data region so the row and column handles appear</span></span>  
  
-   <span data-ttu-id="4c19e-112">在“设计”视图中，单击 Tablix 数据区域的左上角，以使数据区域的上方和侧面显示列控点和行控点。</span><span class="sxs-lookup"><span data-stu-id="4c19e-112">In Design view, click the upper left corner of the tablix data region so that column and row handles appear above and next to it.</span></span>  
  
     <span data-ttu-id="4c19e-113">有关数据区域区域的详细信息，请参阅[列出 &#40;报表生成器和 SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="4c19e-113">For more information about data region areas, see [Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md).</span></span>  
  
### <a name="to-insert-a-row-in-a-selected-data-region"></a><span data-ttu-id="4c19e-114">在所选数据区域中插入行</span><span class="sxs-lookup"><span data-stu-id="4c19e-114">To insert a row in a selected data region</span></span>  
  
-   <span data-ttu-id="4c19e-115">右键单击要插入行的位置对应的行控点，再单击“插入行”，然后单击“上方”或“下方”    。</span><span class="sxs-lookup"><span data-stu-id="4c19e-115">Right-click a row handle where you want to insert a row, click **Insert Row**, and then click **Above** or **Below**.</span></span>  
  
     <span data-ttu-id="4c19e-116">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="4c19e-116">\- or -</span></span>  
  
-   <span data-ttu-id="4c19e-117">右键单击要插入行的数据区域中的单元，再单击“插入行”，然后单击“上方”或“下方”    。</span><span class="sxs-lookup"><span data-stu-id="4c19e-117">Right-click a cell in the data region where you want to insert a row, click **Insert Row**, and then click **Above** or **Below**.</span></span>  
  
### <a name="to-delete-a-row-from-a-selected-data-region"></a><span data-ttu-id="4c19e-118">删除所选数据区域中的行</span><span class="sxs-lookup"><span data-stu-id="4c19e-118">To delete a row from a selected data region</span></span>  
  
-   <span data-ttu-id="4c19e-119">选择要删除的行，右键单击任一所选行的控点，然后单击“删除行”  。</span><span class="sxs-lookup"><span data-stu-id="4c19e-119">Select the row or rows that you want to delete, right-click the handle for one of the rows you selected, and then click **Delete Rows**.</span></span>  
  
     <span data-ttu-id="4c19e-120">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="4c19e-120">\- or -</span></span>  
  
-   <span data-ttu-id="4c19e-121">右键单击要删除的行所在的数据区域中的单元，然后单击“删除行”  。</span><span class="sxs-lookup"><span data-stu-id="4c19e-121">Right-click a cell in the data region where you want to delete a row, and then click **Delete Rows**.</span></span>  
  
### <a name="to-insert-a-row-in-a-group-in-a-selected-data-region"></a><span data-ttu-id="4c19e-122">在所选数据区域的组中插入行</span><span class="sxs-lookup"><span data-stu-id="4c19e-122">To insert a row in a group in a selected data region</span></span>  
  
-   <span data-ttu-id="4c19e-123">在要插入行的 Tablix 数据区域的行组区中，右键单击插入位置的行组单元，再单击“插入行”，然后单击“上方 – 组外部”、“上方 – 组内部”、“下方 – 组内部”或“下方 – 组外部”      。</span><span class="sxs-lookup"><span data-stu-id="4c19e-123">Right-click a row group cell in the row group area of a tablix data region where you want to insert a row, click **Insert Row**, and then click **Above - Outside Group**, **Above - Inside Group**, **Below - Inside Group**, or **Below - Outside Group**.</span></span>  
  
     <span data-ttu-id="4c19e-124">此时将在您单击过的行组单元所表示的组的内部或外部添加一行。</span><span class="sxs-lookup"><span data-stu-id="4c19e-124">A row is added either inside or outside the group represented by the row group cell you clicked on.</span></span>  
  
### <a name="to-delete-a-row-from-a-group-in-a-selected-data-region"></a><span data-ttu-id="4c19e-125">删除所选数据区域的组中的行</span><span class="sxs-lookup"><span data-stu-id="4c19e-125">To delete a row from a group in a selected data region</span></span>  
  
-   <span data-ttu-id="4c19e-126">右键单击要删除的行所在的 Tablix 数据区域的行组区中的行组单元，然后单击“删除行”  。</span><span class="sxs-lookup"><span data-stu-id="4c19e-126">Right-click a row group cell in the row group area of a tablix data region where you want to delete a row, and then click **Delete Rows**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c19e-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4c19e-127">See Also</span></span>  
 <span data-ttu-id="4c19e-128">[Tablix 数据区域（报表生成器和 SSRS）](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4c19e-128">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4c19e-129">[了解组（报表生成器和 SSRS）](understanding-groups-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4c19e-129">[Understanding Groups &#40;Report Builder and SSRS&#41;](understanding-groups-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4c19e-130">[表（报表生成器和 SSRS）](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4c19e-130">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4c19e-131">[矩阵（报表生成器和 SSRS）](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4c19e-131">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4c19e-132">[列表（报表生成器和 SSRS）](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4c19e-132">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="4c19e-133">列表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4c19e-133">Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
