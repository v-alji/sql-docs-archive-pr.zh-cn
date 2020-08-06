---
title: 设置仪表上范围的格式（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ffdec8ca-3e95-41cd-850b-9e8c83be4b49
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 29574c58eef6f18d685b48dd8d695a5fc42c3e6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682713"
---
# <a name="formatting-ranges-on-a-gauge-report-builder-and-ssrs"></a><span data-ttu-id="061c2-102">设置仪表上范围的格式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="061c2-102">Formatting Ranges on a Gauge (Report Builder and SSRS)</span></span>
  <span data-ttu-id="061c2-103">仪表范围是仪表刻度上的带区或区域，用于指示仪表上一段重要的值。</span><span class="sxs-lookup"><span data-stu-id="061c2-103">A gauge range is a zone or area on the gauge scale that indicates an important subsection of values on the gauge.</span></span> <span data-ttu-id="061c2-104">使用仪表范围，能以可见方式指示指针值何时进入某个值范围。</span><span class="sxs-lookup"><span data-stu-id="061c2-104">Using a gauge range, you can visually indicate when the pointer value has gone into a certain span of values.</span></span> <span data-ttu-id="061c2-105">范围由开始值和结束值定义。</span><span class="sxs-lookup"><span data-stu-id="061c2-105">Ranges are defined by a start value and an end value.</span></span>  
  
 <span data-ttu-id="061c2-106">还可以使用范围来定义仪表的各个不同分段。</span><span class="sxs-lookup"><span data-stu-id="061c2-106">You can also use ranges to define different sections of a gauge.</span></span> <span data-ttu-id="061c2-107">例如，在值从 0 到 10 的仪表上，可以定义从 0 到 3 的值为红色范围，从 4 到 7 的值为黄色范围，从 8 到 10 的值为绿色范围。</span><span class="sxs-lookup"><span data-stu-id="061c2-107">For example, on a gauge with values from 0 to 10, you can define a red range that has a value from 0 to 3, a yellow range that has a value from 4 to 7 and a green range that has a value from 8 to 10.</span></span> <span data-ttu-id="061c2-108">如果指定的开始值大于指定的结束值，则值将交换，以使开始值成为结束值，而结束值成为开始值。</span><span class="sxs-lookup"><span data-stu-id="061c2-108">If the start value that you specified is greater than the end value that you specified, the values are swapped so that the start value is the end value and the end value is the start value.</span></span>  
  
 <span data-ttu-id="061c2-109">可以使用在刻度上放置指针的相同方式来设置范围。</span><span class="sxs-lookup"><span data-stu-id="061c2-109">You can position the range in the same way that you position pointers on a scale.</span></span> <span data-ttu-id="061c2-110">**“位置”** 和 **“到刻度的距离”** 属性可确定范围的位置。</span><span class="sxs-lookup"><span data-stu-id="061c2-110">The **Position** and **Distance from scale** properties determine the position of the range.</span></span> <span data-ttu-id="061c2-111">有关详细信息，请参阅 [仪表（报表生成器和 SSRS）](gauges-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="061c2-111">For more information, see [Gauges &#40;Report Builder and SSRS&#41;](gauges-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="061c2-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="061c2-112">See Also</span></span>  
 <span data-ttu-id="061c2-113">[设置仪表上刻度的格式（报表生成器和 SSRS）](formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="061c2-113">[Formatting Scales on a Gauge &#40;Report Builder and SSRS&#41;](formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="061c2-114">[设置仪表上指针的格式（报表生成器和 SSRS）](formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="061c2-114">[Formatting Pointers on a Gauge &#40;Report Builder and SSRS&#41;](formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="061c2-115">[设置仪表的最小值或最大值（报表生成器和 SSRS）](set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="061c2-115">[Set a Minimum or Maximum on a Gauge &#40;Report Builder and SSRS&#41;](set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="061c2-116">[教程：向报表添加 KPI（报表生成器）](../tutorial-adding-a-kpi-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="061c2-116">[Tutorial: Adding a KPI to Your Report &#40;Report Builder&#41;](../tutorial-adding-a-kpi-to-your-report-report-builder.md) </span></span>  
 [<span data-ttu-id="061c2-117">仪表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="061c2-117">Gauges &#40;Report Builder and SSRS&#41;</span></span>](gauges-report-builder-and-ssrs.md)  
  
  
