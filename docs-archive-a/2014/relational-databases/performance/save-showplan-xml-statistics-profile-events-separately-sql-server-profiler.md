---
title: 单独保存 Showplan XML Statistics Profile 事件 (SQL Server Profiler) | Microsoft Docs
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
ms.assetid: df393f13-d538-4d94-8155-9c2fdf5f755d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: be0c02f8396df81af803c365b9ede42610353ed3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689877"
---
# <a name="save-showplan-xml-statistics-profile-events-separately-sql-server-profiler"></a><span data-ttu-id="0b863-102">分别保存 Showplan XML Statistics Profile 事件 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="0b863-102">Save Showplan XML Statistics Profile Events Separately (SQL Server Profiler)</span></span>
  <span data-ttu-id="0b863-103">本主题说明如何使用 **将在跟踪中捕获的** Showplan XML Statistics Profile [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]事件保存到单独的 .SQLPlan 文件中。</span><span class="sxs-lookup"><span data-stu-id="0b863-103">This topic describes how to save **Showplan XML Statistics Profile** events that are captured in traces into separate .SQLPlan files by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="0b863-104">可以在 **中打开** Showplan XML Statistics Profile [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]事件文件，这样您就可以查看每个事件的图形执行计划。</span><span class="sxs-lookup"><span data-stu-id="0b863-104">You can open the **Showplan XML Statistics Profile** event files in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], which enables you to view the graphical execution plan for each event.</span></span>  
  
### <a name="to-save-showplan-xml-statistics-events-separately"></a><span data-ttu-id="0b863-105">分别保存 Showplan XML Statistics 事件</span><span class="sxs-lookup"><span data-stu-id="0b863-105">To save Showplan XML statistics events separately</span></span>  
  
1.  <span data-ttu-id="0b863-106">在 **“文件”** 菜单上，单击 **“新建跟踪”** ，再连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="0b863-106">On the **File** menu, click **New Trace**, and then connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="0b863-107">此时，将显示 **“跟踪属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="0b863-107">The **Trace Properties** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0b863-108">如果你选中了“建立连接后立即开始跟踪”\*\*\*\*，那么系统不会显示“跟踪属性”\*\*\*\* 对话框，而是会开始进行跟踪。</span><span class="sxs-lookup"><span data-stu-id="0b863-108">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box does not appear and the trace begins instead.</span></span> <span data-ttu-id="0b863-109">若要关闭此设置，请在“工具”菜单上，单击“选项”，然后清除“建立连接后立即开始跟踪”复选框。</span><span class="sxs-lookup"><span data-stu-id="0b863-109">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="0b863-110">在 **“跟踪属性”** 对话框内的 **“跟踪名称”** 框中键入跟踪的名称。</span><span class="sxs-lookup"><span data-stu-id="0b863-110">In the **Trace Properties** dialog box, type a name for the trace in the **Trace name** box.</span></span>  
  
3.  <span data-ttu-id="0b863-111">在 **“使用模板”** 列表中，选择要作为跟踪基础的跟踪模板，或选择 **“空”** （如果不想使用模板）。</span><span class="sxs-lookup"><span data-stu-id="0b863-111">In the **Use the template** list, select a trace template to base the trace on, or select **Blank** if you do not want to use a template.</span></span>  
  
4.  <span data-ttu-id="0b863-112">执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="0b863-112">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="0b863-113">单击“保存到文件”\*\*\*\*，将跟踪内容捕获到文件中。</span><span class="sxs-lookup"><span data-stu-id="0b863-113">Click**Save to file**to capture the trace to a file.</span></span> <span data-ttu-id="0b863-114">指定 **“设置最大文件大小”** 的值。</span><span class="sxs-lookup"><span data-stu-id="0b863-114">Specify a value for **Set maximum file size**.</span></span>  
  
         <span data-ttu-id="0b863-115">（可选）选择 "**启用文件滚动更新**" 和 "**服务器处理跟踪数据**"。</span><span class="sxs-lookup"><span data-stu-id="0b863-115">Optionally select **Enable file rollover** and **Server processes trace data**.</span></span>  
  
    -   <span data-ttu-id="0b863-116">单击“保存到表”\*\*\*\*，将跟踪捕获到数据库表中。</span><span class="sxs-lookup"><span data-stu-id="0b863-116">Click**Save to table** to capture the trace to a database table.</span></span>  
  
         <span data-ttu-id="0b863-117">（可选）单击 "**设置最大行**" 并指定一个值。</span><span class="sxs-lookup"><span data-stu-id="0b863-117">Optionally click **Set maximum rows**, and specify a value.</span></span>  
  
5.  <span data-ttu-id="0b863-118">也可以选中 "**启用跟踪停止时间**" 复选框，并指定停止日期和时间。</span><span class="sxs-lookup"><span data-stu-id="0b863-118">Optionally select the **Enable trace stop time** check box, and specify a stop date and time.</span></span>  
  
6.  <span data-ttu-id="0b863-119">单击“事件选择”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="0b863-119">Click the **Events Selection**tab.</span></span>  
  
7.  <span data-ttu-id="0b863-120">在“事件”\*\*\*\* 数据列中，展开“性能”\*\*\*\* 事件类别，然后选中“Showplan XML Statistics Profile”\*\*\*\* 复选框。</span><span class="sxs-lookup"><span data-stu-id="0b863-120">In the **Events**data column, expand the **Performance**event category, and then select the **Showplan XML Statistics Profile**check box.</span></span> <span data-ttu-id="0b863-121">如果 **Performance** 事件类别不可用，请选中 **“显示所有事件”** 以显示该类别。</span><span class="sxs-lookup"><span data-stu-id="0b863-121">If the **Performance** event category is not available, check **Show all events** to display it.</span></span>  
  
     <span data-ttu-id="0b863-122">“事件提取设置”\*\*\*\* 选项卡将添加到“跟踪属性”\*\*\*\* 对话框中。</span><span class="sxs-lookup"><span data-stu-id="0b863-122">The **Events Extraction Settings**tab is added to the **Trace Properties**dialog.</span></span>  
  
8.  <span data-ttu-id="0b863-123">在“事件提取设置”\*\*\*\* 选项卡上，单击“分别保存 XML 显示计划事件”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0b863-123">On the **Events Extraction Settings**tab, click **Save XML Showplan events separately**.</span></span>  
  
9. <span data-ttu-id="0b863-124">在 **“另存为”** 对话框中，输入存储 **Showplan XML Statistics Profile** 事件的文件名。</span><span class="sxs-lookup"><span data-stu-id="0b863-124">In the **Save As** dialog box, enter the file name to store the **Showplan XML Statistics Profile** events.</span></span>  
  
10. <span data-ttu-id="0b863-125">单击“单个文件中的所有批”\*\*\*\*，将所有“Showplan XML Statistics Profile”\*\*\*\* 事件都保存到一个 XML 文件中；或者，单击“不同文件中的每个 XML 显示计划批”\*\*\*\*，为每个“Showplan XML Statistics Profile”\*\*\*\* 事件都新建一个 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="0b863-125">Click **All batches in a single file** to save all **Showplan XML Statistics Profile** events in a single XML file, or click **Each XML Showplan batch in a distinct file**to create a new XML file for each **Showplan XML Statistics Profile** event.</span></span>  
  
11. <span data-ttu-id="0b863-126">若要在 SQL Server Management Studio 中查看 **Showplan XML Statistics Profile** 事件文件，请在 **“文件”** 菜单上，指向 **“打开”**，然后单击 **“文件”**。</span><span class="sxs-lookup"><span data-stu-id="0b863-126">To view the **Showplan XML Statistics Profile** event file in SQL Server Management Studio, on the **File** menu, point to **Open**, and click **File**.</span></span> <span data-ttu-id="0b863-127">导航到保存 **Showplan XML Statistics Profile** 事件文件的目录，以选择一个事件文件并将其打开。</span><span class="sxs-lookup"><span data-stu-id="0b863-127">Navigate to the directory where you saved the **Showplan XML Statistics Profile** event file or files to select one and open it.</span></span> <span data-ttu-id="0b863-128">**Showplan XML Statistics Profile** 事件文件的文件扩展名为 .SQLPlan。</span><span class="sxs-lookup"><span data-stu-id="0b863-128">**Showplan XML Statistics Profile** event files have a .SQLPlan file extension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b863-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0b863-129">See Also</span></span>  
 [<span data-ttu-id="0b863-130">在 SQL Server Profiler 中使用 SHOWPLAN 结果来分析查询</span><span class="sxs-lookup"><span data-stu-id="0b863-130">Analyze Queries with SHOWPLAN Results in SQL Server Profiler</span></span>](../../tools/sql-server-profiler/analyze-queries-with-showplan-results-in-sql-server-profiler.md)  
  
  
