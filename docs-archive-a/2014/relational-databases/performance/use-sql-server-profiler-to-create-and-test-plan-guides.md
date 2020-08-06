---
title: 使用 SQL Server Profiler 创建和测试计划指南 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- checking plan guides
- plan guides [SQL Server], testing
- plan guides [SQL Server], SQL Server Profiler
- matching queries to plan guides [SQL Server]
- testing plan guides
- SQL Server Profiler, plan guides
- plan guides [SQL Server], creating
- capturing query text [SQL Server]
- verifying plan guides
- Profiler [SQL Server Profiler], plan guides
- query-to-plan guide matching [SQL Server]
ms.assetid: 7018dbf0-1a1a-411a-88af-327bedf9cfbd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 543905343d74c9fbabe5f671d9021657ea5f76b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689870"
---
# <a name="use-sql-server-profiler-to-create-and-test-plan-guides"></a><span data-ttu-id="16259-102">使用 SQL Server Profiler 创建和测试计划指南</span><span class="sxs-lookup"><span data-stu-id="16259-102">Use SQL Server Profiler to Create and Test Plan Guides</span></span>
  <span data-ttu-id="16259-103">在创建计划指南时，可以使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 来捕获完全匹配的查询文本，以供 *sp_create_plan_guide* 存储过程的 **statement_text** 参数使用。</span><span class="sxs-lookup"><span data-stu-id="16259-103">When you are creating a plan guide, you can use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to capture the exact query text for use in the *statement_text* argument of the **sp_create_plan_guide** stored procedure.</span></span> <span data-ttu-id="16259-104">这有助于确保计划指南在编译时与查询匹配。</span><span class="sxs-lookup"><span data-stu-id="16259-104">This helps make sure that the plan guide will be matched to the query at compile time.</span></span> <span data-ttu-id="16259-105">创建计划指南后，还可以使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 来测试计划指南是否确实与查询匹配。</span><span class="sxs-lookup"><span data-stu-id="16259-105">After the plan guide is created, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] can also be used to test that the plan guide is, in fact, being matched to the query.</span></span> <span data-ttu-id="16259-106">通常，应使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 来验证查询是否与计划指南匹配，从而测试计划指南。</span><span class="sxs-lookup"><span data-stu-id="16259-106">Generally, you should test plan guides by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to verify that your query is being matched to your plan guide.</span></span>  
  
## <a name="capturing-query-text-by-using-sql-server-profiler"></a><span data-ttu-id="16259-107">使用 SQL Server Profiler 捕获查询文本</span><span class="sxs-lookup"><span data-stu-id="16259-107">Capturing Query Text by Using SQL Server Profiler</span></span>  
 <span data-ttu-id="16259-108">如果执行了查询，并使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 捕获到与提交到 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]时完全相同的文本，则可以创建完全匹配查询文本的 SQL 或 TEMPLATE 类型的计划指南。</span><span class="sxs-lookup"><span data-stu-id="16259-108">If you run a query and capture the text exactly as it was submitted to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can create a plan guide of type SQL or TEMPLATE that will match the query text exactly.</span></span> <span data-ttu-id="16259-109">这将确保计划指南可由查询优化器使用。</span><span class="sxs-lookup"><span data-stu-id="16259-109">This makes sure that the plan guide is used by the query optimizer.</span></span>  
  
 <span data-ttu-id="16259-110">思考以下作为独立批处理由应用程序提交的查询：</span><span class="sxs-lookup"><span data-stu-id="16259-110">Consider the following query that is submitted by an application as a stand-alone batch:</span></span>  
  
```  
SELECT COUNT(*) AS c  
FROM Sales.SalesOrderHeader AS h  
INNER JOIN Sales.SalesOrderDetail AS d  
  ON h.SalesOrderID = d.SalesOrderID  
WHERE h.OrderDate BETWEEN '20000101' and '20050101';  
```  
  
 <span data-ttu-id="16259-111">假设您要通过合并联接操作执行此查询，但 SHOWPLAN 指示该查询未使用合并联接。</span><span class="sxs-lookup"><span data-stu-id="16259-111">Suppose you want this query to execute using a merge join operation, but SHOWPLAN indicates that the query is not using a merge join.</span></span> <span data-ttu-id="16259-112">因为无法在应用程序中直接更改查询，所以可以改为创建计划指南来指定在编译时将 MERGE JOIN 查询提示追加到该查询。</span><span class="sxs-lookup"><span data-stu-id="16259-112">You cannot change the query directly in the application, so instead you create a plan guide to specify that the MERGE JOIN query hint be appended to the query at compile time.</span></span>  
  
 <span data-ttu-id="16259-113">若要捕获与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接收时完全相同的查询文本，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="16259-113">To capture the text of the query exactly as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] receives it, follow these steps:</span></span>  
  
1.  <span data-ttu-id="16259-114">启动 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 跟踪，确保已选中 **SQL:BatchStarting** 事件类型。</span><span class="sxs-lookup"><span data-stu-id="16259-114">Start a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] trace, making sure that the **SQL:BatchStarting** event type is selected.</span></span>  
  
2.  <span data-ttu-id="16259-115">使应用程序运行查询。</span><span class="sxs-lookup"><span data-stu-id="16259-115">Have the application run the query.</span></span>  
  
3.  <span data-ttu-id="16259-116">暂停 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 跟踪。</span><span class="sxs-lookup"><span data-stu-id="16259-116">Pause the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] Trace.</span></span>  
  
4.  <span data-ttu-id="16259-117">单击与该查询对应的 **SQL:BatchStarting** 事件。</span><span class="sxs-lookup"><span data-stu-id="16259-117">Click the **SQL:BatchStarting** event that corresponds to the query.</span></span>  
  
5.  <span data-ttu-id="16259-118">右键单击并选择“提取事件数据”。</span><span class="sxs-lookup"><span data-stu-id="16259-118">Right-click and select **Extract Event Data**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="16259-119">不要尝试通过从事件探查器跟踪窗口的下窗格中选中批处理文本来复制它。</span><span class="sxs-lookup"><span data-stu-id="16259-119">Do not try to copy the batch text by selecting it from the lower pane of the Profiler trace window.</span></span> <span data-ttu-id="16259-120">这可能会导致所创建的计划指南与原始批处理不匹配。</span><span class="sxs-lookup"><span data-stu-id="16259-120">This might cause the plan guide that you create to not match the original batch.</span></span>  
  
6.  <span data-ttu-id="16259-121">将事件数据保存到文件。</span><span class="sxs-lookup"><span data-stu-id="16259-121">Save the event data to a file.</span></span> <span data-ttu-id="16259-122">这就是批处理文本。</span><span class="sxs-lookup"><span data-stu-id="16259-122">This is the batch text.</span></span>  
  
7.  <span data-ttu-id="16259-123">在记事本中打开该批处理文本文件，将文本复制到复制和粘贴缓冲区。</span><span class="sxs-lookup"><span data-stu-id="16259-123">Open the batch text file in Notepad and copy the text to the copy and paste buffer.</span></span>  
  
8.  <span data-ttu-id="16259-124">创建计划指南，并将复制的文本粘贴到为 **@stmt**参数指定的引号 ( **@stmt** ) 内。</span><span class="sxs-lookup"><span data-stu-id="16259-124">Create the plan guide and paste the copied text inside the quotation marks (**''**) specified for the **@stmt** argument.</span></span> <span data-ttu-id="16259-125">必须将参数中的任何单引号替换为其他单引号，才能对参数中的任何单引号进行转义 **@stmt** 。</span><span class="sxs-lookup"><span data-stu-id="16259-125">You must escape any single quotation marks in the **@stmt** argument by preceding them with another single quotation mark.</span></span> <span data-ttu-id="16259-126">插入这些单引号时务必小心，不要添加或删除任何其他字符。</span><span class="sxs-lookup"><span data-stu-id="16259-126">Be careful not to add or remove any other characters when you insert these single quotation marks.</span></span> <span data-ttu-id="16259-127">例如，日期文本 **'** 20000101 **'** 必须分隔为 **''** 20000101 **''** 。</span><span class="sxs-lookup"><span data-stu-id="16259-127">For example, the date literal **'** 20000101 **'** must be delimited as **''** 20000101 **''**.</span></span>  
  
 <span data-ttu-id="16259-128">下面是该计划指南：</span><span class="sxs-lookup"><span data-stu-id="16259-128">Here is the plan guide:</span></span>  
  
```  
EXEC sp_create_plan_guide   
    @name = N'MyGuide1',  
    @stmt = N'<paste the text copied from the batch text file here>',  
    @type = N'SQL',  
    @module_or_batch = NULL,  
    @params = NULL,  
    @hints = N'OPTION (MERGE JOIN)';  
```  
  
## <a name="testing-plan-guides-by-using-sql-server-profiler"></a><span data-ttu-id="16259-129">使用 SQL Server Profiler 测试计划指南</span><span class="sxs-lookup"><span data-stu-id="16259-129">Testing Plan Guides by Using SQL Server Profiler</span></span>  
 <span data-ttu-id="16259-130">若要验证计划指南是否与查询匹配，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="16259-130">To verify that a plan guide is being matched to a query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="16259-131">启动 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 跟踪，确保已选中 **Showplan XML** 事件类型（位于“性能”节点下）。</span><span class="sxs-lookup"><span data-stu-id="16259-131">Start a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] trace, making certain that the **Showplan XML** event type is selected (located under the **Performance** node).</span></span>  
  
2.  <span data-ttu-id="16259-132">使应用程序运行查询。</span><span class="sxs-lookup"><span data-stu-id="16259-132">Have the application run the query.</span></span>  
  
3.  <span data-ttu-id="16259-133">暂停 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 跟踪。</span><span class="sxs-lookup"><span data-stu-id="16259-133">Pause the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] Trace.</span></span>  
  
4.  <span data-ttu-id="16259-134">在 **Showplan XML** 事件中查找受影响的查询。</span><span class="sxs-lookup"><span data-stu-id="16259-134">Find the **Showplan XML** event for the affected query.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="16259-135">无法使用 **“查询编译的 Showplan XML”** 事件。</span><span class="sxs-lookup"><span data-stu-id="16259-135">The **Showplan XML for Query Compile** event cannot be used.</span></span> <span data-ttu-id="16259-136">**PlanGuideDB** 在该事件中不存在。</span><span class="sxs-lookup"><span data-stu-id="16259-136">**PlanGuideDB** does not exist in that event.</span></span>  
  
5.  <span data-ttu-id="16259-137">如果计划指南的类型为 OBJECT 或 SQL，则请验证 **Showplan XML** 事件是否包含您希望与查询匹配的计划指南的 **PlanGuideDB** 和 **PlanGuideName** 属性。</span><span class="sxs-lookup"><span data-stu-id="16259-137">If the plan guide is of type OBJECT or SQL, verify that the **Showplan XML** event contains the **PlanGuideDB** and **PlanGuideName** attributes for the plan guide that you expected to match the query.</span></span> <span data-ttu-id="16259-138">或者，如果计划指南的类型为 TEMPLATE，则请验证 **Showplan XML** 事件是否包含预期计划指南的 **TemplatePlanGuideDB** 和 **TemplatePlanGuideName** 属性。</span><span class="sxs-lookup"><span data-stu-id="16259-138">Or, in the case of a TEMPLATE plan guide, verify that the **Showplan XML** event contains the **TemplatePlanGuideDB** and **TemplatePlanGuideName** attributes for the expected plan guide.</span></span> <span data-ttu-id="16259-139">这可以验证计划指南是否在运行。</span><span class="sxs-lookup"><span data-stu-id="16259-139">This verifies that the plan guide is working.</span></span> <span data-ttu-id="16259-140">这些属性包含在计划的 \<StmtSimple> 元素下。</span><span class="sxs-lookup"><span data-stu-id="16259-140">These attributes are contained under the **\<StmtSimple>** element of the plan.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16259-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="16259-141">See Also</span></span>  
 [<span data-ttu-id="16259-142">sp_create_plan_guide (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="16259-142">sp_create_plan_guide &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)  
  
  
