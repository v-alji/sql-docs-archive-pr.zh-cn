---
title: 在仪表 (报表生成器和 SSRS) 上设置对齐间隔 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0ece7297-6e2f-47fb-835d-b9e9cce53fe2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bdc2a621c4406791838d97e93f47cd32fa9d5f94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691048"
---
# <a name="set-a-snapping-interval-on-a-gauge-report-builder-and-ssrs"></a><span data-ttu-id="21c65-102">在仪表上设置对齐间隔（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="21c65-102">Set a Snapping Interval on a Gauge (Report Builder and SSRS)</span></span>
  <span data-ttu-id="21c65-103">对齐间隔定义一个数值，舍入后的值是它的倍数。</span><span class="sxs-lookup"><span data-stu-id="21c65-103">A snapping interval defines the multiple to which values are rounded.</span></span> <span data-ttu-id="21c65-104">默认情况下，仪表将指向已在数据窗格中指定的字段的精确值。</span><span class="sxs-lookup"><span data-stu-id="21c65-104">By default, the gauge will point to the exact value of the field you have specified in the data pane.</span></span> <span data-ttu-id="21c65-105">但是，您可能希望该精确值向上舍入或向下舍入，以便指针与预设的间隔对齐。</span><span class="sxs-lookup"><span data-stu-id="21c65-105">However, you may want to round the exact value up or down so that the pointer will snap to a preset interval.</span></span> <span data-ttu-id="21c65-106">例如，如果仪表上的值为 34.2 并且您将对齐间隔指定为 5，则仪表指针将指向 35。</span><span class="sxs-lookup"><span data-stu-id="21c65-106">For example, if the value on your gauge is 34.2 and you specify a snapping interval of 5, the gauge pointer will point to 35.</span></span> <span data-ttu-id="21c65-107">如果仪表上的值为 31.2 并且您将对齐间隔指定为 5，则仪表指针将指向 30。</span><span class="sxs-lookup"><span data-stu-id="21c65-107">If the value on your gauge is 31.2 and you specify a snapping interval of 5, the gauge pointer will point to 30.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-a-snapping-interval-on-a-gauge"></a><span data-ttu-id="21c65-108">在仪表上设置对齐间隔</span><span class="sxs-lookup"><span data-stu-id="21c65-108">To set a snapping interval on a gauge</span></span>  
  
1.  <span data-ttu-id="21c65-109">单击仪表上的任意数字，以突出显示刻度。</span><span class="sxs-lookup"><span data-stu-id="21c65-109">Click anywhere on the numbers of the gauge to highlight the scale.</span></span>  
  
2.  <span data-ttu-id="21c65-110">打开“属性”窗格。</span><span class="sxs-lookup"><span data-stu-id="21c65-110">Open the Properties pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="21c65-111">如果看不到 "属性" 窗格，请单击 "**查看**" 选项卡，然后选中 "**属性**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="21c65-111">If you do not see the Properties pane, click the **View** tab and then select the **Properties** checkbox.</span></span>  
  
3.  <span data-ttu-id="21c65-112">在 "**指针**" 属性中，单击 " ( ..." ) "按钮。</span><span class="sxs-lookup"><span data-stu-id="21c65-112">In the **Pointers** property, click the (...) button.</span></span> <span data-ttu-id="21c65-113">此时将打开指针集合编辑器。</span><span class="sxs-lookup"><span data-stu-id="21c65-113">The Pointer Collection Editor opens.</span></span>  
  
4.  <span data-ttu-id="21c65-114">将**SnappingEnabled**属性设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="21c65-114">Set the **SnappingEnabled** property to `True`.</span></span>  
  
5.  <span data-ttu-id="21c65-115">将**SnappingInterval**设置为一个表示对齐间隔的值。</span><span class="sxs-lookup"><span data-stu-id="21c65-115">Set the **SnappingInterval** to a value that represents the snapping interval.</span></span> <span data-ttu-id="21c65-116">指针将与已指定的值的最接近舍入倍数对齐。</span><span class="sxs-lookup"><span data-stu-id="21c65-116">The pointer will be snapped to the nearest round multiple of the value that you have specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21c65-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="21c65-117">See Also</span></span>  
 <span data-ttu-id="21c65-118">[设置仪表上刻度的格式 &#40;报表生成器和 SSRS&#41;](report-design/formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="21c65-118">[Formatting Scales on a Gauge &#40;Report Builder and SSRS&#41;](report-design/formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="21c65-119">[设置仪表上的指针格式 &#40;报表生成器和 SSRS&#41;](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="21c65-119">[Formatting Pointers on a Gauge &#40;Report Builder and SSRS&#41;](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="21c65-120">仪表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="21c65-120">Gauges &#40;Report Builder and SSRS&#41;</span></span>](report-design/gauges-report-builder-and-ssrs.md)  
  
  
