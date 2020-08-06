---
title: 将跟踪结果保存到文件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 74f80667-62f3-4e14-bb1a-f0c2b6ef3402
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 644fc812bbb4863c336ff2f53f5b2d67ee0a4d5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578033"
---
# <a name="save-trace-results-to-a-file"></a><span data-ttu-id="bb784-102">将跟踪结果保存到文件</span><span class="sxs-lookup"><span data-stu-id="bb784-102">Save Trace Results to a File</span></span>
  <span data-ttu-id="bb784-103">可以将跟踪结果保存到文件中。</span><span class="sxs-lookup"><span data-stu-id="bb784-103">You can save trace results to a file.</span></span> <span data-ttu-id="bb784-104">跟踪文件是写入跟踪结果的文件。</span><span class="sxs-lookup"><span data-stu-id="bb784-104">A trace file is a file where the trace results are written.</span></span> <span data-ttu-id="bb784-105">跟踪文件可以位于本地目录（如 C:\\foldername  \\filename.trc  ）中，也可以位于在网络目录（如 \\\computername\sharename\filename.trc）中。</span><span class="sxs-lookup"><span data-stu-id="bb784-105">A trace file can be located either in a local directory (such as C:\\*foldername*\\*filename.trc*) or a network directory (such as \\\computername\sharename\filename.trc).</span></span>  
  
 <span data-ttu-id="bb784-106">可以使用跟踪文件执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="bb784-106">You can use the trace files to do the following:</span></span>  
  
-   <span data-ttu-id="bb784-107">重播跟踪</span><span class="sxs-lookup"><span data-stu-id="bb784-107">Replay traces</span></span>  
  
-   <span data-ttu-id="bb784-108">审核 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb784-108">Audit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="bb784-109">进行性能分析</span><span class="sxs-lookup"><span data-stu-id="bb784-109">Conduct performance analysis</span></span>  
  
-   <span data-ttu-id="bb784-110">将跟踪事件与性能计数器关联以增强问题检测能力</span><span class="sxs-lookup"><span data-stu-id="bb784-110">Correlate trace events with performance counters to enhance problem detection</span></span>  
  
-   <span data-ttu-id="bb784-111">执行数据库引擎优化顾问分析</span><span class="sxs-lookup"><span data-stu-id="bb784-111">Perform Database Engine Tuning Advisor analysis</span></span>  
  
-   <span data-ttu-id="bb784-112">执行查询优化</span><span class="sxs-lookup"><span data-stu-id="bb784-112">Carry out query optimization</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="bb784-113">如果为 **@tracefile** 存储过程**sp_trace_create**的参数指定了路径和文件名，则会将跟踪结果保存到文件。</span><span class="sxs-lookup"><span data-stu-id="bb784-113">saves trace results to a file when a path and file name are specified for the **@tracefile** argument of the stored procedure **sp_trace_create**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bb784-114">如果为存储过程 **sp_trace_create** 指定路径用来保存跟踪文件，则服务器必须可以访问该目录。</span><span class="sxs-lookup"><span data-stu-id="bb784-114">If a path is specified to the **sp_trace_create** stored procedure for saving the trace file, the directory must be accessible to the server.</span></span> <span data-ttu-id="bb784-115">同时注意，如果为 **sp_trace_create**指定本地目录，则该目录应是服务器上的本地目录。</span><span class="sxs-lookup"><span data-stu-id="bb784-115">Also be aware that if a local directory is specified to **sp_trace_create**, it is a local directory on the server computer.</span></span>  
  
 <span data-ttu-id="bb784-116">如果使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ，则可以将跟踪结果保存到文件或表中。</span><span class="sxs-lookup"><span data-stu-id="bb784-116">If [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] is used, it allows you to save trace results to a file or to a table.</span></span> <span data-ttu-id="bb784-117">将跟踪结果保存到表中后，可以与将跟踪保存到文件中后一样进行访问，另外还可以查询表以搜索特定事件。</span><span class="sxs-lookup"><span data-stu-id="bb784-117">Saving trace results to a table allows the same access as saving the trace to a file plus you can query the table to search for specific events.</span></span>  
  
 <span data-ttu-id="bb784-118">有关保存跟踪结果的详细信息，请参阅 [将跟踪结果保存到表 (SQL Server Profiler)](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md) 和 [将跟踪结果保存到文件 (SQL Server Profiler)](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="bb784-118">For more information about saving trace results, see [Save Trace Results to a Table &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md) and [Save Trace Results to a File &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb784-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bb784-119">See Also</span></span>  
 <span data-ttu-id="bb784-120">[sp_trace_create (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bb784-120">[sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql) </span></span>  
 <span data-ttu-id="bb784-121">[创建跟踪 (Transact-SQL)](../sql-trace/create-a-trace-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="bb784-121">[Create a Trace &#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md) </span></span>  
 [<span data-ttu-id="bb784-122">创建跟踪 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="bb784-122">Create a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
  
