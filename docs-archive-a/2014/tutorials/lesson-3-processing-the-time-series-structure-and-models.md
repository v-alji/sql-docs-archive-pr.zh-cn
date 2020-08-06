---
title: 第3课：处理时序结构和模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 16e27b57-eae1-47a7-a02c-47b6ed487d87
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 493d27c9836eb765c655eba5bbb004e4d48cde40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690258"
---
# <a name="lesson-3-processing-the-time-series-structure-and-models"></a><span data-ttu-id="bd941-102">第 3 课：准备时序结构和模型</span><span class="sxs-lookup"><span data-stu-id="bd941-102">Lesson 3: Processing the Time Series Structure and Models</span></span>
  <span data-ttu-id="bd941-103">在本课中，您将使用[INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)语句来处理所创建的时序挖掘结构和挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="bd941-103">In this lesson, you will use the [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) statement to process the time series mining structures and mining models that you created.</span></span>  
  
 <span data-ttu-id="bd941-104">处理挖掘结构时，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将读取源数据并生成支持挖掘模型的结构。</span><span class="sxs-lookup"><span data-stu-id="bd941-104">When you process a mining structure, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] reads the source data and builds the structures that support mining models.</span></span> <span data-ttu-id="bd941-105">您必须始终在首次创建挖掘模型和结构时对它进行处理。</span><span class="sxs-lookup"><span data-stu-id="bd941-105">You always have to process a mining model and structure when you first create it.</span></span> <span data-ttu-id="bd941-106">如果使用 INSERT INTO 指定挖掘结构，该语句将处理挖掘结构及其关联的所有挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="bd941-106">If you specify the mining structure when using INSERT INTO, the statement processes the mining structure and all its associated mining models.</span></span>  
  
 <span data-ttu-id="bd941-107">如果将挖掘模型添加到已处理过的挖掘结构中，则可以利用 `INSERT INTO MINING MODEL` 语句使用现有数据只处理新挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="bd941-107">When you add a mining model to a mining structure that has already been processed, you can use the `INSERT INTO MINING MODEL` statement to process just the new mining model by using the existing data.</span></span>  
  
 <span data-ttu-id="bd941-108">有关处理挖掘模型的详细信息，请参阅[处理 &#40;数据挖掘&#41;的要求和注意事项](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="bd941-108">For more information about processing mining models, see [Processing Requirements and Considerations &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).</span></span>  
  
## <a name="insert-into-statement"></a><span data-ttu-id="bd941-109">INSERT INTO 语句</span><span class="sxs-lookup"><span data-stu-id="bd941-109">INSERT INTO Statement</span></span>  
 <span data-ttu-id="bd941-110">为了训练时序挖掘结构及其所有关联的挖掘模型，请使用[INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)语句。</span><span class="sxs-lookup"><span data-stu-id="bd941-110">In order to train the time series mining structure and all its associated mining models, use the [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) statement.</span></span> <span data-ttu-id="bd941-111">可以将该语句中的代码分为下列几部分。</span><span class="sxs-lookup"><span data-stu-id="bd941-111">The code in the statement can be broken into the following parts.</span></span>  
  
-   <span data-ttu-id="bd941-112">标识挖掘结构</span><span class="sxs-lookup"><span data-stu-id="bd941-112">Identifying the mining structure</span></span>  
  
-   <span data-ttu-id="bd941-113">列出挖掘结构中的列</span><span class="sxs-lookup"><span data-stu-id="bd941-113">Listing the columns in the mining structure</span></span>  
  
-   <span data-ttu-id="bd941-114">定义定型数据</span><span class="sxs-lookup"><span data-stu-id="bd941-114">Defining the training data</span></span>  
  
 <span data-ttu-id="bd941-115">下面是 `INSERT INTO` 语句的一般示例：</span><span class="sxs-lookup"><span data-stu-id="bd941-115">The following is a generic example of the `INSERT INTO` statement:</span></span>  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
)  
OPENQUERY (<source data definition>)  
```  
  
 <span data-ttu-id="bd941-116">代码的第一行标识将定型的挖掘结构：</span><span class="sxs-lookup"><span data-stu-id="bd941-116">The first line of the code identifies the mining structure that you will train:</span></span>  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="bd941-117">代码的接下来各行指定该挖掘结构定义的列。</span><span class="sxs-lookup"><span data-stu-id="bd941-117">The next lines of the code specify the columns that are defined by the mining structure.</span></span> <span data-ttu-id="bd941-118">必须列出挖掘结构的每一列，并且每列必须映射到源查询数据所包含的对应列。</span><span class="sxs-lookup"><span data-stu-id="bd941-118">You must list each column in the mining structure, and each column must map to a column contained within the source query data.</span></span>  
  
```  
(  
   <mining structure columns>  
)  
```  
  
 <span data-ttu-id="bd941-119">代码的最后几行定义将用于定型挖掘结构的数据。</span><span class="sxs-lookup"><span data-stu-id="bd941-119">The final lines of the code define the data that will be used to train the mining structure.</span></span>  
  
```  
OPENQUERY (<source data definition>)  
```  
  
 <span data-ttu-id="bd941-120">在本课中，您将使用 `OPENQUERY` 来定义源数据。</span><span class="sxs-lookup"><span data-stu-id="bd941-120">In this lesson, you use `OPENQUERY` to define the source data.</span></span> <span data-ttu-id="bd941-121">有关为源数据定义查询的其他方法的详细信息，请参阅[&#60;源数据查询&#62;](/sql/dmx/source-data-query)。</span><span class="sxs-lookup"><span data-stu-id="bd941-121">For more information about other methods of defining a query on the source data, see [&#60;source data query&#62;](/sql/dmx/source-data-query).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="bd941-122">课程任务</span><span class="sxs-lookup"><span data-stu-id="bd941-122">Lesson Tasks</span></span>  
 <span data-ttu-id="bd941-123">您将在本课中执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="bd941-123">You will perform the following task in this lesson:</span></span>  
  
-   <span data-ttu-id="bd941-124">处理挖掘结构 Forecasting_MIXED_Structure</span><span class="sxs-lookup"><span data-stu-id="bd941-124">Process the mining structure Forecasting_MIXED_Structure</span></span>  
  
-   <span data-ttu-id="bd941-125">处理相关的挖掘模型 Forecasting_MIXED、Forecasting_ARIMA 和 Forecasting_ARTXP</span><span class="sxs-lookup"><span data-stu-id="bd941-125">Process the related mining models Forecasting_MIXED, Forecasting_ARIMA, and Forecasting_ARTXP</span></span>  
  
## <a name="processing-the-time-series-mining-structure"></a><span data-ttu-id="bd941-126">处理时序挖掘结构</span><span class="sxs-lookup"><span data-stu-id="bd941-126">Processing the Time Series Mining Structure</span></span>  
  
#### <a name="to-process-the-mining-structure-and-related-mining-models-by-using-insert-into"></a><span data-ttu-id="bd941-127">使用 INSERT INTO 处理挖掘结构和相关的挖掘模型</span><span class="sxs-lookup"><span data-stu-id="bd941-127">To process the mining structure and related mining models by using INSERT INTO</span></span>  
  
1.  <span data-ttu-id="bd941-128">在**对象资源管理器**中，右键单击实例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 "**新建查询**"，然后单击 " **DMX**"。</span><span class="sxs-lookup"><span data-stu-id="bd941-128">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="bd941-129">将打开查询编辑器，其中包含一个新的空白查询。</span><span class="sxs-lookup"><span data-stu-id="bd941-129">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="bd941-130">将 INSERT INTO 语句的一般示例复制到空白查询中。</span><span class="sxs-lookup"><span data-stu-id="bd941-130">Copy the generic example of the INSERT INTO statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="bd941-131">将</span><span class="sxs-lookup"><span data-stu-id="bd941-131">Replace the following:</span></span>  
  
    ```  
    [<mining structure>]  
    ```  
  
     <span data-ttu-id="bd941-132">替换为：</span><span class="sxs-lookup"><span data-stu-id="bd941-132">with:</span></span>  
  
    ```  
    Forecasting_MIXED_Structure  
    ```  
  
4.  <span data-ttu-id="bd941-133">将</span><span class="sxs-lookup"><span data-stu-id="bd941-133">Replace the following:</span></span>  
  
    ```  
    <mining structure columns>  
    ```  
  
     <span data-ttu-id="bd941-134">替换为：</span><span class="sxs-lookup"><span data-stu-id="bd941-134">with:</span></span>  
  
    ```  
    [ReportingDate],  
    [ModelRegion]   
    ```  
  
5.  <span data-ttu-id="bd941-135">将</span><span class="sxs-lookup"><span data-stu-id="bd941-135">Replace the following:</span></span>  
  
    ```  
    OPENQUERY(<source data definition>)  
    ```  
  
     <span data-ttu-id="bd941-136">替换为：</span><span class="sxs-lookup"><span data-stu-id="bd941-136">with:</span></span>  
  
    ```  
    OPENQUERY([Adventure Works DW 2008R2],'SELECT [ReportingDate], [ModelRegion], [Quantity], [Amount]  
    FROM vTimeSeries ORDER BY [ReportingDate]')  
    ```  
  
     <span data-ttu-id="bd941-137">源查询引用 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 在中级教程示例项目中定义的数据源。</span><span class="sxs-lookup"><span data-stu-id="bd941-137">The source query references the  [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] data source defined in the IntermediateTutorial sample project.</span></span> <span data-ttu-id="bd941-138">它使用此数据源来访问视图 vTimeSeries。</span><span class="sxs-lookup"><span data-stu-id="bd941-138">It uses this data source to access the view vTimeSeries.</span></span> <span data-ttu-id="bd941-139">此视图包含将用于定型挖掘模型的源数据。</span><span class="sxs-lookup"><span data-stu-id="bd941-139">This view contains the source data that will be used to train the mining model.</span></span> <span data-ttu-id="bd941-140">如果你不熟悉此项目或此视图，请参阅[第2课：生成预测方案 &#40;中级数据挖掘教程&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="bd941-140">If you are not familiar with this project or this views, see[Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).</span></span>  
  
     <span data-ttu-id="bd941-141">现在，完整的语句应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="bd941-141">The complete statement should now be as follows:</span></span>  
  
    ```  
    INSERT INTO MINING STRUCTURE [Forecasting_MIXED_Structure]  
    (  
       [ReportingDate],[ModelRegion],[Quantity],[Amount])  
    )  
    OPENQUERY(  
    [Adventure Works DW 2008R2],  
    'SELECT [ReportingDate],[ModelRegion],[Quantity],[Amount] FROM vTimeSeries ORDER BY [ReportingDate]'  
    )   
    ```  
  
6.  <span data-ttu-id="bd941-142">在 "**文件**" 菜单上，单击 "**将 DMXQuery1 另存为**"。</span><span class="sxs-lookup"><span data-stu-id="bd941-142">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="bd941-143">在 "**另存为**" 对话框中，浏览到相应的文件夹，并将该文件命名为 `ProcessForecastingAll.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="bd941-143">In the **Save As** dialog box, browse to the appropriate folder, and name the file `ProcessForecastingAll.dmx`.</span></span>  
  
8.  <span data-ttu-id="bd941-144">在工具栏上，单击 "**执行**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="bd941-144">On the toolbar, click the **Execute** button.</span></span>  
  
 <span data-ttu-id="bd941-145">在该查询完成运行之后，可以使用处理过的挖掘模型创建预测。</span><span class="sxs-lookup"><span data-stu-id="bd941-145">After the query has finished running, you can create predictions by using the processed mining models.</span></span> <span data-ttu-id="bd941-146">在下一课中，您将基于创建的挖掘模型创建多个预测。</span><span class="sxs-lookup"><span data-stu-id="bd941-146">In the next lesson, you will create several predictions based on the mining models that you created.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="bd941-147">下一课</span><span class="sxs-lookup"><span data-stu-id="bd941-147">Next Lesson</span></span>  
 [<span data-ttu-id="bd941-148">第 4 课：使用 DMX 创建时序预测</span><span class="sxs-lookup"><span data-stu-id="bd941-148">Lesson 4: Creating Time Series Predictions Using DMX</span></span>](../../2014/tutorials/lesson-4-creating-time-series-predictions-using-dmx.md)  
  
## <a name="see-also"></a><span data-ttu-id="bd941-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bd941-149">See Also</span></span>  
 <span data-ttu-id="bd941-150">[数据挖掘 &#40;处理要求和注意事项&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="bd941-150">[Processing Requirements and Considerations &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md) </span></span>  
 <span data-ttu-id="bd941-151">[&#60;源数据查询&#62;](/sql/dmx/source-data-query) </span><span class="sxs-lookup"><span data-stu-id="bd941-151">[&#60;source data query&#62;](/sql/dmx/source-data-query) </span></span>  
 [<span data-ttu-id="bd941-152">OPENQUERY &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="bd941-152">OPENQUERY &#40;DMX&#41;</span></span>](/sql/dmx/source-data-query-openquery)  
  
  
