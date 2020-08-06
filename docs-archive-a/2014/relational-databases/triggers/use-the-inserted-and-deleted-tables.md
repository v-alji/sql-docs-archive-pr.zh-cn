---
title: 使用插入的和删除的表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- inserted tables
- UPDATE statement [SQL Server], DML triggers
- DELETE statement [SQL Server], DML triggers
- INSTEAD OF triggers
- deleted tables
- INSERT statement [SQL Server], DML triggers
- DML triggers, deleted or inserted tables
ms.assetid: ed84567f-7b91-4b44-b5b2-c400bda4590d
author: rothja
ms.author: jroth
ms.openlocfilehash: facc534177113bd93e56e50fca3ae14c3e6b2cfc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590611"
---
# <a name="use-the-inserted-and-deleted-tables"></a><span data-ttu-id="a550f-102">使用插入的和删除的表</span><span class="sxs-lookup"><span data-stu-id="a550f-102">Use the inserted and deleted Tables</span></span>
  <span data-ttu-id="a550f-103">DML 触发器语句使用两种特殊的表：删除的表和插入的表。</span><span class="sxs-lookup"><span data-stu-id="a550f-103">DML trigger statements use two special tables: the deleted table and the inserted tables.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a550f-104">会自动创建和管理这两种表。</span><span class="sxs-lookup"><span data-stu-id="a550f-104">automatically creates and manages these tables.</span></span> <span data-ttu-id="a550f-105">您可以使用这两种驻留内存的临时表来测试特定数据修改的影响以及设置 DML 触发器操作条件。</span><span class="sxs-lookup"><span data-stu-id="a550f-105">You can use these temporary, memory-resident tables to test the effects of certain data modifications and to set conditions for DML trigger actions.</span></span> <span data-ttu-id="a550f-106">但不能直接修改表中的数据或对表执行数据定义语言 (DDL) 操作，例如 CREATE INDEX。</span><span class="sxs-lookup"><span data-stu-id="a550f-106">You cannot directly modify the data in the tables or perform data definition language (DDL) operations on the tables, such as CREATE INDEX.</span></span>  
  
 <span data-ttu-id="a550f-107">在 DML 触发器中，inserted 和 deleted 表主要用于执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="a550f-107">In DML triggers, the inserted and deleted tables are primarily used to perform the following:</span></span>  
  
-   <span data-ttu-id="a550f-108">扩展表之间的引用完整性。</span><span class="sxs-lookup"><span data-stu-id="a550f-108">Extend referential integrity between tables.</span></span>  
  
-   <span data-ttu-id="a550f-109">在以视图为基础的基表中插入或更新数据。</span><span class="sxs-lookup"><span data-stu-id="a550f-109">Insert or update data in base tables underlying a view.</span></span>  
  
-   <span data-ttu-id="a550f-110">检查错误并采取相应的措施。</span><span class="sxs-lookup"><span data-stu-id="a550f-110">Test for errors and take action based on the error.</span></span>  
  
-   <span data-ttu-id="a550f-111">找出数据修改前后表的状态差异并基于该差异采取相应的措施。</span><span class="sxs-lookup"><span data-stu-id="a550f-111">Find the difference between the state of a table before and after a data modification and take actions based on that difference.</span></span>  
  
 <span data-ttu-id="a550f-112">删除的表用于存储 DELETE 和 UPDATE 语句所影响的行的副本。</span><span class="sxs-lookup"><span data-stu-id="a550f-112">The deleted table stores copies of the affected rows during DELETE and UPDATE statements.</span></span> <span data-ttu-id="a550f-113">在执行 DELETE 或 UPDATE 语句的过程中，行从触发器表中删除，并传输到删除的表中。</span><span class="sxs-lookup"><span data-stu-id="a550f-113">During the execution of a DELETE or UPDATE statement, rows are deleted from the trigger table and transferred to the deleted table.</span></span> <span data-ttu-id="a550f-114">删除的表和触发器表通常没有相同的行。</span><span class="sxs-lookup"><span data-stu-id="a550f-114">The deleted table and the trigger table ordinarily have no rows in common.</span></span>  
  
 <span data-ttu-id="a550f-115">插入的表用于存储 INSERT 和 UPDATE 语句所影响的行的副本。</span><span class="sxs-lookup"><span data-stu-id="a550f-115">The inserted table stores copies of the affected rows during INSERT and UPDATE statements.</span></span> <span data-ttu-id="a550f-116">在执行插入或更新事务过程中，新行会同时添加到 inserted 表和触发器表中。</span><span class="sxs-lookup"><span data-stu-id="a550f-116">During an insert or update transaction, new rows are added to both the inserted table and the trigger table.</span></span> <span data-ttu-id="a550f-117">插入的表中的行是触发器表中的新行的副本。</span><span class="sxs-lookup"><span data-stu-id="a550f-117">The rows in the inserted table are copies of the new rows in the trigger table.</span></span>  
  
 <span data-ttu-id="a550f-118">更新事务类似于在删除操作之后执行插入操作；首先，旧行被复制到删除的表中，然后，新行被复制到触发器表和插入的表中。</span><span class="sxs-lookup"><span data-stu-id="a550f-118">An update transaction is similar to a delete operation followed by an insert operation; the old rows are copied to the deleted table first, and then the new rows are copied to the trigger table and to the inserted table.</span></span>  
  
 <span data-ttu-id="a550f-119">在设置触发器条件时，应使用激发触发器的操作相应的插入的和删除的表。</span><span class="sxs-lookup"><span data-stu-id="a550f-119">When you set trigger conditions, use the inserted and deleted tables appropriately for the action that fired the trigger.</span></span> <span data-ttu-id="a550f-120">尽管在测试 INSERT 时引用删除的表或在测试 DELETE 时引用插入的表不会导致任何错误，但在这些情况下，这些触发器测试表将不包含任何行。</span><span class="sxs-lookup"><span data-stu-id="a550f-120">Although referencing the deleted table when testing an INSERT or the inserted table when testing a DELETE does not cause any errors, these trigger test tables do not contain any rows in these cases.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a550f-121">如果触发器操作取决于数据修改所影响的行数，则应对多行数据修改（基于 SELECT 语句的 INSERT、DELETE 或 UPDATE）使用测试（例如检查 @@ROWCOUNT），然后采取相应的措施。</span><span class="sxs-lookup"><span data-stu-id="a550f-121">If trigger actions depend on the number of rows a data modification effects, use tests (such as an examination of @@ROWCOUNT) for multirow data modifications (an INSERT, DELETE, or UPDATE based on a SELECT statement), and take appropriate actions.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="a550f-122">不允许在 AFTER 触发器的插入的和删除的表中引用 `text`、`ntext` 或 `image` 列。</span><span class="sxs-lookup"><span data-stu-id="a550f-122">does not allow for `text`, `ntext`, or `image` column references in the inserted and deleted tables for AFTER triggers.</span></span> <span data-ttu-id="a550f-123">但会包括这些数据类型，这只是为了向后兼容。</span><span class="sxs-lookup"><span data-stu-id="a550f-123">However, these data types are included for backward compatibility purposes only.</span></span> <span data-ttu-id="a550f-124">存储大型数据的首选方法是使用 `varchar(max)`、`nvarchar(max)` 和 `varbinary(max)` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="a550f-124">The preferred storage for large data is to use the `varchar(max)`, `nvarchar(max)`, and `varbinary(max)` data types.</span></span> <span data-ttu-id="a550f-125">AFTER 和 INSTEAD OF 触发器均支持插入的和删除的表中的 `varchar(max)`、`nvarchar(max)` 和 `varbinary(max)` 数据。</span><span class="sxs-lookup"><span data-stu-id="a550f-125">Both AFTER and INSTEAD OF triggers support `varchar(max)`, `nvarchar(max)`, and `varbinary(max)` data in the inserted and deleted tables.</span></span> <span data-ttu-id="a550f-126">有关详细信息，请参阅 [CREATE TRIGGER (Transact-SQL)](/sql/t-sql/statements/create-trigger-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a550f-126">For more information, see [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).</span></span>  
  
 <span data-ttu-id="a550f-127">**在触发器中使用插入的表以强制实施业务规则的示例**</span><span class="sxs-lookup"><span data-stu-id="a550f-127">**An Example of Using the inserted Table in a Trigger to Enforce Business Rules**</span></span>  
  
 <span data-ttu-id="a550f-128">由于 CHECK 约束只能引用定义了列级或表级约束的列，表间的任何约束（在本例中是业务规则）都必须定义为触发器。</span><span class="sxs-lookup"><span data-stu-id="a550f-128">Because CHECK constraints can reference only the columns on which the column-level or table-level constraint is defined, any cross-table constraints (in this case, business rules) must be defined as triggers.</span></span>  
  
 <span data-ttu-id="a550f-129">以下示例将创建一个 DML 触发器。</span><span class="sxs-lookup"><span data-stu-id="a550f-129">The following example creates a DML trigger.</span></span> <span data-ttu-id="a550f-130">如果有人试图将一个新采购订单插入到 `PurchaseOrderHeader` 表中，此触发器将进行检查以确保供应商具有良好的信用等级。</span><span class="sxs-lookup"><span data-stu-id="a550f-130">This trigger checks to make sure the credit rating for the vendor is good when an attempt is made to insert a new purchase order into the `PurchaseOrderHeader` table.</span></span> <span data-ttu-id="a550f-131">若要获取与刚插入的采购订单对应的供应商信用等级，必须引用 `Vendor` 表并将其与插入的表联接。</span><span class="sxs-lookup"><span data-stu-id="a550f-131">To obtain the credit rating of the vendor corresponding to the purchase order that was just inserted, the `Vendor` table must be referenced and joined with the inserted table.</span></span> <span data-ttu-id="a550f-132">如果信用等级太低，则显示信息，并且不执行该插入操作。</span><span class="sxs-lookup"><span data-stu-id="a550f-132">If the credit rating is too low, a message is displayed and the insertion does not execute.</span></span> <span data-ttu-id="a550f-133">请注意，此示例不允许进行多行数据修改。</span><span class="sxs-lookup"><span data-stu-id="a550f-133">Note that this example does not allow for multirow data modifications.</span></span> <span data-ttu-id="a550f-134">有关详细信息，请参阅 [创建 DML 触发器以处理多行数据](../triggers/create-dml-triggers-to-handle-multiple-rows-of-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a550f-134">For more information, see [Create DML Triggers to Handle Multiple Rows of Data](../triggers/create-dml-triggers-to-handle-multiple-rows-of-data.md).</span></span>  
  
 [!code-sql[TriggerDDL#CreateTrigger3](../../snippets/tsql/SQL14/tsql/triggerddl/transact-sql/snippet_create_alter_drop_trigger.sql#createtrigger3)]  
  
## <a name="using-the-inserted-and-deleted-tables-in-instead-of-triggers"></a><span data-ttu-id="a550f-135">在 INSTEAD OF 触发器中使用插入的和删除的表</span><span class="sxs-lookup"><span data-stu-id="a550f-135">Using the inserted and deleted Tables in INSTEAD OF Triggers</span></span>  
 <span data-ttu-id="a550f-136">传递给为表定义的 INSTEAD OF 触发器的插入的和删除的表与传递给 AFTER 触发器的插入的和删除的表遵守相同的规则。</span><span class="sxs-lookup"><span data-stu-id="a550f-136">The inserted and deleted tables passed to INSTEAD OF triggers defined on tables follow the same rules as the inserted and deleted tables passed to AFTER triggers.</span></span> <span data-ttu-id="a550f-137">插入的和删除的表的格式与在其上定义 INSTEAD OF 触发器的表的格式相同。</span><span class="sxs-lookup"><span data-stu-id="a550f-137">The format of the inserted and deleted tables is the same as the format of the table on which the INSTEAD OF trigger is defined.</span></span> <span data-ttu-id="a550f-138">插入的和删除的表中的每一列都直接映射到基表中的列。</span><span class="sxs-lookup"><span data-stu-id="a550f-138">Each column in the inserted and deleted tables maps directly to a column in the base table.</span></span>  
  
 <span data-ttu-id="a550f-139">以下是关于引用带 INSTEAD OF 触发器的表的 INSERT 或 UPDATE 语句何时必须提供列值的规则，当引用的表不带 INSTEAD OF 触发器时也一样：</span><span class="sxs-lookup"><span data-stu-id="a550f-139">The following rules regarding when an INSERT or UPDATE statement referencing a table with an INSTEAD OF trigger must supply values for columns are the same as if the table did not have an INSTEAD OF trigger:</span></span>  
  
-   <span data-ttu-id="a550f-140">不能为计算列或具有 `timestamp` 数据类型的列指定值。</span><span class="sxs-lookup"><span data-stu-id="a550f-140">Values cannot be specified for computed columns or columns with a `timestamp` data type.</span></span>  
  
-   <span data-ttu-id="a550f-141">不能为具有 IDENTITY 属性的列指定值，除非该表的 IDENTITY_INSERT 为 ON。</span><span class="sxs-lookup"><span data-stu-id="a550f-141">Values cannot be specified for columns with an IDENTITY property, unless IDENTITY_INSERT is ON for that table.</span></span> <span data-ttu-id="a550f-142">当 IDENTITY_INSERT 为 ON 时，INSERT 语句必须提供一个值。</span><span class="sxs-lookup"><span data-stu-id="a550f-142">When IDENTITY_INSERT is ON, INSERT statements must supply a value.</span></span>  
  
-   <span data-ttu-id="a550f-143">INSERT 语句必须为所有无 DEFAULT 约束的 NOT NULL 列提供值。</span><span class="sxs-lookup"><span data-stu-id="a550f-143">INSERT statements must supply values for all NOT NULL columns that do not have DEFAULT constraints.</span></span>  
  
-   <span data-ttu-id="a550f-144">对于除计算列、标识列或 `timestamp` 列以外的任何列，任何允许空值的列或具有 DEFAULT 定义的 NOT NULL 列的值都是可选的。</span><span class="sxs-lookup"><span data-stu-id="a550f-144">For any columns except computed, identity, or `timestamp` columns, values are optional for any column that allows nulls, or any NOT NULL column that has a DEFAULT definition.</span></span>  
  
 <span data-ttu-id="a550f-145">当 INSERT、UPDATE 或 DELETE 语句引用具有 INSTEAD OF 触发器的视图时， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 将调用该触发器，而不是对任何表采取任何直接操作。</span><span class="sxs-lookup"><span data-stu-id="a550f-145">When an INSERT, UPDATE, or DELETE statement references a view that has an INSTEAD OF trigger, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] calls the trigger instead of taking any direct action against any table.</span></span> <span data-ttu-id="a550f-146">即使插入的和删除的表中为该视图生成的信息格式不同于基表中的数据格式，触发器也必须使用插入的和删除的表中的信息来生成实现基表中请求的操作所需的任何语句。</span><span class="sxs-lookup"><span data-stu-id="a550f-146">The trigger must use the information presented in the inserted and deleted tables to build any statements required to implement the requested action in the base tables, even when the format of the information in the inserted and deleted tables built for the view is different from the format of the data in the base tables.</span></span>  
  
 <span data-ttu-id="a550f-147">传递给为视图定义的 INSTEAD OF 触发器的插入的和删除的表的格式与为该视图定义的 SELECT 语句的选择列表的格式一致。</span><span class="sxs-lookup"><span data-stu-id="a550f-147">The format of the inserted and deleted tables passed to an INSTEAD OF trigger defined on a view matches the select list of the SELECT statement defined for the view.</span></span> <span data-ttu-id="a550f-148">例如：</span><span class="sxs-lookup"><span data-stu-id="a550f-148">For example:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE VIEW dbo.EmployeeNames (BusinessEntityID, LName, FName)  
AS  
SELECT e.BusinessEntityID, p.LastName, p.FirstName  
FROM HumanResources.Employee AS e   
JOIN Person.Person AS p  
ON e.BusinessEntityID = p.BusinessEntityID;  
```  
  
 <span data-ttu-id="a550f-149">此视图的结果集有三列：一个 `int` 列和两个 `nvarchar` 列。</span><span class="sxs-lookup"><span data-stu-id="a550f-149">The result set for this view has three columns: an `int` column and two `nvarchar` columns.</span></span> <span data-ttu-id="a550f-150">传递给为视图定义的 INSTEAD OF 触发器的插入的和删除的表也有一个名为 `BusinessEntityID` 的 `int` 列、一个名为 `LName` 的 `nvarchar` 列和一个名为 `FName` 的 `nvarchar` 列。</span><span class="sxs-lookup"><span data-stu-id="a550f-150">The inserted and deleted tables passed to an INSTEAD OF trigger defined on the view also have an `int` column named `BusinessEntityID`, an `nvarchar` column named `LName`, and an `nvarchar` column named `FName`.</span></span>  
  
 <span data-ttu-id="a550f-151">视图的选择列表还可以包含不直接映射到单个基表列的表达式。</span><span class="sxs-lookup"><span data-stu-id="a550f-151">The select list of a view can also contain expressions that do not directly map to a single base-table column.</span></span> <span data-ttu-id="a550f-152">一些视图表达式（例如常量调用或函数调用）可能不引用任何列，并且这些表达式会被忽略。</span><span class="sxs-lookup"><span data-stu-id="a550f-152">Some view expressions, such as a constant or function invocation, may not reference any columns and can be ignored.</span></span> <span data-ttu-id="a550f-153">复杂的表达式会引用多个列，但在插入的和删除的表中，每个插入的行仅有一个相应的值。</span><span class="sxs-lookup"><span data-stu-id="a550f-153">Complex expressions can reference multiple columns, yet the inserted and deleted tables have only one value for each inserted row.</span></span> <span data-ttu-id="a550f-154">如果视图中的简单表达式引用包含复杂表达式的计算列，则这些简单表达式也有同样的问题。</span><span class="sxs-lookup"><span data-stu-id="a550f-154">The same issues apply to simple expressions in a view if they reference a computed column that has a complex expression.</span></span> <span data-ttu-id="a550f-155">视图上的 INSTEAD OF 触发器必须处理这些类型的表达式。</span><span class="sxs-lookup"><span data-stu-id="a550f-155">An INSTEAD OF trigger on the view must handle these types of expressions.</span></span>  
  
  
