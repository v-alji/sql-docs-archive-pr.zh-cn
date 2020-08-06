---
title: " (MDX) 创建查询作用域的单元计算 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- WITH keyword
- query-scoped cell calculations [MDX]
ms.assetid: 45987daa-4400-41e9-add7-2428fd75709b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5a9c9d529bfeb26b959b2521e4ce3c3d7f10d082
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693534"
---
# <a name="creating-query-scoped-cell-calculations-mdx"></a><span data-ttu-id="ebca5-102">创建查询作用域的单元计算 (MDX)</span><span class="sxs-lookup"><span data-stu-id="ebca5-102">Creating Query-Scoped Cell Calculations (MDX)</span></span>
  <span data-ttu-id="ebca5-103">在多维表达式 (MDX) 中，可以使用 `WITH` 关键字描述查询上下文中的计算单元。</span><span class="sxs-lookup"><span data-stu-id="ebca5-103">You use the `WITH` keyword in Multidimensional Expressions (MDX) to describe calculated cells within the context of a query.</span></span> <span data-ttu-id="ebca5-104">`WITH` 关键字的语法如下：</span><span class="sxs-lookup"><span data-stu-id="ebca5-104">The `WITH` keyword has the following syntax:</span></span>  
  
```  
WITH CELL CALCULATION Cube_Name.CellCalc_Identifier  String_Expression  
```  
  
 <span data-ttu-id="ebca5-105">`CellCalc_Identifier` 值是计算单元的名称。</span><span class="sxs-lookup"><span data-stu-id="ebca5-105">The `CellCalc_Identifier` value is the name of the calculated cells.</span></span> <span data-ttu-id="ebca5-106">`String_Expression` 值包含一个一维正交 MDX 集表达式列表。</span><span class="sxs-lookup"><span data-stu-id="ebca5-106">The `String_Expression` value contains a list of orthogonal, single-dimensional MDX set expressions.</span></span> <span data-ttu-id="ebca5-107">这些集表达式中的每个表达式都必须解析为下表中列出的一个类别。</span><span class="sxs-lookup"><span data-stu-id="ebca5-107">Each of these set expressions must resolve to one of the categories listed in the following table.</span></span>  
  
|<span data-ttu-id="ebca5-108">类别</span><span class="sxs-lookup"><span data-stu-id="ebca5-108">Category</span></span>|<span data-ttu-id="ebca5-109">说明</span><span class="sxs-lookup"><span data-stu-id="ebca5-109">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="ebca5-110">空集</span><span class="sxs-lookup"><span data-stu-id="ebca5-110">Empty set</span></span>|<span data-ttu-id="ebca5-111">解析为空集的 MDX 集表达式。</span><span class="sxs-lookup"><span data-stu-id="ebca5-111">An MDX set expression that resolves into an empty set.</span></span> <span data-ttu-id="ebca5-112">在这种情况下，计算单元的作用域是整个多维数据集。</span><span class="sxs-lookup"><span data-stu-id="ebca5-112">In this case, the scope of the calculated cell is the whole cube.</span></span>|  
|<span data-ttu-id="ebca5-113">单个成员集</span><span class="sxs-lookup"><span data-stu-id="ebca5-113">Single member set</span></span>|<span data-ttu-id="ebca5-114">解析为单个成员的 MDX 集表达式。</span><span class="sxs-lookup"><span data-stu-id="ebca5-114">An MDX set expression that resolves into a single member.</span></span>|  
|<span data-ttu-id="ebca5-115">级别成员集</span><span class="sxs-lookup"><span data-stu-id="ebca5-115">Set of level members</span></span>|<span data-ttu-id="ebca5-116">解析为单个级别的成员的 MDX 集表达式。</span><span class="sxs-lookup"><span data-stu-id="ebca5-116">An MDX set expression that resolves into the members of a single level.</span></span> <span data-ttu-id="ebca5-117">此类集表达式的一个示例是*Level_Expression*。`Members`</span><span class="sxs-lookup"><span data-stu-id="ebca5-117">An example of such a set expression is the *Level_Expression*.`Members`</span></span> <span data-ttu-id="ebca5-118">MDX 函数。</span><span class="sxs-lookup"><span data-stu-id="ebca5-118">MDX function.</span></span> <span data-ttu-id="ebca5-119">若要包括计算成员，请使用*Level_Expression*。`AllMembers`</span><span class="sxs-lookup"><span data-stu-id="ebca5-119">To include calculated members, use the *Level_Expression*.`AllMembers`</span></span> <span data-ttu-id="ebca5-120">MDX 函数。</span><span class="sxs-lookup"><span data-stu-id="ebca5-120">MDX function.</span></span> <span data-ttu-id="ebca5-121">有关详细信息，请参阅 [AllMembers (MDX)](/sql/mdx/allmembers-mdx)。</span><span class="sxs-lookup"><span data-stu-id="ebca5-121">For more information, see [AllMembers &#40;MDX&#41;](/sql/mdx/allmembers-mdx).</span></span>|  
|<span data-ttu-id="ebca5-122">后代集</span><span class="sxs-lookup"><span data-stu-id="ebca5-122">Set of descendants</span></span>|<span data-ttu-id="ebca5-123">解析为指定成员的后代的 MDX 集表达式。</span><span class="sxs-lookup"><span data-stu-id="ebca5-123">An MDX set expression that resolves into the descendants of a specified member.</span></span> <span data-ttu-id="ebca5-124">此类集表达式的一个示例是 `Descendants` (*Member_Expression*， *Level_Expresion* *Desc_Flag*) MDX 函数。</span><span class="sxs-lookup"><span data-stu-id="ebca5-124">An example of such a set expression is the `Descendants`(*Member_Expression*, *Level_Expresion*, *Desc_Flag*) MDX function.</span></span> <span data-ttu-id="ebca5-125">有关详细信息，请参阅 [Descendants (MDX)](/sql/mdx/descendants-mdx)。</span><span class="sxs-lookup"><span data-stu-id="ebca5-125">For more information, see [Descendants &#40;MDX&#41;](/sql/mdx/descendants-mdx).</span></span>|  
  
 <span data-ttu-id="ebca5-126">如果 `String_Expression` 参数不描述维度，出于构造计算子多维数据集的目的，MDX 将假设包含所有成员。</span><span class="sxs-lookup"><span data-stu-id="ebca5-126">If the `String_Expression` argument does not describe a dimension, MDX assumes that all members are included for the purposes of constructing the calculation subcube.</span></span> <span data-ttu-id="ebca5-127">因此，如果 `String_Expression` 参数为 NULL，计算单元的定义将应用于整个多维数据集。</span><span class="sxs-lookup"><span data-stu-id="ebca5-127">Therefore, if the `String_Expression` argument is NULL, the calculated cells definition applies to the whole cube.</span></span>  
  
 <span data-ttu-id="ebca5-128">`MDX_Expression` 参数包含一个 MDX 表达式，该表达式的计算结果对于 `String_Expression` 参数中定义的所有单元均为某个单元值。</span><span class="sxs-lookup"><span data-stu-id="ebca5-128">The `MDX_Expression` argument contains an MDX expression that evaluates to a cell value for all the cells defined in the `String_Expression` argument.</span></span>  
  
## <a name="additional-considerations"></a><span data-ttu-id="ebca5-129">其他注意事项</span><span class="sxs-lookup"><span data-stu-id="ebca5-129">Additional Considerations</span></span>  
 <span data-ttu-id="ebca5-130">MDX 只处理一次 `CONDITION` 属性指定的计算条件。</span><span class="sxs-lookup"><span data-stu-id="ebca5-130">MDX processes the calculation condition, specified by the `CONDITION` property, only once.</span></span> <span data-ttu-id="ebca5-131">这种只处理一次的做法提高了计算多个计算单元定义的性能，尤其是计算在多维数据集传递间重叠的计算单元时的性能。</span><span class="sxs-lookup"><span data-stu-id="ebca5-131">This single processing provides increased performance for the evaluation of multiple calculated cells definitions, especially with overlapping calculated cells across cube passes.</span></span>  
  
 <span data-ttu-id="ebca5-132">何时发生这唯一的一次处理取决于计算单元定义的创建作用域：</span><span class="sxs-lookup"><span data-stu-id="ebca5-132">When this single processing occurs depends on the creation scope of the calculated cells definition:</span></span>  
  
-   <span data-ttu-id="ebca5-133">如果在全局作用域内作为多维数据集的一部分创建，MDX 将在处理多维数据集时处理计算条件。</span><span class="sxs-lookup"><span data-stu-id="ebca5-133">If created at global scope, as part of a cube, MDX process the calculation condition when the cube is processed.</span></span> <span data-ttu-id="ebca5-134">如果以任何方式在多维数据集中修改了单元，而且单元包括在计算单元定义的计算子多维数据集中，则在重新处理该多维数据集前，该计算条件可能不准确。</span><span class="sxs-lookup"><span data-stu-id="ebca5-134">If cells are modified in the cube in any way, and the cells are included in the calculation subcube of a calculated cells definition, the calculation condition may not be accurate until the cube is reprocessed.</span></span> <span data-ttu-id="ebca5-135">例如，写回中可能发生单元修改。</span><span class="sxs-lookup"><span data-stu-id="ebca5-135">Cell modification can occur from writebacks, for example.</span></span> <span data-ttu-id="ebca5-136">在重新处理该多维数据集时重新处理计算条件。</span><span class="sxs-lookup"><span data-stu-id="ebca5-136">The calculation condition is reprocessed when the cube is reprocessed.</span></span>  
  
-   <span data-ttu-id="ebca5-137">如果在会话作用域内创建，MDX 将在会话期间发出该语句时处理计算条件。</span><span class="sxs-lookup"><span data-stu-id="ebca5-137">If created at session scope, MDX process the calculation condition when the statement is issued during the session.</span></span> <span data-ttu-id="ebca5-138">与在全局作用域内创建的计算单元定义一样，如果修改了单元，计算条件对于计算单元定义可能不准确。</span><span class="sxs-lookup"><span data-stu-id="ebca5-138">As with calculated cells definitions created globally, if the cells are modified, the calculation condition may not be accurate for the calculated cells definition.</span></span>  
  
-   <span data-ttu-id="ebca5-139">如果在查询作用域内创建，MDX 将在运行查询时处理计算条件。</span><span class="sxs-lookup"><span data-stu-id="ebca5-139">If created at query scope, MDX processes the calculation condition when the query runs.</span></span> <span data-ttu-id="ebca5-140">尽管数据滞后问题微不足道，因为 MDX 查询执行的处理时间较短，但这里仍然存在单元修改问题。</span><span class="sxs-lookup"><span data-stu-id="ebca5-140">The cell modification issue applies here, also, although data latency issues are minimal because of the low processing time of MDX query execution.</span></span>  
  
 <span data-ttu-id="ebca5-141">另一方面，只要对多维数据集发出的 MDX 查询涉及计算单元定义中包含的单元，MDX 将就会处理计算公式。</span><span class="sxs-lookup"><span data-stu-id="ebca5-141">On the other hand, MDX processes the calculation formula whenever an MDX query is issued against the cube involving cells included in the calculated cells definition.</span></span> <span data-ttu-id="ebca5-142">此处理的发生不受创建作用域的限制。</span><span class="sxs-lookup"><span data-stu-id="ebca5-142">This processing occurs regardless of the creation scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebca5-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ebca5-143">See Also</span></span>  
 [<span data-ttu-id="ebca5-144">CREATE CELL CALCULATION 语句 (MDX)</span><span class="sxs-lookup"><span data-stu-id="ebca5-144">CREATE CELL CALCULATION Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-definition-create-cell-calculation)  
  
  
