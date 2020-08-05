---
title: 设置和配置度量单位（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a15a96c3-7d2c-433e-a440-4ea051e967a9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c01523dad9a96d2d45b96474d36873bac2484343
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577279"
---
# <a name="set-and-configure-measurement-units-report-builder-and-ssrs"></a><span data-ttu-id="63594-102">设置和配置度量单位（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="63594-102">Set and Configure Measurement Units (Report Builder and SSRS)</span></span>
  <span data-ttu-id="63594-103">指示器提供两种度量单位：百分比和数字。</span><span class="sxs-lookup"><span data-stu-id="63594-103">Indicators provide two measurement units: percentage and numeric.</span></span> <span data-ttu-id="63594-104">默认情况下，指示器配置为使用百分比作为度量单位。</span><span class="sxs-lookup"><span data-stu-id="63594-104">By default, indicators are configured to use percentages as the measurement unit.</span></span> <span data-ttu-id="63594-105">这意味着分配给指示器集中各图标的指示器值由百分比范围确定。</span><span class="sxs-lookup"><span data-stu-id="63594-105">This means that the indicator values assigned to each icon in the indicator set are determined by a percentage range.</span></span> <span data-ttu-id="63594-106">百分比范围在指示器集中的各图标上平均划分。</span><span class="sxs-lookup"><span data-stu-id="63594-106">The percentage ranges are evenly divided across the icons in the indicator set.</span></span> <span data-ttu-id="63594-107">每个图标都表示一个指示器状态。</span><span class="sxs-lookup"><span data-stu-id="63594-107">Each icon represents an indicator state.</span></span> <span data-ttu-id="63594-108">您可以通过指定不同的开始和结束百分比，更改指示器集中每个图标的百分比。</span><span class="sxs-lookup"><span data-stu-id="63594-108">You can change the percentages for each icon in the indicator set by specifying different start and end percentages.</span></span> <span data-ttu-id="63594-109">指示器还自动检测数据中的最小值和最大值。</span><span class="sxs-lookup"><span data-stu-id="63594-109">Indicators also automatically detect the minimum and maximum values in the data.</span></span>  
  
 <span data-ttu-id="63594-110">您可以将度量单位更改为数值。</span><span class="sxs-lookup"><span data-stu-id="63594-110">You can change the measurement unit to be a numeric value.</span></span> <span data-ttu-id="63594-111">在此情况下，不要为数据指定最小值或最大值；而是为指示器使用的每个图标仅提供开始值和结束值。</span><span class="sxs-lookup"><span data-stu-id="63594-111">In this case, you do not specify minimum or maximum for the data; instead, you provide only the start and end values for each icon that the indicator uses.</span></span>  
  
 <span data-ttu-id="63594-112">可以通过使用表达式设置度量单位之类的选项。</span><span class="sxs-lookup"><span data-stu-id="63594-112">Options such as measurement units can be set by using expressions.</span></span> <span data-ttu-id="63594-113">有关详细信息，请参阅[表达式（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="63594-113">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-use-the-numeric-state-measurement-unit"></a><span data-ttu-id="63594-114">使用数字状态度量单位</span><span class="sxs-lookup"><span data-stu-id="63594-114">To use the numeric state measurement unit</span></span>  
  
1.  <span data-ttu-id="63594-115">右键单击要更改的指示器，然后单击“指示器属性”  。</span><span class="sxs-lookup"><span data-stu-id="63594-115">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="63594-116">在左窗格中单击 **“值和状态”** 。</span><span class="sxs-lookup"><span data-stu-id="63594-116">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="63594-117">在 **“状态度量单位”** 列表中，单击 **“数字”** 。</span><span class="sxs-lookup"><span data-stu-id="63594-117">In the **States Measurement Unit** list, click **Numeric**.</span></span>  
  
     <span data-ttu-id="63594-118">或者，单击“表达式”(fx) 按钮，编辑设置该选项的值的表达式   。</span><span class="sxs-lookup"><span data-stu-id="63594-118">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the value of the option.</span></span>  
  
4.  <span data-ttu-id="63594-119">对于指示器集中的每个图标，在 **“开始”** 和 **“结束”** 文本框中更新值。</span><span class="sxs-lookup"><span data-stu-id="63594-119">For each icon in the indicator set, update the values in the **Start** and **End** text boxes.</span></span>  
  
     <span data-ttu-id="63594-120">或者，单击“表达式”(fx) 按钮，编辑设置“开始”和“结束”选项的值的表达式     。</span><span class="sxs-lookup"><span data-stu-id="63594-120">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the values of the **Start** and **End** options.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="63594-121">“开始”和“结束”文本框中的值必须是数字   。</span><span class="sxs-lookup"><span data-stu-id="63594-121">The values in the **Start** and **End** text boxes must be numeric.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-use-the-percentage-measurement-unit"></a><span data-ttu-id="63594-122">使用百分比度量单位</span><span class="sxs-lookup"><span data-stu-id="63594-122">To use the percentage measurement unit</span></span>  
  
1.  <span data-ttu-id="63594-123">右键单击要更改的指示器，然后单击“指示器属性”  。</span><span class="sxs-lookup"><span data-stu-id="63594-123">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="63594-124">在左窗格中单击 **“值和状态”** 。</span><span class="sxs-lookup"><span data-stu-id="63594-124">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="63594-125">在 **“状态度量单位”** 列表中，单击 **“百分比”** 。</span><span class="sxs-lookup"><span data-stu-id="63594-125">In the **States Measurement Unit** list, click **Percentage**.</span></span>  
  
     <span data-ttu-id="63594-126">或者，单击“表达式”(fx) 按钮，编辑设置该选项的值的表达式   。</span><span class="sxs-lookup"><span data-stu-id="63594-126">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the value of the option.</span></span>  
  
4.  <span data-ttu-id="63594-127">还可以更改 **“最小值”** 和 **“最大值”** 选项以使用特定值，而非自动检测指示器使用的数据的最小值和最大值。</span><span class="sxs-lookup"><span data-stu-id="63594-127">Optionally, change the **Minimum** and **Maximum** options to use specific values instead of automatically detecting the minimum and maximum values of the data that the indicator uses.</span></span> <span data-ttu-id="63594-128">**“最小值”** 必须小于 **“最大值”** 。</span><span class="sxs-lookup"><span data-stu-id="63594-128">The value of **Minimum** must be smaller than the value of **Maximum**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="63594-129">如果您显式设置最小值和最大值，则指示器将使用该值范围，而与数据中的实际最小值和最大值无关。</span><span class="sxs-lookup"><span data-stu-id="63594-129">If you explicitly set minimum and maximum values, that value range is used by the indicator regardless of the actual the minimum and maximum values in the data.</span></span> <span data-ttu-id="63594-130">这意味着，在确定要在报表中显示的指示器图标的计算中，将排除低于最小值的值和高于最大值的值。</span><span class="sxs-lookup"><span data-stu-id="63594-130">This means that values lower than the minimum and higher than the maximum are excluded from the evaluation that determine what indictor icon to show in the report.</span></span>  
  
     <span data-ttu-id="63594-131">或者，单击“表达式”(fx) 按钮，编辑设置该选项的值的表达式   。</span><span class="sxs-lookup"><span data-stu-id="63594-131">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the values of the option.</span></span>  
  
5.  <span data-ttu-id="63594-132">对于指示器集中的每个图标，在 **“开始”** 和 **“结束”** 文本框中更新值。</span><span class="sxs-lookup"><span data-stu-id="63594-132">For each icon in the indicator set, update the values in the **Start** and **End** text boxes.</span></span>  
  
     <span data-ttu-id="63594-133">或者，单击“表达式”(fx) 按钮，编辑设置“开始”和“结束”选项的值的表达式     。</span><span class="sxs-lookup"><span data-stu-id="63594-133">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the values of the **Start** and **End** options.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="63594-134">“开始”和“结束”文本框中的值必须是数字   。</span><span class="sxs-lookup"><span data-stu-id="63594-134">The values in the **Start** and **End** text boxes must be numeric.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="63594-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="63594-135">See Also</span></span>  
 [<span data-ttu-id="63594-136">指示器（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="63594-136">Indicators &#40;Report Builder and SSRS&#41;</span></span>](indicators-report-builder-and-ssrs.md)  
  
  
