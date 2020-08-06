---
title: 创建 Transact-SQL 脚本来运行跟踪 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], running
- scripts [SQL Server], traces
ms.assetid: 6b0e2519-998d-40d5-b8ba-5e6a773f91a6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3d4b4bebb2a3e05e3de12e59c53ccca9c980afd5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682498"
---
# <a name="create-a-transact-sql-script-for-running-a-trace-sql-server-profiler"></a><span data-ttu-id="fc805-102">创建 Transact-SQL 脚本来运行跟踪 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="fc805-102">Create a Transact-SQL Script for Running a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="fc805-103">本主题说明了如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]从现有的跟踪文件或表中创建 Transact-SQL 脚本。</span><span class="sxs-lookup"><span data-stu-id="fc805-103">This topic describes how to create a Transact-SQL script from an existing trace file or table by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-create-a-transact-sql-script-to-run-a-trace"></a><span data-ttu-id="fc805-104">创建 Transact-SQL 脚本来运行跟踪</span><span class="sxs-lookup"><span data-stu-id="fc805-104">To create a Transact-SQL script to run a trace</span></span>  
  
1.  <span data-ttu-id="fc805-105">打开跟踪文件或表。</span><span class="sxs-lookup"><span data-stu-id="fc805-105">Open a trace file or table.</span></span> <span data-ttu-id="fc805-106">有关详细信息，请参阅 [打开跟踪文件 (SQL Server Profiler)](open-a-trace-file-sql-server-profiler.md) 或 [打开跟踪表 (SQL Server Profiler)](open-a-trace-table-sql-server-profiler.md)一起提供的预定义优化模板。</span><span class="sxs-lookup"><span data-stu-id="fc805-106">For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).</span></span>  
  
2.  <span data-ttu-id="fc805-107">在“文件”  菜单上，依次指向“导出”  和“脚本跟踪定义”  ，然后单击与你要跟踪的服务器对应的版本。</span><span class="sxs-lookup"><span data-stu-id="fc805-107">On the**File**menu, point to **Export**, point to **Script Trace Definition**, and then click the version that corresponds to the server you want to trace.</span></span>  
  
3.  <span data-ttu-id="fc805-108">在 **“另存为”** 对话框中，输入脚本文件名称，然后单击 **“保存”** 。</span><span class="sxs-lookup"><span data-stu-id="fc805-108">In the **Save As** dialog box, enter a name for the script file, and then click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc805-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fc805-109">See Also</span></span>  
 <span data-ttu-id="fc805-110">[SQL Server Profiler 模板和权限](sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="fc805-110">[SQL Server Profiler Templates and Permissions](sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="fc805-111">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="fc805-111">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
