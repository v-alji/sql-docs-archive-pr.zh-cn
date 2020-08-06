---
title: 查看多维数据集架构 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 82fc715c-e08e-447d-8fc8-9c9005f145f0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2e7d324db1e0c41588694031d3c121fdb47233f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693118"
---
# <a name="view-the-cube-schema"></a><span data-ttu-id="f9e0b-102">查看多维数据集架构</span><span class="sxs-lookup"><span data-stu-id="f9e0b-102">View the Cube Schema</span></span>
  <span data-ttu-id="f9e0b-103">在 **“多维数据集设计器”** 的 **“多维数据集结构”** 选项卡的 **“数据源视图”** 窗格中显示多维数据集架构。</span><span class="sxs-lookup"><span data-stu-id="f9e0b-103">The **Data Source View** pane of the **Cube Structure** tab in **Cube Designer** displays the cube schema.</span></span> <span data-ttu-id="f9e0b-104">架构是从中派生多维数据集的度量值和维度的表的集合。</span><span class="sxs-lookup"><span data-stu-id="f9e0b-104">The schema is the set of tables from which the measures and dimensions for a cube are derived.</span></span> <span data-ttu-id="f9e0b-105">每个多维数据集架构包含多维数据集中的度量值和维度基于的一个或多个事实表以及一个或多个维度表。</span><span class="sxs-lookup"><span data-stu-id="f9e0b-105">Every cube schema consists of one or more fact tables and one or more dimension tables on which the measures and dimensions in the cube are based.</span></span>  
  
 <span data-ttu-id="f9e0b-106">**“多维数据集结构”** 选项卡的 **“数据源视图”** 窗格显示多维数据集所基于的数据源视图的关系图。</span><span class="sxs-lookup"><span data-stu-id="f9e0b-106">The **Data Source View** pane of the **Cube Structure** tab displays a diagram of the data source view on which the cube is based.</span></span> <span data-ttu-id="f9e0b-107">此关系图是数据源视图主关系图的一个子集。</span><span class="sxs-lookup"><span data-stu-id="f9e0b-107">This diagram is a subset of the main diagram of the data source view.</span></span> <span data-ttu-id="f9e0b-108">您可以在 **“数据源视图”** 窗格中隐藏和显示表并查看任何现有的关系图。</span><span class="sxs-lookup"><span data-stu-id="f9e0b-108">You can hide and show tables in the **Data Source View** pane and view any existing diagrams.</span></span> <span data-ttu-id="f9e0b-109">但是，您不能更改（例如添加新关系或命名查询）基础架构。</span><span class="sxs-lookup"><span data-stu-id="f9e0b-109">However, you cannot make changes (such as adding new relationships or named queries) to the underlying schema.</span></span> <span data-ttu-id="f9e0b-110">若要更改该架构，请使用数据源视图设计器。</span><span class="sxs-lookup"><span data-stu-id="f9e0b-110">To make changes to the schema, use Data Source View Designer.</span></span>  
  
 <span data-ttu-id="f9e0b-111">创建多维数据集时， **“多维数据集结构”** 选项卡的 **“数据源视图”** 窗格中显示的关系图最初与项目或数据库的数据源视图中的 **“显示所有表”** 关系图相同。</span><span class="sxs-lookup"><span data-stu-id="f9e0b-111">When you create a cube, the diagram displayed in the **Data Source View** pane of the **Cube Structure** tab is initially the same as the **Show All Tables** diagram in the data source view for the project or database.</span></span> <span data-ttu-id="f9e0b-112">您可以在 **“数据源视图”** 窗格中使用数据源视图中任何现有的关系图替换此关系图并进行调整。</span><span class="sxs-lookup"><span data-stu-id="f9e0b-112">You can replace this diagram with any existing diagram in the data source view and make adjustments in the **Data Source View** pane.</span></span>  
  
 <span data-ttu-id="f9e0b-113">在 **“多维数据集设计器”** 中使用关系图时，作用于选项卡或选项卡中任何所选对象的命令都会在 **“数据源视图”** 菜单中提供。</span><span class="sxs-lookup"><span data-stu-id="f9e0b-113">While you work with the diagram in **Cube Designer**, commands that act on the tab or on any selected object in the tab are available on the **Data Source View** menu.</span></span> <span data-ttu-id="f9e0b-114">您还可以右键单击关系图的背景或关系图中的任何对象来使用作用于关系图或所选对象的命令。</span><span class="sxs-lookup"><span data-stu-id="f9e0b-114">You can also right-click the background of the diagram or any object in the diagram to use commands that act on the diagram or selected object.</span></span> <span data-ttu-id="f9e0b-115">可以：</span><span class="sxs-lookup"><span data-stu-id="f9e0b-115">You can:</span></span>  
  
-   <span data-ttu-id="f9e0b-116">在关系图和树视图之间进行切换。</span><span class="sxs-lookup"><span data-stu-id="f9e0b-116">Switch between diagram and tree formats.</span></span>  
  
-   <span data-ttu-id="f9e0b-117">排列、查找、显示和隐藏表。</span><span class="sxs-lookup"><span data-stu-id="f9e0b-117">Arrange, find, show, and hide tables.</span></span>  
  
-   <span data-ttu-id="f9e0b-118">显示友好名称。</span><span class="sxs-lookup"><span data-stu-id="f9e0b-118">Show friendly names.</span></span>  
  
-   <span data-ttu-id="f9e0b-119">切换布局。</span><span class="sxs-lookup"><span data-stu-id="f9e0b-119">Switch layouts.</span></span>  
  
-   <span data-ttu-id="f9e0b-120">更改放大倍数。</span><span class="sxs-lookup"><span data-stu-id="f9e0b-120">Change the magnification.</span></span>  
  
-   <span data-ttu-id="f9e0b-121">查看属性。</span><span class="sxs-lookup"><span data-stu-id="f9e0b-121">View properties.</span></span>  
  
 <span data-ttu-id="f9e0b-122">此外，您可以执行下表中所列的操作：</span><span class="sxs-lookup"><span data-stu-id="f9e0b-122">Additionally, you can perform the actions listed in the following table:</span></span>  
  
|<span data-ttu-id="f9e0b-123">功能</span><span class="sxs-lookup"><span data-stu-id="f9e0b-123">To</span></span>|<span data-ttu-id="f9e0b-124">操作</span><span class="sxs-lookup"><span data-stu-id="f9e0b-124">Do this</span></span>|  
|--------|-------------|  
|<span data-ttu-id="f9e0b-125">从多维数据集的数据源视图使用关系图</span><span class="sxs-lookup"><span data-stu-id="f9e0b-125">Use a diagram from the data source view of the cube</span></span>|<span data-ttu-id="f9e0b-126">在 **“数据源视图”** 菜单上，指向 **“关系图复制源”**，然后单击要使用的数据源视图关系图。</span><span class="sxs-lookup"><span data-stu-id="f9e0b-126">On the **Data Source View** menu, point to **Copy Diagram from**, and then click the data source view diagram you want to use.</span></span><br /><br /> <span data-ttu-id="f9e0b-127">- 或 -</span><span class="sxs-lookup"><span data-stu-id="f9e0b-127">- or -</span></span><br /><br /> <span data-ttu-id="f9e0b-128">右键单击“数据源视图”窗格的背景，指向“关系图复制源”\*\*\*\*\*\*\*\*，然后单击要使用的数据源视图中的关系图。</span><span class="sxs-lookup"><span data-stu-id="f9e0b-128">Right-click the background of the **Data Source View** pane, point to **Copy Diagram from**, and then click the diagram in the data source view that you want.</span></span> <span data-ttu-id="f9e0b-129">此方法创建关系图的一个独立副本，因此您在 **“多维数据集生成器”** 选项卡上的任何更改不会显示在原始关系图中。</span><span class="sxs-lookup"><span data-stu-id="f9e0b-129">This method creates an independent copy of the diagram, so any changes you make on the **Cube Builder** tab do not appear in the original diagram.</span></span>|  
|<span data-ttu-id="f9e0b-130">只显示多维数据集中使用的表</span><span class="sxs-lookup"><span data-stu-id="f9e0b-130">Show only the tables that are used in the cube</span></span>|<span data-ttu-id="f9e0b-131">在 **“数据源视图”** 菜单上，单击 **“仅显示已用表”**。</span><span class="sxs-lookup"><span data-stu-id="f9e0b-131">On the **Data Source View** menu, click **Show Only Used Tables**.</span></span><br /><br /> <span data-ttu-id="f9e0b-132">- 或 -</span><span class="sxs-lookup"><span data-stu-id="f9e0b-132">- or -</span></span><br /><br /> <span data-ttu-id="f9e0b-133">右键单击“数据源视图”窗格的背景，然后单击“仅显示已用表”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f9e0b-133">Right-click the background of the **Data Source View** pane, and then click **Show Only Used Tables**.</span></span>|  
|<span data-ttu-id="f9e0b-134">编辑数据源视图架构</span><span class="sxs-lookup"><span data-stu-id="f9e0b-134">Edit the data source view schema</span></span>|<span data-ttu-id="f9e0b-135">在 **“数据源视图”** 菜单上，单击 **“编辑数据源视图”**。</span><span class="sxs-lookup"><span data-stu-id="f9e0b-135">On the **Data Source View** menu, click **Edit Data Source View**.</span></span><br /><br /> <span data-ttu-id="f9e0b-136">- 或 -</span><span class="sxs-lookup"><span data-stu-id="f9e0b-136">- or -</span></span><br /><br /> <span data-ttu-id="f9e0b-137">右键单击“数据源视图”窗格的背景，然后单击“编辑数据源视图”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f9e0b-137">Right-click the background of the **Data Source View** pane, and then click **Edit Data Source View**.</span></span>|  
  
  
