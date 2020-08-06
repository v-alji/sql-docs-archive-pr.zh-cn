---
title: 限制跟踪文件和表的大小 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- maximum file size for traces
- traces [SQL Server], file size
- size [SQL Server], tables
- file rollover option [SQL Server]
- size [SQL Server], files
ms.assetid: 88c31b02-f44c-4a14-be8b-437f2097de12
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b7795dfdadb8fb3bbaa1b55dcd5c962d24a7ba29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588460"
---
# <a name="limit-trace-file-and-table-sizes"></a><span data-ttu-id="bc9c0-102">限制跟踪文件和表的大小</span><span class="sxs-lookup"><span data-stu-id="bc9c0-102">Limit Trace File and Table Sizes</span></span>
  <span data-ttu-id="bc9c0-103">SQL 跟踪结果的大小依赖于跟踪中包括的事件类和 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的用法。</span><span class="sxs-lookup"><span data-stu-id="bc9c0-103">SQL Trace results vary in size depending on the event classes that are included in the trace and the way in which the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is used.</span></span> <span data-ttu-id="bc9c0-104">如果跟踪经常出现的事件类，则可以通过设置最大文件大小或最大行数来最小化跟踪收集的数据量。</span><span class="sxs-lookup"><span data-stu-id="bc9c0-104">If you trace event classes that occur frequently, you can minimize the amount of data that the trace collects by setting the maximum file size or the maximum number of rows.</span></span> <span data-ttu-id="bc9c0-105">通过指定最大文件大小或行数，可以确保跟踪文件或表不会增长到超出指定范围。</span><span class="sxs-lookup"><span data-stu-id="bc9c0-105">By specifying the maximum file size or rows, you ensure that the trace file or table will not grow beyond the specified limit.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bc9c0-106">如果将跟踪数据保存到已经存在的文件，则可以向该文件追加数据或覆盖该文件。</span><span class="sxs-lookup"><span data-stu-id="bc9c0-106">If you save trace data to a file that already exists, you can append data to the file or overwrite the file.</span></span> <span data-ttu-id="bc9c0-107">如果选择向该文件追加数据，而此跟踪文件已经达到或超过指定的最大文件大小，则会通知您，并提示您可以增加最大文件大小或指定新文件。</span><span class="sxs-lookup"><span data-stu-id="bc9c0-107">If you choose to append data to the file, and the trace file already meets or exceeds the specified maximum file size, you are notified and given the opportunity either to increase the maximum file size or specify a new file.</span></span> <span data-ttu-id="bc9c0-108">对跟踪表也是如此。</span><span class="sxs-lookup"><span data-stu-id="bc9c0-108">The same is true for trace tables.</span></span>  
  
## <a name="maximum-file-size"></a><span data-ttu-id="bc9c0-109">文件大小上限</span><span class="sxs-lookup"><span data-stu-id="bc9c0-109">Maximum File Size</span></span>  
 <span data-ttu-id="bc9c0-110">指定有最大文件大小的跟踪在达到最大文件大小时，会停止将跟踪信息保存到该文件。</span><span class="sxs-lookup"><span data-stu-id="bc9c0-110">A trace that has a maximum file size stops saving trace information to the file after the maximum file size has been reached.</span></span> <span data-ttu-id="bc9c0-111">使用此选项可将事件分组成更小、更容易管理的文件。</span><span class="sxs-lookup"><span data-stu-id="bc9c0-111">This option allows you to group events into smaller, more manageable files.</span></span> <span data-ttu-id="bc9c0-112">此外，限制文件大小使得无人参与的跟踪运行起来更加安全，因为跟踪会在达到最大文件大小后停止。</span><span class="sxs-lookup"><span data-stu-id="bc9c0-112">In addition, limiting file size makes it safer to run unattended traces, because the trace stops when the maximum file size is reached.</span></span> <span data-ttu-id="bc9c0-113">可以为通过 Transact-SQL 存储过程或使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]创建的跟踪设置最大文件大小。</span><span class="sxs-lookup"><span data-stu-id="bc9c0-113">You can set the maximum file size for traces created by means of Transact-SQL stored procedures or by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
 <span data-ttu-id="bc9c0-114">最大文件大小选项的上限为 1 GB。</span><span class="sxs-lookup"><span data-stu-id="bc9c0-114">There is an upper limit of 1 gigabyte (GB) for the maximum file size option.</span></span> <span data-ttu-id="bc9c0-115">默认最大文件大小为 5 MB。</span><span class="sxs-lookup"><span data-stu-id="bc9c0-115">The default maximum file size is 5 megabytes (MB).</span></span>  
  
### <a name="enabling-file-rollover"></a><span data-ttu-id="bc9c0-116">启用文件滚动更新</span><span class="sxs-lookup"><span data-stu-id="bc9c0-116">Enabling File Rollover</span></span>  
 <span data-ttu-id="bc9c0-117">如果使用文件滚动更新选项，则在达到最大文件大小时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会关闭当前文件并创建一个新文件。</span><span class="sxs-lookup"><span data-stu-id="bc9c0-117">The file rollover option causes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to close the current file and create a new file when the maximum file size is reached.</span></span> <span data-ttu-id="bc9c0-118">新文件与原文件同名，但是文件名后将追加一个整数以表示其序列。</span><span class="sxs-lookup"><span data-stu-id="bc9c0-118">The new file has the same name as the previous file, but an integer is appended to the name to indicate its sequence.</span></span> <span data-ttu-id="bc9c0-119">例如，如果原始跟踪文件命名为 filename_1.trc，则下一跟踪文件为 filename_2.trc，依此类推。</span><span class="sxs-lookup"><span data-stu-id="bc9c0-119">For example, if the original trace file is named filename_1.trc, the next trace file is filename_2.trc, and so on.</span></span> <span data-ttu-id="bc9c0-120">如果指定给新滚动更新文件的名称已经被现有文件使用，则将覆盖现有文件，除非现有文件为只读文件。</span><span class="sxs-lookup"><span data-stu-id="bc9c0-120">If the name assigned to a new rollover file is already used by an existing file, the existing file is overwritten unless it is read only.</span></span> <span data-ttu-id="bc9c0-121">将跟踪数据保存到文件时，默认情况下启用文件滚动选项。</span><span class="sxs-lookup"><span data-stu-id="bc9c0-121">The file rollover option is enabled by default when you are saving trace data to a file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bc9c0-122">如果启用了文件滚动更新选项，则在使用其他某种方法停止跟踪之前，跟踪将一直继续。</span><span class="sxs-lookup"><span data-stu-id="bc9c0-122">With the file rollover option on, the trace continues until it is stopped by some other means.</span></span> <span data-ttu-id="bc9c0-123">若要停止在达到文件大小限制后进行跟踪，请禁用文件滚动更新选项。</span><span class="sxs-lookup"><span data-stu-id="bc9c0-123">To stop the trace after you have reached the file size limit, disable the file rollover option.</span></span>  
  
 <span data-ttu-id="bc9c0-124">**设置跟踪文件的最大文件大小**</span><span class="sxs-lookup"><span data-stu-id="bc9c0-124">**To set a maximum file size for a trace file**</span></span>  
  
 [<span data-ttu-id="bc9c0-125">设置跟踪文件的最大文件大小 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="bc9c0-125">Set a Maximum File Size for a Trace File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-a-maximum-file-size-for-a-trace-file-sql-server-profiler.md)  
  
## <a name="maximum-number-of-rows"></a><span data-ttu-id="bc9c0-126">最大行数</span><span class="sxs-lookup"><span data-stu-id="bc9c0-126">Maximum Number of Rows</span></span>  
 <span data-ttu-id="bc9c0-127">指定有最大行数的跟踪在达到最大行数时，会停止将跟踪信息保存到表。</span><span class="sxs-lookup"><span data-stu-id="bc9c0-127">A trace with a maximum number of rows stops saving trace information to a table after the maximum number of rows has been reached.</span></span> <span data-ttu-id="bc9c0-128">每个事件构成一行，因此该参数可设置收集的事件数的范围。</span><span class="sxs-lookup"><span data-stu-id="bc9c0-128">Each event constitutes one row, so this parameter sets a limit on the number of events that are gathered.</span></span> <span data-ttu-id="bc9c0-129">设置最大行数使得无人参与的跟踪运行起来更加方便。</span><span class="sxs-lookup"><span data-stu-id="bc9c0-129">Setting the maximum number of rows makes it easier to run unattended traces.</span></span> <span data-ttu-id="bc9c0-130">例如，如果需要启动一个将跟踪数据保存到表的跟踪，同时希望在该表变得过大时停止跟踪，则可以使其自动停止。</span><span class="sxs-lookup"><span data-stu-id="bc9c0-130">For example, if you need to start a trace that saves trace data to a table, but you want to stop the trace if the table becomes too large, you can do so automatically.</span></span>  
  
 <span data-ttu-id="bc9c0-131">如果已指定并且达到了最大行数，将在运行 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 的同时继续运行跟踪，但不再记录跟踪信息。</span><span class="sxs-lookup"><span data-stu-id="bc9c0-131">When the maximum number of rows is specified and the maximum number of rows has been reached, the trace continues to run while [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] is running, but the trace information is no longer recorded.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="bc9c0-132">将继续显示跟踪结果，直到跟踪停止。</span><span class="sxs-lookup"><span data-stu-id="bc9c0-132">continues to display the trace results until the trace stops.</span></span>  
  
 <span data-ttu-id="bc9c0-133">**设置跟踪的最大行数**</span><span class="sxs-lookup"><span data-stu-id="bc9c0-133">**To set a maximum number of rows for a trace**</span></span>  
  
 [<span data-ttu-id="bc9c0-134">设置跟踪表的最大表大小 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="bc9c0-134">Set a Maximum Table Size for a Trace Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-a-maximum-table-size-for-a-trace-table-sql-server-profiler.md)  
  
## <a name="see-also"></a><span data-ttu-id="bc9c0-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bc9c0-135">See Also</span></span>  
 [<span data-ttu-id="bc9c0-136">sp_trace_create (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="bc9c0-136">sp_trace_create &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql)  
  
  
