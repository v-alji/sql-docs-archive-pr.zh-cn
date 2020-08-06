---
title: 添加详细信息组（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ef8efba-6d48-4aeb-a3b9-a02ba5a44614
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 24b1f6af1aaf336a69a0068636ced60c364e556d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586470"
---
# <a name="add-a-details-group-report-builder-and-ssrs"></a><span data-ttu-id="601e6-102">添加详细信息组（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="601e6-102">Add a Details Group (Report Builder and SSRS)</span></span>
  <span data-ttu-id="601e6-103">报表数据集的详细信息数据指定为不包含组表达式的组。</span><span class="sxs-lookup"><span data-stu-id="601e6-103">The detail data from a report dataset is specified as a group with no group expression.</span></span> <span data-ttu-id="601e6-104">要显示矩阵的详细信息数据、重新添加已从表或列表中删除的详细信息数据或添加其他详细信息组时，请向现有 tablix 数据区域添加详细信息组。</span><span class="sxs-lookup"><span data-stu-id="601e6-104">Add a detail group to an existing tablix data region when you want to display the detail data for a matrix, add back detail data that you have deleted from a table or list, or to add additional detail groups.</span></span> <span data-ttu-id="601e6-105">有关组的详细信息，请参阅 [了解组（报表生成器和 SSRS）](understanding-groups-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="601e6-105">For more information about groups, see [Understanding Groups &#40;Report Builder and SSRS&#41;](understanding-groups-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-details-group-to-a-tablix-data-region"></a><span data-ttu-id="601e6-106">向 tablix 数据区域添加详细信息组</span><span class="sxs-lookup"><span data-stu-id="601e6-106">To add a details group to a tablix data region</span></span>  
  
1.  <span data-ttu-id="601e6-107">在设计图面上，单击选定 tablix 数据区域中的任意位置。</span><span class="sxs-lookup"><span data-stu-id="601e6-107">On the design surface, click anywhere in a tablix data region to select it.</span></span> <span data-ttu-id="601e6-108">“分组”窗格将显示选定数据区域的行组和列组。</span><span class="sxs-lookup"><span data-stu-id="601e6-108">The Grouping pane displays the row and column groups for the selected data region.</span></span>  
  
2.  <span data-ttu-id="601e6-109">在“分组”窗格中，右键单击作为最内部的子组的组。</span><span class="sxs-lookup"><span data-stu-id="601e6-109">In the Grouping pane, right-click a group that is an innermost child group.</span></span> <span data-ttu-id="601e6-110">单击 **“添加组”** ，然后单击 **“子组”** 。</span><span class="sxs-lookup"><span data-stu-id="601e6-110">Click **Add Group**, and then click **Child Group**.</span></span> <span data-ttu-id="601e6-111">此时将打开 **“Tablix 组”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="601e6-111">The **Tablix Group** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="601e6-112">在 **“组表达式”** 中，使表达式保留为空白。</span><span class="sxs-lookup"><span data-stu-id="601e6-112">In **Group expression**, leave the expression blank.</span></span> <span data-ttu-id="601e6-113">详细信息组没有任何表达式。</span><span class="sxs-lookup"><span data-stu-id="601e6-113">A details group has no expression.</span></span>  
  
4.  <span data-ttu-id="601e6-114">选择 **“显示详细信息数据”** 。</span><span class="sxs-lookup"><span data-stu-id="601e6-114">Select **Show detail data**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="601e6-115">新的详细信息组作为子组添加到“分组”窗格，在步骤 1 中选择的组的行控点显示详细信息组图标。</span><span class="sxs-lookup"><span data-stu-id="601e6-115">A new details group is added as a child group in the Grouping pane, and the row handle for the group you selected in step 1 displays the details group icon.</span></span> <span data-ttu-id="601e6-116">有关控点的详细信息，请参阅 [Tablix 数据区域单元、行和列（报表生成器和 SSRS）](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="601e6-116">For more information about handles, see [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="601e6-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="601e6-117">See Also</span></span>  
 <span data-ttu-id="601e6-118">[在数据区域中添加或删除组（报表生成器和 SSRS）](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="601e6-118">[Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="601e6-119">[了解组（报表生成器和 SSRS）](understanding-groups-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="601e6-119">[Understanding Groups &#40;Report Builder and SSRS&#41;](understanding-groups-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="601e6-120">[Tablix 数据区域（报表生成器和 SSRS）](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="601e6-120">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="601e6-121">[表 &#40;报表生成器和 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="601e6-121">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="601e6-122">[矩阵 &#40;报表生成器和 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="601e6-122">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="601e6-123">[列出 &#40;报表生成器和 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="601e6-123">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="601e6-124">表、矩阵和列表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="601e6-124">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
