---
title: 开发自定义连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- packages [Integration Services], connections
- custom connection managers [Integration Services], about custom connection managers
- connection managers [Integration Services], custom
- Integration Services packages, connection managers
- SSIS packages, connection managers
- SQL Server Integration Services packages, connection managers
- custom connection managers [Integration Services]
ms.assetid: bda0b29e-57f5-4879-b04d-1396dc56daa8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 19c5a9066db6542742537a41a7f567d1b4b1d23d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694040"
---
# <a name="developing-a-custom-connection-manager"></a><span data-ttu-id="e0ba7-102">开发自定义连接管理器</span><span class="sxs-lookup"><span data-stu-id="e0ba7-102">Developing a Custom Connection Manager</span></span>
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="e0ba7-103">使用连接管理器封装连接到外部数据源所需的信息。</span><span class="sxs-lookup"><span data-stu-id="e0ba7-103">uses connection managers to encapsulate the information needed to connect to an external data source.</span></span> [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="e0ba7-104">包括可支持与常用数据源（从企业数据库到文本文件和 Excel 工作表）的连接的各种连接管理器。</span><span class="sxs-lookup"><span data-stu-id="e0ba7-104">includes a variety of connection managers that support connections to the most commonly used data sources, from enterprise databases to text files and Excel worksheets.</span></span> <span data-ttu-id="e0ba7-105">如果 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 支持的连接管理器和外部数据源不能完全满足您的需要，则可以创建自定义连接管理器。</span><span class="sxs-lookup"><span data-stu-id="e0ba7-105">If the connection managers and external data sources supported by [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] do not entirely meet your requirements, you can create a custom connection manager.</span></span>  
  
 <span data-ttu-id="e0ba7-106">若要创建自定义连接管理器，必须创建从 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> 基类继承的类，再将 <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> 属性应用到新类，然后重写基类的重要方法和属性，包括 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> 属性和 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e0ba7-106">To create a custom connection manager, you have to create a class that inherits from the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> base class, apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> attribute to your new class, and override the important methods and properties of the base class, including the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> property and the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> method.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e0ba7-107">内置于 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 的大多数任务、源和目标都只能与特定类型的内置连接管理器一起工作。</span><span class="sxs-lookup"><span data-stu-id="e0ba7-107">Most of the tasks, sources, and destinations that have been built into [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] work only with specific types of built-in connection managers.</span></span> <span data-ttu-id="e0ba7-108">在开发用于内置任务和组件的自定义连接管理器之前，请检查这些组件是否将可用连接管理器的列表限制为特定类型的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="e0ba7-108">Before developing a custom connection manager for use with built-in tasks and components, check whether those components restrict the list of available connection managers to those of a specific type.</span></span> <span data-ttu-id="e0ba7-109">如果您的解决方案需要自定义连接管理器，则还可能必须开发自定义任务或自定义源或目标以与连接管理器一起使用。</span><span class="sxs-lookup"><span data-stu-id="e0ba7-109">If your solution requires a custom connection manager, you might also have to develop a custom task, or a custom source or destination, for use with the connection manager.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e0ba7-110">本节内容</span><span class="sxs-lookup"><span data-stu-id="e0ba7-110">In This Section</span></span>  
 <span data-ttu-id="e0ba7-111">本节介绍如何创建、配置和编写自定义连接管理器及其可选自定义用户界面的代码。</span><span class="sxs-lookup"><span data-stu-id="e0ba7-111">This section describes how to create, configure, and code a custom connection manager and its optional custom user interface.</span></span> <span data-ttu-id="e0ba7-112">本节中演示的代码段来自 SQL Server 自定义连接管理器示例。</span><span class="sxs-lookup"><span data-stu-id="e0ba7-112">The code snippets shown in this section are drawn from the Sql Server Custom Connection Manager Sample.</span></span>  
  
 [<span data-ttu-id="e0ba7-113">创建自定义连接管理器</span><span class="sxs-lookup"><span data-stu-id="e0ba7-113">Creating a Custom Connection Manager</span></span>](creating-a-custom-connection-manager.md)  
 <span data-ttu-id="e0ba7-114">介绍如何为自定义连接管理器项目创建类。</span><span class="sxs-lookup"><span data-stu-id="e0ba7-114">Describes how to create the classes for a custom connection manager project.</span></span>  
  
 [<span data-ttu-id="e0ba7-115">编写自定义连接管理器代码</span><span class="sxs-lookup"><span data-stu-id="e0ba7-115">Coding a Custom Connection Manager</span></span>](coding-a-custom-connection-manager.md)  
 <span data-ttu-id="e0ba7-116">介绍如何通过重写基类的方法和属性实现自定义连接管理器。</span><span class="sxs-lookup"><span data-stu-id="e0ba7-116">Describes how to implement a custom connection manager by overriding the methods and properties of the base class.</span></span>  
  
 [<span data-ttu-id="e0ba7-117">为自定义连接管理器开发用户界面</span><span class="sxs-lookup"><span data-stu-id="e0ba7-117">Developing a User Interface for a Custom Connection Manager</span></span>](developing-a-user-interface-for-a-custom-connection-manager.md)  
 <span data-ttu-id="e0ba7-118">介绍如何实现用户界面类，以及用于配置自定义连接管理器的窗体。</span><span class="sxs-lookup"><span data-stu-id="e0ba7-118">Describes how to implement the user interface class and the form that is used to configure the custom connection manager.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e0ba7-119">相关章节</span><span class="sxs-lookup"><span data-stu-id="e0ba7-119">Related Sections</span></span>  
  
### <a name="information-common-to-all-custom-objects"></a><span data-ttu-id="e0ba7-120">所有自定义对象的通用信息</span><span class="sxs-lookup"><span data-stu-id="e0ba7-120">Information Common to all Custom Objects</span></span>  
 <span data-ttu-id="e0ba7-121">有关可以在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中创建的所有类型自定义对象的通用信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="e0ba7-121">For information that is common to all the type of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>  
  
 [<span data-ttu-id="e0ba7-122">开发 Integration Services 的自定义对象</span><span class="sxs-lookup"><span data-stu-id="e0ba7-122">Developing Custom Objects for Integration Services</span></span>](../developing-custom-objects-for-integration-services.md)  
 <span data-ttu-id="e0ba7-123">介绍实现 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 的所有自定义对象类型的基本步骤。</span><span class="sxs-lookup"><span data-stu-id="e0ba7-123">Describes the basic steps in implementing all types of custom objects for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="e0ba7-124">使自定义对象持久化</span><span class="sxs-lookup"><span data-stu-id="e0ba7-124">Persisting Custom Objects</span></span>](../persisting-custom-objects.md)  
 <span data-ttu-id="e0ba7-125">介绍自定义持久性并在必要时作出解释。</span><span class="sxs-lookup"><span data-stu-id="e0ba7-125">Describes custom persistence and explains when it is necessary.</span></span>  
  
 [<span data-ttu-id="e0ba7-126">生成、部署和调试自定义对象</span><span class="sxs-lookup"><span data-stu-id="e0ba7-126">Building, Deploying, and Debugging Custom Objects</span></span>](../building-deploying-and-debugging-custom-objects.md)  
 <span data-ttu-id="e0ba7-127">介绍生成、签名、部署和调试自定义对象的技术。</span><span class="sxs-lookup"><span data-stu-id="e0ba7-127">Describes the techniques for building, signing, deploying, and debugging custom objects.</span></span>  
  
### <a name="information-about-other-custom-objects"></a><span data-ttu-id="e0ba7-128">其他自定义对象的信息</span><span class="sxs-lookup"><span data-stu-id="e0ba7-128">Information about Other Custom Objects</span></span>  
 <span data-ttu-id="e0ba7-129">有关可在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中创建的其他自定义对象类型的信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="e0ba7-129">For information on the other types of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>  
  
 [<span data-ttu-id="e0ba7-130">开发自定义任务</span><span class="sxs-lookup"><span data-stu-id="e0ba7-130">Developing a Custom Task</span></span>](../task/developing-a-custom-task.md)  
 <span data-ttu-id="e0ba7-131">讨论如何对自定义任务进行编程。</span><span class="sxs-lookup"><span data-stu-id="e0ba7-131">Discusses how to program custom tasks.</span></span>  
  
 [<span data-ttu-id="e0ba7-132">开发自定义日志提供程序</span><span class="sxs-lookup"><span data-stu-id="e0ba7-132">Developing a Custom Log Provider</span></span>](../log-provider/developing-a-custom-log-provider.md)  
 <span data-ttu-id="e0ba7-133">讨论如何对自定义日志提供程序进行编程。</span><span class="sxs-lookup"><span data-stu-id="e0ba7-133">Discusses how to program custom log providers.</span></span>  
  
 [<span data-ttu-id="e0ba7-134">开发自定义 ForEach 枚举器</span><span class="sxs-lookup"><span data-stu-id="e0ba7-134">Developing a Custom ForEach Enumerator</span></span>](../foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 <span data-ttu-id="e0ba7-135">讨论如何对自定义枚举器进行编程。</span><span class="sxs-lookup"><span data-stu-id="e0ba7-135">Discusses how to program custom enumerators.</span></span>  
  
 [<span data-ttu-id="e0ba7-136">开发自定义数据流组件</span><span class="sxs-lookup"><span data-stu-id="e0ba7-136">Developing a Custom Data Flow Component</span></span>](../data-flow/developing-a-custom-data-flow-component.md)  
 <span data-ttu-id="e0ba7-137">讨论如何对自定义数据流源、转换和目标进行编程。</span><span class="sxs-lookup"><span data-stu-id="e0ba7-137">Discusses how to program custom data flow sources, transformations, and destinations.</span></span>  
  
<span data-ttu-id="e0ba7-138">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="e0ba7-138">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="e0ba7-139">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="e0ba7-139">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="e0ba7-140">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="e0ba7-140">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="e0ba7-141">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="e0ba7-141">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
