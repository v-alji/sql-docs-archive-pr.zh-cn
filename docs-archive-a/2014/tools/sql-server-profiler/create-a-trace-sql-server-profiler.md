---
title: 创建跟踪 (SQL Server Profiler) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], creating
ms.assetid: 0302fa6d-d2b5-43fe-ad70-7a337575b112
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7d73333bbf0ba985ed4952e03584b4e4c130ab6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682508"
---
# <a name="create-a-trace-sql-server-profiler"></a><span data-ttu-id="6dab5-102">创建跟踪 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="6dab5-102">Create a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="6dab5-103">本主题介绍如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 来创建跟踪。</span><span class="sxs-lookup"><span data-stu-id="6dab5-103">This topic describes how to use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to create a trace.</span></span>  
  
### <a name="to-create-a-trace"></a><span data-ttu-id="6dab5-104">创建跟踪</span><span class="sxs-lookup"><span data-stu-id="6dab5-104">To create a trace</span></span>  
  
1.  <span data-ttu-id="6dab5-105">在 **“文件”** 菜单上，单击 **“新建跟踪”** ，并连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="6dab5-105">On the **File** menu, click **New Trace**, and connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="6dab5-106">此时，将显示 **“跟踪属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="6dab5-106">The **Trace Properties** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6dab5-107">如果选中 **“建立连接后立即开始跟踪”** ，就不会显示 **“跟踪属性”** 对话框，而是直接开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="6dab5-107">The **Trace Properties** dialog box fails to appear, and the trace begins instead, if **Start tracing immediately after making connection** is selected.</span></span> <span data-ttu-id="6dab5-108">若要关闭此设置，请在“工具”菜单上，单击“选项”，然后清除“建立连接后立即开始跟踪”复选框。</span><span class="sxs-lookup"><span data-stu-id="6dab5-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="6dab5-109">在 **“跟踪名称”** 框中，键入跟踪的名称。</span><span class="sxs-lookup"><span data-stu-id="6dab5-109">In the **Trace name** box, type a name for the trace.</span></span>  
  
3.  <span data-ttu-id="6dab5-110">在 **“使用模板”** 列表中，为此跟踪选择一个跟踪模板；如果不想使用模板，请选择 **“空白”** 。</span><span class="sxs-lookup"><span data-stu-id="6dab5-110">In the **Use the template** list, select a trace template on which to base the trace, or select **Blank** if you do not want to use a template.</span></span>  
  
4.  <span data-ttu-id="6dab5-111">若要保存跟踪结果，请执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="6dab5-111">To save the trace results, do one of the following:</span></span>  
  
    -   <span data-ttu-id="6dab5-112">单击“保存到文件”\*\*\*\*，将跟踪内容捕获到文件中。</span><span class="sxs-lookup"><span data-stu-id="6dab5-112">Click **Save to file**to capture the trace to a file.</span></span> <span data-ttu-id="6dab5-113">指定 **“设置最大文件大小”** 的值。</span><span class="sxs-lookup"><span data-stu-id="6dab5-113">Specify a value for **Set maximum file size**.</span></span> <span data-ttu-id="6dab5-114">默认值为 5 MB。</span><span class="sxs-lookup"><span data-stu-id="6dab5-114">The default value is 5 megabytes (MB).</span></span>  
  
         <span data-ttu-id="6dab5-115">或者，选择 **“启用文件滚动更新”** ，以便当文件大小达到最大值时自动创建新文件。</span><span class="sxs-lookup"><span data-stu-id="6dab5-115">Optionally, select **Enable file rollover** to automatically create new files when the maximum file size is reached.</span></span> <span data-ttu-id="6dab5-116">也可以选择 **“服务器处理跟踪数据”** ，由正在运行跟踪的服务而不是客户端应用程序来处理跟踪数据。</span><span class="sxs-lookup"><span data-stu-id="6dab5-116">You can also optionally select **Server processes trace data**, which causes the service that is running the trace to process trace data instead of the client application.</span></span> <span data-ttu-id="6dab5-117">在服务器处理跟踪数据时，即使是在压力较大的情况下也不会跳过事件，但是服务器性能可能会受到影响。</span><span class="sxs-lookup"><span data-stu-id="6dab5-117">When the server processes trace data, no events are skipped even under stress conditions, but server performance may be affected.</span></span>  
  
    -   <span data-ttu-id="6dab5-118">单击 **“保存到表”** 将跟踪捕获到数据库表中。</span><span class="sxs-lookup"><span data-stu-id="6dab5-118">Click **Save to table** to capture the trace to a database table.</span></span>  
  
         <span data-ttu-id="6dab5-119">根据需要，可以单击 **“设置最大行数”** ，并指定值。</span><span class="sxs-lookup"><span data-stu-id="6dab5-119">Optionally, click **Set maximum rows**, and specify a value.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="6dab5-120">如果不将跟踪结果保存到文件或表中，则当 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 打开时可以查看跟踪。</span><span class="sxs-lookup"><span data-stu-id="6dab5-120">When you do not save the trace results to a file or table, you can view the trace while [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] is open.</span></span> <span data-ttu-id="6dab5-121">但是，在停止跟踪并关闭 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]之后会丢失跟踪结果。</span><span class="sxs-lookup"><span data-stu-id="6dab5-121">However, you lose the trace results after you stop the trace and close [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="6dab5-122">为了避免这种丢失跟踪结果的情况，可以在关闭 **之前单击** “文件” **菜单上的** “保存” [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]来保存结果。</span><span class="sxs-lookup"><span data-stu-id="6dab5-122">To avoid losing the trace results in this way, click **Save** on the **File** menu to save the results before you close [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
5.  <span data-ttu-id="6dab5-123">根据需要，可以选中 **“启用跟踪停止时间”** 复选框，再指定停止日期和时间。</span><span class="sxs-lookup"><span data-stu-id="6dab5-123">Optionally, select the **Enable trace stop time** check box, and specify a stop date and time.</span></span>  
  
6.  <span data-ttu-id="6dab5-124">若要添加或删除事件、数据列或筛选器，请单击 **“事件选择”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="6dab5-124">To add or remove events, data columns or filters, click the **Events Selection**tab.</span></span> <span data-ttu-id="6dab5-125">有关详细信息，请参阅：[指定跟踪文件的事件和数据列 (SQL Server Profiler)](sql-server-profiler.md)</span><span class="sxs-lookup"><span data-stu-id="6dab5-125">For more information, see: [Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](sql-server-profiler.md)</span></span>  
  
7.  <span data-ttu-id="6dab5-126">单击 **“运行”** 以启动跟踪。</span><span class="sxs-lookup"><span data-stu-id="6dab5-126">Click **Run** to start the trace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dab5-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6dab5-127">See Also</span></span>  
 <span data-ttu-id="6dab5-128">[运行 SQL Server Profiler 所需的权限](permissions-required-to-run-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="6dab5-128">[Permissions Required to Run SQL Server Profiler](permissions-required-to-run-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="6dab5-129">[SQL Server Profiler 模板和权限](sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="6dab5-129">[SQL Server Profiler Templates and Permissions](sql-server-profiler-templates-and-permissions.md) </span></span>  
 <span data-ttu-id="6dab5-130">[SQL Server 事件探查器](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="6dab5-130">[SQL Server Profiler](sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="6dab5-131">将跟踪与 Windows 性能日志数据关联 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="6dab5-131">Correlate a Trace with Windows Performance Log Data &#40;SQL Server Profiler&#41;</span></span>](../../database-engine/correlate-a-trace-with-windows-performance-log-data-sql-server-profiler.md)  
  
  
