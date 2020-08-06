---
title: 唯一约束和 CHECK 约束 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- constraints [SQL Server], Visual Database Tools
- Visual Database Tools [SQL Server], constraints
ms.assetid: 637098af-2567-48f8-90f4-b41df059833e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 205e4ae3d6f89f10a933bf357d1eeda458852584
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682772"
---
# <a name="unique-constraints-and-check-constraints"></a><span data-ttu-id="a6c0d-102">唯一约束和 CHECK 约束</span><span class="sxs-lookup"><span data-stu-id="a6c0d-102">Unique Constraints and Check Constraints</span></span>
  <span data-ttu-id="a6c0d-103">UNIQUE 约束和 CHECK 约束是可用于在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中强制数据完整性的两种类型的约束。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-103">UNIQUE constraints and CHECK constraints are two types of constraints that can be used to enforce data integrity in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables.</span></span> <span data-ttu-id="a6c0d-104">这些是重要的数据库对象。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-104">These are important database objects.</span></span>  
  
 <span data-ttu-id="a6c0d-105">本主题包含以下各节。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-105">This topic contains the following sections.</span></span>  
  
 [<span data-ttu-id="a6c0d-106">UNIQUE 约束</span><span class="sxs-lookup"><span data-stu-id="a6c0d-106">UNIQUE Constraints</span></span>](#Unique)  
  
 [<span data-ttu-id="a6c0d-107">CHECK 约束</span><span class="sxs-lookup"><span data-stu-id="a6c0d-107">CHECK Constraints</span></span>](#Check)  
  
 [<span data-ttu-id="a6c0d-108">相关任务</span><span class="sxs-lookup"><span data-stu-id="a6c0d-108">Related Tasks</span></span>](#Tasks)  
  
##  <a name="unique-constraints"></a><a name="Unique"></a> <span data-ttu-id="a6c0d-109">UNIQUE 约束</span><span class="sxs-lookup"><span data-stu-id="a6c0d-109">UNIQUE Constraints</span></span>  
 <span data-ttu-id="a6c0d-110">约束是 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 为您强制执行的规则。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-110">Constraints are rules that the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] enforces for you.</span></span> <span data-ttu-id="a6c0d-111">例如，您可以使用 UNIQUE 约束确保在非主键列中不输入重复的值。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-111">For example, you can use UNIQUE constraints to make sure that no duplicate values are entered in specific columns that do not participate in a primary key.</span></span> <span data-ttu-id="a6c0d-112">尽管 UNIQUE 约束和 PRIMARY KEY 约束都强制唯一性，但想要强制一列或多列组合（不是主键）的唯一性时应使用 UNIQUE 约束而不是 PRIMARY KEY 约束。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-112">Although both a UNIQUE constraint and a PRIMARY KEY constraint enforce uniqueness, use a UNIQUE constraint instead of a PRIMARY KEY constraint when you want to enforce the uniqueness of a column, or combination of columns, that is not the primary key.</span></span>  
  
 <span data-ttu-id="a6c0d-113">UNIQUE 约束允许 NULL 值，这一点与 PRIMARY KEY 约束不同。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-113">Unlike PRIMARY KEY constraints, UNIQUE constraints allow for the value NULL.</span></span> <span data-ttu-id="a6c0d-114">不过，当与参与 UNIQUE 约束的任何值一起使用时，每列只允许一个空值。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-114">However, as with any value participating in a UNIQUE constraint, only one null value is allowed per column.</span></span> <span data-ttu-id="a6c0d-115">FOREIGN KEY 约束可以引用 UNIQUE 约束。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-115">A UNIQUE constraint can be referenced by a FOREIGN KEY constraint.</span></span>  
  
 <span data-ttu-id="a6c0d-116">默认情况下，向表中的现有列添加 UNIQUE 约束后， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 将检查列中的现有数据，以确保所有值都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-116">When a UNIQUE constraint is added to an existing column or columns in the table, by default, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] examines the existing data in the columns to make sure all values are unique.</span></span> <span data-ttu-id="a6c0d-117">如果向含有重复值的列添加 UNIQUE 约束， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 将返回错误消息，并且不添加约束。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-117">If a UNIQUE constraint is added to a column that has duplicated values, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] returns an error and does not add the constraint.</span></span>  
  
 <span data-ttu-id="a6c0d-118">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 将自动创建 UNIQUE 索引来强制执行 UNIQUE 约束的唯一性要求。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-118">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] automatically creates a UNIQUE index to enforce the uniqueness requirement of the UNIQUE constraint.</span></span> <span data-ttu-id="a6c0d-119">因此，如果试图插入重复行， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 将返回错误消息，说明该操作违反了 UNIQUE 约束，不能将该行添加到表中。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-119">Therefore, if an attempt to insert a duplicate row is made, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] returns an error message that states the UNIQUE constraint has been violated and does not add the row to the table.</span></span> <span data-ttu-id="a6c0d-120">除非显式指定了聚集索引，否则，默认情况下将创建唯一的非聚集索引以强制执行 UNIQUE 约束。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-120">Unless a clustered index is explicitly specified, a unique, nonclustered index is created by default to enforce the UNIQUE constraint.</span></span>  
  
##  <a name="check-constraints"></a><a name="Check"></a> <span data-ttu-id="a6c0d-121">CHECK 约束</span><span class="sxs-lookup"><span data-stu-id="a6c0d-121">CHECK Constraints</span></span>  
 <span data-ttu-id="a6c0d-122">通过限制一个或多个列可接受的值，CHECK 约束可以强制域完整性。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-122">CHECK constraints enforce domain integrity by limiting the values that are accepted by one or more columns.</span></span> <span data-ttu-id="a6c0d-123">可以通过任何基于逻辑运算符返回 TRUE 或 FALSE 的逻辑（布尔）表达式创建 CHECK 约束。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-123">You can create a CHECK constraint with any logical (Boolean) expression that returns TRUE or FALSE based on the logical operators.</span></span> <span data-ttu-id="a6c0d-124">例如，可以通过创建 CHECK 约束将 **salary** 列中值的范围限制为从 $15,000 到 $100,000 之间的数据。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-124">For example, the range of values for a **salary** column can be limited by creating a CHECK constraint that allows for only data that ranges from $15,000 through $100,000.</span></span> <span data-ttu-id="a6c0d-125">这可防止薪金超出常规薪金范围之外。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-125">This prevents salaries from being entered beyond the regular salary range.</span></span> <span data-ttu-id="a6c0d-126">逻辑表达式将如下： `salary >= 15000 AND salary <= 100000`。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-126">The logical expression would be the following: `salary >= 15000 AND salary <= 100000`.</span></span>  
  
 <span data-ttu-id="a6c0d-127">可以将多个 CHECK 约束应用于单个列。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-127">You can apply multiple CHECK constraints to a single column.</span></span> <span data-ttu-id="a6c0d-128">还可以通过在表级创建 CHECK 约束，将一个 CHECK 约束应用于多个列。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-128">You can also apply a single CHECK constraint to multiple columns by creating it at the table level.</span></span> <span data-ttu-id="a6c0d-129">例如，多列 CHECK 约束可用于确认 **country_region** 列值为 **USA** 的任意行是否在 **state** 列中还有一个由两个字符构成的值。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-129">For example, a multiple-column CHECK constraint could be used to confirm that any row with a **country_region** column value of **USA** also has a two-character value in the **state** column.</span></span> <span data-ttu-id="a6c0d-130">这使得在一个位置可以同时检查多个条件。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-130">This allows for multiple conditions to be checked in one location.</span></span>  
  
 <span data-ttu-id="a6c0d-131">CHECK 约束类似于 FOREIGN KEY 约束，因为可以控制放入列中的值。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-131">CHECK constraints are similar to FOREIGN KEY constraints in that they control the values that are put in a column.</span></span> <span data-ttu-id="a6c0d-132">但是，它们在确定有效值的方式上有所不同：FOREIGN KEY 约束从其他表获得有效值列表，而 CHECK 约束通过逻辑表达式确定有效值。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-132">The difference is in how they determine which values are valid: FOREIGN KEY constraints obtain the list of valid values from another table, while CHECK constraints determine the valid values from a logical expression.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="a6c0d-133">包括隐式或显式数据类型转换的约束可能会导致某些操作失败。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-133">Constraints that include implicit or explicit data type conversion may cause certain operations to fail.</span></span> <span data-ttu-id="a6c0d-134">例如，为表定义的作为分区切换的源的此类约束可能会导致 ALTER TABLE...SWITCH 操作失败。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-134">For example, such constraints defined on tables that are sources of partition switching may cause an ALTER TABLE...SWITCH operation to fail.</span></span> <span data-ttu-id="a6c0d-135">在约束定义中避免数据类型转换。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-135">Avoid data type conversion in constraint definitions.</span></span>  
  
### <a name="limitations-of-check-constraints"></a><span data-ttu-id="a6c0d-136">CHECK 约束的限制</span><span class="sxs-lookup"><span data-stu-id="a6c0d-136">Limitations of CHECK Constraints</span></span>  
 <span data-ttu-id="a6c0d-137">CHECK 约束不接受计算结果为 FALSE 的值。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-137">CHECK constraints reject values that evaluate to FALSE.</span></span> <span data-ttu-id="a6c0d-138">因为空值的计算结果为 UNKNOWN，所以表达式中存在这些值可能会覆盖约束。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-138">Because null values evaluate to UNKNOWN, their presence in expressions may override a constraint.</span></span> <span data-ttu-id="a6c0d-139">例如，假设您对列设置了约束， `int` **MyColumn**指定**MyColumn**只能包含值 10 (**MyColumn = 10**) 。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-139">For example, suppose you place a constraint on an `int` column **MyColumn** specifying that **MyColumn** can contain only the value 10 (**MyColumn=10**).</span></span> <span data-ttu-id="a6c0d-140">如果将值 NULL 插入到 **MyColumn**， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 将插入 NULL 且不返回错误。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-140">If you insert the value NULL into **MyColumn**, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] inserts NULL and does not return an error.</span></span>  
  
 <span data-ttu-id="a6c0d-141">如果 CHECK 约束检查的条件对于表中的任何行都不是 FALSE，它将返回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-141">A CHECK constraint returns TRUE when the condition it is checking is not FALSE for any row in the table.</span></span> <span data-ttu-id="a6c0d-142">CHECK 约束在行级执行。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-142">A CHECK constraint works at the row level.</span></span> <span data-ttu-id="a6c0d-143">如果刚创建的表没有任何行，则此表的任何 CHECK 约束都视为有效。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-143">If a table that has just been created does not have any rows, any CHECK constraint on this table is considered valid.</span></span> <span data-ttu-id="a6c0d-144">这种情况可能会产生意外结果，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-144">This situation can produce unexpected results, as in the following example.</span></span>  
  
```  
CREATE TABLE CheckTbl (col1 int, col2 int);  
GO  
CREATE FUNCTION CheckFnctn()  
RETURNS int  
AS   
BEGIN  
   DECLARE @retval int  
   SELECT @retval = COUNT(*) FROM CheckTbl  
   RETURN @retval  
END;  
GO  
ALTER TABLE CheckTbl  
ADD CONSTRAINT chkRowCount CHECK (dbo.CheckFnctn() >= 1 );  
GO  
```  
  
 <span data-ttu-id="a6c0d-145">添加的 `CHECK` 约束指定表 `CheckTbl`必须至少包含一行。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-145">The `CHECK` constraint being added specifies that there must be at least one row in table `CheckTbl`.</span></span> <span data-ttu-id="a6c0d-146">但是，因为表中不包含任何可供检查此约束的条件的行，所以 ALTER TABLE 语句将成功。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-146">However, because there are no rows in the table against which to check the condition of this constraint, the ALTER TABLE statement succeeds.</span></span>  
  
 <span data-ttu-id="a6c0d-147">执行 DELETE 语句时不验证 CHECK 约束。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-147">CHECK constraints are not validated during DELETE statements.</span></span> <span data-ttu-id="a6c0d-148">因此，使用特定类型的 CHECK 约束对表执行 DELETE 语句时可能会产生意外结果。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-148">Therefore, executing DELETE statements on tables with certain types of check constraints may produce unexpected results.</span></span> <span data-ttu-id="a6c0d-149">例如，假设对表 `CheckTbl`执行下列语句。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-149">For example, consider the following statements executed on table `CheckTbl`.</span></span>  
  
```  
INSERT INTO CheckTbl VALUES (10, 10);  
GO  
DELETE CheckTbl WHERE col1 = 10;  
```  
  
 <span data-ttu-id="a6c0d-150">即使 `DELETE` 约束指定表 `CHECK` 必须至少包含 `CheckTbl` 行， `1` 语句也会成功。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-150">The `DELETE` statement succeeds, even though the `CHECK` constraint specifies that table `CheckTbl` must have at least `1` row.</span></span>  
  
##  <a name="related-tasks"></a><a name="Tasks"></a> <span data-ttu-id="a6c0d-151">相关任务</span><span class="sxs-lookup"><span data-stu-id="a6c0d-151">Related Tasks</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a6c0d-152">如果表是为复制发布的，则必须使用 Transact-SQL 语句 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 或 SQL Server 管理对象 (SMO) 对架构进行更改。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-152">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="a6c0d-153">使用表设计器或数据库关系图设计器更改架构后，会尝试删除并重新创建表。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-153">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="a6c0d-154">由于您不能删除已发布的对象，因此架构更改将失败。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-154">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
|<span data-ttu-id="a6c0d-155">任务</span><span class="sxs-lookup"><span data-stu-id="a6c0d-155">Task</span></span>|<span data-ttu-id="a6c0d-156">主题</span><span class="sxs-lookup"><span data-stu-id="a6c0d-156">Topic</span></span>|  
|----------|-----------|  
|<span data-ttu-id="a6c0d-157">介绍如何创建唯一约束。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-157">Describes how to create a unique constraint.</span></span>|[<span data-ttu-id="a6c0d-158">创建唯一约束</span><span class="sxs-lookup"><span data-stu-id="a6c0d-158">Create Unique Constraints</span></span>](../tables/create-unique-constraints.md)|  
|<span data-ttu-id="a6c0d-159">介绍如何修改唯一约束。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-159">Describes how to modify a unique constraint.</span></span>|[<span data-ttu-id="a6c0d-160">修改唯一约束</span><span class="sxs-lookup"><span data-stu-id="a6c0d-160">Modify Unique Constraints</span></span>](../tables/modify-unique-constraints.md)|  
|<span data-ttu-id="a6c0d-161">介绍如何删除唯一约束。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-161">Describes how to delete a unique constraint.</span></span>|[<span data-ttu-id="a6c0d-162">删除唯一约束</span><span class="sxs-lookup"><span data-stu-id="a6c0d-162">Delete Unique Constraints</span></span>](../tables/delete-unique-constraints.md)|  
|<span data-ttu-id="a6c0d-163">介绍当复制代理在表中插入或更新数据时如何禁用 CHECK 约束。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-163">Describes how to disable a check constraint when a replication agent inserts or updates data in your table.</span></span>|[<span data-ttu-id="a6c0d-164">对复制禁用 CHECK 约束</span><span class="sxs-lookup"><span data-stu-id="a6c0d-164">Disable Check Constraints for Replication</span></span>](../tables/disable-check-constraints-for-replication.md)|  
|<span data-ttu-id="a6c0d-165">介绍在表中添加、更新或删除数据时如何禁用 CHECK 约束。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-165">Describes how to disable a check constraint when data is added to, updated in, or deleted from a table.</span></span>|[<span data-ttu-id="a6c0d-166">对 INSERT 和 UPDATE 语句禁用 CHECK 约束</span><span class="sxs-lookup"><span data-stu-id="a6c0d-166">Disable Check Constraints with INSERT and UPDATE Statements</span></span>](../tables/disable-check-constraints-with-insert-and-update-statements.md)|  
|<span data-ttu-id="a6c0d-167">介绍如何更改约束表达式或更改对特定条件启用或禁用约束的选项。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-167">Describes how to change the constraint expression or the options that enable or disable the constraint for specific conditions.</span></span>|[<span data-ttu-id="a6c0d-168">修改 CHECK 约束</span><span class="sxs-lookup"><span data-stu-id="a6c0d-168">Modify Check Constraints</span></span>](../tables/modify-check-constraints.md)|  
|<span data-ttu-id="a6c0d-169">介绍如何删除 CHECK 约束。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-169">Describes how to delete a check constraint.</span></span>|[<span data-ttu-id="a6c0d-170">删除 CHECK 约束</span><span class="sxs-lookup"><span data-stu-id="a6c0d-170">Delete Check Constraints</span></span>](../tables/delete-check-constraints.md)|  
|<span data-ttu-id="a6c0d-171">介绍如何查看 CHECK 约束的属性。</span><span class="sxs-lookup"><span data-stu-id="a6c0d-171">Describes how to view the properties of a check constraint.</span></span>|[<span data-ttu-id="a6c0d-172">唯一约束和 CHECK 约束</span><span class="sxs-lookup"><span data-stu-id="a6c0d-172">Unique Constraints and Check Constraints</span></span>](../tables/unique-constraints-and-check-constraints.md)|  
  
  
