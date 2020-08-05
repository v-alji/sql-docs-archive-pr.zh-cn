---
title: 从可用性组中删除主数据库 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.removeprimarydb.f1
helpviewer_keywords:
- primary databases [SQL Server], in availability group
- Availability Groups [SQL Server], removing
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: 6d4ca31e-ddf0-44bf-be5e-a5da060bf096
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6b6fafaf6464431d68f8cfdf9dc9d8fa844a42a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579799"
---
# <a name="remove-a-primary-database-from-an-availability-group-sql-server"></a><span data-ttu-id="f8776-102">从可用性组中删除主数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f8776-102">Remove a Primary Database from an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="f8776-103">本主题说明如何通过在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 PowerShell，从 AlwaysOn 可用性组中删除主数据库和对应的辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="f8776-103">This topic describes how to remove both the primary database and the corresponding secondary database(s) from an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="f8776-104">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="f8776-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f8776-105">先决条件和限制</span><span class="sxs-lookup"><span data-stu-id="f8776-105">Prerequisites and Restrictions</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="f8776-106">安全性</span><span class="sxs-lookup"><span data-stu-id="f8776-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f8776-107">**若要删除可用性数据库，请使用：**</span><span class="sxs-lookup"><span data-stu-id="f8776-107">**To remove an availability database, using:**</span></span>  
  
     [<span data-ttu-id="f8776-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f8776-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f8776-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f8776-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="f8776-110">PowerShell</span><span class="sxs-lookup"><span data-stu-id="f8776-110">PowerShell</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="f8776-111">**跟进：**  [在从可用性组中删除可用性数据库之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="f8776-111">**Follow Up:**  [After Removing an Availability Database from an Availability Group](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f8776-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="f8776-112">Before You Begin</span></span>  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="f8776-113">先决条件和限制</span><span class="sxs-lookup"><span data-stu-id="f8776-113">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="f8776-114">只有主副本支持该任务。</span><span class="sxs-lookup"><span data-stu-id="f8776-114">This task is supported only on primary replicas.</span></span> <span data-ttu-id="f8776-115">您必须连接到承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="f8776-115">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f8776-116">Security</span><span class="sxs-lookup"><span data-stu-id="f8776-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f8776-117">权限</span><span class="sxs-lookup"><span data-stu-id="f8776-117">Permissions</span></span>  
 <span data-ttu-id="f8776-118">对可用性组要求 ALTER AVAILABILITY GROUP 权限、CONTROL AVAILABILITY GROUP 权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="f8776-118">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f8776-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f8776-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="f8776-120">**删除可用性数据库**</span><span class="sxs-lookup"><span data-stu-id="f8776-120">**To remove an availability database**</span></span>  
  
1.  <span data-ttu-id="f8776-121">在对象资源管理器中，连接到承载要删除的一个或多个数据库的主副本的服务器实例，然后展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="f8776-121">In Object Explorer, connect to the server instance that hosts the primary replica of the database or databases to be removed, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="f8776-122">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="f8776-122">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="f8776-123">选择可用性组，然后展开 **“可用性数据库”** 节点。</span><span class="sxs-lookup"><span data-stu-id="f8776-123">Select the availability group, and expand the **Availability Databases** node.</span></span>  
  
4.  <span data-ttu-id="f8776-124">此步骤取决于您是要删除多个数据库组，还是只删除一个数据库，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f8776-124">This step depends on whether you want to remove multiple databases groups or only one database, as follows:</span></span>  
  
    -   <span data-ttu-id="f8776-125">若要删除多个数据库，请使用 **“对象资源管理器详细信息”** 窗格查看并选择所有要删除的数据库。</span><span class="sxs-lookup"><span data-stu-id="f8776-125">To remove multiple databases, use the **Object Explorer Details** pane to view and select all the databases that you want to remove.</span></span> <span data-ttu-id="f8776-126">有关详细信息，请参阅[使用对象资源管理器详细信息监视可用性组 (SQL Server Management Studio)](use-object-explorer-details-to-monitor-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="f8776-126">For more information, see [Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md).</span></span>  
  
    -   <span data-ttu-id="f8776-127">若要删除单个数据库，请在 **“对象资源管理器”** 窗格或 **“对象资源管理器详细信息”** 窗格中选中该数据库。</span><span class="sxs-lookup"><span data-stu-id="f8776-127">To remove a single database, select it in either the **Object Explorer** pane or the **Object Explorer Details** pane.</span></span>  
  
5.  <span data-ttu-id="f8776-128">右键单击选定的一个或多个数据库，然后在命令菜单中选择“从可用性组中删除数据库”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8776-128">Right-click the selected database or databases, and select **Remove Database from Availability Group** in the command menu.</span></span>  
  
6.  <span data-ttu-id="f8776-129">在 **“从可用性组中删除数据库”** 对话框中，删除所有列出的数据库，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="f8776-129">In the **Remove Databases from Availability Group** dialog box, to remove all the listed databases, click **OK**.</span></span> <span data-ttu-id="f8776-130">如果您不想全部删除这些数据库，请单击 **“取消”**。</span><span class="sxs-lookup"><span data-stu-id="f8776-130">If you do not want to remove all them, click **Cancel**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f8776-131">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f8776-131">Using Transact-SQL</span></span>  
 <span data-ttu-id="f8776-132">**删除可用性数据库**</span><span class="sxs-lookup"><span data-stu-id="f8776-132">**To remove an availability database**</span></span>  
  
1.  <span data-ttu-id="f8776-133">连接到承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="f8776-133">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="f8776-134">按如下所示使用 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 语句：</span><span class="sxs-lookup"><span data-stu-id="f8776-134">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="f8776-135">ALTER AVAILABILITY GROUP *group_name* REMOVE DATABASE *availability_database_name*</span><span class="sxs-lookup"><span data-stu-id="f8776-135">ALTER AVAILABILITY GROUP *group_name* REMOVE DATABASE *availability_database_name*</span></span>  
  
     <span data-ttu-id="f8776-136">其中， *group_name* 是可用性组的名称， *database_name* 是要删除的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="f8776-136">where *group_name* is the name of the availability group and *database_name* is the name of the database to be removed.</span></span>  
  
     <span data-ttu-id="f8776-137">下面的示例将从 `Db6` 可用性组中删除名为 `MyAG` 的数据库。</span><span class="sxs-lookup"><span data-stu-id="f8776-137">The following example removes a databases named `Db6` from the `MyAG` availability group.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAG REMOVE DATABASE Db6;  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="f8776-138">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f8776-138">Using PowerShell</span></span>  
 <span data-ttu-id="f8776-139">**删除可用性数据库**</span><span class="sxs-lookup"><span data-stu-id="f8776-139">**To remove an availability database**</span></span>  
  
1.  <span data-ttu-id="f8776-140">将目录 (`cd`) 更改为承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="f8776-140">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="f8776-141">使用 `Remove-SqlAvailabilityDatabase` cmdlet，指定要从可用性组中删除的可用性数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="f8776-141">Use the `Remove-SqlAvailabilityDatabase` cmdlet, specifying the name of the availability database to be removed from the availability group.</span></span> <span data-ttu-id="f8776-142">当您连接到承载主副本的服务器实例时，主数据库及其对应的辅助数据库将从可用性组中全部删除。</span><span class="sxs-lookup"><span data-stu-id="f8776-142">When you are connected to the server instance that hosts the primary replica, the primary database and its corresponding secondary databases are all removed from the availability group.</span></span>  
  
     <span data-ttu-id="f8776-143">例如，下面的命令从名为 `MyDb9` 的可用性组中删除可用性数据库 `MyAg`。</span><span class="sxs-lookup"><span data-stu-id="f8776-143">For example, the following command removes the availability database `MyDb9` from the availability group named `MyAg`.</span></span> <span data-ttu-id="f8776-144">因为此命令在承载主副本的服务器实例上执行，所以，主数据库及其对应的所有辅助数据库都将从可用性组中删除。</span><span class="sxs-lookup"><span data-stu-id="f8776-144">Because the command is executed on the server instance that hosts the primary replica, the primary database and all its corresponding secondary databases are removed from the availability group.</span></span> <span data-ttu-id="f8776-145">在任何辅助副本上都不会出现针对此数据库的数据同步。</span><span class="sxs-lookup"><span data-stu-id="f8776-145">Data synchronization will no longer occur for this database on any secondary replica.</span></span>  
  
    ```powershell
    Remove-SqlAvailabilityDatabase -Path SQLSERVER:\Sql\PrimaryComputer\InstanceName\AvailabilityGroups\MyAg\Databases\MyDb9  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="f8776-146">若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f8776-146">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] PowerShell environment.</span></span> <span data-ttu-id="f8776-147">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="f8776-147">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="f8776-148">**设置和使用 SQL Server PowerShell 提供程序**</span><span class="sxs-lookup"><span data-stu-id="f8776-148">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="f8776-149">SQL Server PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="f8776-149">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-after-removing-an-availability-database-from-an-availability-group"></a><a name="FollowUp"></a><span data-ttu-id="f8776-150">跟进：在从可用性组中删除可用性数据库之后</span><span class="sxs-lookup"><span data-stu-id="f8776-150">Follow Up: After Removing an Availability Database from an Availability Group</span></span>  
 <span data-ttu-id="f8776-151">从其可用性组中删除可用性数据库后，将结束先前主数据库与对应的辅助数据库之间的数据同步。</span><span class="sxs-lookup"><span data-stu-id="f8776-151">Removing an availability database from its availability group ends data synchronization between the former primary database and the corresponding secondary databases.</span></span> <span data-ttu-id="f8776-152">以前的主数据库保持联机状态。</span><span class="sxs-lookup"><span data-stu-id="f8776-152">The former primary database remains online.</span></span> <span data-ttu-id="f8776-153">每个对应的辅助数据库都处于 RESTORING 状态。</span><span class="sxs-lookup"><span data-stu-id="f8776-153">Every corresponding secondary database is placed in the RESTORING state.</span></span>  
  
 <span data-ttu-id="f8776-154">此时，可以通过多种备选方法处理删除的辅助数据库：</span><span class="sxs-lookup"><span data-stu-id="f8776-154">At this point there are alternative ways of dealing with a removed secondary database:</span></span>  
  
-   <span data-ttu-id="f8776-155">如果不再需要给定的辅助数据库，则可以将其删除。</span><span class="sxs-lookup"><span data-stu-id="f8776-155">If you no longer need a given secondary database, you can drop it.</span></span>  
  
     <span data-ttu-id="f8776-156">有关详细信息，请参阅 [删除数据库](../../../relational-databases/databases/delete-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="f8776-156">For more information, see [Delete a Database](../../../relational-databases/databases/delete-a-database.md).</span></span>  
  
-   <span data-ttu-id="f8776-157">如果当辅助数据库已从可用性组中删除后要访问它，则可以恢复此数据库。</span><span class="sxs-lookup"><span data-stu-id="f8776-157">If you want to access a removed secondary database after it has been removed from the availability group, you can recover the database.</span></span> <span data-ttu-id="f8776-158">但是，如果恢复删除的辅助数据库，则会有两个同名的、独立但不同的数据库处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="f8776-158">However, if you recover a removed secondary database, two divergent, independent databases that have the same name are online.</span></span> <span data-ttu-id="f8776-159">您必须确保客户端仅可访问其中一个数据库，通常为最新的主数据库。</span><span class="sxs-lookup"><span data-stu-id="f8776-159">You must make sure that clients can access only one of them, typically the most recent primary database.</span></span>  
  
     <span data-ttu-id="f8776-160">有关详细信息，请参阅[恢复数据库而不还原数据 (Transact-SQL)](../../../relational-databases/backup-restore/recover-a-database-without-restoring-data-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="f8776-160">For more information, see [Recover a Database Without Restoring Data &#40;Transact-SQL&#41;](../../../relational-databases/backup-restore/recover-a-database-without-restoring-data-transact-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8776-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f8776-161">See Also</span></span>  
 <span data-ttu-id="f8776-162">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f8776-162">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="f8776-163">将辅助数据库从可用性组删除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f8776-163">Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
