---
title: 使用脚本任务扩展包 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- scripts [Integration Services]
- SSIS Script task
- tasks [Integration Services], scripts
- Script task [Integration Services], about Script task
- scripts [Integration Services], about Script task with packages
- SSIS Script task, about Script task
ms.assetid: 911e6d26-a6fd-4fc3-a111-bf5f048e9bff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5f1a265b01a898cdc87bdf9df6cb67399879061b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689529"
---
# <a name="extending-the-package-with-the-script-task"></a><span data-ttu-id="ba275-102">使用脚本任务扩展包</span><span class="sxs-lookup"><span data-stu-id="ba275-102">Extending the Package with the Script Task</span></span>
  <span data-ttu-id="ba275-103">脚本任务通过以 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 或 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] Visual C# 编写，在包运行时编译和执行的自定义代码来扩展 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 包的运行时功能。</span><span class="sxs-lookup"><span data-stu-id="ba275-103">The Script task extends the run-time capabilities of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] packages with custom code written in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# that is compiled and executed at package run time.</span></span> <span data-ttu-id="ba275-104">当 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 包含的任务不能满足您的要求时，脚本任务可简化自定义运行时任务的开发。</span><span class="sxs-lookup"><span data-stu-id="ba275-104">The Script task simplifies the development of a custom run-time task when the tasks included with [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] do not fully satisfy your requirements.</span></span> <span data-ttu-id="ba275-105">脚本任务可用于编写所有必需的基础结构代码，这样您就可以只将注意力集中于自定义处理所需的代码。</span><span class="sxs-lookup"><span data-stu-id="ba275-105">The Script task writes all the required infrastructure code for you, letting you focus exclusively on the code that is required for your custom processing.</span></span>  
  
 <span data-ttu-id="ba275-106">脚本任务通过全局 `Dts` 对象，即在脚本环境中公开的 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> 类实例与包含包进行交互。</span><span class="sxs-lookup"><span data-stu-id="ba275-106">A Script task interacts with the containing package through the global `Dts` object, an instance of the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> class that is exposed in the scripting environment.</span></span> <span data-ttu-id="ba275-107">可以在脚本任务中编写用于修改存储在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 变量中的值的代码；稍后，包可使用这些更新值来确定其工作流的路径。</span><span class="sxs-lookup"><span data-stu-id="ba275-107">You can write code in a Script task that modifies the values stored in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] variables; later, the package can use those updated values to determine the path of its workflow.</span></span> <span data-ttu-id="ba275-108">脚本任务还可以使用 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 命名空间、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 类库以及自定义程序集来实现自定义功能。</span><span class="sxs-lookup"><span data-stu-id="ba275-108">The Script task can also use the [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] namespace and the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] class library, as well as custom assemblies, to implement custom functionality.</span></span>  
  
 <span data-ttu-id="ba275-109">脚本任务及其生成的基础结构代码可大大简化自定义任务的开发过程。</span><span class="sxs-lookup"><span data-stu-id="ba275-109">The Script task and the infrastructure code that it generates for you simplify significantly the process of developing a custom task.</span></span> <span data-ttu-id="ba275-110">但是，若要了解脚本任务的工作方式，阅读[开发自定义任务](../../extending-packages-custom-objects/task/developing-a-custom-task.md)部分以了解开发自定义任务的步骤很有帮助。</span><span class="sxs-lookup"><span data-stu-id="ba275-110">However, to understand how the Script task works, you may find it useful to read the section [Developing a Custom Task](../../extending-packages-custom-objects/task/developing-a-custom-task.md) to understand the steps that are involved in developing a custom task.</span></span>  
  
 <span data-ttu-id="ba275-111">如果要创建计划在多个包中重用的任务，则应考虑开发自定义任务，而不使用脚本任务。</span><span class="sxs-lookup"><span data-stu-id="ba275-111">If you are creating a task that you plan to reuse in multiple packages, you should consider developing a custom task instead of using the Script task.</span></span> <span data-ttu-id="ba275-112">有关详细信息，请参阅[比较脚本解决方案与自定义对象](../comparing-scripting-solutions-and-custom-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="ba275-112">For more information, see [Comparing Scripting Solutions and Custom Objects](../comparing-scripting-solutions-and-custom-objects.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ba275-113">本节内容</span><span class="sxs-lookup"><span data-stu-id="ba275-113">In This Section</span></span>  
 <span data-ttu-id="ba275-114">下列主题提供有关脚本任务的详细信息。</span><span class="sxs-lookup"><span data-stu-id="ba275-114">The following topics provide more information about the Script task.</span></span>  
  
 [<span data-ttu-id="ba275-115">在脚本任务编辑器中配置脚本任务</span><span class="sxs-lookup"><span data-stu-id="ba275-115">Configuring the Script Task in the Script Task Editor</span></span>](configuring-the-script-task-in-the-script-task-editor.md)  
 <span data-ttu-id="ba275-116">说明在“脚本任务编辑器”  中配置的属性如何影响脚本任务中代码的功能和性能。</span><span class="sxs-lookup"><span data-stu-id="ba275-116">Explains how the properties that you configure in the **Script Task Editor** affect the capabilities and the performance of the code in the Script task.</span></span>  
  
 [<span data-ttu-id="ba275-117">脚本任务的编码和调试</span><span class="sxs-lookup"><span data-stu-id="ba275-117">Coding and Debugging the Script Task</span></span>](../../control-flow/script-task.md)  
 <span data-ttu-id="ba275-118">说明如何使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) 开发包含在脚本任务中的脚本。</span><span class="sxs-lookup"><span data-stu-id="ba275-118">Explains how to use [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) to develop the scripts that are contained in the Script task.</span></span>  
  
 [<span data-ttu-id="ba275-119">在脚本任务中使用变量</span><span class="sxs-lookup"><span data-stu-id="ba275-119">Using Variables in the Script Task</span></span>](using-variables-in-the-script-task.md)  
 <span data-ttu-id="ba275-120">说明如何通过 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 属性使用变量。</span><span class="sxs-lookup"><span data-stu-id="ba275-120">Explains how to use variables through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property.</span></span>  
  
 [<span data-ttu-id="ba275-121">在脚本任务中连接数据源</span><span class="sxs-lookup"><span data-stu-id="ba275-121">Connecting to Data Sources in the Script Task</span></span>](connecting-to-data-sources-in-the-script-task.md)  
 <span data-ttu-id="ba275-122">说明如何通过 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> 属性使用连接。</span><span class="sxs-lookup"><span data-stu-id="ba275-122">Explains how to use connections through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> property.</span></span>  
  
 [<span data-ttu-id="ba275-123">在脚本任务中引发事件</span><span class="sxs-lookup"><span data-stu-id="ba275-123">Raising Events in the Script Task</span></span>](raising-events-in-the-script-task.md)  
 <span data-ttu-id="ba275-124">说明如何通过 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> 属性引发事件。</span><span class="sxs-lookup"><span data-stu-id="ba275-124">Explains how to raise events through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> property.</span></span>  
  
 [<span data-ttu-id="ba275-125">脚本任务中的日志记录</span><span class="sxs-lookup"><span data-stu-id="ba275-125">Logging in the Script Task</span></span>](logging-in-the-script-task.md)  
 <span data-ttu-id="ba275-126">说明如何通过 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> 方法记录信息。</span><span class="sxs-lookup"><span data-stu-id="ba275-126">Explains how to log information through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> method.</span></span>  
  
 [<span data-ttu-id="ba275-127">从脚本任务返回结果</span><span class="sxs-lookup"><span data-stu-id="ba275-127">Returning Results from the Script Task</span></span>](returning-results-from-the-script-task.md)  
 <span data-ttu-id="ba275-128">说明如何通过 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> 属性和 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> 属性返回结果。</span><span class="sxs-lookup"><span data-stu-id="ba275-128">Explains how to return results through the property <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> and the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> property.</span></span>  
  
 [<span data-ttu-id="ba275-129">脚本任务示例</span><span class="sxs-lookup"><span data-stu-id="ba275-129">Script Task Examples</span></span>](../../extending-packages-scripting-task-examples/script-task-examples.md)  
 <span data-ttu-id="ba275-130">提供一些简单的示例，演示脚本任务的几种可能用法。</span><span class="sxs-lookup"><span data-stu-id="ba275-130">Provides simple examples that demonstrate several possible uses for a Script task.</span></span>  
  
<span data-ttu-id="ba275-131">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="ba275-131">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="ba275-132">若要从 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="ba275-132">For the latest downloads, articles, samples, and videos from [!INCLUDE[msCoName](../../../includes/msconame-md.md)], as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="ba275-133">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="ba275-133">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="ba275-134">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="ba275-134">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba275-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ba275-135">See Also</span></span>  
 <span data-ttu-id="ba275-136">[脚本任务](../../control-flow/script-task.md) </span><span class="sxs-lookup"><span data-stu-id="ba275-136">[Script Task](../../control-flow/script-task.md) </span></span>  
 [<span data-ttu-id="ba275-137">比较脚本任务和脚本组件</span><span class="sxs-lookup"><span data-stu-id="ba275-137">Comparing the Script Task and the Script Component</span></span>](../../extending-packages-scripting/comparing-the-script-task-and-the-script-component.md)  
  
  
