---
title: 开始 SQL Server Profiler |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], starting
- SQL Server Profiler, starting
- starting SQL Server Profiler
ms.assetid: 22e57ffa-63b0-4de3-b92e-df297dda1226
author: stevestein
ms.author: sstein
ms.openlocfilehash: 05743927420865a9b6341fc050ca999f494d64d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690946"
---
# <a name="start-sql-server-profiler"></a><span data-ttu-id="19500-102">启动 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="19500-102">Start SQL Server Profiler</span></span>
  <span data-ttu-id="19500-103">可以通过多种方法启动 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ，以支持在各种情况下收集跟踪输出。</span><span class="sxs-lookup"><span data-stu-id="19500-103">You can start [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] in several different ways to support gathering trace output in a variety of scenarios.</span></span> <span data-ttu-id="19500-104">启动 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 的方法包括：从 **“开始”** 菜单启动、从 **优化顾问中的** “工具” [!INCLUDE[ssDE](../../includes/ssde-md.md)] 菜单启动以及从 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的多个位置启动。</span><span class="sxs-lookup"><span data-stu-id="19500-104">You can start [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] include from the **Start** menu, from the **Tools** menu in [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor, and from several locations in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="19500-105">首次启动 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 并从 **“文件”** 菜单中选择 **“新建跟踪”** 时，此应用程序将显示 **“连接到服务器”** 对话框，在该对话框中可以指定要连接到的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="19500-105">When you first start [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] and select **New Trace** from the **File** menu, the application displays a **Connect to Server** dialog box where you can specify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to which you want to connect.</span></span>  
  
### <a name="to-start-sql-server-profiler-from-the-start-menu"></a><span data-ttu-id="19500-106">从“开始”菜单启动 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="19500-106">To start SQL Server Profiler from the Start menu</span></span>  
  
1.  <span data-ttu-id="19500-107">在 **“开始”** 菜单中，依次指向 **“所有程序”**、 [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]、 **“性能工具”**，然后单击 **SQL Server Profiler**。</span><span class="sxs-lookup"><span data-stu-id="19500-107">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Performance Tools**, and then click **SQL Server Profiler**.</span></span>  
  
### <a name="to-start-sql-server-profiler-in-database-engine-tuning-advisor"></a><span data-ttu-id="19500-108">在数据库引擎优化顾问中启动 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="19500-108">To start SQL Server Profiler in Database Engine Tuning Advisor</span></span>  
  
1.  <span data-ttu-id="19500-109">在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 优化顾问的 **“工具”** 菜单上，单击 **SQL Server Profiler**。</span><span class="sxs-lookup"><span data-stu-id="19500-109">On the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor **Tools** menu, click **SQL Server Profiler**.</span></span>  
  
## <a name="starting-sql-server-profiler-in-management-studio"></a><span data-ttu-id="19500-110">在 Management Studio 中启动 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="19500-110">Starting SQL Server Profiler in Management Studio</span></span>  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="19500-111">启动的每个事件探查器会话处于自己的实例中，在关闭 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的情况下仍继续运行。</span><span class="sxs-lookup"><span data-stu-id="19500-111">starts each profiler session in its own instance and continues to run if you shutdown [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="19500-112">可以从 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 中的多个位置启动 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，如以下过程中所示。</span><span class="sxs-lookup"><span data-stu-id="19500-112">You can start [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] from several locations in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], as illustrated in the following procedures.</span></span> <span data-ttu-id="19500-113">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 在启动时将加载连接上下文、跟踪模板及其启动点的筛选上下文。</span><span class="sxs-lookup"><span data-stu-id="19500-113">When [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] starts it loads the connection context, trace template, and filter context of its launch point.</span></span>  
  
#### <a name="to-start-sql-server-profiler-from-the-tools-menu"></a><span data-ttu-id="19500-114">从“工具”菜单启动 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="19500-114">To start SQL Server Profiler from the Tools menu</span></span>  
  
1.  <span data-ttu-id="19500-115">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的“工具”菜单中，单击“SQL Server Profiler” 。</span><span class="sxs-lookup"><span data-stu-id="19500-115">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Tools** menu, click **SQL Server Profiler**.</span></span>  
  
#### <a name="to-start-sql-server-profiler-from-the-query-editor"></a><span data-ttu-id="19500-116">从查询编辑器启动 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="19500-116">To start SQL Server Profiler from the Query Editor</span></span>  
  
1.  <span data-ttu-id="19500-117">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的菜单栏上，单击 **“新建查询”**。</span><span class="sxs-lookup"><span data-stu-id="19500-117">On the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] menu bar, click **New Query**.</span></span>  
  
2.  <span data-ttu-id="19500-118">在查询编辑器中右键单击，然后选择“在 SQL Server Profiler 中跟踪查询” 。</span><span class="sxs-lookup"><span data-stu-id="19500-118">In Query Editor, right-click and then select **Trace Query in SQL Server Profiler**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="19500-119">该连接上下文为编辑器连接，跟踪模板为 TSQL_SPs，应用的筛选器为 SPID = query window SPID。</span><span class="sxs-lookup"><span data-stu-id="19500-119">The connection context is the editor connection, the trace template is TSQL_SPs, and the applied filter is SPID = query window SPID.</span></span>  
  
#### <a name="to-start-sql-server-profiler-from-activity-monitor"></a><span data-ttu-id="19500-120">从活动监视器启动 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="19500-120">To start SQL Server Profiler from Activity Monitor</span></span>  
  
1.  <span data-ttu-id="19500-121">在对象资源管理器中，右键单击 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例，然后单击“活动监视器” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="19500-121">In Object Explorer, right-click an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and then click **Activity Monitor**.</span></span>  
  
2.  <span data-ttu-id="19500-122">单击“进程” \*\*\*\* 窗格，右键单击要探查的进程，然后单击“在 SQL Server Profiler 中跟踪进程” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="19500-122">Click the **Processes** pane, right-click the process that you want to profile, and then click **Trace Process in SQL Server Profiler**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="19500-123">选定某个进程后，打开活动监视器时连接上下文为对象资源管理器连接。</span><span class="sxs-lookup"><span data-stu-id="19500-123">When a process is selected, the connection context is the Object Explorer connection when Activity Monitor was opened.</span></span> <span data-ttu-id="19500-124">跟踪模板为基于服务器类型的默认模板，并且 SPID 等于所选进程的 SPID。</span><span class="sxs-lookup"><span data-stu-id="19500-124">The trace template is the default based on the server type, and the SPID equals the SPID for the selected process.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="19500-125">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="19500-125">.NET Framework Security</span></span>  
 <span data-ttu-id="19500-126">在 Windows 身份验证模式下，运行 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 的用户帐户必须拥有连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的权限。</span><span class="sxs-lookup"><span data-stu-id="19500-126">In Windows Authentication mode, the user account that runs [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] must have permission to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="19500-127">若要使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]执行跟踪，用户还必须拥有 ALTER TRACE 权限。</span><span class="sxs-lookup"><span data-stu-id="19500-127">To perform tracing with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], users must also have the ALTER TRACE permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19500-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="19500-128">See Also</span></span>  
 <span data-ttu-id="19500-129">[SQL Server Profiler](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="19500-129">[SQL Server Profiler](sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="19500-130">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="19500-130">Use SQL Server Management Studio</span></span>](../../database-engine/use-sql-server-management-studio.md)  
  
  
