---
title: 第2课：向时序挖掘结构中添加挖掘模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 75c2a74b-21ce-44fb-a26b-68be4c685c12
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ae0bb91fafb53c0c077a4e0d82558b550d0e6070
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577170"
---
# <a name="lesson-2-adding-mining-models-to-the-time-series-mining-structure"></a><span data-ttu-id="884ce-102">第 2 课：向时序挖掘结构添加挖掘模型</span><span class="sxs-lookup"><span data-stu-id="884ce-102">Lesson 2: Adding Mining Models to the Time Series Mining Structure</span></span>
  <span data-ttu-id="884ce-103">在本课程中，您将向您在[第1课：创建时序挖掘模型和挖掘结构](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md)中刚创建的挖掘结构中添加一个新的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="884ce-103">In this lesson, you will add a new mining model to the mining structure that you just created in [Lesson 1: Creating a Time Series Mining Model and Mining Structure](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md).</span></span>  
  
## <a name="alter-mining-structure-statement"></a><span data-ttu-id="884ce-104">ALTER MINING STRUCTURE 语句</span><span class="sxs-lookup"><span data-stu-id="884ce-104">ALTER MINING STRUCTURE Statement</span></span>  
 <span data-ttu-id="884ce-105">若要向现有挖掘结构中添加新的挖掘模型，请使用[&#40;DMX&#41;语句的 ALTER 挖掘 structure](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016) 。</span><span class="sxs-lookup"><span data-stu-id="884ce-105">In order to add a new mining model to an existing mining structure, you use the [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016) statement.</span></span> <span data-ttu-id="884ce-106">可以将语句中的代码分为下列几部分：</span><span class="sxs-lookup"><span data-stu-id="884ce-106">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="884ce-107">标识挖掘结构</span><span class="sxs-lookup"><span data-stu-id="884ce-107">Identifying the mining structure</span></span>  
  
-   <span data-ttu-id="884ce-108">命名挖掘模型</span><span class="sxs-lookup"><span data-stu-id="884ce-108">Naming the mining model</span></span>  
  
-   <span data-ttu-id="884ce-109">定义键列</span><span class="sxs-lookup"><span data-stu-id="884ce-109">Defining the key column</span></span>  
  
-   <span data-ttu-id="884ce-110">定义可预测列</span><span class="sxs-lookup"><span data-stu-id="884ce-110">Defining the predictable columns</span></span>  
  
-   <span data-ttu-id="884ce-111">指定算法和任何参数更改</span><span class="sxs-lookup"><span data-stu-id="884ce-111">Specifying the algorithm and any parameter changes</span></span>  
  
 <span data-ttu-id="884ce-112">下面是 ALTER MINING STRUCTURE 语句的一般示例：</span><span class="sxs-lookup"><span data-stu-id="884ce-112">The following is a generic example of the ALTER MINING STRUCTURE statement:</span></span>  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
ADD MINING MODEL [<mining model name>]  
   ([<key columns>],  
    <mining model columns>  
   )  
USING <algorithm name>([<algorithm parameters>])  
[WITH DRILLTHROUGH]  
```  
  
 <span data-ttu-id="884ce-113">代码的第一行标识将向其添加挖掘模型的现有挖掘结构：</span><span class="sxs-lookup"><span data-stu-id="884ce-113">The first line of the code identifies the existing mining structure to which the mining models will be added:</span></span>  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="884ce-114">代码的第二行对将要添加到挖掘结构中的挖掘模型进行命名：</span><span class="sxs-lookup"><span data-stu-id="884ce-114">The next line of the code names the mining model that will be added to the mining structure:</span></span>  
  
```  
ADD MINING MODEL [<mining model name>]  
```  
  
 <span data-ttu-id="884ce-115">有关在 DMX 中命名对象的信息，请参阅[标识符 &#40;DMX&#41;](/sql/dmx/identifiers-dmx)。</span><span class="sxs-lookup"><span data-stu-id="884ce-115">For information about naming an object in DMX, see [Identifiers &#40;DMX&#41;](/sql/dmx/identifiers-dmx).</span></span>  
  
 <span data-ttu-id="884ce-116">代码的接下来的各行定义挖掘结构中将由挖掘模型使用的各列：</span><span class="sxs-lookup"><span data-stu-id="884ce-116">The next lines of the code define columns from the mining structure that will be used by the mining model:</span></span>  
  
```  
[<key columns>],  
<mining model columns>  
```  
  
 <span data-ttu-id="884ce-117">您只能使用挖掘结构中现有的各列，列表中的第一列必须是挖掘结构中的键列。</span><span class="sxs-lookup"><span data-stu-id="884ce-117">You can only use columns that already exist in the mining structure, and the first column in the list must be the key column from the mining structure.</span></span>  
  
 <span data-ttu-id="884ce-118">代码的下一行定义生成挖掘模型的挖掘算法以及可以针对算法设置的算法参数，并指定是否能够从挖掘模型深化到定型事例中的详细数据视图：</span><span class="sxs-lookup"><span data-stu-id="884ce-118">The next lines of the code defines the mining algorithm that generates the mining model and the algorithm parameters that you can set on the algorithm, and specify whether you can drill down from the mining model into view detailed data in the training cases:</span></span>  
  
```  
USING <algorithm name>([<algorithm parameters>])  
WITH DRILLTHROUGH  
```  
  
 <span data-ttu-id="884ce-119">有关可以调整的算法参数的详细信息，请参阅[Microsoft 时序算法技术参考](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="884ce-119">For more information about the algorithm parameters that you can adjust, see [Microsoft Time Series Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="884ce-120">您可以使用以下语法指定将挖掘模型中的一列用于预测：</span><span class="sxs-lookup"><span data-stu-id="884ce-120">You can specify that a column in the mining model be used for prediction by using the following syntax:</span></span>  
  
```  
<mining model column> PREDICT  
```  
  
## <a name="lesson-tasks"></a><span data-ttu-id="884ce-121">课程任务</span><span class="sxs-lookup"><span data-stu-id="884ce-121">Lesson Tasks</span></span>  
 <span data-ttu-id="884ce-122">您将在本课中执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="884ce-122">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="884ce-123">在结构中添加新的时序挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="884ce-123">Add a new time series mining model to the structure.</span></span>  
  
-   <span data-ttu-id="884ce-124">更改算法参数以使用另一种分析和预测方法。</span><span class="sxs-lookup"><span data-stu-id="884ce-124">Change the algorithm parameters to use a different method of analysis and prediction</span></span>  
  
## <a name="adding-an-arima-time-series-model-to-the-structure"></a><span data-ttu-id="884ce-125">在结构中添加 ARIMA 时序模型</span><span class="sxs-lookup"><span data-stu-id="884ce-125">Adding an ARIMA Time Series Model to the Structure</span></span>  
 <span data-ttu-id="884ce-126">第一步是在现有结构中添加新的预测挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="884ce-126">The first step is to add a new forecasting mining model to the existing structure.</span></span> <span data-ttu-id="884ce-127">默认情况下，[!INCLUDE[msCoName](../includes/msconame-md.md)] 时序算法通过使用 ARIMA 和 ARTXP 两种算法并混合所得到的结果来创建时序挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="884ce-127">By default, the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm creates time series mining models by using two algorithms, ARIMA and ARTXP, and blending the results.</span></span> <span data-ttu-id="884ce-128">但是，您可以指定要使用某个算法，也可以指定确切的算法组合。</span><span class="sxs-lookup"><span data-stu-id="884ce-128">However, you can specify a single algorithm to use, or you can specify the exact blend of algorithms.</span></span> <span data-ttu-id="884ce-129">在该步骤中，您将添加一个仅使用 ARIMA 算法的新模型。</span><span class="sxs-lookup"><span data-stu-id="884ce-129">In this step, you will add a new model that uses only the ARIMA algorithm.</span></span> <span data-ttu-id="884ce-130">该算法针对长期预测进行了优化。</span><span class="sxs-lookup"><span data-stu-id="884ce-130">This algorithm is optimized for long-term prediction.</span></span>  
  
#### <a name="to-add-an-arima-time-series-mining-model"></a><span data-ttu-id="884ce-131">添加 ARIMA 时序挖掘模型</span><span class="sxs-lookup"><span data-stu-id="884ce-131">To add an ARIMA time series mining model</span></span>  
  
1.  <span data-ttu-id="884ce-132">在**对象资源管理器**中，右键单击实例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 "**新建查询**"，然后单击 " **DMX** "，打开查询编辑器和一个新的空白查询。</span><span class="sxs-lookup"><span data-stu-id="884ce-132">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX** to open Query Editor and a new, blank query.</span></span>  
  
2.  <span data-ttu-id="884ce-133">将 ALTER MINING STRUCTURE 语句的一般示例复制到空白查询中。</span><span class="sxs-lookup"><span data-stu-id="884ce-133">Copy the generic example of the ALTER MINING STRUCTURE statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="884ce-134">将</span><span class="sxs-lookup"><span data-stu-id="884ce-134">Replace the following:</span></span>  
  
    ```  
    <mining structure name>   
    ```  
  
     <span data-ttu-id="884ce-135">替换为：</span><span class="sxs-lookup"><span data-stu-id="884ce-135">with:</span></span>  
  
    ```  
    [Forecasting_MIXED_Structure]  
    ```  
  
4.  <span data-ttu-id="884ce-136">将</span><span class="sxs-lookup"><span data-stu-id="884ce-136">Replace the following:</span></span>  
  
    ```  
    <mining model name>   
    ```  
  
     <span data-ttu-id="884ce-137">替换为：</span><span class="sxs-lookup"><span data-stu-id="884ce-137">with:</span></span>  
  
    ```  
    Forecasting_ARIMA  
    ```  
  
5.  <span data-ttu-id="884ce-138">将</span><span class="sxs-lookup"><span data-stu-id="884ce-138">Replace the following:</span></span>  
  
    ```  
    <key columns>,  
    ```  
  
     <span data-ttu-id="884ce-139">替换为：</span><span class="sxs-lookup"><span data-stu-id="884ce-139">with:</span></span>  
  
    ```  
    [ReportingDate],  
    [ModelRegion]  
    ```  
  
     <span data-ttu-id="884ce-140">请注意，您不必重复在 CREATE MINING MODEL 语句中提供的有关数据类型或内容类型的任何信息，因为这些信息已经存储在挖掘结构中。</span><span class="sxs-lookup"><span data-stu-id="884ce-140">Note that you do not need to repeat any of the date type or content type information that you provided in the CREATE MINING MODEL statement, because this information is already stored in the mining structure.</span></span>  
  
6.  <span data-ttu-id="884ce-141">将</span><span class="sxs-lookup"><span data-stu-id="884ce-141">Replace the following:</span></span>  
  
    ```  
    <mining model columns>  
    ```  
  
     <span data-ttu-id="884ce-142">替换为：</span><span class="sxs-lookup"><span data-stu-id="884ce-142">with:</span></span>  
  
    ```  
    ([Quantity] PREDICT,  
    [Amount] PREDICT  
    )  
    ```  
  
7.  <span data-ttu-id="884ce-143">将</span><span class="sxs-lookup"><span data-stu-id="884ce-143">Replace the following:</span></span>  
  
    ```  
    USING <algorithm name>([<algorithm parameters>])   
    [WITH DRILLTHROUGH]  
    ```  
  
     <span data-ttu-id="884ce-144">替换为：</span><span class="sxs-lookup"><span data-stu-id="884ce-144">with:</span></span>  
  
    ```  
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = .08, FORECAST_METHOD = 'ARIMA')  
    WITH DRILLTHROUGH  
    ```  
  
     <span data-ttu-id="884ce-145">现在，结果语句应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="884ce-145">The resulting statement should now be as follows:</span></span>  
  
    ```  
    ALTER MINING STRUCTURE [Forecasting_MIXED_Structure]  
    ADD MINING MODEL [Forecasting_ARIMA]  
       (  
       ([ReportingDate],  
        [ModelRegion],  
        ([Quantity] PREDICT,  
        [Amount] PREDICT  
       )   
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = .08, FORECAST_METHOD = 'ARIMA')  
    WITH DRILLTHROUGH  
    ```  
  
8.  <span data-ttu-id="884ce-146">在 "**文件**" 菜单上，单击 "**将 DMXQuery1 另存为**"。</span><span class="sxs-lookup"><span data-stu-id="884ce-146">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
9. <span data-ttu-id="884ce-147">在 "**另存为**" 对话框中，浏览到相应的文件夹，并将该文件命名为 `Forecasting_ARIMA.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="884ce-147">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Forecasting_ARIMA.dmx`.</span></span>  
  
10. <span data-ttu-id="884ce-148">在工具栏上，单击 "**执行**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="884ce-148">On the toolbar, click the **Execute** button.</span></span>  
  
## <a name="adding-an-artxp-time-series-model-to-the-structure"></a><span data-ttu-id="884ce-149">在结构中添加 ARTXP 时序模型</span><span class="sxs-lookup"><span data-stu-id="884ce-149">Adding an ARTXP Time Series Model to the Structure</span></span>  
 <span data-ttu-id="884ce-150">ARTXP 算法是 SQL Server 2005 中的默认时序算法，针对短期预测进行了优化。</span><span class="sxs-lookup"><span data-stu-id="884ce-150">The ARTXP algorithm was the default time series algorithm in SQL Server 2005 and is optimized for short-term prediction.</span></span> <span data-ttu-id="884ce-151">若要使用所有这三个时序算法来比较预测结果，还需要再添加一个基于 ARTXP 算法的模型。</span><span class="sxs-lookup"><span data-stu-id="884ce-151">To compare predictions by using all three time series algorithms, you will add one more model that is based on the ARTXP algorithm.</span></span>  
  
#### <a name="to-add-an-artxp-time-series-mining-model"></a><span data-ttu-id="884ce-152">添加 ARTXP 时序挖掘模型</span><span class="sxs-lookup"><span data-stu-id="884ce-152">To add an ARTXP time series mining model</span></span>  
  
1.  <span data-ttu-id="884ce-153">将以下代码复制到空白的查询窗口中。</span><span class="sxs-lookup"><span data-stu-id="884ce-153">Copy the following code into a blank query window.</span></span>  
  
     <span data-ttu-id="884ce-154">请注意，除了新挖掘模型的名称以及 FORECAST_METHOD 参数的值，您不必更改任何其他内容。</span><span class="sxs-lookup"><span data-stu-id="884ce-154">Note that you do not need to change anything except the name of the new mining model, and the value of the FORECAST_METHOD parameter.</span></span>  
  
    ```  
    ALTER MINING STRUCTURE [Forecasting_MIXED_Structure]  
    ADD MINING MODEL [Forecasting_ARTXP]  
       (  
       ([ReportingDate],  
        [ModelRegion],  
        ([Quantity] PREDICT,  
        [Amount] PREDICT  
       )   
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = .08, FORECAST_METHOD = 'ARTXP')  
    WITH DRILLTHROUGH  
    ```  
  
2.  <span data-ttu-id="884ce-155">在 "**文件**" 菜单上，单击 "**将 DMXQuery1 另存为**"。</span><span class="sxs-lookup"><span data-stu-id="884ce-155">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
3.  <span data-ttu-id="884ce-156">在 "**另存为**" 对话框中，浏览到相应的文件夹，并将该文件命名为 `Forecasting_ARTXP.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="884ce-156">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Forecasting_ARTXP.dmx`.</span></span>  
  
4.  <span data-ttu-id="884ce-157">在工具栏上，单击 "**执行**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="884ce-157">On the toolbar, click the **Execute** button.</span></span>  
  
 <span data-ttu-id="884ce-158">在下一课中，您将处理所有模型和挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="884ce-158">In the next lesson, you will process all of the models and the mining structure.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="884ce-159">下一课</span><span class="sxs-lookup"><span data-stu-id="884ce-159">Next Lesson</span></span>  
 [<span data-ttu-id="884ce-160">第 3 课：准备时序结构和模型</span><span class="sxs-lookup"><span data-stu-id="884ce-160">Lesson 3: Processing the Time Series Structure and Models</span></span>](../../2014/tutorials/lesson-3-processing-the-time-series-structure-and-models.md)  
  
## <a name="see-also"></a><span data-ttu-id="884ce-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="884ce-161">See Also</span></span>  
 <span data-ttu-id="884ce-162">[Microsoft 时序算法](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="884ce-162">[Microsoft Time Series Algorithm](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md) </span></span>  
 [<span data-ttu-id="884ce-163">Microsoft Time Series Algorithm Technical Reference</span><span class="sxs-lookup"><span data-stu-id="884ce-163">Microsoft Time Series Algorithm Technical Reference</span></span>](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)  
  
  
