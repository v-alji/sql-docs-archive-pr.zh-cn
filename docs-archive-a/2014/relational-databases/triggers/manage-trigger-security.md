---
title: 管理触发器安全性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- triggers [SQL Server], security
ms.assetid: e94720a8-a3a2-4364-b0a3-bbe86e3ce4d5
author: rothja
ms.author: jroth
ms.openlocfilehash: fdc176dcad50c3bf28f058c3724a01267975bfc5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590616"
---
# <a name="manage-trigger-security"></a><span data-ttu-id="1b131-102">管理触发器安全性</span><span class="sxs-lookup"><span data-stu-id="1b131-102">Manage Trigger Security</span></span>
  <span data-ttu-id="1b131-103">默认情况下，在调用触发器的用户的上下文中执行 DML 和 DDL 触发器。</span><span class="sxs-lookup"><span data-stu-id="1b131-103">By default, both DML and DDL triggers execute under the context of the user that calls the trigger.</span></span> <span data-ttu-id="1b131-104">触发器的调用方是执行使触发器运行的语句的用户。</span><span class="sxs-lookup"><span data-stu-id="1b131-104">The caller of a trigger is the user that executes the statement that causes the trigger to run.</span></span> <span data-ttu-id="1b131-105">例如，如果用户 **Mary** 执行可以使 DML 触发器 **DML_trigMary** 运行的 DELETE 语句，则 **DML_trigMary** 中的代码将在 **Mary**的用户特权上下文中执行。</span><span class="sxs-lookup"><span data-stu-id="1b131-105">For example, if user **Mary** executes a DELETE statement that causes DML trigger **DML_trigMary** to run, the code inside **DML_trigMary** executes in the context of the user privileges for **Mary**.</span></span> <span data-ttu-id="1b131-106">希望向数据库或服务器实例中引入恶意代码的用户可以使用此默认行为。</span><span class="sxs-lookup"><span data-stu-id="1b131-106">This default behavior can be exploited by users who want to introduce malicious code in the database or server instance.</span></span> <span data-ttu-id="1b131-107">例如，用户 `JohnDoe`创建以下 DDL 触发器：</span><span class="sxs-lookup"><span data-stu-id="1b131-107">For example, the following DDL trigger is created by user `JohnDoe`:</span></span>  
  
 `CREATE TRIGGER DDL_trigJohnDoe`  
  
 `ON DATABASE`  
  
 `FOR ALTER_TABLE`  
  
 `AS`  
  
 `GRANT CONTROL SERVER TO JohnDoe ;`  
  
 `GO`  
  
 <span data-ttu-id="1b131-108">此触发器的含义是：在有权执行 `GRANT CONTROL SERVER` 语句的用户（如 **sysadmin** 固定服务器角色的成员）执行 `ALTER TABLE` 语句时，为 `JohnDoe` 授予 `CONTROL SERVER` 权限。</span><span class="sxs-lookup"><span data-stu-id="1b131-108">What this trigger means is that as soon as a user that has permission to execute a `GRANT CONTROL SERVER` statement, such as a member of the **sysadmin** fixed server role, executes an `ALTER TABLE` statement, `JohnDoe` is granted `CONTROL SERVER` permission.</span></span> <span data-ttu-id="1b131-109">换言之，虽然 `JohnDoe` 不能为自己授予 `CONTROL SERVER` 权限，但是他启用了授予他此权限的触发器代码以在升级特权下执行。</span><span class="sxs-lookup"><span data-stu-id="1b131-109">In other words, although `JohnDoe` cannot grant `CONTROL SERVER` permission to himself, he enabled the trigger code that grants him this permission to execute under escalated privileges.</span></span> <span data-ttu-id="1b131-110">对于此类安全隐患，DML 和 DDL 触发器都处于打开状态。</span><span class="sxs-lookup"><span data-stu-id="1b131-110">Both DML and DDL triggers are open to this kind of security threat.</span></span>  
  
## <a name="trigger-security-best-practices"></a><span data-ttu-id="1b131-111">保证触发器安全的最佳方法</span><span class="sxs-lookup"><span data-stu-id="1b131-111">Trigger Security Best Practices</span></span>  
 <span data-ttu-id="1b131-112">可以采取下列措施阻止触发器代码在升级特权下执行：</span><span class="sxs-lookup"><span data-stu-id="1b131-112">You can take the following measures to prevent trigger code from executing under escalated privileges:</span></span>  
  
-   <span data-ttu-id="1b131-113">注意数据库和服务器实例中存在的 DML 和 DDL 触发器，方法是查询 [sys.triggers](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) 和 [sys.server_triggers](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) 目录视图。</span><span class="sxs-lookup"><span data-stu-id="1b131-113">Be aware of the DML and DDL triggers that exist in the database and on the server instance by querying the [sys.triggers](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) and [sys.server_triggers](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) catalog views.</span></span> <span data-ttu-id="1b131-114">下面的查询将返回当前数据库中的所有 DML 触发器和数据库级别的 DDL 触发器，以及服务器实例中所有服务器级别的 DDL 触发器：</span><span class="sxs-lookup"><span data-stu-id="1b131-114">The following query returns all DML and database-level DDL triggers in the current database, and all server-level DDL triggers on the server instance:</span></span>  
  
    ```  
    SELECT type, name, parent_class_desc FROM sys.triggers  
    UNION  
    SELECT type, name, parent_class_desc FROM sys.server_triggers ;  
    ```  
  
-   <span data-ttu-id="1b131-115">使用 [DISABLE TRIGGER](/sql/t-sql/statements/disable-trigger-transact-sql) 禁用在升级特权下执行时可能会损害数据库或服务器完整性的触发器。</span><span class="sxs-lookup"><span data-stu-id="1b131-115">Use [DISABLE TRIGGER](/sql/t-sql/statements/disable-trigger-transact-sql) to disable triggers that can harm the integrity of the database or server if the triggers execute under escalated privileges.</span></span> <span data-ttu-id="1b131-116">下面的语句可以禁用当前数据库中所有数据库级别的 DDL 触发器：</span><span class="sxs-lookup"><span data-stu-id="1b131-116">The following statement disables all database-level DDL triggers in the current database:</span></span>  
  
    ```  
    DISABLE TRIGGER ALL ON DATABASE  
    ```  
  
     <span data-ttu-id="1b131-117">下面的语句可以禁用服务器实例中所有服务器级别的 DDL 触发器：</span><span class="sxs-lookup"><span data-stu-id="1b131-117">This statement disables all server-level DDL triggers on the server instance:</span></span>  
  
    ```  
    DISABLE TRIGGER ALL ON ALL SERVER  
    ```  
  
     <span data-ttu-id="1b131-118">下面的语句可以禁用当前数据库中的所有 DML 触发器：</span><span class="sxs-lookup"><span data-stu-id="1b131-118">This statement disables all DML triggers in the current database:</span></span>  
  
    ```  
    DECLARE @schema_name sysname, @trigger_name sysname, @object_name sysname ;  
    DECLARE @sql nvarchar(max) ;  
    DECLARE trig_cur CURSOR FORWARD_ONLY READ_ONLY FOR  
        SELECT SCHEMA_NAME(schema_id) AS schema_name,  
            name AS trigger_name,  
            OBJECT_NAME(parent_object_id) as object_name  
        FROM sys.objects WHERE type in ('TR', 'TA') ;  
  
    OPEN trig_cur ;  
    FETCH NEXT FROM trig_cur INTO @schema_name, @trigger_name, @object_name ;  
  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
        SELECT @sql = 'DISABLE TRIGGER ' + QUOTENAME(@schema_name) + '.'  
            + QUOTENAME(@trigger_name) +  
            ' ON ' + QUOTENAME(@schema_name) + '.'   
            + QUOTENAME(@object_name) + ' ; ' ;  
        EXEC (@sql) ;  
        FETCH NEXT FROM trig_cur INTO @schema_name, @trigger_name, @object_name ;  
    END  
    GO  
  
    -- Verify triggers are disabled. Should return an empty result set.  
    SELECT * FROM sys.triggers WHERE is_disabled = 0 ;  
    GO  
  
    CLOSE trig_cur ;  
    DEALLOCATE trig_cur;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1b131-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1b131-119">See Also</span></span>  
 <span data-ttu-id="1b131-120">[CREATE TRIGGER (Transact-SQL)](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1b131-120">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 <span data-ttu-id="1b131-121">[DML 触发器](../triggers/dml-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="1b131-121">[DML Triggers](../triggers/dml-triggers.md) </span></span>  
 [<span data-ttu-id="1b131-122">DDL 触发器</span><span class="sxs-lookup"><span data-stu-id="1b131-122">DDL Triggers</span></span>](../triggers/ddl-triggers.md)  
  
  
