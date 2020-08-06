---
title: 向日志传送配置添加辅助数据库 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- adding secondary databases
- secondary databases [SQL Server], in log shipping
- secondary data files [SQL Server], adding
- log shipping [SQL Server], secondary databases
ms.assetid: b02eba13-f8e6-4684-b7e4-75ea038ea473
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 062df1b53ed74321ba0c75c9df763de79a4802bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586947"
---
# <a name="add-a-secondary-database-to-a-log-shipping-configuration-sql-server"></a><span data-ttu-id="f940d-102">向日志传送配置添加辅助数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f940d-102">Add a Secondary Database to a Log Shipping Configuration (SQL Server)</span></span>
  <span data-ttu-id="f940d-103">此主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中向现有的日志传送配置添加辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="f940d-103">This topic describes how to add a secondary database to an existing log shipping configuration in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="f940d-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="f940d-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f940d-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="f940d-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f940d-106">安全性</span><span class="sxs-lookup"><span data-stu-id="f940d-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f940d-107">**若要添加日志传送辅助数据库，请使用：**</span><span class="sxs-lookup"><span data-stu-id="f940d-107">**To add a log shipping secondary database, using:**</span></span>  
  
     [<span data-ttu-id="f940d-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f940d-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f940d-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f940d-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="f940d-110">相关任务</span><span class="sxs-lookup"><span data-stu-id="f940d-110">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f940d-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="f940d-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f940d-112">Security</span><span class="sxs-lookup"><span data-stu-id="f940d-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f940d-113">权限</span><span class="sxs-lookup"><span data-stu-id="f940d-113">Permissions</span></span>  
 <span data-ttu-id="f940d-114">日志传送存储过程要求 **sysadmin** 固定服务器角色中的成员身份。</span><span class="sxs-lookup"><span data-stu-id="f940d-114">The log-shipping stored procedures require membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f940d-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f940d-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-add-a-log-shipping-secondary-database"></a><span data-ttu-id="f940d-116">添加日志传送辅助数据库</span><span class="sxs-lookup"><span data-stu-id="f940d-116">To add a log shipping secondary database</span></span>  
  
1.  <span data-ttu-id="f940d-117">右键单击要在日志传送配置中用作主数据库的数据库，然后单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="f940d-117">Right-click the database you want to use as your primary database in the log shipping configuration, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="f940d-118">在 **“选择页”** 下，单击 **“事务日志传送”** 。</span><span class="sxs-lookup"><span data-stu-id="f940d-118">Under **Select a page**, click **Transaction Log Shipping**.</span></span>  
  
3.  <span data-ttu-id="f940d-119">在 **“辅助服务器实例和数据库”** 下，单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="f940d-119">Under **Secondary server instances and databases**, click **Add**.</span></span>  
  
4.  <span data-ttu-id="f940d-120">单击 **“连接”** ，连接到要用作辅助服务器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="f940d-120">Click **Connect** and connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to use as your secondary server.</span></span>  
  
5.  <span data-ttu-id="f940d-121">在 **“辅助数据库”** 框中，从列表中选择一个数据库或键入要创建的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="f940d-121">In the **Secondary database** box, choose a database from the list or type the name of the database you want to create.</span></span>  
  
6.  <span data-ttu-id="f940d-122">在 **“初始化辅助数据库”** 选项卡上，选择要用于初始化辅助数据库的选项。</span><span class="sxs-lookup"><span data-stu-id="f940d-122">On the **Initialize Secondary database** tab, choose the option that you want to use to initialize the secondary database.</span></span>  
  
7.  <span data-ttu-id="f940d-123">在 **“复制文件”** 选项卡的 **“复制文件的目标文件夹”** 框中，键入应将事务日志备份复制到的文件夹的路径。</span><span class="sxs-lookup"><span data-stu-id="f940d-123">On the **Copy Files tab**, in the **Destination folder for copied files** box, type the path of the folder into which the transaction logs backups should be copied.</span></span> <span data-ttu-id="f940d-124">该文件夹通常位于辅助服务器上。</span><span class="sxs-lookup"><span data-stu-id="f940d-124">This folder is often located on the secondary server.</span></span>  
  
8.  <span data-ttu-id="f940d-125">请注意 **“复制作业”** 下的 **“计划”** 框中列出的复制计划。</span><span class="sxs-lookup"><span data-stu-id="f940d-125">Note the copy schedule listed in the **Schedule** box under **Copy job**.</span></span> <span data-ttu-id="f940d-126">如果要自定义安装计划，请单击 **“计划”** ，然后根据需要调整 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理计划。</span><span class="sxs-lookup"><span data-stu-id="f940d-126">If you want to customize the schedule for your installation, click **Schedule** and then adjust the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent schedule as needed.</span></span> <span data-ttu-id="f940d-127">此计划应为大致的备份计划。</span><span class="sxs-lookup"><span data-stu-id="f940d-127">This schedule should approximate the backup schedule.</span></span>  
  
9. <span data-ttu-id="f940d-128">在 **“还原”** 选项卡上的 **“还原备份时的数据库状态”** 下，选择 **“无恢复模式”** 或 **“备用模式”** 选项。</span><span class="sxs-lookup"><span data-stu-id="f940d-128">On the **Restore** tab, under **Database state when restoring backups**, choose the **No recovery mode** or **Standby mode** option.</span></span>  
  
10. <span data-ttu-id="f940d-129">如果选择了 **“备用模式”** 选项，请选择是否要在进行还原操作时从辅助数据库断开用户连接。</span><span class="sxs-lookup"><span data-stu-id="f940d-129">If you chose the **Standby mode** option, choose if you want to disconnect users from the secondary database while the restore operation is underway.</span></span>  
  
11. <span data-ttu-id="f940d-130">如果希望延迟辅助服务器上的还原进程，请在 **“延迟还原备份操作至少”** 下选择延迟时间。</span><span class="sxs-lookup"><span data-stu-id="f940d-130">If you want to delay the restore process on the secondary server, choose a delay time under **Delay restoring backups at least**.</span></span>  
  
12. <span data-ttu-id="f940d-131">在 **“在以下时间内没有执行还原时报警”** 下选择警报阈值。</span><span class="sxs-lookup"><span data-stu-id="f940d-131">Choose an alert threshold under **Alert if no restore occurs within**.</span></span>  
  
13. <span data-ttu-id="f940d-132">请注意 **“还原作业”** 下 **“计划”** 框中列出的还原计划。</span><span class="sxs-lookup"><span data-stu-id="f940d-132">Note the restore schedule listed in the **Schedule** box under **Restore job**.</span></span> <span data-ttu-id="f940d-133">如果要自定义安装计划，请单击 **“计划”** ，然后根据需要调整 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理计划。</span><span class="sxs-lookup"><span data-stu-id="f940d-133">If you want to customize the schedule for your installation, click **Schedule** and then adjust the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent schedule as needed.</span></span> <span data-ttu-id="f940d-134">此计划应为大致的备份计划。</span><span class="sxs-lookup"><span data-stu-id="f940d-134">This schedule should approximate the backup schedule.</span></span>  
  
14. <span data-ttu-id="f940d-135">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="f940d-135">Click **OK**.</span></span>  
  
15. <span data-ttu-id="f940d-136">在“数据库属性”对话框上单击 **“确定”** ，以开始配置过程。</span><span class="sxs-lookup"><span data-stu-id="f940d-136">Click **OK** on the Database Properties dialog box to begin the configuration process.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f940d-137">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f940d-137">Using Transact-SQL</span></span>  
  
#### <a name="to-add-a-log-shipping-secondary-database"></a><span data-ttu-id="f940d-138">添加日志传送辅助数据库</span><span class="sxs-lookup"><span data-stu-id="f940d-138">To add a log shipping secondary database</span></span>  
  
1.  <span data-ttu-id="f940d-139">在辅助服务器上，执行 [sp_add_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-primary-transact-sql) ，提供主服务器和数据库的详细信息。</span><span class="sxs-lookup"><span data-stu-id="f940d-139">On the secondary server, execute [sp_add_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-primary-transact-sql) supplying the details of the primary server and database.</span></span> <span data-ttu-id="f940d-140">此存储过程返回辅助 ID 以及复制和还原作业 ID。</span><span class="sxs-lookup"><span data-stu-id="f940d-140">This stored procedure returns the secondary ID and the copy and restore job IDs.</span></span>  
  
2.  <span data-ttu-id="f940d-141">在辅助服务器上，执行 [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) 以设置复制和还原作业的计划。</span><span class="sxs-lookup"><span data-stu-id="f940d-141">On the secondary server, execute [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) to set the schedule for the copy and restore jobs.</span></span>  
  
3.  <span data-ttu-id="f940d-142">在辅助服务器上，执行 [sp_add_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql) 以添加辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="f940d-142">On the secondary server, execute [sp_add_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql) to add a secondary database.</span></span>  
  
4.  <span data-ttu-id="f940d-143">在主服务器上，执行 [sp_add_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-secondary-transact-sql) 向主服务器添加有关新辅助数据库的必需信息。</span><span class="sxs-lookup"><span data-stu-id="f940d-143">On the primary server, execute [sp_add_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-secondary-transact-sql) to add the required information about the new secondary database to the primary server.</span></span>  
  
5.  <span data-ttu-id="f940d-144">在辅助服务器上，启用复制和还原作业。</span><span class="sxs-lookup"><span data-stu-id="f940d-144">On the secondary server, enable the copy and restore jobs.</span></span> <span data-ttu-id="f940d-145">有关详细信息，请参阅 [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md)。</span><span class="sxs-lookup"><span data-stu-id="f940d-145">For more information, see [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f940d-146">相关任务</span><span class="sxs-lookup"><span data-stu-id="f940d-146">Related Tasks</span></span>  
  
-   [<span data-ttu-id="f940d-147">将日志传送升级到 SQL Server 2014 &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="f940d-147">Upgrade Log Shipping to SQL Server 2014 &#40;Transact-SQL&#41;</span></span>](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [<span data-ttu-id="f940d-148">配置日志传送 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f940d-148">Configure Log Shipping &#40;SQL Server&#41;</span></span>](configure-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="f940d-149">从日志传送配置中删除辅助数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f940d-149">Remove a Secondary Database from a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="f940d-150">删除日志传送 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f940d-150">Remove Log Shipping &#40;SQL Server&#41;</span></span>](remove-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="f940d-151">查看日志传送报告 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f940d-151">View the Log Shipping Report &#40;SQL Server Management Studio&#41;</span></span>](view-the-log-shipping-report-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="f940d-152">监视日志传送 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f940d-152">Monitor Log Shipping &#40;Transact-SQL&#41;</span></span>](monitor-log-shipping-transact-sql.md)  
  
-   [<span data-ttu-id="f940d-153">故障转移到日志传送辅助服务器 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f940d-153">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="f940d-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f940d-154">See Also</span></span>  
 <span data-ttu-id="f940d-155">[关于日志传送 (SQL Server)](about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f940d-155">[About Log Shipping &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span></span>  
 [<span data-ttu-id="f940d-156">日志传送表和存储过程</span><span class="sxs-lookup"><span data-stu-id="f940d-156">Log Shipping Tables and Stored Procedures</span></span>](log-shipping-tables-and-stored-procedures.md)  
  
  
