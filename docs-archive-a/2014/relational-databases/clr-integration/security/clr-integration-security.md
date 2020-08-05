---
title: CLR 集成安全性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- security [CLR integration]
- authorization [CLR integration]
- common language runtime [SQL Server], security
- database objects [CLR integration], security
ms.assetid: 05d7a471-c5d5-4730-b903-e4edc8157bb4
author: rothja
ms.author: jroth
ms.openlocfilehash: 0d99d32a061d8fe78a8ac3642a503cceb45f3809
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580777"
---
# <a name="clr-integration-security"></a><span data-ttu-id="f26b3-102">CLR 集成安全性</span><span class="sxs-lookup"><span data-stu-id="f26b3-102">CLR Integration Security</span></span>
  <span data-ttu-id="f26b3-103">[!INCLUDE[ssNoVersion](../../../includes/dnprdnshort-md.md)]公共语言运行时 (clr) 的安全模型管理并保护在 [!INCLUDE[ssNoVersion](../../../includes/tsql-md.md)] 语句或在服务器中运行的其他 CLR 对象之间运行的不同类型 clr 和非 CLR 对象之间的访问。</span><span class="sxs-lookup"><span data-stu-id="f26b3-103">The security model of the [!INCLUDE[ssNoVersion](../../../includes/dnprdnshort-md.md)] common language runtime (CLR) manages and secures access between different types of CLR and non-CLR objects running within [!INCLUDE[ssNoVersion](../../../includes/tsql-md.md)] statement or another CLR object running in the server.</span></span> <span data-ttu-id="f26b3-104">对象之间的调用称为链接。</span><span class="sxs-lookup"><span data-stu-id="f26b3-104">The calls between objects are referred to as links.</span></span> <span data-ttu-id="f26b3-105">对这些对象执行的安全检查类型取决于相关的链接类型。</span><span class="sxs-lookup"><span data-stu-id="f26b3-105">The types of security checks performed on these objects depend on the types of links involved.</span></span>  
  
 <span data-ttu-id="f26b3-106">CLR 集成安全模式可实现以下目的：</span><span class="sxs-lookup"><span data-stu-id="f26b3-106">The CLR integration security model has the following goals:</span></span>  
  
-   <span data-ttu-id="f26b3-107">默认情况下，在上运行托管的用户代码 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f26b3-107">By default, running managed user code on [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f26b3-108">如果执行有可能损害 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 可靠性的操作，则应当受到适当的高级权限的保护。</span><span class="sxs-lookup"><span data-stu-id="f26b3-108">Performing operations that potentially compromise the robustness of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] should be protected by appropriate high-level permissions.</span></span>  
  
-   <span data-ttu-id="f26b3-109">托管用户代码不应当获得对数据库中用户数据或其他用户代码的未经授权访问。</span><span class="sxs-lookup"><span data-stu-id="f26b3-109">Managed user code should not gain unauthorized access to user data or other user code in the database.</span></span> <span data-ttu-id="f26b3-110">用户定义代码应当在调用该代码的用户会话的安全上下文中运行，且拥有该安全上下文的正确特权。</span><span class="sxs-lookup"><span data-stu-id="f26b3-110">User-defined code should run under the security context of the user-session that invoked it, and with the correct privileges for that security context.</span></span>  
  
-   <span data-ttu-id="f26b3-111">应当有控制来限制用户代码不得访问服务器以外的任何资源，而只能用于本地数据访问和计算。</span><span class="sxs-lookup"><span data-stu-id="f26b3-111">There should be controls for restricting user code from accessing any resources outside the server, using it strictly for local data access and computation.</span></span>  
  
-   <span data-ttu-id="f26b3-112">用户定义代码不应能通过在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 进程中运行而获得对系统资源的未经授权访问。</span><span class="sxs-lookup"><span data-stu-id="f26b3-112">User-defined code should not be able to gain unauthorized access to system resources by virtue of running in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] process.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="f26b3-113">使用 CLR 的基于代码访问的安全模型。</span><span class="sxs-lookup"><span data-stu-id="f26b3-113">with the code access-based security model of the CLR.</span></span> <span data-ttu-id="f26b3-114">本节将讨论此组合安全方法的某些优势。</span><span class="sxs-lookup"><span data-stu-id="f26b3-114">Some of the advantages of this combined approach to security are discussed in this section.</span></span>  
  
 <span data-ttu-id="f26b3-115">下表列出了本节的主题。</span><span class="sxs-lookup"><span data-stu-id="f26b3-115">The following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="f26b3-116">CLR 集成代码访问安全性</span><span class="sxs-lookup"><span data-stu-id="f26b3-116">CLR Integration Code Access Security</span></span>](clr-integration-code-access-security.md)  
 <span data-ttu-id="f26b3-117">讨论托管代码的代码访问安全性 (CAS) 模式。</span><span class="sxs-lookup"><span data-stu-id="f26b3-117">Discusses the code access security (CAS) model for managed code.</span></span>  
  
 [<span data-ttu-id="f26b3-118">宿主保护属性和 CLR 集成编程</span><span class="sxs-lookup"><span data-stu-id="f26b3-118">Host Protection Attributes and CLR Integration Programming</span></span>](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)  
 <span data-ttu-id="f26b3-119">提供有关 SAFE 和 EXTERNAL_ACCESS 程序集中禁止的宿主保护属性 (HPA) 值的信息。</span><span class="sxs-lookup"><span data-stu-id="f26b3-119">Provides information about the host protection attribute (HPA) values that are disallowed in SAFE and EXTERNAL_ACCESS assemblies.</span></span>  
  
 [<span data-ttu-id="f26b3-120">CLR 集成安全性中的链接</span><span class="sxs-lookup"><span data-stu-id="f26b3-120">Links in CLR Integration Security</span></span>](../../../database-engine/dev-guide/links-in-clr-integration-security.md)  
 <span data-ttu-id="f26b3-121">介绍在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中用户代码段是如何能相互调用的。</span><span class="sxs-lookup"><span data-stu-id="f26b3-121">Describes how pieces of user-code can call each other in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="f26b3-122">模拟和 CLR 集成安全性</span><span class="sxs-lookup"><span data-stu-id="f26b3-122">Impersonation and CLR Integration Security</span></span>](../../../database-engine/dev-guide/impersonation-and-clr-integration-security.md)  
 <span data-ttu-id="f26b3-123">讨论托管代码是如何使用模拟来访问外部资源的。</span><span class="sxs-lookup"><span data-stu-id="f26b3-123">Discusses how managed code accesses external resources using impersonation.</span></span>  
  
 [<span data-ttu-id="f26b3-124">允许部分可信任的调用方</span><span class="sxs-lookup"><span data-stu-id="f26b3-124">Allowing Partially Trusted Callers</span></span>](../../../database-engine/dev-guide/allowing-partially-trusted-callers.md)  
 <span data-ttu-id="f26b3-125">讨论当托管方法调用其他程序集中所包含类的方法时所产生的问题。</span><span class="sxs-lookup"><span data-stu-id="f26b3-125">Discusses issues that arise when a managed method invokes a method in a class contained in another assembly.</span></span>  
  
 [<span data-ttu-id="f26b3-126">应用程序域和 CLR 集成安全性</span><span class="sxs-lookup"><span data-stu-id="f26b3-126">Application Domains and CLR Integration Security</span></span>](../../../database-engine/dev-guide/application-domains-and-clr-integration-security.md)  
 <span data-ttu-id="f26b3-127">描述如何将程序集加载到应用程序域。</span><span class="sxs-lookup"><span data-stu-id="f26b3-127">Describes how assemblies are loaded into application domains.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f26b3-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f26b3-128">See Also</span></span>  
 [<span data-ttu-id="f26b3-129">管理 CLR 集成程序集</span><span class="sxs-lookup"><span data-stu-id="f26b3-129">Managing CLR Integration Assemblies</span></span>](../assemblies/managing-clr-integration-assemblies.md)  
  
  
