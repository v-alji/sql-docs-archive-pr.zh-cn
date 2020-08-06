---
title: " (艾德 Works 教程) 的多维建模Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- tutorials [Analysis Services]
- Analysis Services, tutorials
ms.assetid: db55e226-601a-4026-8651-573195555a59
author: minewiskan
ms.author: owend
ms.openlocfilehash: cd2e8f856d36cab045e6cbc4d34f7cfeffac3c3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588731"
---
# <a name="multidimensional-modeling-adventure-works-tutorial"></a><span data-ttu-id="ba287-102">多维建模（Adventure Works 教程）</span><span class="sxs-lookup"><span data-stu-id="ba287-102">Multidimensional Modeling (Adventure Works Tutorial)</span></span>
  <span data-ttu-id="ba287-103">欢迎使用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程。</span><span class="sxs-lookup"><span data-stu-id="ba287-103">Welcome to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial.</span></span> <span data-ttu-id="ba287-104">本教程通过在所有示例中使用虚构公司 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] ，说明如何使用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 开发和部署 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="ba287-104">This tutorial describes how to use [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] to develop and deploy an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, using the fictitious company [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] for all examples.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="ba287-105">学习内容</span><span class="sxs-lookup"><span data-stu-id="ba287-105">What You Will Learn</span></span>  
 <span data-ttu-id="ba287-106">在本教程中，您将了解以下内容：</span><span class="sxs-lookup"><span data-stu-id="ba287-106">In this tutorial, you will learn the following:</span></span>  
  
-   <span data-ttu-id="ba287-107">如何在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 的 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]项目中定义数据源、数据源视图、维度、属性、属性关系、层次结构和多维数据集。</span><span class="sxs-lookup"><span data-stu-id="ba287-107">How to define data sources, data source views, dimensions, attributes, attribute relationships, hierarchies, and cubes in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project within [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
-   <span data-ttu-id="ba287-108">如何通过将 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 项目部署到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]实例来查看多维数据集和维度数据，以及如何在随后处理已部署的对象以使用基础数据源中的数据来填充对象。</span><span class="sxs-lookup"><span data-stu-id="ba287-108">How to view cube and dimension data by deploying the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], and how to then process the deployed objects to populate them with data from the underlying data source.</span></span>  
  
-   <span data-ttu-id="ba287-109">如何在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 项目中修改度量值、维度、层次结构、属性和度量值组，以及如何将增量更改部署到开发服务器上的已部署多维数据集。</span><span class="sxs-lookup"><span data-stu-id="ba287-109">How to modify the measures, dimensions, hierarchies, attributes, and measure groups in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and how to then deploy the incremental changes to the deployed cube on the development server.</span></span>  
  
-   <span data-ttu-id="ba287-110">如何定义多维数据集内的计算、关键绩效指标 (KPI)、操作、透视、翻译和安全角色。</span><span class="sxs-lookup"><span data-stu-id="ba287-110">How to define calculations, Key Performance Indicators (KPIs), actions, perspectives, translations, and security roles within a cube.</span></span>  
  
 <span data-ttu-id="ba287-111">在此教程中随附应用场景说明，以便您可以更好地理解这些课程的上下文。</span><span class="sxs-lookup"><span data-stu-id="ba287-111">A scenario description accompanies this tutorial so that you can better understand the context for these lessons.</span></span> <span data-ttu-id="ba287-112">有关详细信息，请参阅 [Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="ba287-112">For more information, see [Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ba287-113">先决条件</span><span class="sxs-lookup"><span data-stu-id="ba287-113">Prerequisites</span></span>  
 <span data-ttu-id="ba287-114">要完成本教程的所有课程，您将需要示例数据、示例项目文件以及软件。</span><span class="sxs-lookup"><span data-stu-id="ba287-114">You will need sample data, sample project files, and software to complete all of the lessons in this tutorial.</span></span> <span data-ttu-id="ba287-115">有关如何查找和安装本教程的必备组件的说明，请参阅 [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](install-sample-data-and-projects.md)。</span><span class="sxs-lookup"><span data-stu-id="ba287-115">For instructions on how to find and install the prerequisites for this tutorial, see [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](install-sample-data-and-projects.md).</span></span>  
  
 <span data-ttu-id="ba287-116">此外，必须具有下列权限才能成功完成本教程：</span><span class="sxs-lookup"><span data-stu-id="ba287-116">Additionally, the following permissions must be in place to successfully complete this tutorial:</span></span>  
  
-   <span data-ttu-id="ba287-117">您必须是 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 计算机上本地管理员组的成员或 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]实例中的服务器管理角色的成员。</span><span class="sxs-lookup"><span data-stu-id="ba287-117">You must be a member of the Administrators local group on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] computer or be a member of the server administration role in the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="ba287-118">您在 **AdventureWorksDW2012** 示例数据库中必须具有读取权限。</span><span class="sxs-lookup"><span data-stu-id="ba287-118">You must have Read permissions in the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="ba287-119">此示例数据库对于 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 版本有效。</span><span class="sxs-lookup"><span data-stu-id="ba287-119">This sample database is valid for the [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] release.</span></span>  
  
## <a name="lessons"></a><span data-ttu-id="ba287-120">课程</span><span class="sxs-lookup"><span data-stu-id="ba287-120">Lessons</span></span>  
 <span data-ttu-id="ba287-121">本教程包括以下几课。</span><span class="sxs-lookup"><span data-stu-id="ba287-121">This tutorial includes the following lessons.</span></span>  
  
|<span data-ttu-id="ba287-122">课程</span><span class="sxs-lookup"><span data-stu-id="ba287-122">Lesson</span></span>|<span data-ttu-id="ba287-123">估计完成时间</span><span class="sxs-lookup"><span data-stu-id="ba287-123">Estimated time to complete</span></span>|  
|------------|--------------------------------|  
|[<span data-ttu-id="ba287-124">第 1 课：在 Analysis Services 项目中定义数据源视图</span><span class="sxs-lookup"><span data-stu-id="ba287-124">Lesson 1: Defining a Data Source View within an Analysis Services Project</span></span>](lesson-1-defining-a-data-source-view-within-an-analysis-services-project.md)|<span data-ttu-id="ba287-125">15 分钟</span><span class="sxs-lookup"><span data-stu-id="ba287-125">15 minutes</span></span>|  
|[<span data-ttu-id="ba287-126">第 2 课：定义和部署多维数据集</span><span class="sxs-lookup"><span data-stu-id="ba287-126">Lesson 2: Defining and Deploying a Cube</span></span>](lesson-2-defining-and-deploying-a-cube.md)|<span data-ttu-id="ba287-127">30 分钟</span><span class="sxs-lookup"><span data-stu-id="ba287-127">30 minutes</span></span>|  
|[<span data-ttu-id="ba287-128">第 3 课：修改度量值、属性和层次结构</span><span class="sxs-lookup"><span data-stu-id="ba287-128">Lesson 3: Modifying Measures, Attributes and Hierarchies</span></span>](lesson-3-modifying-measures-attributes-and-hierarchies.md)|<span data-ttu-id="ba287-129">45 分钟</span><span class="sxs-lookup"><span data-stu-id="ba287-129">45 minutes</span></span>|  
|[<span data-ttu-id="ba287-130">第 4 课：定义高级属性和维度属性</span><span class="sxs-lookup"><span data-stu-id="ba287-130">Lesson 4: Defining Advanced Attribute and Dimension Properties</span></span>](lesson-4-defining-advanced-attribute-and-dimension-properties.md)|<span data-ttu-id="ba287-131">120 分钟</span><span class="sxs-lookup"><span data-stu-id="ba287-131">120 minutes</span></span>|  
|[<span data-ttu-id="ba287-132">第 5 课：定义维度和度量值组之间的关系</span><span class="sxs-lookup"><span data-stu-id="ba287-132">Lesson 5: Defining Relationships Between Dimensions and Measure Groups</span></span>](lesson-5-defining-relationships-between-dimensions-and-measure-groups.md)|<span data-ttu-id="ba287-133">45 分钟</span><span class="sxs-lookup"><span data-stu-id="ba287-133">45 minutes</span></span>|  
|[<span data-ttu-id="ba287-134">第 6 课：定义计算</span><span class="sxs-lookup"><span data-stu-id="ba287-134">Lesson 6: Defining Calculations</span></span>](lesson-6-defining-calculations.md)|<span data-ttu-id="ba287-135">45 分钟</span><span class="sxs-lookup"><span data-stu-id="ba287-135">45 minutes</span></span>|  
|[<span data-ttu-id="ba287-136">第 7 课：定义关键绩效指标 (KPI)</span><span class="sxs-lookup"><span data-stu-id="ba287-136">Lesson 7: Defining Key Performance Indicators &#40;KPIs&#41;</span></span>](lesson-7-defining-key-performance-indicators-kpis.md)|<span data-ttu-id="ba287-137">30 分钟</span><span class="sxs-lookup"><span data-stu-id="ba287-137">30 minutes</span></span>|  
|[<span data-ttu-id="ba287-138">第 8 课：定义操作</span><span class="sxs-lookup"><span data-stu-id="ba287-138">Lesson 8: Defining Actions</span></span>](lesson-8-defining-actions.md)|<span data-ttu-id="ba287-139">30 分钟</span><span class="sxs-lookup"><span data-stu-id="ba287-139">30 minutes</span></span>|  
|[<span data-ttu-id="ba287-140">第 9 课：定义透视和翻译</span><span class="sxs-lookup"><span data-stu-id="ba287-140">Lesson 9: Defining Perspectives and Translations</span></span>](lesson-9-defining-perspectives-and-translations.md)|<span data-ttu-id="ba287-141">30 分钟</span><span class="sxs-lookup"><span data-stu-id="ba287-141">30 minutes</span></span>|  
|[<span data-ttu-id="ba287-142">第 10 课：定义管理角色</span><span class="sxs-lookup"><span data-stu-id="ba287-142">Lesson 10: Defining Administrative Roles</span></span>](lesson-10-defining-administrative-roles.md)|<span data-ttu-id="ba287-143">15 分钟</span><span class="sxs-lookup"><span data-stu-id="ba287-143">15 minutes</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="ba287-144">您将在本教程中创建的多维数据集数据库是 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 多维模型项目的简化版本，此项目是可在 codeplex 站点上下载的 Adventure Works 示例数据库的一部分。</span><span class="sxs-lookup"><span data-stu-id="ba287-144">The cube database that you will create in this tutorial is a simplified version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] multidimensional model project that is part of the Adventure Works sample databases available for download on the codeplex site.</span></span> <span data-ttu-id="ba287-145">简化了艾德公司数据库的教程版本，使你能够更好地专注于要立即改进的特定技能。</span><span class="sxs-lookup"><span data-stu-id="ba287-145">The tutorial version of the Adventure Works multidimensional database is simplified to bring greater focus to the specific skills that you will want to improve right away.</span></span> <span data-ttu-id="ba287-146">在完成该教程后，请考虑自己探索该多维模型项目，以便进一步理解 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 多维建模。</span><span class="sxs-lookup"><span data-stu-id="ba287-146">After you complete the tutorial, consider exploring the multidimensional model project on your own to further your understanding of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] multidimensional modeling.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="ba287-147">下一步</span><span class="sxs-lookup"><span data-stu-id="ba287-147">Next Step</span></span>  
 <span data-ttu-id="ba287-148">要开始学习本教程，请转到第一课： [Lesson 1: Defining a Data Source View within an Analysis Services Project](lesson-1-defining-a-data-source-view-within-an-analysis-services-project.md)。</span><span class="sxs-lookup"><span data-stu-id="ba287-148">To begin the tutorial, continue to the first lesson: [Lesson 1: Defining a Data Source View within an Analysis Services Project](lesson-1-defining-a-data-source-view-within-an-analysis-services-project.md).</span></span>  
  
  
