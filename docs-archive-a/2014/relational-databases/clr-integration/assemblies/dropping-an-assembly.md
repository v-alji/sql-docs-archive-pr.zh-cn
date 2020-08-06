---
title: 删除程序集 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- removing assemblies
- DROP ASSEMBLY statement
- assemblies [CLR integration], removing
- dropping assemblies
ms.assetid: 03481034-dc91-4488-ab24-ba44243e2690
author: rothja
ms.author: jroth
ms.openlocfilehash: 45d02cbb57459a4c1c11330446021c32dc897353
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691239"
---
# <a name="dropping-an-assembly"></a><span data-ttu-id="5688e-102">删除程序集</span><span class="sxs-lookup"><span data-stu-id="5688e-102">Dropping an Assembly</span></span>
  <span data-ttu-id="5688e-103">使用 CREATE ASSEMBLY 语句在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中注册的程序集可以进行删除（如果不再需要程序集所提供的功能）。</span><span class="sxs-lookup"><span data-stu-id="5688e-103">Assemblies that have been registered in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] using the CREATE ASSEMBLY statement can be deleted, or dropped, when the functionality they provide is no longer needed.</span></span> <span data-ttu-id="5688e-104">删除程序集时，将从数据库中删除程序集和它的所有关联文件，如调试文件。</span><span class="sxs-lookup"><span data-stu-id="5688e-104">Dropping an assembly removes the assembly and all of its associated files, such as debug files, from the database.</span></span> <span data-ttu-id="5688e-105">若要删除程序集，可按照如下语法使用 DROP ASSEMBLY 语句：</span><span class="sxs-lookup"><span data-stu-id="5688e-105">To drop an assembly, use the DROP ASSEMBLY statement with the following syntax:</span></span>  
  
```  
DROP ASSEMBLY MyDotNETAssembly  
```  
  
 <span data-ttu-id="5688e-106">DROP ASSEMBLY 不会干扰引用当前正在运行的程序集的任何代码，但是，执行 DROP ASSEMBLY 之后，任何调用程序集代码的尝试都将失败。</span><span class="sxs-lookup"><span data-stu-id="5688e-106">DROP ASSEMBLY does not interfere with any code referencing the assembly that is currently running, but after DROP ASSEMBLY executes, any attempts to invoke the assembly code fail.</span></span>  
  
 <span data-ttu-id="5688e-107">如果程序集被存在于该数据库中的另一个程序集引用，或者它被当前数据库中的公共语言运行时 (CLR) 函数、过程、触发器、用户定义类型 (UDT) 或用户定义聚合 (UDA) 使用，则 DROP ASSEMBLY 返回错误。</span><span class="sxs-lookup"><span data-stu-id="5688e-107">DROP ASSEMBLY returns an error if the assembly is referenced by another assembly that exists in the database, or if it is used by common language runtime (CLR) functions, procedures, triggers, user-defined types (UDTs), or user-defined aggregates (UDAs) in the current database.</span></span> <span data-ttu-id="5688e-108">首先可使用 DROP AGGREGATE、DROP FUNCTION、DROP PROCEDURE、DROP TRIGGER 和 DROP TYPE 语句删除该程序集中所包含的所有托管数据库对象。</span><span class="sxs-lookup"><span data-stu-id="5688e-108">First use the DROP AGGREGATE, DROP FUNCTION, DROP PROCEDURE, DROP TRIGGER, and DROP TYPE statements to delete any managed database objects contained in the assembly.</span></span>  
  
## <a name="removing-a-udt-from-the-database"></a><span data-ttu-id="5688e-109">从数据库中删除 UDT</span><span class="sxs-lookup"><span data-stu-id="5688e-109">Removing a UDT from the Database</span></span>  
 <span data-ttu-id="5688e-110">使用 DROP TYPE 语句从当前数据库中删除 UDT。</span><span class="sxs-lookup"><span data-stu-id="5688e-110">The DROP TYPE statement removes a UDT from the current database.</span></span> <span data-ttu-id="5688e-111">删除了 UDT 之后，可使用 DROP ASSEMBLY 语句从数据库中删除程序集。</span><span class="sxs-lookup"><span data-stu-id="5688e-111">Once a UDT is dropped, you can use the DROP ASSEMBLY statement to drop the assembly from the database.</span></span>  
  
 <span data-ttu-id="5688e-112">如果对象依赖于 UDT，则 DROP TYPE 语句将失败，如以下情况：</span><span class="sxs-lookup"><span data-stu-id="5688e-112">The DROP TYPE statement fails if objects depend on the UDT, as in the following situations:</span></span>  
  
-   <span data-ttu-id="5688e-113">数据库中的表包含使用 UDT 定义的列。</span><span class="sxs-lookup"><span data-stu-id="5688e-113">Tables in the database that contain columns defined using the UDT.</span></span>  
  
-   <span data-ttu-id="5688e-114">在数据库中使用 WITH SCHEMABINDING 子句创建了使用 UDT 变量或参数的函数、存储过程或触发器。</span><span class="sxs-lookup"><span data-stu-id="5688e-114">Functions, stored procedures, or triggers that use variables or parameters of the UDT, created in the database with the WITH SCHEMABINDING clause.</span></span>  
  
### <a name="finding-udt-dependencies"></a><span data-ttu-id="5688e-115">查找 UDT 依赖关系</span><span class="sxs-lookup"><span data-stu-id="5688e-115">Finding UDT Dependencies</span></span>  
 <span data-ttu-id="5688e-116">在执行 DROP TYPE 语句之前，首先必须删除所有依赖对象。</span><span class="sxs-lookup"><span data-stu-id="5688e-116">You must first drop all dependent objects, and then execute the DROP TYPE statement.</span></span> <span data-ttu-id="5688e-117">下面的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 查询查找使用**AdventureWorks**数据库中的 UDT 的所有列和参数。</span><span class="sxs-lookup"><span data-stu-id="5688e-117">The following [!INCLUDE[tsql](../../../includes/tsql-md.md)] query locates all of the columns and parameters that use a UDT in the **AdventureWorks** database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5688e-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5688e-118">See Also</span></span>  
 <span data-ttu-id="5688e-119">[管理 CLR 集成程序集](managing-clr-integration-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="5688e-119">[Managing CLR Integration Assemblies](managing-clr-integration-assemblies.md) </span></span>  
 <span data-ttu-id="5688e-120">[更改程序集](altering-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="5688e-120">[Altering an Assembly](altering-an-assembly.md) </span></span>  
 <span data-ttu-id="5688e-121">[创建程序集](creating-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="5688e-121">[Creating an Assembly](creating-an-assembly.md) </span></span>  
 <span data-ttu-id="5688e-122">[DROP &#40;Transact-sql&#41;](/sql/t-sql/statements/drop-aggregate-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5688e-122">[DROP AGGREGATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-aggregate-transact-sql) </span></span>  
 <span data-ttu-id="5688e-123">[DROP FUNCTION (Transact-SQL)](/sql/t-sql/statements/drop-function-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5688e-123">[DROP FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-function-transact-sql) </span></span>  
 <span data-ttu-id="5688e-124">[DROP PROCEDURE &#40;Transact-sql&#41;](/sql/t-sql/statements/drop-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5688e-124">[DROP PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-procedure-transact-sql) </span></span>  
 <span data-ttu-id="5688e-125">[DROP TRIGGER (Transact-SQL)](/sql/t-sql/statements/drop-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5688e-125">[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span></span>  
 [<span data-ttu-id="5688e-126">DROP TYPE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5688e-126">DROP TYPE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-type-transact-sql)  
  
  
