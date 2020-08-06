---
title: 查看保存的跟踪 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], viewing
- displaying traces
- viewing traces
ms.assetid: 3a95a816-aa89-4d5f-858c-968a9cb3ee87
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f8b67760d575b651b089a6936adc945d74a1c62b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694409"
---
# <a name="view-a-saved-trace-transact-sql"></a><span data-ttu-id="ca20c-102">查看保存的跟踪 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ca20c-102">View a Saved Trace (Transact-SQL)</span></span>
  <span data-ttu-id="ca20c-103">本主题说明如何使用内置函数查看保存的跟踪。</span><span class="sxs-lookup"><span data-stu-id="ca20c-103">This topic describes how to use built-in functions to view a saved trace.</span></span>  
  
### <a name="to-view-a-specific-trace"></a><span data-ttu-id="ca20c-104">查看特定的跟踪</span><span class="sxs-lookup"><span data-stu-id="ca20c-104">To view a specific trace</span></span>  
  
1.  <span data-ttu-id="ca20c-105">通过指定需要获得其信息的跟踪的 ID 来执行 **fn_trace_getinfo** 。</span><span class="sxs-lookup"><span data-stu-id="ca20c-105">Execute **fn_trace_getinfo** by specifying the ID of the trace about which information is needed.</span></span> <span data-ttu-id="ca20c-106">此函数将返回一个表，表中列出了跟踪、跟踪属性以及有关属性的信息。</span><span class="sxs-lookup"><span data-stu-id="ca20c-106">This function returns a table that lists the trace, trace property, and information about the property.</span></span>  
  
     <span data-ttu-id="ca20c-107">请按以下方式调用此函数：</span><span class="sxs-lookup"><span data-stu-id="ca20c-107">Invoke the function this way:</span></span>  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(trace_id)  
    ```  
  
### <a name="to-view-all-existing-traces"></a><span data-ttu-id="ca20c-108">查看所有现有跟踪</span><span class="sxs-lookup"><span data-stu-id="ca20c-108">To view all existing traces</span></span>  
  
1.  <span data-ttu-id="ca20c-109">通过指定 **或** 来执行 `0` fn_trace_getinfo `default`。</span><span class="sxs-lookup"><span data-stu-id="ca20c-109">Execute **fn_trace_getinfo** by specifying `0` or `default`.</span></span> <span data-ttu-id="ca20c-110">此函数将返回一个表，表中列出了所有跟踪、跟踪属性以及有关这些属性的信息。</span><span class="sxs-lookup"><span data-stu-id="ca20c-110">This function returns a table that lists all the traces, their properties, and information about these properties.</span></span>  
  
     <span data-ttu-id="ca20c-111">请按以下方式调用此函数：</span><span class="sxs-lookup"><span data-stu-id="ca20c-111">Invoke the function as follows:</span></span>  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(default)  
    ```  
  
## <a name="net-framework-security"></a><span data-ttu-id="ca20c-112">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="ca20c-112">.NET Framework Security</span></span>  
 <span data-ttu-id="ca20c-113">若要运行内置函数 **fn_trace_getinfo**，用户需要具有以下权限：</span><span class="sxs-lookup"><span data-stu-id="ca20c-113">To run the built-in function **fn_trace_getinfo**, the user needs the following permission:</span></span>  
  
 <span data-ttu-id="ca20c-114">对服务器具有 ALTER TRACE 权限。</span><span class="sxs-lookup"><span data-stu-id="ca20c-114">ALTER TRACE on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca20c-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ca20c-115">See Also</span></span>  
 <span data-ttu-id="ca20c-116">[sys.fn_trace_getinfo (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ca20c-116">[sys.fn_trace_getinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql) </span></span>  
 [<span data-ttu-id="ca20c-117">使用 SQL Server Profiler 查看和分析跟踪</span><span class="sxs-lookup"><span data-stu-id="ca20c-117">View and Analyze Traces with SQL Server Profiler</span></span>](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md)  
  
  
