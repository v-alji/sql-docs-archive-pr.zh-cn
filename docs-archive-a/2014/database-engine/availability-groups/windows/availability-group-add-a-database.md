---
title: 将数据库添加到可用性组 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- primary databases [SQL Server], in availability group
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: 2a54eef8-9e8e-4e04-909c-6970112d55cc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0907cf711cac65ad77a8948841d92705fdc1eac9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577873"
---
# <a name="add-a-database-to-an-availability-group-sql-server"></a><span data-ttu-id="30353-102">将数据库添加到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="30353-102">Add a Database to an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="30353-103">本主题说明如何通过在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]或 PowerShell 将数据库添加到 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="30353-103">This topic describes how to add a database to an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="30353-104">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="30353-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="30353-105">先决条件和限制</span><span class="sxs-lookup"><span data-stu-id="30353-105">Prerequisites and Restrictions</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="30353-106">权限</span><span class="sxs-lookup"><span data-stu-id="30353-106">Permissions</span></span>](#Permissions)  
  
-   <span data-ttu-id="30353-107">**若要将数据库添加到可用性组，请使用：**</span><span class="sxs-lookup"><span data-stu-id="30353-107">**To add a database to an availability group, using:**</span></span>  
  
     [<span data-ttu-id="30353-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="30353-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="30353-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="30353-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="30353-110">PowerShell</span><span class="sxs-lookup"><span data-stu-id="30353-110">PowerShell</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="30353-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="30353-111">Before You Begin</span></span>  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="30353-112">先决条件和限制</span><span class="sxs-lookup"><span data-stu-id="30353-112">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="30353-113">您必须连接到承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="30353-113">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
-   <span data-ttu-id="30353-114">数据库必须位于承载主副本的服务器实例上并符合可用性数据库的先决条件和限制。</span><span class="sxs-lookup"><span data-stu-id="30353-114">The database must reside on the server instance that hosts the primary replica and comply with the prerequisites and restrictions for availability databases.</span></span> <span data-ttu-id="30353-115">有关详细信息，请参阅[针对 AlwaysOn 可用性组的先决条件、限制和建议 (SQL Server)](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="30353-115">For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="30353-116">Security</span><span class="sxs-lookup"><span data-stu-id="30353-116">Security</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="30353-117">权限</span><span class="sxs-lookup"><span data-stu-id="30353-117">Permissions</span></span>  
 <span data-ttu-id="30353-118">对可用性组要求 ALTER AVAILABILITY GROUP 权限、CONTROL AVAILABILITY GROUP 权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="30353-118">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="30353-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="30353-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="30353-120">**将数据库添加到可用性组**</span><span class="sxs-lookup"><span data-stu-id="30353-120">**To add a database to an availability group**</span></span>  
  
1.  <span data-ttu-id="30353-121">在对象资源管理器中，连接到承载主副本的服务器实例，然后展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="30353-121">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="30353-122">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="30353-122">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="30353-123">右键单击可用性组，然后选择下列命令之一：</span><span class="sxs-lookup"><span data-stu-id="30353-123">Right-click the availability group, and select one of the following commands:</span></span>  
  
    -   <span data-ttu-id="30353-124">若要启动“将数据库添加到可用性组向导”，请选择 **“添加数据库”** 命令。</span><span class="sxs-lookup"><span data-stu-id="30353-124">To launch the Add Database to Availability Group Wizard, select the **Add Database** command.</span></span> <span data-ttu-id="30353-125">有关详细信息，请参阅[使用“将数据库添加到可用性组向导”(SQL Server Management Studio)](availability-group-add-database-to-group-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="30353-125">For more information, see [Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;](availability-group-add-database-to-group-wizard.md).</span></span>  
  
    -   <span data-ttu-id="30353-126">若要通过在 **“可用性组属性”** 对话框中指定一个或多个数据库来进行添加，则选择 **“属性”** 命令。</span><span class="sxs-lookup"><span data-stu-id="30353-126">To add one or more databases by specifying them in the **Availability Group Properties** dialog box, select the **Properties** command.</span></span> <span data-ttu-id="30353-127">添加数据库的步骤如下所示：</span><span class="sxs-lookup"><span data-stu-id="30353-127">The steps for adding a database are as follows:</span></span>  
  
        1.  <span data-ttu-id="30353-128">在 **“可用性数据库”** 窗格中，单击 **“添加”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="30353-128">In the **Availability Databases** pane, click the **Add** button.</span></span> <span data-ttu-id="30353-129">这将创建并选择一个空数据库字段。</span><span class="sxs-lookup"><span data-stu-id="30353-129">This creates and selects a blank database field.</span></span>  
  
        2.  <span data-ttu-id="30353-130">输入符合可用性数据库先决条件的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="30353-130">Enter the name of a database that meets the availability-databases prerequisites.</span></span>  
  
         <span data-ttu-id="30353-131">若要添加其他数据库，请重复前面的步骤。</span><span class="sxs-lookup"><span data-stu-id="30353-131">To add another database, repeat the preceding steps.</span></span> <span data-ttu-id="30353-132">当您完成指定数据库后，请单击 **“确定”** 以完成此操作。</span><span class="sxs-lookup"><span data-stu-id="30353-132">When you are done specifying databases, click **OK** to complete the operation.</span></span>  
  
         <span data-ttu-id="30353-133">在您使用 **“可用性组属性”** 对话框将数据库添加到可用性组后，需要在承载辅助副本的每个服务器实例上配置相应的辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="30353-133">After you use the **Availability Group Properties** dialog box to add a database to an availability group, you need to configure the corresponding secondary database on each server instance that hosts a secondary replica.</span></span> <span data-ttu-id="30353-134">有关详细信息，请参阅[启动 AlwaysOn 辅助数据库的数据移动 (SQL Server)](start-data-movement-on-an-always-on-secondary-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="30353-134">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="30353-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="30353-135">Using Transact-SQL</span></span>  
 <span data-ttu-id="30353-136">**将数据库添加到可用性组**</span><span class="sxs-lookup"><span data-stu-id="30353-136">**To add a database to an availability group**</span></span>  
  
1.  <span data-ttu-id="30353-137">连接到承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="30353-137">Connect to the server instance that hosts the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="30353-138">按如下所示使用 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 语句：</span><span class="sxs-lookup"><span data-stu-id="30353-138">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="30353-139">ALTER AVAILABILITY GROUP *group_name* ADD DATABASE *database_name* [,...*n*]</span><span class="sxs-lookup"><span data-stu-id="30353-139">ALTER AVAILABILITY GROUP *group_name* ADD DATABASE *database_name* [,...*n*]</span></span>  
  
     <span data-ttu-id="30353-140">其中 *group_name* 是可用性组的名称， *database_name* 是要添加到该组的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="30353-140">where *group_name* is the name of the availability group and *database_name* is the name of a database to be added to the group.</span></span>  
  
     <span data-ttu-id="30353-141">以下示例添加 *MyDb3* 数据库到 *MyAG* 可用性组。</span><span class="sxs-lookup"><span data-stu-id="30353-141">The following example adds the *MyDb3* database to the *MyAG* availability group.</span></span>  
  
    ```  
    -- Connect to the server instance that hosts the primary replica.  
    -- Add an existing database to the availability group.  
    ALTER AVAILABILITY GROUP MyAG ADD DATABASE MyDb3;  
    GO  
    ```  
  
3.  <span data-ttu-id="30353-142">在您将数据库添加到可用性组后，需要在承载辅助副本的每个服务器实例上配置相应的辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="30353-142">After you add a database to an availability group, you need to configure the corresponding secondary database on each server instance that hosts a secondary replica.</span></span> <span data-ttu-id="30353-143">有关详细信息，请参阅[启动 AlwaysOn 辅助数据库的数据移动 (SQL Server)](start-data-movement-on-an-always-on-secondary-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="30353-143">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="30353-144">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="30353-144">Using PowerShell</span></span>  
 <span data-ttu-id="30353-145">**将数据库添加到可用性组**</span><span class="sxs-lookup"><span data-stu-id="30353-145">**To add a database to an availability group**</span></span>  
  
1.  <span data-ttu-id="30353-146">将目录 (`cd`) 更改为承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="30353-146">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="30353-147">使用 `Add-SqlAvailabilityDatabase` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="30353-147">Use the `Add-SqlAvailabilityDatabase` cmdlet.</span></span>  
  
     <span data-ttu-id="30353-148">例如，以下命令将添加辅助数据库 `MyDd` 到 `MyAG` 可用性组中，其主副本由 `PrimaryServer\InstanceName`承载。</span><span class="sxs-lookup"><span data-stu-id="30353-148">For example, the following command adds the secondary database `MyDd` to the `MyAG` availability group, whose primary replica is hosted by `PrimaryServer\InstanceName`.</span></span>  
  
    ```powershell
    Add-SqlAvailabilityDatabase `   
     -Path SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MyAG `   
     -Database "MyDb"  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="30353-149">若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="30353-149">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="30353-150">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="30353-150">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
3.  <span data-ttu-id="30353-151">在您将数据库添加到可用性组后，需要在承载辅助副本的每个服务器实例上配置相应的辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="30353-151">After you add a database to an availability group, you need to configure the corresponding secondary database on each server instance that hosts a secondary replica.</span></span> <span data-ttu-id="30353-152">有关详细信息，请参阅[启动 AlwaysOn 辅助数据库的数据移动 (SQL Server)](start-data-movement-on-an-always-on-secondary-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="30353-152">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
 <span data-ttu-id="30353-153">若要设置并使用 SQL Server PowerShell 提供程序，请参阅[SQL Server PowerShell 提供程序](../../../powershell/sql-server-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="30353-153">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).</span></span>

 <span data-ttu-id="30353-154">下面的示例说明了一个完整过程：从承载可用性组主副本的服务器实例上的一个数据库中准备一个辅助数据库，将此数据库添加到可用性组（作为主数据库），然后将此辅助数据库加入可用性组。</span><span class="sxs-lookup"><span data-stu-id="30353-154">The following example shows the full process for preparing a secondary database from a database on the server instance that hosts the primary replica of an availability group, adding the database to an availability group (as a primary database), and then joining the secondary database to the availability group.</span></span> <span data-ttu-id="30353-155">首先，该示例备份数据库及其事务日志。</span><span class="sxs-lookup"><span data-stu-id="30353-155">First, the example backs up the database and its transaction log.</span></span> <span data-ttu-id="30353-156">然后，此示例将数据库和日志备份还原到承载辅助副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="30353-156">Then the example restores the database and log backups to the server instances that host a secondary replica.</span></span>  
  
 <span data-ttu-id="30353-157">此示例调用两次 `Add-SqlAvailabilityDatabase`：第一次是针对主副本调用，以便将数据库添加到可用性组；然后对辅助副本调用，以便将该副本上的辅助数据库加入到可用性组。</span><span class="sxs-lookup"><span data-stu-id="30353-157">The example calls `Add-SqlAvailabilityDatabase` twice: first on the primary replica to add the database to the availability group, and then on the secondary replica to join the secondary database on that replica to the availability group.</span></span> <span data-ttu-id="30353-158">如果您有多个辅助副本，则对其中每个副本还原和加入辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="30353-158">If you have more than one secondary replica, restore and join the secondary database on each of them.</span></span>  
  
```powershell
$DatabaseBackupFile = "\\share\backups\MyDatabase.bak"  
$LogBackupFile = "\\share\backups\MyDatabase.trn"  
$MyAgPrimaryPath = "SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MyAg"  
$MyAgSecondaryPath = "SQLSERVER:\SQL\SecondaryServer\InstanceName\AvailabilityGroups\MyAg"  
  
Backup-SqlDatabase -Database "MyDatabase" -BackupFile $DatabaseBackupFile -ServerInstance "PrimaryServer\InstanceName"  
Backup-SqlDatabase -Database "MyDatabase" -BackupFile $LogBackupFile -ServerInstance "PrimaryServer\InstanceName" -BackupAction 'Log'  
  
Restore-SqlDatabase -Database "MyDatabase" -BackupFile $DatabaseBackupFile -ServerInstance "SecondaryServer\InstanceName" -NoRecovery  
Restore-SqlDatabase -Database "MyDatabase" -BackupFile $LogBackupFile -ServerInstance "SecondaryServer\InstanceName" -RestoreAction 'Log' -NoRecovery  
  
Add-SqlAvailabilityDatabase -Path $MyAgPrimaryPath -Database "MyDatabase"  
Add-SqlAvailabilityDatabase -Path $MyAgSecondaryPath -Database "MyDatabase"
```  
  
## <a name="see-also"></a><span data-ttu-id="30353-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="30353-159">See Also</span></span>  
 <span data-ttu-id="30353-160">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="30353-160">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="30353-161">[创建和配置可用性组 (SQL Server)](creation-and-configuration-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="30353-161">[Creation and Configuration of Availability Groups &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="30353-162">[使用 AlwaysOn 仪表板 &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="30353-162">[Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="30353-163">监视可用性组 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="30353-163">Monitor Availability Groups &#40;Transact-SQL&#41;</span></span>](monitor-availability-groups-transact-sql.md)  
