---
title: 在 SQL Server 中注册用户定义类型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- UDTs [CLR integration], maintaining
- user-defined types [CLR integration], maintaining
- dependencies [CLR integration]
- deploying user-defined types [CLR integration]
- CurrencyConversion function
- user-defined types [CLR integration], deploying
- Transact-SQL deploying UDTs
- assemblies [CLR integration], user-defined types
- cross-database UDT support
- CREATE ASSEMBLY statement
- DROP TYPE statement
- Currency UDT
- CREATE TYPE statement
- registering user-defined types
- UDTs [CLR integration], deploying
- removing user-defined types
- user-defined types [CLR integration], registering
- ALTER ASSEMBLY statement
- UDTs [CLR integration], registering
- ADD FILE clause
ms.assetid: f7da3e92-e407-4f0b-b3a3-f214e442b37d
author: rothja
ms.author: jroth
ms.openlocfilehash: 7d24f7948e093335eff708f3c4a8a7361cfc156f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578906"
---
# <a name="registering-user-defined-types-in-sql-server"></a><span data-ttu-id="3cb76-102">在 SQL Server 中注册用户定义类型</span><span class="sxs-lookup"><span data-stu-id="3cb76-102">Registering User-Defined Types in SQL Server</span></span>
  <span data-ttu-id="3cb76-103">若要在中使用用户定义类型 (UDT) [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，必须注册该类型。</span><span class="sxs-lookup"><span data-stu-id="3cb76-103">In order to use a user-defined type (UDT) in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must register it.</span></span> <span data-ttu-id="3cb76-104">注册一个 UDT 涉及两个步骤：在要使用它的数据库中注册程序集和创建该类型。</span><span class="sxs-lookup"><span data-stu-id="3cb76-104">Registering a UDT involves registering the assembly and creating the type in the database in which you wish to use it.</span></span> <span data-ttu-id="3cb76-105">UDT 的作用域仅限单个数据库，不能在多个数据库中使用，除非在各个数据库中注册相同的程序集和 UDT。</span><span class="sxs-lookup"><span data-stu-id="3cb76-105">UDTs are scoped to a single database, and cannot be used in multiple databases unless the identical assembly and UDT are registered with each database.</span></span> <span data-ttu-id="3cb76-106">一旦注册 UDT 程序集并创建了该类型，即可在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 和客户端代码中使用 UDT。</span><span class="sxs-lookup"><span data-stu-id="3cb76-106">Once the UDT assembly is registered and the type created, you can use the UDT in [!INCLUDE[tsql](../../includes/tsql-md.md)] and in client code.</span></span> <span data-ttu-id="3cb76-107">有关详细信息，请参阅 [CLR 用户定义类型](clr-user-defined-types.md)。</span><span class="sxs-lookup"><span data-stu-id="3cb76-107">For more information, see [CLR User-Defined Types](clr-user-defined-types.md).</span></span>  
  
## <a name="using-visual-studio-to-deploy-udts"></a><span data-ttu-id="3cb76-108">使用 Visual Studio 部署 UDT</span><span class="sxs-lookup"><span data-stu-id="3cb76-108">Using Visual Studio to Deploy UDTs</span></span>  
 <span data-ttu-id="3cb76-109">部署 UDT 的最简单方法是使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="3cb76-109">The easiest way to deploy your UDT is by using [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio.</span></span> <span data-ttu-id="3cb76-110">不过，对于更为复杂的部署方案，同时为尽量提高灵活性，应使用本主题下文介绍的 [!INCLUDE[tsql](../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3cb76-110">For more complex deployment scenarios and the greatest flexibility, however, use [!INCLUDE[tsql](../../includes/tsql-md.md)] as discussed later in this topic.</span></span>  
  
 <span data-ttu-id="3cb76-111">遵照以下步骤使用 Visual Studio 创建和部署 UDT：</span><span class="sxs-lookup"><span data-stu-id="3cb76-111">Follow these steps to create and deploy a UDT using Visual Studio:</span></span>  
  
1.  <span data-ttu-id="3cb76-112">在**Visual Basic**或**Visual c #** 语言节点中创建新的**数据库**项目。</span><span class="sxs-lookup"><span data-stu-id="3cb76-112">Create a new **Database** project in the **Visual Basic** or **Visual C#** language nodes.</span></span>  
  
2.  <span data-ttu-id="3cb76-113">向将要包含该 UDT 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库添加引用。</span><span class="sxs-lookup"><span data-stu-id="3cb76-113">Add a reference to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that will contain the UDT.</span></span>  
  
3.  <span data-ttu-id="3cb76-114">添加**用户定义类型**类。</span><span class="sxs-lookup"><span data-stu-id="3cb76-114">Add a **User-Defined Type** class.</span></span>  
  
4.  <span data-ttu-id="3cb76-115">编写用于实现该 UDT 的代码。</span><span class="sxs-lookup"><span data-stu-id="3cb76-115">Write code to implement the UDT.</span></span>  
  
5.  <span data-ttu-id="3cb76-116">在 "**生成**" 菜单中，选择 "**部署**"。</span><span class="sxs-lookup"><span data-stu-id="3cb76-116">From the **Build** menu, select **Deploy**.</span></span> <span data-ttu-id="3cb76-117">这样即可在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库中注册该程序集并创建该类型。</span><span class="sxs-lookup"><span data-stu-id="3cb76-117">This registers the assembly and creates the type in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
## <a name="using-transact-sql-to-deploy-udts"></a><span data-ttu-id="3cb76-118">使用 Transact-SQL 部署 UDT</span><span class="sxs-lookup"><span data-stu-id="3cb76-118">Using Transact-SQL to Deploy UDTs</span></span>  
 <span data-ttu-id="3cb76-119">使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY 语法可以在您希望使用 UDT 的数据库中注册程序集。</span><span class="sxs-lookup"><span data-stu-id="3cb76-119">The [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY syntax is used to register the assembly in the database in which you wish to use the UDT.</span></span> <span data-ttu-id="3cb76-120">该程序集存储在内部的数据库系统表中，而不是存储在外部的文件系统中。</span><span class="sxs-lookup"><span data-stu-id="3cb76-120">It is stored internally in database system tables, not externally in the file system.</span></span> <span data-ttu-id="3cb76-121">如果 UDT 依赖于外部程序集，则必须将这些程序集也加载到数据库中。</span><span class="sxs-lookup"><span data-stu-id="3cb76-121">If the UDT is dependent on external assemblies, they too must be loaded into the database.</span></span> <span data-ttu-id="3cb76-122">使用 CREATE TYPE 语句可以在要使用 UDT 的数据库中创建该 UDT。</span><span class="sxs-lookup"><span data-stu-id="3cb76-122">The CREATE TYPE statement is used to create the UDT in the database in which it is to be used.</span></span> <span data-ttu-id="3cb76-123">有关详细信息，请参阅[CREATE ASSEMBLY &#40;transact-sql&#41;](/sql/t-sql/statements/create-assembly-transact-sql)和[Create TYPE &#40;transact-sql&#41;](/sql/t-sql/statements/create-type-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3cb76-123">For more information, see [CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql) and [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql).</span></span>  
  
### <a name="using-create-assembly"></a><span data-ttu-id="3cb76-124">使用 ASSEMBLY</span><span class="sxs-lookup"><span data-stu-id="3cb76-124">Using CREATE ASSEMBLY</span></span>  
 <span data-ttu-id="3cb76-125">使用 CREATE ASSEMBLY 语法可以在要使用 UDT 的数据库中注册程序集。</span><span class="sxs-lookup"><span data-stu-id="3cb76-125">The CREATE ASSEMBLY syntax registers the assembly in the database in which you wish to use the UDT.</span></span> <span data-ttu-id="3cb76-126">经过注册的程序集不具有任何依赖关系。</span><span class="sxs-lookup"><span data-stu-id="3cb76-126">Once the assembly is registered, it has no dependencies.</span></span>  
  
 <span data-ttu-id="3cb76-127">不允许在给定数据库中创建同一程序集的多个版本。</span><span class="sxs-lookup"><span data-stu-id="3cb76-127">Creating multiple versions of the same assembly in a given database is not allowed.</span></span> <span data-ttu-id="3cb76-128">不过，可以基于给定数据库的区域性创建同一程序集的多个版本。</span><span class="sxs-lookup"><span data-stu-id="3cb76-128">However, it is possible to create multiple versions of the same assembly based on culture in a given database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3cb76-129">通过在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中注册的不同程序集名称来区分程序集的多个区域性版本。</span><span class="sxs-lookup"><span data-stu-id="3cb76-129">distinguishes multiple culture versions of an assembly by different names as registered in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3cb76-130">有关详细信息，请参阅 .NET Framework SDK 中的“创建和使用具有强名称的程序集”。</span><span class="sxs-lookup"><span data-stu-id="3cb76-130">For more information, see "Creating and Using Strong-Named Assemblies" in the .NET Framework SDK.</span></span>  
  
 <span data-ttu-id="3cb76-131">在权限集设置为 SAFE 或 EXTERNAL_ACCESS 的情况下执行 CREATE ASSEMBLY 时，将检查程序集，确保其可验证并且是类型安全的。</span><span class="sxs-lookup"><span data-stu-id="3cb76-131">When CREATE ASSEMBLY is executed with the SAFE or EXTERNAL_ACCESS permission sets, the assembly is checked to make sure that it is verifiable and type safe.</span></span> <span data-ttu-id="3cb76-132">如果未指定权限集，则假定为 SAFE。</span><span class="sxs-lookup"><span data-stu-id="3cb76-132">If you omit specifying a permission set, SAFE is assumed.</span></span> <span data-ttu-id="3cb76-133">不检查权限集为 UNSAFE 的代码。</span><span class="sxs-lookup"><span data-stu-id="3cb76-133">Code with the UNSAFE permission set is not checked.</span></span> <span data-ttu-id="3cb76-134">有关程序集的权限集的详细信息，请参阅[设计程序集](../../relational-databases/clr-integration/assemblies-designing.md)。</span><span class="sxs-lookup"><span data-stu-id="3cb76-134">For more information about assembly permission sets, see [Designing Assemblies](../../relational-databases/clr-integration/assemblies-designing.md).</span></span>  
  
#### <a name="example"></a><span data-ttu-id="3cb76-135">示例</span><span class="sxs-lookup"><span data-stu-id="3cb76-135">Example</span></span>  
 <span data-ttu-id="3cb76-136">下面的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **AdventureWorks**数据库中，用 SAFE 权限集注册 Point 程序集。</span><span class="sxs-lookup"><span data-stu-id="3cb76-136">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement registers the Point assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the **AdventureWorks** database, with the SAFE permission set.</span></span> <span data-ttu-id="3cb76-137">如果省略 WITH PERMISSION_SET 子句，将使用 SAFE 权限集注册该程序集。</span><span class="sxs-lookup"><span data-stu-id="3cb76-137">If the WITH PERMISSION_SET clause is omitted, the assembly is registered with the SAFE permission set.</span></span>  
  
```  
USE AdventureWorks;  
CREATE ASSEMBLY Point  
FROM '\\ShareName\Projects\Point\bin\Point.dll'   
WITH PERMISSION_SET = SAFE;  
```  
  
 <span data-ttu-id="3cb76-138">以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句使用 FROM 子句中的 *<assembly_bits>* 参数注册程序集。</span><span class="sxs-lookup"><span data-stu-id="3cb76-138">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement registers the assembly using *<assembly_bits>* argument in the FROM clause.</span></span> <span data-ttu-id="3cb76-139">此 `varbinary` 值将文件表示为字节流。</span><span class="sxs-lookup"><span data-stu-id="3cb76-139">This `varbinary` value represents the file as a stream of bytes.</span></span>  
  
```  
USE AdventureWorks;  
CREATE ASSEMBLY Point  
FROM 0xfeac4 ... 21ac78  
```  
  
### <a name="using-create-type"></a><span data-ttu-id="3cb76-140">使用 CREATE TYPE</span><span class="sxs-lookup"><span data-stu-id="3cb76-140">Using CREATE TYPE</span></span>  
 <span data-ttu-id="3cb76-141">一旦将程序集加载到数据库中，随后即可使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TYPE 语句创建该类型。</span><span class="sxs-lookup"><span data-stu-id="3cb76-141">Once the assembly is loaded into the database, you can then create the type using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TYPE statement.</span></span> <span data-ttu-id="3cb76-142">这样即可将该类型添加到该数据库的可用类型列表中。</span><span class="sxs-lookup"><span data-stu-id="3cb76-142">This adds the type to the list of available types for that database.</span></span> <span data-ttu-id="3cb76-143">该类型的作用域为数据库，并且只能在创建该类型的数据库中使用。</span><span class="sxs-lookup"><span data-stu-id="3cb76-143">The type has database scope and the type can only be used in the database in which it was created.</span></span> <span data-ttu-id="3cb76-144">如果数据库中已存在 UDT，CREATE TYPE 语句将失败，并且生成错误。</span><span class="sxs-lookup"><span data-stu-id="3cb76-144">If the UDT already exists in the database, the CREATE TYPE statement fails with an error.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3cb76-145">CREATE TYPE 语法还用于创建本机 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 别名数据类型，且旨在取代 `sp_addtype` 作为创建别名数据类型的一种方式。</span><span class="sxs-lookup"><span data-stu-id="3cb76-145">The CREATE TYPE syntax is also used for creating native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alias data types, and is intended to replace `sp_addtype` as a means of creating alias data types.</span></span> <span data-ttu-id="3cb76-146">CREATE TYPE 语法中的某些可选参数与创建 UDT 有关，不适用于创建别名数据类型（如基类型）。</span><span class="sxs-lookup"><span data-stu-id="3cb76-146">Some of the optional arguments in the CREATE TYPE syntax refer to creating UDTs, and are not applicable to creating alias data types (such as base type).</span></span>  
  
 <span data-ttu-id="3cb76-147">有关详细信息，请参阅[CREATE TYPE &#40;transact-sql&#41;](/sql/t-sql/statements/create-type-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3cb76-147">For more information, see [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql).</span></span>  
  
#### <a name="example"></a><span data-ttu-id="3cb76-148">示例</span><span class="sxs-lookup"><span data-stu-id="3cb76-148">Example</span></span>  
 <span data-ttu-id="3cb76-149">以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句创建 `Point` 类型。</span><span class="sxs-lookup"><span data-stu-id="3cb76-149">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement creates the `Point` type.</span></span> <span data-ttu-id="3cb76-150">使用*AssemblyName*的由两部分组成的命名语法指定外部名称。*UDTName*。</span><span class="sxs-lookup"><span data-stu-id="3cb76-150">The EXTERNAL NAME is specified using the two-part naming syntax of *AssemblyName*.*UDTName*.</span></span>  
  
```  
CREATE TYPE dbo.Point   
EXTERNAL NAME Point.[Point];  
```  
  
## <a name="removing-a-udt-from-the-database"></a><span data-ttu-id="3cb76-151">从数据库中删除 UDT</span><span class="sxs-lookup"><span data-stu-id="3cb76-151">Removing a UDT from the Database</span></span>  
 <span data-ttu-id="3cb76-152">使用 DROP TYPE 语句从当前数据库中删除 UDT。</span><span class="sxs-lookup"><span data-stu-id="3cb76-152">The DROP TYPE statement removes a UDT from the current database.</span></span> <span data-ttu-id="3cb76-153">删除了 UDT 之后，可使用 DROP ASSEMBLY 语句从数据库中删除程序集。</span><span class="sxs-lookup"><span data-stu-id="3cb76-153">Once a UDT is dropped, you can use the DROP ASSEMBLY statement to drop the assembly from the database.</span></span>  
  
 <span data-ttu-id="3cb76-154">在以下情况下不执行 DROP TYPE 语句。</span><span class="sxs-lookup"><span data-stu-id="3cb76-154">The DROP TYPE statement does not execute in the following situations:</span></span>  
  
-   <span data-ttu-id="3cb76-155">数据库中的表包含使用 UDT 定义的列。</span><span class="sxs-lookup"><span data-stu-id="3cb76-155">Tables in the database that contain columns defined using the UDT.</span></span>  
  
-   <span data-ttu-id="3cb76-156">在数据库中使用 WITH SCHEMABINDING 子句创建了使用 UDT 变量或参数的函数、存储过程或触发器。</span><span class="sxs-lookup"><span data-stu-id="3cb76-156">Functions, stored procedures, or triggers that use variables or parameters of the UDT, created in the database with the WITH SCHEMABINDING clause.</span></span>  
  
### <a name="example"></a><span data-ttu-id="3cb76-157">示例</span><span class="sxs-lookup"><span data-stu-id="3cb76-157">Example</span></span>  
 <span data-ttu-id="3cb76-158">以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 必须按以下顺序执行。</span><span class="sxs-lookup"><span data-stu-id="3cb76-158">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] must execute in the following order.</span></span> <span data-ttu-id="3cb76-159">首先必须删除引用 `Point` UDT 的表，然后删除类型，最后删除程序集。</span><span class="sxs-lookup"><span data-stu-id="3cb76-159">First the table which references the `Point` UDT must be dropped, then the type, and finally the assembly.</span></span>  
  
```  
DROP TABLE dbo.Points;  
DROP TYPE dbo.Point;  
DROP ASSEMBLY Point;  
```  
  
### <a name="finding-udt-dependencies"></a><span data-ttu-id="3cb76-160">查找 UDT 依赖关系</span><span class="sxs-lookup"><span data-stu-id="3cb76-160">Finding UDT Dependencies</span></span>  
 <span data-ttu-id="3cb76-161">如果存在依赖对象，如具有 UDT 列定义的表，DROP TYPE 语句将失败。</span><span class="sxs-lookup"><span data-stu-id="3cb76-161">If there are dependent objects, such as tables with UDT column definitions, the DROP TYPE statement fails.</span></span> <span data-ttu-id="3cb76-162">如果存在在数据库中用 WITH SCHEMABINDING 子句创建的函数、存储过程或触发器，且这些例程使用用户定义类型的变量或参数，该语句也将失败。</span><span class="sxs-lookup"><span data-stu-id="3cb76-162">It also fails if there are functions, stored procedures, or triggers created in the database using the WITH SCHEMABINDING clause, if these routines use variables or parameters of the user-defined type.</span></span> <span data-ttu-id="3cb76-163">在执行 DROP TYPE 语句之前，首先必须删除所有依赖对象。</span><span class="sxs-lookup"><span data-stu-id="3cb76-163">You must first drop all dependent objects, and then execute the DROP TYPE statement.</span></span>  
  
 <span data-ttu-id="3cb76-164">下面的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询查找使用**AdventureWorks**数据库中的 UDT 的所有列和参数。</span><span class="sxs-lookup"><span data-stu-id="3cb76-164">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] query locates all of the columns and parameters that use a UDT in the **AdventureWorks** database.</span></span>  
  
```  
USE Adventureworks;  
SELECT o.name AS major_name, o.type_desc AS major_type_desc  
     , c.name AS minor_name, c.type_desc AS minor_type_desc  
     , at.assembly_class  
  FROM (  
        SELECT object_id, name, user_type_id, 'SQL_COLUMN' AS type_desc  
          FROM sys.columns  
     UNION ALL  
        SELECT object_id, name, user_type_id, 'SQL_PROCEDURE_PARAMETER'  
          FROM sys.parameters  
     ) AS c  
  JOIN sys.objects AS o  
    ON o.object_id = c.object_id  
  JOIN sys.assembly_types AS at  
    ON at.user_type_id = c.user_type_id;  
```  
  
## <a name="maintaining-udts"></a><span data-ttu-id="3cb76-165">维护 UDT</span><span class="sxs-lookup"><span data-stu-id="3cb76-165">Maintaining UDTs</span></span>  
 <span data-ttu-id="3cb76-166">尽管可以更改 UDT 所基于的程序集，但是一旦在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库中创建了该 UDT 就无法再修改它。</span><span class="sxs-lookup"><span data-stu-id="3cb76-166">You cannot modify a UDT once it is created in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, although you can alter the assembly on which the type is based.</span></span> <span data-ttu-id="3cb76-167">多数情况下，必须使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] DROP TYPE 语句从数据库中删除 UDT、更改基础程序集，然后使用 ALTER ASSEMBLY 语句重新加载它。</span><span class="sxs-lookup"><span data-stu-id="3cb76-167">In most cases, you must remove the UDT from the database with the [!INCLUDE[tsql](../../includes/tsql-md.md)] DROP TYPE statement, make changes to the underlying assembly, and reload it using the ALTER ASSEMBLY statement.</span></span> <span data-ttu-id="3cb76-168">随后还需要重新创建该 UDT 和所有依赖对象。</span><span class="sxs-lookup"><span data-stu-id="3cb76-168">You then need to re-create the UDT and any dependent objects.</span></span>  
  
### <a name="example"></a><span data-ttu-id="3cb76-169">示例</span><span class="sxs-lookup"><span data-stu-id="3cb76-169">Example</span></span>  
 <span data-ttu-id="3cb76-170">在更改 UDT 程序集中的源代码并且重新编译该程序集后，可以使用 ALTER ASSEMBLY 语句。</span><span class="sxs-lookup"><span data-stu-id="3cb76-170">The ALTER ASSEMBLY statement is used after you have made changes to the source code in your UDT assembly and recompiled it.</span></span> <span data-ttu-id="3cb76-171">该语句将 .dll 文件复制到服务器，并且重新绑定到新程序集。</span><span class="sxs-lookup"><span data-stu-id="3cb76-171">It copies the .dll file to the server and rebinds to the new assembly.</span></span> <span data-ttu-id="3cb76-172">有关完整的语法，请参阅[ALTER ASSEMBLY &#40;transact-sql&#41;](/sql/t-sql/statements/alter-assembly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3cb76-172">For the complete syntax, see [ALTER ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-assembly-transact-sql).</span></span>  
  
 <span data-ttu-id="3cb76-173">以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY 语句从指定的磁盘位置重新加载 Point.dll 程序集。</span><span class="sxs-lookup"><span data-stu-id="3cb76-173">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY statement reloads the Point.dll assembly from the specified location on disk.</span></span>  
  
```  
ALTER ASSEMBLY Point  
FROM '\\Projects\Point\bin\Point.dll'  
```  
  
### <a name="using-alter-assembly-to-add-source-code"></a><span data-ttu-id="3cb76-174">使用 ALTER ASSEMBLY 添加源代码</span><span class="sxs-lookup"><span data-stu-id="3cb76-174">Using ALTER ASSEMBLY to Add Source Code</span></span>  
 <span data-ttu-id="3cb76-175">CREATE ASSEMBLY 中不存在 ALTER ASSEMBLY 语法中的 ADD FILE 子句。</span><span class="sxs-lookup"><span data-stu-id="3cb76-175">The ADD FILE clause in the ALTER ASSEMBLY syntax is not present in CREATE ASSEMBLY.</span></span> <span data-ttu-id="3cb76-176">您可以使用该子句来添加源代码或与程序集关联的任何其他文件。</span><span class="sxs-lookup"><span data-stu-id="3cb76-176">You can use it to add source code or any other files associated with an assembly.</span></span> <span data-ttu-id="3cb76-177">这些文件将从其原始位置复制并存储到数据库的系统表中。</span><span class="sxs-lookup"><span data-stu-id="3cb76-177">The files are copied from their original locations and stored in system tables in the database.</span></span> <span data-ttu-id="3cb76-178">如果您需要重新创建或记录 UDT 的当前版本，这样可确保源代码或其他文件随时备用。</span><span class="sxs-lookup"><span data-stu-id="3cb76-178">This ensures that you always have source code or other files on hand should you ever need to re-create or document the current version of the UDT.</span></span>  
  
 <span data-ttu-id="3cb76-179">以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY 语句为 UDT 添加 Point.cs 类源代码 `Point` 。</span><span class="sxs-lookup"><span data-stu-id="3cb76-179">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY statement adds the Point.cs class source code for the `Point` UDT.</span></span> <span data-ttu-id="3cb76-180">这会复制 Point.cs 文件中包含的文本并用名称“PointSource”将其存储在数据库中。</span><span class="sxs-lookup"><span data-stu-id="3cb76-180">This copies the text contained in the Point.cs file and stores it in the database under the name "PointSource".</span></span>  
  
```  
ALTER ASSEMBLY Point  
ADD FILE FROM '\\Projects\Point\Point.cs' AS PointSource;  
```  
  
 <span data-ttu-id="3cb76-181">程序集信息存储在安装了程序集的数据库的**sys.databases. assembly_files**表中。</span><span class="sxs-lookup"><span data-stu-id="3cb76-181">Assembly information is stored in the **sys.assembly_files** table in the database where the assembly has been installed.</span></span> <span data-ttu-id="3cb76-182">**Sys. assembly_files**表包含以下列。</span><span class="sxs-lookup"><span data-stu-id="3cb76-182">The **sys.assembly_files** table contains the following columns.</span></span>  
  
 <span data-ttu-id="3cb76-183">**assembly_id**</span><span class="sxs-lookup"><span data-stu-id="3cb76-183">**assembly_id**</span></span>  
 <span data-ttu-id="3cb76-184">为程序集定义的标识符。</span><span class="sxs-lookup"><span data-stu-id="3cb76-184">The identifier defined for the assembly.</span></span> <span data-ttu-id="3cb76-185">此编号分配到与同一程序集相关的所有对象。</span><span class="sxs-lookup"><span data-stu-id="3cb76-185">This number is assigned to all objects relating to the same assembly.</span></span>  
  
 <span data-ttu-id="3cb76-186">name</span><span class="sxs-lookup"><span data-stu-id="3cb76-186">**name**</span></span>  
 <span data-ttu-id="3cb76-187">对象的名称。</span><span class="sxs-lookup"><span data-stu-id="3cb76-187">The name of the object.</span></span>  
  
 <span data-ttu-id="3cb76-188">**file_id**</span><span class="sxs-lookup"><span data-stu-id="3cb76-188">**file_id**</span></span>  
 <span data-ttu-id="3cb76-189">标识每个对象的数字，其中第一个与给定**assembly_id**关联的对象的值为1。</span><span class="sxs-lookup"><span data-stu-id="3cb76-189">A number identifying each object, with the first object associated with a given **assembly_id** being given the value of 1.</span></span> <span data-ttu-id="3cb76-190">如果有多个对象与同一个**assembly_id**相关联，则每个后续**file_id**值将递增1。</span><span class="sxs-lookup"><span data-stu-id="3cb76-190">If there are multiple objects associated with the same **assembly_id**, then each subsequent **file_id** value is incremented by 1.</span></span>  
  
 <span data-ttu-id="3cb76-191">**content**</span><span class="sxs-lookup"><span data-stu-id="3cb76-191">**content**</span></span>  
 <span data-ttu-id="3cb76-192">程序集或文件的十六进制表示形式。</span><span class="sxs-lookup"><span data-stu-id="3cb76-192">The hexadecimal representation of the assembly or file.</span></span>  
  
 <span data-ttu-id="3cb76-193">您可以使用 CAST 或 CONVERT 函数将**content**列的内容转换为可读文本。</span><span class="sxs-lookup"><span data-stu-id="3cb76-193">You can use the CAST or CONVERT function to convert the contents of the **content** column to readable text.</span></span> <span data-ttu-id="3cb76-194">以下查询将 Point.cs 文件的内容转换为可读文本，查询中使用 WHERE 子句中的名称将结果集限定为一行。</span><span class="sxs-lookup"><span data-stu-id="3cb76-194">The following query converts the contents of the Point.cs file to readable text, using the name in the WHERE clause to restrict the result set to a single row.</span></span>  
  
```  
SELECT CAST(content AS varchar(8000))   
  FROM sys.assembly_files   
  WHERE name='PointSource';  
```  
  
 <span data-ttu-id="3cb76-195">如果将结果复制并粘贴到某一文本编辑器中，您将看到原件中的换行符和空格均得到保留。</span><span class="sxs-lookup"><span data-stu-id="3cb76-195">If you copy and paste the results in to a text editor, you will see that the line breaks and spaces that existed in the original have been preserved.</span></span>  
  
## <a name="managing-udts-and-assemblies"></a><span data-ttu-id="3cb76-196">管理 UDT 和程序集</span><span class="sxs-lookup"><span data-stu-id="3cb76-196">Managing UDTs and Assemblies</span></span>  
 <span data-ttu-id="3cb76-197">对 UDT 的实现进行计划时，应考虑 UDT 程序集本身所需的方法，以及应该在单独的程序集中创建并作为用户定义函数或存储过程实现的方法。</span><span class="sxs-lookup"><span data-stu-id="3cb76-197">When planning your implementation of UDTs, consider which methods are needed in the UDT assembly itself, and which methods should be created in separate assemblies and implemented as user-defined functions or stored procedures.</span></span> <span data-ttu-id="3cb76-198">通过将方法分开放入不同的程序集，您可以更新代码，而不会影响可能存储在表的 UDT 列中的数据。</span><span class="sxs-lookup"><span data-stu-id="3cb76-198">Separating methods into separate assemblies allows you to update code without affecting data that may be stored in a UDT column in a table.</span></span> <span data-ttu-id="3cb76-199">仅当新定义可以读取以前值并且类型签名未更改时，才可以修改 UDT 程序集，而无需删除 UDT 列和其他依赖对象。</span><span class="sxs-lookup"><span data-stu-id="3cb76-199">You can modify UDT assemblies without dropping UDT columns and other dependent objects only when the new definition can read the former values and the signature of the type does not change.</span></span>  
  
 <span data-ttu-id="3cb76-200">将可能发生更改的过程代码与实现 UDT 所需的代码分开，可以极大地简化维护工作。</span><span class="sxs-lookup"><span data-stu-id="3cb76-200">Separating procedural code that may change from the code required to implement the UDT greatly simplifies maintenance.</span></span> <span data-ttu-id="3cb76-201">仅包括启用 UDT 所需的代码并且尽量简化 UDT 定义，这将降低出于代码修订或修复错误的目的可能需要从数据库中删除 UDT 本身的风险。</span><span class="sxs-lookup"><span data-stu-id="3cb76-201">Including only code that is necessary for the UDT to function, and keeping your UDT definitions as simple as possible, reduces the risk that the UDT itself may need to be dropped from the database for code revisions or bug fixes.</span></span>  
  
### <a name="the-currency-udt-and-currency-conversion-function"></a><span data-ttu-id="3cb76-202">Currency UDT 和货币转换函数</span><span class="sxs-lookup"><span data-stu-id="3cb76-202">The Currency UDT and Currency Conversion Function</span></span>  
 <span data-ttu-id="3cb76-203">**AdventureWorks**示例数据库中的**Currency** UDT 提供了一个有用的示例，说明如何构建 UDT 及其关联函数。</span><span class="sxs-lookup"><span data-stu-id="3cb76-203">The **Currency** UDT in the **AdventureWorks** sample database provides a useful example of the recommended way to structure a UDT and its associated functions.</span></span> <span data-ttu-id="3cb76-204">**货币**UDT 用于根据特定区域性的货币系统来处理资金，并允许存储不同货币类型，如美元、欧元等。</span><span class="sxs-lookup"><span data-stu-id="3cb76-204">The **Currency** UDT is used for handling money based on the monetary system of a particular culture, and allows for storage of different currency types, such as dollars, euros, and so forth.</span></span> <span data-ttu-id="3cb76-205">UDT 类将区域性名称公开为字符串，将货币金额公开为 `decimal` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="3cb76-205">The UDT class exposes a culture name as a string, and an amount of money as a `decimal` data type.</span></span> <span data-ttu-id="3cb76-206">所有必需的序列化方法都包括在定义该类的程序集中。</span><span class="sxs-lookup"><span data-stu-id="3cb76-206">All of the necessary serialization methods are contained within the assembly defining the class.</span></span> <span data-ttu-id="3cb76-207">实现从一个区域性到另一个区域性的货币换算的函数作为名为**ConvertCurrency**的外部函数实现，此函数位于单独的程序集中。</span><span class="sxs-lookup"><span data-stu-id="3cb76-207">The function that implements currency conversion from one culture to another is implemented as an external function named **ConvertCurrency**, and this function is located in a separate assembly.</span></span> <span data-ttu-id="3cb76-208">**ConvertCurrency**函数通过从**AdventureWorks**数据库中的表检索转换速率来完成工作。</span><span class="sxs-lookup"><span data-stu-id="3cb76-208">The **ConvertCurrency** function does its work by retrieving the conversion rate from a table in the **AdventureWorks** database.</span></span> <span data-ttu-id="3cb76-209">如果转换速率的源应发生更改，或者对现有代码进行任何其他更改，则可以轻松修改该程序集，而不会影响**货币**UDT。</span><span class="sxs-lookup"><span data-stu-id="3cb76-209">If the source of the conversion rates should ever change, or if there should be any other changes to the existing code, the assembly can be easily modified without affecting the **Currency** UDT.</span></span>  
  
 <span data-ttu-id="3cb76-210">可以通过 (CLR) 示例安装公共语言运行时来找到**Currency** UDT 和**ConvertCurrency**函数的代码列表。</span><span class="sxs-lookup"><span data-stu-id="3cb76-210">The code listing for the **Currency** UDT and **ConvertCurrency** functions can be found by installing the common language runtime (CLR) samples.</span></span>  
  
### <a name="using-udts-across-databases"></a><span data-ttu-id="3cb76-211">跨数据库使用 UDT</span><span class="sxs-lookup"><span data-stu-id="3cb76-211">Using UDTs Across Databases</span></span>  
 <span data-ttu-id="3cb76-212">根据定义，UDT 的作用域为单个数据库。</span><span class="sxs-lookup"><span data-stu-id="3cb76-212">UDTs are by definition scoped to a single database.</span></span> <span data-ttu-id="3cb76-213">因此，在一个数据库中定义的 UDT 不能用在另一个数据库的列定义中。</span><span class="sxs-lookup"><span data-stu-id="3cb76-213">Therefore, a UDT defined in one database cannot be used in a column definition in another database.</span></span> <span data-ttu-id="3cb76-214">要在多个数据库中使用 UDT，必须对各个数据库中的相同程序集执行 CREATE ASSEMBLY 和 CREATE TYPE 语句。</span><span class="sxs-lookup"><span data-stu-id="3cb76-214">In order to use UDTs in multiple databases, you must execute the CREATE ASSEMBLY and CREATE TYPE statements in each database on identical assemblies.</span></span> <span data-ttu-id="3cb76-215">如果各个程序集具有相同的名称、强名称、区域性、版本、权限集和二进制内容，即可将它们视为相同。</span><span class="sxs-lookup"><span data-stu-id="3cb76-215">Assemblies are considered identical if they have the same name, strong name, culture, version, permission set, and binary contents.</span></span>  
  
 <span data-ttu-id="3cb76-216">一旦在两个数据库中注册了 UDT 并且均可从中访问它，即可将一个数据库的 UDT 值进行转换，用于另一个数据库。</span><span class="sxs-lookup"><span data-stu-id="3cb76-216">Once the UDT is registered and accessible in both databases, you can convert a UDT value from one database for use in another.</span></span> <span data-ttu-id="3cb76-217">可以在以下情况下跨数据库使用相同的 UDT：</span><span class="sxs-lookup"><span data-stu-id="3cb76-217">Identical UDTs can be used across databases in the following scenarios:</span></span>  
  
-   <span data-ttu-id="3cb76-218">调用不同数据库中定义的存储过程。</span><span class="sxs-lookup"><span data-stu-id="3cb76-218">Calling stored procedure defined in different databases.</span></span>  
  
-   <span data-ttu-id="3cb76-219">查询不同数据库中定义的表。</span><span class="sxs-lookup"><span data-stu-id="3cb76-219">Querying tables defined in different databases.</span></span>  
  
-   <span data-ttu-id="3cb76-220">选择一个数据库表 UDT 列中的 UDT 数据，然后将其插入另一个具有相同 UDT 列的数据库。</span><span class="sxs-lookup"><span data-stu-id="3cb76-220">Selecting UDT data from one database table UDT column and inserting it into a second database with an identical UDT column.</span></span>  
  
 <span data-ttu-id="3cb76-221">在上述情况下，自动执行服务器所需的任何转换。</span><span class="sxs-lookup"><span data-stu-id="3cb76-221">In these situations, any conversion required by the server occurs automatically.</span></span> <span data-ttu-id="3cb76-222">您无法使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST 或 CONVERT 函数显式执行转换。</span><span class="sxs-lookup"><span data-stu-id="3cb76-222">You are not able to perform the conversions explicitly using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST or CONVERT functions.</span></span>  
  
 <span data-ttu-id="3cb76-223">请注意，在 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] **tempdb**系统数据库中创建工作表时，不需要采取任何措施来使用 udt。</span><span class="sxs-lookup"><span data-stu-id="3cb76-223">Note that you do not need to take any action for using UDTs when [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] creates work tables in the **tempdb** system database.</span></span> <span data-ttu-id="3cb76-224">这包括处理游标、表变量和用户定义的表值函数，这些函数包含 Udt，并以透明方式利用**tempdb**。</span><span class="sxs-lookup"><span data-stu-id="3cb76-224">This includes the handling of cursors, table variables, and user-defined table-valued functions that include UDTs and that transparently make use of **tempdb**.</span></span> <span data-ttu-id="3cb76-225">但是，如果在**tempdb**中显式创建了定义 UDT 列的临时表，则必须以与为用户数据库相同的方式在**TEMPDB**中注册 UDT。</span><span class="sxs-lookup"><span data-stu-id="3cb76-225">However, if you explicitly create a temporary table in **tempdb** that defines a UDT column, then the UDT must be registered in **tempdb** the same way as for a user database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cb76-226">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3cb76-226">See Also</span></span>  
 [<span data-ttu-id="3cb76-227">CLR 用户定义类型</span><span class="sxs-lookup"><span data-stu-id="3cb76-227">CLR User-Defined Types</span></span>](clr-user-defined-types.md)  
  
  
