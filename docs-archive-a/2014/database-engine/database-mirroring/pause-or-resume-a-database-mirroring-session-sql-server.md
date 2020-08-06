---
title: 暂停或恢复数据库镜像会话 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- resuming database mirroring
- database mirroring [SQL Server], sessions
- database mirroring [SQL Server], pausing
- database mirroring [SQL Server], resuming
- pausing database mirroring
ms.assetid: 05ede3b4-6abe-4442-abb7-9f5aee1d6bc0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b8a9e30bed3ff268fcfdc6e352ad15ebedfe4e8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690131"
---
# <a name="pause-or-resume-a-database-mirroring-session-sql-server"></a><span data-ttu-id="2dbb2-102">暂停或恢复数据库镜像会话 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2dbb2-102">Pause or Resume a Database Mirroring Session (SQL Server)</span></span>
  <span data-ttu-id="2dbb2-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中暂停或恢复数据库镜像。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-103">This topic describes how to pause or resume database mirroring in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="2dbb2-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="2dbb2-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2dbb2-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="2dbb2-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2dbb2-106">安全性</span><span class="sxs-lookup"><span data-stu-id="2dbb2-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2dbb2-107">**若要替换此文本，请使用：**</span><span class="sxs-lookup"><span data-stu-id="2dbb2-107">**To ReplaceThisText, using:**</span></span>  
  
     [<span data-ttu-id="2dbb2-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2dbb2-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2dbb2-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2dbb2-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="2dbb2-110">**跟进：**  [暂停或恢复数据库镜像之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="2dbb2-110">**Follow Up:**  [After Pausing or Resuming Database Mirroring](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2dbb2-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="2dbb2-111">Before You Begin</span></span>  
 <span data-ttu-id="2dbb2-112">您可以随时挂起数据库镜像会话，这可能提高瓶颈期间的性能，之后您可以随时恢复挂起的会话。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-112">At any time, you can suspend a database mirroring session, which might improve performance during bottlenecks, and you can resume a suspended session at any time.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="2dbb2-113">在强制服务后，当原始的主体服务器重新连接时，镜像将挂起。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-113">After a forced service, when the original principal server reconnects, mirroring is suspended.</span></span> <span data-ttu-id="2dbb2-114">在这种情况下，恢复镜像可能会导致原始主体服务器上的数据丢失。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-114">Resuming mirroring in this situation could possibly cause data loss on the original principal server.</span></span> <span data-ttu-id="2dbb2-115">有关管理潜在的数据丢失的信息，请参阅[数据库镜像会话期间的角色切换 (SQL Server)](role-switching-during-a-database-mirroring-session-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-115">For information about managing the potential data loss, see [Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2dbb2-116">Security</span><span class="sxs-lookup"><span data-stu-id="2dbb2-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2dbb2-117">权限</span><span class="sxs-lookup"><span data-stu-id="2dbb2-117">Permissions</span></span>  
 <span data-ttu-id="2dbb2-118">需要对数据库拥有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-118">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2dbb2-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2dbb2-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="2dbb2-120">若要暂停或恢复数据库镜像会话，请使用 **“数据库属性镜像”** 页。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-120">To pause or resume a database mirroring session use the **Database Properties Mirroring** page.</span></span>  
  
#### <a name="to-pause-or-resume-database-mirroring"></a><span data-ttu-id="2dbb2-121">暂停或恢复数据库镜像</span><span class="sxs-lookup"><span data-stu-id="2dbb2-121">To pause or resume database mirroring</span></span>  
  
1.  <span data-ttu-id="2dbb2-122">在数据库镜像会话期间，连接到主体服务器实例，然后在对象资源管理器中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-122">During a database mirroring session, connect to the principal server instance, in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="2dbb2-123">展开 **“数据库”** 并选择数据库。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-123">Expand **Databases**, and select the database.</span></span>  
  
3.  <span data-ttu-id="2dbb2-124">右键单击数据库，选择 **“任务”** ，再单击 **“镜像”** 。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-124">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="2dbb2-125">这样便可打开 **“数据库属性”** 对话框的 **“镜像”** 页。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-125">This opens the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="2dbb2-126">若要暂停会话，请单击 **“暂停”**。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-126">To pause the session, click **Pause**.</span></span>  
  
     <span data-ttu-id="2dbb2-127">此时，将显示一个提示，要求您确认；如果单击 **“是”** ，则会话将暂停，并且该按钮改为 **“恢复”** 。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-127">A prompt asks for confirmation; if you click **Yes**, the session is paused, and the button changes to **Resume**.</span></span>  
  
     <span data-ttu-id="2dbb2-128">有关暂停会话的影响的详细信息，请参阅[暂停和恢复数据库镜像 (SQL Server)](database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-128">For more information about the impact of pausing a session, see [Pausing and Resuming Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
5.  <span data-ttu-id="2dbb2-129">若要恢复会话，请单击 **“恢复”** 。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-129">To resume the session, click **Resume**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2dbb2-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2dbb2-130">Using Transact-SQL</span></span>  
  
#### <a name="to-pause-database-mirroring"></a><span data-ttu-id="2dbb2-131">暂停数据库镜像</span><span class="sxs-lookup"><span data-stu-id="2dbb2-131">To pause database mirroring</span></span>  
  
1.  <span data-ttu-id="2dbb2-132">为任一伙伴连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-132">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] for either partner.</span></span>  
  
2.  <span data-ttu-id="2dbb2-133">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-133">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2dbb2-134">发出以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="2dbb2-134">Issue the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
     <span data-ttu-id="2dbb2-135">ALTER DATABASE *database_name* SET PARTNER SUSPEND</span><span class="sxs-lookup"><span data-stu-id="2dbb2-135">ALTER DATABASE *database_name* SET PARTNER SUSPEND</span></span>  
  
     <span data-ttu-id="2dbb2-136">其中 *database_name* 是要挂起其会话的镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-136">where *database_name* is the mirrored database whose session you want to you want to suspend.</span></span>  
  
     <span data-ttu-id="2dbb2-137">下面的示例暂停 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-137">The following example pauses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET PARTNER SUSPEND;  
    ```  
  
##### <a name="to-resume-database-mirroring"></a><span data-ttu-id="2dbb2-138">恢复数据库镜像</span><span class="sxs-lookup"><span data-stu-id="2dbb2-138">To resume database mirroring</span></span>  
  
1.  <span data-ttu-id="2dbb2-139">为任一伙伴连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-139">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] for either partner.</span></span>  
  
2.  <span data-ttu-id="2dbb2-140">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-140">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2dbb2-141">发出以下 Transact-SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="2dbb2-141">Issue the following Transact-SQL statement:</span></span>  
  
     <span data-ttu-id="2dbb2-142">ALTER DATABASE *database_name* SET PARTNER RESUME</span><span class="sxs-lookup"><span data-stu-id="2dbb2-142">ALTER DATABASE *database_name* SET PARTNER RESUME</span></span>  
  
     <span data-ttu-id="2dbb2-143">其中 *database_name* 是要恢复其会话的镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-143">where *database_name* is the mirrored database whose session you want to resume.</span></span>  
  
     <span data-ttu-id="2dbb2-144">下面的示例暂停 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-144">The following example pauses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET PARTNER RESUME;  
    ```  
  
##  <a name="follow-up-after-pausing-or-resuming-database-mirroring"></a><a name="FollowUp"></a> <span data-ttu-id="2dbb2-145">跟进：暂停或恢复数据库镜像之后</span><span class="sxs-lookup"><span data-stu-id="2dbb2-145">Follow Up: After Pausing or Resuming Database Mirroring</span></span>  
  
-   <span data-ttu-id="2dbb2-146">**暂停数据库镜像之后**</span><span class="sxs-lookup"><span data-stu-id="2dbb2-146">**After pausing database mirroring**</span></span>  
  
     <span data-ttu-id="2dbb2-147">在主数据库上采取预防措施以避免填满事务日志。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-147">On the primary database, take precautions to avoid a full transaction log.</span></span> <span data-ttu-id="2dbb2-148">有关详细信息，请参阅 [事务日志 (SQL Server)](../../relational-databases/logs/the-transaction-log-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-148">For more information, see [The Transaction Log &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md).</span></span>  
  
-   <span data-ttu-id="2dbb2-149">**恢复数据库镜像之后**</span><span class="sxs-lookup"><span data-stu-id="2dbb2-149">**After resuming database mirroring**</span></span>  
  
     <span data-ttu-id="2dbb2-150">恢复数据库镜像会将镜像数据库置于 SYNCHRONIZING 状态。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-150">Resuming database mirroring places the mirror database in the SYNCHRONIZING state.</span></span> <span data-ttu-id="2dbb2-151">如果安全级别为 FULL，镜像将达到与主体相同的状态，镜像数据库将进入 SYNCHRONIZED 状态。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-151">If the safety level is FULL, the mirror catches up with the principal and the mirror database enters the SYNCHRONIZED state.</span></span> <span data-ttu-id="2dbb2-152">此时，可以进行故障转移。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-152">At this point, failover becomes possible.</span></span> <span data-ttu-id="2dbb2-153">如果见证服务器存在并且设置为 ON，则可以进行自动故障转移。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-153">If the witness is present and ON, automatic failover is possible.</span></span> <span data-ttu-id="2dbb2-154">在缺少见证服务器的情况下，可以进行手动故障转移。</span><span class="sxs-lookup"><span data-stu-id="2dbb2-154">In the absence of a witness, manual failover is possible.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="2dbb2-155">相关任务</span><span class="sxs-lookup"><span data-stu-id="2dbb2-155">Related Tasks</span></span>  
  
-   [<span data-ttu-id="2dbb2-156">删除数据库镜像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2dbb2-156">Remove Database Mirroring &#40;SQL Server&#41;</span></span>](remove-database-mirroring-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="2dbb2-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2dbb2-157">See Also</span></span>  
 [<span data-ttu-id="2dbb2-158">数据库镜像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2dbb2-158">Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
