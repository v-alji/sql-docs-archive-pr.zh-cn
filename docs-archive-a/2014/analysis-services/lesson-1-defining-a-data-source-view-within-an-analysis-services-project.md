---
title: 第1课：定义 Analysis Services 项目中的数据源视图 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7d3ffabd-78ae-4204-8323-29949d030c16
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8a3d69225217154e5072d0cd34349a247730ddaf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693141"
---
# <a name="lesson-1-defining-a-data-source-view-within-an-analysis-services-project"></a><span data-ttu-id="168ed-102">第 1 课：在 Analysis Services 项目中定义数据源视图</span><span class="sxs-lookup"><span data-stu-id="168ed-102">Lesson 1: Defining a Data Source View within an Analysis Services Project</span></span>
  <span data-ttu-id="168ed-103">若要在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中设计商业智能应用程序，请先在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 中创建一个 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]项目。</span><span class="sxs-lookup"><span data-stu-id="168ed-103">Designing a business intelligence application in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] starts with creating an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="168ed-104">在此项目中，您将从数据源视图开始定义解决方案的所有元素。</span><span class="sxs-lookup"><span data-stu-id="168ed-104">Within this project, you define all the elements of your solution, starting with a data source view.</span></span>  
  
 <span data-ttu-id="168ed-105">本课程包含以下任务：</span><span class="sxs-lookup"><span data-stu-id="168ed-105">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="168ed-106">创建 Analysis Services 项目</span><span class="sxs-lookup"><span data-stu-id="168ed-106">Creating an Analysis Services Project</span></span>](lesson-1-1-creating-an-analysis-services-project.md)  
 <span data-ttu-id="168ed-107">在本任务中，将基于 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 多维模型模板创建 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 项目。</span><span class="sxs-lookup"><span data-stu-id="168ed-107">In this task, you create the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project, based on an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] multidimensional model template.</span></span>  
  
 [<span data-ttu-id="168ed-108">定义数据源</span><span class="sxs-lookup"><span data-stu-id="168ed-108">Defining a Data Source</span></span>](lesson-1-2-defining-a-data-source.md)  
 <span data-ttu-id="168ed-109">在本任务中，将 **AdventureWorksDW2012** 数据库指定为将在后续课程中定义的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 维度和多维数据集的数据源。</span><span class="sxs-lookup"><span data-stu-id="168ed-109">In this task, you specify the **AdventureWorksDW2012** database as the data source for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dimensions and cubes that you will define in subsequent lessons.</span></span>  
  
 [<span data-ttu-id="168ed-110">定义数据源视图</span><span class="sxs-lookup"><span data-stu-id="168ed-110">Defining a Data Source View</span></span>](lesson-1-3-defining-a-data-source-view.md)  
 <span data-ttu-id="168ed-111">在本任务中，为来自 **AdventureWorksDW2012** 数据库中选定表的元数据定义一个统一视图。</span><span class="sxs-lookup"><span data-stu-id="168ed-111">In this task, you define a single unified view of the metadata from selected tables in the **AdventureWorksDW2012** database.</span></span>  
  
 [<span data-ttu-id="168ed-112">修改默认表名</span><span class="sxs-lookup"><span data-stu-id="168ed-112">Modifying Default Table Names</span></span>](lesson-1-4-modifying-default-table-names.md)  
 <span data-ttu-id="168ed-113">在本任务中，将修改数据源视图中的表名，以使您将要定义的后续 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对象名更加用户友好。</span><span class="sxs-lookup"><span data-stu-id="168ed-113">In this task, you modify table names in the data source view, so that the names of subsequent [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects that you define will be more user-friendly.</span></span>  
  
 <span data-ttu-id="168ed-114">将您的结果与为本课程生成的示例项目文件进行比较。</span><span class="sxs-lookup"><span data-stu-id="168ed-114">Compare your results against a sample project file that was built for this lesson.</span></span> <span data-ttu-id="168ed-115">有关下载本教程附随的示例项目的详细信息，请参阅 codeplex 上产品示例页上的 [SSAS Multidimensional Model Projects for SQL Server 2012](https://go.microsoft.com/fwlink/p/?LinkID=221866) （用于 SQL Server 2012 的 SSAS 多维模型项目）。</span><span class="sxs-lookup"><span data-stu-id="168ed-115">For more information about downloading the sample projects that go with this tutorial, see [SSAS Multidimensional Model Projects for SQL Server 2012](https://go.microsoft.com/fwlink/p/?LinkID=221866) on the product samples page on codeplex.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="168ed-116">下一课</span><span class="sxs-lookup"><span data-stu-id="168ed-116">Next Lesson</span></span>  
 [<span data-ttu-id="168ed-117">第 2 课：定义和部署多维数据集</span><span class="sxs-lookup"><span data-stu-id="168ed-117">Lesson 2: Defining and Deploying a Cube</span></span>](lesson-2-defining-and-deploying-a-cube.md)  
  
## <a name="see-also"></a><span data-ttu-id="168ed-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="168ed-118">See Also</span></span>  
 <span data-ttu-id="168ed-119">[&#40;SSDT 创建 Analysis Services 项目&#41;](multidimensional-models/create-an-analysis-services-project-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="168ed-119">[Create an Analysis Services Project &#40;SSDT&#41;](multidimensional-models/create-an-analysis-services-project-ssdt.md) </span></span>  
 <span data-ttu-id="168ed-120">[支持 &#40;SSAS 多维&#41;的数据源](multidimensional-models/supported-data-sources-ssas-multidimensional.md) </span><span class="sxs-lookup"><span data-stu-id="168ed-120">[Data Sources Supported &#40;SSAS Multidimensional&#41;](multidimensional-models/supported-data-sources-ssas-multidimensional.md) </span></span>  
 <span data-ttu-id="168ed-121">[多维模型中的数据源视图](multidimensional-models/data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="168ed-121">[Data Source Views in Multidimensional Models](multidimensional-models/data-source-views-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="168ed-122">[Analysis Services 教程方案](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="168ed-122">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 [<span data-ttu-id="168ed-123">多维建模（Adventure Works 教程）</span><span class="sxs-lookup"><span data-stu-id="168ed-123">Multidimensional Modeling &#40;Adventure Works Tutorial&#41;</span></span>](multidimensional-modeling-adventure-works-tutorial.md)  
  
  
