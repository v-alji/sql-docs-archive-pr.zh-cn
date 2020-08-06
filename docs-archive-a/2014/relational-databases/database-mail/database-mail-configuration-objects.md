---
title: 数据库邮件配置对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqlimail.manageexistingaccount.f1
- sql12.swb.sqlimail.addaccounttoprofile.f1
- sql12.swb.sqlmailconfiguration.f1
- sql12.swb.sqlimail.profileandaccountmanagement.f1
- sql12.swb.sqlimail.manageprofilesecurity.principalview.f1
- sql12.swb.sqlimail.newsqlimailaccount.f1
- sql12.swb.sqlimail.configuresystem.f1
- sql12.swb.sqlimail.selectconfiguration.f1
- sql12.swb.sqlimail.newprofile.f1
- sql12.swb.sqlimail.manageexistingprofile.f1
- sql12.swb.sqlimail.welcome.f1
- sql12.swb.sqlimail.manageprofilesecurity.profileview.f1
- sql12.swb.sqlimail.completewizard.f1
- sql12.swb.sqlimail.newaccount.f1
helpviewer_keywords:
- Database Mail [SQL Server], configuration objects
- Database Mail [SQL Server], accounts
- configuration objects [Database Mail]
- Database Mail [SQL Server], profiles
- profiles [SQL Server], Database Mail
- accounts [Database Mail]
ms.assetid: 03f6e4c0-04ff-490a-bd91-637806215bd1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 45dd4bfc8cdb382f9ad093e92c5939986a9db8e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693971"
---
# <a name="database-mail-configuration-objects"></a><span data-ttu-id="b022e-102">数据库邮件配置对象</span><span class="sxs-lookup"><span data-stu-id="b022e-102">Database Mail Configuration Objects</span></span>
  <span data-ttu-id="b022e-103">数据库邮件有两个配置对象：数据库配置对象提供了一种方法，用于配置从数据库应用程序或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理发送电子邮件时数据库邮件应使用的设置。</span><span class="sxs-lookup"><span data-stu-id="b022e-103">Database Mail has two configuration objects: The database configuration objects provide a way for you to configure the settings that Database mail should use when sending an email from your database application or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
-   <span data-ttu-id="b022e-104">数据库邮件帐户</span><span class="sxs-lookup"><span data-stu-id="b022e-104">Database Mail accounts</span></span>  
  
-   <span data-ttu-id="b022e-105">数据库邮件配置文件</span><span class="sxs-lookup"><span data-stu-id="b022e-105">Database Mail profiles</span></span>  
  
  
##  <a name="database-mail-configuration-object-relationship"></a><a name="VisualElement"></a> <span data-ttu-id="b022e-106">数据库邮件配置对象关系</span><span class="sxs-lookup"><span data-stu-id="b022e-106">Database Mail Configuration Object Relationship</span></span>  
 <span data-ttu-id="b022e-107">图中显示了两个配置文件、三个帐户和三个用户。</span><span class="sxs-lookup"><span data-stu-id="b022e-107">The illustration shows two profiles, three accounts, and three users.</span></span> <span data-ttu-id="b022e-108">用户 1 可以访问配置文件 1，该配置文件使用帐户 1 和帐户 2。</span><span class="sxs-lookup"><span data-stu-id="b022e-108">User 1 has access to Profile 1, which uses Account 1 and Account 2.</span></span> <span data-ttu-id="b022e-109">用户 3 可以访问配置文件 2，该配置文件使用帐户 2 和帐户 3。</span><span class="sxs-lookup"><span data-stu-id="b022e-109">User 3 has access to Profile 2, which uses Account 2 and Account 3.</span></span> <span data-ttu-id="b022e-110">用户 2 既可以访问配置文件 1，也可以访问配置文件 2。</span><span class="sxs-lookup"><span data-stu-id="b022e-110">User 2 has access to both Profile 1 and Profile 2.</span></span>  
  
 <span data-ttu-id="b022e-111">![用户、配置文件和帐户的关系](../../database-engine/media/databasemailprofileaccount.gif "用户、配置文件和帐户的关系")</span><span class="sxs-lookup"><span data-stu-id="b022e-111">![Relationship of users, profiles, and accounts](../../database-engine/media/databasemailprofileaccount.gif "Relationship of users, profiles, and accounts")</span></span>  
  
  
##  <a name="database-mail-account"></a><a name="DBAccount"></a> <span data-ttu-id="b022e-112">数据库邮件帐户</span><span class="sxs-lookup"><span data-stu-id="b022e-112">Database Mail Account</span></span>  
 <span data-ttu-id="b022e-113">数据库邮件帐户包含由 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用于向 SMTP 服务器发送电子邮件的信息。</span><span class="sxs-lookup"><span data-stu-id="b022e-113">A Database Mail account contains the information that Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses to send e-mail messages to an SMTP server.</span></span> <span data-ttu-id="b022e-114">每个帐户均包含一个电子邮件服务器的信息。</span><span class="sxs-lookup"><span data-stu-id="b022e-114">Each account contains information for one e-mail server.</span></span>  
  
 <span data-ttu-id="b022e-115">数据库邮件与 SMTP 服务器进行通信时支持三种身份验证方法：</span><span class="sxs-lookup"><span data-stu-id="b022e-115">A Database Mail supports three methods of authentication to communicate with an SMTP server:</span></span>  
  
-   <span data-ttu-id="b022e-116">Windows 身份验证：数据库邮件使用 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] Windows 服务帐户的凭据在 SMTP 服务器中进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="b022e-116">Windows Authentication: Database Mail uses the credentials of the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] Windows service account for authentication on the SMTP server.</span></span>  
  
-   <span data-ttu-id="b022e-117">基本身份验证：数据库邮件使用指定的用户名和密码在 SMTP 服务器上进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="b022e-117">Basic Authentication:  Database Mail uses the username and password specified to authenticate on the SMTP server.</span></span>  
  
-   <span data-ttu-id="b022e-118">匿名身份验证：SMTP 服务器不要求进行任何身份验证。</span><span class="sxs-lookup"><span data-stu-id="b022e-118">Anonymous Authentication:  The SMTP server does not require any authentication.</span></span>  <span data-ttu-id="b022e-119">数据库邮件将不使用任何凭据在 SMTP 服务器上进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="b022e-119">Database Mail will not use any credentials to authenticate on the SMTP server.</span></span>  
  
 <span data-ttu-id="b022e-120">帐户信息存储在 **msdb** 数据库中。</span><span class="sxs-lookup"><span data-stu-id="b022e-120">Account information is stored in the **msdb** database.</span></span> <span data-ttu-id="b022e-121">每个帐户包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="b022e-121">Each account consists of the following information:</span></span>  
  
-   <span data-ttu-id="b022e-122">帐户名称。</span><span class="sxs-lookup"><span data-stu-id="b022e-122">The name of the account.</span></span>  
  
-   <span data-ttu-id="b022e-123">帐户的说明。</span><span class="sxs-lookup"><span data-stu-id="b022e-123">A description of the account.</span></span>  
  
-   <span data-ttu-id="b022e-124">帐户的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="b022e-124">The e-mail address of the account.</span></span>  
  
-   <span data-ttu-id="b022e-125">帐户的显示名称。</span><span class="sxs-lookup"><span data-stu-id="b022e-125">The display name for the account.</span></span>  
  
-   <span data-ttu-id="b022e-126">用作帐户的答复信息的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="b022e-126">The e-mail address to use as the reply-to information for the account.</span></span>  
  
-   <span data-ttu-id="b022e-127">电子邮件服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="b022e-127">The name of the e-mail server.</span></span>  
  
-   <span data-ttu-id="b022e-128">电子邮件服务器的类型。</span><span class="sxs-lookup"><span data-stu-id="b022e-128">The type of the e-mail server.</span></span> <span data-ttu-id="b022e-129">对于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，其类型始终为简单邮件传输协议 (SMTP)。</span><span class="sxs-lookup"><span data-stu-id="b022e-129">For [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this is always Simple Mail Transfer Protocol(SMTP).</span></span>  
  
-   <span data-ttu-id="b022e-130">电子邮件服务器的端口号。</span><span class="sxs-lookup"><span data-stu-id="b022e-130">The port number of the e-mail server.</span></span>  
  
-   <span data-ttu-id="b022e-131">用于指示是否使用安全套接字层 (SSL) 与 SMTP 邮件服务器建立连接的位列。</span><span class="sxs-lookup"><span data-stu-id="b022e-131">A bit column indicating whether the connection to the SMTP mail server is made using Secure Sockets Layer (SSL).</span></span>  
  
-   <span data-ttu-id="b022e-132">用于指示是否使用为 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]配置的凭据与 SMTP 服务器建立连接的位列。</span><span class="sxs-lookup"><span data-stu-id="b022e-132">A bit column indicating whether the connection to the SMTP server is made using the credentials configured for the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="b022e-133">用于电子邮件服务器身份验证的用户名（如果电子邮件服务器需要身份验证）。</span><span class="sxs-lookup"><span data-stu-id="b022e-133">The user name to use for authentication to the e-mail server, if the e-mail server requires authentication.</span></span>  
  
-   <span data-ttu-id="b022e-134">用于电子邮件服务器身份验证的密码（如果电子邮件服务器需要身份验证）。</span><span class="sxs-lookup"><span data-stu-id="b022e-134">The password to use for authentication to the e-mail server, if the e-mail server requires authentication.</span></span>  
  
 <span data-ttu-id="b022e-135">使用数据库邮件配置向导可以方便地创建和管理帐户。</span><span class="sxs-lookup"><span data-stu-id="b022e-135">The Database Mail Configuration Wizard provides a convenient way to create and manage accounts.</span></span> <span data-ttu-id="b022e-136">还可以使用 **msdb** 中的配置存储过程来创建和管理帐户。</span><span class="sxs-lookup"><span data-stu-id="b022e-136">You can also use the configuration stored procedures in **msdb** to create and manage accounts.</span></span>  
  
  
##  <a name="database-mail-profile"></a><a name="DBProfile"></a> <span data-ttu-id="b022e-137">数据库邮件配置文件</span><span class="sxs-lookup"><span data-stu-id="b022e-137">Database Mail Profile</span></span>  
 <span data-ttu-id="b022e-138">数据库邮件配置文件是相关数据库邮件帐户的有序集合。</span><span class="sxs-lookup"><span data-stu-id="b022e-138">A Database Mail profile is an ordered collection of related Database Mail accounts.</span></span> <span data-ttu-id="b022e-139">配置文件将由使用数据库邮件（而不是直接使用帐户）来发送电子邮件的应用程序指定。</span><span class="sxs-lookup"><span data-stu-id="b022e-139">Applications that send e-mail using Database Mail specify profiles, instead of using accounts directly.</span></span> <span data-ttu-id="b022e-140">将单个电子邮件服务器的信息与应用程序使用的对象分隔可以提高灵活性和可靠性：配置文件提供自动故障转移，因此如果一个电子邮件服务器停止响应，数据库邮件可以自动将邮件发送到另一个电子邮件服务器。</span><span class="sxs-lookup"><span data-stu-id="b022e-140">Separating information about the individual e-mail servers from the objects that the application uses improves flexibility and reliability: profiles provide automatic failover, so that if one e-mail server is unresponsive, Database Mail can automatically send mail to another e-mail server.</span></span> <span data-ttu-id="b022e-141">数据库管理员可以添加、删除或重新配置帐户，而不需要更改应用程序代码或作业步骤。</span><span class="sxs-lookup"><span data-stu-id="b022e-141">Database administrators can add, remove, or reconfigure accounts without requiring changes to application code or job steps.</span></span>  
  
 <span data-ttu-id="b022e-142">配置文件还有助于数据库管理员控制对电子邮件的访问。</span><span class="sxs-lookup"><span data-stu-id="b022e-142">Profiles also help database administrators control access to e-mail.</span></span> <span data-ttu-id="b022e-143">若要发送数据库邮件，必须具有 **DatabaseMailUserRole** 中的成员身份。</span><span class="sxs-lookup"><span data-stu-id="b022e-143">Membership in the **DatabaseMailUserRole** is required to send Database Mail.</span></span> <span data-ttu-id="b022e-144">配置文件使管理员可以更加灵活地控制谁来发送邮件以及使用哪些帐户。</span><span class="sxs-lookup"><span data-stu-id="b022e-144">Profiles provide additional flexibility for administrators to control who sends mail and which accounts are used.</span></span>  
  
 <span data-ttu-id="b022e-145">配置文件可以是公共的，也可以是专用的。</span><span class="sxs-lookup"><span data-stu-id="b022e-145">A profile may be public or private.</span></span>  
  
 <span data-ttu-id="b022e-146">**公共配置文件** 对 **msdb** 数据库中的 **DatabaseMailUserRole** 数据库角色的所有成员都可用。</span><span class="sxs-lookup"><span data-stu-id="b022e-146">**Public profiles** are available for all members of the **DatabaseMailUserRole** database role in the **msdb** database.</span></span> <span data-ttu-id="b022e-147">它们允许 **DatabaseMailUserRole** 角色的所有成员使用该配置文件发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="b022e-147">They allow all members of the **DatabaseMailUserRole** role to send e-mail using the profile.</span></span>  
  
 <span data-ttu-id="b022e-148">**专用配置文件** 为 **msdb** 数据库中的安全主体而定义。</span><span class="sxs-lookup"><span data-stu-id="b022e-148">**Private profiles** are defined for security principals in the **msdb** database.</span></span> <span data-ttu-id="b022e-149">它们仅允许指定的数据库用户、角色和 **sysadmin** 固定服务器角色的成员来使用该配置文件发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="b022e-149">They allow only specified database users, roles, and members of the **sysadmin** fixed server role to send e-mail using the profile.</span></span> <span data-ttu-id="b022e-150">默认情况下，配置文件是专用的，而且仅允许 **sysadmin** 固定服务器角色的成员访问。</span><span class="sxs-lookup"><span data-stu-id="b022e-150">By default, a profile is private, and allows access only to members of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="b022e-151">若要使用专用配置文件， **sysadmin** 必须授予用户使用该配置文件的权限。</span><span class="sxs-lookup"><span data-stu-id="b022e-151">To use a private profile, **sysadmin** must grant users permission to use the profile.</span></span> <span data-ttu-id="b022e-152">此外， **sp_send_dbmail** 存储过程的 EXECUTE 权限只授予 **DatabaseMailUserRole**成员。</span><span class="sxs-lookup"><span data-stu-id="b022e-152">Additionally, EXECUTE permission on the **sp_send_dbmail** stored procedure is only granted to members of the **DatabaseMailUserRole**.</span></span> <span data-ttu-id="b022e-153">系统管理员必须将用户添加到 **DatabaseMailUserRole** 数据库角色，该用户才能发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="b022e-153">A system administrator must add the user to the **DatabaseMailUserRole** database role for the user to send e-mail messages.</span></span>  
  
 <span data-ttu-id="b022e-154">在电子邮件服务器无法访问或无法处理邮件的情况下，配置文件可提高可靠性。</span><span class="sxs-lookup"><span data-stu-id="b022e-154">Profiles improve reliability in cases where an e-mail server becomes unreachable or unable to process messages.</span></span> <span data-ttu-id="b022e-155">配置文件中的每个帐户都有一个序列号。</span><span class="sxs-lookup"><span data-stu-id="b022e-155">Each account in the profile has a sequence number.</span></span> <span data-ttu-id="b022e-156">序列号可以确定数据库邮件使用配置文件中帐户的顺序。</span><span class="sxs-lookup"><span data-stu-id="b022e-156">The sequence number determines the order in which Database Mail uses accounts in the profile.</span></span> <span data-ttu-id="b022e-157">对于新的电子邮件，数据库邮件将使用最后一个成功发送邮件的帐户；如果尚未发送邮件，则使用序列号最小的帐户。</span><span class="sxs-lookup"><span data-stu-id="b022e-157">For a new e-mail message, Database Mail uses the last account that sent a message successfully, or the account that has the lowest sequence number if no message has yet been sent.</span></span> <span data-ttu-id="b022e-158">如果该帐户失败，数据库邮件就使用具有下一个序列号较大的帐户，依此类推，直到数据库邮件成功发送邮件，或者序列号最大的帐户也失败为止。</span><span class="sxs-lookup"><span data-stu-id="b022e-158">Should that account fail, Database Mail uses the account with the next highest sequence number, and so on until either Database Mail sends the message successfully, or the account with the highest sequence number fails.</span></span> <span data-ttu-id="b022e-159">如果序列号最大的帐户失败，数据库邮件将暂停尝试发送邮件，暂停时间在 **sysmail_configure_sp** 的 **AccountRetryDelay**参数中配置，然后从最小序列号再次开始尝试发送邮件的过程。</span><span class="sxs-lookup"><span data-stu-id="b022e-159">If the account with the highest sequence number fails, the Database Mail pauses attempts to send the mail for the amount of time configured in the **AccountRetryDelay** parameter of **sysmail_configure_sp**, then starts the process of attempting to send the mail again, starting with the lowest sequence number.</span></span> <span data-ttu-id="b022e-160">使用 **sysmail_configure_sp** 的 **AccountRetryAttempts**参数可以配置外部邮件进程尝试使用指定配置文件中的每个帐户发送电子邮件的次数。</span><span class="sxs-lookup"><span data-stu-id="b022e-160">Use the **AccountRetryAttempts** parameter of **sysmail_configure_sp**, to configure the number of times that the external mail process attempts to send the e-mail message using each account in the specified profile.</span></span>  
  
 <span data-ttu-id="b022e-161">如果存在具有相同序列号的多个帐户，则数据库邮件将仅使用其中一个帐户发送给定的电子邮件。</span><span class="sxs-lookup"><span data-stu-id="b022e-161">If more than one account exists with the same sequence number, Database Mail only uses one of those accounts for a given e-mail message.</span></span> <span data-ttu-id="b022e-162">在此情况下，数据库邮件不能保证使用具有该序列号的特定帐户，也不能保证使用同一个帐户发送各个邮件。</span><span class="sxs-lookup"><span data-stu-id="b022e-162">In this case, Database Mail makes no guarantees as to which of the accounts is used for that sequence number or that the same account is used from message to message.</span></span>  
  
  
##  <a name="database-mail-configuration-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="b022e-163">数据库邮件配置任务</span><span class="sxs-lookup"><span data-stu-id="b022e-163">Database Mail Configuration Tasks</span></span>  
 <span data-ttu-id="b022e-164">下表介绍了数据库邮件配置任务。</span><span class="sxs-lookup"><span data-stu-id="b022e-164">The following table describes the Database Mail configuration tasks.</span></span>  
  
|<span data-ttu-id="b022e-165">配置任务</span><span class="sxs-lookup"><span data-stu-id="b022e-165">Configuration Task</span></span>|<span data-ttu-id="b022e-166">主题链接</span><span class="sxs-lookup"><span data-stu-id="b022e-166">Topic Link</span></span>|  
|------------------------|----------------|  
|<span data-ttu-id="b022e-167">介绍如何创建数据库邮件帐户</span><span class="sxs-lookup"><span data-stu-id="b022e-167">Describes how to create a Database Mail accounts</span></span>|[<span data-ttu-id="b022e-168">创建数据库邮件帐户</span><span class="sxs-lookup"><span data-stu-id="b022e-168">Create a Database Mail Account</span></span>](create-a-database-mail-account.md)|  
|<span data-ttu-id="b022e-169">介绍如何创建数据库邮件配置文件</span><span class="sxs-lookup"><span data-stu-id="b022e-169">Describes how to Create Database Mail profiles</span></span>|[<span data-ttu-id="b022e-170">创建数据库邮件配置文件</span><span class="sxs-lookup"><span data-stu-id="b022e-170">Create a Database Mail Profile</span></span>](create-a-database-mail-profile.md)|  
|<span data-ttu-id="b022e-171">介绍如何配置数据库邮件</span><span class="sxs-lookup"><span data-stu-id="b022e-171">Describes how to Configure Database mail</span></span>|[<span data-ttu-id="b022e-172">配置数据库邮件</span><span class="sxs-lookup"><span data-stu-id="b022e-172">Configure Database Mail</span></span>](configure-database-mail.md)|  
|<span data-ttu-id="b022e-173">介绍如何使用模板创建数据库邮件配置脚本</span><span class="sxs-lookup"><span data-stu-id="b022e-173">Describes how to create a Database Mail configuration script using templates</span></span>||  
  
  
##  <a name="additional-database-configuration-tasks-system-stored-procedures"></a><a name="Add_Tasks"></a> <span data-ttu-id="b022e-174">附加数据库配置任务（系统存储过程）</span><span class="sxs-lookup"><span data-stu-id="b022e-174">Additional Database Configuration Tasks (System Stored Procedures)</span></span>  
 <span data-ttu-id="b022e-175">数据库邮件配置存储过程位于 **msdb** 数据库中。</span><span class="sxs-lookup"><span data-stu-id="b022e-175">Database Mail configuration stored procedures are located in the **msdb** database.</span></span>  
  
 <span data-ttu-id="b022e-176">以下几个表列出了用于配置和管理数据库邮件的存储过程。</span><span class="sxs-lookup"><span data-stu-id="b022e-176">The following tables list the stored procedures used for configuring and managing Database Mail.</span></span>  
  
### <a name="database-mail-settings"></a><span data-ttu-id="b022e-177">数据库邮件设置</span><span class="sxs-lookup"><span data-stu-id="b022e-177">Database Mail Settings</span></span>  
  
|<span data-ttu-id="b022e-178">名称</span><span class="sxs-lookup"><span data-stu-id="b022e-178">Name</span></span>|<span data-ttu-id="b022e-179">说明</span><span class="sxs-lookup"><span data-stu-id="b022e-179">Description</span></span>|  
|----------|-----------------|  
|[<span data-ttu-id="b022e-180">sysmail_configure_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b022e-180">sysmail_configure_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql)|<span data-ttu-id="b022e-181">更改数据库邮件的配置设置。</span><span class="sxs-lookup"><span data-stu-id="b022e-181">Changes configuration settings for Database Mail.</span></span>|  
|[<span data-ttu-id="b022e-182">sysmail_help_configure_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b022e-182">sysmail_help_configure_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-help-configure-sp-transact-sql)|<span data-ttu-id="b022e-183">显示数据库邮件的配置设置。</span><span class="sxs-lookup"><span data-stu-id="b022e-183">Displays configuration settings for Database Mail.</span></span>|  
  
### <a name="accounts-and-profiles"></a><span data-ttu-id="b022e-184">帐户和配置文件</span><span class="sxs-lookup"><span data-stu-id="b022e-184">Accounts and Profiles</span></span>  
  
|<span data-ttu-id="b022e-185">名称</span><span class="sxs-lookup"><span data-stu-id="b022e-185">Name</span></span>|<span data-ttu-id="b022e-186">说明</span><span class="sxs-lookup"><span data-stu-id="b022e-186">Description</span></span>|  
|----------|-----------------|  
|[<span data-ttu-id="b022e-187">sysmail_add_profileaccount_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b022e-187">sysmail_add_profileaccount_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql)|<span data-ttu-id="b022e-188">将邮件帐户添加到数据库邮件配置文件中。</span><span class="sxs-lookup"><span data-stu-id="b022e-188">Adds a mail account to a Database Mail profile.</span></span>|  
|[<span data-ttu-id="b022e-189">sysmail_delete_account_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b022e-189">sysmail_delete_account_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-account-sp-transact-sql)|<span data-ttu-id="b022e-190">删除数据库邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="b022e-190">Deletes a Database Mail account.</span></span>|  
|[<span data-ttu-id="b022e-191">sysmail_delete_profile_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b022e-191">sysmail_delete_profile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-profile-sp-transact-sql)|<span data-ttu-id="b022e-192">删除数据库邮件配置文件。</span><span class="sxs-lookup"><span data-stu-id="b022e-192">Deletes a Database Mail profile.</span></span>|  
|[<span data-ttu-id="b022e-193">sysmail_delete_profileaccount_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b022e-193">sysmail_delete_profileaccount_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-profileaccount-sp-transact-sql)|<span data-ttu-id="b022e-194">从数据库邮件配置文件中删除帐户。</span><span class="sxs-lookup"><span data-stu-id="b022e-194">Removes an account from a Database Mail profile.</span></span>|  
|[<span data-ttu-id="b022e-195">sysmail_help_account_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b022e-195">sysmail_help_account_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-help-account-sp-transact-sql)|<span data-ttu-id="b022e-196">列出有关数据库邮件帐户的信息。</span><span class="sxs-lookup"><span data-stu-id="b022e-196">Lists information about Database Mail accounts.</span></span>|  
|[<span data-ttu-id="b022e-197">sysmail_help_profile_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b022e-197">sysmail_help_profile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-help-profile-sp-transact-sql)|<span data-ttu-id="b022e-198">列出有关一个或多个数据库邮件配置文件的信息。</span><span class="sxs-lookup"><span data-stu-id="b022e-198">Lists information about one or more Database Mail profiles.</span></span>|  
|[<span data-ttu-id="b022e-199">sysmail_help_profileaccount_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b022e-199">sysmail_help_profileaccount_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-help-profileaccount-sp-transact-sql)|<span data-ttu-id="b022e-200">列出与一个或多个数据库邮件配置文件相关联的帐户。</span><span class="sxs-lookup"><span data-stu-id="b022e-200">Lists the accounts associated with one or more Database Mail profiles.</span></span>|  
|[<span data-ttu-id="b022e-201">sysmail_update_account_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b022e-201">sysmail_update_account_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-update-account-sp-transact-sql)|<span data-ttu-id="b022e-202">更新现有数据库邮件帐户中的信息。</span><span class="sxs-lookup"><span data-stu-id="b022e-202">Updates the information in an existing Database Mail account.</span></span>|  
|[<span data-ttu-id="b022e-203">sysmail_update_profile_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b022e-203">sysmail_update_profile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-update-profile-sp-transact-sql)|<span data-ttu-id="b022e-204">更改数据库邮件配置文件的说明或名称。</span><span class="sxs-lookup"><span data-stu-id="b022e-204">Changes the description or name of a Database Mail profile.</span></span>|  
|[<span data-ttu-id="b022e-205">sysmail_update_profileaccount_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b022e-205">sysmail_update_profileaccount_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-update-profileaccount-sp-transact-sql)|<span data-ttu-id="b022e-206">更新数据库邮件配置文件中帐户的序列号。</span><span class="sxs-lookup"><span data-stu-id="b022e-206">Updates the sequence number of an account within a Database Mail profile.</span></span>|  
  
### <a name="security"></a><span data-ttu-id="b022e-207">安全性</span><span class="sxs-lookup"><span data-stu-id="b022e-207">Security</span></span>  
  
|<span data-ttu-id="b022e-208">名称</span><span class="sxs-lookup"><span data-stu-id="b022e-208">Name</span></span>|<span data-ttu-id="b022e-209">说明</span><span class="sxs-lookup"><span data-stu-id="b022e-209">Description</span></span>|  
|----------|-----------------|  
|[<span data-ttu-id="b022e-210">sysmail_add_principalprofile_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b022e-210">sysmail_add_principalprofile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql)|<span data-ttu-id="b022e-211">授予数据库主体使用数据库邮件配置文件的权限。</span><span class="sxs-lookup"><span data-stu-id="b022e-211">Grants permission for a database principal to use a Database Mail profile.</span></span>|  
|[<span data-ttu-id="b022e-212">sysmail_delete_principalprofile_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b022e-212">sysmail_delete_principalprofile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-principalprofile-sp-transact-sql)|<span data-ttu-id="b022e-213">删除数据库用户使用公共或专用数据库邮件配置文件的权限。</span><span class="sxs-lookup"><span data-stu-id="b022e-213">Removes permission for a database user to use a public or private Database Mail profile.</span></span>|  
|[<span data-ttu-id="b022e-214">sysmail_help_principalprofile_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b022e-214">sysmail_help_principalprofile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-help-principalprofile-sp-transact-sql)|<span data-ttu-id="b022e-215">列出所给数据库用户的数据库邮件配置文件信息。</span><span class="sxs-lookup"><span data-stu-id="b022e-215">Lists Database Mail profile information for a given database user.</span></span>|  
|[<span data-ttu-id="b022e-216">sysmail_update_principalprofile_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b022e-216">sysmail_update_principalprofile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-update-principalprofile-sp-transact-sql)|<span data-ttu-id="b022e-217">更新所给数据库用户的权限信息。</span><span class="sxs-lookup"><span data-stu-id="b022e-217">Updates the permission information for a given database user.</span></span>|  
  
### <a name="system-state"></a><span data-ttu-id="b022e-218">系统状态</span><span class="sxs-lookup"><span data-stu-id="b022e-218">System State</span></span>  
  
|<span data-ttu-id="b022e-219">名称</span><span class="sxs-lookup"><span data-stu-id="b022e-219">Name</span></span>|<span data-ttu-id="b022e-220">说明</span><span class="sxs-lookup"><span data-stu-id="b022e-220">Description</span></span>|  
|----------|-----------------|  
|[<span data-ttu-id="b022e-221">sysmail_start_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b022e-221">sysmail_start_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-start-sp-transact-sql)|<span data-ttu-id="b022e-222">启动数据库邮件外部程序和关联的 SQL Service Broker 队列。</span><span class="sxs-lookup"><span data-stu-id="b022e-222">Starts the Database Mail external program and the associated SQL Service Broker queue.</span></span>|  
|[<span data-ttu-id="b022e-223">sysmail_stop_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b022e-223">sysmail_stop_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-stop-sp-transact-sql)|<span data-ttu-id="b022e-224">停止数据库邮件外部程序和关联的 SQL Service Broker 队列。</span><span class="sxs-lookup"><span data-stu-id="b022e-224">Stops the Database Mail external program and the associated SQL Service Broker queue.</span></span>|  
|[<span data-ttu-id="b022e-225">sysmail_help_status_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b022e-225">sysmail_help_status_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-help-status-sp-transact-sql)|<span data-ttu-id="b022e-226">指示数据库邮件是否已启动。</span><span class="sxs-lookup"><span data-stu-id="b022e-226">Indicates if Database Mail is started.</span></span>|  
  
##  <a name="additional-references"></a><a name="RelatedContent"></a> <span data-ttu-id="b022e-227">其他参考</span><span class="sxs-lookup"><span data-stu-id="b022e-227">Additional References</span></span>  
  
-   [<span data-ttu-id="b022e-228">数据库邮件日志和审核</span><span class="sxs-lookup"><span data-stu-id="b022e-228">Database Mail Log and Audits</span></span>](database-mail-log-and-audits.md)  
  
  
  
