---
title: Analysis Services 中的日志操作 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: aa1db060-95dc-4198-8aeb-cffdda44b140
author: minewiskan
ms.author: owend
ms.openlocfilehash: 95d0e41576e449ab10b243ef49cbe283940afe0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588740"
---
# <a name="log-operations-in-analysis-services"></a><span data-ttu-id="67e4f-102">Analysis Services 中的日志操作</span><span class="sxs-lookup"><span data-stu-id="67e4f-102">Log operations in Analysis Services</span></span>
  <span data-ttu-id="67e4f-103">Analysis Services 实例会将服务器通知、错误和警告记录到 msmdsrv.ini 文件中-每个安装的实例一个。</span><span class="sxs-lookup"><span data-stu-id="67e4f-103">An Analysis Services instance will log server notifications, errors, and warnings to the msmdsrv.log file - one for each instance you install.</span></span> <span data-ttu-id="67e4f-104">管理员参考此日志，了解例程和异常事件等信息。</span><span class="sxs-lookup"><span data-stu-id="67e4f-104">Administrators refer to this log for insights into routine and extraordinary events alike.</span></span> <span data-ttu-id="67e4f-105">在最新版本中，已增强日志记录，能容纳更多信息。</span><span class="sxs-lookup"><span data-stu-id="67e4f-105">In recent releases, logging has been enhanced to include more information.</span></span> <span data-ttu-id="67e4f-106">日志记录现在包括产品版本和版本信息以及处理器、内存、连接性和阻止事件。</span><span class="sxs-lookup"><span data-stu-id="67e4f-106">Log records now include product version and edition information, as well as processor, memory, connectivity, and blocking events.</span></span> <span data-ttu-id="67e4f-107">你可在 [日志记录改进](https://support.microsoft.com/kb/2965035)中查看整个更改列表。</span><span class="sxs-lookup"><span data-stu-id="67e4f-107">You can review the entire change list at [Logging improvements](https://support.microsoft.com/kb/2965035).</span></span>  
  
 <span data-ttu-id="67e4f-108">除了内置日志记录功能，许多管理员和开发人员还使用 Analysis Services 社区提供的工具来收集有关服务器操作（例如 **ASTrace**）的数据。</span><span class="sxs-lookup"><span data-stu-id="67e4f-108">Besides the built-in logging feature, many administrators and developers also use tools provided by the Analysis Services community to collect data about server operations, such as **ASTrace**.</span></span> <span data-ttu-id="67e4f-109">查看 [Microsoft SQL Server 社区示例：Analysis Services](https://sqlsrvanalysissrvcs.codeplex.com/) ，获得下载链接。</span><span class="sxs-lookup"><span data-stu-id="67e4f-109">See [Microsoft SQL Server Community Samples: Analysis Services](https://sqlsrvanalysissrvcs.codeplex.com/) for the download links.</span></span>  
  
 <span data-ttu-id="67e4f-110">本主题包含以下各节：</span><span class="sxs-lookup"><span data-stu-id="67e4f-110">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="67e4f-111">日志的位置和类型</span><span class="sxs-lookup"><span data-stu-id="67e4f-111">Location and types of logs</span></span>](#bkmk_location)  
  
-   [<span data-ttu-id="67e4f-112">日志文件配置设置的一般信息</span><span class="sxs-lookup"><span data-stu-id="67e4f-112">General information on log file configuration settings</span></span>](#bkmk_general)  
  
-   [<span data-ttu-id="67e4f-113">MSMDSRV 服务日志文件</span><span class="sxs-lookup"><span data-stu-id="67e4f-113">MSMDSRV service log file</span></span>](#bkmk_msmdsrv)  
  
-   [<span data-ttu-id="67e4f-114">查询日志</span><span class="sxs-lookup"><span data-stu-id="67e4f-114">Query logs</span></span>](#bkmk_querylog)  
  
-   [<span data-ttu-id="67e4f-115">Mini dump (.mdmp) 文件</span><span class="sxs-lookup"><span data-stu-id="67e4f-115">Mini dump (.mdmp) files</span></span>](#bkmk_mdmp)  
  
-   [<span data-ttu-id="67e4f-116">提示和最佳实践</span><span class="sxs-lookup"><span data-stu-id="67e4f-116">Tips and best practices</span></span>](#bkmk_tips)  
  
> [!NOTE]  
>  <span data-ttu-id="67e4f-117">如果你要查找日志记录的信息，你可能也对跟踪显示处理和查询执行路径的操作感兴趣。</span><span class="sxs-lookup"><span data-stu-id="67e4f-117">If you're looking for information about logging, you might also be interested in tracing operations that show processing and query execution paths.</span></span> <span data-ttu-id="67e4f-118">临时跟踪目标和持续跟踪目标（例如审核多维数据集访问）以及如何最大程度利用 Flight Recorder、SQL Server Profiler 和 xEvents 的建议可通过此页中的链接找到： [监视 Analysis Services 实例](monitor-an-analysis-services-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="67e4f-118">Trace objects for ad hoc and sustained tracing (such as auditing cube access) ─ as well as recommendations on how to best use Flight Recorder, SQL Server Profiler, and xEvents ─ can be found through the links on this page: [Monitor an Analysis Services Instance](monitor-an-analysis-services-instance.md).</span></span>  
  
##  <a name="location-and-types-of-logs"></a><a name="bkmk_location"></a><span data-ttu-id="67e4f-119">日志的位置和类型</span><span class="sxs-lookup"><span data-stu-id="67e4f-119">Location and types of logs</span></span>  
 <span data-ttu-id="67e4f-120">Analysis Services 提供有以下所述日志。</span><span class="sxs-lookup"><span data-stu-id="67e4f-120">Analysis Services provides the logs described below.</span></span>  
  
|<span data-ttu-id="67e4f-121">文件名或位置</span><span class="sxs-lookup"><span data-stu-id="67e4f-121">File name or Location</span></span>|<span data-ttu-id="67e4f-122">类型</span><span class="sxs-lookup"><span data-stu-id="67e4f-122">Type</span></span>|<span data-ttu-id="67e4f-123">用途</span><span class="sxs-lookup"><span data-stu-id="67e4f-123">Used for</span></span>|<span data-ttu-id="67e4f-124">默认开启</span><span class="sxs-lookup"><span data-stu-id="67e4f-124">On by default</span></span>|  
|---------------------------|----------|--------------|-------------------|  
|<span data-ttu-id="67e4f-125">Msmdsrv.log</span><span class="sxs-lookup"><span data-stu-id="67e4f-125">Msmdsrv.log</span></span>|<span data-ttu-id="67e4f-126">错误日志</span><span class="sxs-lookup"><span data-stu-id="67e4f-126">Error log</span></span>|<span data-ttu-id="67e4f-127">例程监控和基本故障排除</span><span class="sxs-lookup"><span data-stu-id="67e4f-127">Routine monitoring and basic troubleshooting</span></span>|<span data-ttu-id="67e4f-128">是</span><span class="sxs-lookup"><span data-stu-id="67e4f-128">Yes</span></span>|  
|<span data-ttu-id="67e4f-129">关系数据库中的 OlapQueryLog 表</span><span class="sxs-lookup"><span data-stu-id="67e4f-129">OlapQueryLog table in a relational database</span></span>|<span data-ttu-id="67e4f-130">查询日志</span><span class="sxs-lookup"><span data-stu-id="67e4f-130">Query log</span></span>|<span data-ttu-id="67e4f-131">为使用情况优化向导收集输入</span><span class="sxs-lookup"><span data-stu-id="67e4f-131">Collect inputs for the Usage Optimization Wizard</span></span>|<span data-ttu-id="67e4f-132">否</span><span class="sxs-lookup"><span data-stu-id="67e4f-132">No</span></span>|  
|<span data-ttu-id="67e4f-133">SQLDmp \<guid> . .mdmp 文件</span><span class="sxs-lookup"><span data-stu-id="67e4f-133">SQLDmp\<guid>.mdmp files</span></span>|<span data-ttu-id="67e4f-134">崩溃和异常</span><span class="sxs-lookup"><span data-stu-id="67e4f-134">Crashes and exceptions</span></span>|<span data-ttu-id="67e4f-135">深度故障排除</span><span class="sxs-lookup"><span data-stu-id="67e4f-135">Deep troubleshooting</span></span>|<span data-ttu-id="67e4f-136">否</span><span class="sxs-lookup"><span data-stu-id="67e4f-136">No</span></span>|  
  
 <span data-ttu-id="67e4f-137">我们强烈建议使用以下链接查看此主题中未涉及的其他信息资源： [来自 Microsoft 支持的初始数据集合提示](https://blogs.msdn.com/b/as_emea/archive/2012/01/02/initial-data-collection-for-troubleshooting-analysis-services-issues.aspx)。</span><span class="sxs-lookup"><span data-stu-id="67e4f-137">We highly recommend the following link for additional information resources not covered in this topic: [Initial data collection tips from Microsoft Support](https://blogs.msdn.com/b/as_emea/archive/2012/01/02/initial-data-collection-for-troubleshooting-analysis-services-issues.aspx).</span></span>  
  
##  <a name="general-information-on-log-file-configuration-settings"></a><a name="bkmk_general"></a><span data-ttu-id="67e4f-138">日志文件配置设置的一般信息</span><span class="sxs-lookup"><span data-stu-id="67e4f-138">General information on log file configuration settings</span></span>  
 <span data-ttu-id="67e4f-139">你可在 msmdsrv.ini 服务器配置文件中找到每个日志的部分，此文件位于 \Program Files\Microsoft SQL Server\MSAS12.MSSQLSERVER\OLAP\Config 文件夹。</span><span class="sxs-lookup"><span data-stu-id="67e4f-139">You can find sections for each log in the msmdsrv.ini server configuration file, located in the \Program Files\Microsoft SQL Server\MSAS12.MSSQLSERVER\OLAP\Config folder.</span></span> <span data-ttu-id="67e4f-140">有关编辑文件的说明，请参阅[在 Analysis Services 中配置服务器属性](../server-properties/server-properties-in-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="67e4f-140">See [Configure Server Properties in Analysis Services](../server-properties/server-properties-in-analysis-services.md) for instructions on editing the file.</span></span>  
  
 <span data-ttu-id="67e4f-141">如有可能，我们建议你在 Management Studio 的服务器属性页设置日志记录属性。</span><span class="sxs-lookup"><span data-stu-id="67e4f-141">Where possible, we suggest that you set logging properties in the server properties page of Management Studio.</span></span> <span data-ttu-id="67e4f-142">但是在某些情况下，你必须直接编辑 msmdsrv.ini 文件以配置管理工具中不可见的设置。</span><span class="sxs-lookup"><span data-stu-id="67e4f-142">Although in some cases, you must edit the msmdsrv.ini file directly to configure settings that are not visible in the administrative tools.</span></span>  
  
 <span data-ttu-id="67e4f-143">![显示日志设置的配置文件的部分](../media/ssas-logfilesettings.png "显示日志设置的配置文件的部分")</span><span class="sxs-lookup"><span data-stu-id="67e4f-143">![Section of the config file showing log settings](../media/ssas-logfilesettings.png "Section of the config file showing log settings")</span></span>  
  
##  <a name="msmdsrv-service-log-file"></a><a name="bkmk_msmdsrv"></a><span data-ttu-id="67e4f-144">MSMDSRV.INI 服务日志文件</span><span class="sxs-lookup"><span data-stu-id="67e4f-144">MSMDSRV service log file</span></span>  
 <span data-ttu-id="67e4f-145">Analysis Services 会将服务器操作记录到 msmdsrv.log 文件中，每个实例一个文件，位于 \program files\Microsoft SQL Server\\<instance\>\Olap\Log。</span><span class="sxs-lookup"><span data-stu-id="67e4f-145">Analysis Services logs server operations to the msmdsrv.log file, one per instance, located at \program files\Microsoft SQL Server\\<instance\>\Olap\Log.</span></span>  
  
 <span data-ttu-id="67e4f-146">此日志文件会在每次重启服务时被清空。</span><span class="sxs-lookup"><span data-stu-id="67e4f-146">This log file is emptied at each service restart.</span></span> <span data-ttu-id="67e4f-147">在以前版本中，管理员有时会重启服务，其唯一目的是在其变得过大不能使用前清空日志文件。</span><span class="sxs-lookup"><span data-stu-id="67e4f-147">In previous releases, administrators would sometimes restart the service for the sole purpose of flushing the log file before it could grow so large as to become unusable.</span></span> <span data-ttu-id="67e4f-148">现在已没有必要。</span><span class="sxs-lookup"><span data-stu-id="67e4f-148">This is no longer necessary.</span></span> <span data-ttu-id="67e4f-149">SQL Server 2012 SP2 和更高版本中引入的配置设置使你可控制日志文件及其历史记录的大小：</span><span class="sxs-lookup"><span data-stu-id="67e4f-149">Configuration settings, introduced in SQL Server 2012 SP2 and later, give you control over the size of the log file and its history:</span></span>  
  
-   <span data-ttu-id="67e4f-150">`MaxFileSizeMB` 指定最大日志文件大小 (MB)。</span><span class="sxs-lookup"><span data-stu-id="67e4f-150">`MaxFileSizeMB` specifies a maximum log file size in megabytes.</span></span> <span data-ttu-id="67e4f-151">默认值为 256。</span><span class="sxs-lookup"><span data-stu-id="67e4f-151">The default is 256.</span></span> <span data-ttu-id="67e4f-152">有效替换值必须是正整数。</span><span class="sxs-lookup"><span data-stu-id="67e4f-152">A valid replacement value must be a positive integer.</span></span> <span data-ttu-id="67e4f-153">达到 `MaxFileSizeMB` 时，Analysis Services 将当前文件重命名为 msmdsrv{current timestamp}.log 文件，然后启动新的 msmdsrv.log 文件。</span><span class="sxs-lookup"><span data-stu-id="67e4f-153">When `MaxFileSizeMB` is reached, Analysis Services renames the current file as msmdsrv{current timestamp}.log file, and starts a new msmdsrv.log file.</span></span>  
  
-   <span data-ttu-id="67e4f-154">`MaxNumberFiles`指定旧日志文件的保留期。</span><span class="sxs-lookup"><span data-stu-id="67e4f-154">`MaxNumberFiles` specifies retention of older log files.</span></span> <span data-ttu-id="67e4f-155">默认值为 0（禁用）。</span><span class="sxs-lookup"><span data-stu-id="67e4f-155">The default is 0 (disabled).</span></span> <span data-ttu-id="67e4f-156">你可将其更改为正整数以保持日志文件的版本。</span><span class="sxs-lookup"><span data-stu-id="67e4f-156">You can change it to a positive integer to keep versions of the log file.</span></span> <span data-ttu-id="67e4f-157">达到 `MaxNumberFiles` 时，Analysis Services 删除名称具有最旧时间戳的文件。</span><span class="sxs-lookup"><span data-stu-id="67e4f-157">When `MaxNumberFiles` is reached, Analysis Services deletes the file with the oldest timestamp in its name.</span></span>  
  
 <span data-ttu-id="67e4f-158">要使用这些设置，请进行以下操作：</span><span class="sxs-lookup"><span data-stu-id="67e4f-158">To use these settings, do the following:</span></span>  
  
1.  <span data-ttu-id="67e4f-159">在记事本中打开 msmdsrv.ini。</span><span class="sxs-lookup"><span data-stu-id="67e4f-159">Open msmdsrv.ini in NotePad.</span></span>  
  
2.  <span data-ttu-id="67e4f-160">复制以下两行：</span><span class="sxs-lookup"><span data-stu-id="67e4f-160">Copy the following two lines:</span></span>  
  
    ```  
    <MaxFileSizeMB>256</MaxFileSizeMB>  
    <MaxNumberOfLogFiles>5</MaxNumberOfLogFiles>  
    ```  
  
3.  <span data-ttu-id="67e4f-161">将两行粘贴到 msmdsrv.ini 的日志部分，在 msmdsrv.log 的文件名下方。</span><span class="sxs-lookup"><span data-stu-id="67e4f-161">Paste the two lines into the Log section of msmdsrv.ini, below the filename for msmdsrv.log.</span></span> <span data-ttu-id="67e4f-162">必须手动添加两个设置。</span><span class="sxs-lookup"><span data-stu-id="67e4f-162">Both settings must be added manually.</span></span> <span data-ttu-id="67e4f-163">其在 msmdsrv.ini 文件中没有占位符。</span><span class="sxs-lookup"><span data-stu-id="67e4f-163">There are no placeholders for them in the msmdsrv.ini file.</span></span>  
  
     <span data-ttu-id="67e4f-164">更改的配置文件应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="67e4f-164">The changed configuration file should look like the following:</span></span>  
  
    ```  
    <Log>  
    <File>msmdsrv.log</File>  
    <MaxFileSizeMB>256</MaxFileSizeMB>  
    <MaxNumberOfLogFiles>5</MaxNumberOfLogFiles>  
    <FileBufferSize>0</FileBufferSize>  
  
    ```  
  
4.  <span data-ttu-id="67e4f-165">如果这些值与你要的值不同，请对其进行编辑。</span><span class="sxs-lookup"><span data-stu-id="67e4f-165">Edit the values if those provided differ from what you want.</span></span>  
  
5.  <span data-ttu-id="67e4f-166">保存文件。</span><span class="sxs-lookup"><span data-stu-id="67e4f-166">Save the file.</span></span>  
  
6.  <span data-ttu-id="67e4f-167">重启服务。</span><span class="sxs-lookup"><span data-stu-id="67e4f-167">Restart the service.</span></span>  
  
##  <a name="query-logs"></a><a name="bkmk_querylog"></a><span data-ttu-id="67e4f-168">查询日志</span><span class="sxs-lookup"><span data-stu-id="67e4f-168">Query logs</span></span>  
 <span data-ttu-id="67e4f-169">查询日志有一点用词不当，因为它不记录你的用户的 MDX 或 DAX 查询活动。</span><span class="sxs-lookup"><span data-stu-id="67e4f-169">The query log is a bit of a misnomer in that it does not log the MDX or DAX query activity of your users.</span></span> <span data-ttu-id="67e4f-170">它收集由 Analysis Services 生成的查询的数据，这些数据后续用作基于使用情况的优化向导中的数据输入。</span><span class="sxs-lookup"><span data-stu-id="67e4f-170">Instead, it collects data about queries generated by Analysis Services, which is subsequently used as data input in the Usage Based Optimization Wizard.</span></span> <span data-ttu-id="67e4f-171">查询日志中收集的数据不用于直接分析。</span><span class="sxs-lookup"><span data-stu-id="67e4f-171">The data collected in the query log is not intended for direct analysis.</span></span> <span data-ttu-id="67e4f-172">具体而言，数据集用比特数组表示，查询中包含指示数据集部分的 0 或 1。</span><span class="sxs-lookup"><span data-stu-id="67e4f-172">Specifically, the datasets are described in bit arrays, with a zero or a one indicating the parts of dataset is included in the query.</span></span> <span data-ttu-id="67e4f-173">再次说明，此数据用于向导。</span><span class="sxs-lookup"><span data-stu-id="67e4f-173">Again, this data is meant for the wizard.</span></span>  
  
 <span data-ttu-id="67e4f-174">对于查询监控和故障排除，许多开发人员和管理员使用社区工具 **ASTrace**来监控查询。</span><span class="sxs-lookup"><span data-stu-id="67e4f-174">For query monitoring and troubleshooting, many developers and administrators use a community tool, **ASTrace**, to monitor queries.</span></span> <span data-ttu-id="67e4f-175">你还可使用 SQL Server Profiler、xEvents 或 Analysis Services 跟踪。</span><span class="sxs-lookup"><span data-stu-id="67e4f-175">You can also use SQL Server Profiler, xEvents, or an Analysis Services trace.</span></span> <span data-ttu-id="67e4f-176">有关跟踪相关的链接，请参阅 [监视 Analysis Services 实例](monitor-an-analysis-services-instance.md) 。</span><span class="sxs-lookup"><span data-stu-id="67e4f-176">See [Monitor an Analysis Services Instance](monitor-an-analysis-services-instance.md) for tracing-related links.</span></span>  
  
 <span data-ttu-id="67e4f-177">你应何时使用查询日志？</span><span class="sxs-lookup"><span data-stu-id="67e4f-177">When should you use the query log?</span></span> <span data-ttu-id="67e4f-178">我们建议启用查询日志，作为包括基于使用情况的优化向导的查询性能微调练习的一部分。</span><span class="sxs-lookup"><span data-stu-id="67e4f-178">We recommend enabling the query log as part of a query performance tuning exercise that includes the Usage Based Optimization Wizard.</span></span> <span data-ttu-id="67e4f-179">在你启用此功能、创建用于支持它的数据结构并设置 Analysis Services 使用的属性以查找和填充日志后，查询日志才存在。</span><span class="sxs-lookup"><span data-stu-id="67e4f-179">The query log does not exist until you enable the feature, create the data structures to support it, and set properties used by Analysis Services to locate and populate the log.</span></span>  
  
 <span data-ttu-id="67e4f-180">要启用查询日志，请遵循以下步骤：</span><span class="sxs-lookup"><span data-stu-id="67e4f-180">To enable the query log, follow these steps:</span></span>  
  
1.  <span data-ttu-id="67e4f-181">创建 SQL Server 关系数据库以存储查询日志。</span><span class="sxs-lookup"><span data-stu-id="67e4f-181">Create a SQL Server relational database to store the query log.</span></span>  
  
2.  <span data-ttu-id="67e4f-182">授予 Analysis Services 帐户有关数据库的足够权限。</span><span class="sxs-lookup"><span data-stu-id="67e4f-182">Grant the Analysis Services service account sufficient permissions on the database.</span></span> <span data-ttu-id="67e4f-183">帐户需要创建表、写入表和从表读取的权限。</span><span class="sxs-lookup"><span data-stu-id="67e4f-183">The account needs permission to create a table, write to the table, and read from the table.</span></span>  
  
3.  <span data-ttu-id="67e4f-184">在 SQL Server Management Studio 中，右键单击**Analysis Services**  |  **属性**  |  "**常规**"，将**CreateQueryLogTable**设置为 true。</span><span class="sxs-lookup"><span data-stu-id="67e4f-184">In SQL Server Management Studio, right-click **Analysis Services** | **Properties** | **General**, set **CreateQueryLogTable** to true.</span></span>  
  
4.  <span data-ttu-id="67e4f-185">或者，如果你要以不同速率取样查询，或者使用表的不同名称，则更改 **QueryLogSampling** 或 **QueryLogTableName** 。</span><span class="sxs-lookup"><span data-stu-id="67e4f-185">Optionally, change **QueryLogSampling** or **QueryLogTableName** if you want to sample queries at a different rate, or use a different name for the table.</span></span>  
  
 <span data-ttu-id="67e4f-186">将不会创建查询日志表，直到你已运行足够的 MDX 查询以满足取样需要。</span><span class="sxs-lookup"><span data-stu-id="67e4f-186">The query log table will not be created until you have run enough MDX queries to meet the sampling requirements.</span></span> <span data-ttu-id="67e4f-187">例如，如果你保持默认值为 10，则必须运行至少 10 个查询才能创建表。</span><span class="sxs-lookup"><span data-stu-id="67e4f-187">For example, if you keep the default value of 10, you must run at least 10 queries before the table will be created.</span></span>  
  
 <span data-ttu-id="67e4f-188">查询日志设置属于服务器范围。</span><span class="sxs-lookup"><span data-stu-id="67e4f-188">Query log settings are server wide.</span></span> <span data-ttu-id="67e4f-189">你指定的设置将被此服务器上运行的所有数据库使用。</span><span class="sxs-lookup"><span data-stu-id="67e4f-189">The settings you specify will be used by all databases running on this server.</span></span>  
  
 <span data-ttu-id="67e4f-190">![Management Studio 中的查询日志设置](../media/ssas-querylogsettings.png "Management Studio 中的查询日志设置")</span><span class="sxs-lookup"><span data-stu-id="67e4f-190">![Query log settings in Management Studio](../media/ssas-querylogsettings.png "Query log settings in Management Studio")</span></span>  
  
 <span data-ttu-id="67e4f-191">指定配置设置后，多次运行 MDX 查询。</span><span class="sxs-lookup"><span data-stu-id="67e4f-191">After the configuration settings are specified, run an MDX query multiple times.</span></span> <span data-ttu-id="67e4f-192">如果取样设置为 10，则运行 11 次查询。验证表是否创建。</span><span class="sxs-lookup"><span data-stu-id="67e4f-192">If sampling is set to 10, run the query 11 times.Verify the table is created.</span></span> <span data-ttu-id="67e4f-193">在 Management Studio 中，连接到关系数据库引擎，打开数据库文件夹，打开 **“表”** 文件夹，并验证 **OlapQueryLog** 是否存在。</span><span class="sxs-lookup"><span data-stu-id="67e4f-193">In Management Studio, connect to the relational database engine, open the database folder, open the **Tables** folder, and verify that **OlapQueryLog** exists.</span></span> <span data-ttu-id="67e4f-194">如果不能立即查看表，则刷新文件夹，提取其内容的任何更改。</span><span class="sxs-lookup"><span data-stu-id="67e4f-194">If you do not immediately see the table, refresh the folder to pick up any changes to its contents.</span></span>  
  
 <span data-ttu-id="67e4f-195">允许查询日志为基于使用情况的优化向导积累足够数据。</span><span class="sxs-lookup"><span data-stu-id="67e4f-195">Allow the query log to accumulate sufficient data for the Usage Based Optimization Wizard.</span></span> <span data-ttu-id="67e4f-196">如果查询量是周期性的，则捕获足够流量以包括具有代表性的一组数据。</span><span class="sxs-lookup"><span data-stu-id="67e4f-196">If query volumes are cyclical, capture enough traffic to have a representative set of data.</span></span> <span data-ttu-id="67e4f-197">有关如何运行向导的说明，请参见 [基于使用情况的优化向导](https://msdn.microsoft.com/library/ms189706.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="67e4f-197">See [Usage Based Optimization Wizard](https://msdn.microsoft.com/library/ms189706.aspx) for instructions on how to run the wizard.</span></span>  
  
 <span data-ttu-id="67e4f-198">有关查询日志配置的详细信息，请参见 [配置 Analysis Services 查询日志](https://technet.microsoft.com/library/Cc917676) 。</span><span class="sxs-lookup"><span data-stu-id="67e4f-198">See [Configuring the Analysis Services Query Log](https://technet.microsoft.com/library/Cc917676) to learn more about query log configuration.</span></span> <span data-ttu-id="67e4f-199">虽然文件很旧，但最新版本中的查询日志配置并未改变，其包含的信息仍适用。</span><span class="sxs-lookup"><span data-stu-id="67e4f-199">Although the paper is quite old, query log configuration has not changed in recent releases and the information it contains still applies.</span></span>  
  
##  <a name="mini-dump-mdmp-files"></a><a name="bkmk_mdmp"></a><span data-ttu-id="67e4f-200">小型转储 ( .mdmp) 文件</span><span class="sxs-lookup"><span data-stu-id="67e4f-200">Mini dump (.mdmp) files</span></span>  
 <span data-ttu-id="67e4f-201">转储文件捕获数据用于分析异常事件。</span><span class="sxs-lookup"><span data-stu-id="67e4f-201">Dump files capture data used for analyzing extraordinary events.</span></span> <span data-ttu-id="67e4f-202">Analysis Services 自动生成迷你转储 (.mdmp) 以应对服务器崩溃、异常和一些配置错误。</span><span class="sxs-lookup"><span data-stu-id="67e4f-202">Analysis Services automatically generates mini dumps (.mdmp) in response to a server crash, exception, and some configuration errors.</span></span> <span data-ttu-id="67e4f-203">已启用此功能，但不能自动发送崩溃报告。</span><span class="sxs-lookup"><span data-stu-id="67e4f-203">The feature is enabled, but does not send crash reports automatically.</span></span>  
  
 <span data-ttu-id="67e4f-204">崩溃报告通过 Msmdsrv.ini 文件中的“异常”部分配置。</span><span class="sxs-lookup"><span data-stu-id="67e4f-204">Crash reports are configured through the Exception section in the Msmdsrv.ini file.</span></span> <span data-ttu-id="67e4f-205">这些设置可控制内存转储文件生成。</span><span class="sxs-lookup"><span data-stu-id="67e4f-205">These settings control memory dump file generation.</span></span> <span data-ttu-id="67e4f-206">以下片段显示默认值：</span><span class="sxs-lookup"><span data-stu-id="67e4f-206">The following snippet shows the default values:</span></span>  
  
```  
<Exception>  
<CreateAndSendCrashReports>1</CreateAndSendCrashReports>  
<CrashReportsFolder/>  
<SQLDumperFlagsOn>0x0</SQLDumperFlagsOn>  
<SQLDumperFlagsOff>0x0</SQLDumperFlagsOff>  
<MiniDumpFlagsOn>0x0</MiniDumpFlagsOn>  
<MiniDumpFlagsOff>0x0</MiniDumpFlagsOff>  
<MinidumpErrorList>0xC1000000, 0xC1000001, 0xC102003F, 0xC1360054, 0xC1360055</MinidumpErrorList>  
<ExceptionHandlingMode>0</ExceptionHandlingMode>  
<CriticalErrorHandling>1</CriticalErrorHandling>  
<MaxExceptions>500</MaxExceptions>  
<MaxDuplicateDumps>1</MaxDuplicateDumps>  
</Exception>  
```  
  
 <span data-ttu-id="67e4f-207">**配置崩溃报告**</span><span class="sxs-lookup"><span data-stu-id="67e4f-207">**Configure Crash Reports**</span></span>  
  
 <span data-ttu-id="67e4f-208">除非 Microsoft 支持另有指示，否则大多数管理员使用默认设置。</span><span class="sxs-lookup"><span data-stu-id="67e4f-208">Unless otherwise directed by Microsoft Support, most administrators use the default settings.</span></span> <span data-ttu-id="67e4f-209">这篇较旧的知识库文章仍用于提供有关如何配置转储文件的说明： [如何配置 Analysis Services 以生成内存转储文件](https://support.microsoft.com/kb/919711)。</span><span class="sxs-lookup"><span data-stu-id="67e4f-209">This older KB article is still used to provide instruction on how to configure dump files: [How to configure Analysis Services to generate memory dump files](https://support.microsoft.com/kb/919711).</span></span>  
  
 <span data-ttu-id="67e4f-210">最可能修改的配置设置是用于确定是否生成内存转储文件的 `CreateAndSendCrashReports` 设置。</span><span class="sxs-lookup"><span data-stu-id="67e4f-210">The configuration setting most likely to be modified is the `CreateAndSendCrashReports` setting used to determine whether a memory dump file will be generated.</span></span>  
  
|<span data-ttu-id="67e4f-211">值</span><span class="sxs-lookup"><span data-stu-id="67e4f-211">Value</span></span>|<span data-ttu-id="67e4f-212">说明</span><span class="sxs-lookup"><span data-stu-id="67e4f-212">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="67e4f-213">0</span><span class="sxs-lookup"><span data-stu-id="67e4f-213">0</span></span>|<span data-ttu-id="67e4f-214">关闭内存转储文件。</span><span class="sxs-lookup"><span data-stu-id="67e4f-214">Turns off the memory dump file.</span></span> <span data-ttu-id="67e4f-215">忽略在“例外”部分下的所有其他设置。</span><span class="sxs-lookup"><span data-stu-id="67e4f-215">All other settings under the Exception section are ignored.</span></span>|  
|<span data-ttu-id="67e4f-216">1</span><span class="sxs-lookup"><span data-stu-id="67e4f-216">1</span></span>|<span data-ttu-id="67e4f-217">（默认）启用，但不发送内存转储文件。</span><span class="sxs-lookup"><span data-stu-id="67e4f-217">(Default) Enables, but does not send, the memory dump file.</span></span>|  
|<span data-ttu-id="67e4f-218">2</span><span class="sxs-lookup"><span data-stu-id="67e4f-218">2</span></span>|<span data-ttu-id="67e4f-219">启用并自动发送错误报告到 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="67e4f-219">Enables and automatically sends an error report to Microsoft.</span></span>|  
  
 <span data-ttu-id="67e4f-220">`CrashReportsFolder` 是转储文件的位置。</span><span class="sxs-lookup"><span data-stu-id="67e4f-220">`CrashReportsFolder` is the location of the dump files.</span></span> <span data-ttu-id="67e4f-221">默认情况下，可在 \Olap\Log 文件夹找到 .mdmp 文件和相关日志记录。</span><span class="sxs-lookup"><span data-stu-id="67e4f-221">By default, an .mdmp file and associated log records can be found in the \Olap\Log folder.</span></span>  
  
 <span data-ttu-id="67e4f-222">`SQLDumperFlagsOn` 用于生成完全转储。</span><span class="sxs-lookup"><span data-stu-id="67e4f-222">`SQLDumperFlagsOn` is used to generate a full dump.</span></span> <span data-ttu-id="67e4f-223">默认情况下，未启用完全转储。</span><span class="sxs-lookup"><span data-stu-id="67e4f-223">By default, full dumps are not enabled.</span></span> <span data-ttu-id="67e4f-224">你可将此属性设置为 `0x34`。</span><span class="sxs-lookup"><span data-stu-id="67e4f-224">You can set this property to `0x34`.</span></span>  
  
 <span data-ttu-id="67e4f-225">以下链接提供了更多背景信息：</span><span class="sxs-lookup"><span data-stu-id="67e4f-225">The following links provide more background:</span></span>  
  
-   [<span data-ttu-id="67e4f-226">深入了解使用 Minidumps 的 SQL Server</span><span class="sxs-lookup"><span data-stu-id="67e4f-226">Looking Deeper into SQL Server using Minidumps</span></span>](https://blogs.msdn.com/b/sqlcat/archive/2009/09/11/looking-deeper-into-sql-server-using-minidumps.aspx)  
  
-   [<span data-ttu-id="67e4f-227">如何创建用户模式转储文件</span><span class="sxs-lookup"><span data-stu-id="67e4f-227">How to create a user mode dump file</span></span>](https://support.microsoft.com/kb/931673)  
  
-   [<span data-ttu-id="67e4f-228">如何使用 Sqldumper.exe 实用工具在 SQL Server 中生成转储文件</span><span class="sxs-lookup"><span data-stu-id="67e4f-228">How to use the Sqldumper.exe utility to generate a dump file in SQL Server</span></span>](https://support.microsoft.com/kb/917825)  
  
##  <a name="tips-and-best-practices"></a><a name="bkmk_tips"></a><span data-ttu-id="67e4f-229">提示和最佳做法</span><span class="sxs-lookup"><span data-stu-id="67e4f-229">Tips and best practices</span></span>  
 <span data-ttu-id="67e4f-230">此部分是此文章中提到的提示回顾。</span><span class="sxs-lookup"><span data-stu-id="67e4f-230">This section is a recap of the tips mentioned throughout this article.</span></span>  
  
-   <span data-ttu-id="67e4f-231">配置 msmdsrv.log 文件以控制 msmdsrv 日志文件的大小和数量。</span><span class="sxs-lookup"><span data-stu-id="67e4f-231">Configure the msmdsrv.log file to control the size and number of msmdsrv log file.</span></span> <span data-ttu-id="67e4f-232">默认情况下不启用这些设置，请确保将其添加为安装后步骤。</span><span class="sxs-lookup"><span data-stu-id="67e4f-232">The settings are not enabled by default, so be sure to add them as post-installation step.</span></span> <span data-ttu-id="67e4f-233">请参阅本主题中的 [MSMDSRV 服务日志文件](#bkmk_msmdsrv) 。</span><span class="sxs-lookup"><span data-stu-id="67e4f-233">See [MSMDSRV service log file](#bkmk_msmdsrv) in this topic.</span></span>  
  
-   <span data-ttu-id="67e4f-234">查看来自 Microsoft 客户支持的这篇博文，了解其使用什么资源来获取有关服务器操作的信息： [初始数据集合](https://blogs.msdn.com/b/as_emea/archive/2012/01/02/initial-data-collection-for-troubleshooting-analysis-services-issues.aspx)</span><span class="sxs-lookup"><span data-stu-id="67e4f-234">Review this blog post from Microsoft Customer Support to learn what resources they use to get information about server operations: [Initial Data Collection](https://blogs.msdn.com/b/as_emea/archive/2012/01/02/initial-data-collection-for-troubleshooting-analysis-services-issues.aspx)</span></span>  
  
-   <span data-ttu-id="67e4f-235">使用 ASTrace2012（而非查询日志）查找谁正在查询多维数据集。</span><span class="sxs-lookup"><span data-stu-id="67e4f-235">Use ASTrace2012, rather than a query log, to find out who is querying cubes.</span></span> <span data-ttu-id="67e4f-236">查询日志通常用于提供输入到基于使用情况的优化向导，其捕获的数据不易读取或解释。</span><span class="sxs-lookup"><span data-stu-id="67e4f-236">The query log is typically used to provide input into the Usage Based Optimization Wizard, and the data it captures is not easy to read or interpret.</span></span> <span data-ttu-id="67e4f-237">ASTrace2012 是一种广泛使用的用于捕获查询操作的社区工具。</span><span class="sxs-lookup"><span data-stu-id="67e4f-237">ASTrace2012 is a community tool, widely used, that captures query operations.</span></span> <span data-ttu-id="67e4f-238">请参阅 [Microsoft SQL Server 社区示例：Analysis Services](https://sqlsrvanalysissrvcs.codeplex.com/)。</span><span class="sxs-lookup"><span data-stu-id="67e4f-238">See [Microsoft SQL Server Community Samples: Analysis Services](https://sqlsrvanalysissrvcs.codeplex.com/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67e4f-239">另请参阅</span><span class="sxs-lookup"><span data-stu-id="67e4f-239">See Also</span></span>  
 <span data-ttu-id="67e4f-240">[Analysis Services 实例管理](analysis-services-instance-management.md) </span><span class="sxs-lookup"><span data-stu-id="67e4f-240">[Analysis Services Instance Management](analysis-services-instance-management.md) </span></span>  
 <span data-ttu-id="67e4f-241">[通过 SQL Server Profiler 监视 Analysis Services 简介](introduction-to-monitoring-analysis-services-with-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="67e4f-241">[Introduction to Monitoring Analysis Services with SQL Server Profiler](introduction-to-monitoring-analysis-services-with-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="67e4f-242">在 Analysis Services 中配置服务器属性</span><span class="sxs-lookup"><span data-stu-id="67e4f-242">Configure Server Properties in Analysis Services</span></span>](../server-properties/server-properties-in-analysis-services.md)  
  
  
