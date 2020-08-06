---
title: 基于文本的查询设计器用户界面 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10010"
- sql12.rtp.rptdesigner.dataview.genericquerydesigner.f1
helpviewer_keywords:
- text-based query designer [Reporting Services]
- query designers [Reporting Services], text-based
ms.assetid: 44b7c664-03aa-494e-a484-052b318e810c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1647d69246ba85dfbe0718799441c3687c0beca3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692637"
---
# <a name="text-based-query-designer-user-interface"></a><span data-ttu-id="8289d-102">基于文本的查询设计器用户界面</span><span class="sxs-lookup"><span data-stu-id="8289d-102">Text-based Query Designer User Interface</span></span>
  <span data-ttu-id="8289d-103">使用基于文本的查询设计器可以用数据源支持的查询语言来指定查询，还可以运行查询并在运行时查看结果。</span><span class="sxs-lookup"><span data-stu-id="8289d-103">Use the text-based query designer to specify a query using the query language supported by the data source, run the query, and view the results at design time.</span></span> <span data-ttu-id="8289d-104">您可以指定多个 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句，为自定义数据处理扩展插件指定查询或命令语法，还可以指定指定为表达式的查询。</span><span class="sxs-lookup"><span data-stu-id="8289d-104">You can specify multiple [!INCLUDE[tsql](../includes/tsql-md.md)] statements, query or command syntax for custom data processing extensions, and queries that are specified as expressions.</span></span> <span data-ttu-id="8289d-105">因为基于文本的查询设计器不会对查询进行预处理，并且能适应任何类型的查询语法，所以成为了众多数据源类型的默认查询设计器工具。</span><span class="sxs-lookup"><span data-stu-id="8289d-105">Because the text-based query designer does not preprocess the query and can accommodate any kind of query syntax, this is the default query designer tool for many data source types.</span></span>

 <span data-ttu-id="8289d-106">基于文本的查询设计器将显示工具栏和以下两个窗格：</span><span class="sxs-lookup"><span data-stu-id="8289d-106">The text-based query designer displays a toolbar and the following two panes:</span></span>

-   <span data-ttu-id="8289d-107">**查询**显示查询文本、表名或存储过程名称。</span><span class="sxs-lookup"><span data-stu-id="8289d-107">**Query** Shows the query text, table name, or stored procedure name.</span></span>

-   <span data-ttu-id="8289d-108">**结果** ：在设计时，显示查询的运行结果。</span><span class="sxs-lookup"><span data-stu-id="8289d-108">**Result** Shows the results of running the query at design time.</span></span>

## <a name="text-based-query-designer-toolbar"></a><span data-ttu-id="8289d-109">基于文本的查询设计器工具栏</span><span class="sxs-lookup"><span data-stu-id="8289d-109">Text-based Query Designer Toolbar</span></span>
 <span data-ttu-id="8289d-110">基于文本的查询设计器为所有命令类型都提供一个单一工具栏。</span><span class="sxs-lookup"><span data-stu-id="8289d-110">The text-based query designer provides a single toolbar for all the command types.</span></span> <span data-ttu-id="8289d-111">下表列出了该工具栏中的每个按钮及其功能。</span><span class="sxs-lookup"><span data-stu-id="8289d-111">The following table lists each button on the toolbar and its function.</span></span>

|<span data-ttu-id="8289d-112">Button</span><span class="sxs-lookup"><span data-stu-id="8289d-112">Button</span></span>|<span data-ttu-id="8289d-113">描述</span><span class="sxs-lookup"><span data-stu-id="8289d-113">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="8289d-114">**编辑为文本**</span><span class="sxs-lookup"><span data-stu-id="8289d-114">**Edit As Text**</span></span>|<span data-ttu-id="8289d-115">在基于文本的查询设计器和图形查询设计器之间切换。</span><span class="sxs-lookup"><span data-stu-id="8289d-115">Toggle between the text-based query designer and the graphical query designer.</span></span> <span data-ttu-id="8289d-116">并非所有的数据源类型都支持图形查询设计器。</span><span class="sxs-lookup"><span data-stu-id="8289d-116">Not all data source types support graphical query designers.</span></span>|
|<span data-ttu-id="8289d-117">**导入**</span><span class="sxs-lookup"><span data-stu-id="8289d-117">**Import**</span></span>|<span data-ttu-id="8289d-118">从文件或报表中导入现有的查询。</span><span class="sxs-lookup"><span data-stu-id="8289d-118">Import an existing query from a file or report.</span></span> <span data-ttu-id="8289d-119">仅支持 .sql 和 .rdl 文件类型。</span><span class="sxs-lookup"><span data-stu-id="8289d-119">Only file types sql and rdl are supported.</span></span> <span data-ttu-id="8289d-120">有关详细信息，请参阅 [报表的嵌入数据集和共享数据集（报表生成器和 SSRS）](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="8289d-120">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>|
|<span data-ttu-id="8289d-121">![运行查询](../analysis-services/media/rsqdicon-run.gif "运行查询")</span><span class="sxs-lookup"><span data-stu-id="8289d-121">![Run the query](../analysis-services/media/rsqdicon-run.gif "Run the query")</span></span>|<span data-ttu-id="8289d-122">运行查询并在“结果”窗格中显示结果集。</span><span class="sxs-lookup"><span data-stu-id="8289d-122">Run the query and display the result set in the Result pane.</span></span>|
|<span data-ttu-id="8289d-123">**命令类型**</span><span class="sxs-lookup"><span data-stu-id="8289d-123">**Command Type**</span></span>|<span data-ttu-id="8289d-124">选择 **Text**、 **StoredProcedure**或 **TableDirect**。</span><span class="sxs-lookup"><span data-stu-id="8289d-124">Select **Text**, **StoredProcedure**, or **TableDirect**.</span></span> <span data-ttu-id="8289d-125">如果存储过程带有参数，则单击工具栏上的 **“运行”** 时，将出现 **“定义查询参数”** 对话框，您可以根据需要填入值。</span><span class="sxs-lookup"><span data-stu-id="8289d-125">If a stored procedure has parameters, the **Define Query Parameters** dialog box appears when you click **Run** on the toolbar, and you can fill in values as needed.</span></span> <span data-ttu-id="8289d-126">请注意，如果存储过程返回多个结果集，则仅使用第一个结果集填充数据集。</span><span class="sxs-lookup"><span data-stu-id="8289d-126">Note that if a stored procedure returns more than one result set, only the first result set is used to populate the dataset.</span></span><br /><br /> <span data-ttu-id="8289d-127">所支持的命令类型因数据源类型而异。</span><span class="sxs-lookup"><span data-stu-id="8289d-127">Support for command type varies by data source type.</span></span> <span data-ttu-id="8289d-128">例如，仅 OLE DB 和 ODBC 支持 **TableDirect**。</span><span class="sxs-lookup"><span data-stu-id="8289d-128">For example, only OLE DB and ODBC support **TableDirect**.</span></span>|

### <a name="command-type-text"></a><span data-ttu-id="8289d-129">命令类型 Text</span><span class="sxs-lookup"><span data-stu-id="8289d-129">Command Type Text</span></span>
 <span data-ttu-id="8289d-130">创建 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据集时，默认情况下，报表设计器会显示图形查询设计器。</span><span class="sxs-lookup"><span data-stu-id="8289d-130">When you create a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] dataset, Report Designer displays the graphical query designer by default.</span></span> <span data-ttu-id="8289d-131">若要切换为基于文本的查询设计器，请单击工具栏上的“编辑为文本”切换按钮。</span><span class="sxs-lookup"><span data-stu-id="8289d-131">To switch to the text-based query designer, click the **Edit As Text** toggle button on the toolbar.</span></span> <span data-ttu-id="8289d-132">基于文本的查询设计器将显示两个窗格：“查询”窗格和“结果”窗格。</span><span class="sxs-lookup"><span data-stu-id="8289d-132">The text-based query designer presents two panes: the Query pane and the Result pane.</span></span> <span data-ttu-id="8289d-133">下图标出了每个窗格。</span><span class="sxs-lookup"><span data-stu-id="8289d-133">The following figure labels each pane.</span></span>

 <span data-ttu-id="8289d-134">![用于关系数据查询的通用查询设计器](../analysis-services/media/rsqd-dsaw-sql-generic.gif "用于关系数据查询的通用查询设计器")</span><span class="sxs-lookup"><span data-stu-id="8289d-134">![Generic query designer, for relational data query](../analysis-services/media/rsqd-dsaw-sql-generic.gif "Generic query designer, for relational data query")</span></span>

 <span data-ttu-id="8289d-135">下表介绍了每个窗格的功能。</span><span class="sxs-lookup"><span data-stu-id="8289d-135">The following table describes the function of each pane.</span></span>

|<span data-ttu-id="8289d-136">窗格</span><span class="sxs-lookup"><span data-stu-id="8289d-136">Pane</span></span>|<span data-ttu-id="8289d-137">函数</span><span class="sxs-lookup"><span data-stu-id="8289d-137">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="8289d-138">查询</span><span class="sxs-lookup"><span data-stu-id="8289d-138">Query</span></span>|<span data-ttu-id="8289d-139">显示 [!INCLUDE[tsql](../includes/tsql-md.md)] 查询文本。</span><span class="sxs-lookup"><span data-stu-id="8289d-139">Displays the [!INCLUDE[tsql](../includes/tsql-md.md)] query text.</span></span> <span data-ttu-id="8289d-140">使用此窗格可以编写或编辑 [!INCLUDE[tsql](../includes/tsql-md.md)] 查询。</span><span class="sxs-lookup"><span data-stu-id="8289d-140">Use this pane to write or edit a [!INCLUDE[tsql](../includes/tsql-md.md)] query.</span></span>|
|<span data-ttu-id="8289d-141">结果</span><span class="sxs-lookup"><span data-stu-id="8289d-141">Result</span></span>|<span data-ttu-id="8289d-142">显示查询的结果。</span><span class="sxs-lookup"><span data-stu-id="8289d-142">Displays the results of the query.</span></span> <span data-ttu-id="8289d-143">若要运行查询，请右键单击任意窗格，然后单击“运行”，或者单击工具栏中的“运行”按钮 。</span><span class="sxs-lookup"><span data-stu-id="8289d-143">To run the query, right-click in any pane and click **Run**, or click the **Run** button on the toolbar.</span></span>|

#### <a name="example"></a><span data-ttu-id="8289d-144">示例</span><span class="sxs-lookup"><span data-stu-id="8289d-144">Example</span></span>
 <span data-ttu-id="8289d-145">以下查询将从 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 数据库的 `Contact` 表中返回姓氏列表：</span><span class="sxs-lookup"><span data-stu-id="8289d-145">The following query returns the list of last names from the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database `Contact` table.</span></span>

```
SELECT LastName FROM Person.Person;
```

 <span data-ttu-id="8289d-146">您可以对命令类型文本使用任何 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句，包括 `EXEC` 语句。</span><span class="sxs-lookup"><span data-stu-id="8289d-146">You can use any [!INCLUDE[tsql](../includes/tsql-md.md)] statement for Command type Text, including `EXEC` statements.</span></span> <span data-ttu-id="8289d-147">下面的查询将调用 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 存储过程 `uspGetEmployeeManagers` ，并返回标识号为1的员工的命令链。</span><span class="sxs-lookup"><span data-stu-id="8289d-147">The following query calls the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] stored procedure `uspGetEmployeeManagers` and returns the chain-of-command for the employee with identification number 1.</span></span>

```
EXEC uspGetEmployeeManagers 1;
```

 <span data-ttu-id="8289d-148">单击工具栏上的 **“运行”** 时，将运行 **“查询”** 窗格中的命令，并在 **“结果”** 窗格中显示结果。</span><span class="sxs-lookup"><span data-stu-id="8289d-148">When you click **Run** on the toolbar, the command in the **Query** pane runs and the results are displayed in the **Result** pane.</span></span>

### <a name="command-type-storedprocedure"></a><span data-ttu-id="8289d-149">命令类型 StoredProcedure</span><span class="sxs-lookup"><span data-stu-id="8289d-149">Command Type StoredProcedure</span></span>
 <span data-ttu-id="8289d-150">选择“Command typeStoredProcedure”时，基于文本的查询设计器将显示两个窗格：“查询”窗格和“结果”窗格。</span><span class="sxs-lookup"><span data-stu-id="8289d-150">When you select **Command typeStoredProcedure**, the text-based query designer presents two panes: the Query pane and the Result pane.</span></span> <span data-ttu-id="8289d-151">在“查询”窗格中输入存储过程的名称，然后单击工具栏中的 **“运行”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="8289d-151">Enter the stored procedure name in the Query pane and click **Run** on the toolbar.</span></span> <span data-ttu-id="8289d-152">此时将打开“定义查询参数”对话框。</span><span class="sxs-lookup"><span data-stu-id="8289d-152">The Define Query Parameters dialog box opens.</span></span> <span data-ttu-id="8289d-153">输入存储过程的参数值。</span><span class="sxs-lookup"><span data-stu-id="8289d-153">Enter the parameter values for the stored procedure.</span></span> <span data-ttu-id="8289d-154">对于每个存储过程参数，都会创建一个报表参数。</span><span class="sxs-lookup"><span data-stu-id="8289d-154">A report parameter is created for every stored procedure parameter.</span></span>

#### <a name="example"></a><span data-ttu-id="8289d-155">示例</span><span class="sxs-lookup"><span data-stu-id="8289d-155">Example</span></span>
 <span data-ttu-id="8289d-156">以下查询调用 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 存储过程 `uspGetEmployeeManagers`。</span><span class="sxs-lookup"><span data-stu-id="8289d-156">The following query calls the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] stored procedure `uspGetEmployeeManagers`.</span></span> <span data-ttu-id="8289d-157">您必须在运行查询时，为雇员标识号参数输入值。</span><span class="sxs-lookup"><span data-stu-id="8289d-157">You must enter a value for the employee identification number parameter when you run the query.</span></span>

```
uspGetEmployeeManagers;
```

### <a name="command-type-tabledirect"></a><span data-ttu-id="8289d-158">命令类型 TableDirect</span><span class="sxs-lookup"><span data-stu-id="8289d-158">Command Type TableDirect</span></span>
 <span data-ttu-id="8289d-159">选择“Command typeTableDirect”时，基于文本的查询设计器将显示两个窗格：“查询”窗格和“结果”窗格。</span><span class="sxs-lookup"><span data-stu-id="8289d-159">When you select **Command typeTableDirect**, the text-based query designer presents two panes: the Query pane and the Result pane.</span></span> <span data-ttu-id="8289d-160">如果输入一个表并单击 **“运行”** 按钮，则将返回该表的所有列。</span><span class="sxs-lookup"><span data-stu-id="8289d-160">When you enter a table and click the **Run** button, all the columns for that table are returned.</span></span>

#### <a name="example"></a><span data-ttu-id="8289d-161">示例</span><span class="sxs-lookup"><span data-stu-id="8289d-161">Example</span></span>
 <span data-ttu-id="8289d-162">以下查询将返回 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 数据库中的所有客户的结果集。</span><span class="sxs-lookup"><span data-stu-id="8289d-162">The following query returns a result set for all customers in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span>

 `Sales.Customer`

 <span data-ttu-id="8289d-163">输入表名称 Sales. Customer 时，它等效于创建 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句 `SELECT * FROM Sales.Customer;` 。</span><span class="sxs-lookup"><span data-stu-id="8289d-163">When you enter the table name Sales.Customer, it is the equivalent of creating the [!INCLUDE[tsql](../includes/tsql-md.md)] statement `SELECT * FROM Sales.Customer;`.</span></span>

## <a name="see-also"></a><span data-ttu-id="8289d-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8289d-164">See Also</span></span>
 <span data-ttu-id="8289d-165">[报表设计器 SQL Server Data Tools 中的查询设计工具 &#40;SSRS&#41;](report-data/query-design-tools-ssrs.md) [报表嵌入数据集和共享数据集 &#40;报表生成器和 SSRS](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)&#41;SQL Server 的[连接](report-data/sql-server-connection-type-ssrs.md)类型 &#40;ssrs&#41;OLE DB ssrs &#40;[类型](report-data/ole-db-connection-type-ssrs.md)&#41;[Ssrs &#40;Ssrs](report-data/odbc-connection-type-ssrs.md)&#41;[报表嵌入数据集和共享数据集 &#40;报表生成器和 SSRS](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)&#41;[rsreportdesigner.config 配置文件](report-server/rsreportdesigner-configuration-file.md)</span><span class="sxs-lookup"><span data-stu-id="8289d-165">[Query Design Tools in Report Designer SQL Server Data Tools &#40;SSRS&#41;](report-data/query-design-tools-ssrs.md) [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) [SQL Server Connection Type &#40;SSRS&#41;](report-data/sql-server-connection-type-ssrs.md) [OLE DB Connection Type &#40;SSRS&#41;](report-data/ole-db-connection-type-ssrs.md) [ODBC Connection Type &#40;SSRS&#41;](report-data/odbc-connection-type-ssrs.md) [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) [RSReportDesigner Configuration File](report-server/rsreportdesigner-configuration-file.md)</span></span>


