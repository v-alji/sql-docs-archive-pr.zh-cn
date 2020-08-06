---
title: 保存死锁图形 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- deadlocks [SQL Server], saving deadlock graphs
- graphs [SQL Server]
- saving deadlock graphs
ms.assetid: bf1fc906-abd6-4a89-842e-da0d66b2defe
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cdd0bd808ba4b934e5b2d91c9079909acf6e3997
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588473"
---
# <a name="save-deadlock-graphs-sql-server-profiler"></a><span data-ttu-id="408ef-102">保存死锁图形（SQL Server 事件探查器）</span><span class="sxs-lookup"><span data-stu-id="408ef-102">Save Deadlock Graphs (SQL Server Profiler)</span></span>
  <span data-ttu-id="408ef-103">本主题介绍了如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]保存 Deadlock Graph 事件。</span><span class="sxs-lookup"><span data-stu-id="408ef-103">This topic describes how to save a deadlock graph by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="408ef-104">Deadlock Graph 事件以 XML 文件形式保存。</span><span class="sxs-lookup"><span data-stu-id="408ef-104">Deadlock graphs are saved as XML files.</span></span>  
  
### <a name="to-save-deadlock-graph-events-separately"></a><span data-ttu-id="408ef-105">分别保存 Deadlock Graph 事件</span><span class="sxs-lookup"><span data-stu-id="408ef-105">To save deadlock graph events separately</span></span>  
  
1.  <span data-ttu-id="408ef-106">在 **“文件”** 菜单上，单击 **“新建跟踪”** ，再连接到 SQL Server 实例。</span><span class="sxs-lookup"><span data-stu-id="408ef-106">On the **File** menu, click **New Trace**, and then connect to an instance of SQL Server.</span></span>  
  
     <span data-ttu-id="408ef-107">将出现“跟踪属性”对话框。 **“跟踪属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="408ef-107">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="408ef-108">如果选择“建立连接后立即开始跟踪”\*\*\*\*，则不会显示“跟踪属性”\*\*\*\* 对话框，而是开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="408ef-108">If **Start tracing immediately after making connection** is selected, the **Trace Properties**dialog box fails to appear, and the trace begins instead.</span></span> <span data-ttu-id="408ef-109">若要关闭此设置，请在“工具”菜单上，单击“选项”，然后清除“建立连接后立即开始跟踪”复选框。</span><span class="sxs-lookup"><span data-stu-id="408ef-109">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="408ef-110">在“跟踪属性”对话框内的“跟踪名称”\*\*\*\* 框中键入跟踪的名称。</span><span class="sxs-lookup"><span data-stu-id="408ef-110">In the Trace Properties dialog box, type a name for the trace in the**Trace name** box.</span></span>  
  
3.  <span data-ttu-id="408ef-111">在 **“使用模板”** 列表中，为此跟踪选择一个跟踪模板；如果不想使用模板，请选择 **“空白”** 。</span><span class="sxs-lookup"><span data-stu-id="408ef-111">In the **Use the template** list, select a trace template on which to base the trace, or select **Blank** if you do not want to use a template.</span></span>  
  
4.  <span data-ttu-id="408ef-112">执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="408ef-112">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="408ef-113">选中“保存到文件”\*\*\*\* 复选框以将跟踪捕获到文件中。</span><span class="sxs-lookup"><span data-stu-id="408ef-113">Select the**Save to file** check box to capture the trace to a file.</span></span> <span data-ttu-id="408ef-114">指定 **“设置最大文件大小”** 的值。</span><span class="sxs-lookup"><span data-stu-id="408ef-114">Specify a value for **Set maximum file size**.</span></span>  
  
         <span data-ttu-id="408ef-115">也可以选择 **“启用文件滚动更新”** 和 **“服务器处理跟踪数据”**。</span><span class="sxs-lookup"><span data-stu-id="408ef-115">Optionally, select **Enable file rollover** and **Server processes trace data**.</span></span>  
  
    -   <span data-ttu-id="408ef-116">选中 **“保存到表”** 复选框以将跟踪捕获到数据库表中。</span><span class="sxs-lookup"><span data-stu-id="408ef-116">Select the **Save to table** check box to capture the trace to a database table.</span></span>  
  
         <span data-ttu-id="408ef-117">根据需要，可以单击 **“设置最大行数”**，并指定值。</span><span class="sxs-lookup"><span data-stu-id="408ef-117">Optionally, click **Set maximum rows**, and specify a value.</span></span>  
  
5.  <span data-ttu-id="408ef-118">根据需要，可以选中 **“启用跟踪停止时间”** 复选框，再指定停止日期和时间。</span><span class="sxs-lookup"><span data-stu-id="408ef-118">Optionally, select the **Enable trace stop time** check box, and specify a stop date and time.</span></span>  
  
6.  <span data-ttu-id="408ef-119">单击“事件选择”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="408ef-119">Click the **Events Selection**tab.</span></span>  
  
7.  <span data-ttu-id="408ef-120">在“事件”\*\*\*\* 数据列中，展开“Locks”\*\*\*\* 事件类别，然后选中“Deadlock Graph”\*\*\*\* 复选框。</span><span class="sxs-lookup"><span data-stu-id="408ef-120">In the **Events**data column, expand the **Locks**event category, and then select the **Deadlock graph**check box.</span></span> <span data-ttu-id="408ef-121">如果没有显示“Locks”事件类别，请选中 **“显示所有事件”** 以显示该类别。</span><span class="sxs-lookup"><span data-stu-id="408ef-121">If the Locks event category is not available, check **Show all events** to display it.</span></span>  
  
     <span data-ttu-id="408ef-122">“事件提取设置”\*\*\*\* 选项卡将添加到“跟踪属性”\*\*\*\* 对话框中。</span><span class="sxs-lookup"><span data-stu-id="408ef-122">The **Events Extraction Settings**tab is added to the **Trace Properties**dialog box.</span></span>  
  
8.  <span data-ttu-id="408ef-123">在“事件提取设置”\*\*\*\* 选项卡上，单击“分别保存死锁 XML 事件”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="408ef-123">On the **Events Extraction Settings**tab, click **Save Deadlock XML Events Separately**.</span></span>  
  
9. <span data-ttu-id="408ef-124">在 **“另存为”** 对话框中，输入要存储 Deadlock Graph 事件的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="408ef-124">In the **Save As** dialog box, enter the name of the file in which to store the deadlock graph events.</span></span>  
  
10. <span data-ttu-id="408ef-125">单击“单个文件中的所有死锁 XML 批”\*\*\*\* 以将所有 Deadlock Graph 事件保存到单个 XML 文件中，或单击“不同文件中的每个死锁 XML 批”\*\*\*\* 以便为每个 Deadlock Graph 事件创建新的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="408ef-125">Click **All Deadlock XML batches in a single file** to save all deadlock graph events in a single XML file, or click **Each Deadlock XML batch in a distinct file**to create a new XML file for each deadlock graph.</span></span>  
  
 <span data-ttu-id="408ef-126">保存死锁文件后，您可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中打开该文件。</span><span class="sxs-lookup"><span data-stu-id="408ef-126">After you have saved the deadlock file, you can open the file in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="408ef-127">有关详细信息，请参阅[打开、查看和打印死锁文件 &#40;SQL Server Management Studio&#41;](open-view-and-print-a-deadlock-file-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="408ef-127">For more information, see [Open, View, and Print a Deadlock File &#40;SQL Server Management Studio&#41;](open-view-and-print-a-deadlock-file-sql-server-management-studio.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="408ef-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="408ef-128">See Also</span></span>  
 [<span data-ttu-id="408ef-129">使用 SQL Server Profiler 分析死锁</span><span class="sxs-lookup"><span data-stu-id="408ef-129">Analyze Deadlocks with SQL Server Profiler</span></span>](../../tools/sql-server-profiler/analyze-deadlocks-with-sql-server-profiler.md)  
  
  
