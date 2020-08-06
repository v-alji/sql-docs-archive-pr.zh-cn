---
title: 单独保存 Showplan XML 事件 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Showplan XML events
- saving Showplan XML events
- events [SQL Server], Showplan XML
ms.assetid: 33320a7a-36e8-401c-876d-5b82c49abd85
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 240fb408bb3ed8585ecc915ba4829ac21285d241
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590736"
---
# <a name="save-showplan-xml-events-separately-sql-server-profiler"></a><span data-ttu-id="56888-102">分别保存 Showplan XML 事件 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="56888-102">Save Showplan XML Events Separately (SQL Server Profiler)</span></span>
  <span data-ttu-id="56888-103">本主题介绍了如何使用 **将在跟踪中捕获到的** Showplan XML [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]事件分别保存到单独的 .SQLPlan 文件中。</span><span class="sxs-lookup"><span data-stu-id="56888-103">This topic describes how to save **Showplan XML** events that are captured in traces into separate .SQLPlan files by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="56888-104">您可以在 **中打开** Showplan XML [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]事件文件，从中可以查看每个事件的以图形表示的执行计划。</span><span class="sxs-lookup"><span data-stu-id="56888-104">You can open the **Showplan XML** event files in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], which enables you to view the graphical execution plan for each event.</span></span>  
  
### <a name="to-save-showplan-xml-events-separately"></a><span data-ttu-id="56888-105">分别保存 Showplan XML 事件</span><span class="sxs-lookup"><span data-stu-id="56888-105">To save Showplan XML events separately</span></span>  
  
1.  <span data-ttu-id="56888-106">在 **“文件”** 菜单上，单击 **“新建跟踪”** ，再连接到 SQL Server 实例。</span><span class="sxs-lookup"><span data-stu-id="56888-106">On the **File** menu, click **New Trace**, and then connect to an instance of SQL Server.</span></span>  
  
     <span data-ttu-id="56888-107">将出现“跟踪属性”对话框。 **“跟踪属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="56888-107">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="56888-108">如果选择“建立连接后立即开始跟踪”，则不会显示“跟踪属性”对话框，而是开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="56888-108">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="56888-109">若要关闭此设置，请在“工具”菜单上，单击“选项”，然后清除“建立连接后立即开始跟踪”复选框。</span><span class="sxs-lookup"><span data-stu-id="56888-109">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="56888-110">在 **“跟踪属性”** 对话框内的 **“跟踪名称”** 框中键入跟踪的名称。</span><span class="sxs-lookup"><span data-stu-id="56888-110">In the **Trace Properties** dialog box, type a name for the trace in the **Trace name** box.</span></span>  
  
3.  <span data-ttu-id="56888-111">在 **“使用模板”** 列表中，为此跟踪选择一个跟踪模板；如果不想使用模板，请选择 **“空白”** 。</span><span class="sxs-lookup"><span data-stu-id="56888-111">In the **Use the template** list, select a trace template on which to base the trace, or select **Blank** if you do not want to use a template.</span></span>  
  
4.  <span data-ttu-id="56888-112">执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="56888-112">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="56888-113">选中“保存到文件”\*\*\*\* 复选框以将跟踪捕获到文件中。</span><span class="sxs-lookup"><span data-stu-id="56888-113">Select the**Save to file** check box to capture the trace to a file.</span></span> <span data-ttu-id="56888-114">指定 **“设置最大文件大小”** 的值。</span><span class="sxs-lookup"><span data-stu-id="56888-114">Specify a value for **Set maximum file size**.</span></span> <span data-ttu-id="56888-115">也可以选中 **“启用文件滚动更新”** 复选框和 **“服务器处理跟踪数据”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="56888-115">Optionally, select the **Enable file rollover** and **Server processes trace data** check boxes.</span></span>  
  
    -   <span data-ttu-id="56888-116">选中“保存到表”\*\*\*\* 复选框以将跟踪捕获到数据库表中。</span><span class="sxs-lookup"><span data-stu-id="56888-116">Select the**Save to table** check box to capture the trace to a database table.</span></span> <span data-ttu-id="56888-117">（可选）单击 "**设置最大行**" 并指定一个值。</span><span class="sxs-lookup"><span data-stu-id="56888-117">Optionally click **Set maximum rows**, and specify a value.</span></span>  
  
5.  <span data-ttu-id="56888-118">根据需要，可以选中 **“启用跟踪停止时间”** 复选框，再指定停止日期和时间。</span><span class="sxs-lookup"><span data-stu-id="56888-118">Optionally, select the **Enable trace stop time** check box, and specify a stop date and time.</span></span>  
  
6.  <span data-ttu-id="56888-119">单击“事件选择”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="56888-119">Click the **Events Selection**tab.</span></span>  
  
7.  <span data-ttu-id="56888-120">在“事件”\*\*\*\* 数据列中，展开“性能”\*\*\*\* 事件类别，然后选中“Showplan XML”\*\*\*\* 复选框。</span><span class="sxs-lookup"><span data-stu-id="56888-120">In the **Events**data column, expand the **Performance**event category, and then select the **Showplan XML**check box.</span></span> <span data-ttu-id="56888-121">如果 **Performance** 事件类别不可用，请选中 **“显示所有事件”** 以显示该类别。</span><span class="sxs-lookup"><span data-stu-id="56888-121">If the **Performance** event category is not available, check **Show all events** to display it.</span></span>  
  
     <span data-ttu-id="56888-122">“事件提取设置”\*\*\*\* 选项卡将添加到“跟踪属性”\*\*\*\* 对话框中。</span><span class="sxs-lookup"><span data-stu-id="56888-122">The **Events Extraction Settings**tab is added to the **Trace Properties**dialog box.</span></span>  
  
8.  <span data-ttu-id="56888-123">在“事件提取设置”\*\*\*\* 选项卡上，单击“分别保存 XML 显示计划事件”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="56888-123">On the **Events Extraction Settings**tab, click **Save XML Showplan events separately**.</span></span>  
  
9. <span data-ttu-id="56888-124">在 **“另存为”** 对话框中，输入要在其中存储 **Showplan XML** 事件的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="56888-124">In the **Save As** dialog box, enter the name of the file in which to store the **Showplan XML** events.</span></span>  
  
10. <span data-ttu-id="56888-125">单击“单个文件中的所有 XML 显示计划批”\*\*\*\* 将所有 **Showplan XML** 事件保存到一个 XML 文件中，或单击“不同文件中的每个 XML 显示计划批”\*\*\*\* 为每个 **Showplan XML** 事件创建一个新的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="56888-125">Click **All XML Showplan batches in a single file** to save all **Showplan XML** events in a single XML file, or click **Each XML Showplan batch in a distinct file**to create a new XML file for each **Showplan XML** event.</span></span>  
  
11. <span data-ttu-id="56888-126">若要在 SQL Server Management Studio 中查看 **Showplan XML** 事件文件，请在 **“文件”** 菜单上指向 **“打开”**，然后单击 **“文件”**。</span><span class="sxs-lookup"><span data-stu-id="56888-126">To view the **Showplan XML** event file in SQL Server Management Studio, on the **File** menu, point to **Open**, and click **File**.</span></span> <span data-ttu-id="56888-127">导航到保存 **Showplan XML** 事件文件的目录，选择一个文件并打开它。</span><span class="sxs-lookup"><span data-stu-id="56888-127">Navigate to the directory where you saved the **Showplan XML** event file or files to select one and open it.</span></span> <span data-ttu-id="56888-128">**Showplan XML** 事件文件带有 .SQLPlan 文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="56888-128">**Showplan XML** event files have a .SQLPlan file extension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56888-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="56888-129">See Also</span></span>  
 [<span data-ttu-id="56888-130">在 SQL Server Profiler 中使用 SHOWPLAN 结果来分析查询</span><span class="sxs-lookup"><span data-stu-id="56888-130">Analyze Queries with SHOWPLAN Results in SQL Server Profiler</span></span>](../../tools/sql-server-profiler/analyze-queries-with-showplan-results-in-sql-server-profiler.md)  
  
  
