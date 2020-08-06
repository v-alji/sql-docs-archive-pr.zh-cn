---
title: 获取有关 DML 触发器的信息 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- metadata [SQL Server], triggers
- viewing DML triggers
- DML triggers, metadata
- displaying DML triggers
- status information [SQL Server], triggers
- DML triggers, viewing
ms.assetid: 37574aac-181d-4aca-a2cc-8abff64237dc
author: rothja
ms.author: jroth
ms.openlocfilehash: 2f65976d2f517137e23bd9e5e1c98cc76324bc49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590628"
---
# <a name="get-information-about-dml-triggers"></a><span data-ttu-id="b94f6-102">获取有关 DML 触发器的信息</span><span class="sxs-lookup"><span data-stu-id="b94f6-102">Get Information About DML Triggers</span></span>
  <span data-ttu-id="b94f6-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中获取有关 DML 触发器的信息。</span><span class="sxs-lookup"><span data-stu-id="b94f6-103">This topic describes how to get information about DML triggers in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="b94f6-104">此信息可包含针对某个表的触发器的类型、触发器的名称、其所有者以及创建或修改日期。</span><span class="sxs-lookup"><span data-stu-id="b94f6-104">This information can include the types of triggers on a table, the name of a trigger, its owner and the date it was created or modified.</span></span> <span data-ttu-id="b94f6-105">如果在创建触发器时未加密，您可获取该触发器的定义。</span><span class="sxs-lookup"><span data-stu-id="b94f6-105">If the trigger was not encrypted when it was created, you obtain the definition of the trigger.</span></span> <span data-ttu-id="b94f6-106">通过该定义，可以帮助您了解该触发器如何影响对其定义该触发器的表。</span><span class="sxs-lookup"><span data-stu-id="b94f6-106">You can use the definition to help you understand how a trigger affects the table up on which it is defined.</span></span> <span data-ttu-id="b94f6-107">此外，您可以找出特定触发器使用的对象。</span><span class="sxs-lookup"><span data-stu-id="b94f6-107">Also, you can find out the objects that a specific trigger uses.</span></span> <span data-ttu-id="b94f6-108">通过该信息，可在数据库中影响触发器的对象发生更改或删除它们时确定这些对象。</span><span class="sxs-lookup"><span data-stu-id="b94f6-108">With this information, you can identify the objects that affect the trigger if they are changed or deleted in the database.</span></span>  
  
 <span data-ttu-id="b94f6-109">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="b94f6-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b94f6-110">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="b94f6-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b94f6-111">安全性</span><span class="sxs-lookup"><span data-stu-id="b94f6-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b94f6-112">**若要获取有关 DML 触发器的信息，请使用：**</span><span class="sxs-lookup"><span data-stu-id="b94f6-112">**To get information about DML triggers, using:**</span></span>  
  
     [<span data-ttu-id="b94f6-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b94f6-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b94f6-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b94f6-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b94f6-115">开始之前</span><span class="sxs-lookup"><span data-stu-id="b94f6-115">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b94f6-116">Security</span><span class="sxs-lookup"><span data-stu-id="b94f6-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b94f6-117">权限</span><span class="sxs-lookup"><span data-stu-id="b94f6-117">Permissions</span></span>  
 <span data-ttu-id="b94f6-118">**sys.sql.modules**, **sys.object**, **sys.triggers**, **sys.events**, **sys.trigger_events**</span><span class="sxs-lookup"><span data-stu-id="b94f6-118">**sys.sql.modules**, **sys.object**, **sys.triggers**, **sys.events**, **sys.trigger_events**</span></span>  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] <span data-ttu-id="b94f6-119">有关详细信息，请参阅 [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="b94f6-119">For more information, see [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md).</span></span>  
  
 <span data-ttu-id="b94f6-120">OBJECT_DEFINITION, OBJECTPROPERTY, **sp_helptext**</span><span class="sxs-lookup"><span data-stu-id="b94f6-120">OBJECT_DEFINITION, OBJECTPROPERTY, **sp_helptext**</span></span>  
 <span data-ttu-id="b94f6-121">要求 **公共** 角色具有成员身份。</span><span class="sxs-lookup"><span data-stu-id="b94f6-121">Requires membership in the **public** role.</span></span> <span data-ttu-id="b94f6-122">用户对象的定义对于对象所有者或具有下列任一权限的被授权者可见：ALTER、CONTROL、TAKE OWNERSHIP 或 VIEW DEFINITION。</span><span class="sxs-lookup"><span data-stu-id="b94f6-122">The definition of user objects is visible to the object owner or grantees that have any one of the following permissions: ALTER, CONTROL, TAKE OWNERSHIP, or VIEW DEFINITION.</span></span> <span data-ttu-id="b94f6-123">**db_owner**、 **db_ddladmin**和 **db_securityadmin** 固定数据库角色的成员隐式具有这些权限。</span><span class="sxs-lookup"><span data-stu-id="b94f6-123">These permissions are implicitly held by members of the **db_owner**, **db_ddladmin**, and **db_securityadmin** fixed database roles.</span></span>  
  
 <span data-ttu-id="b94f6-124">**sys.sql_expression_dependencies**</span><span class="sxs-lookup"><span data-stu-id="b94f6-124">**sys.sql_expression_dependencies**</span></span>  
 <span data-ttu-id="b94f6-125">要求对数据库具有 VIEW DEFINITION 权限，并对数据库的 **sys.sql_expression_dependencies** 具有 SELECT 权限。</span><span class="sxs-lookup"><span data-stu-id="b94f6-125">Requires VIEW DEFINITION permission on the database and SELECT permission on **sys.sql_expression_dependencies** for the database.</span></span> <span data-ttu-id="b94f6-126">默认情况下，SELECT 权限仅授予 **db_owner** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="b94f6-126">By default, SELECT permission is granted only to members of the **db_owner** fixed database role.</span></span> <span data-ttu-id="b94f6-127">将 SELECT 和 VIEW DEFINITION 权限授予其他用户时，被授权者可以查看数据库中的所有依赖关系。</span><span class="sxs-lookup"><span data-stu-id="b94f6-127">When SELECT and VIEW DEFINITION permissions are granted to another user, the grantee can view all dependencies in the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b94f6-128">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b94f6-128">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-definition-of-a-dml-trigger"></a><span data-ttu-id="b94f6-129">查看 DML 触发器的定义</span><span class="sxs-lookup"><span data-stu-id="b94f6-129">To view the definition of a DML trigger</span></span>  
  
1.  <span data-ttu-id="b94f6-130">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="b94f6-130">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="b94f6-131">展开您所需的数据库，再展开 **“表”** ，然后展开包含要查看其定义的触发器的表。</span><span class="sxs-lookup"><span data-stu-id="b94f6-131">Expand the database that you want, expand **Tables**, and then expand the table that contains the trigger for which you want to view the definition.</span></span>  
  
3.  <span data-ttu-id="b94f6-132">展开“触发器”，右键单击需要的触发器，然后单击“修改”。</span><span class="sxs-lookup"><span data-stu-id="b94f6-132">Expand **Triggers**, right-click the trigger you want, and then click **Modify**.</span></span> <span data-ttu-id="b94f6-133">将在查询窗口中显示 DML 触发器的定义。</span><span class="sxs-lookup"><span data-stu-id="b94f6-133">The definition of the DML trigger appears in the query window.</span></span>  
  
#### <a name="to-view-the-dependencies-of-a-dml-trigger"></a><span data-ttu-id="b94f6-134">查看 DML 触发器的依赖关系</span><span class="sxs-lookup"><span data-stu-id="b94f6-134">To view the dependencies of a DML trigger</span></span>  
  
1.  <span data-ttu-id="b94f6-135">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="b94f6-135">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="b94f6-136">展开您所需的数据库，再展开 **“表”** ，然后展开包含要查看的触发器及其依赖关系的表。</span><span class="sxs-lookup"><span data-stu-id="b94f6-136">Expand the database that you want, expand **Tables**, and then expand the table that contains the trigger and its dependencies that you want to view.</span></span>  
  
3.  <span data-ttu-id="b94f6-137">展开“触发器”，右键单击需要的触发器，然后单击“查看依赖关系”。</span><span class="sxs-lookup"><span data-stu-id="b94f6-137">Expand **Triggers**, right-click the trigger you want, and then click **View Dependencies**.</span></span>  
  
4.  <span data-ttu-id="b94f6-138">在“对象依赖关系”窗口中，若要查看依赖于 DML 触发器的对象，请选择“依赖于 \<DML trigger name> 的对象”。</span><span class="sxs-lookup"><span data-stu-id="b94f6-138">In the **Object Dependencies** window, to view the objects that depend on the DML trigger, select **Objects that depend on \<DML trigger name>**.</span></span> <span data-ttu-id="b94f6-139">将在 **“依赖关系”** 区域显示这些对象。</span><span class="sxs-lookup"><span data-stu-id="b94f6-139">The objects appear in the **Dependencies** area.</span></span>  
  
     <span data-ttu-id="b94f6-140">若要查看 DML 所依赖的对象，请选择“\<DML trigger name> 所依赖的对象”。</span><span class="sxs-lookup"><span data-stu-id="b94f6-140">To view the objects on which the DML depends, select **Objects on which \<DML trigger name> depends**.</span></span> <span data-ttu-id="b94f6-141">将在 **“依赖关系”** 区域显示这些对象。</span><span class="sxs-lookup"><span data-stu-id="b94f6-141">The objects appear in the **Dependencies** area.</span></span> <span data-ttu-id="b94f6-142">展开每个节点以查看所有对象。</span><span class="sxs-lookup"><span data-stu-id="b94f6-142">Expand each node to see all the objects.</span></span>  
  
5.  <span data-ttu-id="b94f6-143">若要获取有关 **“依赖关系”** 区域中显示的对象的信息，请单击该对象。</span><span class="sxs-lookup"><span data-stu-id="b94f6-143">To obtain information about an object that appears in the **Dependencies** area, click the object.</span></span> <span data-ttu-id="b94f6-144">在 **“所选对象”** 字段中，在 **“名称”** 、 **“类型”** 和 **“依赖关系类型”** 框中提供信息。</span><span class="sxs-lookup"><span data-stu-id="b94f6-144">In the **Selected object** field, information is provided in the **Name**, **Type**, and **Dependency type** boxes.</span></span>  
  
6.  <span data-ttu-id="b94f6-145">若要关闭 **“对象依赖关系”** 窗口，请单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="b94f6-145">To close the **Object Dependencies** window, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b94f6-146">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b94f6-146">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-definition-of-a-dml-trigger"></a><span data-ttu-id="b94f6-147">查看 DML 触发器的定义</span><span class="sxs-lookup"><span data-stu-id="b94f6-147">To view the definition of a DML trigger</span></span>  
  
1.  <span data-ttu-id="b94f6-148">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b94f6-148">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b94f6-149">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="b94f6-149">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b94f6-150">将以下示例之一复制并粘贴到查询窗口中，然后单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="b94f6-150">Copy and paste one of the following examples into the query window and click **Execute**.</span></span> <span data-ttu-id="b94f6-151">每个示例显示您如何查看 `iuPerson` 触发器的定义。</span><span class="sxs-lookup"><span data-stu-id="b94f6-151">Each example shows how you can view the definition of the `iuPerson` trigger.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT definition   
FROM sys.sql_modules  
WHERE object_id = OBJECT_ID(N'Person.iuPerson');   
GO  
```  
  
```sql  
USE AdventureWorks2012;   
GO  
SELECT OBJECT_DEFINITION (OBJECT_ID(N'Person.iuPerson')) AS ObjectDefinition;   
GO  
  
```  
  
```sql  
USE AdventureWorks2012;   
GO  
EXEC sp_helptext 'Person.iuPerson'  
GO  
  
```  
  
#### <a name="to-view-the-dependencies-of-a-dml-trigger"></a><span data-ttu-id="b94f6-152">查看 DML 触发器的依赖关系</span><span class="sxs-lookup"><span data-stu-id="b94f6-152">To view the dependencies of a DML trigger</span></span>  
  
1.  <span data-ttu-id="b94f6-153">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b94f6-153">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b94f6-154">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="b94f6-154">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b94f6-155">将以下示例之一复制并粘贴到查询窗口中，然后单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="b94f6-155">Copy and paste one of the following examples into the query window and click **Execute**.</span></span> <span data-ttu-id="b94f6-156">每个示例显示您如何查看 `iuPerson` 触发器的依赖关系。</span><span class="sxs-lookup"><span data-stu-id="b94f6-156">Each example shows how you can view the dependencies of `iuPerson` trigger.</span></span>  
  
```  
USE AdventureWorks2012;   
GO  
SELECT OBJECT_NAME(referencing_id) AS referencing_entity_name,   
    o.type_desc AS referencing_desciption,   
    COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
    referencing_class_desc, referenced_class_desc,   
    referenced_server_name, referenced_database_name, referenced_schema_name,   
    referenced_entity_name,   
    COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,   
    is_caller_dependent, is_ambiguous  
FROM sys.sql_expression_dependencies AS sed  
INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
WHERE referencing_id = OBJECT_ID(N'Person.iuPerson');   
GO  
  
```  
  
#### <a name="to-view-information-about-dml-triggers-in-the-database"></a><span data-ttu-id="b94f6-157">查看有关数据库中的 DML 触发器的信息</span><span class="sxs-lookup"><span data-stu-id="b94f6-157">To view information about DML triggers in the database</span></span>  
  
1.  <span data-ttu-id="b94f6-158">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b94f6-158">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b94f6-159">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="b94f6-159">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b94f6-160">将以下示例之一复制并粘贴到查询窗口中，然后单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="b94f6-160">Copy and paste one of the following examples into the query window and click **Execute**.</span></span> <span data-ttu-id="b94f6-161">每个示例显示您如何查看数据库中有关 DML 触发器 (`TR`) 的信息。</span><span class="sxs-lookup"><span data-stu-id="b94f6-161">Each example shows how you can view information about DML triggers (`TR`) in the database.</span></span>  
  
```  
USE AdventureWorks2012;   
GO  
SELECT  name, parent_id, create_date, modify_date, is_instead_of_trigger  
FROM sys.triggers  
WHERE type = 'TR';   
GO  
  
```  
  
```sql  
USE AdventureWorks2012;   
GO  
SELECT  name, object_id, schema_id, parent_object_id, type_desc, create_date, modify_date, is_published  
FROM sys.objects  
WHERE type = 'TR';   
GO  
  
```  
  
```sql  
USE AdventureWorks2012;   
GO  
SELECT OBJECTPROPERTY(OBJECT_ID(N'Person.iuPerson'), 'ExecIsInsteadOfTrigger');   
GO  
  
```  
  
#### <a name="to-view-information-about-events-that-fire-a-dml-trigger"></a><span data-ttu-id="b94f6-162">查看有关激发 DML 触发器的事件的信息</span><span class="sxs-lookup"><span data-stu-id="b94f6-162">To view information about events that fire a DML trigger</span></span>  
  
1.  <span data-ttu-id="b94f6-163">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b94f6-163">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b94f6-164">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="b94f6-164">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b94f6-165">将以下示例之一复制并粘贴到查询窗口中，然后单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="b94f6-165">Copy and paste one of the following examples into the query window and click **Execute**.</span></span> <span data-ttu-id="b94f6-166">每个示例显示如何查看激发 `iuPerson` 触发器的事件。</span><span class="sxs-lookup"><span data-stu-id="b94f6-166">Each example shows how you can view the events that fire the `iuPerson` trigger.</span></span>  
  
```sql  
USE AdventureWorks2012;   
GO  
SELECT object_id, type, type_desc, is_trigger_event, event_group_type, event_group_type_desc   
FROM sys.events  
WHERE object_id = OBJECT_ID('Person.iuPerson');   
GO  
```  
  
```sql  
USE AdventureWorks2012;   
GO   
SELECT object_id, type,is_first, is_last  
FROM sys.trigger_events  
WHERE object_id = OBJECT_ID('Person.iuPerson');   
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="b94f6-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b94f6-167">See Also</span></span>  
 <span data-ttu-id="b94f6-168">[CREATE TRIGGER (Transact-SQL)](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b94f6-168">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 <span data-ttu-id="b94f6-169">[DROP TRIGGER (Transact-SQL)](/sql/t-sql/statements/drop-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b94f6-169">[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span></span>  
 <span data-ttu-id="b94f6-170">[ENABLE TRIGGER (Transact-SQL)](/sql/t-sql/statements/enable-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b94f6-170">[ENABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/enable-trigger-transact-sql) </span></span>  
 <span data-ttu-id="b94f6-171">[DISABLE TRIGGER (Transact-SQL)](/sql/t-sql/statements/disable-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b94f6-171">[DISABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/disable-trigger-transact-sql) </span></span>  
 <span data-ttu-id="b94f6-172">[EVENTDATA (Transact-SQL)](/sql/t-sql/functions/eventdata-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b94f6-172">[EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql) </span></span>  
 <span data-ttu-id="b94f6-173">[sp_rename (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b94f6-173">[sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql) </span></span>  
 <span data-ttu-id="b94f6-174">[ALTER TRIGGER (Transact-SQL)](/sql/t-sql/statements/alter-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b94f6-174">[ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) </span></span>  
 <span data-ttu-id="b94f6-175">[sp_help (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b94f6-175">[sp_help &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql) </span></span>  
 <span data-ttu-id="b94f6-176">[sp_helptrigger (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b94f6-176">[sp_helptrigger &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql) </span></span>  
 <span data-ttu-id="b94f6-177">[sys.triggers (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b94f6-177">[sys.triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) </span></span>  
 <span data-ttu-id="b94f6-178">[sys.trigger_events (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b94f6-178">[sys.trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql) </span></span>  
 <span data-ttu-id="b94f6-179">[sys.sql_modules (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b94f6-179">[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span></span>  
 <span data-ttu-id="b94f6-180">[sys.assembly_modules (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b94f6-180">[sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql) </span></span>  
 <span data-ttu-id="b94f6-181">[sys.server_triggers (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b94f6-181">[sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) </span></span>  
 <span data-ttu-id="b94f6-182">[sys.server_trigger_events (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b94f6-182">[sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql) </span></span>  
 <span data-ttu-id="b94f6-183">[sys.server_sql_modules (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b94f6-183">[sys.server_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql) </span></span>  
 <span data-ttu-id="b94f6-184">[sys.server_assembly_modules (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b94f6-184">[sys.server_assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql) </span></span>  
 <span data-ttu-id="b94f6-185">[OBJECTPROPERTY (Transact-SQL)](/sql/t-sql/functions/objectpropertyex-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b94f6-185">[OBJECTPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectpropertyex-transact-sql) </span></span>  
 [<span data-ttu-id="b94f6-186">OBJECT_DEFINITION (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b94f6-186">OBJECT_DEFINITION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/object-definition-transact-sql)  
  
  
