---
title: Distributed Replay 要求 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 6fffee7d-891f-4d9d-b2c3-dd19855a1c2c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 66be93534756360e722fcccaf405815e14ffa7ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586023"
---
# <a name="distributed-replay-requirements"></a><span data-ttu-id="49090-102">Distributed Replay 要求</span><span class="sxs-lookup"><span data-stu-id="49090-102">Distributed Replay Requirements</span></span>
  <span data-ttu-id="49090-103">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 功能之前，请考虑本主题中列出的产品要求。</span><span class="sxs-lookup"><span data-stu-id="49090-103">Before using the [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay feature, consider the product requirements that are outlined in this topic.</span></span>  
  
## <a name="input-trace-requirements"></a><span data-ttu-id="49090-104">输入跟踪要求</span><span class="sxs-lookup"><span data-stu-id="49090-104">Input Trace Requirements</span></span>  
 <span data-ttu-id="49090-105">若要成功地重播跟踪数据，它必须满足版本和格式的要求，并包含所需的事件和列。</span><span class="sxs-lookup"><span data-stu-id="49090-105">To successfully replay trace data, it must meet the requirements for version and format, and contain the required events and columns.</span></span>  
  
### <a name="input-trace-versions"></a><span data-ttu-id="49090-106">输入跟踪版本</span><span class="sxs-lookup"><span data-stu-id="49090-106">Input Trace Versions</span></span>  
 <span data-ttu-id="49090-107">Distributed Replay 支持在以下版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中所收集的输入跟踪数据：</span><span class="sxs-lookup"><span data-stu-id="49090-107">Distributed Replay supports input trace data that is collected on the following versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
  
### <a name="input-trace-formats"></a><span data-ttu-id="49090-108">输入跟踪格式</span><span class="sxs-lookup"><span data-stu-id="49090-108">Input Trace Formats</span></span>  
 <span data-ttu-id="49090-109">输入跟踪数据可以采用以下任意一种格式：</span><span class="sxs-lookup"><span data-stu-id="49090-109">The input trace data can be in any of the following formats:</span></span>  
  
-   <span data-ttu-id="49090-110">具有 `.trc` 扩展名的单个跟踪文件。</span><span class="sxs-lookup"><span data-stu-id="49090-110">A single trace file that has the `.trc` extension.</span></span>  
  
-   <span data-ttu-id="49090-111">一组遵循文件滚动更新命名约定（例如：`<TraceFile>.trc`、`<TraceFile>_1.trc`、`<TraceFile>_2.trc`、`<TraceFile>_3.trc`…`<TraceFile>_n.trc`）的滚动更新跟踪文件。</span><span class="sxs-lookup"><span data-stu-id="49090-111">A set of rollover trace files that follow the file rollover naming convention, for example: `<TraceFile>.trc`, `<TraceFile>_1.trc`, `<TraceFile>_2.trc`, `<TraceFile>_3.trc`, ... `<TraceFile>_n.trc`.</span></span>  
  
### <a name="input-trace-events-and-columns"></a><span data-ttu-id="49090-112">输入跟踪事件和列</span><span class="sxs-lookup"><span data-stu-id="49090-112">Input Trace Events and Columns</span></span>  
 <span data-ttu-id="49090-113">输入跟踪数据必须包含特定的事件和列才能由 Distributed Replay 进行重播。</span><span class="sxs-lookup"><span data-stu-id="49090-113">The input trace data must contain specific events and columns to be replayed by Distributed Replay.</span></span> <span data-ttu-id="49090-114">**中的** TSQL_Replay [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 模板包含所有必需的事件和列以及其他信息。</span><span class="sxs-lookup"><span data-stu-id="49090-114">The **TSQL_Replay** template in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] contains all of the required events and columns, in addition to extra information.</span></span> <span data-ttu-id="49090-115">有关该模板的详细信息，请参阅 [Replay Requirements](../sql-server-profiler/replay-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="49090-115">For more information about that template, see [Replay Requirements](../sql-server-profiler/replay-requirements.md).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="49090-116">如果你没有使用 **TSQL_Replay** 模板来捕获输入跟踪数据，或者未满足输入跟踪要求，则可能会收到意外的重播结果。</span><span class="sxs-lookup"><span data-stu-id="49090-116">If you do not use the **TSQL_Replay** template to capture the input trace data, or if the input trace requirements are not satisfied, you may receive unexpected replay results.</span></span>  
  
 <span data-ttu-id="49090-117">您也可以创建一个自定义跟踪模板，并使用该模板通过 Distributed Replay 来重播事件，前提条件是该模板包含以下事件：</span><span class="sxs-lookup"><span data-stu-id="49090-117">You can also create a custom trace template and use it to replay events with Distributed Replay, as long as it contains the following events:</span></span>  
  
-   <span data-ttu-id="49090-118">审核登录</span><span class="sxs-lookup"><span data-stu-id="49090-118">Audit Login</span></span>  
  
-   <span data-ttu-id="49090-119">审核注销</span><span class="sxs-lookup"><span data-stu-id="49090-119">Audit Logout</span></span>  
  
-   <span data-ttu-id="49090-120">ExistingConnection</span><span class="sxs-lookup"><span data-stu-id="49090-120">ExistingConnection</span></span>  
  
-   <span data-ttu-id="49090-121">RPC Output Parameter</span><span class="sxs-lookup"><span data-stu-id="49090-121">RPC Output Parameter</span></span>  
  
-   <span data-ttu-id="49090-122">RPC:Completed</span><span class="sxs-lookup"><span data-stu-id="49090-122">RPC:Completed</span></span>  
  
-   <span data-ttu-id="49090-123">RPC:Starting</span><span class="sxs-lookup"><span data-stu-id="49090-123">RPC:Starting</span></span>  
  
-   <span data-ttu-id="49090-124">SQL:BatchCompleted</span><span class="sxs-lookup"><span data-stu-id="49090-124">SQL:BatchCompleted</span></span>  
  
-   <span data-ttu-id="49090-125">SQL:BatchStarting</span><span class="sxs-lookup"><span data-stu-id="49090-125">SQL:BatchStarting</span></span>  
  
 <span data-ttu-id="49090-126">如果您要重播服务器端游标，则还需要以下事件：</span><span class="sxs-lookup"><span data-stu-id="49090-126">If you are replaying server-side cursors, the following events are also required:</span></span>  
  
-   <span data-ttu-id="49090-127">CursorClose</span><span class="sxs-lookup"><span data-stu-id="49090-127">CursorClose</span></span>  
  
-   <span data-ttu-id="49090-128">CursorExecute</span><span class="sxs-lookup"><span data-stu-id="49090-128">CursorExecute</span></span>  
  
-   <span data-ttu-id="49090-129">CursorOpen</span><span class="sxs-lookup"><span data-stu-id="49090-129">CursorOpen</span></span>  
  
-   <span data-ttu-id="49090-130">CursorPrepare</span><span class="sxs-lookup"><span data-stu-id="49090-130">CursorPrepare</span></span>  
  
-   <span data-ttu-id="49090-131">CursorUnprepare</span><span class="sxs-lookup"><span data-stu-id="49090-131">CursorUnprepare</span></span>  
  
 <span data-ttu-id="49090-132">如果您要重播服务器端准备的 SQL 语句，则还需要以下事件：</span><span class="sxs-lookup"><span data-stu-id="49090-132">If you are replaying server-side prepared SQL statements, the following events are also required:</span></span>  
  
-   <span data-ttu-id="49090-133">Exec Prepared SQL</span><span class="sxs-lookup"><span data-stu-id="49090-133">Exec Prepared SQL</span></span>  
  
-   <span data-ttu-id="49090-134">Prepare SQL</span><span class="sxs-lookup"><span data-stu-id="49090-134">Prepare SQL</span></span>  
  
 <span data-ttu-id="49090-135">所有输入跟踪数据都必须包含以下列：</span><span class="sxs-lookup"><span data-stu-id="49090-135">All input trace data must contain the following columns:</span></span>  
  
-   <span data-ttu-id="49090-136">Event Class</span><span class="sxs-lookup"><span data-stu-id="49090-136">Event Class</span></span>  
  
-   <span data-ttu-id="49090-137">EventSequence</span><span class="sxs-lookup"><span data-stu-id="49090-137">EventSequence</span></span>  
  
-   <span data-ttu-id="49090-138">TextData</span><span class="sxs-lookup"><span data-stu-id="49090-138">TextData</span></span>  
  
-   <span data-ttu-id="49090-139">应用程序名称</span><span class="sxs-lookup"><span data-stu-id="49090-139">Application Name</span></span>  
  
-   <span data-ttu-id="49090-140">LoginName</span><span class="sxs-lookup"><span data-stu-id="49090-140">LoginName</span></span>  
  
-   <span data-ttu-id="49090-141">DatabaseName</span><span class="sxs-lookup"><span data-stu-id="49090-141">DatabaseName</span></span>  
  
-   <span data-ttu-id="49090-142">数据库 ID</span><span class="sxs-lookup"><span data-stu-id="49090-142">Database ID</span></span>  
  
-   <span data-ttu-id="49090-143">HostName</span><span class="sxs-lookup"><span data-stu-id="49090-143">HostName</span></span>  
  
-   <span data-ttu-id="49090-144">Binary Data</span><span class="sxs-lookup"><span data-stu-id="49090-144">Binary Data</span></span>  
  
-   <span data-ttu-id="49090-145">SPID</span><span class="sxs-lookup"><span data-stu-id="49090-145">SPID</span></span>  
  
-   <span data-ttu-id="49090-146">开始时间</span><span class="sxs-lookup"><span data-stu-id="49090-146">Start Time</span></span>  
  
-   <span data-ttu-id="49090-147">EndTime</span><span class="sxs-lookup"><span data-stu-id="49090-147">EndTime</span></span>  
  
-   <span data-ttu-id="49090-148">IsSystem</span><span class="sxs-lookup"><span data-stu-id="49090-148">IsSystem</span></span>  
  
## <a name="supported-input-trace-and-target-server-combinations"></a><span data-ttu-id="49090-149">支持的输入跟踪和目标服务器组合</span><span class="sxs-lookup"><span data-stu-id="49090-149">Supported Input Trace and Target Server Combinations</span></span>  
 <span data-ttu-id="49090-150">下表列出了支持的跟踪数据版本，以及对于每种版本，可对其重播数据的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支持版本。</span><span class="sxs-lookup"><span data-stu-id="49090-150">The following table lists the supported versions of trace data, and for each, the supported versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that data can be replayed against.</span></span>  
  
|<span data-ttu-id="49090-151">输入跟踪数据的版本</span><span class="sxs-lookup"><span data-stu-id="49090-151">Version of Input Trace Data</span></span>|<span data-ttu-id="49090-152">目标服务器实例支持的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本</span><span class="sxs-lookup"><span data-stu-id="49090-152">Supported Versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the Target Server Instance</span></span>|  
|---------------------------------|------------------------------------------------------------------------------------|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]<span data-ttu-id="49090-153">, [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49090-153">, [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]<span data-ttu-id="49090-154">, [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49090-154">, [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="49090-155">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49090-155">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]<span data-ttu-id="49090-156">, [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49090-156">, [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
  
## <a name="operating-system-requirements"></a><span data-ttu-id="49090-157">操作系统要求</span><span class="sxs-lookup"><span data-stu-id="49090-157">Operating System Requirements</span></span>  
 <span data-ttu-id="49090-158">支持运行管理工具、控制器和客户端服务的操作系统与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例所要求的操作系统相同。</span><span class="sxs-lookup"><span data-stu-id="49090-158">Supported operating systems for running the administration tool and the controller and client services is the same as your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="49090-159">有关实例支持的操作系统的详细信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅[安装 SQL Server 2014 的硬件和软件要求](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="49090-159">For more information about which operating systems are supported for your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, see [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
 <span data-ttu-id="49090-160">Distributed Replay 功能在基于 x86 和基于 x64 的操作系统上均受支持。</span><span class="sxs-lookup"><span data-stu-id="49090-160">Distributed Replay features are supported on both x86-based and x64-based operating systems.</span></span> <span data-ttu-id="49090-161">对于基于 x64 的操作系统，仅支持 Windows on Windows (WOW) 模式。</span><span class="sxs-lookup"><span data-stu-id="49090-161">For x64-based operating systems, only Windows on Windows (WOW) mode is supported.</span></span>  
  
## <a name="installation-limitations"></a><span data-ttu-id="49090-162">安装限制</span><span class="sxs-lookup"><span data-stu-id="49090-162">Installation Limitations</span></span>  
 <span data-ttu-id="49090-163">任何一台计算机只能安装每个 Distributed Replay 功能的一个实例。</span><span class="sxs-lookup"><span data-stu-id="49090-163">Any one computer can only have a single instance of each Distributed Replay feature installed.</span></span> <span data-ttu-id="49090-164">下表列出了在单个 Distributed Replay 环境中每种功能所允许的安装数。</span><span class="sxs-lookup"><span data-stu-id="49090-164">The following table lists how many installations of each feature are allowed in a single Distributed Replay environment.</span></span>  
  
|<span data-ttu-id="49090-165">Distributed Replay 功能</span><span class="sxs-lookup"><span data-stu-id="49090-165">Distributed Replay Feature</span></span>|<span data-ttu-id="49090-166">每个重播环境的最大安装数</span><span class="sxs-lookup"><span data-stu-id="49090-166">Maximum Installations Per Replay Environment</span></span>|  
|--------------------------------|--------------------------------------------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="49090-167">Distributed Replay 控制器服务</span><span class="sxs-lookup"><span data-stu-id="49090-167">Distributed Replay controller service</span></span>|<span data-ttu-id="49090-168">1</span><span class="sxs-lookup"><span data-stu-id="49090-168">1</span></span>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="49090-169">Distributed Replay 客户端服务</span><span class="sxs-lookup"><span data-stu-id="49090-169">Distributed Replay client service</span></span>|<span data-ttu-id="49090-170">16（物理或虚拟计算机）</span><span class="sxs-lookup"><span data-stu-id="49090-170">16 (physical or virtual computers)</span></span>|  
|<span data-ttu-id="49090-171">管理工具</span><span class="sxs-lookup"><span data-stu-id="49090-171">Administration tool</span></span>|<span data-ttu-id="49090-172">无限制</span><span class="sxs-lookup"><span data-stu-id="49090-172">Unlimited</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="49090-173">虽然一台计算机上只能安装一个管理工具实例，但是您可以启动管理工具的多个实例。</span><span class="sxs-lookup"><span data-stu-id="49090-173">Although only one instance of the administration tool can be installed on a single computer, you can start multiple instances of the administration tool.</span></span> <span data-ttu-id="49090-174">多个管理工具发出的命令按照接收命令的顺序进行解析。</span><span class="sxs-lookup"><span data-stu-id="49090-174">Commands issued from multiple administration tools are resolved in the order in which they are received.</span></span>  
  
## <a name="data-access-provider"></a><span data-ttu-id="49090-175">数据访问提供程序</span><span class="sxs-lookup"><span data-stu-id="49090-175">Data Access Provider</span></span>  
 <span data-ttu-id="49090-176">Distributed Replay 仅支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="49090-176">Distributed Replay only supports the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC data access provider.</span></span>  
  
## <a name="target-server-preparation-requirements"></a><span data-ttu-id="49090-177">目标服务器准备要求</span><span class="sxs-lookup"><span data-stu-id="49090-177">Target Server Preparation Requirements</span></span>  
 <span data-ttu-id="49090-178">建议将目标服务器置于测试环境中。</span><span class="sxs-lookup"><span data-stu-id="49090-178">We recommend that the target server be located in a test environment.</span></span> <span data-ttu-id="49090-179">若要针对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的其他实例而非最初记录跟踪数据的实例重播跟踪数据，请确保目标服务器满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="49090-179">To replay trace data against a different instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] than it was originally recorded, make sure that the following has been done to the target server:</span></span>  
  
-   <span data-ttu-id="49090-180">跟踪数据中包含的所有登录名和用户必须出现在目标服务器的相同数据库中。</span><span class="sxs-lookup"><span data-stu-id="49090-180">All logins and users that are contained in the trace data must be present in the same database on the target server.</span></span>  
  
-   <span data-ttu-id="49090-181">目标服务器上的所有登录名和用户拥有的权限必须与他们在原始服务器上的权限相同。</span><span class="sxs-lookup"><span data-stu-id="49090-181">All logins and users on the target server must have the same permissions they had on the original server.</span></span>  
  
-   <span data-ttu-id="49090-182">目标上的数据库 ID 最好与源上的数据库 ID 相同。</span><span class="sxs-lookup"><span data-stu-id="49090-182">The database IDs on the target ideally should be the same as those on the source.</span></span> <span data-ttu-id="49090-183">但是，如果它们不相同，当跟踪中出现 **DatabaseName** 时，将根据它进行匹配。</span><span class="sxs-lookup"><span data-stu-id="49090-183">However, if they are not the same, matching can be performed based on **DatabaseName** if it is present in the trace.</span></span>  
  
-   <span data-ttu-id="49090-184">跟踪数据中包含的每个登录名的默认数据库必须设置（在目标服务器上）为该登录名相应的目标数据库。</span><span class="sxs-lookup"><span data-stu-id="49090-184">The default database for each login that is contained in the trace data must be set (on the target server) to the respective target database of the login.</span></span> <span data-ttu-id="49090-185">例如，要重播的跟踪数据包含登录名 **Fred**在原始 **实例上** Fred_Db [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据库中的活动。</span><span class="sxs-lookup"><span data-stu-id="49090-185">For example, the trace data to be replayed contains activity for the login, **Fred**, in the database **Fred_Db** on the original instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="49090-186">因此，在目标服务器上，必须将登录名 **Fred**的默认数据库设置为与 **Fred_Db** 匹配的数据库（即使数据库名称不同）。</span><span class="sxs-lookup"><span data-stu-id="49090-186">Therefore, on the target server, the default database for the login, **Fred**, must be set to the database that matches **Fred_Db** (even if the database name is different).</span></span> <span data-ttu-id="49090-187">若要设置登录名的默认数据库，请使用 `sp_defaultdb` 系统存储过程。</span><span class="sxs-lookup"><span data-stu-id="49090-187">To set the default database of the login, use the `sp_defaultdb` system stored procedure.</span></span>  
  
 <span data-ttu-id="49090-188">重播与不存在的或不正确的登录名相关的事件会导致重播错误，但重播操作会继续。</span><span class="sxs-lookup"><span data-stu-id="49090-188">Replaying events associated with missing or incorrect logins results in replay errors, but the replay operation continues.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49090-189">另请参阅</span><span class="sxs-lookup"><span data-stu-id="49090-189">See Also</span></span>  
 <span data-ttu-id="49090-190">[SQL Server 分布式重播](sql-server-distributed-replay.md) </span><span class="sxs-lookup"><span data-stu-id="49090-190">[SQL Server Distributed Replay](sql-server-distributed-replay.md) </span></span>  
 <span data-ttu-id="49090-191">[Distributed Replay 安全性](distributed-replay-security.md) </span><span class="sxs-lookup"><span data-stu-id="49090-191">[Distributed Replay Security](distributed-replay-security.md) </span></span>  
 [<span data-ttu-id="49090-192">安装 Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="49090-192">Install Distributed Replay</span></span>](install-distributed-replay-overview.md)  
  
  
