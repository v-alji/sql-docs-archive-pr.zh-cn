---
title: 基于事件开始时间筛选事件 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- event start times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: e965579e-d006-41a3-89ec-cfd5398c67d2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7f652952ec6706580b876e3e9a20f96e62598f81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692621"
---
# <a name="filter-events-based-on-the-event-start-time-sql-server-profiler"></a><span data-ttu-id="e4662-102">基于事件开始时间筛选事件 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="e4662-102">Filter Events Based on the Event Start Time (SQL Server Profiler)</span></span>
  <span data-ttu-id="e4662-103">本主题介绍了如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]来基于事件开始时间筛选跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="e4662-103">This topic describes how to filter trace events based on the event start time by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-filter-an-event-based-on-the-event-start-time"></a><span data-ttu-id="e4662-104">基于事件开始时间筛选事件</span><span class="sxs-lookup"><span data-stu-id="e4662-104">To filter an event based on the event start time</span></span>  
  
1.  <span data-ttu-id="e4662-105">在 **“文件”** 菜单上，单击 **“新建跟踪”** ，再连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="e4662-105">On the **File** menu, click **New Trace**, and then connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="e4662-106">将出现“跟踪属性”对话框。 **“跟踪属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="e4662-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e4662-107">如果选择“建立连接后立即开始跟踪”  ，则不会显示“跟踪属性”  对话框，而是开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="e4662-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear, and the trace begins instead.</span></span> <span data-ttu-id="e4662-108">若要关闭此设置，请在“工具”  菜单上，单击“选项”  ，然后清除“建立连接后立即开始跟踪”  复选框。</span><span class="sxs-lookup"><span data-stu-id="e4662-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="e4662-109">在 **“跟踪名称”** 框中，键入跟踪的名称。</span><span class="sxs-lookup"><span data-stu-id="e4662-109">In the **Trace name** box, type a name for the trace.</span></span>  
  
3.  <span data-ttu-id="e4662-110">在“使用模板”  名称列表中，选择跟踪模板。</span><span class="sxs-lookup"><span data-stu-id="e4662-110">In the **Use the template**name list, select a trace template.</span></span>  
  
4.  <span data-ttu-id="e4662-111">为跟踪结果指定目标（可选）。</span><span class="sxs-lookup"><span data-stu-id="e4662-111">Optionally specify a destination for the trace results.</span></span>  
  
5.  <span data-ttu-id="e4662-112">在“事件选择”  选项卡上，单击“StartTime”  列标题。</span><span class="sxs-lookup"><span data-stu-id="e4662-112">On the **Events Selection**tab, click the **StartTime** column heading.</span></span> <span data-ttu-id="e4662-113">也可以右键单击列标题，然后单击“编辑列筛选器”  打开“编辑筛选器”  对话框。</span><span class="sxs-lookup"><span data-stu-id="e4662-113">You can also right-click the column heading, and then click **Edit Column Filter** to launch the **Edit Filter** dialog box.</span></span>  
  
6.  <span data-ttu-id="e4662-114">展开 "**大于**" 或 "**小于**"，然后 `datetime` 在比较运算符下显示的字段中输入一个值。</span><span class="sxs-lookup"><span data-stu-id="e4662-114">Expand **Greater than** or **Less than**, and then enter a `datetime` value in the field that appears beneath the comparison operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4662-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e4662-115">See Also</span></span>  
 [<span data-ttu-id="e4662-116">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="e4662-116">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
