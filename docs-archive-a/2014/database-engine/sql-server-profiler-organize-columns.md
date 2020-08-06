---
title: SQL Server Profiler-组织列 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.organize.columns.f1
ms.assetid: bf5674f4-da5e-43f9-aeb2-76ca37993790
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b63c2f7d882bac05fc6baf10614170ec23125c12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691852"
---
# <a name="sql-server-profiler---organize-columns"></a><span data-ttu-id="63540-102">SQL Server Profiler - 组织列</span><span class="sxs-lookup"><span data-stu-id="63540-102">SQL Server Profiler - Organize Columns</span></span>
  <span data-ttu-id="63540-103">使用 **“组织列”** 对话框可为跟踪中所显示的分组或聚合事件选择数据列，以便查看和分析较大的跟踪文件或跟踪表。</span><span class="sxs-lookup"><span data-stu-id="63540-103">Use the **Organize Columns** dialog box to select data columns for grouping or aggregating events that are displayed in a trace, which makes large trace files or tables easier to view and analyze.</span></span>  
  
 <span data-ttu-id="63540-104">通过聚合，可以在跟踪中移动和折叠其相应的事件类类型下的所有事件。</span><span class="sxs-lookup"><span data-stu-id="63540-104">Aggregating moves and collapses all events in the trace under its respective event class type.</span></span> <span data-ttu-id="63540-105">**+** 事件类名称的左侧将显示一个加号 () 。</span><span class="sxs-lookup"><span data-stu-id="63540-105">A plus sign (**+**) appears to the left of the event class name.</span></span> <span data-ttu-id="63540-106">单击加号可展开相应的事件类，以便查看该类型的所有事件。</span><span class="sxs-lookup"><span data-stu-id="63540-106">Clicking the plus sign expands the event class so you can view all events of that type.</span></span>  
  
 <span data-ttu-id="63540-107">通过分组，可以在跟踪显示窗口中将特定类型的所有事件组织起来。</span><span class="sxs-lookup"><span data-stu-id="63540-107">Grouping organizes all event classes of a specific type together in the trace window display.</span></span> <span data-ttu-id="63540-108">但是，这些事件在其事件类类型下并不折叠显示。</span><span class="sxs-lookup"><span data-stu-id="63540-108">However, the events are not collapsed under the event class type.</span></span>  
  
 <span data-ttu-id="63540-109">在跟踪显示窗口中对事件进行分组或聚合时，所选择的用于分组或聚合的列会在显示窗口中保持固定，但是您可以左右滚动，以便查看所有其他的数据列。</span><span class="sxs-lookup"><span data-stu-id="63540-109">When you group or aggregate events in a trace window display, the columns selected for grouping or aggregating remain fixed in the display window, but you can scroll to the right or left to view all other data columns.</span></span>  
  
 <span data-ttu-id="63540-110">若要访问此对话框，请打开现有的跟踪文件或跟踪表，再单击“文件”[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] \*\*\*\* 菜单上的“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63540-110">To access this dialog box, open an existing trace file or table, and click **Properties** on the [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] **File** menu.</span></span> <span data-ttu-id="63540-111">在 **“跟踪属性”** 对话框中，单击 **“事件选择”** 选项卡，再单击 **“组织列”**。</span><span class="sxs-lookup"><span data-stu-id="63540-111">In the **Trace Properties** dialog box, click the **Events Selection** tab, and then click **Organize Columns**.</span></span> <span data-ttu-id="63540-112">您也可以在创建新的跟踪时单击 **“事件选择”** 选项卡上的 **“组织列”** 。</span><span class="sxs-lookup"><span data-stu-id="63540-112">You can also click **Organize Columns** on the **Events Selection** tab when you are creating a new trace.</span></span>  
  
## <a name="options"></a><span data-ttu-id="63540-113">选项</span><span class="sxs-lookup"><span data-stu-id="63540-113">Options</span></span>  
 <span data-ttu-id="63540-114">**组**</span><span class="sxs-lookup"><span data-stu-id="63540-114">**Groups**</span></span>  
 <span data-ttu-id="63540-115">将数据列名称移动到“组”\*\*\*\* 下，可以在跟踪窗口中对事件类进行分组或聚合。</span><span class="sxs-lookup"><span data-stu-id="63540-115">Move data column names under **Groups** to group or aggregate event classes in the trace window.</span></span>  
  
 <span data-ttu-id="63540-116">若要对事件进行聚合，请将一个数据列移动到 **“组”** 中。</span><span class="sxs-lookup"><span data-stu-id="63540-116">To aggregate events, move one data column into **Groups**.</span></span> <span data-ttu-id="63540-117">这会导致在跟踪显示窗口中相应的事件类类型名称下折叠所有特定类型的事件。</span><span class="sxs-lookup"><span data-stu-id="63540-117">This causes all events of a specific type to be collapsed under event class type name in the trace window display.</span></span> <span data-ttu-id="63540-118">**+** 事件类名称的左侧将显示一个加号 () 。</span><span class="sxs-lookup"><span data-stu-id="63540-118">A plus sign (**+**) appears to the left of the event class name.</span></span> <span data-ttu-id="63540-119">单击加号可展开相应的事件类类型，以便查看所有事件。</span><span class="sxs-lookup"><span data-stu-id="63540-119">Click the plus sign to expand the event class type and view all events.</span></span> <span data-ttu-id="63540-120">您可以通过单击 **“视图”** 菜单上的 **“聚合视图”** 或 **“分组视图”** 来启用或禁用聚合和分组功能。</span><span class="sxs-lookup"><span data-stu-id="63540-120">You can set aggregation and grouping on and off by clicking **Aggregated View** or **Grouped View** on the **View** menu.</span></span>  
  
 <span data-ttu-id="63540-121">若要对事件进行分组，请将多个数据列移动到 **“组”** 中。</span><span class="sxs-lookup"><span data-stu-id="63540-121">To group events, move more than one data column into **Groups**.</span></span> <span data-ttu-id="63540-122">这会将跟踪显示窗口中所有特定类型的事件分到一组中，但是不会在各事件类类型名称下折叠事件。</span><span class="sxs-lookup"><span data-stu-id="63540-122">This causes all events of a specific type to be grouped together in the trace window display, but does not collapse the events under each event class type name.</span></span> <span data-ttu-id="63540-123">您可以通过单击“视图”菜单上的 **“分组视图”** 在分组视图和未分组视图之间来回切换。</span><span class="sxs-lookup"><span data-stu-id="63540-123">You can switch back and forth between a grouped view and an ungrouped view by clicking **Grouped View** on the View menu.</span></span> <span data-ttu-id="63540-124">当多个数据列移动到 **“组”** 中时，将无法切换到 **“聚合视图”** 。</span><span class="sxs-lookup"><span data-stu-id="63540-124">When more than one data column is moved into **Groups**, the option to switch to **Aggregated View** is not available.</span></span>  
  
 <span data-ttu-id="63540-125">**“列”**</span><span class="sxs-lookup"><span data-stu-id="63540-125">**Columns**</span></span>  
 <span data-ttu-id="63540-126">列出可移动到“组”\*\*\*\* 中的数据列。</span><span class="sxs-lookup"><span data-stu-id="63540-126">List of data columns available to move into **Groups**.</span></span> <span data-ttu-id="63540-127">单击列左侧的加号 (**+**) 展开列表。 **Columns**</span><span class="sxs-lookup"><span data-stu-id="63540-127">Click the plus sign (**+**) to the left of **Columns** to expand the list.</span></span>  
  
 <span data-ttu-id="63540-128">**Up**</span><span class="sxs-lookup"><span data-stu-id="63540-128">**Up**</span></span>  
 <span data-ttu-id="63540-129">选择数据列之后，单击“向上”\*\*\*\* 可将数据列移动到“组”\*\*\*\* 中。</span><span class="sxs-lookup"><span data-stu-id="63540-129">After selecting a data column, click **Up** to move data columns up into **Groups**.</span></span> <span data-ttu-id="63540-130">您也可以单击 **“向上”** 在跟踪显示窗口中对列的显示顺序重新进行排列。</span><span class="sxs-lookup"><span data-stu-id="63540-130">You can also click **Up** to rearrange the display of columns in the trace window display.</span></span>  
  
 <span data-ttu-id="63540-131">**向下**</span><span class="sxs-lookup"><span data-stu-id="63540-131">**Down**</span></span>  
 <span data-ttu-id="63540-132">选择数据列之后，单击“向下”\*\*\*\* 可将数据列从“组”\*\*\*\* 中移出。</span><span class="sxs-lookup"><span data-stu-id="63540-132">After selecting a data column, click **Down** to move data columns out of **Groups**.</span></span> <span data-ttu-id="63540-133">您也可以单击 **“向下”** 在跟踪显示窗口中对列的显示顺序重新进行排列。</span><span class="sxs-lookup"><span data-stu-id="63540-133">You can also click **Down** to rearrange the display of columns in the trace window display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63540-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="63540-134">See Also</span></span>  
 <span data-ttu-id="63540-135">[组织跟踪中显示的列 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="63540-135">[Organize Columns Displayed in a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="63540-136">[创建跟踪 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="63540-136">[Create a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="63540-137">[创建跟踪模板 (SQL Server Profiler)](../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="63540-137">[Create a Trace Template &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="63540-138">[打开跟踪文件 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="63540-138">[Open a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="63540-139">打开跟踪表 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="63540-139">Open a Trace Table &#40;SQL Server Profiler&#41;</span></span>](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)  
  
  
