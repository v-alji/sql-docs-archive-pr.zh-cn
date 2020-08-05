---
title: 性能计数器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], performance counters
- performance counters [Integration Services]
- data flow [Integration Services], performance
- counters [Integration Services]
- data flow engine [Integration Services]
ms.assetid: 11e17f4e-72ed-44d7-a71d-a68937a78e4c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1b20ac056894066114883153030943bec1c05963
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581353"
---
# <a name="performance-counters"></a><span data-ttu-id="97171-102">性能计数器</span><span class="sxs-lookup"><span data-stu-id="97171-102">Performance Counters</span></span>
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="97171-103">安装一组性能计数器，可用于监视数据流引擎的性能。</span><span class="sxs-lookup"><span data-stu-id="97171-103">installs a set of performance counters that you can use to monitor the performance of the data flow engine.</span></span> <span data-ttu-id="97171-104">例如，可以监视 "Buffers spooled" 计数器，以确定在运行包时数据缓冲区是否正在临时写入磁盘。</span><span class="sxs-lookup"><span data-stu-id="97171-104">For example, you can watch the "Buffers spooled" counter to determine whether data buffers are being written to disk temporarily while a package is running.</span></span> <span data-ttu-id="97171-105">此交换会降低性能并指示计算机内存不足。</span><span class="sxs-lookup"><span data-stu-id="97171-105">This swapping reduces performance and indicates that the computer has insufficient memory.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="97171-106">如果在运行 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的计算机上安装 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]，然后将该计算机升级到 [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)]，则升级过程会从该计算机删除 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 性能计数器。</span><span class="sxs-lookup"><span data-stu-id="97171-106">If you install [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] on a computer that is running [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], and then upgrade that computer to [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)], the upgrade process removes the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] performance counters from the computer.</span></span> <span data-ttu-id="97171-107">若要还原计算机上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 性能计数器，请在修复模式下运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序。</span><span class="sxs-lookup"><span data-stu-id="97171-107">To restore the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] performance counters on the computer, run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup in repair mode.</span></span>  
  
 <span data-ttu-id="97171-108">下表介绍了这些性能计数器：</span><span class="sxs-lookup"><span data-stu-id="97171-108">The following table describes the performance counters.</span></span>  
  
|<span data-ttu-id="97171-109">性能计数器</span><span class="sxs-lookup"><span data-stu-id="97171-109">Performance counter</span></span>|<span data-ttu-id="97171-110">说明</span><span class="sxs-lookup"><span data-stu-id="97171-110">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="97171-111">BLOB bytes read</span><span class="sxs-lookup"><span data-stu-id="97171-111">BLOB bytes read</span></span>|<span data-ttu-id="97171-112">数据流引擎从所有源中读取的二进制大型对象 (BLOB) 数据的字节数。</span><span class="sxs-lookup"><span data-stu-id="97171-112">The number of bytes of binary large object (BLOB) data that the data flow engine has read from all sources.</span></span>|  
|<span data-ttu-id="97171-113">BLOB bytes written</span><span class="sxs-lookup"><span data-stu-id="97171-113">BLOB bytes written</span></span>|<span data-ttu-id="97171-114">数据流引擎已写入所有目标的 BLOB 数据的字节数。</span><span class="sxs-lookup"><span data-stu-id="97171-114">The number of bytes of BLOB data that the data flow engine has written to all destinations.</span></span>|  
|<span data-ttu-id="97171-115">BLOB files in use</span><span class="sxs-lookup"><span data-stu-id="97171-115">BLOB files in use</span></span>|<span data-ttu-id="97171-116">数据流引擎当前用于假脱机的 BLOB 文件数。</span><span class="sxs-lookup"><span data-stu-id="97171-116">The number of BLOB files that the data flow engine currently is using for spooling.</span></span>|  
|<span data-ttu-id="97171-117">Buffer memory</span><span class="sxs-lookup"><span data-stu-id="97171-117">Buffer memory</span></span>|<span data-ttu-id="97171-118">正在使用的内存数量。</span><span class="sxs-lookup"><span data-stu-id="97171-118">The amount of memory that is in use.</span></span> <span data-ttu-id="97171-119">这可能包括物理内存和虚拟内存。</span><span class="sxs-lookup"><span data-stu-id="97171-119">This may include both physical and virtual memory.</span></span> <span data-ttu-id="97171-120">如果该数字大于物理内存量，则 **Buffers Spooled** 计数将随内存交换的增加而增加。</span><span class="sxs-lookup"><span data-stu-id="97171-120">When this number is larger than the amount of physical memory, the **Buffers Spooled** count rises as an indication that memory swapping is increasing.</span></span> <span data-ttu-id="97171-121">内存交换的增加会降低数据流引擎的性能。</span><span class="sxs-lookup"><span data-stu-id="97171-121">Increased memory swapping slows performance of the data flow engine.</span></span>|  
|<span data-ttu-id="97171-122">Buffers in use</span><span class="sxs-lookup"><span data-stu-id="97171-122">Buffers in use</span></span>|<span data-ttu-id="97171-123">数据流组件和数据流引擎当前使用的各种类型的缓冲区对象的数量。</span><span class="sxs-lookup"><span data-stu-id="97171-123">The number of buffer objects, of all types, that all data flow components and the data flow engine is currently using.</span></span>|  
|<span data-ttu-id="97171-124">Buffers Spooled</span><span class="sxs-lookup"><span data-stu-id="97171-124">Buffers spooled</span></span>|<span data-ttu-id="97171-125">当前写入磁盘的缓冲区的数量。</span><span class="sxs-lookup"><span data-stu-id="97171-125">The number of buffers currently written to the disk.</span></span> <span data-ttu-id="97171-126">如果数据流引擎运行时物理内存较低，则当前没有使用的缓冲区会被写入磁盘，然后在需要时重新加载。</span><span class="sxs-lookup"><span data-stu-id="97171-126">If the data flow engine runs low on physical memory, buffers not currently used are written to disk and then reloaded when needed.</span></span>|  
|<span data-ttu-id="97171-127">Flat buffer memory</span><span class="sxs-lookup"><span data-stu-id="97171-127">Flat buffer memory</span></span>|<span data-ttu-id="97171-128">所有平面缓冲区使用的内存总量（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="97171-128">The total amount of memory, in bytes, that all flat buffers use.</span></span> <span data-ttu-id="97171-129">平面缓冲区是组件用于存储数据的内存块。</span><span class="sxs-lookup"><span data-stu-id="97171-129">Flat buffers are blocks of memory that a component uses to store data.</span></span> <span data-ttu-id="97171-130">平面缓冲区是可逐字节访问的大型字节块。</span><span class="sxs-lookup"><span data-stu-id="97171-130">A flat buffer is a large block of bytes that is accessed byte by byte.</span></span>|  
|<span data-ttu-id="97171-131">Flat buffers in use</span><span class="sxs-lookup"><span data-stu-id="97171-131">Flat buffers in use</span></span>|<span data-ttu-id="97171-132">数据流引擎使用的平面缓冲区的数量。</span><span class="sxs-lookup"><span data-stu-id="97171-132">The number of flat buffers that the Data flow engine uses.</span></span> <span data-ttu-id="97171-133">所有平面缓冲区都是专用缓冲区。</span><span class="sxs-lookup"><span data-stu-id="97171-133">All flat buffers are private buffers.</span></span>|  
|<span data-ttu-id="97171-134">Private buffer memory</span><span class="sxs-lookup"><span data-stu-id="97171-134">Private buffer memory</span></span>|<span data-ttu-id="97171-135">所有专用缓冲区所使用的内存总量。</span><span class="sxs-lookup"><span data-stu-id="97171-135">The total amount of memory in use by all private buffers.</span></span> <span data-ttu-id="97171-136">如果数据流引擎创建的是一个支持数据流的缓冲区，则该缓冲区就不是专用缓冲区。</span><span class="sxs-lookup"><span data-stu-id="97171-136">A buffer is not private if the data flow engine creates it to support data flow.</span></span> <span data-ttu-id="97171-137">专用缓冲区是指转换仅用于临时工作的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="97171-137">A private buffer is a buffer that a transformation uses for temporary work only.</span></span> <span data-ttu-id="97171-138">例如，聚合转换使用专用缓冲区来完成其工作。</span><span class="sxs-lookup"><span data-stu-id="97171-138">For example, the Aggregation transformation uses private buffers to do its work.</span></span>|  
|<span data-ttu-id="97171-139">Private buffers in use</span><span class="sxs-lookup"><span data-stu-id="97171-139">Private buffers in use</span></span>|<span data-ttu-id="97171-140">转换使用的缓冲区的数量。</span><span class="sxs-lookup"><span data-stu-id="97171-140">The number of buffers that transformations use.</span></span>|  
|<span data-ttu-id="97171-141">Rows read</span><span class="sxs-lookup"><span data-stu-id="97171-141">Rows read</span></span>|<span data-ttu-id="97171-142">源产生的行数。</span><span class="sxs-lookup"><span data-stu-id="97171-142">The number of rows that a source produces.</span></span> <span data-ttu-id="97171-143">该数值不包括查找转换从引用表中读取的行数。</span><span class="sxs-lookup"><span data-stu-id="97171-143">The number does not include rows read from reference tables by the Lookup transformation.</span></span>|  
|<span data-ttu-id="97171-144">Rows written</span><span class="sxs-lookup"><span data-stu-id="97171-144">Rows written</span></span>|<span data-ttu-id="97171-145">提供给目标的行数。</span><span class="sxs-lookup"><span data-stu-id="97171-145">The number of rows offered to a destination.</span></span> <span data-ttu-id="97171-146">该数值不反映写入目标数据存储区中的行数。</span><span class="sxs-lookup"><span data-stu-id="97171-146">The number does not reflect rows written to the destination data store.</span></span>|  
  
 <span data-ttu-id="97171-147">您可以使用 Microsoft 管理控制台 (MMC) 管理单元“性能”来创建一个捕获性能计数器的日志。</span><span class="sxs-lookup"><span data-stu-id="97171-147">You use the Performance Microsoft Management Console (MMC) snap-in to create a log that captures performance counters.</span></span>  
  
 <span data-ttu-id="97171-148">有关如何提高性能的信息，请参阅 [数据流性能特点](../data-flow/data-flow-performance-features.md)。</span><span class="sxs-lookup"><span data-stu-id="97171-148">For information about how to improve performance, see [Data Flow Performance Features](../data-flow/data-flow-performance-features.md).</span></span>  
  
## <a name="obtain-performance-counter-statistics"></a><span data-ttu-id="97171-149">获取性能计数器统计信息</span><span class="sxs-lookup"><span data-stu-id="97171-149">Obtain Performance Counter Statistics</span></span>  
 <span data-ttu-id="97171-150">对于部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目，你可以通过使用 [dm_execution_performance_counters （SSISDB 数据库）](/sql/integration-services/functions-dm-execution-performance-counters)函数获取性能计数器统计信息。</span><span class="sxs-lookup"><span data-stu-id="97171-150">For [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] projects that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, you can obtain performance counter statistics by using the [dm_execution_performance_counters &#40;SSISDB Database&#41;](/sql/integration-services/functions-dm-execution-performance-counters) function.</span></span>  
  
 <span data-ttu-id="97171-151">在下面的示例中，该函数将返回 ID 为 34 的正在运行的执行的统计信息。</span><span class="sxs-lookup"><span data-stu-id="97171-151">In the following example, the function returns statistics for a running execution with an ID of 34.</span></span>  
  
```  
select * from [catalog].[dm_execution_performance_counters] (34)  
```  
  
 <span data-ttu-id="97171-152">在下面的示例中，该函数返回正在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器上运行的所有执行的统计信息。</span><span class="sxs-lookup"><span data-stu-id="97171-152">In the following example, the function returns statistics for all the executions running on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
```  
select * from [catalog].[dm_execution_performance_counters] (NULL)  
  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="97171-153">如果您是 `ssis_admin` 数据库角色的成员，将返回所有正在运行的执行的性能统计信息。</span><span class="sxs-lookup"><span data-stu-id="97171-153">If you are a member of the `ssis_admin` database role, performance statistics for all running executions are returned.</span></span>  <span data-ttu-id="97171-154">如果您不是 `ssis_admin` 数据库角色的成员，则返回您对其具有读权限的正在运行的执行的性能统计信息。</span><span class="sxs-lookup"><span data-stu-id="97171-154">If you are not a member of the `ssis_admin` database role, performance statistics for the running executions for which you have read permissions, are returned.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="97171-155">相关内容</span><span class="sxs-lookup"><span data-stu-id="97171-155">Related Content</span></span>  
  
-   <span data-ttu-id="97171-156">codeplex.com 上的工具 [Business Intelligence Development Studio 的 SSIS 性能可视化（CodePlex 项目）](https://go.microsoft.com/fwlink/?LinkId=146626)。</span><span class="sxs-lookup"><span data-stu-id="97171-156">Tool, [SSIS Performance Visualization for Business Intelligence Development Studio (CodePlex Project)](https://go.microsoft.com/fwlink/?LinkId=146626), on codeplex.com.</span></span>  
  
-   <span data-ttu-id="97171-157">msdn.microsoft.com 上的视频 [测量和了解 SSIS 包在企业中的性能（SQL Server 视频）](https://go.microsoft.com/fwlink/?LinkId=150497)。</span><span class="sxs-lookup"><span data-stu-id="97171-157">Video, [Measuring and Understanding the Performance of Your SSIS Packages in the Enterprise (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=150497), on msdn.microsoft.com.</span></span>  
  
-   <span data-ttu-id="97171-158">support.microsoft.com 上的支持文章 [升级到 Windows Server 2008 后性能监视器中不再提供 SSIS 性能计数器](https://go.microsoft.com/fwlink/?LinkId=235319)。</span><span class="sxs-lookup"><span data-stu-id="97171-158">Support article, [The SSIS performance counter is no longer available in the Performance Monitor after you upgrade to Windows Server 2008](https://go.microsoft.com/fwlink/?LinkId=235319), on support.microsoft.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97171-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="97171-159">See Also</span></span>  
 [<span data-ttu-id="97171-160">项目和包的执行</span><span class="sxs-lookup"><span data-stu-id="97171-160">Execution of Projects and Packages</span></span>](../packages/run-integration-services-ssis-packages.md)  
  
  
