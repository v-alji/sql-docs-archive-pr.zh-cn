---
title: "\"数据集筛选器或模型筛选器\" 对话框 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a9602174-b7e2-4e16-8ded-dfd8eb9264d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: afa796cd8cb23894c059deba411b3e1d6676e3b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690233"
---
# <a name="data-set-filter-or-model-filter-dialog-box"></a><span data-ttu-id="933d8-102">“数据集筛选器或模型筛选器”对话框</span><span class="sxs-lookup"><span data-stu-id="933d8-102">Data Set Filter or Model Filter Dialog Box</span></span>
  <span data-ttu-id="933d8-103">此对话框帮助您生成可应用于数据集的筛选器。</span><span class="sxs-lookup"><span data-stu-id="933d8-103">This dialog box helps you build the filters that you can apply to a data set.</span></span>  <span data-ttu-id="933d8-104">数据集可以是用于测试的外部数据集，也可以是挖掘模型的事例数据。</span><span class="sxs-lookup"><span data-stu-id="933d8-104">The data set can be an external data set used for testing, or the case data for a mining model.</span></span> <span data-ttu-id="933d8-105">根据筛选器是用于外部数据集还是用于挖掘模型，对话框的名称会发生更改。</span><span class="sxs-lookup"><span data-stu-id="933d8-105">The name of the dialog box changes depending on whether the filter is for an external data set or for a mining model.</span></span>  
  
 <span data-ttu-id="933d8-106">如果将筛选器应用于新数据集，则仅使用满足条件的数据集中的事例来评估数据挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="933d8-106">If you apply the filter to a new data set, the data mining model is evaluated by using only those cases in the data set that meet the conditions.</span></span> <span data-ttu-id="933d8-107">如果将筛选器应用于挖掘模型本身，则仅使用满足筛选条件的现有测试数据集中的事例来为该模型定型并对其进行测试。</span><span class="sxs-lookup"><span data-stu-id="933d8-107">If you apply the filter to the mining model itself, the model will be trained and tested by using only the cases in the existing test data set that meet the filter criteria.</span></span>  
  
-   <span data-ttu-id="933d8-108">可以从 **“挖掘准确性图表”** 设计器的 **“输入选择”** 选项卡中访问 **“数据集筛选器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="933d8-108">The **Data Set Filter** dialog box is available from the **Input Selection** tab of the **Mining Accuracy Chart** designer.</span></span>  
  
-   <span data-ttu-id="933d8-109">可从数据挖掘设计器的“挖掘模型”\*\*\*\* 选项卡中访问“模型筛选器”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="933d8-109">The **Model Filter** dialog box is available from the **Mining Models** tab of the Data Miningdesigner.</span></span>  
  
-   <span data-ttu-id="933d8-110">**“条件”** 网格包含可指定表或列名称、运算符和目标值的列。</span><span class="sxs-lookup"><span data-stu-id="933d8-110">The **Conditions** grid contains columns where you can specify a table or column name, an operator, and target values.</span></span> <span data-ttu-id="933d8-111">使用此网格时，实质上是创建 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="933d8-111">By using this grid you are essentially creating a WHERE clause.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="933d8-112"> 若要根据原始定型数据的子集测试准确性，可以添加用于将定型集定义为外部测试数据的数据源视图，然后在 **“数据集筛选器”** 网格中添加条件。</span><span class="sxs-lookup"><span data-stu-id="933d8-112">To test accuracy on a subset of the original training data, you can add the data source view that was used to define the training set as the external testing data, and then add conditions in the **Data Set Filter** grid.</span></span>  
  
 <span data-ttu-id="933d8-113">**有关详细信息，请参阅** [测试和验证（数据挖掘）](data-mining/testing-and-validation-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="933d8-113">**For more information:** [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="933d8-114">选项</span><span class="sxs-lookup"><span data-stu-id="933d8-114">Options</span></span>  
 <span data-ttu-id="933d8-115">**条件**</span><span class="sxs-lookup"><span data-stu-id="933d8-115">**Conditions**</span></span>  
 <span data-ttu-id="933d8-116">显示表名，后跟带有条件的列名。</span><span class="sxs-lookup"><span data-stu-id="933d8-116">Displays table names, followed by column names with conditions.</span></span>  
  
|<span data-ttu-id="933d8-117">值</span><span class="sxs-lookup"><span data-stu-id="933d8-117">Value</span></span>|<span data-ttu-id="933d8-118">说明</span><span class="sxs-lookup"><span data-stu-id="933d8-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="933d8-119">**And/Or**</span><span class="sxs-lookup"><span data-stu-id="933d8-119">**And/Or**</span></span>|<span data-ttu-id="933d8-120">选择运算符以联接多个条件。</span><span class="sxs-lookup"><span data-stu-id="933d8-120">Choose an operator to join multiple conditions.</span></span>|  
|<span data-ttu-id="933d8-121">**挖掘结构列**</span><span class="sxs-lookup"><span data-stu-id="933d8-121">**Mining Structure Column**</span></span>|<span data-ttu-id="933d8-122">单击此项可选择数据源，然后单击网格中的连续行可添加数据源中的列。</span><span class="sxs-lookup"><span data-stu-id="933d8-122">Click to select a data source, and then click successive lines in the grid to add columns from the data source.</span></span><br /><br /> <span data-ttu-id="933d8-123">网格中的第一行指定数据源视图。</span><span class="sxs-lookup"><span data-stu-id="933d8-123">The first line in the grid specifies the data source view.</span></span> <span data-ttu-id="933d8-124">选择数据源视图后， **“挖掘结构列”** 会显示一个表图标， **“值”** 字段显示为此数据源定义的所有条件的组合。</span><span class="sxs-lookup"><span data-stu-id="933d8-124">After you select a data source view, **Mining Structure Column** displays a table icon, and the **Value** field displays the combination of all criteria that you have defined for this data source.</span></span><br /><br /> <span data-ttu-id="933d8-125">选择数据源后， **“挖掘结构列”** 框提供一个显示该数据源中各个列的下拉列表。</span><span class="sxs-lookup"><span data-stu-id="933d8-125">After you have selected a data source, the **Mining Structure Column** box provides a dropdown list of individual columns in the data source.</span></span>|  
|<span data-ttu-id="933d8-126">**“运算符”**</span><span class="sxs-lookup"><span data-stu-id="933d8-126">**Operator**</span></span>|<span data-ttu-id="933d8-127">从列表中选择运算符。</span><span class="sxs-lookup"><span data-stu-id="933d8-127">Select an operator from the list.</span></span>|  
|<span data-ttu-id="933d8-128">**值**</span><span class="sxs-lookup"><span data-stu-id="933d8-128">**Value**</span></span>|<span data-ttu-id="933d8-129">对于表， **“值”** 字段显示应用于数据源的所有筛选器的组合。</span><span class="sxs-lookup"><span data-stu-id="933d8-129">For tables, the **Value** field shows the combination of all filters applied to the data source.</span></span> <span data-ttu-id="933d8-130">也可以单击文本框右侧的 "生成\*\* ( ..." ) **按钮，以打开 "**筛选器\*\*" 对话框并生成条件。</span><span class="sxs-lookup"><span data-stu-id="933d8-130">You can also click the build **(...)** button at the right of the text box to open the **Filter** dialog box and build a condition.</span></span>|  
  
 <span data-ttu-id="933d8-131">**表达式**</span><span class="sxs-lookup"><span data-stu-id="933d8-131">**Expression**</span></span>  
 <span data-ttu-id="933d8-132">显示使用网格生成的条件组。</span><span class="sxs-lookup"><span data-stu-id="933d8-132">Displays the set of criteria that you built by using the grid.</span></span>  
  
 <span data-ttu-id="933d8-133">**编辑查询**</span><span class="sxs-lookup"><span data-stu-id="933d8-133">**Edit Query**</span></span>  
 <span data-ttu-id="933d8-134">更改筛选器编辑模式，以便可以在“表达式”\*\*\*\* 文本框中直接键入筛选表达式。</span><span class="sxs-lookup"><span data-stu-id="933d8-134">Changes the filter editing mode so that you can type a filter expression directly in the **Expression** text box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="933d8-135">对筛选器表达式进行了手动更改后，即使在 "**输入选择**" 选项卡上的 "**筛选表达式**" 框中保存了该表达式，也不能返回网格编辑模式。如果希望使用网格生成表达式，则必须删除现有的筛选表达式并重新开始。</span><span class="sxs-lookup"><span data-stu-id="933d8-135">After you have made manual changes to the filter expression, you cannot return to grid edit mode, even after you have saved the expression in the **Filter Expression** box on the **Input Selection** tab. If you want to build an expression by using the grid, you must delete the existing filter expression and start over.</span></span>  
  
 <span data-ttu-id="933d8-136">**恢复查询编辑**</span><span class="sxs-lookup"><span data-stu-id="933d8-136">**Revert Query Edits**</span></span>  
 <span data-ttu-id="933d8-137">使网格还原为先前的状态，并取消对筛选表达式所做的任何更改。</span><span class="sxs-lookup"><span data-stu-id="933d8-137">Restores the grid to its previous state and cancels any changes that you made to the filter expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="933d8-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="933d8-138">See Also</span></span>  
 <span data-ttu-id="933d8-139">[测试和验证任务以及操作方法 &#40;数据挖掘&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="933d8-139">[Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span></span>  
 [<span data-ttu-id="933d8-140">挖掘准确性图表设计器 &#40;数据挖掘&#41;</span><span class="sxs-lookup"><span data-stu-id="933d8-140">Mining Accuracy Chart Designer &#40;Data Mining&#41;</span></span>](mining-accuracy-chart-designer-data-mining.md)  
  
  
