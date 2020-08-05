---
title: 从可用性组中删除辅助数据库 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.unjoindb.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- Availability Groups [SQL Server], removing
- Availability Groups [SQL Server], databases
ms.assetid: 4e51a570-58d7-4f01-9390-4198f3602576
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1c3de0afd73b46ae5594d26d1763f5bd78483efd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579797"
---
# <a name="remove-a-secondary-database-from-an-availability-group-sql-server"></a><span data-ttu-id="d549b-102">从可用性组中删除辅助数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d549b-102">Remove a Secondary Database from an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="d549b-103">本主题说明如何通过在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]或 PowerShell 从 AlwaysOn 可用性组中删除辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="d549b-103">This topic describes how to remove a secondary database from an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="d549b-104">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="d549b-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d549b-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="d549b-105">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="d549b-106">安全性</span><span class="sxs-lookup"><span data-stu-id="d549b-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d549b-107">**若要删除辅助数据库，请使用：**</span><span class="sxs-lookup"><span data-stu-id="d549b-107">**To remove a secondary database, using:**</span></span>  
  
     [<span data-ttu-id="d549b-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d549b-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d549b-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d549b-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="d549b-110">PowerShell</span><span class="sxs-lookup"><span data-stu-id="d549b-110">PowerShell</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="d549b-111">**跟进：**  [从可用性组中删除辅助数据库之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="d549b-111">**Follow Up:**  [After Removing a Secondary Database from an Availability Group](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d549b-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="d549b-112">Before You Begin</span></span>  
  
###  <a name="Restrictions"></a>   
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="d549b-113">先决条件和限制</span><span class="sxs-lookup"><span data-stu-id="d549b-113">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="d549b-114">只有辅助副本支持该任务。</span><span class="sxs-lookup"><span data-stu-id="d549b-114">This task is supported only on secondary replicas.</span></span> <span data-ttu-id="d549b-115">您必须连接到承载要从中删除数据库的辅助副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="d549b-115">You must be connected to the server instance that hosts the secondary replica from which the database is to be removed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d549b-116">Security</span><span class="sxs-lookup"><span data-stu-id="d549b-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d549b-117">权限</span><span class="sxs-lookup"><span data-stu-id="d549b-117">Permissions</span></span>  
 <span data-ttu-id="d549b-118">需要对数据库拥有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="d549b-118">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d549b-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d549b-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="d549b-120">**从可用性组中删除辅助数据库**</span><span class="sxs-lookup"><span data-stu-id="d549b-120">**To remove a secondary database from an availability group**</span></span>  
  
1.  <span data-ttu-id="d549b-121">在对象资源管理器中，连接到承载您要从中删除一个或多个辅助数据库的辅助副本的服务器实例，然后展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="d549b-121">In Object Explorer, connect to the server instance that hosts the secondary replica from which you want to remove one or more secondary databases, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="d549b-122">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="d549b-122">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="d549b-123">选择可用性组，然后展开 **“可用性数据库”** 节点。</span><span class="sxs-lookup"><span data-stu-id="d549b-123">Select the availability group, and expand the **Availability Databases** node.</span></span>  
  
4.  <span data-ttu-id="d549b-124">此步骤取决于您是要删除多个数据库组，还是只删除一个数据库，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d549b-124">This step depends on whether you want to remove multiple databases groups or only one database, as follows:</span></span>  
  
    -   <span data-ttu-id="d549b-125">若要删除多个数据库，请使用 **“对象资源管理器详细信息”** 窗格查看并选择所有要删除的数据库。</span><span class="sxs-lookup"><span data-stu-id="d549b-125">To remove multiple databases, use the **Object Explorer Details** pane to view and select all the databases that you want to remove.</span></span> <span data-ttu-id="d549b-126">有关详细信息，请参阅[使用对象资源管理器详细信息监视可用性组 (SQL Server Management Studio)](use-object-explorer-details-to-monitor-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="d549b-126">For more information, see [Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md).</span></span>  
  
    -   <span data-ttu-id="d549b-127">若要删除单个数据库，请在 **“对象资源管理器”** 窗格或 **“对象资源管理器详细信息”** 窗格中选中该数据库。</span><span class="sxs-lookup"><span data-stu-id="d549b-127">To remove a single database, select it in either the **Object Explorer** pane or the **Object Explorer Details** pane.</span></span>  
  
5.  <span data-ttu-id="d549b-128">右键单击选定的一个或多个数据库，然后在命令菜单中选择“删除辅助数据库”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d549b-128">Right-click the selected database or databases, and select **Remove Secondary Database** in the command menu.</span></span>  
  
6.  <span data-ttu-id="d549b-129">在 **“从可用性组删除数据库”** 对话框中，要删除所有列出的数据库，则单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="d549b-129">In the **Remove Database from Availability Group** dialog box, to remove all the listed databases, click **OK**.</span></span> <span data-ttu-id="d549b-130">如果您不想删除所有列出的数据库，请单击 **“取消”**。</span><span class="sxs-lookup"><span data-stu-id="d549b-130">If you do not want to remove all the listed databases, click **Cancel**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d549b-131">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d549b-131">Using Transact-SQL</span></span>  
 <span data-ttu-id="d549b-132">**从可用性组中删除辅助数据库**</span><span class="sxs-lookup"><span data-stu-id="d549b-132">**To remove a secondary database from an availability group**</span></span>  
  
1.  <span data-ttu-id="d549b-133">连接到承载辅助副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="d549b-133">Connect to the server instance that hosts the secondary replica.</span></span>  
  
2.  <span data-ttu-id="d549b-134">使用 [ALTER DATABASE 语句的 SET HADR 子句](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) ，如下所述：</span><span class="sxs-lookup"><span data-stu-id="d549b-134">Use the [SET HADR clause of the ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) statement, as follows:</span></span>  
  
     <span data-ttu-id="d549b-135">ALTER DATABASE *database_name* SET HADR OFF</span><span class="sxs-lookup"><span data-stu-id="d549b-135">ALTER DATABASE *database_name* SET HADR OFF</span></span>  
  
     <span data-ttu-id="d549b-136">其中， *database_name* 为要从其所属的可用性组中删除的辅助数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="d549b-136">where *database_name* is the name of a secondary database to be removed from the availability group to which it belongs.</span></span>  
  
     <span data-ttu-id="d549b-137">下面的示例将本地辅助数据库 *MyDb2* 从其可用性组中删除。</span><span class="sxs-lookup"><span data-stu-id="d549b-137">The following example removes the local secondary database *MyDb2* from its availability group.</span></span>  
  
    ```sql
    ALTER DATABASE MyDb2 SET HADR OFF;  
    GO  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="d549b-138">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d549b-138">Using PowerShell</span></span>  
 <span data-ttu-id="d549b-139">**从可用性组中删除辅助数据库**</span><span class="sxs-lookup"><span data-stu-id="d549b-139">**To remove a secondary database from an availability group**</span></span>  
  
1.  <span data-ttu-id="d549b-140">切换目录 (`cd`) 到承载辅助副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="d549b-140">Change directory (`cd`) to the server instance that hosts the secondary replica.</span></span>  
  
2.  <span data-ttu-id="d549b-141">使用 **Remove-SqlAvailabilityDatabase** cmdlet，指定要从可用性组中删除的可用性数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="d549b-141">Use the **Remove-SqlAvailabilityDatabase** cmdlet, specifying the name of the availability database to be removed from the availability group.</span></span> <span data-ttu-id="d549b-142">当您连接到承载辅助副本的服务器实例时，只能从可用性组中删除本地辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="d549b-142">When you are connected to a server instance that hosts a secondary replica, only the local secondary database is removed from the availability group.</span></span>  
  
     <span data-ttu-id="d549b-143">例如，下面的命令从名为 `MyDb8` 的服务器实例承载的次要副本中删除辅助数据库 `SecondaryComputer\Instance`。</span><span class="sxs-lookup"><span data-stu-id="d549b-143">For example, the following command removes the secondary database `MyDb8` from the secondary replica hosted by the server instance named `SecondaryComputer\Instance`.</span></span> <span data-ttu-id="d549b-144">与已删除的辅助数据库的数据同步将停止。</span><span class="sxs-lookup"><span data-stu-id="d549b-144">Data synchronization to the removed secondary databases ceases.</span></span> <span data-ttu-id="d549b-145">此命令将不会影响主数据库或任何其他辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="d549b-145">This command does not affect the primary database or any other secondary databases.</span></span>  
  
    ```powershell
    Remove-SqlAvailabilityDatabase -Path SQLSERVER:\Sql\SecondaryComputer\InstanceName\AvailabilityGroups\MyAg\Databases\MyDb8  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="d549b-146">若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d549b-146">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="d549b-147">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="d549b-147">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="d549b-148">**设置和使用 SQL Server PowerShell 提供程序**</span><span class="sxs-lookup"><span data-stu-id="d549b-148">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="d549b-149">SQL Server PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="d549b-149">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-after-removing-a-secondary-database-from-an-availability-group"></a><a name="FollowUp"></a> <span data-ttu-id="d549b-150">跟进：从可用性组中删除辅助数据库之后</span><span class="sxs-lookup"><span data-stu-id="d549b-150">Follow Up: After Removing a Secondary Database from an Availability Group</span></span>  
 <span data-ttu-id="d549b-151">删除辅助数据库之后，它不再加入到可用性组中，有关删除的辅助数据库的所有信息都会被可用性组丢弃。</span><span class="sxs-lookup"><span data-stu-id="d549b-151">When a secondary database is removed, it is no longer joined to the availability group and all information about the removed secondary database is discarded by the availability group.</span></span> <span data-ttu-id="d549b-152">删除的辅助数据库处于 RESTORING 状态。</span><span class="sxs-lookup"><span data-stu-id="d549b-152">The removed secondary database is placed in the RESTORING state.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="d549b-153">在删除辅助数据库后的较短时间中，您可能能够通过将其重新联接到可用性组，在数据库上重新启动 AlwaysOn 数据同步。</span><span class="sxs-lookup"><span data-stu-id="d549b-153">For a short time after removing a secondary database, you might be able to restart AlwaysOn data synchronization on the database by re-joining it to the availability group.</span></span> <span data-ttu-id="d549b-154">有关详细信息，请参阅 [将辅助数据库联接到可用性组 (SQL Server)](join-a-secondary-database-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d549b-154">For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
 <span data-ttu-id="d549b-155">此时，可以通过多种备选方法处理删除的辅助数据库：</span><span class="sxs-lookup"><span data-stu-id="d549b-155">At this point there are alternative ways of dealing with a removed secondary database:</span></span>  
  
-   <span data-ttu-id="d549b-156">如果不再需要该辅助数据库，则可以将其删除。</span><span class="sxs-lookup"><span data-stu-id="d549b-156">If you no longer need the secondary database, you can drop it.</span></span>  
  
     <span data-ttu-id="d549b-157">有关详细信息，请参阅 [DROP DATABASE (Transact SQL)](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) 或[删除数据库](../../../relational-databases/databases/delete-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="d549b-157">For more information, see [DROP DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) or [Delete a Database](../../../relational-databases/databases/delete-a-database.md).</span></span>  
  
-   <span data-ttu-id="d549b-158">如果当辅助数据库已从可用性组中删除后要访问它，则可以恢复此数据库。</span><span class="sxs-lookup"><span data-stu-id="d549b-158">If you want to access a removed secondary database after it has been removed from the availability group, you can recover the database.</span></span> <span data-ttu-id="d549b-159">但是，如果恢复删除的辅助数据库，则会有两个同名的、独立但不同的数据库处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="d549b-159">However, if you recover a removed secondary database, two divergent, independent databases that have the same name are online.</span></span> <span data-ttu-id="d549b-160">您必须确保客户端仅可访问当前主数据库。</span><span class="sxs-lookup"><span data-stu-id="d549b-160">You must make sure that clients can access only the current primary database.</span></span>  
  
     <span data-ttu-id="d549b-161">有关详细信息，请参阅[恢复数据库而不还原数据 (Transact-SQL)](../../../relational-databases/backup-restore/recover-a-database-without-restoring-data-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="d549b-161">For more information, see [Recover a Database Without Restoring Data &#40;Transact-SQL&#41;](../../../relational-databases/backup-restore/recover-a-database-without-restoring-data-transact-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d549b-162">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d549b-162">See Also</span></span>  
 <span data-ttu-id="d549b-163">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d549b-163">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="d549b-164">将主数据库从可用性组删除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d549b-164">Remove a Primary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-primary-database-from-an-availability-group-sql-server.md)  
