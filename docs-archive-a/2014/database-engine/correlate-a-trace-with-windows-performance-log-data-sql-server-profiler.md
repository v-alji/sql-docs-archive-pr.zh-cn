---
title: 将跟踪与 Windows 性能日志数据 (SQL Server Profiler) 相关联 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], logs
ms.assetid: e1b3072c-8daf-49a7-9895-c8cccd2adb95
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 34575cf4270d817ecfbb5b2d1824831cc99454fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586961"
---
# <a name="correlate-a-trace-with-windows-performance-log-data-sql-server-profiler"></a><span data-ttu-id="27385-102">将跟踪与 Windows 性能日志数据关联 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="27385-102">Correlate a Trace with Windows Performance Log Data (SQL Server Profiler)</span></span>
  [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]<span data-ttu-id="27385-103">可以将 Microsoft Windows 系统监视器计数器与 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 或事件相关联 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="27385-103">can correlate Microsoft Windows System Monitor counters with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] events.</span></span> <span data-ttu-id="27385-104">Windows 系统监视器将指定计数器的系统活动记录在性能日志中。</span><span class="sxs-lookup"><span data-stu-id="27385-104">Windows System Monitor logs system activity for specified counters in performance logs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="27385-105">有关在 Windows 不同版本间共享日志的信息，请参阅本主题结尾处介绍的过程。</span><span class="sxs-lookup"><span data-stu-id="27385-105">For information about sharing logs among different versions of Windows, see the procedure at the end of this topic.</span></span>  
  
### <a name="to-correlate-a-trace-with-performance-log-data"></a><span data-ttu-id="27385-106">将跟踪与性能日志数据关联</span><span class="sxs-lookup"><span data-stu-id="27385-106">To correlate a trace with performance log data</span></span>  
  
1.  <span data-ttu-id="27385-107">在 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]中，打开保存的跟踪文件或跟踪表。</span><span class="sxs-lookup"><span data-stu-id="27385-107">In [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)], open a saved trace file or trace table.</span></span> <span data-ttu-id="27385-108">不能关联仍在收集事件数据的运行中的跟踪。</span><span class="sxs-lookup"><span data-stu-id="27385-108">You cannot correlate a running trace that is still collecting event data.</span></span> <span data-ttu-id="27385-109">为实现与系统监视器数据的准确关联，跟踪必须同时包含 **StartTime** 和 **EndTime** 数据列。</span><span class="sxs-lookup"><span data-stu-id="27385-109">For accurate correlation with System Monitor data, the trace must contain both **StartTime** and **EndTime** data columns.</span></span>  
  
2.  <span data-ttu-id="27385-110">在 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] **“文件”** 菜单上，单击“导入性能数据”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27385-110">On the [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] **File** menu, click **Import Performance Data**.</span></span>  
  
3.  <span data-ttu-id="27385-111">在 **“打开”** 对话框中，选择包含性能日志的文件。</span><span class="sxs-lookup"><span data-stu-id="27385-111">In the **Open** dialog box, select a file that contains a performance log.</span></span> <span data-ttu-id="27385-112">必须在捕获跟踪数据的同一时间段捕获性能日志数据。</span><span class="sxs-lookup"><span data-stu-id="27385-112">The performance log data must have been captured during the same time period in which the trace data is captured.</span></span>  
  
4.  <span data-ttu-id="27385-113">在 **“性能计数器限制”** 对话框中，选中与要显示在跟踪旁边的系统监视器对象和计数器相对应的复选框。</span><span class="sxs-lookup"><span data-stu-id="27385-113">In the **Performance Counters Limit** dialog box, select the check boxes that correspond to the System Monitor objects and counters that you want to display alongside the trace.</span></span> <span data-ttu-id="27385-114">单击“确定” **。**</span><span class="sxs-lookup"><span data-stu-id="27385-114">Click **OK.**</span></span>  
  
5.  <span data-ttu-id="27385-115">在跟踪事件窗口中选择一个事件，或者使用箭头键在跟踪事件窗口的几个相邻行中导航。</span><span class="sxs-lookup"><span data-stu-id="27385-115">Select an event in the trace events window, or navigate through several adjacent rows in the trace events window by using the arrow keys.</span></span> <span data-ttu-id="27385-116">**“系统监视器数据”** 窗口中的红色竖线指明与所选跟踪事件关联的性能日志数据。</span><span class="sxs-lookup"><span data-stu-id="27385-116">The vertical red bar in the **System Monitor data** window indicates the performance log data that is correlated with the selected trace event.</span></span>  
  
6.  <span data-ttu-id="27385-117">在系统监视器图形中单击一个相关点。</span><span class="sxs-lookup"><span data-stu-id="27385-117">Click a point of interest in the System Monitor graph.</span></span> <span data-ttu-id="27385-118">将选中时间最接近的相应跟踪行。</span><span class="sxs-lookup"><span data-stu-id="27385-118">The corresponding trace row that is nearest in time is selected.</span></span> <span data-ttu-id="27385-119">若要扩大时间范围，请在系统监视器图形中按住并拖动鼠标指针。</span><span class="sxs-lookup"><span data-stu-id="27385-119">To zoom in on a time range, press and drag the mouse pointer in the System Monitor graph.</span></span>  
  
### <a name="to-create-performance-logs-that-can-be-shared-among-different-versions-of-windows"></a><span data-ttu-id="27385-120">创建可在 Windows 不同版本间共享的性能日志</span><span class="sxs-lookup"><span data-stu-id="27385-120">To create performance logs that can be shared among different versions of Windows</span></span>  
  
1.  <span data-ttu-id="27385-121">在“控制面板”中，打开 **“管理工具”**，再双击 **“性能”**。</span><span class="sxs-lookup"><span data-stu-id="27385-121">In Control Panel, open **Administrative Tools**, and then double click **Performance**.</span></span>  
  
2.  <span data-ttu-id="27385-122">在“性能”对话框中，展开“性能日志和警报”，右键单击“计数器日志”，再单击“新建日志设置”。</span><span class="sxs-lookup"><span data-stu-id="27385-122">In the **Performance** dialog box, expand **Performance Logs and Alerts**, right-click **Counter Logs**, and then click **New Log Settings**.</span></span>  
  
3.  <span data-ttu-id="27385-123">键入计数器日志的名称，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="27385-123">Type a name for the counter log, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="27385-124">在 **“常规”** 选项卡中，单击 **“添加计数器”**。</span><span class="sxs-lookup"><span data-stu-id="27385-124">On the **General** tab, click **Add Counters**.</span></span>  
  
5.  <span data-ttu-id="27385-125">在 **“性能对象”** 列表中，选择要监视的性能对象。</span><span class="sxs-lookup"><span data-stu-id="27385-125">In the **Performance object** list, select a performance object you want to monitor.</span></span> <span data-ttu-id="27385-126">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 默认实例的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 性能对象名称以 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 开头，命名实例以 MSSQL$*instanceName*开头。</span><span class="sxs-lookup"><span data-stu-id="27385-126">The names of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] performance objects for default instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] start with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and named instances start with MSSQL$*instanceName*.</span></span>  
  
6.  <span data-ttu-id="27385-127">添加 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例所需的所有计数器和其他重要值（例如处理器时间和磁盘时间）。</span><span class="sxs-lookup"><span data-stu-id="27385-127">Add as many counters as necessary for your [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance and other important values, such as processor time and disk time.</span></span>  
  
7.  <span data-ttu-id="27385-128">添加计数器后，单击 **“关闭”**。</span><span class="sxs-lookup"><span data-stu-id="27385-128">When you have finished adding counters, click **Close**.</span></span>  
  
8.  <span data-ttu-id="27385-129">设置 **“数据抽样间隔”** 的值。</span><span class="sxs-lookup"><span data-stu-id="27385-129">Set values for the **Sample data every** interval.</span></span> <span data-ttu-id="27385-130">开始时使用适中的抽样间隔值（例如 5 分钟），然后在必要时调整间隔值。</span><span class="sxs-lookup"><span data-stu-id="27385-130">Start with a modest sampling interval, such as 5 minutes, and then adjust the interval if necessary.</span></span>  
  
9. <span data-ttu-id="27385-131">在“日志文件”\*\*\*\* 选项卡上，从“日志文件类型”\*\*\*\* 列表中选择“文本文件（逗号分隔）”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27385-131">On the **Log Files** tab, choose **TextFile (Comma delimited)** from the **Log file type** list.</span></span> <span data-ttu-id="27385-132">逗号分隔文本日志文件可以在不同版本的 Windows 中共享，并可以稍后在报表工具（例如 Microsoft Excel）中查看。</span><span class="sxs-lookup"><span data-stu-id="27385-132">Comma-delimited text log files can be shared among different versions of Windows and can be viewed later in reporting tools such as Microsoft Excel.</span></span>  
  
10. <span data-ttu-id="27385-133">在 **“计划”** 选项卡上，指定监视计划。</span><span class="sxs-lookup"><span data-stu-id="27385-133">On the **Schedule** tab, specify a monitoring schedule.</span></span>  
  
11. <span data-ttu-id="27385-134">单击 **“确定”** 创建性能日志。</span><span class="sxs-lookup"><span data-stu-id="27385-134">Click **OK** to create the performance log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27385-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="27385-135">See Also</span></span>  
 <span data-ttu-id="27385-136">[SQL Server Profiler 模板和权限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="27385-136">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="27385-137">启动 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="27385-137">Start SQL Server Profiler</span></span>](../tools/sql-server-profiler/start-sql-server-profiler.md)  
  
  
