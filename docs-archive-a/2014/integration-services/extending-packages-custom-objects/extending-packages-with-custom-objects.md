---
title: 用自定义对象扩展包 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 26616eb8-9e80-434d-b22a-ece1b00f449d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0159983f518e51aa082ea23745663e7f09eee1fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682354"
---
# <a name="extending-packages-with-custom-objects"></a><span data-ttu-id="8d85d-102">用自定义对象扩展包</span><span class="sxs-lookup"><span data-stu-id="8d85d-102">Extending Packages with Custom Objects</span></span>
  <span data-ttu-id="8d85d-103">如果觉得 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 内提供的组件不能满足您的需求，可以通过编写自己的扩展插件代码来扩展 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的功能。</span><span class="sxs-lookup"><span data-stu-id="8d85d-103">If you find that the components provided in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] do not meet your requirements, you can extend the power of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] by coding your own extensions.</span></span> <span data-ttu-id="8d85d-104">对于扩展包，您有两种不同的选择：可以在脚本任务和脚本组件提供的功能强大的包装中编写代码，或者通过从 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 对象模型提供的基类进行派生，完全重新创建自定义 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 扩展插件。</span><span class="sxs-lookup"><span data-stu-id="8d85d-104">You have two discrete options for extending your packages: you can write code within the powerful wrappers provided by the Script task and the Script component, or you can create custom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] extensions from scratch by deriving from the base classes provided by the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] object model.</span></span>  
  
 <span data-ttu-id="8d85d-105">本节介绍这两种方法中较为高级的方法：使用自定义对象扩展包。</span><span class="sxs-lookup"><span data-stu-id="8d85d-105">This section explores the more advanced of the two options - extending packages with custom objects.</span></span>  
  
 <span data-ttu-id="8d85d-106">如果自定义 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 解决方案所需的灵活性要比脚本任务和脚本组件所具有的灵活性高，或如果需要可以在多个包中重复使用的组件，您可以通过 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 对象模型从头开始生成自定义任务、数据流组件和其他使用托管代码生成的包对象。</span><span class="sxs-lookup"><span data-stu-id="8d85d-106">When your custom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] solution requires more flexibility than the Script task and the Script component provide, or when you need a component that you can reuse in multiple packages, the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] object model lets you build custom tasks, data flow components, and other package objects in managed code from the ground up.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8d85d-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="8d85d-107">In This Section</span></span>  
 [<span data-ttu-id="8d85d-108">开发 Integration Services 的自定义对象</span><span class="sxs-lookup"><span data-stu-id="8d85d-108">Developing Custom Objects for Integration Services</span></span>](developing-custom-objects-for-integration-services.md)  
 <span data-ttu-id="8d85d-109">讨论可以为 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 创建的自定义对象，并概括介绍基本步骤和设置。</span><span class="sxs-lookup"><span data-stu-id="8d85d-109">Discusses the custom objects that can be created for [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], and summarizes the essential steps and settings.</span></span>  
  
 [<span data-ttu-id="8d85d-110">使自定义对象持久化</span><span class="sxs-lookup"><span data-stu-id="8d85d-110">Persisting Custom Objects</span></span>](persisting-custom-objects.md)  
 <span data-ttu-id="8d85d-111">讨论自定义对象的默认持久性和实现自定义持久性的过程。</span><span class="sxs-lookup"><span data-stu-id="8d85d-111">Discusses the default persistence of custom objects, and the process of implementing custom persistence.</span></span>  
  
 [<span data-ttu-id="8d85d-112">生成、部署和调试自定义对象</span><span class="sxs-lookup"><span data-stu-id="8d85d-112">Building, Deploying, and Debugging Custom Objects</span></span>](building-deploying-and-debugging-custom-objects.md)  
 <span data-ttu-id="8d85d-113">讨论生成、部署和测试各种类型自定义对象的常用方法。</span><span class="sxs-lookup"><span data-stu-id="8d85d-113">Discusses the common approaches to building, deploying and testing the various types of custom objects.</span></span>  
  
 [<span data-ttu-id="8d85d-114">开发自定义任务</span><span class="sxs-lookup"><span data-stu-id="8d85d-114">Developing a Custom Task</span></span>](task/developing-a-custom-task.md)  
 <span data-ttu-id="8d85d-115">介绍编写自定义任务代码的过程。</span><span class="sxs-lookup"><span data-stu-id="8d85d-115">Describes the process of coding a custom task.</span></span>  
  
 [<span data-ttu-id="8d85d-116">开发自定义连接管理器</span><span class="sxs-lookup"><span data-stu-id="8d85d-116">Developing a Custom Connection Manager</span></span>](connection-manager/developing-a-custom-connection-manager.md)  
 <span data-ttu-id="8d85d-117">介绍编写自定义连接管理器代码的过程。</span><span class="sxs-lookup"><span data-stu-id="8d85d-117">Describes the process of coding a custom connection manager.</span></span>  
  
 [<span data-ttu-id="8d85d-118">开发自定义日志提供程序</span><span class="sxs-lookup"><span data-stu-id="8d85d-118">Developing a Custom Log Provider</span></span>](log-provider/developing-a-custom-log-provider.md)  
 <span data-ttu-id="8d85d-119">介绍编写自定义日志提供程序代码的过程。</span><span class="sxs-lookup"><span data-stu-id="8d85d-119">Describes the process of coding a custom log provider.</span></span>  
  
 [<span data-ttu-id="8d85d-120">开发自定义 ForEach 枚举器</span><span class="sxs-lookup"><span data-stu-id="8d85d-120">Developing a Custom ForEach Enumerator</span></span>](foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 <span data-ttu-id="8d85d-121">介绍编写自定义枚举器代码的过程。</span><span class="sxs-lookup"><span data-stu-id="8d85d-121">Describes the process of coding a custom enumerator.</span></span>  
  
 [<span data-ttu-id="8d85d-122">开发自定义数据流组件</span><span class="sxs-lookup"><span data-stu-id="8d85d-122">Developing a Custom Data Flow Component</span></span>](data-flow/developing-a-custom-data-flow-component.md)  
 <span data-ttu-id="8d85d-123">讨论如何对自定义数据流源、转换和目标进行编程。</span><span class="sxs-lookup"><span data-stu-id="8d85d-123">Discusses how to program custom data flow sources, transformations, and destinations.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8d85d-124">参考</span><span class="sxs-lookup"><span data-stu-id="8d85d-124">Reference</span></span>  
 [<span data-ttu-id="8d85d-125">Integration Services 错误和消息引用</span><span class="sxs-lookup"><span data-stu-id="8d85d-125">Integration Services Error and Message Reference</span></span>](../integration-services-error-and-message-reference.md)  
 <span data-ttu-id="8d85d-126">列出预定义的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 错误代码及其符号名称和说明。</span><span class="sxs-lookup"><span data-stu-id="8d85d-126">Lists the predefined [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] error codes with their symbolic names and descriptions.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8d85d-127">相关章节</span><span class="sxs-lookup"><span data-stu-id="8d85d-127">Related Sections</span></span>  
 [<span data-ttu-id="8d85d-128">用脚本扩展包</span><span class="sxs-lookup"><span data-stu-id="8d85d-128">Extending Packages with Scripting</span></span>](../extending-packages-scripting/extending-packages-with-scripting.md)  
 <span data-ttu-id="8d85d-129">讨论如何使用脚本任务扩展控制流，或使用脚本组件扩展数据流。</span><span class="sxs-lookup"><span data-stu-id="8d85d-129">Discusses how to extend the control flow by using the Script task, or extend the data flow by using the Script component.</span></span>  
  
 [<span data-ttu-id="8d85d-130">以编程方式生成包</span><span class="sxs-lookup"><span data-stu-id="8d85d-130">Building Packages Programmatically</span></span>](../building-packages-programmatically/building-packages-programmatically.md)  
 <span data-ttu-id="8d85d-131">介绍如何以编程方式创建、配置、运行、加载、保存和管理 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="8d85d-131">Describes how to create, configure, run, load, save, and manage [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages programmatically.</span></span>  
  
<span data-ttu-id="8d85d-132">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="8d85d-132">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="8d85d-133">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="8d85d-133">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="8d85d-134">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="8d85d-134">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="8d85d-135">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="8d85d-135">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d85d-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8d85d-136">See Also</span></span>  
 <span data-ttu-id="8d85d-137">[比较脚本解决方案和自定义对象](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md) </span><span class="sxs-lookup"><span data-stu-id="8d85d-137">[Comparing Scripting Solutions and Custom Objects](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md) </span></span>  
 [<span data-ttu-id="8d85d-138">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="8d85d-138">SQL Server Integration Services</span></span>](../sql-server-integration-services.md)  
  
  
