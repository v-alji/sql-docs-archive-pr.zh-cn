---
title: 恢复可用性数据库 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.resumedatamove.f1
helpviewer_keywords:
- Availability Groups [SQL Server], resuming a database
- secondary databases [SQL Server], in availability group
- primary databases [SQL Server], in availability group
- Availability Groups [SQL Server], databases
ms.assetid: 20e9147b-e985-4caa-910e-fc4b38dbf9a1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6a2279940c2502a310e9dac4448bd6029b6e13dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693106"
---
# <a name="resume-an-availability-database-sql-server"></a><span data-ttu-id="b834f-102">恢复可用性数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b834f-102">Resume an Availability Database (SQL Server)</span></span>
  <span data-ttu-id="b834f-103">您可以通过使用 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中的 PowerShell，在 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中恢复已挂起的可用性数据库。</span><span class="sxs-lookup"><span data-stu-id="b834f-103">You can resume a suspended availability database in [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="b834f-104">恢复挂起的数据库会将数据库置于 SYNCHRONIZING 状态。</span><span class="sxs-lookup"><span data-stu-id="b834f-104">Resuming a suspended database puts the database into the SYNCHRONIZING state.</span></span> <span data-ttu-id="b834f-105">恢复主数据库还将恢复挂起主数据库时导致挂起的任何辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="b834f-105">Resuming the primary database also resumes any of its secondary databases that were suspended as the result of suspending the primary database.</span></span> <span data-ttu-id="b834f-106">如果任何辅助数据库是从承载辅助副本的服务器实例中本地挂起的，则该辅助数据库必须进行本地恢复。</span><span class="sxs-lookup"><span data-stu-id="b834f-106">If any secondary database was suspended locally, from the server instance that hosts the secondary replica, that secondary database must be resumed locally.</span></span> <span data-ttu-id="b834f-107">一旦给定的辅助数据库和相应的主数据库处于 SYNCHRONIZING 状态，则在辅助数据库上将恢复数据同步。</span><span class="sxs-lookup"><span data-stu-id="b834f-107">Once a given secondary database and the corresponding primary database are in the SYNCHRONIZING state, data synchronization resumes on the secondary database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b834f-108">暂停和恢复 AlwaysOn 辅助数据库并不直接影响主数据库的可用性。</span><span class="sxs-lookup"><span data-stu-id="b834f-108">Suspending and resuming an AlwaysOn secondary database does not directly affect the availability of the primary database.</span></span> <span data-ttu-id="b834f-109">但是，暂停某一辅助数据库可能会在恢复这个暂停的辅助数据库之前影响主数据库的冗余和故障转移功能。</span><span class="sxs-lookup"><span data-stu-id="b834f-109">However, suspending a secondary database can impact redundancy and failover capabilities for the primary database, until the suspended secondary database is resumed.</span></span> <span data-ttu-id="b834f-110">这与数据库镜像相反，在数据库镜像中，在恢复镜像前镜像状态在镜像数据库和主数据库上都挂起。</span><span class="sxs-lookup"><span data-stu-id="b834f-110">This is in contrast to database mirroring, where the mirroring state is suspended on both the mirror database and the principal database until mirroring is resumed.</span></span> <span data-ttu-id="b834f-111">挂起 AlwaysOn 主数据库将挂起所有相应辅助数据库上的数据移动，并且在恢复主数据库前针对该数据库的冗余和故障转移功能将停止。</span><span class="sxs-lookup"><span data-stu-id="b834f-111">Suspending an AlwaysOn primary database suspends data movement on all the corresponding secondary databases, and redundancy and failover capabilities cease for that database until the primary database is resumed.</span></span>  
  
-   <span data-ttu-id="b834f-112">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="b834f-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b834f-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="b834f-113">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="b834f-114">先决条件</span><span class="sxs-lookup"><span data-stu-id="b834f-114">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="b834f-115">安全性</span><span class="sxs-lookup"><span data-stu-id="b834f-115">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b834f-116">**若要恢复辅助数据库，请使用：**</span><span class="sxs-lookup"><span data-stu-id="b834f-116">**To resume a secondary database, using:**</span></span>  
  
     [<span data-ttu-id="b834f-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b834f-117">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b834f-118">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b834f-118">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="b834f-119">PowerShell</span><span class="sxs-lookup"><span data-stu-id="b834f-119">PowerShell</span></span>](#PowerShellProcedure)  
  
-   [<span data-ttu-id="b834f-120">相关任务</span><span class="sxs-lookup"><span data-stu-id="b834f-120">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b834f-121">开始之前</span><span class="sxs-lookup"><span data-stu-id="b834f-121">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b834f-122">限制和局限</span><span class="sxs-lookup"><span data-stu-id="b834f-122">Limitations and Restrictions</span></span>  
 <span data-ttu-id="b834f-123">RESUME 命令只要被承载目标数据库的副本接受后就返回，但是实际上继续数据库以异步方式发生。</span><span class="sxs-lookup"><span data-stu-id="b834f-123">A RESUME command returns as soon as it has been accepted by the replica that hosts the target database, but actually resuming the database occurs asynchronously.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="b834f-124">先决条件</span><span class="sxs-lookup"><span data-stu-id="b834f-124">Prerequisites</span></span>  
  
-   <span data-ttu-id="b834f-125">您必须连接到承载要恢复的数据库的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="b834f-125">You must be connected to the server instance that hosts the database to be resumed.</span></span>  
  
-   <span data-ttu-id="b834f-126">可用性组必须联机。</span><span class="sxs-lookup"><span data-stu-id="b834f-126">The availability group must be online.</span></span>  
  
-   <span data-ttu-id="b834f-127">主数据库必须处于联机状态且可用。</span><span class="sxs-lookup"><span data-stu-id="b834f-127">The primary database must be online and available.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b834f-128">Security</span><span class="sxs-lookup"><span data-stu-id="b834f-128">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b834f-129">权限</span><span class="sxs-lookup"><span data-stu-id="b834f-129">Permissions</span></span>  
 <span data-ttu-id="b834f-130">需要对数据库拥有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="b834f-130">Requires ALTER permission on the database.</span></span>  
  
 <span data-ttu-id="b834f-131">对可用性组要求 ALTER AVAILABILITY GROUP 权限、CONTROL AVAILABILITY GROUP 权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="b834f-131">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b834f-132">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b834f-132">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="b834f-133">**恢复辅助数据库**</span><span class="sxs-lookup"><span data-stu-id="b834f-133">**To resume a secondary database**</span></span>  
  
1.  <span data-ttu-id="b834f-134">在对象资源管理器中，连接到承载要恢复的数据库所在的可用性副本的服务器实例，然后展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="b834f-134">In Object Explorer, connect to the server instance that hosts the availability replica on which you want to resume a database, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="b834f-135">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="b834f-135">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="b834f-136">展开该可用性组。</span><span class="sxs-lookup"><span data-stu-id="b834f-136">Expand the availability group.</span></span>  
  
4.  <span data-ttu-id="b834f-137">展开“可用性数据库”节点，右键单击该数据库，然后单击“恢复数据移动”。</span><span class="sxs-lookup"><span data-stu-id="b834f-137">Expand the **Availability Databases** node, right-click the database, and click **Resume Data Movement**.</span></span>  
  
5.  <span data-ttu-id="b834f-138">在 **“恢复数据移动”** 对话框中，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="b834f-138">In the **Resume Data Movement** dialog box, click **OK**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b834f-139">若要恢复此副本位置上的其他数据库，请对每个数据库重复执行步骤 4 和 5。</span><span class="sxs-lookup"><span data-stu-id="b834f-139">To resume additional databases on this replica location, repeat steps 4 and 5 for each database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b834f-140">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b834f-140">Using Transact-SQL</span></span>  
 <span data-ttu-id="b834f-141">**恢复本地挂起的辅助数据库**</span><span class="sxs-lookup"><span data-stu-id="b834f-141">**To resume a secondary database that was suspended locally**</span></span>  
  
1.  <span data-ttu-id="b834f-142">连接到承载想要恢复其数据库的辅助副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="b834f-142">Connect to the server instance that hosts the secondary replica whose database you want to resume.</span></span>  
  
2.  <span data-ttu-id="b834f-143">通过使用下面的 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr)语句恢复辅助数据库：</span><span class="sxs-lookup"><span data-stu-id="b834f-143">Resume the secondary database by using the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr)statement:</span></span>  
  
     <span data-ttu-id="b834f-144">更改数据库*database_name*设置 HADR 简历</span><span class="sxs-lookup"><span data-stu-id="b834f-144">ALTER DATABASE *database_name* SET HADR RESUME</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="b834f-145">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b834f-145">Using PowerShell</span></span>  

### <a name="to-resume-a-secondary-database"></a><span data-ttu-id="b834f-146">恢复辅助数据库</span><span class="sxs-lookup"><span data-stu-id="b834f-146">To resume a secondary database</span></span>
  
1.  <span data-ttu-id="b834f-147">将目录 (`cd`) 更改为承载要恢复的数据库所在副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="b834f-147">Change directory (`cd`) to the server instance that hosts the replica whose database you want to resume.</span></span> <span data-ttu-id="b834f-148">有关详细信息，请参阅本主题前面的 [先决条件](#Prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="b834f-148">For more information, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>  
  
2.  <span data-ttu-id="b834f-149">使用 **Resume-SqlAvailabilityDatabase** cmdlet 恢复可用性组。</span><span class="sxs-lookup"><span data-stu-id="b834f-149">Use the **Resume-SqlAvailabilityDatabase** cmdlet to resume the availability group.</span></span>  
  
     <span data-ttu-id="b834f-150">例如，下面的命令针对可用性组 `MyDb3` 中的可用性数据库 `MyAg`恢复数据同步。</span><span class="sxs-lookup"><span data-stu-id="b834f-150">For example, the following command resumes data synchronization for the availability database `MyDb3` in the availability group `MyAg`.</span></span>  
  
    ```powershell
    Resume-SqlAvailabilityDatabase -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\Databases\MyDb3  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="b834f-151">若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b834f-151">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="b834f-152">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="b834f-152">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="b834f-153">**设置和使用 SQL Server PowerShell 提供程序**</span><span class="sxs-lookup"><span data-stu-id="b834f-153">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="b834f-154">SQL Server PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="b834f-154">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="b834f-155">相关任务</span><span class="sxs-lookup"><span data-stu-id="b834f-155">Related Tasks</span></span>  
  
-   [<span data-ttu-id="b834f-156">挂起可用性数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b834f-156">Suspend an Availability Database &#40;SQL Server&#41;</span></span>](suspend-an-availability-database-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="b834f-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b834f-157">See Also</span></span>  
 [<span data-ttu-id="b834f-158">AlwaysOn 可用性组 &#40;SQL Server 概述&#41;</span><span class="sxs-lookup"><span data-stu-id="b834f-158">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
