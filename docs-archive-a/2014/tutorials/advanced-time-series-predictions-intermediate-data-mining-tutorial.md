---
title: " (中级数据挖掘教程) 的高级时序预测 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b614ebdb-07ca-44af-a0ff-893364bd4b71
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 70ebf856ba0782cbf44969aba30602818015582a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691408"
---
# <a name="advanced-time-series-predictions-intermediate-data-mining-tutorial"></a><span data-ttu-id="da76b-102">高级时序预测（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="da76b-102">Advanced Time Series Predictions (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="da76b-103">通过浏览预测模型，您发现尽管大多数区域的销售额都遵循一个相似的模式，但是某些区域和某些型号（例如，太平洋地区的 M200 型号）却呈现出完全不同的趋势。</span><span class="sxs-lookup"><span data-stu-id="da76b-103">You saw from exploring the forecasting model that although sales in most of the regions follow a similar pattern, some regions and some models, such as the M200 model in the Pacific region, exhibit very different trends.</span></span> <span data-ttu-id="da76b-104">您对此并不感到惊奇，因为您知道区域之间的差异很常见，可以由多种因素引起，其中包括市场促销、错误的报告或地理政治事件。</span><span class="sxs-lookup"><span data-stu-id="da76b-104">This does not surprise you, as you know that differences among regions are common and can be caused by many factors, including marketing promotions, inaccurate reporting, or geopolitical events.</span></span>  
  
 <span data-ttu-id="da76b-105">但是，您的用户要求提供可在全球范围内应用的模型。</span><span class="sxs-lookup"><span data-stu-id="da76b-105">However, your users are asking for a model that can be applied worldwide.</span></span> <span data-ttu-id="da76b-106">因此，为了将各个因素对预测所造成的影响降至最低，您决定生成一个基于全球范围内销售额的聚合度量值的模型。</span><span class="sxs-lookup"><span data-stu-id="da76b-106">Therefore, to minimize the effect of individual factors on projections, you decide to build a model that is based on aggregated measures of worldwide sales.</span></span> <span data-ttu-id="da76b-107">然后，您可以使用此模型对每个区域进行预测。</span><span class="sxs-lookup"><span data-stu-id="da76b-107">You can then use this model to make predictions for each individual region.</span></span>  
  
 <span data-ttu-id="da76b-108">在本任务中，您将生成所需的所有数据源以执行高级预测任务。</span><span class="sxs-lookup"><span data-stu-id="da76b-108">In this task, you will build all the data sources that you need to perform the advanced prediction tasks.</span></span> <span data-ttu-id="da76b-109">您将创建两个数据源视图用作预测查询的输入，一个数据源视图用于生成新模型。</span><span class="sxs-lookup"><span data-stu-id="da76b-109">You will create two data source views for use as inputs to the prediction query, and one data source view to use in building a new model.</span></span>  
  
 <span data-ttu-id="da76b-110">**步骤**</span><span class="sxs-lookup"><span data-stu-id="da76b-110">**Steps**</span></span>  
  
1.  [<span data-ttu-id="da76b-111">准备扩展的销售额数据（用于预测）</span><span class="sxs-lookup"><span data-stu-id="da76b-111">Prepare the extended sales data (for prediction)</span></span>](#bkmk_newExtendData)  
  
2.  [<span data-ttu-id="da76b-112">准备聚合数据（用于生成模型）</span><span class="sxs-lookup"><span data-stu-id="da76b-112">Prepare the aggregated data (for building the model)</span></span>](#bkmk_newReplaceData)  
  
3.  [<span data-ttu-id="da76b-113">准备序列数据（用于交叉预测）</span><span class="sxs-lookup"><span data-stu-id="da76b-113">Prepare the series data (for cross-prediction)</span></span>](#bkmk_CrossData2)  
  
4.  [<span data-ttu-id="da76b-114">使用 EXTEND 进行预测</span><span class="sxs-lookup"><span data-stu-id="da76b-114">Predict using EXTEND</span></span>](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
5.  [<span data-ttu-id="da76b-115">创建交叉预测模型</span><span class="sxs-lookup"><span data-stu-id="da76b-115">Create the cross-prediction model</span></span>](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
6.  [<span data-ttu-id="da76b-116">使用 REPLACE 进行预测</span><span class="sxs-lookup"><span data-stu-id="da76b-116">Predict using REPLACE</span></span>](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
7.  [<span data-ttu-id="da76b-117">查看新预测</span><span class="sxs-lookup"><span data-stu-id="da76b-117">Review the new predictions</span></span>](../../2014/tutorials/comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial.md)  
  
##  <a name="creating-the-new-extended-sales-data"></a><a name="bkmk_newExtendData"></a><span data-ttu-id="da76b-118">创建新的扩展销售数据</span><span class="sxs-lookup"><span data-stu-id="da76b-118">Creating the New Extended Sales Data</span></span>  
 <span data-ttu-id="da76b-119">要更新您的销售额数据，您需要获取最新的销售额数字。</span><span class="sxs-lookup"><span data-stu-id="da76b-119">To update your sales data, you will need to get the latest sales figures.</span></span> <span data-ttu-id="da76b-120">特别关注来自太平洋地区的数据，该地区启动了区域性促销以吸引新商店的关注并提升产品知名度。</span><span class="sxs-lookup"><span data-stu-id="da76b-120">Of particular interest are the data just in from the Pacific region, which launched a regional sales promotion to call attention to the new stores and raise awareness of their products.</span></span>  
  
 <span data-ttu-id="da76b-121">对于此方案，我们假定已从 Excel 工作簿导入数据，该工作簿只包含几个月的新数据供几个区域使用。</span><span class="sxs-lookup"><span data-stu-id="da76b-121">For this scenario, we'll assume that the data has been imported from an Excel workbook that contains just three months of new data for a couple of regions.</span></span> <span data-ttu-id="da76b-122">您将使用 Transact-sql 脚本为数据创建一个表，然后定义要用于预测的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="da76b-122">You'll create a table for the data using a Transact-SQL script, and then define a data source view to use for prediction.</span></span>  
  
#### <a name="create-the-table-with-new-sales-data"></a><span data-ttu-id="da76b-123">使用新的销售额数据创建表</span><span class="sxs-lookup"><span data-stu-id="da76b-123">Create the table with new sales data</span></span>  
  
1.  <span data-ttu-id="da76b-124">在 Transact-SQL 查询窗口中，执行以下语句以将销售额数据添加到 AdventureWorksDW 数据库（或者任何其他数据库）。</span><span class="sxs-lookup"><span data-stu-id="da76b-124">In a Transact-SQL query window, execute the following statement to add the sales data to the AdventureWorksDW database (or any other database).</span></span>  
  
    ```  
    USE [database name];  
    GO  
    IF OBJECT_ID ([dbo].[NewSalesData]) IS NOT NULL   
        DROP TABLE [dbo].[NewSalesData];  
    GO  
    CREATE TABLE [dbo].[NewSalesData]([Series] [nvarchar](255) NULL,  
    [NewDate] [datetime] NULL,  
    [NewQty] [float] NULL,  
    [NewAmount] [money] NULL) ON [PRIMARY]  
  
    GO  
    ```  
  
2.  <span data-ttu-id="da76b-125">使用以下脚本插入新值。</span><span class="sxs-lookup"><span data-stu-id="da76b-125">Insert the new values using the following script.</span></span>  
  
    ```  
    INSERT INTO [NewSalesData]  
    (Series,NewDate,NewQty,NewAmount)  
    VALUES('T1000 Pacific', '7/25/08', 55, '$130,170.22'),  
    ('T1000 Pacific', '8/25/08', 50, '$114,435.36 '),  
    ('T1000 Pacific', '9/25/08', 50, '$117,296.24 '),  
    ('T1000 Europe', '7/25/08', 37, '$88,210.00 '),  
    ('T1000 Europe', '8/25/08', 41, '$97,746.00 '),  
    ('T1000 Europe', '9/25/08', 37, '$88,210.00 '),  
    ('T1000 North America', '7/25/08', 69, '$164,500.00 '),  
    ('T1000 North America', '8/25/08', 66, '$157,348.00 '),  
    ('T1000 North America', '9/25/08', 58, '$138,276.00 '),  
    ('M200 Pacific', '7/25/08', 65, '$149,824.35'),  
    ('M200 Pacific', '8/25/08', 54,  '$124,619.46'),  
    ('M200 Pacific', '9/25/08', 61, '$141,143.39'),  
    ('M200 Europe', '7/25/08', 75, '$173,026.00'),  
    ('M200 Europe', '8/25/08', 76, '$175,212.00'),  
    ('M200 Europe', '9/25/08', 84, '$193,731.00'),  
    ('M200 North America', '7/25/08', 94, '$216,916.00'),  
    ('M200 North America', '8/25/08', 94, '$216,891.00'),  
    ('M200 North America', '9/25/08', 91,'$209,943.00');  
    ```  
  
    > [!WARNING]  
    >  <span data-ttu-id="da76b-126">引号用于货币值，以防止出现逗号分隔符和货币符号的问题。</span><span class="sxs-lookup"><span data-stu-id="da76b-126">The quotation marks are used with the currency values to prevent problems with the comma separator and the currency symbol.</span></span> <span data-ttu-id="da76b-127">您还可以采用以下格式传入货币值：`130170.22`</span><span class="sxs-lookup"><span data-stu-id="da76b-127">You could also pass in the currency values in this format: `130170.22`</span></span>  
    >   
    >  <span data-ttu-id="da76b-128">请注意，在示例数据库中使用的日期对于此版本已更改。</span><span class="sxs-lookup"><span data-stu-id="da76b-128">Note that the dates used in the sample database have changed for this release.</span></span> <span data-ttu-id="da76b-129">如果您使用较早版本的 AdventureWorks，则可能需要对插入的日期进行相应的调整。</span><span class="sxs-lookup"><span data-stu-id="da76b-129">If you are using an earlier edition of AdventureWorks, you might need to adjust the inserted dates accordingly.</span></span>  
  
###  <a name="create-a-data-source-view-using-the-new-sales-data"></a><a name="bkmk_newReplaceData"></a><span data-ttu-id="da76b-130">使用新的销售数据创建数据源视图</span><span class="sxs-lookup"><span data-stu-id="da76b-130">Create a data source view using the new sales data</span></span>  
  
1.  <span data-ttu-id="da76b-131">在**解决方案资源管理器**中，右键单击 "**数据源视图**"，然后选择 "**新建数据源视图**"。</span><span class="sxs-lookup"><span data-stu-id="da76b-131">In **Solution Explorer**, right-click **Data Source Views**, and then select **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="da76b-132">在数据源视图向导中进行以下选择：</span><span class="sxs-lookup"><span data-stu-id="da76b-132">In the Data Source View wizard, make the following selections:</span></span>  
  
     <span data-ttu-id="da76b-133">**数据源**：[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da76b-133">**Data Source**: [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]</span></span>  
  
     <span data-ttu-id="da76b-134">**选择表和视图**：选择刚刚创建的表 NewSalesData。</span><span class="sxs-lookup"><span data-stu-id="da76b-134">**Select Tables and Views**: Select the table that you just created, NewSalesData.</span></span>  
  
3.  <span data-ttu-id="da76b-135">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="da76b-135">Click **Finish**.</span></span>  
  
4.  <span data-ttu-id="da76b-136">在数据源视图设计图面中，右键单击 NewSalesData，然后选择 "**浏览数据**" 以验证数据。</span><span class="sxs-lookup"><span data-stu-id="da76b-136">In the Data Source View design surface, right-click NewSalesData, and then select **Explore Data** to verify the data.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="da76b-137">您仅将此数据用于预测，因此数据是否完整并不重要。</span><span class="sxs-lookup"><span data-stu-id="da76b-137">You will use this data for prediction only, so it does not matter that the data is incomplete.</span></span>  
  
##  <a name="creating-the-data-for-the-cross-prediction-model"></a><a name="bkmk_CrossData2"></a><span data-ttu-id="da76b-138">创建跨预测模型的数据</span><span class="sxs-lookup"><span data-stu-id="da76b-138">Creating the Data for the Cross-Prediction Model</span></span>  
 <span data-ttu-id="da76b-139">在原始预测模型中使用的数据已被视图 vTimeSeries 略微分组，它将几个自行车型号折叠为更少的类别，将几个国家/地区的结果合并为区域结果。</span><span class="sxs-lookup"><span data-stu-id="da76b-139">The data that was used in the original forecasting model was already grouped somewhat by the view vTimeSeries, which collapsed several bike models into a smaller number of categories, and merged results from individual countries into regions.</span></span> <span data-ttu-id="da76b-140">为了创建可用于全球范围内预测的模型，您将直接在数据源视图设计器中创建一些其他简单的聚合。</span><span class="sxs-lookup"><span data-stu-id="da76b-140">To create a model that can be used for world-wide projections, you will create some additional simple aggregations directly in the Data Source View Designer.</span></span> <span data-ttu-id="da76b-141">新的数据源视图将仅包含所有产品在各个区域的销售额的总和以及平均值。</span><span class="sxs-lookup"><span data-stu-id="da76b-141">The new data source view will contain just a sum and an average of the sales of all products for all regions.</span></span>  
  
 <span data-ttu-id="da76b-142">创建了用于模型的数据源后，必须创建用于预测的新数据源视图。</span><span class="sxs-lookup"><span data-stu-id="da76b-142">After you have created the data source used for the model, you must create a new data source view to use for prediction.</span></span> <span data-ttu-id="da76b-143">例如，您要使用新的全球范围内模型预测欧洲的销售额，必须仅输入欧洲区域的数据。</span><span class="sxs-lookup"><span data-stu-id="da76b-143">For example, if you want to predict sales for Europe using the new worldwide model, you must feed in data for the Europe region only.</span></span> <span data-ttu-id="da76b-144">因此，您将设置一个筛选原始数据的新数据源视图，并为每组预测查询更改筛选条件。</span><span class="sxs-lookup"><span data-stu-id="da76b-144">So you will set up a new data source view that filters the original data, and change the filter condition for each set of prediction queries.</span></span>  
  
#### <a name="to-create-the-model-data-using-a-custom-data-source-view"></a><span data-ttu-id="da76b-145">使用自定义数据源视图创建模型数据</span><span class="sxs-lookup"><span data-stu-id="da76b-145">To create the model data using a custom data source view</span></span>  
  
1.  <span data-ttu-id="da76b-146">在**解决方案资源管理器**中，右键单击 "**数据源视图**"，然后选择 "**新建数据源视图**"。</span><span class="sxs-lookup"><span data-stu-id="da76b-146">In **Solution Explorer**, right-click **Data Source Views**, and then select **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="da76b-147">在向导的欢迎页上，单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="da76b-147">On the welcome page of the wizard, click **Next**.</span></span>  
  
3.  <span data-ttu-id="da76b-148">在 **“选择数据源”** 页上，选择 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="da76b-148">On the **Select Data Source** page, select [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)], and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="da76b-149">在 "**选择表和视图**" 页中，不添加任何表，只需单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="da76b-149">In the page, **Select Tables and Views**, do not add any tables-just click **Next**.</span></span>  
  
5.  <span data-ttu-id="da76b-150">在 "**完成向导**" 页上，键入名称 `AllRegions` ，然后单击 "**完成**"。</span><span class="sxs-lookup"><span data-stu-id="da76b-150">On the page, **Completing the Wizard**, type the name `AllRegions`, and then click **Finish**.</span></span>  
  
6.  <span data-ttu-id="da76b-151">接下来，右键单击空白数据源视图设计图面，然后选择 "**新建命名查询**"。</span><span class="sxs-lookup"><span data-stu-id="da76b-151">Next, right-click the blank data source view design surface, and then select **New Named Query**.</span></span>  
  
7.  <span data-ttu-id="da76b-152">在 "**创建命名查询**" 对话框中，为 "**名称**" 键入 `AllRegions` ，为 "**说明**" 键入**所有型号和区域的销售额的总和和平均值**。</span><span class="sxs-lookup"><span data-stu-id="da76b-152">In the **Create Named Query** dialog box, for **Name**, type `AllRegions`, and for **Description**, type **Sum and average of sales for all models and regions**.</span></span>  
  
8.  <span data-ttu-id="da76b-153">在“SQL 文本”窗格中键入以下语句，然后单击“确定”：</span><span class="sxs-lookup"><span data-stu-id="da76b-153">In the SQL text pane, type the following statement and then click OK:</span></span>  
  
    ```  
    SELECT ReportingDate,   
    SUM([Quantity]) as SumQty, AVG([Quantity]) as AvgQty,  
    SUM([Amount]) AS SumAmt, AVG([Amount]) AS AvgAmt,  
    'All Regions' as [Region]  
    FROM dbo.vTimeSeries   
    GROUP BY ReportingDate  
    ```  
  
9. <span data-ttu-id="da76b-154">右键单击 `AllRegions` 该表，然后选择 "**浏览数据**"。</span><span class="sxs-lookup"><span data-stu-id="da76b-154">Right-click the `AllRegions` table, and then select **Explore Data**.</span></span>  
  
###  <a name="to-create-the-series-data-for-cross-prediction"></a><a name="bkmk_CrossData"></a><span data-ttu-id="da76b-155">创建用于交叉预测的序列数据</span><span class="sxs-lookup"><span data-stu-id="da76b-155">To create the series data for cross-prediction</span></span>  
  
1.  <span data-ttu-id="da76b-156">在**解决方案资源管理器**中，右键单击 "**数据源视图**"，然后选择 "**新建数据源视图**"。</span><span class="sxs-lookup"><span data-stu-id="da76b-156">In **Solution Explorer**, right-click **Data Source Views**, and then select **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="da76b-157">在数据源视图向导中进行以下选择：</span><span class="sxs-lookup"><span data-stu-id="da76b-157">In the Data Source View wizard, make the following selections:</span></span>  
  
     <span data-ttu-id="da76b-158">**数据源**：[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da76b-158">**Data Source**: [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]</span></span>  
  
     <span data-ttu-id="da76b-159">**选择表和视图**：不选择任何表</span><span class="sxs-lookup"><span data-stu-id="da76b-159">**Select Tables and Views**: Do not select any tables</span></span>  
  
     <span data-ttu-id="da76b-160">**名称**：`T1000 Pacific Region`</span><span class="sxs-lookup"><span data-stu-id="da76b-160">**Name**: `T1000 Pacific Region`</span></span>  
  
3.  <span data-ttu-id="da76b-161">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="da76b-161">Click **Finish**.</span></span>  
  
4.  <span data-ttu-id="da76b-162">右键单击**T1000 太平洋 Region**的空设计图面，然后选择 "**新建命名查询**"。</span><span class="sxs-lookup"><span data-stu-id="da76b-162">Right-click the empty design surface for **T1000 Pacific Region.dsv**, and then select **New Named Query**.</span></span>  
  
     <span data-ttu-id="da76b-163">**“创建命名查询”** 对话框随即出现。</span><span class="sxs-lookup"><span data-stu-id="da76b-163">The **Create Named Query** dialog box appears.</span></span> <span data-ttu-id="da76b-164">重新键入名称，然后添加下面的说明：</span><span class="sxs-lookup"><span data-stu-id="da76b-164">Retype the name, and then add the following description:</span></span>  
  
     <span data-ttu-id="da76b-165">**名称**：`T1000 Pacific Region`</span><span class="sxs-lookup"><span data-stu-id="da76b-165">**Name**: `T1000 Pacific Region`</span></span>  
  
     <span data-ttu-id="da76b-166">**说明**： \*\* `vTimeSeries` 按区域和型号筛选\*\*</span><span class="sxs-lookup"><span data-stu-id="da76b-166">**Description**: **Filter`vTimeSeries`by region and model**</span></span>  
  
5.  <span data-ttu-id="da76b-167">在“文本”窗格中键入以下查询，然后单击“确定”：</span><span class="sxs-lookup"><span data-stu-id="da76b-167">In the text pane, type the following query, and then click OK:</span></span>  
  
    ```  
    SELECT ReportingDate, ModelRegion, Quantity, Amount  
    FROM dbo.vTimeSeries  
    WHERE (ModelRegion = N'T1000 Pacific')  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="da76b-168">由于需要单独为每个序列创建预测，您可能要复制查询文本并将其保存为文本文件，以便其他数据序列可以重用它。</span><span class="sxs-lookup"><span data-stu-id="da76b-168">Since you will need to create predictions for each series separately, you might want to copy the query text and save it to a text file so that you can re-use it for the other data series.</span></span>  
  
6.  <span data-ttu-id="da76b-169">在数据源视图设计图面中，右键单击 "T1000"，然后选择 "**浏览数据**" 以验证是否已正确筛选数据。</span><span class="sxs-lookup"><span data-stu-id="da76b-169">In the Data Source View design surface, right-click T1000 Pacific, and then select **Explore Data** to verify that the data is filtered correctly.</span></span>  
  
     <span data-ttu-id="da76b-170">在创建交叉预测查询时，您将使用此数据作为模型的输入。</span><span class="sxs-lookup"><span data-stu-id="da76b-170">You will use this data as the input to the model when creating cross-prediction queries.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="da76b-171">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="da76b-171">Next Task in Lesson</span></span>  
 [<span data-ttu-id="da76b-172">使用更新的数据 &#40;中级数据挖掘教程的时序预测&#41;</span><span class="sxs-lookup"><span data-stu-id="da76b-172">Time Series Predictions using Updated Data &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="da76b-173">另请参阅</span><span class="sxs-lookup"><span data-stu-id="da76b-173">See Also</span></span>  
 <span data-ttu-id="da76b-174">[Microsoft 时序算法](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="da76b-174">[Microsoft Time Series Algorithm](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md) </span></span>  
 <span data-ttu-id="da76b-175">[Microsoft 时序算法技术参考](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="da76b-175">[Microsoft Time Series Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="da76b-176">多维模型中的数据源视图</span><span class="sxs-lookup"><span data-stu-id="da76b-176">Data Source Views in Multidimensional Models</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models)  
  
  
