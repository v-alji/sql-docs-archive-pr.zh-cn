---
title: 检查使用数据库邮件发送的电子邮件的状态 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- e-mail [SQL Server], status information
- mail [SQL Server], status information
- Database Mail [SQL Server], message status
- status information [Database Mail]
ms.assetid: eb290f24-b52f-46bc-84eb-595afee6a5f3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1642c456cd64484dede64f8127ff2f979f2242e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591370"
---
# <a name="check-the-status-of-e-mail-messages-sent-with-database-mail"></a><span data-ttu-id="21bf4-102">检查使用数据库邮件发送的电子邮件的状态</span><span class="sxs-lookup"><span data-stu-id="21bf4-102">Check the Status of E-Mail Messages Sent With Database Mail</span></span>
  <span data-ttu-id="21bf4-103">本主题说明在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中如何使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]检查通过数据库邮件发送的电子邮件的状态。</span><span class="sxs-lookup"><span data-stu-id="21bf4-103">This topic describes how to check the status of the e-mail message sent using Database Mail  in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="21bf4-104">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="21bf4-104">**Before you begin:**</span></span>  
  
-   <span data-ttu-id="21bf4-105">若要查看通过数据库邮件发送的电子邮件的状态，请使用：  [Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="21bf4-105">**To view the status of the e-mail sent using Database Mail, using:**  [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="21bf4-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="21bf4-106">Before You Begin</span></span>  
 <span data-ttu-id="21bf4-107">数据库邮件保留发送的电子邮件的副本，并在 **msdb**数据库的 **sysmail_allitems**、 **sysmail_sentitems**、 **sysmail_unsentitems** 、 **sysmail_faileditems** 视图中显示它们。</span><span class="sxs-lookup"><span data-stu-id="21bf4-107">Database Mail keeps copies of outgoing e-mail messages and displays them in the **sysmail_allitems**, **sysmail_sentitems**, **sysmail_unsentitems**, **sysmail_faileditems** views of the **msdb** database.</span></span> <span data-ttu-id="21bf4-108">数据库邮件外部程序记录活动，并通过 Windows 应用程序事件日志以及 **msdb** 数据库的 **sysmail_event_log** 视图显示日志。</span><span class="sxs-lookup"><span data-stu-id="21bf4-108">The Database Mail external program logs activity and displays the log through the Windows Application Event Log and the **sysmail_event_log** view in the **msdb** database.</span></span> <span data-ttu-id="21bf4-109">若要检查电子邮件的状态，请对此视图运行查询。</span><span class="sxs-lookup"><span data-stu-id="21bf4-109">To check the status of an e-mail message, run a query against this view.</span></span> <span data-ttu-id="21bf4-110">电子邮件可以处于下列四种可能的状态之一： **sent**、 **unsent**、 **retrying**和 **failed**。</span><span class="sxs-lookup"><span data-stu-id="21bf4-110">E-mail messages have one of four possible statuses: **sent**, **unsent**, **retrying**, and **failed**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="21bf4-111">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="21bf4-111">Using Transact-SQL</span></span>  
 <span data-ttu-id="21bf4-112">**查看通过数据库邮件发送的电子邮件的状态**</span><span class="sxs-lookup"><span data-stu-id="21bf4-112">**To view the status of the e-mail sent using Database Mail**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="21bf4-113">有关此过程的示例，请参阅本节后面的 [示例 (Transact-SQL)](#TsqlExample)。</span><span class="sxs-lookup"><span data-stu-id="21bf4-113">For an example of this procedure, see [Example (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="21bf4-114">从 **sysmail_allitems** 表中选择，按 **mailitem_id** 或 **sent_status**指定要检查的邮件。</span><span class="sxs-lookup"><span data-stu-id="21bf4-114">Select from the **sysmail_allitems** table, specifying the messages of interest by **mailitem_id** or **sent_status**.</span></span>  
  
2.  <span data-ttu-id="21bf4-115">若要检查外部程序返回的电子邮件的状态，请将 **sysmail_allitems** 联接到 **sysmail_event_log** 视图中的 **mailitem_id** 列，如下所示。</span><span class="sxs-lookup"><span data-stu-id="21bf4-115">To check the status returned from the external program for the e-mail messages, join **sysmail_allitems** to **sysmail_event_log** view on the **mailitem_id** column, as shown in the following section.</span></span>  
  
     <span data-ttu-id="21bf4-116">默认情况下，外部程序不会记录有关发送成功的邮件的信息。</span><span class="sxs-lookup"><span data-stu-id="21bf4-116">By default, the external program does not log information about messages that were successfully sent.</span></span> <span data-ttu-id="21bf4-117">若要记录所有邮件，请使用 **“数据库邮件配置向导”** 的 **“配置系统参数”** 页，将日志级别设置为“详细”。</span><span class="sxs-lookup"><span data-stu-id="21bf4-117">To log all messages, set the logging level to verbose using the **Configure System Parameters** page of the **Database Mail Configuration Wizard.**</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="21bf4-118">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="21bf4-118">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="21bf4-119">下面的示例列出了有关发送到 `danw` 的所有电子邮件（外部程序无法成功发送）的信息。</span><span class="sxs-lookup"><span data-stu-id="21bf4-119">The following example lists information about any e-mail messages sent to `danw` that the external program could not send successfully.</span></span> <span data-ttu-id="21bf4-120">该语句列出了邮件的主题、外部程序发送邮件失败的日期和时间以及来自数据库邮件日志的错误消息。</span><span class="sxs-lookup"><span data-stu-id="21bf4-120">The statement lists the subject, the date and time that the external program failed to send the message, and the error message from the Database Mail log.</span></span>  
  
```  
USE msdb ;  
GO  
  
-- Show the subject, the time that the mail item row was last  
-- modified, and the log information.  
-- Join sysmail_faileditems to sysmail_event_log   
-- on the mailitem_id column.  
-- In the WHERE clause list items where danw was in the recipients,  
-- copy_recipients, or blind_copy_recipients.  
-- These are the items that would have been sent  
-- to danw.  
  
SELECT items.subject,  
    items.last_mod_date  
    ,l.description FROM dbo.sysmail_faileditems as items  
INNER JOIN dbo.sysmail_event_log AS l  
    ON items.mailitem_id = l.mailitem_id  
WHERE items.recipients LIKE '%danw%'    
    OR items.copy_recipients LIKE '%danw%'   
    OR items.blind_copy_recipients LIKE '%danw%'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="21bf4-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="21bf4-121">See Also</span></span>  
 [<span data-ttu-id="21bf4-122">数据库邮件日志和审核</span><span class="sxs-lookup"><span data-stu-id="21bf4-122">Database Mail Log and Audits</span></span>](database-mail-log-and-audits.md)  
  
  
