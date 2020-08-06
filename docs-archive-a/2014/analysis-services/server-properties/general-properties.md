---
title: 常规属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- IdleConnectionTimeout property
- InstanceVisible property
- TempDir property
- AdminTimeout property
- MinIdleSessionTimeout property
- MaxIdleSessionTimeout property
- IdleOrphanSessionTimeout property
- BackupDir property
- CommitTimeout property
- ExternalCommandTimeout property
- Enabled property
- ForceCommitTimeout property
- Port property
- CoordinatorShutdownMode property
- ServerTimeout property
- AllowedBrowsingFolders property
- CoordinatorCancelCount property
- DataDir property
- CoordinatorQueryMaxThreads property
- CoordinatorExecutionMode property
- ExternalConnectionTimeout property
- CollationName property
- EnableFast1033Locale property
- CoordinatorBuildMaxThreads property
- Language property
- StatisticsStoreSize property
- RepositoryConnectionString property
ms.assetid: 88a8117c-396a-469f-a62d-c6f262504021
author: minewiskan
ms.author: owend
ms.openlocfilehash: ca746a1bb57e84cf0f6a8f47622b118c7180eb1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694587"
---
# <a name="general-properties"></a><span data-ttu-id="40588-102">常规属性</span><span class="sxs-lookup"><span data-stu-id="40588-102">General Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="40588-103">支持下表中列出的服务器属性。</span><span class="sxs-lookup"><span data-stu-id="40588-103">supports the server properties listed in the following tables.</span></span> <span data-ttu-id="40588-104">本主题介绍 msmdsrv.ini 文件中未专门介绍的那些服务器属性，如 Security、Network 或 ThreadPool。</span><span class="sxs-lookup"><span data-stu-id="40588-104">This topic documents those server properties in the msmdsrv.ini file that are not otherwise included in a specific section, such as Security, Network, or ThreadPool.</span></span> <span data-ttu-id="40588-105">有关更多服务器属性以及如何设置这些属性的详细信息，请参阅 [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="40588-105">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="40588-106">**适用于：** 多维和表格服务器模式，除非另外说明。</span><span class="sxs-lookup"><span data-stu-id="40588-106">**Applies to:** Multidimensional and Tabular server mode, unless noted otherwise</span></span>  
  
## <a name="non-specific-category"></a><span data-ttu-id="40588-107">非特定类别</span><span class="sxs-lookup"><span data-stu-id="40588-107">Non-Specific Category</span></span>  
 `AdminTimeout`  
 <span data-ttu-id="40588-108">有符号 32 位整数属性，用于定义管理员超时值（秒）。</span><span class="sxs-lookup"><span data-stu-id="40588-108">A signed 32-bit integer property that defines the administrator timeout in seconds.</span></span> <span data-ttu-id="40588-109">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="40588-109">This is an advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="40588-110">此属性的默认值为零 (0)，指示没有超时设置。</span><span class="sxs-lookup"><span data-stu-id="40588-110">The default value for this property is zero (0), which indicates there is no timeout.</span></span>  
  
 `AllowedBrowsingFolders`  
 <span data-ttu-id="40588-111">一个字符串属性，它在分隔的列表中指定在 Analysis Services 对话框中保存、打开和查找文件时可浏览的文件夹。</span><span class="sxs-lookup"><span data-stu-id="40588-111">A string property that specifies in a delimited list the folders that can be browsed when saving, opening, and finding files in Analysis Services dialog boxes.</span></span> <span data-ttu-id="40588-112">Analysis Services 服务帐户必须对您添加到该列表的所有文件夹都具有读写权限。</span><span class="sxs-lookup"><span data-stu-id="40588-112">The Analysis Services service account must have read and write permissions to any folders that you add to the list.</span></span>  
  
 `BackupDir`  
 <span data-ttu-id="40588-113">一个字符串属性，用于标识默认情况下存储备份文件的目录的名称，如果未将路径指定为 Backup 命令的一部分。</span><span class="sxs-lookup"><span data-stu-id="40588-113">A string property that identifies the name of the directory where backup files are stored by default, in the event a path is not specified as part of the Backup command.</span></span>  
  
 `CollationName`  
 <span data-ttu-id="40588-114">字符串属性，用于标识服务器排序规则。</span><span class="sxs-lookup"><span data-stu-id="40588-114">A string property that identifies the server collation.</span></span> <span data-ttu-id="40588-115">有关详细信息，请参阅[语言和排序规则 (Analysis Services)](../languages-and-collations-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="40588-115">For more information, see [Languages and Collations &#40;Analysis Services&#41;](../languages-and-collations-analysis-services.md).</span></span>  
  
 `CommitTimeout`  
 <span data-ttu-id="40588-116">一个整数属性，它指定服务器出于提交事务的目的将等待获取写入锁的时间（毫秒）。</span><span class="sxs-lookup"><span data-stu-id="40588-116">An integer property that specifies how long (in milliseconds) the server will wait to acquire a write lock for the purpose of committing a transaction.</span></span> <span data-ttu-id="40588-117">通常需要一个等待时间，因为服务器必须等待其他锁释放，然后才能获取提交事务的写入锁。</span><span class="sxs-lookup"><span data-stu-id="40588-117">A waiting period is often required because the server must wait for other locks to be released before it can take a write lock that commits the transaction.</span></span>  
  
 <span data-ttu-id="40588-118">此属性的默认值为零 (0)，指示服务器将无限期等待。</span><span class="sxs-lookup"><span data-stu-id="40588-118">The default value for this property is zero (0), which indicates that the server will wait indefinitely.</span></span> <span data-ttu-id="40588-119">有关与锁相关的属性的详细信息，请参阅 [SQL Server 2008 R2 Analysis Services 操作指南](https://go.microsoft.com/fwlink/?LinkID=225539)。</span><span class="sxs-lookup"><span data-stu-id="40588-119">For more information about lock-related properties, see [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
 `CoordinatorBuildMaxThreads`  
 <span data-ttu-id="40588-120">有符号 32 位整数属性，用于定义为生成分区索引分配的最大线程数。</span><span class="sxs-lookup"><span data-stu-id="40588-120">A signed 32-bit integer property that defines the maximum number of threads allocated to building partition indexes.</span></span> <span data-ttu-id="40588-121">如果增加此值，则可加快分区索引速度，同时增加内存使用的开销。</span><span class="sxs-lookup"><span data-stu-id="40588-121">Increase this value in order to speed-up partition indexing, at the cost of memory usage.</span></span> <span data-ttu-id="40588-122">有关此属性的详细信息，请参阅 [SQL Server 2008 R2 Analysis Services 操作指南](https://go.microsoft.com/fwlink/?LinkID=225539)。</span><span class="sxs-lookup"><span data-stu-id="40588-122">For more information about this property, see [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
 `CoordinatorCancelCount`  
 <span data-ttu-id="40588-123">有符号 32 位整数属性，用于定义服务器应检查是否发生取消事件的频率（基于内部迭代计数）。</span><span class="sxs-lookup"><span data-stu-id="40588-123">A signed 32-bit integer property that defines how frequently the server should check whether a Cancel event occurred (based on internal iteration count).</span></span> <span data-ttu-id="40588-124">如果减小此值，则可加快检查取消事件的频率，同时将降低系统的整体性能。</span><span class="sxs-lookup"><span data-stu-id="40588-124">Decrease this number in order to check for Cancel more frequently, at the expense of general performance.</span></span>  
  
 <span data-ttu-id="40588-125">`CoordinatorCancelCount` 在表格服务器模式下将被忽略。</span><span class="sxs-lookup"><span data-stu-id="40588-125">`CoordinatorCancelCount` is ignored in tabular server mode.</span></span>  
  
 `CoordinatorExecutionMode`  
 <span data-ttu-id="40588-126">有符号 32 位整数属性，用于定义服务器将尝试的最大并行操作（包括处理操作和查询操作）数。</span><span class="sxs-lookup"><span data-stu-id="40588-126">A signed 32-bit integer property that defines the maximum number of parallel operations the server will attempt, including processing and querying operations.</span></span> <span data-ttu-id="40588-127">零 (0) 指示服务器将基于内部算法来决定。</span><span class="sxs-lookup"><span data-stu-id="40588-127">Zero (0) indicates that the server will decide, based on an internal algorithm.</span></span> <span data-ttu-id="40588-128">正数指示最大操作总数。</span><span class="sxs-lookup"><span data-stu-id="40588-128">A positive number indicates the maximum number of operations in total.</span></span> <span data-ttu-id="40588-129">如果是符号相反的负数，则指示每个处理器的最大操作数。</span><span class="sxs-lookup"><span data-stu-id="40588-129">A negative number, with the sign reversed, indicates the maximum number of operations per processor.</span></span>  
  
 <span data-ttu-id="40588-130">`CoordinatorExecutionMode` 在表格服务器模式下将被忽略。</span><span class="sxs-lookup"><span data-stu-id="40588-130">`CoordinatorExecutionMode` is ignored in tabular server mode.</span></span>  
  
 <span data-ttu-id="40588-131">此属性的默认值为 -4，指示将服务器限制为每个处理器 4 个并行操作。</span><span class="sxs-lookup"><span data-stu-id="40588-131">The default value for this property is -4, which indicates the server is limited to 4 parallel operations per processor.</span></span> <span data-ttu-id="40588-132">有关此属性的详细信息，请参阅 [SQL Server 2008 R2 Analysis Services 操作指南](https://go.microsoft.com/fwlink/?LinkID=225539)。</span><span class="sxs-lookup"><span data-stu-id="40588-132">For more information about this property, see [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
 `CoordinatorQueryMaxThreads`  
 <span data-ttu-id="40588-133">有符号 32 位整数属性，用于定义在查询解析期间每个分区段的最大线程数。</span><span class="sxs-lookup"><span data-stu-id="40588-133">A signed 32-bit integer property that defines the maximum number of threads per partition segment during query resolution.</span></span> <span data-ttu-id="40588-134">并发用户数越少，此值就会越高，同时会增加内存开销。</span><span class="sxs-lookup"><span data-stu-id="40588-134">The fewer the number of concurrent users, the higher this value can be, at the cost of memory.</span></span> <span data-ttu-id="40588-135">相反，如果并发用户数很大，则此值就可能降低。</span><span class="sxs-lookup"><span data-stu-id="40588-135">Conversely, it may need to be lowered if there are a large number of concurrent users.</span></span>  
  
 `CoordinatorShutdownMode`  
 <span data-ttu-id="40588-136">布尔值属性，用于定义协调器关闭模式。</span><span class="sxs-lookup"><span data-stu-id="40588-136">A Boolean property that defines coordinator shutdown mode.</span></span> <span data-ttu-id="40588-137">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="40588-137">This is an advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataDir`  
 <span data-ttu-id="40588-138">字符串属性，用于标识存储数据的目录的名称。</span><span class="sxs-lookup"><span data-stu-id="40588-138">A string property that identifies the name of the directory where data is stored.</span></span>  
  
 `DeploymentMode`  
 <span data-ttu-id="40588-139">确定 Analysis Services 服务器实例的操作上下文。</span><span class="sxs-lookup"><span data-stu-id="40588-139">Determines the operational context of an Analysis Services server instance.</span></span> <span data-ttu-id="40588-140">此属性在对话框、消息和文档中称为 "服务器模式"。</span><span class="sxs-lookup"><span data-stu-id="40588-140">This property is referred to as 'server mode' in dialog boxes, messages, and documentation.</span></span> <span data-ttu-id="40588-141">此属性由 SQL Server 安装程序根据安装 Analysis Services 时所选择的服务器模式进行相应配置。</span><span class="sxs-lookup"><span data-stu-id="40588-141">This property is configured by SQL Server Setup based on the server mode you selected when installing Analysis Services.</span></span> <span data-ttu-id="40588-142">只应考虑在内部使用此属性，并且始终使用安装程序指定的值。</span><span class="sxs-lookup"><span data-stu-id="40588-142">This property should be considered internal only, always using the value specified by Setup.</span></span>  
  
 <span data-ttu-id="40588-143">此属性的有效值包括以下项：</span><span class="sxs-lookup"><span data-stu-id="40588-143">Valid values for this property include the following:</span></span>  
  
|<span data-ttu-id="40588-144">值</span><span class="sxs-lookup"><span data-stu-id="40588-144">Value</span></span>|<span data-ttu-id="40588-145">说明</span><span class="sxs-lookup"><span data-stu-id="40588-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="40588-146">0</span><span class="sxs-lookup"><span data-stu-id="40588-146">0</span></span>|<span data-ttu-id="40588-147">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="40588-147">This is the default value.</span></span> <span data-ttu-id="40588-148">它指定多维模式，用于支持使用 MOLAP、HOLAP 和 ROLAP 存储以及数据挖掘模型的多维数据库。</span><span class="sxs-lookup"><span data-stu-id="40588-148">It specifies multidimensional mode, used to service multidimensional databases that use MOLAP, HOLAP, and ROLAP storage, as well as data mining models.</span></span>|  
|<span data-ttu-id="40588-149">1</span><span class="sxs-lookup"><span data-stu-id="40588-149">1</span></span>|<span data-ttu-id="40588-150">指定 Analysis Services 实例已作为 PowerPivot for SharePoint 部署的一部分安装。</span><span class="sxs-lookup"><span data-stu-id="40588-150">Specifies Analysis Services instances that were installed as part of a PowerPivot for SharePoint deployment.</span></span> <span data-ttu-id="40588-151">不要更改作为 PowerPivot for SharePoint 安装的一部分的 Analysis Services 实例的部署模式属性。</span><span class="sxs-lookup"><span data-stu-id="40588-151">Do not change the deployment mode property of Analysis Services instance that is part of a PowerPivot for SharePoint installation.</span></span> <span data-ttu-id="40588-152">如果您更改该模式，PowerPivot 数据将不再在该服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="40588-152">PowerPivot data will no longer run on the server if you change the mode.</span></span>|  
|<span data-ttu-id="40588-153">2</span><span class="sxs-lookup"><span data-stu-id="40588-153">2</span></span>|<span data-ttu-id="40588-154">指定用于承载使用内存中存储或 DirectQuery 存储的表格模型数据库的表格模式。</span><span class="sxs-lookup"><span data-stu-id="40588-154">Specifies Tabular mode used for hosting tabular model databases that use in-memory storage or DirectQuery storage.</span></span>|  
  
 <span data-ttu-id="40588-155">每个模式与其他模式都是互斥的。</span><span class="sxs-lookup"><span data-stu-id="40588-155">Each mode is exclusive of the other.</span></span> <span data-ttu-id="40588-156">配置为表格模式的服务器不能运行包含多维数据集和维度的 Analysis Services 数据库。</span><span class="sxs-lookup"><span data-stu-id="40588-156">A server that is configured for tabular mode cannot run Analysis Services databases that contain cubes and dimensions.</span></span> <span data-ttu-id="40588-157">如果基础计算机硬件能够支持，则您可以在同一台计算机上安装 Analysis Services 的多个实例并且对每个实例进行配置以便使用不同的部署模式。</span><span class="sxs-lookup"><span data-stu-id="40588-157">If the underlying computer hardware can support it, you can install multiple instances of Analysis Services on the same computer and configure each instance to use a different deployment mode.</span></span> <span data-ttu-id="40588-158">请记住，Analysis Services 是一种消耗大量资源的应用程序。</span><span class="sxs-lookup"><span data-stu-id="40588-158">Remember that Analysis Services is a resource intensive application.</span></span> <span data-ttu-id="40588-159">仅推荐对于高端服务器，才在同一个系统上部署多个实例。</span><span class="sxs-lookup"><span data-stu-id="40588-159">Deploying multiple instances on the same system is recommended only for high-end servers.</span></span>  
  
 `EnableFast1033Locale`  
 <span data-ttu-id="40588-160">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="40588-160">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ExternalCommandTimeout`  
 <span data-ttu-id="40588-161">一个整数属性，用于定义向外部服务器（包括关系数据源和外部 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 服务器）发出的命令的超时值（秒）。</span><span class="sxs-lookup"><span data-stu-id="40588-161">An integer property that defines the timeout, in seconds, for commands issued to external servers, including relational data sources and external [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] servers.</span></span>  
  
 <span data-ttu-id="40588-162">此属性的默认值为 3600（秒）。</span><span class="sxs-lookup"><span data-stu-id="40588-162">The default value for this property is 3600 (seconds).</span></span>  
  
 `ExternalConnectionTimeout`  
 <span data-ttu-id="40588-163">一个整数属性，用于定义创建到外部服务器（包括关系数据源和外部 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 服务器）的连接的超时值（秒）。</span><span class="sxs-lookup"><span data-stu-id="40588-163">An integer property that defines the timeout, in seconds, for creating connections to external servers, including relational data sources and external [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] servers.</span></span> <span data-ttu-id="40588-164">如果在连接字符串中指定了连接超时，则忽略此属性。</span><span class="sxs-lookup"><span data-stu-id="40588-164">This property is ignored if a connection timeout is specified on the connection string.</span></span>  
  
 <span data-ttu-id="40588-165">此属性的默认值为 60（秒）。</span><span class="sxs-lookup"><span data-stu-id="40588-165">The default value for this property is 60 (seconds).</span></span>  
  
 `ForceCommitTimeout`  
 <span data-ttu-id="40588-166">一个整数属性，它指定写入提交操作在取消先于当前命令（包括正在处理的查询）执行的其他命令之前应等待的时间（毫秒）。</span><span class="sxs-lookup"><span data-stu-id="40588-166">An integer property that specifies how long, in milliseconds, a write commit operation should wait before canceling other commands that preceded the current command, including queries in progress.</span></span> <span data-ttu-id="40588-167">这允许提交事务通过取消较低优先级的操作（例如查询）来继续。</span><span class="sxs-lookup"><span data-stu-id="40588-167">This allows the commit transaction to proceed by canceling lower priority operations, such as queries.</span></span>  
  
 <span data-ttu-id="40588-168">此属性的默认值为 30 秒（30000 毫秒），指示在提交事务已等待 30 秒之前，其他命令不会被强制超时。</span><span class="sxs-lookup"><span data-stu-id="40588-168">The default value for this property is 30 seconds (30000 milliseconds), which indicates that other commands will not be forced to timeout until the commit transaction has been waiting for 30 seconds.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="40588-169">被此事件取消的查询和进程将报告以下错误消息：“`Server: The operation has been cancelled`”</span><span class="sxs-lookup"><span data-stu-id="40588-169">Queries and processes cancelled by this event will report the following error message: "`Server: The operation has been cancelled`"</span></span>  
  
 <span data-ttu-id="40588-170">有关此属性的详细信息，请参阅 [SQL Server 2008 R2 Analysis Services 操作指南](https://go.microsoft.com/fwlink/?LinkID=225539)。</span><span class="sxs-lookup"><span data-stu-id="40588-170">For more information about this property, see [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="40588-171">`ForceCommitTimeout` 适用于多维数据集处理命令和写回操作。</span><span class="sxs-lookup"><span data-stu-id="40588-171">`ForceCommitTimeout` applies to cube processing commands and to writeback operations.</span></span>  
  
 `IdleConnectionTimeout`  
 <span data-ttu-id="40588-172">一个整数属性，指定处于非活动状态的连接的超时值（秒）。</span><span class="sxs-lookup"><span data-stu-id="40588-172">An integer property that specifies a timeout, in seconds, for connections that are inactive.</span></span>  
  
 <span data-ttu-id="40588-173">此属性的默认值为零 (0)，指示空闲连接将不使用超时。</span><span class="sxs-lookup"><span data-stu-id="40588-173">The default value for this property is zero (0), which indicates that idle connections will not be timed out.</span></span>  
  
 `IdleOrphanSessionTimeout`  
 <span data-ttu-id="40588-174">一个整数属性，用于定义孤立会话将在服务器内存中保留的时间（秒）。</span><span class="sxs-lookup"><span data-stu-id="40588-174">An integer property that defines how long, in seconds, orphaned sessions will be retained in server memory.</span></span> <span data-ttu-id="40588-175">孤立会话是一种不再具有关联的连接的会话。</span><span class="sxs-lookup"><span data-stu-id="40588-175">An orphaned session is one that no longer has an associated connection.</span></span> <span data-ttu-id="40588-176">默认值为 120 秒。</span><span class="sxs-lookup"><span data-stu-id="40588-176">The default is 120 seconds.</span></span>  
  
 `InstanceVisible`  
 <span data-ttu-id="40588-177">一个布尔值属性，指示服务器实例对来自 SQL Server Browser 服务的发现实例请求是否可见。</span><span class="sxs-lookup"><span data-stu-id="40588-177">A Boolean property that indicates whether the server instance is visible to discover instance requests from SQL Server Browser service.</span></span> <span data-ttu-id="40588-178">默认值为 True。</span><span class="sxs-lookup"><span data-stu-id="40588-178">The default is True.</span></span> <span data-ttu-id="40588-179">如果将该属性设置为 false，则该实例对于 SQL Server Browser 不可见。</span><span class="sxs-lookup"><span data-stu-id="40588-179">If you set it to false, the instance is not visible to SQL Server Browser.</span></span>  
  
 `Language`  
 <span data-ttu-id="40588-180">字符串属性，用于定义语言（包括错误消息和数字格式）。</span><span class="sxs-lookup"><span data-stu-id="40588-180">A string property that defines the language, including error messages and number formatting.</span></span> <span data-ttu-id="40588-181">此属性优先级高于 CollationName 属性。</span><span class="sxs-lookup"><span data-stu-id="40588-181">This property overrides the CollationName property.</span></span>  
  
 <span data-ttu-id="40588-182">此属性的默认值为空，指示 CollationName 属性定义语言。</span><span class="sxs-lookup"><span data-stu-id="40588-182">The default value for this property is blank, which indicates that the CollationName property defines the language.</span></span>  
  
 `LogDir`  
 <span data-ttu-id="40588-183">字符串属性，用于标识包含服务器日志的目录的名称。</span><span class="sxs-lookup"><span data-stu-id="40588-183">A string property that identifies the name of the directory that contains server logs.</span></span> <span data-ttu-id="40588-184">此属性仅适用于使用磁盘文件进行日志记录的情况，这一点与数据库表相反（默认行为）。</span><span class="sxs-lookup"><span data-stu-id="40588-184">This property only applies when disk files are used for logging, as opposed to database tables (the default behavior).</span></span>  
  
 `MaxIdleSessionTimeout`  
 <span data-ttu-id="40588-185">一个整数属性，用于定义空闲会话最大超时值（秒）。</span><span class="sxs-lookup"><span data-stu-id="40588-185">An integer property that defines the maximum idle session timeout, in seconds.</span></span> <span data-ttu-id="40588-186">默认值为零 (0) ，指示会话永远不会超时。但是，如果服务器处于资源限制下，则仍将删除空闲会话。</span><span class="sxs-lookup"><span data-stu-id="40588-186">The default is zero (0), indicating that sessions are never timed out. However, idle sessions will still be removed if the server is under resource constraints.</span></span>  
  
 `MinIdleSessionTimeout`  
 <span data-ttu-id="40588-187">一个整数属性，用于定义空闲会话最小超时值（秒）。</span><span class="sxs-lookup"><span data-stu-id="40588-187">An integer property that defines the minimum time, in seconds, that idle sessions will timeout.</span></span> <span data-ttu-id="40588-188">默认值为 2700 秒。</span><span class="sxs-lookup"><span data-stu-id="40588-188">The default is 2700 seconds.</span></span> <span data-ttu-id="40588-189">达到此时间后，服务器可以终止空闲会话，但只在需要释放内存时才这样做。</span><span class="sxs-lookup"><span data-stu-id="40588-189">After this time expires, the server is permitted to end the idle session, but will only do so as memory is needed.</span></span>  
  
 `Port`  
 <span data-ttu-id="40588-190">一个整数属性，用于定义服务器侦听客户端连接所在的端口号。</span><span class="sxs-lookup"><span data-stu-id="40588-190">An integer property that defines the port number on which server will listen for client connections.</span></span> <span data-ttu-id="40588-191">如果未设置，服务器将动态查找第一个未使用的端口。</span><span class="sxs-lookup"><span data-stu-id="40588-191">If not set, server dynamically finds first unused port.</span></span>  
  
 <span data-ttu-id="40588-192">此属性的默认值为零 (0)，指示默认侦听端口 2383。</span><span class="sxs-lookup"><span data-stu-id="40588-192">The default value for this property is zero (0), which in turn defaults to port 2383.</span></span> <span data-ttu-id="40588-193">有关端口配置的详细信息，请参阅 [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)。</span><span class="sxs-lookup"><span data-stu-id="40588-193">For more information about port configuration, see [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).</span></span>  
  
 `ServerTimeout`  
 <span data-ttu-id="40588-194">一个整数，用于定义查询的超时值（秒）。</span><span class="sxs-lookup"><span data-stu-id="40588-194">An integer that defines the timeout, in seconds, for queries.</span></span> <span data-ttu-id="40588-195">默认值为 3600 秒（或 60 分钟）。</span><span class="sxs-lookup"><span data-stu-id="40588-195">The default is 3600 seconds (or 60 minutes).</span></span> <span data-ttu-id="40588-196">零 (0) 指定任何查询都不会超时。</span><span class="sxs-lookup"><span data-stu-id="40588-196">Zero (0) specifies that no queries will timeout.</span></span>  
  
 `TempDir`  
 <span data-ttu-id="40588-197">一个字符串属性，指定用于存储在处理、还原和其他操作过程中使用的临时文件的位置。</span><span class="sxs-lookup"><span data-stu-id="40588-197">A string property that specifies the location for storing temporary files used during processing, restoring, and other operations.</span></span> <span data-ttu-id="40588-198">此属性的默认值由安装程序确定。</span><span class="sxs-lookup"><span data-stu-id="40588-198">The default value for this property is determined by setup.</span></span> <span data-ttu-id="40588-199">如果未指定，则默认为 Data 目录。</span><span class="sxs-lookup"><span data-stu-id="40588-199">If not specified, the default is the Data directory.</span></span>  
  
## <a name="requestprioritization-category"></a><span data-ttu-id="40588-200">RequestPrioritization 类别</span><span class="sxs-lookup"><span data-stu-id="40588-200">RequestPrioritization Category</span></span>  
 `Enabled`  
 <span data-ttu-id="40588-201">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="40588-201">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `StatisticsStoreSize`  
 <span data-ttu-id="40588-202">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="40588-202">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40588-203">另请参阅</span><span class="sxs-lookup"><span data-stu-id="40588-203">See Also</span></span>  
 <span data-ttu-id="40588-204">[在 Analysis Services 中配置服务器属性](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="40588-204">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="40588-205">确定 Analysis Services 实例的服务器模式</span><span class="sxs-lookup"><span data-stu-id="40588-205">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
