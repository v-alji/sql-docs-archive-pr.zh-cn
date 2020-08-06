---
title: 更改报表参数的顺序（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: abd61e19-dba3-423c-a26c-e8bc43197d3f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ad9dd25be7a87fee089a48849fcc716e682e4c64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692257"
---
# <a name="change-the-order-of-a-report-parameter-report-builder-and-ssrs"></a><span data-ttu-id="4f631-102">更改报表参数的顺序（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4f631-102">Change the Order of a Report Parameter (Report Builder and SSRS)</span></span>
  <span data-ttu-id="4f631-103">当依赖参数位于它所依赖的参数之前时，需要更改报表参数的顺序。</span><span class="sxs-lookup"><span data-stu-id="4f631-103">Change the order of report parameters when you have a dependent parameter that is listed before the parameter it is dependent on.</span></span> <span data-ttu-id="4f631-104">当您有级联参数或希望在用户选择其他参数值之前向他们显示参数的默认值时，参数顺序非常重要。</span><span class="sxs-lookup"><span data-stu-id="4f631-104">Parameter order is important when you have cascading parameters, or when you want to show users the default value for one parameter before they choose values for other parameters.</span></span> <span data-ttu-id="4f631-105">依赖报表参数在其默认值查询或有效值查询中包含对一个查询参数的引用，该查询参数指向“报表数据”窗格的参数列表中该依赖报表参数之后的报表参数。</span><span class="sxs-lookup"><span data-stu-id="4f631-105">A dependent report parameter contains a reference, in either its default values query or valid values query, to a query parameter that points to a report parameter that is after it in the parameter list in the Report Data pane.</span></span>  
  
 <span data-ttu-id="4f631-106">您所看到的报表查看器工具栏上显示参数的顺序由“报表数据”窗格中参数的顺序决定。</span><span class="sxs-lookup"><span data-stu-id="4f631-106">The order that you see parameters display on the report viewer toolbar is determined by the order of the parameters in the Report Data pane.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-order-of-report-parameters"></a><span data-ttu-id="4f631-107">更改报表参数的顺序</span><span class="sxs-lookup"><span data-stu-id="4f631-107">To change the order of report parameters</span></span>  
  
1.  <span data-ttu-id="4f631-108">在“报表数据”窗格中，展开“参数”节点。</span><span class="sxs-lookup"><span data-stu-id="4f631-108">In the Report Data pane, expand the Parameters node.</span></span>  
  
2.  <span data-ttu-id="4f631-109">单击参数，然后使用“报表数据”窗格工具栏上的向上和向下箭头按钮在列表中上下移动该参数。</span><span class="sxs-lookup"><span data-stu-id="4f631-109">Click a parameter and use the up and down arrow buttons on the Report Data pane toolbar to move the parameter higher or lower in the list.</span></span> <span data-ttu-id="4f631-110">下图显示报表生成器中的“报表数据”窗格。</span><span class="sxs-lookup"><span data-stu-id="4f631-110">The following image shows the Report Data pane in Report Builder.</span></span>  
  
     <span data-ttu-id="4f631-111">![“报表数据”窗格](../media/reportdatapane.png "“报表数据”窗格")</span><span class="sxs-lookup"><span data-stu-id="4f631-111">![Report Data Pane](../media/reportdatapane.png "Report Data Pane")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f631-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4f631-112">See Also</span></span>  
 <span data-ttu-id="4f631-113">[报表参数 &#40;报表生成器和报表设计器&#41;](report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="4f631-113">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="4f631-114">[报表生成器对话框、窗格和向导的帮助](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="4f631-114">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="4f631-115">[向报表添加级联参数 &#40;报表生成器和 SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4f631-115">[Add Cascading Parameters to a Report &#40;Report Builder and SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4f631-116">[教程：向报表添加参数 &#40;报表生成器&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="4f631-116">[Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span></span>  
 <span data-ttu-id="4f631-117">[添加数据集筛选器、数据区域筛选器和组筛选器 &#40;报表生成器和 SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="4f631-117">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 [<span data-ttu-id="4f631-118">Parameters 集合引用（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4f631-118">Parameters Collection References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-parameters-collection-references-report-builder.md)  
  
  
