---
title: SQL Server 2014 Analysis Services |Microsoft Docs
ms.custom: ''
ms.date: 04/06/2020
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, about Analysis Services - Multidimensional Data
- SSAS
- Analysis Services
- SQL Server Analysis Services, about Analysis Services - Multidimensional Data
- SQL Server Analysis Services
- multidimensional data [Analysis Services]
- SSAS, about Analysis Services - Multidimensional Data
ms.assetid: 49d186f4-4b4d-4a5a-bb1a-e2699c64a731
author: minewiskan
ms.author: owend
ms.openlocfilehash: c111bdadefeb508897538089ecb9d9a7b583d410
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579381"
---
# <a name="sql-server-2014-analysis-services"></a><span data-ttu-id="a7725-102">SQL Server 2014 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="a7725-102">SQL Server 2014 Analysis Services</span></span>

  <span data-ttu-id="a7725-103">SQL Server 2014 Analysis Services 是在决策支持和商业智能 (BI) 解决方案中使用的分析数据引擎，它为商业报表和客户端应用程序（如 Excel、Reporting Services 报表和其他第三方 BI 工具）提供分析数据。</span><span class="sxs-lookup"><span data-stu-id="a7725-103">SQL Server 2014 Analysis Services is an analytical data engine used in decision support and business intelligence (BI) solutions, providing the analytical data for business reports and client applications such as Excel, Reporting Services reports, and other third-party BI tools.</span></span> 

## <a name="about-sql-server-analysis-services-documentation"></a><span data-ttu-id="a7725-104">关于 SQL Server Analysis Services 文档</span><span class="sxs-lookup"><span data-stu-id="a7725-104">About SQL Server Analysis Services documentation</span></span>

<span data-ttu-id="a7725-105">文档由版本分隔。</span><span class="sxs-lookup"><span data-stu-id="a7725-105">Documentation is separated by version.</span></span> <span data-ttu-id="a7725-106">目前处于 SQL Server 2014 Analysis Services 文档中。</span><span class="sxs-lookup"><span data-stu-id="a7725-106">You are currently in SQL Server 2014 Analysis Services documentation.</span></span>

- <span data-ttu-id="a7725-107">若要详细了解 SQL Server 2012 及更早版本，请参阅[SQL Server 以前版本的文档](https://docs.microsoft.com/previous-versions/sql/)。</span><span class="sxs-lookup"><span data-stu-id="a7725-107">To learn more about SQL Server 2012 and earlier, see [SQL Server previous versions documentation](https://docs.microsoft.com/previous-versions/sql/).</span></span>
- <span data-ttu-id="a7725-108">若要了解有关 SQL Server 2014 的详细信息，请参阅[SQL Server 2014 的联机丛书](../index.yml)</span><span class="sxs-lookup"><span data-stu-id="a7725-108">To learn more about SQL Server 2014, see [Books Online for SQL Server 2014](../index.yml)</span></span>
- <span data-ttu-id="a7725-109">若要详细了解 SQL Server 2016 及更高版本，请参阅[Analysis Services 文档](https://docs.microsoft.com/analysis-services/)。</span><span class="sxs-lookup"><span data-stu-id="a7725-109">To learn more about SQL Server 2016 and later, see [Analysis Services documentation](https://docs.microsoft.com/analysis-services/).</span></span>
- <span data-ttu-id="a7725-110">若要详细了解 Azure Analysis Services，请参阅[Azure Analysis Services 文档](https://docs.microsoft.com/azure/analysis-services/)。</span><span class="sxs-lookup"><span data-stu-id="a7725-110">To learn more about Azure Analysis Services, see [Azure Analysis Services Documentation](https://docs.microsoft.com/azure/analysis-services/).</span></span>

## <a name="analysis-services-workflow"></a><span data-ttu-id="a7725-111">Analysis Services 工作流</span><span class="sxs-lookup"><span data-stu-id="a7725-111">Analysis Services workflow</span></span>

<span data-ttu-id="a7725-112">典型工作流包括生成 OLAP 或表格数据模型、将模型作为数据库部署到服务器实例、处理数据库以便使用数据进行加载，然后分配权限以允许数据访问。</span><span class="sxs-lookup"><span data-stu-id="a7725-112">A typical workflow includes building an OLAP or tabular data model, deploy the model as a database to a server instance, process the database to load it with data, and then assign permissions to allow data access.</span></span> <span data-ttu-id="a7725-113">所有工作完成后，任何将 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 作为数据源进行支持的客户端应用程序均可访问此多用途数据模型。</span><span class="sxs-lookup"><span data-stu-id="a7725-113">When it's ready to go, this multi-purpose data model can be accessed by any client application supporting [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] as a data source.</span></span>  
  
 <span data-ttu-id="a7725-114">若要创建模型，请使用 SQL Server Data Tools (请参阅[Analysis Services) 中使用的工具和应用程序](tools-and-applications-used-in-analysis-services.md)，并选择表格或多维和数据挖掘项目模板。</span><span class="sxs-lookup"><span data-stu-id="a7725-114">To create a model, use SQL Server Data Tools (see [Tools and applications used in Analysis Services](tools-and-applications-used-in-analysis-services.md)), choosing either a Tabular or Multidimensional and Data Mining project template.</span></span> <span data-ttu-id="a7725-115">项目模板包含在模型中所需的所有对象的文件夹。</span><span class="sxs-lookup"><span data-stu-id="a7725-115">The project template contains folders for all of the objects needed in a model.</span></span> <span data-ttu-id="a7725-116">你可以使用向导来创建所有基本元素，如数据源、数据源视图、维度、多维数据集和角色。</span><span class="sxs-lookup"><span data-stu-id="a7725-116">You can use wizards to create all of the basic elements, such as data sources, data source views, dimensions, cubes, and roles.</span></span>  
  
 <span data-ttu-id="a7725-117">模型由外部数据系统中的数据填充，通常是承载于 SQL Server 或 Oracle 关系数据库引擎中承载的数据仓库（表格模型支持其他数据源类型）。</span><span class="sxs-lookup"><span data-stu-id="a7725-117">Models are populated with data from external data systems, usually data warehouses hosted on a SQL Server or Oracle relational database engine (Tabular models support additional data source types).</span></span> <span data-ttu-id="a7725-118">模型可指定查询对象（如多维数据集），也可以指定用于多个多维数据集、计算和 KPI（封装业务逻辑）和交互（如导航和钻取行为）的维度。</span><span class="sxs-lookup"><span data-stu-id="a7725-118">Models specify query objects, such as cubes, but also specify dimensions that can be used in multiple cubes, calculations and KPIs that encapsulate business logic, and interactions such as navigation and drill-through behaviors.</span></span>  
  
 <span data-ttu-id="a7725-119">若要使用模型，则将其部署到在特定服务器模式下运行数据库的服务器实例，使数据可供通过 Excel 或其他应用程序进行连接的授权用户使用。</span><span class="sxs-lookup"><span data-stu-id="a7725-119">To use a model, it's deployed to a server instance that runs databases in a particular server mode, making the data available to authorized users who connect through Excel or other applications.</span></span>  
  
 <span data-ttu-id="a7725-120">可以在以下三种服务器模式之一中安装实例：</span><span class="sxs-lookup"><span data-stu-id="a7725-120">You can install an instance in one of three server modes:</span></span>  
  
-   <span data-ttu-id="a7725-121">作为表格实例，并运行表格模型。</span><span class="sxs-lookup"><span data-stu-id="a7725-121">As a Tabular instance, running Tabular models.</span></span>  
  
-   <span data-ttu-id="a7725-122">作为多维和数据挖掘实例，并运行 OLAP 多维数据集和数据挖掘模型（这是默认值）。</span><span class="sxs-lookup"><span data-stu-id="a7725-122">As a Multidimensional and Data Mining instance, running OLAP cubes and data mining models (this is the default).</span></span>  
  
-   <span data-ttu-id="a7725-123">作为 PowerPivot for SharePoint，并在 SharePoint 中运行 PowerPivot 和 Excel 数据模型（PowerPivot for SharePoint 是加载、查询和刷新 SharePoint 中承载的数据模型的中间层数据引擎）。</span><span class="sxs-lookup"><span data-stu-id="a7725-123">As PowerPivot for SharePoint, running PowerPivot and Excel data models in SharePoint (PowerPivot for SharePoint is a middle-tier data engine that loads, queries, and refreshes data models hosted in SharePoint).</span></span>  
  
 <span data-ttu-id="a7725-124">相同的数据引擎；使用数据引擎的三种不同方法。</span><span class="sxs-lookup"><span data-stu-id="a7725-124">Same data engine; three different ways to use it.</span></span> <span data-ttu-id="a7725-125">请注意，服务器模式在安装期间设置且以后无法更改。</span><span class="sxs-lookup"><span data-stu-id="a7725-125">Note that server modes are set during installation and cannot be changed later.</span></span> <span data-ttu-id="a7725-126">如果您需要其他模式，则应安装新实例。</span><span class="sxs-lookup"><span data-stu-id="a7725-126">You should install a new instance if you require a different mode.</span></span>  
  
 <span data-ttu-id="a7725-127">针对 Analysis Services 的基础文档划分为多节，每一节都与您生成的项目类型相对应。</span><span class="sxs-lookup"><span data-stu-id="a7725-127">Foundational documentation for Analysis Services is organized into sections that correspond to the type of project you are building.</span></span> <span data-ttu-id="a7725-128">从以下链接中进行选择，以了解每种模式或功能范围的详情。</span><span class="sxs-lookup"><span data-stu-id="a7725-128">Choose from the following links to learn more about each mode or feature area.</span></span>  
  
 <span data-ttu-id="a7725-129">**按区域浏览内容**</span><span class="sxs-lookup"><span data-stu-id="a7725-129">**Browse Content by Area**</span></span>  
 <span data-ttu-id="a7725-130">用于[比较表格和多维解决方案 &#40;SSAS&#41;的](comparing-tabular-and-multidimensional-solutions-ssas.md)![小文件文件夹图标](../../2014/integration-services/media/filefolder-small.gif "小文件文件夹图标")</span><span class="sxs-lookup"><span data-stu-id="a7725-130">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Comparing Tabular and Multidimensional Solutions &#40;SSAS&#41;](comparing-tabular-and-multidimensional-solutions-ssas.md)</span></span>  
  
 <span data-ttu-id="a7725-131">![小文件文件夹图标](../../2014/integration-services/media/filefolder-small.gif "小文件文件夹图标") [Analysis Services 实例管理](instances/analysis-services-instance-management.md)</span><span class="sxs-lookup"><span data-stu-id="a7725-131">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Analysis Services Instance Management](instances/analysis-services-instance-management.md)</span></span>  
  
 <span data-ttu-id="a7725-132">![小文件文件夹图标](../../2014/integration-services/media/filefolder-small.gif "小文件文件夹图标") [&#40;SSAS 表格的表格建模&#41;](tabular-models/tabular-models-ssas.md)</span><span class="sxs-lookup"><span data-stu-id="a7725-132">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Tabular Modeling &#40;SSAS Tabular&#41;](tabular-models/tabular-models-ssas.md)</span></span>  
  
 <span data-ttu-id="a7725-133">![小文件文件夹图标](../../2014/integration-services/media/filefolder-small.gif "小文件文件夹图标")[多维建模 &#40;SSAS&#41;](multidimensional-models/multidimensional-models-ssas.md)</span><span class="sxs-lookup"><span data-stu-id="a7725-133">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Multidimensional Modeling &#40;SSAS&#41;](multidimensional-models/multidimensional-models-ssas.md)</span></span>  
  
 <span data-ttu-id="a7725-134">![小文件文件夹图标](../../2014/integration-services/media/filefolder-small.gif "小文件文件夹图标")[数据挖掘 &#40;SSAS&#41;](data-mining/data-mining-ssas.md)</span><span class="sxs-lookup"><span data-stu-id="a7725-134">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Data Mining &#40;SSAS&#41;](data-mining/data-mining-ssas.md)</span></span>  
  
 <span data-ttu-id="a7725-135">[&#40;SSAS PowerPivot for SharePoint](power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)的![小文件文件夹图标](../../2014/integration-services/media/filefolder-small.gif "小文件文件夹图标")&#41;</span><span class="sxs-lookup"><span data-stu-id="a7725-135">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [PowerPivot for SharePoint &#40;SSAS&#41;](power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="a7725-136">功能因版本而异。</span><span class="sxs-lookup"><span data-stu-id="a7725-136">features vary by edition.</span></span> <span data-ttu-id="a7725-137">多维和数据挖掘模型在标准版本中可用，但其功能少于更高版本。</span><span class="sxs-lookup"><span data-stu-id="a7725-137">Multidimensional and data mining models are available in standard edition, but with fewer features than higher editions.</span></span> <span data-ttu-id="a7725-138">表格模型和 PowerPivot for SharePoint 是高级功能，且在标准版本许可证中不可用。</span><span class="sxs-lookup"><span data-stu-id="a7725-138">Tabular models and PowerPivot for SharePoint are premium features and are not available in a standard edition license.</span></span> <span data-ttu-id="a7725-139">有关详细信息，请参阅 [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="a7725-139">For more information, see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7725-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a7725-140">See Also</span></span>  
 <span data-ttu-id="a7725-141">[SSAS&#41;Analysis Services 教程 &#40;](analysis-services-tutorials-ssas.md) </span><span class="sxs-lookup"><span data-stu-id="a7725-141">[Analysis Services Tutorials &#40;SSAS&#41;](analysis-services-tutorials-ssas.md) </span></span>  
 <span data-ttu-id="a7725-142">[安装 SQL Server 2014](../database-engine/install-windows/installation-for-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a7725-142">[Installation for SQL Server 2014](../database-engine/install-windows/installation-for-sql-server.md) </span></span>  
 <span data-ttu-id="a7725-143">[开发人员指南 &#40;Analysis Services&#41;](analysis-services-developer-documentation.md) </span><span class="sxs-lookup"><span data-stu-id="a7725-143">[Developer's Guide &#40;Analysis Services&#41;](analysis-services-developer-documentation.md) </span></span>  
 <span data-ttu-id="a7725-144">[SQL Server 资源中心](https://go.microsoft.com/fwlink/?linkID=219676) </span><span class="sxs-lookup"><span data-stu-id="a7725-144">[SQL Server Resource Center](https://go.microsoft.com/fwlink/?linkID=219676) </span></span>  
 [<span data-ttu-id="a7725-145">SQLCat.com</span><span class="sxs-lookup"><span data-stu-id="a7725-145">SQLCat.com</span></span>](https://go.microsoft.com/fwlink/?linkID=220963)  
  
  
