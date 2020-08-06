---
title: 以编程方式创建包 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SSIS packages, creating
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
ms.assetid: e44bcc70-32d3-43e8-a84b-29aef819d5d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1159784fc95dd86d9d33c4354291cc7c52812982
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689561"
---
# <a name="creating-a-package-programmatically"></a><span data-ttu-id="cad33-102">以编程方式创建包</span><span class="sxs-lookup"><span data-stu-id="cad33-102">Creating a Package Programmatically</span></span>
  <span data-ttu-id="cad33-103"><xref:Microsoft.SqlServer.Dts.Runtime.Package> 对象是 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 项目解决方案中的所有其他对象的顶级容器。</span><span class="sxs-lookup"><span data-stu-id="cad33-103">The <xref:Microsoft.SqlServer.Dts.Runtime.Package> object is the top-level container for all other objects in an [!INCLUDE[ssIS](../../includes/ssis-md.md)] project solution.</span></span> <span data-ttu-id="cad33-104">作为顶级容器，包是第一个创建的对象，并将后续对象添加到该包，然后在包的上下文中执行这些对象。</span><span class="sxs-lookup"><span data-stu-id="cad33-104">As the top-level container, the package is the first object created, and subsequent objects are added to it, and then executed within the context of the package.</span></span> <span data-ttu-id="cad33-105">包本身并不移动或转换数据。</span><span class="sxs-lookup"><span data-stu-id="cad33-105">The package itself does not move or transform data.</span></span> <span data-ttu-id="cad33-106">包依靠自己包含的任务执行工作。</span><span class="sxs-lookup"><span data-stu-id="cad33-106">The package relies on the tasks it contains to perform the work.</span></span> <span data-ttu-id="cad33-107">任务执行大多数由包执行的工作，并定义包的功能。</span><span class="sxs-lookup"><span data-stu-id="cad33-107">Tasks perform most of the work performed by a package, and define the functionality of a package.</span></span> <span data-ttu-id="cad33-108">只需三行代码即可完成包的创建和执行，但需要向包中添加各种任务和 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 对象以增加其功能。</span><span class="sxs-lookup"><span data-stu-id="cad33-108">A package is created and executed with just three lines of code, but various tasks and <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> objects are added to give additional functionality to your package.</span></span> <span data-ttu-id="cad33-109">本节讨论如何以编程方式创建包。</span><span class="sxs-lookup"><span data-stu-id="cad33-109">This section discusses how to programmatically create a package.</span></span> <span data-ttu-id="cad33-110">不提供有关如何创建任务或 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 的信息。</span><span class="sxs-lookup"><span data-stu-id="cad33-110">It does not provide information about how to create the tasks or the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>.</span></span> <span data-ttu-id="cad33-111">有关信息，请参阅后续相关章节。</span><span class="sxs-lookup"><span data-stu-id="cad33-111">These are covered in later sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cad33-112">示例</span><span class="sxs-lookup"><span data-stu-id="cad33-112">Example</span></span>  
 <span data-ttu-id="cad33-113">若要使用 Visual Studio IDE 编写代码，需要对 Microsoft.SqlServer.ManagedDTS.DLL 的引用，以便创建针对 Microsoft.SqlServer.Dts.Runtime 的 `using` 语句（在 Visual Basic .NET 中为 `Imports`）。</span><span class="sxs-lookup"><span data-stu-id="cad33-113">To write code using the Visual Studio IDE, a reference to Microsoft.SqlServer.ManagedDTS.DLL is required in order to create a `using` statement (`Imports` in Visual Basic .NET) to the Microsoft.SqlServer.Dts.Runtime.</span></span> <span data-ttu-id="cad33-114">下面的代码示例演示如何创建一个空包。</span><span class="sxs-lookup"><span data-stu-id="cad33-114">The following code sample demonstrates creating an empty package.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package package;  
      package = new Package();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Package  
    package = New Package  
  
  End Sub  
  
End Module  
```  
  
 <span data-ttu-id="cad33-115">若要编译并运行该示例，请在 Visual Studio 中按 F5。</span><span class="sxs-lookup"><span data-stu-id="cad33-115">To compile and run the sample, press F5 in Visual Studio.</span></span> <span data-ttu-id="cad33-116">若要使用 C# 编译器 csc.exe 生成代码，并在命令提示符处进行编译，请使用下面的命令和文件引用将 \<filename> 替换为 .cs 或 .vb 文件的名称，并选择 \<outputfilename> 。</span><span class="sxs-lookup"><span data-stu-id="cad33-116">To build the code using the C# compiler, **csc.exe**, at the command prompt to compile, use the following command and file references, replacing the *\<filename>* with the name of the .cs or .vb file, and giving it an *\<outputfilename>* of your choice.</span></span>  
  
 <span data-ttu-id="cad33-117">csc /target:library /out: \<outputfilename>.dll \<filename>.cs /r:Microsoft.SqlServer.Managed DTS.dll" /r:System.dll</span><span class="sxs-lookup"><span data-stu-id="cad33-117">**csc /target:library /out: \<outputfilename>.dll \<filename>.cs /r:Microsoft.SqlServer.Managed DTS.dll" /r:System.dll**</span></span>  
  
 <span data-ttu-id="cad33-118">若要使用 Visual Basic .NET 编译器 (vbc.exe) 生成代码，并在命令提示符处进行编译，请使用下面的命令和文件引用  。</span><span class="sxs-lookup"><span data-stu-id="cad33-118">To build the code using the Visual Basic .NET compiler, **vbc.exe**, at the command prompt to compile, use the following command and file references.</span></span>  
  
 <span data-ttu-id="cad33-119">vbc /target:library /out: \<outputfilename>.dll \<filename>.vb /r:Microsoft.SqlServer.Managed DTS.dll" /r:System.dll</span><span class="sxs-lookup"><span data-stu-id="cad33-119">**vbc /target:library /out: \<outputfilename>.dll \<filename>.vb /r:Microsoft.SqlServer.Managed DTS.dll" /r:System.dll**</span></span>  
  
 <span data-ttu-id="cad33-120">还可以通过将存储在磁盘中的现有包加载到文件系统或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中来创建包。</span><span class="sxs-lookup"><span data-stu-id="cad33-120">You can also create a package by loading an existing package that was saved on disk, in the file system, or to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="cad33-121">区别是要先创建 <xref:Microsoft.SqlServer.Dts.Runtime.Application>，然后由任一应用程序已重载方法填充包对象：`LoadPackage` 用于平面文件，`LoadFromSQLServer` 用于保存到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的包，<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A> 用于保存到文件系统的包。</span><span class="sxs-lookup"><span data-stu-id="cad33-121">The difference is that the <xref:Microsoft.SqlServer.Dts.Runtime.Application> object is first created, and then the package object is filled by one of the Application's overloaded methods: `LoadPackage` for flat files, `LoadFromSQLServer` for packages saved to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A> for packages saved to the file system.</span></span> <span data-ttu-id="cad33-122">下面的示例从磁盘加载一个现有包，然后查看该包的多个属性。</span><span class="sxs-lookup"><span data-stu-id="cad33-122">The following example loads an existing package from disk, and then views several properties on the package.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class ApplicationTests  
  {  
    static void Main(string[] args)  
    {  
      // The variable pkg points to the location of the  
      // ExecuteProcess package sample that was installed with  
      // the SSIS samples.  
      string pkg = @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\ExecuteProcess Sample\ExecuteProcess\UsingExecuteProcess.dtsx";  
  
      Application app = new Application();  
      Package p = app.LoadPackage(pkg, null);  
  
      // Now that the package is loaded, we can query on  
      // its properties.  
      int n = p.Configurations.Count;  
      DtsProperty p2 = p.Properties["VersionGUID"];  
      DTSProtectionLevel pl = p.ProtectionLevel;  
  
      Console.WriteLine("Number of configurations = " + n.ToString());  
      Console.WriteLine("VersionGUID = " + (string)p2.GetValue(p));  
      Console.WriteLine("ProtectionLevel = " + pl.ToString());  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module ApplicationTests  
  
  Sub Main()  
  
    ' The variable pkg points to the location of the  
    ' ExecuteProcess package sample that was installed with  
    ' the SSIS samples.  
    Dim pkg As String = _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\ExecuteProcess Sample\ExecuteProcess\UsingExecuteProcess.dtsx"  
  
    Dim app As Application = New Application()  
    Dim p As Package = app.LoadPackage(pkg, Nothing)  
  
    ' Now that the package is loaded, we can query on  
    ' its properties.  
    Dim n As Integer = p.Configurations.Count  
    Dim p2 As DtsProperty = p.Properties("VersionGUID")  
    Dim pl As DTSProtectionLevel = p.ProtectionLevel  
  
    Console.WriteLine("Number of configurations = " & n.ToString())  
    Console.WriteLine("VersionGUID = " & CType(p2.GetValue(p), String))  
    Console.WriteLine("ProtectionLevel = " & pl.ToString())  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
 <span data-ttu-id="cad33-123">**示例输出：**</span><span class="sxs-lookup"><span data-stu-id="cad33-123">**Sample Output:**</span></span>  
  
 `Number of configurations = 2`  
  
 `VersionGUID = {09016682-89B8-4406-AAC9-AF1E527FF50F}`  
  
 `ProtectionLevel = DontSaveSensitive`  
  
## <a name="external-resources"></a><span data-ttu-id="cad33-124">外部资源</span><span class="sxs-lookup"><span data-stu-id="cad33-124">External Resources</span></span>  
  
-   <span data-ttu-id="cad33-125">blogs.msdn.com 上的博客文章 [API Sample - OleDB source and OleDB destination](https://go.microsoft.com/fwlink/?LinkId=220824)（API 示例 - OleDB 源和 OleDB 目标）。</span><span class="sxs-lookup"><span data-stu-id="cad33-125">Blog entry, [API Sample - OleDB source and OleDB destination](https://go.microsoft.com/fwlink/?LinkId=220824), on blogs.msdn.com.</span></span>  
  
-   <span data-ttu-id="cad33-126">blogs.msdn.com 上的博客文章 [EzAPI - 为 SQL Server 2012 更新](https://go.microsoft.com/fwlink/?LinkId=243223)。</span><span class="sxs-lookup"><span data-stu-id="cad33-126">Blog entry, [EzAPI - Updated for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223), on blogs.msdn.com.</span></span>  
  
<span data-ttu-id="cad33-127">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="cad33-127">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="cad33-128">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="cad33-128">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="cad33-129">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="cad33-129">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="cad33-130">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="cad33-130">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cad33-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cad33-131">See Also</span></span>  
 [<span data-ttu-id="cad33-132">以编程方式添加任务</span><span class="sxs-lookup"><span data-stu-id="cad33-132">Adding Tasks Programmatically</span></span>](../building-packages-programmatically/adding-tasks-programmatically.md)  
  
  
