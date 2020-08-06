---
title: 更改可用性副本的故障转移模式 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover modes [SQL Server]
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], failover modes
- Availability Groups [SQL Server], configuring
ms.assetid: 619a826f-8e65-48eb-8c34-39497d238279
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d946440e2950192299c42652babb4082790dbd03
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693497"
---
# <a name="change-the-failover-mode-of-an-availability-replica-sql-server"></a><span data-ttu-id="9806c-102">更改可用性副本的故障转移模式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9806c-102">Change the Failover Mode of an Availability Replica (SQL Server)</span></span>
  <span data-ttu-id="9806c-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或 PowerShell 更改 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中 AlwaysOn 可用性组的可用性副本的故障转移模式。</span><span class="sxs-lookup"><span data-stu-id="9806c-103">This topic describes how to change the failover mode of an availability replica in an AlwaysOn availability group in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell.</span></span> <span data-ttu-id="9806c-104">故障转移模式是一个副本属性，用于确定在同步提交可用性模式下运行的副本的故障转移模式。</span><span class="sxs-lookup"><span data-stu-id="9806c-104">The failover mode is a replica property that determines the failover mode for replicas that run under synchronous-commit availability mode.</span></span> <span data-ttu-id="9806c-105">有关详细信息，请参阅[故障转移和故障转移模式（AlwaysOn 可用性组）](failover-and-failover-modes-always-on-availability-groups.md)和[可用性模式（AlwaysOn 可用性组）](availability-modes-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="9806c-105">For more information, see [Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;](failover-and-failover-modes-always-on-availability-groups.md) and [Availability Modes &#40;AlwaysOn Availability Groups&#41;](availability-modes-always-on-availability-groups.md).</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9806c-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="9806c-106">Before You Begin</span></span>  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="9806c-107">先决条件和限制</span><span class="sxs-lookup"><span data-stu-id="9806c-107">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="9806c-108">只有主副本支持该任务。</span><span class="sxs-lookup"><span data-stu-id="9806c-108">This task is supported only on primary replicas.</span></span> <span data-ttu-id="9806c-109">您必须连接到承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="9806c-109">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
-   <span data-ttu-id="9806c-110">SQL Server 故障转移群集实例 (FCI) 不支持通过可用性组来自动进行故障转移，因此，只能为手动故障转移配置任何由 FCI 承载的可用性副本。</span><span class="sxs-lookup"><span data-stu-id="9806c-110">SQL Server Failover Cluster Instances (FCIs) do not support automatic failover by availability groups, so any availability replica that is hosted by an FCI can only be configured for manual failover.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9806c-111">Security</span><span class="sxs-lookup"><span data-stu-id="9806c-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9806c-112">权限</span><span class="sxs-lookup"><span data-stu-id="9806c-112">Permissions</span></span>  
 <span data-ttu-id="9806c-113">对可用性组要求 ALTER AVAILABILITY GROUP 权限、CONTROL AVAILABILITY GROUP 权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="9806c-113">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9806c-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9806c-114">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="9806c-115">**更改可用性副本的故障转移模式**</span><span class="sxs-lookup"><span data-stu-id="9806c-115">**To change the failover mode of an availability replica**</span></span>  
  
1.  <span data-ttu-id="9806c-116">在对象资源管理器中，连接到承载主副本的服务器实例，然后展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="9806c-116">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="9806c-117">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="9806c-117">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="9806c-118">单击要更改其副本的可用性组。</span><span class="sxs-lookup"><span data-stu-id="9806c-118">Click the availability group whose replica you want to change.</span></span>  
  
4.  <span data-ttu-id="9806c-119">右键单击该副本，然后单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="9806c-119">Right-click the replica, and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="9806c-120">在 **“可用性副本属性”** 对话框中，使用 **“故障转移模式”** 下拉列表更改此副本的故障转移模式。</span><span class="sxs-lookup"><span data-stu-id="9806c-120">In the **Availability Replica Properties** dialog box, use the **Failover mode** drop list to change the failover mode of this replica.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9806c-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9806c-121">Using Transact-SQL</span></span>  
 <span data-ttu-id="9806c-122">**更改可用性副本的故障转移模式**</span><span class="sxs-lookup"><span data-stu-id="9806c-122">**To change the failover mode of an availability replica**</span></span>  
  
1.  <span data-ttu-id="9806c-123">连接到承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="9806c-123">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="9806c-124">按如下所示使用 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 语句：</span><span class="sxs-lookup"><span data-stu-id="9806c-124">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="9806c-125">ALTER AVAILABILITY GROUP *group_name* MODIFY REPLICA ON '*server_name*'</span><span class="sxs-lookup"><span data-stu-id="9806c-125">ALTER AVAILABILITY GROUP *group_name* MODIFY REPLICA ON '*server_name*'</span></span>  
  
     <span data-ttu-id="9806c-126">WITH ( {</span><span class="sxs-lookup"><span data-stu-id="9806c-126">WITH ( {</span></span>  
  
     <span data-ttu-id="9806c-127">AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }</span><span class="sxs-lookup"><span data-stu-id="9806c-127">AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }</span></span>  
  
     <span data-ttu-id="9806c-128">| FAILOVER_MODE = { AUTOMATIC | MANUAL }</span><span class="sxs-lookup"><span data-stu-id="9806c-128">| FAILOVER_MODE = { AUTOMATIC | MANUAL }</span></span>  
  
     <span data-ttu-id="9806c-129">}  )</span><span class="sxs-lookup"><span data-stu-id="9806c-129">}  )</span></span>  
  
     <span data-ttu-id="9806c-130">其中</span><span class="sxs-lookup"><span data-stu-id="9806c-130">where</span></span>  
  
    -   <span data-ttu-id="9806c-131">其中，*group_name* 是可用性组的名称。</span><span class="sxs-lookup"><span data-stu-id="9806c-131">*group_name* is the name of the availability group.</span></span>  
  
    -   <span data-ttu-id="9806c-132">{ '*system_name*[\\*instance_name*]' | '*FCI_network_name*[\\*instance_name*]' }</span><span class="sxs-lookup"><span data-stu-id="9806c-132">{ '*system_name*[\\*instance_name*]' | '*FCI_network_name*[\\*instance_name*]' }</span></span>  
  
         <span data-ttu-id="9806c-133">指定承载要更改的可用性副本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的地址。</span><span class="sxs-lookup"><span data-stu-id="9806c-133">Specifies the address of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the availability replica to be altered.</span></span> <span data-ttu-id="9806c-134">此地址由以下部分组成：</span><span class="sxs-lookup"><span data-stu-id="9806c-134">The components of this address are as follows:</span></span>  
  
         <span data-ttu-id="9806c-135">*system_name*</span><span class="sxs-lookup"><span data-stu-id="9806c-135">*system_name*</span></span>  
         <span data-ttu-id="9806c-136">为独立服务器实例所在的计算机系统的 NetBIOS 名称。</span><span class="sxs-lookup"><span data-stu-id="9806c-136">Is the NetBIOS name of the computer system on which a stand-alone server instance resides.</span></span>  
  
         <span data-ttu-id="9806c-137">*FCI_network_name*</span><span class="sxs-lookup"><span data-stu-id="9806c-137">*FCI_network_name*</span></span>  
         <span data-ttu-id="9806c-138">为用于访问 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 故障转移群集的网络名称，在此群集中目标服务器实例为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 故障转移伙伴 (FCI)。</span><span class="sxs-lookup"><span data-stu-id="9806c-138">Is the network name that is used to access a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster in which a target server instance is a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover partner (an FCI).</span></span>  
  
         <span data-ttu-id="9806c-139">*instance_name*</span><span class="sxs-lookup"><span data-stu-id="9806c-139">*instance_name*</span></span>  
         <span data-ttu-id="9806c-140">为承载目标可用性副本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="9806c-140">Is the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the target availability replica.</span></span> <span data-ttu-id="9806c-141">对于默认服务器实例， *instance_name* 是可选的。</span><span class="sxs-lookup"><span data-stu-id="9806c-141">For a default server instance, *instance_name* is optional.</span></span>  
  
     <span data-ttu-id="9806c-142">有关这些参数的详细信息，请参阅 [ALTER AVAILABILITY GROUP (Transact-SQL)](/sql/t-sql/statements/alter-availability-group-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9806c-142">For more information about these parameters, see [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql).</span></span>  
  
     <span data-ttu-id="9806c-143">以下示例（在 *MyAG* 可用性组的主要副本上输入）在可用性副本上（位于名为 *COMPUTER01*的计算机的默认服务器实例上）将故障转移模式更改为自动故障转移。</span><span class="sxs-lookup"><span data-stu-id="9806c-143">The following example, entered on the primary replica of the *MyAG* availability group, changes the failover mode to automatic failover on the availability replica that is located on the default server instance on a computer named *COMPUTER01*.</span></span>  
  
    ```  
    ALTER AVAILABILITY GROUP MyAG MODIFY REPLICA ON 'COMPUTER01' WITH  
       (FAILOVER_MODE = AUTOMATIC);  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="9806c-144">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9806c-144">Using PowerShell</span></span>  

### <a name="to-change-the-failover-mode-of-an-availability-replica"></a><span data-ttu-id="9806c-145">更改可用性副本的故障转移模式</span><span class="sxs-lookup"><span data-stu-id="9806c-145">To change the failover mode of an availability replica</span></span>
  
1.  <span data-ttu-id="9806c-146">将目录 (`cd`) 更改为承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="9806c-146">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="9806c-147">将 `Set-SqlAvailabilityReplica` cmdlet 与 `FailoverMode` 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="9806c-147">Use the `Set-SqlAvailabilityReplica` cmdlet with the `FailoverMode` parameter.</span></span> <span data-ttu-id="9806c-148">在将某一副本设置为自动故障转移时，您可能需要使用 `AvailabilityMode` 参数将该副本更改为同步提交可用性模式。</span><span class="sxs-lookup"><span data-stu-id="9806c-148">When setting a replica to automatic failover, you might need to use the `AvailabilityMode` parameter to change the replica to synchronous-commit availability mode.</span></span>  
  
     <span data-ttu-id="9806c-149">例如，以下命令将修改可用性组 `MyReplica` 中的副本 `MyAg` 以使用同步提交可用性模式和支持自动故障转移。</span><span class="sxs-lookup"><span data-stu-id="9806c-149">For example, the following command modifies the replica `MyReplica` in the availability group `MyAg` to use synchronous-commit availability mode and to support automatic failover.</span></span>  
  
    ```powershell
    Set-SqlAvailabilityReplica -AvailabilityMode "SynchronousCommit" -FailoverMode "Automatic" `
     -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\Replicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="9806c-150">若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9806c-150">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="9806c-151">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="9806c-151">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="9806c-152">若要设置并使用 SQL Server PowerShell 提供程序，请参阅[SQL Server PowerShell 提供程序](../../../powershell/sql-server-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="9806c-152">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9806c-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9806c-153">See Also</span></span>  
 [<span data-ttu-id="9806c-154">AlwaysOn 可用性组 &#40;SQL Server 概述&#41;</span><span class="sxs-lookup"><span data-stu-id="9806c-154">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
 <span data-ttu-id="9806c-155">[可用性模式 &#40;AlwaysOn 可用性组&#41;](availability-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="9806c-155">[Availability Modes &#40;AlwaysOn Availability Groups&#41;](availability-modes-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="9806c-156">故障转移和故障转移模式 &#40;AlwaysOn 可用性组&#41;</span><span class="sxs-lookup"><span data-stu-id="9806c-156">Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;</span></span>](failover-and-failover-modes-always-on-availability-groups.md) 
