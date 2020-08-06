---
title: 筛选跟踪中的事件 (SQL Server Profiler) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: 0fd63573-3b35-4f67-9e1e-ed9aabee11a8
author: stevestein
ms.author: sstein
ms.openlocfilehash: fef9dd6956d407011261c54f796a751a0bf94941
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692622"
---
# <a name="filter-events-in-a-trace-sql-server-profiler"></a><span data-ttu-id="028ca-102">在跟踪中筛选事件 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="028ca-102">Filter Events in a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="028ca-103">筛选器将限制跟踪内收集的事件。</span><span class="sxs-lookup"><span data-stu-id="028ca-103">Filters limit the events collected in a trace.</span></span> <span data-ttu-id="028ca-104">如果没有设置筛选器，则跟踪输出中将返回选定事件类的所有事件。</span><span class="sxs-lookup"><span data-stu-id="028ca-104">If a filter is not set, all events of the selected event classes are returned in the trace output.</span></span> <span data-ttu-id="028ca-105">并不一定要为跟踪设置筛选器。</span><span class="sxs-lookup"><span data-stu-id="028ca-105">It is not mandatory to set a filter for a trace.</span></span> <span data-ttu-id="028ca-106">但筛选器可使跟踪过程中造成的开销最小化。</span><span class="sxs-lookup"><span data-stu-id="028ca-106">However, a filter minimizes the overhead that is incurred during tracing.</span></span>  
  
 <span data-ttu-id="028ca-107">可以使用 **“跟踪属性”** 或 **“跟踪模板属性”** 对话框中的 **“事件选择”** 选项卡向跟踪定义中添加筛选器。</span><span class="sxs-lookup"><span data-stu-id="028ca-107">You add filters to trace definitions by using the **Events Selection** tab of the **Trace Properties** or **Trace Template Properties** dialog box.</span></span>  
  
### <a name="to-filter-events-in-a-trace"></a><span data-ttu-id="028ca-108">在跟踪中筛选事件</span><span class="sxs-lookup"><span data-stu-id="028ca-108">To filter events in a trace</span></span>  
  
1.  <span data-ttu-id="028ca-109">在 **“跟踪属性”** 或 **“跟踪模板属性”** 对话框中，单击 **“事件选择”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="028ca-109">In the **Trace Properties** or **Trace Template Properties** dialog box, click the **Events Selection** tab.</span></span>  
  
     <span data-ttu-id="028ca-110">**“事件选择”** 选项卡包含一个网格控件。</span><span class="sxs-lookup"><span data-stu-id="028ca-110">The **Events Selection** tab contains a grid control.</span></span> <span data-ttu-id="028ca-111">网格控件是包含所有可跟踪事件类的表。</span><span class="sxs-lookup"><span data-stu-id="028ca-111">The grid control is a table that contains each of the traceable event classes.</span></span> <span data-ttu-id="028ca-112">每个事件类在表中占一行。</span><span class="sxs-lookup"><span data-stu-id="028ca-112">The table contains one row for each event class.</span></span> <span data-ttu-id="028ca-113">事件类可能略有不同，这取决于所连接服务器的类型和版本。</span><span class="sxs-lookup"><span data-stu-id="028ca-113">The event classes may differ slightly, depending on the type and version of server to which you are connected.</span></span> <span data-ttu-id="028ca-114">事件类由网格的“事件” **“事件”** 列进行标识，并按事件类别进行分组。</span><span class="sxs-lookup"><span data-stu-id="028ca-114">The event classes are identified in the **Events**column of the grid and are grouped by event category.</span></span> <span data-ttu-id="028ca-115">其余列则列出每个事件类可以返回的数据列。</span><span class="sxs-lookup"><span data-stu-id="028ca-115">The remaining columns list the data columns that can be returned for each event class.</span></span>  
  
2.  <span data-ttu-id="028ca-116">单击 **“列筛选器”.**</span><span class="sxs-lookup"><span data-stu-id="028ca-116">Click **Column Filters.**</span></span>  
  
     <span data-ttu-id="028ca-117">此时将显示“编辑筛选器”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="028ca-117">The **Edit Filter**dialog box appears.</span></span> <span data-ttu-id="028ca-118">“编辑筛选器”对话框包含一个比较运算符列表，可以使用这些运算符在跟踪中筛选事件\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="028ca-118">The **Edit Filter**dialog box contains a list of comparison operators that you can use to filter events in a trace.</span></span>  
  
3.  <span data-ttu-id="028ca-119">若要应用筛选器，请单击比较运算符，再键入要用于该筛选器的值。</span><span class="sxs-lookup"><span data-stu-id="028ca-119">To apply a filter, click the comparison operator, and type a value to use for the filter.</span></span>  
  
4.  <span data-ttu-id="028ca-120">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="028ca-120">Click **OK**.</span></span>  
  
 <span data-ttu-id="028ca-121">**注意事项：**</span><span class="sxs-lookup"><span data-stu-id="028ca-121">**Considerations:**</span></span>  
  
-   <span data-ttu-id="028ca-122">如果要对“事件选择”选项卡上的 **StartTime** 和 **EndTime** 数据列设置筛选条件，那么请确保：</span><span class="sxs-lookup"><span data-stu-id="028ca-122">If you set filter conditions on the **StartTime** and **EndTime** data columns of the Events Selection tab, then make sure that:</span></span>  
  
    -   <span data-ttu-id="028ca-123">输入的日期符合此格式： `YYYY/MM/DD HH:mm:sec`。</span><span class="sxs-lookup"><span data-stu-id="028ca-123">The date you enter matches this format: `YYYY/MM/DD HH:mm:sec`.</span></span>  
  
         <span data-ttu-id="028ca-124">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="028ca-124">-OR-</span></span>  
  
    -   <span data-ttu-id="028ca-125">在 **“常规选项”** 对话框中选中了 **“使用区域设置来显示日期和时间值”** 。</span><span class="sxs-lookup"><span data-stu-id="028ca-125">**Use regional settings to display date and time values** is checked in the **General Options** dialog box.</span></span> <span data-ttu-id="028ca-126">要查看“常规选项”  对话框，请在 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 的“工具”  菜单上单击“选项”  。</span><span class="sxs-lookup"><span data-stu-id="028ca-126">To view the **General Options** dialog box, on the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Tools** menu, click **Option**.</span></span>  
  
         <span data-ttu-id="028ca-127">-以及-</span><span class="sxs-lookup"><span data-stu-id="028ca-127">-AND-</span></span>  
  
    -   <span data-ttu-id="028ca-128">输入的日期介于 1753 年 1 月 1 日到 9999 年 12 月 31 日之间。</span><span class="sxs-lookup"><span data-stu-id="028ca-128">The date you enter is between January 1, 1753 and December 31, 9999.</span></span>  
  
-   <span data-ttu-id="028ca-129">如果从 **osql** 实用工具或 **sqlcmd** 实用工具跟踪事件，则始终将 **%** 追加到 **TextData** 数据列上的筛选器。</span><span class="sxs-lookup"><span data-stu-id="028ca-129">If tracing events from the **osql** utility or from the **sqlcmd** utility, always append **%** to filters on the **TextData** data column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="028ca-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="028ca-130">See Also</span></span>  
 [<span data-ttu-id="028ca-131">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="028ca-131">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
