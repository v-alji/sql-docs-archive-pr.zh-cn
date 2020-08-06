---
title: SQL Server Profiler "工具"-"选项" ("常规选项" 页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.tools.generaloptions.f1
helpviewer_keywords:
- General Options dialog box
ms.assetid: a888246d-ccfe-415f-bbdc-d6adafac250a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fad4d3529482835367898276a973bd7c8827b553
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588683"
---
# <a name="sql-server-profiler---tools-options-general-options-page"></a><span data-ttu-id="8d6f1-102">SQL Server Profiler 工具-选项 (常规选项页) </span><span class="sxs-lookup"><span data-stu-id="8d6f1-102">SQL Server Profiler - Tools-Options (General Options Page)</span></span>
  <span data-ttu-id="8d6f1-103">使用 **“常规选项”** 对话框可以查看或指定以下选项：</span><span class="sxs-lookup"><span data-stu-id="8d6f1-103">Use the **General Options** dialog box to view or specify the following options.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8d6f1-104">选项</span><span class="sxs-lookup"><span data-stu-id="8d6f1-104">Options</span></span>  
  
### <a name="display-options"></a><span data-ttu-id="8d6f1-105">显示选项</span><span class="sxs-lookup"><span data-stu-id="8d6f1-105">Display Options</span></span>  
 <span data-ttu-id="8d6f1-106">**字体名称**</span><span class="sxs-lookup"><span data-stu-id="8d6f1-106">**Font name**</span></span>  
 <span data-ttu-id="8d6f1-107">显示在跟踪过程中“跟踪结果”网格所使用字体的名称。</span><span class="sxs-lookup"><span data-stu-id="8d6f1-107">Displays the name of the font used in the trace results grid during traces.</span></span>  
  
 <span data-ttu-id="8d6f1-108">**字号**</span><span class="sxs-lookup"><span data-stu-id="8d6f1-108">**Font size**</span></span>  
 <span data-ttu-id="8d6f1-109">显示在跟踪过程中“跟踪结果”网格所使用字体的大小。</span><span class="sxs-lookup"><span data-stu-id="8d6f1-109">Displays the size of the font used in the trace results grid during traces.</span></span>  
  
 <span data-ttu-id="8d6f1-110">**选择字体**</span><span class="sxs-lookup"><span data-stu-id="8d6f1-110">**Choose Font**</span></span>  
 <span data-ttu-id="8d6f1-111">打开一个对话框，可以在其中更改字体设置。</span><span class="sxs-lookup"><span data-stu-id="8d6f1-111">Opens a dialog to change the font settings.</span></span>  
  
 <span data-ttu-id="8d6f1-112">**使用区域设置来显示日期和时间值**</span><span class="sxs-lookup"><span data-stu-id="8d6f1-112">**Use regional settings to display date and time values**</span></span>  
 <span data-ttu-id="8d6f1-113">使用为计算机配置的区域设置显示日期和时间值。</span><span class="sxs-lookup"><span data-stu-id="8d6f1-113">Displays date and time values in regional settings configured for your computer.</span></span> <span data-ttu-id="8d6f1-114">如果不选择此选项，日期和时间值将采用 Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]使用的固定格式显示，在该格式中包含毫秒。</span><span class="sxs-lookup"><span data-stu-id="8d6f1-114">If you do not select this option, the date and time values are displayed in the fixed format used by Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], which includes milliseconds.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8d6f1-115">切换此复选框将更改时间列的显示格式，如 **StartTime** 和 **EndTime**。</span><span class="sxs-lookup"><span data-stu-id="8d6f1-115">Toggling this checkbox changes the time columns display format such as **StartTime** and **EndTime**.</span></span> <span data-ttu-id="8d6f1-116">但是，此操作不会更改语言事件或远程过程调用 (RPC) 中的 **DateTime** 值参数。</span><span class="sxs-lookup"><span data-stu-id="8d6f1-116">However, it does not change the **DateTime** value parameters inside the language events or remote procedure calls (RPCs).</span></span>  
  
 <span data-ttu-id="8d6f1-117">**在“持续时间”列中以微秒为单位显示值**</span><span class="sxs-lookup"><span data-stu-id="8d6f1-117">**Show values in Duration column in microseconds**</span></span>  
 <span data-ttu-id="8d6f1-118">在跟踪的 **“持续时间”** 数据列中以微秒为单位显示值。</span><span class="sxs-lookup"><span data-stu-id="8d6f1-118">Displays the values in microseconds in the **Duration** data column of traces.</span></span> <span data-ttu-id="8d6f1-119">默认情况下， **“持续时间”** 列以毫秒为单位显示值。</span><span class="sxs-lookup"><span data-stu-id="8d6f1-119">By default, the **Duration** column displays values in milliseconds.</span></span>  
  
### <a name="tracing-options"></a><span data-ttu-id="8d6f1-120">跟踪选项</span><span class="sxs-lookup"><span data-stu-id="8d6f1-120">Tracing Options</span></span>  
 <span data-ttu-id="8d6f1-121">**建立连接后立即开始跟踪**</span><span class="sxs-lookup"><span data-stu-id="8d6f1-121">**Start tracing immediately after making connection**</span></span>  
 <span data-ttu-id="8d6f1-122">建立连接后立即使用默认模板开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="8d6f1-122">Begin a trace using the default template as soon as a connection is made.</span></span>  
  
 <span data-ttu-id="8d6f1-123">**当提供程序版本发生更改时更新跟踪定义**</span><span class="sxs-lookup"><span data-stu-id="8d6f1-123">**Update trace definition when provider version changes**</span></span>  
 <span data-ttu-id="8d6f1-124">更新提供程序后，为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 应用最新的跟踪定义。</span><span class="sxs-lookup"><span data-stu-id="8d6f1-124">Apply the most current trace definition to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] when the provider is updated.</span></span> <span data-ttu-id="8d6f1-125">默认情况下不选中此项。</span><span class="sxs-lookup"><span data-stu-id="8d6f1-125">This item is not checked by default.</span></span> <span data-ttu-id="8d6f1-126">此选项强制 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 在服务器中查询跟踪定义，如果存在，则将在磁盘上重新创建该文件。</span><span class="sxs-lookup"><span data-stu-id="8d6f1-126">This forces [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] to query the server for the trace definition and re-create, if one exists, the file on disk.</span></span>  
  
### <a name="file-rollover-options"></a><span data-ttu-id="8d6f1-127">文件滚动更新选项</span><span class="sxs-lookup"><span data-stu-id="8d6f1-127">File Rollover Options</span></span>  
 <span data-ttu-id="8d6f1-128">**不作提示，依次加载所有滚动更新文件**</span><span class="sxs-lookup"><span data-stu-id="8d6f1-128">**Load all rollover files in sequence without prompting**</span></span>  
 <span data-ttu-id="8d6f1-129">在打开跟踪文件时，自动加载滚动更新文件。</span><span class="sxs-lookup"><span data-stu-id="8d6f1-129">Load rollover files automatically when a trace file is opened.</span></span> <span data-ttu-id="8d6f1-130">如果在跟踪时创建了多个文件，选择此选项可以自动加载所有滚动更新文件。</span><span class="sxs-lookup"><span data-stu-id="8d6f1-130">If more than one file was created while tracing, selecting this option automatically loads all rollover files.</span></span>  
  
 <span data-ttu-id="8d6f1-131">**加载滚动更新文件之前进行提示**</span><span class="sxs-lookup"><span data-stu-id="8d6f1-131">**Prompt before loading rollover files**</span></span>  
 <span data-ttu-id="8d6f1-132">打开跟踪文件后，让 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 在添加滚动更新文件之前进行提示。</span><span class="sxs-lookup"><span data-stu-id="8d6f1-132">Have [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] prompt you before adding a rollover file when a trace file is opened.</span></span>  
  
 <span data-ttu-id="8d6f1-133">**从不加载后续滚动更新文件**</span><span class="sxs-lookup"><span data-stu-id="8d6f1-133">**Never load subsequent rollover files**</span></span>  
 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] <span data-ttu-id="8d6f1-134">从不在跟踪文件处于打开状态时加载后续滚动更新文件。</span><span class="sxs-lookup"><span data-stu-id="8d6f1-134">never loads subsequent rollover files when a trace file is opened.</span></span>  
  
### <a name="replay-options"></a><span data-ttu-id="8d6f1-135">重播选项</span><span class="sxs-lookup"><span data-stu-id="8d6f1-135">Replay Options</span></span>  
 <span data-ttu-id="8d6f1-136">**默认重播线程数**</span><span class="sxs-lookup"><span data-stu-id="8d6f1-136">**Default number of replay threads**</span></span>  
 <span data-ttu-id="8d6f1-137">指定要并发使用的重播线程数。</span><span class="sxs-lookup"><span data-stu-id="8d6f1-137">Specify the number of replay threads to use concurrently.</span></span> <span data-ttu-id="8d6f1-138">数目越大，重播期间消耗的资源越多，但是可增加并发的重播事件数目。</span><span class="sxs-lookup"><span data-stu-id="8d6f1-138">A higher number consumes more resources during replay, but increases replay concurrency.</span></span>  
  
 <span data-ttu-id="8d6f1-139">**默认 Health Monitor 等待间隔(秒)**</span><span class="sxs-lookup"><span data-stu-id="8d6f1-139">**Default health monitor wait interval (sec)**</span></span>  
 <span data-ttu-id="8d6f1-140">指定重播的等待间隔（秒）。</span><span class="sxs-lookup"><span data-stu-id="8d6f1-140">Specify the wait interval to replay in seconds.</span></span> <span data-ttu-id="8d6f1-141">默认值为 3600 秒（1 小时）。</span><span class="sxs-lookup"><span data-stu-id="8d6f1-141">Default is 3600 seconds (1 hour).</span></span> <span data-ttu-id="8d6f1-142">此设置影响线程在被 Health Monitor 终止前所允许运行的时间。</span><span class="sxs-lookup"><span data-stu-id="8d6f1-142">This setting affects the amount of time a thread is allowed to run before being terminated by the health monitor.</span></span>  
  
 <span data-ttu-id="8d6f1-143">**默认 Health Monitor 轮询间隔(秒)**</span><span class="sxs-lookup"><span data-stu-id="8d6f1-143">**Default health monitor poll interval (sec)**</span></span>  
 <span data-ttu-id="8d6f1-144">指定重播过程中的 Health Monitor 轮询间隔（秒）。</span><span class="sxs-lookup"><span data-stu-id="8d6f1-144">Specify the health monitor poll interval during replay in seconds.</span></span> <span data-ttu-id="8d6f1-145">默认值为 60 秒。</span><span class="sxs-lookup"><span data-stu-id="8d6f1-145">Default is 60 seconds.</span></span> <span data-ttu-id="8d6f1-146">使用此值，用户可以配置 Health Monitor 对终止候选项的轮询频率。</span><span class="sxs-lookup"><span data-stu-id="8d6f1-146">This value allows the user to configure how often the health monitor polls for candidates for termination.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d6f1-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8d6f1-147">See Also</span></span>  
 <span data-ttu-id="8d6f1-148">[连接到服务器后自动启动跟踪 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="8d6f1-148">[Start a Trace Automatically after Connecting to a Server &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="8d6f1-149">[设置跟踪显示默认值 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="8d6f1-149">[Set Trace Display Defaults &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="8d6f1-150">[重播跟踪表 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="8d6f1-150">[Replay a Trace Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="8d6f1-151">[重播跟踪文件 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="8d6f1-151">[Replay a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="8d6f1-152">[重播跟踪](../tools/sql-server-profiler/replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="8d6f1-152">[Replay Traces](../tools/sql-server-profiler/replay-traces.md) </span></span>  
 <span data-ttu-id="8d6f1-153">[设置全局跟踪选项 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/set-global-trace-options-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="8d6f1-153">[Set Global Trace Options &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/set-global-trace-options-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="8d6f1-154">[SQL Server Profiler 模板和权限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="8d6f1-154">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="8d6f1-155">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="8d6f1-155">SQL Server Profiler</span></span>](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
