---
title: 更改图表类型（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fff24978-e3bd-4fac-8cd7-d6aa81f3cc25
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fb466bed475b27206bf6837a60d0867f5fb745be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682733"
---
# <a name="change-a-chart-type-report-builder-and-ssrs"></a><span data-ttu-id="68ef5-102">更改图表类型（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="68ef5-102">Change a Chart Type (Report Builder and SSRS)</span></span>
  <span data-ttu-id="68ef5-103">首次将图表插入报表中时，将显示 **“选择图表类型”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="68ef5-103">When you first insert a chart into a report, the **Select Chart Type** dialog appears.</span></span> <span data-ttu-id="68ef5-104">如果取消此对话框，则默认情况下会添加柱形图图表类型。</span><span class="sxs-lookup"><span data-stu-id="68ef5-104">If you cancel this dialog, a Column chart type is added by default.</span></span>  
  
 <span data-ttu-id="68ef5-105">设计报表时，可随时将图表类型更改为某些更适合该报表的类型。</span><span class="sxs-lookup"><span data-stu-id="68ef5-105">At any point when designing the report, you can change the chart type to something more suitable to the report.</span></span> <span data-ttu-id="68ef5-106">为您的数据选择正确的图表类型非常重要，这样才能正确解释该数据。</span><span class="sxs-lookup"><span data-stu-id="68ef5-106">It is important to select the correct chart type for your data so that it can be interpreted correctly.</span></span> <span data-ttu-id="68ef5-107">您应该了解每种图表类型的特征以确定哪种图表类型最适合您的数据。</span><span class="sxs-lookup"><span data-stu-id="68ef5-107">You should understand each chart type's characteristics to determine what chart type is best suited for your data.</span></span> <span data-ttu-id="68ef5-108">有关详细信息，请参阅 [图表类型（报表生成器和 SSRS）](chart-types-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="68ef5-108">For more information, see [Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="68ef5-109">当多个序列显示在图表中时，您可能希望更改各个序列的图表类型。</span><span class="sxs-lookup"><span data-stu-id="68ef5-109">When multiple series are displayed on a chart, you may want to change the chart type of an individual series.</span></span> <span data-ttu-id="68ef5-110">仅当各个序列的图表类型为面积图、柱形图、折线图或散点图时，才能更改图表类型。</span><span class="sxs-lookup"><span data-stu-id="68ef5-110">You can only change the chart type of an individual series if the chart type is Area, Column, Line, or Scatter.</span></span> <span data-ttu-id="68ef5-111">对于所有其他图表类型，图表中的所有序列都将更改为所选图表类型。</span><span class="sxs-lookup"><span data-stu-id="68ef5-111">For all other chart types, all series in your chart will be changed to the selected chart type.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-chart-type"></a><span data-ttu-id="68ef5-112">更改图表类型</span><span class="sxs-lookup"><span data-stu-id="68ef5-112">To change the chart type</span></span>  
  
1.  <span data-ttu-id="68ef5-113">在“设计”视图中，右键单击图表，然后单击“更改图表类型”  。</span><span class="sxs-lookup"><span data-stu-id="68ef5-113">In Design view, right-click the chart and then click **Change Chart Type**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="68ef5-114">有多个序列显示在图表中时，必须右键单击要更改的序列，而不是图表。</span><span class="sxs-lookup"><span data-stu-id="68ef5-114">When there are multiple series on a chart, you must right-click on the series, not the chart, which you want to change.</span></span>  
  
2.  <span data-ttu-id="68ef5-115">在“选择图表类型”  对话框中，从列表中选择图表类型。</span><span class="sxs-lookup"><span data-stu-id="68ef5-115">In the **SelectChart Type** dialog box, select a chart type from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68ef5-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="68ef5-116">See Also</span></span>  
 <span data-ttu-id="68ef5-117">[图表（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="68ef5-117">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="68ef5-118">[仪表（报表生成器和 SSRS）](gauges-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="68ef5-118">[Gauges &#40;Report Builder and SSRS&#41;](gauges-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="68ef5-119">向报表添加图表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="68ef5-119">Add a Chart to a Report &#40;Report Builder and SSRS&#41;</span></span>](add-a-chart-to-a-report-report-builder-and-ssrs.md)  
  
  
