---
title: 多维模型中的数据源 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- metadata [Analysis Services]
- Analysis Services objects, data sources
- storing data [Analysis Services], data sources
- data sources [Analysis Services], about data sources
- security [Analysis Services], data sources
- data sources [Analysis Services]
- storage [Analysis Services], data sources
ms.assetid: a16469d9-9d53-4e35-9982-fc06327a9d33
author: minewiskan
ms.author: owend
ms.openlocfilehash: 41386c1c7abb0324aa17df24b3c427ca8cbb5615
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589926"
---
# <a name="data-sources-in-multidimensional-models"></a><span data-ttu-id="5e39e-102">多维模型中的数据源</span><span class="sxs-lookup"><span data-stu-id="5e39e-102">Data Sources in Multidimensional Models</span></span>
  <span data-ttu-id="5e39e-103">您导入或加载到多维模型中的所有数据都来自外部数据源。</span><span class="sxs-lookup"><span data-stu-id="5e39e-103">All data that you import or load into a multidimensional model originates from an external data source.</span></span> <span data-ttu-id="5e39e-104">通常源数据来自用于报告目的数据仓库，但它也可以来自可直接访问或通过媒介（如 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包）间接访问的任意关系数据库。</span><span class="sxs-lookup"><span data-stu-id="5e39e-104">Typically, source data is from a data warehouse designed for reporting purposes, but it could come from any relational database that is accessed directly or indirectly through an intermediary, such as an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package.</span></span>  
  
 <span data-ttu-id="5e39e-105">**中的** “数据源” [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 对象指定与外部数据源的直接连接。</span><span class="sxs-lookup"><span data-stu-id="5e39e-105">A **data source** object in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] specifies a direct connection to an external data source.</span></span> <span data-ttu-id="5e39e-106">除了物理位置之外，数据源对象还指定连接字符串、数据访问接口、凭据和控制连接行为的其他属性。</span><span class="sxs-lookup"><span data-stu-id="5e39e-106">In addition to physical location, a data source object specifies the connection string, data provider, credentials, and other properties that control connection behavior.</span></span>  
  
 <span data-ttu-id="5e39e-107">在下列操作期间使用数据源对象提供的信息：</span><span class="sxs-lookup"><span data-stu-id="5e39e-107">Information provided by the data source object is used during the following operations:</span></span>  
  
-   <span data-ttu-id="5e39e-108">将架构信息和用于生成数据源视图的其他元数据提供给模型。</span><span class="sxs-lookup"><span data-stu-id="5e39e-108">Get schema information and other metadata used to generate data source views into a model.</span></span>  
  
-   <span data-ttu-id="5e39e-109">在处理期间查询或将数据加载到模型。</span><span class="sxs-lookup"><span data-stu-id="5e39e-109">Query or load data into a model during processing.</span></span>  
  
-   <span data-ttu-id="5e39e-110">对使用 ROLAP 存储模式的多维模型或数据挖掘模型运行查询。</span><span class="sxs-lookup"><span data-stu-id="5e39e-110">Run queries against multidimensional or data mining models that use ROLAP storage mode.</span></span>  
  
-   <span data-ttu-id="5e39e-111">读取或写入到远程分区。</span><span class="sxs-lookup"><span data-stu-id="5e39e-111">Read or write to remote partitions.</span></span>  
  
-   <span data-ttu-id="5e39e-112">连接到链接对象，以及从目标同步到源。</span><span class="sxs-lookup"><span data-stu-id="5e39e-112">Connect to linked objects, as well as synchronize from target to source.</span></span>  
  
-   <span data-ttu-id="5e39e-113">执行更新存储在关系数据库中的事实数据表数据的写回操作。</span><span class="sxs-lookup"><span data-stu-id="5e39e-113">Perform write back operations that update fact table data stored in a relational database.</span></span>  
  
 <span data-ttu-id="5e39e-114">在从头开始生成一个多维模型时，可通过创建数据源对象来开始，然后使用该对象生成下一个对象，即 **“数据源视图”**。</span><span class="sxs-lookup"><span data-stu-id="5e39e-114">When building a multidimensional model from the bottom up, you start by creating the data source object, and then use it to generate the next object, a **data source view**.</span></span> <span data-ttu-id="5e39e-115">数据源视图是模型中的数据抽象层。</span><span class="sxs-lookup"><span data-stu-id="5e39e-115">A data source view is the data abstraction layer in the model.</span></span> <span data-ttu-id="5e39e-116">它通常在数据源对象之后创建，并且使用源数据库的架构作为基础。</span><span class="sxs-lookup"><span data-stu-id="5e39e-116">It is typically created after the data source object, using the schema of the source database as the basis.</span></span> <span data-ttu-id="5e39e-117">不过，您可以选择其他方法来生成模型，包括从多维数据集和维度开始，并且生成最好地支持您的设计的架构。</span><span class="sxs-lookup"><span data-stu-id="5e39e-117">However, you can choose other ways to build a model, including starting with cubes and dimensions, and generating the schema that best supports your design.</span></span>  
  
 <span data-ttu-id="5e39e-118">无论您是以何种方式来生成模型的，每个模型都要求至少一个数据源对象，该对象指定与源数据的连接。</span><span class="sxs-lookup"><span data-stu-id="5e39e-118">Regardless of how you build it, each model requires at least one data source object that specifies a connection to source data.</span></span> <span data-ttu-id="5e39e-119">您可以在单个模型中创建多个数据源对象，以便使用来自不同源的数据或者针对特定对象改变连接属性。</span><span class="sxs-lookup"><span data-stu-id="5e39e-119">You can create multiple data source objects in a single model to use data from different sources or vary connection properties for specific objects.</span></span>  
  
 <span data-ttu-id="5e39e-120">可独立于您的模型中的其他对象来管理数据源对象。</span><span class="sxs-lookup"><span data-stu-id="5e39e-120">Data source objects can be managed independently of other objects in your model.</span></span> <span data-ttu-id="5e39e-121">创建一个数据源后，可在以后更改其属性，然后对模型进行预处理以确保正确地检索数据。</span><span class="sxs-lookup"><span data-stu-id="5e39e-121">After you create a data source, you can change its properties later, and then preprocess the model to ensure the data is retrieved correctly.</span></span>  
  
## <a name="related-topics-and-tasks"></a><span data-ttu-id="5e39e-122">相关主题和任务</span><span class="sxs-lookup"><span data-stu-id="5e39e-122">Related Topics and Tasks</span></span>  
  
|<span data-ttu-id="5e39e-123">主题</span><span class="sxs-lookup"><span data-stu-id="5e39e-123">Topic</span></span>|<span data-ttu-id="5e39e-124">说明</span><span class="sxs-lookup"><span data-stu-id="5e39e-124">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5e39e-125">支持 &#40;SSAS 多维&#41;的数据源</span><span class="sxs-lookup"><span data-stu-id="5e39e-125">Data Sources Supported &#40;SSAS Multidimensional&#41;</span></span>](supported-data-sources-ssas-multidimensional.md)|<span data-ttu-id="5e39e-126">介绍可以在多维模型中使用的数据源的类型。</span><span class="sxs-lookup"><span data-stu-id="5e39e-126">Describes the types of data sources that can be used in a multidimensional model.</span></span>|  
|[<span data-ttu-id="5e39e-127">创建数据源（SSAS 多维）</span><span class="sxs-lookup"><span data-stu-id="5e39e-127">Create a Data Source &#40;SSAS Multidimensional&#41;</span></span>](create-a-data-source-ssas-multidimensional.md)|<span data-ttu-id="5e39e-128">说明如何将数据源对象添加到多维模型。</span><span class="sxs-lookup"><span data-stu-id="5e39e-128">Explains how to add a data source object to a multidimensional model.</span></span>|  
|[<span data-ttu-id="5e39e-129">在解决方案资源管理器中删除数据源（SSAS 多维）</span><span class="sxs-lookup"><span data-stu-id="5e39e-129">Delete a Data Source in Solution Explorer &#40;SSAS Multidimensional&#41;</span></span>](delete-a-data-source-in-solution-explorer-ssas-multidimensional.md)|<span data-ttu-id="5e39e-130">使用此过程可从多维模型中删除数据源对象。</span><span class="sxs-lookup"><span data-stu-id="5e39e-130">Use this procedure to delete a data source object from a multidimensional model.</span></span>|  
|[<span data-ttu-id="5e39e-131">设置数据源属性（SSAS 多维）</span><span class="sxs-lookup"><span data-stu-id="5e39e-131">Set Data Source Properties &#40;SSAS Multidimensional&#41;</span></span>](set-data-source-properties-ssas-multidimensional.md)|<span data-ttu-id="5e39e-132">描述每个属性，并说明如何设置每个属性。</span><span class="sxs-lookup"><span data-stu-id="5e39e-132">Describes each property and explains how to set each one.</span></span>|  
|[<span data-ttu-id="5e39e-133">设置模拟选项（SSAS - 多维）</span><span class="sxs-lookup"><span data-stu-id="5e39e-133">Set Impersonation Options &#40;SSAS - Multidimensional&#41;</span></span>](set-impersonation-options-ssas-multidimensional.md)|<span data-ttu-id="5e39e-134">说明如何在“模拟信息”对话框中配置选项。</span><span class="sxs-lookup"><span data-stu-id="5e39e-134">Explains how to configure options in the Impersonation Information dialog box.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5e39e-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5e39e-135">See Also</span></span>  
 <span data-ttu-id="5e39e-136">[Analysis Services 多维数据 &#40;的数据库对象&#41;](olap-logical/database-objects-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="5e39e-136">[Database Objects &#40;Analysis Services - Multidimensional Data&#41;](olap-logical/database-objects-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="5e39e-137">[逻辑体系结构 &#40;Analysis Services 多维数据&#41;](olap-logical/understanding-microsoft-olap-logical-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="5e39e-137">[Logical Architecture &#40;Analysis Services - Multidimensional Data&#41;](olap-logical/understanding-microsoft-olap-logical-architecture.md) </span></span>  
 <span data-ttu-id="5e39e-138">[多维模型中的数据源视图](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="5e39e-138">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="5e39e-139">数据源和绑定（SSAS 多维）</span><span class="sxs-lookup"><span data-stu-id="5e39e-139">Data Sources and Bindings &#40;SSAS Multidimensional&#41;</span></span>](data-sources-and-bindings-ssas-multidimensional.md)  
  
  
