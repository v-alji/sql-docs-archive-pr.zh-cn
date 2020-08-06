---
title: 配置“并行的开销阈值”服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 10/26/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- cost threshold for parallelism option
ms.assetid: dad21bee-fe28-41f6-9d2f-e6ababfaf9db
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 675055a753e84ace3a4fcb44b41b8c914326c5c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578437"
---
# <a name="configure-the-cost-threshold-for-parallelism-server-configuration-option"></a><span data-ttu-id="af393-102">配置并行的开销阈值服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="af393-102">Configure the cost threshold for parallelism Server Configuration Option</span></span>
  <span data-ttu-id="af393-103">本主题说明了如何使用 **或** 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中配置 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] “并行的开销阈值” [!INCLUDE[tsql](../../includes/tsql-md.md)]服务器配置选项。</span><span class="sxs-lookup"><span data-stu-id="af393-103">This topic describes how to configure the **cost threshold for parallelism** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="af393-104">**cost threshold for parallelism** 选项指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 创建和运行并行查询计划的阈值。</span><span class="sxs-lookup"><span data-stu-id="af393-104">The **cost threshold for parallelism** option specifies the threshold at which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creates and runs parallel plans for queries.</span></span> <span data-ttu-id="af393-105">仅当运行同一查询的串行计划的估计开销高于在“并行的开销阈值”中设置的值时，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 才创建和运行该查询的并行计划。</span><span class="sxs-lookup"><span data-stu-id="af393-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creates and runs a parallel plan for a query only when the estimated cost to run a serial plan for the same query is higher than the value set in **cost threshold for parallelism**.</span></span> <span data-ttu-id="af393-106">开销指的是在特定硬件配置中运行串行计划估计需要花费的时间（秒）。</span><span class="sxs-lookup"><span data-stu-id="af393-106">The cost refers to an estimated elapsed time in seconds required to run the serial plan on a specific hardware configuration.</span></span> <span data-ttu-id="af393-107">**“并行的开销阈值”** 选项可设置为 0 到 32767 之间的任何值。</span><span class="sxs-lookup"><span data-stu-id="af393-107">The **cost threshold for parallelism** option can be set to any value from 0 through 32767.</span></span> <span data-ttu-id="af393-108">默认值为 5。</span><span class="sxs-lookup"><span data-stu-id="af393-108">The default value is 5.</span></span>  
  
 <span data-ttu-id="af393-109">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="af393-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="af393-110">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="af393-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="af393-111">限制和局限</span><span class="sxs-lookup"><span data-stu-id="af393-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="af393-112">建议</span><span class="sxs-lookup"><span data-stu-id="af393-112">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="af393-113">安全性</span><span class="sxs-lookup"><span data-stu-id="af393-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="af393-114">**若要配置并行的开销阈值选项，请使用：**</span><span class="sxs-lookup"><span data-stu-id="af393-114">**To configure the cost threshold for parallelism option, using:**</span></span>  
  
     [<span data-ttu-id="af393-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="af393-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="af393-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="af393-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="af393-117">**跟进：** [在配置并行的开销阈值选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="af393-117">**Follow Up:**  [After you configure the cost threshold for parallelism option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="af393-118">开始之前</span><span class="sxs-lookup"><span data-stu-id="af393-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="af393-119">限制和局限</span><span class="sxs-lookup"><span data-stu-id="af393-119">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="af393-120">开销指的是在特定硬件配置中运行串行计划估计需要花费的时间（秒）。</span><span class="sxs-lookup"><span data-stu-id="af393-120">The cost refers to an estimated elapsed time in seconds required to run the serial plan on a specific hardware configuration.</span></span> <span data-ttu-id="af393-121">只能为对称多处理器设置 **cost threshold for parallelism** 。</span><span class="sxs-lookup"><span data-stu-id="af393-121">Only set **cost threshold for parallelism** on symmetric multiprocessors.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="af393-122">将忽略 **或** 的值：</span><span class="sxs-lookup"><span data-stu-id="af393-122">ignores the **cost threshold for parallelism** value under the following conditions:</span></span>  
  
    -   <span data-ttu-id="af393-123">计算机只有一个逻辑处理器。</span><span class="sxs-lookup"><span data-stu-id="af393-123">Your computer has only one logical processor.</span></span>  
  
    -   <span data-ttu-id="af393-124">由于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 相关性掩码 **配置选项的原因，只有一个逻辑处理器可供** 使用。</span><span class="sxs-lookup"><span data-stu-id="af393-124">Only a single logical processor is available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] because of the **affinity mask** configuration option.</span></span>  
  
    -   <span data-ttu-id="af393-125">**“最大并行度”** 选项设置为 1。</span><span class="sxs-lookup"><span data-stu-id="af393-125">The **max degree of parallelism** option is set to 1.</span></span>  
  
 <span data-ttu-id="af393-126">逻辑处理器是处理器硬件的基本单元，可让操作系统调度任务或执行线程上下文。</span><span class="sxs-lookup"><span data-stu-id="af393-126">A logical processor is the basic unit of processor hardware that allows the operating system to dispatch a task or execute a thread context.</span></span> <span data-ttu-id="af393-127">每个逻辑处理器一次只执行一个线程上下文。</span><span class="sxs-lookup"><span data-stu-id="af393-127">Each logical processor can execute only one thread context at a time.</span></span> <span data-ttu-id="af393-128">处理器内核是提供解码和执行指令的能力的电路。</span><span class="sxs-lookup"><span data-stu-id="af393-128">The processor core is the circuitry that provides ability to decode and execute instructions.</span></span> <span data-ttu-id="af393-129">一个处理器内核可能包含一个或多个逻辑处理器。</span><span class="sxs-lookup"><span data-stu-id="af393-129">A processor core may contain one or more logical processors.</span></span> <span data-ttu-id="af393-130">以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询可用于获取系统的 CPU 信息。</span><span class="sxs-lookup"><span data-stu-id="af393-130">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] query can be used for obtaining CPU information for the system.</span></span>  
  
```  
SELECT (cpu_count / hyperthread_ratio) AS PhysicalCPUs,   
cpu_count AS logicalCPUs   
FROM sys.dm_os_sys_info  
```  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="af393-131">建议</span><span class="sxs-lookup"><span data-stu-id="af393-131">Recommendations</span></span>  
  
-   <span data-ttu-id="af393-132">此选项是一个高级选项，仅应由有经验的数据库管理员或认证的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技术人员更改。</span><span class="sxs-lookup"><span data-stu-id="af393-132">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="af393-133">在某些情况下，即使查询的开销计划小于当前 **“并行的开销阈值”** 的值，也有可能选择并行计划。</span><span class="sxs-lookup"><span data-stu-id="af393-133">In certain cases, a parallel plan may be chosen even though the query's cost plan is less than the current **cost threshold for parallelism** value.</span></span> <span data-ttu-id="af393-134">出现这种情况，是因为使用并行还是串行计划是根据完成完全优化之前所提供的开销估计确定的。</span><span class="sxs-lookup"><span data-stu-id="af393-134">This can happen because the decision to use a parallel or serial plan is based on a cost estimate provided before the full optimization is complete.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="af393-135">Security</span><span class="sxs-lookup"><span data-stu-id="af393-135">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="af393-136">权限</span><span class="sxs-lookup"><span data-stu-id="af393-136">Permissions</span></span>  
 <span data-ttu-id="af393-137">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="af393-137">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="af393-138">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="af393-138">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="af393-139">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="af393-139">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="af393-140">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="af393-140">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-cost-threshold-for-parallelism-option"></a><span data-ttu-id="af393-141">配置并行的开销阈值选项</span><span class="sxs-lookup"><span data-stu-id="af393-141">To configure the cost threshold for parallelism option</span></span>  
  
1.  <span data-ttu-id="af393-142">在对象资源管理器中，右键单击服务器并选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="af393-142">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="af393-143">单击 **“高级”** 节点。</span><span class="sxs-lookup"><span data-stu-id="af393-143">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="af393-144">在 **“并行”** 下，将 **“CostThresholdForParallelism”** 选项更改为所需值。</span><span class="sxs-lookup"><span data-stu-id="af393-144">Under **Parallelism**, change the **CostThresholdForParallelism** option to the value you want.</span></span> <span data-ttu-id="af393-145">键入或选择一个值（介于 0 到 32767 之间）。</span><span class="sxs-lookup"><span data-stu-id="af393-145">Type or select a value from 0 to 32767.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="af393-146">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="af393-146">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-cost-threshold-for-parallelism-option"></a><span data-ttu-id="af393-147">配置并行的开销阈值选项</span><span class="sxs-lookup"><span data-stu-id="af393-147">To configure the cost threshold for parallelism option</span></span>  
  
1.  <span data-ttu-id="af393-148">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="af393-148">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="af393-149">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="af393-149">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="af393-150">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="af393-150">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="af393-151">此示例说明如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将 `cost threshold for parallelism` 选项的值设置为 `10`。</span><span class="sxs-lookup"><span data-stu-id="af393-151">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `cost threshold for parallelism` option to `10`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'cost threshold for parallelism', 10 ;  
GO  
RECONFIGURE  
GO  
```  
  
 <span data-ttu-id="af393-152">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="af393-152">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-cost-threshold-for-parallelism-option"></a><a name="FollowUp"></a> <span data-ttu-id="af393-153">跟进：在配置并行的开销阈值选项之后</span><span class="sxs-lookup"><span data-stu-id="af393-153">Follow Up: After you configure the cost threshold for parallelism option</span></span>  
 <span data-ttu-id="af393-154">该设置将立即生效，无需重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="af393-154">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af393-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="af393-155">See Also</span></span>  
 <span data-ttu-id="af393-156">[配置并行索引操作](../../relational-databases/indexes/configure-parallel-index-operations.md) </span><span class="sxs-lookup"><span data-stu-id="af393-156">[Configure Parallel Index Operations](../../relational-databases/indexes/configure-parallel-index-operations.md) </span></span>  
 <span data-ttu-id="af393-157">[查询提示 (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-query) </span><span class="sxs-lookup"><span data-stu-id="af393-157">[Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span></span>  
 <span data-ttu-id="af393-158">[ALTER WORKLOAD GROUP (Transact-SQL)](/sql/t-sql/statements/alter-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="af393-158">[ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-workload-group-transact-sql) </span></span>  
 <span data-ttu-id="af393-159">[affinity mask 服务器配置选项](affinity-mask-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="af393-159">[affinity mask Server Configuration Option](affinity-mask-server-configuration-option.md) </span></span>  
 <span data-ttu-id="af393-160">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="af393-160">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="af393-161">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="af393-161">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="af393-162">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af393-162">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
