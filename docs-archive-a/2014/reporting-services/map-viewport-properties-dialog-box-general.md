---
title: "\"地图视区属性\" 对话框-\"常规\" |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapviewport.general.f1
- "10505"
ms.assetid: 6c9c773e-5c56-4571-95ed-8a157cfdfe52
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d760d6a0572cbbd1bd948eab382c0727eb276c4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577376"
---
# <a name="map-viewport-properties-dialog-box-general"></a><span data-ttu-id="74065-102">“地图视区属性”对话框 -&gt;“常规”</span><span class="sxs-lookup"><span data-stu-id="74065-102">Map Viewport Properties Dialog Box, General</span></span>
  <span data-ttu-id="74065-103">选择 **“地图视区属性”** 对话框中的 **“常规”** 可以更改坐标系统、投影和边界选项。</span><span class="sxs-lookup"><span data-stu-id="74065-103">Select **General** on the **Map Viewport Properties** dialog box to change the coordinate system, the projection, and the boundary options.</span></span>  
  
## <a name="options"></a><span data-ttu-id="74065-104">选项</span><span class="sxs-lookup"><span data-stu-id="74065-104">Options</span></span>  
 <span data-ttu-id="74065-105">**坐标系统**</span><span class="sxs-lookup"><span data-stu-id="74065-105">**Coordinate system**</span></span>  
 <span data-ttu-id="74065-106">指示地图数据使用的坐标系统的类型。</span><span class="sxs-lookup"><span data-stu-id="74065-106">Indicate the type of coordinate system that the map data uses.</span></span>  
  
-   <span data-ttu-id="74065-107">**平面数据** 当地图数据用 X 和 Y 坐标表示时选择此选项，例如用于建筑物规划。</span><span class="sxs-lookup"><span data-stu-id="74065-107">**Planar** Choose this option when map data is in X and Y coordinates, for example, for building plans.</span></span>  
  
-   <span data-ttu-id="74065-108">**地理** 当地图数据用经度和纬度坐标表示时选择此选项，例如用于城市位置。</span><span class="sxs-lookup"><span data-stu-id="74065-108">**Geographic** Choose this option when map data is in longitude and latitude coordinates, for example, for city locations.</span></span>  
  
 <span data-ttu-id="74065-109">**投影**</span><span class="sxs-lookup"><span data-stu-id="74065-109">**Projection**</span></span>  
 <span data-ttu-id="74065-110">指定用于将地理坐标投影到二维图面的方法。</span><span class="sxs-lookup"><span data-stu-id="74065-110">Specify the method to use to project geographic coordinates onto a two-dimensional surface.</span></span> <span data-ttu-id="74065-111">选择与将要可视化的数据兼容的投影。</span><span class="sxs-lookup"><span data-stu-id="74065-111">Choose a projection that is compatible with the data that you are visualizing.</span></span> <span data-ttu-id="74065-112">受投影影响的四个空间属性是区域、形状、距离和方向。</span><span class="sxs-lookup"><span data-stu-id="74065-112">The four spatial properties that are affected by projection are area, shape, distance, and direction.</span></span> <span data-ttu-id="74065-113">对于地球的视图，投影的选择取决于中心视图、地图边界和缩放系数。</span><span class="sxs-lookup"><span data-stu-id="74065-113">For views of the earth, a good choice of projection depends on the center view, the map boundaries, and the zoom factor.</span></span>  
  
 <span data-ttu-id="74065-114">以下的每个投影具有这些空间属性的一个或多个：</span><span class="sxs-lookup"><span data-stu-id="74065-114">Each of the following projections preserves one or more of these spatial properties:</span></span>  
  
-   <span data-ttu-id="74065-115">**Equirectangular** 选择此选项以将经度和纬度作为矩形坐标。</span><span class="sxs-lookup"><span data-stu-id="74065-115">**Equirectangular** Choose this option to use longitude and latitude as rectangular coordinates.</span></span>  
  
-   <span data-ttu-id="74065-116">**Mercator** 选择此常用投影用于赤道周围扭曲较少的较小区域，或者当您要添加具有使用 Mercator 投影的现有图块层的地图层时选择它。</span><span class="sxs-lookup"><span data-stu-id="74065-116">**Mercator** Choose this popular projection for smaller areas, for less distortion around the equator, or when you want to add a map layer with an existing tile layer that uses the Mercator projection.</span></span>  
  
-   <span data-ttu-id="74065-117">**Robinson** 选择此选项用于从赤道到极地的扭曲较少的大区域。</span><span class="sxs-lookup"><span data-stu-id="74065-117">**Robinson** Choose this option for less distortion of large areas that span from the equator to the poles.</span></span> <span data-ttu-id="74065-118">由 Arthur H. Robinson 在 1963 年开发。</span><span class="sxs-lookup"><span data-stu-id="74065-118">Developed by Arthur H. Robinson in 1963.</span></span>  
  
-   <span data-ttu-id="74065-119">**Fahey** 选择此选项用于从赤道到极地的扭曲较少的大区域。</span><span class="sxs-lookup"><span data-stu-id="74065-119">**Fahey** Choose this option for less distortion of large areas that span from the equator to the poles.</span></span> <span data-ttu-id="74065-120">由 Lawrence Fahey 在 1975 年开发。</span><span class="sxs-lookup"><span data-stu-id="74065-120">Developed by Lawrence Fahey in 1975.</span></span>  
  
-   <span data-ttu-id="74065-121">**Eckert1** 选择此选项可以使用等距的纬线和为直线的经线。</span><span class="sxs-lookup"><span data-stu-id="74065-121">**Eckert1** Choose this option to use equally spaced parallels in latitude and straight lines for meridians in longitude.</span></span>  
  
-   <span data-ttu-id="74065-122">**Eckert3** 选择此选项可以使用等距的纬线和为曲线的经线。</span><span class="sxs-lookup"><span data-stu-id="74065-122">**Eckert3** Choose this option to use equally spaced parallels in latitude and curved lines for meridians in longitude.</span></span>  
  
-   <span data-ttu-id="74065-123">**HammerAitoff** 选择此选项用于极地地图或世界地图。</span><span class="sxs-lookup"><span data-stu-id="74065-123">**HammerAitoff** Choose this option for polar maps or world maps.</span></span>  
  
-   <span data-ttu-id="74065-124">**Wagner3** 选择此选项用于世界地图。</span><span class="sxs-lookup"><span data-stu-id="74065-124">**Wagner3** Choose this option for world maps.</span></span>  
  
-   <span data-ttu-id="74065-125">**Bonne** 选择此选项可以查看地图中的各地地貌和城市等。</span><span class="sxs-lookup"><span data-stu-id="74065-125">**Bonne** Choose this option to view the world as it appears in an atlas.</span></span>  
  
 <span data-ttu-id="74065-126">**分页符选项**</span><span class="sxs-lookup"><span data-stu-id="74065-126">**Page break options**</span></span>  
 <span data-ttu-id="74065-127">选择所需选项以指示如何调整内容以使其适合报表页面。</span><span class="sxs-lookup"><span data-stu-id="74065-127">Select options to indicate how content is fitted to a report page.</span></span>  
  
 <span data-ttu-id="74065-128">**边界选项**</span><span class="sxs-lookup"><span data-stu-id="74065-128">**Boundary options**</span></span>  
 <span data-ttu-id="74065-129">指定坐标的上边界和下边界，以控制在报表中出现的地图部分。</span><span class="sxs-lookup"><span data-stu-id="74065-129">Specify the lower and upper boundaries for coordinates to control which part of the map appears in the report.</span></span>  
  
 <span data-ttu-id="74065-130">**最小 X**</span><span class="sxs-lookup"><span data-stu-id="74065-130">**Minimum X**</span></span>  
 <span data-ttu-id="74065-131">最小 X 值。</span><span class="sxs-lookup"><span data-stu-id="74065-131">Lowest X value.</span></span> <span data-ttu-id="74065-132">仅适用于 **“平面数据”** 。</span><span class="sxs-lookup"><span data-stu-id="74065-132">Available for **Planar** only.</span></span>  
  
 <span data-ttu-id="74065-133">**最大 X**</span><span class="sxs-lookup"><span data-stu-id="74065-133">**Maximum X**</span></span>  
 <span data-ttu-id="74065-134">最大 X 值。</span><span class="sxs-lookup"><span data-stu-id="74065-134">Highest X value.</span></span> <span data-ttu-id="74065-135">仅适用于 **“平面数据”** 。</span><span class="sxs-lookup"><span data-stu-id="74065-135">Available for **Planar** only.</span></span>  
  
 <span data-ttu-id="74065-136">**最小 Y**</span><span class="sxs-lookup"><span data-stu-id="74065-136">**Minimum Y**</span></span>  
 <span data-ttu-id="74065-137">最小 Y 值。</span><span class="sxs-lookup"><span data-stu-id="74065-137">Lowest Y value.</span></span> <span data-ttu-id="74065-138">仅适用于 **“平面数据”** 。</span><span class="sxs-lookup"><span data-stu-id="74065-138">Available for **Planar** only.</span></span>  
  
 <span data-ttu-id="74065-139">**最大 Y**</span><span class="sxs-lookup"><span data-stu-id="74065-139">**Maximum Y**</span></span>  
 <span data-ttu-id="74065-140">最大 Y 值。</span><span class="sxs-lookup"><span data-stu-id="74065-140">Highest Y value.</span></span> <span data-ttu-id="74065-141">仅适用于 **“平面数据”** 。</span><span class="sxs-lookup"><span data-stu-id="74065-141">Available for **Planar** only.</span></span>  
  
 <span data-ttu-id="74065-142">**最低经度**</span><span class="sxs-lookup"><span data-stu-id="74065-142">**Minimum Longitude**</span></span>  
 <span data-ttu-id="74065-143">最低经度值。</span><span class="sxs-lookup"><span data-stu-id="74065-143">Lowest longitude value.</span></span> <span data-ttu-id="74065-144">仅适用于 **“地理”** 。</span><span class="sxs-lookup"><span data-stu-id="74065-144">Available for **Geographic** only.</span></span>  
  
 <span data-ttu-id="74065-145">**最高经度**</span><span class="sxs-lookup"><span data-stu-id="74065-145">**Maximum Longitude**</span></span>  
 <span data-ttu-id="74065-146">最高经度值。</span><span class="sxs-lookup"><span data-stu-id="74065-146">Highest longitude value.</span></span> <span data-ttu-id="74065-147">仅适用于 **“地理”** 。</span><span class="sxs-lookup"><span data-stu-id="74065-147">Available for **Geographic** only.</span></span>  
  
 <span data-ttu-id="74065-148">**最低纬度**</span><span class="sxs-lookup"><span data-stu-id="74065-148">**Minimum Latitude**</span></span>  
 <span data-ttu-id="74065-149">最低纬度值。</span><span class="sxs-lookup"><span data-stu-id="74065-149">Lowest latitude value.</span></span> <span data-ttu-id="74065-150">仅适用于 **“地理”** 。</span><span class="sxs-lookup"><span data-stu-id="74065-150">Available for **Geographic** only.</span></span>  
  
 <span data-ttu-id="74065-151">**最高纬度**</span><span class="sxs-lookup"><span data-stu-id="74065-151">**Maximum Latitude**</span></span>  
 <span data-ttu-id="74065-152">最高纬度值。</span><span class="sxs-lookup"><span data-stu-id="74065-152">Highest latitude value.</span></span> <span data-ttu-id="74065-153">仅适用于 **“地理”** 。</span><span class="sxs-lookup"><span data-stu-id="74065-153">Available for **Geographic** only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74065-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="74065-154">See Also</span></span>  
 [<span data-ttu-id="74065-155">地图（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="74065-155">Maps &#40;Report Builder and SSRS&#41;</span></span>](report-design/maps-report-builder-and-ssrs.md)  
  
  
