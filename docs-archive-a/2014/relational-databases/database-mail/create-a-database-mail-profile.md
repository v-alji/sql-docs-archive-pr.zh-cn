---
title: 创建数据库邮件配置文件 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], public profiles
- profiles [SQL Server], Database Mail
- public profiles [Database Mail]
ms.assetid: 58ae749d-6ada-4f9c-bf00-de7c7a992a2d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0453d495c90c1e599bfc7777b4899f30e6659c52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580294"
---
# <a name="create-a-database-mail-profile"></a><span data-ttu-id="730c2-102">创建数据库邮件配置文件</span><span class="sxs-lookup"><span data-stu-id="730c2-102">Create a Database Mail Profile</span></span>
  <span data-ttu-id="730c2-103">使用 **数据库邮件配置向导** 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 可创建数据库邮件的公共和专用配置文件。</span><span class="sxs-lookup"><span data-stu-id="730c2-103">Use either the **Database Mail Configuration Wizard** or [!INCLUDE[tsql](../../includes/tsql-md.md)] to create Database Mail public and private profiles.</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="730c2-104">开始之前</span><span class="sxs-lookup"><span data-stu-id="730c2-104">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="730c2-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="730c2-105">Prerequisites</span></span>  
 <span data-ttu-id="730c2-106">为配置文件创建一个或多个数据库邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="730c2-106">Create one or more Database Mail accounts for the profile.</span></span> <span data-ttu-id="730c2-107">有关创建数据库邮件帐户的详细信息，请参阅 [创建数据库邮件帐户](create-a-database-mail-account.md)。</span><span class="sxs-lookup"><span data-stu-id="730c2-107">For more information about creating Database Mail accounts, see [Create a Database Mail Account](create-a-database-mail-account.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="730c2-108">Security</span><span class="sxs-lookup"><span data-stu-id="730c2-108">Security</span></span>  
 <span data-ttu-id="730c2-109">公共配置文件允许有权访问 **msdb** 数据库的任意用户使用该配置文件发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="730c2-109">A public profile allows any user with access to the **msdb** database to send e-mail using that profile.</span></span> <span data-ttu-id="730c2-110">专用配置文件可由用户或角色来使用。</span><span class="sxs-lookup"><span data-stu-id="730c2-110">A private profile can be used by a user or by a role.</span></span> <span data-ttu-id="730c2-111">授予角色访问配置文件的权限可创建更易维护的体系结构。</span><span class="sxs-lookup"><span data-stu-id="730c2-111">Granting roles access to profiles creates a more easily maintained architecture.</span></span> <span data-ttu-id="730c2-112">若要发送邮件，您必须是 **msdb** 数据库中的 **DatabaseMailUserRole** 的成员，并且至少有权访问一个数据库邮件配置文件。</span><span class="sxs-lookup"><span data-stu-id="730c2-112">To send mail you must be a member of the **DatabaseMailUserRole** in the **msdb** database, and have access to at least one Database Mail profile.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="730c2-113">权限</span><span class="sxs-lookup"><span data-stu-id="730c2-113">Permissions</span></span>  
 <span data-ttu-id="730c2-114">创建配置文件帐户和执行存储过程的用户应是 sysadmin 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="730c2-114">The user creating the profiles accounts and executing stored procedures should be a member of the sysadmin fixed server role.</span></span>  
  

  
##  <a name="using-database-mail-configuration-wizard"></a><a name="SSMSProcedure"></a> <span data-ttu-id="730c2-115">使用数据库邮件配置向导</span><span class="sxs-lookup"><span data-stu-id="730c2-115">Using Database Mail Configuration Wizard</span></span>  
 <span data-ttu-id="730c2-116">**创建数据库邮件配置文件**</span><span class="sxs-lookup"><span data-stu-id="730c2-116">**To Create a Database Mail profile**</span></span>  
  
-   <span data-ttu-id="730c2-117">在对象资源管理器中，连接到您要在其上配置数据库邮件的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，然后展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="730c2-117">In Object Explorer, connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you want to configure Database Mail on, and expand the server tree.</span></span>  
  
-   <span data-ttu-id="730c2-118">展开 **“管理”** 节点</span><span class="sxs-lookup"><span data-stu-id="730c2-118">Expand the **Management** node</span></span>  
  
-   <span data-ttu-id="730c2-119">双击数据库邮件以打开数据库邮件配置向导。</span><span class="sxs-lookup"><span data-stu-id="730c2-119">Double click Database Mail to open the Database Mail Configuration Wizard.</span></span>  
  
-   <span data-ttu-id="730c2-120">在 "**选择配置任务**" 页上，选择 "**管理数据库邮件帐户和配置文件**" 选项并单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="730c2-120">On the **Select Configuration Task** page, select **Manage Database Mail accounts and profiles** option and click **Next**.</span></span>  
  
-   <span data-ttu-id="730c2-121">在 **“管理配置文件和帐户”** 页上，选择 **“创建新配置文件”** 选项，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="730c2-121">On the **Manage Profiles and Accounts** page, select **Create a new profile** option, and click **Next**.</span></span>  
  
-   <span data-ttu-id="730c2-122">在“新建配置文件”页上，指定配置文件的名称、说明并添加要包括在配置文件中的帐户，然后单击“下一步”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="730c2-122">On the **New Profile** page, specify the Profile name, Description and add accounts to be included in the profile, and click **Next**.</span></span>  
  
-   <span data-ttu-id="730c2-123">在 **“完成该向导”** 页上，检查要执行的操作，然后单击 **“完成”** 以完成创建新配置文件。</span><span class="sxs-lookup"><span data-stu-id="730c2-123">On the **Complete the Wizard** page, review the actions to be performed and click **Finish** to complete creating the new profile.</span></span>  
  
-   <span data-ttu-id="730c2-124">**配置数据库邮件专用配置文件：**</span><span class="sxs-lookup"><span data-stu-id="730c2-124">**To configure a Database Mail private profile:**</span></span>  
  
    -   <span data-ttu-id="730c2-125">打开数据库邮件配置向导。</span><span class="sxs-lookup"><span data-stu-id="730c2-125">Open the Database Mail Configuration Wizard.</span></span>  
  
    -   <span data-ttu-id="730c2-126">在 **“选择配置任务”** 页上，选择 **“管理数据库邮件帐户和配置文件”** 选项，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="730c2-126">On the **Select Configuration Task** page, select **Manage Database Mail accounts and profiles** option, and click **Next**.</span></span>  
  
    -   <span data-ttu-id="730c2-127">在 **“管理配置文件和帐户”** 页上，选择 **“管理配置文件安全性”** 选项，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="730c2-127">On the **Manage Profiles and Accounts** page, select **Manage profile security** option and click **Next**.</span></span>  
  
    -   <span data-ttu-id="730c2-128">在 **“专用配置文件”** 选项卡中，选中您要配置的配置文件所对应的复选框，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="730c2-128">In the **Private Profiles** tab, select the check box for the profile you would like to configure and click **Next**.</span></span>  
  
    -   <span data-ttu-id="730c2-129">在 **“完成该向导”** 页上，检查要执行的操作，然后单击 **“完成”** 以完成配置该配置文件。</span><span class="sxs-lookup"><span data-stu-id="730c2-129">On the **Complete the Wizard** page, review the actions to be performed and click **Finish** to complete configuring the profile.</span></span>  
  
-   <span data-ttu-id="730c2-130">**配置数据库邮件公共配置文件：**</span><span class="sxs-lookup"><span data-stu-id="730c2-130">**To configure a Database Mail public profile:**</span></span>  
  
    -   <span data-ttu-id="730c2-131">打开数据库邮件配置向导。</span><span class="sxs-lookup"><span data-stu-id="730c2-131">Open the Database Mail Configuration Wizard.</span></span>  
  
    -   <span data-ttu-id="730c2-132">在 **“选择配置任务”** 页上，选择 **“管理数据库邮件帐户和配置文件”** 选项，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="730c2-132">On the **Select Configuration Task** page, select **Manage Database Mail accounts and profiles** option, and click **Next**.</span></span>  
  
    -   <span data-ttu-id="730c2-133">在 **“管理配置文件和帐户”** 页上，选择 **“管理配置文件安全性”** 选项，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="730c2-133">On the **Manage Profiles and Accounts** page, select **Manage profile security** option and click **Next**.</span></span>  
  
    -   <span data-ttu-id="730c2-134">在 **“公共配置文件”** 选项卡中，选中您要配置的配置文件所对应的复选框，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="730c2-134">In the **Public Profiles** tab, select the check box for the profile you would like to configure and click **Next**.</span></span>  
  
    -   <span data-ttu-id="730c2-135">在 **“完成该向导”** 页上，检查要执行的操作，然后单击 **“完成”** 以完成配置该配置文件。</span><span class="sxs-lookup"><span data-stu-id="730c2-135">On the **Complete the Wizard** page, review the actions to be performed and click **Finish** to complete configuring the profile.</span></span>  
  

  
## <a name="using-transact-sql"></a><span data-ttu-id="730c2-136">“使用 Transact-SQL”</span><span class="sxs-lookup"><span data-stu-id="730c2-136">Using Transact-SQL</span></span>  
  
###  <a name="to-create-a-database-mail-private-profile"></a><a name="PrivateProfile"></a><span data-ttu-id="730c2-137">创建数据库邮件专用配置文件</span><span class="sxs-lookup"><span data-stu-id="730c2-137">To Create a Database Mail private profile</span></span>  
  
-   <span data-ttu-id="730c2-138">连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="730c2-138">Connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="730c2-139">若要创建新的配置文件，请运行系统存储过程 [sysmail_add_profile_sp (Transact SQL)](/sql/relational-databases/system-stored-procedures/sysmail-add-profile-sp-transact-sql)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="730c2-139">To create a new profile, run the system stored procedure [sysmail_add_profile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profile-sp-transact-sql) as follows:</span></span>  
  
     <span data-ttu-id="730c2-140">**EXECUTEmsdb.dbo.sysmail_add_profile_sp**</span><span class="sxs-lookup"><span data-stu-id="730c2-140">**EXECUTEmsdb.dbo.sysmail_add_profile_sp**</span></span>  
  
     <span data-ttu-id="730c2-141">*@profile_name*= '*配置文件名称*'</span><span class="sxs-lookup"><span data-stu-id="730c2-141">*@profile_name* = '*Profile Name*'</span></span>  
  
     <span data-ttu-id="730c2-142">*@description*= '*说明 '*</span><span class="sxs-lookup"><span data-stu-id="730c2-142">*@description* = '*Desciption*'</span></span>  
  
     <span data-ttu-id="730c2-143">其中 *@profile_name* ，是配置文件的名称， *@description* 是配置文件的说明。</span><span class="sxs-lookup"><span data-stu-id="730c2-143">where *@profile_name* is the name of the profile, and *@description* is the description of the profile.</span></span> <span data-ttu-id="730c2-144">此参数是可选的。</span><span class="sxs-lookup"><span data-stu-id="730c2-144">This parameter is optional.</span></span>  
  
-   <span data-ttu-id="730c2-145">对于每个帐户，运行存储过程 [sysmail_add_profileaccount_sp (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="730c2-145">For each account, run the stored procedure [sysmail_add_profileaccount_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql) as follows:</span></span>  
  
     <span data-ttu-id="730c2-146">**EXECUTEmsdb.dbo.sysmail_add_profileaccount_sp**</span><span class="sxs-lookup"><span data-stu-id="730c2-146">**EXECUTEmsdb.dbo.sysmail_add_profileaccount_sp**</span></span>  
  
     <span data-ttu-id="730c2-147">*@profile_name*= '*配置文件的名称*'</span><span class="sxs-lookup"><span data-stu-id="730c2-147">*@profile_name* = '*Name of the profile*'</span></span>  
  
     <span data-ttu-id="730c2-148">*@account_name*= '*帐户名称*</span><span class="sxs-lookup"><span data-stu-id="730c2-148">*@account_name* = '*Name of the account*'</span></span>  
  
     <span data-ttu-id="730c2-149">*@sequence_number*= '*配置文件中帐户的序列号。*</span><span class="sxs-lookup"><span data-stu-id="730c2-149">*@sequence_number* = '*sequence number of the account within the profile.*</span></span> <span data-ttu-id="730c2-150">'</span><span class="sxs-lookup"><span data-stu-id="730c2-150">'</span></span>  
  
     <span data-ttu-id="730c2-151">其中 *@profile_name* ，是配置文件的名称， *@account_name* 是要添加到配置文件的帐户的名称， *@sequence_number* 用于确定在配置文件中使用帐户的顺序。</span><span class="sxs-lookup"><span data-stu-id="730c2-151">where *@profile_name* is the name of the profile, and *@account_name* is the name of the account to add to the profile, *@sequence_number* determines the order in which the accounts are used in the profile.</span></span>  
  
-   <span data-ttu-id="730c2-152">对于将使用此配置文件发送邮件的每个数据库角色或用户，请向他们授予对此配置文件的访问权限。</span><span class="sxs-lookup"><span data-stu-id="730c2-152">For each database role or user that will send mail using this profile, grant access to the profile.</span></span> <span data-ttu-id="730c2-153">对于每个帐户，运行存储过程 [sysmail_add_principalprofile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="730c2-153">To do this, run the stored procedure [sysmail_add_principalprofile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql) as follows:</span></span>  
  
     <span data-ttu-id="730c2-154">**EXECUTEmsdb.sysmail_add_principalprofile_sp**</span><span class="sxs-lookup"><span data-stu-id="730c2-154">**EXECUTEmsdb.sysmail_add_principalprofile_sp**</span></span>  
  
     <span data-ttu-id="730c2-155">*@profile_name*= '*配置文件的名称*'</span><span class="sxs-lookup"><span data-stu-id="730c2-155">*@profile_name* = '*Name of the profile*'</span></span>  
  
     <span data-ttu-id="730c2-156">*@ principal_name* = '数据库用户或角色的名称\*\*'</span><span class="sxs-lookup"><span data-stu-id="730c2-156">*@ principal_name* = '*Name of the database user or role*'</span></span>  
  
     <span data-ttu-id="730c2-157">*@is_default*= '*默认配置文件状态*'</span><span class="sxs-lookup"><span data-stu-id="730c2-157">*@is_default* = '*Default Profile status* '</span></span>  
  
     <span data-ttu-id="730c2-158">其中 *@profile_name* ，是配置文件的名称， *@principal_name* 是数据库用户或角色的名称， *@is_default* 确定此配置文件是否为数据库用户或角色的默认值。</span><span class="sxs-lookup"><span data-stu-id="730c2-158">where *@profile_name* is the name of the profile, and *@principal_name* is the name of the database user or role, *@is_default* determines the whether this profile is the default for the database user or role.</span></span>  
  
 <span data-ttu-id="730c2-159">以下示例创建了一个数据库邮件帐户和一个数据库邮件专用配置文件，然后将帐户添加到该配置文件中，并向 **msdb** 数据库中的 **DBMailUsers** 数据库角色授予对该配置文件的访问权限。</span><span class="sxs-lookup"><span data-stu-id="730c2-159">The following example creates a Database Mail account, creates a Database Mail private profile, then adds the account to the profile and grants access to the profile to the **DBMailUsers** database role in the **msdb** database.</span></span>  
  
```  
-- Create a Database Mail account  
EXECUTE msdb.dbo.sysmail_add_account_sp  
    @account_name = 'AdventureWorks Administrator',  
    @description = 'Mail account for administrative e-mail.',  
    @email_address = 'dba@Adventure-Works.com',  
    @replyto_address = 'danw@Adventure-Works.com',  
    @display_name = 'AdventureWorks Automated Mailer',  
    @mailserver_name = 'smtp.Adventure-Works.com' ;  
  
-- Create a Database Mail profile  
EXECUTE msdb.dbo.sysmail_add_profile_sp  
    @profile_name = 'AdventureWorks Administrator Profile',  
    @description = 'Profile used for administrative mail.' ;  
  
-- Add the account to the profile  
EXECUTE msdb.dbo.sysmail_add_profileaccount_sp  
    @profile_name = 'AdventureWorks Administrator Profile',  
    @account_name = 'AdventureWorks Administrator',  
    @sequence_number =1 ;  
  
-- Grant access to the profile to the DBMailUsers role  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @profile_name = 'AdventureWorks Administrator Profile',  
    @principal_name = 'ApplicationUser',  
    @is_default = 1 ;  
```  
  
 
  
###  <a name="to-create-a-database-mail-public-profile"></a><a name="PublicProfile"></a><span data-ttu-id="730c2-160">创建数据库邮件公用配置文件</span><span class="sxs-lookup"><span data-stu-id="730c2-160">To Create a Database Mail public profile</span></span>  
  
-   <span data-ttu-id="730c2-161">连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="730c2-161">Connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="730c2-162">若要创建新的配置文件，请运行系统存储过程 [sysmail_add_profile_sp (Transact SQL)](/sql/relational-databases/system-stored-procedures/sysmail-add-profile-sp-transact-sql)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="730c2-162">To create a new profile, run the system stored procedure [sysmail_add_profile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profile-sp-transact-sql) as follows:</span></span>  
  
     <span data-ttu-id="730c2-163">**EXECUTEmsdb.dbo.sysmail_add_profile_sp**</span><span class="sxs-lookup"><span data-stu-id="730c2-163">**EXECUTEmsdb.dbo.sysmail_add_profile_sp**</span></span>  
  
     <span data-ttu-id="730c2-164">*@profile_name*= '*配置文件名称*'</span><span class="sxs-lookup"><span data-stu-id="730c2-164">*@profile_name* = '*Profile Name*'</span></span>  
  
     <span data-ttu-id="730c2-165">*@description*= '*说明 '*</span><span class="sxs-lookup"><span data-stu-id="730c2-165">*@description* = '*Desciption*'</span></span>  
  
     <span data-ttu-id="730c2-166">其中 *@profile_name* ，是配置文件的名称， *@description* 是配置文件的说明。</span><span class="sxs-lookup"><span data-stu-id="730c2-166">where *@profile_name* is the name of the profile, and *@description* is the description of the profile.</span></span> <span data-ttu-id="730c2-167">此参数是可选的。</span><span class="sxs-lookup"><span data-stu-id="730c2-167">This parameter is optional.</span></span>  
  
-   <span data-ttu-id="730c2-168">对于每个帐户，运行存储过程 [sysmail_add_profileaccount_sp (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="730c2-168">For each account, run the stored procedure [sysmail_add_profileaccount_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql) as follows:</span></span>  
  
     <span data-ttu-id="730c2-169">**EXECUTEmsdb.dbo.sysmail_add_profileaccount_sp**</span><span class="sxs-lookup"><span data-stu-id="730c2-169">**EXECUTEmsdb.dbo.sysmail_add_profileaccount_sp**</span></span>  
  
     <span data-ttu-id="730c2-170">*@profile_name*= '*配置文件的名称*'</span><span class="sxs-lookup"><span data-stu-id="730c2-170">*@profile_name* = '*Name of the profile*'</span></span>  
  
     <span data-ttu-id="730c2-171">*@account_name*= '*帐户名称*</span><span class="sxs-lookup"><span data-stu-id="730c2-171">*@account_name* = '*Name of the account*'</span></span>  
  
     <span data-ttu-id="730c2-172">*@sequence_number*= '*配置文件中帐户的序列号。*</span><span class="sxs-lookup"><span data-stu-id="730c2-172">*@sequence_number* = '*sequence number of the account within the profile.*</span></span> <span data-ttu-id="730c2-173">'</span><span class="sxs-lookup"><span data-stu-id="730c2-173">'</span></span>  
  
     <span data-ttu-id="730c2-174">其中 *@profile_name* ，是配置文件的名称， *@account_name* 是要添加到配置文件的帐户的名称， *@sequence_number* 用于确定在配置文件中使用帐户的顺序。</span><span class="sxs-lookup"><span data-stu-id="730c2-174">where *@profile_name* is the name of the profile, and *@account_name* is the name of the account to add to the profile, *@sequence_number* determines the order in which the accounts are used in the profile.</span></span>  
  
-   <span data-ttu-id="730c2-175">若要授予公共访问权限，请运行存储过程 [sysmail_add_principalprofile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="730c2-175">To grant public access, run the stored procedure [sysmail_add_principalprofile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql) as follows:</span></span>  
  
     <span data-ttu-id="730c2-176">**EXECUTEmsdb.sysmail_add_principalprofile_sp**</span><span class="sxs-lookup"><span data-stu-id="730c2-176">**EXECUTEmsdb.sysmail_add_principalprofile_sp**</span></span>  
  
     <span data-ttu-id="730c2-177">*@profile_name*= '*配置文件的名称*'</span><span class="sxs-lookup"><span data-stu-id="730c2-177">*@profile_name* = '*Name of the profile*'</span></span>  
  
     <span data-ttu-id="730c2-178">*@ principal_name* = '**公共** 或 **0**'</span><span class="sxs-lookup"><span data-stu-id="730c2-178">*@ principal_name* = '**public** or **0**'</span></span>  
  
     <span data-ttu-id="730c2-179">*@is_default*= '*默认配置文件状态*'</span><span class="sxs-lookup"><span data-stu-id="730c2-179">*@is_default* = '*Default Profile status* '</span></span>  
  
     <span data-ttu-id="730c2-180">其中， *@profile_name* 是配置文件的名称，指示此配置文件是 *@principal_name* 公共配置文件， *@is_default* 确定此配置文件是否为数据库用户或角色的默认值。</span><span class="sxs-lookup"><span data-stu-id="730c2-180">where *@profile_name* is the name of the profile, and *@principal_name* to indicate this is a public profile, *@is_default* determines the whether this profile is the default for the database user or role.</span></span>  
  
 <span data-ttu-id="730c2-181">以下示例创建了一个数据库邮件帐户和一个数据库邮件专用配置文件，然后将帐户添加到该配置文件中并授予对该配置文件的公共访问权限。</span><span class="sxs-lookup"><span data-stu-id="730c2-181">The following example creates a Database Mail account, creates a Database Mail private profile, then adds the account to the profile and grants public access to the profile.</span></span>  
  
```  
-- Create a Database Mail account  
  
EXECUTE msdb.dbo.sysmail_add_account_sp  
    @account_name = 'AdventureWorks Public Account',  
    @description = 'Mail account for use by all database users.',  
    @email_address = 'db_users@Adventure-Works.com',  
    @replyto_address = 'danw@Adventure-Works.com',  
    @display_name = 'AdventureWorks Automated Mailer',  
    @mailserver_name = 'smtp.Adventure-Works.com' ;  
  
-- Create a Database Mail profile  
  
EXECUTE msdb.dbo.sysmail_add_profile_sp  
    @profile_name = 'AdventureWorks Public Profile',  
    @description = 'Profile used for administrative mail.' ;  
  
-- Add the account to the profile  
  
EXECUTE msdb.dbo.sysmail_add_profileaccount_sp  
    @profile_name = 'AdventureWorks Public Profile',  
    @account_name = 'AdventureWorks Public Account',  
    @sequence_number =1 ;  
  
-- Grant access to the profile to all users in the msdb database  
  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @profile_name = 'AdventureWorks Public Profile',  
    @principal_name = 'public',  
    @is_default = 1 ;  
```  
  

  
  
