---
title: 跟踪文件属性 (事件选择选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.tracefileproperties.eventsselection.f1
helpviewer_keywords:
- Trace File Properties dialog box
ms.assetid: 158d442f-2225-4173-8545-fb1cf611b4d0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: abfadc2b1df4cda039d7e413e5ba0c7777e7c04e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690774"
---
# <a name="trace-file-properties-events-selection-tab"></a><span data-ttu-id="7057a-102">跟踪文件属性（“事件选择”选项卡）</span><span class="sxs-lookup"><span data-stu-id="7057a-102">Trace File Properties (Events Selection Tab)</span></span>
  <span data-ttu-id="7057a-103">使用 **“跟踪文件模板属性”** 对话框的 **“事件选择”** 选项卡，可以查看跟踪的列属性或者从跟踪中删除数据列。</span><span class="sxs-lookup"><span data-stu-id="7057a-103">Use the **Events Selection** tab of the **Trace File Template Properties** dialog box to view the column properties of the trace or remove data columns from the trace.</span></span>  
  
 <span data-ttu-id="7057a-104">若要查看此窗口，请打开跟踪文件。</span><span class="sxs-lookup"><span data-stu-id="7057a-104">To view this window, open a trace file.</span></span> <span data-ttu-id="7057a-105">然后，在 **“文件”** 菜单上，单击 **“属性”**，再单击 **“事件选择”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="7057a-105">Then, on the **File** menu, click **Properties**, and then click the **Events Selection** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7057a-106">选项</span><span class="sxs-lookup"><span data-stu-id="7057a-106">Options</span></span>  
 <span data-ttu-id="7057a-107">“事件”\*\*\*\* 列</span><span class="sxs-lookup"><span data-stu-id="7057a-107">**Events** column</span></span>  
 <span data-ttu-id="7057a-108">查看按事件类别组织的跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="7057a-108">View traced events which are organized by event category.</span></span> <span data-ttu-id="7057a-109">最初，跟踪中的所有事件均被选中。</span><span class="sxs-lookup"><span data-stu-id="7057a-109">Initially, all events in the trace are selected.</span></span> <span data-ttu-id="7057a-110">可以通过选中事件框或选中事件的数据列来选择事件。</span><span class="sxs-lookup"><span data-stu-id="7057a-110">Events can be selected by checking the box or by checking a data column for an event.</span></span> <span data-ttu-id="7057a-111">如果选中事件框，则该事件的所有可用数据列均被选中。</span><span class="sxs-lookup"><span data-stu-id="7057a-111">If the event box is checked, all data columns available for that event are selected.</span></span> <span data-ttu-id="7057a-112">如果选中了某个事件的数据列，则该事件将被选中，并且其他所有必需列也被自动选中。</span><span class="sxs-lookup"><span data-stu-id="7057a-112">If the data column for an event is checked, the event is checked and any other required column is also automatically checked.</span></span> <span data-ttu-id="7057a-113">如果您正在查看跟踪文件或表，清除事件复选框或数据列将减少跟踪窗口中的可见数据量，便于分析。</span><span class="sxs-lookup"><span data-stu-id="7057a-113">If you are viewing a trace file or table, clearing check boxes for events or data columns reduces the amount of visible data in the trace window for easier analysis.</span></span> <span data-ttu-id="7057a-114">您也可以更改列筛选器以减少跟踪窗口中的可见数据量。</span><span class="sxs-lookup"><span data-stu-id="7057a-114">You can also change column filters to reduce the amount of visible data in the trace window.</span></span> <span data-ttu-id="7057a-115">有关事件类的详细信息，请参阅 [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="7057a-115">For more information about event classes, see [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md).</span></span>  
  
 <span data-ttu-id="7057a-116">数据列</span><span class="sxs-lookup"><span data-stu-id="7057a-116">Data Columns</span></span>  
 <span data-ttu-id="7057a-117">查看跟踪数据列。</span><span class="sxs-lookup"><span data-stu-id="7057a-117">View traced data columns.</span></span> <span data-ttu-id="7057a-118">默认情况下，将会为跟踪中包含的每个事件选中跟踪中的所有相关数据列。</span><span class="sxs-lookup"><span data-stu-id="7057a-118">All relevant data columns in the trace are checked by default for each event included in the trace.</span></span>  
  
 <span data-ttu-id="7057a-119">通过单击数据列标题并输入筛选条件指定筛选器。</span><span class="sxs-lookup"><span data-stu-id="7057a-119">Specify filters by clicking the data column heading and entering the filter criteria.</span></span> <span data-ttu-id="7057a-120">筛选出来的数据列由 **“编辑筛选器”** 对话框中列标签左边的筛选器图标指示。</span><span class="sxs-lookup"><span data-stu-id="7057a-120">Filtered data columns are indicated by a filter icon to the left of the column label in the **Edit Filter** dialog box.</span></span>  
  
 <span data-ttu-id="7057a-121">**显示所有事件**</span><span class="sxs-lookup"><span data-stu-id="7057a-121">**Show all events**</span></span>  
 <span data-ttu-id="7057a-122">显示所有可用事件。</span><span class="sxs-lookup"><span data-stu-id="7057a-122">Show all available events.</span></span> <span data-ttu-id="7057a-123">默认情况下，仅显示 **“事件选择”** 网格中选定的行。</span><span class="sxs-lookup"><span data-stu-id="7057a-123">By default, only rows in the **Events Selection** grid that are selected display.</span></span> <span data-ttu-id="7057a-124">取消选中此框，将隐藏 **“事件选择”** 网格中所有未选定的事件。</span><span class="sxs-lookup"><span data-stu-id="7057a-124">Uncheck this box to hide all unselected events in the **Events Selection** grid.</span></span> <span data-ttu-id="7057a-125">如果选中了 **“显示所有事件”** ，并且您正在查看跟踪文件或表，则跟踪过程中记录的所有事件都将显示在跟踪窗口中。</span><span class="sxs-lookup"><span data-stu-id="7057a-125">If **Show all events** is checked and you are viewing a trace file or table, all events that were recorded in the trace display in the trace window.</span></span>  
  
 <span data-ttu-id="7057a-126">**显示所有列**</span><span class="sxs-lookup"><span data-stu-id="7057a-126">**Show all columns**</span></span>  
 <span data-ttu-id="7057a-127">显示所有可用数据列。</span><span class="sxs-lookup"><span data-stu-id="7057a-127">Show all available data columns.</span></span> <span data-ttu-id="7057a-128">默认情况下，仅显示选定的数据列。</span><span class="sxs-lookup"><span data-stu-id="7057a-128">By default, only data columns that are selected display.</span></span> <span data-ttu-id="7057a-129">取消选中此框，将隐藏 **“事件选择”** 网格中所有未选定的数据列。</span><span class="sxs-lookup"><span data-stu-id="7057a-129">Uncheck this box to hide all unselected data columns in the **Events Selection** grid.</span></span>  
  
 <span data-ttu-id="7057a-130">**列筛选器**</span><span class="sxs-lookup"><span data-stu-id="7057a-130">**Column Filters**</span></span>  
 <span data-ttu-id="7057a-131">启动“编辑筛选器”\*\*\*\* 对话框，该对话框将在已筛选数据列的列标签左侧显示筛选器图标。</span><span class="sxs-lookup"><span data-stu-id="7057a-131">Launches the **Edit Filter** dialog box, which displays a filter icon to the left of the column label for filtered data columns.</span></span> <span data-ttu-id="7057a-132">使用 **“编辑筛选器”** 对话框可编辑数据列筛选器。</span><span class="sxs-lookup"><span data-stu-id="7057a-132">Use the **Edit Filter** dialog box to edit data column filters.</span></span>  
  
 <span data-ttu-id="7057a-133">**组织列**</span><span class="sxs-lookup"><span data-stu-id="7057a-133">**Organize Columns**</span></span>  
 <span data-ttu-id="7057a-134">选择要跟踪的**事件**和数据列后，单击“组织列”\*\*\*\* 将强制网格对跟踪结果窗口中的列重新排序。</span><span class="sxs-lookup"><span data-stu-id="7057a-134">After selecting **Events** and data columns to trace, click **Organize Columns** to force the grid to reorder the column in the trace results window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7057a-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7057a-135">See Also</span></span>  
 <span data-ttu-id="7057a-136">[指定跟踪文件的事件和数据列 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="7057a-136">[Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="7057a-137">[筛选跟踪 &#40;SQL Server Profiler 中的事件&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="7057a-137">[Filter Events in a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="7057a-138">[查看筛选器信息 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="7057a-138">[View Filter Information &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="7057a-139">[修改筛选器 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="7057a-139">[Modify a Filter &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="7057a-140">[SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="7057a-140">[SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="7057a-141">SQL Server Profiler 模板和权限</span><span class="sxs-lookup"><span data-stu-id="7057a-141">SQL Server Profiler Templates and Permissions</span></span>](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)  
  
  
