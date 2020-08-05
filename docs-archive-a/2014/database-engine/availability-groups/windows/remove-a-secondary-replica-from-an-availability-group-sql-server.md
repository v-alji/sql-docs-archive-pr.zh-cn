---
title: 从可用性组中删除次要副本 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.removesecondaryar.f1
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], configuring
ms.assetid: 35ddc8b6-3e7c-4417-9a0a-d4987a09ddf7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e3f2b35ec9cf27f2f7b23714a41665f2709837a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579794"
---
# <a name="remove-a-secondary-replica-from-an-availability-group-sql-server"></a><span data-ttu-id="bd720-102">从可用性组中删除辅助副本 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bd720-102">Remove a Secondary Replica from an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="bd720-103">本主题说明如何通过在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]或 PowerShell 从 AlwaysOn 可用性组中删除辅助副本。</span><span class="sxs-lookup"><span data-stu-id="bd720-103">This topic describes how to remove a secondary replica from an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="bd720-104">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="bd720-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="bd720-105">限制和局限</span><span class="sxs-lookup"><span data-stu-id="bd720-105">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="bd720-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="bd720-106">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="bd720-107">安全性</span><span class="sxs-lookup"><span data-stu-id="bd720-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="bd720-108">**若要删除辅助副本，请使用：**</span><span class="sxs-lookup"><span data-stu-id="bd720-108">**To remove a secondary replica, using:**</span></span>  
  
     [<span data-ttu-id="bd720-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bd720-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="bd720-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bd720-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="bd720-111">PowerShell</span><span class="sxs-lookup"><span data-stu-id="bd720-111">PowerShell</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="bd720-112">**跟进：**  [在删除次要副本之后](#PostBestPractices)</span><span class="sxs-lookup"><span data-stu-id="bd720-112">**Follow Up:**  [After Removing a Secondary Replica](#PostBestPractices)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="bd720-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="bd720-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="bd720-114">限制和局限</span><span class="sxs-lookup"><span data-stu-id="bd720-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="bd720-115">只有主副本支持该任务。</span><span class="sxs-lookup"><span data-stu-id="bd720-115">This task is supported only on the primary replica.</span></span>  
  
-   <span data-ttu-id="bd720-116">从可用性组中仅可删除辅助副本。</span><span class="sxs-lookup"><span data-stu-id="bd720-116">Only a secondary replica can be removed from an availability group.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="bd720-117">先决条件</span><span class="sxs-lookup"><span data-stu-id="bd720-117">Prerequisites</span></span>  
  
-   <span data-ttu-id="bd720-118">您必须连接到承载可用性组的主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="bd720-118">You must be connected to the server instance that hosts the primary replica of the availability group.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="bd720-119">Security</span><span class="sxs-lookup"><span data-stu-id="bd720-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="bd720-120">权限</span><span class="sxs-lookup"><span data-stu-id="bd720-120">Permissions</span></span>  
 <span data-ttu-id="bd720-121">对可用性组要求 ALTER AVAILABILITY GROUP 权限、CONTROL AVAILABILITY GROUP 权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="bd720-121">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="bd720-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bd720-122">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="bd720-123">**删除辅助副本**</span><span class="sxs-lookup"><span data-stu-id="bd720-123">**To remove a secondary replica**</span></span>  
  
1.  <span data-ttu-id="bd720-124">在对象资源管理器中，连接到承载主副本的服务器实例，然后展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="bd720-124">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="bd720-125">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="bd720-125">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="bd720-126">选择可用性组，然后展开 **“可用性副本”** 节点。</span><span class="sxs-lookup"><span data-stu-id="bd720-126">Select the availability group, and expand the **Availability Replicas** node.</span></span>  
  
4.  <span data-ttu-id="bd720-127">此步骤取决于您是要删除多个副本，还是只删除一个副本，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bd720-127">This step depends on whether you want to remove multiple replicas or only one replica, as follows:</span></span>  
  
    -   <span data-ttu-id="bd720-128">若要删除多个副本，请使用 **“对象资源管理器详细信息”** 窗格查看并选择所有要删除的副本。</span><span class="sxs-lookup"><span data-stu-id="bd720-128">To remove multiple replicas, use the **Object Explorer Details** pane to view and select all the replicas that you want to remove.</span></span> <span data-ttu-id="bd720-129">有关详细信息，请参阅[使用对象资源管理器详细信息监视可用性组 (SQL Server Management Studio)](use-object-explorer-details-to-monitor-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="bd720-129">For more information, see [Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md).</span></span>  
  
    -   <span data-ttu-id="bd720-130">若要删除单个副本，请在 **“对象资源管理器”** 窗格或 **“对象资源管理器详细信息”** 窗格中选中此副本。</span><span class="sxs-lookup"><span data-stu-id="bd720-130">To remove a single replica, select it in either the **Object Explorer** pane or the **Object Explorer Details** pane.</span></span>  
  
5.  <span data-ttu-id="bd720-131">右键单击选定的一个或多个次要副本，然后在命令菜单中选择“从可用性组中删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bd720-131">Right-click the selected secondary replica or replicas, and select **Remove from Availability Group** in the command menu.</span></span>  
  
6.  <span data-ttu-id="bd720-132">在 **“从可用性组删除辅助副本”** 对话框中，要删除所有列出的辅助副本，请单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="bd720-132">In the **Remove Secondary Replicas from Availability Group** dialog box, to remove all the listed secondary replicas, click **OK**.</span></span> <span data-ttu-id="bd720-133">如果您不想删除所有列出的副本，请单击 **“取消”**。</span><span class="sxs-lookup"><span data-stu-id="bd720-133">If you do not want to remove all the listed replicas, click **Cancel**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="bd720-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bd720-134">Using Transact-SQL</span></span>  
 <span data-ttu-id="bd720-135">**删除辅助副本**</span><span class="sxs-lookup"><span data-stu-id="bd720-135">**To remove a secondary replica**</span></span>  
  
1.  <span data-ttu-id="bd720-136">连接到承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="bd720-136">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="bd720-137">按如下所示使用 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 语句：</span><span class="sxs-lookup"><span data-stu-id="bd720-137">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="bd720-138">ALTER AVAILABILITY GROUP group_name\*\* REMOVE REPLICA ON 'instance_name**' [,...n**]</span><span class="sxs-lookup"><span data-stu-id="bd720-138">ALTER AVAILABILITY GROUP *group_name* REMOVE REPLICA ON '*instance_name*' [,...*n*]</span></span>  
  
     <span data-ttu-id="bd720-139">其中，group_name\*\* 为可用性组的名称，instance_name\*\* 为该次要副本所在的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="bd720-139">where *group_name* is the name of the availability group and *instance_name* is the server instance where the secondary replica is located.</span></span>  
  
     <span data-ttu-id="bd720-140">下面的示例将次要副本从 *MyAG* 可用性组中删除。</span><span class="sxs-lookup"><span data-stu-id="bd720-140">The following example removes a secondary replica from the *MyAG* availability group.</span></span> <span data-ttu-id="bd720-141">目标次要副本位于名为 COMPUTER02\*\* 的计算机上的服务器实例（名为 HADR_INSTANCE\*\*）上。</span><span class="sxs-lookup"><span data-stu-id="bd720-141">The target secondary replica is located on a server instance named *HADR_INSTANCE* on a computer named *COMPUTER02*.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAG REMOVE REPLICA ON 'COMPUTER02\HADR_INSTANCE';  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="bd720-142">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bd720-142">Using PowerShell</span></span>  
 <span data-ttu-id="bd720-143">**删除辅助副本**</span><span class="sxs-lookup"><span data-stu-id="bd720-143">**To remove a secondary replica**</span></span>  
  
1.  <span data-ttu-id="bd720-144">将目录 (`cd`) 更改为承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="bd720-144">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="bd720-145">使用 **Remove-SqlAvailabilityReplica** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bd720-145">Use the **Remove-SqlAvailabilityReplica** cmdlet.</span></span>  
  
     <span data-ttu-id="bd720-146">例如，下面的命令从名为 `MyReplica` 的可用性组中删除服务器 `MyAg`上的可用性副本。</span><span class="sxs-lookup"><span data-stu-id="bd720-146">For example, the following command removes the availability replica on the server `MyReplica` from the availability group named `MyAg`.</span></span>  <span data-ttu-id="bd720-147">此命令必须在承载可用性组的主副本的服务器实例上运行。</span><span class="sxs-lookup"><span data-stu-id="bd720-147">This command must be run on the server instance that hosts the primary replica of the availability group.</span></span>  
  
    ```powershell
    Remove-SqlAvailabilityReplica -Path SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="bd720-148">若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bd720-148">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="bd720-149">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="bd720-149">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="bd720-150">**设置和使用 SQL Server PowerShell 提供程序**</span><span class="sxs-lookup"><span data-stu-id="bd720-150">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="bd720-151">SQL Server PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="bd720-151">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-after-removing-a-secondary-replica"></a><a name="PostBestPractices"></a> <span data-ttu-id="bd720-152">跟进：在删除辅助副本之后</span><span class="sxs-lookup"><span data-stu-id="bd720-152">Follow Up: After Removing a Secondary Replica</span></span>  
 <span data-ttu-id="bd720-153">如果您指定一个当前不可用的副本，则在该副本联机时，将发现该副本已被删除。</span><span class="sxs-lookup"><span data-stu-id="bd720-153">If you specify a replica that is currently unavailable, when the replica comes online, it will discover that it has been removed.</span></span>  
  
 <span data-ttu-id="bd720-154">删除副本会导致它停止接收数据。</span><span class="sxs-lookup"><span data-stu-id="bd720-154">Removing a replica causes it to stop receiving data.</span></span> <span data-ttu-id="bd720-155">在某个辅助副本确认其已从全局存储中删除之后，该副本将从其数据库（在本地服务器实例上保留为 RECOVERING 状态）中删除可用性组设置。</span><span class="sxs-lookup"><span data-stu-id="bd720-155">After a secondary replica confirms that it has been removed from the global store, the replica removes the availability group settings from its databases, which remain on the local server instance in the RECOVERING state.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd720-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bd720-156">See Also</span></span>  
 <span data-ttu-id="bd720-157">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bd720-157">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="bd720-158">[将辅助副本添加到可用性组 &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bd720-158">[Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md) </span></span>  
 [<span data-ttu-id="bd720-159">删除可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bd720-159">Remove an Availability Group &#40;SQL Server&#41;</span></span>](remove-an-availability-group-sql-server.md)  
