---
title: 获取有关事件通知的信息 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- event notifications [SQL Server], metadata
- status information [SQL Server], event notifications
- metadata [SQL Server], event notifications
ms.assetid: 8bc10867-66d6-4f57-ac32-a6c29f3327cd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c8d8271b6279910321058d01c7b2f96b1df62bd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689815"
---
# <a name="get-information-about-event-notifications"></a><span data-ttu-id="f1357-102">获取有关事件通知的信息</span><span class="sxs-lookup"><span data-stu-id="f1357-102">Get Information About Event Notifications</span></span>
  <span data-ttu-id="f1357-103">下列目录视图可用于查询有关事件通知的元数据。</span><span class="sxs-lookup"><span data-stu-id="f1357-103">The following catalog views are available to query metadata about event notifications.</span></span>  
  
 <span data-ttu-id="f1357-104">**获取有关非服务器级别事件通知的信息**</span><span class="sxs-lookup"><span data-stu-id="f1357-104">**To get information about nonserver-level event notifications**</span></span>  
  
-   [<span data-ttu-id="f1357-105">sys.event_notifications (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f1357-105">sys.event_notifications &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-event-notifications-transact-sql)  
  
> [!NOTE]  
>  <span data-ttu-id="f1357-106">若要查看 **sys.event_notifications** 中在数据库级别创建的任意事件通知的元数据，至少必须满足下列条件：对数据库具有 CONTROL、ALTER、TAKE OWNERSHIP 或 VIEW DEFINITION 权限，是事件通知的所有者，或者具有 ALTER ANY DATABASE EVENT NOTIFICATION 权限。</span><span class="sxs-lookup"><span data-stu-id="f1357-106">To view metadata about any event notification in **sys.event_notifications** created at the database level, at the minimum you must have the following: CONTROL, ALTER, TAKE OWNERSHIP, or VIEW DEFINITION permission on the database, be the owner of the event notification, or have ALTER ANY DATABASE EVENT NOTIFICATION permission.</span></span> <span data-ttu-id="f1357-107">对于对特定队列创建的事件通知，至少必须满足下列条件：对对象具有 CONTROL、ALTER、TAKE OWNERSHIP 或 VIEW DEFINITION 权限，是事件通知的所有者，或者具有 ALTER ANY DATABASE EVENT NOTIFICATION 权限。</span><span class="sxs-lookup"><span data-stu-id="f1357-107">For event notifications created on a specific queue, at the minimum you must have the following: CONTROL, ALTER, TAKE OWNERSHIP, or VIEW DEFINITION permission on the object, be the owner of the event notification, or have ALTER ANY DATABASE EVENT NOTIFICATION permission.</span></span>  
  
 <span data-ttu-id="f1357-108">**获取有关服务器级别事件通知的信息**</span><span class="sxs-lookup"><span data-stu-id="f1357-108">**To get information about server-level event notifications**</span></span>  
  
-   [<span data-ttu-id="f1357-109">sys.server_event_notifications (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f1357-109">sys.server_event_notifications &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql)  
  
> [!NOTE]  
>  <span data-ttu-id="f1357-110">至少必须满足下列条件：对服务器具有 CONTROL 或 VIEW ANY DEFINITION 权限，是事件通知的登录者或所有者，或者具有查看 **sys.server_event_notifications**中的任何事件通知的元数据的 ALTER ANY EVENT NOTIFICATION 权限。</span><span class="sxs-lookup"><span data-stu-id="f1357-110">At the minimum, you must have the following: CONTROL or VIEW ANY DEFINITION permission on the server, be the logon or owner of the event notification, or have ALTER ANY EVENT NOTIFICATION permission to view metadata about any event notification in **sys.server_event_notifications**.</span></span>  
  
 <span data-ttu-id="f1357-111">**获取有关可以激发事件通知的所有事件的信息**</span><span class="sxs-lookup"><span data-stu-id="f1357-111">**To get information about all events that can fire event notifications**</span></span>  
  
-   [<span data-ttu-id="f1357-112">sys.event_notification_event_types (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f1357-112">sys.event_notification_event_types &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-event-notification-event-types-transact-sql)  
  
> [!NOTE]  
>  <span data-ttu-id="f1357-113">此目录视图不返回事件组。</span><span class="sxs-lookup"><span data-stu-id="f1357-113">This catalog view does not return event groups.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1357-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f1357-114">See Also</span></span>  
 [<span data-ttu-id="f1357-115">事件通知</span><span class="sxs-lookup"><span data-stu-id="f1357-115">Event Notifications</span></span>](event-notifications.md)  
  
  
