---
title: 模拟和 CLR 集成安全性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- impersonation [CLR integration]
- security [CLR integration]
- execution context [CLR integration]
- user impersonation [CLR integration]
- context [CLR integration]
ms.assetid: 1495a7af-2248-4cee-afdb-9269fb3a7774
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a2313733c5a24f28c44571dd230ddc58fc9a1264
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694089"
---
# <a name="impersonation-and-clr-integration-security"></a><span data-ttu-id="0bfe7-102">模拟和 CLR 集成安全性</span><span class="sxs-lookup"><span data-stu-id="0bfe7-102">Impersonation and CLR Integration Security</span></span>
  <span data-ttu-id="0bfe7-103">托管代码访问外部资源时，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不会自动模拟执行例程所处的当前执行上下文。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-103">When managed code accesses external resources, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not automatically impersonate the current execution context under which the routine is executing.</span></span> <span data-ttu-id="0bfe7-104">`EXTERNAL_ACCESS` 和 `UNSAFE` 程序集中的代码可以显式模拟当前执行上下文。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-104">Code in `EXTERNAL_ACCESS` and `UNSAFE` assemblies can explicitly impersonate the current execution context.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0bfe7-105">有关模拟中的行为更改的信息，请参阅[SQL Server 2014 中数据库引擎功能的重大更改](../breaking-changes-to-database-engine-features-in-sql-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-105">For information on behavior changes in impersonation, see [Breaking Changes to Database Engine Features in SQL Server 2014](../breaking-changes-to-database-engine-features-in-sql-server-2016.md).</span></span>  
  
 <span data-ttu-id="0bfe7-106">进程内数据访问提供程序提供了一个应用程序编程接口 `SqlContext.WindowsIdentity`，该接口可用于检索与当前安全上下文有关的令牌。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-106">The in-process data access provider provides an application programming interface, `SqlContext.WindowsIdentity`, that can be used to retrieve the token associated with the current security context.</span></span> <span data-ttu-id="0bfe7-107">`EXTERNAL_ACCESS` 和 `UNSAFE` 程序集中的托管代码可使用此方法检索上下文并使用 .NET Framework `WindowsIdentity.Impersonate` 方法模拟该上下文。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-107">Managed code in `EXTERNAL_ACCESS` and `UNSAFE` assemblies can use this method to retrieve the context and use the .NET Framework `WindowsIdentity.Impersonate` method to impersonate that context.</span></span> <span data-ttu-id="0bfe7-108">当用户代码显式模拟时，适用下列限制：</span><span class="sxs-lookup"><span data-stu-id="0bfe7-108">The following restrictions apply when user code explicitly impersonates:</span></span>  
  
-   <span data-ttu-id="0bfe7-109">托管代码处于模拟状态时，不允许进程内数据访问。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-109">In-process data access is not allowed when managed code is in an impersonated state.</span></span> <span data-ttu-id="0bfe7-110">代码可以撤消模拟，然后调用进程内数据访问。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-110">Code can undo impersonation and then call in-process data access.</span></span> <span data-ttu-id="0bfe7-111">请注意，这需要存储原始 `WindowsImpersonationContext` 方法的返回值（`Impersonate` 对象）并对该 `Undo` 调用 `WindowsImpersonationContext` 方法。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-111">Note that this requires storing the return value (a `WindowsImpersonationContext` object) of the original `Impersonate` method, and calling the `Undo` method on this `WindowsImpersonationContext`.</span></span>  
  
     <span data-ttu-id="0bfe7-112">该限制意味着当出现进程内数据访问时，实际它将始终位于该会话当前安全上下文的上下文中。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-112">This restriction means that when in-process data access occurs, it is always in the context of the current security context in effect for the session.</span></span> <span data-ttu-id="0bfe7-113">在托管代码内无法通过显式模拟对此进行修改。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-113">It cannot be modified by explicit impersonation within managed code.</span></span>  
  
-   <span data-ttu-id="0bfe7-114">为异步执行托管代码（例如通过 `UNSAFE` 程序集创建线程并异步运行代码），从不允许进程内数据访问。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-114">For managed code executing asynchronously (for example, through `UNSAFE` assemblies creating threads and running code asynchronously), in-process data access is never allowed.</span></span> <span data-ttu-id="0bfe7-115">无论是否存在模拟，结果都将为 True。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-115">This is true whether or not there is impersonation.</span></span>  
  
 <span data-ttu-id="0bfe7-116">当代码在与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的上下文不同的模拟上下文中运行时，无法执行进程内数据访问调用，该代码在进行进程内数据访问调用之前应撤消此模拟上下文。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-116">When code is running in an impersonated context that is different from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], it cannot perform in-process data access calls; it should undo the impersonation context before making in-process data access calls.</span></span> <span data-ttu-id="0bfe7-117">当从托管代码中进行进程内数据访问时，指向托管代码中的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 项的原始执行上下文始终用于授权。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-117">When in-process data access is made from managed code, the original execution context of the [!INCLUDE[tsql](../../includes/tsql-md.md)] entry point into the managed code is always used for authorization.</span></span>  
  
 <span data-ttu-id="0bfe7-118">`EXTERNAL_ACCESS` 程序集和 `UNSAFE` 程序集都使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务帐户访问操作系统资源，除非它们如上所述自动模拟当前的安全上下文。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-118">Both `EXTERNAL_ACCESS` assemblies and `UNSAFE` assemblies access operating system resources with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account, unless they voluntarily impersonate the current security context as previously described.</span></span> <span data-ttu-id="0bfe7-119">因此，`EXTERNAL_ACCESS` 程序集的作者需要具有比 `SAFE` 程序集的作者更高的信任级别，该级别由 `EXTERNAL ACCESS` 登录级别权限指定。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-119">Because of this, the authors of `EXTERNAL_ACCESS` assemblies require a higher level of trust than those of `SAFE` assemblies, which is specified by the `EXTERNAL ACCESS` login-level permission.</span></span> <span data-ttu-id="0bfe7-120">只有被信任可在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务帐户下运行代码的登录名才应被授予 `EXTERNAL ACCESS` 权限。</span><span class="sxs-lookup"><span data-stu-id="0bfe7-120">Only logins who are trusted to run code under the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account should be granted the `EXTERNAL ACCESS` permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bfe7-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0bfe7-121">See Also</span></span>  
 <span data-ttu-id="0bfe7-122">[CLR 集成安全性](../../relational-databases/clr-integration/security/clr-integration-security.md) </span><span class="sxs-lookup"><span data-stu-id="0bfe7-122">[CLR Integration Security](../../relational-databases/clr-integration/security/clr-integration-security.md) </span></span>  
 [<span data-ttu-id="0bfe7-123">模拟和连接凭据</span><span class="sxs-lookup"><span data-stu-id="0bfe7-123">Impersonation and Credentials for Connections</span></span>](../../relational-databases/clr-integration/data-access/impersonation-and-credentials-for-connections.md)  
  
  
