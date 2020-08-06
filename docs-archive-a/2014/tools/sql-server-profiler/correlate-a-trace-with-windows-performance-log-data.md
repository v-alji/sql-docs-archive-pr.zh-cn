---
title: 将跟踪与 Windows 性能日志数据关联 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- correlating trace with log data
- logs [SQL Server], traces
- Profiler [SQL Server Profiler], correlating trace with log data
- traces [SQL Server], logs
- SQL Server Profiler, correlating trace with log data
ms.assetid: 1e4412c8-d27c-4aae-9b35-214128d1d00a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 879441c948f0ad04b971159a37ec0dcec90e3ada
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682510"
---
# <a name="correlate-a-trace-with-windows-performance-log-data"></a><span data-ttu-id="d7042-102">将跟踪与 Windows 性能日志数据关联</span><span class="sxs-lookup"><span data-stu-id="d7042-102">Correlate a Trace with Windows Performance Log Data</span></span>
  <span data-ttu-id="d7042-103">使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]，您可以打开 Microsoft Windows 性能日志、选择要与跟踪关联的计数器，并在 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 图形用户界面中将所选性能计数器与跟踪一起显示。</span><span class="sxs-lookup"><span data-stu-id="d7042-103">Using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can open a Microsoft Windows performance log, choose the counters you want to correlate with a trace, and display the selected performance counters alongside the trace in the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] graphical user interface.</span></span> <span data-ttu-id="d7042-104">选择跟踪窗口中的事件时， [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 的系统监视器数据窗口窗格中的红色竖线用于指示与所选跟踪事件关联的性能日志数据。</span><span class="sxs-lookup"><span data-stu-id="d7042-104">When you select an event in the trace window, a vertical red bar in the System Monitor data window pane of [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] indicates the performance log data that correlates with the selected trace event.</span></span>  
  
 <span data-ttu-id="d7042-105">若要将跟踪与性能计数器关联，请打开包含 StartTime  和 EndTime  数据列的跟踪文件或表，然后在  **的“文件”** [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]菜单上，单击“导入性能数据”  。</span><span class="sxs-lookup"><span data-stu-id="d7042-105">To correlate a trace with performance counters, open a trace file or table that contains the **StartTime** and **EndTime** data columns, and then click **Import Performance Data** on the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **File** menu.</span></span> <span data-ttu-id="d7042-106">然后您就可以打开性能日志，选择要与跟踪关联的系统监视器对象和计数器。</span><span class="sxs-lookup"><span data-stu-id="d7042-106">You can then open a performance log, and select the System Monitor objects and counters that you want to correlate with the trace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7042-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d7042-107">See Also</span></span>  
 [<span data-ttu-id="d7042-108">将跟踪与 Windows 性能日志数据关联 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="d7042-108">Correlate a Trace with Windows Performance Log Data &#40;SQL Server Profiler&#41;</span></span>](correlate-a-trace-with-windows-performance-log-data.md)  
  
  
