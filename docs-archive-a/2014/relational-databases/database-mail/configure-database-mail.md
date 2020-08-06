---
title: 配置数据库邮件 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- Sql12.swb.sqlimail.newaccount.f1
- Sql12.swb.sqlimail.manageexistingaccount.f1
- Sql12.swb.dbmail.manageexistingaccount.f1
- Sql12.swb.sqlimail.manageexistingprofile.f1
- Sql12.swb.sqlimail.newprofile.f1
- Sql12.swb.sqlimail.profileandaccountmanagement.f1
- Sql12.swb.dbmail.configuresystem.f1
- Sql12.swb.dbmail.profileandaccountmanagement.f1
- Sql12.swb.dbmail. manageprofilesecurity.profileview.f1
- Sql12.swb.dbmail.selectconfiguration.f1
- Sql12.swb.dbmail.newsqlimailaccount.f1
- Sql12.swb.sqlimail.manageprofilesecurity.profileview.f1
- Sql12.swb.sqlimail.newsqlimailaccount.f1
- Sql12.swb.dbmail.newaccount.f1
- Sql12.swb.dbmail.manageexistingprofile.f1
- Sql12.swb.sqlimail.configuresystem.f1
- Sql12.swb.sqlimail.selectconfiguration.f1
- Sql12.swb.dbmail.completewizard.f1
- Sql12.swb.sqlimail.welcome.f1
- sql12.swb.dbmail.sendtestemail.f1
- Sql12.swb.sqlimail.addaccounttoprofile.f1
- Sql12.swb.dbmail.welcome.f1
- Sql12.swb.dbmail.newprofile.f1
- Sql12.swb.dbmail.addaccounttoprofile.f1
- sql12.swb.dbmail.sendtestemail.test.f1
- Sql12.swb.sqlimail.completewizard.f1
- Sql12.swb.sqlimail.manageprofilesecurity.principalview.f1
- Sql12.swb.dbmail.manageprofilesecurity.principalview.f1
ms.assetid: 7edc21d4-ccf3-42a9-84c0-3f70333efce6
author: stevestein
ms.author: sstein
ms.openlocfilehash: cbf9af4b5af3043c6ca8fa2cba01ebe43019fb41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591369"
---
# <a name="configure-database-mail"></a><span data-ttu-id="72737-102">配置数据库邮件</span><span class="sxs-lookup"><span data-stu-id="72737-102">Configure Database Mail</span></span>
  <span data-ttu-id="72737-103">本主题说明如何使用数据库邮件配置向导启用和配置数据库邮件，以及使用模板创建数据库邮件配置脚本。</span><span class="sxs-lookup"><span data-stu-id="72737-103">This topic describes how to enable and configure Database Mail using the Database Mail Configuration Wizard, and create a Database Mail Configuration script using templates.</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="72737-104">开始之前</span><span class="sxs-lookup"><span data-stu-id="72737-104">Before You Begin</span></span>  
 <span data-ttu-id="72737-105">使用 **DatabaseMail XPs** 选项可以在此服务器上启用数据库邮件。</span><span class="sxs-lookup"><span data-stu-id="72737-105">Use the **DatabaseMail XPs** option to enable Database Mail on this server.</span></span> <span data-ttu-id="72737-106">有关详细信息，请参阅主题 [Database Mail XPs Server 配置选项](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md) 。</span><span class="sxs-lookup"><span data-stu-id="72737-106">For more information, see [Database Mail XPs Server Configuration Option](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md) reference topic.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="72737-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="72737-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="72737-108">在任何数据库中启用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Broker 都需要数据库锁。</span><span class="sxs-lookup"><span data-stu-id="72737-108">Enabling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Broker in any database requires a database lock.</span></span> <span data-ttu-id="72737-109">如果在 **msdb**中停用了 Service Broker，则若要启用数据库邮件，应首先停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理，以使 Service Broker 可以获取所需的锁。</span><span class="sxs-lookup"><span data-stu-id="72737-109">If Service Broker was deactivated in **msdb**, to enable Database Mail, first stop [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent so Service Broker can obtain the necessary lock.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="72737-110">Security</span><span class="sxs-lookup"><span data-stu-id="72737-110">Security</span></span>  
 <span data-ttu-id="72737-111">要配置数据库邮件，您必须是 **sysadmin** 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="72737-111">To configure Database Mail you must be a member of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="72737-112">若要发送数据库邮件，您必须是 **msdb** 数据库中的 **DatabaseMailUserRole** 数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="72737-112">To send Database Mail you must be a member of the **DatabaseMailUserRole** database role in the **msdb** database.</span></span>  
  
##  <a name="using-database-mail-configuration-wizard"></a><a name="SSMSProcedure"></a> <span data-ttu-id="72737-113">使用数据库邮件配置向导</span><span class="sxs-lookup"><span data-stu-id="72737-113">Using Database Mail Configuration Wizard</span></span>  
 <span data-ttu-id="72737-114">**使用向导配置数据库邮件**</span><span class="sxs-lookup"><span data-stu-id="72737-114">**To configure Database Mail using a wizard**</span></span>  
  
1.  <span data-ttu-id="72737-115">在对象资源管理器中，展开要配置数据库邮件的实例所在节点。</span><span class="sxs-lookup"><span data-stu-id="72737-115">In Object Explorer, expand the node for the instance  you want to configure Database mail.</span></span>  
  
2.  <span data-ttu-id="72737-116">展开 "**管理**" 节点。</span><span class="sxs-lookup"><span data-stu-id="72737-116">Expand the **Management** node.</span></span>  
  
3.  <span data-ttu-id="72737-117">右键单击“数据库邮件”\*\*\*\* 然后单击“配置数据库邮件”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="72737-117">Right-click **Database Mail**, and then click **Configure Database Mail**.</span></span>  
  
4.  <span data-ttu-id="72737-118">完成向导对话框</span><span class="sxs-lookup"><span data-stu-id="72737-118">Complete the Wizard dialogs</span></span>  
  

  
  
  
###  <a name="welcome-page"></a><a name="Welcome"></a><span data-ttu-id="72737-119">欢迎页</span><span class="sxs-lookup"><span data-stu-id="72737-119">Welcome Page</span></span>  
 <span data-ttu-id="72737-120">此页说明配置数据库邮件的步骤。</span><span class="sxs-lookup"><span data-stu-id="72737-120">This page describes the steps to configuring Database Mail.</span></span>  
  
 <span data-ttu-id="72737-121">不再**显示此页**-选中此选项可跳过此欢迎页在以后显示。</span><span class="sxs-lookup"><span data-stu-id="72737-121">**Do not show this page again** - Check this to skip this welcome page from displaying in the future.</span></span>  
  
 <span data-ttu-id="72737-122">**下一步** - 继续到“选择配置任务”\*\*\*\* 页。</span><span class="sxs-lookup"><span data-stu-id="72737-122">**Next** - Proceeds to the **Select a configuration task** page.</span></span>  
  
 <span data-ttu-id="72737-123">**取消** - 终止向导而无需配置数据库邮件</span><span class="sxs-lookup"><span data-stu-id="72737-123">**Cancel** - Terminates the wizard without configuring Database Mail</span></span>  
  
 
  
###  <a name="select-configuration-task"></a><a name="ConfigTask"></a><span data-ttu-id="72737-124">选择配置任务</span><span class="sxs-lookup"><span data-stu-id="72737-124">Select Configuration Task</span></span>  
 <span data-ttu-id="72737-125">使用 **“选择配置任务”** 页可以指示每次使用此向导时要完成的任务。</span><span class="sxs-lookup"><span data-stu-id="72737-125">Use the **Select Configuration Task** page, to indicate which task you will complete each time you use the wizard.</span></span> <span data-ttu-id="72737-126">如果您在完成向导前改变了主意，请使用 **“上一步”** 按钮返回此页并选择其他任务。</span><span class="sxs-lookup"><span data-stu-id="72737-126">If you change your mind before you complete the wizard, use the **Back** button to return to this page and select a different task.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="72737-127">如果数据库邮件尚未启用，您将收到以下消息： **“数据库邮件功能不可用。是否要启用此功能？**</span><span class="sxs-lookup"><span data-stu-id="72737-127">If Database Mail has not been enabled, you will receive the message: **The Database Mail feature is not available.  Would you like to enable this feature?**</span></span> <span data-ttu-id="72737-128">回答“是”\*\*\*\* 相当于使用 **sp_configure** 系统存储过程的 [Mail XPs 选项](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md)启用数据库邮件。</span><span class="sxs-lookup"><span data-stu-id="72737-128">Responding **Yes**, is equivalent to enabling Database Mail by using the [Database Mail XPs option](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md) of the **sp_configure** system stored procedure.</span></span>  
  
 <span data-ttu-id="72737-129">**通过执行以下任务来设置数据库邮件**</span><span class="sxs-lookup"><span data-stu-id="72737-129">**Set up Database Mail by performing the following tasks**</span></span>  
 <span data-ttu-id="72737-130">执行第一次设置数据库邮件所需的所有任务。</span><span class="sxs-lookup"><span data-stu-id="72737-130">Perform all of the tasks required to set up Database Mail for the first time.</span></span> <span data-ttu-id="72737-131">此选项包含所有其他三个选项。</span><span class="sxs-lookup"><span data-stu-id="72737-131">This option includes all of the other three options.</span></span>  
  
 <span data-ttu-id="72737-132">**管理数据库邮件帐户和配置文件**</span><span class="sxs-lookup"><span data-stu-id="72737-132">**Manage Database Mail accounts and profiles**</span></span>  
 <span data-ttu-id="72737-133">创建新的数据库邮件帐户和配置文件，或者查看、更改或删除现有数据库邮件帐户和配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-133">Create new Database Mail accounts and profiles or to view, change, or delete existing Database Mail accounts and profiles.</span></span>  
  
 <span data-ttu-id="72737-134">**管理配置文件安全性**</span><span class="sxs-lookup"><span data-stu-id="72737-134">**Manage profile security**</span></span>  
 <span data-ttu-id="72737-135">配置对数据库邮件配置文件具有访问权限的用户。</span><span class="sxs-lookup"><span data-stu-id="72737-135">Configure which users have access to Database Mail profiles.</span></span>  
  
 <span data-ttu-id="72737-136">**查看或更改系统参数**</span><span class="sxs-lookup"><span data-stu-id="72737-136">**View or change system parameters**</span></span>  
 <span data-ttu-id="72737-137">配置数据库邮件系统参数，例如附件的最大文件大小。</span><span class="sxs-lookup"><span data-stu-id="72737-137">Configure Database Mail system parameters such as the maximum file size for attachments.</span></span>  
  

  
###  <a name="new-account-page"></a><a name="NewAccount"></a><span data-ttu-id="72737-138">"新建帐户" 页</span><span class="sxs-lookup"><span data-stu-id="72737-138">New Account Page</span></span>  
 <span data-ttu-id="72737-139">使用此页可以创建新的数据库邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="72737-139">Use this page to create a new Database Mail account.</span></span> <span data-ttu-id="72737-140">数据库邮件帐户包含向 SMTP 服务器发送电子邮件所需的信息。</span><span class="sxs-lookup"><span data-stu-id="72737-140">A Database Mail account contains information for sending e-mail to an SMTP server.</span></span>  
  
 <span data-ttu-id="72737-141">数据库邮件帐户包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 向 SMTP 服务器发送电子邮件所需的信息。</span><span class="sxs-lookup"><span data-stu-id="72737-141">A Database Mail account contains the information that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses to send e-mail messages to an SMTP server.</span></span> <span data-ttu-id="72737-142">每个帐户均包含一个电子邮件服务器的信息。</span><span class="sxs-lookup"><span data-stu-id="72737-142">Each account contains information for one e-mail server.</span></span>  
  
 <span data-ttu-id="72737-143">数据库邮件帐户仅用于数据库邮件。</span><span class="sxs-lookup"><span data-stu-id="72737-143">A Database Mail account is only used for Database Mail.</span></span> <span data-ttu-id="72737-144">数据库邮件帐户与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户或 Microsoft Windows 帐户之间不相互对应。</span><span class="sxs-lookup"><span data-stu-id="72737-144">A Database Mail account does not correspond to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account or a Microsoft Windows account.</span></span> <span data-ttu-id="72737-145">可以利用 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的凭据或您提供的其他凭据发送数据库邮件，也可以用匿名方式发送。</span><span class="sxs-lookup"><span data-stu-id="72737-145">Database Mail can be sent using the credentials of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], using other credentials that you supply, or anonymously.</span></span> <span data-ttu-id="72737-146">使用基本身份验证时，数据库邮件帐户中的用户名和密码仅用于在电子邮件服务器中进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="72737-146">When using basic authentication, the user name and password in a Database Mail account are only used for authentication with the e-mail server.</span></span> <span data-ttu-id="72737-147">帐户无需与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用户或运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的计算机上的用户对应。</span><span class="sxs-lookup"><span data-stu-id="72737-147">An account need not correspond to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user or a user on the computer running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="72737-148">**帐户名称**</span><span class="sxs-lookup"><span data-stu-id="72737-148">**Account name**</span></span>  
 <span data-ttu-id="72737-149">键入新帐户的名称。</span><span class="sxs-lookup"><span data-stu-id="72737-149">Type the name of the new account.</span></span>  
  
 <span data-ttu-id="72737-150">**说明**</span><span class="sxs-lookup"><span data-stu-id="72737-150">**Description**</span></span>  
 <span data-ttu-id="72737-151">键入帐户的说明。</span><span class="sxs-lookup"><span data-stu-id="72737-151">Type a description of the account.</span></span> <span data-ttu-id="72737-152">说明是可选的。</span><span class="sxs-lookup"><span data-stu-id="72737-152">The description is optional.</span></span>  
  
 <span data-ttu-id="72737-153">**电子邮件地址**</span><span class="sxs-lookup"><span data-stu-id="72737-153">**E-mail address**</span></span>  
 <span data-ttu-id="72737-154">键入帐户电子邮件地址的名称。</span><span class="sxs-lookup"><span data-stu-id="72737-154">Type the name of the e-mail address for the account.</span></span> <span data-ttu-id="72737-155">这是发送电子邮件的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="72737-155">This is the e-mail address that e-mail is sent from.</span></span> <span data-ttu-id="72737-156">例如， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的帐户可能会通过地址 SqlAgent@Adventure-Works.com 发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="72737-156">For example, an account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent may send e-mail from the address SqlAgent@Adventure-Works.com.</span></span>  
  
 <span data-ttu-id="72737-157">**显示名称**</span><span class="sxs-lookup"><span data-stu-id="72737-157">**Display name**</span></span>  
 <span data-ttu-id="72737-158">键入由此帐户发送的电子邮件上显示的名称。</span><span class="sxs-lookup"><span data-stu-id="72737-158">Type the name to show on e-mail messages sent from this account.</span></span> <span data-ttu-id="72737-159">显示名称为可选项。</span><span class="sxs-lookup"><span data-stu-id="72737-159">The display name is optional.</span></span> <span data-ttu-id="72737-160">这是由此帐户发送的邮件上显示的名称。</span><span class="sxs-lookup"><span data-stu-id="72737-160">This is the name displayed on messages sent from this account.</span></span> <span data-ttu-id="72737-161">例如， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的帐户可能会在电子邮件上显示名称“SQL Server 代理自动发件人”。</span><span class="sxs-lookup"><span data-stu-id="72737-161">For example, an account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent may display the name "SQL Server Agent Automated Mailer" on e-mail messages.</span></span>  
  
 <span data-ttu-id="72737-162">**答复电子邮件**</span><span class="sxs-lookup"><span data-stu-id="72737-162">**Reply e-mail**</span></span>  
 <span data-ttu-id="72737-163">键入电子邮件地址，该地址是答复由此帐户发送的电子邮件所用到的地址。</span><span class="sxs-lookup"><span data-stu-id="72737-163">Type the e-mail address that will be used for replies to e-mail messages sent from this account.</span></span> <span data-ttu-id="72737-164">答复电子邮件为可选项。</span><span class="sxs-lookup"><span data-stu-id="72737-164">The reply e-mail is optional.</span></span> <span data-ttu-id="72737-165">例如，给 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的帐户的回信可能会发送给数据库管理员 danw@Adventure-Works.com。</span><span class="sxs-lookup"><span data-stu-id="72737-165">For example, replies to an account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent may go to the database administrator, danw@Adventure-Works.com.</span></span>  
  
 <span data-ttu-id="72737-166">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="72737-166">**Server name**</span></span>  
 <span data-ttu-id="72737-167">键入此帐户发送电子邮件所用的 SMTP 服务器的名称或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="72737-167">Type the name or IP address of the SMTP server the account uses to send e-mail.</span></span> <span data-ttu-id="72737-168">通常，这种格式类似于 `smtp.` *<your_company>* `.com` 。</span><span class="sxs-lookup"><span data-stu-id="72737-168">Typically this is in a format similar to `smtp.`*<your_company>*`.com`.</span></span> <span data-ttu-id="72737-169">如需相关帮助，请询问您的邮件管理员。</span><span class="sxs-lookup"><span data-stu-id="72737-169">For help with this, consult your mail administrator.</span></span>  
  
 <span data-ttu-id="72737-170">**端口号**</span><span class="sxs-lookup"><span data-stu-id="72737-170">**Port number**</span></span>  
 <span data-ttu-id="72737-171">键入此帐户的 SMTP 服务器的端口号。</span><span class="sxs-lookup"><span data-stu-id="72737-171">Type the port number of the SMTP server for this account.</span></span> <span data-ttu-id="72737-172">大多数 SMTP 服务器使用端口 25。</span><span class="sxs-lookup"><span data-stu-id="72737-172">Most SMTP servers use port 25.</span></span>  
  
 <span data-ttu-id="72737-173">**此服务器要求安全连接(SSL)**</span><span class="sxs-lookup"><span data-stu-id="72737-173">**This server requires a secure connection (SSL)**</span></span>  
 <span data-ttu-id="72737-174">使用安全套接字层加密通信。</span><span class="sxs-lookup"><span data-stu-id="72737-174">Encrypts communication using Secure Sockets Layer.</span></span>  
  
 <span data-ttu-id="72737-175">**使用数据库引擎服务凭据的 Windows 身份验证**</span><span class="sxs-lookup"><span data-stu-id="72737-175">**Windows Authentication using Database Engine service credentials**</span></span>  
 <span data-ttu-id="72737-176">使用为 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 服务配置的凭据生成指向 SMTP 服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="72737-176">Connection is made to the SMTP server using the credentials configured for the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] service.</span></span>  
  
 <span data-ttu-id="72737-177">**基本身份验证**</span><span class="sxs-lookup"><span data-stu-id="72737-177">**Basic Authentication**</span></span>  
 <span data-ttu-id="72737-178">指定 SMTP 服务器要求的用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="72737-178">Specify the user name and password required by the SMTP server.</span></span>  
  
 <span data-ttu-id="72737-179">**用户名**</span><span class="sxs-lookup"><span data-stu-id="72737-179">**User name**</span></span>  
 <span data-ttu-id="72737-180">键入数据库邮件登录 SMTP 服务器所用的用户名。</span><span class="sxs-lookup"><span data-stu-id="72737-180">Type the user name that Database Mail uses to log in to the SMTP server.</span></span> <span data-ttu-id="72737-181">如果 SMTP 服务器要求基本身份验证，则需要提供用户名。</span><span class="sxs-lookup"><span data-stu-id="72737-181">The user name is required if the SMTP server requires basic authentication.</span></span>  
  
 <span data-ttu-id="72737-182">**密码**</span><span class="sxs-lookup"><span data-stu-id="72737-182">**Password**</span></span>  
 <span data-ttu-id="72737-183">键入数据库邮件登录 SMTP 服务器所用的密码。</span><span class="sxs-lookup"><span data-stu-id="72737-183">Type the password that Database Mail uses to log in to the SMTP server.</span></span> <span data-ttu-id="72737-184">如果 SMTP 服务器要求基本身份验证，则需要提供密码。</span><span class="sxs-lookup"><span data-stu-id="72737-184">The password is required if the SMTP server requires basic authentication.</span></span>  
  
 <span data-ttu-id="72737-185">**确认密码**</span><span class="sxs-lookup"><span data-stu-id="72737-185">**Confirm password**</span></span>  
 <span data-ttu-id="72737-186">再次输入密码以进行确认。</span><span class="sxs-lookup"><span data-stu-id="72737-186">Type the password again to confirm the password.</span></span> <span data-ttu-id="72737-187">如果 SMTP 服务器要求基本身份验证，则需要提供密码。</span><span class="sxs-lookup"><span data-stu-id="72737-187">The password is required if the SMTP server requires basic authentication.</span></span>  
  
 <span data-ttu-id="72737-188">**匿名身份验证**</span><span class="sxs-lookup"><span data-stu-id="72737-188">**Anonymous authentication**</span></span>  
 <span data-ttu-id="72737-189">在没有登录凭据的情况下，将邮件发送至 SMTP 服务器。</span><span class="sxs-lookup"><span data-stu-id="72737-189">Mail is sent to the SMTP server without login credentials.</span></span> <span data-ttu-id="72737-190">在 SMTP 服务器不要求进行身份验证时可以使用此选项。</span><span class="sxs-lookup"><span data-stu-id="72737-190">Use this option when the SMTP server does not require authentication.</span></span>  
  
 
  
###  <a name="manage-existing-account-page"></a><a name="ExistingAccount"></a><span data-ttu-id="72737-191">"管理现有帐户" 页</span><span class="sxs-lookup"><span data-stu-id="72737-191">Manage Existing Account Page</span></span>  
 <span data-ttu-id="72737-192">使用此页可以管理现有数据库邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="72737-192">Use this page to manage an existing Database Mail account.</span></span>  
  
 <span data-ttu-id="72737-193">**帐户名称**</span><span class="sxs-lookup"><span data-stu-id="72737-193">**Account name**</span></span>  
 <span data-ttu-id="72737-194">选择要查看、更新或删除的帐户。</span><span class="sxs-lookup"><span data-stu-id="72737-194">Select the account to view, update or delete.</span></span>  
  
 <span data-ttu-id="72737-195">**删除**</span><span class="sxs-lookup"><span data-stu-id="72737-195">**Delete**</span></span>  
 <span data-ttu-id="72737-196">删除选定的帐户。</span><span class="sxs-lookup"><span data-stu-id="72737-196">Delete the selected account.</span></span> <span data-ttu-id="72737-197">必须从关联的配置文件中删除此帐户，或者删除此类配置文件，才能够删除所选帐户。</span><span class="sxs-lookup"><span data-stu-id="72737-197">You must remove this account from associated profiles, or delete such profiles, before you delete the selected account.</span></span>  
  
 <span data-ttu-id="72737-198">**说明**</span><span class="sxs-lookup"><span data-stu-id="72737-198">**Description**</span></span>  
 <span data-ttu-id="72737-199">查看或更新帐户的说明。</span><span class="sxs-lookup"><span data-stu-id="72737-199">View or update the description of the account.</span></span> <span data-ttu-id="72737-200">说明是可选的。</span><span class="sxs-lookup"><span data-stu-id="72737-200">The description is optional.</span></span>  
  
 <span data-ttu-id="72737-201">**电子邮件地址**</span><span class="sxs-lookup"><span data-stu-id="72737-201">**E-mail address**</span></span>  
 <span data-ttu-id="72737-202">查看或更新帐户电子邮件地址的名称。</span><span class="sxs-lookup"><span data-stu-id="72737-202">View or update the name of the e-mail address for the account.</span></span> <span data-ttu-id="72737-203">这是发送电子邮件的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="72737-203">This is the e-mail address that e-mail is sent from.</span></span> <span data-ttu-id="72737-204">例如，Microsoft SQL Server 代理的帐户可能会从该地址发送电子邮件 **SqlAgent@Adventure-Works.com** 。</span><span class="sxs-lookup"><span data-stu-id="72737-204">For example, an account for Microsoft SQL Server Agent may send e-mail from the address **SqlAgent@Adventure-Works.com**.</span></span>  
  
 <span data-ttu-id="72737-205">**显示名称**</span><span class="sxs-lookup"><span data-stu-id="72737-205">**Display name**</span></span>  
 <span data-ttu-id="72737-206">查看或更新由此帐户发送的电子邮件上显示的名称。</span><span class="sxs-lookup"><span data-stu-id="72737-206">View or update the name to show on e-mail messages sent from this account.</span></span> <span data-ttu-id="72737-207">显示名称为可选项。</span><span class="sxs-lookup"><span data-stu-id="72737-207">The display name is optional.</span></span> <span data-ttu-id="72737-208">这是由此帐户发送的邮件上显示的名称。</span><span class="sxs-lookup"><span data-stu-id="72737-208">This is the name displayed on messages sent from this account.</span></span> <span data-ttu-id="72737-209">例如，SQL Server 代理的帐户可能会在电子邮件上显示名称 **SQL Server Agent Automated Mailer** 。</span><span class="sxs-lookup"><span data-stu-id="72737-209">For example, an account for SQL Server Agent may display the name **SQL Server Agent Automated Mailer** on e-mail messages.</span></span>  
  
 <span data-ttu-id="72737-210">**答复电子邮件**</span><span class="sxs-lookup"><span data-stu-id="72737-210">**Reply e-mail**</span></span>  
 <span data-ttu-id="72737-211">查看或更新电子邮件地址，该地址是答复由此帐户发送的电子邮件所用到的地址。</span><span class="sxs-lookup"><span data-stu-id="72737-211">View or update the e-mail address that will be used for replies to e-mail messages sent from this account.</span></span> <span data-ttu-id="72737-212">答复电子邮件为可选项。</span><span class="sxs-lookup"><span data-stu-id="72737-212">The reply e-mail is optional.</span></span> <span data-ttu-id="72737-213">例如，对 SQL Server 代理帐户的答复可能会发送给数据库管理员 **danw@Adventure-Works.com** 。</span><span class="sxs-lookup"><span data-stu-id="72737-213">For example, replies to an account for SQL Server Agent may go to the database administrator, **danw@Adventure-Works.com**.</span></span>  
  
 <span data-ttu-id="72737-214">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="72737-214">**Server name**</span></span>  
 <span data-ttu-id="72737-215">查看或更新该帐户发送电子邮件所用的 SMTP 服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="72737-215">View or update the name of the SMTP server the account uses to send e-mail.</span></span> <span data-ttu-id="72737-216">通常此格式类似于 **smtp.<your_company>.com**。</span><span class="sxs-lookup"><span data-stu-id="72737-216">Typically this is in a format similar to **smtp.<your_company>.com**.</span></span> <span data-ttu-id="72737-217">如需相关帮助，请询问您的邮件管理员。</span><span class="sxs-lookup"><span data-stu-id="72737-217">For help with this, consult your mail administrator.</span></span>  
  
 <span data-ttu-id="72737-218">**端口号**</span><span class="sxs-lookup"><span data-stu-id="72737-218">**Port number**</span></span>  
 <span data-ttu-id="72737-219">查看或更新此帐户的 SMTP 服务器的端口号。</span><span class="sxs-lookup"><span data-stu-id="72737-219">View or update the port number of the SMTP server for this account.</span></span> <span data-ttu-id="72737-220">大多数 SMTP 服务器使用端口 25。</span><span class="sxs-lookup"><span data-stu-id="72737-220">Most SMTP servers use port 25.</span></span>  
  
 <span data-ttu-id="72737-221">**此服务器要求安全连接(SSL)**</span><span class="sxs-lookup"><span data-stu-id="72737-221">**This server requires a secure connection (SSL)**</span></span>  
 <span data-ttu-id="72737-222">使用安全套接字层加密通信。</span><span class="sxs-lookup"><span data-stu-id="72737-222">Encrypts communication using Secure Sockets Layer.</span></span>  
  
 <span data-ttu-id="72737-223">**使用数据库引擎服务凭据的 Windows 身份验证**</span><span class="sxs-lookup"><span data-stu-id="72737-223">**Windows Authentication using Database Engine service credentials**</span></span>  
 <span data-ttu-id="72737-224">使用为 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 服务配置的凭据生成指向 SMTP 服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="72737-224">Connection is made to the SMTP server using the credentials configured for the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] service.</span></span>  
  
 <span data-ttu-id="72737-225">**基本身份验证**</span><span class="sxs-lookup"><span data-stu-id="72737-225">**Basic Authentication**</span></span>  
 <span data-ttu-id="72737-226">指定 SMTP 服务器要求的用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="72737-226">Specify the user name and password required by the SMTP server.</span></span>  
  
 <span data-ttu-id="72737-227">**用户名**</span><span class="sxs-lookup"><span data-stu-id="72737-227">**User name**</span></span>  
 <span data-ttu-id="72737-228">查看或更新数据库邮件登录 SMTP 服务器所用的用户名。</span><span class="sxs-lookup"><span data-stu-id="72737-228">View or update the user name that Database Mail uses to log in to the SMTP server.</span></span> <span data-ttu-id="72737-229">如果 SMTP 服务器要求基本身份验证，则需要提供用户名。</span><span class="sxs-lookup"><span data-stu-id="72737-229">The user name is required if the SMTP server requires basic authentication.</span></span>  
  
 <span data-ttu-id="72737-230">**密码**</span><span class="sxs-lookup"><span data-stu-id="72737-230">**Password**</span></span>  
 <span data-ttu-id="72737-231">更改数据库邮件登录 SMTP 服务器所用的密码。</span><span class="sxs-lookup"><span data-stu-id="72737-231">Change the password that Database Mail uses to log in to the SMTP server.</span></span> <span data-ttu-id="72737-232">如果 SMTP 服务器要求基本身份验证，则需要提供密码。</span><span class="sxs-lookup"><span data-stu-id="72737-232">The password is required if the SMTP server requires basic authentication.</span></span>  
  
 <span data-ttu-id="72737-233">**确认密码**</span><span class="sxs-lookup"><span data-stu-id="72737-233">**Confirm password**</span></span>  
 <span data-ttu-id="72737-234">再次输入密码以进行确认。</span><span class="sxs-lookup"><span data-stu-id="72737-234">Type the password again to confirm the password.</span></span> <span data-ttu-id="72737-235">如果 SMTP 服务器要求基本身份验证，则需要提供密码。</span><span class="sxs-lookup"><span data-stu-id="72737-235">The password is required if the SMTP server requires basic authentication.</span></span>  
  
 <span data-ttu-id="72737-236">**匿名身份验证**</span><span class="sxs-lookup"><span data-stu-id="72737-236">**Anonymous authentication**</span></span>  
 <span data-ttu-id="72737-237">在没有登录凭据的情况下，将邮件发送至 SMTP 服务器。</span><span class="sxs-lookup"><span data-stu-id="72737-237">Mail is sent to the SMTP server without login credentials.</span></span> <span data-ttu-id="72737-238">在 SMTP 服务器不要求进行身份验证时可以使用此选项。</span><span class="sxs-lookup"><span data-stu-id="72737-238">Use this option when the SMTP server does not require authentication.</span></span>  
  

  
###  <a name="new-profile-page"></a><a name="NewProfile"></a><span data-ttu-id="72737-239">新建配置文件页</span><span class="sxs-lookup"><span data-stu-id="72737-239">New Profile Page</span></span>  
 <span data-ttu-id="72737-240">使用此页可以创建数据库邮件配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-240">Use this page to create a Database Mail profile.</span></span> <span data-ttu-id="72737-241">数据库邮件配置文件是数据库邮件帐户的集合。</span><span class="sxs-lookup"><span data-stu-id="72737-241">A Database Mail profile is a collection of Database Mail accounts.</span></span> <span data-ttu-id="72737-242">在无法访问电子邮件服务器时，配置文件通过提供其他的数据库邮件帐户来提高可靠性。</span><span class="sxs-lookup"><span data-stu-id="72737-242">Profiles improve reliability in cases where an e-mail server becomes unreachable, by providing alternative Database Mail accounts.</span></span> <span data-ttu-id="72737-243">至少需要一个数据库邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="72737-243">At least one Database Mail account is required.</span></span> <span data-ttu-id="72737-244">有关在配置文件中设置数据库邮件帐户的优先级的详细信息，请参阅 [Create a Database Mail Profile](create-a-database-mail-profile.md)。</span><span class="sxs-lookup"><span data-stu-id="72737-244">For more information about setting the priority of Database Mail accounts in the profile, see [Create a Database Mail Profile](create-a-database-mail-profile.md).</span></span>  
  
 <span data-ttu-id="72737-245">使用 **“上移”** 和 **“下移”** 按钮可以更改数据库邮件帐户的使用顺序。</span><span class="sxs-lookup"><span data-stu-id="72737-245">Use the **Move Up** and **Move Down** buttons to change the order in which Database Mail accounts are used.</span></span> <span data-ttu-id="72737-246">此顺序由一个名为序列号的值来确定。</span><span class="sxs-lookup"><span data-stu-id="72737-246">This order is determined by a value called the sequence number.</span></span> <span data-ttu-id="72737-247">**“上移”** 减小序列号， **“下移”** 增大序列号。</span><span class="sxs-lookup"><span data-stu-id="72737-247">**Move Up** lowers the sequence number and **Move Down** increases the sequence number.</span></span> <span data-ttu-id="72737-248">序列号可以确定数据库邮件使用配置文件中帐户的顺序。</span><span class="sxs-lookup"><span data-stu-id="72737-248">The sequence number determines the order in which Database Mail uses accounts in the profile.</span></span> <span data-ttu-id="72737-249">对于新的电子邮件，数据库邮件将从序列号最小的帐户开始。</span><span class="sxs-lookup"><span data-stu-id="72737-249">For a new e-mail message, Database Mail starts with the account that has the lowest sequence number.</span></span> <span data-ttu-id="72737-250">如果该帐户失败，数据库邮件就使用具有下一个序列号较大的帐户，依此类推，直到数据库邮件成功发送邮件，或者序列号最大的帐户也失败为止。</span><span class="sxs-lookup"><span data-stu-id="72737-250">Should that account fail, Database Mail uses the account with the next highest sequence number, and so on until either Database Mail sends the message successfully, or the account with the highest sequence number fails.</span></span> <span data-ttu-id="72737-251">如果具有最高序列号的帐户失败，则数据库邮件将在一段时间内（该时间在数据库邮件的 **AccountRetryDelay** 参数中配置）暂停发送邮件，之后从最低序列号开始重新尝试发送邮件。</span><span class="sxs-lookup"><span data-stu-id="72737-251">If the account with the highest sequence number fails, the Database Mail pauses attempts to send the mail for the amount of time configured in the Database Mail **AccountRetryDelay** parameter, then starts the process of attempting to send the mail again, starting with the lowest sequence number.</span></span> <span data-ttu-id="72737-252">使用数据库邮件的 **AccountRetryAttempts** 参数，可以配置外部邮件进程使用指定配置文件中的每个帐户尝试发送电子邮件的次数。</span><span class="sxs-lookup"><span data-stu-id="72737-252">Use the Database Mail **AccountRetryAttempts** parameter, to configure the number of times that the external mail process attempts to send the e-mail message using each account in the specified profile.</span></span> <span data-ttu-id="72737-253">可以在数据库邮件配置向导的 **“配置系统参数”** 页上配置 **AccountRetryDelay** 和 **AccountRetryAttempts** 参数。</span><span class="sxs-lookup"><span data-stu-id="72737-253">You can configure the **AccountRetryDelay** and **AccountRetryAttempts** parameters on the **Configure System Parameters** page of the Database Mail Configuration Wizard.</span></span>  
  
 <span data-ttu-id="72737-254">**配置文件名称**</span><span class="sxs-lookup"><span data-stu-id="72737-254">**Profile name**</span></span>  
 <span data-ttu-id="72737-255">键入新配置文件的名称。</span><span class="sxs-lookup"><span data-stu-id="72737-255">Type the name for the new profile.</span></span> <span data-ttu-id="72737-256">将使用此名称创建配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-256">The profile is created with this name.</span></span> <span data-ttu-id="72737-257">不要使用现有配置文件的名称。</span><span class="sxs-lookup"><span data-stu-id="72737-257">Do not use the name of an existing profile.</span></span>  
  
 <span data-ttu-id="72737-258">**说明**</span><span class="sxs-lookup"><span data-stu-id="72737-258">**Description**</span></span>  
 <span data-ttu-id="72737-259">键入配置文件的说明。</span><span class="sxs-lookup"><span data-stu-id="72737-259">Type a description for the profile.</span></span> <span data-ttu-id="72737-260">说明是可选的。</span><span class="sxs-lookup"><span data-stu-id="72737-260">The description is optional.</span></span>  
  
 <span data-ttu-id="72737-261">**SMTP 帐户**</span><span class="sxs-lookup"><span data-stu-id="72737-261">**SMTP accounts**</span></span>  
 <span data-ttu-id="72737-262">为配置文件选择一个或多个帐户。</span><span class="sxs-lookup"><span data-stu-id="72737-262">Choose one or more accounts for the profile.</span></span> <span data-ttu-id="72737-263">优先级设置数据库邮件使用帐户的顺序。</span><span class="sxs-lookup"><span data-stu-id="72737-263">The priority sets the order in which Database Mail uses the accounts.</span></span> <span data-ttu-id="72737-264">如果没有列出任何帐户，必须单击 **“添加”** 继续，并添加新的 SMTP 帐户。</span><span class="sxs-lookup"><span data-stu-id="72737-264">If no accounts are listed, you must click **Add** to continue, and add a new SMTP account.</span></span>  
  
 <span data-ttu-id="72737-265">**添加**</span><span class="sxs-lookup"><span data-stu-id="72737-265">**Add**</span></span>  
 <span data-ttu-id="72737-266">向配置文件中添加帐户。</span><span class="sxs-lookup"><span data-stu-id="72737-266">Add an account to the profile.</span></span>  
  
 <span data-ttu-id="72737-267">**移除**</span><span class="sxs-lookup"><span data-stu-id="72737-267">**Remove**</span></span>  
 <span data-ttu-id="72737-268">从配置文件中删除所选帐户。</span><span class="sxs-lookup"><span data-stu-id="72737-268">Remove the selected account from the profile.</span></span>  
  
 <span data-ttu-id="72737-269">**上移**</span><span class="sxs-lookup"><span data-stu-id="72737-269">**Move Up**</span></span>  
 <span data-ttu-id="72737-270">提高选定帐户的优先级。</span><span class="sxs-lookup"><span data-stu-id="72737-270">Increase the priority of the selected account.</span></span>  
  
 <span data-ttu-id="72737-271">**“下移”**</span><span class="sxs-lookup"><span data-stu-id="72737-271">**Move Down**</span></span>  
 <span data-ttu-id="72737-272">降低选定帐户的优先级。</span><span class="sxs-lookup"><span data-stu-id="72737-272">Decrease the priority of the selected account.</span></span>  
  

  
###  <a name="manage-existing-profile-page"></a><a name="ExistingProfile"></a><span data-ttu-id="72737-273">"管理现有配置文件" 页</span><span class="sxs-lookup"><span data-stu-id="72737-273">Manage Existing Profile Page</span></span>  
 <span data-ttu-id="72737-274">使用此页可以管理现有的数据库邮件配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-274">Use this page to manage an existing Database Mail profile.</span></span> <span data-ttu-id="72737-275">数据库邮件配置文件是数据库邮件帐户的集合。</span><span class="sxs-lookup"><span data-stu-id="72737-275">A Database Mail profile is a collection of Database Mail accounts.</span></span> <span data-ttu-id="72737-276">在无法访问电子邮件服务器时，配置文件通过提供其他的数据库邮件帐户来提高可靠性。</span><span class="sxs-lookup"><span data-stu-id="72737-276">Profiles improve reliability in cases where an e-mail server becomes unreachable, by providing alternative Database Mail accounts.</span></span> <span data-ttu-id="72737-277">至少需要一个数据库邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="72737-277">At least one Database Mail account is required.</span></span> <span data-ttu-id="72737-278">有关在配置文件中设置数据库邮件帐户的优先级的详细信息，请参阅 [Create a Database Mail Profile](create-a-database-mail-profile.md)。</span><span class="sxs-lookup"><span data-stu-id="72737-278">For more information about setting the priority of Database Mail accounts in the profile, see [Create a Database Mail Profile](create-a-database-mail-profile.md).</span></span>  
  
 <span data-ttu-id="72737-279">使用 **“上移”** 和 **“下移”** 按钮可以更改数据库邮件帐户的使用顺序。</span><span class="sxs-lookup"><span data-stu-id="72737-279">Use the **Move Up** and **Move Down** buttons to change the order in which Database Mail accounts are used.</span></span> <span data-ttu-id="72737-280">此顺序由一个名为序列号的值来确定。</span><span class="sxs-lookup"><span data-stu-id="72737-280">This order is determined by a value called the sequence number.</span></span> <span data-ttu-id="72737-281">**“上移”** 减小序列号， **“下移”** 增大序列号。</span><span class="sxs-lookup"><span data-stu-id="72737-281">**Move Up** lowers the sequence number and **Move Down** increases the sequence number.</span></span> <span data-ttu-id="72737-282">序列号可以确定数据库邮件使用配置文件中帐户的顺序。</span><span class="sxs-lookup"><span data-stu-id="72737-282">The sequence number determines the order in which Database Mail uses accounts in the profile.</span></span> <span data-ttu-id="72737-283">对于新的电子邮件，数据库邮件将从序列号最小的帐户开始。</span><span class="sxs-lookup"><span data-stu-id="72737-283">For a new e-mail message, Database Mail starts with the account that has the lowest sequence number.</span></span> <span data-ttu-id="72737-284">如果该帐户失败，数据库邮件就使用具有下一个序列号较大的帐户，依此类推，直到数据库邮件成功发送邮件，或者序列号最大的帐户也失败为止。</span><span class="sxs-lookup"><span data-stu-id="72737-284">Should that account fail, Database Mail uses the account with the next highest sequence number, and so on until either Database Mail sends the message successfully, or the account with the highest sequence number fails.</span></span> <span data-ttu-id="72737-285">如果具有最高序列号的帐户失败，则数据库邮件将在一段时间内（该时间在数据库邮件的 **AccountRetryDelay** 参数中配置）暂停发送邮件，之后从最低序列号开始重新尝试发送邮件。</span><span class="sxs-lookup"><span data-stu-id="72737-285">If the account with the highest sequence number fails, the Database Mail pauses attempts to send the mail for the amount of time configured in the Database Mail **AccountRetryDelay** parameter, then starts the process of attempting to send the mail again, starting with the lowest sequence number.</span></span> <span data-ttu-id="72737-286">使用数据库邮件的 **AccountRetryAttempts** 参数，可以配置外部邮件进程使用指定配置文件中的每个帐户尝试发送电子邮件的次数。</span><span class="sxs-lookup"><span data-stu-id="72737-286">Use the Database Mail **AccountRetryAttempts** parameter, to configure the number of times that the external mail process attempts to send the e-mail message using each account in the specified profile.</span></span> <span data-ttu-id="72737-287">可以在数据库邮件配置向导的 **“配置系统参数”** 页上配置 **AccountRetryDelay** 和 **AccountRetryAttempts** 参数。</span><span class="sxs-lookup"><span data-stu-id="72737-287">You can configure the **AccountRetryDelay** and **AccountRetryAttempts** parameters on the **Configure System Parameters** page of the Database Mail Configuration Wizard.</span></span>  
  
 <span data-ttu-id="72737-288">**配置文件名称**</span><span class="sxs-lookup"><span data-stu-id="72737-288">**Profile name**</span></span>  
 <span data-ttu-id="72737-289">选择要管理的配置文件的名称。</span><span class="sxs-lookup"><span data-stu-id="72737-289">Select the name of the profile to manage.</span></span>  
  
 <span data-ttu-id="72737-290">**删除**</span><span class="sxs-lookup"><span data-stu-id="72737-290">**Delete**</span></span>  
 <span data-ttu-id="72737-291">删除所选配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-291">Delete the selected profile.</span></span> <span data-ttu-id="72737-292">系统将提示您选择 **“是”** 以删除所选配置文件并舍弃任何未发送的邮件，或者选择 **“否”** 以仅在没有未发送邮件时删除所选配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-292">You will be prompted to select **Yes** to delete the selected profile and to fail any unsent messages, or to select **No** to delete the selected profile only if there are no unsent messages.</span></span>  
  
 <span data-ttu-id="72737-293">**说明**</span><span class="sxs-lookup"><span data-stu-id="72737-293">**Description**</span></span>  
 <span data-ttu-id="72737-294">查看或更改所选配置文件的说明。</span><span class="sxs-lookup"><span data-stu-id="72737-294">View or change the description of the selected profile.</span></span> <span data-ttu-id="72737-295">说明是可选的。</span><span class="sxs-lookup"><span data-stu-id="72737-295">The description is optional.</span></span>  
  
 <span data-ttu-id="72737-296">**SMTP 帐户**</span><span class="sxs-lookup"><span data-stu-id="72737-296">**SMTP accounts**</span></span>  
 <span data-ttu-id="72737-297">为配置文件选择一个或多个帐户。</span><span class="sxs-lookup"><span data-stu-id="72737-297">Choose one or more accounts for the profile.</span></span> <span data-ttu-id="72737-298">故障转移优先级设置了在进行故障转移时数据库邮件使用帐户的顺序。</span><span class="sxs-lookup"><span data-stu-id="72737-298">The failover priority sets the order in which Database Mail uses the account in case of a failover.</span></span>  
  
 <span data-ttu-id="72737-299">**添加**</span><span class="sxs-lookup"><span data-stu-id="72737-299">**Add**</span></span>  
 <span data-ttu-id="72737-300">向配置文件中添加帐户。</span><span class="sxs-lookup"><span data-stu-id="72737-300">Add an account to the profile.</span></span>  
  
 <span data-ttu-id="72737-301">**移除**</span><span class="sxs-lookup"><span data-stu-id="72737-301">**Remove**</span></span>  
 <span data-ttu-id="72737-302">从配置文件中删除所选帐户。</span><span class="sxs-lookup"><span data-stu-id="72737-302">Remove the selected account from the profile.</span></span>  
  
 <span data-ttu-id="72737-303">**上移**</span><span class="sxs-lookup"><span data-stu-id="72737-303">**Move Up**</span></span>  
 <span data-ttu-id="72737-304">提高所选帐户的故障转移优先级。</span><span class="sxs-lookup"><span data-stu-id="72737-304">Increase the failover priority of the selected account.</span></span>  
  
 <span data-ttu-id="72737-305">**“下移”**</span><span class="sxs-lookup"><span data-stu-id="72737-305">**Move Down**</span></span>  
 <span data-ttu-id="72737-306">降低所选帐户的故障转移优先级。</span><span class="sxs-lookup"><span data-stu-id="72737-306">Decrease the failover priority of the selected account.</span></span>  
  
 <span data-ttu-id="72737-307">**Priority**</span><span class="sxs-lookup"><span data-stu-id="72737-307">**Priority**</span></span>  
 <span data-ttu-id="72737-308">查看帐户的当前故障转移优先级。</span><span class="sxs-lookup"><span data-stu-id="72737-308">View the current failover priority of the account.</span></span>  
  
 <span data-ttu-id="72737-309">**帐户名称**</span><span class="sxs-lookup"><span data-stu-id="72737-309">**Account name**</span></span>  
 <span data-ttu-id="72737-310">查看帐户的名称。</span><span class="sxs-lookup"><span data-stu-id="72737-310">View the name of the account.</span></span>  
  
 <span data-ttu-id="72737-311">**电子邮件地址**</span><span class="sxs-lookup"><span data-stu-id="72737-311">**E-mail Address**</span></span>  
 <span data-ttu-id="72737-312">查看帐户的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="72737-312">View the e-mail address of the account.</span></span>  
  

  
###  <a name="add-account-to-profile-page"></a><a name="AddAccount"></a><span data-ttu-id="72737-313">"将帐户添加到配置文件" 页</span><span class="sxs-lookup"><span data-stu-id="72737-313">Add Account to Profile Page</span></span>  
 <span data-ttu-id="72737-314">使用此页可选择要添加到配置文件的帐户。</span><span class="sxs-lookup"><span data-stu-id="72737-314">Use this page to choose the account to add to the profile.</span></span> <span data-ttu-id="72737-315">请从 **“帐户名”** 框中选择现有帐户，或单击 **“新建帐户”**。</span><span class="sxs-lookup"><span data-stu-id="72737-315">Either choose an existing account from the **Account name** box, or click **New Account**.</span></span>  
  
 <span data-ttu-id="72737-316">**帐户名称**</span><span class="sxs-lookup"><span data-stu-id="72737-316">**Account name**</span></span>  
 <span data-ttu-id="72737-317">选择要添加到配置文件的帐户的名称。</span><span class="sxs-lookup"><span data-stu-id="72737-317">Select the name of the account to add to the profile.</span></span>  
  
 <span data-ttu-id="72737-318">**电子邮件地址**</span><span class="sxs-lookup"><span data-stu-id="72737-318">**E-mail address**</span></span>  
 <span data-ttu-id="72737-319">查看所选帐户的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="72737-319">View the e-mail address for the selected account.</span></span> <span data-ttu-id="72737-320">您不能在此页中更改电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="72737-320">You cannot change the e-mail address from this page.</span></span> <span data-ttu-id="72737-321">若要更改该帐户的电子邮件地址，请返回到该向导的主页，再选择“管理数据库邮件帐户和配置文件”\*\*\*\* 选项。</span><span class="sxs-lookup"><span data-stu-id="72737-321">To change the e-mail address for the account, go back to the main page of the wizard and select the **Manage Database Mail accounts and profiles** option.</span></span>  
  
 <span data-ttu-id="72737-322">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="72737-322">**Server name**</span></span>  
 <span data-ttu-id="72737-323">查看所选帐户的邮件服务器名称。</span><span class="sxs-lookup"><span data-stu-id="72737-323">View the mail server name for the selected account.</span></span> <span data-ttu-id="72737-324">您不能在此页中更改服务器名称。</span><span class="sxs-lookup"><span data-stu-id="72737-324">You cannot change the server name from this page.</span></span> <span data-ttu-id="72737-325">若要更改该帐户的服务器名称，请返回到该向导的主页，再选择 **“管理数据库邮件帐户和配置文件”** 选项。</span><span class="sxs-lookup"><span data-stu-id="72737-325">To change the server name for the account, go back to the main page of the wizard and select the **Manage Database Mail accounts and profiles** option.</span></span>  
  
 <span data-ttu-id="72737-326">**“新建帐户”**</span><span class="sxs-lookup"><span data-stu-id="72737-326">**New Account**</span></span>  
 <span data-ttu-id="72737-327">创建新帐户。</span><span class="sxs-lookup"><span data-stu-id="72737-327">Create a new account.</span></span>  
  

  
###  <a name="manage-accounts-and-profiles-page"></a><a name="AccountsProfiles"></a><span data-ttu-id="72737-328">"管理帐户和配置文件" 页</span><span class="sxs-lookup"><span data-stu-id="72737-328">Manage Accounts and Profiles Page</span></span>  
 <span data-ttu-id="72737-329">使用此页可选择用于管理配置文件或帐户的任务。</span><span class="sxs-lookup"><span data-stu-id="72737-329">Use this page to choose a task for managing a profile or account.</span></span>  
  
 <span data-ttu-id="72737-330">**创建新帐户**</span><span class="sxs-lookup"><span data-stu-id="72737-330">**Create a new account**</span></span>  
 <span data-ttu-id="72737-331">创建新帐户。</span><span class="sxs-lookup"><span data-stu-id="72737-331">Create a new account.</span></span>  
  
 <span data-ttu-id="72737-332">**查看、更改或删除现有帐户**</span><span class="sxs-lookup"><span data-stu-id="72737-332">**View, change or delete an existing account**</span></span>  
 <span data-ttu-id="72737-333">管理或删除现有帐户。</span><span class="sxs-lookup"><span data-stu-id="72737-333">Manage or delete an existing account.</span></span>  
  
 <span data-ttu-id="72737-334">**创建新的配置文件**</span><span class="sxs-lookup"><span data-stu-id="72737-334">**Create a new profile**</span></span>  
 <span data-ttu-id="72737-335">创建新的配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-335">Create a new profile.</span></span>  
  
 <span data-ttu-id="72737-336">**查看、更改或删除现有配置文件。你还可以管理与该配置文件关联的帐户。**</span><span class="sxs-lookup"><span data-stu-id="72737-336">**View, change or delete an existing profile. You can also manage accounts associated with the profile.**</span></span>  
 <span data-ttu-id="72737-337">更新或删除现有配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-337">Update or delete an existing profile.</span></span> <span data-ttu-id="72737-338">使用此选项，您还可以管理与该配置文件关联的帐户。</span><span class="sxs-lookup"><span data-stu-id="72737-338">This option also allows you to manage accounts associated with the profile.</span></span>  
  

  
###  <a name="manage-profile-security-public-tab"></a><a name="ProfileSecurityPublic"></a><span data-ttu-id="72737-339">管理配置文件安全性，公共选项卡</span><span class="sxs-lookup"><span data-stu-id="72737-339">Manage Profile Security, Public Tab</span></span>  
 <span data-ttu-id="72737-340">使用此页可配置公共配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-340">Use this page to configure a public profile.</span></span>  
  
 <span data-ttu-id="72737-341">配置文件可以为公共配置文件或专用配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-341">Profiles are either public or private.</span></span> <span data-ttu-id="72737-342">只有特定用户或角色才能访问专用配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-342">A private profile is accessible only to specific users or roles.</span></span> <span data-ttu-id="72737-343">公共配置文件允许所有用户或角色访问邮件主机数据库 (**msdb**)，以使用该配置文件发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="72737-343">A public profile allows any user or role with access to the mail host database (**msdb**) to send e-mail using that profile.</span></span>  
  
 <span data-ttu-id="72737-344">配置文件可以是默认的配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-344">A profile may be a default profile.</span></span> <span data-ttu-id="72737-345">在这种情况下，用户或角色可以使用该配置文件发送电子邮件，而无需显式指定配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-345">In this case, users or roles can send e-mail using the profile without explicitly specifying the profile.</span></span> <span data-ttu-id="72737-346">如果发送电子邮件的用户或角色具有默认的专用配置文件，则数据库邮件将使用该配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-346">If the user or role sending the e-mail message has a default private profile, Database Mail uses that profile.</span></span> <span data-ttu-id="72737-347">如果用户或角色没有默认的专用配置文件，则 **sp_send_dbmail** 将使用 **msdb** 数据库的默认公共配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-347">If the user or role has no default private profile, **sp_send_dbmail** uses the default public profile for the **msdb** database.</span></span> <span data-ttu-id="72737-348">如果用户或角色没有默认的专用配置文件，且该数据库也没有默认的公共配置文件，则 **sp_send_dbmail** 将返回错误。</span><span class="sxs-lookup"><span data-stu-id="72737-348">If there is no default private profile for the user or role and no default public profile for the database, **sp_send_dbmail** returns an error.</span></span> <span data-ttu-id="72737-349">仅可以将一个配置文件标记为默认配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-349">Only one profile can be marked as the default profile.</span></span>  
  
 <span data-ttu-id="72737-350">**公共**</span><span class="sxs-lookup"><span data-stu-id="72737-350">**Public**</span></span>  
 <span data-ttu-id="72737-351">选择此选项可将指定的配置文件转为公共配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-351">Select this option to make the specified profile public.</span></span>  
  
 <span data-ttu-id="72737-352">**配置文件名**</span><span class="sxs-lookup"><span data-stu-id="72737-352">**Profile Name**</span></span>  
 <span data-ttu-id="72737-353">显示配置文件的名称。</span><span class="sxs-lookup"><span data-stu-id="72737-353">Displays the name of the profile.</span></span>  
  
 <span data-ttu-id="72737-354">**默认配置文件**</span><span class="sxs-lookup"><span data-stu-id="72737-354">**Default Profile**</span></span>  
 <span data-ttu-id="72737-355">选择此选项可将指定的配置文件转为默认配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-355">Select this option to make the specified profile the default profile.</span></span>  
  
 <span data-ttu-id="72737-356">**仅显示现有的公共配置文件**</span><span class="sxs-lookup"><span data-stu-id="72737-356">**Show only existing public profiles**</span></span>  
 <span data-ttu-id="72737-357">选择此选项将仅显示指定数据库中的公共配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-357">Select this option to show only public profiles in the specified database.</span></span>  
  

  
###  <a name="manage-profile-security-private-tab"></a><a name="ProfileSecurityPrivate"></a><span data-ttu-id="72737-358">管理配置文件安全性，专用选项卡</span><span class="sxs-lookup"><span data-stu-id="72737-358">Manage Profile Security, Private Tab</span></span>  
 <span data-ttu-id="72737-359">使用此页可配置专用配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-359">Use this page to configure a private profile.</span></span>  
  
 <span data-ttu-id="72737-360">配置文件可以为公共配置文件或专用配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-360">Profiles are either public or private.</span></span> <span data-ttu-id="72737-361">只有特定用户或角色才能访问专用配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-361">A private profile is accessible only to specific users or roles.</span></span> <span data-ttu-id="72737-362">公共配置文件允许所有用户或角色访问邮件主机数据库 (**msdb**)，以使用该配置文件发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="72737-362">A public profile allows any user or role with access to the mail host database (**msdb**) to send e-mail using that profile.</span></span>  
  
 <span data-ttu-id="72737-363">配置文件可以是默认的配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-363">A profile may be a default profile.</span></span> <span data-ttu-id="72737-364">在这种情况下，用户或角色可以使用该配置文件发送电子邮件，而无需显式指定配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-364">In this case, users or roles can send e-mail using the profile without explicitly specifying the profile.</span></span> <span data-ttu-id="72737-365">如果发送电子邮件的用户或角色具有默认的专用配置文件，则数据库邮件将使用该配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-365">If the user or role sending the e-mail message has a default private profile, Database Mail uses that profile.</span></span> <span data-ttu-id="72737-366">如果用户或角色没有默认的专用配置文件，则 **sp_send_dbmail** 将使用 **msdb** 数据库的默认公共配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-366">If the user or role has no default private profile, **sp_send_dbmail** uses the default public profile for the **msdb** database.</span></span> <span data-ttu-id="72737-367">如果用户或角色没有默认的专用配置文件，且该数据库也没有默认的公共配置文件，则 **sp_send_dbmail** 将返回错误。</span><span class="sxs-lookup"><span data-stu-id="72737-367">If there is no default private profile for the user or role and no default public profile for the database, **sp_send_dbmail** returns an error.</span></span>  
  
 <span data-ttu-id="72737-368">**用户名**</span><span class="sxs-lookup"><span data-stu-id="72737-368">**User name**</span></span>  
 <span data-ttu-id="72737-369">在 **msdb** 数据库中选择用户或角色的名称。</span><span class="sxs-lookup"><span data-stu-id="72737-369">Select the name of a user or role in the **msdb** database.</span></span>  
  
 <span data-ttu-id="72737-370">**访问**</span><span class="sxs-lookup"><span data-stu-id="72737-370">**Access**</span></span>  
 <span data-ttu-id="72737-371">选择该用户或角色是否可以访问指定的配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-371">Select whether the user or role has access to the specified profile.</span></span>  
  
 <span data-ttu-id="72737-372">**配置文件名称**</span><span class="sxs-lookup"><span data-stu-id="72737-372">**Profile name**</span></span>  
 <span data-ttu-id="72737-373">查看配置文件的名称。</span><span class="sxs-lookup"><span data-stu-id="72737-373">View the name of the profile.</span></span>  
  
 <span data-ttu-id="72737-374">**是默认配置文件**</span><span class="sxs-lookup"><span data-stu-id="72737-374">**Is Default Profile**</span></span>  
 <span data-ttu-id="72737-375">选择该配置文件是否为该用户或角色的默认配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-375">Select whether the profile is the default profile for the user or role.</span></span> <span data-ttu-id="72737-376">每个用户或角色只能有一个默认配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-376">Each user or role may have only one default profile.</span></span>  
  
 <span data-ttu-id="72737-377">**仅显示此用户的现有专用配置文件**</span><span class="sxs-lookup"><span data-stu-id="72737-377">**Show only existing private profiles for this user**</span></span>  
 <span data-ttu-id="72737-378">选择此选项将仅显示指定的用户或角色可以访问的配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-378">Select this option to display only profiles that the specified user or role already has access to.</span></span>  
  

  
###  <a name="configure-system-parameters"></a><a name="SystemParameters"></a><span data-ttu-id="72737-379">配置系统参数</span><span class="sxs-lookup"><span data-stu-id="72737-379">Configure System Parameters</span></span>  
 <span data-ttu-id="72737-380">使用此页可以指定数据库邮件系统参数。</span><span class="sxs-lookup"><span data-stu-id="72737-380">Use this page to specify Database Mail system parameters.</span></span> <span data-ttu-id="72737-381">查看系统参数和每个参数的当前值。</span><span class="sxs-lookup"><span data-stu-id="72737-381">View the system parameters and the current value of each parameter.</span></span> <span data-ttu-id="72737-382">选择某个参数可以在信息窗格中查看其简短说明。</span><span class="sxs-lookup"><span data-stu-id="72737-382">Select a parameter to view a short description in the information pane.</span></span>  
  
 <span data-ttu-id="72737-383">**帐户重试次数**</span><span class="sxs-lookup"><span data-stu-id="72737-383">**Account Retry Attempts**</span></span>  
 <span data-ttu-id="72737-384">外部电子邮件进程尝试使用指定配置文件中的每个帐户发送电子邮件的次数。</span><span class="sxs-lookup"><span data-stu-id="72737-384">The number of times that the external mail process attempts to send the e-mail message using each account in the specified profile.</span></span>  
  
 <span data-ttu-id="72737-385">**帐户重试延迟时间(秒)**</span><span class="sxs-lookup"><span data-stu-id="72737-385">**Account Retry Delay (seconds)**</span></span>  
 <span data-ttu-id="72737-386">在尝试使用配置文件中的所有帐户传递消息后，外部邮件进程在再次尝试使用所有帐户之前等待的时间（秒）。</span><span class="sxs-lookup"><span data-stu-id="72737-386">The amount of time, in seconds, for the external mail process to wait after it tries to deliver a message using all accounts in the profile before it attempts all accounts again.</span></span>  
  
 <span data-ttu-id="72737-387">**最大文件大小(字节)**</span><span class="sxs-lookup"><span data-stu-id="72737-387">**Maximum File Size (Bytes)**</span></span>  
 <span data-ttu-id="72737-388">附件的最大大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="72737-388">The maximum size of an attachment, in bytes.</span></span>  
  
 <span data-ttu-id="72737-389">**禁止的附件文件扩展名**</span><span class="sxs-lookup"><span data-stu-id="72737-389">**Prohibited Attachment File Extensions**</span></span>  
 <span data-ttu-id="72737-390">一组以逗号分隔的扩展名，具有这些扩展名的文件不能作为电子邮件附件发送。</span><span class="sxs-lookup"><span data-stu-id="72737-390">A comma-separated list of extensions which cannot be sent as an attachment to an e-mail message.</span></span> <span data-ttu-id="72737-391">单击浏览按钮 (**...**) 以添加其他扩展名。</span><span class="sxs-lookup"><span data-stu-id="72737-391">Click the browse button (**...**) to add additional extensions.</span></span>  
  
 <span data-ttu-id="72737-392">**数据库邮件可执行文件的最短生存期(秒)**</span><span class="sxs-lookup"><span data-stu-id="72737-392">**Database Mail Executable Minimum Lifetime (seconds)**</span></span>  
 <span data-ttu-id="72737-393">外部邮件进程保持活动状态的最少时间（以秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="72737-393">The minimum amount of time, in seconds, that the external mail process remains active.</span></span> <span data-ttu-id="72737-394">只要数据库邮件队列中有电子邮件，该进程就会保持活动状态。</span><span class="sxs-lookup"><span data-stu-id="72737-394">The process remains active as long as there are e-mails in the Database Mail queue.</span></span> <span data-ttu-id="72737-395">此参数指定了在没有要处理的消息时该进程保持活动状态的时间。</span><span class="sxs-lookup"><span data-stu-id="72737-395">This parameter specifies the time the process remains active if there are no messages to process.</span></span>  
  
 <span data-ttu-id="72737-396">**日志记录级别**</span><span class="sxs-lookup"><span data-stu-id="72737-396">**Logging level**</span></span>  
 <span data-ttu-id="72737-397">指定数据库邮件日志中要记录的消息。</span><span class="sxs-lookup"><span data-stu-id="72737-397">Specify which messages are recorded in the Database Mail log.</span></span> <span data-ttu-id="72737-398">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="72737-398">Possible values are:</span></span>  
  
-   <span data-ttu-id="72737-399">普通 - 仅记录错误</span><span class="sxs-lookup"><span data-stu-id="72737-399">Normal - logs only errors</span></span>  
  
-   <span data-ttu-id="72737-400">扩展 - 记录错误、警告和信息性消息</span><span class="sxs-lookup"><span data-stu-id="72737-400">Extended - logs errors, warnings, and informational messages</span></span>  
  
-   <span data-ttu-id="72737-401">详细 - 记录错误、警告、信息性消息、成功消息和其他内部消息。</span><span class="sxs-lookup"><span data-stu-id="72737-401">Verbose - logs errors, warnings, informational messages, success messages, and additional internal messages.</span></span> <span data-ttu-id="72737-402">使用详细日志记录可进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="72737-402">Use verbose logging for troubleshooting.</span></span>  
  
 <span data-ttu-id="72737-403">默认值为“扩展”。</span><span class="sxs-lookup"><span data-stu-id="72737-403">Default value is Extended.</span></span>  
  
 <span data-ttu-id="72737-404">**全部重置**</span><span class="sxs-lookup"><span data-stu-id="72737-404">**Reset All**</span></span>  
 <span data-ttu-id="72737-405">选择此选项可将该页上的值重置为默认值。</span><span class="sxs-lookup"><span data-stu-id="72737-405">Select this option to reset the values on the page to the default values.</span></span>  
  

  
###  <a name="complete-the-wizard-page"></a><a name="CompleteWizard"></a><span data-ttu-id="72737-406">完成向导页面</span><span class="sxs-lookup"><span data-stu-id="72737-406">Complete the Wizard Page</span></span>  
 <span data-ttu-id="72737-407">使用此页可以查看 **“数据库邮件配置向导”** 将要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="72737-407">Use this page to review the actions that **Database Mail Configuration Wizard** will perform.</span></span> <span data-ttu-id="72737-408">在完成该向导之前，不会进行任何更改。</span><span class="sxs-lookup"><span data-stu-id="72737-408">No changes are made until you finish the wizard.</span></span>  
  

  
###  <a name="send-test-e-mail-page"></a><a name="TestEmail"></a> <span data-ttu-id="72737-409">Send Test E-Mail Page</span><span class="sxs-lookup"><span data-stu-id="72737-409">Send Test E-Mail Page</span></span>  
 <span data-ttu-id="72737-410">使用**从 _<instance_name>_ 发送测试电子邮件**页，可以使用指定的数据库邮件配置文件发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="72737-410">Use the **Send Test E-Mail from**_<instance_name>_ page to send an e-mail message using the specified Database Mail profile.</span></span> <span data-ttu-id="72737-411">只有 **sysadmin** 固定服务器角色的成员才可以使用此页发送测试电子邮件。</span><span class="sxs-lookup"><span data-stu-id="72737-411">Only members of the **sysadmin** fixed server role can send test e-mail using this page.</span></span>  
  
 <span data-ttu-id="72737-412">**数据库邮件配置文件**</span><span class="sxs-lookup"><span data-stu-id="72737-412">**Database Mail Profile**</span></span>  
 <span data-ttu-id="72737-413">从列表中选择数据库邮件配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-413">Select a Database Mail profile from the list.</span></span> <span data-ttu-id="72737-414">这是必填字段。</span><span class="sxs-lookup"><span data-stu-id="72737-414">This is a required field.</span></span> <span data-ttu-id="72737-415">如果没有显示配置文件，则没有配置文件或您不具有选择配置文件的权限。</span><span class="sxs-lookup"><span data-stu-id="72737-415">If no profiles are shown, there are no profiles or you do not have permission to a profile.</span></span> <span data-ttu-id="72737-416">使用 **数据库邮件配置向导** 可以创建和配置配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-416">Use the **Database Mail Configuration Wizard** to create and configure profiles.</span></span> <span data-ttu-id="72737-417">如果没有列出配置文件，请使用数据库邮件配置向导来创建要使用的配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-417">If no profiles are listed, use the Database Mail Configuration Wizard to create a profile for your use.</span></span>  
  
 <span data-ttu-id="72737-418">**收件人**</span><span class="sxs-lookup"><span data-stu-id="72737-418">**To**</span></span>  
 <span data-ttu-id="72737-419">电子邮件收件人的地址。</span><span class="sxs-lookup"><span data-stu-id="72737-419">The e-mail address of the message recipients.</span></span> <span data-ttu-id="72737-420">至少需要一个收件人。</span><span class="sxs-lookup"><span data-stu-id="72737-420">At least one recipient is required.</span></span>  
  
 <span data-ttu-id="72737-421">**主题**</span><span class="sxs-lookup"><span data-stu-id="72737-421">**Subject**</span></span>  
 <span data-ttu-id="72737-422">测试电子邮件的主题行。</span><span class="sxs-lookup"><span data-stu-id="72737-422">The subject line for the test e-mail.</span></span> <span data-ttu-id="72737-423">更改默认主题，以更好地标识电子邮件以进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="72737-423">Change the default subject to better identify your email for troubleshooting.</span></span>  
  
 <span data-ttu-id="72737-424">**正文**</span><span class="sxs-lookup"><span data-stu-id="72737-424">**Body**</span></span>  
 <span data-ttu-id="72737-425">测试电子邮件的正文。</span><span class="sxs-lookup"><span data-stu-id="72737-425">The body of the test e-mail.</span></span> <span data-ttu-id="72737-426">更改默认主题，以更好地标识电子邮件以进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="72737-426">Change the default subject to better identify your email for troubleshooting.</span></span>  
  
 <span data-ttu-id="72737-427">“数据库邮件测试电子邮件”\*\*\*\* 对话框确认数据库邮件尝试发送的测试消息，并为测试电子邮件提供 **mailitem_id**。</span><span class="sxs-lookup"><span data-stu-id="72737-427">The **Database Mail Test E-Mail** dialog box confirms that the test message that Database Mail attempted to send the message and provides the **mailitem_id** for the test e-mail message.</span></span> <span data-ttu-id="72737-428">请与收件人核实以确定该电子邮件是否已到达。</span><span class="sxs-lookup"><span data-stu-id="72737-428">Check with the recipient to determine if the e-mail arrived.</span></span> <span data-ttu-id="72737-429">通常几分钟后即可接收到电子邮件，但是由于网络速度较慢、邮件服务器上的邮件积压或服务器暂时不可用，该电子邮件可能会延迟。</span><span class="sxs-lookup"><span data-stu-id="72737-429">Normally e-mail is received in a few minutes, but the e-mail can be delayed because of slow network performance, a backlog of messages at the mail server, or if the server is temporarily unavailable.</span></span> <span data-ttu-id="72737-430">使用 **mailitem_id** 以进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="72737-430">Use the **mailitem_id** for troubleshooting.</span></span>  
  
 <span data-ttu-id="72737-431">**发送电子邮件**</span><span class="sxs-lookup"><span data-stu-id="72737-431">**Sent e-mail**</span></span>  
 <span data-ttu-id="72737-432">测试电子邮件的 **mailitem_id** 。</span><span class="sxs-lookup"><span data-stu-id="72737-432">The **mailitem_id** of the test e-mail message.</span></span>  
  
 <span data-ttu-id="72737-433">**故障排除**</span><span class="sxs-lookup"><span data-stu-id="72737-433">**Troubleshoot**</span></span>  
 <span data-ttu-id="72737-434">单击可打开联机丛书的 [对数据库邮件进行故障排除](https://msdn.microsoft.com/library/ms188663.aspx)主题。</span><span class="sxs-lookup"><span data-stu-id="72737-434">Click to open Books Online to the [Troubleshooting Database Mail](https://msdn.microsoft.com/library/ms188663.aspx)topic.</span></span>  
  

  
##  <a name="using-templates"></a><a name="Template"></a><span data-ttu-id="72737-435">使用模板</span><span class="sxs-lookup"><span data-stu-id="72737-435">Using Templates</span></span>  
 <span data-ttu-id="72737-436">**创建数据库邮件配置脚本**</span><span class="sxs-lookup"><span data-stu-id="72737-436">**To create a Database Mail configuration script**</span></span>  
  
1.  <span data-ttu-id="72737-437">在 **“视图”** 菜单上，选择 **“模板资源管理器”**。</span><span class="sxs-lookup"><span data-stu-id="72737-437">On the **View** menu, select **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="72737-438">在 **“模板资源管理器”** 窗口中，展开 **“数据库邮件”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="72737-438">In the **Template Explorer** window, expand the **Database Mail** folder.</span></span>  
  
3.  <span data-ttu-id="72737-439">双击“简单数据库邮件配置”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="72737-439">Double-click **Simple Database Mail Configuration**.</span></span> <span data-ttu-id="72737-440">模板将在新的查询窗口中打开。</span><span class="sxs-lookup"><span data-stu-id="72737-440">The template opens in a new query window.</span></span>  
  
4.  <span data-ttu-id="72737-441">在 **“查询”** 菜单上，选择 **“指定模板参数的值”**。</span><span class="sxs-lookup"><span data-stu-id="72737-441">On the **Query** menu, select **Specify Values for Template Parameters**.</span></span> <span data-ttu-id="72737-442">将打开 **“替换模板参数”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="72737-442">The **Replace Template Parameters** window opens.</span></span>  
  
5.  <span data-ttu-id="72737-443">为 **profile_name**、 **account_name**、 **SMTP_servername**、 **email_address**和 **display_name**键入值。</span><span class="sxs-lookup"><span data-stu-id="72737-443">Type values for the **profile_name**, **account_name**, **SMTP_servername**, **email_address**, and **display_name**.</span></span> <span data-ttu-id="72737-444">SQL Server Management Studio 将使用您提供的值填充模板。</span><span class="sxs-lookup"><span data-stu-id="72737-444">SQL Server Management Studio fills in the template with the values you provide.</span></span>  
  
6.  <span data-ttu-id="72737-445">执行脚本来创建配置。</span><span class="sxs-lookup"><span data-stu-id="72737-445">Execute the script to create the configuration.</span></span>  
  
7.  <span data-ttu-id="72737-446">该脚本不授予任何数据库用户对配置文件的访问权限。</span><span class="sxs-lookup"><span data-stu-id="72737-446">The script does not grant any database users access to the profile.</span></span> <span data-ttu-id="72737-447">因此，默认情况下，只有 **sysadmin** 固定安全角色的成员才可以使用该配置文件。</span><span class="sxs-lookup"><span data-stu-id="72737-447">Therefore, by default, the profile can only be used by members of the **sysadmin** fixed security role.</span></span> <span data-ttu-id="72737-448">有关对配置文件授予访问权限的详细信息，请参阅 [sysmail_add_principalprofile_sp (Transact SQL)](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="72737-448">For more information about granting access to profiles, see [sysmail_add_principalprofile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql)</span></span>  
  
  
