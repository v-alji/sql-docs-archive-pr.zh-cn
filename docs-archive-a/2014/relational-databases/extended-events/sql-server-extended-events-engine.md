---
title: SQL Server 扩展事件引擎 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], engine
ms.assetid: d74642a5-42b9-4a15-aa3d-f98bfe695050
author: rothja
ms.author: jroth
ms.openlocfilehash: ef11ac8e2cfaf39d2bca90f1d5d52439989ee327
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577652"
---
# <a name="sql-server-extended-events-engine"></a><span data-ttu-id="807cc-102">SQL Server 扩展事件引擎</span><span class="sxs-lookup"><span data-stu-id="807cc-102">SQL Server Extended Events Engine</span></span>
  <span data-ttu-id="807cc-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 扩展事件引擎是具有以下功能的服务和对象的集合：</span><span class="sxs-lookup"><span data-stu-id="807cc-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Extended Events engine is a collection of services and objects that:</span></span>  
  
-   <span data-ttu-id="807cc-104">可以定义事件。</span><span class="sxs-lookup"><span data-stu-id="807cc-104">Enable the definition of events.</span></span>  
  
-   <span data-ttu-id="807cc-105">可以处理事件数据。</span><span class="sxs-lookup"><span data-stu-id="807cc-105">Enable processing event data.</span></span>  
  
-   <span data-ttu-id="807cc-106">管理系统中的扩展事件服务和对象。</span><span class="sxs-lookup"><span data-stu-id="807cc-106">Manage Extended Events services and objects in the system.</span></span>  
  
-   <span data-ttu-id="807cc-107">维护扩展事件会话列表并管理对该列表的访问。</span><span class="sxs-lookup"><span data-stu-id="807cc-107">Maintain a list of Extended Events sessions and manage access to that list.</span></span>  
  
 <span data-ttu-id="807cc-108">扩展事件引擎本身并不提供任何事件，也不提供在事件激发时要采取的操作。</span><span class="sxs-lookup"><span data-stu-id="807cc-108">The Extended Events engine itself does not provide any events or actions to take when an event fires.</span></span> <span data-ttu-id="807cc-109">使用扩展事件引擎的进程定义与引擎之间的交互。</span><span class="sxs-lookup"><span data-stu-id="807cc-109">The processes that use the Extended Events engine define interaction with the engine.</span></span> <span data-ttu-id="807cc-110">这些进程用于添加事件点并提供为了响应事件激发而要采取的操作。</span><span class="sxs-lookup"><span data-stu-id="807cc-110">These processes add event points and supply the actions to take in response to event firing.</span></span>  
  
 <span data-ttu-id="807cc-111">下图是扩展事件会话的一个简化视图。</span><span class="sxs-lookup"><span data-stu-id="807cc-111">The following illustration shows a simplified view of an Extended Events session.</span></span> <span data-ttu-id="807cc-112">有关详细信息，请参阅 [SQL Server Extended Events Sessions](sql-server-extended-events-sessions.md)。</span><span class="sxs-lookup"><span data-stu-id="807cc-112">For more information, see [SQL Server Extended Events Sessions](sql-server-extended-events-sessions.md).</span></span>  
  
 <span data-ttu-id="807cc-113">![详细扩展事件体系结构](../../database-engine/media/xearchitecturedetailed.gif "详细扩展事件体系结构")</span><span class="sxs-lookup"><span data-stu-id="807cc-113">![Detailed extended events architecture](../../database-engine/media/xearchitecturedetailed.gif "Detailed extended events architecture")</span></span>  
  
 <span data-ttu-id="807cc-114">注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="807cc-114">Note the following:</span></span>  
  
-   <span data-ttu-id="807cc-115">每个 Windows 进程都可以有一个或多个模块（**Win32 进程**、 **Win32 模块**）。</span><span class="sxs-lookup"><span data-stu-id="807cc-115">Each Windows process can have one or more modules (**Win32 process**, **Win32 module**).</span></span> <span data-ttu-id="807cc-116">这些模块也称为“二进制模块” \*\* 或“可执行模块” \*\*。</span><span class="sxs-lookup"><span data-stu-id="807cc-116">These are also known as *binaries* or *executable modules*.</span></span>  
  
-   <span data-ttu-id="807cc-117">每个 Windows 进程模块都可以包含一个或多个扩展事件包（**包**），而扩展事件包则包含一个或多个扩展事件对象（**类型**、 **目标**、 **操作Action**、 **映射**、 **谓词**和 **事件**）。</span><span class="sxs-lookup"><span data-stu-id="807cc-117">Each of the Windows process modules can contain one or more Extended Events packages (**Package**), which contain one or more Extended Events objects (**Type**, **Target**, **Action**, **Map**, **Predicate**, and **Event**).</span></span>  
  
-   <span data-ttu-id="807cc-118">在主机进程中只能有一个扩展事件引擎实例（**扩展事件引擎**），该实例具有如下功能：</span><span class="sxs-lookup"><span data-stu-id="807cc-118">Inside a host process there can only be one instance of the Extended Events engine (**Extended event engine**), which:</span></span>  
  
    -   <span data-ttu-id="807cc-119">管理会话的某些方面（如枚举会话）。</span><span class="sxs-lookup"><span data-stu-id="807cc-119">Manages some aspects of the session (for example, enumerating sessions).</span></span>  
  
    -   <span data-ttu-id="807cc-120">处理调度（**调度程序**）。</span><span class="sxs-lookup"><span data-stu-id="807cc-120">Handles dispatching (**Dispatcher**).</span></span> <span data-ttu-id="807cc-121">这类似于线程池。</span><span class="sxs-lookup"><span data-stu-id="807cc-121">This is similar to a thread pool.</span></span>  
  
    -   <span data-ttu-id="807cc-122">处理事件的内存缓冲区（**缓冲区**）。</span><span class="sxs-lookup"><span data-stu-id="807cc-122">Handles memory buffers (**Buffer**) for events.</span></span> <span data-ttu-id="807cc-123">缓冲区在填充后将被分派给目标。</span><span class="sxs-lookup"><span data-stu-id="807cc-123">When buffers are filled, the buffers are dispatched to targets.</span></span>  
  
-   <span data-ttu-id="807cc-124">在创建会话并将事件绑定（可选）到该会话（**会话上下文**）之后：</span><span class="sxs-lookup"><span data-stu-id="807cc-124">After a session is created and events are optionally bound to the session (**Session context**):</span></span>  
  
    -   <span data-ttu-id="807cc-125">还可以创建目标实例（**目标实例**）并将其添加到会话中。</span><span class="sxs-lookup"><span data-stu-id="807cc-125">Instances of targets (**Target instance**) may be also be created and added to the session.</span></span>  
  
    -   <span data-ttu-id="807cc-126">缓冲区在填充后将被分派给目标。</span><span class="sxs-lookup"><span data-stu-id="807cc-126">When buffers are filled, those buffers are dispatched to targets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="807cc-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="807cc-127">See Also</span></span>  
 [<span data-ttu-id="807cc-128">扩展事件</span><span class="sxs-lookup"><span data-stu-id="807cc-128">Extended Events</span></span>](extended-events.md)  
  
  
