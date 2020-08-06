---
title: 在脚本任务中使用变量 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Foreach Loop containers
- Script task [Integration Services], variables
- scripts [Integration Services], variables
- Variables property
- Variable object
- SSIS Script task, variables
- variables [Integration Services], Script task
ms.assetid: 593b5961-4bfa-4ce1-9531-a251c34e89d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2cd8fee5741c3d0e28e52c8712c3896428a05e8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694530"
---
# <a name="using-variables-in-the-script-task"></a><span data-ttu-id="bc6e1-102">在脚本任务中使用变量</span><span class="sxs-lookup"><span data-stu-id="bc6e1-102">Using Variables in the Script Task</span></span>
  <span data-ttu-id="bc6e1-103">通过变量，脚本任务可以与包中的其他对象交换数据。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-103">Variables make it possible for the Script task to exchange data with other objects in the package.</span></span> <span data-ttu-id="bc6e1-104">有关详细信息，请参阅 [Integration Services (SSIS) 变量](../../integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-104">For more information, see [Integration Services &#40;SSIS&#41; Variables](../../integration-services-ssis-variables.md).</span></span>  
  
 <span data-ttu-id="bc6e1-105">脚本任务使用 `Dts` 对象的 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 属性，从包中的 <xref:Microsoft.SqlServer.Dts.Runtime.Variable> 对象读取数据或向其中写入数据。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-105">The Script task uses the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property of the `Dts` object to read from and write to <xref:Microsoft.SqlServer.Dts.Runtime.Variable> objects in the package.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bc6e1-106"><xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> 类的 <xref:Microsoft.SqlServer.Dts.Runtime.Variable> 属性的类型为 `Object`。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-106">The <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> property of the <xref:Microsoft.SqlServer.Dts.Runtime.Variable> class is of type `Object`.</span></span> <span data-ttu-id="bc6e1-107">由于脚本任务启用了 `Option Strict`，因此在使用 <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> 属性之前，必须先将其转换为适当的类型。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-107">Because the Script task has `Option Strict` enabled, you must cast the <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> property to the appropriate type before you can use it.</span></span>  
  
 <span data-ttu-id="bc6e1-108">可以在“脚本任务编辑器”中向 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadOnlyVariables%2A> 和 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadWriteVariables%2A> 列表添加现有变量，以使它们可用于自定义脚本  。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-108">You add existing variables to the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadOnlyVariables%2A> and <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadWriteVariables%2A> lists in the **Script Task Editor** to make them available to the custom script.</span></span> <span data-ttu-id="bc6e1-109">请注意，变量名称区分大小写。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-109">Keep in mind that variable names are case-sensitive.</span></span> <span data-ttu-id="bc6e1-110">在脚本内，您可以通过 `Dts` 对象的 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 属性访问这两种类型的变量。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-110">Within the script, you access variables of both types through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property of the `Dts` object.</span></span> <span data-ttu-id="bc6e1-111">使用 `Value` 属性可以从单个变量读取数据或向其中写入数据。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-111">Use the `Value` property to read from and write to individual variables.</span></span> <span data-ttu-id="bc6e1-112">脚本任务在脚本读取和修改变量的值时，透明地管理锁定。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-112">The Script task transparently manages locking as the script reads and modifies the values of variables.</span></span>  
  
 <span data-ttu-id="bc6e1-113">在代码中使用某个变量之前，可以使用 <xref:Microsoft.SqlServer.Dts.Runtime.Variables.Contains%2A> 属性返回的 <xref:Microsoft.SqlServer.Dts.Runtime.Variables> 集合的 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 方法来检查该变量是否存在。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-113">You can use the <xref:Microsoft.SqlServer.Dts.Runtime.Variables.Contains%2A> method of the <xref:Microsoft.SqlServer.Dts.Runtime.Variables> collection returned by the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property to check for the existence of a variable before using it in your code.</span></span>  
  
 <span data-ttu-id="bc6e1-114">还可以使用 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> 属性 (Dts.VariableDispenser) 在脚本任务中处理变量。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-114">You can also use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> property (Dts.VariableDispenser) to work with variables in the Script task.</span></span> <span data-ttu-id="bc6e1-115">使用 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> 时，您必须在您自己的代码中处理锁定语义和变量值的数据类型转换。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-115">When using the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>, you must handle both the locking semantics and the casting of data types for variable values in your own code.</span></span> <span data-ttu-id="bc6e1-116">如果要使用在设计时不可用，而是以编程方式在运行时创建的变量，可能需要使用 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> 属性，而不是 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-116">You may need to use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> property instead of the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property if you want to work with a variable that is not available at design time but is created programmatically at run time.</span></span>  
  
## <a name="using-the-script-task-within-a-foreach-loop-container"></a><span data-ttu-id="bc6e1-117">在 Foreach 循环容器中使用脚本任务</span><span class="sxs-lookup"><span data-stu-id="bc6e1-117">Using the Script Task within a Foreach Loop Container</span></span>  
 <span data-ttu-id="bc6e1-118">当脚本任务在 Foreach 循环容器内重复运行时，脚本通常需要使用枚举器中当前项的内容。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-118">When a Script task runs repeatedly within a Foreach Loop container, the script usually needs to work with the contents of the current item in the enumerator.</span></span> <span data-ttu-id="bc6e1-119">例如，使用 Foreach 文件枚举器时，脚本需要知道当前文件名；使用 Foreach ADO 枚举器时，脚本需要知道当前数据行中各列的内容。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-119">For example, when using a Foreach File enumerator, the script needs to know the current file name; when using a Foreach ADO enumerator, the script needs to know the contents of the columns in the current row of data.</span></span>  
  
 <span data-ttu-id="bc6e1-120">Foreach 循环容器与脚本任务之间的这种通信可以通过变量实现。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-120">Variables make this communication between the Foreach Loop container and the Script task possible.</span></span> <span data-ttu-id="bc6e1-121">在“Foreach 循环编辑器”的“变量映射”页中，可以向单个枚举项返回的每个数据项分配变量   。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-121">On the **Variable Mappings** page of the **Foreach Loop Editor**, assign variables to each item of data that is returned by a single enumerated item.</span></span> <span data-ttu-id="bc6e1-122">例如，Foreach 文件枚举器仅返回索引 0 处的一个文件名，因此只需要一个变量映射，而在每行中返回多个数据列的枚举器需要将不同的变量映射到要在脚本任务中使用的每一列。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-122">For example, a Foreach File enumerator returns only a file name at Index 0 and therefore requires only one variable mapping, whereas an enumerator that returns several columns of data in each row requires you to map a different variable to each column that you want to use in the Script task.</span></span>  
  
 <span data-ttu-id="bc6e1-123">在将枚举项映射到变量后，必须将映射的变量添加到 `ReadOnlyVariables` **脚本任务编辑器**的 "**脚本**" 页上的属性，以使其可供脚本使用。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-123">After you have mapped enumerated items to variables, then you must add the mapped variables to the `ReadOnlyVariables` property on the **Script** page of the **Script Task Editor** to make them available to your script.</span></span> <span data-ttu-id="bc6e1-124">有关在 Foreach 循环容器中处理文件夹中的图像文件的脚本任务示例，请参阅[使用脚本任务处理图像](../../extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md)。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-124">For an example of a Script task within a Foreach Loop container that processes the image files in a folder, see [Working with Images with the Script Task](../../extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md).</span></span>  
  
## <a name="variables-example"></a><span data-ttu-id="bc6e1-125">变量示例</span><span class="sxs-lookup"><span data-stu-id="bc6e1-125">Variables Example</span></span>  
 <span data-ttu-id="bc6e1-126">下面的示例演示如何在脚本任务中访问并使用变量，以确定包工作流的路径。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-126">The following example demonstrates how to access and use variables in a Script task to determine the path of package workflow.</span></span> <span data-ttu-id="bc6e1-127">该示例假设您已经创建了名为和的整数变量 `CustomerCount` `MaxRecordCount` ，并将其添加到了 `ReadOnlyVariables` "**脚本任务编辑器**" 中的集合。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-127">The sample assumes that you have created integer variables named `CustomerCount` and `MaxRecordCount` and added them to the `ReadOnlyVariables` collection in the **Script Task Editor**.</span></span> <span data-ttu-id="bc6e1-128">`CustomerCount` 变量包含要导入的客户记录的数目。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-128">The `CustomerCount` variable contains the number of customer records to be imported.</span></span> <span data-ttu-id="bc6e1-129">如果其值大于 `MaxRecordCount` 的值，则脚本任务将报告失败。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-129">If its value is greater than the value of `MaxRecordCount`, the Script task reports failure.</span></span> <span data-ttu-id="bc6e1-130">如果因超过 `MaxRecordCount` 阈值而导致失败，则工作流的错误路径可实现任何所需的清除操作。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-130">When a failure occurs because the `MaxRecordCount` threshold has been exceeded, the error path of the workflow can implement any required clean-up.</span></span>  
  
 <span data-ttu-id="bc6e1-131">若要成功编译该示例，需要添加对 Microsoft.SqlServer.ScriptTask 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-131">To successfully compile the sample, you need to add a reference to the Microsoft.SqlServer.ScriptTask assembly.</span></span>  
  
```vb  
Public Sub Main()  
  
    Dim customerCount As Integer  
    Dim maxRecordCount As Integer  
  
    If Dts.Variables.Contains("CustomerCount") = True AndAlso _  
        Dts.Variables.Contains("MaxRecordCount") = True Then  
  
        customerCount = _  
            CType(Dts.Variables("CustomerCount").Value, Integer)  
        maxRecordCount = _  
            CType(Dts.Variables("MaxRecordCount").Value, Integer)  
  
    End If  
  
    If customerCount > maxRecordCount Then  
            Dts.TaskResult = ScriptResults.Failure  
    Else  
            Dts.TaskResult = ScriptResults.Success  
    End If  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime;  
  
public class ScriptMain  
{  
  
    public void Main()  
    {  
        int customerCount;  
        int maxRecordCount;  
  
        if (Dts.Variables.Contains("CustomerCount")==true&&Dts.Variables.Contains("MaxRecordCount")==true)  
  
        {  
            customerCount = (int) Dts.Variables["CustomerCount"].Value;  
            maxRecordCount = (int) Dts.Variables["MaxRecordCount"].Value;  
  
        }  
  
        if (customerCount>maxRecordCount)  
        {  
            Dts.TaskResult = (int)ScriptResults.Failure;  
        }  
        else  
        {  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
  
    }  
  
}  
  
```  
  
<span data-ttu-id="bc6e1-132">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="bc6e1-132">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="bc6e1-133">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="bc6e1-133">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="bc6e1-134">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="bc6e1-134">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="bc6e1-135">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="bc6e1-135">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc6e1-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bc6e1-136">See Also</span></span>  
 <span data-ttu-id="bc6e1-137">[Integration Services (SSIS) 变量](../../integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="bc6e1-137">[Integration Services &#40;SSIS&#41; Variables](../../integration-services-ssis-variables.md) </span></span>  
 [<span data-ttu-id="bc6e1-138">使用包中的变量</span><span class="sxs-lookup"><span data-stu-id="bc6e1-138">Use Variables in Packages</span></span>](../../use-variables-in-packages.md)  
  
  
