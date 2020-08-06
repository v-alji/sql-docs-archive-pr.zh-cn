---
title: SQL Server 2014 的版本和组件 |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- Enterprise Edition [SQL Server]
- Developer Edition [SQL Server]
- 32-bit vs. 64-bit editions [SQL Server]
- default components
- Workgroup Edition [SQL Server]
- Internet servers [SQL Server]
- installing SQL Server, components
- Setup [SQL Server], components
- SQL Server, editions
- SQL Server, components
- client/server applications [SQL Server]
- editions [SQL Server]
- versions [SQL Server]
- Setup [SQL Server], editions
- SQL Server Installation Wizard
- components [SQL Server]
- Standard Edition [SQL Server]
- 64-bit edition [SQL Server]
- IIS [SQL Server]
- installing SQL Server, editions
- editions [SQL Server], about edition options
- Setup [SQL Server]
ms.assetid: e5186f02-dd91-47d0-8fa4-de3f41c76903
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ba357d09a50912d8b2ffff8dec948df06a24c3d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586302"
---
# <a name="editions-and-components-of-sql-server-2014"></a><span data-ttu-id="bce6c-102">SQL Server 2014 的版本和组件</span><span class="sxs-lookup"><span data-stu-id="bce6c-102">Editions and Components of SQL Server 2014</span></span>
  <span data-ttu-id="bce6c-103">根据应用程序的需要，安装要求会有所不同。</span><span class="sxs-lookup"><span data-stu-id="bce6c-103">Installation requirements vary based on your application needs.</span></span> <span data-ttu-id="bce6c-104">不同版本的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 能够满足单位和个人独特的性能、运行时以及价格要求。</span><span class="sxs-lookup"><span data-stu-id="bce6c-104">The different editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] accommodate the unique performance, runtime, and price requirements of organizations and individuals.</span></span> <span data-ttu-id="bce6c-105">安装哪些 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 组件还取决于您的具体需要。</span><span class="sxs-lookup"><span data-stu-id="bce6c-105">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] components that you install also depend on your specific requirements.</span></span> <span data-ttu-id="bce6c-106">下面各节将帮助您了解如何在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的不同版本和可用组件中做出最佳选择。</span><span class="sxs-lookup"><span data-stu-id="bce6c-106">The following sections help you understand how to make the best choice among the editions and components available in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="principal-editions-of-sscurrent"></a><span data-ttu-id="bce6c-107"> 的主要版本</span><span class="sxs-lookup"><span data-stu-id="bce6c-107">Principal Editions of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]</span></span>  
 <span data-ttu-id="bce6c-108">下表介绍 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的主要版本。</span><span class="sxs-lookup"><span data-stu-id="bce6c-108">The following table describes the principal editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bce6c-109">有关详细信息，请参阅[SQL Server 2014 的各个版本支持的功能](../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)</span><span class="sxs-lookup"><span data-stu-id="bce6c-109">For more information, see [Features Supported by the Editions of SQL Server 2014](../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)</span></span>  
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="bce6c-110">版本</span><span class="sxs-lookup"><span data-stu-id="bce6c-110">edition</span></span>|<span data-ttu-id="bce6c-111">定义</span><span class="sxs-lookup"><span data-stu-id="bce6c-111">Definition</span></span>|  
|---------------------------------------|----------------|  
|<span data-ttu-id="bce6c-112">Enterprise（64 位和 32 位）</span><span class="sxs-lookup"><span data-stu-id="bce6c-112">Enterprise (64-bit and 32-bit)</span></span>|<span data-ttu-id="bce6c-113">作为高级版本，[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Enterprise 版提供了全面的高端数据中心功能，性能极为快捷、虚拟化不受限制，还具有端到端的商业智能，可为关键任务工作负荷提供较高服务级别，支持最终用户访问深层数据。</span><span class="sxs-lookup"><span data-stu-id="bce6c-113">The premium offering, [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Enterprise edition delivers comprehensive high-end datacenter capabilities with blazing-fast performance, unlimited virtualization, and end-to-end business intelligence - enabling high service levels for mission-critical workloads and end user access to data insights.</span></span>|  
|<span data-ttu-id="bce6c-114">Business Intelligence（64 位和 32 位）</span><span class="sxs-lookup"><span data-stu-id="bce6c-114">Business Intelligence (64-bit and 32-bit)</span></span>|[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] <span data-ttu-id="bce6c-115">Business Intelligence 版提供了综合性平台，可支持组织构建和部署安全、可扩展且易于管理的 BI 解决方案。</span><span class="sxs-lookup"><span data-stu-id="bce6c-115">Business Intelligence edition delivers comprehensive platform empowering organizations to build and deploy secure, scalable and manageable BI solutions.</span></span> <span data-ttu-id="bce6c-116">它提供了令人兴奋的功能，如基于浏览器的数据浏览和可视化。强大的数据混合功能，以及增强的集成管理。</span><span class="sxs-lookup"><span data-stu-id="bce6c-116">It offers exciting functionality such as browser based data exploration and visualization; powerful data mash-up capabilities, and enhanced integration management.</span></span>|  
|<span data-ttu-id="bce6c-117">Standard（64 位和 32 位）</span><span class="sxs-lookup"><span data-stu-id="bce6c-117">Standard (64-bit and 32-bit)</span></span>|[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] <span data-ttu-id="bce6c-118">Standard 版提供了基本数据管理和商业智能数据库，使部门和小型组织能够顺利运行其应用程序并支持将常用开发工具用于内部部署和云部署，有助于以最少的 IT 资源获得高效的数据库管理。</span><span class="sxs-lookup"><span data-stu-id="bce6c-118">Standard edition delivers basic data management and business intelligence database for departments and small organizations to run their applications and supports common development tools for on-premise and cloud - enabling effective database management with minimal IT resources.</span></span>|  
  
## <a name="specialized-editions-of-sscurrent"></a><span data-ttu-id="bce6c-119">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 的专业版本</span><span class="sxs-lookup"><span data-stu-id="bce6c-119">Specialized Editions of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]</span></span>  
 <span data-ttu-id="bce6c-120">专业化版本的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 面向不同的业务工作负荷。</span><span class="sxs-lookup"><span data-stu-id="bce6c-120">Specialized editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] are targeted for business workloads.</span></span> <span data-ttu-id="bce6c-121">下表介绍 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的专业化版本。</span><span class="sxs-lookup"><span data-stu-id="bce6c-121">The following table describes the specialized editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="bce6c-122">版本</span><span class="sxs-lookup"><span data-stu-id="bce6c-122">edition</span></span>|<span data-ttu-id="bce6c-123">说明</span><span class="sxs-lookup"><span data-stu-id="bce6c-123">Description</span></span>|  
|---------------------------------------|-----------------|  
|<span data-ttu-id="bce6c-124">Web（64 位和 32 位）</span><span class="sxs-lookup"><span data-stu-id="bce6c-124">Web (64-bit and 32-bit)</span></span>|<span data-ttu-id="bce6c-125">对于为从小规模至大规模 Web 资产提供可伸缩性、经济性和可管理性功能的 Web 宿主和 Web VAP 来说，[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Web 版本是一项总拥有成本较低的选择。</span><span class="sxs-lookup"><span data-stu-id="bce6c-125">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Web edition is a low total-cost-of-ownership option for Web hosters and Web VAPs to provide scalability, affordability, and manageability capabilities for small to large scale Web properties.</span></span>|  
  
## <a name="breadth-editions-of-sscurrent"></a><span data-ttu-id="bce6c-126"> 的扩展版本</span><span class="sxs-lookup"><span data-stu-id="bce6c-126">Breadth Editions of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]</span></span>  
 <span data-ttu-id="bce6c-127">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 延伸版是针对特定的用户应用而设计的，可免费获取或只需支付极少的费用。</span><span class="sxs-lookup"><span data-stu-id="bce6c-127">Breadth editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] are engineered for specific customer scenarios and are offered FREE or at a very nominal cost.</span></span> <span data-ttu-id="bce6c-128">下表介绍 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的延伸版本。</span><span class="sxs-lookup"><span data-stu-id="bce6c-128">The following table describes the breadth editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="bce6c-129">版本</span><span class="sxs-lookup"><span data-stu-id="bce6c-129">edition</span></span>|<span data-ttu-id="bce6c-130">说明</span><span class="sxs-lookup"><span data-stu-id="bce6c-130">Description</span></span>|  
|---------------------------------------|-----------------|  
|<span data-ttu-id="bce6c-131">Developer（64 位和 32 位）</span><span class="sxs-lookup"><span data-stu-id="bce6c-131">Developer (64-bit and 32-bit)</span></span>|[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] <span data-ttu-id="bce6c-132">Developer 版支持开发人员基于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]构建任意类型的应用程序。</span><span class="sxs-lookup"><span data-stu-id="bce6c-132">Developer edition lets developers build any kind of application on top of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bce6c-133">它包括 Enterprise 版的所有功能，但有许可限制，只能用作开发和测试系统，而不能用作生产服务器。</span><span class="sxs-lookup"><span data-stu-id="bce6c-133">It includes all the functionality of Enterprise edition, but is licensed for use as a development and test system, not as a production server.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="bce6c-134">Developer 是构建和测试应用程序的人员的理想之选。</span><span class="sxs-lookup"><span data-stu-id="bce6c-134">Developer is an ideal choice for people who build and test applications.</span></span>|  
|<span data-ttu-id="bce6c-135">Express 版（64 位和 32 位）</span><span class="sxs-lookup"><span data-stu-id="bce6c-135">Express (64-bit and 32-bit) editions</span></span>|[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] <span data-ttu-id="bce6c-136">Express 是入门级的免费数据库，是学习和构建桌面及小型服务器数据驱动应用程序的理想选择。</span><span class="sxs-lookup"><span data-stu-id="bce6c-136">Express edition is the entry-level, free database and is ideal for learning and building desktop and small server data-driven applications.</span></span> <span data-ttu-id="bce6c-137">它是独立软件供应商、开发人员和热衷于构建客户端应用程序的人员的最佳选择。</span><span class="sxs-lookup"><span data-stu-id="bce6c-137">It is the best choice for independent software vendors, developers, and hobbyists building client applications.</span></span> <span data-ttu-id="bce6c-138">如果您需要使用更高级的数据库功能，则可以将 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Express 无缝升级到其他更高端的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]版本。</span><span class="sxs-lookup"><span data-stu-id="bce6c-138">If you need more advanced database features, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Express can be seamlessly upgraded to other higher end versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="bce6c-139">Express LocalDB 是 Express 的一种轻型版本，该版本具备所有可编程性功能，但在用户模式下运行，并且具有快速的零配置安装和必备组件要求较少的特点。</span><span class="sxs-lookup"><span data-stu-id="bce6c-139">Express LocalDB, a lightweight version of Express that has all of its programmability features, yet runs in user mode and has a fast, zero-configuration installation and a short list of prerequisites.</span></span>|  
  
## <a name="using-ssnoversion-with-an-internet-server"></a><span data-ttu-id="bce6c-140">将 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 用于 Internet 服务器</span><span class="sxs-lookup"><span data-stu-id="bce6c-140">Using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] with an Internet Server</span></span>  
 <span data-ttu-id="bce6c-141">在 Internet 服务器（如运行 Internet Information Services (IIS) 的服务器）上通常都会安装 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 客户端工具。</span><span class="sxs-lookup"><span data-stu-id="bce6c-141">On an Internet server, such as a server that is running Internet Information Services (IIS), you will typically install the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] client tools.</span></span> <span data-ttu-id="bce6c-142">客户端工具包括连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]实例的应用程序所使用的客户端连接组件。</span><span class="sxs-lookup"><span data-stu-id="bce6c-142">Client tools include the client connectivity components used by an application connecting to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bce6c-143">尽管可以在运行 IIS 的计算机上安装 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例，但这种做法通常只用于仅包含一台服务器的小型网站。</span><span class="sxs-lookup"><span data-stu-id="bce6c-143">Although you can install an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on a computer that is running IIS, this is typically done only for small Web sites that have a single server computer.</span></span> <span data-ttu-id="bce6c-144">大多数网站都将其中间层 IIS 系统安装在一台服务器上或服务器群集中，将数据库安装在另外一个服务器或服务器联合体上。</span><span class="sxs-lookup"><span data-stu-id="bce6c-144">Most Web sites have their middle-tier IIS systems on one server or a cluster of servers, and their databases on a separate server or federation of servers.</span></span>  
  
## <a name="using-ssnoversion-with-clientserver-applications"></a><span data-ttu-id="bce6c-145">将 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 用于客户端/服务器应用程序</span><span class="sxs-lookup"><span data-stu-id="bce6c-145">Using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] with Client/Server Applications</span></span>  
 <span data-ttu-id="bce6c-146">在运行直接连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例的客户端/服务器应用程序的计算机上，只能安装 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]客户端组件。</span><span class="sxs-lookup"><span data-stu-id="bce6c-146">You can install just the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] client components on a computer that is running client/server applications that connect directly to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bce6c-147">如果要在数据库服务器上管理 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例，或者打算开发 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 应用程序，那么客户端组件安装也是一个不错的选择。</span><span class="sxs-lookup"><span data-stu-id="bce6c-147">A client components installation is also a good option if you administer an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on a database server, or if you plan to develop [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] applications.</span></span>  
  
 <span data-ttu-id="bce6c-148">客户端工具选项安装以下 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 功能：向后兼容性组件、 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]、连接组件、管理工具、软件开发包和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 联机丛书组件。</span><span class="sxs-lookup"><span data-stu-id="bce6c-148">The client tools option installs the following [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] features: backward compatibility components, [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], connectivity components, management tools, software development kit, and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online components.</span></span> <span data-ttu-id="bce6c-149">有关详细信息，请参阅安装[向导中的安装 SQL Server 2014 &#40;安装&#41;](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="bce6c-149">For more information, see [Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).</span></span>  
  
## <a name="deciding-among-ssnoversion-components"></a><span data-ttu-id="bce6c-150">选择 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 组件</span><span class="sxs-lookup"><span data-stu-id="bce6c-150">Deciding Among [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Components</span></span>  
 <span data-ttu-id="bce6c-151">使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安装向导的“功能选择”页面选择安装 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]时要安装的组件。</span><span class="sxs-lookup"><span data-stu-id="bce6c-151">Use the Feature Selection page of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Installation Wizard to select the components to include in an installation of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bce6c-152">默认情况下未选中树中的任何功能。</span><span class="sxs-lookup"><span data-stu-id="bce6c-152">By default, none of the features in the tree are selected.</span></span>  
  
 <span data-ttu-id="bce6c-153">可根据下表中给出的信息确定最能满足需要的功能集合。</span><span class="sxs-lookup"><span data-stu-id="bce6c-153">Use the information in the following tables to determine the set of features that best fits your needs.</span></span>  
  
|<span data-ttu-id="bce6c-154">服务器组件</span><span class="sxs-lookup"><span data-stu-id="bce6c-154">Server components</span></span>|<span data-ttu-id="bce6c-155">说明</span><span class="sxs-lookup"><span data-stu-id="bce6c-155">Description</span></span>|  
|-----------------------|-----------------|  
|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] <span data-ttu-id="bce6c-156">包括[!INCLUDE[ssDE](../includes/ssde-md.md)]（用于存储、处理和保护数据安全的核心服务）、复制、全文搜索、用于管理关系数据和 XML 数据的工具以及 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 服务器。</span><span class="sxs-lookup"><span data-stu-id="bce6c-156">includes the [!INCLUDE[ssDE](../includes/ssde-md.md)], the core service for storing, processing, and securing data, replication, full-text search, tools for managing relational and XML data, and the [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) server.</span></span>|  
|[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]|[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="bce6c-157">包括一些工具，可用于创建和管理联机分析处理 (OLAP) 以及数据挖掘应用程序。</span><span class="sxs-lookup"><span data-stu-id="bce6c-157">includes the tools for creating and managing online analytical processing (OLAP) and data mining applications.</span></span>|  
|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="bce6c-158">包括用于创建、管理和部署表格报表、矩阵报表、图形报表以及自由格式报表的服务器和客户端组件。</span><span class="sxs-lookup"><span data-stu-id="bce6c-158">includes server and client components for creating, managing, and deploying tabular, matrix, graphical, and free-form reports.</span></span> [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="bce6c-159">还是一个可用于开发报表应用程序的可扩展平台。</span><span class="sxs-lookup"><span data-stu-id="bce6c-159">is also an extensible platform that you can use to develop report applications.</span></span>|  
|[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]|[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="bce6c-160">是一组图形工具和可编程对象，用于移动、复制和转换数据。</span><span class="sxs-lookup"><span data-stu-id="bce6c-160">is a set of graphical tools and programmable objects for moving, copying, and transforming data.</span></span> <span data-ttu-id="bce6c-161">它还包括 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] 的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)](DQS) 组件。</span><span class="sxs-lookup"><span data-stu-id="bce6c-161">It also includes the [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) component for [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] <span data-ttu-id="bce6c-162">(MDS) 是针对主数据管理的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 解决方案。</span><span class="sxs-lookup"><span data-stu-id="bce6c-162">(MDS) is the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] solution for master data management.</span></span> <span data-ttu-id="bce6c-163">可以配置 MDS 来管理任何领域（产品、客户、帐户）；MDS 中可包括层次结构、各种级别的安全性、事务、数据版本控制和业务规则，以及可用于管理数据的 [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="bce6c-163">MDS can be configured to manage any domain (products, customers, accounts) and includes hierarchies, granular security, transactions, data versioning, and business rules, as well as an [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] that can be used to manage data.</span></span>|  
  
|<span data-ttu-id="bce6c-164">管理工具</span><span class="sxs-lookup"><span data-stu-id="bce6c-164">Management tools</span></span>|<span data-ttu-id="bce6c-165">说明</span><span class="sxs-lookup"><span data-stu-id="bce6c-165">Description</span></span>|  
|----------------------|-----------------|  
|[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]|[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="bce6c-166">是用于访问、配置、管理和开发 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]组件的集成环境。</span><span class="sxs-lookup"><span data-stu-id="bce6c-166">is an integrated environment to access, configure, manage, administer, and develop components of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] <span data-ttu-id="bce6c-167">使各种技术水平的开发人员和管理员都能使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bce6c-167">lets developers and administrators of all skill levels use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="bce6c-168">配置管理器</span><span class="sxs-lookup"><span data-stu-id="bce6c-168">Configuration Manager</span></span>|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="bce6c-169">配置管理器为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 服务、服务器协议、客户端协议和客户端别名提供基本配置管理。</span><span class="sxs-lookup"><span data-stu-id="bce6c-169">Configuration Manager provides basic configuration management for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] services, server protocols, client protocols, and client aliases.</span></span>|  
|[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]|[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] <span data-ttu-id="bce6c-170">提供了一个图形用户界面，用于监视 [!INCLUDE[ssDE](../includes/ssde-md.md)] 实例或 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="bce6c-170">provides a graphical user interface to monitor an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)] or [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>|  
|[!INCLUDE[ssDE](../includes/ssde-md.md)] <span data-ttu-id="bce6c-171">优化顾问</span><span class="sxs-lookup"><span data-stu-id="bce6c-171">Tuning Advisor</span></span>|[!INCLUDE[ssDE](../includes/ssde-md.md)] <span data-ttu-id="bce6c-172">优化顾问可以协助创建索引、索引视图和分区的最佳组合。</span><span class="sxs-lookup"><span data-stu-id="bce6c-172">Tuning Advisor helps create optimal sets of indexes, indexed views, and partitions.</span></span>|  
|<span data-ttu-id="bce6c-173">数据质量客户端</span><span class="sxs-lookup"><span data-stu-id="bce6c-173">Data Quality Client</span></span>|<span data-ttu-id="bce6c-174">提供了一个非常简单和直观的图形用户界面，用于连接到 DQS 数据库并执行数据清理操作。</span><span class="sxs-lookup"><span data-stu-id="bce6c-174">Provides a highly simple and intuitive graphical user interface to connect to the DQS server, and perform data cleansing operations.</span></span> <span data-ttu-id="bce6c-175">它还允许您集中监视在数据清理操作过程中执行的各项活动。</span><span class="sxs-lookup"><span data-stu-id="bce6c-175">It also allows you to centrally monitor various activities performed during the data cleansing operation.</span></span>|  
|[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]|[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] <span data-ttu-id="bce6c-176">提供 IDE 以便为以下商业智能组件生成解决方案： [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]和 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bce6c-176">provides an IDE for building solutions for the Business Intelligence components: [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], and [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="bce6c-177">（以前称作 Business Intelligence Development Studio）。</span><span class="sxs-lookup"><span data-stu-id="bce6c-177">(Formerly called Business Intelligence Development Studio).</span></span><br /><br /> [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] <span data-ttu-id="bce6c-178">还包含“数据库项目”，为数据库开发人员提供集成环境，以便在 Visual Studio 内为任何 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 平台（包括本地和外部）执行其所有数据库设计工作。</span><span class="sxs-lookup"><span data-stu-id="bce6c-178">also includes "Database Projects", which provides an integrated environment for database developers to carry out all their database design work for any [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] platform (both on and off premise) within Visual Studio.</span></span> <span data-ttu-id="bce6c-179">数据库开发人员可以使用 Visual Studio 中功能增强的服务器资源管理器，轻松创建或编辑数据库对象和数据或执行查询。</span><span class="sxs-lookup"><span data-stu-id="bce6c-179">Database developers can use the enhanced Server Explorer in Visual Studio to easily create or edit database objects and data, or execute queries.</span></span>|  
|<span data-ttu-id="bce6c-180">连接组件</span><span class="sxs-lookup"><span data-stu-id="bce6c-180">Connectivity Components</span></span>|<span data-ttu-id="bce6c-181">安装用于客户端和服务器之间通信的组件，以及用于 DB-Library、ODBC 和 OLE DB 的网络库。</span><span class="sxs-lookup"><span data-stu-id="bce6c-181">Installs components for communication between clients and servers, and network libraries for DB-Library, ODBC, and OLE DB.</span></span>|  
  
|<span data-ttu-id="bce6c-182">文档</span><span class="sxs-lookup"><span data-stu-id="bce6c-182">Documentation</span></span>|<span data-ttu-id="bce6c-183">说明</span><span class="sxs-lookup"><span data-stu-id="bce6c-183">Description</span></span>|  
|-------------------|-----------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="bce6c-184">联机丛书</span><span class="sxs-lookup"><span data-stu-id="bce6c-184">Books Online</span></span>|<span data-ttu-id="bce6c-185">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的核心文档。</span><span class="sxs-lookup"><span data-stu-id="bce6c-185">Core documentation for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bce6c-186">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bce6c-186">See Also</span></span>  
 <span data-ttu-id="bce6c-187">[计划 SQL Server 安装](install/planning-a-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="bce6c-187">[Planning a SQL Server Installation](install/planning-a-sql-server-installation.md) </span></span>  
 [<span data-ttu-id="bce6c-188">从安装向导安装 SQL Server 2014 &#40;安装程序&#41;</span><span class="sxs-lookup"><span data-stu-id="bce6c-188">Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;</span></span>](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)  
  
  