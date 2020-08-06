---
title: 开发自定义数据流组件 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow task [Integration Services], extending
- data flow [Integration Services], extending
- extending data flow task [Integration Services]
- components [Integration Services], data flow
ms.assetid: be126913-2a9a-41c9-9bf5-a7b0a0aea2f8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7126129ede3f419c6fbdcae6245a47636e6e65ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690763"
---
# <a name="developing-a-custom-data-flow-component"></a><span data-ttu-id="46ab3-102">开发自定义数据流组件</span><span class="sxs-lookup"><span data-stu-id="46ab3-102">Developing a Custom Data Flow Component</span></span>
  <span data-ttu-id="46ab3-103">数据流任务由一些组件组成，这些组件用于连接各种数据源，然后快速转换和路由数据。</span><span class="sxs-lookup"><span data-stu-id="46ab3-103">The data flow task consists of components that connect to a variety of data sources and then transform and route that data at high speed.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="46ab3-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 提供一个可扩展的对象模型，该模型允许开发人员创建可在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 和已部署的包中使用的自定义源、转换和目标。</span><span class="sxs-lookup"><span data-stu-id="46ab3-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] provides an extensible object model that lets developers create custom sources, transformations, and destinations that you can use in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] and in deployed packages.</span></span> <span data-ttu-id="46ab3-105">本节包含的主题将指导您开发自定义数据流组件。</span><span class="sxs-lookup"><span data-stu-id="46ab3-105">This section contains topics that will guide you in developing custom data flow components.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="46ab3-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="46ab3-106">In This Section</span></span>
 <span data-ttu-id="46ab3-107">[创建自定义数据流组件](creating-a-custom-data-flow-component.md)介绍创建自定义数据流组件的初始步骤。</span><span class="sxs-lookup"><span data-stu-id="46ab3-107">[Creating a Custom Data Flow Component](creating-a-custom-data-flow-component.md) Describes the initial steps in creating a custom data flow component.</span></span>

 <span data-ttu-id="46ab3-108">数据流[组件的设计时方法](design-time-methods-of-a-data-flow-component.md)描述要在自定义数据流组件中实现的设计时方法。</span><span class="sxs-lookup"><span data-stu-id="46ab3-108">[Design-time Methods of a Data Flow Component](design-time-methods-of-a-data-flow-component.md) Describes the design-time methods to implement in a custom data flow component.</span></span>

 <span data-ttu-id="46ab3-109">数据流[组件的运行时方法](run-time-methods-of-a-data-flow-component.md)描述要在自定义数据流组件中实现的运行时方法。</span><span class="sxs-lookup"><span data-stu-id="46ab3-109">[Run-time Methods of a Data Flow Component](run-time-methods-of-a-data-flow-component.md) Describes the run-time methods to implement in a custom data flow component.</span></span>

 <span data-ttu-id="46ab3-110">[执行计划和缓冲区分配](execution-plan-and-buffer-allocation.md)介绍数据流执行计划和数据缓冲区分配。</span><span class="sxs-lookup"><span data-stu-id="46ab3-110">[Execution Plan and Buffer Allocation](execution-plan-and-buffer-allocation.md) Describes the data flow execution plan and the allocation of data buffers.</span></span>

 <span data-ttu-id="46ab3-111">使用数据流[中的数据类型](working-with-data-types-in-the-data-flow.md)说明数据流如何将 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 数据类型映射到 .NET Framework 托管数据类型。</span><span class="sxs-lookup"><span data-stu-id="46ab3-111">[Working with Data Types in the Data Flow](working-with-data-types-in-the-data-flow.md) Explains how the data flow maps [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] data types to .NET Framework managed data types.</span></span>

 <span data-ttu-id="46ab3-112">[验证数据流组件](validating-a-data-flow-component.md)说明用于验证组件配置和重新配置组件元数据的方法。</span><span class="sxs-lookup"><span data-stu-id="46ab3-112">[Validating a Data Flow Component](validating-a-data-flow-component.md) Explains the methods used to validate component configuration and to reconfigure component metadata.</span></span>

 <span data-ttu-id="46ab3-113">[实现外部元数据](implementing-external-metadata.md)说明如何使用外部元数据列进行数据验证。</span><span class="sxs-lookup"><span data-stu-id="46ab3-113">[Implementing External Metadata](implementing-external-metadata.md) Explains how to use external metadata columns for data validation.</span></span>

 <span data-ttu-id="46ab3-114">[在数据流组件中引发和定义事件](raising-and-defining-events-in-a-data-flow-component.md)介绍如何引发预定义事件和自定义事件。</span><span class="sxs-lookup"><span data-stu-id="46ab3-114">[Raising and Defining Events in a Data Flow Component](raising-and-defining-events-in-a-data-flow-component.md) Explains how to raise predefined and custom events.</span></span>

 <span data-ttu-id="46ab3-115">[在数据流组件中记录和定义日志条目](logging-and-defining-log-entries-in-a-data-flow-component.md)说明如何创建和写入自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="46ab3-115">[Logging and Defining Log Entries in a Data Flow Component](logging-and-defining-log-entries-in-a-data-flow-component.md) Explains how to create and write to custom log entries.</span></span>

 <span data-ttu-id="46ab3-116">[在数据流组件中使用错误输出](using-error-outputs-in-a-data-flow-component.md)说明如何将错误行重定向到其他输出。</span><span class="sxs-lookup"><span data-stu-id="46ab3-116">[Using Error Outputs in a Data Flow Component](using-error-outputs-in-a-data-flow-component.md) Explains how to redirect error rows to an alternative output.</span></span>

 <span data-ttu-id="46ab3-117">[升级数据流组件的版本](upgrading-the-version-of-a-data-flow-component.md)说明如何在首次使用组件的新版本时更新已保存的组件元数据。</span><span class="sxs-lookup"><span data-stu-id="46ab3-117">[Upgrading the Version of a Data Flow Component](upgrading-the-version-of-a-data-flow-component.md) Explains how to update saved component metadata when a new version of your component is first used.</span></span>

 <span data-ttu-id="46ab3-118">[为数据流组件开发用户界面](developing-a-user-interface-for-a-data-flow-component.md)说明如何实现组件的自定义编辑器。</span><span class="sxs-lookup"><span data-stu-id="46ab3-118">[Developing a User Interface for a Data Flow Component](developing-a-user-interface-for-a-data-flow-component.md) Explains how to implement a custom editor for a component.</span></span>

 <span data-ttu-id="46ab3-119">[开发特定类型的数据流组件](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)介绍如何开发这三种类型的数据流组件：源、转换和目标。</span><span class="sxs-lookup"><span data-stu-id="46ab3-119">[Developing Specific Types of Data Flow Components](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md) Contains information about developing the three types of data flow components: sources, transformations, and destinations.</span></span>

## <a name="reference"></a><span data-ttu-id="46ab3-120">参考</span><span class="sxs-lookup"><span data-stu-id="46ab3-120">Reference</span></span>
 <span data-ttu-id="46ab3-121"><xref:Microsoft.SqlServer.Dts.Pipeline>包含用于创建自定义数据流组件的类和接口。</span><span class="sxs-lookup"><span data-stu-id="46ab3-121"><xref:Microsoft.SqlServer.Dts.Pipeline> Contains the classes and interfaces used to create custom data flow components.</span></span>

 <span data-ttu-id="46ab3-122"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>包含组成数据流任务对象模型的类和接口，用于创建自定义数据流组件或生成数据流任务。</span><span class="sxs-lookup"><span data-stu-id="46ab3-122"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper> Contains the classes and interfaces that make up the data flow task object model, and is used to create custom data flow components or build a data flow task.</span></span>

 <span data-ttu-id="46ab3-123"><xref:Microsoft.SqlServer.Dts.Pipeline.Design>包含用于创建数据流组件的用户界面的类和接口。</span><span class="sxs-lookup"><span data-stu-id="46ab3-123"><xref:Microsoft.SqlServer.Dts.Pipeline.Design> Contains the classes and interfaces used to create the user interface for data flow components.</span></span>

 <span data-ttu-id="46ab3-124">[Integration Services 错误和消息引用](../../integration-services-error-and-message-reference.md)列出预定义的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 错误代码及其符号名称和说明。</span><span class="sxs-lookup"><span data-stu-id="46ab3-124">[Integration Services Error and Message Reference](../../integration-services-error-and-message-reference.md) Lists the predefined [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] error codes with their symbolic names and descriptions.</span></span>

## <a name="related-sections"></a><span data-ttu-id="46ab3-125">相关章节</span><span class="sxs-lookup"><span data-stu-id="46ab3-125">Related Sections</span></span>

### <a name="information-common-to-all-custom-objects"></a><span data-ttu-id="46ab3-126">所有自定义对象的通用信息</span><span class="sxs-lookup"><span data-stu-id="46ab3-126">Information Common to All Custom Objects</span></span>
 <span data-ttu-id="46ab3-127">有关可以在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中创建的所有类型自定义对象的通用信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="46ab3-127">For information that is common to all the type of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>

 <span data-ttu-id="46ab3-128">[开发 Integration Services 的自定义对象](../../extending-packages-custom-objects/developing-custom-objects-for-integration-services.md)介绍实现的所有类型自定义对象的基本步骤 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="46ab3-128">[Developing Custom Objects for Integration Services](../../extending-packages-custom-objects/developing-custom-objects-for-integration-services.md) Describes the basic steps in implementing all types of custom objects for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>

 <span data-ttu-id="46ab3-129">[持久保存自定义对象](../../extending-packages-custom-objects/persisting-custom-objects.md)描述自定义持久性，并在必要时对其进行说明。</span><span class="sxs-lookup"><span data-stu-id="46ab3-129">[Persisting Custom Objects](../../extending-packages-custom-objects/persisting-custom-objects.md) Describes custom persistence and explains when it is necessary.</span></span>

 <span data-ttu-id="46ab3-130">[生成、部署和调试自定义对象](../../extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)介绍用于生成、签名、部署和调试自定义对象的方法。</span><span class="sxs-lookup"><span data-stu-id="46ab3-130">[Building, Deploying, and Debugging Custom Objects](../../extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md) Describes the techniques for building, signing, deploying, and debugging custom objects.</span></span>

### <a name="information-about-other-custom-objects"></a><span data-ttu-id="46ab3-131">其他自定义对象的信息</span><span class="sxs-lookup"><span data-stu-id="46ab3-131">Information about Other Custom Objects</span></span>
 <span data-ttu-id="46ab3-132">有关可在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中创建的其他自定义对象类型的信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="46ab3-132">For information on the other types of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>

 <span data-ttu-id="46ab3-133">[开发自定义任务](../../extending-packages-custom-objects/task/developing-a-custom-task.md)讨论如何对自定义任务进行编程。</span><span class="sxs-lookup"><span data-stu-id="46ab3-133">[Developing a Custom Task](../../extending-packages-custom-objects/task/developing-a-custom-task.md) Discusses how to program custom tasks.</span></span>

 <span data-ttu-id="46ab3-134">[开发自定义连接管理器](../../extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md)讨论如何对自定义连接管理器进行编程。</span><span class="sxs-lookup"><span data-stu-id="46ab3-134">[Developing a Custom Connection Manager](../../extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md) Discusses how to program custom connection managers.</span></span>

 <span data-ttu-id="46ab3-135">[开发自定义日志提供程序](../../extending-packages-custom-objects/log-provider/developing-a-custom-log-provider.md)讨论如何对自定义日志提供程序进行编程。</span><span class="sxs-lookup"><span data-stu-id="46ab3-135">[Developing a Custom Log Provider](../../extending-packages-custom-objects/log-provider/developing-a-custom-log-provider.md) Discusses how to program custom log providers.</span></span>

 <span data-ttu-id="46ab3-136">[开发自定义 ForEach 枚举器](../../extending-packages-custom-objects/foreach-enumerator/developing-a-custom-foreach-enumerator.md)讨论如何对自定义枚举器进行编程。</span><span class="sxs-lookup"><span data-stu-id="46ab3-136">[Developing a Custom ForEach Enumerator](../../extending-packages-custom-objects/foreach-enumerator/developing-a-custom-foreach-enumerator.md) Discusses how to program custom enumerators.</span></span>

<span data-ttu-id="46ab3-137">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="46ab3-137">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="46ab3-138">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="46ab3-138">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="46ab3-139">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="46ab3-139">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="46ab3-140">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="46ab3-140">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="46ab3-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="46ab3-141">See Also</span></span>
 <span data-ttu-id="46ab3-142">[用脚本组件扩展数据流] (。/..[比较脚本解决方案和自定义对象的](../../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md</span><span class="sxs-lookup"><span data-stu-id="46ab3-142">[Extending the Data Flow with the Script Component](../../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md [Comparing Scripting Solutions and Custom Objects](../../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)</span></span>


