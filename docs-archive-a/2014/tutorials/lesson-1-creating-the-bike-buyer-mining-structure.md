---
title: 第1课：创建自行车购买者挖掘结构 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a73ac60b-660f-458a-bd2f-993fbeba7226
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d6384910858d87a80aa3c8f897bc88e45f4504fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690927"
---
# <a name="lesson-1-creating-the-bike-buyer-mining-structure"></a><span data-ttu-id="4385e-102">第 1 课：创建自行车购买者挖掘结构</span><span class="sxs-lookup"><span data-stu-id="4385e-102">Lesson 1: Creating the Bike Buyer Mining Structure</span></span>
  <span data-ttu-id="4385e-103">在本课中，将创建一个挖掘结构，可以使用该结构预测 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 的潜在客户是否会购买自行车。</span><span class="sxs-lookup"><span data-stu-id="4385e-103">In this lesson, you will create a mining structure that allows you to predict whether a potential customer of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] will purchase a bicycle.</span></span> <span data-ttu-id="4385e-104">如果不熟悉挖掘结构及其在数据挖掘中的角色，请参阅[挖掘结构 &#40;Analysis Services 数据挖掘&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="4385e-104">If you are unfamiliar with mining structures and their role in data mining, see [Mining Structures &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="4385e-105">您将在本课中创建的自行车购买者挖掘结构支持根据[Microsoft 聚类分析算法](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)[Microsoft 决策树算法](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)添加挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="4385e-105">The Bike Buyer mining structure that you will create in this lesson supports adding mining models based on the [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)[Microsoft Decision Trees Algorithm](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md).</span></span> <span data-ttu-id="4385e-106">在后面的课程中，您将使用聚类分析挖掘模型来浏览各种客户分组方式，并使用决策树挖掘模型来预测潜在的客户是否将购买自行车。</span><span class="sxs-lookup"><span data-stu-id="4385e-106">In later lessons, you will use the clustering mining models to explore the different ways in which customers can be grouped, and will use decision tree mining models to predict whether or not a potential customer will purchase a bicycle.</span></span>  
  
## <a name="create-mining-structure-statement"></a><span data-ttu-id="4385e-107">CREATE 挖掘 STRUCTURE 语句</span><span class="sxs-lookup"><span data-stu-id="4385e-107">CREATE MINING STRUCTURE Statement</span></span>  
 <span data-ttu-id="4385e-108">若要创建挖掘结构，请使用[CREATE 挖掘 structure &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx)语句。</span><span class="sxs-lookup"><span data-stu-id="4385e-108">To create a mining structure, you use the [CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx) statement.</span></span> <span data-ttu-id="4385e-109">可以将语句中的代码分为下列几部分：</span><span class="sxs-lookup"><span data-stu-id="4385e-109">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="4385e-110">命名结构。</span><span class="sxs-lookup"><span data-stu-id="4385e-110">Naming the structure.</span></span>  
  
-   <span data-ttu-id="4385e-111">定义键列。</span><span class="sxs-lookup"><span data-stu-id="4385e-111">Defining the key column.</span></span>  
  
-   <span data-ttu-id="4385e-112">定义挖掘列。</span><span class="sxs-lookup"><span data-stu-id="4385e-112">Defining the mining columns.</span></span>  
  
-   <span data-ttu-id="4385e-113">定义可选的测试数据集。</span><span class="sxs-lookup"><span data-stu-id="4385e-113">Defining an optional testing data set.</span></span>  
  
 <span data-ttu-id="4385e-114">下面是 CREATE MINING STRUCTURE 语句的一般示例：</span><span class="sxs-lookup"><span data-stu-id="4385e-114">The following is a generic example of the CREATE MINING STRUCTURE statement:</span></span>  
  
```  
CREATE MINING STRUCTURE [<mining structure name>]  
(  
    <key column>,  
    <mining structure columns>  
)   
WITH HOLDOUT (<holdout specifier>)  
```  
  
 <span data-ttu-id="4385e-115">代码的第一行定义了结构的名称：</span><span class="sxs-lookup"><span data-stu-id="4385e-115">The first line of the code defines the name of the structure:</span></span>  
  
```  
CREATE MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="4385e-116">有关在 (DMX) 的数据挖掘扩展插件中命名对象的信息，请参阅[标识符 &#40;dmx&#41;](/sql/dmx/identifiers-dmx)。</span><span class="sxs-lookup"><span data-stu-id="4385e-116">For information about naming an object in Data Mining Extensions (DMX), see [Identifiers &#40;DMX&#41;](/sql/dmx/identifiers-dmx).</span></span>  
  
 <span data-ttu-id="4385e-117">代码的下一行定义了挖掘结构的键列，它唯一标识源数据中的实体：</span><span class="sxs-lookup"><span data-stu-id="4385e-117">The next line of the code defines the key column for the mining structure, which uniquely identifies an entity in the source data:</span></span>  
  
```  
<key column>,  
```  
  
 <span data-ttu-id="4385e-118">在将要创建的挖掘结构中，客户标识符 `CustomerKey` 定义了源数据中的实体。</span><span class="sxs-lookup"><span data-stu-id="4385e-118">In the mining structure you will create, the customer identifier, `CustomerKey`, defines an entity in the source data.</span></span>  
  
 <span data-ttu-id="4385e-119">代码的下一行用于定义与挖掘结构关联的挖掘模型所使用的挖掘列：</span><span class="sxs-lookup"><span data-stu-id="4385e-119">The next line of the code is used to define the mining columns that will be used by the mining models associated with the mining structure:</span></span>  
  
```  
<mining structure columns>  
```  
  
 <span data-ttu-id="4385e-120">可以通过使用以下语法，在中使用离散化函数 \<mining structure columns> 来离散化连续列：</span><span class="sxs-lookup"><span data-stu-id="4385e-120">You can use the DISCRETIZE function within \<mining structure columns> to discretize continuous columns by using the following syntax:</span></span>  
  
 `DISCRETIZE(<method>,<number of buckets>)`  
  
 <span data-ttu-id="4385e-121">有关离散化列的详细信息，请参阅[数据挖掘&#41;&#40;离散化方法](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="4385e-121">For more information about discretizing columns, see [Discretization Methods &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md).</span></span> <span data-ttu-id="4385e-122">有关您可以定义的挖掘结构列类型的详细信息，请参阅[挖掘结构列](../../2014/analysis-services/data-mining/mining-structure-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="4385e-122">For more information about the types of mining structure columns that you can define, see [Mining Structure Columns](../../2014/analysis-services/data-mining/mining-structure-columns.md).</span></span>  
  
 <span data-ttu-id="4385e-123">最后一行代码定义挖掘结构中的可选分区：</span><span class="sxs-lookup"><span data-stu-id="4385e-123">The final line of the code defines an optional partition in the mining structure:</span></span>  
  
```  
WITH HOLDOUT (<holdout specifier>)  
```  
  
 <span data-ttu-id="4385e-124">您要指定某些数据用于测试与该结构相关的挖掘模型，剩余数据用于定型该模型。</span><span class="sxs-lookup"><span data-stu-id="4385e-124">You specify some portion of the data to use for testing mining models that are related to the structure, and the remaining data is used for training the models.</span></span> <span data-ttu-id="4385e-125">默认情况下，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 创建的测试数据集包含所有事例数据的 30%。</span><span class="sxs-lookup"><span data-stu-id="4385e-125">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] creates a test data set that contains 30 percent of all case data.</span></span> <span data-ttu-id="4385e-126">您将添加这样一个说明：测试数据集应包含 30% 的事例，并且最多可以包含 1000 个事例。</span><span class="sxs-lookup"><span data-stu-id="4385e-126">You will add the specification that the test data set should contain 30 percent of the cases up to a maximum of 1000 cases.</span></span> <span data-ttu-id="4385e-127">如果 30% 的事例不足 1000 个，则测试数据集将包含较小数量的事例。</span><span class="sxs-lookup"><span data-stu-id="4385e-127">If 30 percent of the cases is less than 1000, the test data set will contain the smaller amount.</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="4385e-128">课程任务</span><span class="sxs-lookup"><span data-stu-id="4385e-128">Lesson Tasks</span></span>  
 <span data-ttu-id="4385e-129">您将在本课中执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="4385e-129">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="4385e-130">创建新的空白查询。</span><span class="sxs-lookup"><span data-stu-id="4385e-130">Create a new blank query.</span></span>  
  
-   <span data-ttu-id="4385e-131">更改查询以创建挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="4385e-131">Alter the query to create the mining structure.</span></span>  
  
-   <span data-ttu-id="4385e-132">执行查询。</span><span class="sxs-lookup"><span data-stu-id="4385e-132">Execute the query.</span></span>  
  
## <a name="creating-the-query"></a><span data-ttu-id="4385e-133">创建查询</span><span class="sxs-lookup"><span data-stu-id="4385e-133">Creating the Query</span></span>  
 <span data-ttu-id="4385e-134">第一步是连接到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例，并在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中创建一个新的 DMX 查询。</span><span class="sxs-lookup"><span data-stu-id="4385e-134">The first step is to connect to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and create a new DMX query in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a><span data-ttu-id="4385e-135">在 SQL Server Management Studio 中创建一个新的 DMX 查询</span><span class="sxs-lookup"><span data-stu-id="4385e-135">To create a new DMX query in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="4385e-136">打开 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4385e-136">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="4385e-137">在 "**连接到服务器**" 对话框中，选择 "**服务器类型**" **Analysis Services**。</span><span class="sxs-lookup"><span data-stu-id="4385e-137">In the **Connect to Server** dialog box, for **Server type**, select **Analysis Services**.</span></span> <span data-ttu-id="4385e-138">在 "**服务器名称**" 中，键入 `LocalHost` 或键入 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 要为本课连接到的实例的名称。</span><span class="sxs-lookup"><span data-stu-id="4385e-138">In **Server name**, type `LocalHost`, or type the name of the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you want to connect to for this lesson.</span></span> <span data-ttu-id="4385e-139">单击“连接” 。</span><span class="sxs-lookup"><span data-stu-id="4385e-139">Click **Connect**.</span></span>  
  
3.  <span data-ttu-id="4385e-140">在**对象资源管理器**中，右键单击实例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 "**新建查询**"，然后单击 " **DMX** "，打开**查询编辑器**和一个新的空白查询。</span><span class="sxs-lookup"><span data-stu-id="4385e-140">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX** to open the **Query Editor** and a new, blank query.</span></span>  
  
## <a name="altering-the-query"></a><span data-ttu-id="4385e-141">更改查询</span><span class="sxs-lookup"><span data-stu-id="4385e-141">Altering the Query</span></span>  
 <span data-ttu-id="4385e-142">第二步是修改上述 CREATE MINING STRUCTURE 语句以创建自行车购买者挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="4385e-142">The next step is to modify the CREATE MINING STRUCTURE statement described above to create the Bike Buyer mining structure.</span></span>  
  
#### <a name="to-customize-the-create-mining-structure-statement"></a><span data-ttu-id="4385e-143">自定义 CREATE MINING STRUCTURE 语句</span><span class="sxs-lookup"><span data-stu-id="4385e-143">To customize the CREATE MINING STRUCTURE statement</span></span>  
  
1.  <span data-ttu-id="4385e-144">在查询编辑器中，将 CREATE MINING STRUCTURE 语句的一般示例复制到空白查询中。</span><span class="sxs-lookup"><span data-stu-id="4385e-144">In the Query Editor, copy the generic example of the CREATE MINING STRUCTURE statement into the blank query.</span></span>  
  
2.  <span data-ttu-id="4385e-145">将</span><span class="sxs-lookup"><span data-stu-id="4385e-145">Replace the following:</span></span>  
  
    ```  
    [<mining structure>]   
    ```  
  
     <span data-ttu-id="4385e-146">替换为：</span><span class="sxs-lookup"><span data-stu-id="4385e-146">with:</span></span>  
  
    ```  
    [Bike Buyer]  
    ```  
  
3.  <span data-ttu-id="4385e-147">将</span><span class="sxs-lookup"><span data-stu-id="4385e-147">Replace the following:</span></span>  
  
    ```  
    <key column>   
    ```  
  
     <span data-ttu-id="4385e-148">替换为：</span><span class="sxs-lookup"><span data-stu-id="4385e-148">with:</span></span>  
  
    ```  
    CustomerKey LONG KEY  
    ```  
  
4.  <span data-ttu-id="4385e-149">将</span><span class="sxs-lookup"><span data-stu-id="4385e-149">Replace the following:</span></span>  
  
    ```  
    <mining structure columns>   
    ```  
  
     <span data-ttu-id="4385e-150">替换为：</span><span class="sxs-lookup"><span data-stu-id="4385e-150">with:</span></span>  
  
    ```  
    [Age] LONG DISCRETIZED(Automatic,10),  
    [Bike Buyer] LONG DISCRETE,  
    [Commute Distance] TEXT DISCRETE,  
    [Education] TEXT DISCRETE,  
    [Gender] TEXT DISCRETE,  
    [House Owner Flag] TEXT DISCRETE,  
    [Marital Status] TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Number Children At Home] LONG DISCRETE,  
    [Occupation] TEXT DISCRETE,  
    [Region] TEXT DISCRETE,  
    [Total Children]LONG DISCRETE,  
    [Yearly Income] DOUBLE CONTINUOUS  
    ```  
  
5.  <span data-ttu-id="4385e-151">将</span><span class="sxs-lookup"><span data-stu-id="4385e-151">Replace the following:</span></span>  
  
    ```  
    WITH HOLDOUT (holdout specifier>)  
    ```  
  
     <span data-ttu-id="4385e-152">替换为：</span><span class="sxs-lookup"><span data-stu-id="4385e-152">with:</span></span>  
  
    ```  
    WITH HOLDOUT (30 PERCENT or 1000 CASES)  
    ```  
  
     <span data-ttu-id="4385e-153">现在，完整的挖掘结构语句应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="4385e-153">The complete mining structure statement should now be as follows:</span></span>  
  
    ```  
    CREATE MINING STRUCTURE [Bike Buyer]  
    (  
       [Customer Key] LONG KEY,  
       [Age]LONG DISCRETIZED(Automatic,10),  
       [Bike Buyer] LONG DISCRETE,  
       [Commute Distance] TEXT DISCRETE,  
       [Education] TEXT DISCRETE,  
       [Gender] TEXT DISCRETE,  
       [House Owner Flag] TEXT DISCRETE,  
       [Marital Status] TEXT DISCRETE,  
       [Number Cars Owned]LONG DISCRETE,  
       [Number Children At Home]LONG DISCRETE,  
       [Occupation] TEXT DISCRETE,  
       [Region] TEXT DISCRETE,  
       [Total Children]LONG DISCRETE,  
       [Yearly Income] DOUBLE CONTINUOUS  
    )  
    WITH HOLDOUT (30 PERCENT or 1000 CASES)  
  
    ```  
  
6.  <span data-ttu-id="4385e-154">在 "**文件**" 菜单上，单击 "**将 DMXQuery1 另存为**"。</span><span class="sxs-lookup"><span data-stu-id="4385e-154">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="4385e-155">在 "**另存为**" 对话框中，浏览到相应的文件夹，并将该文件命名为 `Bike Buyer Structure.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="4385e-155">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Bike Buyer Structure.dmx`.</span></span>  
  
## <a name="executing-the-query"></a><span data-ttu-id="4385e-156">执行查询</span><span class="sxs-lookup"><span data-stu-id="4385e-156">Executing the Query</span></span>  
 <span data-ttu-id="4385e-157">最后一步是执行查询。</span><span class="sxs-lookup"><span data-stu-id="4385e-157">The final step is to execute the query.</span></span> <span data-ttu-id="4385e-158">创建并保存查询后，需要执行查询。</span><span class="sxs-lookup"><span data-stu-id="4385e-158">After a query is created and saved, it needs to be executed.</span></span> <span data-ttu-id="4385e-159">也就是说，需要运行查询语句以便在服务器上创建挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="4385e-159">That is, the statement needs to be run in order to create the mining structure on the server.</span></span> <span data-ttu-id="4385e-160">有关在查询编辑器中执行查询的详细信息，请参阅[SQL Server Management Studio&#41;数据库引擎查询编辑器 &#40;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="4385e-160">For more information about executing queries in Query Editor, see [Database Engine Query Editor &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="4385e-161">执行查询</span><span class="sxs-lookup"><span data-stu-id="4385e-161">To execute the query</span></span>  
  
1.  <span data-ttu-id="4385e-162">在查询编辑器中，单击工具栏上的 "**执行**"。</span><span class="sxs-lookup"><span data-stu-id="4385e-162">In Query Editor, on the toolbar, click **Execute**.</span></span>  
  
     <span data-ttu-id="4385e-163">语句执行完毕后，查询的状态将显示在查询编辑器底部的 "**消息**" 选项卡中。</span><span class="sxs-lookup"><span data-stu-id="4385e-163">The status of the query is displayed in the **Messages** tab at the bottom of Query Editor after the statement finishes executing.</span></span> <span data-ttu-id="4385e-164">所显示的消息应为：</span><span class="sxs-lookup"><span data-stu-id="4385e-164">Messages should display:</span></span>  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     <span data-ttu-id="4385e-165">名为 "**自行车购买**者" 的新结构现在存在于服务器上。</span><span class="sxs-lookup"><span data-stu-id="4385e-165">A new structure named **Bike Buyer** now exists on the server.</span></span>  
  
 <span data-ttu-id="4385e-166">在下一课中，您将向刚才创建的结构中添加挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="4385e-166">In the next lesson, you will add mining models to the structure you just created.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="4385e-167">下一课</span><span class="sxs-lookup"><span data-stu-id="4385e-167">Next Lesson</span></span>  
 [<span data-ttu-id="4385e-168">第 2 课：向自行车购买者挖掘结构添加挖掘模型</span><span class="sxs-lookup"><span data-stu-id="4385e-168">Lesson 2: Adding Mining Models to the Bike Buyer Mining Structure</span></span>](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)  
  
  
