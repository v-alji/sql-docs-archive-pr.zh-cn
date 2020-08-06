---
title: 多维模型中的多维数据集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- OLAP objects [Analysis Services], cubes
- cubes [Analysis Services], about cubes
- cubes [Analysis Services]
- OLAP [Analysis Services], cubes
ms.assetid: e0f7acf3-4b07-41fc-a5fc-ac30b4a56c54
author: minewiskan
ms.author: owend
ms.openlocfilehash: 372bb8075b232ff8fbf8a54facf9bc065e6763a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693547"
---
# <a name="cubes-in-multidimensional-models"></a><span data-ttu-id="8c077-102">多维模型中的多维数据集</span><span class="sxs-lookup"><span data-stu-id="8c077-102">Cubes in Multidimensional Models</span></span>
  <span data-ttu-id="8c077-103">多维数据集是包含用于分析的信息的多维结构；多维数据集主要由维度和度量值构成。</span><span class="sxs-lookup"><span data-stu-id="8c077-103">A cube is a multidimensional structure that contains information for analytical purposes; the main constituents of a cube are dimensions and measures.</span></span> <span data-ttu-id="8c077-104">维度定义您用来对其执行切片操作的多维数据集的结构，而度量值提供最终用户感兴趣的聚合数值。</span><span class="sxs-lookup"><span data-stu-id="8c077-104">Dimensions define the structure of the cube that you use to slice and dice over, and measures provide aggregated numerical values of interest to the end user.</span></span> <span data-ttu-id="8c077-105">作为逻辑结构，多维数据集允许客户端应用程序检索度量值的值，就像它们包含在多维数据集的单元中一样；将为每个可能的摘要值都定义单元。</span><span class="sxs-lookup"><span data-stu-id="8c077-105">As a logical structure, a cube allows a client application to retrieve values, of measures, as if they were contained in cells in the cube; cells are defined for every possible summarized value.</span></span> <span data-ttu-id="8c077-106">多维数据集中的单元通过维度成员的交集定义，并且包含该特定交集处的度量值的聚合值。</span><span class="sxs-lookup"><span data-stu-id="8c077-106">A cell, in the cube, is defined by the intersection of dimension members and contains the aggregated values of the measures at that specific intersection.</span></span>  
  
## <a name="benefits-of-using-cubes"></a><span data-ttu-id="8c077-107">使用多维数据集的好处</span><span class="sxs-lookup"><span data-stu-id="8c077-107">Benefits of Using Cubes</span></span>  
 <span data-ttu-id="8c077-108">多维数据集提供存储所有相关数据以便进行分析的单一位置。</span><span class="sxs-lookup"><span data-stu-id="8c077-108">A cube provides a single place where all related data, for analysis, is stored.</span></span>  
  
## <a name="components-of-cubes"></a><span data-ttu-id="8c077-109">多维数据集的组件</span><span class="sxs-lookup"><span data-stu-id="8c077-109">Components of Cubes</span></span>  
 <span data-ttu-id="8c077-110">一个多维数据集由以下组件构成：</span><span class="sxs-lookup"><span data-stu-id="8c077-110">A cube is composed of:</span></span>  
  
|<span data-ttu-id="8c077-111">元素</span><span class="sxs-lookup"><span data-stu-id="8c077-111">Element</span></span>|<span data-ttu-id="8c077-112">说明</span><span class="sxs-lookup"><span data-stu-id="8c077-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8c077-113">维度</span><span class="sxs-lookup"><span data-stu-id="8c077-113">Dimensions</span></span>|[<span data-ttu-id="8c077-114">多维模型中的维度</span><span class="sxs-lookup"><span data-stu-id="8c077-114">Dimensions in Multidimensional Models</span></span>](dimensions-in-multidimensional-models.md)|  
|<span data-ttu-id="8c077-115">度量值和度量值组</span><span class="sxs-lookup"><span data-stu-id="8c077-115">Measures and Measure Groups</span></span>|[<span data-ttu-id="8c077-116">在多维模型中创建度量值和度量值组</span><span class="sxs-lookup"><span data-stu-id="8c077-116">Create Measures and Measure Groups in Multidimensional Models</span></span>](create-measures-and-measure-groups-in-multidimensional-models.md)|  
|<span data-ttu-id="8c077-117">分区</span><span class="sxs-lookup"><span data-stu-id="8c077-117">Partitions</span></span>|[<span data-ttu-id="8c077-118">多维模型中的分区</span><span class="sxs-lookup"><span data-stu-id="8c077-118">Partitions in Multidimensional Models</span></span>](partitions-in-multidimensional-models.md)|  
|<span data-ttu-id="8c077-119">透视</span><span class="sxs-lookup"><span data-stu-id="8c077-119">Perspectives</span></span>|[<span data-ttu-id="8c077-120">多维模型中的透视</span><span class="sxs-lookup"><span data-stu-id="8c077-120">Perspectives in Multidimensional Models</span></span>](perspectives-in-multidimensional-models.md)|  
|<span data-ttu-id="8c077-121">层次结构</span><span class="sxs-lookup"><span data-stu-id="8c077-121">Hierarchies</span></span>|[<span data-ttu-id="8c077-122">创建用户定义层次结构</span><span class="sxs-lookup"><span data-stu-id="8c077-122">Create User-Defined Hierarchies</span></span>](user-defined-hierarchies-create.md)|  
|<span data-ttu-id="8c077-123">操作</span><span class="sxs-lookup"><span data-stu-id="8c077-123">Actions</span></span>|[<span data-ttu-id="8c077-124">多维模型中的操作</span><span class="sxs-lookup"><span data-stu-id="8c077-124">Actions in Multidimensional Models</span></span>](actions-in-multidimensional-models.md)|  
|<span data-ttu-id="8c077-125">关键绩效指标 (KPI)</span><span class="sxs-lookup"><span data-stu-id="8c077-125">Key Performance Indicators (KPI)</span></span>|[<span data-ttu-id="8c077-126">多维模型中的关键绩效指标 (KPI)</span><span class="sxs-lookup"><span data-stu-id="8c077-126">Key Performance Indicators &#40;KPIs&#41; in Multidimensional Models</span></span>](key-performance-indicators-kpis-in-multidimensional-models.md)|  
|<span data-ttu-id="8c077-127">计算</span><span class="sxs-lookup"><span data-stu-id="8c077-127">Calculations</span></span>|[<span data-ttu-id="8c077-128">多维模型中的计算</span><span class="sxs-lookup"><span data-stu-id="8c077-128">Calculations in Multidimensional Models</span></span>](calculations-in-multidimensional-models.md)|  
|<span data-ttu-id="8c077-129">翻译</span><span class="sxs-lookup"><span data-stu-id="8c077-129">Translations</span></span>|[<span data-ttu-id="8c077-130">多维模型中的翻译</span><span class="sxs-lookup"><span data-stu-id="8c077-130">Translations in Multidimensional Models</span></span>](translations-in-multidimensional-models-analysis-services.md)|  
  
## <a name="related-tasks"></a><span data-ttu-id="8c077-131">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="8c077-131">Related Tasks</span></span>  
  
|<span data-ttu-id="8c077-132">主题</span><span class="sxs-lookup"><span data-stu-id="8c077-132">Topic</span></span>|<span data-ttu-id="8c077-133">说明</span><span class="sxs-lookup"><span data-stu-id="8c077-133">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="8c077-134">使用多维数据集向导创建多维数据集</span><span class="sxs-lookup"><span data-stu-id="8c077-134">Create a Cube Using the Cube Wizard</span></span>](create-a-cube-using-the-cube-wizard.md)|<span data-ttu-id="8c077-135">说明如何使用多维数据集向导定义多维数据集、维度、维度属性以及用户定义层次结构。</span><span class="sxs-lookup"><span data-stu-id="8c077-135">Describes how to use the Cube Wizard to define a cube, dimensions, dimension attributes, and user-defined hierarchies.</span></span>|  
|[<span data-ttu-id="8c077-136">在多维模型中创建度量值和度量值组</span><span class="sxs-lookup"><span data-stu-id="8c077-136">Create Measures and Measure Groups in Multidimensional Models</span></span>](create-measures-and-measure-groups-in-multidimensional-models.md)|<span data-ttu-id="8c077-137">介绍如何定义度量值组。</span><span class="sxs-lookup"><span data-stu-id="8c077-137">Describes how to define measure groups.</span></span>|  
|[<span data-ttu-id="8c077-138">多维模型中的计算</span><span class="sxs-lookup"><span data-stu-id="8c077-138">Calculations in Multidimensional Models</span></span>](calculations-in-multidimensional-models.md)|<span data-ttu-id="8c077-139">说明如何在 MDX 脚本中定义和配置计算。</span><span class="sxs-lookup"><span data-stu-id="8c077-139">Describes how to define and configure a calculation in an MDX script.</span></span>|  
|[<span data-ttu-id="8c077-140">多维模型中的操作</span><span class="sxs-lookup"><span data-stu-id="8c077-140">Actions in Multidimensional Models</span></span>](actions-in-multidimensional-models.md)|<span data-ttu-id="8c077-141">说明如何定义和配置操作。</span><span class="sxs-lookup"><span data-stu-id="8c077-141">Describes how to define and configure an action.</span></span>|  
|[<span data-ttu-id="8c077-142">多维模型中的透视</span><span class="sxs-lookup"><span data-stu-id="8c077-142">Perspectives in Multidimensional Models</span></span>](perspectives-in-multidimensional-models.md)|<span data-ttu-id="8c077-143">说明如何定义和配置透视。</span><span class="sxs-lookup"><span data-stu-id="8c077-143">Describes how to define and configure a perspective.</span></span>|  
|[<span data-ttu-id="8c077-144">定义存储过程</span><span class="sxs-lookup"><span data-stu-id="8c077-144">Defining Stored Procedures</span></span>](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)|<span data-ttu-id="8c077-145">说明如何使用存储过程。</span><span class="sxs-lookup"><span data-stu-id="8c077-145">Describes how to work with stored procedures.</span></span>|  
  
  
