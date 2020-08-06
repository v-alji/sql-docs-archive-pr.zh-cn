---
title: 设置数字和日期的格式（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.placeholderproperties.number.f1
- sql12.rtp.rptdesigner.serieslabelproperties.number.f1
- "10127"
- sql12.rtp.rptdesigner.axisproperties.number.f1
- "10130"
- "10286"
- sql12.rtp.rptdesigner.textboxproperties.number.f1
- "10285"
ms.assetid: 6de1a725-9f06-4708-be26-2d55e442e344
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 597ff535e72bc174cc6f9bd5a226e95641ba8a4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682718"
---
# <a name="formatting-numbers-and-dates-report-builder-and-ssrs"></a><span data-ttu-id="44244-102">设置数字和日期的格式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="44244-102">Formatting Numbers and Dates (Report Builder and SSRS)</span></span>
  <span data-ttu-id="44244-103">通过从相应数据区域的 **“属性”** 对话框的 **“数字”** 页选择格式，可以在数据区域中设置数字和日期的格式。</span><span class="sxs-lookup"><span data-stu-id="44244-103">You can format numbers and dates in data regions by selecting a format from the **Number** page of the corresponding data region's **Properties** dialog box.</span></span>  
  
 <span data-ttu-id="44244-104">若要指定文本框报表项中的格式字符串，需要选择要对其设置格式的项，右键单击该项，选择 **“文本框属性”** ，然后单击 **“数字”** 。</span><span class="sxs-lookup"><span data-stu-id="44244-104">To specify format strings within a text box report item, you need to select the item that you want to format, right-click, select **Text Box Properties**, and then click **Number**.</span></span> <span data-ttu-id="44244-105">可以通过相同方式设置表或矩阵数据区域中的各个单元格的格式，因为表或矩阵中的单元格是单个文本框。</span><span class="sxs-lookup"><span data-stu-id="44244-105">You can format individual cells in a table or matrix data region in the same manner, because cells in a table or matrix are individual text boxes.</span></span>  
  
 <span data-ttu-id="44244-106">图表数据区域通常显示沿类别 (x) 轴的日期，和沿值 (y) 轴的值。</span><span class="sxs-lookup"><span data-stu-id="44244-106">A chart data region commonly shows dates along the category (x) axis, and values along the value (y) axis.</span></span> <span data-ttu-id="44244-107">若要指定图表中的格式设置，请右键单击某个轴并选择 **“轴属性”** 。</span><span class="sxs-lookup"><span data-stu-id="44244-107">To specify formatting in a chart, right-click an axis and select **Axis Properties**.</span></span> <span data-ttu-id="44244-108">在值轴上，只能为数字指定格式。</span><span class="sxs-lookup"><span data-stu-id="44244-108">On the value axis, you can specify formats only for numbers.</span></span> <span data-ttu-id="44244-109">有关详细信息，请参阅[设置图表上轴标签的格式（报表生成器和 SSRS）](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="44244-109">For more information, see [Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="44244-110">若要指定仪表数据区域中的格式设置，请右键单击仪表的刻度，并选择 **“径向刻度属性”** 或 **“线性刻度属性”** 。</span><span class="sxs-lookup"><span data-stu-id="44244-110">To specify formatting in a Gauge data region, right-click the scale of the gauge and select **Radial Scale Properties** or **Linear Scale Properties**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="44244-111">如果要使用的某些格式设置选项显示为灰色，这表示这些格式设置选项与字段的数据类型（在数据源中设置）不兼容。</span><span class="sxs-lookup"><span data-stu-id="44244-111">If some formatting options you want to use are grayed out, it means that those formatting options are not compatible the field's data type, which is set in the data source.</span></span> <span data-ttu-id="44244-112">例如，如果该字段包含数值，但该字段的数据类型为 String，则无法应用数值数据格式设置选项（如货币或小数）。</span><span class="sxs-lookup"><span data-stu-id="44244-112">For example, if the field contains number values but the field's data type is String, you cannot apply numerical data formatting options such as currency or decimals.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="considerations-for-formatting-numbers-and-dates"></a><span data-ttu-id="44244-113">设置数字和日期格式的注意事项</span><span class="sxs-lookup"><span data-stu-id="44244-113">Considerations for Formatting Numbers and Dates</span></span>  
 <span data-ttu-id="44244-114">在设置报表中数字和日期的格式之前，应注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="44244-114">Before you format numbers and dates in your report, consider the following:</span></span>  
  
-   <span data-ttu-id="44244-115">默认情况下，数字的格式设置反映客户端计算机上的区域性设置。</span><span class="sxs-lookup"><span data-stu-id="44244-115">By default, numbers are formatted to reflect the cultural settings on the client computer.</span></span> <span data-ttu-id="44244-116">将格式设置字符串用于指定数字的显示方式，可使格式设置保持一致，而无论用户在何处查看报表。</span><span class="sxs-lookup"><span data-stu-id="44244-116">Use formatting strings to specify how numbers are displayed so that formatting is consistent regardless of where the person who is viewing the report is located.</span></span>  
  
-   <span data-ttu-id="44244-117">**“数字”** 页上提供的格式是 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 标准数字格式字符串的子集。</span><span class="sxs-lookup"><span data-stu-id="44244-117">The formats provided on the **Number** page are a subset of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] standard numeric format strings.</span></span> <span data-ttu-id="44244-118">若要使用未显示在对话框中的自定义格式来设置数字或日期格式，可以将任何 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 格式字符串用于数字或日期。</span><span class="sxs-lookup"><span data-stu-id="44244-118">To format a number or date using a custom format that is not shown in the dialog box, you can use any [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] format strings for numbers or dates.</span></span> <span data-ttu-id="44244-119">有关自定义格式字符串的详细信息，请参阅 MSDN 上的主题 [Formatting Types](https://go.microsoft.com/fwlink/?LinkId=112024) （设置类型的格式）。</span><span class="sxs-lookup"><span data-stu-id="44244-119">For more information about custom format strings, see the [Formatting Types](https://go.microsoft.com/fwlink/?LinkId=112024) topic on MSDN.</span></span>  
  
-   <span data-ttu-id="44244-120">如果已指定了自定义格式字符串，则它的优先级比特定于区域性的默认设置的优先级更高。</span><span class="sxs-lookup"><span data-stu-id="44244-120">If a custom format string has been specified, it has a higher priority over default settings that are culture-specific.</span></span> <span data-ttu-id="44244-121">例如，假定设置了自定义格式字符串“#,###”以将数字 1234 显示为 1,234。</span><span class="sxs-lookup"><span data-stu-id="44244-121">For example, suppose you set a custom format string of "#,###" to show the number 1234 as 1,234.</span></span> <span data-ttu-id="44244-122">对于美国用户和欧洲的用户而言，它的含义可能是不同的。</span><span class="sxs-lookup"><span data-stu-id="44244-122">This may have different meaning to users in the United States than it does to users in Europe.</span></span> <span data-ttu-id="44244-123">在指定自定义格式之前，请考虑您选择的格式将会如何影响那些可能会查看报表的不同区域性的用户。</span><span class="sxs-lookup"><span data-stu-id="44244-123">Before you specify a custom format, consider how the format you choose will affect users of different cultures who may view the report.</span></span>  
  
-   <span data-ttu-id="44244-124">如果指定了无效的格式字符串，则将被格式化文本解释为覆盖格式设置的文字字符串。</span><span class="sxs-lookup"><span data-stu-id="44244-124">If you specify an invalid format string, the formatted text is interpreted as a literal string which overrides the formatting.</span></span>  
  
-   <span data-ttu-id="44244-125">如果是对同一文本框中的数字和字符组合设置格式，请考虑使用占位符，以将数字和其余文本区分开来单独设置格式。</span><span class="sxs-lookup"><span data-stu-id="44244-125">If you are formatting a mix of numbers and characters in the same text box, consider using a placeholder to format the number separately from the rest of the text.</span></span> <span data-ttu-id="44244-126">有关详细信息，请参阅 [设置文本和占位符的格式（报表生成器和 SSRS）](formatting-text-and-placeholders-report-builder-and-ssrs.md)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="44244-126">For more information, see [Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md).</span></span> <span data-ttu-id="44244-127">如果为文本框的 Format 属性指定了无效格式字符串，则该格式字符串会被忽略。</span><span class="sxs-lookup"><span data-stu-id="44244-127">If an invalid format string is specified for the Format property on the text box, the format string is ignored.</span></span> <span data-ttu-id="44244-128">如果为图表或仪表上的 Format 属性指定了无效格式字符串，则指定的格式字符串将被解释为字符串并且不会应用格式设置。</span><span class="sxs-lookup"><span data-stu-id="44244-128">If an invalid format string is specified for the Format property on the chart or gauge, the format string that you specified is interpreted as a string and formatting is not applied.</span></span>  
  
-   <span data-ttu-id="44244-129">如果选择 **“类别”** 下的 **“货币”** 并选中 **“值的显示位置”** ，则可以选择 **“千”** 、 **“百万”** 或 **“十亿”** 使用财务格式显示数字。</span><span class="sxs-lookup"><span data-stu-id="44244-129">If you select **Currency** under **Category** and you check **Show values in**, you can select **Thousands**, **Millions**, or **Billions** to display numbers using financial formats.</span></span> <span data-ttu-id="44244-130">例如，如果字段值为 1,789,905,394，且您选择 **“十亿”** 并指定 2 个小数位，则该值在报表中显示为 1.78。</span><span class="sxs-lookup"><span data-stu-id="44244-130">For example, if the field value is 1,789,905,394 and you select **Billions** and specify 2 decimal places, the value displayed in the report is 1.78.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44244-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="44244-131">See Also</span></span>  
 <span data-ttu-id="44244-132">[设置文本和占位符的格式（报表生成器和 SSRS）](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="44244-132">[Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="44244-133">[设置线条、颜色和图像的格式（报表生成器和 SSRS）](images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="44244-133">[Formatting Lines, Colors, and Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="44244-134">[设置图表格式（报表生成器和 SSRS）](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="44244-134">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="44244-135">[将轴标签的格式设置为日期或货币（报表生成器和 SSRS）](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="44244-135">[Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="44244-136">设置仪表上刻度的格式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="44244-136">Formatting Scales on a Gauge &#40;Report Builder and SSRS&#41;</span></span>](formatting-scales-on-a-gauge-report-builder-and-ssrs.md)  
  
  
