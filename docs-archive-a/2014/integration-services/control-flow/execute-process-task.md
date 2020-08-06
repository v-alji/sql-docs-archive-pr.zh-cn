---
title: 执行进程任务 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executeprocesstask.f1
helpviewer_keywords:
- Execute Process task [Integration Services]
ms.assetid: aca5a0b5-34a9-45bc-a234-8e63ea51a1ee
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c0db683d7c900e2554b3b856cbf68f7cfb1ca087
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585919"
---
# <a name="execute-process-task"></a><span data-ttu-id="a7147-102">执行进程任务</span><span class="sxs-lookup"><span data-stu-id="a7147-102">Execute Process Task</span></span>
  <span data-ttu-id="a7147-103">执行进程任务在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包工作流中运行应用程序或批处理文件。</span><span class="sxs-lookup"><span data-stu-id="a7147-103">The Execute Process task runs an application or batch file as part of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package workflow.</span></span> <span data-ttu-id="a7147-104">虽然可以使用执行进程任务打开任意标准应用程序（例如 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 或 [!INCLUDE[ofprword](../../includes/ofprword-md.md)]），但通常还是使用它来运行针对数据源执行的业务应用程序或批处理文件。</span><span class="sxs-lookup"><span data-stu-id="a7147-104">Although you can use the Execute Process task to open any standard application, such as [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] or [!INCLUDE[ofprword](../../includes/ofprword-md.md)], you typically use it to run business applications or batch files that work against a data source.</span></span> <span data-ttu-id="a7147-105">例如，可以使用执行进程任务来展开一个压缩的文本文件。</span><span class="sxs-lookup"><span data-stu-id="a7147-105">For example, you can use the Execute Process task to expand a compressed text file.</span></span> <span data-ttu-id="a7147-106">然后，包可将该文本文件用作包中数据流的数据源。</span><span class="sxs-lookup"><span data-stu-id="a7147-106">Then the package can use the text file as a data source for the data flow in the package.</span></span> <span data-ttu-id="a7147-107">再举一个例子，您可以使用执行进程任务运行生成日销售额报表的自定义 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 应用程序。</span><span class="sxs-lookup"><span data-stu-id="a7147-107">As another example, you can use the Execute Process task to run a custom [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] application that generates a daily sales report.</span></span> <span data-ttu-id="a7147-108">然后，可以将该报表附加到发送邮件任务，并将其转发给通讯组列表。</span><span class="sxs-lookup"><span data-stu-id="a7147-108">Then you can attach the report to a Send Mail task and forward the report to a distribution list.</span></span>  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="a7147-109">还包含一些执行工作流操作的其他任务（如执行包）。</span><span class="sxs-lookup"><span data-stu-id="a7147-109">includes other tasks that perform workflow operations such as executing packages.</span></span> <span data-ttu-id="a7147-110">有关详细信息，请参阅 [Execute Package Task](execute-package-task.md)</span><span class="sxs-lookup"><span data-stu-id="a7147-110">For more information, see [Execute Package Task](execute-package-task.md)</span></span>  
  
## <a name="custom-log-entries-available-on-the-execute-process-task"></a><span data-ttu-id="a7147-111">执行进程任务可用的自定义日志项</span><span class="sxs-lookup"><span data-stu-id="a7147-111">Custom Log Entries Available on the Execute Process Task</span></span>  
 <span data-ttu-id="a7147-112">下表列出了执行进程任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="a7147-112">The following table lists the custom log entries for the Execute Process task.</span></span> <span data-ttu-id="a7147-113">有关详细信息，请参阅 [Integration Services (SSIS) 日志记录](../performance/integration-services-ssis-logging.md)和[日志记录的自定义消息](../custom-messages-for-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="a7147-113">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="a7147-114">日志项</span><span class="sxs-lookup"><span data-stu-id="a7147-114">Log entry</span></span>|<span data-ttu-id="a7147-115">说明</span><span class="sxs-lookup"><span data-stu-id="a7147-115">Description</span></span>|  
|---------------|-----------------|  
|`ExecuteProcessExecutingProcess`|<span data-ttu-id="a7147-116">提供所配置任务要运行的进程的信息。</span><span class="sxs-lookup"><span data-stu-id="a7147-116">Provides information about the process that the task is configured to run.</span></span><br /><br /> <span data-ttu-id="a7147-117">写入两个日志条目。</span><span class="sxs-lookup"><span data-stu-id="a7147-117">Two log entries are written.</span></span> <span data-ttu-id="a7147-118">一个日志条目包含有关任务所运行可执行文件的名称和位置的信息，另一个条目则记录从可执行文件退出的信息。</span><span class="sxs-lookup"><span data-stu-id="a7147-118">One contains information about the name and location of the executable that the task runs, and the other entry records the exit from the executable.</span></span>|  
|`ExecuteProcessVariableRouting`|<span data-ttu-id="a7147-119">提供有关哪些变量被路由到可执行文件的输入和输出的信息。</span><span class="sxs-lookup"><span data-stu-id="a7147-119">Provides information about which variables are routed to the input and outputs of the executable.</span></span> <span data-ttu-id="a7147-120">将为 stdin（输入）、stdout（输出）和 stderr（错误输出）写入日志条目。</span><span class="sxs-lookup"><span data-stu-id="a7147-120">Log entries are written for stdin (the input), stdout (the output), and stderr (the error output).</span></span>|  
  
## <a name="configuration-of-the-execute-process-task"></a><span data-ttu-id="a7147-121">执行进程任务的配置</span><span class="sxs-lookup"><span data-stu-id="a7147-121">Configuration of the Execute Process Task</span></span>  
 <span data-ttu-id="a7147-122">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="a7147-122">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="a7147-123">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="a7147-123">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="a7147-124">执行进程任务编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="a7147-124">Execute Process Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="a7147-125">执行进程任务编辑器（“进程”页）</span><span class="sxs-lookup"><span data-stu-id="a7147-125">Execute Process Task Editor &#40;Process Page&#41;</span></span>](../execute-process-task-editor-process-page.md)  
  
 <span data-ttu-id="a7147-126">有关如何在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击下列主题：</span><span class="sxs-lookup"><span data-stu-id="a7147-126">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="a7147-127">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="a7147-127">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
### <a name="property-settings"></a><span data-ttu-id="a7147-128">属性设置</span><span class="sxs-lookup"><span data-stu-id="a7147-128">Property Settings</span></span>  
 <span data-ttu-id="a7147-129">当执行进程任务运行自定义应用程序时，该任务将通过以下一种或两种方法为该应用程序提供输入：</span><span class="sxs-lookup"><span data-stu-id="a7147-129">When the Execute Process task runs a custom application, the task provides input to the application through one or both of the following methods:</span></span>  
  
-   <span data-ttu-id="a7147-130">在 **StandardInputVariable** 属性设置中指定的变量。</span><span class="sxs-lookup"><span data-stu-id="a7147-130">A variable that you specify in the **StandardInputVariable** property setting.</span></span> <span data-ttu-id="a7147-131">有关变量的详细信息，请参阅 [Integration Services (SSIS) 变量](../integration-services-ssis-variables.md)和[在包中使用变量](../use-variables-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="a7147-131">For more information about variables, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
-   <span data-ttu-id="a7147-132">在 **Arguments** 属性设置中指定的参数。</span><span class="sxs-lookup"><span data-stu-id="a7147-132">An argument that you specify in the **Arguments** property setting.</span></span> <span data-ttu-id="a7147-133">（例如，如果该任务打开一个 Word 格式的文档，该参数就可指定该 .doc 文件的名称。）</span><span class="sxs-lookup"><span data-stu-id="a7147-133">(For example, if the task opens a document in Word, the argument can name the .doc file.)</span></span>  
  
 <span data-ttu-id="a7147-134">若要在一个执行进程任务中向自定义应用程序传递多个参数，请使用空格将这些参数隔开。</span><span class="sxs-lookup"><span data-stu-id="a7147-134">To pass multiple arguments to a custom application in one Execute Process task, use spaces to delimit the arguments.</span></span> <span data-ttu-id="a7147-135">参数中不能包含空格，否则该任务将不运行。</span><span class="sxs-lookup"><span data-stu-id="a7147-135">An argument cannot include a space; otherwise, the task will not run.</span></span> <span data-ttu-id="a7147-136">可以使用表达式将变量值作为参数传递。</span><span class="sxs-lookup"><span data-stu-id="a7147-136">You can use an expression to pass a variable value as the argument.</span></span> <span data-ttu-id="a7147-137">在下面的示例中，表达式将两个变量值作为参数传递并使用空格将参数隔开：</span><span class="sxs-lookup"><span data-stu-id="a7147-137">In the following example, the expression passes two variable values as arguments, and uses a space to delimit the arguments:</span></span>  
  
 `@variable1 + " " + @variable2`  
  
 <span data-ttu-id="a7147-138">可以使用表达式设置执行进程任务的各种属性。</span><span class="sxs-lookup"><span data-stu-id="a7147-138">You can use an expression to set various Execute Process task properties.</span></span>  
  
 <span data-ttu-id="a7147-139">使用**StandardInputVariable**属性配置执行进程任务以提供输入时，请 `Console.ReadLine` 从应用程序中调用方法以读取输入。</span><span class="sxs-lookup"><span data-stu-id="a7147-139">When you use the **StandardInputVariable** property to configure the Execute Process task to provide input, call the `Console.ReadLine` method from the application to read the input.</span></span> <span data-ttu-id="a7147-140">有关详细信息，请参阅 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 类库中的 [Console.ReadLine 方法](https://go.microsoft.com/fwlink/?LinkId=129201)主题。</span><span class="sxs-lookup"><span data-stu-id="a7147-140">For more information, see [Console.ReadLine Method](https://go.microsoft.com/fwlink/?LinkId=129201)the topic, , in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Class Library.</span></span>  
  
 <span data-ttu-id="a7147-141">当使用 **Arguments** 属性配置执行进程任务以提供输入时，请执行下列步骤之一以获得参数：</span><span class="sxs-lookup"><span data-stu-id="a7147-141">When you use the **Arguments** property to configure the Execute Process task to provide input, do one of the following steps to obtain the arguments:</span></span>  
  
-   <span data-ttu-id="a7147-142">如果使用 Microsoft Visual Basic 编写应用程序，请设置 `My.Application.CommandLineArgs` 属性。</span><span class="sxs-lookup"><span data-stu-id="a7147-142">If you use Microsoft Visual Basic to write the application, set the `My.Application.CommandLineArgs` property.</span></span> <span data-ttu-id="a7147-143">下面的示例设置 `My.Application.CommandLineArgs` 属性以检索两个参数：</span><span class="sxs-lookup"><span data-stu-id="a7147-143">The following example sets the `My.Application.CommandLineArgs` property is to retrieve two arguments:</span></span>  
  
    ```  
    Dim variable1 As String = My.Application.CommandLineArgs.Item(0)  
    Dim variable2 As String = My.Application.CommandLineArgs.Item(1)   
    ```  
  
     <span data-ttu-id="a7147-144">有关详细信息，请参阅 [参考中的](https://go.microsoft.com/fwlink/?LinkId=129200)My.Application.CommandLineArgs 属性 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 这一主题。</span><span class="sxs-lookup"><span data-stu-id="a7147-144">For more information, see the topic, [My.Application.CommandLineArgs Property](https://go.microsoft.com/fwlink/?LinkId=129200), in the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] reference.</span></span>  
  
-   <span data-ttu-id="a7147-145">如果使用 Microsoft Visual C# 编写该应用程序，请使用 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="a7147-145">If you use Microsoft Visual C# to write the applicate, use the `Main` method.</span></span>  
  
     <span data-ttu-id="a7147-146">有关详细信息，请参阅 C# 编程指南中的 [命令行参数（C# 编程指南）](https://go.microsoft.com/fwlink/?LinkId=129406)这一主题。</span><span class="sxs-lookup"><span data-stu-id="a7147-146">For more information, see the topic, [Command-Line Arguments (C# Programming Guide)](https://go.microsoft.com/fwlink/?LinkId=129406), in the C# Programming Guide.</span></span>  
  
 <span data-ttu-id="a7147-147">执行进程任务还包括 **StandardOutputVariable** 和 **StandardErrorVariable** 属性，用来分别指定使用该应用程序的标准输出和错误输出的变量。</span><span class="sxs-lookup"><span data-stu-id="a7147-147">The Execute Process task also includes the **StandardOutputVariable** and **StandardErrorVariable** properties for specifying the variables that consume the standard output and error output of the application, respectively.</span></span>  
  
 <span data-ttu-id="a7147-148">另外，您还可以配置执行进程任务来指定工作目录、超时期限或表示可执行文件成功运行的值。</span><span class="sxs-lookup"><span data-stu-id="a7147-148">Additionally, you can configure the Execute Process task to specify a working directory, a time-out period, or a value to indicate that the executable ran successfully.</span></span> <span data-ttu-id="a7147-149">您还可以对该任务进行配置，使其在可执行文件的返回代码与指示成功的值不匹配时或者在指定位置找不到可执行文件时失败。</span><span class="sxs-lookup"><span data-stu-id="a7147-149">The task can also be configured to fail if the return code of the executable does not match the value that indicates success, or if the executable is not found at the specified location.</span></span>  
  
## <a name="programmatic-configuration-of-the-execute-process-task"></a><span data-ttu-id="a7147-150">执行进程任务的编程配置</span><span class="sxs-lookup"><span data-stu-id="a7147-150">Programmatic Configuration of the Execute Process Task</span></span>  
 <span data-ttu-id="a7147-151">有关以编程方式设置这些属性的详细信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="a7147-151">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.ExecuteProcess.ExecuteProcess>  
  
## <a name="see-also"></a><span data-ttu-id="a7147-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a7147-152">See Also</span></span>  
 <span data-ttu-id="a7147-153">[Integration Services 任务](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="a7147-153">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="a7147-154">控制流</span><span class="sxs-lookup"><span data-stu-id="a7147-154">Control Flow</span></span>](control-flow.md)  
  
  
