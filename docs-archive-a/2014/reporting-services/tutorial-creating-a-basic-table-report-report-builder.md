---
title: 教程：生成基本表报表（报表生成器）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d9e30521-f8ae-4c45-89c3-d40727f622f7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3587e2a53e2b09dd347a2733875eafd708b8a05a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579450"
---
# <a name="tutorial-creating-a-basic-table-report-report-builder"></a><span data-ttu-id="e6c06-102">教程：生成基本表报表（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="e6c06-102">Tutorial: Creating a Basic Table Report (Report Builder)</span></span>
  <span data-ttu-id="e6c06-103">本教程教您如何基于示例销售数据创建基本表格报表。</span><span class="sxs-lookup"><span data-stu-id="e6c06-103">This tutorial teaches you to create a basic table report based on sample sales data.</span></span> <span data-ttu-id="e6c06-104">下图显示了将创建的报表。</span><span class="sxs-lookup"><span data-stu-id="e6c06-104">The following illustration shows the report you will create.</span></span>  
  
 <span data-ttu-id="e6c06-105">![rs_CreateBasicReportTutorial](../../2014/tutorials/media/rs-createbasicreporttutorial.gif "rs_CreateBasicReportTutorial")</span><span class="sxs-lookup"><span data-stu-id="e6c06-105">![rs_CreateBasicReportTutorial](../../2014/tutorials/media/rs-createbasicreporttutorial.gif "rs_CreateBasicReportTutorial")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="e6c06-106">你将学习的内容</span><span class="sxs-lookup"><span data-stu-id="e6c06-106">What You Will Learn</span></span>  
 <span data-ttu-id="e6c06-107">在本教程中，您将了解如何执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="e6c06-107">In this tutorial, you will learn how to do the following:</span></span>  
  
1.  [<span data-ttu-id="e6c06-108">从“入门”创建新的报表</span><span class="sxs-lookup"><span data-stu-id="e6c06-108">Create a New Report from Getting Started</span></span>](#CreateTable)  
  
    1.  [<span data-ttu-id="e6c06-109">在表向导中指定数据连接</span><span class="sxs-lookup"><span data-stu-id="e6c06-109">Specify a Data Connection in the Table Wizard</span></span>](#DataConnection)  
  
    2.  [<span data-ttu-id="e6c06-110">在表向导中创建查询</span><span class="sxs-lookup"><span data-stu-id="e6c06-110">Create a Query in the Table Wizard</span></span>](#Query)  
  
    3.  [<span data-ttu-id="e6c06-111">在表向导中将数据组织到组中</span><span class="sxs-lookup"><span data-stu-id="e6c06-111">Organize Data into Groups in the Table Wizard</span></span>](#Groups)  
  
    4.  [<span data-ttu-id="e6c06-112">在表向导中添加小计行和合计行</span><span class="sxs-lookup"><span data-stu-id="e6c06-112">Add Subtotal and Total Rows in the Table Wizard</span></span>](#Subtotals)  
  
    5.  [<span data-ttu-id="e6c06-113">在表向导中选择样式</span><span class="sxs-lookup"><span data-stu-id="e6c06-113">Choose a Style in the Table Wizard</span></span>](#Style)  
  
2.  [<span data-ttu-id="e6c06-114">将数据格式设置为货币</span><span class="sxs-lookup"><span data-stu-id="e6c06-114">Format Data as Currency</span></span>](#FormatCurrency)  
  
3.  [<span data-ttu-id="e6c06-115">将数据格式设置为日期格式</span><span class="sxs-lookup"><span data-stu-id="e6c06-115">Format Data as Date</span></span>](#FormatDate)  
  
4.  [<span data-ttu-id="e6c06-116">更改列宽</span><span class="sxs-lookup"><span data-stu-id="e6c06-116">Change Column Widths</span></span>](#Width)  
  
5.  [<span data-ttu-id="e6c06-117">添加报表标题</span><span class="sxs-lookup"><span data-stu-id="e6c06-117">Add a Report Title</span></span>](#Title)  
  
6.  [<span data-ttu-id="e6c06-118">保存报表</span><span class="sxs-lookup"><span data-stu-id="e6c06-118">Save the Report</span></span>](#Save)  
  
7.  [<span data-ttu-id="e6c06-119">导出报表</span><span class="sxs-lookup"><span data-stu-id="e6c06-119">Export the Report</span></span>](#Export)  
  
 <span data-ttu-id="e6c06-120">完成本教程的预计学时：20 分钟。</span><span class="sxs-lookup"><span data-stu-id="e6c06-120">Estimated time to complete this tutorial: 20 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6c06-121">要求</span><span class="sxs-lookup"><span data-stu-id="e6c06-121">Requirements</span></span>  
 <span data-ttu-id="e6c06-122">有关要求的详细信息，请参阅[教程先决条件（报表生成器）](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="e6c06-122">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-new-report-from-getting-started"></a><a name="CreateTable"></a><span data-ttu-id="e6c06-123">1. 从入门创建新报表</span><span class="sxs-lookup"><span data-stu-id="e6c06-123">1. Create a New Report from Getting Started</span></span>  
 <span data-ttu-id="e6c06-124">从 "**入门**" 对话框创建表报表。</span><span class="sxs-lookup"><span data-stu-id="e6c06-124">Create a table report from the **Getting Started** dialog box.</span></span> <span data-ttu-id="e6c06-125">有两类模式：报表设计模式和共享数据集设计模式。</span><span class="sxs-lookup"><span data-stu-id="e6c06-125">There are two modes: report design and shared dataset design.</span></span> <span data-ttu-id="e6c06-126">在报表设计模式中，您可以在“报表数据”窗格中指定数据，在设计图面上指定报表布局。</span><span class="sxs-lookup"><span data-stu-id="e6c06-126">In report design mode, you specify data in the Report Data pane and the report layout on the design surface.</span></span> <span data-ttu-id="e6c06-127">在共享数据集设计模式中，可以创建与他人共享的数据集查询。</span><span class="sxs-lookup"><span data-stu-id="e6c06-127">In shared dataset design mode, you create dataset queries to share with others.</span></span> <span data-ttu-id="e6c06-128">在本教程中，您将使用报表设计模式。</span><span class="sxs-lookup"><span data-stu-id="e6c06-128">In this tutorial, you will be using report design mode.</span></span>  
  
#### <a name="to-create-a-new-report"></a><span data-ttu-id="e6c06-129">创建新的报表</span><span class="sxs-lookup"><span data-stu-id="e6c06-129">To create a new report</span></span>  
  
1.  <span data-ttu-id="e6c06-130">单击 **“开始”**，依次指向 **“程序”**、 **Microsoft SQL Server 2012 Report Builder**，再单击 **“报表生成器”**。</span><span class="sxs-lookup"><span data-stu-id="e6c06-130">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="e6c06-131">随即将打开“入门”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="e6c06-131">The **Getting Started** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e6c06-132">如果未显示 "**入门**" 对话框，请在 "**报表生成器**" 按钮中单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="e6c06-132">If the **Getting Started** dialog box does not appear, from the **Report Builder** button, click **New**.</span></span>  
  
2.  <span data-ttu-id="e6c06-133">在左窗格中，确认已选中 **“新建报表”** 。</span><span class="sxs-lookup"><span data-stu-id="e6c06-133">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="e6c06-134">在右窗格中，确认已选中“表或矩阵向导”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-134">In the right pane, verify that **Table or Matrix Wizard** is selected.</span></span>  
  
##  <a name="1a-specify-a-data-connection-in-the-table-wizard"></a><a name="DataConnection"></a><span data-ttu-id="e6c06-135">1a.</span><span class="sxs-lookup"><span data-stu-id="e6c06-135">1a.</span></span> <span data-ttu-id="e6c06-136">在表向导中指定数据连接</span><span class="sxs-lookup"><span data-stu-id="e6c06-136">Specify a Data Connection in the Table Wizard</span></span>  
 <span data-ttu-id="e6c06-137">数据连接包含要连接到外部数据源（如 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库）的信息。</span><span class="sxs-lookup"><span data-stu-id="e6c06-137">A data connection contains the information to connect to an external data source such as a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="e6c06-138">通常会从数据源所有者处获取连接信息以及要使用的凭据类型。</span><span class="sxs-lookup"><span data-stu-id="e6c06-138">Usually, you get the connection information and the type of credentials to use from the data source owner.</span></span> <span data-ttu-id="e6c06-139">若要指定数据连接，可以从报表服务器使用共享数据源或创建仅在此报表中使用的嵌入数据源。</span><span class="sxs-lookup"><span data-stu-id="e6c06-139">To specify a data connection, you can use a shared data source from the report server or create an embedded data source that is used only in this report.</span></span>  
  
 <span data-ttu-id="e6c06-140">在本教程中，您将使用嵌入数据源。</span><span class="sxs-lookup"><span data-stu-id="e6c06-140">In this tutorial, you will use an embedded data source.</span></span> <span data-ttu-id="e6c06-141">若要了解有关使用共享数据源的详细信息，请参阅[获取数据连接的备选方式（报表生成器）](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="e6c06-141">To learn more about using a shared data sources, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
#### <a name="to-create-an-embedded-data-source"></a><span data-ttu-id="e6c06-142">创建嵌入数据源</span><span class="sxs-lookup"><span data-stu-id="e6c06-142">To create an embedded data source</span></span>  
  
1.  <span data-ttu-id="e6c06-143">在“选择数据集”页上，选择“创建数据集”，然后单击“下一步”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-143">On the **Choose a dataset** page, select **Create a dataset**, and then click **Next**.</span></span> <span data-ttu-id="e6c06-144">将打开“选择数据源的连接”\*\*\*\* 页面。</span><span class="sxs-lookup"><span data-stu-id="e6c06-144">The **Choose a connection to a data source** page opens.</span></span>  
  
2.  <span data-ttu-id="e6c06-145">单击 **“新建”** 。</span><span class="sxs-lookup"><span data-stu-id="e6c06-145">Click **New**.</span></span> <span data-ttu-id="e6c06-146">此时将打开 **“数据源属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="e6c06-146">The **Data Source Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="e6c06-147">在 "**名称**" 中，键入数据源的 "**产品销售额**"。</span><span class="sxs-lookup"><span data-stu-id="e6c06-147">In **Name**, type **Product Sales** a name for the data source.</span></span>  
  
4.  <span data-ttu-id="e6c06-148">在“选择连接类型”中，确认已选择“Microsoft SQL Server”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-148">In **Select a connection type**, verify that **Microsoft SQL Server** is selected.</span></span>  
  
5.  <span data-ttu-id="e6c06-149">在 "**连接字符串**" 中，键入以下文本，其中 *\<servername>* 是实例的名称 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="e6c06-149">In **Connection string**, type the following text, where *\<servername>* is the name of an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
    ```  
    Data Source=<servername>  
    ```  
  
     <span data-ttu-id="e6c06-150">由于您将使用的查询会包含数据而不是从数据库检索数据，因此连接字符串不包含数据库名称。</span><span class="sxs-lookup"><span data-stu-id="e6c06-150">Because you will use a query that contains the data instead of retrieving the data from a database, the connection string does not include the database name.</span></span> <span data-ttu-id="e6c06-151">有关详细信息，请参阅[教程先决条件&#40;报表生成器&#41;](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="e6c06-151">For more information, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
6.  <span data-ttu-id="e6c06-152">单击 **“凭据”**。</span><span class="sxs-lookup"><span data-stu-id="e6c06-152">Click **Credentials**.</span></span> <span data-ttu-id="e6c06-153">输入访问外部数据源所需的凭据。</span><span class="sxs-lookup"><span data-stu-id="e6c06-153">Enter the credentials that you need to access the external data source.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="e6c06-154">返回至“选择数据源的连接”页\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-154">You are back on the **Choose a connection to a data source** page.</span></span>  
  
8.  <span data-ttu-id="e6c06-155">若要验证是否能连接到数据源，请单击“测试连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-155">To verify that you can connect to the data source, click **Test Connection**.</span></span>  
  
     <span data-ttu-id="e6c06-156">将显示消息“已成功地创建连接”。</span><span class="sxs-lookup"><span data-stu-id="e6c06-156">The message "Connection created successfully" appears.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. <span data-ttu-id="e6c06-157">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="e6c06-157">Click **Next**.</span></span>  
  
##  <a name="1b-create-a-query-in-the-table-wizard"></a><a name="Query"></a><span data-ttu-id="e6c06-158">1b.</span><span class="sxs-lookup"><span data-stu-id="e6c06-158">1b.</span></span> <span data-ttu-id="e6c06-159">在表向导中创建查询</span><span class="sxs-lookup"><span data-stu-id="e6c06-159">Create a Query in the Table Wizard</span></span>  
 <span data-ttu-id="e6c06-160">在报表中，可以使用具有预定义查询的共享数据集，也可以创建仅在报表中使用的嵌入数据集。</span><span class="sxs-lookup"><span data-stu-id="e6c06-160">In a report, you can use a shared dataset that has a predefined query, or you can create an embedded dataset for use only in your report.</span></span> <span data-ttu-id="e6c06-161">在本教程中，将创建一个嵌入数据集。</span><span class="sxs-lookup"><span data-stu-id="e6c06-161">In this tutorial, you will create an embedded dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e6c06-162">在本教程中，由于查询包含了数据值，因此它不需要外部数据源。</span><span class="sxs-lookup"><span data-stu-id="e6c06-162">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="e6c06-163">这样，查询就会非常长。</span><span class="sxs-lookup"><span data-stu-id="e6c06-163">This makes the query quite long.</span></span> <span data-ttu-id="e6c06-164">在业务环境中，查询不会包含数据。</span><span class="sxs-lookup"><span data-stu-id="e6c06-164">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="e6c06-165">本教程中的查询仅供学习使用。</span><span class="sxs-lookup"><span data-stu-id="e6c06-165">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-query"></a><span data-ttu-id="e6c06-166">创建查询</span><span class="sxs-lookup"><span data-stu-id="e6c06-166">To create a query</span></span>  
  
1.  <span data-ttu-id="e6c06-167">在“设计查询”页中，关系查询设计器处于打开状态\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-167">On the **Design a query** page, the relational query designer is open.</span></span> <span data-ttu-id="e6c06-168">在本教程中，您将使用基于文本的查询设计器。</span><span class="sxs-lookup"><span data-stu-id="e6c06-168">For this tutorial, you will use the text-based query designer.</span></span>  
  
     <span data-ttu-id="e6c06-169">单击 "**编辑为文本**"。</span><span class="sxs-lookup"><span data-stu-id="e6c06-169">Click **Edit As Text**.</span></span> <span data-ttu-id="e6c06-170">基于文本的查询设计器将显示查询窗格和结果窗格。</span><span class="sxs-lookup"><span data-stu-id="e6c06-170">The text-based query designer displays a query pane and a results pane.</span></span>  
  
2.  <span data-ttu-id="e6c06-171">将以下 [!INCLUDE[tsql](../includes/tsql-md.md)] 查询粘贴到“查询”框中\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-171">Paste the following [!INCLUDE[tsql](../includes/tsql-md.md)] query into the **Query** box.</span></span>  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Carrying Case' as Product, CAST(9924.60 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-11' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Mini Battery Charger' as Product, CAST(1056.00 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Accessories' as Subcategory,  
       'Telephoto Conversion Lens' as Product, CAST(1380.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,'Accessories' as Subcategory,    
       'USB Cable' as Product, CAST(780.00 AS money) AS Sales, 26 as Quantity  
    UNION SELECT CAST('2009-01-08' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(3798.00 AS money) AS Sales, 9 as Quantity  
    UNION SELECT CAST('2009-01-09' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Business Videographer' as Product, CAST(10400.00 AS money) AS Sales, 13 as Quantity  
    UNION SELECT CAST('2009-01-10' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Social Videographer' as Product, CAST(3000.00 AS money) AS Sales, 60 as Quantity  
    UNION SELECT CAST('2009-01-11' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Advanced Digital' as Product, CAST(7234.50 AS money) AS Sales, 39 as Quantity  
    UNION SELECT CAST('2009-01-07' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Compact Digital' as Product, CAST(10836.00 AS money) AS Sales, 84 as Quantity  
    UNION SELECT CAST('2009-01-08' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Consumer Digital' as Product, CAST(2550.00 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Digital' as Subcategory,   
       'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2009-01-09' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'SLR Camera 35mm' as Product, CAST(18530.00 AS money) AS Sales, 34 as Quantity  
    UNION SELECT CAST('2009-01-07' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'SLR Camera' as Product, CAST(26576.00 AS money) AS Sales, 88 as Quantity  
  
    ```  
  
3.  <span data-ttu-id="e6c06-172">在查询设计器工具栏上，单击 "**运行** (**！**) "。</span><span class="sxs-lookup"><span data-stu-id="e6c06-172">On the query designer toolbar, click **Run** (**!**).</span></span>  
  
     <span data-ttu-id="e6c06-173">该查询运行并显示 SalesDate、Subcategory、Product、Sales 和 Quantity 字段的结果集。</span><span class="sxs-lookup"><span data-stu-id="e6c06-173">The query runs and displays the result set for the fields SalesDate, Subcategory, Product, Sales, and Quantity.</span></span>  
  
     <span data-ttu-id="e6c06-174">在结果集中，列标题基于查询中的名称。</span><span class="sxs-lookup"><span data-stu-id="e6c06-174">In the result set, the column headings are based on the names in the query.</span></span> <span data-ttu-id="e6c06-175">在数据集中，列标题会成为字段名称并保存在报表中。</span><span class="sxs-lookup"><span data-stu-id="e6c06-175">In the dataset, the column headings become the field names, and are saved in the report.</span></span> <span data-ttu-id="e6c06-176">完成向导后，可以使用“报表数据”窗格查看数据集字段集合。</span><span class="sxs-lookup"><span data-stu-id="e6c06-176">After you complete the wizard, you can use the Report Data pane to view the collection of dataset fields.</span></span>  
  
4.  <span data-ttu-id="e6c06-177">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="e6c06-177">Click **Next**.</span></span>  
  
##  <a name="1c-organize-data-into-groups-in-the-table-wizard"></a><a name="Groups"></a><span data-ttu-id="e6c06-178">1c.</span><span class="sxs-lookup"><span data-stu-id="e6c06-178">1c.</span></span> <span data-ttu-id="e6c06-179">在表向导中将数据组织到组中</span><span class="sxs-lookup"><span data-stu-id="e6c06-179">Organize Data into Groups in the Table Wizard</span></span>  
 <span data-ttu-id="e6c06-180">在选择要进行分组的字段时，可以设计一个表格，其中的行和列显示了详细数据和聚合数据。</span><span class="sxs-lookup"><span data-stu-id="e6c06-180">When you select fields to group on, you design a table that has rows and columns that display detail data and aggregated data.</span></span>  
  
#### <a name="to-organize-data-into-groups"></a><span data-ttu-id="e6c06-181">将数据组织到组中</span><span class="sxs-lookup"><span data-stu-id="e6c06-181">To organize data into groups</span></span>  
  
1.  <span data-ttu-id="e6c06-182">在“排列字段”页上，将 Product 拖到“值”中\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-182">On the **Arrange fields** page, drag Product to **Values**.</span></span>  
  
2.  <span data-ttu-id="e6c06-183">将 Quantity 拖到“值”中并将其置于 Product 下方\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-183">Drag Quantity to **Values** and place below Product.</span></span>  
  
     <span data-ttu-id="e6c06-184">Quantity 由 Sum 函数（即数值字段的默认聚合函数）自动聚合。</span><span class="sxs-lookup"><span data-stu-id="e6c06-184">Quantity is automatically aggregated by the Sum function, the default aggregate for numeric fields.</span></span> <span data-ttu-id="e6c06-185">值为 [Sum(Quantity)]。</span><span class="sxs-lookup"><span data-stu-id="e6c06-185">The value is [Sum(Quantity)].</span></span>  
  
     <span data-ttu-id="e6c06-186">可以打开下拉列表以查看其他可用聚合函数。</span><span class="sxs-lookup"><span data-stu-id="e6c06-186">You can open the drop-down list to view the other aggregate functions available.</span></span> <span data-ttu-id="e6c06-187">不要更改聚合函数。</span><span class="sxs-lookup"><span data-stu-id="e6c06-187">Do not change the aggregate function.</span></span>  
  
3.  <span data-ttu-id="e6c06-188">将 Sales 拖到“值”中并将其置于 [Sum(Quantity)] 下方\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-188">Drag Sales to **Values** and place below [Sum(Quantity)].</span></span>  
  
     <span data-ttu-id="e6c06-189">Sales 由 Sum 函数聚合。</span><span class="sxs-lookup"><span data-stu-id="e6c06-189">Sales is aggregated by the Sum function.</span></span> <span data-ttu-id="e6c06-190">值为 [Sum(Sales)]。</span><span class="sxs-lookup"><span data-stu-id="e6c06-190">The value is [Sum(Sales)].</span></span>  
  
     <span data-ttu-id="e6c06-191">步骤 1、2 和 3 指定要在表中显示的数据。</span><span class="sxs-lookup"><span data-stu-id="e6c06-191">Steps 1, 2, and 3 specify the data to display in the table.</span></span>  
  
4.  <span data-ttu-id="e6c06-192">将 SalesDate 拖到“行组”\*\*\*\* 中。</span><span class="sxs-lookup"><span data-stu-id="e6c06-192">Drag SalesDate to **Row groups**.</span></span>  
  
5.  <span data-ttu-id="e6c06-193">将 Subcategory 拖到“行组”中并将其置于 SalesDate 下方\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-193">Drag Subcategory to **Row groups** and place below SalesDate.</span></span>  
  
     <span data-ttu-id="e6c06-194">步骤 4 和 5 首先按日期组织字段的值，然后按照该日期的产品子类别组织字段的值。</span><span class="sxs-lookup"><span data-stu-id="e6c06-194">Steps 4 and 5 organize the values for the fields first by date, and then by product subcategory for that date.</span></span>  
  
6.  <span data-ttu-id="e6c06-195">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="e6c06-195">Click **Next**.</span></span>  
  
##  <a name="1d-add-subtotal-and-total-rows-in-the-table-wizard"></a><a name="Subtotals"></a><span data-ttu-id="e6c06-196">1d.</span><span class="sxs-lookup"><span data-stu-id="e6c06-196">1d.</span></span> <span data-ttu-id="e6c06-197">在表向导中添加小计行和合计行</span><span class="sxs-lookup"><span data-stu-id="e6c06-197">Add Subtotal and Total Rows in the Table Wizard</span></span>  
 <span data-ttu-id="e6c06-198">创建组后，可以添加用于显示字段的聚合值的行并设置其格式。</span><span class="sxs-lookup"><span data-stu-id="e6c06-198">After you create groups, you can add and format rows on which to display aggregate values for the fields.</span></span> <span data-ttu-id="e6c06-199">可以选择是显示所有数据还是允许用户以交互方式展开和折叠已分组数据。</span><span class="sxs-lookup"><span data-stu-id="e6c06-199">You can choose whether to show all the data or to let a user expand and collapse grouped data interactively.</span></span>  
  
#### <a name="to-add-subtotals-and-totals"></a><span data-ttu-id="e6c06-200">添加小计和总计</span><span class="sxs-lookup"><span data-stu-id="e6c06-200">To add subtotals and totals</span></span>  
  
1.  <span data-ttu-id="e6c06-201">在“选择布局”页的“选项”下，确认已选择“显示小计和总计”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-201">On the **Choose the layout** page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
2.  <span data-ttu-id="e6c06-202">验证是否选择了“分块式，小计下方显示”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-202">Verify that **Blocked, subtotal below** is selected.</span></span>  
  
     <span data-ttu-id="e6c06-203">向导的“预览”窗格将显示包含有五行的表。</span><span class="sxs-lookup"><span data-stu-id="e6c06-203">The wizard Preview pane displays a table with five rows.</span></span> <span data-ttu-id="e6c06-204">当您运行报表时，每行将按以下方式显示：</span><span class="sxs-lookup"><span data-stu-id="e6c06-204">When you run the report, each row will display in the following way:</span></span>  
  
    1.  <span data-ttu-id="e6c06-205">第一行将对表重复一次以显示列标题。</span><span class="sxs-lookup"><span data-stu-id="e6c06-205">The first row will repeat once for the table to show column headings.</span></span>  
  
    2.  <span data-ttu-id="e6c06-206">第二行将对销售订单中的每个行项重复一次并显示产品名称、订单数量和行总计。</span><span class="sxs-lookup"><span data-stu-id="e6c06-206">The second row will repeat once for each line item in the sales order and display the product name, order quantity, and line total.</span></span>  
  
    3.  <span data-ttu-id="e6c06-207">第三行将对每个销售订单重复一次以显示每个订单的小计。</span><span class="sxs-lookup"><span data-stu-id="e6c06-207">The third row will repeat once for each sales order to display subtotals per order.</span></span>  
  
    4.  <span data-ttu-id="e6c06-208">第四行将对每个订单日期重复一次以显示每天的小计。</span><span class="sxs-lookup"><span data-stu-id="e6c06-208">The fourth row will repeat once for each order date to display the subtotals per day.</span></span>  
  
    5.  <span data-ttu-id="e6c06-209">第五行将对表重复一次以显示总计。</span><span class="sxs-lookup"><span data-stu-id="e6c06-209">The fifth row will repeat once for the table to display the grand totals.</span></span>  
  
3.  <span data-ttu-id="e6c06-210">清除“展开/折叠组”选项\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-210">Clear the option **Expand/collapse groups**.</span></span> <span data-ttu-id="e6c06-211">在本教程中，创建的报表不会使用明细功能（用户可通过此功能来展开父组层次结构）来显示子组行和详细信息行。</span><span class="sxs-lookup"><span data-stu-id="e6c06-211">In this tutorial, the report you create does not use the drilldown feature that lets a user expand a parent group hierarchy to display child group rows and detail rows.</span></span>  
  
4.  <span data-ttu-id="e6c06-212">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="e6c06-212">Click **Next**.</span></span>  
  
##  <a name="1e-choose-a-style-in-the-table-wizard"></a><a name="Style"></a><span data-ttu-id="e6c06-213">1e.</span><span class="sxs-lookup"><span data-stu-id="e6c06-213">1e.</span></span> <span data-ttu-id="e6c06-214">在表向导中选择样式</span><span class="sxs-lookup"><span data-stu-id="e6c06-214">Choose a Style in the Table Wizard</span></span>  
 <span data-ttu-id="e6c06-215">样式指定字形、颜色集和边框样式。</span><span class="sxs-lookup"><span data-stu-id="e6c06-215">A style specifies a font style, a set of colors, and a border style.</span></span>  
  
#### <a name="to-specify-a-table-style"></a><span data-ttu-id="e6c06-216">指定表样式</span><span class="sxs-lookup"><span data-stu-id="e6c06-216">To specify a table style</span></span>  
  
1.  <span data-ttu-id="e6c06-217">在 "**选择样式**" 页的 "样式" 窗格中，选择 "海运"。</span><span class="sxs-lookup"><span data-stu-id="e6c06-217">On the **Choose a Style** page, in the Styles pane, select Ocean.</span></span>  
  
     <span data-ttu-id="e6c06-218">“预览”窗格将显示具有该样式的表的示例。</span><span class="sxs-lookup"><span data-stu-id="e6c06-218">The Preview pane displays a sample of the table with that style.</span></span>  
  
2.  <span data-ttu-id="e6c06-219">（可选）单击其他样式以查看应用了样式的示例。</span><span class="sxs-lookup"><span data-stu-id="e6c06-219">Optionally, click the other styles to see the sample with them applied.</span></span>  
  
3.  <span data-ttu-id="e6c06-220">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="e6c06-220">Click **Finish**.</span></span>  
  
 <span data-ttu-id="e6c06-221">表将添加到设计图面中。</span><span class="sxs-lookup"><span data-stu-id="e6c06-221">The table is added to the design surface.</span></span> <span data-ttu-id="e6c06-222">该表有 5 列、5 行。</span><span class="sxs-lookup"><span data-stu-id="e6c06-222">The table has 5 columns and 5 rows.</span></span> <span data-ttu-id="e6c06-223">“行组”窗格显示三个行组：SalesDate、Subcategory 和 Details。</span><span class="sxs-lookup"><span data-stu-id="e6c06-223">The Row Groups pane shows three row groups: SalesDate, Subcategory, and Details.</span></span> <span data-ttu-id="e6c06-224">详细信息数据是由数据集查询检索的所有数据。</span><span class="sxs-lookup"><span data-stu-id="e6c06-224">Detail data is all the data that is retrieved by the dataset query.</span></span>  
  
##  <a name="2-format-data-as-currency"></a><a name="FormatCurrency"></a><span data-ttu-id="e6c06-225">2. 将数据格式设置为货币</span><span class="sxs-lookup"><span data-stu-id="e6c06-225">2. Format Data as Currency</span></span>  
 <span data-ttu-id="e6c06-226">默认情况下，Sales 字段的汇总数据将显示总数。</span><span class="sxs-lookup"><span data-stu-id="e6c06-226">By default, the summary data for the Sales field displays a general number.</span></span> <span data-ttu-id="e6c06-227">请设置其格式，以使其显示货币形式的数字。</span><span class="sxs-lookup"><span data-stu-id="e6c06-227">Format it to display the number as currency.</span></span> <span data-ttu-id="e6c06-228">切换“占位符样式”，将格式化的文本框和占位符文本显示为示例值\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-228">Toggle **Placeholder Styles** to display formatted text boxes and placeholder text as sample values.</span></span>  
  
#### <a name="to-format-a-currency-field"></a><span data-ttu-id="e6c06-229">设置货币字段格式</span><span class="sxs-lookup"><span data-stu-id="e6c06-229">To format a currency field</span></span>  
  
1.  <span data-ttu-id="e6c06-230">单击 "**设计**" 切换到 "设计" 视图。</span><span class="sxs-lookup"><span data-stu-id="e6c06-230">Click **Design** to switch to design view.</span></span>  
  
2.  <span data-ttu-id="e6c06-231">单击第二行（位于列标题行下）Sales 列的单元，然后向下拖动以选定包含 `[Sum(Sales)]`的所有单元。</span><span class="sxs-lookup"><span data-stu-id="e6c06-231">Click the cell in the second row (under the column headings row) in the Sales column and drag down to select all cells that contain `[Sum(Sales)]`.</span></span>  
  
3.  <span data-ttu-id="e6c06-232">在“开始”选项卡上的“数字”组中，单击“货币”按钮\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-232">On the **Home** tab, in the **Number** group, click the **Currency** button.</span></span> <span data-ttu-id="e6c06-233">单元会更改为显示已设置好格式的货币。</span><span class="sxs-lookup"><span data-stu-id="e6c06-233">The cells change to show the formatted currency.</span></span>  
  
     <span data-ttu-id="e6c06-234">如果区域设置为“英语(美国)”，则默认示例文本为 [**$12,345.00**]。</span><span class="sxs-lookup"><span data-stu-id="e6c06-234">If your regional setting is English (United States), the default sample text is [**$12,345.00**].</span></span> <span data-ttu-id="e6c06-235">如果看不到示例货币值，请在 "**数字**" 组中单击 "**占位符样式**"，然后单击 "**示例值**"。</span><span class="sxs-lookup"><span data-stu-id="e6c06-235">If you do not see an example currency value, click **Placeholder Styles** in the **Numbers** group, and then click **Sample Values**.</span></span>  
  
4.  <span data-ttu-id="e6c06-236">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="e6c06-236">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="e6c06-237">Sales 的汇总值会以货币形式显示。</span><span class="sxs-lookup"><span data-stu-id="e6c06-237">The summary values for Sales display as currency.</span></span>  
  
##  <a name="3-format-data-as-date"></a><a name="FormatDate"></a><span data-ttu-id="e6c06-238">3. 将数据格式设置为日期</span><span class="sxs-lookup"><span data-stu-id="e6c06-238">3. Format Data as Date</span></span>  
 <span data-ttu-id="e6c06-239">默认情况下，SalesDate 字段会同时显示日期和时间信息。</span><span class="sxs-lookup"><span data-stu-id="e6c06-239">By default, the SalesDate field displays both date and time information.</span></span> <span data-ttu-id="e6c06-240">您可以设置其格式，使其只显示日期。</span><span class="sxs-lookup"><span data-stu-id="e6c06-240">You can format them to display only the date.</span></span>  
  
#### <a name="to-format-a-date-field-as-the-default-format"></a><span data-ttu-id="e6c06-241">将日期字段设置为默认格式</span><span class="sxs-lookup"><span data-stu-id="e6c06-241">To format a date field as the default format</span></span>  
  
1.  <span data-ttu-id="e6c06-242">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="e6c06-242">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="e6c06-243">单击包含 `[SalesDate]`的单元格。</span><span class="sxs-lookup"><span data-stu-id="e6c06-243">Click the cell that contains `[SalesDate]`.</span></span>  
  
3.  <span data-ttu-id="e6c06-244">在功能区上，在 "**主页**" 选项卡上的 "**数字**" 组中，从下拉列表中选择 "**日期**"。</span><span class="sxs-lookup"><span data-stu-id="e6c06-244">On the Ribbon, on the **Home** tab, in the **Number** group, from the drop-down list, select **Date**.</span></span>  
  
     <span data-ttu-id="e6c06-245">单元格将显示示例日期 **[1/31/2000]**。</span><span class="sxs-lookup"><span data-stu-id="e6c06-245">The cell displays the example date **[1/31/2000]**.</span></span> <span data-ttu-id="e6c06-246">如果看不到示例日期，请单击“数字”\*\*\*\* 组中的“占位符样式”\*\*\*\*，然后单击“示例值”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-246">If you do not see an example date, click **Placeholder Styles** in the **Numbers** group, and then click **Sample Values**.</span></span>  
  
4.  <span data-ttu-id="e6c06-247">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="e6c06-247">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="e6c06-248">SalesDate 值将以默认日期格式显示。</span><span class="sxs-lookup"><span data-stu-id="e6c06-248">The SalesDate values display in the default date format.</span></span>  
  
#### <a name="to-change-the-date-format-to-a-custom-format"></a><span data-ttu-id="e6c06-249">将日期格式更改为自定义格式</span><span class="sxs-lookup"><span data-stu-id="e6c06-249">To change the date format to a custom format</span></span>  
  
1.  <span data-ttu-id="e6c06-250">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="e6c06-250">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="e6c06-251">单击包含 `[SalesDate]`的单元格。</span><span class="sxs-lookup"><span data-stu-id="e6c06-251">Click the cell that contains `[SalesDate]`.</span></span>  
  
3.  <span data-ttu-id="e6c06-252">在 "**主页**" 选项卡上的 "**数字**" 组中，单击对话框启动器。</span><span class="sxs-lookup"><span data-stu-id="e6c06-252">On the **Home** tab, in the **Number** group, click the dialog box launcher.</span></span>  
  
     <span data-ttu-id="e6c06-253">启动器是该组右侧角中的小箭头。</span><span class="sxs-lookup"><span data-stu-id="e6c06-253">The launcher is the small arrow in the right-hand corner of the group.</span></span> <span data-ttu-id="e6c06-254">将打开“文本框属性”对话框\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-254">The **Text Box Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="e6c06-255">在“类别”窗格中，确认已选中“日期”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-255">In the Category pane, verify that **Date** is selected.</span></span>  
  
5.  <span data-ttu-id="e6c06-256">在“类型”窗格中，选择“2000 年 1 月 31 日”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-256">In the **Type** pane, select **January 31, 2000**.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="e6c06-257">单元会显示示例日期 **[2000 年 1 月 31 日]**。</span><span class="sxs-lookup"><span data-stu-id="e6c06-257">The cell displays the example date **[January 31, 2000]**.</span></span>  
  
7.  <span data-ttu-id="e6c06-258">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="e6c06-258">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="e6c06-259">SalesDate 值将显示月份名而非月份数字。</span><span class="sxs-lookup"><span data-stu-id="e6c06-259">The SalesDate value displays with the name of the month instead of the number for the month.</span></span>  
  
##  <a name="4-change-column-widths"></a><a name="Width"></a><span data-ttu-id="e6c06-260">4. 更改列宽</span><span class="sxs-lookup"><span data-stu-id="e6c06-260">4. Change Column Widths</span></span>  
 <span data-ttu-id="e6c06-261">默认情况下，表中的每个单元格都包含一个文本框。</span><span class="sxs-lookup"><span data-stu-id="e6c06-261">By default, each cell in a table contains a text box.</span></span> <span data-ttu-id="e6c06-262">在呈现页面时，文本框将垂直扩展以容纳文本。</span><span class="sxs-lookup"><span data-stu-id="e6c06-262">A text box expands vertically to accommodate text when the page is rendered.</span></span> <span data-ttu-id="e6c06-263">在呈现的报表中，每个行将扩展到行中呈现的最高文本框的高度。</span><span class="sxs-lookup"><span data-stu-id="e6c06-263">In the rendered report, each row expands to the height of the tallest rendered text box in the row.</span></span> <span data-ttu-id="e6c06-264">设计图面上的行的高度不会影响已呈现报表中的行的高度。</span><span class="sxs-lookup"><span data-stu-id="e6c06-264">The height of the row on the design surface has no affect on the height of the row in the rendered report.</span></span>  
  
 <span data-ttu-id="e6c06-265">若要减少每个行占用的垂直空间量，请扩展列宽以容纳单个行的列中的文本框的预计内容。</span><span class="sxs-lookup"><span data-stu-id="e6c06-265">To reduce the amount of vertical space each row takes, expand the column width to accommodate the expected contents of the text boxes in the column on one line.</span></span>  
  
#### <a name="to-change-the-width-of-table-columns"></a><span data-ttu-id="e6c06-266">更改表的列宽</span><span class="sxs-lookup"><span data-stu-id="e6c06-266">To change the width of table columns</span></span>  
  
1.  <span data-ttu-id="e6c06-267">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="e6c06-267">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="e6c06-268">单击表，以便在此表的上方和旁边显示列控点和行控点。</span><span class="sxs-lookup"><span data-stu-id="e6c06-268">Click the table so that column and row handles appear above and next to the table.</span></span>  
  
     <span data-ttu-id="e6c06-269">沿此表的上方和一侧显示的灰色条状物就是列控点和行控点。</span><span class="sxs-lookup"><span data-stu-id="e6c06-269">The gray bars along the top and side of the table are the column and row handles.</span></span>  
  
3.  <span data-ttu-id="e6c06-270">指向列控点之间的行，使光标变为双箭头。</span><span class="sxs-lookup"><span data-stu-id="e6c06-270">Point to the line between column handles so that the cursor changes into a double arrow.</span></span> <span data-ttu-id="e6c06-271">拖动列，调整到所需大小。</span><span class="sxs-lookup"><span data-stu-id="e6c06-271">Drag the columns to the size you want.</span></span> <span data-ttu-id="e6c06-272">例如，展开 Product 列，以便产品名称显示在一行中。</span><span class="sxs-lookup"><span data-stu-id="e6c06-272">For example, expand the column for Product so that the product name displays on one line.</span></span>  
  
4.  <span data-ttu-id="e6c06-273">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="e6c06-273">Click **Run** to preview your report.</span></span>  
  
##  <a name="5-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="e6c06-274">5. 添加报表标题</span><span class="sxs-lookup"><span data-stu-id="e6c06-274">5. Add a Report Title</span></span>  
 <span data-ttu-id="e6c06-275">报表标题将出现在报表的顶部。</span><span class="sxs-lookup"><span data-stu-id="e6c06-275">A report title appears at the top of the report.</span></span> <span data-ttu-id="e6c06-276">可以将报表标题置于报表表头中或置于表体顶部的文本框中（如果报表未使用表头）。</span><span class="sxs-lookup"><span data-stu-id="e6c06-276">You can place the report title in a report header or if the report does not use one, in a text box at the top of the report body.</span></span> <span data-ttu-id="e6c06-277">在本教程中，您将使用自动放置在表体顶部的文本框。</span><span class="sxs-lookup"><span data-stu-id="e6c06-277">In this tutorial, you will use the text box that is automatically placed at the top of the report body.</span></span>  
  
 <span data-ttu-id="e6c06-278">通过将不同的字体样式、大小和颜色应用于文本的短语和单个字符，可以进一步增强文本。</span><span class="sxs-lookup"><span data-stu-id="e6c06-278">The text can be further enhanced by applying different font styles, sizes, and colors to phrases and individual characters of the text.</span></span> <span data-ttu-id="e6c06-279">有关详细信息，请参阅[设置文本框中文本的格式（报表生成器和 SSRS）](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e6c06-279">For more information, see [Format Text in a Text Box &#40;Report Builder and SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md).</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="e6c06-280">添加报表标题</span><span class="sxs-lookup"><span data-stu-id="e6c06-280">To add a report title</span></span>  
  
1.  <span data-ttu-id="e6c06-281">在设计图面上，单击“单击以添加标题”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-281">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="e6c06-282">键入 **Product Sales**，然后在文本框外部单击。</span><span class="sxs-lookup"><span data-stu-id="e6c06-282">Type **Product Sales**, and then click outside the text box.</span></span>  
  
3.  <span data-ttu-id="e6c06-283">右键单击包含 Product Sales 的文本框，然后单击“文本框属性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-283">Right-click the text box that contains **Product Sales** and click **Text Box Properties**.</span></span>  
  
4.  <span data-ttu-id="e6c06-284">在“文本框属性”\*\*\*\* 对话框中，单击“字体”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-284">In the **Text Box Properties** dialog box, click **Font**.</span></span>  
  
5.  <span data-ttu-id="e6c06-285">在“大小”\*\*\*\* 列表中，选择“18pt”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-285">In the **Size** list, select **18pt**.</span></span>  
  
6.  <span data-ttu-id="e6c06-286">在“颜色”列表中，选择“青蓝色”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-286">In the **Color** list, select **Cornflower Blue**.</span></span>  
  
7.  <span data-ttu-id="e6c06-287">选择“粗体”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-287">Select **Bold**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="6-save-the-report"></a><a name="Save"></a><span data-ttu-id="e6c06-288">6. 保存报表</span><span class="sxs-lookup"><span data-stu-id="e6c06-288">6. Save the Report</span></span>  
 <span data-ttu-id="e6c06-289">将报表保存到报表服务器或计算机上。</span><span class="sxs-lookup"><span data-stu-id="e6c06-289">Save the report to a report server or your computer.</span></span> <span data-ttu-id="e6c06-290">如果不将报表保存到报表服务器上，则许多 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 功能（如报表部件和子报表）将不可用。</span><span class="sxs-lookup"><span data-stu-id="e6c06-290">If you do not save the report to the report server, a number of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features such as report parts and subreports are not available.</span></span>  
  
#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="e6c06-291">将报表保存到报表服务器</span><span class="sxs-lookup"><span data-stu-id="e6c06-291">To save the report on a report server</span></span>  
  
1.  <span data-ttu-id="e6c06-292">从 **“报表生成器”** 按钮，单击 **“另存为”**。</span><span class="sxs-lookup"><span data-stu-id="e6c06-292">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="e6c06-293">单击 **“最近使用的站点和服务器”**。</span><span class="sxs-lookup"><span data-stu-id="e6c06-293">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="e6c06-294">选择或键入您拥有保存报表权限的报表服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="e6c06-294">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="e6c06-295">此时将显示“正在连接到报表服务器”消息。</span><span class="sxs-lookup"><span data-stu-id="e6c06-295">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="e6c06-296">当连接完成时，您将看到报表服务器管理员指定为报表默认位置的报表文件夹的内容。</span><span class="sxs-lookup"><span data-stu-id="e6c06-296">When the connection is complete, you see the contents of the report folder that the report server administrator specified as the default location for reports.</span></span>  
  
4.  <span data-ttu-id="e6c06-297">在“名称”中，用“Product Sales”替换默认名称\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-297">In **Name**, replace the default name with **Product Sales**.</span></span>  
  
5.  <span data-ttu-id="e6c06-298">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="e6c06-298">Click **Save**.</span></span>  
  
 <span data-ttu-id="e6c06-299">报表即已保存至报表服务器。</span><span class="sxs-lookup"><span data-stu-id="e6c06-299">The report is saved to the report server.</span></span> <span data-ttu-id="e6c06-300">您连接的报表服务器的名称将显示在窗口底部的状态栏中。</span><span class="sxs-lookup"><span data-stu-id="e6c06-300">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
#### <a name="to-save-the-report-on-your-computer"></a><span data-ttu-id="e6c06-301">将报表保存到计算机上</span><span class="sxs-lookup"><span data-stu-id="e6c06-301">To save the report on your computer</span></span>  
  
1.  <span data-ttu-id="e6c06-302">从 **“报表生成器”** 按钮，单击 **“另存为”**。</span><span class="sxs-lookup"><span data-stu-id="e6c06-302">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="e6c06-303">依次单击“桌面”、“我的文档”或“我的电脑”，并浏览到要保存该报表的文件夹\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-303">Click **Desktop**, **My Documents**, or **My computer**, and browse to the folder where you want to save the report.</span></span>  
  
3.  <span data-ttu-id="e6c06-304">在“名称”中，用“Product Sales”替换默认名称\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6c06-304">In **Name**, replace the default name with **Product Sales**.</span></span>  
  
4.  <span data-ttu-id="e6c06-305">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="e6c06-305">Click **Save**.</span></span>  
  
##  <a name="7-export-the-report"></a><a name="Export"></a><span data-ttu-id="e6c06-306">7. 导出报表</span><span class="sxs-lookup"><span data-stu-id="e6c06-306">7. Export the Report</span></span>  
 <span data-ttu-id="e6c06-307">可以将报表导出为不同的格式，如 Microsoft Excel 和以逗号分隔的值 (CSV)。</span><span class="sxs-lookup"><span data-stu-id="e6c06-307">Reports can be exported to different formats such Microsoft Excel and comma separated value (CSV).</span></span> <span data-ttu-id="e6c06-308">有关详细信息，请参阅[导出报表 &#40;报表生成器和 SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e6c06-308">For more information, see [Exporting Reports &#40;Report Builder and SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="e6c06-309">在本教程中，您将报表导出为 Excel 格式，并设置报表的属性以便为工作簿选项卡提供自定义名称。</span><span class="sxs-lookup"><span data-stu-id="e6c06-309">In this tutorial, you will export the report to Excel and set a property on the report to provide a custom name for the workbook tab.</span></span>  
  
#### <a name="to-specify-the-workbook-tab-name"></a><span data-ttu-id="e6c06-310">指定工作簿选项卡名称</span><span class="sxs-lookup"><span data-stu-id="e6c06-310">To specify the workbook tab name</span></span>  
  
1.  <span data-ttu-id="e6c06-311">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="e6c06-311">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="e6c06-312">单击该报表的外部。</span><span class="sxs-lookup"><span data-stu-id="e6c06-312">Click anywhere outside the report.</span></span>  
  
3.  <span data-ttu-id="e6c06-313">.在 "属性" 窗格中，找到 "InitialPageName" 属性并键入**Product Sales Excel**。</span><span class="sxs-lookup"><span data-stu-id="e6c06-313">.In the Properties pane, locate the InitialPageName property and type **Product Sales Excel**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e6c06-314">如果 "属性" 窗格不可见，请单击功能区上的 "视图" 选项卡，然后单击 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="e6c06-314">If the Properties pane is not visible, click the View tab on the ribbon, and then click **Properties**.</span></span>  
  
#### <a name="to-export-a-report-to-excel"></a><span data-ttu-id="e6c06-315">将报表导出为 Excel 格式</span><span class="sxs-lookup"><span data-stu-id="e6c06-315">To export a report to Excel</span></span>  
  
1.  <span data-ttu-id="e6c06-316">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="e6c06-316">Click **Run** to preview the report.</span></span>  
  
2.  <span data-ttu-id="e6c06-317">.在功能区上，单击 "**导出**"，然后单击 " **Excel**"。</span><span class="sxs-lookup"><span data-stu-id="e6c06-317">.On the ribbon, click **Export**, and then click **Excel**.</span></span>  
  
     <span data-ttu-id="e6c06-318">此时会打开“另存为”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="e6c06-318">The **Save As** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="e6c06-319">浏览到 "**文档**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="e6c06-319">Browse to the **Documents** folder.</span></span>  
  
4.  <span data-ttu-id="e6c06-320">在 "**文件名**" 文本框中，键入**Product Sales Excel**。</span><span class="sxs-lookup"><span data-stu-id="e6c06-320">In the **File name** text box, type **Product Sales Excel**.</span></span>  
  
5.  <span data-ttu-id="e6c06-321">确认文件类型为 " **Excel 工作簿**"。</span><span class="sxs-lookup"><span data-stu-id="e6c06-321">Verify that the file type is **Excel Workbook**.</span></span>  
  
6.  <span data-ttu-id="e6c06-322">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="e6c06-322">Click **Save**.</span></span>  
  
#### <a name="to-view-the-report-in-excel"></a><span data-ttu-id="e6c06-323">在 Excel 中查看报表</span><span class="sxs-lookup"><span data-stu-id="e6c06-323">To view the report in Excel</span></span>  
  
1.  <span data-ttu-id="e6c06-324">打开 "**文档**" 文件夹，然后双击 "**产品销售额 Excel.xlsx**。</span><span class="sxs-lookup"><span data-stu-id="e6c06-324">Open the **Documents** folder and double click **Product Sales Excel.xlsx**.</span></span>  
  
2.  <span data-ttu-id="e6c06-325">验证工作簿选项卡的名称是否为 **Product Sales Excel**。</span><span class="sxs-lookup"><span data-stu-id="e6c06-325">Verify that the name of the workbook tab is **Product Sales Excel**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e6c06-326">后续步骤</span><span class="sxs-lookup"><span data-stu-id="e6c06-326">Next Steps</span></span>  
 <span data-ttu-id="e6c06-327">到此为止，我们结束了有关如何创建基本表格报表的演练。</span><span class="sxs-lookup"><span data-stu-id="e6c06-327">This concludes the walkthrough for how to create a basic table report.</span></span> <span data-ttu-id="e6c06-328">有关表的详细信息，请参阅[表、矩阵和列表（报表生成器和 SSRS）](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e6c06-328">For more information about tables, see [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6c06-329">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e6c06-329">See Also</span></span>  
 <span data-ttu-id="e6c06-330">[教程 &#40;报表生成器&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="e6c06-330">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="e6c06-331">SQL Server 2014 中的报表生成器</span><span class="sxs-lookup"><span data-stu-id="e6c06-331">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
