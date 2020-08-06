---
title: 设置或更改列排序规则 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- tempdb database [SQL Server], collations
- collations [SQL Server], column
ms.assetid: d7a9638b-717c-4680-9b98-8849081e08be
author: stevestein
ms.author: sstein
ms.openlocfilehash: 05b8211569b6ce83faaec043e5eb527a60f0ddab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591397"
---
# <a name="set-or-change-the-column-collation"></a><span data-ttu-id="a051c-102">设置或更改列排序规则</span><span class="sxs-lookup"><span data-stu-id="a051c-102">Set or Change the Column Collation</span></span>
  <span data-ttu-id="a051c-103">可以覆盖 `char`、`varchar`、`text`、`nchar`、`nvarchar` 和 `ntext` 数据的数据库排序规则，方法是为表的特定列指定不同的排序规则并使用以下方式之一：</span><span class="sxs-lookup"><span data-stu-id="a051c-103">You can override the database collation for `char`, `varchar`, `text`, `nchar`, `nvarchar`, and `ntext` data by specifying a different collation for a specific column of a table and using one of the following:</span></span>  
  
-   <span data-ttu-id="a051c-104">[CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) 和 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql)的 COLLATE 子句。</span><span class="sxs-lookup"><span data-stu-id="a051c-104">The COLLATE clause of [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) and [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql).</span></span> <span data-ttu-id="a051c-105">例如：</span><span class="sxs-lookup"><span data-stu-id="a051c-105">For example:</span></span>  
  
    ```  
    CREATE TABLE dbo.MyTable  
      (PrimaryKey   int PRIMARY KEY,  
       CharCol      varchar(10) COLLATE French_CI_AS NOT NULL  
      );  
    GO  
    ALTER TABLE dbo.MyTable ALTER COLUMN CharCol  
                varchar(10)COLLATE Latin1_General_CI_AS NOT NULL;  
    GO  
    ```  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="a051c-106">.</span><span class="sxs-lookup"><span data-stu-id="a051c-106">.</span></span> <span data-ttu-id="a051c-107">有关详细信息，请参阅 [排序规则和 Unicode 支持](collation-and-unicode-support.md)。</span><span class="sxs-lookup"><span data-stu-id="a051c-107">For more information, [Collation and Unicode Support](collation-and-unicode-support.md).</span></span>  
  
-   <span data-ttu-id="a051c-108">使用 `Column.Collation` 管理对象中的属性 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SMO) 。</span><span class="sxs-lookup"><span data-stu-id="a051c-108">Using the `Column.Collation` property in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO).</span></span>  
  
 <span data-ttu-id="a051c-109">如果下列其中之一当前正在引用一个列，则无法更改该列的排序规则。</span><span class="sxs-lookup"><span data-stu-id="a051c-109">You cannot change the collation of a column that is currently referenced by any one of the following:</span></span>  
  
-   <span data-ttu-id="a051c-110">计算列</span><span class="sxs-lookup"><span data-stu-id="a051c-110">A computed column</span></span>  
  
-   <span data-ttu-id="a051c-111">索引</span><span class="sxs-lookup"><span data-stu-id="a051c-111">An index</span></span>  
  
-   <span data-ttu-id="a051c-112">自动生成或由 CREATE STATISTICS 语句生成的分发统计信息</span><span class="sxs-lookup"><span data-stu-id="a051c-112">Distribution statistics, either generated automatically or by the CREATE STATISTICS statement</span></span>  
  
-   <span data-ttu-id="a051c-113">CHECK 约束</span><span class="sxs-lookup"><span data-stu-id="a051c-113">A CHECK constraint</span></span>  
  
-   <span data-ttu-id="a051c-114">FOREIGN KEY 约束</span><span class="sxs-lookup"><span data-stu-id="a051c-114">A FOREIGN KEY constraint</span></span>  
  
 <span data-ttu-id="a051c-115">使用 **tempdb**时， [COLLATE](/sql/t-sql/statements/collations) 子句包括了 *database_default* 选项，以此来指定对于该连接，临时表中的列使用当前用户数据库的默认排序规则而非 **tempdb**的排序规则。</span><span class="sxs-lookup"><span data-stu-id="a051c-115">When you work with **tempdb**, the [COLLATE](/sql/t-sql/statements/collations) clause includes a *database_default* option to specify that a column in a temporary table uses the collation default of the current user database for the connection instead of the collation of **tempdb**.</span></span>  
  
## <a name="collations-and-text-columns"></a><span data-ttu-id="a051c-116">排序规则和文本列</span><span class="sxs-lookup"><span data-stu-id="a051c-116">Collations and text Columns</span></span>  
 <span data-ttu-id="a051c-117">如果 `text` 列的排序规则不同于数据库默认排序规则的代码页，则可以在该列中插入值或更新该列中的值。</span><span class="sxs-lookup"><span data-stu-id="a051c-117">You can insert or update values in a `text` column whose collation is different from the code page of the default collation of the database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a051c-118">会隐式地将这些值转换为该列的排序规则。</span><span class="sxs-lookup"><span data-stu-id="a051c-118">implicitly converts the values to the collation of the column.</span></span>  
  
## <a name="collations-and-tempdb"></a><span data-ttu-id="a051c-119">排序规则和 tempdb</span><span class="sxs-lookup"><span data-stu-id="a051c-119">Collations and tempdb</span></span>  
 <span data-ttu-id="a051c-120">每次启动 **时，都会创建** tempdb [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库。该数据库与 **model** 数据库具有相同的默认排序规则。</span><span class="sxs-lookup"><span data-stu-id="a051c-120">The **tempdb** database is built every time [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is started and has the same default collation as the **model** database.</span></span> <span data-ttu-id="a051c-121">这通常与实例的默认排序规则相同。</span><span class="sxs-lookup"><span data-stu-id="a051c-121">This is typically the same as the default collation of the instance.</span></span> <span data-ttu-id="a051c-122">如果为创建的用户数据库指定的默认排序规则与 **model**的排序规则不同，则该用户数据库与 **tempdb**的默认排序规则也不同。</span><span class="sxs-lookup"><span data-stu-id="a051c-122">If you create a user database and specify a different default collation than **model**, the user database has a different default collation than **tempdb**.</span></span> <span data-ttu-id="a051c-123">所有临时存储过程或临时表都创建和存储在 **tempdb**中。</span><span class="sxs-lookup"><span data-stu-id="a051c-123">All temporary stored procedures or temporary tables are created and stored in **tempdb**.</span></span> <span data-ttu-id="a051c-124">这意味着临时表中的所有隐式列以及临时存储过程中的所有强制默认常量、变量和参数都具有与可比较对象（在永久表和存储过程中创建）不同的排序规则。</span><span class="sxs-lookup"><span data-stu-id="a051c-124">This means that all implicit columns in temporary tables and all coercible-default constants, variables, and parameters in temporary stored procedures have collations that are different from comparable objects created in permanent tables and stored procedures.</span></span>  
  
 <span data-ttu-id="a051c-125">这将导致用户定义的数据库和系统数据库对象之间的排序规则出现互相不匹配的问题。</span><span class="sxs-lookup"><span data-stu-id="a051c-125">This could lead to problems with a mismatch in collations between user-defined databases and system database objects.</span></span> <span data-ttu-id="a051c-126">例如， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例使用 Latin1_General_CS_AS 排序规则，而您执行以下语句：</span><span class="sxs-lookup"><span data-stu-id="a051c-126">For example, an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses the Latin1_General_CS_AS collation and you execute the following statements:</span></span>  
  
```  
CREATE DATABASE TestDB COLLATE Estonian_CS_AS;  
USE TestDB;  
CREATE TABLE TestPermTab (PrimaryKey int PRIMARY KEY, Col1 nchar );  
```  
  
 <span data-ttu-id="a051c-127">在此系统中， **tempdb** 数据库使用代码页 1252 的 Latin1_General_CS_AS 排序规则， `TestDB` 和 `TestPermTab.Col1` 使用代码页 1257 的 `Estonian_CS_AS` 排序规则。</span><span class="sxs-lookup"><span data-stu-id="a051c-127">In this system, the **tempdb** database uses the Latin1_General_CS_AS collation with code page 1252, and `TestDB` and `TestPermTab.Col1` use the `Estonian_CS_AS` collation with code page 1257.</span></span> <span data-ttu-id="a051c-128">例如：</span><span class="sxs-lookup"><span data-stu-id="a051c-128">For example:</span></span>  
  
```  
USE TestDB;  
GO  
-- Create a temporary table with the same column declarations  
-- as TestPermTab  
CREATE TABLE #TestTempTab (PrimaryKey int PRIMARY KEY, Col1 nchar );  
INSERT INTO #TestTempTab  
         SELECT * FROM TestPermTab;  
GO  
```  
  
 <span data-ttu-id="a051c-129">在上述示例中， **tempdb** 数据库使用 Latin1_General_CS_AS 排序规则， `TestDB` 和 `TestTab.Col1` 使用 `Estonian_CS_AS` 排序规则。</span><span class="sxs-lookup"><span data-stu-id="a051c-129">With the previous example, the **tempdb** database uses the Latin1_General_CS_AS collation, and `TestDB` and `TestTab.Col1` use the `Estonian_CS_AS` collation.</span></span> <span data-ttu-id="a051c-130">例如：</span><span class="sxs-lookup"><span data-stu-id="a051c-130">For example:</span></span>  
  
```  
SELECT * FROM TestPermTab AS a INNER JOIN #TestTempTab on a.Col1 = #TestTempTab.Col1;  
```  
  
 <span data-ttu-id="a051c-131">由于 **tempdb** 使用默认的服务器排序规则，而 `TestPermTab.Col1` 使用其他排序规则，因此 SQL Server 会返回如下错误：“无法解决等于运算中 'Latin1_General_CI_AS_KS_WS' 与 'Estonian_CS_AS' 之间的排序规则冲突。”</span><span class="sxs-lookup"><span data-stu-id="a051c-131">Because **tempdb** uses the default server collation and `TestPermTab.Col1` uses a different collation, SQL Server returns this error: "Cannot resolve collation conflict between 'Latin1_General_CI_AS_KS_WS' and 'Estonian_CS_AS' in equal to operation."</span></span>  
  
 <span data-ttu-id="a051c-132">为防止出现此错误，可以使用下列方法之一：</span><span class="sxs-lookup"><span data-stu-id="a051c-132">To prevent the error, you can use one of the following alternatives:</span></span>  
  
-   <span data-ttu-id="a051c-133">指定临时表列使用用户数据库（而不是 **tempdb**）的默认排序规则。</span><span class="sxs-lookup"><span data-stu-id="a051c-133">Specify that the temporary table column use the default collation of the user database, not **tempdb**.</span></span> <span data-ttu-id="a051c-134">如果系统需要，这可以使临时表在多个数据库中使用具有类似格式的表。</span><span class="sxs-lookup"><span data-stu-id="a051c-134">This enables the temporary table to work with similarly formatted tables in multiple databases, if that is required of your system.</span></span>  
  
    ```  
    CREATE TABLE #TestTempTab  
       (PrimaryKey int PRIMARY KEY,  
        Col1 nchar COLLATE database_default  
       );  
    ```  
  
-   <span data-ttu-id="a051c-135">为 `#TestTempTab` 列指定正确的排序规则：</span><span class="sxs-lookup"><span data-stu-id="a051c-135">Specify the correct collation for the `#TestTempTab` column:</span></span>  
  
    ```  
    CREATE TABLE #TestTempTab  
       (PrimaryKey int PRIMARY KEY,  
        Col1 nchar COLLATE Estonian_CS_AS  
       );  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a051c-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a051c-136">See Also</span></span>  
 <span data-ttu-id="a051c-137">[设置或更改服务器排序规则](set-or-change-the-server-collation.md) </span><span class="sxs-lookup"><span data-stu-id="a051c-137">[Set or Change the Server Collation](set-or-change-the-server-collation.md) </span></span>  
 <span data-ttu-id="a051c-138">[设置或更改数据库排序规则](set-or-change-the-database-collation.md) </span><span class="sxs-lookup"><span data-stu-id="a051c-138">[Set or Change the Database Collation](set-or-change-the-database-collation.md) </span></span>  
 [<span data-ttu-id="a051c-139">排序规则和 Unicode 支持</span><span class="sxs-lookup"><span data-stu-id="a051c-139">Collation and Unicode Support</span></span>](collation-and-unicode-support.md)  
  
  
