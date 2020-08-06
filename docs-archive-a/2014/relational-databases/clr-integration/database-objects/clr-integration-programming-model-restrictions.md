---
title: CLR 集成编程模型限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], programming model restrictions
- assemblies [CLR integration], CREATE ASSEMBLY checks
- programming model restrictions [CLR integration]
- assemblies [CLR integration], runtime checks
ms.assetid: 2446afc2-9d21-42d3-9847-7733d3074de9
author: rothja
ms.author: jroth
ms.openlocfilehash: 01a32e1460ad9c49061b39b1bdc419c7cd2f1342
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576827"
---
# <a name="clr-integration-programming-model-restrictions"></a><span data-ttu-id="7cf67-102">CLR 集成编程模型限制</span><span class="sxs-lookup"><span data-stu-id="7cf67-102">CLR Integration Programming Model Restrictions</span></span>
  <span data-ttu-id="7cf67-103">在生成托管存储过程或其他托管数据库对象时，通过在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库中首次注册、使用 `CREATE ASSEMBLY` 语句以及在运行时执行检查，可执行某些代码检查。</span><span class="sxs-lookup"><span data-stu-id="7cf67-103">When you are building a managed stored procedure or other managed database object, there are certain code checks performed by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] performs checks on the managed code assembly when it is first registered in the database, using the `CREATE ASSEMBLY` statement, and also at runtime.</span></span> <span data-ttu-id="7cf67-104">在运行时也将检查托管代码，这是因为在程序集中，也许存在在运行时实际上可能永远无法访问的代码路径。</span><span class="sxs-lookup"><span data-stu-id="7cf67-104">The managed code is also checked at runtime because in an assembly there may be code paths that may never actually be reached at runtime.</span></span>  <span data-ttu-id="7cf67-105">这样一来，在注册第三方程序集时尤其灵活，因为，当存在专门在客户端环境下运行而从不在承载的 CLR 中执行的“不安全”代码时，不会阻塞程序集。</span><span class="sxs-lookup"><span data-stu-id="7cf67-105">This provides flexibility for registering third party assemblies, especially, so that an assembly wouldn't be blocked where there is 'unsafe' code designed to run in a client environment but would never be executed in the hosted CLR.</span></span> <span data-ttu-id="7cf67-106">托管代码必须满足的要求取决于该程序集是注册为 `SAFE` 、 `EXTERNAL_ACCESS` 还是 `UNSAFE` ，还是 `SAFE` 最严格的，如下所示。</span><span class="sxs-lookup"><span data-stu-id="7cf67-106">The requirements that the managed code must meet depend on whether the assembly is registered as `SAFE`, `EXTERNAL_ACCESS`, or `UNSAFE`, `SAFE` being the strictest, and are listed below.</span></span>  
  
 <span data-ttu-id="7cf67-107">除了对托管代码程序集进行了限制，还授予了一些代码安全权限。</span><span class="sxs-lookup"><span data-stu-id="7cf67-107">In addition to restrictions being placed on the managed code assemblies, there are also code security permissions that are granted.</span></span> <span data-ttu-id="7cf67-108">公共语言运行时 (CLR) 支持称为代码访问安全性 (CAS) 的托管代码安全模式。</span><span class="sxs-lookup"><span data-stu-id="7cf67-108">The common language runtime (CLR) supports a security model called code access security (CAS) for managed code.</span></span> <span data-ttu-id="7cf67-109">在这种模式下，根据代码的标识来对程序集授予权限。</span><span class="sxs-lookup"><span data-stu-id="7cf67-109">In this model, permissions are granted to assemblies based on the identity of the code.</span></span> <span data-ttu-id="7cf67-110">`SAFE`、`EXTERNAL_ACCESS` 和 `UNSAFE` 程序集具有不同的 CAS 权限。</span><span class="sxs-lookup"><span data-stu-id="7cf67-110">`SAFE`, `EXTERNAL_ACCESS`, and `UNSAFE` assemblies have different CAS permissions.</span></span> <span data-ttu-id="7cf67-111">有关详细信息，请参阅[CLR 集成代码访问安全性](../security/clr-integration-code-access-security.md)。</span><span class="sxs-lookup"><span data-stu-id="7cf67-111">For more information, see [CLR Integration Code Access Security](../security/clr-integration-code-access-security.md).</span></span>  
  
## <a name="create-assembly-checks"></a><span data-ttu-id="7cf67-112">CREATE ASSEMBLY 检查</span><span class="sxs-lookup"><span data-stu-id="7cf67-112">CREATE ASSEMBLY Checks</span></span>  
 <span data-ttu-id="7cf67-113">运行 `CREATE ASSEMBLY` 语句时，将为每个安全级别执行以下检查。</span><span class="sxs-lookup"><span data-stu-id="7cf67-113">When the `CREATE ASSEMBLY` statement is run, the following checks are performed for each security level.</span></span>  <span data-ttu-id="7cf67-114">如果有任何检查失败，则 `CREATE ASSEMBLY` 也将失败，且显示一条错误消息。</span><span class="sxs-lookup"><span data-stu-id="7cf67-114">If any check fails, `CREATE ASSEMBLY` will fail with an error message.</span></span>  
  
### <a name="global-any-security-level"></a><span data-ttu-id="7cf67-115">全局（任何安全级别）</span><span class="sxs-lookup"><span data-stu-id="7cf67-115">Global (any security level)</span></span>  
 <span data-ttu-id="7cf67-116">所有被引用的程序集都必须满足下列一个或多个条件：</span><span class="sxs-lookup"><span data-stu-id="7cf67-116">All referenced assemblies must meet one or more of the following criteria:</span></span>  
  
-   <span data-ttu-id="7cf67-117">程序集已在数据库中注册。</span><span class="sxs-lookup"><span data-stu-id="7cf67-117">The assembly is already registered in the database.</span></span>  
  
-   <span data-ttu-id="7cf67-118">程序集是受支持的程序集之一。</span><span class="sxs-lookup"><span data-stu-id="7cf67-118">The assembly is one of the supported assemblies.</span></span> <span data-ttu-id="7cf67-119">有关详细信息，请参阅[支持的 .NET Framework 库](supported-net-framework-libraries.md)。</span><span class="sxs-lookup"><span data-stu-id="7cf67-119">For more information, see [Supported .NET Framework Libraries](supported-net-framework-libraries.md).</span></span>  
  
-   <span data-ttu-id="7cf67-120">你使用的是 `CREATE ASSEMBLY FROM` \* \<location> ，\* 并且所有引用的程序集及其依赖项都可以在中使用 *\<location>* 。</span><span class="sxs-lookup"><span data-stu-id="7cf67-120">You are using `CREATE ASSEMBLY FROM`*\<location>,* and all the referenced assemblies and their dependencies are available in *\<location>*.</span></span>  
  
-   <span data-ttu-id="7cf67-121">你使用的是 `CREATE ASSEMBLY FROM` \* \<bytes ...> ，\* 并且所有引用都是通过以空格分隔的字节来指定的。</span><span class="sxs-lookup"><span data-stu-id="7cf67-121">You are using `CREATE ASSEMBLY FROM`*\<bytes ...>,* and all the references are specified via space separated bytes.</span></span>  
  
### <a name="external_access"></a><span data-ttu-id="7cf67-122">EXTERNAL_ACCESS</span><span class="sxs-lookup"><span data-stu-id="7cf67-122">EXTERNAL_ACCESS</span></span>  
 <span data-ttu-id="7cf67-123">所有 `EXTERNAL_ACCESS` 程序集都必须满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="7cf67-123">All `EXTERNAL_ACCESS` assemblies must meet the following criteria:</span></span>  
  
-   <span data-ttu-id="7cf67-124">静态字段不用来存储信息。</span><span class="sxs-lookup"><span data-stu-id="7cf67-124">Static fields are not used to store information.</span></span> <span data-ttu-id="7cf67-125">允许只读静态字段。</span><span class="sxs-lookup"><span data-stu-id="7cf67-125">Read-only static fields are allowed.</span></span>  
  
-   <span data-ttu-id="7cf67-126">PEVerify 测试通过。</span><span class="sxs-lookup"><span data-stu-id="7cf67-126">PEVerify test is passed.</span></span> <span data-ttu-id="7cf67-127">PEVerify 工具 (peverify.exe) 随 .NET Framework SDK 一起提供，该工具可检查 MSIL 代码及关联元数据是否满足类型安全要求。</span><span class="sxs-lookup"><span data-stu-id="7cf67-127">The PEVerify tool (peverify.exe), which checks that the MSIL code and associated metadata meet type safety requirements, is provided with the .NET Framework SDK.</span></span>  
  
-   <span data-ttu-id="7cf67-128">不使用同步，例如与 `SynchronizationAttribute` 类的同步。</span><span class="sxs-lookup"><span data-stu-id="7cf67-128">Synchronization, for example with the `SynchronizationAttribute` class, is not used.</span></span>  
  
-   <span data-ttu-id="7cf67-129">不使用终结器方法。</span><span class="sxs-lookup"><span data-stu-id="7cf67-129">Finalizer methods are not used.</span></span>  
  
 <span data-ttu-id="7cf67-130">在 `EXTERNAL_ACCESS` 程序集中不允许以下自定义属性：</span><span class="sxs-lookup"><span data-stu-id="7cf67-130">The following custom attributes are disallowed in `EXTERNAL_ACCESS` assemblies:</span></span>  
  
-   <span data-ttu-id="7cf67-131">System.ContextStaticAttribute</span><span class="sxs-lookup"><span data-stu-id="7cf67-131">System.ContextStaticAttribute</span></span>  
  
-   <span data-ttu-id="7cf67-132">System.MTAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="7cf67-132">System.MTAThreadAttribute</span></span>  
  
-   <span data-ttu-id="7cf67-133">System.Runtime.CompilerServices.MethodImplAttribute</span><span class="sxs-lookup"><span data-stu-id="7cf67-133">System.Runtime.CompilerServices.MethodImplAttribute</span></span>  
  
-   <span data-ttu-id="7cf67-134">System.Runtime.CompilerServices.CompilationRelaxationsAttribute</span><span class="sxs-lookup"><span data-stu-id="7cf67-134">System.Runtime.CompilerServices.CompilationRelaxationsAttribute</span></span>  
  
-   <span data-ttu-id="7cf67-135">System.Runtime.Remoting.Contexts.ContextAttribute</span><span class="sxs-lookup"><span data-stu-id="7cf67-135">System.Runtime.Remoting.Contexts.ContextAttribute</span></span>  
  
-   <span data-ttu-id="7cf67-136">System.Runtime.Remoting.Contexts.SynchronizationAttribute</span><span class="sxs-lookup"><span data-stu-id="7cf67-136">System.Runtime.Remoting.Contexts.SynchronizationAttribute</span></span>  
  
-   <span data-ttu-id="7cf67-137">System.Runtime.InteropServices.DllImportAttribute</span><span class="sxs-lookup"><span data-stu-id="7cf67-137">System.Runtime.InteropServices.DllImportAttribute</span></span>  
  
-   <span data-ttu-id="7cf67-138">System.Security.Permissions.CodeAccessSecurityAttribute</span><span class="sxs-lookup"><span data-stu-id="7cf67-138">System.Security.Permissions.CodeAccessSecurityAttribute</span></span>  
  
-   <span data-ttu-id="7cf67-139">System.Security.SuppressUnmanagedCodeSecurityAttribute</span><span class="sxs-lookup"><span data-stu-id="7cf67-139">System.Security.SuppressUnmanagedCodeSecurityAttribute</span></span>  
  
-   <span data-ttu-id="7cf67-140">System.Security.UnverifiableCodeAttribute</span><span class="sxs-lookup"><span data-stu-id="7cf67-140">System.Security.UnverifiableCodeAttribute</span></span>  
  
-   <span data-ttu-id="7cf67-141">System.STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="7cf67-141">System.STAThreadAttribute</span></span>  
  
-   <span data-ttu-id="7cf67-142">System.ThreadStaticAttribute</span><span class="sxs-lookup"><span data-stu-id="7cf67-142">System.ThreadStaticAttribute</span></span>  
  
### <a name="safe"></a><span data-ttu-id="7cf67-143">SAFE</span><span class="sxs-lookup"><span data-stu-id="7cf67-143">SAFE</span></span>  
  
-   <span data-ttu-id="7cf67-144">检查所有 `EXTERNAL_ACCESS` 程序集条件。</span><span class="sxs-lookup"><span data-stu-id="7cf67-144">All `EXTERNAL_ACCESS` assembly conditions are checked.</span></span>  
  
## <a name="runtime-checks"></a><span data-ttu-id="7cf67-145">运行时检查</span><span class="sxs-lookup"><span data-stu-id="7cf67-145">Runtime Checks</span></span>  
 <span data-ttu-id="7cf67-146">在运行时，将针对下列条件检查代码程序集。</span><span class="sxs-lookup"><span data-stu-id="7cf67-146">At runtime, the code assembly is checked for the following conditions.</span></span> <span data-ttu-id="7cf67-147">如果发现任何一个条件，则将不允许托管代码运行，且将会引发异常。</span><span class="sxs-lookup"><span data-stu-id="7cf67-147">If any of these conditions are found, the managed code will not be allowed to run and an exception will be thrown.</span></span>  
  
### <a name="unsafe"></a><span data-ttu-id="7cf67-148">UNSAFE</span><span class="sxs-lookup"><span data-stu-id="7cf67-148">UNSAFE</span></span>  
 <span data-ttu-id="7cf67-149">`System.Reflection.Assembly.Load()`不允许通过从字节数组调用方法或通过使用命名空间隐式加载程序集 `Reflection.Emit` 。</span><span class="sxs-lookup"><span data-stu-id="7cf67-149">Loading an assembly-either explicitly by calling the `System.Reflection.Assembly.Load()` method from a byte array, or implicitly through the use of `Reflection.Emit` namespace-is not permitted.</span></span>  
  
### <a name="external_access"></a><span data-ttu-id="7cf67-150">EXTERNAL_ACCESS</span><span class="sxs-lookup"><span data-stu-id="7cf67-150">EXTERNAL_ACCESS</span></span>  
 <span data-ttu-id="7cf67-151">检查所有 `UNSAFE` 条件。</span><span class="sxs-lookup"><span data-stu-id="7cf67-151">All `UNSAFE` conditions are checked.</span></span>  
  
 <span data-ttu-id="7cf67-152">在支持的程序集列表中不允许所有使用以下宿主保护属性 (HPA) 值批注的类型和方法。</span><span class="sxs-lookup"><span data-stu-id="7cf67-152">All types and methods annotated with the following host protection attribute (HPA) values in the supported list of assemblies are disallowed.</span></span>  
  
-   <span data-ttu-id="7cf67-153">SelfAffectingProcessMgmt</span><span class="sxs-lookup"><span data-stu-id="7cf67-153">SelfAffectingProcessMgmt</span></span>  
  
-   <span data-ttu-id="7cf67-154">SelfAffectingThreading</span><span class="sxs-lookup"><span data-stu-id="7cf67-154">SelfAffectingThreading</span></span>  
  
-   <span data-ttu-id="7cf67-155">同步</span><span class="sxs-lookup"><span data-stu-id="7cf67-155">Synchronization</span></span>  
  
-   <span data-ttu-id="7cf67-156">SharedState</span><span class="sxs-lookup"><span data-stu-id="7cf67-156">SharedState</span></span>  
  
-   <span data-ttu-id="7cf67-157">ExternalProcessMgmt</span><span class="sxs-lookup"><span data-stu-id="7cf67-157">ExternalProcessMgmt</span></span>  
  
-   <span data-ttu-id="7cf67-158">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="7cf67-158">ExternalThreading</span></span>  
  
-   <span data-ttu-id="7cf67-159">SecurityInfrastructure</span><span class="sxs-lookup"><span data-stu-id="7cf67-159">SecurityInfrastructure</span></span>  
  
-   <span data-ttu-id="7cf67-160">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="7cf67-160">MayLeakOnAbort</span></span>  
  
-   <span data-ttu-id="7cf67-161">UI</span><span class="sxs-lookup"><span data-stu-id="7cf67-161">UI</span></span>  
  
 <span data-ttu-id="7cf67-162">有关 Hpa 的详细信息以及支持的程序集中不允许的类型和成员的列表，请参阅[宿主保护属性和 CLR 集成编程](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="7cf67-162">For more information about HPAs and a list of disallowed types and members in the supported assemblies, see [Host Protection Attributes and CLR Integration Programming](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md).</span></span>  
  
### <a name="safe"></a><span data-ttu-id="7cf67-163">SAFE</span><span class="sxs-lookup"><span data-stu-id="7cf67-163">SAFE</span></span>  
 <span data-ttu-id="7cf67-164">检查所有 `EXTERNAL_ACCESS` 条件。</span><span class="sxs-lookup"><span data-stu-id="7cf67-164">All `EXTERNAL_ACCESS` conditions are checked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cf67-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7cf67-165">See Also</span></span>  
 <span data-ttu-id="7cf67-166">[支持的 .NET Framework 库](supported-net-framework-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="7cf67-166">[Supported .NET Framework Libraries](supported-net-framework-libraries.md) </span></span>  
 <span data-ttu-id="7cf67-167">[CLR 集成代码访问安全性](../security/clr-integration-code-access-security.md) </span><span class="sxs-lookup"><span data-stu-id="7cf67-167">[CLR Integration Code Access Security](../security/clr-integration-code-access-security.md) </span></span>  
 <span data-ttu-id="7cf67-168">[宿主保护属性和 CLR 集成编程](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md) </span><span class="sxs-lookup"><span data-stu-id="7cf67-168">[Host Protection Attributes and CLR Integration Programming](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md) </span></span>  
 [<span data-ttu-id="7cf67-169">创建程序集</span><span class="sxs-lookup"><span data-stu-id="7cf67-169">Creating an Assembly</span></span>](../assemblies/creating-an-assembly.md)  
  
  
