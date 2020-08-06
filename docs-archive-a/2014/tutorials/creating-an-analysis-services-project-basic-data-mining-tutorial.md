---
title: 创建 Analysis Services 项目 (基本数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 784c0401-0358-4117-9c85-4e8220ce71d9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 83eb808bc7d18ebe715d309d9f911c010ee172d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577967"
---
# <a name="creating-an-analysis-services-project-basic-data-mining-tutorial"></a><span data-ttu-id="f0aea-102">创建 Analysis Services 项目（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="f0aea-102">Creating an Analysis Services Project (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="f0aea-103">每个 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 项目都定义单个数据库中的对象 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f0aea-103">Each [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project defines the objects in a single [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="f0aea-104">一个 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库可以包含很多不同类型的对象</span><span class="sxs-lookup"><span data-stu-id="f0aea-104">An [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database can contains many different types of objects</span></span>  
  
-   <span data-ttu-id="f0aea-105">多维模型（多维数据集）</span><span class="sxs-lookup"><span data-stu-id="f0aea-105">Multidimensional models (cubes)</span></span>  
  
-   <span data-ttu-id="f0aea-106">挖掘结构和挖掘模型</span><span class="sxs-lookup"><span data-stu-id="f0aea-106">Mining structures and mining models</span></span>  
  
-   <span data-ttu-id="f0aea-107">支持各种对象，如数据源、数据源视图和自定义程序集</span><span class="sxs-lookup"><span data-stu-id="f0aea-107">Supporting objects such as data sources, data source views, and custom assemblies</span></span>  
  
 <span data-ttu-id="f0aea-108">请注意您 **不** 需要有多维数据集就可以进行数据挖掘。</span><span class="sxs-lookup"><span data-stu-id="f0aea-108">Note that you **do not** require a cube to do data mining.</span></span> <span data-ttu-id="f0aea-109">如果您需要对现有多维数据集执行数据挖掘，应将数据挖掘模型添加到用于生成多维数据集的同一项目。</span><span class="sxs-lookup"><span data-stu-id="f0aea-109">If you need to perform data mining on an existing cube, you should add the data mining models to the same project you used to build the cube.</span></span> <span data-ttu-id="f0aea-110">但是，对于大多数用途，您可以针对关系数据源（如数据仓库）生成模型，如果不涉及多维数据集，将获得更好的性能。</span><span class="sxs-lookup"><span data-stu-id="f0aea-110">However, for most purposes you can build your models on relational data sources, such as a data warehouse, and get better performance if a cube is not involved.</span></span>  
  
 <span data-ttu-id="f0aea-111">在本教程中，您将使用一个关系数据仓库 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]作为数据源。</span><span class="sxs-lookup"><span data-stu-id="f0aea-111">In this tutorial you will use a relational data warehouse, [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)], as the data source.</span></span> <span data-ttu-id="f0aea-112">你将所有数据挖掘对象部署到名为 `BasicDataMining` 的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库，它仅用于数据挖掘。</span><span class="sxs-lookup"><span data-stu-id="f0aea-112">You will deploy all your data mining objects to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database named `BasicDataMining`, used just for data mining.</span></span>  
  
 <span data-ttu-id="f0aea-113">默认情况下， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 使用新项目的“localhost” \*\*\*\* 实例。</span><span class="sxs-lookup"><span data-stu-id="f0aea-113">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses the **localhost** instance for new projects.</span></span> <span data-ttu-id="f0aea-114">如果使用命名实例或者另一台服务器，则必须首先创建和打开该项目，然后更改实例名称。</span><span class="sxs-lookup"><span data-stu-id="f0aea-114">If you are using a named instance or a different server, you must first create and open the project and then change the instance name.</span></span>  
  
 <span data-ttu-id="f0aea-115">有关项目的详细信息 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，请参阅[创建 Analysis Services 项目](../analysis-services/lesson-1-1-creating-an-analysis-services-project.md)。</span><span class="sxs-lookup"><span data-stu-id="f0aea-115">For more information about [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] projects, see [Creating an Analysis Services Project](../analysis-services/lesson-1-1-creating-an-analysis-services-project.md).</span></span>  
  
### <a name="to-create-an-analysis-services-project"></a><span data-ttu-id="f0aea-116">创建 Analysis Services 项目</span><span class="sxs-lookup"><span data-stu-id="f0aea-116">To create an Analysis Services project</span></span>  
  
1.  <span data-ttu-id="f0aea-117">打开 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f0aea-117">Open [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="f0aea-118">在 **“文件”** 菜单上，指向 **“新建”**，然后选择 **“项目”**。</span><span class="sxs-lookup"><span data-stu-id="f0aea-118">On the **File** menu, point to **New**, and then select **Project**.</span></span>  
  
3.  <span data-ttu-id="f0aea-119">确保已选中 **“项目类型”** 窗格中的 **“商业智能项目”** 。</span><span class="sxs-lookup"><span data-stu-id="f0aea-119">Verify that **Business Intelligence Projects** is selected in the **Project types** pane.</span></span>  
  
4.  <span data-ttu-id="f0aea-120">在 **“模板”** 窗格中选择 **“Analysis Services 多维和数据挖掘项目”**。</span><span class="sxs-lookup"><span data-stu-id="f0aea-120">In the **Templates** pane, select **Analysis Services Multidimensional and Data Mining Project**.</span></span>  
  
5.  <span data-ttu-id="f0aea-121">在 "**名称**" 框中，将新项目命名为 `BasicDataMining` 。</span><span class="sxs-lookup"><span data-stu-id="f0aea-121">In the **Name** box, name the new project `BasicDataMining`.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-instance-where-data-mining-objects-are-stored"></a><span data-ttu-id="f0aea-122">更改存储数据挖掘对象的实例</span><span class="sxs-lookup"><span data-stu-id="f0aea-122">To change the instance where data mining objects are stored</span></span>  
  
1.  <span data-ttu-id="f0aea-123">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，选择 **“项目”** 菜单中的 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="f0aea-123">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], on the **Project** menu, select **Properties**.</span></span>  
  
2.  <span data-ttu-id="f0aea-124">在 **“属性页”** 窗格左侧的 **“配置属性”** 下，单击 **“部署”**。</span><span class="sxs-lookup"><span data-stu-id="f0aea-124">On the left side of the **Property Pages** pane, under **Configuration Properties**, click **Deployment**.</span></span>  
  
3.  <span data-ttu-id="f0aea-125">在 **“属性页”** 窗格右侧的 **“目标”** 下，确保 **“服务器”** 名称为 **localhost**。</span><span class="sxs-lookup"><span data-stu-id="f0aea-125">On the right side of the **Property Pages** pane, under **Target**, verify that the **Server** name is **localhost**.</span></span> <span data-ttu-id="f0aea-126">如果使用的是其他实例，请键入该实例的名称。</span><span class="sxs-lookup"><span data-stu-id="f0aea-126">If you are using a different instance, type the name of the instance.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="f0aea-127">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="f0aea-127">Next Task in Lesson</span></span>  
 [<span data-ttu-id="f0aea-128">创建数据源 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="f0aea-128">Creating a Data Source &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="f0aea-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f0aea-129">See Also</span></span>  
 <span data-ttu-id="f0aea-130">[&#40;SSDT 生成 Analysis Services 项目&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/build-analysis-services-projects-ssdt) </span><span class="sxs-lookup"><span data-stu-id="f0aea-130">[Build Analysis Services Projects &#40;SSDT&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/build-analysis-services-projects-ssdt) </span></span>  
 [<span data-ttu-id="f0aea-131">创建 Analysis Services 项目 (SSDT)</span><span class="sxs-lookup"><span data-stu-id="f0aea-131">Create an Analysis Services Project &#40;SSDT&#41;</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt)  
  
  
