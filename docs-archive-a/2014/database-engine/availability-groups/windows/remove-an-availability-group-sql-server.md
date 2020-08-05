---
title: 删除可用性组 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.deleteag.f1
helpviewer_keywords:
- Availability Groups [SQL Server], removing
- Availability Groups [SQL Server], dropping
ms.assetid: 4b7f7f62-43a3-49db-a72e-22d4d7c2ddbb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c17b7d5b362d8b4030d66ebf7ba0e425495410e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579792"
---
# <a name="remove-an-availability-group-sql-server"></a><span data-ttu-id="83403-102">删除可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="83403-102">Remove an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="83403-103">本主题说明如何使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../../includes/tsql-md.md)] 或 PowerShell 在 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 中删除 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="83403-103">This topic describes how to delete (drop) an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="83403-104">如果在删除某一可用性组时承载可用性副本之一的服务器实例处于脱机状态，则在联机后，该服务器实例将删除本地可用性副本。</span><span class="sxs-lookup"><span data-stu-id="83403-104">If a server instance that hosts one of the availability replicas is offline when you delete an availability group, after coming online, the server instance will drop the local availability replica.</span></span> <span data-ttu-id="83403-105">删除可用性组时，将删除任何关联的可用性组侦听器。</span><span class="sxs-lookup"><span data-stu-id="83403-105">Dropping an availability group deletes any associated availability group listener.</span></span>  
  
 <span data-ttu-id="83403-106">请注意，如果需要，您可以从拥有某一可用性组的正确安全凭据的任何 Windows Server 故障转移群集 (WSFC) 节点删除该可用性组。</span><span class="sxs-lookup"><span data-stu-id="83403-106">Note that, if necessary, you can drop an availability group from any Windows Server Failover Clustering (WSFC) node that possesses the correct security credentials for the availability group.</span></span> <span data-ttu-id="83403-107">因此，在某一可用性组未保留任何可用性副本时，您可以删除该可用性组。</span><span class="sxs-lookup"><span data-stu-id="83403-107">This enables you to delete an availability group when none of its availability replicas remain.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="83403-108">如果可能，请仅在连接到承载主副本的服务器实例时删除此可用性组。</span><span class="sxs-lookup"><span data-stu-id="83403-108">If possible, remove the availability group only while connected to the server instance that hosts the primary replica.</span></span> <span data-ttu-id="83403-109">从主副本中删除此可用性组时，允许对以前的主数据库进行更改（不具有高可用性保护）。</span><span class="sxs-lookup"><span data-stu-id="83403-109">When the availability group is dropped from the primary replica, changes are allowed in the former primary databases (without high availability protection).</span></span> <span data-ttu-id="83403-110">从辅助副本中删除可用性组会使主副本处于 RESTORING 状态，且不允许对此数据库进行更改。</span><span class="sxs-lookup"><span data-stu-id="83403-110">Deleting an availability group from a secondary replica leaves the primary replica in the RESTORING state, and changes are not allowed on the databases.</span></span>  
  
-   <span data-ttu-id="83403-111">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="83403-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="83403-112">限制和建议</span><span class="sxs-lookup"><span data-stu-id="83403-112">Limitations and Recommendations</span></span>](#Restrictions)  
  
     [<span data-ttu-id="83403-113">安全性</span><span class="sxs-lookup"><span data-stu-id="83403-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="83403-114">**删除可用性组，使用：**</span><span class="sxs-lookup"><span data-stu-id="83403-114">**To delete an availability group, using:**</span></span>  
  
     [<span data-ttu-id="83403-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="83403-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="83403-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="83403-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="83403-117">PowerShell</span><span class="sxs-lookup"><span data-stu-id="83403-117">PowerShell</span></span>](#PowerShellProcedure)  
  
-   [<span data-ttu-id="83403-118">相关内容</span><span class="sxs-lookup"><span data-stu-id="83403-118">Related Content</span></span>](#RelatedContent)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="83403-119">开始之前</span><span class="sxs-lookup"><span data-stu-id="83403-119">Before You Begin</span></span>  
  
###  <a name="limitations-and-recommendations"></a><a name="Restrictions"></a><span data-ttu-id="83403-120">限制和建议</span><span class="sxs-lookup"><span data-stu-id="83403-120">Limitations and Recommendations</span></span>  
  
-   <span data-ttu-id="83403-121">当可用性组处于联机状态时，从辅助副本删除它会导致主副本转换为 RESTORING 状态。</span><span class="sxs-lookup"><span data-stu-id="83403-121">When the availability group is online, deleting it from a secondary replica causes the primary replica to transition to the RESTORING state.</span></span> <span data-ttu-id="83403-122">因此，如果可能，请仅从承载主副本的服务器实例中删除此可用性组。</span><span class="sxs-lookup"><span data-stu-id="83403-122">Therefore, if possible, remove the availability group only from the server instance that hosts the primary replica.</span></span>  
  
-   <span data-ttu-id="83403-123">如果您从已被 WSFC 故障转移群集删除或逐出的计算机删除某一可用性组，则该可用性组仅在本地删除。</span><span class="sxs-lookup"><span data-stu-id="83403-123">If you delete an availability group from a computer that has been removed or evicted from the WSFC failover cluster, the availability group is only deleted locally.</span></span>  
  
-   <span data-ttu-id="83403-124">如果 Windows Server 故障转移群集 (WSFC) 群集没有仲裁，则避免删除可用性组。</span><span class="sxs-lookup"><span data-stu-id="83403-124">Avoid dropping an availability group when the Windows Server Failover Clustering (WSFC) cluster has no quorum.</span></span> <span data-ttu-id="83403-125">如果在群集缺少仲裁时必须删除可用性组，则不删除群集中存储的元数据可用性组。</span><span class="sxs-lookup"><span data-stu-id="83403-125">If you must drop an availability group while the cluster lacks quorum, the metadata availability group that is stored in the cluster is not removed.</span></span> <span data-ttu-id="83403-126">在群集重新获得仲裁后，将需要再次删除此可用性组以便将其从 WSFC 群集中删除。</span><span class="sxs-lookup"><span data-stu-id="83403-126">After the cluster regains quorum, you will need to drop the availability group again to remove it from the WSFC cluster.</span></span>  
  
-   <span data-ttu-id="83403-127">在辅助副本上，DROP AVAILABILITY GROUP 应仅用于紧急情况。</span><span class="sxs-lookup"><span data-stu-id="83403-127">On a secondary replica, DROP AVAILABILITY GROUP should only be used only for emergency purposes.</span></span> <span data-ttu-id="83403-128">这是因为删除可用性组会使该可用性组脱机。</span><span class="sxs-lookup"><span data-stu-id="83403-128">This is because dropping an availability group takes the availability group offline.</span></span> <span data-ttu-id="83403-129">如果您从辅助副本中删除该可用性组，则主副本无法确定出现 OFFLINE 状态是因为仲裁丢失、强制故障转移还是 DROP AVAILABILITY GROUP 命令。</span><span class="sxs-lookup"><span data-stu-id="83403-129">If you drop the availability group from a secondary replica, the primary replica cannot determine whether the OFFLINE state occurred because of quorum loss, a forced failover, or a DROP AVAILABILITY GROUP command.</span></span> <span data-ttu-id="83403-130">主副本将转换为 RESTORING 状态以避免出现可能的裂脑情况。</span><span class="sxs-lookup"><span data-stu-id="83403-130">The primary replica transitions to the RESTORING state to prevent a possible split-brain situation.</span></span> <span data-ttu-id="83403-131">有关详细信息，请参阅 [工作方式：DROP AVAILABILITY GROUP 行为](https://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) （CSS SQL Server 工程师博客）。</span><span class="sxs-lookup"><span data-stu-id="83403-131">For more information, see [How It Works: DROP AVAILABILITY GROUP Behaviors](https://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) (CSS SQL Server Engineers blog).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="83403-132">Security</span><span class="sxs-lookup"><span data-stu-id="83403-132">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="83403-133">权限</span><span class="sxs-lookup"><span data-stu-id="83403-133">Permissions</span></span>  
 <span data-ttu-id="83403-134">对可用性组要求 ALTER AVAILABILITY GROUP 权限、CONTROL AVAILABILITY GROUP 权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="83403-134">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span> <span data-ttu-id="83403-135">若要删除并非由本地服务器实例承载的某一可用性组，您需要针对该可用性组的 CONTROL SERVER 权限或 CONTROL 权限。</span><span class="sxs-lookup"><span data-stu-id="83403-135">To drop an availability group that is not hosted by the local server instance you need CONTROL SERVER permission or CONTROL permission on that Availability Group.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="83403-136">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="83403-136">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="83403-137">**删除可用性组**</span><span class="sxs-lookup"><span data-stu-id="83403-137">**To delete an availability group**</span></span>  
  
1.  <span data-ttu-id="83403-138">在对象资源管理器中，连接到承载主副本的服务器实例，如果可能，还可以连接到 WSFC 节点（该节点拥有可用性组的正确安全凭据）上为 AlwaysOn 可用性组启用的另一个服务器实例。</span><span class="sxs-lookup"><span data-stu-id="83403-138">In Object Explorer, connect to the server instance that hosts primary replica, if possible, or connect to another server instance that is enabled for AlwaysOn Availability Groups on a WSFC node that possess the correct security credentials for the availability group.</span></span> <span data-ttu-id="83403-139">展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="83403-139">Expand the server tree.</span></span>  
  
2.  <span data-ttu-id="83403-140">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="83403-140">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="83403-141">此步骤取决于您是要删除多个可用性组还是只删除一个可用性组，如下所示：</span><span class="sxs-lookup"><span data-stu-id="83403-141">This step depends on whether you want to delete multiple availability groups or only one availability group, as follows:</span></span>  
  
    -   <span data-ttu-id="83403-142">若要删除多个可用性组（其主要副本位于连接的服务器实例上），请使用“对象资源管理器详细信息”\*\*\*\* 窗格查看和选择要删除的所有可用性组。</span><span class="sxs-lookup"><span data-stu-id="83403-142">To delete multiple availability groups (whose primary replicas are on the connected server instance), use the **Object Explorer Details** pane to view and select all the availability groups that you want to delete.</span></span> <span data-ttu-id="83403-143">有关详细信息，请参阅[使用对象资源管理器详细信息监视可用性组 (SQL Server Management Studio)](use-object-explorer-details-to-monitor-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="83403-143">For more information, see [Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md).</span></span>  
  
    -   <span data-ttu-id="83403-144">若要删除单个可用性组，请在 **“对象资源管理器”** 窗格或 **“对象资源管理器详细信息”** 窗格中选择它。</span><span class="sxs-lookup"><span data-stu-id="83403-144">To delete a single availability group, select it in either the **Object Explorer** pane or the **Object Explorer Details** pane.</span></span>  
  
4.  <span data-ttu-id="83403-145">右键单击所选的可用性组，然后选择“删除”\*\*\*\* 命令。</span><span class="sxs-lookup"><span data-stu-id="83403-145">Right-click the selected availability group or groups, and select the **Delete** command.</span></span>  
  
5.  <span data-ttu-id="83403-146">在 **“删除可用性组”** 对话框中，若要删除所有列出的可用性组，请单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="83403-146">In the **Remove Availability Group** dialog box, to delete all the listed availability groups, click **OK**.</span></span> <span data-ttu-id="83403-147">如果您不想删除所有列出的可用性组，请单击 **“取消”**。</span><span class="sxs-lookup"><span data-stu-id="83403-147">If you do not want to remove all the listed availability groups, click **Cancel**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="83403-148">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="83403-148">Using Transact-SQL</span></span>  
 <span data-ttu-id="83403-149">**删除可用性组**</span><span class="sxs-lookup"><span data-stu-id="83403-149">**To delete an availability group**</span></span>  
  
1.  <span data-ttu-id="83403-150">连接到承载主副本的服务器实例，如果可能，还可以连接到 WSFC 节点（该节点拥有可用性组的正确安全凭据）上为 AlwaysOn 可用性组启用的另一个服务器实例。</span><span class="sxs-lookup"><span data-stu-id="83403-150">Connect to the server instance that hosts the primary replica, if possible, or connect to another server instance that is enabled for AlwaysOn Availability Groups on a WSFC node that possess the correct security credentials for the availability group.</span></span>  
  
2.  <span data-ttu-id="83403-151">按如下所示使用 [DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql) 语句</span><span class="sxs-lookup"><span data-stu-id="83403-151">Use the [DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql) statement, as follows</span></span>  
  
     <span data-ttu-id="83403-152">DROP AVAILABILITY GROUP *group_name*</span><span class="sxs-lookup"><span data-stu-id="83403-152">DROP AVAILABILITY GROUP *group_name*</span></span>  
  
     <span data-ttu-id="83403-153">其中， *group_name* 是要删除的可用性组的名称。</span><span class="sxs-lookup"><span data-stu-id="83403-153">where *group_name* is the name of the availability group to be dropped.</span></span>  
  
     <span data-ttu-id="83403-154">下面的示例将删除 `MyAG` 可用性组。</span><span class="sxs-lookup"><span data-stu-id="83403-154">The following example deletes the `MyAG` availability group.</span></span>  
  
    ```sql
    DROP AVAILABILITY GROUP MyAG;  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="83403-155">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="83403-155">Using PowerShell</span></span>  
 <span data-ttu-id="83403-156">**删除可用性组**</span><span class="sxs-lookup"><span data-stu-id="83403-156">**To delete an availability group**</span></span>  
  
 <span data-ttu-id="83403-157">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 提供程序中：</span><span class="sxs-lookup"><span data-stu-id="83403-157">In the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell provider:</span></span>  
  
1.  <span data-ttu-id="83403-158">将目录切换 (`cd`) 到承载主副本的服务器实例，如果可能，还可以切换到 WSFC 节点（该节点拥有可用性组的正确安全凭据）上为 AlwaysOn 可用性组启用的另一个服务器实例。</span><span class="sxs-lookup"><span data-stu-id="83403-158">Change directory (`cd`) to the server instance that hosts the primary replica, if possible, or connect to another server instance that is enabled for AlwaysOn Availability Groups on a WSFC node that possess the correct security credentials for the availability group.</span></span>  
  
2.  <span data-ttu-id="83403-159">使用 **Remove-SqlAvailabilityGroup** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="83403-159">Use the **Remove-SqlAvailabilityGroup** cmdlet.</span></span>  
  
     <span data-ttu-id="83403-160">例如，下面的命令删除名为 `MyAg`的可用性组。</span><span class="sxs-lookup"><span data-stu-id="83403-160">For example, the following command removes the availability group named `MyAg`.</span></span> <span data-ttu-id="83403-161">可以对承载可用性组的可用性副本的任何服务器实例执行此命令。</span><span class="sxs-lookup"><span data-stu-id="83403-161">This command can be executed on any server instance that hosts an availability replica for the availability group.</span></span>  
  
    ```powershell
    Remove-SqlAvailabilityGroup -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="83403-162">若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="83403-162">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="83403-163">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="83403-163">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="83403-164">**设置和使用 SQL Server PowerShell 提供程序**</span><span class="sxs-lookup"><span data-stu-id="83403-164">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="83403-165">SQL Server PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="83403-165">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="83403-166">相关内容</span><span class="sxs-lookup"><span data-stu-id="83403-166">Related Content</span></span>  
  
-   <span data-ttu-id="83403-167">[工作方式：DROP AVAILABILITY GROUP 行为](https://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) （CSS SQL Server 工程师博客）</span><span class="sxs-lookup"><span data-stu-id="83403-167">[How It Works: DROP AVAILABILITY GROUP Behaviors](https://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) (CSS SQL Server Engineers blog)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83403-168">另请参阅</span><span class="sxs-lookup"><span data-stu-id="83403-168">See Also</span></span>  
 <span data-ttu-id="83403-169">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="83403-169">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="83403-170">创建和配置可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="83403-170">Creation and Configuration of Availability Groups &#40;SQL Server&#41;</span></span>](creation-and-configuration-of-availability-groups-sql-server.md)  
