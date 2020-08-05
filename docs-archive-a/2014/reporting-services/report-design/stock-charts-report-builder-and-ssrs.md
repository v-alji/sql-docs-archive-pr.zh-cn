---
title: 股价图（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f75ca11e-b7f5-4ac0-ba17-fe6f82742dad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a0f8c9c7dbc750bdb477f2ea1d96aa03f7ad022f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577254"
---
# <a name="stock-charts-report-builder-and-ssrs"></a><span data-ttu-id="64411-102">股价图（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="64411-102">Stock Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="64411-103">股价图是为每个数据点使用多达四个值的财务或科学数据而专门设计的。</span><span class="sxs-lookup"><span data-stu-id="64411-103">A stock chart is specifically designed for financial or scientific data that uses up to four values per data point.</span></span> <span data-ttu-id="64411-104">这些值与用于绘制财务股价数据的高、低、开盘和收盘值相对应。</span><span class="sxs-lookup"><span data-stu-id="64411-104">These values align with the high, low, open and close values that are used to plot financial stock data.</span></span> <span data-ttu-id="64411-105">这种图表类型通过使用标记（通常为线条或三角形）来显示开盘值和收盘值。</span><span class="sxs-lookup"><span data-stu-id="64411-105">This chart type displays opening and closing values by using markers, which are typically lines or triangles.</span></span> <span data-ttu-id="64411-106">在下例中，开盘值由左侧的标记表示，收盘值由右侧的标记表示。</span><span class="sxs-lookup"><span data-stu-id="64411-106">In the following example, the opening values are shown by the markers on the left, and the closing values are shown by the markers on the right.</span></span>  
  
 <span data-ttu-id="64411-107">![股价图](../media/rs-stockchart.gif "股价图")</span><span class="sxs-lookup"><span data-stu-id="64411-107">![Stock chart](../media/rs-stockchart.gif "Stock chart")</span></span>  
  
 <span data-ttu-id="64411-108">股价图的示例可用于示例 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 报表生成器报表。</span><span class="sxs-lookup"><span data-stu-id="64411-108">An example of a stock chart is available as a sample [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] Report Builder report.</span></span> <span data-ttu-id="64411-109">有关下载此示例报表和其他内容的详细信息，请参阅 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] [报表生成器和报表设计器示例报表](https://go.microsoft.com/fwlink/?LinkId=198283)。</span><span class="sxs-lookup"><span data-stu-id="64411-109">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="64411-110">变体</span><span class="sxs-lookup"><span data-stu-id="64411-110">Variations</span></span>  
  
-   <span data-ttu-id="64411-111">**K 线图**。</span><span class="sxs-lookup"><span data-stu-id="64411-111">**Candlestick**.</span></span> <span data-ttu-id="64411-112">K 线图是一种专用形式的股价图，其中的框用于说明开盘值与收盘值之间的范围。</span><span class="sxs-lookup"><span data-stu-id="64411-112">The candlestick chart is a specialized form of the stock chart, wherein boxes are used to show the range between the open and close values.</span></span> <span data-ttu-id="64411-113">与股价图相似，K 线图可以针对每个数据点显示多达四个值。</span><span class="sxs-lookup"><span data-stu-id="64411-113">Like the stock chart, the candlestick chart can display up to four values per data point.</span></span>  
  
## <a name="data-considerations-for-stock-charts"></a><span data-ttu-id="64411-114">股价图的数据注意事项</span><span class="sxs-lookup"><span data-stu-id="64411-114">Data Considerations for Stock Charts</span></span>  
  
-   <span data-ttu-id="64411-115">当显示多个股价数据点（例如年股价趋势）时，若要区分每个数据点的每个开盘值、收盘值、高值和低值，这是十分困难的。</span><span class="sxs-lookup"><span data-stu-id="64411-115">When presenting many stock data points, such as annual stock price trend, it is difficult to distinguish each open, close, high and low value of each data point.</span></span> <span data-ttu-id="64411-116">此时应考虑使用折线图而不是股价图。</span><span class="sxs-lookup"><span data-stu-id="64411-116">In this scenario, consider using a line chart instead of a stock chart.</span></span>  
  
-   <span data-ttu-id="64411-117">当生成轴标签时，标记通常从零开始。</span><span class="sxs-lookup"><span data-stu-id="64411-117">When axis labels are generated, labeling usually begins at zero.</span></span>  <span data-ttu-id="64411-118">一般而言，股价与其他数据集的波动程度不同。</span><span class="sxs-lookup"><span data-stu-id="64411-118">In general, stock prices do not fluctuate to the same degree as other data sets.</span></span> <span data-ttu-id="64411-119">因此，可能希望禁用从零开始的轴标签，以便获得更好的数据视图。</span><span class="sxs-lookup"><span data-stu-id="64411-119">For this reason, you may want to disable the axis labels from starting at zero, in order to get a better view of your data.</span></span> <span data-ttu-id="64411-120">若要实现此目的，请在 **“轴属性”** 或“属性”窗口中将 **IncludeZero** 设置为 **false** 。</span><span class="sxs-lookup"><span data-stu-id="64411-120">To do this, set **IncludeZero** to **false** in the **Axis Properties** dialog box or the Properties window.</span></span> <span data-ttu-id="64411-121">有关图表如何生成轴标签的详细信息，请参阅[设置图表上轴标签的格式（报表生成器和 SSRS）](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="64411-121">For more information about how the chart generates axis labels, see [Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="64411-122">提供了许多用于股价图的计算公式，包括价格指标、相对强弱指数、MACD 等。</span><span class="sxs-lookup"><span data-stu-id="64411-122">provides many calculated formulas for use with stock charts, including Price Indicator, Relative Strength Index, MACD and more.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64411-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="64411-123">See Also</span></span>  
 <span data-ttu-id="64411-124">[范围图 &#40;报表生成器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="64411-124">[Range Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="64411-125">[图表 &#40;报表生成器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="64411-125">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="64411-126">[设置图表格式 &#40;报表生成器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="64411-126">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="64411-127">“轴属性”对话框 -&gt;“轴选项”（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="64411-127">Axis Properties Dialog Box, Axis Options &#40;Report Builder and SSRS&#41;</span></span>](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md)  
  
  
