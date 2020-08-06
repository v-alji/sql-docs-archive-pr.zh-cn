---
title: 广播关闭消息（命令提示符）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server, stopping
- named instances [SQL Server], broadcasting shutdown messages
- shutdown message broadcast
- broadcasting shutdown message
- command prompt [SQL Server], broadcasting shutdown messages
- default instances [SQL Server], broadcasting shutdown messages
- stopping SQL Server
ms.assetid: 9f20ccd5-d952-431d-ba12-339911af9430
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 540baada4a78d7b5caf54cbabb9196ce5a79780e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690138"
---
# <a name="broadcast-a-shutdown-message-command-prompt"></a><span data-ttu-id="3a6f3-102">广播关闭消息（命令提示符）</span><span class="sxs-lookup"><span data-stu-id="3a6f3-102">Broadcast a Shutdown Message (Command Prompt)</span></span>
  <span data-ttu-id="3a6f3-103">本主题介绍了如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] net send **命令在** 中广播关闭消息。</span><span class="sxs-lookup"><span data-stu-id="3a6f3-103">This topic describes how to broadcast a shutdown message in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using the **net send** command.</span></span> <span data-ttu-id="3a6f3-104">在消息中，包括 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例将停止的时间，以便用户可以及时完成任务。</span><span class="sxs-lookup"><span data-stu-id="3a6f3-104">In the message, include the time the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will be stopped so that users can finish their tasks.</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-broadcast-a-shutdown-message"></a><span data-ttu-id="3a6f3-105">广播关闭消息</span><span class="sxs-lookup"><span data-stu-id="3a6f3-105">To broadcast a shutdown message</span></span>  
  
1.  <span data-ttu-id="3a6f3-106">从命令提示符输入以下命令：</span><span class="sxs-lookup"><span data-stu-id="3a6f3-106">From a command prompt, enter:</span></span>  
  
     <span data-ttu-id="3a6f3-107">**net send /users "message"**</span><span class="sxs-lookup"><span data-stu-id="3a6f3-107">**net send /users "message"**</span></span>  
  
     <span data-ttu-id="3a6f3-108">**/users** 选项指定将消息发送给已连接到服务器的所有用户</span><span class="sxs-lookup"><span data-stu-id="3a6f3-108">The **/users** option specifies that the message be sent to all users connected to the server</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3a6f3-109">**net send** 命令要求在发送和接收计算机上同时运行信使服务。</span><span class="sxs-lookup"><span data-stu-id="3a6f3-109">The **net send** command requires the messenger service to be running on both the sending and the receiving computers.</span></span> <span data-ttu-id="3a6f3-110">该 Messenger 服务默认情况下在 Windows Server 2003 上被禁用。</span><span class="sxs-lookup"><span data-stu-id="3a6f3-110">The messenger service is disabled by default on Windows Server 2003.</span></span> <span data-ttu-id="3a6f3-111">有关 **net send**的信息，请参阅 Windows 文档。</span><span class="sxs-lookup"><span data-stu-id="3a6f3-111">For information about **net send**, see the Windows documentation.</span></span>  
  
 <span data-ttu-id="3a6f3-112">在网络上，可能更适合通过电子邮件或电话与用户联系。</span><span class="sxs-lookup"><span data-stu-id="3a6f3-112">On your network, it may be more appropriate to contact users by e-mail or the telephone.</span></span> <span data-ttu-id="3a6f3-113">若要确定当前哪些用户连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，请使用活动监视器。</span><span class="sxs-lookup"><span data-stu-id="3a6f3-113">To determine which users are currently connected to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], use the Activity Monitor.</span></span> <span data-ttu-id="3a6f3-114">有关活动监视器的信息，请参阅[活动监视器](../../relational-databases/performance-monitor/activity-monitor.md) 和[打开活动监视器 (SQL Server Management Studio)](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="3a6f3-114">For information on the Activity Monitor, see [Activity Monitor](../../relational-databases/performance-monitor/activity-monitor.md) and [Open Activity Monitor &#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a6f3-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3a6f3-115">See Also</span></span>  
 [<span data-ttu-id="3a6f3-116">启动、停止、暂停、继续、重新启动数据库引擎、SQL Server 代理或 SQL Server Browser 服务</span><span class="sxs-lookup"><span data-stu-id="3a6f3-116">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>](start-stop-pause-resume-restart-sql-server-services.md)  
  
  
