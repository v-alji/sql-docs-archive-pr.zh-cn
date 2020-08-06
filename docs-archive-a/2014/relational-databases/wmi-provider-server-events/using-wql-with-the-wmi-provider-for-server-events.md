---
title: 将 WQL 与 WMI Provider for Server Events 一起使用 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- queries [WMI]
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Server Events, WQL
ms.assetid: 58b67426-1e66-4445-8e2c-03182e94c4be
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: df2bbf5c6031781494695f95116441fde34bf4f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586537"
---
# <a name="using-wql-with-the-wmi-provider-for-server-events"></a><span data-ttu-id="c235c-102">将 WQL 与 WMI Provider for Server Events 结合使用</span><span class="sxs-lookup"><span data-stu-id="c235c-102">Using WQL with the WMI Provider for Server Events</span></span>
  <span data-ttu-id="c235c-103">管理应用程序通过发出 WMI 查询语言 (WQL) 语句来访问使用 WMI Provider for Server Events 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 事件。</span><span class="sxs-lookup"><span data-stu-id="c235c-103">Management applications access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events using the WMI Provider for Server Events by issuing WMI Query Language (WQL) statements.</span></span> <span data-ttu-id="c235c-104">WQL 是结构化查询语言 (SQL) 的简化子集，它还包含一些特定于 WMI 的扩展。</span><span class="sxs-lookup"><span data-stu-id="c235c-104">WQL is a simplified subset of structured query language (SQL), with some WMI-specific extensions.</span></span> <span data-ttu-id="c235c-105">当使用 WQL 时，应用程序将针对特定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例、数据库或数据库对象（当前唯一支持的对象为队列）来检索事件类型。</span><span class="sxs-lookup"><span data-stu-id="c235c-105">In using WQL, an application retrieves an event type against a specific instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a database, or a database object (the only object currently supported is queue).</span></span> <span data-ttu-id="c235c-106">用于服务器事件的 WMI 提供程序将查询转换为在数据库范围内或对象范围的事件通知的目标数据库中创建的事件通知，或在用于服务器范围内的事件通知的**master**数据库中创建的事件通知。</span><span class="sxs-lookup"><span data-stu-id="c235c-106">The WMI Provider for Server Events translates the query into an event notification that is created in the target database for database-scoped or object-scoped event notifications, or in the **master** database for server-scoped event notifications.</span></span>  
  
 <span data-ttu-id="c235c-107">例如，请考虑下列 WQL 查询：</span><span class="sxs-lookup"><span data-stu-id="c235c-107">For example, consider the following WQL query:</span></span>  
  
```  
SELECT * FROM DDL_DATABASE_LEVEL_EVENTS WHERE DatabaseName = 'AdventureWorks'  
```  
  
 <span data-ttu-id="c235c-108">在以下查询中，WMI 提供程序试图在目标服务器上生成此事件通知的等效项：</span><span class="sxs-lookup"><span data-stu-id="c235c-108">From this query, the WMI Provider tries to produce the equivalent of this event notification on the target server:</span></span>  
  
```  
USE AdventureWorks ;  
GO  
  
CREATE EVENT NOTIFICATION SQLWEP_76CF38C1_18BB_42DD_A7DC_C8820155B0E9  
    ON DATABASE  
    WITH FAN_IN  
    FOR DDL_DATABASE_LEVEL_EVENTS  
    TO SERVICE   
        'SQL/Notifications/ProcessWMIEventProviderNotification/v1.0',  
        'A7E5521A-1CA6-4741-865D-826F804E5135';  
GO  
```  
  
 <span data-ttu-id="c235c-109">WQL 查询 (`FROM`) 的 `DDL_DATABASE_LEVEL_EVENTS` 子句中的参数可以为可对其创建事件通知的任何有效事件。</span><span class="sxs-lookup"><span data-stu-id="c235c-109">The argument in the `FROM` clause of the WQL query (`DDL_DATABASE_LEVEL_EVENTS`) can be any valid event upon which an event notification can be created.</span></span> <span data-ttu-id="c235c-110">`SELECT` 和 `WHERE` 子句中的参数可以指定与某一事件或其父事件关联的任何事件属性。</span><span class="sxs-lookup"><span data-stu-id="c235c-110">The arguments in the `SELECT` and `WHERE` clauses can specify any event property associated with an event or its parent event.</span></span> <span data-ttu-id="c235c-111">有关有效事件和事件属性的列表，请参阅[ (数据库引擎) 的事件通知](https://technet.microsoft.com/library/ms182602.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c235c-111">For a list of valid events and event properties, see [Event Notifications (Database Engine)](https://technet.microsoft.com/library/ms182602.aspx).</span></span>  
  
 <span data-ttu-id="c235c-112">WMI Provider for Server Events 显式支持以下 WQL 语法。</span><span class="sxs-lookup"><span data-stu-id="c235c-112">The following WQL syntax is supported explicitly by the WMI Provider for Server Events.</span></span> <span data-ttu-id="c235c-113">也可以指定附加 WQL 语法，但该语法并非特定于此提供程序，并且由 WMI 主机服务进行分析。</span><span class="sxs-lookup"><span data-stu-id="c235c-113">Additional WQL syntax may be specified, but it is not specific to this provider and is parsed instead by the WMI host service.</span></span> <span data-ttu-id="c235c-114">有关 WMI 查询语言的详细信息，请参阅 Microsoft Developer Network (MSDN) 上的 WQL 文档。</span><span class="sxs-lookup"><span data-stu-id="c235c-114">For more information about the WMI Query Language, see the WQL documentation on the Microsoft Developer Network (MSDN).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c235c-115">语法</span><span class="sxs-lookup"><span data-stu-id="c235c-115">Syntax</span></span>  
  
```  
  
SELECT { event_property [ ,...n ] | * }  
FROM event_type   
WHERE where_condition  
```  
  
## <a name="arguments"></a><span data-ttu-id="c235c-116">参数</span><span class="sxs-lookup"><span data-stu-id="c235c-116">Arguments</span></span>  
 <span data-ttu-id="c235c-117">*event_property*</span><span class="sxs-lookup"><span data-stu-id="c235c-117">*event_property*</span></span>  
 <span data-ttu-id="c235c-118">事件的属性。</span><span class="sxs-lookup"><span data-stu-id="c235c-118">Is a property of an event.</span></span> <span data-ttu-id="c235c-119">示例包括 `PostTime`、`SPID` 和 `LoginName`。</span><span class="sxs-lookup"><span data-stu-id="c235c-119">Examples include `PostTime`, `SPID`, and `LoginName`.</span></span> <span data-ttu-id="c235c-120">查找[WMI Provider For Server Events 类和属性](wmi-provider-for-server-events-classes-and-properties.md)中列出的每个事件，以确定其包含的属性。</span><span class="sxs-lookup"><span data-stu-id="c235c-120">Look up each event listed in [WMI Provider for Server Events Classes and Properties](wmi-provider-for-server-events-classes-and-properties.md) to determine which properties it holds.</span></span> <span data-ttu-id="c235c-121">例如，DDL_DATABASE_LEVEL_EVENTS 事件具有 `DatabaseName` 和 `UserName` 属性。</span><span class="sxs-lookup"><span data-stu-id="c235c-121">For example, the DDL_DATABASE_LEVEL_EVENTS event holds the `DatabaseName` and `UserName` properties.</span></span> <span data-ttu-id="c235c-122">事件还从其父事件继承 `SQLInstance`、`LoginName`、`PostTime`、`SPID` 和 `ComputerName` 属性。</span><span class="sxs-lookup"><span data-stu-id="c235c-122">It also inherits the `SQLInstance`, `LoginName`, `PostTime`, `SPID`, and `ComputerName` properties from its parent events.</span></span>  
  
 <span data-ttu-id="c235c-123">**,** *...n*</span><span class="sxs-lookup"><span data-stu-id="c235c-123">**,** *...n*</span></span>  
 <span data-ttu-id="c235c-124">指示*event_property*可以查询多次，用逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="c235c-124">Indicates that *event_property* can be queried multiple times, separated by commas.</span></span>  
  
 \*  
 <span data-ttu-id="c235c-125">指定对与事件关联的所有属性进行查询。</span><span class="sxs-lookup"><span data-stu-id="c235c-125">Specifies that all properties associated with an event are queried.</span></span>  
  
 <span data-ttu-id="c235c-126">event_type</span><span class="sxs-lookup"><span data-stu-id="c235c-126">*event_type*</span></span>  
 <span data-ttu-id="c235c-127">可针对其创建事件通知的任何事件。</span><span class="sxs-lookup"><span data-stu-id="c235c-127">Is any event against which an event notification can be created.</span></span> <span data-ttu-id="c235c-128">有关可用事件的列表，请参阅[WMI Provider For Server Events 类和属性](https://technet.microsoft.com/library/ms186449.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c235c-128">For a list of available events, see [WMI Provider for Server Events Classes and Properties](https://technet.microsoft.com/library/ms186449.aspx).</span></span> <span data-ttu-id="c235c-129">请注意，*事件类型*名称对应于*event_type*  |  通过使用 create event notification 手动创建事件通知时可以指定的相同 event_type*event_group* 。</span><span class="sxs-lookup"><span data-stu-id="c235c-129">Note that *event type* names correspond to the same *event_type* | *event_group* that can be specified when you manually create an event notification by using CREATE EVENT NOTIFICATION.</span></span> <span data-ttu-id="c235c-130">*事件类型*的示例包括 CREATE_TABLE、LOCK_DEADLOCK、DDL_USER_EVENTS 和 TRC_DATABASE。</span><span class="sxs-lookup"><span data-stu-id="c235c-130">Examples of *event type* include CREATE_TABLE, LOCK_DEADLOCK, DDL_USER_EVENTS, and TRC_DATABASE.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c235c-131">执行 DDL 式操作的某些系统存储过程也可以激发事件通知。</span><span class="sxs-lookup"><span data-stu-id="c235c-131">Certain system stored procedures that perform DDL-like operations can also fire event notifications.</span></span> <span data-ttu-id="c235c-132">测试您的事件通知以确定它们是否响应运行的系统存储过程。</span><span class="sxs-lookup"><span data-stu-id="c235c-132">Test your event notifications to determine their responses to system stored procedures that are run.</span></span> <span data-ttu-id="c235c-133">例如，CREATE TYPE 语句和**sp_addtype**存储过程都将激发在 CREATE_TYPE 事件上创建的事件通知。</span><span class="sxs-lookup"><span data-stu-id="c235c-133">For example, the CREATE TYPE statement and **sp_addtype** stored procedure will both fire an event notification that is created on a CREATE_TYPE event.</span></span> <span data-ttu-id="c235c-134">但**sp_rename**存储过程不会激发任何事件通知。</span><span class="sxs-lookup"><span data-stu-id="c235c-134">However, the **sp_rename** stored procedure does not fire any event notifications.</span></span> <span data-ttu-id="c235c-135">有关详细信息，请参阅[DDL 事件](../triggers/ddl-events.md)。</span><span class="sxs-lookup"><span data-stu-id="c235c-135">For more information, see[DDL Events](../triggers/ddl-events.md).</span></span>  
  
 <span data-ttu-id="c235c-136">*where_condition*</span><span class="sxs-lookup"><span data-stu-id="c235c-136">*where_condition*</span></span>  
 <span data-ttu-id="c235c-137">一个 WHERE 子句查询谓词，其中包含*event_property*名称和逻辑运算符和比较运算符。</span><span class="sxs-lookup"><span data-stu-id="c235c-137">Is a WHERE clause query predicate made up of *event_property* names and logical and comparison operators.</span></span> <span data-ttu-id="c235c-138">*Where_condition*确定在目标数据库中注册相应事件通知的范围。</span><span class="sxs-lookup"><span data-stu-id="c235c-138">The *where_condition* determines the scope in which the corresponding event notification is registered in the target database.</span></span> <span data-ttu-id="c235c-139">它还可以充当筛选器，以面向要从中查询 event_type 的特定架构或对象 *。*</span><span class="sxs-lookup"><span data-stu-id="c235c-139">It can also act as a filter to target a particular schema or object from which to query *event_type.*</span></span> <span data-ttu-id="c235c-140">有关详细信息，请参阅本主题后面的 "备注" 部分。</span><span class="sxs-lookup"><span data-stu-id="c235c-140">For more information, see the Remarks section later in this topic.</span></span>  
  
 <span data-ttu-id="c235c-141">只有 `=` 操作数可与 `DatabaseName`、`SchemaName` 和 `ObjectName` 一起使用。</span><span class="sxs-lookup"><span data-stu-id="c235c-141">Only the `=` operand can be used together with `DatabaseName`, `SchemaName`, and `ObjectName`.</span></span> <span data-ttu-id="c235c-142">其他表达式不能与这些事件属性一起使用。</span><span class="sxs-lookup"><span data-stu-id="c235c-142">Other expressions cannot be used with these event properties.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c235c-143">备注</span><span class="sxs-lookup"><span data-stu-id="c235c-143">Remarks</span></span>  
 <span data-ttu-id="c235c-144">"用于服务器事件的 WMI 提供程序" 语法的*where_condition*确定以下各项：</span><span class="sxs-lookup"><span data-stu-id="c235c-144">The *where_condition* of the WMI Provider for Server Events syntax determines the following:</span></span>  
  
-   <span data-ttu-id="c235c-145">提供程序尝试检索指定*event_type*的作用域：服务器级别、数据库级别或对象级别 (当前支持的唯一对象是队列) 。</span><span class="sxs-lookup"><span data-stu-id="c235c-145">The scope by which the provider tries to retrieve the specified *event_type*: the server level, database level, or object level (the only object currently supported is queue).</span></span> <span data-ttu-id="c235c-146">最后，此范围用于确定在目标数据库中创建的事件通知的类型。</span><span class="sxs-lookup"><span data-stu-id="c235c-146">Ultimately, this scope determines the type of event notification created in the target database.</span></span> <span data-ttu-id="c235c-147">这个过程称为事件通知注册。</span><span class="sxs-lookup"><span data-stu-id="c235c-147">This process called event notification registration.</span></span>  
  
-   <span data-ttu-id="c235c-148">要在其上进行注册的数据库、架构和对象（视具体情况而定）。</span><span class="sxs-lookup"><span data-stu-id="c235c-148">The database, schema, and object, where appropriate, on which to register.</span></span>  
  
 <span data-ttu-id="c235c-149">WMI Provider for Server Events 使用从下到上的最先适应算法为基础 EVENT NOTIFICATION 生成尽可能小的范围。</span><span class="sxs-lookup"><span data-stu-id="c235c-149">The WMI Provider for Server Events uses a bottom-up, first-fit algorithm to produce the narrowest possible scope for the underlying EVENT NOTIFICATION.</span></span> <span data-ttu-id="c235c-150">该算法试图将服务器上的内部活动和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例与 WMI 主机进程之间的网络通信流量降至最低。</span><span class="sxs-lookup"><span data-stu-id="c235c-150">The algorithm tries to minimize internal activity on the server and network traffic between the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the WMI host process.</span></span> <span data-ttu-id="c235c-151">提供程序检查 FROM 子句中指定的*event_type*和 WHERE 子句中的条件，并尝试向最小的可能范围注册基础事件通知。</span><span class="sxs-lookup"><span data-stu-id="c235c-151">The provider examines the *event_type* specified in the FROM clause and the conditions in the WHERE clause, and tries to register the underlying EVENT NOTIFICATION with the narrowest possible scope.</span></span> <span data-ttu-id="c235c-152">如果提供程序无法在最小的范围内注册，则它会依次尝试在更大的范围内注册，直到注册最终成功为止。</span><span class="sxs-lookup"><span data-stu-id="c235c-152">If the provider cannot register at the narrowest scope, it tries to register at successively higher scopes until a registration finally succeeds.</span></span> <span data-ttu-id="c235c-153">如果它达到服务器级别的最大范围且失败，则它将向使用者返回一个错误。</span><span class="sxs-lookup"><span data-stu-id="c235c-153">If it reaches the highest scope the server-level) and fails, it returns an error to the consumer.</span></span>  
  
 <span data-ttu-id="c235c-154">例如，如果在 WHERE 子句中指定 DatabaseName =**'** AdventureWorks **'**，则提供程序将尝试在数据库中注册事件通知 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c235c-154">For example, if DatabaseName=**'** AdventureWorks **'** is specified in the WHERE clause, the provider tries to register an event notification in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="c235c-155">如果 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库存在且调用客户端拥有在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 中创建事件通知所需的权限，则注册成功。</span><span class="sxs-lookup"><span data-stu-id="c235c-155">If the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database exists and the calling client has the required permissions to create an event notification in [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], the registration is successful.</span></span> <span data-ttu-id="c235c-156">否则，将尝试在服务器级别注册事件通知。</span><span class="sxs-lookup"><span data-stu-id="c235c-156">Otherwise, an attempt is made to register the event notification at the server level.</span></span> <span data-ttu-id="c235c-157">如果 WMI 客户端拥有所需的权限，则注册成功。</span><span class="sxs-lookup"><span data-stu-id="c235c-157">The registration succeeds if the WMI client has the required permissions.</span></span> <span data-ttu-id="c235c-158">但是，在这种情况下，在创建完 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库之前不会将事件返回给客户端。</span><span class="sxs-lookup"><span data-stu-id="c235c-158">However, under this scenario, events are not returned to the client until the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database has been created.</span></span>  
  
 <span data-ttu-id="c235c-159">*Where_condition*还可以充当筛选器，以进一步限制特定数据库、架构或对象的查询。</span><span class="sxs-lookup"><span data-stu-id="c235c-159">The *where_condition* can also act as a filter to additionally limit the query to a specific database, schema, or object.</span></span> <span data-ttu-id="c235c-160">例如，请考虑下列 WQL 查询：</span><span class="sxs-lookup"><span data-stu-id="c235c-160">For example, consider the following WQL query:</span></span>  
  
```  
SELECT * FROM ALTER_TABLE   
WHERE DatabaseName = 'AdventureWorks' AND SchemaName = 'Sales'   
    AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'  
```  
  
 <span data-ttu-id="c235c-161">根据注册过程的结果的不同，可以在数据库级别或服务器级别注册此 WQL 查询。</span><span class="sxs-lookup"><span data-stu-id="c235c-161">Depending on the outcome of the registration process, this WQL query may be registered either at the database or server level.</span></span> <span data-ttu-id="c235c-162">但是，即使此查询的注册是在服务器级别进行的，提供程序最终还是会筛选不适用于 `ALTER_TABLE` 表的所有 `AdventureWorks.Sales.SalesOrderDetail` 事件。</span><span class="sxs-lookup"><span data-stu-id="c235c-162">However, even if it is registered at the server level, the provider ultimately filters any `ALTER_TABLE` events that do not apply to the `AdventureWorks.Sales.SalesOrderDetail` table.</span></span> <span data-ttu-id="c235c-163">也就是说，提供程序只会返回在此特定表上出现的 `ALTER_TABLE` 事件的属性。</span><span class="sxs-lookup"><span data-stu-id="c235c-163">In other words, the provider returns only the properties of the `ALTER_TABLE` events that occur on that specific table.</span></span>  
  
 <span data-ttu-id="c235c-164">如果指定复合表达式，例如 `DatabaseName='AW1'` OR `DatabaseName='AW2'`，则会尝试在服务器范围注册单个事件通知，而不是两个独立的事件通知。</span><span class="sxs-lookup"><span data-stu-id="c235c-164">If a compound expression such as `DatabaseName='AW1'` OR `DatabaseName='AW2'` is specified, an attempt is made to register a single event notification at the server scope instead of two separate event notifications.</span></span> <span data-ttu-id="c235c-165">如果调用客户端拥有权限，则注册成功。</span><span class="sxs-lookup"><span data-stu-id="c235c-165">The registration succeeds if the calling client has permissions.</span></span>  
  
 <span data-ttu-id="c235c-166">如果在 `SchemaName='X' AND ObjectType='Y' AND ObjectName='Z'` 子句中指定 all `WHERE` ，则尝试直接在架构中的对象上注册事件通知 `Z` `X` 。</span><span class="sxs-lookup"><span data-stu-id="c235c-166">If `SchemaName='X' AND ObjectType='Y' AND ObjectName='Z'` are all specified in the `WHERE` clause, an attempt is made to register the event notification directly on object `Z` in schema `X`.</span></span> <span data-ttu-id="c235c-167">如果客户端拥有权限，则注册成功。</span><span class="sxs-lookup"><span data-stu-id="c235c-167">The registration succeeds if the client has permissions.</span></span> <span data-ttu-id="c235c-168">请注意，当前仅在队列上支持对象级事件，并且仅针对 QUEUE_ACTIVATION *event_type*。</span><span class="sxs-lookup"><span data-stu-id="c235c-168">Note that currently, object-level events are supported only on queues, and only for the QUEUE_ACTIVATION *event_type*.</span></span>  
  
 <span data-ttu-id="c235c-169">请注意，并非所有事件均可在任何特定的范围内进行查询。</span><span class="sxs-lookup"><span data-stu-id="c235c-169">Note that not all events can be queried at any particular scope.</span></span> <span data-ttu-id="c235c-170">例如，针对跟踪事件（例如 Lock_Deadlock）或跟踪事件组（例如 TRC_LOCKS）的 WQL 查询仅可在服务器级别进行注册。</span><span class="sxs-lookup"><span data-stu-id="c235c-170">For example, a WQL query on a trace event such as Lock_Deadlock, or a trace event group such as TRC_LOCKS, can only be registered at the server level.</span></span> <span data-ttu-id="c235c-171">与此类似，CREATE_ENDPOINT 事件和 DDL_ENDPOINT_EVENTS 事件组也只能在服务器级别进行注册。</span><span class="sxs-lookup"><span data-stu-id="c235c-171">Similarly, the CREATE_ENDPOINT event and the DDL_ENDPOINT_EVENTS event group can also be registered only at the server level.</span></span> <span data-ttu-id="c235c-172">有关用于注册事件的适当范围的详细信息，请参阅[设计事件通知](https://technet.microsoft.com/library/ms175854\(v=sql.105\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="c235c-172">For more information about the appropriate scope for registering events, see [Designing Event Notifications](https://technet.microsoft.com/library/ms175854\(v=sql.105\).aspx).</span></span> <span data-ttu-id="c235c-173">尝试注册 WQL 查询（其*event_type*只能在服务器级别注册）始终在服务器级别进行。</span><span class="sxs-lookup"><span data-stu-id="c235c-173">An attempt to register a WQL query whose *event_type* can only be registered at the server level is always made at the server level.</span></span> <span data-ttu-id="c235c-174">如果 WMI 客户端拥有权限，则注册成功。</span><span class="sxs-lookup"><span data-stu-id="c235c-174">Registration succeeds if the WMI client has permissions.</span></span> <span data-ttu-id="c235c-175">否则，将向客户端返回一个错误。</span><span class="sxs-lookup"><span data-stu-id="c235c-175">Otherwise, an error is returned to the client.</span></span> <span data-ttu-id="c235c-176">不过，在某些情况下，仍可根据与服务器级别事件对应的属性将 WHERE 子句用作服务器级别事件的筛选器。</span><span class="sxs-lookup"><span data-stu-id="c235c-176">In some cases, however, you can still use the WHERE clause as a filter for server-level events based on the properties that correspond to the event.</span></span> <span data-ttu-id="c235c-177">例如，许多跟踪事件具有可在 WHERE 子句中用作筛选器的 `DatabaseName` 属性。</span><span class="sxs-lookup"><span data-stu-id="c235c-177">For example, many trace events have a `DatabaseName` property that can be used in the WHERE clause as a filter.</span></span>  
  
 <span data-ttu-id="c235c-178">服务器范围内的事件通知在**master**数据库中创建，并且可以通过使用[sys. server_event_notifications](/sql/relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql)目录视图来查询元数据。</span><span class="sxs-lookup"><span data-stu-id="c235c-178">Server-scoped event notifications are created in the **master** database and can be queried for metadata by using the [sys.server_event_notifications](/sql/relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="c235c-179">数据库范围内或对象范围内的事件通知在指定的数据库中创建，并且可以通过使用[sys. event_notifications](/sql/relational-databases/system-catalog-views/sys-event-notifications-transact-sql)目录视图来查询元数据。</span><span class="sxs-lookup"><span data-stu-id="c235c-179">Database-scoped or object-scoped event notifications are created in the specified database and can be queried for metadata by using the [sys.event_notifications](/sql/relational-databases/system-catalog-views/sys-event-notifications-transact-sql) catalog view.</span></span> <span data-ttu-id="c235c-180">（您必须为目录视图加上对应的数据库名前缀。）</span><span class="sxs-lookup"><span data-stu-id="c235c-180">(You must prefix the catalog view with the corresponding database name.)</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c235c-181">示例</span><span class="sxs-lookup"><span data-stu-id="c235c-181">Examples</span></span>  
  
### <a name="a-querying-for-events-at-the-server-scope"></a><span data-ttu-id="c235c-182">A.</span><span class="sxs-lookup"><span data-stu-id="c235c-182">A.</span></span> <span data-ttu-id="c235c-183">在服务器范围查询事件</span><span class="sxs-lookup"><span data-stu-id="c235c-183">Querying for events at the server scope</span></span>  
 <span data-ttu-id="c235c-184">以下 WQL 查询检索在 `SERVER_MEMORY_CHANGE` 实例上出现的任何 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 跟踪事件的所有事件属性。</span><span class="sxs-lookup"><span data-stu-id="c235c-184">The following WQL query retrieves all event properties for any `SERVER_MEMORY_CHANGE` trace event that occurs on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
```  
SELECT * FROM SERVER_MEMORY_CHANGE  
```  
  
### <a name="b-querying-for-events-at-the-database-scope"></a><span data-ttu-id="c235c-185">B.</span><span class="sxs-lookup"><span data-stu-id="c235c-185">B.</span></span> <span data-ttu-id="c235c-186">在数据库范围查询事件</span><span class="sxs-lookup"><span data-stu-id="c235c-186">Querying for events at the database scope</span></span>  
 <span data-ttu-id="c235c-187">以下 WQL 查询检索在 `AdventureWorks` 数据库中出现且存在于 `DDL_DATABASE_LEVEL_EVENTS` 事件组下的任何事件的特定事件属性。</span><span class="sxs-lookup"><span data-stu-id="c235c-187">The following WQL query retrieves specific event properties for any event that occurs in the `AdventureWorks` database and exists under the `DDL_DATABASE_LEVEL_EVENTS` event group.</span></span>  
  
```  
SELECT SPID, SQLInstance, DatabaseName FROM DDL_DATABASE_LEVEL_EVENTS   
WHERE DatabaseName = 'AdventureWorks'   
```  
  
### <a name="c-querying-for-events-at-the-database-scope-filtering-by-schema-and-object"></a><span data-ttu-id="c235c-188">C.</span><span class="sxs-lookup"><span data-stu-id="c235c-188">C.</span></span> <span data-ttu-id="c235c-189">在数据库范围查询事件，并按架构和对象进行筛选</span><span class="sxs-lookup"><span data-stu-id="c235c-189">Querying for events at the database scope, filtering by schema and object</span></span>  
 <span data-ttu-id="c235c-190">以下查询检索在表 `ALTER_TABLE` 上出现的任何 `AdventureWorks.Sales.SalesOrderDetail` 事件的所有事件属性。</span><span class="sxs-lookup"><span data-stu-id="c235c-190">The following query retrieves all event properties for any `ALTER_TABLE` event that occurs on table `AdventureWorks.Sales.SalesOrderDetail`.</span></span>  
  
```  
SELECT * FROM ALTER_TABLE   
WHERE DatabaseName = 'AdventureWorks' AND SchemaName = 'Sales'   
    AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'  
```  
  
## <a name="see-also"></a><span data-ttu-id="c235c-191">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c235c-191">See Also</span></span>  
 <span data-ttu-id="c235c-192">[WMI Provider for Server Events 的概念](https://technet.microsoft.com/library/ms180560.aspx) </span><span class="sxs-lookup"><span data-stu-id="c235c-192">[WMI Provider for Server Events Concepts](https://technet.microsoft.com/library/ms180560.aspx) </span></span>  
 [<span data-ttu-id="c235c-193">事件通知（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="c235c-193">Event Notifications (Database Engine)</span></span>](https://technet.microsoft.com/library/ms182602.aspx)  
  
  
