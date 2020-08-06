---
title: IntelliSense 支持的 Transact-SQL 语法
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- Transact-SQL IntelliSense
- IntelliSense [SQL Server], Transact-SQL syntax
ms.assetid: 194e8f4f-fd7e-4f32-a169-f23531128004
author: rothja
ms.author: jroth
ms.openlocfilehash: b3d34fc79dd7817e64b34b61083415477860ce97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690491"
---
# <a name="transact-sql-syntax-supported-by-intellisense"></a><span data-ttu-id="0b79e-102">IntelliSense 支持的 Transact-SQL 语法</span><span class="sxs-lookup"><span data-stu-id="0b79e-102">Transact-SQL Syntax Supported by IntelliSense</span></span>
  <span data-ttu-id="0b79e-103">本主题介绍了 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中的 IntelliSense 支持的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]语句和语法元素。</span><span class="sxs-lookup"><span data-stu-id="0b79e-103">This topic describes the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and syntax elements that are supported by IntelliSense in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="statements-supported-by-intellisense"></a><span data-ttu-id="0b79e-104">IntelliSense 支持的语句</span><span class="sxs-lookup"><span data-stu-id="0b79e-104">Statements Supported by IntelliSense</span></span>  
 <span data-ttu-id="0b79e-105">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，IntelliSense 只支持最常用的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="0b79e-105">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], IntelliSense supports only the most commonly used [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="0b79e-106">有些通用 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器条件可能妨碍 IntelliSense 正常运行。</span><span class="sxs-lookup"><span data-stu-id="0b79e-106">Some general [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor conditions might prevent IntelliSense from functioning.</span></span> <span data-ttu-id="0b79e-107">有关详细信息，请参阅 [IntelliSense 故障排除 (SQL Server Management Studio)](troubleshooting-intellisense.md)。</span><span class="sxs-lookup"><span data-stu-id="0b79e-107">For more information, see [Troubleshooting IntelliSense &#40;SQL Server Management Studio&#41;](troubleshooting-intellisense.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0b79e-108">IntelliSense 不能用于加密的数据库对象，例如加密的存储过程或用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="0b79e-108">IntelliSense is not available for encrypted database objects, such as encrypted stored procedures or user-defined functions.</span></span> <span data-ttu-id="0b79e-109">参数帮助和快速信息不能用于扩展存储过程和 CLR 集成用户定义类型的参数。</span><span class="sxs-lookup"><span data-stu-id="0b79e-109">Parameter help and Quick Info are not available for the parameters of extended stored procedures and CLR Integration user-defined types.</span></span>  
  
### <a name="select-statement"></a><span data-ttu-id="0b79e-110">SELECT 语句</span><span class="sxs-lookup"><span data-stu-id="0b79e-110">SELECT Statement</span></span>  
 <span data-ttu-id="0b79e-111">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器为 SELECT 语句中的以下语法元素提供 IntelliSense 支持：</span><span class="sxs-lookup"><span data-stu-id="0b79e-111">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor provides IntelliSense support for the following syntax elements in the SELECT statement:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0b79e-112">SELECT</span><span class="sxs-lookup"><span data-stu-id="0b79e-112">SELECT</span></span>|<span data-ttu-id="0b79e-113">WHERE</span><span class="sxs-lookup"><span data-stu-id="0b79e-113">WHERE</span></span>|  
|<span data-ttu-id="0b79e-114">FROM</span><span class="sxs-lookup"><span data-stu-id="0b79e-114">FROM</span></span>|<span data-ttu-id="0b79e-115">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="0b79e-115">ORDER BY</span></span>|  
|<span data-ttu-id="0b79e-116">HAVING</span><span class="sxs-lookup"><span data-stu-id="0b79e-116">HAVING</span></span>|<span data-ttu-id="0b79e-117">UNION</span><span class="sxs-lookup"><span data-stu-id="0b79e-117">UNION</span></span>|  
|<span data-ttu-id="0b79e-118">FOR</span><span class="sxs-lookup"><span data-stu-id="0b79e-118">FOR</span></span>|<span data-ttu-id="0b79e-119">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="0b79e-119">GROUP BY</span></span>|  
|<span data-ttu-id="0b79e-120">返回页首</span><span class="sxs-lookup"><span data-stu-id="0b79e-120">TOP</span></span>|<span data-ttu-id="0b79e-121">OPTION（提示）</span><span class="sxs-lookup"><span data-stu-id="0b79e-121">OPTION (hint)</span></span>|  
  
### <a name="additional-transact-sql-statements-that-are-supported"></a><span data-ttu-id="0b79e-122">支持的其他 Transact-SQL 语句</span><span class="sxs-lookup"><span data-stu-id="0b79e-122">Additional Transact-SQL Statements That Are Supported</span></span>  
 <span data-ttu-id="0b79e-123">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器还为下表中列出的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句提供 IntelliSense 支持。</span><span class="sxs-lookup"><span data-stu-id="0b79e-123">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor also provides IntelliSense support for [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that are shown in the following table.</span></span>  
  
|<span data-ttu-id="0b79e-124">Transact-SQL 语句</span><span class="sxs-lookup"><span data-stu-id="0b79e-124">Transact-SQL statement</span></span>|<span data-ttu-id="0b79e-125">支持的语法</span><span class="sxs-lookup"><span data-stu-id="0b79e-125">Syntax supported</span></span>|  
|-----------------------------|----------------------|  
|[<span data-ttu-id="0b79e-126">INSERT</span><span class="sxs-lookup"><span data-stu-id="0b79e-126">INSERT</span></span>](/sql/t-sql/statements/insert-transact-sql)|<span data-ttu-id="0b79e-127">所有语法， *execute_statement* 子句除外。</span><span class="sxs-lookup"><span data-stu-id="0b79e-127">All syntax, except the *execute_statement* clause.</span></span>|  
|[<span data-ttu-id="0b79e-128">UPDATE</span><span class="sxs-lookup"><span data-stu-id="0b79e-128">UPDATE</span></span>](/sql/t-sql/queries/update-transact-sql)|<span data-ttu-id="0b79e-129">所有语法。</span><span class="sxs-lookup"><span data-stu-id="0b79e-129">All syntax.</span></span>|  
|[<span data-ttu-id="0b79e-130">DELETE</span><span class="sxs-lookup"><span data-stu-id="0b79e-130">DELETE</span></span>](/sql/t-sql/statements/delete-transact-sql)|<span data-ttu-id="0b79e-131">所有语法。</span><span class="sxs-lookup"><span data-stu-id="0b79e-131">All syntax.</span></span>|  
|[<span data-ttu-id="0b79e-132">DECLARE @local_variable</span><span class="sxs-lookup"><span data-stu-id="0b79e-132">DECLARE @local_variable</span></span>](/sql/t-sql/language-elements/declare-local-variable-transact-sql)|<span data-ttu-id="0b79e-133">所有语法。</span><span class="sxs-lookup"><span data-stu-id="0b79e-133">All syntax.</span></span>|  
|[<span data-ttu-id="0b79e-134">字符集@local_variable</span><span class="sxs-lookup"><span data-stu-id="0b79e-134">SET @local_variable</span></span>](/sql/t-sql/language-elements/set-local-variable-transact-sql)|<span data-ttu-id="0b79e-135">所有语法。</span><span class="sxs-lookup"><span data-stu-id="0b79e-135">All syntax.</span></span>|  
|[<span data-ttu-id="0b79e-136">EXECUTE</span><span class="sxs-lookup"><span data-stu-id="0b79e-136">EXECUTE</span></span>](/sql/t-sql/language-elements/execute-transact-sql)|<span data-ttu-id="0b79e-137">执行用户定义的存储过程、系统存储过程、用户定义函数和系统函数。</span><span class="sxs-lookup"><span data-stu-id="0b79e-137">Execution of user-defined stored procedures, system stored procedures, user-defined functions, and system functions.</span></span>|  
|[<span data-ttu-id="0b79e-138">CREATE TABLE</span><span class="sxs-lookup"><span data-stu-id="0b79e-138">CREATE TABLE</span></span>](/sql/t-sql/statements/create-table-transact-sql)|<span data-ttu-id="0b79e-139">所有语法。</span><span class="sxs-lookup"><span data-stu-id="0b79e-139">All syntax.</span></span>|  
|[<span data-ttu-id="0b79e-140">CREATE VIEW</span><span class="sxs-lookup"><span data-stu-id="0b79e-140">CREATE VIEW</span></span>](/sql/t-sql/statements/create-view-transact-sql)|<span data-ttu-id="0b79e-141">所有语法。</span><span class="sxs-lookup"><span data-stu-id="0b79e-141">All syntax.</span></span>|  
|[<span data-ttu-id="0b79e-142">CREATE PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="0b79e-142">CREATE PROCEDURE</span></span>](/sql/t-sql/statements/create-procedure-transact-sql)|<span data-ttu-id="0b79e-143">所有语法，以下情况除外：</span><span class="sxs-lookup"><span data-stu-id="0b79e-143">All syntax, with the following exceptions:</span></span><br /><br /> <span data-ttu-id="0b79e-144">对 EXTERNAL NAME 子句不提供 IntelliSense 支持。</span><span class="sxs-lookup"><span data-stu-id="0b79e-144">There is no IntelliSense support for the EXTERNAL NAME clause.</span></span><br /><br /> <span data-ttu-id="0b79e-145">在 AS 子句中，IntelliSense 仅支持本主题中列出的语句和语法。</span><span class="sxs-lookup"><span data-stu-id="0b79e-145">In the AS clause, IntelliSense supports only the statements and syntax that are listed in this topic.</span></span>|  
|[<span data-ttu-id="0b79e-146">ALTER PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="0b79e-146">ALTER PROCEDURE</span></span>](/sql/t-sql/statements/alter-procedure-transact-sql)|<span data-ttu-id="0b79e-147">所有语法，以下情况除外：</span><span class="sxs-lookup"><span data-stu-id="0b79e-147">All syntax, with the following exceptions:</span></span><br /><br /> <span data-ttu-id="0b79e-148">对 EXTERNAL NAME 子句不提供 IntelliSense 支持。</span><span class="sxs-lookup"><span data-stu-id="0b79e-148">There is no IntelliSense support for the EXTERNAL NAME clause.</span></span><br /><br /> <span data-ttu-id="0b79e-149">在 AS 子句中，IntelliSense 仅支持本主题中列出的语句和语法。</span><span class="sxs-lookup"><span data-stu-id="0b79e-149">In the AS clause, IntelliSense supports only the statements and syntax that are listed in this topic.</span></span>|  
|[<span data-ttu-id="0b79e-150">USE</span><span class="sxs-lookup"><span data-stu-id="0b79e-150">USE</span></span>](/sql/t-sql/language-elements/use-transact-sql)|<span data-ttu-id="0b79e-151">所有语法。</span><span class="sxs-lookup"><span data-stu-id="0b79e-151">All syntax.</span></span>|  
  
## <a name="intellisense-in-supported-statements"></a><span data-ttu-id="0b79e-152">IntelliSense 在支持的语句中</span><span class="sxs-lookup"><span data-stu-id="0b79e-152">IntelliSense in Supported Statements</span></span>  
 <span data-ttu-id="0b79e-153">当以下语法元素用于受支持的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 语句之一时， [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询编辑器中的 IntelliSense 提供支持：</span><span class="sxs-lookup"><span data-stu-id="0b79e-153">IntelliSense in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor supports the following syntax elements when they are used in one of the supported [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
-   <span data-ttu-id="0b79e-154">所有联接类型，包括 APPLY</span><span class="sxs-lookup"><span data-stu-id="0b79e-154">All join types, including APPLY</span></span>  
  
-   <span data-ttu-id="0b79e-155">PIVOT 和 UNPIVOT</span><span class="sxs-lookup"><span data-stu-id="0b79e-155">PIVOT and UNPIVOT</span></span>  
  
-   <span data-ttu-id="0b79e-156">对以下数据库对象的引用：</span><span class="sxs-lookup"><span data-stu-id="0b79e-156">References to the following database objects:</span></span>  
  
    -   <span data-ttu-id="0b79e-157">数据库和架构</span><span class="sxs-lookup"><span data-stu-id="0b79e-157">Databases and schemas</span></span>  
  
    -   <span data-ttu-id="0b79e-158">表、视图、表值函数和表表达式</span><span class="sxs-lookup"><span data-stu-id="0b79e-158">Tables, views, table-valued functions, and table expressions</span></span>  
  
    -   <span data-ttu-id="0b79e-159">列</span><span class="sxs-lookup"><span data-stu-id="0b79e-159">Columns</span></span>  
  
    -   <span data-ttu-id="0b79e-160">过程和过程参数</span><span class="sxs-lookup"><span data-stu-id="0b79e-160">Procedures and procedure parameters</span></span>  
  
    -   <span data-ttu-id="0b79e-161">标量函数和标量表达式</span><span class="sxs-lookup"><span data-stu-id="0b79e-161">Scalar functions and scalar expressions</span></span>  
  
    -   <span data-ttu-id="0b79e-162">局部变量</span><span class="sxs-lookup"><span data-stu-id="0b79e-162">Local variables</span></span>  
  
    -   <span data-ttu-id="0b79e-163">公用表表达式 (CTE)</span><span class="sxs-lookup"><span data-stu-id="0b79e-163">Common table expressions (CTE)</span></span>  
  
-   <span data-ttu-id="0b79e-164">仅在脚本或批处理中的 CREATE 或 ALTER 语句中引用的数据库对象，但由于还未运行该脚本或批处理，数据库中不存在这些对象。</span><span class="sxs-lookup"><span data-stu-id="0b79e-164">Database objects that are referenced only in CREATE or ALTER statements in the script or batch, but which do not exist in the database because the script or batch has not yet been run.</span></span> <span data-ttu-id="0b79e-165">这些对象如下：</span><span class="sxs-lookup"><span data-stu-id="0b79e-165">These objects are as follows:</span></span>  
  
    -   <span data-ttu-id="0b79e-166">已在脚本或批处理中的 CREATE TABLE 或 CREATE PROCEDURE 语句中指定的表和过程。</span><span class="sxs-lookup"><span data-stu-id="0b79e-166">Tables and procedures that have been specified in a CREATE TABLE or CREATE PROCEDURE statement in the script or batch.</span></span>  
  
    -   <span data-ttu-id="0b79e-167">对已在脚本或批处理中的 ALTER TABLE 或 ALTER PROCEDURE 语句中指定的表和过程的更改。</span><span class="sxs-lookup"><span data-stu-id="0b79e-167">Changes to tables and procedures that have been specified in an ALTER TABLE or ALTER PROCEDURE statement in the script or batch.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0b79e-168">在执行 CREATE VIEW 语句之前，IntelliSense 不能用于 CREATE VIEW 语句的列。</span><span class="sxs-lookup"><span data-stu-id="0b79e-168">IntelliSense is not available for the columns of a CREATE VIEW statement until the CREATE VIEW statement has been executed.</span></span>  
  
 <span data-ttu-id="0b79e-169">对于上文所列的元素，当它们在其他 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句中使用时，不提供 IntelliSense 支持。</span><span class="sxs-lookup"><span data-stu-id="0b79e-169">IntelliSense is not provided for the previously listed elements when they are used in other [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="0b79e-170">例如，对于在 SELECT 语句中使用的列名，提供 IntelliSense 支持，而对于在 CREATE FUNCTION 语句中使用的列，则不提供 IntelliSense 支持。</span><span class="sxs-lookup"><span data-stu-id="0b79e-170">For example, there is IntelliSense support for column names that are used in a SELECT statement, but not for columns that are used in the CREATE FUNCTION statement.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="0b79e-171">示例</span><span class="sxs-lookup"><span data-stu-id="0b79e-171">Examples</span></span>  
 <span data-ttu-id="0b79e-172">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本或批处理中， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器中的 IntelliSense 仅支持本主题中列出的语句和语法。</span><span class="sxs-lookup"><span data-stu-id="0b79e-172">Within a [!INCLUDE[tsql](../../includes/tsql-md.md)] script or batch, IntelliSense in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor supports only the statements and syntax that are listed in this topic.</span></span> <span data-ttu-id="0b79e-173">下面的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码示例显示 IntelliSense 支持哪些语句和语法元素。</span><span class="sxs-lookup"><span data-stu-id="0b79e-173">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] code examples show what statements and syntax elements IntelliSense supports.</span></span> <span data-ttu-id="0b79e-174">例如，在以下批处理中，如果 `SELECT` 语句单独使用，则可以使用 IntelliSense，但是，如果 `SELECT` 包含在 `CREATE FUNCTION` 语句中，则不能使用 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="0b79e-174">For example, in the following batch, IntelliSense is available for the `SELECT` statement when it is coded by itself, but not when the `SELECT` is contained in a `CREATE FUNCTION` statement.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Name  
FROM Production.Product  
WHERE Name LIKE N'Road-250%' and Color = N'Red';  
GO  
CREATE FUNCTION Production.ufn_Red250 ()  
RETURNS TABLE  
AS  
RETURN   
(  
    SELECT Name  
    FROM AdventureWorks2012.Production.Product  
    WHERE Name LIKE N'Road-250%'  
      AND Color = N'Red'  
);GO  
```  
  
 <span data-ttu-id="0b79e-175">该功能也适用于 CREATE PROCEDURE 或 ALTER PROCEDURE 语句中 AS 子句中的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句组。</span><span class="sxs-lookup"><span data-stu-id="0b79e-175">This functionality also applies to the sets of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the AS clause of a CREATE PROCEDURE or ALTER PROCEDURE statement.</span></span>  
  
 <span data-ttu-id="0b79e-176">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本或批处理中，IntelliSense 支持 CREATE 或 ALTER 语句中已指定的对象；但由于尚未执行这些语句，因此数据库中不存在这些对象。</span><span class="sxs-lookup"><span data-stu-id="0b79e-176">Within a [!INCLUDE[tsql](../../includes/tsql-md.md)] script or batch, IntelliSense supports objects that have been specified in a CREATE or ALTER statement; however, these objects do not exist in the database because the statements have not been executed.</span></span> <span data-ttu-id="0b79e-177">例如，可在查询编辑器中输入以下代码：</span><span class="sxs-lookup"><span data-stu-id="0b79e-177">For example, you might enter the following code in the Query Editor:</span></span>  
  
```  
USE MyTestDB;  
GO  
CREATE TABLE MyTable  
    (PrimaryKeyCol   INT PRIMARY KEY,  
    FirstNameCol      NVARCHAR(50),  
   LastNameCol       NVARCHAR(50));  
GO  
SELECT   
```  
  
 <span data-ttu-id="0b79e-178">键入 `SELECT`后，即使尚未执行脚本并且 **中尚不存在**，IntelliSense 也会列出 **“PrimaryKeyCol”**、 **“FirstNameCol”** 和 `MyTable` “LastNameCol” `MyTestDB`作为选择列表中的可能元素。</span><span class="sxs-lookup"><span data-stu-id="0b79e-178">After you type `SELECT`, IntelliSense lists **PrimaryKeyCol**, **FirstNameCol**, and **LastNameCol** as possible elements in the select list, even if the script has not been executed and `MyTable` does not yet exist in `MyTestDB`.</span></span>  
  
  
