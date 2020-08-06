---
title: 调试 CLR 数据库对象 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- database objects [CLR integration], debugging
- permissions [CLR integration]
- debugging [CLR integration]
- building database objects [CLR integration], debugging
- common language runtime [SQL Server], debugging
ms.assetid: 1332035c-d6ed-424d-8234-46ad21168319
author: rothja
ms.author: jroth
ms.openlocfilehash: 084b2494ec55b502f71154ca1f174a6de6d2ab70
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576821"
---
# <a name="debugging-clr-database-objects"></a><span data-ttu-id="a7805-102">调试 CLR 数据库对象</span><span class="sxs-lookup"><span data-stu-id="a7805-102">Debugging CLR Database Objects</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="a7805-103">为调试 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 和数据库中的公共语言运行时 (CLR) 对象提供支持。</span><span class="sxs-lookup"><span data-stu-id="a7805-103">provides support for debugging [!INCLUDE[tsql](../../../includes/tsql-md.md)] and common language runtime (CLR) objects in the database.</span></span> <span data-ttu-id="a7805-104">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中进行调试的主要特点一个是易于设置和使用，另一个是 SQL Server 调试器与 Microsoft Visual Studio 调试器集成。</span><span class="sxs-lookup"><span data-stu-id="a7805-104">The key aspects of debugging in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] are the ease of setup and use, and the integration of the SQL Server debugger with the Microsoft Visual Studio debugger.</span></span> <span data-ttu-id="a7805-105">此外，还可以跨语言进行调试。</span><span class="sxs-lookup"><span data-stu-id="a7805-105">Furthermore, debugging works across languages.</span></span> <span data-ttu-id="a7805-106">用户可以在 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 中无缝地单步执行 CLR 对象，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="a7805-106">Users can step seamlessly into CLR objects from [!INCLUDE[tsql](../../../includes/tsql-md.md)], and vice versa.</span></span> <span data-ttu-id="a7805-107">SQL Server Management Studio 中的 Transact-SQL 调试器无法用于调试托管数据库对象，但您可以通过使用 Visual Studio 中的调试器来调试这些对象。</span><span class="sxs-lookup"><span data-stu-id="a7805-107">The Transact-SQL debugger in SQL Server Management Studio cannot be used to debug managed database objects, but you can debug the objects by using the debuggers in Visual Studio.</span></span> <span data-ttu-id="a7805-108">Visual Studio 中的托管数据库对象调试支持所有常见的调试功能，例如，在服务器上执行的例程中的“单步执行”语句和“逐过程”语句。</span><span class="sxs-lookup"><span data-stu-id="a7805-108">Managed database object debugging in Visual Studio supports all common debugging features, such as "step into" and "step over" statements within routines executing on the server.</span></span> <span data-ttu-id="a7805-109">调试器可以在调试过程中设置断点、检查调用堆栈、检查变量以及修改变量值。</span><span class="sxs-lookup"><span data-stu-id="a7805-109">Debuggers can set breakpoints, inspect the call stack, inspect variables, and modify variable values while debugging.</span></span> <span data-ttu-id="a7805-110">请注意，Visual Studio .NET 2003 无法用于 CLR 集成编程或调试。</span><span class="sxs-lookup"><span data-stu-id="a7805-110">Note that Visual Studio .NET 2003 cannot be used for CLR integration programming or debugging.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="a7805-111">包含预先安装的 .NET Framework，而 Visual Studio .NET 2003 无法使用 .NET Framework 2.0 程序集。</span><span class="sxs-lookup"><span data-stu-id="a7805-111">includes the .NET Framework pre-installed, and Visual Studio .NET 2003 cannot use the .NET Framework 2.0 assemblies.</span></span>  
  
 <span data-ttu-id="a7805-112">有关使用 Visual Studio 调试托管代码的详细信息，请参阅 Visual Studio 文档中的 "[调试托管代码](https://go.microsoft.com/fwlink/?LinkId=120377)" 主题。</span><span class="sxs-lookup"><span data-stu-id="a7805-112">For more information about debugging managed code using Visual Studio, see the "[Debugging Managed Code](https://go.microsoft.com/fwlink/?LinkId=120377)" topic in the Visual Studio documentation.</span></span>  
  
## <a name="debugging-permissions-and-restrictions"></a><span data-ttu-id="a7805-113">调试权限和限制</span><span class="sxs-lookup"><span data-stu-id="a7805-113">Debugging Permissions and Restrictions</span></span>  
 <span data-ttu-id="a7805-114">调试是一项高度特权的操作，因此只有**sysadmin**固定服务器角色的成员才可以在中执行此操作 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a7805-114">Debugging is a highly privileged operation, and therefore only members of the **sysadmin** fixed server role are allowed to do so in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="a7805-115">调试时存在下列限制：</span><span class="sxs-lookup"><span data-stu-id="a7805-115">The following restrictions apply while debugging:</span></span>  
  
-   <span data-ttu-id="a7805-116">调试 CLR 例程时仅限一次运行一个调试器实例。</span><span class="sxs-lookup"><span data-stu-id="a7805-116">Debugging CLR routines is restricted to one debugger instance at a time.</span></span> <span data-ttu-id="a7805-117">存在此限制的原因是，所有 CLR 代码执行在命中断点时都会冻结，并且执行在调试器从断点继续运行之前不会继续。</span><span class="sxs-lookup"><span data-stu-id="a7805-117">This limitation applies because all CLR code execution freezes when a break point is hit and execution does not continue until the debugger advances from the break point.</span></span> <span data-ttu-id="a7805-118">但是，您可以在其他连接中继续调试 [!INCLUDE[tsql](../../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a7805-118">However, you can continue debugging [!INCLUDE[tsql](../../../includes/tsql-md.md)] in other connections.</span></span> <span data-ttu-id="a7805-119">尽管 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 调试不会冻结服务器上的其他执行，但它会因持有锁而导致其他连接等待。</span><span class="sxs-lookup"><span data-stu-id="a7805-119">Although [!INCLUDE[tsql](../../../includes/tsql-md.md)] debugging does not freeze other executions on the server, it could cause other connections to wait by holding a lock.</span></span>  
  
-   <span data-ttu-id="a7805-120">无法调试现有连接，只能调试新连接，因为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 在建立连接之前需要客户端和调试器环境的相关信息。</span><span class="sxs-lookup"><span data-stu-id="a7805-120">Existing connections cannot be debugged, only new connections, as [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] requires information about the client and debugger environment before the connection can be made.</span></span>  
  
 <span data-ttu-id="a7805-121">由于存在上述限制，建议在测试服务器上而不是在生产服务器上调试 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 和 CLR 代码。</span><span class="sxs-lookup"><span data-stu-id="a7805-121">Due to the above restrictions, we recommend that [!INCLUDE[tsql](../../../includes/tsql-md.md)] and CLR code be debugged on a test server, and not on a production server.</span></span>  
  
## <a name="overview-of-debugging-managed-database-objects"></a><span data-ttu-id="a7805-122">关于调试托管数据库对象的概述</span><span class="sxs-lookup"><span data-stu-id="a7805-122">Overview of Debugging Managed Database Objects</span></span>  
 <span data-ttu-id="a7805-123">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中进行的调试遵循单连接模式。</span><span class="sxs-lookup"><span data-stu-id="a7805-123">Debugging in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] follows a per-connection model.</span></span> <span data-ttu-id="a7805-124">一个调试器只能检测和调试其附加到的客户端连接的活动。</span><span class="sxs-lookup"><span data-stu-id="a7805-124">A debugger can detect and debug activities only to the client connection to which it is attached.</span></span> <span data-ttu-id="a7805-125">由于调试器的功能不受连接类型的限制，因此表格格式数据流 (TDS) 和 HTTP 连接都可以进行调试。</span><span class="sxs-lookup"><span data-stu-id="a7805-125">Because the functionality of the debugger is not limited by the type of connection, both tabular data stream (TDS) and HTTP connections can be debugged.</span></span> <span data-ttu-id="a7805-126">不过，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 不允许调试现有连接。</span><span class="sxs-lookup"><span data-stu-id="a7805-126">However, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not allow debugging existing connections.</span></span> <span data-ttu-id="a7805-127">调试支持在服务器上执行的例程中使用所有常见的调试功能。</span><span class="sxs-lookup"><span data-stu-id="a7805-127">Debugging supports all common debugging features within routines executing on the server.</span></span> <span data-ttu-id="a7805-128">调试器与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 之间的交互通过分布式组件对象模型 (COM) 进行。</span><span class="sxs-lookup"><span data-stu-id="a7805-128">The interaction between a debugger and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] happens through distributed Component Object Model (COM).</span></span>  
  
 <span data-ttu-id="a7805-129">有关调试托管存储过程、函数、触发器、用户定义类型和聚合的详细信息和方案，请参阅 Visual Studio 文档中的 "[SQL SERVER CLR 集成数据库调试](https://go.microsoft.com/fwlink/?LinkId=120378)" 主题。</span><span class="sxs-lookup"><span data-stu-id="a7805-129">For more information and scenarios about debugging managed stored procedures, functions, triggers, user-defined types, and aggregates, see the "[SQL Server CLR Integration Database Debugging](https://go.microsoft.com/fwlink/?LinkId=120378)" topic in the Visual Studio documentation.</span></span>  
  
 <span data-ttu-id="a7805-130">必须对 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例启用 TCP/IP 网络协议，才能使用 Visual Studio 进行远程开发、调试和开发。</span><span class="sxs-lookup"><span data-stu-id="a7805-130">The TCP/IP network protocol must be enabled on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance in order to use Visual Studio for remote development, debugging, and development.</span></span> <span data-ttu-id="a7805-131">有关在服务器上启用 TCP/IP 协议的详细信息，请参阅[配置客户端协议](../../database-engine/configure-windows/configure-client-protocols.md)。</span><span class="sxs-lookup"><span data-stu-id="a7805-131">For more information about enabling TCP/IP protocol on the server, see [Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md).</span></span>  
  
#### <a name="to-debug-a-managed-database-object"></a><span data-ttu-id="a7805-132">调试托管数据库对象</span><span class="sxs-lookup"><span data-stu-id="a7805-132">To debug a managed database object</span></span>  
  
1.  <span data-ttu-id="a7805-133">打开 Microsoft Visual Studio，创建一个新的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 项目，并与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例上的数据库建立连接。</span><span class="sxs-lookup"><span data-stu-id="a7805-133">Open Microsoft Visual Studio, create a new [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] project, and establish a connection to a database on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="a7805-134">创建一种新类型。</span><span class="sxs-lookup"><span data-stu-id="a7805-134">Create a new type.</span></span> <span data-ttu-id="a7805-135">在**解决方案资源管理器**中，右键单击项目，选择 "**添加**" 和 "**新建项 ...** "从 "**添加新项**" 窗口中，选择**存储过程**、**用户定义函数**、**用户定义类型**、**触发器**、**聚合**或**类**。</span><span class="sxs-lookup"><span data-stu-id="a7805-135">In **Solution Explorer**, right-click the project, select **Add** and **New Item...** From the **Add New Item** window, select **Stored Procedure**, **User-Defined Function**, **User-Defined Type**, **Trigger**, **Aggregate**, or **Class**.</span></span> <span data-ttu-id="a7805-136">指定新类型的源文件的名称，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="a7805-136">Specify a name for the source file of the new type and click **Add**.</span></span>  
  
3.  <span data-ttu-id="a7805-137">将此新类型的代码添加到文本编辑器中。</span><span class="sxs-lookup"><span data-stu-id="a7805-137">Add code for the new type to the text editor.</span></span> <span data-ttu-id="a7805-138">有关示例存储过程的示例代码，请参阅本主题后面的部分。</span><span class="sxs-lookup"><span data-stu-id="a7805-138">For sample code for an example stored procedure, see the section later in this topic.</span></span>  
  
4.  <span data-ttu-id="a7805-139">添加测试该类型的脚本。</span><span class="sxs-lookup"><span data-stu-id="a7805-139">Add a script that tests the type.</span></span> <span data-ttu-id="a7805-140">在**解决方案资源管理器**中，展开**TestScripts**目录双击 "test.txt **" 以打开默认的测试脚本**源文件。</span><span class="sxs-lookup"><span data-stu-id="a7805-140">In **Solution Explorer**, expand the **TestScripts** directory double-click **Test.sql** to open the default test script source file.</span></span> <span data-ttu-id="a7805-141">将调用要调试的代码的测试脚本添加到文本编辑器中。</span><span class="sxs-lookup"><span data-stu-id="a7805-141">Add the test script, one that invokes the code to be debugged, to the text editor.</span></span> <span data-ttu-id="a7805-142">示例脚本见下文。</span><span class="sxs-lookup"><span data-stu-id="a7805-142">See below for a sample script.</span></span>  
  
5.  <span data-ttu-id="a7805-143">将一个或多个断点放在源代码中。</span><span class="sxs-lookup"><span data-stu-id="a7805-143">Place one or more breakpoints in the source code.</span></span> <span data-ttu-id="a7805-144">在文本编辑器中，右键单击要调试的函数或例程内的代码行，然后选择 "**断点**" 和 "**插入断点**"。</span><span class="sxs-lookup"><span data-stu-id="a7805-144">Right-click on a line of code in the text editor, within the function or routine you want to debug, and select **Breakpoint** and **Insert Breakpoint**.</span></span> <span data-ttu-id="a7805-145">即会添加断点，并以红色突出显示该行代码。</span><span class="sxs-lookup"><span data-stu-id="a7805-145">The breakpoint is added, highlighting the line of code in red.</span></span>  
  
6.  <span data-ttu-id="a7805-146">在 "**调试**" 菜单中，选择 "**启动调试**" 以编译、部署和测试项目。</span><span class="sxs-lookup"><span data-stu-id="a7805-146">In the **Debug** menu, select **Start Debugging** to compile, deploy, and test the project.</span></span> <span data-ttu-id="a7805-147">将运行 Test.sql 中的测试脚本，并将调用托管数据库对象。</span><span class="sxs-lookup"><span data-stu-id="a7805-147">The test script in Test.sql will be run and the managed database object will be invoked.</span></span>  
  
7.  <span data-ttu-id="a7805-148">如果在断点代码执行暂停时出现表示指令指针的黄色箭头，则您可以开始调试托管数据库对象。</span><span class="sxs-lookup"><span data-stu-id="a7805-148">When the yellow arrow designating the instruction pointer appears at the breakpoint code execution pauses and you can begin debugging your managed database object.</span></span> <span data-ttu-id="a7805-149">可以从 "**调试**" 菜单**单步执行**，将指令指针前进到下一行代码。</span><span class="sxs-lookup"><span data-stu-id="a7805-149">You can **Step Over** from the **Debug** menu to advance the instruction pointer to the next line of code.</span></span> <span data-ttu-id="a7805-150">"**局部变量**" 窗口用于观察当前由指令指针突出显示的对象的状态。</span><span class="sxs-lookup"><span data-stu-id="a7805-150">The **Locals** window is used to observe the state of the objects currently highlighted by the instruction pointer.</span></span> <span data-ttu-id="a7805-151">可以将变量添加到 "**监视**" 窗口。</span><span class="sxs-lookup"><span data-stu-id="a7805-151">Variables can be added to the **Watch** window.</span></span> <span data-ttu-id="a7805-152">受监视变量的状态在整个调试会话过程中都可以进行观察，而不是仅当变量位于当前由指令指针突出显示的代码行中时才可以进行观察。</span><span class="sxs-lookup"><span data-stu-id="a7805-152">The state of watched variables can be observed throughout the entire debugging session, not only when the variable is in the line of code currently highlighted by instruction pointer.</span></span> <span data-ttu-id="a7805-153">从“调试”菜单中选择“继续”以使指令指针前进到下一个断点或完成例程的执行（如果不再有其他断点）。</span><span class="sxs-lookup"><span data-stu-id="a7805-153">Select Continue from the Debug menu to advance the instruction pointer to the next breakpoint or to complete execution of the routine if there are no more breakpoints.</span></span>  
  
### <a name="example"></a><span data-ttu-id="a7805-154">示例</span><span class="sxs-lookup"><span data-stu-id="a7805-154">Example</span></span>  
 <span data-ttu-id="a7805-155">下面的示例将 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本返回给调用方。</span><span class="sxs-lookup"><span data-stu-id="a7805-155">The following example returns the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] version to the caller.</span></span>  
  
 <span data-ttu-id="a7805-156">C#</span><span class="sxs-lookup"><span data-stu-id="a7805-156">C#</span></span>  
  
```  
using System;  
using System.Data;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void GetVersion()  
   {  
   using(SqlConnection connection = new SqlConnection("context connection=true"))   
   {  
      connection.Open();  
      SqlCommand command = new SqlCommand("select @@version",  
                                           connection);  
      SqlContext.Pipe.ExecuteAndSend(command);  
      }  
   }  
}  
```  
  
 <span data-ttu-id="a7805-157">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a7805-157">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
Partial Public Class StoredProcedures   
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub GetVersion()  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT @@VERSION", connection)  
            SqlContext.Pipe.ExecuteAndSend(command)  
        End Using  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="a7805-158">下面是调用上面定义的 GetVersion 存储过程的测试脚本。</span><span class="sxs-lookup"><span data-stu-id="a7805-158">The following is a test script that invokes the GetVersion stored procedure defined above.</span></span>  
  
```  
EXEC GetVersion  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7805-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a7805-159">See Also</span></span>  
 [<span data-ttu-id="a7805-160">公共语言运行时 (CLR) 集成编程概念</span><span class="sxs-lookup"><span data-stu-id="a7805-160">Common Language Runtime &#40;CLR&#41; Integration Programming Concepts</span></span>](common-language-runtime-clr-integration-programming-concepts.md)  
  
  
