---
title: 以编程方式加载和运行本地包 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Integration Services packages, running
- events [Integration Services], capturing
- packages [Integration Services], running
- loading packages programmatically
- Visual Basic [Integration Services]
- running packages [Integration Services]
- programmatically load and run packages [SSIS]
ms.assetid: 2f9fc1a8-a001-4c54-8c64-63b443725422
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a29faf623c02fea4fd8722c235f595f0fe4492e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687956"
---
# <a name="loading-and-running-a-local-package-programmatically"></a><span data-ttu-id="6d2fd-102">以编程方式加载和运行本地包</span><span class="sxs-lookup"><span data-stu-id="6d2fd-102">Loading and Running a Local Package Programmatically</span></span>
  <span data-ttu-id="6d2fd-103">可以使用[运行包](../packages/run-integration-services-ssis-packages.md)中介绍的方法，根据需要或在预定时间运行 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-103">You can run [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages as needed or at predetermined times by using the methods described in [Running Packages](../packages/run-integration-services-ssis-packages.md).</span></span> <span data-ttu-id="6d2fd-104">但是，也可以只用几行代码，从自定义应用程序（如 Windows 窗体应用程序、控制台应用程序、ASP.NET Web 窗体或 Web 服务、Windows 服务）运行包。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-104">However, with only a few lines of code, you can also run a package from a custom application such as a Windows Forms application, a console application, an ASP.NET Web form or Web service, or a Windows service.</span></span>  
  
 <span data-ttu-id="6d2fd-105">本主题讨论：</span><span class="sxs-lookup"><span data-stu-id="6d2fd-105">This topic discusses:</span></span>  
  
-   <span data-ttu-id="6d2fd-106">以编程方式加载包</span><span class="sxs-lookup"><span data-stu-id="6d2fd-106">Loading a package programmatically</span></span>  
  
-   <span data-ttu-id="6d2fd-107">以编程方式运行包</span><span class="sxs-lookup"><span data-stu-id="6d2fd-107">Running a package programmatically</span></span>  
  
 <span data-ttu-id="6d2fd-108">本主题中使用的所有加载和运行包的方法都需要引用 `Microsoft.SqlServer.ManagedDTS` 程序集。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-108">All of the methods used in this topic to load and run packages require a reference to the `Microsoft.SqlServer.ManagedDTS` assembly.</span></span> <span data-ttu-id="6d2fd-109">在新项目中添加该引用后，请使用 `using` 或 `Imports` 语句导入 <xref:Microsoft.SqlServer.Dts.Runtime> 命名空间。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-109">After adding the reference in a new project, import the <xref:Microsoft.SqlServer.Dts.Runtime> namespace with a `using` or `Imports` statement.</span></span>  
  
## <a name="loading-a-package-programmatically"></a><span data-ttu-id="6d2fd-110">以编程方式加载包</span><span class="sxs-lookup"><span data-stu-id="6d2fd-110">Loading a Package Programmatically</span></span>  
 <span data-ttu-id="6d2fd-111">若要以编程方式在本地计算机中加载包，无论包是本地存储还是远程存储，都可以调用以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="6d2fd-111">To load a package programmatically on the local computer, whether the package is stored locally or remotely, call one of the following methods:</span></span>  
  
|<span data-ttu-id="6d2fd-112">存储位置</span><span class="sxs-lookup"><span data-stu-id="6d2fd-112">Storage Location</span></span>|<span data-ttu-id="6d2fd-113">调用的方法</span><span class="sxs-lookup"><span data-stu-id="6d2fd-113">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="6d2fd-114">文件</span><span class="sxs-lookup"><span data-stu-id="6d2fd-114">File</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadPackage%2A>|  
|<span data-ttu-id="6d2fd-115">SSIS 包存储区</span><span class="sxs-lookup"><span data-stu-id="6d2fd-115">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromSqlServer%2A>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6d2fd-116"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 类中用于处理 SSIS 包存储区的方法只支持“.”、localhost 或本地服务器的服务器名称。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-116">The methods of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> class for working with the SSIS Package Store only support ".", localhost, or the server name for the local server.</span></span> <span data-ttu-id="6d2fd-117">不能使用“(local)”。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-117">You cannot use "(local)".</span></span>  
  
## <a name="running-a-package-programmatically"></a><span data-ttu-id="6d2fd-118">以编程方式运行包</span><span class="sxs-lookup"><span data-stu-id="6d2fd-118">Running a Package Programmatically</span></span>  
 <span data-ttu-id="6d2fd-119">以托管代码方式开发在本地计算机上运行包的自定义应用程序需要采用以下方式。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-119">Developing a custom application in managed code that runs a package on the local computer requires the following approach.</span></span> <span data-ttu-id="6d2fd-120">此处总结的步骤在随后的控制台应用程序示例中演示。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-120">The steps summarized here are demonstrated in the sample console application that follows.</span></span>  
  
#### <a name="to-run-a-package-on-the-local-computer-programmatically"></a><span data-ttu-id="6d2fd-121">以编程方式在本地计算机中运行包</span><span class="sxs-lookup"><span data-stu-id="6d2fd-121">To run a package on the local computer programmatically</span></span>  
  
1.  <span data-ttu-id="6d2fd-122">启动 Visual Studio 开发环境，以您首选的开发语言创建新的应用程序。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-122">Start the Visual Studio development environment, and create a new application in your preferred development language.</span></span> <span data-ttu-id="6d2fd-123">本示例使用的是控制台应用程序；但您也可以从 Windows 窗体应用程序、ASP.NET Web 窗体或 Web 服务或者 Windows 服务运行包。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-123">This example uses a console application; however you can also run a package from a Windows Forms application, an ASP.NET Web form or Web service, or a Windows service.</span></span>  
  
2.  <span data-ttu-id="6d2fd-124">在“项目”  菜单上，单击“添加引用”  ，向 Microsoft.SqlServer.ManagedDTS.dll  添加一个引用。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-124">On the **Project** menu, click **Add Reference** and add a reference to **Microsoft.SqlServer.ManagedDTS.dll**.</span></span> <span data-ttu-id="6d2fd-125">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="6d2fd-125">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="6d2fd-126">使用 Visual Basic `Imports` 语句或 c # `using` 语句来导入**Microsoft SqlServer**命名空间。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-126">Use the Visual Basic `Imports` statement or the C# `using` statement to import the **Microsoft.SqlServer.Dts.Runtime** namespace.</span></span>  
  
4.  <span data-ttu-id="6d2fd-127">在主例程中添加以下代码。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-127">Add the following code in the main routine.</span></span> <span data-ttu-id="6d2fd-128">完成的控制台应用程序应类似于下面的示例。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-128">The completed console application should look like the following example.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6d2fd-129">该示例代码演示如何使用 <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadPackage%2A> 方法从文件系统加载包。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-129">The sample code demonstrates loading the package from the file system by using the <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadPackage%2A> method.</span></span> <span data-ttu-id="6d2fd-130">但您也可以通过调用 <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromSqlServer%2A> 方法，从 MSDB 数据库加载包，或者通过调用 <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A> 方法，从 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包存储区加载包。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-130">However you can also load the package from the MSDB database by calling the <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromSqlServer%2A> method, or from the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package store by calling the <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A> method.</span></span>  
  
5.  <span data-ttu-id="6d2fd-131">运行该项目。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-131">Run the project.</span></span> <span data-ttu-id="6d2fd-132">示例代码执行随 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 示例安装的 CalculatedColumns 示例包。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-132">The sample code executes the CalculatedColumns sample package that is installed with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] samples.</span></span> <span data-ttu-id="6d2fd-133">包执行的结果显示在控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-133">The result of package execution is displayed in the console window.</span></span>  
  
### <a name="sample-code"></a><span data-ttu-id="6d2fd-134">代码示例</span><span class="sxs-lookup"><span data-stu-id="6d2fd-134">Sample Code</span></span>  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim pkgLocation As String  
    Dim pkg As New Package  
    Dim app As New Application  
    Dim pkgResults As DTSExecResult  
  
    pkgLocation = _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx"  
    pkg = app.LoadPackage(pkgLocation, Nothing)  
    pkgResults = pkg.Execute()  
  
    Console.WriteLine(pkgResults.ToString())  
    Console.ReadKey()  
  
  End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace RunFromClientAppCS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string pkgLocation;  
      Package pkg;  
      Application app;  
      DTSExecResult pkgResults;  
  
      pkgLocation =  
        @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx";  
      app = new Application();  
      pkg = app.LoadPackage(pkgLocation, null);  
      pkgResults = pkg.Execute();  
  
      Console.WriteLine(pkgResults.ToString());  
      Console.ReadKey();  
    }  
  }  
}  
```  
  
## <a name="capturing-events-from-a-running-package"></a><span data-ttu-id="6d2fd-135">从运行中的包捕获事件</span><span class="sxs-lookup"><span data-stu-id="6d2fd-135">Capturing Events from a Running Package</span></span>  
 <span data-ttu-id="6d2fd-136">当您按照上面的示例所示以编程方式运行包时，还可以捕获包执行时发生的错误及其他事件。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-136">When you run a package programmatically as shown in the preceding sample, you may also want to capture errors and other events that occur as the package executes.</span></span> <span data-ttu-id="6d2fd-137">为此，请添加从 <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> 类继承的类，并在加载包时传递对该类的引用。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-137">You can accomplish this by adding a class that inherits from the <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> class, and by passing a reference to that class when you load the package.</span></span> <span data-ttu-id="6d2fd-138">下面的示例仅捕获 <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents.OnError%2A> 事件，但还有其他很多事件可以通过 <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> 类捕获。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-138">Although the following example captures only the <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents.OnError%2A> event, there are many other events that the <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> class lets you capture.</span></span>  
  
#### <a name="to-run-a-package-on-the-local-computer-programmatically-and-capture-package-events"></a><span data-ttu-id="6d2fd-139">以编程方式在本地计算机中运行包同时捕获包事件</span><span class="sxs-lookup"><span data-stu-id="6d2fd-139">To run a package on the local computer programmatically and capture package events</span></span>  
  
1.  <span data-ttu-id="6d2fd-140">按照前面示例中的步骤为此示例创建项目。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-140">Follow the steps in the preceding example to create a project for this example.</span></span>  
  
2.  <span data-ttu-id="6d2fd-141">在主例程中添加以下代码。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-141">Add the following code in the main routine.</span></span> <span data-ttu-id="6d2fd-142">完成的控制台应用程序应类似于下面的示例。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-142">The completed console application should look like the following example.</span></span>  
  
3.  <span data-ttu-id="6d2fd-143">运行该项目。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-143">Run the project.</span></span> <span data-ttu-id="6d2fd-144">示例代码执行随 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 示例安装的 CalculatedColumns 示例包。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-144">The sample code executes the CalculatedColumns sample package that is installed with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] samples.</span></span> <span data-ttu-id="6d2fd-145">包执行的结果显示在控制台窗口中，同时显示发生的所有错误。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-145">The result of package execution is displayed in the console window, along with any errors that occur.</span></span>  
  
### <a name="sample-code"></a><span data-ttu-id="6d2fd-146">代码示例</span><span class="sxs-lookup"><span data-stu-id="6d2fd-146">Sample Code</span></span>  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim pkgLocation As String  
    Dim pkg As New Package  
    Dim app As New Application  
    Dim pkgResults As DTSExecResult  
  
    Dim eventListener As New EventListener()  
  
    pkgLocation = _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx"  
    pkg = app.LoadPackage(pkgLocation, eventListener)  
    pkgResults = pkg.Execute(Nothing, Nothing, eventListener, Nothing, Nothing)  
  
    Console.WriteLine(pkgResults.ToString())  
    Console.ReadKey()  
  
  End Sub  
  
End Module  
  
Class EventListener  
  Inherits DefaultEvents  
  
  Public Overrides Function OnError(ByVal source As Microsoft.SqlServer.Dts.Runtime.DtsObject, _  
    ByVal errorCode As Integer, ByVal subComponent As String, ByVal description As String, _  
    ByVal helpFile As String, ByVal helpContext As Integer, _  
    ByVal idofInterfaceWithError As String) As Boolean  
  
    ' Add application-specific diagnostics here.  
    Console.WriteLine("Error in {0}/{1} : {2}", source, subComponent, description)  
    Return False  
  
  End Function  
  
End Class  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace RunFromClientAppWithEventsCS  
{  
  class MyEventListener : DefaultEvents  
  {  
    public override bool OnError(DtsObject source, int errorCode, string subComponent,   
      string description, string helpFile, int helpContext, string idofInterfaceWithError)  
    {  
      // Add application-specific diagnostics here.  
      Console.WriteLine("Error in {0}/{1} : {2}", source, subComponent, description);  
      return false;  
    }  
  }  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string pkgLocation;  
      Package pkg;  
      Application app;  
      DTSExecResult pkgResults;  
  
      MyEventListener eventListener = new MyEventListener();  
  
      pkgLocation =  
        @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx";  
      app = new Application();  
      pkg = app.LoadPackage(pkgLocation, eventListener);  
      pkgResults = pkg.Execute(null, null, eventListener, null, null);  
  
      Console.WriteLine(pkgResults.ToString());  
      Console.ReadKey();  
    }  
  }  
}  
```  
  
<span data-ttu-id="6d2fd-147">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="6d2fd-147">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="6d2fd-148">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="6d2fd-148">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="6d2fd-149">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="6d2fd-149">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="6d2fd-150">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="6d2fd-150">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d2fd-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6d2fd-151">See Also</span></span>  
 <span data-ttu-id="6d2fd-152">[了解本地执行与远程执行之间的差异](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md) </span><span class="sxs-lookup"><span data-stu-id="6d2fd-152">[Understanding the Differences between Local and Remote Execution](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md) </span></span>  
 <span data-ttu-id="6d2fd-153">[以编程方式加载和运行远程包](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md) </span><span class="sxs-lookup"><span data-stu-id="6d2fd-153">[Loading and Running a Remote Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md) </span></span>  
 [<span data-ttu-id="6d2fd-154">加载本地包的输出</span><span class="sxs-lookup"><span data-stu-id="6d2fd-154">Loading the Output of a Local Package</span></span>](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  
