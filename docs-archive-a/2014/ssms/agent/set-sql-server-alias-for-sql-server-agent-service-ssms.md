---
title: 设置跟踪筛选器 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], traces
- traces [SQL Server], filters
ms.assetid: 7b976a84-7381-43a6-a828-ba83ada71cbe
author: stevestein
ms.author: sstein
ms.openlocfilehash: 47d797c84a05f50da026280f6e197f965d804426
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588234"
---
# <a name="set-a-trace-filter-transact-sql"></a><span data-ttu-id="f5068-102">设置跟踪筛选器 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f5068-102">Set a Trace Filter (Transact-SQL)</span></span>
  <span data-ttu-id="f5068-103">本主题介绍了如何使用存储过程创建只检索有关所需跟踪事件信息的筛选器。</span><span class="sxs-lookup"><span data-stu-id="f5068-103">This topic describes how to use stored procedures to create a filter that retrieves only the information you need on an event being traced.</span></span>  
  
### <a name="to-set-a-trace-filter"></a><span data-ttu-id="f5068-104">设置跟踪筛选器</span><span class="sxs-lookup"><span data-stu-id="f5068-104">To set a trace filter</span></span>  
  
1.  <span data-ttu-id="f5068-105">如果跟踪已在运行，请在执行 **sp_trace_setstatus** 时通过指定 **@status = 0** 停止跟踪。</span><span class="sxs-lookup"><span data-stu-id="f5068-105">If the trace is already running, execute **sp_trace_setstatus** by specifying **@status = 0** to stop the trace.</span></span>  
  
2.  <span data-ttu-id="f5068-106">执行 **sp_trace_setfilter** 以配置有关检索跟踪事件信息的类型。</span><span class="sxs-lookup"><span data-stu-id="f5068-106">Execute **sp_trace_setfilter** to configure the type of information to retrieve for the event being traced.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f5068-107">与常规的存储过程不同，所有 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 存储过程 (<strong>sp_trace_xx</strong>) 参数的类型都受到严格限制，不支持自动的数据类型转换\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5068-107">Unlike regular stored procedures, parameters of all [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] stored procedures (<strong>sp_trace_*xx*</strong>) are strictly typed and do not support automatic data type conversion.</span></span> <span data-ttu-id="f5068-108">如果没有用正确的输入参数数据类型（参数说明中指定的类型）来调用这些参数，则存储过程将返回错误。</span><span class="sxs-lookup"><span data-stu-id="f5068-108">If these parameters are not called with the correct input parameter data types, as specified in the argument description, the stored procedure will return an error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5068-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f5068-109">See Also</span></span>  
 <span data-ttu-id="f5068-110">[筛选跟踪](../../relational-databases/sql-trace/filter-a-trace.md) </span><span class="sxs-lookup"><span data-stu-id="f5068-110">[Filter a Trace](../../relational-databases/sql-trace/filter-a-trace.md) </span></span>  
 <span data-ttu-id="f5068-111">[sp_trace_setfilter &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f5068-111">[sp_trace_setfilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql) </span></span>  
 <span data-ttu-id="f5068-112">[sp_trace_setstatus &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f5068-112">[sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql) </span></span>  
 <span data-ttu-id="f5068-113">[&#40;Transact-sql&#41;系统存储过程](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f5068-113">[System Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span></span>  
 [<span data-ttu-id="f5068-114">SQL Server Profiler 存储过程 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f5068-114">SQL Server Profiler Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
