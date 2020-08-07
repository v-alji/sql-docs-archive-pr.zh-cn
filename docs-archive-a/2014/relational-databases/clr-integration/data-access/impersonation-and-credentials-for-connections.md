---
title: 连接的模拟和凭据 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- impersonation [CLR integration]
- security [CLR integration]
- database objects [CLR integration], connections
- connections [CLR integration]
- authentication [CLR integration]
- user impersonation [CLR integration]
- credentials [CLR integration]
- database objects [CLR integration], security
ms.assetid: 293dce7d-1db2-4657-992f-8c583d6e9ebb
author: rothja
ms.author: jroth
ms.openlocfilehash: cdbc52e07f4502adda7301ce7f635c050ed9c3c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587861"
---
# <a name="impersonation-and-credentials-for-connections"></a><span data-ttu-id="f58ed-102">模拟和连接凭据</span><span class="sxs-lookup"><span data-stu-id="f58ed-102">Impersonation and Credentials for Connections</span></span>
  <span data-ttu-id="f58ed-103">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 公共语言运行时 (CLR) 集成中，使用 Windows 身份验证虽然比较复杂，但是比使用 SQL Server 身份验证更为安全。</span><span class="sxs-lookup"><span data-stu-id="f58ed-103">In the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] common language runtime (CLR) integration, using Windows Authentication is complex, but is more secure than using SQL Server Authentication.</span></span> <span data-ttu-id="f58ed-104">使用 Windows 身份验证时，请谨记下列注意事项：</span><span class="sxs-lookup"><span data-stu-id="f58ed-104">When using Windows Authentication, keep in mind the following considerations.</span></span>  
  
 <span data-ttu-id="f58ed-105">默认情况下，连出至 Windows 的 SQL Server 进程会获得 SQL Server Windows 服务帐户的安全上下文。</span><span class="sxs-lookup"><span data-stu-id="f58ed-105">By default, a SQL Server process that connects out to Windows acquires the security context of the SQL Server Windows service account.</span></span> <span data-ttu-id="f58ed-106">但可以将 CLR 函数映射到代理标识上，以便其出站连接具有的安全上下文不同于 Windows 服务帐户的安全上下文。</span><span class="sxs-lookup"><span data-stu-id="f58ed-106">But it is possible to map a CLR function to a proxy identity, so that its outbound connections have a different security context than that of the Windows service account.</span></span>  
  
 <span data-ttu-id="f58ed-107">在某些情况下，最好使用 `SqlContext.WindowsIdentity` 属性来模拟调用方，而非作为服务帐户运行。</span><span class="sxs-lookup"><span data-stu-id="f58ed-107">In some cases, you may want to impersonate the caller by using the `SqlContext.WindowsIdentity` property instead of running as the service account.</span></span> <span data-ttu-id="f58ed-108">`WindowsIdentity` 实例表示调用调用代码的客户端的标识，并且仅在客户端使用 Windows 身份验证时才可用。</span><span class="sxs-lookup"><span data-stu-id="f58ed-108">The `WindowsIdentity` instance represents the identity of the client that invoked the calling code, and is only available when the client used Windows Authentication.</span></span> <span data-ttu-id="f58ed-109">在已获得 `WindowsIdentity` 实例后，可以调用 `Impersonate` 来更改线程的安全令牌，然后代表客户端打开 ADO.NET 连接。</span><span class="sxs-lookup"><span data-stu-id="f58ed-109">After you have obtained the `WindowsIdentity` instance, you can call `Impersonate` to change the security token of the thread, and then open ADO.NET connections on behalf of the client.</span></span>  
  
 <span data-ttu-id="f58ed-110">调用 SQLContext 后，无法访问本地数据并且无法访问系统数据。</span><span class="sxs-lookup"><span data-stu-id="f58ed-110">After you call SQLContext.WindowsIdentity.Impersonate, you cannot access local data and you cannot access system data.</span></span> <span data-ttu-id="f58ed-111">若要再次访问数据，必须调用 WindowsImpersonationContext。</span><span class="sxs-lookup"><span data-stu-id="f58ed-111">To access data again, you have to call WindowsImpersonationContext.Undo.</span></span>  
  
 <span data-ttu-id="f58ed-112">下面的示例将说明如何使用 `SqlContext.WindowsIdentity` 属性来模拟调用方。</span><span class="sxs-lookup"><span data-stu-id="f58ed-112">The following example shows how to impersonate the caller by using the `SqlContext.WindowsIdentity` property.</span></span>  
  
 <span data-ttu-id="f58ed-113">Visual C#</span><span class="sxs-lookup"><span data-stu-id="f58ed-113">Visual C#</span></span>  
  
```  
WindowsIdentity clientId = null;  
WindowsImpersonationContext impersonatedUser = null;  
  
clientId = SqlContext.WindowsIdentity;  
  
// This outer try block is used to protect from   
// exception filter attacks which would prevent  
// the inner finally block from executing and   
// resetting the impersonation.  
try  
{  
   try  
   {  
      impersonatedUser = clientId.Impersonate();  
      if (impersonatedUser != null)  
         return GetFileDetails(directoryPath);  
         else return null;  
   }  
   finally  
   {  
      if (impersonatedUser != null)  
         impersonatedUser.Undo();  
   }  
}  
catch  
{  
   throw;  
}  
```  
  
> [!NOTE]  
>  <span data-ttu-id="f58ed-114">有关模拟中行为更改的信息，请参阅[SQL Server 2014 中数据库引擎功能的重大更改](../../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="f58ed-114">For information about behavior changes in impersonation, see [Breaking Changes to Database Engine Features in SQL Server 2014](../../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md).</span></span>  
  
 <span data-ttu-id="f58ed-115">另外，如果获得了 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 标识实例，则默认情况下不能将该实例传播到其他计算机；默认情况下 Windows 安全基础结构会限制这种传播。</span><span class="sxs-lookup"><span data-stu-id="f58ed-115">Furthermore, if you obtained the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows identity instance, by default you cannot propagate that instance to another computer; Windows security infrastructure restricts that by default.</span></span> <span data-ttu-id="f58ed-116">然而，存在一种称为“委托”的机制，通过该机制可在多个可信任的计算机之间启用 Windows 标识传播。</span><span class="sxs-lookup"><span data-stu-id="f58ed-116">There is, however, a mechanism called "delegation" that enables propagation of Windows identities across multiple trusted computers.</span></span> <span data-ttu-id="f58ed-117">你可以在 TechNet 文章 "[Kerberos 协议转换和约束委派](https://go.microsoft.com/fwlink/?LinkId=50419)" 中了解有关委派的详细信息。</span><span class="sxs-lookup"><span data-stu-id="f58ed-117">You can learn more about delegation in the TechNet article, "[Kerberos Protocol Transition and Constrained Delegation](https://go.microsoft.com/fwlink/?LinkId=50419)".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f58ed-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f58ed-118">See Also</span></span>  
 [<span data-ttu-id="f58ed-119">SqlContext 对象</span><span class="sxs-lookup"><span data-stu-id="f58ed-119">SqlContext Object</span></span>](../../clr-integration-data-access-in-process-ado-net/sqlcontext-object.md)  
  
  
