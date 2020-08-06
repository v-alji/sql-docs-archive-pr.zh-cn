---
title: 创建用户定义事件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent alerts, user-defined events
- user-defined events [SQL Server]
- multiple language support [SQL Server], alerts
- languages [SQL Server], alerts
- severity levels [SQL Server]
- global considerations [SQL Server], alerts
- events [SQL Server], user-defined
- SQL Server Agent alerts, multiple-language environments
- alerts [SQL Server], user-defined events
- alerts [SQL Server], multiple-language environments
- custom events [SQL Server Agent]
- international considerations [SQL Server], alerts
ms.assetid: 03d71a35-97fa-4bba-aa9a-23ac9c9cf879
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2323dc4da3d1a8a67dad41ea189877ade25eff0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694210"
---
# <a name="create-a-user-defined-event"></a><span data-ttu-id="3ccb4-102">创建用户定义事件</span><span class="sxs-lookup"><span data-stu-id="3ccb4-102">Create a User-Defined Event</span></span>
  <span data-ttu-id="3ccb4-103">如果需要监视非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 预定义的事件，可以创建用户定义事件。</span><span class="sxs-lookup"><span data-stu-id="3ccb4-103">You can create user-defined events if you want to monitor events other than events that are predefined by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3ccb4-104">还可以为每个用户定义事件指定严重级别。</span><span class="sxs-lookup"><span data-stu-id="3ccb4-104">You can also assign a severity level to each user-defined event.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ccb4-105">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 时，请为每个用户定义事件消息选择“写入 Windows 应用程序事件日志”\*\*\*\* 选项，以确保记录该消息。</span><span class="sxs-lookup"><span data-stu-id="3ccb4-105">When using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the **Write to Windows application event log** option for each user-defined event message, to ensure that the messages are logged.</span></span> <span data-ttu-id="3ccb4-106">默认情况下，出现严重级别低于 19 的用户定义消息时，不会将其发送到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 应用程序日志。</span><span class="sxs-lookup"><span data-stu-id="3ccb4-106">By default, user-defined messages of severity lower than 19 are not sent to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application log when they occur.</span></span> <span data-ttu-id="3ccb4-107">因此严重级别低于 19 的用户定义消息不会触发 SQL Server 代理警报。</span><span class="sxs-lookup"><span data-stu-id="3ccb4-107">User-defined messages of severity lower than 19 therefore do not trigger SQL Server Agent alerts.</span></span>  
  
 <span data-ttu-id="3ccb4-108">用户定义事件必须具有唯一的消息号。</span><span class="sxs-lookup"><span data-stu-id="3ccb4-108">User-defined events must have a unique message number.</span></span> <span data-ttu-id="3ccb4-109">用户定义事件的消息号必须大于 50,000。</span><span class="sxs-lookup"><span data-stu-id="3ccb4-109">Message numbers for a user-defined event must be greater than 50,000.</span></span> <span data-ttu-id="3ccb4-110">可以使用多种语言来定义事件的消息。</span><span class="sxs-lookup"><span data-stu-id="3ccb4-110">You can define messages for the event in multiple languages.</span></span> <span data-ttu-id="3ccb4-111">但是，在添加其他语言的错误消息之前， **En-US** 错误消息必须已经存在。</span><span class="sxs-lookup"><span data-stu-id="3ccb4-111">However, an **En-US** error message must exist before messages in other languages can be added.</span></span>  
  
 <span data-ttu-id="3ccb4-112">如果管理的是多语言 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 环境，可以使用所支持的每种语言来创建用户定义的消息。</span><span class="sxs-lookup"><span data-stu-id="3ccb4-112">If you administer a multiple-language [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] environment, create user-defined messages in each of the languages that are supported.</span></span> <span data-ttu-id="3ccb4-113">例如，若要创建一个既用于英语服务器又用于德语服务器的新事件消息，可以在两个服务器上使用相同的消息号和严重级别，但为每个服务器指定不同的语言。</span><span class="sxs-lookup"><span data-stu-id="3ccb4-113">For example, if you are creating a new event message to be used on both an English and a German server, use the same message number and severity for both, but assign a different language to each.</span></span>  
  
 <span data-ttu-id="3ccb4-114">下列任务介绍了如何创建用户定义事件以及响应这些事件的警报：</span><span class="sxs-lookup"><span data-stu-id="3ccb4-114">The following tasks provide information about how to create user-defined events and alerts that respond to them:</span></span>  
  
 <span data-ttu-id="3ccb4-115">**基于消息号创建警报**</span><span class="sxs-lookup"><span data-stu-id="3ccb4-115">**To create an alert based on a message number**</span></span>  
  
-   [<span data-ttu-id="3ccb4-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3ccb4-116">SQL Server Management Studio</span></span>](create-an-alert-using-an-error-number.md)  
  
-   [<span data-ttu-id="3ccb4-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3ccb4-117">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 <span data-ttu-id="3ccb4-118">**基于严重级别创建警报**</span><span class="sxs-lookup"><span data-stu-id="3ccb4-118">**To create an alert based on severity levels**</span></span>  
  
-   [<span data-ttu-id="3ccb4-119">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3ccb4-119">SQL Server Management Studio</span></span>](create-an-alert-using-severity-level.md)  
  
-   [<span data-ttu-id="3ccb4-120">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3ccb4-120">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 <span data-ttu-id="3ccb4-121">**定义对警报的响应**</span><span class="sxs-lookup"><span data-stu-id="3ccb4-121">**To define the response to an alert**</span></span>  
  
-   [<span data-ttu-id="3ccb4-122">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3ccb4-122">SQL Server Management Studio</span></span>](../sql-server-management-studio-ssms.md)  
  
-   [<span data-ttu-id="3ccb4-123">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3ccb4-123">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)  
  
 <span data-ttu-id="3ccb4-124">**创建用户定义事件的错误消息**</span><span class="sxs-lookup"><span data-stu-id="3ccb4-124">**To create a user-defined event error message**</span></span>  
  
-   [<span data-ttu-id="3ccb4-125">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3ccb4-125">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-addmessage-transact-sql)  
  
 <span data-ttu-id="3ccb4-126">**修改用户定义事件的错误消息**</span><span class="sxs-lookup"><span data-stu-id="3ccb4-126">**To modify a user-defined event error message**</span></span>  
  
-   [<span data-ttu-id="3ccb4-127">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3ccb4-127">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-altermessage-transact-sql)  
  
 <span data-ttu-id="3ccb4-128">**删除用户定义事件的错误消息**</span><span class="sxs-lookup"><span data-stu-id="3ccb4-128">**To delete a user-defined event error message**</span></span>  
  
-   [<span data-ttu-id="3ccb4-129">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3ccb4-129">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropmessage-transact-sql)  
  
 <span data-ttu-id="3ccb4-130">**禁用或重新激活警报**</span><span class="sxs-lookup"><span data-stu-id="3ccb4-130">**To disable or reactivate an alert**</span></span>  
  
-   [<span data-ttu-id="3ccb4-131">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3ccb4-131">SQL Server Management Studio</span></span>](disable-or-reactivate-an-alert.md)  
  
-   [<span data-ttu-id="3ccb4-132">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3ccb4-132">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="3ccb4-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3ccb4-133">See Also</span></span>  
 [<span data-ttu-id="3ccb4-134">sp_update_alert &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="3ccb4-134">sp_update_alert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)  
  
  
