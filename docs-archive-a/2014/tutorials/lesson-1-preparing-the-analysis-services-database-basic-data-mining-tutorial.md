---
title: 第1课：准备 Analysis Services 数据库 (数据挖掘基础教程) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2a796977-6568-4705-9d27-86a9b36658c2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 07647a940851fbdbdc65357e168747662dc88380
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694196"
---
# <a name="lesson-1-preparing-the-analysis-services-database-basic-data-mining-tutorial"></a><span data-ttu-id="816c3-102">第 1 课：准备 Analysis Services 数据库（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="816c3-102">Lesson 1: Preparing the Analysis Services Database (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="816c3-103">你是 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 在中设计商业智能应用程序的人员的新员工 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="816c3-103">You are a new employee of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] who has been tasked with designing a business intelligence application in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span> [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]<span data-ttu-id="816c3-104">希望利用您的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据挖掘经验来发现有关已购买自行车的人员的有趣且可操作的信息。</span><span class="sxs-lookup"><span data-stu-id="816c3-104">hopes to leverage your [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data mining experience to discover interesting and actionable information about people who have purchased bicycles.</span></span> <span data-ttu-id="816c3-105">然后，他们希望您预测哪些预期客户将来最有可能购买自行车。</span><span class="sxs-lookup"><span data-stu-id="816c3-105">They then want you to predict which prospective customers are most likely to purchase a bicycle in the future.</span></span>  
  
 <span data-ttu-id="816c3-106">在中设计此应用程序时， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 将 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 基于 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 用于多维建模和数据挖掘的项目模板在项目中创建。</span><span class="sxs-lookup"><span data-stu-id="816c3-106">Designing this application in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] starts with the creation in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] of a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project based on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project template for multidimensional modeling and data mining.</span></span> <span data-ttu-id="816c3-107">创建 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 项目后，再定义一个或多个数据源。</span><span class="sxs-lookup"><span data-stu-id="816c3-107">After you create an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, you define one or more data sources.</span></span> <span data-ttu-id="816c3-108">然后，从数据源中选择的表和视图中定义称为*数据源视图*的元数据视图。</span><span class="sxs-lookup"><span data-stu-id="816c3-108">Then, you define a view of the metadata, called a *data source view*, from selected tables and views from the data sources.</span></span>  
  
 <span data-ttu-id="816c3-109">在本课中，您将创建一个 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 项目，定义一个单个数据源，并向数据源视图添加一个表子集。</span><span class="sxs-lookup"><span data-stu-id="816c3-109">In this lesson, you will create an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, define a single data source, and add a subset of tables to a data source view.</span></span> <span data-ttu-id="816c3-110">本课程包括以下任务：</span><span class="sxs-lookup"><span data-stu-id="816c3-110">This lesson includes the following tasks:</span></span>  
  
 [<span data-ttu-id="816c3-111">&#40;数据挖掘基础教程创建 Analysis Services 项目&#41;</span><span class="sxs-lookup"><span data-stu-id="816c3-111">Creating an Analysis Services Project &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="816c3-112">创建数据源 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="816c3-112">Creating a Data Source &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="816c3-113">创建数据源视图 &#40;数据挖掘基础教程&#41;</span><span class="sxs-lookup"><span data-stu-id="816c3-113">Creating a Data Source View &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-data-source-view-basic-data-mining-tutorial.md)  
  
## <a name="first-task-in-lesson"></a><span data-ttu-id="816c3-114">课程中的第一个任务</span><span class="sxs-lookup"><span data-stu-id="816c3-114">First Task in Lesson</span></span>  
 [<span data-ttu-id="816c3-115">&#40;数据挖掘基础教程创建 Analysis Services 项目&#41;</span><span class="sxs-lookup"><span data-stu-id="816c3-115">Creating an Analysis Services Project &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="816c3-116">下一课</span><span class="sxs-lookup"><span data-stu-id="816c3-116">Next Lesson</span></span>  
 [<span data-ttu-id="816c3-117">第2课： &#40;基本数据挖掘教程生成目标邮件结构&#41;</span><span class="sxs-lookup"><span data-stu-id="816c3-117">Lesson 2: Building a Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="816c3-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="816c3-118">See Also</span></span>  
 <span data-ttu-id="816c3-119">[多维模型中的数据源视图](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models) </span><span class="sxs-lookup"><span data-stu-id="816c3-119">[Data Source Views in Multidimensional Models](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models) </span></span>  
 <span data-ttu-id="816c3-120">[支持 &#40;SSAS 多维&#41;的数据源](https://docs.microsoft.com/analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional) </span><span class="sxs-lookup"><span data-stu-id="816c3-120">[Data Sources Supported &#40;SSAS Multidimensional&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional) </span></span>  
 <span data-ttu-id="816c3-121">[&#40;SSDT 生成 Analysis Services 项目&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/build-analysis-services-projects-ssdt) </span><span class="sxs-lookup"><span data-stu-id="816c3-121">[Build Analysis Services Projects &#40;SSDT&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/build-analysis-services-projects-ssdt) </span></span>  
 [<span data-ttu-id="816c3-122">创建 Analysis Services 项目</span><span class="sxs-lookup"><span data-stu-id="816c3-122">Creating an Analysis Services Project</span></span>](../analysis-services/lesson-1-1-creating-an-analysis-services-project.md)  
  
  
