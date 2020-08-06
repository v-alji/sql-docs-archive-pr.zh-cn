---
title: DDL 触发器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- DDL triggers, about DDL triggers
ms.assetid: 1a4a6564-9820-4a14-9305-2c0e9ea37454
author: rothja
ms.author: jroth
ms.openlocfilehash: 6cbcc9f1efc477b8c54ad131f9efa9ff49cc5845
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590631"
---
# <a name="ddl-triggers"></a><span data-ttu-id="61533-102">DDL 触发器</span><span class="sxs-lookup"><span data-stu-id="61533-102">DDL Triggers</span></span>
  <span data-ttu-id="61533-103">DDL 触发器将激发，以响应各种数据定义语言 (DDL) 事件。</span><span class="sxs-lookup"><span data-stu-id="61533-103">DDL triggers fire in response to a variety of Data Definition Language (DDL) events.</span></span> <span data-ttu-id="61533-104">这些事件主要与以关键字 CREATE、ALTER、DROP、GRANT、DENY、REVOKE 或 UPDATE STATISTICS 开头的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句对应。</span><span class="sxs-lookup"><span data-stu-id="61533-104">These events primarily correspond to [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that start with the keywords CREATE, ALTER, DROP, GRANT, DENY, REVOKE or UPDATE STATISTICS.</span></span> <span data-ttu-id="61533-105">执行 DDL 式操作的系统存储过程也可以激发 DDL 触发器。</span><span class="sxs-lookup"><span data-stu-id="61533-105">Certain system stored procedures that perform DDL-like operations can also fire DDL triggers.</span></span>  
  
 <span data-ttu-id="61533-106">如果要执行以下操作，请使用 DDL 触发器：</span><span class="sxs-lookup"><span data-stu-id="61533-106">Use DDL triggers when you want to do the following:</span></span>  
  
-   <span data-ttu-id="61533-107">防止对数据库架构进行某些更改。</span><span class="sxs-lookup"><span data-stu-id="61533-107">Prevent certain changes to your database schema.</span></span>  
  
-   <span data-ttu-id="61533-108">希望数据库中发生某种情况以响应数据库架构的更改。</span><span class="sxs-lookup"><span data-stu-id="61533-108">Have something occur in the database in response to a change in your database schema.</span></span>  
  
-   <span data-ttu-id="61533-109">记录数据库架构的更改或事件。</span><span class="sxs-lookup"><span data-stu-id="61533-109">Record changes or events in the database schema.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="61533-110">测试您的 DDL 触发器以确定它们是否响应运行的系统存储过程。</span><span class="sxs-lookup"><span data-stu-id="61533-110">Test your DDL triggers to determine their responses to system stored procedures that are run.</span></span> <span data-ttu-id="61533-111">例如，CREATE TYPE 语句和 **sp_addtype** 存储过程都将激发针对 CREATE_TYPE 事件创建的 DDL 触发器。</span><span class="sxs-lookup"><span data-stu-id="61533-111">For example, the CREATE TYPE statement and the **sp_addtype** stored procedure will both fire a DDL trigger that is created on a CREATE_TYPE event.</span></span>  
  
## <a name="types-of-ddl-triggers"></a><span data-ttu-id="61533-112">DDL 触发器的类型</span><span class="sxs-lookup"><span data-stu-id="61533-112">Types of DDL Triggers</span></span>  
 <span data-ttu-id="61533-113">Transact-SQL DDL 触发器</span><span class="sxs-lookup"><span data-stu-id="61533-113">Transact-SQL DDL Trigger</span></span>  
 <span data-ttu-id="61533-114">用于执行一个或多个 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句以响应服务器范围或数据库范围事件的一种特殊类型的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程。</span><span class="sxs-lookup"><span data-stu-id="61533-114">A special type of [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure that executes one or more [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in response to a server-scoped or database-scoped event.</span></span> <span data-ttu-id="61533-115">例如，如果执行某个语句（如 ALTER SERVER CONFIGURATION）或者使用 DROP TABLE 删除某个表，则激发 DDL 触发器。</span><span class="sxs-lookup"><span data-stu-id="61533-115">For example, a DDL Trigger may fire if a statement such as ALTER SERVER CONFIGURATION is executed or if a table is deleted by using DROP TABLE.</span></span>  
  
 <span data-ttu-id="61533-116">CLR DDL 触发器</span><span class="sxs-lookup"><span data-stu-id="61533-116">CLR DDL Trigger</span></span>  
 <span data-ttu-id="61533-117">CLR 触发器将执行在托管代码（在 .NET Framework 中创建并在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中上载的程序集的成员）中编写的方法，而不用执行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]存储过程。</span><span class="sxs-lookup"><span data-stu-id="61533-117">Instead of executing a [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure, a CLR trigger executes one or more methods written in managed code that are members of an assembly created in the .NET Framework and uploaded in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="61533-118">仅在运行触发 DDL 触发器的 DDL 语句后，DDL 触发器才会激发。</span><span class="sxs-lookup"><span data-stu-id="61533-118">DDL triggers fire only after the DDL statements that trigger them are run.</span></span> <span data-ttu-id="61533-119">DDL 触发器无法作为 INSTEAD OF 触发器使用。</span><span class="sxs-lookup"><span data-stu-id="61533-119">DDL triggers cannot be used as INSTEAD OF triggers.</span></span> <span data-ttu-id="61533-120">对于影响局部或全局临时表和存储过程的事件，不会触发 DDL 触发器。</span><span class="sxs-lookup"><span data-stu-id="61533-120">DDL triggers do not fire in response to events that affect local or global temporary tables and stored procedures.</span></span>  
  
 <span data-ttu-id="61533-121">DDL 触发器不会创建特殊的 `inserted` 和 `deleted` 表。</span><span class="sxs-lookup"><span data-stu-id="61533-121">DDL triggers do not create the special `inserted` and `deleted` tables.</span></span>  
  
 <span data-ttu-id="61533-122">可以使用 EVENTDATA 函数捕获有关激发 DDL 触发器的事件以及触发器导致的后续更改的信息。</span><span class="sxs-lookup"><span data-stu-id="61533-122">The information about an event that fires a DDL trigger, and the subsequent changes caused by the trigger, is captured by using the EVENTDATA function.</span></span>  
  
 <span data-ttu-id="61533-123">为每个 DDL 事件创建多个触发器。</span><span class="sxs-lookup"><span data-stu-id="61533-123">Multiple triggers to be created for each DDL event.</span></span>  
  
 <span data-ttu-id="61533-124">与 DML 触发器不同，DDL 触发器的作用域不是架构。</span><span class="sxs-lookup"><span data-stu-id="61533-124">Unlike DML triggers, DDL triggers are not scoped to schemas.</span></span> <span data-ttu-id="61533-125">因此，不能将 OBJECT_ID、OBJECT_NAME、OBJECTPROPERTY 和 OBJECTPROPERTYEX 之类的函数用于查询有关 DDL 触发器的元数据。</span><span class="sxs-lookup"><span data-stu-id="61533-125">Therefore, functions such as OBJECT_ID, OBJECT_NAME, OBJECTPROPERTY, and OBJECTPROPERTYEX cannot be used for querying metadata about DDL triggers.</span></span> <span data-ttu-id="61533-126">请改用目录视图。</span><span class="sxs-lookup"><span data-stu-id="61533-126">Use the catalog views instead.</span></span>  
  
 <span data-ttu-id="61533-127">服务器范围的 DDL 触发器显示在 SQL Server Management Studio 对象资源管理器的“触发器”  文件夹中。</span><span class="sxs-lookup"><span data-stu-id="61533-127">Server-scoped DDL triggers appear in the SQL Server Management Studio Object Explorer in the **Triggers** folder.</span></span> <span data-ttu-id="61533-128">此文件夹位于 **“服务器对象”** 文件夹下。</span><span class="sxs-lookup"><span data-stu-id="61533-128">This folder is located under the **Server Objects** folder.</span></span> <span data-ttu-id="61533-129">数据库范围的 DDL 触发器显示在“数据库触发器”  文件夹中。</span><span class="sxs-lookup"><span data-stu-id="61533-129">Database-scoped DDL triggers appear in the **Database Triggers** folder.</span></span> <span data-ttu-id="61533-130">此文件夹位于相应数据库的 **“可编程性”** 文件夹下。</span><span class="sxs-lookup"><span data-stu-id="61533-130">This folder is located under the **Programmability** folder of the corresponding database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="61533-131">触发器内部的恶意代码可以在升级后的权限下运行。</span><span class="sxs-lookup"><span data-stu-id="61533-131">Malicious code inside triggers can run under escalated privileges.</span></span> <span data-ttu-id="61533-132">有关如何帮助减少此威胁的详细信息，请参阅 [管理触发器安全](manage-trigger-security.md)。</span><span class="sxs-lookup"><span data-stu-id="61533-132">For more information about how to help reduce this threat, see [Manage Trigger Security](manage-trigger-security.md).</span></span>  
  
## <a name="ddl-trigger-scope"></a><span data-ttu-id="61533-133">DDL 触发器作用域</span><span class="sxs-lookup"><span data-stu-id="61533-133">DDL Trigger Scope</span></span>  
 <span data-ttu-id="61533-134">在响应当前数据库或服务器上处理的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 事件时，可以触发 DDL 触发器。</span><span class="sxs-lookup"><span data-stu-id="61533-134">DDL triggers can fire in response to a [!INCLUDE[tsql](../../includes/tsql-md.md)] event processed in the current database, or on the current server.</span></span> <span data-ttu-id="61533-135">触发器的作用域取决于事件。</span><span class="sxs-lookup"><span data-stu-id="61533-135">The scope of the trigger depends on the event.</span></span> <span data-ttu-id="61533-136">例如，每当数据库中或服务器实例上发生 CREATE_TABLE 事件时，都会激发为响应 CREATE_TABLE 事件创建的 DDL 触发器。</span><span class="sxs-lookup"><span data-stu-id="61533-136">For example, a DDL trigger created to fire in response to a CREATE_TABLE event can do so whenever a CREATE_TABLE event occurs in the database, or on the server instance.</span></span> <span data-ttu-id="61533-137">仅当服务器实例上发生 CREATE_LOGIN 事件时，才能激发为响应 CREATE_LOGIN 事件创建的 DDL 触发器。</span><span class="sxs-lookup"><span data-stu-id="61533-137">A DDL trigger created to fire in response to a CREATE_LOGIN event can do so only when a CREATE_LOGIN event occurs in the server instance.</span></span>  
  
 <span data-ttu-id="61533-138">在下面的示例中，每当数据库中发生 `safety` 或 `DROP_TABLE` 事件时，都会激发 DDL 触发器 `ALTER_TABLE` 。</span><span class="sxs-lookup"><span data-stu-id="61533-138">In the following example, DDL trigger `safety` will fire whenever a `DROP_TABLE` or `ALTER_TABLE` event occurs in the database.</span></span>  
  
```  
CREATE TRIGGER safety   
ON DATABASE   
FOR DROP_TABLE, ALTER_TABLE   
AS   
   PRINT 'You must disable Trigger "safety" to drop or alter tables!'   
   ROLLBACK;  
```  
  
 <span data-ttu-id="61533-139">在下面的示例中，如果当前服务器实例上发生任何 `CREATE_DATABASE` 事件，DDL 触发器将输出消息。</span><span class="sxs-lookup"><span data-stu-id="61533-139">In the following example, a DDL trigger prints a message if any `CREATE_DATABASE` event occurs on the current server instance.</span></span> <span data-ttu-id="61533-140">此示例使用 `EVENTDATA` 函数检索相应的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的文本。</span><span class="sxs-lookup"><span data-stu-id="61533-140">The example uses the `EVENTDATA` function to retrieve the text of the corresponding [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="61533-141">有关如何将 EVENTDATA 与 DDL 触发器配合使用的详细信息，请参阅 [使用 EVENTDATA 函数](use-the-eventdata-function.md)。</span><span class="sxs-lookup"><span data-stu-id="61533-141">For more information about how to use EVENTDATA with DDL triggers, see [Use the EVENTDATA Function](use-the-eventdata-function.md).</span></span>  
  
```  
IF EXISTS (SELECT * FROM sys.server_triggers  
    WHERE name = 'ddl_trig_database')  
DROP TRIGGER ddl_trig_database  
ON ALL SERVER;  
GO  
CREATE TRIGGER ddl_trig_database   
ON ALL SERVER   
FOR CREATE_DATABASE   
AS   
    PRINT 'Database Created.'  
    SELECT EVENTDATA().value('(/EVENT_INSTANCE/TSQLCommand/CommandText)[1]','nvarchar(max)')  
GO  
DROP TRIGGER ddl_trig_database  
ON ALL SERVER;  
GO  
  
```  
  
 <span data-ttu-id="61533-142">本主题后面的“选择触发 DDL 触发器的特定 DDL 语句”一部分中提供了一些链接，通过这些链接可以找到将 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句映射到为它们指定的作用域的列表。</span><span class="sxs-lookup"><span data-stu-id="61533-142">The lists that map the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements to the scopes that can be specified for them are available through the links provided in the section "Selecting a Particular DDL Statement to Fire a DDL Trigger," later in this topic.</span></span>  
  
 <span data-ttu-id="61533-143">数据库范围内的 DDL 触发器都作为对象存储在创建它们的数据库中。</span><span class="sxs-lookup"><span data-stu-id="61533-143">Database-scoped DDL triggers are stored as objects in the database in which they are created.</span></span> <span data-ttu-id="61533-144">可以在 **master** 数据库中创建 DDL 触发器，这些触发器的行为与在用户设计的数据库中创建的 DDL 触发器的行为类似。</span><span class="sxs-lookup"><span data-stu-id="61533-144">DDL triggers can be created in the **master** database and behave just like those created in user-designed databases.</span></span> <span data-ttu-id="61533-145">可以通过查询 **sys.triggers** 目录视图获取有关 DDL 触发器的信息。</span><span class="sxs-lookup"><span data-stu-id="61533-145">You can obtain information about DDL triggers by querying the **sys.triggers** catalog view.</span></span> <span data-ttu-id="61533-146">可以在创建触发器的数据库上下文中或通过指定数据库名称作为标识符（例如 **master.sys.triggers** ），查询 **sys.triggers**。</span><span class="sxs-lookup"><span data-stu-id="61533-146">You can query **sys.triggers** within the database context in which the triggers are created or by specifying the database name as an identifier, such as **master.sys.triggers**.</span></span>  
  
 <span data-ttu-id="61533-147">服务器范围内的 DDL 触发器作为对象存储在 **master** 数据库中。</span><span class="sxs-lookup"><span data-stu-id="61533-147">Server-scoped DDL triggers are stored as objects in the **master** database.</span></span> <span data-ttu-id="61533-148">然而，可以通过在任何数据库上下文中查询 **sys.server_triggers** 目录视图，获取有关服务器范围内的 DDL 触发器的信息。</span><span class="sxs-lookup"><span data-stu-id="61533-148">However, you can obtain information about server-scoped DDL triggers by querying the **sys.server_triggers** catalog view in any database context.</span></span>  
  
## <a name="specifying-a-transact-sql-statement-or-group-of-statements"></a><span data-ttu-id="61533-149">指定 Transact-SQL 语句或语句组</span><span class="sxs-lookup"><span data-stu-id="61533-149">Specifying a Transact-SQL Statement or Group of Statements</span></span>  
  
### <a name="selecting-a-particular-ddl-statement-to-fire-a-ddl-trigger"></a><span data-ttu-id="61533-150">选择触发 DDL 触发器的特定 DDL 语句</span><span class="sxs-lookup"><span data-stu-id="61533-150">Selecting a Particular DDL Statement to Fire a DDL Trigger</span></span>  
 <span data-ttu-id="61533-151">可以安排在运行一个或多个特定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句后触发 DDL 触发器。</span><span class="sxs-lookup"><span data-stu-id="61533-151">DDL triggers can be designed to fire after one or more particular [!INCLUDE[tsql](../../includes/tsql-md.md)] statements are run.</span></span> <span data-ttu-id="61533-152">在前面的示例中，在发生任何 `safety` 或 `DROP_TABLE` 事件后触发 `ALTER_TABLE` 触发器。</span><span class="sxs-lookup"><span data-stu-id="61533-152">In the previous example, trigger `safety` fires after any `DROP_TABLE` or `ALTER_TABLE` event.</span></span> <span data-ttu-id="61533-153">有关可指定激发 DDL 触发器的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的列表，请参阅 [DDL 事件](ddl-events.md)。</span><span class="sxs-lookup"><span data-stu-id="61533-153">For lists of the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that can be specified to fire a DDL trigger, and the scope at which the trigger can fire, see [DDL Events](ddl-events.md).</span></span>  
  
### <a name="selecting-a-predefined-group-of-ddl-statements-to-fire-a-ddl-trigger"></a><span data-ttu-id="61533-154">选择触发 DDL 触发器的一组预定义的 DDL 语句</span><span class="sxs-lookup"><span data-stu-id="61533-154">Selecting a Predefined Group of DDL Statements to Fire a DDL Trigger</span></span>  
 <span data-ttu-id="61533-155">可以在执行属于一组预定义的相似事件的任何 [!INCLUDE[tsql](../../includes/tsql-md.md)] 事件后激发 DDL 触发器。</span><span class="sxs-lookup"><span data-stu-id="61533-155">A DDL trigger can fire after execution of any [!INCLUDE[tsql](../../includes/tsql-md.md)] event that belongs to a predefined grouping of similar events.</span></span> <span data-ttu-id="61533-156">例如，如果希望在运行 CREATE TABLE、ALTER TABLE 或 DROP TABLE 语句后触发 DDL 触发器，则可以在 CREATE TRIGGER 语句中指定 FOR DDL_TABLE_EVENTS。</span><span class="sxs-lookup"><span data-stu-id="61533-156">For example, if you want a DDL trigger to fire after any CREATE TABLE, ALTER TABLE, or DROP TABLE statement is run, you can specify FOR DDL_TABLE_EVENTS in the CREATE TRIGGER statement.</span></span> <span data-ttu-id="61533-157">运行 CREATE TRIGGER 后，事件组涵盖的事件都添加到 **sys.trigger_events** 目录视图中。</span><span class="sxs-lookup"><span data-stu-id="61533-157">After CREATE TRIGGER is run, the events that are covered by an event group are added to the **sys.trigger_events** catalog view.</span></span>  
  
 <span data-ttu-id="61533-158">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]中，如果对事件组创建触发器，则 **sys.trigger_events** 不包括有关该事件组的信息，而 **sys.trigger_events** 仅包括有关该组涵盖的个别事件的信息。</span><span class="sxs-lookup"><span data-stu-id="61533-158">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], if a trigger is created on an event group, **sys.trigger_events** does not include information about the event group, **sys.trigger_events** includes information only about the individual events covered by that group.</span></span> <span data-ttu-id="61533-159">在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 和更高版本中， **sys.trigger_events** 保留有关创建触发器的事件组的元数据，以及有关该事件组涵盖的个别事件的元数据。</span><span class="sxs-lookup"><span data-stu-id="61533-159">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and higher, **sys.trigger_events** persists metadata about the event group on which the triggers is created, and also about the individual events that the event group covers.</span></span> <span data-ttu-id="61533-160">因此，对 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 和更高版本中事件组所涵盖的事件的更改并不适用于在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]中对这些事件组创建的 DDL 触发器。</span><span class="sxs-lookup"><span data-stu-id="61533-160">Therefore, changes to the events that are covered by event groups in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and higher do not apply to DDL triggers that are created on those event groups in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="61533-161">有关可用于 DDL 触发器的预定义 DDL 语句组、事件组所涵盖的特定语句以及可以对这些事件组进行编程的作用域的列表，请参阅 [DDL Event Groups](ddl-event-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="61533-161">For a list of the predefined groups of DDL statements that are available for DDL triggers, the particular statements the event groups cover, and the scopes at which these event groups can be programmed, see [DDL Event Groups](ddl-event-groups.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="61533-162">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="61533-162">Related Tasks</span></span>  
  
|<span data-ttu-id="61533-163">任务</span><span class="sxs-lookup"><span data-stu-id="61533-163">Task</span></span>|<span data-ttu-id="61533-164">主题</span><span class="sxs-lookup"><span data-stu-id="61533-164">Topic</span></span>|  
|----------|-----------|  
|<span data-ttu-id="61533-165">说明如何创建、修改、删除或禁用 DDL 触发器。</span><span class="sxs-lookup"><span data-stu-id="61533-165">Describes how to create, modify, delete or disable DDL triggers.</span></span>|[<span data-ttu-id="61533-166">实现 DDL 触发器</span><span class="sxs-lookup"><span data-stu-id="61533-166">Implement DDL Triggers</span></span>](implement-ddl-triggers.md)|  
|<span data-ttu-id="61533-167">说明如何创建 CLR DDL 触发器。</span><span class="sxs-lookup"><span data-stu-id="61533-167">Describes how to create a CLR DDL trigger.</span></span>|[<span data-ttu-id="61533-168">创建 CLR 触发器</span><span class="sxs-lookup"><span data-stu-id="61533-168">Create CLR Triggers</span></span>](create-clr-triggers.md)|  
|<span data-ttu-id="61533-169">说明如何返回有关 DDL 触发器的信息。</span><span class="sxs-lookup"><span data-stu-id="61533-169">Describes how to return information about DDL triggers.</span></span>|[<span data-ttu-id="61533-170">获取有关 DDL 触发器的信息</span><span class="sxs-lookup"><span data-stu-id="61533-170">Get Information About DDL Triggers</span></span>](get-information-about-ddl-triggers.md)|  
|<span data-ttu-id="61533-171">说明如何返回有关使用 EVENTDATA 函数激发 DDL 触发器的事件的信息。</span><span class="sxs-lookup"><span data-stu-id="61533-171">Describes how to return information about an event that fires a DDL trigger by using the EVENTDATA function.</span></span>|[<span data-ttu-id="61533-172">使用 EVENTDATA 函数</span><span class="sxs-lookup"><span data-stu-id="61533-172">Use the EVENTDATA Function</span></span>](use-the-eventdata-function.md)|  
|<span data-ttu-id="61533-173">说明如何管理触发器安全性。</span><span class="sxs-lookup"><span data-stu-id="61533-173">Describes how to manage trigger security.</span></span>|[<span data-ttu-id="61533-174">管理触发器安全性</span><span class="sxs-lookup"><span data-stu-id="61533-174">Manage Trigger Security</span></span>](manage-trigger-security.md)|  
  
## <a name="see-also"></a><span data-ttu-id="61533-175">另请参阅</span><span class="sxs-lookup"><span data-stu-id="61533-175">See Also</span></span>  
 <span data-ttu-id="61533-176">[DML 触发器](dml-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="61533-176">[DML Triggers](dml-triggers.md) </span></span>  
 <span data-ttu-id="61533-177">[登录触发器](logon-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="61533-177">[Logon Triggers](logon-triggers.md) </span></span>  
 [<span data-ttu-id="61533-178">CREATE TRIGGER (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61533-178">CREATE TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-trigger-transact-sql)  
  
  
