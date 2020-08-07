---
title: 第1课：创建市场篮挖掘结构 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a817c8d1-aff4-42b4-b194-ad9cc1c60f35
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a6a6e123e525512a72d70bcc8ca2eba549d1347e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690928"
---
# <a name="lesson-1-creating-the-market-basket-mining-structure"></a><span data-ttu-id="7dbeb-102">第 1 课：创建市场篮挖掘模型</span><span class="sxs-lookup"><span data-stu-id="7dbeb-102">Lesson 1: Creating the Market Basket Mining Structure</span></span>
  <span data-ttu-id="7dbeb-103">在本课中，将创建一个挖掘模型，可以使用该模型预测客户要同时购买的 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 产品。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-103">In this lesson, you will create a mining structure that allows you to predict what [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] products a customer tends to purchase at the same time.</span></span> <span data-ttu-id="7dbeb-104">如果不熟悉挖掘结构及其在数据挖掘中的角色，请参阅[挖掘结构 &#40;Analysis Services 数据挖掘&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-104">If you are unfamiliar with mining structures and their role in data mining, see [Mining Structures &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="7dbeb-105">您将在本课中创建的关联挖掘结构支持根据[Microsoft 关联算法](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)添加挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-105">The association mining structure that you will create in this lesson supports adding mining models based on the [Microsoft Association Algorithm](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md).</span></span> <span data-ttu-id="7dbeb-106">在后面的课程中，您将使用挖掘模型来预测客户要同时购买的产品类型，这称为市场篮分析。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-106">In later lessons, you will use the mining models to predict the type of products a customer tends to purchase at the same time, which is called a market basket analysis.</span></span> <span data-ttu-id="7dbeb-107">例如，您可能会发现客户要同时购买山地自行车、自行车轮胎和头盔。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-107">For example, you may find that customers tend to buy mountain bikes, bike tires, and helmets at the same time.</span></span>  
  
 <span data-ttu-id="7dbeb-108">在本课中，挖掘结构是使用嵌套表定义的。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-108">In this lesson, the mining structure is defined by using nested tables.</span></span> <span data-ttu-id="7dbeb-109">使用嵌套表是因为将由结构定义的数据域分别包含在两个不同的源表中。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-109">Nested tables are used because the data domain that will be defined by the structure is contained within two different source tables.</span></span> <span data-ttu-id="7dbeb-110">有关嵌套表的详细信息，请参阅[&#40;Analysis Services 数据挖掘&#41;的嵌套表](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-110">For more information on nested tables, see [Nested Tables &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md).</span></span>  
  
## <a name="create-mining-structure-statement"></a><span data-ttu-id="7dbeb-111">CREATE 挖掘 STRUCTURE 语句</span><span class="sxs-lookup"><span data-stu-id="7dbeb-111">CREATE MINING STRUCTURE Statement</span></span>  
 <span data-ttu-id="7dbeb-112">若要创建包含嵌套表的挖掘结构，请使用[CREATE 挖掘 structure &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx)语句。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-112">In order to create a mining structure containing a nested table, you use the [CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx) statement.</span></span> <span data-ttu-id="7dbeb-113">可以将语句中的代码分为下列几部分：</span><span class="sxs-lookup"><span data-stu-id="7dbeb-113">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="7dbeb-114">命名结构</span><span class="sxs-lookup"><span data-stu-id="7dbeb-114">Naming the structure</span></span>  
  
-   <span data-ttu-id="7dbeb-115">定义键列</span><span class="sxs-lookup"><span data-stu-id="7dbeb-115">Defining the key column</span></span>  
  
-   <span data-ttu-id="7dbeb-116">定义挖掘列</span><span class="sxs-lookup"><span data-stu-id="7dbeb-116">Defining the mining columns</span></span>  
  
-   <span data-ttu-id="7dbeb-117">定义嵌套表列</span><span class="sxs-lookup"><span data-stu-id="7dbeb-117">Defining the nested table columns</span></span>  
  
 <span data-ttu-id="7dbeb-118">下面是 CREATE MINING STRUCTURE 语句的一般示例：</span><span class="sxs-lookup"><span data-stu-id="7dbeb-118">The following is a generic example of the CREATE MINING STRUCTURE statement:</span></span>  
  
```  
CREATE MINING STRUCTURE [<Mining Structure Name>]  
(  
   <key column>,  
   <mining structure columns>,  
   <table columns>  
   (  <nested key column>,  
      <nested mining structure columns> )  
)  
  
```  
  
 <span data-ttu-id="7dbeb-119">代码的第一行定义了结构的名称：</span><span class="sxs-lookup"><span data-stu-id="7dbeb-119">The first line of the code defines the name of the structure:</span></span>  
  
```  
CREATE MINING STRUCTURE [Mining Structure Name]  
```  
  
 <span data-ttu-id="7dbeb-120">有关在 DMX 中命名对象的信息，请参阅[标识符 &#40;DMX&#41;](/sql/dmx/identifiers-dmx)。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-120">For information about naming an object in DMX, see [Identifiers &#40;DMX&#41;](/sql/dmx/identifiers-dmx).</span></span>  
  
 <span data-ttu-id="7dbeb-121">代码的下一行定义了挖掘结构的键列，它唯一标识源数据中的实体：</span><span class="sxs-lookup"><span data-stu-id="7dbeb-121">The next line of the code defines the key column for the mining structure, which uniquely identifies an entity in the source data:</span></span>  
  
```  
<key column>  
```  
  
 <span data-ttu-id="7dbeb-122">代码的下一行用于定义与挖掘结构关联的挖掘模型所使用的挖掘列：</span><span class="sxs-lookup"><span data-stu-id="7dbeb-122">The next line of the code is used to define the mining columns that will be used by the mining models associated with the mining structure:</span></span>  
  
```  
<mining structure columns>  
```  
  
 <span data-ttu-id="7dbeb-123">代码中接下来几行定义了嵌套表列：</span><span class="sxs-lookup"><span data-stu-id="7dbeb-123">The next lines of the code define the nested table columns:</span></span>  
  
```  
<table columns>  
(  <nested key column>,  
   <nested mining structure columns> )  
```  
  
 <span data-ttu-id="7dbeb-124">有关您可以定义的挖掘结构列的类型的信息，请参阅[挖掘结构列](../../2014/analysis-services/data-mining/mining-structure-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-124">For information about the types of mining structure columns that you can define, see [Mining Structure Columns](../../2014/analysis-services/data-mining/mining-structure-columns.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7dbeb-125">默认情况下，[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 为每个挖掘结构创建 30% 的维持数据集；但是，如果使用 DMX 创建挖掘结构，则必须手动添加维持数据集（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-125">By default, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] creates a 30 percent holdout data set for each mining structure; however, when you use DMX to create a mining structure, you must manually add the holdout data set, if desired.</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="7dbeb-126">课程任务</span><span class="sxs-lookup"><span data-stu-id="7dbeb-126">Lesson Tasks</span></span>  
 <span data-ttu-id="7dbeb-127">您将在本课中执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="7dbeb-127">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="7dbeb-128">创建新的空白查询</span><span class="sxs-lookup"><span data-stu-id="7dbeb-128">Create a new blank query</span></span>  
  
-   <span data-ttu-id="7dbeb-129">更改查询以创建挖掘结构</span><span class="sxs-lookup"><span data-stu-id="7dbeb-129">Alter the query to create the mining structure</span></span>  
  
-   <span data-ttu-id="7dbeb-130">执行查询</span><span class="sxs-lookup"><span data-stu-id="7dbeb-130">Execute the query</span></span>  
  
## <a name="creating-the-query"></a><span data-ttu-id="7dbeb-131">创建查询</span><span class="sxs-lookup"><span data-stu-id="7dbeb-131">Creating the Query</span></span>  
 <span data-ttu-id="7dbeb-132">第一步是连接到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例，并在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中创建一个新的 DMX 查询。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-132">The first step is to connect to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and create a new DMX query in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a><span data-ttu-id="7dbeb-133">在 SQL Server Management Studio 中创建一个新的 DMX 查询</span><span class="sxs-lookup"><span data-stu-id="7dbeb-133">To create a new DMX query in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="7dbeb-134">打开 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-134">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="7dbeb-135">在 "**连接到服务器**" 对话框中，选择 "**服务器类型**" **Analysis Services**。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-135">In the **Connect to Server** dialog box, for **Server type**, select **Analysis Services**.</span></span> <span data-ttu-id="7dbeb-136">在 "**服务器名称**" 中，键入 `LocalHost` 或 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 要为本课连接到的实例的名称。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-136">In **Server name**, type `LocalHost`, or the name of the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you want to connect to for this lesson.</span></span> <span data-ttu-id="7dbeb-137">单击“连接” 。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-137">Click **Connect**.</span></span>  
  
3.  <span data-ttu-id="7dbeb-138">在**对象资源管理器**中，右键单击实例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 "**新建查询**"，然后单击 " **DMX**"。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-138">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="7dbeb-139">将打开查询编辑器，其中包含一个新的空白查询。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-139">Query Editor opens and contains a new, blank query.</span></span>  
  
## <a name="altering-the-query"></a><span data-ttu-id="7dbeb-140">更改查询</span><span class="sxs-lookup"><span data-stu-id="7dbeb-140">Altering the Query</span></span>  
 <span data-ttu-id="7dbeb-141">下一步是修改上述 CREATE MINING STRUCTURE 语句以创建市场篮挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-141">The next step is to modify the CREATE MINING STRUCTURE statement described above to create the Market Basket mining structure.</span></span>  
  
#### <a name="to-customize-the-create-mining-structure-statement"></a><span data-ttu-id="7dbeb-142">自定义 CREATE MINING STRUCTURE 语句</span><span class="sxs-lookup"><span data-stu-id="7dbeb-142">To customize the CREATE MINING STRUCTURE statement</span></span>  
  
1.  <span data-ttu-id="7dbeb-143">在查询编辑器中，将 CREATE 挖掘 STRUCTURE 语句的一般示例复制到空白查询中。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-143">In Query Editor, copy the generic example of the CREATE MINING STRUCTURE statement into the blank query.</span></span>  
  
2.  <span data-ttu-id="7dbeb-144">将</span><span class="sxs-lookup"><span data-stu-id="7dbeb-144">Replace the following:</span></span>  
  
    ```  
    [mining structure name]   
    ```  
  
     <span data-ttu-id="7dbeb-145">替换为：</span><span class="sxs-lookup"><span data-stu-id="7dbeb-145">with:</span></span>  
  
    ```  
    [Market Basket]  
    ```  
  
3.  <span data-ttu-id="7dbeb-146">将</span><span class="sxs-lookup"><span data-stu-id="7dbeb-146">Replace the following:</span></span>  
  
    ```  
    <key column>  
    ```  
  
     <span data-ttu-id="7dbeb-147">替换为：</span><span class="sxs-lookup"><span data-stu-id="7dbeb-147">with:</span></span>  
  
    ```  
    OrderNumber TEXT KEY  
    ```  
  
4.  <span data-ttu-id="7dbeb-148">将</span><span class="sxs-lookup"><span data-stu-id="7dbeb-148">Replace the following:</span></span>  
  
    ```  
    <table columns>  
    (  <nested key column>,  
       <nested mining structure columns> )  
    ```  
  
     <span data-ttu-id="7dbeb-149">替换为：</span><span class="sxs-lookup"><span data-stu-id="7dbeb-149">with:</span></span>  
  
    ```  
    [Products] TABLE (  
        [Model] TEXT KEY  
    )  
    ```  
  
     <span data-ttu-id="7dbeb-150">TEXT KEY 语言指定 Model 列为嵌套表的键列。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-150">The TEXT KEY language specifies that the Model column is the key column for the nested table.</span></span>  
  
     <span data-ttu-id="7dbeb-151">现在，完整的挖掘结构语句应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="7dbeb-151">The complete mining structure statement should now be as follows:</span></span>  
  
    ```  
    CREATE MINING STRUCTURE [Market Basket] (  
        OrderNumber TEXT KEY,  
        [Products] TABLE (  
            [Model] TEXT KEY  
        )  
    )  
    ```  
  
5.  <span data-ttu-id="7dbeb-152">在 "**文件**" 菜单上，单击 "**将 DMXQuery1 另存为**"。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-152">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
6.  <span data-ttu-id="7dbeb-153">在 "**另存为**" 对话框中，浏览到相应的文件夹，并将该文件命名为 `Market Basket Structure.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-153">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Market Basket Structure.dmx`.</span></span>  
  
## <a name="executing-the-query"></a><span data-ttu-id="7dbeb-154">执行查询</span><span class="sxs-lookup"><span data-stu-id="7dbeb-154">Executing the Query</span></span>  
 <span data-ttu-id="7dbeb-155">最后一步是执行查询。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-155">The final step is to execute the query.</span></span> <span data-ttu-id="7dbeb-156">创建并保存查询后，需要执行该查询（即，需要执行该语句）以便在服务器中创建挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-156">After a query is created and saved, it needs to be executed (that is, the statement needs to be run) in order to create the mining structure on the server.</span></span> <span data-ttu-id="7dbeb-157">有关在查询编辑器中执行查询的详细信息，请参阅[SQL Server Management Studio&#41;数据库引擎查询编辑器 &#40;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-157">For more information about executing queries in Query Editor, see [Database Engine Query Editor &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="7dbeb-158">执行查询</span><span class="sxs-lookup"><span data-stu-id="7dbeb-158">To execute the query</span></span>  
  
-   <span data-ttu-id="7dbeb-159">在查询编辑器中，单击工具栏上的 "**执行**"。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-159">In Query Editor, on the toolbar, click **Execute**.</span></span>  
  
     <span data-ttu-id="7dbeb-160">语句执行完毕后，查询的状态将显示在查询编辑器底部的 "**消息**" 选项卡中。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-160">The status of the query is displayed in the **Messages** tab at the bottom of Query Editor after the statement finishes executing.</span></span> <span data-ttu-id="7dbeb-161">所显示的消息应为：</span><span class="sxs-lookup"><span data-stu-id="7dbeb-161">Messages should display:</span></span>  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     <span data-ttu-id="7dbeb-162">服务器上现在已有一个名为 "**市场篮**" 的新结构。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-162">A new structure named **Market Basket** now exists on the server.</span></span>  
  
 <span data-ttu-id="7dbeb-163">在下一课中，您将向刚才创建的市场篮挖掘结构中添加挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="7dbeb-163">In the next lesson, you will add mining models to the Market Basket mining structure you just created.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="7dbeb-164">下一课</span><span class="sxs-lookup"><span data-stu-id="7dbeb-164">Next Lesson</span></span>  
 [<span data-ttu-id="7dbeb-165">第 2 课：向市场篮挖掘结构中添加挖掘模型</span><span class="sxs-lookup"><span data-stu-id="7dbeb-165">Lesson 2: Adding Mining Models to the Market Basket Mining Structure</span></span>](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)  
  
  
