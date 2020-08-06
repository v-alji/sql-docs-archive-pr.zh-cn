---
title: 向图表添加空点 (报表生成器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2b056119-439f-494f-83cf-ee0c05dc6487
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 53d891c58210bcd51cd4e49f2f9a691a7729c884
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692266"
---
# <a name="add-empty-points-to-the-chart-report-builder-and-ssrs"></a><span data-ttu-id="56c86-102">向图表添加空点（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="56c86-102">Add Empty Points to the Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="56c86-103">Null 值在图表中显示为空格或显示为序列中数据点间的空白。</span><span class="sxs-lookup"><span data-stu-id="56c86-103">Null values are shown on the chart as empty spaces or gaps between data points in a series.</span></span> <span data-ttu-id="56c86-104">空点是可在由 Null 值创建的空格中插入的数据点。</span><span class="sxs-lookup"><span data-stu-id="56c86-104">Empty points are data points that can be inserted in the empty space created by null values.</span></span>  
  
 <span data-ttu-id="56c86-105">默认情况下，空点是通过取包含值的前一个数据点和后一个数据点的平均值而计算的。</span><span class="sxs-lookup"><span data-stu-id="56c86-105">By default, empty points are calculated by taking the average of the previous and next data points that contain a value.</span></span> <span data-ttu-id="56c86-106">您可以更改此默认行为以使所有空点都在零处插入。</span><span class="sxs-lookup"><span data-stu-id="56c86-106">You can change this so that all empty points are inserted at zero.</span></span>  
  
 <span data-ttu-id="56c86-107">有关详细信息，请参阅[图表中的空点和 Null 数据点（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="56c86-107">For more information, see [Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-empty-points-on-a-chart"></a><span data-ttu-id="56c86-108">在图表中指定空点</span><span class="sxs-lookup"><span data-stu-id="56c86-108">To specify empty points on a chart</span></span>  
  
1.  <span data-ttu-id="56c86-109">打开“属性”窗格。</span><span class="sxs-lookup"><span data-stu-id="56c86-109">Open the Properties pane.</span></span>  
  
2.  <span data-ttu-id="56c86-110">在设计图面上，右键单击包含 Null 值的序列。</span><span class="sxs-lookup"><span data-stu-id="56c86-110">On the design surface, right-click the series that contains null values.</span></span> <span data-ttu-id="56c86-111">序列的属性将显示在“属性”窗格中。</span><span class="sxs-lookup"><span data-stu-id="56c86-111">The properties for the series are displayed in the Properties pane.</span></span>  
  
3.  <span data-ttu-id="56c86-112">展开 **EmptyPoint** 节点。</span><span class="sxs-lookup"><span data-stu-id="56c86-112">Expand the **EmptyPoint** node.</span></span>  
  
4.  <span data-ttu-id="56c86-113">为 Color 属性选择颜色值。</span><span class="sxs-lookup"><span data-stu-id="56c86-113">Select a color value for the Color property.</span></span>  
  
5.  <span data-ttu-id="56c86-114">在 **EmptyPoint** 节点中，展开 Marker 节点。</span><span class="sxs-lookup"><span data-stu-id="56c86-114">In the **EmptyPoint** node, expand the Marker node.</span></span>  
  
6.  <span data-ttu-id="56c86-115">为 MarkerType 属性选择标记类型。</span><span class="sxs-lookup"><span data-stu-id="56c86-115">Select a marker type for the MarkerType property.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="56c86-116">您必须选择标记类型以将空点添加到条形图、柱形图或散点图中。</span><span class="sxs-lookup"><span data-stu-id="56c86-116">You must select a marker type to add empty points to a bar, column or scatter chart.</span></span> <span data-ttu-id="56c86-117">但是，对于面积图、折线图和雷达图，是否选择标记类型是可选的，因为这些图表会填充空格或空白，而不需要指定标记。</span><span class="sxs-lookup"><span data-stu-id="56c86-117">However, for area, line and radar charts, selecting a marker type is optional because the chart fills in the empty space or gap without requiring a marker to be specified.</span></span>  
  
7.  <span data-ttu-id="56c86-118">设置空点的值。</span><span class="sxs-lookup"><span data-stu-id="56c86-118">Set the value of the empty point.</span></span>  
  
    1.  <span data-ttu-id="56c86-119">在“属性”窗格中，展开 **CustomAttributes** 节点。</span><span class="sxs-lookup"><span data-stu-id="56c86-119">In the Properties pane, expand the **CustomAttributes** node.</span></span>  
  
    2.  <span data-ttu-id="56c86-120">设置 EmptyPointValue 属性。</span><span class="sxs-lookup"><span data-stu-id="56c86-120">Set the EmptyPointValue property.</span></span> <span data-ttu-id="56c86-121">若要在前一个数据点和后一个数据点的平均值插入空点，请选择 **Average**。</span><span class="sxs-lookup"><span data-stu-id="56c86-121">To insert empty points at an average of the previous and next data points, select **Average**.</span></span> <span data-ttu-id="56c86-122">若要在零处插入空点，请选择 **Zero**。</span><span class="sxs-lookup"><span data-stu-id="56c86-122">To insert empty points at zero, select **Zero**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56c86-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="56c86-123">See Also</span></span>  
 <span data-ttu-id="56c86-124">[添加数据集筛选器、数据区域筛选器和组筛选器（报表生成器和 SSRS）](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="56c86-124">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="56c86-125">[图表类型（报表生成器和 SSRS）](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="56c86-125">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="56c86-126">[在图表中添加刻度分隔线（报表生成器和 SSRS）](add-scale-breaks-to-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="56c86-126">[Add Scale Breaks to a Chart &#40;Report Builder and SSRS&#41;](add-scale-breaks-to-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="56c86-127">图表&#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="56c86-127">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
