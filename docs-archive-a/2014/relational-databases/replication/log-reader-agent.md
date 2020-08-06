---
title: 日志读取器代理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.logreaderagent.f1
helpviewer_keywords:
- Log Reader Agent dialog box
ms.assetid: 300a3c46-0e48-4334-99c0-9ee690d2ef4f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2b908e43cf97350fee2913e8cc6bab30a1bcd0dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692840"
---
# <a name="log-reader-agent"></a><span data-ttu-id="12ff8-102">日志读取器代理</span><span class="sxs-lookup"><span data-stu-id="12ff8-102">Log Reader Agent</span></span>
  <span data-ttu-id="12ff8-103">**“日志读取器代理”** 对话框显示有关日志读取器代理的详细信息，包括状态、历史记录、信息性消息和所有错误消息。</span><span class="sxs-lookup"><span data-stu-id="12ff8-103">The **Log Reader Agent** dialog box displays detailed information on the Log Reader Agent, including status, history, informational messages, and any error messages.</span></span>  
  
## <a name="options"></a><span data-ttu-id="12ff8-104">选项</span><span class="sxs-lookup"><span data-stu-id="12ff8-104">Options</span></span>  
 <span data-ttu-id="12ff8-105">从 **“视图”** 菜单中选择要查看的日志读取器代理会话，然后在标记为 **“日志读取器代理的会话”** 的网格中选择特定的会话。</span><span class="sxs-lookup"><span data-stu-id="12ff8-105">Select which Log Reader Agent sessions to view from the **View** menu, and then select a specific session in the grid labeled **Sessions of the Log Reader Agent**.</span></span> <span data-ttu-id="12ff8-106">有关此会话的详细信息显示在标记为 **“所选会话中的操作”** 的网格中。</span><span class="sxs-lookup"><span data-stu-id="12ff8-106">Detailed information on this session is displayed in the grid labeled **Actions in the selected session**.</span></span> <span data-ttu-id="12ff8-107">如果所选会话由于出错而结束，则还将显示一个标记为 **“所选会话的错误详细信息或消息”** 的文本区域。</span><span class="sxs-lookup"><span data-stu-id="12ff8-107">If the selected session ended in an error, the text area labeled **Error details or message of the selected session** is also displayed.</span></span>  
  
 <span data-ttu-id="12ff8-108">**视图**</span><span class="sxs-lookup"><span data-stu-id="12ff8-108">**View**</span></span>  
 <span data-ttu-id="12ff8-109">选择要查看的日志读取器代理会话。</span><span class="sxs-lookup"><span data-stu-id="12ff8-109">Select which Log Reader Agent sessions to view.</span></span> <span data-ttu-id="12ff8-110">日志读取器代理通常连续运行，因此可能只有一个可供查看的会话。</span><span class="sxs-lookup"><span data-stu-id="12ff8-110">The Log Reader Agent typically runs continuously, therefore there might be only one session to view.</span></span>  
  
 <span data-ttu-id="12ff8-111">**Status**</span><span class="sxs-lookup"><span data-stu-id="12ff8-111">**Status**</span></span>  
 <span data-ttu-id="12ff8-112">日志读取器代理的状态。</span><span class="sxs-lookup"><span data-stu-id="12ff8-112">The status of the Log Reader Agent.</span></span> <span data-ttu-id="12ff8-113">下面列出了可能的状态值：</span><span class="sxs-lookup"><span data-stu-id="12ff8-113">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="12ff8-114">错误</span><span class="sxs-lookup"><span data-stu-id="12ff8-114">Error</span></span>  
  
-   <span data-ttu-id="12ff8-115">正在重试失败的命令</span><span class="sxs-lookup"><span data-stu-id="12ff8-115">Retrying failed commands</span></span>  
  
-   <span data-ttu-id="12ff8-116">未运行</span><span class="sxs-lookup"><span data-stu-id="12ff8-116">Not running</span></span>  
  
-   <span data-ttu-id="12ff8-117">正在运行</span><span class="sxs-lookup"><span data-stu-id="12ff8-117">Running</span></span>  
  
 <span data-ttu-id="12ff8-118">**Start Time**</span><span class="sxs-lookup"><span data-stu-id="12ff8-118">**Start Time**</span></span>  
 <span data-ttu-id="12ff8-119">会话的开始时间。</span><span class="sxs-lookup"><span data-stu-id="12ff8-119">The start time of the session.</span></span>  
  
 <span data-ttu-id="12ff8-120">**结束时间**</span><span class="sxs-lookup"><span data-stu-id="12ff8-120">**End Time**</span></span>  
 <span data-ttu-id="12ff8-121">会话的结束时间。</span><span class="sxs-lookup"><span data-stu-id="12ff8-121">The end time of the session.</span></span> <span data-ttu-id="12ff8-122">如果代理尚未停止，此字段为空。</span><span class="sxs-lookup"><span data-stu-id="12ff8-122">If the agent has not stopped, this field is empty.</span></span>  
  
 <span data-ttu-id="12ff8-123">**Duration**</span><span class="sxs-lookup"><span data-stu-id="12ff8-123">**Duration**</span></span>  
 <span data-ttu-id="12ff8-124">日志读取器代理已在此会话中运行的时间。</span><span class="sxs-lookup"><span data-stu-id="12ff8-124">The amount of time the Log Reader Agent has run in this session.</span></span> <span data-ttu-id="12ff8-125">如果代理当前正在运行，该时间表示已用时间；如果代理会话已经结束，则该时间表示会话的总时间。</span><span class="sxs-lookup"><span data-stu-id="12ff8-125">The time represents elapsed time if the agent is currently running and the total time of the session if the agent session has ended.</span></span>  
  
 <span data-ttu-id="12ff8-126">**错误消息**</span><span class="sxs-lookup"><span data-stu-id="12ff8-126">**Error Message**</span></span>  
 <span data-ttu-id="12ff8-127">如果会话由于出错而结束，此字段将显示日志读取器代理记录的上一条错误消息。</span><span class="sxs-lookup"><span data-stu-id="12ff8-127">If a session ended in an error, this field displays the last error message logged by the Log Reader Agent.</span></span> <span data-ttu-id="12ff8-128">如果某会话未因出错而结束，此字段为空白。</span><span class="sxs-lookup"><span data-stu-id="12ff8-128">If a session did not end in an error, this field is blank.</span></span>  
  
 <span data-ttu-id="12ff8-129">**操作消息**</span><span class="sxs-lookup"><span data-stu-id="12ff8-129">**Action Message**</span></span>  
 <span data-ttu-id="12ff8-130">日志读取器代理在所选会话期间记录的所有信息性消息和错误消息。</span><span class="sxs-lookup"><span data-stu-id="12ff8-130">All informational messages and error messages that the Log Reader Agent has logged during the selected session.</span></span>  
  
 <span data-ttu-id="12ff8-131">**操作时间**</span><span class="sxs-lookup"><span data-stu-id="12ff8-131">**Action Time**</span></span>  
 <span data-ttu-id="12ff8-132">执行 **“操作消息”** 列中所述操作的时间。</span><span class="sxs-lookup"><span data-stu-id="12ff8-132">The time at which the action described in the **Action Message** column was performed.</span></span>  
  
 <span data-ttu-id="12ff8-133">**“所选会话的错误详细信息或消息”**</span><span class="sxs-lookup"><span data-stu-id="12ff8-133">**Error details or message of the selected session**</span></span>  
 <span data-ttu-id="12ff8-134">只有当所选会话在 **“状态”** 列中显示 **“错误”** 值时，才会显示此项。</span><span class="sxs-lookup"><span data-stu-id="12ff8-134">Displayed only if the selected session displays a value of **Error** in the **Status** column.</span></span> <span data-ttu-id="12ff8-135">此文本区域显示详细错误信息以及出错时尝试执行的命令。</span><span class="sxs-lookup"><span data-stu-id="12ff8-135">This text area displays detailed error information and the command that was attempted at the time of the error.</span></span> <span data-ttu-id="12ff8-136">另外，还包括指向与该错误相关的其他内容的链接。</span><span class="sxs-lookup"><span data-stu-id="12ff8-136">It also includes links to additional content related to the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12ff8-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="12ff8-137">See Also</span></span>  
 <span data-ttu-id="12ff8-138">[启动复制监视器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="12ff8-138">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="12ff8-139">[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="12ff8-139">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="12ff8-140">[监视复制](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="12ff8-140">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="12ff8-141">复制代理概述</span><span class="sxs-lookup"><span data-stu-id="12ff8-141">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
