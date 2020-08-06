---
title: 监视事件和响应事件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- notifications [SQL Server], alert
- events [SQL Server], alerts
- alerts [SQL Server]
- notifications [SQL Server]
- events [SQL Server], automatically responding to
- administrator notifications [SQL Server Agent]
- automatic event responses
- SQL Server Agent alerts
- monitoring [SQL Server], events
- responding to events automatically
ms.assetid: f7fbe155-5b68-4777-bc71-a47637471f32
author: stevestein
ms.author: sstein
ms.openlocfilehash: afdf1beffd6099fce84f03a8ba65f7de9abb8f0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689238"
---
# <a name="monitor-and-respond-to-events"></a><span data-ttu-id="0eca2-102">监视事件和响应事件</span><span class="sxs-lookup"><span data-stu-id="0eca2-102">Monitor and Respond to Events</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0eca2-103">代理可监视并自动响应*事件*，例如来自 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的消息、特定性能条件以及 Windows Management Instrumentation (WMI) 事件。</span><span class="sxs-lookup"><span data-stu-id="0eca2-103">Agent can monitor and automatically respond to *events*, such as messages from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], specific performance conditions, and Windows Management Instrumentation (WMI) events.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0eca2-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="0eca2-104">In This Section</span></span>  
 [<span data-ttu-id="0eca2-105">警报</span><span class="sxs-lookup"><span data-stu-id="0eca2-105">Alerts</span></span>](alerts.md)  
 <span data-ttu-id="0eca2-106">介绍了命名警报以及选择警报响应的事件或性能条件。</span><span class="sxs-lookup"><span data-stu-id="0eca2-106">Contains information about naming an alert and selecting the events or performance conditions to which alerts respond.</span></span>  
  
 [<span data-ttu-id="0eca2-107">创建用户定义事件</span><span class="sxs-lookup"><span data-stu-id="0eca2-107">Create a User-Defined Event</span></span>](create-a-user-defined-event.md)  
 <span data-ttu-id="0eca2-108">介绍了如何创建由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]预定义的事件以外的事件。</span><span class="sxs-lookup"><span data-stu-id="0eca2-108">Contains information about how to create events other than those that are predefined by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="0eca2-109">运算符</span><span class="sxs-lookup"><span data-stu-id="0eca2-109">Operators</span></span>](operators.md)  
 <span data-ttu-id="0eca2-110">介绍了为管理员创建 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理可用于在作业失败或成功时用来发送通知的别名。</span><span class="sxs-lookup"><span data-stu-id="0eca2-110">Contains information about creating aliases for administrators that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can use to send notifications when jobs fail or succeed.</span></span>  
  
## <a name="about-monitoring-and-responding-to-events"></a><span data-ttu-id="0eca2-111">关于监视事件和响应事件</span><span class="sxs-lookup"><span data-stu-id="0eca2-111">About Monitoring and Responding to Events</span></span>  
 <span data-ttu-id="0eca2-112">对事件的自动响应称为“警报”\*\*。</span><span class="sxs-lookup"><span data-stu-id="0eca2-112">Automated responses to events are called *alerts*.</span></span> <span data-ttu-id="0eca2-113">您可以针对一个或多个事件定义警报，指定希望 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理如何响应发生的这些事件。</span><span class="sxs-lookup"><span data-stu-id="0eca2-113">You can define an alert on one or more events to specify how you want [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to respond to their occurrence.</span></span> <span data-ttu-id="0eca2-114">警报可以通过通知管理员和/或运行某项作业来响应事件。</span><span class="sxs-lookup"><span data-stu-id="0eca2-114">An alert can respond to an event by notifying an administrator or running a job, or both.</span></span> <span data-ttu-id="0eca2-115">警报还可以将事件转发到其他计算机上的 Microsoft Windows 应用程序日志。</span><span class="sxs-lookup"><span data-stu-id="0eca2-115">An alert can also forward an event to the Microsoft Windows application log on a different computer.</span></span> <span data-ttu-id="0eca2-116">例如，您可以指定在发生严重性为 19 的事件时立即通知操作员。</span><span class="sxs-lookup"><span data-stu-id="0eca2-116">For example, you can specify that an operator be notified immediately if an event of severity 19 occurs.</span></span> <span data-ttu-id="0eca2-117">通过定义警报，数据库管理员可以更有效地监视和管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0eca2-117">By defining alerts, database administrators can more effectively monitor and manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0eca2-118">代理只响应定义了警报的事件。</span><span class="sxs-lookup"><span data-stu-id="0eca2-118">Agent only responds to events for which an alert is defined.</span></span> <span data-ttu-id="0eca2-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理用来监视事件的方法取决于事件的类型。</span><span class="sxs-lookup"><span data-stu-id="0eca2-119">The method that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent uses to monitor events depends on the type of event.</span></span>  
  
 <span data-ttu-id="0eca2-120">当为一个性能计数器定义了一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理警报后， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理将直接监视该性能计数器。</span><span class="sxs-lookup"><span data-stu-id="0eca2-120">When a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert is defined for a performance counter, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent directly monitors the performance counter.</span></span> <span data-ttu-id="0eca2-121">对于 WMI 事件， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理为 WMI 事件注册一个事件查询。</span><span class="sxs-lookup"><span data-stu-id="0eca2-121">For a WMI event, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent registers an event query for the WMI event.</span></span>  
  
 <span data-ttu-id="0eca2-122">为了响应来自 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的消息， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理会监视 Windows 应用程序日志。</span><span class="sxs-lookup"><span data-stu-id="0eca2-122">To respond to messages from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent monitors the Windows application log.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0eca2-123">代理只能响应此日志中出现的消息。</span><span class="sxs-lookup"><span data-stu-id="0eca2-123">Agent can only respond to messages that appear in this log.</span></span> <span data-ttu-id="0eca2-124">默认情况下，SQL Server 将下列消息记录在 Windows 应用程序日志中：</span><span class="sxs-lookup"><span data-stu-id="0eca2-124">By default, SQL Server logs the following messages in the Windows application log:</span></span>  
  
-   <span data-ttu-id="0eca2-125">严重性为 19 或更高的 sysmessages 错误。</span><span class="sxs-lookup"><span data-stu-id="0eca2-125">Severity 19 or higher sysmessages errors.</span></span>  
  
     <span data-ttu-id="0eca2-126">如果您还希望记录严重性低于 19 的特定 sysmessages 错误，请使用 sp_altermessage 存储过程将这类错误指定为“始终记录”。</span><span class="sxs-lookup"><span data-stu-id="0eca2-126">If you also want to log specific sysmessages errors that have a severity lower than 19, use the sp_altermessage stored procedure to designate such errors as "always logged".</span></span>  
  
-   <span data-ttu-id="0eca2-127">所有使用 WITH LOG 语法调用的 RAISERROR 语句。</span><span class="sxs-lookup"><span data-stu-id="0eca2-127">Any RAISERROR statement invoked by using the WITH LOG syntax.</span></span>  
  
     <span data-ttu-id="0eca2-128">建议使用 RAISERROR WITH LOG 将 SQL Server 实例的相关信息写入 Windows 应用程序日志。</span><span class="sxs-lookup"><span data-stu-id="0eca2-128">Using RAISERROR WITH LOG is the recommended way to write to the Windows application log from an instance of SQL Server.</span></span>  
  
-   <span data-ttu-id="0eca2-129">所有使用 xp_logevent 记录的应用程序事件。</span><span class="sxs-lookup"><span data-stu-id="0eca2-129">Any application event that is logged by using xp_logevent.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0eca2-130">记录应用程序事件会占用日志空间，并导致 Windows 应用程序日志超出其最大大小。</span><span class="sxs-lookup"><span data-stu-id="0eca2-130">Logging application events consumes log space and can cause the Windows application log to exceed its maximum size.</span></span> <span data-ttu-id="0eca2-131">请确保 Windows 应用程序日志最大大小足够大，以免丢失 SQL Server 事件信息。</span><span class="sxs-lookup"><span data-stu-id="0eca2-131">Make sure that the maximum Windows application log size is large enough to avoid loss of SQL Server event information.</span></span>  
  
 <span data-ttu-id="0eca2-132">当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 记录消息时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服务将该消息与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理员定义的警报进行比较。</span><span class="sxs-lookup"><span data-stu-id="0eca2-132">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logs a message, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service compares the message against the alerts defined by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrator.</span></span>  
  
 <span data-ttu-id="0eca2-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服务通过执行事件警报中指定的任务来响应事件，而不管事件的源是什么。</span><span class="sxs-lookup"><span data-stu-id="0eca2-133">Regardless of the source of the event, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service responds to the event by performing the tasks specified in the alert for the event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eca2-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0eca2-134">See Also</span></span>  
 [<span data-ttu-id="0eca2-135">sp_altermessage &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="0eca2-135">sp_altermessage &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-altermessage-transact-sql)  
  
  
