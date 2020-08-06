---
title: 教程：创建矩阵报表（报表生成器）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9ee19c2e-2a8c-4bb0-9274-04a5812c2e96
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3df32098d9e6400931ba2a88b2ffd22d6e015a62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692219"
---
# <a name="tutorial-creating-a-matrix-report-report-builder"></a><span data-ttu-id="b9055-102">教程：创建矩阵报表（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="b9055-102">Tutorial: Creating a Matrix Report (Report Builder)</span></span>
  <span data-ttu-id="b9055-103">本教程教您如何基于示例销售数据创建基本矩阵报表。</span><span class="sxs-lookup"><span data-stu-id="b9055-103">This tutorial teaches you how to create a basic matrix report based on sample sales data.</span></span> <span data-ttu-id="b9055-104">该矩阵具有嵌套行组和列组，以及相邻列组。</span><span class="sxs-lookup"><span data-stu-id="b9055-104">The matrix has nested row and column groups and an adjacent column group.</span></span> <span data-ttu-id="b9055-105">您将学习如何设置列的格式以及旋转文本。</span><span class="sxs-lookup"><span data-stu-id="b9055-105">You will also learn how to format columns and rotate text.</span></span> <span data-ttu-id="b9055-106">下图显示与您将创建的报表类似的报表。</span><span class="sxs-lookup"><span data-stu-id="b9055-106">The following illustration shows a report similar to the one you will create.</span></span>  
  
 <span data-ttu-id="b9055-107">![rs_CreateMatixReportTutorial](../../2014/tutorials/media/rs-creatematixreporttutorial.gif "rs_CreateMatixReportTutorial")</span><span class="sxs-lookup"><span data-stu-id="b9055-107">![rs_CreateMatixReportTutorial](../../2014/tutorials/media/rs-creatematixreporttutorial.gif "rs_CreateMatixReportTutorial")</span></span>  
  
 <span data-ttu-id="b9055-108">您在本教程中将创建的报表的增强版本可用作示例 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 报表生成器报表。</span><span class="sxs-lookup"><span data-stu-id="b9055-108">An enhanced version of the report you will create in this tutorial is available as a sample [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Report Builder report.</span></span> <span data-ttu-id="b9055-109">有关下载此示例报表和其他内容的详细信息，请参阅[报表生成器示例报表](https://go.microsoft.com/fwlink/?LinkId=184851)。</span><span class="sxs-lookup"><span data-stu-id="b9055-109">For more information about downloading this sample report and others, see [Report Builder sample reports](https://go.microsoft.com/fwlink/?LinkId=184851).</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="b9055-110">你将学习的内容</span><span class="sxs-lookup"><span data-stu-id="b9055-110">What You Will Learn</span></span>  
 <span data-ttu-id="b9055-111">在本教程中，您将学习如何执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="b9055-111">In this tutorial, you will learn how to:</span></span>  
  
1.  [<span data-ttu-id="b9055-112">使用新的表或矩阵向导创建矩阵报表和数据集</span><span class="sxs-lookup"><span data-stu-id="b9055-112">Create a Matrix Report and Dataset from the New Table or Matrix Wizard</span></span>](#CreateMatrix)  
  
2.  [<span data-ttu-id="b9055-113">使用新的表或矩阵向导组织数据并选择布局和样式</span><span class="sxs-lookup"><span data-stu-id="b9055-113">Organize Data and Choose Layout and Style from the New Table or Matrix Wizard</span></span>](#Groups)  
  
3.  [<span data-ttu-id="b9055-114">设置数据格式</span><span class="sxs-lookup"><span data-stu-id="b9055-114">Format Data</span></span>](#FormatData)  
  
4.  [<span data-ttu-id="b9055-115">添加相邻列组</span><span class="sxs-lookup"><span data-stu-id="b9055-115">Add Adjacent Column Group</span></span>](#AdjacentGroup)  
  
5.  [<span data-ttu-id="b9055-116">更改列宽</span><span class="sxs-lookup"><span data-stu-id="b9055-116">Change Column Widths</span></span>](#Width)  
  
6.  [<span data-ttu-id="b9055-117">合并矩阵单元</span><span class="sxs-lookup"><span data-stu-id="b9055-117">Merge Matrix Cells</span></span>](#MergeCells)  
  
7.  [<span data-ttu-id="b9055-118">添加报表表头和报表标题</span><span class="sxs-lookup"><span data-stu-id="b9055-118">Add a Report Header and Report Title</span></span>](#HeaderTitle)  
  
8.  [<span data-ttu-id="b9055-119">保存报表</span><span class="sxs-lookup"><span data-stu-id="b9055-119">Save the Report</span></span>](#Save)  
  
### <a name="other-optional-step"></a><span data-ttu-id="b9055-120">其他可选步骤</span><span class="sxs-lookup"><span data-stu-id="b9055-120">Other Optional Step</span></span>  
  
1.  [<span data-ttu-id="b9055-121">旋转文本框 270 度</span><span class="sxs-lookup"><span data-stu-id="b9055-121">Rotate Text Box 270 Degrees</span></span>](#RotateTextBox)  
  
 <span data-ttu-id="b9055-122">完成本教程的预计学时：20 分钟。</span><span class="sxs-lookup"><span data-stu-id="b9055-122">Estimated time to complete this tutorial: 20 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9055-123">要求</span><span class="sxs-lookup"><span data-stu-id="b9055-123">Requirements</span></span>  
 <span data-ttu-id="b9055-124">有关要求的详细信息，请参阅[教程先决条件（报表生成器）](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="b9055-124">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-matrix-report-and-dataset-from-the-new-table-or-matrix-wizard"></a><a name="CreateMatrix"></a><span data-ttu-id="b9055-125">1. 使用新建表或矩阵向导创建矩阵报表和数据集</span><span class="sxs-lookup"><span data-stu-id="b9055-125">1. Create a Matrix Report and Dataset from the New Table or Matrix Wizard</span></span>  
 <span data-ttu-id="b9055-126">从报表生成器中的 "**入门**" 对话框中，选择共享数据源，创建嵌入数据集，然后在矩阵中显示数据。</span><span class="sxs-lookup"><span data-stu-id="b9055-126">From the **Getting Started** dialog box in Report Builder, choose a shared data source, create an embedded dataset, and then display the data in a matrix.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b9055-127">在本教程中，由于查询已经包含了数据值，因此它不需要外部数据源。</span><span class="sxs-lookup"><span data-stu-id="b9055-127">In this tutorial, the query already contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="b9055-128">这样，查询就会非常长。</span><span class="sxs-lookup"><span data-stu-id="b9055-128">This makes the query quite long.</span></span> <span data-ttu-id="b9055-129">在业务环境中，查询不会包含数据。</span><span class="sxs-lookup"><span data-stu-id="b9055-129">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="b9055-130">本教程中的查询仅供学习使用。</span><span class="sxs-lookup"><span data-stu-id="b9055-130">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-new-matrix"></a><span data-ttu-id="b9055-131">创建新矩阵</span><span class="sxs-lookup"><span data-stu-id="b9055-131">To create a new matrix</span></span>  
  
1.  <span data-ttu-id="b9055-132">单击 **“开始”**，依次指向 **“程序”**、 **Microsoft SQL Server 2012 Report Builder**，再单击 **“报表生成器”**。</span><span class="sxs-lookup"><span data-stu-id="b9055-132">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b9055-133">此时应显示 **“入门”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="b9055-133">The **Getting Started** dialog box should appear.</span></span> <span data-ttu-id="b9055-134">如果没有，请单击 "报表生成器" 按钮，单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="b9055-134">If it doesn't, from the Report Builder button, click **New**.</span></span>  
  
2.  <span data-ttu-id="b9055-135">在左窗格中，确认已选中 **“新建报表”** 。</span><span class="sxs-lookup"><span data-stu-id="b9055-135">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="b9055-136">在右窗格中，单击“表或矩阵向导”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b9055-136">In the right pane, click **Table or Matrix Wizard**.</span></span>  
  
4.  <span data-ttu-id="b9055-137">在“选择数据集”页上，单击“创建数据集”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b9055-137">On the **Choose a dataset** page, click **Create a dataset**.</span></span>  
  
5.  <span data-ttu-id="b9055-138">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="b9055-138">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="b9055-139">在 "**选择数据源的连接**" 页上，选择现有数据源或浏览到 Report Server，然后选择一个数据源。</span><span class="sxs-lookup"><span data-stu-id="b9055-139">On the **Choose a connection to a data source** page, select an existing data source or browse to the report server, and then select a data source.</span></span> <span data-ttu-id="b9055-140">如果没有可用数据源，或您无权访问报表服务器，您可以改用嵌入数据源。</span><span class="sxs-lookup"><span data-stu-id="b9055-140">If no data source is available or you do not have access to a report server, you can use an embedded data source instead.</span></span> <span data-ttu-id="b9055-141">有关创建嵌入数据源的详细信息，请参阅[教程：创建基本表报表 &#40;报表生成器&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="b9055-141">For more information about creating an embedded data source, see [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
7.  <span data-ttu-id="b9055-142">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="b9055-142">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="b9055-143">在“设计查询”页上，单击“编辑为文本”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b9055-143">On the **Design a query** page, click **Edit as Text**.</span></span>  
  
9. <span data-ttu-id="b9055-144">复制并将以下查询粘贴到查询窗格中：</span><span class="sxs-lookup"><span data-stu-id="b9055-144">Copy and paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13747.25 AS money) AS Sales, 55 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(9248.15 AS money) As Sales, 37 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1800.00 AS money) AS Sales, 24 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1125.00 AS money) AS Sales, 15 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory,  'Lens Adapter' as Product, CAST(742.50 AS money) AS Sales, 11 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1417.50 AS money) AS Sales, 21 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13497.30 AS money) AS Sales, 54 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(11997.60 AS money) AS Sales, 48 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(10247.95 AS money) As Sales, 41 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory, 'Tripod' as Product, CAST(1200.00 AS money) AS Sales, 16 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(2025.00 AS money) AS Sales, 27 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1425.00 AS money) AS Sales, 19 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(887.50 AS money) AS Sales, 13 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory, 'Lens Adapter' as Product, CAST(607.50 AS money) AS Sales, 9 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1215.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(10191.00 AS money) AS Sales, 79 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'North' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8772.00 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(10578.00 AS money) AS Sales, 82 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Central' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(7218.10 AS money) AS Sales, 38 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'North' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'South' as Territory,'Digital' as Subcategory,'Slim Digital' as Product, CAST(9307.55 AS money) AS Sales, 49 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(3870.00 AS money) AS Sales, 30 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'North' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(5805.00 AS money) AS Sales, 45 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8643.00 AS money) AS Sales, 67 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Central' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(9877.40 AS money) AS Sales, 52 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'North' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(12536.70 AS money) AS Sales, 66 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'South' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(6648.25 AS money) AS Sales, 35 as Quantity  
    ```  
  
10. <span data-ttu-id="b9055-145">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="b9055-145">Click **Next**.</span></span>  
  
##  <a name="2-organize-data-and-choose-layout-and-style-from-the-new-table-or-matrix-wizard"></a><a name="Groups"></a><span data-ttu-id="b9055-146">2. 在 "新建表或矩阵" 向导中组织数据并选择布局和样式</span><span class="sxs-lookup"><span data-stu-id="b9055-146">2. Organize Data and Choose Layout and Style from the New Table or Matrix Wizard</span></span>  
 <span data-ttu-id="b9055-147">使用此向导可提供用于显示数据的起始设计。</span><span class="sxs-lookup"><span data-stu-id="b9055-147">Use the wizard to provide a starting design on which to display data.</span></span> <span data-ttu-id="b9055-148">此向导中的预览窗格可帮助您在完成矩阵设计之前展现对数据进行分组的结果。</span><span class="sxs-lookup"><span data-stu-id="b9055-148">The preview pane in the wizard helps you to visualize the result of grouping data before you complete the matrix design.</span></span>  
  
#### <a name="to-organize-data-into-groups-and-choose-a-layout-and-style"></a><span data-ttu-id="b9055-149">将数据组织到组中并选择布局和样式</span><span class="sxs-lookup"><span data-stu-id="b9055-149">To organize data into groups and choose a layout and style</span></span>  
  
1.  <span data-ttu-id="b9055-150">在“排列字段”\*\*\*\* 页上，将 Territory 从“可用字段”\*\*\*\* 拖到“行组”\*\*\*\* 中。</span><span class="sxs-lookup"><span data-stu-id="b9055-150">On the **Arrange fields** page, drag Territory from **Available fields** to **Row groups**.</span></span>  
  
2.  <span data-ttu-id="b9055-151">将 SalesDate 拖到“行组”\*\*\*\* 中并将其放在 Territory 下面。</span><span class="sxs-lookup"><span data-stu-id="b9055-151">Drag SalesDate to **Row groups** and place it below Territory.</span></span>  
  
     <span data-ttu-id="b9055-152">“行组”\*\*\*\* 中字段的列出顺序定义组层次结构。</span><span class="sxs-lookup"><span data-stu-id="b9055-152">The order in which fields are listed in **Row groups** defines the group hierarchy.</span></span> <span data-ttu-id="b9055-153">步骤 1 和 2 首先按地区组织字段的值，然后按照销售日期组织字段的值。</span><span class="sxs-lookup"><span data-stu-id="b9055-153">Steps 1 and 2 organize the values of the fields first by territory, and then by sales date.</span></span>  
  
3.  <span data-ttu-id="b9055-154">将 Subcategory 拖到“列组”\*\*\*\* 中。</span><span class="sxs-lookup"><span data-stu-id="b9055-154">Drag Subcategory to **Column groups**.</span></span>  
  
4.  <span data-ttu-id="b9055-155">将 "产品 **" 拖到 "列组"，** 然后将其置于子类别下。</span><span class="sxs-lookup"><span data-stu-id="b9055-155">Drag Product to **Column groups,** and then place below Subcategory.</span></span>  
  
     <span data-ttu-id="b9055-156">字段在**列组**中的列出顺序定义组层次结构。</span><span class="sxs-lookup"><span data-stu-id="b9055-156">The order in which fields are listed in **Column groups** defines the group hierarchy.</span></span>  
  
     <span data-ttu-id="b9055-157">步骤 3 和 4 首先按子类别组织字段的值，然后按照产品组织字段的值。</span><span class="sxs-lookup"><span data-stu-id="b9055-157">Steps 3 and 4 organize the values for the fields first by subcategory, and then by product.</span></span>  
  
5.  <span data-ttu-id="b9055-158">将 Sales 拖到“值”\*\*\*\* 中。</span><span class="sxs-lookup"><span data-stu-id="b9055-158">Drag Sales to **Values**.</span></span>  
  
     <span data-ttu-id="b9055-159">将使用汇总数值字段的默认函数 Sum 函数对 Sales 进行汇总。</span><span class="sxs-lookup"><span data-stu-id="b9055-159">Sales is summarized with the Sum function, the default function to summarize numeric fields.</span></span>  
  
6.  <span data-ttu-id="b9055-160">将 Quantity 拖到“值”中\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b9055-160">Drag Quantity to **Values**.</span></span>  
  
     <span data-ttu-id="b9055-161">Quantity 使用 Sum 函数进行汇总。</span><span class="sxs-lookup"><span data-stu-id="b9055-161">Quantity is summarized with the Sum function.</span></span>  
  
     <span data-ttu-id="b9055-162">步骤 5 和 6 指定要在矩阵数据单元中显示的数据。</span><span class="sxs-lookup"><span data-stu-id="b9055-162">Steps 5 and 6 specify the data to display in the matrix data cells.</span></span>  
  
7.  <span data-ttu-id="b9055-163">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="b9055-163">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="b9055-164">在 "选择布局" 页的 "**选项**" 下，验证是否选择了 "**显示小计和总计**"。</span><span class="sxs-lookup"><span data-stu-id="b9055-164">On the Choose the Layout page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
9. <span data-ttu-id="b9055-165">验证是否选择了“分块式，小计下方显示”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b9055-165">Verify that **Blocked, subtotal below** is selected.</span></span>  
  
10. <span data-ttu-id="b9055-166">确认选择了“展开/折叠组”\*\*\*\* 选项。</span><span class="sxs-lookup"><span data-stu-id="b9055-166">Verify the option **Expand/collapse groups** is selected.</span></span>  
  
11. <span data-ttu-id="b9055-167">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="b9055-167">Click **Next**.</span></span>  
  
12. <span data-ttu-id="b9055-168">在 “选择样式” 页的 “样式” 窗格中，选择 **“石板”**。</span><span class="sxs-lookup"><span data-stu-id="b9055-168">On the Choose a Style page, in the Styles pane, select **Slate**.</span></span>  
  
13. <span data-ttu-id="b9055-169">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="b9055-169">Click **Finish**.</span></span>  
  
     <span data-ttu-id="b9055-170">矩阵将添加到设计图面中。</span><span class="sxs-lookup"><span data-stu-id="b9055-170">The matrix is added to the design surface.</span></span> <span data-ttu-id="b9055-171">“行组”窗格显示两个行组：Territory 和 SalesDate。</span><span class="sxs-lookup"><span data-stu-id="b9055-171">The Row Groups pane shows two row groups: Territory and SalesDate.</span></span> <span data-ttu-id="b9055-172">“列组”窗格显示两个列组：Subcategory 和 Product。</span><span class="sxs-lookup"><span data-stu-id="b9055-172">The Column Groups pane shows two column groups: Subcategory and Product.</span></span> <span data-ttu-id="b9055-173">详细信息数据是由数据集查询检索的所有数据。</span><span class="sxs-lookup"><span data-stu-id="b9055-173">Detail data is all the data that is retrieved by the dataset query.</span></span>  
  
14. <span data-ttu-id="b9055-174">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="b9055-174">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="b9055-175">对于在特定日期销售的每个产品，该矩阵显示产品所属于的子类别以及销售地区。</span><span class="sxs-lookup"><span data-stu-id="b9055-175">For each product that is sold on a specific date, the matrix shows the subcategory to which the product belongs and the territory of the sales.</span></span>  
  
##  <a name="3-format-data"></a><a name="FormatData"></a><span data-ttu-id="b9055-176">3. 设置数据格式</span><span class="sxs-lookup"><span data-stu-id="b9055-176">3. Format Data</span></span>  
 <span data-ttu-id="b9055-177">默认情况下，Sales 字段的汇总数据显示一般数字，而 SalesDate 字段则显示日期和时间信息。</span><span class="sxs-lookup"><span data-stu-id="b9055-177">By default, the summary data for the Sales field displays a general number and the SalesDate field displays both date and time information.</span></span> <span data-ttu-id="b9055-178">设置 Sales 字段格式以便将数字显示为货币，并且设置 SalesDate 字段格式以便只显示日期。</span><span class="sxs-lookup"><span data-stu-id="b9055-178">Format the Sales field to display the number as currency and the SalesDate field to display only the date.</span></span> <span data-ttu-id="b9055-179">切换“占位符样式”，将格式化的文本框和占位符文本显示为示例值\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b9055-179">Toggle **Placeholder Styles** to display formatted text boxes and placeholder text as sample values.</span></span>  
  
#### <a name="to-format-fields"></a><span data-ttu-id="b9055-180">设置字段格式</span><span class="sxs-lookup"><span data-stu-id="b9055-180">To format fields</span></span>  
  
1.  <span data-ttu-id="b9055-181">单击 "**设计**" 切换到 "设计" 视图。</span><span class="sxs-lookup"><span data-stu-id="b9055-181">Click **Design** to switch to design view.</span></span>  
  
2.  <span data-ttu-id="b9055-182">按 Ctrl 键，然后选择包含 `[Sum(Sales)]`的九个单元。</span><span class="sxs-lookup"><span data-stu-id="b9055-182">Press the Ctrl key, and then select the nine cells that contain `[Sum(Sales)]`.</span></span>  
  
3.  <span data-ttu-id="b9055-183">在“主文件夹”\*\*\*\* 选项卡上的“数字”\*\*\*\* 组中，单击“货币”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b9055-183">On the **Home** tab, in the **Number** group, click **Currency**.</span></span> <span data-ttu-id="b9055-184">单元会更改为显示已设置好格式的货币。</span><span class="sxs-lookup"><span data-stu-id="b9055-184">The cells changeto show the formatted currency.</span></span>  
  
     <span data-ttu-id="b9055-185">如果区域设置为“英语(美国)”，则默认示例文本为 [**$12,345.00**]。</span><span class="sxs-lookup"><span data-stu-id="b9055-185">If your regional setting is English (United States), the default sample text is [**$12,345.00**].</span></span> <span data-ttu-id="b9055-186">如果看不到示例货币值，请在 "**数字**" 组中单击 "**占位符样式**"，然后单击 "**示例值**"。</span><span class="sxs-lookup"><span data-stu-id="b9055-186">If you do not see an example currency value, click **Placeholder Styles** in the **Numbers** group, and then click **Sample Values**.</span></span>  
  
4.  <span data-ttu-id="b9055-187">单击包含 `[SalesDate]`的单元格。</span><span class="sxs-lookup"><span data-stu-id="b9055-187">Click the cell that contains `[SalesDate]`.</span></span>  
  
5.  <span data-ttu-id="b9055-188">在 "**数字**" 组中，从下拉列表中选择 "**日期**"。</span><span class="sxs-lookup"><span data-stu-id="b9055-188">In the **Number** group, from the drop-down list, select **Date**.</span></span>  
  
     <span data-ttu-id="b9055-189">单元格将显示示例日期 **[1/31/2000]**。</span><span class="sxs-lookup"><span data-stu-id="b9055-189">The cell displays the example date **[1/31/2000]**.</span></span> <span data-ttu-id="b9055-190">如果看不到示例日期，请单击“数字”\*\*\*\* 组中的“占位符样式”\*\*\*\*，然后单击“示例值”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b9055-190">If you do not see an example date, click **Placeholder Styles** in the **Numbers** group, and then click **Sample Values**.</span></span>  
  
6.  <span data-ttu-id="b9055-191">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="b9055-191">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="b9055-192">日期值仅显示日期，销售值显示为货币。</span><span class="sxs-lookup"><span data-stu-id="b9055-192">The date values display only dates and the sales values display as currency.</span></span>  
  
##  <a name="4-add-adjacent-column-group"></a><a name="AdjacentGroup"></a><span data-ttu-id="b9055-193">4. 添加相邻列组</span><span class="sxs-lookup"><span data-stu-id="b9055-193">4. Add Adjacent Column Group</span></span>  
 <span data-ttu-id="b9055-194">您可以在父子关系中嵌套行组和列组，或者在同级关系中保持它们相邻。</span><span class="sxs-lookup"><span data-stu-id="b9055-194">You can nest row and column groups in parent child relationships or adjacent in sibling relationships.</span></span>  
  
 <span data-ttu-id="b9055-195">添加与 Subcategory 列组相邻的列组，复制单元以便填充这个新的列组，然后使用表达式创建列组标题的值。</span><span class="sxs-lookup"><span data-stu-id="b9055-195">Add a column group that is adjacent to the Subcategory column group, copy cells to populate the new column group, and then use an expression to create the value of the column group header.</span></span>  
  
#### <a name="to-add-an-adjacent-column-group"></a><span data-ttu-id="b9055-196">添加相邻列组</span><span class="sxs-lookup"><span data-stu-id="b9055-196">To add an adjacent column group</span></span>  
  
1.  <span data-ttu-id="b9055-197">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="b9055-197">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="b9055-198">右键单击包含 `[Subcategory]` 的单元，指向“添加组”\*\*\*\*，然后单击“右侧相邻”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b9055-198">Right-click the cell that contains `[Subcategory]`, point to **Add Group**, and then click **Adjacent Right**.</span></span>  
  
     <span data-ttu-id="b9055-199">此时将打开 **“Tablix 组”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="b9055-199">The **Tablix Group** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="b9055-200">在“分组依据”\*\*\*\* 列表中选择 SalesDate，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b9055-200">In the **Group By** list, select SalesDate, and then click **OK**.</span></span>  
  
     <span data-ttu-id="b9055-201">一个新的列组将添加到 Subcategory 列组的左侧。</span><span class="sxs-lookup"><span data-stu-id="b9055-201">A new column group is added to the left of the Subcategory column group.</span></span>  
  
4.  <span data-ttu-id="b9055-202">右键单击新列组中包含 `[SalesDate],` 的单元，然后单击“表达式”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b9055-202">Right-click the cell in the new column group that contains `[SalesDate],` and then click **Expression**.</span></span>  
  
5.  <span data-ttu-id="b9055-203">将以下表达式复制到“表达式”框中。</span><span class="sxs-lookup"><span data-stu-id="b9055-203">Copy the following expression to expression box.</span></span>  
  
    ```  
    =WeekdayName(DatePart("w",Fields!SalesDate.Value))  
    ```  
  
     <span data-ttu-id="b9055-204">该表达式从销售日期中提取工作日名称。</span><span class="sxs-lookup"><span data-stu-id="b9055-204">This expression extracts the weekday name from the sales date.</span></span> <span data-ttu-id="b9055-205">有关详细信息，请参阅[表达式（报表生成器和 SSRS）](report-design/expressions-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="b9055-205">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md).</span></span>  
  
6.  <span data-ttu-id="b9055-206">右键单击 Subcategory 列组中包含 Total 的单元，然后单击“复制”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b9055-206">Right-click the cell in the Subcategory column group that contains Total, and then click **Copy**.</span></span>  
  
7.  <span data-ttu-id="b9055-207">右键单击包含在步骤 5 中创建的表达式的单元紧下方的单元，然后单击“粘贴”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b9055-207">Right-click the cell immediately below the cell that contains the expression you created in step 5 and click **Paste**.</span></span>  
  
8.  <span data-ttu-id="b9055-208">按 Ctrl 键。</span><span class="sxs-lookup"><span data-stu-id="b9055-208">Press the Ctrl key.</span></span>  
  
9. <span data-ttu-id="b9055-209">在 Subcategory 组中，单击 Sales 列标题以及标题下的三个单元，右键单击，然后单击“复制”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b9055-209">In the Subcategory group, click the Sales column header and the three cells below it, right-click, and then click **Copy**.</span></span>  
  
10. <span data-ttu-id="b9055-210">将这四个单元粘贴到新列组中的四个空单元中。</span><span class="sxs-lookup"><span data-stu-id="b9055-210">Paste the four cells into the four empty cells in the new column group.</span></span>  
  
11. <span data-ttu-id="b9055-211">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="b9055-211">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="b9055-212">报表包括名为 Monday 和 Tuesday 的列。</span><span class="sxs-lookup"><span data-stu-id="b9055-212">The report includes columns named Monday and Tuesday.</span></span> <span data-ttu-id="b9055-213">数据集仅包含针对这两天的数据。</span><span class="sxs-lookup"><span data-stu-id="b9055-213">The dataset contains only data for these two days.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b9055-214">如果数据包括了其他天，则报表也将包括这些天的相应列。</span><span class="sxs-lookup"><span data-stu-id="b9055-214">If the data included other days, the report would include columns for them as well.</span></span> <span data-ttu-id="b9055-215">每个列都具有列标题、 `Sales` 和按区域的销售总额。</span><span class="sxs-lookup"><span data-stu-id="b9055-215">Each column has the column header, `Sales`, and sales totals by territory.</span></span>  
  
##  <a name="5-change-column-widths"></a><a name="Width"></a><span data-ttu-id="b9055-216">5. 更改列宽</span><span class="sxs-lookup"><span data-stu-id="b9055-216">5. Change Column Widths</span></span>  
 <span data-ttu-id="b9055-217">包括矩阵的报表填充以水平方式展开，并且在运行时以垂直方式展开。</span><span class="sxs-lookup"><span data-stu-id="b9055-217">A report that includes a matrix typically expands horizontally as well as vertically when it runs.</span></span> <span data-ttu-id="b9055-218">如果您计划将数据导出到用于打印报表的格式（例如 Microsoft Word 或 Adobe PDF），则控制水平展开将特别重要。</span><span class="sxs-lookup"><span data-stu-id="b9055-218">Controlling horizontal expansion is particularly important if you plan to export the report to formats such as Microsoft Word or Adobe PDF that are used for printed reports.</span></span> <span data-ttu-id="b9055-219">如果报表跨多页水平展开，则打印报表将很难理解。</span><span class="sxs-lookup"><span data-stu-id="b9055-219">If the report expands horizontally across multiple pages, the printed report is difficult to understand.</span></span> <span data-ttu-id="b9055-220">为了尽量缩小水平展开，您可以将列的大小调整为宽度仅供无需换行就可以显示数据。</span><span class="sxs-lookup"><span data-stu-id="b9055-220">To minimize horizontal expansion, you can resize columns to be only the width necessary to display the data without wrapping.</span></span> <span data-ttu-id="b9055-221">您还可以重命名列，以便其标题适合显示数据所需的宽度。</span><span class="sxs-lookup"><span data-stu-id="b9055-221">You can also rename columns so that their titles fit the width needed to display the data.</span></span>  
  
#### <a name="to-rename-and-resize-the-columns"></a><span data-ttu-id="b9055-222">重命名列和调整列的大小</span><span class="sxs-lookup"><span data-stu-id="b9055-222">To rename and resize the columns</span></span>  
  
1.  <span data-ttu-id="b9055-223">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="b9055-223">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="b9055-224">选择距左侧最远的 Quantity 列中的文本，然后键入“QTY”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b9055-224">Select the text in the furthest Quantity column to the left, and then type **QTY**.</span></span>  
  
     <span data-ttu-id="b9055-225">列标题现在是 QTY。</span><span class="sxs-lookup"><span data-stu-id="b9055-225">The column title is now QTY.</span></span>  
  
3.  <span data-ttu-id="b9055-226">对于名为 Quantity 的其他列，重复执行步骤 2。</span><span class="sxs-lookup"><span data-stu-id="b9055-226">Repeat step 2 for the other columns named Quantity.</span></span> <span data-ttu-id="b9055-227">共有两个这样的列。</span><span class="sxs-lookup"><span data-stu-id="b9055-227">There are two of them.</span></span>  
  
4.  <span data-ttu-id="b9055-228">单击矩阵，以便在此矩阵的上方和旁边显示列控点和行控点。</span><span class="sxs-lookup"><span data-stu-id="b9055-228">Click the matrix so that column and row handles appear above and next to the matrix.</span></span>  
  
     <span data-ttu-id="b9055-229">沿此表的上方和一侧显示的灰色条状物就是列控点和行控点。</span><span class="sxs-lookup"><span data-stu-id="b9055-229">The gray bars along the top and side of the table are the column and row handles.</span></span>  
  
5.  <span data-ttu-id="b9055-230">为了将最远的 QTY 列向左侧调整，请指向列控点之间的线条，使光标变为双箭头。</span><span class="sxs-lookup"><span data-stu-id="b9055-230">To resize the furthest QTY column to the left, point to the line between column handles so that the cursor changes into a double arrow.</span></span> <span data-ttu-id="b9055-231">将列向左侧拖动，直到宽度为 1/2 英寸。</span><span class="sxs-lookup"><span data-stu-id="b9055-231">Drag the column towards the left until it is 1/2 inch wide.</span></span>  
  
     <span data-ttu-id="b9055-232">1/2 英寸的列宽足以显示数量了。</span><span class="sxs-lookup"><span data-stu-id="b9055-232">A column width of 1/2 inch is adequate to display the quantity.</span></span>  
  
6.  <span data-ttu-id="b9055-233">对于名为 QTY 的其他列，重复执行步骤 5。</span><span class="sxs-lookup"><span data-stu-id="b9055-233">Repeat step 5 for the other columns named QTY.</span></span>  
  
7.  <span data-ttu-id="b9055-234">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="b9055-234">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="b9055-235">报表中包含数量的列现在名为 QTY，并且这些列更窄了。</span><span class="sxs-lookup"><span data-stu-id="b9055-235">The columns in the report that contains quantities are now named QTY and the columns are narrower.</span></span>  
  
##  <a name="6-merge-matrix-cells"></a><a name="MergeCells"></a><span data-ttu-id="b9055-236">6. 合并矩阵单元</span><span class="sxs-lookup"><span data-stu-id="b9055-236">6. Merge Matrix Cells</span></span>  
 <span data-ttu-id="b9055-237">角区域是矩阵的左上角。</span><span class="sxs-lookup"><span data-stu-id="b9055-237">The corner area is in the upper left corner of the matrix.</span></span> <span data-ttu-id="b9055-238">根据矩阵中行组和列组的数目，角区域中单元的数目将有所不同。</span><span class="sxs-lookup"><span data-stu-id="b9055-238">Depending on the number of row and column groups in the matrix, the number of cells in the corner area varies.</span></span> <span data-ttu-id="b9055-239">在本教程中内置的矩阵在其角区域中具有四个单元。</span><span class="sxs-lookup"><span data-stu-id="b9055-239">The matrix, built in this tutorial, has four cells in its corner area.</span></span> <span data-ttu-id="b9055-240">单元按两行和两列排列，反映行和列组层次结构的深度。</span><span class="sxs-lookup"><span data-stu-id="b9055-240">The cells are arranged in two rows and two columns, reflecting the depth of row and column group hierarchies.</span></span> <span data-ttu-id="b9055-241">这四个单元并不用于此报表，并且您要将它们合并为一个单元。</span><span class="sxs-lookup"><span data-stu-id="b9055-241">The four cells are not used in this report and you will merge them into one.</span></span>  
  
#### <a name="to-merge-matrix-cells"></a><span data-ttu-id="b9055-242">合并矩阵单元</span><span class="sxs-lookup"><span data-stu-id="b9055-242">To merge matrix cells</span></span>  
  
1.  <span data-ttu-id="b9055-243">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="b9055-243">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="b9055-244">单击矩阵，以便在此矩阵的上方和旁边显示列控点和行控点。</span><span class="sxs-lookup"><span data-stu-id="b9055-244">Click the matrix so that column and row handles appear above and next to the matrix.</span></span>  
  
3.  <span data-ttu-id="b9055-245">按 Ctrl 键，然后选择四个角单元。</span><span class="sxs-lookup"><span data-stu-id="b9055-245">Press the Ctrl key, and then select the four corner cells.</span></span>  
  
4.  <span data-ttu-id="b9055-246">右键单击单元，然后单击 "**合并单元**"。</span><span class="sxs-lookup"><span data-stu-id="b9055-246">Right-click the cells and then click **Merge Cells**.</span></span>  
  
5.  <span data-ttu-id="b9055-247">右键单击角单元，然后单击 "**文本框属性**"。</span><span class="sxs-lookup"><span data-stu-id="b9055-247">Right-click the corner cell, and then click **Text Box Properties**.</span></span>  
  
6.  <span data-ttu-id="b9055-248">单击 **“填充”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="b9055-248">Click the **Fill** tab.</span></span>  
  
7.  <span data-ttu-id="b9055-249">单击 "**填充颜色**" 的 " (***fx***) " 按钮。</span><span class="sxs-lookup"><span data-stu-id="b9055-249">Click the (***fx***) button for **Fill color**.</span></span>  
  
8.  <span data-ttu-id="b9055-250">将以下表达式复制并粘贴到“表达式”框中。</span><span class="sxs-lookup"><span data-stu-id="b9055-250">Copy and paste the following expression in the expression box.</span></span>  
  
    ```  
    #96a4b2  
    ```  
  
     <span data-ttu-id="b9055-251">这是用于在“石板”样式中使用的蓝灰色的 RGB 十六进制值。</span><span class="sxs-lookup"><span data-stu-id="b9055-251">This is the RGB hex value for a gray blue color used in the Slate style.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. <span data-ttu-id="b9055-252">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="b9055-252">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="b9055-253">右上角的矩阵是单个单元，具有与行组和列组单元相同的颜色。</span><span class="sxs-lookup"><span data-stu-id="b9055-253">The upper corner matrix is a single cell and has the same color as the row group and column group cells.</span></span>  
  
##  <a name="7-add-a-report-header-and-report-title"></a><a name="HeaderTitle"></a><span data-ttu-id="b9055-254">7. 添加报表表头和报表标题</span><span class="sxs-lookup"><span data-stu-id="b9055-254">7. Add a Report Header and Report Title</span></span>  
 <span data-ttu-id="b9055-255">报表标题将出现在报表的顶部。</span><span class="sxs-lookup"><span data-stu-id="b9055-255">A report title appears at the top of the report.</span></span> <span data-ttu-id="b9055-256">可以将报表标题置于报表表头中或置于表体顶部的文本框中（如果报表未使用表头）。</span><span class="sxs-lookup"><span data-stu-id="b9055-256">You can place the report title in a report header or if the report does not use one, in a text box at the top of the report body.</span></span> <span data-ttu-id="b9055-257">在本教程中，您将删除报表顶部的文本框，并向表头中添加主题。</span><span class="sxs-lookup"><span data-stu-id="b9055-257">In this tutorial, you will remove the text box at the top of the report and add a title to the header.</span></span>  
  
#### <a name="to-add-a-report-header-and-report-title"></a><span data-ttu-id="b9055-258">添加报表表头和报表标题</span><span class="sxs-lookup"><span data-stu-id="b9055-258">To add a report header and report title</span></span>  
  
1.  <span data-ttu-id="b9055-259">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="b9055-259">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="b9055-260">单击表体顶部包含 "**单击以添加标题**" 的文本框，然后按 Delete 键。</span><span class="sxs-lookup"><span data-stu-id="b9055-260">Click the text box at the top of the report body that contains **Click to add title**, and then press the Delete key.</span></span>  
  
3.  <span data-ttu-id="b9055-261">在功能区的 "**插入**" 选项卡上，单击 "**页眉**"，然后单击 "**添加标头**"。</span><span class="sxs-lookup"><span data-stu-id="b9055-261">On the **Insert** tab of the ribbon, click **Header** and then click **Add Header**.</span></span>  
  
     <span data-ttu-id="b9055-262">页眉将添加到表体的顶部。</span><span class="sxs-lookup"><span data-stu-id="b9055-262">A header is added to the top of the report body.</span></span>  
  
4.  <span data-ttu-id="b9055-263">在“插入”\*\*\*\* 选项卡中，单击“文本框”\*\*\*\*，然后将某一文本框拖到报表表头内。</span><span class="sxs-lookup"><span data-stu-id="b9055-263">On the **Insert** tab, click **Text Box**, and then drag a text box inside the report header.</span></span> <span data-ttu-id="b9055-264">使文本框大约 6 英寸长、3/4 英寸高，并且将其放置于表头的左侧。</span><span class="sxs-lookup"><span data-stu-id="b9055-264">Make the text box about 6 inches long and 3/4 inch tall and place it on the left side of the report header.</span></span>  
  
5.  <span data-ttu-id="b9055-265">在文本框中，键入“Sales by Territory, Subcategory, and Day”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b9055-265">In the text box, type **Sales by Territory, Subcategory, and Day**.</span></span>  
  
6.  <span data-ttu-id="b9055-266">选择键入的文本，右键单击，然后单击 "**文本属性**"。</span><span class="sxs-lookup"><span data-stu-id="b9055-266">Select the text you typed, right-click, and then click **Text Properties**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b9055-267">若要一起设置多个字符的格式，这些字符必须是连续的。</span><span class="sxs-lookup"><span data-stu-id="b9055-267">To format characters at the same time, they must be contiguous.</span></span>  
  
7.  <span data-ttu-id="b9055-268">在 "**文本属性**" 对话框中，单击 "**字体**"。</span><span class="sxs-lookup"><span data-stu-id="b9055-268">In the **Text Properties** dialog box, click **Font**.</span></span>  
  
8.  <span data-ttu-id="b9055-269">在 "**字体**" 列表中，选择 " **New Roman**";**大小**选择**24 pt**，在 "**颜色**" 中选择 "**褐紫红色**"，在 "**样式**" 中选择 "**斜体**"。</span><span class="sxs-lookup"><span data-stu-id="b9055-269">In the **Font** list, select **Times New Roman**; in **Size** select **24 pt**, in **Color** select **Maroon**, and in **Style** select **Italic**.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. <span data-ttu-id="b9055-270">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="b9055-270">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="b9055-271">报表在表头中包含一个报表标题。</span><span class="sxs-lookup"><span data-stu-id="b9055-271">The report includes a report title in the report header.</span></span>  
  
##  <a name="8-save-the-report"></a><a name="Save"></a><span data-ttu-id="b9055-272">8. 保存报表</span><span class="sxs-lookup"><span data-stu-id="b9055-272">8. Save the Report</span></span>  
 <span data-ttu-id="b9055-273">您可以将报表保存到报表服务器、SharePoint 库或本地计算机。</span><span class="sxs-lookup"><span data-stu-id="b9055-273">You can save reports to a report server, SharePoint library, or your computer.</span></span>  
  
 <span data-ttu-id="b9055-274">在本教程中，将报表保存到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="b9055-274">In this tutorial, save the report to a report server.</span></span> <span data-ttu-id="b9055-275">如果您没有对报表服务器的访问权限，则可以保存到您的计算机。</span><span class="sxs-lookup"><span data-stu-id="b9055-275">If you do not have access to a report server, save the report to your computer.</span></span>  
  
#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="b9055-276">将报表保存到报表服务器</span><span class="sxs-lookup"><span data-stu-id="b9055-276">To save the report on a report server</span></span>  
  
1.  <span data-ttu-id="b9055-277">从 **“报表生成器”** 按钮，单击 **“另存为”**。</span><span class="sxs-lookup"><span data-stu-id="b9055-277">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="b9055-278">单击 **“最近使用的站点和服务器”**。</span><span class="sxs-lookup"><span data-stu-id="b9055-278">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="b9055-279">选择或键入您拥有保存报表权限的报表服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="b9055-279">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="b9055-280">此时将显示“正在连接到报表服务器”消息。</span><span class="sxs-lookup"><span data-stu-id="b9055-280">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="b9055-281">当连接完成时，您将看到报表服务器管理员指定为默认报表位置的报表文件夹的内容。</span><span class="sxs-lookup"><span data-stu-id="b9055-281">When the connection is complete, you will see the contents of the report folder that the report server administrator specified as the default report location.</span></span>  
  
4.  <span data-ttu-id="b9055-282">在“名称”\*\*\*\* 中，用“SalesByTerritorySubcategory”\*\*\*\* 替换默认名称。</span><span class="sxs-lookup"><span data-stu-id="b9055-282">In **Name**, replace the default name with **SalesByTerritorySubcategory**.</span></span>  
  
5.  <span data-ttu-id="b9055-283">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="b9055-283">Click **Save**.</span></span>  
  
 <span data-ttu-id="b9055-284">报表即已保存至报表服务器。</span><span class="sxs-lookup"><span data-stu-id="b9055-284">The report is saved to the report server.</span></span> <span data-ttu-id="b9055-285">您连接的报表服务器的名称将显示在窗口底部的状态栏中。</span><span class="sxs-lookup"><span data-stu-id="b9055-285">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
#### <a name="to-save-the-report-on-your-computer"></a><span data-ttu-id="b9055-286">将报表保存到计算机上</span><span class="sxs-lookup"><span data-stu-id="b9055-286">To save the report on your computer</span></span>  
  
1.  <span data-ttu-id="b9055-287">从 **“报表生成器”** 按钮，单击 **“另存为”**。</span><span class="sxs-lookup"><span data-stu-id="b9055-287">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="b9055-288">单击 **“桌面”**、 **“我的文档”** 或 **“我的电脑”**，然后浏览到要将报表保存到的文件夹。</span><span class="sxs-lookup"><span data-stu-id="b9055-288">Click **Desktop**, **My Documents**, or **My computer**, and then browse to the folder where you want to save the report.</span></span>  
  
3.  <span data-ttu-id="b9055-289">在“名称”\*\*\*\* 中，用“SalesByTerritorySubcategory”\*\*\*\* 替换默认名称。</span><span class="sxs-lookup"><span data-stu-id="b9055-289">In **Name**, replace the default name with **SalesByTerritorySubcategory**.</span></span>  
  
4.  <span data-ttu-id="b9055-290">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="b9055-290">Click **Save**.</span></span>  
  
##  <a name="9-optional-rotate-text-box-270-degrees"></a><a name="RotateTextBox"></a><span data-ttu-id="b9055-291">9. (可选) 旋转文本框270度</span><span class="sxs-lookup"><span data-stu-id="b9055-291">9. (Optional) Rotate Text Box 270 Degrees</span></span>  
 <span data-ttu-id="b9055-292">具有矩阵的报表在运行时可以垂直方式和水平方式展开。</span><span class="sxs-lookup"><span data-stu-id="b9055-292">A report with matrices can expand horizontally and vertically when it runs.</span></span> <span data-ttu-id="b9055-293">通过垂直旋转文本框或者旋转 270 度，您可以节约水平空间。</span><span class="sxs-lookup"><span data-stu-id="b9055-293">By rotating text boxes vertically, or 270 degrees, you can save horizontal space.</span></span> <span data-ttu-id="b9055-294">呈现的报表然后将更窄，并且如果导出到 Microsoft Word 之类的格式，报表将更有可能适合打印页面。</span><span class="sxs-lookup"><span data-stu-id="b9055-294">The rendered report is then narrower and if exported to a format such as Microsoft Word, will be more likely to fit on a printed page.</span></span>  
  
 <span data-ttu-id="b9055-295">文本框还可以将文本显示为竖排（从上到下）。</span><span class="sxs-lookup"><span data-stu-id="b9055-295">A text box can also display text as horizontal, vertical (top to bottom).</span></span> <span data-ttu-id="b9055-296">有关详细信息，请参阅[文本框（报表生成器和 SSRS）](report-design/text-boxes-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="b9055-296">For more information, see [Text Boxes &#40;Report Builder and SSRS&#41;](report-design/text-boxes-report-builder-and-ssrs.md).</span></span>  
  
#### <a name="to-rotate-text-box-270-degrees"></a><span data-ttu-id="b9055-297">旋转文本框 270 度</span><span class="sxs-lookup"><span data-stu-id="b9055-297">To rotate text box 270 degrees</span></span>  
  
1.  <span data-ttu-id="b9055-298">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="b9055-298">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="b9055-299">单击包含 `[Territory].` 的单元。</span><span class="sxs-lookup"><span data-stu-id="b9055-299">Click the cell that contains `[Territory].`</span></span>  
  
3.  <span data-ttu-id="b9055-300">在 "属性" 窗格中，找到 "WritingMode" 属性，然后在其下拉列表中选择 " **Rotate270**"。</span><span class="sxs-lookup"><span data-stu-id="b9055-300">In the Properties pane, locate the WritingMode property and in its drop-down list, select **Rotate270**.</span></span>  
  
     <span data-ttu-id="b9055-301">如果“属性”窗格未打开，请单击功能区的“视图”\*\*\*\* 选项卡，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b9055-301">If the Properties pane is not open, click the **View** tab of the ribbon, and then select **Properties**.</span></span>  
  
4.  <span data-ttu-id="b9055-302">验证 CanGrow 属性是否设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="b9055-302">Verify that the CanGrow property is set to `True`.</span></span>  
  
5.  <span data-ttu-id="b9055-303">将 Territory 列的大小调整为 1/2 英寸宽，并且删除列标题。</span><span class="sxs-lookup"><span data-stu-id="b9055-303">Resize the Territory column to be 1/2 inch wide and delete the column title.</span></span>  
  
6.  <span data-ttu-id="b9055-304">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="b9055-304">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="b9055-305">地区名称垂直书写，从下到上。</span><span class="sxs-lookup"><span data-stu-id="b9055-305">The territory name is written vertically, bottom to top.</span></span> <span data-ttu-id="b9055-306">Territory 行组的高度由地区名称的长度决定。</span><span class="sxs-lookup"><span data-stu-id="b9055-306">The height of the Territory row group varies by the length of the territory name.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b9055-307">后续步骤</span><span class="sxs-lookup"><span data-stu-id="b9055-307">Next Steps</span></span>  
 <span data-ttu-id="b9055-308">有关如何创建矩阵报表的教程到此结束。</span><span class="sxs-lookup"><span data-stu-id="b9055-308">This concludes the tutorial for how to create a matrix report.</span></span> <span data-ttu-id="b9055-309">有关矩阵的详细信息，请参阅[表、矩阵和列表 &#40;报表生成器和 ssrs&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)，[矩阵 &#40;报表生成器和 ssrs&#41;](report-design/create-a-matrix-report-builder-and-ssrs.md)， [tablix 数据区域区域 &#40;报表生成器和 Ssrs&#41;](report-design/tablix-data-region-areas-report-builder-and-ssrs.md)，以及[Tablix 数据区域单元、行和列 &#40;报表生成器&#41; 和 SSRS](report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="b9055-309">For more information about matrices, see [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md), [Matrices &#40;Report Builder and SSRS&#41;](report-design/create-a-matrix-report-builder-and-ssrs.md), [Tablix Data Region Areas &#40;Report Builder and SSRS&#41;](report-design/tablix-data-region-areas-report-builder-and-ssrs.md), and [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9055-310">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b9055-310">See Also</span></span>  
 <span data-ttu-id="b9055-311">[教程 &#40;报表生成器&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="b9055-311">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="b9055-312">SQL Server 2014 中的报表生成器</span><span class="sxs-lookup"><span data-stu-id="b9055-312">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
