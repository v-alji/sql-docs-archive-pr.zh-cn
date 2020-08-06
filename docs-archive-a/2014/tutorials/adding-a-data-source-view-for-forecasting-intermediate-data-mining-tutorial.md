---
title: 添加用于预测的数据源视图 (中级数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2665040a-1291-4064-ba01-f458637dda57
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9424988efa6a9856f4ef0d558992fc90ac303861
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691410"
---
# <a name="adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial"></a><span data-ttu-id="117e3-102">为 Forecasting 添加数据源视图（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="117e3-102">Adding a Data Source View for Forecasting (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="117e3-103">在本任务中，添加将用于预测方案的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="117e3-103">In this task, you add a data source view that will be used for the forecasting scenario.</span></span> <span data-ttu-id="117e3-104">预测模型要求数据包含一个可用于标识时序中的步长的列。</span><span class="sxs-lookup"><span data-stu-id="117e3-104">A forecasting model requires that the data contains a column that can be used to identify steps in a time series.</span></span> <span data-ttu-id="117e3-105">如果计划分析多个数据序列，则所有序列的结束日期或时间步长必须相同。</span><span class="sxs-lookup"><span data-stu-id="117e3-105">If you plan to analyze multiple series of data, all series must end on the same date or time step.</span></span>  
  
### <a name="to-add-a-data-source-view"></a><span data-ttu-id="117e3-106">添加数据源视图</span><span class="sxs-lookup"><span data-stu-id="117e3-106">To add a data source view</span></span>  
  
1.  <span data-ttu-id="117e3-107">在解决方案资源管理器中，右键单击 "**数据源视图**"，然后选择 "**新建数据源视图**"。</span><span class="sxs-lookup"><span data-stu-id="117e3-107">In Solution Explorer, right-click **Data Source Views**, and then select **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="117e3-108">在“欢迎使用数据源视图向导”  页上，单击“下一步” 。</span><span class="sxs-lookup"><span data-stu-id="117e3-108">On the **Welcome to the Data Source View Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="117e3-109">在 "**选择数据源**" 页的 "**关系数据源**" 下，选择 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 数据源。</span><span class="sxs-lookup"><span data-stu-id="117e3-109">On the **Select a Data Source** page, under **Relational data sources**, select the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] data source.</span></span> <span data-ttu-id="117e3-110">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="117e3-110">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="117e3-111">如果您没有此数据源，可以在[数据挖掘基础教程](../../2014/tutorials/basic-data-mining-tutorial.md)中找到创建数据源的步骤。</span><span class="sxs-lookup"><span data-stu-id="117e3-111">If you do not have this data source, you can find the steps to create the data source in the [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md).</span></span>  
  
4.  <span data-ttu-id="117e3-112">在 "**选择表和视图**" 页上，选择表 vTimeSeries (dbo) ，然后单击右箭头将其添加到数据源视图。</span><span class="sxs-lookup"><span data-stu-id="117e3-112">On the **Select Tables and Views** page, select the table, vTimeSeries (dbo), and then click the right arrow to add it to the data source view.</span></span>  
  
5.  <span data-ttu-id="117e3-113">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="117e3-113">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="117e3-114">在 "**完成向导**" 页上，默认将数据源视图命名为 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="117e3-114">On the **Completing the Wizard** page, by default the data source view is named [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)].</span></span> <span data-ttu-id="117e3-115">将名称更改为**salesbyregion.dsv**，然后单击 "**完成**"。</span><span class="sxs-lookup"><span data-stu-id="117e3-115">Change the name to **SalesByRegion**, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="117e3-116">数据源视图设计器随即打开，并显示**salesbyregion.dsv**数据源视图。</span><span class="sxs-lookup"><span data-stu-id="117e3-116">Data Source View Designer opens and the **SalesByRegion** data source view appears.</span></span>  
  
## <a name="working-with-the-data-source-view"></a><span data-ttu-id="117e3-117">使用数据源视图</span><span class="sxs-lookup"><span data-stu-id="117e3-117">Working with the Data Source View</span></span>  
 <span data-ttu-id="117e3-118">创建数据源视图之后，可以通过以下方法浏览数据：</span><span class="sxs-lookup"><span data-stu-id="117e3-118">After you have created the data source view, you can explore the data in the following ways:</span></span>  
  
-   <span data-ttu-id="117e3-119">在设计器中右键单击表 vTimeSeries，然后选择 "**浏览数据**" 以在网格中打开所选的表。</span><span class="sxs-lookup"><span data-stu-id="117e3-119">Right-click the table vTimeSeries in the designer, and select **Explore Data** to open the selected table in a grid.</span></span>  
  
-   <span data-ttu-id="117e3-120">单击 "**抽样选项**"，然后使用 "**数据浏览选项**" 对话框更改采样方法。</span><span class="sxs-lookup"><span data-stu-id="117e3-120">Click **Sampling options** and then use the **Data Exploration Options** dialog box to change the sampling method.</span></span> <span data-ttu-id="117e3-121">单击 "**刷新**" 以使用新的选项设置加载表中的数据。</span><span class="sxs-lookup"><span data-stu-id="117e3-121">Click **Refresh** to load data in the table using the new option settings.</span></span> <span data-ttu-id="117e3-122">例如，可以在示例中指定要输出的行数，或选择前 n 行。</span><span class="sxs-lookup"><span data-stu-id="117e3-122">For example, you could specify the number of rows to output in the sample, or choose the top n rows.</span></span>  
  
-   <span data-ttu-id="117e3-123">右键单击表 vTimeSeries，然后选择 "**属性**"，为表分配新名称。</span><span class="sxs-lookup"><span data-stu-id="117e3-123">Right-click the table vTimeSeries and select **Properties** to assign a new name to the table.</span></span> <span data-ttu-id="117e3-124">您还可以从数据源视图中选择单个列，并修改列属性。</span><span class="sxs-lookup"><span data-stu-id="117e3-124">You can also select individual columns from the data source view, and the modify the column properties.</span></span>  
  
-   <span data-ttu-id="117e3-125">在数据源视图设计区域内的任意位置单击，创建一个新查询并向其分配名称，创建各表之间的关系，或者更改设计区域的布局。</span><span class="sxs-lookup"><span data-stu-id="117e3-125">Click anywhere in the data source view design area to create a new query and assign a name to it, to create relationships between tables, or to change the layout of the design area.</span></span>  
  
-   <span data-ttu-id="117e3-126">右键单击表，然后选择 "**新建命名计算**" 以创建派生列（包括聚合）。</span><span class="sxs-lookup"><span data-stu-id="117e3-126">Right-click a table and select **New Named Calculation** to create derived columns, including aggregations.</span></span> <span data-ttu-id="117e3-127">还可以在此视图中从数据源添加新的表和视图。</span><span class="sxs-lookup"><span data-stu-id="117e3-127">You can also add new tables and views from the data source in this view.</span></span>  
  
 <span data-ttu-id="117e3-128">在下一个任务中，您将浏览时序数据并确定最适合用作时序标识符的列。</span><span class="sxs-lookup"><span data-stu-id="117e3-128">In the next task, you will explore the time series data and determine the best column to use as the time series identifier.</span></span> <span data-ttu-id="117e3-129">您还将了解如何处理时序数据中的空白。</span><span class="sxs-lookup"><span data-stu-id="117e3-129">You will also learn how to handle gaps in time series data.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="117e3-130">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="117e3-130">Next Task in Lesson</span></span>  
 [<span data-ttu-id="117e3-131">了解 &#40;中级数据挖掘教程的时序模型的要求&#41;</span><span class="sxs-lookup"><span data-stu-id="117e3-131">Understanding the Requirements for a Time Series Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/time-series-model-requirements-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="117e3-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="117e3-132">See Also</span></span>  
 [<span data-ttu-id="117e3-133">Microsoft 时序算法</span><span class="sxs-lookup"><span data-stu-id="117e3-133">Microsoft Time Series Algorithm</span></span>](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
