---
title: 使用脚本任务为 ForEach 循环收集列表 | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Foreach Loop containers
- Script task [Integration Services], Foreach loops
- Script task [Integration Services], examples
- SSIS Script task, Foreach loops
ms.assetid: 694f0462-d0c5-4191-b64e-821b1bdef055
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 039860da121efaa52115bb515b158ea10373e459
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688035"
---
# <a name="gathering-a-list-for-the-foreach-loop-with-the-script-task"></a><span data-ttu-id="e7810-102">使用脚本任务为 Foreach 循环收集列表</span><span class="sxs-lookup"><span data-stu-id="e7810-102">Gathering a List for the ForEach Loop with the Script Task</span></span>
  <span data-ttu-id="e7810-103">变量枚举器的 Foreach 枚举通过变量传递给它的各列表项，并对每一项执行相同的任务。</span><span class="sxs-lookup"><span data-stu-id="e7810-103">The Foreach from Variable Enumerator enumerates over the items in a list that is passed to it in a variable and performs the same tasks on each item.</span></span> <span data-ttu-id="e7810-104">您可以在脚本任务中使用自定义代码来填充用于此目的的列表。</span><span class="sxs-lookup"><span data-stu-id="e7810-104">You can use custom code in a Script task to populate a list for this purpose.</span></span> <span data-ttu-id="e7810-105">有关枚举器的详细信息，请参阅 [Foreach 循环容器](../control-flow/foreach-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="e7810-105">For more information about the enumerator, see [Foreach Loop Container](../control-flow/foreach-loop-container.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7810-106">如果希望创建可更方便地重用于多个包的任务，请考虑以此脚本任务示例中的代码为基础，创建自定义任务。</span><span class="sxs-lookup"><span data-stu-id="e7810-106">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="e7810-107">有关详细信息，请参阅 [开发自定义任务](../extending-packages-custom-objects/task/developing-a-custom-task.md)。</span><span class="sxs-lookup"><span data-stu-id="e7810-107">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="description"></a><span data-ttu-id="e7810-108">说明</span><span class="sxs-lookup"><span data-stu-id="e7810-108">Description</span></span>  
 <span data-ttu-id="e7810-109">下面的示例使用 `System.IO` 命名空间的方法，收集计算机中 Excel 工作簿的一个列表，其中的工作簿存在天数大于或小于用户在变量中指定的天数。</span><span class="sxs-lookup"><span data-stu-id="e7810-109">The following example uses methods from the `System.IO` namespace to gather a list of Excel workbooks on the computer that are either newer or older than a number of days specified by the user in a variable.</span></span> <span data-ttu-id="e7810-110">它会以递归方式搜索驱动器 C 的各目录中扩展名为 .xls 的文件，并检查每个文件的最新修改日期，以确定该文件是否属于此列表。</span><span class="sxs-lookup"><span data-stu-id="e7810-110">It searches directories on Drive C recursively for files that have the .xls extension and examines the date on which each file was last modified to determine whether the file belongs in the list.</span></span> <span data-ttu-id="e7810-111">它会将符合要求的文件添加到 `ArrayList` 中，并将 `ArrayList` 保存到一个变量中，以供以后在 Foreach 循环容器中使用。</span><span class="sxs-lookup"><span data-stu-id="e7810-111">It adds qualifying files to an `ArrayList` and saves the `ArrayList` to a variable for later use in a Foreach Loop container.</span></span> <span data-ttu-id="e7810-112">Foreach 循环容器配置为使用变量枚举器的 Foreach。</span><span class="sxs-lookup"><span data-stu-id="e7810-112">The Foreach Loop container is configured to use the Foreach from Variable enumerator.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7810-113">用于变量枚举器的 Foreach 的变量必须为 `Object` 类型。</span><span class="sxs-lookup"><span data-stu-id="e7810-113">The variable that you use with the Foreach from Variable Enumerator must be of type `Object`.</span></span> <span data-ttu-id="e7810-114">放入该变量中的对象必须实现以下接口之一：`System.Collections.IEnumerable`、`System.Runtime.InteropServices.ComTypes.IEnumVARIANT`、`System.ComponentModel IListSource` 或 `Microsoft.SqlServer.Dts.Runtime.Wrapper.ForEachEnumeratorHost`。</span><span class="sxs-lookup"><span data-stu-id="e7810-114">The object that you place in the variable must implement one of the following interfaces: `System.Collections.IEnumerable`, `System.Runtime.InteropServices.ComTypes.IEnumVARIANT`, `System.ComponentModel IListSource`, or `Microsoft.SqlServer.Dts.Runtime.Wrapper.ForEachEnumeratorHost`.</span></span> <span data-ttu-id="e7810-115">通常会使用 `Array` 或 `ArrayList`。</span><span class="sxs-lookup"><span data-stu-id="e7810-115">An `Array` or `ArrayList` is commonly used.</span></span> <span data-ttu-id="e7810-116">`ArrayList` 需要引用 `Imports` 命名空间，因此需要对该命名空间的 `System.Collections` 语句。</span><span class="sxs-lookup"><span data-stu-id="e7810-116">The `ArrayList` requires a reference and an `Imports` statement for the `System.Collections` namespace.</span></span>  
  
 <span data-ttu-id="e7810-117">您可以对 `FileAge` 包变量使用不同的正值和负值来试用此任务。</span><span class="sxs-lookup"><span data-stu-id="e7810-117">You can experiment with this task by using different positive and negative values for the `FileAge` package variable.</span></span> <span data-ttu-id="e7810-118">例如，可以输入 5 以搜索最近 5 天内创建的文件，或者输入 -3 以搜索 3 天以前创建的文件。</span><span class="sxs-lookup"><span data-stu-id="e7810-118">For example, you can enter 5 to search for files created in the last five days, or enter -3 to search for files that were created more than three days ago.</span></span> <span data-ttu-id="e7810-119">对于要搜索较多文件夹的驱动器，此任务可能会花费一两分钟时间。</span><span class="sxs-lookup"><span data-stu-id="e7810-119">This task may take a minute or two on a drive with many folders to search.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="e7810-120">配置此脚本任务示例</span><span class="sxs-lookup"><span data-stu-id="e7810-120">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="e7810-121">创建一个名为 `FileAge` 的 Integer 类型包变量，并输入一个正整数值或负整数值。</span><span class="sxs-lookup"><span data-stu-id="e7810-121">Create a package variable named `FileAge` of type integer and enter a positive or negative integer value.</span></span> <span data-ttu-id="e7810-122">该值为正时，代码将搜索指定天数之内创建的文件；该值为负时，代码将搜索指定天数之前创建的文件。</span><span class="sxs-lookup"><span data-stu-id="e7810-122">When the value is positive, the code searches for files newer than the specified number of days; when negative, for files older than the specified number of days.</span></span>  
  
2.  <span data-ttu-id="e7810-123">创建一个名为 `FileList` 的 `Object` 类型包变量，以接收脚本任务收集的文件列表，以供变量枚举器的 Foreach 以后使用。</span><span class="sxs-lookup"><span data-stu-id="e7810-123">Create a package variable named `FileList` of type `Object` to receive the list of files gathered by the Script task for later use by the Foreach from Variable Enumerator.</span></span>  
  
3.  <span data-ttu-id="e7810-124">将 `FileAge` 变量添加到脚本任务的 `ReadOnlyVariables` 属性中，将 `FileList` 变量添加到 `ReadWriteVariables` 属性中。</span><span class="sxs-lookup"><span data-stu-id="e7810-124">Add the `FileAge` variable to the Script task's `ReadOnlyVariables` property, and add the `FileList` variable to the `ReadWriteVariables` property.</span></span>  
  
4.  <span data-ttu-id="e7810-125">在您的代码中，导入 `System.Collections` 和 `System.IO` 命名空间。</span><span class="sxs-lookup"><span data-stu-id="e7810-125">In your code, import the `System.Collections` and the `System.IO` namespaces.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e7810-126">代码</span><span class="sxs-lookup"><span data-stu-id="e7810-126">Code</span></span>  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Math  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports System.Collections  
Imports System.IO  
  
Public Class ScriptMain  
  
  Private Const FILE_AGE As Integer = -50  
  
  Private Const FILE_ROOT As String = "C:\"  
  Private Const FILE_FILTER As String = "*.xls"  
  
  Private isCheckForNewer As Boolean = True  
  Dim fileAgeLimit As Integer  
  Private listForEnumerator As ArrayList  
  
  Public Sub Main()  
  
    fileAgeLimit = DirectCast(Dts.Variables("FileAge").Value, Integer)  
  
    ' If value provided is positive, we want files NEWER THAN n days.  
    '  If negative, we want files OLDER THAN n days.  
    If fileAgeLimit < 0 Then  
      isCheckForNewer = False  
    End If  
    ' Extract number of days as positive integer.  
    fileAgeLimit = Math.Abs(fileAgeLimit)  
  
    listForEnumerator = New ArrayList  
  
    GetFilesInFolder(FILE_ROOT)  
  
    ' Return the list of files to the variable  
    '  for later use by the Foreach from Variable enumerator.  
    System.Windows.Forms.MessageBox.Show("Matching files: " & listForEnumerator.Count.ToString, "Results", Windows.Forms.MessageBoxButtons.OK, Windows.Forms.MessageBoxIcon.Information)  
    Dts.Variables("FileList").Value = listForEnumerator  
  
    Dts.TaskResult = ScriptResults.Success  
  
  End Sub  
  
  Private Sub GetFilesInFolder(ByVal folderPath As String)  
  
    Dim localFiles() As String  
    Dim localFile As String  
    Dim fileChangeDate As Date  
    Dim fileAge As TimeSpan  
    Dim fileAgeInDays As Integer  
    Dim childFolder As String  
  
    Try  
      localFiles = Directory.GetFiles(folderPath, FILE_FILTER)  
      For Each localFile In localFiles  
        fileChangeDate = File.GetLastWriteTime(localFile)  
        fileAge = DateTime.Now.Subtract(fileChangeDate)  
        fileAgeInDays = fileAge.Days  
        CheckAgeOfFile(localFile, fileAgeInDays)  
      Next  
  
      If Directory.GetDirectories(folderPath).Length > 0 Then  
        For Each childFolder In Directory.GetDirectories(folderPath)  
          GetFilesInFolder(childFolder)  
        Next  
      End If  
  
    Catch  
      ' Ignore exceptions on special folders such as System Volume Information.  
    End Try  
  
  End Sub  
  
  Private Sub CheckAgeOfFile(ByVal localFile As String, ByVal fileAgeInDays As Integer)  
  
    If isCheckForNewer Then  
      If fileAgeInDays <= fileAgeLimit Then  
        listForEnumerator.Add(localFile)  
      End If  
    Else  
      If fileAgeInDays > fileAgeLimit Then  
        listForEnumerator.Add(localFile)  
      End If  
    End If  
  
  End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Math;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Collections;  
using System.IO;  
  
public partial class ScriptMain : Microsoft.SqlServer.Dts.Tasks.ScriptTask.VSTARTScriptObjectModelBase  
    {  
  
        private const int FILE_AGE = -50;  
  
        private const string FILE_ROOT = "C:\\";  
        private const string FILE_FILTER = "*.xls";  
  
        private bool isCheckForNewer = true;  
        int fileAgeLimit;  
        private ArrayList listForEnumerator;  
  
        public void Main()  
  {  
  
    fileAgeLimit = (int)(Dts.Variables["FileAge"].Value);  
  
    // If value provided is positive, we want files NEWER THAN n days.  
    // If negative, we want files OLDER THAN n days.  
    if (fileAgeLimit<0)  
    {  
      isCheckForNewer = false;  
    }  
    // Extract number of days as positive integer.  
    fileAgeLimit = Math.Abs(fileAgeLimit);  
  
    ArrayList listForEnumerator = new ArrayList();  
  
    GetFilesInFolder(FILE_ROOT);  
  
    // Return the list of files to the variable  
    // for later use by the Foreach from Variable enumerator.  
    System.Windows.Forms.MessageBox.Show("Matching files: "+ listForEnumerator.Count, "Results",   
MessageBoxButtons.OK, MessageBoxIcon.Information);  
    Dts.Variables["FileList"].Value = listForEnumerator;  
  
    Dts.TaskResult = (int)ScriptResults.Success;  
  
  }  
  
        private void GetFilesInFolder(string folderPath)  
        {  
  
            string[] localFiles;  
            DateTime fileChangeDate;  
            TimeSpan fileAge;  
            int fileAgeInDays;  
  
            try  
            {  
                localFiles = Directory.GetFiles(folderPath, FILE_FILTER);  
                foreach (string localFile in localFiles)  
                {  
                    fileChangeDate = File.GetLastWriteTime(localFile);  
                    fileAge = DateTime.Now.Subtract(fileChangeDate);  
                    fileAgeInDays = fileAge.Days;  
                    CheckAgeOfFile(localFile, fileAgeInDays);  
                }  
  
                if (Directory.GetDirectories(folderPath).Length > 0)  
                {  
                    foreach (string childFolder in Directory.GetDirectories(folderPath))  
                    {  
                        GetFilesInFolder(childFolder);  
                    }  
                }  
  
            }  
            catch  
            {  
                // Ignore exceptions on special folders, such as System Volume Information.  
            }  
  
        }  
  
        private void CheckAgeOfFile(string localFile, int fileAgeInDays)  
        {  
  
            if (isCheckForNewer)  
            {  
                if (fileAgeInDays <= fileAgeLimit)  
                {  
                    listForEnumerator.Add(localFile);  
                }  
            }  
            else  
            {  
                if (fileAgeInDays > fileAgeLimit)  
                {  
                    listForEnumerator.Add(localFile);  
                }  
            }  
  
        }  
  
    }  
```  
  
<span data-ttu-id="e7810-127">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="e7810-127">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="e7810-128">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="e7810-128">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="e7810-129">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="e7810-129">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="e7810-130">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="e7810-130">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7810-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7810-131">See Also</span></span>  
 <span data-ttu-id="e7810-132">[Foreach 循环容器](../control-flow/foreach-loop-container.md) </span><span class="sxs-lookup"><span data-stu-id="e7810-132">[Foreach Loop Container](../control-flow/foreach-loop-container.md) </span></span>  
 [<span data-ttu-id="e7810-133">配置 Foreach 循环容器</span><span class="sxs-lookup"><span data-stu-id="e7810-133">Configure a Foreach Loop Container</span></span>](../configure-a-foreach-loop-container.md)  
  
  
