---
title: 跟踪表属性 (事件选择选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.tracetableproperties.eventsselection.f1
helpviewer_keywords:
- Trace Table Properties dialog box
ms.assetid: fa21df6a-b6b5-4b15-9104-957385821594
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a2e72f299c9d83762876ce250f750924430ba2f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693443"
---
# <a name="trace-table-properties-events-selection-tab"></a><span data-ttu-id="ff225-102">跟踪表属性（“事件选择”选项卡）</span><span class="sxs-lookup"><span data-stu-id="ff225-102">Trace Table Properties (Events Selection Tab)</span></span>
  <span data-ttu-id="ff225-103">使用 **“跟踪表属性”** 对话框的 **“事件选择”** 选项卡可以查看跟踪的事件和数据列属性，或者从跟踪中删除事件或列。</span><span class="sxs-lookup"><span data-stu-id="ff225-103">Use the **Events Selection** tab of the **Trace Table Properties** dialog box to view the events and data column properties of the trace or to remove events or columns from the trace.</span></span>  
  
 <span data-ttu-id="ff225-104">若要查看此窗口，请使用 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 打开一个跟踪表。</span><span class="sxs-lookup"><span data-stu-id="ff225-104">To view this window, use [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] to open a trace table.</span></span> <span data-ttu-id="ff225-105">然后，在 "**文件**" 菜单上，单击 "**属性**"，然后单击 "**事件选择**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="ff225-105">Then on the **File** menu, click **Properties**, and then click the **Events Selection** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ff225-106">选项</span><span class="sxs-lookup"><span data-stu-id="ff225-106">Options</span></span>  
 <span data-ttu-id="ff225-107">“事件”\*\*\*\* 列</span><span class="sxs-lookup"><span data-stu-id="ff225-107">**Events** column</span></span>  
 <span data-ttu-id="ff225-108">查看按事件类别组织的跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="ff225-108">View traced events which are organized by event category.</span></span> <span data-ttu-id="ff225-109">可以通过选中事件框或选中事件的数据列来选择事件。</span><span class="sxs-lookup"><span data-stu-id="ff225-109">Events can be selected by checking the box or by checking a data column for an event.</span></span> <span data-ttu-id="ff225-110">如果选中事件框，则该事件的所有可用数据列均被选中。</span><span class="sxs-lookup"><span data-stu-id="ff225-110">If the event box is checked, all data columns available for that event are selected.</span></span> <span data-ttu-id="ff225-111">如果选中了某个事件的数据列，则该事件将被选中，并且其他所有必需列也被自动选中。</span><span class="sxs-lookup"><span data-stu-id="ff225-111">If the data column for an event is checked, the event is checked and any other required column is also automatically checked.</span></span> <span data-ttu-id="ff225-112">如果您正在查看跟踪文件或表，清除事件复选框或数据列将减少跟踪窗口中的可见数据量，便于分析。</span><span class="sxs-lookup"><span data-stu-id="ff225-112">If you are viewing a trace file or table, clearing check boxes for events or data columns reduces the amount of visible data in the trace window for easier analysis.</span></span> <span data-ttu-id="ff225-113">您也可以更改列筛选器以减少跟踪窗口中的可见数据量。</span><span class="sxs-lookup"><span data-stu-id="ff225-113">You can also change column filters to reduce the amount of visible data in the trace window.</span></span> <span data-ttu-id="ff225-114">有关事件类的详细信息，请参阅 [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="ff225-114">For more information about event classes, see [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md).</span></span>  
  
 <span data-ttu-id="ff225-115">其他数据列</span><span class="sxs-lookup"><span data-stu-id="ff225-115">Other data columns</span></span>  
 <span data-ttu-id="ff225-116">查看跟踪数据列。</span><span class="sxs-lookup"><span data-stu-id="ff225-116">View traced data columns.</span></span> <span data-ttu-id="ff225-117">默认情况下，将会为跟踪中包含的每个事件选中跟踪中的所有相关数据列。</span><span class="sxs-lookup"><span data-stu-id="ff225-117">All relevant data columns in the trace are checked by default for each event included in the trace.</span></span>  
  
 <span data-ttu-id="ff225-118">通过单击数据列标题并输入筛选条件指定筛选器。</span><span class="sxs-lookup"><span data-stu-id="ff225-118">Specify filters by clicking the data column heading and entering the filter criteria.</span></span> <span data-ttu-id="ff225-119">筛选出来的数据列由 **“编辑筛选器”** 对话框中列标签左边的筛选器图标指示。</span><span class="sxs-lookup"><span data-stu-id="ff225-119">Filtered data columns are indicated by a filter icon to the left of the column label in the **Edit Filter** dialog box.</span></span>  
  
 <span data-ttu-id="ff225-120">**显示所有事件**</span><span class="sxs-lookup"><span data-stu-id="ff225-120">**Show all events**</span></span>  
 <span data-ttu-id="ff225-121">显示所有可用事件。</span><span class="sxs-lookup"><span data-stu-id="ff225-121">Show all available events.</span></span> <span data-ttu-id="ff225-122">默认情况下，仅显示 **“事件选择”** 网格中选定的行。</span><span class="sxs-lookup"><span data-stu-id="ff225-122">By default, only rows in the **Events Selection** grid that are selected display.</span></span> <span data-ttu-id="ff225-123">取消选中此框，将隐藏 **“事件选择”** 网格中所有未选定的事件。</span><span class="sxs-lookup"><span data-stu-id="ff225-123">Uncheck this box to hide all unselected events in the **Events Selection** grid.</span></span> <span data-ttu-id="ff225-124">如果选中了 **“显示所有事件”** ，并且您正在查看跟踪文件或表，则跟踪过程中记录的所有事件都将显示在跟踪窗口中。</span><span class="sxs-lookup"><span data-stu-id="ff225-124">If **Show all events** is checked and you are viewing a trace file or table, all events that were recorded in the trace display in the trace window.</span></span>  
  
 <span data-ttu-id="ff225-125">**显示所有列**</span><span class="sxs-lookup"><span data-stu-id="ff225-125">**Show all columns**</span></span>  
 <span data-ttu-id="ff225-126">显示所有可用数据列。</span><span class="sxs-lookup"><span data-stu-id="ff225-126">Show all available data columns.</span></span> <span data-ttu-id="ff225-127">默认情况下，仅显示选定的数据列。</span><span class="sxs-lookup"><span data-stu-id="ff225-127">By default, only data columns that are selected display.</span></span> <span data-ttu-id="ff225-128">取消选中此框，将隐藏 **“事件选择”** 网格中所有未选定的数据列。</span><span class="sxs-lookup"><span data-stu-id="ff225-128">Uncheck this box to hide all unselected data columns in the **Events Selection** grid.</span></span>  
  
 <span data-ttu-id="ff225-129">**列筛选器**</span><span class="sxs-lookup"><span data-stu-id="ff225-129">**Column Filters**</span></span>  
 <span data-ttu-id="ff225-130">启动“编辑筛选器”\*\*\*\* 对话框，该对话框在列标签的左侧显示一个筛选器图标。</span><span class="sxs-lookup"><span data-stu-id="ff225-130">Launches the **Edit Filter** dialog box, which displays a filter icon to the left of the column label.</span></span> <span data-ttu-id="ff225-131">您可以使用此对话框编辑数据列筛选器。</span><span class="sxs-lookup"><span data-stu-id="ff225-131">You can use this dialog box to edit data column filters.</span></span>  
  
 <span data-ttu-id="ff225-132">**组织列**</span><span class="sxs-lookup"><span data-stu-id="ff225-132">**Organize Columns**</span></span>  
 <span data-ttu-id="ff225-133">选择要跟踪的**事件**和数据列后，单击“组织列”\*\*\*\* 将强制网格对跟踪结果窗口中的列重新排序。</span><span class="sxs-lookup"><span data-stu-id="ff225-133">After selecting **Events** and data columns to trace, click **Organize Columns** to force the grid to reorder the column in the trace results window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff225-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ff225-134">See Also</span></span>  
 <span data-ttu-id="ff225-135">[打开跟踪表 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="ff225-135">[Open a Trace Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="ff225-136">[SQL Server Profiler 模板和权限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="ff225-136">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="ff225-137">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="ff225-137">SQL Server Profiler</span></span>](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
