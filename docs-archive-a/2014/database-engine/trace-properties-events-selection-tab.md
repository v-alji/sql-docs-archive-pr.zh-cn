---
title: 跟踪属性 (事件选择选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.traceproperties.eventsselection.f1
helpviewer_keywords:
- Trace Properties dialog box
ms.assetid: e1892f24-7272-4d5d-8926-6150cc82b2c3
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 11f4725865d39c21e36f5fd09eaf2afd4cde3017
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690773"
---
# <a name="trace-properties-events-selection-tab"></a><span data-ttu-id="c0711-102">跟踪属性（“事件选择”选项卡）</span><span class="sxs-lookup"><span data-stu-id="c0711-102">Trace Properties (Events Selection Tab)</span></span>
  <span data-ttu-id="c0711-103">使用 **“跟踪属性”** 对话框的 **“事件选择”** 选项卡可以查看或指定跟踪的事件和数据列。</span><span class="sxs-lookup"><span data-stu-id="c0711-103">Use the **Events Selection** tab of the **Trace Properties** dialog box to view or specify traced events and data columns.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c0711-104">选项</span><span class="sxs-lookup"><span data-stu-id="c0711-104">Options</span></span>  
 <span data-ttu-id="c0711-105">“事件”\*\*\*\* 列</span><span class="sxs-lookup"><span data-stu-id="c0711-105">**Events** column</span></span>  
 <span data-ttu-id="c0711-106">通过选中或清除事件列中的复选框，指定跟踪的事件。</span><span class="sxs-lookup"><span data-stu-id="c0711-106">Specify traced events by selecting or clearing the check box in the event column.</span></span> <span data-ttu-id="c0711-107">**事件**按事件类别进行组织。</span><span class="sxs-lookup"><span data-stu-id="c0711-107">**Events** are organized by event category.</span></span> <span data-ttu-id="c0711-108">模板中指定的事件类是自动选择的。</span><span class="sxs-lookup"><span data-stu-id="c0711-108">Event classes specified in the template are automatically selected.</span></span> <span data-ttu-id="c0711-109">有关详细信息，请参阅 [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="c0711-109">For more information, see [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md).</span></span>  
  
 <span data-ttu-id="c0711-110">数据列</span><span class="sxs-lookup"><span data-stu-id="c0711-110">Data columns</span></span>  
 <span data-ttu-id="c0711-111">通过选中与所需的事件和数据列对应的框，指定跟踪的数据列。</span><span class="sxs-lookup"><span data-stu-id="c0711-111">Specify traced data columns by checking the box that corresponds with the event and the data column you need.</span></span> <span data-ttu-id="c0711-112">对于在跟踪中包括的每个事件，将默认选中所有相关事件列。</span><span class="sxs-lookup"><span data-stu-id="c0711-112">All relevant event columns are checked by default for each event included in the trace.</span></span>  
  
 <span data-ttu-id="c0711-113">通过单击数据列标题并输入筛选条件指定筛选器。</span><span class="sxs-lookup"><span data-stu-id="c0711-113">Specify filters by clicking the data column heading and entering the filter criteria.</span></span> <span data-ttu-id="c0711-114">筛选出来的数据列由 **“编辑筛选器”** 对话框中列标签左边的筛选器图标指示。</span><span class="sxs-lookup"><span data-stu-id="c0711-114">Filtered data columns are indicated by a filter icon to the left of the column label in the **Edit Filter** dialog box.</span></span> <span data-ttu-id="c0711-115">有关详细信息，请参阅 [SQL Server Profiler - 编辑筛选器](../../2014/database-engine/sql-server-profiler-edit-filter.md)。</span><span class="sxs-lookup"><span data-stu-id="c0711-115">For more information, see [SQL Server Profiler - Edit Filter](../../2014/database-engine/sql-server-profiler-edit-filter.md).</span></span>  
  
 <span data-ttu-id="c0711-116">**显示所有事件**</span><span class="sxs-lookup"><span data-stu-id="c0711-116">**Show all events**</span></span>  
 <span data-ttu-id="c0711-117">显示所有可用事件。</span><span class="sxs-lookup"><span data-stu-id="c0711-117">Show all available events.</span></span> <span data-ttu-id="c0711-118">默认情况下，仅显示 **“事件选择”** 网格中选定的行。</span><span class="sxs-lookup"><span data-stu-id="c0711-118">By default, only rows in the **Events Selection** grid that are selected display.</span></span> <span data-ttu-id="c0711-119">取消选中此框，将隐藏 **“事件选择”** 网格中所有未选定的事件。</span><span class="sxs-lookup"><span data-stu-id="c0711-119">Uncheck this box to hide all unselected events in the **Events Selection** grid.</span></span>  
  
 <span data-ttu-id="c0711-120">**显示所有列**</span><span class="sxs-lookup"><span data-stu-id="c0711-120">**Show all columns**</span></span>  
 <span data-ttu-id="c0711-121">显示所有可用数据列。</span><span class="sxs-lookup"><span data-stu-id="c0711-121">Show all available data columns.</span></span> <span data-ttu-id="c0711-122">默认情况下，仅显示选定的数据列。</span><span class="sxs-lookup"><span data-stu-id="c0711-122">By default, only data columns that are selected display.</span></span> <span data-ttu-id="c0711-123">取消选中此框，将隐藏 **“事件选择”** 网格中所有未选定的数据列。</span><span class="sxs-lookup"><span data-stu-id="c0711-123">Uncheck this box to hide all unselected data columns in the **Events Selection** grid.</span></span>  
  
 <span data-ttu-id="c0711-124">**列筛选器**</span><span class="sxs-lookup"><span data-stu-id="c0711-124">**Column Filters**</span></span>  
 <span data-ttu-id="c0711-125">启动“编辑筛选器”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="c0711-125">Launches the **Edit Filter** dialog box.</span></span> <span data-ttu-id="c0711-126">您可以使用此对话框编辑数据列筛选器。</span><span class="sxs-lookup"><span data-stu-id="c0711-126">You can use this dialog to edit data column filters.</span></span>  
  
 <span data-ttu-id="c0711-127">**组织列**</span><span class="sxs-lookup"><span data-stu-id="c0711-127">**Organize Columns**</span></span>  
 <span data-ttu-id="c0711-128">更改跟踪中列的顺序，并按一列或多列对结果分组。</span><span class="sxs-lookup"><span data-stu-id="c0711-128">Changes the order of columns in the trace and groups results by one or more columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0711-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c0711-129">See Also</span></span>  
 <span data-ttu-id="c0711-130">[指定跟踪文件的事件和数据列 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="c0711-130">[Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="c0711-131">[组织跟踪中显示的列 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="c0711-131">[Organize Columns Displayed in a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="c0711-132">[筛选跟踪 &#40;SQL Server Profiler 中的事件&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="c0711-132">[Filter Events in a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="c0711-133">[查看筛选器信息 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="c0711-133">[View Filter Information &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="c0711-134">[修改筛选器 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="c0711-134">[Modify a Filter &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="c0711-135">[SQL Server Profiler 模板和权限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="c0711-135">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="c0711-136">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="c0711-136">SQL Server Profiler</span></span>](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
