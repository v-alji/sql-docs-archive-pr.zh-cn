---
title: 第2课：定义和部署多维数据集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: bb62e3c9-462f-4ad2-ac8e-92e2f9e9cc28
author: minewiskan
ms.author: owend
ms.openlocfilehash: a2c043920ac646ec4da9eaa2aace4bf6f48e694c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589339"
---
# <a name="lesson-2-defining-and-deploying-a-cube"></a><span data-ttu-id="6b588-102">第 2 课：定义和部署多维数据集</span><span class="sxs-lookup"><span data-stu-id="6b588-102">Lesson 2: Defining and Deploying a Cube</span></span>
  <span data-ttu-id="6b588-103">在项目中定义数据源视图后，便可以 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 定义初始 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 多维数据集。</span><span class="sxs-lookup"><span data-stu-id="6b588-103">After you define a data source view in your [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, you are ready to define an initial [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube.</span></span>  
  
 <span data-ttu-id="6b588-104">可以使用多维数据集向导，通过单个步骤定义一个多维数据集及其维度。</span><span class="sxs-lookup"><span data-stu-id="6b588-104">You can define a cube and its dimensions in a single pass using the Cube Wizard.</span></span> <span data-ttu-id="6b588-105">也可以先定义一个或多个维度，然后使用多维数据集向导定义一个使用这些维度的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="6b588-105">Alternatively, you can define one or more dimensions and then use the Cube Wizard to define a cube that uses those dimensions.</span></span> <span data-ttu-id="6b588-106">如果要设计一个复杂的解决方案，通常是先定义维度。</span><span class="sxs-lookup"><span data-stu-id="6b588-106">If you are designing a complex solution, you generally start by defining the dimensions.</span></span> <span data-ttu-id="6b588-107">有关详细信息，请参阅 [多维模型中的维度](multidimensional-models/dimensions-in-multidimensional-models.md) 或 [多维模型中的多维数据集](multidimensional-models/cubes-in-multidimensional-models.md)。</span><span class="sxs-lookup"><span data-stu-id="6b588-107">For more information, see [Dimensions in Multidimensional Models](multidimensional-models/dimensions-in-multidimensional-models.md) or [Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6b588-108">本教程的所有课程中的已完成项目均可以从网上获得。</span><span class="sxs-lookup"><span data-stu-id="6b588-108">Completed projects for all of the lessons in this tutorial are available online.</span></span> <span data-ttu-id="6b588-109">您可以通过将前一课程的已完成项目作为起始点，跳转到后面的任何课程。</span><span class="sxs-lookup"><span data-stu-id="6b588-109">You can jump ahead to any lesson by using the completed project from the previous lesson as a starting point.</span></span> <span data-ttu-id="6b588-110">[单击此处](https://go.microsoft.com/fwlink/?LinkID=221866) 可以下载本教程随附的示例项目。</span><span class="sxs-lookup"><span data-stu-id="6b588-110">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to download the sample projects that go with this tutorial.</span></span>  
  
 <span data-ttu-id="6b588-111">本课程包含以下任务：</span><span class="sxs-lookup"><span data-stu-id="6b588-111">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="6b588-112">定义维度</span><span class="sxs-lookup"><span data-stu-id="6b588-112">Defining a Dimension</span></span>](lesson-2-1-defining-a-dimension.md)  
 <span data-ttu-id="6b588-113">在该任务中，将使用维度向导来定义维度。</span><span class="sxs-lookup"><span data-stu-id="6b588-113">In this task, you use the Dimension Wizard to define a dimension.</span></span>  
  
 [<span data-ttu-id="6b588-114">定义多维数据集</span><span class="sxs-lookup"><span data-stu-id="6b588-114">Defining a Cube</span></span>](lesson-2-2-defining-a-cube.md)  
 <span data-ttu-id="6b588-115">在该任务中，将使用多维数据集向导来定义一个初始 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 多维数据集。</span><span class="sxs-lookup"><span data-stu-id="6b588-115">In this task, you use the Cube Wizard to define an initial [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube.</span></span>  
  
 [<span data-ttu-id="6b588-116">向维度添加属性</span><span class="sxs-lookup"><span data-stu-id="6b588-116">Adding Attributes to Dimensions</span></span>](lesson-2-3-adding-attributes-to-dimensions.md)  
 <span data-ttu-id="6b588-117">在该任务中，将向您创建的维度中添加属性。</span><span class="sxs-lookup"><span data-stu-id="6b588-117">In this task, you add attributes to the dimensions that you created.</span></span>  
  
 [<span data-ttu-id="6b588-118">检查多维数据集和维度属性</span><span class="sxs-lookup"><span data-stu-id="6b588-118">Reviewing Cube and Dimension Properties</span></span>](lesson-2-4-reviewing-cube-and-dimension-properties.md)  
 <span data-ttu-id="6b588-119">在该任务中，将检查您使用多维数据集向导定义的多维数据集的结构。</span><span class="sxs-lookup"><span data-stu-id="6b588-119">In this task, you review the structure of the cube that you defined by using the Cube Wizard.</span></span>  
  
 [<span data-ttu-id="6b588-120">部署 Analysis Services 项目</span><span class="sxs-lookup"><span data-stu-id="6b588-120">Deploying an Analysis Services Project</span></span>](lesson-2-5-deploying-an-analysis-services-project.md)  
 <span data-ttu-id="6b588-121">在此任务中，将 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 项目部署到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]本地实例，并了解某些部署属性。</span><span class="sxs-lookup"><span data-stu-id="6b588-121">In this task, you deploy the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project to your local instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], and learn about certain deployment properties.</span></span>  
  
 [<span data-ttu-id="6b588-122">浏览多维数据集</span><span class="sxs-lookup"><span data-stu-id="6b588-122">Browsing the Cube</span></span>](lesson-2-6-browsing-the-cube.md)  
 <span data-ttu-id="6b588-123">在该任务中，将使用 Excel 或来 MDX 查询设计器来浏览多维数据集和维度数据。</span><span class="sxs-lookup"><span data-stu-id="6b588-123">In this task, you browse the cube and dimension data by using Excel or the MDX query designer.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="6b588-124">下一课</span><span class="sxs-lookup"><span data-stu-id="6b588-124">Next Lesson</span></span>  
 [<span data-ttu-id="6b588-125">第 3 课：修改度量值、属性和层次结构</span><span class="sxs-lookup"><span data-stu-id="6b588-125">Lesson 3: Modifying Measures, Attributes and Hierarchies</span></span>](lesson-3-modifying-measures-attributes-and-hierarchies.md)  
  
## <a name="see-also"></a><span data-ttu-id="6b588-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6b588-126">See Also</span></span>  
 <span data-ttu-id="6b588-127">[Analysis Services 教程方案](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="6b588-127">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 <span data-ttu-id="6b588-128">[&#40;艾德作品的多维建模教程&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="6b588-128">[Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span></span>  
 <span data-ttu-id="6b588-129">[多维模型中的维度](multidimensional-models/dimensions-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="6b588-129">[Dimensions in Multidimensional Models](multidimensional-models/dimensions-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="6b588-130">[多维模型中的多维数据集](multidimensional-models/cubes-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="6b588-130">[Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="6b588-131">[配置 Analysis Services 项目属性 &#40;SSDT&#41;](multidimensional-models/configure-analysis-services-project-properties-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="6b588-131">[Configure Analysis Services Project Properties &#40;SSDT&#41;](multidimensional-models/configure-analysis-services-project-properties-ssdt.md) </span></span>  
 <span data-ttu-id="6b588-132">[&#40;SSDT 生成 Analysis Services 项目&#41;](multidimensional-models/build-analysis-services-projects-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="6b588-132">[Build Analysis Services Projects &#40;SSDT&#41;](multidimensional-models/build-analysis-services-projects-ssdt.md) </span></span>  
 [<span data-ttu-id="6b588-133">部署 Analysis Services 项目 (SSDT)</span><span class="sxs-lookup"><span data-stu-id="6b588-133">Deploy Analysis Services Projects &#40;SSDT&#41;</span></span>](multidimensional-models/deploy-analysis-services-projects-ssdt.md)  
  
  
