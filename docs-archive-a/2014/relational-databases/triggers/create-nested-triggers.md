---
title: 创建嵌套触发器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- recursive DML triggers [SQL Server]
- DML triggers, nested
- triggers [SQL Server], nested
- direct recursion [SQL Server]
- triggers [SQL Server], recursive
- DML triggers, recursive
- RECURSIVE_TRIGGERS option
- indirect recursion [SQL Server]
- nested DML triggers
ms.assetid: cd522dda-b4ab-41b8-82b0-02445bdba7af
author: rothja
ms.author: jroth
ms.openlocfilehash: c0016fc3cdd93ea78ceed56efa076a01bd85be50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590637"
---
# <a name="create-nested-triggers"></a><span data-ttu-id="9179b-102">创建嵌套触发器</span><span class="sxs-lookup"><span data-stu-id="9179b-102">Create Nested Triggers</span></span>
  <span data-ttu-id="9179b-103">当触发器执行启动其他触发器的操作时，DML 和 DDL 触发器都是嵌套触发器。</span><span class="sxs-lookup"><span data-stu-id="9179b-103">Both DML and DDL triggers are nested when a trigger performs an action that initiates another trigger.</span></span> <span data-ttu-id="9179b-104">这些操作都可以启动其他触发器等。</span><span class="sxs-lookup"><span data-stu-id="9179b-104">These actions can initiate other triggers, and so on.</span></span> <span data-ttu-id="9179b-105">DML 触发器和 DDL 触发器最多可以嵌套 32 层。</span><span class="sxs-lookup"><span data-stu-id="9179b-105">DML and DDL triggers can be nested up to 32 levels.</span></span> <span data-ttu-id="9179b-106">可以通过 **nested triggers** 服务器配置选项来控制是否可以嵌套 AFTER 触发器。</span><span class="sxs-lookup"><span data-stu-id="9179b-106">You can control whether AFTER triggers can be nested through the **nested triggers** server configuration option.</span></span> <span data-ttu-id="9179b-107">但不管此设置是什么，都可以嵌套 INSTEAD OF 触发器（只有 DML 触发器可以为 INSTEAD OF 触发器）。</span><span class="sxs-lookup"><span data-stu-id="9179b-107">INSTEAD OF triggers (only DML triggers can be INSTEAD OF triggers) can be nested regardless of this setting.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9179b-108">[!INCLUDE[tsql](../../includes/tsql-md.md)] 触发器中对托管代码的任何引用均计为 32 层嵌套限制中的一层。</span><span class="sxs-lookup"><span data-stu-id="9179b-108">Any reference to managed code from a [!INCLUDE[tsql](../../includes/tsql-md.md)] trigger counts as one level against the 32-level nesting limit.</span></span> <span data-ttu-id="9179b-109">从托管代码内部调用的方法不根据此限制进行计数。</span><span class="sxs-lookup"><span data-stu-id="9179b-109">Methods invoked from within managed code do not count against this limit.</span></span>  
  
 <span data-ttu-id="9179b-110">如果允许使用嵌套触发器，且链中的一个触发器启动了一个无限循环，则将超出嵌套层限制，且触发器将终止。</span><span class="sxs-lookup"><span data-stu-id="9179b-110">If nested triggers are allowed and a trigger in the chain starts an infinite loop, the nesting level is exceeded and the trigger terminates.</span></span>  
  
 <span data-ttu-id="9179b-111">可使用嵌套触发器执行一些有用的日常工作，如保存前一个触发器所影响行的一个备份副本。</span><span class="sxs-lookup"><span data-stu-id="9179b-111">You can use nested triggers to perform useful housekeeping functions such as storing a backup copy of rows affected by a previous trigger.</span></span> <span data-ttu-id="9179b-112">例如，可以在 `PurchaseOrderDetail` 上创建一个触发器，以保存由 `PurchaseOrderDetail` 触发器所删除的 `delcascadetrig` 行的备份副本。</span><span class="sxs-lookup"><span data-stu-id="9179b-112">For example, you can create a trigger on `PurchaseOrderDetail` that saves a backup copy of the `PurchaseOrderDetail` rows that the `delcascadetrig` trigger deleted.</span></span> <span data-ttu-id="9179b-113">`delcascadetrig` 触发器有效时，从 `PurchaseOrderID` 中删除 `PurchaseOrderHeader` 1965 将删除 `PurchaseOrderDetail`中对应的行。</span><span class="sxs-lookup"><span data-stu-id="9179b-113">With the `delcascadetrig` trigger in effect, deleting `PurchaseOrderID` 1965 from `PurchaseOrderHeader` deletes the corresponding row or rows from `PurchaseOrderDetail`.</span></span> <span data-ttu-id="9179b-114">为了保存数据，可在 `PurchaseOrderDetail` 上创建一个 DELETE 触发器，该触发器可将删除的数据保存到另一个单独创建的表 ( `del_save`) 中。</span><span class="sxs-lookup"><span data-stu-id="9179b-114">To save the data, you can create a DELETE trigger on `PurchaseOrderDetail` that saves the deleted data into another separately created table, `del_save`.</span></span> <span data-ttu-id="9179b-115">例如：</span><span class="sxs-lookup"><span data-stu-id="9179b-115">For example:</span></span>  
  
```  
CREATE TRIGGER Purchasing.savedel  
   ON Purchasing.PurchaseOrderDetail  
FOR DELETE  
AS  
   INSERT del_save;  
   SELECT * FROM deleted;  
```  
  
 <span data-ttu-id="9179b-116">建议不要按与顺序相关的序列使用嵌套触发器。</span><span class="sxs-lookup"><span data-stu-id="9179b-116">We do not recommend using nested triggers in an order-dependent sequence.</span></span> <span data-ttu-id="9179b-117">应使用单独的触发器级联数据修改。</span><span class="sxs-lookup"><span data-stu-id="9179b-117">Use separate triggers to cascade data modifications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9179b-118">由于触发器在事务中执行，如果在一组嵌套触发器的任意层中发生错误，则整个事务都将取消，且所有的数据修改都将回滚。</span><span class="sxs-lookup"><span data-stu-id="9179b-118">Because triggers execute within a transaction, a failure at any level of a set of nested triggers cancels the entire transaction, and all data modifications are rolled back.</span></span> <span data-ttu-id="9179b-119">在触发器中包含 PRINT 语句可以确定错误的发生位置。</span><span class="sxs-lookup"><span data-stu-id="9179b-119">Include PRINT statements in your triggers so that you can determine where the failure has occurred.</span></span>  
  
## <a name="recursive-triggers"></a><span data-ttu-id="9179b-120">递归触发器</span><span class="sxs-lookup"><span data-stu-id="9179b-120">Recursive Triggers</span></span>  
 <span data-ttu-id="9179b-121">AFTER 触发器不会以递归方式自行调用，除非设置了 RECURSIVE_TRIGGERS 数据库选项。</span><span class="sxs-lookup"><span data-stu-id="9179b-121">An AFTER trigger does not call itself recursively unless the RECURSIVE_TRIGGERS database option is set.</span></span>  
  
 <span data-ttu-id="9179b-122">有两种不同的递归方式：</span><span class="sxs-lookup"><span data-stu-id="9179b-122">There are two types of recursion:</span></span>  
  
-   <span data-ttu-id="9179b-123">直接递归</span><span class="sxs-lookup"><span data-stu-id="9179b-123">Direct recursion</span></span>  
  
     <span data-ttu-id="9179b-124">在触发器触发并执行一个导致同一个触发器再次触发的操作时，将发生此递归。</span><span class="sxs-lookup"><span data-stu-id="9179b-124">This recursion occurs when a trigger fires and performs an action that causes the same trigger to fire again.</span></span> <span data-ttu-id="9179b-125">例如，应用程序更新了表 **T3**，从而触发了触发器 **Trig3** 。</span><span class="sxs-lookup"><span data-stu-id="9179b-125">For example, an application updates table **T3**; this causes trigger **Trig3** to fire.</span></span> <span data-ttu-id="9179b-126">**Trig3** 再次更新表 **T3** ，从而再次触发了触发器 **Trig3** 。</span><span class="sxs-lookup"><span data-stu-id="9179b-126">**Trig3** updates table **T3** again; this causes trigger **Trig3** to fire again.</span></span>  
  
     <span data-ttu-id="9179b-127">调用其他类型的触发器（AFTER 或 INSTEAD OF）之后再次调用同一个触发器时，也会发生直接递归。</span><span class="sxs-lookup"><span data-stu-id="9179b-127">Direct recursion can also occur when the same trigger is called again, but after a trigger of a different type (AFTER or INSTEAD OF) is called.</span></span> <span data-ttu-id="9179b-128">换言之，当同一个 INSTEAD OF 触发器被第二次调用时，即使在这两次调用之间调用了一个或多个 AFTER 触发器，也会发生 INSTEAD OF 触发器的直接递归。</span><span class="sxs-lookup"><span data-stu-id="9179b-128">In other words, direct recursion of an INSTEAD OF trigger can occur when the same INSTEAD OF trigger is called for a second time, even if one or more AFTER triggers are called in between.</span></span> <span data-ttu-id="9179b-129">同样，当同一个 AFTER 触发器被第二次调用时，即使在这两次调用之间调用了一个或多个 INSTEAD OF 触发器，也会发生 AFTER 触发器的直接递归。</span><span class="sxs-lookup"><span data-stu-id="9179b-129">Likewise, direct recursion of an AFTER trigger can occur when the same AFTER trigger is called for a second time, even if one or more INSTEAD OF triggers are called in between.</span></span> <span data-ttu-id="9179b-130">例如，一个应用程序对表 **T4**进行更新。</span><span class="sxs-lookup"><span data-stu-id="9179b-130">For example, an application updates table **T4**.</span></span> <span data-ttu-id="9179b-131">此更新将导致触发 INSTEAD OF 触发器 **Trig4** 。</span><span class="sxs-lookup"><span data-stu-id="9179b-131">This update causes INSTEAD OF trigger **Trig4** to fire.</span></span> <span data-ttu-id="9179b-132">**Trig4** 对表 **T5**进行更新。</span><span class="sxs-lookup"><span data-stu-id="9179b-132">**Trig4** updates table **T5**.</span></span> <span data-ttu-id="9179b-133">此更新将导致触发 AFTER 触发器 **Trig5** 。</span><span class="sxs-lookup"><span data-stu-id="9179b-133">This update causes AFTER trigger **Trig5** to fire.</span></span> <span data-ttu-id="9179b-134">**Trig5** 更新表 **T4**，此更新将导致再次触发 INSTEAD OF 触发器 **Trig4** 。</span><span class="sxs-lookup"><span data-stu-id="9179b-134">**Trig5** updates table **T4**, and this update causes INSTEAD OF trigger **Trig4** to fire again.</span></span> <span data-ttu-id="9179b-135">此事件链即被认为是 **Trig4**的直接递归。</span><span class="sxs-lookup"><span data-stu-id="9179b-135">This chain of events is considered direct recursion for **Trig4**.</span></span>  
  
-   <span data-ttu-id="9179b-136">间接递归</span><span class="sxs-lookup"><span data-stu-id="9179b-136">Indirect recursion</span></span>  
  
     <span data-ttu-id="9179b-137">当触发器触发并执行导致触发相同类型的其他触发器（AFTER 或 INSTEAD OF）的操作时，会发生此类递归。</span><span class="sxs-lookup"><span data-stu-id="9179b-137">This recursion occurs when a trigger fires and performs an action that causes another trigger of the same type (AFTER or INSTEAD OF) to fire.</span></span> <span data-ttu-id="9179b-138">第二个触发器执行一个再次触发第一个触发器的操作。</span><span class="sxs-lookup"><span data-stu-id="9179b-138">This second trigger performs an action that causes the original trigger to fire again.</span></span> <span data-ttu-id="9179b-139">换言之，当在这两次调用之间调用其他 INSTEAD OF 触发器之前第二次调用 INSTEAD OF 触发器，便会发生间接递归。</span><span class="sxs-lookup"><span data-stu-id="9179b-139">In other words, indirect recursion can occur when an INSTEAD OF trigger is called for a second time, but not until another INSTEAD OF trigger is called in between.</span></span> <span data-ttu-id="9179b-140">同样，当在这两次调用之间调用其他 AFTER 触发器之前第二次调用 AFTER 触发器，也会发生间接递归。</span><span class="sxs-lookup"><span data-stu-id="9179b-140">Likewise, indirect recursion can occur when an AFTER trigger is called for a second time, but not until another AFTER trigger is called in between.</span></span> <span data-ttu-id="9179b-141">例如，一个应用程序对表 **T1**进行更新。</span><span class="sxs-lookup"><span data-stu-id="9179b-141">For example, an application updates table **T1**.</span></span> <span data-ttu-id="9179b-142">此更新将导致触发 AFTER 触发器 **Trig1** 。</span><span class="sxs-lookup"><span data-stu-id="9179b-142">This update causes AFTER trigger **Trig1** to fire.</span></span> <span data-ttu-id="9179b-143">**Trig1** 更新表 **T2**，此更新将导致触发 AFTER 触发器 **Trig2** 。</span><span class="sxs-lookup"><span data-stu-id="9179b-143">**Trig1** updates table **T2**, and this update causes AFTER trigger **Trig2** to fire.</span></span> <span data-ttu-id="9179b-144">**Trig2** 反过来更新表 **T1** ，从而导致再次触发 AFTER 触发器 **Trig1** 。</span><span class="sxs-lookup"><span data-stu-id="9179b-144">**Trig2** in turn updates table **T1** that causes AFTER trigger **Trig1** to fire again.</span></span>  
  
 <span data-ttu-id="9179b-145">当 RECURSIVE_TRIGGERS 数据库选项设置为 OFF 时，仅阻止 AFTER 触发器的直接递归。</span><span class="sxs-lookup"><span data-stu-id="9179b-145">Only direct recursion of AFTER triggers is prevented when the RECURSIVE_TRIGGERS database option is set to OFF.</span></span> <span data-ttu-id="9179b-146">若要禁用 AFTER 触发器的间接递归，还必须将 **nested triggers** 服务器选项设置为 **0**。</span><span class="sxs-lookup"><span data-stu-id="9179b-146">To disable indirect recursion of AFTER triggers, also set the **nested triggers** server option to **0**.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="9179b-147">示例</span><span class="sxs-lookup"><span data-stu-id="9179b-147">Examples</span></span>  
 <span data-ttu-id="9179b-148">下面的示例中说明使用递归触发器来解决自引用关系（也称为传递闭包）。</span><span class="sxs-lookup"><span data-stu-id="9179b-148">The following example shows using recursive triggers to solve a self-referencing relationship (also known as transitive closure).</span></span> <span data-ttu-id="9179b-149">例如，表 `emp_mgr` 定义了以下内容：</span><span class="sxs-lookup"><span data-stu-id="9179b-149">For example, the table `emp_mgr` defines the following:</span></span>  
  
-   <span data-ttu-id="9179b-150">一个公司中的雇员 (`emp`)。</span><span class="sxs-lookup"><span data-stu-id="9179b-150">An employee (`emp`) in a company.</span></span>  
  
-   <span data-ttu-id="9179b-151">每个雇员的经理 (`mgr`)。</span><span class="sxs-lookup"><span data-stu-id="9179b-151">The manager for each employee (`mgr`).</span></span>  
  
-   <span data-ttu-id="9179b-152">组织树中向每个经理汇报的雇员总数 (`NoOfReports`)。</span><span class="sxs-lookup"><span data-stu-id="9179b-152">The total number of employees in the organizational tree reporting to each employee (`NoOfReports`).</span></span>  
  
 <span data-ttu-id="9179b-153">递归 UPDATE 触发器可以用于在插入新雇员记录时让 `NoOfReports` 列保持最新。</span><span class="sxs-lookup"><span data-stu-id="9179b-153">A recursive UPDATE trigger can be used to keep the `NoOfReports` column up-to-date as new employee records are inserted.</span></span> <span data-ttu-id="9179b-154">INSERT 触发器更新经理记录的 `NoOfReports` 列，而该操作递归更新管理层向上的其他记录的 `NoOfReports` 列。</span><span class="sxs-lookup"><span data-stu-id="9179b-154">The INSERT trigger updates the `NoOfReports` column of the manager record, which recursively updates the `NoOfReports` column of other records up the management hierarchy.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
-- Turn recursive triggers ON in the database.  
ALTER DATABASE AdventureWorks2012  
   SET RECURSIVE_TRIGGERS ON;  
GO  
CREATE TABLE dbo.emp_mgr (  
   emp char(30) PRIMARY KEY,  
    mgr char(30) NULL FOREIGN KEY REFERENCES emp_mgr(emp),  
    NoOfReports int DEFAULT 0  
);  
GO  
CREATE TRIGGER dbo.emp_mgrins ON dbo.emp_mgr  
FOR INSERT  
AS  
DECLARE @e char(30), @m char(30);  
DECLARE c1 CURSOR FOR  
   SELECT emp_mgr.emp  
   FROM   emp_mgr, inserted  
   WHERE emp_mgr.emp = inserted.mgr;  
  
OPEN c1;  
FETCH NEXT FROM c1 INTO @e;  
WHILE @@fetch_status = 0  
BEGIN  
   UPDATE dbo.emp_mgr  
   SET emp_mgr.NoOfReports = emp_mgr.NoOfReports + 1 -- Add 1 for newly  
   WHERE emp_mgr.emp = @e ;                           -- added employee.  
  
   FETCH NEXT FROM c1 INTO @e;  
END  
CLOSE c1;  
DEALLOCATE c1;  
GO  
-- This recursive UPDATE trigger works assuming:  
--   1. Only singleton updates on emp_mgr.  
--   2. No inserts in the middle of the org tree.  
CREATE TRIGGER dbo.emp_mgrupd ON dbo.emp_mgr FOR UPDATE  
AS  
IF UPDATE (mgr)  
BEGIN  
   UPDATE dbo.emp_mgr  
   SET emp_mgr.NoOfReports = emp_mgr.NoOfReports + 1 -- Increment mgr's  
   FROM inserted                            -- (no. of reports) by  
   WHERE emp_mgr.emp = inserted.mgr;         -- 1 for the new report.  
  
   UPDATE dbo.emp_mgr  
   SET emp_mgr.NoOfReports = emp_mgr.NoOfReports - 1 -- Decrement mgr's  
   FROM deleted                             -- (no. of reports) by 1  
   WHERE emp_mgr.emp = deleted.mgr;          -- for the new report.  
END  
GO  
-- Insert some test data rows.  
INSERT dbo.emp_mgr(emp, mgr) VALUES  
    ('Harry', NULL)  
    ,('Alice', 'Harry')  
    ,('Paul', 'Alice')  
    ,('Joe', 'Alice')  
    ,('Dave', 'Joe');  
GO  
SELECT emp,mgr,NoOfReports  
FROM dbo.emp_mgr;  
GO  
-- Change Dave's manager from Joe to Harry  
UPDATE dbo.emp_mgr SET mgr = 'Harry'  
WHERE emp = 'Dave';  
GO  
SELECT emp,mgr,NoOfReports FROM emp_mgr;  
  
GO  
```  
  
 <span data-ttu-id="9179b-155">以下是更新前的结果。</span><span class="sxs-lookup"><span data-stu-id="9179b-155">Here are the results before the update.</span></span>  
  
```  
emp                            mgr                           NoOfReports  
------------------------------ ----------------------------- -----------  
Alice                          Harry                          2  
Dave                           Joe                            0  
Harry                          NULL                           1  
Joe                            Alice                          1  
Paul                           Alice                          0  
```  
  
 <span data-ttu-id="9179b-156">以下是更新后的结果。</span><span class="sxs-lookup"><span data-stu-id="9179b-156">Here are the results after the update.</span></span>  
  
```  
emp                            mgr                           NoOfReports  
------------------------------ ----------------------------- -----------  
Alice                          Harry                          2  
Dave                           Harry                          0  
Harry                          NULL                           2  
Joe                            Alice                          0  
Paul                           Alice                          0  
```  
  
 <span data-ttu-id="9179b-157">**设置 nested triggers 选项**</span><span class="sxs-lookup"><span data-stu-id="9179b-157">**To set the nested triggers option**</span></span>  
  
-   [<span data-ttu-id="9179b-158">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9179b-158">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
 <span data-ttu-id="9179b-159">**设置 RECURSIVE_TRIGGERS 数据库选项**</span><span class="sxs-lookup"><span data-stu-id="9179b-159">**To set the RECURSIVE_TRIGGERS database option**</span></span>  
  
-   [<span data-ttu-id="9179b-160">ALTER DATABASE SET 选项 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9179b-160">ALTER DATABASE SET Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
## <a name="see-also"></a><span data-ttu-id="9179b-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9179b-161">See Also</span></span>  
 <span data-ttu-id="9179b-162">[CREATE TRIGGER (Transact-SQL)](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9179b-162">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 [<span data-ttu-id="9179b-163">配置 nested triggers 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="9179b-163">Configure the nested triggers Server Configuration Option</span></span>](../../database-engine/configure-windows/configure-the-nested-triggers-server-configuration-option.md)  
  
  
