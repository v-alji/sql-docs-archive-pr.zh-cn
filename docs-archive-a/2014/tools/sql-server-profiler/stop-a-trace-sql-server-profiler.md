---
title: 停止跟踪 (SQL Server Profiler) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], stopping
- stopping traces
ms.assetid: 47c4f33d-63e0-4444-bec8-4c1c91f8e25c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 501ea4a4838f8e2ea42fc475c486466d48020a4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690944"
---
# <a name="stop-a-trace-sql-server-profiler"></a><span data-ttu-id="52f77-102">停止跟踪 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="52f77-102">Stop a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="52f77-103">本主题介绍如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]停止正在运行的跟踪。</span><span class="sxs-lookup"><span data-stu-id="52f77-103">This topic describes how to stop a trace that is running by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
 <span data-ttu-id="52f77-104">停止跟踪将停止捕获数据。</span><span class="sxs-lookup"><span data-stu-id="52f77-104">Stopping a trace stops data from being captured.</span></span> <span data-ttu-id="52f77-105">停止跟踪后，除非已将数据捕获到了跟踪文件或跟踪表中，否则重新启动该跟踪将丢失以前捕获的数据。</span><span class="sxs-lookup"><span data-stu-id="52f77-105">After a trace is stopped, it cannot be restarted without losing previously captured data, unless the data has been captured to a trace file or trace table.</span></span> <span data-ttu-id="52f77-106">您还可以在停止跟踪后将收集的数据保存到表或文件。</span><span class="sxs-lookup"><span data-stu-id="52f77-106">You can also save the collected data to a table or file after stopping a trace.</span></span> <span data-ttu-id="52f77-107">当停止跟踪时，以前选择的所有跟踪属性将保留，</span><span class="sxs-lookup"><span data-stu-id="52f77-107">All trace properties that were previously selected are preserved when a trace is stopped.</span></span> <span data-ttu-id="52f77-108">您也可以更改名称、事件、列和筛选器。</span><span class="sxs-lookup"><span data-stu-id="52f77-108">When a trace is stopped, you can change the name, events, columns, and filters.</span></span>  
  
### <a name="to-stop-a-trace"></a><span data-ttu-id="52f77-109">停止跟踪</span><span class="sxs-lookup"><span data-stu-id="52f77-109">To stop a trace</span></span>  
  
1.  <span data-ttu-id="52f77-110">选择正在运行的跟踪。</span><span class="sxs-lookup"><span data-stu-id="52f77-110">Select a trace that is running.</span></span>  
  
2.  <span data-ttu-id="52f77-111">在 **“文件”** 菜单上，单击 **“停止跟踪”** 。</span><span class="sxs-lookup"><span data-stu-id="52f77-111">On the **File** menu, click **Stop Trace**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52f77-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="52f77-112">See Also</span></span>  
 [<span data-ttu-id="52f77-113">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="52f77-113">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
