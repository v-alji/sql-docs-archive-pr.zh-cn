---
title: 删除日志传送 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], removing
- removing log shipping
- deleting log shipping
ms.assetid: 859373db-c744-4a4b-8479-45163f61e8cb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 14fdc36c66073e89dcc2014aed4319a2ce78a98f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586946"
---
# <a name="remove-log-shipping-sql-server"></a><span data-ttu-id="893a5-102">删除日志传送 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="893a5-102">Remove Log Shipping (SQL Server)</span></span>
  <span data-ttu-id="893a5-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中删除日志传送。</span><span class="sxs-lookup"><span data-stu-id="893a5-103">This topic describes how to remove log shipping in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="893a5-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="893a5-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="893a5-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="893a5-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="893a5-106">安全性</span><span class="sxs-lookup"><span data-stu-id="893a5-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="893a5-107">**若要删除日志传送，请使用：**</span><span class="sxs-lookup"><span data-stu-id="893a5-107">**To remove log shipping, using:**</span></span>  
  
     [<span data-ttu-id="893a5-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="893a5-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="893a5-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="893a5-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="893a5-110">相关任务</span><span class="sxs-lookup"><span data-stu-id="893a5-110">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="893a5-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="893a5-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="893a5-112">Security</span><span class="sxs-lookup"><span data-stu-id="893a5-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="893a5-113">权限</span><span class="sxs-lookup"><span data-stu-id="893a5-113">Permissions</span></span>  
 <span data-ttu-id="893a5-114">日志传送存储过程要求 **sysadmin** 固定服务器角色中的成员身份。</span><span class="sxs-lookup"><span data-stu-id="893a5-114">The log-shipping stored procedures require membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="893a5-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="893a5-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-remove-log-shipping"></a><span data-ttu-id="893a5-116">删除日志传送</span><span class="sxs-lookup"><span data-stu-id="893a5-116">To remove log shipping</span></span>  
  
1.  <span data-ttu-id="893a5-117">连接到当前是日志传送主服务器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例并展开该实例。</span><span class="sxs-lookup"><span data-stu-id="893a5-117">Connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is currently the log shipping primary server and expand that instance.</span></span>  
  
2.  <span data-ttu-id="893a5-118">展开“数据库”，右键单击日志传送主数据库，再单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="893a5-118">Expand **Databases**, right-click the log shipping primary database, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="893a5-119">在 **“选择页”** 下，单击 **“事务日志传送”** 。</span><span class="sxs-lookup"><span data-stu-id="893a5-119">Under **Select a page**, click **Transaction Log Shipping**.</span></span>  
  
4.  <span data-ttu-id="893a5-120">清除 **“将此数据库启用为日志传送配置中的主数据库”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="893a5-120">Clear the **Enable this as a primary database in a log shipping configuration** check box.</span></span>  
  
5.  <span data-ttu-id="893a5-121">单击 **“确定”** ，从此主数据库中删除日志传送。</span><span class="sxs-lookup"><span data-stu-id="893a5-121">Click **OK** to remove log shipping from this primary database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="893a5-122">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="893a5-122">Using Transact-SQL</span></span>  
  
#### <a name="to-remove-log-shipping"></a><span data-ttu-id="893a5-123">删除日志传送</span><span class="sxs-lookup"><span data-stu-id="893a5-123">To Remove Log Shipping</span></span>  
  
1.  <span data-ttu-id="893a5-124">在日志传送主服务器上，执行 [sp_delete_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql) 从主服务器上删除有关辅助数据库的信息。</span><span class="sxs-lookup"><span data-stu-id="893a5-124">On the log shipping primary server, execute [sp_delete_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql) to delete the information about the secondary database from the primary server.</span></span>  
  
2.  <span data-ttu-id="893a5-125">在日志传送辅助服务器上，执行 [sp_delete_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql) 以删除辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="893a5-125">On the log shipping secondary server, execute [sp_delete_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql) to delete the secondary database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="893a5-126">如果不存在具有相同辅助 ID 的其他辅助数据库，则从 **sp_delete_log_shipping_secondary_database** 调用 **sp_delete_log_shipping_secondary_primary** ，以删除该辅助 ID 的项并删除复制和还原作业。</span><span class="sxs-lookup"><span data-stu-id="893a5-126">If there are no other secondary databases with the same secondary ID, **sp_delete_log_shipping_secondary_primary** is invoked from **sp_delete_log_shipping_secondary_database** and deletes the entry for the secondary ID and the copy and restore jobs.</span></span>  
  
3.  <span data-ttu-id="893a5-127">在日志传送主服务器上，执行 **sp_delete_log_shipping_primary_database** 以删除有关主服务器的日志传送配置的信息。</span><span class="sxs-lookup"><span data-stu-id="893a5-127">On the log shipping primary server, execute **sp_delete_log_shipping_primary_database** to delete information about the log shipping configuration from the primary server.</span></span> <span data-ttu-id="893a5-128">此操作还将删除备份作业。</span><span class="sxs-lookup"><span data-stu-id="893a5-128">This also deletes the backup job.</span></span>  
  
4.  <span data-ttu-id="893a5-129">在日志传送主服务器上，禁用备份作业。</span><span class="sxs-lookup"><span data-stu-id="893a5-129">On the log shipping primary server, disable the backup job.</span></span> <span data-ttu-id="893a5-130">有关详细信息，请参阅 [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md)。</span><span class="sxs-lookup"><span data-stu-id="893a5-130">For more information, see [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md).</span></span>  
  
5.  <span data-ttu-id="893a5-131">在日志传送辅助服务器上，禁用复制和还原作业。</span><span class="sxs-lookup"><span data-stu-id="893a5-131">On the log shipping secondary server, disable the copy and restore jobs.</span></span>  
  
6.  <span data-ttu-id="893a5-132">或者，如果您不再使用日志传送辅助数据库，则可以从辅助服务器中删除它。</span><span class="sxs-lookup"><span data-stu-id="893a5-132">Optionally, if you are no longer using the log shipping secondary database, you can delete it from the secondary server.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="893a5-133">相关任务</span><span class="sxs-lookup"><span data-stu-id="893a5-133">Related Tasks</span></span>  
  
-   [<span data-ttu-id="893a5-134">将日志传送升级到 SQL Server 2014 &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="893a5-134">Upgrade Log Shipping to SQL Server 2014 &#40;Transact-SQL&#41;</span></span>](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [<span data-ttu-id="893a5-135">配置日志传送 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="893a5-135">Configure Log Shipping &#40;SQL Server&#41;</span></span>](configure-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="893a5-136">向日志传送配置添加辅助数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="893a5-136">Add a Secondary Database to a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](add-a-secondary-database-to-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="893a5-137">从日志传送配置中删除辅助数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="893a5-137">Remove a Secondary Database from a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="893a5-138">监视日志传送 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="893a5-138">Monitor Log Shipping &#40;Transact-SQL&#41;</span></span>](monitor-log-shipping-transact-sql.md)  
  
-   [<span data-ttu-id="893a5-139">故障转移到日志传送辅助服务器 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="893a5-139">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
-   [<span data-ttu-id="893a5-140">Disable or Enable a Job</span><span class="sxs-lookup"><span data-stu-id="893a5-140">Disable or Enable a Job</span></span>](../../ssms/agent/disable-or-enable-a-job.md)  
  
## <a name="see-also"></a><span data-ttu-id="893a5-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="893a5-141">See Also</span></span>  
 <span data-ttu-id="893a5-142">[关于日志传送 (SQL Server)](about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="893a5-142">[About Log Shipping &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span></span>  
 [<span data-ttu-id="893a5-143">日志传送表和存储过程</span><span class="sxs-lookup"><span data-stu-id="893a5-143">Log Shipping Tables and Stored Procedures</span></span>](log-shipping-tables-and-stored-procedures.md)  
  
  
