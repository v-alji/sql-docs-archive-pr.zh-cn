---
title: 通过添加带状线突出显示图表数据（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: addd6137-4b6e-4e88-a7e8-9600fcd1ccce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 01b0bb41a71daf9ac558ce8d8bb84480426870c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578633"
---
# <a name="highlight-chart-data-by-adding-strip-lines-report-builder-and-ssrs"></a><span data-ttu-id="3c905-102">通过添加条带线突出显示图表数据（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="3c905-102">Highlight Chart Data by Adding Strip Lines (Report Builder and SSRS)</span></span>
  <span data-ttu-id="3c905-103">条带线（或条带）是按固定或自定义间隔使图表背景带有阴影的水平或垂直区域。</span><span class="sxs-lookup"><span data-stu-id="3c905-103">Strip lines, or strips, are horizontal or vertical ranges that shade the background of the chart in regular or custom intervals.</span></span> <span data-ttu-id="3c905-104">可以使用条带线执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="3c905-104">You can use strip lines to:</span></span>  
  
-   <span data-ttu-id="3c905-105">提高在图表上查找各个值时的可读性。</span><span class="sxs-lookup"><span data-stu-id="3c905-105">Improve readability for looking up individual values on the chart.</span></span> <span data-ttu-id="3c905-106">指定固定间隔的条带线有助于读取该图表时分离数据点。</span><span class="sxs-lookup"><span data-stu-id="3c905-106">Specify strip lines at regular intervals to help separate data points when reading the chart.</span></span>  
  
-   <span data-ttu-id="3c905-107">突出显示定期出现的日期。</span><span class="sxs-lookup"><span data-stu-id="3c905-107">Highlight dates that occur at regular intervals.</span></span> <span data-ttu-id="3c905-108">例如，在销售报表中，可能会使用条带线标识周末数据点。</span><span class="sxs-lookup"><span data-stu-id="3c905-108">For example, in a sales report you might use strip lines to identify weekend data points.</span></span>  
  
-   <span data-ttu-id="3c905-109">突出显示特定键范围。</span><span class="sxs-lookup"><span data-stu-id="3c905-109">Highlight a specific key range.</span></span> <span data-ttu-id="3c905-110">在上一示例中，可以使用一根条带线突出显示 80-100 美元之间的最高销售额区域。</span><span class="sxs-lookup"><span data-stu-id="3c905-110">Using the previous example, you can use one strip line to highlight the highest range of sales that is between $80-100.</span></span>  
  
 <span data-ttu-id="3c905-111">条带线不适用于极坐标图或形状图类型。</span><span class="sxs-lookup"><span data-stu-id="3c905-111">Strip lines are not applicable to Shape or Polar chart types.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-interlaced-strip-lines-at-regular-intervals-on-a-chart"></a><span data-ttu-id="3c905-112">在图表上按固定间隔显示交错条带线</span><span class="sxs-lookup"><span data-stu-id="3c905-112">To display interlaced strip lines at regular intervals on a chart</span></span>  
  
1.  <span data-ttu-id="3c905-113">若要显示水平带状线，请右键单击垂直图表轴，然后单击“垂直轴属性”  。</span><span class="sxs-lookup"><span data-stu-id="3c905-113">To show horizontal strip lines, right-click the vertical chart axis and click **VerticalAxis Properties**.</span></span>  
  
     <span data-ttu-id="3c905-114">若要显示垂直带状线，请右键单击水平图表轴，然后单击“水平轴属性”  。</span><span class="sxs-lookup"><span data-stu-id="3c905-114">To show vertical strip lines, right-click the horizontal chart axis and click **Horizontal Axis Properties**.</span></span>  
  
2.  <span data-ttu-id="3c905-115">选择 **“使用交错”** 选项。</span><span class="sxs-lookup"><span data-stu-id="3c905-115">Select the **Use interlacing** option.</span></span> <span data-ttu-id="3c905-116">图表上将显示灰色条带线。</span><span class="sxs-lookup"><span data-stu-id="3c905-116">Grey strip lines will appear on your chart.</span></span>  
  
3.  <span data-ttu-id="3c905-117">（可选）使用相邻的“颜色”  下拉列表指定带状线的颜色。</span><span class="sxs-lookup"><span data-stu-id="3c905-117">(Optional) Specify a color for the strip lines using the adjacent **Color** drop-down list.</span></span>  
  
### <a name="to-display-interlaced-strip-lines-at-custom-intervals-on-a-chart"></a><span data-ttu-id="3c905-118">在图表上按自定义间隔显示交错条带线</span><span class="sxs-lookup"><span data-stu-id="3c905-118">To display interlaced strip lines at custom intervals on a chart</span></span>  
  
1.  <span data-ttu-id="3c905-119">若要显示水平带状线，请右键单击垂直图表轴，然后单击“垂直轴属性”  。</span><span class="sxs-lookup"><span data-stu-id="3c905-119">To show horizontal strip lines, right-click the vertical chart axis and click **VerticalAxis Properties**.</span></span>  
  
     <span data-ttu-id="3c905-120">若要显示垂直带状线，请右键单击水平图表轴，然后单击“水平轴属性”  。</span><span class="sxs-lookup"><span data-stu-id="3c905-120">To show vertical strip lines, right-click the horizontal chart axis and click **Horizontal Axis Properties**.</span></span>  
  
     <span data-ttu-id="3c905-121">轴属性将显示在“属性”窗口中。</span><span class="sxs-lookup"><span data-stu-id="3c905-121">The axis properties are displayed in the Properties window.</span></span>  
  
2.  <span data-ttu-id="3c905-122">在“属性”窗格的“外观”部分的 StripLines 属性中，单击“编辑集合(…)”按钮打开“ChartStripLine 集合编辑器”   。</span><span class="sxs-lookup"><span data-stu-id="3c905-122">In the **Appearance** section of the Properties pane, for the StripLines property, click the Edit Collection (...) button to open the **ChartStripLine Collection Editor**.</span></span>  
  
3.  <span data-ttu-id="3c905-123">单击 **“添加”** 向集合中添加一个新条带线。</span><span class="sxs-lookup"><span data-stu-id="3c905-123">Click **Add** to add a new strip line to the collection.</span></span>  
  
4.  <span data-ttu-id="3c905-124">单击 StripWidth 可指定报表上带状线的宽度（以英寸为单位）。</span><span class="sxs-lookup"><span data-stu-id="3c905-124">Click StripWidth to specify the width of the strip line, measured in inches on the report.</span></span> <span data-ttu-id="3c905-125">如果是突出显示日期或时间，请单击 StripWidthType，然后选择一个时间间隔。</span><span class="sxs-lookup"><span data-stu-id="3c905-125">If you are highlighting dates or times, click StripWidthType and select a time interval.</span></span>  
  
5.  <span data-ttu-id="3c905-126">键入 Interval 的值或表达式以指定带状线的重复显示频率。</span><span class="sxs-lookup"><span data-stu-id="3c905-126">Type a value or expression for the Interval to specify how often the strip line will repeat.</span></span>  <span data-ttu-id="3c905-127">例如，如果指定间隔为 10，条带线宽度为 5，则条带线将在 0 到 5、15 到 20、30 到 35 等处显示。</span><span class="sxs-lookup"><span data-stu-id="3c905-127">For example, if you specify an interval of 10, and your strip line width is 5, strip lines will display at values of 0 to 5, 15 to 20, 30 to 35, and so on.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3c905-128">默认情况下，Interval 设置为“自动”，这表示图表将不计算自定义带状线的间隔。</span><span class="sxs-lookup"><span data-stu-id="3c905-128">By default, Interval is set to Auto, which means the chart will not calculate an interval for custom strip lines.</span></span> <span data-ttu-id="3c905-129">仅当设置间隔值后图表才计算条带线的间隔。</span><span class="sxs-lookup"><span data-stu-id="3c905-129">The chart only calculates intervals for strip lines if an interval value is set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c905-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3c905-130">See Also</span></span>  
 <span data-ttu-id="3c905-131">[设置图表上轴标签的格式（报表生成器和 SSRS）](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3c905-131">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3c905-132">[设置图表格式（报表生成器和 SSRS）](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3c905-132">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="3c905-133">向图表添加移动平均线（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="3c905-133">Add a Moving Average to a Chart &#40;Report Builder and SSRS&#41;</span></span>](add-a-moving-average-to-a-chart-report-builder-and-ssrs.md)  
  
  
