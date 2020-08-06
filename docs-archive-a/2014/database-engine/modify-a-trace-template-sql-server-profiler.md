---
title: SQL Server Profiler) 修改跟踪模板 (|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- templates [SQL Server], traces
- trace templates [SQL Server]
- modifying traces
ms.assetid: b81df2a1-e202-43d8-92b0-0beb145f0116
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2a93baedb1875ac740e74065ae7188f9b576e083
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578384"
---
# <a name="modify-a-trace-template-sql-server-profiler"></a><span data-ttu-id="21d3b-102">修改跟踪模板 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="21d3b-102">Modify a Trace Template (SQL Server Profiler)</span></span>
  <span data-ttu-id="21d3b-103">本主题介绍了如何使用 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]修改跟踪模板。</span><span class="sxs-lookup"><span data-stu-id="21d3b-103">This topic describes how to modify a trace template by using [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-modify-a-trace-template"></a><span data-ttu-id="21d3b-104">修改跟踪模板</span><span class="sxs-lookup"><span data-stu-id="21d3b-104">To modify a trace template</span></span>  
  
1.  <span data-ttu-id="21d3b-105">在 **“文件”** 菜单上，指向 **“模板”**，然后单击 **“编辑模板”**。</span><span class="sxs-lookup"><span data-stu-id="21d3b-105">On the **File** menu, point to **Templates**, and then click **Edit Template**.</span></span>  
  
2.  <span data-ttu-id="21d3b-106">在 **“跟踪模板属性”** 对话框的 **“常规”** 选项卡上，可以修改服务器类型和模板名称，或者选择将默认模板用于服务器类型。</span><span class="sxs-lookup"><span data-stu-id="21d3b-106">In the **Trace Template Properties** dialog box, on the **General** tab, you can modify the server type and template name, or choose to use a default template for the server type.</span></span>  
  
3.  <span data-ttu-id="21d3b-107">在 "**事件选择**" 选项卡上，使用网格控件来添加或删除跟踪文件中的事件和数据列，如下所示。</span><span class="sxs-lookup"><span data-stu-id="21d3b-107">On the **Events Selection**tab, use the grid control to add or remove events and data columns from the trace file as follows.</span></span>  
  
    -   <span data-ttu-id="21d3b-108">若要添加事件，请在 **“事件”** 列中展开相应的事件类别，再选择事件名称。</span><span class="sxs-lookup"><span data-stu-id="21d3b-108">To add an event, expand the appropriate event category in the **Events** column, and then select the event name.</span></span>  
  
    -   <span data-ttu-id="21d3b-109">添加事件时，默认情况下将包含所有相关数据列。</span><span class="sxs-lookup"><span data-stu-id="21d3b-109">When you add an event, all relevant data columns are included by default.</span></span> <span data-ttu-id="21d3b-110">若要从跟踪中删除某个事件的数据列，请清除此事件的该数据列中的复选框。</span><span class="sxs-lookup"><span data-stu-id="21d3b-110">To remove a data column for an event from a trace, clear the check box in the data column for the event.</span></span>  
  
    -   <span data-ttu-id="21d3b-111">若要添加筛选器，请单击数据列的名称，然后在 **“编辑筛选器”** 对话框中指定筛选条件。</span><span class="sxs-lookup"><span data-stu-id="21d3b-111">To add filters, click the data column name and specify the filter criteria in the **Edit Filter** dialog box.</span></span> <span data-ttu-id="21d3b-112">也可以右键单击数据列名称，再单击“编辑列筛选器”\*\*\*\*，以启动“编辑筛选器”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="21d3b-112">You can also right-click the data column name, and click **Edit Column Filter** to launch the **Edit Filter** dialog box.</span></span> <span data-ttu-id="21d3b-113">单击 **“确定”** 以添加筛选器。</span><span class="sxs-lookup"><span data-stu-id="21d3b-113">Click **OK** to add the filter.</span></span>  
  
4.  <span data-ttu-id="21d3b-114">单击“保存”，\*\*\*\* 或单击“另存为”\*\*\*\* 将跟踪模板另存为其他名称。</span><span class="sxs-lookup"><span data-stu-id="21d3b-114">Click **Save**, or click **Save As**to save the trace template under another name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21d3b-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="21d3b-115">See Also</span></span>  
 <span data-ttu-id="21d3b-116">[指定跟踪文件的事件和数据列 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="21d3b-116">[Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="21d3b-117">[从正在运行的跟踪中派生模板 (SQL Server Profiler)](../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="21d3b-117">[Derive a Template from a Running Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="21d3b-118">[从跟踪文件或跟踪表派生模板 (SQL Server Profiler)](../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="21d3b-118">[Derive a Template from a Trace File or Trace Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="21d3b-119">[SQL Server Profiler 模板和权限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="21d3b-119">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="21d3b-120">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="21d3b-120">SQL Server Profiler</span></span>](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
