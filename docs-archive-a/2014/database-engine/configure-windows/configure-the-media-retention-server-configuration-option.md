---
title: 配置“介质保持期”服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- backup retention duration [SQL Server]
- backup sets [SQL Server], retention duration
- media retention option
ms.assetid: 12e9fe6a-20a5-4c6e-9cc9-d500c003b70a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 092e0a2b5cfc30fd2d2362645fc1242bf4a1651e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580370"
---
# <a name="configure-the-media-retention-server-configuration-option"></a><span data-ttu-id="f6d75-102">配置 media retention 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="f6d75-102">Configure the media retention Server Configuration Option</span></span>
  <span data-ttu-id="f6d75-103">本主题说明如何使用 **或** 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中配置 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] media retention [!INCLUDE[tsql](../../includes/tsql-md.md)]服务器配置选项。</span><span class="sxs-lookup"><span data-stu-id="f6d75-103">This topic describes how to configure the **media retention** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="f6d75-104">**media retention** 选项指定保留每个备份集的时间长度。</span><span class="sxs-lookup"><span data-stu-id="f6d75-104">The **media retention** option specifies the length of time to retain each backup set.</span></span> <span data-ttu-id="f6d75-105">此选项可以防止在指定的天数前覆盖备份。</span><span class="sxs-lookup"><span data-stu-id="f6d75-105">The option helps protect backups from being overwritten until the specified number of days has elapsed.</span></span> <span data-ttu-id="f6d75-106">配置了 **media retention** 选项后，无需在每次进行备份时都指定系统备份的保持时间。</span><span class="sxs-lookup"><span data-stu-id="f6d75-106">After you configure **media retention** option, you do not have to specify the length of time to retain system backups each time you perform a backup.</span></span> <span data-ttu-id="f6d75-107">默认值为 0 天，最大值为 365 天。</span><span class="sxs-lookup"><span data-stu-id="f6d75-107">The default value is 0 days, and the maximum value is 365 days.</span></span>  
  
 <span data-ttu-id="f6d75-108">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="f6d75-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f6d75-109">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="f6d75-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f6d75-110">限制和局限</span><span class="sxs-lookup"><span data-stu-id="f6d75-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f6d75-111">建议</span><span class="sxs-lookup"><span data-stu-id="f6d75-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="f6d75-112">安全性</span><span class="sxs-lookup"><span data-stu-id="f6d75-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f6d75-113">**配置 media retention 选项，使用：**</span><span class="sxs-lookup"><span data-stu-id="f6d75-113">**To configure the media retention option, using:**</span></span>  
  
     [<span data-ttu-id="f6d75-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f6d75-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f6d75-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f6d75-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="f6d75-116">**跟进：** [在配置介质保留期选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="f6d75-116">**Follow Up:**  [After you configure the media retention option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f6d75-117">开始之前</span><span class="sxs-lookup"><span data-stu-id="f6d75-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f6d75-118">限制和局限</span><span class="sxs-lookup"><span data-stu-id="f6d75-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="f6d75-119">如果未等设定的天数过去即使用备份介质， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将会发出警告消息。</span><span class="sxs-lookup"><span data-stu-id="f6d75-119">If you use the backup medium before the set number of days has passed, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] issues a warning message.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f6d75-120">不会发出警告。</span><span class="sxs-lookup"><span data-stu-id="f6d75-120">does not issue a warning unless you change the default.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="f6d75-121">建议</span><span class="sxs-lookup"><span data-stu-id="f6d75-121">Recommendations</span></span>  
  
-   <span data-ttu-id="f6d75-122">此选项是一个高级选项，仅应由有经验的数据库管理员或认证的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技术人员更改。</span><span class="sxs-lookup"><span data-stu-id="f6d75-122">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="f6d75-123">**media retention** 选项可以使用 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 语句的 RETAINDAYS 子句覆盖。</span><span class="sxs-lookup"><span data-stu-id="f6d75-123">The **media retention** option can be overridden by using the RETAINDAYS clause of the [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f6d75-124">Security</span><span class="sxs-lookup"><span data-stu-id="f6d75-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f6d75-125">权限</span><span class="sxs-lookup"><span data-stu-id="f6d75-125">Permissions</span></span>  
 <span data-ttu-id="f6d75-126">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="f6d75-126">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="f6d75-127">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="f6d75-127">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="f6d75-128">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="f6d75-128">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f6d75-129">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f6d75-129">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-media-retention-option"></a><span data-ttu-id="f6d75-130">配置 media retention 选项</span><span class="sxs-lookup"><span data-stu-id="f6d75-130">To configure the media retention option</span></span>  
  
1.  <span data-ttu-id="f6d75-131">在对象资源管理器中，右键单击服务器并选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="f6d75-131">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="f6d75-132">单击 **“数据库设置”** 节点。</span><span class="sxs-lookup"><span data-stu-id="f6d75-132">Click the **Database settings** node.</span></span>  
  
3.  <span data-ttu-id="f6d75-133">在 **“备份/还原”** 下的 **“默认备份媒体保持期”** 框中，键入或选择一个 0 到 365 之间的值，以设置备份媒体在数据库或事务日志备份后保留的天数。</span><span class="sxs-lookup"><span data-stu-id="f6d75-133">Under **Backup/Restore**, in the **Default backup media retention** box, type or select a value from 0 through 365 to set the number of days the backup medium will be retained after a database or transaction log backup.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f6d75-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f6d75-134">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-media-retention-option"></a><span data-ttu-id="f6d75-135">配置 media retention 选项</span><span class="sxs-lookup"><span data-stu-id="f6d75-135">To configure the media retention option</span></span>  
  
1.  <span data-ttu-id="f6d75-136">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f6d75-136">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f6d75-137">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="f6d75-137">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f6d75-138">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="f6d75-138">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="f6d75-139">此示例说明如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将 `media retention` 选项的值设置为 `60` 天。</span><span class="sxs-lookup"><span data-stu-id="f6d75-139">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `media retention` option to `60` days.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'media retention', 60 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="f6d75-140">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="f6d75-140">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-media-retention-option"></a><a name="FollowUp"></a> <span data-ttu-id="f6d75-141">跟进：在配置介质保留期选项之后</span><span class="sxs-lookup"><span data-stu-id="f6d75-141">Follow Up: After you configure the media retention option</span></span>  
 <span data-ttu-id="f6d75-142">该设置将立即生效，无需重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="f6d75-142">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6d75-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f6d75-143">See Also</span></span>  
 <span data-ttu-id="f6d75-144">[SQL Server 数据库的备份和还原](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="f6d75-144">[Back Up and Restore of SQL Server Databases](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="f6d75-145">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f6d75-145">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="f6d75-146">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f6d75-146">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="f6d75-147">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f6d75-147">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="f6d75-148">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f6d75-148">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
