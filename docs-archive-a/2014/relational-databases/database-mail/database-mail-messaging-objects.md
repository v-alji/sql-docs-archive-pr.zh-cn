---
title: 数据库邮件消息处理对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], host databases
- Database Mail [SQL Server], messaging objects
- mail host databases [SQL Server]
- host databases [Database Mail]
ms.assetid: 5aa2886e-1db1-4066-85df-57ccf4538c54
author: stevestein
ms.author: sstein
ms.openlocfilehash: d284d3ef1d0ac349dea95b1a6a134cb2429e6e4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693961"
---
# <a name="database-mail-messaging-objects"></a><span data-ttu-id="b8e4d-102">数据库邮件消息处理对象</span><span class="sxs-lookup"><span data-stu-id="b8e4d-102">Database Mail Messaging Objects</span></span>
  <span data-ttu-id="b8e4d-103">**msdb** 数据库是数据库邮件主机数据库。</span><span class="sxs-lookup"><span data-stu-id="b8e4d-103">The **msdb** database is the Database Mail host database.</span></span> <span data-ttu-id="b8e4d-104">此数据库包含数据库邮件的存储过程和消息处理对象。</span><span class="sxs-lookup"><span data-stu-id="b8e4d-104">This database contains the stored procedures and messaging objects for Database Mail.</span></span> <span data-ttu-id="b8e4d-105">Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中带有数据库邮件配置向导，可用来启用数据库邮件、创建和管理配置文件和帐户以及配置数据库邮件选项。</span><span class="sxs-lookup"><span data-stu-id="b8e4d-105">Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] includes the Database Mail Configuration Wizard for enabling Database Mail, creating and managing profiles and accounts, and configuring Database Mail options.</span></span>  
  
##  <a name="objects-in-msdb-database"></a><a name="ComponentsAndConcepts"></a><span data-ttu-id="b8e4d-106">**msdb** 数据库中的对象</span><span class="sxs-lookup"><span data-stu-id="b8e4d-106">Objects in **msdb** database</span></span>  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)] <span data-ttu-id="b8e4d-107">msdb **msdb** 。</span><span class="sxs-lookup"><span data-stu-id="b8e4d-107">must be enabled in the **msdb** database.</span></span> <span data-ttu-id="b8e4d-108">不过，数据库邮件不使用 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 网络。</span><span class="sxs-lookup"><span data-stu-id="b8e4d-108">However, Database Mail does not use [!INCLUDE[ssSB](../../includes/sssb-md.md)] networking.</span></span> <span data-ttu-id="b8e4d-109">因此，用户不必创建 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 端点即可使用数据库邮件。</span><span class="sxs-lookup"><span data-stu-id="b8e4d-109">Therefore, users do not have to create a [!INCLUDE[ssSB](../../includes/sssb-md.md)] endpoint to use Database Mail.</span></span> <span data-ttu-id="b8e4d-110">外部数据库邮件进程使用标准的 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 连接与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]通信。</span><span class="sxs-lookup"><span data-stu-id="b8e4d-110">The external Database Mail process uses a standard [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection to communicate with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b8e4d-111">如果启用了数据库邮件，它将在 **msdb** 数据库中显示下列对象。</span><span class="sxs-lookup"><span data-stu-id="b8e4d-111">Database Mail exposes the following objects in the **msdb** database when Database Mail is enabled.</span></span>  
  
 <span data-ttu-id="b8e4d-112">这些对象是数据库邮件在邮件主机数据库内的接口。</span><span class="sxs-lookup"><span data-stu-id="b8e4d-112">These objects are the interface for Database Mail within the mail host database.</span></span> <span data-ttu-id="b8e4d-113">还会安装其他对象以执行上面列出的对象所提供的功能，</span><span class="sxs-lookup"><span data-stu-id="b8e4d-113">Other objects are installed to implement the functionality provided by the objects listed above.</span></span> <span data-ttu-id="b8e4d-114">但是这些对象仅供内部使用。</span><span class="sxs-lookup"><span data-stu-id="b8e4d-114">However, those objects are reserved for internal use.</span></span>  
  
|<span data-ttu-id="b8e4d-115">名称</span><span class="sxs-lookup"><span data-stu-id="b8e4d-115">Name</span></span>|<span data-ttu-id="b8e4d-116">类型</span><span class="sxs-lookup"><span data-stu-id="b8e4d-116">Type</span></span>|<span data-ttu-id="b8e4d-117">说明</span><span class="sxs-lookup"><span data-stu-id="b8e4d-117">Description</span></span>|  
|----------|----------|-----------------|  
|[<span data-ttu-id="b8e4d-118">sysmail_allitems (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b8e4d-118">sysmail_allitems &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sysmail-allitems-transact-sql)|`View`|<span data-ttu-id="b8e4d-119">列出已提交到数据库邮件的所有邮件。</span><span class="sxs-lookup"><span data-stu-id="b8e4d-119">Lists all messages submitted to Database Mail.</span></span>|  
|[<span data-ttu-id="b8e4d-120">sysmail_event_log (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b8e4d-120">sysmail_event_log &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sysmail-event-log-transact-sql)|`View`|<span data-ttu-id="b8e4d-121">列出有关 [Database Mail External Program](database-mail-external-program.md)行为的邮件。</span><span class="sxs-lookup"><span data-stu-id="b8e4d-121">Lists messages about the behavior of the [Database Mail External Program](database-mail-external-program.md).</span></span>|  
|[<span data-ttu-id="b8e4d-122">sysmail_faileditems (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b8e4d-122">sysmail_faileditems &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sysmail-faileditems-transact-sql)|`View`|<span data-ttu-id="b8e4d-123">有关数据库邮件无法发送的邮件的信息。</span><span class="sxs-lookup"><span data-stu-id="b8e4d-123">Information about messages that Database Mail could not sent.</span></span>|  
|[<span data-ttu-id="b8e4d-124">sysmail_mailattachments (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b8e4d-124">sysmail_mailattachments &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sysmail-mailattachments-transact-sql)|`View`|<span data-ttu-id="b8e4d-125">有关数据库邮件附件的信息。</span><span class="sxs-lookup"><span data-stu-id="b8e4d-125">Information about attachments to Database Mail messages.</span></span>|  
|[<span data-ttu-id="b8e4d-126">sysmail_sentitems (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b8e4d-126">sysmail_sentitems &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sysmail-sentitems-transact-sql)|`View`|<span data-ttu-id="b8e4d-127">有关已使用数据库邮件发送的邮件的信息。</span><span class="sxs-lookup"><span data-stu-id="b8e4d-127">Information about messages that have been sent using Database Mail.</span></span>|  
|[<span data-ttu-id="b8e4d-128">sysmail_unsentitems (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b8e4d-128">sysmail_unsentitems &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sysmail-unsentitems-transact-sql)|`View`|<span data-ttu-id="b8e4d-129">有关数据库邮件当前正在尝试发送的邮件的信息。</span><span class="sxs-lookup"><span data-stu-id="b8e4d-129">Information about messages that Database Mail in currently trying to send.</span></span>|  
|[<span data-ttu-id="b8e4d-130">sp_send_dbmail (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b8e4d-130">sp_send_dbmail &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql)|`Stored Procedure`|<span data-ttu-id="b8e4d-131">使用数据库邮件发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="b8e4d-131">Sends e-mail messages using Database Mail.</span></span>|  
|[<span data-ttu-id="b8e4d-132">sysmail_delete_log_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b8e4d-132">sysmail_delete_log_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-log-sp-transact-sql)|`Stored Procedure`|<span data-ttu-id="b8e4d-133">从数据库邮件日志中删除邮件。</span><span class="sxs-lookup"><span data-stu-id="b8e4d-133">Deletes messages from the Database Mail log.</span></span>|  
|[<span data-ttu-id="b8e4d-134">sysmail_delete_mailitems_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b8e4d-134">sysmail_delete_mailitems_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-mailitems-sp-transact-sql)|`Stored Procedure`|<span data-ttu-id="b8e4d-135">从数据库邮件队列中删除邮件项。</span><span class="sxs-lookup"><span data-stu-id="b8e4d-135">Deletes mail items from the Database Mail queue.</span></span>|  
|[<span data-ttu-id="b8e4d-136">sysmail_help_status_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b8e4d-136">sysmail_help_status_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-help-status-sp-transact-sql)|`Stored Procedure`|<span data-ttu-id="b8e4d-137">指示数据库邮件是否已启动。</span><span class="sxs-lookup"><span data-stu-id="b8e4d-137">Indicates if Database Mail is started.</span></span>|  
|[<span data-ttu-id="b8e4d-138">sysmail_start_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b8e4d-138">sysmail_start_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-start-sp-transact-sql)|`Stored Procedure`|<span data-ttu-id="b8e4d-139">启动外部程序使用的 Service Broker 对象。</span><span class="sxs-lookup"><span data-stu-id="b8e4d-139">Starts the Service Broker objects that the external program uses.</span></span> <span data-ttu-id="b8e4d-140">默认情况下将会启动这些对象。</span><span class="sxs-lookup"><span data-stu-id="b8e4d-140">These objects are started by default.</span></span>|  
|[<span data-ttu-id="b8e4d-141">sysmail_stop_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b8e4d-141">sysmail_stop_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-stop-sp-transact-sql)|`Stored Procedure`|<span data-ttu-id="b8e4d-142">停止外部程序使用的 Service Broker 对象。</span><span class="sxs-lookup"><span data-stu-id="b8e4d-142">Stops the Service Broker objects that the external program uses.</span></span>|  
  

  
## <a name="see-also"></a><span data-ttu-id="b8e4d-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b8e4d-143">See Also</span></span>  
 <span data-ttu-id="b8e4d-144">[数据库邮件](database-mail.md) </span><span class="sxs-lookup"><span data-stu-id="b8e4d-144">[Database Mail](database-mail.md) </span></span>  
 [<span data-ttu-id="b8e4d-145">SQL Server Service Broker</span><span class="sxs-lookup"><span data-stu-id="b8e4d-145">SQL Server Service Broker</span></span>](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
