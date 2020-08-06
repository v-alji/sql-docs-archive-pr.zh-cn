---
title: 图表中的三维效果、凹凸效果和其他效果（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10156"
ms.assetid: 18ef2119-2931-43ae-9078-f39b460462dd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f505a0226d1c95a1c0c7c3caffde2be60f407b43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590073"
---
# <a name="3d-bevel-and-other-effects-in-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="7211d-102">图表中的三维效果、凹凸效果和其他效果（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="7211d-102">3D, Bevel, and Other Effects in a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="7211d-103">三维 (3D) 效果可以使图表具有深度并增强视觉效果。</span><span class="sxs-lookup"><span data-stu-id="7211d-103">Three-dimensional (3D) effects can be used to provide depth and add visual impact to your chart.</span></span> <span data-ttu-id="7211d-104">例如，若要强调分离型饼图的某个特定切片，可以旋转并更改图表的透视，以便人们可以首先注意到该切片。</span><span class="sxs-lookup"><span data-stu-id="7211d-104">For example, if you want to emphasize a particular slice of an exploded pie chart, you can rotate and change the perspective of the chart so that people notice that slice first.</span></span> <span data-ttu-id="7211d-105">将三维效果应用于图表时，将会禁用所有渐变颜色和阴影类型。</span><span class="sxs-lookup"><span data-stu-id="7211d-105">When 3D effects are applied to your chart, all gradient colors and hatching styles are disabled.</span></span>  
  
 <span data-ttu-id="7211d-106">可以将三维效果应用于单个图表，还可以在同一报表中同时显示二维和三维图表。</span><span class="sxs-lookup"><span data-stu-id="7211d-106">Three-dimensional effects can be applied to individual charts, and it is possible to display both two-dimensional and three-dimensional charts on the same report.</span></span>  
  
 <span data-ttu-id="7211d-107">对于所有的图表类型，你都可以通过在“图表区属性”对话框中选择“启用三维”，将三维效果应用到图表区   。</span><span class="sxs-lookup"><span data-stu-id="7211d-107">For all chart types, you can add three-dimensional effects to a chart area in the **Chart Area Properties** dialog box by selecting **Enable 3D**.</span></span> <span data-ttu-id="7211d-108">有关详细信息，请参阅 [向图表添加三维效果（报表生成器和 SSRS）](chart-effects-add-3d-effects-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="7211d-108">For more information, see [Add 3D Effects to a Chart &#40;Report Builder and SSRS&#41;](chart-effects-add-3d-effects-report-builder.md).</span></span>  
  
 <span data-ttu-id="7211d-109">为图表增添视觉影响的另外一种方法是在条形图、柱形图、饼图和圆环图中添加凹凸效果、阳文和纹理样式。</span><span class="sxs-lookup"><span data-stu-id="7211d-109">Another way to add visual impact to charts is by adding bevel, emboss and texture styles in bar, column, pie and doughnut charts.</span></span> <span data-ttu-id="7211d-110">有关详细信息，请参阅[向图表添加凹凸效果、阳文和纹理样式（报表生成器和 SSRS）](chart-effects-add-bevel-emboss-or-texture-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="7211d-110">For more information, see [Add Bevel, Emboss, and Texture Styles to a Chart &#40;Report Builder and SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="coordinate-based-three-dimensional-charts"></a><span data-ttu-id="7211d-111">基于坐标的三维图表</span><span class="sxs-lookup"><span data-stu-id="7211d-111">Coordinate-Based Three-Dimensional Charts</span></span>  
 <span data-ttu-id="7211d-112">使用基于坐标的图表类型（柱形图、条形图、面积图、点状图、折线图和范围图）时，三维效果显示的图表具有第三条坐标轴，称为“Z 轴”。</span><span class="sxs-lookup"><span data-stu-id="7211d-112">When working with coordinate-based chart types (Column, Bar, Area, Point, Line and Range), three-dimensional effects display the chart with a third axis, known as the "z-axis".</span></span> <span data-ttu-id="7211d-113">通过引入第三条坐标轴，可以使您在图表中应用各种视觉增强效果。</span><span class="sxs-lookup"><span data-stu-id="7211d-113">The introduction of this third axis allows you to apply a variety of visual enhancements to your chart.</span></span>  
  
### <a name="changing-the-white-space-in-a-3d-chart"></a><span data-ttu-id="7211d-114">更改三维图表中的空格</span><span class="sxs-lookup"><span data-stu-id="7211d-114">Changing the White Space in a 3D Chart</span></span>  
 <span data-ttu-id="7211d-115">在三维模式下显示图表区时，每个序列都会沿图表的 Z 轴显示在单独的行中。</span><span class="sxs-lookup"><span data-stu-id="7211d-115">When you display a chart area in three-dimensional mode, each series is shown in a separate row along the z-axis of the chart.</span></span> <span data-ttu-id="7211d-116">若要更改每个序列之间的空格量，可通过更改“三维效果”对话框中的 **“点间隙深度”** 属性来修改图表的点间隙深度。</span><span class="sxs-lookup"><span data-stu-id="7211d-116">To change the amount of space between each series, modify the chart's point gap depth by changing the **Point Gap Depth** property in the 3D Effects dialog box.</span></span>  
  
### <a name="changing-the-projection-of-a-3d-chart"></a><span data-ttu-id="7211d-117">更改三维图表的投影</span><span class="sxs-lookup"><span data-stu-id="7211d-117">Changing the Projection of a 3D Chart</span></span>  
 <span data-ttu-id="7211d-118">有两种类型的三维投影：倾斜和透视。</span><span class="sxs-lookup"><span data-stu-id="7211d-118">There are two types of 3D projections: oblique and perspective.</span></span> <span data-ttu-id="7211d-119">图表的倾斜投影可以增加二维图表的深度维度。</span><span class="sxs-lookup"><span data-stu-id="7211d-119">An oblique projection to the chart adds a depth dimension to a two-dimensional chart.</span></span> <span data-ttu-id="7211d-120">绘制的 Z 轴与水平轴和垂直轴的角度是相等的，这三根轴像在二维图表中一样彼此保持垂直。</span><span class="sxs-lookup"><span data-stu-id="7211d-120">The z-axis is drawn at equal angles from the horizontal and vertical axes, which remain perpendicular to each other just as in a two-dimensional chart.</span></span>  
  
 <span data-ttu-id="7211d-121">透视投影可以通过估计一个视图平面，然后如同从该点查看图表那样重新绘制图表，来对该图表进行转换。</span><span class="sxs-lookup"><span data-stu-id="7211d-121">Perspective projection transforms the chart by estimating a view plane and re-drawing the chart as if it were being viewed from that point.</span></span> <span data-ttu-id="7211d-122">**“旋转”** 值将视图沿垂直方向从地平面 0 度移动到高于地平面 90 度。</span><span class="sxs-lookup"><span data-stu-id="7211d-122">The **Rotation** value shifts the view vertically from "ground level" at 0 to overhead at 90.</span></span> <span data-ttu-id="7211d-123">**“倾角”** 值将视角向左或向右移动。</span><span class="sxs-lookup"><span data-stu-id="7211d-123">The **Inclination** value shifts the viewing angle to the left or right.</span></span> <span data-ttu-id="7211d-124">如果该值为 0，则相当于二维视图的图表。</span><span class="sxs-lookup"><span data-stu-id="7211d-124">A value of 0 is equivalent to a two-dimensional view of the chart.</span></span> <span data-ttu-id="7211d-125">**“透视”** 值定义显示投影时使用的失真百分比。</span><span class="sxs-lookup"><span data-stu-id="7211d-125">The **Perspective** value defines the percentage of distortion that will be used when displaying the projection.</span></span> <span data-ttu-id="7211d-126">此类投影可以保持图表的比例，但图表的外观会显得失真，所以使用低角度透视是最有效的方法。</span><span class="sxs-lookup"><span data-stu-id="7211d-126">This type of projection maintains the proportions of your chart, but the chart's appearance becomes distorted, so it is most effective to use a lower degree of perspective.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7211d-127">倾斜和透视投影是单独的投影类型，所以它们不能在同一个图表中同时使用。</span><span class="sxs-lookup"><span data-stu-id="7211d-127">The oblique and perspective projections are separate types of projections, so they cannot be used together on the same chart.</span></span>  
  
### <a name="clustering-data"></a><span data-ttu-id="7211d-128">聚类分析数据</span><span class="sxs-lookup"><span data-stu-id="7211d-128">Clustering Data</span></span>  
 <span data-ttu-id="7211d-129">在二维图表中，多个序列的数据并行显示。</span><span class="sxs-lookup"><span data-stu-id="7211d-129">In 2D charts, multiple series of data appear side-by-side.</span></span> <span data-ttu-id="7211d-130">聚类分析将每个序列分别显示在三维图表的单独行中。</span><span class="sxs-lookup"><span data-stu-id="7211d-130">Clustering shows individual series in separate rows on a 3D chart.</span></span> <span data-ttu-id="7211d-131">例如，如果您的图表包含三个序列的数据点，聚类分析会将每个序列沿 Z 轴显示在单独的行中。</span><span class="sxs-lookup"><span data-stu-id="7211d-131">For example, if you have a chart that contains three series of data points, clustering will display each of the three series on a separate row along the z-axis.</span></span> <span data-ttu-id="7211d-132">默认情况下，会聚集所有以三维形式显示的图表类型。</span><span class="sxs-lookup"><span data-stu-id="7211d-132">By default, all chart types shown in 3D are clustered.</span></span>  
  
 <span data-ttu-id="7211d-133">可以在条形图和柱形图中禁用聚类分析。</span><span class="sxs-lookup"><span data-stu-id="7211d-133">Clustering can be disabled for bar and column charts.</span></span> <span data-ttu-id="7211d-134">禁用聚类分析时，会在同一行中并行显示多个条形和柱形序列。</span><span class="sxs-lookup"><span data-stu-id="7211d-134">When clustering is disabled, multiple bar and column series are displayed side-by-side in one row.</span></span>  
  
## <a name="shape-based-three-dimensional-charts"></a><span data-ttu-id="7211d-135">基于形状的三维图表</span><span class="sxs-lookup"><span data-stu-id="7211d-135">Shape-Based Three-Dimensional Charts</span></span>  
 <span data-ttu-id="7211d-136">基于形状的图表类型（饼图、圆环图、漏斗图、棱锥图）可用的三维效果较少。</span><span class="sxs-lookup"><span data-stu-id="7211d-136">Shape-based chart types (Pie, Doughnut, Funnel, Pyramid) have fewer three-dimensional effects available.</span></span> <span data-ttu-id="7211d-137">在使用基于形状的图表类型时，您只能更改旋转值和倾角值。</span><span class="sxs-lookup"><span data-stu-id="7211d-137">When working with shape-based chart types, you can change the rotation and inclination values only.</span></span>  
  
## <a name="rotations"></a><span data-ttu-id="7211d-138">旋转</span><span class="sxs-lookup"><span data-stu-id="7211d-138">Rotations</span></span>  
 <span data-ttu-id="7211d-139">图表可以从 -90 到 90 度进行水平和垂直旋转。</span><span class="sxs-lookup"><span data-stu-id="7211d-139">Charts can be rotated horizontally and vertically from -90 to 90 degrees.</span></span> <span data-ttu-id="7211d-140">水平的正角会将图表沿 X 轴逆时针旋转，而垂直的正角则会将图表沿 Y 轴顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="7211d-140">A positive horizontal angle will rotate the chart counter-clockwise around the x-axis, while a positive vertical angle will rotate the chart clockwise around the y-axis.</span></span>  
  
## <a name="highlighting-3d-effects"></a><span data-ttu-id="7211d-141">突出显示三维效果</span><span class="sxs-lookup"><span data-stu-id="7211d-141">Highlighting 3D Effects</span></span>  
 <span data-ttu-id="7211d-142">选择图表区时，您可以通过在“属性”窗格中 Area3Dstyle 下出现的 **“明暗度”** 属性，为三维图表添加突出显示样式。</span><span class="sxs-lookup"><span data-stu-id="7211d-142">You can add highlighting styles to a 3D chart via the **Shading** property, which appears under Area3DStyle in the Properties pane when the chart area is selected.</span></span> <span data-ttu-id="7211d-143">简单的照明样式会对图表区元素应用相同的色调。</span><span class="sxs-lookup"><span data-stu-id="7211d-143">A simple lighting style applies the same hue to the chart area elements.</span></span> <span data-ttu-id="7211d-144">真实样式会根据指定的照明角度，更改图表区元素的色调。</span><span class="sxs-lookup"><span data-stu-id="7211d-144">A realistic style changes the hues of the chart area elements depending on a specified lighting angle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7211d-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7211d-145">See Also</span></span>  
 <span data-ttu-id="7211d-146">[设置图表上轴标签的格式（报表生成器和 SSRS）](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7211d-146">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7211d-147">[设置图表格式（报表生成器和 SSRS）](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7211d-147">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="7211d-148">向图表添加三维效果（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="7211d-148">Add 3D Effects to a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-effects-add-3d-effects-report-builder.md)  
  
  
