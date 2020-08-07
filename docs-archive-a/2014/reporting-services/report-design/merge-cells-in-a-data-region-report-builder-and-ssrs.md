---
title: 合并数据区域中的单元（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 43551300-89b2-4f4e-af09-69084324afaf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c69ce8182bda3e0b644893e97b69280a003f5732
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691079"
---
# <a name="merge-cells-in-a-data-region-report-builder-and-ssrs"></a><span data-ttu-id="a5e42-102">合并数据区域中的单元（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="a5e42-102">Merge Cells in a Data Region (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a5e42-103">可通过合并数据区域中的单元来合并多个单元、改善数据区域外观或者为列组和行组提供跨越式标签。</span><span class="sxs-lookup"><span data-stu-id="a5e42-103">You can merge cells in a data region to combine cells, improve data region appearance, or provide spanning labels for column groups and row groups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a5e42-104">只能合并数据区域中同一个区内的单元，这些区包括：角部、列标题、组定义（或行标题）和正文。</span><span class="sxs-lookup"><span data-stu-id="a5e42-104">Cells can only be merged within each area of a data region: corner, column headers, group definition (or row headers), and body.</span></span> <span data-ttu-id="a5e42-105">不能合并跨区边界的单元。</span><span class="sxs-lookup"><span data-stu-id="a5e42-105">You cannot merge cells that cross area boundaries.</span></span> <span data-ttu-id="a5e42-106">例如，不能将数据区域角部区中的单元与行组区中的单元合并在一起。</span><span class="sxs-lookup"><span data-stu-id="a5e42-106">For example, you cannot merge a cell in the data region corner area with a cell in the row group area.</span></span> <span data-ttu-id="a5e42-107">有关 tablix 区域的详细信息，请参阅[列出 &#40;报表生成器和 SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="a5e42-107">For more information about tablix areas, see [Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-merge-cells-in-a-data-region"></a><span data-ttu-id="a5e42-108">合并数据区域中的单元</span><span class="sxs-lookup"><span data-stu-id="a5e42-108">To merge cells in a data region</span></span>  
  
1.  <span data-ttu-id="a5e42-109">在报表设计图面的数据区域中，单击第一个要合并的单元。</span><span class="sxs-lookup"><span data-stu-id="a5e42-109">In the data region on the report design surface, click the first cell to merge.</span></span> <span data-ttu-id="a5e42-110">按住鼠标左键，垂直或水平拖动以选择相邻单元。</span><span class="sxs-lookup"><span data-stu-id="a5e42-110">Holding the left mouse button down, drag vertically or horizontally to select adjacent cells.</span></span> <span data-ttu-id="a5e42-111">所选单元会突出显示。</span><span class="sxs-lookup"><span data-stu-id="a5e42-111">The selected cells are highlighted.</span></span>  
  
2.  <span data-ttu-id="a5e42-112">右键单击所选单元并选择“合并单元”  。</span><span class="sxs-lookup"><span data-stu-id="a5e42-112">Right-click the selected cells and select **Merge Cells**.</span></span> <span data-ttu-id="a5e42-113">所选单元将合并为一个单元。</span><span class="sxs-lookup"><span data-stu-id="a5e42-113">The selected cells are combined into a single cell.</span></span>  
  
3.  <span data-ttu-id="a5e42-114">重复步骤 1 和 2 可合并数据区域中的其他相邻单元。</span><span class="sxs-lookup"><span data-stu-id="a5e42-114">Repeat steps 1 and 2 to merge other adjacent cells in a data region.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5e42-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a5e42-115">See Also</span></span>  
 <span data-ttu-id="a5e42-116">[Tablix 数据区域 &#40;报表生成器和 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a5e42-116">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a5e42-117">[表（报表生成器和 SSRS）](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a5e42-117">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a5e42-118">[矩阵 &#40;报表生成器和 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a5e42-118">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a5e42-119">[列出 &#40;报表生成器和 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a5e42-119">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a5e42-120">列表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="a5e42-120">Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
