---
title: 从日志传送配置中删除辅助数据库 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- deleting secondary databases
- secondary databases [SQL Server], in log shipping
- removing secondary databases
- secondary data files [SQL Server], removing
- log shipping [SQL Server], secondary databases
ms.assetid: ebe368a4-ca1c-45d0-9a71-3ddbd5b26a8e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 119f2762d41d0787b6b3279507e9671e89fddfca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588015"
---
# <a name="remove-a-secondary-database-from-a-log-shipping-configuration-sql-server"></a><span data-ttu-id="cc9c0-102">从日志传送配置中删除辅助数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="cc9c0-102">Remove a Secondary Database from a Log Shipping Configuration (SQL Server)</span></span>
  <span data-ttu-id="cc9c0-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中删除日志传送辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="cc9c0-103">This topic describes how to remove a log shipping secondary database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="cc9c0-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="cc9c0-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="cc9c0-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="cc9c0-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="cc9c0-106">安全性</span><span class="sxs-lookup"><span data-stu-id="cc9c0-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="cc9c0-107">**若要删除日志传送辅助数据库，请使用：**</span><span class="sxs-lookup"><span data-stu-id="cc9c0-107">**To remove a log shipping secondary database, using:**</span></span>  
  
     [<span data-ttu-id="cc9c0-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cc9c0-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="cc9c0-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cc9c0-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="cc9c0-110">相关任务</span><span class="sxs-lookup"><span data-stu-id="cc9c0-110">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cc9c0-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="cc9c0-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cc9c0-112">Security</span><span class="sxs-lookup"><span data-stu-id="cc9c0-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cc9c0-113">权限</span><span class="sxs-lookup"><span data-stu-id="cc9c0-113">Permissions</span></span>  
 <span data-ttu-id="cc9c0-114">日志传送存储过程要求 **sysadmin** 固定服务器角色中的成员身份。</span><span class="sxs-lookup"><span data-stu-id="cc9c0-114">The log-shipping stored procedures require membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cc9c0-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cc9c0-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-remove-a-log-shipping-secondary-database"></a><span data-ttu-id="cc9c0-116">删除日志传送辅助数据库</span><span class="sxs-lookup"><span data-stu-id="cc9c0-116">To remove a log shipping secondary database</span></span>  
  
1.  <span data-ttu-id="cc9c0-117">连接到当前是日志传送主服务器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例并展开该实例。</span><span class="sxs-lookup"><span data-stu-id="cc9c0-117">Connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is currently the log shipping primary server and expand that instance.</span></span>  
  
2.  <span data-ttu-id="cc9c0-118">展开“数据库”，右键单击日志传送主数据库，再单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="cc9c0-118">Expand **Databases**, right-click the log shipping primary database, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="cc9c0-119">在 **“选择页”** 下，单击 **“事务日志传送”** 。</span><span class="sxs-lookup"><span data-stu-id="cc9c0-119">Under **Select a page**, click **Transaction Log Shipping**.</span></span>  
  
4.  <span data-ttu-id="cc9c0-120">在 **“辅助服务器实例和数据库”** 下，单击要删除的数据库。</span><span class="sxs-lookup"><span data-stu-id="cc9c0-120">Under **Secondary server instances and databases**, click the database you want to remove.</span></span>  
  
5.  <span data-ttu-id="cc9c0-121">单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="cc9c0-121">Click **Remove**.</span></span>  
  
6.  <span data-ttu-id="cc9c0-122">单击 **“确定”** 更新配置。</span><span class="sxs-lookup"><span data-stu-id="cc9c0-122">Click **OK** to update the configuration.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cc9c0-123">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cc9c0-123">Using Transact-SQL</span></span>  
  
#### <a name="to-remove-a-secondary-database"></a><span data-ttu-id="cc9c0-124">删除辅助数据库</span><span class="sxs-lookup"><span data-stu-id="cc9c0-124">To Remove a Secondary Database</span></span>  
  
1.  <span data-ttu-id="cc9c0-125">在主服务器上，执行 [sp_delete_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql) 从主服务器上删除有关辅助数据库的信息。</span><span class="sxs-lookup"><span data-stu-id="cc9c0-125">On the primary server, execute [sp_delete_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql) to delete the information about the secondary database from the primary server.</span></span>  
  
2.  <span data-ttu-id="cc9c0-126">在辅助服务器上，执行 [sp_delete_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql) 以删除辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="cc9c0-126">On the secondary server, execute [sp_delete_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql) to delete the secondary database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cc9c0-127">如果不存在具有相同辅助 ID 的其他辅助数据库，则从 **sp_delete_log_shipping_secondary_database** 调用 **sp_delete_log_shipping_secondary_primary** ，以删除该辅助 ID 的项并删除复制和还原作业。</span><span class="sxs-lookup"><span data-stu-id="cc9c0-127">If there are no other secondary databases with the same secondary ID, **sp_delete_log_shipping_secondary_primary** is invoked from **sp_delete_log_shipping_secondary_database** and deletes the entry for the secondary ID and the copy and restore jobs.</span></span>  
  
3.  <span data-ttu-id="cc9c0-128">在辅助服务器上，禁用复制和还原作业。</span><span class="sxs-lookup"><span data-stu-id="cc9c0-128">On the secondary server, disable the copy and restore jobs.</span></span> <span data-ttu-id="cc9c0-129">有关详细信息，请参阅 [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md)。</span><span class="sxs-lookup"><span data-stu-id="cc9c0-129">For more information, see [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="cc9c0-130">相关任务</span><span class="sxs-lookup"><span data-stu-id="cc9c0-130">Related Tasks</span></span>  
  
-   [<span data-ttu-id="cc9c0-131">将日志传送升级到 SQL Server 2014 &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="cc9c0-131">Upgrade Log Shipping to SQL Server 2014 &#40;Transact-SQL&#41;</span></span>](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [<span data-ttu-id="cc9c0-132">配置日志传送 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="cc9c0-132">Configure Log Shipping &#40;SQL Server&#41;</span></span>](configure-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="cc9c0-133">向日志传送配置添加辅助数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="cc9c0-133">Add a Secondary Database to a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](add-a-secondary-database-to-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="cc9c0-134">删除日志传送 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="cc9c0-134">Remove Log Shipping &#40;SQL Server&#41;</span></span>](remove-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="cc9c0-135">查看日志传送报告 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="cc9c0-135">View the Log Shipping Report &#40;SQL Server Management Studio&#41;</span></span>](view-the-log-shipping-report-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="cc9c0-136">监视日志传送 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="cc9c0-136">Monitor Log Shipping &#40;Transact-SQL&#41;</span></span>](monitor-log-shipping-transact-sql.md)  
  
-   [<span data-ttu-id="cc9c0-137">故障转移到日志传送辅助服务器 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="cc9c0-137">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="cc9c0-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cc9c0-138">See Also</span></span>  
 <span data-ttu-id="cc9c0-139">[关于日志传送 (SQL Server)](about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cc9c0-139">[About Log Shipping &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span></span>  
 [<span data-ttu-id="cc9c0-140">日志传送表和存储过程</span><span class="sxs-lookup"><span data-stu-id="cc9c0-140">Log Shipping Tables and Stored Procedures</span></span>](log-shipping-tables-and-stored-procedures.md)  
  
  
