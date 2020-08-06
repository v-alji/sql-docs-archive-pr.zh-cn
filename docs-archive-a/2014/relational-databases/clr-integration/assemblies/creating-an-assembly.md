---
title: 创建程序集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- creating assemblies
- UNSAFE assemblies
- CREATE ASSEMBLY statement
- SAFE assemblies
- EXTERNAL_ACCESS assemblies
- assemblies [CLR integration], creating
ms.assetid: a2bc503d-b6b2-4963-8beb-c11c323f18e0
author: rothja
ms.author: jroth
ms.openlocfilehash: 9dea1f8fe57691f05274cac353a1064420309e06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691241"
---
# <a name="creating-an-assembly"></a><span data-ttu-id="f72e5-102">创建程序集</span><span class="sxs-lookup"><span data-stu-id="f72e5-102">Creating an Assembly</span></span>
  <span data-ttu-id="f72e5-103">托管数据库对象（如存储过程或触发器）先经过编译，然后部署到称为程序集的单元中。</span><span class="sxs-lookup"><span data-stu-id="f72e5-103">Managed database objects, such as stored procedures or triggers, are compiled and then deployed in units called an assembly.</span></span> <span data-ttu-id="f72e5-104">托管 DLL 程序集必须在中注册， [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] 然后才能使用程序集提供的功能。</span><span class="sxs-lookup"><span data-stu-id="f72e5-104">Managed DLL assemblies must be registered in [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] before the functionality the assembly provides can be used.</span></span> <span data-ttu-id="f72e5-105">若要在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库中注册程序集，请使用 CREATE ASSEMBLY 语句。</span><span class="sxs-lookup"><span data-stu-id="f72e5-105">To register an assembly in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database, use the CREATE ASSEMBLY statement.</span></span> <span data-ttu-id="f72e5-106">本主题讨论如何使用 CREATE ASSEMBLY 语句在数据库中注册程序集，以及如何为程序集指定安全设置。</span><span class="sxs-lookup"><span data-stu-id="f72e5-106">This topic discusses how to register an assembly in a database using the CREATE ASSEMBLY statement, and how to specify the security settings for the assembly.</span></span>  
  
## <a name="the-create-assembly-statement"></a><span data-ttu-id="f72e5-107">CREATE ASSEMBLY 语句</span><span class="sxs-lookup"><span data-stu-id="f72e5-107">The CREATE ASSEMBLY Statement</span></span>  
 <span data-ttu-id="f72e5-108">CREATE ASSEMBLY 语句用于在数据库中创建程序集。</span><span class="sxs-lookup"><span data-stu-id="f72e5-108">The CREATE ASSEMBLY statement is used to create an assembly in a database.</span></span> <span data-ttu-id="f72e5-109">以下是示例：</span><span class="sxs-lookup"><span data-stu-id="f72e5-109">Here is an example:</span></span>  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 <span data-ttu-id="f72e5-110">FROM 子句指定要创建的程序集的路径名。</span><span class="sxs-lookup"><span data-stu-id="f72e5-110">The FROM clause specifies the pathname of the assembly to create.</span></span> <span data-ttu-id="f72e5-111">此路径既可以是通用命名约定 (UNC) 路径，也可以是计算机本地的物理文件路径。</span><span class="sxs-lookup"><span data-stu-id="f72e5-111">This path can either be a Universal Naming Convention (UNC) path or a physical file path that is local to the machine.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="f72e5-112">不允许使用相同的名称、区域性和公钥来注册程序集的不同版本。</span><span class="sxs-lookup"><span data-stu-id="f72e5-112">does not allow registering different versions of an assembly with the same name, culture and public key.</span></span>  
  
 <span data-ttu-id="f72e5-113">可以创建引用其他程序集的程序集。</span><span class="sxs-lookup"><span data-stu-id="f72e5-113">It is possible to create assemblies that reference other assemblies.</span></span> <span data-ttu-id="f72e5-114">当在中创建程序集时 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，如果未在数据库中创建引用的程序集，则还会创建根级别程序集所引用的程序集。</span><span class="sxs-lookup"><span data-stu-id="f72e5-114">When an assembly is created in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] also creates the assemblies referenced by the root-level assembly, if the referenced assemblies are not already created into the database.</span></span>  
  
 <span data-ttu-id="f72e5-115">将向数据库用户或用户角色授予在数据库中创建进而拥有程序集的权限。</span><span class="sxs-lookup"><span data-stu-id="f72e5-115">Database users or user roles are given permissions to create, and thereby own, assemblies in a database.</span></span> <span data-ttu-id="f72e5-116">为了创建程序集，数据库用户或角色应具有 CREATE ASSEMBLY 权限。</span><span class="sxs-lookup"><span data-stu-id="f72e5-116">In order to create assemblies, the database user or role should have the CREATE ASSEMBLY permission.</span></span>  
  
 <span data-ttu-id="f72e5-117">仅当满足以下条件时，程序集才能成功地引用其他程序集：</span><span class="sxs-lookup"><span data-stu-id="f72e5-117">An assembly can only succeed in referencing other assemblies if:</span></span>  
  
-   <span data-ttu-id="f72e5-118">所调用或被引用的程序集由同一个用户或角色所有。</span><span class="sxs-lookup"><span data-stu-id="f72e5-118">The assembly that is called or referenced is owned by the same user or role.</span></span>  
  
-   <span data-ttu-id="f72e5-119">所调用或被引用的程序集是在同一个数据库中创建的。</span><span class="sxs-lookup"><span data-stu-id="f72e5-119">The assembly that is called or referenced was created in the same database.</span></span>  
  
## <a name="specifying-security-when-creating-assemblies"></a><span data-ttu-id="f72e5-120">创建程序集时指定安全性</span><span class="sxs-lookup"><span data-stu-id="f72e5-120">Specifying Security When Creating Assemblies</span></span>  
 <span data-ttu-id="f72e5-121">当在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库中创建程序集时，可以指定您的代码可在以下三种安全级别的哪一种下运行：`SAFE`、`EXTERNAL_ACCESS` 或 `UNSAFE`。</span><span class="sxs-lookup"><span data-stu-id="f72e5-121">When creating an assembly into a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database, you can specify one of three different levels of security in which your code can run: `SAFE`, `EXTERNAL_ACCESS`, or `UNSAFE`.</span></span> <span data-ttu-id="f72e5-122">当运行 `CREATE ASSEMBLY` 语句时，会对代码程序集执行某些检查，看看是否存在可能导致程序集无法在服务器上注册的问题。</span><span class="sxs-lookup"><span data-stu-id="f72e5-122">When the `CREATE ASSEMBLY` statement is run, certain checks are performed on the code assembly which may cause the assembly to fail to register on the server.</span></span> <span data-ttu-id="f72e5-123">有关详细信息，请参阅[CodePlex](https://msftengprodsamples.codeplex.com/)上的模拟示例。</span><span class="sxs-lookup"><span data-stu-id="f72e5-123">For more information, see the Impersonation sample on [CodePlex](https://msftengprodsamples.codeplex.com/).</span></span>  
  
 <span data-ttu-id="f72e5-124">`SAFE` 是默认的权限集，适用于绝大多数应用场景。</span><span class="sxs-lookup"><span data-stu-id="f72e5-124">`SAFE` is the default permission set and works for the majority of scenarios.</span></span> <span data-ttu-id="f72e5-125">若要指定给定的安全级别，您可以按如下所示修改 CREATE ASSEMBLY 语句的语法：</span><span class="sxs-lookup"><span data-stu-id="f72e5-125">To specify a given security level, you modify the syntax of the CREATE ASSEMBLY statement as follows:</span></span>  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = SAFE;  
```  
  
 <span data-ttu-id="f72e5-126">也可以通过只是省略上述代码的第三行，使用 `SAFE` 权限集创建程序集：</span><span class="sxs-lookup"><span data-stu-id="f72e5-126">It is also possible to create an assembly with the `SAFE` permission set by simply omitting the third line of code above:</span></span>  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 <span data-ttu-id="f72e5-127">当程序集中的代码在 `SAFE` 权限集下运行时，它只能通过进程中的托管提供程序在服务器内执行计算和数据访问。</span><span class="sxs-lookup"><span data-stu-id="f72e5-127">When code in an assembly runs under the `SAFE` permission set, it can only do computation and data access within the server through the in-process managed provider.</span></span>  
  
### <a name="creating-external_access-and-unsafe-assemblies"></a><span data-ttu-id="f72e5-128">创建 EXTERNAL_ACCESS 和 UNSAFE 程序集</span><span class="sxs-lookup"><span data-stu-id="f72e5-128">Creating EXTERNAL_ACCESS and UNSAFE Assemblies</span></span>  
 <span data-ttu-id="f72e5-129">`EXTERNAL_ACCESS` 适用于代码需要访问服务器之外的资源（如文件、网络、注册表和环境变量）的应用场景。</span><span class="sxs-lookup"><span data-stu-id="f72e5-129">`EXTERNAL_ACCESS` addresses scenarios in which the code needs to access resources outside the server, such as files, network, registry, and environment variables.</span></span> <span data-ttu-id="f72e5-130">只要服务器访问外部资源，它就会模拟调用托管代码的用户的安全上下文。</span><span class="sxs-lookup"><span data-stu-id="f72e5-130">Whenever the server accesses an external resource, it impersonates the security context of the user calling the managed code.</span></span>  
  
 <span data-ttu-id="f72e5-131">`UNSAFE` 代码权限适用的场合为：程序集并非可验证为安全的，或程序集要求进一步访问受限资源（如 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32 API）。</span><span class="sxs-lookup"><span data-stu-id="f72e5-131">`UNSAFE` code permission is for those situations in which an assembly is not verifiably safe or requires additional access to restricted resources, such as the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32 API.</span></span>  
  
 <span data-ttu-id="f72e5-132">为了在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中创建 `EXTERNAL_ACCESS` 或 `UNSAFE` 程序集，必须满足以下两个条件：</span><span class="sxs-lookup"><span data-stu-id="f72e5-132">To create an `EXTERNAL_ACCESS` or `UNSAFE` assembly in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], one of the following two conditions must be met:</span></span>  
  
1.  <span data-ttu-id="f72e5-133">程序集经过了强名称签名或使用证书进行了 Authenticode 签名。</span><span class="sxs-lookup"><span data-stu-id="f72e5-133">The assembly is strong name signed or Authenticode signed with a certificate.</span></span> <span data-ttu-id="f72e5-134">此强名称（或证书）在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 内部作为非对称密钥（或证书）创建，它具有对应的带有 `EXTERNAL ACCESS ASSEMBLY` 权限（对于外部访问程序集）或 `UNSAFE ASSEMBLY` 权限（对于不安全的程序集）的登录名。</span><span class="sxs-lookup"><span data-stu-id="f72e5-134">This strong name (or certificate) is created inside [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as an asymmetric key (or certificate), and has a corresponding login with `EXTERNAL ACCESS ASSEMBLY` permission (for external access assemblies) or `UNSAFE ASSEMBLY` permission (for unsafe assemblies).</span></span>  
  
2.  <span data-ttu-id="f72e5-135">数据库所有者 (DBO) 已 `EXTERNAL ACCESS ASSEMBLY` (程序 `EXTERNAL ACCESS` 集) 或 `UNSAFE ASSEMBLY` (`UNSAFE` 程序集) 权限，并且数据库已将[可信数据库属性](../../security/trustworthy-database-property.md)设置为 `ON` 。</span><span class="sxs-lookup"><span data-stu-id="f72e5-135">The database owner (DBO) has `EXTERNAL ACCESS ASSEMBLY` (for `EXTERNAL ACCESS` assemblies) or `UNSAFE ASSEMBLY` (for `UNSAFE` assemblies) permission, and the database has the [TRUSTWORTHY Database Property](../../security/trustworthy-database-property.md) set to `ON`.</span></span>  
  
 <span data-ttu-id="f72e5-136">在加载程序集（包括执行）时，也将检查上面所列的两个条件。</span><span class="sxs-lookup"><span data-stu-id="f72e5-136">The two conditions listed above are also checked at assembly load time (which includes execution).</span></span> <span data-ttu-id="f72e5-137">至少必须满足这些条件之一才能加载程序集。</span><span class="sxs-lookup"><span data-stu-id="f72e5-137">At least one of the conditions must be met in order to load the assembly.</span></span>  
  
 <span data-ttu-id="f72e5-138">建议不要将数据库上的 "[可信数据库" 属性](../../security/trustworthy-database-property.md)设置为 `ON` 仅在服务器进程中 (CLR) 代码中运行公共语言运行时。</span><span class="sxs-lookup"><span data-stu-id="f72e5-138">We recommend that the [TRUSTWORTHY Database Property](../../security/trustworthy-database-property.md) on a database not be set to `ON` only to run common language runtime (CLR) code in the server process.</span></span> <span data-ttu-id="f72e5-139">而是建议在 master 数据库中通过程序集文件创建非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="f72e5-139">Instead, we recommend that an asymmetric key be created from the assembly file in the master database.</span></span> <span data-ttu-id="f72e5-140">然后，必须创建映射到此非对称密钥的登录名，并且必须向此登录名授予 `EXTERNAL ACCESS ASSEMBLY` 或 `UNSAFE ASSEMBLY` 权限。</span><span class="sxs-lookup"><span data-stu-id="f72e5-140">A login mapped to this asymmetric key must then be created, and the login must be granted `EXTERNAL ACCESS ASSEMBLY` or `UNSAFE ASSEMBLY` permission.</span></span>  
  
 <span data-ttu-id="f72e5-141">[!INCLUDE[tsql](../../../includes/tsql-md.md)]运行 CREATE ASSEMBLY 语句之前的以下语句。</span><span class="sxs-lookup"><span data-stu-id="f72e5-141">The following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements before running the CREATE ASSEMBLY statement.</span></span>  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll'     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey     
GRANT EXTERNAL ACCESS ASSEMBLY TO SQLCLRTestLogin;   
GO   
```  
  
> [!NOTE]  
>  <span data-ttu-id="f72e5-142">必须创建新的登录名以与非对称密钥关联。</span><span class="sxs-lookup"><span data-stu-id="f72e5-142">You must create a new login to associate with the asymmetric key.</span></span> <span data-ttu-id="f72e5-143">此登录名仅用于授予权限；不必与用户关联或在应用程序中使用。</span><span class="sxs-lookup"><span data-stu-id="f72e5-143">This login is only used to grant permissions; it does not have to be associated with a user, or used within the application.</span></span>  
  
 <span data-ttu-id="f72e5-144">若要创建 `EXTERNAL ACCESS` 程序集，创建者需要具有 `EXTERNAL ACCESS` 权限。</span><span class="sxs-lookup"><span data-stu-id="f72e5-144">To create an `EXTERNAL ACCESS` assembly, the creator needs to have `EXTERNAL ACCESS` permission.</span></span> <span data-ttu-id="f72e5-145">此权限在创建程序集时指定：</span><span class="sxs-lookup"><span data-stu-id="f72e5-145">This is specified when creating the assembly:</span></span>  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
```  
  
 <span data-ttu-id="f72e5-146">[!INCLUDE[tsql](../../../includes/tsql-md.md)]运行 CREATE ASSEMBLY 语句之前的以下语句。</span><span class="sxs-lookup"><span data-stu-id="f72e5-146">The following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements before running the CREATE ASSEMBLY statement.</span></span>  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll';     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey ;    
GRANT UNSAFE ASSEMBLY TO SQLCLRTestLogin ;  
GO  
```  
  
 <span data-ttu-id="f72e5-147">若要指定使用 `UNSAFE` 权限加载程序集，则当将程序集加载到服务器时，应指定 `UNSAFE` 权限集。</span><span class="sxs-lookup"><span data-stu-id="f72e5-147">To specify that an assembly loads with `UNSAFE` permission, you specify the `UNSAFE` permission set when loading the assembly into the server:</span></span>  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = UNSAFE;  
```  
  
 <span data-ttu-id="f72e5-148">有关每个设置的权限的详细信息，请参阅[CLR 集成安全性](../security/clr-integration-security.md)。</span><span class="sxs-lookup"><span data-stu-id="f72e5-148">For more details about the permissions for each of the settings, see [CLR Integration Security](../security/clr-integration-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f72e5-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f72e5-149">See Also</span></span>  
 <span data-ttu-id="f72e5-150">[管理 CLR 集成程序集](managing-clr-integration-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="f72e5-150">[Managing CLR Integration Assemblies](managing-clr-integration-assemblies.md) </span></span>  
 <span data-ttu-id="f72e5-151">[更改程序集](altering-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="f72e5-151">[Altering an Assembly](altering-an-assembly.md) </span></span>  
 <span data-ttu-id="f72e5-152">[删除程序集](dropping-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="f72e5-152">[Dropping an Assembly](dropping-an-assembly.md) </span></span>  
 <span data-ttu-id="f72e5-153">[CLR 集成代码访问安全性](../security/clr-integration-code-access-security.md) </span><span class="sxs-lookup"><span data-stu-id="f72e5-153">[CLR Integration Code Access Security](../security/clr-integration-code-access-security.md) </span></span>  
 <span data-ttu-id="f72e5-154">[TRUSTWORTHY 数据库属性](../../security/trustworthy-database-property.md) </span><span class="sxs-lookup"><span data-stu-id="f72e5-154">[TRUSTWORTHY Database Property](../../security/trustworthy-database-property.md) </span></span>  
 [<span data-ttu-id="f72e5-155">允许部分可信任的调用方</span><span class="sxs-lookup"><span data-stu-id="f72e5-155">Allowing Partially Trusted Callers</span></span>](../../../database-engine/dev-guide/allowing-partially-trusted-callers.md)  
  
