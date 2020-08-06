---
title: 教程：表达式简介 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2d05ef4c-5f91-48b2-8795-f0a201a0b3cc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 62a815800dba0730052eb812124d4561d031d0e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692211"
---
# <a name="tutorial-introducing-expressions"></a><span data-ttu-id="1ec61-102">教程：表达式简介</span><span class="sxs-lookup"><span data-stu-id="1ec61-102">Tutorial: Introducing Expressions</span></span>
  <span data-ttu-id="1ec61-103">表达式帮助您创建功能强大、灵活的报表。</span><span class="sxs-lookup"><span data-stu-id="1ec61-103">Expressions help you create powerful and flexible reports.</span></span> <span data-ttu-id="1ec61-104">本教程指导您创建和实现使用常用函数和运算符的表达式。</span><span class="sxs-lookup"><span data-stu-id="1ec61-104">This tutorial teaches you to create and implement expressions that use common functions and operators.</span></span> <span data-ttu-id="1ec61-105">您将使用 "**表达式**" 对话框编写表达式来连接名称值、在单独的数据集中查找值、基于字段值显示不同的图片等。</span><span class="sxs-lookup"><span data-stu-id="1ec61-105">You will use the **Expression** dialog box to write expressions that concatenate name values, look up values in a separate dataset, display different pictures based on field values, and so on.</span></span>  
  
 <span data-ttu-id="1ec61-106">报表是一个条纹形式的报表，用白色和彩色交替显示行颜色。</span><span class="sxs-lookup"><span data-stu-id="1ec61-106">The report is a barred report with alternating row colors in white and a color.</span></span> <span data-ttu-id="1ec61-107">报表包括用于选择非白色行的颜色的参数。</span><span class="sxs-lookup"><span data-stu-id="1ec61-107">The report includes a parameter for selecting the color of the non-white rows.</span></span>  
  
 <span data-ttu-id="1ec61-108">下图显示与您将创建的报表类似的报表。</span><span class="sxs-lookup"><span data-stu-id="1ec61-108">The following illustration shows a report similar to the one you will create.</span></span>  
  
 <span data-ttu-id="1ec61-109">![rs_ExpressionsTutorial](../../2014/tutorials/media/rs-expressionstutorial.gif "rs_ExpressionsTutorial")</span><span class="sxs-lookup"><span data-stu-id="1ec61-109">![rs_ExpressionsTutorial](../../2014/tutorials/media/rs-expressionstutorial.gif "rs_ExpressionsTutorial")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="1ec61-110">你将学习的内容</span><span class="sxs-lookup"><span data-stu-id="1ec61-110">What You Will Learn</span></span>  
 <span data-ttu-id="1ec61-111">在本教程中，您将学习如何执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="1ec61-111">In this tutorial you will learn how to do the following:</span></span>  
  
1.  [<span data-ttu-id="1ec61-112">使用表向导或矩阵向导创建表报表和数据集</span><span class="sxs-lookup"><span data-stu-id="1ec61-112">Create a Table Report and Dataset from the Table or Matrix Wizard</span></span>](#Setup)  
  
2.  [<span data-ttu-id="1ec61-113">更新数据源和数据集的默认名称</span><span class="sxs-lookup"><span data-stu-id="1ec61-113">Update Default Names of the Data Source and Dataset</span></span>](#UpdateNames)  
  
3.  [<span data-ttu-id="1ec61-114">显示名字、首字母和姓氏</span><span class="sxs-lookup"><span data-stu-id="1ec61-114">Display First Name, Initial, and Last Name</span></span>](#Concatenate)  
  
4.  [<span data-ttu-id="1ec61-115">使用图像显示性别</span><span class="sxs-lookup"><span data-stu-id="1ec61-115">Use Images to Display Gender</span></span>](#Gender)  
  
5.  [<span data-ttu-id="1ec61-116">查找 CountryRegion 名称</span><span class="sxs-lookup"><span data-stu-id="1ec61-116">Look Up CountryRegion Name</span></span>](#Lookup)  
  
6.  [<span data-ttu-id="1ec61-117">计算自上次采购后的天数</span><span class="sxs-lookup"><span data-stu-id="1ec61-117">Count Days Since Last Purchase</span></span>](#Count)  
  
7.  [<span data-ttu-id="1ec61-118">使用指示器显示销售情况对比</span><span class="sxs-lookup"><span data-stu-id="1ec61-118">Use an Indicator to Show Sales Comparison</span></span>](#Indicator)  
  
8.  [<span data-ttu-id="1ec61-119">使报表成为 "绿色条" 报表</span><span class="sxs-lookup"><span data-stu-id="1ec61-119">Make the Report a "Green Bar" Report</span></span>](#GreenBar)  
  
### <a name="other-optional-steps"></a><span data-ttu-id="1ec61-120">其他可选步骤</span><span class="sxs-lookup"><span data-stu-id="1ec61-120">Other Optional Steps</span></span>  
  
-   [<span data-ttu-id="1ec61-121">设置日期列的格式</span><span class="sxs-lookup"><span data-stu-id="1ec61-121">Format Date Column</span></span>](#DateFormat)  
  
-   [<span data-ttu-id="1ec61-122">添加报表标题</span><span class="sxs-lookup"><span data-stu-id="1ec61-122">Add a Report Title</span></span>](#Title)  
  
-   [<span data-ttu-id="1ec61-123">保存报表</span><span class="sxs-lookup"><span data-stu-id="1ec61-123">Save the Report</span></span>](#Save)  
  
 <span data-ttu-id="1ec61-124">本教程的预计学时：30 分钟。</span><span class="sxs-lookup"><span data-stu-id="1ec61-124">Estimated time to complete this tutorial: 30 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ec61-125">要求</span><span class="sxs-lookup"><span data-stu-id="1ec61-125">Requirements</span></span>  
 <span data-ttu-id="1ec61-126">有关要求的信息，请参阅[教程先决条件（报表生成器）](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="1ec61-126">For information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-table-report-and-dataset-from-the-table-or-matrix-wizard"></a><a name="Setup"></a><span data-ttu-id="1ec61-127">1. 使用表或矩阵向导创建表报表和数据集</span><span class="sxs-lookup"><span data-stu-id="1ec61-127">1. Create a Table Report and Dataset from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="1ec61-128">创建表报表、数据源和数据集。</span><span class="sxs-lookup"><span data-stu-id="1ec61-128">Create a table report, a data source, and a dataset.</span></span> <span data-ttu-id="1ec61-129">在设计表的布局时，将只包含若干字段。</span><span class="sxs-lookup"><span data-stu-id="1ec61-129">When you lay out the table, you will include only a few fields.</span></span> <span data-ttu-id="1ec61-130">完成向导后，您将手动添加列。</span><span class="sxs-lookup"><span data-stu-id="1ec61-130">After you complete the wizard you will manually add columns.</span></span> <span data-ttu-id="1ec61-131">使用该向导可以方便地对表进行布局和应用样式。</span><span class="sxs-lookup"><span data-stu-id="1ec61-131">The wizard makes it easy for you to lay out the table and apply a style.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ec61-132">在本教程中，由于查询包含了数据值，因此它不需要外部数据源。</span><span class="sxs-lookup"><span data-stu-id="1ec61-132">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="1ec61-133">这样，查询就会非常长。</span><span class="sxs-lookup"><span data-stu-id="1ec61-133">This makes the query quite long.</span></span> <span data-ttu-id="1ec61-134">在业务环境中，查询不会包含数据。</span><span class="sxs-lookup"><span data-stu-id="1ec61-134">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="1ec61-135">本教程中的查询仅供学习使用。</span><span class="sxs-lookup"><span data-stu-id="1ec61-135">This is for learning purposes only.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ec61-136">在本教程中，将向导的多个步骤合并为一个过程。</span><span class="sxs-lookup"><span data-stu-id="1ec61-136">In this tutorial, the steps for the wizard are consolidated into one procedure.</span></span> <span data-ttu-id="1ec61-137">有关如何浏览到报表服务器、选择数据源和创建数据集的分步说明，请参阅本系列中的第一个教程：[教程：创建基本表报表（报表生成器）](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="1ec61-137">For step-by-step instructions about how to browse to a report server, choose a data source, and create a dataset, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
#### <a name="to-create-a-new-table-report"></a><span data-ttu-id="1ec61-138">创建新的表报表</span><span class="sxs-lookup"><span data-stu-id="1ec61-138">To create a new table report</span></span>  
  
1.  <span data-ttu-id="1ec61-139">单击 "**开始**"，指向 "**程序**"，单击 " [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **报表生成器**"，然后单击 "**报表生成器**"。</span><span class="sxs-lookup"><span data-stu-id="1ec61-139">Click **Start**, point to **Programs**, click [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]**Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="1ec61-140">此时将显示 "**入门**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="1ec61-140">The **Getting Started** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1ec61-141">如果未显示 "**入门**" 对话框，请在 "**报表生成器**" 按钮中单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="1ec61-141">If the **Getting Started** dialog box does not appear, from the **Report Builder** button, click **New**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1ec61-142">如果你更喜欢使用报表生成器的 ClickOnce 版本，请打开报表管理器并单击 "**报表生成器**"，或跳到已启用 Reporting Services 的内容类型（如报表）的 SharePoint 站点，然后在共享文档库的 "**文档**" 选项卡上的 "**新建文档**" 菜单上单击 "**报表生成器报表**"。</span><span class="sxs-lookup"><span data-stu-id="1ec61-142">If you prefer using the ClickOnce version of Report Builder, open Report Manager and click **Report Builder**, or go to a SharePoint site on which Reporting Services content types such as reports are enabled and click **Report Builder Report** on the **New Document** menu on the **Documents** tab of a shared documents library.</span></span>  
  
2.  <span data-ttu-id="1ec61-143">在左窗格中，确认已选中 **“新建报表”** 。</span><span class="sxs-lookup"><span data-stu-id="1ec61-143">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="1ec61-144">在右窗格中，单击“表或矩阵向导”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-144">In the right pane, click **Table or Matrix Wizard**.</span></span>  
  
4.  <span data-ttu-id="1ec61-145">在“选择数据集”页上，单击“创建数据集”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-145">On the **Choose a dataset** page, click **Create a dataset**.</span></span>  
  
5.  <span data-ttu-id="1ec61-146">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="1ec61-146">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="1ec61-147">在“选择数据源的连接”\*\*\*\* 页上，选择类型为“SQL Server”\*\*\*\* 的数据源。</span><span class="sxs-lookup"><span data-stu-id="1ec61-147">On the **Choose a connection to a data source** page, select a data source that is type **SQL Server**.</span></span> <span data-ttu-id="1ec61-148">从列表中选择一个数据源或浏览到报表服务器以选择一个数据源。</span><span class="sxs-lookup"><span data-stu-id="1ec61-148">Select a data source from the list or browse to the report server to select one.</span></span>  
  
7.  <span data-ttu-id="1ec61-149">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="1ec61-149">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="1ec61-150">在“设计查询”页上，单击“编辑为文本”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-150">On the **Design a query** page, click **Edit as Text**.</span></span>  
  
9. <span data-ttu-id="1ec61-151">将以下查询粘贴到查询窗格中：</span><span class="sxs-lookup"><span data-stu-id="1ec61-151">Paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT 'Lauren' AS FirstName,'Johnson' AS LastName, 'American Samoa' AS StateProvince, 1 AS CountryRegionID,'Unknown' AS Gender, CAST(9996.60 AS money) AS YTDPurchase, CAST('2010-6-10' AS date) AS LastPurchase  
    UNION SELECT'Warren' AS FirstName, 'Pal' AS LastName, 'New South Wales' AS StateProvince, 2 AS CountryRegionID, 'Male' AS Gender, CAST(5747.25 AS money) AS YTDPurchase, CAST('2010-7-3' AS date) AS LastPurchase  
    UNION SELECT 'Fernando' AS FirstName, 'Ross' AS LastName, 'Alberta' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(9248.15 AS money) AS YTDPurchase, CAST('2010-10-17' AS date) AS LastPurchase  
    UNION SELECT 'Rob' AS FirstName, 'Caron' AS LastName, 'Northwest Territories' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(742.50 AS money) AS YTDPurchase, CAST('2010-4-29' AS date) AS LastPurchase  
    UNION SELECT 'James' AS FirstName, 'Bailey' AS LastName, 'British Columbia' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(1147.50 AS money) AS YTDPurchase, CAST('2010-6-15' AS date) AS LastPurchase  
    UNION SELECT  'Bridget' AS FirstName, 'She' AS LastName, 'Hamburg' AS StateProvince, 4 AS CountryRegionID, 'Female' AS Gender, CAST(7497.30 AS money) AS YTDPurchase, CAST('2010-5-10' AS date) AS LastPurchase  
    UNION SELECT 'Alexander' AS FirstName, 'Martin' AS LastName, 'Saxony' AS StateProvince, 4 AS CountryRegionID, 'Male' AS Gender, CAST(2997.60 AS money) AS YTDPurchase, CAST('2010-11-19' AS date) AS LastPurchase  
    UNION SELECT 'Yolanda' AS FirstName, 'Sharma' AS LastName ,'Micronesia' AS StateProvince, 5 AS CountryRegionID, 'Female' AS Gender, CAST(3247.95 AS money) AS YTDPurchase, CAST('2010-8-23' AS date) AS LastPurchase  
    UNION SELECT 'Marc' AS FirstName, 'Zimmerman' AS LastName, 'Moselle' AS StateProvince, 6 AS CountryRegionID, 'Male' AS Gender, CAST(1200.00 AS money) AS YTDPurchase, CAST('2010-11-16' AS date) AS LastPurchase  
    UNION SELECT 'Katherine' AS FirstName, 'Abel' AS LastName, 'Moselle' AS StateProvince, 6 AS CountryRegionID, 'Female' AS Gender, CAST(2025.00 AS money) AS YTDPurchase, CAST('2010-12-1' AS date) AS LastPurchase  
    UNION SELECT 'Nicolas' as FirstName, 'Anand' AS LastName, 'Seine (Paris)' AS StateProvince, 6 AS CountryRegionID, 'Male' AS Gender, CAST(1425.00 AS money) AS YTDPurchase, CAST('2010-12-11' AS date) AS LastPurchase  
    UNION SELECT 'James' AS FirstName, 'Peters' AS LastName, 'England' AS StateProvince, 12 AS CountryRegionID, 'Male' AS Gender, CAST(887.50 AS money) AS YTDPurchase, CAST('2010-8-15' AS date) AS LastPurchase  
    UNION SELECT 'Alison' AS FirstName, 'Nath' AS LastName, 'Alaska' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(607.50 AS money) AS YTDPurchase, CAST('2010-10-13' AS date) AS LastPurchase  
    UNION SELECT 'Grace' AS FirstName, 'Patterson' AS LastName, 'Kansas' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(1215.00 AS money) AS YTDPurchase, CAST('2010-10-18' AS date) AS LastPurchase  
    UNION SELECT 'Bobby' AS FirstName, 'Sanchez' AS LastName, 'North Dakota' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(6191.00 AS money) AS YTDPurchase, CAST('2010-9-17' AS date) AS LastPurchase  
    UNION SELECT 'Charles' AS FirstName, 'Reed' AS LastName, 'Nebraska' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(8772.00 AS money) AS YTDPurchase, CAST('2010-8-27' AS date) AS LastPurchase  
    UNION SELECT 'Orlando' AS FirstName, 'Romeo' AS LastName, 'Texas' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(8578.00 AS money) AS YTDPurchase, CAST('2010-7-29' AS date) AS LastPurchase  
    UNION SELECT 'Cynthia' AS FirstName, 'Randall' AS LastName, 'Utah' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(7218.10 AS money) AS YTDPurchase, CAST('2010-1-11' AS date) AS LastPurchase  
    UNION SELECT 'Rebecca' AS FirstName, 'Roberts' AS LastName, 'Washington' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(8357.80 AS money) AS YTDPurchase, CAST('2010-10-28' AS date) AS LastPurchase  
    UNION SELECT 'Cristian' AS FirstName, 'Petulescu' AS LastName, 'Wisconsin' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(3470.00 AS money) AS YTDPurchase, CAST('2010-11-30' AS date) AS LastPurchase  
    UNION SELECT 'Cynthia' AS FirstName, 'Randall' AS LastName, 'Utah' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(7218.10 AS money) AS YTDPurchase, CAST('2010-1-11' AS date) AS LastPurchase  
    UNION SELECT 'Rebecca' AS FirstName, 'Roberts' AS LastName, 'Washington' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(8357.80 AS money) AS YTDPurchase, CAST('2010-10-28' AS date) AS LastPurchase  
    UNION SELECT 'Cristian' AS FirstName, 'Petulescu' AS LastName, 'Wisconsin' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(3470.00 AS money) AS YTDPurchase, CAST('2010-11-30' AS date) AS LastPurchase  
    ```  
  
     <span data-ttu-id="1ec61-152">该查询指定列名称，这些名称包括出生日期、名字、姓氏、省/市/自治区、国家/地区标识符、性别和年初至今的采购信息。</span><span class="sxs-lookup"><span data-stu-id="1ec61-152">The query specifies column names that include a birth date, first name, last name, state or province, country/region identifier, gender, and year-to-date purchases.</span></span>  
  
10. <span data-ttu-id="1ec61-153">在查询设计器工具栏上，单击 "**运行** (**！**) "。</span><span class="sxs-lookup"><span data-stu-id="1ec61-153">On the query designer toolbar, click **Run** (**!**).</span></span> <span data-ttu-id="1ec61-154">结果集显示 20 行的数据并包括以下列：FirstName、LastName、StateProvince、CountryRegionID、Gender、YTDPurchase 和 LastPurchase。</span><span class="sxs-lookup"><span data-stu-id="1ec61-154">The result set displays 20 rows of data and includes the following columns: FirstName, LastName, StateProvince, CountryRegionID, Gender, YTDPurchase, and LastPurchase.</span></span>  
  
11. <span data-ttu-id="1ec61-155">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="1ec61-155">Click **Next**.</span></span>  
  
12. <span data-ttu-id="1ec61-156">在“排列字段”页上，将以下字段按指定顺序从“可用字段”列表拖到“值”列表\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-156">On the **Arrange fields** page, drag the following fields, in the specified order, from the **Available Fields** list to the **Values** list.</span></span>  
  
    -   <span data-ttu-id="1ec61-157">StateProvince</span><span class="sxs-lookup"><span data-stu-id="1ec61-157">StateProvince</span></span>  
  
    -   <span data-ttu-id="1ec61-158">CountryRegionID</span><span class="sxs-lookup"><span data-stu-id="1ec61-158">CountryRegionID</span></span>  
  
    -   <span data-ttu-id="1ec61-159">LastPurchase</span><span class="sxs-lookup"><span data-stu-id="1ec61-159">LastPurchase</span></span>  
  
    -   <span data-ttu-id="1ec61-160">YTDPurchase</span><span class="sxs-lookup"><span data-stu-id="1ec61-160">YTDPurchase</span></span>  
  
     <span data-ttu-id="1ec61-161">因为 CountryRegionID 和 YTDPurchase 包含数值数据，所以，SUM 聚合将默认应用于这两个字段。</span><span class="sxs-lookup"><span data-stu-id="1ec61-161">Because the CountryRegionID and YTDPurchase contain numeric data, the SUM aggregate is applied to them by default.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1ec61-162">FirstName 和 LastName 字段不包括在内。</span><span class="sxs-lookup"><span data-stu-id="1ec61-162">The FirstName and LastName fields are not included.</span></span> <span data-ttu-id="1ec61-163">您将在后面的步骤中添加这两个字段。</span><span class="sxs-lookup"><span data-stu-id="1ec61-163">You will add them in a later step.</span></span>  
  
13. <span data-ttu-id="1ec61-164">在 "**值**" 列表中，右键单击 `CountryRegionID` 并单击 " **Sum** " 选项。</span><span class="sxs-lookup"><span data-stu-id="1ec61-164">In the **Values** list, right-click `CountryRegionID` and click the **Sum** option.</span></span>  
  
     <span data-ttu-id="1ec61-165">Sum 不再应用于 CountryRegionID。</span><span class="sxs-lookup"><span data-stu-id="1ec61-165">Sum is no longer applied to CountryRegionID.</span></span>  
  
14. <span data-ttu-id="1ec61-166">在“值”列表中，右键单击“YTDPurchase”，然后单击“Sum”选项\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-166">In the **Values** list, right-click **YTDPurchase** and click the **Sum** option.</span></span>  
  
     <span data-ttu-id="1ec61-167">Sum 不再应用于 YTDPurchase。</span><span class="sxs-lookup"><span data-stu-id="1ec61-167">Sum is no longer applied to YTDPurchase.</span></span>  
  
15. <span data-ttu-id="1ec61-168">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="1ec61-168">Click **Next**.</span></span>  
  
16. <span data-ttu-id="1ec61-169">在“选择布局”\*\*\*\* 页上，单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-169">On the **Choose the layout** page, click **Next**.</span></span>  
  
17. <span data-ttu-id="1ec61-170">在 "**选择样式**" 页上，单击 "**石板**"，然后单击 "**完成**"。</span><span class="sxs-lookup"><span data-stu-id="1ec61-170">On the **Choose a style** page, click **Slate**, and then click **Finish**.</span></span>  
  
##  <a name="2-update-default-names-of-the-data-source-and-dataset"></a><a name="UpdateNames"></a><span data-ttu-id="1ec61-171">2. 更新数据源和数据集的默认名称</span><span class="sxs-lookup"><span data-stu-id="1ec61-171">2. Update Default Names of the Data Source and Dataset</span></span>  
  
#### <a name="to-update-the-default-name-of-the-data-source"></a><span data-ttu-id="1ec61-172">更新数据源的默认名称</span><span class="sxs-lookup"><span data-stu-id="1ec61-172">To update the default name of the data source</span></span>  
  
1.  <span data-ttu-id="1ec61-173">在“报表数据”窗格中，展开“数据源”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-173">In the Report Data pane, expand **Data Sources**.</span></span>  
  
2.  <span data-ttu-id="1ec61-174">右键单击“DataSource1”\*\*\*\*，然后单击“数据源属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-174">Right-click **DataSource1** and click **Data Source Properties.**</span></span>  
  
3.  <span data-ttu-id="1ec61-175">在“名称”框中，键入“ExpressionsDataSource”\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1ec61-175">In the **Name** box, type **ExpressionsDataSource**</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-update-the-default-name-of-the-dataset"></a><span data-ttu-id="1ec61-176">更新数据集的默认名称</span><span class="sxs-lookup"><span data-stu-id="1ec61-176">To update the default name of the dataset</span></span>  
  
1.  <span data-ttu-id="1ec61-177">在“报表数据”窗格中，展开“数据集”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-177">In the Report Data pane, expand **Datasets**.</span></span>  
  
2.  <span data-ttu-id="1ec61-178">右键单击“DataSet1”\*\*\*\*，然后单击“数据集属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-178">Right-click **DataSet1** and click **Dataset Properties.**</span></span>  
  
3.  <span data-ttu-id="1ec61-179">在“名称”\*\*\*\* 框中，键入 **Expressions**</span><span class="sxs-lookup"><span data-stu-id="1ec61-179">In the **Name** box, type **Expressions**</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="3-display-first-name-initial-and-last-name"></a><a name="Concatenate"></a><span data-ttu-id="1ec61-180">3. 显示名字、初始名称和姓氏</span><span class="sxs-lookup"><span data-stu-id="1ec61-180">3. Display First Name, Initial, and Last Name</span></span>  
 <span data-ttu-id="1ec61-181">在表达式中使用 **Left** 函数和 **Concatenate** (**&**) 运算符（其计算结果为包括首字母和姓氏的名称）。</span><span class="sxs-lookup"><span data-stu-id="1ec61-181">Use the **Left** function and the **Concatenate** (**&**) operator in an expression that evaluates to a name that includes an initial and a last name.</span></span> <span data-ttu-id="1ec61-182">你可以逐步生成表达式，也可以跳过一些步骤，将表达式从教程复制/粘贴到“表达式”\*\*\*\* 对话框中。</span><span class="sxs-lookup"><span data-stu-id="1ec61-182">You can build the expression step by step or skip ahead in the procedure and copy/paste the expression from the tutorial into the **Expression** dialog box.</span></span>  
  
#### <a name="to-add-the-name-column"></a><span data-ttu-id="1ec61-183">添加 Name 列</span><span class="sxs-lookup"><span data-stu-id="1ec61-183">To add the Name column</span></span>  
  
1.  <span data-ttu-id="1ec61-184">右键单击“StateProvince”\*\*\*\* 列，指向“插入列”\*\*\*\*，然后单击“左”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-184">Right-click the **StateProvince** column, point to **Insert Column**, and then click **Left**.</span></span>  
  
     <span data-ttu-id="1ec61-185">一个新列添加到“StateProvince”\*\*\*\* 列的左侧。</span><span class="sxs-lookup"><span data-stu-id="1ec61-185">A new column is added to the left of the **StateProvince** column.</span></span>  
  
2.  <span data-ttu-id="1ec61-186">单击新列的标题，然后键入 **Name**</span><span class="sxs-lookup"><span data-stu-id="1ec61-186">Click the title of the new column and type **Name**</span></span>  
  
3.  <span data-ttu-id="1ec61-187">右键单击“Name”\*\*\*\* 列的数据单元，然后单击“表达式”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-187">Right-click the data cell for the **Name** column and click **Expression**.</span></span>  
  
4.  <span data-ttu-id="1ec61-188">在“表达式”\*\*\*\* 对话框中，展开“常见函数”\*\*\*\*，然后单击“文本”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-188">In the **Expression** dialog box, expand **Common Functions**, and then click **Text**.</span></span>  
  
5.  <span data-ttu-id="1ec61-189">在“项”列表中，双击“左”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-189">In the **Item** list, double-click **Left**.</span></span>  
  
     <span data-ttu-id="1ec61-190">将 **Left** 函数添加到表达式中。</span><span class="sxs-lookup"><span data-stu-id="1ec61-190">The **Left** function is added to the expression.</span></span>  
  
6.  <span data-ttu-id="1ec61-191">在“类别”\*\*\*\* 列表中，单击“字段(表达式)”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-191">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
7.  <span data-ttu-id="1ec61-192">在“值”\*\*\*\* 列表中，双击 **FirstName**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-192">In the **Values** list, double-click **FirstName**.</span></span>  
  
8.  <span data-ttu-id="1ec61-193">键入 **, 1)**</span><span class="sxs-lookup"><span data-stu-id="1ec61-193">Type **, 1)**</span></span>  
  
     <span data-ttu-id="1ec61-194">此表达式将从 **FirstName** 值提取一个字符，从左侧开始计数。</span><span class="sxs-lookup"><span data-stu-id="1ec61-194">This expression extracts one character from the **FirstName** value, counting from the left.</span></span>  
  
9. <span data-ttu-id="1ec61-195">键入 **&" "&**</span><span class="sxs-lookup"><span data-stu-id="1ec61-195">Type **&" "&**</span></span>  
  
10. <span data-ttu-id="1ec61-196">在“值”\*\*\*\* 列表中，双击 **LastName**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-196">In the **Values** list, double-click **LastName**.</span></span>  
  
     <span data-ttu-id="1ec61-197">完成的表达式： `=Left(Fields!FirstName.Value, 1) &" "& Fields!LastName.Value`</span><span class="sxs-lookup"><span data-stu-id="1ec61-197">The completed expression: `=Left(Fields!FirstName.Value, 1) &" "& Fields!LastName.Value`</span></span>  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. <span data-ttu-id="1ec61-198">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="1ec61-198">Click **Run** to preview the report.</span></span>  
  
##  <a name="4-use-images-to-display-gender"></a><a name="Gender"></a><span data-ttu-id="1ec61-199">4. 使用图像显示性别</span><span class="sxs-lookup"><span data-stu-id="1ec61-199">4. Use Images to Display Gender</span></span>  
 <span data-ttu-id="1ec61-200">使用图像可以显示人员的性别，并且通过使用第三个图像标识未知性别值。</span><span class="sxs-lookup"><span data-stu-id="1ec61-200">Use images to show the gender of a person, and identify unknown gender values by using a third image.</span></span> <span data-ttu-id="1ec61-201">您将向报表添加三个隐藏的图像和一个用于显示这些图像的新列，然后基于“性别”字段的值确定在列中显示的图像。</span><span class="sxs-lookup"><span data-stu-id="1ec61-201">You will add to the report three hidden images and a new column to display the images, and then determine the image that appears in the column based on the value of the Gender field.</span></span>  
  
 <span data-ttu-id="1ec61-202">在使报表成为条纹形式报表时，若要将颜色应用于包含图像的表单元，需要添加一个矩形，然后将图像添加到该矩形。</span><span class="sxs-lookup"><span data-stu-id="1ec61-202">To apply a color to the table cell that contains the image when you make the report a barred report, you will add a rectangle and then add the image to the rectangle.</span></span> <span data-ttu-id="1ec61-203">您需要使用矩形，因为背景色可以应用于矩形，但不能应用于图像。</span><span class="sxs-lookup"><span data-stu-id="1ec61-203">You need to use a rectangle because you can apply a background color to a rectangle, but not to an image.</span></span>  
  
 <span data-ttu-id="1ec61-204">本教程使用随 Windows 一起安装的图像，但您可以使用任何可用的图像。</span><span class="sxs-lookup"><span data-stu-id="1ec61-204">The tutorial uses images that are installed with Windows, but you can use any images available to you.</span></span> <span data-ttu-id="1ec61-205">您将使用嵌入图像，但这些图像无需安装在本地计算机或报表服务器上。</span><span class="sxs-lookup"><span data-stu-id="1ec61-205">You will use embedded images, and they do not need to be installed on your local computer or the report server.</span></span>  
  
#### <a name="to-add-images-to-the-report-body"></a><span data-ttu-id="1ec61-206">向报表正文添加图像</span><span class="sxs-lookup"><span data-stu-id="1ec61-206">To add images to the report body</span></span>  
  
1.  <span data-ttu-id="1ec61-207">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="1ec61-207">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="1ec61-208">在功能区的“插入”\*\*\*\* 选项卡上，单击“图像”\*\*\*\*，然后在表下面的报表正文中单击。</span><span class="sxs-lookup"><span data-stu-id="1ec61-208">On the **Insert** tab of the ribbon, click **Image** and then click in the report body, below the table.</span></span>  
  
     <span data-ttu-id="1ec61-209">将打开“图像属性”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="1ec61-209">The **Image Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="1ec61-210">单击“导入”\*\*\*\* 并导航到 C:\Users\Public\Public Pictures\Sample Pictures。</span><span class="sxs-lookup"><span data-stu-id="1ec61-210">Click **Import** and navigate to C:\Users\Public\Public Pictures\Sample Pictures.</span></span>  
  
4.  <span data-ttu-id="1ec61-211">单击“Penguins.JPG”，然后单击“打开”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-211">Click Penguins.JPG and click **Open**.</span></span>  
  
     <span data-ttu-id="1ec61-212">在“图像属性”\*\*\*\* 对话框中，单击“可见性”\*\*\*\*，然后单击“隐藏”\*\*\*\* 选项。</span><span class="sxs-lookup"><span data-stu-id="1ec61-212">In the **Image Properties** dialog box, click **Visibility** and then click the **Hide** option.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="1ec61-213">重复执行第 2 步到第 5 步，但选择 Koala.JPG。</span><span class="sxs-lookup"><span data-stu-id="1ec61-213">Repeat steps 2 through 5, but choose Koala.JPG.</span></span>  
  
7.  <span data-ttu-id="1ec61-214">重复执行第 2 步到第 5 步，但选择 Tulips.JPG。</span><span class="sxs-lookup"><span data-stu-id="1ec61-214">Repeat steps 2 through 5, but choose Tulips.JPG.</span></span>  
  
#### <a name="to-add-the-gender-column"></a><span data-ttu-id="1ec61-215">添加 Gender 列</span><span class="sxs-lookup"><span data-stu-id="1ec61-215">To add the Gender column</span></span>  
  
1.  <span data-ttu-id="1ec61-216">右键单击“名称”\*\*\*\* 列，指向“插入列”\*\*\*\*，然后单击“右”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-216">Right-click the **Name** column, point to **Insert Column**, and then click **Right**.</span></span>  
  
     <span data-ttu-id="1ec61-217">一个新列添加到 **Name** 列的右侧。</span><span class="sxs-lookup"><span data-stu-id="1ec61-217">A new column is added to the right of the **Name** column.</span></span>  
  
2.  <span data-ttu-id="1ec61-218">单击新列的标题，然后键入 **Gender**</span><span class="sxs-lookup"><span data-stu-id="1ec61-218">Click the title of the new column and type **Gender**</span></span>  
  
#### <a name="to-add-a-rectangle"></a><span data-ttu-id="1ec61-219">添加矩形</span><span class="sxs-lookup"><span data-stu-id="1ec61-219">To add a rectangle</span></span>  
  
-   <span data-ttu-id="1ec61-220">在功能区的“插入”\*\*\*\* 选项卡上，单击“矩形”\*\*\*\*，然后在 **Gender** 列的数据单元中单击。</span><span class="sxs-lookup"><span data-stu-id="1ec61-220">On the **Insert** tab of the ribbon, click **Rectangle** and then click in the data cell of the **Gender** column.</span></span>  
  
     <span data-ttu-id="1ec61-221">将在该单元中添加一个矩形。</span><span class="sxs-lookup"><span data-stu-id="1ec61-221">A rectangle is added to the cell.</span></span>  
  
#### <a name="to-add-an-image-to-the-rectangle"></a><span data-ttu-id="1ec61-222">向矩形添加图像</span><span class="sxs-lookup"><span data-stu-id="1ec61-222">To add an image to the rectangle</span></span>  
  
1.  <span data-ttu-id="1ec61-223">在矩形中右键单击，指向“插入”\*\*\*\*，然后单击“图像”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-223">Right-click in the rectangle, point to **Insert**, and then click **Image**.</span></span>  
  
2.  <span data-ttu-id="1ec61-224">在“图像属性”\*\*\*\* 对话框中，单击“使用此图像”\*\*\*\* 旁的向下箭头，然后选择添加的图像之一，例如 Penguins.JPG。</span><span class="sxs-lookup"><span data-stu-id="1ec61-224">In the **Image Properties** dialog box, click the down arrow beside **Use this image**, and select one of the images you added, for example, Penguins.JPG.</span></span>  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-use-images-to-show-gender"></a><span data-ttu-id="1ec61-225">若要使用图像显示性别</span><span class="sxs-lookup"><span data-stu-id="1ec61-225">To use images to show gender</span></span>  
  
1.  <span data-ttu-id="1ec61-226">右键单击 **Gender** 列的数据单元中的图像，然后单击“图像属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-226">Right-click the image in the data cell in the **Gender** column and click **Image Properties**.</span></span>  
  
2.  <span data-ttu-id="1ec61-227">在“图像属性”\*\*\*\* 对话框中，单击“使用此图像”\*\*\*\* 文本框旁边的表达式 **fx**按钮。</span><span class="sxs-lookup"><span data-stu-id="1ec61-227">In the **Image Properties** dialog box, click the expression **fx** button next to the **Use this image** text box.</span></span>  
  
3.  <span data-ttu-id="1ec61-228">在“表达式”\*\*\*\* 对话框中，展开“常见函数”\*\*\*\*，然后单击“程序流”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-228">In the **Expression** dialog box, expand **Common Functions** and click **Program Flow**.</span></span>  
  
4.  <span data-ttu-id="1ec61-229">在“项”列表中，双击“Switch”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-229">In the **Item** list, double-click **Switch**.</span></span>  
  
5.  <span data-ttu-id="1ec61-230">在“类别”\*\*\*\* 列表中，单击“字段(表达式)”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-230">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
6.  <span data-ttu-id="1ec61-231">在“值”\*\*\*\* 列表中，双击 **Gender**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-231">In the **Values** list, double-click **Gender**.</span></span>  
  
7.  <span data-ttu-id="1ec61-232">键入 **="Male", "Koala",**</span><span class="sxs-lookup"><span data-stu-id="1ec61-232">Type **="Male", "Koala",**</span></span>  
  
8.  <span data-ttu-id="1ec61-233">在“值”\*\*\*\* 列表中，双击 **Gender**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-233">In the **Values** list, double-click **Gender**.</span></span>  
  
9. <span data-ttu-id="1ec61-234">键入 **="Female", "Penguins",**</span><span class="sxs-lookup"><span data-stu-id="1ec61-234">Type **="Female", "Penguins",**</span></span>  
  
10. <span data-ttu-id="1ec61-235">在“值”\*\*\*\* 列表中，双击 **Gender**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-235">In the **Values** list, double-click **Gender**.</span></span>  
  
11. <span data-ttu-id="1ec61-236">键入 **="Unknown", "Tulips")**</span><span class="sxs-lookup"><span data-stu-id="1ec61-236">Type **="Unknown", "Tulips")**</span></span>  
  
     <span data-ttu-id="1ec61-237">完成的表达式： `=Switch(Fields!Gender.Value ="Male", "Koala",Fields!Gender.Value ="Female","Penguins",Fields!Gender.Value ="Unknown","Tulips")`</span><span class="sxs-lookup"><span data-stu-id="1ec61-237">The completed expression: `=Switch(Fields!Gender.Value ="Male", "Koala",Fields!Gender.Value ="Female","Penguins",Fields!Gender.Value ="Unknown","Tulips")`</span></span>  
  
12. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
13. <span data-ttu-id="1ec61-238">再次单击“确定”\*\*\*\* 以关闭“图像属性”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="1ec61-238">Click **OK** again to close the **Image Properties** dialog box.</span></span>  
  
14. <span data-ttu-id="1ec61-239">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="1ec61-239">Click **Run** to preview the report.</span></span>  
  
##  <a name="5-look-up-countryregion-name"></a><a name="Lookup"></a><span data-ttu-id="1ec61-240">5. 查找国家/地区名称</span><span class="sxs-lookup"><span data-stu-id="1ec61-240">5. Look Up CountryRegion Name</span></span>  
 <span data-ttu-id="1ec61-241">创建 CountryRegion 数据集，使用“Lookup”\*\*\*\* 函数显示国家/地区的名称，而非国家/地区的标识符。</span><span class="sxs-lookup"><span data-stu-id="1ec61-241">Create the CountryRegion dataset and use the **Lookup** function to display the name of a country/region instead of the identifier of the country/region.</span></span>  
  
#### <a name="to-create-the-countryregion-dataset"></a><span data-ttu-id="1ec61-242">创建 CountryRegion 数据集</span><span class="sxs-lookup"><span data-stu-id="1ec61-242">To create the CountryRegion dataset</span></span>  
  
1.  <span data-ttu-id="1ec61-243">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="1ec61-243">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="1ec61-244">在 "报表数据" 窗格中，单击 "**新建**"，然后单击 "**数据集**"。</span><span class="sxs-lookup"><span data-stu-id="1ec61-244">In the Report Data pane, click **New** and then click **Dataset**.</span></span>  
  
3.  <span data-ttu-id="1ec61-245">单击 **“使用在我的报表中嵌入的数据集”**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-245">Click **Use a dataset embedded in my report**.</span></span>  
  
4.  <span data-ttu-id="1ec61-246">在“数据源”\*\*\*\* 列表中，选择“ExpressionsDataSource”。</span><span class="sxs-lookup"><span data-stu-id="1ec61-246">In the **Data source** list, select ExpressionsDataSource.</span></span>  
  
5.  <span data-ttu-id="1ec61-247">在“名称”框中，键入“CountryRegion”\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1ec61-247">In the **Name** box, type **CountryRegion**</span></span>  
  
6.  <span data-ttu-id="1ec61-248">确保已选择“文本”查询类型，然后单击“查询设计器”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-248">Verify that the **Text** query type is selected and click **Query Designer**.</span></span>  
  
7.  <span data-ttu-id="1ec61-249">单击 **“编辑为文本”**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-249">Click **Edit as Text**.</span></span>  
  
8.  <span data-ttu-id="1ec61-250">复制并将以下查询粘贴到查询窗格中：</span><span class="sxs-lookup"><span data-stu-id="1ec61-250">Copy and paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT 1 AS ID, 'American Samoa' AS CountryRegion  
    UNION SELECT 2 AS CountryRegionID, 'Australia' AS CountryRegion  
    UNION SELECT 3 AS ID, 'Canada' AS CountryRegion  
    UNION SELECT 4 AS ID, 'Germany' AS CountryRegion  
    UNION SELECT 5 AS ID, 'Micronesia' AS CountryRegion  
    UNION SELECT 6 AS ID, 'France' AS CountryRegion  
    UNION SELECT 7 AS ID, 'United States' AS CountryRegion  
    UNION SELECT 8 AS ID, 'Brazil' AS CountryRegion  
    UNION SELECT 9 AS ID, 'Mexico' AS CountryRegion  
    UNION SELECT 10 AS ID, 'Japan' AS CountryRegion  
    UNION SELECT 10 AS ID, 'Australia' AS CountryRegion  
    UNION SELECT 12 AS ID, 'United Kingdom' AS CountryRegion  
    ```  
  
9. <span data-ttu-id="1ec61-251">单击 "**运行** (**！**) 以运行查询。</span><span class="sxs-lookup"><span data-stu-id="1ec61-251">Click **Run** (**!**) to run the query.</span></span>  
  
     <span data-ttu-id="1ec61-252">查询结果是国家/地区标识符和名称。</span><span class="sxs-lookup"><span data-stu-id="1ec61-252">The query results are the country/region identifiers and names.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. <span data-ttu-id="1ec61-253">再次单击“确定”\*\*\*\* 以关闭“数据集属性”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="1ec61-253">Click **OK** again to close the **Dataset Properties** dialog box.</span></span>  
  
#### <a name="to-look-up-values-in-the-countryregion-dataset"></a><span data-ttu-id="1ec61-254">查找 CountryRegion 数据集中的值</span><span class="sxs-lookup"><span data-stu-id="1ec61-254">To look up values in the CountryRegion dataset</span></span>  
  
1.  <span data-ttu-id="1ec61-255">单击“Country Region ID”\*\*\*\* 列标题，删除文本：ID。</span><span class="sxs-lookup"><span data-stu-id="1ec61-255">Click the **Country Region ID** column title and delete the text: ID.</span></span>  
  
2.  <span data-ttu-id="1ec61-256">右键单击“Country Region”\*\*\*\* 列的数据单元，然后单击“表达式”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-256">Right-click the data cell for the **Country Region** column and click **Expression**.</span></span>  
  
3.  <span data-ttu-id="1ec61-257">删除表达式，开头的等号 (=) 除外。</span><span class="sxs-lookup"><span data-stu-id="1ec61-257">Delete the expression except the initial equal (=) sign.</span></span>  
  
     <span data-ttu-id="1ec61-258">剩余表达式为： `=`</span><span class="sxs-lookup"><span data-stu-id="1ec61-258">The remaining expression is: `=`</span></span>  
  
4.  <span data-ttu-id="1ec61-259">在“表达式”\*\*\*\* 对话框中，展开“常见函数”\*\*\*\*，然后单击“杂项”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-259">In the **Expression** dialog box, expand **Common Functions** and click **Miscellaneous**.</span></span>  
  
5.  <span data-ttu-id="1ec61-260">在“项”\*\*\*\* 列表中，双击“Lookup”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-260">In the **Item** list, double-click **Lookup**.</span></span>  
  
6.  <span data-ttu-id="1ec61-261">在“类别”\*\*\*\* 列表中，单击“字段(表达式)”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-261">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
7.  <span data-ttu-id="1ec61-262">在 "**值**" 列表中，双击 `CountryRegionID` 。</span><span class="sxs-lookup"><span data-stu-id="1ec61-262">In the **Values** list, double-click `CountryRegionID`.</span></span>  
  
8.  <span data-ttu-id="1ec61-263">如果鼠标光标不是紧接 `CountryRegionID.Value` 之后，请将光标置于其后。</span><span class="sxs-lookup"><span data-stu-id="1ec61-263">If the cursor is not already immediately after `CountryRegionID.Value`, place it there.</span></span>  
  
9. <span data-ttu-id="1ec61-264">删除右括号，然后键入 **,Fields!ID.value, Fields!CountryRegion.value, "CountryRegion")**</span><span class="sxs-lookup"><span data-stu-id="1ec61-264">Delete the right parenthesis and then type **,Fields!ID.value, Fields!CountryRegion.value, "CountryRegion")**</span></span>  
  
     <span data-ttu-id="1ec61-265">完成的表达式： `=Lookup(Fields!CountryRegionID.Value,Fields!ID.value, Fields!CountryRegion.value, "CountryRegion")`</span><span class="sxs-lookup"><span data-stu-id="1ec61-265">The completed expression: `=Lookup(Fields!CountryRegionID.Value,Fields!ID.value, Fields!CountryRegion.value, "CountryRegion")`</span></span>  
  
     <span data-ttu-id="1ec61-266">该 **Lookup** 函数的语法指定对 CountryRegion 数据集中的 CountryRegionID 和 ID 进行查找，返回 CountryRegion 值（该值也在 CountryRegion 数据集中）。</span><span class="sxs-lookup"><span data-stu-id="1ec61-266">The syntax of the **Lookup** function specifies a lookup between CountryRegionID and ID in the CountryRegion dataset that returns the CountryRegion value, which is also in the CountryRegion dataset.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. <span data-ttu-id="1ec61-267">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="1ec61-267">Click **Run** to preview the report.</span></span>  
  
##  <a name="6-count-days-since-last-purchase"></a><a name="Count"></a><span data-ttu-id="1ec61-268">6. 统计自上次购买以来的天数</span><span class="sxs-lookup"><span data-stu-id="1ec61-268">6. Count Days Since Last Purchase</span></span>  
 <span data-ttu-id="1ec61-269">添加一个列，然后使用**Now**函数或 `ExecutionTime` 内置全局变量来计算自上一次购买以来的天数。</span><span class="sxs-lookup"><span data-stu-id="1ec61-269">Add a column and then use the **Now** function or the `ExecutionTime` built-in global variable to calculate the number of days from today since a person's last purchases.</span></span>  
  
#### <a name="to-add-the-days-ago-column"></a><span data-ttu-id="1ec61-270">添加 Days Ago 列</span><span class="sxs-lookup"><span data-stu-id="1ec61-270">To add the Days Ago column</span></span>  
  
1.  <span data-ttu-id="1ec61-271">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="1ec61-271">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="1ec61-272">右键单击“Last Purchase”列，指向“插入列”，然后单击“右”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-272">Right-click the **Last Purchase** column, point to **Insert Column**, and then click **Right**.</span></span>  
  
     <span data-ttu-id="1ec61-273">一个新列将添加到“Last Purchase”列的右侧\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-273">A new column is added to the right of the **Last Purchase** column.</span></span>  
  
3.  <span data-ttu-id="1ec61-274">在列标题中，键入“Days Ago”\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1ec61-274">In the column header, type **Days Ago**</span></span>  
  
4.  <span data-ttu-id="1ec61-275">右键单击“Days Ago”列的数据单元格，然后单击“表达式”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-275">Right-click the data cell for the **Days Ago** column and click **Expression**.</span></span>  
  
5.  <span data-ttu-id="1ec61-276">在“表达式”对话框中，展开“常见函数”，然后单击“日期和时间”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-276">In the **Expression** dialog box, expand **Common Functions**, and then click **Date & Time**.</span></span>  
  
6.  <span data-ttu-id="1ec61-277">在“项”\*\*\*\* 列表中，双击 **DateDiff**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-277">In the **Item** list, double-click **DateDiff**.</span></span>  
  
7.  <span data-ttu-id="1ec61-278">如果鼠标光标不是紧接 `DateDiff(` 之后，请将光标置于其后。</span><span class="sxs-lookup"><span data-stu-id="1ec61-278">If the cursor is not already immediately after `DateDiff(`, place it there.</span></span>  
  
8.  <span data-ttu-id="1ec61-279">键入 **"d",**</span><span class="sxs-lookup"><span data-stu-id="1ec61-279">Type **"d",**</span></span>  
  
9. <span data-ttu-id="1ec61-280">在“类别”\*\*\*\* 列表中，单击“字段(表达式)”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-280">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
10. <span data-ttu-id="1ec61-281">在“值”\*\*\*\* 列表中，双击 **LastPurchase**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-281">In the **Values** list, double-click **LastPurchase**.</span></span>  
  
11. <span data-ttu-id="1ec61-282">如果鼠标光标不是紧接 `Fields!LastPurchase.Value` 之后，请将光标置于其后。</span><span class="sxs-lookup"><span data-stu-id="1ec61-282">If the cursor is not already immediately after `Fields!LastPurchase.Value`, place it there.</span></span>  
  
12. <span data-ttu-id="1ec61-283">键入 **，**</span><span class="sxs-lookup"><span data-stu-id="1ec61-283">Type **,**</span></span>  
  
13. <span data-ttu-id="1ec61-284">在“类别”\*\*\*\* 列表中，再次单击“日期和时间”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-284">In the **Category** list, click **Date & Time** again.</span></span>  
  
14. <span data-ttu-id="1ec61-285">在“项”\*\*\*\* 列表中，双击 **Now**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-285">In the **Item** list, double-click **Now**.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="1ec61-286">在生产报表中，不应在报表呈现过程中会多次计算的表达式中（例如，在报表的详细信息行中）使用 **Now** 函数。</span><span class="sxs-lookup"><span data-stu-id="1ec61-286">In production reports you should not use the **Now** function in expressions that are evaluated multiple times as the report renders (for example, in the detail rows of a report).</span></span> <span data-ttu-id="1ec61-287">**Now** 的值随行变化，不同的值会影响表达式的计算结果，这将导致结果略微不一致。</span><span class="sxs-lookup"><span data-stu-id="1ec61-287">The value of **Now** changes from row to row and the different values affect the evaluation results of expressions, which leads to results that are subtly inconsistent.</span></span> <span data-ttu-id="1ec61-288">应改用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 提供的 `ExecutionTime` 全局变量。</span><span class="sxs-lookup"><span data-stu-id="1ec61-288">Instead, you should use the `ExecutionTime` global variable that [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] provides.</span></span>  
  
15. <span data-ttu-id="1ec61-289">如果鼠标光标不是紧接 `Now(` 之后，请将光标置于其后。</span><span class="sxs-lookup"><span data-stu-id="1ec61-289">If the cursor is not already immediately after `Now(`, place it there.</span></span>  
  
16. <span data-ttu-id="1ec61-290">删除左括号，然后键入 **)**</span><span class="sxs-lookup"><span data-stu-id="1ec61-290">Delete the left parenthesis and then type **)**</span></span>  
  
     <span data-ttu-id="1ec61-291">完成的表达式： `=DateDiff("d", Fields!LastPurchase.Value, Now)`</span><span class="sxs-lookup"><span data-stu-id="1ec61-291">The completed expression: `=DateDiff("d", Fields!LastPurchase.Value, Now)`</span></span>  
  
17. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="7-use-an-indicator-to-show-sales-comparison"></a><a name="Indicator"></a><span data-ttu-id="1ec61-292">7. 使用指示器显示销售额比较</span><span class="sxs-lookup"><span data-stu-id="1ec61-292">7. Use an Indicator to Show Sales Comparison</span></span>  
 <span data-ttu-id="1ec61-293">添加一个新列，并使用指示器显示某个人的年初至今 (本年迄今) 购买高于还是低于平均 YTD 采购。</span><span class="sxs-lookup"><span data-stu-id="1ec61-293">Add a new column and use an indicator to show whether a person's year-to-date (YTD) purchases are above or below the average YTD purchases.</span></span> <span data-ttu-id="1ec61-294">**Round** 函数从值中去掉小数部分。</span><span class="sxs-lookup"><span data-stu-id="1ec61-294">The **Round** function removes decimals from values.</span></span>  
  
 <span data-ttu-id="1ec61-295">该指示器及其状态的配置需要许多步骤。</span><span class="sxs-lookup"><span data-stu-id="1ec61-295">The configuration of the indicator and its states requires many steps.</span></span> <span data-ttu-id="1ec61-296">如果需要，在 "配置指示器" 过程中，您可以跳过此教程并将已完成的表达式从本教程复制/粘贴到 "**表达式**" 对话框中。</span><span class="sxs-lookup"><span data-stu-id="1ec61-296">If you want to, in the "To configure the indicator" procedure, you can skip ahead and copy/paste the completed expressions from this tutorial into the **Expression** dialog box.</span></span>  
  
#### <a name="to-add-the--or---avg-sales-column"></a><span data-ttu-id="1ec61-297">添加 + or - AVG Sales 列</span><span class="sxs-lookup"><span data-stu-id="1ec61-297">To add the + or - AVG Sales column</span></span>  
  
1.  <span data-ttu-id="1ec61-298">右键单击“YTD Purchase”列，指向“插入列”，然后单击“右”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-298">Right-click the **YTD Purchase** column, point to **Insert Column**, and then click **Right**.</span></span>  
  
     <span data-ttu-id="1ec61-299">将一个新列添加到“YTD Purchase”\*\*\*\* 列的右侧。</span><span class="sxs-lookup"><span data-stu-id="1ec61-299">A new column is added to the right of the **YTD Purchase** column.</span></span>  
  
2.  <span data-ttu-id="1ec61-300">单击该列的标题，然后键入 **+ or - AVG Sales**</span><span class="sxs-lookup"><span data-stu-id="1ec61-300">Click the title of the column and type **+ or - AVG Sales**</span></span>  
  
#### <a name="to-add-an-indicator"></a><span data-ttu-id="1ec61-301">添加指示器</span><span class="sxs-lookup"><span data-stu-id="1ec61-301">To add an indicator</span></span>  
  
1.  <span data-ttu-id="1ec61-302">在功能区的“插入”\*\*\*\* 选项卡上，单击“指示器”\*\*\*\*，然后在 **+ or - AVG Sales** 列的数据单元中单击。</span><span class="sxs-lookup"><span data-stu-id="1ec61-302">On the **Insert** tab of the ribbon, click **Indicator**, and then click the data cell for the **+ or - AVG Sales** column.</span></span>  
  
     <span data-ttu-id="1ec61-303">“选择指示器类型”\*\*\*\* 对话框即会打开。</span><span class="sxs-lookup"><span data-stu-id="1ec61-303">The **Select Indicator Type** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="1ec61-304">在图标集的“方向”\*\*\*\* 组中，单击由三个灰色箭头构成的图标集。</span><span class="sxs-lookup"><span data-stu-id="1ec61-304">In the **Directional** group of icon sets, click the set of three gray arrows.</span></span>  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-configure-the-indicator"></a><span data-ttu-id="1ec61-305">配置指示器</span><span class="sxs-lookup"><span data-stu-id="1ec61-305">To configure the indicator</span></span>  
  
1.  <span data-ttu-id="1ec61-306">右键单击指示器，单击“指示器属性”，然后单击“值和状态”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-306">Right-click the indicator, click **Indicator Properties**, and then click **Value and States**.</span></span>  
  
2.  <span data-ttu-id="1ec61-307">单击“值”文本框旁边的表达式“fx”按钮\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-307">Click the expression **fx** button next to the **Value** text box.</span></span>  
  
3.  <span data-ttu-id="1ec61-308">在“表达式”\*\*\*\* 对话框中，展开“常见函数”\*\*\*\*，然后单击 **Math**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-308">In the **Expression** dialog box, expand **Common Functions**, and then click **Math**.</span></span>  
  
4.  <span data-ttu-id="1ec61-309">在“项”\*\*\*\* 列表中，双击 **Round**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-309">In the **Item** list, double-click **Round**.</span></span>  
  
5.  <span data-ttu-id="1ec61-310">在“类别”\*\*\*\* 列表中，单击“字段(表达式)”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-310">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
6.  <span data-ttu-id="1ec61-311">在“值”\*\*\*\* 列表中，双击 **YTDPurchase**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-311">In the **Values** list, double-click **YTDPurchase**.</span></span>  
  
7.  <span data-ttu-id="1ec61-312">如果鼠标光标不是紧接 `Fields!YTDPurchase.Value` 之后，请将光标置于其后。</span><span class="sxs-lookup"><span data-stu-id="1ec61-312">If the cursor is not already immediately after `Fields!YTDPurchase.Value`, place it there.</span></span>  
  
8.  <span data-ttu-id="1ec61-313">类别**-**</span><span class="sxs-lookup"><span data-stu-id="1ec61-313">Type  **-**</span></span>  
  
9. <span data-ttu-id="1ec61-314">再次展开“常见函数”\*\*\*\*，然后单击 **Aggregate**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-314">Expand **Common Functions** again and click **Aggregate**.</span></span>  
  
10. <span data-ttu-id="1ec61-315">在“项”\*\*\*\* 列表中，双击 **Avg**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-315">In the **Item** list, double-click **Avg**.</span></span>  
  
11. <span data-ttu-id="1ec61-316">在“类别”\*\*\*\* 列表中，单击“字段(表达式)”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-316">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
12. <span data-ttu-id="1ec61-317">在“值”\*\*\*\* 列表中，双击 **YTDPurchase**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-317">In the **Values** list, double-click **YTDPurchase**.</span></span>  
  
13. <span data-ttu-id="1ec61-318">如果鼠标光标不是紧接 `Fields!YTDPurchase.Value` 之后，请将光标置于其后。</span><span class="sxs-lookup"><span data-stu-id="1ec61-318">If the cursor is not already immediately after `Fields!YTDPurchase.Value`, place it there.</span></span>  
  
14. <span data-ttu-id="1ec61-319">键入 **, "Expressions"))**</span><span class="sxs-lookup"><span data-stu-id="1ec61-319">Type **, "Expressions"))**</span></span>  
  
     <span data-ttu-id="1ec61-320">完成的表达式： `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions"))`</span><span class="sxs-lookup"><span data-stu-id="1ec61-320">The completed expression: `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions"))`</span></span>  
  
15. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
16. <span data-ttu-id="1ec61-321">在“状态度量单位”\*\*\*\* 框中，选择“数字”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-321">In the **States Measurement Unit** box, select **Numeric**.</span></span>  
  
17. <span data-ttu-id="1ec61-322">在具有向下箭头的行中，单击“起始”\*\*\*\* 值的文本框右侧的 **fx**按钮。</span><span class="sxs-lookup"><span data-stu-id="1ec61-322">In the row with the down-pointing arrow, click the **fx** button to the right of the text box for the **Start** value.</span></span>  
  
18. <span data-ttu-id="1ec61-323">在“表达式”\*\*\*\* 对话框中，展开“常见函数”\*\*\*\*，然后单击 **Math**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-323">In the **Expression** dialog box, expand **Common Functions**, and then click **Math**.</span></span>  
  
19. <span data-ttu-id="1ec61-324">在“项”\*\*\*\* 列表中，双击 **Round**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-324">In the **Item** list, double-click **Round**.</span></span>  
  
20. <span data-ttu-id="1ec61-325">在“类别”\*\*\*\* 列表中，单击“字段(表达式)”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-325">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
21. <span data-ttu-id="1ec61-326">在“值”\*\*\*\* 列表中，双击 **YTDPurchase**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-326">In the **Values** list, double-click **YTDPurchase**.</span></span>  
  
22. <span data-ttu-id="1ec61-327">如果鼠标光标不是紧接 `Fields!YTDPurchase.Value` 之后，请将光标置于其后。</span><span class="sxs-lookup"><span data-stu-id="1ec61-327">If the cursor is not already immediately after `Fields!YTDPurchase.Value`, place it there.</span></span>  
  
23. <span data-ttu-id="1ec61-328">类别**-**</span><span class="sxs-lookup"><span data-stu-id="1ec61-328">Type  **-**</span></span>  
  
24. <span data-ttu-id="1ec61-329">再次展开“常见函数”\*\*\*\*，然后单击 **Aggregate**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-329">Expand **Common Functions** again and click **Aggregate**.</span></span>  
  
25. <span data-ttu-id="1ec61-330">在“项”\*\*\*\* 列表中，双击 **Avg**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-330">In the **Item** list, double-click **Avg**.</span></span>  
  
26. <span data-ttu-id="1ec61-331">在“类别”\*\*\*\* 列表中，单击“字段(表达式)”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-331">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
27. <span data-ttu-id="1ec61-332">在“值”\*\*\*\* 列表中，双击 **YTDPurchase**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-332">In the **Values** list, double-click **YTDPurchase**.</span></span>  
  
28. <span data-ttu-id="1ec61-333">如果鼠标光标不是紧接 `Fields!YTDPurchase.Value` 之后，请将光标置于其后。</span><span class="sxs-lookup"><span data-stu-id="1ec61-333">If the cursor is not already immediately after `Fields!YTDPurchase.Value`, place it there.</span></span>  
  
29. <span data-ttu-id="1ec61-334">键入 **, "Expressions")) < 0**</span><span class="sxs-lookup"><span data-stu-id="1ec61-334">Type **, "Expressions")) < 0**</span></span>  
  
     <span data-ttu-id="1ec61-335">完成的表达式： `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) < 0`</span><span class="sxs-lookup"><span data-stu-id="1ec61-335">The completed expression: `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) < 0`</span></span>  
  
30. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
31. <span data-ttu-id="1ec61-336">在“结束”\*\*\*\* 值的文本框中，键入 **0**</span><span class="sxs-lookup"><span data-stu-id="1ec61-336">In the text box for the **End** value, type **0**</span></span>  
  
32. <span data-ttu-id="1ec61-337">单击具有水平方向箭头的行，然后单击“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-337">Click the row with the horizontal-pointing arrow and click **Delete**.</span></span>  
  
33. <span data-ttu-id="1ec61-338">在具有向上箭头的行的“起始”\*\*\*\* 框中，键入 **0**</span><span class="sxs-lookup"><span data-stu-id="1ec61-338">In the row with the up-pointing arrow, in the **Start** box, type **0**</span></span>  
  
34. <span data-ttu-id="1ec61-339">单击“结束”\*\*\*\* 值的文本框右侧的 **fx** 按钮。</span><span class="sxs-lookup"><span data-stu-id="1ec61-339">Click the **fx** button to the right of the text box for the **End** value.</span></span>  
  
35. <span data-ttu-id="1ec61-340">在 "**表达式**" 对话框中，创建表达式：`=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) >0`</span><span class="sxs-lookup"><span data-stu-id="1ec61-340">In the **Expression** dialog box, create the expression: `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) >0`</span></span>  
  
36. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
37. <span data-ttu-id="1ec61-341">再次单击“确定”\*\*\*\* 以关闭“指示器属性”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="1ec61-341">Click **OK** again to close the **Indicator properties** dialog box.</span></span>  
  
38. <span data-ttu-id="1ec61-342">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="1ec61-342">Click **Run** to preview the report.</span></span>  
  
##  <a name="8-make-the-report-a-green-bar-report"></a><a name="GreenBar"></a><span data-ttu-id="1ec61-343">8. 使报表成为 "绿色条" 报表</span><span class="sxs-lookup"><span data-stu-id="1ec61-343">8. Make the Report a "Green Bar" Report</span></span>  
 <span data-ttu-id="1ec61-344">使用参数指定要应用于报表的交替行的颜色，使报表成为条纹形式的报表。</span><span class="sxs-lookup"><span data-stu-id="1ec61-344">Use a parameter to specify the color to apply to alternating rows in the report, making it a barred report.</span></span>  
  
#### <a name="to-add-a-parameter"></a><span data-ttu-id="1ec61-345">添加参数</span><span class="sxs-lookup"><span data-stu-id="1ec61-345">To add a parameter</span></span>  
  
1.  <span data-ttu-id="1ec61-346">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="1ec61-346">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="1ec61-347">在“报表数据”\*\*\*\* 窗格中，右键单击“参数”\*\*\*\*，然后单击“添加参数”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-347">In the **Report Data** pane, right-click **Parameters** and click **Add Parameter**.</span></span>  
  
     <span data-ttu-id="1ec61-348">此时将打开 **“报表参数属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="1ec61-348">The **Report Parameter Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="1ec61-349">在“提示符”下，键入“选择颜色”\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1ec61-349">In **Prompt**, type **Choose color**</span></span>  
  
4.  <span data-ttu-id="1ec61-350">在“名称”\*\*\*\* 中，键入 **RowColor**</span><span class="sxs-lookup"><span data-stu-id="1ec61-350">In **Name**, type **RowColor**</span></span>  
  
5.  <span data-ttu-id="1ec61-351">在左窗格中单击“可用值”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-351">In the left pane, click **Available Values**.</span></span>  
  
6.  <span data-ttu-id="1ec61-352">单击“指定值”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-352">Click **Specify values**.</span></span>  
  
7.  <span data-ttu-id="1ec61-353">单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="1ec61-353">Click **Add**.</span></span>  
  
8.  <span data-ttu-id="1ec61-354">在“标签”\*\*\*\* 框中，键入 **Yellow**</span><span class="sxs-lookup"><span data-stu-id="1ec61-354">In the **Label** box, type: **Yellow**</span></span>  
  
9. <span data-ttu-id="1ec61-355">在“值”\*\*\*\* 框中，键入 **Yellow**</span><span class="sxs-lookup"><span data-stu-id="1ec61-355">In the **Value** box, type **Yellow**</span></span>  
  
10. <span data-ttu-id="1ec61-356">单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="1ec61-356">Click **Add**.</span></span>  
  
11. <span data-ttu-id="1ec61-357">在“标签”\*\*\*\* 框中，键入“绿色”\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1ec61-357">In the **Label** box, type **Green**</span></span>  
  
12. <span data-ttu-id="1ec61-358">在“值”\*\*\*\* 框中，键入“淡绿色”\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1ec61-358">In the **Value** box, type **PaleGreen**</span></span>  
  
13. <span data-ttu-id="1ec61-359">单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="1ec61-359">Click **Add**.</span></span>  
  
14. <span data-ttu-id="1ec61-360">在“标签”\*\*\*\* 框中，键入“蓝色”\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1ec61-360">In the **Label** box, type **Blue**</span></span>  
  
15. <span data-ttu-id="1ec61-361">在“值”\*\*\*\* 框中，键入“浅蓝色”\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1ec61-361">In the **Value** box, type **LightBlue**</span></span>  
  
16. <span data-ttu-id="1ec61-362">单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="1ec61-362">Click **Add**.</span></span>  
  
17. <span data-ttu-id="1ec61-363">在“标签”\*\*\*\* 框中，键入“粉色”\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1ec61-363">In the **Label** box, type **Pink**</span></span>  
  
18. <span data-ttu-id="1ec61-364">在“值”\*\*\*\* 框中，键入 **Pink**</span><span class="sxs-lookup"><span data-stu-id="1ec61-364">In the **Value** box, type **Pink**</span></span>  
  
19. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-apply-alternating-colors-to-detail-rows"></a><span data-ttu-id="1ec61-365">将交替颜色应用于详细信息行</span><span class="sxs-lookup"><span data-stu-id="1ec61-365">To apply alternating colors to detail rows</span></span>  
  
1.  <span data-ttu-id="1ec61-366">单击功能区上的“视图”\*\*\*\* 选项卡，确认选中了“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-366">Click the **View** tab on the ribbon and verify that **Properties** is selected.</span></span>  
  
2.  <span data-ttu-id="1ec61-367">按住 Shift 键单击“Name”\*\*\*\* 列的数据单元。</span><span class="sxs-lookup"><span data-stu-id="1ec61-367">Click the data cell for the **Name** column and press the Shift key.</span></span>  
  
3.  <span data-ttu-id="1ec61-368">逐一单击行中的其他单元。</span><span class="sxs-lookup"><span data-stu-id="1ec61-368">One by one, click the other cells in the row.</span></span>  
  
4.  <span data-ttu-id="1ec61-369">在“属性”窗格中，单击 **BackgroundColor**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-369">In the Properties pane, click **BackgroundColor**.</span></span>  
  
     <span data-ttu-id="1ec61-370">如果“属性”窗格按类别列出属性，则“BackgroundColor”\*\*\*\* 在“填充”\*\*\*\* 类别下。</span><span class="sxs-lookup"><span data-stu-id="1ec61-370">If your Properties pane lists properties by category, you will find the **BackgroundColor** under the **Fill** category.</span></span>  
  
5.  <span data-ttu-id="1ec61-371">单击向下箭头，然后单击“表达式”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-371">Click the down arrow and then click **Expression**.</span></span>  
  
6.  <span data-ttu-id="1ec61-372">在“表达式”\*\*\*\* 对话框中，展开“常见函数”\*\*\*\*，然后单击“程序流”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-372">In the **Expression** dialog box, expand **Common Functions**, and then click **Program Flow**.</span></span>  
  
7.  <span data-ttu-id="1ec61-373">在“项”\*\*\*\* 列表中，双击“IIf”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-373">In the **Item** list, double-click **IIf**.</span></span>  
  
8.  <span data-ttu-id="1ec61-374">展开“常见函数”\*\*\*\*，然后单击“Aggregate”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-374">Expand **Common Functions** and click **Aggregate**.</span></span>  
  
9. <span data-ttu-id="1ec61-375">在“项”\*\*\*\* 列表中，双击“RunningValue”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-375">In the **Item** list, double-click **RunningValue**.</span></span>  
  
10. <span data-ttu-id="1ec61-376">在“类别”\*\*\*\* 列表中，单击“字段(表达式)”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-376">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
11. <span data-ttu-id="1ec61-377">在“值”\*\*\*\* 列表中，双击 **FirstName**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-377">In the **Values** list, double-click **FirstName**.</span></span>  
  
12. <span data-ttu-id="1ec61-378">如果鼠标光标不是紧接 `Fields!FirstName.Value` 之后，请将光标置于其后并键入 **,**</span><span class="sxs-lookup"><span data-stu-id="1ec61-378">If the cursor is not already immediately after `Fields!FirstName.Value`, place it there and type **,**</span></span>  
  
13. <span data-ttu-id="1ec61-379">展开“常见函数”\*\*\*\*，然后单击“Aggregate”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-379">Expand **Common Functions** and click **Aggregate**.</span></span>  
  
14. <span data-ttu-id="1ec61-380">在“项”\*\*\*\* 列表中，双击“Count”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-380">In the **Item** list, double-click **Count**.</span></span>  
  
15. <span data-ttu-id="1ec61-381">如果鼠标光标不是紧接 `Count(` 之后，请将光标置于其后。</span><span class="sxs-lookup"><span data-stu-id="1ec61-381">If the cursor is not already immediately after `Count(`, place it there.</span></span>  
  
16. <span data-ttu-id="1ec61-382">删除左括号，然后键入 \*\*"表达式" ) \*\*</span><span class="sxs-lookup"><span data-stu-id="1ec61-382">Delete the left parenthesis and then type **,"Expressions")**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1ec61-383">Expressions 是要对其数据行进行计数的数据集的名称。</span><span class="sxs-lookup"><span data-stu-id="1ec61-383">Expressions is the name of the dataset in which to count data rows.</span></span>  
  
17. <span data-ttu-id="1ec61-384">展开“运算符”\*\*\*\*，然后单击“算术”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-384">Expand **Operators** and click **Arithmetic**.</span></span>  
  
18. <span data-ttu-id="1ec61-385">在“项”\*\*\*\* 列表中，双击“Mod”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-385">In the **Item** list, double-click **Mod**.</span></span>  
  
19. <span data-ttu-id="1ec61-386">如果鼠标光标不是紧接 `Mod` 之后，请将光标置于其后。</span><span class="sxs-lookup"><span data-stu-id="1ec61-386">If the cursor is not already immediately after `Mod`, place it there.</span></span>  
  
20. <span data-ttu-id="1ec61-387">键入 **2 =0,**</span><span class="sxs-lookup"><span data-stu-id="1ec61-387">Type  **2 =0,**</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="1ec61-388">请确保在键入数值 2 之前包含一个空格。</span><span class="sxs-lookup"><span data-stu-id="1ec61-388">Be sure you include a space before you type the number 2.</span></span>  
  
21. <span data-ttu-id="1ec61-389">单击“参数”\*\*\*\*，在“值”\*\*\*\* 列表中，双击“RowColor”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-389">Click **Parameters** and in the **Values** list, double-click **RowColor**.</span></span>  
  
22. <span data-ttu-id="1ec61-390">如果鼠标光标不是紧接 `Parameters!RowColor.Value` 之后，请将光标置于其后。</span><span class="sxs-lookup"><span data-stu-id="1ec61-390">If the cursor is not already immediately after `Parameters!RowColor.Value`, place it there.</span></span>  
  
23. <span data-ttu-id="1ec61-391">键入 \*\*"白色" ) \*\*</span><span class="sxs-lookup"><span data-stu-id="1ec61-391">Type **, "White")**</span></span>  
  
     <span data-ttu-id="1ec61-392">完成的表达式： `=IIf(RunningValue(Fields!FirstName.Value,Count, "Expressions") Mod 2 =0, Parameters!RowColor.Value, "White")`</span><span class="sxs-lookup"><span data-stu-id="1ec61-392">The completed expression: `=IIf(RunningValue(Fields!FirstName.Value,Count, "Expressions") Mod 2 =0, Parameters!RowColor.Value, "White")`</span></span>  
  
24. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="run-the-report"></a><span data-ttu-id="1ec61-393">运行报表</span><span class="sxs-lookup"><span data-stu-id="1ec61-393">Run the Report</span></span>  
  
1.  <span data-ttu-id="1ec61-394">如果不是在“开始”\*\*\*\* 选项卡上，请单击“开始”\*\*\*\* 返回到设计视图。</span><span class="sxs-lookup"><span data-stu-id="1ec61-394">If not on the **Home** tab, click **Home** to return to design view.</span></span>  
  
2.  <span data-ttu-id="1ec61-395">单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="1ec61-395">Click **Run**.</span></span>  
  
3.  <span data-ttu-id="1ec61-396">在“选择颜色”\*\*\*\* 下拉列表中，选择报表上非白色条的颜色。</span><span class="sxs-lookup"><span data-stu-id="1ec61-396">In the **Choose color** drop-down list, select the color of the non-white bars on the report.</span></span>  
  
4.  <span data-ttu-id="1ec61-397">单击“查看报表”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-397">Click **View Report**.</span></span>  
  
     <span data-ttu-id="1ec61-398">该报表呈现，报表行交替呈现您所选的背景。</span><span class="sxs-lookup"><span data-stu-id="1ec61-398">The report renders and alternating rows have the background that you chose.</span></span>  
  
##  <a name="optional-format-date-column"></a><a name="DateFormat"></a> <span data-ttu-id="1ec61-399">(可选) 格式日期列</span><span class="sxs-lookup"><span data-stu-id="1ec61-399">(optional) Format Date Column</span></span>  
 <span data-ttu-id="1ec61-400">设置包含日期的“Last Purchase”\*\*\*\* 列的格式。</span><span class="sxs-lookup"><span data-stu-id="1ec61-400">Format the **Last Purchase** column, which contains dates.</span></span>  
  
#### <a name="to-format-date-column"></a><span data-ttu-id="1ec61-401">若要设置日期列的格式</span><span class="sxs-lookup"><span data-stu-id="1ec61-401">To format date column</span></span>  
  
1.  <span data-ttu-id="1ec61-402">单击 **“设计”** 返回设计视图。</span><span class="sxs-lookup"><span data-stu-id="1ec61-402">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="1ec61-403">右键单击“Last Purchase”\*\*\*\* 列的数据单元，然后单击“文本框属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-403">Right-click the data cell for the **Last Purchase** column and click **Text Box Properties**.</span></span>  
  
3.  <span data-ttu-id="1ec61-404">在“文本框属性”\*\*\*\* 对话框中，依次单击“数字”\*\*\*\*、“日期”\*\*\*\* 和类型“2000/1/31”**\***。</span><span class="sxs-lookup"><span data-stu-id="1ec61-404">In the **Text Box Properties** dialog box, click **Number**, click **Date**, and then click the type **\*1/31/2000**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="optional-add-a-report-title"></a><a name="Title"></a> <span data-ttu-id="1ec61-405">(可选) 添加报表标题</span><span class="sxs-lookup"><span data-stu-id="1ec61-405">(optional) Add a Report Title</span></span>  
 <span data-ttu-id="1ec61-406">为报表添加标题。</span><span class="sxs-lookup"><span data-stu-id="1ec61-406">Add a title to the report.</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="1ec61-407">添加报表标题</span><span class="sxs-lookup"><span data-stu-id="1ec61-407">To add a report title</span></span>  
  
1.  <span data-ttu-id="1ec61-408">在设计图面上，单击“单击以添加标题”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-408">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="1ec61-409">键入 **Sales Comparison Summary**，然后在文本框外部单击。</span><span class="sxs-lookup"><span data-stu-id="1ec61-409">Type **Sales Comparison Summary**, and then click outside the text box.</span></span>  
  
3.  <span data-ttu-id="1ec61-410">右键单击包含 **Sales Comparison Summary** 的文本框，然后单击“文本框属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-410">Right-click the text box that contains **Sales Comparison Summary** and click **Text Box Properties**.</span></span>  
  
4.  <span data-ttu-id="1ec61-411">在“文本框属性”\*\*\*\* 对话框中，单击“字体”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-411">In the **Text Box Properties** dialog box, click **Font**.</span></span>  
  
5.  <span data-ttu-id="1ec61-412">在“大小”\*\*\*\* 列表中，选择“18pt”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-412">In the **Size** list, select **18pt**.</span></span>  
  
6.  <span data-ttu-id="1ec61-413">在“颜色”\*\*\*\* 列表中，选择“灰色”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-413">In the **Color** list, select **Gray**.</span></span>  
  
7.  <span data-ttu-id="1ec61-414">选择“粗体”\*\*\*\* 和“斜体”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ec61-414">Select  **Bold** and  **Italic**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="optional-save-the-report"></a><a name="Save"></a> <span data-ttu-id="1ec61-415">(可选) 保存报表</span><span class="sxs-lookup"><span data-stu-id="1ec61-415">(optional) Save the Report</span></span>  
 <span data-ttu-id="1ec61-416">您可以将报表保存到报表服务器、SharePoint 库或本地计算机。</span><span class="sxs-lookup"><span data-stu-id="1ec61-416">You can save reports to a report server, SharePoint library, or your computer.</span></span> <span data-ttu-id="1ec61-417">有关详细信息，请参阅[保存报表（报表生成器）](report-builder/saving-reports-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="1ec61-417">For more information, see [Saving Reports &#40;Report Builder&#41;](report-builder/saving-reports-report-builder.md).</span></span>  
  
 <span data-ttu-id="1ec61-418">在本教程中，将报表保存到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="1ec61-418">In this tutorial, save the report to a report server.</span></span> <span data-ttu-id="1ec61-419">如果您没有对报表服务器的访问权限，则可以保存到您的计算机。</span><span class="sxs-lookup"><span data-stu-id="1ec61-419">If you do not have access to a report server, save the report to your computer.</span></span>  
  
#### <a name="to-save-the-report-to-a-report-server"></a><span data-ttu-id="1ec61-420">将报表保存到报表服务器</span><span class="sxs-lookup"><span data-stu-id="1ec61-420">To save the report to a report server</span></span>  
  
1.  <span data-ttu-id="1ec61-421">从 **“报表生成器”** 按钮，单击 **“另存为”**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-421">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="1ec61-422">单击 **“最近使用的站点和服务器”**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-422">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="1ec61-423">选择或键入您拥有保存报表权限的报表服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="1ec61-423">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="1ec61-424">此时将显示“正在连接到报表服务器”消息。</span><span class="sxs-lookup"><span data-stu-id="1ec61-424">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="1ec61-425">当连接完成时，您将看到报表服务器管理员指定为默认报表位置的报表文件夹的内容。</span><span class="sxs-lookup"><span data-stu-id="1ec61-425">When the connection is complete, you will see the contents of the report folder that the report server administrator specified as the default report location.</span></span>  
  
4.  <span data-ttu-id="1ec61-426">在“名称”\*\*\*\* 中，用“Sales Comparison Summary”\*\*\*\* 替换默认名称。</span><span class="sxs-lookup"><span data-stu-id="1ec61-426">In **Name**, replace the default name with **Sales Comparison Summary**.</span></span>  
  
5.  <span data-ttu-id="1ec61-427">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="1ec61-427">Click **Save**.</span></span>  
  
 <span data-ttu-id="1ec61-428">报表即已保存至报表服务器。</span><span class="sxs-lookup"><span data-stu-id="1ec61-428">The report is saved to the report server.</span></span> <span data-ttu-id="1ec61-429">您连接的报表服务器的名称将显示在窗口底部的状态栏中。</span><span class="sxs-lookup"><span data-stu-id="1ec61-429">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
#### <a name="to-save-the-report-to-your-computer"></a><span data-ttu-id="1ec61-430">将报表保存到计算机</span><span class="sxs-lookup"><span data-stu-id="1ec61-430">To save the report to your computer</span></span>  
  
1.  <span data-ttu-id="1ec61-431">从 **“报表生成器”** 按钮，单击 **“另存为”**。</span><span class="sxs-lookup"><span data-stu-id="1ec61-431">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="1ec61-432">单击 **“桌面”**、 **“我的文档”** 或 **“我的电脑”**，然后浏览到要将报表保存到的文件夹。</span><span class="sxs-lookup"><span data-stu-id="1ec61-432">Click **Desktop**, **My Documents**, or **My computer**, and then browse to the folder where you want to save the report.</span></span>  
  
3.  <span data-ttu-id="1ec61-433">在“名称”\*\*\*\* 中，用“Sales Comparison Summary”\*\*\*\* 替换默认名称。</span><span class="sxs-lookup"><span data-stu-id="1ec61-433">In **Name**, replace the default name with **Sales Comparison Summary**.</span></span>  
  
4.  <span data-ttu-id="1ec61-434">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="1ec61-434">Click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ec61-435">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1ec61-435">See Also</span></span>  
 <span data-ttu-id="1ec61-436">[表达式（报表生成器和 SSRS）](report-design/expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1ec61-436">[Expressions &#40;Report Builder and SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1ec61-437">[表达式示例（报表生成器和 SSRS）](report-design/expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1ec61-437">[Expression Examples &#40;Report Builder and SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1ec61-438">[指标 &#40;报表生成器和 SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1ec61-438">[Indicators &#40;Report Builder and SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1ec61-439">[图像、文本框、矩形和线条 &#40;报表生成器和 SSRS&#41;](report-design/rectangles-and-lines-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1ec61-439">[Images, Text Boxes, Rectangles, and Lines &#40;Report Builder and SSRS&#41;](report-design/rectangles-and-lines-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1ec61-440">[表 &#40;报表生成器和 SSRS&#41;](report-design/tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1ec61-440">[Tables &#40;Report Builder  and SSRS&#41;](report-design/tables-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="1ec61-441">将数据添加到报表 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1ec61-441">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-data/report-datasets-ssrs.md)  
  
  
