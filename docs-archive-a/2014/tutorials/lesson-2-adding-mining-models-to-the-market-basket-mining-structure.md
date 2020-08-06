---
title: 第2课：向市场篮挖掘结构中添加挖掘模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d96a7a7d-35d7-4b34-abb5-f0822c256253
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b9573d9359983e33cf23533787c26039572710ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690261"
---
# <a name="lesson-2-adding-mining-models-to-the-market-basket-mining-structure"></a><span data-ttu-id="43167-102">第 2 课：向市场篮挖掘结构中添加挖掘模型</span><span class="sxs-lookup"><span data-stu-id="43167-102">Lesson 2: Adding Mining Models to the Market Basket Mining Structure</span></span>
  <span data-ttu-id="43167-103">在本课中，您将向在[第1课：创建市场篮挖掘结构](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md)中创建的市场篮挖掘结构中添加两个挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="43167-103">In this lesson, you will add two mining models to the Market Basket mining structure that you created in [Lesson 1: Creating the Market Basket Mining Structure](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md).</span></span> <span data-ttu-id="43167-104">您可以通过这些挖掘模型创建预测。</span><span class="sxs-lookup"><span data-stu-id="43167-104">These mining models will allow you to create predictions.</span></span>  
  
 <span data-ttu-id="43167-105">若要预测客户往往同时购买的产品类型，您将使用[Microsoft 关联算法](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)创建两个挖掘模型，并为*MINIMUM_PROBABILTY*参数创建两个不同的值。</span><span class="sxs-lookup"><span data-stu-id="43167-105">To predict the types of products that customers tend to purchase at the same time, you will create two mining models using the [Microsoft Association Algorithm](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md) and two different values for the *MINIMUM_PROBABILTY* parameter.</span></span>  
  
 <span data-ttu-id="43167-106">*MINIMUM_PROBABILTY*是一种 [!INCLUDE[msCoName](../includes/msconame-md.md)] 关联算法参数，通过指定规则必须具有的最小概率，有助于确定挖掘模型将包含的规则数。</span><span class="sxs-lookup"><span data-stu-id="43167-106">*MINIMUM_PROBABILTY* is a [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm parameter that helps to determine the number of rules that a mining model will contain by specifying the minimum probability that a rule must have.</span></span> <span data-ttu-id="43167-107">例如，如果此值设置为 0.4，则表明仅当规则所描述的产品组合具有至少 40% 的发生概率时才可生成此规则。</span><span class="sxs-lookup"><span data-stu-id="43167-107">For example, setting this value to 0.4 specifies that a rule can be generated only if the combination of products that the rule describes has at least a forty percent probability of occurring.</span></span>  
  
 <span data-ttu-id="43167-108">您将在后面的课程中查看更改*MINIMUM_PROBABILTY*参数的效果。</span><span class="sxs-lookup"><span data-stu-id="43167-108">You will view the effect of changing the *MINIMUM_PROBABILTY* parameter in a later lesson.</span></span>  
  
## <a name="alter-mining-structure-statement"></a><span data-ttu-id="43167-109">ALTER MINING STRUCTURE 语句</span><span class="sxs-lookup"><span data-stu-id="43167-109">ALTER MINING STRUCTURE Statement</span></span>  
 <span data-ttu-id="43167-110">若要将包含嵌套表的挖掘模型添加到挖掘结构，请使用[&#40;DMX&#41;语句的 ALTER 挖掘 structure](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016) 。</span><span class="sxs-lookup"><span data-stu-id="43167-110">To add a mining model that contains a nested table to a mining structure, you use the [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016) statement.</span></span> <span data-ttu-id="43167-111">可以将语句中的代码分为下列几部分：</span><span class="sxs-lookup"><span data-stu-id="43167-111">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="43167-112">标识挖掘结构</span><span class="sxs-lookup"><span data-stu-id="43167-112">Identifying the mining structure</span></span>  
  
-   <span data-ttu-id="43167-113">命名挖掘模型</span><span class="sxs-lookup"><span data-stu-id="43167-113">Naming the mining model</span></span>  
  
-   <span data-ttu-id="43167-114">定义键列</span><span class="sxs-lookup"><span data-stu-id="43167-114">Defining the key column</span></span>  
  
-   <span data-ttu-id="43167-115">定义输入列和可预测列</span><span class="sxs-lookup"><span data-stu-id="43167-115">Defining the input and predictable columns</span></span>  
  
-   <span data-ttu-id="43167-116">定义嵌套表列</span><span class="sxs-lookup"><span data-stu-id="43167-116">Defining the nested table columns</span></span>  
  
-   <span data-ttu-id="43167-117">标识算法和参数更改</span><span class="sxs-lookup"><span data-stu-id="43167-117">Identifying the algorithm and parameter changes</span></span>  
  
 <span data-ttu-id="43167-118">下面是 `ALTER MINING STRUCTURE` 语句的一般示例，它将包含嵌套表列的挖掘模型添加到结构中：</span><span class="sxs-lookup"><span data-stu-id="43167-118">The following is a generic example of the `ALTER MINING STRUCTURE` statement that adds a mining model to a structure that includes nested table columns:</span></span>  
  
```  
ALTER MINING STRUCTURE [<Mining Structure Name>]  
ADD MINING MODEL [<Mining Model Name>]  
(  
    [<key column>],  
    <mining model column> <usage>,  
    <table columns>  
    (  [<nested key column>],  
       <nested mining model columns> )  
) USING <algorithm>( <algorithm parameters> )  
```  
  
 <span data-ttu-id="43167-119">上述代码的第一行标识要向其添加挖掘模型的现有挖掘结构：</span><span class="sxs-lookup"><span data-stu-id="43167-119">The first line of the code identifies the existing mining structure to which the mining model will be added:</span></span>  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="43167-120">代码的第二行对将要添加到挖掘结构中的挖掘模型进行命名：</span><span class="sxs-lookup"><span data-stu-id="43167-120">The next line of the code names the mining model that will be added to the mining structure:</span></span>  
  
```  
ADD MINING MODEL [<mining model name>]  
```  
  
 <span data-ttu-id="43167-121">有关在 (DMX) 的数据挖掘扩展插件中命名对象的信息，请参阅[标识符 &#40;dmx&#41;](/sql/dmx/identifiers-dmx)。</span><span class="sxs-lookup"><span data-stu-id="43167-121">For information about naming an object in Data Mining Extensions (DMX), see [Identifiers &#40;DMX&#41;](/sql/dmx/identifiers-dmx).</span></span>  
  
 <span data-ttu-id="43167-122">代码的接下来的各行对挖掘结构中将由挖掘模型使用的各列进行定义：</span><span class="sxs-lookup"><span data-stu-id="43167-122">The next lines of the code define the columns in the mining structure that will be used by the mining model:</span></span>  
  
```  
[<key column>],  
<mining model columns> <usage>,  
```  
  
 <span data-ttu-id="43167-123">您可以只使用挖掘结构中已有的列。</span><span class="sxs-lookup"><span data-stu-id="43167-123">You can only use columns that already exist in the mining structure.</span></span>  
  
 <span data-ttu-id="43167-124">挖掘模型列的列表中的第一列必须为挖掘结构中的键列。</span><span class="sxs-lookup"><span data-stu-id="43167-124">The first column in the list of mining model columns must be the key column in the mining structure.</span></span> <span data-ttu-id="43167-125">但是，您不必在 `KEY` 键列的后面键入来指定用法。</span><span class="sxs-lookup"><span data-stu-id="43167-125">However, you do not have to type `KEY` after the key column to specify usage.</span></span> <span data-ttu-id="43167-126">这是因为您在创建挖掘结构时已将列定义为键。</span><span class="sxs-lookup"><span data-stu-id="43167-126">That is because you have already defined the column as a key when you created the mining structure.</span></span>  
  
 <span data-ttu-id="43167-127">其他行指定新挖掘模型中的列的用法。</span><span class="sxs-lookup"><span data-stu-id="43167-127">The remaining lines specify the usage of the columns in the new mining model.</span></span> <span data-ttu-id="43167-128">您可以使用以下语法指定挖掘模型中的列将用于预测：</span><span class="sxs-lookup"><span data-stu-id="43167-128">You can specify that a column in the mining model will be used for prediction by using the following syntax:</span></span>  
  
```  
<column name> PREDICT,  
```  
  
 <span data-ttu-id="43167-129">如果没有指定用法，则不必在列表中包含数据挖掘结构列。</span><span class="sxs-lookup"><span data-stu-id="43167-129">If you do not specify usage, you do not have to include a data mining structure column in the list.</span></span> <span data-ttu-id="43167-130">由引用的数据挖掘结构所使用的所有列可自动用于基于该结构的挖掘模型中。</span><span class="sxs-lookup"><span data-stu-id="43167-130">All columns that are used by the referenced data mining structure are automatically available for use by the mining models that are based on that structure.</span></span> <span data-ttu-id="43167-131">但是，除非您指定用法，否则模型不会将这些列用于定型。</span><span class="sxs-lookup"><span data-stu-id="43167-131">However, the model will not use the columns for training unless you specify the usage.</span></span>  
  
 <span data-ttu-id="43167-132">代码的最后一行定义将用于生成挖掘模型的算法和算法参数。</span><span class="sxs-lookup"><span data-stu-id="43167-132">The last line in the code defines the algorithm and algorithm parameters that will be used to generate the mining model.</span></span>  
  
```  
) USING <algorithm>( <algorithm parameters> )  
```  
  
## <a name="lesson-tasks"></a><span data-ttu-id="43167-133">课程任务</span><span class="sxs-lookup"><span data-stu-id="43167-133">Lesson Tasks</span></span>  
 <span data-ttu-id="43167-134">您将在本课中执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="43167-134">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="43167-135">使用默认的概率向结构中添加关联挖掘模型</span><span class="sxs-lookup"><span data-stu-id="43167-135">Add an association mining model to the structure using the default probability</span></span>  
  
-   <span data-ttu-id="43167-136">使用修改的概率向结构中添加关联挖掘模型</span><span class="sxs-lookup"><span data-stu-id="43167-136">Add an association mining model to the structure using a modified probability</span></span>  
  
## <a name="adding-an-association-mining-model-to-the-structure-using-the-default-minimum_probability"></a><span data-ttu-id="43167-137">使用默认的 MINIMUM_PROBABILITY 向结构中添加关联挖掘模型</span><span class="sxs-lookup"><span data-stu-id="43167-137">Adding an Association Mining Model to the Structure Using the Default MINIMUM_PROBABILITY</span></span>  
 <span data-ttu-id="43167-138">第一个任务是 [!INCLUDE[msCoName](../includes/msconame-md.md)] 使用*MINIMUM_PROBABILITY*的默认值将新的挖掘模型添加到市场篮挖掘结构中。</span><span class="sxs-lookup"><span data-stu-id="43167-138">The first task is to add a new mining model to the Market Basket mining structure based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm using the default value for *MINIMUM_PROBABILITY*.</span></span>  
  
#### <a name="to-add-an-association-mining-model"></a><span data-ttu-id="43167-139">添加关联挖掘模型</span><span class="sxs-lookup"><span data-stu-id="43167-139">To add an Association mining model</span></span>  
  
1.  <span data-ttu-id="43167-140">在**对象资源管理器**中，右键单击实例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 "**新建查询**"，然后单击 " **DMX**"。</span><span class="sxs-lookup"><span data-stu-id="43167-140">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="43167-141">将打开查询编辑器，其中包含一个新的空白查询。</span><span class="sxs-lookup"><span data-stu-id="43167-141">Query Editor opens and contains a new, blank query.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="43167-142">若要对特定的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库创建 DMX 查询，请右键单击该数据库而不是右键单击实例。</span><span class="sxs-lookup"><span data-stu-id="43167-142">To create a DMX query against a specific [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, right-click the database instead of the instance.</span></span>  
  
2.  <span data-ttu-id="43167-143">将 `ALTER MINING STRUCTURE` 语句的一般示例复制到空白查询中。</span><span class="sxs-lookup"><span data-stu-id="43167-143">Copy the generic example of the `ALTER MINING STRUCTURE` statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="43167-144">将</span><span class="sxs-lookup"><span data-stu-id="43167-144">Replace the following:</span></span>  
  
    ```  
    <mining structure name>   
    ```  
  
     <span data-ttu-id="43167-145">替换为：</span><span class="sxs-lookup"><span data-stu-id="43167-145">with:</span></span>  
  
    ```  
    [Market Basket]  
    ```  
  
4.  <span data-ttu-id="43167-146">将</span><span class="sxs-lookup"><span data-stu-id="43167-146">Replace the following:</span></span>  
  
    ```  
    <mining model name>   
    ```  
  
     <span data-ttu-id="43167-147">替换为：</span><span class="sxs-lookup"><span data-stu-id="43167-147">with:</span></span>  
  
    ```  
    [Default Association]  
    ```  
  
5.  <span data-ttu-id="43167-148">将</span><span class="sxs-lookup"><span data-stu-id="43167-148">Replace the following:</span></span>  
  
    ```  
    [<key column>],  
    <mining model columns>,  
    <table columns>  
    (  [<nested key column>],  
       <nested mining model columns> )  
    ```  
  
     <span data-ttu-id="43167-149">替换为：</span><span class="sxs-lookup"><span data-stu-id="43167-149">with:</span></span>  
  
    ```  
    OrderNumber,  
        [Products] PREDICT (  
            [Model]  
        )  
    ```  
  
     <span data-ttu-id="43167-150">在本例中，`[Products]` 表已被指定为可预测列`.`。此外，`[Model]` 列包含于嵌套表列的列表中，原因是它是嵌套表的键列。</span><span class="sxs-lookup"><span data-stu-id="43167-150">In this case, the `[Products]` table has been designated as the predictable column`.` Also, the `[Model]` column is included in the list of nested table columns because it is the key column of the nested table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="43167-151">请注意，嵌套键不同于事例键。</span><span class="sxs-lookup"><span data-stu-id="43167-151">Remember that a nested key is different from a case key.</span></span> <span data-ttu-id="43167-152">事例键是事例的唯一标识符，而嵌套键是您想要建模的属性。</span><span class="sxs-lookup"><span data-stu-id="43167-152">A case key is a unique identifier of the case, whereas the nested key is an attribute that you want to model.</span></span>  
  
6.  <span data-ttu-id="43167-153">将</span><span class="sxs-lookup"><span data-stu-id="43167-153">Replace the following:</span></span>  
  
    ```  
    USING <algorithm>( <algorithm parameters> )  
    ```  
  
     <span data-ttu-id="43167-154">替换为：</span><span class="sxs-lookup"><span data-stu-id="43167-154">with:</span></span>  
  
    ```  
    Using Microsoft_Association_Rules  
    ```  
  
     <span data-ttu-id="43167-155">现在，结果语句应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="43167-155">The resulting statement should now be as follows:</span></span>  
  
    ```  
    ALTER MINING STRUCTURE [Market Basket]  
    ADD MINING MODEL [Default Association]  
    (  
        OrderNumber,  
        [Products] PREDICT (  
            [Model]  
        )  
    )  
    Using Microsoft_Association_Rules  
    ```  
  
7.  <span data-ttu-id="43167-156">在 "**文件**" 菜单上，单击 "**将 DMXQuery1 另存为**"。</span><span class="sxs-lookup"><span data-stu-id="43167-156">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
8.  <span data-ttu-id="43167-157">在 "**另存为**" 对话框中，浏览到相应的文件夹，并将该文件命名为 `Default_Association_Model.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="43167-157">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Default_Association_Model.dmx`.</span></span>  
  
9. <span data-ttu-id="43167-158">在工具栏上，单击 "**执行**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="43167-158">On the toolbar, click the **Execute** button.</span></span>  
  
## <a name="adding-an-association-mining-model-to-the-structure-changing-the-default-minimum_probability"></a><span data-ttu-id="43167-159">向结构中添加关联挖掘模型并更改默认的 MINIMUM_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="43167-159">Adding an Association Mining Model to the Structure Changing the Default MINIMUM_PROBABILITY</span></span>  
 <span data-ttu-id="43167-160">下一个任务是根据 [!INCLUDE[msCoName](../includes/msconame-md.md)] 关联算法，向市场篮挖掘结构中添加新的挖掘模型，并将 MINIMUM_PROBABILITY 的默认值改为 0.01。</span><span class="sxs-lookup"><span data-stu-id="43167-160">The next task is to add a new mining model to the Market Basket mining structure based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm, and change the default value for MINIMUM_PROBABILITY to 0.01.</span></span> <span data-ttu-id="43167-161">更改参数会导致 [!INCLUDE[msCoName](../includes/msconame-md.md)] 关联算法创建更多的规则。</span><span class="sxs-lookup"><span data-stu-id="43167-161">Changing the parameter will cause the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm to create more rules.</span></span>  
  
#### <a name="to-add-an-association-mining-model"></a><span data-ttu-id="43167-162">添加关联挖掘模型</span><span class="sxs-lookup"><span data-stu-id="43167-162">To add an Association mining model</span></span>  
  
1.  <span data-ttu-id="43167-163">在**对象资源管理器**中，右键单击实例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 "**新建查询**"，然后单击 " **DMX**"。</span><span class="sxs-lookup"><span data-stu-id="43167-163">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="43167-164">将打开查询编辑器，其中包含一个新的空白查询。</span><span class="sxs-lookup"><span data-stu-id="43167-164">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="43167-165">将 `ALTER MINING STRUCTURE` 语句的一般示例复制到空白查询中。</span><span class="sxs-lookup"><span data-stu-id="43167-165">Copy the generic example of the `ALTER MINING STRUCTURE` statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="43167-166">将</span><span class="sxs-lookup"><span data-stu-id="43167-166">Replace the following:</span></span>  
  
    ```  
    <mining structure name>   
    ```  
  
     <span data-ttu-id="43167-167">替换为：</span><span class="sxs-lookup"><span data-stu-id="43167-167">with:</span></span>  
  
    ```  
    Market Basket  
    ```  
  
4.  <span data-ttu-id="43167-168">将</span><span class="sxs-lookup"><span data-stu-id="43167-168">Replace the following:</span></span>  
  
    ```  
    <mining model name>   
    ```  
  
     <span data-ttu-id="43167-169">替换为：</span><span class="sxs-lookup"><span data-stu-id="43167-169">with:</span></span>  
  
    ```  
    [Modified Association]  
    ```  
  
5.  <span data-ttu-id="43167-170">将</span><span class="sxs-lookup"><span data-stu-id="43167-170">Replace the following:</span></span>  
  
    ```  
    <mining model columns>,  
    <table columns>  
    (  [<nested key column>],  
       <nested mining model columns> )  
    ```  
  
     <span data-ttu-id="43167-171">替换为：</span><span class="sxs-lookup"><span data-stu-id="43167-171">with:</span></span>  
  
    ```  
    OrderNumber,  
    [Products] PREDICT (  
            [Model]  
        )  
    ```  
  
     <span data-ttu-id="43167-172">在本例中，`[Products]` 表已被指定为可预测列。</span><span class="sxs-lookup"><span data-stu-id="43167-172">In this case, the `[Products]` table has been designated as the predictable column.</span></span> <span data-ttu-id="43167-173">此外，`[MODEL]` 列包含于列表中，原因在于它是嵌套表的键列。</span><span class="sxs-lookup"><span data-stu-id="43167-173">Also, the `[MODEL]` column is included in the list because it is the key column in the nested table.</span></span>  
  
6.  <span data-ttu-id="43167-174">将</span><span class="sxs-lookup"><span data-stu-id="43167-174">Replace the following:</span></span>  
  
    ```  
    USING <algorithm>( <algorithm parameters> )  
    ```  
  
     <span data-ttu-id="43167-175">替换为：</span><span class="sxs-lookup"><span data-stu-id="43167-175">with:</span></span>  
  
    ```  
    USING Microsoft_Association_Rules (Minimum_Probability = 0.1)  
    ```  
  
     <span data-ttu-id="43167-176">现在，结果语句应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="43167-176">The resulting statement should now be as follows:</span></span>  
  
    ```  
    ALTER MINING STRUCTURE [Market Basket]  
    ADD MINING MODEL [Modified Assocation]  
    (  
        OrderNumber,  
        [Products] PREDICT (  
            [Model]  
        )  
    )  
    USING Microsoft_Association_Rules (Minimum_Probability = 0.1)  
    ```  
  
7.  <span data-ttu-id="43167-177">在 "**文件**" 菜单上，单击 "**将 DMXQuery1 另存为**"。</span><span class="sxs-lookup"><span data-stu-id="43167-177">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
8.  <span data-ttu-id="43167-178">在 "**另存为**" 对话框中，浏览到相应的文件夹，并将该文件命名为 `Modified Association_Model.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="43167-178">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Modified Association_Model.dmx`.</span></span>  
  
9. <span data-ttu-id="43167-179">在工具栏上，单击 "**执行**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="43167-179">On the toolbar, click the **Execute** button.</span></span>  
  
 <span data-ttu-id="43167-180">在下一课中，您将处理市场篮挖掘结构及其关联的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="43167-180">In this next lesson you will process the Market Basket mining structure together with its associated mining models.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="43167-181">下一课</span><span class="sxs-lookup"><span data-stu-id="43167-181">Next Lesson</span></span>  
 [<span data-ttu-id="43167-182">第 3 课：处理市场篮挖掘结构</span><span class="sxs-lookup"><span data-stu-id="43167-182">Lesson 3: Processing the Market Basket Mining Structure</span></span>](../../2014/tutorials/lesson-3-processing-the-market-basket-mining-structure.md)  
  
  
