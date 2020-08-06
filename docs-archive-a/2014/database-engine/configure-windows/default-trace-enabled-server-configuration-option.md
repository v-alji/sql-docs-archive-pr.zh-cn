---
title: default trace enabled 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], traces
- traces [SQL Server], logs
- default trace enabled option
ms.assetid: 1322d668-44f4-469e-8fd6-e0d02a81c8f2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8d40305de7375f2ae10d563871fd40b7acfa463f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693086"
---
# <a name="default-trace-enabled-server-configuration-option"></a><span data-ttu-id="d134a-102">default trace enabled 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="d134a-102">default trace enabled Server Configuration Option</span></span>
  <span data-ttu-id="d134a-103">使用 **default trace enabled** 选项可启用或禁用默认跟踪日志文件。</span><span class="sxs-lookup"><span data-stu-id="d134a-103">Use the **default trace enabled** option to enable or disable the default trace log files.</span></span> <span data-ttu-id="d134a-104">默认跟踪功能提供了丰富持久的活动日志，并主要根据配置选项进行更改。</span><span class="sxs-lookup"><span data-stu-id="d134a-104">The default trace functionality provides a rich, persistent log of activity and changes primarily related to the configuration options.</span></span>  
  
> [!WARNING]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] <span data-ttu-id="d134a-105">请改用扩展事件。</span><span class="sxs-lookup"><span data-stu-id="d134a-105">Use Extended Events instead.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="d134a-106">目的</span><span class="sxs-lookup"><span data-stu-id="d134a-106">Purpose</span></span>  
 <span data-ttu-id="d134a-107">默认跟踪可确保数据库管理员在问题首次出现时即具有诊断该问题所需的日志数据，从而为数据库管理员提供了故障排除帮助。</span><span class="sxs-lookup"><span data-stu-id="d134a-107">Default trace provides troubleshooting assistance to database administrators by ensuring that they have the log data necessary to diagnose problems the first time they occur.</span></span>  
  
## <a name="viewing"></a><span data-ttu-id="d134a-108">查看</span><span class="sxs-lookup"><span data-stu-id="d134a-108">Viewing</span></span>  
 <span data-ttu-id="d134a-109">默认跟踪日志可以通过 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 打开和检查，或者通过 [!INCLUDE[tsql](../../includes/tsql-md.md)] 使用 `fn_trace_gettable` 系统函数来查询。</span><span class="sxs-lookup"><span data-stu-id="d134a-109">The default trace logs can be opened and examined by [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or queried with [!INCLUDE[tsql](../../includes/tsql-md.md)] by using the `fn_trace_gettable` system function.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="d134a-110">可以像打开正常跟踪输出文件一样打开默认跟踪日志文件。</span><span class="sxs-lookup"><span data-stu-id="d134a-110">can open the default trace log files just as it does normal trace output files.</span></span> <span data-ttu-id="d134a-111">默认情况下，默认跟踪日志以滚动更新跟踪文件的形式存储在 `\MSSQL\LOG` 目录中。</span><span class="sxs-lookup"><span data-stu-id="d134a-111">The default trace log is stored by default in the `\MSSQL\LOG` directory using a rollover trace file.</span></span> <span data-ttu-id="d134a-112">默认跟踪日志文件的基本文件名是 `log.trc`。</span><span class="sxs-lookup"><span data-stu-id="d134a-112">The base file name for the default trace log file is `log.trc`.</span></span> <span data-ttu-id="d134a-113">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的典型安装中，默认跟踪启用并因而成为 TraceID 1。</span><span class="sxs-lookup"><span data-stu-id="d134a-113">In a typical installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the default trace is enabled and thus becomes TraceID 1.</span></span> <span data-ttu-id="d134a-114">如果在安装和创建其他跟踪后启用，该 TraceID 可以变成更大的数字。</span><span class="sxs-lookup"><span data-stu-id="d134a-114">If enabled after installation and after creating other traces, the TraceID can become a larger number.</span></span>  
  
 <span data-ttu-id="d134a-115">有关使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 事件探查器查看此跟踪文件的详细信息，请参阅[打开跟踪文件 (SQL Server Profiler)](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="d134a-115">For more information about using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler to view this trace file, see [Open a Trace File &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)</span></span>  
  
### <a name="example"></a><span data-ttu-id="d134a-116">示例：</span><span class="sxs-lookup"><span data-stu-id="d134a-116">Example:</span></span>  
 <span data-ttu-id="d134a-117">以下语句将打开默认位置中的默认跟踪日志：</span><span class="sxs-lookup"><span data-stu-id="d134a-117">The following statement opens the default trace log in the default location:</span></span>  
  
```  
SELECT *   
FROM fn_trace_gettable  
('C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\LOG\log.trc', default);  
GO  
  
```  
  
## <a name="configuring"></a><span data-ttu-id="d134a-118">配置</span><span class="sxs-lookup"><span data-stu-id="d134a-118">Configuring</span></span>  
 <span data-ttu-id="d134a-119">如果将 **default trace enabled** 选项设置为 1，可启用“默认跟踪” 。</span><span class="sxs-lookup"><span data-stu-id="d134a-119">When set to 1, the **default trace enabled** option enables **Default Trace**.</span></span> <span data-ttu-id="d134a-120">此选项的默认设置为 1 (ON)。</span><span class="sxs-lookup"><span data-stu-id="d134a-120">The default setting for this option is 1 (ON).</span></span> <span data-ttu-id="d134a-121">值为 0 时将关闭跟踪。</span><span class="sxs-lookup"><span data-stu-id="d134a-121">A value of 0 turns off the trace.</span></span>  
  
 <span data-ttu-id="d134a-122">**default trace enabled** 选项是一个高级选项。</span><span class="sxs-lookup"><span data-stu-id="d134a-122">The **default trace enabled** option is an advanced option.</span></span> <span data-ttu-id="d134a-123">如果使用 **sp_configure** 系统存储过程来更改该设置，则仅当 **show advanced options** 设置为 1 时才能更改 **default trace enabled** 选项。</span><span class="sxs-lookup"><span data-stu-id="d134a-123">If you are using the **sp_configure** system stored procedure to change the setting, you can change the **default trace enabled** option only when **show advanced options** is set to 1.</span></span> <span data-ttu-id="d134a-124">该设置将立即生效，无需重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="d134a-124">The setting takes effect immediately without a server restart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d134a-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d134a-125">See Also</span></span>  
 <span data-ttu-id="d134a-126">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d134a-126">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="d134a-127">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d134a-127">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="d134a-128">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d134a-128">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
