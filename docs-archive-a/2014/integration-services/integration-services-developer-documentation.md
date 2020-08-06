---
title: 开发人员&#39;指南 (Integration Services) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Integration Services, programming
- SSIS, programming
- SQL Server Integration Services, programming
- packages [Integration Services], programming
ms.assetid: 60fe148b-a7c4-4289-ae3e-2e949fc1886c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c16ec1a21cf7ebb711f6d3996eb6239ea052c83c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589755"
---
# <a name="developer39s-guide-integration-services"></a><span data-ttu-id="e79b3-102">开发人员&#39;指南 (Integration Services) </span><span class="sxs-lookup"><span data-stu-id="e79b3-102">Developer&#39;s Guide (Integration Services)</span></span>
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="e79b3-103">包含一个完全重写的对象模型，已使用使用功能改善了该模型，以使包扩展和编程更加方便、灵活和强大。</span><span class="sxs-lookup"><span data-stu-id="e79b3-103">includes a completely rewritten object model, which has been enhanced with many features that make extending and programming packages easier, more flexible, and more powerful.</span></span> <span data-ttu-id="e79b3-104">开发人员几乎可以对 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包进行全方位的扩展和编程。</span><span class="sxs-lookup"><span data-stu-id="e79b3-104">Developers can extend and program almost every aspect of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span>  
  
 <span data-ttu-id="e79b3-105">作为 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 开发人员，您有两种基本的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 编程方法可选用：</span><span class="sxs-lookup"><span data-stu-id="e79b3-105">As an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] developer, there are two fundamental approaches that you can take to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] programming:</span></span>  
  
-   <span data-ttu-id="e79b3-106">您可以通过编写 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中可用的组件来扩展包，以在包中提供自定义功能。</span><span class="sxs-lookup"><span data-stu-id="e79b3-106">You can extend packages by writing components that become available within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to provide custom functionality in a package.</span></span>  
  
-   <span data-ttu-id="e79b3-107">您可以用编程方式从您自己的应用程序创建、配置和运行包。</span><span class="sxs-lookup"><span data-stu-id="e79b3-107">You can create, configure, and run packages programmatically from your own applications.</span></span>  
  
 <span data-ttu-id="e79b3-108">如果觉得 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中的内置组件不能满足要求，可以编写自己的扩展代码来扩展 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 的功能。</span><span class="sxs-lookup"><span data-stu-id="e79b3-108">If you find that the built-in components in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] do not meet your requirements, you can extend the power of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] by coding your own extensions.</span></span> <span data-ttu-id="e79b3-109">如果采用这种方法，则有两种不同的选择：</span><span class="sxs-lookup"><span data-stu-id="e79b3-109">In this approach, you have two discrete options:</span></span>  
  
-   <span data-ttu-id="e79b3-110">对于单个包中的即席使用，可以通过在脚本任务中编写代码来创建自定义任务，或通过在脚本组件中编写代码来创建可配置为源、转换或目标的自定义数据流组件。</span><span class="sxs-lookup"><span data-stu-id="e79b3-110">For ad hoc use in a single package, you can create a custom task by writing code in the Script task, or a custom data flow component by writing code in the Script component, which you can configure as a source, transformation, or destination.</span></span> <span data-ttu-id="e79b3-111">这些功能强大的包装可为您编写基础结构代码，使您可将注意力集中于开发您自己的自定义功能；但这些代码较难在别处重用。</span><span class="sxs-lookup"><span data-stu-id="e79b3-111">These powerful wrappers write the infrastructure code for you and let you focus exclusively on developing your custom functionality; however, they are not easily reusable elsewhere.</span></span>  
  
-   <span data-ttu-id="e79b3-112">对于在多个包中使用时，可以创建自定义 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 扩展插件，如连接管理器、任务、枚举器、日志提供程序和数据流组件。</span><span class="sxs-lookup"><span data-stu-id="e79b3-112">For use in multiple packages, you can create custom [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] extensions such as connection managers, tasks, enumerators, log providers, and data flow components.</span></span> <span data-ttu-id="e79b3-113">托管 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 对象模型包含一些基类，这些基类可作为开发自定义扩展插件的基础，使开发更加方便。</span><span class="sxs-lookup"><span data-stu-id="e79b3-113">The managed [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] object model contains base classes that provide a starting point and make developing custom extensions easier than ever.</span></span>  
  
 <span data-ttu-id="e79b3-114">如果要动态创建包，或在开发环境外管理并运行 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包，则可以采用编程方式来操作包。</span><span class="sxs-lookup"><span data-stu-id="e79b3-114">If you want to create packages dynamically, or to manage and run [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages outside the development environment, you can manipulate packages programmatically.</span></span> <span data-ttu-id="e79b3-115">您不但可以加载、修改和运行现有包，还可以用编程方式创建和运行全新的包。</span><span class="sxs-lookup"><span data-stu-id="e79b3-115">You can load, modify, and run existing packages, or you can create and run entirely new packages programmatically.</span></span> <span data-ttu-id="e79b3-116">如果采用这种方法，则有一系列选择：</span><span class="sxs-lookup"><span data-stu-id="e79b3-116">In this approach, you have a continuous range of options:</span></span>  
  
-   <span data-ttu-id="e79b3-117">加载和运行现有包，不进行修改。</span><span class="sxs-lookup"><span data-stu-id="e79b3-117">Load and run an existing package without modification.</span></span>  
  
-   <span data-ttu-id="e79b3-118">加载现有包，对其进行重新配置（例如，指定一个不同的数据源），然后运行。</span><span class="sxs-lookup"><span data-stu-id="e79b3-118">Load an existing package, reconfigure it (for example, specify a different data source), and run it.</span></span>  
  
-   <span data-ttu-id="e79b3-119">创建一个新包，添加并配置组件（逐个对象和属性进行更改），保存并运行。</span><span class="sxs-lookup"><span data-stu-id="e79b3-119">Create a new package, add and configure components, making changes object by object and property by property, save it, and then run it.</span></span>  
  
 <span data-ttu-id="e79b3-120">本节介绍这些 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 编程方法，并用示例加以说明。</span><span class="sxs-lookup"><span data-stu-id="e79b3-120">These approaches to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] programming are described in this section and demonstrated with examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e79b3-121">本节内容</span><span class="sxs-lookup"><span data-stu-id="e79b3-121">In This Section</span></span>  
 [<span data-ttu-id="e79b3-122">Integration Services 编程概述</span><span class="sxs-lookup"><span data-stu-id="e79b3-122">Integration Services Programming Overview</span></span>](integration-services-programming-overview.md)  
 <span data-ttu-id="e79b3-123">介绍 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 开发中的控制流和数据流的角色。</span><span class="sxs-lookup"><span data-stu-id="e79b3-123">Describes the roles of control flow and data flow in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] development.</span></span>  
  
 [<span data-ttu-id="e79b3-124">了解同步和异步转换</span><span class="sxs-lookup"><span data-stu-id="e79b3-124">Understanding Synchronous and Asynchronous Transformations</span></span>](understanding-synchronous-and-asynchronous-transformations.md)  
 <span data-ttu-id="e79b3-125">介绍同步输出与异步输出之间的重要差异以及在数据流中使用这些输出的组件。</span><span class="sxs-lookup"><span data-stu-id="e79b3-125">Describes the important distinction between synchronous and asynchronous outputs and the components that use them in the data flow.</span></span>  
  
 [<span data-ttu-id="e79b3-126">以编程方式使用连接管理器</span><span class="sxs-lookup"><span data-stu-id="e79b3-126">Working with Connection Managers Programmatically</span></span>](working-with-connection-managers-programmatically.md)  
 <span data-ttu-id="e79b3-127">列出了可从托管代码使用的连接管理器，以及代码调用 `AcquireConnection` 方法时连接管理器返回的值。</span><span class="sxs-lookup"><span data-stu-id="e79b3-127">Lists the connection managers that you can use from managed code, and the values that the connection managers return when the code calls the `AcquireConnection` method.</span></span>  
  
 [<span data-ttu-id="e79b3-128">用脚本扩展包</span><span class="sxs-lookup"><span data-stu-id="e79b3-128">Extending Packages with Scripting</span></span>](extending-packages-scripting/extending-packages-with-scripting.md)  
 <span data-ttu-id="e79b3-129">介绍如何使用脚本任务扩展控制流或使用脚本组件扩展数据流。</span><span class="sxs-lookup"><span data-stu-id="e79b3-129">Describes how to extend the control flow by using the Script task, or the data flow by using the Script component.</span></span>  
  
 [<span data-ttu-id="e79b3-130">用自定义对象扩展包</span><span class="sxs-lookup"><span data-stu-id="e79b3-130">Extending Packages with Custom Objects</span></span>](extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
 <span data-ttu-id="e79b3-131">介绍在多个包中使用时，如何创建自定义任务、数据流组件和其他包对象以及如何进行相关的编程。</span><span class="sxs-lookup"><span data-stu-id="e79b3-131">Describes how to create and program custom tasks, data flow components, and other package objects for use in multiple packages.</span></span>  
  
 [<span data-ttu-id="e79b3-132">以编程方式生成包</span><span class="sxs-lookup"><span data-stu-id="e79b3-132">Building Packages Programmatically</span></span>](building-packages-programmatically/building-packages-programmatically.md)  
 <span data-ttu-id="e79b3-133">介绍如何以编程方式创建、配置和保存 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="e79b3-133">Describes how to create, configure, and save [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages programmatically.</span></span>  
  
 [<span data-ttu-id="e79b3-134">以编程方式运行和管理包</span><span class="sxs-lookup"><span data-stu-id="e79b3-134">Running and Managing Packages Programmatically</span></span>](run-manage-packages-programmatically/running-and-managing-packages-programmatically.md)  
 <span data-ttu-id="e79b3-135">介绍如何以编程方式枚举、运行和管理 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="e79b3-135">Describes how to enumerate, run, and manage [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages programmatically.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e79b3-136">参考</span><span class="sxs-lookup"><span data-stu-id="e79b3-136">Reference</span></span>  
 [<span data-ttu-id="e79b3-137">Integration Services 错误和消息引用</span><span class="sxs-lookup"><span data-stu-id="e79b3-137">Integration Services Error and Message Reference</span></span>](integration-services-error-and-message-reference.md)  
 <span data-ttu-id="e79b3-138">列出预定义的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 错误代码及其符号名称和说明。</span><span class="sxs-lookup"><span data-stu-id="e79b3-138">Lists the predefined [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] error codes, together with their symbolic names and descriptions.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e79b3-139">相关章节</span><span class="sxs-lookup"><span data-stu-id="e79b3-139">Related Sections</span></span>  
 [<span data-ttu-id="e79b3-140">包开发的疑难解答工具</span><span class="sxs-lookup"><span data-stu-id="e79b3-140">Troubleshooting Tools for Package Development</span></span>](troubleshooting/troubleshooting-tools-for-package-development.md)  
 <span data-ttu-id="e79b3-141">介绍 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 提供的用于在开发过程中对包进行故障排除的功能和工具。</span><span class="sxs-lookup"><span data-stu-id="e79b3-141">Describes the features and tools that [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] provides for troubleshooting packages during development.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="e79b3-142">外部资源</span><span class="sxs-lookup"><span data-stu-id="e79b3-142">External Resources</span></span>  
  
-   <span data-ttu-id="e79b3-143">www.codeplex.com/MSFTISProdSamples 上的 CodePlex 示例 [Integration Services 产品示例](https://go.microsoft.com/fwlink/?LinkID=131204)</span><span class="sxs-lookup"><span data-stu-id="e79b3-143">CodePlex samples, [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkID=131204), on www.codeplex.com/MSFTISProdSamples</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e79b3-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e79b3-144">See Also</span></span>  
 [<span data-ttu-id="e79b3-145">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="e79b3-145">SQL Server Integration Services</span></span>](sql-server-integration-services.md)  
  
  
