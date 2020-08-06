---
title: 修改现有跟踪 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], modifying
- modifying traces
ms.assetid: 8792b43f-2510-44e3-9239-e73ad8227b89
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 55b8172ef8e6188059c484ab41f1a719e0e9f8c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578035"
---
# <a name="modify-an-existing-trace-transact-sql"></a><span data-ttu-id="bdaaf-102">修改现有跟踪 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="bdaaf-102">Modify an Existing Trace (Transact-SQL)</span></span>
  <span data-ttu-id="bdaaf-103">本主题介绍了如何使用存储过程修改现有跟踪。</span><span class="sxs-lookup"><span data-stu-id="bdaaf-103">This topic describes how to use stored procedures to modify an existing trace.</span></span>  
  
### <a name="to-modify-an-existing-trace"></a><span data-ttu-id="bdaaf-104">修改现有跟踪</span><span class="sxs-lookup"><span data-stu-id="bdaaf-104">To modify an existing trace</span></span>  
  
1.  <span data-ttu-id="bdaaf-105">如果跟踪已在运行，请在执行 **sp_trace_setstatus** 时通过指定 **@status = 0** 停止跟踪。</span><span class="sxs-lookup"><span data-stu-id="bdaaf-105">If the trace is already running, execute **sp_trace_setstatus** by specifying **@status = 0** to stop the trace.</span></span>  
  
2.  <span data-ttu-id="bdaaf-106">若要修改跟踪事件，请执行 **sp_trace_setevent** ，并通过参数指定更改。</span><span class="sxs-lookup"><span data-stu-id="bdaaf-106">To modify trace events, execute **sp_trace_setevent** by specifying the changes through the parameters.</span></span> <span data-ttu-id="bdaaf-107">下面按顺序列出了参数：</span><span class="sxs-lookup"><span data-stu-id="bdaaf-107">Listed in order, the parameters are:</span></span>  
  
    -   <span data-ttu-id="bdaaf-108">**@traceid** (跟踪 ID) </span><span class="sxs-lookup"><span data-stu-id="bdaaf-108">**@traceid** (Trace ID)</span></span>  
  
    -   <span data-ttu-id="bdaaf-109">**@eventid** (事件 ID) </span><span class="sxs-lookup"><span data-stu-id="bdaaf-109">**@eventid** (Event ID)</span></span>  
  
    -   <span data-ttu-id="bdaaf-110">**@columnid** (列 ID) </span><span class="sxs-lookup"><span data-stu-id="bdaaf-110">**@columnid** (Column ID)</span></span>  
  
    -   <span data-ttu-id="bdaaf-111">**@on**) 上的 (</span><span class="sxs-lookup"><span data-stu-id="bdaaf-111">**@on** (ON)</span></span>  
  
     <span data-ttu-id="bdaaf-112">修改 **@on** 参数时，请记住它与参数的交互 **@columnid** ：</span><span class="sxs-lookup"><span data-stu-id="bdaaf-112">When you modify the **@on** parameter, keep in mind its interaction with the **@columnid** parameter:</span></span>  
  
    |<span data-ttu-id="bdaaf-113">ON</span><span class="sxs-lookup"><span data-stu-id="bdaaf-113">ON</span></span>|<span data-ttu-id="bdaaf-114">列 ID</span><span class="sxs-lookup"><span data-stu-id="bdaaf-114">Column ID</span></span>|<span data-ttu-id="bdaaf-115">结果</span><span class="sxs-lookup"><span data-stu-id="bdaaf-115">Result</span></span>|  
    |--------|---------------|------------|  
    |<span data-ttu-id="bdaaf-116">ON (**1**)</span><span class="sxs-lookup"><span data-stu-id="bdaaf-116">ON (**1**)</span></span>|<span data-ttu-id="bdaaf-117">Null</span><span class="sxs-lookup"><span data-stu-id="bdaaf-117">NULL</span></span>|<span data-ttu-id="bdaaf-118">事件打开，</span><span class="sxs-lookup"><span data-stu-id="bdaaf-118">Event is turned on.</span></span> <span data-ttu-id="bdaaf-119">所有列被清除。</span><span class="sxs-lookup"><span data-stu-id="bdaaf-119">All columns are cleared.</span></span>|  
    ||<span data-ttu-id="bdaaf-120">NOT NULL</span><span class="sxs-lookup"><span data-stu-id="bdaaf-120">NOT NULL</span></span>|<span data-ttu-id="bdaaf-121">指定事件的列打开。</span><span class="sxs-lookup"><span data-stu-id="bdaaf-121">Column is turned on for the specified event.</span></span>|  
    |<span data-ttu-id="bdaaf-122">OFF (**0**)</span><span class="sxs-lookup"><span data-stu-id="bdaaf-122">OFF (**0**)</span></span>|<span data-ttu-id="bdaaf-123">Null</span><span class="sxs-lookup"><span data-stu-id="bdaaf-123">NULL</span></span>|<span data-ttu-id="bdaaf-124">事件关闭，</span><span class="sxs-lookup"><span data-stu-id="bdaaf-124">Event is turned off.</span></span> <span data-ttu-id="bdaaf-125">所有列被清除。</span><span class="sxs-lookup"><span data-stu-id="bdaaf-125">All columns are cleared.</span></span>|  
    ||<span data-ttu-id="bdaaf-126">NOT NULL</span><span class="sxs-lookup"><span data-stu-id="bdaaf-126">NOT NULL</span></span>|<span data-ttu-id="bdaaf-127">指定事件的列关闭。</span><span class="sxs-lookup"><span data-stu-id="bdaaf-127">Column is turned off for the specified event.</span></span>|  
  
> [!IMPORTANT]
>  <span data-ttu-id="bdaaf-128">与常规的存储过程不同，所有 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 存储过程 (<strong>sp_trace_xx</strong>) 参数的类型都受到严格限制，不支持自动的数据类型转换。</span><span class="sxs-lookup"><span data-stu-id="bdaaf-128">Unlike regular stored procedures, parameters of all [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] stored procedures (<strong>sp_trace_*xx*</strong>) are strictly typed and do not support automatic data type conversion.</span></span> <span data-ttu-id="bdaaf-129">如果这些参数不是使用正确的输入参数数据类型（正如参数说明中指定的一样）调用的，则存储过程会返回错误。</span><span class="sxs-lookup"><span data-stu-id="bdaaf-129">If these parameters are not called with the correct input parameter data types, as specified in the argument description, the stored procedure returns an error.</span></span>  

## <a name="see-also"></a><span data-ttu-id="bdaaf-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bdaaf-130">See Also</span></span>  
 <span data-ttu-id="bdaaf-131">[sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bdaaf-131">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 <span data-ttu-id="bdaaf-132">[sp_trace_setstatus (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bdaaf-132">[sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql) </span></span>  
 <span data-ttu-id="bdaaf-133">[系统存储过程 (Transact-SQL)](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bdaaf-133">[System Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span></span>  
 [<span data-ttu-id="bdaaf-134">SQL Server Profiler 存储过程 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="bdaaf-134">SQL Server Profiler Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
