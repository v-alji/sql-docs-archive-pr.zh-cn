---
title: Multilookup 函数（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1fec079e-33b3-4e4d-92b3-6b4d06a49a77
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2f2aff7a2a39e1a072cf4b05f0a04e12ced529af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586406"
---
# <a name="multilookup-function-report-builder-and-ssrs"></a><span data-ttu-id="53a17-102">Multilookup 函数（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="53a17-102">Multilookup Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="53a17-103">从包含名称/值对的数据集返回指定名称集的一组第一个匹配值。</span><span class="sxs-lookup"><span data-stu-id="53a17-103">Returns the set of first-match values for the specified set of names from a dataset that contains name/value pairs.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="53a17-104">语法</span><span class="sxs-lookup"><span data-stu-id="53a17-104">Syntax</span></span>  
  
```  
  
Multilookup(source_expression, destination_expression, result_expression, dataset)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53a17-105">parameters</span><span class="sxs-lookup"><span data-stu-id="53a17-105">Parameters</span></span>  
 <span data-ttu-id="53a17-106">*source_expression*</span><span class="sxs-lookup"><span data-stu-id="53a17-106">*source_expression*</span></span>  
 <span data-ttu-id="53a17-107">(`VariantArray`) 在当前作用域中计算结果并指定要查找的名称或键的集合的表达式。</span><span class="sxs-lookup"><span data-stu-id="53a17-107">(`VariantArray`) An expression that is evaluated in the current scope and that specifies the set of names or keys to look up.</span></span> <span data-ttu-id="53a17-108">例如，对于多值参数， `=Parameters!IDs.value`。</span><span class="sxs-lookup"><span data-stu-id="53a17-108">For example, for a multivalue parameter, `=Parameters!IDs.value`.</span></span>  
  
 <span data-ttu-id="53a17-109">*destination_expression*</span><span class="sxs-lookup"><span data-stu-id="53a17-109">*destination_expression*</span></span>  
 <span data-ttu-id="53a17-110">(`Variant`) 针对数据集中的每行计算结果并指定要匹配的名称或键的表达式。</span><span class="sxs-lookup"><span data-stu-id="53a17-110">(`Variant`) An expression that is evaluated for each row in a dataset and that specifies the name or key to match on.</span></span> <span data-ttu-id="53a17-111">例如，`=Fields!ID.Value` 。</span><span class="sxs-lookup"><span data-stu-id="53a17-111">For example, `=Fields!ID.Value`.</span></span>  
  
 <span data-ttu-id="53a17-112">*result_expression*</span><span class="sxs-lookup"><span data-stu-id="53a17-112">*result_expression*</span></span>  
 <span data-ttu-id="53a17-113"> (`Variant`) 为 dataset 中的行计算的表达式，其中*source_expression*  =  *destination_expression*，并指定要检索的值。</span><span class="sxs-lookup"><span data-stu-id="53a17-113">(`Variant`) An expression that is evaluated for the row in the dataset where *source_expression* = *destination_expression*, and that specifies the value to retrieve.</span></span> <span data-ttu-id="53a17-114">例如，`=Fields!Name.Value` 。</span><span class="sxs-lookup"><span data-stu-id="53a17-114">For example, `=Fields!Name.Value`.</span></span>  
  
 <span data-ttu-id="53a17-115">*数据集 (dataset)*</span><span class="sxs-lookup"><span data-stu-id="53a17-115">*dataset*</span></span>  
 <span data-ttu-id="53a17-116">指定报表中数据集的名称的常量。</span><span class="sxs-lookup"><span data-stu-id="53a17-116">A constant that specifies the name of a dataset in the report.</span></span> <span data-ttu-id="53a17-117">例如，“Colors”。</span><span class="sxs-lookup"><span data-stu-id="53a17-117">For example, "Colors".</span></span>  
  
## <a name="return"></a><span data-ttu-id="53a17-118">返回</span><span class="sxs-lookup"><span data-stu-id="53a17-118">Return</span></span>  
 <span data-ttu-id="53a17-119">返回 `VariantArray`，如果没有匹配项，则返回 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="53a17-119">Returns a `VariantArray`, or `Nothing` if there is no match.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53a17-120">备注</span><span class="sxs-lookup"><span data-stu-id="53a17-120">Remarks</span></span>  
 <span data-ttu-id="53a17-121">使用 `Multilookup` 从名称-值对（每对具有 1 对 1 的关系）的数据集中检索一组值。</span><span class="sxs-lookup"><span data-stu-id="53a17-121">Use `Multilookup` to retrieve a set of values from a dataset for name-value pairs where each pair has a 1-to-1 relationship.</span></span> <span data-ttu-id="53a17-122">`MultiLookup` 等同于对一组名称或键调用 `Lookup`。</span><span class="sxs-lookup"><span data-stu-id="53a17-122">`MultiLookup` is the equivalent of calling `Lookup` for a set of names or keys.</span></span> <span data-ttu-id="53a17-123">例如，对于基于主键标识符的多值参数，可以在表中使用文本框表达式中的 `Multilookup` 来检索未绑定到该参数或该表的数据集中的相关值。</span><span class="sxs-lookup"><span data-stu-id="53a17-123">For example, for a multivalue parameter that is based on primary key identifiers, you can use `Multilookup` in an expression in a text box in a table to retrieve associated values from a dataset that is not bound to the parameter or to the table.</span></span>  
  
 <span data-ttu-id="53a17-124">`Multilookup` 执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="53a17-124">`Multilookup` does the following:</span></span>  
  
-   <span data-ttu-id="53a17-125">计算当前作用域中源表达式的结果并生成变体对象的数组。</span><span class="sxs-lookup"><span data-stu-id="53a17-125">Evaluates the source expression in the current scope and generates an array of variant objects.</span></span>  
  
-   <span data-ttu-id="53a17-126">对于数组中的每个对象，调用 [Lookup 函数（报表生成器和 SSRS）](report-builder-functions-lookup-function.md)并向返回数组添加结果。</span><span class="sxs-lookup"><span data-stu-id="53a17-126">For each object in the array, calls [Lookup Function &#40;Report Builder and SSRS&#41;](report-builder-functions-lookup-function.md) and adds the result to the return array.</span></span>  
  
-   <span data-ttu-id="53a17-127">返回结果集。</span><span class="sxs-lookup"><span data-stu-id="53a17-127">Returns the set of results.</span></span>  
  
 <span data-ttu-id="53a17-128">若要从具有指定名称的名称/值对（具有 1 对 1 的关系）的数据集中检索单个值，请使用 [Lookup 函数（报表生成器和 SSRS）](report-builder-functions-lookup-function.md)。</span><span class="sxs-lookup"><span data-stu-id="53a17-128">To retrieve a single value from a dataset with name-value pairs for a specified name where there is a 1-to-1 relationship, use [Lookup Function &#40;Report Builder and SSRS&#41;](report-builder-functions-lookup-function.md).</span></span> <span data-ttu-id="53a17-129">若要从具有某名称的名称-值对（具有 1 对多的关系）的数据集中检索多个值，请使用 [LookupSet 函数（报表生成器和 SSRS）](report-builder-functions-lookupset-function.md)。</span><span class="sxs-lookup"><span data-stu-id="53a17-129">To retrieve multiple values from a dataset with name-value pairs for a name where there is a 1-to-many relationship, use [LookupSet Function &#40;Report Builder and SSRS&#41;](report-builder-functions-lookupset-function.md).</span></span>  
  
 <span data-ttu-id="53a17-130">存在以下限制：</span><span class="sxs-lookup"><span data-stu-id="53a17-130">The following restrictions apply:</span></span>  
  
-   <span data-ttu-id="53a17-131">在应用所有筛选表达式后计算 `Multilookup` 的结果</span><span class="sxs-lookup"><span data-stu-id="53a17-131">`Multilookup` is evaluated after all filter expressions are applied</span></span>  
  
-   <span data-ttu-id="53a17-132">只支持一个级别的查找。</span><span class="sxs-lookup"><span data-stu-id="53a17-132">Only one level of look-up is supported.</span></span> <span data-ttu-id="53a17-133">源、目标或结果表达式不能包含对查找函数的引用。</span><span class="sxs-lookup"><span data-stu-id="53a17-133">A source, destination, or result expression cannot include a reference to a lookup function.</span></span>  
  
-   <span data-ttu-id="53a17-134">源和目标表达式必须对同一数据类型计算结果。</span><span class="sxs-lookup"><span data-stu-id="53a17-134">Source and destination expressions must evaluate to the same data type.</span></span>  
  
-   <span data-ttu-id="53a17-135">源、目标和结果表达式不能包含对报表或组变量的引用。</span><span class="sxs-lookup"><span data-stu-id="53a17-135">Source, destination, and result expressions cannot include references to report or group variables.</span></span>  
  
-   <span data-ttu-id="53a17-136">`Multilookup` 不能作为以下报表项的表达式：</span><span class="sxs-lookup"><span data-stu-id="53a17-136">`Multilookup` cannot be used as an expression for the following report items:</span></span>  
  
    -   <span data-ttu-id="53a17-137">数据源的动态连接字符串。</span><span class="sxs-lookup"><span data-stu-id="53a17-137">Dynamic connection strings for a data source.</span></span>  
  
    -   <span data-ttu-id="53a17-138">数据集中的计算字段。</span><span class="sxs-lookup"><span data-stu-id="53a17-138">Calculated fields in a dataset.</span></span>  
  
    -   <span data-ttu-id="53a17-139">数据集中的查询参数。</span><span class="sxs-lookup"><span data-stu-id="53a17-139">Query parameters in a dataset.</span></span>  
  
    -   <span data-ttu-id="53a17-140">数据集中的筛选器。</span><span class="sxs-lookup"><span data-stu-id="53a17-140">Filters in a dataset.</span></span>  
  
    -   <span data-ttu-id="53a17-141">报表参数。</span><span class="sxs-lookup"><span data-stu-id="53a17-141">Report parameters.</span></span>  
  
    -   <span data-ttu-id="53a17-142">Report.Language 属性。</span><span class="sxs-lookup"><span data-stu-id="53a17-142">The Report.Language property.</span></span>  
  
 <span data-ttu-id="53a17-143">有关详细信息，请参阅[聚合函数引用（报表生成器和 SSRS）](report-builder-functions-aggregate-functions-reference.md)和[总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="53a17-143">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="53a17-144">示例</span><span class="sxs-lookup"><span data-stu-id="53a17-144">Example</span></span>  
 <span data-ttu-id="53a17-145">假定名为“Category”的数据集包含字段 CategoryList，该字段包含类别标识符的逗号分隔列表，例如“2, 4, 2, 1”。</span><span class="sxs-lookup"><span data-stu-id="53a17-145">Assume a dataset called "Category" contains the field CategoryList, which is a field that contains a comma-separated list of category identifers, for example, "2, 4, 2, 1".</span></span>  
  
 <span data-ttu-id="53a17-146">数据集 CategoryNames 包含类别标识符和类别名称，如下表中所示：</span><span class="sxs-lookup"><span data-stu-id="53a17-146">The dataset CategoryNames contains the category identifier and category name, as shown in the following table.</span></span>  
  
|<span data-ttu-id="53a17-147">ID</span><span class="sxs-lookup"><span data-stu-id="53a17-147">ID</span></span>|<span data-ttu-id="53a17-148">名称</span><span class="sxs-lookup"><span data-stu-id="53a17-148">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="53a17-149">1</span><span class="sxs-lookup"><span data-stu-id="53a17-149">1</span></span>|<span data-ttu-id="53a17-150">Accessories</span><span class="sxs-lookup"><span data-stu-id="53a17-150">Accessories</span></span>|  
|<span data-ttu-id="53a17-151">2</span><span class="sxs-lookup"><span data-stu-id="53a17-151">2</span></span>|<span data-ttu-id="53a17-152">Bikes</span><span class="sxs-lookup"><span data-stu-id="53a17-152">Bikes</span></span>|  
|<span data-ttu-id="53a17-153">3</span><span class="sxs-lookup"><span data-stu-id="53a17-153">3</span></span>|<span data-ttu-id="53a17-154">Clothing</span><span class="sxs-lookup"><span data-stu-id="53a17-154">Clothing</span></span>|  
|<span data-ttu-id="53a17-155">4</span><span class="sxs-lookup"><span data-stu-id="53a17-155">4</span></span>|<span data-ttu-id="53a17-156">组件</span><span class="sxs-lookup"><span data-stu-id="53a17-156">Components</span></span>|  
  
 <span data-ttu-id="53a17-157">若要查找与标识符列表对应的名称，请使用 `Multilookup`。</span><span class="sxs-lookup"><span data-stu-id="53a17-157">To look up the names that correspond to the list of  identifiers, use `Multilookup`.</span></span> <span data-ttu-id="53a17-158">必须首先将该列表拆分为字符串数组，调用 `Multilookup` 以检索类别名称，然后将结果连接成字符串。</span><span class="sxs-lookup"><span data-stu-id="53a17-158">You must first split the list into a string array, call `Multilookup` to retrieve the category names, and concatenate the results into a string.</span></span>  
  
 <span data-ttu-id="53a17-159">将以下表达式放入绑定到 Category 数据集的数据区域中的文本框时，显示“自行车, 组件, 自行车, 附件”：</span><span class="sxs-lookup"><span data-stu-id="53a17-159">The following expression, when placed in a text box in a data region bound to the Category dataset, displays "Bikes, Components, Bikes, Accessories":</span></span>  
  
```  
=Join(MultiLookup(Split(Fields!CategoryList.Value,","),  
   Fields!CategoryID.Value,Fields!CategoryName.Value,"Category")),  
   ", ")  
```  
  
## <a name="example"></a><span data-ttu-id="53a17-160">示例</span><span class="sxs-lookup"><span data-stu-id="53a17-160">Example</span></span>  
 <span data-ttu-id="53a17-161">假定数据集 ProductColors 包含颜色标识符字段 ColorID 和颜色值字段 Color，如下表中所示：</span><span class="sxs-lookup"><span data-stu-id="53a17-161">Assume a dataset ProductColors contains a color identifier field ColorID and a color value field Color, as shown in the following table.</span></span>  
  
|<span data-ttu-id="53a17-162">ColorID</span><span class="sxs-lookup"><span data-stu-id="53a17-162">ColorID</span></span>|<span data-ttu-id="53a17-163">Color</span><span class="sxs-lookup"><span data-stu-id="53a17-163">Color</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="53a17-164">1</span><span class="sxs-lookup"><span data-stu-id="53a17-164">1</span></span>|<span data-ttu-id="53a17-165">Red</span><span class="sxs-lookup"><span data-stu-id="53a17-165">Red</span></span>|  
|<span data-ttu-id="53a17-166">2</span><span class="sxs-lookup"><span data-stu-id="53a17-166">2</span></span>|<span data-ttu-id="53a17-167">蓝色</span><span class="sxs-lookup"><span data-stu-id="53a17-167">Blue</span></span>|  
|<span data-ttu-id="53a17-168">3</span><span class="sxs-lookup"><span data-stu-id="53a17-168">3</span></span>|<span data-ttu-id="53a17-169">绿色</span><span class="sxs-lookup"><span data-stu-id="53a17-169">Green</span></span>|  
  
 <span data-ttu-id="53a17-170">假定多值参数 *MyColors* 未绑定到数据集以获取可用值。</span><span class="sxs-lookup"><span data-stu-id="53a17-170">Assume the multivalue parameter *MyColors* is not bound to a dataset for its available values.</span></span> <span data-ttu-id="53a17-171">该参数的默认值设置为 2 和 3。</span><span class="sxs-lookup"><span data-stu-id="53a17-171">The default values for the parameter are set to 2 and 3.</span></span> <span data-ttu-id="53a17-172">将以下表达式放入表中的文本框时，将该参数的多个所选值连接为逗号分隔的列表并显示“蓝色, 绿色”。</span><span class="sxs-lookup"><span data-stu-id="53a17-172">The following expression, when placed in a text box in a table, concatenates the multiple selected values for the parameter into a comma-separated list and displays "Blue, Green".</span></span>  
  
```  
=Join(MultiLookup(Parameters!MyColors.Value,Fields!ColorID.Value,Fields!Color.Value,"ProductColors"),", ")  
```  
  
## <a name="see-also"></a><span data-ttu-id="53a17-173">另请参阅</span><span class="sxs-lookup"><span data-stu-id="53a17-173">See Also</span></span>  
 <span data-ttu-id="53a17-174">[在报表中使用表达式（报表生成器和 SSRS）](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="53a17-174">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="53a17-175">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="53a17-175">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="53a17-176">[表达式中的数据类型（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="53a17-176">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="53a17-177">总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="53a17-177">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
