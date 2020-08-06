---
title: 脚本任务 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scripttask.f1
helpviewer_keywords:
- scripts [Integration Services], tasks
- Script task [Integration Services], about Script task
- Script task [Integration Services]
ms.assetid: f6cce7df-4bd6-4b75-9f89-6c37b4bb5558
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 69c051994eb06cbab041db3db2683a487a6e1994
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576925"
---
# <a name="script-task"></a><span data-ttu-id="ab257-102">脚本任务</span><span class="sxs-lookup"><span data-stu-id="ab257-102">Script Task</span></span>
  <span data-ttu-id="ab257-103">脚本任务提供代码来执行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 内置任务和转换中不可用的函数。</span><span class="sxs-lookup"><span data-stu-id="ab257-103">The Script task provides code to perform functions that are not available in the built-in tasks and transformations that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides.</span></span> <span data-ttu-id="ab257-104">脚本任务还可将函数组合到一个脚本中，而不必使用多个任务和转换。</span><span class="sxs-lookup"><span data-stu-id="ab257-104">The Script task can also combine functions in one script instead of using multiple tasks and transformations.</span></span> <span data-ttu-id="ab257-105">脚本任务用于执行必须在包中一次完成（或每个枚举对象一次完成）、而不是每个数据行一次完成的工作。</span><span class="sxs-lookup"><span data-stu-id="ab257-105">You use the Script task for work that must be done once in a package (or once per enumerated object), instead than once per data row.</span></span>  
  
 <span data-ttu-id="ab257-106">可以将脚本任务用于下列目的：</span><span class="sxs-lookup"><span data-stu-id="ab257-106">You can use the Script task for the following purposes:</span></span>  
  
-   <span data-ttu-id="ab257-107">用内置连接类型不支持的其他技术访问数据。</span><span class="sxs-lookup"><span data-stu-id="ab257-107">Access data by using other technologies that are not supported by built-in connection types.</span></span> <span data-ttu-id="ab257-108">例如，脚本可使用 Active Directory 服务接口 (ADSI) 访问 Active Directory，并从中提取用户名。</span><span class="sxs-lookup"><span data-stu-id="ab257-108">For example, a script can use Active Directory Service Interfaces (ADSI) to access and extract user names from Active Directory.</span></span>  
  
-   <span data-ttu-id="ab257-109">创建特定于包的性能计数器。</span><span class="sxs-lookup"><span data-stu-id="ab257-109">Create a package-specific performance counter.</span></span> <span data-ttu-id="ab257-110">例如，脚本可以创建一个性能计数器，在运行复杂任务或性能差的任务时，该计数器将被更新。</span><span class="sxs-lookup"><span data-stu-id="ab257-110">For example, a script can create a performance counter that is updated while a complex or poorly performing task runs.</span></span>  
  
-   <span data-ttu-id="ab257-111">标识是否指定的文件为空或它们包含多少行，然后基于该信息影响包中的控制流。</span><span class="sxs-lookup"><span data-stu-id="ab257-111">Identify whether specified files are empty or how many rows they contain, and then based on that information affect the control flow in a package.</span></span> <span data-ttu-id="ab257-112">例如，如果文件包含零行，则将变量的值设置为 0，然后计算该值的优先约束将防止文件系统任务复制此文件。</span><span class="sxs-lookup"><span data-stu-id="ab257-112">For example, if a file contains zero rows, the value of a variable set to 0, and a precedence constraint that evaluates the value prevents a File System task from copying the file.</span></span>  
  
 <span data-ttu-id="ab257-113">如果必须使用脚本对集中的每个数据行执行相同的工作，则应当使用脚本组件而不是脚本任务。</span><span class="sxs-lookup"><span data-stu-id="ab257-113">If you have to use the script to do the same work for each row of data in a set, you should use the Script component instead of the Script task.</span></span> <span data-ttu-id="ab257-114">例如，如果希望评估邮资金额的合理性，从而跳过金额极高或极低的数据行，则应当使用脚本组件。</span><span class="sxs-lookup"><span data-stu-id="ab257-114">For example, if you want to assess the reasonableness of a postage amount and skip data rows that have very high or low amounts, you would use a Script component.</span></span> <span data-ttu-id="ab257-115">有关详细信息，请参阅 [Script Component](../data-flow/transformations/script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="ab257-115">For more information, see [Script Component](../data-flow/transformations/script-component.md).</span></span>  
  
 <span data-ttu-id="ab257-116">如果多个包使用一个脚本，请考虑使用自定义任务而不要使用脚本任务。</span><span class="sxs-lookup"><span data-stu-id="ab257-116">If more than one package uses a script, consider writing a custom task instead of using the Script task.</span></span> <span data-ttu-id="ab257-117">有关详细信息，请参阅 [开发自定义任务](../extending-packages-custom-objects/task/developing-a-custom-task.md)。</span><span class="sxs-lookup"><span data-stu-id="ab257-117">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
 <span data-ttu-id="ab257-118">确定脚本任务是包的正确选择之后，必须开发该任务使用的脚本，还必须配置任务本身。</span><span class="sxs-lookup"><span data-stu-id="ab257-118">After you decide that the Script task is the appropriate choice for your package, you have to both develop the script that the task uses and configure the task itself.</span></span>  
  
## <a name="writing-and-running-the-script-that-the-task-uses"></a><span data-ttu-id="ab257-119">编写和运行任务使用的脚本</span><span class="sxs-lookup"><span data-stu-id="ab257-119">Writing and Running the Script that the Task Uses</span></span>  
 <span data-ttu-id="ab257-120">脚本任务将 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) 用作编写脚本的环境和运行这些脚本的引擎。</span><span class="sxs-lookup"><span data-stu-id="ab257-120">The Script task uses [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) as the environment in which you write the scripts and the engine that runs those scripts.</span></span>  
  
 <span data-ttu-id="ab257-121">VSTA 提供 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 环境的所有标准功能，如具有颜色编码的 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 编辑器、IntelliSense 和“对象资源管理器”  。</span><span class="sxs-lookup"><span data-stu-id="ab257-121">VSTA provides all the standard features of the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] environment, such as the color-coded [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] editor, IntelliSense, and **Object Explorer**.</span></span> <span data-ttu-id="ab257-122">VSTA 还可以使用与其他 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 开发工具使用的调试器。</span><span class="sxs-lookup"><span data-stu-id="ab257-122">VSTA also uses the same debugger that other [!INCLUDE[msCoName](../../includes/msconame-md.md)] development tools use.</span></span> <span data-ttu-id="ab257-123">脚本中的断点与 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 任务和容器上的断点可以无缝集合。</span><span class="sxs-lookup"><span data-stu-id="ab257-123">Breakpoints in the script work seamlessly with breakpoints on [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] tasks and containers.</span></span> <span data-ttu-id="ab257-124">VSTA 支持 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic 和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# 编程语言。</span><span class="sxs-lookup"><span data-stu-id="ab257-124">VSTA supports both the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# programming languages.</span></span>  
  
 <span data-ttu-id="ab257-125">若要运行脚本，运行包的计算机上必须安装有 VSTA。</span><span class="sxs-lookup"><span data-stu-id="ab257-125">To run a script, you must have VSTA installed on the computer where the package runs.</span></span> <span data-ttu-id="ab257-126">运行包时，任务将加载脚本引擎并运行脚本。</span><span class="sxs-lookup"><span data-stu-id="ab257-126">When the package runs, the task loads the script engine and runs the script.</span></span> <span data-ttu-id="ab257-127">可以通过向项目中的程序集添加引用的方式来访问脚本中的外部 .NET 程序集。</span><span class="sxs-lookup"><span data-stu-id="ab257-127">You can access external .NET assemblies in scripts by adding references to the assemblies in the project.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab257-128">在早期版本中您可以指示是否对脚本进行预编译，而在 [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] 和更高版本中，不同的是，所有脚本都要预编译。</span><span class="sxs-lookup"><span data-stu-id="ab257-128">Unlike earlier versions where you could indicate whether the scripts were precompiled, all scripts are precompiled in [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] and later versions.</span></span> <span data-ttu-id="ab257-129">脚本进行预编译后，运行时将不加载语言引擎，因此包运行得更快。</span><span class="sxs-lookup"><span data-stu-id="ab257-129">When a script is precompiled, the language engine is not loaded at run time and the package runs more quickly.</span></span> <span data-ttu-id="ab257-130">但是，预编译二进制文件占用了大量的磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="ab257-130">However, precompiled binary files consume significant disk space.</span></span>  
  
## <a name="configuring-the-script-task"></a><span data-ttu-id="ab257-131">配置脚本任务</span><span class="sxs-lookup"><span data-stu-id="ab257-131">Configuring the Script Task</span></span>  
 <span data-ttu-id="ab257-132">可以采用下列方法来配置脚本任务：</span><span class="sxs-lookup"><span data-stu-id="ab257-132">You can configure the Script task in the following ways:</span></span>  
  
-   <span data-ttu-id="ab257-133">提供任务运行的自定义脚本。</span><span class="sxs-lookup"><span data-stu-id="ab257-133">Provide the custom script that the task runs.</span></span>  
  
-   <span data-ttu-id="ab257-134">在 VSTA 项目中指定 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 运行时作为脚本任务代码入口点调用的方法。</span><span class="sxs-lookup"><span data-stu-id="ab257-134">Specify the method in the VSTA project that the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] runtime calls as the entry point into the Script task code.</span></span>  
  
-   <span data-ttu-id="ab257-135">指定脚本语言。</span><span class="sxs-lookup"><span data-stu-id="ab257-135">Specify the script language.</span></span>  
  
-   <span data-ttu-id="ab257-136">根据需要提供脚本中使用的只读和读/写变量列表。</span><span class="sxs-lookup"><span data-stu-id="ab257-136">Optionally, provide lists of read-only and read/write variables for use in the script.</span></span>  
  
 <span data-ttu-id="ab257-137">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置这些属性。</span><span class="sxs-lookup"><span data-stu-id="ab257-137">You can set these properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
### <a name="configuring-the-script-task-in-the-designer"></a><span data-ttu-id="ab257-138">在设计器中配置脚本任务</span><span class="sxs-lookup"><span data-stu-id="ab257-138">Configuring the Script Task in the Designer</span></span>  
 <span data-ttu-id="ab257-139">下表描述可以为脚本任务进行记录的 `ScriptTaskLogEntry` 事件。</span><span class="sxs-lookup"><span data-stu-id="ab257-139">The following table describes the `ScriptTaskLogEntry` event that can be logged for Script task.</span></span> <span data-ttu-id="ab257-140">`ScriptTaskLogEntry`已在 "**配置 SSIS 日志**" 对话框的 "**详细信息**" 选项卡上选择要记录的事件。</span><span class="sxs-lookup"><span data-stu-id="ab257-140">The `ScriptTaskLogEntry` event is selected for logging on the **Details** tab of the **Configure SSIS Logs** dialog box.</span></span> <span data-ttu-id="ab257-141">有关详细信息，请参阅 [Integration Services (SSIS) 日志记录](../performance/integration-services-ssis-logging.md)和[日志记录的自定义消息](../custom-messages-for-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="ab257-141">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="ab257-142">日志项</span><span class="sxs-lookup"><span data-stu-id="ab257-142">Log entry</span></span>|<span data-ttu-id="ab257-143">说明</span><span class="sxs-lookup"><span data-stu-id="ab257-143">Description</span></span>|  
|---------------|-----------------|  
|`ScriptTaskLogEntry`|<span data-ttu-id="ab257-144">报告在脚本中实现日志记录的结果。</span><span class="sxs-lookup"><span data-stu-id="ab257-144">Reports the results of implementing logging in the script.</span></span> <span data-ttu-id="ab257-145">该任务在每次调用 `Log` 对象的 `Dts` 方法时都编写一个日志条目。</span><span class="sxs-lookup"><span data-stu-id="ab257-145">The task writes a log entry for each call to the `Log` method of the `Dts` object.</span></span> <span data-ttu-id="ab257-146">然后，在运行代码时编写这些条目。</span><span class="sxs-lookup"><span data-stu-id="ab257-146">The task writes these entries when the code is run.</span></span> <span data-ttu-id="ab257-147">有关详细信息，请参阅 [Logging in the Script Task](../extending-packages-scripting/task/logging-in-the-script-task.md)。</span><span class="sxs-lookup"><span data-stu-id="ab257-147">For more information, see [Logging in the Script Task](../extending-packages-scripting/task/logging-in-the-script-task.md).</span></span>|  
  
 <span data-ttu-id="ab257-148">有关可在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="ab257-148">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see the following topics:</span></span>  
  
-   [<span data-ttu-id="ab257-149">脚本任务编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="ab257-149">Script Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="ab257-150">脚本任务编辑器（“脚本”页）</span><span class="sxs-lookup"><span data-stu-id="ab257-150">Script Task Editor &#40;Script Page&#41;</span></span>](../script-task-editor-script-page.md)  
  
-   [<span data-ttu-id="ab257-151">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="ab257-151">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="ab257-152">有关如何在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="ab257-152">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see the following topic:</span></span>  
  
-   [<span data-ttu-id="ab257-153">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="ab257-153">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
### <a name="configuring-the-script-task-programmatically"></a><span data-ttu-id="ab257-154">以编程方式配置脚本任务</span><span class="sxs-lookup"><span data-stu-id="ab257-154">Configuring the Script Task Programmatically</span></span>  
 <span data-ttu-id="ab257-155">有关以编程方式设置这些属性的详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="ab257-155">For more information about programmatically setting these properties, see the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask>  
  
## <a name="related-content"></a><span data-ttu-id="ab257-156">相关内容</span><span class="sxs-lookup"><span data-stu-id="ab257-156">Related Content</span></span>  
  
-   <span data-ttu-id="ab257-157">shareourideas.com 上的技术文章 [如何在 C# 中发送具有传递通知的电子邮件](https://go.microsoft.com/fwlink/?LinkId=237625)（如何在 C# 中发送具有传递通知的电子邮件）</span><span class="sxs-lookup"><span data-stu-id="ab257-157">Technical article, [How to send email with delivery notification in C#](https://go.microsoft.com/fwlink/?LinkId=237625), on shareourideas.com</span></span>  
  
  
