---
title: 使用脚本扩展包 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- SQL Server Integration Services, scripting
- SSIS, scripting
- scripts [Integration Services], about scripting
ms.assetid: 67fe18ef-f3aa-41d4-9b9d-5defd4618c4b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3bc3aac2483a29a686f8a2c4dfbf0688c5810546
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691314"
---
# <a name="extending-packages-with-scripting"></a><span data-ttu-id="bbfbe-102">用脚本扩展包</span><span class="sxs-lookup"><span data-stu-id="bbfbe-102">Extending Packages with Scripting</span></span>
  <span data-ttu-id="bbfbe-103">如果您觉得 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中的内置组件不能满足您的要求，您可以编写自己的扩展插件代码来扩展 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的功能。</span><span class="sxs-lookup"><span data-stu-id="bbfbe-103">If you find that the built-in components [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] do not meet your requirements, you can extend the power of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] by coding your own extensions.</span></span> <span data-ttu-id="bbfbe-104">对于扩展包，您有两种不同的选择：可以在脚本任务和脚本组件提供的功能强大的包装中编写代码，或者通过从 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 对象模型提供的基类进行派生，完全重新创建自定义 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 扩展插件。</span><span class="sxs-lookup"><span data-stu-id="bbfbe-104">You have two discrete options for extending your packages: you can write code within the powerful wrappers provided by the Script task and the Script component, or you can create custom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] extensions from scratch by deriving from the base classes provided by the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] object model.</span></span>

 <span data-ttu-id="bbfbe-105">本节介绍这两种方法中较为简单的方法：用脚本扩展包。</span><span class="sxs-lookup"><span data-stu-id="bbfbe-105">This section explores the simpler of the two options - extending packages with scripting.</span></span>

 <span data-ttu-id="bbfbe-106">使用脚本任务和脚本组件，可以通过很少的编码对 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的控制流和数据流进行扩展。</span><span class="sxs-lookup"><span data-stu-id="bbfbe-106">The Script task and the Script component let you extend both the control flow and the data flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package with very little coding.</span></span> <span data-ttu-id="bbfbe-107">这两种对象均使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) 开发环境和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic 或 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# 编程语言，并且均可使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 类库和自定义程序集所提供的所有功能。</span><span class="sxs-lookup"><span data-stu-id="bbfbe-107">Both objects use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) development environment and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# programming languages, and benefit from all the functionality offered by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] class library, as well as custom assemblies.</span></span> <span data-ttu-id="bbfbe-108">开发人员使用脚本任务和脚本组件创建自定义功能时，不必编写通常在开发自定义任务或自定义数据流组件时所需的所有基础结构代码。</span><span class="sxs-lookup"><span data-stu-id="bbfbe-108">The Script task and the Script component let the developer create custom functionality without having to write all the infrastructure code that is typically required when developing a custom task or custom data flow component.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="bbfbe-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="bbfbe-109">In This Section</span></span>
 <span data-ttu-id="bbfbe-110">[比较脚本任务和脚本组件](../extending-packages-scripting/comparing-the-script-task-and-the-script-component.md)讨论脚本任务和脚本组件之间的相似性和差异。</span><span class="sxs-lookup"><span data-stu-id="bbfbe-110">[Comparing the Script Task and the Script Component](../extending-packages-scripting/comparing-the-script-task-and-the-script-component.md) Discusses the similarities and differences between the Script task and the Script component.</span></span>

 <span data-ttu-id="bbfbe-111">[比较脚本解决方案和自定义对象](comparing-scripting-solutions-and-custom-objects.md)讨论在脚本解决方案和自定义对象的开发之间进行选择时要使用的条件。</span><span class="sxs-lookup"><span data-stu-id="bbfbe-111">[Comparing Scripting Solutions and Custom Objects](comparing-scripting-solutions-and-custom-objects.md) Discusses the criteria to use in choosing between a scripting solution and the development of a custom object.</span></span>

 <span data-ttu-id="bbfbe-112">[引用脚本解决方案中的其他程序集](referencing-other-assemblies-in-scripting-solutions.md)讨论在脚本项目中引用和使用外部程序集和命名空间所需的步骤。</span><span class="sxs-lookup"><span data-stu-id="bbfbe-112">[Referencing Other Assemblies in Scripting Solutions](referencing-other-assemblies-in-scripting-solutions.md) Discusses the steps required to reference and use external assemblies and namespaces in a scripting project.</span></span>

 <span data-ttu-id="bbfbe-113">[用脚本任务扩展包](../extending-packages-scripting/task/extending-the-package-with-the-script-task.md)讨论如何使用脚本任务创建自定义任务。</span><span class="sxs-lookup"><span data-stu-id="bbfbe-113">[Extending the Package with the Script Task](../extending-packages-scripting/task/extending-the-package-with-the-script-task.md) Discusses how to create custom tasks by using the Script task.</span></span> <span data-ttu-id="bbfbe-114">通常，每次包执行会调用任务一次，包每次打开一个数据源也会调用任务一次。</span><span class="sxs-lookup"><span data-stu-id="bbfbe-114">A task is typically called one time per package execution, or one time for each data source opened by a package.</span></span>

 <span data-ttu-id="bbfbe-115">[用脚本组件扩展数据流](data-flow-script-component/extending-the-data-flow-with-the-script-component.md)介绍如何使用脚本组件创建自定义数据流源、转换和目标。</span><span class="sxs-lookup"><span data-stu-id="bbfbe-115">[Extending the Data Flow with the Script Component](data-flow-script-component/extending-the-data-flow-with-the-script-component.md) Discusses how to create custom data flow sources, transformations, and destinations by using the Script component.</span></span> <span data-ttu-id="bbfbe-116">通常，处理每一行数据时会调用一次数据流组件。</span><span class="sxs-lookup"><span data-stu-id="bbfbe-116">A data flow component is typically called one time for each row of data that is processed.</span></span>

## <a name="reference"></a><span data-ttu-id="bbfbe-117">参考</span><span class="sxs-lookup"><span data-stu-id="bbfbe-117">Reference</span></span>
 <span data-ttu-id="bbfbe-118">[Integration Services 错误和消息引用](../integration-services-error-and-message-reference.md)列出预定义的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 错误代码及其符号名称和说明。</span><span class="sxs-lookup"><span data-stu-id="bbfbe-118">[Integration Services Error and Message Reference](../integration-services-error-and-message-reference.md) Lists the predefined [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] error codes with their symbolic names and descriptions.</span></span>

## <a name="related-sections"></a><span data-ttu-id="bbfbe-119">相关章节</span><span class="sxs-lookup"><span data-stu-id="bbfbe-119">Related Sections</span></span>
 <span data-ttu-id="bbfbe-120">[用自定义对象扩展包](../extending-packages-custom-objects/extending-packages-with-custom-objects.md)讨论如何创建程序自定义任务、数据流组件和其他包对象以便在多个包中使用。</span><span class="sxs-lookup"><span data-stu-id="bbfbe-120">[Extending Packages with Custom Objects](../extending-packages-custom-objects/extending-packages-with-custom-objects.md) Discusses how to create program custom tasks, data flow components, and other package objects for use in multiple packages.</span></span>

 <span data-ttu-id="bbfbe-121">[以编程方式生成包](../building-packages-programmatically/building-packages-programmatically.md)描述如何以编程方式创建、配置、运行、加载、保存和管理 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="bbfbe-121">[Building Packages Programmatically](../building-packages-programmatically/building-packages-programmatically.md) Describes how to create, configure, run, load, save, and manage [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages programmatically.</span></span>

<span data-ttu-id="bbfbe-122">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="bbfbe-122">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="bbfbe-123">若要从 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="bbfbe-123">For the latest downloads, articles, samples, and videos from [!INCLUDE[msCoName](../../includes/msconame-md.md)], as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="bbfbe-124">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="bbfbe-124">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="bbfbe-125">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="bbfbe-125">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="bbfbe-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bbfbe-126">See Also</span></span>
 [<span data-ttu-id="bbfbe-127">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="bbfbe-127">SQL Server Integration Services</span></span>](../sql-server-integration-services.md)


