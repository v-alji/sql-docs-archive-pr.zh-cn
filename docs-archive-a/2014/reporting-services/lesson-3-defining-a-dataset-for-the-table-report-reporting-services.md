---
title: 第 3 课：为表报表定义数据集 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ee93dfcb-8f52-4d63-b4f6-0d38e00fd350
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 33fe48a60db2e7d15d205a4bff6205347f95c61c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580050"
---
# <a name="lesson-3-defining-a-dataset-for-the-table-report-reporting-services"></a><span data-ttu-id="69482-102">第 3 课：为表报表定义数据集 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="69482-102">Lesson 3: Defining a Dataset for the Table Report (Reporting Services)</span></span>
  <span data-ttu-id="69482-103">定义数据源后，您需要定义数据集。</span><span class="sxs-lookup"><span data-stu-id="69482-103">After you define the data source, you need to define a dataset.</span></span> <span data-ttu-id="69482-104">在 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 中，在报表中使用的数据包含在“数据集”中\*\*。</span><span class="sxs-lookup"><span data-stu-id="69482-104">In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], data that you use in reports is contained in a *dataset*.</span></span> <span data-ttu-id="69482-105">数据集包括一个指向数据源的指针、将由报表使用的查询以及计算字段和变量。</span><span class="sxs-lookup"><span data-stu-id="69482-105">A dataset includes a pointer to a data source and a query to be used by the report, as well as calculated fields and variables.</span></span>  
  
 <span data-ttu-id="69482-106">可以在报表设计器中使用查询设计器来设计查询。</span><span class="sxs-lookup"><span data-stu-id="69482-106">You can use the query designer in Report Designer to design the query.</span></span> <span data-ttu-id="69482-107">在本教程中，您将创建一个查询，用于从2008数据库检索销售订单信息 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] **2008** 。</span><span class="sxs-lookup"><span data-stu-id="69482-107">For this tutorial, you will create a query that retrieves sales order information from the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]**2008** database.</span></span>  
  
### <a name="to-define-a-transact-sql-query-for-report-data"></a><span data-ttu-id="69482-108">为报表数据定义 Transact-SQL 查询</span><span class="sxs-lookup"><span data-stu-id="69482-108">To define a Transact-SQL query for report data</span></span>  
  
1.  <span data-ttu-id="69482-109">在 "**报表数据**" 窗格中，单击 "**新建**"，然后单击 "**数据集 ...**"。"**数据集属性**" 对话框将打开。</span><span class="sxs-lookup"><span data-stu-id="69482-109">In the **Report Data** pane, click **New**, and then click **Dataset...**. The **Dataset Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="69482-110">在“名称”框中，键入 AdventureWorksDataset\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="69482-110">In the **Name** box, type **AdventureWorksDataset**.</span></span>  
  
3.  <span data-ttu-id="69482-111">单击 **“使用在我的报表中嵌入的数据集”**。</span><span class="sxs-lookup"><span data-stu-id="69482-111">Click **Use a dataset embedded in my report**.</span></span>  
  
4.  <span data-ttu-id="69482-112">请确保数据源的名称 AdventureWorks2012 在 "**数据源**" 文本框中，并确保 "**查询类型**" 为 "**文本**"。</span><span class="sxs-lookup"><span data-stu-id="69482-112">Make sure the name of your data source, AdventureWorks2012, is in the **Data source** text box, and that the **Query type** is **Text**.</span></span>  
  
5.  <span data-ttu-id="69482-113">将以下 Transact-SQL 查询键入（或复制并粘贴）到“查询”框中\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="69482-113">Type, or copy and paste, the following Transact-SQL query into the **Query** box.</span></span>  
  
    ```  
    SELECT   
       soh.OrderDate AS [Date],   
       soh.SalesOrderNumber AS [Order],   
       pps.Name AS Subcat, pp.Name as Product,    
       SUM(sd.OrderQty) AS Qty,  
       SUM(sd.LineTotal) AS LineTotal  
    FROM Sales.SalesPerson sp   
       INNER JOIN Sales.SalesOrderHeader AS soh   
          ON sp.BusinessEntityID = soh.SalesPersonID  
       INNER JOIN Sales.SalesOrderDetail AS sd   
          ON sd.SalesOrderID = soh.SalesOrderID  
       INNER JOIN Production.Product AS pp   
          ON sd.ProductID = pp.ProductID  
       INNER JOIN Production.ProductSubcategory AS pps   
          ON pp.ProductSubcategoryID = pps.ProductSubcategoryID  
       INNER JOIN Production.ProductCategory AS ppc   
          ON ppc.ProductCategoryID = pps.ProductCategoryID  
    GROUP BY ppc.Name, soh.OrderDate, soh.SalesOrderNumber, pps.Name, pp.Name,   
       soh.SalesPersonID  
    HAVING ppc.Name = 'Clothing'  
    ```  
  
6.  <span data-ttu-id="69482-114">（可选）单击“查询设计器”按钮\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="69482-114">(Optional) Click the **Query Designer** button.</span></span> <span data-ttu-id="69482-115">查询将在基于文本的查询设计器中显示。</span><span class="sxs-lookup"><span data-stu-id="69482-115">The query is displayed in the text-based query designer.</span></span> <span data-ttu-id="69482-116">通过单击“编辑为文本”，可以切换到图形查询设计器\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="69482-116">You can toggle to the graphical query designer by clicking **Edit As Text**.</span></span> <span data-ttu-id="69482-117">通过单击查询设计器工具栏上的 "运行\*\* (！ ) \*\* " 按钮，查看查询的结果。</span><span class="sxs-lookup"><span data-stu-id="69482-117">View the results of the query by clicking the run **(!)** button on the query designer toolbar.</span></span>  
  
     <span data-ttu-id="69482-118">将看到来自 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 数据库中四个不同表的六个字段的数据。</span><span class="sxs-lookup"><span data-stu-id="69482-118">You see the data from six fields from four different tables in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="69482-119">查询利用别名等 Transact-SQL 功能。</span><span class="sxs-lookup"><span data-stu-id="69482-119">The query makes use of Transact-SQL functionality such as aliases.</span></span> <span data-ttu-id="69482-120">例如，SalesOrderHeader 表称为 soh。</span><span class="sxs-lookup"><span data-stu-id="69482-120">For example, the SalesOrderHeader table is called soh.</span></span>  
  
     <span data-ttu-id="69482-121">单击“确定”退出查询设计器\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="69482-121">Click **OK** to exit the query designer.</span></span>  
  
7.  <span data-ttu-id="69482-122">单击“确定”退出“数据集属性”对话框\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="69482-122">Click **OK** to exit the **Dataset Properties** dialog box.</span></span>  
  
     <span data-ttu-id="69482-123">此时将在“报表数据”窗格中显示 **AdventureWorksDataset** 数据集和字段。</span><span class="sxs-lookup"><span data-stu-id="69482-123">Your **AdventureWorksDataset** dataset and fields appear in the Report Data pane.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="69482-124">下一个任务</span><span class="sxs-lookup"><span data-stu-id="69482-124">Next Task</span></span>  
 <span data-ttu-id="69482-125">您已成功指定了一个用于检索报表数据的查询。</span><span class="sxs-lookup"><span data-stu-id="69482-125">You have successfully specified a query that retrieves data for your report.</span></span> <span data-ttu-id="69482-126">接下来将创建报表布局。</span><span class="sxs-lookup"><span data-stu-id="69482-126">Next, you will create the report layout.</span></span> <span data-ttu-id="69482-127">请参阅[第 4 课：向报表添加表 (Reporting Services)](lesson-4-adding-a-table-to-the-report-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="69482-127">See [Lesson 4: Adding a Table to the Report &#40;Reporting Services&#41;](lesson-4-adding-a-table-to-the-report-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69482-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="69482-128">See Also</span></span>  
 <span data-ttu-id="69482-129">[查询设计工具报表设计器 SQL Server Data Tools &#40;SSRS&#41;](report-data/query-design-tools-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="69482-129">[Query Design Tools in Report Designer SQL Server Data Tools &#40;SSRS&#41;](report-data/query-design-tools-ssrs.md) </span></span>  
 <span data-ttu-id="69482-130">[&#40;SSRS&#41;SQL Server 连接类型](report-data/sql-server-connection-type-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="69482-130">[SQL Server Connection Type &#40;SSRS&#41;](report-data/sql-server-connection-type-ssrs.md) </span></span>  
 [<span data-ttu-id="69482-131">教程：编写 Transact-SQL 语句</span><span class="sxs-lookup"><span data-stu-id="69482-131">Tutorial: Writing Transact-SQL Statements</span></span>](../t-sql/tutorial-writing-transact-sql-statements.md)  
  
  
