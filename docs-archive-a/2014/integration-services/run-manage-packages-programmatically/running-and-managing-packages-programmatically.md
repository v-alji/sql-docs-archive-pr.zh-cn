---
title: 以编程方式运行和管理包 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 1a08c75e-ce8c-45ee-81bd-32248bbdb2b2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0b07b0b98674fa17891dbbcb01ec42934c2a72e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688993"
---
# <a name="running-and-managing-packages-programmatically"></a><span data-ttu-id="f0abd-102">以编程方式运行和管理包</span><span class="sxs-lookup"><span data-stu-id="f0abd-102">Running and Managing Packages Programmatically</span></span>
  <span data-ttu-id="f0abd-103">如果您需要在开发环境之外管理和运行 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包，可以采用编程方式对包进行操作。</span><span class="sxs-lookup"><span data-stu-id="f0abd-103">If you need manage and run [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages outside the development environment, you can manipulate packages programmatically.</span></span> <span data-ttu-id="f0abd-104">如果采用这种方法，则您有多种选择：</span><span class="sxs-lookup"><span data-stu-id="f0abd-104">In this approach, you have a range of options:</span></span>  
  
-   <span data-ttu-id="f0abd-105">加载和运行现有包，不进行修改。</span><span class="sxs-lookup"><span data-stu-id="f0abd-105">Load and run an existing package without modification.</span></span>  
  
-   <span data-ttu-id="f0abd-106">加载现有包，对其进行重新配置（例如，针对一个不同的数据源），然后运行。</span><span class="sxs-lookup"><span data-stu-id="f0abd-106">Load an existing package, reconfigure it (for example, for a different data source), and run it.</span></span>  
  
-   <span data-ttu-id="f0abd-107">创建一个新包，添加并配置组件（逐个对象和属性），保存并运行。</span><span class="sxs-lookup"><span data-stu-id="f0abd-107">Create a new package, add and configure components object by object and property by property, save it, and run it.</span></span>  
  
 <span data-ttu-id="f0abd-108">您可以只编写几行代码，从客户端应用程序加载和运行现有包。</span><span class="sxs-lookup"><span data-stu-id="f0abd-108">You can load and run an existing package from a client application by writing only a few lines of code.</span></span>  
  
 <span data-ttu-id="f0abd-109">本节介绍并演示如何以编程方式运行现有包，以及如何从其他应用程序访问数据流的输出。</span><span class="sxs-lookup"><span data-stu-id="f0abd-109">This section describes and demonstrates how to run an existing package programmatically and how to access the output of the data flow from other applications.</span></span> <span data-ttu-id="f0abd-110">作为高级编程选项，可以按照[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]以编程方式生成包[主题中的说明，已编程方式逐行创建 ](../building-packages-programmatically/building-packages-programmatically.md) 包。</span><span class="sxs-lookup"><span data-stu-id="f0abd-110">As an advanced programming option, you can programmatically create an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package line by line as described in the topic, [Building Packages Programmatically](../building-packages-programmatically/building-packages-programmatically.md).</span></span>  
  
 <span data-ttu-id="f0abd-111">本节还讨论其他可以用编程方式执行的管理任务，用于管理存储的包、正在运行的包和包角色。</span><span class="sxs-lookup"><span data-stu-id="f0abd-111">This section also discusses other administrative tasks that you can perform programmatically to manage stored packages, running packages, and package roles.</span></span>  
  
## <a name="running-packages-on-the-integration-services-server"></a><span data-ttu-id="f0abd-112">在 Integration Services 服务器上运行包</span><span class="sxs-lookup"><span data-stu-id="f0abd-112">Running Packages on the Integration Services Server</span></span>  
 <span data-ttu-id="f0abd-113">将包部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器时，可以使用 <xref:Microsoft.SqlServer.Management.IntegrationServices> 命名空间以编程方式运行包。</span><span class="sxs-lookup"><span data-stu-id="f0abd-113">When you deploy packages to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, you can run the packages programmatically by using the <xref:Microsoft.SqlServer.Management.IntegrationServices> namespace.</span></span> <span data-ttu-id="f0abd-114">使用 .NET Framework 3.5 编译 Microsoft.SqlServer.Management.IntegrationServices 程序集。</span><span class="sxs-lookup"><span data-stu-id="f0abd-114">The Microsoft.SqlServer.Management.IntegrationServices assembly is compiled with .NET Framework 3.5.</span></span> <span data-ttu-id="f0abd-115">如果您正在生成 .NET Framework 4.0 应用程序，可能需要将程序集引用直接添加到项目文件。</span><span class="sxs-lookup"><span data-stu-id="f0abd-115">If you are building a .NET Framework 4.0 application, you might need to add the assembly reference directly to your project file.</span></span>  
  
 <span data-ttu-id="f0abd-116">您还可以使用该命名空间在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器上部署和管理 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="f0abd-116">You can also use the namespace to deploy and manage [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] projects on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="f0abd-117">有关命名空间和代码片段的概述，请参阅 blogs.msdn.com 上的博客文章 [SSIS 目录托管对象模型一瞥](https://techcommunity.microsoft.com/t5/sql-server-integration-services/a-glimpse-of-the-ssis-catalog-managed-object-model/ba-p/387892)。</span><span class="sxs-lookup"><span data-stu-id="f0abd-117">For an overview of the namespace and code snippets, see the blog entry, [A Glimpse of the SSIS Catalog Managed Object Model](https://techcommunity.microsoft.com/t5/sql-server-integration-services/a-glimpse-of-the-ssis-catalog-managed-object-model/ba-p/387892), on blogs.msdn.com.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f0abd-118">本节内容</span><span class="sxs-lookup"><span data-stu-id="f0abd-118">In This Section</span></span>  
 [<span data-ttu-id="f0abd-119">了解本地执行与远程执行之间的差异</span><span class="sxs-lookup"><span data-stu-id="f0abd-119">Understanding the Differences between Local and Remote Execution</span></span>](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md)  
 <span data-ttu-id="f0abd-120">讨论在本地执行包和在服务器上执行包的重大差别。</span><span class="sxs-lookup"><span data-stu-id="f0abd-120">Discusses critical differences between executing a package locally or on the server.</span></span>  
  
 [<span data-ttu-id="f0abd-121">以编程方式加载和运行本地包</span><span class="sxs-lookup"><span data-stu-id="f0abd-121">Loading and Running a Local Package Programmatically</span></span>](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)  
 <span data-ttu-id="f0abd-122">介绍如何在本地计算机上从客户端应用程序执行现有包。</span><span class="sxs-lookup"><span data-stu-id="f0abd-122">Describes how to execute an existing package from a client application on the local computer.</span></span>  
  
 [<span data-ttu-id="f0abd-123">以编程方式加载和运行远程包</span><span class="sxs-lookup"><span data-stu-id="f0abd-123">Loading and Running a Remote Package Programmatically</span></span>](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)  
 <span data-ttu-id="f0abd-124">介绍如何从客户端应用程序执行现有包以及如何确保包在服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="f0abd-124">Describes how to execute an existing package from a client application and to ensure that the package runs on the server.</span></span>  
  
 [<span data-ttu-id="f0abd-125">加载本地包的输出</span><span class="sxs-lookup"><span data-stu-id="f0abd-125">Loading the Output of a Local Package</span></span>](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
 <span data-ttu-id="f0abd-126">介绍如何在本地计算机上执行包，以及如何使用 DataReader 目标和 DtsClient 命名空间将数据流输出加载到客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="f0abd-126">Describes how to execute a package on the local computer and how to load the data flow output into a client application by using the DataReader destination and the DtsClient namespace.</span></span>  
  
 [<span data-ttu-id="f0abd-127">以编程方式枚举可用的包</span><span class="sxs-lookup"><span data-stu-id="f0abd-127">Enumerating Available Packages Programmatically</span></span>](../run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
 <span data-ttu-id="f0abd-128">介绍如何发现由 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务管理的可用包。</span><span class="sxs-lookup"><span data-stu-id="f0abd-128">Describes how to discover available packages that are managed by the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service.</span></span>  
  
 [<span data-ttu-id="f0abd-129">以编程方式管理包和文件夹</span><span class="sxs-lookup"><span data-stu-id="f0abd-129">Managing Packages and Folders Programmatically</span></span>](../run-manage-packages-programmatically/managing-packages-and-folders-programmatically.md)  
 <span data-ttu-id="f0abd-130">介绍如何创建、重命名和删除包与文件夹。</span><span class="sxs-lookup"><span data-stu-id="f0abd-130">Describes how to create, rename, and delete both packages and folders.</span></span>  
  
 [<span data-ttu-id="f0abd-131">以编程方式管理正在运行的包</span><span class="sxs-lookup"><span data-stu-id="f0abd-131">Managing Running Packages Programmatically</span></span>](../run-manage-packages-programmatically/managing-running-packages-programmatically.md)  
 <span data-ttu-id="f0abd-132">介绍如何列出当前正在运行的包，如何检查其属性以及如何停止正在运行的包。</span><span class="sxs-lookup"><span data-stu-id="f0abd-132">Describes how to list packages that are currently running, examine their properties, and stop a running package.</span></span>  
  
 [<span data-ttu-id="f0abd-133">以编程方式管理包角色（SSIS 服务）</span><span class="sxs-lookup"><span data-stu-id="f0abd-133">Managing Package Roles Programmatically &#40;SSIS Service&#41;</span></span>](../run-manage-packages-programmatically/managing-package-roles-programmatically-ssis-service.md)  
 <span data-ttu-id="f0abd-134">介绍如何获取或设置有关分配给包或文件夹的角色的信息。</span><span class="sxs-lookup"><span data-stu-id="f0abd-134">Describes how to get or set information about the roles assigned to a package or a folder.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f0abd-135">参考</span><span class="sxs-lookup"><span data-stu-id="f0abd-135">Reference</span></span>  
 [<span data-ttu-id="f0abd-136">Integration Services 错误和消息引用</span><span class="sxs-lookup"><span data-stu-id="f0abd-136">Integration Services Error and Message Reference</span></span>](../integration-services-error-and-message-reference.md)  
 <span data-ttu-id="f0abd-137">列出预定义的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 错误代码及其符号名称和说明。</span><span class="sxs-lookup"><span data-stu-id="f0abd-137">Lists the predefined [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] error codes with their symbolic names and descriptions.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f0abd-138">相关章节</span><span class="sxs-lookup"><span data-stu-id="f0abd-138">Related Sections</span></span>  
 [<span data-ttu-id="f0abd-139">用脚本扩展包</span><span class="sxs-lookup"><span data-stu-id="f0abd-139">Extending Packages with Scripting</span></span>](../extending-packages-scripting/extending-packages-with-scripting.md)  
 <span data-ttu-id="f0abd-140">讨论如何使用脚本任务扩展控制流，以及如何使用脚本组件扩展数据流。</span><span class="sxs-lookup"><span data-stu-id="f0abd-140">Discusses how to extend the control flow by using the Script task, and how to extend the data flow by using the Script component.</span></span>  
  
 [<span data-ttu-id="f0abd-141">用自定义对象扩展包</span><span class="sxs-lookup"><span data-stu-id="f0abd-141">Extending Packages with Custom Objects</span></span>](../extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
 <span data-ttu-id="f0abd-142">讨论如何创建用于多个包的编程自定义任务、数据流组件以及其他包对象。</span><span class="sxs-lookup"><span data-stu-id="f0abd-142">Discusses how to create program custom tasks, data flow components, and other package objects for use in multiple packages.</span></span>  
  
 [<span data-ttu-id="f0abd-143">以编程方式生成包</span><span class="sxs-lookup"><span data-stu-id="f0abd-143">Building Packages Programmatically</span></span>](../building-packages-programmatically/building-packages-programmatically.md)  
 <span data-ttu-id="f0abd-144">讨论如何以编程方式创建、配置和保存 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="f0abd-144">Discusses how to create, configure, and save [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages programmatically.</span></span>  
  
<span data-ttu-id="f0abd-145">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="f0abd-145">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="f0abd-146">若要从 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="f0abd-146">For the latest downloads, articles, samples, and videos from [!INCLUDE[msCoName](../../includes/msconame-md.md)], as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="f0abd-147">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="f0abd-147">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="f0abd-148">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="f0abd-148">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0abd-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f0abd-149">See Also</span></span>  
 [<span data-ttu-id="f0abd-150">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="f0abd-150">SQL Server Integration Services</span></span>](../sql-server-integration-services.md)  
  
  
