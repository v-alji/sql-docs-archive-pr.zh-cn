---
title: 教程：创建自由格式的报表（报表生成器） | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 87288b59-faf2-4b1d-a8e4-a7582baedf2f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 515b0d2566efa4e11216a28648338c7ec43f3950
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692225"
---
# <a name="tutorial-creating-a-free-form-report-report-builder"></a><span data-ttu-id="f64e6-102">教程：创建自由格式的报表（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="f64e6-102">Tutorial: Creating a Free Form Report (Report Builder)</span></span>
  <span data-ttu-id="f64e6-103">本教程教你如何创建一个与书信格式类似的 SSRS 自由格式报表。</span><span class="sxs-lookup"><span data-stu-id="f64e6-103">This tutorial teaches you how to create an SSRS free form report that resembles a forms letter.</span></span> <span data-ttu-id="f64e6-104">你可以排列报表项来创建一个具有文本框、图像和其他数据区域的窗体。</span><span class="sxs-lookup"><span data-stu-id="f64e6-104">You can arrange report items to create a form with text boxes, images and other data regions.</span></span>

 <span data-ttu-id="f64e6-105">你在本教程中创建的报表是基于教程中包括的示例销售数据创建的。</span><span class="sxs-lookup"><span data-stu-id="f64e6-105">The report you create in this tutorial is based on sample sales data that is included in the tutorial.</span></span> <span data-ttu-id="f64e6-106">该报表按地区对信息进行分组，并且显示该地区的销售经理的姓名以及详细和汇总销售信息。</span><span class="sxs-lookup"><span data-stu-id="f64e6-106">The report groups information by territory and displays the name of the sales manager for the territory as well as detailed and summary sales information.</span></span> <span data-ttu-id="f64e6-107">您将使用列表数据区域作为自由格式的报表的基础，然后添加具有图像的装饰性面板、插入了数据的静态文本、用于显示详细信息的表以及可选的用于显示汇总信息的饼图和柱形图。</span><span class="sxs-lookup"><span data-stu-id="f64e6-107">You will use the list data region as the foundation for the free form report, and then add a decorative panel with an image, static text with data inserted, a table to show detailed information, and optionally, pie and column charts to display summary information.</span></span>

##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="f64e6-108">你将学习的内容</span><span class="sxs-lookup"><span data-stu-id="f64e6-108">What You Will Learn</span></span>
 <span data-ttu-id="f64e6-109">在本教程中，您将了解如何执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="f64e6-109">In this tutorial, you will learn how to do the following:</span></span>

-   [<span data-ttu-id="f64e6-110">创建空白报表、数据源和数据集</span><span class="sxs-lookup"><span data-stu-id="f64e6-110">Create a Blank Report, Data Source, and Dataset</span></span>](#BlankReport)

-   [<span data-ttu-id="f64e6-111">添加并配置列表</span><span class="sxs-lookup"><span data-stu-id="f64e6-111">Add and Configure a List</span></span>](#List)

-   [<span data-ttu-id="f64e6-112">添加图形</span><span class="sxs-lookup"><span data-stu-id="f64e6-112">Add Graphics</span></span>](#Graphics)

-   [<span data-ttu-id="f64e6-113">添加自由格式的文本</span><span class="sxs-lookup"><span data-stu-id="f64e6-113">Add Free Form Text</span></span>](#Text)

-   [<span data-ttu-id="f64e6-114">添加用于显示详细信息的表</span><span class="sxs-lookup"><span data-stu-id="f64e6-114">Add a Table to Show Details</span></span>](#Table)

-   [<span data-ttu-id="f64e6-115">设置数据格式</span><span class="sxs-lookup"><span data-stu-id="f64e6-115">Format Data</span></span>](#Format)

-   [<span data-ttu-id="f64e6-116">保存报表</span><span class="sxs-lookup"><span data-stu-id="f64e6-116">Save the Report</span></span>](#Save)

### <a name="other-optional-steps"></a><span data-ttu-id="f64e6-117">其他可选步骤</span><span class="sxs-lookup"><span data-stu-id="f64e6-117">Other Optional Steps</span></span>

-   [<span data-ttu-id="f64e6-118">添加线条以便分隔报表区域</span><span class="sxs-lookup"><span data-stu-id="f64e6-118">Add a Line to Separate Areas of Report</span></span>](#Line)

-   [<span data-ttu-id="f64e6-119">添加汇总数据可视化</span><span class="sxs-lookup"><span data-stu-id="f64e6-119">Add Summary Data Visualization</span></span>](#Visualization)

 <span data-ttu-id="f64e6-120">完成本教程的预计学时：20 分钟。</span><span class="sxs-lookup"><span data-stu-id="f64e6-120">Estimated time to complete this tutorial: 20 minutes.</span></span>

## <a name="requirements"></a><span data-ttu-id="f64e6-121">要求</span><span class="sxs-lookup"><span data-stu-id="f64e6-121">Requirements</span></span>
 <span data-ttu-id="f64e6-122">有关要求的详细信息，请参阅[教程先决条件（报表生成器）](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="f64e6-122">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>

##  <a name="1-create-a-blank-report-data-source-and-dataset"></a><a name="BlankReport"></a><span data-ttu-id="f64e6-123">1. 创建空白报表、数据源和数据集</span><span class="sxs-lookup"><span data-stu-id="f64e6-123">1. Create a Blank Report, Data Source, and Dataset</span></span>

> [!NOTE]
>  <span data-ttu-id="f64e6-124">在本教程中，查询包含了数据值，这样报表则不需要外部数据源。</span><span class="sxs-lookup"><span data-stu-id="f64e6-124">In this tutorial, the query contains the data values so that the report does not need an external data source.</span></span> <span data-ttu-id="f64e6-125">使用此内部数据类型对达成学习目标非常有益，但是该方法会使查询变得很长。</span><span class="sxs-lookup"><span data-stu-id="f64e6-125">The use of this type of internal data is great for learning purposes, but the approach makes the query long.</span></span> <span data-ttu-id="f64e6-126">.</span><span class="sxs-lookup"><span data-stu-id="f64e6-126">.</span></span>

#### <a name="to-create-a-blank-report"></a><span data-ttu-id="f64e6-127">创建空白报表</span><span class="sxs-lookup"><span data-stu-id="f64e6-127">To create a blank report</span></span>

1.  <span data-ttu-id="f64e6-128">单击 **“开始”**，依次指向 **“程序”**、 **Microsoft SQL Server 2012 Report Builder**，再单击 **“报表生成器”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-128">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="f64e6-129">此时应显示 **“入门”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="f64e6-129">The **Getting Started** dialog box should appear.</span></span> <span data-ttu-id="f64e6-130">如果未显示该对话框，则从“报表生成器”按钮，单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-130">If it does not, from the Report Builder button, click **New**.</span></span>

2.  <span data-ttu-id="f64e6-131">在 **“入门”** 对话框的左窗格中，确保已选择 **“新建报表”** 。</span><span class="sxs-lookup"><span data-stu-id="f64e6-131">In the left pane of the **Getting Started** dialog box, verify that **New Report** is selected.</span></span>

3.  <span data-ttu-id="f64e6-132">在右窗格中，单击 **“空白报表”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-132">In the right pane, click **Blank Report**.</span></span>

#### <a name="to-create-a-new-data-source"></a><span data-ttu-id="f64e6-133">创建新数据源</span><span class="sxs-lookup"><span data-stu-id="f64e6-133">To create a new data source</span></span>

1.  <span data-ttu-id="f64e6-134">在 "报表数据" 窗格中，单击 "**新建**"，然后单击 "**数据源**"。</span><span class="sxs-lookup"><span data-stu-id="f64e6-134">In the Report Data pane, click **New**, and then click **Data Source**.</span></span>

2.  <span data-ttu-id="f64e6-135">在 " `Name` 类型" 框中，键入： **listdatasource。**</span><span class="sxs-lookup"><span data-stu-id="f64e6-135">In the `Name` box, type: **ListDataSource**</span></span>

3.  <span data-ttu-id="f64e6-136">单击 **“使用我的报表中嵌入的连接”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-136">Click **Use a connection embedded in my report**.</span></span>

4.  <span data-ttu-id="f64e6-137">验证连接类型是否为 "Microsoft SQL Server"，然后在 "**连接字符串**" 框中键入： **Data \<servername> Source =**</span><span class="sxs-lookup"><span data-stu-id="f64e6-137">Verify that the connection type is Microsoft SQL Server, and then in the **Connection string** box type: **Data Source = \<servername>**</span></span>

     <span data-ttu-id="f64e6-138">\<servername>例如，Report001) ，指定在其上安装 SQL Server 数据库引擎实例的计算机。</span><span class="sxs-lookup"><span data-stu-id="f64e6-138">\<servername>, for example Report001, specifies a computer on which an instance of the SQL Server Database Engine is installed.</span></span> <span data-ttu-id="f64e6-139">因为报表数据不是从 SQL Server 数据库提取的，所以不需要包括数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="f64e6-139">Because the report data is not extracted from a SQL Server database, you need not include the name of a database.</span></span> <span data-ttu-id="f64e6-140">指定服务器上的默认数据库用于对查询进行分析。</span><span class="sxs-lookup"><span data-stu-id="f64e6-140">The default database on the specified server is used to parse the query.</span></span>

5.  <span data-ttu-id="f64e6-141">单击 **“凭据”**，然后输入连接至 SQL Server 数据库引擎实例所需的凭据。</span><span class="sxs-lookup"><span data-stu-id="f64e6-141">Click **Credentials**, and enter the credentials needed to connect to the instance of the SQL Server Database Engine.</span></span>

6.  <span data-ttu-id="f64e6-142">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="f64e6-142">Click **OK**.</span></span>

#### <a name="to-create-a-new-dataset"></a><span data-ttu-id="f64e6-143">新建数据集</span><span class="sxs-lookup"><span data-stu-id="f64e6-143">To create a new dataset</span></span>

1.  <span data-ttu-id="f64e6-144">在 "报表数据" 窗格中，单击 "**新建**"，然后单击 "**数据集**"。</span><span class="sxs-lookup"><span data-stu-id="f64e6-144">In the Report Data pane, click **New**, and then click **Dataset**.</span></span>

2.  <span data-ttu-id="f64e6-145">在 " `Name` 类型" 框中，键入： **ListDataset。**</span><span class="sxs-lookup"><span data-stu-id="f64e6-145">In the `Name` box, type: **ListDataset.**</span></span>

3.  <span data-ttu-id="f64e6-146">单击“使用在我的报表中嵌入的数据集” \*\*\*\*，然后验证数据源是否为 **ListDataSource**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-146">Click **Use a dataset embedded in my report**, and verify that the data source is **ListDataSource**.</span></span>

4.  <span data-ttu-id="f64e6-147">确保已选择 **“文本”** 查询类型，然后单击 **“查询设计器”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-147">Verify that the **Text** query type is selected, and then click **Query Designer**.</span></span>

5.  <span data-ttu-id="f64e6-148">单击 **“编辑为文本”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-148">Click **Edit as Text**.</span></span>

6.  <span data-ttu-id="f64e6-149">复制并将以下查询粘贴到查询窗格中：</span><span class="sxs-lookup"><span data-stu-id="f64e6-149">Copy and paste the following query into the query pane:</span></span>

    ```
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13747.25 AS money) AS Sales, 55 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(9248.15 AS money) As Sales, 37 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1800.00 AS money) AS Sales, 24 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1125.00 AS money) AS Sales, 15 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,  'Lens Adapter' as Product, CAST(742.50 AS money) AS Sales, 11 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1417.50 AS money) AS Sales, 21 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13497.30 AS money) AS Sales, 54 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(11997.60 AS money) AS Sales, 48 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(10247.95 AS money) As Sales, 41 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Tripod' as Product, CAST(1200.00 AS money) AS Sales, 16 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(2025.00 AS money) AS Sales, 27 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1425.00 AS money) AS Sales, 19 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(887.50 AS money) AS Sales, 13 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Lens Adapter' as Product, CAST(607.50 AS money) AS Sales, 9 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1215.00 AS money) AS Sales, 18 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(10191.00 AS money) AS Sales, 79 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8772.00 AS money) AS Sales, 68 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(10578.00 AS money) AS Sales, 82 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(7218.10 AS money) AS Sales, 38 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory,'Digital' as Subcategory,'Slim Digital' as Product, CAST(9307.55 AS money) AS Sales, 49 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(3870.00 AS money) AS Sales, 30 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(5805.00 AS money) AS Sales, 45 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8643.00 AS money) AS Sales, 67 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(9877.40 AS money) AS Sales, 52 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(12536.70 AS money) AS Sales, 66 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(6648.25 AS money) AS Sales, 35 as Quantity
    ```

7.  <span data-ttu-id="f64e6-150">单击“运行”图标以运行查询。</span><span class="sxs-lookup"><span data-stu-id="f64e6-150">Click Run icon to run the query.</span></span>

     <span data-ttu-id="f64e6-151">查询结果将是可用于在您的报表中显示的数据。</span><span class="sxs-lookup"><span data-stu-id="f64e6-151">The query results are the data available to display in your report.</span></span>

     <span data-ttu-id="f64e6-152">![查询设计器](../../2014/tutorials/media/tutorial-querydesigner.png "查询设计器")</span><span class="sxs-lookup"><span data-stu-id="f64e6-152">![Query Designer](../../2014/tutorials/media/tutorial-querydesigner.png "Query Designer")</span></span>

8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

##  <a name="2-add-and-configure-a-list"></a><a name="List"></a><span data-ttu-id="f64e6-153">2. 添加并配置列表</span><span class="sxs-lookup"><span data-stu-id="f64e6-153">2. Add and Configure a List</span></span>
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="f64e6-154">提供三个数据区域模板：表、矩阵和列表。</span><span class="sxs-lookup"><span data-stu-id="f64e6-154">provides three data region templates: table, matrix, and list.</span></span> <span data-ttu-id="f64e6-155">这些模板全都基于 Tablix 数据区域。</span><span class="sxs-lookup"><span data-stu-id="f64e6-155">These templates are all based on a tablix data region.</span></span>

 <span data-ttu-id="f64e6-156">在本教程中，你将使用一个列表来显示一个类似新闻稿的报表中各销售区域的销售信息。</span><span class="sxs-lookup"><span data-stu-id="f64e6-156">In this tutorial, you will use a list to display the sales information for sales territories in a report that resembles a newsletter.</span></span> <span data-ttu-id="f64e6-157">这些信息按地区分组。</span><span class="sxs-lookup"><span data-stu-id="f64e6-157">The information is grouped by territory.</span></span> <span data-ttu-id="f64e6-158">您将添加一个按地区对数据进行分组的新行组，然后删除内置的“详细信息”行组。</span><span class="sxs-lookup"><span data-stu-id="f64e6-158">You will add a new row group that groups data by territory, and then delete the built-in Details row group.</span></span> <span data-ttu-id="f64e6-159">该列表模板是创建自由格式报表的理想工具。</span><span class="sxs-lookup"><span data-stu-id="f64e6-159">The list template is ideal for creating free form reports.</span></span> <span data-ttu-id="f64e6-160">有关详细信息，请参阅[列出 &#40;报表生成器和 SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f64e6-160">For more information, see [Lists &#40;Report Builder and SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="f64e6-161">此报表使用纸张大小 Letter (8.5 X11) 以及 1 英寸的边距。</span><span class="sxs-lookup"><span data-stu-id="f64e6-161">This report uses the paper size Letter (8.5 X11) and 1 inch margins.</span></span> <span data-ttu-id="f64e6-162">高于 9 英寸或宽于 6 1/2 英寸的报表页可能会生成空白页。</span><span class="sxs-lookup"><span data-stu-id="f64e6-162">A report page taller than 9 inches or wider than 6 1/2 inches might generate blank pages.</span></span>

#### <a name="to-add-a-list"></a><span data-ttu-id="f64e6-163">添加列表</span><span class="sxs-lookup"><span data-stu-id="f64e6-163">To add a list</span></span>

1.  <span data-ttu-id="f64e6-164">在功能区的 **“插入”** 选项卡的 **“数据区域”** 区域中，单击 **“列表”** ，然后将该列表拖到表体内。</span><span class="sxs-lookup"><span data-stu-id="f64e6-164">On the **Insert** tab of the ribbon, in the **Data Regions** area, click **List** and then drag the list inside the report body.</span></span> <span data-ttu-id="f64e6-165">将列表设为 7 英寸高，6.25 英寸宽。</span><span class="sxs-lookup"><span data-stu-id="f64e6-165">Make the list 7 inches tall and 6.25 inches wide.</span></span>

2.  <span data-ttu-id="f64e6-166">在列表内单击，右键单击列表顶部，然后单击 **“Tablix 属性”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-166">Click inside the list, right-click the top of the list, and then click **Tablix Properties**.</span></span>

     <span data-ttu-id="f64e6-167">![正在添加列表](../../2014/tutorials/media/tutorial-addinglistwithnumbers.png "正在添加列表")</span><span class="sxs-lookup"><span data-stu-id="f64e6-167">![Adding list](../../2014/tutorials/media/tutorial-addinglistwithnumbers.png "Adding list")</span></span>

3.  <span data-ttu-id="f64e6-168">在 **“数据集名称”** 下拉列表中，选择 **ListDataset**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-168">In the **Dataset name** drop-down list, select **ListDataset**.</span></span>

4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

5.  <span data-ttu-id="f64e6-169">在列表内右键单击，然后单击 **“矩形属性”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-169">Right-click inside the list, and then click **Rectangle Properties**.</span></span>

     <span data-ttu-id="f64e6-170">![矩形属性命令](../../2014/tutorials/media/tutorial-rectanglepropertiescommand.png "矩形属性命令")</span><span class="sxs-lookup"><span data-stu-id="f64e6-170">![Rectangle Properties command](../../2014/tutorials/media/tutorial-rectanglepropertiescommand.png "Rectangle Properties command")</span></span>

6.  <span data-ttu-id="f64e6-171">在 **“常规”** 选项卡中，选中 **“在组件后面添加分页符”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="f64e6-171">On the **General** tab, select the **Add a page break after** checkbox.</span></span>

7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

#### <a name="to-add-a-new-row-group-and-to-delete-the-details-group"></a><span data-ttu-id="f64e6-172">添加新行组和删除“详细信息”组</span><span class="sxs-lookup"><span data-stu-id="f64e6-172">To add a new row group and to delete the Details group</span></span>

1.  <span data-ttu-id="f64e6-173">在“行组”窗格中，右键单击“详细信息”组，指向 **“添加组”**，然后单击 **“父组”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-173">In the Row Groups pane, right-click the Details group, point to **Add Group**, and then click **Parent Group**.</span></span>

     <span data-ttu-id="f64e6-174">![父组命令](../../2014/tutorials/media/tutorial-parentgroupcommand.png "父组命令")</span><span class="sxs-lookup"><span data-stu-id="f64e6-174">![Parent Group command](../../2014/tutorials/media/tutorial-parentgroupcommand.png "Parent Group command")</span></span>

2.  <span data-ttu-id="f64e6-175">在下拉列表中，选择 `[Territory].`。</span><span class="sxs-lookup"><span data-stu-id="f64e6-175">In the drop-down list, select `[Territory].`</span></span>

3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

     <span data-ttu-id="f64e6-176">将一列添加到该列表中。</span><span class="sxs-lookup"><span data-stu-id="f64e6-176">A column is added to the list.</span></span> <span data-ttu-id="f64e6-177">该列包含单元 `[Territory].`。</span><span class="sxs-lookup"><span data-stu-id="f64e6-177">The column contains the cell `[Territory].`</span></span>

4.  <span data-ttu-id="f64e6-178">右键单击列表中的 Territory 列，然后单击 **“删除列”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-178">Right-click the Territory column in the list, and then click **Delete Columns**.</span></span>

     <span data-ttu-id="f64e6-179">![删除列](../../2014/tutorials/media/tutorial-deletecolumnscommand.png "“删除列”")</span><span class="sxs-lookup"><span data-stu-id="f64e6-179">![Delete columns](../../2014/tutorials/media/tutorial-deletecolumnscommand.png "Delete columns")</span></span>

5.  <span data-ttu-id="f64e6-180">单击 **“仅删除列”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-180">Click **Delete Columns only**.</span></span>

     <span data-ttu-id="f64e6-181">!["删除列" 对话框](../../2014/tutorials/media/tutorial-deletecolumnsdialog.png "“删除列”对话框")</span><span class="sxs-lookup"><span data-stu-id="f64e6-181">![Delete Columns dialog box](../../2014/tutorials/media/tutorial-deletecolumnsdialog.png "Delete Columns dialog box")</span></span>

6.  <span data-ttu-id="f64e6-182">在“行组”窗格中，右键单击 **“详细信息”** 组，然后单击 **“删除组”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-182">In the Row Groups pane, right-click the **Details** group, and then click **Delete Group**.</span></span>

     <span data-ttu-id="f64e6-183">![删除详细信息组](../../2014/tutorials/media/tutorial-deletedetailsgroup.png "删除详细信息组")</span><span class="sxs-lookup"><span data-stu-id="f64e6-183">![Delete Details Group](../../2014/tutorials/media/tutorial-deletedetailsgroup.png "Delete Details Group")</span></span>

7.  <span data-ttu-id="f64e6-184">单击 **“仅删除组”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-184">Click **Delete Group only**.</span></span>

8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

##  <a name="3-add-graphics"></a><a name="Graphics"></a><span data-ttu-id="f64e6-185">3. 添加图形</span><span class="sxs-lookup"><span data-stu-id="f64e6-185">3. Add Graphics</span></span>
 <span data-ttu-id="f64e6-186">使用列表数据区域的好处之一是，您可以将矩形和文本框之类的报表项添加到任何地方，而不会被限制为表格布局。</span><span class="sxs-lookup"><span data-stu-id="f64e6-186">One of the advantages of using a list data region is that you can add report items such as rectangles and text boxes anywhere, instead of being limited to a tabular layout.</span></span> <span data-ttu-id="f64e6-187">您将通过添加图形（用颜色填充的矩形）增强报表的外观。</span><span class="sxs-lookup"><span data-stu-id="f64e6-187">You will enhance the appearance of the report by adding a graphic (a rectangle filled with a color).</span></span>

#### <a name="to-add-graphic-elements-to-the-report"></a><span data-ttu-id="f64e6-188">向报表添加图形元素</span><span class="sxs-lookup"><span data-stu-id="f64e6-188">To add graphic elements to the report</span></span>

1.  <span data-ttu-id="f64e6-189">在功能区的 "**插入**" 选项卡上，单击 "**矩形**"，然后将一个矩形拖到该列表的左上角。</span><span class="sxs-lookup"><span data-stu-id="f64e6-189">On the **Insert** tab of the ribbon, click **Rectangle**,and then drag a rectangle to the upper left corner of the list.</span></span> <span data-ttu-id="f64e6-190">使该矩形 7 英寸高，1 英寸宽。</span><span class="sxs-lookup"><span data-stu-id="f64e6-190">Make the rectangle 7 inches tall and 1 inch wide.</span></span>

2.  <span data-ttu-id="f64e6-191">右键单击该矩形，再单击 **“矩形属性”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-191">Right-click the rectangle, and then click **Rectangle Properties**.</span></span>

3.  <span data-ttu-id="f64e6-192">单击 **“填充”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f64e6-192">Click the **Fill** tab.</span></span>

4.  <span data-ttu-id="f64e6-193">在 **“填充颜色”** 下拉列表中，单击 **“其他颜色”**，然后选择 **“深灰”** 色。</span><span class="sxs-lookup"><span data-stu-id="f64e6-193">In the **Fill color** drop-down list, click **More Colors**, and then select the **DarkGray** color.</span></span>

     <span data-ttu-id="f64e6-194">![选择填充颜色](../../2014/tutorials/media/tutorial-selectfillcolorwithnumbers.png "选择填充颜色")</span><span class="sxs-lookup"><span data-stu-id="f64e6-194">![Select fill color](../../2014/tutorials/media/tutorial-selectfillcolorwithnumbers.png "Select fill color")</span></span>

5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

6.  <span data-ttu-id="f64e6-195">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="f64e6-195">Click **Run** to preview the report.</span></span>

 <span data-ttu-id="f64e6-196">该报表的左侧现在具有一个垂直图形，该图形由一个深灰色的矩形构成。</span><span class="sxs-lookup"><span data-stu-id="f64e6-196">The left side of the report now has vertical graphic that consists of a dark gray rectangle.</span></span>

##  <a name="4-add-free-form-text"></a><a name="Text"></a><span data-ttu-id="f64e6-197">4. 添加自由格式的文本</span><span class="sxs-lookup"><span data-stu-id="f64e6-197">4. Add Free Form Text</span></span>
 <span data-ttu-id="f64e6-198">文本框包含在每个报表页上都重复的静态文本以及多个数据字段。</span><span class="sxs-lookup"><span data-stu-id="f64e6-198">A text box contains static text that is repeated on each report page as well as data fields.</span></span>

#### <a name="to-add-text-to-the-report"></a><span data-ttu-id="f64e6-199">向报表添加文本</span><span class="sxs-lookup"><span data-stu-id="f64e6-199">To add text to the report</span></span>

1.  <span data-ttu-id="f64e6-200">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="f64e6-200">Click **Design** to return to design view.</span></span>

2.  <span data-ttu-id="f64e6-201">在功能区的 **“插入”** 选项卡上，单击 **“文本框”**，然后将一个文本框拖到该列表的左上角，但放在你以前添加的矩形内。</span><span class="sxs-lookup"><span data-stu-id="f64e6-201">On the **Insert** tab of the ribbon, click **Text Box**, and then drag a text box to the upper left corner of the list, but inside of the rectangle you added previously.</span></span> <span data-ttu-id="f64e6-202">使该文本框大约 3 英寸高，5 英寸宽。</span><span class="sxs-lookup"><span data-stu-id="f64e6-202">Make the text box about 3 inches tall and 5 inches wide.</span></span>

3.  <span data-ttu-id="f64e6-203">将光标置于文本框的上部，然后键入： **Newsletter for** 。</span><span class="sxs-lookup"><span data-stu-id="f64e6-203">Place the cursor in the upper part of the text box, and then type: **Newsletter for** .</span></span>

     <span data-ttu-id="f64e6-204">![添加新闻稿标题文本](../../2014/tutorials/media/tutorial-newsletterfor.png "添加新闻稿标题文本")</span><span class="sxs-lookup"><span data-stu-id="f64e6-204">![Add newsletter heading text](../../2014/tutorials/media/tutorial-newsletterfor.png "Add newsletter heading text")</span></span>

    > [!NOTE]
    >  <span data-ttu-id="f64e6-205">请确保在“for”一词之后包含一个多余的空格。</span><span class="sxs-lookup"><span data-stu-id="f64e6-205">Be sure to include the extra space after the word "for".</span></span> <span data-ttu-id="f64e6-206">该空格用于将文本以及您将在下一步骤中添加的字段分隔开来。</span><span class="sxs-lookup"><span data-stu-id="f64e6-206">The space separates the text and the field that you will add in the next step.</span></span>

4.  <span data-ttu-id="f64e6-207">将 Territory 字段拖到该文本框，然后将其置于您在步骤 3 中键入的文本之后。</span><span class="sxs-lookup"><span data-stu-id="f64e6-207">Drag the Territory field to the text box and place it after the text you typed in step 3.</span></span>

     <span data-ttu-id="f64e6-208">![添加 Territorial 字段](../../2014/tutorials/media/tutorial-addterritorialfield.png "添加 Territorial 字段")</span><span class="sxs-lookup"><span data-stu-id="f64e6-208">![Add Territorial field](../../2014/tutorials/media/tutorial-addterritorialfield.png "Add Territorial field")</span></span>

5.  <span data-ttu-id="f64e6-209">选择所有文本，右键单击，然后单击 **“文本属性”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-209">Select all text, right-click, and then click **Text Properties**.</span></span>

6.  <span data-ttu-id="f64e6-210">单击 **“字体”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f64e6-210">Click the **Font** tab.</span></span>

7.  <span data-ttu-id="f64e6-211">在 **“字体”** 列表中，选择 **“Times New Roman”**；在 **“字号”** 中，选择 **“20 pt”**；在 **“颜色”** 中，选择 **“红色”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-211">In the **Font** list, select **Times New Roman**; in **Size** select **20 pt**, in **Color** select **Red**.</span></span>

     <span data-ttu-id="f64e6-212">![文本属性](../../2014/tutorials/media/tutorial-textpropertieswithnumbers.png "“文本属性”")</span><span class="sxs-lookup"><span data-stu-id="f64e6-212">![Text Properties](../../2014/tutorials/media/tutorial-textpropertieswithnumbers.png "Text Properties")</span></span>

8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

9. <span data-ttu-id="f64e6-213">将光标置于您在步骤 3 中键入的文本之下，然后键入： **Hello** 。</span><span class="sxs-lookup"><span data-stu-id="f64e6-213">Place the cursor below the text you typed in step 3 and type: **Hello** .</span></span>

    > [!NOTE]
    >  <span data-ttu-id="f64e6-214">请确保在“Hello”一词之后包含一个多余的空格。</span><span class="sxs-lookup"><span data-stu-id="f64e6-214">Be sure to include the extra space after the word "Hello".</span></span> <span data-ttu-id="f64e6-215">该空格用于将文本以及您将在下一步骤中添加的字段分隔开来。</span><span class="sxs-lookup"><span data-stu-id="f64e6-215">The space separates the text and the field that you will add in the next step.</span></span>

10. <span data-ttu-id="f64e6-216">将 FullName 字段拖到该文本框，将其置于您在步骤 9 中键入的文本之后，然后键入一个逗号 (,)。</span><span class="sxs-lookup"><span data-stu-id="f64e6-216">Drag the FullName field to the text box and place it after the text you typed in step 9, and then type a comma (,).</span></span>

     <span data-ttu-id="f64e6-217">![添加“全名”字段](../../2014/tutorials/media/tutorial-addfullnamefield.png "添加“全名”字段")</span><span class="sxs-lookup"><span data-stu-id="f64e6-217">![Add Full Name field](../../2014/tutorials/media/tutorial-addfullnamefield.png "Add Full Name field")</span></span>

11. <span data-ttu-id="f64e6-218">选择您在步骤 9 和 10 中添加的文本，右键单击，然后单击 **“文本属性”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-218">Select the text you added in steps 9 and 10, right-click, and then click **Text Properties**.</span></span>

12. <span data-ttu-id="f64e6-219">单击 **“字体”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f64e6-219">Click the **Font** tab.</span></span>

13. <span data-ttu-id="f64e6-220">在 **“字体”** 列表中，选择 **“Times New Roman”**；在 **“字号”** 中，选择 **“16 pt”**；在 **“颜色”** 中，选择 **“黑色”** 。</span><span class="sxs-lookup"><span data-stu-id="f64e6-220">In the **Font** list, select **Times New Roman**; in **Size** select **16 pt**, in **Color** select **Black** color.</span></span>

14. [!INCLUDE[clickOK](../includes/clickok-md.md)]

15. <span data-ttu-id="f64e6-221">将光标置于您在步骤 9 到 13 中添加的文本的下方，然后复制并粘贴以下“难懂的”文本：</span><span class="sxs-lookup"><span data-stu-id="f64e6-221">Place the cursor below the text you added in steps 9 through 13, and then copy and paste the following "greeked" text:</span></span>

    ```
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin sed dolor in ipsum pulvinar egestas. Sed sed lacus at leo ornare ultricies. Vivamus velit risus, euismod nec sodales gravida, gravida in dui. Etiam ullamcorper elit vitae justo fermentum ut ullamcorper augue sodales. Ut placerat, nisl quis feugiat adipiscing, nibh est aliquet est, mollis faucibus mauris lectus quis arcu. In mollis tincidunt lacinia. In vitae erat ut lorem tincidunt luctus. Curabitur et magna nunc, sit amet adipiscing nisi. Nulla rhoncus elementum orci nec tincidunt. Aliquam imperdiet cursus erat vel tincidunt. Donec et neque ac urna rutrum sodales. In id purus et nisl dignissim dapibus. Sed rhoncus metus at felis feugiat eu tempor dolor vehicula. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam faucibus consectetur diam eu pellentesque. 
    Nulla facilisi. Proin ligula enim, porta ut tincidunt id, adipiscing sit amet eros. Ut purus sem, bibendum et vulputate sit amet, facilisis eget magna. Sed aliquam erat non erat eleifend hendrerit. Ut a ligula est, sit amet eleifend enim. Ut et nisl enim, sit amet adipiscing augue. Vivamus eu arcu ac libero posuere elementum. Integer condimentum bibendum venenatis. Integer odio tellus, feugiat in pellentesque semper, interdum nec sem. Sed cursus euismod sem, ut elementum sapien placerat vel. 
    ```

16. <span data-ttu-id="f64e6-222">选择您在步骤 15 中添加的文本，右键单击，然后单击 **“文本属性”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-222">Select the text you added in steps 15, right-click, and then click **Text Properties**.</span></span>

17. <span data-ttu-id="f64e6-223">单击 **“字体”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f64e6-223">Click the **Font** tab.</span></span>

18. <span data-ttu-id="f64e6-224">在 **“字体”** 列表中，选择 **“Arial”**；在 **“字号”** 中，选择 **“10 pt”**；在 **“颜色”** 中，选择 **“黑色”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-224">In the **Font** list, select **Arial**; in **Size** select **10 pt**, in **Color** select **Black**.</span></span>

19. [!INCLUDE[clickOK](../includes/clickok-md.md)]

     <span data-ttu-id="f64e6-225">![添加新闻稿文本](../../2014/tutorials/media/tutorial-newslettertext.png "添加新闻稿文本")</span><span class="sxs-lookup"><span data-stu-id="f64e6-225">![Add newsletter text](../../2014/tutorials/media/tutorial-newslettertext.png "Add newsletter text")</span></span>

20. <span data-ttu-id="f64e6-226">将光标置于您在步骤 15 中粘贴的文本的下方，然后键入： **Congratulations on your total sales of** 。</span><span class="sxs-lookup"><span data-stu-id="f64e6-226">Place the cursor below the text you pasted in step 15, and then type: **Congratulations on your total sales of** .</span></span>

    > [!NOTE]
    >  <span data-ttu-id="f64e6-227">请确保在“of”一词之后包含一个多余的空格。</span><span class="sxs-lookup"><span data-stu-id="f64e6-227">Be sure to include the extra space after the word "of".</span></span> <span data-ttu-id="f64e6-228">该空格用于将文本以及您将在下一步骤中添加的字段分隔开来。</span><span class="sxs-lookup"><span data-stu-id="f64e6-228">The space separates the text and the field that you will add in the next step.</span></span>

21. <span data-ttu-id="f64e6-229">将 Sales 字段拖到该文本框，将其置于您在步骤 20 中键入的文本之后，然后键入一个感叹号 (!)。</span><span class="sxs-lookup"><span data-stu-id="f64e6-229">Drag the Sales field to the text box, place it after the text you typed in step 20, and then type an exclamation mark (!).</span></span>

22. <span data-ttu-id="f64e6-230">突出显示 "销售额" 字段，右键单击该字段，然后单击 "**表达式**"。</span><span class="sxs-lookup"><span data-stu-id="f64e6-230">Highlight the Sales field, right-click the field, and then click **Expression**.</span></span>

23. <span data-ttu-id="f64e6-231">在表达式框中，更改表达式以便包括 Sum 函数，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f64e6-231">In the expression box, change the expression to include the Sum function as follows:</span></span>

    ```
    =Sum(Fields!Sales.value)
    ```

24. [!INCLUDE[clickOK](../includes/clickok-md.md)]

     <span data-ttu-id="f64e6-232">![向 sales 字段添加表达式](../../2014/tutorials/media/tutorial-addexpressiontosalesfield.png "向 sales 字段添加表达式")</span><span class="sxs-lookup"><span data-stu-id="f64e6-232">![Add an expression to sales field](../../2014/tutorials/media/tutorial-addexpressiontosalesfield.png "Add an expression to sales field")</span></span>

25. <span data-ttu-id="f64e6-233">选择您在步骤 20 到 23 中添加的文本，右键单击，然后单击 **“文本属性”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-233">Select the text you added in steps 20 through 23, right-click, and then click **Text Properties**.</span></span>

26. <span data-ttu-id="f64e6-234">单击 **“字体”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f64e6-234">Click the **Font** tab.</span></span>

27. <span data-ttu-id="f64e6-235">在 **“字体”** 列表中，选择 **“Times New Roman”**；在 **“字号”** 中，选择 **“16 pt”**；在 **“颜色”** 中，选择 **“红色”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-235">In the **Font** list, select **Times New Roman**; in **Size** select **16 pt**, in **Color** select **Red**.</span></span>

28. [!INCLUDE[clickOK](../includes/clickok-md.md)]

29. <span data-ttu-id="f64e6-236">选择 `[Sum(Sales)]` ，在功能区的 **“主文件夹”** 选项卡的 **“编号”** 组中，单击 **“货币”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="f64e6-236">Select `[Sum(Sales)]` and on the **Home** tab, in the **Number** group, click the **Currency** button.</span></span>

     <span data-ttu-id="f64e6-237">![添加货币符号](../../2014/tutorials/media/tutorial-addcurrencysymbol.png "添加货币符号")</span><span class="sxs-lookup"><span data-stu-id="f64e6-237">![Add currency symbol](../../2014/tutorials/media/tutorial-addcurrencysymbol.png "Add currency symbol")</span></span>

30. <span data-ttu-id="f64e6-238">右键单击包含“单击以添加标题”文本的文本框，然后单击 **“删除”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-238">Right-click the text box with the "Click to add title" text, and then click **Delete**.</span></span>

31. <span data-ttu-id="f64e6-239">选择列表框，并且使用箭头键将其移到页面的顶部。</span><span class="sxs-lookup"><span data-stu-id="f64e6-239">Select the list box and using the arrow keys, move it to the top of the page.</span></span>

32. <span data-ttu-id="f64e6-240">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="f64e6-240">Click **Run** to preview the report.</span></span>

 <span data-ttu-id="f64e6-241">报表将显示静态文本，并且每个报表页都包括属于某个地区的数据。</span><span class="sxs-lookup"><span data-stu-id="f64e6-241">The report displays static text and each report page includes data that pertains to a territory.</span></span> <span data-ttu-id="f64e6-242">销售额的格式设为货币。</span><span class="sxs-lookup"><span data-stu-id="f64e6-242">Sales are formatted as currency.</span></span>

 <span data-ttu-id="f64e6-243">![新闻稿预览](../../2014/tutorials/media/tutorial-newsletters.png "新闻稿预览")</span><span class="sxs-lookup"><span data-stu-id="f64e6-243">![Preview of Newsletter](../../2014/tutorials/media/tutorial-newsletters.png "Preview of Newsletter")</span></span>

##  <a name="5-add-a-table-to-show-sales-details"></a><a name="Table"></a><span data-ttu-id="f64e6-244">5. 添加一个表以显示销售详细信息</span><span class="sxs-lookup"><span data-stu-id="f64e6-244">5. Add a Table to Show Sales Details</span></span>
 <span data-ttu-id="f64e6-245">使用新建表和矩阵向导可以将表添加到自由格式的报表。</span><span class="sxs-lookup"><span data-stu-id="f64e6-245">Use the New Table and Matrix Wizard to add a table to the free form report.</span></span> <span data-ttu-id="f64e6-246">完成向导后，您将手动添加一个合计行。</span><span class="sxs-lookup"><span data-stu-id="f64e6-246">After you complete the wizard, you will manually add a row for totals.</span></span>

#### <a name="to-add-a-table"></a><span data-ttu-id="f64e6-247">添加表</span><span class="sxs-lookup"><span data-stu-id="f64e6-247">To add a table</span></span>

1.  <span data-ttu-id="f64e6-248">在功能区的 **“插入”** 选项卡的 **“数据区域”** 区域中，单击 **“表”**，然后单击 **“表向导”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-248">On the **Insert** tab of the ribbon, in the **Data Regions** area, click **Table**, and then click **Table Wizard**.</span></span>

2.  <span data-ttu-id="f64e6-249">在“选择数据集”页上，单击 **ListDataset**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-249">On the Choose a dataset page, click **ListDataset**.</span></span>

3.  <span data-ttu-id="f64e6-250">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="f64e6-250">Click **Next**.</span></span>

4.  <span data-ttu-id="f64e6-251">在“排列字段”页上，将“Product”字段从“可用字段”拖到“值”中\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f64e6-251">On the **Arrange fields** page, drag the Product field from **Available fields** to **Values.**</span></span>

5.  <span data-ttu-id="f64e6-252">对于 SalesDate、Quantity 和 Sales，重复执行步骤 4。</span><span class="sxs-lookup"><span data-stu-id="f64e6-252">Repeat step 4, for SalesDate, Quantity, and Sales.</span></span> <span data-ttu-id="f64e6-253">将 SalesDate 放置于 Product 之下，将 Quantity 放置于 SalesDate 之下，并且将 Sales 放置于 SalesDate 之下。</span><span class="sxs-lookup"><span data-stu-id="f64e6-253">Place SalesDate below Product, Quantity below SalesDate, and Sales below SalesDate.</span></span>

6.  <span data-ttu-id="f64e6-254">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="f64e6-254">Click **Next**.</span></span>

7.  <span data-ttu-id="f64e6-255">在 **“选择布局”** 页上，查看表的布局。</span><span class="sxs-lookup"><span data-stu-id="f64e6-255">On the **Choose the layout** page, view the layout of the table.</span></span>

     <span data-ttu-id="f64e6-256">该表非常简单。</span><span class="sxs-lookup"><span data-stu-id="f64e6-256">The table is very simple.</span></span> <span data-ttu-id="f64e6-257">它由五列构成，没有行组或列组。</span><span class="sxs-lookup"><span data-stu-id="f64e6-257">It consists of five columns and has no row or column groups.</span></span> <span data-ttu-id="f64e6-258">因为它不具有组，所以与组相关的布局选项不可用。</span><span class="sxs-lookup"><span data-stu-id="f64e6-258">Because it has no groups, the layout options related to groups, are not available.</span></span> <span data-ttu-id="f64e6-259">您将手动更新该表以便包括本教程后面部分中的总计。</span><span class="sxs-lookup"><span data-stu-id="f64e6-259">You will manually update the table to include a total later in the tutorial.</span></span>

8.  <span data-ttu-id="f64e6-260">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="f64e6-260">Click **Next**.</span></span>

9. <span data-ttu-id="f64e6-261">在 **“选择样式”** 页的 **“样式”** 窗格中，选择 **“石板”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-261">On the **Choose a Style** page, in the **Styles** pane, select **Slate**.</span></span>

10. <span data-ttu-id="f64e6-262">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="f64e6-262">Click **Finish**.</span></span>

11. <span data-ttu-id="f64e6-263">将该表拖到您在第 4 课中添加的文本框之下。</span><span class="sxs-lookup"><span data-stu-id="f64e6-263">Drag the table to below the text box that you added in lesson 4.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="f64e6-264">请确保该表位于列表内。</span><span class="sxs-lookup"><span data-stu-id="f64e6-264">Make sure the table is inside the list.</span></span>

12. <span data-ttu-id="f64e6-265">确认表已选，然后在“行组”窗格中，右键单击“详细信息”，指向 **“添加总计”**，然后单击 **“之后”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-265">Confirmed that the table is selected, then in the Row Group pane right-click Details, point to **Add Total**, and then click **After**.</span></span>

     <span data-ttu-id="f64e6-266">![添加报表总数](../../2014/tutorials/media/tutorial-addtotal.png "添加报表总数")</span><span class="sxs-lookup"><span data-stu-id="f64e6-266">![Add report total](../../2014/tutorials/media/tutorial-addtotal.png "Add report total")</span></span>

13. <span data-ttu-id="f64e6-267">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="f64e6-267">Click **Run** to preview the report.</span></span>

 <span data-ttu-id="f64e6-268">该报表将显示具有销售详细信息和总计的一个表。</span><span class="sxs-lookup"><span data-stu-id="f64e6-268">The report displays a table with sales details and totals.</span></span>

 <span data-ttu-id="f64e6-269">![报表中的总销售额](../../2014/tutorials/media/tutorial-reportsalestotals.png "报表中的总销售额")</span><span class="sxs-lookup"><span data-stu-id="f64e6-269">![Sales totals in report](../../2014/tutorials/media/tutorial-reportsalestotals.png "Sales totals in report")</span></span>

##  <a name="6-format-data"></a><a name="Format"></a><span data-ttu-id="f64e6-270">6. 设置数据格式</span><span class="sxs-lookup"><span data-stu-id="f64e6-270">6. Format Data</span></span>
 <span data-ttu-id="f64e6-271">将数字数据的格式设为货币，将日期格式设为仅限天和时间。</span><span class="sxs-lookup"><span data-stu-id="f64e6-271">Format numeric data as currency and dates as day and time only.</span></span>

#### <a name="to-format-fields-table"></a><span data-ttu-id="f64e6-272">设置字段表的格式</span><span class="sxs-lookup"><span data-stu-id="f64e6-272">To format fields table</span></span>

1.  <span data-ttu-id="f64e6-273">单击 "**设计**" 切换到 "设计" 视图。</span><span class="sxs-lookup"><span data-stu-id="f64e6-273">Click **Design** to switch to design view.</span></span>

2.  <span data-ttu-id="f64e6-274">单击包含 `[Sum(SalesSales)]` 的表单元，然后在 **“主文件夹”** 选项卡上的 **“数字”** 组中，单击 **“货币”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="f64e6-274">Click the table cells that contain `[Sum(SalesSales)]` and on the **Home** tab, in the **Number** group, click the **Currency** button.</span></span>

     <span data-ttu-id="f64e6-275">![向总销售额添加货币符号](../../2014/tutorials/media/tutorial-sumsales-currencysymbol.png "向总销售额添加货币符号")</span><span class="sxs-lookup"><span data-stu-id="f64e6-275">![Add currency symbol to sum sales](../../2014/tutorials/media/tutorial-sumsales-currencysymbol.png "Add currency symbol to sum sales")</span></span>

3.  <span data-ttu-id="f64e6-276">单击包含 `[SalesDate]` 的单元，然后在 **“数字”** 组上，从下拉列表中选择 **“日期”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-276">Click the cell that contains `[SalesDate]` and in the **Number** group, from the drop-down list, select **Date**.</span></span>

4.  <span data-ttu-id="f64e6-277">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="f64e6-277">Click **Run** to preview the report.</span></span>

 <span data-ttu-id="f64e6-278">报表现在将显示设置了格式的数据并且更易于阅读。</span><span class="sxs-lookup"><span data-stu-id="f64e6-278">The report now displays formatted data and is easier to read.</span></span>

 <span data-ttu-id="f64e6-279">![报表中的格式化总销售额](../../2014/tutorials/media/tutorial-reportsalestotals-formatted.png "报表中的格式化总销售额")</span><span class="sxs-lookup"><span data-stu-id="f64e6-279">![Format sales totals in report](../../2014/tutorials/media/tutorial-reportsalestotals-formatted.png "Format sales totals in report")</span></span>

##  <a name="7-save-the-report"></a><a name="Save"></a><span data-ttu-id="f64e6-280">7. 保存报表</span><span class="sxs-lookup"><span data-stu-id="f64e6-280">7. Save the Report</span></span>
 <span data-ttu-id="f64e6-281">您可以将报表保存到报表服务器、SharePoint 库或本地计算机。</span><span class="sxs-lookup"><span data-stu-id="f64e6-281">You can save reports to a report server, SharePoint library, or your computer.</span></span> <span data-ttu-id="f64e6-282">你还可以运行报表并从 \*\*\*\* “导出”菜单选择格式，将报表以各种格式导出（如 Word 和 PDF）。</span><span class="sxs-lookup"><span data-stu-id="f64e6-282">You can also export the report to a variety of formats such as Word and PDF, by running the report and selecting the format from the **Export** menu.</span></span>

 <span data-ttu-id="f64e6-283">在本教程中，将报表保存到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="f64e6-283">In this tutorial, save the report to a report server.</span></span> <span data-ttu-id="f64e6-284">如果您没有对报表服务器的访问权限，则可以保存到您的计算机。</span><span class="sxs-lookup"><span data-stu-id="f64e6-284">If you do not have access to a report server, save the report to your computer.</span></span>

#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="f64e6-285">将报表保存到报表服务器</span><span class="sxs-lookup"><span data-stu-id="f64e6-285">To save the report on a report server</span></span>

1.  <span data-ttu-id="f64e6-286">从 **“报表生成器”** 按钮，单击 **“另存为”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-286">From the **Report Builder** button, click **Save As**.</span></span>

2.  <span data-ttu-id="f64e6-287">单击 **“最近使用的站点和服务器”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-287">Click **Recent Sites and Servers**.</span></span>

3.  <span data-ttu-id="f64e6-288">选择或键入您拥有保存报表权限的报表服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="f64e6-288">Select or type the name of the report server where you have permission to save reports.</span></span>

     <span data-ttu-id="f64e6-289">此时将显示“正在连接到报表服务器”消息。</span><span class="sxs-lookup"><span data-stu-id="f64e6-289">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="f64e6-290">当连接完成时，您将看到报表服务器管理员指定为报表默认位置的报表文件夹的内容。</span><span class="sxs-lookup"><span data-stu-id="f64e6-290">When the connection is complete, you see the contents of the report folder that the report server administrator specified as the default location for reports.</span></span>

4.  <span data-ttu-id="f64e6-291">在中 `Name` ，用**SalesInformationByTerritory**替换默认名称。</span><span class="sxs-lookup"><span data-stu-id="f64e6-291">In `Name`, replace the default name with **SalesInformationByTerritory**.</span></span>

5.  <span data-ttu-id="f64e6-292">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="f64e6-292">Click **Save**.</span></span>

 <span data-ttu-id="f64e6-293">报表即已保存至报表服务器。</span><span class="sxs-lookup"><span data-stu-id="f64e6-293">The report is saved to the report server.</span></span> <span data-ttu-id="f64e6-294">您连接的报表服务器的名称将显示在窗口底部的状态栏中。</span><span class="sxs-lookup"><span data-stu-id="f64e6-294">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>

#### <a name="to-save-the-report-on-your-computer"></a><span data-ttu-id="f64e6-295">将报表保存到计算机上</span><span class="sxs-lookup"><span data-stu-id="f64e6-295">To save the report on your computer</span></span>

1.  <span data-ttu-id="f64e6-296">从 **“报表生成器”** 按钮，单击 **“另存为”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-296">From the **Report Builder** button, click **Save As**.</span></span>

2.  <span data-ttu-id="f64e6-297">单击 **“桌面”**、 **“我的文档”** 或 **“我的电脑”**，然后浏览到要将报表保存到的文件夹。</span><span class="sxs-lookup"><span data-stu-id="f64e6-297">Click **Desktop**, **My Documents**, or **My computer**, and then browse to the folder where you want to save the report.</span></span>

3.  <span data-ttu-id="f64e6-298">在中 `Name` ，用**SalesInformationByTerritory**替换默认名称。</span><span class="sxs-lookup"><span data-stu-id="f64e6-298">In `Name`, replace the default name with **SalesInformationByTerritory**.</span></span>

4.  <span data-ttu-id="f64e6-299">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="f64e6-299">Click **Save**.</span></span>

##  <a name="8-optional-add-a-line-to-separate-areas-of-the-report"></a><a name="Line"></a><span data-ttu-id="f64e6-300">8. (可选) 添加线条以便分隔报表区域</span><span class="sxs-lookup"><span data-stu-id="f64e6-300">8. (Optional) Add a Line to Separate Areas of the Report</span></span>
 <span data-ttu-id="f64e6-301">添加线条可以分隔报表的可编辑区域和详细信息区域。</span><span class="sxs-lookup"><span data-stu-id="f64e6-301">Add a line to separate the editorial and details areas of the report.</span></span>

#### <a name="to-add-a-line"></a><span data-ttu-id="f64e6-302">添加线条</span><span class="sxs-lookup"><span data-stu-id="f64e6-302">To add a line</span></span>

1.  <span data-ttu-id="f64e6-303">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="f64e6-303">Click **Design** to return to design view.</span></span>

2.  <span data-ttu-id="f64e6-304">在功能区的 **“插入”** 选项卡的 **“报表项”** 区域中，单击 **“线条”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-304">On the **Insert** tab of the ribbon, in the **Report Items** area, click **Line.**</span></span>

3.  <span data-ttu-id="f64e6-305">将一个线条拖到您在第 4 课中添加的自由格式的文本框之下。</span><span class="sxs-lookup"><span data-stu-id="f64e6-305">Draw a line below the free form text box you added in lesson 4.</span></span>

4.  <span data-ttu-id="f64e6-306">单击该线条。</span><span class="sxs-lookup"><span data-stu-id="f64e6-306">Click the line.</span></span>

5.  <span data-ttu-id="f64e6-307">单击 **“主文件夹”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f64e6-307">Click the **Home** tab.</span></span>

6.  <span data-ttu-id="f64e6-308">在 **“边框”** 区域中，对于宽度选择 **4 1/2** pt，对于颜色选择 **“红色”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-308">In the **Border** area, for width select **4 1/2** pt and for color, for color select **Red**.</span></span>

     <span data-ttu-id="f64e6-309">![向报表添加线条](../../2014/tutorials/media/tutorial-reportwithline.png "向报表添加线条")</span><span class="sxs-lookup"><span data-stu-id="f64e6-309">![Add line to report](../../2014/tutorials/media/tutorial-reportwithline.png "Add line to report")</span></span>

##  <a name="9-optional-add-summary-data-visualization"></a><a name="Visualization"></a><span data-ttu-id="f64e6-310">9. (可选) 添加汇总数据可视化</span><span class="sxs-lookup"><span data-stu-id="f64e6-310">9. (Optional) Add Summary Data Visualization</span></span>
 <span data-ttu-id="f64e6-311">矩形有助于控制报表的呈现方式。</span><span class="sxs-lookup"><span data-stu-id="f64e6-311">Rectangles help you control how the report renders.</span></span> <span data-ttu-id="f64e6-312">将饼图和柱形图放置于矩形内，可以确保报表以您所需的方式呈现。</span><span class="sxs-lookup"><span data-stu-id="f64e6-312">Place a pie and column chart inside a rectangle to ensure that the report renders the way you want.</span></span>

#### <a name="to-add-a-rectangle"></a><span data-ttu-id="f64e6-313">添加矩形</span><span class="sxs-lookup"><span data-stu-id="f64e6-313">To add a rectangle</span></span>

1.  <span data-ttu-id="f64e6-314">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="f64e6-314">Click **Design** to return to design view.</span></span>

2.  <span data-ttu-id="f64e6-315">在功能区的 **“插入”** 选项卡的 **“报表项”** 区域中，单击 **“矩形”**，然后将该矩形拖到列表内表的右侧。</span><span class="sxs-lookup"><span data-stu-id="f64e6-315">On the **Insert** tab of the ribbon, in the **Report Items** area click **Rectangle**, and then drag the rectangle inside the list, to the right of the table.</span></span> <span data-ttu-id="f64e6-316">使该矩形 2 英寸宽，4 英寸高。</span><span class="sxs-lookup"><span data-stu-id="f64e6-316">Make the rectangle 2 inches wide and 4 inches tall.</span></span>

3.  <span data-ttu-id="f64e6-317">将矩形的顶部和表的顶部对齐。</span><span class="sxs-lookup"><span data-stu-id="f64e6-317">Align the tops of the rectangle and the table.</span></span>

#### <a name="to-add-a-pie-chart"></a><span data-ttu-id="f64e6-318">添加饼图</span><span class="sxs-lookup"><span data-stu-id="f64e6-318">To add a pie chart</span></span>

1.  <span data-ttu-id="f64e6-319">在功能区 **“插入”** 选项卡上的 **“数据可视化”** 区域中，单击 **“图表”** ，然后单击 **“图表向导”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-319">On the **Insert** tab of the ribbon, in the **Data Visualizations** area, click **Chart,** and then click **Chart Wizard**.</span></span>

2.  <span data-ttu-id="f64e6-320">在 “选择数据集” 页上，单击 **ListDataset**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-320">On the Choose a dataset page, click **ListDataset**, and then click **Next**.</span></span>

3.  <span data-ttu-id="f64e6-321">单击 **“饼图”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-321">Click **Pie**, and then click **Next**.</span></span>

4.  <span data-ttu-id="f64e6-322">在“排列图表字段”页上，将“Product”拖到“类别”中\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f64e6-322">On the arrange chart fields page, drag Product to **Categories**.</span></span>

5.  <span data-ttu-id="f64e6-323">将数量拖到 "**值**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="f64e6-323">Drag Quantity to **Values**, and then click **Next**.</span></span>

6.  <span data-ttu-id="f64e6-324">在 **“选择样式”** 页的 **“样式”** 窗格中，选择 **“石板”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-324">On the **Choose a Style** page, in the **Styles** pane, select **Slate**.</span></span>

7.  <span data-ttu-id="f64e6-325">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="f64e6-325">Click **Finish**.</span></span>

8.  <span data-ttu-id="f64e6-326">调整在报表的左上角中出现的图表大小，使其为 1 1/2 英寸高，2 英寸宽。</span><span class="sxs-lookup"><span data-stu-id="f64e6-326">Resize the chart that appears in the upper left corner of the report, to be 1 1/2 inches tall and 2 inches wide.</span></span>

9. <span data-ttu-id="f64e6-327">将图表拖至该矩形内。</span><span class="sxs-lookup"><span data-stu-id="f64e6-327">Drag the chart inside the rectangle.</span></span>

     <span data-ttu-id="f64e6-328">![添加饼图](../../2014/tutorials/media/tutorial-addpiechart.png "添加饼图")</span><span class="sxs-lookup"><span data-stu-id="f64e6-328">![Add pie chart](../../2014/tutorials/media/tutorial-addpiechart.png "Add pie chart")</span></span>

10. <span data-ttu-id="f64e6-329">右键单击图表标题，然后单击 **“标题属性”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-329">Right-click the chart title, and then click **Title Properties**.</span></span>

11. <span data-ttu-id="f64e6-330">在 **“图表标题属性”** 对话框的“标题”文本中，键入： **Product Quantities Sold**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-330">In the **Chart Title Properties** dialog box, in Title text, type: **Product Quantities Sold**.</span></span>

12. <span data-ttu-id="f64e6-331">单击 **“字体”** 选项卡，然后在 **“大小”** 列表中，单击 **10pt**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-331">Click the **Font** tab, and in the **Size** list, click **10pt**.</span></span>

13. [!INCLUDE[clickOK](../includes/clickok-md.md)]

#### <a name="to-add-a-column-chart"></a><span data-ttu-id="f64e6-332">添加柱形图</span><span class="sxs-lookup"><span data-stu-id="f64e6-332">To add a column chart</span></span>

1.  <span data-ttu-id="f64e6-333">在功能区 **“插入”** 选项卡上的 **“数据可视化”** 区域中，单击 **“图表”** ，然后单击 **“图表向导”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-333">On the **Insert** tab of the ribbon, in the **Data Visualizations** area, click **Chart,** and then click **Chart Wizard**.</span></span>

2.  <span data-ttu-id="f64e6-334">在 **“选择数据集”** 页上，单击 **ListDataset**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-334">On the **Choose a dataset** page, click **ListDataset**, and then click **Next**.</span></span>

3.  <span data-ttu-id="f64e6-335">单击 **“柱形”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-335">Click **Column**, and then click **Next**.</span></span>

4.  <span data-ttu-id="f64e6-336">在 "排列图表字段" 页上，将 "Product" 字段拖到 "**类别**"。</span><span class="sxs-lookup"><span data-stu-id="f64e6-336">On the arrange chart fields page, drag the Product field to **Categories**.</span></span>

5.  <span data-ttu-id="f64e6-337">将“Sales”拖到“值”中，然后单击“下一步”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f64e6-337">Drag Sales to **Values,** and then click **Next**.</span></span>

     <span data-ttu-id="f64e6-338">“值”显示在垂直轴上。</span><span class="sxs-lookup"><span data-stu-id="f64e6-338">Values display on the vertical axis.</span></span>

6.  <span data-ttu-id="f64e6-339">在 **“选择样式”** 页的 **“样式”** 窗格中，选择 **“石板”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-339">On the **Choose a Style** page, in the **Styles** pane, select **Slate**.</span></span>

7.  <span data-ttu-id="f64e6-340">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="f64e6-340">Click **Finish**.</span></span>

     <span data-ttu-id="f64e6-341">一个柱形图将添加到报表的左上角。</span><span class="sxs-lookup"><span data-stu-id="f64e6-341">A column chart is added to the upper left corner of the report.</span></span>

8.  <span data-ttu-id="f64e6-342">调整图表的大小，使其 2 英寸宽，2 英寸高。</span><span class="sxs-lookup"><span data-stu-id="f64e6-342">Resize the chart to be 2 inches wide and 2 inches tall.</span></span>

9. <span data-ttu-id="f64e6-343">将图表拖至该矩形内的饼图之下。</span><span class="sxs-lookup"><span data-stu-id="f64e6-343">Drag the chart inside the rectangle, below the pie chart.</span></span>

     <span data-ttu-id="f64e6-344">![添加柱形图](../../2014/tutorials/media/tutorial-addcolumnchart.png "添加柱形图")</span><span class="sxs-lookup"><span data-stu-id="f64e6-344">![Add column chart](../../2014/tutorials/media/tutorial-addcolumnchart.png "Add column chart")</span></span>

10. <span data-ttu-id="f64e6-345">右键单击图表标题，然后单击 "**标题属性**"。</span><span class="sxs-lookup"><span data-stu-id="f64e6-345">Right-click the chart title and then click **Title Properties**.</span></span>

11. <span data-ttu-id="f64e6-346">在 **“图表标题属性”** 对话框的“标题”文本中，键入： **Product Sales**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-346">In the **Chart Title Properties** dialog box, in Title text, type: **Product Sales**.</span></span>

12. <span data-ttu-id="f64e6-347">单击 **“字体”** 选项卡，然后在 **“大小”** 列表中，单击 **10pt**，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-347">Click the **Font** tab, and in the **Size** list click **10pt**, and then click **OK**.</span></span>

13. <span data-ttu-id="f64e6-348">在柱形图中，右键单击垂直轴，然后取消选中 **“显示轴标题”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-348">In the column chart, right click the vertical axis, and then deselect **Show Axis Title**.</span></span>

14. <span data-ttu-id="f64e6-349">对于水平轴，重复执行步骤 13。</span><span class="sxs-lookup"><span data-stu-id="f64e6-349">Repeat step 13 for the horizontal axis.</span></span>

15. <span data-ttu-id="f64e6-350">右键单击图例，然后单击 **“删除图例”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-350">Right click the legend, and then click **Delete Legend**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="f64e6-351">删除轴标题和图例将在图表为较小大小时更容易阅读。</span><span class="sxs-lookup"><span data-stu-id="f64e6-351">Removing axis titles and the legend makes the chart more readable when it is a small size.</span></span>

 <span data-ttu-id="f64e6-352">![更改图表标题并删除轴标题](../../2014/tutorials/media/tutorial-columnchart-newtitle-noaxistitle.png "更改图表标题并删除轴标题")</span><span class="sxs-lookup"><span data-stu-id="f64e6-352">![Change chart titles and remove axis title](../../2014/tutorials/media/tutorial-columnchart-newtitle-noaxistitle.png "Change chart titles and remove axis title")</span></span>

#### <a name="to-verify-the-charts-are-inside-the-rectangle"></a><span data-ttu-id="f64e6-353">确认图表位于矩形内</span><span class="sxs-lookup"><span data-stu-id="f64e6-353">To verify the charts are inside the rectangle</span></span>

1.  <span data-ttu-id="f64e6-354">单击你在本课程前面部分添加的矩形。</span><span class="sxs-lookup"><span data-stu-id="f64e6-354">Click the rectangle you added earlier in this lesson.</span></span>

     <span data-ttu-id="f64e6-355">在“属性”窗格中，`Name` 属性显示矩形的名称。</span><span class="sxs-lookup"><span data-stu-id="f64e6-355">In the Properties pane, the `Name` property displays the name of the rectangle.</span></span>

     <span data-ttu-id="f64e6-356">![矩形名称](../../2014/tutorials/media/tutorial-rectanglename.png "矩形名称")</span><span class="sxs-lookup"><span data-stu-id="f64e6-356">![Name of rectangle](../../2014/tutorials/media/tutorial-rectanglename.png "Name of rectangle")</span></span>

2.  <span data-ttu-id="f64e6-357">单击饼图。</span><span class="sxs-lookup"><span data-stu-id="f64e6-357">Click the pie chart.</span></span>

3.  <span data-ttu-id="f64e6-358">在 "**属性**" 窗格中，确认 `Parent` 属性包含矩形的名称。</span><span class="sxs-lookup"><span data-stu-id="f64e6-358">In the **Properties** pane, verify that the `Parent` property contains the name of the rectangle.</span></span>

     <span data-ttu-id="f64e6-359">![饼图父属性](../../2014/tutorials/media/tutorial-piechart-parentproperty.png "饼图父属性")</span><span class="sxs-lookup"><span data-stu-id="f64e6-359">![Parent property for pie chart](../../2014/tutorials/media/tutorial-piechart-parentproperty.png "Parent property for pie chart")</span></span>

4.  <span data-ttu-id="f64e6-360">单击柱形图，重复执行步骤 2 和 3。</span><span class="sxs-lookup"><span data-stu-id="f64e6-360">Click the column chart and repeat steps 2 and 3.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="f64e6-361">如果这些图表不位于矩形内，则呈现的报表不会一起显示这些图表。</span><span class="sxs-lookup"><span data-stu-id="f64e6-361">If the charts are not inside the rectangle, the rendered report does not display the charts together.</span></span>

#### <a name="to-make-the-charts-the-same-size"></a><span data-ttu-id="f64e6-362">使图表具有相同大小</span><span class="sxs-lookup"><span data-stu-id="f64e6-362">To make the charts the same size</span></span>

1.  <span data-ttu-id="f64e6-363">单击饼图，按下 Ctrl 键，然后单击柱形图。</span><span class="sxs-lookup"><span data-stu-id="f64e6-363">Click the pie chart, press the Ctrl key, and then click the column chart.</span></span>

2.  <span data-ttu-id="f64e6-364">选择这两个图表，右键单击，指向 **“布局”**，然后单击 **“使宽度相同”**。</span><span class="sxs-lookup"><span data-stu-id="f64e6-364">With both charts selected, right-click, point to **Layout**, and then click **Make Same Width**.</span></span>

     <span data-ttu-id="f64e6-365">![使图表宽度相同](../../2014/tutorials/media/tutorial-makechartssamewidth.png "使图表宽度相同")</span><span class="sxs-lookup"><span data-stu-id="f64e6-365">![Make chart widths the same](../../2014/tutorials/media/tutorial-makechartssamewidth.png "Make chart widths the same")</span></span>

    > [!NOTE]
    >  <span data-ttu-id="f64e6-366">你首先单击的项决定所有选定项的宽度。</span><span class="sxs-lookup"><span data-stu-id="f64e6-366">The item you click first determines the width of all the selected items.</span></span>

3.  <span data-ttu-id="f64e6-367">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="f64e6-367">Click **Run** to preview the report.</span></span>

 <span data-ttu-id="f64e6-368">报表现在将在饼图和柱形图中显示汇总销售数据。</span><span class="sxs-lookup"><span data-stu-id="f64e6-368">The report now displays summary sales data in pie and column charts.</span></span>

 <span data-ttu-id="f64e6-369">![SSRS 教程，自由格式报告](../../2014/tutorials/media/tutorial-reportfinal.png "SSRS 教程，自由格式报告")</span><span class="sxs-lookup"><span data-stu-id="f64e6-369">![SSRS tutorial, free form report](../../2014/tutorials/media/tutorial-reportfinal.png "SSRS tutorial, free form report")</span></span>

## <a name="more-information"></a><span data-ttu-id="f64e6-370">更多信息</span><span class="sxs-lookup"><span data-stu-id="f64e6-370">More Information</span></span>
 <span data-ttu-id="f64e6-371">有关列表的详细信息，请参阅[表、矩阵和列表 &#40;报表生成器和 ssrs&#41;](report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)，[列表 &#40;报表生成器和 ssrs&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)、&#40;和 ssrs 报表生成器中的[tablix 数据区域区域](report-design/tablix-data-region-areas-report-builder-and-ssrs.md)&#41;和[tablix 数据区域单元格、行和列 &#40;报表生成器&#41; 和 SSRS](report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f64e6-371">For more information about lists, see [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](report-design/tables-matrices-and-lists-report-builder-and-ssrs.md), [Lists &#40;Report Builder and SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md), [Tablix Data Region Areas &#40;Report Builder and SSRS&#41;](report-design/tablix-data-region-areas-report-builder-and-ssrs.md), and [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).</span></span>

 <span data-ttu-id="f64e6-372">有关查询设计器的详细信息，请参阅[查询设计器（报表生成器）](../../2014/reporting-services/query-designers-report-builder.md)和[基于文本的查询设计器用户界面（报表生成器）](report-data/text-based-query-designer-user-interface-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="f64e6-372">For more information about query designers, see [Query Designers &#40;Report Builder&#41;](../../2014/reporting-services/query-designers-report-builder.md) and [Text-based Query Designer User Interface &#40;Report Builder&#41;](report-data/text-based-query-designer-user-interface-report-builder.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f64e6-373">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f64e6-373">See Also</span></span>
 <span data-ttu-id="f64e6-374">[SQL Server 2014 中](report-builder/report-builder-in-sql-server-2016.md)[报表生成器&#41;报表生成器教程 &#40;](report-builder-tutorials.md)</span><span class="sxs-lookup"><span data-stu-id="f64e6-374">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) [Report Builder in SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)</span></span>


