---
title: 与 SQL Server 的实例断开连接 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, disconnecting
- SMO [SQL Server], disconnecting
- instances of SQL Server, disconnecting
- disconnecting [SMO]
ms.assetid: 4ca7f7eb-6b3f-4c73-ac63-88afa8570b61
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3514fce8fb8f1ccc8bd1b54acfa27825eaebbd34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590694"
---
# <a name="disconnecting-from-an-instance-of-sql-server"></a><span data-ttu-id="f5b39-102">断开与 SQL Server 实例的连接</span><span class="sxs-lookup"><span data-stu-id="f5b39-102">Disconnecting from an Instance of SQL Server</span></span>
  <span data-ttu-id="f5b39-103">不需要手动关闭和断开 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理对象 (SMO) 对象。</span><span class="sxs-lookup"><span data-stu-id="f5b39-103">Manually closing and disconnecting [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) objects is not required.</span></span> <span data-ttu-id="f5b39-104">系统会根据需要打开和关闭连接。</span><span class="sxs-lookup"><span data-stu-id="f5b39-104">Connections are opened and closed as required.</span></span>  
  
## <a name="connection-pooling"></a><span data-ttu-id="f5b39-105">连接池</span><span class="sxs-lookup"><span data-stu-id="f5b39-105">Connection Pooling</span></span>  
 <span data-ttu-id="f5b39-106">如果调用了 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> 方法，则不会自动释放连接。</span><span class="sxs-lookup"><span data-stu-id="f5b39-106">When the <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> method is called, the connection is not automatically released.</span></span> <span data-ttu-id="f5b39-107">必须显式调用 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> 方法才能释放与连接池的连接。</span><span class="sxs-lookup"><span data-stu-id="f5b39-107">The <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> method must be called explicitly to release the connection to the connection pool.</span></span> <span data-ttu-id="f5b39-108">您还可以请求不加入连接池的连接。</span><span class="sxs-lookup"><span data-stu-id="f5b39-108">Also, you can request a non-pooled connection.</span></span> <span data-ttu-id="f5b39-109">通过设置引用 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> 对象的 <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> 属性的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 属性，可以实现此目的。</span><span class="sxs-lookup"><span data-stu-id="f5b39-109">You do this by setting the <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> property that references the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
## <a name="disconnecting-from-an-instance-of-sql-server-for-rmo"></a><span data-ttu-id="f5b39-110">断开 RMO 的 SQL Server 实例连接</span><span class="sxs-lookup"><span data-stu-id="f5b39-110">Disconnecting from an Instance of SQL Server for RMO</span></span>  
 <span data-ttu-id="f5b39-111">在使用 RMO 进行编程时，关闭服务器连接的操作过程与使用 SMO 时略有不同。</span><span class="sxs-lookup"><span data-stu-id="f5b39-111">Closing server connections when you are programming with RMO works slightly different from SMO.</span></span>  
  
 <span data-ttu-id="f5b39-112">由于 RMO 对象的服务器连接由对象维护，因此当 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 你使用 RMO 进行编程时，还会使用此对象。</span><span class="sxs-lookup"><span data-stu-id="f5b39-112">Because the server connection for an RMO object is maintained by the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object, this object is also used when disconnecting from an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] when you program by using RMO.</span></span> <span data-ttu-id="f5b39-113">若要使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象关闭连接，请调用 RMO 对象的 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f5b39-113">To close a connection by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object, call the <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> method of the RMO object.</span></span> <span data-ttu-id="f5b39-114">在关闭连接之后，无法再使用 RMO 对象。</span><span class="sxs-lookup"><span data-stu-id="f5b39-114">After the connection has been closed, RMO objects cannot be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5b39-115">示例</span><span class="sxs-lookup"><span data-stu-id="f5b39-115">Example</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-basic"></a><span data-ttu-id="f5b39-116">在 Visual Basic 中关闭和断开 SMO 对象</span><span class="sxs-lookup"><span data-stu-id="f5b39-116">Closing and Disconnecting an SMO Object in Visual Basic</span></span>  
 <span data-ttu-id="f5b39-117">此代码示例演示如何请求不加入连接池的连接，方法是设置 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> 对象属性的 <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="f5b39-117">This code example shows how to request a non-pooled connection by setting the <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> object property.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VB4](SMO How to#SMO_VB4)]  -->  
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-c"></a><span data-ttu-id="f5b39-118">在 Visual C# 中关闭和断开 SMO 对象</span><span class="sxs-lookup"><span data-stu-id="f5b39-118">Closing and Disconnecting an SMO Object in Visual C#</span></span>  
 <span data-ttu-id="f5b39-119">此代码示例演示如何请求不加入连接池的连接，方法是设置 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> 对象属性的 <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="f5b39-119">This code example shows how to request a non-pooled connection by setting the <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> object property.</span></span>  
  
```  
{   
Server srv;   
srv = new Server();   
//Disable automatic disconnection.   
srv.ConnectionContext.AutoDisconnectMode = AutoDisconnectMode.NoAutoDisconnect;   
//Connect to the local, default instance of SQL Server.   
srv.ConnectionContext.Connect();   
//The actual connection is made when a property is retrieved.   
Console.WriteLine(srv.Information.Version);   
//Disconnect explicitly.   
srv.ConnectionContext.Disconnect();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5b39-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f5b39-120">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>  
  
  
