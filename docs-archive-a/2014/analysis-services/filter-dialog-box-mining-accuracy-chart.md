---
title: "\"筛选器\" 对话框 (挖掘准确性图表) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 71e884a9-7ec4-4459-a4c4-87f6c796d478
author: minewiskan
ms.author: owend
ms.openlocfilehash: dcdfb7cd7b425c3f8c4711e8b1812afc12898e1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588746"
---
# <a name="filter-dialog-box-mining-accuracy-chart"></a><span data-ttu-id="20372-102">“筛选器”对话框（挖掘准确性图表）</span><span class="sxs-lookup"><span data-stu-id="20372-102">Filter Dialog Box (Mining Accuracy Chart)</span></span>
  <span data-ttu-id="20372-103">**“筛选器”** 对话框有助于生成可应用于数据集的条件。</span><span class="sxs-lookup"><span data-stu-id="20372-103">The **Filter** dialog box helps you build conditions that you can apply to a data set.</span></span> <span data-ttu-id="20372-104">数据集可以是用于测试的外部数据集，也可以是定型挖掘模型所使用的事例数据。</span><span class="sxs-lookup"><span data-stu-id="20372-104">The data set can be an external data set used for testing, or the case data used to train a mining model.</span></span> <span data-ttu-id="20372-105">此对话框有助于生成可在 **“数据集筛选器”** 对话框或 **“模型筛选器”** 对话框中作为较复杂筛选条件的一部分进行保存的条件。</span><span class="sxs-lookup"><span data-stu-id="20372-105">This dialog box helps you build criteria that you can save as part of more complex filter criteria in either the **Data Set Filter** dialog box or the **Model Filter** dialog box.</span></span>  
  
-   <span data-ttu-id="20372-106">可以从 **“挖掘准确性图表”** 设计器的 **“输入选择”** 选项卡中访问 **“数据集筛选器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="20372-106">The **Data Set Filter** dialog box is available from the **Input Selection** tab of the **Mining Accuracy Chart** designer.</span></span>  
  
-   <span data-ttu-id="20372-107">可以从数据挖掘设计器的 **“挖掘模型”** 选项卡中访问 **“模型筛选器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="20372-107">The **Model Filter** dialog box is available from the **Mining Models** tab of the Data Mining designer.</span></span>  
  
 <span data-ttu-id="20372-108">如果要将筛选器应用于挖掘模型，则首先使用 **“模型筛选器”** 对话框选择一个表。</span><span class="sxs-lookup"><span data-stu-id="20372-108">If you are applying a filter to a mining model, first you use the **Model Filter** dialog box to choose a table.</span></span> <span data-ttu-id="20372-109">然后，可以使用 **“筛选器”** 对话框生成仅应用于该表的条件。</span><span class="sxs-lookup"><span data-stu-id="20372-109">Then, you can use the **Filter** dialog box to build conditions that apply only to that table.</span></span>  
  
 <span data-ttu-id="20372-110">如果要创建应用于外部测试数据集的筛选器，则首先使用 **“数据集筛选器”** 对话框从数据源视图的表列表中选择一个表。</span><span class="sxs-lookup"><span data-stu-id="20372-110">If you are creating a filter to apply to an external test data set, first you use the **Data Set Filter** dialog box to choose a table from the list of tables in a data source view.</span></span> <span data-ttu-id="20372-111">然后，使用 **“筛选器”** 对话框生成仅应用于该表的条件。</span><span class="sxs-lookup"><span data-stu-id="20372-111">Then, you use the **Filter** dialog box to build conditions that apply only to that table.</span></span>  
  
 <span data-ttu-id="20372-112">创建一组应用于单个表的条件后， [!INCLUDE[clickOK](../includes/clickok-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="20372-112">After you have created a set of conditions that apply to a single table, [!INCLUDE[clickOK](../includes/clickok-md.md)].</span></span> <span data-ttu-id="20372-113">在 **“筛选器”** 对话框中所做的更改会自动添加到父对话框 **“数据集筛选器”** 或 **“模型筛选器”** 中的筛选表达式。</span><span class="sxs-lookup"><span data-stu-id="20372-113">The changes that you made in the **Filter** dialog box are automatically added to the filter expression in the parent dialog box, **Data Set Filter** or **Model Filter**.</span></span>  
  
 <span data-ttu-id="20372-114">如果将筛选器应用于新数据集，则现有数据挖掘模型将仅用于评估数据集中满足条件的事例。</span><span class="sxs-lookup"><span data-stu-id="20372-114">If you apply the filter to the new data set, the existing data mining model is used to evaluate only those cases in the data set that meet the conditions.</span></span> <span data-ttu-id="20372-115">但如果将筛选器应用于挖掘模型本身，则仅针对挖掘模型中满足这些条件的事例评估模型的准确性。</span><span class="sxs-lookup"><span data-stu-id="20372-115">However, if you apply the filter to the mining model itself, the accuracy of the model is assessed for only those cases within the mining model that meet those criteria.</span></span>  
  
 <span data-ttu-id="20372-116">**有关详细信息，请参阅** [测试和验证（数据挖掘）](data-mining/testing-and-validation-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="20372-116">**For more information:** [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="20372-117">选项</span><span class="sxs-lookup"><span data-stu-id="20372-117">Options</span></span>  
 <span data-ttu-id="20372-118">**条件**</span><span class="sxs-lookup"><span data-stu-id="20372-118">**Conditions**</span></span>  
 <span data-ttu-id="20372-119">一个网格，其中包含为在“数据集筛选器”\*\*\*\* 对话框中选择的表中的列指定条件的列。</span><span class="sxs-lookup"><span data-stu-id="20372-119">A grid that contains columns where you specify conditions on columns from the table that you selected in the **Data Set Filter** dialog box.</span></span>  
  
|<span data-ttu-id="20372-120">值</span><span class="sxs-lookup"><span data-stu-id="20372-120">Value</span></span>|<span data-ttu-id="20372-121">说明</span><span class="sxs-lookup"><span data-stu-id="20372-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="20372-122">**And/Or**</span><span class="sxs-lookup"><span data-stu-id="20372-122">**And/Or**</span></span>|<span data-ttu-id="20372-123">单击此项可指定是将 AND 运算符还是 OR 运算符应用于此行中的条件。</span><span class="sxs-lookup"><span data-stu-id="20372-123">Click to specify whether to apply the AND operator or the OR operator to the condition on this line.</span></span> <span data-ttu-id="20372-124">仅在从 **“挖掘结构列”** 列表中选择一列后，这些值才可用。</span><span class="sxs-lookup"><span data-stu-id="20372-124">These values become available only after you have selected a column from the **Mining Structure Column** list.</span></span>|  
|<span data-ttu-id="20372-125">**挖掘结构列**</span><span class="sxs-lookup"><span data-stu-id="20372-125">**Mining Structure Column**</span></span>|<span data-ttu-id="20372-126">单击此项可从表中包含的列的列表中选择一列，该表是从 **“数据集筛选器”** 对话框的数据源中选择的。</span><span class="sxs-lookup"><span data-stu-id="20372-126">Click to select a column from the list of the columns contained in the table that you selected from the data source in the **Data Set Filter** dialog box.</span></span>|  
|<span data-ttu-id="20372-127">**“运算符”**</span><span class="sxs-lookup"><span data-stu-id="20372-127">**Operator**</span></span>|<span data-ttu-id="20372-128">从列表中选择运算符。</span><span class="sxs-lookup"><span data-stu-id="20372-128">Select an operator from the list.</span></span> <span data-ttu-id="20372-129">可用的运算符取决于列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="20372-129">The operators that are available depend on the data type of the column.</span></span><br /><br /> <span data-ttu-id="20372-130">如果列包含离散值，则只有以下运算符可用：</span><span class="sxs-lookup"><span data-stu-id="20372-130">If the column contains discrete values, only the following operators are available:</span></span><br /><br /> <span data-ttu-id="20372-131">=（等于）、<>（不等于）、IS NOT NULL、IS NULL。</span><span class="sxs-lookup"><span data-stu-id="20372-131">= (equal to), <> (not equal to), IS NOT NULL, IS NULL.</span></span><br /><br /> <span data-ttu-id="20372-132">如果列包含连续值，则还支持进行大于和小于运算的运算符。</span><span class="sxs-lookup"><span data-stu-id="20372-132">If the column contains continuous values, operators for greater than and less than operations are also supported.</span></span>|  
|<span data-ttu-id="20372-133">**值**</span><span class="sxs-lookup"><span data-stu-id="20372-133">**Value**</span></span>|<span data-ttu-id="20372-134">键入要用作条件的值。</span><span class="sxs-lookup"><span data-stu-id="20372-134">Type a value to use as a condition.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="20372-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="20372-135">See Also</span></span>  
 <span data-ttu-id="20372-136">[测试和验证任务以及操作方法 &#40;数据挖掘&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="20372-136">[Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span></span>  
 [<span data-ttu-id="20372-137">挖掘准确性图表设计器 &#40;数据挖掘&#41;</span><span class="sxs-lookup"><span data-stu-id="20372-137">Mining Accuracy Chart Designer &#40;Data Mining&#41;</span></span>](mining-accuracy-chart-designer-data-mining.md)  
  
  
