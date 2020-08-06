---
title: 开发自定义 ForEach 枚举器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom foreach enumerators [Integration Services]
- custom foreach enumerators [Integration Services], about custom foreach enumerators
- foreach enumerators [Integration Services]
ms.assetid: bffe26e0-1b9a-47ad-bae6-6b708cb4cf4f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bc3d61f98266320f63d7ee56262b7c85dfb64d39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586908"
---
# <a name="developing-a-custom-foreach-enumerator"></a><span data-ttu-id="121d5-102">开发自定义 ForEach 枚举器</span><span class="sxs-lookup"><span data-stu-id="121d5-102">Developing a Custom ForEach Enumerator</span></span>
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="121d5-103">使用 Foreach 枚举器可循环访问集合中的项并为每个元素执行相同的任务。</span><span class="sxs-lookup"><span data-stu-id="121d5-103">uses foreach enumerators to iterate over the items in a collection and perform the same tasks for each element.</span></span> [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="121d5-104">包括支持常用集合的各种 Foreach 枚举器，例如文件夹中的所有文件、数据库中的所有表或包变量中存储的所有列表元素。</span><span class="sxs-lookup"><span data-stu-id="121d5-104">includes a variety of foreach enumerators that support the most commonly used collections, such as all the files in a folder, all the tables in a database, or all the elements of a list stored in a package variable.</span></span> <span data-ttu-id="121d5-105">如果提供的 Foreach 枚举器和集合不能完全满足您的需要，您可以创建自定义 Foreach 枚举器。</span><span class="sxs-lookup"><span data-stu-id="121d5-105">If the foreach enumerators and collections that are provided do not entirely meet your requirements, you can create a custom foreach enumerator.</span></span>  
  
 <span data-ttu-id="121d5-106">若要创建 Foreach 枚举器，必须创建从 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator> 基类继承的类，再将 <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> 属性应用到新类，然后重写基类的重要方法和属性，包括 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="121d5-106">To create a custom foreach enumerator, you have to create a class that inherits from the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator> base class, apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> attribute to your new class, and override the important methods and properties of the base class, including the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> method.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="121d5-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="121d5-107">In This Section</span></span>  
 <span data-ttu-id="121d5-108">本节介绍如何创建、配置和编写自定义 Foreach 枚举器及其自定义用户界面的代码。</span><span class="sxs-lookup"><span data-stu-id="121d5-108">This section describes how to create, configure, and code a custom foreach enumerator and its custom user interface.</span></span>  
  
 [<span data-ttu-id="121d5-109">创建自定义 Foreach 枚举器</span><span class="sxs-lookup"><span data-stu-id="121d5-109">Creating a Custom Foreach Enumerator</span></span>](creating-a-custom-foreach-enumerator.md)  
 <span data-ttu-id="121d5-110">介绍如何为自定义 Foreach 枚举器项目创建类。</span><span class="sxs-lookup"><span data-stu-id="121d5-110">Describes how to create the classes for a custom foreach enumerator project.</span></span>  
  
 [<span data-ttu-id="121d5-111">编写自定义 Foreach 枚举器代码</span><span class="sxs-lookup"><span data-stu-id="121d5-111">Coding a Custom Foreach Enumerator</span></span>](coding-a-custom-foreach-enumerator.md)  
 <span data-ttu-id="121d5-112">介绍如何通过重写基类的方法和属性实现自定义 Foreach 枚举器。</span><span class="sxs-lookup"><span data-stu-id="121d5-112">Describes how to implement a custom foreach enumerator by overriding the methods and properties of the base class.</span></span>  
  
 [<span data-ttu-id="121d5-113">为自定义 ForEach 枚举器开发用户界面</span><span class="sxs-lookup"><span data-stu-id="121d5-113">Developing a User Interface for a Custom ForEach Enumerator</span></span>](developing-a-user-interface-for-a-custom-foreach-enumerator.md)  
 <span data-ttu-id="121d5-114">介绍如何实现用户界面类，以及用于配置自定义 Foreach 枚举器的窗体。</span><span class="sxs-lookup"><span data-stu-id="121d5-114">Describes how to implement the user interface class and the form that is used to configure the custom foreach enumerator.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="121d5-115">相关主题</span><span class="sxs-lookup"><span data-stu-id="121d5-115">Related Topics</span></span>  
  
### <a name="information-common-to-all-custom-objects"></a><span data-ttu-id="121d5-116">所有自定义对象的通用信息</span><span class="sxs-lookup"><span data-stu-id="121d5-116">Information Common to all Custom Objects</span></span>  
 <span data-ttu-id="121d5-117">有关可以在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中创建的所有类型自定义对象的通用信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="121d5-117">For information that is common to all the type of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>  
  
 [<span data-ttu-id="121d5-118">开发 Integration Services 的自定义对象</span><span class="sxs-lookup"><span data-stu-id="121d5-118">Developing Custom Objects for Integration Services</span></span>](../developing-custom-objects-for-integration-services.md)  
 <span data-ttu-id="121d5-119">介绍实现 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 的所有自定义对象类型的基本步骤。</span><span class="sxs-lookup"><span data-stu-id="121d5-119">Describes the basic steps in implementing all types of custom objects for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="121d5-120">使自定义对象持久化</span><span class="sxs-lookup"><span data-stu-id="121d5-120">Persisting Custom Objects</span></span>](../persisting-custom-objects.md)  
 <span data-ttu-id="121d5-121">介绍自定义持久性并在必要时作出解释。</span><span class="sxs-lookup"><span data-stu-id="121d5-121">Describes custom persistence and explains when it is necessary.</span></span>  
  
 [<span data-ttu-id="121d5-122">生成、部署和调试自定义对象</span><span class="sxs-lookup"><span data-stu-id="121d5-122">Building, Deploying, and Debugging Custom Objects</span></span>](../building-deploying-and-debugging-custom-objects.md)  
 <span data-ttu-id="121d5-123">介绍生成、签名、部署和调试自定义对象的技术。</span><span class="sxs-lookup"><span data-stu-id="121d5-123">Describes the techniques for building, signing, deploying, and debugging custom objects.</span></span>  
  
### <a name="information-about-other-custom-objects"></a><span data-ttu-id="121d5-124">其他自定义对象的信息</span><span class="sxs-lookup"><span data-stu-id="121d5-124">Information about Other Custom Objects</span></span>  
 <span data-ttu-id="121d5-125">有关可在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中创建的其他自定义对象类型的信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="121d5-125">For information on the other types of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>  
  
 [<span data-ttu-id="121d5-126">开发自定义任务</span><span class="sxs-lookup"><span data-stu-id="121d5-126">Developing a Custom Task</span></span>](../task/developing-a-custom-task.md)  
 <span data-ttu-id="121d5-127">讨论如何对自定义任务进行编程。</span><span class="sxs-lookup"><span data-stu-id="121d5-127">Discusses how to program custom tasks.</span></span>  
  
 [<span data-ttu-id="121d5-128">开发自定义连接管理器</span><span class="sxs-lookup"><span data-stu-id="121d5-128">Developing a Custom Connection Manager</span></span>](../connection-manager/developing-a-custom-connection-manager.md)  
 <span data-ttu-id="121d5-129">讨论如何对自定义连接管理器进行编程。</span><span class="sxs-lookup"><span data-stu-id="121d5-129">Discusses how to program custom connection managers.</span></span>  
  
 [<span data-ttu-id="121d5-130">开发自定义日志提供程序</span><span class="sxs-lookup"><span data-stu-id="121d5-130">Developing a Custom Log Provider</span></span>](../log-provider/developing-a-custom-log-provider.md)  
 <span data-ttu-id="121d5-131">讨论如何对自定义日志提供程序进行编程。</span><span class="sxs-lookup"><span data-stu-id="121d5-131">Discusses how to program custom log providers.</span></span>  
  
 [<span data-ttu-id="121d5-132">开发自定义数据流组件</span><span class="sxs-lookup"><span data-stu-id="121d5-132">Developing a Custom Data Flow Component</span></span>](../data-flow/developing-a-custom-data-flow-component.md)  
 <span data-ttu-id="121d5-133">讨论如何对自定义数据流源、转换和目标进行编程。</span><span class="sxs-lookup"><span data-stu-id="121d5-133">Discusses how to program custom data flow sources, transformations, and destinations.</span></span>  
  
<span data-ttu-id="121d5-134">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="121d5-134">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="121d5-135">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="121d5-135">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="121d5-136">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="121d5-136">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="121d5-137">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="121d5-137">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
