---
title: 第1课：创建时序挖掘模型和挖掘结构 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b201f2b8-9ab5-425b-9ff3-fe321a60a7b7
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2513bc3837dd224f6561eb0015ced538ea3add8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578589"
---
# <a name="lesson-1-creating-a-time-series-mining-model-and-mining-structure"></a><span data-ttu-id="c2605-102">第 1 课：创建时序挖掘模型和挖掘结构</span><span class="sxs-lookup"><span data-stu-id="c2605-102">Lesson 1: Creating a Time Series Mining Model and Mining Structure</span></span>
  <span data-ttu-id="c2605-103">在本课中，将创建一个挖掘模型，可以使用该模型根据历史数据预测一段时间内的值。</span><span class="sxs-lookup"><span data-stu-id="c2605-103">In this lesson, you will create a mining model that allows you to predict values over time, based on historical data.</span></span> <span data-ttu-id="c2605-104">创建该模型时，基础结构会自动生成，且可以用作其他挖掘模型的基础。</span><span class="sxs-lookup"><span data-stu-id="c2605-104">When you create the model, the underlying structure will be generated automatically and can be used as the basis for additional mining models.</span></span>  
  
 <span data-ttu-id="c2605-105">本课假定您已熟悉预测模型以及 Microsoft 时序算法的要求。</span><span class="sxs-lookup"><span data-stu-id="c2605-105">This lesson assumes that you are familiar with forecasting models and with the requirements of the Microsoft Time Series algorithm.</span></span> <span data-ttu-id="c2605-106">有关详细信息，请参阅 [Microsoft Time Series Algorithm](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)。</span><span class="sxs-lookup"><span data-stu-id="c2605-106">For more information, see [Microsoft Time Series Algorithm](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md).</span></span>  
  
## <a name="create-mining-model-statement"></a><span data-ttu-id="c2605-107">CREATE 挖掘 MODEL 语句</span><span class="sxs-lookup"><span data-stu-id="c2605-107">CREATE MINING MODEL Statement</span></span>  
 <span data-ttu-id="c2605-108">为了直接创建挖掘模型并自动生成基础挖掘结构，请使用[CREATE 挖掘 model &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx)语句。</span><span class="sxs-lookup"><span data-stu-id="c2605-108">In order to create a mining model directly and automatically generate the underlying mining structure, you use the [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx) statement.</span></span> <span data-ttu-id="c2605-109">可以将语句中的代码分为下列几部分：</span><span class="sxs-lookup"><span data-stu-id="c2605-109">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="c2605-110">命名模型</span><span class="sxs-lookup"><span data-stu-id="c2605-110">Naming the model</span></span>  
  
-   <span data-ttu-id="c2605-111">定义时间戳</span><span class="sxs-lookup"><span data-stu-id="c2605-111">Defining the time stamp</span></span>  
  
-   <span data-ttu-id="c2605-112">定义可选序列键列</span><span class="sxs-lookup"><span data-stu-id="c2605-112">Defining the optional series key column</span></span>  
  
-   <span data-ttu-id="c2605-113">定义可预测属性</span><span class="sxs-lookup"><span data-stu-id="c2605-113">Defining the predictable attribute or attributes</span></span>  
  
 <span data-ttu-id="c2605-114">下面是 CREATE MINING MODEL 语句的一般示例：</span><span class="sxs-lookup"><span data-stu-id="c2605-114">The following is a generic example of the CREATE MINING MODEL statement:</span></span>  
  
```  
CREATE MINING MODEL [<Mining Structure Name>]  
(  
   <key columns>,  
   <predictable attribute columns>  
)  
USING <algorithm name>([parameter list])  
WITH DRILLTHROUGH  
```  
  
 <span data-ttu-id="c2605-115">代码的第一行定义了挖掘模型的名称：</span><span class="sxs-lookup"><span data-stu-id="c2605-115">The first line of the code defines the name of the mining model:</span></span>  
  
```  
CREATE MINING MODEL [Mining Model Name]  
```  
  
 <span data-ttu-id="c2605-116">通过在模型名称后追加“_structure”，Analysis Services 自动生成基础结构的名称，这样可以确保将结构名称与模型名称区分开。</span><span class="sxs-lookup"><span data-stu-id="c2605-116">Analysis Services automatically generates a name for the underlying structure, by appending "_structure" to the model name, which ensures that the structure name is unique from the model name.</span></span> <span data-ttu-id="c2605-117">有关在 DMX 中命名对象的信息，请参阅[标识符 &#40;DMX&#41;](/sql/dmx/identifiers-dmx)。</span><span class="sxs-lookup"><span data-stu-id="c2605-117">For information about naming an object in DMX, see [Identifiers &#40;DMX&#41;](/sql/dmx/identifiers-dmx).</span></span>  
  
 <span data-ttu-id="c2605-118">代码中的下一行定义了挖掘模型的键列，如果是时序模型，则它可唯一标识源数据中的时间步长。</span><span class="sxs-lookup"><span data-stu-id="c2605-118">The next line of the code defines the key column for the mining model, which in the case of a time series model uniquely identifies a time step in the source data.</span></span> <span data-ttu-id="c2605-119">时间步长在列名和数据类型后使用 `KEY TIME` 关键字进行标识。</span><span class="sxs-lookup"><span data-stu-id="c2605-119">The time step is identified with the `KEY TIME` keywords after the column name and data types.</span></span> <span data-ttu-id="c2605-120">如果时序模型具有单独的序列键，则使用 `KEY` 关键字对它进行标识。</span><span class="sxs-lookup"><span data-stu-id="c2605-120">If the time series model has a separate series key, it is identified by using the `KEY` keyword.</span></span>  
  
```  
<key columns>  
```  
  
 <span data-ttu-id="c2605-121">代码中的下一行用于定义将预测的模型中的列。</span><span class="sxs-lookup"><span data-stu-id="c2605-121">The next line of the code is used to define the columns in the model that will be predicted.</span></span> <span data-ttu-id="c2605-122">一个挖掘模型中可以有多个可预测属性。</span><span class="sxs-lookup"><span data-stu-id="c2605-122">You can have multiple predictable attributes in a single mining model.</span></span> <span data-ttu-id="c2605-123">如果有多个可预测属性，Microsoft 时序算法会为每个序列生成一个单独的分析：</span><span class="sxs-lookup"><span data-stu-id="c2605-123">When there are multiple predictable attributes, the Microsoft Time Series algorithm generates a separate analysis for each series:</span></span>  
  
```  
<predictable attribute columns>  
```  
  
## <a name="lesson-tasks"></a><span data-ttu-id="c2605-124">课程任务</span><span class="sxs-lookup"><span data-stu-id="c2605-124">Lesson Tasks</span></span>  
 <span data-ttu-id="c2605-125">您将在本课中执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="c2605-125">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="c2605-126">创建新的空白查询</span><span class="sxs-lookup"><span data-stu-id="c2605-126">Create a new blank query</span></span>  
  
-   <span data-ttu-id="c2605-127">更改查询以创建挖掘模型</span><span class="sxs-lookup"><span data-stu-id="c2605-127">Alter the query to create the mining model</span></span>  
  
-   <span data-ttu-id="c2605-128">执行查询</span><span class="sxs-lookup"><span data-stu-id="c2605-128">Execute the query</span></span>  
  
## <a name="creating-the-query"></a><span data-ttu-id="c2605-129">创建查询</span><span class="sxs-lookup"><span data-stu-id="c2605-129">Creating the Query</span></span>  
 <span data-ttu-id="c2605-130">第一步是连接到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例，并在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中创建一个新的 DMX 查询。</span><span class="sxs-lookup"><span data-stu-id="c2605-130">The first step is to connect to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and create a new DMX query in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a><span data-ttu-id="c2605-131">在 SQL Server Management Studio 中创建一个新的 DMX 查询</span><span class="sxs-lookup"><span data-stu-id="c2605-131">To create a new DMX query in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="c2605-132">打开 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c2605-132">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="c2605-133">在 "**连接到服务器**" 对话框中，选择 "**服务器类型**" **Analysis Services**。</span><span class="sxs-lookup"><span data-stu-id="c2605-133">In the **Connect to Server** dialog box, for **Server type**, select **Analysis Services**.</span></span> <span data-ttu-id="c2605-134">在 "**服务器名称**" 中，键入 `LocalHost` 或 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 要为本课连接到的实例的名称。</span><span class="sxs-lookup"><span data-stu-id="c2605-134">In **Server name**, type `LocalHost`, or the name of the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you want to connect to for this lesson.</span></span> <span data-ttu-id="c2605-135">单击“连接” 。</span><span class="sxs-lookup"><span data-stu-id="c2605-135">Click **Connect**.</span></span>  
  
3.  <span data-ttu-id="c2605-136">在**对象资源管理器**中，右键单击实例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 "**新建查询**"，然后单击 " **DMX**"。</span><span class="sxs-lookup"><span data-stu-id="c2605-136">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="c2605-137">将打开查询编辑器，其中包含一个新的空白查询。</span><span class="sxs-lookup"><span data-stu-id="c2605-137">Query Editor opens and contains a new, blank query.</span></span>  
  
## <a name="altering-the-query"></a><span data-ttu-id="c2605-138">更改查询</span><span class="sxs-lookup"><span data-stu-id="c2605-138">Altering the Query</span></span>  
 <span data-ttu-id="c2605-139">下一步是修改 CREATE MINING MODEL 语句，以创建用于预测的挖掘模型及其基础挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="c2605-139">The next step is to modify the CREATE MINING MODEL statement to create the mining model used for forecasting, together with its underlying mining structure.</span></span>  
  
#### <a name="to-customize-the-create-mining-model-statement"></a><span data-ttu-id="c2605-140">自定义 CREATE MINING MODEL 语句</span><span class="sxs-lookup"><span data-stu-id="c2605-140">To customize the CREATE MINING MODEL statement</span></span>  
  
1.  <span data-ttu-id="c2605-141">在查询编辑器中，将 CREATE MINING MODEL 语句的一般示例复制到空白查询中。</span><span class="sxs-lookup"><span data-stu-id="c2605-141">In Query Editor, copy the generic example of the CREATE MINING MODEL statement into the blank query.</span></span>  
  
2.  <span data-ttu-id="c2605-142">将</span><span class="sxs-lookup"><span data-stu-id="c2605-142">Replace the following:</span></span>  
  
    ```  
    [mining model name]   
    ```  
  
     <span data-ttu-id="c2605-143">替换为：</span><span class="sxs-lookup"><span data-stu-id="c2605-143">with:</span></span>  
  
    ```  
    [Forecasting_MIXED]  
    ```  
  
3.  <span data-ttu-id="c2605-144">将</span><span class="sxs-lookup"><span data-stu-id="c2605-144">Replace the following:</span></span>  
  
    ```  
    <key columns>  
    ```  
  
     <span data-ttu-id="c2605-145">替换为：</span><span class="sxs-lookup"><span data-stu-id="c2605-145">with:</span></span>  
  
    ```  
    [Reporting Date] DATE KEY TIME,  
    [Model Region] TEXT KEY  
    ```  
  
     <span data-ttu-id="c2605-146">`TIME KEY` 关键字指示 ReportingDate 列包含用于对值进行排序的时间步长值。</span><span class="sxs-lookup"><span data-stu-id="c2605-146">The `TIME KEY` keyword indicates that the ReportingDate column contains the time step values used to order the values.</span></span> <span data-ttu-id="c2605-147">时间步长可以为日期和时间、整数或任何有序数据类型，只要值唯一且数据有序即可。</span><span class="sxs-lookup"><span data-stu-id="c2605-147">Time steps can be dates and times, integers, or any ordered data type, so long as the values are unique and the data is sorted.</span></span>  
  
     <span data-ttu-id="c2605-148">`TEXT` 和 `KEY` 关键字指示 ModelRegion 列包含额外的序列键。</span><span class="sxs-lookup"><span data-stu-id="c2605-148">The `TEXT` and `KEY` keywords indicate that the ModelRegion column contains an additional series key.</span></span> <span data-ttu-id="c2605-149">只能有一个序列键，并且该列中的值必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="c2605-149">You can have only one series key, and the values in the column must be distinct.</span></span>  
  
4.  <span data-ttu-id="c2605-150">将</span><span class="sxs-lookup"><span data-stu-id="c2605-150">Replace the following:</span></span>  
  
    ```  
    < predictable attribute columns> )  
    ```  
  
     <span data-ttu-id="c2605-151">替换为：</span><span class="sxs-lookup"><span data-stu-id="c2605-151">with:</span></span>  
  
    ```  
    [Quantity] LONG CONTINUOUS PREDICT,  
    [Amount] DOUBLE CONTINUOUS PREDICT  
    )  
    ```  
  
5.  <span data-ttu-id="c2605-152">将</span><span class="sxs-lookup"><span data-stu-id="c2605-152">Replace the following:</span></span>  
  
    ```  
    USING <algorithm name>([parameter list])  
    WITH DRILLTHROUGH  
    ```  
  
     <span data-ttu-id="c2605-153">替换为：</span><span class="sxs-lookup"><span data-stu-id="c2605-153">with:</span></span>  
  
    ```  
    USING Microsoft_Time_Series(AUTO_DETECT_PERIODICITY = 0.8, FORECAST_METHOD = 'MIXED')  
    WITH DRILLTHROUGH  
    ```  
  
     <span data-ttu-id="c2605-154">算法参数 `AUTO_DETECT_PERIODICITY` = 0.8 指示您希望使用该算法来检测数据中的周期。</span><span class="sxs-lookup"><span data-stu-id="c2605-154">The algorithm parameter, `AUTO_DETECT_PERIODICITY` = 0.8, indicates that you want the algorithm to detect cycles in the data.</span></span> <span data-ttu-id="c2605-155">如果将此值设置为接近于 1 的数，往往会发现许多模式，不过会降低处理速度。</span><span class="sxs-lookup"><span data-stu-id="c2605-155">Setting this value closer to 1 favors the discovery of many patterns but can slow processing.</span></span>  
  
     <span data-ttu-id="c2605-156">算法参数 `FORECAST_METHOD` 指示您是否希望使用 ARTXP、ARIMA 或两者的组合来对数据进行分析。</span><span class="sxs-lookup"><span data-stu-id="c2605-156">The algorithm parameter, `FORECAST_METHOD`, indicates whether you want the data to be analyzed using ARTXP, ARIMA, or a mixture of both.</span></span>  
  
     <span data-ttu-id="c2605-157">关键字 `WITH DRILLTHROUGH` 指示您希望能够在模型完成后查看源数据中的详细统计信息。</span><span class="sxs-lookup"><span data-stu-id="c2605-157">The keyword, `WITH DRILLTHROUGH`, specify that you want to be able to view detailed statistics in the source data after the model is complete.</span></span> <span data-ttu-id="c2605-158">如果希望使用 Microsoft 时序查看器浏览模型，则必须添加此子句。</span><span class="sxs-lookup"><span data-stu-id="c2605-158">You must add this clause if you want to browse the model by using the Microsoft Time Series Viewer.</span></span> <span data-ttu-id="c2605-159">它不是预测所必需的。</span><span class="sxs-lookup"><span data-stu-id="c2605-159">It is not required for prediction.</span></span>  
  
     <span data-ttu-id="c2605-160">现在，完整的语句应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="c2605-160">The complete statement should now be as follows:</span></span>  
  
    ```  
    CREATE MINING MODEL [Forecasting_MIXED]  
         (  
        [Reporting Date] DATE KEY TIME,  
        [Model Region] TEXT KEY,  
        [Quantity] LONG CONTINUOUS PREDICT,  
        [Amount] DOUBLE CONTINUOUS PREDICT  
        )  
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = 0.8, FORECAST_METHOD = 'MIXED')  
    WITH DRILLTHROUGH  
  
    ```  
  
6.  <span data-ttu-id="c2605-161">在 "**文件**" 菜单上，单击 "**将 DMXQuery1 另存为**"。</span><span class="sxs-lookup"><span data-stu-id="c2605-161">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="c2605-162">在 "**另存为**" 对话框中，浏览到相应的文件夹，并将该文件命名为 `Forecasting_MIXED.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="c2605-162">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Forecasting_MIXED.dmx`.</span></span>  
  
## <a name="executing-the-query"></a><span data-ttu-id="c2605-163">执行查询</span><span class="sxs-lookup"><span data-stu-id="c2605-163">Executing the Query</span></span>  
 <span data-ttu-id="c2605-164">最后一步是执行查询。</span><span class="sxs-lookup"><span data-stu-id="c2605-164">The final step is to execute the query.</span></span> <span data-ttu-id="c2605-165">创建并保存查询后，需要执行查询，以在服务器上创建挖掘模型及其挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="c2605-165">After a query is created and saved, it needs to be executed to create the mining model and its mining structure on the server.</span></span> <span data-ttu-id="c2605-166">有关在查询编辑器中执行查询的详细信息，请参阅[SQL Server Management Studio&#41;数据库引擎查询编辑器 &#40;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="c2605-166">For more information about executing queries in Query Editor, see [Database Engine Query Editor &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="c2605-167">执行查询</span><span class="sxs-lookup"><span data-stu-id="c2605-167">To execute the query</span></span>  
  
-   <span data-ttu-id="c2605-168">在查询编辑器中，单击工具栏上的 "**执行**"。</span><span class="sxs-lookup"><span data-stu-id="c2605-168">In Query Editor, on the toolbar, click **Execute**.</span></span>  
  
     <span data-ttu-id="c2605-169">语句执行完毕后，查询的状态将显示在查询编辑器底部的 "**消息**" 选项卡中。</span><span class="sxs-lookup"><span data-stu-id="c2605-169">The status of the query is displayed in the **Messages** tab at the bottom of Query Editor after the statement finishes executing.</span></span> <span data-ttu-id="c2605-170">所显示的消息应为：</span><span class="sxs-lookup"><span data-stu-id="c2605-170">Messages should display:</span></span>  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     <span data-ttu-id="c2605-171">服务器上现在存在一个名为**Forecasting_MIXED_Structure**的新结构，以及相关的挖掘模型**Forecasting_MIXED**。</span><span class="sxs-lookup"><span data-stu-id="c2605-171">A new structure named **Forecasting_MIXED_Structure** now exists on the server, together with the related mining model **Forecasting_MIXED**.</span></span>  
  
 <span data-ttu-id="c2605-172">在下一课中，您将向刚创建的**Forecasting_MIXED**挖掘结构中添加挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="c2605-172">In the next lesson, you will add a mining model to the **Forecasting_MIXED** mining structure that you just created.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="c2605-173">下一课</span><span class="sxs-lookup"><span data-stu-id="c2605-173">Next Lesson</span></span>  
 [<span data-ttu-id="c2605-174">第 2 课：向时序挖掘结构添加挖掘模型</span><span class="sxs-lookup"><span data-stu-id="c2605-174">Lesson 2: Adding Mining Models to the Time Series Mining Structure</span></span>](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md)  
  
## <a name="see-also"></a><span data-ttu-id="c2605-175">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c2605-175">See Also</span></span>  
 <span data-ttu-id="c2605-176">[时序模型的挖掘模型内容 &#40;Analysis Services 数据挖掘&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="c2605-176">[Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="c2605-177">Microsoft Time Series Algorithm Technical Reference</span><span class="sxs-lookup"><span data-stu-id="c2605-177">Microsoft Time Series Algorithm Technical Reference</span></span>](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)  
  
  
