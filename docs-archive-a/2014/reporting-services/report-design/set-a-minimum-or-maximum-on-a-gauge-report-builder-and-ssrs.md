---
title: 设置仪表的最小值或最大值（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b4c260c0-5a88-4f30-8977-eb5cc78fc146
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 344122dbff647a8c35b838ecce637602f202864b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578632"
---
# <a name="set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs"></a><span data-ttu-id="fdca9-102">设置仪表的最小值或最大值（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="fdca9-102">Set a Minimum or Maximum on a Gauge (Report Builder and SSRS)</span></span>
  <span data-ttu-id="fdca9-103">与其中定义了多个组的图表不同，仪表上只显示一个值。</span><span class="sxs-lookup"><span data-stu-id="fdca9-103">Unlike the chart, where multiple groups are defined, the gauge only shows one value.</span></span> <span data-ttu-id="fdca9-104">由于报表生成器和报表设计器确定要在仪表上显示的一个值的上下文或相对重要性，因此必须定义刻度的最小值和最大值。</span><span class="sxs-lookup"><span data-stu-id="fdca9-104">Since Report Builder and Report Designer determine the context or relative significance of the one value that you are trying to show on the gauge, you must define the minimum and maximum of the scale.</span></span> <span data-ttu-id="fdca9-105">例如，如果数据值是介于 0 到 10 之间的评分，则需要将最小值设置为 0，将最大值设置为 10。</span><span class="sxs-lookup"><span data-stu-id="fdca9-105">For example, if your data values are rankings between 0 and 10, you will want to set the minimum to 0 and maximum to 10.</span></span> <span data-ttu-id="fdca9-106">间隔数值会根据指定的最小值和最大值自动计算。</span><span class="sxs-lookup"><span data-stu-id="fdca9-106">The interval numbers are calculated automatically based on the values specified for the minimum and maximum.</span></span> <span data-ttu-id="fdca9-107">默认情况下，最小值设置为 0，最大值设置为 100，但这是您可任意更改的值。</span><span class="sxs-lookup"><span data-stu-id="fdca9-107">By default, the minimum and maximum are set to 0 and 100, but this is an arbitrary value that you should change.</span></span> <span data-ttu-id="fdca9-108">应用程序不会将您的值计算为百分比。</span><span class="sxs-lookup"><span data-stu-id="fdca9-108">The application does not calculate your value as a percentage.</span></span>  
  
 <span data-ttu-id="fdca9-109">如果您的值范围较大，例如从 0 到 10000，可考虑使用乘数以减少仪表上零的数量。</span><span class="sxs-lookup"><span data-stu-id="fdca9-109">If the range of your values is large, for example from 0 to 10000, consider using a multiplier to reduce the number of zeroes on the gauge.</span></span> <span data-ttu-id="fdca9-110">乘数只会减小仪表上数值的刻度，但不会减小值本身。</span><span class="sxs-lookup"><span data-stu-id="fdca9-110">The multiplier will only reduce the scale of the numbers on the gauge, not the value itself.</span></span>  
  
 <span data-ttu-id="fdca9-111">您可以使用表达式来设置 **“最小值”** 和 **“最大值”** 选项的值。</span><span class="sxs-lookup"><span data-stu-id="fdca9-111">You can use expressions to set the values of the **Minimum** and **Maximum** options.</span></span> <span data-ttu-id="fdca9-112">有关详细信息，请参阅[表达式（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="fdca9-112">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-the-minimum-and-maximum-on-the-gauge"></a><span data-ttu-id="fdca9-113">在仪表上设置最小值和最大值</span><span class="sxs-lookup"><span data-stu-id="fdca9-113">To set the minimum and maximum on the gauge</span></span>  
  
1.  <span data-ttu-id="fdca9-114">右键单击刻度并选择“刻度属性”  。</span><span class="sxs-lookup"><span data-stu-id="fdca9-114">Right-click on the scale and select **Scale Properties**.</span></span> <span data-ttu-id="fdca9-115">此时将显示 **“刻度属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="fdca9-115">The **Scale Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="fdca9-116">在 **“常规”** 中，为 **“最小值”** 指定一个值。</span><span class="sxs-lookup"><span data-stu-id="fdca9-116">In **General**, specify a value for **Minimum**.</span></span> <span data-ttu-id="fdca9-117">默认情况下，此值为 0。</span><span class="sxs-lookup"><span data-stu-id="fdca9-117">By default, this value is 0.</span></span> <span data-ttu-id="fdca9-118">或者，单击“表达式”(fx) 按钮，编辑设置该选项值的表达式   。</span><span class="sxs-lookup"><span data-stu-id="fdca9-118">Optionally, click the **Expression** (*fx*) button to edit the expression that sets the value of the option.</span></span>  
  
3.  <span data-ttu-id="fdca9-119">为 **“最大值”** 指定一个值。</span><span class="sxs-lookup"><span data-stu-id="fdca9-119">Specify a value for **Maximum**.</span></span> <span data-ttu-id="fdca9-120">默认情况下，此值为 100。</span><span class="sxs-lookup"><span data-stu-id="fdca9-120">By default, this value is 100.</span></span> <span data-ttu-id="fdca9-121">或者，单击“表达式”(fx) 按钮，编辑设置该选项值的表达式   。</span><span class="sxs-lookup"><span data-stu-id="fdca9-121">Optionally, click the **Expression** (*fx*) button to edit the expression that sets the value of the option.</span></span>  
  
4.  <span data-ttu-id="fdca9-122">（可选）如果最大值和最小值较大，请为“刻度标签乘以”  选项指定一个值。</span><span class="sxs-lookup"><span data-stu-id="fdca9-122">(Optional) If the values for your minimum and maximum are large, specify a value for the **Multiply scale labels by** option.</span></span> <span data-ttu-id="fdca9-123">若要指定可减小刻度的乘数，请使用小数。</span><span class="sxs-lookup"><span data-stu-id="fdca9-123">To specify a multiplier that reduces your scale, use a decimal number.</span></span> <span data-ttu-id="fdca9-124">例如，如果刻度范围为 0 到 1000，则可指定乘数值 0.01，以将刻度范围减少到只显示 0 到 10。</span><span class="sxs-lookup"><span data-stu-id="fdca9-124">For example, if you have a scale from 0 to 1000, you can specify a multiplier value of 0.01 to reduce the scale to read 0 to 10.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdca9-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fdca9-125">See Also</span></span>  
 <span data-ttu-id="fdca9-126">[设置仪表上刻度的格式（报表生成器和 SSRS）](formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fdca9-126">[Formatting Scales on a Gauge &#40;Report Builder and SSRS&#41;](formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="fdca9-127">[设置仪表上指针的格式（报表生成器和 SSRS）](formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fdca9-127">[Formatting Pointers on a Gauge &#40;Report Builder and SSRS&#41;](formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="fdca9-128">仪表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="fdca9-128">Gauges &#40;Report Builder and SSRS&#41;</span></span>](gauges-report-builder-and-ssrs.md)  
  
  
