---
title: 将项目部署到 Integration Services Server |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 6e9402f4-4d50-49ff-820d-65a77829c4a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 944dff3531fa24344c5157a1ac90e0109c6d0387
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590309"
---
# <a name="deploy-projects-to-integration-services-server"></a><span data-ttu-id="65f9b-102">Deploy Projects to Integration Services Server</span><span class="sxs-lookup"><span data-stu-id="65f9b-102">Deploy Projects to Integration Services Server</span></span>
  <span data-ttu-id="65f9b-103">在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]的当前版本中，您可以将您的项目部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="65f9b-103">In the current release of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], you can deploy your projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="65f9b-104">通过 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务器，您可以使用环境来管理包、运行包以及为包配置运行时值。</span><span class="sxs-lookup"><span data-stu-id="65f9b-104">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server enables you to manage packages, run packages, and configure runtime values for packages by using environments.</span></span>  
  
 <span data-ttu-id="65f9b-105">有关环境的详细信息，请参阅 [创建和映射服务器环境](../../2014/integration-services/create-and-map-a-server-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="65f9b-105">For more information about environments, see [Create and Map a Server Environment](../../2014/integration-services/create-and-map-a-server-environment.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="65f9b-106">与 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]的早期版本一样，在当前版本中，您也可以将您的包部署到 SQL Server 实例并且使用 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务运行和管理包。</span><span class="sxs-lookup"><span data-stu-id="65f9b-106">As in earlier versions of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], in the current release you can also deploy your packages to an instance of SQL Server and use [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service to run and manage the packages.</span></span> <span data-ttu-id="65f9b-107">您使用包部署模型。</span><span class="sxs-lookup"><span data-stu-id="65f9b-107">You use the package deployment model.</span></span> <span data-ttu-id="65f9b-108">有关详细信息，请参阅[包部署 &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="65f9b-108">For more information, see [Package Deployment &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md).</span></span>  
  
 <span data-ttu-id="65f9b-109">若要将项目部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务器，请完成以下任务：</span><span class="sxs-lookup"><span data-stu-id="65f9b-109">To deploy a project to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, complete the following tasks:</span></span>  
  
1.  <span data-ttu-id="65f9b-110">创建一个 SSISDB 目录（如果尚未创建）。</span><span class="sxs-lookup"><span data-stu-id="65f9b-110">Create an SSISDB catalog, if you haven't already.</span></span> <span data-ttu-id="65f9b-111">有关详细信息，请参阅 [创建 SSIS 目录](catalog/ssis-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="65f9b-111">For more information, see [Create the SSIS Catalog](catalog/ssis-catalog.md).</span></span>  
  
2.  <span data-ttu-id="65f9b-112">通过运行 **“Integration Services 项目转换向导”** 可以将项目转换为项目部署模型。</span><span class="sxs-lookup"><span data-stu-id="65f9b-112">Convert the project to the project deployment model by running the **Integration Services Project Conversion Wizard** .</span></span> <span data-ttu-id="65f9b-113">有关详细信息，请参阅下面的说明： [将项目转换为项目部署模型](#convert)</span><span class="sxs-lookup"><span data-stu-id="65f9b-113">For more information, see the instructions below: [To convert a project to the project deployment model](#convert)</span></span>  
  
    -   <span data-ttu-id="65f9b-114">如果在 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)]中创建了项目，默认情况下该项目使用项目部署模型。</span><span class="sxs-lookup"><span data-stu-id="65f9b-114">If you created the project in [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)], by default the project uses the project deployment model.</span></span>  
  
    -   <span data-ttu-id="65f9b-115">如果您在早期版本的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]中创建了项目，则在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中打开项目文件之后，将该项目转换为项目部署模型。</span><span class="sxs-lookup"><span data-stu-id="65f9b-115">If you created the project in an earlier release of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], after you open the project file in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], convert the project to the project deployment model.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="65f9b-116">如果项目包含一个或多个数据源，则在项目转换完成时删除数据源。</span><span class="sxs-lookup"><span data-stu-id="65f9b-116">If the project contains one or more datasources, the datasources are removed when the project conversion is completed.</span></span> <span data-ttu-id="65f9b-117">若要创建到项目中的包可共享的数据源的连接，请在项目级别添加连接管理器。</span><span class="sxs-lookup"><span data-stu-id="65f9b-117">To create a connection to a data source that the packages in the project can share, add a connection manager at the project level.</span></span> <span data-ttu-id="65f9b-118">有关详细信息，请参阅 [在包中添加、删除或共享连接管理器](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md)。</span><span class="sxs-lookup"><span data-stu-id="65f9b-118">For more information, see [Add, Delete, or Share a Connection Manager in a Package](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md).</span></span>  
  
         <span data-ttu-id="65f9b-119">根据您是从 **还是从** 运行 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] “Integration Services 项目转换向导” [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]，该向导将执行不同的转换任务。</span><span class="sxs-lookup"><span data-stu-id="65f9b-119">Depending on whether you run the **Integration Services Project Conversion Wizard** from [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] or from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], the wizard performs different conversion tasks.</span></span>  
  
        -   <span data-ttu-id="65f9b-120">如果您是从 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]运行该向导的，则在项目中包含的包将从 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 2005、2008 或 2008 R2 转换为当前版本的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]使用的格式。</span><span class="sxs-lookup"><span data-stu-id="65f9b-120">If you run the wizard from [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], the packages contained in the project are converted from [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 2005, 2008, or 2008 R2 to the format that is used by the current version of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="65f9b-121">原始项目 (.dtproj) 和包 (.dtsx) 文件将升级。</span><span class="sxs-lookup"><span data-stu-id="65f9b-121">The original project (.dtproj) and package (.dtsx) files are upgraded.</span></span>  
  
        -   <span data-ttu-id="65f9b-122">如果你是从 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]运行该向导的，则该向导将根据项目中包含的包和配置生成一个项目部署文件 (.ispac)。</span><span class="sxs-lookup"><span data-stu-id="65f9b-122">If you run the wizard from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], the wizard generates a project deployment file (.ispac) from the packages and configurations contained in the project.</span></span> <span data-ttu-id="65f9b-123">原始包 (.dtsx) 文件不升级。</span><span class="sxs-lookup"><span data-stu-id="65f9b-123">The original package (.dtsx) files are not upgraded.</span></span>  
  
             <span data-ttu-id="65f9b-124">您可以在该向导的 **“选择目标”** 页中选择一个现有文件或创建一个新文件。</span><span class="sxs-lookup"><span data-stu-id="65f9b-124">You can select an existing file or create a new file, in the **Selection Destination** page of the wizard.</span></span>  
  
             <span data-ttu-id="65f9b-125">若要在转换项目时升级包文件，请从 **运行** “Integration Services 项目转换向导” [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="65f9b-125">To upgrade package files when a project is converted, run the **Integration Services Project Conversion Wizard** from [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="65f9b-126">若要单独从项目转换中升级包文件，请从 **中运行** “Integration Services 项目转换向导” [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ，然后运行 **“SSIS 包升级向导”**。</span><span class="sxs-lookup"><span data-stu-id="65f9b-126">To upgrade package files separately from a project conversion, run the **Integration Services Project Conversion Wizard** from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and then run the **SSIS Package Upgrade Wizard**.</span></span> <span data-ttu-id="65f9b-127">如果单独升级包文件，请确保您保存了这些更改。</span><span class="sxs-lookup"><span data-stu-id="65f9b-127">If you upgrade the package files separately, ensure that you save the changes.</span></span> <span data-ttu-id="65f9b-128">否则，在您将项目转换为项目部署模型时，将不会转换对包的任何未保存的更改。</span><span class="sxs-lookup"><span data-stu-id="65f9b-128">Otherwise, when you convert the project to the project deployment model, any unsaved changes to the package are not converted.</span></span>  
  
     <span data-ttu-id="65f9b-129">有关包升级的详细信息，请参阅 [升级 Integration Services 包](install-windows/upgrade-integration-services-packages.md) 和 [使用 SSIS 包升级向导升级 Integration Services 包](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="65f9b-129">For more information on package upgrade, see [Upgrade Integration Services Packages](install-windows/upgrade-integration-services-packages.md) and [Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md).</span></span>  
  
3.  <span data-ttu-id="65f9b-130">将项目部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="65f9b-130">Deploy the project to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="65f9b-131">有关详细信息，请参阅下面的说明：[将项目部署到 Integration Services 服务器](#deploy)。</span><span class="sxs-lookup"><span data-stu-id="65f9b-131">For more information, see the instructions below: [To deploy a project to the Integration Services Server](#deploy).</span></span>  
  
4.  <span data-ttu-id="65f9b-132">（可选）创建已部署项目的环境。</span><span class="sxs-lookup"><span data-stu-id="65f9b-132">(Optional) Create an environment for the deployed project.</span></span> <span data-ttu-id="65f9b-133">有关详细信息，请参阅 [创建和映射服务器环境](../../2014/integration-services/create-and-map-a-server-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="65f9b-133">For more information, see [Create and Map a Server Environment](../../2014/integration-services/create-and-map-a-server-environment.md).</span></span>  
  
##  <a name="to-convert-a-project-to-the-project-deployment-model"></a><a name="convert"></a><span data-ttu-id="65f9b-134">将项目转换为项目部署模型</span><span class="sxs-lookup"><span data-stu-id="65f9b-134">To convert a project to the project deployment model</span></span>  
  
1.  <span data-ttu-id="65f9b-135">在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中打开该项目，然后在解决方案资源管理器中，右键单击该项目并单击“转换为项目部署模型”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65f9b-135">Open the project in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], and then in Solution Explorer, right-click the project and click **Convert to Project Deployment Model**.</span></span>  
  
     <span data-ttu-id="65f9b-136">- 或 -</span><span class="sxs-lookup"><span data-stu-id="65f9b-136">-or-</span></span>  
  
     <span data-ttu-id="65f9b-137">从 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 的对象资源管理器中，右键单击“项目”\*\*\*\* 节点并选择“导入包”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65f9b-137">From Object Explorer in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], right-click the **Projects** node and select **Import Packages**.</span></span>  
  
2.  <span data-ttu-id="65f9b-138">完成向导。</span><span class="sxs-lookup"><span data-stu-id="65f9b-138">Complete the wizard.</span></span> <span data-ttu-id="65f9b-139">有关详细信息，请参阅 [Integration Services Project Conversion Wizard](../../2014/integration-services/integration-services-project-conversion-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="65f9b-139">For more information, see [Integration Services Project Conversion Wizard](../../2014/integration-services/integration-services-project-conversion-wizard.md).</span></span>  
  
##  <a name="to-deploy-a-project-to-the-integration-services-server"></a><a name="deploy"></a><span data-ttu-id="65f9b-140">将项目部署到 Integration Services 服务器</span><span class="sxs-lookup"><span data-stu-id="65f9b-140">To deploy a project to the Integration Services Server</span></span>  
  
1.  <span data-ttu-id="65f9b-141">在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]并打开项目，然后从 **“项目”** 菜单，选择 **“部署”** 以便启动 **“Integration Services 部署向导”**。</span><span class="sxs-lookup"><span data-stu-id="65f9b-141">Open the project in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], and then From the **Project** menu, select **Deploy** to launch the **Integration Services Deployment Wizard**.</span></span>  
  
     <span data-ttu-id="65f9b-142">- 或 -</span><span class="sxs-lookup"><span data-stu-id="65f9b-142">-or-</span></span>  
  
     <span data-ttu-id="65f9b-143">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 的对象资源管理器中，展开 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] > SSISDB\*\*\*\* 节点，并查找想要部署的项目的项目文件夹。</span><span class="sxs-lookup"><span data-stu-id="65f9b-143">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], expand the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] > **SSISDB** node in Object Explorer, and locate the Projects folder for the project you want to deploy.</span></span> <span data-ttu-id="65f9b-144">右键单击“项目”\*\*\*\* 文件夹，然后单击“部署项目”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65f9b-144">Right-click the **Projects** folder, and then click **Deploy Project**.</span></span>  
  
     <span data-ttu-id="65f9b-145">- 或 -</span><span class="sxs-lookup"><span data-stu-id="65f9b-145">-or-</span></span>  
  
     <span data-ttu-id="65f9b-146">在命令提示符下，从 **%ProgramFiles%\Microsoft SQL Server\110\DTS\Binn** 运行 **isdeploymentwizard.exe**。</span><span class="sxs-lookup"><span data-stu-id="65f9b-146">From the command prompt, run **isdeploymentwizard.exe** from **%ProgramFiles%\Microsoft SQL Server\110\DTS\Binn**.</span></span> <span data-ttu-id="65f9b-147">在 64 位计算机上， **%ProgramFiles(x86)%\Microsoft SQL Server\100\DTS\Binn**中还有 32 位版本的工具。</span><span class="sxs-lookup"><span data-stu-id="65f9b-147">On 64-bit computers, there is also a 32-bit version of the tool in **%ProgramFiles(x86)%\Microsoft SQL Server\100\DTS\Binn**.</span></span>  
  
2.  <span data-ttu-id="65f9b-148">在 **“选择源”** 页上，单击 **“项目部署文件”** 以便选择项目的部署文件。</span><span class="sxs-lookup"><span data-stu-id="65f9b-148">On the **Select Source** page, click **Project deployment file** to select the deployment file for the project.</span></span>  
  
     <span data-ttu-id="65f9b-149">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="65f9b-149">-OR-</span></span>  
  
     <span data-ttu-id="65f9b-150">单击 **“Integration Services 目录”** 以便选择已部署到 SSISDB 目录的项目。</span><span class="sxs-lookup"><span data-stu-id="65f9b-150">Click **Integration Services catalog** to select a project that has already been deployed to the SSISDB catalog.</span></span>  
  
3.  <span data-ttu-id="65f9b-151">完成向导。</span><span class="sxs-lookup"><span data-stu-id="65f9b-151">Complete the wizard.</span></span> <span data-ttu-id="65f9b-152">有关详细信息，请参阅 [Integration Services Deployment Wizard](../../2014/integration-services/integration-services-deployment-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="65f9b-152">For more information, see [Integration Services Deployment Wizard](../../2014/integration-services/integration-services-deployment-wizard.md).</span></span>  
  
  
