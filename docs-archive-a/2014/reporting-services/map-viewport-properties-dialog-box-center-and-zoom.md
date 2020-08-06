---
title: "\"地图视区属性\" 对话框-\"中心和缩放\" |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapviewport.centerandzoom.f1
- "10506"
ms.assetid: 642a06f5-293f-48e0-97a6-1489dbefa719
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 913c00773abf71ca627b8cc2a94a873484e8ab30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580048"
---
# <a name="map-viewport-properties-dialog-box-center-and-zoom"></a><span data-ttu-id="b6f83-102">“地图视区属性”对话框 -&gt;“中心和缩放”</span><span class="sxs-lookup"><span data-stu-id="b6f83-102">Map Viewport Properties Dialog Box, Center and Zoom</span></span>
  <span data-ttu-id="b6f83-103">选择 **“地图视区属性”** 对话框中的 **“中心和缩放”** 可以设置地图的中心视图和缩放系数。</span><span class="sxs-lookup"><span data-stu-id="b6f83-103">Select **Center and Zoom** for the **Map Viewport Properties** dialog box to set the center view and zoom factor for a map.</span></span> <span data-ttu-id="b6f83-104">指定地图数据源和要在报表中包含的地图的边界后，可以指定视图中心和缩放系数以进一步控制地图的显示。</span><span class="sxs-lookup"><span data-stu-id="b6f83-104">After you specify a map data source and the boundaries of the map that you want to include in your report, you can specify the view center and the zoom factor to further control the map display.</span></span> <span data-ttu-id="b6f83-105">根据用于指定中心和缩放值的不同方法，选项也会不同。</span><span class="sxs-lookup"><span data-stu-id="b6f83-105">Options change depending on which method you use to specify the center and zoom values.</span></span> <span data-ttu-id="b6f83-106">单击 **“表达式”** (*fx*) 按钮以编辑设置该选项的值的表达式。</span><span class="sxs-lookup"><span data-stu-id="b6f83-106">Click the **Expression** (*fx*) button to edit an expression that sets the value of the option.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b6f83-107">选项</span><span class="sxs-lookup"><span data-stu-id="b6f83-107">Options</span></span>  
 <span data-ttu-id="b6f83-108">**设置视图中心和缩放级别**</span><span class="sxs-lookup"><span data-stu-id="b6f83-108">**Set a view center and zoom level**</span></span>  
 <span data-ttu-id="b6f83-109">选择此选项可以指定视图中心和缩放级别的自定义值。</span><span class="sxs-lookup"><span data-stu-id="b6f83-109">Choose this option to specify custom values for the view center and the zoom level.</span></span>  
  
 <span data-ttu-id="b6f83-110">**将地图居中以显示地图层**</span><span class="sxs-lookup"><span data-stu-id="b6f83-110">**Center map to show a map layer**</span></span>  
 <span data-ttu-id="b6f83-111">选择此选项可以指定一个层并自动使视图位于其地图数据的中心。</span><span class="sxs-lookup"><span data-stu-id="b6f83-111">Choose this option to specify a layer and automatically center the view on its map data.</span></span> <span data-ttu-id="b6f83-112">例如，使视图位于 LineLayer1 的中心。</span><span class="sxs-lookup"><span data-stu-id="b6f83-112">For example, center the view on LineLayer1.</span></span>  
  
 <span data-ttu-id="b6f83-113">**将地图居中以显示嵌入的地图元素**</span><span class="sxs-lookup"><span data-stu-id="b6f83-113">**Center map to show an embedded map element**</span></span>  
 <span data-ttu-id="b6f83-114">选择此选项可以使视图位于特定的数据绑定地图元素的中心。</span><span class="sxs-lookup"><span data-stu-id="b6f83-114">Choose this option to center the view on a specific data-bound map element.</span></span> <span data-ttu-id="b6f83-115">空间数据必须与分析数据具有某种关系才能指定此选项。</span><span class="sxs-lookup"><span data-stu-id="b6f83-115">The spatial data must have a relationship with analytical data to specify this option.</span></span>  
  
 <span data-ttu-id="b6f83-116">例如，将视图位于这样的地图元素中心：匹配字段的名称为 [City] 且匹配值为“Seattle”。</span><span class="sxs-lookup"><span data-stu-id="b6f83-116">For example, center the view on the map element where the name of the match field is [City] and the match value is "Seattle".</span></span>  
  
 <span data-ttu-id="b6f83-117">**将地图居中以显示所有数据绑定地图元素**</span><span class="sxs-lookup"><span data-stu-id="b6f83-117">**Center map to show all data-bound map elements**</span></span>  
 <span data-ttu-id="b6f83-118">选择此选项可以将视图位于此层中所有地图元素的中心。</span><span class="sxs-lookup"><span data-stu-id="b6f83-118">Choose this option to center the view on all map elements in the layer.</span></span> <span data-ttu-id="b6f83-119">空间数据必须与分析数据具有某种关系才能指定此选项。</span><span class="sxs-lookup"><span data-stu-id="b6f83-119">The spatial data must have a relationship with analytical data to specify this option.</span></span>  
  
 <span data-ttu-id="b6f83-120">例如，将视图位于显示城市的多边形气泡图层的中心，且气泡大小与人口数有关。</span><span class="sxs-lookup"><span data-stu-id="b6f83-120">For example, center the view on the polygon bubble layer that shows cities and the bubble size is related to population.</span></span> <span data-ttu-id="b6f83-121">在计算视区的中心时，只包括具有匹配人口数值的那些城市。</span><span class="sxs-lookup"><span data-stu-id="b6f83-121">Only those cities with a matching population value are included when calculating the center for the viewport.</span></span>  
  
 <span data-ttu-id="b6f83-122">**中心和缩放选项**</span><span class="sxs-lookup"><span data-stu-id="b6f83-122">**Center and zoom options**</span></span>  
 <span data-ttu-id="b6f83-123">选择一个选项来指定视图中心和缩放级别。</span><span class="sxs-lookup"><span data-stu-id="b6f83-123">Select an option to specify the view center and zoom level.</span></span>  
  
 <span data-ttu-id="b6f83-124">**视图中心(X) %**</span><span class="sxs-lookup"><span data-stu-id="b6f83-124">**View center (X) %**</span></span>  
 <span data-ttu-id="b6f83-125">水平坐标。</span><span class="sxs-lookup"><span data-stu-id="b6f83-125">The horizontal coordinate.</span></span> <span data-ttu-id="b6f83-126">默认值 50% 表示</span><span class="sxs-lookup"><span data-stu-id="b6f83-126">The default value, 50%.</span></span> <span data-ttu-id="b6f83-127">将视图中心位于最小水平值和最大水平值之间的中点。</span><span class="sxs-lookup"><span data-stu-id="b6f83-127">centers the view at the midpoint between the minimum and maximum horizontal values.</span></span>  
  
 <span data-ttu-id="b6f83-128">**视图中心(Y) %**</span><span class="sxs-lookup"><span data-stu-id="b6f83-128">**View center (Y) %**</span></span>  
 <span data-ttu-id="b6f83-129">垂直坐标。</span><span class="sxs-lookup"><span data-stu-id="b6f83-129">The vertical coordinate.</span></span> <span data-ttu-id="b6f83-130">默认值 50% 表示将视图中心位于最小垂直值和最大垂直值之间的中点。</span><span class="sxs-lookup"><span data-stu-id="b6f83-130">The default value, 50%, centers the view at the midpoint between the minimum and maximum vertical values.</span></span>  
  
 <span data-ttu-id="b6f83-131">**缩放级别(%)**</span><span class="sxs-lookup"><span data-stu-id="b6f83-131">**Zoom level (%)**</span></span>  
 <span data-ttu-id="b6f83-132">缩放系数。</span><span class="sxs-lookup"><span data-stu-id="b6f83-132">The zoom factor.</span></span> <span data-ttu-id="b6f83-133">默认值 100% 表示不放大。</span><span class="sxs-lookup"><span data-stu-id="b6f83-133">The default value, 100%, indicates no magnification.</span></span>  
  
 <span data-ttu-id="b6f83-134">**将此层上的视图居中**</span><span class="sxs-lookup"><span data-stu-id="b6f83-134">**Center view on this layer**</span></span>  
 <span data-ttu-id="b6f83-135">指定层的名称。</span><span class="sxs-lookup"><span data-stu-id="b6f83-135">Specify the name of the layer.</span></span>  
  
 <span data-ttu-id="b6f83-136">**在地图元素满足此条件时将视图居中**</span><span class="sxs-lookup"><span data-stu-id="b6f83-136">**Center view on the map element that matches this condition**</span></span>  
 <span data-ttu-id="b6f83-137">显示的只读字段用于将地图数据与分析数据匹配。</span><span class="sxs-lookup"><span data-stu-id="b6f83-137">The read-only field that is displayed is used to match map data and analytical data.</span></span> <span data-ttu-id="b6f83-138">指定要匹配的值。</span><span class="sxs-lookup"><span data-stu-id="b6f83-138">Specify the value that you want to match on.</span></span> <span data-ttu-id="b6f83-139">视图将自动在此地图元素上居中。</span><span class="sxs-lookup"><span data-stu-id="b6f83-139">The view automatically centers on this map element.</span></span> <span data-ttu-id="b6f83-140">例如，NAME = TEXAS。</span><span class="sxs-lookup"><span data-stu-id="b6f83-140">For example, NAME = TEXAS.</span></span> <span data-ttu-id="b6f83-141">默认情况下，条件的数据类型是 String 且匹配区分大小写。</span><span class="sxs-lookup"><span data-stu-id="b6f83-141">By default, the data type for the condition is String and the match is case-sensitive.</span></span>  
  
 <span data-ttu-id="b6f83-142">若要匹配具有不同数据类型的字段，必须编写一个计算结果为该数据类型的表达式。</span><span class="sxs-lookup"><span data-stu-id="b6f83-142">To match on a field that has a different data type, you must write an expression that evaluates to that data type.</span></span> <span data-ttu-id="b6f83-143">例如，如果匹配字段为存储为整数的 5 个数字的邮政编码，则若要指定邮政编码 98053，必须使用表达式 =98053。</span><span class="sxs-lookup"><span data-stu-id="b6f83-143">For example, if the match field is a 5 digit postal code that is stored as an integer, then to specify the postal code 98053, you must use the expression =98053.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6f83-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b6f83-144">See Also</span></span>  
 [<span data-ttu-id="b6f83-145">地图（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="b6f83-145">Maps &#40;Report Builder and SSRS&#41;</span></span>](report-design/maps-report-builder-and-ssrs.md)  
  
  
