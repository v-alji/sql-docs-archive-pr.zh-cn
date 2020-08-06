---
title: 本机编译的存储过程中支持的构造 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 05515013-28b5-4ccf-9a54-ae861448945b
author: rothja
ms.author: jroth
ms.openlocfilehash: 65e6e794c5858a68c4b2a9b298513911b487cf52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590807"
---
# <a name="supported-constructs-in-natively-compiled-stored-procedures"></a><span data-ttu-id="6682a-102">本机编译的存储过程中支持的构造</span><span class="sxs-lookup"><span data-stu-id="6682a-102">Supported Constructs in Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="6682a-103">本主题包含对本机编译存储过程支持的功能列表， ([CREATE PROCEDURE &#40;transact-sql&#41;](/sql/t-sql/statements/create-procedure-transact-sql)) ：</span><span class="sxs-lookup"><span data-stu-id="6682a-103">This topic contains a list of supported features for natively compiled stored procedures ([CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql)):</span></span>  
  
-   [<span data-ttu-id="6682a-104">本机编译的存储过程中的可编程性</span><span class="sxs-lookup"><span data-stu-id="6682a-104">Programmability in Natively Compiled Stored Procedures</span></span>](#pncsp)  
  
-   [<span data-ttu-id="6682a-105">支持的运算符</span><span class="sxs-lookup"><span data-stu-id="6682a-105">Supported Operators</span></span>](#so)  
  
-   [<span data-ttu-id="6682a-106">本机编译的存储过程中的内置函数</span><span class="sxs-lookup"><span data-stu-id="6682a-106">Built-in Functions in Natively Compiled Stored Procedures</span></span>](#bfncsp)  
  
-   [<span data-ttu-id="6682a-107">在本机编译的存储过程中查询外围应用</span><span class="sxs-lookup"><span data-stu-id="6682a-107">Query Surface Area in Natively Compiled Stored Procedures</span></span>](#qsancsp)  
  
-   [<span data-ttu-id="6682a-108">审核</span><span class="sxs-lookup"><span data-stu-id="6682a-108">Auditing</span></span>](#auditing)  
  
-   [<span data-ttu-id="6682a-109">表、查询和联接提示</span><span class="sxs-lookup"><span data-stu-id="6682a-109">Table, Query, and Join Hints</span></span>](#tqh)  
  
-   [<span data-ttu-id="6682a-110">排序限制</span><span class="sxs-lookup"><span data-stu-id="6682a-110">Limitations on Sorting</span></span>](#los)  
  
 <span data-ttu-id="6682a-111">有关本机编译存储过程中支持的数据类型的信息，请参阅 [Supported Data Types](supported-data-types-for-in-memory-oltp.md)。</span><span class="sxs-lookup"><span data-stu-id="6682a-111">For information on data types supported in natively compiled stored procedures, see [Supported Data Types](supported-data-types-for-in-memory-oltp.md).</span></span>  
  
 <span data-ttu-id="6682a-112">有关不支持的构造的完整信息以及有关如何处理本机编译的存储过程中不支持的某些功能的信息，请参阅 [Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="6682a-112">For complete information about unsupported constructs, and for information about how to work around some of the unsupported features in natively compiled stored procedures, see [Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md).</span></span> <span data-ttu-id="6682a-113">有关不支持的功能的详细信息，请参阅 [内存中 OLTP 不支持的 Transact-SQL 构造](transact-sql-constructs-not-supported-by-in-memory-oltp.md)。</span><span class="sxs-lookup"><span data-stu-id="6682a-113">For more information about unsupported features, see [Transact-SQL Constructs Not Supported by In-Memory OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md).</span></span>  
  
##  <a name="programmability-in-natively-compiled-stored-procedures"></a><a name="pncsp"></a><span data-ttu-id="6682a-114">本机编译的存储过程中的可编程性</span><span class="sxs-lookup"><span data-stu-id="6682a-114">Programmability in Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="6682a-115">支持以下各项：</span><span class="sxs-lookup"><span data-stu-id="6682a-115">The following are supported:</span></span>  
  
-   <span data-ttu-id="6682a-116">BEGIN ATOMIC（位于存储过程的外层）、LANGUAGE、ISOLATION LEVEL、DATEFORMAT 和 DATEFIRST。</span><span class="sxs-lookup"><span data-stu-id="6682a-116">BEGIN ATOMIC (at the outer level of the stored procedure), LANGUAGE, ISOLATION LEVEL, DATEFORMAT, and DATEFIRST.</span></span>  
  
-   <span data-ttu-id="6682a-117">将变量声明为 NULL 或 NOT NULL。</span><span class="sxs-lookup"><span data-stu-id="6682a-117">Declaring variables as NULL or NOT NULL.</span></span> <span data-ttu-id="6682a-118">如果变量声明为 NOT NULL，则声明必须具有初始值设定项。</span><span class="sxs-lookup"><span data-stu-id="6682a-118">If a variable is declared as NOT NULL, the declaration must have an initializer.</span></span> <span data-ttu-id="6682a-119">如果变量未声明为 NOT NULL，则初始值设定项是可选的。</span><span class="sxs-lookup"><span data-stu-id="6682a-119">If a variable is not declared as NOT NULL, an initializer is optional.</span></span>  
  
-   <span data-ttu-id="6682a-120">IF 和 WHILE</span><span class="sxs-lookup"><span data-stu-id="6682a-120">IF and WHILE</span></span>  
  
-   <span data-ttu-id="6682a-121">INSERT/UPDATE/DELETE</span><span class="sxs-lookup"><span data-stu-id="6682a-121">INSERT/UPDATE/DELETE</span></span>  
  
     <span data-ttu-id="6682a-122">不支持子查询。</span><span class="sxs-lookup"><span data-stu-id="6682a-122">Subqueries are not supported.</span></span> <span data-ttu-id="6682a-123">在 WHERE 或 HAVING 子句中，支持 AND 和 BETWEEN；不支持 OR、NOT 和 IN。</span><span class="sxs-lookup"><span data-stu-id="6682a-123">In the WHERE or HAVING clause, AND and BETWEEN are supported; OR, NOT, and IN are not supported.</span></span>  
  
-   <span data-ttu-id="6682a-124">内存优化的表类型和表变量。</span><span class="sxs-lookup"><span data-stu-id="6682a-124">Memory-optimized table types and table variables.</span></span>  
  
-   <span data-ttu-id="6682a-125">RETURN</span><span class="sxs-lookup"><span data-stu-id="6682a-125">RETURN</span></span>  
  
-   <span data-ttu-id="6682a-126">SELECT</span><span class="sxs-lookup"><span data-stu-id="6682a-126">SELECT</span></span>  
  
-   <span data-ttu-id="6682a-127">SET</span><span class="sxs-lookup"><span data-stu-id="6682a-127">SET</span></span>  
  
-   <span data-ttu-id="6682a-128">TRY/CATCH/THROW</span><span class="sxs-lookup"><span data-stu-id="6682a-128">TRY/CATCH/THROW</span></span>  
  
     <span data-ttu-id="6682a-129">要优化性能，请对整个本机编译存储过程使用单个 TRY/CATCH 块。</span><span class="sxs-lookup"><span data-stu-id="6682a-129">To optimize performance, use a single TRY/CATCH block for an entire natively compiled stored procedure.</span></span>  
  
##  <a name="supported-operators"></a><a name="so"></a> <span data-ttu-id="6682a-130">支持的运算符</span><span class="sxs-lookup"><span data-stu-id="6682a-130">Supported Operators</span></span>  
 <span data-ttu-id="6682a-131">支持下列运算符。</span><span class="sxs-lookup"><span data-stu-id="6682a-131">The following operators are supported.</span></span>  
  
-   <span data-ttu-id="6682a-132">[比较运算符 &#40;transact-sql&#41;](/sql/t-sql/language-elements/comparison-operators-transact-sql) (例如，>、 \<, > = 和 <=) ，如果 (，则在条件) 中支持。</span><span class="sxs-lookup"><span data-stu-id="6682a-132">[Comparison Operators &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/comparison-operators-transact-sql) (for example, >, \<, >=, and <=) are supported in conditionals (IF, WHILE).</span></span>  
  
-   <span data-ttu-id="6682a-133">一元运算符（+、-）。</span><span class="sxs-lookup"><span data-stu-id="6682a-133">Unary operators (+, -).</span></span>  
  
-   <span data-ttu-id="6682a-134">二元运算符（\*、/、+、-、%（取模））。</span><span class="sxs-lookup"><span data-stu-id="6682a-134">Binary operators (\*, /, +, -, % (modulo)).</span></span>  
  
     <span data-ttu-id="6682a-135">数字和字符串都支持加号运算符 (+)。</span><span class="sxs-lookup"><span data-stu-id="6682a-135">The plus operator (+) is supported on both numbers and strings.</span></span>  
  
-   <span data-ttu-id="6682a-136">逻辑运算符（AND、OR、NOT）。</span><span class="sxs-lookup"><span data-stu-id="6682a-136">Logical operators (AND, OR, NOT).</span></span> <span data-ttu-id="6682a-137">IF 和 WHILE 语句支持 OR 和 NOT，WHERE 或 HAVING 子句不支持 OR 和 NOT。</span><span class="sxs-lookup"><span data-stu-id="6682a-137">OR and NOT are supported in IF and WHILE statements but not in WHERE or HAVING clauses.</span></span>  
  
-   <span data-ttu-id="6682a-138">按位运算符 ~、&、| 和 ^</span><span class="sxs-lookup"><span data-stu-id="6682a-138">Bitwise operators ~, &, |, and ^</span></span>  
  
##  <a name="built-in-functions-in-natively-compiled-stored-procedures"></a><a name="bfncsp"></a><span data-ttu-id="6682a-139">本机编译的存储过程中的内置函数</span><span class="sxs-lookup"><span data-stu-id="6682a-139">Built-in Functions in Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="6682a-140">内存优化表的默认约束中以及本机编译的存储过程中支持以下函数。</span><span class="sxs-lookup"><span data-stu-id="6682a-140">The following functions are supported in default constraints on memory-optimized tables and in natively compiled stored procedures.</span></span>  
  
-   <span data-ttu-id="6682a-141">数学函数：ACOS、ASIN、ATAN、ATN2、COS、COT、DEGREES、EXP、LOG、LOG10、PI、POWER、RADIANS、RAND、SIN、SQRT、SQUARE 和 TAN</span><span class="sxs-lookup"><span data-stu-id="6682a-141">Math Functions: ACOS, ASIN, ATAN, ATN2, COS, COT, DEGREES, EXP, LOG, LOG10, PI, POWER, RADIANS, RAND, SIN, SQRT, SQUARE, and TAN</span></span>  
  
-   <span data-ttu-id="6682a-142">日期函数：CURRENT_TIMESTAMP、DATEADD、DATEDIFF、DATEFROMPARTS、DATEPART、DATETIME2FROMPARTS、DATETIMEFROMPARTS、DAY、EOMONTH、GETDATE、GETUTCDATE、MONTH、SMALLDATETIMEFROMPARTS、SYSDATETIME、SYSUTCDATETIME 和 YEAR。</span><span class="sxs-lookup"><span data-stu-id="6682a-142">Date Functions: CURRENT_TIMESTAMP, DATEADD, DATEDIFF, DATEFROMPARTS, DATEPART, DATETIME2FROMPARTS, DATETIMEFROMPARTS, DAY, EOMONTH, GETDATE, GETUTCDATE, MONTH, SMALLDATETIMEFROMPARTS, SYSDATETIME, SYSUTCDATETIME, and YEAR.</span></span>  
  
-   <span data-ttu-id="6682a-143">字符串函数：LEN、LTRIM、RTRIM 和 SUBSTRING</span><span class="sxs-lookup"><span data-stu-id="6682a-143">String Functions: LEN, LTRIM, RTRIM, and SUBSTRING</span></span>  
  
-   <span data-ttu-id="6682a-144">恒等函数：SCOPE_IDENTITY</span><span class="sxs-lookup"><span data-stu-id="6682a-144">Identity Function: SCOPE_IDENTITY</span></span>  
  
-   <span data-ttu-id="6682a-145">NULL 函数：ISNULL</span><span class="sxs-lookup"><span data-stu-id="6682a-145">NULL functions: ISNULL</span></span>  
  
-   <span data-ttu-id="6682a-146">Uniqueidentifier 函数：NEWID 和 NEWSEQUENTIALID</span><span class="sxs-lookup"><span data-stu-id="6682a-146">Uniqueidentifier functions: NEWID and NEWSEQUENTIALID</span></span>  
  
-   <span data-ttu-id="6682a-147">错误函数：ERROR_LINE、ERROR_MESSAGE、ERROR_NUMBER、ERROR_PROCEDURE、ERROR_SEVERITY 和 ERROR_STATE</span><span class="sxs-lookup"><span data-stu-id="6682a-147">Error Functions: ERROR_LINE, ERROR_MESSAGE, ERROR_NUMBER, ERROR_PROCEDURE, ERROR_SEVERITY, and ERROR_STATE</span></span>  
  
-   <span data-ttu-id="6682a-148">转换操作：CAST 和 CONVERT。</span><span class="sxs-lookup"><span data-stu-id="6682a-148">Conversions: CAST and CONVERT.</span></span> <span data-ttu-id="6682a-149">不支持在 Unicode 与非 Unicode 字符串（n(var)char 和 (var)char）之间进行转换。</span><span class="sxs-lookup"><span data-stu-id="6682a-149">Conversions between Unicode and non-Unicode character strings (n(var)char and (var)char) are not supported.</span></span>  
  
-   <span data-ttu-id="6682a-150">系统函数：@@rowcount。</span><span class="sxs-lookup"><span data-stu-id="6682a-150">System Functions: @@rowcount.</span></span> <span data-ttu-id="6682a-151">本机编译存储过程中的语句会更新 @@rowcount，因此，可使用本机编译存储过程中的 @@rowcount 来确定受在该本机编译存储过程中执行的上条语句影响的行数。</span><span class="sxs-lookup"><span data-stu-id="6682a-151">Statements inside natively compiled stored procedures update @@rowcount and you can use @@rowcount in a natively compiled stored procedure to determine the number of rows affected by the last statement executed within that natively compiled stored procedure.</span></span> <span data-ttu-id="6682a-152">但是，@@rowcount 在本机编译存储过程执行开始和结束时会重置为 0。</span><span class="sxs-lookup"><span data-stu-id="6682a-152">However, @@rowcount is reset to 0 at the start and at the end of the execution of a natively compiled stored procedure.</span></span>  
  
##  <a name="query-surface-area-in-natively-compiled-stored-procedures"></a><a name="qsancsp"></a><span data-ttu-id="6682a-153">本机编译的存储过程中的查询外围应用</span><span class="sxs-lookup"><span data-stu-id="6682a-153">Query Surface Area in Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="6682a-154">支持以下各项：</span><span class="sxs-lookup"><span data-stu-id="6682a-154">The following are supported:</span></span>  
  
-   <span data-ttu-id="6682a-155">BETWEEN</span><span class="sxs-lookup"><span data-stu-id="6682a-155">BETWEEN</span></span>  
  
-   <span data-ttu-id="6682a-156">列名别名（使用 AS 或 = 语法）。</span><span class="sxs-lookup"><span data-stu-id="6682a-156">Column name aliases (using either AS or = syntax).</span></span>  
  
-   <span data-ttu-id="6682a-157">CROSS JOIN 和 INNER JOIN 仅支持与 SELECT 查询连用。</span><span class="sxs-lookup"><span data-stu-id="6682a-157">CROSS JOIN and INNER JOIN, supported only with SELECT queries.</span></span>  
  
-   <span data-ttu-id="6682a-158">如果表达式使用受支持的运算符，则 SELECT list 和[WHERE &#40;transact-sql&#41;](/sql/t-sql/queries/where-transact-sql)子句均受支持。</span><span class="sxs-lookup"><span data-stu-id="6682a-158">Expressions are supported in SELECT list and [WHERE &#40;Transact-SQL&#41;](/sql/t-sql/queries/where-transact-sql) clause if they use a supported operator.</span></span> <span data-ttu-id="6682a-159">有关当前支持的运算符的列表，请参阅 [Supported Operators](#so) 。</span><span class="sxs-lookup"><span data-stu-id="6682a-159">See [Supported Operators](#so) for the list of currently-supported operators.</span></span>  
  
-   <span data-ttu-id="6682a-160">筛选器谓词 IS [NOT] NULL</span><span class="sxs-lookup"><span data-stu-id="6682a-160">Filter predicate IS [NOT] NULL</span></span>  
  
-   <span data-ttu-id="6682a-161">FROM \<memory optimized table></span><span class="sxs-lookup"><span data-stu-id="6682a-161">FROM \<memory optimized table></span></span>  
  
-   <span data-ttu-id="6682a-162">支持[GROUP BY &#40;transact-sql&#41;](/sql/t-sql/queries/select-group-by-transact-sql) ，以及聚合函数 AVG、COUNT、COUNT_BIG、MIN、MAX 和 SUM。</span><span class="sxs-lookup"><span data-stu-id="6682a-162">[GROUP BY &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-group-by-transact-sql) is supported, along with the aggregate functions AVG, COUNT, COUNT_BIG, MIN, MAX, and SUM.</span></span> <span data-ttu-id="6682a-163">类型 nvarchar、char、varchar、varchar、varbinary 和 Binary 不支持 MIN 和 MAX。</span><span class="sxs-lookup"><span data-stu-id="6682a-163">MIN and MAX are not supported for types nvarchar, char, varchar, varchar, varbinary, and binary.</span></span> <span data-ttu-id="6682a-164">如果 ORDER by 列表中的表达式在 "分组依据" 列表中按原义显示，则[order By 子句 &#40;transact-sql&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql)受[Group by &#40;transact-sql&#41;](/sql/t-sql/queries/select-group-by-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="6682a-164">[ORDER BY Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql) is supported with [GROUP BY &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-group-by-transact-sql) if an expression in the ORDER BY list appears verbatim in the GROUP BY list.</span></span> <span data-ttu-id="6682a-165">例如，支持 GROUP BY a + b ORDER BY a + b，但不支持 GROUP BY a、b ORDER BY a + b。</span><span class="sxs-lookup"><span data-stu-id="6682a-165">For example, GROUP BY a + b ORDER BY a + b is supported, but GROUP BY a, b ORDER BY a + b is not.</span></span>  
  
-   <span data-ttu-id="6682a-166">HAVING 具有与 WHERE 子句相同的表达式限制。</span><span class="sxs-lookup"><span data-stu-id="6682a-166">HAVING, subject to the same expression limitations as the WHERE clause.</span></span>  
  
-   <span data-ttu-id="6682a-167">INSERT VALUES（每条语句一行）和 INSERT SELECT</span><span class="sxs-lookup"><span data-stu-id="6682a-167">INSERT VALUES (one row per statement) and INSERT SELECT</span></span>  
  
-   <span data-ttu-id="6682a-168">按<sup>1</sup>排序</span><span class="sxs-lookup"><span data-stu-id="6682a-168">ORDER BY <sup>1</sup></span></span>  
  
-   <span data-ttu-id="6682a-169">不引用列的谓词。</span><span class="sxs-lookup"><span data-stu-id="6682a-169">Predicates not referencing a column.</span></span>  
  
-   <span data-ttu-id="6682a-170">SELECT、UPDATE 和 DELETE</span><span class="sxs-lookup"><span data-stu-id="6682a-170">SELECT, UPDATE, and DELETE</span></span>  
  
-   <span data-ttu-id="6682a-171">顶部<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6682a-171">TOP <sup>1</sup></span></span>  
  
-   <span data-ttu-id="6682a-172">SELECT 列表中的变量赋值。</span><span class="sxs-lookup"><span data-stu-id="6682a-172">Variable assignment in the SELECT list.</span></span>  
  
-   <span data-ttu-id="6682a-173">WHERE .。。与</span><span class="sxs-lookup"><span data-stu-id="6682a-173">WHERE ... AND</span></span>  
  
 <span data-ttu-id="6682a-174"><sup>1</sup>本机编译的存储过程支持 ORDER BY 和 TOP，但有一些限制：</span><span class="sxs-lookup"><span data-stu-id="6682a-174"><sup>1</sup> ORDER BY and TOP are supported in natively compiled stored procedures, with some restrictions:</span></span>  
  
-   <span data-ttu-id="6682a-175">在 `DISTINCT` 或 `SELECT` 子句中不支持 `ORDER BY`。</span><span class="sxs-lookup"><span data-stu-id="6682a-175">There is no support for `DISTINCT` in the `SELECT` or `ORDER BY` clause.</span></span>  
  
-   <span data-ttu-id="6682a-176">在 `WITH TIES` 子句中不支持 `PERCENT` 或 `TOP`。</span><span class="sxs-lookup"><span data-stu-id="6682a-176">There is no support for `WITH TIES` or `PERCENT` in the `TOP` clause.</span></span>  
  
-   <span data-ttu-id="6682a-177">在 `TOP` 子句中使用常量时，结合使用 `ORDER BY` 与 `TOP` 不支持超过 8,192。</span><span class="sxs-lookup"><span data-stu-id="6682a-177">`TOP` combined with `ORDER BY` does not support more than 8,192 when using a constant in the `TOP` clause.</span></span> <span data-ttu-id="6682a-178">当查询包含联接或聚合函数时，该限制数可能降低。</span><span class="sxs-lookup"><span data-stu-id="6682a-178">This limit may be lowered in case the query contains joins or aggregate functions.</span></span> <span data-ttu-id="6682a-179">（例如，对于一个联接（两个表），限制为 4,096 行。</span><span class="sxs-lookup"><span data-stu-id="6682a-179">(For example, with one join (two tables), the limit is 4,096 rows.</span></span> <span data-ttu-id="6682a-180">对于两个联接（三个表），限制为 2,730 行。）</span><span class="sxs-lookup"><span data-stu-id="6682a-180">With two joins (three tables), the limit is 2,730 rows.)</span></span>  
  
     <span data-ttu-id="6682a-181">可通过将行数存储在变量中来获得多于 8,192 的结果：</span><span class="sxs-lookup"><span data-stu-id="6682a-181">You can obtain results greater than 8,192 by storing the number of rows in a variable:</span></span>  
  
    ```sql  
    DECLARE @v INT = 9000  
    SELECT TOP (@v) ... FROM ... ORDER BY ...  
    ```  
  
 <span data-ttu-id="6682a-182">不过，与使用变量相比，在 `TOP` 子句中使用常量将提供更好的性能。</span><span class="sxs-lookup"><span data-stu-id="6682a-182">However, a constant in the `TOP` clause results in better performance compared to using a variable.</span></span>  
  
 <span data-ttu-id="6682a-183">这些限制不适用于针对内存优化表的解释的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 访问。</span><span class="sxs-lookup"><span data-stu-id="6682a-183">These restrictions do not apply to interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] access on memory-optimized tables.</span></span>  
  
##  <a name="auditing"></a><a name="auditing"></a> <span data-ttu-id="6682a-184">审核</span><span class="sxs-lookup"><span data-stu-id="6682a-184">Auditing</span></span>  
 <span data-ttu-id="6682a-185">在本机编译存储过程中支持过程级审核。</span><span class="sxs-lookup"><span data-stu-id="6682a-185">Procedure level auditing is supported in natively compiled stored procedures.</span></span> <span data-ttu-id="6682a-186">不支持语句级审核。</span><span class="sxs-lookup"><span data-stu-id="6682a-186">Statement level auditing is not supported.</span></span>  
  
 <span data-ttu-id="6682a-187">有关审核的详细信息，请参阅 [创建服务器审核规范和数据库审核规范](../security/auditing/create-a-server-audit-and-database-audit-specification.md)。</span><span class="sxs-lookup"><span data-stu-id="6682a-187">For more information about auditing, see [Create a Server Audit and Database Audit Specification](../security/auditing/create-a-server-audit-and-database-audit-specification.md).</span></span>  
  
##  <a name="table-query-and-join-hints"></a><a name="tqh"></a><span data-ttu-id="6682a-188">表、查询和联接提示</span><span class="sxs-lookup"><span data-stu-id="6682a-188">Table, Query, and Join Hints</span></span>  
 <span data-ttu-id="6682a-189">支持以下各项：</span><span class="sxs-lookup"><span data-stu-id="6682a-189">The following are supported:</span></span>  
  
-   <span data-ttu-id="6682a-190">INDEX、FORCESCAN 和 FORCESEEK 提示，位于表提示语法或查询的 [OPTION Clause (Transact-SQL)](/sql/t-sql/queries/option-clause-transact-sql) 中。</span><span class="sxs-lookup"><span data-stu-id="6682a-190">INDEX, FORCESCAN, and FORCESEEK hints, either in table hints syntax or in [OPTION Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/option-clause-transact-sql) of the query.</span></span>  
  
-   <span data-ttu-id="6682a-191">FORCE ORDER</span><span class="sxs-lookup"><span data-stu-id="6682a-191">FORCE ORDER</span></span>  
  
-   <span data-ttu-id="6682a-192">INNER LOOP JOIN</span><span class="sxs-lookup"><span data-stu-id="6682a-192">INNER LOOP JOIN</span></span>  
  
-   <span data-ttu-id="6682a-193">OPTIMIZE FOR</span><span class="sxs-lookup"><span data-stu-id="6682a-193">OPTIMIZE FOR</span></span>  
  
 <span data-ttu-id="6682a-194">有关详细信息，请参阅[提示 &#40;transact-sql&#41;](/sql/t-sql/queries/hints-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6682a-194">For more information, see [Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql).</span></span>  
  
##  <a name="limitations-on-sorting"></a><a name="los"></a><span data-ttu-id="6682a-195">排序限制</span><span class="sxs-lookup"><span data-stu-id="6682a-195">Limitations on Sorting</span></span>  
 <span data-ttu-id="6682a-196">可以在使用 [TOP (Transact-SQL)](/sql/t-sql/queries/top-transact-sql) 和 [ORDER BY 子句 (Transact-SQL)](/sql/t-sql/queries/select-order-by-clause-transact-sql) 的查询中对 8,000 多行进行排序。</span><span class="sxs-lookup"><span data-stu-id="6682a-196">You can sort greater than 8,000 rows in a query that uses [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) and an [ORDER BY Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql).</span></span> <span data-ttu-id="6682a-197">但是，如果没有 [ORDER BY 子句 (Transact-SQL)](/sql/t-sql/queries/select-order-by-clause-transact-sql)，[TOP (Transact-SQL)](/sql/t-sql/queries/top-transact-sql) 最多可对 8,000 行进行排序（如果存在联接，则更少）。</span><span class="sxs-lookup"><span data-stu-id="6682a-197">However, without [ORDER BY Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql), [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) can sort up to 8,000 rows (fewer rows if there are joins).</span></span>  
  
 <span data-ttu-id="6682a-198">如果查询同时使用 [TOP (Transact-SQL)](/sql/t-sql/queries/top-transact-sql) 运算符和 [ORDER BY 子句 (Transact-SQL)](/sql/t-sql/queries/select-order-by-clause-transact-sql)，则可以对 TOP 运算符指定多达 8192 行。</span><span class="sxs-lookup"><span data-stu-id="6682a-198">If your query uses both the [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) operator and an [ORDER BY Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql), you can specify up to 8192 rows for the TOP operator.</span></span> <span data-ttu-id="6682a-199">如果指定超过 8192 行，则将收到错误消息：消息 41398、级别 16、状态 1、程序 \<procedureName>行 \<lineNumber> TOP 运算符可返回最多 8192 行；但请求了 \<number> 行。  </span><span class="sxs-lookup"><span data-stu-id="6682a-199">If you specify more than 8192 rows you get the error message: **Msg 41398, Level 16, State 1, Procedure *\<procedureName>*, Line *\<lineNumber>* The TOP operator can return a maximum of 8192 rows; *\<number>* was requested.**</span></span>  
  
 <span data-ttu-id="6682a-200">如果您没有 TOP 子句，则可以使用 ORDER BY 对任何数目的行进行排序。</span><span class="sxs-lookup"><span data-stu-id="6682a-200">If you do not have a TOP clause, you can sort any number of rows with ORDER BY.</span></span>  
  
 <span data-ttu-id="6682a-201">如果您没有使用 ORDER BY 子句，则可以将任何整数值用于 TOP 运算符。</span><span class="sxs-lookup"><span data-stu-id="6682a-201">If you do not use an ORDER BY clause, you can use any integer value with the TOP operator.</span></span>  
  
 <span data-ttu-id="6682a-202">使用 TOP N = 8192 的示例：编译</span><span class="sxs-lookup"><span data-stu-id="6682a-202">Example with TOP N = 8192: Compiles</span></span>  
  
```sql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8192 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 <span data-ttu-id="6682a-203">使用 TOP N > 8192 的示例：无法编译。</span><span class="sxs-lookup"><span data-stu-id="6682a-203">Example with TOP N > 8192: Fails to compile.</span></span>  
  
```sql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8193 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 <span data-ttu-id="6682a-204">该 8192 行限制仅适用于 `TOP N` ，其中 `N` 是常量，如前面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="6682a-204">The 8192 row limitation only applies to `TOP N` where `N` is a constant, as in the preceding examples.</span></span>  <span data-ttu-id="6682a-205">如果您需要 `N` 大于 8192，则可以将该值分配给一个变量并且将该变量用于 `TOP`。</span><span class="sxs-lookup"><span data-stu-id="6682a-205">If you need `N` greater than 8192 you can assign the value to a variable and use that variable with `TOP`.</span></span>  
  
 <span data-ttu-id="6682a-206">使用变量的示例：编译</span><span class="sxs-lookup"><span data-stu-id="6682a-206">Example using a variable: Compiles</span></span>  
  
```sql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    DECLARE @v int = 8193   
    SELECT TOP (@v) ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 <span data-ttu-id="6682a-207">**对返回的行数的限制：** 有两种情形可减少可由 TOP 运算符返回的行数：</span><span class="sxs-lookup"><span data-stu-id="6682a-207">**Limitations on rows returned:** There are two cases where that can potentially reduce the number of rows that can be returned by the TOP operator:</span></span>  
  
-   <span data-ttu-id="6682a-208">在查询中使用 JOIN。</span><span class="sxs-lookup"><span data-stu-id="6682a-208">Using JOINs in the query.</span></span>  <span data-ttu-id="6682a-209">JOIN 对该限制的影响依赖于查询计划。</span><span class="sxs-lookup"><span data-stu-id="6682a-209">The influence of JOINs on the limitation depends on the query plan.</span></span>  
  
-   <span data-ttu-id="6682a-210">在 ORDER BY 子句中使用聚合函数或对聚合函数的引用。</span><span class="sxs-lookup"><span data-stu-id="6682a-210">Using aggregate functions or references to aggregate functions in the ORDER BY clause.</span></span>  
  
 <span data-ttu-id="6682a-211">用于在 TOP N 中计算最差情形下支持的最大 N 的公式为： `N = floor ( 65536 / number_of_tables * 8 + total_size+of+aggs )`。</span><span class="sxs-lookup"><span data-stu-id="6682a-211">The formula to calculate a worst case maximum supported N in TOP N is: `N = floor ( 65536 / number_of_tables * 8 + total_size+of+aggs )`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6682a-212">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6682a-212">See Also</span></span>  
 <span data-ttu-id="6682a-213">[本机编译存储过程](natively-compiled-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="6682a-213">[Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md) </span></span>  
 [<span data-ttu-id="6682a-214">本机编译存储过程的迁移问题</span><span class="sxs-lookup"><span data-stu-id="6682a-214">Migration Issues for Natively Compiled Stored Procedures</span></span>](migration-issues-for-natively-compiled-stored-procedures.md)  
  
  
