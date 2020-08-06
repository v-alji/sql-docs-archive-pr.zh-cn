---
title: 数据库邮件 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- architecture [SQL Server], Database Mail
- Database Mail [SQL Server], architecture
- Database Mail [SQL Server], components
ms.assetid: 9e4563dd-4799-4b32-a78a-048ea44a44c1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 97a5a459fafd80956a2b8d31c27b86169c6fa850
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693958"
---
# <a name="database-mail"></a><span data-ttu-id="05dec-102">数据库邮件</span><span class="sxs-lookup"><span data-stu-id="05dec-102">Database Mail</span></span>
  <span data-ttu-id="05dec-103">数据库邮件是从 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]中发送电子邮件的企业解决方案。</span><span class="sxs-lookup"><span data-stu-id="05dec-103">Database Mail is an enterprise solution for sending e-mail messages from the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="05dec-104">通过使用数据库邮件，数据库应用程序可以向用户发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="05dec-104">Using Database Mail, your database applications can send e-mail messages to users.</span></span> <span data-ttu-id="05dec-105">邮件中可以包含查询结果，还可以包含来自网络中任何资源的文件。</span><span class="sxs-lookup"><span data-stu-id="05dec-105">The messages can contain query results, and can also include files from any resource on your network.</span></span>  
  
 
  
##  <a name="benefits-of-using-database-mail"></a><a name="Benefits"></a> <span data-ttu-id="05dec-106">使用数据库邮件的优点</span><span class="sxs-lookup"><span data-stu-id="05dec-106">Benefits of using Database Mail</span></span>  
 <span data-ttu-id="05dec-107">数据库邮件旨在实现可靠性、灵活性、安全性和兼容性。</span><span class="sxs-lookup"><span data-stu-id="05dec-107">Database Mail is designed for reliability, scalability, security, and supportability.</span></span>  
  
### <a name="reliability"></a><span data-ttu-id="05dec-108">可靠性</span><span class="sxs-lookup"><span data-stu-id="05dec-108">Reliability</span></span>  
  
-   <span data-ttu-id="05dec-109">数据库邮件使用标准的简单邮件传输协议 (SMTP) 发送邮件。</span><span class="sxs-lookup"><span data-stu-id="05dec-109">Database Mail uses the standard Simple Mail Transfer Protocol (SMTP) to send mail.</span></span> <span data-ttu-id="05dec-110">无须在运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的计算机上安装扩展 MAPI 客户端便可以使用数据库邮件。</span><span class="sxs-lookup"><span data-stu-id="05dec-110">You can use Database Mail without installing an Extended MAPI client on the computer that runs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="05dec-111">进程隔离。</span><span class="sxs-lookup"><span data-stu-id="05dec-111">Process isolation.</span></span> <span data-ttu-id="05dec-112">若要最大程度上减小对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的影响，传递电子邮件的组件必须在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]外部的单独进程中运行。</span><span class="sxs-lookup"><span data-stu-id="05dec-112">To minimize the impact on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the component that delivers e-mail runs outside of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], in a separate process.</span></span> <span data-ttu-id="05dec-113">即使外部进程停止或失败，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 也会继续对电子邮件进行排队。</span><span class="sxs-lookup"><span data-stu-id="05dec-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will continue to queue e-mail messages even if the external process stops or fails.</span></span> <span data-ttu-id="05dec-114">队列中的邮件将在外部进程或 SMTP 服务器联机时发送。</span><span class="sxs-lookup"><span data-stu-id="05dec-114">The queued messages will be sent once the outside process or SMTP server comes online.</span></span>  
  
-   <span data-ttu-id="05dec-115">故障转移帐户。</span><span class="sxs-lookup"><span data-stu-id="05dec-115">Failover accounts.</span></span> <span data-ttu-id="05dec-116">数据库邮件配置文件允许您指定多台 SMTP 服务器。</span><span class="sxs-lookup"><span data-stu-id="05dec-116">A Database Mail profile allows you to specify more than one SMTP server.</span></span> <span data-ttu-id="05dec-117">如果一台 SMTP 服务器不可用，还可以将邮件传递至其他的 SMTP 服务器。</span><span class="sxs-lookup"><span data-stu-id="05dec-117">Should an SMTP server be unavailable, mail can still be delivered to another SMTP server.</span></span>  
  
-   <span data-ttu-id="05dec-118">群集支持。</span><span class="sxs-lookup"><span data-stu-id="05dec-118">Cluster support.</span></span> <span data-ttu-id="05dec-119">数据库邮件与群集兼容，并且可以完全用于群集中。</span><span class="sxs-lookup"><span data-stu-id="05dec-119">Database Mail is cluster-aware and is fully supported on a cluster.</span></span>  
  
### <a name="scalability"></a><span data-ttu-id="05dec-120">可伸缩性</span><span class="sxs-lookup"><span data-stu-id="05dec-120">Scalability</span></span>  
  
-   <span data-ttu-id="05dec-121">后台传递：数据库邮件提供后台（或异步）传递。</span><span class="sxs-lookup"><span data-stu-id="05dec-121">Background Delivery: Database Mail provides background, or asynchronous, delivery.</span></span> <span data-ttu-id="05dec-122">调用 **sp_send_dbmail** 发送消息时，数据库邮件可以向 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 队列中添加请求。</span><span class="sxs-lookup"><span data-stu-id="05dec-122">When you call **sp_send_dbmail** to send a message, Database Mail adds a request to a [!INCLUDE[ssSB](../../includes/sssb-md.md)] queue.</span></span> <span data-ttu-id="05dec-123">存储过程将立即返回。</span><span class="sxs-lookup"><span data-stu-id="05dec-123">The stored procedure returns immediately.</span></span> <span data-ttu-id="05dec-124">外部电子邮件组件将接收请求并传递电子邮件。</span><span class="sxs-lookup"><span data-stu-id="05dec-124">The external e-mail component receives the request and delivers the e-mail.</span></span>  
  
-   <span data-ttu-id="05dec-125">多个配置文件：数据库邮件允许您在一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中创建多个配置文件。</span><span class="sxs-lookup"><span data-stu-id="05dec-125">Multiple profiles: Database Mail allows you to create multiple profiles within a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="05dec-126">另外，您也可以选择发送邮件时数据库邮件使用的配置文件。</span><span class="sxs-lookup"><span data-stu-id="05dec-126">Optionally, you can choose the profile that Database Mail uses when you send a message.</span></span>  
  
-   <span data-ttu-id="05dec-127">多个帐户：每个配置文件都可以包含多个故障转移帐户。</span><span class="sxs-lookup"><span data-stu-id="05dec-127">Multiple accounts: Each profile can contain multiple failover accounts.</span></span> <span data-ttu-id="05dec-128">您可以配置包含不同帐户的不同配置文件以跨多台电子邮件服务器分发电子邮件。</span><span class="sxs-lookup"><span data-stu-id="05dec-128">You can configure different profiles with different accounts to distribute e-mail across multiple e-mail servers.</span></span>  
  
-   <span data-ttu-id="05dec-129">64 位兼容性：数据库邮件完全可以用于采用 64 位安装的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="05dec-129">64-bit compatibility: Database Mail is fully supported on 64-bit installations of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="security"></a><span data-ttu-id="05dec-130">安全性</span><span class="sxs-lookup"><span data-stu-id="05dec-130">Security</span></span>  
  
-   <span data-ttu-id="05dec-131">默认为关闭：为了减少 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的外围应用，默认情况下，禁用数据库邮件存储过程。</span><span class="sxs-lookup"><span data-stu-id="05dec-131">Off by default: To reduce the surface area of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Database Mail stored procedures are disabled by default.</span></span>  
  
-   <span data-ttu-id="05dec-132">邮件安全性：若要发送数据库邮件，您必须是 **msdb** 数据库中的 **DatabaseMailUserRole** 数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="05dec-132">Mail Security:To send Database Mail, you must be a member of the **DatabaseMailUserRole** database role in the **msdb** database.</span></span>  
  
-   <span data-ttu-id="05dec-133">配置文件安全性：数据库邮件增强了邮件配置文件的安全性。</span><span class="sxs-lookup"><span data-stu-id="05dec-133">Profile security: Database Mail enforces security for mail profiles.</span></span> <span data-ttu-id="05dec-134">您可以选择对数据库邮件配置文件具有访问权限的 **msdb** 数据库用户或组，</span><span class="sxs-lookup"><span data-stu-id="05dec-134">You choose the **msdb** database users or groups that have access to a Database Mail profile.</span></span> <span data-ttu-id="05dec-135">并可以为 **msdb**中的任一特定用户或所有用户授予访问权限。</span><span class="sxs-lookup"><span data-stu-id="05dec-135">You can grant access to either specific users, or all users in **msdb**.</span></span> <span data-ttu-id="05dec-136">专用配置文件用于限制指定用户的访问权限。</span><span class="sxs-lookup"><span data-stu-id="05dec-136">A private profile restricts access to a specified list of users.</span></span> <span data-ttu-id="05dec-137">公共配置文件可供数据库中的所有用户使用。</span><span class="sxs-lookup"><span data-stu-id="05dec-137">A public profile is available to all users in a database.</span></span>  
  
-   <span data-ttu-id="05dec-138">附件大小调控器：数据库邮件增强了对附件文件大小的可配置限制。</span><span class="sxs-lookup"><span data-stu-id="05dec-138">Attachment size governor: Database Mail enforces a configurable limit on the attachment file size.</span></span> <span data-ttu-id="05dec-139">可以使用 [sysmail_configure_sp](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql) 存储过程更改此限制。</span><span class="sxs-lookup"><span data-stu-id="05dec-139">You can change this limit by using the [sysmail_configure_sp](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql) stored procedure.</span></span>  
  
-   <span data-ttu-id="05dec-140">禁止的文件扩展名：数据库邮件维护一个禁止的文件扩展名列表。</span><span class="sxs-lookup"><span data-stu-id="05dec-140">Prohibited file extensions: Database Mail maintains a list of prohibited file extensions.</span></span> <span data-ttu-id="05dec-141">用户无法附加扩展名为列表中某个扩展名的文件。</span><span class="sxs-lookup"><span data-stu-id="05dec-141">Users cannot attach files with an extension that appears in the list.</span></span> <span data-ttu-id="05dec-142">可以使用 sysmail_configure_sp 更改该列表。</span><span class="sxs-lookup"><span data-stu-id="05dec-142">You can change this list by using sysmail_configure_sp.</span></span>  
  
-   <span data-ttu-id="05dec-143">数据库邮件在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 引擎服务帐户下运行。</span><span class="sxs-lookup"><span data-stu-id="05dec-143">Database Mail runs under the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Engine service account.</span></span> <span data-ttu-id="05dec-144">若要将文件夹中的文件附加到电子邮件， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 引擎帐户应有权访问该文件所在的文件夹。</span><span class="sxs-lookup"><span data-stu-id="05dec-144">To attach a file from a folder to an email, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] engine account should have permissions to access the folder with the file.</span></span>  
  
### <a name="supportability"></a><span data-ttu-id="05dec-145">可支持性</span><span class="sxs-lookup"><span data-stu-id="05dec-145">Supportability</span></span>  
  
-   <span data-ttu-id="05dec-146">集成配置：数据库邮件在 [!INCLUDE[ssDEnoversion](../../includes/tsql-md.md)]中维护电子邮件帐户的信息。</span><span class="sxs-lookup"><span data-stu-id="05dec-146">Integrated configuration: Database Mail maintains the information for e-mail accounts within [!INCLUDE[ssDEnoversion](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="05dec-147">日志记录。</span><span class="sxs-lookup"><span data-stu-id="05dec-147">Logging.</span></span> <span data-ttu-id="05dec-148">数据库邮件将电子邮件活动记录到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、Microsoft Windows 应用程序事件日志和 **msdb** 数据库的表中。</span><span class="sxs-lookup"><span data-stu-id="05dec-148">Database Mail logs e-mail activity to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the Microsoft Windows application event log, and to tables in the **msdb** database.</span></span>  
  
-   <span data-ttu-id="05dec-149">审核：数据库邮件将发送的邮件和附件的副本保留在 **msdb** 数据库中。</span><span class="sxs-lookup"><span data-stu-id="05dec-149">Auditing: Database Mail keeps copies of messages and attachments sent in the **msdb** database.</span></span> <span data-ttu-id="05dec-150">您可以轻松地审核数据库邮件的使用情况并检查保留的邮件。</span><span class="sxs-lookup"><span data-stu-id="05dec-150">You can easily audit Database Mail usage and review the retained messages.</span></span>  
  
-   <span data-ttu-id="05dec-151">支持 HTML：数据库邮件允许您以 HTML 格式发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="05dec-151">Support for HTML: Database Mail allows you to send e-mail formatted as HTML.</span></span>  
  

  
##  <a name="database-mail-architecture"></a><a name="VisualElement"></a> <span data-ttu-id="05dec-152">数据库邮件体系结构</span><span class="sxs-lookup"><span data-stu-id="05dec-152">Database Mail Architecture</span></span>  
 <span data-ttu-id="05dec-153">数据库邮件的设计基于使用 Service Broker 技术的排队体系结构。</span><span class="sxs-lookup"><span data-stu-id="05dec-153">Database Mail is designed on a queued architecture that uses service broker technologies.</span></span> <span data-ttu-id="05dec-154">当用户执行 **sp_send_dbmail**时，存储过程将向邮件队列中插入一项，并创建一条包含该电子邮件信息的记录。</span><span class="sxs-lookup"><span data-stu-id="05dec-154">When users execute **sp_send_dbmail**, the stored procedure inserts an item into the mail queue and creates a record that contains the e-mail message.</span></span> <span data-ttu-id="05dec-155">在邮件队列中插入新项将启动数据库邮件外部进程 (DatabaseMail.exe)。</span><span class="sxs-lookup"><span data-stu-id="05dec-155">Inserting the new entry in the mail queue starts the external Database Mail process (DatabaseMail.exe).</span></span> <span data-ttu-id="05dec-156">该外部进程会读取电子邮件的信息并将电子邮件发送到相应的一台或多台电子邮件服务器。</span><span class="sxs-lookup"><span data-stu-id="05dec-156">The external process reads the e-mail information and sends the e-mail message to the appropriate e-mail server or servers.</span></span> <span data-ttu-id="05dec-157">该外部进程还会在状态队列中插入一项，来指示发送操作的结果。</span><span class="sxs-lookup"><span data-stu-id="05dec-157">The external process inserts an item in the Status queue for the outcome of the send operation.</span></span> <span data-ttu-id="05dec-158">在状态队列中插入新项将启动内部存储过程，该过程将更新电子邮件信息的状态。</span><span class="sxs-lookup"><span data-stu-id="05dec-158">Inserting the new entry in the status queue starts an internal stored procedure that updates the status of the e-mail message.</span></span> <span data-ttu-id="05dec-159">除存储已发送（或未发送）的电子邮件信息外，数据库邮件还在系统表中记录所有电子邮件的附件。</span><span class="sxs-lookup"><span data-stu-id="05dec-159">Besides storing the sent, or unsent, e-mail message, Database Mail also records any e-mail attachments in the system tables.</span></span> <span data-ttu-id="05dec-160">数据库邮件视图提供了供排除故障使用的邮件状态，使用存储过程可以对数据库邮件队列进行管理。</span><span class="sxs-lookup"><span data-stu-id="05dec-160">Database Mail views provide the status of messages for troubleshooting, and stored procedures allow for administration of the Database Mail queue.</span></span>  
  
 <span data-ttu-id="05dec-161">![msdb 将消息发送至 SMTP 邮件服务器](../../database-engine/media/databasemail.gif "msdb 将消息发送至 SMTP 邮件服务器")</span><span class="sxs-lookup"><span data-stu-id="05dec-161">![msdb sends messages to an SMTP mail server](../../database-engine/media/databasemail.gif "msdb sends messages to an SMTP mail server")</span></span>  
  

  
##  <a name="introduction-to-database-mail-components"></a><a name="ComponentsAndConcepts"></a> <span data-ttu-id="05dec-162">数据库邮件组件简介</span><span class="sxs-lookup"><span data-stu-id="05dec-162">Introduction to Database Mail Components</span></span>  
 <span data-ttu-id="05dec-163">数据库邮件由以下主要组件构成：</span><span class="sxs-lookup"><span data-stu-id="05dec-163">Database Mail consists of the following main components:</span></span>  
  
-   <span data-ttu-id="05dec-164">配置和安全组件</span><span class="sxs-lookup"><span data-stu-id="05dec-164">Configuration and security components</span></span>  
  
     <span data-ttu-id="05dec-165">数据库邮件将配置和安全信息存储在 **msdb** 数据库中。</span><span class="sxs-lookup"><span data-stu-id="05dec-165">Database Mail stores configuration and security information in the **msdb** database.</span></span> <span data-ttu-id="05dec-166">配置和安全对象可创建数据库邮件所用的配置文件和帐户。</span><span class="sxs-lookup"><span data-stu-id="05dec-166">Configuration and security objects create profiles and accounts used by Database Mail.</span></span>  
  
-   <span data-ttu-id="05dec-167">邮件处理组件</span><span class="sxs-lookup"><span data-stu-id="05dec-167">Messaging components</span></span>  
  
     <span data-ttu-id="05dec-168">**msdb** 数据库是邮件主机数据库，包含数据库邮件用于发送电子邮件的消息处理对象。</span><span class="sxs-lookup"><span data-stu-id="05dec-168">The **msdb** database acts as the mail-host database that holds the messaging objects that Database Mail uses to send e-mail.</span></span> <span data-ttu-id="05dec-169">这些对象包括 **sp_send_dbmail** 存储过程和保存邮件信息的数据结构。</span><span class="sxs-lookup"><span data-stu-id="05dec-169">These objects include the **sp_send_dbmail** stored procedure and the data structures that hold information about messages.</span></span>  
  
-   <span data-ttu-id="05dec-170">数据库邮件可执行文件</span><span class="sxs-lookup"><span data-stu-id="05dec-170">Database Mail executable</span></span>  
  
     <span data-ttu-id="05dec-171">数据库邮件可执行文件是一个外部程序，从 **msdb** 数据库中的队列读取邮件并将邮件发送到电子邮件服务器。</span><span class="sxs-lookup"><span data-stu-id="05dec-171">The Database Mail executable is an external program that reads from a queue in the **msdb** database and sends messages to e-mail servers.</span></span>  
  
-   <span data-ttu-id="05dec-172">日志记录和审核组件</span><span class="sxs-lookup"><span data-stu-id="05dec-172">Logging and auditing components</span></span>  
  
     <span data-ttu-id="05dec-173">数据库邮件将日志记录信息记录在 **msdb** 数据库和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 应用程序事件日志中。</span><span class="sxs-lookup"><span data-stu-id="05dec-173">Database Mail records logging information in the **msdb** database and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application event log.</span></span>  
  
 <span data-ttu-id="05dec-174">**配置代理以使用数据库邮件：**</span><span class="sxs-lookup"><span data-stu-id="05dec-174">**Configuring Agent to use Database Mail:**</span></span>  
  
 <span data-ttu-id="05dec-175">SQL Server 代理可配置为使用数据库邮件。</span><span class="sxs-lookup"><span data-stu-id="05dec-175">SQL Server Agent can be configured to use Database Mail.</span></span> <span data-ttu-id="05dec-176">对于作业完成时的警报通知和自动通知，这是必需的。</span><span class="sxs-lookup"><span data-stu-id="05dec-176">This is required for alert notifications and automatic notification when a job completes.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="05dec-177">无需将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理配置为使用数据库邮件，作业中的各个作业步骤也可以发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="05dec-177">Individual job steps within a job can also send e-mail without configuring [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to use Database Mail.</span></span> <span data-ttu-id="05dec-178">例如， [!INCLUDE[tsql](../../../includes/tsql-md.md)] 作业步骤可以使用数据库邮件将查询结果发送给一些收件人。</span><span class="sxs-lookup"><span data-stu-id="05dec-178">For example, a [!INCLUDE[tsql](../../../includes/tsql-md.md)] job step can use Database Mail to send the results of a query to a list of recipients.</span></span>  
  
 <span data-ttu-id="05dec-179">您可以配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理，使其在出现下列情况时向预定义的操作员发送电子邮件：</span><span class="sxs-lookup"><span data-stu-id="05dec-179">You can configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to send e-mail messages to predefined operators when:</span></span>  
  
-   <span data-ttu-id="05dec-180">警报触发时。</span><span class="sxs-lookup"><span data-stu-id="05dec-180">An alert is triggered.</span></span> <span data-ttu-id="05dec-181">可以配置警报，以针对所发生的特定事件发送电子邮件通知。</span><span class="sxs-lookup"><span data-stu-id="05dec-181">Alerts can be configured to send e-mail notification of specific events that occur.</span></span> <span data-ttu-id="05dec-182">例如，可以配置警报，将可能需要立即采取行动的特定数据库事件或操作系统情况通知操作员。</span><span class="sxs-lookup"><span data-stu-id="05dec-182">For example, alerts can be configured to notify an operator of a particular database event or operating system condition that may need immediate action.</span></span> <span data-ttu-id="05dec-183">有关配置警报的详细信息，请参阅 [警报](../../ssms/agent/alerts.md)。</span><span class="sxs-lookup"><span data-stu-id="05dec-183">For more information about configuring alerts, see [Alerts](../../ssms/agent/alerts.md).</span></span>  
  
-   <span data-ttu-id="05dec-184">计划任务成功完成或未完成（例如，数据库备份或复制事件）。</span><span class="sxs-lookup"><span data-stu-id="05dec-184">A scheduled task, such as a database backup or replication event, succeeds or fails.</span></span> <span data-ttu-id="05dec-185">例如，如果在月底的处理过程中出现错误，就可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理邮件通知操作员。</span><span class="sxs-lookup"><span data-stu-id="05dec-185">For example, you can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Mail to notify operators if an error occurs during processing at the end of a month.</span></span>  
  
 
  
##  <a name="database-mail-component-topics"></a><a name="RelatedContent"></a> <span data-ttu-id="05dec-186">数据库邮件组件主题</span><span class="sxs-lookup"><span data-stu-id="05dec-186">Database Mail Component Topics</span></span>  
  
-   [<span data-ttu-id="05dec-187">数据库邮件配置对象</span><span class="sxs-lookup"><span data-stu-id="05dec-187">Database Mail Configuration Objects</span></span>](database-mail-configuration-objects.md)  
  
-   [<span data-ttu-id="05dec-188">数据库邮件消息处理对象</span><span class="sxs-lookup"><span data-stu-id="05dec-188">Database Mail Messaging Objects</span></span>](database-mail-messaging-objects.md)  
  
-   [<span data-ttu-id="05dec-189">数据库邮件外部程序</span><span class="sxs-lookup"><span data-stu-id="05dec-189">Database Mail External Program</span></span>](database-mail-external-program.md)  
  
-   [<span data-ttu-id="05dec-190">数据库邮件日志和审核</span><span class="sxs-lookup"><span data-stu-id="05dec-190">Database Mail Log and Audits</span></span>](database-mail-log-and-audits.md)  
  
-   [<span data-ttu-id="05dec-191">配置 SQL Server 代理邮件以使用数据库邮件</span><span class="sxs-lookup"><span data-stu-id="05dec-191">Configure SQL Server Agent Mail to Use Database Mail</span></span>](configure-sql-server-agent-mail-to-use-database-mail.md)  
  

  
  
