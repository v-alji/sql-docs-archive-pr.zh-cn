---
title: 跨多个形状图指定一致的颜色 (报表生成器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d52f68e9-2ba7-4bff-9053-4089e5164ab4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c2c89f0f8cda3b7d6ef6b2acbd0de66c87170357
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577261"
---
# <a name="specify-consistent-colors-across-multiple-shape-charts-report-builder-and-ssrs"></a><span data-ttu-id="665b3-102">对多个形状图指定一致的颜色（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="665b3-102">Specify Consistent Colors across Multiple Shape Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="665b3-103">在非形状图上，基于图表中的序列索引，从调色板中选择一种新颜色。</span><span class="sxs-lookup"><span data-stu-id="665b3-103">On non-shape charts, a new color is selected from the palette based on the index of series in the chart.</span></span> <span data-ttu-id="665b3-104">例如，图表中的第一个序列将映射到调色板中的第一个颜色。</span><span class="sxs-lookup"><span data-stu-id="665b3-104">For example, the first series on your chart will be mapped to the first color in the palette.</span></span> <span data-ttu-id="665b3-105">但是，对于形状图，该行为则不相同。</span><span class="sxs-lookup"><span data-stu-id="665b3-105">However, this behavior differs for shape charts.</span></span> <span data-ttu-id="665b3-106">在形状图中，调色板中的每个颜色都映射到数据集中的数据点。</span><span class="sxs-lookup"><span data-stu-id="665b3-106">On shape charts, each color in the palette is mapped to a data point in the dataset.</span></span> <span data-ttu-id="665b3-107">例如，数据点 1 映射到调色板中的第一个颜色，数据点 2 映射调色板中的第二个颜色，依此类推。</span><span class="sxs-lookup"><span data-stu-id="665b3-107">For example, data point 1 is mapped to the first color in the palette, data point 2 is mapped to the second color palette and so on.</span></span>  
  
 <span data-ttu-id="665b3-108">如果数据点没有值，该数据点则不显示在形状图中。</span><span class="sxs-lookup"><span data-stu-id="665b3-108">If a data point has no value, it is omitted from display on a shape chart.</span></span> <span data-ttu-id="665b3-109">这表示显示颜色时将跳过此数据点。</span><span class="sxs-lookup"><span data-stu-id="665b3-109">This means that the data point is skipped from being colored.</span></span> <span data-ttu-id="665b3-110">例如，如果点 2 的值为零，点 1 将映射到调色板中的第一个颜色，点 3 将映射到调色板中的第二个颜色。</span><span class="sxs-lookup"><span data-stu-id="665b3-110">For example, if point 2 has a value of zero, point 1 will be mapped to the first color in the palette, and point 3 will be mapped to the second color in the palette.</span></span> <span data-ttu-id="665b3-111">上述方法非常有用，因为除非在必要情况下，否则当不需要绘制饼图数据集中的空点时，空点不会使用调色板颜色。</span><span class="sxs-lookup"><span data-stu-id="665b3-111">This approach is useful because the empty points in the dataset of a pie chart do not unnecessarily use a palette color when the empty point does not need to be drawn.</span></span>  
  
 <span data-ttu-id="665b3-112">其副作用是，当在报表中显示多个饼图时，饼图可能会对具有相同类别分组的数据点显示不同的颜色。</span><span class="sxs-lookup"><span data-stu-id="665b3-112">As a side effect, when multiple pie charts are displayed in a report, the pie charts may display different colors for data points that have the same category grouping.</span></span> <span data-ttu-id="665b3-113">若要解决该问题，您需要定义映射到类别组而不是各数据值的每一种颜色。</span><span class="sxs-lookup"><span data-stu-id="665b3-113">To resolve this, you need to define individual colors that map to a category group instead of individual data values.</span></span> <span data-ttu-id="665b3-114">您如何进行定义取决于形状图是否是表或矩阵中的迷你图或者它们是否是报表本身中的形状图。</span><span class="sxs-lookup"><span data-stu-id="665b3-114">How you do this depends on if the shape charts are sparklines in a table or matrix, or if they are shape charts in the report itself.</span></span>  
  
 <span data-ttu-id="665b3-115">图例与序列相连，因此为序列指定的任何颜色将自动在图例上显示。</span><span class="sxs-lookup"><span data-stu-id="665b3-115">The legend is connected to the series, so any color you specify for the series will automatically be shown on the legend.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-consistent-colors-across-multiple-sparkline-shape-charts-in-a-table-or-matrix"></a><span data-ttu-id="665b3-116">在表或矩阵中跨多个迷你图形状图指定一致的颜色</span><span class="sxs-lookup"><span data-stu-id="665b3-116">To specify consistent colors across multiple sparkline shape charts in a table or matrix</span></span>  
  
1.  <span data-ttu-id="665b3-117">单击图表以显示“图表数据”窗格。</span><span class="sxs-lookup"><span data-stu-id="665b3-117">Click the chart to display the Chart Data pane.</span></span>  
  
2.  <span data-ttu-id="665b3-118">在“类别组”区域中右键单击某一类别，然后单击“类别组属性”   。</span><span class="sxs-lookup"><span data-stu-id="665b3-118">In the **Category Groups** area, right-click a category and click **Category Group Properties**.</span></span>  
  
3.  <span data-ttu-id="665b3-119">在“常规”选项卡上的 **“同步其中的组”** 框中，单击要同步其颜色的类别的名称，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="665b3-119">On the General tab, in the **Synchronize groups in** box, click the name of the category for which you would like to synchronize colors, and then click **OK**.</span></span>  
  
### <a name="to-specify-consistent-colors-across-multiple-shape-charts"></a><span data-ttu-id="665b3-120">跨多个形状图指定一致的颜色</span><span class="sxs-lookup"><span data-stu-id="665b3-120">To specify consistent colors across multiple shape charts</span></span>  
  
1.  <span data-ttu-id="665b3-121">右键单击表体外部区域，然后选择“报表属性”  。</span><span class="sxs-lookup"><span data-stu-id="665b3-121">Right-click outside the body of the report, and select **Report Properties**.</span></span>  
  
2.  <span data-ttu-id="665b3-122">在 **“代码”** 中，将以下代码键入到文本框中。</span><span class="sxs-lookup"><span data-stu-id="665b3-122">In **Code**, type the following code into the textbox.</span></span>  
  
    ```  
    Private colorPalette As String() = {"Color1", "Color2", "Color3"}  
    Private count As Integer = 0  
    Private mapping As New System.Collections.Hashtable()  
    Public Function GetColor(ByVal groupingValue As String) As String  
        If mapping.ContainsKey(groupingValue) Then  
            Return mapping(groupingValue)  
        End If  
        Dim c As String = colorPalette(count Mod colorPalette.Length)  
        count = count + 1  
        mapping.Add(groupingValue, c)  
        Return c  
    End Function  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="665b3-123">您需要用您自己的颜色替换“Color1”。</span><span class="sxs-lookup"><span data-stu-id="665b3-123">You will need to replace the "Color1" strings with your own colors.</span></span> <span data-ttu-id="665b3-124">可以使用命名颜色，例如“Red”，也可以使用表示颜色的六位十六进制值，例如用“#FFFFFF”表示黑色。</span><span class="sxs-lookup"><span data-stu-id="665b3-124">You can use named colors, for example "Red", or you can use six-digit hexadecimal value that represent the color, such as "#FFFFFF" for black.</span></span> <span data-ttu-id="665b3-125">如果已定义三种以上的颜色，则需要扩展颜色数组，以使数组中的颜色数与形状图中的点数匹配。</span><span class="sxs-lookup"><span data-stu-id="665b3-125">If you have more than three colors defined, you will need to extend the array of colors so that the number of colors in the array matches the number of points in your shape chart.</span></span> <span data-ttu-id="665b3-126">通过指定包含命名颜色或颜色的十六进制表示形式、且以逗号分隔的字符串值列表，可以向数组添加新的颜色。</span><span class="sxs-lookup"><span data-stu-id="665b3-126">You can add new colors to the array by specifying a comma-separated list of string values that contain named colors or hexadecimal representations of colors.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="665b3-127">右键单击形状图，然后选择“序列属性”  。</span><span class="sxs-lookup"><span data-stu-id="665b3-127">Right-click on the shape chart and select **Series Properties**.</span></span>  
  
5.  <span data-ttu-id="665b3-128">在“填充”中，单击“表达式”(fx) 按钮可以编辑“颜色”属性的表达式     。</span><span class="sxs-lookup"><span data-stu-id="665b3-128">In **Fill**, click the **Expression** (*fx*) button to edit the expression for the **Color** property.</span></span>  
  
6.  <span data-ttu-id="665b3-129">键入以下表达式，其中“MyCategoryField”是在 **“类别组”** 区域中显示的字段：</span><span class="sxs-lookup"><span data-stu-id="665b3-129">Type the following expression, where "MyCategoryField" is the field that is displayed in the **Category Groups** area:</span></span>  
  
    ```  
    =Code.GetColor(Fields!MyCategoryField)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="665b3-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="665b3-130">See Also</span></span>  
 <span data-ttu-id="665b3-131">[设置图表上序列颜色的格式（报表生成器和 SSRS）](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="665b3-131">[Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="665b3-132">[向图表添加凹凸效果、浮雕和纹理样式（报表生成器和 SSRS）](chart-effects-add-bevel-emboss-or-texture-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="665b3-132">[Add Bevel, Emboss, and Texture Styles to a Chart &#40;Report Builder and SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md) </span></span>  
 <span data-ttu-id="665b3-133">[使用调色板定义图表上的颜色（报表生成器和 SSRS）](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="665b3-133">[Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="665b3-134">[向图表添加空点 &#40;报表生成器和 SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="665b3-134">[Add Empty Points to the Chart &#40;Report Builder and SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="665b3-135">[形状图（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="665b3-135">[Shape Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="665b3-136">[将多个数据区域链接到同一数据集（报表生成器和 SSRS）](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="665b3-136">[Linking Multiple Data Regions to the Same Dataset &#40;Report Builder and SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="665b3-137">[嵌套数据区域（报表生成器和 SSRS）](nested-data-regions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="665b3-137">[Nested Data Regions &#40;Report Builder and SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="665b3-138">迷你图和数据条（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="665b3-138">Sparklines and Data Bars &#40;Report Builder and SSRS&#41;</span></span>](sparklines-and-data-bars-report-builder-and-ssrs.md)  
  
  
