---
title: 基于事件结束时间筛选事件 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- event end times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: 74628f9e-2d39-496a-a443-0a3887db223d
author: stevestein
ms.author: sstein
ms.openlocfilehash: d25d8e1adbd95f48d88fd1516c48dcc0f8374a7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693583"
---
# <a name="filter-events-based-on-the-event-end-time-sql-server-profiler"></a><span data-ttu-id="54837-102">基于事件结束时间筛选事件 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="54837-102">Filter Events Based on the Event End Time (SQL Server Profiler)</span></span>
  <span data-ttu-id="54837-103">本主题介绍了如何通过使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]来根据事件结束时间筛选跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="54837-103">This topic describes how to filter trace events based on the event ending time by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-filter-events-based-on-the-event-end-time"></a><span data-ttu-id="54837-104">根据事件结束时间筛选事件</span><span class="sxs-lookup"><span data-stu-id="54837-104">To filter events based on the event end time</span></span>  
  
1.  <span data-ttu-id="54837-105">在 **“文件”** 菜单上，单击 **“新建跟踪”** ，再连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="54837-105">On the **File** menu, click **New Trace**, and then connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="54837-106">将出现“跟踪属性”对话框。 **“跟踪属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="54837-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="54837-107">如果选择“建立连接后立即开始跟踪”  ，则不会显示“跟踪属性”  对话框，而是开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="54837-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="54837-108">若要关闭此设置，请在“工具”  菜单上，单击“选项”  ，然后清除“建立连接后立即开始跟踪”  复选框。</span><span class="sxs-lookup"><span data-stu-id="54837-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="54837-109">在 **“跟踪属性”** 对话框中，确保选中 **“常规”** 选项卡，然后在 **TraceName** 文本框中输入名称。</span><span class="sxs-lookup"><span data-stu-id="54837-109">In the **Trace Properties** dialog box, make sure the **General** tab is selected, and enter a name in the **TraceName** text box.</span></span>  
  
3.  <span data-ttu-id="54837-110">从“使用模板”  列表中选择一个跟踪模板。</span><span class="sxs-lookup"><span data-stu-id="54837-110">From the **Use the template**list, select a trace template.</span></span>  
  
4.  <span data-ttu-id="54837-111">根据需要，指定保存跟踪结果的目标文件或表。</span><span class="sxs-lookup"><span data-stu-id="54837-111">Optionally, specify a destination file or table in which to save the trace results.</span></span>  
  
5.  <span data-ttu-id="54837-112">在“事件选择”  选项卡上，单击“EndTime”  数据列启动“编辑筛选器”  对话框。</span><span class="sxs-lookup"><span data-stu-id="54837-112">On the **Events Selection**tab, click the **EndTime** data column to launch the **Edit Filter** dialog box.</span></span> <span data-ttu-id="54837-113">也可以右键单击列标题，然后选择“编辑列筛选器”  。</span><span class="sxs-lookup"><span data-stu-id="54837-113">You can also right-click the column heading, and select **Edit Column Filter**.</span></span>  
  
6.  <span data-ttu-id="54837-114">展开 "**大于**" 或 "**小于**"，然后在 `datetime` 比较运算符下显示的字段中输入一个值。</span><span class="sxs-lookup"><span data-stu-id="54837-114">Expand **Greater than** or **Less than**, and enter a `datetime`value in the field that appears beneath the comparison operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54837-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="54837-115">See Also</span></span>  
 <span data-ttu-id="54837-116">[SQL Server 事件探查器](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="54837-116">[SQL Server Profiler](sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="54837-117">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="54837-117">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
