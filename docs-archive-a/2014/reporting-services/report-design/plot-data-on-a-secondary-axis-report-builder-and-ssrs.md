---
title: 在辅助轴上绘制数据（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 094f39bf-3634-4852-9fc3-3adec4b266e5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cec58820e0373bb1e9ef2d50d022e5b4ef7e962b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682676"
---
# <a name="plot-data-on-a-secondary-axis-report-builder-and-ssrs"></a><span data-ttu-id="b6007-102">在辅助轴上绘制数据（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="b6007-102">Plot Data on a Secondary Axis (Report Builder and SSRS)</span></span>
  <span data-ttu-id="b6007-103">图表有两个轴类型：主轴和辅助轴。</span><span class="sxs-lookup"><span data-stu-id="b6007-103">The chart has two axis types: primary and secondary.</span></span> <span data-ttu-id="b6007-104">将两个值集与共享共有类别的两个不同数据范围进行比较时，辅助轴将非常有用。</span><span class="sxs-lookup"><span data-stu-id="b6007-104">The secondary axis is useful when comparing two value sets with two distinct data ranges that share a common category.</span></span>  
  
 <span data-ttu-id="b6007-105">例如，假设您有一个计算 2008 年 Revenue 和 Tax 的图表。</span><span class="sxs-lookup"><span data-stu-id="b6007-105">For example, suppose you have a chart that calculates Revenue vs. Tax for the year 2008.</span></span> <span data-ttu-id="b6007-106">在这种情况下，对于这两个值集而言，2008 年这一时间段是它们共有的。</span><span class="sxs-lookup"><span data-stu-id="b6007-106">In this case, the 2008 time period is common to both value sets.</span></span> <span data-ttu-id="b6007-107">但是，在同一个 Y 轴上绘制这两个序列时，我们无法进行有用的比较，因为 Y 轴上的刻度已针对数据集中的最大值进行了优化。</span><span class="sxs-lookup"><span data-stu-id="b6007-107">However, when both series are plotted on the same y-axis, we cannot make a useful comparison because the scale of the y-axis is optimized for the largest values in the dataset.</span></span> <span data-ttu-id="b6007-108">如果在主轴上显示 Revenue，在辅助轴上显示 Tax，则可以在每个序列各自的 Y 轴上分别显示它们，并显示其各自的值范围。</span><span class="sxs-lookup"><span data-stu-id="b6007-108">If we show Revenue on the primary axis, and Tax on the secondary axis, we can display each series on its own y-axis with its own scale of values.</span></span> <span data-ttu-id="b6007-109">序列仍共享共有的 X 轴。</span><span class="sxs-lookup"><span data-stu-id="b6007-109">The series still share a common x-axis.</span></span>  
  
 <span data-ttu-id="b6007-110">在需要对两种以上的序列进行比较的情况下，可考虑使用不同的方法来在图表中比较和显示多个序列。</span><span class="sxs-lookup"><span data-stu-id="b6007-110">In situations where there are more than two series to be compared, consider a different approach for comparing and displaying multiple series in a chart.</span></span> <span data-ttu-id="b6007-111">有关详细信息，请参阅 [图表中的多个序列（报表生成器和 SSRS）](multiple-series-on-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="b6007-111">For more information, see [Multiple Series on a Chart &#40;Report Builder and SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="b6007-112">此图表的示例可用于示例报表。</span><span class="sxs-lookup"><span data-stu-id="b6007-112">An example of this chart is available as a sample report.</span></span> <span data-ttu-id="b6007-113">有关下载此示例报表和其他内容的详细信息，请参阅 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [报表生成器和报表设计器示例报表](https://go.microsoft.com/fwlink/?LinkId=198283)。</span><span class="sxs-lookup"><span data-stu-id="b6007-113">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-plot-a-series-on-the-secondary-axis"></a><span data-ttu-id="b6007-114">在辅助轴上绘制序列</span><span class="sxs-lookup"><span data-stu-id="b6007-114">To plot a series on the secondary axis</span></span>  
  
1.  <span data-ttu-id="b6007-115">右键单击图表中的序列，或右键单击要在辅助轴上显示的 **“值”** 区域中的某个字段，然后单击 **“序列属性”** 。</span><span class="sxs-lookup"><span data-stu-id="b6007-115">Right-click the series in the chart or right-click on a field in the **Values** area that you want to display on the secondary axis and click **Series Properties**.</span></span> <span data-ttu-id="b6007-116">随即出现 **“序列属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="b6007-116">The **Series Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="b6007-117">单击 **“轴和图表区”** ，然后选择要启用的辅助轴、值轴或类别轴。</span><span class="sxs-lookup"><span data-stu-id="b6007-117">Click **Axes and Chart Area**, and select which of the secondary axes you want to enable, the value axis or the category axis.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6007-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b6007-118">See Also</span></span>  
 <span data-ttu-id="b6007-119">[设置图表上轴标签的格式 &#40;报表生成器和 SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b6007-119">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="b6007-120">指定轴间隔（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="b6007-120">Specify an Axis Interval &#40;Report Builder and SSRS&#41;</span></span>](specify-an-axis-interval-report-builder-and-ssrs.md)  
  
  
