---
title: 基于文本的查询设计器用户界面（报表生成器）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10010"
helpviewer_keywords:
- query designers, text-based
ms.assetid: 89fddca5-bd96-4128-9072-5348d1b6e02c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c1415bdfada46ac09c9ab04047d63484593933e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577305"
---
# <a name="text-based-query-designer-user-interface-report-builder"></a><span data-ttu-id="da0d6-102">基于文本的查询设计器用户界面（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="da0d6-102">Text-based Query Designer User Interface (Report Builder)</span></span>
  <span data-ttu-id="da0d6-103">使用基于文本的查询设计器可以用数据源支持的查询语言来指定查询，还可以运行查询并在运行时查看结果。</span><span class="sxs-lookup"><span data-stu-id="da0d6-103">Use the text-based query designer to specify a query using the query language supported by the data source, run the query, and view the results at design time.</span></span> <span data-ttu-id="da0d6-104">您可以指定多个 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句，为自定义数据处理扩展插件指定查询或命令语法，还可以指定指定为表达式的查询。</span><span class="sxs-lookup"><span data-stu-id="da0d6-104">You can specify multiple [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements, query or command syntax for custom data processing extensions, and queries that are specified as expressions.</span></span> <span data-ttu-id="da0d6-105">因为基于文本的查询设计器不会对查询进行预处理，并且能适应任何类型的查询语法，所以成为了众多数据源类型的默认查询设计器工具。</span><span class="sxs-lookup"><span data-stu-id="da0d6-105">Because the text-based query designer does not preprocess the query and can accommodate any kind of query syntax, this is the default query designer tool for many data source types.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="da0d6-106">用户创建和运行查询时访问数据源。</span><span class="sxs-lookup"><span data-stu-id="da0d6-106">Users access data sources when they create and run queries.</span></span> <span data-ttu-id="da0d6-107">您应授予对数据源的最小权限（如只读权限）。</span><span class="sxs-lookup"><span data-stu-id="da0d6-107">You should grant minimal permissions on the data sources, such as read-only permissions.</span></span>

 <span data-ttu-id="da0d6-108">基于文本的查询设计器将显示工具栏和以下两个窗格：</span><span class="sxs-lookup"><span data-stu-id="da0d6-108">The text-based query designer displays a toolbar and the following two panes:</span></span>

-   <span data-ttu-id="da0d6-109">**查询** ：根据查询类型的不同，显示查询文本、表名或存储过程名称。</span><span class="sxs-lookup"><span data-stu-id="da0d6-109">**Query** Shows the query text, table name, or stored procedure name depending on the query type.</span></span> <span data-ttu-id="da0d6-110">并非所有查询类型都适用于所有数据源类型。</span><span class="sxs-lookup"><span data-stu-id="da0d6-110">Not all query types are available for all data source types.</span></span> <span data-ttu-id="da0d6-111">例如，只有数据源类型 OLE DB 支持表名。</span><span class="sxs-lookup"><span data-stu-id="da0d6-111">For example, table name is supported only for the data source type OLE DB.</span></span>

-   <span data-ttu-id="da0d6-112">**结果** ：在设计时，显示查询的运行结果。</span><span class="sxs-lookup"><span data-stu-id="da0d6-112">**Result** Shows the results of running the query at design time.</span></span>

## <a name="text-based-query-designer-toolbar"></a><span data-ttu-id="da0d6-113">基于文本的查询设计器工具栏</span><span class="sxs-lookup"><span data-stu-id="da0d6-113">Text-based Query Designer Toolbar</span></span>
 <span data-ttu-id="da0d6-114">基于文本的查询设计器为所有命令类型都提供一个单一工具栏。</span><span class="sxs-lookup"><span data-stu-id="da0d6-114">The text-based query designer provides a single toolbar for all the command types.</span></span> <span data-ttu-id="da0d6-115">下表列出了该工具栏中的每个按钮及其功能。</span><span class="sxs-lookup"><span data-stu-id="da0d6-115">The following table lists each button on the toolbar and its function.</span></span>

|<span data-ttu-id="da0d6-116">Button</span><span class="sxs-lookup"><span data-stu-id="da0d6-116">Button</span></span>|<span data-ttu-id="da0d6-117">描述</span><span class="sxs-lookup"><span data-stu-id="da0d6-117">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="da0d6-118">**编辑为文本**</span><span class="sxs-lookup"><span data-stu-id="da0d6-118">**Edit As Text**</span></span>|<span data-ttu-id="da0d6-119">在基于文本的查询设计器和图形查询设计器之间切换。</span><span class="sxs-lookup"><span data-stu-id="da0d6-119">Toggle between the text-based query designer and the graphical query designer.</span></span> <span data-ttu-id="da0d6-120">并非所有的数据源类型都支持图形查询设计器。</span><span class="sxs-lookup"><span data-stu-id="da0d6-120">Not all data source types support graphical query designers.</span></span>|
|<span data-ttu-id="da0d6-121">**导入**</span><span class="sxs-lookup"><span data-stu-id="da0d6-121">**Import**</span></span>|<span data-ttu-id="da0d6-122">从文件或报表中导入现有的查询。</span><span class="sxs-lookup"><span data-stu-id="da0d6-122">Import an existing query from a file or report.</span></span> <span data-ttu-id="da0d6-123">仅支持 sql 和 rdl 文件类型</span><span class="sxs-lookup"><span data-stu-id="da0d6-123">Only file types sql and rdl are supported</span></span>|
|<span data-ttu-id="da0d6-124">![运行查询](../../analysis-services/media/rsqdicon-run.gif "运行查询")</span><span class="sxs-lookup"><span data-stu-id="da0d6-124">![Run the query](../../analysis-services/media/rsqdicon-run.gif "Run the query")</span></span>|<span data-ttu-id="da0d6-125">运行查询并在“结果”窗格中显示结果集。</span><span class="sxs-lookup"><span data-stu-id="da0d6-125">Run the query and display the result set in the Result pane.</span></span>|
|<span data-ttu-id="da0d6-126">**命令类型**</span><span class="sxs-lookup"><span data-stu-id="da0d6-126">**Command Type**</span></span>|<span data-ttu-id="da0d6-127">选择 **Text**、 **StoredProcedure**或 **TableDirect**。</span><span class="sxs-lookup"><span data-stu-id="da0d6-127">Select **Text**, **StoredProcedure**, or **TableDirect**.</span></span> <span data-ttu-id="da0d6-128">如果存储过程带有参数，则单击工具栏上的 **“运行”** 时，将出现 **“定义查询参数”** 对话框，您可以根据需要填入值。</span><span class="sxs-lookup"><span data-stu-id="da0d6-128">If a stored procedure has parameters, the **Define Query Parameters** dialog box appears when you click **Run** on the toolbar, and you can fill in values as needed.</span></span><br /><br /> <span data-ttu-id="da0d6-129">注意：如果存储过程返回多个结果集，则仅使用第一个结果集填充数据集。</span><span class="sxs-lookup"><span data-stu-id="da0d6-129">Note: If a stored procedure returns more than one result set, only the first result set is used to populate the dataset.</span></span>|

### <a name="command-type-text"></a><span data-ttu-id="da0d6-130">命令类型 Text</span><span class="sxs-lookup"><span data-stu-id="da0d6-130">Command Type Text</span></span>
 <span data-ttu-id="da0d6-131">创建 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据集时，默认情况下，关系查询设计器将会打开。</span><span class="sxs-lookup"><span data-stu-id="da0d6-131">When you create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dataset, the relational query designer opens by default.</span></span> <span data-ttu-id="da0d6-132">若要切换为基于文本的查询设计器，请单击工具栏上的“编辑为文本”切换按钮。</span><span class="sxs-lookup"><span data-stu-id="da0d6-132">To switch to the text-based query designer, click the **Edit As Text** toggle button on the toolbar.</span></span> <span data-ttu-id="da0d6-133">基于文本的查询设计器将显示两个窗格：“查询”窗格和“结果”窗格。</span><span class="sxs-lookup"><span data-stu-id="da0d6-133">The text-based query designer presents two panes: the Query pane and the Result pane.</span></span> <span data-ttu-id="da0d6-134">下图标出了每个窗格。</span><span class="sxs-lookup"><span data-stu-id="da0d6-134">The following figure labels each pane.</span></span>

 <span data-ttu-id="da0d6-135">![用于关系数据查询的通用查询设计器](../../analysis-services/media/rsqd-dsaw-sql-generic.gif "用于关系数据查询的通用查询设计器")</span><span class="sxs-lookup"><span data-stu-id="da0d6-135">![Generic query designer, for relational data query](../../analysis-services/media/rsqd-dsaw-sql-generic.gif "Generic query designer, for relational data query")</span></span>

 <span data-ttu-id="da0d6-136">下表介绍了每个窗格的功能。</span><span class="sxs-lookup"><span data-stu-id="da0d6-136">The following table describes the function of each pane.</span></span>

|<span data-ttu-id="da0d6-137">窗格</span><span class="sxs-lookup"><span data-stu-id="da0d6-137">Pane</span></span>|<span data-ttu-id="da0d6-138">函数</span><span class="sxs-lookup"><span data-stu-id="da0d6-138">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="da0d6-139">查询</span><span class="sxs-lookup"><span data-stu-id="da0d6-139">Query</span></span>|<span data-ttu-id="da0d6-140">显示 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 查询文本。</span><span class="sxs-lookup"><span data-stu-id="da0d6-140">Displays the [!INCLUDE[tsql](../../../includes/tsql-md.md)] query text.</span></span> <span data-ttu-id="da0d6-141">使用此窗格可以编写或编辑 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 查询。</span><span class="sxs-lookup"><span data-stu-id="da0d6-141">Use this pane to write or edit a [!INCLUDE[tsql](../../../includes/tsql-md.md)] query.</span></span>|
|<span data-ttu-id="da0d6-142">结果</span><span class="sxs-lookup"><span data-stu-id="da0d6-142">Result</span></span>|<span data-ttu-id="da0d6-143">显示查询的结果。</span><span class="sxs-lookup"><span data-stu-id="da0d6-143">Displays the results of the query.</span></span> <span data-ttu-id="da0d6-144">若要运行查询，请右键单击任意窗格，然后单击“运行”，或者单击工具栏中的“运行”按钮 。</span><span class="sxs-lookup"><span data-stu-id="da0d6-144">To run the query, right-click in any pane and click **Run**, or click the **Run** button on the toolbar.</span></span>|

#### <a name="example"></a><span data-ttu-id="da0d6-145">示例</span><span class="sxs-lookup"><span data-stu-id="da0d6-145">Example</span></span>
 <span data-ttu-id="da0d6-146">下面的查询将返回该架构的 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] **2008**数据库表中的姓氏列表 `ContactType` `Person` 。</span><span class="sxs-lookup"><span data-stu-id="da0d6-146">The following query returns the list of last names from the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)]**2008** database `ContactType` table for the `Person` schema.</span></span>

```
SELECT Name FROM Person.ContactType
```

 <span data-ttu-id="da0d6-147">单击工具栏上的 **“运行”** 时，将运行 **“查询”** 窗格中的命令，并在 **“结果”** 窗格中显示结果。</span><span class="sxs-lookup"><span data-stu-id="da0d6-147">When you click **Run** on the toolbar, the command in the **Query** pane runs and the results are displayed in the **Result** pane.</span></span> <span data-ttu-id="da0d6-148">结果集显示 20 种类型的联系人列表，例如，所有者或销售代理。</span><span class="sxs-lookup"><span data-stu-id="da0d6-148">The resultset displays a list of 20 types of contacts, for example, Owner or Sales Agent.</span></span>

### <a name="command-type-storedprocedure"></a><span data-ttu-id="da0d6-149">命令类型 StoredProcedure</span><span class="sxs-lookup"><span data-stu-id="da0d6-149">Command Type StoredProcedure</span></span>
 <span data-ttu-id="da0d6-150">选择“Command typeStoredProcedure”时，基于文本的查询设计器将显示两个窗格：“查询”窗格和“结果”窗格。</span><span class="sxs-lookup"><span data-stu-id="da0d6-150">When you select **Command typeStoredProcedure**, the text-based query designer presents two panes: the Query pane and the Result pane.</span></span> <span data-ttu-id="da0d6-151">在“查询”窗格中输入存储过程的名称，然后单击工具栏中的 **“运行”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="da0d6-151">Enter the stored procedure name in the Query pane and click **Run** on the toolbar.</span></span> <span data-ttu-id="da0d6-152">如果存储过程使用参数，将打开 **“定义查询参数”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="da0d6-152">If the stored procedures uses parameters, the **Define Query Parameters** dialog box opens.</span></span> <span data-ttu-id="da0d6-153">输入存储过程的参数值。</span><span class="sxs-lookup"><span data-stu-id="da0d6-153">Enter the parameter values for the stored procedure.</span></span> <span data-ttu-id="da0d6-154">对于每个存储过程输入参数，都会创建一个报表参数。</span><span class="sxs-lookup"><span data-stu-id="da0d6-154">A report parameter is created for every stored procedure input parameter.</span></span>

 <span data-ttu-id="da0d6-155">下图显示运行存储过程时的“查询”和“结果”窗格。</span><span class="sxs-lookup"><span data-stu-id="da0d6-155">The following figure shows the Query and Results panes when you run a stored procedure.</span></span> <span data-ttu-id="da0d6-156">在此示例中，输入参数为常量。</span><span class="sxs-lookup"><span data-stu-id="da0d6-156">In this case, the input parameters are constants.</span></span>

 <span data-ttu-id="da0d6-157">![基于文本的查询设计器中的存储过程](../../analysis-services/media/rs-relational-text-sp.gif "基于文本的查询设计器中的存储过程")</span><span class="sxs-lookup"><span data-stu-id="da0d6-157">![Stored procedure in text-based query designer](../../analysis-services/media/rs-relational-text-sp.gif "Stored procedure in text-based query designer")</span></span>

 <span data-ttu-id="da0d6-158">下表介绍了每个窗格的功能。</span><span class="sxs-lookup"><span data-stu-id="da0d6-158">The following table describes the function of each pane.</span></span>

|<span data-ttu-id="da0d6-159">窗格</span><span class="sxs-lookup"><span data-stu-id="da0d6-159">Pane</span></span>|<span data-ttu-id="da0d6-160">函数</span><span class="sxs-lookup"><span data-stu-id="da0d6-160">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="da0d6-161">查询</span><span class="sxs-lookup"><span data-stu-id="da0d6-161">Query</span></span>|<span data-ttu-id="da0d6-162">显示存储过程的名称和所有输入参数。</span><span class="sxs-lookup"><span data-stu-id="da0d6-162">Displays the name of the stored procedure and any input parameters.</span></span>|
|<span data-ttu-id="da0d6-163">结果</span><span class="sxs-lookup"><span data-stu-id="da0d6-163">Result</span></span>|<span data-ttu-id="da0d6-164">显示查询的结果。</span><span class="sxs-lookup"><span data-stu-id="da0d6-164">Displays the results of the query.</span></span> <span data-ttu-id="da0d6-165">若要运行查询，请右键单击任意窗格，然后单击“运行”，或者单击工具栏中的“运行”按钮 。</span><span class="sxs-lookup"><span data-stu-id="da0d6-165">To run the query, right-click in any pane and click **Run**, or click the **Run** button on the toolbar.</span></span>|

#### <a name="example"></a><span data-ttu-id="da0d6-166">示例</span><span class="sxs-lookup"><span data-stu-id="da0d6-166">Example</span></span>
 <span data-ttu-id="da0d6-167">下面的查询将调用 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] **2008**存储过程 `uspGetWhereUsedProductID` 。</span><span class="sxs-lookup"><span data-stu-id="da0d6-167">The following query calls the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)]**2008** stored procedure `uspGetWhereUsedProductID`.</span></span> <span data-ttu-id="da0d6-168">在运行查询时，您必须为产品标识号参数输入一个值。</span><span class="sxs-lookup"><span data-stu-id="da0d6-168">You must enter a value for the product identification number parameter when you run the query.</span></span>

```
uspGetWhereUsedProductID
```

 <span data-ttu-id="da0d6-169">单击“运行”( **!** ) 按钮。</span><span class="sxs-lookup"><span data-stu-id="da0d6-169">Click the **Run** (**!**) button.</span></span> <span data-ttu-id="da0d6-170">提示输入查询参数的值时，请使用下表来输入值。</span><span class="sxs-lookup"><span data-stu-id="da0d6-170">When prompted for the query parameters, use the following table to enter values.</span></span>

|||
|-|-|
|*@StartProductID*|<span data-ttu-id="da0d6-171">820</span><span class="sxs-lookup"><span data-stu-id="da0d6-171">820</span></span>|
|*@CheckDate*|<span data-ttu-id="da0d6-172">20010115</span><span class="sxs-lookup"><span data-stu-id="da0d6-172">20010115</span></span>|

 <span data-ttu-id="da0d6-173">对于指定日期，结果集显示使用指定组件号的 13 个产品标识符列表。</span><span class="sxs-lookup"><span data-stu-id="da0d6-173">For the specified date, the result set displays a list of 13 product identifiers that used the specified component number.</span></span>

### <a name="command-type-tabledirect"></a><span data-ttu-id="da0d6-174">命令类型 TableDirect</span><span class="sxs-lookup"><span data-stu-id="da0d6-174">Command Type TableDirect</span></span>
 <span data-ttu-id="da0d6-175">选择“Command typeTableDirect”时，基于文本的查询设计器将显示两个窗格：“查询”窗格和“结果”窗格。</span><span class="sxs-lookup"><span data-stu-id="da0d6-175">When you select **Command typeTableDirect**, the text-based query designer presents two panes: the Query pane and the Result pane.</span></span> <span data-ttu-id="da0d6-176">如果输入一个表并单击 **“运行”** 按钮，则将返回该表的所有列。</span><span class="sxs-lookup"><span data-stu-id="da0d6-176">When you enter a table and click the **Run** button, all the columns for that table are returned.</span></span>

#### <a name="example"></a><span data-ttu-id="da0d6-177">示例</span><span class="sxs-lookup"><span data-stu-id="da0d6-177">Example</span></span>
 <span data-ttu-id="da0d6-178">对于数据源类型 OLE DB，以下数据集查询将为2008数据库中的所有联系人类型返回结果集 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] **2008** 。</span><span class="sxs-lookup"><span data-stu-id="da0d6-178">For a data source type OLE DB, the following dataset query returns a result set for all contact types in the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)]**2008** database.</span></span>

 `Person.ContactType`

 <span data-ttu-id="da0d6-179">如果输入表名 Person.ContactType，则等同于创建 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句 `SELECT * FROM Person.ContactType`。</span><span class="sxs-lookup"><span data-stu-id="da0d6-179">When you enter the table name Person.ContactType, it is the equivalent of creating the [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement `SELECT * FROM Person.ContactType`.</span></span>

## <a name="see-also"></a><span data-ttu-id="da0d6-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="da0d6-180">See Also</span></span>
 <span data-ttu-id="da0d6-181">[关系查询设计器用户界面 &#40;报表生成器&#41;](relational-query-designer-user-interface-report-builder.md) [查询设计器 &#40;报表生成器](../query-designers-report-builder.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="da0d6-181">[Relational Query Designer User Interface &#40;Report Builder&#41;](relational-query-designer-user-interface-report-builder.md) [Query Designers &#40;Report Builder&#41;](../query-designers-report-builder.md)</span></span>


