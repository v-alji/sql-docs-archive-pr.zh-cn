---
title: "\"地图并行属性\" 对话框-\"标签\" |Microsoft Docs"
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapparallelproperties.labels.f1
- "10519"
ms.assetid: 4560a7e4-e19b-4a6e-8ef4-e963497e01ae
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c08baa31ad8ee65f1f096ecf4304803a79e0fbfe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577377"
---
# <a name="map-parallel-properties-dialog-box-labels"></a><span data-ttu-id="0b653-102">“地图纬线属性”对话框 -&gt;“标签”</span><span class="sxs-lookup"><span data-stu-id="0b653-102">Map Parallel Properties Dialog Box, Labels</span></span>
  <span data-ttu-id="0b653-103">使用 " **MapParallel 属性**" 对话框可以更改地图视区中水平网格的标签选项。</span><span class="sxs-lookup"><span data-stu-id="0b653-103">Use the **MapParallel Properties** dialog box to change label options for the horizontal grid in the map viewport.</span></span> <span data-ttu-id="0b653-104">根据视区的指定坐标系统，纬线表示以下值之一：</span><span class="sxs-lookup"><span data-stu-id="0b653-104">A parallel represents the following value depending on the specified coordinate system for the viewport:</span></span>  
  
-   <span data-ttu-id="0b653-105">**平面.**</span><span class="sxs-lookup"><span data-stu-id="0b653-105">**Planar.**</span></span> <span data-ttu-id="0b653-106">X 坐标。</span><span class="sxs-lookup"><span data-stu-id="0b653-106">The X coordinate.</span></span>  
  
-   <span data-ttu-id="0b653-107">**地区性.**</span><span class="sxs-lookup"><span data-stu-id="0b653-107">**Geographic.**</span></span> <span data-ttu-id="0b653-108">当前投影的纬度。</span><span class="sxs-lookup"><span data-stu-id="0b653-108">The latitude for the current projection.</span></span>  
  
 <span data-ttu-id="0b653-109">单击 **“表达式”** (*fx*) 按钮以编辑设置该选项的值的表达式。</span><span class="sxs-lookup"><span data-stu-id="0b653-109">Click the **Expression** (*fx*) button to edit an expression that sets the value of the option.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0b653-110">选项</span><span class="sxs-lookup"><span data-stu-id="0b653-110">Options</span></span>  
 <span data-ttu-id="0b653-111">**时间间隔**</span><span class="sxs-lookup"><span data-stu-id="0b653-111">**Interval**</span></span>  
 <span data-ttu-id="0b653-112">键入以度为单位的整数值，指定纬线之间的间隔。</span><span class="sxs-lookup"><span data-stu-id="0b653-112">Type an integer value in degrees that specifies the interval between parallels.</span></span> <span data-ttu-id="0b653-113">默认情况下，选择 **“自动”** 。</span><span class="sxs-lookup"><span data-stu-id="0b653-113">By default, **Auto** is selected.</span></span> <span data-ttu-id="0b653-114">如果将此选项设置为 **“自动”**，则值将由地图数据集中的数据决定。</span><span class="sxs-lookup"><span data-stu-id="0b653-114">If this option is set to **Auto**, the value is determined by the data from the map dataset.</span></span>  
  
 <span data-ttu-id="0b653-115">**显示标签**</span><span class="sxs-lookup"><span data-stu-id="0b653-115">**Show labels**</span></span>  
 <span data-ttu-id="0b653-116">选择此选项可以显示纬线的标签。</span><span class="sxs-lookup"><span data-stu-id="0b653-116">Select this option to display labels for the parallels.</span></span>  
  
 <span data-ttu-id="0b653-117">**定位**</span><span class="sxs-lookup"><span data-stu-id="0b653-117">**Placement**</span></span>  
 <span data-ttu-id="0b653-118">选择标签相对于视区的显示位置（顶部、中心和底部）。</span><span class="sxs-lookup"><span data-stu-id="0b653-118">Select a location to display the labels relative to the top, center, and bottom of the viewport.</span></span> <span data-ttu-id="0b653-119">默认位置为 **“近端”**。</span><span class="sxs-lookup"><span data-stu-id="0b653-119">The default placement is **Near**.</span></span>  
  
-   <span data-ttu-id="0b653-120">**近端** 在顶部显示标签。</span><span class="sxs-lookup"><span data-stu-id="0b653-120">**Near** Display labels at the top.</span></span>  
  
-   <span data-ttu-id="0b653-121">**四分之一** 在顶部和中心之间的一半位置处显示标签。</span><span class="sxs-lookup"><span data-stu-id="0b653-121">**One Quarter** Display labels half way between the top and the center.</span></span>  
  
-   <span data-ttu-id="0b653-122">**居中** 在中心显示标签。</span><span class="sxs-lookup"><span data-stu-id="0b653-122">**Center** Display labels at the center.</span></span>  
  
-   <span data-ttu-id="0b653-123">**四分之三** 在中心和底部之间的一半位置处显示标签。</span><span class="sxs-lookup"><span data-stu-id="0b653-123">**Three Quarters** Display labels half way between the center and the bottom.</span></span>  
  
-   <span data-ttu-id="0b653-124">**远端** 在底部显示标签。</span><span class="sxs-lookup"><span data-stu-id="0b653-124">**Far** Display labels at the bottom.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b653-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0b653-125">See Also</span></span>  
 <span data-ttu-id="0b653-126">[地图（报表生成器和 SSRS）](report-design/maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0b653-126">[Maps &#40;Report Builder and SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="0b653-127">更改地图图例、色阶和关联的规则（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="0b653-127">Change Map Legends, Color Scale, and Associated Rules &#40;Report Builder and SSRS&#41;</span></span>](report-design/change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs.md)  
  
  
