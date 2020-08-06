---
title: 配置“最大工作线程数”服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- worker threads [SQL Server]
- max worker threads option
ms.assetid: abeadfa4-a14d-469a-bacf-75812e48fac1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4881cefee350d34d93b539c56be6f43866d3ddfe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588042"
---
# <a name="configure-the-max-worker-threads-server-configuration-option"></a><span data-ttu-id="c7381-102">配置 max worker threads 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="c7381-102">Configure the max worker threads Server Configuration Option</span></span>
  <span data-ttu-id="c7381-103">本主题说明如何使用  或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中配置 max worker threads [!INCLUDE[tsql](../../includes/tsql-md.md)]服务器配置选项。</span><span class="sxs-lookup"><span data-stu-id="c7381-103">This topic describes how to configure the **max worker threads** server configuration option in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="c7381-104">**max worker threads** 选项配置可用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程的工作线程数。</span><span class="sxs-lookup"><span data-stu-id="c7381-104">The **max worker threads** option configures the number of worker threads that are available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] processes.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c7381-105">使用操作系统的本机线程服务，以便使一个或多个线程支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 同时支持的每一个网络，另一个线程处理数据库检查点，而线程池则处理所有用户。</span><span class="sxs-lookup"><span data-stu-id="c7381-105">uses the native thread services of the operating systems so that one or more threads support each network that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supports simultaneously, another thread handles database checkpoints, and a pool of threads handles all users.</span></span> <span data-ttu-id="c7381-106">**max worker threads** 的默认值为 0。</span><span class="sxs-lookup"><span data-stu-id="c7381-106">The default value for **max worker threads** is 0.</span></span> <span data-ttu-id="c7381-107">这使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在启动时自动配置工作线程数。</span><span class="sxs-lookup"><span data-stu-id="c7381-107">This enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to automatically configure the number of worker threads at startup.</span></span> <span data-ttu-id="c7381-108">默认设置对于大多数系统为最佳设置。</span><span class="sxs-lookup"><span data-stu-id="c7381-108">The default setting is best for most systems.</span></span> <span data-ttu-id="c7381-109">不过，根据您的系统配置，有时将 **max worker threads** 设置为特定值会提高性能。</span><span class="sxs-lookup"><span data-stu-id="c7381-109">However, depending on your system configuration, setting **max worker threads** to a specific value sometimes improves performance.</span></span>  
  
 <span data-ttu-id="c7381-110">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="c7381-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c7381-111">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="c7381-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c7381-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="c7381-112">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="c7381-113">建议</span><span class="sxs-lookup"><span data-stu-id="c7381-113">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="c7381-114">安全性</span><span class="sxs-lookup"><span data-stu-id="c7381-114">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c7381-115">**配置 max worker threads 选项，使用：**</span><span class="sxs-lookup"><span data-stu-id="c7381-115">**To configure the max worker threads option, using:**</span></span>  
  
     [<span data-ttu-id="c7381-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c7381-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c7381-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c7381-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="c7381-118">**跟进：** [在配置“最大工作线程”选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="c7381-118">**Follow Up:**  [After you configure the max worker threads option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c7381-119">开始之前</span><span class="sxs-lookup"><span data-stu-id="c7381-119">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="c7381-120">限制和局限</span><span class="sxs-lookup"><span data-stu-id="c7381-120">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="c7381-121">当实际的查询请求数量少于 **max worker threads**中设置的数量时，每一个线程处理一个查询请求。</span><span class="sxs-lookup"><span data-stu-id="c7381-121">When the actual number of query requests is less than the amount set in **max worker threads**, one thread handles each query request.</span></span> <span data-ttu-id="c7381-122">但是，如果实际的查询请求数超过**最大工作线程**数中设置的数量，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会将工作线程汇集在一起，以便下一个可用的工作线程可以处理该请求。</span><span class="sxs-lookup"><span data-stu-id="c7381-122">However, if the actual number of query request exceeds the amount set in **max worker threads**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pools the worker threads so that the next available worker thread can handle the request.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="c7381-123">建议</span><span class="sxs-lookup"><span data-stu-id="c7381-123">Recommendations</span></span>  
  
-   <span data-ttu-id="c7381-124">此选项是一个高级选项，仅应由有经验的数据库管理员或认证的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技术人员更改。</span><span class="sxs-lookup"><span data-stu-id="c7381-124">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="c7381-125">当服务器上连接有大量客户端时，线程池有助于优化性能。</span><span class="sxs-lookup"><span data-stu-id="c7381-125">Thread pooling helps optimize performance when large numbers of clients are connected to the server.</span></span> <span data-ttu-id="c7381-126">一般情况下，会为每个查询请求创建一个单独的操作系统线程。</span><span class="sxs-lookup"><span data-stu-id="c7381-126">Usually, a separate operating system thread is created for each query request.</span></span> <span data-ttu-id="c7381-127">但是，当到服务器的连接达到数以百计时，为每个查询请求使用一个线程会占用大量的系统资源。</span><span class="sxs-lookup"><span data-stu-id="c7381-127">However, with hundreds of connections to the server, using one thread per query request can consume large amounts of system resources.</span></span> <span data-ttu-id="c7381-128">**max worker threads** 选项使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可以为更大数量的查询请求创建一个工作线程池，这将提高性能。</span><span class="sxs-lookup"><span data-stu-id="c7381-128">The **max worker threads** option enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to create a pool of worker threads to service a larger number of query requests, which improves performance.</span></span>  
  
-   <span data-ttu-id="c7381-129">下表显示了针对各种 CPU 与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="c7381-129">The following table shows the automatically configured number of max worker threads for various combinations of CPUs and versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
    |<span data-ttu-id="c7381-130">CPU 数</span><span class="sxs-lookup"><span data-stu-id="c7381-130">Number of CPUs</span></span>|<span data-ttu-id="c7381-131">32 位计算机</span><span class="sxs-lookup"><span data-stu-id="c7381-131">32-bit computer</span></span>|<span data-ttu-id="c7381-132">64 位计算机</span><span class="sxs-lookup"><span data-stu-id="c7381-132">64-bit computer</span></span>|  
    |--------------------|----------------------|----------------------|  
    |<span data-ttu-id="c7381-133">\<= 4 个处理器</span><span class="sxs-lookup"><span data-stu-id="c7381-133">\<= 4 processors</span></span>|<span data-ttu-id="c7381-134">256</span><span class="sxs-lookup"><span data-stu-id="c7381-134">256</span></span>|<span data-ttu-id="c7381-135">512</span><span class="sxs-lookup"><span data-stu-id="c7381-135">512</span></span>|  
    |<span data-ttu-id="c7381-136">8 个处理器</span><span class="sxs-lookup"><span data-stu-id="c7381-136">8 processors</span></span>|<span data-ttu-id="c7381-137">288</span><span class="sxs-lookup"><span data-stu-id="c7381-137">288</span></span>|<span data-ttu-id="c7381-138">576</span><span class="sxs-lookup"><span data-stu-id="c7381-138">576</span></span>|  
    |<span data-ttu-id="c7381-139">16 个处理器</span><span class="sxs-lookup"><span data-stu-id="c7381-139">16 processors</span></span>|<span data-ttu-id="c7381-140">352</span><span class="sxs-lookup"><span data-stu-id="c7381-140">352</span></span>|<span data-ttu-id="c7381-141">704</span><span class="sxs-lookup"><span data-stu-id="c7381-141">704</span></span>|  
    |<span data-ttu-id="c7381-142">32 个处理器</span><span class="sxs-lookup"><span data-stu-id="c7381-142">32 processors</span></span>|<span data-ttu-id="c7381-143">480</span><span class="sxs-lookup"><span data-stu-id="c7381-143">480</span></span>|<span data-ttu-id="c7381-144">960</span><span class="sxs-lookup"><span data-stu-id="c7381-144">960</span></span>|  
    |<span data-ttu-id="c7381-145">64 个处理器</span><span class="sxs-lookup"><span data-stu-id="c7381-145">64 processors</span></span>|<span data-ttu-id="c7381-146">736</span><span class="sxs-lookup"><span data-stu-id="c7381-146">736</span></span>|<span data-ttu-id="c7381-147">1472</span><span class="sxs-lookup"><span data-stu-id="c7381-147">1472</span></span>|  
    |<span data-ttu-id="c7381-148">128 个处理器</span><span class="sxs-lookup"><span data-stu-id="c7381-148">128 processors</span></span>|<span data-ttu-id="c7381-149">4224</span><span class="sxs-lookup"><span data-stu-id="c7381-149">4224</span></span>|<span data-ttu-id="c7381-150">4480</span><span class="sxs-lookup"><span data-stu-id="c7381-150">4480</span></span>|  
    |<span data-ttu-id="c7381-151">256 个处理器</span><span class="sxs-lookup"><span data-stu-id="c7381-151">256 processors</span></span>|<span data-ttu-id="c7381-152">8320</span><span class="sxs-lookup"><span data-stu-id="c7381-152">8320</span></span>|<span data-ttu-id="c7381-153">8576</span><span class="sxs-lookup"><span data-stu-id="c7381-153">8576</span></span>|  
  
    > [!NOTE]  
    >  <span data-ttu-id="c7381-154">有关使用 64 个以上的 CPU 的建议，请参考 [在具有超过 64 个 CPU 的计算机上运行 SQL Server 的最佳做法](https://technet.microsoft.com/library/ee210547\(SQL.105\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="c7381-154">For recommendations on using more than 64 CPUs, refer to [Best Practices for Running SQL Server on Computers That Have More Than 64 CPUs](https://technet.microsoft.com/library/ee210547\(SQL.105\).aspx).</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="c7381-155">我们建议对于 32 位计算机上运行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，最大工作线程数为 1024。</span><span class="sxs-lookup"><span data-stu-id="c7381-155">We recommend 1024 as the maximum number of worker threads for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is running on a 32-bit computer.</span></span>  
  
-   <span data-ttu-id="c7381-156">如果所有工作线程因为长时间运行的查询而处于活动状态， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可能停止响应，直到一个工作线程完成并变成可用。</span><span class="sxs-lookup"><span data-stu-id="c7381-156">When all worker threads are active with long running queries, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might appear unresponsive until a worker thread completes and becomes available.</span></span> <span data-ttu-id="c7381-157">虽然这不是缺点，但有时用户可能并不希望如此。</span><span class="sxs-lookup"><span data-stu-id="c7381-157">Although this is not a defect, it can sometimes be undesirable.</span></span> <span data-ttu-id="c7381-158">如果进程显示为停止响应并且不再处理新查询，则将使用专用管理员连接 (DAC) 连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，并关闭此进程。</span><span class="sxs-lookup"><span data-stu-id="c7381-158">If a process appears to be unresponsive and no new queries can be processed, then connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the dedicated administrator connection (DAC), and kill the process.</span></span> <span data-ttu-id="c7381-159">为避免此种情况发生，请增大最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="c7381-159">To prevent this, increase the number of max worker threads.</span></span>  
  
 <span data-ttu-id="c7381-160">**max worker threads** 服务器配置选项不考虑所有系统任务（例如可用性组、Service Broker、锁管理器等）所需的线程。</span><span class="sxs-lookup"><span data-stu-id="c7381-160">The **max worker threads** server configuration option does not take into account threads that are required for all the system tasks such as Availibility Groups, Service Broker, Lock Manager, and others.</span></span>  <span data-ttu-id="c7381-161">如果超过了配置的线程数目，下列查询将提供有关生成了附加线程的系统任务的信息。</span><span class="sxs-lookup"><span data-stu-id="c7381-161">If the number of threads configured are being exceeded, the following query will provide information about the system tasks that have spawned the additional threads.</span></span>  
  
```  
SELECT  
s.session_id,  
r.command,  
r.status,  
r.wait_type,  
r.scheduler_id,  
w.worker_address,  
w.is_preemptive,  
w.state,  
t.task_state,  
t.session_id,  
t.exec_context_id,  
t.request_id  
FROM sys.dm_exec_sessions AS s  
INNERJOIN sys.dm_exec_requests AS r  
    ON s.session_id = r.session_id  
INNER JOIN sys.dm_os_tasks AS t  
    ON r.task_address = t.task_address  
INNER JOIN sys.dm_os_workers AS w  
    ON t.worker_address = w.worker_address  
WHERE s.is_user_process = 0;  
  
```  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c7381-162">Security</span><span class="sxs-lookup"><span data-stu-id="c7381-162">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c7381-163">权限</span><span class="sxs-lookup"><span data-stu-id="c7381-163">Permissions</span></span>  
 <span data-ttu-id="c7381-164">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="c7381-164">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="c7381-165">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="c7381-165">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="c7381-166">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="c7381-166">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c7381-167">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c7381-167">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-max-worker-threads-option"></a><span data-ttu-id="c7381-168">配置 max worker threads 选项</span><span class="sxs-lookup"><span data-stu-id="c7381-168">To configure the max worker threads option</span></span>  
  
1.  <span data-ttu-id="c7381-169">在对象资源管理器中，右键单击服务器并选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="c7381-169">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="c7381-170">单击 **“处理器”** 节点。</span><span class="sxs-lookup"><span data-stu-id="c7381-170">Click the **Processors** node.</span></span>  
  
3.  <span data-ttu-id="c7381-171">在 "**最大工作线程数**" 框中，键入或选择一个介于128和32767之间的值。</span><span class="sxs-lookup"><span data-stu-id="c7381-171">In the **Max worker threads** box, type or select a value from 128 through 32767.</span></span>  
  
     <span data-ttu-id="c7381-172">使用 **max worker threads** 选项配置可用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程的工作线程数。</span><span class="sxs-lookup"><span data-stu-id="c7381-172">Use the **max worker threads** option to configure the number of worker threads available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] processes.</span></span> <span data-ttu-id="c7381-173">**max worker threads** 的默认设置适用于大多数系统。</span><span class="sxs-lookup"><span data-stu-id="c7381-173">The default setting for **max worker threads** is best for most systems.</span></span> <span data-ttu-id="c7381-174">不过，根据您的系统配置，有时将 **max worker threads** 设置为较小的值会提高性能。</span><span class="sxs-lookup"><span data-stu-id="c7381-174">However, depending on your system configuration, setting **max worker threads** to a smaller value sometimes improves performance.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c7381-175">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c7381-175">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-max-worker-threads-option"></a><span data-ttu-id="c7381-176">配置 max worker threads 选项</span><span class="sxs-lookup"><span data-stu-id="c7381-176">To configure the max worker threads option</span></span>  
  
1.  <span data-ttu-id="c7381-177">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c7381-177">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c7381-178">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="c7381-178">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c7381-179">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="c7381-179">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="c7381-180">此示例说明如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将 `max worker threads` 选项的值配置为 `900`。</span><span class="sxs-lookup"><span data-stu-id="c7381-180">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the `max worker threads` option to `900`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'max worker threads', 900 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="c7381-181">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="c7381-181">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-max-worker-threads-option"></a><a name="FollowUp"></a> <span data-ttu-id="c7381-182">跟进：在配置“最大工作线程数”选项后</span><span class="sxs-lookup"><span data-stu-id="c7381-182">Follow Up: After you configure the max worker threads option</span></span>  
 <span data-ttu-id="c7381-183">此更改将立即生效，而无需重新启动 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c7381-183">The change will take effect immediately without requiring the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to restart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7381-184">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c7381-184">See Also</span></span>  
 <span data-ttu-id="c7381-185">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c7381-185">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="c7381-186">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c7381-186">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="c7381-187">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c7381-187">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="c7381-188">用于数据库管理员的诊断连接</span><span class="sxs-lookup"><span data-stu-id="c7381-188">Diagnostic Connection for Database Administrators</span></span>](diagnostic-connection-for-database-administrators.md)  
  
  
