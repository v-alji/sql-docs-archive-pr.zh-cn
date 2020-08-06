---
title: 创建 DML 触发器以处理多行数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- multiple row DML triggers
- UPDATE statement [SQL Server], DML triggers
- DELETE statement [SQL Server], DML triggers
- multirow DML triggers [SQL Server]
- INSERT statement [SQL Server], DML triggers
- DML triggers, multirow
ms.assetid: d476c124-596b-4b27-a883-812b6b50a735
author: rothja
ms.author: jroth
ms.openlocfilehash: 11ea7aa457a5cdfcafd4a8c4e0ac170ae0e3b9c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590640"
---
# <a name="create-dml-triggers-to-handle-multiple-rows-of-data"></a><span data-ttu-id="4e5fb-102">创建 DML 触发器以处理多行数据</span><span class="sxs-lookup"><span data-stu-id="4e5fb-102">Create DML Triggers to Handle Multiple Rows of Data</span></span>
  <span data-ttu-id="4e5fb-103">为 DML 触发器编写代码时，请考虑导致触发器激发的语句可能是影响多行数据（而不是单行）的单个语句。</span><span class="sxs-lookup"><span data-stu-id="4e5fb-103">When you write the code for a DML trigger, consider that the statement that causes the trigger to fire can be a single statement that affects multiple rows of data, instead of a single row.</span></span> <span data-ttu-id="4e5fb-104">这对于 UPDATE 和 DELETE 触发器很常见，因为这些语句经常影响多行。</span><span class="sxs-lookup"><span data-stu-id="4e5fb-104">This behavior is common for UPDATE and DELETE triggers because these statements frequently affect multiple rows.</span></span> <span data-ttu-id="4e5fb-105">而这对于 INSERT 触发器比较少见，因为基本 INSERT 语句仅添加单行。</span><span class="sxs-lookup"><span data-stu-id="4e5fb-105">The behavior is less common for INSERT triggers because the basic INSERT statement adds only a single row.</span></span> <span data-ttu-id="4e5fb-106">但是，由于 INSERT 触发器可以通过 INSERT INTO (*table_name*) SELECT 语句触发，因此插入多行可能导致调用单个触发器。</span><span class="sxs-lookup"><span data-stu-id="4e5fb-106">However, because an INSERT trigger can be fired by an INSERT INTO (*table_name*) SELECT statement, the insertion of many rows may cause a single trigger invocation.</span></span>  
  
 <span data-ttu-id="4e5fb-107">在下列情况下关于多行的注意事项尤为重要：DML 触发器的功能自动重新计算一个表中的汇总值，并将结果存储在另一个表中以继续进行计数。</span><span class="sxs-lookup"><span data-stu-id="4e5fb-107">Multirow considerations are especially important when the function of a DML trigger is to automatically recalculate summary values from one table and store the results in another for ongoing tallies.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4e5fb-108">我们建议不要在触发器中使用游标，因为它们可能会降低性能。</span><span class="sxs-lookup"><span data-stu-id="4e5fb-108">We do not recommend using cursors in triggers because they could potentially reduce performance.</span></span> <span data-ttu-id="4e5fb-109">若要设计一个影响多行的触发器，请使用基于行集的逻辑，而不要使用游标。</span><span class="sxs-lookup"><span data-stu-id="4e5fb-109">To design a trigger that affects multiple rows, use rowset-based logic instead of cursors.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4e5fb-110">示例</span><span class="sxs-lookup"><span data-stu-id="4e5fb-110">Examples</span></span>  
 <span data-ttu-id="4e5fb-111">下列示例中的 DML 触发器用于在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 示例数据库的另一个表中存储某列的运行总计。</span><span class="sxs-lookup"><span data-stu-id="4e5fb-111">The DML triggers in the following examples are designed to store a running total of a column in another table of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
### <a name="a-storing-a-running-total-for-a-single-row-insert"></a><span data-ttu-id="4e5fb-112">A.</span><span class="sxs-lookup"><span data-stu-id="4e5fb-112">A.</span></span> <span data-ttu-id="4e5fb-113">存储单行插入的运行总计</span><span class="sxs-lookup"><span data-stu-id="4e5fb-113">Storing a running total for a single-row insert</span></span>  
 <span data-ttu-id="4e5fb-114">第一种 DML 触发器在一行数据加载到 `PurchaseOrderDetail` 表中时适合于单行插入。</span><span class="sxs-lookup"><span data-stu-id="4e5fb-114">The first version of the DML trigger works well for a single-row insert when a row of data is loaded into the `PurchaseOrderDetail` table.</span></span> <span data-ttu-id="4e5fb-115">INSERT 语句激发 DML 触发器，新行在触发器执行期间加载到 **插入的** 表中。</span><span class="sxs-lookup"><span data-stu-id="4e5fb-115">An INSERT statement fires the DML trigger, and the new row is loaded into the **inserted** table for the duration of the trigger execution.</span></span> <span data-ttu-id="4e5fb-116">`UPDATE` 语句读取该行的 `LineTotal` 列值，并将该值与 `SubTotal` 表的 `PurchaseOrderHeader` 列中的现有值相加。</span><span class="sxs-lookup"><span data-stu-id="4e5fb-116">The `UPDATE` statement reads the `LineTotal` column value for the row and adds that value to the existing value in the `SubTotal` column in the `PurchaseOrderHeader` table.</span></span> <span data-ttu-id="4e5fb-117">`WHERE` 子句确保 `PurchaseOrderDetail` 表中的更新行与 `PurchaseOrderID` 插入的 **表中** 行相匹配。</span><span class="sxs-lookup"><span data-stu-id="4e5fb-117">The `WHERE` clause makes sure that the updated row in the `PurchaseOrderDetail` table matches the `PurchaseOrderID` of the row in the **inserted** table.</span></span>  
  
```  
-- Trigger is valid for single-row inserts.  
USE AdventureWorks2012;  
GO  
CREATE TRIGGER NewPODetail  
ON Purchasing.PurchaseOrderDetail  
AFTER INSERT AS  
   UPDATE PurchaseOrderHeader  
   SET SubTotal = SubTotal + LineTotal  
   FROM inserted  
   WHERE PurchaseOrderHeader.PurchaseOrderID = inserted.PurchaseOrderID ;  
```  
  
### <a name="b-storing-a-running-total-for-a-multirow-or-single-row-insert"></a><span data-ttu-id="4e5fb-118">B.</span><span class="sxs-lookup"><span data-stu-id="4e5fb-118">B.</span></span> <span data-ttu-id="4e5fb-119">存储多行或单行插入的运行总计</span><span class="sxs-lookup"><span data-stu-id="4e5fb-119">Storing a running total for a multirow or single-row insert</span></span>  
 <span data-ttu-id="4e5fb-120">对于多行插入，示例 A 中的 DML 触发器可能不会正确运行；位于 UPDATE 语句 (`SubTotal` + `LineTotal`) 中赋值表达式右侧的表达式只能是单个值，而非值列表。</span><span class="sxs-lookup"><span data-stu-id="4e5fb-120">For a multirow insert, the DML trigger in example A might not operate correctly; the expression to the right of an assignment expression in an UPDATE statement (`SubTotal` + `LineTotal`) can be only a single value, not a list of values.</span></span> <span data-ttu-id="4e5fb-121">因此，该触发器的作用是检索 **插入的** 表中任意一行的值，并将该值与 `SubTotal` 表中的现有 `PurchaseOrderHeader` 值相加，以获得特定 `PurchaseOrderID` 值。</span><span class="sxs-lookup"><span data-stu-id="4e5fb-121">Therefore, the effect of the trigger is to retrieve a value from any single row in the **inserted** table and add that value to the existing `SubTotal` value in the `PurchaseOrderHeader` table for a specific `PurchaseOrderID` value.</span></span> <span data-ttu-id="4e5fb-122">如果某个 `PurchaseOrderID` 值在 **插入的** 表中出现多次，则此操作可能无法达到预期效果。</span><span class="sxs-lookup"><span data-stu-id="4e5fb-122">This operation might not have the expected effect if a single `PurchaseOrderID` value occurred more than one time in the **inserted** table.</span></span>  
  
 <span data-ttu-id="4e5fb-123">若要正确更新 `PurchaseOrderHeader` 表，必须允许对 **插入的** 表中的多行使用触发器。</span><span class="sxs-lookup"><span data-stu-id="4e5fb-123">To correctly update the `PurchaseOrderHeader` table, the trigger must allow for the chance of multiple rows in the **inserted** table.</span></span> <span data-ttu-id="4e5fb-124">可以通过使用 `SUM` 函数达到此目的，该函数计算每个 `LineTotal` 的 **插入的** 表中许多行的总 `PurchaseOrderID`。</span><span class="sxs-lookup"><span data-stu-id="4e5fb-124">You can do this by using the `SUM` function that calculates the total `LineTotal` for a group of rows in the **inserted** table for each `PurchaseOrderID`.</span></span> <span data-ttu-id="4e5fb-125">`SUM` 函数包含在相关子查询（括号中的 `SELECT` 语句）中。</span><span class="sxs-lookup"><span data-stu-id="4e5fb-125">The `SUM` function is included in a correlated subquery (the `SELECT` statement in parentheses).</span></span> <span data-ttu-id="4e5fb-126">此子查询将为 `PurchaseOrderID` 插入的 **表中的每个** 返回一个值，该值与 `PurchaseOrderID` 表中的 `PurchaseOrderHeader` 匹配或相关。</span><span class="sxs-lookup"><span data-stu-id="4e5fb-126">This subquery returns a single value for each `PurchaseOrderID` in the **inserted** table that matches or is correlated with a `PurchaseOrderID` in the `PurchaseOrderHeader` table.</span></span>  
  
```  
-- Trigger is valid for multirow and single-row inserts.  
USE AdventureWorks2012;  
GO  
CREATE TRIGGER NewPODetail2  
ON Purchasing.PurchaseOrderDetail  
AFTER INSERT AS  
   UPDATE Purchasing.PurchaseOrderHeader  
   SET SubTotal = SubTotal +   
      (SELECT SUM(LineTotal)  
      FROM inserted  
      WHERE PurchaseOrderHeader.PurchaseOrderID  
       = inserted.PurchaseOrderID)  
   WHERE PurchaseOrderHeader.PurchaseOrderID IN  
      (SELECT PurchaseOrderID FROM inserted);  
```  
  
 <span data-ttu-id="4e5fb-127">此触发器还适合于单行插入； `LineTotal` 值列的和为单行的和。</span><span class="sxs-lookup"><span data-stu-id="4e5fb-127">This trigger also works correctly in a single-row insert; the sum of the `LineTotal` value column is the sum of a single row.</span></span> <span data-ttu-id="4e5fb-128">但是，对于此触发器，相关子查询和 `IN` 子句中使用的 `WHERE` 运算符需要从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中进行其他处理。</span><span class="sxs-lookup"><span data-stu-id="4e5fb-128">However, with this trigger the correlated subquery and the `IN` operator that is used in the `WHERE` clause require additional processing from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4e5fb-129">这对于单行插入来说，是不必要的。</span><span class="sxs-lookup"><span data-stu-id="4e5fb-129">This is unnecessary for a single-row insert.</span></span>  
  
### <a name="c-storing-a-running-total-based-on-the-type-of-insert"></a><span data-ttu-id="4e5fb-130">C.</span><span class="sxs-lookup"><span data-stu-id="4e5fb-130">C.</span></span> <span data-ttu-id="4e5fb-131">基于插入类型存储运行总计</span><span class="sxs-lookup"><span data-stu-id="4e5fb-131">Storing a running total based on the type of insert</span></span>  
 <span data-ttu-id="4e5fb-132">可以更改触发器以针对不同行数使用最优方法。</span><span class="sxs-lookup"><span data-stu-id="4e5fb-132">You can change the trigger to use the method optimal for the number of rows.</span></span> <span data-ttu-id="4e5fb-133">例如，可以在触发器逻辑中使用 `@@ROWCOUNT` 函数来区分单行插入和多行插入。</span><span class="sxs-lookup"><span data-stu-id="4e5fb-133">For example, the `@@ROWCOUNT` function can be used in the logic of the trigger to distinguish between a single and a multirow insert.</span></span>  
  
```  
-- Trigger valid for multirow and single row inserts  
-- and optimal for single row inserts.  
USE AdventureWorks2012;  
GO  
CREATE TRIGGER NewPODetail3  
ON Purchasing.PurchaseOrderDetail  
FOR INSERT AS  
IF @@ROWCOUNT = 1  
BEGIN  
   UPDATE Purchasing.PurchaseOrderHeader  
   SET SubTotal = SubTotal + LineTotal  
   FROM inserted  
   WHERE PurchaseOrderHeader.PurchaseOrderID = inserted.PurchaseOrderID  
END  
ELSE  
BEGIN  
      UPDATE Purchasing.PurchaseOrderHeader  
   SET SubTotal = SubTotal +   
      (SELECT SUM(LineTotal)  
      FROM inserted  
      WHERE PurchaseOrderHeader.PurchaseOrderID  
       = inserted.PurchaseOrderID)  
   WHERE PurchaseOrderHeader.PurchaseOrderID IN  
      (SELECT PurchaseOrderID FROM inserted)  
END;  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e5fb-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4e5fb-134">See Also</span></span>  
 [<span data-ttu-id="4e5fb-135">DML 触发器</span><span class="sxs-lookup"><span data-stu-id="4e5fb-135">DML Triggers</span></span>](dml-triggers.md)  
  
  
