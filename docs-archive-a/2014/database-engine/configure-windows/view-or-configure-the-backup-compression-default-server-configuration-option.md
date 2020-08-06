---
title: 查看或配置 backup compression default 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], backup compression default option
- backup compression [SQL Server], backup compression default Option
ms.assetid: 23029395-3e93-4c29-b7d6-e5a47a3526ff
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f02458c069d7c155b199e24feb7ef028ae0f258a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591573"
---
# <a name="view-or-configure-the-backup-compression-default-server-configuration-option"></a><span data-ttu-id="2f75c-102">查看或配置 backup compression default 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="2f75c-102">View or Configure the backup compression default Server Configuration Option</span></span>
  <span data-ttu-id="2f75c-103">本主题说明如何使用 **或** 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中查看或配置 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] backup compression default [!INCLUDE[tsql](../../includes/tsql-md.md)]服务器配置选项。</span><span class="sxs-lookup"><span data-stu-id="2f75c-103">This topic describes how to view or configure the **backup compression default** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="2f75c-104">**backup compression default** 选项确定默认情况下服务器实例是否创建压缩的备份。</span><span class="sxs-lookup"><span data-stu-id="2f75c-104">The **backup compression default** option determines whether the server instance creates compressed backups by default.</span></span> <span data-ttu-id="2f75c-105">当安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时， **backup compression default** 选项关闭。</span><span class="sxs-lookup"><span data-stu-id="2f75c-105">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed, the **backup compression default** option is off.</span></span>  
  
 <span data-ttu-id="2f75c-106">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="2f75c-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2f75c-107">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="2f75c-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2f75c-108">限制和局限</span><span class="sxs-lookup"><span data-stu-id="2f75c-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="2f75c-109">建议</span><span class="sxs-lookup"><span data-stu-id="2f75c-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="2f75c-110">安全性</span><span class="sxs-lookup"><span data-stu-id="2f75c-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2f75c-111">**查看或配置 backup compression default 选项，使用：**</span><span class="sxs-lookup"><span data-stu-id="2f75c-111">**To view or configure the backup compression default option, using:**</span></span>  
  
     [<span data-ttu-id="2f75c-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2f75c-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2f75c-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2f75c-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="2f75c-114">**跟进：** [在配置 backup compression default 选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="2f75c-114">**Follow Up:**  [After you configure the backup compression default option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2f75c-115">开始之前</span><span class="sxs-lookup"><span data-stu-id="2f75c-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="2f75c-116">限制和局限</span><span class="sxs-lookup"><span data-stu-id="2f75c-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="2f75c-117">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的所有版本中不提供备份压缩功能。</span><span class="sxs-lookup"><span data-stu-id="2f75c-117">Backup compression is not available in all editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2f75c-118">有关详细信息，请参阅 [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="2f75c-118">For more information, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="2f75c-119">默认情况下，压缩会显著增加 CPU 的使用，并且压缩进程所消耗的额外 CPU 可能会对并发操作产生不利影响。</span><span class="sxs-lookup"><span data-stu-id="2f75c-119">By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely impact concurrent operations.</span></span> <span data-ttu-id="2f75c-120">因此，你可能需要在会话中创建低优先级的压缩备份，其 CPU 使用率受 [资源调控器](../../relational-databases/resource-governor/resource-governor.md)限制。</span><span class="sxs-lookup"><span data-stu-id="2f75c-120">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by [Resource Governor](../../relational-databases/resource-governor/resource-governor.md).</span></span> <span data-ttu-id="2f75c-121">有关详细信息，请参阅本主题后面的 [使用资源调控器限制备份压缩的 CPU 使用量 (Transact-SQL)](../../relational-databases/backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)限制。</span><span class="sxs-lookup"><span data-stu-id="2f75c-121">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="2f75c-122">建议</span><span class="sxs-lookup"><span data-stu-id="2f75c-122">Recommendations</span></span>  
  
-   <span data-ttu-id="2f75c-123">创建单个备份、配置日志传送配置或创建维护计划时，可以覆盖服务器级默认设置。</span><span class="sxs-lookup"><span data-stu-id="2f75c-123">When you are creating an individual backup, configuring a log shipping configuration, or creating a maintenance plan, you can override the server-level default.</span></span>  
  
-   <span data-ttu-id="2f75c-124">磁盘备份设备和磁带备份设备都支持备份压缩。</span><span class="sxs-lookup"><span data-stu-id="2f75c-124">Backup compression is supported for both disk backup devices and tape backup devices.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2f75c-125">Security</span><span class="sxs-lookup"><span data-stu-id="2f75c-125">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2f75c-126">权限</span><span class="sxs-lookup"><span data-stu-id="2f75c-126">Permissions</span></span>  
 <span data-ttu-id="2f75c-127">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="2f75c-127">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="2f75c-128">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="2f75c-128">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="2f75c-129">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="2f75c-129">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2f75c-130">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2f75c-130">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-configure-the-backup-compression-default-option"></a><span data-ttu-id="2f75c-131">查看或配置备份压缩默认值选项</span><span class="sxs-lookup"><span data-stu-id="2f75c-131">To view or configure the backup compression default option</span></span>  
  
1.  <span data-ttu-id="2f75c-132">在对象资源管理器中，右键单击服务器并选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="2f75c-132">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="2f75c-133">单击 **“数据库设置”** 节点。</span><span class="sxs-lookup"><span data-stu-id="2f75c-133">Click the **Database settings** node.</span></span>  
  
3.  <span data-ttu-id="2f75c-134">在“备份和还原” 下，“压缩备份”  显示了 **backup compression default** 选项的当前设置。</span><span class="sxs-lookup"><span data-stu-id="2f75c-134">Under **Backup and restore**, **Compress backup** shows the current setting of the **backup compression default** option.</span></span> <span data-ttu-id="2f75c-135">该设置确定压缩备份的服务器级默认设置，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2f75c-135">This setting determines the server-level default for compressing backups, as follows:</span></span>  
  
    -   <span data-ttu-id="2f75c-136">如果未选中 **“压缩备份”** 框，在默认情况下将不压缩新备份。</span><span class="sxs-lookup"><span data-stu-id="2f75c-136">If the **Compress backup** box is blank, new backups are uncompressed by default.</span></span>  
  
    -   <span data-ttu-id="2f75c-137">如果 **“压缩备份”** 框已选中，则默认情况下将压缩新备份。</span><span class="sxs-lookup"><span data-stu-id="2f75c-137">If the **Compress backup** box is checked, new backups are compressed by default.</span></span>  
  
     <span data-ttu-id="2f75c-138">如果你是 **sysadmin** 或 **serveradmin** 固定服务器角色的成员，还可以通过单击“压缩备份”  框来更改默认设置。</span><span class="sxs-lookup"><span data-stu-id="2f75c-138">If you are a member of the **sysadmin** or **serveradmin** fixed server role, you can also change the default setting by clicking the **Compress backup** box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2f75c-139">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2f75c-139">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-backup-compression-default-option"></a><span data-ttu-id="2f75c-140">查看 backup compression default 选项</span><span class="sxs-lookup"><span data-stu-id="2f75c-140">To view the backup compression default option</span></span>  
  
1.  <span data-ttu-id="2f75c-141">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2f75c-141">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2f75c-142">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="2f75c-142">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2f75c-143">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="2f75c-143">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="2f75c-144">此示例查询 [sys.configurations](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) 目录视图以确定 `backup compression default`的值。</span><span class="sxs-lookup"><span data-stu-id="2f75c-144">This example queries the [sys.configurations](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) catalog view to determine the value for `backup compression default`.</span></span> <span data-ttu-id="2f75c-145">值为 0 表示禁用备份压缩功能，值为 1 表示启用备份压缩功能。</span><span class="sxs-lookup"><span data-stu-id="2f75c-145">A value of 0 means that backup compression is off, and a value of 1 means that backup compression is enabled.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
SELECT value   
FROM sys.configurations   
WHERE name = 'backup compression default' ;  
GO  
  
```  
  
#### <a name="to-configure-the-backup-compression-default-option"></a><span data-ttu-id="2f75c-146">配置 backup compression default 选项</span><span class="sxs-lookup"><span data-stu-id="2f75c-146">To configure the backup compression default option</span></span>  
  
1.  <span data-ttu-id="2f75c-147">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2f75c-147">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2f75c-148">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="2f75c-148">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2f75c-149">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="2f75c-149">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="2f75c-150">此示例说明了如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将服务器实例配置为在默认情况下创建压缩备份。</span><span class="sxs-lookup"><span data-stu-id="2f75c-150">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the server instance to create compressed backups by default.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_configure 'backup compression default', 1 ;  
RECONFIGURE WITH OVERRIDE ;  
GO  
  
```  
  
 <span data-ttu-id="2f75c-151">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="2f75c-151">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-backup-compression-default-option"></a><a name="FollowUp"></a> <span data-ttu-id="2f75c-152">跟进：在配置 backup compression default 选项之后</span><span class="sxs-lookup"><span data-stu-id="2f75c-152">Follow Up: After you configure the backup compression default option</span></span>  
 <span data-ttu-id="2f75c-153">该设置将立即生效，无需重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="2f75c-153">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f75c-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2f75c-154">See Also</span></span>  
 <span data-ttu-id="2f75c-155">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2f75c-155">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="2f75c-156">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2f75c-156">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="2f75c-157">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2f75c-157">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="2f75c-158">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2f75c-158">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="2f75c-159">备份概述 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2f75c-159">Backup Overview &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/backup-overview-sql-server.md)  
  
  
