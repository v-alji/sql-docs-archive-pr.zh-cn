---
title: 连接到 SQL Server 的实例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, connections
- connections [SMO]
- instances of SQL Server, connections
- SMO [SQL Server], connections
ms.assetid: ad3cf354-b2e3-468b-b986-1232e375fd84
author: stevestein
ms.author: sstein
ms.openlocfilehash: efc21451f4a876c6edfe4a2389ca937d11bc5c8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590696"
---
# <a name="connecting-to-an-instance-of-sql-server"></a><span data-ttu-id="76314-102">连接到 SQL Server 实例</span><span class="sxs-lookup"><span data-stu-id="76314-102">Connecting to an Instance of SQL Server</span></span>
  <span data-ttu-id="76314-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]管理对象 (SMO) 应用程序中的第一个编程步骤是创建对象的实例 <xref:Microsoft.SqlServer.Management.Smo.Server> ，并建立与实例的连接 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="76314-103">The first programming step in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) application is to create an instance of the <xref:Microsoft.SqlServer.Management.Smo.Server> object and to establish its connection to an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="76314-104">您可以创建 <xref:Microsoft.SqlServer.Management.Smo.Server> 对象的实例并且以三种方式建立与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的实例的连接。</span><span class="sxs-lookup"><span data-stu-id="76314-104">You can create an instance of the <xref:Microsoft.SqlServer.Management.Smo.Server> object and establish a connection to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in three ways.</span></span> <span data-ttu-id="76314-105">第一种方式是使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象变量提供连接信息。</span><span class="sxs-lookup"><span data-stu-id="76314-105">The first is using a <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object variable to provide the connection information.</span></span> <span data-ttu-id="76314-106">第二种方式是通过显式设置 <xref:Microsoft.SqlServer.Management.Smo.Server> 对象属性，提供连接信息。</span><span class="sxs-lookup"><span data-stu-id="76314-106">The second is to provide the connection information by explicitly setting the <xref:Microsoft.SqlServer.Management.Smo.Server> object properties.</span></span> <span data-ttu-id="76314-107">第三种方式是将 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的名称传递到 <xref:Microsoft.SqlServer.Management.Smo.Server> 对象构造函数中。</span><span class="sxs-lookup"><span data-stu-id="76314-107">The third is to pass the name of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance in the <xref:Microsoft.SqlServer.Management.Smo.Server> object constructor.</span></span>  
  
 <span data-ttu-id="76314-108">**使用 ServerConnection 对象**</span><span class="sxs-lookup"><span data-stu-id="76314-108">**Using a ServerConnection object**</span></span>  
  
 <span data-ttu-id="76314-109">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象变量的优点在于可以重复使用连接信息。</span><span class="sxs-lookup"><span data-stu-id="76314-109">The advantage of using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object variable is that the connection information can be reused.</span></span> <span data-ttu-id="76314-110">声明一个 <xref:Microsoft.SqlServer.Management.Smo.Server> 对象变量。</span><span class="sxs-lookup"><span data-stu-id="76314-110">Declare a <xref:Microsoft.SqlServer.Management.Smo.Server> object variable.</span></span> <span data-ttu-id="76314-111">然后，声明一个 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象，并且设置与连接信息（例如 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的名称）和身份验证模式有关的属性。</span><span class="sxs-lookup"><span data-stu-id="76314-111">Then, declare a <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object and set properties with connection information such as the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], and the authentication mode.</span></span> <span data-ttu-id="76314-112">接下来，将 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象变量作为参数传递到 <xref:Microsoft.SqlServer.Management.Smo.Server> 对象构造函数中。</span><span class="sxs-lookup"><span data-stu-id="76314-112">Then, pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object variable as a parameter to the <xref:Microsoft.SqlServer.Management.Smo.Server> object constructor.</span></span> <span data-ttu-id="76314-113">建议不要同时在不同的服务器对象之间共享连接。</span><span class="sxs-lookup"><span data-stu-id="76314-113">It is not recommended to share connections between different server objects at the same time.</span></span> <span data-ttu-id="76314-114">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> 方法可以获取现有连接设置的副本。</span><span class="sxs-lookup"><span data-stu-id="76314-114">Use the <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> method to get a copy of the existing connection settings.</span></span>  
  
 <span data-ttu-id="76314-115">**显式设置服务器对象属性**</span><span class="sxs-lookup"><span data-stu-id="76314-115">**Setting Server object properties explicitly**</span></span>  
  
 <span data-ttu-id="76314-116">或者，您可以声明 <xref:Microsoft.SqlServer.Management.Smo.Server> 对象变量并调用默认构造函数。</span><span class="sxs-lookup"><span data-stu-id="76314-116">Alternatively, you can declare the <xref:Microsoft.SqlServer.Management.Smo.Server> object variable and call the default constructor.</span></span> <span data-ttu-id="76314-117">照原样，<xref:Microsoft.SqlServer.Management.Smo.Server> 对象将尝试通过所有默认连接设置连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的默认实例。</span><span class="sxs-lookup"><span data-stu-id="76314-117">As is, the <xref:Microsoft.SqlServer.Management.Smo.Server> object tries to connect to the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] with all the default connection settings.</span></span>  
  
 <span data-ttu-id="76314-118">**在服务器对象构造函数中提供 SQL Server 实例名称**</span><span class="sxs-lookup"><span data-stu-id="76314-118">**Providing the SQL Server instance name in the Server object constructor**</span></span>  
  
 <span data-ttu-id="76314-119">声明 <xref:Microsoft.SqlServer.Management.Smo.Server> 对象变量并将 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例名称作为字符串参数传递到构造函数中。</span><span class="sxs-lookup"><span data-stu-id="76314-119">Declare the <xref:Microsoft.SqlServer.Management.Smo.Server> object variable and pass the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance name as a string parameter in the constructor.</span></span> <span data-ttu-id="76314-120"><xref:Microsoft.SqlServer.Management.Smo.Server> 对象使用默认的连接设置建立与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的实例的连接。</span><span class="sxs-lookup"><span data-stu-id="76314-120">The <xref:Microsoft.SqlServer.Management.Smo.Server> object establishes a connection with the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] with the default connection settings.</span></span>  
  
## <a name="connection-pooling"></a><span data-ttu-id="76314-121">连接池</span><span class="sxs-lookup"><span data-stu-id="76314-121">Connection Pooling</span></span>  
 <span data-ttu-id="76314-122">通常不要求调用 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> 对象的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 方法。</span><span class="sxs-lookup"><span data-stu-id="76314-122">It is typically not required to call the <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> method of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span> <span data-ttu-id="76314-123">在需要时，SMO 会自动建立连接，并在操作完成后，将连接发布到连接池。</span><span class="sxs-lookup"><span data-stu-id="76314-123">SMO will automatically establish a connection when required, and release the connection to the connection pool after it has finished performing operations.</span></span> <span data-ttu-id="76314-124">在调用 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> 方法时，不释放与池的连接。</span><span class="sxs-lookup"><span data-stu-id="76314-124">When the <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> method is called, the connection is not released to the pool.</span></span> <span data-ttu-id="76314-125">若要释放与池的连接，需要显式调用 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="76314-125">An explicit call to the <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> method is required to release the connection to the pool.</span></span> <span data-ttu-id="76314-126">此外，您可以通过设置 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> 对象的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 属性，请求非池的连接。</span><span class="sxs-lookup"><span data-stu-id="76314-126">Additionally, you can request a non-pooled connection by setting the <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> property of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
## <a name="multithreaded-applications"></a><span data-ttu-id="76314-127">多线程应用程序</span><span class="sxs-lookup"><span data-stu-id="76314-127">Multithreaded Applications</span></span>  
 <span data-ttu-id="76314-128">对于多线程应用程序，每个线程应使用单独的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象。</span><span class="sxs-lookup"><span data-stu-id="76314-128">For multithreaded applications, a separate <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object should be used in each thread.</span></span>  
  
## <a name="connecting-to-an-instance-of-sql-server-for-rmo"></a><span data-ttu-id="76314-129">连接到用于 RMO 的 SQL Server 实例</span><span class="sxs-lookup"><span data-stu-id="76314-129">Connecting to an Instance of SQL Server for RMO</span></span>  
 <span data-ttu-id="76314-130">复制管理对象 (RMO) 用于连接到复制服务器的方法与 SMO 稍有不同。</span><span class="sxs-lookup"><span data-stu-id="76314-130">Replication Management Objects (RMO) uses a slightly different method from SMO to connect to a replication server.</span></span>  
  
 <span data-ttu-id="76314-131">RMO 编程对象要求通过使用 `Microsoft.SqlServer.Management.Common` 命名空间实现的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象，建立与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的实例的连接。</span><span class="sxs-lookup"><span data-stu-id="76314-131">RMO programming objects require that a connection to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is made by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object implemented by the `Microsoft.SqlServer.Management.Common` namespace.</span></span> <span data-ttu-id="76314-132">与服务器的这一连接独立于 RMO 编程对象建立。</span><span class="sxs-lookup"><span data-stu-id="76314-132">This connection to the server is made independently of an RMO programming object.</span></span> <span data-ttu-id="76314-133">然后，在实例创建期间或通过指派该对象的 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性，将它传递到 RMO 对象。</span><span class="sxs-lookup"><span data-stu-id="76314-133">It is then it is passed to the RMO object either during instance creation or by assignment to the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property of the object.</span></span> <span data-ttu-id="76314-134">采用这种方式，RMO 编程对象实例和连接对象实例可以分别创建和管理，而多个 RMO 编程对象可以重用一个连接对象。</span><span class="sxs-lookup"><span data-stu-id="76314-134">In this manner, an RMO programming object and the connection object instances can be created and managed separately, and a single connection object can be reused with multiple RMO programming objects.</span></span> <span data-ttu-id="76314-135">连接复制服务器时适用下列规则：</span><span class="sxs-lookup"><span data-stu-id="76314-135">The following rules apply for connections to a replication server:</span></span>  
  
-   <span data-ttu-id="76314-136">为指定的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象定义连接的所有属性。</span><span class="sxs-lookup"><span data-stu-id="76314-136">All properties for the connection are defined for a specified <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
-   <span data-ttu-id="76314-137">与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的每个连接都必须具有自己的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象。</span><span class="sxs-lookup"><span data-stu-id="76314-137">Each connection to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] must have its own <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
-   <span data-ttu-id="76314-138">执行连接并成功登录服务器所需的所有验证信息由 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象提供。</span><span class="sxs-lookup"><span data-stu-id="76314-138">All authentication information to make the connection and successfully log on to the server is supplied in the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
-   <span data-ttu-id="76314-139">默认情况下，使用 Microsoft Windows 身份验证进行连接。</span><span class="sxs-lookup"><span data-stu-id="76314-139">By default, connections are made by using Microsoft Windows Authentication.</span></span> <span data-ttu-id="76314-140">若要使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证，<xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.LoginSecure%2A> 必须设置为 False，并且 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Login%2A> 和 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Password%2A> 必须设置为有效的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="76314-140">To use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.LoginSecure%2A> must be set to False and <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Login%2A> and <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Password%2A> must be set to a valid [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logon and password.</span></span> <span data-ttu-id="76314-141">安全凭据必须始终以安全的方式存储和处理，并且尽可能在运行时提供。</span><span class="sxs-lookup"><span data-stu-id="76314-141">Security credentials must always be stored and handled securely, and supplied at run time whenever possible.</span></span>  
  
-   <span data-ttu-id="76314-142">必须在将连接传递到任何 RMO 编程对象前调用 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="76314-142">The <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> method must be called before passing the connection to any RMO programming object.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="76314-143">示例</span><span class="sxs-lookup"><span data-stu-id="76314-143">Examples</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="connecting-to-the-local-instance-of-sql-server-by-using-windows-authentication-in-visual-basic"></a><span data-ttu-id="76314-144">通过在 Visual Basic 中使用 Windows 身份验证连接到 SQL Server 的本地实例</span><span class="sxs-lookup"><span data-stu-id="76314-144">Connecting to the Local Instance of SQL Server by Using Windows Authentication in Visual Basic</span></span>  
 <span data-ttu-id="76314-145">连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的本地实例并不要求大量代码。</span><span class="sxs-lookup"><span data-stu-id="76314-145">Connecting to the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not require much code.</span></span> <span data-ttu-id="76314-146">而是依赖于身份验证方法和服务器的默认设置。</span><span class="sxs-lookup"><span data-stu-id="76314-146">Instead, it relies on default settings for authentication method and server.</span></span> <span data-ttu-id="76314-147">要求检索数据的第一个操作将导致创建连接。</span><span class="sxs-lookup"><span data-stu-id="76314-147">The first operation that requires data to be retrieved will cause a connection to be created.</span></span>  
  
 <span data-ttu-id="76314-148">此示例是 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 通过使用 Windows 身份验证连接到的本地实例的 .net 代码。</span><span class="sxs-lookup"><span data-stu-id="76314-148">This example is [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET code that connects to the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using Windows Authentication.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VB1](SMO How to#SMO_VB1)]  -->  
  
## <a name="connecting-to-the-local-instance-of-sql-server-by-using-windows-authentication-in-visual-c"></a><span data-ttu-id="76314-149">通过在 Visual C# 中使用 Windows 身份验证连接到 SQL Server 的本地实例</span><span class="sxs-lookup"><span data-stu-id="76314-149">Connecting to the Local Instance of SQL Server by Using Windows Authentication in Visual C#</span></span>  
 <span data-ttu-id="76314-150">连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的本地实例并不要求大量代码。</span><span class="sxs-lookup"><span data-stu-id="76314-150">Connecting to the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not require much code.</span></span> <span data-ttu-id="76314-151">而是依赖于身份验证方法和服务器的默认设置。</span><span class="sxs-lookup"><span data-stu-id="76314-151">Instead, it relies on default settings for authentication method and server.</span></span> <span data-ttu-id="76314-152">要求检索数据的第一个操作将导致创建连接。</span><span class="sxs-lookup"><span data-stu-id="76314-152">The first operation that requires data to be retrieved will cause a connection to be created.</span></span>  
  
 <span data-ttu-id="76314-153">此示例是 Visual C# .NET 代码，它通过使用 Windows 身份验证连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的本地实例。</span><span class="sxs-lookup"><span data-stu-id="76314-153">This example is Visual C# .NET code that connects to the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using Windows Authentication.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//The connection is established when a property is requested.   
Console.WriteLine(srv.Information.Version);   
}   
//The connection is automatically disconnected when the Server variable goes out of scope.  
```  
  
## <a name="connecting-to-a-remote-instance-of-sql-server-by-using-windows-authentication-in-visual-basic"></a><span data-ttu-id="76314-154">通过在 Visual Basic 中使用 Windows 身份验证连接到 SQL Server 的远程实例</span><span class="sxs-lookup"><span data-stu-id="76314-154">Connecting to a Remote Instance of SQL Server by Using Windows Authentication in Visual Basic</span></span>  
 <span data-ttu-id="76314-155">在您通过使用 Windows 身份验证连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的实例时，不必指定身份验证类型。</span><span class="sxs-lookup"><span data-stu-id="76314-155">When you connect to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using Windows Authentication, you do not have to specify the authentication type.</span></span> <span data-ttu-id="76314-156">默认情况下使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="76314-156">Windows Authentication is the default.</span></span>  
  
 <span data-ttu-id="76314-157">此示例是 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 通过使用 Windows 身份验证连接到远程实例的 .net 代码。</span><span class="sxs-lookup"><span data-stu-id="76314-157">This example is [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET code that connects to the remote instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using Windows Authentication.</span></span> <span data-ttu-id="76314-158">字符串变量*strServer*包含远程实例的名称。</span><span class="sxs-lookup"><span data-stu-id="76314-158">The string variable *strServer* contains the name of the remote instance.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VB2](SMO How to#SMO_VB2)]  -->  
  
## <a name="connecting-to-a-remote-instance-of-sql-server-by-using-windows-authentication-in-visual-c"></a><span data-ttu-id="76314-159">通过在 Visual C# 中使用 Windows 身份验证连接到 SQL Server 的远程实例</span><span class="sxs-lookup"><span data-stu-id="76314-159">Connecting to a Remote Instance of SQL Server by Using Windows Authentication in Visual C#</span></span>  
 <span data-ttu-id="76314-160">在您通过使用 Windows 身份验证连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的实例时，不必指定身份验证类型。</span><span class="sxs-lookup"><span data-stu-id="76314-160">When you connect to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using Windows Authentication, you do not have to specify the authentication type.</span></span> <span data-ttu-id="76314-161">默认情况下使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="76314-161">Windows Authentication is the default.</span></span>  
  
 <span data-ttu-id="76314-162">此示例是 Visual C# .NET 代码，它通过使用 Windows 身份验证连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的远程实例。</span><span class="sxs-lookup"><span data-stu-id="76314-162">This example is Visual C# .NET code that connects to the remote instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using Windows Authentication.</span></span> <span data-ttu-id="76314-163">字符串变量*strServer*包含远程实例的名称。</span><span class="sxs-lookup"><span data-stu-id="76314-163">The string variable *strServer* contains the name of the remote instance.</span></span>  
  
```  
{   
//Connect to a remote instance of SQL Server.   
Server srv;   
//The strServer string variable contains the name of a remote instance of SQL Server.   
srv = new Server(strServer);   
//The actual connection is made when a property is retrieved.   
Console.WriteLine(srv.Information.Version);   
}   
//The connection is automatically disconnected when the Server variable goes out of scope.  
```  
  
## <a name="connecting-to-an-instance-of-sql-server-by-using-sql-server-authentication-in-visual-basic"></a><span data-ttu-id="76314-164">通过在 Visual Basic 中使用 SQL Server 身份验证连接到 SQL Server 的实例</span><span class="sxs-lookup"><span data-stu-id="76314-164">Connecting to an Instance of SQL Server by Using SQL Server Authentication in Visual Basic</span></span>  
 <span data-ttu-id="76314-165">在您通过使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的实例时，必须指定身份验证类型。</span><span class="sxs-lookup"><span data-stu-id="76314-165">When you connect to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, you must specify the authentication type.</span></span> <span data-ttu-id="76314-166">此示例演示声明 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象变量的替代方法，从而使连接信息可以重复使用。</span><span class="sxs-lookup"><span data-stu-id="76314-166">This example demonstrates the alternative method of declaring a <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object variable, which enables the connection information to be reused.</span></span>  
  
 <span data-ttu-id="76314-167">示例是 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .net 代码，演示如何连接到远程，并且*vPassword*包含登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="76314-167">The example is [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET code that demonstrates how to connect to the remote and *vPassword* contain the logon and password.</span></span>  
  
```  
' compile with:   
' /r:Microsoft.SqlServer.Smo.dll  
' /r:Microsoft.SqlServer.ConnectionInfo.dll  
' /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Common  
  
Public Class A  
   Public Shared Sub Main()  
      Dim sqlServerLogin As [String] = "user_id"  
      Dim password As [String] = "pwd"  
      Dim instanceName As [String] = "instance_name"  
      Dim remoteSvrName As [String] = "remote_server_name"  
  
      ' Connecting to an instance of SQL Server using SQL Server Authentication  
      Dim srv1 As New Server()   ' connects to default instance  
      srv1.ConnectionContext.LoginSecure = False   ' set to true for Windows Authentication  
      srv1.ConnectionContext.Login = sqlServerLogin  
      srv1.ConnectionContext.Password = password  
      Console.WriteLine(srv1.Information.Version)   ' connection is established  
  
      ' Connecting to a named instance of SQL Server with SQL Server Authentication using ServerConnection  
      Dim srvConn As New ServerConnection()  
      srvConn.ServerInstance = ".\" & instanceName   ' connects to named instance  
      srvConn.LoginSecure = False   ' set to true for Windows Authentication  
      srvConn.Login = sqlServerLogin  
      srvConn.Password = password  
      Dim srv2 As New Server(srvConn)  
      Console.WriteLine(srv2.Information.Version)   ' connection is established  
  
      ' For remote connection, remote server name / ServerInstance needs to be specified  
      Dim srvConn2 As New ServerConnection(remoteSvrName)  
      srvConn2.LoginSecure = False  
      srvConn2.Login = sqlServerLogin  
      srvConn2.Password = password  
      Dim srv3 As New Server(srvConn2)  
      Console.WriteLine(srv3.Information.Version)   ' connection is established  
   End Sub  
End Class  
```  
  
## <a name="connecting-to-an-instance-of-sql-server-by-using-sql-server-authentication-in-visual-c"></a><span data-ttu-id="76314-168">通过在 Visual C# 中使用 SQL Server 身份验证连接到 SQL Server 的实例</span><span class="sxs-lookup"><span data-stu-id="76314-168">Connecting to an Instance of SQL Server by Using SQL Server Authentication in Visual C#</span></span>  
 <span data-ttu-id="76314-169">在您通过使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的实例时，必须指定身份验证类型。</span><span class="sxs-lookup"><span data-stu-id="76314-169">When you connect to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, you must specify the authentication type.</span></span> <span data-ttu-id="76314-170">此示例演示声明 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象变量的替代方法，从而使连接信息可以重复使用。</span><span class="sxs-lookup"><span data-stu-id="76314-170">This example demonstrates the alternative method of declaring a <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object variable, which enables the connection information to be reused.</span></span>  
  
 <span data-ttu-id="76314-171">该示例是 Visual c # .NET 代码，演示如何连接到远程，并且*vPassword*包含登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="76314-171">The example is Visual C# .NET code that demonstrates how to connect to the remote and *vPassword* contain the logon and password.</span></span>  
  
```  
// compile with:   
// /r:Microsoft.SqlServer.Smo.dll  
// /r:Microsoft.SqlServer.ConnectionInfo.dll  
// /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
using System;  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Common;  
  
public class A {  
   public static void Main() {   
      String sqlServerLogin = "user_id";  
      String password = "pwd";  
      String instanceName = "instance_name";  
      String remoteSvrName = "remote_server_name";  
  
      // Connecting to an instance of SQL Server using SQL Server Authentication  
      Server srv1 = new Server();   // connects to default instance  
      srv1.ConnectionContext.LoginSecure = false;   // set to true for Windows Authentication  
      srv1.ConnectionContext.Login = sqlServerLogin;  
      srv1.ConnectionContext.Password = password;  
      Console.WriteLine(srv1.Information.Version);   // connection is established  
  
      // Connecting to a named instance of SQL Server with SQL Server Authentication using ServerConnection  
      ServerConnection srvConn = new ServerConnection();  
      srvConn.ServerInstance = @".\" + instanceName;   // connects to named instance  
      srvConn.LoginSecure = false;   // set to true for Windows Authentication  
      srvConn.Login = sqlServerLogin;  
      srvConn.Password = password;  
      Server srv2 = new Server(srvConn);  
      Console.WriteLine(srv2.Information.Version);   // connection is established  
  
      // For remote connection, remote server name / ServerInstance needs to be specified  
      ServerConnection srvConn2 = new ServerConnection(remoteSvrName);  
      srvConn2.LoginSecure = false;  
      srvConn2.Login = sqlServerLogin;  
      srvConn2.Password = password;  
      Server srv3 = new Server(srvConn2);  
      Console.WriteLine(srv3.Information.Version);   // connection is established  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="76314-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="76314-172">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>  
  
  
