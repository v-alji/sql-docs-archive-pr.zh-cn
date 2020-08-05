---
title: 数据库标识符 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- regular identifiers [SQL Server]
- identifiers [SQL Server]
- names [SQL Server], identifiers
- identifiers [SQL Server], about identifiers
- SQL Server identifiers
- Transact-SQL identifiers
- database objects [SQL Server], names
ms.assetid: 171291bb-f57f-4ad1-8cea-0b092d5d150c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 347b20c12a0ac5edd82172741377617aa0fe12c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581307"
---
# <a name="database-identifiers"></a><span data-ttu-id="dbf7b-102">数据库标识符</span><span class="sxs-lookup"><span data-stu-id="dbf7b-102">Database Identifiers</span></span>
  <span data-ttu-id="dbf7b-103">数据库对象的名称即为其标识符。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-103">The database object name is referred to as its identifier.</span></span> <span data-ttu-id="dbf7b-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的所有内容都可以有标识符。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-104">Everything in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can have an identifier.</span></span> <span data-ttu-id="dbf7b-105">服务器、数据库和数据库对象（例如表、视图、列、索引、触发器、过程、约束及规则等）都可以有标识符。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-105">Servers, databases, and database objects, such as tables, views, columns, indexes, triggers, procedures, constraints, and rules, can have identifiers.</span></span> <span data-ttu-id="dbf7b-106">大多数对象要求有标识符，但对有些对象（例如约束），标识符是可选的。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-106">Identifiers are required for most objects, but are optional for some objects such as constraints.</span></span>  
  
 <span data-ttu-id="dbf7b-107">对象标识符是在定义对象时创建的。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-107">An object identifier is created when the object is defined.</span></span> <span data-ttu-id="dbf7b-108">标识符随后用于引用该对象。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-108">The identifier is then used to reference the object.</span></span> <span data-ttu-id="dbf7b-109">例如，下列语句创建一个标识符为 `TableX`的表，该表中有两列的标识符分别是 `KeyCol` 和 `Description`：</span><span class="sxs-lookup"><span data-stu-id="dbf7b-109">For example, the following statement creates a table with the identifier `TableX`, and two columns with the identifiers `KeyCol` and `Description`:</span></span>  
  
```  
CREATE TABLE TableX  
(KeyCol INT PRIMARY KEY, Description nvarchar(80))  
```  
  
 <span data-ttu-id="dbf7b-110">此表还有一个未命名的约束。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-110">This table also has an unnamed constraint.</span></span> <span data-ttu-id="dbf7b-111">`PRIMARY KEY` 约束没有标识符。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-111">The `PRIMARY KEY` constraint has no identifier.</span></span>  
  
 <span data-ttu-id="dbf7b-112">标识符的排序规则取决于定义标识符的级别。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-112">The collation of an identifier depends on the level at which it is defined.</span></span> <span data-ttu-id="dbf7b-113">为实例级对象（如登录名和数据库名）的标识符分配实例的默认排序规则。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-113">Identifiers of instance-level objects, such as logins and database names, are assigned the default collation of the instance.</span></span> <span data-ttu-id="dbf7b-114">为数据库对象（如表、视图和列名）的标识符分配数据库的默认排序规则。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-114">Identifiers of objects in a database, such as tables, views, and column names, are assigned the default collation of the database.</span></span> <span data-ttu-id="dbf7b-115">例如，对于名称差别仅在于大小写的两个表，可在使用区分大小写排序规则的数据库中创建，但不能在使用不区分大小写排序规则的数据库中创建。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-115">For example, two tables with names that differ only in case can be created in a database that has case-sensitive collation, but cannot be created in a database that has case-insensitive collation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dbf7b-116">变量的名称或函数和存储过程的参数必须符合 [!INCLUDE[tsql](../../includes/tsql-md.md)] 标识符的规则。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-116">The names of variables, or the parameters of functions and stored procedures must comply with the rules for [!INCLUDE[tsql](../../includes/tsql-md.md)] identifiers.</span></span>  
  
## <a name="classes-of-identifiers"></a><span data-ttu-id="dbf7b-117">标识符的种类</span><span class="sxs-lookup"><span data-stu-id="dbf7b-117">Classes of Identifiers</span></span>  
 <span data-ttu-id="dbf7b-118">有两类标识符：</span><span class="sxs-lookup"><span data-stu-id="dbf7b-118">There are two classes of identifiers:</span></span>  
  
 <span data-ttu-id="dbf7b-119">常规标识符</span><span class="sxs-lookup"><span data-stu-id="dbf7b-119">Regular identifiers</span></span>  
 <span data-ttu-id="dbf7b-120">符合标识符的格式规则。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-120">Comply with the rules for the format of identifiers.</span></span> <span data-ttu-id="dbf7b-121">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句中使用常规标识符时不用将其分隔开。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-121">Regular identifiers are not delimited when they are used in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
```  
SELECT *  
FROM TableX  
WHERE KeyCol = 124  
```  
  
 <span data-ttu-id="dbf7b-122">分隔标识符</span><span class="sxs-lookup"><span data-stu-id="dbf7b-122">Delimited identifiers</span></span>  
 <span data-ttu-id="dbf7b-123">包含在双引号 (") 或者方括号 ([ ]) 内。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-123">Are enclosed in double quotation marks (") or brackets ([ ]).</span></span> <span data-ttu-id="dbf7b-124">不会分隔符合标识符格式规则的标识符。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-124">Identifiers that comply with the rules for the format of identifiers might not be delimited.</span></span> <span data-ttu-id="dbf7b-125">例如：</span><span class="sxs-lookup"><span data-stu-id="dbf7b-125">For example:</span></span>  
  
```  
SELECT *  
FROM [TableX]         --Delimiter is optional.  
WHERE [KeyCol] = 124  --Delimiter is optional.  
```  
  
 <span data-ttu-id="dbf7b-126">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句中，必须对不符合所有标识符规则的标识符进行分隔。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-126">Identifiers that do not comply with all the rules for identifiers must be delimited in a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="dbf7b-127">例如：</span><span class="sxs-lookup"><span data-stu-id="dbf7b-127">For example:</span></span>  
  
```  
SELECT *  
FROM [My Table]      --Identifier contains a space and uses a reserved keyword.  
WHERE [order] = 10   --Identifier is a reserved keyword.  
```  
  
 <span data-ttu-id="dbf7b-128">常规标识符和分隔标识符包含的字符数都必须在 1 到 128 之间。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-128">Both regular and delimited identifiers must contain from 1 through 128 characters.</span></span> <span data-ttu-id="dbf7b-129">对于本地临时表，标识符最多可以有 116 个字符。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-129">For local temporary tables, the identifier can have a maximum of 116 characters.</span></span>  
  
## <a name="rules-for-regular-identifiers"></a><span data-ttu-id="dbf7b-130">常规标识符规则</span><span class="sxs-lookup"><span data-stu-id="dbf7b-130">Rules for Regular Identifiers</span></span>  
 <span data-ttu-id="dbf7b-131">变量、函数和存储过程的名称必须符合 [!INCLUDE[tsql](../../includes/tsql-md.md)] 标识符的规则。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-131">The names of variables, functions, and stored procedures must comply with the following rules for [!INCLUDE[tsql](../../includes/tsql-md.md)] identifiers.</span></span>  
  
1.  <span data-ttu-id="dbf7b-132">第一个字符必须是下列字符之一：</span><span class="sxs-lookup"><span data-stu-id="dbf7b-132">The first character must be one of the following:</span></span>  
  
    -   <span data-ttu-id="dbf7b-133">Unicode 标准 3.2 定义的字母，</span><span class="sxs-lookup"><span data-stu-id="dbf7b-133">A letter as defined by the Unicode Standard 3.2.</span></span> <span data-ttu-id="dbf7b-134">Unicode 中定义的字母包括拉丁字符 a-z 和 A-Z，以及来自其他语言的字母字符。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-134">The Unicode definition of letters includes Latin characters from a through z, from A through Z, and also letter characters from other languages.</span></span>  
  
    -   <span data-ttu-id="dbf7b-135">下划线 (_)、at 符号 (@) 或数字符号 (#)。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-135">The underscore (_), at sign (@), or number sign (#).</span></span>  
  
         <span data-ttu-id="dbf7b-136">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，某些位于标识符开头位置的符号具有特殊意义。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-136">Certain symbols at the beginning of an identifier have special meaning in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="dbf7b-137">以 at 符号开头的常规标识符始终表示局部变量或参数，并且不能用作任何其他类型的对象的名称。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-137">A regular identifier that starts with the at sign always denotes a local variable or parameter and cannot be used as the name of any other type of object.</span></span> <span data-ttu-id="dbf7b-138">以一个数字符号开头的标识符表示临时表或过程。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-138">An identifier that starts with a number sign denotes a temporary table or procedure.</span></span> <span data-ttu-id="dbf7b-139">以两个数字符号 (##) 开头的标识符表示全局临时对象。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-139">An identifier that starts with double number signs (##) denotes a global temporary object.</span></span> <span data-ttu-id="dbf7b-140">虽然数字符号或两个数字符号字符可用作其他类型对象名的开头，但是我们建议不要这样做。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-140">Although the number sign or double number sign characters can be used to begin the names of other types of objects, we do not recommend this practice.</span></span>  
  
         <span data-ttu-id="dbf7b-141">某些 [!INCLUDE[tsql](../../includes/tsql-md.md)] 函数的名称以两个 at 符号 (@@) 开头。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-141">Some [!INCLUDE[tsql](../../includes/tsql-md.md)] functions have names that start with double at signs (@@).</span></span> <span data-ttu-id="dbf7b-142">为了避免与这些函数混淆，不应使用以 @@ 开头的名称。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-142">To avoid confusion with these functions, you should not use names that start with @@.</span></span>  
  
2.  <span data-ttu-id="dbf7b-143">后续字符可以包括：</span><span class="sxs-lookup"><span data-stu-id="dbf7b-143">Subsequent characters can include the following:</span></span>  
  
    -   <span data-ttu-id="dbf7b-144">Unicode 标准 3.2 定义的字母。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-144">Letters as defined in the Unicode Standard 3.2.</span></span>  
  
    -   <span data-ttu-id="dbf7b-145">基本拉丁字符或其他国家/地区字符中的十进制数字。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-145">Decimal numbers from either Basic Latin or other national scripts.</span></span>  
  
    -   <span data-ttu-id="dbf7b-146">at 符号、美元符号 ($)、数字符号或下划线。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-146">The at sign, dollar sign ($), number sign, or underscore.</span></span>  
  
3.  <span data-ttu-id="dbf7b-147">标识符必须不能是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 保留字。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-147">The identifier must not be a [!INCLUDE[tsql](../../includes/tsql-md.md)] reserved word.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="dbf7b-148">保留保留字的大写和小写版本。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-148">reserves both the uppercase and lowercase versions of reserved words.</span></span> <span data-ttu-id="dbf7b-149">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句中使用标识符时，不符合这些规则的标识符必须由双引号或括号分隔。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-149">When identifiers are used in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, the identifiers that do not comply with these rules must be delimited by double quotation marks or brackets.</span></span> <span data-ttu-id="dbf7b-150">保留字依赖于数据库兼容级别。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-150">The words that are reserved depend on the database compatibility level.</span></span> <span data-ttu-id="dbf7b-151">可通过使用 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) 语句设置该级别。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-151">This level can be set by using the [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) statement.</span></span>  
  
4.  <span data-ttu-id="dbf7b-152">不允许嵌入空格或特殊字符。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-152">Embedded spaces or special characters are not allowed.</span></span>  
  
5.  <span data-ttu-id="dbf7b-153">不允许使用增补字符。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-153">Supplementary characters are not allowed.</span></span>  
  
 <span data-ttu-id="dbf7b-154">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句中使用标识符时，不符合这些规则的标识符必须由双引号或括号分隔。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-154">When identifiers are used in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, the identifiers that do not comply with these rules must be delimited by double quotation marks or brackets.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dbf7b-155">一些常规标识符格式规则取决于数据库兼容级别。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-155">Some rules for the format of regular identifiers depend on the database compatibility level.</span></span> <span data-ttu-id="dbf7b-156">该级别可以使用 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)设置。</span><span class="sxs-lookup"><span data-stu-id="dbf7b-156">This level can be set by using [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbf7b-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dbf7b-157">See Also</span></span>  
 <span data-ttu-id="dbf7b-158">[ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dbf7b-158">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 <span data-ttu-id="dbf7b-159">[CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dbf7b-159">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 <span data-ttu-id="dbf7b-160">[CREATE DEFAULT (Transact-SQL)](/sql/t-sql/statements/create-default-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dbf7b-160">[CREATE DEFAULT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-default-transact-sql) </span></span>  
 <span data-ttu-id="dbf7b-161">[CREATE PROCEDURE (Transact-SQL)](/sql/t-sql/statements/create-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dbf7b-161">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span></span>  
 <span data-ttu-id="dbf7b-162">[CREATE RULE (Transact-SQL)](/sql/t-sql/statements/create-rule-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dbf7b-162">[CREATE RULE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-rule-transact-sql) </span></span>  
 <span data-ttu-id="dbf7b-163">[CREATE TABLE (Transact-SQL)](/sql/t-sql/statements/create-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dbf7b-163">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span></span>  
 <span data-ttu-id="dbf7b-164">[CREATE TRIGGER (Transact-SQL)](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dbf7b-164">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 <span data-ttu-id="dbf7b-165">[CREATE VIEW (Transact-SQL)](/sql/t-sql/statements/create-view-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dbf7b-165">[CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql) </span></span>  
 <span data-ttu-id="dbf7b-166">[DECLARE @local_variable (Transact-SQL)](/sql/t-sql/language-elements/declare-local-variable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dbf7b-166">[DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) </span></span>  
 <span data-ttu-id="dbf7b-167">[DELETE (Transact-SQL)](/sql/t-sql/statements/delete-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dbf7b-167">[DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) </span></span>  
 <span data-ttu-id="dbf7b-168">[INSERT (Transact-SQL)](/sql/t-sql/statements/insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dbf7b-168">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span></span>  
 <span data-ttu-id="dbf7b-169">[保留关键字 (Transact-SQL)](/sql/t-sql/language-elements/reserved-keywords-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dbf7b-169">[Reserved Keywords &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reserved-keywords-transact-sql) </span></span>  
 <span data-ttu-id="dbf7b-170">[SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dbf7b-170">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="dbf7b-171">UPDATE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="dbf7b-171">UPDATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/update-transact-sql)  
  
  
