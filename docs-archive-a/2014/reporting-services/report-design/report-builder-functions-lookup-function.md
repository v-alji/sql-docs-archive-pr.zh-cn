---
title: Lookup 函数（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e60e5bab-b286-4897-9685-9ff12703517d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 053fefff51e4b4e338e262664bd7570280c92540
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586408"
---
# <a name="lookup-function-report-builder-and-ssrs"></a><span data-ttu-id="2690f-102">Lookup 函数（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="2690f-102">Lookup Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="2690f-103">从包含名称/值对的数据集返回指定名称的第一个匹配值。</span><span class="sxs-lookup"><span data-stu-id="2690f-103">Returns the first matching value for the specified name from a dataset that contains name/value pairs.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="2690f-104">语法</span><span class="sxs-lookup"><span data-stu-id="2690f-104">Syntax</span></span>  
  
```  
  
Lookup(source_expression, destination_expression, result_expression, dataset)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2690f-105">参数</span><span class="sxs-lookup"><span data-stu-id="2690f-105">Parameters</span></span>  
 <span data-ttu-id="2690f-106">*source_expression*</span><span class="sxs-lookup"><span data-stu-id="2690f-106">*source_expression*</span></span>  
 <span data-ttu-id="2690f-107">(`Variant`) 在当前作用域中计算结果并指定要查找的名称或键的表达式。</span><span class="sxs-lookup"><span data-stu-id="2690f-107">(`Variant`) An expression that is evaluated in the current scope and that specifies the name or key to look up.</span></span> <span data-ttu-id="2690f-108">例如，`=Fields!ProdID.Value` 。</span><span class="sxs-lookup"><span data-stu-id="2690f-108">For example, `=Fields!ProdID.Value`.</span></span>  
  
 <span data-ttu-id="2690f-109">*destination_expression*</span><span class="sxs-lookup"><span data-stu-id="2690f-109">*destination_expression*</span></span>  
 <span data-ttu-id="2690f-110">(`Variant`) 针对数据集中的每行计算结果并指定要匹配的名称或键的表达式。</span><span class="sxs-lookup"><span data-stu-id="2690f-110">(`Variant`) An expression that is evaluated for each row in a dataset and that specifies the name or key to match on.</span></span> <span data-ttu-id="2690f-111">例如，`=Fields!ProductID.Value` 。</span><span class="sxs-lookup"><span data-stu-id="2690f-111">For example, `=Fields!ProductID.Value`.</span></span>  
  
 <span data-ttu-id="2690f-112">*result_expression*</span><span class="sxs-lookup"><span data-stu-id="2690f-112">*result_expression*</span></span>  
 <span data-ttu-id="2690f-113"> (`Variant`) 为 dataset 中的行计算的表达式，其中*source_expression*  =  *destination_expression*，并指定要检索的值。</span><span class="sxs-lookup"><span data-stu-id="2690f-113">(`Variant`) An expression that is evaluated for the row in the dataset where *source_expression* = *destination_expression*, and that specifies the value to retrieve.</span></span> <span data-ttu-id="2690f-114">例如，`=Fields!ProductName.Value` 。</span><span class="sxs-lookup"><span data-stu-id="2690f-114">For example, `=Fields!ProductName.Value`.</span></span>  
  
 <span data-ttu-id="2690f-115">*数据集 (dataset)*</span><span class="sxs-lookup"><span data-stu-id="2690f-115">*dataset*</span></span>  
 <span data-ttu-id="2690f-116">指定报表中数据集的名称的常量。</span><span class="sxs-lookup"><span data-stu-id="2690f-116">A constant that specifies the name of a dataset in the report.</span></span> <span data-ttu-id="2690f-117">例如，“Products”。</span><span class="sxs-lookup"><span data-stu-id="2690f-117">For example, "Products".</span></span>  
  
## <a name="return"></a><span data-ttu-id="2690f-118">返回</span><span class="sxs-lookup"><span data-stu-id="2690f-118">Return</span></span>  
 <span data-ttu-id="2690f-119">返回 `Variant`，如果没有匹配项，则返回 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="2690f-119">Returns a `Variant`, or `Nothing` if there is no match.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2690f-120">备注</span><span class="sxs-lookup"><span data-stu-id="2690f-120">Remarks</span></span>  
 <span data-ttu-id="2690f-121">使用 `Lookup` 从指定的数据集中为名称-值对（每对具有 1 对 1 关系）检索值。</span><span class="sxs-lookup"><span data-stu-id="2690f-121">Use `Lookup` to retrieve the value from the specified dataset for a name/value pair where there is a 1-to-1 relationship.</span></span> <span data-ttu-id="2690f-122">例如，对于表中的 ID 字段，可以使用 `Lookup` 从未绑定到该数据区域的数据集检索对应的名称字段。</span><span class="sxs-lookup"><span data-stu-id="2690f-122">For example, for an ID field in a table, you can use `Lookup` to retrieve the corresponding Name field from a dataset that is not bound to the data region.</span></span>  
  
 <span data-ttu-id="2690f-123">`Lookup` 执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="2690f-123">`Lookup` does the following:</span></span>  
  
-   <span data-ttu-id="2690f-124">计算当前作用域中源表达式的结果。</span><span class="sxs-lookup"><span data-stu-id="2690f-124">Evaluates the source expression in the current scope.</span></span>  
  
-   <span data-ttu-id="2690f-125">根据指定数据集的排序规则，在应用筛选器后对指定数据集的每行计算目标表达式的结果。</span><span class="sxs-lookup"><span data-stu-id="2690f-125">Evaluates the destination expression for each row of the specified dataset after filters have been applied, based on the collation of the specified dataset.</span></span>  
  
-   <span data-ttu-id="2690f-126">对于源表达式和目标表达式的第一个匹配，计算数据集中该行的结果表达式。</span><span class="sxs-lookup"><span data-stu-id="2690f-126">On the first match of source expression and destination expression, evaluates the result expression for that row in the dataset.</span></span>  
  
-   <span data-ttu-id="2690f-127">返回结果表达式值。</span><span class="sxs-lookup"><span data-stu-id="2690f-127">Returns the result expression value.</span></span>  
  
 <span data-ttu-id="2690f-128">若要为单个名称或键字段检索多个值（具有 1 对多关系），请使用[LookupSet 函数（报表生成器和 SSRS）](report-builder-functions-lookupset-function.md)。</span><span class="sxs-lookup"><span data-stu-id="2690f-128">To retrieve multiple values for a single name or key field where there is a 1-to-many relationship, use [LookupSet Function &#40;Report Builder and SSRS&#41;](report-builder-functions-lookupset-function.md).</span></span> <span data-ttu-id="2690f-129">若要调用 `Lookup` 一组值，请使用[Multilookup 函数 &#40;报表生成器和 SSRS&#41;](report-builder-functions-lookup-function.md)。</span><span class="sxs-lookup"><span data-stu-id="2690f-129">To call `Lookup` for a set of values, use [Multilookup Function &#40;Report Builder and SSRS&#41;](report-builder-functions-lookup-function.md).</span></span>  
  
 <span data-ttu-id="2690f-130">存在以下限制：</span><span class="sxs-lookup"><span data-stu-id="2690f-130">The following restrictions apply:</span></span>  
  
-   <span data-ttu-id="2690f-131">在应用所有筛选表达式后计算 `Lookup` 的结果。</span><span class="sxs-lookup"><span data-stu-id="2690f-131">`Lookup` is evaluated after all filter expressions are applied.</span></span>  
  
-   <span data-ttu-id="2690f-132">只支持一个级别的查找。</span><span class="sxs-lookup"><span data-stu-id="2690f-132">Only one level of lookup is supported.</span></span> <span data-ttu-id="2690f-133">源、目标或结果表达式不能包含对查找函数的引用。</span><span class="sxs-lookup"><span data-stu-id="2690f-133">A source, destination, or result expression cannot include a reference to a lookup function.</span></span>  
  
-   <span data-ttu-id="2690f-134">源和目标表达式必须对同一数据类型计算结果。</span><span class="sxs-lookup"><span data-stu-id="2690f-134">Source and destination expressions must evaluate to the same data type.</span></span> <span data-ttu-id="2690f-135">返回类型和计算后的结果表达式的数据类型相同。</span><span class="sxs-lookup"><span data-stu-id="2690f-135">The return type is the same as the data type of the evaluated result expression.</span></span>  
  
-   <span data-ttu-id="2690f-136">源、目标和结果表达式不能包含对报表或组变量的引用。</span><span class="sxs-lookup"><span data-stu-id="2690f-136">Source, destination, and result expressions cannot include references to report or group variables.</span></span>  
  
-   <span data-ttu-id="2690f-137">`Lookup` 不能作为以下报表项的表达式：</span><span class="sxs-lookup"><span data-stu-id="2690f-137">`Lookup` cannot be used as an expression for the following report items:</span></span>  
  
    -   <span data-ttu-id="2690f-138">数据源的动态连接字符串。</span><span class="sxs-lookup"><span data-stu-id="2690f-138">Dynamic connection strings for a data source.</span></span>  
  
    -   <span data-ttu-id="2690f-139">数据集中的计算字段。</span><span class="sxs-lookup"><span data-stu-id="2690f-139">Calculated fields in a dataset.</span></span>  
  
    -   <span data-ttu-id="2690f-140">数据集中的查询参数。</span><span class="sxs-lookup"><span data-stu-id="2690f-140">Query parameters in a dataset.</span></span>  
  
    -   <span data-ttu-id="2690f-141">数据集中的筛选器。</span><span class="sxs-lookup"><span data-stu-id="2690f-141">Filters in a dataset.</span></span>  
  
    -   <span data-ttu-id="2690f-142">报表参数。</span><span class="sxs-lookup"><span data-stu-id="2690f-142">Report parameters.</span></span>  
  
    -   <span data-ttu-id="2690f-143">Report.Language 属性。</span><span class="sxs-lookup"><span data-stu-id="2690f-143">The Report.Language property.</span></span>  
  
 <span data-ttu-id="2690f-144">有关详细信息，请参阅[聚合函数引用（报表生成器和 SSRS）](report-builder-functions-aggregate-functions-reference.md)和[总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="2690f-144">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2690f-145">示例</span><span class="sxs-lookup"><span data-stu-id="2690f-145">Example</span></span>  
 <span data-ttu-id="2690f-146">在以下示例中，假定将某个表绑定到包含一个用于产品标识符 ProductID 的字段的数据集。</span><span class="sxs-lookup"><span data-stu-id="2690f-146">In the following example, assume that a table is bound to a dataset that includes a field for the product identifier ProductID.</span></span> <span data-ttu-id="2690f-147">一个单独的称为“Product”的数据集包含相应的产品标识符“ID”和产品名称“名称”。</span><span class="sxs-lookup"><span data-stu-id="2690f-147">A separate dataset called "Product" contains the corresponding product identifier ID and the product name Name.</span></span>  
  
 <span data-ttu-id="2690f-148">在下面的表达式中，`Lookup` 将 ProductID 的值与名为“Product”的数据集的每行中的 ID 进行比较，当找到匹配项后，为该行返回“名称”字段的值。</span><span class="sxs-lookup"><span data-stu-id="2690f-148">In the following expression, `Lookup` compares the value of ProductID to ID in each row of the dataset called "Product" and, when a match is found, returns the value of the Name field for that row.</span></span>  
  
```  
=Lookup(Fields!ProductID.Value, Fields!ID.Value, Fields!Name.Value, "Product")  
```  
  
## <a name="see-also"></a><span data-ttu-id="2690f-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2690f-149">See Also</span></span>  
 <span data-ttu-id="2690f-150">[在报表中使用表达式（报表生成器和 SSRS）](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2690f-150">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2690f-151">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2690f-151">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2690f-152">[表达式中的数据类型（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2690f-152">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="2690f-153">总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="2690f-153">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
