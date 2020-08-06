---
title: SQL Server 扩展事件会话 | Microsoft Docs
ms.custom: ''
ms.date: 05/26/2020
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- xe
- sessions
- extend events [SQL Server]
ms.assetid: c3c92544-351a-4bce-a06a-1f2a47e494e9
author: rothja
ms.author: jroth
ms.openlocfilehash: 3aab8c57a578ea60829514b575e168bc5a1dd8c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577648"
---
# <a name="sql-server-extended-events-sessions"></a><span data-ttu-id="84fa3-102">SQL Server Extended Events Sessions</span><span class="sxs-lookup"><span data-stu-id="84fa3-102">SQL Server Extended Events Sessions</span></span>
  <span data-ttu-id="84fa3-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 扩展事件会话是在用于承载 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 扩展事件引擎的进程中创建的。</span><span class="sxs-lookup"><span data-stu-id="84fa3-103">A [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Extended Events session is created in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] process hosting the Extended Events engine.</span></span> <span data-ttu-id="84fa3-104">扩展事件会话的以下各方面信息可为您理解扩展事件基础结构和所发生的常规处理提供有关背景知识：</span><span class="sxs-lookup"><span data-stu-id="84fa3-104">The following aspects of an Extended Events session provide a context for understanding the Extended Events infrastructure and the general processing that takes place:</span></span>  
  
-   <span data-ttu-id="84fa3-105">会话状态。</span><span class="sxs-lookup"><span data-stu-id="84fa3-105">Session states.</span></span> <span data-ttu-id="84fa3-106">执行 CREATE EVENT SESSION 和 ALTER EVENT SESSION 语句时扩展事件会话所处的不同状态。</span><span class="sxs-lookup"><span data-stu-id="84fa3-106">The different states that an Extended Events session is in when CREATE EVENT SESSION and ALTER EVENT SESSION statements are executed.</span></span>  
  
-   <span data-ttu-id="84fa3-107">会话内容和特征。</span><span class="sxs-lookup"><span data-stu-id="84fa3-107">Session content and characteristics.</span></span> <span data-ttu-id="84fa3-108">扩展事件会话的内容（例如目标和事件）以及这些对象在某个会话中或多个会话间的关系。</span><span class="sxs-lookup"><span data-stu-id="84fa3-108">The content of an Extended Events session, such as targets and events, and how these objects are related in a session or between sessions.</span></span>  
  
## <a name="session-states"></a><span data-ttu-id="84fa3-109">会话状态</span><span class="sxs-lookup"><span data-stu-id="84fa3-109">Session States</span></span>  
 <span data-ttu-id="84fa3-110">下图说明了扩展事件会话的不同状态。</span><span class="sxs-lookup"><span data-stu-id="84fa3-110">The following illustration shows the various states of an Extended Events session.</span></span>  

<span data-ttu-id="84fa3-111">![扩展事件会话状态](../../database-engine/media/xesessionstate.png "扩展事件会话状态")</span><span class="sxs-lookup"><span data-stu-id="84fa3-111">![Extended event session state](../../database-engine/media/xesessionstate.png "Extended event session state")</span></span>

 <span data-ttu-id="84fa3-112">对照前面的图，可以注意到在对事件会话发出不同的 DDL 命令时会话状态将发生更改。</span><span class="sxs-lookup"><span data-stu-id="84fa3-112">Referring to the preceding figure, note that session state changes as the different DDL commands are issued for an event session.</span></span> <span data-ttu-id="84fa3-113">下表说明了这些状态更改。</span><span class="sxs-lookup"><span data-stu-id="84fa3-113">The following table describes these changes in state.</span></span>  
  
|<span data-ttu-id="84fa3-114">图例标签</span><span class="sxs-lookup"><span data-stu-id="84fa3-114">Illustration label</span></span>|<span data-ttu-id="84fa3-115">DDL 语句</span><span class="sxs-lookup"><span data-stu-id="84fa3-115">DDL statement</span></span>|<span data-ttu-id="84fa3-116">说明</span><span class="sxs-lookup"><span data-stu-id="84fa3-116">Description</span></span>|  
|------------------------|-------------------|-----------------|  
|<span data-ttu-id="84fa3-117">创建</span><span class="sxs-lookup"><span data-stu-id="84fa3-117">Create</span></span>|<span data-ttu-id="84fa3-118">CREATE EVENT SESSION</span><span class="sxs-lookup"><span data-stu-id="84fa3-118">CREATE EVENT SESSION</span></span>|<span data-ttu-id="84fa3-119">主机进程将创建一个会话对象，其中包含由 CREATE EVENT SESSION 提供的元数据。</span><span class="sxs-lookup"><span data-stu-id="84fa3-119">The host process creates a session object that contains the metadata provided by CREATE EVENT SESSION.</span></span> <span data-ttu-id="84fa3-120">主机进程将验证会话定义和用户权限级别，并将元数据存储在 master 数据库中。</span><span class="sxs-lookup"><span data-stu-id="84fa3-120">The host process validates the session definition, validates the user permission level, and stores the metadata in the master database.</span></span> <span data-ttu-id="84fa3-121">此时该会话处于不活动状态。</span><span class="sxs-lookup"><span data-stu-id="84fa3-121">At this point the session is not active.</span></span>|  
|<span data-ttu-id="84fa3-122">更改</span><span class="sxs-lookup"><span data-stu-id="84fa3-122">Alter</span></span>|<span data-ttu-id="84fa3-123">ALTER EVENT SESSION, STATE=START</span><span class="sxs-lookup"><span data-stu-id="84fa3-123">ALTER EVENT SESSION, STATE=START</span></span>|<span data-ttu-id="84fa3-124">主机进程启动会话。</span><span class="sxs-lookup"><span data-stu-id="84fa3-124">The host process starts the session.</span></span> <span data-ttu-id="84fa3-125">主机进程将读取存储的元数据、验证会话定义、验证用户权限级别并创建会话。</span><span class="sxs-lookup"><span data-stu-id="84fa3-125">The host process reads the stored metadata, validates the session definition, verifies the level of user permission level, and creates the session.</span></span> <span data-ttu-id="84fa3-126">此操作还将载入会话对象（例如事件和目标），此时事件处理即处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="84fa3-126">Session objects, such as events and targets, are loaded and event handling is active.</span></span>|  
|<span data-ttu-id="84fa3-127">更改</span><span class="sxs-lookup"><span data-stu-id="84fa3-127">Alter</span></span>|<span data-ttu-id="84fa3-128">ALTER EVENT SESSION, STATE=STOP</span><span class="sxs-lookup"><span data-stu-id="84fa3-128">ALTER EVENT SESSION, STATE=STOP</span></span>|<span data-ttu-id="84fa3-129">主机进程将停止活动会话，但会保留元数据。</span><span class="sxs-lookup"><span data-stu-id="84fa3-129">The host process stops the active session but retains the metadata.</span></span>|  
|<span data-ttu-id="84fa3-130">丢弃</span><span class="sxs-lookup"><span data-stu-id="84fa3-130">Drop</span></span>|<span data-ttu-id="84fa3-131">删除事件会话</span><span class="sxs-lookup"><span data-stu-id="84fa3-131">DROP EVENT SESSION</span></span>|<span data-ttu-id="84fa3-132">此“删除”(DROP SESSION) 操作将删除元数据并关闭活动会话，或仅删除会话元数据；具体取决于会话是否处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="84fa3-132">Depending on whether or not the session is active, Drop (DROP SESSION) will delete the metadata and close the active session, or delete the session metadata.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="84fa3-133">ALTER EVENT SESSION 和 DROP EVENT SESSION 均可应用于元数据或者应用于活动会话与元数据。</span><span class="sxs-lookup"><span data-stu-id="84fa3-133">Both ALTER EVENT SESSION and DROP EVENT SESSION can be applied to the metadata or to an active session and the metadata.</span></span>  
  
## <a name="session-content-and-characteristics"></a><span data-ttu-id="84fa3-134">会话内容和特征</span><span class="sxs-lookup"><span data-stu-id="84fa3-134">Session Content and Characteristics</span></span>  
 <span data-ttu-id="84fa3-135">扩展事件会话包括隐含的边界，因为一个会话的配置不会更改另一个会话的配置。</span><span class="sxs-lookup"><span data-stu-id="84fa3-135">Extended Event sessions have implied boundaries in that the configuration of one session does not change the configuration of another session.</span></span> <span data-ttu-id="84fa3-136">但是，这些边界不会阻止在多个会话中同时使用某个事件或目标。</span><span class="sxs-lookup"><span data-stu-id="84fa3-136">However, these boundaries do not prevent an event or target from being used in more than one session.</span></span>  
  
 <span data-ttu-id="84fa3-137">下图说明了会话内容以及包和会话之间的关系。</span><span class="sxs-lookup"><span data-stu-id="84fa3-137">The following illustration shows session content and the relationship between packages and sessions.</span></span>  
  
 <span data-ttu-id="84fa3-138">![会话中的对象共存和共享。](../../database-engine/media/xesessions.gif "会话中的对象共存和共享。")</span><span class="sxs-lookup"><span data-stu-id="84fa3-138">![Object co-existance and sharing in sessions.](../../database-engine/media/xesessions.gif "Object co-existance and sharing in sessions.")</span></span>  
  
 <span data-ttu-id="84fa3-139">对照前面的图，可注意到：</span><span class="sxs-lookup"><span data-stu-id="84fa3-139">Referring to the preceding illustration, note that:</span></span>  
  
-   <span data-ttu-id="84fa3-140">包对象与会话之间的映射是多对多映射，也就是说，一个对象可在多个会话中出现，一个会话也可包含多个对象。</span><span class="sxs-lookup"><span data-stu-id="84fa3-140">The mapping between package objects and sessions is many to many, which means that an object can appear in several sessions, and a session can contain several objects.</span></span>  
  
-   <span data-ttu-id="84fa3-141">可在多个会话中启用同一个事件 (Event 1) 或目标 (Target 1)。</span><span class="sxs-lookup"><span data-stu-id="84fa3-141">The same event (Event 1) or target (Target 1) can be enabled in more than one session.</span></span>  
  
 <span data-ttu-id="84fa3-142">会话具有以下特征：</span><span class="sxs-lookup"><span data-stu-id="84fa3-142">Sessions have the following characteristics:</span></span>  
  
-   <span data-ttu-id="84fa3-143">对于每个会话，操作和谓词均将绑定到事件。</span><span class="sxs-lookup"><span data-stu-id="84fa3-143">Actions and predicates are bound to events on a per-session basis.</span></span> <span data-ttu-id="84fa3-144">如果在会话 A 中包含事件 1（绑定有操作 1 和谓词 Z），这将不会对会话 B 中包含事件 1（绑定有操作 2 和操作 3，但没有谓词）有任何影响。</span><span class="sxs-lookup"><span data-stu-id="84fa3-144">If you have Event 1 in Session A with Action 1 and Predicate Z, this will not in any way affect having Event 1 in Session B with Action 2 and Action 3 with no predicate.</span></span>  
  
-   <span data-ttu-id="84fa3-145">策略将被附加到会话以处理缓冲和调度以及因果关系跟踪。</span><span class="sxs-lookup"><span data-stu-id="84fa3-145">Policies are attached to sessions to handle buffering and dispatch, and causality tracking.</span></span>  
  
 <span data-ttu-id="84fa3-146">**缓冲和调度**</span><span class="sxs-lookup"><span data-stu-id="84fa3-146">**Buffering and dispatch**</span></span>  
  
 <span data-ttu-id="84fa3-147">缓冲指运行事件会话期间事件数据的存储方式。</span><span class="sxs-lookup"><span data-stu-id="84fa3-147">Buffering refers to how event data is stored while an event session is running.</span></span>  <span data-ttu-id="84fa3-148">缓冲策略将指定用于事件数据的内存大小以及针对事件的丢失策略。</span><span class="sxs-lookup"><span data-stu-id="84fa3-148">Buffering policies specify how much memory to use for event data, and the loss policy for the events.</span></span> <span data-ttu-id="84fa3-149">调度指事件在被传递给目标进行处理之前驻留在缓冲区的时间。</span><span class="sxs-lookup"><span data-stu-id="84fa3-149">Dispatch refers to the amount of time events will stay in buffers before being served to targets for processing.</span></span>  
  
 <span data-ttu-id="84fa3-150">**因果关系跟踪**</span><span class="sxs-lookup"><span data-stu-id="84fa3-150">**Causality tracking**</span></span>  
  
 <span data-ttu-id="84fa3-151">因果关系跟踪提供了跨越多个任务来跟踪工作的功能。</span><span class="sxs-lookup"><span data-stu-id="84fa3-151">Causality tracking provides the ability to track work across multiple tasks.</span></span> <span data-ttu-id="84fa3-152">当启用因果关系跟踪时，每个激发的事件在系统中都具有一个唯一的活动 ID。</span><span class="sxs-lookup"><span data-stu-id="84fa3-152">When causality tracking is enabled, each event fired has a unique activity ID across the system.</span></span> <span data-ttu-id="84fa3-153">活动 ID 是 GUID 值和序列号的组合，GUID 值对于某项任务的所有事件将保持不变，而序列号将随着事件的每次激发而递增。</span><span class="sxs-lookup"><span data-stu-id="84fa3-153">The activity ID is a combination of a GUID value that remains constant across all events for a task, and a sequence number that is incremented each time an event is fired.</span></span> <span data-ttu-id="84fa3-154">当一项任务导致对另一项任务执行工作时，父任务的活动 ID 将发送到子任务。</span><span class="sxs-lookup"><span data-stu-id="84fa3-154">When one task causes work to be done on another, the activity ID of the parent is sent to the child task.</span></span> <span data-ttu-id="84fa3-155">子任务将在其第一次激发事件时输出父任务的活动 ID。</span><span class="sxs-lookup"><span data-stu-id="84fa3-155">The child task outputs the parent's activity ID the first time it fires an event.</span></span>  
  
 <span data-ttu-id="84fa3-156">扩展事件体系结构提供了一个灵活的系统，允许同时使用多个对象以解决特定的问题。</span><span class="sxs-lookup"><span data-stu-id="84fa3-156">The Extended Events architecture provides a flexible system that allows a variety of objects to be used together to solve specific problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84fa3-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="84fa3-157">See Also</span></span>  
 [<span data-ttu-id="84fa3-158">扩展事件</span><span class="sxs-lookup"><span data-stu-id="84fa3-158">Extended Events</span></span>](extended-events.md)  
  
  
