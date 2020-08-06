---
title: 数据库邮件日志和审核 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- Database Mail [SQL Server], auditing
- logs [Database Mail]
- audits [SQL Server], Database Mail
- Database Mail [SQL Server], logging
ms.assetid: 846589ee-5fe5-4ab3-b335-0c253e569f99
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6267389f187b955982ec1c18c411f703b4562f3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693964"
---
# <a name="database-mail-log-and-audits"></a><span data-ttu-id="9071b-102">数据库邮件日志和审核</span><span class="sxs-lookup"><span data-stu-id="9071b-102">Database Mail Log and Audits</span></span>
  <span data-ttu-id="9071b-103">数据库邮件日志记录功能旨在提供一种隔离和更正问题的方法。</span><span class="sxs-lookup"><span data-stu-id="9071b-103">The Database Mail logging functionality is designed to provide a way to isolate and correct problems.</span></span> <span data-ttu-id="9071b-104">数据库邮件将日志信息存储在 **msdb** 数据库中。</span><span class="sxs-lookup"><span data-stu-id="9071b-104">Database Mail stores the log information in the **msdb** database.</span></span> <span data-ttu-id="9071b-105">有关数据库邮件电子邮件内容的信息、电子邮件状态以及已接收的任何消息（例如，数据库邮件记录的错误）可用于故障排除和审核目的。</span><span class="sxs-lookup"><span data-stu-id="9071b-105">Information about Database Mail e-mail content, status of e-mails, and any messages received, such as errors  are logged by Database Mail and can be used for troubleshooting and auditing purposes.</span></span>  
  
## <a name="database-mail-logs"></a><span data-ttu-id="9071b-106">数据库邮件日志</span><span class="sxs-lookup"><span data-stu-id="9071b-106">Database Mail Logs</span></span>  
 <span data-ttu-id="9071b-107">**msdb** 数据库中的表用于记录来自 [Database Mail External Program](database-mail-external-program.md)的信息。</span><span class="sxs-lookup"><span data-stu-id="9071b-107">Tables in the **msdb** database log information from the [Database Mail External Program](database-mail-external-program.md).</span></span> <span data-ttu-id="9071b-108">[数据库邮件视图 (Transact SQL)](/sql/relational-databases/system-catalog-views/database-mail-views-transact-sql) 公开这些表以进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="9071b-108">[Database Mail Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/database-mail-views-transact-sql) expose the tables for troubleshooting purposes.</span></span> <span data-ttu-id="9071b-109">如果 Service Broker 不能激活外部程序、外部程序遇到网络错误或者简单邮件传输协议 (SMTP) 服务器拒绝电子邮件，[sysmail_event_log (Transact-SQL)](/sql/relational-databases/system-catalog-views/sysmail-event-log-transact-sql) 视图中就会显示错误。</span><span class="sxs-lookup"><span data-stu-id="9071b-109">Errors appear in the [sysmail_event_log &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sysmail-event-log-transact-sql) view if Service Broker cannot activate the external program, if the external program encounters networking errors or if the Simple Mail Transport Protocol (SMTP) server refuses an e-mail message.</span></span> <span data-ttu-id="9071b-110">如果外部程序无法将错误记录到 **msdb** 表，则会将错误记录到 Windows 应用程序事件日志。</span><span class="sxs-lookup"><span data-stu-id="9071b-110">In the event that the external program cannot log to the **msdb** tables, the program logs errors to the Windows application event log.</span></span>  
  
 <span data-ttu-id="9071b-111">**msdb** 数据库的内部表包含从数据库邮件发送的电子邮件和附件以及每封邮件的当前状态。</span><span class="sxs-lookup"><span data-stu-id="9071b-111">Internal tables in the **msdb** database contain the e-mail messages and attachments sent from Database Mail, together with the current status of each message.</span></span> <span data-ttu-id="9071b-112">每封邮件被处理后，数据库邮件就会更新这些表。</span><span class="sxs-lookup"><span data-stu-id="9071b-112">Database Mail updates these tables as each message is processed.</span></span>  
  
## <a name="database-mail-auditing-tasks"></a><span data-ttu-id="9071b-113">数据库邮件审核任务</span><span class="sxs-lookup"><span data-stu-id="9071b-113">Database Mail Auditing tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9071b-114">**查看和管理数据库邮件日志**</span><span class="sxs-lookup"><span data-stu-id="9071b-114">**Reviewing and managing Database Mail logs**</span></span>|<span data-ttu-id="9071b-115">**指向主题的链接**</span><span class="sxs-lookup"><span data-stu-id="9071b-115">**Link to Topic**</span></span>|  
|<span data-ttu-id="9071b-116">检查各个邮件的传递状态</span><span class="sxs-lookup"><span data-stu-id="9071b-116">Check the delivery status of an individual message</span></span>|[<span data-ttu-id="9071b-117">检查使用数据库邮件发送的电子邮件的状态</span><span class="sxs-lookup"><span data-stu-id="9071b-117">Check the Status of E-Mail Messages Sent With Database Mail</span></span>](check-the-status-of-e-mail-messages-sent-with-database-mail.md)|  
|<span data-ttu-id="9071b-118">清理数据库邮件消息、附件和日志条目</span><span class="sxs-lookup"><span data-stu-id="9071b-118">Clean up Database Mail messages, attachments, and log entries</span></span>|[<span data-ttu-id="9071b-119">sysmail_delete_mailitems_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9071b-119">sysmail_delete_mailitems_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-mailitems-sp-transact-sql)<br /><br /> [<span data-ttu-id="9071b-120">sysmail_delete_log_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9071b-120">sysmail_delete_log_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-log-sp-transact-sql)|  
|<span data-ttu-id="9071b-121">存档数据库邮件和日志</span><span class="sxs-lookup"><span data-stu-id="9071b-121">Archive the Database Email Messages and Logs</span></span>|[<span data-ttu-id="9071b-122">创建 SQL Server 代理作业以存档数据库邮件和事件日志</span><span class="sxs-lookup"><span data-stu-id="9071b-122">Create a SQL Server Agent Job to Archive Database Mail Messages and Event Logs</span></span>](create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md)|  
  
## <a name="see-also"></a><span data-ttu-id="9071b-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9071b-123">See Also</span></span>  
 [<span data-ttu-id="9071b-124">监视资源使用情况（系统监视器）</span><span class="sxs-lookup"><span data-stu-id="9071b-124">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](../performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
