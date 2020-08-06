---
title: 部署数据挖掘解决方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], deploying
- deploying [Analysis Services], production environments
- deploying [Analysis Services - data mining]
- solutions [Analysis Services], deploying
- models [Analysis Services], data mining
ms.assetid: d83effc7-437d-42e9-8ac3-b65f79e27043
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5764be2f7530add2fa4cb028b288be69598bb95c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589963"
---
# <a name="deployment-of-data-mining-solutions"></a><span data-ttu-id="d0dfe-102">部署数据挖掘解决方案</span><span class="sxs-lookup"><span data-stu-id="d0dfe-102">Deployment of Data Mining Solutions</span></span>
  <span data-ttu-id="d0dfe-103">数据挖掘过程的最后一步是将模型部署到生产环境中。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-103">The last step in the data mining process is to deploy the models to a production environment.</span></span> <span data-ttu-id="d0dfe-104">部署非常重要，这是因为它使用户可以利用模型，以便执行以任何任务：</span><span class="sxs-lookup"><span data-stu-id="d0dfe-104">Deployment is important because it makes the models available to users so that you can perform any of the following tasks:</span></span>  
  
-   <span data-ttu-id="d0dfe-105">使用这些模型创建预测并做出业务决策。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-105">Use the models to create predictions and make business decisions.</span></span> <span data-ttu-id="d0dfe-106">有关可用于创建查询的工具的信息，请参阅[数据挖掘查询接口](data-mining-query-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-106">For information about the tools you can use to create queries, see [Data Mining Query Interfaces](data-mining-query-tools.md).</span></span>  
  
-   <span data-ttu-id="d0dfe-107">直接将数据挖掘功能嵌入到应用程序。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-107">Embed data mining functionality directly into an application.</span></span> <span data-ttu-id="d0dfe-108">您可以包括分析管理对象 (AMO) 或一个包含一组对象（应用程序可使用这组对象创建、更改、处理以及删除挖掘结构和挖掘模型）的程序集。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-108">You can include Analysis Management Objects (AMO) or an assembly that contains a set of objects that your application can use to create, alter, process, and delete mining structures and mining models.</span></span>  
  
-   <span data-ttu-id="d0dfe-109">创建可供用户用来请求预测、查看趋势或比较模型的报表。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-109">Create reports that let users request predictions, view trends, or compare models.</span></span>  
  
 <span data-ttu-id="d0dfe-110">本节提供有关部署选项的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-110">This section provides detailed information about deployment options.</span></span>  
  
 [<span data-ttu-id="d0dfe-111">部署数据挖掘解决方案的要求</span><span class="sxs-lookup"><span data-stu-id="d0dfe-111">Requirements for Deployment of Data Mining Solutions</span></span>](#bkmk_Reqs)  
  
 [<span data-ttu-id="d0dfe-112">部署关系解决方案</span><span class="sxs-lookup"><span data-stu-id="d0dfe-112">Deploying a Relational Solution</span></span>](#bkmk_RelationalSltn)  
  
 [<span data-ttu-id="d0dfe-113">部署多维解决方案</span><span class="sxs-lookup"><span data-stu-id="d0dfe-113">Deploying a Multidimensional Solution</span></span>](#bkmk_MDSltn)  
  
 [<span data-ttu-id="d0dfe-114">相关资源</span><span class="sxs-lookup"><span data-stu-id="d0dfe-114">Related Resources</span></span>](#bkmk_Resources)  
  
## <a name="in-this-section"></a><span data-ttu-id="d0dfe-115">本节内容</span><span class="sxs-lookup"><span data-stu-id="d0dfe-115">In This Section</span></span>  
 [<span data-ttu-id="d0dfe-116">将数据挖掘解决方案部署到以前版本的 SQL Server</span><span class="sxs-lookup"><span data-stu-id="d0dfe-116">Deploy a Data Mining Solution to Previous Versions of SQL Server</span></span>](deploy-a-data-mining-solution-to-previous-versions-of-sql-server.md)  
  
 [<span data-ttu-id="d0dfe-117">导出和导入数据挖掘对象</span><span class="sxs-lookup"><span data-stu-id="d0dfe-117">Export and Import Data Mining Objects</span></span>](export-and-import-data-mining-objects.md)  
  
##  <a name="requirements-for-deployment-of-data-mining-solutions"></a><a name="bkmk_Reqs"></a><span data-ttu-id="d0dfe-118">部署数据挖掘解决方案的要求</span><span class="sxs-lookup"><span data-stu-id="d0dfe-118">Requirements for Deployment of Data Mining Solutions</span></span>  
 <span data-ttu-id="d0dfe-119">要将解决方案部署到的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例必须在支持多维对象和数据挖掘对象的模式下运行；即，您不能将数据挖掘对象部署到承载表格模型或 PowerPivot 数据的实例。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-119">The instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to which you deploy the solution must be running in a mode that supports multidimensional objects and data mining objects; that is, you cannot deploy data mining objects to an instance that hosts tabular models or PowerPivot data.</span></span>  
  
 <span data-ttu-id="d0dfe-120">因此，在 Visual Studio 中创建数据挖掘解决方案时，请务必使用模板 **“Analysis Services 多维和数据挖掘项目”**。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-120">Therefore, when you create a data mining solution in Visual Studio, be sure to use the template, **Analysis Services Multidimensional and Data Mining Project**.</span></span>  
  
 <span data-ttu-id="d0dfe-121">在部署解决方案时，将在与解决方案文件同名的数据库中的指定 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例中创建用于数据挖掘的对象。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-121">When you deploy the solution, the objects used for data mining are created in the specified [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, in a database with the same name as the solution file.</span></span>  
  
###  <a name="deploying-a-relational-solution"></a><a name="bkmk_RelationalSltn"></a><span data-ttu-id="d0dfe-122">部署关系解决方案</span><span class="sxs-lookup"><span data-stu-id="d0dfe-122">Deploying a Relational Solution</span></span>  
 <span data-ttu-id="d0dfe-123">在部署关系数据挖掘解决方案时，将在新的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库中创建所需的数据挖掘对象，并且默认情况下会处理这些对象。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-123">When you deploy a relational data mining solution, the required data mining objects are created within a new [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, and the objects are processed by default.</span></span> <span data-ttu-id="d0dfe-124">可以使用配置属性 **“处理选项”** 更改处理选项。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-124">You can change processing options by using the configuration property, **Processing Option**.</span></span> <span data-ttu-id="d0dfe-125">有关详细信息，请参阅 [配置 Analysis Services 项目属性 (SSDT)](../multidimensional-models/configure-analysis-services-project-properties-ssdt.md)。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-125">For more information, see [Configure Analysis Services Project Properties &#40;SSDT&#41;](../multidimensional-models/configure-analysis-services-project-properties-ssdt.md).</span></span>  
  
 <span data-ttu-id="d0dfe-126">默认情况下，每次只部署增量更改。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-126">By default, only incremental changes are deployed each time.</span></span> <span data-ttu-id="d0dfe-127">换句话说，您可以修改一个挖掘模型，并且在您重新部署项目时，只会更新该挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-127">In other words, you can modify a mining model, and when you re-deploy the project, only that mining model would be updated.</span></span> <span data-ttu-id="d0dfe-128">但是，如果有多个客户端同时在编辑 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库，则此操作可能会导致错误。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-128">However, if you have multiple clients editing the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, this can lead to errors.</span></span> <span data-ttu-id="d0dfe-129">若要更改默认部署模式，以便在部署解决方案时刷新整个数据库，请更改 **“部署模式”** 属性。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-129">To change the default deployment mode so that the entire database is refreshed when you deploy the solution, change the **Deployment Mode** property</span></span>  
  
 <span data-ttu-id="d0dfe-130">在关系数据挖掘解决方案中，必须部署的唯一对象为数据源定义、已使用的任何数据源视图、挖掘结构和所有依赖挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-130">In a relational data mining solution, the only objects that must be deployed are the data source definition, any data source views that were used, the mining structures, and all dependent mining models.</span></span>  
  
###  <a name="deploying-a-multidimensional-solution"></a><a name="bkmk_MDSltn"></a><span data-ttu-id="d0dfe-131">部署多维解决方案</span><span class="sxs-lookup"><span data-stu-id="d0dfe-131">Deploying a Multidimensional Solution</span></span>  
 <span data-ttu-id="d0dfe-132">在部署一个多维数据挖掘解决方案时，该解决方案将在源多维数据集所在的数据库中创建数据挖掘对象。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-132">When you deploy a multidimensional data mining solution, this solution creates your data mining objects within the same database as the source cube.</span></span>  
  
 <span data-ttu-id="d0dfe-133">在处理挖掘结构或挖掘模型时，您还必须处理源多维数据集。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-133">When you process the mining structure or mining model, you must process the source cube as well.</span></span> <span data-ttu-id="d0dfe-134">为此，部署使用 OLAP 挖掘模型的解决方案所需的时间将多于部署关系数据挖掘解决方案所需的时间。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-134">For this reason, deploying a solution that uses OLAP mining models can take longer than relational data mining solutions.</span></span>  
  
 <span data-ttu-id="d0dfe-135">一般情况下，数据挖掘对象还使用对多维数据集使用的数据源和数据源视图。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-135">Typically data mining objects also use the same data sources and data source views that are used for the cube.</span></span> <span data-ttu-id="d0dfe-136">不过，您可以添加专门用于数据挖掘的数据源和数据源视图。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-136">However, you can add data sources and data source views that are targeted specifically to data mining.</span></span> <span data-ttu-id="d0dfe-137">例如，一般情况下，多维数据集将不会包含有关潜在客户端的数据，或多维对象中未使用的外部数据。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-137">For example, typically a cube would not contain data about prospective clients, or external data not used in the multidimensional objects.</span></span>  
  
##  <a name="related-resources"></a><a name="bkmk_Resources"></a><span data-ttu-id="d0dfe-138">相关资源</span><span class="sxs-lookup"><span data-stu-id="d0dfe-138">Related Resources</span></span>  
 [<span data-ttu-id="d0dfe-139">移动数据挖掘对象</span><span class="sxs-lookup"><span data-stu-id="d0dfe-139">Moving Data Mining Objects</span></span>](moving-data-mining-objects.md)  
  
 <span data-ttu-id="d0dfe-140">如果模型仅基于关系数据，则使用 DMX 导出和导入对象是移动对象的最简单方式。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-140">If your model is based on relational data only, exporting and importing objects using DMX is the easiest way to move models.</span></span>  
  
 [<span data-ttu-id="d0dfe-141">移动 Analysis Services 数据库</span><span class="sxs-lookup"><span data-stu-id="d0dfe-141">Move an Analysis Services Database</span></span>](../multidimensional-models/move-an-analysis-services-database.md)  
  
 <span data-ttu-id="d0dfe-142">当模型将多维数据集用作数据源时，请参考本主题以了解有关如何移动模型及其支持的多维数据集数据的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-142">When models use a cube as a data source, refer to this topic for more information about how to move models and their supporting cube data.</span></span>  
  
 [<span data-ttu-id="d0dfe-143">部署 Analysis Services 项目 (SSDT)</span><span class="sxs-lookup"><span data-stu-id="d0dfe-143">Deploy Analysis Services Projects &#40;SSDT&#41;</span></span>](../multidimensional-models/deploy-analysis-services-projects-ssdt.md)  
  
 <span data-ttu-id="d0dfe-144">提供有关部署 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目的常规信息，并介绍可作为项目配置的一部分设置的属性。</span><span class="sxs-lookup"><span data-stu-id="d0dfe-144">Provides general information about deployment of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projects, and describes the properties that you can set as part of the project configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0dfe-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d0dfe-145">See Also</span></span>  
 <span data-ttu-id="d0dfe-146">[多维模型对象处理](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="d0dfe-146">[Multidimensional Model Object Processing](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md) </span></span>  
 <span data-ttu-id="d0dfe-147">[数据挖掘查询接口](data-mining-query-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d0dfe-147">[Data Mining Query Interfaces](data-mining-query-tools.md) </span></span>  
 [<span data-ttu-id="d0dfe-148">处理要求和注意事项（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="d0dfe-148">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](processing-requirements-and-considerations-data-mining.md)  
  
  
