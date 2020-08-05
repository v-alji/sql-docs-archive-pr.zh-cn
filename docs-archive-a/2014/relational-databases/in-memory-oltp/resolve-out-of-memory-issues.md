---
title: 解决内存不足问题 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f855e931-7502-44bd-8a8b-b8543645c7f4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f5f57725d559b0cd62679550e2bb7c04dbd7e2bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580749"
---
# <a name="resolve-out-of-memory-issues"></a><span data-ttu-id="bac13-102">解决内存不足问题</span><span class="sxs-lookup"><span data-stu-id="bac13-102">Resolve Out Of Memory Issues</span></span>
  [!INCLUDE[hek_1](../../includes/hek-1-md.md)] <span data-ttu-id="bac13-103">相比， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bac13-103">uses more memory and in different ways than does [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bac13-104">随着需求的不断增加，为 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 安装和分配的内存量可能会不足。</span><span class="sxs-lookup"><span data-stu-id="bac13-104">It is possible that the amount of memory you installed and allocated for [!INCLUDE[hek_2](../../includes/hek-2-md.md)] becomes inadequate for your growing needs.</span></span> <span data-ttu-id="bac13-105">这时内存就会不足。</span><span class="sxs-lookup"><span data-stu-id="bac13-105">If so, you could run out of memory.</span></span> <span data-ttu-id="bac13-106">本主题介绍如何从 OOM 情况恢复。</span><span class="sxs-lookup"><span data-stu-id="bac13-106">This topic covers how to recover from an OOM situation.</span></span> <span data-ttu-id="bac13-107">有关可帮助你避免很多 OOM 情况的指南，请参阅 [内存使用情况的监视和故障排除](monitor-and-troubleshoot-memory-usage.md) 。</span><span class="sxs-lookup"><span data-stu-id="bac13-107">See [Monitor and Troubleshoot Memory Usage](monitor-and-troubleshoot-memory-usage.md) for guidance that can help you avoid many OOM situations.</span></span>  
  
## <a name="covered-in-this-topic"></a><span data-ttu-id="bac13-108">本主题的内容</span><span class="sxs-lookup"><span data-stu-id="bac13-108">Covered in this topic</span></span>  
  
|<span data-ttu-id="bac13-109">主题</span><span class="sxs-lookup"><span data-stu-id="bac13-109">Topic</span></span>|<span data-ttu-id="bac13-110">概述</span><span class="sxs-lookup"><span data-stu-id="bac13-110">Overview</span></span>|  
|-----------|--------------|  
| [<span data-ttu-id="bac13-111">解决 OOM 导致的数据库还原故障</span><span class="sxs-lookup"><span data-stu-id="bac13-111">Resolve database restore failures due to OOM</span></span>](#resolve-database-restore-failures-due-to-oom) |<span data-ttu-id="bac13-112">收到错误消息“由于资源池 '\<resourcePoolName>' 内存不足，数据库 '\<databaseName>' 的还原操作失败”时应采取的操作 。</span><span class="sxs-lookup"><span data-stu-id="bac13-112">What to do if you get the error message, "Restore operation failed for database '*\<databaseName>*' due to insufficient memory in the resource pool '*\<resourcePoolName>*'."</span></span>|  
| [<span data-ttu-id="bac13-113">消除工作负荷的低内存或 OOM 情况的影响</span><span class="sxs-lookup"><span data-stu-id="bac13-113">Resolve impact of low memory or OOM conditions on the workload</span></span>](#resolve-impact-of-low-memory-or-oom-conditions-on-the-workload)|<span data-ttu-id="bac13-114">发现内存不足问题对性能产生负面影响时应采取的操作。</span><span class="sxs-lookup"><span data-stu-id="bac13-114">What to do if you find low memory issues are negatively impacting performance.</span></span>|  
| [<span data-ttu-id="bac13-115">在提供足够内存时，解决由于内存不足导致的页分配失败问题</span><span class="sxs-lookup"><span data-stu-id="bac13-115">Resolve page allocation failures due to insufficient memory when sufficient memory is available</span></span>](#resolve-page-allocation-failures-due-to-insufficient-memory-when-sufficient-memory-is-available) |<span data-ttu-id="bac13-116">收到错误消息“由于资源池 '\<resourcePoolName>' 内存不足，不允许对数据库 '\<databaseName>' 进行页分配”时应采取的操作 。</span><span class="sxs-lookup"><span data-stu-id="bac13-116">What to do if you get the error message, "Disallowing page allocations for database '*\<databaseName>*' due to insufficient memory in the resource pool '*\<resourcePoolName>*'.</span></span> <span data-ttu-id="bac13-117">……”当可用内存足以进行操作时。</span><span class="sxs-lookup"><span data-stu-id="bac13-117">..." when available memory is sufficient for the operation.</span></span>|  
  
## <a name="resolve-database-restore-failures-due-to-oom"></a><span data-ttu-id="bac13-118">解决 OOM 导致的数据库还原故障</span><span class="sxs-lookup"><span data-stu-id="bac13-118">Resolve database restore failures due to OOM</span></span>  
 <span data-ttu-id="bac13-119">尝试还原数据库时，可能会收到以下错误消息： " *\<databaseName>* 由于资源池" "中的内存不足，数据库" "的还原操作失败 *\<resourcePoolName>* 。"你必须通过使更多内存可用来解决内存不足问题，然后才能成功还原数据库。</span><span class="sxs-lookup"><span data-stu-id="bac13-119">When you attempt to restore a database you may get the error message: "Restore operation failed for database '*\<databaseName>*' due to insufficient memory in the resource pool '*\<resourcePoolName>*'." Before you can successfully restore the database you must resolve the insufficient memory issue by making more memory available.</span></span>  
  
 <span data-ttu-id="bac13-120">若要解决 OOM 导致的还原故障，请使用以下任何或所有方法以便增加可用内存，来暂时增加可用于恢复操作的内存。</span><span class="sxs-lookup"><span data-stu-id="bac13-120">To resolve recovery failure due to OOM increase available memory using any or al of these means to temporarily increase memory available for the recovery operation.</span></span>  
  
-   <span data-ttu-id="bac13-121">临时关闭正在运行的应用程序。</span><span class="sxs-lookup"><span data-stu-id="bac13-121">Temporarily close running applications.</span></span>   
    <span data-ttu-id="bac13-122">通过关闭一个或多个正在运行的应用程序，如 Visual Studio、Internet Explorer、OneNote 等，可以将它们使用的内存用于还原操作。</span><span class="sxs-lookup"><span data-stu-id="bac13-122">By closing one or more running applications, such as Visual Studio, Internet Explorer, OneNote, and others, you make the memory they were using available for the restore operation.</span></span> <span data-ttu-id="bac13-123">您可以在成功还原后重新启动这些应用程序。</span><span class="sxs-lookup"><span data-stu-id="bac13-123">You can restart them following the successful restore.</span></span>  
  
-   <span data-ttu-id="bac13-124">增加 MAX_MEMORY_PERCENT 值。</span><span class="sxs-lookup"><span data-stu-id="bac13-124">Increase the value of MAX_MEMORY_PERCENT.</span></span>   
    <span data-ttu-id="bac13-125">此代码段将资源池 PoolHk 的 MAX_MEMORY_PERCENT 更改为所安装内存的 70%。</span><span class="sxs-lookup"><span data-stu-id="bac13-125">This code snippet changes MAX_MEMORY_PERCENT for the resource pool PoolHk to 70% of installed memory.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="bac13-126">如果服务器在虚拟机上运行，并且不是专用服务器，请将 MIN_MEMORY_PERCENT 设置为与 MAX_MEMORY_PERCENT 相同的值。</span><span class="sxs-lookup"><span data-stu-id="bac13-126">If the server is running on a VM and is not dedicated, set the value of MIN_MEMORY_PERCENT to the same value as MAX_MEMORY_PERCENT.</span></span>   
    > <span data-ttu-id="bac13-127">有关详细信息，请参阅主题[最佳做法：在虚拟机环境下使用内存中 OLTP](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="bac13-127">See the topic [Best Practices: Using In-Memory OLTP in a VM environment](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) for more information.</span></span>  
  
    ```sql  
  
    -- disable resource governor  
    ALTER RESOURCE GOVERNOR DISABLE  
  
    -- change the value of MAX_MEMORY_PERCENT  
    ALTER RESOURCE POOL PoolHk  
    WITH  
         ( MAX_MEMORY_PERCENT = 70 )  
    GO  
  
    -- reconfigure the Resource Governor  
    --    RECONFIGURE enables resource governor  
    ALTER RESOURCE GOVERNOR RECONFIGURE  
    GO  
  
    ```  
  
     <span data-ttu-id="bac13-128">有关 MAX_MEMORY_PERCENT 的最大值的信息，请参阅主题部分[可用于内存优化表和索引的内存百分比](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#percent-of-memory-available-for-memory-optimized-tables-and-indexes)</span><span class="sxs-lookup"><span data-stu-id="bac13-128">For information on maximum values for MAX_MEMORY_PERCENT see the topic section [Percent of memory available for memory-optimized tables and indexes](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#percent-of-memory-available-for-memory-optimized-tables-and-indexes)</span></span>
  
-   <span data-ttu-id="bac13-129">重新配置**最大服务器内存**。</span><span class="sxs-lookup"><span data-stu-id="bac13-129">Reconfigure **max server memory**.</span></span>  
    <span data-ttu-id="bac13-130">有关如何配置**最大服务器内存**[使用内存配置选项优化服务器性能](https://technet.microsoft.com/library/ms177455\(v=SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="bac13-130">For information on configuring **max server memory** see the topic [Optimizing Server Performance Using Memory Configuration Options](https://technet.microsoft.com/library/ms177455\(v=SQL.105\).aspx).</span></span>  
  
## <a name="resolve-impact-of-low-memory-or-oom-conditions-on-the-workload"></a><span data-ttu-id="bac13-131">消除工作负荷的低内存或 OOM 情况的影响</span><span class="sxs-lookup"><span data-stu-id="bac13-131">Resolve impact of low memory or OOM conditions on the workload</span></span>  
 <span data-ttu-id="bac13-132">当然，最好不要出现低内存或 OOM（内存不足）情况。</span><span class="sxs-lookup"><span data-stu-id="bac13-132">Obviously, it is best to not get into a low memory or OOM (Out of Memory) situation.</span></span> <span data-ttu-id="bac13-133">好的计划和监视有助于避免 OOM 情况。</span><span class="sxs-lookup"><span data-stu-id="bac13-133">Good planning and monitoring can help avoid OOM situations.</span></span> <span data-ttu-id="bac13-134">但再好的计划也并不总能预见实际情况，最后仍有可能遇到低内存或 OOM 情况。</span><span class="sxs-lookup"><span data-stu-id="bac13-134">Still, the best planning does not always foresee what actually happens and you might end up with low memory or OOM.</span></span> <span data-ttu-id="bac13-135">从 OOM 恢复有两个步骤：</span><span class="sxs-lookup"><span data-stu-id="bac13-135">There are two steps to recovering from OOM:</span></span>  
  
1.  [<span data-ttu-id="bac13-136">打开 DAC（专用管理员连接）</span><span class="sxs-lookup"><span data-stu-id="bac13-136">Open a DAC (Dedicated Administrator Connection)</span></span>](#open-a-dac-dedicated-administrator-connection) 
  
2.  [<span data-ttu-id="bac13-137">采取纠正措施</span><span class="sxs-lookup"><span data-stu-id="bac13-137">Take corrective action</span></span>](#take-corrective-action) 
  
### <a name="open-a-dac-dedicated-administrator-connection"></a><span data-ttu-id="bac13-138">打开 DAC（专用管理员连接）</span><span class="sxs-lookup"><span data-stu-id="bac13-138">Open a DAC (Dedicated Administrator Connection)</span></span>  
 <span data-ttu-id="bac13-139">Microsoft SQL Server 提供了专用管理员连接 (DAC)。</span><span class="sxs-lookup"><span data-stu-id="bac13-139">Microsoft SQL Server provides a dedicated administrator connection (DAC).</span></span> <span data-ttu-id="bac13-140">即使服务器对其他客户端连接停止响应，管理员也可以使用 DAC 访问正在运行的 SQL Server 数据库引擎实例来排除服务器上的故障。</span><span class="sxs-lookup"><span data-stu-id="bac13-140">The DAC allows an administrator to access a running instance of SQL Server Database Engine to troubleshoot problems on the server-even when the server is unresponsive to other client connections.</span></span> <span data-ttu-id="bac13-141">DAC 可通过 `sqlcmd` 实用工具和 SQL Server Management Studio (SSMS) 获得。</span><span class="sxs-lookup"><span data-stu-id="bac13-141">The DAC is available through the `sqlcmd` utility and SQL Server Management Studio (SSMS).</span></span>  
  
 <span data-ttu-id="bac13-142">有关如何使用 `sqlcmd` 和 DAC 的指南，请参阅 [使用专用管理员连接](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)。</span><span class="sxs-lookup"><span data-stu-id="bac13-142">For guidance on using `sqlcmd` and DAC see [Using a Dedicated Administrator Connection](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md).</span></span> <span data-ttu-id="bac13-143">有关通过 SSMS 使用 DAC 的指南，请参阅 [如何：将 SQL Server Management Studio 与专用管理员连接配合使用](https://msdn.microsoft.com/library/ms178068.aspx)。</span><span class="sxs-lookup"><span data-stu-id="bac13-143">For guidance on using DAC through SSMS see [How to: Use the Dedicated Administrator Connection with SQL Server Management Studio](https://msdn.microsoft.com/library/ms178068.aspx).</span></span>  
  
### <a name="take-corrective-action"></a><span data-ttu-id="bac13-144">采取纠正措施</span><span class="sxs-lookup"><span data-stu-id="bac13-144">Take corrective action</span></span>  
 <span data-ttu-id="bac13-145">要处理 OOM 情况，需要通过减少使用量释放现有内存，或者为内存中表提供更多可用内存。</span><span class="sxs-lookup"><span data-stu-id="bac13-145">To resolve your OOM condition you need to either free up existing memory by reducing usage, or make more memory available to your in-memory tables.</span></span>  
  
#### <a name="free-up-existing-memory"></a><span data-ttu-id="bac13-146">释放现有内存</span><span class="sxs-lookup"><span data-stu-id="bac13-146">Free up existing memory</span></span>  
  
##### <a name="delete-non-essential-memory-optimized-table-rows-and-wait-for-garbage-collection"></a><span data-ttu-id="bac13-147">删除不重要的内存优化表行并等待垃圾收集</span><span class="sxs-lookup"><span data-stu-id="bac13-147">Delete non-essential memory optimized table rows and wait for garbage collection</span></span>  
 <span data-ttu-id="bac13-148">您可以删除内存优化表中不重要的行。</span><span class="sxs-lookup"><span data-stu-id="bac13-148">You can remove non-essential rows from a memory optimized table.</span></span> <span data-ttu-id="bac13-149">垃圾收集器将这些行使用的内存返回可用内存</span><span class="sxs-lookup"><span data-stu-id="bac13-149">The garbage collector returns the memory used by these rows to available memory.</span></span> <span data-ttu-id="bac13-150">.</span><span class="sxs-lookup"><span data-stu-id="bac13-150">.</span></span> <span data-ttu-id="bac13-151">内存中 OLTP 引擎能够积极回收垃圾。</span><span class="sxs-lookup"><span data-stu-id="bac13-151">In-memory OLTP engine collects garbage rows aggressively.</span></span> <span data-ttu-id="bac13-152">但是，长时间运行的事务可能会妨碍垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="bac13-152">However, a long running transaction can prevent garbage collection.</span></span> <span data-ttu-id="bac13-153">例如，如果有一个事务运行 5 分钟，在事务活动期间，无法对所有因更新/删除操作而创建的行版本进行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="bac13-153">For example, if you have a transaction that runs for 5 minutes, any row versions created due to update/delete operations while the transaction was active can't be garbage collected.</span></span>  
  
##### <a name="move-one-or-more-rows-to-a-disk-based-table"></a><span data-ttu-id="bac13-154">将一行或多行移到基于磁盘的表</span><span class="sxs-lookup"><span data-stu-id="bac13-154">Move one or more rows to a disk-based table</span></span>  
 <span data-ttu-id="bac13-155">下面的 TechNet 文章提供有关将行从内存优化表移到基于磁盘的表的指导。</span><span class="sxs-lookup"><span data-stu-id="bac13-155">The following TechNet articles provide guidance on moving rows from a memory-optimized table to a disk-based table.</span></span>  
  
-   <span data-ttu-id="bac13-156">[应用程序级分区](https://technet.microsoft.com/library/dn296452\(v=sql.120\).aspx)</span><span class="sxs-lookup"><span data-stu-id="bac13-156">[Application-Level Partitioning](https://technet.microsoft.com/library/dn296452\(v=sql.120\).aspx)</span></span>  
  
-   <span data-ttu-id="bac13-157">[用于对内存优化表进行分区的应用程序模式](https://technet.microsoft.com/library/dn133171\(v=sql.120\).aspx)</span><span class="sxs-lookup"><span data-stu-id="bac13-157">[Application Pattern for Partitioning Memory-Optimized Tables](https://technet.microsoft.com/library/dn133171\(v=sql.120\).aspx)</span></span>  
  
#### <a name="increase-available-memory"></a><span data-ttu-id="bac13-158">增加可用内存</span><span class="sxs-lookup"><span data-stu-id="bac13-158">Increase available memory</span></span>  
  
##### <a name="increase-value-of-max_memory_percent-on-the-resource-pool"></a><span data-ttu-id="bac13-159">增加资源池的 MAX_MEMORY_PERCENT 值</span><span class="sxs-lookup"><span data-stu-id="bac13-159">Increase value of MAX_MEMORY_PERCENT on the resource pool</span></span>  
 <span data-ttu-id="bac13-160">如果尚未为内存中表创建命名资源池，应该创建一个，并将 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 数据库与其绑定。</span><span class="sxs-lookup"><span data-stu-id="bac13-160">If you have not created a named resource pool for your in-memory tables you should do that and bind your [!INCLUDE[hek_2](../../includes/hek-2-md.md)] databases to it.</span></span> <span data-ttu-id="bac13-161">有关如何创建并将 [数据库与资源池绑定的指南，请参阅主题](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) 将具有内存优化表的数据库绑定至资源池 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="bac13-161">See the topic [Bind a Database with Memory-Optimized Tables to a Resource Pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) for guidance on creating and binding your [!INCLUDE[hek_2](../../includes/hek-2-md.md)] databases to a resource pool.</span></span>  
  
 <span data-ttu-id="bac13-162">如果 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 数据库绑定至资源池，可以增加资源池可访问的内存百分比。</span><span class="sxs-lookup"><span data-stu-id="bac13-162">If your [!INCLUDE[hek_2](../../includes/hek-2-md.md)] database is bound to a resource pool you may be able to increase the percent of memory the pool can access.</span></span> <span data-ttu-id="bac13-163">有关如何更改资源池的 MIN_MEMORY_PERCENT 和 MAX_MEMORY_PERCENT 值的指南，请参阅子主题 [更改现有池的 MIN_MEMORY_PERCENT 和 MAX_MEMORY_PERCENT](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool) 。</span><span class="sxs-lookup"><span data-stu-id="bac13-163">See the sub-topic [Change MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT on an existing pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool) for guidance on changing the value of MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT for a resource pool.</span></span>  
  
 <span data-ttu-id="bac13-164">增加 MAX_MEMORY_PERCENT 值。</span><span class="sxs-lookup"><span data-stu-id="bac13-164">Increase the value of MAX_MEMORY_PERCENT.</span></span>   
<span data-ttu-id="bac13-165">此代码段将资源池 PoolHk 的 MAX_MEMORY_PERCENT 更改为所安装内存的 70%。</span><span class="sxs-lookup"><span data-stu-id="bac13-165">This code snippet changes MAX_MEMORY_PERCENT for the resource pool PoolHk to 70% of installed memory.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bac13-166">如果服务器在虚拟机上运行，并且不是专用服务器，请将 MIN_MEMORY_PERCENT 和 MAX_MEMORY_PERCENT 设置为相同值。</span><span class="sxs-lookup"><span data-stu-id="bac13-166">If the server is running on a VM and is not dedicated, set the value of MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT to the same value.</span></span>   
> <span data-ttu-id="bac13-167">有关详细信息，请参阅主题[最佳做法：在虚拟机环境下使用内存中 OLTP](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="bac13-167">See the topic [Best Practices: Using In-Memory OLTP in a VM environment](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) for more information.</span></span>  
  
```sql  
  
-- disable resource governor  
ALTER RESOURCE GOVERNOR DISABLE  
  
-- change the value of MAX_MEMORY_PERCENT  
ALTER RESOURCE POOL PoolHk  
WITH  
     ( MAX_MEMORY_PERCENT = 70 )  
GO  
  
-- reconfigure the Resource Governor  
--    RECONFIGURE enables resource governor  
ALTER RESOURCE GOVERNOR RECONFIGURE  
GO  
  
```  
  
 <span data-ttu-id="bac13-168">有关 MAX_MEMORY_PERCENT 最大值的信息，请参阅主题部分 [可用于内存优化表和索引的内存百分比](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#percent-of-memory-available-for-memory-optimized-tables-and-indexes)。</span><span class="sxs-lookup"><span data-stu-id="bac13-168">For information on maximum values for MAX_MEMORY_PERCENT see the topic section [Percent of memory available for memory-optimized tables and indexes](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#percent-of-memory-available-for-memory-optimized-tables-and-indexes).</span></span>  
  
##### <a name="install-additional-memory"></a><span data-ttu-id="bac13-169">安装更多内存</span><span class="sxs-lookup"><span data-stu-id="bac13-169">Install additional memory</span></span>  
 <span data-ttu-id="bac13-170">如果可能，最终的最佳解决方案是安装更多物理内存。</span><span class="sxs-lookup"><span data-stu-id="bac13-170">Ultimately the best solution, if possible, is to install additional physical memory.</span></span> <span data-ttu-id="bac13-171">这时，请注意，还是可以增加 MAX_MEMORY_PERCENT 的值（请参阅子主题[更改现有池的 MIN_MEMORY_PERCENT 和 MAX_MEMORY_PERCENT](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool)），因为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可能不需要更多内存，当新安装的内存不能都用于此资源池时，这可以得到最好的效果。</span><span class="sxs-lookup"><span data-stu-id="bac13-171">If you do this, remember that you will probably be able to also increase the value of MAX_MEMORY_PERCENT (see the sub-topic [Change MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT on an existing pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool)) since [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] won't likely need more memory, allowing you to make most if not all of the newly installed memory available to the resource pool.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bac13-172">如果服务器在虚拟机上运行，并且不是专用服务器，请将 MIN_MEMORY_PERCENT 和 MAX_MEMORY_PERCENT 设置为相同值。</span><span class="sxs-lookup"><span data-stu-id="bac13-172">If the server is running on a VM and is not dedicated, set the value of MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT to the same value.</span></span>   
> <span data-ttu-id="bac13-173">有关详细信息，请参阅主题[最佳做法：在虚拟机环境下使用内存中 OLTP](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="bac13-173">See the topic [Best Practices: Using In-Memory OLTP in a VM environment](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) for more information.</span></span>  
  
## <a name="resolve-page-allocation-failures-due-to-insufficient-memory-when-sufficient-memory-is-available"></a><span data-ttu-id="bac13-174">在提供足够内存时，解决由于内存不足导致的页分配失败问题</span><span class="sxs-lookup"><span data-stu-id="bac13-174">Resolve page allocation failures due to insufficient memory when sufficient memory is available</span></span>  
 <span data-ttu-id="bac13-175">如果收到错误消息 " *\<databaseName>* 由于资源池" "中的内存不足，不允许数据库" "的页分配 *\<resourcePoolName>* 。</span><span class="sxs-lookup"><span data-stu-id="bac13-175">If you get the error message, "Disallowing page allocations for database '*\<databaseName>*' due to insufficient memory in the resource pool '*\<resourcePoolName>*'.</span></span> <span data-ttu-id="bac13-176">有关详细信息，请参阅 " <https://go.microsoft.com/fwlink/?LinkId=330673> "。</span><span class="sxs-lookup"><span data-stu-id="bac13-176">See '<https://go.microsoft.com/fwlink/?LinkId=330673>' for more information."</span></span> <span data-ttu-id="bac13-177">，这可能是因为禁用了资源调控器。</span><span class="sxs-lookup"><span data-stu-id="bac13-177">in the error log when the available physical memory is sufficient to allocate the page, it may be due to a disabled Resource Governor.</span></span> <span data-ttu-id="bac13-178">在资源调控器被禁用时，MEMORYBROKER_FOR_RESERVE 导致虚假内存压力。</span><span class="sxs-lookup"><span data-stu-id="bac13-178">When the Resource Governor is disabled MEMORYBROKER_FOR_RESERVE induces artificial memory pressure.</span></span>  
  
 <span data-ttu-id="bac13-179">若要解决此问题，您需要启用资源调控器。</span><span class="sxs-lookup"><span data-stu-id="bac13-179">To resolve this you need to enable the Resource Governor.</span></span>  
  
 <span data-ttu-id="bac13-180">有关使用对象资源管理器、资源调控器属性或 Transact-SQL 启用资源调控器的限制和局限以及指导的信息，请参阅 [启用资源调控器](https://technet.microsoft.com/library/bb895149.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="bac13-180">See [Enable Resource Governor](https://technet.microsoft.com/library/bb895149.aspx) for information on Limits and Restrictions as well as guidance on enabling Resource Governor using Object Explorer, Resource Governor properties, or Transact-SQL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bac13-181">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bac13-181">See Also</span></span>  
 <span data-ttu-id="bac13-182">[管理内存中 OLTP 的内存](../../database-engine/managing-memory-for-in-memory-oltp.md) </span><span class="sxs-lookup"><span data-stu-id="bac13-182">[Managing Memory for In-Memory OLTP](../../database-engine/managing-memory-for-in-memory-oltp.md) </span></span>  
 <span data-ttu-id="bac13-183">[内存使用情况的监视和故障排除](monitor-and-troubleshoot-memory-usage.md) </span><span class="sxs-lookup"><span data-stu-id="bac13-183">[Monitor and Troubleshoot Memory Usage](monitor-and-troubleshoot-memory-usage.md) </span></span>  
 <span data-ttu-id="bac13-184">[数据库与资源池绑定的指南，请参阅主题](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="bac13-184">[Bind a Database with Memory-Optimized Tables to a Resource Pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) </span></span>  
 [<span data-ttu-id="bac13-185">最佳做法：在虚拟机环境中使用内存中 OLTP</span><span class="sxs-lookup"><span data-stu-id="bac13-185">Best Practices: Using In-Memory OLTP in a VM environment</span></span>](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md)  
  
  
