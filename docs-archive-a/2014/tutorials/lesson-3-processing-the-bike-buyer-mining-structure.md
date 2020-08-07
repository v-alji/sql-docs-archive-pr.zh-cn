---
title: 第3课：处理自行车购买者挖掘结构 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e748c2cd-339d-4e82-82f1-be2d0fc41b61
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2e3f85016b32884b9a6b809e28d20d9985f97cd9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690921"
---
# <a name="lesson-3-processing-the-bike-buyer-mining-structure"></a><span data-ttu-id="0c922-102">第 3 课：处理自行车购买者挖掘结构</span><span class="sxs-lookup"><span data-stu-id="0c922-102">Lesson 3: Processing the Bike Buyer Mining Structure</span></span>
  <span data-ttu-id="0c922-103">在本课中，您将使用示例数据库中的 INSERT INTO 语句和 vTargetMail 视图 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 来处理您在第1课中创建的挖掘结构和挖掘模型[：创建自行车购买者挖掘结构](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md)和[第2课：向自行车购买者挖掘结构中添加挖掘模型](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="0c922-103">In this lesson, you will use the INSERT INTO statement and the vTargetMail view from the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sample database to process the mining structures and mining models that you created in [Lesson 1: Creating the Bike Buyer Mining Structure](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md) and [Lesson 2: Adding Mining Models to the Bike Buyer Mining Structure](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md).</span></span>  
  
 <span data-ttu-id="0c922-104">处理挖掘结构时，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将读取源数据并生成支持挖掘模型的结构。</span><span class="sxs-lookup"><span data-stu-id="0c922-104">When you process a mining structure, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] reads the source data and builds the structures that support mining models.</span></span> <span data-ttu-id="0c922-105">处理挖掘模型时，挖掘结构定义的数据将通过所选择的数据挖掘算法进行传递。</span><span class="sxs-lookup"><span data-stu-id="0c922-105">When you process a mining model, the data defined by the mining structure is passed through the data mining algorithm that you choose.</span></span> <span data-ttu-id="0c922-106">该算法将搜索趋势和模式，然后在挖掘模型中存储此信息。</span><span class="sxs-lookup"><span data-stu-id="0c922-106">The algorithm searches for trends and patterns, and then stores this information in the mining model.</span></span> <span data-ttu-id="0c922-107">因此，挖掘模型不包含实际源数据，而是包含由算法发现的信息。</span><span class="sxs-lookup"><span data-stu-id="0c922-107">The mining model, therefore, does not contain the actual source data, but instead contains the information that was discovered by the algorithm.</span></span> <span data-ttu-id="0c922-108">有关处理挖掘模型的详细信息，请参阅[处理 &#40;数据挖掘&#41;的要求和注意事项](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="0c922-108">For more information about processing mining models, see [Processing Requirements and Considerations &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).</span></span>  
  
 <span data-ttu-id="0c922-109">仅在更改了结构列或源数据的情况下，才需要重新处理挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="0c922-109">You need to reprocess a mining structure only if you change a structure column or change the source data.</span></span> <span data-ttu-id="0c922-110">如果将挖掘模型添加到已处理的挖掘结构中，则可使用 INSERT INTO MINING MODEL 语句定型新的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="0c922-110">If you add a mining model to a mining structure that has already been processed, you can use the INSERT INTO MINING MODEL statement to train the new mining model.</span></span>  
  
## <a name="train-structure-template"></a><span data-ttu-id="0c922-111">定型结构模板</span><span class="sxs-lookup"><span data-stu-id="0c922-111">Train Structure Template</span></span>  
 <span data-ttu-id="0c922-112">为了定型挖掘结构及其关联的挖掘模型，请使用[INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)语句。</span><span class="sxs-lookup"><span data-stu-id="0c922-112">In order to train the mining structure and its associated mining models, use the [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) statement.</span></span> <span data-ttu-id="0c922-113">可以将语句中的代码分为下列几部分：</span><span class="sxs-lookup"><span data-stu-id="0c922-113">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="0c922-114">标识挖掘结构</span><span class="sxs-lookup"><span data-stu-id="0c922-114">Identifying the mining structure</span></span>  
  
-   <span data-ttu-id="0c922-115">列出挖掘结构中的列</span><span class="sxs-lookup"><span data-stu-id="0c922-115">Listing the columns in the mining structure</span></span>  
  
-   <span data-ttu-id="0c922-116">定义定型数据</span><span class="sxs-lookup"><span data-stu-id="0c922-116">Defining the training data</span></span>  
  
 <span data-ttu-id="0c922-117">下面是 INSERT INTO 语句的一般示例：</span><span class="sxs-lookup"><span data-stu-id="0c922-117">The following is a generic example of the INSERT INTO statement:</span></span>  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
)  
OPENQUERY([<datasource>],'<SELECT statement>')  
```  
  
 <span data-ttu-id="0c922-118">代码的第一行标识将定型的挖掘结构：</span><span class="sxs-lookup"><span data-stu-id="0c922-118">The first line of the code identifies the mining structure that you will train:</span></span>  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="0c922-119">代码的第二行指定由挖掘结构定义的列。</span><span class="sxs-lookup"><span data-stu-id="0c922-119">The next line of the code specifies the columns that are defined by the mining structure.</span></span> <span data-ttu-id="0c922-120">必须列出挖掘结构的每一列，并且每列必须映射到源查询数据所包含的对应列。</span><span class="sxs-lookup"><span data-stu-id="0c922-120">You must list each column in the mining structure, and each column must map to a column contained within the source query data.</span></span>  
  
```  
(  
   <mining structure columns>  
)  
```  
  
 <span data-ttu-id="0c922-121">代码的最后一行定义将用于定型挖掘结构的数据：</span><span class="sxs-lookup"><span data-stu-id="0c922-121">The final line of the code defines the data that will be used to train the mining structure:</span></span>  
  
```  
OPENQUERY([<datasource>],'<SELECT statement>')  
```  
  
 <span data-ttu-id="0c922-122">在本课中，您将使用 `OPENQUERY` 来定义源数据。</span><span class="sxs-lookup"><span data-stu-id="0c922-122">In this lesson, you use `OPENQUERY` to define the source data.</span></span> <span data-ttu-id="0c922-123">有关定义源查询的其他方法的信息，请参阅[&#60;源数据查询&#62;](/sql/dmx/source-data-query)。</span><span class="sxs-lookup"><span data-stu-id="0c922-123">For information about other methods of defining the source query, see [&#60;source data query&#62;](/sql/dmx/source-data-query).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="0c922-124">课程任务</span><span class="sxs-lookup"><span data-stu-id="0c922-124">Lesson Tasks</span></span>  
 <span data-ttu-id="0c922-125">您将在本课中执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="0c922-125">You will perform the following task in this lesson:</span></span>  
  
-   <span data-ttu-id="0c922-126">处理自行车购买者挖掘结构</span><span class="sxs-lookup"><span data-stu-id="0c922-126">Process the Bike Buyer mining structure</span></span>  
  
## <a name="processing-the-predictive-mining-structure"></a><span data-ttu-id="0c922-127">处理预测性挖掘结构</span><span class="sxs-lookup"><span data-stu-id="0c922-127">Processing the Predictive Mining Structure</span></span>  
  
#### <a name="to-process-the-mining-structure-by-using-insert-into"></a><span data-ttu-id="0c922-128">使用 INSERT INTO 处理挖掘结构</span><span class="sxs-lookup"><span data-stu-id="0c922-128">To process the mining structure by using INSERT INTO</span></span>  
  
1.  <span data-ttu-id="0c922-129">在**对象资源管理器**中，右键单击实例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 "**新建查询**"，然后单击 " **DMX**"。</span><span class="sxs-lookup"><span data-stu-id="0c922-129">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="0c922-130">将打开查询编辑器，其中包含一个新的空白查询。</span><span class="sxs-lookup"><span data-stu-id="0c922-130">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="0c922-131">将 INSERT INTO 语句的一般示例复制到空白查询中。</span><span class="sxs-lookup"><span data-stu-id="0c922-131">Copy the generic example of the INSERT INTO statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="0c922-132">将</span><span class="sxs-lookup"><span data-stu-id="0c922-132">Replace the following:</span></span>  
  
    ```  
    [<mining structure name>]   
    ```  
  
     <span data-ttu-id="0c922-133">替换为：</span><span class="sxs-lookup"><span data-stu-id="0c922-133">with:</span></span>  
  
    ```  
    Bike Buyer  
    ```  
  
4.  <span data-ttu-id="0c922-134">将</span><span class="sxs-lookup"><span data-stu-id="0c922-134">Replace the following:</span></span>  
  
    ```  
    <mining structure columns>  
    ```  
  
     <span data-ttu-id="0c922-135">替换为：</span><span class="sxs-lookup"><span data-stu-id="0c922-135">with:</span></span>  
  
    ```  
    [Customer Key],  
    [Age],  
    [Bike Buyer],  
    [Commute Distance],  
    [Education],  
    [Gender],  
    [House Owner Flag],  
    [Marital Status],  
    [Number Cars Owned],  
    [Number Children At Home],  
    [Occupation],  
    [Region],  
    [Total Children],  
    [Yearly Income]  
    ```  
  
5.  <span data-ttu-id="0c922-136">将</span><span class="sxs-lookup"><span data-stu-id="0c922-136">Replace the following:</span></span>  
  
    ```  
    OPENQUERY([<datasource>],'<SELECT statement>')  
    ```  
  
     <span data-ttu-id="0c922-137">替换为：</span><span class="sxs-lookup"><span data-stu-id="0c922-137">with:</span></span>  
  
    ```  
    OPENQUERY([Adventure Works DW],  
       'SELECT CustomerKey, Age, BikeBuyer,  
             CommuteDistance,EnglishEducation,  
             Gender,HouseOwnerFlag,MaritalStatus,  
             NumberCarsOwned,NumberChildrenAtHome,   
             EnglishOccupation,Region,TotalChildren,  
             YearlyIncome   
        FROM dbo.vTargetMail')  
    ```  
  
     <span data-ttu-id="0c922-138">OPENQUERY 语句将引用 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 数据源，以访问 vTargetMail 视图。</span><span class="sxs-lookup"><span data-stu-id="0c922-138">The OPENQUERY statement references the [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] data source to access the view vTargetMail.</span></span> <span data-ttu-id="0c922-139">该视图包含将用于定型挖掘模型的源数据。</span><span class="sxs-lookup"><span data-stu-id="0c922-139">The view contains the source data that will be used to train the mining models.</span></span>  
  
     <span data-ttu-id="0c922-140">现在，完整的语句应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="0c922-140">The complete statement should now be as follows:</span></span>  
  
    ```  
    INSERT INTO MINING STRUCTURE [Bike Buyer]  
    (  
       [Customer Key],  
       [Age],  
       [Bike Buyer],  
       [Commute Distance],  
       [Education],  
       [Gender],  
       [House Owner Flag],  
       [Marital Status],  
       [Number Cars Owned],  
       [Number Children At Home],  
       [Occupation],  
       [Region],  
       [Total Children],  
       [Yearly Income]     
    )  
    OPENQUERY([Adventure Works DW],  
       'SELECT CustomerKey, Age, BikeBuyer,  
             CommuteDistance,EnglishEducation,  
             Gender,HouseOwnerFlag,MaritalStatus,  
             NumberCarsOwned,NumberChildrenAtHome,   
             EnglishOccupation,Region,TotalChildren,  
             YearlyIncome   
        FROM dbo.vTargetMail')  
    ```  
  
6.  <span data-ttu-id="0c922-141">在 "**文件**" 菜单上，单击 "**将 DMXQuery1 另存为**"。</span><span class="sxs-lookup"><span data-stu-id="0c922-141">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="0c922-142">在 "**另存为**" 对话框中，浏览到相应的文件夹，并将该文件命名为 `Process Bike Buyer Structure.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="0c922-142">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Process Bike Buyer Structure.dmx`.</span></span>  
  
8.  <span data-ttu-id="0c922-143">在工具栏上，单击 "**执行**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="0c922-143">On the toolbar, click the **Execute** button.</span></span>  
  
 <span data-ttu-id="0c922-144">在下一课中，您将浏览在本课中向挖掘结构添加的挖掘模型中的内容。</span><span class="sxs-lookup"><span data-stu-id="0c922-144">In the next lesson, you will explore content in the mining models you added to the mining structure in this lesson.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="0c922-145">下一课</span><span class="sxs-lookup"><span data-stu-id="0c922-145">Next Lesson</span></span>  
 [<span data-ttu-id="0c922-146">第 4 课：浏览自行车购买者挖掘模型</span><span class="sxs-lookup"><span data-stu-id="0c922-146">Lesson 4: Browsing the Bike Buyer Mining Models</span></span>](../../2014/tutorials/lesson-4-browsing-the-bike-buyer-mining-models.md)  
  
  
