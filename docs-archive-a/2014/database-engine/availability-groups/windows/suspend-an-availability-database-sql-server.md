---
title: 挂起可用性数据库 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.suspenddatamove.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- primary databases [SQL Server], in availability group
- Availability Groups [SQL Server], suspending a database
- Availability Groups [SQL Server], databases
ms.assetid: 86858982-6af1-4e80-9a93-87451f0d7ee9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 49afe868a509f84160fc1ad154135e8e67f6900a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693482"
---
# <a name="suspend-an-availability-database-sql-server"></a><span data-ttu-id="1e7a8-102">挂起可用性数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1e7a8-102">Suspend an Availability Database (SQL Server)</span></span>
  <span data-ttu-id="1e7a8-103">您可以通过使用 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中的 PowerShell，在 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中挂起可用性数据库。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-103">You can suspend an availability database in [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="1e7a8-104">请注意，挂起命令需要对承载要挂起或恢复的数据库的服务器实例发出。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-104">Note that a suspend command needs to be issued on the server instance that hosts the database to be suspended or resumed.</span></span>  
  
 <span data-ttu-id="1e7a8-105">挂起命令的效果取决于您挂起的是辅助数据库还是主数据库，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1e7a8-105">The effect of a suspend command depends on whether you suspend a secondary database or a primary database, as follows:</span></span>  
  
|<span data-ttu-id="1e7a8-106">挂起的数据库</span><span class="sxs-lookup"><span data-stu-id="1e7a8-106">Suspended Database</span></span>|<span data-ttu-id="1e7a8-107">挂起命令的效果</span><span class="sxs-lookup"><span data-stu-id="1e7a8-107">Effect of Suspend Command</span></span>|  
|------------------------|-------------------------------|  
|<span data-ttu-id="1e7a8-108">辅助数据库</span><span class="sxs-lookup"><span data-stu-id="1e7a8-108">Secondary database</span></span>|<span data-ttu-id="1e7a8-109">仅挂起本地辅助数据库，并且其同步状态变为 NOT SYNCHRONIZING。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-109">Only the local secondary database is suspended and its synchronization state becomes NOT SYNCHRONIZING.</span></span> <span data-ttu-id="1e7a8-110">其他辅助数据库不受影响。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-110">Other secondary databases are not affected.</span></span> <span data-ttu-id="1e7a8-111">挂起的数据库将停止接收和应用数据（日志记录），并且开始落在主数据库的后面。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-111">The suspended database stops receiving and applying data (log records) and begins to fall behind the primary database.</span></span> <span data-ttu-id="1e7a8-112">可读辅助副本上的现有连接会保持可用状态。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-112">Existing connections on the readable secondary remain usable.</span></span> <span data-ttu-id="1e7a8-113">可读辅助副本上挂起数据库的新连接在数据移动恢复之前一直处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-113">New connections to the suspended database on the readable secondary are not allowed until data movement is resumed.</span></span><br /><br /> <span data-ttu-id="1e7a8-114">主数据库仍然可用。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-114">The primary database remains available.</span></span> <span data-ttu-id="1e7a8-115">如果您挂起相应的每个辅助数据库，则主数据库将公开运行。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-115">If you suspend each of the corresponding secondary databases, the primary database runs exposed.</span></span><br /><br /> <span data-ttu-id="1e7a8-116">**\*\* 重要提示 \*\*** 当挂起辅助数据库时，对应主数据库的发送队列将累积未发送的事务日志记录。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-116">**\*\* Important \*\*** While a secondary database is suspended, the send queue of the corresponding primary database will accumulate unsent transaction log records.</span></span> <span data-ttu-id="1e7a8-117">与辅助副本的连接将返回在数据移动挂起时可用的数据。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-117">Connections to the secondary replica return data that was available at the time the data movement was suspended.</span></span>|  
|<span data-ttu-id="1e7a8-118">主数据库</span><span class="sxs-lookup"><span data-stu-id="1e7a8-118">Primary database</span></span>|<span data-ttu-id="1e7a8-119">主数据库将停止数据移动到每个连接的辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-119">The primary database stops data movement to every connected secondary database.</span></span> <span data-ttu-id="1e7a8-120">主数据库将继续在公开模式下运行。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-120">The primary database continues running, in an exposed mode.</span></span> <span data-ttu-id="1e7a8-121">主数据库仍然保持对客户端可用，可读取辅助数据库上的现有连接保持可用并且可以建立新连接。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-121">The primary database remains available to clients, and existing connections on a readable secondary remain usable and new connections can be made.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="1e7a8-122">挂起 AlwaysOn 辅助数据库并不直接影响主数据库的可用性。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-122">Suspending an AlwaysOn secondary database does not directly affect the availability of the primary database.</span></span> <span data-ttu-id="1e7a8-123">但是，挂起辅助数据库可能会影响主数据库的冗余和故障转移功能。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-123">However, suspending a secondary database can impact redundancy and failover capabilities for the primary database.</span></span> <span data-ttu-id="1e7a8-124">这与数据库镜像相反，在数据库镜像中，镜像状态在镜像数据库和主数据库上都挂起。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-124">This is in contrast to database mirroring, where the mirroring state is suspended on both the mirror database and the principal database.</span></span> <span data-ttu-id="1e7a8-125">挂起 AlwaysOn 主数据库将挂起所有相应辅助数据库上的数据移动，并且在恢复主数据库前针对该数据库的冗余和故障转移功能将停止。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-125">Suspending an AlwaysOn primary database suspends data movement on all the corresponding secondary databases, and redundancy and failover capabilities cease for that database until the primary database is resumed.</span></span>  
  
-   <span data-ttu-id="1e7a8-126">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="1e7a8-126">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1e7a8-127">限制和局限</span><span class="sxs-lookup"><span data-stu-id="1e7a8-127">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="1e7a8-128">先决条件</span><span class="sxs-lookup"><span data-stu-id="1e7a8-128">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="1e7a8-129">建议</span><span class="sxs-lookup"><span data-stu-id="1e7a8-129">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="1e7a8-130">安全性</span><span class="sxs-lookup"><span data-stu-id="1e7a8-130">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1e7a8-131">**挂起数据库，使用：**</span><span class="sxs-lookup"><span data-stu-id="1e7a8-131">**To suspend a database, using:**</span></span>  
  
-   [<span data-ttu-id="1e7a8-132">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1e7a8-132">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1e7a8-133">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1e7a8-133">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="1e7a8-134">PowerShell</span><span class="sxs-lookup"><span data-stu-id="1e7a8-134">PowerShell</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="1e7a8-135">**跟进：** [避免出现已满事务日志](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="1e7a8-135">**Follow up:** [Avoiding a Full Transaction Log](#FollowUp)</span></span>  
  
-   [<span data-ttu-id="1e7a8-136">相关任务</span><span class="sxs-lookup"><span data-stu-id="1e7a8-136">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1e7a8-137">开始之前</span><span class="sxs-lookup"><span data-stu-id="1e7a8-137">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1e7a8-138">限制和局限</span><span class="sxs-lookup"><span data-stu-id="1e7a8-138">Limitations and Restrictions</span></span>  
 <span data-ttu-id="1e7a8-139">SUSPEND 命令只要被承载目标数据库的副本接受后就返回，但是实际上挂起数据库以异步方式发生。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-139">A SUSPEND command returns as soon as it has been accepted by the replica that hosts the target database, but actually suspending the database occurs asynchronously.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="1e7a8-140">先决条件</span><span class="sxs-lookup"><span data-stu-id="1e7a8-140">Prerequisites</span></span>  
 <span data-ttu-id="1e7a8-141">您必须连接到承载要挂起的数据库的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-141">You must be connected to the server instance that hosts the database that you want to suspend.</span></span> <span data-ttu-id="1e7a8-142">若要挂起主数据库和相应的辅助数据库，请连接到承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-142">To suspend a primary database and the corresponding secondary databases, connect to the server instance that hosts the primary replica.</span></span> <span data-ttu-id="1e7a8-143">若要挂起辅助数据库但保持主数据库可用，请连接到辅助副本。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-143">To suspend a secondary database while leaving the primary database available, connect to the secondary replica.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="1e7a8-144">建议</span><span class="sxs-lookup"><span data-stu-id="1e7a8-144">Recommendations</span></span>  
 <span data-ttu-id="1e7a8-145">出现瓶颈时，短暂挂起一个或多个辅助数据库可能有助于暂时提高主副本的性能。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-145">During bottlenecks, suspending one or more secondary databases briefly might be useful to improve performance temporarily on the primary replica.</span></span> <span data-ttu-id="1e7a8-146">只要有一个辅助数据库仍挂起，就无法截断相应的主数据库的事务日志。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-146">As long as a secondary database remains suspended, the transaction log of the corresponding primary database cannot be truncated.</span></span> <span data-ttu-id="1e7a8-147">这将导致日志记录在主数据库上累积。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-147">This causes log records to accumulate on the primary database.</span></span> <span data-ttu-id="1e7a8-148">因此，我们建议您快速恢复或删除挂起的辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-148">Therefore, we recommend that you resume, or remove, a suspended secondary database quickly.</span></span> <span data-ttu-id="1e7a8-149">有关详细信息，请参阅本主题后面部分的[跟进：避免出现已满事务日志](#FollowUp)。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-149">For more information, see [Follow up: Avoiding a Full Transaction Log](#FollowUp), later in this topic.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1e7a8-150">Security</span><span class="sxs-lookup"><span data-stu-id="1e7a8-150">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1e7a8-151">权限</span><span class="sxs-lookup"><span data-stu-id="1e7a8-151">Permissions</span></span>  
 <span data-ttu-id="1e7a8-152">需要对数据库拥有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-152">Requires ALTER permission on the database.</span></span>  
  
 <span data-ttu-id="1e7a8-153">对可用性组要求 ALTER AVAILABILITY GROUP 权限、CONTROL AVAILABILITY GROUP 权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-153">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1e7a8-154">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1e7a8-154">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="1e7a8-155">**挂起数据库**</span><span class="sxs-lookup"><span data-stu-id="1e7a8-155">**To suspend a database**</span></span>  
  
1.  <span data-ttu-id="1e7a8-156">在对象资源管理器中，连接到承载要挂起的数据库所在的可用性副本的服务器实例，然后展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-156">In Object Explorer, connect to the server instance that hosts the availability replica on which you want to suspend a database, and expand the server tree.</span></span> <span data-ttu-id="1e7a8-157">有关详细信息，请参阅本主题前面的 [先决条件](#Prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-157">For more information, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>  
  
2.  <span data-ttu-id="1e7a8-158">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-158">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="1e7a8-159">展开该可用性组。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-159">Expand the availability group.</span></span>  
  
4.  <span data-ttu-id="1e7a8-160">展开“可用性数据库”节点，右键单击该数据库，然后单击“挂起数据移动”。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-160">Expand the **Availability Databases** node, right-click the database, and click **Suspend Data Movement**.</span></span>  
  
5.  <span data-ttu-id="1e7a8-161">在 **“挂起数据移动”** 对话框中，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-161">In the **Suspend Data Movement** dialog box, click **OK**.</span></span>  
  
     <span data-ttu-id="1e7a8-162">对象资源管理器通过更改数据库图标以显示一个暂停指示符，来指示已挂起该数据库。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-162">Object Explorer indicates that the database is suspended by changing  the database icon to display a pause indicator.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1e7a8-163">若要挂起此副本位置上的其他数据库，请对每个数据库重复执行步骤 4 和 5。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-163">To suspend additional databases on this replica location, repeat steps 4 and 5  for each database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1e7a8-164">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1e7a8-164">Using Transact-SQL</span></span>  
 <span data-ttu-id="1e7a8-165">**挂起数据库**</span><span class="sxs-lookup"><span data-stu-id="1e7a8-165">**To suspend a database**</span></span>  
  
1.  <span data-ttu-id="1e7a8-166">连接到承载要挂起数据库的副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-166">Connect to the server instance that hosts the replica whose database you want to suspend.</span></span> <span data-ttu-id="1e7a8-167">有关详细信息，请参阅本主题前面的 [先决条件](#Prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-167">For more information, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>  
  
2.  <span data-ttu-id="1e7a8-168">通过使用以下 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr)语句，挂起数据库：</span><span class="sxs-lookup"><span data-stu-id="1e7a8-168">Suspend the database by using the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr)statement:</span></span>  
  
     <span data-ttu-id="1e7a8-169">更改数据库*database_name*设置 HADR 挂起</span><span class="sxs-lookup"><span data-stu-id="1e7a8-169">ALTER DATABASE *database_name* SET HADR SUSPEND</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="1e7a8-170">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1e7a8-170">Using PowerShell</span></span>  
 <span data-ttu-id="1e7a8-171">**挂起数据库**</span><span class="sxs-lookup"><span data-stu-id="1e7a8-171">**To suspend a database**</span></span>  
  
1.  <span data-ttu-id="1e7a8-172">将目录 (`cd`) 改为承载要挂起数据库的副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-172">Change directory (`cd`) to the server instance that hosts the replica whose database you want to suspend.</span></span> <span data-ttu-id="1e7a8-173">有关详细信息，请参阅本主题前面的 [先决条件](#Prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-173">For more information, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>  
  
2.  <span data-ttu-id="1e7a8-174">使用 `Suspend-SqlAvailabilityDatabase` cmdlet 挂起可用性组。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-174">Use the `Suspend-SqlAvailabilityDatabase` cmdlet to suspend the availability group.</span></span>  
  
     <span data-ttu-id="1e7a8-175">例如，以下命令为可用性数据库 `MyDb3` （位于 `MyAg` 服务器实例上的可用性组 `Computer\Instance`中）暂停数据同步。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-175">For example, the following command suspends data synchronization for the availability database `MyDb3` in the availability group `MyAg` on the server instance named `Computer\Instance`.</span></span>  
  
    ```powershell
    Suspend-SqlAvailabilityDatabase -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\Databases\MyDb3  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="1e7a8-176">若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-176">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="1e7a8-177">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-177">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="1e7a8-178">**设置和使用 SQL Server PowerShell 提供程序**</span><span class="sxs-lookup"><span data-stu-id="1e7a8-178">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="1e7a8-179">SQL Server PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="1e7a8-179">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-avoiding-a-full-transaction-log"></a><a name="FollowUp"></a> <span data-ttu-id="1e7a8-180">跟进：避免出现已满事务日志</span><span class="sxs-lookup"><span data-stu-id="1e7a8-180">Follow Up: Avoiding a Full Transaction Log</span></span>  
 <span data-ttu-id="1e7a8-181">通常，在数据库上执行自动检查点操作时，事务日志将在下一个日志备份后截断到该检查点。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-181">Normally, when an automatic checkpoint is performed on a database, its transaction log is truncated to that checkpoint after the next log backup.</span></span> <span data-ttu-id="1e7a8-182">但是，当挂起辅助数据库时，当前的所有日志记录在主数据库上都保持活动状态。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-182">However, while a secondary database is suspended, all of the current log records remain active on the primary database.</span></span> <span data-ttu-id="1e7a8-183">如果填满该事务日志（因为它达到其最大大小或服务器实例耗尽空间），则数据库将无法再执行任何更新。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-183">If the transaction log fills up (either because it reaches its maximum size or the server instance runs out of space), the database cannot perform any more updates.</span></span>  
  
 <span data-ttu-id="1e7a8-184">若要避免此问题，应执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="1e7a8-184">To avoid this problem, you should do one of the following:</span></span>  
  
-   <span data-ttu-id="1e7a8-185">为主数据库添加更多日志空间。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-185">Add more log space for the primary database.</span></span>  
  
-   <span data-ttu-id="1e7a8-186">在日志填满之前恢复辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-186">Resume the secondary database before the log fills up.</span></span> <span data-ttu-id="1e7a8-187">有关详细信息，请参阅本主题后面的 [恢复可用性数据库 (SQL Server)](resume-an-availability-database-sql-server.md)中挂起可用性数据库。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-187">For more information, see [Resume an Availability Database &#40;SQL Server&#41;](resume-an-availability-database-sql-server.md).</span></span>  
  
-   <span data-ttu-id="1e7a8-188">删除辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-188">Remove the secondary database.</span></span> <span data-ttu-id="1e7a8-189">有关详细信息，请参阅[从可用性组中删除辅助数据库 (SQL Server)](remove-a-secondary-database-from-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1e7a8-189">For more information, see [Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md).</span></span>  
  
 <span data-ttu-id="1e7a8-190">**解决事务日志已满的问题**</span><span class="sxs-lookup"><span data-stu-id="1e7a8-190">**To troubleshoot a full transaction log**</span></span>  
  
-   [<span data-ttu-id="1e7a8-191">解决事务日志已满的问题（SQL Server 错误 9002）</span><span class="sxs-lookup"><span data-stu-id="1e7a8-191">Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;</span></span>](../../../relational-databases/logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="1e7a8-192">相关任务</span><span class="sxs-lookup"><span data-stu-id="1e7a8-192">Related Tasks</span></span>  
  
-   [<span data-ttu-id="1e7a8-193">恢复可用性数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1e7a8-193">Resume an Availability Database &#40;SQL Server&#41;</span></span>](resume-an-availability-database-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="1e7a8-194">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1e7a8-194">See Also</span></span>  
 <span data-ttu-id="1e7a8-195">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1e7a8-195">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="1e7a8-196">恢复可用性数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1e7a8-196">Resume an Availability Database &#40;SQL Server&#41;</span></span>](resume-an-availability-database-sql-server.md)  
