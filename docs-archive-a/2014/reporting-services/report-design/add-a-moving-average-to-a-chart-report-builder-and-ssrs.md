---
title: 向图表添加移动平均线（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 166cf9c1-0750-4866-8381-542e4fbfe65a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9bc16d0cb45a3240148f931009a836c231b442b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577290"
---
# <a name="add-a-moving-average-to-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="de9a3-102">向图表添加移动平均线（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="de9a3-102">Add a Moving Average to a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="de9a3-103">移动平均值是序列中数据的平均值，它是根据定义的时间段内的数据计算的。</span><span class="sxs-lookup"><span data-stu-id="de9a3-103">A moving average is an average of the data in your series, calculated over a defined period of time.</span></span> <span data-ttu-id="de9a3-104">可以在图表中显示移动平均值来标识明显趋势。</span><span class="sxs-lookup"><span data-stu-id="de9a3-104">The moving average can be shown on the chart to identify significant trends.</span></span>  
  
 <span data-ttu-id="de9a3-105">移动平均值公式是技术分析中最常用的价格指标。</span><span class="sxs-lookup"><span data-stu-id="de9a3-105">The Moving Average formula is the most popular price indicator used in technical analyses.</span></span> <span data-ttu-id="de9a3-106">包括平均值、中值和标准偏差在内的许多其他公式也可以从图表的序列中派生。</span><span class="sxs-lookup"><span data-stu-id="de9a3-106">Many other formulas, including mean, median and standard deviation, can also be derived from a series on the chart.</span></span> <span data-ttu-id="de9a3-107">指定移动平均值时，每个公式可能有一个或多个必须指定的参数。</span><span class="sxs-lookup"><span data-stu-id="de9a3-107">When specifying a moving average, each formula may have one or more parameters that must be specified.</span></span>  
  
 <span data-ttu-id="de9a3-108">在设计模式下添加移动平均值公式时，添加的行序列只会显示为占位符。</span><span class="sxs-lookup"><span data-stu-id="de9a3-108">When a moving average formula is added in Design mode, the line series that is added is only a visual placeholder.</span></span> <span data-ttu-id="de9a3-109">该图表将在报表处理期间计算每个公式的数据点。</span><span class="sxs-lookup"><span data-stu-id="de9a3-109">The chart will calculate the data points of each formula during report processing.</span></span>  
  
 <span data-ttu-id="de9a3-110">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]中不提供对趋势线的内置支持。</span><span class="sxs-lookup"><span data-stu-id="de9a3-110">Built-in support for trend lines is not available in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-calculated-moving-average-to-a-series-on-the-chart"></a><span data-ttu-id="de9a3-111">将计算的移动平均值添加到图表的序列</span><span class="sxs-lookup"><span data-stu-id="de9a3-111">To add a calculated moving average to a series on the chart</span></span>  
  
1.  <span data-ttu-id="de9a3-112">右键单击“ **值** ”区域中的字段，然后单击“ **添加计算序列**”。</span><span class="sxs-lookup"><span data-stu-id="de9a3-112">Right-click on a field in the **Values** area and click **Add Calculated Series**.</span></span> <span data-ttu-id="de9a3-113">随即打开 **“计算序列属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="de9a3-113">The **Calculated Series Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="de9a3-114">从“ **公式** ”下拉列表中选择“ **移动平均值** ”选项。</span><span class="sxs-lookup"><span data-stu-id="de9a3-114">Select the **Moving average** option from the **Formula** drop-down list.</span></span>  
  
3.  <span data-ttu-id="de9a3-115">为表示移动平均值期间的 **“期间”** 指定一个整数值。</span><span class="sxs-lookup"><span data-stu-id="de9a3-115">Specify an integer value for the **Period** that represents the period of the moving average.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="de9a3-116">期间是用来计算移动平均值的天数。</span><span class="sxs-lookup"><span data-stu-id="de9a3-116">The period is the number of days used to calculate a moving average.</span></span> <span data-ttu-id="de9a3-117">如果未在 X 轴上指定日期／时间值，该期间将由用于计算移动平均值的数据点的数量来表示。</span><span class="sxs-lookup"><span data-stu-id="de9a3-117">If date/time values are not specified on the x-axis, the period is represented by the number of data points used to calculate a moving average.</span></span> <span data-ttu-id="de9a3-118">如果只有一个数据点，移动平均值公式将不会进行计算。</span><span class="sxs-lookup"><span data-stu-id="de9a3-118">If there is only one data point, the moving average formula does not calculate.</span></span> <span data-ttu-id="de9a3-119">移动平均值从第二个点处开始计算。</span><span class="sxs-lookup"><span data-stu-id="de9a3-119">The moving average is calculated starting at the second point.</span></span> <span data-ttu-id="de9a3-120">如果您指定 **“从第一点开始”** 选项，则图表将从第一个点处的移动平均值开始。</span><span class="sxs-lookup"><span data-stu-id="de9a3-120">If you specify the **Start from first point** option, the chart will start the moving average at the first point.</span></span> <span data-ttu-id="de9a3-121">如果只有一个数据点，则计算出的移动平均值中的点将与原始序列中的第一个点一致。</span><span class="sxs-lookup"><span data-stu-id="de9a3-121">If there is only one data point, the point in the calculated moving average will be identical to the first point in your original series.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de9a3-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="de9a3-122">See Also</span></span>  
 <span data-ttu-id="de9a3-123">[设置图表格式 &#40;报表生成器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="de9a3-123">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="de9a3-124">[图表 &#40;报表生成器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="de9a3-124">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="de9a3-125">向图表添加空点 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="de9a3-125">Add Empty Points to the Chart &#40;Report Builder and SSRS&#41;</span></span>](add-empty-points-to-a-chart-report-builder-and-ssrs.md)  
  
  
