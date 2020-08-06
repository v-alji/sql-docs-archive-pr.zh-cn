---
title: 设置图表格式（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10214"
- sql12.rtp.rptdesigner.calculatedseriesproperties.fill.f1
- sql12.rtp.rptdesigner.serieslabelproperties.fill.f1
- sql12.rtp.rptdesigner.legendproperties.fill.f1
- "10149"
- sql12.rtp.rptdesigner.seriesproperties.shadow.f1
- sql12.rtp.rptdesigner.seriesproperties.markers.f1
- "10255"
- sql12.rtp.rptdesigner.charttitleproperties.fill.f1
- "10154"
- "10170"
- "10173"
- sql12.rtp.rptdesigner.seriesproperties.fill.f1
- "10169"
- "10158"
- sql12.rtp.rptdesigner.chartareaproperties.fill.f1
- sql12.rtp.rptdesigner.charttitleproperties.shadow.f1
- "10246"
- "10150"
- sql12.rtp.rptdesigner.calculatedseriesproperties.borders.f1
- sql12.rtp.rptdesigner.chartproperties.fill.f1
- "10159"
- sql12.rtp.rptdesigner.majorgridlineproperties.gridlineoptions.f1
- "10160"
- sql12.rtp.rptdesigner.serieslabelproperties.font.f1
- "10182"
- "10163"
- "10164"
- "10253"
- "10216"
- "10171"
- "10257"
- sql12.rtp.rptdesigner.chartareaproperties.border.f1
- sql12.rtp.rptdesigner.calculatedseriesproperties.shadow.f1
- sql12.rtp.rptdesigner.chartproperties.border.f1
- sql12.rtp.rptdesigner.minorgridlineproperties.gridlineoptions.f1
- sql12.rtp.rptdesigner.chartareaproperties.shadow.f1
- sql12.rtp.rptdesigner.charttitleproperties.borders.f1
- sql12.rtp.rptdesigner.charttitleproperties.font.f1
- "10247"
ms.assetid: d3984300-c766-42f8-b7c4-863123d67c99
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: af164d4db9b6439f0634d113652b95939827b0f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580578"
---
# <a name="formatting-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="4ca6f-102">设置图表格式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4ca6f-102">Formatting a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="4ca6f-103">为图表定义数据并且该图表按预期方式显示之后，您可添加格式设置以改善整体外观效果并突出显示关键数据点。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-103">After you have defined the data for your chart and it is appearing the way you want, you can add formatting to improve the overall appearance and highlight key data points.</span></span> <span data-ttu-id="4ca6f-104">可以从“属性”对话框修改最常用的格式设置选项，此对话框在右键单击某图表元素以显示其快捷菜单时出现。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-104">The most common formatting options can be modified from the Properties dialog box that are found when you right-click a chart element to display its shortcut menu.</span></span> <span data-ttu-id="4ca6f-105">每个图表元素都有其相对应的对话框。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-105">Each chart element has its own dialog box.</span></span> <span data-ttu-id="4ca6f-106">有关图表元素的详细信息，请参阅 [图表（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-106">For more information about chart elements, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="4ca6f-107">与图表相关的所有属性都位于“属性”窗格中，但是其中许多属性都可以从对话框中进行设置。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-107">All properties that relate to the chart are located in the Properties pane, but many of these properties can also be set from a dialog box.</span></span> <span data-ttu-id="4ca6f-108">如果要对这些序列进行格式设置，可以使用自定义属性指定特定于序列的属性，这些属性只存在于“属性”窗格内的 **CustomAttributes** 属性类别中。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-108">If you are formatting the series, you can specify series-specific properties using custom attributes, which can only be found in the **CustomAttributes** category of properties, located in the Properties pane.</span></span>  
  
 <span data-ttu-id="4ca6f-109">若要使用最少的步骤有效地设置图表的格式，请更改默认边框样式、调色板和绘制样式。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-109">To effectively format the chart using a minimal number of steps, change the default border style, palette and drawing style.</span></span> <span data-ttu-id="4ca6f-110">这三种功能可在图表中产生最大程度的视觉效果变化。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-110">These three features produce the largest visible change on the chart.</span></span> <span data-ttu-id="4ca6f-111">绘制样式只适用于饼图、圆环图、条形图和柱形图。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-111">Drawing styles are only applicable to pie, doughnut, bar and column charts.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="in-this-section"></a><span data-ttu-id="4ca6f-112">本节内容</span><span class="sxs-lookup"><span data-stu-id="4ca6f-112">In This Section</span></span>  
 [<span data-ttu-id="4ca6f-113">设置图表上序列颜色的格式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4ca6f-113">Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;</span></span>](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)  
 <span data-ttu-id="4ca6f-114">讨论如何使用调色板定义颜色、如何定义自己的调色板，以及如何根据表达式定义颜色。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-114">Discusses how colors are defined using a palette, how you can define your own color palette, and how to define colors based on an expression.</span></span>  
  
 [<span data-ttu-id="4ca6f-115">设置图表上轴标签的格式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4ca6f-115">Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;</span></span>](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)  
 <span data-ttu-id="4ca6f-116">讨论如何显示网格线、刻度线和标题，以及如何设置轴刻度上数字和日期的格式。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-116">Discusses how to display gridlines, tick marks, and titles, and how to format numbers and dates on the axis scale.</span></span>  
  
 [<span data-ttu-id="4ca6f-117">设置图表上图例的格式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4ca6f-117">Formatting the Legend on a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-legend-formatting-report-builder.md)  
 <span data-ttu-id="4ca6f-118">讨论如何对图表图例中的项进行重新排序和格式设置。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-118">Discusses how to re-order and format items in the chart legend.</span></span>  
  
 [<span data-ttu-id="4ca6f-119">设置图表上数据点的格式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4ca6f-119">Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;</span></span>](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)  
 <span data-ttu-id="4ca6f-120">讨论如何放置数据点标签以及如何设置图表中每个序列的数据点标记的格式。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-120">Discusses how to position data point labels and format data point markers for every series on the chart.</span></span>  
  
 [<span data-ttu-id="4ca6f-121">图表中的三维效果、凹凸效果和其他效果（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4ca6f-121">3D, Bevel, and Other Effects in a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-effects-3d-bevel-and-other-report-builder.md)  
 <span data-ttu-id="4ca6f-122">讨论您可以对图表应用的各种三维效果。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-122">Discusses various 3D effects that you can apply to a chart.</span></span>  
  
 [<span data-ttu-id="4ca6f-123">向图表添加边框（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4ca6f-123">Add a Border Frame to a Chart &#40;Report Builder and SSRS&#41;</span></span>](add-a-border-frame-to-a-chart-report-builder-and-ssrs.md)  
 <span data-ttu-id="4ca6f-124">说明如何向图表添加边框。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-124">Explains how to add a border frame to a chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ca6f-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4ca6f-125">See Also</span></span>  
 <span data-ttu-id="4ca6f-126">[图表（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4ca6f-126">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4ca6f-127">[向图表添加边框（报表生成器和 SSRS）](add-a-border-frame-to-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4ca6f-127">[Add a Border Frame to a Chart &#40;Report Builder and SSRS&#41;](add-a-border-frame-to-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4ca6f-128">[使用调色板定义图表上的颜色（报表生成器和 SSRS）](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4ca6f-128">[Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="4ca6f-129">向图表添加凹凸效果、阳文和纹理样式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4ca6f-129">Add Bevel, Emboss, and Texture Styles to a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-effects-add-bevel-emboss-or-texture-report-builder.md)  
  
  
