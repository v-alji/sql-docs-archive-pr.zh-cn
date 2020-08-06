---
title: 删除或禁用 DML 触发器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- DML triggers, disabling
- removing DML triggers
- disabling DML triggers
- dropping DML triggers
- deleting DML triggers
- DML triggers, removing
ms.assetid: 0f97f953-33c5-4b26-afeb-db2a26ce38b4
author: rothja
ms.author: jroth
ms.openlocfilehash: 39b345ade1258987df06938791ac0024e8612365
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590632"
---
# <a name="delete-or-disable-dml-triggers"></a><span data-ttu-id="4106b-102">删除或禁用 DML 触发器</span><span class="sxs-lookup"><span data-stu-id="4106b-102">Delete or Disable DML Triggers</span></span>
  <span data-ttu-id="4106b-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中删除或禁用 DML 触发器。</span><span class="sxs-lookup"><span data-stu-id="4106b-103">This topic describes how to delete or disable a DML trigger in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="4106b-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="4106b-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4106b-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="4106b-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4106b-106">建议</span><span class="sxs-lookup"><span data-stu-id="4106b-106">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="4106b-107">安全性</span><span class="sxs-lookup"><span data-stu-id="4106b-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4106b-108">**若要删除或禁用 DML 触发器，请使用：**</span><span class="sxs-lookup"><span data-stu-id="4106b-108">**To delete or disable a DML trigger, using:**</span></span>  
  
     [<span data-ttu-id="4106b-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4106b-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4106b-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4106b-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4106b-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="4106b-111">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="4106b-112">建议</span><span class="sxs-lookup"><span data-stu-id="4106b-112">Recommendations</span></span>  
  
-   <span data-ttu-id="4106b-113">删除了触发器后，它就从当前数据库中删除了。</span><span class="sxs-lookup"><span data-stu-id="4106b-113">When a trigger is deleted, it is dropped from the current database.</span></span> <span data-ttu-id="4106b-114">它所基于的表和数据不会受到影响。</span><span class="sxs-lookup"><span data-stu-id="4106b-114">The table and the data upon which it is based are not affected.</span></span> <span data-ttu-id="4106b-115">删除表将自动删除其上的所有触发器。</span><span class="sxs-lookup"><span data-stu-id="4106b-115">Deleting a table automatically deletes any triggers on the table.</span></span>  
  
-   <span data-ttu-id="4106b-116">在创建触发器时，触发器默认为启用状态。</span><span class="sxs-lookup"><span data-stu-id="4106b-116">A trigger is enabled by default when it is created.</span></span>  
  
-   <span data-ttu-id="4106b-117">禁用触发器不会删除该触发器。</span><span class="sxs-lookup"><span data-stu-id="4106b-117">Disabling a trigger does not drop it.</span></span> <span data-ttu-id="4106b-118">该触发器仍然作为对象存在于当前数据库中。</span><span class="sxs-lookup"><span data-stu-id="4106b-118">The trigger still exists as an object in the current database.</span></span> <span data-ttu-id="4106b-119">但是，当执行任意 INSERT、UPDATE 或 DELETE 语句（在其上对触发器进行了编程）时，触发器将不会激发。</span><span class="sxs-lookup"><span data-stu-id="4106b-119">However, the trigger will not fire when any INSERT, UPDATE, or DELETE statement on which it was programmed is executed.</span></span> <span data-ttu-id="4106b-120">已禁用的触发器可以被重新启用。</span><span class="sxs-lookup"><span data-stu-id="4106b-120">Triggers that are disabled can be reenabled.</span></span> <span data-ttu-id="4106b-121">启用触发器并不是要重新创建它。</span><span class="sxs-lookup"><span data-stu-id="4106b-121">Enabling a trigger does not re-create it.</span></span> <span data-ttu-id="4106b-122">触发器将以最初创建它时的方式激发。</span><span class="sxs-lookup"><span data-stu-id="4106b-122">The trigger fires in the same manner as when it was originally created.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4106b-123">Security</span><span class="sxs-lookup"><span data-stu-id="4106b-123">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4106b-124">权限</span><span class="sxs-lookup"><span data-stu-id="4106b-124">Permissions</span></span>  
 <span data-ttu-id="4106b-125">若要删除 DML 触发器，要求对要定义触发器的表或视图具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="4106b-125">To delete a DML trigger requires ALTER permission on the table or view on which the trigger is defined.</span></span>  
  
 <span data-ttu-id="4106b-126">若要禁用或启用 DML 触发器，用户必须至少对为其创建触发器的表或视图具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="4106b-126">To disable or enable a DML trigger, at a minimum, a user must have ALTER permission on the table or view on which the trigger was created.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4106b-127">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4106b-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-dml-trigger"></a><span data-ttu-id="4106b-128">删除 DML 触发器</span><span class="sxs-lookup"><span data-stu-id="4106b-128">To delete a DML trigger</span></span>  
  
1.  <span data-ttu-id="4106b-129">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="4106b-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="4106b-130">展开您所需的数据库，再展开 **“表”** ，然后展开包含要删除的触发器的表。</span><span class="sxs-lookup"><span data-stu-id="4106b-130">Expand the database that you want, expand **Tables**, and then expand the table that contains the trigger that you want to delete.</span></span>  
  
3.  <span data-ttu-id="4106b-131">展开 **“触发器”** ，右键单击要删除的触发器，再单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="4106b-131">Expand **Triggers**, right-click the trigger to delete, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="4106b-132">在 **“删除对象”** 对话框中，确认要删除的触发器，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="4106b-132">In the **Delete Object** dialog box, verify the trigger to delete, and then click **OK**.</span></span>  
  
#### <a name="to-disable-and-enable-a-dml-trigger"></a><span data-ttu-id="4106b-133">禁用和启用 DML 触发器</span><span class="sxs-lookup"><span data-stu-id="4106b-133">To disable and enable a DML trigger</span></span>  
  
1.  <span data-ttu-id="4106b-134">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="4106b-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="4106b-135">展开您所需的数据库，再展开 **“表”** ，然后展开包含要禁用的触发器的表。</span><span class="sxs-lookup"><span data-stu-id="4106b-135">Expand the database that you want, expand **Tables**, and then expand the table that contains the trigger that you want to disable.</span></span>  
  
3.  <span data-ttu-id="4106b-136">展开 **“触发器”** ，右键单击要禁用的触发器，再单击 **“禁用”** 。</span><span class="sxs-lookup"><span data-stu-id="4106b-136">Expand **Triggers**, right-click the trigger to disable, and then click **Disable**.</span></span>  
  
4.  <span data-ttu-id="4106b-137">若要启用触发器，请单击 **“启用”** 。</span><span class="sxs-lookup"><span data-stu-id="4106b-137">To enable the trigger, click **Enable**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4106b-138">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4106b-138">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-dml-trigger"></a><span data-ttu-id="4106b-139">删除 DML 触发器</span><span class="sxs-lookup"><span data-stu-id="4106b-139">To delete a DML trigger</span></span>  
  
1.  <span data-ttu-id="4106b-140">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4106b-140">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4106b-141">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="4106b-141">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4106b-142">复制以下示例并将其粘贴到查询窗口中。</span><span class="sxs-lookup"><span data-stu-id="4106b-142">Copy and paste the following examples into the query window.</span></span> <span data-ttu-id="4106b-143">执行 [CREATE TRIGGER](/sql/t-sql/statements/create-trigger-transact-sql) 语句以创建 `Sales.bonus_reminder` 触发器。</span><span class="sxs-lookup"><span data-stu-id="4106b-143">Execute the [CREATE TRIGGER](/sql/t-sql/statements/create-trigger-transact-sql) statement to create the `Sales.bonus_reminder` trigger.</span></span> <span data-ttu-id="4106b-144">若要删除该触发器，请执行 [DROP TRIGGER](/sql/t-sql/statements/drop-trigger-transact-sql) 语句。</span><span class="sxs-lookup"><span data-stu-id="4106b-144">To delete the trigger, execute the [DROP TRIGGER](/sql/t-sql/statements/drop-trigger-transact-sql) statement.</span></span>  
  
```sql  
--Create the trigger.  
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
--Delete the trigger.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ('Sales.bonus_reminder', 'TR') IS NOT NULL  
   DROP TRIGGER Sales.bonus_reminder;  
GO  
  
```  
  
#### <a name="to-disable-and-enable-a-dml-trigger"></a><span data-ttu-id="4106b-145">禁用和启用 DML 触发器</span><span class="sxs-lookup"><span data-stu-id="4106b-145">To disable and enable a DML trigger</span></span>  
  
1.  <span data-ttu-id="4106b-146">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4106b-146">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4106b-147">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="4106b-147">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4106b-148">复制以下示例并将其粘贴到查询窗口中。</span><span class="sxs-lookup"><span data-stu-id="4106b-148">Copy and paste the following examples into the query window.</span></span> <span data-ttu-id="4106b-149">执行 [CREATE TRIGGER](/sql/t-sql/statements/create-trigger-transact-sql) 语句以创建 `Sales.bonus_reminder` 触发器。</span><span class="sxs-lookup"><span data-stu-id="4106b-149">Execute the [CREATE TRIGGER](/sql/t-sql/statements/create-trigger-transact-sql) statement to create the `Sales.bonus_reminder` trigger.</span></span> <span data-ttu-id="4106b-150">若要禁用和启用该触发器，请分别执行 [DISABLE TRIGGER](/sql/t-sql/statements/disable-trigger-transact-sql) 语句和 [ENABLE TRIGGER](/sql/t-sql/statements/enable-trigger-transact-sql) 语句。</span><span class="sxs-lookup"><span data-stu-id="4106b-150">To disable and enable the trigger, execute the [DISABLE TRIGGER](/sql/t-sql/statements/disable-trigger-transact-sql) and [ENABLE TRIGGER](/sql/t-sql/statements/enable-trigger-transact-sql) statements, respectively.</span></span>  
  
```sql  
--Create the trigger.  
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
--Disable the trigger.  
USE AdventureWorks2012;  
GO  
DISABLE TRIGGER Sales.bonus_reminder ON Sales.SalesPersonQuotaHistory;  
GO  
  
```  
  
```sql  
--Enable the trigger.  
USE AdventureWorks2012;  
GO  
ENABLE TRIGGER Sales.bonus_reminder ON Sales.SalesPersonQuotaHistory;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="4106b-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4106b-151">See Also</span></span>  
 <span data-ttu-id="4106b-152">[ALTER TRIGGER (Transact-SQL)](/sql/t-sql/statements/alter-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4106b-152">[ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) </span></span>  
 <span data-ttu-id="4106b-153">[CREATE TRIGGER (Transact-SQL)](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4106b-153">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 <span data-ttu-id="4106b-154">[DROP TRIGGER (Transact-SQL)](/sql/t-sql/statements/drop-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4106b-154">[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span></span>  
 <span data-ttu-id="4106b-155">[ENABLE TRIGGER (Transact-SQL)](/sql/t-sql/statements/enable-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4106b-155">[ENABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/enable-trigger-transact-sql) </span></span>  
 <span data-ttu-id="4106b-156">[DISABLE TRIGGER (Transact-SQL)](/sql/t-sql/statements/disable-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4106b-156">[DISABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/disable-trigger-transact-sql) </span></span>  
 <span data-ttu-id="4106b-157">[EVENTDATA (Transact-SQL)](/sql/t-sql/functions/eventdata-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4106b-157">[EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql) </span></span>  
 <span data-ttu-id="4106b-158">[获取有关 DML 触发器的信息](dml-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="4106b-158">[Get Information About DML Triggers](dml-triggers.md) </span></span>  
 <span data-ttu-id="4106b-159">[sp_help (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4106b-159">[sp_help &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql) </span></span>  
 <span data-ttu-id="4106b-160">[sp_helptrigger (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4106b-160">[sp_helptrigger &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql) </span></span>  
 <span data-ttu-id="4106b-161">[sys.triggers (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4106b-161">[sys.triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) </span></span>  
 <span data-ttu-id="4106b-162">[sys.trigger_events (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4106b-162">[sys.trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql) </span></span>  
 <span data-ttu-id="4106b-163">[sys.sql_modules (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4106b-163">[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span></span>  
 <span data-ttu-id="4106b-164">[sys.assembly_modules (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4106b-164">[sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql) </span></span>  
 <span data-ttu-id="4106b-165">[sys.server_triggers (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4106b-165">[sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) </span></span>  
 <span data-ttu-id="4106b-166">[sys.server_trigger_events (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4106b-166">[sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql) </span></span>  
 <span data-ttu-id="4106b-167">[sys.server_sql_modules (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4106b-167">[sys.server_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql) </span></span>  
 [<span data-ttu-id="4106b-168">sys.server_assembly_modules (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4106b-168">sys.server_assembly_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql)  
  
  
