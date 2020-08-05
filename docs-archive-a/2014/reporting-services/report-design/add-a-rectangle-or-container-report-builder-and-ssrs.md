---
title: 添加矩形或容器（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10061"
- sql12.rtp.rptdesigner.rectangleproperties.general.f1
ms.assetid: f905c35f-754d-4d02-80f3-85e29ddda826
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5fddda2f02b9f370d9742ae6add5bae444f8f55f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577285"
---
# <a name="add-a-rectangle-or-container-report-builder-and-ssrs"></a><span data-ttu-id="8b113-102">添加矩形或容器（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="8b113-102">Add a Rectangle or Container (Report Builder and SSRS)</span></span>
  <span data-ttu-id="8b113-103">如果希望使用图形元素分隔报表的各部分、强调某些报表区或为一个或多个报表项提供背景，则可以向报表中添加矩形。</span><span class="sxs-lookup"><span data-stu-id="8b113-103">Add a rectangle to your report when you want a graphical element to separate areas of the report, emphasize areas of a report, or provide a background for one or more report items.</span></span> <span data-ttu-id="8b113-104">矩形还可以用作容器，以控制数据区域在报表中的呈现方式。</span><span class="sxs-lookup"><span data-stu-id="8b113-104">Rectangles are also used as containers to help control the way data regions render in a report.</span></span> <span data-ttu-id="8b113-105">可以通过编辑矩形属性（如背景和边框颜色）自定义矩形的外观。</span><span class="sxs-lookup"><span data-stu-id="8b113-105">You can customize the appearance of a rectangle by editing rectangle properties such as the background and border colors.</span></span> <span data-ttu-id="8b113-106">有关使用矩形作为容器的详细信息，请参阅[矩形和线条（报表生成器和 SSRS）](rectangles-and-lines-report-builder-and-ssrs.md)和[在矩阵和图表中显示相同数据（报表生成器）](display-the-same-data-on-a-matrix-and-a-chart-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="8b113-106">For more information about using a rectangle as a container, see [Rectangles and Lines &#40;Report Builder and SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md) and [Display the Same Data on a Matrix and a Chart &#40;Report Builder&#41;](display-the-same-data-on-a-matrix-and-a-chart-report-builder.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-rectangle"></a><span data-ttu-id="8b113-107">添加矩形</span><span class="sxs-lookup"><span data-stu-id="8b113-107">To add a rectangle</span></span>  
  
1.  <span data-ttu-id="8b113-108">在 **“插入”** 选项卡的 **“报表项”** 组中，单击 **“矩形”** 。</span><span class="sxs-lookup"><span data-stu-id="8b113-108">On the **Insert** tab, in the **Report Items** group, click **Rectangle.**</span></span>  
  
2.  <span data-ttu-id="8b113-109">在设计图面上，单击希望矩形左上角所处的位置，并拖动至希望矩形右下角所处的位置。</span><span class="sxs-lookup"><span data-stu-id="8b113-109">On the design surface, click the location where you want the upper left corner of the rectangle, and drag to where you want the lower-right corner.</span></span>  
  
     <span data-ttu-id="8b113-110">请注意，当移动游标时，“对齐线”将以游标行的形式与其他对象一起显示在设计图面上。</span><span class="sxs-lookup"><span data-stu-id="8b113-110">Note that as you move the cursor, "snap lines" appear as the cursor lines up with other objects on the design surface.</span></span> <span data-ttu-id="8b113-111">如果您要使对象对齐，这些对齐线将对您很有帮助。</span><span class="sxs-lookup"><span data-stu-id="8b113-111">These help you if you want objects to be aligned.</span></span>  
  
### <a name="to-create-a-container"></a><span data-ttu-id="8b113-112">创建容器</span><span class="sxs-lookup"><span data-stu-id="8b113-112">To create a container</span></span>  
  
1.  <span data-ttu-id="8b113-113">向报表中添加矩形报表项。</span><span class="sxs-lookup"><span data-stu-id="8b113-113">Add a rectangle report item to the report.</span></span>  
  
2.  <span data-ttu-id="8b113-114">将其他报表项拖到矩形中。</span><span class="sxs-lookup"><span data-stu-id="8b113-114">Drag other report items into the rectangle.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8b113-115">矩形是可在其中创建项或将项拖到其中的唯一容器。</span><span class="sxs-lookup"><span data-stu-id="8b113-115">A rectangle is only a container for items that you either create in the rectangle or drag into the rectangle.</span></span> <span data-ttu-id="8b113-116">如果您在设计图面上现有项的周围绘制一个矩形，则此矩形不会充当该项的容器。</span><span class="sxs-lookup"><span data-stu-id="8b113-116">If you draw a rectangle around an item that already exists on the design surface, the rectangle will not act as its container.</span></span>  
  
### <a name="to-change-rectangle-properties-such-as-color-style-or-weight"></a><span data-ttu-id="8b113-117">更改矩形的属性（如颜色、样式或粗细）</span><span class="sxs-lookup"><span data-stu-id="8b113-117">To change rectangle properties such as color, style, or weight</span></span>  
  
1.  <span data-ttu-id="8b113-118">选择矩形，然后在“主页”选项卡的 **“边框”** 部分单击线条的颜色、样式或粗细选项。</span><span class="sxs-lookup"><span data-stu-id="8b113-118">Select the rectangle, and then click the line color, style, or weight options in the **Border** section of the Home tab.</span></span>  
  
2.  <span data-ttu-id="8b113-119">单击 **“边框”** 按钮旁的箭头以确定要更改矩形的哪些边。</span><span class="sxs-lookup"><span data-stu-id="8b113-119">Click the arrow next to the **Border** button to determine which sides of the rectangle to change.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8b113-120">如果将线条样式设置为 "**双**线" 并且线条宽度为 1 1/2 磅或更窄，则在报表生成器、报表设计器或报表管理器中运行报表时，线条可能不会显示为双线。</span><span class="sxs-lookup"><span data-stu-id="8b113-120">If you set the line style to **Double** and the line width is 1 1/2 pt or narrower, the line may not appear double when you run the report in Report Builder, Report Designer, or Report Manager.</span></span> <span data-ttu-id="8b113-121">将报表导出为其他格式（例如 Microsoft Word 和 Acrobat PDF）后，线条会显示为双线。</span><span class="sxs-lookup"><span data-stu-id="8b113-121">It will appear double when you export the report to other formats such as Microsoft Word and Acrobat PDF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b113-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8b113-122">See Also</span></span>  
 <span data-ttu-id="8b113-123">[矩形和线条（报表生成器和 SSRS）](rectangles-and-lines-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8b113-123">[Rectangles and Lines &#40;Report Builder and SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="8b113-124">呈现行为（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="8b113-124">Rendering Behaviors &#40;Report Builder  and SSRS&#41;</span></span>](rendering-behaviors-report-builder-and-ssrs.md)  
  
  
