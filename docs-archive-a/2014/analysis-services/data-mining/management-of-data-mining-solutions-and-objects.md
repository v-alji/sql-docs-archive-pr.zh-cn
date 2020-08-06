---
title: 管理数据挖掘解决方案和对象 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], managing
- managing mining models
ms.assetid: 06fc61dd-925c-4347-8677-7046ee5d2f6f
author: minewiskan
ms.author: owend
ms.openlocfilehash: ae3e672932dd320c6b369f23f03c1f056d30d4ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577093"
---
# <a name="management-of-data-mining-solutions-and-objects"></a><span data-ttu-id="56f15-102">管理数据挖掘解决方案和对象</span><span class="sxs-lookup"><span data-stu-id="56f15-102">Management of Data Mining Solutions and Objects</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="56f15-103">提供可用于管理现有挖掘结构和挖掘模型的客户端工具。</span><span class="sxs-lookup"><span data-stu-id="56f15-103">provides client tools that you can use to manage existing mining structures and mining models.</span></span> <span data-ttu-id="56f15-104">本节介绍使用每种环境可以执行的管理操作。</span><span class="sxs-lookup"><span data-stu-id="56f15-104">This section describes the management operations that you can perform using each environment.</span></span>  
  
 <span data-ttu-id="56f15-105">除了这些工具之外，还可以使用 AMO 以编程方式管理数据挖掘对象，或使用连接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库的其他客户端，如 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007 的数据挖掘外接程序。</span><span class="sxs-lookup"><span data-stu-id="56f15-105">In addition to these tools, you can manage data mining objects programmatically, by using AMO, or use other clients that connect to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, such as the Data Mining Add-ins for [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="56f15-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="56f15-106">In this Section</span></span>  
 [<span data-ttu-id="56f15-107">移动数据挖掘对象</span><span class="sxs-lookup"><span data-stu-id="56f15-107">Moving Data Mining Objects</span></span>](moving-data-mining-objects.md)  
  
 [<span data-ttu-id="56f15-108">处理要求和注意事项（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="56f15-108">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](processing-requirements-and-considerations-data-mining.md)  
  
 [<span data-ttu-id="56f15-109">使用 SQL Server 事件探查器监视数据挖掘（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="56f15-109">Using SQL Server Profiler to Monitor Data Mining &#40;Analysis Services - Data Mining&#41;</span></span>](using-sql-server-profiler-to-monitor-data-mining-analysis-services-data-mining.md)  
  
## <a name="location-of-data-mining-objects"></a><span data-ttu-id="56f15-110">数据挖掘对象的位置</span><span class="sxs-lookup"><span data-stu-id="56f15-110">Location of Data Mining Objects</span></span>  
 <span data-ttu-id="56f15-111">已处理的挖掘结构和挖掘模型通常存储在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的实例中。</span><span class="sxs-lookup"><span data-stu-id="56f15-111">Mining structures and models that have been processed are stored in an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="56f15-112">如果在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] `Immediate` 开发数据挖掘对象时在模式下创建了与数据库的连接，则在工作时，所创建的任何对象都会立即添加到服务器中。</span><span class="sxs-lookup"><span data-stu-id="56f15-112">If you create a connection to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in `Immediate` mode when developing your data mining objects, any objects that you create are immediately added to the server as you work.</span></span> <span data-ttu-id="56f15-113">但是，如果在 **“脱机”** 模式下设计数据挖掘对象，这也是在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中工作时的默认设置，则您创建的挖掘对象在部署到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]实例之前只是一些元数据容器。</span><span class="sxs-lookup"><span data-stu-id="56f15-113">However, if you design data mining objects in **Offline** mode, which is the default when you work in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], the mining objects that you create are only metadata containers until you deploy them to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="56f15-114">因此，无论任何时候，只要对对象进行了更改，则就必须将对象重新部署到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="56f15-114">Therefore, any time that you make a change to an object, you must redeploy the object to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server.</span></span> <span data-ttu-id="56f15-115">有关数据挖掘体系结构的详细信息，请参阅[物理体系结构（Analysis Services - 数据挖掘）](physical-architecture-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="56f15-115">For more information about data mining architecture, see [Physical Architecture &#40;Analysis Services - Data Mining&#41;](physical-architecture-analysis-services-data-mining.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="56f15-116">诸如 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007 数据挖掘外接程序之类的客户端还可用于创建会话挖掘模型和挖掘结构，它们使用到实例的连接，但只在会话期间在服务器中存储挖掘结构和挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="56f15-116">Some clients, such as the Data Mining Add-ins for [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007, also let you create session mining models and mining structures, which use a connection to an instance but store the mining structure and models on the server only for the duration of the session.</span></span> <span data-ttu-id="56f15-117">您仍然可以通过客户端管理这些模型，就如同管理 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库中存储的结构和模型一样，但断开与 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]实例的连接后，不会持久化这些对象。</span><span class="sxs-lookup"><span data-stu-id="56f15-117">You can still manage these models through the client, the same as you would structures and models stored in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, but the objects are not persisted after you disconnect from the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="managing-data-mining-objects-in-sql-server-data-tools"></a><span data-ttu-id="56f15-118">在 SQL Server Data Tools 中管理数据挖掘对象</span><span class="sxs-lookup"><span data-stu-id="56f15-118">Managing Data Mining Objects in SQL Server Data Tools</span></span>  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="56f15-119">提供便于创建、浏览和编辑数据挖掘对象的功能。</span><span class="sxs-lookup"><span data-stu-id="56f15-119">offers features that make it easy to create, browse, and edit data mining objects.</span></span>  
  
 <span data-ttu-id="56f15-120">以下链接提供有关如何使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]修改数据挖掘对象的信息：</span><span class="sxs-lookup"><span data-stu-id="56f15-120">The following links provide information on how you can modify data mining objects by using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]:</span></span>  
  
-   [<span data-ttu-id="56f15-121">编辑用于挖掘结构的数据源视图</span><span class="sxs-lookup"><span data-stu-id="56f15-121">Edit the Data Source View used for a Mining Structure</span></span>](edit-the-data-source-view-used-for-a-mining-structure.md)  
  
-   [<span data-ttu-id="56f15-122">更改挖掘结构的属性</span><span class="sxs-lookup"><span data-stu-id="56f15-122">Change the Properties of a Mining Structure</span></span>](change-the-properties-of-a-mining-structure.md)  
  
-   [<span data-ttu-id="56f15-123">更改挖掘模型的属性</span><span class="sxs-lookup"><span data-stu-id="56f15-123">Change the Properties of a Mining Model</span></span>](change-the-properties-of-a-mining-model.md)  
  
-   [<span data-ttu-id="56f15-124">查看或更改建模标志（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="56f15-124">View or Change Modeling Flags &#40;Data Mining&#41;</span></span>](modeling-flags-data-mining.md)  
  
-   [<span data-ttu-id="56f15-125">查看或更改算法参数</span><span class="sxs-lookup"><span data-stu-id="56f15-125">View or Change Algorithm Parameters</span></span>](view-or-change-algorithm-parameters.md)  
  
 <span data-ttu-id="56f15-126">通常，您将使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 作为工具来开发新项目和添加到现有项目，然后管理已使用诸如 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的工具进行部署的项目和对象。</span><span class="sxs-lookup"><span data-stu-id="56f15-126">Typically you will use [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] as a tool for developing new projects and adding to existing projects, and then manage projects and objects that have been deployed by using tools such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="56f15-127">但是，您可以使用 `Immediate` 选项并在联机模式下连接到 ssASnoversion 实例，直接修改已部署到该服务器的对象。</span><span class="sxs-lookup"><span data-stu-id="56f15-127">However, you can directly modify objects that are already deployed to an instance of ssASnoversion by using the `Immediate` option and connecting to the server in Online mode.</span></span> <span data-ttu-id="56f15-128">有关详细信息，请参阅 [Connect in Online Mode to an Analysis Services Database](../multidimensional-models/connect-in-online-mode-to-an-analysis-services-database.md)。</span><span class="sxs-lookup"><span data-stu-id="56f15-128">For more information, see [Connect in Online Mode to an Analysis Services Database](../multidimensional-models/connect-in-online-mode-to-an-analysis-services-database.md).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="56f15-129">所有对挖掘结构或挖掘模型的更改，包括对元数据（如名称或说明）的更改，都要求重新处理结构或模型。</span><span class="sxs-lookup"><span data-stu-id="56f15-129">All changes to a mining structure or mining model, including changes to metadata such as a name or description, require that the structure or model be reprocessed.</span></span>  
  
 <span data-ttu-id="56f15-130">如果您没有用于创建数据挖掘项目或对象的解决方案文件，则可以使用 Analysis Services 导入向导从服务器导入现有项目，对该对象进行修改，然后使用 `Incremental` 选项重新进行部署。</span><span class="sxs-lookup"><span data-stu-id="56f15-130">If you do not have the solution file that was used to create the data mining project or objects, you can import the existing project from the server using the Analysis Services Import wizard, make modifications to the objects, and then redeploy using the `Incremental` option.</span></span> <span data-ttu-id="56f15-131">有关详细信息，请参阅 [使用 Analysis Services 导入向导导入数据挖掘项目](import-a-data-mining-project-using-the-analysis-services-import-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="56f15-131">For more information, see [Import a Data Mining Project using the Analysis Services Import Wizard](import-a-data-mining-project-using-the-analysis-services-import-wizard.md).</span></span>  
  
## <a name="managing-data-mining-objects-in-sql-server-management-studio"></a><span data-ttu-id="56f15-132">在 SQL Server Management Studio 中管理数据挖掘对象</span><span class="sxs-lookup"><span data-stu-id="56f15-132">Managing Data Mining Objects in SQL Server Management Studio</span></span>  
 <span data-ttu-id="56f15-133">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，可以编写挖掘结构和挖掘模型的脚本、处理或删除挖掘结构和挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="56f15-133">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can script, process, or delete mining structures and mining models.</span></span> <span data-ttu-id="56f15-134">使用对象资源管理器仅可以查看有限的一组属性；但是，您可以通过打开 **“DMX 查询”** 窗口并选择挖掘结构，以查看有关挖掘模型的其他元数据。</span><span class="sxs-lookup"><span data-stu-id="56f15-134">You can view only a limited set of properties by using Object Explorer; however, you can view additional metadata about mining models by opening a **DMX Query** window and selecting a mining structure.</span></span>  
  
-   [<span data-ttu-id="56f15-135">在 SQL Server Management Studio 中创建一个 DMX 查询</span><span class="sxs-lookup"><span data-stu-id="56f15-135">Create a DMX Query in SQL Server Management Studio</span></span>](create-a-dmx-query-in-sql-server-management-studio.md)  
  
## <a name="managing-data-mining-objects-programmatically"></a><span data-ttu-id="56f15-136">以编程方式管理数据挖掘对象</span><span class="sxs-lookup"><span data-stu-id="56f15-136">Managing Data Mining Objects Programmatically</span></span>  
 <span data-ttu-id="56f15-137">使用以下编程语言可创建、更改、处理和删除数据挖掘对象。</span><span class="sxs-lookup"><span data-stu-id="56f15-137">You can create, alter, process, and delete data mining objects by using the following programming languages.</span></span> <span data-ttu-id="56f15-138">每种语言都是针对不同任务设计的，因此，对您可执行的操作类型可能有一些限制。</span><span class="sxs-lookup"><span data-stu-id="56f15-138">Each language is designed for different tasks and as a result, there might be restrictions on the type of operations that you can perform.</span></span> <span data-ttu-id="56f15-139">例如，数据挖掘对象的某些属性不能通过使用数据挖掘扩展插件 (DMX) 进行更改，而必须使用 XMLA 或 AMO。</span><span class="sxs-lookup"><span data-stu-id="56f15-139">For example, some properties of data mining objects cannot be changed by using Data Mining Extensions (DMX); you must use XMLA or AMO.</span></span>  
  
### <a name="analysis-management-objects-amo"></a><span data-ttu-id="56f15-140">分析管理对象 (AMO)</span><span class="sxs-lookup"><span data-stu-id="56f15-140">Analysis Management Objects (AMO)</span></span>  
 <span data-ttu-id="56f15-141">Analysis Management Objects (AMO) 是一个构建在 XMLA 之上的对象模型，它使您可以完全控制数据挖掘对象。</span><span class="sxs-lookup"><span data-stu-id="56f15-141">Analysis Management Objects (AMO) is an object model built on top of XMLA that gives you full control over data mining objects.</span></span> <span data-ttu-id="56f15-142">通过使用 AMO，您可以创建、部署和监视挖掘结构和挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="56f15-142">By using AMO, you can create, deploy, and monitor mining structures and mining models</span></span>  
  
-   [<span data-ttu-id="56f15-143">AMO 概念和对象模型</span><span class="sxs-lookup"><span data-stu-id="56f15-143">AMO Concepts and Object Model</span></span>](https://docs.microsoft.com/bi-reference/amo/amo-concepts-and-object-model)  
  
-   <xref:Microsoft.AnalysisServices>  
  
 <span data-ttu-id="56f15-144">**限制：** 无。</span><span class="sxs-lookup"><span data-stu-id="56f15-144">**Restrictions:** None.</span></span>  
  
### <a name="data-mining-extensions-dmx"></a><span data-ttu-id="56f15-145">数据挖掘扩展插件 (DMX)</span><span class="sxs-lookup"><span data-stu-id="56f15-145">Data Mining Extensions (DMX)</span></span>  
 <span data-ttu-id="56f15-146">数据挖掘扩展插件 (DMX) 可以与其他命令接口（如 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 或 ADOMD.Net）配合使用来创建、删除和查询挖掘结构和挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="56f15-146">Data Mining Extensions (DMX) can be used with other command interfaces such as [!INCLUDE[vstecado](../../includes/vstecado-md.md)] or ADOMD.Net to create, delete, and query mining structures and mining models.</span></span>  
  
-   [<span data-ttu-id="56f15-147">数据挖掘扩展插件 (DMX) 数据定义语句</span><span class="sxs-lookup"><span data-stu-id="56f15-147">Data Mining Extensions &#40;DMX&#41; Data Definition Statements</span></span>](/sql/dmx/dmx-statements-data-definition)  
  
 <span data-ttu-id="56f15-148">**限制：** 使用 DMX 无法更改某些属性。</span><span class="sxs-lookup"><span data-stu-id="56f15-148">**Restrictions:** Some properties cannot be changed by using DMX.</span></span>  
  
### <a name="xml-for-analysis-xmla"></a><span data-ttu-id="56f15-149">XML for Analysis (XMLA)</span><span class="sxs-lookup"><span data-stu-id="56f15-149">XML for Analysis (XMLA)</span></span>  
 <span data-ttu-id="56f15-150">XML for Analysis (XMLA) 是用于所有 Analysis Services 的数据定义语言。</span><span class="sxs-lookup"><span data-stu-id="56f15-150">XML for Analysis (XMLA) is the data definition language for all of Analysis Services.</span></span> <span data-ttu-id="56f15-151">XMLA 使您可以控制大多数数据挖掘对象和服务器操作。</span><span class="sxs-lookup"><span data-stu-id="56f15-151">XMLA gives you control over most data mining objects and server operations.</span></span> <span data-ttu-id="56f15-152">客户端和服务器之间的所有管理操作都可通过使用 XMLA 来执行。</span><span class="sxs-lookup"><span data-stu-id="56f15-152">All management operations between the client and the server can be performed by using XMLA.</span></span> <span data-ttu-id="56f15-153">为了方便，可以使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 脚本语言 (ASSL) 对 XML 进行换行。</span><span class="sxs-lookup"><span data-stu-id="56f15-153">For convenience, you can use the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language (ASSL) to wrap the XML.</span></span>  
  
 <span data-ttu-id="56f15-154">**限制：** [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 生成的某些 XMLA 语句仅支持在内部使用，而不能在 XML DDL 脚本中使用。</span><span class="sxs-lookup"><span data-stu-id="56f15-154">**Restrictions:** [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] generates some XMLA statements that are supported for internal use only, and cannot be used in XML DDL scripts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56f15-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="56f15-155">See Also</span></span>  
 [<span data-ttu-id="56f15-156">开发人员指南 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="56f15-156">Developer's Guide &#40;Analysis Services&#41;</span></span>](../analysis-services-developer-documentation.md)  
  
  
