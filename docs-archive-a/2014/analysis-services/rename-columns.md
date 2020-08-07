---
title: 第3课：重命名列 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5fc8ba1a-2b30-4775-9b3b-c09dee711b3e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 59904f1110455b65679b3d19e6e8b7c731465ee9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576991"
---
# <a name="lesson-3-rename-columns"></a><span data-ttu-id="dad18-102">第 3 课：对列重命名</span><span class="sxs-lookup"><span data-stu-id="dad18-102">Lesson 3: Rename Columns</span></span>
  <span data-ttu-id="dad18-103">在本课中，您将重命名您导入的每个表中的很多列。</span><span class="sxs-lookup"><span data-stu-id="dad18-103">In this lesson, you will rename many of the columns in each table you imported.</span></span> <span data-ttu-id="dad18-104">通过重命名，您可以更易于识别列，且更易于在模型设计器中以及通过用户在客户端应用程序中选择字段来进行导航列。</span><span class="sxs-lookup"><span data-stu-id="dad18-104">Renaming makes columns more identifiable and easier to navigate in both the model designer as well by users selecting fields in a client application.</span></span> <span data-ttu-id="dad18-105">若要了解详细信息，请参阅[重命名表或列（SSAS 表格）](tabular-models/rename-a-table-or-column-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="dad18-105">To learn more, see [Rename a Table or Column &#40;SSAS Tabular&#41;](tabular-models/rename-a-table-or-column-ssas-tabular.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="dad18-106">重命名列对于完成本教程不是必需的；但剩下的课程（尤其是包含使用 DAX 公式来创建关系、创建计算列和度量值的课程）将引用在本课中介绍的列友好名称。</span><span class="sxs-lookup"><span data-stu-id="dad18-106">Renaming columns is not necessary to complete this tutorial; however, remaining lessons, in particular those that include creating relationships and creating calculated columns and measures using DAX formulas, refer to the column friendly names described in this lesson.</span></span> <span data-ttu-id="dad18-107">如果您选择不重命名列，则必须编辑第 5、6 和 7 课中的 DAX 公式，以便使用本课中提供的原始源列名称。</span><span class="sxs-lookup"><span data-stu-id="dad18-107">If you choose not to rename columns, you will have to edit the DAX formulas in lessons 5, 6, and 7 to use the original source column names provided in this lesson.</span></span>  
  
 <span data-ttu-id="dad18-108">本课预计完成时间：**20 分钟**</span><span class="sxs-lookup"><span data-stu-id="dad18-108">Estimated time to complete this lesson: **20 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="dad18-109">必备条件</span><span class="sxs-lookup"><span data-stu-id="dad18-109">Prerequisites</span></span>  
 <span data-ttu-id="dad18-110">本主题是表格建模教程的一部分，应当按顺序完成。</span><span class="sxs-lookup"><span data-stu-id="dad18-110">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="dad18-111">执行本课中的任务之前，须已完成上一课： [第 2 课：添加数据](lesson-2-add-data.md)。</span><span class="sxs-lookup"><span data-stu-id="dad18-111">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 2: Add Data](lesson-2-add-data.md).</span></span>  
  
## <a name="rename-columns"></a><span data-ttu-id="dad18-112">对列重命名</span><span class="sxs-lookup"><span data-stu-id="dad18-112">Rename Columns</span></span>  
  
#### <a name="to-rename-columns"></a><span data-ttu-id="dad18-113">对列进行重命名</span><span class="sxs-lookup"><span data-stu-id="dad18-113">To rename columns</span></span>  
  
1.  <span data-ttu-id="dad18-114">在模型设计器中，单击“Customer”\*\*\*\* 表（选项卡）。</span><span class="sxs-lookup"><span data-stu-id="dad18-114">In the model designer, click the **Customer** table (tab).</span></span>  
  
     <span data-ttu-id="dad18-115">单击某个选项卡时，该表将在模型设计器窗口中变为活动状态。</span><span class="sxs-lookup"><span data-stu-id="dad18-115">When you click a tab, that table becomes active in the model designer window.</span></span>  
  
2.  <span data-ttu-id="dad18-116">双击 " **CustomerKey** " 列名称，然后键入 `Customer  Id` ，然后按 enter。</span><span class="sxs-lookup"><span data-stu-id="dad18-116">Double click the **CustomerKey** column name, then type `Customer  Id`, and then press ENTER.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="dad18-117">您还可以在列的 "**属性**" 窗口或关系图视图中重命名列**名称**属性中的列。</span><span class="sxs-lookup"><span data-stu-id="dad18-117">You can also rename a column in the **Column Name** property in the column's **Properties** window, or in Diagram View.</span></span>  
  
3.  <span data-ttu-id="dad18-118">重命名 **Customer** 表中的其余列以及其余表中的列，用友好名称替换源名称：</span><span class="sxs-lookup"><span data-stu-id="dad18-118">Rename the remaining columns in the **Customer** table, as well as the columns in the remaining tables, replacing the source name with the friendly name:</span></span>  
  
     <span data-ttu-id="dad18-119">**Customer 表**</span><span class="sxs-lookup"><span data-stu-id="dad18-119">**Customer Table**</span></span>  
  
    |<span data-ttu-id="dad18-120">源名称</span><span class="sxs-lookup"><span data-stu-id="dad18-120">Source Name</span></span>|<span data-ttu-id="dad18-121">友好名称</span><span class="sxs-lookup"><span data-stu-id="dad18-121">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="dad18-122">GeographyKey</span><span class="sxs-lookup"><span data-stu-id="dad18-122">GeographyKey</span></span>|<span data-ttu-id="dad18-123">Geography Id</span><span class="sxs-lookup"><span data-stu-id="dad18-123">Geography Id</span></span>|  
    |<span data-ttu-id="dad18-124">CustomerAlternateKey</span><span class="sxs-lookup"><span data-stu-id="dad18-124">CustomerAlternateKey</span></span>|<span data-ttu-id="dad18-125">Customer Alternate Id</span><span class="sxs-lookup"><span data-stu-id="dad18-125">Customer Alternate Id</span></span>|  
    |<span data-ttu-id="dad18-126">FirstName</span><span class="sxs-lookup"><span data-stu-id="dad18-126">FirstName</span></span>|<span data-ttu-id="dad18-127">名字</span><span class="sxs-lookup"><span data-stu-id="dad18-127">First Name</span></span>|  
    |<span data-ttu-id="dad18-128">MiddleName</span><span class="sxs-lookup"><span data-stu-id="dad18-128">MiddleName</span></span>|<span data-ttu-id="dad18-129">Middle Name</span><span class="sxs-lookup"><span data-stu-id="dad18-129">Middle Name</span></span>|  
    |<span data-ttu-id="dad18-130">LastName</span><span class="sxs-lookup"><span data-stu-id="dad18-130">LastName</span></span>|<span data-ttu-id="dad18-131">姓氏</span><span class="sxs-lookup"><span data-stu-id="dad18-131">Last Name</span></span>|  
    |<span data-ttu-id="dad18-132">NameStyle</span><span class="sxs-lookup"><span data-stu-id="dad18-132">NameStyle</span></span>|<span data-ttu-id="dad18-133">Name Style</span><span class="sxs-lookup"><span data-stu-id="dad18-133">Name Style</span></span>|  
    |<span data-ttu-id="dad18-134">BirthDate</span><span class="sxs-lookup"><span data-stu-id="dad18-134">BirthDate</span></span>|<span data-ttu-id="dad18-135">Birth Date</span><span class="sxs-lookup"><span data-stu-id="dad18-135">Birth Date</span></span>|  
    |<span data-ttu-id="dad18-136">MaritalStatus</span><span class="sxs-lookup"><span data-stu-id="dad18-136">MaritalStatus</span></span>|<span data-ttu-id="dad18-137">婚姻状况</span><span class="sxs-lookup"><span data-stu-id="dad18-137">Marital Status</span></span>|  
    |<span data-ttu-id="dad18-138">EmailAddress</span><span class="sxs-lookup"><span data-stu-id="dad18-138">EmailAddress</span></span>|<span data-ttu-id="dad18-139">电子邮件地址</span><span class="sxs-lookup"><span data-stu-id="dad18-139">Email Address</span></span>|  
    |<span data-ttu-id="dad18-140">YearlyIncome</span><span class="sxs-lookup"><span data-stu-id="dad18-140">YearlyIncome</span></span>|<span data-ttu-id="dad18-141">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="dad18-141">Yearly Income</span></span>|  
    |<span data-ttu-id="dad18-142">TotalChildren</span><span class="sxs-lookup"><span data-stu-id="dad18-142">TotalChildren</span></span>|<span data-ttu-id="dad18-143">Total Children</span><span class="sxs-lookup"><span data-stu-id="dad18-143">Total Children</span></span>|  
    |<span data-ttu-id="dad18-144">NumberChildrenAtHome</span><span class="sxs-lookup"><span data-stu-id="dad18-144">NumberChildrenAtHome</span></span>|<span data-ttu-id="dad18-145">Number of Children At Home</span><span class="sxs-lookup"><span data-stu-id="dad18-145">Number of Children At Home</span></span>|  
    |<span data-ttu-id="dad18-146">EnglishEducation</span><span class="sxs-lookup"><span data-stu-id="dad18-146">EnglishEducation</span></span>|<span data-ttu-id="dad18-147">教育</span><span class="sxs-lookup"><span data-stu-id="dad18-147">Education</span></span>|  
    |<span data-ttu-id="dad18-148">EnglishOccupation</span><span class="sxs-lookup"><span data-stu-id="dad18-148">EnglishOccupation</span></span>|<span data-ttu-id="dad18-149">职业</span><span class="sxs-lookup"><span data-stu-id="dad18-149">Occupation</span></span>|  
    |<span data-ttu-id="dad18-150">HouseOwnerFlag</span><span class="sxs-lookup"><span data-stu-id="dad18-150">HouseOwnerFlag</span></span>|<span data-ttu-id="dad18-151">Owns House</span><span class="sxs-lookup"><span data-stu-id="dad18-151">Owns House</span></span>|  
    |<span data-ttu-id="dad18-152">NumberCarsOwned</span><span class="sxs-lookup"><span data-stu-id="dad18-152">NumberCarsOwned</span></span>|<span data-ttu-id="dad18-153">Number of Cars Owned</span><span class="sxs-lookup"><span data-stu-id="dad18-153">Number of Cars Owned</span></span>|  
    |<span data-ttu-id="dad18-154">AddressLine1</span><span class="sxs-lookup"><span data-stu-id="dad18-154">AddressLine1</span></span>|<span data-ttu-id="dad18-155">Address Line 1</span><span class="sxs-lookup"><span data-stu-id="dad18-155">Address Line 1</span></span>|  
    |<span data-ttu-id="dad18-156">AddressLine2</span><span class="sxs-lookup"><span data-stu-id="dad18-156">AddressLine2</span></span>|<span data-ttu-id="dad18-157">Address Line 2</span><span class="sxs-lookup"><span data-stu-id="dad18-157">Address Line 2</span></span>|  
    |<span data-ttu-id="dad18-158">电话</span><span class="sxs-lookup"><span data-stu-id="dad18-158">Phone</span></span>|<span data-ttu-id="dad18-159">电话号码</span><span class="sxs-lookup"><span data-stu-id="dad18-159">Phone Number</span></span>|  
    |<span data-ttu-id="dad18-160">DateFirstPurchase</span><span class="sxs-lookup"><span data-stu-id="dad18-160">DateFirstPurchase</span></span>|<span data-ttu-id="dad18-161">Date of First Purchase</span><span class="sxs-lookup"><span data-stu-id="dad18-161">Date of First Purchase</span></span>|  
    |<span data-ttu-id="dad18-162">CommuteDistance</span><span class="sxs-lookup"><span data-stu-id="dad18-162">CommuteDistance</span></span>|<span data-ttu-id="dad18-163">上下班路程</span><span class="sxs-lookup"><span data-stu-id="dad18-163">Commute Distance</span></span>|  
  
     <span data-ttu-id="dad18-164">**Date**</span><span class="sxs-lookup"><span data-stu-id="dad18-164">**Date**</span></span>  
  
    |<span data-ttu-id="dad18-165">源名称</span><span class="sxs-lookup"><span data-stu-id="dad18-165">Source Name</span></span>|<span data-ttu-id="dad18-166">友好名称</span><span class="sxs-lookup"><span data-stu-id="dad18-166">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="dad18-167">FullDateAlternateKey</span><span class="sxs-lookup"><span data-stu-id="dad18-167">FullDateAlternateKey</span></span>|<span data-ttu-id="dad18-168">日期</span><span class="sxs-lookup"><span data-stu-id="dad18-168">Date</span></span>|  
    |<span data-ttu-id="dad18-169">DayNumberOfWeek</span><span class="sxs-lookup"><span data-stu-id="dad18-169">DayNumberOfWeek</span></span>|<span data-ttu-id="dad18-170">Day Number of Week</span><span class="sxs-lookup"><span data-stu-id="dad18-170">Day Number of Week</span></span>|  
    |<span data-ttu-id="dad18-171">EnglishDayNameOfWeek</span><span class="sxs-lookup"><span data-stu-id="dad18-171">EnglishDayNameOfWeek</span></span>|<span data-ttu-id="dad18-172">Day Name</span><span class="sxs-lookup"><span data-stu-id="dad18-172">Day Name</span></span>|  
    |<span data-ttu-id="dad18-173">DayNumberOfMonth</span><span class="sxs-lookup"><span data-stu-id="dad18-173">DayNumberOfMonth</span></span>|<span data-ttu-id="dad18-174">每月的某一日</span><span class="sxs-lookup"><span data-stu-id="dad18-174">Day of Month</span></span>|  
    |<span data-ttu-id="dad18-175">DayNumberOfYear</span><span class="sxs-lookup"><span data-stu-id="dad18-175">DayNumberOfYear</span></span>|<span data-ttu-id="dad18-176">每年的某一日</span><span class="sxs-lookup"><span data-stu-id="dad18-176">Day of Year</span></span>|  
    |<span data-ttu-id="dad18-177">WeekNumberOfYear</span><span class="sxs-lookup"><span data-stu-id="dad18-177">WeekNumberOfYear</span></span>|<span data-ttu-id="dad18-178">Week Number of Year</span><span class="sxs-lookup"><span data-stu-id="dad18-178">Week Number of Year</span></span>|  
    |<span data-ttu-id="dad18-179">EnglishMonthName</span><span class="sxs-lookup"><span data-stu-id="dad18-179">EnglishMonthName</span></span>|<span data-ttu-id="dad18-180">月份名称</span><span class="sxs-lookup"><span data-stu-id="dad18-180">Month Name</span></span>|  
    |<span data-ttu-id="dad18-181">MonthNumberOfYear</span><span class="sxs-lookup"><span data-stu-id="dad18-181">MonthNumberOfYear</span></span>|<span data-ttu-id="dad18-182">月份</span><span class="sxs-lookup"><span data-stu-id="dad18-182">Month</span></span>|  
    |<span data-ttu-id="dad18-183">CalendarQuarter</span><span class="sxs-lookup"><span data-stu-id="dad18-183">CalendarQuarter</span></span>|<span data-ttu-id="dad18-184">Calendar Quarter</span><span class="sxs-lookup"><span data-stu-id="dad18-184">Calendar Quarter</span></span>|  
    |<span data-ttu-id="dad18-185">CalendarYear</span><span class="sxs-lookup"><span data-stu-id="dad18-185">CalendarYear</span></span>|<span data-ttu-id="dad18-186">Calendar Year</span><span class="sxs-lookup"><span data-stu-id="dad18-186">Calendar Year</span></span>|  
    |<span data-ttu-id="dad18-187">CalendarSemester</span><span class="sxs-lookup"><span data-stu-id="dad18-187">CalendarSemester</span></span>|<span data-ttu-id="dad18-188">Calendar Semester</span><span class="sxs-lookup"><span data-stu-id="dad18-188">Calendar Semester</span></span>|  
    |<span data-ttu-id="dad18-189">FiscalQuarter</span><span class="sxs-lookup"><span data-stu-id="dad18-189">FiscalQuarter</span></span>|<span data-ttu-id="dad18-190">Fiscal Quarter</span><span class="sxs-lookup"><span data-stu-id="dad18-190">Fiscal Quarter</span></span>|  
    |<span data-ttu-id="dad18-191">FiscalYear</span><span class="sxs-lookup"><span data-stu-id="dad18-191">FiscalYear</span></span>|<span data-ttu-id="dad18-192">Fiscal Year</span><span class="sxs-lookup"><span data-stu-id="dad18-192">Fiscal Year</span></span>|  
    |<span data-ttu-id="dad18-193">FiscalSemester</span><span class="sxs-lookup"><span data-stu-id="dad18-193">FiscalSemester</span></span>|<span data-ttu-id="dad18-194">Fiscal Semester</span><span class="sxs-lookup"><span data-stu-id="dad18-194">Fiscal Semester</span></span>|  
  
     <span data-ttu-id="dad18-195">**地域**</span><span class="sxs-lookup"><span data-stu-id="dad18-195">**Geography**</span></span>  
  
    |<span data-ttu-id="dad18-196">源名称</span><span class="sxs-lookup"><span data-stu-id="dad18-196">Source Name</span></span>|<span data-ttu-id="dad18-197">友好名称</span><span class="sxs-lookup"><span data-stu-id="dad18-197">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="dad18-198">GeographyKey</span><span class="sxs-lookup"><span data-stu-id="dad18-198">GeographyKey</span></span>|<span data-ttu-id="dad18-199">Geography Id</span><span class="sxs-lookup"><span data-stu-id="dad18-199">Geography Id</span></span>|  
    |<span data-ttu-id="dad18-200">StateProvinceCode</span><span class="sxs-lookup"><span data-stu-id="dad18-200">StateProvinceCode</span></span>|<span data-ttu-id="dad18-201">State Province Code</span><span class="sxs-lookup"><span data-stu-id="dad18-201">State Province Code</span></span>|  
    |<span data-ttu-id="dad18-202">StateProvinceName</span><span class="sxs-lookup"><span data-stu-id="dad18-202">StateProvinceName</span></span>|<span data-ttu-id="dad18-203">State Province Name</span><span class="sxs-lookup"><span data-stu-id="dad18-203">State Province Name</span></span>|  
    |<span data-ttu-id="dad18-204">CountryRegionCode</span><span class="sxs-lookup"><span data-stu-id="dad18-204">CountryRegionCode</span></span>|<span data-ttu-id="dad18-205">Country Region Code</span><span class="sxs-lookup"><span data-stu-id="dad18-205">Country Region Code</span></span>|  
    |<span data-ttu-id="dad18-206">EnglishCountryRegionName</span><span class="sxs-lookup"><span data-stu-id="dad18-206">EnglishCountryRegionName</span></span>|<span data-ttu-id="dad18-207">Country Region Name</span><span class="sxs-lookup"><span data-stu-id="dad18-207">Country Region Name</span></span>|  
    |<span data-ttu-id="dad18-208">邮政编码</span><span class="sxs-lookup"><span data-stu-id="dad18-208">PostalCode</span></span>|<span data-ttu-id="dad18-209">邮政编码</span><span class="sxs-lookup"><span data-stu-id="dad18-209">Postal Code</span></span>|  
    |<span data-ttu-id="dad18-210">SalesTerritoryKey</span><span class="sxs-lookup"><span data-stu-id="dad18-210">SalesTerritoryKey</span></span>|<span data-ttu-id="dad18-211">Sales Territory Id</span><span class="sxs-lookup"><span data-stu-id="dad18-211">Sales Territory Id</span></span>|  
  
     <span data-ttu-id="dad18-212">**Product**</span><span class="sxs-lookup"><span data-stu-id="dad18-212">**Product**</span></span>  
  
    |<span data-ttu-id="dad18-213">源名称</span><span class="sxs-lookup"><span data-stu-id="dad18-213">Source Name</span></span>|<span data-ttu-id="dad18-214">友好名称</span><span class="sxs-lookup"><span data-stu-id="dad18-214">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="dad18-215">ProductKey</span><span class="sxs-lookup"><span data-stu-id="dad18-215">ProductKey</span></span>|<span data-ttu-id="dad18-216">Product Id</span><span class="sxs-lookup"><span data-stu-id="dad18-216">Product Id</span></span>|  
    |<span data-ttu-id="dad18-217">ProductAlternateKey</span><span class="sxs-lookup"><span data-stu-id="dad18-217">ProductAlternateKey</span></span>|<span data-ttu-id="dad18-218">Product Alternate Id</span><span class="sxs-lookup"><span data-stu-id="dad18-218">Product Alternate Id</span></span>|  
    |<span data-ttu-id="dad18-219">ProductSubcategoryKey</span><span class="sxs-lookup"><span data-stu-id="dad18-219">ProductSubcategoryKey</span></span>|<span data-ttu-id="dad18-220">Product Subcategory Id</span><span class="sxs-lookup"><span data-stu-id="dad18-220">Product Subcategory Id</span></span>|  
    |<span data-ttu-id="dad18-221">WeightUnitMeasureCode</span><span class="sxs-lookup"><span data-stu-id="dad18-221">WeightUnitMeasureCode</span></span>|<span data-ttu-id="dad18-222">Weight Unit Code</span><span class="sxs-lookup"><span data-stu-id="dad18-222">Weight Unit Code</span></span>|  
    |<span data-ttu-id="dad18-223">SizeUnitMeasureCode</span><span class="sxs-lookup"><span data-stu-id="dad18-223">SizeUnitMeasureCode</span></span>|<span data-ttu-id="dad18-224">Size Unit Code</span><span class="sxs-lookup"><span data-stu-id="dad18-224">Size Unit Code</span></span>|  
    |<span data-ttu-id="dad18-225">EnglishProductName</span><span class="sxs-lookup"><span data-stu-id="dad18-225">EnglishProductName</span></span>|<span data-ttu-id="dad18-226">产品名称</span><span class="sxs-lookup"><span data-stu-id="dad18-226">Product Name</span></span>|  
    |<span data-ttu-id="dad18-227">StandardCost</span><span class="sxs-lookup"><span data-stu-id="dad18-227">StandardCost</span></span>|<span data-ttu-id="dad18-228">标准成本</span><span class="sxs-lookup"><span data-stu-id="dad18-228">Standard Cost</span></span>|  
    |<span data-ttu-id="dad18-229">FinishedGoodsFlag</span><span class="sxs-lookup"><span data-stu-id="dad18-229">FinishedGoodsFlag</span></span>|<span data-ttu-id="dad18-230">Is Finished Product</span><span class="sxs-lookup"><span data-stu-id="dad18-230">Is Finished Product</span></span>|  
    |<span data-ttu-id="dad18-231">SafetyStockLevel</span><span class="sxs-lookup"><span data-stu-id="dad18-231">SafetyStockLevel</span></span>|<span data-ttu-id="dad18-232">Safety Stock Level</span><span class="sxs-lookup"><span data-stu-id="dad18-232">Safety Stock Level</span></span>|  
    |<span data-ttu-id="dad18-233">ReorderPoint</span><span class="sxs-lookup"><span data-stu-id="dad18-233">ReorderPoint</span></span>|<span data-ttu-id="dad18-234">Reorder Point</span><span class="sxs-lookup"><span data-stu-id="dad18-234">Reorder Point</span></span>|  
    |<span data-ttu-id="dad18-235">ListPrice</span><span class="sxs-lookup"><span data-stu-id="dad18-235">ListPrice</span></span>|<span data-ttu-id="dad18-236">标价</span><span class="sxs-lookup"><span data-stu-id="dad18-236">List Price</span></span>|  
    |<span data-ttu-id="dad18-237">SizeRange</span><span class="sxs-lookup"><span data-stu-id="dad18-237">SizeRange</span></span>|<span data-ttu-id="dad18-238">Size Range</span><span class="sxs-lookup"><span data-stu-id="dad18-238">Size Range</span></span>|  
    |<span data-ttu-id="dad18-239">DaysToManufacture</span><span class="sxs-lookup"><span data-stu-id="dad18-239">DaysToManufacture</span></span>|<span data-ttu-id="dad18-240">Days to Manufacture</span><span class="sxs-lookup"><span data-stu-id="dad18-240">Days to Manufacture</span></span>|  
    |<span data-ttu-id="dad18-241">ProductLine</span><span class="sxs-lookup"><span data-stu-id="dad18-241">ProductLine</span></span>|<span data-ttu-id="dad18-242">Product Line</span><span class="sxs-lookup"><span data-stu-id="dad18-242">Product Line</span></span>|  
    |<span data-ttu-id="dad18-243">经销价格</span><span class="sxs-lookup"><span data-stu-id="dad18-243">Dealer Price</span></span>|<span data-ttu-id="dad18-244">经销价格</span><span class="sxs-lookup"><span data-stu-id="dad18-244">Dealer Price</span></span>|  
    |<span data-ttu-id="dad18-245">ModelName</span><span class="sxs-lookup"><span data-stu-id="dad18-245">ModelName</span></span>|<span data-ttu-id="dad18-246">模型名称</span><span class="sxs-lookup"><span data-stu-id="dad18-246">Model Name</span></span>|  
    |<span data-ttu-id="dad18-247">LargePhoto</span><span class="sxs-lookup"><span data-stu-id="dad18-247">LargePhoto</span></span>|<span data-ttu-id="dad18-248">Large Photo</span><span class="sxs-lookup"><span data-stu-id="dad18-248">Large Photo</span></span>|  
    |<span data-ttu-id="dad18-249">EnglishDescription</span><span class="sxs-lookup"><span data-stu-id="dad18-249">EnglishDescription</span></span>|<span data-ttu-id="dad18-250">说明</span><span class="sxs-lookup"><span data-stu-id="dad18-250">Description</span></span>|  
    |<span data-ttu-id="dad18-251">StartDate</span><span class="sxs-lookup"><span data-stu-id="dad18-251">StartDate</span></span>|<span data-ttu-id="dad18-252">Product Start Date</span><span class="sxs-lookup"><span data-stu-id="dad18-252">Product Start Date</span></span>|  
    |<span data-ttu-id="dad18-253">EndDate</span><span class="sxs-lookup"><span data-stu-id="dad18-253">EndDate</span></span>|<span data-ttu-id="dad18-254">Product End Date</span><span class="sxs-lookup"><span data-stu-id="dad18-254">Product End Date</span></span>|  
    |<span data-ttu-id="dad18-255">状态</span><span class="sxs-lookup"><span data-stu-id="dad18-255">Status</span></span>|<span data-ttu-id="dad18-256">Product Status</span><span class="sxs-lookup"><span data-stu-id="dad18-256">Product Status</span></span>|  
  
     <span data-ttu-id="dad18-257">**产品类别**</span><span class="sxs-lookup"><span data-stu-id="dad18-257">**Product Category**</span></span>  
  
    |<span data-ttu-id="dad18-258">源名称</span><span class="sxs-lookup"><span data-stu-id="dad18-258">Source Name</span></span>|<span data-ttu-id="dad18-259">友好名称</span><span class="sxs-lookup"><span data-stu-id="dad18-259">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="dad18-260">ProductCategoryKey</span><span class="sxs-lookup"><span data-stu-id="dad18-260">ProductCategoryKey</span></span>|<span data-ttu-id="dad18-261">Product Category Id</span><span class="sxs-lookup"><span data-stu-id="dad18-261">Product Category Id</span></span>|  
    |<span data-ttu-id="dad18-262">ProductCategoryAlternateKey</span><span class="sxs-lookup"><span data-stu-id="dad18-262">ProductCategoryAlternateKey</span></span>|<span data-ttu-id="dad18-263">Product Category Alternate Id</span><span class="sxs-lookup"><span data-stu-id="dad18-263">Product Category Alternate Id</span></span>|  
    |<span data-ttu-id="dad18-264">EnglishProductCategoryName</span><span class="sxs-lookup"><span data-stu-id="dad18-264">EnglishProductCategoryName</span></span>|<span data-ttu-id="dad18-265">Product Category Name</span><span class="sxs-lookup"><span data-stu-id="dad18-265">Product Category Name</span></span>|  
  
     <span data-ttu-id="dad18-266">**Product Subcategory**</span><span class="sxs-lookup"><span data-stu-id="dad18-266">**Product Subcategory**</span></span>  
  
    |<span data-ttu-id="dad18-267">源名称</span><span class="sxs-lookup"><span data-stu-id="dad18-267">Source Name</span></span>|<span data-ttu-id="dad18-268">友好名称</span><span class="sxs-lookup"><span data-stu-id="dad18-268">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="dad18-269">ProductSubcategoryKey</span><span class="sxs-lookup"><span data-stu-id="dad18-269">ProductSubcategoryKey</span></span>|<span data-ttu-id="dad18-270">Product Subcategory Id</span><span class="sxs-lookup"><span data-stu-id="dad18-270">Product Subcategory Id</span></span>|  
    |<span data-ttu-id="dad18-271">ProductSubcategoryAlternateKey</span><span class="sxs-lookup"><span data-stu-id="dad18-271">ProductSubcategoryAlternateKey</span></span>|<span data-ttu-id="dad18-272">Product Subcategory Alternate Id</span><span class="sxs-lookup"><span data-stu-id="dad18-272">Product Subcategory Alternate Id</span></span>|  
    |<span data-ttu-id="dad18-273">EnglishProductSubcategoryName</span><span class="sxs-lookup"><span data-stu-id="dad18-273">EnglishProductSubcategoryName</span></span>|<span data-ttu-id="dad18-274">Product Subcategory Name</span><span class="sxs-lookup"><span data-stu-id="dad18-274">Product Subcategory Name</span></span>|  
    |<span data-ttu-id="dad18-275">ProductCategoryKey</span><span class="sxs-lookup"><span data-stu-id="dad18-275">ProductCategoryKey</span></span>|<span data-ttu-id="dad18-276">Product Category Id</span><span class="sxs-lookup"><span data-stu-id="dad18-276">Product Category Id</span></span>|  
  
     <span data-ttu-id="dad18-277">**Internet Sales**</span><span class="sxs-lookup"><span data-stu-id="dad18-277">**Internet Sales**</span></span>  
  
    |<span data-ttu-id="dad18-278">源名称</span><span class="sxs-lookup"><span data-stu-id="dad18-278">Source Name</span></span>|<span data-ttu-id="dad18-279">友好名称</span><span class="sxs-lookup"><span data-stu-id="dad18-279">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="dad18-280">ProductKey</span><span class="sxs-lookup"><span data-stu-id="dad18-280">ProductKey</span></span>|<span data-ttu-id="dad18-281">Product Id</span><span class="sxs-lookup"><span data-stu-id="dad18-281">Product Id</span></span>|  
    |<span data-ttu-id="dad18-282">CustomerKey</span><span class="sxs-lookup"><span data-stu-id="dad18-282">CustomerKey</span></span>|<span data-ttu-id="dad18-283">Customer Id</span><span class="sxs-lookup"><span data-stu-id="dad18-283">Customer Id</span></span>|  
    |<span data-ttu-id="dad18-284">PromotionKey</span><span class="sxs-lookup"><span data-stu-id="dad18-284">PromotionKey</span></span>|<span data-ttu-id="dad18-285">Promotion Id</span><span class="sxs-lookup"><span data-stu-id="dad18-285">Promotion Id</span></span>|  
    |<span data-ttu-id="dad18-286">CurrencyKey</span><span class="sxs-lookup"><span data-stu-id="dad18-286">CurrencyKey</span></span>|<span data-ttu-id="dad18-287">Currency Id</span><span class="sxs-lookup"><span data-stu-id="dad18-287">Currency Id</span></span>|  
    |<span data-ttu-id="dad18-288">SalesTerritoryKey</span><span class="sxs-lookup"><span data-stu-id="dad18-288">SalesTerritoryKey</span></span>|<span data-ttu-id="dad18-289">Sales Territory Id</span><span class="sxs-lookup"><span data-stu-id="dad18-289">Sales Territory Id</span></span>|  
    |<span data-ttu-id="dad18-290">SalesOrderNumber</span><span class="sxs-lookup"><span data-stu-id="dad18-290">SalesOrderNumber</span></span>|<span data-ttu-id="dad18-291">Sales Order Number</span><span class="sxs-lookup"><span data-stu-id="dad18-291">Sales Order Number</span></span>|  
    |<span data-ttu-id="dad18-292">SalesOrderLineNumber</span><span class="sxs-lookup"><span data-stu-id="dad18-292">SalesOrderLineNumber</span></span>|<span data-ttu-id="dad18-293">Sales Order Line Number</span><span class="sxs-lookup"><span data-stu-id="dad18-293">Sales Order Line Number</span></span>|  
    |<span data-ttu-id="dad18-294">RevisionNumber</span><span class="sxs-lookup"><span data-stu-id="dad18-294">RevisionNumber</span></span>|<span data-ttu-id="dad18-295">修订号</span><span class="sxs-lookup"><span data-stu-id="dad18-295">Revision Number</span></span>|  
    |<span data-ttu-id="dad18-296">OrderQuantity</span><span class="sxs-lookup"><span data-stu-id="dad18-296">OrderQuantity</span></span>|<span data-ttu-id="dad18-297">Order Quantity</span><span class="sxs-lookup"><span data-stu-id="dad18-297">Order Quantity</span></span>|  
    |<span data-ttu-id="dad18-298">UnitPrice</span><span class="sxs-lookup"><span data-stu-id="dad18-298">UnitPrice</span></span>|<span data-ttu-id="dad18-299">Unit Price</span><span class="sxs-lookup"><span data-stu-id="dad18-299">Unit Price</span></span>|  
    |<span data-ttu-id="dad18-300">ExtendedAmount</span><span class="sxs-lookup"><span data-stu-id="dad18-300">ExtendedAmount</span></span>|<span data-ttu-id="dad18-301">Extended Amount</span><span class="sxs-lookup"><span data-stu-id="dad18-301">Extended Amount</span></span>|  
    |<span data-ttu-id="dad18-302">UnitPriceDiscountPct</span><span class="sxs-lookup"><span data-stu-id="dad18-302">UnitPriceDiscountPct</span></span>|<span data-ttu-id="dad18-303">Unit Price Discount Pct</span><span class="sxs-lookup"><span data-stu-id="dad18-303">Unit Price Discount Pct</span></span>|  
    |<span data-ttu-id="dad18-304">DiscountAmount</span><span class="sxs-lookup"><span data-stu-id="dad18-304">DiscountAmount</span></span>|<span data-ttu-id="dad18-305">Discount Amount</span><span class="sxs-lookup"><span data-stu-id="dad18-305">Discount Amount</span></span>|  
    |<span data-ttu-id="dad18-306">ProductStandardCost</span><span class="sxs-lookup"><span data-stu-id="dad18-306">ProductStandardCost</span></span>|<span data-ttu-id="dad18-307">Product Standard Cost</span><span class="sxs-lookup"><span data-stu-id="dad18-307">Product Standard Cost</span></span>|  
    |<span data-ttu-id="dad18-308">TotalProductCost</span><span class="sxs-lookup"><span data-stu-id="dad18-308">TotalProductCost</span></span>|<span data-ttu-id="dad18-309">Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="dad18-309">Total Product Cost</span></span>|  
    |<span data-ttu-id="dad18-310">销售额</span><span class="sxs-lookup"><span data-stu-id="dad18-310">SalesAmount</span></span>|<span data-ttu-id="dad18-311">Sales Amount</span><span class="sxs-lookup"><span data-stu-id="dad18-311">Sales Amount</span></span>|  
    |<span data-ttu-id="dad18-312">TaxAmt</span><span class="sxs-lookup"><span data-stu-id="dad18-312">TaxAmt</span></span>|<span data-ttu-id="dad18-313">税额</span><span class="sxs-lookup"><span data-stu-id="dad18-313">Tax Amt</span></span>|  
    |<span data-ttu-id="dad18-314">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="dad18-314">CarrierTrackingNumber</span></span>|<span data-ttu-id="dad18-315">Carrier Tracking Number</span><span class="sxs-lookup"><span data-stu-id="dad18-315">Carrier Tracking Number</span></span>|  
    |<span data-ttu-id="dad18-316">CustomerPONumber</span><span class="sxs-lookup"><span data-stu-id="dad18-316">CustomerPONumber</span></span>|<span data-ttu-id="dad18-317">Customer PO Number</span><span class="sxs-lookup"><span data-stu-id="dad18-317">Customer PO Number</span></span>|  
    |<span data-ttu-id="dad18-318">OrderDate</span><span class="sxs-lookup"><span data-stu-id="dad18-318">OrderDate</span></span>|<span data-ttu-id="dad18-319">Order Date</span><span class="sxs-lookup"><span data-stu-id="dad18-319">Order Date</span></span>|  
    |<span data-ttu-id="dad18-320">DueDate</span><span class="sxs-lookup"><span data-stu-id="dad18-320">DueDate</span></span>|<span data-ttu-id="dad18-321">Due Date</span><span class="sxs-lookup"><span data-stu-id="dad18-321">Due Date</span></span>|  
    |<span data-ttu-id="dad18-322">ShipDate</span><span class="sxs-lookup"><span data-stu-id="dad18-322">ShipDate</span></span>|<span data-ttu-id="dad18-323">Ship Date</span><span class="sxs-lookup"><span data-stu-id="dad18-323">Ship Date</span></span>|  
  
## <a name="next-step"></a><span data-ttu-id="dad18-324">下一步</span><span class="sxs-lookup"><span data-stu-id="dad18-324">Next Step</span></span>  
 <span data-ttu-id="dad18-325">若要继续学习本教程，请转到下一课： [第 4 课：标记为日期表](lesson-3-mark-as-date-table.md)。</span><span class="sxs-lookup"><span data-stu-id="dad18-325">To continue this tutorial, go to the next lesson: [Lesson 4: Mark as Date Table](lesson-3-mark-as-date-table.md).</span></span>  
  
  
