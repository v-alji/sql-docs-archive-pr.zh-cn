---
title: 第2课：添加数据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 13c3a8cc-b1db-4aba-ad9b-038b7971be8d
author: minewiskan
ms.author: owend
ms.openlocfilehash: c844ea6558949407ca9b8206601ff7fe802ec399
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579858"
---
# <a name="lesson-2-add-data"></a><span data-ttu-id="ad938-102">第 2 课：添加数据</span><span class="sxs-lookup"><span data-stu-id="ad938-102">Lesson 2: Add Data</span></span>
  <span data-ttu-id="ad938-103">在本课程中，您将使用 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中的“表导入向导”连接到 AdventureWorksDW SQL 数据库，选择数据，预览并筛选数据，然后将数据导入到模型工作区中。</span><span class="sxs-lookup"><span data-stu-id="ad938-103">In this lesson, you will use the Table Import Wizard in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] to connect to the AdventureWorksDW SQL database, select data, preview, and filter the data, and then import the data into your model workspace.</span></span>  
  
 <span data-ttu-id="ad938-104">通过使用“表导入向导”，可以导入来自多种关系数据源的数据：Access、SQL、Oracle、Sybase、Informix、DB2、Teradata 等。</span><span class="sxs-lookup"><span data-stu-id="ad938-104">By using the Table Import Wizard, you can import data from a variety of relational sources: Access, SQL, Oracle, Sybase, Informix, DB2, Teradata, and more.</span></span> <span data-ttu-id="ad938-105">从上述关系数据源中的每个关系数据源导入数据的步骤与下面描述的步骤非常类似。</span><span class="sxs-lookup"><span data-stu-id="ad938-105">The steps for importing data from each of these relational sources are very similar to what is described below.</span></span> <span data-ttu-id="ad938-106">此外，还可以使用存储过程选择数据。</span><span class="sxs-lookup"><span data-stu-id="ad938-106">Additionally, data can be selected using a stored procedure.</span></span>  
  
 <span data-ttu-id="ad938-107">若要了解有关导入数据以及可从中导入的不同数据源类型的详细信息，请参阅[数据源（SSAS 表格）](data-sources-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="ad938-107">To learn more about importing data and the different types of data sources you can import from, see [Data Sources &#40;SSAS Tabular&#41;](data-sources-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="ad938-108">本课预计完成时间：**20 分钟**</span><span class="sxs-lookup"><span data-stu-id="ad938-108">Estimated time to complete this lesson: **20 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ad938-109">先决条件</span><span class="sxs-lookup"><span data-stu-id="ad938-109">Prerequisites</span></span>  
 <span data-ttu-id="ad938-110">本主题是表格建模教程的一部分，应当按顺序完成。</span><span class="sxs-lookup"><span data-stu-id="ad938-110">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="ad938-111">在执行本课程中的任务之前，应该已完成上一课： [第 1 课：创建新的表格模型项目](lesson-1-create-a-new-tabular-model-project.md)。</span><span class="sxs-lookup"><span data-stu-id="ad938-111">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 1: Create a New Tabular Model Project](lesson-1-create-a-new-tabular-model-project.md).</span></span>  
  
## <a name="create-a-connection"></a><span data-ttu-id="ad938-112">创建连接</span><span class="sxs-lookup"><span data-stu-id="ad938-112">Create a Connection</span></span>  
  
#### <a name="to-create-a-connection-to-a-the-adventureworksdw2012-database"></a><span data-ttu-id="ad938-113">创建到 AdventureWorksDW2012 数据库的连接</span><span class="sxs-lookup"><span data-stu-id="ad938-113">To create a connection to a the AdventureWorksDW2012 database</span></span>  
  
1.  <span data-ttu-id="ad938-114">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中，单击“模型”\*\*\*\* 菜单，然后单击“从数据源导入”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ad938-114">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click on the **Model** menu, and then click **Import from Data Source**.</span></span>  
  
     <span data-ttu-id="ad938-115">这将启动“表导入向导”，它将引导您设置与数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="ad938-115">This launches the Table Import Wizard which guides you through setting up a connection to a data source.</span></span> <span data-ttu-id="ad938-116">如果“从数据源导入”\*\*\*\* 处于灰显状态，则在“解决方案资源管理器”\*\*\*\* 中双击“Model.bim”\*\*\*\*，以便在设计器中打开模型。</span><span class="sxs-lookup"><span data-stu-id="ad938-116">If **Import from Data Source** is greyed out, double click **Model.bim** in **Solution Explorer** to open the model in the designer.</span></span>  
  
2.  <span data-ttu-id="ad938-117">在“表导入向导”\*\*\*\* 的“关系数据库”\*\*\*\* 下，单击“Microsoft SQL Server”\*\*\*\*，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ad938-117">In the **Table Import Wizard**, under **Relational Databases**, click **Microsoft SQL Server**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="ad938-118">在 "**连接到 Microsoft SQL Server 数据库**" 页的 "**友好连接名称**" 中，键入 `Adventure Works DB from SQL` 。</span><span class="sxs-lookup"><span data-stu-id="ad938-118">In the **Connect to a Microsoft SQL Server Database** page, in **Friendly Connection Name**, type `Adventure Works DB from SQL`.</span></span>  
  
4.  <span data-ttu-id="ad938-119">在“服务器名称”\*\*\*\* 中，键入安装了 AdventureWorksDW 数据库的服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="ad938-119">In **Server name**, type the name of the server you installed the AdventureWorksDW database.</span></span>  
  
5.  <span data-ttu-id="ad938-120">在“数据库名称”\*\*\*\* 字段中，单击向下箭头并选择“AdventureWorksDW”\*\*\*\*，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ad938-120">In the **Database name** field, click the down arrow and select **AdventureWorksDW**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="ad938-121">在“模拟信息”\*\*\*\* 页中，需要指定在导入和处理数据时 Analysis Services 将用于连接数据源的凭据。</span><span class="sxs-lookup"><span data-stu-id="ad938-121">In the **Impersonation Information** page, you need to specify the credentials Analysis Services will use to connect to the data source when importing and processing data.</span></span> <span data-ttu-id="ad938-122">确认已选中“特定的 Windows 用户名和密码”\*\*\*\*，在“用户名”\*\*\*\* 和“密码”\*\*\*\* 中输入 Windows 登录凭据，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ad938-122">Verify **Specific Windows user name and password** is selected, and then in **User Name** and **Password**, enter your Windows logon credentials, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ad938-123">使用 Windows 用户帐户和密码可以提供连接到数据源的最安全方法。</span><span class="sxs-lookup"><span data-stu-id="ad938-123">Using a Windows user account and password provides the most secure method of connecting to a data source.</span></span> <span data-ttu-id="ad938-124">有关详细信息，请参阅[模拟（SSAS 表格）](tabular-models/impersonation-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="ad938-124">For more information, see [Impersonation &#40;SSAS Tabular&#41;](tabular-models/impersonation-ssas-tabular.md).</span></span>  
  
7.  <span data-ttu-id="ad938-125">在“选择如何导入数据”\*\*\*\* 页中，确认已选中“从表和视图的列表中进行选择，以便选择要导入的数据”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ad938-125">In the **Choose How to Import the Data** page, verify **Select from a list of tables and views to choose the data to import** is selected.</span></span> <span data-ttu-id="ad938-126">需要从表和视图的列表中进行选择，因此，单击“下一步”\*\*\*\* 以便显示源数据库内所有源表的列表。</span><span class="sxs-lookup"><span data-stu-id="ad938-126">You want to select from a list of tables and views, so click **Next** to display a list of all the source tables in the source database.</span></span>  
  
8.  <span data-ttu-id="ad938-127">在“选择表和视图”\*\*\*\* 页中，选中以下各表的复选框：“DimCustomer”\*\*\*\*、“DimDate”\*\*\*\*、“DimGeography”\*\*\*\*、“DimProduct”\*\*\*\*、“DimProductCategory”\*\*\*\*、“DimProductSubcategory”\*\*\*\* 和“FactInternetSales”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ad938-127">In the **Select Tables and Views** page, select the check box for the following tables: **DimCustomer**, **DimDate**, **DimGeography**, **DimProduct**, **DimProductCategory**, **DimProductSubcategory**, and **FactInternetSales**.</span></span>  
  
9. <span data-ttu-id="ad938-128">我们希望为模型中的表提供更易理解的名称。</span><span class="sxs-lookup"><span data-stu-id="ad938-128">We want to give the tables in the model more easily understood names.</span></span> <span data-ttu-id="ad938-129">单击“友好名称”\*\*\*\* 列中对应于“DimCustomer”\*\*\*\* 的单元格。</span><span class="sxs-lookup"><span data-stu-id="ad938-129">Click on the cell in the **Friendly Name** column for **DimCustomer**.</span></span> <span data-ttu-id="ad938-130">通过从 DimCustomer 中删除 "Dim" 重命名该表。</span><span class="sxs-lookup"><span data-stu-id="ad938-130">Rename the table by removing "Dim" from DimCustomer.</span></span>  
  
10. <span data-ttu-id="ad938-131">重命名其他表：</span><span class="sxs-lookup"><span data-stu-id="ad938-131">Rename the other tables:</span></span>  
  
    |<span data-ttu-id="ad938-132">源名称</span><span class="sxs-lookup"><span data-stu-id="ad938-132">Source name</span></span>|<span data-ttu-id="ad938-133">友好名称</span><span class="sxs-lookup"><span data-stu-id="ad938-133">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="ad938-134">DimDate</span><span class="sxs-lookup"><span data-stu-id="ad938-134">DimDate</span></span>|<span data-ttu-id="ad938-135">Date</span><span class="sxs-lookup"><span data-stu-id="ad938-135">Date</span></span>|  
    |<span data-ttu-id="ad938-136">DimGeography</span><span class="sxs-lookup"><span data-stu-id="ad938-136">DimGeography</span></span>|<span data-ttu-id="ad938-137">地理位置</span><span class="sxs-lookup"><span data-stu-id="ad938-137">Geography</span></span>|  
    |<span data-ttu-id="ad938-138">DimProduct</span><span class="sxs-lookup"><span data-stu-id="ad938-138">DimProduct</span></span>|<span data-ttu-id="ad938-139">产品</span><span class="sxs-lookup"><span data-stu-id="ad938-139">Product</span></span>|  
    |<span data-ttu-id="ad938-140">DimProductCategory</span><span class="sxs-lookup"><span data-stu-id="ad938-140">DimProductCategory</span></span>|<span data-ttu-id="ad938-141">产品类别</span><span class="sxs-lookup"><span data-stu-id="ad938-141">Product Category</span></span>|  
    |<span data-ttu-id="ad938-142">DimProductSubcategory</span><span class="sxs-lookup"><span data-stu-id="ad938-142">DimProductSubcategory</span></span>|<span data-ttu-id="ad938-143">Product Subcategory</span><span class="sxs-lookup"><span data-stu-id="ad938-143">Product Subcategory</span></span>|  
    |<span data-ttu-id="ad938-144">FactInternetSales</span><span class="sxs-lookup"><span data-stu-id="ad938-144">FactInternetSales</span></span>|<span data-ttu-id="ad938-145">Internet Sales</span><span class="sxs-lookup"><span data-stu-id="ad938-145">Internet Sales</span></span>|  
  
     <span data-ttu-id="ad938-146">**请不要**单击“完成”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ad938-146">**DO NOT** click **Finish**.</span></span>  
  
 <span data-ttu-id="ad938-147">现在已连接到数据库，选择了要导入的表，并向表提供了友好名称，请转到下一部分：[导入之前对表数据进行筛选](#FilterData)。</span><span class="sxs-lookup"><span data-stu-id="ad938-147">Now that you have connected to the database, selected the tables to import, and given the tables friendly names, go to the next section, [Filter the Table Data prior to Importing](#FilterData).</span></span>  
  
##  <a name="filter-the-table-data"></a><a name="FilterData"></a><span data-ttu-id="ad938-148">筛选表数据</span><span class="sxs-lookup"><span data-stu-id="ad938-148">Filter the Table Data</span></span>  
 <span data-ttu-id="ad938-149">您正在从数据库中导入的 DimCustomer 表包含来自原始 SQL Server Adventure Works 数据库的数据子集。</span><span class="sxs-lookup"><span data-stu-id="ad938-149">The DimCustomer table that you are importing from the database contains a subset of the data from the original SQL Server Adventure Works database.</span></span> <span data-ttu-id="ad938-150">您将从 DimCustomer 表中筛选掉不必要的某些列。</span><span class="sxs-lookup"><span data-stu-id="ad938-150">You will filter out some of the columns from the DimCustomer table that aren't necessary.</span></span> <span data-ttu-id="ad938-151">如果可能，您希望筛选掉将不使用的数据，以便节省模型使用的内存中空间。</span><span class="sxs-lookup"><span data-stu-id="ad938-151">When possible, you will want to filter out data that will not be used in order to save in-memory space used by the model.</span></span>  
  
#### <a name="to-filter-the-table-data-prior-to-importing"></a><span data-ttu-id="ad938-152">导入之前对表数据进行筛选</span><span class="sxs-lookup"><span data-stu-id="ad938-152">To filter the table data prior to importing</span></span>  
  
1.  <span data-ttu-id="ad938-153">选择“Customer”\*\*\*\* 表中的行，然后单击“预览并筛选”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ad938-153">Select the row for the **Customer** table, and then click **Preview & Filter**.</span></span> <span data-ttu-id="ad938-154">“预览所选表”\*\*\*\* 窗口将打开，其中显示“DimCustomer”源表中的所有列。</span><span class="sxs-lookup"><span data-stu-id="ad938-154">The **Preview Selected Table** window opens with all the columns in the DimCustomer source table displayed.</span></span>  
  
2.  <span data-ttu-id="ad938-155">清除位于以下各列顶部的复选框：</span><span class="sxs-lookup"><span data-stu-id="ad938-155">Clear the checkbox at the top of the following columns:</span></span>  
  
    |<span data-ttu-id="ad938-156">客户</span><span class="sxs-lookup"><span data-stu-id="ad938-156">Customer</span></span>|  
    |--------------|  
    |<span data-ttu-id="ad938-157">**SpanishEducation**</span><span class="sxs-lookup"><span data-stu-id="ad938-157">**SpanishEducation**</span></span>|  
    |<span data-ttu-id="ad938-158">**FrenchEducation**</span><span class="sxs-lookup"><span data-stu-id="ad938-158">**FrenchEducation**</span></span>|  
    |<span data-ttu-id="ad938-159">**SpanishOccupation**</span><span class="sxs-lookup"><span data-stu-id="ad938-159">**SpanishOccupation**</span></span>|  
    |<span data-ttu-id="ad938-160">**FrenchOccupation**</span><span class="sxs-lookup"><span data-stu-id="ad938-160">**FrenchOccupation**</span></span>|  
  
     <span data-ttu-id="ad938-161">因为这些列的值与互联网销售分析无关，所以不需要导入这些列。</span><span class="sxs-lookup"><span data-stu-id="ad938-161">Since the values for these columns are not relevant to Internet sales analysis, there is no need to import these columns.</span></span> <span data-ttu-id="ad938-162">消除不必要的列将使您的模型变小。</span><span class="sxs-lookup"><span data-stu-id="ad938-162">Eliminating unnecessary columns will make your model smaller.</span></span>  
  
3.  <span data-ttu-id="ad938-163">确认已选中所有其他列，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ad938-163">Verify that all other columns are checked, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ad938-164">请注意，"**应用的筛选器**" 字样现在显示在**Customer**行的 "**筛选器详细信息**" 列中。如果单击该链接，您将看到您刚刚应用的筛选器的文本说明。</span><span class="sxs-lookup"><span data-stu-id="ad938-164">Notice the words **Applied filters** are now displayed in the **Filter Details** column in the **Customer** row; if you click on that link you'll see a text description of the filters you just applied.</span></span>  
  
4.  <span data-ttu-id="ad938-165">通过针对每个表中的以下各列清除复选框，筛选其余的表：</span><span class="sxs-lookup"><span data-stu-id="ad938-165">Filter the remaining tables by clearing the checkboxes for the following columns in each table:</span></span>  
  
    |<span data-ttu-id="ad938-166">Date</span><span class="sxs-lookup"><span data-stu-id="ad938-166">Date</span></span>|  
    |----------|  
    |<span data-ttu-id="ad938-167">**DateKey**</span><span class="sxs-lookup"><span data-stu-id="ad938-167">**DateKey**</span></span>|  
    |<span data-ttu-id="ad938-168">**SpanishDayNameOfWeek**</span><span class="sxs-lookup"><span data-stu-id="ad938-168">**SpanishDayNameOfWeek**</span></span>|  
    |<span data-ttu-id="ad938-169">**FrenchDayNameOfWeek**</span><span class="sxs-lookup"><span data-stu-id="ad938-169">**FrenchDayNameOfWeek**</span></span>|  
    |<span data-ttu-id="ad938-170">**SpanishMonthName**</span><span class="sxs-lookup"><span data-stu-id="ad938-170">**SpanishMonthName**</span></span>|  
    |<span data-ttu-id="ad938-171">**FrenchMonthName**</span><span class="sxs-lookup"><span data-stu-id="ad938-171">**FrenchMonthName**</span></span>|  
  
    |<span data-ttu-id="ad938-172">地理位置</span><span class="sxs-lookup"><span data-stu-id="ad938-172">Geography</span></span>|  
    |---------------|  
    |<span data-ttu-id="ad938-173">**SpanishCountryRegionName**</span><span class="sxs-lookup"><span data-stu-id="ad938-173">**SpanishCountryRegionName**</span></span>|  
    |<span data-ttu-id="ad938-174">**FrenchCountryRegionName**</span><span class="sxs-lookup"><span data-stu-id="ad938-174">**FrenchCountryRegionName**</span></span>|  
    |<span data-ttu-id="ad938-175">**IpAddressLocator**</span><span class="sxs-lookup"><span data-stu-id="ad938-175">**IpAddressLocator**</span></span>|  
  
    |<span data-ttu-id="ad938-176">产品</span><span class="sxs-lookup"><span data-stu-id="ad938-176">Product</span></span>|  
    |-------------|  
    |<span data-ttu-id="ad938-177">**SpanishProductName**</span><span class="sxs-lookup"><span data-stu-id="ad938-177">**SpanishProductName**</span></span>|  
    |<span data-ttu-id="ad938-178">**FrenchProductName**</span><span class="sxs-lookup"><span data-stu-id="ad938-178">**FrenchProductName**</span></span>|  
    |<span data-ttu-id="ad938-179">**FrenchDescription**</span><span class="sxs-lookup"><span data-stu-id="ad938-179">**FrenchDescription**</span></span>|  
    |<span data-ttu-id="ad938-180">**ChineseDescription**</span><span class="sxs-lookup"><span data-stu-id="ad938-180">**ChineseDescription**</span></span>|  
    |<span data-ttu-id="ad938-181">**ArabicDescription**</span><span class="sxs-lookup"><span data-stu-id="ad938-181">**ArabicDescription**</span></span>|  
    |<span data-ttu-id="ad938-182">**HebrewDescription**</span><span class="sxs-lookup"><span data-stu-id="ad938-182">**HebrewDescription**</span></span>|  
    |<span data-ttu-id="ad938-183">**ThaiDescription**</span><span class="sxs-lookup"><span data-stu-id="ad938-183">**ThaiDescription**</span></span>|  
    |<span data-ttu-id="ad938-184">**GermanDescription**</span><span class="sxs-lookup"><span data-stu-id="ad938-184">**GermanDescription**</span></span>|  
    |<span data-ttu-id="ad938-185">**JapaneseDescription**</span><span class="sxs-lookup"><span data-stu-id="ad938-185">**JapaneseDescription**</span></span>|  
    |<span data-ttu-id="ad938-186">**TurkishDescription**</span><span class="sxs-lookup"><span data-stu-id="ad938-186">**TurkishDescription**</span></span>|  
  
    |<span data-ttu-id="ad938-187">产品类别</span><span class="sxs-lookup"><span data-stu-id="ad938-187">Product Category</span></span>|  
    |----------------------|  
    |<span data-ttu-id="ad938-188">**SpanishProductCategoryName**</span><span class="sxs-lookup"><span data-stu-id="ad938-188">**SpanishProductCategoryName**</span></span>|  
    |<span data-ttu-id="ad938-189">**FrenchProductCategoryName**</span><span class="sxs-lookup"><span data-stu-id="ad938-189">**FrenchProductCategoryName**</span></span>|  
  
    |<span data-ttu-id="ad938-190">Product Subcategory</span><span class="sxs-lookup"><span data-stu-id="ad938-190">Product Subcategory</span></span>|  
    |-------------------------|  
    |<span data-ttu-id="ad938-191">**SpanishProductSubcategoryName**</span><span class="sxs-lookup"><span data-stu-id="ad938-191">**SpanishProductSubcategoryName**</span></span>|  
    |<span data-ttu-id="ad938-192">**FrenchProductSubcategoryName**</span><span class="sxs-lookup"><span data-stu-id="ad938-192">**FrenchProductSubcategoryName**</span></span>|  
  
    |<span data-ttu-id="ad938-193">Internet Sales</span><span class="sxs-lookup"><span data-stu-id="ad938-193">Internet Sales</span></span>|  
    |--------------------|  
    |<span data-ttu-id="ad938-194">**OrderDateKey**</span><span class="sxs-lookup"><span data-stu-id="ad938-194">**OrderDateKey**</span></span>|  
    |<span data-ttu-id="ad938-195">**DueDateKey**</span><span class="sxs-lookup"><span data-stu-id="ad938-195">**DueDateKey**</span></span>|  
    |<span data-ttu-id="ad938-196">**ShipDateKey**</span><span class="sxs-lookup"><span data-stu-id="ad938-196">**ShipDateKey**</span></span>|  
  
 <span data-ttu-id="ad938-197">既然您已预览并筛选掉了不必要的数据，您可以导入数据了。</span><span class="sxs-lookup"><span data-stu-id="ad938-197">Now that you have previewed and filtered out unnecessary data, you can import the data.</span></span> <span data-ttu-id="ad938-198">转到下一部分： **导入选择的表和列数据**。</span><span class="sxs-lookup"><span data-stu-id="ad938-198">Go to the next section **Import the Selected Tables and Column Data**.</span></span>  
  
##  <a name="import-the-selected-tables-and-column-data"></a><a name="Import"></a><span data-ttu-id="ad938-199">导入所选的表和列数据</span><span class="sxs-lookup"><span data-stu-id="ad938-199">Import the Selected Tables and Column Data</span></span>  
 <span data-ttu-id="ad938-200">现在您可以导入所选数据。</span><span class="sxs-lookup"><span data-stu-id="ad938-200">You can now import the selected data.</span></span> <span data-ttu-id="ad938-201">向导将导入表数据以及各个表之间的关系。</span><span class="sxs-lookup"><span data-stu-id="ad938-201">The wizard imports the table data along with any relationships between tables.</span></span> <span data-ttu-id="ad938-202">将使用您指定的友好名称在模型中创建新表和列，并且不会导入您筛选掉的数据。</span><span class="sxs-lookup"><span data-stu-id="ad938-202">New tables and columns are created in the model using the friendly names you specified, and data that you filtered out will not be imported.</span></span>  
  
#### <a name="to-import-the-selected-tables-and-column-data"></a><span data-ttu-id="ad938-203">导入所选的表和列数据</span><span class="sxs-lookup"><span data-stu-id="ad938-203">To import the selected tables and column data</span></span>  
  
1.  <span data-ttu-id="ad938-204">复查选择。</span><span class="sxs-lookup"><span data-stu-id="ad938-204">Review your selections.</span></span> <span data-ttu-id="ad938-205">如果一切都看上去没什么问题，则单击“完成”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ad938-205">If everything looks OK, click **Finish**.</span></span>  
  
     <span data-ttu-id="ad938-206">导入数据时，该向导会显示已提取的行的数量。</span><span class="sxs-lookup"><span data-stu-id="ad938-206">While importing the data, the wizard displays how many rows have been fetched.</span></span> <span data-ttu-id="ad938-207">导入完所有数据之后，将显示一条指示成功的消息。</span><span class="sxs-lookup"><span data-stu-id="ad938-207">When all the data has been imported, a message indicating success is displayed.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="ad938-208">若要查看在导入的表之间自动创建的关系，请在“数据准备”\*\*\*\* 行上单击“详细信息”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ad938-208">To see the relationships that were automatically created between the imported tables, on the **Data preparation** row, click **Details**.</span></span>  
  
2.  <span data-ttu-id="ad938-209">单击 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="ad938-209">Click **Close**.</span></span>  
  
     <span data-ttu-id="ad938-210">该向导将关闭并且模型设计器将可见。</span><span class="sxs-lookup"><span data-stu-id="ad938-210">The wizard closes and the model designer is visible.</span></span> <span data-ttu-id="ad938-211">每个表都已作为新的选项卡添加到模型设计器中。</span><span class="sxs-lookup"><span data-stu-id="ad938-211">Each table has been added as a new tab in the model designer.</span></span>  
  
## <a name="save-the-model-project"></a><span data-ttu-id="ad938-212">保存模型项目</span><span class="sxs-lookup"><span data-stu-id="ad938-212">Save the Model Project</span></span>  
 <span data-ttu-id="ad938-213">请务必经常保存模型项目。</span><span class="sxs-lookup"><span data-stu-id="ad938-213">It is important to frequently save your model project.</span></span>  
  
#### <a name="to-save-the-model-project"></a><span data-ttu-id="ad938-214">保存模型项目</span><span class="sxs-lookup"><span data-stu-id="ad938-214">To save the model project</span></span>  
  
-   <span data-ttu-id="ad938-215">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中，单击“文件”\*\*\*\* 菜单，然后单击“全部保存”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ad938-215">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click on the **File** menu, and then click **Save All**.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="ad938-216">下一步</span><span class="sxs-lookup"><span data-stu-id="ad938-216">Next Step</span></span>  
 <span data-ttu-id="ad938-217">若要继续学习本教程，请转到下一课： [第 3 课：重命名列](rename-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="ad938-217">To continue this tutorial, go to the next lesson: [Lesson 3: Rename Columns](rename-columns.md).</span></span>  
  
  
