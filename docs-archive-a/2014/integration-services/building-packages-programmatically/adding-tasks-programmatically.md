---
title: 以编程方式添加任务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- tasks [Integration Services], packages
- adding package tasks
ms.assetid: 5d4652d5-228c-4238-905c-346dd8503fdf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aa61eb2fb87f45fe5b534b96280b8b4e2c21788d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580844"
---
# <a name="adding-tasks-programmatically"></a><span data-ttu-id="6c9bc-102">以编程方式添加任务</span><span class="sxs-lookup"><span data-stu-id="6c9bc-102">Adding Tasks Programmatically</span></span>
  <span data-ttu-id="6c9bc-103">可在运行时引擎中将任务添加到下列对象类型中：</span><span class="sxs-lookup"><span data-stu-id="6c9bc-103">Tasks can be added to the following types of objects in the run-time engine:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.Package>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.Sequence>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.ForLoop>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>  
  
 <span data-ttu-id="6c9bc-104">这些类被视为容器，它们均继承了 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSequence.Executables%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-104">These classes are considered containers, and they all inherit the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSequence.Executables%2A> property.</span></span> <span data-ttu-id="6c9bc-105">容器可包含任务集合，任务是在容器执行期间，由运行库处理的可执行对象。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-105">Containers can contain a collection of tasks, which are executable objects processed by the runtime during execution of the container.</span></span> <span data-ttu-id="6c9bc-106">集合中对象的执行顺序由对容器中每个任务设置的 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> 确定。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-106">The order of execution of the objects in the collection is determined any <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> set on each task in the containers.</span></span> <span data-ttu-id="6c9bc-107">使用优先约束可使执行基于集合中的 <xref:Microsoft.SqlServer.Dts.Runtime.Executable> 的成功、失败或完成进行分支跳转。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-107">Precedence constraints enable execution branching based on the success, failure, or completion of an <xref:Microsoft.SqlServer.Dts.Runtime.Executable> in the collection.</span></span>  
  
 <span data-ttu-id="6c9bc-108">每个容器都有一个包含各个 <xref:Microsoft.SqlServer.Dts.Runtime.Executables> 对象的 <xref:Microsoft.SqlServer.Dts.Runtime.Executable> 集合。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-108">Each container has an <xref:Microsoft.SqlServer.Dts.Runtime.Executables> collection that contains the individual <xref:Microsoft.SqlServer.Dts.Runtime.Executable> objects.</span></span> <span data-ttu-id="6c9bc-109">每个可执行任务都继承并实现 <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Execute%2A> 方法和 <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Validate%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-109">Each executable task inherits and implements the <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Execute%2A> method and <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Validate%2A> method.</span></span> <span data-ttu-id="6c9bc-110">运行时引擎会调用这两个方法来处理每个 <xref:Microsoft.SqlServer.Dts.Runtime.Executable>。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-110">These two methods are called by the run-time engine to process each <xref:Microsoft.SqlServer.Dts.Runtime.Executable>.</span></span>  
  
 <span data-ttu-id="6c9bc-111">若要向包中添加任务，您需要一个具有现有 <xref:Microsoft.SqlServer.Dts.Runtime.Executables> 集合的容器。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-111">To add a task to a package, you need a container with an <xref:Microsoft.SqlServer.Dts.Runtime.Executables> existing collection.</span></span> <span data-ttu-id="6c9bc-112">大多数情况下，要添加到该集合中的任务为包。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-112">Most of the time, the task that you will add to the collection is a package.</span></span> <span data-ttu-id="6c9bc-113">若要向容器的该集合中添加新任务可执行文件，可以调用 <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-113">To add the new task executable into the collection for that container, you call the <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> method .</span></span> <span data-ttu-id="6c9bc-114">该方法只有一个参数，是个字符串，它包含要添加的任务的 CLSID、PROGID、STOCK 名字对象或 <xref:Microsoft.SqlServer.Dts.Runtime.TaskInfo.CreationName%2A>。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-114">The method has a single parameter, a string, that contains the CLSID, PROGID, STOCK moniker, or <xref:Microsoft.SqlServer.Dts.Runtime.TaskInfo.CreationName%2A> of the task you are adding.</span></span>  
  
## <a name="task-names"></a><span data-ttu-id="6c9bc-115">任务名称</span><span class="sxs-lookup"><span data-stu-id="6c9bc-115">Task Names</span></span>  
 <span data-ttu-id="6c9bc-116">虽然您可以通过名称或 ID 指定任务，但 `STOCK` 名字对象是 <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> 方法中最常用的参数。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-116">Although you can specify a task by name or by ID, the `STOCK` moniker is the parameter used most often in the <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> method.</span></span> <span data-ttu-id="6c9bc-117">若要向 `STOCK` 名字对象所标识的可执行文件添加任务，请使用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="6c9bc-117">To add a task to an executable identified by the `STOCK` moniker, use the following syntax:</span></span>  
  
```csharp  
Executable exec = package.Executables.Add("STOCK:BulkInsertTask");  
  
```  
  
```vb  
Dim exec As Executable = package.Executables.Add("STOCK:BulkInsertTask")  
  
```  
  
 <span data-ttu-id="6c9bc-118">下面列出了 `STOCK` 名字对象后使用的每个任务的名称。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-118">The following list shows the names for each task that are used after the `STOCK` moniker.</span></span>  
  
-   <span data-ttu-id="6c9bc-119">ActiveXScriptTask</span><span class="sxs-lookup"><span data-stu-id="6c9bc-119">ActiveXScriptTask</span></span>  
  
-   <span data-ttu-id="6c9bc-120">BulkInsertTask</span><span class="sxs-lookup"><span data-stu-id="6c9bc-120">BulkInsertTask</span></span>  
  
-   <span data-ttu-id="6c9bc-121">ExecuteProcessTask</span><span class="sxs-lookup"><span data-stu-id="6c9bc-121">ExecuteProcessTask</span></span>  
  
-   <span data-ttu-id="6c9bc-122">ExecutePackageTask</span><span class="sxs-lookup"><span data-stu-id="6c9bc-122">ExecutePackageTask</span></span>  
  
-   <span data-ttu-id="6c9bc-123">Exec80PackageTask</span><span class="sxs-lookup"><span data-stu-id="6c9bc-123">Exec80PackageTask</span></span>  
  
-   <span data-ttu-id="6c9bc-124">FileSystemTask</span><span class="sxs-lookup"><span data-stu-id="6c9bc-124">FileSystemTask</span></span>  
  
-   <span data-ttu-id="6c9bc-125">FTPTask</span><span class="sxs-lookup"><span data-stu-id="6c9bc-125">FTPTask</span></span>  
  
-   <span data-ttu-id="6c9bc-126">MSMQTask</span><span class="sxs-lookup"><span data-stu-id="6c9bc-126">MSMQTask</span></span>  
  
-   <span data-ttu-id="6c9bc-127">PipelineTask</span><span class="sxs-lookup"><span data-stu-id="6c9bc-127">PipelineTask</span></span>  
  
-   <span data-ttu-id="6c9bc-128">ScriptTask</span><span class="sxs-lookup"><span data-stu-id="6c9bc-128">ScriptTask</span></span>  
  
-   <span data-ttu-id="6c9bc-129">SendMailTask</span><span class="sxs-lookup"><span data-stu-id="6c9bc-129">SendMailTask</span></span>  
  
-   <span data-ttu-id="6c9bc-130">SQLTask</span><span class="sxs-lookup"><span data-stu-id="6c9bc-130">SQLTask</span></span>  
  
-   <span data-ttu-id="6c9bc-131">TransferStoredProceduresTask</span><span class="sxs-lookup"><span data-stu-id="6c9bc-131">TransferStoredProceduresTask</span></span>  
  
-   <span data-ttu-id="6c9bc-132">TransferLoginsTask</span><span class="sxs-lookup"><span data-stu-id="6c9bc-132">TransferLoginsTask</span></span>  
  
-   <span data-ttu-id="6c9bc-133">TransferErrorMessagesTask</span><span class="sxs-lookup"><span data-stu-id="6c9bc-133">TransferErrorMessagesTask</span></span>  
  
-   <span data-ttu-id="6c9bc-134">TransferJobsTask</span><span class="sxs-lookup"><span data-stu-id="6c9bc-134">TransferJobsTask</span></span>  
  
-   <span data-ttu-id="6c9bc-135">TransferObjectsTask</span><span class="sxs-lookup"><span data-stu-id="6c9bc-135">TransferObjectsTask</span></span>  
  
-   <span data-ttu-id="6c9bc-136">TransferDatabaseTask</span><span class="sxs-lookup"><span data-stu-id="6c9bc-136">TransferDatabaseTask</span></span>  
  
-   <span data-ttu-id="6c9bc-137">WebServiceTask</span><span class="sxs-lookup"><span data-stu-id="6c9bc-137">WebServiceTask</span></span>  
  
-   <span data-ttu-id="6c9bc-138">WmiDataReaderTask</span><span class="sxs-lookup"><span data-stu-id="6c9bc-138">WmiDataReaderTask</span></span>  
  
-   <span data-ttu-id="6c9bc-139">WmiEventWatcherTask</span><span class="sxs-lookup"><span data-stu-id="6c9bc-139">WmiEventWatcherTask</span></span>  
  
-   <span data-ttu-id="6c9bc-140">XMLTask</span><span class="sxs-lookup"><span data-stu-id="6c9bc-140">XMLTask</span></span>  
  
 <span data-ttu-id="6c9bc-141">如果您倾向于使用更为明确的语法，或您要添加的任务没有 STOCK 名字对象，则您可以使用任务的长名称来向可执行文件添加任务。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-141">If you prefer a more explicit syntax, or if the task that you want to add does not have a STOCK moniker, you can add the task to the executable using its long name.</span></span> <span data-ttu-id="6c9bc-142">此语法还要求您指定任务的版本号。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-142">This syntax requires that you also specify the version number of the task.</span></span>  
  
```csharp  
Executable exec = package.Executables.Add(  
  "Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask, " +  
  "Microsoft.SqlServer.ScriptTask, Version=10.0.000.0, " +  
  "Culture=neutral, PublicKeyToken=89845dcd8080cc91");  
```  
  
```vb  
Dim exec As Executable = package.Executables.Add( _  
  "Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask, " & _  
  "Microsoft.SqlServer.ScriptTask, Version=10.0.000.0, " & _  
  "Culture=neutral, PublicKeyToken=89845dcd8080cc91")  
```  
  
 <span data-ttu-id="6c9bc-143">可以使用类的 AssemblyQualifiedName  属性，以编程方式获取任务的长名称，而无须指定任务版本，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-143">You can obtain the long name for the task programmatically, without having to specify the task version, by using the **AssemblyQualifiedName** property of the class, as shown in the following example.</span></span> <span data-ttu-id="6c9bc-144">此示例需要引用 Microsoft.SqlServer.SQLTask 程序集。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-144">This example requires a reference to the Microsoft.SqlServer.SQLTask assembly.</span></span>  
  
```csharp  
using Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask;  
...  
      Executable exec = package.Executables.Add(  
        typeof(Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask.ExecuteSQLTask).AssemblyQualifiedName);  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask  
...  
    Dim exec As Executable = package.Executables.Add( _  
      GetType(Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask.ExecuteSQLTask).AssemblyQualifiedName)  
```  
  
 <span data-ttu-id="6c9bc-145">下面的代码示例演示如何从新包创建 <xref:Microsoft.SqlServer.Dts.Runtime.Executables> 集合，并使用相应任务的 `STOCK` 名字对象向该集合添加一个文件系统任务和一个大容量插入任务。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-145">The following code example shows how to create an <xref:Microsoft.SqlServer.Dts.Runtime.Executables> collection from a new package, and then add a File System task and a Bulk Insert task to the collection, by using their `STOCK` monikers.</span></span> <span data-ttu-id="6c9bc-146">此示例需要引用 Microsoft.SqlServer.FileSystemTask 和 Microsoft.SqlServer.BulkInsertTask 程序集。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-146">This example requires a reference to the Microsoft.SqlServer.FileSystemTask and Microsoft.SqlServer.BulkInsertTask assemblies.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Tasks.FileSystemTask;  
using Microsoft.SqlServer.Dts.Tasks.BulkInsertTask;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
      // Add a File System task to the package.  
      Executable exec1 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileSystemTask = exec1 as TaskHost;  
      // Add a Bulk Insert task to the package.  
      Executable exec2 = p.Executables.Add("STOCK:BulkInsertTask");  
      TaskHost thBulkInsertTask = exec2 as TaskHost;  
  
      // Iterate through the package Executables collection.  
      Executables pExecs = p.Executables;  
      foreach (Executable pExec in pExecs)  
      {  
        TaskHost taskHost = (TaskHost)pExec;  
        Console.WriteLine("Type {0}", taskHost.InnerObject.ToString());  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Tasks.FileSystemTask  
Imports Microsoft.SqlServer.Dts.Tasks.BulkInsertTask  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    ' Add a File System task to the package.  
    Dim exec1 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileSystemTask As TaskHost = CType(exec1, TaskHost)  
    ' Add a Bulk Insert task to the package.  
    Dim exec2 As Executable = p.Executables.Add("STOCK:BulkInsertTask")  
    Dim thBulkInsertTask As TaskHost = CType(exec2, TaskHost)  
  
    ' Iterate through the package Executables collection.  
    Dim pExecs As Executables = p.Executables  
    Dim pExec As Executable  
    For Each pExec In pExecs  
      Dim taskHost As TaskHost = CType(pExec, TaskHost)  
      Console.WriteLine("Type {0}", taskHost.InnerObject.ToString())  
    Next  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
 <span data-ttu-id="6c9bc-147">**示例输出：**</span><span class="sxs-lookup"><span data-stu-id="6c9bc-147">**Sample Output:**</span></span>  
  
 `Type Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask`  
  
 `Type Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask`  
  
## <a name="taskhost-container"></a><span data-ttu-id="6c9bc-148">TaskHost 容器</span><span class="sxs-lookup"><span data-stu-id="6c9bc-148">TaskHost Container</span></span>  
 <span data-ttu-id="6c9bc-149"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 类是一个容器，虽然不显示在图形用户界面中，但对于编程非常重要。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-149">The <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> class is a container that does not appear in the graphical user interface, but is very important in programming.</span></span> <span data-ttu-id="6c9bc-150">此类是所有任务的包装。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-150">This class is a wrapper for every task.</span></span> <span data-ttu-id="6c9bc-151">使用 <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> 方法，作为 <xref:Microsoft.SqlServer.Dts.Runtime.Executable> 对象添加到包中的任务可转换为 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 对象。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-151">Tasks that are added to the package by using the <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> method as an <xref:Microsoft.SqlServer.Dts.Runtime.Executable> object can be cast as a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> object.</span></span> <span data-ttu-id="6c9bc-152">当任务转换为 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 后，您可以对其使用其他属性和方法。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-152">When a task is cast as a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, you can use additional properties and methods on the task.</span></span> <span data-ttu-id="6c9bc-153">此外，任务本身也可以通过 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A> 的 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 属性访问。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-153">Also, the task itself can be accessed through the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A> property of the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>.</span></span> <span data-ttu-id="6c9bc-154">依据您的需求，您可以决定将该任务保留为 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 对象，这样就可以通过 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> 集合使用任务的属性。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-154">Depending on your needs, you may decide to keep the task as a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> object so that you can use the properties of the task through the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> collection.</span></span> <span data-ttu-id="6c9bc-155">使用 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> 的优势是可以编写更为通用的代码。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-155">The advantage of using the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> is that you can write more generic code.</span></span> <span data-ttu-id="6c9bc-156">如果您需要特定于任务的代码，则应将任务转换为其适当的对象。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-156">If you need very specific code for a task, then you should cast the task to its appropriate object.</span></span>  
  
 <span data-ttu-id="6c9bc-157">下面的代码示例演示如何将一个包含 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 的 <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask> (thBulkInsertTask) 转换为一个 <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask> 对象。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-157">The following code example shows how to cast a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, thBulkInsertTask, that contains a <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask>, to a <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask> object.</span></span>  
  
```csharp  
BulkInsertTask myTask = thBulkInsertTask.InnerObject as BulkInsertTask;  
```  
  
```vb  
Dim myTask As BulkInsertTask = CType(thBulkInsertTask.InnerObject, BulkInsertTask)  
```  
  
 <span data-ttu-id="6c9bc-158">下面的代码示例演示如何将可执行文件转换为 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>，然后使用 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A> 属性确定主机包含的可执行文件的类型。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-158">The following code example shows how to cast the executable to a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, and then use the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A> property to determine which type of executable is contained by the host.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Tasks.FileSystemTask;  
using Microsoft.SqlServer.Dts.Tasks.BulkInsertTask;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
      // Add a File System task to the package.  
      Executable exec1 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileSystemTask1 = exec1 as TaskHost;  
      // Add a Bulk Insert task to the package.  
      Executable exec2 = p.Executables.Add("STOCK:BulkInsertTask");  
      TaskHost thFileSystemTask2 = exec2 as TaskHost;  
  
      // Iterate through the package Executables collection.  
      Executables pExecs = p.Executables;  
      foreach (Executable pExec in pExecs)  
      {  
        TaskHost taskHost = (TaskHost)pExec;  
        if (taskHost.InnerObject is Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask)  
        {  
          // Do work with FileSystemTask here.  
          Console.WriteLine("Found task of type {0}", taskHost.InnerObject.ToString());  
        }  
        else if (taskHost.InnerObject is Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask)  
        {  
          // Do work with BulkInsertTask here.  
          Console.WriteLine("Found task of type {0}", taskHost.InnerObject.ToString());  
        }  
        // Add additional statements to check InnerObject, if desired.  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Tasks.FileSystemTask  
Imports Microsoft.SqlServer.Dts.Tasks.BulkInsertTask  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    ' Add a File System task to the package.  
    Dim exec1 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileSystemTask1 As TaskHost = CType(exec1, TaskHost)  
    ' Add a Bulk Insert task to the package.  
    Dim exec2 As Executable = p.Executables.Add("STOCK:BulkInsertTask")  
    Dim thFileSystemTask2 As TaskHost = CType(exec2, TaskHost)  
  
    ' Iterate through the package Executables collection.  
    Dim pExecs As Executables = p.Executables  
    Dim pExec As Executable  
    For Each pExec In pExecs  
      Dim taskHost As TaskHost = CType(pExec, TaskHost)  
      If TypeOf taskHost.InnerObject Is Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask Then  
        ' Do work with FileSystemTask here.  
        Console.WriteLine("Found task of type {0}", taskHost.InnerObject.ToString())  
      ElseIf TypeOf taskHost.InnerObject Is Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask Then  
        ' Do work with BulkInsertTask here.  
        Console.WriteLine("Found task of type {0}", taskHost.InnerObject.ToString())  
      End If  
      ' Add additional statements to check InnerObject, if desired.  
    Next  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
 <span data-ttu-id="6c9bc-159">**示例输出：**</span><span class="sxs-lookup"><span data-stu-id="6c9bc-159">**Sample Output:**</span></span>  
  
 `Found task of type Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask`  
  
 `Found task of type Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask`  
  
 <span data-ttu-id="6c9bc-160"><xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> 语句返回一个可执行文件，该文件从新创建的 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 对象转换为 <xref:Microsoft.SqlServer.Dts.Runtime.Executable> 对象。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-160">The <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> statement returns an executable that is cast to a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> object from the newly created <xref:Microsoft.SqlServer.Dts.Runtime.Executable> object.</span></span>  
  
 <span data-ttu-id="6c9bc-161">若要对新对象设置属性或调用方法，您有两种选择：</span><span class="sxs-lookup"><span data-stu-id="6c9bc-161">To set properties or to call methods on the new object, you have two options:</span></span>  
  
1.  <span data-ttu-id="6c9bc-162">使用 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> 的 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 集合。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-162">Use the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> collection of the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>.</span></span> <span data-ttu-id="6c9bc-163">例如，若要从该对象获取属性，可使用 `th.Properties["propertyname"].GetValue(th))`。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-163">For example, to obtain a property from the object, use `th.Properties["propertyname"].GetValue(th))`.</span></span> <span data-ttu-id="6c9bc-164">若要设置属性，可使用 `th.Properties["propertyname"].SetValue(th, <value>);`。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-164">To set a property, use `th.Properties["propertyname"].SetValue(th, <value>);`.</span></span>  
  
2.  <span data-ttu-id="6c9bc-165">将 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A> 的 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 转换为任务类。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-165">Cast the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A> of the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> to the task class.</span></span> <span data-ttu-id="6c9bc-166">例如，若要在将大容量插入任务作为 <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask> 添加到包中，然后将其转换为 <xref:Microsoft.SqlServer.Dts.Runtime.Executable> 之后，再将其转换为 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>，可使用 `BulkInsertTask myTask = th.InnerObject as BulkInsertTask;`。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-166">For example, to cast the Bulk Insert task to a <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask> after it has been added to a package as an <xref:Microsoft.SqlServer.Dts.Runtime.Executable> and subsequently cast to a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, use `BulkInsertTask myTask = th.InnerObject as BulkInsertTask;`.</span></span>  
  
 <span data-ttu-id="6c9bc-167">在代码中使用 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 类而不是转换为特定于任务的类具有下列好处：</span><span class="sxs-lookup"><span data-stu-id="6c9bc-167">Using the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> class in code, instead of casting to the task-specific class has the following advantages:</span></span>  
  
-   <span data-ttu-id="6c9bc-168"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> 访问接口不要求在代码中引用程序集。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-168">The <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> provider does not require a reference to the assembly in the code.</span></span>  
  
-   <span data-ttu-id="6c9bc-169">您可以编写适用于任何任务的通用例程，因为您无需在编译时知道任务的名称。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-169">You can code generic routines that work for any task, because you do not have to know the name of the task at compile time.</span></span> <span data-ttu-id="6c9bc-170">这样的通用例程包含的方法中，您向方法传递任务的名称，因此方法代码适用于所有任务。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-170">Such generic routines include methods where you pass in the name of the task to the method, and the method code works for all tasks.</span></span> <span data-ttu-id="6c9bc-171">这是一种编写测试代码的好方法。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-171">This is a good method for writing test code.</span></span>  
  
 <span data-ttu-id="6c9bc-172">从 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 转换为特定于任务的类具有下列好处：</span><span class="sxs-lookup"><span data-stu-id="6c9bc-172">Casting from the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> to the task-specific class has the following advantages:</span></span>  
  
-   <span data-ttu-id="6c9bc-173">Visual Studio 项目提供语句完成 (IntelliSense)。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-173">The Visual Studio project gives you statement completion (IntelliSense).</span></span>  
  
-   <span data-ttu-id="6c9bc-174">代码的运行速度可能会更快。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-174">The code may run faster.</span></span>  
  
-   <span data-ttu-id="6c9bc-175">特定于任务的对象允许早期绑定和结果优化。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-175">Task-specific objects enable early binding and the resulting optimizations.</span></span> <span data-ttu-id="6c9bc-176">有关早期绑定和后期绑定的详细信息，请参阅 Visual Basic 语言概念中的主题“早期绑定和后期绑定”。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-176">For more information about early and late binding, see the topic "Early and Late Binding" in Visual Basic Language Concepts.</span></span>  
  
 <span data-ttu-id="6c9bc-177">下面的代码示例具体阐释了重用任务代码的概念。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-177">The following code example expands on the concept of reusing task code.</span></span> <span data-ttu-id="6c9bc-178">该代码示例没有将任务转换为其特定的类等价对象，而是演示了如何将可执行文件转换为 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>，随后使用 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> 编写针对所有任务的通用代码。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-178">Instead of casting tasks to their specific class equivalents, the code example shows how to cast the executable to a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, and then uses the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> to write generic code against all the tasks.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package package = new Package();  
  
      string[] tasks = { "STOCK:SQLTask", "STOCK:ScriptTask",   
        "STOCK:ExecuteProcessTask", "STOCK:PipelineTask",   
        "STOCK:FTPTask", "STOCK:SendMailTask", "STOCK:MSMQTask" };  
  
      foreach (string s in tasks)  
      {  
        TaskHost taskhost = package.Executables.Add(s) as TaskHost;  
        DtsProperties props = taskhost.Properties;  
        Console.WriteLine("Enumerating properties on " + taskhost.Name);  
        Console.WriteLine(" TaskHost.InnerObject is " + taskhost.InnerObject.ToString());  
        Console.WriteLine();  
  
        foreach (DtsProperty prop in props)  
        {  
          Console.WriteLine("Properties for " + prop.Name);  
          Console.WriteLine("Name : " + prop.Name);  
          Console.WriteLine("Type : " + prop.Type.ToString());  
          Console.WriteLine("Readable : " + prop.Get.ToString());  
          Console.WriteLine("Writable : " + prop.Set.ToString());  
          Console.WriteLine();  
        }  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Package = New Package()  
  
    Dim tasks() As String = New String() {"STOCK:SQLTask", "STOCK:ScriptTask", _  
              "STOCK:ExecuteProcessTask", "STOCK:PipelineTask", _  
              "STOCK:FTPTask", "STOCK:SendMailTask", "STOCK:MSMQTask"}  
  
    For Each s As String In tasks  
  
      Dim taskhost As TaskHost = CType(package.Executables.Add(s), TaskHost)  
      Dim props As DtsProperties = taskhost.Properties  
      Console.WriteLine("Enumerating properties on " & taskhost.Name)  
      Console.WriteLine(" TaskHost.InnerObject is " & taskhost.InnerObject.ToString())  
      Console.WriteLine()  
  
      For Each prop As DtsProperty In props  
        Console.WriteLine("Properties for " + prop.Name)  
        Console.WriteLine(" Name : " + prop.Name)  
        Console.WriteLine(" Type : " + prop.Type.ToString())  
        Console.WriteLine(" Readable : " + prop.Get.ToString())  
        Console.WriteLine(" Writable : " + prop.Set.ToString())  
        Console.WriteLine()  
      Next  
  
    Next  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
## <a name="external-resources"></a><span data-ttu-id="6c9bc-179">外部资源</span><span class="sxs-lookup"><span data-stu-id="6c9bc-179">External Resources</span></span>  
 <span data-ttu-id="6c9bc-180">blogs.msdn.com 上的博客文章 [EzAPI - 为 SQL Server 2012 更新](https://go.microsoft.com/fwlink/?LinkId=243223)。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-180">Blog entry, [EzAPI - Updated for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223), on blogs.msdn.com.</span></span>  
  
<span data-ttu-id="6c9bc-181">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="6c9bc-181">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="6c9bc-182">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="6c9bc-182">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="6c9bc-183">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="6c9bc-183">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="6c9bc-184">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="6c9bc-184">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c9bc-185">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6c9bc-185">See Also</span></span>  
 [<span data-ttu-id="6c9bc-186">以编程方式连接任务</span><span class="sxs-lookup"><span data-stu-id="6c9bc-186">Connecting Tasks Programmatically</span></span>](../building-packages-programmatically/connecting-tasks-programmatically.md)  
  
  
