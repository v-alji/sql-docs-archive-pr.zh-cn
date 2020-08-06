---
title: " (SSAS 表格) 的计算列 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e1011278-556d-4984-b01d-a37f8a33b304
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5d77b36ee3327d1b9e0d31ac97e5dbe135093a63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682386"
---
# <a name="calculated-columns-ssas-tabular"></a><span data-ttu-id="9f46f-102">计算列（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="9f46f-102">Calculated Columns (SSAS Tabular)</span></span>
  <span data-ttu-id="9f46f-103">在表格模型中，通过计算列可以将新数据添加到您的模型。</span><span class="sxs-lookup"><span data-stu-id="9f46f-103">Calculated columns, in tabular models, allow you to add new data to your model.</span></span> <span data-ttu-id="9f46f-104">您可以创建定义列的行级值的 DAX 公式，而不是在列中粘贴或导入值。</span><span class="sxs-lookup"><span data-stu-id="9f46f-104">Instead of pasting or importing values into the column, you create a DAX formula that defines the column's row level values.</span></span> <span data-ttu-id="9f46f-105">然后，计算列可用于报表、数据透视表或数据透视图中，您可以像使用任何其他数据列一样使用计算列。</span><span class="sxs-lookup"><span data-stu-id="9f46f-105">The calculated column can then be used in a report, PivotTable, or PivotChart as would any other column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f46f-106">在 DirectQuery 模式下，表格模型不支持计算列。</span><span class="sxs-lookup"><span data-stu-id="9f46f-106">Calculated columns are not supported for tabular models in DirectQuery mode.</span></span> <span data-ttu-id="9f46f-107">有关详细信息，请参阅 [DirectQuery 模式（SSAS 表格）](directquery-mode-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="9f46f-107">For more information, see [DirectQuery Mode &#40;SSAS Tabular&#41;](directquery-mode-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="9f46f-108">本主题的内容：</span><span class="sxs-lookup"><span data-stu-id="9f46f-108">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="9f46f-109">优点</span><span class="sxs-lookup"><span data-stu-id="9f46f-109">Benefits</span></span>](#bkmk_understanding)  
  
-   [<span data-ttu-id="9f46f-110">命名计算列</span><span class="sxs-lookup"><span data-stu-id="9f46f-110">Naming a Calculated Column</span></span>](#bkmk_naming)  
  
-   [<span data-ttu-id="9f46f-111">计算列的性能</span><span class="sxs-lookup"><span data-stu-id="9f46f-111">Performance of Calculated Columns</span></span>](#bkmk_perf)  
  
-   [<span data-ttu-id="9f46f-112">相关任务</span><span class="sxs-lookup"><span data-stu-id="9f46f-112">Related Tasks</span></span>](#bkmk_rel_tasks)  
  
##  <a name="benefits"></a><a name="bkmk_understanding"></a> <span data-ttu-id="9f46f-113">优势</span><span class="sxs-lookup"><span data-stu-id="9f46f-113">Benefits</span></span>  
 <span data-ttu-id="9f46f-114">计算列中的公式非常类似于 Excel 中的公式。</span><span class="sxs-lookup"><span data-stu-id="9f46f-114">Formulas in calculated columns are much like formulas in Excel.</span></span> <span data-ttu-id="9f46f-115">但与 Excel 不同，您不能为表中的不同行创建不同的公式；而是 DAX 公式自动应用于整个列。</span><span class="sxs-lookup"><span data-stu-id="9f46f-115">Unlike Excel, however, you cannot create different formulas for different rows in a table; instead, the DAX formula is automatically applied to the entire column.</span></span>  
  
 <span data-ttu-id="9f46f-116">在某个列包含公式时，将为每一行都计算值。</span><span class="sxs-lookup"><span data-stu-id="9f46f-116">When a column contains a formula, the value is computed for each row.</span></span> <span data-ttu-id="9f46f-117">在您输入有效公式时，将立即为列计算结果。</span><span class="sxs-lookup"><span data-stu-id="9f46f-117">The results are calculated for the column when you enter a valid formula.</span></span> <span data-ttu-id="9f46f-118">在需要时（例如，在刷新基础数据时），将重新计算列值。</span><span class="sxs-lookup"><span data-stu-id="9f46f-118">Column values are then recalculated as necessary, such as when the underlying data is refreshed.</span></span>  
  
 <span data-ttu-id="9f46f-119">您可以创建基于度量值和其他计算列的计算列。</span><span class="sxs-lookup"><span data-stu-id="9f46f-119">You can create calculated columns that are based on measures and other calculated columns.</span></span> <span data-ttu-id="9f46f-120">例如，您可以创建一个计算列以便从文本字符串中提取一个数字，然后在其他计算列中使用该数字。</span><span class="sxs-lookup"><span data-stu-id="9f46f-120">For example, you might create one calculated column to extract a number from a string of text, and then use that number in another calculated column.</span></span>  
  
 <span data-ttu-id="9f46f-121">计算列基于您已在现有表中具有的数据，或者通过使用 DAX 公式创建。</span><span class="sxs-lookup"><span data-stu-id="9f46f-121">A calculated column is based on data that you already have in an existing table, or created by using a DAX formula.</span></span> <span data-ttu-id="9f46f-122">例如，您可以选择串联值、执行添加、提取子字符串或比较其他字段中的值。</span><span class="sxs-lookup"><span data-stu-id="9f46f-122">For example, you might choose to concatenate values, perform addition, extract substrings, or compare the values in other fields.</span></span> <span data-ttu-id="9f46f-123">若要添加某一计算列，您必须在模型中具有至少一个表。</span><span class="sxs-lookup"><span data-stu-id="9f46f-123">To add a calculated column, you must have at least one table in your model.</span></span>  
  
 <span data-ttu-id="9f46f-124">此示例演示计算列中的一个简单的公式：</span><span class="sxs-lookup"><span data-stu-id="9f46f-124">This example demonstrates a simple formula in a calculated column:</span></span>  
  
```  
=EOMONTH([StartDate],0])  
  
```  
  
 <span data-ttu-id="9f46f-125">此公式将从 StartDate 列中提取月份。</span><span class="sxs-lookup"><span data-stu-id="9f46f-125">This formula extracts the month from the StartDate column.</span></span> <span data-ttu-id="9f46f-126">它然后计算表中每一行的月末值。</span><span class="sxs-lookup"><span data-stu-id="9f46f-126">It then calculates the end of the month value for each row in the table.</span></span> <span data-ttu-id="9f46f-127">第二个参数指定 StartDate 中该月前或该月后的月份数；在这个例子中，0 意味着同一月。</span><span class="sxs-lookup"><span data-stu-id="9f46f-127">The second parameter specifies the number of months before or after the month in StartDate; in this case, 0 means the same month.</span></span> <span data-ttu-id="9f46f-128">例如，如果 StartDate 列中的值为 6/1/2001，则计算列中的值将是 6/30/2001。</span><span class="sxs-lookup"><span data-stu-id="9f46f-128">For example, if the value in the StartDate column is 6/1/2001, the value in the calculated column will be 6/30/2001.</span></span>  
  
##  <a name="naming-a-calculated-column"></a><a name="bkmk_naming"></a><span data-ttu-id="9f46f-129">命名计算列</span><span class="sxs-lookup"><span data-stu-id="9f46f-129">Naming a Calculated Column</span></span>  
 <span data-ttu-id="9f46f-130">默认情况下，新的计算列将添加到表中其他列的右侧，并且自动向该列分配默认名称 **CalculatedColumn1**、 **CalculatedColumn2**，依此类推。</span><span class="sxs-lookup"><span data-stu-id="9f46f-130">By default, new calculated columns are added to the right of other columns in a table, and the column is automatically assigned the default name of **CalculatedColumn1**, **CalculatedColumn2**, and so forth.</span></span> <span data-ttu-id="9f46f-131">您也可以右键单击某一列，然后单击“插入列”以便在两个现有列之间创建一个新列。</span><span class="sxs-lookup"><span data-stu-id="9f46f-131">You can also right click a column, and then click Insert Column to create a new column between two existing columns.</span></span> <span data-ttu-id="9f46f-132">您可以通过单击和拖动在同一个表中重新排列列，并且可以在创建列后重命名列；但是，您应该知道针对计算列的更改的以下限制：</span><span class="sxs-lookup"><span data-stu-id="9f46f-132">You can rearrange columns within the same table by clicking and dragging, and you can rename columns after they are created; however, you should be aware of the following restrictions on changes to calculated columns:</span></span>  
  
-   <span data-ttu-id="9f46f-133">每个列名称在表中都必须唯一。</span><span class="sxs-lookup"><span data-stu-id="9f46f-133">Each column name must be unique within a table.</span></span>  
  
-   <span data-ttu-id="9f46f-134">避免使用已用于同一模型中的度量值的名称。</span><span class="sxs-lookup"><span data-stu-id="9f46f-134">Avoid names that have already been used for measures within the same model.</span></span> <span data-ttu-id="9f46f-135">尽管度量值和计算列可以具有相同的名称，但是如果名称不唯一，可能会导致计算错误。</span><span class="sxs-lookup"><span data-stu-id="9f46f-135">Although it is possible for a measure and a calculated column to have the same name, if names are not unique you can get calculation errors.</span></span> <span data-ttu-id="9f46f-136">为了避免无意中调用度量值，在引用列时请始终使用完全限定的列引用。</span><span class="sxs-lookup"><span data-stu-id="9f46f-136">To avoid accidentally invoking a measure, when referring to a column always use a fully qualified column reference.</span></span>  
  
-   <span data-ttu-id="9f46f-137">当您重命名计算列时，必须手动更新依赖于该列的所有公式。</span><span class="sxs-lookup"><span data-stu-id="9f46f-137">When you rename a calculated column, any formulas that rely on the column must be updated manually.</span></span> <span data-ttu-id="9f46f-138">如果您没有处于手动更新模式，则更新公式结果将自动发生。</span><span class="sxs-lookup"><span data-stu-id="9f46f-138">Unless you are in manual update mode, updating the results of formulas takes place automatically.</span></span> <span data-ttu-id="9f46f-139">但是，此操作可能要花一些时间。</span><span class="sxs-lookup"><span data-stu-id="9f46f-139">However, this operation might take some time.</span></span>  
  
-   <span data-ttu-id="9f46f-140">有一些字符不能用于列名中。</span><span class="sxs-lookup"><span data-stu-id="9f46f-140">There are some characters that cannot be used within the names of columns.</span></span> <span data-ttu-id="9f46f-141">有关详细信息，请参阅 [PowerPivot 的 DAX 语法规范](/dax/dax-syntax-reference)中的“命名要求”。</span><span class="sxs-lookup"><span data-stu-id="9f46f-141">For more information, see "Naming Requirements" in [DAX Syntax Specification for PowerPivot](/dax/dax-syntax-reference).</span></span>  
  
##  <a name="performance-of-calculated-columns"></a><a name="bkmk_perf"></a><span data-ttu-id="9f46f-142">计算列的性能</span><span class="sxs-lookup"><span data-stu-id="9f46f-142">Performance of Calculated Columns</span></span>  
 <span data-ttu-id="9f46f-143">与用于度量值的公式相比，用于计算列的公式可能会消耗更多的资源。</span><span class="sxs-lookup"><span data-stu-id="9f46f-143">The formula for a calculated column can be more resource-intensive than the formula used for a measure.</span></span> <span data-ttu-id="9f46f-144">原因之一是：计算列的结果始终是为表中的每一行计算的，而度量值仅是为报表、数据透视表或数据透视图中使用的筛选器定义的单元计算的。</span><span class="sxs-lookup"><span data-stu-id="9f46f-144">One reason is that the result for a calculated column is always calculated for each row in a table, whereas a measure is only calculated for the cells defined by the filter used in a report, PivotTable, or PivotChart.</span></span> <span data-ttu-id="9f46f-145">例如，某个具有 100 万行的表将始终具有含 100 万个结果的计算列，并且对性能具有相应影响。</span><span class="sxs-lookup"><span data-stu-id="9f46f-145">For example, a table with a million rows will always have a calculated column with a million results, and a corresponding effect on performance.</span></span> <span data-ttu-id="9f46f-146">但是，数据透视表通常会通过应用行和列标题对数据进行筛选；因此，仅为数据透视表的每个单元中的数据子集计算度量值。</span><span class="sxs-lookup"><span data-stu-id="9f46f-146">However, a PivotTable generally filters data by applying row and column headings; therefore, a measure is calculated only for the subset of data in each cell of the PivotTable.</span></span>  
  
 <span data-ttu-id="9f46f-147">一个公式对于在公式中引用的对象（例如其他列或计算值的表达式）具有依赖关系。</span><span class="sxs-lookup"><span data-stu-id="9f46f-147">A formula has dependencies on the objects that are referenced in the formula, such as other columns or expressions that evaluate values.</span></span> <span data-ttu-id="9f46f-148">例如，对于基于其他列的计算列，或对于包含引用列的表达式的计算，只有在计算这些相关列之后，才会计算它们。</span><span class="sxs-lookup"><span data-stu-id="9f46f-148">For example, a calculated column that is based on another column, or a calculation that contains an expression with a column reference, cannot be evaluated until the other column is evaluated.</span></span> <span data-ttu-id="9f46f-149">默认情况下，在工作簿中启用自动刷新；因此，在更新值和刷新公式时，所有此类依赖项都可能会影响性能。</span><span class="sxs-lookup"><span data-stu-id="9f46f-149">By default, automatic refresh is enabled in workbooks; therefore, all such dependencies can affect performance while values are updated and formulas refreshed.</span></span>  
  
 <span data-ttu-id="9f46f-150">为了避免在创建计算列时出现性能问题，请遵循下列指导原则：</span><span class="sxs-lookup"><span data-stu-id="9f46f-150">To avoid performance issues when you create calculated columns, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="9f46f-151">不要创建包含许多复杂依赖关系的单个公式，而应分步创建多个公式并将结果保存到列中，这样您就能够验证结果并评估性能。</span><span class="sxs-lookup"><span data-stu-id="9f46f-151">Rather than create a single formula that contains many complex dependencies, create the formulas in steps, with results saved to columns, so that you can validate the results and assess performance.</span></span>  
  
-   <span data-ttu-id="9f46f-152">修改数据通常要求重新计算计算列。</span><span class="sxs-lookup"><span data-stu-id="9f46f-152">Modification of data will often require that calculated columns be recalculated.</span></span> <span data-ttu-id="9f46f-153">可以通过将重新计算模式设置为手动来避免上述情况；但是，如果计算列中的任何值不正确，则该列将灰显，直到您刷新并重新计算数据。</span><span class="sxs-lookup"><span data-stu-id="9f46f-153">You can prevent this by setting the recalculation mode to manual; however, if any values in the calculated column are incorrect the column will be grayed out until you refresh and recalculate the data.</span></span>  
  
-   <span data-ttu-id="9f46f-154">如果更改或删除表之间的关系，则使用这些表中的列的公式将会失效。</span><span class="sxs-lookup"><span data-stu-id="9f46f-154">If you change or delete relationships between tables, formulas that use columns in those tables will become invalid.</span></span>  
  
-   <span data-ttu-id="9f46f-155">如果创建了一个包含循环或自引用依赖关系的公式，将会发生错误。</span><span class="sxs-lookup"><span data-stu-id="9f46f-155">If you create a formula that contains a circular or self-referencing dependency, an error will occur.</span></span>  
  
##  <a name="related-tasks"></a><a name="bkmk_rel_tasks"></a> <span data-ttu-id="9f46f-156">相关任务</span><span class="sxs-lookup"><span data-stu-id="9f46f-156">Related Tasks</span></span>  
  
|<span data-ttu-id="9f46f-157">主题</span><span class="sxs-lookup"><span data-stu-id="9f46f-157">Topic</span></span>|<span data-ttu-id="9f46f-158">说明</span><span class="sxs-lookup"><span data-stu-id="9f46f-158">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="9f46f-159">创建计算列（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="9f46f-159">Create a Calculated Column &#40;SSAS Tabular&#41;</span></span>](ssas-calculated-columns-create-a-calculated-column.md)|<span data-ttu-id="9f46f-160">本主题中的任务描述了如何向表中添加新的计算列。</span><span class="sxs-lookup"><span data-stu-id="9f46f-160">Tasks in this topic describe how to add a new calculated column to a table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9f46f-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9f46f-161">See Also</span></span>  
 <span data-ttu-id="9f46f-162">[&#40;SSAS 表格&#41;的表和列](tables-and-columns-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="9f46f-162">[Tables and Columns &#40;SSAS Tabular&#41;](tables-and-columns-ssas-tabular.md) </span></span>  
 <span data-ttu-id="9f46f-163">[&#40;SSAS 表格&#41;度量值](measures-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="9f46f-163">[Measures &#40;SSAS Tabular&#41;](measures-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="9f46f-164">计算（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="9f46f-164">Calculations &#40;SSAS Tabular&#41;</span></span>](calculations-ssas-tabular.md)  
  
  
