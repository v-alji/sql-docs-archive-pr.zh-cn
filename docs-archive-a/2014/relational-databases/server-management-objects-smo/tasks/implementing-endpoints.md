---
title: 实现终结点 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- endpoints [SMO]
ms.assetid: f8674dbb-9bc0-488f-9def-e9e0ce1ddf86
author: stevestein
ms.author: sstein
ms.openlocfilehash: 293a661c6e1ad6f6139e30e0824e99686af98f90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692819"
---
# <a name="implementing-endpoints"></a><span data-ttu-id="980ef-102">实现端点</span><span class="sxs-lookup"><span data-stu-id="980ef-102">Implementing Endpoints</span></span>
  <span data-ttu-id="980ef-103">端点是一种可以本机方式侦听请求的服务。</span><span class="sxs-lookup"><span data-stu-id="980ef-103">An endpoint is a service that can listen natively for requests.</span></span> <span data-ttu-id="980ef-104">SMO 通过使用 <xref:Microsoft.SqlServer.Management.Smo.Endpoint> 对象支持各种类型的端点。</span><span class="sxs-lookup"><span data-stu-id="980ef-104">SMO supports various types of endpoints by using the <xref:Microsoft.SqlServer.Management.Smo.Endpoint> object.</span></span> <span data-ttu-id="980ef-105">您可以创建用于处理特定类型负载且使用特定协议的端点服务，方法是创建一个 <xref:Microsoft.SqlServer.Management.Smo.Endpoint> 对象的实例并设置其属性。</span><span class="sxs-lookup"><span data-stu-id="980ef-105">You can create an endpoint service that handles a specific type of payload, which uses a specific protocol, by creating an instance of an <xref:Microsoft.SqlServer.Management.Smo.Endpoint> object and setting its properties.</span></span>  
  
 <span data-ttu-id="980ef-106"><xref:Microsoft.SqlServer.Management.Smo.Endpoint.EndpointType%2A> 对象的 <xref:Microsoft.SqlServer.Management.Smo.Endpoint> 属性可用于指定下列负载类型之一：</span><span class="sxs-lookup"><span data-stu-id="980ef-106">The <xref:Microsoft.SqlServer.Management.Smo.Endpoint.EndpointType%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Endpoint> object can be used to specify on of the following payload types:</span></span>  
  
-   <span data-ttu-id="980ef-107">数据库镜像</span><span class="sxs-lookup"><span data-stu-id="980ef-107">Database mirroring</span></span>  
  
-   <span data-ttu-id="980ef-108">SOAP（ [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 和更低的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本中支持 SOAP 端点）</span><span class="sxs-lookup"><span data-stu-id="980ef-108">SOAP (support for SOAP endpoints is present in [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] and earlier [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] versions)</span></span>  
  
-   <span data-ttu-id="980ef-109">Service Broker</span><span class="sxs-lookup"><span data-stu-id="980ef-109">Service Broker</span></span>  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)]  
  
 <span data-ttu-id="980ef-110"><xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A> 属性还可用于指定以下两种支持的协议：</span><span class="sxs-lookup"><span data-stu-id="980ef-110">Also, the <xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A> property can be used to specify the following two supported protocols:</span></span>  
  
-   <span data-ttu-id="980ef-111">HTTP 协议</span><span class="sxs-lookup"><span data-stu-id="980ef-111">HTTP protocol</span></span>  
  
-   <span data-ttu-id="980ef-112">TCP 协议</span><span class="sxs-lookup"><span data-stu-id="980ef-112">TCP protocol</span></span>  
  
 <span data-ttu-id="980ef-113">如果指定了负载的类型，则可以通过使用 <xref:Microsoft.SqlServer.Management.Smo.Endpoint.Payload%2A> 对象属性设置实际负载。</span><span class="sxs-lookup"><span data-stu-id="980ef-113">Having specified the type of payload, the actual payload can be set by using the <xref:Microsoft.SqlServer.Management.Smo.Endpoint.Payload%2A> object property.</span></span> <span data-ttu-id="980ef-114"><xref:Microsoft.SqlServer.Management.Smo.Payload> 对象属性提供了对指定类型的负载对象的引用，可以修改该负载对象的属性。</span><span class="sxs-lookup"><span data-stu-id="980ef-114">The <xref:Microsoft.SqlServer.Management.Smo.Payload> object property provides a reference to a payload object of the specified type, for which the properties can be modified.</span></span>  
  
 <span data-ttu-id="980ef-115">对于 <xref:Microsoft.SqlServer.Management.Smo.DatabaseMirroringPayload> 对象，必须指定镜像角色和是否启用加密。</span><span class="sxs-lookup"><span data-stu-id="980ef-115">For the <xref:Microsoft.SqlServer.Management.Smo.DatabaseMirroringPayload> object, you must specify the mirroring role and whether encryption is enabled.</span></span> <span data-ttu-id="980ef-116"><xref:Microsoft.SqlServer.Management.Smo.ServiceBrokerPayload> 对象要求提供与消息转发、允许的最大连接数和身份验证模式有关的信息。</span><span class="sxs-lookup"><span data-stu-id="980ef-116">The <xref:Microsoft.SqlServer.Management.Smo.ServiceBrokerPayload> object requires information about message forwarding, maximum number of connections allowed and the authentication mode.</span></span> <span data-ttu-id="980ef-117"><xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethod.%23ctor%2A> 对象需要设置各种属性，包括用来指定可用于客户端（存储过程和用户定义函数）的 SOAP 负载方法的 <xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethodCollection.Add%2A> 对象属性。</span><span class="sxs-lookup"><span data-stu-id="980ef-117">The <xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethod.%23ctor%2A> object requires various properties to be set including the <xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethodCollection.Add%2A> object property that specifies the SOAP payload methods available to clients (stored procedures and user-defined functions).</span></span>  
  
 <span data-ttu-id="980ef-118">与此类似，通过使用 <xref:Microsoft.SqlServer.Management.Smo.Endpoint.Protocol%2A> 对象属性可以设置实际协议，该对象属性引用由 <xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A> 属性所指定类型的协议对象。</span><span class="sxs-lookup"><span data-stu-id="980ef-118">Similarly, the actual protocol can be set by using the <xref:Microsoft.SqlServer.Management.Smo.Endpoint.Protocol%2A> object property that references a protocol object of the type specified by <xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A> property.</span></span> <span data-ttu-id="980ef-119"><xref:Microsoft.SqlServer.Management.Smo.HttpProtocol> 对象要求提供受限 IP 地址、端口、网站和身份验证信息的列表。</span><span class="sxs-lookup"><span data-stu-id="980ef-119">The <xref:Microsoft.SqlServer.Management.Smo.HttpProtocol> object requires a list of restricted IP addresses, and port, website, and authentication information.</span></span> <span data-ttu-id="980ef-120"><xref:Microsoft.SqlServer.Management.Smo.TcpProtocol> 对象也需要受限 IP 地址和端口信息的列表。</span><span class="sxs-lookup"><span data-stu-id="980ef-120">The <xref:Microsoft.SqlServer.Management.Smo.TcpProtocol> object also requires a list of restricted IP addresses and port information.</span></span>  
  
 <span data-ttu-id="980ef-121">创建端点并完全定义之后，便可授予、撤消及拒绝数据库用户、组、角色和登录名的访问权限。</span><span class="sxs-lookup"><span data-stu-id="980ef-121">When the endpoint has been created and fully defined, access can be granted to, revoked from, and denied to database users, groups, roles, and logons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="980ef-122">示例</span><span class="sxs-lookup"><span data-stu-id="980ef-122">Example</span></span>  
 <span data-ttu-id="980ef-123">对于下面的代码示例，您必须选择编程环境、编程模板和编程语言才能创建应用程序。</span><span class="sxs-lookup"><span data-stu-id="980ef-123">For the following code example, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="980ef-124">有关详细信息，请参阅[在 Visual studio .net 中创建 VISUAL BASIC SMO 项目](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)和[在 visual Studio .Net 中创建 VISUAL C&#35; smo 项目](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="980ef-124">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-visual-basic"></a><span data-ttu-id="980ef-125">在 Visual Basic 中创建数据库镜像端点服务</span><span class="sxs-lookup"><span data-stu-id="980ef-125">Creating a Database Mirroring Endpoint Service in Visual Basic</span></span>  
 <span data-ttu-id="980ef-126">代码示例演示了如何在 SMO 中创建数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="980ef-126">The code example demonstrates how to create a Database Mirroring endpoint in SMO.</span></span> <span data-ttu-id="980ef-127">这是创建数据库镜像之前的必要步骤。</span><span class="sxs-lookup"><span data-stu-id="980ef-127">This is necessary before you create a database mirror.</span></span> <span data-ttu-id="980ef-128">请使用 <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> 和 <xref:Microsoft.SqlServer.Management.Smo.Database> 对象上的其他属性创建数据库镜像。</span><span class="sxs-lookup"><span data-stu-id="980ef-128">Use the <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> and other properties on the <xref:Microsoft.SqlServer.Management.Smo.Database> object to create a database mirror.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBEndpoints1](SMO How to#SMO_VBEndpoints1)]  -->  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-visual-c"></a><span data-ttu-id="980ef-129">在 Visual C# 中创建数据库镜像端点服务</span><span class="sxs-lookup"><span data-stu-id="980ef-129">Creating a Database Mirroring Endpoint Service in Visual C#</span></span>  
 <span data-ttu-id="980ef-130">代码示例演示了如何在 SMO 中创建数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="980ef-130">The code example demonstrates how to create a Database Mirroring endpoint in SMO.</span></span> <span data-ttu-id="980ef-131">这是创建数据库镜像之前的必要步骤。</span><span class="sxs-lookup"><span data-stu-id="980ef-131">This is necessary before you create a database mirror.</span></span> <span data-ttu-id="980ef-132">请使用 <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> 和 <xref:Microsoft.SqlServer.Management.Smo.Database> 对象上的其他属性创建数据库镜像。</span><span class="sxs-lookup"><span data-stu-id="980ef-132">Use the <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> and other properties on the <xref:Microsoft.SqlServer.Management.Smo.Database> object to create a database mirror.</span></span>  
  
```csharp
{  
            //Set up a database mirroring endpoint on the server before   
        //setting up a database mirror.   
        //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
            //Define an Endpoint object variable for database mirroring.   
            Endpoint ep = default(Endpoint);  
            ep = new Endpoint(srv, "Mirroring_Endpoint");  
            ep.ProtocolType = ProtocolType.Tcp;  
            ep.EndpointType = EndpointType.DatabaseMirroring;  
            //Specify the protocol ports.   
            ep.Protocol.Http.SslPort = 5024;  
            ep.Protocol.Tcp.ListenerPort = 6666;  
            //Specify the role of the payload.   
            ep.Payload.DatabaseMirroring.ServerMirroringRole = ServerMirroringRole.All;  
            //Create the endpoint on the instance of SQL Server.   
            ep.Create();  
            //Start the endpoint.   
            ep.Start();  
            Console.WriteLine(ep.EndpointState);  
        }  
```  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-powershell"></a><span data-ttu-id="980ef-133">在 PowerShell 中创建数据库镜像端点服务</span><span class="sxs-lookup"><span data-stu-id="980ef-133">Creating a Database Mirroring Endpoint Service in PowerShell</span></span>  
 <span data-ttu-id="980ef-134">代码示例演示了如何在 SMO 中创建数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="980ef-134">The code example demonstrates how to create a Database Mirroring endpoint in SMO.</span></span> <span data-ttu-id="980ef-135">这是创建数据库镜像之前的必要步骤。</span><span class="sxs-lookup"><span data-stu-id="980ef-135">This is necessary before you create a database mirror.</span></span> <span data-ttu-id="980ef-136">请使用 <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> 和 <xref:Microsoft.SqlServer.Management.Smo.Database> 对象上的其他属性创建数据库镜像。</span><span class="sxs-lookup"><span data-stu-id="980ef-136">Use the <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> and other properties on the <xref:Microsoft.SqlServer.Management.Smo.Database> object to create a database mirror.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = Get-Item default  
  
#Get a new endpoint to congure and add  
$ep = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Endpoint -argumentlist $srv,"Mirroring_Endpoint"  
  
#Set some properties  
$ep.ProtocolType = [Microsoft.SqlServer.Management.SMO.ProtocolType]::Tcp  
$ep.EndpointType = [Microsoft.SqlServer.Management.SMO.EndpointType]::DatabaseMirroring  
$ep.Protocol.Http.SslPort = 5024  
$ep.Protocol.Tcp.ListenerPort = 6666 #inline comment  
$ep.Payload.DatabaseMirroring.ServerMirroringRole = [Microsoft.SqlServer.Management.SMO.ServerMirroringRole]::All  
  
# Create the endpoint on the instance  
$ep.Create()  
  
# Start the endpoint  
$ep.Start()  
  
# Report its state  
$ep.EndpointState;  
```  
  
## <a name="see-also"></a><span data-ttu-id="980ef-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="980ef-137">See Also</span></span>  
 [<span data-ttu-id="980ef-138">数据库镜像终结点 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="980ef-138">The Database Mirroring Endpoint &#40;SQL Server&#41;</span></span>](../../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
