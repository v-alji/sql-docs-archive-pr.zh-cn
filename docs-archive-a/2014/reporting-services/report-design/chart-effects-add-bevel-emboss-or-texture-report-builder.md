---
title: 向图表添加棱台、浮雕和纹理样式（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 737cfc80-b39e-497c-817b-b46693deb58f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 92c5d4af47b7889b9ba5ec421706848f8822075b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590069"
---
# <a name="add-bevel-emboss-and-texture-styles-to-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="57b4d-102">向图表添加凹凸效果、阳文和纹理样式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="57b4d-102">Add Bevel, Emboss, and Texture Styles to a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="57b4d-103">当使用某些图表类型时，您可以指定绘制样式以增加图表的视觉效果。</span><span class="sxs-lookup"><span data-stu-id="57b4d-103">When using certain chart types, you can specify a drawing effect to increase the visual impact of your chart.</span></span> <span data-ttu-id="57b4d-104">这些绘制效果仅适用于图表的序列。</span><span class="sxs-lookup"><span data-stu-id="57b4d-104">These drawing effects are only applied to the series of your chart.</span></span> <span data-ttu-id="57b4d-105">它们对其他图表元素不起任何作用。</span><span class="sxs-lookup"><span data-stu-id="57b4d-105">They have no effect on any other chart element.</span></span>  
  
 <span data-ttu-id="57b4d-106">当使用的是饼图或圆环图的任何变体时，可以指定软边或凹陷绘制样式，这类似于可应用到图像的凹凸效果或阳文效果。</span><span class="sxs-lookup"><span data-stu-id="57b4d-106">When you are using any variant of a pie or doughnut chart, you can specify a soft edge or concave drawing style, similar to bevel or emboss effects that can be applied to an image.</span></span>  
  
 <span data-ttu-id="57b4d-107">当使用的是条形图或柱状图的任何变体时，可以对各个图条或图柱应用纹理样式，例如柱状、楔形和亮转暗。</span><span class="sxs-lookup"><span data-stu-id="57b4d-107">When you are using any variant of a bar or column chart, you can apply texture styles, such as cylinder, wedge, and light-to-dark, to the individual bars or columns.</span></span>  
  
 <span data-ttu-id="57b4d-108">除了上述绘制样式外，还可以向许多图表元素添加边框和阴影，以制造一种具有深度的错觉。</span><span class="sxs-lookup"><span data-stu-id="57b4d-108">In addition to these drawing styles, you can add borders and shadows to many chart elements to give the illusion of depth.</span></span> <span data-ttu-id="57b4d-109">有关设置图表格式的其它方法的详细信息，请参阅 [设置图表格式（报表生成器和 SSRS）](formatting-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="57b4d-109">For more information on other ways to format the chart, see [Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-bevel-or-emboss-styles-to-a-pie-or-doughnut-chart"></a><span data-ttu-id="57b4d-110">向饼图或圆环图添加凹凸效果或阳文样式</span><span class="sxs-lookup"><span data-stu-id="57b4d-110">To add bevel or emboss styles to a pie or doughnut chart</span></span>  
  
1.  <span data-ttu-id="57b4d-111">在 **“视图”** 选项卡上，选择 **“属性”** 以打开“属性”窗格。</span><span class="sxs-lookup"><span data-stu-id="57b4d-111">On the **View** tab, select **Properties** to open the Properties pane.</span></span>  
  
2.  <span data-ttu-id="57b4d-112">选择要增强的饼图或圆环图。</span><span class="sxs-lookup"><span data-stu-id="57b4d-112">Select the pie or doughnut chart that you want to enhance.</span></span> <span data-ttu-id="57b4d-113">选择图表中的一个数据字段，而不是整个图表。</span><span class="sxs-lookup"><span data-stu-id="57b4d-113">Select a data field in the chart, not the entire chart.</span></span>  
  
3.  <span data-ttu-id="57b4d-114">在“属性”窗格中，展开 **CustomAttributes** 节点。</span><span class="sxs-lookup"><span data-stu-id="57b4d-114">In the Properties pane, expand the **CustomAttributes** node.</span></span>  
  
4.  <span data-ttu-id="57b4d-115">对于 PieDrawingStyle，从下拉列表中选择一种样式。</span><span class="sxs-lookup"><span data-stu-id="57b4d-115">For PieDrawingStyle, select a style from the drop-down list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="57b4d-116">不能在同一个图表上具有三维和凹凸效果或阳文样式。</span><span class="sxs-lookup"><span data-stu-id="57b4d-116">You can't have 3D and bevel or emboss styles on the same chart.</span></span> <span data-ttu-id="57b4d-117">如果已为图表启用三维样式，将看不到 PieDrawingStyle 属性。</span><span class="sxs-lookup"><span data-stu-id="57b4d-117">If you have enabled 3D for the chart, you will not see the PieDrawingStyle property.</span></span>  
  
 <span data-ttu-id="57b4d-118">![具有凹形绘制样式的饼图](../media/rs-piedrawingeffects-concave.gif "具有凹形绘制样式的饼图")</span><span class="sxs-lookup"><span data-stu-id="57b4d-118">![Pie chart with concave drawing style](../media/rs-piedrawingeffects-concave.gif "Pie chart with concave drawing style")</span></span>  
  
### <a name="to-add-texture-styles-to-a-bar-or-column-chart"></a><span data-ttu-id="57b4d-119">向条形图或柱状图中添加纹理样式</span><span class="sxs-lookup"><span data-stu-id="57b4d-119">To add texture styles to a bar or column chart</span></span>  
  
1.  <span data-ttu-id="57b4d-120">选择要增强的条形图或柱状图。</span><span class="sxs-lookup"><span data-stu-id="57b4d-120">Select the bar or column chart that you want to enhance.</span></span> <span data-ttu-id="57b4d-121">选择图表中的一个数据字段，而不是整个图表。</span><span class="sxs-lookup"><span data-stu-id="57b4d-121">Select a data field in the chart, not the entire chart.</span></span>  
  
2.  <span data-ttu-id="57b4d-122">打开“属性”窗格。</span><span class="sxs-lookup"><span data-stu-id="57b4d-122">Open the Properties pane.</span></span>  
  
3.  <span data-ttu-id="57b4d-123">展开 **CustomAttributes** 节点。</span><span class="sxs-lookup"><span data-stu-id="57b4d-123">Expand the **CustomAttributes** node.</span></span>  
  
4.  <span data-ttu-id="57b4d-124">对于 DrawingStyle，从下拉列表中选择一种样式。</span><span class="sxs-lookup"><span data-stu-id="57b4d-124">For DrawingStyle, select a style from the drop-down list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="57b4d-125">不能在同一个图表上具有三维和凹凸效果或阳文样式。</span><span class="sxs-lookup"><span data-stu-id="57b4d-125">You can't have 3D and bevel or emboss styles on the same chart.</span></span> <span data-ttu-id="57b4d-126">如果已为图表启用三维样式，将看不到 PieDrawingStyle 属性。</span><span class="sxs-lookup"><span data-stu-id="57b4d-126">If you have enabled 3D for the chart, you will not see the PieDrawingStyle property.</span></span>  
  
 <span data-ttu-id="57b4d-127">![具有 LightToDark 绘制效果的条形图](../media/rs-bardrawingeffects-lighttodark.gif "具有 LightToDark 绘制效果的条形图")</span><span class="sxs-lookup"><span data-stu-id="57b4d-127">![Bar chart with LightToDark drawing effect](../media/rs-bardrawingeffects-lighttodark.gif "Bar chart with LightToDark drawing effect")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57b4d-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="57b4d-128">See Also</span></span>  
 <span data-ttu-id="57b4d-129">[条形图（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="57b4d-129">[Bar Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="57b4d-130">[柱形图（报表生成器和 SSRS）](column-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="57b4d-130">[Column Charts &#40;Report Builder and SSRS&#41;](column-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="57b4d-131">[饼图（报表生成器和 SSRS）](pie-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="57b4d-131">[Pie Charts &#40;Report Builder and SSRS&#41;](pie-charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="57b4d-132">设置图表格式&#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="57b4d-132">Formatting a Chart &#40;Report Builder and SSRS&#41;</span></span>](formatting-a-chart-report-builder-and-ssrs.md)  
  
  
