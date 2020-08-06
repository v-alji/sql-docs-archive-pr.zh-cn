---
title: 同义词（数据库引擎）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- synonyms [SQL Server], about synonyms
ms.assetid: 6210e1d5-075f-47e4-ac8d-f84bcf26fbc0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3494f4f5b13c422efb8e2a39597e131c10d81ed1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586576"
---
# <a name="synonyms-database-engine"></a><span data-ttu-id="cb134-102">同义词（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="cb134-102">Synonyms (Database Engine)</span></span>
  <span data-ttu-id="cb134-103">同义词是用来实现下列用途的数据库对象：</span><span class="sxs-lookup"><span data-stu-id="cb134-103">A synonym is a database object that serves the following purposes:</span></span>  
  
-   <span data-ttu-id="cb134-104">为可以存在于本地或远程服务器上的其他数据库对象（称为基对象）提供备用名称。</span><span class="sxs-lookup"><span data-stu-id="cb134-104">Provides an alternative name for another database object, referred to as the base object, that can exist on a local or remote server.</span></span>  
  
-   <span data-ttu-id="cb134-105">提供抽象层以免对客户端应用程序基对象的名称或位置进行更改。</span><span class="sxs-lookup"><span data-stu-id="cb134-105">Provides a layer of abstraction that protects a client application from changes made to the name or location of the base object.</span></span>  
  
 <span data-ttu-id="cb134-106">例如，名为 **Server1** 的服务器上有 [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)]的 **Employee**表。</span><span class="sxs-lookup"><span data-stu-id="cb134-106">For example, consider the **Employee** table of [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)], located on a server named **Server1**.</span></span> <span data-ttu-id="cb134-107">若要从其他服务器 **Server2**引用此表，则客户端应用程序必须使用由四个部分构成的名称 **Server1.AdventureWorks.Person.Employee**。</span><span class="sxs-lookup"><span data-stu-id="cb134-107">To reference this table from another server, **Server2**, a client application would have to use the four-part name **Server1.AdventureWorks.Person.Employee**.</span></span> <span data-ttu-id="cb134-108">另外，如果更改表的位置（例如，更改为其他服务器），则必须修改客户端应用程序以反映此更改。</span><span class="sxs-lookup"><span data-stu-id="cb134-108">Also, if the location of the table were to change, for example, to another server, the client application would have to be modified to reflect that change.</span></span>  
  
 <span data-ttu-id="cb134-109">若要解决这两个问题，您可以在 **Server2**上为 **Server1** 上的 **Employee** 表创建一个同义词 **EmpTable**。</span><span class="sxs-lookup"><span data-stu-id="cb134-109">To address both these issues, you can create a synonym, **EmpTable**, on **Server2** for the **Employee** table on **Server1**.</span></span> <span data-ttu-id="cb134-110">这样，客户端应用程序只需使用由一个部分构成的名称 **EmpTable**来引用 **Employee** 表。</span><span class="sxs-lookup"><span data-stu-id="cb134-110">Now, the client application only has to use the single-part name, **EmpTable**, to reference the **Employee** table.</span></span> <span data-ttu-id="cb134-111">另外，如果 **Employee** 表的位置发生变化，则必须修改同义词 **EmpTable**以指向 **Employee** 表的新位置。</span><span class="sxs-lookup"><span data-stu-id="cb134-111">Also, if the location of the **Employee** table changes, you will have to modify the synonym, **EmpTable**, to point to the new location of the **Employee** table.</span></span> <span data-ttu-id="cb134-112">由于不存在 ALTER SYNONYM 语句，因此必须首先删除同义词 **EmpTable**，然后重新创建同名的同义词，但是要将同义词指向 **Employee**的新位置。</span><span class="sxs-lookup"><span data-stu-id="cb134-112">Because there is no ALTER SYNONYM statement, you first have to drop the synonym, **EmpTable**, and then re-create the synonym with the same name, but point the synonym to the new location of **Employee**.</span></span>  
  
 <span data-ttu-id="cb134-113">同义词从属于架构，并且与架构中的其他对象一样，其名称必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="cb134-113">A synonym belongs to a schema, and like other objects in a schema, the name of a synonym must be unique.</span></span> <span data-ttu-id="cb134-114">可以为下列数据库对象创建同义词：</span><span class="sxs-lookup"><span data-stu-id="cb134-114">You can create synonyms for the following database objects:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cb134-115">程序集 (CLR) 存储过程</span><span class="sxs-lookup"><span data-stu-id="cb134-115">Assembly (CLR) stored procedure</span></span>|<span data-ttu-id="cb134-116">程序集 (CLR) 表值函数</span><span class="sxs-lookup"><span data-stu-id="cb134-116">Assembly (CLR) table-valued function</span></span>|  
|<span data-ttu-id="cb134-117">程序集 (CLR) 标量函数</span><span class="sxs-lookup"><span data-stu-id="cb134-117">Assembly (CLR) scalar function</span></span>|<span data-ttu-id="cb134-118">程序集 (CLR) 聚合函数</span><span class="sxs-lookup"><span data-stu-id="cb134-118">Assembly (CLR) aggregate functions</span></span>|  
|<span data-ttu-id="cb134-119">复制筛选过程</span><span class="sxs-lookup"><span data-stu-id="cb134-119">Replication-filter-procedure</span></span>|<span data-ttu-id="cb134-120">扩展存储过程</span><span class="sxs-lookup"><span data-stu-id="cb134-120">Extended stored procedure</span></span>|  
|<span data-ttu-id="cb134-121">SQL 标量函数</span><span class="sxs-lookup"><span data-stu-id="cb134-121">SQL scalar function</span></span>|<span data-ttu-id="cb134-122">SQL 表值函数</span><span class="sxs-lookup"><span data-stu-id="cb134-122">SQL table-valued function</span></span>|  
|<span data-ttu-id="cb134-123">SQL 内联表值函数</span><span class="sxs-lookup"><span data-stu-id="cb134-123">SQL inline-tabled-valued function</span></span>|<span data-ttu-id="cb134-124">SQL 存储过程</span><span class="sxs-lookup"><span data-stu-id="cb134-124">SQL stored procedure</span></span>|  
|<span data-ttu-id="cb134-125">查看</span><span class="sxs-lookup"><span data-stu-id="cb134-125">View</span></span>|<span data-ttu-id="cb134-126">表<sup>1</sup>（用户定义）</span><span class="sxs-lookup"><span data-stu-id="cb134-126">Table<sup>1</sup> (User-defined)</span></span>|  
  
 <span data-ttu-id="cb134-127"><sup>1</sup>包括本地和全局临时表</span><span class="sxs-lookup"><span data-stu-id="cb134-127"><sup>1</sup> Includes local and global temporary tables</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cb134-128">不支持使用函数基对象的四部分名称。</span><span class="sxs-lookup"><span data-stu-id="cb134-128">Four-part names for function base objects are not supported.</span></span>  
  
 <span data-ttu-id="cb134-129">同义词不能是另一个同义词的基对象，也不能引用用户定义聚合函数。</span><span class="sxs-lookup"><span data-stu-id="cb134-129">A synonym cannot be the base object for another synonym, and a synonym cannot reference a user-defined aggregate function.</span></span>  
  
 <span data-ttu-id="cb134-130">同义词与其基对象之间只是按名称绑定。</span><span class="sxs-lookup"><span data-stu-id="cb134-130">The binding between a synonym and its base object is by name only.</span></span> <span data-ttu-id="cb134-131">对基对象的存在性、类型和权限检查都在运行时执行。</span><span class="sxs-lookup"><span data-stu-id="cb134-131">All existence, type, and permissions checking on the base object is deferred until run time.</span></span> <span data-ttu-id="cb134-132">因此，可以修改或删除基对象，也可以先删除基对象，然后用与原始基对象同名的另一个对象来替换该基对象。</span><span class="sxs-lookup"><span data-stu-id="cb134-132">Therefore, the base object can be modified, dropped, or dropped and replaced by another object that has the same name as the original base object.</span></span> <span data-ttu-id="cb134-133">例如，有一个引用 **中的**Person.Contact **表的同义词** MyContacts [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cb134-133">For example, consider a synonym, **MyContacts**, that references the **Person.Contact** table in [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)].</span></span> <span data-ttu-id="cb134-134">如果将 **Contact** 表删除，并用名为 **Person.Contact**的视图替换该表，则 **MyContacts** 将引用 **Person.Contact** 视图。</span><span class="sxs-lookup"><span data-stu-id="cb134-134">If the **Contact** table is dropped and replaced by a view named **Person.Contact**, **MyContacts** now references the **Person.Contact** view.</span></span>  
  
 <span data-ttu-id="cb134-135">同义词的引用不是绑定到架构的。</span><span class="sxs-lookup"><span data-stu-id="cb134-135">References to synonyms are not schema-bound.</span></span> <span data-ttu-id="cb134-136">因此，可以随时删除同义词。</span><span class="sxs-lookup"><span data-stu-id="cb134-136">Therefore, a synonym can be dropped at any time.</span></span> <span data-ttu-id="cb134-137">但删除同义词后，会留下已删除同义词的无关联引用，</span><span class="sxs-lookup"><span data-stu-id="cb134-137">However, by dropping a synonym, you run the risk of leaving dangling references to the synonym that was dropped.</span></span> <span data-ttu-id="cb134-138">而只有在运行时才会发现这些引用。</span><span class="sxs-lookup"><span data-stu-id="cb134-138">These references will only be found at run time.</span></span>  
  
## <a name="synonyms-and-schemas"></a><span data-ttu-id="cb134-139">同义词和架构</span><span class="sxs-lookup"><span data-stu-id="cb134-139">Synonyms and Schemas</span></span>  
 <span data-ttu-id="cb134-140">如果具有不属于您的默认架构并要创建同义词，则必须使用属于您的架构名称限定同义词名称。</span><span class="sxs-lookup"><span data-stu-id="cb134-140">If you have a default schema that you do not own and want to create a synonym, you must qualify the synonym name with the name of a schema that you do own.</span></span> <span data-ttu-id="cb134-141">例如，如果拥有架构 **x**，但 **y** 是默认架构，那么使用 CREATE SYNONYM 语句时，必须在同义词名称前添加架构 **x**，而不是使用由一个部分构成的名称来命名同义词。</span><span class="sxs-lookup"><span data-stu-id="cb134-141">For example, if you own a schema **x**, but **y** is your default schema and you use the CREATE SYNONYM statement, you must prefix the name of the synonym with the schema **x**, instead of naming the synonym by using a single-part name.</span></span> <span data-ttu-id="cb134-142">有关如何创建同义词的详细信息，请参阅 [CREATE SYNONYM (Transact-SQL)](/sql/t-sql/statements/create-synonym-transact-sql)表。</span><span class="sxs-lookup"><span data-stu-id="cb134-142">For more information about how to create synonyms, see [CREATE SYNONYM &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-synonym-transact-sql).</span></span>  
  
## <a name="granting-permissions-on-a-synonym"></a><span data-ttu-id="cb134-143">授予同义词的有关权限</span><span class="sxs-lookup"><span data-stu-id="cb134-143">Granting Permissions on a Synonym</span></span>  
 <span data-ttu-id="cb134-144">只有同义词所有者、 **db_owner**的成员或 **db_ddladmin** 的成员才能授予同义词的有关权限。</span><span class="sxs-lookup"><span data-stu-id="cb134-144">Only synonym owners, members of **db_owner**, or members of **db_ddladmin** can grant permission on a synonym.</span></span>  
  
 <span data-ttu-id="cb134-145">可以授予、拒绝和撤消对同义词的下列所有权限或任一权限：</span><span class="sxs-lookup"><span data-stu-id="cb134-145">You can GRANT, DENY, REVOKE all or any of the following permissions on a synonym:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cb134-146">CONTROL</span><span class="sxs-lookup"><span data-stu-id="cb134-146">CONTROL</span></span>|<span data-ttu-id="cb134-147">DELETE</span><span class="sxs-lookup"><span data-stu-id="cb134-147">DELETE</span></span>|  
|<span data-ttu-id="cb134-148">EXECUTE</span><span class="sxs-lookup"><span data-stu-id="cb134-148">EXECUTE</span></span>|<span data-ttu-id="cb134-149">INSERT</span><span class="sxs-lookup"><span data-stu-id="cb134-149">INSERT</span></span>|  
|<span data-ttu-id="cb134-150">SELECT</span><span class="sxs-lookup"><span data-stu-id="cb134-150">SELECT</span></span>|<span data-ttu-id="cb134-151">TAKE OWNERSHIP</span><span class="sxs-lookup"><span data-stu-id="cb134-151">TAKE OWNERSHIP</span></span>|  
|<span data-ttu-id="cb134-152">UPDATE</span><span class="sxs-lookup"><span data-stu-id="cb134-152">UPDATE</span></span>|<span data-ttu-id="cb134-153">VIEW DEFINITION</span><span class="sxs-lookup"><span data-stu-id="cb134-153">VIEW DEFINITION</span></span>|  
  
## <a name="using-synonyms"></a><span data-ttu-id="cb134-154">使用同义词</span><span class="sxs-lookup"><span data-stu-id="cb134-154">Using Synonyms</span></span>  
 <span data-ttu-id="cb134-155">可以在一些 SQL 语句和表达式上下文中使用同义词替代其引用的基对象。</span><span class="sxs-lookup"><span data-stu-id="cb134-155">You can use synonyms in place of their referenced base object in several SQL statements and expression contexts.</span></span> <span data-ttu-id="cb134-156">下表包含这些语句和表达式上下文的列表：</span><span class="sxs-lookup"><span data-stu-id="cb134-156">The following table contains a list of these statements and expression contexts:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cb134-157">SELECT</span><span class="sxs-lookup"><span data-stu-id="cb134-157">SELECT</span></span>|<span data-ttu-id="cb134-158">INSERT</span><span class="sxs-lookup"><span data-stu-id="cb134-158">INSERT</span></span>|  
|<span data-ttu-id="cb134-159">UPDATE</span><span class="sxs-lookup"><span data-stu-id="cb134-159">UPDATE</span></span>|<span data-ttu-id="cb134-160">DELETE</span><span class="sxs-lookup"><span data-stu-id="cb134-160">DELETE</span></span>|  
|<span data-ttu-id="cb134-161">EXECUTE</span><span class="sxs-lookup"><span data-stu-id="cb134-161">EXECUTE</span></span>|<span data-ttu-id="cb134-162">嵌套的 SELECT</span><span class="sxs-lookup"><span data-stu-id="cb134-162">Sub-selects</span></span>|  
  
 <span data-ttu-id="cb134-163">在以前说明的上下文中使用同义词时，该基对象会受到影响。</span><span class="sxs-lookup"><span data-stu-id="cb134-163">When you are working with synonyms in the contexts previously stated, the base object is affected.</span></span> <span data-ttu-id="cb134-164">例如，如果某个同义词引用了基对象（表）并且将行插入同义词中，则实际上将行插入到引用的表中。</span><span class="sxs-lookup"><span data-stu-id="cb134-164">For example, if a synonym references a base object that is a table and you insert a row into the synonym, you are actually inserting a row into the referenced table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cb134-165">无法引用位于链接服务器上的同义词。</span><span class="sxs-lookup"><span data-stu-id="cb134-165">You cannot reference a synonym that is located on a linked server.</span></span>  
  
 <span data-ttu-id="cb134-166">可以使用同义词作为 OBJECT_ID 函数的参数；但是，函数返回同义词的对象 ID，而不是基对象。</span><span class="sxs-lookup"><span data-stu-id="cb134-166">You can use a synonym as the parameter for the OBJECT_ID function; however, the function returns the object ID of the synonym, not the base object.</span></span>  
  
 <span data-ttu-id="cb134-167">不能在 DDL 语句中引用同义词。</span><span class="sxs-lookup"><span data-stu-id="cb134-167">You cannot reference a synonym in a DDL statement.</span></span> <span data-ttu-id="cb134-168">例如，引用名为 `dbo.MyProduct`的同义词的下列语句将生成错误：</span><span class="sxs-lookup"><span data-stu-id="cb134-168">For example, the following statements, which reference a synonym named `dbo.MyProduct`, generate errors:</span></span>  
  
```  
ALTER TABLE dbo.MyProduct  
   ADD NewFlag int null;  
EXEC ('ALTER TABLE dbo.MyProduct  
   ADD NewFlag int null');  
```  
  
 <span data-ttu-id="cb134-169">下列权限语句仅与同义词（而不是基对象）关联：</span><span class="sxs-lookup"><span data-stu-id="cb134-169">The following permission statements are associated only with the synonym and not the base object:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cb134-170">GRANT</span><span class="sxs-lookup"><span data-stu-id="cb134-170">GRANT</span></span>|<span data-ttu-id="cb134-171">DENY</span><span class="sxs-lookup"><span data-stu-id="cb134-171">DENY</span></span>|  
|<span data-ttu-id="cb134-172">REVOKE</span><span class="sxs-lookup"><span data-stu-id="cb134-172">REVOKE</span></span>||  
  
 <span data-ttu-id="cb134-173">因为同义词不绑定到架构，所以无法通过下列架构绑定表达式上下文引用：</span><span class="sxs-lookup"><span data-stu-id="cb134-173">Synonyms are not schema-bound and, therefore, cannot be referenced by the following schema-bound expression contexts:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cb134-174">CHECK 约束</span><span class="sxs-lookup"><span data-stu-id="cb134-174">CHECK constraints</span></span>|<span data-ttu-id="cb134-175">计算列</span><span class="sxs-lookup"><span data-stu-id="cb134-175">Computed columns</span></span>|  
|<span data-ttu-id="cb134-176">默认的表达式</span><span class="sxs-lookup"><span data-stu-id="cb134-176">Default expressions</span></span>|<span data-ttu-id="cb134-177">规则表达式</span><span class="sxs-lookup"><span data-stu-id="cb134-177">Rule expressions</span></span>|  
|<span data-ttu-id="cb134-178">绑定到架构的视图</span><span class="sxs-lookup"><span data-stu-id="cb134-178">Schema-bound views</span></span>|<span data-ttu-id="cb134-179">绑定到架构的函数</span><span class="sxs-lookup"><span data-stu-id="cb134-179">Schema-bound functions</span></span>|  
  
 <span data-ttu-id="cb134-180">有关绑定到架构的函数的详细信息，请参阅[创建用户定义的函数（数据库引擎）](../user-defined-functions/create-user-defined-functions-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="cb134-180">For more information about schema-bound functions, see [Create User-defined Functions &#40;Database Engine&#41;](../user-defined-functions/create-user-defined-functions-database-engine.md).</span></span>  
  
## <a name="getting-information-about-synonyms"></a><span data-ttu-id="cb134-181">获取有关同义词的信息</span><span class="sxs-lookup"><span data-stu-id="cb134-181">Getting Information About Synonyms</span></span>  
 <span data-ttu-id="cb134-182">sys.synonyms 目录视图包含给定的数据库中的所有同义词项。</span><span class="sxs-lookup"><span data-stu-id="cb134-182">The sys.synonyms catalog view contains an entry for each synonym in a given database.</span></span> <span data-ttu-id="cb134-183">该目录视图将显示同义词元数据，例如同义词的名称和基对象的名称。</span><span class="sxs-lookup"><span data-stu-id="cb134-183">This catalog view exposes synonym metadata such as the name of the synonym and the name of the base object.</span></span> <span data-ttu-id="cb134-184">有关目录视图的详细信息 `sys.synonyms` ，请参阅[Sys.databases &#40;transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-synonyms-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cb134-184">For more information about the `sys.synonyms` catalog view, see [sys.synonyms &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-synonyms-transact-sql).</span></span>  
  
 <span data-ttu-id="cb134-185">使用扩展属性，您可以将描述性或说明性文本、输入掩码以及格式化规则添加为同义词的属性。</span><span class="sxs-lookup"><span data-stu-id="cb134-185">By using extended properties, you can add descriptive or instructional text, input masks, and formatting rules as properties of a synonym.</span></span> <span data-ttu-id="cb134-186">因为属性存储在数据库中，因此所有读取属性的应用程序都能以相同的方式评估对象。</span><span class="sxs-lookup"><span data-stu-id="cb134-186">Because the property is stored in the database, all applications that read the property can evaluate the object in the same way.</span></span> <span data-ttu-id="cb134-187">有关详细信息，请参阅 [sp_addextendedproperty (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cb134-187">For more information, see [sp_addextendedproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql).</span></span>  
  
 <span data-ttu-id="cb134-188">若要查找同义词基对象的基类型，请使用 OBJECTPROPERTYEX 函数。</span><span class="sxs-lookup"><span data-stu-id="cb134-188">To find the base type of the base object of a synonym, use the OBJECTPROPERTYEX function.</span></span> <span data-ttu-id="cb134-189">有关详细信息，请参阅 [OBJECTPROPERTYEX (Transact-SQL) ](/sql/t-sql/functions/objectproperty-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cb134-189">For more information, see [OBJECTPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectproperty-transact-sql).</span></span>  
  
### <a name="examples"></a><span data-ttu-id="cb134-190">示例</span><span class="sxs-lookup"><span data-stu-id="cb134-190">Examples</span></span>  
 <span data-ttu-id="cb134-191">下面的示例将返回同义词基对象（本地对象）的基类型。</span><span class="sxs-lookup"><span data-stu-id="cb134-191">The following example returns the base type of a synonym's base object that is a local object.</span></span>  
  
```  
USE tempdb;  
GO  
CREATE SYNONYM MyEmployee   
FOR AdventureWorks2012.HumanResources.Employee;  
GO  
SELECT OBJECTPROPERTYEX(OBJECT_ID('MyEmployee'), 'BaseType') AS BaseType;  
```  
  
 <span data-ttu-id="cb134-192">下面的示例将返回同义词基对象（位于名为 `Server1`的服务器上的远程对象）的基类型。</span><span class="sxs-lookup"><span data-stu-id="cb134-192">The following example returns the base type of a synonym's base object that is a remote object located on a server named `Server1`.</span></span>  
  
```  
EXECUTE sp_addlinkedserver Server1;  
GO  
CREATE SYNONYM MyRemoteEmployee  
FOR Server1.AdventureWorks2012.HumanResources.Employee;  
GO  
SELECT OBJECTPROPERTYEX(OBJECT_ID('MyRemoteEmployee'), 'BaseType') AS BaseType;  
GO  
```  
  
## <a name="related-content"></a><span data-ttu-id="cb134-193">相关内容</span><span class="sxs-lookup"><span data-stu-id="cb134-193">Related Content</span></span>  
 [<span data-ttu-id="cb134-194">创建同义词</span><span class="sxs-lookup"><span data-stu-id="cb134-194">Create Synonyms</span></span>](create-synonyms.md)  
  
 [<span data-ttu-id="cb134-195">CREATE SYNONYM (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="cb134-195">CREATE SYNONYM &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-synonym-transact-sql)  
  
 [<span data-ttu-id="cb134-196">DROP SYNONYM (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="cb134-196">DROP SYNONYM &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-synonym-transact-sql)  
  
  
