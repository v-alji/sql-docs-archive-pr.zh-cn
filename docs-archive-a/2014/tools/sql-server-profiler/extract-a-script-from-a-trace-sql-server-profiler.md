---
title: 从跟踪提取脚本 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], traces
- extracting script from trace [SQL Server]
ms.assetid: 431126a6-ff91-4818-8763-4442152bd571
author: stevestein
ms.author: sstein
ms.openlocfilehash: f6633fafb8a39b189093044ef39694afa601af7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682493"
---
# <a name="extract-a-script-from-a-trace-sql-server-profiler"></a><span data-ttu-id="5346c-102">从跟踪提取脚本 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="5346c-102">Extract a Script from a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="5346c-103">本主题说明如何使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 从跟踪文件或表提取 [!INCLUDE[tsql](../../includes/tsql-md.md)] 事件并将它们保存为 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]脚本文件。</span><span class="sxs-lookup"><span data-stu-id="5346c-103">This topic describes how to extract [!INCLUDE[tsql](../../includes/tsql-md.md)] events from a trace file or table and save them as a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-extract-a-transact-sql-script-from-a-trace-file-or-table"></a><span data-ttu-id="5346c-104">从跟踪文件或表提取 Transact-SQL 脚本</span><span class="sxs-lookup"><span data-stu-id="5346c-104">To extract a Transact-SQL script from a trace file or table</span></span>  
  
1.  <span data-ttu-id="5346c-105">打开一个包含要将其保存到 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本文件的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 事件的跟踪文件或表。</span><span class="sxs-lookup"><span data-stu-id="5346c-105">Open a trace file or table that contains [!INCLUDE[tsql](../../includes/tsql-md.md)] events that you want to save to a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file.</span></span> <span data-ttu-id="5346c-106">有关详细信息，请参阅 [打开跟踪文件 (SQL Server Profiler)](open-a-trace-file-sql-server-profiler.md) 或 [打开跟踪表 (SQL Server Profiler)](open-a-trace-table-sql-server-profiler.md)一起提供的预定义优化模板。</span><span class="sxs-lookup"><span data-stu-id="5346c-106">For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).</span></span>  
  
2.  <span data-ttu-id="5346c-107">在  “文件”菜单上，指向  “导出”，再指向  “提取 SQL Server 事件”，然后单击  “提取 Transact-SQL 事件”。</span><span class="sxs-lookup"><span data-stu-id="5346c-107">On the **File** menu, point to **Export**, point to **Extract SQL Server Events**, and then click **Extract Transact-SQL Events**.</span></span>  
  
3.  <span data-ttu-id="5346c-108">在 **“另存为”** 对话框中，键入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 文件的名称，然后单击 **“保存”** 。</span><span class="sxs-lookup"><span data-stu-id="5346c-108">In the **Save As** dialog box, type a name for the [!INCLUDE[tsql](../../includes/tsql-md.md)] file, and click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5346c-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5346c-109">See Also</span></span>  
 [<span data-ttu-id="5346c-110">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="5346c-110">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
