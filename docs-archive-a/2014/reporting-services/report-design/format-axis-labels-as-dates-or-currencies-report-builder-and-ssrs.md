---
title: 将轴标签的格式设置为日期或货币（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e9a01a74-2f51-4b35-be3a-a6138568f6cf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ffe9d903a2271db95d4b1c2ef6201d2b0f3edab3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580580"
---
# <a name="format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs"></a><span data-ttu-id="9ef3b-102">将轴标签的格式设置为日期或货币（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="9ef3b-102">Format Axis Labels as Dates or Currencies (Report Builder and SSRS)</span></span>
  <span data-ttu-id="9ef3b-103">在轴上显示格式设置正确的 DateTime 值时，图表会自动将这些值显示为天数。</span><span class="sxs-lookup"><span data-stu-id="9ef3b-103">When you show properly formatted DateTime values on an axis, a chart will automatically display these values as days.</span></span> <span data-ttu-id="9ef3b-104">若要为 x 轴指定日期/时间间隔，如月份或小时间隔，则必须设置轴标签的格式，并要将轴间隔的类型设置为有效的日期或时间间隔。</span><span class="sxs-lookup"><span data-stu-id="9ef3b-104">To specify a date/time interval for the x-axis, such as an interval of months or an interval of hours, you must format the axis labels and set the type of axis interval to a valid date or time interval.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9ef3b-105">在柱形图和散点图中，水平轴（或 x 轴）是类别轴。</span><span class="sxs-lookup"><span data-stu-id="9ef3b-105">In column and scatter charts, the horizontal, or x-axis, is the category axis.</span></span> <span data-ttu-id="9ef3b-106">在条形图中，垂直轴（或 y 轴）是类别轴。</span><span class="sxs-lookup"><span data-stu-id="9ef3b-106">In bar charts, the vertical, or y-axis, is the category axis.</span></span>  
  
 <span data-ttu-id="9ef3b-107">X 轴上显示的值的计算结果必须为 <xref:System.DateTime> 数据类型，才能正确地设置时间间隔的格式。</span><span class="sxs-lookup"><span data-stu-id="9ef3b-107">In order to format time intervals correctly, the values displayed on the x-axis must evaluate to a <xref:System.DateTime> data type.</span></span> <span data-ttu-id="9ef3b-108">如果字段的数据类型为 <xref:System.String>，则图表不会将间隔计算为日期或时间。</span><span class="sxs-lookup"><span data-stu-id="9ef3b-108">If your field has a data type of <xref:System.String>, the chart will not calculate intervals as dates or times.</span></span> <span data-ttu-id="9ef3b-109">有关详细信息，请参阅 [图表（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="9ef3b-109">For more information, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="9ef3b-110">向 Y 轴添加数值时，默认情况下，图表不会在显示该数值前设置其格式。</span><span class="sxs-lookup"><span data-stu-id="9ef3b-110">When a numeric value is added to the y-axis, by default, the chart does not format the number before displaying it.</span></span> <span data-ttu-id="9ef3b-111">如果数值字段为销售数字，请考虑将其格式设置为货币，以增强图表的可读性。</span><span class="sxs-lookup"><span data-stu-id="9ef3b-111">If your numeric field is a sales figure, consider formatting the numbers as currencies to increase the readability of the chart.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-format-x-axis-labels-as-monthly-intervals"></a><span data-ttu-id="9ef3b-112">将 X 轴标签的格式设置为月间隔</span><span class="sxs-lookup"><span data-stu-id="9ef3b-112">To format x-axis labels as monthly intervals</span></span>  
  
1.  <span data-ttu-id="9ef3b-113">右键单击图表的水平轴（或 x 轴），然后选择“水平轴属性”  。</span><span class="sxs-lookup"><span data-stu-id="9ef3b-113">Right-click the horizontal, or x-axis, of the chart, and select **HorizontalAxis Properties**.</span></span>  
  
2.  <span data-ttu-id="9ef3b-114">在“水平轴属性”对话框中，选择“数字”   。</span><span class="sxs-lookup"><span data-stu-id="9ef3b-114">In the **HorizontalAxis Properties** dialog box, select **Number**.</span></span>  
  
3.  <span data-ttu-id="9ef3b-115">从 **“类别”** 列表中，选择 **“日期”** 。</span><span class="sxs-lookup"><span data-stu-id="9ef3b-115">From the **Category** list, select **Date**.</span></span> <span data-ttu-id="9ef3b-116">从“类型”列表中，选择要应用到 X 轴标签的日期格式  。</span><span class="sxs-lookup"><span data-stu-id="9ef3b-116">From the **Type** list, select a date format to apply to the x-axis labels.</span></span>  
  
4.  <span data-ttu-id="9ef3b-117">选择 **“轴选项”** 。</span><span class="sxs-lookup"><span data-stu-id="9ef3b-117">Select **Axis Options.**</span></span>  
  
5.  <span data-ttu-id="9ef3b-118">在 **“间隔”** 中，键入 **1**。</span><span class="sxs-lookup"><span data-stu-id="9ef3b-118">In **Interval**, type **1**.</span></span> <span data-ttu-id="9ef3b-119">在 **“间隔类型”** 属性中，选择 **“月”** 。</span><span class="sxs-lookup"><span data-stu-id="9ef3b-119">In **Interval type** property, select **Months**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9ef3b-120">如果不指定间隔类型，则图表将按天计算间隔。</span><span class="sxs-lookup"><span data-stu-id="9ef3b-120">If you do not specify an interval type, the chart will calculate intervals in terms of days.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-format-y-axis-labels-using-a-currency-format"></a><span data-ttu-id="9ef3b-121">使用货币格式设置 Y 轴标签的格式</span><span class="sxs-lookup"><span data-stu-id="9ef3b-121">To format y-axis labels using a currency format</span></span>  
  
1.  <span data-ttu-id="9ef3b-122">右键单击图表的垂直轴（或 y 轴），然后选择“垂直轴属性”  。</span><span class="sxs-lookup"><span data-stu-id="9ef3b-122">Right-click the vertical, or y-axis, of the chart, and select **VerticalAxis Properties**.</span></span>  
  
2.  <span data-ttu-id="9ef3b-123">在“垂直轴属性”对话框中，选择“数字”   。</span><span class="sxs-lookup"><span data-stu-id="9ef3b-123">In the **VerticalAxis Properties** dialog box, select **Number**.</span></span>  
  
3.  <span data-ttu-id="9ef3b-124">从 **“类别”** 列表中，选择 **“货币”** 。</span><span class="sxs-lookup"><span data-stu-id="9ef3b-124">From the **Category** list, select **Currency**.</span></span> <span data-ttu-id="9ef3b-125">从“符号”列表中，选择要应用到 Y 轴标签的货币格式  。</span><span class="sxs-lookup"><span data-stu-id="9ef3b-125">From the **Symbol** list, select a currency format to apply to the y-axis labels.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9ef3b-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9ef3b-126">See Also</span></span>  
 <span data-ttu-id="9ef3b-127">[设置图表上轴标签的格式（报表生成器和 SSRS）](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9ef3b-127">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9ef3b-128">[设置图表格式（报表生成器和 SSRS）](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9ef3b-128">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9ef3b-129">[指定对数刻度（报表生成器和 SSRS）](specify-a-logarithmic-scale-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9ef3b-129">[Specify a Logarithmic Scale &#40;Report Builder and SSRS&#41;](specify-a-logarithmic-scale-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="9ef3b-130">指定轴间隔（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="9ef3b-130">Specify an Axis Interval &#40;Report Builder and SSRS&#41;</span></span>](specify-an-axis-interval-report-builder-and-ssrs.md)  
  
  
