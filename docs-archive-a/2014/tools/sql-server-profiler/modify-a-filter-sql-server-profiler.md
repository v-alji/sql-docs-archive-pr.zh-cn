---
title: 修改筛选器 (SQL Server Profiler) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], modifying
- modifying filters, modifying
- filters [SQL Server], traces
ms.assetid: 8b317813-4918-4485-b930-77b1951aa00c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5a7bab18952820a3dc49c9479797a411521f8e71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581077"
---
# <a name="modify-a-filter-sql-server-profiler"></a><span data-ttu-id="6c3ec-102">修改筛选器 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="6c3ec-102">Modify a Filter (SQL Server Profiler)</span></span>
  <span data-ttu-id="6c3ec-103">可以通过将筛选器添加到包含跟踪定义的跟踪模板，来限制跟踪所收集的事件数。</span><span class="sxs-lookup"><span data-stu-id="6c3ec-103">You add filters to trace templates, which contain the trace definitions, to limit the number of events that are gathered by a trace.</span></span> <span data-ttu-id="6c3ec-104">限制收集的事件数能够减少跟踪对性能的影响。</span><span class="sxs-lookup"><span data-stu-id="6c3ec-104">Limiting the number of events gathered can reduce the performance effects of tracing.</span></span> <span data-ttu-id="6c3ec-105">如果已设置了跟踪模板的筛选器，并发现该跟踪没有收集所需类型的信息，则可以对该筛选器进行编辑。</span><span class="sxs-lookup"><span data-stu-id="6c3ec-105">If you set filters for a trace template and find that the trace is not gathering the kind of information that you need, you can edit the filter.</span></span>  
  
### <a name="to-modify-a-filter"></a><span data-ttu-id="6c3ec-106">修改筛选器</span><span class="sxs-lookup"><span data-stu-id="6c3ec-106">To modify a filter</span></span>  
  
1.  <span data-ttu-id="6c3ec-107">在 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]中，打开要修改的跟踪筛选器的模板。</span><span class="sxs-lookup"><span data-stu-id="6c3ec-107">In [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], open the template for the trace filter that you want to modify.</span></span> <span data-ttu-id="6c3ec-108">在 **“文件”** 菜单上，单击 **“模板”** ，然后选择 **“编辑模板”** 。</span><span class="sxs-lookup"><span data-stu-id="6c3ec-108">On the **File** menu, click **Templates**, and then choose **Edit Template**.</span></span>  
  
2.  <span data-ttu-id="6c3ec-109">在 **“跟踪模板属性”** 对话框的 **“常规”** 选项卡中，选择 **“选择模板名称”** 列表中的一个模板。</span><span class="sxs-lookup"><span data-stu-id="6c3ec-109">In the **General** tab of the **Trace Template Properties** dialog, select a template from the **Select template name** list.</span></span>  
  
3.  <span data-ttu-id="6c3ec-110">单击 **“事件选择”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="6c3ec-110">Click the **Events Selection** tab.</span></span>  
  
     <span data-ttu-id="6c3ec-111">**“事件选择”** 选项卡包含一个网格控件。</span><span class="sxs-lookup"><span data-stu-id="6c3ec-111">The **Events Selection** tab contains a grid control.</span></span> <span data-ttu-id="6c3ec-112">网格控件是包含所有可跟踪事件类的表。</span><span class="sxs-lookup"><span data-stu-id="6c3ec-112">The grid control is a table that contains each of the traceable event classes.</span></span> <span data-ttu-id="6c3ec-113">每个事件类在表中占一行。</span><span class="sxs-lookup"><span data-stu-id="6c3ec-113">The table contains one row for each event class.</span></span> <span data-ttu-id="6c3ec-114">事件类可能略有不同，这取决于所连接服务器的类型和版本。</span><span class="sxs-lookup"><span data-stu-id="6c3ec-114">The event classes may differ slightly, depending on the type and version of server to which you are connected.</span></span> <span data-ttu-id="6c3ec-115">事件类由网格的“事件” **“事件”** 列进行标识，并按事件类别进行分组。</span><span class="sxs-lookup"><span data-stu-id="6c3ec-115">The event classes are identified in the **Events**column of the grid and are grouped by event category.</span></span> <span data-ttu-id="6c3ec-116">其余列则列出每个事件类可以返回的数据列。</span><span class="sxs-lookup"><span data-stu-id="6c3ec-116">The remaining columns list the data columns that can be returned for each event class.</span></span>  
  
4.  <span data-ttu-id="6c3ec-117">单击 **“列筛选器”** 。</span><span class="sxs-lookup"><span data-stu-id="6c3ec-117">Click **Column Filters**.</span></span>  
  
5.  <span data-ttu-id="6c3ec-118">在 **“编辑筛选器”** 对话框中，单击要编辑的比较运算符旁边的值，然后键入新值或删除一个值。</span><span class="sxs-lookup"><span data-stu-id="6c3ec-118">In the **Edit Filter** dialog box, click the value next to the comparison operator that you want to edit, and type the new value or delete a value.</span></span> <span data-ttu-id="6c3ec-119">此外，还可以添加其他筛选器。</span><span class="sxs-lookup"><span data-stu-id="6c3ec-119">You can also add additional filters.</span></span>  
  
6.  <span data-ttu-id="6c3ec-120">单击 **“确定”** 保存模板。</span><span class="sxs-lookup"><span data-stu-id="6c3ec-120">Click **OK** and save the template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c3ec-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6c3ec-121">See Also</span></span>  
 [<span data-ttu-id="6c3ec-122">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="6c3ec-122">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
