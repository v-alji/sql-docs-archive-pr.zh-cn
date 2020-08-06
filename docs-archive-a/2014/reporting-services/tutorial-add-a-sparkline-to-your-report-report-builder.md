---
title: 教程：向报表添加迷你图（报表生成器）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 18c90a36-48bf-4805-a960-2d1e8f00c2dc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fb1bf83810b6c743b977e399864ce2edd514f572
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691547"
---
# <a name="tutorial-add-a-sparkline-to-your-report-report-builder"></a><span data-ttu-id="35066-102">教程：向报表添加迷你图（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="35066-102">Tutorial: Add a Sparkline to Your Report (Report Builder)</span></span>
  <span data-ttu-id="35066-103">在本教程中，您将基于示例销售数据创建一个基本的表报表，然后向该表的单元中添加迷你图。</span><span class="sxs-lookup"><span data-stu-id="35066-103">In this tutorial, you create a basic table report based on sample sales data, and then add a sparkline chart to a cell in the table.</span></span>  
  
 <span data-ttu-id="35066-104">您在本教程中创建的报表的增强版本可用作示例 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 报表生成器报表。</span><span class="sxs-lookup"><span data-stu-id="35066-104">An enhanced version of the report you create in this tutorial is available as a sample [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Report Builder report.</span></span> <span data-ttu-id="35066-105">有关下载此示例报表和其他内容的详细信息，请参阅[报表生成器示例报表](https://go.microsoft.com/fwlink/?LinkId=184851)。</span><span class="sxs-lookup"><span data-stu-id="35066-105">For more information about downloading this sample report and others, see [Report Builder sample reports](https://go.microsoft.com/fwlink/?LinkId=184851).</span></span> <span data-ttu-id="35066-106">下图显示与您将创建的报表类似的示例报表。</span><span class="sxs-lookup"><span data-stu-id="35066-106">The following illustration shows the sample report similar to the one that you will create.</span></span>  
  
 <span data-ttu-id="35066-107">![rs_SparklineMatrixTutorial](../../2014/tutorials/media/rs-sparklinematrixtutorial.gif "rs_SparklineMatrixTutorial")</span><span class="sxs-lookup"><span data-stu-id="35066-107">![rs_SparklineMatrixTutorial](../../2014/tutorials/media/rs-sparklinematrixtutorial.gif "rs_SparklineMatrixTutorial")</span></span>  
  
 <span data-ttu-id="35066-108">视频[如何：在表中创建迷你图 (报表生成器视频) ](https://technet.microsoft.com/bi/ff871942.aspx)演示如何使用迷你图创建相似的报表。</span><span class="sxs-lookup"><span data-stu-id="35066-108">The video [How to: Create a Sparkline in a Table (Report Builder Video)](https://technet.microsoft.com/bi/ff871942.aspx) illustrates how to create a similar report with sparklines.</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="35066-109">你将学习的内容</span><span class="sxs-lookup"><span data-stu-id="35066-109">What You Will Learn</span></span>  
 <span data-ttu-id="35066-110">在本教程中，您将了解如何执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="35066-110">In this tutorial, you will learn how to do the following:</span></span>  
  
 1. [<span data-ttu-id="35066-111">创建含有表的报表</span><span class="sxs-lookup"><span data-stu-id="35066-111">Create a Report with a Table</span></span>](#CreateTable)  
  
 2. [<span data-ttu-id="35066-112">在表或矩阵向导中创建查询</span><span class="sxs-lookup"><span data-stu-id="35066-112">Create a Query in the Table or Matrix Wizard</span></span>](#Query)  
  
 3. [<span data-ttu-id="35066-113">向表中添加迷你图</span><span class="sxs-lookup"><span data-stu-id="35066-113">Add a Sparkline to the Table</span></span>](#Sparkline)  
  
 4. [<span data-ttu-id="35066-114">沿水平方向和垂直方向对齐迷你图</span><span class="sxs-lookup"><span data-stu-id="35066-114">Align the Sparklines Vertically and Horizontally</span></span>](#AlignSparklines)  
  
### <a name="other-optional-steps"></a><span data-ttu-id="35066-115">其他可选步骤</span><span class="sxs-lookup"><span data-stu-id="35066-115">Other Optional Steps</span></span>  
 5. [<span data-ttu-id="35066-116">将数据格式设置为货币</span><span class="sxs-lookup"><span data-stu-id="35066-116">Format Data as Currency</span></span>](#FormatCurrency)  
  
 6. [<span data-ttu-id="35066-117">将数据格式设置为日期格式</span><span class="sxs-lookup"><span data-stu-id="35066-117">Format Data as Dates</span></span>](#FormatDates)  
  
 7. [<span data-ttu-id="35066-118">更改列宽</span><span class="sxs-lookup"><span data-stu-id="35066-118">Change Column Widths</span></span>](#Width)  
  
 8. [<span data-ttu-id="35066-119">添加报表标题</span><span class="sxs-lookup"><span data-stu-id="35066-119">Add a Report Title</span></span>](#Title)  
  
 9. [<span data-ttu-id="35066-120">保存报表</span><span class="sxs-lookup"><span data-stu-id="35066-120">Save the Report</span></span>](#Save)  
  
 <span data-ttu-id="35066-121">本教程的预计学时：30 分钟。</span><span class="sxs-lookup"><span data-stu-id="35066-121">Estimated time to complete this tutorial: 30 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35066-122">要求</span><span class="sxs-lookup"><span data-stu-id="35066-122">Requirements</span></span>  
 <span data-ttu-id="35066-123">有关要求的详细信息，请参阅[教程先决条件（报表生成器）](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="35066-123">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-report-with-a-table"></a><a name="CreateTable"></a><span data-ttu-id="35066-124">1. 创建含有表的报表</span><span class="sxs-lookup"><span data-stu-id="35066-124">1. Create a Report with a Table</span></span>  
  
#### <a name="to-create-a-report"></a><span data-ttu-id="35066-125">创建报表</span><span class="sxs-lookup"><span data-stu-id="35066-125">To create a report</span></span>  
  
1.  <span data-ttu-id="35066-126">单击 **“开始”**，依次指向 **“程序”**、 **Microsoft SQL Server 2012 Report Builder**，再单击 **“报表生成器”**。</span><span class="sxs-lookup"><span data-stu-id="35066-126">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="35066-127">随即将打开“入门”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="35066-127">The **Getting Started** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="35066-128">如果未显示 "**入门**" 对话框，请在 "**报表生成器**" 按钮中单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="35066-128">If the **Getting Started** dialog box does not appear, from the **Report Builder** button, click **New**.</span></span>  
  
2.  <span data-ttu-id="35066-129">在左窗格中，确认已选中 **“新建报表”** 。</span><span class="sxs-lookup"><span data-stu-id="35066-129">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="35066-130">在右窗格中，单击“表或矩阵向导”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-130">In the right pane, click **Table or Matrix Wizard**.</span></span>  
  
4.  <span data-ttu-id="35066-131">在“选择数据集”页上，选择“创建数据集”，然后单击“下一步”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-131">On the **Choose a dataset** page, select **Create a dataset**, and then click **Next**.</span></span> <span data-ttu-id="35066-132">将打开“选择数据源的连接”\*\*\*\* 页面。</span><span class="sxs-lookup"><span data-stu-id="35066-132">The **Choose a connection to a data source** page opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="35066-133">本教程不需要具体数据；只需要与 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="35066-133">This tutorial does not need specific data; it just needs a connection to a [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] database.</span></span> <span data-ttu-id="35066-134">如果已经具有在“数据源连接”下列出的某一数据源连接，则可以选择该连接并且转到步骤 10。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="35066-134">If you already have a data source connection listed under **Data Source Connections**, you can select it and go to step 10.</span></span> <span data-ttu-id="35066-135">有关详细信息，请参阅[获取数据连接的备选方式（报表生成器）](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="35066-135">For more information, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
5.  <span data-ttu-id="35066-136">单击 **“新建”** 。</span><span class="sxs-lookup"><span data-stu-id="35066-136">Click **New**.</span></span> <span data-ttu-id="35066-137">此时将打开 **“数据源属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="35066-137">The **Data Source Properties** dialog box opens.</span></span>  
  
6.  <span data-ttu-id="35066-138">在“名称”中，键入数据源的名称“Product Sales”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-138">In **Name**, type **Product Sales**, a name for the data source.</span></span>  
  
7.  <span data-ttu-id="35066-139">在“选择连接类型”中，确认已选择“Microsoft SQL Server”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-139">In **Select a connection type**, verify that **Microsoft SQL Server** is selected.</span></span>  
  
8.  <span data-ttu-id="35066-140">在“连接字符串”中，键入以下文本\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="35066-140">In **Connection string**, type the following text:</span></span>  
  
     <span data-ttu-id="35066-141">**数据源 =\<servername>**</span><span class="sxs-lookup"><span data-stu-id="35066-141">**Data Source=\<servername>**</span></span>  
  
     <span data-ttu-id="35066-142">表达式 \<servername>（例如 Report001）指定安装了 SQL Server 数据库引擎实例的计算机。</span><span class="sxs-lookup"><span data-stu-id="35066-142">The expression \<servername>, for example Report001, specifies a computer on which an instance of the SQL Server Database Engine is installed.</span></span> <span data-ttu-id="35066-143">因为报表数据不是从 SQL Server 数据库提取的，所以不需要包括数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="35066-143">Because the report data is not extracted from a SQL Server database, you need not include the name of a database.</span></span> <span data-ttu-id="35066-144">指定服务器上的默认数据库用于对查询进行分析。</span><span class="sxs-lookup"><span data-stu-id="35066-144">The default database on the specified server is used to parse the query.</span></span>  
  
9. <span data-ttu-id="35066-145">单击 **“凭据”**。</span><span class="sxs-lookup"><span data-stu-id="35066-145">Click **Credentials**.</span></span> <span data-ttu-id="35066-146">输入访问外部数据源所需的凭据。</span><span class="sxs-lookup"><span data-stu-id="35066-146">Enter the credentials that you need to access the external data source.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="35066-147">返回至“选择数据源的连接”页\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-147">You are back on the **Choose a connection to a data source** page.</span></span>  
  
11. <span data-ttu-id="35066-148">若要验证是否能连接到数据源，请单击“测试连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-148">To verify that you can connect to the data source, click **Test Connection**.</span></span>  
  
     <span data-ttu-id="35066-149">将显示消息“已成功地创建连接”。</span><span class="sxs-lookup"><span data-stu-id="35066-149">The message "Connection created successfully" appears.</span></span>  
  
12. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
13. <span data-ttu-id="35066-150">单击“下一步”。 </span><span class="sxs-lookup"><span data-stu-id="35066-150">Click **Next**.</span></span>  
  
##  <a name="2-create-a-query-in-the-table-wizard"></a><a name="Query"></a><span data-ttu-id="35066-151">2. 在表向导中创建查询</span><span class="sxs-lookup"><span data-stu-id="35066-151">2. Create a Query in the Table Wizard</span></span>  
 <span data-ttu-id="35066-152">在报表中，可以使用具有预定义查询的共享数据集，也可以创建仅在报表中使用的嵌入数据集。</span><span class="sxs-lookup"><span data-stu-id="35066-152">In a report, you can use a shared dataset that has a predefined query, or you can create an embedded dataset for use only in your report.</span></span> <span data-ttu-id="35066-153">在本教程中，将创建一个嵌入数据集。</span><span class="sxs-lookup"><span data-stu-id="35066-153">In this tutorial, you will create an embedded dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="35066-154">在本教程中，由于查询包含了数据值，因此它不需要外部数据源。</span><span class="sxs-lookup"><span data-stu-id="35066-154">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="35066-155">这样，查询就会非常长。</span><span class="sxs-lookup"><span data-stu-id="35066-155">This makes the query quite long.</span></span> <span data-ttu-id="35066-156">在业务环境中，查询不会包含数据。</span><span class="sxs-lookup"><span data-stu-id="35066-156">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="35066-157">本教程中的查询仅供学习使用。</span><span class="sxs-lookup"><span data-stu-id="35066-157">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-query"></a><span data-ttu-id="35066-158">创建查询</span><span class="sxs-lookup"><span data-stu-id="35066-158">To create a query</span></span>  
  
1.  <span data-ttu-id="35066-159">在“设计查询”页中，关系查询设计器处于打开状态\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-159">On the **Design a query** page, the relational query designer is open.</span></span> <span data-ttu-id="35066-160">在本教程中，您将使用基于文本的查询设计器。</span><span class="sxs-lookup"><span data-stu-id="35066-160">For this tutorial, you will use the text-based query designer.</span></span>  
  
2.  <span data-ttu-id="35066-161">单击 "**编辑为文本**"。</span><span class="sxs-lookup"><span data-stu-id="35066-161">Click **Edit As Text**.</span></span> <span data-ttu-id="35066-162">基于文本的查询设计器将显示查询窗格和结果窗格。</span><span class="sxs-lookup"><span data-stu-id="35066-162">The text-based query designer displays a query pane and a results pane.</span></span>  
  
3.  <span data-ttu-id="35066-163">将以下 [!INCLUDE[tsql](../includes/tsql-md.md)] 查询粘贴到“查询”框中\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-163">Paste the following [!INCLUDE[tsql](../includes/tsql-md.md)] query into the **Query** box.</span></span>  
  
    ```  
    SELECT CAST('2010-01-04' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2010-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Carrying Case' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2010-01-10' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Carrying Case' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2010-01-04' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Budget Movie-Maker' as Product, CAST(1056.00 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2010-01-05' AS date) as SalesDate,  'Accessories' as Subcategory,  
       'Slim Digital' as Product, CAST(1380.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2010-01-05' AS date) as SalesDate,'Accessories' as Subcategory,    
       'Budget Movie-Maker' as Product, CAST(780.00 AS money) AS Sales, 26 as Quantity  
    UNION SELECT CAST('2010-01-07' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(3798.00 AS money) AS Sales, 9 as Quantity  
    UNION SELECT CAST('2010-01-08' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(10400.00 AS money) AS Sales, 13 as Quantity  
    UNION SELECT CAST('2010-01-09' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(3000.00 AS money) AS Sales, 60 as Quantity  
    UNION SELECT CAST('2010-01-10' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(7234.50 AS money) AS Sales, 39 as Quantity  
    UNION SELECT CAST('2010-01-06' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Carrying Case' as Product, CAST(10836.00 AS money) AS Sales, 84 as Quantity  
    UNION SELECT CAST('2010-01-07' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Slim Digital' as Product, CAST(2550.00 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2010-01-04' AS date) as SalesDate, 'Digital' as Subcategory,   
       'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2010-01-08' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'Slim Digital' as Product, CAST(18530.00 AS money) AS Sales, 34 as Quantity  
    UNION SELECT CAST('2010-01-06' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'Slim Digital' as Product, CAST(26576.00 AS money) AS Sales, 88 as Quantity  
    ```  
  
4.  <span data-ttu-id="35066-164">在查询设计器工具栏中，单击“运行”(**!**)。</span><span class="sxs-lookup"><span data-stu-id="35066-164">On the query designer toolbar, click Run  (**!**).</span></span>  
  
     <span data-ttu-id="35066-165">该查询运行并显示 **SalesDate**、 **Subcategory**、 **Product**、 **Sales**和 **Quantity**字段的结果集。</span><span class="sxs-lookup"><span data-stu-id="35066-165">The query runs and displays the result set for the fields **SalesDate**, **Subcategory**, **Product**, **Sales**, and **Quantity**.</span></span>  
  
5.  <span data-ttu-id="35066-166">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="35066-166">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="35066-167">在“排列字段”页上，将 Sales 拖到“值”中\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-167">On the **Arrange fields** page, drag **Sales** to **Values**.</span></span>  
  
     <span data-ttu-id="35066-168">**Sales** 由 Sum 函数聚合。</span><span class="sxs-lookup"><span data-stu-id="35066-168">**Sales** is aggregated by the Sum function.</span></span> <span data-ttu-id="35066-169">值为 [Sum(Sales)]。</span><span class="sxs-lookup"><span data-stu-id="35066-169">The value is [Sum(Sales)].</span></span>  
  
7.  <span data-ttu-id="35066-170">将 Product 拖到“行组”中\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-170">Drag **Product** to **Row groups**.</span></span>  
  
8.  <span data-ttu-id="35066-171">将 SalesDate 拖到“列组”中\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-171">Drag **SalesDate** to **Column groups**.</span></span>  
  
9. <span data-ttu-id="35066-172">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="35066-172">Click **Next**.</span></span>  
  
10. <span data-ttu-id="35066-173">在“选择布局”页的“选项”下，确认已选择“显示小计和总计”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-173">On the **Choose the layout** page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
     <span data-ttu-id="35066-174">向导的“预览”窗格将显示包含有三行的表。</span><span class="sxs-lookup"><span data-stu-id="35066-174">The wizard Preview pane displays a table with three rows.</span></span> <span data-ttu-id="35066-175">当您运行报表时，每行将按以下方式显示：</span><span class="sxs-lookup"><span data-stu-id="35066-175">When you run the report, each row will display in the following way:</span></span>  
  
    1.  <span data-ttu-id="35066-176">第一行将对表出现一次以显示列标题。</span><span class="sxs-lookup"><span data-stu-id="35066-176">The first row will appear once for the table to show column headings.</span></span>  
  
    2.  <span data-ttu-id="35066-177">第二行将对每个产品重复一次并显示产品名称、每日总计和行总计。</span><span class="sxs-lookup"><span data-stu-id="35066-177">The second row will repeat once for each product and display the product name, total per day, and line total.</span></span>  
  
    3.  <span data-ttu-id="35066-178">第三行将对表出现一次以显示总计。</span><span class="sxs-lookup"><span data-stu-id="35066-178">The third row will appear once for the table to display the grand totals.</span></span>  
  
11. <span data-ttu-id="35066-179">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="35066-179">Click **Next**.</span></span>  
  
12. <span data-ttu-id="35066-180">在 **“选择样式”** 页的 **“样式”** 窗格中，选择 **“石板”**。</span><span class="sxs-lookup"><span data-stu-id="35066-180">On the **Choose a Style** page, in the **Styles** pane, select **Slate**.</span></span>  
  
     <span data-ttu-id="35066-181">“预览”窗格将显示具有该样式的表的示例。</span><span class="sxs-lookup"><span data-stu-id="35066-181">The Preview pane displays a sample of the table with that style.</span></span>  
  
13. <span data-ttu-id="35066-182">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="35066-182">Click **Finish**.</span></span>  
  
14. <span data-ttu-id="35066-183">表将添加到设计图面中。</span><span class="sxs-lookup"><span data-stu-id="35066-183">The table is added to the design surface.</span></span> <span data-ttu-id="35066-184">此表有三列和三行。</span><span class="sxs-lookup"><span data-stu-id="35066-184">The table has three columns and three rows.</span></span>  
  
     <span data-ttu-id="35066-185">在“分组”窗格中查找。</span><span class="sxs-lookup"><span data-stu-id="35066-185">Look in the Grouping pane.</span></span> <span data-ttu-id="35066-186">如果未显示“分组”窗格，请在“视图”菜单上，单击“分组”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-186">If you can't see the Grouping pane, on the **View** menu, click **Grouping**.</span></span> <span data-ttu-id="35066-187">“行组”窗格显示一个行组： **Product**。</span><span class="sxs-lookup"><span data-stu-id="35066-187">The Row Groups pane shows one row group: **Product**.</span></span> <span data-ttu-id="35066-188">“列组”窗格显示一个列组： **SalesDate**。</span><span class="sxs-lookup"><span data-stu-id="35066-188">The Column Groups pane shows one column group: **SalesDate**.</span></span> <span data-ttu-id="35066-189">详细信息数据是由数据集查询检索的所有数据。</span><span class="sxs-lookup"><span data-stu-id="35066-189">Detail data is all the data that is retrieved by the dataset query.</span></span>  
  
15. <span data-ttu-id="35066-190">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="35066-190">Click **Run** to preview the report.</span></span>  
  
##  <a name="3-add-a-sparkline"></a><a name="Sparkline"></a><span data-ttu-id="35066-191">3. 添加迷你图</span><span class="sxs-lookup"><span data-stu-id="35066-191">3. Add a Sparkline</span></span>  
  
#### <a name="to-add-a-sparkline-chart-to-a-table"></a><span data-ttu-id="35066-192">向表中添加迷你图</span><span class="sxs-lookup"><span data-stu-id="35066-192">To add a sparkline chart to a table</span></span>  
  
1.  <span data-ttu-id="35066-193">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="35066-193">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="35066-194">选择表中的“Total”列。</span><span class="sxs-lookup"><span data-stu-id="35066-194">Select the Total column in your table.</span></span>  
  
3.  <span data-ttu-id="35066-195">右键单击，指向“插入列”，然后单击“左”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-195">Right-click, point to **Insert Column**, and then click **Left**.</span></span>  
  
4.  <span data-ttu-id="35066-196">在新列中，右键单击 [Product] 行，指向 "**插入**" 功能区选项卡，然后单击 "**迷你图**"。</span><span class="sxs-lookup"><span data-stu-id="35066-196">In the new column, right-click in the [Product] row, point to the **Insert** ribbon tab, and then click **Sparkline**.</span></span>  
  
5.  <span data-ttu-id="35066-197">请确保选择**列**行中的第一个迷你图，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="35066-197">Make sure the first sparkline in the **Column** row is selected and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="35066-198">单击要在“图表数据”窗格中显示的迷你图。</span><span class="sxs-lookup"><span data-stu-id="35066-198">Click the sparkline to show the Chart Data pane.</span></span>  
  
7.  <span data-ttu-id="35066-199">单击 "值" 框中的加号 ("+) "，然后单击 "**销售额**"。</span><span class="sxs-lookup"><span data-stu-id="35066-199">Click the plus (+) sign in the Values box, and then click **Sales**.</span></span>  
  
     <span data-ttu-id="35066-200">“Sales”字段中的值现在是迷你图的值\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-200">The values in the **Sales** field are now the values for the sparkline.</span></span>  
  
8.  <span data-ttu-id="35066-201">单击 "类别组" 框中的加号 ("+) "，然后单击 " **SalesDate**"。</span><span class="sxs-lookup"><span data-stu-id="35066-201">Click the plus (+) sign in the Category Groups box, and then click **SalesDate**.</span></span>  
  
9. <span data-ttu-id="35066-202">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="35066-202">Click **Run** to preview your report.</span></span>  
  
     <span data-ttu-id="35066-203">请注意，在表的每一行中都有迷你图，但这些迷你图不正确。</span><span class="sxs-lookup"><span data-stu-id="35066-203">Note that there are sparkline charts in each row of the table, but they're not correct.</span></span> <span data-ttu-id="35066-204">迷你图中的各条形不互连。</span><span class="sxs-lookup"><span data-stu-id="35066-204">The bars in the charts don't line up with each other.</span></span> <span data-ttu-id="35066-205">在第二行数据中只有四个条形，因此，这些条比第一行中的条宽，因为第一行中有六个条形。</span><span class="sxs-lookup"><span data-stu-id="35066-205">There are only four bars in the second row of data, so the bars are wider than the bars in the first row, which has six.</span></span> <span data-ttu-id="35066-206">您不能比较每天每个产品的值。</span><span class="sxs-lookup"><span data-stu-id="35066-206">You can't compare values for each product per day.</span></span> <span data-ttu-id="35066-207">它们之间需要相互对齐。</span><span class="sxs-lookup"><span data-stu-id="35066-207">They need to line up with each other.</span></span>  
  
     <span data-ttu-id="35066-208">还要注意的是，对于每一行，该行的最高的条形是行高。</span><span class="sxs-lookup"><span data-stu-id="35066-208">Also note that for each row, the tallest bar for that row is the height of the row.</span></span> <span data-ttu-id="35066-209">这也会产生误解，因为每行的最大值不相等：预算 Movie Maker 的最大值为 $10400，但超薄数字的最大值为 $26576-大于两倍。</span><span class="sxs-lookup"><span data-stu-id="35066-209">This is misleading, too, because the largest values for each row are not equal: the largest value for Budget Movie-Maker is $10,400, but the largest value for Slim Digital is $26,576-more than twice as large.</span></span> <span data-ttu-id="35066-210">并且，这两行的最大的条形大约为相同高度。</span><span class="sxs-lookup"><span data-stu-id="35066-210">And yet the largest bars in those two rows are about the same height.</span></span> <span data-ttu-id="35066-211">此外，它还需要与其他迷你图相一致。</span><span class="sxs-lookup"><span data-stu-id="35066-211">That also needs to be made to scale with the other sparklines.</span></span>  
  
     <span data-ttu-id="35066-212">![rs_SprklineMtrxUnaligndBars](../../2014/tutorials/media/rs-sprklinemtrxunaligndbars.gif "rs_SprklineMtrxUnaligndBars")</span><span class="sxs-lookup"><span data-stu-id="35066-212">![rs_SprklineMtrxUnaligndBars](../../2014/tutorials/media/rs-sprklinemtrxunaligndbars.gif "rs_SprklineMtrxUnaligndBars")</span></span>  
  
##  <a name="4-align-the-sparklines-vertically-and-horizontally"></a><a name="AlignSparklines"></a><span data-ttu-id="35066-213">4. 垂直和水平对齐迷你图</span><span class="sxs-lookup"><span data-stu-id="35066-213">4. Align the Sparklines Vertically and Horizontally</span></span>  
 <span data-ttu-id="35066-214">如果不使用相同的度量，则很难读取迷你图。</span><span class="sxs-lookup"><span data-stu-id="35066-214">The sparklines are hard to read when they don't all use the same measurements.</span></span> <span data-ttu-id="35066-215">每个迷你图的水平轴和垂直轴都需要与其他部分匹配。</span><span class="sxs-lookup"><span data-stu-id="35066-215">Both the horizontal and vertical axes for each need to match the rest.</span></span>  
  
#### <a name="to-set-alignment-for-the-sparklines-in-the-table"></a><span data-ttu-id="35066-216">设置表中迷你图的对齐方式</span><span class="sxs-lookup"><span data-stu-id="35066-216">To set alignment for the sparklines in the table</span></span>  
  
1.  <span data-ttu-id="35066-217">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="35066-217">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="35066-218">右键单击迷你图，然后单击“垂直轴属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-218">Right-click the sparkline and click **Vertical Axis Properties**.</span></span>  
  
3.  <span data-ttu-id="35066-219">选中“对齐轴”复选框\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-219">Check the **Align axes in** check box.</span></span>  
  
     <span data-ttu-id="35066-220">Tablix1 显示在列表中。</span><span class="sxs-lookup"><span data-stu-id="35066-220">Tablix1 is showing in the list.</span></span> <span data-ttu-id="35066-221">这是唯一的选项。</span><span class="sxs-lookup"><span data-stu-id="35066-221">That is the only option.</span></span> <span data-ttu-id="35066-222">该选项设置在各迷你图中条形相对于其他条形的高度。</span><span class="sxs-lookup"><span data-stu-id="35066-222">This sets the height of the bars in each sparkline relative to the others.</span></span>  
  
4.  <span data-ttu-id="35066-223">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="35066-223">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="35066-224">右键单击迷你图，然后单击“水平轴属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-224">Right-click the sparkline and click **Horizontal Axis Properties**.</span></span>  
  
6.  <span data-ttu-id="35066-225">选中“对齐轴”复选框\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-225">Check the **Align axes in** check box.</span></span>  
  
     <span data-ttu-id="35066-226">Tablix1 显示在列表中。</span><span class="sxs-lookup"><span data-stu-id="35066-226">Tablix1 is showing in the list.</span></span> <span data-ttu-id="35066-227">这是唯一的选项。</span><span class="sxs-lookup"><span data-stu-id="35066-227">That is the only option.</span></span> <span data-ttu-id="35066-228">该选项设置在各迷你图中条形相对于其他条形的宽度。</span><span class="sxs-lookup"><span data-stu-id="35066-228">This sets the width of the bars in each sparkline relative to the others.</span></span> <span data-ttu-id="35066-229">如果某些迷你图中的条形比其他迷你图少，则这些迷你图将对于缺失的数据具有空白空间。</span><span class="sxs-lookup"><span data-stu-id="35066-229">If some sparklines have fewer bars than others, then those sparklines will have blank spaces for the missing data.</span></span>  
  
7.  <span data-ttu-id="35066-230">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="35066-230">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="35066-231">单击“运行”，再次预览报表\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-231">Click **Run** to preview your report again.</span></span>  
  
 <span data-ttu-id="35066-232">请注意，所有条形现在与其他行中的条形对齐。</span><span class="sxs-lookup"><span data-stu-id="35066-232">Note that all the bars are now aligned with the bars in the other rows.</span></span>  
  
##  <a name="5-optional-format-data-as-currency"></a><a name="FormatCurrency"></a><span data-ttu-id="35066-233">5. (可选) 将数据格式设置为货币</span><span class="sxs-lookup"><span data-stu-id="35066-233">5. (Optional) Format Data as Currency</span></span>  
 <span data-ttu-id="35066-234">默认情况下，“Sales”字段的汇总数据显示为常规数字\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-234">By default, the summary data for the **Sales** field displays a general number.</span></span> <span data-ttu-id="35066-235">请设置其格式，以使其显示货币形式的数字。</span><span class="sxs-lookup"><span data-stu-id="35066-235">Format it to display the number as currency.</span></span> <span data-ttu-id="35066-236">切换“占位符样式”，将格式化的文本框和占位符文本显示为示例值\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-236">Toggle **Placeholder Styles** to display formatted text boxes and placeholder text as sample values.</span></span>  
  
#### <a name="to-format-a-currency-field"></a><span data-ttu-id="35066-237">设置货币字段格式</span><span class="sxs-lookup"><span data-stu-id="35066-237">To format a currency field</span></span>  
  
1.  <span data-ttu-id="35066-238">单击 "**设计**" 切换到 "设计" 视图。</span><span class="sxs-lookup"><span data-stu-id="35066-238">Click **Design** to switch to design view.</span></span>  
  
2.  <span data-ttu-id="35066-239">单击第二行中的单元格 (**SalesDate**列中的列标题行) 下，并拖动以选择包含的所有单元格 `[Sum(Sales)]` 。</span><span class="sxs-lookup"><span data-stu-id="35066-239">Click the cell in the second row (under the column headings row) in the **SalesDate** column and drag to select all cells that contain `[Sum(Sales)]`.</span></span>  
  
3.  <span data-ttu-id="35066-240">在“开始”选项卡上的“数字”组中，单击“货币”按钮\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-240">On the **Home** tab, in the **Number** group, click the **Currency** button.</span></span> <span data-ttu-id="35066-241">单元会更改为显示已设置好格式的货币。</span><span class="sxs-lookup"><span data-stu-id="35066-241">The cells change to show the formatted currency.</span></span>  
  
     <span data-ttu-id="35066-242">如果区域设置为“英语(美国)”，则默认示例文本为 [**$12,345.00**]。</span><span class="sxs-lookup"><span data-stu-id="35066-242">If your regional setting is English (United States), the default sample text is [**$12,345.00**].</span></span> <span data-ttu-id="35066-243">如果看不到示例货币值，请在 "**数字**" 组中单击 "**占位符样式**"，然后单击 "**示例值**"。</span><span class="sxs-lookup"><span data-stu-id="35066-243">If you do not see an example currency value, click **Placeholder Styles** in the **Numbers** group, and then click **Sample Values**.</span></span>  
  
4.  <span data-ttu-id="35066-244">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="35066-244">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="35066-245">**Sales**的汇总值显示为货币。</span><span class="sxs-lookup"><span data-stu-id="35066-245">The summary values for **Sales** display as currency.</span></span>  
  
##  <a name="6-optional-format-data-as-dates"></a><a name="FormatDates"></a><span data-ttu-id="35066-246">6. (可选) 将数据设置为日期格式</span><span class="sxs-lookup"><span data-stu-id="35066-246">6. (Optional) Format Data as Dates</span></span>  
 <span data-ttu-id="35066-247">默认情况下， **SalesDate**字段会同时显示日期和时间信息。</span><span class="sxs-lookup"><span data-stu-id="35066-247">By default, the **SalesDate** field displays both date and time information.</span></span> <span data-ttu-id="35066-248">您可以设置其格式，使其只显示日期。</span><span class="sxs-lookup"><span data-stu-id="35066-248">You can format them to display only the date.</span></span>  
  
#### <a name="to-format-a-date-field-as-the-default-format"></a><span data-ttu-id="35066-249">将日期字段设置为默认格式</span><span class="sxs-lookup"><span data-stu-id="35066-249">To format a date field as the default format</span></span>  
  
1.  <span data-ttu-id="35066-250">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="35066-250">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="35066-251">单击包含 `[SalesDate]`的单元格。</span><span class="sxs-lookup"><span data-stu-id="35066-251">Click the cell that contains `[SalesDate]`.</span></span>  
  
3.  <span data-ttu-id="35066-252">在功能区上，在 "**主页**" 选项卡上的 "**数字**" 组中，从下拉列表中选择 "**日期**"。</span><span class="sxs-lookup"><span data-stu-id="35066-252">On the Ribbon, on the **Home** tab, in the **Number** group, from the drop-down list, select **Date**.</span></span>  
  
     <span data-ttu-id="35066-253">单元格将显示示例日期 **[1/31/2000]**。</span><span class="sxs-lookup"><span data-stu-id="35066-253">The cell displays the example date **[1/31/2000]**.</span></span> <span data-ttu-id="35066-254">如果看不到示例日期，请单击“数字”\*\*\*\* 组中的“占位符样式”\*\*\*\*，然后单击“示例值”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-254">If you do not see an example date, click **Placeholder Styles** in the **Numbers** group, and then click **Sample Values**.</span></span>  
  
4.  <span data-ttu-id="35066-255">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="35066-255">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="35066-256">**SalesDate**值以默认日期格式显示。</span><span class="sxs-lookup"><span data-stu-id="35066-256">The **SalesDate** values display in the default date format.</span></span>  
  
##  <a name="7-optional-change-column-widths"></a><a name="Width"></a><span data-ttu-id="35066-257">7. (可选) 更改列宽</span><span class="sxs-lookup"><span data-stu-id="35066-257">7. (Optional) Change Column Widths</span></span>  
 <span data-ttu-id="35066-258">默认情况下，表中的每个单元格都包含一个文本框。</span><span class="sxs-lookup"><span data-stu-id="35066-258">By default, each cell in a table contains a text box.</span></span> <span data-ttu-id="35066-259">在呈现页面时，文本框将垂直扩展以容纳文本。</span><span class="sxs-lookup"><span data-stu-id="35066-259">A text box expands vertically to accommodate text when the page is rendered.</span></span> <span data-ttu-id="35066-260">在呈现的报表中，每个行将扩展到行中呈现的最高文本框的高度。</span><span class="sxs-lookup"><span data-stu-id="35066-260">In the rendered report, each row expands to the height of the tallest rendered text box in the row.</span></span> <span data-ttu-id="35066-261">设计图面上的行的高度不会影响已呈现报表中的行的高度。</span><span class="sxs-lookup"><span data-stu-id="35066-261">The height of the row on the design surface has no affect on the height of the row in the rendered report.</span></span>  
  
 <span data-ttu-id="35066-262">若要减少每个行占用的垂直空间量，请扩展列宽以容纳单个行的列中的文本框的预计内容。</span><span class="sxs-lookup"><span data-stu-id="35066-262">To reduce the amount of vertical space each row takes, expand the column width to accommodate the expected contents of the text boxes in the column on one line.</span></span>  
  
#### <a name="to-change-the-width-of-columns"></a><span data-ttu-id="35066-263">更改列宽</span><span class="sxs-lookup"><span data-stu-id="35066-263">To change the width of columns</span></span>  
  
1.  <span data-ttu-id="35066-264">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="35066-264">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="35066-265">单击表，以便在此表的上方和旁边显示列控点和行控点。</span><span class="sxs-lookup"><span data-stu-id="35066-265">Click the table so that column and row handles appear above and next to the table.</span></span>  
  
     <span data-ttu-id="35066-266">沿此表的上方和一侧显示的灰色条状物就是列控点和行控点。</span><span class="sxs-lookup"><span data-stu-id="35066-266">The gray bars along the top and side of the table are the column and row handles.</span></span>  
  
3.  <span data-ttu-id="35066-267">指向列控点之间的行，使光标变为双箭头。</span><span class="sxs-lookup"><span data-stu-id="35066-267">Point to the line between column handles so that the cursor changes into a double arrow.</span></span> <span data-ttu-id="35066-268">拖动列，调整到所需大小。</span><span class="sxs-lookup"><span data-stu-id="35066-268">Drag the columns to the size you want.</span></span> <span data-ttu-id="35066-269">例如，展开**product**列，以便产品名称显示在一行上。</span><span class="sxs-lookup"><span data-stu-id="35066-269">For example, expand the column for **Product** so that the product name displays on one line.</span></span>  
  
4.  <span data-ttu-id="35066-270">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="35066-270">Click **Run** to preview your report.</span></span>  
  
##  <a name="8-optional-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="35066-271">8. (可选) 添加报表标题</span><span class="sxs-lookup"><span data-stu-id="35066-271">8. (Optional) Add a Report Title</span></span>  
 <span data-ttu-id="35066-272">报表标题将出现在报表的顶部。</span><span class="sxs-lookup"><span data-stu-id="35066-272">A report title appears at the top of the report.</span></span> <span data-ttu-id="35066-273">可以将报表标题置于报表表头中或置于表体顶部的文本框中（如果报表未使用表头）。</span><span class="sxs-lookup"><span data-stu-id="35066-273">You can place the report title in a report header or if the report does not use one, in a text box at the top of the report body.</span></span> <span data-ttu-id="35066-274">在本教程中，您将使用自动放置在表体顶部的文本框。</span><span class="sxs-lookup"><span data-stu-id="35066-274">In this tutorial, you will use the text box that is automatically placed at the top of the report body.</span></span>  
  
 <span data-ttu-id="35066-275">通过将不同的字体样式、大小和颜色应用于文本的短语和单个字符，可以进一步增强文本。</span><span class="sxs-lookup"><span data-stu-id="35066-275">The text can be further enhanced by applying different font styles, sizes, and colors to phrases and individual characters of the text.</span></span> <span data-ttu-id="35066-276">有关详细信息，请参阅[设置文本框中文本的格式（报表生成器和 SSRS）](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="35066-276">For more information, see [Format Text in a Text Box &#40;Report Builder and SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md).</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="35066-277">添加报表标题</span><span class="sxs-lookup"><span data-stu-id="35066-277">To add a report title</span></span>  
  
1.  <span data-ttu-id="35066-278">在设计图面上，单击“单击以添加标题”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-278">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="35066-279">键入 **Product Sales**，然后在文本框外部单击。</span><span class="sxs-lookup"><span data-stu-id="35066-279">Type **Product Sales**, and then click outside the text box.</span></span>  
  
3.  <span data-ttu-id="35066-280">右键单击包含 Product Sales 的文本框，然后单击“文本框属性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-280">Right-click the text box that contains **Product Sales** and click **Text Box Properties**.</span></span>  
  
4.  <span data-ttu-id="35066-281">在“文本框属性”\*\*\*\* 对话框中，单击“字体”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-281">In the **Text Box Properties** dialog box, click **Font**.</span></span>  
  
5.  <span data-ttu-id="35066-282">在“大小”\*\*\*\* 列表中，选择“18pt”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-282">In the **Size** list, select **18pt**.</span></span>  
  
6.  <span data-ttu-id="35066-283">在 "**颜色**" 列表中，选择 "**褐紫红色**"。</span><span class="sxs-lookup"><span data-stu-id="35066-283">In the **Color** list, select **Maroon**.</span></span>  
  
7.  <span data-ttu-id="35066-284">选择“粗体”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-284">Select **Bold**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="9-save-the-report"></a><a name="Save"></a><span data-ttu-id="35066-285">9. 保存报表</span><span class="sxs-lookup"><span data-stu-id="35066-285">9. Save the Report</span></span>  
 <span data-ttu-id="35066-286">将报表保存到报表服务器或计算机上。</span><span class="sxs-lookup"><span data-stu-id="35066-286">Save the report to a report server or your computer.</span></span> <span data-ttu-id="35066-287">如果不将报表保存到报表服务器上，则许多 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 功能（如报表部件和子报表）将不可用。</span><span class="sxs-lookup"><span data-stu-id="35066-287">If you do not save the report to the report server, a number of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features such as report parts and subreports are not available.</span></span>  
  
#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="35066-288">将报表保存到报表服务器</span><span class="sxs-lookup"><span data-stu-id="35066-288">To save the report on a report server</span></span>  
  
1.  <span data-ttu-id="35066-289">从 **“报表生成器”** 按钮，单击 **“另存为”**。</span><span class="sxs-lookup"><span data-stu-id="35066-289">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="35066-290">单击 **“最近使用的站点和服务器”**。</span><span class="sxs-lookup"><span data-stu-id="35066-290">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="35066-291">选择或键入您拥有保存报表权限的报表服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="35066-291">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="35066-292">此时将显示“正在连接到报表服务器”消息。</span><span class="sxs-lookup"><span data-stu-id="35066-292">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="35066-293">当连接完成时，您将看到报表服务器管理员指定为报表默认位置的报表文件夹的内容。</span><span class="sxs-lookup"><span data-stu-id="35066-293">When the connection is complete, you see the contents of the report folder that the report server administrator specified as the default location for reports.</span></span>  
  
4.  <span data-ttu-id="35066-294">在“名称”中，用“Product Sales”替换默认名称\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-294">In **Name**, replace the default name with **Product Sales**.</span></span>  
  
5.  <span data-ttu-id="35066-295">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="35066-295">Click **Save**.</span></span>  
  
 <span data-ttu-id="35066-296">报表即已保存至报表服务器。</span><span class="sxs-lookup"><span data-stu-id="35066-296">The report is saved to the report server.</span></span> <span data-ttu-id="35066-297">您连接的报表服务器的名称将显示在窗口底部的状态栏中。</span><span class="sxs-lookup"><span data-stu-id="35066-297">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
#### <a name="to-save-the-report-on-your-computer"></a><span data-ttu-id="35066-298">将报表保存到计算机上</span><span class="sxs-lookup"><span data-stu-id="35066-298">To save the report on your computer</span></span>  
  
1.  <span data-ttu-id="35066-299">从 **“报表生成器”** 按钮，单击 **“另存为”**。</span><span class="sxs-lookup"><span data-stu-id="35066-299">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="35066-300">依次单击“桌面”、“我的文档”或“我的电脑”，并浏览到要保存该报表的文件夹\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-300">Click **Desktop**, **My Documents**, or **My computer**, and browse to the folder where you want to save the report.</span></span>  
  
3.  <span data-ttu-id="35066-301">在“名称”中，用“Product Sales”替换默认名称\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35066-301">In **Name**, replace the default name with **Product Sales**.</span></span>  
  
4.  <span data-ttu-id="35066-302">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="35066-302">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="35066-303">后续步骤</span><span class="sxs-lookup"><span data-stu-id="35066-303">Next Steps</span></span>  
 <span data-ttu-id="35066-304">用于创建具有迷你图的表报表的教程到此结束。</span><span class="sxs-lookup"><span data-stu-id="35066-304">This concludes the tutorial for creating a table report with sparkline charts.</span></span> <span data-ttu-id="35066-305">有关迷你图的详细信息，请参阅[迷你图和数据条（报表生成器和 SSRS）](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="35066-305">For more information about sparklines, see [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35066-306">另请参阅</span><span class="sxs-lookup"><span data-stu-id="35066-306">See Also</span></span>  
 <span data-ttu-id="35066-307">[教程 &#40;报表生成器&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="35066-307">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="35066-308">SQL Server 2014 中的报表生成器</span><span class="sxs-lookup"><span data-stu-id="35066-308">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
