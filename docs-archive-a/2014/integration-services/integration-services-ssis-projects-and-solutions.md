---
title: Integration Services (SSIS) 项目 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- projects [Integration Services], creating
- folders [Integration Services], projects
- files [Integration Services], projects
- folders [Integration Services]
- projects [Integration Services], about projects
ms.assetid: 28ea8120-0a79-4029-93f0-07d521b32bee
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f71555a5339412bd0b79492607769d744c0d1a89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586861"
---
# <a name="integration-services-ssis-projects"></a><span data-ttu-id="ca236-102">Integration Services (SSIS) 项目</span><span class="sxs-lookup"><span data-stu-id="ca236-102">Integration Services (SSIS) Projects</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="ca236-103">提供 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 用于开发 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="ca236-103">provides [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for the development of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span>

 <span data-ttu-id="ca236-104">将包部署到 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库或 [!INCLUDE[ssIS](../includes/ssis-md.md)] 包存储区时，可以使用 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务来管理包。</span><span class="sxs-lookup"><span data-stu-id="ca236-104">When you deploy packages to a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database or the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Store, you use the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service to manage the packages.</span></span> <span data-ttu-id="ca236-105">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务只在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中可用。</span><span class="sxs-lookup"><span data-stu-id="ca236-105">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is available only in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="ca236-106">有关详细信息，请参阅 [Integration Services 服务（SSIS 服务）](service/integration-services-service-ssis-service.md)。</span><span class="sxs-lookup"><span data-stu-id="ca236-106">For more information about the service, see [Integration Services Service &#40;SSIS Service&#41;](service/integration-services-service-ssis-service.md).</span></span> <span data-ttu-id="ca236-107">有关包部署的详细信息，请参阅[包部署 &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="ca236-107">For more information about package deployment, see [Package Deployment &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md).</span></span>

 <span data-ttu-id="ca236-108">将 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目部署到[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务器时，您在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中使用 Transact-SQL 视图和存储过程来管理项目。</span><span class="sxs-lookup"><span data-stu-id="ca236-108">When you deploy [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, you use Transact-SQL views and stored procedures in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to manage the projects.</span></span> <span data-ttu-id="ca236-109">有关项目部署的详细信息，请参阅 [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="ca236-109">For more information about project deployment, see [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span> <span data-ttu-id="ca236-110">有关 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务器的详细信息，请参阅 [Integration Services (SSIS) 服务器](catalog/integration-services-ssis-server-and-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="ca236-110">For more information about the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, see [Integration Services &#40;SSIS&#41; Server](catalog/integration-services-ssis-server-and-catalog.md).</span></span>

 <span data-ttu-id="ca236-111">有关 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 和 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 的概述，请参阅 [Integration Services (SSIS) 和 Studio 环境](integration-services-ssis-development-and-management-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="ca236-111">For an overview of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], see [Integration Services &#40;SSIS&#41; and Studio Environments](integration-services-ssis-development-and-management-tools.md).</span></span>

## <a name="understanding-integration-services-projects"></a><span data-ttu-id="ca236-112">了解 Integration Services 项目</span><span class="sxs-lookup"><span data-stu-id="ca236-112">Understanding Integration Services Projects</span></span>
 <span data-ttu-id="ca236-113">项目是您开发 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包的容器。</span><span class="sxs-lookup"><span data-stu-id="ca236-113">A project is a container in which you develop [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span>

 <span data-ttu-id="ca236-114">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目可以存储与该包相关的文件并对这些文件进行分组。</span><span class="sxs-lookup"><span data-stu-id="ca236-114">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project stores and groups the files that are related to the package.</span></span> <span data-ttu-id="ca236-115">例如，项目包括创建特定提取、传输和加载 (ETL) 解决方案所需的文件。</span><span class="sxs-lookup"><span data-stu-id="ca236-115">For example, a project includes the files that are required to create a specific extract, transfer, and load (ETL) solution.</span></span>

 <span data-ttu-id="ca236-116">在创建 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目之前，应熟悉此类项目的基本内容。</span><span class="sxs-lookup"><span data-stu-id="ca236-116">Before you create an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, you should become familiar with the basic contents of this kind of project.</span></span> <span data-ttu-id="ca236-117">在了解项目包含的内容之后，即可开始创建和使用 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="ca236-117">After you understand what a project contains, you can begin creating and working with an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>

### <a name="folders-in-integration-services-projects"></a><span data-ttu-id="ca236-118">Integration Services 项目中的文件夹</span><span class="sxs-lookup"><span data-stu-id="ca236-118">Folders in Integration Services Projects</span></span>
 <span data-ttu-id="ca236-119">下面的关系图显示 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中一个 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]项目中的文件夹。</span><span class="sxs-lookup"><span data-stu-id="ca236-119">The following diagram shows the folders in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>

 <span data-ttu-id="ca236-120">![集成服务项目中的文件夹](media/solutionexplorer.gif "集成服务项目中的文件夹")</span><span class="sxs-lookup"><span data-stu-id="ca236-120">![Folders in an Integration Services project](media/solutionexplorer.gif "Folders in an Integration Services project")</span></span>

 <span data-ttu-id="ca236-121">下表介绍 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目中出现的文件夹。</span><span class="sxs-lookup"><span data-stu-id="ca236-121">The following table describes the folders that appear in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>

|<span data-ttu-id="ca236-122">Folder</span><span class="sxs-lookup"><span data-stu-id="ca236-122">Folder</span></span>|<span data-ttu-id="ca236-123">说明</span><span class="sxs-lookup"><span data-stu-id="ca236-123">Description</span></span>|
|------------|-----------------|
|[!INCLUDE[ssIS](../includes/ssis-md.md)] <span data-ttu-id="ca236-124">包</span><span class="sxs-lookup"><span data-stu-id="ca236-124">Packages</span></span>|<span data-ttu-id="ca236-125">包含包。</span><span class="sxs-lookup"><span data-stu-id="ca236-125">Contains packages.</span></span> <span data-ttu-id="ca236-126">有关详细信息，请参阅 [Integration Services (SSIS) 包](../../2014/integration-services/integration-services-ssis-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="ca236-126">For more information, see [Integration Services &#40;SSIS&#41; Packages](../../2014/integration-services/integration-services-ssis-packages.md).</span></span>|
|<span data-ttu-id="ca236-127">杂项</span><span class="sxs-lookup"><span data-stu-id="ca236-127">Miscellaneous</span></span>|<span data-ttu-id="ca236-128">包含除包文件以外的文件。</span><span class="sxs-lookup"><span data-stu-id="ca236-128">Contains files other than package files.</span></span>|

### <a name="files-in-integration-services-projects"></a><span data-ttu-id="ca236-129">Integration Services 项目中的文件</span><span class="sxs-lookup"><span data-stu-id="ca236-129">Files in Integration Services Projects</span></span>
 <span data-ttu-id="ca236-130">向解决方案添加新的或现有 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目时， [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 创建具有扩展名 .dtproj 、.dtproj.user 和 .database 的项目文件。</span><span class="sxs-lookup"><span data-stu-id="ca236-130">When you add a new or an existing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project to a solution, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] creates project files that have the extensions .dtproj and .dtproj.user and .database.</span></span>

-   <span data-ttu-id="ca236-131">\*.dtproj 文件包含有关项目配置以及像包这类项的信息。</span><span class="sxs-lookup"><span data-stu-id="ca236-131">The \*.dtproj file contains information about project configurations and items such as packages.</span></span>

-   <span data-ttu-id="ca236-132">\*.dtproj.user 文件包含有关使用项目的首选项的信息。</span><span class="sxs-lookup"><span data-stu-id="ca236-132">The \*.dtproj.user file contains information about your preferences for working with the project.</span></span>

-   <span data-ttu-id="ca236-133">\*.database 文件包含 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 打开 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目所需的信息。</span><span class="sxs-lookup"><span data-stu-id="ca236-133">The \*.database file contains information that [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] requires to open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>

## <a name="understanding-solutions"></a><span data-ttu-id="ca236-134">了解解决方案</span><span class="sxs-lookup"><span data-stu-id="ca236-134">Understanding Solutions</span></span>
 <span data-ttu-id="ca236-135">解决方案是对开发端到端商业解决方案时所使用的项目进行分组和管理的容器。</span><span class="sxs-lookup"><span data-stu-id="ca236-135">A solution is a container that groups and manages the projects that you use when you develop end-to-end business solutions.</span></span> <span data-ttu-id="ca236-136">使用解决方案，您可以将多个项目作为一个单元处理，并将构成商业解决方案的一个或多个相关项目组合在一起。</span><span class="sxs-lookup"><span data-stu-id="ca236-136">A solution lets you handle multiple projects as one unit and to bring together one or more related projects that contribute to a business solution.</span></span>

 <span data-ttu-id="ca236-137">解决方案可以包含不同类型的项目。</span><span class="sxs-lookup"><span data-stu-id="ca236-137">Solutions can include different types of projects.</span></span> <span data-ttu-id="ca236-138">如果要用 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器创建 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包，请使用 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 所提供的解决方案中的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]项目。</span><span class="sxs-lookup"><span data-stu-id="ca236-138">If you want to use [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to create an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package, you work in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in a solution provided by [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>

 <span data-ttu-id="ca236-139">创建新的解决方案时， [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 将在解决方案资源管理器中添加一个解决方案文件夹，并创建扩展名为 .sln 和 .suo 的文件：</span><span class="sxs-lookup"><span data-stu-id="ca236-139">When you create a new solution, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] adds a Solution folder to Solution Explorer, and creates files that have the extensions, .sln and .suo:</span></span>

-   <span data-ttu-id="ca236-140">\*.sln 文件包含有关解决方案配置的信息，并列出解决方案中的项目。</span><span class="sxs-lookup"><span data-stu-id="ca236-140">The \*.sln file contains information about the solution configuration and lists the projects in the solution.</span></span>

-   <span data-ttu-id="ca236-141">\*.suo 文件包含有关使用解决方案的首选项的信息。</span><span class="sxs-lookup"><span data-stu-id="ca236-141">The \*.suo file contains information about your preferences for working with the solution.</span></span>

 <span data-ttu-id="ca236-142">当您创建新项目时 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 将自动创建解决方案，但您也可创建空解决方案，然后再添加项目。</span><span class="sxs-lookup"><span data-stu-id="ca236-142">While [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] automatically creates a solution when you create a new project, you can also create a blank solution, and then add projects later.</span></span>

> [!NOTE]
>  <span data-ttu-id="ca236-143">默认情况下，在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中创建新 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]项目时， **“项目资源管理器”** 窗格不会显示解决方案。</span><span class="sxs-lookup"><span data-stu-id="ca236-143">By default, when you create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the solution is not shown in the **Project Explorer** pane.</span></span> <span data-ttu-id="ca236-144">若要更改此默认行为，请在 **“工具”** 菜单上单击 **“选项”**。</span><span class="sxs-lookup"><span data-stu-id="ca236-144">To change this default behavior, on the **Tools** menus, click **Options**.</span></span> <span data-ttu-id="ca236-145">在 **“选项”** 对话框中，展开 **“项目和解决方案”**，然后单击 **“常规”**。</span><span class="sxs-lookup"><span data-stu-id="ca236-145">In the **Options** dialog box, expand **Projects and Solutions**, and then click **General**.</span></span> <span data-ttu-id="ca236-146">在 **“常规”** 页上，选择 **“总是显示解决方案”**。</span><span class="sxs-lookup"><span data-stu-id="ca236-146">On the **General** page, select **Always show solution**.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="ca236-147">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="ca236-147">Related Tasks</span></span>
 [<span data-ttu-id="ca236-148">在解决方案中添加或删除 Integration Services 项目</span><span class="sxs-lookup"><span data-stu-id="ca236-148">Add or Remove an Integration Services Project in a Solution</span></span>](../../2014/integration-services/add-or-remove-an-integration-services-project-in-a-solution.md)

 [<span data-ttu-id="ca236-149">创建新的 Integration Services 项目</span><span class="sxs-lookup"><span data-stu-id="ca236-149">Create a New Integration Services Project</span></span>](../../2014/integration-services/create-a-new-integration-services-project.md)

 [<span data-ttu-id="ca236-150">向 Integration Services 项目添加项</span><span class="sxs-lookup"><span data-stu-id="ca236-150">Add an Item to an Integration Services Project</span></span>](../../2014/integration-services/add-an-item-to-an-integration-services-project.md)

 [<span data-ttu-id="ca236-151">复制项目项</span><span class="sxs-lookup"><span data-stu-id="ca236-151">Copy Project Items</span></span>](../../2014/integration-services/copy-project-items.md)

## <a name="related-content"></a><span data-ttu-id="ca236-152">相关内容</span><span class="sxs-lookup"><span data-stu-id="ca236-152">Related Content</span></span>
 [<span data-ttu-id="ca236-153">Integration Services 项目的开发</span><span class="sxs-lookup"><span data-stu-id="ca236-153">Development of an Integration Services Project</span></span>](../../2014/integration-services/development-of-an-integration-services-project.md)


