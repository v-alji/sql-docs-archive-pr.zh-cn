---
title: Transact-SQL 对内存中 OLTP 的支持 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: b1cc7c30-1747-4c21-88ac-e95a5e58baac
author: rothja
ms.author: jroth
ms.openlocfilehash: bf3708a258e3bb97231e45b10bea2c59351a06a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693326"
---
# <a name="transact-sql-support-for-in-memory-oltp"></a><span data-ttu-id="5602d-102">对内存中 OLTP 的 Transact-SQL 支持</span><span class="sxs-lookup"><span data-stu-id="5602d-102">Transact-SQL Support for In-Memory OLTP</span></span>
  <span data-ttu-id="5602d-103">可以使用任何 Transact-SQL 查询或 DML 语句（SELECT、INSERT、UPDATE 或 DELETE）、即席语句和 SQL 模块（如存储过程、表值函数、标量函数、触发器和视图）来访问内存优化表。</span><span class="sxs-lookup"><span data-stu-id="5602d-103">You can access memory-optimized tables using any Transact-SQL query or DML statement (SELECT, INSERT, UPDATE, or DELETE), ad hoc statement, and SQL module such as stored procedures, table-value functions, scalar functions, triggers, and views.</span></span> <span data-ttu-id="5602d-104">有关详细信息，请参阅[使用解释型 Transact-sql 访问内存优化表](accessing-memory-optimized-tables-using-interpreted-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="5602d-104">For more information see [Accessing Memory-Optimized Tables Using Interpreted Transact-SQL](accessing-memory-optimized-tables-using-interpreted-transact-sql.md).</span></span>  
  
 <span data-ttu-id="5602d-105">仅引用内存优化表的存储过程可本机编译为机器代码，所提高的性能通常比解释型（基于磁盘的）存储过程更显著。</span><span class="sxs-lookup"><span data-stu-id="5602d-105">Stored procedures that only reference memory-optimized tables can be natively compiled into machine code and typically provide significant performance gains over interpreted (disk-based) stored procedures.</span></span> <span data-ttu-id="5602d-106">对于内存优化表的优化访问，使用本机编译存储过程。</span><span class="sxs-lookup"><span data-stu-id="5602d-106">For optimized access to memory-optimized tables use natively compiled stored procedures.</span></span> <span data-ttu-id="5602d-107">有关详细信息，请参阅[本机编译的存储过程](natively-compiled-stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="5602d-107">For more information, see [Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md).</span></span>  
  
 <span data-ttu-id="5602d-108">创建和修改数据对象（DDL 语句）时，修改了以下语句：</span><span class="sxs-lookup"><span data-stu-id="5602d-108">When creating and modifying database objects (DDL statements), the following statements have been modified:</span></span>  
  
-   <span data-ttu-id="5602d-109">[ALTER DATABASE 文件和文件组选项 &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) (参阅 `MEMORY_OPTIMIZED_DATA`) </span><span class="sxs-lookup"><span data-stu-id="5602d-109">[ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) (see `MEMORY_OPTIMIZED_DATA`)</span></span>  
  
-   <span data-ttu-id="5602d-110">[SQL Server transact-sql&#41;创建数据库 &#40;](/sql/t-sql/statements/create-database-sql-server-transact-sql) (参阅 `MEMORY_OPTIMIZED_DATA`) </span><span class="sxs-lookup"><span data-stu-id="5602d-110">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) (see `MEMORY_OPTIMIZED_DATA`)</span></span>  
  
-   <span data-ttu-id="5602d-111">[CREATE PROCEDURE &#40;transact-sql&#41;](/sql/t-sql/statements/create-procedure-transact-sql) (参阅、、 `NATIVE_COMPILATION` `SCHEMABINDING` `EXECUTE AS` 和 `BEGIN ATOMIC`) </span><span class="sxs-lookup"><span data-stu-id="5602d-111">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) (see `NATIVE_COMPILATION`, `SCHEMABINDING`, `EXECUTE AS`, and `BEGIN ATOMIC`)</span></span>  
  
-   <span data-ttu-id="5602d-112">[CREATE TABLE &#40;transact-sql&#41;](/sql/t-sql/statements/create-table-transact-sql) (参阅、、 `MEMORY_OPTIMIZED` `DURABILITY` `BUCKET_COUNT` 、 `INDEX` 和 `HASH`) </span><span class="sxs-lookup"><span data-stu-id="5602d-112">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) (see `MEMORY_OPTIMIZED`, `DURABILITY`, `BUCKET_COUNT`, `INDEX`, and `HASH`)</span></span>  
  
-   <span data-ttu-id="5602d-113">[CREATE TYPE &#40;transact-sql&#41;](/sql/t-sql/statements/create-type-transact-sql) (参阅、、 `MEMORY_OPTIMIZED` `BUCKET_COUNT` `INDEX` 和 `HASH`) </span><span class="sxs-lookup"><span data-stu-id="5602d-113">[CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql) (see `MEMORY_OPTIMIZED`, `BUCKET_COUNT`, `INDEX`, and `HASH`)</span></span>  
  
-   <span data-ttu-id="5602d-114">[声明 @local_variable &#40;transact-sql&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) (参阅 `NULL`  |  `NOT NULL`) </span><span class="sxs-lookup"><span data-stu-id="5602d-114">[DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) (see `NULL` | `NOT NULL`)</span></span>  
  
 <span data-ttu-id="5602d-115">内存优化表支持 `PRIMARY KEY` 和 `NOT NULL` 约束。</span><span class="sxs-lookup"><span data-stu-id="5602d-115">Memory-optimized tables support `PRIMARY KEY` and `NOT NULL` constraints.</span></span> <span data-ttu-id="5602d-116">有关实现不受支持的约束的信息，请参阅[迁移 Check 和 Foreign Key 约束](../../database-engine/migrating-check-and-foreign-key-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="5602d-116">For information on implementing unsupported constraints, see [Migrating Check and Foreign Key Constraints](../../database-engine/migrating-check-and-foreign-key-constraints.md).</span></span>  
  
 <span data-ttu-id="5602d-117">有关不支持的功能的信息，请参阅[内存中 OLTP 不支持的 Transact-SQL 构造](transact-sql-constructs-not-supported-by-in-memory-oltp.md)。</span><span class="sxs-lookup"><span data-stu-id="5602d-117">For information on unsupported features, see [Transact-SQL Constructs Not Supported by In-Memory OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5602d-118">本节内容</span><span class="sxs-lookup"><span data-stu-id="5602d-118">In This Section</span></span>  
  
-   [<span data-ttu-id="5602d-119">支持的数据类型</span><span class="sxs-lookup"><span data-stu-id="5602d-119">Supported Data Types</span></span>](supported-data-types-for-in-memory-oltp.md)  
  
-   [<span data-ttu-id="5602d-120">使用解释型 Transact-SQL 访问内存优化表</span><span class="sxs-lookup"><span data-stu-id="5602d-120">Accessing Memory-Optimized Tables Using Interpreted Transact-SQL</span></span>](accessing-memory-optimized-tables-using-interpreted-transact-sql.md)  
  
-   [<span data-ttu-id="5602d-121">系统视图、存储过程、内存中 OLTP 的 DMV 和等待类型</span><span class="sxs-lookup"><span data-stu-id="5602d-121">System Views, Stored Procedures, DMVs and Wait Types for In-Memory OLTP</span></span>](../../database-engine/system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp.md)  
  
## <a name="see-also"></a><span data-ttu-id="5602d-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5602d-122">See Also</span></span>  
 <span data-ttu-id="5602d-123">[内存中 OLTP（内存中优化）](in-memory-oltp-in-memory-optimization.md) </span><span class="sxs-lookup"><span data-stu-id="5602d-123">[In-Memory OLTP &#40;In-Memory Optimization&#41;](in-memory-oltp-in-memory-optimization.md) </span></span>  
 <span data-ttu-id="5602d-124">[本机编译的存储过程的迁移问题](migration-issues-for-natively-compiled-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="5602d-124">[Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md) </span></span>  
 <span data-ttu-id="5602d-125">[支持的 SQL Server 功能](unsupported-sql-server-features-for-in-memory-oltp.md) </span><span class="sxs-lookup"><span data-stu-id="5602d-125">[Supported SQL Server Features](unsupported-sql-server-features-for-in-memory-oltp.md) </span></span>  
 [<span data-ttu-id="5602d-126">本机编译的存储过程</span><span class="sxs-lookup"><span data-stu-id="5602d-126">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
