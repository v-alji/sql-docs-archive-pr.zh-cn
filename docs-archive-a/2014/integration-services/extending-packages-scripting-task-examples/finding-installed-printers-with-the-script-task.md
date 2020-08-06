---
title: 使用脚本任务查找已安装的打印机 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- System.Drawing.Printing namespace
- printers [Integration Services]
- SSIS Script task, printers
- locating printers
- Printing namespace
- Script task [Integration Services], examples
- finding printers [SQL Server]
- Script task [Integration Services], printers
ms.assetid: 50a55014-e2c3-4ecd-84e1-3e877c55a260
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cc4bc06879a55d4d07afca1011cc479dd7e7903a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691815"
---
# <a name="finding-installed-printers-with-the-script-task"></a><span data-ttu-id="b26dd-102">使用脚本任务查找已安装的打印机</span><span class="sxs-lookup"><span data-stu-id="b26dd-102">Finding Installed Printers with the Script Task</span></span>
  <span data-ttu-id="b26dd-103">由 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包转换的数据的最终目的通常是打印成一份报表。</span><span class="sxs-lookup"><span data-stu-id="b26dd-103">The data that is transformed by [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages often has a printed report as its final destination.</span></span> <span data-ttu-id="b26dd-104">`System.Drawing.Printing`中的命名空间 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 提供了用于使用打印机的类。</span><span class="sxs-lookup"><span data-stu-id="b26dd-104">The `System.Drawing.Printing` namespace in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] provides classes for working with printers.</span></span>

> [!NOTE]
>  <span data-ttu-id="b26dd-105">如果希望创建可更方便地重用于多个包的任务，请考虑以此脚本任务示例中的代码为基础，创建自定义任务。</span><span class="sxs-lookup"><span data-stu-id="b26dd-105">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="b26dd-106">有关详细信息，请参阅 [开发自定义任务](../extending-packages-custom-objects/task/developing-a-custom-task.md)。</span><span class="sxs-lookup"><span data-stu-id="b26dd-106">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>

## <a name="description"></a><span data-ttu-id="b26dd-107">说明</span><span class="sxs-lookup"><span data-stu-id="b26dd-107">Description</span></span>
 <span data-ttu-id="b26dd-108">以下示例查找服务器上安装的支持合法纸张大小（以在美国使用为例）的打印机。</span><span class="sxs-lookup"><span data-stu-id="b26dd-108">The following example locates printers installed on the server that support legal size paper (as used in the United States).</span></span> <span data-ttu-id="b26dd-109">用于检查所支持的纸张大小的代码封装在一个私有函数中。</span><span class="sxs-lookup"><span data-stu-id="b26dd-109">The code to check supported paper sizes is encapsulated in a private function.</span></span> <span data-ttu-id="b26dd-110">为了能够跟踪脚本检查每个打印机设置的进度，脚本使用 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> 方法对具有合法纸张大小的打印机引发信息性消息，对不具有合法纸张大小的打印机引发警告。</span><span class="sxs-lookup"><span data-stu-id="b26dd-110">To enable you to track the progress of the script as it checks the settings for each printer, the script uses the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> method to raise an informational message for printers with legal size paper, and to raise a warning for printers without legal size paper.</span></span> <span data-ttu-id="b26dd-111">在设计器中运行包时，这些消息显示在   Tools for Applications (VSTA) IDE 的“输出”窗口中[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b26dd-111">These messages appear in the **Output** window of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE when you run the package in the designer.</span></span>

#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="b26dd-112">配置此脚本任务示例</span><span class="sxs-lookup"><span data-stu-id="b26dd-112">To configure this Script Task example</span></span>

1.  <span data-ttu-id="b26dd-113">创建名为 `PrinterList` 的 `Object` 类型变量。</span><span class="sxs-lookup"><span data-stu-id="b26dd-113">Create the variable named `PrinterList` with type `Object`.</span></span>

2.  <span data-ttu-id="b26dd-114">在“脚本任务编辑器”的“脚本”页，将此变量添加到 ReadWriteVariables 属性。</span><span class="sxs-lookup"><span data-stu-id="b26dd-114">On the **Script** page of the **Script Task Editor**, add this variable to the ReadWriteVariables property.</span></span>

3.  <span data-ttu-id="b26dd-115">在脚本项目中，添加对 System.Drawing  命名空间的引用。</span><span class="sxs-lookup"><span data-stu-id="b26dd-115">In the script project, add a reference to the **System.Drawing** namespace.</span></span>

4.  <span data-ttu-id="b26dd-116">在代码中，使用 `Imports` 语句导入**system.web**和 `System.Drawing.Printing` 命名空间。</span><span class="sxs-lookup"><span data-stu-id="b26dd-116">In your code, use `Imports` statements to import the **System.Collections** and the `System.Drawing.Printing` namespaces.</span></span>

### <a name="code"></a><span data-ttu-id="b26dd-117">代码</span><span class="sxs-lookup"><span data-stu-id="b26dd-117">Code</span></span>

```vb
Public Sub Main()

    Dim printerName As String
    Dim currentPrinter As New PrinterSettings
    Dim size As PaperSize

    Dim printerList As New ArrayList
    For Each printerName In PrinterSettings.InstalledPrinters
        currentPrinter.PrinterName = printerName
        If PrinterHasLegalPaper(currentPrinter) Then
            printerList.Add(printerName)
            Dts.Events.FireInformation(0, "Example", _
                "Printer " & printerName & " has legal paper.", _
                String.Empty, 0, False)
        Else
            Dts.Events.FireWarning(0, "Example", _
                "Printer " & printerName & " DOES NOT have legal paper.", _
                String.Empty, 0)
        End If
    Next

    Dts.Variables("PrinterList").Value = printerList

    Dts.TaskResult = ScriptResults.Success

End Sub

Private Function PrinterHasLegalPaper( _
    ByVal thisPrinter As PrinterSettings) As Boolean

    Dim size As PaperSize
    Dim hasLegal As Boolean = False

    For Each size In thisPrinter.PaperSizes
        If size.Kind = PaperKind.Legal Then
            hasLegal = True
        End If
    Next

    Return hasLegal

End Function
```

```csharp
public void Main()
        {

            PrinterSettings currentPrinter = new PrinterSettings();
            PaperSize size;
            Boolean Flag = false;

            ArrayList printerList = new ArrayList();
            foreach (string printerName in PrinterSettings.InstalledPrinters)
            {
                currentPrinter.PrinterName = printerName;
                if (PrinterHasLegalPaper(currentPrinter))
                {
                    printerList.Add(printerName);
                    Dts.Events.FireInformation(0, "Example", "Printer " + printerName + " has legal paper.", String.Empty, 0, ref Flag);
                }
                else
                {
                    Dts.Events.FireWarning(0, "Example", "Printer " + printerName + " DOES NOT have legal paper.", String.Empty, 0);
                }
            }

            Dts.Variables["PrinterList"].Value = printerList;

            Dts.TaskResult = (int)ScriptResults.Success;

        }

        private bool PrinterHasLegalPaper(PrinterSettings thisPrinter)
        {

            bool hasLegal = false;

            foreach (PaperSize size in thisPrinter.PaperSizes)
            {
                if (size.Kind == PaperKind.Legal)
                {
                    hasLegal = true;
                }
            }

            return hasLegal;

        }
```

<span data-ttu-id="b26dd-118">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="b26dd-118">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="b26dd-119">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="b26dd-119">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="b26dd-120">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="b26dd-120">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="b26dd-121">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="b26dd-121">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="b26dd-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b26dd-122">See Also</span></span>
 [<span data-ttu-id="b26dd-123">脚本任务示例</span><span class="sxs-lookup"><span data-stu-id="b26dd-123">Script Task Examples</span></span>](../extending-packages-scripting-task-examples/script-task-examples.md)


