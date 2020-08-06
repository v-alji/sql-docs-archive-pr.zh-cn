---
title: 向地图添加自定义位置（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- MICROSOFT.REPORTDESIGNER.MAPPOINT.POINTTEMPLATE
ms.assetid: 7d36faae-5bcc-446a-9eba-f42349cafacb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 167558534280f08d576205b5ff1b94d0588fcb78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692280"
---
# <a name="add-custom-locations-to-a-map-report-builder-and-ssrs"></a><span data-ttu-id="db6a6-102">向地图添加自定义位置（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="db6a6-102">Add Custom Locations to a Map (Report Builder and SSRS)</span></span>
  <span data-ttu-id="db6a6-103">向报表添加地图之后，可以添加您自己的点位置。</span><span class="sxs-lookup"><span data-stu-id="db6a6-103">After you add a map to a report, you can add your own point locations.</span></span>  
  
 <span data-ttu-id="db6a6-104">通过设置层的点属性的选项来控制层上所有点的显示属性。</span><span class="sxs-lookup"><span data-stu-id="db6a6-104">Display properties for all points on a layer are controlled by setting options for the point properties for the layer.</span></span> <span data-ttu-id="db6a6-105">对于所选的嵌入点，可以覆盖这些显示属性。</span><span class="sxs-lookup"><span data-stu-id="db6a6-105">For a selected embedded point, you can override the display properties.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db6a6-106">覆盖该嵌入点的层显示属性时，您所做的更改无法还原。</span><span class="sxs-lookup"><span data-stu-id="db6a6-106">When you override the layer display properties for the embedded point, the changes that you make are not reversible.</span></span>  
  
 <span data-ttu-id="db6a6-107">有关详细信息，请参阅 [按规则和分析数据更改多边形、线条和点的显示方式（报表生成器和 SSRS）](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)。</span><span class="sxs-lookup"><span data-stu-id="db6a6-107">For more information, see [Vary Polygon, Line, and Point Display by Rules and Analytical Data &#40;Report Builder and SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-point-layer"></a><span data-ttu-id="db6a6-108">添加点层</span><span class="sxs-lookup"><span data-stu-id="db6a6-108">To add a point layer</span></span>  
  
1.  <span data-ttu-id="db6a6-109">在报表设计图面中，单击该地图以选择它并显示“地图”窗格。</span><span class="sxs-lookup"><span data-stu-id="db6a6-109">On the report design surface, click the map to select it and display the Map pane.</span></span>  
  
2.  <span data-ttu-id="db6a6-110">在工具栏中，单击 **“添加层”** 。</span><span class="sxs-lookup"><span data-stu-id="db6a6-110">On the toolbar, click **Add Layer**.</span></span>  
  
3.  <span data-ttu-id="db6a6-111">从下拉列表中，单击“添加点层”  。</span><span class="sxs-lookup"><span data-stu-id="db6a6-111">From the drop-down list, click **Add Point Layer**.</span></span> <span data-ttu-id="db6a6-112">将不包含点的点层添加到该地图。</span><span class="sxs-lookup"><span data-stu-id="db6a6-112">A point layer with no points is added to the map.</span></span> <span data-ttu-id="db6a6-113">默认情况下，为嵌入的点准备了点层。</span><span class="sxs-lookup"><span data-stu-id="db6a6-113">By default, the point layer is ready for embedded points.</span></span>  
  
### <a name="to-add-a-custom-point"></a><span data-ttu-id="db6a6-114">添加自定义点</span><span class="sxs-lookup"><span data-stu-id="db6a6-114">To add a custom point</span></span>  
  
1.  <span data-ttu-id="db6a6-115">在报表设计图面中，单击该地图以选择它并显示“地图”窗格。</span><span class="sxs-lookup"><span data-stu-id="db6a6-115">On the report design surface, click the map to select it and display the Map pane.</span></span>  
  
2.  <span data-ttu-id="db6a6-116">在“地图”窗格中，右键单击具有类型“嵌入”  的点层，然后单击“添加点”  。</span><span class="sxs-lookup"><span data-stu-id="db6a6-116">In the Map pane, right-click a point layer that has type **Embedded**, and then click **Add Point**.</span></span> <span data-ttu-id="db6a6-117">光标将变为十字准线。</span><span class="sxs-lookup"><span data-stu-id="db6a6-117">The cursor changes to crosshairs.</span></span>  
  
3.  <span data-ttu-id="db6a6-118">若要添加点，请单击地图上的某个位置。</span><span class="sxs-lookup"><span data-stu-id="db6a6-118">To add a point, click a location on the map.</span></span> <span data-ttu-id="db6a6-119">在您单击的位置将嵌入的点添加到所选层中。</span><span class="sxs-lookup"><span data-stu-id="db6a6-119">An embedded point is added to the selected layer at the location where you click.</span></span>  
  
### <a name="to-customize-the-display-for-an-embedded-point"></a><span data-ttu-id="db6a6-120">自定义嵌入点的显示方式</span><span class="sxs-lookup"><span data-stu-id="db6a6-120">To customize the display for an embedded point</span></span>  
  
1.  <span data-ttu-id="db6a6-121">右键单击该点，然后单击“点属性”  。</span><span class="sxs-lookup"><span data-stu-id="db6a6-121">Right-click the point, and then click **Point Properties**.</span></span> <span data-ttu-id="db6a6-122">将打开 **“地图嵌入点属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="db6a6-122">The **Map Embedded Point Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="db6a6-123">单击 **“覆盖此层的点选项”** 。</span><span class="sxs-lookup"><span data-stu-id="db6a6-123">Click **Override point options for this layer**.</span></span> <span data-ttu-id="db6a6-124">将在左窗格中显示多个属性页。</span><span class="sxs-lookup"><span data-stu-id="db6a6-124">Multiple property pages appear in the left pane.</span></span>  
  
3.  <span data-ttu-id="db6a6-125">单击这些页并设置要应用到此点的显示属性。</span><span class="sxs-lookup"><span data-stu-id="db6a6-125">Click the pages and set the display properties that you want to apply to this point.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db6a6-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="db6a6-126">See Also</span></span>  
 <span data-ttu-id="db6a6-127">[地图（报表生成器和 SSRS）](maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="db6a6-127">[Maps &#40;Report Builder and SSRS&#41;](maps-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="db6a6-128">按规则和分析数据更改多边形、线条和点的显示方式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="db6a6-128">Vary Polygon, Line, and Point Display by Rules and Analytical Data &#40;Report Builder and SSRS&#41;</span></span>](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)  
  
  
