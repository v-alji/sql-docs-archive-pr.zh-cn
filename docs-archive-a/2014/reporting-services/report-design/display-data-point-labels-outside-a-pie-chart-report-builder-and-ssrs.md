---
title: 在饼图外显示数据点标签（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 959b7574-cf43-470b-b592-4944d8a9948f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dd4f38f24d2729acacfa3520635b93d8af2e9433
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691622"
---
# <a name="display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs"></a><span data-ttu-id="dc839-102">在饼图外显示数据点标签（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="dc839-102">Display Data Point Labels Outside a Pie Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="dc839-103">在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]中，饼图标签经过了优化，可以仅在几个数据切片中显示标签。</span><span class="sxs-lookup"><span data-stu-id="dc839-103">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], pie chart labeling is optimized to display labels on only several slices of data.</span></span> <span data-ttu-id="dc839-104">如果饼图包含的切片过多，标签可能会重叠。</span><span class="sxs-lookup"><span data-stu-id="dc839-104">Labels may overlap if the pie chart contains too many slices.</span></span> <span data-ttu-id="dc839-105">一种解决方案是在饼图外显示标签，这样可能会为较长的数据标签留出更多的空间。</span><span class="sxs-lookup"><span data-stu-id="dc839-105">One solution is to display the labels outside the pie chart, which may create more room for longer data labels.</span></span> <span data-ttu-id="dc839-106">如果发现标签仍然重叠，可以启用三维来为这些标签留出更多的空间。</span><span class="sxs-lookup"><span data-stu-id="dc839-106">If you find that your labels still overlap, you can create more space for them by enabling 3D.</span></span> <span data-ttu-id="dc839-107">这将减小饼图的直径，在饼图周围留出更多的空间。</span><span class="sxs-lookup"><span data-stu-id="dc839-107">This reduces the diameter of the pie chart, creating more space around the chart.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-data-point-labels-inside-a-pie-chart"></a><span data-ttu-id="dc839-108">在饼图内显示数据点标签</span><span class="sxs-lookup"><span data-stu-id="dc839-108">To display data point labels inside a pie chart</span></span>  
  
1.  <span data-ttu-id="dc839-109">向报表添加一个饼图。</span><span class="sxs-lookup"><span data-stu-id="dc839-109">Add a pie chart to your report.</span></span> <span data-ttu-id="dc839-110">有关详细信息，请参阅[向报表添加图表（报表生成器和 SSRS）](add-a-chart-to-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="dc839-110">For more information, see [Add a Chart to a Report &#40;Report Builder and SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="dc839-111">在设计图面上，右键单击图表并选择“显示数据标签”  。</span><span class="sxs-lookup"><span data-stu-id="dc839-111">On the design surface, right-click on the chart and select **Show Data Labels**.</span></span>  
  
### <a name="to-display-data-point-labels-outside-a-pie-chart"></a><span data-ttu-id="dc839-112">在饼图外显示数据点标签</span><span class="sxs-lookup"><span data-stu-id="dc839-112">To display data point labels outside a pie chart</span></span>  
  
1.  <span data-ttu-id="dc839-113">创建一个饼图，并显示数据标签。</span><span class="sxs-lookup"><span data-stu-id="dc839-113">Create a pie chart and display the data labels.</span></span>  
  
2.  <span data-ttu-id="dc839-114">打开“属性”窗格。</span><span class="sxs-lookup"><span data-stu-id="dc839-114">Open the Properties pane.</span></span>  
  
3.  <span data-ttu-id="dc839-115">在设计图面上，单击饼图本身以在“属性”窗格中显示 **“类别”** 属性。</span><span class="sxs-lookup"><span data-stu-id="dc839-115">On the design surface, click on the pie itself to display the **Category** properties in the Properties pane.</span></span>  
  
4.  <span data-ttu-id="dc839-116">展开 **CustomAttributes** 节点。</span><span class="sxs-lookup"><span data-stu-id="dc839-116">Expand the **CustomAttributes** node.</span></span> <span data-ttu-id="dc839-117">此时将显示该饼图的属性列表。</span><span class="sxs-lookup"><span data-stu-id="dc839-117">A list of attributes for the pie chart is displayed.</span></span>  
  
5.  <span data-ttu-id="dc839-118">将 **PieLabelStyle** 属性设置为 **Outside**。</span><span class="sxs-lookup"><span data-stu-id="dc839-118">Set the **PieLabelStyle** property to **Outside**.</span></span>  
  
6.  <span data-ttu-id="dc839-119">将 `PieLineColor` 属性设置为**黑色**。</span><span class="sxs-lookup"><span data-stu-id="dc839-119">Set the `PieLineColor` property to **Black**.</span></span> <span data-ttu-id="dc839-120">PieLineColor 属性可为每个数据点标签定义标注线条。</span><span class="sxs-lookup"><span data-stu-id="dc839-120">The PieLineColor property defines callout lines for each data point label.</span></span>  
  
### <a name="to-prevent-overlapping-labels-displayed-outside-a-pie-chart"></a><span data-ttu-id="dc839-121">防止在饼图外显示的标签重叠</span><span class="sxs-lookup"><span data-stu-id="dc839-121">To prevent overlapping labels displayed outside a pie chart</span></span>  
  
1.  <span data-ttu-id="dc839-122">创建一个带有外部标签的饼图。</span><span class="sxs-lookup"><span data-stu-id="dc839-122">Create a pie chart with external labels.</span></span>  
  
2.  <span data-ttu-id="dc839-123">在设计图面上，在饼图外部但在饼图边界之内右键单击，然后选择“图表区域属性”  。随即将显示“图表区域属性”  对话框。</span><span class="sxs-lookup"><span data-stu-id="dc839-123">On the design surface, right-click outside the pie chart but inside the chart borders and select **Chart Area Properties**.The **Chart AreaProperties** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="dc839-124">在 **“三维选项”** 选项卡上，选择 **“启用三维”** 。</span><span class="sxs-lookup"><span data-stu-id="dc839-124">On the **3D Options** tab, select **Enable 3D**.</span></span>  
  
4.  <span data-ttu-id="dc839-125">如果希望图表为标签留出更多空间但仍显示二维效果，则将“旋转”  和“倾角”  属性设置为“0”  。</span><span class="sxs-lookup"><span data-stu-id="dc839-125">If you want the chart to have more room for labels but still appear two-dimensional, set the **Rotation** and **Inclination** properties to **0**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc839-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dc839-126">See Also</span></span>  
 <span data-ttu-id="dc839-127">[饼图（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dc839-127">[Pie Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="dc839-128">[收集饼图上的小切片（报表生成器和 SSRS）](collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dc839-128">[Collect Small Slices on a Pie Chart &#40;Report Builder and SSRS&#41;](collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="dc839-129">在饼图上显示百分比值（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="dc839-129">Display Percentage Values on a Pie Chart &#40;Report Builder and SSRS&#41;</span></span>](display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md)  
  
  
