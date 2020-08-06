---
title: 跟踪模板属性 (事件选择选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.tracetemplateproperties.eventsselection.f1
helpviewer_keywords:
- Trace Template Properties dialog box
ms.assetid: 5b202457-ab42-4902-8012-7f3f40aa09f5
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: da497db6e9373c63836753dc2be96deb3ce90244
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693042"
---
# <a name="trace-template-properties-events-selection-tab"></a><span data-ttu-id="b3201-102">跟踪模板属性（“事件选择”选项卡）</span><span class="sxs-lookup"><span data-stu-id="b3201-102">Trace Template Properties (Events Selection Tab)</span></span>
  <span data-ttu-id="b3201-103">使用 **“跟踪模板属性”** 对话框的 **“事件选择”** 选项卡，可以查看、编辑或指定要包含在 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 跟踪模板中的事件类和数据列。</span><span class="sxs-lookup"><span data-stu-id="b3201-103">Use the **Events Selection** tab of the **Trace Template Properties** dialog box to view, edit, or specify event classes and data columns to include in a [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] trace template.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b3201-104">选项</span><span class="sxs-lookup"><span data-stu-id="b3201-104">Options</span></span>  
 <span data-ttu-id="b3201-105">“事件”\*\*\*\* 列</span><span class="sxs-lookup"><span data-stu-id="b3201-105">**Events** column</span></span>  
 <span data-ttu-id="b3201-106">通过选择或清除事件列中的复选框，指定要跟踪的事件。</span><span class="sxs-lookup"><span data-stu-id="b3201-106">Specify events that should be traced by selecting or clearing the check box in the event column.</span></span> <span data-ttu-id="b3201-107">事件按事件类别进行组织。</span><span class="sxs-lookup"><span data-stu-id="b3201-107">Events are organized by event category.</span></span>  
  
 <span data-ttu-id="b3201-108">如果在 **“常规”** 选项卡上选中 **“使新模板基于现有模板”** ，将会根据指定的模板自动选择事件。</span><span class="sxs-lookup"><span data-stu-id="b3201-108">If you selected **Base new template on existing one** on the **General** tab, events are automatically selected according to the specified template.</span></span> <span data-ttu-id="b3201-109">有关事件类的详细信息，请参阅 [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="b3201-109">For more information about event classes, see [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md).</span></span>  
  
 <span data-ttu-id="b3201-110">数据列</span><span class="sxs-lookup"><span data-stu-id="b3201-110">Data columns</span></span>  
 <span data-ttu-id="b3201-111">通过选中与所需的事件和数据列对应的框，指定要跟踪的数据列。</span><span class="sxs-lookup"><span data-stu-id="b3201-111">Specify data columns that should be traced by checking the box that corresponds with the event and the data column you need.</span></span> <span data-ttu-id="b3201-112">如果选中与事件对应的复选框，则默认情况下，将选中与跟踪中包括的每一个事件相关的事件列。</span><span class="sxs-lookup"><span data-stu-id="b3201-112">All relevant event columns are checked by default for each event included in the trace, if the checkbox corresponding to the event is checked.</span></span> <span data-ttu-id="b3201-113">如果在 **“常规”** 选项卡上选中 **“使新模板基于现有模板”** ，将会根据指定的模板自动选择数据列和筛选器。</span><span class="sxs-lookup"><span data-stu-id="b3201-113">If you checked **Base new template on existing one** on the **General** tab, data columns and filters are automatically selected according to the specified template.</span></span>  
  
 <span data-ttu-id="b3201-114">通过单击数据列标题并输入筛选条件指定筛选器。</span><span class="sxs-lookup"><span data-stu-id="b3201-114">Specify filters by clicking the data column heading and entering the filter criteria.</span></span> <span data-ttu-id="b3201-115">筛选出来的数据列由 **“编辑筛选器”** 对话框中列标签左边的筛选器图标指示。</span><span class="sxs-lookup"><span data-stu-id="b3201-115">Filtered data columns are indicated by a filter icon to the left of the column label in the **Edit Filter** dialog box.</span></span>  
  
 <span data-ttu-id="b3201-116">**显示所有事件**</span><span class="sxs-lookup"><span data-stu-id="b3201-116">**Show all events**</span></span>  
 <span data-ttu-id="b3201-117">显示所有可用事件。</span><span class="sxs-lookup"><span data-stu-id="b3201-117">Show all available events.</span></span> <span data-ttu-id="b3201-118">如果创建的新模板不是基于现有模板，默认情况下将选中此选项。</span><span class="sxs-lookup"><span data-stu-id="b3201-118">This option is checked by default if you are creating a new template that is not based on an existing template.</span></span> <span data-ttu-id="b3201-119">取消选中该复选卡可以隐藏 **“事件选择”** 网格中所有未选定的事件。</span><span class="sxs-lookup"><span data-stu-id="b3201-119">Uncheck to hide all unselected events in the **Events Selection** grid.</span></span>  
  
 <span data-ttu-id="b3201-120">**显示所有列**</span><span class="sxs-lookup"><span data-stu-id="b3201-120">**Show all columns**</span></span>  
 <span data-ttu-id="b3201-121">显示所有可用数据列。</span><span class="sxs-lookup"><span data-stu-id="b3201-121">Show all available data columns.</span></span> <span data-ttu-id="b3201-122">如果创建的新模板不是基于现有模板，默认情况下将选中此选项。</span><span class="sxs-lookup"><span data-stu-id="b3201-122">This option is checked by default if you are creating a new template that is not based on an existing template.</span></span> <span data-ttu-id="b3201-123">取消选中该复选卡可以隐藏 **“事件选择”** 网格中所有未选定的数据列。</span><span class="sxs-lookup"><span data-stu-id="b3201-123">Uncheck to hide all unselected data columns in the **Events Selection** grid.</span></span>  
  
 <span data-ttu-id="b3201-124">**列筛选器**</span><span class="sxs-lookup"><span data-stu-id="b3201-124">**Column Filters**</span></span>  
 <span data-ttu-id="b3201-125">启动“编辑筛选器”\*\*\*\* 对话框，该对话框将在数据列标签的左侧显示一个筛选器图标。</span><span class="sxs-lookup"><span data-stu-id="b3201-125">Launches the **Edit Filter** dialog box, which displays a filter icon to the left of the data column label.</span></span> <span data-ttu-id="b3201-126">使用 **“编辑筛选器”** 对话框可编辑数据列筛选器。</span><span class="sxs-lookup"><span data-stu-id="b3201-126">Use the **Edit Filter** dialog box to edit data column filters.</span></span>  
  
 <span data-ttu-id="b3201-127">**组织列**</span><span class="sxs-lookup"><span data-stu-id="b3201-127">**Organize Columns**</span></span>  
 <span data-ttu-id="b3201-128">更改跟踪中列的顺序，并按一列或多列对结果分组。</span><span class="sxs-lookup"><span data-stu-id="b3201-128">Changes the order of columns in the trace and groups results by one or more columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3201-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b3201-129">See Also</span></span>  
 <span data-ttu-id="b3201-130">[指定跟踪文件的事件和数据列 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="b3201-130">[Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="b3201-131">[组织跟踪中显示的列 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="b3201-131">[Organize Columns Displayed in a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="b3201-132">[筛选跟踪 &#40;SQL Server Profiler 中的事件&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="b3201-132">[Filter Events in a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="b3201-133">[查看筛选器信息 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="b3201-133">[View Filter Information &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="b3201-134">[修改筛选器 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="b3201-134">[Modify a Filter &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="b3201-135">[SQL Server Profiler 模板和权限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="b3201-135">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="b3201-136">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="b3201-136">SQL Server Profiler</span></span>](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
