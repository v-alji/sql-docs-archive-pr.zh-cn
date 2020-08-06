---
title: 教程：设置文本格式（报表生成器）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 67d8513e-8a70-464b-b87f-e91d010cfd82
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c96b500f8aa30b77c78f75ccd1342398fd44eb2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692214"
---
# <a name="tutorial-format-text-report-builder"></a><span data-ttu-id="38bae-102">教程：设置文本格式（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="38bae-102">Tutorial: Format Text (Report Builder)</span></span>
  <span data-ttu-id="38bae-103">在本教程中，您可以练习以不同方式设置文本格式。</span><span class="sxs-lookup"><span data-stu-id="38bae-103">In this tutorial, you can practice formatting text in various ways.</span></span> <span data-ttu-id="38bae-104">在设置了具有数据源和数据集的空白报表后，您可以选择要完成的步骤。</span><span class="sxs-lookup"><span data-stu-id="38bae-104">After you set up the blank report with the data source and dataset, you can pick and choose the steps that you want to explore.</span></span>  
  
 <span data-ttu-id="38bae-105">下图显示与您将创建的报表类似的报表。</span><span class="sxs-lookup"><span data-stu-id="38bae-105">The following illustration shows a report similar to the one you will create.</span></span>  
  
 <span data-ttu-id="38bae-106">![rs_FormatTextFinal](../../2014/tutorials/media/rs-formattextfinal.gif "rs_FormatTextFinal")</span><span class="sxs-lookup"><span data-stu-id="38bae-106">![rs_FormatTextFinal](../../2014/tutorials/media/rs-formattextfinal.gif "rs_FormatTextFinal")</span></span>  
  
 <span data-ttu-id="38bae-107">在一个步骤中，您可以故意犯某个错误，以便可以了解错误的成因。</span><span class="sxs-lookup"><span data-stu-id="38bae-107">In one step, you make a mistake on purpose so you can see why it is a mistake.</span></span> <span data-ttu-id="38bae-108">然后，您可以纠正该错误以便实现预期效果。</span><span class="sxs-lookup"><span data-stu-id="38bae-108">Then you correct the mistake to achieve the desired effect.</span></span>  
  
 <span data-ttu-id="38bae-109">您在本教程中创建的报表的增强版本可用作示例 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 报表生成器报表。</span><span class="sxs-lookup"><span data-stu-id="38bae-109">An enhanced version of the report you create in this tutorial is available as a sample [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Report Builder report.</span></span> <span data-ttu-id="38bae-110">有关下载此示例报表和其他内容的详细信息，请参阅[报表生成器示例报表](https://go.microsoft.com/fwlink/?LinkId=184851)。</span><span class="sxs-lookup"><span data-stu-id="38bae-110">For more information about downloading this sample report and others, see [Report Builder sample reports](https://go.microsoft.com/fwlink/?LinkId=184851).</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="38bae-111">你将学习的内容</span><span class="sxs-lookup"><span data-stu-id="38bae-111">What You Will Learn</span></span>  
  
### <a name="set-up-the-report"></a><span data-ttu-id="38bae-112">设置报表</span><span class="sxs-lookup"><span data-stu-id="38bae-112">Set Up the Report</span></span>  
 1. [<span data-ttu-id="38bae-113">创建具有数据源和数据集的空白报表</span><span class="sxs-lookup"><span data-stu-id="38bae-113">Create a Blank Report with a Data Source and Dataset</span></span>](#CreateReport)  
  
 2. [<span data-ttu-id="38bae-114">向报表设计图面添加字段（故意犯错，然后纠正）</span><span class="sxs-lookup"><span data-stu-id="38bae-114">Add a Field to the Report Design Surface (Incorrectly, then Correctly)</span></span>](#AddField)  
  
 3. [<span data-ttu-id="38bae-115">向报表添加表 Design Surface</span><span class="sxs-lookup"><span data-stu-id="38bae-115">Add a Table to the Report Design Surface</span></span>](#AddTable)  
  
### <a name="pick-and-choose"></a><span data-ttu-id="38bae-116">选取和选择</span><span class="sxs-lookup"><span data-stu-id="38bae-116">Pick and Choose</span></span>  
 [<span data-ttu-id="38bae-117">向报表添加超链接</span><span class="sxs-lookup"><span data-stu-id="38bae-117">Add a Hyperlink to the Report</span></span>](#AddHyperlink)  
  
 [<span data-ttu-id="38bae-118">旋转报表中的文本</span><span class="sxs-lookup"><span data-stu-id="38bae-118">Rotate Text in the Report</span></span>](#RotateText)  
  
 [<span data-ttu-id="38bae-119">用 HTML 格式显示文本</span><span class="sxs-lookup"><span data-stu-id="38bae-119">Displaying Text with HTML Formatting</span></span>](#FormatHTML)  
  
 [<span data-ttu-id="38bae-120">设置货币格式</span><span class="sxs-lookup"><span data-stu-id="38bae-120">Format Currency</span></span>](#FormatCurrency)  
  
 [<span data-ttu-id="38bae-121">保存报表</span><span class="sxs-lookup"><span data-stu-id="38bae-121">Save the Report</span></span>](#Save)  
  
 <span data-ttu-id="38bae-122">完成本教程的预计学时：20 分钟。</span><span class="sxs-lookup"><span data-stu-id="38bae-122">Estimated time to complete this tutorial: 20 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38bae-123">要求</span><span class="sxs-lookup"><span data-stu-id="38bae-123">Requirements</span></span>  
 <span data-ttu-id="38bae-124">有关要求的详细信息，请参阅[教程先决条件（报表生成器）](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="38bae-124">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="create-a-blank-report-with-a-data-source-and-dataset"></a><a name="CreateReport"></a><span data-ttu-id="38bae-125">创建具有数据源和数据集的空白报表</span><span class="sxs-lookup"><span data-stu-id="38bae-125">Create a Blank Report with a Data Source and Dataset</span></span>  
  
#### <a name="to-create-a-blank-report"></a><span data-ttu-id="38bae-126">创建空白报表</span><span class="sxs-lookup"><span data-stu-id="38bae-126">To create a blank report</span></span>  
  
1.  <span data-ttu-id="38bae-127">单击 "**开始**"，指向 "**程序**"，指向 [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] "**报表生成器**"，然后单击 "**报表生成器**"。</span><span class="sxs-lookup"><span data-stu-id="38bae-127">Click **Start**, point to **Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]**Report Builder**, and then click **Report Builder**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="38bae-128">此时应显示 **“入门”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="38bae-128">The **Getting Started** dialog box should appear.</span></span> <span data-ttu-id="38bae-129">如果未显示该对话框，则从“报表生成器”按钮，单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="38bae-129">If it does not, from the Report Builder button, click **New**.</span></span>  
  
2.  <span data-ttu-id="38bae-130">在 **“入门”** 对话框的左窗格中，确保已选择 **“新建报表”** 。</span><span class="sxs-lookup"><span data-stu-id="38bae-130">In the left pane of the **Getting Started** dialog box, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="38bae-131">在右窗格中，单击 **“空白报表”**。</span><span class="sxs-lookup"><span data-stu-id="38bae-131">In the right pane, click **Blank Report**.</span></span>  
  
#### <a name="to-create-a-data-source"></a><span data-ttu-id="38bae-132">创建数据源</span><span class="sxs-lookup"><span data-stu-id="38bae-132">To create a data source</span></span>  
  
1.  <span data-ttu-id="38bae-133">在 "报表数据" 窗格中，单击 "**新建**"，然后单击 "**数据源**"。</span><span class="sxs-lookup"><span data-stu-id="38bae-133">In the Report Data pane, click **New**, and then click **Data Source**.</span></span>  
  
2.  <span data-ttu-id="38bae-134">在“名称”框中，键入：TextDataSource\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="38bae-134">In the **Name** box, type: **TextDataSource**</span></span>  
  
3.  <span data-ttu-id="38bae-135">单击 **“使用我的报表中嵌入的连接”**。</span><span class="sxs-lookup"><span data-stu-id="38bae-135">Click **Use a connection embedded in my report**.</span></span>  
  
4.  <span data-ttu-id="38bae-136">验证连接类型是否为 "Microsoft SQL Server"，然后在 "**连接字符串**" 框中键入： **Data \<servername> Source =**</span><span class="sxs-lookup"><span data-stu-id="38bae-136">Verify that the connection type is Microsoft SQL Server, and then in the **Connection string** box type: **Data Source = \<servername>**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="38bae-137">表达式 \<servername>（例如 Report001）指定安装了 SQL Server 数据库引擎实例的计算机。</span><span class="sxs-lookup"><span data-stu-id="38bae-137">The expression \<servername>, for example Report001, specifies a computer on which an instance of the SQL Server Database Engine is installed.</span></span> <span data-ttu-id="38bae-138">本教程不需要具体数据；只需要与 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="38bae-138">This tutorial does not need specific data; it just needs a connection to a [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] database.</span></span> <span data-ttu-id="38bae-139">如果你已经具有在“数据源连接”\*\*\*\* 下列出的某一数据源连接，则可以选择该连接并且转到下一过程“创建数据集”。</span><span class="sxs-lookup"><span data-stu-id="38bae-139">If you already have a data source connection listed under **Data Source Connections**, you can select it and go to the next procedure, "To create a dataset."</span></span> <span data-ttu-id="38bae-140">有关详细信息，请参阅[获取数据连接的备选方式（报表生成器）](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="38bae-140">For more information, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-create-a-dataset"></a><span data-ttu-id="38bae-141">创建数据集</span><span class="sxs-lookup"><span data-stu-id="38bae-141">To create a dataset</span></span>  
  
1.  <span data-ttu-id="38bae-142">在 "报表数据" 窗格中，单击 "**新建**"，然后单击 "**数据集**"。</span><span class="sxs-lookup"><span data-stu-id="38bae-142">In the Report Data pane, click **New**, and then click **Dataset**.</span></span>  
  
2.  <span data-ttu-id="38bae-143">确保数据源为 **TextDataSource**。</span><span class="sxs-lookup"><span data-stu-id="38bae-143">Verify that the data source is **TextDataSource**.</span></span>  
  
3.  <span data-ttu-id="38bae-144">在“名称”框中，键入：TextDataset\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="38bae-144">In the **Name** box, type: **TextDataset.**</span></span>  
  
4.  <span data-ttu-id="38bae-145">确保已选择 **“文本”** 查询类型，然后单击 **“查询设计器”**。</span><span class="sxs-lookup"><span data-stu-id="38bae-145">Verify that the **Text** query type is selected, and then click **Query Designer**.</span></span>  
  
5.  <span data-ttu-id="38bae-146">单击 **“编辑为文本”**。</span><span class="sxs-lookup"><span data-stu-id="38bae-146">Click **Edit as Text**.</span></span>  
  
6.  <span data-ttu-id="38bae-147">将以下查询粘贴到查询窗格中：</span><span class="sxs-lookup"><span data-stu-id="38bae-147">Paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13747.25 AS money) AS Sales, 55 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(9248.15 AS money) As Sales, 37 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1800.00 AS money) AS Sales, 24 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1125.00 AS money) AS Sales, 15 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,  'Lens Adapter' as Product, CAST(742.50 AS money) AS Sales, 11 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1417.50 AS money) AS Sales, 21 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13497.30 AS money) AS Sales, 54 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(11997.60 AS money) AS Sales, 48 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(10247.95 AS money) As Sales, 41 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Tripod' as Product, CAST(1200.00 AS money) AS Sales, 16 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(2025.00 AS money) AS Sales, 27 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1425.00 AS money) AS Sales, 19 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(887.50 AS money) AS Sales, 13 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Lens Adapter' as Product, CAST(607.50 AS money) AS Sales, 9 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1215.00 AS money) AS Sales, 18 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(10191.00 AS money) AS Sales, 79 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8772.00 AS money) AS Sales, 68 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(10578.00 AS money) AS Sales, 82 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(7218.10 AS money) AS Sales, 38 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory,'Digital' as Subcategory,'Slim Digital' as Product, CAST(9307.55 AS money) AS Sales, 49 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(3870.00 AS money) AS Sales, 30 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(5805.00 AS money) AS Sales, 45 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8643.00 AS money) AS Sales, 67 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(9877.40 AS money) AS Sales, 52 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(12536.70 AS money) AS Sales, 66 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(6648.25 AS money) AS Sales, 35 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    ```  
  
7.  <span data-ttu-id="38bae-148">单击“运行” (**!**) 以运行查询。</span><span class="sxs-lookup"><span data-stu-id="38bae-148">Click Run (**!**) to run the query.</span></span>  
  
     <span data-ttu-id="38bae-149">查询结果将是可用于在您的报表中显示的数据。</span><span class="sxs-lookup"><span data-stu-id="38bae-149">The query results are the data available to display in your report.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="add-a-field-to-the-report-design-surface"></a><a name="AddField"></a><span data-ttu-id="38bae-150">向报表添加字段 Design Surface</span><span class="sxs-lookup"><span data-stu-id="38bae-150">Add a Field to the Report Design Surface</span></span>  
 <span data-ttu-id="38bae-151">如果您希望来自您的数据集的字段出现在报表中，则第一感可能是要将其直接拖到设计图面。</span><span class="sxs-lookup"><span data-stu-id="38bae-151">If you want a field from your dataset to appear in a report, your first impulse may be to drag it directly to the design surface.</span></span> <span data-ttu-id="38bae-152">本练习指出为什么无法这样做以及相应替代步骤。</span><span class="sxs-lookup"><span data-stu-id="38bae-152">This exercise points out why that doesn't work and what to do instead.</span></span>  
  
#### <a name="to-add-a-field-to-the-report-and-get-the-wrong-result"></a><span data-ttu-id="38bae-153">向报表添加字段（获得错误结果）</span><span class="sxs-lookup"><span data-stu-id="38bae-153">To add a field to the report (and get the wrong result)</span></span>  
  
1.  <span data-ttu-id="38bae-154">将 **FullName** 字段从“报表数据”窗格中拖到设计图面中。</span><span class="sxs-lookup"><span data-stu-id="38bae-154">Drag the **FullName** field from the Report Data pane to the design surface.</span></span>  
  
     <span data-ttu-id="38bae-155">报表生成器将创建一个文本框，文本框中有一个表达式，该表达式表示为 \<Expr>。</span><span class="sxs-lookup"><span data-stu-id="38bae-155">Report Builder creates a text box with an expression in it, represented as \<Expr>.</span></span>  
  
2.  <span data-ttu-id="38bae-156">单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="38bae-156">Click **Run**.</span></span>  
  
     <span data-ttu-id="38bae-157">请注意，只有一条记录**Fernando Ross**，它按字母顺序排列查询中的第一条记录。</span><span class="sxs-lookup"><span data-stu-id="38bae-157">Note that there is just one record, **Fernando Ross**, which is alphabetically the first record in the query.</span></span> <span data-ttu-id="38bae-158">该字段并不重复以便显示该字段中的其他记录。</span><span class="sxs-lookup"><span data-stu-id="38bae-158">The field does not repeat to show the other records in that field.</span></span>  
  
3.  <span data-ttu-id="38bae-159">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="38bae-159">Click **Design** to return to design view.</span></span>  
  
4.  <span data-ttu-id="38bae-160">在文本框中选择表达式 \<Expr> 。</span><span class="sxs-lookup"><span data-stu-id="38bae-160">Select the expression \<Expr> in the text box.</span></span>  
  
5.  <span data-ttu-id="38bae-161">在“属性”窗格中，对于“值”属性，将看到以下内容（如果没有看到“属性”窗格，则在“视图”选项卡上，选中“属性”）\*\*\*\*\*\*\*\*\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="38bae-161">In the Properties pane, for the **Value** property, you see the following (if you don't see the Properties pane, on the **View** tab, check **Properties**):</span></span>  
  
    ```  
    =First(Fields!FullName.Value, "TextDataSet")  
    ```  
  
     <span data-ttu-id="38bae-162">`First` 函数设计为只检索字段中的第一个值，这就是您所看到的内容。</span><span class="sxs-lookup"><span data-stu-id="38bae-162">The `First` function is designed to retrieve only the first value in a field, and that is what it has done.</span></span>  
  
     <span data-ttu-id="38bae-163">将该字段直接拖到设计图面上创建了一个文本框。</span><span class="sxs-lookup"><span data-stu-id="38bae-163">Dragging the field directly to the design surface created a text box.</span></span> <span data-ttu-id="38bae-164">文本框本身并非数据区域，因此它们不显示来自报表数据集的数据。</span><span class="sxs-lookup"><span data-stu-id="38bae-164">Text boxes by themselves are not data regions, so they do not display data from a report dataset.</span></span> <span data-ttu-id="38bae-165">数据区域（例如表、矩阵和列表）中的文本框显示数据。</span><span class="sxs-lookup"><span data-stu-id="38bae-165">Text boxes in data regions, such as tables, matrices, and lists, do display data.</span></span>  
  
6.  <span data-ttu-id="38bae-166">选择文本框（如果您已经选择了表达式，则按下 Esc 以便选择该文本框），然后按 Delete 键。</span><span class="sxs-lookup"><span data-stu-id="38bae-166">Select the text box (if you have the expression selected, press ESC to select the text box), and press the DELETE key.</span></span>  
  
#### <a name="to-add-a-field-to-the-report-and-get-the-right-result"></a><span data-ttu-id="38bae-167">向报表添加字段（获得正确结果）</span><span class="sxs-lookup"><span data-stu-id="38bae-167">To add a field to the report (and get the right result)</span></span>  
  
1.  <span data-ttu-id="38bae-168">在功能区的“插入”选项卡的“数据区域”区域中，单击“列表”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="38bae-168">On the **Insert** tab of the ribbon, in the **Data Regions** area, click **List**.</span></span> <span data-ttu-id="38bae-169">单击设计图面，然后拖动以便创建一个框，该框大约两英寸宽、一英寸高。</span><span class="sxs-lookup"><span data-stu-id="38bae-169">Click the design surface, and then drag to create a box that about two inches wide and one inch tall.</span></span>  
  
2.  <span data-ttu-id="38bae-170">将 **FullName** 字段从“报表数据”窗格中拖到列表框中。</span><span class="sxs-lookup"><span data-stu-id="38bae-170">Drag the **FullName** field from the Report Data pane to the list box.</span></span>  
  
     <span data-ttu-id="38bae-171">此时，报表生成器将创建一个文本框，表达式 `[FullName]` 将位于该文本框中。</span><span class="sxs-lookup"><span data-stu-id="38bae-171">This time Report Builder creates a text box with the expression `[FullName]` in it.</span></span>  
  
3.  <span data-ttu-id="38bae-172">单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="38bae-172">Click **Run**.</span></span>  
  
     <span data-ttu-id="38bae-173">请注意，此时该框将重复以便显示查询中的所有记录。</span><span class="sxs-lookup"><span data-stu-id="38bae-173">Note that this time the box repeats to show all the records in the query.</span></span>  
  
4.  <span data-ttu-id="38bae-174">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="38bae-174">Click **Design** to return to design view.</span></span>  
  
5.  <span data-ttu-id="38bae-175">在文本框中选择该表达式。</span><span class="sxs-lookup"><span data-stu-id="38bae-175">Select the expression in the text box.</span></span>  
  
6.  <span data-ttu-id="38bae-176">在“属性”窗格中，对于“值”属性，将看到以下内容\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="38bae-176">In the Properties pane, for the **Value** property, you see the following:</span></span>  
  
    ```  
    =Fields!FullName.Value  
    ```  
  
     <span data-ttu-id="38bae-177">通过将文本框拖到列表数据区域，将显示处于数据集中的数据。</span><span class="sxs-lookup"><span data-stu-id="38bae-177">By dragging the text box to the list data region, you display the data that is in the dataset.</span></span>  
  
7.  <span data-ttu-id="38bae-178">选择列表框并按 Delete 键。</span><span class="sxs-lookup"><span data-stu-id="38bae-178">Select the list box and press the DELETE key.</span></span>  
  
##  <a name="add-a-table-to-the-report-design-surface"></a><a name="AddTable"></a><span data-ttu-id="38bae-179">向报表添加表 Design Surface</span><span class="sxs-lookup"><span data-stu-id="38bae-179">Add a Table to the Report Design Surface</span></span>  
 <span data-ttu-id="38bae-180">创建此表，以便您可以在其中放置超链接和旋转后的文本。</span><span class="sxs-lookup"><span data-stu-id="38bae-180">Create this table so that you'll have a place to put hyperlinks and rotated text.</span></span>  
  
#### <a name="to-add-a-table-to-the-report"></a><span data-ttu-id="38bae-181">将表添加到报表中</span><span class="sxs-lookup"><span data-stu-id="38bae-181">To add a table to the report</span></span>  
  
1.  <span data-ttu-id="38bae-182">在 "**插入**" 菜单上，单击 "**表**"，然后单击 "**表向导**"。</span><span class="sxs-lookup"><span data-stu-id="38bae-182">On the **Insert** menu, click **Table**, and then click **Table Wizard**.</span></span>  
  
2.  <span data-ttu-id="38bae-183">在 "新建表或矩阵" 向导的 "**选择数据集**" 页上，单击 "**选择此报表中的现有数据集或共享数据**集"，然后单击 " **TextDataset () 此报表**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="38bae-183">On the **Choose a dataset** page of the New Table or Matrix wizard, click **Choose an existing dataset in this report or a shared dataset**, and click **TextDataset (in this Report)**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="38bae-184">在 "**排列字段**" 页上，将 "**区域**"、" **externallink><maml linktext>**" 和 "**产品**" 字段拖到 "**行组**"，将 " **Sales** " 字段拖到 "**值**" 中，**然后单击 "**</span><span class="sxs-lookup"><span data-stu-id="38bae-184">On the **Arrange fields** page, drag the **Territory**, **LinkText**, and **Product** fields to **Row groups**, drag the **Sales** field to **Values**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="38bae-185">在 "**选择布局**" 页上，清除 "**展开/折叠组**" 复选框，以便可以看到整个表，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="38bae-185">On the **Choose the layout** page, clear the **Expand/collapse groups** check box so you can see the whole table, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="38bae-186">在 "**选择样式**" 页上，单击 "**石板**"，然后单击 "**完成**"。</span><span class="sxs-lookup"><span data-stu-id="38bae-186">On the **Choose a style** page, click **Slate**, and then click **Finish**.</span></span>  
  
6.  <span data-ttu-id="38bae-187">拖动该表以便该表位于标题块之下。</span><span class="sxs-lookup"><span data-stu-id="38bae-187">Drag the table so it is below the title block.</span></span>  
  
7.  <span data-ttu-id="38bae-188">单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="38bae-188">Click **Run**.</span></span>  
  
     <span data-ttu-id="38bae-189">该表看起来没问题，但具有两个总计行。</span><span class="sxs-lookup"><span data-stu-id="38bae-189">The table looks OK, but it has two Total rows.</span></span> <span data-ttu-id="38bae-190">**Externallink><maml linktext>** 字段不需要总计行。</span><span class="sxs-lookup"><span data-stu-id="38bae-190">The **LinkText** field doesn't need a Total row.</span></span>  
  
8.  <span data-ttu-id="38bae-191">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="38bae-191">Click **Design** to return to design view.</span></span>  
  
9. <span data-ttu-id="38bae-192">右键单击包含的文本框 `[LinkText]` ，然后单击 "**拆分单元**"。</span><span class="sxs-lookup"><span data-stu-id="38bae-192">Right-click the text box that contains `[LinkText]`, and click **Split Cells**.</span></span>  
  
10. <span data-ttu-id="38bae-193">选择该单元格下方的空单元格 `[LinkText]` ，然后按住 SHIFT 键并选择其右侧的两个单元： " **Product** " 列中的 "**合计**" 单元和 " `[Sum(Sales)]` **销售**" 列中的单元格。</span><span class="sxs-lookup"><span data-stu-id="38bae-193">Select the empty cell below the `[LinkText]` cell, and then hold down the SHIFT key and select the two cells to its right: the **Total** cell in the **Product** column and the `[Sum(Sales)]` cell in the **Sales** column.</span></span>  
  
11. <span data-ttu-id="38bae-194">选定这三个单元后，右键单击其中一个单元格，然后单击 "**删除行**"。</span><span class="sxs-lookup"><span data-stu-id="38bae-194">With those three cells selected, right-click one of those cells and click **Delete Row**.</span></span>  
  
12. <span data-ttu-id="38bae-195">单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="38bae-195">Click **Run**.</span></span>  
  
##  <a name="add-a-hyperlink-to-the-report"></a><a name="AddHyperlink"></a><span data-ttu-id="38bae-196">向报表添加超链接</span><span class="sxs-lookup"><span data-stu-id="38bae-196">Add a Hyperlink to the Report</span></span>  
 <span data-ttu-id="38bae-197">在本节中，您将向前一节中的表中的文本添加超链接。</span><span class="sxs-lookup"><span data-stu-id="38bae-197">In this section, you add a hyperlink to text in the table from the previous section.</span></span>  
  
#### <a name="to-add-a-hyperlink-to-the-report"></a><span data-ttu-id="38bae-198">向报表添加超链接</span><span class="sxs-lookup"><span data-stu-id="38bae-198">To add a hyperlink to the report</span></span>  
  
1.  <span data-ttu-id="38bae-199">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="38bae-199">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="38bae-200">右键单击包含 `[LinkText]` 的单元格，然后单击“文本框属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="38bae-200">Right-click in the cell containing `[LinkText]`, and click **Text Box Properties**.</span></span>  
  
3.  <span data-ttu-id="38bae-201">在 "**文本框属性**" 框中，单击 "**操作**"。</span><span class="sxs-lookup"><span data-stu-id="38bae-201">In the **Text Box Properties** box, click **Action**.</span></span>  
  
4.  <span data-ttu-id="38bae-202">单击 "**前往 URL**"。</span><span class="sxs-lookup"><span data-stu-id="38bae-202">Click **Go to URL**.</span></span>  
  
5.  <span data-ttu-id="38bae-203">在 "**选择 url** " 框中，单击 " **url**"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="38bae-203">In the **Select URL** box, click **[URL]**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="38bae-204">请注意，文本在外观上看不出任何区别。</span><span class="sxs-lookup"><span data-stu-id="38bae-204">Note that the text does not look any different.</span></span> <span data-ttu-id="38bae-205">您需要使其看起来像链接文本。</span><span class="sxs-lookup"><span data-stu-id="38bae-205">You need to make it look like link text.</span></span>  
  
7.  <span data-ttu-id="38bae-206">选择 `[LinkText]`。</span><span class="sxs-lookup"><span data-stu-id="38bae-206">Select `[LinkText]`.</span></span>  
  
8.  <span data-ttu-id="38bae-207">在 "**主页**" 选项卡的 "**字体**" 部分中，单击 "**下划线**" 按钮，然后单击 "**颜色**" 按钮旁的下拉箭头，然后单击 "**蓝色**"。</span><span class="sxs-lookup"><span data-stu-id="38bae-207">In the **Font** section of the **Home** tab, click the **Underline** button, and then click the drop-down arrow next to the **Color** button, and click **Blue**.</span></span>  
  
9. <span data-ttu-id="38bae-208">单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="38bae-208">Click **Run**.</span></span>  
  
     <span data-ttu-id="38bae-209">文本现在看起来像链接了。</span><span class="sxs-lookup"><span data-stu-id="38bae-209">The text now looks like a link.</span></span>  
  
10. <span data-ttu-id="38bae-210">单击某一链接。</span><span class="sxs-lookup"><span data-stu-id="38bae-210">Click a link.</span></span> <span data-ttu-id="38bae-211">如果计算机已连接到 Internet，则浏览器将打开到报表生成器的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="38bae-211">If the computer is connected to the Internet, a browser will open to a Report Builder Help topic.</span></span>  
  
##  <a name="rotate-text-in-the-report"></a><a name="RotateText"></a><span data-ttu-id="38bae-212">旋转报表中的文本</span><span class="sxs-lookup"><span data-stu-id="38bae-212">Rotate Text in the Report</span></span>  
 <span data-ttu-id="38bae-213">在本节中，您将旋转前一节的表中的某些文本。</span><span class="sxs-lookup"><span data-stu-id="38bae-213">In this section, you rotate some of the text in the table from the previous sections.</span></span>  
  
#### <a name="to-rotate-text"></a><span data-ttu-id="38bae-214">旋转文本</span><span class="sxs-lookup"><span data-stu-id="38bae-214">To rotate text</span></span>  
  
1.  <span data-ttu-id="38bae-215">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="38bae-215">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="38bae-216">单击包含 的单元格。 `[Territory].`</span><span class="sxs-lookup"><span data-stu-id="38bae-216">Click in the cell containing `[Territory].`</span></span>  
  
3.  <span data-ttu-id="38bae-217">在“开始”\*\*\*\* 选项卡上的“字体”\*\*\*\* 部分中，单击“加粗”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="38bae-217">On the **Home** tab in the **Font** section, click the **Bold** button.</span></span>  
  
4.  <span data-ttu-id="38bae-218">如果“属性”窗格未打开，请在“视图”选项卡上选中“属性”复选框\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="38bae-218">If the Properties pane is not open, on the **View** tab, select the **Properties** check box.</span></span>  
  
5.  <span data-ttu-id="38bae-219">在 "属性" 窗格中找到 "WritingMode" 属性。</span><span class="sxs-lookup"><span data-stu-id="38bae-219">Locate the WritingMode property in the Properties pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="38bae-220">对“属性”窗格中的属性进行分类时，WritingMode 位于“本地化”类别中\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="38bae-220">When the properties in the Properties pane are organized into categories, WritingMode is in the **Localization** category.</span></span> <span data-ttu-id="38bae-221">请确保您选择的是单元，而非文本。</span><span class="sxs-lookup"><span data-stu-id="38bae-221">Be sure you have selected the cell and not the text.</span></span> <span data-ttu-id="38bae-222">WritingMode 是文本框的属性，而非文本的属性。</span><span class="sxs-lookup"><span data-stu-id="38bae-222">WritingMode is a property of the text box, not of the text.</span></span>  
  
6.  <span data-ttu-id="38bae-223">在列表框中，单击 " **Rotate270**"。</span><span class="sxs-lookup"><span data-stu-id="38bae-223">In the list box, click **Rotate270**.</span></span>  
  
7.  <span data-ttu-id="38bae-224">在 "**主页**" 选项卡上的 "**段落**" 部分中，单击**中间**和中间按钮，以在单元格的中间**垂直和水平**位置查找文本。</span><span class="sxs-lookup"><span data-stu-id="38bae-224">On the **Home** tab in the **Paragraph** section, click the **Middle** and **Center** buttons to locate the text in the center of the cell both vertically and horizontally.</span></span>  
  
8.  <span data-ttu-id="38bae-225">单击“运行”(**!**)。</span><span class="sxs-lookup"><span data-stu-id="38bae-225">Click Run (**!**).</span></span>  
  
 <span data-ttu-id="38bae-226">现在， `[Territory]` 单元中的文本将从单元的底部到顶部垂直放置。</span><span class="sxs-lookup"><span data-stu-id="38bae-226">Now the text in the `[Territory]` cell runs vertically from the bottom to the top of the cells.</span></span>  
  
##  <a name="displaying-text-with-html-formatting"></a><a name="FormatHTML"></a><span data-ttu-id="38bae-227">用 HTML 格式显示文本</span><span class="sxs-lookup"><span data-stu-id="38bae-227">Displaying Text with HTML Formatting</span></span>  
  
#### <a name="to-display-text-formatted-as-html"></a><span data-ttu-id="38bae-228">以 HTML 格式显示文本</span><span class="sxs-lookup"><span data-stu-id="38bae-228">To display text formatted as HTML</span></span>  
  
1.  <span data-ttu-id="38bae-229">单击 "**设计**" 切换到 "设计" 视图。</span><span class="sxs-lookup"><span data-stu-id="38bae-229">Click **Design** to switch to design view.</span></span>  
  
2.  <span data-ttu-id="38bae-230">在“插入”选项卡上，单击“文本框”，然后在设计图面上，单击并拖动以便在表的下方创建一个宽度为四英寸、高度为三英寸的文本框\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="38bae-230">On the **Insert** tab, click **Text Box**, and then on the design surface, click and drag to create a text box under the table, about four inches wide and three inches tall.</span></span>  
  
3.  <span data-ttu-id="38bae-231">复制此文本并将其粘贴到文本框中：</span><span class="sxs-lookup"><span data-stu-id="38bae-231">Copy this text and paste it into the text box:</span></span>  
  
    ```  
    <h4>Limitations of cascading style sheet attributes</h4>  
          <p>Only a basic set of <b>cascading style sheet (CSS)</b> attributes are defined:</p>  
          <ul><li>  
              text-align, text-indent  
            </li><li>  
              font-family, font-size  
            </li><li>  
              color  
            </li><li>  
              padding, padding-bottom, padding-top, padding-right, padding-left  
            </li><li>  
              font-weight  
            </li></ul>  
    ```  
  
4.  <span data-ttu-id="38bae-232">选择文本框中的所有文本。</span><span class="sxs-lookup"><span data-stu-id="38bae-232">Select all of the text in the text box.</span></span>  
  
     <span data-ttu-id="38bae-233">这是文本的属性，而非文本框的属性，因此，在一个文本框中，你可以混用纯文本和使用 HTML 标记作为样式的文本。</span><span class="sxs-lookup"><span data-stu-id="38bae-233">This is a property of the text, not the text box, so in one text box you could have a mixture of plain text and text that uses HTML tags as styles.</span></span>  
  
5.  <span data-ttu-id="38bae-234">右键单击所有选定文本，然后单击“文本属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="38bae-234">Right-click all of the selected text and click **Text Properties**.</span></span>  
  
6.  <span data-ttu-id="38bae-235">在 "**常规**" 页上的 "**标记类型**" 下，单击 " **Html-将 html 标记解释为样式**"。</span><span class="sxs-lookup"><span data-stu-id="38bae-235">On the **General** page, under **Markup type**, click **HTML - Interpret HTML tags as styles**.</span></span>  
  
7.  <span data-ttu-id="38bae-236">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="38bae-236">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="38bae-237">单击“运行” (**!**) 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="38bae-237">Click Run (**!**) to preview the report.</span></span>  
  
 <span data-ttu-id="38bae-238">文本框中的文本将显示为标题、段落和带项目符号的列表。</span><span class="sxs-lookup"><span data-stu-id="38bae-238">The text in the text box is displayed as a heading, paragraph, and bulleted list.</span></span>  
  
##  <a name="format-currency"></a><a name="FormatCurrency"></a><span data-ttu-id="38bae-239">设置货币格式</span><span class="sxs-lookup"><span data-stu-id="38bae-239">Format Currency</span></span>  
  
#### <a name="to-format-numbers-as-currency"></a><span data-ttu-id="38bae-240">将数字设为货币格式</span><span class="sxs-lookup"><span data-stu-id="38bae-240">To format numbers as currency</span></span>  
  
1.  <span data-ttu-id="38bae-241">单击 "**设计**" 切换到 "设计" 视图。</span><span class="sxs-lookup"><span data-stu-id="38bae-241">Click **Design** to switch to design view.</span></span>  
  
2.  <span data-ttu-id="38bae-242">单击包含 `[Sum(Sales)]`的顶部表单元，按住 Shift 键，然后单击包含 `[Sum(Sales)]`的底部表单元。</span><span class="sxs-lookup"><span data-stu-id="38bae-242">Click the top table cell that contains `[Sum(Sales)]`, hold down the SHIFT key, and click the bottom table cell that contains `[Sum(Sales)]`.</span></span>  
  
3.  <span data-ttu-id="38bae-243">在“开始”选项卡上的“数字”组中，单击“货币”按钮\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="38bae-243">On the **Home** tab, in the **Number** group, click the **Currency** button.</span></span>  
  
4.  <span data-ttu-id="38bae-244"> (可选) 在 "**主页**" 选项卡上的 "**数字**" 组中，单击 "**占位符样式**" 按钮，然后单击 "**示例值**" 以查看数字的格式设置。</span><span class="sxs-lookup"><span data-stu-id="38bae-244">(Optional) On the **Home** tab, in the **Number** group, click the **Placeholder Styles** button and click **Sample Values** to see how the numbers will be formatted.</span></span>  
  
5.  <span data-ttu-id="38bae-245">（可选）在“开始”选项卡上的“数字”组中，单击两次“减少小数位数”按钮，显示不带美分的美元数字\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="38bae-245">(Optional) On the **Home** tab, in the **Number** group, click the **Decrease Decimals** button twice to display dollar figures with no cents.</span></span>  
  
6.  <span data-ttu-id="38bae-246">单击“运行” (**!**) 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="38bae-246">Click Run (**!**) to preview the report.</span></span>  
  
 <span data-ttu-id="38bae-247">报表现在将显示设置了格式的数据并且更易于阅读。</span><span class="sxs-lookup"><span data-stu-id="38bae-247">The report now displays formatted data and is easier to read.</span></span>  
  
##  <a name="save-the-report"></a><a name="Save"></a><span data-ttu-id="38bae-248">保存报表</span><span class="sxs-lookup"><span data-stu-id="38bae-248">Save the Report</span></span>  
 <span data-ttu-id="38bae-249">您可以将报表保存到报表服务器、SharePoint 库或本地计算机。</span><span class="sxs-lookup"><span data-stu-id="38bae-249">You can save reports to a report server, SharePoint library, or your computer.</span></span>  
  
 <span data-ttu-id="38bae-250">在本教程中，将报表保存到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="38bae-250">In this tutorial, save the report to a report server.</span></span> <span data-ttu-id="38bae-251">如果您没有对报表服务器的访问权限，则可以保存到您的计算机。</span><span class="sxs-lookup"><span data-stu-id="38bae-251">If you do not have access to a report server, save the report to your computer.</span></span>  
  
#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="38bae-252">将报表保存到报表服务器</span><span class="sxs-lookup"><span data-stu-id="38bae-252">To save the report on a report server</span></span>  
  
1.  <span data-ttu-id="38bae-253">从 **“报表生成器”** 按钮，单击 **“另存为”**。</span><span class="sxs-lookup"><span data-stu-id="38bae-253">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="38bae-254">单击 **“最近使用的站点和服务器”**。</span><span class="sxs-lookup"><span data-stu-id="38bae-254">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="38bae-255">选择或键入您拥有保存报表权限的报表服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="38bae-255">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="38bae-256">此时将显示“正在连接到报表服务器”消息。</span><span class="sxs-lookup"><span data-stu-id="38bae-256">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="38bae-257">当连接完成时，您将看到报表服务器管理员指定为报表默认位置的报表文件夹的内容。</span><span class="sxs-lookup"><span data-stu-id="38bae-257">When the connection is complete, you see the contents of the report folder that the report server administrator specified as the default location for reports.</span></span>  
  
4.  <span data-ttu-id="38bae-258">在“名称”中，用选择的名称替换默认名称\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="38bae-258">In **Name**, replace the default name with a name of your choosing.</span></span>  
  
5.  <span data-ttu-id="38bae-259">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="38bae-259">Click **Save**.</span></span>  
  
 <span data-ttu-id="38bae-260">报表即已保存至报表服务器。</span><span class="sxs-lookup"><span data-stu-id="38bae-260">The report is saved to the report server.</span></span> <span data-ttu-id="38bae-261">您连接的报表服务器的名称将显示在窗口底部的状态栏中。</span><span class="sxs-lookup"><span data-stu-id="38bae-261">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
#### <a name="to-save-the-report-on-your-computer"></a><span data-ttu-id="38bae-262">将报表保存到计算机上</span><span class="sxs-lookup"><span data-stu-id="38bae-262">To save the report on your computer</span></span>  
  
1.  <span data-ttu-id="38bae-263">从 **“报表生成器”** 按钮，单击 **“另存为”**。</span><span class="sxs-lookup"><span data-stu-id="38bae-263">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="38bae-264">单击 **“桌面”**、 **“我的文档”** 或 **“我的电脑”**，然后浏览到要将报表保存到的文件夹。</span><span class="sxs-lookup"><span data-stu-id="38bae-264">Click **Desktop**, **My Documents**, or **My computer**, and then browse to the folder where you want to save the report.</span></span>  
  
3.  <span data-ttu-id="38bae-265">在“名称”中，用选择的名称替换默认名称\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="38bae-265">In **Name**, replace the default name with a name of your choosing.</span></span>  
  
4.  <span data-ttu-id="38bae-266">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="38bae-266">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="38bae-267">后续步骤</span><span class="sxs-lookup"><span data-stu-id="38bae-267">Next Steps</span></span>  
 <span data-ttu-id="38bae-268">可以通过多种方式设置文本格式报表生成器[教程：创建自由格式的报表 &#40;报表生成器&#41;](../reporting-services/tutorial-creating-a-free-form-report-report-builder.md)包含更多示例。</span><span class="sxs-lookup"><span data-stu-id="38bae-268">There are many ways to format text in Report Builder [Tutorial: Creating a Free Form Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-free-form-report-report-builder.md) contains more examples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38bae-269">另请参阅</span><span class="sxs-lookup"><span data-stu-id="38bae-269">See Also</span></span>  
 <span data-ttu-id="38bae-270">[教程 &#40;报表生成器&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="38bae-270">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 <span data-ttu-id="38bae-271">[&#40;报表生成器和 SSRS 的格式设置报表项&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="38bae-271">[Formatting Report Items &#40;Report Builder and SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="38bae-272">SQL Server 2014 中的报表生成器</span><span class="sxs-lookup"><span data-stu-id="38bae-272">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
