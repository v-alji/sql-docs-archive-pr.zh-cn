---
title: 指定断点筛选器
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint filter
ms.assetid: 7bf1dddd-7b0b-4c47-8a7b-28a5569b4fa5
author: rothja
ms.author: jroth
ms.openlocfilehash: 9fc320397da1bddc0d28191c359c4d311b23e044
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587319"
---
# <a name="specify-a-breakpoint-filter"></a><span data-ttu-id="1008b-102">指定断点筛选器</span><span class="sxs-lookup"><span data-stu-id="1008b-102">Specify a Breakpoint Filter</span></span>
  <span data-ttu-id="1008b-103">断点筛选器对断点进行限制，使其仅对指定的计算机、操作系统进程和线程执行操作。</span><span class="sxs-lookup"><span data-stu-id="1008b-103">A breakpoint filter limits the breakpoint to acting only on specified computers, operating system processes, and threads.</span></span> <span data-ttu-id="1008b-104">断点筛选器通常在调试并行应用程序时使用。</span><span class="sxs-lookup"><span data-stu-id="1008b-104">Breakpoint filters are typically used when debugging parallel applications.</span></span>  
  
##  <a name="filter-considerations"></a><a name="BKMK_ActionConsiderations"></a> <span data-ttu-id="1008b-105">筛选器注意事项</span><span class="sxs-lookup"><span data-stu-id="1008b-105">Filter Considerations</span></span>  
 <span data-ttu-id="1008b-106">断点筛选器通常不与 [!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器结合使用，因为 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本和存储过程不是并行应用程序。</span><span class="sxs-lookup"><span data-stu-id="1008b-106">Breakpoint filters are not typically used with the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger because [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts and stored procedures are not parallel applications.</span></span>  
  
#### <a name="to-specify-a-breakpoint-filter"></a><span data-ttu-id="1008b-107">指定断点筛选器</span><span class="sxs-lookup"><span data-stu-id="1008b-107">To Specify a Breakpoint Filter</span></span>  
  
1.  <span data-ttu-id="1008b-108">在“编辑器”窗口中，右键单击断点符号，然后单击快捷菜单上的“筛选器”  。</span><span class="sxs-lookup"><span data-stu-id="1008b-108">In the editor window, right-click the breakpoint glyph, and then click **Filter** on the shortcut menu.</span></span>  
  
     <span data-ttu-id="1008b-109">-或-</span><span class="sxs-lookup"><span data-stu-id="1008b-109">-or-</span></span>  
  
     <span data-ttu-id="1008b-110">在“断点”  窗口中，右键单击断点符号，然后单击快捷菜单上的“筛选器”  。</span><span class="sxs-lookup"><span data-stu-id="1008b-110">In the **Breakpoints** window, right-click the breakpoint glyph, and then click **Filter** on the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="1008b-111">在 **“断点筛选器”** 对话框中，使用 **“筛选器”** 框按名称指定计算机，或者按名称或 ID 编号指定操作系统进程和线程：</span><span class="sxs-lookup"><span data-stu-id="1008b-111">In the **Breakpoint Filters** dialog box, use the **Filter** box to specify computers by name, or operating system processes and threads by either name or ID number:</span></span>  
  
    -   <span data-ttu-id="1008b-112">`MachineName` 是运行数据库引擎实例的计算机。</span><span class="sxs-lookup"><span data-stu-id="1008b-112">`MachineName` is the computer running the instance of the Database Engine.</span></span>  
  
    -   <span data-ttu-id="1008b-113">`ProcessID` 和 `ProcessName` 是运行数据库引擎实例的操作系统进程。</span><span class="sxs-lookup"><span data-stu-id="1008b-113">`ProcessID`, and `ProcessName` are the operating system process running the instance of the Database Engine.</span></span>  
  
    -   <span data-ttu-id="1008b-114">`ThreadID` 和 `ThreadName` 是在数据库引擎实例中运行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批处理、过程或功能的操作系统线程。</span><span class="sxs-lookup"><span data-stu-id="1008b-114">`ThreadID` and `ThreadName` are the operating system thread running the [!INCLUDE[tsql](../../includes/tsql-md.md)] batch, procedure, or function in the instance of the Database Engine.</span></span>  
  
3.  <span data-ttu-id="1008b-115">单击 **“确定”** 实施更改，或单击 **“取消”** 退出而不应用更改。</span><span class="sxs-lookup"><span data-stu-id="1008b-115">Click **OK** to implement the changes, or **Cancel** to exit without applying the changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1008b-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1008b-116">See Also</span></span>  
 <span data-ttu-id="1008b-117">[指定断点条件](specify-a-breakpoint-condition.md) </span><span class="sxs-lookup"><span data-stu-id="1008b-117">[Specify a Breakpoint Condition](specify-a-breakpoint-condition.md) </span></span>  
 <span data-ttu-id="1008b-118">[指定命中计数](specify-a-hit-count.md) </span><span class="sxs-lookup"><span data-stu-id="1008b-118">[Specify a Hit Count](specify-a-hit-count.md) </span></span>  
 [<span data-ttu-id="1008b-119">指定断点操作</span><span class="sxs-lookup"><span data-stu-id="1008b-119">Specify a Breakpoint Action</span></span>](specify-a-breakpoint-action.md)  
