---
title: 指定跟踪文件的事件和数据列 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- adding events
- traces [SQL Server], data columns
- deleting events
- removing events
- traces [SQL Server], events
ms.assetid: 7da715a3-2f03-4063-b6a4-20fd7b44e675
author: stevestein
ms.author: sstein
ms.openlocfilehash: ffb8639a187f1e7e091e382031886659bd47d7d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576460"
---
# <a name="specify-events-and-data-columns-for-a-trace-file-sql-server-profiler"></a><span data-ttu-id="7b03c-102">指定跟踪文件的事件和数据列 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="7b03c-102">Specify Events and Data Columns for a Trace File (SQL Server Profiler)</span></span>
  <span data-ttu-id="7b03c-103">本主题介绍了如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]指定跟踪的事件类和数据列。</span><span class="sxs-lookup"><span data-stu-id="7b03c-103">This topic describes how to specify event classes and data columns for traces by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-specify-events-and-data-columns-for-a-trace"></a><span data-ttu-id="7b03c-104">指定跟踪的事件和数据列</span><span class="sxs-lookup"><span data-stu-id="7b03c-104">To specify events and data columns for a trace</span></span>  
  
1.  <span data-ttu-id="7b03c-105">在 **“跟踪属性”** 或 **“跟踪模板属性”** 对话框中，单击 **“事件选择”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="7b03c-105">On the **Trace Properties** or **Trace Template Properties** dialog box, click the **Events Selection** tab.</span></span>  
  
     <span data-ttu-id="7b03c-106">**“事件选择”** 选项卡包含一个网格控件。</span><span class="sxs-lookup"><span data-stu-id="7b03c-106">The **Events Selection** tab contains a grid control.</span></span> <span data-ttu-id="7b03c-107">网格控件是包含所有可跟踪事件类的表。</span><span class="sxs-lookup"><span data-stu-id="7b03c-107">The grid control is a table that contains each of the traceable event classes.</span></span> <span data-ttu-id="7b03c-108">每个事件类在表中占一行。</span><span class="sxs-lookup"><span data-stu-id="7b03c-108">The table contains one row for each event class.</span></span> <span data-ttu-id="7b03c-109">根据您所连接的服务器的类型和版本的不同，事件类会略有不同。</span><span class="sxs-lookup"><span data-stu-id="7b03c-109">The event classes can differ slightly depending on the type and version of server to which you are connected.</span></span> <span data-ttu-id="7b03c-110">事件类由网格的“事件” **“事件”** 列进行标识，并按事件类别进行分组。</span><span class="sxs-lookup"><span data-stu-id="7b03c-110">The event classes are identified in the **Events**column of the grid and are grouped by event category.</span></span> <span data-ttu-id="7b03c-111">其余列则列出每个事件类可以返回的数据列。</span><span class="sxs-lookup"><span data-stu-id="7b03c-111">The remaining columns list the data columns that can be returned for each event class.</span></span>  
  
2.  <span data-ttu-id="7b03c-112">在 **“事件选择”** 选项卡上，使用网格控件在跟踪文件中添加或删除事件和数据列。</span><span class="sxs-lookup"><span data-stu-id="7b03c-112">On the **Events Selection**tab, use the grid control to add or remove events and data columns from the trace file.</span></span>  
  
3.  <span data-ttu-id="7b03c-113">若要从跟踪中删除事件，请清除每个事件类的 **“事件”** 列中的复选框。</span><span class="sxs-lookup"><span data-stu-id="7b03c-113">To remove events from the trace, clear the check box in the **Events** column for each event class.</span></span>  
  
4.  <span data-ttu-id="7b03c-114">若要在跟踪中包括事件，请选中每个事件类的 **“事件”** 列中的复选框，或者选中对应于事件的数据列。</span><span class="sxs-lookup"><span data-stu-id="7b03c-114">To include events in a trace, check the box in the **Events** column for each event class, or check a data column that corresponds to an event.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7b03c-115">如果跟踪要与系统监视器或性能监视器数据关联，则必须在跟踪中包括“开始时间”  和“结束时间”  数据列。</span><span class="sxs-lookup"><span data-stu-id="7b03c-115">If the trace is going be correlated with System Monitor or Performance Monitor data, both **Start Time** and **End Time** data columns must be included in the trace.</span></span>  
  
 <span data-ttu-id="7b03c-116">如果已选中对应于事件的复选框，在包括事件类时，跟踪中也将包括关联的数据列。</span><span class="sxs-lookup"><span data-stu-id="7b03c-116">When you include an event class, every associated data column is also included to the trace, if you have checked the box corresponding to an event.</span></span> <span data-ttu-id="7b03c-117">如果选中某个特定列的复选框，跟踪中将只包括该列。</span><span class="sxs-lookup"><span data-stu-id="7b03c-117">If you checked the box for a particular column, only that column is included in the trace.</span></span>  
  
1.  <span data-ttu-id="7b03c-118">若要从某个事件类删除数据列，请从事件类行中的数据列清除复选框，或右键单击列标题并选择“取消选择列”  选项。</span><span class="sxs-lookup"><span data-stu-id="7b03c-118">To remove data columns from an event class, clear the check boxes from the data column in the event class row, or right-click on the column header and select the **Deselect column** option.</span></span>  
  
2.  <span data-ttu-id="7b03c-119">或者，对跟踪应用筛选器。</span><span class="sxs-lookup"><span data-stu-id="7b03c-119">Optionally, apply filters to the trace.</span></span> <span data-ttu-id="7b03c-120">有关详细信息，请参阅[在跟踪中筛选事件 (SQL Server Profiler)](filter-events-in-a-trace-sql-server-profiler.md)</span><span class="sxs-lookup"><span data-stu-id="7b03c-120">For more information, see [Filter Events in a Trace &#40;SQL Server Profiler&#41;](filter-events-in-a-trace-sql-server-profiler.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b03c-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7b03c-121">See Also</span></span>  
 [<span data-ttu-id="7b03c-122">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="7b03c-122">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
