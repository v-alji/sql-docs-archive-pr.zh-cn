---
title: 向图表添加边框（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ca0c5040-40bb-4cb7-bc2b-5bcbe73858bb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4c91d3de00caa4eab6ed1894042b2214b7dcf4b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692741"
---
# <a name="add-a-border-frame-to-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="f804b-102">向图表添加边框（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="f804b-102">Add a Border Frame to a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f804b-103">若要增强图表的视觉效果，可以考虑在图表的外部周围使用边框。</span><span class="sxs-lookup"><span data-stu-id="f804b-103">To give a chart more visual impact, consider using a border frame around the outside of the chart.</span></span> <span data-ttu-id="f804b-104">可以使用 **“图表属性”** 对话框或“属性”窗格来选择边框。</span><span class="sxs-lookup"><span data-stu-id="f804b-104">You can select a border frame by using the **Chart Properties** dialog box or by using the Properties pane.</span></span> <span data-ttu-id="f804b-105">图表的边框不能应用于任何其他数据区域。</span><span class="sxs-lookup"><span data-stu-id="f804b-105">The chart border frames cannot be applied to any other data region.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-apply-a-border-to-a-chart"></a><span data-ttu-id="f804b-106">向图表应用边框</span><span class="sxs-lookup"><span data-stu-id="f804b-106">To apply a border to a chart</span></span>  
  
1.  <span data-ttu-id="f804b-107">右键单击图表上的任意位置并选择“图表属性”  。</span><span class="sxs-lookup"><span data-stu-id="f804b-107">Right-click anywhere on the chart and select **Chart Properties**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f804b-108">如果看不到“图表属性”，请在快捷菜单中指向“图表”，然后选择“图表属性”    。</span><span class="sxs-lookup"><span data-stu-id="f804b-108">If you do not see the **Chart Properties**, point to **Chart** on the shortcut menu and select **Chart Properties**.</span></span>  
  
2.  <span data-ttu-id="f804b-109">选择 **“边框”** ，然后单击要应用于图表的边框类型。</span><span class="sxs-lookup"><span data-stu-id="f804b-109">Select **Border**, and click the type of border to apply to the chart.</span></span>  
  
3.  <span data-ttu-id="f804b-110">（可选）选择一个值或键入一个表示边框样式的表达式。</span><span class="sxs-lookup"><span data-stu-id="f804b-110">(Optional) Select a value or type an expression that represents the style of the border.</span></span>  
  
4.  <span data-ttu-id="f804b-111">（可选）指定将绘制在图表周围作为边框的线条的颜色。</span><span class="sxs-lookup"><span data-stu-id="f804b-111">(Optional) Specify the color of the line that will be drawn around the chart as the border.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f804b-112">**“线条颜色”** 列表中包括常用颜色。</span><span class="sxs-lookup"><span data-stu-id="f804b-112">The **Line color** list contains common colors.</span></span> <span data-ttu-id="f804b-113">若要在更多颜色列表中进行选择，请在列表中单击“更多颜色”，或单击列表旁的表达式 (fx) 按钮以打开“表达式”编辑器    。</span><span class="sxs-lookup"><span data-stu-id="f804b-113">If you want to select from a list of more colors, click **More colors** in the list or click the expression (**fx**) button next to the list to bring up the **Expression** editor.</span></span>  
  
5.  <span data-ttu-id="f804b-114">（可选）指定边框的宽度。</span><span class="sxs-lookup"><span data-stu-id="f804b-114">(Optional) Specify the width of the border.</span></span> <span data-ttu-id="f804b-115">有效值介于 0.25pt 到 20pt 之间。</span><span class="sxs-lookup"><span data-stu-id="f804b-115">Valid values are between 0.25pt and 20pt.</span></span> <span data-ttu-id="f804b-116">可以考虑将边框的大小保持在 1pt 到 3pt 之间，以获得最佳视觉效果。</span><span class="sxs-lookup"><span data-stu-id="f804b-116">Consider keeping the size of your border to between 1 and 3pt for the best visual effect.</span></span>  
  
6.  <span data-ttu-id="f804b-117">（可选）如果报表包含白色之外的背景色，可以考虑定义同一种颜色的页面颜色。</span><span class="sxs-lookup"><span data-stu-id="f804b-117">(Optional) If your report contains a background color other than white, consider defining a page color that is the same color.</span></span> <span data-ttu-id="f804b-118">页面颜色是边框线外部的背景色。</span><span class="sxs-lookup"><span data-stu-id="f804b-118">The page color is the background color outside of the border line.</span></span>  
  
7.  <span data-ttu-id="f804b-119">（可选）如果选择“框架”类型，则可为该框架指定样式和颜色。</span><span class="sxs-lookup"><span data-stu-id="f804b-119">(Optional) If you choose a Frame type, specify a style and color for the frame.</span></span> <span data-ttu-id="f804b-120">**“框架填充颜色”** 列表中包括常用颜色。</span><span class="sxs-lookup"><span data-stu-id="f804b-120">The **Frame fill color** list contains common colors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f804b-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f804b-121">See Also</span></span>  
 <span data-ttu-id="f804b-122">[图表（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f804b-122">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f804b-123">[设置图表格式（报表生成器和 SSRS）](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f804b-123">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f804b-124">向图表添加凹凸效果、阳文和纹理样式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="f804b-124">Add Bevel, Emboss, and Texture Styles to a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-effects-add-bevel-emboss-or-texture-report-builder.md)  
  
  
