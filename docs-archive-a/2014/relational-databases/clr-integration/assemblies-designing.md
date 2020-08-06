---
title: 设计程序集 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- designing assemblies [SQL Server]
- assemblies [CLR integration], designing
ms.assetid: 9c07f706-6508-41aa-a4d7-56ce354f9061
author: rothja
ms.author: jroth
ms.openlocfilehash: 785ab80a529140a52ec18ef96ccaaeafd03698cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691253"
---
# <a name="designing-assemblies"></a><span data-ttu-id="6f673-102">设计程序集</span><span class="sxs-lookup"><span data-stu-id="6f673-102">Designing Assemblies</span></span>
  <span data-ttu-id="6f673-103">本主题说明了设计程序集时应考虑的下列因素：</span><span class="sxs-lookup"><span data-stu-id="6f673-103">This topic describes the following factors you should consider when you design assemblies:</span></span>  
  
-   <span data-ttu-id="6f673-104">打包程序集</span><span class="sxs-lookup"><span data-stu-id="6f673-104">Packaging assemblies</span></span>  
  
-   <span data-ttu-id="6f673-105">管理程序集安全性</span><span class="sxs-lookup"><span data-stu-id="6f673-105">Managing assembly security</span></span>  
  
-   <span data-ttu-id="6f673-106">对程序集的限制</span><span class="sxs-lookup"><span data-stu-id="6f673-106">Restrictions on assemblies</span></span>  
  
## <a name="packaging-assemblies"></a><span data-ttu-id="6f673-107">打包程序集</span><span class="sxs-lookup"><span data-stu-id="6f673-107">Packaging Assemblies</span></span>  
 <span data-ttu-id="6f673-108">程序集可以在其类和方法中包含多个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 例程或类型的功能。</span><span class="sxs-lookup"><span data-stu-id="6f673-108">An assembly can contain functionality for more than one [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] routine or type in its classes and methods.</span></span> <span data-ttu-id="6f673-109">在大部分时间里，打包在同一程序集中执行相关函数的例程的功能才有意义，如果这些例程共享相互调用方法的类，则尤为如此。</span><span class="sxs-lookup"><span data-stu-id="6f673-109">Most of the time, it makes sense to package the functionality of routines that perform related functions within the same assembly, especially if these routines share classes whose methods call one another.</span></span> <span data-ttu-id="6f673-110">例如，可以将执行公共语言运行时 (CLR) 触发器和 CLR 存储过程的数据项管理任务的类在同一程序集中打包。</span><span class="sxs-lookup"><span data-stu-id="6f673-110">For example, classes that perform data entry management tasks for common language runtime (CLR) triggers and CLR stored procedures can be packaged in the same assembly.</span></span> <span data-ttu-id="6f673-111">这是因为这些类的方法比起不相关的任务而言更可能调用对方。</span><span class="sxs-lookup"><span data-stu-id="6f673-111">This is because the methods for these classes are more likely to call each other than those of less related tasks.</span></span>  
  
 <span data-ttu-id="6f673-112">将代码打包到程序集中时，应考虑以下内容：</span><span class="sxs-lookup"><span data-stu-id="6f673-112">When you are packaging code into assembly, you should consider the following:</span></span>  
  
-   <span data-ttu-id="6f673-113">依赖于 CLR 用户定义函数的 CLR 用户定义类型和索引可以导致持久化数据存在于依赖程序集的数据库中。</span><span class="sxs-lookup"><span data-stu-id="6f673-113">CLR user-defined types and indexes that depend on CLR user-defined functions can cause persisted data to be in the database that depends on the assembly.</span></span> <span data-ttu-id="6f673-114">数据库中具有依赖于程序集的持久化数据时，修改程序集的代码通常更加复杂。</span><span class="sxs-lookup"><span data-stu-id="6f673-114">Modifying the code of an assembly is frequently more complex when there is persisted data that depends on the assembly in the database.</span></span> <span data-ttu-id="6f673-115">因此，通常将持久化数据相关性依赖（例如使用用户定义函数的用户定义类型和索引）的代码与没有这种持久化数据相关性的代码分开更好。</span><span class="sxs-lookup"><span data-stu-id="6f673-115">Therefore, it is generally better to separate code on which persisted data dependencies rely (such as user-defined types and indexes using user-defined functions) from code that does not have such persisted data dependencies.</span></span> <span data-ttu-id="6f673-116">有关详细信息，请参阅[实现程序集](assemblies-implementing.md)和[ALTER ASSEMBLY &#40;transact-sql&#41;](/sql/t-sql/statements/alter-assembly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6f673-116">For more information, see [Implementing Assemblies](assemblies-implementing.md) and [ALTER ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-assembly-transact-sql).</span></span>  
  
-   <span data-ttu-id="6f673-117">如果托管代码需要更高的权限，最好将该代码与不需要更高权限的代码分开，并将其放入单独的程序集。</span><span class="sxs-lookup"><span data-stu-id="6f673-117">If a piece of managed code requires higher permission, it is better to separate that code into a separate assembly from code that does not require higher permission.</span></span>  
  
## <a name="managing-assembly-security"></a><span data-ttu-id="6f673-118">管理程序集安全性</span><span class="sxs-lookup"><span data-stu-id="6f673-118">Managing Assembly Security</span></span>  
 <span data-ttu-id="6f673-119">当程序集运行托管代码时，可以控制程序集访问受 .NET 代码访问安全性保护的资源的程度。</span><span class="sxs-lookup"><span data-stu-id="6f673-119">You can control how much an assembly can access resources protected by .NET Code Access Security when it runs managed code.</span></span> <span data-ttu-id="6f673-120">可以通过在创建或修改程序集时指定三个权限集（SAFE、EXTERNAL_ACCESS 或 UNSAFE）之一执行以上操作。</span><span class="sxs-lookup"><span data-stu-id="6f673-120">You do this by specifying one of three permission sets when you create or modify an assembly: SAFE, EXTERNAL_ACCESS, or UNSAFE.</span></span>  
  
### <a name="safe"></a><span data-ttu-id="6f673-121">SAFE</span><span class="sxs-lookup"><span data-stu-id="6f673-121">SAFE</span></span>  
 <span data-ttu-id="6f673-122">SAFE 是默认的权限集，并且最具限制性。</span><span class="sxs-lookup"><span data-stu-id="6f673-122">SAFE is the default permission set and it is the most restrictive.</span></span> <span data-ttu-id="6f673-123">使用具有 SAFE 权限的程序集运行的代码不能访问外部系统资源（例如文件、网络、环境变量或注册表）。</span><span class="sxs-lookup"><span data-stu-id="6f673-123">Code run by an assembly with SAFE permissions cannot access external system resources such as files, the network, environment variables, or the registry.</span></span> <span data-ttu-id="6f673-124">SAFE 代码可以从本地 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库访问数据，或执行不涉及访问本地数据库以外资源的计算和业务逻辑。</span><span class="sxs-lookup"><span data-stu-id="6f673-124">SAFE code can access data from the local [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases or perform computations and business logic that do not involve accessing resources outside the local databases.</span></span>  
  
 <span data-ttu-id="6f673-125">大多数程序集执行计算和数据管理任务，而不需要访问 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外的资源。</span><span class="sxs-lookup"><span data-stu-id="6f673-125">Most assemblies perform computation and data management tasks without having to access resources outside [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6f673-126">因此，建议您将 SAFE 作为程序集权限集。</span><span class="sxs-lookup"><span data-stu-id="6f673-126">Therefore, we recommend SAFE as the assembly permission set.</span></span>  
  
### <a name="external_access"></a><span data-ttu-id="6f673-127">EXTERNAL_ACCESS</span><span class="sxs-lookup"><span data-stu-id="6f673-127">EXTERNAL_ACCESS</span></span>  
 <span data-ttu-id="6f673-128">EXTERNAL_ACCESS 允许程序集访问某些外部系统资源（例如文件、网络、Web 服务、环境变量和注册表）。</span><span class="sxs-lookup"><span data-stu-id="6f673-128">EXTERNAL_ACCESS allows for assemblies to access certain external system resources such as files, networks, Web services, environmental variables, and the registry.</span></span> <span data-ttu-id="6f673-129">只有具有 EXTERNAL ACCESS 权限的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登录名才能创建 EXTERNAL_ACCESS 程序集。</span><span class="sxs-lookup"><span data-stu-id="6f673-129">Only [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logins with EXTERNAL ACCESS permissions can create EXTERNAL_ACCESS assemblies.</span></span>  
  
 <span data-ttu-id="6f673-130">SAFE 和 EXTERNAL_ACCESS 程序集只能包含可验证为类型安全的代码。</span><span class="sxs-lookup"><span data-stu-id="6f673-130">SAFE and EXTERNAL_ACCESS assemblies can contain only code that is verifiably type-safe.</span></span> <span data-ttu-id="6f673-131">这意味着这些程序集仅可以通过对类型定义有效的具有定义完善的入口点来访问类。</span><span class="sxs-lookup"><span data-stu-id="6f673-131">This means that these assemblies can only access classes through well-defined entry points that are valid for the type definition.</span></span> <span data-ttu-id="6f673-132">因此，它们不能随意访问不属于该代码所有的内存缓冲区。</span><span class="sxs-lookup"><span data-stu-id="6f673-132">Therefore, they cannot arbitrarily access memory buffers not owned by the code.</span></span> <span data-ttu-id="6f673-133">另外，它们不能执行可能对 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 进程的可靠性具有负面影响的操作。</span><span class="sxs-lookup"><span data-stu-id="6f673-133">Additionally, they cannot perform operations that might have an adverse effect on the robustness of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] process.</span></span>  
  
### <a name="unsafe"></a><span data-ttu-id="6f673-134">UNSAFE</span><span class="sxs-lookup"><span data-stu-id="6f673-134">UNSAFE</span></span>  
 <span data-ttu-id="6f673-135">UNSAFE 不限制程序集访问资源，包括 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以内和以外的资源。</span><span class="sxs-lookup"><span data-stu-id="6f673-135">UNSAFE gives assemblies unrestricted access to resources, both within and outside [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6f673-136">在 UNSAFE 程序集内运行的代码可以调用非托管代码。</span><span class="sxs-lookup"><span data-stu-id="6f673-136">Code that is running from within an UNSAFE assembly can call unmanaged code.</span></span>  
  
 <span data-ttu-id="6f673-137">同时，指定 UNSAFE 将允许程序集中的代码执行 CLR 验证工具认为是非安全类型的操作。</span><span class="sxs-lookup"><span data-stu-id="6f673-137">Also, specifying UNSAFE allows for the code in the assembly to perform operations that are considered type-unsafe by the CLR verifier.</span></span> <span data-ttu-id="6f673-138">这些操作可能以非控制的方式访问 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 进程空间中的内存缓冲区。</span><span class="sxs-lookup"><span data-stu-id="6f673-138">These operations can potentially access memory buffers in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] process space in an uncontrolled manner.</span></span> <span data-ttu-id="6f673-139">UNSAFE 程序集也可能破坏 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 或公共语言运行时的安全系统。</span><span class="sxs-lookup"><span data-stu-id="6f673-139">UNSAFE assemblies can also potentially subvert the security system of either [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or the common language runtime.</span></span> <span data-ttu-id="6f673-140">有经验的开发人员或管理员应仅向高度可信的程序集授予 UNSAFE 权限。</span><span class="sxs-lookup"><span data-stu-id="6f673-140">UNSAFE permissions should be granted only to highly trusted assemblies by experienced developers or administrators.</span></span> <span data-ttu-id="6f673-141">只有**sysadmin**固定服务器角色的成员才可以创建不安全的程序集。</span><span class="sxs-lookup"><span data-stu-id="6f673-141">Only members of the **sysadmin** fixed server role can create UNSAFE assemblies.</span></span>  
  
## <a name="restrictions-on-assemblies"></a><span data-ttu-id="6f673-142">对程序集的限制</span><span class="sxs-lookup"><span data-stu-id="6f673-142">Restrictions on Assemblies</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="6f673-143">对程序集中的托管代码有一些限制，以便确保可以以可靠和可伸缩的方式运行它们。</span><span class="sxs-lookup"><span data-stu-id="6f673-143">puts certain restrictions on managed code in assemblies to make sure that they can run in a reliable and scalable manner.</span></span> <span data-ttu-id="6f673-144">这意味着在 SAFE 和 EXTERNAL_ACCESS 程序集不允许可能危及服务器可靠性的某些操作。</span><span class="sxs-lookup"><span data-stu-id="6f673-144">This means that certain operations that can compromise the robustness of the server are not permitted in SAFE and EXTERNAL_ACCESS assemblies.</span></span>  
  
### <a name="disallowed-custom-attributes"></a><span data-ttu-id="6f673-145">禁止的自定义属性</span><span class="sxs-lookup"><span data-stu-id="6f673-145">Disallowed Custom Attributes</span></span>  
 <span data-ttu-id="6f673-146">不能用以下自定义属性批注程序集：</span><span class="sxs-lookup"><span data-stu-id="6f673-146">Assemblies cannot be annotated with the following custom attributes:</span></span>  
  
```  
System.ContextStaticAttribute  
System.MTAThreadAttribute  
System.Runtime.CompilerServices.MethodImplAttribute  
System.Runtime.CompilerServices.CompilationRelaxationsAttribute  
System.Runtime.Remoting.Contexts.ContextAttribute  
System.Runtime.Remoting.Contexts.SynchronizationAttribute  
System.Runtime.InteropServices.DllImportAttribute   
System.Security.Permissions.CodeAccessSecurityAttribute  
System.STAThreadAttribute  
System.ThreadStaticAttribute  
```  
  
 <span data-ttu-id="6f673-147">另外，不能用以下自定义属性批注 SAFE 和 EXTERNAL_ACCESS 程序集：</span><span class="sxs-lookup"><span data-stu-id="6f673-147">Additionally, SAFE and EXTERNAL_ACCESS assemblies cannot be annotated with the following custom attributes:</span></span>  
  
```  
System.Security.SuppressUnmanagedCodeSecurityAttribute  
System.Security.UnverifiableCodeAttribute  
```  
  
### <a name="disallowed-net-framework-apis"></a><span data-ttu-id="6f673-148">禁止的 .NET Framework API</span><span class="sxs-lookup"><span data-stu-id="6f673-148">Disallowed .NET Framework APIs</span></span>  
 <span data-ttu-id="6f673-149">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 不能从安全的和 EXTERNAL_ACCESS 的程序集调用任何用某个不允许的**HostProtectionAttributes**批注的 API。</span><span class="sxs-lookup"><span data-stu-id="6f673-149">Any [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] API that is annotated with one of the disallowed **HostProtectionAttributes** cannot be called from SAFE and EXTERNAL_ACCESS assemblies.</span></span>  
  
```  
eSelfAffectingProcessMgmt  
eSelfAffectingThreading  
eSynchronization  
eSharedState   
eExternalProcessMgmt  
eExternalThreading  
eSecurityInfrastructure  
eMayLeakOnAbort  
eUI  
```  
  
### <a name="supported-net-framework-assemblies"></a><span data-ttu-id="6f673-150">支持的 .NET Framework 程序集</span><span class="sxs-lookup"><span data-stu-id="6f673-150">Supported .NET Framework Assemblies</span></span>  
 <span data-ttu-id="6f673-151">必须使用 CREATE ASSEMBLY 将自定义程序集引用的任何程序集都加载到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="6f673-151">Any assembly that is referenced by your custom assembly must be loaded into [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using CREATE ASSEMBLY.</span></span> <span data-ttu-id="6f673-152">下列 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 程序集已经加载到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，因此，它们可以由自定义程序集引用，而不必使用 CREATE ASSEMBLY。</span><span class="sxs-lookup"><span data-stu-id="6f673-152">The following [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] assemblies are already loaded into [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and, therefore, can be referenced by custom assemblies without having to use CREATE ASSEMBLY.</span></span>  
  
```  
custommarshallers.dll  
Microsoft.visualbasic.dll  
Microsoft.visualc.dll  
mscorlib.dll  
system.data.dll  
System.Data.SqlXml.dll  
system.dll  
system.security.dll  
system.web.services.dll  
system.xml.dll  
System.Transactions  
System.Data.OracleClient  
System.Configuration  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f673-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6f673-153">See Also</span></span>  
 <span data-ttu-id="6f673-154">[程序集 &#40;数据库引擎&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="6f673-154">[Assemblies &#40;Database Engine&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span></span>  
 [<span data-ttu-id="6f673-155">CLR 集成安全性</span><span class="sxs-lookup"><span data-stu-id="6f673-155">CLR Integration Security</span></span>](security/clr-integration-security.md)  
  
  
