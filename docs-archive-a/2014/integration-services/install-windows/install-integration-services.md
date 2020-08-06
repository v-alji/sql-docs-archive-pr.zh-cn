---
title: 安装 Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, installing
- SSIS, installing
- installing Integration Services, about installing Integration Services
- SQL Server Integration Services, installing
- Setup [Integration Services], about installing Integration Services
- installing Integration Services
- Setup [Integration Services]
ms.assetid: bd20fd3a-414b-4581-959d-ebba4ddf5a55
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4a5d1e12af23c58ad42154455718d0e99cf8b399
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586888"
---
# <a name="install-integration-services"></a><span data-ttu-id="8a831-102">安装集成服务</span><span class="sxs-lookup"><span data-stu-id="8a831-102">Install Integration Services</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8a831-103">提供了单个安装程序来安装其包括 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]在内的任一组件或所有组件。</span><span class="sxs-lookup"><span data-stu-id="8a831-103">provides a single Setup program to install any or all of its components, including [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="8a831-104">通过安装程序，可在单台计算机上将 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件一起安装，也可以单独安装。</span><span class="sxs-lookup"><span data-stu-id="8a831-104">Through Setup, you can install [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] with or without other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components on a single computer.</span></span>  
  
 <span data-ttu-id="8a831-105">本主题重点介绍在安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]之前应了解的重要注意事项。</span><span class="sxs-lookup"><span data-stu-id="8a831-105">This topic highlights important considerations that you should know before you install [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="8a831-106">本主题中的信息将帮助您评估安装选项，以便您可以选择使安装成功。</span><span class="sxs-lookup"><span data-stu-id="8a831-106">Information in this topic will help you evaluate the installation options so that you can make selections that result in a successful installation.</span></span>  
  
 <span data-ttu-id="8a831-107">本主题不包括有关启动安装程序、使用安装向导或从命令行运行安装程序的说明。</span><span class="sxs-lookup"><span data-stu-id="8a831-107">This topic does not include instructions for starting Setup, using the Setup Wizard, or running Setup from the command line.</span></span> <span data-ttu-id="8a831-108">有关如何启动安装程序并选择要安装的组件的分步说明，请参阅[SQL Server 2014 的快速入门安装](../../getting-started/quick-start-installation-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="8a831-108">For step-by-step instructions on how to start Setup and select components to install, see [Quick-Start Installation of SQL Server 2014](../../getting-started/quick-start-installation-of-sql-server-2014.md).</span></span> <span data-ttu-id="8a831-109">有关用于安装的命令行选项的信息 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ，请参阅[从命令提示符安装 SQL Server 2014](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)。</span><span class="sxs-lookup"><span data-stu-id="8a831-109">For information about command-line options for installing [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], see [Install SQL Server 2014 from the Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span>  
  
## <a name="preparing-to-install-integration-services"></a><span data-ttu-id="8a831-110">正在准备安装 Integration Services</span><span class="sxs-lookup"><span data-stu-id="8a831-110">Preparing to Install Integration Services</span></span>  
 <span data-ttu-id="8a831-111">安装之前 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ，请查看以下要求：</span><span class="sxs-lookup"><span data-stu-id="8a831-111">Before you install [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], review the following requirements:</span></span>  
  
-   [<span data-ttu-id="8a831-112">安装 SQL Server 2014 的硬件和软件要求</span><span class="sxs-lookup"><span data-stu-id="8a831-112">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
-   [<span data-ttu-id="8a831-113">系统配置检查器的检查参数</span><span class="sxs-lookup"><span data-stu-id="8a831-113">Check Parameters for the System Configuration Checker</span></span>](../../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md)  
  
-   [<span data-ttu-id="8a831-114">安装 SQL Server 的安全注意事项</span><span class="sxs-lookup"><span data-stu-id="8a831-114">Security Considerations for a SQL Server Installation</span></span>](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
## <a name="selecting-an-integration-services-configuration"></a><span data-ttu-id="8a831-115">选择 Integration Services 配置</span><span class="sxs-lookup"><span data-stu-id="8a831-115">Selecting an Integration Services Configuration</span></span>  
 <span data-ttu-id="8a831-116">可以按下列配置安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]：</span><span class="sxs-lookup"><span data-stu-id="8a831-116">You can install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] in the following configurations:</span></span>  
  
-   <span data-ttu-id="8a831-117">可以在没有旧 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的计算机上安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8a831-117">You can install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] on a computer that has no previous instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="8a831-118">可以将 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 与 [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] 和 [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)]的现有实例并行安装。</span><span class="sxs-lookup"><span data-stu-id="8a831-118">You can install [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] side-by-side with an existing instance of [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] and [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)].</span></span>  
  
     <span data-ttu-id="8a831-119">当您在已安装了这些 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 早期版本之一的计算机上升级到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 时， [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 将与该早期版本并行安装。</span><span class="sxs-lookup"><span data-stu-id="8a831-119">When you upgrade to [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] on a machine that has one of these earlier versions of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] already installed, [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] is installed side-by-side with the earlier version.</span></span>  
  
     <span data-ttu-id="8a831-120">有关升级的详细信息 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]，请参阅 [升级集成服务](upgrade-integration-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8a831-120">For more information on upgrading [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], see [Upgrade Integration Services](upgrade-integration-services.md).</span></span> <span data-ttu-id="8a831-121">有关早期版本的向后兼容性详细信息， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]请参阅 [集成服务向后兼容性](../integration-services-backward-compatibility.md)。</span><span class="sxs-lookup"><span data-stu-id="8a831-121">For information about backward compatibility with earlier versions of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], see [Integration Services Backward Compatibility](../integration-services-backward-compatibility.md).</span></span>  
  
## <a name="installing-integration-services"></a><span data-ttu-id="8a831-122">安装集成服务</span><span class="sxs-lookup"><span data-stu-id="8a831-122">Installing Integration Services</span></span>  
 <span data-ttu-id="8a831-123">在查看 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的安装要求并确保计算机满足这些要求之后，就可以安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]了。</span><span class="sxs-lookup"><span data-stu-id="8a831-123">After you review the installation requirements for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and ensure that your computer meets those requirements, you are ready to install [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8a831-124">在以前版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，在您安装了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 后，默认情况下 Users 组中的所有用户都已对 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务具有访问权限。</span><span class="sxs-lookup"><span data-stu-id="8a831-124">In previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], by default when you installed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] all users in the Users group had access to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="8a831-125">在您安装 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]时，用户无权访问 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="8a831-125">When you install [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], users do not have access to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="8a831-126">该服务默认是安全的。</span><span class="sxs-lookup"><span data-stu-id="8a831-126">The service is secure by default.</span></span> <span data-ttu-id="8a831-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]安装后， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理员必须运行 DCOM 配置工具 ( # A0) 向特定用户授予**SQL Server Integration Services 12.0**的访问权限。</span><span class="sxs-lookup"><span data-stu-id="8a831-127">After [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrator must run the DCOM Configuration tool (Dcomcnfg.exe) to grant specific users access to **SQL Server Integration Services 12.0**.</span></span>  
>   
>  <span data-ttu-id="8a831-128">有关如何授予权限的说明，请参阅 [Grant Permissions to Integration Services Service](../grant-permissions-to-integration-services-service.md)。</span><span class="sxs-lookup"><span data-stu-id="8a831-128">For instructions on how to grant permissions, see [Grant Permissions to Integration Services Service](../grant-permissions-to-integration-services-service.md).</span></span>  
  
 <span data-ttu-id="8a831-129">如果使用安装向导安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]，则将使用一系列页面来指定组件和选项。</span><span class="sxs-lookup"><span data-stu-id="8a831-129">If you are using the Setup Wizard to install [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], you will use a series of pages to specify components and options.</span></span> <span data-ttu-id="8a831-130">以下是安装向导中的页面，你选择的选项会影响你安装的选择 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 建议：</span><span class="sxs-lookup"><span data-stu-id="8a831-130">The following are pages in the Setup Wizard where the options that you select affect your installation of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] with selection recommendations:</span></span>  
  
-   <span data-ttu-id="8a831-131">**功能选择**</span><span class="sxs-lookup"><span data-stu-id="8a831-131">**Feature Selection**</span></span>  
  
     <span data-ttu-id="8a831-132">选择 **集成服务** 可安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务并可在设计环境之外运行包。</span><span class="sxs-lookup"><span data-stu-id="8a831-132">Select **Integration Services** to install the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service and to run packages outside the design environment.</span></span>  
  
     <span data-ttu-id="8a831-133">若要进行 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]以及用于开发和管理包的工具和文档的完整安装，请同时选择 **集成服务** 及以下 **“共享功能”**：</span><span class="sxs-lookup"><span data-stu-id="8a831-133">For a complete installation of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], together with the tools and documentation for developing and managing packages, select both **Integration Services** and the following **Shared Features**:</span></span>  
  
    -   <span data-ttu-id="8a831-134">**SQL Server Data Tools** ，以便安装用于设计包的工具。</span><span class="sxs-lookup"><span data-stu-id="8a831-134">**SQL Server Data Tools** to install the tools for designing packages.</span></span>  
  
    -   <span data-ttu-id="8a831-135">**管理工具 – 完整** 以便安装 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 用于管理包的工具。</span><span class="sxs-lookup"><span data-stu-id="8a831-135">**Management Tools - Complete** to install [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] for managing packages.</span></span>  
  
    -   <span data-ttu-id="8a831-136">**客户端工具 SDK** ，以便安装用于 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 编程的托管程序集。</span><span class="sxs-lookup"><span data-stu-id="8a831-136">**Client Tools SDK** to install managed assemblies for [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] programming.</span></span>  
  
     <span data-ttu-id="8a831-137">许多数据仓库解决方案还要求安装其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件，如 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8a831-137">Many data warehousing solutions also require the installation of additional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components, such as the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8a831-138">如果选择了可在安装向导的“功能选择”页上选择进行安装的某些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件，则会安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 组件的部分子集  。</span><span class="sxs-lookup"><span data-stu-id="8a831-138">Some [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components that you can select for installation on the **Feature Selection** page of the Setup Wizard install a partial subset of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components.</span></span> <span data-ttu-id="8a831-139">这些组件对特定任务是有用的，但 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 功能将受到限制。</span><span class="sxs-lookup"><span data-stu-id="8a831-139">These components are useful for specific tasks, but the functionality of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] will be limited.</span></span> <span data-ttu-id="8a831-140">例如， **“数据库引擎服务”** 选项将安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 导入和导出向导所需的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件。</span><span class="sxs-lookup"><span data-stu-id="8a831-140">For example, the **Database Engine Services** option installs the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard.</span></span> <span data-ttu-id="8a831-141">**“SQL Server Data Tools”** 选项将安装在设计包时所需的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 组件，但不会安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务，并且不能在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]之外运行包。</span><span class="sxs-lookup"><span data-stu-id="8a831-141">The **SQL Server Data Tools** option installs the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components required to design a package, but the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is not installed and you cannot run packages outside of [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="8a831-142">为确保完整安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]，必须在 **“功能选择”** 页上选择“ **集成服务** ”。</span><span class="sxs-lookup"><span data-stu-id="8a831-142">To ensure a complete installation of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], you must select **Integration Services** on the **Feature Selection** page.</span></span>  
  
     <span data-ttu-id="8a831-143">**在 64 位计算机上安装** 在 64 位计算机上安装，选择 **集成服务** ，则只安装 64 位运行时和工具。</span><span class="sxs-lookup"><span data-stu-id="8a831-143">**Installing on a 64-bit Computer** On a 64-bit computer, selecting **Integration Services** installs only the 64-bit runtime and tools.</span></span> <span data-ttu-id="8a831-144">如果必须以 32 位模式来运行包，还必须选择其他选项以安装 32 位运行时和工具：</span><span class="sxs-lookup"><span data-stu-id="8a831-144">If you have to run packages in 32-bit mode, you must also select an additional option to install the 32-bit runtime and tools:</span></span>  
  
    -   <span data-ttu-id="8a831-145">如果64位计算机运行的是 x86 操作系统，请选择 " **SQL Server Data Tools** " 或 "**管理工具-完整**"。</span><span class="sxs-lookup"><span data-stu-id="8a831-145">If the 64-bit computer is running the x86 operating system, select **SQL Server Data Tools** or **Management Tools - Complete**.</span></span>  
  
    -   <span data-ttu-id="8a831-146">如果64位计算机运行的是 [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)] 操作系统，请选择 "**管理工具-完整**"。</span><span class="sxs-lookup"><span data-stu-id="8a831-146">If the 64-bit computer is running the [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)] operating system, select **Management Tools - Complete**.</span></span>  
  
     <span data-ttu-id="8a831-147">**为 ETL 安装专用服务器** 若要对提取、转换和加载 (ETL) 过程使用专用服务器，建议你在安装 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 时安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]的本地实例。</span><span class="sxs-lookup"><span data-stu-id="8a831-147">**Installing on a Dedicated Server for ETL** To use a dedicated server for extraction, transformation, and loading (ETL) processes, we recommend that you install a local instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] when you install [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="8a831-148">通常将包存储在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例中，并使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理对这些包进行计划。</span><span class="sxs-lookup"><span data-stu-id="8a831-148">typically stores packages in an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and relies on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent for scheduling those packages.</span></span> <span data-ttu-id="8a831-149">如果 ETL 服务器上没有 [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例，则必须通过具有 [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例的服务器计划或运行包。</span><span class="sxs-lookup"><span data-stu-id="8a831-149">If the ETL server does not have an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], you will have to schedule or run packages from a server that does have an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="8a831-150">这表示这些包不会在 ETL 服务器上运行，而是在其启动时所在的服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="8a831-150">This means that the packages will not be running on the ETL server, but instead on the server from which they were started.</span></span> <span data-ttu-id="8a831-151">因此，专用 ETL 服务器的资源不会按预期方式使用。</span><span class="sxs-lookup"><span data-stu-id="8a831-151">As a result, the resources of the dedicated ETL server are not being used as intended.</span></span> <span data-ttu-id="8a831-152">而且，其他服务器的资源可能会受到 ETL 进程运行的影响</span><span class="sxs-lookup"><span data-stu-id="8a831-152">Furthermore, the resources of other servers may be strained by the running ETL processes</span></span>  
  
-   <span data-ttu-id="8a831-153">**Instance Configuration**</span><span class="sxs-lookup"><span data-stu-id="8a831-153">**Instance Configuration**</span></span>  
  
     <span data-ttu-id="8a831-154">在 **“实例配置”** 页上做出的任何选择都不会影响 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 或 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="8a831-154">Any selection that you make on the **Instance Configuration** page does not affect [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] or the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service.</span></span>  
  
     <span data-ttu-id="8a831-155">在一台计算机上只能安装一个 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务实例。</span><span class="sxs-lookup"><span data-stu-id="8a831-155">You can only install one instance of the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service on a computer.</span></span> <span data-ttu-id="8a831-156">可使用计算机名称连接到该服务。</span><span class="sxs-lookup"><span data-stu-id="8a831-156">You connect to the service by using the computer name.</span></span>  
  
     <span data-ttu-id="8a831-157">默认情况下， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务将配置为管理存储在与 **同时安装的数据库引擎实例的** msdb [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]数据库中的包。</span><span class="sxs-lookup"><span data-stu-id="8a831-157">By default, the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is configured to manage packages that are stored in the **msdb** database in the instance of the Database Engine that is installed at the same time as [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="8a831-158">如果数据库引擎实例未与 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]同时安装，则 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务将配置为管理存储在本地默认 **实例的** msdb [!INCLUDE[ssDE](../../includes/ssde-md.md)]数据库中的包。</span><span class="sxs-lookup"><span data-stu-id="8a831-158">If an instance of the Database Engine is not installed at the same time as [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is configured to manage packages that are stored in the **msdb** database of the local, default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="8a831-159">若要管理存储在 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的某个命名实例或远程实例中的包或存储在 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的多个实例中的包，必须修改配置文件。</span><span class="sxs-lookup"><span data-stu-id="8a831-159">To manage packages that are stored in a named instance or a remote instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], or in multiple instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], you have to modify the configuration file.</span></span> <span data-ttu-id="8a831-160">有关如何修改此配置文件的详细信息，请参阅[配置 Integration Services Service (SSIS 服务)](../service/integration-services-service-ssis-service.md)。</span><span class="sxs-lookup"><span data-stu-id="8a831-160">For more information about how to modify this configuration file, see [Configuring the Integration Services Service &#40;SSIS Service&#41;](../service/integration-services-service-ssis-service.md).</span></span>  
  
-   <span data-ttu-id="8a831-161">**服务器配置**</span><span class="sxs-lookup"><span data-stu-id="8a831-161">**Server Configuration**</span></span>  
  
     <span data-ttu-id="8a831-162">在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] “服务器配置” **页的** “服务帐户” **选项卡上查看** 服务的设置。</span><span class="sxs-lookup"><span data-stu-id="8a831-162">Review the settings for the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service on the **Service Accounts** tab of the **Server Configuration** page.</span></span>  
  
     <span data-ttu-id="8a831-163">如果安装了 Windows 7 或 Windows Server 2008 R2，则 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务将注册为在 NT Services\MsDtsServer120 虚拟帐户下运行，并且**启动类型**为 "**自动**"。</span><span class="sxs-lookup"><span data-stu-id="8a831-163">If Windows 7 or Windows Server 2008 R2 is installed, the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is registered to run under the NT Services\MsDtsServer120 virtual account, and the **Startup Type** is **Automatic**.</span></span>  <span data-ttu-id="8a831-164">您不必输入内置虚拟帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="8a831-164">You do not have to enter a password for the virtual account.</span></span> <span data-ttu-id="8a831-165">如果安装了 Microsoft Vista 或 Windows Server 2008，则 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务将注册为在内置网络服务帐户下运行，并且 **启动类型** 为 **自动**。</span><span class="sxs-lookup"><span data-stu-id="8a831-165">If Microsoft Vista or Windows Server 2008 is installed, the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is registered to run under the built-in Network Service account, and the **Startup Type** is **Automatic**.</span></span> <span data-ttu-id="8a831-166">您不必输入内置 Network Service 帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="8a831-166">You do not have to enter a password for the built-in Network Service account.</span></span>  
  
 <span data-ttu-id="8a831-167">默认情况下，在全新安装中， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 配置为不将与运行包相关的事件记录到应用程序事件日志中。</span><span class="sxs-lookup"><span data-stu-id="8a831-167">By default, in a new installation, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] is configured not to log events that are related to the running of packages to the Application event log.</span></span> <span data-ttu-id="8a831-168">使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的数据收集器功能时，此设置可防止生成太多事件日志项。</span><span class="sxs-lookup"><span data-stu-id="8a831-168">This setting prevents too many event log entries when you use the Data Collector feature of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="8a831-169">未记录的事件是，EventID 12288“包已启动”和 EventID 12289“包已成功完成”。</span><span class="sxs-lookup"><span data-stu-id="8a831-169">The events that are not logged are EventID 12288, "Package started," and EventID 12289, "Package finished successfully."</span></span> <span data-ttu-id="8a831-170">若要将这些事件记录到应用程序事件日志中，请打开注册表以进行编辑。</span><span class="sxs-lookup"><span data-stu-id="8a831-170">To log these events to the Application event log, open the registry for editing.</span></span> <span data-ttu-id="8a831-171">然后在注册表中，找到 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\SSIS 节点，并将 LogPackageExecutionToEventLog 设置的 DWORD 值从 0 更改为 1。</span><span class="sxs-lookup"><span data-stu-id="8a831-171">Then, in the registry, locate the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\SSIS node, and change the DWORD value of the LogPackageExecutionToEventLog setting from 0 to 1.</span></span>  
  
## <a name="understanding-the-integration-services-service"></a><span data-ttu-id="8a831-172">了解 Integration Services 服务</span><span class="sxs-lookup"><span data-stu-id="8a831-172">Understanding the Integration Services Service</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="8a831-173">安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="8a831-173">installs the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service.</span></span>  
  
 <span data-ttu-id="8a831-174">如果在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] “功能选择” **页上选择“** 集成服务 **”选项，则会安装** 服务。</span><span class="sxs-lookup"><span data-stu-id="8a831-174">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is installed when you select the **Integration Services** option on the **Feature Selection** page.</span></span> <span data-ttu-id="8a831-175">如果接受 **“服务器配置”** 页上的默认设置，则会启用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务，且 **“启动类型”** 为 **“自动”**。</span><span class="sxs-lookup"><span data-stu-id="8a831-175">When you accept the default settings on the **Server Configuration** page, the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is enabled and its **Startup Type** is **Automatic**.</span></span>  
  
 <span data-ttu-id="8a831-176">在一台计算机上可以只安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务的一个实例。</span><span class="sxs-lookup"><span data-stu-id="8a831-176">You can only install a single instance of the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service on a computer.</span></span> <span data-ttu-id="8a831-177">该服务并不特定于具体的数据库引擎实例。</span><span class="sxs-lookup"><span data-stu-id="8a831-177">The service is not specific to a particular instance of the Database Engine.</span></span> <span data-ttu-id="8a831-178">可使用运行该服务的计算机的名称连接到该服务。</span><span class="sxs-lookup"><span data-stu-id="8a831-178">You connect to the service by using the name of the computer on which the service is running.</span></span>  
  
## <a name="installing-integration-services-on-64-bit-computers"></a><span data-ttu-id="8a831-179">在 64 位计算机上安装 Integration Services</span><span class="sxs-lookup"><span data-stu-id="8a831-179">Installing Integration Services on 64-bit Computers</span></span>  
  
### <a name="integration-services-features-installed-on-64-bit-computers"></a><span data-ttu-id="8a831-180">安装在 64 位计算机上的 Integration Services 功能</span><span class="sxs-lookup"><span data-stu-id="8a831-180">Integration Services Features Installed on 64-bit Computers</span></span>  
 <span data-ttu-id="8a831-181">安装程序将根据您选择的安装选项安装各种 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 功能：</span><span class="sxs-lookup"><span data-stu-id="8a831-181">Setup installs various [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] features based on the setup options that you select:</span></span>  
  
-   <span data-ttu-id="8a831-182">安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时，如果选择安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ，安装程序将安装所有可用的 64 位 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 功能和工具。</span><span class="sxs-lookup"><span data-stu-id="8a831-182">When you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and select [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] for installation, Setup installs all available 64-bit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] features and tools.</span></span>  
  
-   <span data-ttu-id="8a831-183">如果需要 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 设计时功能，还必须安装 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8a831-183">If you require [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] design-time features, you must also install [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="8a831-184">如果需要 32 位版本的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 运行时和工具，以便能以 32 位模式运行某些包，还必须安装 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8a831-184">If you require 32-bit versions of the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] runtime and tools to run certain packages in 32-bit mode, you must also install [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="8a831-185">64 位功能安装在 **Program Files** 目录下，而 32 位功能单独安装在 **Program Files (x86)** 目录下。</span><span class="sxs-lookup"><span data-stu-id="8a831-185">64-bit features are installed under the **Program Files** directory, and 32-bit features are installed separately under the **Program Files (x86)** directory.</span></span> <span data-ttu-id="8a831-186">（这种行为并不特定于 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]）。</span><span class="sxs-lookup"><span data-stu-id="8a831-186">(This behavior is not specific to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] or to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="8a831-187">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 64 位操作系统上不支持 [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)] 包的 32 位开发环境，因此不能将其安装在 [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)] 服务器上。</span><span class="sxs-lookup"><span data-stu-id="8a831-187">, the 32-bit development environment for [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, is not supported on the [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)] 64-bit operating system and is not installed on [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)] servers.</span></span>  
  
  