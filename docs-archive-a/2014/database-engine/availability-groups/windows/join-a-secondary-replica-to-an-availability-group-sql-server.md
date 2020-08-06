---
title: 将次要副本联接到可用性组 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.joinreplica.f1
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], joining
- Availability Groups [SQL Server], configuring
ms.assetid: e5bd2489-097a-490e-8ea1-34fe48378ad1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c38c2d59a46b15fc9a1dca77ae6a67e8e59e1b80
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585966"
---
# <a name="join-a-secondary-replica-to-an-availability-group-sql-server"></a><span data-ttu-id="78dbd-102">将辅助副本联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="78dbd-102">Join a Secondary Replica to an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="78dbd-103">本主题说明如何通过在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]或 PowerShell 来将辅助副本联接到 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="78dbd-103">This topic describes how to join a secondary replica to an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="78dbd-104">在将某一辅助副本添加到一个 AlwaysOn 可用性组后，这个辅助副本必须联接到该可用性组。</span><span class="sxs-lookup"><span data-stu-id="78dbd-104">After a secondary replica is added to an AlwaysOn availability group, the secondary replica must be joined to the availability group.</span></span> <span data-ttu-id="78dbd-105">该联接副本操作必须在承载辅助副本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例上执行。</span><span class="sxs-lookup"><span data-stu-id="78dbd-105">The join-replica operation must be performed on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is hosting the secondary replica.</span></span>  
  
-   <span data-ttu-id="78dbd-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="78dbd-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="78dbd-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="78dbd-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="78dbd-108">安全性</span><span class="sxs-lookup"><span data-stu-id="78dbd-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="78dbd-109">**若要准备辅助数据库，请使用：**</span><span class="sxs-lookup"><span data-stu-id="78dbd-109">**To prepare a secondary database, using:**</span></span>  
  
     [<span data-ttu-id="78dbd-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="78dbd-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="78dbd-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="78dbd-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="78dbd-112">PowerShell</span><span class="sxs-lookup"><span data-stu-id="78dbd-112">PowerShell</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="78dbd-113">**跟进：** [配置辅助数据库](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="78dbd-113">**Follow Up:** [Configure Secondary Databases](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="78dbd-114">开始之前</span><span class="sxs-lookup"><span data-stu-id="78dbd-114">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="78dbd-115">先决条件</span><span class="sxs-lookup"><span data-stu-id="78dbd-115">Prerequisites</span></span>  
  
-   <span data-ttu-id="78dbd-116">该可用性组的主副本当前必须处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="78dbd-116">The primary replica of the availability group must currently be online.</span></span>  
  
-   <span data-ttu-id="78dbd-117">您必须连接到承载尚未联接到该可用性组的辅助副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="78dbd-117">You must be connected to the server instance that hosts a secondary replica that has not yet have been joined to the availability group.</span></span>  
  
-   <span data-ttu-id="78dbd-118">本地服务器实例必须能够连接到承载主副本的服务器实例的数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="78dbd-118">The local server instance must be able to connect to the database mirroring endpoint of the server instance that is hosting the primary replica.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="78dbd-119">如果不满足任何先决条件，联接操作将会失败。</span><span class="sxs-lookup"><span data-stu-id="78dbd-119">If any prerequisite is not met, the join operation fails.</span></span> <span data-ttu-id="78dbd-120">在联接尝试失败之后，您可能需要连接到承载主副本的服务器实例以删除并重新添加辅助副本，然后您才可以将其联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="78dbd-120">After a failed join attempt, you might need to connect to the server instance that hosts the primary replica to remove and re-add the secondary replica before you can join it to the availability group.</span></span> <span data-ttu-id="78dbd-121">有关详细信息，请参阅[将辅助副本从可用性组删除 (SQL Server)](remove-a-secondary-replica-from-an-availability-group-sql-server.md) 和[将辅助副本添加到可用性组 (SQL Server)](add-a-secondary-replica-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="78dbd-121">For more information, see [Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md) and [Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="78dbd-122">Security</span><span class="sxs-lookup"><span data-stu-id="78dbd-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="78dbd-123">权限</span><span class="sxs-lookup"><span data-stu-id="78dbd-123">Permissions</span></span>  
 <span data-ttu-id="78dbd-124">对可用性组要求 ALTER AVAILABILITY GROUP 权限、CONTROL AVAILABILITY GROUP 权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="78dbd-124">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="78dbd-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="78dbd-125">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="78dbd-126">**将可用性副本联接到可用性组**</span><span class="sxs-lookup"><span data-stu-id="78dbd-126">**To join an availability replica to an availability group**</span></span>  
  
1.  <span data-ttu-id="78dbd-127">在对象资源管理器中，连接到承载辅助副本的服务器实例，然后单击服务器名称以便展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="78dbd-127">In Object Explorer, connect to the server instance that hosts the secondary replica, and click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="78dbd-128">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="78dbd-128">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="78dbd-129">选择您连接到辅助副本的可用性组。</span><span class="sxs-lookup"><span data-stu-id="78dbd-129">Select the availability group of the secondary replica to which you are connected.</span></span>  
  
4.  <span data-ttu-id="78dbd-130">右键单击辅助副本，然后单击\*\*\*\*“联接到可用性组”。</span><span class="sxs-lookup"><span data-stu-id="78dbd-130">Right-click the secondary replica, and click **Join to Availability Group**.</span></span>  
  
5.  <span data-ttu-id="78dbd-131">这将打开 **“将副本联接到可用性组”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="78dbd-131">This opens the **Join Replica to Availability Group** dialog box.</span></span>  
  
6.  <span data-ttu-id="78dbd-132">若要将辅助副本联接到可用性组，请单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="78dbd-132">To join the secondary replica to the availability group, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="78dbd-133">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="78dbd-133">Using Transact-SQL</span></span>  
 <span data-ttu-id="78dbd-134">**将可用性副本联接到可用性组**</span><span class="sxs-lookup"><span data-stu-id="78dbd-134">**To join an availability replica to an availability group**</span></span>  
  
1.  <span data-ttu-id="78dbd-135">连接到承载辅助副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="78dbd-135">Connect to the server instance that hosts the secondary replica.</span></span>  
  
2.  <span data-ttu-id="78dbd-136">按如下所示使用 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 语句：</span><span class="sxs-lookup"><span data-stu-id="78dbd-136">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="78dbd-137">ALTER AVAILABILITY GROUP *group_name* JOIN</span><span class="sxs-lookup"><span data-stu-id="78dbd-137">ALTER AVAILABILITY GROUP *group_name* JOIN</span></span>  
  
     <span data-ttu-id="78dbd-138">其中， *group_name* 是可用性组的名称。</span><span class="sxs-lookup"><span data-stu-id="78dbd-138">where *group_name* is the name of the availability group.</span></span>  
  
     <span data-ttu-id="78dbd-139">下面的示例将辅助副本联接到 `MyAG` 可用性组。</span><span class="sxs-lookup"><span data-stu-id="78dbd-139">The following example, joins the secondary replica to the `MyAG` availability group.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAG JOIN;  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="78dbd-140">若要查看此用于上下文的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句，请参阅[创建可用性组 (Transact-SQL)](create-an-availability-group-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="78dbd-140">To see this [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement used in context, see [Create an Availability Group &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md).</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="78dbd-141">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="78dbd-141">Using PowerShell</span></span>  
 <span data-ttu-id="78dbd-142">**将可用性副本联接到可用性组**</span><span class="sxs-lookup"><span data-stu-id="78dbd-142">**To join an availability replica to an availability group**</span></span>  
  
 <span data-ttu-id="78dbd-143">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 提供程序中：</span><span class="sxs-lookup"><span data-stu-id="78dbd-143">In the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell provider:</span></span>  
  
1.  <span data-ttu-id="78dbd-144">切换目录 (`cd`) 到承载辅助副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="78dbd-144">Change directory (`cd`) to the server instance that hosts the secondary replica.</span></span>  
  
2.  <span data-ttu-id="78dbd-145">通过使用可用性组的名称执行 **Join-SqlAvailabilityGroup** cmdlet，将辅助副本联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="78dbd-145">Join the secondary replica to the availability group by executing the **Join-SqlAvailabilityGroup** cmdlet with the name of the availability group.</span></span>  
  
     <span data-ttu-id="78dbd-146">例如，以下命令将由位于指定路径的服务器实例承载的辅助副本联接到名为 `MyAg`的可用性组。</span><span class="sxs-lookup"><span data-stu-id="78dbd-146">For example, the following command joins a secondary replica hosted by the server instance located at the specified path to the availability group named `MyAg`.</span></span>  <span data-ttu-id="78dbd-147">此服务器实例必须承载此可用性组中的辅助副本。</span><span class="sxs-lookup"><span data-stu-id="78dbd-147">This server instance must host a secondary replica in this availability group.</span></span>  
  
    ```powershell
    Join-SqlAvailabilityGroup -Path SQLSERVER:\SQL\SecondaryServer\InstanceName -Name 'MyAg'  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="78dbd-148">若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="78dbd-148">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="78dbd-149">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="78dbd-149">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="78dbd-150">**设置和使用 SQL Server PowerShell 提供程序**</span><span class="sxs-lookup"><span data-stu-id="78dbd-150">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="78dbd-151">SQL Server PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="78dbd-151">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-configure-secondary-databases"></a><a name="FollowUp"></a><span data-ttu-id="78dbd-152">跟进：配置辅助数据库</span><span class="sxs-lookup"><span data-stu-id="78dbd-152">Follow Up: Configure Secondary Databases</span></span>  
 <span data-ttu-id="78dbd-153">对于该可用性组中的每个数据库，您在承载辅助副本的服务器实例上需要辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="78dbd-153">For every database in the availability group, you need a secondary database on the server instance that is hosting the secondary replica.</span></span> <span data-ttu-id="78dbd-154">您可以在将辅助副本联接到可用性组之前或之后，按如下所述配置辅助数据库：</span><span class="sxs-lookup"><span data-stu-id="78dbd-154">You can configure secondary databases either before or after you join a secondary replica to an availability group, as follows:</span></span>  
  
1.  <span data-ttu-id="78dbd-155">通过将 RESTORE WITH NORECOVERY 用于每个还原操作，将各个主数据库的最近数据库和日志备份还原到承载辅助副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="78dbd-155">Restore recent database and log backups of each primary database onto the server instance that hosts the secondary replica, using RESTORE WITH NORECOVERY for every restore operation.</span></span> <span data-ttu-id="78dbd-156">有关详细信息，请参阅 [为可用性组手动准备辅助数据库 (SQL Server)](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)或 PowerShell 将辅助数据库联接到 Always On 可用性组。</span><span class="sxs-lookup"><span data-stu-id="78dbd-156">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="78dbd-157">将每个辅助数据库联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="78dbd-157">Join each secondary database to the availability group.</span></span> <span data-ttu-id="78dbd-158">有关详细信息，请参阅 [将辅助数据库联接到可用性组 (SQL Server)](join-a-secondary-database-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="78dbd-158">For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78dbd-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="78dbd-159">See Also</span></span>  
 <span data-ttu-id="78dbd-160">[创建和配置可用性组 (SQL Server)](creation-and-configuration-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="78dbd-160">[Creation and Configuration of Availability Groups &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="78dbd-161">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="78dbd-161">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="78dbd-162">&#41;删除 AlwaysOn 可用性组配置 &#40;SQL Server 的疑难解答</span><span class="sxs-lookup"><span data-stu-id="78dbd-162">Troubleshoot AlwaysOn Availability Groups Configuration &#40;SQL Server&#41;deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
