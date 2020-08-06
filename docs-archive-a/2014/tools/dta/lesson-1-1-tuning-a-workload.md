---
title: 优化工作负荷 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- workloads [SQL Server], tuning
ms.assetid: 6229bf3f-1182-4bc6-8451-cedc37f4b62e
author: stevestein
ms.author: sstein
ms.openlocfilehash: f95aab55d402ac72228dcc4326ad00ea15e7471f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690970"
---
# <a name="tuning-a-workload"></a><span data-ttu-id="6a607-102">优化工作负荷</span><span class="sxs-lookup"><span data-stu-id="6a607-102">Tuning a Workload</span></span>
  <span data-ttu-id="6a607-103">可以使用数据库引擎优化顾问，针对您选择进行优化的数据库和表来找到查询性能最佳的物理数据库设计。</span><span class="sxs-lookup"><span data-stu-id="6a607-103">The Database Engine Tuning Advisor can be used to find the best physical database design for query performance on the databases and tables that you select for tuning.</span></span>  
  
 <span data-ttu-id="6a607-104">此任务使用 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="6a607-104">This task uses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="6a607-105">为了增强安全性，默认情况下不会安装示例数据库。</span><span class="sxs-lookup"><span data-stu-id="6a607-105">To enhance security, the sample databases are not installed by default.</span></span> <span data-ttu-id="6a607-106">若要安装示例数据库，请参阅 [安装 SQL Server 示例和示例数据库](http://sqlserversamples.codeplex.com)。</span><span class="sxs-lookup"><span data-stu-id="6a607-106">To install the sample databases, see [Installing SQL Server Samples and Sample Databases](http://sqlserversamples.codeplex.com).</span></span>  
  
### <a name="tune-a-workload-transact-sql-script-file"></a><span data-ttu-id="6a607-107">优化工作负荷 Transact-SQL 脚本文件</span><span class="sxs-lookup"><span data-stu-id="6a607-107">Tune a workload Transact-SQL script file</span></span>  
  
1.  <span data-ttu-id="6a607-108">从</span><span class="sxs-lookup"><span data-stu-id="6a607-108">Copy a sample SELECT statement or statements from "A.</span></span> <span data-ttu-id="6a607-109">[SELECT 示例 (Transact-SQL)](/sql/t-sql/queries/select-examples-transact-sql) 中的“A. 使用 SELECT 检索行和列”复制示例 SELECT 语句或语句，并将语句粘贴到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的查询编辑器中。</span><span class="sxs-lookup"><span data-stu-id="6a607-109">Using SELECT to retrieve rows and columns" in [SELECT Examples &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-examples-transact-sql) and paste the statements into the Query Editor of [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="6a607-110">将该文件保存为 MyScript.sql\*\*\*\*，并存储在可以轻松找到的目录中。</span><span class="sxs-lookup"><span data-stu-id="6a607-110">Save the file as **MyScript.sql** in a directory where you can easily find it.</span></span>  
  
2.  <span data-ttu-id="6a607-111">启动数据库引擎优化顾问。</span><span class="sxs-lookup"><span data-stu-id="6a607-111">Start Database Engine Tuning Advisor.</span></span> <span data-ttu-id="6a607-112">请参阅 [启动数据库引擎优化顾问](../../relational-databases/performance/database-engine-tuning-advisor.md)。</span><span class="sxs-lookup"><span data-stu-id="6a607-112">See [Launching Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md).</span></span>  
  
3.  <span data-ttu-id="6a607-113">在数据库引擎优化顾问 GUI 右窗格的“会话名称”\*\*\*\* 中，键入 **MySession**。</span><span class="sxs-lookup"><span data-stu-id="6a607-113">In the right pane of the Database Engine Tuning Advisor GUI, type **MySession** in **Session name**.</span></span>  
  
4.  <span data-ttu-id="6a607-114">针对“工作负荷”\*\*\*\* 选择“文件”\*\*\*\*，再单击“查找工作负荷文件”\*\*\*\* 按钮，以查找在步骤 1 中保存的 **MyScript.sql** 文件。</span><span class="sxs-lookup"><span data-stu-id="6a607-114">Select **File** for your **Workload**, and click the **Browse for a workload file** button to locate the **MyScript.sql** file that you saved in Step 1.</span></span>  
  
5.  <span data-ttu-id="6a607-115">在“用于工作负荷分析的数据库”\*\*\*\* 列表中选择 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]，或在“选择要优化的数据库和表”\*\*\*\* 网格中选择 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]，使“保存优化日志”\*\*\*\* 保持选中状态。</span><span class="sxs-lookup"><span data-stu-id="6a607-115">Select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] in the **Database for workload analysis** list, select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] in the **Select databases and tables to tune** grid, and leave **Save tuning log** selected.</span></span> <span data-ttu-id="6a607-116">“用于工作负荷分析的数据库”\*\*\*\* 指定数据库引擎优化顾问在优化工作负荷时连接到的第一个数据库。</span><span class="sxs-lookup"><span data-stu-id="6a607-116">**Database for workload analysis** specifies the first database to which Database Engine Tuning Advisor connects when tuning a workload.</span></span> <span data-ttu-id="6a607-117">优化开始之后，数据库引擎优化顾问连接到由工作负荷中包含的 `USE DATABASE` 语句所指定的数据库。</span><span class="sxs-lookup"><span data-stu-id="6a607-117">After tuning begins, Database Engine Tuning Advisor connects to the databases specified by the `USE DATABASE` statements contained in the workload.</span></span>  
  
6.  <span data-ttu-id="6a607-118">单击 "**优化选项**" 选项卡。你不会为此练习设置任何优化选项，但请花些时间来查看默认的优化选项。</span><span class="sxs-lookup"><span data-stu-id="6a607-118">Click the **Tuning Options** tab. You will not set any tuning options for this practice, but take a moment to review the default tuning options.</span></span> <span data-ttu-id="6a607-119">按 F1 键可查看该选项卡式页面的帮助。</span><span class="sxs-lookup"><span data-stu-id="6a607-119">Press F1 to view the Help for this tabbed page.</span></span> <span data-ttu-id="6a607-120">单击“高级选项”\*\*\*\* 可查看其他的优化选项。</span><span class="sxs-lookup"><span data-stu-id="6a607-120">Click **Advanced Options** to view additional tuning options.</span></span> <span data-ttu-id="6a607-121">请在“高级优化选项”\*\*\*\* 对话框中单击“帮助”\*\*\*\*，以了解有关此处所显示的优化选项的信息。</span><span class="sxs-lookup"><span data-stu-id="6a607-121">Click **Help** in the **Advanced Tuning Options** dialog box for information about the tuning options that are displayed there.</span></span> <span data-ttu-id="6a607-122">单击“取消”\*\*\*\* 关闭“高级优化选项”\*\*\*\* 对话框，并保留选中默认选项。</span><span class="sxs-lookup"><span data-stu-id="6a607-122">Click **Cancel** to close the **Advanced Tuning Options** dialog box, leaving the default options selected.</span></span>  
  
7.  <span data-ttu-id="6a607-123">在工具栏中，单击 **“开始分析”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="6a607-123">Click the **Start Analysis** button on the toolbar.</span></span> <span data-ttu-id="6a607-124">数据库引擎优化顾问分析工作负荷时，可以在 "**进度**" 选项卡上监视状态。优化完成后，将显示 "**建议**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="6a607-124">While Database Engine Tuning Advisor is analyzing the workload, you can monitor the status on the **Progress** tab. When tuning is complete, the **Recommendations** tab is displayed.</span></span>  
  
     <span data-ttu-id="6a607-125">如果收到有关优化结束日期和时间的错误，请检查主 "**优化选项**" 选项卡上的 "**停止**时间"。确保 "**停止**日期和时间" 大于当前日期和时间，如有必要，请更改它们。</span><span class="sxs-lookup"><span data-stu-id="6a607-125">If you receive an error about the tuning stop date and time, check the **Stop at** time on the main **Tuning Options** tab. Make sure the **Stop at** date and time are greater than the current date and time, and if necessary, change them.</span></span>  
  
8.  <span data-ttu-id="6a607-126">分析完成之后，在“操作”\*\*\*\* 菜单中，单击“保存建议”\*\*\*\*，将建议保存为 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本。</span><span class="sxs-lookup"><span data-stu-id="6a607-126">After the analysis completes, save your recommendation as a [!INCLUDE[tsql](../../includes/tsql-md.md)] script by clicking **Save Recommendations** on the **Actions** menu.</span></span> <span data-ttu-id="6a607-127">在“另存为”\*\*\*\* 对话框中，导航到要保存建议脚本的目录，然后键入文件名 **MyRecommendations**。</span><span class="sxs-lookup"><span data-stu-id="6a607-127">In the **Save As** dialog box, navigate to the directory where you want to save the recommendations script, and type the file name **MyRecommendations**.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="6a607-128">摘要</span><span class="sxs-lookup"><span data-stu-id="6a607-128">Summary</span></span>  
 <span data-ttu-id="6a607-129">您已完成对 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库的简单 SELECT 语句工作负荷的优化。</span><span class="sxs-lookup"><span data-stu-id="6a607-129">You have completed tuning a simple SELECT statement workload on the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="6a607-130">数据库引擎优化顾问还可将 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 跟踪文件和表作为优化工作负荷。</span><span class="sxs-lookup"><span data-stu-id="6a607-130">The Database Engine Tuning Advisor can also take [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] trace files and tables as tuning workloads.</span></span> <span data-ttu-id="6a607-131">下一个任务将向您展示如何查看和解释进行优化后所收到的优化建议。</span><span class="sxs-lookup"><span data-stu-id="6a607-131">The next task shows you how to view and interpret the tuning recommendations that you received as a result of the practice tuning.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="6a607-132">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="6a607-132">Next Task in Lesson</span></span>  
 [<span data-ttu-id="6a607-133">查看优化建议</span><span class="sxs-lookup"><span data-stu-id="6a607-133">Viewing Tuning Recommendations</span></span>](lesson-1-2-viewing-tuning-recommendations.md)  
  
  
