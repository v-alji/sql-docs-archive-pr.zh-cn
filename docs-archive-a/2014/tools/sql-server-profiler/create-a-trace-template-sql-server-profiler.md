---
title: SQL Server Profiler) 创建跟踪模板 (|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- templates [SQL Server], traces
- trace templates [SQL Server]
- saving trace template
ms.assetid: 025868b0-3790-4cda-8757-5a58327bfba0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 355f97c7fecd8a9e31f10de881d1ae6df3b8f122
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682499"
---
# <a name="create-a-trace-template-sql-server-profiler"></a><span data-ttu-id="219f1-102">创建跟踪模板 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="219f1-102">Create a Trace Template (SQL Server Profiler)</span></span>
  <span data-ttu-id="219f1-103">本主题介绍如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]创建新的跟踪模板。</span><span class="sxs-lookup"><span data-stu-id="219f1-103">This topic describes how to create a new trace template by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-create-a-trace-template"></a><span data-ttu-id="219f1-104">创建跟踪模板</span><span class="sxs-lookup"><span data-stu-id="219f1-104">To create a trace template</span></span>  
  
1.  <span data-ttu-id="219f1-105">在 **“文件”** 菜单上，指向 **“模板”** ，然后单击 **“新建模板”** 。</span><span class="sxs-lookup"><span data-stu-id="219f1-105">On the **File** menu, point to **Templates**, and then click **New Template**.</span></span>  
  
2.  <span data-ttu-id="219f1-106">在 **“跟踪模板属性”** 对话框中，从 **“选择服务器类型”** 列表中选择服务器类型。</span><span class="sxs-lookup"><span data-stu-id="219f1-106">In the **Trace Template Properties** dialog box, select a server type from the **Select server type**list.</span></span>  
  
3.  <span data-ttu-id="219f1-107">在“ **新模板名称** ”框中，输入模板的名称。</span><span class="sxs-lookup"><span data-stu-id="219f1-107">In the **New template name** box, enter a template name.</span></span>  
  
4.  <span data-ttu-id="219f1-108">或者，单击 **“使新模板基于现有模板”** ，然后从列表中选择模板。</span><span class="sxs-lookup"><span data-stu-id="219f1-108">Optionally, click **Base new template on existing one**, and then select a template from the list.</span></span>  
  
     <span data-ttu-id="219f1-109">所有事件、数据列和筛选器的初始设置都由选定模板指定。</span><span class="sxs-lookup"><span data-stu-id="219f1-109">All events, data columns, and filters are initially set as specified in the selected template.</span></span>  
  
5.  <span data-ttu-id="219f1-110">或者，单击 **“用作所选服务器类型的默认模板”** 。</span><span class="sxs-lookup"><span data-stu-id="219f1-110">Optionally, click **Use as a default template for selected server type**.</span></span>  
  
6.  <span data-ttu-id="219f1-111">在 **“事件选择”** 选项卡上，添加、删除或修改事件、数据列或筛选器。</span><span class="sxs-lookup"><span data-stu-id="219f1-111">On the **Events Selection** tab, add, remove, or modify events, data columns, or filters.</span></span>  
  
7.  <span data-ttu-id="219f1-112">在 **“事件选择”** 选项卡上，使用网格控件来添加或删除跟踪文件中的事件和数据列，如下所示：</span><span class="sxs-lookup"><span data-stu-id="219f1-112">On the **Events Selection**tab, use the grid control to add or remove events and data columns from the trace file as follows:</span></span>  
  
    -   <span data-ttu-id="219f1-113">若要添加事件，请在 **“事件”** 列中展开相应的事件类别，再选择事件名称。</span><span class="sxs-lookup"><span data-stu-id="219f1-113">To add an event, expand the appropriate event category in the **Events** column, and then select the event name.</span></span>  
  
    -   <span data-ttu-id="219f1-114">添加事件时，默认情况下将包含所有相关数据列。</span><span class="sxs-lookup"><span data-stu-id="219f1-114">When you add an event, all relevant data columns are included by default.</span></span> <span data-ttu-id="219f1-115">若要从跟踪中删除某个事件的数据列，请清除此事件的该数据列中的复选框。</span><span class="sxs-lookup"><span data-stu-id="219f1-115">To remove a data column for an event from a trace, clear the check box in the data column for the event.</span></span>  
  
    -   <span data-ttu-id="219f1-116">若要添加筛选器，请单击数据列的名称，然后在 **“编辑筛选器”** 对话框中指定筛选条件。</span><span class="sxs-lookup"><span data-stu-id="219f1-116">To add filters, click the data column name and specify the filter criteria in the **Edit Filter** dialog box.</span></span> <span data-ttu-id="219f1-117">也可以右键单击数据列名称，再单击“编辑列筛选器”  ，以启动“编辑筛选器”  对话框。</span><span class="sxs-lookup"><span data-stu-id="219f1-117">You can also right-click the data column name, and click **Edit Column Filter** to launch the **Edit Filter** dialog box.</span></span> <span data-ttu-id="219f1-118">单击 **“确定”** 以添加筛选器。</span><span class="sxs-lookup"><span data-stu-id="219f1-118">Click **OK** to add the filter.</span></span>  
  
8.  <span data-ttu-id="219f1-119">单击“保存”  。</span><span class="sxs-lookup"><span data-stu-id="219f1-119">Click **Save.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="219f1-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="219f1-120">See Also</span></span>  
 <span data-ttu-id="219f1-121">[指定跟踪文件的事件和数据列 (SQL Server Profiler)](specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="219f1-121">[Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="219f1-122">[从正在运行的跟踪中派生模板 (SQL Server Profiler)](derive-a-template-from-a-running-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="219f1-122">[Derive a Template from a Running Trace &#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="219f1-123">[从跟踪文件或跟踪表派生模板 (SQL Server Profiler)](derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="219f1-123">[Derive a Template from a Trace File or Trace Table &#40;SQL Server Profiler&#41;](derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="219f1-124">[SQL Server Profiler 模板和权限](sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="219f1-124">[SQL Server Profiler Templates and Permissions](sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="219f1-125">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="219f1-125">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
