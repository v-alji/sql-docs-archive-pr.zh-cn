---
title: 宿主保护属性和 CLR 集成编程 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- HostProtectionAttribute [CLR integration]
- common language runtime [SQL Server], host protection attributes
- disallowed types and members [CLR integration]
- common language runtime [SQL Server], disallowed types and members
- HPAs [CLR integration]
ms.assetid: 268078df-63ca-4c03-a8e7-7108bcea9697
author: rothja
ms.author: jroth
ms.openlocfilehash: 16ca1e4734e66b0eca85523764739e8f8b32634a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691256"
---
# <a name="host-protection-attributes-and-clr-integration-programming"></a><span data-ttu-id="53472-102">宿主保护属性和 CLR 集成编程</span><span class="sxs-lookup"><span data-stu-id="53472-102">Host Protection Attributes and CLR Integration Programming</span></span>
  <span data-ttu-id="53472-103">公共语言运行时 (CLR) 提供一种机制，用于使用 CLR 宿主（例如从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 开始的 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]）可能需要的特定属性对属于 .NET Framework 的托管应用程序编程接口 (API) 进行批注。</span><span class="sxs-lookup"><span data-stu-id="53472-103">The common language runtime (CLR) provides a mechanism to annotate managed application programming interfaces (APIs) that are part of the .NET Framework with certain attributes that may be of interest to a host of the CLR, such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="53472-104">这种宿主保护属性 (HPA) 的示例包括：</span><span class="sxs-lookup"><span data-stu-id="53472-104">Examples of such host protection attributes (HPAs) include:</span></span>  
  
-   <span data-ttu-id="53472-105">`SharedState`，指示 API 是否公开创建或管理共享状态（例如，静态类字段）的功能。</span><span class="sxs-lookup"><span data-stu-id="53472-105">`SharedState`, which indicates whether the API exposes the ability to create or manage shared state (for example, static class fields).</span></span>  
  
-   <span data-ttu-id="53472-106">`Synchronization`，指示 API 是否公开在线程之间执行同步的功能。</span><span class="sxs-lookup"><span data-stu-id="53472-106">`Synchronization`, which indicates whether the API exposes the ability to perform synchronization between threads.</span></span>  
  
-   <span data-ttu-id="53472-107">`ExternalProcessMgmt`，指示 API 是否公开控制宿主进程的方法。</span><span class="sxs-lookup"><span data-stu-id="53472-107">`ExternalProcessMgmt`, which indicates whether the API exposes a way to control the host process.</span></span>  
  
 <span data-ttu-id="53472-108">在给定这些属性的基础上，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可通过代码访问安全性 (CAS) 指定在宿主环境下不允许的 HPA 的列表。</span><span class="sxs-lookup"><span data-stu-id="53472-108">Given these attributes, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specifies a list of HPAs that are disallowed in the hosted environment through code access security (CAS).</span></span> <span data-ttu-id="53472-109">CAS 要求由以下三个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 权限集之一指定：`SAFE`、`EXTERNAL_ACCESS` 或 `UNSAFE`。</span><span class="sxs-lookup"><span data-stu-id="53472-109">The CAS requirements are specified by one of three [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permission sets: `SAFE`, `EXTERNAL_ACCESS`, or `UNSAFE`.</span></span> <span data-ttu-id="53472-110">在服务器上使用 `CREATE ASSEMBLY` 语句注册程序集时，将指定这三个安全级别之一。</span><span class="sxs-lookup"><span data-stu-id="53472-110">One of these three security levels is specified when the assembly is registered on the server, using the `CREATE ASSEMBLY` statement.</span></span> <span data-ttu-id="53472-111">在 `SAFE` 或 `EXTERNAL_ACCESS` 权限集内执行的代码必须避免应用了 `System.Security.Permissions.HostProtectionAttribute` 属性的特定类型或成员。</span><span class="sxs-lookup"><span data-stu-id="53472-111">Code executing within the `SAFE` or `EXTERNAL_ACCESS` permission sets must avoid certain types or members that have the `System.Security.Permissions.HostProtectionAttribute` attribute applied.</span></span> <span data-ttu-id="53472-112">有关详细信息，请参阅[创建程序集](../clr-integration/assemblies/creating-an-assembly.md)和[CLR 集成编程模型限制](../clr-integration/database-objects/clr-integration-programming-model-restrictions.md)。</span><span class="sxs-lookup"><span data-stu-id="53472-112">For more information, see [Creating an Assembly](../clr-integration/assemblies/creating-an-assembly.md) and [CLR Integration Programming Model Restrictions](../clr-integration/database-objects/clr-integration-programming-model-restrictions.md).</span></span>  
  
 <span data-ttu-id="53472-113">`HostProtectionAttribute` 与其说是一项安全权限，不如说是一种用于提高可靠性的方法，原因在于它标识宿主可能不允许的特定代码构造（类型或方法）。</span><span class="sxs-lookup"><span data-stu-id="53472-113">The `HostProtectionAttribute` is not a security permission as much as a way to improve reliability, in that it identifies specific code constructs, either types or methods, that the host may disallow.</span></span> <span data-ttu-id="53472-114">使用 `HostProtectionAttribute` 会强制执行可帮助保护宿主稳定性的编程模型。</span><span class="sxs-lookup"><span data-stu-id="53472-114">The use of the `HostProtectionAttribute` enforces a programming model that helps protect the stability of the host.</span></span>  
  
## <a name="host-protection-attributes"></a><span data-ttu-id="53472-115">宿主保护属性</span><span class="sxs-lookup"><span data-stu-id="53472-115">Host Protection Attributes</span></span>  
 <span data-ttu-id="53472-116">HPA 可标识不适合宿主编程模型的类型或成员，并表示可靠性威胁的以下递增级别：</span><span class="sxs-lookup"><span data-stu-id="53472-116">HPAs identify types or members that do not fit the host programming model and represent the following increasing levels of reliability threat:</span></span>  
  
-   <span data-ttu-id="53472-117">在其他方面为良性。</span><span class="sxs-lookup"><span data-stu-id="53472-117">Are otherwise benign.</span></span>  
  
-   <span data-ttu-id="53472-118">可能会导致反序列化服务器托管的用户代码。</span><span class="sxs-lookup"><span data-stu-id="53472-118">Could lead to destabilization of server-managed user code.</span></span>  
  
-   <span data-ttu-id="53472-119">可能会导致反序列化服务器进程本身。</span><span class="sxs-lookup"><span data-stu-id="53472-119">Could lead to destabilization of the server process itself.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="53472-120">不允许使用指定了值为、、、、、、、或的枚举的类型或成员 `HostProtectionAttribute` `System.Security.Permissions.HostProtectionResource` `ExternalProcessMgmt` `ExternalThreading` `MayLeakOnAbort` `SecurityInfrastructure` `SelfAffectingProcessMgmnt` `SelfAffectingThreading` `SharedState` `Synchronization` `UI` 。</span><span class="sxs-lookup"><span data-stu-id="53472-120">disallows the use of a type or member that has a `HostProtectionAttribute` that specifies a `System.Security.Permissions.HostProtectionResource` enumeration with a value of `ExternalProcessMgmt`, `ExternalThreading`, `MayLeakOnAbort`, `SecurityInfrastructure`, `SelfAffectingProcessMgmnt`, `SelfAffectingThreading`, `SharedState`, `Synchronization`, or `UI`.</span></span> <span data-ttu-id="53472-121">这会阻止程序集调用启用共享状态、执行同步、可能导致终止时资源泄漏或影响 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程的完整性的成员。</span><span class="sxs-lookup"><span data-stu-id="53472-121">This prevents the assemblies from calling members that enable sharing state, perform synchronization, might cause a resource leak on termination, or affect the integrity of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span>  
  
### <a name="disallowed-types-and-members"></a><span data-ttu-id="53472-122">不允许的类型和成员</span><span class="sxs-lookup"><span data-stu-id="53472-122">Disallowed Types and Members</span></span>  
 <span data-ttu-id="53472-123">下面的主题标识了其 `HostProtectionResource` 值被 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 禁用的类型和成员。</span><span class="sxs-lookup"><span data-stu-id="53472-123">The following topics identify types and members whose `HostProtectionResource` values are disallowed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="53472-124">这些主题中的列表是通过受支持的程序集生成的。</span><span class="sxs-lookup"><span data-stu-id="53472-124">The lists in these topics were generated from the supported assemblies.</span></span>  <span data-ttu-id="53472-125">有关详细信息，请参阅[支持的 .NET Framework 库](../clr-integration/database-objects/supported-net-framework-libraries.md)。</span><span class="sxs-lookup"><span data-stu-id="53472-125">For more information, see [Supported .NET Framework Libraries](../clr-integration/database-objects/supported-net-framework-libraries.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="53472-126">本节内容</span><span class="sxs-lookup"><span data-stu-id="53472-126">In This Section</span></span>  
 [<span data-ttu-id="53472-127">Microsoft.VisualBasic.dll 中禁用的类型和成员</span><span class="sxs-lookup"><span data-stu-id="53472-127">Disallowed Types and Members in Microsoft.VisualBasic.dll</span></span>](disallowed-types-and-members-in-microsoft-visualbasic-dll.md)  
 <span data-ttu-id="53472-128">列出了 Microsoft.VisualBasic.dll 中其 HPA 值被禁用的类型和成员。</span><span class="sxs-lookup"><span data-stu-id="53472-128">Lists the types and members in Microsoft.VisualBasic.dll whose HPA values are disallowed.</span></span>  
  
 [<span data-ttu-id="53472-129">mscorlib.dll 中禁用的类型和成员</span><span class="sxs-lookup"><span data-stu-id="53472-129">Disallowed Types and Members in mscorlib.dll</span></span>](disallowed-types-and-members-in-mscorlib-dll.md)  
 <span data-ttu-id="53472-130">列出了 mscorlib.dll 中其 HPA 值被禁用的类型和成员。</span><span class="sxs-lookup"><span data-stu-id="53472-130">Lists the types and members in mscorlib.dll whose HPA values are disallowed.</span></span>  
  
 [<span data-ttu-id="53472-131">System.dll 中禁用的类型和成员</span><span class="sxs-lookup"><span data-stu-id="53472-131">Disallowed Types and Members in System.dll</span></span>](disallowed-types-and-members-in-system-dll.md)  
 <span data-ttu-id="53472-132">列出了 System.dll 中其 HPA 值被禁用的类型和成员。</span><span class="sxs-lookup"><span data-stu-id="53472-132">Lists the types and members in System.dll whose HPA values are disallowed.</span></span>  
  
 [<span data-ttu-id="53472-133">System.Data.dll 中禁用的类型和成员</span><span class="sxs-lookup"><span data-stu-id="53472-133">Disallowed Types and Members in System.Data.dll</span></span>](disallowed-types-and-members-in-system-data-dll.md)  
 <span data-ttu-id="53472-134">列出了 System.Data.dll 中其 HPA 值被禁用的类型和成员。</span><span class="sxs-lookup"><span data-stu-id="53472-134">Lists the types and members in System.Data.dll whose HPA values are disallowed.</span></span>  
  
 [<span data-ttu-id="53472-135">System.Core.dll 中禁用的类型和成员</span><span class="sxs-lookup"><span data-stu-id="53472-135">Disallowed Types and Members in System.Core.dll</span></span>](disallowed-types-and-members-in-system-core-dll.md)  
 <span data-ttu-id="53472-136">列出了 System.Core.dll 中其 HPA 值被禁用的类型和成员。</span><span class="sxs-lookup"><span data-stu-id="53472-136">Lists the types and members in System.Core.dll whose HPA values are disallowed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53472-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="53472-137">See Also</span></span>  
 <span data-ttu-id="53472-138">[CLR 集成代码访问安全性](../clr-integration/security/clr-integration-code-access-security.md) </span><span class="sxs-lookup"><span data-stu-id="53472-138">[CLR Integration Code Access Security](../clr-integration/security/clr-integration-code-access-security.md) </span></span>  
 <span data-ttu-id="53472-139">[CLR 集成编程模型限制](../clr-integration/database-objects/clr-integration-programming-model-restrictions.md) </span><span class="sxs-lookup"><span data-stu-id="53472-139">[CLR Integration Programming Model Restrictions](../clr-integration/database-objects/clr-integration-programming-model-restrictions.md) </span></span>  
 [<span data-ttu-id="53472-140">创建程序集</span><span class="sxs-lookup"><span data-stu-id="53472-140">Creating an Assembly</span></span>](../clr-integration/assemblies/creating-an-assembly.md)  
  
  
