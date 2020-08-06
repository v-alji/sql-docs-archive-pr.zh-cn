---
title: 入门与 CLR 集成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- database objects [CLR integration]
- namespaces [CLR integration]
- database objects [CLR integration], about CLR integration
- stored procedures [CLR integration]
- common language runtime [SQL Server], about CLR integration
- building database objects [CLR integration], about CLR integration
- common language runtime [SQL Server], stored procedures
- common language runtime [SQL Server], namespaces
- Hello World example [CLR integration]
- library [CLR integration]
ms.assetid: c73e628a-f54a-411a-bfe3-6dae519316cc
author: rothja
ms.author: jroth
ms.openlocfilehash: 43c97e411a4d74aa48b88f2edbbe420ae17f3534
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576822"
---
# <a name="getting-started-with-clr-integration"></a><span data-ttu-id="093a0-102">CLR 集成入门</span><span class="sxs-lookup"><span data-stu-id="093a0-102">Getting Started with CLR Integration</span></span>
  <span data-ttu-id="093a0-103">本主题概述了使用 [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] 与 .NET Framework 公共语言运行时 (CLR) 的集成编译数据库对象所需的命名空间和库。</span><span class="sxs-lookup"><span data-stu-id="093a0-103">This topic provides an overview of the namespaces and libraries required to compile database objects using the [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] integration with the .NET Framework common language runtime (CLR).</span></span> <span data-ttu-id="093a0-104">本主题还说明如何编写、编译和运行用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# 编写的简单 CLR 存储过程。</span><span class="sxs-lookup"><span data-stu-id="093a0-104">The topic also shows you how to write, compile, and run a simple CLR stored procedure written in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.</span></span>  
  
## <a name="required-namespaces"></a><span data-ttu-id="093a0-105">所需命名空间</span><span class="sxs-lookup"><span data-stu-id="093a0-105">Required Namespaces</span></span>  
 <span data-ttu-id="093a0-106">从开始 [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="093a0-106">Beginning with [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="093a0-107">CLR 集成功能在称作 system.data.dll 的程序集中公开，该程序集是 .NET Framework 的一部分。</span><span class="sxs-lookup"><span data-stu-id="093a0-107">CLR integration functionality is exposed in an assembly called system.data.dll, which is part of the .NET Framework.</span></span> <span data-ttu-id="093a0-108">该程序集还在全局程序集缓存 (GAC) 以及 .NET Framework 目录中提供。</span><span class="sxs-lookup"><span data-stu-id="093a0-108">This assembly can be found in the Global Assembly Cache (GAC) as well as in the .NET Framework directory.</span></span> <span data-ttu-id="093a0-109">对此程序集的引用通常由命令行工具和 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio 自动添加，因此无需手动添加它。</span><span class="sxs-lookup"><span data-stu-id="093a0-109">A reference to this assembly is typically added automatically by both command line tools and [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio, so there is no need to add it manually.</span></span>  
  
 <span data-ttu-id="093a0-110">system.data.dll 程序集包含以下命名空间，这些命名空间是编译 CLR 数据库对象所必需的：</span><span class="sxs-lookup"><span data-stu-id="093a0-110">The system.data.dll assembly contains the following namespaces, which are required for compiling CLR database objects:</span></span>  
  
 `System.Data`  
  
 `System.Data.Sql`  
  
 `Microsoft.SqlServer.Server`  
  
 `System.Data.SqlTypes`  
  
## <a name="writing-a-simple-hello-world-stored-procedure"></a><span data-ttu-id="093a0-111">撰写一个简单的“Hello World”存储过程</span><span class="sxs-lookup"><span data-stu-id="093a0-111">Writing A Simple "Hello World" Stored Procedure</span></span>  
 <span data-ttu-id="093a0-112">将以下 Visual C# 或 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 代码复制并粘贴到某一文本编辑器中，并且将其保存在名为“helloworld.cs”或“helloworld.vb”的文件中。</span><span class="sxs-lookup"><span data-stu-id="093a0-112">Copy and paste the following Visual C# or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic code into a text editor, and save it in a file named "helloworld.cs" or "helloworld.vb".</span></span>  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlTypes;  
  
public class HelloWorldProc  
{  
    [Microsoft.SqlServer.Server.SqlProcedure]  
    public static void HelloWorld(out string text)  
    {  
        SqlContext.Pipe.Send("Hello world!" + Environment.NewLine);  
        text = "Hello world!";  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlTypes  
Imports System.Runtime.InteropServices  
  
Public Class HelloWorldProc  
    <Microsoft.SqlServer.Server.SqlProcedure> _   
    Public Shared  Sub HelloWorld(<Out()> ByRef text as String)  
        SqlContext.Pipe.Send("Hello world!" & Environment.NewLine)  
        text = "Hello world!"  
    End Sub  
End Class  
  
```  
  
 <span data-ttu-id="093a0-113">这一简单的程序包含针对公共类的单个静态方法。</span><span class="sxs-lookup"><span data-stu-id="093a0-113">This simple program contains a single static method on a public class.</span></span> <span data-ttu-id="093a0-114">此方法使用两个新类 `SqlContext` 和 `SqlPipe`，用于创建托管数据库对象以输出简单的文本消息。</span><span class="sxs-lookup"><span data-stu-id="093a0-114">This method uses two new classes, `SqlContext` and `SqlPipe`, for creating managed database objects to output a simple text message.</span></span> <span data-ttu-id="093a0-115">此方法还将字符串“Hello world!”指派</span><span class="sxs-lookup"><span data-stu-id="093a0-115">The method also assigns the string "Hello world!"</span></span> <span data-ttu-id="093a0-116">为某一输出参数的值。</span><span class="sxs-lookup"><span data-stu-id="093a0-116">as the value of an out parameter.</span></span> <span data-ttu-id="093a0-117">此方法可以声明为存储过程中的存储过程 [!INCLUDE[ssNoVersion](../../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="093a0-117">This method can be declared as a stored procedure in [!INCLUDE[ssNoVersion](../../../includes/tsql-md.md)] stored procedure.</span></span>  
  
 <span data-ttu-id="093a0-118">我们现在将此程序编译为一个库，将其加载到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，然后将其作为存储过程运行。</span><span class="sxs-lookup"><span data-stu-id="093a0-118">We will now compile this program as a library, load it into [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], and run it as a stored procedure.</span></span>  
  
## <a name="compiling-the-hello-world-stored-procedure"></a><span data-ttu-id="093a0-119">编译“Hello World”存储过程</span><span class="sxs-lookup"><span data-stu-id="093a0-119">Compiling the "Hello World" Stored Procedure</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/msconame-md.md)]<span data-ttu-id="093a0-120">默认情况下，.NET Framework 再分发文件。</span><span class="sxs-lookup"><span data-stu-id="093a0-120">.NET Framework redistribution files by default.</span></span> <span data-ttu-id="093a0-121">这些文件包括 csc.exe 和 vbc.exe，它们是用于 Visual C# 和 Visual Basic 程序的命令行编译器。</span><span class="sxs-lookup"><span data-stu-id="093a0-121">These files include csc.exe and vbc.exe, the command-line compilers for Visual C# and Visual Basic programs.</span></span> <span data-ttu-id="093a0-122">为了编译我们的示例，您必须修改路径变量以指向包含 csc.exe 或 vbc.exe 的目录。</span><span class="sxs-lookup"><span data-stu-id="093a0-122">In order to compile our sample, you must modify your path variable to point to the directory containing csc.exe or vbc.exe.</span></span> <span data-ttu-id="093a0-123">下面是 .NET Framework 的默认安装路径。</span><span class="sxs-lookup"><span data-stu-id="093a0-123">The following is the default installation path of the .NET Framework.</span></span>  
  
```  
C:\Windows\Microsoft.NET\Framework\(version)  
```  
  
 <span data-ttu-id="093a0-124">Version 包含已安装 .NET Framework 可再发行组件的版本号。</span><span class="sxs-lookup"><span data-stu-id="093a0-124">Version contains the version number of the installed .NET Framework redistributable.</span></span> <span data-ttu-id="093a0-125">例如：</span><span class="sxs-lookup"><span data-stu-id="093a0-125">For example:</span></span>  
  
```  
C:\Windows\Microsoft.NET\Framework\v2.0.31113  
```  
  
 <span data-ttu-id="093a0-126">一旦将 .NET Framework 目录添加到路径后，您可以使用以下命令将该存储过程示例编译到某一程序集中。</span><span class="sxs-lookup"><span data-stu-id="093a0-126">Once you have added the .NET Framework directory to your path, you can compile the sample stored procedure into an assembly with the following command.</span></span> <span data-ttu-id="093a0-127">`/target` 选项可用于将其编译到某一程序集中。</span><span class="sxs-lookup"><span data-stu-id="093a0-127">The `/target` option allows you to compile it into an assembly.</span></span>  
  
 <span data-ttu-id="093a0-128">对于 Visual C# 源文件：</span><span class="sxs-lookup"><span data-stu-id="093a0-128">For Visual C# source files:</span></span>  
  
```  
csc /target:library helloworld.cs   
```  
  
 <span data-ttu-id="093a0-129">对于 Visual Basic 源文件：</span><span class="sxs-lookup"><span data-stu-id="093a0-129">For Visual Basic source files:</span></span>  
  
```  
vbc /target:library helloworld.vb  
```  
  
 <span data-ttu-id="093a0-130">以上命令使用 /target 选项启动 Visual C# 或 Visual Basic 编译器，以指定生成库 DLL。</span><span class="sxs-lookup"><span data-stu-id="093a0-130">These commands launch the Visual C# or Visual Basic compiler using the /target option to specify building a library DLL.</span></span>  
  
## <a name="loading-and-running-the-hello-world-stored-procedure-in-sql-server"></a><span data-ttu-id="093a0-131">在 SQL Server 中加载并运行“Hello World”存储过程</span><span class="sxs-lookup"><span data-stu-id="093a0-131">Loading and Running the "Hello World" Stored Procedure in SQL Server</span></span>  
 <span data-ttu-id="093a0-132">成功编译该示例过程后，可以在中对其进行测试， [!INCLUDE[ssNoVersion](../../../includes/ssmanstudiofull-md.md)] 并创建新的查询，连接到合适的测试数据库 (例如，AdventureWorks 示例数据库) 。</span><span class="sxs-lookup"><span data-stu-id="093a0-132">Once the sample procedure has successfully compiled, you can test it in [!INCLUDE[ssNoVersion](../../../includes/ssmanstudiofull-md.md)] and create a new query, connecting to a suitable test database (for example, the AdventureWorks sample database).</span></span>  
  
 <span data-ttu-id="093a0-133">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，能否执行公共语言运行时 (CLR) 代码默认设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="093a0-133">The ability to execute common language runtime (CLR) code is set to OFF by default in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="093a0-134">可以通过使用**sp_configure**系统存储过程来启用 CLR 代码。</span><span class="sxs-lookup"><span data-stu-id="093a0-134">The CLR code can be enabled by using the **sp_configure** system stored procedure.</span></span> <span data-ttu-id="093a0-135">有关详细信息，请参阅 [Enabling CLR Integration](../clr-integration-enabling.md)。</span><span class="sxs-lookup"><span data-stu-id="093a0-135">For more information, see [Enabling CLR Integration](../clr-integration-enabling.md).</span></span>  
  
 <span data-ttu-id="093a0-136">我们将需要创建该程序集，以便可以访问该存储过程。</span><span class="sxs-lookup"><span data-stu-id="093a0-136">We will need to create the assembly so we can access the stored procedure.</span></span> <span data-ttu-id="093a0-137">对于此示例，我们将假定您已在 C:\ 目录中创建了 helloworld.dll 程序集。</span><span class="sxs-lookup"><span data-stu-id="093a0-137">For this example, we will assume that you have created the helloworld.dll assembly in the C:\ directory.</span></span> <span data-ttu-id="093a0-138">将以下 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句添加到您的查询中。</span><span class="sxs-lookup"><span data-stu-id="093a0-138">Add the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement to your query.</span></span>  
  
```  
CREATE ASSEMBLY helloworld from 'c:\helloworld.dll' WITH PERMISSION_SET = SAFE  
```  
  
 <span data-ttu-id="093a0-139">一旦创建了该程序集后，我们现在就可以通过使用 create procedure 语句访问 HelloWorld 方法。</span><span class="sxs-lookup"><span data-stu-id="093a0-139">Once the assembly has been created, we can now access our HelloWorld method by using the create procedure statement.</span></span> <span data-ttu-id="093a0-140">我们将存储过程称为“hello”：</span><span class="sxs-lookup"><span data-stu-id="093a0-140">We will call our stored procedure "hello":</span></span>  
  
```  
  
CREATE PROCEDURE hello  
@i nchar(25) OUTPUT  
AS  
EXTERNAL NAME helloworld.HelloWorldProc.HelloWorld  
-- if the HelloWorldProc class is inside a namespace (called MyNS),  
-- the last line in the create procedure statement would be  
-- EXTERNAL NAME helloworld.[MyNS.HelloWorldProc].HelloWorld  
```  
  
 <span data-ttu-id="093a0-141">一旦创建该存储过程后，就可以像用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 编写的普通存储过程一样运行该存储过程。</span><span class="sxs-lookup"><span data-stu-id="093a0-141">Once the procedure has been created, it can be run just like a normal stored procedure written in [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="093a0-142">请执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="093a0-142">Execute the following command:</span></span>  
  
```  
DECLARE @J nchar(25)  
EXEC hello @J out  
PRINT @J  
```  
  
 <span data-ttu-id="093a0-143">这将在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 消息窗口中导致以下输出。</span><span class="sxs-lookup"><span data-stu-id="093a0-143">This should result in the following output in the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] messages window.</span></span>  
  
```  
Hello world!  
Hello world!  
```  
  
## <a name="removing-the-hello-world-stored-procedure-sample"></a><span data-ttu-id="093a0-144">删除“Hello World”存储过程示例</span><span class="sxs-lookup"><span data-stu-id="093a0-144">Removing the "Hello World" Stored Procedure Sample</span></span>  
 <span data-ttu-id="093a0-145">在您完成该存储过程示例的运行后，可以从测试数据库中删除该过程和程序集。</span><span class="sxs-lookup"><span data-stu-id="093a0-145">When you are finished running the sample stored procedure, you can remove the procedure and the assembly from your test database.</span></span>  
  
 <span data-ttu-id="093a0-146">首先，使用 drop procedure 命令删除该存储过程。</span><span class="sxs-lookup"><span data-stu-id="093a0-146">First, remove the procedure using the drop procedure command.</span></span>  
  
```  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'hello')  
   drop procedure hello  
```  
  
 <span data-ttu-id="093a0-147">一旦该存储过程删除后，就可以删除包含示例代码的程序集。</span><span class="sxs-lookup"><span data-stu-id="093a0-147">Once the procedure has been dropped, you can remove the assembly containing your sample code.</span></span>  
  
```  
IF EXISTS (SELECT name FROM sys.assemblies WHERE name = 'helloworld')  
   drop assembly helloworld  
```  
  
## <a name="see-also"></a><span data-ttu-id="093a0-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="093a0-148">See Also</span></span>  
 <span data-ttu-id="093a0-149">[CLR 存储过程](../../../database-engine/dev-guide/clr-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="093a0-149">[CLR Stored Procedures](../../../database-engine/dev-guide/clr-stored-procedures.md) </span></span>  
 <span data-ttu-id="093a0-150">[SQL Server ADO.NET 中特定于进程的扩展](../../clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md) </span><span class="sxs-lookup"><span data-stu-id="093a0-150">[SQL Server In-Process Specific Extensions to ADO.NET](../../clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md) </span></span>  
 <span data-ttu-id="093a0-151">[调试 CLR 数据库对象](../debugging-clr-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="093a0-151">[Debugging CLR Database Objects](../debugging-clr-database-objects.md) </span></span>  
 [<span data-ttu-id="093a0-152">CLR 集成安全性</span><span class="sxs-lookup"><span data-stu-id="093a0-152">CLR Integration Security</span></span>](../security/clr-integration-security.md)  
  
  
