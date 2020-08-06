---
title: 第3课：处理市场篮挖掘结构 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 095a043f-cf6f-45bb-a021-ae4e1b535c65
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ce2c2e6944d524a38edc331d2cd128ca7cf7d419
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682469"
---
# <a name="lesson-3-processing-the-market-basket-mining-structure"></a><span data-ttu-id="ec22c-102">第 3 课：处理市场篮挖掘结构</span><span class="sxs-lookup"><span data-stu-id="ec22c-102">Lesson 3: Processing the Market Basket Mining Structure</span></span>
  <span data-ttu-id="ec22c-103">在本课中，您将使用[INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)语句以及示例数据库中的 VAssocSeqLineItems 和 vAssocSeqOrders [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 来处理您在第1课中创建的挖掘结构和挖掘模型[：创建市场篮挖掘结构](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md)和[第2课：向市场篮挖掘结构中添加挖掘模型](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="ec22c-103">In this lesson, you will use the [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) statement and the vAssocSeqLineItems and vAssocSeqOrders from the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sample database to process the mining structures and mining models that you created in [Lesson 1: Creating the Market Basket Mining Structure](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md) and [Lesson 2: Adding Mining Models to the Market Basket Mining Structure](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md).</span></span>  
  
 <span data-ttu-id="ec22c-104">处理挖掘结构时，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将读取源数据并生成支持挖掘模型的结构。</span><span class="sxs-lookup"><span data-stu-id="ec22c-104">When you process a mining structure, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] reads the source data and builds the structures that support mining models.</span></span> <span data-ttu-id="ec22c-105">处理挖掘模型时，由挖掘结构定义的数据通过您选择的数据挖掘算法进行传递。</span><span class="sxs-lookup"><span data-stu-id="ec22c-105">When you process a mining model, the data defined by the mining structure is passed through the data mining algorithm that you chose.</span></span> <span data-ttu-id="ec22c-106">该算法将搜索趋势和模式，然后在挖掘模型中存储此信息。</span><span class="sxs-lookup"><span data-stu-id="ec22c-106">The algorithm searches for trends and patterns, and then stores this information in the mining model.</span></span> <span data-ttu-id="ec22c-107">因此，挖掘模型不包含实际源数据，而是包含由算法发现的信息。</span><span class="sxs-lookup"><span data-stu-id="ec22c-107">The mining model, therefore, does not contain the actual source data, but instead contains the information that was discovered by the algorithm.</span></span> <span data-ttu-id="ec22c-108">有关处理挖掘模型的详细信息，请参阅[处理 &#40;数据挖掘&#41;的要求和注意事项](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="ec22c-108">For more information about processing mining models, see [Processing Requirements and Considerations &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).</span></span>  
  
 <span data-ttu-id="ec22c-109">如果更改了结构列或源数据，则只需要重新处理挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="ec22c-109">You only have to reprocess a mining structure if you change a structure column or change the source data.</span></span> <span data-ttu-id="ec22c-110">如果将挖掘模型添加到已处理的挖掘结构中，则可以使用 `INSERT INTO MINING MODEL` 语句针对现有数据为新的挖掘模型定型。</span><span class="sxs-lookup"><span data-stu-id="ec22c-110">If you add a mining model to a mining structure that has already been processed, you can use the `INSERT INTO MINING MODEL` statement to train the new mining model on the existing data.</span></span>  
  
 <span data-ttu-id="ec22c-111">由于市场篮挖掘结构包含嵌套表，因此，需要使用嵌套表结构定义要定型的挖掘列，并使用 `SHAPE` 命令定义从源表请求定型数据的查询。</span><span class="sxs-lookup"><span data-stu-id="ec22c-111">Because the Market Basket mining structure contains a nested table, you will have to define the mining columns to be trained using the nested table structure, and use the `SHAPE` command to define the queries that pull the training data from the source tables.</span></span>  
  
## <a name="insert-into-statement"></a><span data-ttu-id="ec22c-112">INSERT INTO 语句</span><span class="sxs-lookup"><span data-stu-id="ec22c-112">INSERT INTO Statement</span></span>  
 <span data-ttu-id="ec22c-113">为了训练市场篮挖掘结构及其关联的挖掘模型，请使用[INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)语句。</span><span class="sxs-lookup"><span data-stu-id="ec22c-113">In order to train the Market Basket mining structure and its associated mining models, use the [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) statement.</span></span> <span data-ttu-id="ec22c-114">可以将该语句中的代码分为下列几部分。</span><span class="sxs-lookup"><span data-stu-id="ec22c-114">The code in the statement can be broken into the following parts.</span></span>  
  
-   <span data-ttu-id="ec22c-115">标识挖掘结构</span><span class="sxs-lookup"><span data-stu-id="ec22c-115">Identifying the mining structure</span></span>  
  
-   <span data-ttu-id="ec22c-116">列出挖掘结构中的列</span><span class="sxs-lookup"><span data-stu-id="ec22c-116">Listing the columns in the mining structure</span></span>  
  
-   <span data-ttu-id="ec22c-117">使用 `SHAPE` 定义定型数据</span><span class="sxs-lookup"><span data-stu-id="ec22c-117">Defining the training data using `SHAPE`</span></span>  
  
 <span data-ttu-id="ec22c-118">下面是 `INSERT INTO` 语句的一般示例：</span><span class="sxs-lookup"><span data-stu-id="ec22c-118">The following is a generic example of the `INSERT INTO` statement:</span></span>  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
   [<nested table>]  
   ( SKIP, <skipped column> )  
)  
SHAPE {  
  OPENQUERY([<datasource>],'<SELECT statement>') }  
APPEND  
(   
  {OPENQUERY([<datasource>],'<nested SELECT statement>')  
}  
RELATE [<case key>] TO [<foreign key>]  
) AS [<nested table>]  
```  
  
 <span data-ttu-id="ec22c-119">代码的第一行标识将定型的挖掘结构：</span><span class="sxs-lookup"><span data-stu-id="ec22c-119">The first line of the code identifies the mining structure that you will train:</span></span>  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="ec22c-120">代码的接下来各行指定该挖掘结构定义的列。</span><span class="sxs-lookup"><span data-stu-id="ec22c-120">The next lines of the code specify the columns that are defined by the mining structure.</span></span> <span data-ttu-id="ec22c-121">必须列出挖掘结构的每一列，并且每列必须映射到源查询数据所包含的对应列。</span><span class="sxs-lookup"><span data-stu-id="ec22c-121">You must list each column in the mining structure, and each column must map to a column contained within the source query data.</span></span> <span data-ttu-id="ec22c-122">可以使用 `SKIP` 来忽略源数据中存在但挖掘结构中不存在的列。</span><span class="sxs-lookup"><span data-stu-id="ec22c-122">You can use `SKIP` to ignore columns that exist in the source data but do not exist in the mining structure.</span></span> <span data-ttu-id="ec22c-123">有关如何使用的详细信息 `SKIP` ，请参阅[INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)。</span><span class="sxs-lookup"><span data-stu-id="ec22c-123">For more information about how to use `SKIP`, see [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx).</span></span>  
  
```  
(  
   <mining structure columns>  
   [<nested table>]  
   ( SKIP, <skipped column> )  
)  
```  
  
 <span data-ttu-id="ec22c-124">代码的最后几行定义将用于定型挖掘结构的数据。</span><span class="sxs-lookup"><span data-stu-id="ec22c-124">The final lines of the code define the data that will be used to train the mining structure.</span></span> <span data-ttu-id="ec22c-125">由于源数据包含在两个表中，因此，将使用 `SHAPE` 来关联这两个表。</span><span class="sxs-lookup"><span data-stu-id="ec22c-125">Because the source data is contained within two tables, you will use `SHAPE` to relate the tables.</span></span>  
  
```  
SHAPE {  
  OPENQUERY([<datasource>],'<SELECT statement>') }  
APPEND  
(   
  {OPENQUERY([<datasource>],''<nested SELECT statement>'')  
}  
RELATE [<case key>] TO [<foreign key>]  
) AS [<nested table>]  
```  
  
 <span data-ttu-id="ec22c-126">在本课中，您将使用 `OPENQUERY` 来定义源数据。</span><span class="sxs-lookup"><span data-stu-id="ec22c-126">In this lesson, you use `OPENQUERY` to define the source data.</span></span> <span data-ttu-id="ec22c-127">有关针对源数据定义查询的其他方法的信息，请参阅[&#60;源数据查询&#62;](/sql/dmx/source-data-query)。</span><span class="sxs-lookup"><span data-stu-id="ec22c-127">For information about other methods of defining a query on the source data, see [&#60;source data query&#62;](/sql/dmx/source-data-query).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="ec22c-128">课程任务</span><span class="sxs-lookup"><span data-stu-id="ec22c-128">Lesson Tasks</span></span>  
 <span data-ttu-id="ec22c-129">您将在本课中执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="ec22c-129">You will perform the following task in this lesson:</span></span>  
  
-   <span data-ttu-id="ec22c-130">处理市场篮挖掘结构</span><span class="sxs-lookup"><span data-stu-id="ec22c-130">Process the Market Basket mining structure</span></span>  
  
## <a name="processing-the-market-basket-mining-structure"></a><span data-ttu-id="ec22c-131">处理市场篮挖掘结构</span><span class="sxs-lookup"><span data-stu-id="ec22c-131">Processing the Market Basket Mining Structure</span></span>  
  
#### <a name="to-process-the-mining-structure-by-using-insert-into"></a><span data-ttu-id="ec22c-132">使用 INSERT INTO 处理挖掘结构</span><span class="sxs-lookup"><span data-stu-id="ec22c-132">To process the mining structure by using INSERT INTO</span></span>  
  
1.  <span data-ttu-id="ec22c-133">在**对象资源管理器**中，右键单击实例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 "**新建查询**"，然后单击 " **DMX**"。</span><span class="sxs-lookup"><span data-stu-id="ec22c-133">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="ec22c-134">将打开查询编辑器，其中包含一个新的空白查询。</span><span class="sxs-lookup"><span data-stu-id="ec22c-134">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="ec22c-135">将 INSERT INTO 语句的一般示例复制到空白查询中。</span><span class="sxs-lookup"><span data-stu-id="ec22c-135">Copy the generic example of the INSERT INTO statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="ec22c-136">将</span><span class="sxs-lookup"><span data-stu-id="ec22c-136">Replace the following:</span></span>  
  
    ```  
    [<mining structure>]  
    ```  
  
     <span data-ttu-id="ec22c-137">替换为：</span><span class="sxs-lookup"><span data-stu-id="ec22c-137">with:</span></span>  
  
    ```  
    Market Basket  
    ```  
  
4.  <span data-ttu-id="ec22c-138">将</span><span class="sxs-lookup"><span data-stu-id="ec22c-138">Replace the following:</span></span>  
  
    ```  
    <mining structure columns>  
    [<nested table>]  
    ( SKIP, <skipped column> )  
    ```  
  
     <span data-ttu-id="ec22c-139">替换为：</span><span class="sxs-lookup"><span data-stu-id="ec22c-139">with:</span></span>  
  
    ```  
    [OrderNumber],  
    [Products]   
    (SKIP, [Model])  
    ```  
  
     <span data-ttu-id="ec22c-140">在语句中，`Products` 指代 SHAPE 语句定义的 Products 表。</span><span class="sxs-lookup"><span data-stu-id="ec22c-140">In the statement, `Products` refers to the Products table defined by the SHAPE statement.</span></span> <span data-ttu-id="ec22c-141">`SKIP` 用于忽略 Model 列，该列在源数据中作为键存在，但是挖掘结构未使用它。</span><span class="sxs-lookup"><span data-stu-id="ec22c-141">`SKIP` is used to ignore the Model column, which exists in the source data as a key, but is not used by the mining structure.</span></span>  
  
5.  <span data-ttu-id="ec22c-142">将</span><span class="sxs-lookup"><span data-stu-id="ec22c-142">Replace the following:</span></span>  
  
    ```  
    SHAPE {  
      OPENQUERY([<datasource>],'<SELECT statement>') }  
    APPEND  
    (   
      {OPENQUERY([<datasource>],'<nested SELECT statement>')  
    }  
    RELATE [<case key>] TO [<foreign key>]  
    ) AS [<nested table>]  
    ```  
  
     <span data-ttu-id="ec22c-143">替换为：</span><span class="sxs-lookup"><span data-stu-id="ec22c-143">with:</span></span>  
  
    ```  
    SHAPE {  
      OPENQUERY([Adventure Works DW],'SELECT OrderNumber  
                FROM vAssocSeqOrders ORDER BY OrderNumber')}  
    APPEND  
    (   
      {OPENQUERY([Adventure Works DW],'SELECT OrderNumber, Model FROM   
        dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')  
    }  
    RELATE OrderNumber to OrderNumber   
    ) AS [Products]  
    ```  
  
     <span data-ttu-id="ec22c-144">源查询引用 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 在示例项目中定义的数据源 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ec22c-144">The source query references the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] data source defined in the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sample project.</span></span> <span data-ttu-id="ec22c-145">它使用此数据源访问 vAssocSeqLineItems 和 vAssocSeqOrders 视图。</span><span class="sxs-lookup"><span data-stu-id="ec22c-145">It uses this data source to access the vAssocSeqLineItems and vAssocSeqOrders views.</span></span> <span data-ttu-id="ec22c-146">这些视图包含将用于定型挖掘模型的源数据。</span><span class="sxs-lookup"><span data-stu-id="ec22c-146">These views contain the source data that will be used to train the mining model.</span></span> <span data-ttu-id="ec22c-147">如果尚未创建此项目或这些视图，请参阅[数据挖掘基础教程](../../2014/tutorials/basic-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="ec22c-147">If you have not created this project or these views, see [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md).</span></span>  
  
     <span data-ttu-id="ec22c-148">在 `SHAPE` 命令中，将使用 `OPENQUERY` 定义两个查询。</span><span class="sxs-lookup"><span data-stu-id="ec22c-148">Within the `SHAPE` command, you will use `OPENQUERY` to define two queries.</span></span> <span data-ttu-id="ec22c-149">第一个查询定义父表，第二个查询定义嵌套表。</span><span class="sxs-lookup"><span data-stu-id="ec22c-149">The first query defines the parent table, and the second query defines the nested table.</span></span> <span data-ttu-id="ec22c-150">这两个表是使用 OrderNumber 列关联的，两个表中都包含该列。</span><span class="sxs-lookup"><span data-stu-id="ec22c-150">The two tables are related using the OrderNumber column, which exists in both tables.</span></span>  
  
     <span data-ttu-id="ec22c-151">现在，完整的语句应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="ec22c-151">The complete statement should now be as follows:</span></span>  
  
    ```  
    INSERT INTO MINING STRUCTURE [Market Basket]  
    (  
       [OrderNumber],[Products] (SKIP, [Model])  
    )  
    SHAPE {  
      OPENQUERY([Adventure Works DW],'SELECT OrderNumber  
                FROM vAssocSeqOrders ORDER BY OrderNumber')}  
    APPEND  
    (   
      {OPENQUERY([Adventure Works DW],'SELECT OrderNumber, Model FROM   
        dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')  
    }  
    RELATE OrderNumber to OrderNumber   
    ) AS [Products]  
    ```  
  
6.  <span data-ttu-id="ec22c-152">在 "**文件**" 菜单上，单击 "**将 DMXQuery1 另存为**"。</span><span class="sxs-lookup"><span data-stu-id="ec22c-152">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="ec22c-153">在 "**另存为**" 对话框中，浏览到相应的文件夹，并将该文件命名为 `Process Market Basket.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="ec22c-153">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Process Market Basket.dmx`.</span></span>  
  
8.  <span data-ttu-id="ec22c-154">在工具栏上，单击 "**执行**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="ec22c-154">On the toolbar, click the **Execute** button.</span></span>  
  
 <span data-ttu-id="ec22c-155">在该查询完成运行之后，可以查看已经找到的模式和项集，查看关联，或按项集、概率或重要性进行筛选。</span><span class="sxs-lookup"><span data-stu-id="ec22c-155">After the query has finished running, you can view the patterns and itemsets that were found, view associations, or filter by itemset, probability, or importance.</span></span> <span data-ttu-id="ec22c-156">若要查看此信息，请在中 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 右键单击数据模型的名称，然后单击 "**浏览**"。</span><span class="sxs-lookup"><span data-stu-id="ec22c-156">To view this information, in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], right-click the name of the data model, and then click **Browse**.</span></span>  
  
 <span data-ttu-id="ec22c-157">在下一课中，您将基于添加到市场篮结构中的挖掘模型创建多个预测。</span><span class="sxs-lookup"><span data-stu-id="ec22c-157">In the next lesson, you will create several predictions based on the mining models that you added to the Market Basket structure.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="ec22c-158">下一课</span><span class="sxs-lookup"><span data-stu-id="ec22c-158">Next Lesson</span></span>  
 [<span data-ttu-id="ec22c-159">第 4 课：执行市场篮预测</span><span class="sxs-lookup"><span data-stu-id="ec22c-159">Lesson 4: Executing Market Basket Predictions</span></span>](../../2014/tutorials/lesson-4-executing-market-basket-predictions.md)  
  
  
