---
title: 数据库邮件外部程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- external programs [Database Mail]
- DatabaseMail90.exe
- Database Mail [SQL Server], external programs
ms.assetid: bc124164-eb6e-4b7f-bf66-98a3113d02f7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 698fc8d97a565b4181552691a0260486c9c43bfd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693972"
---
# <a name="database-mail-external-program"></a><span data-ttu-id="d8b30-102">数据库邮件外部程序</span><span class="sxs-lookup"><span data-stu-id="d8b30-102">Database Mail External Program</span></span>
  <span data-ttu-id="d8b30-103">数据库邮件外部可执行程序是 **DatabaseMail.exe**，该程序位于 **安装的** MSSQL\Binn directory [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目录中。</span><span class="sxs-lookup"><span data-stu-id="d8b30-103">The Database Mail external executable is **DatabaseMail.exe**, located in the **MSSQL\Binn directory** of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span> <span data-ttu-id="d8b30-104">当有电子邮件要处理时，数据库邮件使用 Service Broker 激活来启动该外部程序。</span><span class="sxs-lookup"><span data-stu-id="d8b30-104">Database Mail uses Service Broker activation to start the external program when there are e-mail messages to be processed.</span></span> <span data-ttu-id="d8b30-105">数据库邮件启动该外部程序的一个实例。</span><span class="sxs-lookup"><span data-stu-id="d8b30-105">Database Mail starts one instance of the external program.</span></span> <span data-ttu-id="d8b30-106">该外部程序在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的服务帐户的安全上下文中运行。</span><span class="sxs-lookup"><span data-stu-id="d8b30-106">The external program runs in the security context of the service account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d8b30-107">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="d8b30-107">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="d8b30-108">数据库邮件外部程序概念</span><span class="sxs-lookup"><span data-stu-id="d8b30-108">Database Mail External Program Concepts</span></span>](#ComponentsAndConcepts)  
  
-   [<span data-ttu-id="d8b30-109">与配置数据库邮件外部程序相关的任务</span><span class="sxs-lookup"><span data-stu-id="d8b30-109">Tasks Related to Configuring Database Mail External Program</span></span>](#RelatedTasks)  
  
##  <a name="database-mail-external-program-concepts"></a><a name="ComponentsAndConcepts"></a> <span data-ttu-id="d8b30-110">数据库邮件外部程序概念</span><span class="sxs-lookup"><span data-stu-id="d8b30-110">Database Mail External Program Concepts</span></span>  
 <span data-ttu-id="d8b30-111">该外部程序启动后，使用 Windows 身份验证连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 并开始处理电子邮件。</span><span class="sxs-lookup"><span data-stu-id="d8b30-111">When the external program starts, the program connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Windows Authentication and begins processing e-mail messages.</span></span> <span data-ttu-id="d8b30-112">如果达到指定的超时期限时没有邮件要发送，该程序将退出。</span><span class="sxs-lookup"><span data-stu-id="d8b30-112">When there have been no messages to send for the specified time-out period, the program exits.</span></span> <span data-ttu-id="d8b30-113">可以使用数据库邮件配置向导或数据库邮件存储过程配置该程序退出前等待的时间。</span><span class="sxs-lookup"><span data-stu-id="d8b30-113">You can configure the amount of time that the program waits before exiting by using either Database Mail Configuration Wizard or the Database Mail stored procedures.</span></span> <span data-ttu-id="d8b30-114">有关详细信息，请参阅 [sysmail_configure_sp (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql)的服务帐户的安全上下文中运行。</span><span class="sxs-lookup"><span data-stu-id="d8b30-114">For more information, see [sysmail_configure_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql).</span></span>  
  
 <span data-ttu-id="d8b30-115">外部程序将信息存储在 **msdb** 数据库的系统表中。</span><span class="sxs-lookup"><span data-stu-id="d8b30-115">The external program stores information in system tables in the **msdb** database.</span></span> <span data-ttu-id="d8b30-116">如果该外部程序无法与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]通信，就将错误记录在 Microsoft Windows 应用程序事件日志中。</span><span class="sxs-lookup"><span data-stu-id="d8b30-116">If the external program cannot communicate with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the program logs errors to the Microsoft Windows application event log.</span></span> <span data-ttu-id="d8b30-117">如果在 **数据库邮件配置向导** 的 **“配置系统参数”** 对话框中将日志记录级别设置为 **“详细”** ，则还会记录其他消息。</span><span class="sxs-lookup"><span data-stu-id="d8b30-117">Additional message logging is provided when the logging level is set to **Verbose** in the **Configure System Parameters** dialog box of the **Database Mail Configuration Wizard**.</span></span>  
  
 <span data-ttu-id="d8b30-118">请注意，为了提高效率，该外部程序会缓存帐户和配置文件信息。</span><span class="sxs-lookup"><span data-stu-id="d8b30-118">Notice that, for efficiency, the external program caches account and profile information.</span></span> <span data-ttu-id="d8b30-119">因此，对帐户和配置文件所做的配置更改在几分钟内可能不会反映在该外部程序中。</span><span class="sxs-lookup"><span data-stu-id="d8b30-119">Therefore, configuration changes to accounts and profiles may not be reflected in the external program for a few minutes.</span></span>  
  
##  <a name="tasks-related-to-configuring-database-mail-external-program"></a><a name="RelatedTasks"></a> <span data-ttu-id="d8b30-120">与配置数据库邮件外部程序相关的任务</span><span class="sxs-lookup"><span data-stu-id="d8b30-120">Tasks Related to Configuring Database Mail External Program</span></span>  
  
|<span data-ttu-id="d8b30-121">配置任务</span><span class="sxs-lookup"><span data-stu-id="d8b30-121">Configuration Task</span></span>|<span data-ttu-id="d8b30-122">主题链接</span><span class="sxs-lookup"><span data-stu-id="d8b30-122">Topic Link</span></span>|  
|------------------------|----------------|  
|<span data-ttu-id="d8b30-123">指定外部程序在退出前的时间。</span><span class="sxs-lookup"><span data-stu-id="d8b30-123">Specify the time that the External Program before exiting.</span></span>|[<span data-ttu-id="d8b30-124">sysmail_configure_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d8b30-124">sysmail_configure_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql)|  
  
## <a name="see-also"></a><span data-ttu-id="d8b30-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d8b30-125">See Also</span></span>  
 <span data-ttu-id="d8b30-126">[SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md) </span><span class="sxs-lookup"><span data-stu-id="d8b30-126">[SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md) </span></span>  
 <span data-ttu-id="d8b30-127">[数据库邮件日志和审核](database-mail-log-and-audits.md) </span><span class="sxs-lookup"><span data-stu-id="d8b30-127">[Database Mail Log and Audits](database-mail-log-and-audits.md) </span></span>  
 [<span data-ttu-id="d8b30-128">数据库邮件</span><span class="sxs-lookup"><span data-stu-id="d8b30-128">Database Mail</span></span>](database-mail.md)  
  
  
