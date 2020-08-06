---
title: "\"地图颜色规则\" 对话框-\"常规\" |Microsoft Docs"
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10541"
- sql12.rtp.rptdesigner.shared.mapcolorrulesgeneral.f1
ms.assetid: 14ff5fc1-4cf8-4a45-9d98-47a1bf1c52c4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0dffc6c0b31400cb4eb9cecbbada1a52f8f41443
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590566"
---
# <a name="map-color-rules-dialog-box-general"></a><span data-ttu-id="57ae1-102">“地图颜色规则”对话框 -&gt;“常规”</span><span class="sxs-lookup"><span data-stu-id="57ae1-102">Map Color Rules Dialog Box, General</span></span>
  <span data-ttu-id="57ae1-103">选择 **“颜色规则属性”** 对话框中的 **“常规”** 可以定义此层上地图元素的颜色选项。</span><span class="sxs-lookup"><span data-stu-id="57ae1-103">Select **General** on the **Color Rules Properties** dialog box to define color options for map elements on this layer.</span></span> <span data-ttu-id="57ae1-104">地图元素包括多边形、线条和点。</span><span class="sxs-lookup"><span data-stu-id="57ae1-104">Map elements include polygons, lines, and points.</span></span> <span data-ttu-id="57ae1-105">当您创建了基于空间数据的地图元素和来自数据集字段（或来自空间数据源字段）的分析数据之间的关系后，就可以应用颜色规则。</span><span class="sxs-lookup"><span data-stu-id="57ae1-105">Color rules can be applied when you have created a relationship between map elements based on spatial data and analytical data from a dataset field or from a spatial data source field.</span></span>  
  
 <span data-ttu-id="57ae1-106">若要通过指定具有不同主要颜色和辅助颜色的装饰性渐变来显示层上的所有地图元素，请使用“地图多边形属性”对话框的 **“填充”** 页。</span><span class="sxs-lookup"><span data-stu-id="57ae1-106">To display all map elements on a layer by specifying a decorative gradient with different primary and secondary colors, use the **Fill** page of the Map Polygon Properties Dialog Box.</span></span> <span data-ttu-id="57ae1-107">对于层来说，颜色规则优先于显示属性。</span><span class="sxs-lookup"><span data-stu-id="57ae1-107">Color rules take precedence over display properties for a layer.</span></span> <span data-ttu-id="57ae1-108">有关详细信息，请参阅[自定义地图或地图层的数据和显示（报表生成器和 SSRS）](report-design/customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="57ae1-108">For more information, see [Customize the Data and Display of a Map or Map Layer &#40;Report Builder and SSRS&#41;](report-design/customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="57ae1-109">选项</span><span class="sxs-lookup"><span data-stu-id="57ae1-109">Options</span></span>  
 <span data-ttu-id="57ae1-110">**应用模板样式**</span><span class="sxs-lookup"><span data-stu-id="57ae1-110">**Apply template style**</span></span>  
 <span data-ttu-id="57ae1-111">选择此选项可以基于主题使用颜色，该主题在向导中选择或在“多边形”、“线条”或“点”层属性中设置。</span><span class="sxs-lookup"><span data-stu-id="57ae1-111">Select this option to use color based on the theme that was chosen in the wizard or set in the Polygon, Line, or Point layer properties.</span></span> <span data-ttu-id="57ae1-112">主题为地图的颜色、字体和边框设置默认选项。</span><span class="sxs-lookup"><span data-stu-id="57ae1-112">A theme sets default options for color, font, and borders for the map.</span></span> <span data-ttu-id="57ae1-113">对于此选项，不应用任何规则来将颜色分配给每个地图元素。</span><span class="sxs-lookup"><span data-stu-id="57ae1-113">For this option, no rule is applied to assign colors to each map element.</span></span>  
  
 <span data-ttu-id="57ae1-114">**使用调色板实现数据的可视化效果**</span><span class="sxs-lookup"><span data-stu-id="57ae1-114">**Visualize data by using color palette**</span></span>  
 <span data-ttu-id="57ae1-115">选择此选项可以使用特定调色板中的颜色来将分析数据可视化。</span><span class="sxs-lookup"><span data-stu-id="57ae1-115">Select this option to visualize analytical data by using colors from a specific color palette.</span></span>  
  
 <span data-ttu-id="57ae1-116">**使用颜色范围实现数据的可视化效果**</span><span class="sxs-lookup"><span data-stu-id="57ae1-116">**Visualize data by using color ranges**</span></span>  
 <span data-ttu-id="57ae1-117">选择此选项可以使用每个地图元素的颜色范围来将分析数据可视化。</span><span class="sxs-lookup"><span data-stu-id="57ae1-117">Select this option to visualize analytical data by using a range of colors for each map element.</span></span> <span data-ttu-id="57ae1-118">例如，当您指定“红”作为开始颜色、“黄”作为中间颜色以及“绿”作为结束颜色时，在低范围中的值将为“红”，在中间范围中的值将为“黄”，在高范围中的值将为“绿”。</span><span class="sxs-lookup"><span data-stu-id="57ae1-118">For example, when you specify Red as a start color, Yellow as a middle color, and Green as an end color, values in the low range are Red, values in the middle range are Yellow, and values in the top range are Green.</span></span>  
  
 <span data-ttu-id="57ae1-119">**使用自定义颜色实现数据的可视化效果**</span><span class="sxs-lookup"><span data-stu-id="57ae1-119">**Visualize data by using custom colors**</span></span>  
 <span data-ttu-id="57ae1-120">选择此选项可以通过指定您自己的颜色列表来将分析数据可视化。</span><span class="sxs-lookup"><span data-stu-id="57ae1-120">Select this option to visualize analytical data by specifying your own list of colors.</span></span>  
  
 <span data-ttu-id="57ae1-121">**数据字段**</span><span class="sxs-lookup"><span data-stu-id="57ae1-121">**Data field**</span></span>  
 <span data-ttu-id="57ae1-122">选择 **“实现数据的可视化效果”** 选项之一时，将显示此选项。</span><span class="sxs-lookup"><span data-stu-id="57ae1-122">This option appears when you select one of the **Visualize data** options.</span></span>  
  
 <span data-ttu-id="57ae1-123">从下拉列表中选择要使用的分析数据字段。</span><span class="sxs-lookup"><span data-stu-id="57ae1-123">Select the analytical data field to use from the drop-down list.</span></span> <span data-ttu-id="57ae1-124">根据空间数据的来源不同，该列表显示来自空间数据源的字段或具有空间数据和分析数据之间的某一对应关系的报表数据集的字段。</span><span class="sxs-lookup"><span data-stu-id="57ae1-124">Depending on the source of spatial data, the list displays fields from the spatial data source and from a report dataset that has a relationship between the spatial data and analytical data.</span></span> <span data-ttu-id="57ae1-125">若要创建这样的关系，请在所选地图层的“分析数据”页上设置数据选项。</span><span class="sxs-lookup"><span data-stu-id="57ae1-125">To create such a relationship, set the data options on the Analytical Data page for the selected map layer.</span></span>  
  
 <span data-ttu-id="57ae1-126">**调板**</span><span class="sxs-lookup"><span data-stu-id="57ae1-126">**Palette**</span></span>  
 <span data-ttu-id="57ae1-127">键入或选择调色板的名称。</span><span class="sxs-lookup"><span data-stu-id="57ae1-127">Type or select the name of the color palette.</span></span>  
  
 <span data-ttu-id="57ae1-128">**开始颜色**</span><span class="sxs-lookup"><span data-stu-id="57ae1-128">**Start color**</span></span>  
 <span data-ttu-id="57ae1-129">指定处于数据范围低端的数据要使用的颜色。</span><span class="sxs-lookup"><span data-stu-id="57ae1-129">Specify the color to use for data at the low end of the data range.</span></span>  
  
 <span data-ttu-id="57ae1-130">**中间颜色**</span><span class="sxs-lookup"><span data-stu-id="57ae1-130">**Middle color**</span></span>  
 <span data-ttu-id="57ae1-131">指定处于数据范围中部的数据要使用的颜色。</span><span class="sxs-lookup"><span data-stu-id="57ae1-131">Specify the color to use for data in the middle of the data range.</span></span> <span data-ttu-id="57ae1-132">选择 **“无颜色”** 可以删除此范围。</span><span class="sxs-lookup"><span data-stu-id="57ae1-132">Select **No Color** to remove this range.</span></span>  
  
 <span data-ttu-id="57ae1-133">**结束颜色**</span><span class="sxs-lookup"><span data-stu-id="57ae1-133">**End color**</span></span>  
 <span data-ttu-id="57ae1-134">指定处于数据范围高端的数据要使用的颜色。</span><span class="sxs-lookup"><span data-stu-id="57ae1-134">Specify the color to use for data at the high end of the data range.</span></span>  
  
 <span data-ttu-id="57ae1-135">**添加**</span><span class="sxs-lookup"><span data-stu-id="57ae1-135">**Add**</span></span>  
 <span data-ttu-id="57ae1-136">单击 **“添加”** 可以为颜色规则指定您自己的颜色。</span><span class="sxs-lookup"><span data-stu-id="57ae1-136">Click **Add** to specify your own colors for the color rule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57ae1-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="57ae1-137">See Also</span></span>  
 <span data-ttu-id="57ae1-138">[地图（报表生成器和 SSRS）](report-design/maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="57ae1-138">[Maps &#40;Report Builder and SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="57ae1-139">更改地图图例、色阶和关联的规则（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="57ae1-139">Change Map Legends, Color Scale, and Associated Rules &#40;Report Builder and SSRS&#41;</span></span>](report-design/change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs.md)  
  
  
