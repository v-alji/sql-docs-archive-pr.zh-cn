---
title: 计算列上的索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- computed columns, index creation
- index creation [SQL Server], computed columns
- imprecise columns
- persisted computed columns
- precise [SQL Server]
ms.assetid: 8d17ac9c-f3af-4bbb-9cc1-5cf647e994c4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2ecbca9e7838c4c9395a8bcb6e11351c40f7037f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693868"
---
# <a name="indexes-on-computed-columns"></a><span data-ttu-id="0be0a-102">计算列上的索引</span><span class="sxs-lookup"><span data-stu-id="0be0a-102">Indexes on Computed Columns</span></span>
  <span data-ttu-id="0be0a-103">只要满足下列要求就可以为计算列定义索引：</span><span class="sxs-lookup"><span data-stu-id="0be0a-103">You can define indexes on computed columns as long as the following requirements are met:</span></span>  
  
-   <span data-ttu-id="0be0a-104">所有权要求</span><span class="sxs-lookup"><span data-stu-id="0be0a-104">Ownership requirements</span></span>  
  
-   <span data-ttu-id="0be0a-105">确定性要求</span><span class="sxs-lookup"><span data-stu-id="0be0a-105">Determinism requirements</span></span>  
  
-   <span data-ttu-id="0be0a-106">精度要求</span><span class="sxs-lookup"><span data-stu-id="0be0a-106">Precision requirements</span></span>  
  
-   <span data-ttu-id="0be0a-107">数据类型要求</span><span class="sxs-lookup"><span data-stu-id="0be0a-107">Data type requirements</span></span>  
  
-   <span data-ttu-id="0be0a-108">SET 选项要求</span><span class="sxs-lookup"><span data-stu-id="0be0a-108">SET option requirements</span></span>  
  
 <span data-ttu-id="0be0a-109">**Ownership Requirements**</span><span class="sxs-lookup"><span data-stu-id="0be0a-109">**Ownership Requirements**</span></span>  
  
 <span data-ttu-id="0be0a-110">计算列中的所有函数引用必须与表具有相同的所有者。</span><span class="sxs-lookup"><span data-stu-id="0be0a-110">All function references in the computed column must have the same owner as the table.</span></span>  
  
 <span data-ttu-id="0be0a-111">**Determinism Requirements**</span><span class="sxs-lookup"><span data-stu-id="0be0a-111">**Determinism Requirements**</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0be0a-112">如果对于一组指定的输入表达式始终返回相同的结果，则说明表达式具有确定性。</span><span class="sxs-lookup"><span data-stu-id="0be0a-112">Expressions are deterministic if they always return the same result for a specified set of inputs.</span></span> <span data-ttu-id="0be0a-113">**COLUMNPROPERTY** 函数的 [IsDeterministic](/sql/t-sql/functions/columnproperty-transact-sql) 属性报告 *computed_column_expression* 是否具有确定性。</span><span class="sxs-lookup"><span data-stu-id="0be0a-113">The **IsDeterministic** property of the [COLUMNPROPERTY](/sql/t-sql/functions/columnproperty-transact-sql) function reports whether a *computed_column_expression* is deterministic.</span></span>  
  
 <span data-ttu-id="0be0a-114">*Computed_column_expression* 必须具有确定性。</span><span class="sxs-lookup"><span data-stu-id="0be0a-114">The *computed_column_expression* must be deterministic.</span></span> <span data-ttu-id="0be0a-115">如果下列一项或多项为真，则 *computed_column_expression* 具有确定性：</span><span class="sxs-lookup"><span data-stu-id="0be0a-115">A *computed_column_expression* is deterministic when one or more of the following is true:</span></span>  
  
-   <span data-ttu-id="0be0a-116">表达式引用的所有函数都具有确定性，并且是精确的。</span><span class="sxs-lookup"><span data-stu-id="0be0a-116">All functions that are referenced by the expression are deterministic and precise.</span></span> <span data-ttu-id="0be0a-117">这些函数包括用户定义函数和内置函数。</span><span class="sxs-lookup"><span data-stu-id="0be0a-117">These functions include both user-defined and built-in functions.</span></span> <span data-ttu-id="0be0a-118">有关详细信息，请参阅 [Deterministic and Nondeterministic Functions](../user-defined-functions/deterministic-and-nondeterministic-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="0be0a-118">For more information, see [Deterministic and Nondeterministic Functions](../user-defined-functions/deterministic-and-nondeterministic-functions.md).</span></span> <span data-ttu-id="0be0a-119">如果计算列是 PERSISTED，则函数可能不精确。</span><span class="sxs-lookup"><span data-stu-id="0be0a-119">Functions might be imprecise if the computed column is PERSISTED.</span></span> <span data-ttu-id="0be0a-120">有关详细信息，请参阅本主题后面的 [对持久化计算列创建索引](#BKMK_persisted) 。</span><span class="sxs-lookup"><span data-stu-id="0be0a-120">For more information, see [Creating Indexes on Persisted Computed Columns](#BKMK_persisted) later in this topic.</span></span>  
  
-   <span data-ttu-id="0be0a-121">表达式引用的所有列都来自包含计算列的表。</span><span class="sxs-lookup"><span data-stu-id="0be0a-121">All columns that are referenced in the expression come from the table that contains the computed column.</span></span>  
  
-   <span data-ttu-id="0be0a-122">没有列引用从多行中请求数据。</span><span class="sxs-lookup"><span data-stu-id="0be0a-122">No column reference pulls data from multiple rows.</span></span> <span data-ttu-id="0be0a-123">例如，聚合函数（如 SUM 或 AVG）依靠来自多行的数据，这使 *computed_column_expression* 具有不确定性。</span><span class="sxs-lookup"><span data-stu-id="0be0a-123">For example, aggregate functions such as SUM or AVG depend on data from multiple rows and would make a *computed_column_expression* nondeterministic.</span></span>  
  
-   <span data-ttu-id="0be0a-124">*computed_column_expression* 没有系统数据访问或用户数据访问。</span><span class="sxs-lookup"><span data-stu-id="0be0a-124">The *computed_column_expression* has no system data access or user data access.</span></span>  
  
 <span data-ttu-id="0be0a-125">任何包含公共语言运行时 (CLR) 表达式的计算列都必须具有确定性并标记为 PERSISTED，这样才能为该列创建索引。</span><span class="sxs-lookup"><span data-stu-id="0be0a-125">Any computed column that contains a common language runtime (CLR) expression must be deterministic and marked PERSISTED before the column can be indexed.</span></span> <span data-ttu-id="0be0a-126">允许在计算列定义中使用 CLR 用户定义类型的表达式。</span><span class="sxs-lookup"><span data-stu-id="0be0a-126">CLR user-defined type expressions are allowed in computed column definitions.</span></span> <span data-ttu-id="0be0a-127">类型为 CLR 用户定义类型的计算列只要其类型是可比较的，就可以在该列上创建索引。</span><span class="sxs-lookup"><span data-stu-id="0be0a-127">Computed columns whose type is a CLR user-defined type can be indexed as long as the type is comparable.</span></span> <span data-ttu-id="0be0a-128">有关详细信息，请参阅 [CLR 用户定义类型](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)。</span><span class="sxs-lookup"><span data-stu-id="0be0a-128">For more information, see [CLR User-Defined Types](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0be0a-129">如果您在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]内的索引计算列中引用 date 数据类型的字符串文字，则建议使用确定性日期格式样式将该文字显式转换为所需的日期类型。</span><span class="sxs-lookup"><span data-stu-id="0be0a-129">When you refer to string literals of the date data type in indexed computed columns in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], we recommend that you explicitly convert the literal to the date type that you want by using a deterministic date format style.</span></span> <span data-ttu-id="0be0a-130">有关确定性日期格式样式的列表，请参阅 [CAST and CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0be0a-130">For a list of the date format styles that are deterministic, see [CAST and CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span> <span data-ttu-id="0be0a-131">除非数据库兼容级别设置为 80 或更低，否则涉及字符串到 date 数据类型的隐式转换的表达式将被视为具有不确定性。</span><span class="sxs-lookup"><span data-stu-id="0be0a-131">Expressions that involve implicit conversion of character strings to date data types are considered nondeterministic, unless the database compatibility level is set to 80 or earlier.</span></span> <span data-ttu-id="0be0a-132">这是因为结果取决于服务器会话的 [LANGUAGE](/sql/t-sql/statements/set-language-transact-sql) 和 [DATEFORMAT](/sql/t-sql/statements/set-dateformat-transact-sql) 设置。</span><span class="sxs-lookup"><span data-stu-id="0be0a-132">This is because the results depend on the [LANGUAGE](/sql/t-sql/statements/set-language-transact-sql) and [DATEFORMAT](/sql/t-sql/statements/set-dateformat-transact-sql) settings of the server session.</span></span> <span data-ttu-id="0be0a-133">例如，表达式 `CONVERT (datetime, '30 listopad 1996', 113)` 的结果取决于 LANGUAGE 设置，因为字符串`30 listopad 1996`在不同语言中表示不同的月份。</span><span class="sxs-lookup"><span data-stu-id="0be0a-133">For example, the results of the expression `CONVERT (datetime, '30 listopad 1996', 113)` depend on the LANGUAGE setting because the string '`30 listopad 1996`' means different months in different languages.</span></span> <span data-ttu-id="0be0a-134">同样，在表达式 `DATEADD(mm,3,'2000-12-01')`中， [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 基于 DATEFORMAT 设置解释字符串 `'2000-12-01'` 。</span><span class="sxs-lookup"><span data-stu-id="0be0a-134">Similarly, in the expression `DATEADD(mm,3,'2000-12-01')`, the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] interprets the string `'2000-12-01'` based on the DATEFORMAT setting.</span></span>  
>   
>  <span data-ttu-id="0be0a-135">非 Unicode 字符数据在排序规则间的隐式转换也被视为具有不确定性，除非兼容级别设置为 80 或更低。</span><span class="sxs-lookup"><span data-stu-id="0be0a-135">Implicit conversion of non-Unicode character data between collations is also considered nondeterministic, unless the compatibility level is set to 80 or earlier.</span></span>  
>   
>  <span data-ttu-id="0be0a-136">当数据库兼容级别设置为 90 时，不能对包含这些表达式的计算列创建索引。</span><span class="sxs-lookup"><span data-stu-id="0be0a-136">When the database compatibility level setting is 90, you cannot create indexes on computed columns that contain these expressions.</span></span> <span data-ttu-id="0be0a-137">但在已升级的数据库中，包含这些表达式的现有计算列是可以维护的。</span><span class="sxs-lookup"><span data-stu-id="0be0a-137">However, existing computed columns that contain these expressions from an upgraded database are maintainable.</span></span> <span data-ttu-id="0be0a-138">如果使用包含字符串到日期的隐式转换的索引计算列，则为了避免损坏索引，请确保数据库和应用程序中的 LANGUAGE 和 DATEFORMAT 设置一致。</span><span class="sxs-lookup"><span data-stu-id="0be0a-138">If you use indexed computed columns that contain implicit string to date conversions, to avoid possible index corruption, make sure that the LANGUAGE and DATEFORMAT settings are consistent in your databases and applications.</span></span>  
  
 <span data-ttu-id="0be0a-139">**Precision Requirements**</span><span class="sxs-lookup"><span data-stu-id="0be0a-139">**Precision Requirements**</span></span>  
  
 <span data-ttu-id="0be0a-140">*computed_column_expression* 必须精确。</span><span class="sxs-lookup"><span data-stu-id="0be0a-140">The *computed_column_expression* must be precise.</span></span> <span data-ttu-id="0be0a-141">如果下列一项或多项为真，则 *computed_column_expression* 是精确的：</span><span class="sxs-lookup"><span data-stu-id="0be0a-141">A *computed_column_expression* is precise when one or more of the following is true:</span></span>  
  
-   <span data-ttu-id="0be0a-142">表达式的数据类型不是 `float` 或 `real`。</span><span class="sxs-lookup"><span data-stu-id="0be0a-142">It is not an expression of the `float` or `real` data types.</span></span>  
  
-   <span data-ttu-id="0be0a-143">表达式定义中没有使用 `float` 或 `real` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="0be0a-143">It does not use a `float` or `real` data type in its definition.</span></span> <span data-ttu-id="0be0a-144">例如，在下列语句中，列 `y` 为 `int` 且具有确定性，但不精确。</span><span class="sxs-lookup"><span data-stu-id="0be0a-144">For example, in the following statement, column `y` is `int` and deterministic but not precise.</span></span>  
  
    ```  
    CREATE TABLE t2 (a int, b int, c int, x float,   
       y AS CASE x   
             WHEN 0 THEN a   
             WHEN 1 THEN b   
             ELSE c   
          END);  
    ```  
  
> [!NOTE]  
>  <span data-ttu-id="0be0a-145">任何 `float` 或 `real` 表达式都被认为是不精确的，不能作为索引键；`float` 或 `real` 表达式可以在索引视图中使用，但不能作为键使用。</span><span class="sxs-lookup"><span data-stu-id="0be0a-145">Any `float` or `real` expression is considered imprecise and cannot be a key of an index; a `float` or `real` expression can be used in an indexed view but not as a key.</span></span> <span data-ttu-id="0be0a-146">对于计算列同样如此。</span><span class="sxs-lookup"><span data-stu-id="0be0a-146">This is true also for computed columns.</span></span> <span data-ttu-id="0be0a-147">如果任何函数、表达式或用户定义函数包含任何 `float` 或 `real` 表达式，则被认为是不精确的。</span><span class="sxs-lookup"><span data-stu-id="0be0a-147">Any function, expression, or user-defined function is considered imprecise if it contains any `float` or `real` expressions.</span></span> <span data-ttu-id="0be0a-148">这也包括逻辑表达式（比较）。</span><span class="sxs-lookup"><span data-stu-id="0be0a-148">This includes logical ones (comparisons).</span></span>  
  
 <span data-ttu-id="0be0a-149">COLUMNPROPERTY 函数的 **IsPrecise** 属性报告 *computed_column_expression* 是否精确。</span><span class="sxs-lookup"><span data-stu-id="0be0a-149">The **IsPrecise** property of the COLUMNPROPERTY function reports whether a *computed_column_expression* is precise.</span></span>  
  
 <span data-ttu-id="0be0a-150">**Data Type Requirements**</span><span class="sxs-lookup"><span data-stu-id="0be0a-150">**Data Type Requirements**</span></span>  
  
-   <span data-ttu-id="0be0a-151">为计算列定义的*computed_column_expression*的计算结果不能为 `text` 、 `ntext` 或 `image` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="0be0a-151">The *computed_column_expression* defined for the computed column cannot evaluate to the `text`, `ntext`, or `image` data types.</span></span>  
  
-   <span data-ttu-id="0be0a-152">只要计算列的数据类型可以作为索引键列，从 `image`、`ntext`、`text`、`varchar(max)`、`nvarchar(max)`、`varbinary(max)` 和 `xml` 数据类型派生的计算列上就可以创建索引。</span><span class="sxs-lookup"><span data-stu-id="0be0a-152">Computed columns derived from `image`, `ntext`, `text`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, and `xml` data types can be indexed as long as the computed column data type is allowable as an index key column.</span></span>  
  
-   <span data-ttu-id="0be0a-153">只要计算列的数据类型可以作为非键索引列，从 `image`、`ntext` 和 `text` 数据类型派生的计算列就可以作为非聚集索引中的非键（包含性）列。</span><span class="sxs-lookup"><span data-stu-id="0be0a-153">Computed columns derived from `image`, `ntext`, and `text` data types can be nonkey (included) columns in a nonclustered index as long as the computed column data type is allowable as a nonkey index column.</span></span>  
  
 <span data-ttu-id="0be0a-154">**SET 选项要求**</span><span class="sxs-lookup"><span data-stu-id="0be0a-154">**SET Option Requirements**</span></span>  
  
-   <span data-ttu-id="0be0a-155">执行定义计算列的 CREATE TABLE 或 ALTER TABLE 语句时，必须将 ANSI_NULLS 连接级选项设置为 ON。</span><span class="sxs-lookup"><span data-stu-id="0be0a-155">The ANSI_NULLS connection-level option must be set to ON when the CREATE TABLE or ALTER TABLE statement that defines the computed column is executed.</span></span> <span data-ttu-id="0be0a-156">[OBJECTPROPERTY](/sql/t-sql/functions/objectpropertyex-transact-sql) 函数通过 **IsAnsiNullsOn** 属性报告此选项是否设置为 ON。</span><span class="sxs-lookup"><span data-stu-id="0be0a-156">The [OBJECTPROPERTY](/sql/t-sql/functions/objectpropertyex-transact-sql) function reports whether the option is on through the **IsAnsiNullsOn** property.</span></span>  
  
-   <span data-ttu-id="0be0a-157">对于在其中创建索引的连接和所有尝试执行 INSERT、UPDATE 或 DELETE 语句（将更改索引中的值）的连接，必须将六个 SET 选项设置为 ON，将一个选项设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="0be0a-157">The connection on which the index is created, and all connections trying INSERT, UPDATE, or DELETE statements that will change values in the index, must have six SET options set to ON and one option set to OFF.</span></span> <span data-ttu-id="0be0a-158">如果不具有上述选项设置的连接执行了任何 SELECT 语句，优化器将忽略计算列的索引。</span><span class="sxs-lookup"><span data-stu-id="0be0a-158">The optimizer ignores an index on a computed column for any SELECT statement executed by a connection that does not have these same option settings.</span></span>  
  
    -   <span data-ttu-id="0be0a-159">NUMERIC_ROUNDABORT 选项必须设置为 OFF，且下列选项必须设置为 ON：</span><span class="sxs-lookup"><span data-stu-id="0be0a-159">The NUMERIC_ROUNDABORT option must be set to OFF, and the following options must be set to ON:</span></span>  
  
    -   <span data-ttu-id="0be0a-160">ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="0be0a-160">ANSI_NULLS</span></span>  
  
    -   <span data-ttu-id="0be0a-161">ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="0be0a-161">ANSI_PADDING</span></span>  
  
    -   <span data-ttu-id="0be0a-162">ANSI_WARNINGS</span><span class="sxs-lookup"><span data-stu-id="0be0a-162">ANSI_WARNINGS</span></span>  
  
    -   <span data-ttu-id="0be0a-163">ARITHABORT</span><span class="sxs-lookup"><span data-stu-id="0be0a-163">ARITHABORT</span></span>  
  
    -   <span data-ttu-id="0be0a-164">CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="0be0a-164">CONCAT_NULL_YIELDS_NULL</span></span>  
  
    -   <span data-ttu-id="0be0a-165">QUOTED_IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="0be0a-165">QUOTED_IDENTIFIER</span></span>  
  
     <span data-ttu-id="0be0a-166">当数据库兼容级别设置为 90 或更高时，如果将 ANSI_WARNINGS 设置为 ON，则将使 ARITHABORT 隐式设置为 ON。</span><span class="sxs-lookup"><span data-stu-id="0be0a-166">Setting ANSI_WARNINGS to ON implicitly sets ARITHABORT to ON when the database compatibility level is set to 90 or higher.</span></span>  
  
##  <a name="creating-indexes-on-persisted-computed-columns"></a><a name="BKMK_persisted"></a> <span data-ttu-id="0be0a-167">对持久化计算列创建索引</span><span class="sxs-lookup"><span data-stu-id="0be0a-167">Creating Indexes on Persisted Computed Columns</span></span>  
 <span data-ttu-id="0be0a-168">如果计算列使用确定性但不精确的表达式定义，但在 CREATE TABLE 或 ALTER TABLE 语句中标记为 PERSISTED，则可以在该列上创建索引。</span><span class="sxs-lookup"><span data-stu-id="0be0a-168">You can create an index on a computed column that is defined with a deterministic, but imprecise, expression if the column is marked PERSISTED in the CREATE TABLE or ALTER TABLE statement.</span></span> <span data-ttu-id="0be0a-169">这意味着，在对 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 列创建索引时，以及在查询中引用该索引时，将使用这些持久值。</span><span class="sxs-lookup"><span data-stu-id="0be0a-169">This means that the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] uses these persisted values when it creates an index on the column, and when the index is referenced in a query.</span></span> <span data-ttu-id="0be0a-170">使用此选项可以在时对计算列创建索引，但这 [!INCLUDE[ssDE](../../../includes/dnprdnshort-md.md)] 既是确定性的，也是精确的。</span><span class="sxs-lookup"><span data-stu-id="0be0a-170">This option enables you to create an index on a computed column when [!INCLUDE[ssDE](../../../includes/dnprdnshort-md.md)], is both deterministic and precise.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="0be0a-171">相关内容</span><span class="sxs-lookup"><span data-stu-id="0be0a-171">Related Content</span></span>  
 [<span data-ttu-id="0be0a-172">COLUMNPROPERTY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0be0a-172">COLUMNPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/columnproperty-transact-sql)  
  
  
