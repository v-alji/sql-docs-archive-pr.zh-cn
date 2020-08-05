---
title: 在 Visio 中查看数据挖掘模型 (数据挖掘外接程序) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- diagram, modifying
- templates [Visio]
- shapes, data mining
- diagram
ms.assetid: 5841adea-6650-4fae-8526-26af33edbede
author: minewiskan
ms.author: owend
ms.openlocfilehash: f3c1e63c058295b93e2562c64a6df90a30273a10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580389"
---
# <a name="viewing-data-mining-models-in-visio-data-mining-add-ins"></a><span data-ttu-id="1f5e3-102">在 Visio 中查看数据挖掘模型（数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="1f5e3-102">Viewing Data Mining Models in Visio (Data Mining Add-ins)</span></span>
  <span data-ttu-id="1f5e3-103">通过 Visio 数据挖掘形状，您可以连接服务器并创建一个表示现有数据挖掘模型的关系图。</span><span class="sxs-lookup"><span data-stu-id="1f5e3-103">The Visio shapes for data mining let you connect to a server and create a diagram representing an existing data mining model.</span></span> <span data-ttu-id="1f5e3-104">然后，可以使用 Visio 控件对关系图进行自定义，也可以深化到数据来公开一些基础统计信息并利用基础模型。</span><span class="sxs-lookup"><span data-stu-id="1f5e3-104">The diagrams can then be customized using Visio controls, but you can also drill down into data, expose some of the underlying statistics, and work with the underlying model.</span></span>  
  
## <a name="building-a-model-diagram"></a><span data-ttu-id="1f5e3-105">生成模型关系图</span><span class="sxs-lookup"><span data-stu-id="1f5e3-105">Building a Model Diagram</span></span>  
 <span data-ttu-id="1f5e3-106">打开包含用于数据挖掘的 Visio 形状的文件时，"**形状**" 窗格将显示以下形状。</span><span class="sxs-lookup"><span data-stu-id="1f5e3-106">When you open the file containing the Visio shapes for data mining, the **Shapes** pane shows the following shapes.</span></span>  
  
 <span data-ttu-id="1f5e3-107">如果在打开 Visio 时没有显示数据挖掘形状，则请从安装文件夹打开模板文件。</span><span class="sxs-lookup"><span data-stu-id="1f5e3-107">If you do not see the data mining shapes when you open Visio, open the template file from the installation folder.</span></span>  
  
 <span data-ttu-id="1f5e3-108">![DM](media/dm-stencil.gif "DM")</span><span class="sxs-lookup"><span data-stu-id="1f5e3-108">![DM](media/dm-stencil.gif "DM")</span></span>  
  
 <span data-ttu-id="1f5e3-109">若要使用形状，则请将其拖至该页。</span><span class="sxs-lookup"><span data-stu-id="1f5e3-109">To use a shape, drag it to the page.</span></span> <span data-ttu-id="1f5e3-110">每个形状都会打开一个不同的向导，可帮助您选择源数据，设置特定关系图类型的选项，以及指定明暗度和其他显示选项。</span><span class="sxs-lookup"><span data-stu-id="1f5e3-110">Each of the shapes opens a different wizard, which helps you select source data, set options for the specific diagram type, and specify shading and other display options.</span></span>  
  
 <span data-ttu-id="1f5e3-111">下表列出了可用于各关系图类型的模型类型。</span><span class="sxs-lookup"><span data-stu-id="1f5e3-111">The following table lists the types of models that you can use with each type of diagram.</span></span>  
  
|<span data-ttu-id="1f5e3-112">Visio 形状</span><span class="sxs-lookup"><span data-stu-id="1f5e3-112">Visio shape</span></span>|<span data-ttu-id="1f5e3-113">支持的模型</span><span class="sxs-lookup"><span data-stu-id="1f5e3-113">Supported models</span></span>|  
|-----------------|----------------------|  
|<span data-ttu-id="1f5e3-114">决策树</span><span class="sxs-lookup"><span data-stu-id="1f5e3-114">Decision Tree</span></span>|<span data-ttu-id="1f5e3-115">此形状用于基于决策树算法或线性回归算法的模型。</span><span class="sxs-lookup"><span data-stu-id="1f5e3-115">Use this shape for models based on the decision tree or linear regression algorithms.</span></span>|  
|<span data-ttu-id="1f5e3-116">依赖关系网络</span><span class="sxs-lookup"><span data-stu-id="1f5e3-116">Dependency Network</span></span>|<span data-ttu-id="1f5e3-117">此形状用于基于以下任何算法的模型：Naive Bayes、决策树或关联规则。</span><span class="sxs-lookup"><span data-stu-id="1f5e3-117">Use this shape for models based on any of the following algorithms: Naive Bayes, Decision Trees, or Association Rules.</span></span>|  
|<span data-ttu-id="1f5e3-118">群集</span><span class="sxs-lookup"><span data-stu-id="1f5e3-118">Cluster</span></span>|<span data-ttu-id="1f5e3-119">此形状用于基于聚类分析算法的模型。</span><span class="sxs-lookup"><span data-stu-id="1f5e3-119">Use this shape for models based on clustering algorithms.</span></span>|  
  
 <span data-ttu-id="1f5e3-120">根据挖掘模型中的数据类型的不同，向导可能会具有不同的选项。</span><span class="sxs-lookup"><span data-stu-id="1f5e3-120">Depending on the type of data in your mining model, the wizard may offer different options.</span></span> <span data-ttu-id="1f5e3-121">例如，包含连续数字的列和包含分类变量的列显示不同。</span><span class="sxs-lookup"><span data-stu-id="1f5e3-121">For example, columns that contain continuous numbers are visualized differently than categorical variables.</span></span>  
  
## <a name="working-with-completed-shapes"></a><span data-ttu-id="1f5e3-122">使用已完成的形状</span><span class="sxs-lookup"><span data-stu-id="1f5e3-122">Working with Completed Shapes</span></span>  
 <span data-ttu-id="1f5e3-123">完成关系图后，可以用它浏览数据挖掘模型或增强关系图以便在演示中使用。</span><span class="sxs-lookup"><span data-stu-id="1f5e3-123">After the diagram is complete, you can use it to browse the data mining model or enhance the diagram for use in presentations.</span></span>  
  
### <a name="visio-menus"></a><span data-ttu-id="1f5e3-124">Visio 菜单</span><span class="sxs-lookup"><span data-stu-id="1f5e3-124">Visio Menus</span></span>  
 <span data-ttu-id="1f5e3-125">Visio 提供了多种呈现控件、主题和快捷菜单以帮助您增强关系图。</span><span class="sxs-lookup"><span data-stu-id="1f5e3-125">Visio provides a variety of rendering controls, themes, and shortcut menus to help enhance a diagram.</span></span>  
  
-   <span data-ttu-id="1f5e3-126">使用 Visio 主题更改关系图颜色。</span><span class="sxs-lookup"><span data-stu-id="1f5e3-126">Use Visio themes to alter diagram colors.</span></span>  
  
-   <span data-ttu-id="1f5e3-127">更改连接器或图表布局。</span><span class="sxs-lookup"><span data-stu-id="1f5e3-127">Change connectors or diagram layout.</span></span>  
  
### <a name="data-mining-menus"></a><span data-ttu-id="1f5e3-128">数据挖掘菜单</span><span class="sxs-lookup"><span data-stu-id="1f5e3-128">Data Mining Menus</span></span>  
 <span data-ttu-id="1f5e3-129">这些工具栏和菜单由每种形状和模型类型特定的外接程序提供。</span><span class="sxs-lookup"><span data-stu-id="1f5e3-129">These toolbars and menu items are provided by the add-ins that are specific to each shape or model type</span></span>  
  
-   <span data-ttu-id="1f5e3-130">每个关系图类型都具有针对形状的快捷菜单，可用于访问特殊选项。</span><span class="sxs-lookup"><span data-stu-id="1f5e3-130">Each diagram type has a shortcut menu for the shape that lets you access special options.</span></span> <span data-ttu-id="1f5e3-131">尽管此菜单中的许多选项都是所有 Visio 形状共有的，但某些选项对于数据挖掘模板是唯一的</span><span class="sxs-lookup"><span data-stu-id="1f5e3-131">Although many options in this menu are common to all Visio shapes, some options are unique to the data mining templates</span></span>  
  
     <span data-ttu-id="1f5e3-132">例如，在决策树关系图中，您可单击单个节点然后折叠子节点以使关系图更简单，或者将子节点移到单独的页。</span><span class="sxs-lookup"><span data-stu-id="1f5e3-132">For example, in a decision tree diagram, you can click an individual node and then collapse the child nodes to make the diagram simpler, or move child nodes to a separate page.</span></span>  
  
-   <span data-ttu-id="1f5e3-133">由于形状绑定到模型数据，所以您也可以使用关系图进行一些浏览：</span><span class="sxs-lookup"><span data-stu-id="1f5e3-133">Because the shape is bound to the model data, you can also do some amount of exploration using the diagram:</span></span>  
  
     <span data-ttu-id="1f5e3-134">筛选显示的节点，或更改树的级别或图形深度。</span><span class="sxs-lookup"><span data-stu-id="1f5e3-134">Filter the nodes that are displayed, or change the level of the tree or depth of the graph.</span></span>  
  
     <span data-ttu-id="1f5e3-135">放大特定部分、搜索包含某个属性的节点或者按其边缘（概率）筛选依赖关系图。</span><span class="sxs-lookup"><span data-stu-id="1f5e3-135">Zoom in on specific sections, search for nodes that contain a certain attribute, or filter a dependency graph by its edges (probability).</span></span>  
  
## <a name="walkthroughs"></a><span data-ttu-id="1f5e3-136">演练</span><span class="sxs-lookup"><span data-stu-id="1f5e3-136">Walkthroughs</span></span>  
 <span data-ttu-id="1f5e3-137">有关如何使用和解释某一已完成关系图的示例，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="1f5e3-137">For examples of how to work with and interpret a completed diagram, see these topics:</span></span>  
  
 [<span data-ttu-id="1f5e3-138">分类关系图演练</span><span class="sxs-lookup"><span data-stu-id="1f5e3-138">Cluster Diagram Walkthrough</span></span>](cluster-diagram-walkthrough-data-mining-add-ins.md)  
  
 [<span data-ttu-id="1f5e3-139">依赖关系网络关系图演练</span><span class="sxs-lookup"><span data-stu-id="1f5e3-139">Dependency Net Diagram Walkthrough</span></span>](dependency-network-diagram-walkthrough-data-mining-add-ins.md)  
  
 [<span data-ttu-id="1f5e3-140">决策树关系图演练</span><span class="sxs-lookup"><span data-stu-id="1f5e3-140">Decision Tree Diagram Walkthrough</span></span>](decision-tree-diagram-walkthrough-data-mining-add-ins.md)  
  
## <a name="see-also"></a><span data-ttu-id="1f5e3-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1f5e3-141">See Also</span></span>  
 [<span data-ttu-id="1f5e3-142">在 Excel 中浏览模型 &#40;SQL Server 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="1f5e3-142">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
