---
title: 保存跟踪和跟踪模板 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- saving traces
- traces [SQL Server], saving
- templates [SQL Server], SQL Server Profiler
- Profiler [SQL Server Profiler], templates
- trace templates [SQL Server]
- exporting trace templates
- importing trace templates
- SQL Server Profiler, templates
ms.assetid: 957e6bf8-e7a3-4a59-a1cd-0a41538a8158
author: stevestein
ms.author: sstein
ms.openlocfilehash: 36db7ccfd8b185d60eb39c20a58842f469e7878d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691433"
---
# <a name="save-traces-and-trace-templates"></a><span data-ttu-id="a824f-102">保存跟踪和跟踪模板</span><span class="sxs-lookup"><span data-stu-id="a824f-102">Save Traces and Trace Templates</span></span>
  <span data-ttu-id="a824f-103">区分保存跟踪文件和保存跟踪模板很重要。</span><span class="sxs-lookup"><span data-stu-id="a824f-103">It is important to distinguish saving trace files from saving trace templates.</span></span> <span data-ttu-id="a824f-104">保存跟踪文件是指将捕获的事件数据保存到指定位置。</span><span class="sxs-lookup"><span data-stu-id="a824f-104">Saving a trace file involves saving the captured event data to a specified place.</span></span> <span data-ttu-id="a824f-105">保存跟踪模板是指保存跟踪定义，例如指定的数据列、事件类或筛选器。</span><span class="sxs-lookup"><span data-stu-id="a824f-105">Saving a trace template involves saving the definition of the trace, such as specified data columns, event classes, or filters.</span></span>  
  
## <a name="saving-traces"></a><span data-ttu-id="a824f-106">保存跟踪</span><span class="sxs-lookup"><span data-stu-id="a824f-106">Saving Traces</span></span>  
 <span data-ttu-id="a824f-107">如果需要在以后分析或重播捕获数据，请将捕获的事件数据保存到文件或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中。</span><span class="sxs-lookup"><span data-stu-id="a824f-107">Save captured event data to a file or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table when you need to analyze or replay the captured data at a later time.</span></span> <span data-ttu-id="a824f-108">使用跟踪文件可以执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="a824f-108">Use a trace file to do the following:</span></span>  
  
-   <span data-ttu-id="a824f-109">使用跟踪文件或跟踪表可以创建工作负荷，作为数据库引擎优化顾问的输入。</span><span class="sxs-lookup"><span data-stu-id="a824f-109">Use a trace file or trace table to create a workload that is used as input for Database Engine Tuning Advisor.</span></span>  
  
-   <span data-ttu-id="a824f-110">使用跟踪文件可以捕获事件，并将跟踪文件发送给支持提供商供其分析。</span><span class="sxs-lookup"><span data-stu-id="a824f-110">Use a trace file to capture events and send the trace file to the support provider for analysis.</span></span>  
  
-   <span data-ttu-id="a824f-111">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的查询处理工具可以访问数据或在 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]中查看数据。</span><span class="sxs-lookup"><span data-stu-id="a824f-111">Use the query processing tools in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to access the data or to view the data in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="a824f-112">只有 **sysadmin** 固定服务器角色的成员或表的创建者可以直接访问跟踪表。</span><span class="sxs-lookup"><span data-stu-id="a824f-112">Only members of the **sysadmin** fixed server role or the table creator can access the trace table directly.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a824f-113">将跟踪数据捕获到表比将跟踪数据捕获到文件慢。</span><span class="sxs-lookup"><span data-stu-id="a824f-113">Capturing trace data to a table is a slower operation than capturing trace data to a file.</span></span> <span data-ttu-id="a824f-114">因此可以将跟踪数据捕获到文件，打开该跟踪文件，然后将跟踪另存为跟踪表。</span><span class="sxs-lookup"><span data-stu-id="a824f-114">An alternative is to capture trace data to a file, open the trace file, and then save the trace as a trace table.</span></span>  
  
 <span data-ttu-id="a824f-115">如果你使用跟踪文件， [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 会将捕获的事件数据（而非跟踪定义）保存到 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 跟踪文件 (\*.trc) 中。</span><span class="sxs-lookup"><span data-stu-id="a824f-115">When you use a trace file, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] saves captured event data (not trace definitions) to a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] Trace (\*.trc) file.</span></span> <span data-ttu-id="a824f-116">保存跟踪文件时自动在文件名的末尾加上该扩展名，不管是否指定任何其他扩展名。</span><span class="sxs-lookup"><span data-stu-id="a824f-116">The extension is added to the end of the file automatically when the trace file is saved, regardless of any other specified extension.</span></span> <span data-ttu-id="a824f-117">例如，如果指定一个名为 **Trace.dat**的跟踪文件，则创建的文件名为 **Trace.dat.trc**。</span><span class="sxs-lookup"><span data-stu-id="a824f-117">For example, if you specify a trace file called **Trace.dat**, the file created is called **Trace.dat.trc**.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a824f-118">拥有 SHOWPLAN、ALTER TRACE 或 VIEW SERVER STATE 权限的用户可以对显示计划输出中捕获的查询进行查看。</span><span class="sxs-lookup"><span data-stu-id="a824f-118">Users who have the SHOWPLAN, the ALTER TRACE, or the VIEW SERVER STATE permission can view queries that are captured in Showplan output.</span></span> <span data-ttu-id="a824f-119">这些查询可能包含敏感信息，例如密码。</span><span class="sxs-lookup"><span data-stu-id="a824f-119">These queries may contain sensitive information such as passwords.</span></span> <span data-ttu-id="a824f-120">因此，建议仅将这些权限授予有权查看敏感信息的一类用户，例如 **db_owner** 固定数据库角色的成员或 **sysadmin** 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="a824f-120">Therefore, we recommend that you only grant these permissions to users who are authorized to view sensitive information, such as members of the **db_owner** fixed database role, or members of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="a824f-121">此外，建议您最好将包含显示计划相关事件的显示计划文件或跟踪文件保存到使用 NTFS 文件系统的某个位置，并且只允许有权查看敏感信息的用户对之进行访问。</span><span class="sxs-lookup"><span data-stu-id="a824f-121">Additionally, we recommend that you only save Showplan files or trace files that contain Showplan-related events to a location that uses the NTFS file system, and that you restrict access to users who are authorized to view sensitive information.</span></span>  
  
## <a name="saving-templates"></a><span data-ttu-id="a824f-122">保存模板</span><span class="sxs-lookup"><span data-stu-id="a824f-122">Saving Templates</span></span>  
 <span data-ttu-id="a824f-123">跟踪的模板定义包括事件类、数据列、筛选器和用于创建跟踪的所有其他属性（捕获的事件数据除外）。</span><span class="sxs-lookup"><span data-stu-id="a824f-123">The template definition of a trace includes the event classes, data columns, filters, and all other properties (except the captured event data) that are used to create a trace.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="a824f-124">提供针对常见跟踪任务和特定任务的预定义系统模板，如创建可供数据库引擎优化顾问用来优化物理数据库设计的工作负荷。</span><span class="sxs-lookup"><span data-stu-id="a824f-124">provides predefined system templates for common tracing tasks and for specific tasks, such as creating a workload that Database Engine Tuning Advisor can use to tune the physical database design.</span></span> <span data-ttu-id="a824f-125">还可以创建和保存用户定义模板。</span><span class="sxs-lookup"><span data-stu-id="a824f-125">You can also create and save user-defined templates.</span></span>  
  
### <a name="importing-and-exporting-templates"></a><span data-ttu-id="a824f-126">导入和导出模板</span><span class="sxs-lookup"><span data-stu-id="a824f-126">Importing and Exporting Templates</span></span>  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="a824f-127">允许在服务器之间导入和导出模板。</span><span class="sxs-lookup"><span data-stu-id="a824f-127">allows you to import and export templates from one server to another.</span></span> <span data-ttu-id="a824f-128">导出模板会将现有模板的副本移到指定目录。</span><span class="sxs-lookup"><span data-stu-id="a824f-128">Exporting a template moves a copy of an existing template to a directory that you specify.</span></span> <span data-ttu-id="a824f-129">导入模板会复制指定的模板。</span><span class="sxs-lookup"><span data-stu-id="a824f-129">Importing a template makes a copy of a template that you specify.</span></span> <span data-ttu-id="a824f-130">在 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]中查看这些模板时，可以通过模板名称后的“(user)”使它们区别于系统模板。</span><span class="sxs-lookup"><span data-stu-id="a824f-130">When these templates are viewed in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can distinguish them from system templates by the term "(user)" that follows the template name.</span></span> <span data-ttu-id="a824f-131">您无法覆盖或直接修改预定义系统模板。</span><span class="sxs-lookup"><span data-stu-id="a824f-131">You cannot overwrite or directly modify a predefined system template.</span></span>  
  
### <a name="analyzing-performance-with-templates"></a><span data-ttu-id="a824f-132">使用模板分析性能</span><span class="sxs-lookup"><span data-stu-id="a824f-132">Analyzing Performance with Templates</span></span>  
 <span data-ttu-id="a824f-133">如果您经常监视 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，请使用模板分析性能。</span><span class="sxs-lookup"><span data-stu-id="a824f-133">If you frequently monitor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], use templates to analyze performance.</span></span> <span data-ttu-id="a824f-134">模板每次都捕获相同的事件数据，并使用同一跟踪定义监视相同的事件。</span><span class="sxs-lookup"><span data-stu-id="a824f-134">The templates capture the same event data each time and use the same trace definition to monitor the same events.</span></span> <span data-ttu-id="a824f-135">您不需要在每次创建跟踪时都定义事件类和数据列。</span><span class="sxs-lookup"><span data-stu-id="a824f-135">You do not need to define the event classes and data columns every time you create a trace.</span></span> <span data-ttu-id="a824f-136">此外，可以将模板提供给其他用户，供其监视特定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 事件。</span><span class="sxs-lookup"><span data-stu-id="a824f-136">Also, a template can be given to another user to monitor specific [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events.</span></span> <span data-ttu-id="a824f-137">例如，支持提供商可以向客户提供一个模板。</span><span class="sxs-lookup"><span data-stu-id="a824f-137">For example, a support provider can supply a customer with a template.</span></span> <span data-ttu-id="a824f-138">客户使用该模板捕获所需的事件数据，然后将数据发送给支持提供商供其分析。</span><span class="sxs-lookup"><span data-stu-id="a824f-138">The customer uses the template to capture the required event data, which is then sent to the support provider for analysis.</span></span>  
  
 <span data-ttu-id="a824f-139">**将跟踪保存到文件**</span><span class="sxs-lookup"><span data-stu-id="a824f-139">**To save a trace to a file**</span></span>  
  
 [<span data-ttu-id="a824f-140">将跟踪结果保存到文件 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="a824f-140">Save Trace Results to a File &#40;SQL Server Profiler&#41;</span></span>](save-trace-results-to-a-file-sql-server-profiler.md)  
  
 [<span data-ttu-id="a824f-141">sp_trace_create (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a824f-141">sp_trace_create &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="a824f-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a824f-142">See Also</span></span>  
 <span data-ttu-id="a824f-143">[将跟踪结果保存到表 (SQL Server Profiler)](save-trace-results-to-a-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="a824f-143">[Save Trace Results to a Table &#40;SQL Server Profiler&#41;](save-trace-results-to-a-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="a824f-144">[创建跟踪模板 (SQL Server Profiler)](create-a-trace-template-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="a824f-144">[Create a Trace Template &#40;SQL Server Profiler&#41;](create-a-trace-template-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="a824f-145">[从正在运行的跟踪中派生模板 (SQL Server Profiler)](derive-a-template-from-a-running-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="a824f-145">[Derive a Template from a Running Trace &#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="a824f-146">[从跟踪文件或跟踪表派生模板 (SQL Server Profiler)](derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="a824f-146">[Derive a Template from a Trace File or Trace Table &#40;SQL Server Profiler&#41;](derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="a824f-147">[导出跟踪模板 (SQL Server Profiler)](export-a-trace-template-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="a824f-147">[Export a Trace Template &#40;SQL Server Profiler&#41;](export-a-trace-template-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="a824f-148">导入跟踪模板 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="a824f-148">Import a Trace Template &#40;SQL Server Profiler&#41;</span></span>](import-a-trace-template-sql-server-profiler.md)  
  
  
