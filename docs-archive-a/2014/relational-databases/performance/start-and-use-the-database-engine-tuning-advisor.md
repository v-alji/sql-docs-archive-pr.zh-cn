---
title: 启动并使用数据库引擎优化顾问 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.dta.advancedtuningoptions.f1
- sql12.dta.general.f1
- sql12.dta.tuningoptions.f1
- sql12.dta.workload.f1
- sql12.dta.progress.f1
- sql12.dta.options.f1
helpviewer_keywords:
- Database Engine Tuning Advisor [SQL Server], starting
ms.assetid: a4e3226a-3917-4ec8-bdf0-472879d231c9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 46f8e49de657d7021d846c7e57022a580b877f8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689876"
---
# <a name="start-and-use-the-database-engine-tuning-advisor"></a><span data-ttu-id="782e0-102">启动并使用数据库引擎优化顾问</span><span class="sxs-lookup"><span data-stu-id="782e0-102">Start and Use the Database Engine Tuning Advisor</span></span>
  <span data-ttu-id="782e0-103">本主题介绍如何在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中启动和使用数据库引擎优化顾问。</span><span class="sxs-lookup"><span data-stu-id="782e0-103">This topic describes how to start and use Database Engine Tuning Advisor in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="782e0-104">有关如何查看和使用数据库优化结果，请参阅 [查看和使用数据库引擎优化顾问的输出](database-engine-tuning-advisor.md)。</span><span class="sxs-lookup"><span data-stu-id="782e0-104">For information about how to view and work with the results after you tune a database, see [View and Work with the Output from the Database Engine Tuning Advisor](database-engine-tuning-advisor.md).</span></span>  
  
##  <a name="initialize-the-database-engine-tuning-advisor"></a><a name="Initialize"></a> <span data-ttu-id="782e0-105">初始化数据库引擎优化顾问</span><span class="sxs-lookup"><span data-stu-id="782e0-105">Initialize the Database Engine Tuning Advisor</span></span>  
 <span data-ttu-id="782e0-106">第一次使用时，作为 **sysadmin** 固定服务器角色成员的用户必须初始化数据库引擎优化顾问。</span><span class="sxs-lookup"><span data-stu-id="782e0-106">On first use, a user who is member of the **sysadmin** fixed server role must initialize the Database Engine Tuning Advisor.</span></span> <span data-ttu-id="782e0-107">这是因为必须在 `msdb` 数据库中创建多个系统表才能支持优化操作。</span><span class="sxs-lookup"><span data-stu-id="782e0-107">This is because several system tables must be created in the `msdb` database to support tuning operations.</span></span> <span data-ttu-id="782e0-108">如果用户是 **db_owner** 固定数据库角色的成员，初始化还可以使他们能够优化数据库（他们拥有的数据库）中的表的工作负荷。</span><span class="sxs-lookup"><span data-stu-id="782e0-108">Initialization also enables users that are members of the **db_owner** fixed database role to tune workloads on tables in databases that they own.</span></span>  
  
 <span data-ttu-id="782e0-109">具有系统管理员权限的用户必须执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="782e0-109">A user that has system administrator permissions must perform either of the following actions:</span></span>  
  
-   <span data-ttu-id="782e0-110">使用数据库引擎优化顾问图形用户界面连接到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="782e0-110">Use the Database Engine Tuning Advisor graphical user interface to connect to an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="782e0-111">有关详细信息，请参阅本主题后面的 [启动数据库引擎优化顾问](#Start) 。</span><span class="sxs-lookup"><span data-stu-id="782e0-111">For more information, see [Start the Database Engine Tuning Advisor](#Start) later in this topic.</span></span>  
  
-   <span data-ttu-id="782e0-112">使用 **dta** 实用工具优化第一个工作负荷。</span><span class="sxs-lookup"><span data-stu-id="782e0-112">Use the **dta** utility to tune the first workload.</span></span> <span data-ttu-id="782e0-113">有关详细信息，请参阅本主题后面的 [使用 dta 实用工具](#dta) 。</span><span class="sxs-lookup"><span data-stu-id="782e0-113">For more information, see [Use the dta Utility](#dta) later in this topic.</span></span>  
  
##  <a name="start-the-database-engine-tuning-advisor"></a><a name="Start"></a> <span data-ttu-id="782e0-114">启动数据库引擎优化顾问</span><span class="sxs-lookup"><span data-stu-id="782e0-114">Start the Database Engine Tuning Advisor</span></span>  
 <span data-ttu-id="782e0-115">可以用几种不同的方式启动数据库引擎优化顾问图形用户界面 (GUI)，以支持不同情况下的数据库优化。</span><span class="sxs-lookup"><span data-stu-id="782e0-115">You can start the Database Engine Tuning Advisor graphical user interface (GUI) in several different ways to support database tuning in a variety of scenarios.</span></span> <span data-ttu-id="782e0-116">启动数据库引擎优化顾问的其他方式包括：通过 **“开始”** 菜单启动，通过 **中的** “工具” [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]菜单启动，通过 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的查询编辑器启动，以及通过 **中的** “工具” [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]菜单启动。</span><span class="sxs-lookup"><span data-stu-id="782e0-116">The different ways to start Database Engine Tuning Advisor include: from the **Start** menu, from the **Tools** menu in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], from the Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and from the **Tools** menu in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="782e0-117">第一次启动数据库引擎优化顾问时，该应用程序将显示一个 **“连接到服务器”** 对话框，您可以在该对话框中指定要连接的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="782e0-117">When you first start Database Engine Tuning Advisor, the application displays a **Connect to Server** dialog box where you can specify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to which you want to connect.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="782e0-118">当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以单用户模式运行时，不要启动数据库引擎优化顾问。</span><span class="sxs-lookup"><span data-stu-id="782e0-118">Do not start Database Engine Tuning Advisor when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running in single-user mode.</span></span> <span data-ttu-id="782e0-119">如果试图在服务器处于单用户模式时启动该服务器，将返回错误，并且不会启动数据库引擎优化顾问。</span><span class="sxs-lookup"><span data-stu-id="782e0-119">If you attempt to start it while the server is in single-user mode, an error will be returned and Database Engine Tuning Advisor will not start.</span></span> <span data-ttu-id="782e0-120">有关单用户模式的详细信息，请参阅 [在单用户模式下启动 SQL Server](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="782e0-120">For more information about single-user mode, see [Start SQL Server in Single-User Mode](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md).</span></span>  
  
#### <a name="to-start-database-engine-tuning-advisor-from-the-windows-start-menu"></a><span data-ttu-id="782e0-121">通过 Windows“开始”菜单启动数据库引擎优化顾问</span><span class="sxs-lookup"><span data-stu-id="782e0-121">To start Database Engine Tuning Advisor from the Windows Start menu</span></span>  
  
1.  <span data-ttu-id="782e0-122">在 **“开始”** 菜单中，依次指向 **“所有程序”** 、 **“Microsoft SQL Server”** 和 **“性能工具”** ，然后单击 **“数据库引擎优化顾问”** 。</span><span class="sxs-lookup"><span data-stu-id="782e0-122">On the **Start** menu, point to **All Programs**, point to **Microsoft SQL Server**, point to **Performance Tools**, and then click **Database Engine Tuning Advisor**.</span></span>  
  
#### <a name="to-start-the-database-engine-tuning-advisor-in-sql-server-management-studio"></a><span data-ttu-id="782e0-123">在 SQL Server Management Studio 中启动数据库引擎优化顾问</span><span class="sxs-lookup"><span data-stu-id="782e0-123">To start the Database Engine Tuning Advisor in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="782e0-124">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的“工具”菜单中，单击“数据库引擎优化顾问” 。</span><span class="sxs-lookup"><span data-stu-id="782e0-124">On the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Tools** menu, click **Database Engine Tuning Advisor**.</span></span>  
  
#### <a name="to-start-the-database-engine-tuning-advisor-from-the-sql-server-management-studio-query-editor"></a><span data-ttu-id="782e0-125">在 SQL Server Management Studio 查询编辑器中启动数据库引擎优化顾问</span><span class="sxs-lookup"><span data-stu-id="782e0-125">To start the Database Engine Tuning Advisor from the SQL Server Management Studio Query Editor</span></span>  
  
1.  <span data-ttu-id="782e0-126">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中打开 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]脚本文件。</span><span class="sxs-lookup"><span data-stu-id="782e0-126">Open a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="782e0-127">有关详细信息，请参阅[查询和文本编辑器 (SQL Server Management Studio)](../scripting/query-and-text-editors-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="782e0-127">For more information, see [Query and Text Editors &#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md).</span></span>  
  
2.  <span data-ttu-id="782e0-128">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本中选择一个查询，或选择整个脚本，右键单击选定的内容，再选择“在数据库引擎优化顾问中分析查询”。</span><span class="sxs-lookup"><span data-stu-id="782e0-128">Select a query in the [!INCLUDE[tsql](../../includes/tsql-md.md)] script, or select the entire script, right-click the selection, and choose **Analyze Query in Database Engine Tuning Advisor**.</span></span> <span data-ttu-id="782e0-129">此时将打开数据库引擎优化顾问图形用户界面，并将该脚本作为 XML 文件工作负荷导入。</span><span class="sxs-lookup"><span data-stu-id="782e0-129">The Database Engine Tuning Advisor GUI opens and imports the script as an XML file workload.</span></span> <span data-ttu-id="782e0-130">可以指定会话名称和优化选项，以将选定的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询作为工作负荷进行优化。</span><span class="sxs-lookup"><span data-stu-id="782e0-130">You can specify a session name and tuning options to tune the selected [!INCLUDE[tsql](../../includes/tsql-md.md)] queries as your workload.</span></span>  
  
#### <a name="to-start-the-database-engine-tuning-advisor-in-sql-server-profiler"></a><span data-ttu-id="782e0-131">在 SQL Server Profiler 中启动数据库引擎优化顾问</span><span class="sxs-lookup"><span data-stu-id="782e0-131">To start the Database Engine Tuning Advisor in SQL Server Profiler</span></span>  
  
1.  <span data-ttu-id="782e0-132">在 SQL Server Profiler 的 **“工具”** 菜单中，单击 **“数据库引擎优化顾问”** 。</span><span class="sxs-lookup"><span data-stu-id="782e0-132">On the SQL Server Profiler **Tools** menu, click **Database Engine Tuning Advisor**.</span></span>  
  
##  <a name="create-a-workload"></a><a name="Create"></a> <span data-ttu-id="782e0-133">创建工作负荷</span><span class="sxs-lookup"><span data-stu-id="782e0-133">Create a Workload</span></span>  
 <span data-ttu-id="782e0-134">工作负荷是对要优化的一个或多个数据库执行的一组 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="782e0-134">A workload is a set of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that execute against a database or databases that you want to tune.</span></span> <span data-ttu-id="782e0-135">数据库引擎优化顾问将分析这些工作负荷以便建议要使用的索引或分区策略来改善服务器的查询性能。</span><span class="sxs-lookup"><span data-stu-id="782e0-135">Database Engine Tuning Advisor analyzes these workloads to recommend indexes or partitioning strategies that will improve your server's query performance.</span></span>  
  
 <span data-ttu-id="782e0-136">您可以通过使用以下方法之一创建工作负荷。</span><span class="sxs-lookup"><span data-stu-id="782e0-136">You can create a workload by using one of the following methods.</span></span>  
  
-   <span data-ttu-id="782e0-137">将计划缓存用作工作负荷。</span><span class="sxs-lookup"><span data-stu-id="782e0-137">Use the plan cache as a workload.</span></span> <span data-ttu-id="782e0-138">这样，可以避免手动创建工作负荷。</span><span class="sxs-lookup"><span data-stu-id="782e0-138">By doing this, you can avoid having to manually create a workload.</span></span> <span data-ttu-id="782e0-139">有关详细信息，请参阅本主题后面的 [优化数据库](#Tune) 。</span><span class="sxs-lookup"><span data-stu-id="782e0-139">For more information, see [Tune a Database](#Tune) later in this topic.</span></span>  
  
-   <span data-ttu-id="782e0-140">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的查询编辑器或您最喜欢的文本编辑器来手动创建 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本工作负荷。</span><span class="sxs-lookup"><span data-stu-id="782e0-140">Use the Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or your favorite text editor to manually create [!INCLUDE[tsql](../../includes/tsql-md.md)] script workloads.</span></span>  
  
-   <span data-ttu-id="782e0-141">使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 创建跟踪文件或跟踪表工作负荷</span><span class="sxs-lookup"><span data-stu-id="782e0-141">Use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to create trace file or trace table workloads</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="782e0-142">使用跟踪表作为工作负荷时，该表必须位于数据库引擎优化顾问正在优化的那台服务器上。</span><span class="sxs-lookup"><span data-stu-id="782e0-142">When using a trace table as a workload, that table must exist on the same server where Database Engine Tuning Advisor is tuning.</span></span> <span data-ttu-id="782e0-143">如果您创建的跟踪表位于其他服务器上，请将其移到数据库引擎优化顾问正在优化的服务器上。</span><span class="sxs-lookup"><span data-stu-id="782e0-143">If you create the trace table on a different server, then move it to the server where Database Engine Tuning Advisor is tuning.</span></span>  
  
-   <span data-ttu-id="782e0-144">工作负荷也可以嵌入到 XML 输入文件，在此文件中您也可以为每一事件指定一个权重。</span><span class="sxs-lookup"><span data-stu-id="782e0-144">Workloads can also be embedded in an XML input file, where you can also specify a weight for each event.</span></span> <span data-ttu-id="782e0-145">有关指定嵌入的工作负荷的详细信息，请参阅本主题后面的 [创建 XML 输入文件](#XMLInput) 。</span><span class="sxs-lookup"><span data-stu-id="782e0-145">For more information about specifying embedded workloads, see [Create an XML Input File](#XMLInput) later in this topic.</span></span>  
  
###  <a name="to-create-transact-sql-script-workloads"></a><a name="SSMS"></a> <span data-ttu-id="782e0-146">创建 TRANSACT-SQL 脚本工作负荷</span><span class="sxs-lookup"><span data-stu-id="782e0-146">To create Transact-SQL script workloads</span></span>  
  
1.  <span data-ttu-id="782e0-147">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中启动查询编辑器。</span><span class="sxs-lookup"><span data-stu-id="782e0-147">Launch the Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="782e0-148">有关详细信息，请参阅[查询和文本编辑器 (SQL Server Management Studio)](../scripting/query-and-text-editors-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="782e0-148">For more information, see [Query and Text Editors &#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md).</span></span>  
  
2.  <span data-ttu-id="782e0-149">在查询编辑器中键入您的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本。</span><span class="sxs-lookup"><span data-stu-id="782e0-149">Type your [!INCLUDE[tsql](../../includes/tsql-md.md)] script into the Query Editor.</span></span> <span data-ttu-id="782e0-150">此脚本应包含一组对想要优化的数据库执行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="782e0-150">This script should contain a set of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that execute against the database or databases that you want to tune.</span></span>  
  
3.  <span data-ttu-id="782e0-151">使用 **.sql** 扩展名保存文件。</span><span class="sxs-lookup"><span data-stu-id="782e0-151">Save the file with a **.sql** extension.</span></span> <span data-ttu-id="782e0-152">数据库引擎优化顾问 GUI 和命令行 **dta** 实用工具可以将此 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本用作工作负荷。</span><span class="sxs-lookup"><span data-stu-id="782e0-152">The Database Engine Tuning Advisor GUI and the command-line **dta** utility can use this [!INCLUDE[tsql](../../includes/tsql-md.md)] script as a workload.</span></span>  
  
###  <a name="to-create-trace-file-and-trace-table-workloads"></a><a name="Profiler"></a> <span data-ttu-id="782e0-153">创建跟踪文件和跟踪表工作负荷</span><span class="sxs-lookup"><span data-stu-id="782e0-153">To create trace file and trace table workloads</span></span>  
  
1.  <span data-ttu-id="782e0-154">使用下列方法之一启动 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="782e0-154">Launch [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] by using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="782e0-155">在 **“开始”** 菜单中，依次指向 **“所有程序”** 、 **Microsoft SQL Server**、 **“性能工具”** ，然后单击 **SQL Server Profiler**。</span><span class="sxs-lookup"><span data-stu-id="782e0-155">On the **Start** menu, point to **All Programs**, **Microsoft SQL Server**, **Performance Tools**, and then click **SQL Server Profiler**.</span></span>  
  
    -   <span data-ttu-id="782e0-156">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，单击 **“工具”** 菜单，然后单击 **“SQL Server Profiler”** 。</span><span class="sxs-lookup"><span data-stu-id="782e0-156">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], click the **Tools** menu, and then click **SQL Server Profiler**.</span></span>  
  
2.  <span data-ttu-id="782e0-157">按照下面介绍的步骤，使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 的“优化”模板来创建跟踪文件或表：</span><span class="sxs-lookup"><span data-stu-id="782e0-157">Create a trace file or table as described in the following procedures that uses the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Tuning** template:</span></span>  
  
    -   [<span data-ttu-id="782e0-158">创建跟踪 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="782e0-158">Create a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
    -   [<span data-ttu-id="782e0-159">将跟踪结果保存到文件 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="782e0-159">Save Trace Results to a File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md)  
  
         <span data-ttu-id="782e0-160">数据库引擎优化顾问假定工作负荷跟踪文件是滚动更新文件。</span><span class="sxs-lookup"><span data-stu-id="782e0-160">Database Engine Tuning Advisor assumes that the workload trace file is a rollover file.</span></span> <span data-ttu-id="782e0-161">有关滚动更新文件的详细信息，请参阅 [Limit Trace File and Table Sizes](../sql-trace/limit-trace-file-and-table-sizes.md)。</span><span class="sxs-lookup"><span data-stu-id="782e0-161">For more information about rollover files, see [Limit Trace File and Table Sizes](../sql-trace/limit-trace-file-and-table-sizes.md).</span></span>  
  
    -   [<span data-ttu-id="782e0-162">将跟踪结果保存到表 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="782e0-162">Save Trace Results to a Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md)  
  
         <span data-ttu-id="782e0-163">确保在将跟踪表用作工作负荷之前已经停止了跟踪。</span><span class="sxs-lookup"><span data-stu-id="782e0-163">Make sure that tracing has stopped before using a trace table as a workload.</span></span>  
  
 <span data-ttu-id="782e0-164">建议使用 SQL Server Profiler 优化模板来为数据库引擎优化顾问捕获工作负荷。</span><span class="sxs-lookup"><span data-stu-id="782e0-164">We recommend that you use the SQL Server Profiler Tuning template for capturing workloads for Database Engine Tuning Advisor.</span></span>  
  
 <span data-ttu-id="782e0-165">如果要使用自己的模板，请确保捕获了以下跟踪事件：</span><span class="sxs-lookup"><span data-stu-id="782e0-165">If you want to use your own template, ensure that the following trace events are captured:</span></span>  
  
-   <span data-ttu-id="782e0-166">**RPC:Completed**</span><span class="sxs-lookup"><span data-stu-id="782e0-166">**RPC:Completed**</span></span>  
  
-   <span data-ttu-id="782e0-167">**SQL:BatchCompleted**</span><span class="sxs-lookup"><span data-stu-id="782e0-167">**SQL:BatchCompleted**</span></span>  
  
-   <span data-ttu-id="782e0-168">**SP:StmtCompleted**</span><span class="sxs-lookup"><span data-stu-id="782e0-168">**SP:StmtCompleted**</span></span>  
  
 <span data-ttu-id="782e0-169">也可以使用这些跟踪事件的 **Starting** 版本。</span><span class="sxs-lookup"><span data-stu-id="782e0-169">You can also use the **Starting** versions of these trace events.</span></span> <span data-ttu-id="782e0-170">例如， **SQL:BatchStarting**。</span><span class="sxs-lookup"><span data-stu-id="782e0-170">For example, **SQL:BatchStarting**.</span></span> <span data-ttu-id="782e0-171">但是，这些跟踪事件的 **Completed** 版本包括 **Duration** 列，它能使数据库引擎优化顾问更有效地优化工作负荷。</span><span class="sxs-lookup"><span data-stu-id="782e0-171">However, the **Completed** versions of these trace events include the **Duration** column, which allows Database Engine Tuning Advisor to more effectively tune the workload.</span></span> <span data-ttu-id="782e0-172">数据库引擎优化顾问不优化其他类型的跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="782e0-172">Database Engine Tuning Advisor does not tune other types of trace events.</span></span> <span data-ttu-id="782e0-173">有关这些跟踪事件的详细信息，请参阅 [Stored Procedures Event Category](../event-classes/stored-procedures-event-category.md) 和 [TSQL Event Category](../event-classes/tsql-event-category.md)。</span><span class="sxs-lookup"><span data-stu-id="782e0-173">For more information about these trace events, see [Stored Procedures Event Category](../event-classes/stored-procedures-event-category.md) and [TSQL Event Category](../event-classes/tsql-event-category.md).</span></span> <span data-ttu-id="782e0-174">有关使用 SQL 跟踪存储过程来创建跟踪文件工作负荷的信息，请参阅[创建跟踪 (Transact-SQL)](../sql-trace/create-a-trace-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="782e0-174">For information about using the SQL Trace stored procedures to create a trace file workload, see [Create a Trace &#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md).</span></span>  
  
### <a name="trace-file-or-trace-table-workloads-that-contain-the-loginname-data-column"></a><span data-ttu-id="782e0-175">包含 LoginName 数据列的跟踪文件或跟踪表工作负荷</span><span class="sxs-lookup"><span data-stu-id="782e0-175">Trace File or Trace Table Workloads That Contain the LoginName Data Column</span></span>  
 <span data-ttu-id="782e0-176">数据库引擎优化顾问在优化过程中提交显示计划请求。</span><span class="sxs-lookup"><span data-stu-id="782e0-176">Database Engine Tuning Advisor submits Showplan requests as part of the tuning process.</span></span> <span data-ttu-id="782e0-177">当包含 **LoginName** 数据列的跟踪表或跟踪文件被用作工作负荷时，数据库引擎优化顾问将模拟 **LoginName**中指定的用户。</span><span class="sxs-lookup"><span data-stu-id="782e0-177">When a trace table or file that contains the **LoginName** data column is consumed as a workload, Database Engine Tuning Advisor impersonates the user specified in **LoginName**.</span></span> <span data-ttu-id="782e0-178">如果没有为此用户授予 SHOWPLAN 权限（该权限使用户能够为跟踪中包含的语句执行和生成显示计划），数据库引擎优化顾问将不会优化这些语句。</span><span class="sxs-lookup"><span data-stu-id="782e0-178">If this user has not been granted the SHOWPLAN permission, which enables the user to execute and produce Showplans for the statements contained in the trace, Database Engine Tuning Advisor will not tune those statements.</span></span>  
  
##### <a name="to-avoid-granting-the-showplan-permission-to-each-user-specified-in-the-loginname-column-of-the-trace"></a><span data-ttu-id="782e0-179">避免为跟踪的 LoginName 列中指定的每个用户授予 SHOWPLAN 权限</span><span class="sxs-lookup"><span data-stu-id="782e0-179">To avoid granting the SHOWPLAN permission to each user specified in the LoginName column of the trace</span></span>  
  
1.  <span data-ttu-id="782e0-180">优化跟踪文件或跟踪表工作负荷。</span><span class="sxs-lookup"><span data-stu-id="782e0-180">Tune the trace file or table workload.</span></span> <span data-ttu-id="782e0-181">有关详细信息，请参阅本主题后面的 [优化数据库](#Tune) 。</span><span class="sxs-lookup"><span data-stu-id="782e0-181">For more information, see [Tune a Database](#Tune) later in this topic.</span></span>  
  
2.  <span data-ttu-id="782e0-182">在优化日志中查看由于权限不足而没有优化的语句。</span><span class="sxs-lookup"><span data-stu-id="782e0-182">Check the tuning log for statements that were not tuned due to inadequate permissions.</span></span> <span data-ttu-id="782e0-183">有关详细信息，请参阅 [查看和使用数据库引擎优化顾问的输出](database-engine-tuning-advisor.md)。</span><span class="sxs-lookup"><span data-stu-id="782e0-183">For more information, see [View and Work with the Output from the Database Engine Tuning Advisor](database-engine-tuning-advisor.md).</span></span>  
  
3.  <span data-ttu-id="782e0-184">通过从未优化的事件中删除 **LoginName** 列来创建新的工作负荷，然后只将未优化的事件保存到新的跟踪文件或跟踪表中。</span><span class="sxs-lookup"><span data-stu-id="782e0-184">Create a new workload by deleting the **LoginName** column from the events that were not tuned, and then save only the untuned events in a new trace file or table.</span></span> <span data-ttu-id="782e0-185">有关从跟踪中删除数据列的详细信息，请参阅[指定跟踪文件的事件和数据列 (SQL Server Profiler)](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) 或[修改现有跟踪 (Transact SQL)](../sql-trace/modify-an-existing-trace-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="782e0-185">For more information about deleting data columns from a trace, see [Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) or [Modify an Existing Trace &#40;Transact-SQL&#41;](../sql-trace/modify-an-existing-trace-transact-sql.md).</span></span>  
  
4.  <span data-ttu-id="782e0-186">将不带 **LoginName** 列的新工作负荷重新提交到数据库引擎优化顾问。</span><span class="sxs-lookup"><span data-stu-id="782e0-186">Resubmit the new workload without the **LoginName** column to Database Engine Tuning Advisor.</span></span>  
  
 <span data-ttu-id="782e0-187">数据库引擎优化顾问将优化新的工作负荷，因为跟踪中未指定登录信息。</span><span class="sxs-lookup"><span data-stu-id="782e0-187">Database Engine Tuning Advisor will tune the new workload because login information is not specified in the trace.</span></span> <span data-ttu-id="782e0-188">如果某个语句没有相应的 **LoginName** ，数据库引擎优化顾问将通过模拟启动优化会话的用户（ **sysadmin** 固定服务器角色或 **db_owner** 固定数据库角色的成员）来优化该语句。</span><span class="sxs-lookup"><span data-stu-id="782e0-188">If the **LoginName** does not exist for a statement, Database Engine Tuning Advisor tunes that statement by impersonating the user who started the tuning session (a member of either the **sysadmin** fixed server role or the **db_owner** fixed database role).</span></span>  
  
##  <a name="tune-a-database"></a><a name="Tune"></a> <span data-ttu-id="782e0-189">优化数据库</span><span class="sxs-lookup"><span data-stu-id="782e0-189">Tune a Database</span></span>  
 <span data-ttu-id="782e0-190">若要优化数据库，可以使用数据库引擎优化顾问 GUI 或 **dta** 实用工具。</span><span class="sxs-lookup"><span data-stu-id="782e0-190">To tune a database, you can use the Database Engine Tuning Advisor GUI or the **dta** utility.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="782e0-191">在使用跟踪表作为数据库引擎优化顾问的工作负荷之前，确保跟踪已停止。</span><span class="sxs-lookup"><span data-stu-id="782e0-191">Make sure that tracing has stopped before using a trace table as a workload for Database Engine Tuning Advisor.</span></span> <span data-ttu-id="782e0-192">数据库引擎优化顾问不支持将还在写入跟踪事件的跟踪表作为工作负荷使用。</span><span class="sxs-lookup"><span data-stu-id="782e0-192">Database Engine Tuning Advisor does not support using a trace table to which trace events are still being written as a workload.</span></span>  
  
### <a name="use-the-database-engine-tuning-advisor-graphical-user-interface"></a><span data-ttu-id="782e0-193">使用数据库引擎优化顾问图形用户界面</span><span class="sxs-lookup"><span data-stu-id="782e0-193">Use the Database Engine Tuning Advisor Graphical User Interface</span></span>  
 <span data-ttu-id="782e0-194">在数据库引擎优化顾问 GUI 上，可以利用计划缓存、工作负荷文件或工作负荷表来优化数据库。</span><span class="sxs-lookup"><span data-stu-id="782e0-194">On the Database Engine Tuning Advisor GUI, you can tune a database by using the plan cache, workload files, or workload tables.</span></span> <span data-ttu-id="782e0-195">可使用数据库引擎优化顾问 GUI 轻松查看您当前的优化会话结果和以前的优化会话结果。</span><span class="sxs-lookup"><span data-stu-id="782e0-195">You can use the Database Engine Tuning Advisor GUI to easily view the results of your current tuning session and results of previous tuning sessions.</span></span> <span data-ttu-id="782e0-196">有关用户界面选项的信息，请参阅本主题后面的 [用户界面说明](#UI) 。</span><span class="sxs-lookup"><span data-stu-id="782e0-196">For information about user interface options, see [User Interface Descriptions](#UI) later in this topic.</span></span> <span data-ttu-id="782e0-197">有关使用数据库优化结果的详细信息，请参阅 [查看和使用数据库引擎优化顾问的输出](database-engine-tuning-advisor.md)。</span><span class="sxs-lookup"><span data-stu-id="782e0-197">For more information about working with the output after you tune a database, see [View and Work with the Output from the Database Engine Tuning Advisor](database-engine-tuning-advisor.md).</span></span>  
  
####  <a name="to-tune-a-database-by-using-the-plan-cache"></a><a name="PlanCache"></a> <span data-ttu-id="782e0-198">使用计划缓存优化数据库</span><span class="sxs-lookup"><span data-stu-id="782e0-198">To tune a database by using the plan cache</span></span>  
  
1.  <span data-ttu-id="782e0-199">启动数据库引擎优化顾问，并登录到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="782e0-199">Launch Database Engine Tuning Advisor, and log into an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="782e0-200">有关详细信息，请参阅本主题前面的 [启动数据库引擎优化顾问](#Start) 。</span><span class="sxs-lookup"><span data-stu-id="782e0-200">For more information, see [Start the Database Engine Tuning Advisor](#Start) earlier in this topic.</span></span>  
  
2.  <span data-ttu-id="782e0-201">在 **“常规”** 选项卡上，在 **“会话名称”** 中键入一个名称以创建新的优化会话。</span><span class="sxs-lookup"><span data-stu-id="782e0-201">On the **General** tab, type a name in **Session name** to create a new tuning session.</span></span> <span data-ttu-id="782e0-202">在启动优化会话之前，必须配置 **“常规”** 选项卡中的字段。</span><span class="sxs-lookup"><span data-stu-id="782e0-202">You must configure the fields in the **General** tab before starting a tuning session.</span></span> <span data-ttu-id="782e0-203">在启动优化会话之前，不必修改 **“优化选项”** 选项卡的设置。</span><span class="sxs-lookup"><span data-stu-id="782e0-203">It is not necessary to modify the settings of the **Tuning Options** tab before starting a tuning session.</span></span>  
  
3.  <span data-ttu-id="782e0-204">选择 **“计划缓存”** 作为工作负荷选项。</span><span class="sxs-lookup"><span data-stu-id="782e0-204">Select **Plan Cache** as the workload option.</span></span> <span data-ttu-id="782e0-205">数据库引擎优化顾问将从计划缓存中选择前 1,000 个事件用于分析。</span><span class="sxs-lookup"><span data-stu-id="782e0-205">Database Engine Tuning Advisor selects the top 1,000 events from the plan cache to use for analysis.</span></span>  
  
4.  <span data-ttu-id="782e0-206">选择要优化的数据库，或者可选择从 **“选择的表”** 中为每个数据库选择一个或多个表。</span><span class="sxs-lookup"><span data-stu-id="782e0-206">Select the database or databases that you want to tune, and optionally from **Selected Tables**, choose one or more tables from each database.</span></span> <span data-ttu-id="782e0-207">若要包括所有数据库的缓存项，请从 **“优化选项”** 中单击 **“高级选项”** ，然后选中 **“包括来自所有数据库的计划缓存事件”** 。</span><span class="sxs-lookup"><span data-stu-id="782e0-207">To include cache entries for all databases, from **Tuning Options**, click **Advanced Options** and then check **Include plan cache events from all databases**.</span></span>  
  
5.  <span data-ttu-id="782e0-208">选中 **“保存优化日志”** 以保存优化日志的副本。</span><span class="sxs-lookup"><span data-stu-id="782e0-208">Check **Save tuning log** to save a copy of the tuning log.</span></span> <span data-ttu-id="782e0-209">如果不希望保存优化日志的副本，请清除该复选框。</span><span class="sxs-lookup"><span data-stu-id="782e0-209">Clear the check box if you do not want to save a copy of the tuning log.</span></span>  
  
     <span data-ttu-id="782e0-210">在分析之后，可以通过打开会话并选择 **“进度”** 选项卡来查看优化日志。</span><span class="sxs-lookup"><span data-stu-id="782e0-210">You can view the tuning log after analysis by opening the session and selecting the **Progress** tab.</span></span>  
  
6.  <span data-ttu-id="782e0-211">单击 **“优化选项”** 选项卡，从列出的选项中进行选择。</span><span class="sxs-lookup"><span data-stu-id="782e0-211">Click the **Tuning Options** tab and select from the options listed there.</span></span>  
  
7.  <span data-ttu-id="782e0-212">单击 **“开始分析”** 。</span><span class="sxs-lookup"><span data-stu-id="782e0-212">Click **Start Analysis**.</span></span>  
  
     <span data-ttu-id="782e0-213">如果希望停止已经启动的优化会话，请在 **“操作”** 菜单上选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="782e0-213">If you want to stop the tuning session after it has started, choose one of the following options on the **Actions** menu:</span></span>  
  
    -   <span data-ttu-id="782e0-214">选择“停止分析（并提供建议）”将停止优化会话，并提示你选择是否希望数据库引擎优化顾问根据目前已完成的分析来生成建议。</span><span class="sxs-lookup"><span data-stu-id="782e0-214">**Stop Analysis (With Recommendations)** stops the tuning session and prompts you to decide whether you want Database Engine Tuning Advisor to generate recommendations based on the analysis done up to this point.</span></span>  
  
    -   <span data-ttu-id="782e0-215">选择 **“停止分析”** 将停止优化会话而不生成任何建议。</span><span class="sxs-lookup"><span data-stu-id="782e0-215">**Stop Analysis** stops the tuning session without generating any recommendations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="782e0-216">不支持暂停数据库引擎优化顾问。</span><span class="sxs-lookup"><span data-stu-id="782e0-216">Pausing Database Engine Tuning Advisor is not supported.</span></span> <span data-ttu-id="782e0-217">如果在单击“停止分析”或“停止分析（并提供建议）”工具栏按钮之后单击“开始分析”工具栏按钮，数据库引擎优化顾问将启动新的优化会话。  </span><span class="sxs-lookup"><span data-stu-id="782e0-217">If you click the **Start Analysis** toolbar button after clicking either the **Stop Analysis** or **Stop Analysis (With Recommendations)** toolbar buttons, Database Engine Tuning Advisor starts a new tuning session.</span></span>  
  
##### <a name="to-tune-a-database-using-a-workload-file-or-table-as-input"></a><span data-ttu-id="782e0-218">使用工作负荷文件或表作为输入来优化数据库</span><span class="sxs-lookup"><span data-stu-id="782e0-218">To tune a database using a workload file or table as input</span></span>  
  
1.  <span data-ttu-id="782e0-219">确定您希望数据库引擎优化顾问在分析过程中考虑添加、删除或保留的数据库功能（索引、索引视图、分区）。</span><span class="sxs-lookup"><span data-stu-id="782e0-219">Determine the database features (indexes, indexed views, partitioning) you want Database Engine Tuning Advisor to consider adding, removing, or retaining during analysis.</span></span>  
  
2.  <span data-ttu-id="782e0-220">创建工作负荷。</span><span class="sxs-lookup"><span data-stu-id="782e0-220">Create a workload.</span></span> <span data-ttu-id="782e0-221">有关详细信息，请参阅本主题前面的 [创建工作负荷](#Create) 。</span><span class="sxs-lookup"><span data-stu-id="782e0-221">For more information, see [Create a Workload](#Create) earlier in this topic.</span></span>  
  
3.  <span data-ttu-id="782e0-222">启动数据库引擎优化顾问，并登录到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="782e0-222">Launch Database Engine Tuning Advisor, and log into an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="782e0-223">有关详细信息，请参阅本主题前面的 [启动数据库引擎优化顾问](#Start) 。</span><span class="sxs-lookup"><span data-stu-id="782e0-223">For more information, see [Start the Database Engine Tuning Advisor](#Start) earlier in this topic.</span></span>  
  
4.  <span data-ttu-id="782e0-224">在 **“常规”** 选项卡上，在 **“会话名称”** 中键入一个名称以创建新的优化会话。</span><span class="sxs-lookup"><span data-stu-id="782e0-224">On the **General** tab, type a name in **Session name** to create a new tuning session.</span></span>  
  
5.  <span data-ttu-id="782e0-225">选择一个 **“工作负荷文件”** 或 **“表”** ，然后在相邻的文本框中键入文件的路径或表的名称。</span><span class="sxs-lookup"><span data-stu-id="782e0-225">Choose either a **Workload File** or **Table** and type either the path to the file, or the name of the table in the adjacent text box.</span></span>  
  
     <span data-ttu-id="782e0-226">指定表的格式为</span><span class="sxs-lookup"><span data-stu-id="782e0-226">The format for specifying a table is</span></span>  
  
    ```  
  
    database_name.schema_name.table_name  
    ```  
  
     <span data-ttu-id="782e0-227">若要搜索工作负荷文件或表，请单击 **“浏览”** 。</span><span class="sxs-lookup"><span data-stu-id="782e0-227">To search for a workload file or table, click **Browse**.</span></span> <span data-ttu-id="782e0-228">数据库引擎优化顾问假定工作负荷文件是滚动更新文件。</span><span class="sxs-lookup"><span data-stu-id="782e0-228">Database Engine Tuning Advisor assumes that workload files are rollover files.</span></span> <span data-ttu-id="782e0-229">有关滚动更新文件的详细信息，请参阅 [Limit Trace File and Table Sizes](../sql-trace/limit-trace-file-and-table-sizes.md)。</span><span class="sxs-lookup"><span data-stu-id="782e0-229">For more information about rollover files, see [Limit Trace File and Table Sizes](../sql-trace/limit-trace-file-and-table-sizes.md).</span></span>  
  
     <span data-ttu-id="782e0-230">使用跟踪表作为工作负荷时，该表必须存在于数据库引擎优化顾问正在优化的同一台服务器上。</span><span class="sxs-lookup"><span data-stu-id="782e0-230">When using a trace table as a workload, that table must exist on the same server that Database Engine Tuning Advisor is tuning.</span></span> <span data-ttu-id="782e0-231">如果您创建的跟踪表在其他服务器上，则必须将其移到数据库引擎优化顾问准备优化的服务器上才能用作工作负荷。</span><span class="sxs-lookup"><span data-stu-id="782e0-231">If you create the trace table on a different server, move it to the server that Database Engine Tuning Advisor is tuning before using it as your workload.</span></span>  
  
6.  <span data-ttu-id="782e0-232">选择要对其运行在步骤 5 中选择的工作负荷的数据库和表。</span><span class="sxs-lookup"><span data-stu-id="782e0-232">Select the databases and tables against which you wish to run the workload that you selected in step 5.</span></span> <span data-ttu-id="782e0-233">要选择表，请单击 **“所选表”** 箭头。</span><span class="sxs-lookup"><span data-stu-id="782e0-233">To select the tables, click the **Selected Tables** arrow.</span></span>  
  
7.  <span data-ttu-id="782e0-234">选中 **“保存优化日志”** 以保存优化日志的副本。</span><span class="sxs-lookup"><span data-stu-id="782e0-234">Check **Save tuning log** to save a copy of the tuning log.</span></span> <span data-ttu-id="782e0-235">如果不希望保存优化日志的副本，请清除该复选框。</span><span class="sxs-lookup"><span data-stu-id="782e0-235">Clear the check box if you do not want to save a copy of the tuning log.</span></span>  
  
     <span data-ttu-id="782e0-236">在分析之后，可以通过打开会话并选择 **“进度”** 选项卡来查看优化日志。</span><span class="sxs-lookup"><span data-stu-id="782e0-236">You can view the tuning log after analysis by opening the session and selecting the **Progress** tab.</span></span>  
  
8.  <span data-ttu-id="782e0-237">单击 **“优化选项”** 选项卡，从列出的选项中进行选择。</span><span class="sxs-lookup"><span data-stu-id="782e0-237">Click the **Tuning Options** tab and select from the options listed there.</span></span>  
  
9. <span data-ttu-id="782e0-238">单击工具栏中的 **“开始分析”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="782e0-238">Click the **Start Analysis** button in the toolbar.</span></span>  
  
     <span data-ttu-id="782e0-239">如果希望停止已经启动的优化会话，请在 **“操作”** 菜单上选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="782e0-239">If you want to stop the tuning session after it has started, choose one of the following options on the **Actions** menu:</span></span>  
  
    -   <span data-ttu-id="782e0-240">选择“停止分析（并提供建议）”将停止优化会话，并提示你选择是否希望数据库引擎优化顾问根据目前已完成的分析来生成建议。</span><span class="sxs-lookup"><span data-stu-id="782e0-240">**Stop Analysis (With Recommendations)** stops the tuning session and prompts you to decide whether you want Database Engine Tuning Advisor to generate recommendations based on the analysis done up to this point.</span></span>  
  
    -   <span data-ttu-id="782e0-241">选择 **“停止分析”** 将停止优化会话而不生成任何建议。</span><span class="sxs-lookup"><span data-stu-id="782e0-241">**Stop Analysis** stops the tuning session without generating any recommendations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="782e0-242">不支持暂停数据库引擎优化顾问。</span><span class="sxs-lookup"><span data-stu-id="782e0-242">Pausing Database Engine Tuning Advisor is not supported.</span></span> <span data-ttu-id="782e0-243">如果在单击“停止分析”或“停止分析（并提供建议）”工具栏按钮之后单击“开始分析”工具栏按钮，数据库引擎优化顾问将启动新的优化会话。  </span><span class="sxs-lookup"><span data-stu-id="782e0-243">If you click the **Start Analysis** toolbar button after clicking either the **Stop Analysis** or **Stop Analysis (With Recommendations)** toolbar buttons, Database Engine Tuning Advisor starts a new tuning session.</span></span>  
  
###  <a name="use-the-dta-utility"></a><a name="dta"></a> <span data-ttu-id="782e0-244">使用 dta 实用工具</span><span class="sxs-lookup"><span data-stu-id="782e0-244">Use the dta Utility</span></span>  
 <span data-ttu-id="782e0-245">[dta 实用工具](../../tools/dta/dta-utility.md) 提供了一个命令提示符可执行文件，可以用来优化数据库。</span><span class="sxs-lookup"><span data-stu-id="782e0-245">The [dta utility](../../tools/dta/dta-utility.md) provides a command prompt executable file that you can use to tune databases.</span></span> <span data-ttu-id="782e0-246">该实用工具使您能够在批处理文件和脚本中使用数据库引擎优化顾问的功能。</span><span class="sxs-lookup"><span data-stu-id="782e0-246">It enables you to use Database Engine Tuning Advisor functionality in batch files and scripts.</span></span> <span data-ttu-id="782e0-247">**dta** 实用工具使用计划缓存项、跟踪文件、跟踪表和 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本作为工作负荷。</span><span class="sxs-lookup"><span data-stu-id="782e0-247">The **dta** utility takes plan cache entries, trace files, trace tables, and [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts as workloads.</span></span> <span data-ttu-id="782e0-248">它还将使用符合数据库引擎优化顾问 XML 架构的 XML 输入，有关该架构的详细信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?linkid=43100)。</span><span class="sxs-lookup"><span data-stu-id="782e0-248">It also takes XML input that conforms to the Database Engine Tuning Advisor XML schema, which is available at this [Microsoft Web site](https://go.microsoft.com/fwlink/?linkid=43100).</span></span>  
  
 <span data-ttu-id="782e0-249">在使用 **dta** 实用工具开始优化工作负荷之前，请考虑下列事项：</span><span class="sxs-lookup"><span data-stu-id="782e0-249">Consider the following before you begin tuning a workload with the **dta** utility:</span></span>  
  
-   <span data-ttu-id="782e0-250">使用跟踪表作为工作负荷时，该表必须存在于数据库引擎优化顾问正在优化的同一台服务器上。</span><span class="sxs-lookup"><span data-stu-id="782e0-250">When using a trace table as a workload, that table must exist on the same server that Database Engine Tuning Advisor is tuning.</span></span> <span data-ttu-id="782e0-251">如果在其他服务器上创建了跟踪表，则将该跟踪表移动到数据库引擎优化顾问正在优化的服务器。</span><span class="sxs-lookup"><span data-stu-id="782e0-251">If you create the trace table on a different server, then move it to the server that Database Engine Tuning Advisor is tuning.</span></span>  
  
-   <span data-ttu-id="782e0-252">在使用跟踪表作为数据库引擎优化顾问的工作负荷之前，确保跟踪已停止。</span><span class="sxs-lookup"><span data-stu-id="782e0-252">Make sure that tracing has stopped before using a trace table as a workload for Database Engine Tuning Advisor.</span></span> <span data-ttu-id="782e0-253">数据库引擎优化顾问不支持将还在写入跟踪事件的跟踪表作为工作负荷使用。</span><span class="sxs-lookup"><span data-stu-id="782e0-253">Database Engine Tuning Advisor does not support using a trace table to which trace events are still being written as a workload.</span></span>  
  
-   <span data-ttu-id="782e0-254">如果优化会话运行的时间比预计运行时间长，可以按 CTRL+C 停止优化会话并根据 **dta** 此时已完成的分析生成建议。</span><span class="sxs-lookup"><span data-stu-id="782e0-254">If a tuning session continues running longer than you had anticipated it would run, you can press CTRL+C to stop the tuning session and generate recommendations based on the analysis **dta** has completed up to this point.</span></span> <span data-ttu-id="782e0-255">系统将提示您确定是否要生成建议。</span><span class="sxs-lookup"><span data-stu-id="782e0-255">You will be prompted to decide whether you want to generate recommendations or not.</span></span> <span data-ttu-id="782e0-256">再次按 Ctrl+C 停止优化会话，而不生成建议。</span><span class="sxs-lookup"><span data-stu-id="782e0-256">Press CTRL+C again to stop the tuning session without generating recommendations.</span></span>  
  
 <span data-ttu-id="782e0-257">有关 **dta** 实用工具语法和示例的详细信息，请参阅 [dta Utility](../../tools/dta/dta-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="782e0-257">For more information about **dta** utility syntax and examples, see [dta Utility](../../tools/dta/dta-utility.md).</span></span>  
  
##### <a name="to-tune-a-database-by-using-the-plan-cache"></a><span data-ttu-id="782e0-258">使用计划缓存优化数据库</span><span class="sxs-lookup"><span data-stu-id="782e0-258">To tune a database by using the plan cache</span></span>  
  
1.  <span data-ttu-id="782e0-259">指定 **-ip** 选项。</span><span class="sxs-lookup"><span data-stu-id="782e0-259">Specify the **-ip** option.</span></span> <span data-ttu-id="782e0-260">分析选定数据库的前 1000 个计划缓存事件。</span><span class="sxs-lookup"><span data-stu-id="782e0-260">The top 1,000 plan cache events for the selected databases are analyzed.</span></span>  
  
     <span data-ttu-id="782e0-261">在命令提示符下，输入以下内容：</span><span class="sxs-lookup"><span data-stu-id="782e0-261">From a command prompt, enter the following:</span></span>  
  
    ```  
    dta -E -D DatabaseName -ip -s SessionName  
    ```  
  
2.  <span data-ttu-id="782e0-262">若要修改用于分析的事件数，请指定“–n”选项。</span><span class="sxs-lookup"><span data-stu-id="782e0-262">To modify the number of events to use for analysis, specify the **-n** option.</span></span> <span data-ttu-id="782e0-263">以下示例将缓存项数提高到 2,000。</span><span class="sxs-lookup"><span data-stu-id="782e0-263">The following example increases the number of cache entries to 2,000.</span></span>  
  
    ```  
    dta -E -D DatabaseName -ip -n 2000-s SessionName1  
    ```  
  
3.  <span data-ttu-id="782e0-264">若要分析实例中的所有数据库的事件，请指定 **-ipf** 选项。</span><span class="sxs-lookup"><span data-stu-id="782e0-264">To analyze events for all databases in the instance, specify the **-ipf** option.</span></span>  
  
    ```  
    dta -E -D DatabaseName -ip -ipf -n 2000 -s SessionName2  
    ```  
  
##### <a name="to-tune-a-database-by-using-a-workload-and-dta-utility-default-settings"></a><span data-ttu-id="782e0-265">使用工作负荷和 dta 实用工具的默认设置优化数据库</span><span class="sxs-lookup"><span data-stu-id="782e0-265">To tune a database by using a workload and dta utility default settings</span></span>  
  
1.  <span data-ttu-id="782e0-266">确定您希望数据库引擎优化顾问在分析过程中考虑添加、删除或保留的数据库功能（索引、索引视图、分区）。</span><span class="sxs-lookup"><span data-stu-id="782e0-266">Determine the database features (indexes, indexed views, partitioning) you want Database Engine Tuning Advisor to consider adding, removing, or retaining during analysis.</span></span>  
  
2.  <span data-ttu-id="782e0-267">创建工作负荷。</span><span class="sxs-lookup"><span data-stu-id="782e0-267">Create a workload.</span></span> <span data-ttu-id="782e0-268">有关详细信息，请参阅本主题前面的 [创建工作负荷](#Create) 。</span><span class="sxs-lookup"><span data-stu-id="782e0-268">For more information, see [Create a Workload](#Create) earlier in this topic.</span></span>  
  
3.  <span data-ttu-id="782e0-269">在命令提示符下，输入以下内容：</span><span class="sxs-lookup"><span data-stu-id="782e0-269">From a command prompt, enter the following:</span></span>  
  
    ```  
    dta -E -D DatabaseName -if WorkloadFile -s SessionName  
    ```  
  
     <span data-ttu-id="782e0-270">其中， `-E` 指定优化会话使用的是可信连接（而不是登录 ID 和密码）， `-D` 指定要优化的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="782e0-270">where `-E` specifies that your tuning session uses a trusted connection (instead of a login ID and password), `-D` specifies the name of the database you want to tune.</span></span> <span data-ttu-id="782e0-271">默认情况下，实用工具会连接到本地计算机上的默认 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="782e0-271">By default, the utility connects to the default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the local computer.</span></span> <span data-ttu-id="782e0-272">（使用 `-S` 选项可以像下面过程中显示的那样指定远程数据库，或者指定命名实例。） `-if` 选项指定工作负荷文件（可以是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本或跟踪文件）的名称和路径， `-s` 指定优化会话的名称。</span><span class="sxs-lookup"><span data-stu-id="782e0-272">(Use the `-S` option to specify a remote database as shown in the following procedure, or to specify a named instance.) The `-if` option specifies the name and path to a workload file (which can be a [!INCLUDE[tsql](../../includes/tsql-md.md)] script or a trace file), and `-s` specifies a name for your tuning session.</span></span>  
  
     <span data-ttu-id="782e0-273">此处显示的四个选项（数据库名称、工作负荷、连接类型和会话名称）是必需的。</span><span class="sxs-lookup"><span data-stu-id="782e0-273">The four options shown here (database name, workload, connection type, and session name) are mandatory.</span></span>  
  
##### <a name="to-tune-a-remote-database-or-a-named-instance-for-a-specific-duration"></a><span data-ttu-id="782e0-274">在特定的持续时间内优化远程数据库或命名实例</span><span class="sxs-lookup"><span data-stu-id="782e0-274">To tune a remote database or a named instance for a specific duration</span></span>  
  
1.  <span data-ttu-id="782e0-275">确定您希望数据库引擎优化顾问在分析过程中考虑添加、删除或保留的数据库功能（索引、索引视图、分区）。</span><span class="sxs-lookup"><span data-stu-id="782e0-275">Determine the database features (indexes, indexed views, partitioning) you want Database Engine Tuning Advisor to consider adding, removing, or retaining during analysis.</span></span>  
  
2.  <span data-ttu-id="782e0-276">创建工作负荷。</span><span class="sxs-lookup"><span data-stu-id="782e0-276">Create a workload.</span></span> <span data-ttu-id="782e0-277">有关详细信息，请参阅本主题前面的 [创建工作负荷](#Create) 。</span><span class="sxs-lookup"><span data-stu-id="782e0-277">For more information, see [Create a Workload](#Create) earlier in this topic.</span></span>  
  
3.  <span data-ttu-id="782e0-278">在命令提示符下，输入以下内容：</span><span class="sxs-lookup"><span data-stu-id="782e0-278">From a command prompt, enter the following:</span></span>  
  
    ```  
    dta -S ServerName\Instance -D DatabaseName -it WorkloadTableName   
    -U LoginID -P Password -s SessionName -A TuningTimeInMinutes  
    ```  
  
     <span data-ttu-id="782e0-279">其中， `-S` 指定远程服务器的名称和实例（而不是本地服务器上的命名实例）， `-D` 指定要优化的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="782e0-279">where `-S` specifies a remote server name and instance (or a named instance on the local server) and `-D` specifies the name of the database you want to tune.</span></span> <span data-ttu-id="782e0-280">`-it` 选项指定工作负荷表的名称， `-U` 和 `-P` 指定登录远程数据库的登录 ID 和密码， `-s` 指定优化会话的名称， `-A` 指定优化会话的持续时间（分钟）。</span><span class="sxs-lookup"><span data-stu-id="782e0-280">The `-it` option specifies the name of the workload table, `-U` and `-P` specify the login ID and password to the remote database, `-s` specifies the tuning session name, and `-A` specifies the tuning session duration in minutes.</span></span> <span data-ttu-id="782e0-281">默认情况下， **dta** 实用工具使用的优化持续时间为 8 小时。</span><span class="sxs-lookup"><span data-stu-id="782e0-281">By default, the **dta** utility uses an 8-hour tuning duration.</span></span> <span data-ttu-id="782e0-282">如果希望数据库引擎优化顾问在时间长度不限的条件下优化工作负荷，请将 **选项指定为** 0 `-A` （零）。</span><span class="sxs-lookup"><span data-stu-id="782e0-282">If you would like Database Engine Tuning Advisor to tune a workload for an unlimited amount of time, specify **0** (zero) with the `-A` option.</span></span>  
  
##### <a name="to-tune-a-database-using-an-xml-input-file"></a><span data-ttu-id="782e0-283">使用 XML 输入文件优化数据库</span><span class="sxs-lookup"><span data-stu-id="782e0-283">To tune a database using an XML input file</span></span>  
  
1.  <span data-ttu-id="782e0-284">确定您希望数据库引擎优化顾问在分析过程中考虑添加、删除或保留的数据库功能（索引、索引视图、分区）。</span><span class="sxs-lookup"><span data-stu-id="782e0-284">Determine the database features (indexes, indexed views, partitioning) you want Database Engine Tuning Advisor to consider adding, removing, or retaining during analysis.</span></span>  
  
2.  <span data-ttu-id="782e0-285">创建工作负荷。</span><span class="sxs-lookup"><span data-stu-id="782e0-285">Create a workload.</span></span> <span data-ttu-id="782e0-286">有关详细信息，请参阅本主题前面的 [创建工作负荷](#Create) 。</span><span class="sxs-lookup"><span data-stu-id="782e0-286">For more information, see [Create a Workload](#Create) earlier in this topic.</span></span>  
  
3.  <span data-ttu-id="782e0-287">创建 XML 输入文件。</span><span class="sxs-lookup"><span data-stu-id="782e0-287">Create an XML input file.</span></span> <span data-ttu-id="782e0-288">有关详细信息，请参阅本主题后面的 [创建 XML 输入文件](#XMLInput) 。</span><span class="sxs-lookup"><span data-stu-id="782e0-288">For more information, see [Create XML Input Files](#XMLInput) later in this topic.</span></span>  
  
4.  <span data-ttu-id="782e0-289">在命令提示符下，输入以下内容：</span><span class="sxs-lookup"><span data-stu-id="782e0-289">From a command prompt, enter the following:</span></span>  
  
    ```  
    dta -E -S ServerName\Instance -s SessionName -ix PathToXMLInputFile  
    ```  
  
     <span data-ttu-id="782e0-290">其中， `-E` 指定可信连接， `-S` 指定远程服务器和实例或本地服务器上的命名实例， `-s` 指定优化会话的名称， `-ix` 指定用于优化会话的 XML 输入文件。</span><span class="sxs-lookup"><span data-stu-id="782e0-290">where `-E` specifies a trusted connection, `-S` specifies a remote server and instance, or a named instance on the local server, `-s` specifies a tuning session name, and `-ix` specifies the XML input file to use for the tuning session.</span></span>  
  
5.  <span data-ttu-id="782e0-291">实用工具完成工作负荷的优化之后，可以使用数据库引擎优化顾问 GUI 查看优化会话的结果。</span><span class="sxs-lookup"><span data-stu-id="782e0-291">After the utility finishes tuning the workload, you can view the results of tuning sessions with the Database Engine Tuning Advisor GUI.</span></span> <span data-ttu-id="782e0-292">还有一种方法，可以使用 **-ox** 选项指定将优化建议写入 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="782e0-292">As an alternative, you can also specify that the tuning recommendations be written to an XML file with the **-ox** option.</span></span> <span data-ttu-id="782e0-293">有关详细信息，请参阅 [dta Utility](../../tools/dta/dta-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="782e0-293">For more information, see [dta Utility](../../tools/dta/dta-utility.md).</span></span>  
  
##  <a name="create-an-xml-input-file"></a><a name="XMLInput"></a> <span data-ttu-id="782e0-294">创建 XML 输入文件</span><span class="sxs-lookup"><span data-stu-id="782e0-294">Create an XML Input File</span></span>  
 <span data-ttu-id="782e0-295">如果是有经验的 XML 开发人员，您可以创建一些 XML 格式的文件， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 优化顾问可使用这些文件来优化工作负荷。</span><span class="sxs-lookup"><span data-stu-id="782e0-295">If you are an experienced XML developer, you can create XML-formatted files that [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor can use to tune workloads.</span></span> <span data-ttu-id="782e0-296">若要创建这些 XML 文件，请使用您最喜爱的 XML 工具编辑示例文件，或者通过 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 优化顾问 XML 架构生成实例。</span><span class="sxs-lookup"><span data-stu-id="782e0-296">To create these XML files, use your favorite XML tools to edit a sample file or to generate an instance from the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML schema.</span></span>  
  
 <span data-ttu-id="782e0-297">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 优化顾问 XML 架构位于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装的以下位置：</span><span class="sxs-lookup"><span data-stu-id="782e0-297">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML schema is available in your [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation in the following location:</span></span>  
  
 <span data-ttu-id="782e0-298">C:\Program Files\Microsoft SQL Server\100\Tools\Binn\schemas\sqlserver\2004\07\dta\dtaschema.xsd</span><span class="sxs-lookup"><span data-stu-id="782e0-298">C:\Program Files\Microsoft SQL Server\100\Tools\Binn\schemas\sqlserver\2004\07\dta\dtaschema.xsd</span></span>  
  
 <span data-ttu-id="782e0-299">此 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Microsoft 网站 [上也在线提供了](https://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409)优化顾问 XML 架构。</span><span class="sxs-lookup"><span data-stu-id="782e0-299">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML schema is also available online at this [Microsoft Web site](https://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409).</span></span>  
  
 <span data-ttu-id="782e0-300">单击此 URL 可打开一个包含许多 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML 架构的页面。</span><span class="sxs-lookup"><span data-stu-id="782e0-300">This URL takes you to a page where many [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML schemas are available.</span></span> <span data-ttu-id="782e0-301">向下滚动页面，直至找到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 优化顾问所在的行。</span><span class="sxs-lookup"><span data-stu-id="782e0-301">Scroll down the page until you reach the row for [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor.</span></span>  
  
#### <a name="to-create-an-xml-input-file-to-tune-workloads"></a><span data-ttu-id="782e0-302">创建 XML 输入文件以优化工作负荷</span><span class="sxs-lookup"><span data-stu-id="782e0-302">To create an XML input file to tune workloads</span></span>  
  
1.  <span data-ttu-id="782e0-303">创建工作负荷。</span><span class="sxs-lookup"><span data-stu-id="782e0-303">Create a workload.</span></span> <span data-ttu-id="782e0-304">您可以通过使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]中的优化模板来使用跟踪文件或表，或创建可产生典型 [!INCLUDE[tsql](../../includes/tsql-md.md)] 工作负荷的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]脚本。</span><span class="sxs-lookup"><span data-stu-id="782e0-304">You can use a trace file or table by using the tuning template in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], or create a [!INCLUDE[tsql](../../includes/tsql-md.md)] script that reproduces a representative workload for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="782e0-305">有关详细信息，请参阅本主题前面的 [创建工作负荷](#Create) 。</span><span class="sxs-lookup"><span data-stu-id="782e0-305">For more information, see [Create a Workload](#Create) earlier in this topic.</span></span>  
  
2.  <span data-ttu-id="782e0-306">使用下列方法之一创建 XML 输入文件：</span><span class="sxs-lookup"><span data-stu-id="782e0-306">Create an XML input file by one of the following methods:</span></span>  
  
    -   <span data-ttu-id="782e0-307">复制一个 [XML 输入文件示例 (DTA)](../../tools/dta/xml-input-file-samples-dta.md) 并将其粘贴到你最喜爱的 XML 编辑器。</span><span class="sxs-lookup"><span data-stu-id="782e0-307">Copy and paste one of the [XML Input File Samples &#40;DTA&#41;](../../tools/dta/xml-input-file-samples-dta.md) into your favorite XML editor.</span></span> <span data-ttu-id="782e0-308">更改值来为安装的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 指定适当的参数，然后保存 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="782e0-308">Change the values to specify the appropriate arguments for your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation, and save the XML file.</span></span>  
  
    -   <span data-ttu-id="782e0-309">使用您最喜爱的 XML 工具，通过 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 优化顾问 XML 架构生成一个实例。</span><span class="sxs-lookup"><span data-stu-id="782e0-309">Using your favorite XML tool, generate an instance from the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML schema.</span></span>  
  
3.  <span data-ttu-id="782e0-310">创建 XML 输入文件之后，将它用作 **dta** 命令行实用工具的输入来优化工作负荷。</span><span class="sxs-lookup"><span data-stu-id="782e0-310">After creating the XML input file, use it as input to the **dta** command-line utility to tune the workload.</span></span> <span data-ttu-id="782e0-311">有关通过此实用工具使用 XML 输入文件的信息，请参阅本主题前面的 [使用 dta 实用工具](#dta) 部分。</span><span class="sxs-lookup"><span data-stu-id="782e0-311">For information about using XML input files with this utility, see the section [Use the dta Utililty](#dta) earlier in this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="782e0-312">如果你要使用内联工作负荷（即在 XML 输入文件中直接指定的工作负荷），请使用[内联工作负荷的 XML 输入文件示例 (DTA)](../../tools/dta/xml-input-file-sample-with-inline-workload-dta.md) 示例。</span><span class="sxs-lookup"><span data-stu-id="782e0-312">If you want to use an inline workload, which is a workload that is specified directly in the XML input file, use the sample [XML Input File Sample with Inline Workload &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-inline-workload-dta.md).</span></span>  
  
##  <a name="user-interface-descriptions"></a><a name="UI"></a> <span data-ttu-id="782e0-313">用户界面说明</span><span class="sxs-lookup"><span data-stu-id="782e0-313">User Interface Descriptions</span></span>  
  
### <a name="tools-menuoptions-page"></a><span data-ttu-id="782e0-314">“工具”菜单/“选项”页</span><span class="sxs-lookup"><span data-stu-id="782e0-314">Tools Menu/Options Page</span></span>  
 <span data-ttu-id="782e0-315">使用此对话框可以为数据库引擎优化顾问指定常规配置参数。</span><span class="sxs-lookup"><span data-stu-id="782e0-315">Use this dialog box to specify general configuration parameters for the Database Engine Tuning Advisor.</span></span>  
  
 <span data-ttu-id="782e0-316">**启动时**</span><span class="sxs-lookup"><span data-stu-id="782e0-316">**On startup**</span></span>  
 <span data-ttu-id="782e0-317">指定数据库引擎优化顾问在启动时应执行的操作：以不连接数据库的方式打开、显示“新建连接”对话框、显示新会话或者加载上次已加载的会话。</span><span class="sxs-lookup"><span data-stu-id="782e0-317">Specify what Database Engine Tuning Advisor should do when it is started: open without a database connection, show a **New Connection** dialog box, show a new session, or load the last loaded session.</span></span>  
  
 <span data-ttu-id="782e0-318">**更改字体**</span><span class="sxs-lookup"><span data-stu-id="782e0-318">**Change font**</span></span>  
 <span data-ttu-id="782e0-319">指定由数据库引擎优化顾问表使用的显示字体。</span><span class="sxs-lookup"><span data-stu-id="782e0-319">Specify the display font used by Database Engine Tuning Advisor tables.</span></span>  
  
 <span data-ttu-id="782e0-320">**最近使用的列表中的项数**</span><span class="sxs-lookup"><span data-stu-id="782e0-320">**Number of items in most recently used lists**</span></span>  
 <span data-ttu-id="782e0-321">指定在“文件”菜单的“最近使用的会话”和“最近使用的文件”下显示的会话数或文件数。</span><span class="sxs-lookup"><span data-stu-id="782e0-321">Specify the number of sessions or files to display under **Recent Sessions** or **Recent Files** in the **File** menu.</span></span>  
  
 <span data-ttu-id="782e0-322">**记住我上次设置的优化选项**</span><span class="sxs-lookup"><span data-stu-id="782e0-322">**Remember my last tuning options**</span></span>  
 <span data-ttu-id="782e0-323">在会话之间保留优化选项。</span><span class="sxs-lookup"><span data-stu-id="782e0-323">Retain tuning options between sessions.</span></span> <span data-ttu-id="782e0-324">默认为选中状态。</span><span class="sxs-lookup"><span data-stu-id="782e0-324">Selected by default.</span></span> <span data-ttu-id="782e0-325">如果清除此复选框，则总是使用数据库引擎优化顾问默认值启动。</span><span class="sxs-lookup"><span data-stu-id="782e0-325">Clear this check box to always start with the Database Engine Tuning Advisor defaults.</span></span>  
  
 <span data-ttu-id="782e0-326">**在永久删除会话之前询问**</span><span class="sxs-lookup"><span data-stu-id="782e0-326">**Ask before permanently deleting sessions**</span></span>  
 <span data-ttu-id="782e0-327">在删除会话之前显示确认对话框。</span><span class="sxs-lookup"><span data-stu-id="782e0-327">Display a confirmation dialog box before deleting sessions.</span></span>  
  
 <span data-ttu-id="782e0-328">**在停止会话分析之前询问**</span><span class="sxs-lookup"><span data-stu-id="782e0-328">**Ask before stopping session analysis**</span></span>  
 <span data-ttu-id="782e0-329">在停止工作负荷分析之前，显示确认对话框。</span><span class="sxs-lookup"><span data-stu-id="782e0-329">Display a confirmation dialog box before stopping analysis of a workload.</span></span>  
  
#### <a name="general-tab-options"></a><span data-ttu-id="782e0-330">“常规”选项卡选项</span><span class="sxs-lookup"><span data-stu-id="782e0-330">General Tab Options</span></span>  
 <span data-ttu-id="782e0-331">在启动优化会话之前，必须配置 **“常规”** 选项卡中的字段。</span><span class="sxs-lookup"><span data-stu-id="782e0-331">You must configure the fields in the **General** tab before starting a tuning session.</span></span> <span data-ttu-id="782e0-332">在启动优化会话之前，无需修改 **“优化选项”** 选项卡的设置。</span><span class="sxs-lookup"><span data-stu-id="782e0-332">You do not have to modify the settings of the **Tuning Options** tab before starting a tuning session.</span></span>  
  
 <span data-ttu-id="782e0-333">**“会话名称”**</span><span class="sxs-lookup"><span data-stu-id="782e0-333">**Session name**</span></span>  
 <span data-ttu-id="782e0-334">指定会话的名称。</span><span class="sxs-lookup"><span data-stu-id="782e0-334">Specify a name for the session.</span></span> <span data-ttu-id="782e0-335">会话名称将名称与优化会话相关联。</span><span class="sxs-lookup"><span data-stu-id="782e0-335">The session name associates a name with a tuning session.</span></span> <span data-ttu-id="782e0-336">此后，您可以通过引用此名称来查看优化会话。</span><span class="sxs-lookup"><span data-stu-id="782e0-336">You can refer to this name to review the tuning session later.</span></span>  
  
 <span data-ttu-id="782e0-337">**File**</span><span class="sxs-lookup"><span data-stu-id="782e0-337">**File**</span></span>  
 <span data-ttu-id="782e0-338">为工作负荷指定 .sql 脚本或跟踪文件。</span><span class="sxs-lookup"><span data-stu-id="782e0-338">Specify a .sql script or trace file for a workload.</span></span> <span data-ttu-id="782e0-339">在关联的文本框中指定路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="782e0-339">Specify the path and filename in the associated text box.</span></span> <span data-ttu-id="782e0-340">数据库引擎优化顾问假定工作负荷跟踪文件是滚动更新文件。</span><span class="sxs-lookup"><span data-stu-id="782e0-340">Database Engine Tuning Advisor assumes that the workload trace file is a rollover file.</span></span> <span data-ttu-id="782e0-341">有关滚动更新文件的详细信息，请参阅 [Limit Trace File and Table Sizes](../sql-trace/limit-trace-file-and-table-sizes.md)。</span><span class="sxs-lookup"><span data-stu-id="782e0-341">For more information about rollover files, see [Limit Trace File and Table Sizes](../sql-trace/limit-trace-file-and-table-sizes.md).</span></span>  
  
 <span data-ttu-id="782e0-342">**表**</span><span class="sxs-lookup"><span data-stu-id="782e0-342">**Table**</span></span>  
 <span data-ttu-id="782e0-343">为工作负荷指定跟踪表。</span><span class="sxs-lookup"><span data-stu-id="782e0-343">Specify a trace table for a workload.</span></span> <span data-ttu-id="782e0-344">在关联的文本框中指定跟踪表的完全限定名称，如下所示：</span><span class="sxs-lookup"><span data-stu-id="782e0-344">Specify the fully qualified name of the trace table in the associated text box as follows:</span></span>  
  
```  
database_name.owner_name.table_name  
```  
  
-   <span data-ttu-id="782e0-345">确保在将跟踪表用作工作负荷之前已经停止了跟踪。</span><span class="sxs-lookup"><span data-stu-id="782e0-345">Make sure that tracing has stopped before using a trace table as a workload.</span></span>  
  
-   <span data-ttu-id="782e0-346">该跟踪表必须位于数据库引擎优化顾问正在优化的同一台服务器上。</span><span class="sxs-lookup"><span data-stu-id="782e0-346">The trace table must exist on the same server that Database Engine Tuning Advisor is tuning.</span></span> <span data-ttu-id="782e0-347">如果在其他服务器上创建了跟踪表，则将该跟踪表移动到数据库引擎优化顾问正在优化的服务器。</span><span class="sxs-lookup"><span data-stu-id="782e0-347">If you create the trace table on a different server, then move it to the server that Database Engine Tuning Advisor is tuning.</span></span>  
  
 <span data-ttu-id="782e0-348">**“计划缓存”**</span><span class="sxs-lookup"><span data-stu-id="782e0-348">**Plan Cache**</span></span>  
 <span data-ttu-id="782e0-349">将计划缓存指定为工作负荷。</span><span class="sxs-lookup"><span data-stu-id="782e0-349">Specify the plan cache as a workload.</span></span> <span data-ttu-id="782e0-350">这样，可以避免手动创建工作负荷。</span><span class="sxs-lookup"><span data-stu-id="782e0-350">By doing this, you can avoid having to manually create a workload.</span></span> <span data-ttu-id="782e0-351">数据库引擎优化顾问将选择前 1,000 个事件用于分析。</span><span class="sxs-lookup"><span data-stu-id="782e0-351">Database Engine Tuning Advisor selects the top 1,000 events to use for analysis.</span></span>  
  
 <span data-ttu-id="782e0-352">**Xml**</span><span class="sxs-lookup"><span data-stu-id="782e0-352">**Xml**</span></span>  
 <span data-ttu-id="782e0-353">除非您从 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中导入了工作负荷查询，否则不会显示此项。</span><span class="sxs-lookup"><span data-stu-id="782e0-353">This does not appear unless you import a workload query from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="782e0-354">若要从 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中导入工作负荷查询，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="782e0-354">To import a workload query from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]:</span></span>  
  
1.  <span data-ttu-id="782e0-355">在查询编辑器中键入查询并突出显示该查询。</span><span class="sxs-lookup"><span data-stu-id="782e0-355">Type a query into Query Editor and highlight it.</span></span>  
  
2.  <span data-ttu-id="782e0-356">右键单击突出显示的查询，并单击“在数据库引擎优化顾问中分析查询”。</span><span class="sxs-lookup"><span data-stu-id="782e0-356">Right-click the highlighted query and click **Analyze Query in Database Engine Tuning Advisor**.</span></span>  
  
 <span data-ttu-id="782e0-357">**查找工作负荷文件或查找工作负荷表**</span><span class="sxs-lookup"><span data-stu-id="782e0-357">**Browse for a workload [file or table]**</span></span>  
 <span data-ttu-id="782e0-358">选择“文件”或“表”作为工作负荷源时，请使用此浏览按钮选择目标。</span><span class="sxs-lookup"><span data-stu-id="782e0-358">When **File** or **Table** is selected as the workload source, use this browse button to select the target.</span></span>  
  
 <span data-ttu-id="782e0-359">**预览 XML 工作负荷**</span><span class="sxs-lookup"><span data-stu-id="782e0-359">**Preview the XML workload**</span></span>  
 <span data-ttu-id="782e0-360">查看从 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中导出的 XML 格式的工作负荷。</span><span class="sxs-lookup"><span data-stu-id="782e0-360">View an XML-formatted workload that has been imported from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="782e0-361">**用于工作负荷分析的数据库**</span><span class="sxs-lookup"><span data-stu-id="782e0-361">**Database for workload analysis**</span></span>  
 <span data-ttu-id="782e0-362">指定数据库引擎优化顾问在优化工作负荷时连接的第一个数据库。</span><span class="sxs-lookup"><span data-stu-id="782e0-362">Specify the first database to which Database Engine Tuning Advisor connects when tuning a workload.</span></span> <span data-ttu-id="782e0-363">优化开始之后，数据库引擎优化顾问连接到由工作负荷中包含的 `USE DATABASE` 语句所指定的数据库。</span><span class="sxs-lookup"><span data-stu-id="782e0-363">After tuning begins, Database Engine Tuning Advisor connects to the databases specified by the `USE DATABASE` statements contained in the workload.</span></span>  
  
 <span data-ttu-id="782e0-364">**选择要优化的数据库和表**</span><span class="sxs-lookup"><span data-stu-id="782e0-364">**Select databases and tables to tune**</span></span>  
 <span data-ttu-id="782e0-365">指定要优化的数据库和表。</span><span class="sxs-lookup"><span data-stu-id="782e0-365">Specify the databases and tables to be tuned.</span></span> <span data-ttu-id="782e0-366">若要指定所有数据库，请选中 **“名称”** 列标题中的复选框。</span><span class="sxs-lookup"><span data-stu-id="782e0-366">To specify all of the databases, select the check box in the **Name** column heading.</span></span> <span data-ttu-id="782e0-367">若要指定特定数据库，请选中数据库名称旁的复选框。</span><span class="sxs-lookup"><span data-stu-id="782e0-367">To specify certain databases, select the check box next to the database name.</span></span> <span data-ttu-id="782e0-368">默认情况下，选定数据库的所有表都自动包括在优化会话中。</span><span class="sxs-lookup"><span data-stu-id="782e0-368">By default, all of the tables for selected databases are automatically included in the tuning session.</span></span> <span data-ttu-id="782e0-369">如果要使优化会话不包括某些表，请单击 **“选定的表”** 列中的箭头，再清除不希望优化的表旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="782e0-369">To exclude tables, click the arrow in the **Selected Tables** column, and then clear the check boxes next to the tables that you do not want to tune.</span></span>  
  
 <span data-ttu-id="782e0-370">“所选表”下箭头</span><span class="sxs-lookup"><span data-stu-id="782e0-370">**Selected Tables** down arrow</span></span>  
 <span data-ttu-id="782e0-371">展开表列表以允许选择个别表进行优化。</span><span class="sxs-lookup"><span data-stu-id="782e0-371">Expand the tables list to allow selecting individual tables for tuning.</span></span>  
  
 <span data-ttu-id="782e0-372">**“保存优化日志”**</span><span class="sxs-lookup"><span data-stu-id="782e0-372">**Save tuning log**</span></span>  
 <span data-ttu-id="782e0-373">在会话期间创建日志并记录错误。</span><span class="sxs-lookup"><span data-stu-id="782e0-373">Create a log and record errors during the session.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="782e0-374">数据库引擎优化顾问不会自动更新 **“常规”** 选项卡上所显示表的行信息。相反，它依赖于数据库中的元数据。</span><span class="sxs-lookup"><span data-stu-id="782e0-374">Database Engine Tuning Advisor does not automatically update the rows information for the tables displayed on the **General** tab. Instead it relies upon the metadata in the database.</span></span> <span data-ttu-id="782e0-375">如果怀疑行信息过时，请对相关的对象运行 DBCC UPDATEUSAGE 命令。</span><span class="sxs-lookup"><span data-stu-id="782e0-375">If you suspect that the rows information is outdated, run the DBCC UPDATEUSAGE command for the relevant objects.</span></span>  
  
##### <a name="tuning-tab-options"></a><span data-ttu-id="782e0-376">“优化”选项卡选项</span><span class="sxs-lookup"><span data-stu-id="782e0-376">Tuning Tab Options</span></span>  
 <span data-ttu-id="782e0-377">使用 **“优化选项”** 选项卡可以修改常规优化选项的默认设置。</span><span class="sxs-lookup"><span data-stu-id="782e0-377">Use the **Tuning Options** tab to modify default settings of general tuning options.</span></span> <span data-ttu-id="782e0-378">在启动优化会话之前，无需修改 **“优化选项”** 选项卡的设置。</span><span class="sxs-lookup"><span data-stu-id="782e0-378">You do not have to modify the settings of the **Tuning Options** tab before starting a tuning session.</span></span>  
  
 <span data-ttu-id="782e0-379">**限制优化时间**</span><span class="sxs-lookup"><span data-stu-id="782e0-379">**Limit tuning time**</span></span>  
 <span data-ttu-id="782e0-380">限制当前优化会话的时间。</span><span class="sxs-lookup"><span data-stu-id="782e0-380">Limits the time for the current tuning session.</span></span> <span data-ttu-id="782e0-381">提供更多优化时间可以提高建议质量。</span><span class="sxs-lookup"><span data-stu-id="782e0-381">Providing more time for turning improves the quality of the recommendations.</span></span> <span data-ttu-id="782e0-382">为了确保获取最佳的建议，请不要选中此选项。</span><span class="sxs-lookup"><span data-stu-id="782e0-382">To ensure the best recommendations, do not select this option.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="782e0-383">优化顾问在分析期间会占用系统资源。</span><span class="sxs-lookup"><span data-stu-id="782e0-383">Tuning Advisor consumes system resources during analysis.</span></span> <span data-ttu-id="782e0-384">使用 **“限制优化时间”** 会在对服务器上预期的高工作负荷进行优化之前停止优化。</span><span class="sxs-lookup"><span data-stu-id="782e0-384">Use **Limit tuning time** to stop tuning before periods of anticipated heavy workload on the server being tuned.</span></span>  
  
 <span data-ttu-id="782e0-385">**“高级选项”**</span><span class="sxs-lookup"><span data-stu-id="782e0-385">**Advanced Options**</span></span>  
 <span data-ttu-id="782e0-386">使用“高级优化选项”对话框可以配置有关最大空间、最大键列数和联机索引的建议设置。</span><span class="sxs-lookup"><span data-stu-id="782e0-386">Use the **Advanced Tuning Options** dialog box to configure the maximum space, maximum key columns, and online index recommendations.</span></span>  
  
 <span data-ttu-id="782e0-387">**定义建议所用的最大空间(MB)**</span><span class="sxs-lookup"><span data-stu-id="782e0-387">**Define max. space for recommendations (MB)**</span></span>  
 <span data-ttu-id="782e0-388">键入数据库引擎优化顾问建议的供物理设计结构使用的最大空间量。</span><span class="sxs-lookup"><span data-stu-id="782e0-388">Type the maximum amount of space to be used by physical design structures recommended by Database Engine Tuning Advisor.</span></span>  
  
 <span data-ttu-id="782e0-389">如果没有在此处输入值，则数据库引擎优化顾问将假定为以下空间限制中的较小者：</span><span class="sxs-lookup"><span data-stu-id="782e0-389">If no value is entered here, Database Engine Tuning Advisor assumes the smaller of the following space limits:</span></span>  
  
-   <span data-ttu-id="782e0-390">当前原始数据大小的三倍，包括数据库中表的堆和聚集索引的总大小。</span><span class="sxs-lookup"><span data-stu-id="782e0-390">Three times the current raw data size, which includes the total size of heaps and clustered indexes on tables in the database.</span></span>  
  
-   <span data-ttu-id="782e0-391">所有已附连磁盘驱动器的可用空间加上原始数据的大小。</span><span class="sxs-lookup"><span data-stu-id="782e0-391">The free space on all attached disk drives plus the raw data size.</span></span>  
  
 <span data-ttu-id="782e0-392">**“包括来自所有数据库的计划缓存事件”**</span><span class="sxs-lookup"><span data-stu-id="782e0-392">**Include plan cache events from all databases**</span></span>  
 <span data-ttu-id="782e0-393">指定将分析来自所有数据库的计划缓存事件。</span><span class="sxs-lookup"><span data-stu-id="782e0-393">Specify that plan cache events from all databases are analyzed.</span></span>  
  
 <span data-ttu-id="782e0-394">**每个索引的最大列数**</span><span class="sxs-lookup"><span data-stu-id="782e0-394">**Max. columns per index**</span></span>  
 <span data-ttu-id="782e0-395">指定任一索引中可包括的最大列数。</span><span class="sxs-lookup"><span data-stu-id="782e0-395">Specify the maximum number of columns to include in any index.</span></span> <span data-ttu-id="782e0-396">默认值为 1023。</span><span class="sxs-lookup"><span data-stu-id="782e0-396">The default is 1023.</span></span>  
  
 <span data-ttu-id="782e0-397">**所有建议均为脱机建议**</span><span class="sxs-lookup"><span data-stu-id="782e0-397">**All recommendations are offline**</span></span>  
 <span data-ttu-id="782e0-398">生成可能的最佳建议，但不建议联机创建任何物理设计结构。</span><span class="sxs-lookup"><span data-stu-id="782e0-398">Generate the best recommendations possible, but do not recommend that any physical design structures be created online.</span></span>  
  
 <span data-ttu-id="782e0-399">**如果可能，则生成联机建议**</span><span class="sxs-lookup"><span data-stu-id="782e0-399">**Generate online recommendations where possible**</span></span>  
 <span data-ttu-id="782e0-400">在创建 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句以实现建议时，即使可以使用更快的脱机方法，也选用可以在服务器上联机实现的方法。</span><span class="sxs-lookup"><span data-stu-id="782e0-400">When creating [!INCLUDE[tsql](../../includes/tsql-md.md)] statements to implement the recommendations, choose methods that can be implemented with the server online, even if a faster offline method is available.</span></span>  
  
 <span data-ttu-id="782e0-401">**仅生成联机建议**</span><span class="sxs-lookup"><span data-stu-id="782e0-401">**Generate only online recommendations**</span></span>  
 <span data-ttu-id="782e0-402">仅生成允许服务器保持联机的建议。</span><span class="sxs-lookup"><span data-stu-id="782e0-402">Only make recommendations that allow the server to stay online.</span></span>  
  
 <span data-ttu-id="782e0-403">**结束时间**</span><span class="sxs-lookup"><span data-stu-id="782e0-403">**Stop at**</span></span>  
 <span data-ttu-id="782e0-404">提供 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 优化顾问的结束日期和时间。</span><span class="sxs-lookup"><span data-stu-id="782e0-404">Provide the date and time when [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor should stop.</span></span>  
  
 <span data-ttu-id="782e0-405">**索引和索引视图**</span><span class="sxs-lookup"><span data-stu-id="782e0-405">**Indexes and indexed views**</span></span>  
 <span data-ttu-id="782e0-406">选中此框可包括添加聚集索引、非聚集索引和索引视图建议。</span><span class="sxs-lookup"><span data-stu-id="782e0-406">Check this box to include recommendations for adding clustered indexes, nonclustered indexes, and indexed views.</span></span>  
  
 <span data-ttu-id="782e0-407">**索引视图**</span><span class="sxs-lookup"><span data-stu-id="782e0-407">**Indexed views**</span></span>  
 <span data-ttu-id="782e0-408">只包括添加索引视图建议。</span><span class="sxs-lookup"><span data-stu-id="782e0-408">Only include recommendations for adding indexed views.</span></span> <span data-ttu-id="782e0-409">不会为聚集和非聚集索引提供建议。</span><span class="sxs-lookup"><span data-stu-id="782e0-409">Clustered and nonclustered indexes will not be recommended.</span></span>  
  
 <span data-ttu-id="782e0-410">**包括筛选的索引**</span><span class="sxs-lookup"><span data-stu-id="782e0-410">**Include filtered indexes**</span></span>  
 <span data-ttu-id="782e0-411">包括用来添加筛选索引的建议。</span><span class="sxs-lookup"><span data-stu-id="782e0-411">Include recommendations for adding filtered indexes.</span></span> <span data-ttu-id="782e0-412">如果选择下列物理设计结构之一，则此选项可用：索引和索引视图、索引或非聚集索引  。</span><span class="sxs-lookup"><span data-stu-id="782e0-412">This option is available if you select one of these physical design structures: **Indexes and indexed views**, **Indexes**, or **Nonclustered indexes**.</span></span>  
  
 <span data-ttu-id="782e0-413">**索引**</span><span class="sxs-lookup"><span data-stu-id="782e0-413">**Indexes**</span></span>  
 <span data-ttu-id="782e0-414">只包括添加聚集和非聚集索引建议。</span><span class="sxs-lookup"><span data-stu-id="782e0-414">Only include recommendations for adding clustered and nonclustered indexes.</span></span> <span data-ttu-id="782e0-415">不会为索引视图提供建议。</span><span class="sxs-lookup"><span data-stu-id="782e0-415">Indexed views will not be recommended.</span></span>  
  
 <span data-ttu-id="782e0-416">**“非聚集索引”**</span><span class="sxs-lookup"><span data-stu-id="782e0-416">**Nonclustered indexes**</span></span>  
 <span data-ttu-id="782e0-417">只包括对非聚集索引的建议。</span><span class="sxs-lookup"><span data-stu-id="782e0-417">Include recommendations for only nonclustered indexes.</span></span> <span data-ttu-id="782e0-418">不会为聚集索引和索引视图提供建议。</span><span class="sxs-lookup"><span data-stu-id="782e0-418">Clustered indexes and indexed views will not be recommended.</span></span>  
  
 <span data-ttu-id="782e0-419">**仅计算现有 PDS 的使用率**</span><span class="sxs-lookup"><span data-stu-id="782e0-419">**Evaluate utilization of existing PDS only**</span></span>  
 <span data-ttu-id="782e0-420">评估当前索引的效用，但不会为其他索引或索引视图提供建议。</span><span class="sxs-lookup"><span data-stu-id="782e0-420">Evaluate the effectiveness of the current indexes but do not recommend additional indexes or indexed views.</span></span>  
  
 <span data-ttu-id="782e0-421">**不分区**</span><span class="sxs-lookup"><span data-stu-id="782e0-421">**No partitioning**</span></span>  
 <span data-ttu-id="782e0-422">不提供分区建议。</span><span class="sxs-lookup"><span data-stu-id="782e0-422">Do not recommend partitioning.</span></span>  
  
 <span data-ttu-id="782e0-423">**完全分区**</span><span class="sxs-lookup"><span data-stu-id="782e0-423">**Full partitioning**</span></span>  
 <span data-ttu-id="782e0-424">包含分区建议。</span><span class="sxs-lookup"><span data-stu-id="782e0-424">Include recommendations for partitioning.</span></span>  
  
 <span data-ttu-id="782e0-425">**对齐分区**</span><span class="sxs-lookup"><span data-stu-id="782e0-425">**Aligned partitioning**</span></span>  
 <span data-ttu-id="782e0-426">将对齐新建议的分区以便于维护。</span><span class="sxs-lookup"><span data-stu-id="782e0-426">New recommended partitions will be aligned to make partitions easy to maintain.</span></span>  
  
 <span data-ttu-id="782e0-427">**不保留任何现有 PDS**</span><span class="sxs-lookup"><span data-stu-id="782e0-427">**Do not keep any existing PDS**</span></span>  
 <span data-ttu-id="782e0-428">建议删除不必要的现有索引、视图和分区。</span><span class="sxs-lookup"><span data-stu-id="782e0-428">Recommend dropping unnecessary existing indexes, views, and partitioning.</span></span> <span data-ttu-id="782e0-429">如果现有物理设计结构 (PDS) 对工作负荷有用， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 优化顾问会建议不要删除该结构。</span><span class="sxs-lookup"><span data-stu-id="782e0-429">If an existing physical design structure (PDS) is useful to the workload, [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor does not recommend dropping it.</span></span>  
  
 <span data-ttu-id="782e0-430">**仅保留索引**</span><span class="sxs-lookup"><span data-stu-id="782e0-430">**Keep indexes only**</span></span>  
 <span data-ttu-id="782e0-431">保留所有现有索引，但建议删除不必要的索引视图和分区。</span><span class="sxs-lookup"><span data-stu-id="782e0-431">Keep all existing indexes but recommend dropping unnecessary indexed views, and partitioning.</span></span>  
  
 <span data-ttu-id="782e0-432">**保留所有现有 PDS**</span><span class="sxs-lookup"><span data-stu-id="782e0-432">**Keep all existing PDS**</span></span>  
 <span data-ttu-id="782e0-433">保留所有现有索引、索引视图和分区。</span><span class="sxs-lookup"><span data-stu-id="782e0-433">Keep all existing indexes, indexed views, and partitioning.</span></span>  
  
 <span data-ttu-id="782e0-434">**仅保留聚集索引**</span><span class="sxs-lookup"><span data-stu-id="782e0-434">**Keep clustered indexes only**</span></span>  
 <span data-ttu-id="782e0-435">保留所有现有聚集索引，但建议删除不必要的索引视图、分区和非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="782e0-435">Keep all existing clustered indexes but recommend dropping unnecessary indexed views, partitions, and nonclustered indexes.</span></span>  
  
 <span data-ttu-id="782e0-436">**保留对齐分区**</span><span class="sxs-lookup"><span data-stu-id="782e0-436">**Keep aligned partitioning**</span></span>  
 <span data-ttu-id="782e0-437">保留当前对齐的分区结构，但建议删除不必要的索引视图、索引和未对齐的分区。</span><span class="sxs-lookup"><span data-stu-id="782e0-437">Keep partitioning structures that are currently aligned, but recommend dropping unnecessary indexed views, indexes, and non-aligned partitioning.</span></span> <span data-ttu-id="782e0-438">建议的其他任何分区将与当前分区方案对齐。</span><span class="sxs-lookup"><span data-stu-id="782e0-438">Any additional partitioning recommended will align with the current partitioning scheme.</span></span>  
  
###### <a name="progress-tab-options"></a><span data-ttu-id="782e0-439">“进度”选项卡选项</span><span class="sxs-lookup"><span data-stu-id="782e0-439">Progress Tab Options</span></span>  
 <span data-ttu-id="782e0-440">数据库引擎优化顾问开始分析工作负荷后，会显示数据库引擎优化顾问的 **“进度”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="782e0-440">The **Progress** tab of Database Engine Tuning Advisor appears after Database Engine Tuning Advisor begins analyzing a workload.</span></span>  
  
 <span data-ttu-id="782e0-441">如果希望停止已经启动的优化会话，请在 **“操作”** 菜单上选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="782e0-441">If you want to stop the tuning session after it has started, choose one of the following options on the **Actions** menu:</span></span>  
  
-   <span data-ttu-id="782e0-442">选择“停止分析（并提供建议）”将停止优化会话，并提示你选择是否希望数据库引擎优化顾问根据目前已完成的分析来生成建议。</span><span class="sxs-lookup"><span data-stu-id="782e0-442">**Stop Analysis (With Recommendations)** stops the tuning session and prompts you to decide whether you want Database Engine Tuning Advisor to generate recommendations based on the analysis done up to this point.</span></span>  
  
-   <span data-ttu-id="782e0-443">选择 **“停止分析”** 将停止优化会话而不生成任何建议。</span><span class="sxs-lookup"><span data-stu-id="782e0-443">**Stop Analysis** stops the tuning session without generating any recommendations.</span></span>  
  
 <span data-ttu-id="782e0-444">**优化进度**</span><span class="sxs-lookup"><span data-stu-id="782e0-444">**Tuning Progress**</span></span>  
 <span data-ttu-id="782e0-445">指示进度的当前状态。</span><span class="sxs-lookup"><span data-stu-id="782e0-445">Indicates the current status of the progress.</span></span> <span data-ttu-id="782e0-446">其中包含已执行操作的数量，以及接收到的错误、成功和警告消息的数量。</span><span class="sxs-lookup"><span data-stu-id="782e0-446">Contains the number of actions performed, and the number of error, success, and warning messages received.</span></span>  
  
 <span data-ttu-id="782e0-447">**详细信息**</span><span class="sxs-lookup"><span data-stu-id="782e0-447">**Details**</span></span>  
 <span data-ttu-id="782e0-448">包含指示状态的图标。</span><span class="sxs-lookup"><span data-stu-id="782e0-448">Contains an icon indicating status.</span></span>  
  
 <span data-ttu-id="782e0-449">**Action**</span><span class="sxs-lookup"><span data-stu-id="782e0-449">**Action**</span></span>  
 <span data-ttu-id="782e0-450">显示正在执行的步骤。</span><span class="sxs-lookup"><span data-stu-id="782e0-450">Displays the steps being performed.</span></span>  
  
 <span data-ttu-id="782e0-451">**Status**</span><span class="sxs-lookup"><span data-stu-id="782e0-451">**Status**</span></span>  
 <span data-ttu-id="782e0-452">显示操作步骤的状态。</span><span class="sxs-lookup"><span data-stu-id="782e0-452">Displays the status of the action step.</span></span>  
  
 <span data-ttu-id="782e0-453">**消息**</span><span class="sxs-lookup"><span data-stu-id="782e0-453">**Message**</span></span>  
 <span data-ttu-id="782e0-454">包含操作步骤返回的所有消息。</span><span class="sxs-lookup"><span data-stu-id="782e0-454">Contains any messages returned by the action steps.</span></span>  
  
 <span data-ttu-id="782e0-455">**优化日志**</span><span class="sxs-lookup"><span data-stu-id="782e0-455">**Tuning Log**</span></span>  
 <span data-ttu-id="782e0-456">包含与此优化会话有关的信息。</span><span class="sxs-lookup"><span data-stu-id="782e0-456">Contains information regarding this tuning session.</span></span> <span data-ttu-id="782e0-457">若要打印此日志，请右键单击此日志，再单击“打印”。</span><span class="sxs-lookup"><span data-stu-id="782e0-457">To print this log, right-click the log, and then click **Print**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="782e0-458">另请参阅</span><span class="sxs-lookup"><span data-stu-id="782e0-458">See Also</span></span>  
 <span data-ttu-id="782e0-459">[查看和使用数据库引擎优化顾问的输出](database-engine-tuning-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="782e0-459">[View and Work with the Output from the Database Engine Tuning Advisor](database-engine-tuning-advisor.md) </span></span>  
 [<span data-ttu-id="782e0-460">dta 实用工具</span><span class="sxs-lookup"><span data-stu-id="782e0-460">dta Utility</span></span>](../../tools/dta/dta-utility.md)  
  
  
