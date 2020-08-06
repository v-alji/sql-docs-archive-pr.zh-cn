---
title: 开发自定义日志提供程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- SSIS packages, log providers
- custom log providers [Integration Services]
- SQL Server Integration Services packages, log providers
- log providers [Integration Services]
- packages [Integration Services], logs
- Integration Services packages, log providers
ms.assetid: 3f715b95-7074-4f5c-8ae2-246998052e78
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 88d4f70fa9d50628b831b56f9fa22100648fce51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578361"
---
# <a name="developing-a-custom-log-provider"></a><span data-ttu-id="5da56-102">开发自定义日志提供程序</span><span class="sxs-lookup"><span data-stu-id="5da56-102">Developing a Custom Log Provider</span></span>
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="5da56-103">所具有的广泛的日志记录功能使其可捕获在包执行过程中发生的事件。</span><span class="sxs-lookup"><span data-stu-id="5da56-103">has extensive logging capabilities that make it possible to capture events that occur during package execution.</span></span> [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="5da56-104">包含各种日志提供程序，可用于创建日志并以 XML、文本、数据库或 Windows 事件日志等格式存储这些日志。</span><span class="sxs-lookup"><span data-stu-id="5da56-104">includes a variety of log providers that enable logs to be created and stored in formats such as XML, text, database, or in the Windows event log.</span></span> <span data-ttu-id="5da56-105">如果提供的日志提供程序和输出格式不能完全满足您的需要，您可以创建自定义日志提供程序。</span><span class="sxs-lookup"><span data-stu-id="5da56-105">If the log providers and the output formats that are provided do not entirely meet your requirements, you can create a custom log provider.</span></span>

 <span data-ttu-id="5da56-106">若要创建自定义日志提供程序，必须创建从 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> 基类继承的类，再将 <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> 属性应用到新类，然后重写基类的重要方法和属性，包括 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> 属性和 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="5da56-106">To create a custom log provider, you have to create a class that inherits from the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> base class, apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> attribute to your new class, and override the important methods and properties of the base class, including the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> property and the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> method.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="5da56-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="5da56-107">In This Section</span></span>
 <span data-ttu-id="5da56-108">本节介绍如何创建、配置和编写自定义日志提供程序代码。</span><span class="sxs-lookup"><span data-stu-id="5da56-108">This section describes how to create, configure, and code a custom log provider.</span></span>

 <span data-ttu-id="5da56-109">[创建自定义日志提供程序](creating-a-custom-log-provider.md)介绍如何为自定义日志提供程序项目创建类。</span><span class="sxs-lookup"><span data-stu-id="5da56-109">[Creating a Custom Log Provider](creating-a-custom-log-provider.md) Describes how to create the classes for a custom log provider project.</span></span>

 <span data-ttu-id="5da56-110">[编写自定义日志提供程序代码](coding-a-custom-log-provider.md)介绍如何通过重写基类的方法和属性实现自定义日志提供程序。</span><span class="sxs-lookup"><span data-stu-id="5da56-110">[Coding a Custom Log Provider](coding-a-custom-log-provider.md) Describes how to implement a custom log provider by overriding the methods and properties of the base class.</span></span>

 <span data-ttu-id="5da56-111">[为自定义日志提供程序开发用户界面](developing-a-user-interface-for-a-custom-log-provider.md)中不支持自定义日志提供程序的自定义用户界面 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5da56-111">[Developing a User Interface for a Custom Log Provider](developing-a-user-interface-for-a-custom-log-provider.md) Custom user interfaces for custom log providers are not supported in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>

## <a name="related-topics"></a><span data-ttu-id="5da56-112">相关主题</span><span class="sxs-lookup"><span data-stu-id="5da56-112">Related Topics</span></span>

### <a name="information-common-to-all-custom-objects"></a><span data-ttu-id="5da56-113">所有自定义对象的通用信息</span><span class="sxs-lookup"><span data-stu-id="5da56-113">Information Common to all Custom Objects</span></span>
 <span data-ttu-id="5da56-114">有关可以在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中创建的所有类型自定义对象的通用信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="5da56-114">For information that is common to all the type of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>

 <span data-ttu-id="5da56-115">[开发 Integration Services 的自定义对象](../developing-custom-objects-for-integration-services.md)介绍实现的所有类型自定义对象的基本步骤 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5da56-115">[Developing Custom Objects for Integration Services](../developing-custom-objects-for-integration-services.md) Describes the basic steps in implementing all types of custom objects for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>

 <span data-ttu-id="5da56-116">[持久保存自定义对象](../persisting-custom-objects.md)描述自定义持久性，并在必要时对其进行说明。</span><span class="sxs-lookup"><span data-stu-id="5da56-116">[Persisting Custom Objects](../persisting-custom-objects.md) Describes custom persistence and explains when it is necessary.</span></span>

 <span data-ttu-id="5da56-117">[生成、部署和调试自定义对象](../building-deploying-and-debugging-custom-objects.md)介绍用于生成、签名、部署和调试自定义对象的方法。</span><span class="sxs-lookup"><span data-stu-id="5da56-117">[Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md) Describes the techniques for building, signing, deploying, and debugging custom objects.</span></span>

### <a name="information-about-other-custom-objects"></a><span data-ttu-id="5da56-118">其他自定义对象的信息</span><span class="sxs-lookup"><span data-stu-id="5da56-118">Information about Other Custom Objects</span></span>
 <span data-ttu-id="5da56-119">有关可在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中创建的其他自定义对象类型的信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="5da56-119">For information on the other types of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>

 <span data-ttu-id="5da56-120">[开发自定义任务](../task/developing-a-custom-task.md)讨论如何对自定义任务进行编程。</span><span class="sxs-lookup"><span data-stu-id="5da56-120">[Developing a Custom Task](../task/developing-a-custom-task.md) Discusses how to program custom tasks.</span></span>

 <span data-ttu-id="5da56-121">[开发自定义连接管理器](../connection-manager/developing-a-custom-connection-manager.md)讨论如何对自定义连接管理器进行编程。</span><span class="sxs-lookup"><span data-stu-id="5da56-121">[Developing a Custom Connection Manager](../connection-manager/developing-a-custom-connection-manager.md) Discusses how to program custom connection managers.</span></span>

 <span data-ttu-id="5da56-122">[开发自定义 ForEach 枚举器](../foreach-enumerator/developing-a-custom-foreach-enumerator.md)讨论如何对自定义枚举器进行编程。</span><span class="sxs-lookup"><span data-stu-id="5da56-122">[Developing a Custom ForEach Enumerator](../foreach-enumerator/developing-a-custom-foreach-enumerator.md) Discusses how to program custom enumerators.</span></span>

 <span data-ttu-id="5da56-123">[开发自定义数据流组件](../data-flow/developing-a-custom-data-flow-component.md)讨论如何对自定义数据流源、转换和目标进行编程。</span><span class="sxs-lookup"><span data-stu-id="5da56-123">[Developing a Custom Data Flow Component](../data-flow/developing-a-custom-data-flow-component.md) Discusses how to program custom data flow sources, transformations, and destinations.</span></span>

<span data-ttu-id="5da56-124">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="5da56-124">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="5da56-125">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="5da56-125">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="5da56-126">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="5da56-126">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="5da56-127">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="5da56-127">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>


