---
title: 包含数据库的排序规则 | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- contained database, collations
ms.assetid: 4b44f6b9-2359-452f-8bb1-5520f2528483
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2648dbedea7708c4f39c922c56bba96cf38b0c0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690643"
---
# <a name="contained-database-collations"></a><span data-ttu-id="55fc2-102">包含数据库的排序规则</span><span class="sxs-lookup"><span data-stu-id="55fc2-102">Contained Database Collations</span></span>
  <span data-ttu-id="55fc2-103">许多属性会影响文本数据的排序顺序和相等语义，包括区分大小写、区分重音以及所用的基本语言。</span><span class="sxs-lookup"><span data-stu-id="55fc2-103">Various properties affect the sort order and equality semantics of textual data, including case sensitivity, accent sensitivity, and the base language being used.</span></span> <span data-ttu-id="55fc2-104">对于这些特性，可通过选择数据的排序规则来表示给 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="55fc2-104">These qualities are expressed to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] through the choice of collation for the data.</span></span> <span data-ttu-id="55fc2-105">有关排序规则本身的更深入讨论，请参阅 [排序规则和 Unicode 支持](../collations/collation-and-unicode-support.md)。</span><span class="sxs-lookup"><span data-stu-id="55fc2-105">For a more in-depth discussion of collations themselves, see [Collation and Unicode Support](../collations/collation-and-unicode-support.md).</span></span>  
  
 <span data-ttu-id="55fc2-106">排序规则不仅适用于用户表中存储的数据，还适用于由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 处理的所有文本，包括元数据、临时对象、变量名称等。在这些内容的处理方面，包含数据库和非包含数据库采用不同的方式。</span><span class="sxs-lookup"><span data-stu-id="55fc2-106">Collations apply not only to data stored in user tables, but to all text handled by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], including metadata, temporary objects, variable names, etc. The handling of these differs in contained and non-contained databases.</span></span> <span data-ttu-id="55fc2-107">此更改不会影响很多用户，而且有助于提供独立而统一的实例。</span><span class="sxs-lookup"><span data-stu-id="55fc2-107">This change will not affect many users, but helps provide instance independence and uniformity.</span></span> <span data-ttu-id="55fc2-108">但是，此更改也可能导致某些混淆，并可能使同时访问包含数据库和非包含数据库的会话出现问题。</span><span class="sxs-lookup"><span data-stu-id="55fc2-108">But this may also cause some confusion, as well as problems for sessions that access both contained and non-contained databases.</span></span>  
  
 <span data-ttu-id="55fc2-109">本主题阐明更改的内容，并考察这一更改可能导致问题的领域。</span><span class="sxs-lookup"><span data-stu-id="55fc2-109">This topic clarifies the content of the change, and examines areas where the change may cause problems.</span></span>  
  
## <a name="non-contained-databases"></a><span data-ttu-id="55fc2-110">非包含数据库</span><span class="sxs-lookup"><span data-stu-id="55fc2-110">Non-Contained Databases</span></span>  
 <span data-ttu-id="55fc2-111">所有数据库都有一种默认的排序规则（可在创建或更改数据库时设置）。</span><span class="sxs-lookup"><span data-stu-id="55fc2-111">All databases have a default collation (which can be set when creating or altering a database.</span></span> <span data-ttu-id="55fc2-112">此排序规则用于数据库中的所有元数据，以及数据库中所有字符串列的默认值。</span><span class="sxs-lookup"><span data-stu-id="55fc2-112">This collation is used for all metadata in the database, as well as the default for all string columns within the database.</span></span> <span data-ttu-id="55fc2-113">通过使用 `COLLATE` 子句，用户可为任何特定的列选择不同的排序规则。</span><span class="sxs-lookup"><span data-stu-id="55fc2-113">Users can choose a different collation for any particular column by using the `COLLATE` clause.</span></span>  
  
### <a name="example-1"></a><span data-ttu-id="55fc2-114">示例 1</span><span class="sxs-lookup"><span data-stu-id="55fc2-114">Example 1</span></span>  
 <span data-ttu-id="55fc2-115">例如，如果我们在北京工作，则可能会使用中文排序规则：</span><span class="sxs-lookup"><span data-stu-id="55fc2-115">For example, if we were working in Beijing, we might use a Chinese collation:</span></span>  
  
```sql  
ALTER DATABASE MyDB COLLATE Chinese_Simplified_Pinyin_100_CI_AS;  
```  
  
 <span data-ttu-id="55fc2-116">现在，如果我们创建一个列，其默认排序规则将是此中文排序规则，但我们可以根据需要选择其他排序规则：</span><span class="sxs-lookup"><span data-stu-id="55fc2-116">Now if we create a column, its default collation will be this Chinese collation, but we can choose another one if we want:</span></span>  
  
```sql  
CREATE TABLE MyTable  
      (mycolumn1 nvarchar,  
      mycolumn2 nvarchar COLLATE Frisian_100_CS_AS);  
GO  
SELECT name, collation_name  
FROM sys.columns  
WHERE name LIKE 'mycolumn%' ;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```sql  
name            collation_name  
--------------- ----------------------------------  
mycolumn1       Chinese_Simplified_Pinyin_100_CI_AS  
mycolumn2       Frisian_100_CS_AS  
```  
  
 <span data-ttu-id="55fc2-117">这看起来比较简单，但会引发几个问题。</span><span class="sxs-lookup"><span data-stu-id="55fc2-117">This appears relatively simple, but several problems arise.</span></span> <span data-ttu-id="55fc2-118">由于列的排序规则依赖于在其中创建表的数据库，因此使用存储在中的临时表会出现问题 `tempdb` 。</span><span class="sxs-lookup"><span data-stu-id="55fc2-118">Because the collation for a column is dependent on the database in which the table is created, problems arise with the use of temporary tables which are stored in `tempdb`.</span></span> <span data-ttu-id="55fc2-119">的排序规则 `tempdb` 通常与实例的排序规则匹配，而不必与数据库排序规则匹配。</span><span class="sxs-lookup"><span data-stu-id="55fc2-119">The collation of `tempdb` usually matches the collation for the instance, which does not have to match the database collation.</span></span>  
  
### <a name="example-2"></a><span data-ttu-id="55fc2-120">示例 2</span><span class="sxs-lookup"><span data-stu-id="55fc2-120">Example 2</span></span>  
 <span data-ttu-id="55fc2-121">假设在排序规则为 **Latin1_General** 的实例上使用上述（中文）数据库：</span><span class="sxs-lookup"><span data-stu-id="55fc2-121">For example, consider the (Chinese) database above when used on an instance with a **Latin1_General** collation:</span></span>  
  
```sql  
CREATE TABLE T1 (T1_txt nvarchar(max)) ;  
GO  
CREATE TABLE #T2 (T2_txt nvarchar(max)) ;  
GO  
```  
  
 <span data-ttu-id="55fc2-122">乍看起来这两个表似乎具有相同的架构，但由于数据库的排序规则不同，它们的值实际上并不兼容：</span><span class="sxs-lookup"><span data-stu-id="55fc2-122">At first glance, these two tables look like they have the same schema, but since the collations of the databases differ, the values are actually incompatible:</span></span>  
  
```  
SELECT T1_txt, T2_txt  
FROM T1   
JOIN #T2   
    ON T1.T1_txt = #T2.T2_txt  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 <span data-ttu-id="55fc2-123">消息 468，级别 16，状态 9，第 2 行</span><span class="sxs-lookup"><span data-stu-id="55fc2-123">Msg 468, Level 16, State 9, Line 2</span></span>  
  
 <span data-ttu-id="55fc2-124">无法解决等于运算中“Latin1_General_100_CI_AS_KS_WS_SC”与“Chinese_Simplified_Pinyin_100_CI_AS”之间的排序规则冲突。</span><span class="sxs-lookup"><span data-stu-id="55fc2-124">Cannot resolve the collation conflict between "Latin1_General_100_CI_AS_KS_WS_SC" and Chinese_Simplified_Pinyin_100_CI_AS" in the equal to operation.</span></span>  
  
 <span data-ttu-id="55fc2-125">通过显式排列临时表可修复此问题。</span><span class="sxs-lookup"><span data-stu-id="55fc2-125">We can fix this by explicitly collating the temporary table.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="55fc2-126">为 `DATABASE_DEFAULT` 子句提供了 `COLLATE` 关键字，使操作在一定程度上得到了简化。</span><span class="sxs-lookup"><span data-stu-id="55fc2-126">makes this somewhat easier by providing the `DATABASE_DEFAULT` keyword for the `COLLATE` clause.</span></span>  
  
```sql  
CREATE TABLE T1 (T1_txt nvarchar(max)) ;  
GO  
CREATE TABLE #T2 (T2_txt nvarchar(max) COLLATE DATABASE_DEFAULT);  
GO  
SELECT T1_txt, T2_txt  
FROM T1   
JOIN #T2   
    ON T1.T1_txt = #T2.T2_txt ;  
```  
  
 <span data-ttu-id="55fc2-127">现在此代码将可以正常运行。</span><span class="sxs-lookup"><span data-stu-id="55fc2-127">This now runs without error.</span></span>  
  
 <span data-ttu-id="55fc2-128">我们还可以看到，变量的行为也依赖于排序规则。</span><span class="sxs-lookup"><span data-stu-id="55fc2-128">We can also see collation-dependent behavior with variables.</span></span> <span data-ttu-id="55fc2-129">请考虑以下函数：</span><span class="sxs-lookup"><span data-stu-id="55fc2-129">Consider the following function:</span></span>  
  
```  
CREATE FUNCTION f(@x INT) RETURNS INT  
AS BEGIN   
      DECLARE @I INT = 1  
      DECLARE @?? INT = 2  
      RETURN @x * @i  
END;  
```  
  
 <span data-ttu-id="55fc2-130">这是一个相当特殊的函数。</span><span class="sxs-lookup"><span data-stu-id="55fc2-130">This is a rather peculiar function.</span></span> <span data-ttu-id="55fc2-131">在区分大小写的排序规则中， @i return 子句中的不能绑定到 @I 或 @??。</span><span class="sxs-lookup"><span data-stu-id="55fc2-131">In a case-sensitive collation, the @i in the return clause cannot bind to either @I or @??.</span></span> <span data-ttu-id="55fc2-132">在不区分大小写的 Latin1_General 排序规则中，@i 绑定到 @I，该函数返回 1。</span><span class="sxs-lookup"><span data-stu-id="55fc2-132">In a case-insensitive Latin1_General collation, @i binds to @I, and the function returns 1.</span></span> <span data-ttu-id="55fc2-133">但在不区分大小写的土耳其语排序规则中， @i 绑定到 @??, 并且函数返回2。</span><span class="sxs-lookup"><span data-stu-id="55fc2-133">But in a case-insensitive Turkish collation, @i binds to @??, and the function returns 2.</span></span> <span data-ttu-id="55fc2-134">如果在采用不同排序规则的实例之间移动数据库，则会给数据库造成严重的破坏。</span><span class="sxs-lookup"><span data-stu-id="55fc2-134">This can wreak havoc on a database that moves between instances with different collations.</span></span>  
  
## <a name="contained-databases"></a><span data-ttu-id="55fc2-135">包含的数据库</span><span class="sxs-lookup"><span data-stu-id="55fc2-135">Contained Databases</span></span>  
 <span data-ttu-id="55fc2-136">由于包含数据库的设计目标是让自身实现独立，因此必须切断它们对实例和 `tempdb` 排序规则的依赖。</span><span class="sxs-lookup"><span data-stu-id="55fc2-136">Since a design objective of contained databases is to make them self-contained, the dependence on the instance and `tempdb` collations must be severed.</span></span> <span data-ttu-id="55fc2-137">为此，包含数据库引入了目录排序规则的概念。</span><span class="sxs-lookup"><span data-stu-id="55fc2-137">To do this, contained databases introduce the concept of the catalog collation.</span></span> <span data-ttu-id="55fc2-138">目录排序规则适用于系统元数据和临时对象。</span><span class="sxs-lookup"><span data-stu-id="55fc2-138">The catalog collation is used for system metadata and transient objects.</span></span> <span data-ttu-id="55fc2-139">下面将详细介绍这一概念。</span><span class="sxs-lookup"><span data-stu-id="55fc2-139">Details are provided below.</span></span>  
  
 <span data-ttu-id="55fc2-140">如果某个包含数据库的目录排序规则是 **Latin1_General_100_CI_AS_WS_KS_SC**。</span><span class="sxs-lookup"><span data-stu-id="55fc2-140">In a contained database, the catalog collation **Latin1_General_100_CI_AS_WS_KS_SC**.</span></span> <span data-ttu-id="55fc2-141">则所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上的所有包含数据库都采用此排序规则，而且不能更改。</span><span class="sxs-lookup"><span data-stu-id="55fc2-141">This collation is the same for all contained databases on all instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and cannot be changed.</span></span>  
  
 <span data-ttu-id="55fc2-142">数据库排序规则将得到保留，但只能用作用户数据的默认排序规则。</span><span class="sxs-lookup"><span data-stu-id="55fc2-142">The database collation is retained, but is only used as the default collation for user data.</span></span> <span data-ttu-id="55fc2-143">默认情况下，数据库排序规则等于 model 数据库排序规则，但用户可通过 `CREATE` 或 `ALTER DATABASE` 命令更改为非包含数据库。</span><span class="sxs-lookup"><span data-stu-id="55fc2-143">By default, the database collation is equal to the model database collation, but can be changed by the user through a `CREATE` or `ALTER DATABASE` command as with non-contained databases.</span></span>  
  
 <span data-ttu-id="55fc2-144">`CATALOG_DEFAULT` 子句中提供了一个新关键字 `COLLATE`。</span><span class="sxs-lookup"><span data-stu-id="55fc2-144">A new keyword, `CATALOG_DEFAULT`, is available in the `COLLATE` clause.</span></span> <span data-ttu-id="55fc2-145">此关键字用作包含数据库和非包含数据库中当前元数据排序规则的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="55fc2-145">This is used as a shortcut to the current collation of metadata in both contained and non-contained databases.</span></span> <span data-ttu-id="55fc2-146">换言之，在非包含数据库中，`CATALOG_DEFAULT` 将返回当前的数据库排序规则，因为元数据是按数据库排序规则排列的。</span><span class="sxs-lookup"><span data-stu-id="55fc2-146">That is, in a non-contained database, `CATALOG_DEFAULT` will return the current database collation, since metadata is collated in the database collation.</span></span> <span data-ttu-id="55fc2-147">在包含数据库中，这两个值可能是不同的，因为用户可以更改数据库排序规则，以使其不同于目录排序规则。</span><span class="sxs-lookup"><span data-stu-id="55fc2-147">In a contained database, these two values may be different, since the user can change the database collation so that it does not match the catalog collation.</span></span>  
  
 <span data-ttu-id="55fc2-148">下表总结了非包含数据库和包含数据库中各个对象的行为：</span><span class="sxs-lookup"><span data-stu-id="55fc2-148">The behavior of various objects in both non-contained and contained databases is summarized in this table:</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="55fc2-149">**项**</span><span class="sxs-lookup"><span data-stu-id="55fc2-149">**Item**</span></span>|<span data-ttu-id="55fc2-150">**非包含数据库**</span><span class="sxs-lookup"><span data-stu-id="55fc2-150">**Non-Contained Database**</span></span>|<span data-ttu-id="55fc2-151">**包含数据库**</span><span class="sxs-lookup"><span data-stu-id="55fc2-151">**Contained Database**</span></span>|  
|<span data-ttu-id="55fc2-152">用户数据（默认）</span><span class="sxs-lookup"><span data-stu-id="55fc2-152">User Data (default)</span></span>|<span data-ttu-id="55fc2-153">COLLATE</span><span class="sxs-lookup"><span data-stu-id="55fc2-153">DATABASE_DEFAULT</span></span>|<span data-ttu-id="55fc2-154">COLLATE</span><span class="sxs-lookup"><span data-stu-id="55fc2-154">DATABASE_DEFAULT</span></span>|  
|<span data-ttu-id="55fc2-155">临时数据（默认）</span><span class="sxs-lookup"><span data-stu-id="55fc2-155">Temp Data (default)</span></span>|<span data-ttu-id="55fc2-156">TempDB 排序规则</span><span class="sxs-lookup"><span data-stu-id="55fc2-156">TempDB Collation</span></span>|<span data-ttu-id="55fc2-157">COLLATE</span><span class="sxs-lookup"><span data-stu-id="55fc2-157">DATABASE_DEFAULT</span></span>|  
|<span data-ttu-id="55fc2-158">元数据</span><span class="sxs-lookup"><span data-stu-id="55fc2-158">Metadata</span></span>|<span data-ttu-id="55fc2-159">DATABASE_DEFAULT/CATALOG_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="55fc2-159">DATABASE_DEFAULT / CATALOG_DEFAULT</span></span>|<span data-ttu-id="55fc2-160">CATALOG_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="55fc2-160">CATALOG_DEFAULT</span></span>|  
|<span data-ttu-id="55fc2-161">临时元数据</span><span class="sxs-lookup"><span data-stu-id="55fc2-161">Temporary Metadata</span></span>|<span data-ttu-id="55fc2-162">TempDB 排序规则</span><span class="sxs-lookup"><span data-stu-id="55fc2-162">tempdb Collation</span></span>|<span data-ttu-id="55fc2-163">CATALOG_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="55fc2-163">CATALOG_DEFAULT</span></span>|  
|<span data-ttu-id="55fc2-164">变量</span><span class="sxs-lookup"><span data-stu-id="55fc2-164">Variables</span></span>|<span data-ttu-id="55fc2-165">实例排序规则</span><span class="sxs-lookup"><span data-stu-id="55fc2-165">Instance Collation</span></span>|<span data-ttu-id="55fc2-166">CATALOG_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="55fc2-166">CATALOG_DEFAULT</span></span>|  
|<span data-ttu-id="55fc2-167">Goto 标签</span><span class="sxs-lookup"><span data-stu-id="55fc2-167">Goto Labels</span></span>|<span data-ttu-id="55fc2-168">实例排序规则</span><span class="sxs-lookup"><span data-stu-id="55fc2-168">Instance Collation</span></span>|<span data-ttu-id="55fc2-169">CATALOG_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="55fc2-169">CATALOG_DEFAULT</span></span>|  
|<span data-ttu-id="55fc2-170">游标名称</span><span class="sxs-lookup"><span data-stu-id="55fc2-170">Cursor Names</span></span>|<span data-ttu-id="55fc2-171">实例排序规则</span><span class="sxs-lookup"><span data-stu-id="55fc2-171">Instance Collation</span></span>|<span data-ttu-id="55fc2-172">CATALOG_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="55fc2-172">CATALOG_DEFAULT</span></span>|  
  
 <span data-ttu-id="55fc2-173">通过上述临时表示例可以看出，此排序规则行为使大多数临时表不再需要使用显式 `COLLATE` 子句。</span><span class="sxs-lookup"><span data-stu-id="55fc2-173">If we temp table example previously described, we can see that this collation behavior eliminates the need for an explicit `COLLATE` clause in most temp table uses.</span></span> <span data-ttu-id="55fc2-174">在包含数据库中，即使数据库和实例采用不同的排序规则，此代码现在也可以正常运行：</span><span class="sxs-lookup"><span data-stu-id="55fc2-174">In a contained database, this code now runs without error, even if the database and instance collations differ:</span></span>  
  
```sql  
CREATE TABLE T1 (T1_txt nvarchar(max)) ;  
GO  
CREATE TABLE #T2 (T2_txt nvarchar(max));  
GO  
SELECT T1_txt, T2_txt  
FROM T1   
JOIN #T2   
    ON T1.T1_txt = #T2.T2_txt ;  
```  
  
 <span data-ttu-id="55fc2-175">之所以能够正常运行，是因为 `T1_txt` 和 `T2_txt` 都按包含数据库的数据库排序规则排列。</span><span class="sxs-lookup"><span data-stu-id="55fc2-175">This works because both `T1_txt` and `T2_txt` are collated in the database collation of the contained database.</span></span>  
  
## <a name="crossing-between-contained-and-uncontained-contexts"></a><span data-ttu-id="55fc2-176">跨越包含和非包含上下文</span><span class="sxs-lookup"><span data-stu-id="55fc2-176">Crossing Between Contained and Uncontained Contexts</span></span>  
 <span data-ttu-id="55fc2-177">只要包含数据库中的会话仍处于包含状态，就必须保留在它所连接到的数据库内。</span><span class="sxs-lookup"><span data-stu-id="55fc2-177">As long as a session in a contained database remains contained, it must remain within the database to which it connected.</span></span> <span data-ttu-id="55fc2-178">此时的行为非常简单。</span><span class="sxs-lookup"><span data-stu-id="55fc2-178">In this case the behavior is very straightforward.</span></span> <span data-ttu-id="55fc2-179">但是，如果会话跨越包含和非包含上下文，其行为就会变得比较复杂，因为必须将两组规则联系起来。</span><span class="sxs-lookup"><span data-stu-id="55fc2-179">But if a session crosses between contained and non-contained contexts, the behavior becomes more complex, since the two sets of rules must be bridged.</span></span> <span data-ttu-id="55fc2-180">这种情况可能出现在部分包含数据库中，因为用户可对另一个数据库应用 `USE`。</span><span class="sxs-lookup"><span data-stu-id="55fc2-180">This can happen in a partially-contained database, since a user may `USE` to another database.</span></span> <span data-ttu-id="55fc2-181">在此情况下，排序规则之间的差异按以下原则处理。</span><span class="sxs-lookup"><span data-stu-id="55fc2-181">In this case, the difference in collation rules is handled by the following principle.</span></span>  
  
-   <span data-ttu-id="55fc2-182">批处理的排序规则行为由开始执行批处理的数据库决定。</span><span class="sxs-lookup"><span data-stu-id="55fc2-182">The collation behavior for a batch is determined by the database in which the batch begins.</span></span>  
  
 <span data-ttu-id="55fc2-183">请注意，此决定是在发出任何命令之前做出的，包括最初的 `USE`。</span><span class="sxs-lookup"><span data-stu-id="55fc2-183">Note that this decision is made before any commands are issued, including an initial `USE`.</span></span> <span data-ttu-id="55fc2-184">也即，如果批处理是在包含数据库中开始执行的，而应用于非包含数据库的第一个命令是 `USE`，则仍对该批处理应用包含数据库的排序规则行为。</span><span class="sxs-lookup"><span data-stu-id="55fc2-184">That is, if a batch begins in a contained database, but the first command is a `USE` to a non-contained database, the contained collation behavior will still be used for the batch.</span></span> <span data-ttu-id="55fc2-185">鉴于此，引用（例如对变量的引用）可能会产生多种可能的结果：</span><span class="sxs-lookup"><span data-stu-id="55fc2-185">Given this, a reference to a variable, for example, may have multiple possible outcomes:</span></span>  
  
-   <span data-ttu-id="55fc2-186">引用可能只找到一个匹配项。</span><span class="sxs-lookup"><span data-stu-id="55fc2-186">The reference may find exactly one match.</span></span> <span data-ttu-id="55fc2-187">在此情况下，该引用可正常操作。</span><span class="sxs-lookup"><span data-stu-id="55fc2-187">In this case, the reference will work without error.</span></span>  
  
-   <span data-ttu-id="55fc2-188">引用在当前排序规则中可能找不到匹配项，而原本存在匹配项。</span><span class="sxs-lookup"><span data-stu-id="55fc2-188">The reference may not find a match in the current collation where there was one before.</span></span> <span data-ttu-id="55fc2-189">这将引发一个错误，指示该变量不存在，即使已明确创建该变量也不例外。</span><span class="sxs-lookup"><span data-stu-id="55fc2-189">This will raise an error indicating that the variable does not exist, even though it was apparently created.</span></span>  
  
-   <span data-ttu-id="55fc2-190">引用可能会找到多个原本不同的匹配项。</span><span class="sxs-lookup"><span data-stu-id="55fc2-190">The reference may find multiple matches that were originally distinct.</span></span> <span data-ttu-id="55fc2-191">这也将引发错误。</span><span class="sxs-lookup"><span data-stu-id="55fc2-191">This will also raise an error.</span></span>  
  
 <span data-ttu-id="55fc2-192">我们将用几个示例加以说明。</span><span class="sxs-lookup"><span data-stu-id="55fc2-192">We'll illustrate this with a few examples.</span></span> <span data-ttu-id="55fc2-193">在这些示例中，假定存在一个名为 `MyCDB` 的部分包含数据库；其数据库排序规则设置为默认排序规则 **Latin1_General_100_CI_AS_WS_KS_SC**。</span><span class="sxs-lookup"><span data-stu-id="55fc2-193">For these we assume there is a partially-contained database named `MyCDB` with its database collation set to the default collation, **Latin1_General_100_CI_AS_WS_KS_SC**.</span></span> <span data-ttu-id="55fc2-194">实例排序规则为 `Latin1_General_100_CS_AS_WS_KS_SC`，</span><span class="sxs-lookup"><span data-stu-id="55fc2-194">We assume that the instance collation is `Latin1_General_100_CS_AS_WS_KS_SC`.</span></span> <span data-ttu-id="55fc2-195">两个排序规则的区别只在于是否区分大小写。</span><span class="sxs-lookup"><span data-stu-id="55fc2-195">The two collations differ only in case sensitivity.</span></span>  
  
### <a name="example-1"></a><span data-ttu-id="55fc2-196">示例 1</span><span class="sxs-lookup"><span data-stu-id="55fc2-196">Example 1</span></span>  
 <span data-ttu-id="55fc2-197">下面的示例演示引用只找到一个匹配项的情况。</span><span class="sxs-lookup"><span data-stu-id="55fc2-197">The following example illustrates the case where the reference finds exactly one match.</span></span>  
  
```  
USE MyCDB;  
GO  
  
CREATE TABLE #a(x int);  
INSERT INTO #a VALUES(1);  
GO  
  
USE master;  
GO  
  
SELECT * FROM #a;  
GO  
  
Results:  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
x  
-----------  
1  
```  
  
 <span data-ttu-id="55fc2-198">在此示例中，标识的 #a 同时绑定在不区分大小写的目录排序规则和区分大小写的实例排序规则中，代码可以正常运行。</span><span class="sxs-lookup"><span data-stu-id="55fc2-198">In this case, the identified #a binds in both the case-insensitive catalog collation and the case-sensitive instance collation, and the code works.</span></span>  
  
### <a name="example-2"></a><span data-ttu-id="55fc2-199">示例 2</span><span class="sxs-lookup"><span data-stu-id="55fc2-199">Example 2</span></span>  
 <span data-ttu-id="55fc2-200">下面的示例演示当前排序规则中原本有匹配项而引用却找不到匹配项的情况。</span><span class="sxs-lookup"><span data-stu-id="55fc2-200">The following example illustrates the case where the reference does not find a match in the current collation where there was one before.</span></span>  
  
```  
USE MyCDB;  
GO  
  
CREATE TABLE #a(x int);  
INSERT INTO #A VALUES(1);  
GO  
```  
  
 <span data-ttu-id="55fc2-201">在此示例中，#A 绑定到不区分大小写的默认排序规则中的 #a，而且插入部分可正常运行。</span><span class="sxs-lookup"><span data-stu-id="55fc2-201">Here, the #A binds to #a in the case-insensitive default collation, and the insert works,</span></span>  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
(1 row(s) affected)  
```  
  
 <span data-ttu-id="55fc2-202">但如果继续运行脚本...</span><span class="sxs-lookup"><span data-stu-id="55fc2-202">But if we continue the script...</span></span>  
  
```  
USE master;  
GO  
  
SELECT * FROM #A;  
GO  
```  
  
 <span data-ttu-id="55fc2-203">将显示一个错误，因为我们尝试绑定到区分大小写的实例排序规则中的 #A；</span><span class="sxs-lookup"><span data-stu-id="55fc2-203">We get an error trying to bind to #A in the case-sensitive instance collation;</span></span>  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 <span data-ttu-id="55fc2-204">消息 208，级别 16，状态 0，第 2 行</span><span class="sxs-lookup"><span data-stu-id="55fc2-204">Msg 208, Level 16, State 0, Line 2</span></span>  
  
 <span data-ttu-id="55fc2-205">对象名“#A”无效。</span><span class="sxs-lookup"><span data-stu-id="55fc2-205">Invalid object name '#A'.</span></span>  
  
### <a name="example-3"></a><span data-ttu-id="55fc2-206">示例 3</span><span class="sxs-lookup"><span data-stu-id="55fc2-206">Example 3</span></span>  
 <span data-ttu-id="55fc2-207">下面的示例演示引用找到多个原本不同的匹配项的情况。</span><span class="sxs-lookup"><span data-stu-id="55fc2-207">The following example illustrates the case where the reference finds multiple matches that were originally distinct.</span></span> <span data-ttu-id="55fc2-208">首先，我们开始 `tempdb` (与实例) 具有相同的区分大小写的排序规则，并执行以下语句。</span><span class="sxs-lookup"><span data-stu-id="55fc2-208">First, we start in `tempdb` (which has the same case-sensitive collation as our instance) and execute the following statements.</span></span>  
  
```  
USE tempdb;  
GO  
  
CREATE TABLE #a(x int);  
GO  
CREATE TABLE #A(x int);  
GO  
INSERT INTO #a VALUES(1);  
GO  
INSERT INTO #A VALUES(2);  
GO  
```  
  
 <span data-ttu-id="55fc2-209">此操作成功，因为采用此排序规则的表是不同的。</span><span class="sxs-lookup"><span data-stu-id="55fc2-209">This succeeds, since the tables are distinct in this collation:</span></span>  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
(1 row(s) affected)  
(1 row(s) affected)  
```  
  
 <span data-ttu-id="55fc2-210">但是，一旦进入包含数据库，我们就会发现无法再绑定到这些表。</span><span class="sxs-lookup"><span data-stu-id="55fc2-210">If we move into our contained database, however, we find that we can no longer bind to these tables.</span></span>  
  
```  
USE MyCDB;  
GO  
SELECT * FROM #a;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 <span data-ttu-id="55fc2-211">消息 12800，级别 16，状态 1，第 2 行</span><span class="sxs-lookup"><span data-stu-id="55fc2-211">Msg 12800, Level 16, State 1, Line 2</span></span>  
  
 <span data-ttu-id="55fc2-212">对临时表名称“#a”的引用不明确，无法解析。</span><span class="sxs-lookup"><span data-stu-id="55fc2-212">The reference to temp table name '#a' is ambiguous and cannot be resolved.</span></span> <span data-ttu-id="55fc2-213">可能的候选项是“#a”和“#A”。</span><span class="sxs-lookup"><span data-stu-id="55fc2-213">Possible candidates are '#a' and '#A'.</span></span>  
  
## <a name="conclusion"></a><span data-ttu-id="55fc2-214">结束语</span><span class="sxs-lookup"><span data-stu-id="55fc2-214">Conclusion</span></span>  
 <span data-ttu-id="55fc2-215">与非包含数据库相比，包含数据库的排序规则行为略有不同。</span><span class="sxs-lookup"><span data-stu-id="55fc2-215">The collation behavior of contained databases differs subtly from that in non-contained databases.</span></span> <span data-ttu-id="55fc2-216">此行为通常是有益的，因为它可以提供独立而简单的实例。</span><span class="sxs-lookup"><span data-stu-id="55fc2-216">This behavior is generally beneficial, providing instance-independence and simplicity.</span></span> <span data-ttu-id="55fc2-217">某些用户可能会遇到问题，特别是当会话同时访问包含数据库和非包含数据库时。</span><span class="sxs-lookup"><span data-stu-id="55fc2-217">Some users may have issues, particularly when a session accesses both contained and non-contained databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55fc2-218">另请参阅</span><span class="sxs-lookup"><span data-stu-id="55fc2-218">See Also</span></span>  
 [<span data-ttu-id="55fc2-219">包含的数据库</span><span class="sxs-lookup"><span data-stu-id="55fc2-219">Contained Databases</span></span>](contained-databases.md)  
  
  
