---
title: SQL Server 代理属性（“高级”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.advanced.f1
ms.assetid: a4d798ee-4c18-40d4-b6af-63d17503738c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8ec0d9d7fbd51f9350bf692588f90c292e54f4e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590012"
---
# <a name="sql-server-agent-properties-advanced-page"></a><span data-ttu-id="cdeb1-102">SQL Server 代理属性（“高级”页）</span><span class="sxs-lookup"><span data-stu-id="cdeb1-102">SQL Server Agent Properties (Advanced Page)</span></span>
  <span data-ttu-id="cdeb1-103">使用此页可以查看和修改代理服务的高级属性 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cdeb1-103">Use this page to view and modify advanced properties of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="cdeb1-104">选项</span><span class="sxs-lookup"><span data-stu-id="cdeb1-104">Options</span></span>  
 <span data-ttu-id="cdeb1-105">**SQL Server 事件转发**</span><span class="sxs-lookup"><span data-stu-id="cdeb1-105">**SQL Server event forwarding**</span></span>  
 <span data-ttu-id="cdeb1-106">此类别中的选项可用来激活和配置事件转发功能。</span><span class="sxs-lookup"><span data-stu-id="cdeb1-106">The options in this category activate and configure event forwarding.</span></span>  
  
 <span data-ttu-id="cdeb1-107">**将事件转发到其他服务器**</span><span class="sxs-lookup"><span data-stu-id="cdeb1-107">**Forward events to a different server**</span></span>  
 <span data-ttu-id="cdeb1-108">将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理事件转发到其他服务器。</span><span class="sxs-lookup"><span data-stu-id="cdeb1-108">Forwards [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent events to a different server.</span></span>  
  
 <span data-ttu-id="cdeb1-109">**Server**</span><span class="sxs-lookup"><span data-stu-id="cdeb1-109">**Server**</span></span>  
 <span data-ttu-id="cdeb1-110">选择要将事件转发到的服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="cdeb1-110">Select the name of the server to forward events to.</span></span>  
  
 <span data-ttu-id="cdeb1-111">**未处理的事件**</span><span class="sxs-lookup"><span data-stu-id="cdeb1-111">**Unhandled events**</span></span>  
 <span data-ttu-id="cdeb1-112">仅将未处理的事件转发到指定的服务器。</span><span class="sxs-lookup"><span data-stu-id="cdeb1-112">Forwards only unhandled events to the specified server.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cdeb1-113">代理仅转发警报未对其响应的事件。</span><span class="sxs-lookup"><span data-stu-id="cdeb1-113">Agent forwards only events that no alert responds to.</span></span>  
  
 <span data-ttu-id="cdeb1-114">**所有事件**</span><span class="sxs-lookup"><span data-stu-id="cdeb1-114">**All events**</span></span>  
 <span data-ttu-id="cdeb1-115">转发所有事件。</span><span class="sxs-lookup"><span data-stu-id="cdeb1-115">Forwards all events.</span></span> <span data-ttu-id="cdeb1-116">当本地实例中的某个警报响应该事件时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理将转发该事件并处理此警报。</span><span class="sxs-lookup"><span data-stu-id="cdeb1-116">When an alert in the local instance responds to the event, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agent will both forward the event and process the alert.</span></span>  
  
 <span data-ttu-id="cdeb1-117">**如果事件的严重性不低于**</span><span class="sxs-lookup"><span data-stu-id="cdeb1-117">**If event has severity at or above**</span></span>  
 <span data-ttu-id="cdeb1-118">仅转发严重级别不低于指定级别的事件。</span><span class="sxs-lookup"><span data-stu-id="cdeb1-118">Forwards only events with a severity level at or above the level specified.</span></span>  
  
 <span data-ttu-id="cdeb1-119">**空闲 CPU 条件**</span><span class="sxs-lookup"><span data-stu-id="cdeb1-119">**Idle CPU Condition**</span></span>  
 <span data-ttu-id="cdeb1-120">此类别中的选项定义一些条件，在这些条件下， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理运行那些“空闲 CPU”计划安排的作业。</span><span class="sxs-lookup"><span data-stu-id="cdeb1-120">The options in this category define the conditions under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent runs jobs scheduled to run on the Idle CPU schedule.</span></span>  
  
 <span data-ttu-id="cdeb1-121">**定义空闲 CPU 条件**</span><span class="sxs-lookup"><span data-stu-id="cdeb1-121">**Define idle CPU condition**</span></span>  
 <span data-ttu-id="cdeb1-122">定义 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理认为 CPU 处于空闲状态的条件。</span><span class="sxs-lookup"><span data-stu-id="cdeb1-122">Defines the conditions under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent considers the CPU to be idle.</span></span>  
  
 <span data-ttu-id="cdeb1-123">**CPU 平均使用率低于**</span><span class="sxs-lookup"><span data-stu-id="cdeb1-123">**Average CPU usage falls below**</span></span>  
 <span data-ttu-id="cdeb1-124">CPU 平均使用率，在低于该使用率时，CPU 被认为处于空闲状态。</span><span class="sxs-lookup"><span data-stu-id="cdeb1-124">Percentage of CPU usage below which the CPU is considered to be idle.</span></span>  
  
 <span data-ttu-id="cdeb1-125">**并且保持低于此级别**</span><span class="sxs-lookup"><span data-stu-id="cdeb1-125">**And remains below this level for**</span></span>  
 <span data-ttu-id="cdeb1-126">CPU 平均占用时间量必须低于指定的级别， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理才可按照“空闲 CPU”计划运行作业。</span><span class="sxs-lookup"><span data-stu-id="cdeb1-126">Amount of time that the average CPU must below the level specified before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent runs jobs on the Idle CPU schedule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdeb1-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cdeb1-127">See Also</span></span>  
 <span data-ttu-id="cdeb1-128">[创建计划并将计划附加到作业](create-and-attach-schedules-to-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="cdeb1-128">[Create and Attach Schedules to Jobs](create-and-attach-schedules-to-jobs.md) </span></span>  
 [<span data-ttu-id="cdeb1-129">管理事件</span><span class="sxs-lookup"><span data-stu-id="cdeb1-129">Manage Events</span></span>](manage-events.md)  
  
  
