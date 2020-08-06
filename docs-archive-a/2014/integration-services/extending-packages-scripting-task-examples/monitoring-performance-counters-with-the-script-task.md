---
title: 使用脚本任务监视性能计数器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- performance counters [Integration Services]
- SSIS Script task, performance counters
- custom performance counters [Integration Services]
- Script task [Integration Services], examples
- Script task [Integration Services], performance counters
- counters [Integration Services]
ms.assetid: 86609bf1-cae6-435e-a58d-41bdfc521e94
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 143e11ff966eb11961aa15073a503522c4b9c86b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691803"
---
# <a name="monitoring-performance-counters-with-the-script-task"></a><span data-ttu-id="53cbd-102">使用脚本任务监视性能计数器</span><span class="sxs-lookup"><span data-stu-id="53cbd-102">Monitoring Performance Counters with the Script Task</span></span>
  <span data-ttu-id="53cbd-103">管理员可能需要监视对大量数据执行复杂转换的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的性能。</span><span class="sxs-lookup"><span data-stu-id="53cbd-103">Administrators may need to monitor the performance of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages that perform complex transformations on large amounts of data.</span></span> <span data-ttu-id="53cbd-104">  的 System.Diagnostics 命名空间不但提供使用现有性能计数器的类，还提供用于创建自己性能计数器的类[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="53cbd-104">The **System.Diagnostics** namespace of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] provides classes for using existing performance counters and for creating your own performance counters.</span></span>  
  
 <span data-ttu-id="53cbd-105">性能计数器存储应用程序的性能信息，您可以利用这些信息分析软件在一段时间内的性能。</span><span class="sxs-lookup"><span data-stu-id="53cbd-105">Performance counters store application performance information that you can use to analyze the performance of software over time.</span></span> <span data-ttu-id="53cbd-106">使用“性能监视器”  工具可以在本地或远程监视性能计数器。</span><span class="sxs-lookup"><span data-stu-id="53cbd-106">Performance counters can be monitored locally or remotely by using the **Performance Monitor** tool.</span></span> <span data-ttu-id="53cbd-107">您可以将性能计数器的值存储在变量中，用于以后在包中进行控制流分支跳转。</span><span class="sxs-lookup"><span data-stu-id="53cbd-107">You can store the values of performance counters in variables for later control flow branching in the package.</span></span>  
  
 <span data-ttu-id="53cbd-108">除了使用性能计数器，还可以通过 `Dts` 对象的 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A> 属性引发 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> 事件。</span><span class="sxs-lookup"><span data-stu-id="53cbd-108">As an alternative to using performance counters, you can raise the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A> event through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> property of the `Dts` object.</span></span> <span data-ttu-id="53cbd-109"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A> 事件向 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 运行时返回增量进度和完成的百分比信息。</span><span class="sxs-lookup"><span data-stu-id="53cbd-109">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A> event returns both incremental progress and percentage complete information to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] runtime.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="53cbd-110">如果希望创建可更方便地重用于多个包的任务，请考虑以此脚本任务示例中的代码为基础，创建自定义任务。</span><span class="sxs-lookup"><span data-stu-id="53cbd-110">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="53cbd-111">有关详细信息，请参阅 [开发自定义任务](../extending-packages-custom-objects/task/developing-a-custom-task.md)。</span><span class="sxs-lookup"><span data-stu-id="53cbd-111">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="description"></a><span data-ttu-id="53cbd-112">说明</span><span class="sxs-lookup"><span data-stu-id="53cbd-112">Description</span></span>  
 <span data-ttu-id="53cbd-113">下面的示例创建一个自定义性能计数器并递增该计数器。</span><span class="sxs-lookup"><span data-stu-id="53cbd-113">The following example creates a custom performance counter and increments the counter.</span></span> <span data-ttu-id="53cbd-114">首先，该示例确定性能计数器是否已存在。</span><span class="sxs-lookup"><span data-stu-id="53cbd-114">First, the example determines whether the performance counter already exists.</span></span> <span data-ttu-id="53cbd-115">如果尚未创建性能计数器，则脚本会调用 `Create` 对象的 `PerformanceCounterCategory` 方法来创建它。</span><span class="sxs-lookup"><span data-stu-id="53cbd-115">If the performance counter has not been created, the script calls the `Create` method of the `PerformanceCounterCategory` object to create it.</span></span> <span data-ttu-id="53cbd-116">创建性能计数器后，脚本将递增该计数器。</span><span class="sxs-lookup"><span data-stu-id="53cbd-116">After the performance counter has been created, the script increments the counter.</span></span> <span data-ttu-id="53cbd-117">最后，该示例依照最佳实践，在不再需要该性能计数器时，对其调用 `Close` 方法。</span><span class="sxs-lookup"><span data-stu-id="53cbd-117">Finally, the example follows the best practice of calling the `Close` method on the performance counter when it is no longer needed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="53cbd-118">创建新的性能计数器类别和性能计数器需要管理权限。</span><span class="sxs-lookup"><span data-stu-id="53cbd-118">Creating a new performance counter category and performance counter requires administrative rights.</span></span> <span data-ttu-id="53cbd-119">此外，新类别和计数器在创建后将持久存在于计算机中。</span><span class="sxs-lookup"><span data-stu-id="53cbd-119">Also, the new category and counter persist on the computer after creation.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="53cbd-120">配置此脚本任务示例</span><span class="sxs-lookup"><span data-stu-id="53cbd-120">To configure this Script Task example</span></span>  
  
-   <span data-ttu-id="53cbd-121">使用 `Imports` 代码中的语句导入**系统诊断**命名空间。</span><span class="sxs-lookup"><span data-stu-id="53cbd-121">Use an `Imports` statement in your code to import the **System.Diagnostics** namespace.</span></span>  
  
### <a name="example-code"></a><span data-ttu-id="53cbd-122">示例代码</span><span class="sxs-lookup"><span data-stu-id="53cbd-122">Example Code</span></span>  
  
```vb  
Public Sub Main()  
  
    Dim myCounter As PerformanceCounter  
  
    Try  
        'Create the performance counter if it does not already exist.  
        If Not _  
        PerformanceCounterCategory.Exists("TaskExample") Then  
            PerformanceCounterCategory.Create("TaskExample", _  
                "Task Performance Counter Example", "Iterations", _  
                "Number of times this task has been called.")  
        End If  
  
        'Initialize the performance counter.  
        myCounter = New PerformanceCounter("TaskExample", _  
            "Iterations", String.Empty, False)  
  
        'Increment the performance counter.  
        myCounter.Increment()  
  
         myCounter.Close()  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        Dts.Events.FireError(0, _  
            "Task Performance Counter Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
```  
  
```csharp  
  
public class ScriptMain  
{  
  
public void Main()  
        {  
  
            PerformanceCounter myCounter;  
  
            try  
            {  
                //Create the performance counter if it does not already exist.  
                if (!PerformanceCounterCategory.Exists("TaskExample"))  
                {  
                    PerformanceCounterCategory.Create("TaskExample", "Task Performance Counter Example", "Iterations", "Number of times this task has been called.");  
                }  
  
                //Initialize the performance counter.  
                myCounter = new PerformanceCounter("TaskExample", "Iterations", String.Empty, false);  
  
                //Increment the performance counter.  
                myCounter.Increment();  
  
                myCounter.Close();  
                Dts.TaskResult = (int)ScriptResults.Success;  
            }  
            catch (Exception ex)  
            {  
                Dts.Events.FireError(0, "Task Performance Counter Example", ex.Message + "\r" + ex.StackTrace, String.Empty, 0);  
                Dts.TaskResult = (int)ScriptResults.Failure;  
            }  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
  
```  
  
<span data-ttu-id="53cbd-123">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="53cbd-123">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="53cbd-124">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="53cbd-124">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="53cbd-125">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="53cbd-125">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="53cbd-126">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="53cbd-126">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
