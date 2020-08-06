---
title: 更改可用性副本的会话超时期限 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], session timeout
- session timeout [SQL Server]
ms.assetid: e23c6e06-1cd1-4d4a-9bc2-e3e06ab2933d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 302ba4a2b0b72a70b05e563eb4085913074469eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693494"
---
# <a name="change-the-session-timeout-period-for-an-availability-replica-sql-server"></a><span data-ttu-id="8d188-102">更改可用性副本的会话超时期限 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8d188-102">Change the Session-Timeout Period for an Availability Replica (SQL Server)</span></span>
  <span data-ttu-id="8d188-103">本主题介绍如何通过在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]或 PowerShell 来配置 AlwaysOn 可用性副本的会话超时期限。</span><span class="sxs-lookup"><span data-stu-id="8d188-103">This topic describes how to configure the session-timeout period of an AlwaysOn availability replica by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="8d188-104">会话超时期限是一个副本属性，用来控制可用性副本等待已连接副本的 ping 响应的时间（秒数），超过该期限则认为连接已失败。</span><span class="sxs-lookup"><span data-stu-id="8d188-104">The session-timeout period is a replica property that controls how many seconds (in seconds) that an availability replica waits for a ping response from a connected replica before considering the connection to have failed.</span></span> <span data-ttu-id="8d188-105">默认情况下，副本等待 ping 响应的时长为 10 秒钟。</span><span class="sxs-lookup"><span data-stu-id="8d188-105">By default, a replica waits 10 seconds for a ping response.</span></span> <span data-ttu-id="8d188-106">此副本属性仅适用于可用性组的给定辅助副本与主副本之间的连接。</span><span class="sxs-lookup"><span data-stu-id="8d188-106">This replica property applies only the connection between a given secondary replica and the primary replica of the availability group.</span></span> <span data-ttu-id="8d188-107">有关会话超时期限的详细信息，请参阅 [AlwaysOn 可用性组概述 (SQL Server)](overview-of-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="8d188-107">For more information about the session-timeout period, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="8d188-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="8d188-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8d188-109">先决条件</span><span class="sxs-lookup"><span data-stu-id="8d188-109">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="8d188-110">建议</span><span class="sxs-lookup"><span data-stu-id="8d188-110">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="8d188-111">安全性</span><span class="sxs-lookup"><span data-stu-id="8d188-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8d188-112">**若要更改会话超时期限，可使用：**</span><span class="sxs-lookup"><span data-stu-id="8d188-112">**To change the session-timeout period, using:**</span></span>  
  
     [<span data-ttu-id="8d188-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8d188-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="8d188-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8d188-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="8d188-115">PowerShell</span><span class="sxs-lookup"><span data-stu-id="8d188-115">PowerShell</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8d188-116">开始之前</span><span class="sxs-lookup"><span data-stu-id="8d188-116">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="8d188-117">先决条件</span><span class="sxs-lookup"><span data-stu-id="8d188-117">Prerequisites</span></span>  
  
-   <span data-ttu-id="8d188-118">您必须连接到承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="8d188-118">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="8d188-119">建议</span><span class="sxs-lookup"><span data-stu-id="8d188-119">Recommendations</span></span>  
 <span data-ttu-id="8d188-120">我们建议您将超时期限保持为 10 秒或更长。</span><span class="sxs-lookup"><span data-stu-id="8d188-120">We recommend that you keep the time-out period at 10 seconds or greater.</span></span> <span data-ttu-id="8d188-121">如果将值设置为低于 10 秒，则可能使高负荷系统丢失 PING 并声明错误故障。</span><span class="sxs-lookup"><span data-stu-id="8d188-121">Setting the value to less than 10 seconds creates the possibility of a heavily loaded system missing PINGs and declaring a false failure.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8d188-122">Security</span><span class="sxs-lookup"><span data-stu-id="8d188-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8d188-123">权限</span><span class="sxs-lookup"><span data-stu-id="8d188-123">Permissions</span></span>  
 <span data-ttu-id="8d188-124">对可用性组要求 ALTER AVAILABILITY GROUP 权限、CONTROL AVAILABILITY GROUP 权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="8d188-124">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8d188-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8d188-125">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="8d188-126">**更改可用性副本的会话超时期限**</span><span class="sxs-lookup"><span data-stu-id="8d188-126">**To change the session-timeout period for an availability replica**</span></span>  
  
1.  <span data-ttu-id="8d188-127">在对象资源管理器中，连接到承载主副本的服务器实例，然后展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="8d188-127">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="8d188-128">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="8d188-128">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="8d188-129">单击要配置其可用性副本的可用性组。</span><span class="sxs-lookup"><span data-stu-id="8d188-129">Click the availability group whose availability replica you want to configure.</span></span>  
  
4.  <span data-ttu-id="8d188-130">右键单击要配置的副本，然后单击 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="8d188-130">Right-click the replica to be configured, and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="8d188-131">在 **“可用性副本属性”** 对话框中，使用 **“会话超时（秒）”** 字段更改此副本的会话超时期限的秒数。</span><span class="sxs-lookup"><span data-stu-id="8d188-131">In the **Availability Replica Properties** dialog box, use the **Session timeout (seconds)** field to change the number of seconds for the session-timeout period on this replica.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="8d188-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8d188-132">Using Transact-SQL</span></span>  
 <span data-ttu-id="8d188-133">**更改可用性副本的会话超时期限**</span><span class="sxs-lookup"><span data-stu-id="8d188-133">**To change the session-timeout period for an availability replica**</span></span>  
  
1.  <span data-ttu-id="8d188-134">连接到承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="8d188-134">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="8d188-135">按如下所示使用 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 语句：</span><span class="sxs-lookup"><span data-stu-id="8d188-135">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="8d188-136">ALTER AVAILABILITY GROUP *group_name*</span><span class="sxs-lookup"><span data-stu-id="8d188-136">ALTER AVAILABILITY GROUP *group_name*</span></span>  
  
     <span data-ttu-id="8d188-137">MODIFY REPLICA ON '*instance_name*' WITH ( SESSION_TIMEOUT =*seconds* )</span><span class="sxs-lookup"><span data-stu-id="8d188-137">MODIFY REPLICA ON '*instance_name*' WITH ( SESSION_TIMEOUT =*seconds* )</span></span>  
  
     <span data-ttu-id="8d188-138">其中， *group_name* 是可用性组的名称， *instance_name* 是承载要修改的可用性副本的服务器实例的名称， *seconds* 指定该副本在充当次要副本时将日志应用到数据库之前必须等待的最少秒数。</span><span class="sxs-lookup"><span data-stu-id="8d188-138">where *group_name* is the name of the availability group, *instance_name* is the name of the server instance that hosts the availability replica to be modified, and *seconds* specifies the minimum number of seconds that the replica must wait before applying log to databases when acting as a secondary replica.</span></span> <span data-ttu-id="8d188-139">默认值为 0 秒，指示无应用延迟。</span><span class="sxs-lookup"><span data-stu-id="8d188-139">The default is 0 seconds, which indicates that there is no apply delay.</span></span>  
  
     <span data-ttu-id="8d188-140">在 `AccountsAG` 可用性组的主副本上输入的以下示例，将 `15` 服务器实例上的副本的会话超时值更改为 `INSTANCE09` 秒。</span><span class="sxs-lookup"><span data-stu-id="8d188-140">The following example, entered on the primary replica of the `AccountsAG` availability group, changes the session-timeout value to `15` seconds for the replica located on the `INSTANCE09` server instance.</span></span>  
  
    ```  
    ALTER AVAILABILITY GROUP AccountsAG   
       MODIFY REPLICA ON 'INSTANCE09' WITH (SESSION_TIMEOUT = 15);  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="8d188-141">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8d188-141">Using PowerShell</span></span>  

### <a name="to-change-the-session-timeout-period-for-an-availability-replica"></a><span data-ttu-id="8d188-142">更改可用性副本的会话超时期限</span><span class="sxs-lookup"><span data-stu-id="8d188-142">To change the session-timeout period for an availability replica</span></span>
  
1.  <span data-ttu-id="8d188-143">将目录 (`cd`) 更改为承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="8d188-143">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="8d188-144">使用 `Set-SqlAvailabilityReplica` cmdlet 和 `SessionTimeout` 参数，更改指定的可用性副本上的会话超时期限的秒数。</span><span class="sxs-lookup"><span data-stu-id="8d188-144">Use the `Set-SqlAvailabilityReplica` cmdlet with the `SessionTimeout` parameter to change the number of seconds for the session-timeout period on a specified availability replica.</span></span>  
  
     <span data-ttu-id="8d188-145">例如，以下命令将会话超时期限设置为 15 秒。</span><span class="sxs-lookup"><span data-stu-id="8d188-145">For example, the following command sets the session-timeout period to 15 seconds.</span></span>  
  
    ```powershell
    Set-SqlAvailabilityReplica -SessionTimeout 15 -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="8d188-146">若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8d188-146">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="8d188-147">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="8d188-147">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="8d188-148">若要设置并使用 SQL Server PowerShell 提供程序，请参阅[SQL Server PowerShell 提供程序](../../../powershell/sql-server-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="8d188-148">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8d188-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8d188-149">See Also</span></span>  
 [<span data-ttu-id="8d188-150">AlwaysOn 可用性组 &#40;SQL Server 概述&#41;</span><span class="sxs-lookup"><span data-stu-id="8d188-150">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
