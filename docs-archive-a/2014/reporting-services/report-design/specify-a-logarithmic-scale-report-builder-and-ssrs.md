---
title: 指定对数刻度（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f3092c1c-b128-433d-9a95-983508b2a8d4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2cc422a6f95a420445dc604d08a23e8f8e65c95d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577263"
---
# <a name="specify-a-logarithmic-scale-report-builder-and-ssrs"></a><span data-ttu-id="b5237-102">指定对数刻度（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="b5237-102">Specify a Logarithmic Scale (Report Builder and SSRS)</span></span>
  <span data-ttu-id="b5237-103">如果您的数据按对数成比例，您可能需要考虑在图表上使用对数刻度。</span><span class="sxs-lookup"><span data-stu-id="b5237-103">If you have data that is logarithmically proportional, you may want to consider using a logarithmic scale on the chart.</span></span> <span data-ttu-id="b5237-104">这样做可以使数据更容易管理，因而有助于改善图表的外观。</span><span class="sxs-lookup"><span data-stu-id="b5237-104">This helps improve the appearance of the chart by making your data more manageable.</span></span> <span data-ttu-id="b5237-105">大多数对数刻度都以 10 为底数。</span><span class="sxs-lookup"><span data-stu-id="b5237-105">Most logarithmic scales use a base of 10.</span></span>  
  
 <span data-ttu-id="b5237-106">此功能仅可在值轴上使用。</span><span class="sxs-lookup"><span data-stu-id="b5237-106">This feature is only available on the value axis.</span></span> <span data-ttu-id="b5237-107">值轴通常是垂直轴（或 y 轴）。</span><span class="sxs-lookup"><span data-stu-id="b5237-107">The value axis is usually the vertical, or y-axis.</span></span> <span data-ttu-id="b5237-108">但在条形图中，值轴是水平轴（或 x 轴）。</span><span class="sxs-lookup"><span data-stu-id="b5237-108">On bar charts, however, it is the horizontal, or x-axis.</span></span>  
  
 <span data-ttu-id="b5237-109">如果轴是采用对数刻度的轴，则与该轴相关的所有其他属性都将采用对数刻度。</span><span class="sxs-lookup"><span data-stu-id="b5237-109">If your axis is logarithmic, all other properties relating to the axis will be scaled logarithmically.</span></span> <span data-ttu-id="b5237-110">例如，如果您指定在轴上采用以 10 为底数的对数刻度，则将轴间隔设置为 2 得到的间隔数量级将是 10 的 2 次幂，也就是 100。</span><span class="sxs-lookup"><span data-stu-id="b5237-110">For example, if you specify a base-10 logarithmic scale on your axis, setting an axis interval of 2 will generate intervals in magnitudes of 10 to the power of 2, or 100.</span></span> <span data-ttu-id="b5237-111">这意味着，您的轴值读数将为 1、100、10000，而不是默认结果 1、10、100、1000、10000。</span><span class="sxs-lookup"><span data-stu-id="b5237-111">This means your axis values will read 1, 100, 10000, instead of the default result of 1, 10, 100, 1000, 10000.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-a-logarithmic-scale"></a><span data-ttu-id="b5237-112">指定对数刻度</span><span class="sxs-lookup"><span data-stu-id="b5237-112">To specify a logarithmic scale</span></span>  
  
1.  <span data-ttu-id="b5237-113">右键单击图表的 y 轴，然后单击“垂直轴属性”  。</span><span class="sxs-lookup"><span data-stu-id="b5237-113">Right-click the y-axis of your chart, and click **VerticalAxis Properties**.</span></span> <span data-ttu-id="b5237-114">随即出现“垂直轴属性”对话框  。</span><span class="sxs-lookup"><span data-stu-id="b5237-114">The **VerticalAxis Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="b5237-115">在“轴选项”中，选择“使用对数刻度”   。</span><span class="sxs-lookup"><span data-stu-id="b5237-115">In **Axis Options**, select **Uselogarithmic scale**.</span></span>  
  
3.  <span data-ttu-id="b5237-116">在“对数底数”文本框中，键入一个用作对数底数的正值  。</span><span class="sxs-lookup"><span data-stu-id="b5237-116">In the **Logbase** text box, type a positive value for the logarithmic base.</span></span> <span data-ttu-id="b5237-117">如果不指定任何值，则对数底数采用默认值 10。</span><span class="sxs-lookup"><span data-stu-id="b5237-117">If no value is specified, the logarithmic base defaults to 10.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5237-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b5237-118">See Also</span></span>  
 <span data-ttu-id="b5237-119">[设置图表上轴标签的格式（报表生成器和 SSRS）](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b5237-119">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b5237-120">[设置图表格式（报表生成器和 SSRS）](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b5237-120">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b5237-121">[将轴标签的格式设置为日期或货币（报表生成器和 SSRS）](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b5237-121">[Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="b5237-122">图表&#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b5237-122">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
