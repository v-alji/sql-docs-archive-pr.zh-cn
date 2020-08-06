---
title: 跟踪和重播事件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- replaying events
- traces [SMO]
- events [SMO], replaying
- events [SMO], tracing
ms.assetid: f41b3f85-2f6c-4c3e-9776-8c73d2cc7a53
author: stevestein
ms.author: sstein
ms.openlocfilehash: f7f0d570c70ef1cba080217e6c3a0f9b6055a4d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689822"
---
# <a name="tracing-and-replaying-events"></a><span data-ttu-id="1f323-102">跟踪和重播事件</span><span class="sxs-lookup"><span data-stu-id="1f323-102">Tracing and Replaying Events</span></span>
  <span data-ttu-id="1f323-103">在 SMO 中，`Trace` 命名空间中的 `Replay` 和 <xref:Microsoft.SqlServer.Management.Trace> 对象提供对 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] 功能（用于监视 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 的实例）的编程访问。</span><span class="sxs-lookup"><span data-stu-id="1f323-103">In SMO, the `Trace` and `Replay` objects in the <xref:Microsoft.SqlServer.Management.Trace> namespace provide programmatic access to the [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] functionality, which is used for monitoring an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="1f323-104">您可以捕获有关每个事件的数据并将其保存到文件或表中供以后分析。</span><span class="sxs-lookup"><span data-stu-id="1f323-104">You can capture and save data about each event to a file or table to analyze later.</span></span> <span data-ttu-id="1f323-105">例如，可以监视生产环境，了解哪些过程由于执行速度太慢影响了性能。</span><span class="sxs-lookup"><span data-stu-id="1f323-105">For example, you can monitor a production environment to see which procedures are impeding performance by executing too slowly.</span></span>  
  
 <span data-ttu-id="1f323-106"> 和  对象提供一组对象，可用于针对  的实例创建跟踪。</span><span class="sxs-lookup"><span data-stu-id="1f323-106">The `Trace` and `Replay` objects provide a set of objects that can be used to create traces on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1f323-107">可以在您自己的应用程序中使用这些对象为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 手动创建跟踪。</span><span class="sxs-lookup"><span data-stu-id="1f323-107">These objects can be used from within your own applications to create traces manually for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="1f323-108">此外，可以使用 SMO `Trace` 对象读取 SQL 跟踪文件和表，这些文件和表是通过监视 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 或 DTS 日志记录而创建的。</span><span class="sxs-lookup"><span data-stu-id="1f323-108">Additionally, SMO `Trace` objects can be used to read SQL Trace files and tables that were created by monitoring [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], or DTS logging.</span></span>  
  
 <span data-ttu-id="1f323-109">SMO `Trace` 对象支持您执行以下功能：</span><span class="sxs-lookup"><span data-stu-id="1f323-109">SMO `Trace` objects let you perform the following functions:</span></span>  
  
-   <span data-ttu-id="1f323-110">创建跟踪。</span><span class="sxs-lookup"><span data-stu-id="1f323-110">Create a trace.</span></span>  
  
-   <span data-ttu-id="1f323-111">设置跟踪筛选器。</span><span class="sxs-lookup"><span data-stu-id="1f323-111">Set filters on the trace.</span></span>  
  
-   <span data-ttu-id="1f323-112">设置正在跟踪的事件。</span><span class="sxs-lookup"><span data-stu-id="1f323-112">Set the events that are being traced.</span></span>  
  
-   <span data-ttu-id="1f323-113">停止或启动跟踪。</span><span class="sxs-lookup"><span data-stu-id="1f323-113">Stop or start a trace.</span></span>  
  
-   <span data-ttu-id="1f323-114">读取跟踪文件和跟踪表。</span><span class="sxs-lookup"><span data-stu-id="1f323-114">Read trace files, and trace tables.</span></span>  
  
-   <span data-ttu-id="1f323-115">获取有关跟踪中的事件的信息。</span><span class="sxs-lookup"><span data-stu-id="1f323-115">Get information about events on a trace.</span></span>  
  
-   <span data-ttu-id="1f323-116">获取有关跟踪中的筛选器的信息。</span><span class="sxs-lookup"><span data-stu-id="1f323-116">Get information about filters on a trace.</span></span>  
  
-   <span data-ttu-id="1f323-117">以编程方式操作跟踪数据。</span><span class="sxs-lookup"><span data-stu-id="1f323-117">Manipulate trace data programmatically.</span></span>  
  
-   <span data-ttu-id="1f323-118">写入跟踪表和跟踪文件。</span><span class="sxs-lookup"><span data-stu-id="1f323-118">Write trace tables and trace files.</span></span>  
  
-   <span data-ttu-id="1f323-119">重播跟踪文件或跟踪表。</span><span class="sxs-lookup"><span data-stu-id="1f323-119">Replay trace files or trace tables.</span></span>  
  
 <span data-ttu-id="1f323-120">`Trace` `Replay` SMO 应用程序可以使用和对象中的跟踪数据，也可以使用[SQL Server Profiler](../../../tools/sql-server-profiler/sql-server-profiler.md)手动对其进行检查。</span><span class="sxs-lookup"><span data-stu-id="1f323-120">The trace data from the `Trace` and `Replay` objects can be used by the SMO application, or it can be examined manually by using [SQL Server Profiler](../../../tools/sql-server-profiler/sql-server-profiler.md).</span></span> <span data-ttu-id="1f323-121">跟踪数据还与同时提供跟踪功能的[SQL 跟踪](../../sql-trace/sql-trace.md)存储过程兼容。</span><span class="sxs-lookup"><span data-stu-id="1f323-121">The trace data is also compatible with the [SQL Trace](../../sql-trace/sql-trace.md) stored procedures that also provide tracing capabilities.</span></span>  
  
 <span data-ttu-id="1f323-122">SMO 跟踪对象驻留在 <xref:Microsoft.SqlServer.Management.Trace> 命名空间中，该命名空间要求引用 Microsoft.SQLServer.ConnectionInfo.dll 文件。</span><span class="sxs-lookup"><span data-stu-id="1f323-122">The SMO trace objects reside in the <xref:Microsoft.SqlServer.Management.Trace> namespace, which requires a reference to the Microsoft.SQLServer.ConnectionInfo.dll file.</span></span>  
  
 <span data-ttu-id="1f323-123">`Trace` 和 `Replay` 对象需要通过 <xref:Microsoft.SqlServer.Management.Common.ServerConnection><xref:Microsoft.SqlServer.Management.Smo.Server.%23ctor%2A> 对象建立与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的实例的连接。</span><span class="sxs-lookup"><span data-stu-id="1f323-123">The `Trace` and `Replay` objects require a <xref:Microsoft.SqlServer.Management.Common.ServerConnection><xref:Microsoft.SqlServer.Management.Smo.Server.%23ctor%2A> object to establish a connection with the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1f323-124"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象驻留在 <xref:Microsoft.SqlServer.Management.Common> 命名空间中，该命名空间要求引用 Microsoft.SQLServer.ConnectionInfo.dll 文件。</span><span class="sxs-lookup"><span data-stu-id="1f323-124">The <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object resides in the <xref:Microsoft.SqlServer.Management.Common> namespace, which requires a reference to the Microsoft.SQLServer.ConnectionInfo.dll file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1f323-125">64 位平台不支持 `Trace` 和 `Replay` 对象。</span><span class="sxs-lookup"><span data-stu-id="1f323-125">The `Trace` and `Replay` objects are not supported on a 64-bit platform.</span></span>  
  
  
