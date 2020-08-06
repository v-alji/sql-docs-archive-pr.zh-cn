---
title: 多维数据集设计器的多维数据集结构 ()  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.cubebuilderview.f1
ms.assetid: 00f0b605-5352-4b42-84f5-bd6c3e42d3d1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 857dd87c1d638a29adfa11c7de5a4d9f2d006314
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589385"
---
# <a name="cube-structure-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="5527c-102">多维数据集结构（多维数据集设计器）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="5527c-102">Cube Structure (Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="5527c-103">可以使用 **中的** 多维数据集设计器 **的** “多维数据集结构” [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 选项卡，创建和修改度量值组和度量值，添加多维数据集维度，以及通过关联数据源视图显示多维数据集中包含的对象。</span><span class="sxs-lookup"><span data-stu-id="5527c-103">Use the **Cube Structure** tab in **Cube Designer** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create and modify measure groups and measures, add cube dimensions, and display the objects included in the cube from the associated data source view.</span></span>  
  
 <span data-ttu-id="5527c-104">**“多维数据集结构”** 选项卡包含以下窗格：</span><span class="sxs-lookup"><span data-stu-id="5527c-104">The **Cube Structure** tab contains the following panes:</span></span>  
  
## <a name="panes"></a><span data-ttu-id="5527c-105">窗格</span><span class="sxs-lookup"><span data-stu-id="5527c-105">Panes</span></span>  
  
|<span data-ttu-id="5527c-106">窗格</span><span class="sxs-lookup"><span data-stu-id="5527c-106">Pane</span></span>|<span data-ttu-id="5527c-107">定义</span><span class="sxs-lookup"><span data-stu-id="5527c-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="5527c-108">**工具栏**</span><span class="sxs-lookup"><span data-stu-id="5527c-108">**Toolbar**</span></span>|<span data-ttu-id="5527c-109">使用工具栏可以执行此选项卡中的常见操作。有关此窗格的详细信息，请参阅[Toolbar &#40;多维数据集结构 "选项卡、多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](toolbar-cube-structure-cube-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="5527c-109">Use the toolbar to perform common actions in this tab. For more information about this pane, see [Toolbar &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-cube-structure-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="5527c-110">**措施**</span><span class="sxs-lookup"><span data-stu-id="5527c-110">**Measures**</span></span>|<span data-ttu-id="5527c-111">使用 **“度量值”** 窗格，可以创建和修改所选多维数据集的度量值和度量值组。</span><span class="sxs-lookup"><span data-stu-id="5527c-111">Use the **Measures** pane to create and modify measure groups and measures for the selected cube.</span></span> <span data-ttu-id="5527c-112">有关此窗格的详细信息，请参阅[度量值（“多维数据集结构”选项卡，多维数据集设计器）（Analysis Services - 多维数据）](measures-cube-structure-cube-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="5527c-112">For more information about this pane, see [Measures &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](measures-cube-structure-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="5527c-113">**Dimensions**</span><span class="sxs-lookup"><span data-stu-id="5527c-113">**Dimensions**</span></span>|<span data-ttu-id="5527c-114">使用 **“维度”** 窗格，可以包括和修改所选多维数据集的多维数据集维度。</span><span class="sxs-lookup"><span data-stu-id="5527c-114">Use the **Dimensions** pane to include and modify cube dimensions for the selected cube.</span></span> <span data-ttu-id="5527c-115">有关此窗格的详细信息，请参阅[维度（“多维数据集结构”选项卡，多维数据集设计器）（Analysis Services - 多维数据）](dimensions-cube-structure-cube-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="5527c-115">For more information about this pane, see [Dimensions &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](dimensions-cube-structure-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="5527c-116">**“数据源视图”**</span><span class="sxs-lookup"><span data-stu-id="5527c-116">**Data Source View**</span></span>|<span data-ttu-id="5527c-117">使用 **“数据源视图”** 窗格，可以查看和编辑与所选多维数据集相关联的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="5527c-117">Use the **Data Source View** pane to view and edit the data source view associated with the selected cube.</span></span> <span data-ttu-id="5527c-118">有关此窗格的详细信息，请参阅[数据源视图（“多维数据集结构”选项卡，多维数据集设计器）（Analysis Services - 多维数据）](data-source-view-cube-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="5527c-118">For more information about this pane, see [Data Source View &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5527c-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5527c-119">See Also</span></span>  
 <span data-ttu-id="5527c-120">[逻辑体系结构 &#40;Analysis Services 多维数据&#41;](multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="5527c-120">[Logical Architecture &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md) </span></span>  
 <span data-ttu-id="5527c-121">[多维模型中的多维数据集](multidimensional-models/cubes-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="5527c-121">[Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="5527c-122">[配置度量值属性](multidimensional-models/configure-measure-properties.md) </span><span class="sxs-lookup"><span data-stu-id="5527c-122">[Configure Measure Properties](multidimensional-models/configure-measure-properties.md) </span></span>  
 <span data-ttu-id="5527c-123">[Analysis Services 多维数据 &#40;维度&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="5527c-123">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="5527c-124">[多维模型中的数据源视图](multidimensional-models/data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="5527c-124">[Data Source Views in Multidimensional Models](multidimensional-models/data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="5527c-125">多维数据集设计器 &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="5527c-125">Cube Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](cube-designer-analysis-services-multidimensional-data.md)  
  
  
