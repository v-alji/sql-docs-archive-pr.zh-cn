---
title: 配置灵活的故障转移策略，以控制 Always On 可用性组的自动故障转移 (的条件) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], flexible failover policy
- Availability Groups [SQL Server], failover
- failover [SQL Server], AlwaysOn Availability Groups
ms.assetid: 1ed564b4-9835-4245-ae35-9ba67419a4ce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c938624a3ed39fe2d41f21a21af5231aa76a8c17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693114"
---
# <a name="configure-the-flexible-failover-policy-to-control-conditions-for-automatic-failover-always-on-availability-groups"></a><span data-ttu-id="49b65-102">配置灵活的故障转移策略以控制自动故障转移的条件（Always On 可用性组）</span><span class="sxs-lookup"><span data-stu-id="49b65-102">Configure the Flexible Failover Policy to Control Conditions for Automatic Failover (Always On Availability Groups)</span></span>
  <span data-ttu-id="49b65-103">本主题介绍如何在 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 中使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]或 PowerShell 为 AlwaysOn 可用性组配置灵活故障转移策略。</span><span class="sxs-lookup"><span data-stu-id="49b65-103">This topic describes how to configure the flexible failover policy for an AlwaysOn availability group by using [!INCLUDE[tsql](../../../includes/tsql-md.md)] or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="49b65-104">灵活的故障转移策略提供了对导致可用性组自动执行故障转移的条件的精确控制。</span><span class="sxs-lookup"><span data-stu-id="49b65-104">A flexible failover policy provides granular control over the conditions that cause automatic failover for an availability group.</span></span> <span data-ttu-id="49b65-105">通过更改触发自动故障转移的失败条件和运行状况检查的频率，可增大或减小自动进行故障转移来支持高可用性 SLA 的可能性。</span><span class="sxs-lookup"><span data-stu-id="49b65-105">By changing the failure conditions that trigger an automatic failover and the frequency of health checks, you can increase or decrease the likelihood of an automatic failover to support your SLA for high availability.</span></span>  
  
  
  
    > [!NOTE]  
    >  The flexible failover policy of an availability group cannot be configured by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="49b65-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="49b65-106">Before You Begin</span></span>  
  
###  <a name="limitations-on-automatic-failovers"></a><a name="Limitations"></a><span data-ttu-id="49b65-107">自动故障转移的限制</span><span class="sxs-lookup"><span data-stu-id="49b65-107">Limitations on Automatic Failovers</span></span>  
  
-   <span data-ttu-id="49b65-108">要执行自动故障转移，当前主副本和一个辅助副本必须配置为使用自动故障转移的同步提交可用性模式，而且辅助副本必须与主副本同步。</span><span class="sxs-lookup"><span data-stu-id="49b65-108">For an automatic failover to occur, the current primary replica and one secondary replica must be configured for synchronous-commit availability mode with automatic failover and the secondary replica must be synchronized with the primary replica.</span></span>  
  
-   <span data-ttu-id="49b65-109">如果某个可用性组超过其 WSFC 故障阈值，则该 WSFC 群集不会尝试为该可用性组执行自动故障转移。</span><span class="sxs-lookup"><span data-stu-id="49b65-109">If an availability group exceeds its WSFC failure threshold, the WSFC cluster will not attempt an automatic failover for the availability group.</span></span> <span data-ttu-id="49b65-110">此外，该可用性组的 WSFC 资源组始终保持失败状态，直到群集管理员手动将该失败的资源组联机，或是数据库管理员对该可用性组执行手动故障转移。</span><span class="sxs-lookup"><span data-stu-id="49b65-110">Furthermore, the WSFC resource group of the availability group remains in a failed state until either the cluster administrator manually brings the failed resource group online or the database administrator performs a manual failover of the availability group.</span></span> <span data-ttu-id="49b65-111">WSFC 故障阈值 \*\* 定义为给定时间段中可用性组所支持的最大故障数。</span><span class="sxs-lookup"><span data-stu-id="49b65-111">The *WSFC failure threshold* is defined as the maximum number of failures supported for the availability group during a given time period.</span></span> <span data-ttu-id="49b65-112">默认时间段为六个小时，此时间段中最大故障数的默认值为 *n*-1，其中 *n* 是 WSFC 节点的数目。</span><span class="sxs-lookup"><span data-stu-id="49b65-112">The default time period is six hours, and the default value for the maximum number of failures during this period is *n*-1, where *n* is the number of WSFC nodes.</span></span> <span data-ttu-id="49b65-113">若要更改给定的可用性组的故障阈值，请使用 WSFC 故障转移管理器控制台。</span><span class="sxs-lookup"><span data-stu-id="49b65-113">To change the failure-threshold values for a given availability group, use the WSFC Failover Manager Console.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="49b65-114">先决条件</span><span class="sxs-lookup"><span data-stu-id="49b65-114">Prerequisites</span></span>  
  
-   <span data-ttu-id="49b65-115">您必须连接到承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="49b65-115">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="49b65-116">Security</span><span class="sxs-lookup"><span data-stu-id="49b65-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="49b65-117">权限</span><span class="sxs-lookup"><span data-stu-id="49b65-117">Permissions</span></span>  
  
|<span data-ttu-id="49b65-118">任务</span><span class="sxs-lookup"><span data-stu-id="49b65-118">Task</span></span>|<span data-ttu-id="49b65-119">权限</span><span class="sxs-lookup"><span data-stu-id="49b65-119">Permissions</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="49b65-120">为新的可用性组配置灵活故障转移策略</span><span class="sxs-lookup"><span data-stu-id="49b65-120">To configure the flexible failover policy for a new availability group</span></span>|<span data-ttu-id="49b65-121">需要 **sysadmin** 固定服务器角色的成员资格，以及 CREATE AVAILABILITY GROUP 服务器权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="49b65-121">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
|<span data-ttu-id="49b65-122">修改现有可用性组的策略</span><span class="sxs-lookup"><span data-stu-id="49b65-122">To modify the policy of an existing availability group</span></span>|<span data-ttu-id="49b65-123">对可用性组要求 ALTER AVAILABILITY GROUP 权限、CONTROL AVAILABILITY GROUP 权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="49b65-123">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="49b65-124">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="49b65-124">Using Transact-SQL</span></span>  
 <span data-ttu-id="49b65-125">**配置灵活故障转移策略**</span><span class="sxs-lookup"><span data-stu-id="49b65-125">**To configure the flexible failover policy**</span></span>  
  
1.  <span data-ttu-id="49b65-126">连接到承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="49b65-126">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="49b65-127">对于新的可用性组，请使用[CREATE AVAILABILITY group](/sql/t-sql/statements/create-availability-group-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="49b65-127">For a new availability group, use the [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="49b65-128">如果要修改现有的可用性组，请使用[ALTER AVAILABILITY group](/sql/t-sql/statements/alter-availability-group-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="49b65-128">If you are modifying an existing availability group, use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span>  
  
    -   <span data-ttu-id="49b65-129">若要设置故障转移条件级别，请使用 FAILURE_CONDITION_LEVEL = *n* 选项，其中， *n* 是 1 到 5 的整数。</span><span class="sxs-lookup"><span data-stu-id="49b65-129">To set the failover condition level, use the FAILURE_CONDITION_LEVEL = *n* option, where, *n* is an integer from 1 to 5.</span></span>  
  
         <span data-ttu-id="49b65-130">例如，以下 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句将现有可用性组 `AG1`的故障条件级别更改为一级：</span><span class="sxs-lookup"><span data-stu-id="49b65-130">For example, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement changes the failure-condition level of an existing availability group, `AG1`, to level one:</span></span>  
  
        ```sql
        ALTER AVAILABILITY GROUP AG1 SET (FAILURE_CONDITION_LEVEL = 1);  
        ```  
  
         <span data-ttu-id="49b65-131">这些整数值与故障条件级别的关系如下：</span><span class="sxs-lookup"><span data-stu-id="49b65-131">The relationship of these integer values to the failure condition levels is as follows:</span></span>  
  
        |[!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="49b65-132">值</span><span class="sxs-lookup"><span data-stu-id="49b65-132">Value</span></span>|<span data-ttu-id="49b65-133">级别</span><span class="sxs-lookup"><span data-stu-id="49b65-133">Level</span></span>|<span data-ttu-id="49b65-134">当出现以下情况时，自动启动故障转移…</span><span class="sxs-lookup"><span data-stu-id="49b65-134">Automatic Is Failover Initiated When...</span></span>|  
        |------------------------------|-----------|-------------------------------------------|  
        |<span data-ttu-id="49b65-135">1</span><span class="sxs-lookup"><span data-stu-id="49b65-135">1</span></span>|<span data-ttu-id="49b65-136">一个</span><span class="sxs-lookup"><span data-stu-id="49b65-136">One</span></span>|<span data-ttu-id="49b65-137">当服务器关闭时。</span><span class="sxs-lookup"><span data-stu-id="49b65-137">On server down.</span></span> <span data-ttu-id="49b65-138">SQL Server 服务因故障转移或重新启动而停止。</span><span class="sxs-lookup"><span data-stu-id="49b65-138">The SQL Server service stops because of a failover or restart.</span></span>|  
        |<span data-ttu-id="49b65-139">2</span><span class="sxs-lookup"><span data-stu-id="49b65-139">2</span></span>|<span data-ttu-id="49b65-140">两个</span><span class="sxs-lookup"><span data-stu-id="49b65-140">Two</span></span>|<span data-ttu-id="49b65-141">当服务器无响应时。</span><span class="sxs-lookup"><span data-stu-id="49b65-141">On server unresponsive.</span></span> <span data-ttu-id="49b65-142">满足任何下限值条件，SQL Server 服务连接到群集，超过运行状况检查超时阈值，或当前主副本处于失败状态。</span><span class="sxs-lookup"><span data-stu-id="49b65-142">Any condition of lower value is satisfied, the SQL Server service is connected to the cluster and the health check timeout threshold is exceeded, or the current primary replica is in a failed state.</span></span>|  
        |<span data-ttu-id="49b65-143">3</span><span class="sxs-lookup"><span data-stu-id="49b65-143">3</span></span>|<span data-ttu-id="49b65-144">三级</span><span class="sxs-lookup"><span data-stu-id="49b65-144">Three</span></span>|<span data-ttu-id="49b65-145">出现严重服务器错误时。</span><span class="sxs-lookup"><span data-stu-id="49b65-145">On critical server error.</span></span> <span data-ttu-id="49b65-146">满足任何下限值条件或发生严重的内部服务器错误。</span><span class="sxs-lookup"><span data-stu-id="49b65-146">Any condition of lower value is satisfied or an internal critical server error occurs.</span></span><br /><br /> <span data-ttu-id="49b65-147">这是默认级别。</span><span class="sxs-lookup"><span data-stu-id="49b65-147">This is the default level.</span></span>|  
        |<span data-ttu-id="49b65-148">4</span><span class="sxs-lookup"><span data-stu-id="49b65-148">4</span></span>|<span data-ttu-id="49b65-149">四级</span><span class="sxs-lookup"><span data-stu-id="49b65-149">Four</span></span>|<span data-ttu-id="49b65-150">出现严重服务器错误时。</span><span class="sxs-lookup"><span data-stu-id="49b65-150">On moderate server error.</span></span> <span data-ttu-id="49b65-151">满足任何下限值条件或发生中度的服务器错误。</span><span class="sxs-lookup"><span data-stu-id="49b65-151">Any condition of lower value is satisfied or a moderate Server error occurs.</span></span>|  
        |<span data-ttu-id="49b65-152">5</span><span class="sxs-lookup"><span data-stu-id="49b65-152">5</span></span>|<span data-ttu-id="49b65-153">五级</span><span class="sxs-lookup"><span data-stu-id="49b65-153">Five</span></span>|<span data-ttu-id="49b65-154">在出现任何限定的失败条件时。</span><span class="sxs-lookup"><span data-stu-id="49b65-154">On any qualified failure conditions.</span></span> <span data-ttu-id="49b65-155">满足任何下限值条件或出现限定的失败条件。</span><span class="sxs-lookup"><span data-stu-id="49b65-155">Any condition of lower value is satisfied or a qualifying failure condition occurs.</span></span>|  
  
         <span data-ttu-id="49b65-156">有关故障转移条件级别的更多信息，请参阅[针对可用性组的自动故障转移的灵活的故障转移策略 (SQL Server)](flexible-automatic-failover-policy-availability-group.md)。</span><span class="sxs-lookup"><span data-stu-id="49b65-156">For more information about the failover condition levels, see [Flexible Failover Policy for Automatic Failover of an Availability Group &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md).</span></span>  
  
    -   <span data-ttu-id="49b65-157">若要配置运行状况检查超时阈值，请使用 HEALTH_CHECK_TIMEOUT = *n* 选项，其中， *n* 是一个从 15000 毫秒（15 秒）到 4294967295 毫秒的整数。</span><span class="sxs-lookup"><span data-stu-id="49b65-157">To configure the health check timeout threshold, use the HEALTH_CHECK_TIMEOUT = *n* option, where, *n* is an integer from 15000 milliseconds (15 seconds) to 4294967295 milliseconds.</span></span> <span data-ttu-id="49b65-158">默认值为 30000 毫秒（30 秒）</span><span class="sxs-lookup"><span data-stu-id="49b65-158">The default value is 30000 milliseconds (30 seconds)</span></span>  
  
         <span data-ttu-id="49b65-159">例如，以下 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句会将现有可用性组 `AG1`的运行状况检查超时阈值更改为 60,000 毫秒（1 分钟）。</span><span class="sxs-lookup"><span data-stu-id="49b65-159">For example, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement changes the health-check timeout threshold of an existing availability group, `AG1`, to 60,000 milliseconds (one minute).</span></span>  
  
        ```sql
        ALTER AVAILABILITY GROUP AG1 SET (HEALTH_CHECK_TIMEOUT = 60000);  
        ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="49b65-160">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="49b65-160">Using PowerShell</span></span>  

### <a name="to-configure-the-flexible-failover-policy"></a><span data-ttu-id="49b65-161">配置灵活的故障转移策略 \* \*</span><span class="sxs-lookup"><span data-stu-id="49b65-161">To configure the flexible failover policy\*\*</span></span>  
  
1.  <span data-ttu-id="49b65-162">将默认的 (`cd`) 设置为承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="49b65-162">Set default (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="49b65-163">在将可用性副本添加到可用性组中时，请使用 `New-SqlAvailabilityGroup` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="49b65-163">When adding an availability replica to an availability group, use the `New-SqlAvailabilityGroup` cmdlet.</span></span> <span data-ttu-id="49b65-164">在修改现有可用性副本时，请使用 `Set-SqlAvailabilityGroup` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="49b65-164">When modifying an existing availability replica, use the `Set-SqlAvailabilityGroup` cmdlet.</span></span>  
  
    -   <span data-ttu-id="49b65-165">若要设置故障转移条件级别，请使用 `FailureConditionLevel` *level*参数，其中， *level*是下列值之一：</span><span class="sxs-lookup"><span data-stu-id="49b65-165">To set the failover condition level, use the `FailureConditionLevel`*level* parameter, where, *level* is one of the following values:</span></span>  
  
        |<span data-ttu-id="49b65-166">值</span><span class="sxs-lookup"><span data-stu-id="49b65-166">Value</span></span>|<span data-ttu-id="49b65-167">级别</span><span class="sxs-lookup"><span data-stu-id="49b65-167">Level</span></span>|<span data-ttu-id="49b65-168">当出现以下情况时，自动启动故障转移…</span><span class="sxs-lookup"><span data-stu-id="49b65-168">Automatic Is Failover Initiated When...</span></span>|  
        |-----------|-----------|-------------------------------------------|  
        |`OnServerDown`|<span data-ttu-id="49b65-169">一个</span><span class="sxs-lookup"><span data-stu-id="49b65-169">One</span></span>|<span data-ttu-id="49b65-170">当服务器关闭时。</span><span class="sxs-lookup"><span data-stu-id="49b65-170">On server down.</span></span> <span data-ttu-id="49b65-171">SQL Server 服务因故障转移或重新启动而停止。</span><span class="sxs-lookup"><span data-stu-id="49b65-171">The SQL Server service stops because of a failover or restart.</span></span>|  
        |`OnServerUnresponsive`|<span data-ttu-id="49b65-172">两个</span><span class="sxs-lookup"><span data-stu-id="49b65-172">Two</span></span>|<span data-ttu-id="49b65-173">当服务器无响应时。</span><span class="sxs-lookup"><span data-stu-id="49b65-173">On server unresponsive.</span></span> <span data-ttu-id="49b65-174">满足任何下限值条件，SQL Server 服务连接到群集，超过运行状况检查超时阈值，或当前主副本处于失败状态。</span><span class="sxs-lookup"><span data-stu-id="49b65-174">Any condition of lower value is satisfied, the SQL Server service is connected to the cluster and the health check timeout threshold is exceeded, or the current primary replica is in a failed state.</span></span>|  
        |`OnCriticalServerError`|<span data-ttu-id="49b65-175">三级</span><span class="sxs-lookup"><span data-stu-id="49b65-175">Three</span></span>|<span data-ttu-id="49b65-176">出现严重服务器错误时。</span><span class="sxs-lookup"><span data-stu-id="49b65-176">On critical server error.</span></span> <span data-ttu-id="49b65-177">满足任何下限值条件或发生严重的内部服务器错误。</span><span class="sxs-lookup"><span data-stu-id="49b65-177">Any condition of lower value is satisfied or an internal critical server error occurs.</span></span><br /><br /> <span data-ttu-id="49b65-178">这是默认级别。</span><span class="sxs-lookup"><span data-stu-id="49b65-178">This is the default level.</span></span>|  
        |`OnModerateServerError`|<span data-ttu-id="49b65-179">四级</span><span class="sxs-lookup"><span data-stu-id="49b65-179">Four</span></span>|<span data-ttu-id="49b65-180">出现严重服务器错误时。</span><span class="sxs-lookup"><span data-stu-id="49b65-180">On moderate server error.</span></span> <span data-ttu-id="49b65-181">满足任何下限值条件或发生中度的服务器错误。</span><span class="sxs-lookup"><span data-stu-id="49b65-181">Any condition of lower value is satisfied or a moderate Server error occurs.</span></span>|  
        |`OnAnyQualifiedFailureConditions`|<span data-ttu-id="49b65-182">五级</span><span class="sxs-lookup"><span data-stu-id="49b65-182">Five</span></span>|<span data-ttu-id="49b65-183">在出现任何限定的失败条件时。</span><span class="sxs-lookup"><span data-stu-id="49b65-183">On any qualified failure conditions.</span></span> <span data-ttu-id="49b65-184">满足任何下限值条件或出现限定的失败条件。</span><span class="sxs-lookup"><span data-stu-id="49b65-184">Any condition of lower value is satisfied or a qualifying failure condition occurs.</span></span>|  
  
         <span data-ttu-id="49b65-185">有关故障转移条件级别的更多信息，请参阅[针对可用性组的自动故障转移的灵活的故障转移策略 (SQL Server)](flexible-automatic-failover-policy-availability-group.md)。</span><span class="sxs-lookup"><span data-stu-id="49b65-185">For more information about the failover condition levels, see [Flexible Failover Policy for Automatic Failover of an Availability Group &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md).</span></span>  
  
         <span data-ttu-id="49b65-186">例如，以下命令会将现有可用性组 `AG1`的故障条件级别更改为一级。</span><span class="sxs-lookup"><span data-stu-id="49b65-186">For example, the following command changes the failure-condition level of an existing availability group, `AG1`, to level one.</span></span>  
  
        ```powershell
        Set-SqlAvailabilityGroup `
         -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg `
         -FailureConditionLevel OnServerDown  
        ```  
  
    -   <span data-ttu-id="49b65-187">若要设置运行状况检查超时阈值，请使用 `HealthCheckTimeout` *n*参数，其中*n*是15000毫秒 (15 秒) 到4294967295毫秒的整数。</span><span class="sxs-lookup"><span data-stu-id="49b65-187">To set the health check timeout threshold, use the `HealthCheckTimeout`*n* parameter, where, *n* is an integer from 15000 milliseconds (15 seconds) to 4294967295 milliseconds.</span></span> <span data-ttu-id="49b65-188">默认值为 30000 毫秒（30 秒）。</span><span class="sxs-lookup"><span data-stu-id="49b65-188">The default value is 30000 milliseconds (30 seconds).</span></span>  
  
         <span data-ttu-id="49b65-189">例如，以下命令会将现有可用性组 `AG1`的运行状况检查超时阈值更改为 120,000 毫秒（2 分钟）。</span><span class="sxs-lookup"><span data-stu-id="49b65-189">For example, the following command changes the health-check timeout threshold of an existing availability group, `AG1`, to 120,000 milliseconds (two minutes).</span></span>  
  
        ```powershell
        Set-SqlAvailabilityGroup `
         -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAG `
         -HealthCheckTimeout 120000  
        ```  
  
> [!NOTE]  
>  <span data-ttu-id="49b65-190">若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="49b65-190">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="49b65-191">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="49b65-191">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="49b65-192">**设置和使用 SQL Server PowerShell 提供程序**</span><span class="sxs-lookup"><span data-stu-id="49b65-192">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="49b65-193">SQL Server PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="49b65-193">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
-   [<span data-ttu-id="49b65-194">Get Help SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="49b65-194">Get Help SQL Server PowerShell</span></span>](../../../powershell/sql-server-powershell.md)  
  
## <a name="see-also"></a><span data-ttu-id="49b65-195">另请参阅</span><span class="sxs-lookup"><span data-stu-id="49b65-195">See Also</span></span>  
 <span data-ttu-id="49b65-196">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="49b65-196">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="49b65-197">[可用性模式 (AlwaysOn 可用性组) ](availability-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="49b65-197">[Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md) </span></span>  
 <span data-ttu-id="49b65-198">[故障转移和故障转移模式 &#40;AlwaysOn 可用性组&#41;](failover-and-failover-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="49b65-198">[Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;](failover-and-failover-modes-always-on-availability-groups.md) </span></span>  
 <span data-ttu-id="49b65-199">[Windows Server 故障转移群集 (WSFC) 与 SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="49b65-199">[Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span></span>  
 <span data-ttu-id="49b65-200">[故障转移群集实例的故障转移策略](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md) </span><span class="sxs-lookup"><span data-stu-id="49b65-200">[Failover Policy for Failover Cluster Instances](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md) </span></span>  
 [<span data-ttu-id="49b65-201">sp_server_diagnostics (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="49b65-201">sp_server_diagnostics &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql)  
