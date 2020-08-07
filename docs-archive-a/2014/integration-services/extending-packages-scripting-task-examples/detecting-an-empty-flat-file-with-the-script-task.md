---
title: 使用脚本任务检测空平面文件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- flat files
- Script task [Integration Services], empty flat files
- SSIS Script task, empty flat files
- Script task [Integration Services], examples
ms.assetid: 1b4defb8-886a-483d-8056-d1b91d37bc90
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 379b11bd18752ad648fc5f24d11d9ed5bfb63e14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587471"
---
# <a name="detecting-an-empty-flat-file-with-the-script-task"></a><span data-ttu-id="1b449-102">使用脚本任务检测空平面文件</span><span class="sxs-lookup"><span data-stu-id="1b449-102">Detecting an Empty Flat File with the Script Task</span></span>
  <span data-ttu-id="1b449-103">平面文件源在尝试处理平面文件之前不确定该平面文件是否包含数据行。</span><span class="sxs-lookup"><span data-stu-id="1b449-103">The Flat File source does not determine whether a flat file contains rows of data before attempting to process it.</span></span> <span data-ttu-id="1b449-104">您可能希望跳过不含任何数据行的文件，从而提高包的效率，尤其是循环访问大量平面文件的包。</span><span class="sxs-lookup"><span data-stu-id="1b449-104">You may want to improve the efficiency of a package, especially of a package that iterates over numerous flat files, by skipping files that do not contain any rows of data.</span></span> <span data-ttu-id="1b449-105">脚本任务可以在包开始处理数据流之前查找空平面文件。</span><span class="sxs-lookup"><span data-stu-id="1b449-105">The Script task can look for an empty flat file before the package begins to process the data flow.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1b449-106">如果希望创建可更方便地重用于多个包的任务，请考虑以此脚本任务示例中的代码为基础，创建自定义任务。</span><span class="sxs-lookup"><span data-stu-id="1b449-106">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="1b449-107">有关详细信息，请参阅 [开发自定义任务](../extending-packages-custom-objects/task/developing-a-custom-task.md)。</span><span class="sxs-lookup"><span data-stu-id="1b449-107">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="description"></a><span data-ttu-id="1b449-108">说明</span><span class="sxs-lookup"><span data-stu-id="1b449-108">Description</span></span>  
 <span data-ttu-id="1b449-109">下面的示例使用 `System.IO` 命名空间中的方法来测试在平面文件连接管理器中指定的平面文件，以确定该文件是否是空的，或者是否只包含预期的非数据行，例如，列标题或空行。</span><span class="sxs-lookup"><span data-stu-id="1b449-109">The following example uses methods from the `System.IO` namespace to test the flat file specified in a Flat File connection manager to determine whether the file is empty, or whether it contains only expected non-data rows such as column headers or an empty line.</span></span> <span data-ttu-id="1b449-110">该脚本先检查文件的大小，如果大小为零字节，则该文件是空的。</span><span class="sxs-lookup"><span data-stu-id="1b449-110">The script checks the size of the file first; if the size is zero bytes, the file is empty.</span></span> <span data-ttu-id="1b449-111">如果文件大小大于零，该脚本会从文件中读取行，直到没有行可读为止，或者直到行数超过预期的非数据行数为止。</span><span class="sxs-lookup"><span data-stu-id="1b449-111">If the file size is greater than zero, the script reads lines from the file until there are no more lines, or until the number of lines exceeds the expected number of non-data rows.</span></span> <span data-ttu-id="1b449-112">如果该文件中的行数小于或等于预期的非数据行数，则认为该文件是空的。</span><span class="sxs-lookup"><span data-stu-id="1b449-112">If the number of lines in the file is less than or equal to the expected number of non-data rows, then the file is considered empty.</span></span> <span data-ttu-id="1b449-113">结果将以布尔值的形式在用户变量中返回，该变量的值可用于在包控制流中进行分支跳转。</span><span class="sxs-lookup"><span data-stu-id="1b449-113">The result is returned as a Boolean value in a user variable, the value of which can be used for branching in the package's control flow.</span></span> <span data-ttu-id="1b449-114">`FireInformation`方法还会**Output**在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (VSTA) 的应用程序的工具的 "输出" 窗口中显示结果。</span><span class="sxs-lookup"><span data-stu-id="1b449-114">The `FireInformation` method also displays the result in the **Output** window of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="1b449-115">配置此脚本任务示例</span><span class="sxs-lookup"><span data-stu-id="1b449-115">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="1b449-116">创建并配置一个名为的平面文件连接管理器 `EmptyFlatFileTest` 。</span><span class="sxs-lookup"><span data-stu-id="1b449-116">Create and configure a flat file connection manager named `EmptyFlatFileTest`.</span></span>  
  
2.  <span data-ttu-id="1b449-117">创建一个名为 `FFNonDataRows` 的整数变量，并将其值设置为预期在平面文件中出现的非数据行数。</span><span class="sxs-lookup"><span data-stu-id="1b449-117">Create an integer variable named `FFNonDataRows` and set its value to the number of non-data rows expected in the flat file.</span></span>  
  
3.  <span data-ttu-id="1b449-118">创建一个名为 `FFIsEmpty` 的布尔变量。</span><span class="sxs-lookup"><span data-stu-id="1b449-118">Create a Boolean variable named `FFIsEmpty`.</span></span>  
  
4.  <span data-ttu-id="1b449-119">将 `FFNonDataRows` 变量添加到脚本任务的 **ReadOnlyVariables** 属性中。</span><span class="sxs-lookup"><span data-stu-id="1b449-119">Add the `FFNonDataRows` variable to the Script task's **ReadOnlyVariables** property.</span></span>  
  
5.  <span data-ttu-id="1b449-120">将 `FFIsEmpty` 变量添加到脚本任务的 **ReadWriteVariables** 属性中。</span><span class="sxs-lookup"><span data-stu-id="1b449-120">Add the `FFIsEmpty` variable to the Script task's **ReadWriteVariables** property.</span></span>  
  
6.  <span data-ttu-id="1b449-121">在您的代码中，导入 `System.IO` 命名空间。</span><span class="sxs-lookup"><span data-stu-id="1b449-121">In your code, import the `System.IO` namespace.</span></span>  
  
 <span data-ttu-id="1b449-122">如果使用的是 Foreach 文件枚举器来循环访问文件，而不是使用单个平面文件连接管理器，则需要修改下面的代码，以便从存储枚举值的变量中而不是从连接管理器获取文件名和路径。</span><span class="sxs-lookup"><span data-stu-id="1b449-122">If you are iterating over files with a Foreach File enumerator, instead of using a single Flat File connection manager, you will need to modify the sample code below to obtain the file name and path from the variable in which the enumerated value is stored instead of from the connection manager.</span></span>  
  
### <a name="code"></a><span data-ttu-id="1b449-123">代码</span><span class="sxs-lookup"><span data-stu-id="1b449-123">Code</span></span>  
  
```vb  
Public Sub Main()  
  
  Dim nonDataRows As Integer = _  
      DirectCast(Dts.Variables("FFNonDataRows").Value, Integer)  
  Dim ffConnection As String = _  
      DirectCast(Dts.Connections("EmptyFlatFileTest").AcquireConnection(Nothing), _  
      String)  
  Dim flatFileInfo As New FileInfo(ffConnection)  
  ' If file size is 0 bytes, flat file does not contain data.  
  Dim fileSize As Long = flatFileInfo.Length  
  If fileSize > 0 Then  
    Dim lineCount As Integer = 0  
    Dim line As String  
    Dim fsFlatFile As New StreamReader(ffConnection)  
    Do Until fsFlatFile.EndOfStream  
      line = fsFlatFile.ReadLine  
      lineCount += 1  
      ' If line count > expected number of non-data rows,  
      '  flat file contains data (default value).  
      If lineCount > nonDataRows Then  
        Exit Do  
      End If  
      ' If line count <= expected number of non-data rows,  
      '  flat file does not contain data.  
      If lineCount <= nonDataRows Then  
        Dts.Variables("FFIsEmpty").Value = True  
      End If  
    Loop  
  Else  
    Dts.Variables("FFIsEmpty").Value = True  
  End If  
  
  Dim fireAgain As Boolean = False  
  Dts.Events.FireInformation(0, "Script Task", _  
      String.Format("{0}: {1}", ffConnection, _  
      Dts.Variables("FFIsEmpty").Value.ToString), _  
      String.Empty, 0, fireAgain)  
  
  Dts.TaskResult = ScriptResults.Success  
  
End Sub  
```  
  
```csharp  
public void Main()  
        {  
  
            int nonDataRows = (int)(Dts.Variables["FFNonDataRows"].Value);  
            string ffConnection = (string)(Dts.Connections["EmptyFlatFileTest"].AcquireConnection(null) as String);  
            FileInfo flatFileInfo = new FileInfo(ffConnection);  
            // If file size is 0 bytes, flat file does not contain data.  
            long fileSize = flatFileInfo.Length;  
            if (fileSize > 0)  
            {  
  
                int lineCount = 0;  
                string line;  
                StreamReader fsFlatFile = new StreamReader(ffConnection);  
                while (!(fsFlatFile.EndOfStream))  
                {  
                    Console.WriteLine (fsFlatFile.ReadLine());  
                    lineCount += 1;  
                    // If line count > expected number of non-data rows,  
                    //  flat file contains data (default value).  
                    if (lineCount > nonDataRows)  
                    {  
                        break;  
                    }  
                    // If line count <= expected number of non-data rows,  
                    //  flat file does not contain data.  
                    if (lineCount <= nonDataRows)  
                    {  
                        Dts.Variables["FFIsEmpty"].Value = true;  
                    }  
                }  
            }  
            else  
            {  
                Dts.Variables["FFIsEmpty"].Value = true;  
            }  
  
            bool fireAgain = false;  
            Dts.Events.FireInformation(0, "Script Task", String.Format("{0}: {1}", ffConnection, Dts.Variables["FFIsEmpty"].Value), String.Empty, 0, ref fireAgain);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
```  
  
<span data-ttu-id="1b449-124">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="1b449-124">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="1b449-125">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="1b449-125">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="1b449-126">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="1b449-126">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="1b449-127">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="1b449-127">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b449-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1b449-128">See Also</span></span>  
 [<span data-ttu-id="1b449-129">脚本任务示例</span><span class="sxs-lookup"><span data-stu-id="1b449-129">Script Task Examples</span></span>](../extending-packages-scripting-task-examples/script-task-examples.md)  
  
  
