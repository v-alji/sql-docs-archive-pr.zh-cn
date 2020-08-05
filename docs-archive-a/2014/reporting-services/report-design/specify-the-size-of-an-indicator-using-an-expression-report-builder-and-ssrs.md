---
title: 使用表达式指定指示器的大小（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ab0b86f1-4882-4258-a2b6-c612faecfa4b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b450abb957329b8dbaa4f7f0e4c963c5f63f06b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577256"
---
# <a name="specify-the-size-of-an-indicator-using-an-expression-report-builder-and-ssrs"></a><span data-ttu-id="d73b1-102">使用表达式指定指示器的大小（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="d73b1-102">Specify the Size of an Indicator Using an Expression (Report Builder and SSRS)</span></span>
  <span data-ttu-id="d73b1-103">除了颜色、方向和形状外，您还可以使用大小来提供最佳的指示器视觉效果。</span><span class="sxs-lookup"><span data-stu-id="d73b1-103">In addition to color, direction, and shape, you can use size to maximize the visual impact of indicators.</span></span>  
  
 <span data-ttu-id="d73b1-104">指示器具有名为 IndicatorStates 的指示器状态的集合。</span><span class="sxs-lookup"><span data-stu-id="d73b1-104">An indicator has a collection of indicator states named IndicatorStates.</span></span> <span data-ttu-id="d73b1-105">IndicatorStates 集合通常具有多个状态。</span><span class="sxs-lookup"><span data-stu-id="d73b1-105">The IndicatorStates collection typically have multiple states.</span></span> <span data-ttu-id="d73b1-106">每个状态都是该集合的成员，并且由一个图标表示。</span><span class="sxs-lookup"><span data-stu-id="d73b1-106">Each state is a member of the collection and is represented by an icon.</span></span> <span data-ttu-id="d73b1-107">这些状态一起构成了 IndicatorsStates 集合。</span><span class="sxs-lookup"><span data-stu-id="d73b1-107">Together the states constitute the IndicatorsStates collection.</span></span>  
  
 <span data-ttu-id="d73b1-108">若要动态配置图标大小，请在报表生成器的“属性”窗格中设置 IndicatorsStates 集合中各成员的属性。</span><span class="sxs-lookup"><span data-stu-id="d73b1-108">To dynamically configure the sizes of icons, you set properties of members of the IndicatorsStates collection in the Properties pane of Report Builder.</span></span> <span data-ttu-id="d73b1-109">如果 **“属性”** 窗格不可见，请单击 **“视图”** 选项卡，然后选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="d73b1-109">If the **Properties** pane is not visible, click the **View** tab and select **Properties**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d73b1-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，使用 **“属性”** 窗口以便设置成员属性。</span><span class="sxs-lookup"><span data-stu-id="d73b1-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you use the **Properties** window to set the member properties.</span></span> <span data-ttu-id="d73b1-111">如果 **“属性”** 窗口未打开，则按 F4 键。</span><span class="sxs-lookup"><span data-stu-id="d73b1-111">If the **Properties** window is not open, press the F4 key.</span></span>  
  
 <span data-ttu-id="d73b1-112">“属性”窗格提供对指示器的 IndicatorStates 集合的属性的访问  。</span><span class="sxs-lookup"><span data-stu-id="d73b1-112">The **Properties** pane provides access to the properties of the IndicatorStates collection of an indicator.</span></span> <span data-ttu-id="d73b1-113">可以通过使用表达式设置 IndicatorStates 集合成员的 ScaleFactor 属性，将图标配置为不同的大小。</span><span class="sxs-lookup"><span data-stu-id="d73b1-113">You configure the icons to be different sizes by setting the ScaleFactor property of the IndicatorStates collection members using an expression.</span></span> <span data-ttu-id="d73b1-114">有关详细信息，请参阅[表达式（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="d73b1-114">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="d73b1-115">在此过程中使用的表达式还用于生成具有不同大小的指示器的报表，如 [指示器（报表生成器和 SSRS）](indicators-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="d73b1-115">The expression used in this procedure was also used to generate the report with different sizes of indicators, shown in [Indicators &#40;Report Builder and SSRS&#41;](indicators-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-the-indicator-icon-size-using-an-expression"></a><span data-ttu-id="d73b1-116">使用表达式指定指示器图标大小</span><span class="sxs-lookup"><span data-stu-id="d73b1-116">To specify the indicator icon size using an expression</span></span>  
  
1.  <span data-ttu-id="d73b1-117">单击要更改的指示器。</span><span class="sxs-lookup"><span data-stu-id="d73b1-117">Click the indicator you want to change.</span></span>  
  
2.  <span data-ttu-id="d73b1-118">在“属性”窗格中找到 IndicatorStates 属性。</span><span class="sxs-lookup"><span data-stu-id="d73b1-118">In the Properties pane, locate the IndicatorStates property.</span></span>  
  
     <span data-ttu-id="d73b1-119">如果“属性”窗格按类别进行组织，则将在“状态”类别中找到 IndicatorStates  。</span><span class="sxs-lookup"><span data-stu-id="d73b1-119">If the Properties pane is organized by category, you will find IndicatorStates in the **States** category.</span></span>  
  
3.  <span data-ttu-id="d73b1-120">单击 IndicatorStates 旁的省略号 **(...)** 按钮。</span><span class="sxs-lookup"><span data-stu-id="d73b1-120">Click the ellipsis **(...)** button next to IndicatorStates.</span></span> <span data-ttu-id="d73b1-121">**“指示器状态集合编辑器”** 对话框将打开。</span><span class="sxs-lookup"><span data-stu-id="d73b1-121">The **IndicatorState Collection Editor** dialog box opens.</span></span>  
  
     <span data-ttu-id="d73b1-122">选择该集合的所有成员。</span><span class="sxs-lookup"><span data-stu-id="d73b1-122">Select all members of the collection.</span></span>  
  
4.  <span data-ttu-id="d73b1-123">在“多选属性”列表中，单击 ScaleFactor 旁的向下箭头，然后单击“表达式”   。</span><span class="sxs-lookup"><span data-stu-id="d73b1-123">In the **Multi-Select Properties** list, click the down arrow next to ScaleFactor and then click **Expression**.</span></span>  
  
5.  <span data-ttu-id="d73b1-124">在 **“表达式”** 对话框中，写入表达式。</span><span class="sxs-lookup"><span data-stu-id="d73b1-124">In the **Expression** dialog box write the expression.</span></span>  
  
     <span data-ttu-id="d73b1-125">下面的示例表达式基于 **SalesYTD** 字段的值使图标采用不同的大小。</span><span class="sxs-lookup"><span data-stu-id="d73b1-125">The following sample expression makes the icon a different size based on the value of the **SalesYTD** field.</span></span>  
  
     `=IIF(Fields!SalesYTD.value = 0,0,Fields!SalesYTD.value/Max(Fields!SalesYTD.value,"Indicator"))`  
  
     <span data-ttu-id="d73b1-126">有关详细信息，请参阅[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="d73b1-126">For more information, see [Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md).</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d73b1-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d73b1-127">See Also</span></span>  
 [<span data-ttu-id="d73b1-128">指示器（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="d73b1-128">Indicators &#40;Report Builder and SSRS&#41;</span></span>](indicators-report-builder-and-ssrs.md)  
  
  
