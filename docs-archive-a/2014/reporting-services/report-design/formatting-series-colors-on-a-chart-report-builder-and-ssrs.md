---
title: 设置图表上序列颜色的格式（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10245"
- "10252"
- sql12.rtp.rptdesigner.serieslabelproperties.borders.f1
- sql12.rtp.rptdesigner.seriesproperties.borders.f1
ms.assetid: fe541501-cac5-47b1-b95f-c410db789190
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f0e4f526e32ba38b94c5707c1ce3acc3cd073626
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682708"
---
# <a name="formatting-series-colors-on-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="628ba-102">设置图表上序列颜色的格式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="628ba-102">Formatting Series Colors on a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="628ba-103">Reporting Services 为图表提供了多种内置调色板，或者您也可以定义自定义调色板。</span><span class="sxs-lookup"><span data-stu-id="628ba-103">Reporting Services provides several built-in palettes for charts, or you can define a custom palette.</span></span> <span data-ttu-id="628ba-104">默认情况下，图表使用内置**BrightPastel**调色板填充每个序列。</span><span class="sxs-lookup"><span data-stu-id="628ba-104">By default, charts use the built-in **BrightPastel** color palette to fill each series.</span></span> <span data-ttu-id="628ba-105">这些颜色也会显示在图例中。</span><span class="sxs-lookup"><span data-stu-id="628ba-105">These colors also appear in the legend.</span></span> <span data-ttu-id="628ba-106">向图表添加多个序列时，图表按颜色在调色板中的定义顺序为序列各分配一种颜色。</span><span class="sxs-lookup"><span data-stu-id="628ba-106">When multiple series are added to the chart, the chart assigns the series a color in the order that the colors have been defined in the palette.</span></span>  
  
 <span data-ttu-id="628ba-107">如果序列中的颜色数多于调色板中的颜色，图表将开始重用颜色，因此两个序列可能具有相同的颜色。</span><span class="sxs-lookup"><span data-stu-id="628ba-107">If there are a greater number of series than there are colors in the palette, the chart will begin reusing colors, and two series may have the same color.</span></span> <span data-ttu-id="628ba-108">如果使用的是形状图，形状图中的每个数据点都分配有调色板中的颜色，因此可能经常发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="628ba-108">This frequently occurs if you are using a Shape chart, where each data point is assigned a color from the palette.</span></span> <span data-ttu-id="628ba-109">为避免混淆，请将自定义调色板的颜色数至少定义为图表上的相同序列数。</span><span class="sxs-lookup"><span data-stu-id="628ba-109">To avoid confusion, define a custom palette with at least the same number of colors as you have series on your chart.</span></span>  
  
 <span data-ttu-id="628ba-110">可以选择新调色板，也可以从“属性”窗格定义自定义调色板。</span><span class="sxs-lookup"><span data-stu-id="628ba-110">You can select a new palette or define a custom palette from the Properties pane.</span></span> <span data-ttu-id="628ba-111">有关详细信息，请参阅[使用调色板定义图表上的颜色（报表生成器和 SSRS）](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="628ba-111">For more information, see [Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="using-built-in-palettes"></a><span data-ttu-id="628ba-112">使用内置调色板</span><span class="sxs-lookup"><span data-stu-id="628ba-112">Using Built-In Palettes</span></span>  
 <span data-ttu-id="628ba-113">Reporting Services 提供了一系列可用于为图表上的序列定义颜色集的预定义内置调色板。</span><span class="sxs-lookup"><span data-stu-id="628ba-113">Reporting Services provides a list of predefined, built-in palettes that you can use to define a color set for series on your chart.</span></span> <span data-ttu-id="628ba-114">所有内置调色板包含 10 至 16 种颜色值。</span><span class="sxs-lookup"><span data-stu-id="628ba-114">All built-in palettes contain between 10 and 16 color values.</span></span> <span data-ttu-id="628ba-115">无法扩展内置调色板使其包括更多颜色，因此如果需要的颜色超过 16 种，必须定义自定义调色板。</span><span class="sxs-lookup"><span data-stu-id="628ba-115">You cannot extend the built-in palette to include more colors, so if you need more than 16 colors, you must define a custom palette.</span></span>  
  
 <span data-ttu-id="628ba-116">如果要打印报表，请考虑使用 **“灰度”** 调色板。</span><span class="sxs-lookup"><span data-stu-id="628ba-116">If you are printing a report, consider using the **Greyscale** palette.</span></span> <span data-ttu-id="628ba-117">该调色板使用多种色度的黑色和白色来表示图表中的每个序列。</span><span class="sxs-lookup"><span data-stu-id="628ba-117">This palette uses shades of black and white to represent each series in a chart.</span></span>  
  
 <span data-ttu-id="628ba-118">名为“默认”的调色板在 Reporting Services 早期版本中用作默认图表调色板。</span><span class="sxs-lookup"><span data-stu-id="628ba-118">The palette named Default was used as the default chart palette in earlier versions of Reporting Services.</span></span> <span data-ttu-id="628ba-119">该调色板使用相同名称进行维护以保持一致。</span><span class="sxs-lookup"><span data-stu-id="628ba-119">It has been maintained with the same name for consistency.</span></span> <span data-ttu-id="628ba-120">图表将使用默认调色板进行无缝升级，但在升级之后，可以考虑更改它。</span><span class="sxs-lookup"><span data-stu-id="628ba-120">Charts will upgrade seamlessly using the Default palette, but after upgrading, you might consider changing it.</span></span>  
  
## <a name="using-custom-palettes"></a><span data-ttu-id="628ba-121">使用自定义调色板</span><span class="sxs-lookup"><span data-stu-id="628ba-121">Using Custom Palettes</span></span>  
 <span data-ttu-id="628ba-122">如果要向图表应用您自己的颜色，请使用自定义调色板。</span><span class="sxs-lookup"><span data-stu-id="628ba-122">If you want to apply your own colors to the chart, use a custom palette.</span></span> <span data-ttu-id="628ba-123">使用自定义调色板可以按颜色在图表上的所需显示顺序来添加您自己的颜色。</span><span class="sxs-lookup"><span data-stu-id="628ba-123">A custom palette let you add your own colors in the order you want them to appear on the chart.</span></span> <span data-ttu-id="628ba-124">如果在设计时不知道图表中的序列数，使用自定义调色板尤其有用。</span><span class="sxs-lookup"><span data-stu-id="628ba-124">A custom palette is especially helpful if the number of series in your chart is unknown at design time.</span></span> <span data-ttu-id="628ba-125">有关详细信息，请参阅[使用调色板定义图表上的颜色（报表生成器和 SSRS）](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="628ba-125">For more information, see [Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md).</span></span>  
  
## <a name="using-a-color-fill-on-each-series"></a><span data-ttu-id="628ba-126">对每个序列使用颜色填充</span><span class="sxs-lookup"><span data-stu-id="628ba-126">Using a Color Fill on Each Series</span></span>  
 <span data-ttu-id="628ba-127">通过为图表中的每个序列各指定一种颜色，还可以在图表上定义您自己的颜色。</span><span class="sxs-lookup"><span data-stu-id="628ba-127">You can also define your own colors on the chart by specifying a color for each series on the chart.</span></span> <span data-ttu-id="628ba-128">为此，请打开 **“序列属性”** 对话框，并设置 **“填充”** 的 **“颜色”** 属性。</span><span class="sxs-lookup"><span data-stu-id="628ba-128">To do this, open the **Series Properties** dialog box and set the **Color** property for **Fill**.</span></span> <span data-ttu-id="628ba-129">该方法将覆盖定义的所有调色板。</span><span class="sxs-lookup"><span data-stu-id="628ba-129">This approach will override all defined palettes.</span></span> <span data-ttu-id="628ba-130">通常，最好使用自定义调色板定义您自己的颜色，因为在报表处理之前，您可能不知道数据集中的序列数。</span><span class="sxs-lookup"><span data-stu-id="628ba-130">Generally, it is better to use a custom palette to define your own colors because the number of series in your dataset may not be known until report processing.</span></span>  
  
 <span data-ttu-id="628ba-131">该方法最适合希望根据表达式按条件设置序列颜色的情况。</span><span class="sxs-lookup"><span data-stu-id="628ba-131">This approach is best suited when you want to conditionally set the color of the series based on an expression.</span></span>  <span data-ttu-id="628ba-132">有关详细信息，请参阅 [设置图表上数据点的格式（报表生成器和 SSRS）](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="628ba-132">For more information, see [Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="628ba-133">本节内容</span><span class="sxs-lookup"><span data-stu-id="628ba-133">In This Section</span></span>  
 [<span data-ttu-id="628ba-134">对多个形状图指定一致的颜色（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="628ba-134">Specify Consistent Colors across Multiple Shape Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
 <span data-ttu-id="628ba-135">[使用调色板定义图表上的颜色（报表生成器和 SSRS](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md)）</span><span class="sxs-lookup"><span data-stu-id="628ba-135">[Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md))</span></span>  
  
 [<span data-ttu-id="628ba-136">通过添加条带线突出显示图表数据（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="628ba-136">Highlight Chart Data by Adding Strip Lines &#40;Report Builder and SSRS&#41;</span></span>](highlight-chart-data-by-adding-strip-lines-report-builder-and-ssrs.md)  
  
## <a name="see-also"></a><span data-ttu-id="628ba-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="628ba-137">See Also</span></span>  
 <span data-ttu-id="628ba-138">[设置图表格式（报表生成器和 SSRS）](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="628ba-138">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="628ba-139">[向图表添加凹凸效果、浮雕和纹理样式（报表生成器和 SSRS）](chart-effects-add-bevel-emboss-or-texture-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="628ba-139">[Add Bevel, Emboss, and Texture Styles to a Chart &#40;Report Builder and SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md) </span></span>  
 <span data-ttu-id="628ba-140">[图表（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="628ba-140">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="628ba-141">设置图表上图例的格式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="628ba-141">Formatting the Legend on a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-legend-formatting-report-builder.md)  
  
  
