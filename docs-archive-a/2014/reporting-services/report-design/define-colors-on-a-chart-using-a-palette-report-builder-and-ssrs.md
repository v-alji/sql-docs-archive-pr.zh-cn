---
title: 使用调色板定义图表上的颜色（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d95efc22-5a32-43d4-9bd2-12753e7fd395
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7db137ed87b0c84e43577dcf2936a6287abd8e36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586441"
---
# <a name="define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs"></a><span data-ttu-id="68187-102">使用调色板定义图表上的颜色（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="68187-102">Define Colors on a Chart Using a Palette (Report Builder and SSRS)</span></span>
  <span data-ttu-id="68187-103">您可以通过选择预定义调色板或定义自定义调色板来更改图表的调色板。</span><span class="sxs-lookup"><span data-stu-id="68187-103">You can change the color palette for a chart by selecting a pre-defined palette or defining a custom palette.</span></span> <span data-ttu-id="68187-104">自定义调色板是针对具体报表而言。</span><span class="sxs-lookup"><span data-stu-id="68187-104">Custom palettes are report-specific.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-colors-on-the-chart-using-a-built-in-color-palette"></a><span data-ttu-id="68187-105">使用内置调色板更改图表的颜色</span><span class="sxs-lookup"><span data-stu-id="68187-105">To change the colors on the chart using a built-in color palette</span></span>  
  
1.  <span data-ttu-id="68187-106">打开“属性”窗格。</span><span class="sxs-lookup"><span data-stu-id="68187-106">Open the Properties pane.</span></span>  
  
2.  <span data-ttu-id="68187-107">在设计图面上，单击该图表。</span><span class="sxs-lookup"><span data-stu-id="68187-107">On the design surface, click the chart.</span></span> <span data-ttu-id="68187-108">图表对象的属性将显示在“属性”窗格中。</span><span class="sxs-lookup"><span data-stu-id="68187-108">The properties for the chart object are displayed in the Properties pane.</span></span>  
  
     <span data-ttu-id="68187-109">对象名称（默认为**Chart1** ）将显示在“属性”窗格顶部的下拉列表中。</span><span class="sxs-lookup"><span data-stu-id="68187-109">The object name (**Chart1** by default) appears in the drop-down list at the top of the Properties pane.</span></span>  
  
3.  <span data-ttu-id="68187-110">在“图表”部分，从下拉列表中为 Palette 属性选择新的调色板  。</span><span class="sxs-lookup"><span data-stu-id="68187-110">In the **Chart** section, for the Palette property, select a new palette from the drop-down list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="68187-111">您无法更改预定义调色板中的颜色或顺序。</span><span class="sxs-lookup"><span data-stu-id="68187-111">You cannot change the colors or order in a pre-defined palette.</span></span>  
  
### <a name="to-define-your-own-colors-on-the-chart-using-a-custom-color-palette"></a><span data-ttu-id="68187-112">使用自定义调色板定义自己的图表颜色</span><span class="sxs-lookup"><span data-stu-id="68187-112">To define your own colors on the chart using a custom color palette</span></span>  
  
1.  <span data-ttu-id="68187-113">打开“属性”窗格。</span><span class="sxs-lookup"><span data-stu-id="68187-113">Open the Properties pane.</span></span>  
  
2.  <span data-ttu-id="68187-114">在设计图面上，单击该图表。</span><span class="sxs-lookup"><span data-stu-id="68187-114">On the design surface, click the chart.</span></span> <span data-ttu-id="68187-115">图表对象的属性将显示在“属性”窗格中。</span><span class="sxs-lookup"><span data-stu-id="68187-115">The properties for the chart object are displayed in the Properties pane.</span></span>  
  
3.  <span data-ttu-id="68187-116">在 "**图表**" 部分，为 " `Palette` 属性" 选择 "**自定义**"。</span><span class="sxs-lookup"><span data-stu-id="68187-116">In the **Chart** section, for the `Palette` property, select **Custom**.</span></span>  
  
4.  <span data-ttu-id="68187-117">在 CustomPaletteColors 属性中，单击“编辑集合”(…) 按钮  。</span><span class="sxs-lookup"><span data-stu-id="68187-117">In the CustomPaletteColors property, click the Edit Collection (**...**) button.</span></span> <span data-ttu-id="68187-118">将打开 **“ReportColorExpression 集合编辑器”** 。</span><span class="sxs-lookup"><span data-stu-id="68187-118">The **ReportColorExpression Collection Editor** opens.</span></span>  
  
5.  <span data-ttu-id="68187-119">单击 **“添加”** 以添加颜色。</span><span class="sxs-lookup"><span data-stu-id="68187-119">Click **Add** to add a color.</span></span> <span data-ttu-id="68187-120">从下拉列表中选择颜色或选择“表达式”并为特定颜色指定十六进制值，例如“橙色”为 ff6600。</span><span class="sxs-lookup"><span data-stu-id="68187-120">Select a color from the drop-down list or select Expression and specify a hex value for a specific color, such as ff6600 for "Orange".</span></span>  
  
     <span data-ttu-id="68187-121">有关十六进制值的更多信息，请参阅 MSDN 上的 [Color Table](https://go.microsoft.com/fwlink/?linkid=9258) （颜色表）。</span><span class="sxs-lookup"><span data-stu-id="68187-121">For more information about hex values, see [Color Table](https://go.microsoft.com/fwlink/?linkid=9258) on MSDN.</span></span>  
  
6.  <span data-ttu-id="68187-122">单击 **“添加”** 以向调色板添加更多颜色。</span><span class="sxs-lookup"><span data-stu-id="68187-122">Click **Add** to add more colors to the palette.</span></span>  
  
7.  <span data-ttu-id="68187-123">完成后，单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="68187-123">When you are done, click **OK**.</span></span>  
  
 <span data-ttu-id="68187-124">如果使用自定义调色板，可更改颜色顺序以调整图表中不同序列的颜色。</span><span class="sxs-lookup"><span data-stu-id="68187-124">If you are using a custom palette, you can change the order of the colors to change the color of different series in the chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68187-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="68187-125">See Also</span></span>  
 <span data-ttu-id="68187-126">[设置图表上序列颜色的格式（报表生成器和 SSRS）](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="68187-126">[Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="68187-127">[图表（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="68187-127">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="68187-128">对多个形状图指定一致的颜色（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="68187-128">Specify Consistent Colors across Multiple Shape Charts &#40;Report Builder and SSRS&#41;</span></span>](shape-charts-report-builder-and-ssrs.md)  
  
  
