---
title: SQL Server 扩展事件包 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], packages
- xe
ms.assetid: 6bcb04fc-ca04-48f4-b96a-20b604973447
author: rothja
ms.author: jroth
ms.openlocfilehash: 45c452300c008d486bd1f4ab4c92b5f76b96ecd8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577650"
---
# <a name="sql-server-extended-events-packages"></a><span data-ttu-id="64bac-102">SQL Server 扩展事件包</span><span class="sxs-lookup"><span data-stu-id="64bac-102">SQL Server Extended Events Packages</span></span>
  <span data-ttu-id="64bac-103">包是用于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 扩展事件对象的容器。</span><span class="sxs-lookup"><span data-stu-id="64bac-103">A package is a container for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Extended Events objects.</span></span> <span data-ttu-id="64bac-104">扩展事件包有三种类型，它们是：</span><span class="sxs-lookup"><span data-stu-id="64bac-104">There are three kinds of Extended Events packages, which include the following:</span></span>  
  
-   <span data-ttu-id="64bac-105">package0 - 扩展事件系统对象。</span><span class="sxs-lookup"><span data-stu-id="64bac-105">package0 - Extended Events system objects.</span></span> <span data-ttu-id="64bac-106">这是默认包。</span><span class="sxs-lookup"><span data-stu-id="64bac-106">This is the default package.</span></span>  
  
-   <span data-ttu-id="64bac-107">sqlserver - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 相关对象。</span><span class="sxs-lookup"><span data-stu-id="64bac-107">sqlserver - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] related objects.</span></span>  
  
-   <span data-ttu-id="64bac-108">sqlos - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 操作系统 (SQLOS) 相关对象。</span><span class="sxs-lookup"><span data-stu-id="64bac-108">sqlos - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Operating System (SQLOS) related objects.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="64bac-109">SecAudit 包由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 审核使用。</span><span class="sxs-lookup"><span data-stu-id="64bac-109">The SecAudit package is used by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit.</span></span> <span data-ttu-id="64bac-110">包中的所有对象均不能通过扩展事件数据定义语言 (DDL) 使用。</span><span class="sxs-lookup"><span data-stu-id="64bac-110">None of the objects in the package are available through the Extended Events data definition language (DDL).</span></span>  
  
 <span data-ttu-id="64bac-111">包是由名称、GUID 以及包含该包的二进制模块进行标识的。</span><span class="sxs-lookup"><span data-stu-id="64bac-111">Packages are identified by a name, a GUID, and the binary module that contains the package.</span></span> <span data-ttu-id="64bac-112">有关详细信息，请参阅 [sys.dm_xe_packages (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="64bac-112">For more information, see [sys.dm_xe_packages &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql).</span></span>  
  
 <span data-ttu-id="64bac-113">包可以包含以下任一对象或所有对象，稍后将在本主题中详细介绍这些对象：</span><span class="sxs-lookup"><span data-stu-id="64bac-113">A package can contain any or all of the following objects, which are discussed in greater detail later in this topic:</span></span>  
  
-   <span data-ttu-id="64bac-114">事件</span><span class="sxs-lookup"><span data-stu-id="64bac-114">Events</span></span>  
  
-   <span data-ttu-id="64bac-115">目标</span><span class="sxs-lookup"><span data-stu-id="64bac-115">Targets</span></span>  
  
-   <span data-ttu-id="64bac-116">操作</span><span class="sxs-lookup"><span data-stu-id="64bac-116">Actions</span></span>  
  
-   <span data-ttu-id="64bac-117">类型</span><span class="sxs-lookup"><span data-stu-id="64bac-117">Types</span></span>  
  
-   <span data-ttu-id="64bac-118">谓词</span><span class="sxs-lookup"><span data-stu-id="64bac-118">Predicates</span></span>  
  
-   <span data-ttu-id="64bac-119">Maps</span><span class="sxs-lookup"><span data-stu-id="64bac-119">Maps</span></span>  
  
 <span data-ttu-id="64bac-120">在一个事件会话中可混合不同包中的对象。</span><span class="sxs-lookup"><span data-stu-id="64bac-120">Objects from different packages can be mixed in an event session.</span></span> <span data-ttu-id="64bac-121">有关详细信息，请参阅 [SQL Server Extended Events Sessions](sql-server-extended-events-sessions.md)。</span><span class="sxs-lookup"><span data-stu-id="64bac-121">For more information, see [SQL Server Extended Events Sessions](sql-server-extended-events-sessions.md).</span></span>  
  
## <a name="package-contents"></a><span data-ttu-id="64bac-122">包的内容</span><span class="sxs-lookup"><span data-stu-id="64bac-122">Package Contents</span></span>  
 <span data-ttu-id="64bac-123">下图显示了可以在包含于模块中的包中存在的对象。</span><span class="sxs-lookup"><span data-stu-id="64bac-123">The following illustration shows the objects that can exist in packages, which are contained in a module.</span></span> <span data-ttu-id="64bac-124">模块可以是可执行文件或者是动态链接库。</span><span class="sxs-lookup"><span data-stu-id="64bac-124">A module can be an executable or a dynamic link library.</span></span>  
  
 <span data-ttu-id="64bac-125">![模块、包和对象之间的关系](../../database-engine/media/xepackagesobjects.gif "模块、包和对象之间的关系")</span><span class="sxs-lookup"><span data-stu-id="64bac-125">![The relationship of a module, packages, and object](../../database-engine/media/xepackagesobjects.gif "The relationship of a module, packages, and object")</span></span>  
  
### <a name="events"></a><span data-ttu-id="64bac-126">事件</span><span class="sxs-lookup"><span data-stu-id="64bac-126">Events</span></span>  
 <span data-ttu-id="64bac-127">事件是程序（例如 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]）的执行路径中的相关监视点。</span><span class="sxs-lookup"><span data-stu-id="64bac-127">Events are monitoring points of interest in the execution path of a program, such as [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="64bac-128">事件触发即表明已经到达相关点，并具有自事件触发以来的状态信息。</span><span class="sxs-lookup"><span data-stu-id="64bac-128">An event firing carries with it the fact that the point of interest was reached, and state information from the time the event was fired.</span></span>  
  
 <span data-ttu-id="64bac-129">事件可仅用于跟踪目的或用于触发操作。</span><span class="sxs-lookup"><span data-stu-id="64bac-129">Events can be used solely for tracing purposes or for triggering actions.</span></span> <span data-ttu-id="64bac-130">这些操作可以是同步的，也可以是异步的。</span><span class="sxs-lookup"><span data-stu-id="64bac-130">These actions can either be synchronous or asynchronous.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="64bac-131">事件不知道在对事件触发做出响应时可能会触发的操作。</span><span class="sxs-lookup"><span data-stu-id="64bac-131">An event does not have any knowledge of the actions that may be triggered in response to the event firing.</span></span>  
  
 <span data-ttu-id="64bac-132">在向扩展事件注册包后，将不能更改该包中的事件集。</span><span class="sxs-lookup"><span data-stu-id="64bac-132">A set of events in a package cannot change after the package is registered with Extended Events.</span></span>  
  
 <span data-ttu-id="64bac-133">所有事件都有一个用于定义其内容的版本控制架构。</span><span class="sxs-lookup"><span data-stu-id="64bac-133">All events have a versioned schema which defines their contents.</span></span> <span data-ttu-id="64bac-134">此架构由其类型已定义好的事件列组成。</span><span class="sxs-lookup"><span data-stu-id="64bac-134">This schema is composed of event columns with well defined types.</span></span> <span data-ttu-id="64bac-135">特定类型的事件在提供其数据时必须始终完全遵守在架构中指定的相同顺序。</span><span class="sxs-lookup"><span data-stu-id="64bac-135">An event of a specific type must always provide its data in exactly the same order that is specified in the schema.</span></span> <span data-ttu-id="64bac-136">但是，事件目标不必使用提供的所有数据。</span><span class="sxs-lookup"><span data-stu-id="64bac-136">However, an event target does not have to consume all the data that is provided.</span></span>  
  
#### <a name="event-categorization"></a><span data-ttu-id="64bac-137">事件分类</span><span class="sxs-lookup"><span data-stu-id="64bac-137">Event Categorization</span></span>  
 <span data-ttu-id="64bac-138">扩展事件使用与 Windows 事件跟踪 (ETW) 类似的事件分类模型。</span><span class="sxs-lookup"><span data-stu-id="64bac-138">Extended Events uses an event categorization model similar to Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="64bac-139">两个事件属性将用于分类、通道和关键字。</span><span class="sxs-lookup"><span data-stu-id="64bac-139">Two event properties are used for categorization, channel and keyword.</span></span> <span data-ttu-id="64bac-140">使用这些属性可支持将扩展事件与 ETW 及其工具进行集成。</span><span class="sxs-lookup"><span data-stu-id="64bac-140">Using these properties supports the integration of Extended Events with ETW and its tools.</span></span>  
  
 <span data-ttu-id="64bac-141">**频道**</span><span class="sxs-lookup"><span data-stu-id="64bac-141">**Channel**</span></span>  
  
 <span data-ttu-id="64bac-142">通道用于标识事件的用户。</span><span class="sxs-lookup"><span data-stu-id="64bac-142">A channel identifies the audience for an event.</span></span> <span data-ttu-id="64bac-143">下表对这些通道进行了说明。</span><span class="sxs-lookup"><span data-stu-id="64bac-143">These channels are described in the following table.</span></span>  
  
|<span data-ttu-id="64bac-144">术语</span><span class="sxs-lookup"><span data-stu-id="64bac-144">Term</span></span>|<span data-ttu-id="64bac-145">定义</span><span class="sxs-lookup"><span data-stu-id="64bac-145">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="64bac-146">管理员</span><span class="sxs-lookup"><span data-stu-id="64bac-146">Admin</span></span>|<span data-ttu-id="64bac-147">管理员事件主要针对的是最终用户、管理员和支持人员。</span><span class="sxs-lookup"><span data-stu-id="64bac-147">Admin events are primarily targeted to the end users, administrators, and support.</span></span> <span data-ttu-id="64bac-148">管理员通道中包含的事件指示定义好的解决方案出现问题，管理员可以对该问题进行处理。</span><span class="sxs-lookup"><span data-stu-id="64bac-148">The events that are found in the admin channels indicate a problem with a well-defined solution that an administrator can act on.</span></span> <span data-ttu-id="64bac-149">例如，应用程序无法连接到打印机就是一个管理员事件。</span><span class="sxs-lookup"><span data-stu-id="64bac-149">An example of an admin event is when an application fails to connect to a printer.</span></span> <span data-ttu-id="64bac-150">这些事件可能在文档中有详细描述，或者有与之关联的消息告诉读者如何纠正这一问题。</span><span class="sxs-lookup"><span data-stu-id="64bac-150">These events are either well-documented or have a message associated with them that tells the reader what to do to rectify the problem.</span></span>|  
|<span data-ttu-id="64bac-151">可运行</span><span class="sxs-lookup"><span data-stu-id="64bac-151">Operational</span></span>|<span data-ttu-id="64bac-152">操作事件用于分析和诊断问题或匹配项。</span><span class="sxs-lookup"><span data-stu-id="64bac-152">Operational events are used for analyzing and diagnosing a problem or occurrence.</span></span> <span data-ttu-id="64bac-153">它们可用于根据问题或发生的事件触发工具或任务。</span><span class="sxs-lookup"><span data-stu-id="64bac-153">They can be used to trigger tools or tasks based on the problem or occurrence.</span></span> <span data-ttu-id="64bac-154">操作事件的一个示例是从系统中添加或删除打印机。</span><span class="sxs-lookup"><span data-stu-id="64bac-154">An example of an operational event is when a printer is added or removed from a system.</span></span>|  
|<span data-ttu-id="64bac-155">分析</span><span class="sxs-lookup"><span data-stu-id="64bac-155">Analytic</span></span>|<span data-ttu-id="64bac-156">分析事件的发布量是很大的。</span><span class="sxs-lookup"><span data-stu-id="64bac-156">Analytic events are published in high volume.</span></span> <span data-ttu-id="64bac-157">它们对程序操作进行说明并且通常用于性能调查。</span><span class="sxs-lookup"><span data-stu-id="64bac-157">They describe program operation and are typically used in performance investigations.</span></span>|  
|<span data-ttu-id="64bac-158">调试</span><span class="sxs-lookup"><span data-stu-id="64bac-158">Debug</span></span>|<span data-ttu-id="64bac-159">调试事件仅由开发人员用来诊断问题以进行调试。</span><span class="sxs-lookup"><span data-stu-id="64bac-159">Debug events are used solely by developers to diagnose a problem for debugging.</span></span><br /><br /> <span data-ttu-id="64bac-160">注意：调试通道中的事件返回特定于实现的内部状态数据。</span><span class="sxs-lookup"><span data-stu-id="64bac-160">Note: Events in the Debug channel return internal implementation-specific state data.</span></span> <span data-ttu-id="64bac-161">这些事件返回的架构和数据可能在 SQL Server 的将来版本中更改或失效。</span><span class="sxs-lookup"><span data-stu-id="64bac-161">The schemas and data that the events return may change or become invalid in future versions of SQL Server.</span></span> <span data-ttu-id="64bac-162">因此，调试渠道中的事件在 SQL Server 的将来版本中可能更改或删除且不事先通知。</span><span class="sxs-lookup"><span data-stu-id="64bac-162">Therefore, events in the Debug channel may change or be removed in future versions of SQL Server without notice.</span></span>|  
  
 <span data-ttu-id="64bac-163">**关键字**</span><span class="sxs-lookup"><span data-stu-id="64bac-163">**Keyword**</span></span>  
  
 <span data-ttu-id="64bac-164">关键字是特定于应用程序的，并且使得对相关事件的分组更加细化，这样您能更容易地指定和检索要在会话中使用的事件。</span><span class="sxs-lookup"><span data-stu-id="64bac-164">A keyword is application specific and enables a finer-grained grouping of related events, which makes it easier for you to specify and retrieve an event that you want to use in a session.</span></span> <span data-ttu-id="64bac-165">可以使用以下查询来获取关键字信息。</span><span class="sxs-lookup"><span data-stu-id="64bac-165">You can use the following query to obtain keyword information.</span></span>  
  
```  
select map_value Keyword from sys.dm_xe_map_values  
where name = 'keyword_map'  
```  
  
> [!NOTE]  
>  <span data-ttu-id="64bac-166">关键字将紧密映射到 SQL 跟踪事件的当前分组中。</span><span class="sxs-lookup"><span data-stu-id="64bac-166">Keywords map closely to the current grouping of SQL Trace events.</span></span>  
  
### <a name="targets"></a><span data-ttu-id="64bac-167">目标</span><span class="sxs-lookup"><span data-stu-id="64bac-167">Targets</span></span>  
 <span data-ttu-id="64bac-168">目标是指事件使用者。</span><span class="sxs-lookup"><span data-stu-id="64bac-168">Targets are event consumers.</span></span> <span data-ttu-id="64bac-169">目标在触发事件的线程中同步处理事件或在系统提供的线程中异步处理事件。</span><span class="sxs-lookup"><span data-stu-id="64bac-169">Targets process events, either synchronously on the thread that fires the event or asynchronously on a system provided thread.</span></span> <span data-ttu-id="64bac-170">扩展事件提供了多个目标，您可以根据需要将其用于定向事件输出。</span><span class="sxs-lookup"><span data-stu-id="64bac-170">Extended Events provides several targets that you can use as appropriate for directing event output.</span></span> <span data-ttu-id="64bac-171">有关详细信息，请参阅 [SQL Server Extended Events Targets](../../database-engine/sql-server-extended-events-targets.md)。</span><span class="sxs-lookup"><span data-stu-id="64bac-171">For more information, see [SQL Server Extended Events Targets](../../database-engine/sql-server-extended-events-targets.md).</span></span>  
  
### <a name="actions"></a><span data-ttu-id="64bac-172">操作</span><span class="sxs-lookup"><span data-stu-id="64bac-172">Actions</span></span>  
 <span data-ttu-id="64bac-173">操作是对事件做出的一个编程方式的响应或一系列响应。</span><span class="sxs-lookup"><span data-stu-id="64bac-173">An action is a programmatic response or series of responses to an event.</span></span> <span data-ttu-id="64bac-174">操作与事件绑定在一起，并且每个事件都可能具有唯一的一组操作。</span><span class="sxs-lookup"><span data-stu-id="64bac-174">Actions are bound to an event, and each event may have a unique set of actions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="64bac-175">用于一组特定事件的操作不能绑定到未知事件。</span><span class="sxs-lookup"><span data-stu-id="64bac-175">Actions that are intended for a specific set of events cannot bind to unknown events.</span></span>  
  
 <span data-ttu-id="64bac-176">在触发事件的线程上将同步调用与该事件绑定的操作。</span><span class="sxs-lookup"><span data-stu-id="64bac-176">An action bound to an event is invoked synchronously on the thread that fired the event.</span></span> <span data-ttu-id="64bac-177">操作类型很多，并且它们都具有多种功能。</span><span class="sxs-lookup"><span data-stu-id="64bac-177">There are many types of actions and they have a wide range of capabilities.</span></span> <span data-ttu-id="64bac-178">操作可以：</span><span class="sxs-lookup"><span data-stu-id="64bac-178">Actions can:</span></span>  
  
-   <span data-ttu-id="64bac-179">捕获堆栈转储和检查数据。</span><span class="sxs-lookup"><span data-stu-id="64bac-179">Capture a stack dump and inspect data.</span></span>  
  
-   <span data-ttu-id="64bac-180">使用变量存储将状态信息存储在本地上下文中。</span><span class="sxs-lookup"><span data-stu-id="64bac-180">Store state information in a local context using variable storage.</span></span>  
  
-   <span data-ttu-id="64bac-181">聚合事件数据。</span><span class="sxs-lookup"><span data-stu-id="64bac-181">Aggregate event data.</span></span>  
  
-   <span data-ttu-id="64bac-182">将数据追加到事件数据。</span><span class="sxs-lookup"><span data-stu-id="64bac-182">Append data to event data.</span></span>  
  
 <span data-ttu-id="64bac-183">以下是一些典型且熟知的操作示例：</span><span class="sxs-lookup"><span data-stu-id="64bac-183">Some typical and well known examples of actions are:</span></span>  
  
-   <span data-ttu-id="64bac-184">堆栈转储器</span><span class="sxs-lookup"><span data-stu-id="64bac-184">Stack dumper</span></span>  
  
-   <span data-ttu-id="64bac-185">执行计划检测（仅限[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ）</span><span class="sxs-lookup"><span data-stu-id="64bac-185">Execution plan detection ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] only)</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="64bac-186">堆栈集合（仅[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ）</span><span class="sxs-lookup"><span data-stu-id="64bac-186">stack collection ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] only)</span></span>  
  
-   <span data-ttu-id="64bac-187">运行时统计信息计算</span><span class="sxs-lookup"><span data-stu-id="64bac-187">Run time statistics calculation</span></span>  
  
-   <span data-ttu-id="64bac-188">收集发生异常时的用户输入</span><span class="sxs-lookup"><span data-stu-id="64bac-188">Gather user input on exception</span></span>  
  
### <a name="predicates"></a><span data-ttu-id="64bac-189">谓词</span><span class="sxs-lookup"><span data-stu-id="64bac-189">Predicates</span></span>  
 <span data-ttu-id="64bac-190">谓词是一组逻辑规则，用于在处理事件时计算这些事件。</span><span class="sxs-lookup"><span data-stu-id="64bac-190">Predicates are a set of logical rules that are used to evaluate events when they are processed.</span></span> <span data-ttu-id="64bac-191">这可以使扩展事件用户根据特定条件有选择地捕获事件数据。</span><span class="sxs-lookup"><span data-stu-id="64bac-191">This enables the Extended Events user to selectively capture event data based on specific criteria.</span></span>  
  
 <span data-ttu-id="64bac-192">谓词可在本地上下文中存储用于创建谓词的数据，这些谓词每 *n* 分钟或每当事件触发 *n* 次时返回一次 true。</span><span class="sxs-lookup"><span data-stu-id="64bac-192">Predicates can store data in a local context that can be used for creating predicates that return true once every *n* minutes or every *n* times that an event fires.</span></span> <span data-ttu-id="64bac-193">本地上下文存储也可用于动态更新谓词，从而在事件包含类似数据时取消未来的事件触发。</span><span class="sxs-lookup"><span data-stu-id="64bac-193">This local context storage can also be used to dynamically update the predicate, thereby suppressing future event firing if the events contain similar data.</span></span>  
  
 <span data-ttu-id="64bac-194">谓词能够检索上下文信息，例如线程 ID 以及事件的特定数据。</span><span class="sxs-lookup"><span data-stu-id="64bac-194">Predicates have the ability to retrieve context information, such as the thread ID, as well as event specific data.</span></span> <span data-ttu-id="64bac-195">谓词的计算结果为完整的布尔表达式，并且它支持在整个表达式为 false 的第一个点处执行短路。</span><span class="sxs-lookup"><span data-stu-id="64bac-195">Predicates are evaluated as full Boolean expressions, and support short circuiting at the first point where the entire expression is found to be false.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="64bac-196">如果早期的谓词检查失败，则可能无法计算具有副作用的谓词。</span><span class="sxs-lookup"><span data-stu-id="64bac-196">Predicates with side effects may not be evaluated if an earlier predicate check fails.</span></span>  
  
### <a name="types"></a><span data-ttu-id="64bac-197">类型</span><span class="sxs-lookup"><span data-stu-id="64bac-197">Types</span></span>  
 <span data-ttu-id="64bac-198">由于数据是排列在一起的字节集合，因此需要使用字节集合的长度和特征来解释这些数据。</span><span class="sxs-lookup"><span data-stu-id="64bac-198">Because data is a collection of bytes strung together, the length and characteristics of the byte collection are required in order to interpret the data.</span></span> <span data-ttu-id="64bac-199">该信息将封装在 Type 对象中。</span><span class="sxs-lookup"><span data-stu-id="64bac-199">This information is encapsulated in the Type object.</span></span> <span data-ttu-id="64bac-200">下面是为包对象提供的类型：</span><span class="sxs-lookup"><span data-stu-id="64bac-200">The following types are provided for package objects:</span></span>  
  
-   <span data-ttu-id="64bac-201">event</span><span class="sxs-lookup"><span data-stu-id="64bac-201">event</span></span>  
  
-   <span data-ttu-id="64bac-202">action</span><span class="sxs-lookup"><span data-stu-id="64bac-202">action</span></span>  
  
-   <span data-ttu-id="64bac-203">目标</span><span class="sxs-lookup"><span data-stu-id="64bac-203">target</span></span>  
  
-   <span data-ttu-id="64bac-204">pred_source</span><span class="sxs-lookup"><span data-stu-id="64bac-204">pred_source</span></span>  
  
-   <span data-ttu-id="64bac-205">pred_compare</span><span class="sxs-lookup"><span data-stu-id="64bac-205">pred_compare</span></span>  
  
-   <span data-ttu-id="64bac-206">类型</span><span class="sxs-lookup"><span data-stu-id="64bac-206">type</span></span>  
  
 <span data-ttu-id="64bac-207">有关详细信息，请参阅 [sys.dm_xe_objects (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="64bac-207">For more information, see [sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql).</span></span>  
  
### <a name="maps"></a><span data-ttu-id="64bac-208">Maps</span><span class="sxs-lookup"><span data-stu-id="64bac-208">Maps</span></span>  
 <span data-ttu-id="64bac-209">映射表用于将内部值映射到字符串，这使用户可以知道该值代表什么。</span><span class="sxs-lookup"><span data-stu-id="64bac-209">A map table maps an internal value to a string, which enables a user to know what the value represents.</span></span> <span data-ttu-id="64bac-210">用户可以获得关于内部值真正含义的说明，而不是只能够获取数值。</span><span class="sxs-lookup"><span data-stu-id="64bac-210">Instead of only being able to obtain a numeric value, a user can get a meaningful description of the internal value.</span></span> <span data-ttu-id="64bac-211">下面的查询显示了获取映射值的方式。</span><span class="sxs-lookup"><span data-stu-id="64bac-211">The following query shows how to obtain map values.</span></span>  
  
```  
select map_key, map_value from sys.dm_xe_map_values  
where name = 'lock_mode'  
```  
  
 <span data-ttu-id="64bac-212">前面的查询生成以下输出。</span><span class="sxs-lookup"><span data-stu-id="64bac-212">The preceding query produces the following output.</span></span>  
  
 `map_key     map_value`  
  
 `---------------------`  
  
 `0           NL`  
  
 `1           SCH_S`  
  
 `2           SCH_M`  
  
 `3           S`  
  
 `4           U`  
  
 `5           X`  
  
 `6           IS`  
  
 `7           IU`  
  
 `8           IX`  
  
 `9           SIU`  
  
 `10          SIX`  
  
 `11          UIX`  
  
 `12          BU`  
  
 `13          RS_S`  
  
 `14          RS_U`  
  
 `15          RI_NL`  
  
 `16          RI_S`  
  
 `17          RI_U`  
  
 `18          RI_X`  
  
 `19          RX_S`  
  
 `20          RX_U`  
  
 `21          RX_X`  
  
 `21          RX_X`  
  
 <span data-ttu-id="64bac-213">以此表为例，假定有一名为模式的列，且其值为 5。</span><span class="sxs-lookup"><span data-stu-id="64bac-213">Using this table as an example, assume that you have a column named mode, and its value is 5.</span></span> <span data-ttu-id="64bac-214">此表指示 5 映射到 X，即表示锁类型为排他。</span><span class="sxs-lookup"><span data-stu-id="64bac-214">The table indicates that 5 maps to X, which means the lock type is Exclusive.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64bac-215">另请参阅</span><span class="sxs-lookup"><span data-stu-id="64bac-215">See Also</span></span>  
 <span data-ttu-id="64bac-216">[SQL Server 扩展事件会话](sql-server-extended-events-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="64bac-216">[SQL Server Extended Events Sessions](sql-server-extended-events-sessions.md) </span></span>  
 <span data-ttu-id="64bac-217">[SQL Server 扩展事件引擎](sql-server-extended-events-engine.md) </span><span class="sxs-lookup"><span data-stu-id="64bac-217">[SQL Server Extended Events Engine](sql-server-extended-events-engine.md) </span></span>  
 [<span data-ttu-id="64bac-218">SQL Server 扩展事件目标</span><span class="sxs-lookup"><span data-stu-id="64bac-218">SQL Server Extended Events Targets</span></span>](../../database-engine/sql-server-extended-events-targets.md)  
  
  
