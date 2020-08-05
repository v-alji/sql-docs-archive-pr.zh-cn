---
title: 创建数据库邮件帐户 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], accounts
- accounts [Database Mail]
ms.assetid: c07abbc6-fc6a-470b-8fa3-532f2e06b16a
author: stevestein
ms.author: sstein
ms.openlocfilehash: ec7d1c9147998b5a19cc0e6af13220bd64e165fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580295"
---
# <a name="create-a-database-mail-account"></a><span data-ttu-id="388b7-102">创建数据库邮件帐户</span><span class="sxs-lookup"><span data-stu-id="388b7-102">Create a Database Mail Account</span></span>
  <span data-ttu-id="388b7-103">使用 **“数据库邮件配置向导”** 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 可以创建数据库邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="388b7-103">Use either the **Database Mail Configuration Wizard** or [!INCLUDE[tsql](../../includes/tsql-md.md)] to create a Database Mail account.</span></span>  
  
-   <span data-ttu-id="388b7-104">**开始之前：** [先决条件](#Prerequisites)</span><span class="sxs-lookup"><span data-stu-id="388b7-104">**Before you begin:**  [Prerequisites](#Prerequisites)</span></span>  
  
-   <span data-ttu-id="388b7-105">使用以下内容创建数据库邮件帐户：  [数据库邮件配置向导](#SSMSProcedure)、[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="388b7-105">**To Create a Database Mail Account, using:**  [Database Mail Configuration Wizard](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
-   <span data-ttu-id="388b7-106">**跟进：** [用于配置数据库邮件的后续步骤](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="388b7-106">**Follow Up:**  [Next Steps to Configure the Database Mail](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="388b7-107">开始之前</span><span class="sxs-lookup"><span data-stu-id="388b7-107">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="388b7-108">先决条件</span><span class="sxs-lookup"><span data-stu-id="388b7-108">Prerequisites</span></span>  
  
-   <span data-ttu-id="388b7-109">确定用于发送电子邮件的服务器名称和简单邮件传输协议 (SMTP) 服务器的端口号。如果 SMTP 服务器需要身份验证，请确定 SMTP 服务器的用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="388b7-109">Determine the server name and port number for the Simple Mail Transfer Protocol (SMTP) server you use to send e-mail.If the SMTP server requires authentication, determine the user name and password for the SMTP server.</span></span>  
  
-   <span data-ttu-id="388b7-110">（可选）还可以指定服务器的类型和服务器的端口号。</span><span class="sxs-lookup"><span data-stu-id="388b7-110">Optionally, you may also specify the type of the server and the port number for the server.</span></span> <span data-ttu-id="388b7-111">发送邮件的服务器类型始终为 SMTP。</span><span class="sxs-lookup"><span data-stu-id="388b7-111">The server type is always 'SMTP' for outgoing mail.</span></span> <span data-ttu-id="388b7-112">默认情况下，大多数 SMTP 服务器使用端口 25。</span><span class="sxs-lookup"><span data-stu-id="388b7-112">Most SMTP servers use port 25, the default.</span></span>  
  
##  <a name="using-database-mail-configuration-wizard"></a><a name="SSMSProcedure"></a> <span data-ttu-id="388b7-113">使用数据库邮件配置向导</span><span class="sxs-lookup"><span data-stu-id="388b7-113">Using Database Mail Configuration Wizard</span></span>  
 <span data-ttu-id="388b7-114">**使用向导创建数据库邮件帐户**</span><span class="sxs-lookup"><span data-stu-id="388b7-114">**To create a Database Mail account using a Wizard**</span></span>  
  
-   <span data-ttu-id="388b7-115">在对象资源管理器中，连接到您要在其上配置数据库邮件的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，然后展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="388b7-115">In Object Explorer, connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you want to configure Database Mail on, and expand the server tree.</span></span>  
  
-   <span data-ttu-id="388b7-116">展开 **“管理”** 节点</span><span class="sxs-lookup"><span data-stu-id="388b7-116">Expand the **Management** node</span></span>  
  
-   <span data-ttu-id="388b7-117">双击数据库邮件以打开数据库邮件配置向导。</span><span class="sxs-lookup"><span data-stu-id="388b7-117">Double Click Database Mail to open the Database Mail Configuration Wizard.</span></span>  
  
-   <span data-ttu-id="388b7-118">在 **“选择配置任务”** 页上，选择 **“管理数据库邮件帐户和配置文件”** ，然后单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="388b7-118">On the **Select Configuration Task** page, select **Manage Database Mail accounts and profiles**, and click **Next**.</span></span>  
  
-   <span data-ttu-id="388b7-119">在 **“管理配置文件和帐户”** 页上，选择 **“创建新帐户”** ，然后单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="388b7-119">On the **Manage Profiles and Accounts** page, select **Create a new account** and click **Next**.</span></span>  
  
-   <span data-ttu-id="388b7-120">在 **“新建帐户”** 页上，指定帐户名称、说明、邮件服务器信息和身份验证类型。</span><span class="sxs-lookup"><span data-stu-id="388b7-120">On the **New Account** page, specify the account name, description, mail server information, and authentication type.</span></span> <span data-ttu-id="388b7-121">点击“下一步” </span><span class="sxs-lookup"><span data-stu-id="388b7-121">Click **Next**</span></span>  
  
-   <span data-ttu-id="388b7-122">在 **“完成该向导”** 页上，检查要执行的操作，然后单击 **“完成”** 以完成创建新帐户。</span><span class="sxs-lookup"><span data-stu-id="388b7-122">On the **Complete the Wizard** page, review the actions to be performed and click **Finish** to complete creating the new account.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="388b7-123">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="388b7-123">Using Transact-SQL</span></span>  
 <span data-ttu-id="388b7-124">**使用 Transact-SQL 创建数据库邮件帐户**</span><span class="sxs-lookup"><span data-stu-id="388b7-124">**To Create a Database Mail account using Transact-SQL**</span></span>  
  
 <span data-ttu-id="388b7-125">执行存储过程 **msdb.dbo.sysmail_add_account_sp** 以创建帐户，并指定以下信息：</span><span class="sxs-lookup"><span data-stu-id="388b7-125">Execute the stored procedure **msdb.dbo.sysmail_add_account_sp** to create the account and specify the following information:</span></span>  
  
-   <span data-ttu-id="388b7-126">要创建的帐户名。</span><span class="sxs-lookup"><span data-stu-id="388b7-126">The name of the account to create.</span></span>  
  
-   <span data-ttu-id="388b7-127">帐户的可选说明。</span><span class="sxs-lookup"><span data-stu-id="388b7-127">An optional description of the account.</span></span>  
  
-   <span data-ttu-id="388b7-128">要在发送的电子邮件上显示的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="388b7-128">The e-mail address to show on outgoing e-mail messages.</span></span>  
  
-   <span data-ttu-id="388b7-129">要在发送的电子邮件上显示的显示名称。</span><span class="sxs-lookup"><span data-stu-id="388b7-129">The display name to show on outgoing e-mail messages.</span></span>  
  
-   <span data-ttu-id="388b7-130">SMTP 服务器名称。</span><span class="sxs-lookup"><span data-stu-id="388b7-130">The server name of the SMTP server.</span></span>  
  
-   <span data-ttu-id="388b7-131">用于登录到 SMTP 服务器的用户名（如果 SMTP 服务器要求身份验证）。</span><span class="sxs-lookup"><span data-stu-id="388b7-131">The user name to use to log on to the SMTP server, if the SMTP server requires authentication.</span></span>  
  
-   <span data-ttu-id="388b7-132">用于登录到 SMTP 服务器的密码（如果 SMTP 服务器要求身份验证）。</span><span class="sxs-lookup"><span data-stu-id="388b7-132">The password to use to log on to the SMTP server, if the SMTP server requires authentication.</span></span>  
  
 <span data-ttu-id="388b7-133">以下示例将创建一个新数据库邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="388b7-133">The following example creates a new Database Mail account.</span></span>  
  
```  
EXECUTE msdb.dbo.sysmail_add_account_sp  
    @account_name = 'AdventureWorks Administrator',  
    @description = 'Mail account for administrative e-mail.',  
    @email_address = 'dba@Adventure-Works.com',  
    @display_name = 'AdventureWorks Automated Mailer',  
    @mailserver_name = 'smtp.Adventure-Works.com' ;  
```  
  
##  <a name="follow-up-next-steps-to-configuring-the-database-mail"></a><a name="FollowUp"></a> <span data-ttu-id="388b7-134">跟进：用于配置数据库邮件的后续步骤</span><span class="sxs-lookup"><span data-stu-id="388b7-134">Follow Up: Next Steps to Configuring the Database Mail</span></span>  
  
-   [<span data-ttu-id="388b7-135">创建数据库邮件配置文件</span><span class="sxs-lookup"><span data-stu-id="388b7-135">Create a Database Mail Profile</span></span>](create-a-database-mail-profile.md)  
  
  
