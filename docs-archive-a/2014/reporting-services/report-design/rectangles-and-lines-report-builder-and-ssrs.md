---
title: 矩形和线条（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d6226b0c-0398-4185-8565-96099876fc21
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 96b795c3edeabb938e836be3486e28e08737a8e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590049"
---
# <a name="rectangles-and-lines-report-builder-and-ssrs"></a><span data-ttu-id="de4ee-102">矩形和线条（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="de4ee-102">Rectangles and Lines (Report Builder and SSRS)</span></span>
  <span data-ttu-id="de4ee-103">使用矩形和线条可在报表中创建各种视觉效果。</span><span class="sxs-lookup"><span data-stu-id="de4ee-103">Rectangles and lines can create visual effects within a report.</span></span> <span data-ttu-id="de4ee-104">您可以在“主页”选项卡的“边框”部分设置这些报表项的显示属性，还可以使用“属性”窗格设置其他属性。</span><span class="sxs-lookup"><span data-stu-id="de4ee-104">You can set display properties on these report items from the Border section of the Home tab, and set other properties by using the Properties pane.</span></span> <span data-ttu-id="de4ee-105">可以为矩形添加类似背景色或图像、工具提示或书签这样的功能。</span><span class="sxs-lookup"><span data-stu-id="de4ee-105">You can add features like a background color or image, a tooltip, or a bookmark to a rectangle.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="rectangles-and-lines-as-report-parts"></a><a name="RectanglesLinesReportParts"></a> <span data-ttu-id="de4ee-106">将矩形和线条作为报表部件</span><span class="sxs-lookup"><span data-stu-id="de4ee-106">Rectangles and Lines as Report Parts</span></span>  
 <span data-ttu-id="de4ee-107">您可以将矩形与它们所包含的项作为报表部件与报表分开发布。</span><span class="sxs-lookup"><span data-stu-id="de4ee-107">You can publish rectangles with the items that they contain separately from the report as report parts.</span></span> [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
 <span data-ttu-id="de4ee-108">不能将该矩形中的报表项作为报表部件发布。</span><span class="sxs-lookup"><span data-stu-id="de4ee-108">You cannot publish the report items within the rectangle as report parts.</span></span> <span data-ttu-id="de4ee-109">当用户向报表添加该矩形时，他们将获取该矩形及其包含的项。</span><span class="sxs-lookup"><span data-stu-id="de4ee-109">When people add the rectangle to a report, they get the rectangle and the items it contains.</span></span>  
  

  
##  <a name="using-a-rectangle-as-a-container"></a><a name="RectangleAsContainer"></a><span data-ttu-id="de4ee-110">使用矩形作为容器</span><span class="sxs-lookup"><span data-stu-id="de4ee-110">Using a Rectangle as a Container</span></span>  
 <span data-ttu-id="de4ee-111">可以将矩形用作其他项的容器。</span><span class="sxs-lookup"><span data-stu-id="de4ee-111">You can use a rectangle as a container for other items.</span></span> <span data-ttu-id="de4ee-112">移动矩形时，其中包含的项也将随之一起移动。</span><span class="sxs-lookup"><span data-stu-id="de4ee-112">When you move the rectangle, the items that are contained within the rectangle move along with it.</span></span> <span data-ttu-id="de4ee-113">矩形中的项在其 **Parent** 属性中显示该矩形的名称。</span><span class="sxs-lookup"><span data-stu-id="de4ee-113">An item within the rectangle shows the name of the rectangle in its **Parent** property.</span></span> <span data-ttu-id="de4ee-114">有关使用矩形作为容器的详细信息，请参阅[添加矩形或容器（报表生成器和 SSRS）](add-a-rectangle-or-container-report-builder-and-ssrs.md)和[在矩阵和图表中显示相同数据（报表生成器）](display-the-same-data-on-a-matrix-and-a-chart-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="de4ee-114">For more information about using a rectangle as a container, see [Add a Rectangle or Container &#40;Report Builder and SSRS&#41;](add-a-rectangle-or-container-report-builder-and-ssrs.md) and [Display the Same Data on a Matrix and a Chart &#40;Report Builder&#41;](display-the-same-data-on-a-matrix-and-a-chart-report-builder.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="de4ee-115">矩形是可在其中创建项或将项拖到其中的唯一容器。</span><span class="sxs-lookup"><span data-stu-id="de4ee-115">A rectangle is only a container for items that you either create in the rectangle or drag into the rectangle.</span></span> <span data-ttu-id="de4ee-116">如果您在设计图面上现有项的周围绘制一个矩形，则此矩形不会充当该项的容器。</span><span class="sxs-lookup"><span data-stu-id="de4ee-116">If you draw a rectangle around an item that already exists on the design surface, the rectangle will not act as its container.</span></span> <span data-ttu-id="de4ee-117">矩形不会在项的 Parent 属性中列出。</span><span class="sxs-lookup"><span data-stu-id="de4ee-117">The rectangle will not be listed in the item's Parent property.</span></span>  
  
 <span data-ttu-id="de4ee-118">使用矩形来包含报表项时，请考虑在报表呈现期间这些项作为整体将受到怎样的影响。</span><span class="sxs-lookup"><span data-stu-id="de4ee-118">When using rectangles to contain report items, consider how the items will be affected as a whole during report rendering.</span></span> <span data-ttu-id="de4ee-119">包含重复数据行（例如，表）的报表项将展开，以容纳查询所返回的数据，这将影响矩形中其他项的定位。</span><span class="sxs-lookup"><span data-stu-id="de4ee-119">Report items that contain repeated rows of data (for example, tables) will expand to accommodate the data that is returned by a query, and this affects the positioning of other items in the rectangle.</span></span> <span data-ttu-id="de4ee-120">如果将项定位于数据区域的下面，表将使这些项下移。</span><span class="sxs-lookup"><span data-stu-id="de4ee-120">A table will push items down if they are positioned below the data region.</span></span> <span data-ttu-id="de4ee-121">若要将项定位到合适的位置，您可以将报表项放在矩形内，该矩形的上边缘要在表的下边缘之上。</span><span class="sxs-lookup"><span data-stu-id="de4ee-121">To anchor an item in place, you can place the report item inside of a rectangle that has an upper edge above the lower edge of the table.</span></span> <span data-ttu-id="de4ee-122">有关详细信息，请参阅[呈现行为（报表生成器和 SSRS）](rendering-behaviors-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="de4ee-122">For more information, see [Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="adding-a-report-border"></a><a name="ReportBorder"></a> <span data-ttu-id="de4ee-123">添加报表边框</span><span class="sxs-lookup"><span data-stu-id="de4ee-123">Adding a Report Border</span></span>  
 <span data-ttu-id="de4ee-124">通过向表头、表尾和表体本身添加边框（而不是添加线条或矩形），可以为报表添加边框。</span><span class="sxs-lookup"><span data-stu-id="de4ee-124">You can add a border to a report by adding borders to the headers, footers, and report body themselves, without adding lines or rectangles.</span></span> <span data-ttu-id="de4ee-125">有关详细信息，请参阅 [向报表添加边框（报表生成器和 SSRS）](add-a-border-to-a-report-report-builder-and-ssrs.md)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="de4ee-125">For more information, see [Add a Border to a Report &#40;Report Builder and SSRS&#41;](add-a-border-to-a-report-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="de4ee-126">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="de4ee-126">How-To Topics</span></span>  
 [<span data-ttu-id="de4ee-127">向报表添加边框（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="de4ee-127">Add a Border to a Report &#40;Report Builder and SSRS&#41;</span></span>](add-a-border-to-a-report-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="de4ee-128">添加矩形或容器（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="de4ee-128">Add a Rectangle or Container &#40;Report Builder and SSRS&#41;</span></span>](add-a-rectangle-or-container-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="de4ee-129">添加和修改线条（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="de4ee-129">Add and Modify a Line &#40;Report Builder and SSRS&#41;</span></span>](add-and-modify-a-line-report-builder-and-ssrs.md)  
  
## <a name="see-also"></a><span data-ttu-id="de4ee-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="de4ee-130">See Also</span></span>  
 [<span data-ttu-id="de4ee-131">添加矩形或容器（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="de4ee-131">Add a Rectangle or Container &#40;Report Builder and SSRS&#41;</span></span>](add-a-rectangle-or-container-report-builder-and-ssrs.md)  
  
  
