---
title: 以编程方式生成包 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 7474b1f4-7607-4f28-a6fd-67f7db1dd3f8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8ef8fd0b6b5bdeead718f204a0933771fe58924a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580840"
---
# <a name="building-packages-programmatically"></a><span data-ttu-id="a9df0-102">以编程方式生成包</span><span class="sxs-lookup"><span data-stu-id="a9df0-102">Building Packages Programmatically</span></span>
  <span data-ttu-id="a9df0-103">如果您需要动态创建包，或需要在开发环境之外管理和执行 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包，则可以采用编程方式对包进行操作。</span><span class="sxs-lookup"><span data-stu-id="a9df0-103">If you need to create packages dynamically, or to manage and execute [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages outside the development environment, you can manipulate packages programmatically.</span></span> <span data-ttu-id="a9df0-104">如果采用这种方法，则有一系列选择：</span><span class="sxs-lookup"><span data-stu-id="a9df0-104">In this approach, you have a continuous range of options:</span></span>

-   <span data-ttu-id="a9df0-105">加载并执行现有包，不进行修改。</span><span class="sxs-lookup"><span data-stu-id="a9df0-105">Load and execute an existing package without modification.</span></span>

-   <span data-ttu-id="a9df0-106">加载现有包，对其进行重新配置（例如，指定一个不同的数据源），然后执行。</span><span class="sxs-lookup"><span data-stu-id="a9df0-106">Load an existing package, reconfigure it (for example, for a different data source), and execute it.</span></span>

-   <span data-ttu-id="a9df0-107">创建一个新包，添加并配置组件（逐个对象和属性），保存并执行。</span><span class="sxs-lookup"><span data-stu-id="a9df0-107">Create a new package, add and configure components object by object and property by property, save it, and execute it.</span></span>

 <span data-ttu-id="a9df0-108">您可以使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 对象模型，以任何托管编程语言编写可创建、配置和执行包的代码。</span><span class="sxs-lookup"><span data-stu-id="a9df0-108">You can use the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] object model to write code that creates, configures, and executes packages in any managed programming language.</span></span> <span data-ttu-id="a9df0-109">例如，您可能希望创建元数据驱动的包，它们可以基于所选数据源及其表和列，配置它们的连接或数据源、转换和目标。</span><span class="sxs-lookup"><span data-stu-id="a9df0-109">For example, you may want to create metadata-driven packages that configure their connections or their data sources, transformations, and destinations based on the selected data source and its tables and columns.</span></span>

 <span data-ttu-id="a9df0-110">本节逐行介绍并演示如何以编程方式创建和配置包。</span><span class="sxs-lookup"><span data-stu-id="a9df0-110">This section describes and demonstrates how to create and configure a package programmatically line by line.</span></span> <span data-ttu-id="a9df0-111">如果选择复杂性最低的包编程方式，只需加载并运行现有包，不需要进行[以编程方式运行和管理包](../run-manage-packages-programmatically/running-and-managing-packages-programmatically.md)中所介绍的修改。</span><span class="sxs-lookup"><span data-stu-id="a9df0-111">At the less complex end of the range of package programming options, you can simply load and run an existing package without modification as described in [Running and Managing Packages Programmatically](../run-manage-packages-programmatically/running-and-managing-packages-programmatically.md).</span></span>

 <span data-ttu-id="a9df0-112">这里没有介绍一种中间方式，即将一个现有包加载为模板，对其进行重新配置（例如，指定一个不同的数据源），然后执行。</span><span class="sxs-lookup"><span data-stu-id="a9df0-112">An intermediate option not described here is that of loading an existing package as a template, reconfiguring it (for example, for a different data source), and executing it.</span></span> <span data-ttu-id="a9df0-113">您也可以使用本节中的信息，修改包中的现有对象。</span><span class="sxs-lookup"><span data-stu-id="a9df0-113">You can also use the information in this section to modify the existing objects in a package.</span></span>

> [!NOTE]
>  <span data-ttu-id="a9df0-114">将现有包用作模板并修改数据流中的现有列时，您可能必须删除现有列并调用受影响组件的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a9df0-114">When you use an existing package as a template and modify existing columns in the data flow, you may have to remove existing columns and call the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> method of affected components.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a9df0-115">本节内容</span><span class="sxs-lookup"><span data-stu-id="a9df0-115">In This Section</span></span>
 <span data-ttu-id="a9df0-116">[以编程方式创建包](../building-packages-programmatically/creating-a-package-programmatically.md)描述如何以编程方式创建包。</span><span class="sxs-lookup"><span data-stu-id="a9df0-116">[Creating a Package Programmatically](../building-packages-programmatically/creating-a-package-programmatically.md) Describes how to create a package programmatically.</span></span>

 <span data-ttu-id="a9df0-117">[以编程方式添加任务](../building-packages-programmatically/adding-tasks-programmatically.md)描述如何向包中添加任务。</span><span class="sxs-lookup"><span data-stu-id="a9df0-117">[Adding Tasks Programmatically](../building-packages-programmatically/adding-tasks-programmatically.md) Describes how to add tasks to the package.</span></span>

 <span data-ttu-id="a9df0-118">[以编程方式连接任务](../building-packages-programmatically/connecting-tasks-programmatically.md)介绍如何根据上一个任务或容器的执行结果来控制包中的容器和任务的执行。</span><span class="sxs-lookup"><span data-stu-id="a9df0-118">[Connecting Tasks Programmatically](../building-packages-programmatically/connecting-tasks-programmatically.md) Describes how to control execution of the containers and tasks in a package based on the result of the execution of a previous task or container.</span></span>

 <span data-ttu-id="a9df0-119">[以编程方式添加连接](../building-packages-programmatically/adding-connections-programmatically.md)描述如何将连接管理器添加到包。</span><span class="sxs-lookup"><span data-stu-id="a9df0-119">[Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md) Describes how to add connection managers to a package.</span></span>

 <span data-ttu-id="a9df0-120">[以编程方式使用变量](../building-packages-programmatically/working-with-variables-programmatically.md)描述如何在包执行期间添加和使用变量。</span><span class="sxs-lookup"><span data-stu-id="a9df0-120">[Working with Variables Programmatically](../building-packages-programmatically/working-with-variables-programmatically.md) Describes how to add and use variables during package execution.</span></span>

 <span data-ttu-id="a9df0-121">[以编程方式处理事件](../building-packages-programmatically/handling-events-programmatically.md)描述如何处理包和任务事件。</span><span class="sxs-lookup"><span data-stu-id="a9df0-121">[Handling Events Programmatically](../building-packages-programmatically/handling-events-programmatically.md) Describes how to handle package and task events.</span></span>

 <span data-ttu-id="a9df0-122">[以编程方式启用日志记录](../building-packages-programmatically/enabling-logging-programmatically.md)描述如何为包或任务启用日志记录，以及如何将自定义筛选器应用于记录事件。</span><span class="sxs-lookup"><span data-stu-id="a9df0-122">[Enabling Logging Programmatically](../building-packages-programmatically/enabling-logging-programmatically.md) Describes how to enable logging for a package or task, and how to apply custom filters to log events.</span></span>

 <span data-ttu-id="a9df0-123">[以编程方式添加数据流任务](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md)介绍如何添加和配置数据流任务及其组件。</span><span class="sxs-lookup"><span data-stu-id="a9df0-123">[Adding the Data Flow Task Programmatically](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md) Describes how to add and configure the Data Flow task and its components.</span></span>

 <span data-ttu-id="a9df0-124">[以编程方式查找数据流组件](../building-packages-programmatically/discovering-data-flow-components-programmatically.md)描述如何检测本地计算机上安装的组件。</span><span class="sxs-lookup"><span data-stu-id="a9df0-124">[Discovering Data Flow Components Programmatically](../building-packages-programmatically/discovering-data-flow-components-programmatically.md) Describes how to detect the components that are installed on the local computer.</span></span>

 <span data-ttu-id="a9df0-125">[以编程方式添加数据流组件](../building-packages-programmatically/adding-data-flow-components-programmatically.md)描述如何将组件添加到数据流任务。</span><span class="sxs-lookup"><span data-stu-id="a9df0-125">[Adding Data Flow Components Programmatically](../building-packages-programmatically/adding-data-flow-components-programmatically.md) Describes how to add a component to a data flow task.</span></span>

 <span data-ttu-id="a9df0-126">[以编程方式连接数据流组件](../building-packages-programmatically/connecting-data-flow-components-programmatically.md)介绍如何连接两个数据流组件。</span><span class="sxs-lookup"><span data-stu-id="a9df0-126">[Connecting Data Flow Components Programmatically](../building-packages-programmatically/connecting-data-flow-components-programmatically.md) Describes how to connect two data flow components.</span></span>

 <span data-ttu-id="a9df0-127">[以编程方式选择输入列](../building-packages-programmatically/selecting-input-columns-programmatically.md)描述如何从数据流中的上游组件向组件提供的输入列。</span><span class="sxs-lookup"><span data-stu-id="a9df0-127">[Selecting Input Columns Programmatically](../building-packages-programmatically/selecting-input-columns-programmatically.md) Describes how to select input columns from those that are provided to a component by upstream components in the data flow.</span></span>

 <span data-ttu-id="a9df0-128">[以编程方式保存包](../building-packages-programmatically/saving-a-package-programmatically.md)描述如何以编程方式保存包。</span><span class="sxs-lookup"><span data-stu-id="a9df0-128">[Saving a Package Programmatically](../building-packages-programmatically/saving-a-package-programmatically.md) Describes how to save a package programmatically.</span></span>

## <a name="reference"></a><span data-ttu-id="a9df0-129">参考</span><span class="sxs-lookup"><span data-stu-id="a9df0-129">Reference</span></span>
 <span data-ttu-id="a9df0-130">[Integration Services 错误和消息引用](../integration-services-error-and-message-reference.md)列出预定义的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 错误代码及其符号名称和说明。</span><span class="sxs-lookup"><span data-stu-id="a9df0-130">[Integration Services Error and Message Reference](../integration-services-error-and-message-reference.md) Lists the predefined [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] error codes with their symbolic names and descriptions.</span></span>

## <a name="related-sections"></a><span data-ttu-id="a9df0-131">相关章节</span><span class="sxs-lookup"><span data-stu-id="a9df0-131">Related Sections</span></span>
 <span data-ttu-id="a9df0-132">[用脚本扩展包](../extending-packages-scripting/extending-packages-with-scripting.md)讨论如何使用脚本任务扩展控制流，以及如何使用脚本组件扩展数据流。</span><span class="sxs-lookup"><span data-stu-id="a9df0-132">[Extending Packages with Scripting](../extending-packages-scripting/extending-packages-with-scripting.md) Discusses how to extend the control flow by using the Script task, and how to extend the data flow by using the Script component.</span></span>

 <span data-ttu-id="a9df0-133">[用自定义对象扩展包](../extending-packages-custom-objects/extending-packages-with-custom-objects.md)讨论如何创建程序自定义任务、数据流组件和其他包对象以便在多个包中使用。</span><span class="sxs-lookup"><span data-stu-id="a9df0-133">[Extending Packages with Custom Objects](../extending-packages-custom-objects/extending-packages-with-custom-objects.md) Discusses how to create program custom tasks, data flow components, and other package objects for use in multiple packages.</span></span>

 <span data-ttu-id="a9df0-134">[以编程方式运行和管理包](../run-manage-packages-programmatically/running-and-managing-packages-programmatically.md)讨论如何枚举、运行和管理包以及存储包的文件夹。</span><span class="sxs-lookup"><span data-stu-id="a9df0-134">[Running and Managing Packages Programmatically](../run-manage-packages-programmatically/running-and-managing-packages-programmatically.md) Discusses how to enumerate, run, and manage packages and the folders in which they are stored.</span></span>

## <a name="external-resources"></a><span data-ttu-id="a9df0-135">外部资源</span><span class="sxs-lookup"><span data-stu-id="a9df0-135">External Resources</span></span>

-   <span data-ttu-id="a9df0-136"> [www.codeplex.com/MSFTISProdSamples](www.codeplex.com/MSFTISProdSamples) 上的 CodePlex 示例 [Integration Services 产品示例](https://go.microsoft.com/fwlink/?LinkID=131204)</span><span class="sxs-lookup"><span data-stu-id="a9df0-136">CodePlex samples, [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkID=131204), on www.codeplex.com/MSFTISProdSamples</span></span>

-   <span data-ttu-id="a9df0-137">blogs.msdn.com 上的博客文章[自定义扩展插件性能探查](https://go.microsoft.com/fwlink/?LinkId=238831)</span><span class="sxs-lookup"><span data-stu-id="a9df0-137">Blog entry, [Performance profiling your custom extensions](https://go.microsoft.com/fwlink/?LinkId=238831), on blogs.msdn.com.</span></span>

<span data-ttu-id="a9df0-138">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="a9df0-138">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="a9df0-139">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="a9df0-139">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="a9df0-140">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="a9df0-140">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="a9df0-141">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="a9df0-141">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9df0-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a9df0-142">See Also</span></span>
 [<span data-ttu-id="a9df0-143">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="a9df0-143">SQL Server Integration Services</span></span>](../sql-server-integration-services.md)


