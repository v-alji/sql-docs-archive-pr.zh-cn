---
title: 修改或重命名 DML 触发器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- renaming triggers
- modifying triggers
- DML triggers, modifying
ms.assetid: c7317eec-c0e9-479e-a4a7-83b6b6c58d59
author: rothja
ms.author: jroth
ms.openlocfilehash: 65bb13552b552d54b5547eadedc412977e423a57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590615"
---
# <a name="modify-or-rename-dml-triggers"></a><span data-ttu-id="43c82-102">修改或重命名 DML 触发器</span><span class="sxs-lookup"><span data-stu-id="43c82-102">Modify or Rename DML Triggers</span></span>
  <span data-ttu-id="43c82-103">本主题将说明如何在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)]修改或重命名 DML 触发器。</span><span class="sxs-lookup"><span data-stu-id="43c82-103">This topic describes how to modify or rename a DML trigger in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="43c82-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="43c82-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="43c82-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="43c82-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="43c82-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="43c82-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="43c82-107">建议</span><span class="sxs-lookup"><span data-stu-id="43c82-107">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="43c82-108">安全性</span><span class="sxs-lookup"><span data-stu-id="43c82-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="43c82-109">**若要修改或重命名 DML 触发器，请使用：**</span><span class="sxs-lookup"><span data-stu-id="43c82-109">**To modify or rename a DML trigger, using:**</span></span>  
  
     [<span data-ttu-id="43c82-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="43c82-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="43c82-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="43c82-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="43c82-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="43c82-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="43c82-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="43c82-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="43c82-114">重命名触发器时，该触发器必须位于当前数据库中，并且新名称必须遵守 [标识符](../databases/database-identifiers.md)规则。</span><span class="sxs-lookup"><span data-stu-id="43c82-114">When you rename a trigger, the trigger must be in the current database, and the new name must follow the rules for [identifiers](../databases/database-identifiers.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="43c82-115">建议</span><span class="sxs-lookup"><span data-stu-id="43c82-115">Recommendations</span></span>  
  
-   <span data-ttu-id="43c82-116">我们建议你不要使用 [sp_rename](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql) 存储过程重命名触发器。</span><span class="sxs-lookup"><span data-stu-id="43c82-116">We recommend you do not use the [sp_rename](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql) stored procedure to rename a trigger.</span></span> <span data-ttu-id="43c82-117">更改对象名的任一部分都可能破坏脚本和存储过程。</span><span class="sxs-lookup"><span data-stu-id="43c82-117">Changing any part of an object name can break scripts and stored procedures.</span></span> <span data-ttu-id="43c82-118">重命名触发器将不会更改 [sys.sql_modules](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) 目录视图的定义列中相应对象名的名称。</span><span class="sxs-lookup"><span data-stu-id="43c82-118">Renaming a trigger does not change the name of the corresponding object name in the definition column of the [sys.sql_modules](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) catalog view.</span></span> <span data-ttu-id="43c82-119">我们建议删除并重新创建触发器。</span><span class="sxs-lookup"><span data-stu-id="43c82-119">We recommend that you drop and re-create the trigger instead.</span></span>  
  
-   <span data-ttu-id="43c82-120">如果更改了 DML 触发器引用的对象名，则必须修改触发器以使其文本反映新的名称。</span><span class="sxs-lookup"><span data-stu-id="43c82-120">If you change the name of an object referenced by a DML trigger, you must modify the trigger so that its text reflects the new name.</span></span> <span data-ttu-id="43c82-121">因此，在重命名对象之前，需要先显示该对象的依赖关系，以确定所建议的更改是否会影响任何触发器。</span><span class="sxs-lookup"><span data-stu-id="43c82-121">Therefore, before you rename an object, display the dependencies of the object first to determine whether any triggers are affected by the proposed change.</span></span>  
  
-   <span data-ttu-id="43c82-122">也可以修改 DML 触发器以加密其定义。</span><span class="sxs-lookup"><span data-stu-id="43c82-122">A DML trigger can also be modified to encrypt its definition.</span></span>  
  
-   <span data-ttu-id="43c82-123">若要查看触发器的依赖项，您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或以下函数和目录视图：</span><span class="sxs-lookup"><span data-stu-id="43c82-123">To view the dependencies of a trigger, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or the following function and catalog views:</span></span>  
  
    -   [<span data-ttu-id="43c82-124">sys.sql_expression_dependencies (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="43c82-124">sys.sql_expression_dependencies &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
    -   [<span data-ttu-id="43c82-125">sys.dm_sql_referenced_entities (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="43c82-125">sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)  
  
    -   [<span data-ttu-id="43c82-126">sys.dm_sql_referencing_entities (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="43c82-126">sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql)  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="43c82-127">Security</span><span class="sxs-lookup"><span data-stu-id="43c82-127">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="43c82-128">权限</span><span class="sxs-lookup"><span data-stu-id="43c82-128">Permissions</span></span>  
 <span data-ttu-id="43c82-129">若要更改 DML 触发器，需要对于定义该触发器所在的表或视图拥有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="43c82-129">To alter a DML trigger requires ALTER permission on the table or view on which the trigger is defined.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="43c82-130">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="43c82-130">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-dml-trigger"></a><span data-ttu-id="43c82-131">修改 DML 触发器</span><span class="sxs-lookup"><span data-stu-id="43c82-131">To modify a DML trigger</span></span>  
  
1.  <span data-ttu-id="43c82-132">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="43c82-132">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="43c82-133">展开您所需的数据库，再展开 **“表”** ，然后展开包含要修改的触发器的表。</span><span class="sxs-lookup"><span data-stu-id="43c82-133">Expand the database that you want, expand **Tables**, and then expand the table that contains the trigger that you want to modify.</span></span>  
  
3.  <span data-ttu-id="43c82-134">展开 **“触发器”** ，右键单击要修改的触发器，然后单击 **“修改”** 。</span><span class="sxs-lookup"><span data-stu-id="43c82-134">Expand **Triggers**, right-click the trigger to modify, and then click **Modify**.</span></span>  
  
4.  <span data-ttu-id="43c82-135">修改该触发器，然后单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="43c82-135">Modify the trigger, and then click **Execute**.</span></span>  
  
#### <a name="to-rename-a-dml-trigger"></a><span data-ttu-id="43c82-136">重命名 DML 触发器</span><span class="sxs-lookup"><span data-stu-id="43c82-136">To rename a DML trigger</span></span>  
  
1.  <span data-ttu-id="43c82-137">[删除要重命名的触发器](../triggers/dml-triggers.md) 。</span><span class="sxs-lookup"><span data-stu-id="43c82-137">[Delete the trigger](../triggers/dml-triggers.md) that you want to rename.</span></span>  
  
2.  <span data-ttu-id="43c82-138">[重新创建触发器](../triggers/create-dml-triggers.md)，指定新名称。</span><span class="sxs-lookup"><span data-stu-id="43c82-138">[Re-create the trigger](../triggers/create-dml-triggers.md), specifying the new name.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="43c82-139">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="43c82-139">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-a-trigger-using-alter-trigger"></a><span data-ttu-id="43c82-140">使用 ALTER TRIGGER 修改触发器</span><span class="sxs-lookup"><span data-stu-id="43c82-140">To modify a trigger using ALTER TRIGGER</span></span>  
  
1.  <span data-ttu-id="43c82-141">连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="43c82-141">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="43c82-142">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="43c82-142">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="43c82-143">复制并将以下示例粘贴到查询中。</span><span class="sxs-lookup"><span data-stu-id="43c82-143">Copy and paste the following examples into the query.</span></span> <span data-ttu-id="43c82-144">执行第一个示例以创建 DML 触发器，在用户尝试添加或更改 `SalesPersonQuotaHistory` 表中的数据时，该触发器将用户定义的信息打印到客户端。</span><span class="sxs-lookup"><span data-stu-id="43c82-144">Execute the first example to create a DML trigger that prints a user-defined message to the client when a user tries to add or change data in the `SalesPersonQuotaHistory` table.</span></span> <span data-ttu-id="43c82-145">执行 [ALTER TRIGGER](/sql/t-sql/statements/alter-trigger-transact-sql) 语句修改该触发器以便仅对 `INSERT` 活动激发。</span><span class="sxs-lookup"><span data-stu-id="43c82-145">Execute the [ALTER TRIGGER](/sql/t-sql/statements/alter-trigger-transact-sql) statement to modify the trigger to fire only on `INSERT` activities.</span></span> <span data-ttu-id="43c82-146">此触发器十分有用，因为它可提醒向此表中插入行或更新行的用户也要通知 `Compensation` 部门。</span><span class="sxs-lookup"><span data-stu-id="43c82-146">This trigger is helpful because it reminds the user that updates or inserts rows into this table to also notify the `Compensation` department.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
```sql  
USE AdventureWorks2012;  
GO  
ALTER TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
AFTER INSERT  
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
#### <a name="to-rename-a-trigger-using-drop-trigger-and-alter-trigger"></a><span data-ttu-id="43c82-147">若要重命名触发器，请使用 DROP TRIGGER 和 ALTER TRIGGER</span><span class="sxs-lookup"><span data-stu-id="43c82-147">To rename a trigger using DROP TRIGGER and ALTER TRIGGER</span></span>  
  
1.  <span data-ttu-id="43c82-148">连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="43c82-148">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="43c82-149">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="43c82-149">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="43c82-150">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="43c82-150">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="43c82-151">该示例使用 [DROP TRIGGER](/sql/t-sql/statements/drop-trigger-transact-sql) 和 [ALTER TRIGGER](/sql/t-sql/statements/alter-trigger-transact-sql) 语句将 `Sales.bonus_reminder` 触发器重命名为 `Sales.bonus_reminder_2`。</span><span class="sxs-lookup"><span data-stu-id="43c82-151">This example use the [DROP TRIGGER](/sql/t-sql/statements/drop-trigger-transact-sql) and [ALTER TRIGGER](/sql/t-sql/statements/alter-trigger-transact-sql) statements to rename the `Sales.bonus_reminder` trigger to `Sales.bonus_reminder_2`.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder_2  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="43c82-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="43c82-152">See Also</span></span>  
 <span data-ttu-id="43c82-153">[CREATE TRIGGER (Transact-SQL)](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="43c82-153">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 <span data-ttu-id="43c82-154">[DROP TRIGGER (Transact-SQL)](/sql/t-sql/statements/drop-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="43c82-154">[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span></span>  
 <span data-ttu-id="43c82-155">[ENABLE TRIGGER (Transact-SQL)](/sql/t-sql/statements/enable-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="43c82-155">[ENABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/enable-trigger-transact-sql) </span></span>  
 <span data-ttu-id="43c82-156">[DISABLE TRIGGER (Transact-SQL)](/sql/t-sql/statements/disable-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="43c82-156">[DISABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/disable-trigger-transact-sql) </span></span>  
 <span data-ttu-id="43c82-157">[EVENTDATA (Transact-SQL)](/sql/t-sql/functions/eventdata-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="43c82-157">[EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql) </span></span>  
 <span data-ttu-id="43c82-158">[sp_rename (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="43c82-158">[sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql) </span></span>  
 <span data-ttu-id="43c82-159">[ALTER TRIGGER (Transact-SQL)](/sql/t-sql/statements/alter-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="43c82-159">[ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) </span></span>  
 <span data-ttu-id="43c82-160">[获取有关 DML 触发器的信息](../triggers/get-information-about-dml-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="43c82-160">[Get Information About DML Triggers](../triggers/get-information-about-dml-triggers.md) </span></span>  
 <span data-ttu-id="43c82-161">[sp_help (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="43c82-161">[sp_help &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql) </span></span>  
 <span data-ttu-id="43c82-162">[sp_helptrigger (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="43c82-162">[sp_helptrigger &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql) </span></span>  
 <span data-ttu-id="43c82-163">[sys.triggers (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="43c82-163">[sys.triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) </span></span>  
 <span data-ttu-id="43c82-164">[sys.trigger_events (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="43c82-164">[sys.trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql) </span></span>  
 <span data-ttu-id="43c82-165">[sys.sql_modules (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="43c82-165">[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span></span>  
 <span data-ttu-id="43c82-166">[sys.assembly_modules (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="43c82-166">[sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql) </span></span>  
 <span data-ttu-id="43c82-167">[sys.server_triggers (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="43c82-167">[sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) </span></span>  
 <span data-ttu-id="43c82-168">[sys.server_trigger_events (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="43c82-168">[sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql) </span></span>  
 <span data-ttu-id="43c82-169">[sys.server_sql_modules (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="43c82-169">[sys.server_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql) </span></span>  
 [<span data-ttu-id="43c82-170">sys.server_assembly_modules (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="43c82-170">sys.server_assembly_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql)  
  
  
