---
title: 开发自定义任务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom tasks [Integration Services], about custom tasks
- Task class
- custom tasks [Integration Services]
- SSIS custom tasks
- SSIS custom tasks, about custom tasks
- IDtsTaskUI interface
- DtsTaskAttribute attribute
- tasks [Integration Services], custom
- TaskHost object
ms.assetid: dcbd8615-fa6d-4ddb-b8a5-0b19dddd6239
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d9d3446acff7ced73ab47014bec51708dba225b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588656"
---
# <a name="developing-a-custom-task"></a><span data-ttu-id="37f62-102">开发自定义任务</span><span class="sxs-lookup"><span data-stu-id="37f62-102">Developing a Custom Task</span></span>
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]<span data-ttu-id="37f62-103">使用任务执行工作单元，从而支持数据的提取、转换和加载。</span><span class="sxs-lookup"><span data-stu-id="37f62-103">uses tasks to perform units of work in support of the extraction, transformation, and loading of data.</span></span> [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="37f62-104">包含多种任务，这些任务可执行从执行 SQL 语句到从 FTP 站点下载文件的大部分常用操作。</span><span class="sxs-lookup"><span data-stu-id="37f62-104">includes a variety of tasks that perform the most frequently used actions, from executing an SQL statement to downloading a file from an FTP site.</span></span> <span data-ttu-id="37f62-105">如果包含的任务和支持的操作不能完全满足您的要求，您可以创建自定义任务。</span><span class="sxs-lookup"><span data-stu-id="37f62-105">If the included tasks and supported actions do not completely meet your requirements, you can create a custom task.</span></span>  
  
 <span data-ttu-id="37f62-106">若要创建自定义任务，必须创建从 [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) 基类继承的类，再将 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 属性应用到新类，然后重写基类的重要方法和属性，包括 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="37f62-106">To create a custom task, you have to create a class that inherits from the [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) base class, apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute to your new class, and override the important methods and properties of the base class, including the <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> method.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="37f62-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="37f62-107">In This Section</span></span>  
 <span data-ttu-id="37f62-108">本节介绍如何创建、配置和编写自定义任务及其可选自定义用户界面的代码。</span><span class="sxs-lookup"><span data-stu-id="37f62-108">This section describes how to create, configure, and code a custom task and its optional custom user interface.</span></span>  
  
 [<span data-ttu-id="37f62-109">创建自定义任务</span><span class="sxs-lookup"><span data-stu-id="37f62-109">Creating a Custom Task</span></span>](creating-a-custom-task.md)  
 <span data-ttu-id="37f62-110">介绍第一个步骤，即创建自定义任务。</span><span class="sxs-lookup"><span data-stu-id="37f62-110">Describes the first step, which is creating the custom task.</span></span>  
  
 [<span data-ttu-id="37f62-111">编写自定义任务代码</span><span class="sxs-lookup"><span data-stu-id="37f62-111">Coding a Custom Task</span></span>](coding-a-custom-task.md)  
 <span data-ttu-id="37f62-112">介绍如何编写自定义任务的主要方法的代码。</span><span class="sxs-lookup"><span data-stu-id="37f62-112">Describes how to code the principal methods of a custom task.</span></span>  
  
 [<span data-ttu-id="37f62-113">在自定义任务中连接数据源</span><span class="sxs-lookup"><span data-stu-id="37f62-113">Connecting to Data Sources in a Custom Task</span></span>](connecting-to-data-sources-in-a-custom-task.md)  
 <span data-ttu-id="37f62-114">介绍如何将自定义任务连接到数据源。</span><span class="sxs-lookup"><span data-stu-id="37f62-114">Describes how to connect a custom task to a data source.</span></span>  
  
 [<span data-ttu-id="37f62-115">在自定义任务中引发和定义事件</span><span class="sxs-lookup"><span data-stu-id="37f62-115">Raising and Defining Events in a Custom Task</span></span>](raising-and-defining-events-in-a-custom-task.md)  
 <span data-ttu-id="37f62-116">介绍如何从自定义任务引发事件和定义自定义事件。</span><span class="sxs-lookup"><span data-stu-id="37f62-116">Describes how to raise events and define custom events from the custom task.</span></span>  
  
 [<span data-ttu-id="37f62-117">在自定义任务中添加对调试的支持</span><span class="sxs-lookup"><span data-stu-id="37f62-117">Adding Support for Debugging in a Custom Task</span></span>](adding-support-for-debugging-in-a-custom-task.md)  
 <span data-ttu-id="37f62-118">介绍如何在自定义任务中创建断点目标。</span><span class="sxs-lookup"><span data-stu-id="37f62-118">Describes how to create breakpoint targets in the custom task.</span></span>  
  
 [<span data-ttu-id="37f62-119">为自定义任务开发用户界面</span><span class="sxs-lookup"><span data-stu-id="37f62-119">Developing a User Interface for a Custom Task</span></span>](developing-a-user-interface-for-a-custom-task.md)  
 <span data-ttu-id="37f62-120">介绍如何创建显示在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中用于配置自定义任务属性的用户界面。</span><span class="sxs-lookup"><span data-stu-id="37f62-120">Describes how to create a user interface that shows in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer to configure properties on the custom task.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="37f62-121">相关章节</span><span class="sxs-lookup"><span data-stu-id="37f62-121">Related Sections</span></span>  
  
### <a name="information-common-to-all-custom-objects"></a><span data-ttu-id="37f62-122">所有自定义对象的通用信息</span><span class="sxs-lookup"><span data-stu-id="37f62-122">Information Common to all Custom Objects</span></span>  
 <span data-ttu-id="37f62-123">有关可以在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中创建的所有类型自定义对象的通用信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="37f62-123">For information that is common to all the type of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>  
  
 [<span data-ttu-id="37f62-124">开发 Integration Services 的自定义对象</span><span class="sxs-lookup"><span data-stu-id="37f62-124">Developing Custom Objects for Integration Services</span></span>](../developing-custom-objects-for-integration-services.md)  
 <span data-ttu-id="37f62-125">介绍实现 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 的所有类型自定义对象的基本步骤。</span><span class="sxs-lookup"><span data-stu-id="37f62-125">Describes the basic steps in implementing all kinds of custom objects for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="37f62-126">使自定义对象持久化</span><span class="sxs-lookup"><span data-stu-id="37f62-126">Persisting Custom Objects</span></span>](../persisting-custom-objects.md)  
 <span data-ttu-id="37f62-127">介绍自定义持久性并在必要时作出解释。</span><span class="sxs-lookup"><span data-stu-id="37f62-127">Describes custom persistence and explains when it is necessary.</span></span>  
  
 [<span data-ttu-id="37f62-128">生成、部署和调试自定义对象</span><span class="sxs-lookup"><span data-stu-id="37f62-128">Building, Deploying, and Debugging Custom Objects</span></span>](../building-deploying-and-debugging-custom-objects.md)  
 <span data-ttu-id="37f62-129">介绍生成、签名、部署和调试自定义对象的技术。</span><span class="sxs-lookup"><span data-stu-id="37f62-129">Describes the techniques for building, signing, deploying, and debugging custom objects.</span></span>  
  
### <a name="information-about-other-custom-objects"></a><span data-ttu-id="37f62-130">其他自定义对象的信息</span><span class="sxs-lookup"><span data-stu-id="37f62-130">Information about Other Custom Objects</span></span>  
 <span data-ttu-id="37f62-131">有关可以在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中创建的其他类型自定义对象的信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="37f62-131">For information about the other types of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>  
  
 [<span data-ttu-id="37f62-132">开发自定义连接管理器</span><span class="sxs-lookup"><span data-stu-id="37f62-132">Developing a Custom Connection Manager</span></span>](../connection-manager/developing-a-custom-connection-manager.md)  
 <span data-ttu-id="37f62-133">讨论如何对自定义连接管理器进行编程。</span><span class="sxs-lookup"><span data-stu-id="37f62-133">Discusses how to program custom connection managers.</span></span>  
  
 [<span data-ttu-id="37f62-134">开发自定义日志提供程序</span><span class="sxs-lookup"><span data-stu-id="37f62-134">Developing a Custom Log Provider</span></span>](../log-provider/developing-a-custom-log-provider.md)  
 <span data-ttu-id="37f62-135">讨论如何对自定义日志提供程序进行编程。</span><span class="sxs-lookup"><span data-stu-id="37f62-135">Discusses how to program custom log providers.</span></span>  
  
 [<span data-ttu-id="37f62-136">开发自定义 ForEach 枚举器</span><span class="sxs-lookup"><span data-stu-id="37f62-136">Developing a Custom ForEach Enumerator</span></span>](../foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 <span data-ttu-id="37f62-137">讨论如何对自定义枚举器进行编程。</span><span class="sxs-lookup"><span data-stu-id="37f62-137">Discusses how to program custom enumerators.</span></span>  
  
 [<span data-ttu-id="37f62-138">开发自定义数据流组件</span><span class="sxs-lookup"><span data-stu-id="37f62-138">Developing a Custom Data Flow Component</span></span>](../data-flow/developing-a-custom-data-flow-component.md)  
 <span data-ttu-id="37f62-139">讨论如何对自定义数据流源、转换和目标进行编程。</span><span class="sxs-lookup"><span data-stu-id="37f62-139">Discusses how to program custom data flow sources, transformations, and destinations.</span></span>  
  
<span data-ttu-id="37f62-140">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="37f62-140">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="37f62-141">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="37f62-141">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="37f62-142">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="37f62-142">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="37f62-143">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="37f62-143">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37f62-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="37f62-144">See Also</span></span>  
 <span data-ttu-id="37f62-145">[使用脚本任务扩展包](../../extending-packages-scripting/task/extending-the-package-with-the-script-task.md) </span><span class="sxs-lookup"><span data-stu-id="37f62-145">[Extending the Package with the Script Task](../../extending-packages-scripting/task/extending-the-package-with-the-script-task.md) </span></span>  
 [<span data-ttu-id="37f62-146">比较脚本解决方案和自定义对象</span><span class="sxs-lookup"><span data-stu-id="37f62-146">Comparing Scripting Solutions and Custom Objects</span></span>](../../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)  
  
  
