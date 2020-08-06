---
title: 在多维和数据挖掘模式下安装 Analysis Services |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Analysis Services, about installing Analysis Services
- installing Analysis Services
- SSAS, installing
- Analysis Services, installing
- SQL Server Analysis Services, installing
ms.assetid: 8a1f33e8-2bd6-4fb8-bd46-c86f2a067f60
author: heidisteen
ms.author: heidist
ms.openlocfilehash: e88d4440a65392b4f6351fa2503ea7819cf528b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578024"
---
# <a name="install-analysis-services-in-multidimensional-and-data-mining-mode"></a><span data-ttu-id="ca1c9-102">在多维和数据挖掘模式下安装 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="ca1c9-102">Install Analysis Services in Multidimensional and Data Mining Mode</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="ca1c9-103">为商业智能应用程序提供联机分析处理 (OLAP) 和数据挖掘功能。</span><span class="sxs-lookup"><span data-stu-id="ca1c9-103">provides online analytical processing (OLAP) and data mining functionality for business intelligence applications.</span></span> <span data-ttu-id="ca1c9-104">在此版本中，在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] *多维模式下*安装时，支持 OLAP 数据库和数据挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="ca1c9-104">In this release, support for OLAP databases and data mining models is available when you install [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in *Multidimensional mode*.</span></span> <span data-ttu-id="ca1c9-105">多维模式是 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 运行时所采用的三种服务器模式之一。</span><span class="sxs-lookup"><span data-stu-id="ca1c9-105">Multidimensional mode is one of three server modes that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] runs in.</span></span> <span data-ttu-id="ca1c9-106">它是默认模式。</span><span class="sxs-lookup"><span data-stu-id="ca1c9-106">It is the default mode.</span></span> <span data-ttu-id="ca1c9-107">如果使用默认值安装 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]，则将获得运行多维数据库和数据挖掘模型的实例。</span><span class="sxs-lookup"><span data-stu-id="ca1c9-107">If you install [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] using default values, you will get an instance that runs multidimensional databases and data mining models.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="ca1c9-108">是一种多实例功能，这意味着您可以在单个计算机上安装 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的多个实例，或者与早期版本并行运行 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的新实例。</span><span class="sxs-lookup"><span data-stu-id="ca1c9-108">is a multi-instance feature, which means that you can install more than one instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] on a single computer, or run a new instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] side-by-side an earlier version.</span></span> <span data-ttu-id="ca1c9-109">服务器模式特定于实例。</span><span class="sxs-lookup"><span data-stu-id="ca1c9-109">Server mode is specific to an instance.</span></span> <span data-ttu-id="ca1c9-110">使用其他模式要求安装服务器的其他实例。</span><span class="sxs-lookup"><span data-stu-id="ca1c9-110">Using other modes requires that you install additional instances of the server.</span></span>  
  
 <span data-ttu-id="ca1c9-111">您可以单独安装 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 或将其与其他组件一起安装。</span><span class="sxs-lookup"><span data-stu-id="ca1c9-111">You can install [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] by itself or with other components.</span></span> <span data-ttu-id="ca1c9-112">如果只安装了 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，则在安装向导的 "功能选择" 页上选择 " **Analysis Services** " 时，将安装以下功能 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="ca1c9-112">If you install just [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the following features are installed when you select **Analysis Services** on the Feature Selection page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard:</span></span>  
  
-   <span data-ttu-id="ca1c9-113">用于运行 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库和数据挖掘模型的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 服务器</span><span class="sxs-lookup"><span data-stu-id="ca1c9-113">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server for running [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases and data mining models</span></span>  
  
-   <span data-ttu-id="ca1c9-114">用于对源数据库进行 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据访问的数据访问接口</span><span class="sxs-lookup"><span data-stu-id="ca1c9-114">Data providers used for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data access to source databases</span></span>  
  
-   <span data-ttu-id="ca1c9-115">SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="ca1c9-115">SQL Server Configuration Manager</span></span>  
  
## <a name="choosing-additional-features"></a><span data-ttu-id="ca1c9-116">选择其他功能</span><span class="sxs-lookup"><span data-stu-id="ca1c9-116">Choosing additional features</span></span>  
 <span data-ttu-id="ca1c9-117">Analysis Services OLAP 和数据仓库解决方案将要求安装附加的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件，以便实现 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库的开发、部署和管理。</span><span class="sxs-lookup"><span data-stu-id="ca1c9-117">Analysis Services OLAP and data warehouse solutions will require the installation of additional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components to enable the development, deployment, and administration of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases.</span></span> <span data-ttu-id="ca1c9-118">下列附加功能是许多典型用户应用场景的可选项：</span><span class="sxs-lookup"><span data-stu-id="ca1c9-118">The following additional features are options for many typical user scenarios:</span></span>  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="ca1c9-119">，用于创建和查看 Analysis Services 数据结构和数据挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="ca1c9-119">, used to create and view Analysis Services data structures and data mining models.</span></span>  
  
-   <span data-ttu-id="ca1c9-120">客户端工具连接组件，用于客户端与服务器之间通信的组件，包括用于 DB-Library、ODBC 和 OLE DB 的网络库。</span><span class="sxs-lookup"><span data-stu-id="ca1c9-120">Client tools connectivity components, used for communication between clients and servers, including network libraries for DB-Library, ODBC, and OLE DB.</span></span>  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]<span data-ttu-id="ca1c9-121">，一组用于移动、复制和转换数据的图形化和可编程的对象。</span><span class="sxs-lookup"><span data-stu-id="ca1c9-121">, a set of graphical and programmable objects for moving, copying, and transforming data.</span></span>  
  
-   <span data-ttu-id="ca1c9-122">管理工具，包括 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 和复制监视器。</span><span class="sxs-lookup"><span data-stu-id="ca1c9-122">Management tools, including [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], and Replication Monitor.</span></span>  
  
## <a name="installation-tasks"></a><span data-ttu-id="ca1c9-123">安装任务</span><span class="sxs-lookup"><span data-stu-id="ca1c9-123">Installation Tasks</span></span>  
 <span data-ttu-id="ca1c9-124">安装任务包括以下内容：</span><span class="sxs-lookup"><span data-stu-id="ca1c9-124">Installation tasks include the following:</span></span>  
  
|<span data-ttu-id="ca1c9-125">链接</span><span class="sxs-lookup"><span data-stu-id="ca1c9-125">Links</span></span>|<span data-ttu-id="ca1c9-126">任务</span><span class="sxs-lookup"><span data-stu-id="ca1c9-126">Tasks</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="ca1c9-127">[安装 SQL Server 2014 的硬件和软件要求](hardware-and-software-requirements-for-installing-sql-server.md)，并[配置 Windows 服务帐户和权限](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="ca1c9-127">[Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>|<span data-ttu-id="ca1c9-128">在您运行安装程序前，请检查安装 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的先决条件，并确定将用于设置服务器的帐户。</span><span class="sxs-lookup"><span data-stu-id="ca1c9-128">Before you run Setup, check prerequisites for installing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and determine which account you will use to provision the server.</span></span>|  
|<span data-ttu-id="ca1c9-129">[从安装向导安装 SQL Server 2014 &#40;安装&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="ca1c9-129">[Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).</span></span>|<span data-ttu-id="ca1c9-130">运行 SQL Server 安装程序以便安装该软件。</span><span class="sxs-lookup"><span data-stu-id="ca1c9-130">Run SQL Server Setup to install the software.</span></span>|  
|[<span data-ttu-id="ca1c9-131">配置 Windows 防火墙以允许 Analysis Services 访问</span><span class="sxs-lookup"><span data-stu-id="ca1c9-131">Configure the Windows Firewall to Allow Analysis Services Access</span></span>](https://docs.microsoft.com/analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access)|<span data-ttu-id="ca1c9-132">在完成安装后，必须配置防火墙设置，以便允许与服务器的远程连接。</span><span class="sxs-lookup"><span data-stu-id="ca1c9-132">After Setup is finished, you must configure firewall settings to allow remote connections to the server.</span></span>|  
|[<span data-ttu-id="ca1c9-133">授予对对象和操作的访问权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="ca1c9-133">Authorizing access to objects and operations &#40;Analysis Services&#41;</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services)|<span data-ttu-id="ca1c9-134">访问 Analysis Services 数据库的用户必须对服务器上的至少一个数据库具有读取权限。</span><span class="sxs-lookup"><span data-stu-id="ca1c9-134">Users who access Analysis Services databases must have Read permission on at least one database on the server.</span></span>|  
  
## <a name="related-content"></a><span data-ttu-id="ca1c9-135">相关内容</span><span class="sxs-lookup"><span data-stu-id="ca1c9-135">Related Content</span></span>  
 <span data-ttu-id="ca1c9-136">其他安装程序内容可以在下列主题中找到：</span><span class="sxs-lookup"><span data-stu-id="ca1c9-136">Additional setup content can be found in the following topics:</span></span>  
  
 [<span data-ttu-id="ca1c9-137">在表格模式下安装 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="ca1c9-137">Install Analysis Services in Tabular Mode</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services)  
  
 [<span data-ttu-id="ca1c9-138">PowerPivot for SharePoint 2010 安装</span><span class="sxs-lookup"><span data-stu-id="ca1c9-138">PowerPivot for SharePoint 2010 Installation</span></span>](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
 [<span data-ttu-id="ca1c9-139">确定 Analysis Services 实例的服务器模式</span><span class="sxs-lookup"><span data-stu-id="ca1c9-139">Determine the Server Mode of an Analysis Services Instance</span></span>](https://docs.microsoft.com/analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance)  
  
 [<span data-ttu-id="ca1c9-140">SQL Server 数据挖掘外接程序</span><span class="sxs-lookup"><span data-stu-id="ca1c9-140">SQL Server Data Mining Add-ins</span></span>](https://www.microsoft.com/download/details.aspx?id=35578)  
  
 <span data-ttu-id="ca1c9-141">默认情况下，不会将示例数据库、示例代码和客户端应用程序外接程序作为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序的一部分进行安装。</span><span class="sxs-lookup"><span data-stu-id="ca1c9-141">By default, sample databases, sample code, and client application add-ins are not installed as part of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span> <span data-ttu-id="ca1c9-142">若要安装示例数据库和示例代码，请参阅 [CodePlex 网站](https://go.microsoft.com/fwlink/?LinkId=87843)。</span><span class="sxs-lookup"><span data-stu-id="ca1c9-142">To install sample databases and sample code, see the [CodePlex Web site](https://go.microsoft.com/fwlink/?LinkId=87843).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca1c9-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ca1c9-143">See Also</span></span>  
 <span data-ttu-id="ca1c9-144">[SQL Server 2012 的各个版本支持的功能](https://go.microsoft.com/fwlink/?linkid=232473) </span><span class="sxs-lookup"><span data-stu-id="ca1c9-144">[Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) </span></span>  
 <span data-ttu-id="ca1c9-145">[语言和排序规则 &#40;Analysis Services&#41;](../../../2014/analysis-services/languages-and-collations-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="ca1c9-145">[Languages and Collations &#40;Analysis Services&#41;](../../../2014/analysis-services/languages-and-collations-analysis-services.md) </span></span>  
 [<span data-ttu-id="ca1c9-146">升级 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="ca1c9-146">Upgrade Analysis Services</span></span>](../../database-engine/install-windows/upgrade-analysis-services.md)  
  
  
