---
title: LookupSet 函数（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7685acfd-1c8d-420c-993c-903236fbe1ff
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4edc7a17f2aa3813e8aa73e538594b5df3aeabc1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586411"
---
# <a name="lookupset-function-report-builder-and-ssrs"></a><span data-ttu-id="21f71-102">LookupSet 函数（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="21f71-102">LookupSet Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="21f71-103">从包含名称/值对的数据集返回指定名称的一组匹配值。</span><span class="sxs-lookup"><span data-stu-id="21f71-103">Returns the set of matching values for the specified name from a dataset that contains name/value pairs.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="21f71-104">语法</span><span class="sxs-lookup"><span data-stu-id="21f71-104">Syntax</span></span>  
  
```  
  
LookupSet(source_expression, destination_expression, result_expression, dataset)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21f71-105">参数</span><span class="sxs-lookup"><span data-stu-id="21f71-105">Parameters</span></span>  
 <span data-ttu-id="21f71-106">*source_expression*</span><span class="sxs-lookup"><span data-stu-id="21f71-106">*source_expression*</span></span>  
 <span data-ttu-id="21f71-107">(`Variant`) 在当前作用域中计算结果并指定要查找的名称或键的表达式。</span><span class="sxs-lookup"><span data-stu-id="21f71-107">(`Variant`) An expression that is evaluated in the current scope and that specifies the name or key to look up.</span></span> <span data-ttu-id="21f71-108">例如，`=Fields!ID.Value` 。</span><span class="sxs-lookup"><span data-stu-id="21f71-108">For example, `=Fields!ID.Value`.</span></span>  
  
 <span data-ttu-id="21f71-109">*destination_expression*</span><span class="sxs-lookup"><span data-stu-id="21f71-109">*destination_expression*</span></span>  
 <span data-ttu-id="21f71-110">(`Variant`) 针对数据集中的每行计算结果并指定要匹配的名称或键的表达式。</span><span class="sxs-lookup"><span data-stu-id="21f71-110">(`Variant`) An expression that is evaluated for each row in a dataset and that specifies the name or key to match on.</span></span> <span data-ttu-id="21f71-111">例如，`=Fields!CustomerID.Value` 。</span><span class="sxs-lookup"><span data-stu-id="21f71-111">For example, `=Fields!CustomerID.Value`.</span></span>  
  
 <span data-ttu-id="21f71-112">*result_expression*</span><span class="sxs-lookup"><span data-stu-id="21f71-112">*result_expression*</span></span>  
 <span data-ttu-id="21f71-113"> (`Variant`) 为 dataset 中的行计算的表达式，其中*source_expression*  =  *destination_expression*，并指定要检索的值。</span><span class="sxs-lookup"><span data-stu-id="21f71-113">(`Variant`) An expression that is evaluated for the row in the dataset where *source_expression* = *destination_expression*, and that specifies the value to retrieve.</span></span> <span data-ttu-id="21f71-114">例如，`=Fields!PhoneNumber.Value` 。</span><span class="sxs-lookup"><span data-stu-id="21f71-114">For example, `=Fields!PhoneNumber.Value`.</span></span>  
  
 <span data-ttu-id="21f71-115">*数据集 (dataset)*</span><span class="sxs-lookup"><span data-stu-id="21f71-115">*dataset*</span></span>  
 <span data-ttu-id="21f71-116">指定报表中数据集的名称的常量。</span><span class="sxs-lookup"><span data-stu-id="21f71-116">A constant that specifies the name of a dataset in the report.</span></span> <span data-ttu-id="21f71-117">例如，“ContactInformation”。</span><span class="sxs-lookup"><span data-stu-id="21f71-117">For example, "ContactInformation".</span></span>  
  
## <a name="return"></a><span data-ttu-id="21f71-118">返回</span><span class="sxs-lookup"><span data-stu-id="21f71-118">Return</span></span>  
 <span data-ttu-id="21f71-119">返回 `VariantArray`，如果没有匹配项，则返回 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="21f71-119">Returns a `VariantArray`, or `Nothing` if there is no match.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21f71-120">备注</span><span class="sxs-lookup"><span data-stu-id="21f71-120">Remarks</span></span>  
 <span data-ttu-id="21f71-121">使用 `LookupSet` 从名称/值对（每对具有 1 对多的关系）的指定数据集中检索一组值。</span><span class="sxs-lookup"><span data-stu-id="21f71-121">Use `LookupSet` to retrieve a set of values from the specified dataset for a name/value pair where there is a 1-to-many relationship.</span></span> <span data-ttu-id="21f71-122">例如，对于表中的客户标识符，可以使用 `LookupSet` 从未绑定到该数据区域的数据集检索该客户的所有相关电话号码。</span><span class="sxs-lookup"><span data-stu-id="21f71-122">For example, for a customer identifier in a table, you can use `LookupSet` to retrieve all the associated phone numbers for that customer from a dataset that is not bound to the data region.</span></span>  
  
 <span data-ttu-id="21f71-123">`LookupSet` 执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="21f71-123">`LookupSet` does the following:</span></span>  
  
-   <span data-ttu-id="21f71-124">计算当前作用域中源表达式的结果。</span><span class="sxs-lookup"><span data-stu-id="21f71-124">Evaluates the source expression in the current scope.</span></span>  
  
-   <span data-ttu-id="21f71-125">根据指定数据集的排序规则，在应用筛选器后对指定数据集的每行计算目标表达式的结果。</span><span class="sxs-lookup"><span data-stu-id="21f71-125">Evaluates the destination expression for each row of the specified dataset after filters have been applied, based on the collation of the specified dataset.</span></span>  
  
-   <span data-ttu-id="21f71-126">对于源表达式和目标表达式的每个匹配，计算数据集中该行的结果表达式。</span><span class="sxs-lookup"><span data-stu-id="21f71-126">For each match of source expression and destination expression, evaluates the result expression for that row in the dataset.</span></span>  
  
-   <span data-ttu-id="21f71-127">返回一组结果表达式值。</span><span class="sxs-lookup"><span data-stu-id="21f71-127">Returns the set of result expression values.</span></span>  
  
 <span data-ttu-id="21f71-128">若要从具有指定名称的名称/值对（具有 1 对 1 的关系）的数据集中检索单个值，请使用 [Lookup 函数（报表生成器和 SSRS）](report-builder-functions-lookup-function.md)。</span><span class="sxs-lookup"><span data-stu-id="21f71-128">To retrieve a single value from a dataset with name/value pairs for a specified name where there is a 1-to-1 relationship, use [Lookup Function &#40;Report Builder and SSRS&#41;](report-builder-functions-lookup-function.md).</span></span> <span data-ttu-id="21f71-129">若要调用 `Lookup` 一组值，请使用[Multilookup 函数 &#40;报表生成器和 SSRS&#41;](report-builder-functions-multilookup-function.md)。</span><span class="sxs-lookup"><span data-stu-id="21f71-129">To call `Lookup` for a set of values, use [Multilookup Function &#40;Report Builder and SSRS&#41;](report-builder-functions-multilookup-function.md).</span></span>  
  
 <span data-ttu-id="21f71-130">存在以下限制：</span><span class="sxs-lookup"><span data-stu-id="21f71-130">The following restrictions apply:</span></span>  
  
-   <span data-ttu-id="21f71-131">在应用所有筛选表达式后计算 `LookupSet` 的结果。</span><span class="sxs-lookup"><span data-stu-id="21f71-131">`LookupSet` is evaluated after all filter expressions are applied.</span></span>  
  
-   <span data-ttu-id="21f71-132">只支持一个级别的查找。</span><span class="sxs-lookup"><span data-stu-id="21f71-132">Only one level of lookup is supported.</span></span> <span data-ttu-id="21f71-133">源、目标或结果表达式不能包含对查找函数的引用。</span><span class="sxs-lookup"><span data-stu-id="21f71-133">A source, destination, or result expression cannot include a reference to a lookup function.</span></span>  
  
-   <span data-ttu-id="21f71-134">源和目标表达式必须对同一数据类型计算结果。</span><span class="sxs-lookup"><span data-stu-id="21f71-134">Source and destination expressions must evaluate to the same data type.</span></span>  
  
-   <span data-ttu-id="21f71-135">源、目标和结果表达式不能包含对报表或组变量的引用。</span><span class="sxs-lookup"><span data-stu-id="21f71-135">Source, destination, and result expressions cannot include references to report or group variables.</span></span>  
  
-   <span data-ttu-id="21f71-136">`LookupSet` 不能作为以下报表项的表达式：</span><span class="sxs-lookup"><span data-stu-id="21f71-136">`LookupSet` cannot be used as an expression for the following report items:</span></span>  
  
    -   <span data-ttu-id="21f71-137">数据源的动态连接字符串。</span><span class="sxs-lookup"><span data-stu-id="21f71-137">Dynamic connection strings for a data source.</span></span>  
  
    -   <span data-ttu-id="21f71-138">数据集中的计算字段。</span><span class="sxs-lookup"><span data-stu-id="21f71-138">Calculated fields in a dataset.</span></span>  
  
    -   <span data-ttu-id="21f71-139">数据集中的查询参数。</span><span class="sxs-lookup"><span data-stu-id="21f71-139">Query parameters in a dataset.</span></span>  
  
    -   <span data-ttu-id="21f71-140">数据集中的筛选器。</span><span class="sxs-lookup"><span data-stu-id="21f71-140">Filters in a dataset.</span></span>  
  
    -   <span data-ttu-id="21f71-141">报表参数。</span><span class="sxs-lookup"><span data-stu-id="21f71-141">Report parameters.</span></span>  
  
    -   <span data-ttu-id="21f71-142">Report.Language 属性。</span><span class="sxs-lookup"><span data-stu-id="21f71-142">The Report.Language property.</span></span>  
  
 <span data-ttu-id="21f71-143">有关详细信息，请参阅[聚合函数引用（报表生成器和 SSRS）](report-builder-functions-aggregate-functions-reference.md)和[总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="21f71-143">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="21f71-144">示例</span><span class="sxs-lookup"><span data-stu-id="21f71-144">Example</span></span>  
 <span data-ttu-id="21f71-145">在以下示例中，假定将表绑定到包含销售区域标识符 TerritoryGroupID 的数据集。</span><span class="sxs-lookup"><span data-stu-id="21f71-145">In the following example, assume the table is bound to a dataset that includes a sales territory identifier TerritoryGroupID.</span></span> <span data-ttu-id="21f71-146">名为“Stores”的独立数据集包含区域中的所有商店列表以及区域标识符 ID 和商店名称 StoreName。</span><span class="sxs-lookup"><span data-stu-id="21f71-146">A separate dataset called "Stores" contains the list of all stores in a territory and includes the territory identifier ID and the name of the store StoreName.</span></span>  
  
 <span data-ttu-id="21f71-147">在以下表达式中，`LookupSet` 将值 TerritoryGroupID 与名为“Stores”的数据集中每行的 ID 进行比较。</span><span class="sxs-lookup"><span data-stu-id="21f71-147">In the following expression, `LookupSet` compares the value TerritoryGroupID to ID for each row in the dataset called "Stores".</span></span> <span data-ttu-id="21f71-148">对于每个匹配项，将该行的 StoreName 字段值添加到结果集。</span><span class="sxs-lookup"><span data-stu-id="21f71-148">For each match, the value of the StoreName field for that row is added to the result set.</span></span>  
  
```  
=LookupSet(Fields!TerritoryGroupID.Value, Fields!ID.Value, Fields!StoreName.Value, "Stores")  
```  
  
## <a name="example"></a><span data-ttu-id="21f71-149">示例</span><span class="sxs-lookup"><span data-stu-id="21f71-149">Example</span></span>  
 <span data-ttu-id="21f71-150">由于 `LookupSet` 返回对象的集合，因此不能直接在文本框中显示结果表达式。</span><span class="sxs-lookup"><span data-stu-id="21f71-150">Because `LookupSet` returns a collection of objects, you cannot display the result expression directly in a text box.</span></span> <span data-ttu-id="21f71-151">可以将集合中每个对象的值连接为一个字符串。</span><span class="sxs-lookup"><span data-stu-id="21f71-151">You can concatenate the value of each object in the collection as a string.</span></span>  
  
 <span data-ttu-id="21f71-152">使用 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 函数 `Join` 可以创建来自一组对象的带分隔符的字符串。</span><span class="sxs-lookup"><span data-stu-id="21f71-152">Use the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] function `Join` create a delimited string from a set of objects.</span></span> <span data-ttu-id="21f71-153">使用逗号作为分隔符来合并一行中的对象。</span><span class="sxs-lookup"><span data-stu-id="21f71-153">Use a comma as a separator to combine the objects in a single line.</span></span> <span data-ttu-id="21f71-154">在某些呈现器中，你可能使用 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 换行 (`vbCrLF`) 作为分隔符以在新行列出每个值。</span><span class="sxs-lookup"><span data-stu-id="21f71-154">In some renderers, you might use a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] line feed (`vbCrLF`) as a separator to list each value on a new line.</span></span>  
  
 <span data-ttu-id="21f71-155">以下表达式用作文本框的 "值" 属性时，使用 `Join` 来创建一个列表。</span><span class="sxs-lookup"><span data-stu-id="21f71-155">The following expression, when it is used as the Value property for a text box, uses `Join` to create a list.</span></span>  
  
```  
=Join(LookupSet(Fields!TerritoryGroupID.Value, Fields!ID.Value, Fields!StoreName.Value, "Stores"),",")  
```  
  
## <a name="example"></a><span data-ttu-id="21f71-156">示例</span><span class="sxs-lookup"><span data-stu-id="21f71-156">Example</span></span>  
 <span data-ttu-id="21f71-157">对于仅呈现几次的文本框，您可以选择添加自定义代码来生成 HTML 以显示文本框中的值。</span><span class="sxs-lookup"><span data-stu-id="21f71-157">For text boxes that only render a few times, you might choose to add custom code to generate HTML to display values in a text box.</span></span> <span data-ttu-id="21f71-158">文本框中的 HTML 需要特别处理，因此对于呈现数千次的文本框来说不要这样做。</span><span class="sxs-lookup"><span data-stu-id="21f71-158">HTML in a text box requires extra processing, so this would not be a good choice for a text box that is rendered thousands of times.</span></span>  
  
 <span data-ttu-id="21f71-159">将以下 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 函数复制到报表定义中的代码块。</span><span class="sxs-lookup"><span data-stu-id="21f71-159">Copy the following [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions to a Code block in a report definition.</span></span> <span data-ttu-id="21f71-160">**MakeList** 提取在 *result_expression* 中返回的对象数组并使用 HTML 标记生成未排序的列表。</span><span class="sxs-lookup"><span data-stu-id="21f71-160">**MakeList** takes the object array that is returned in *result_expression* and builds an unordered list by using HTML tags.</span></span> <span data-ttu-id="21f71-161">**Length** 返回对象数组中的项数。</span><span class="sxs-lookup"><span data-stu-id="21f71-161">**Length** returns the number of items in the object array.</span></span>  
  
```  
Function MakeList(ByVal items As Object()) As String  
   If items Is Nothing Then  
      Return Nothing  
   End If  
  
   Dim builder As System.Text.StringBuilder =   
      New System.Text.StringBuilder()  
   builder.Append("<ul>")  
  
   For Each item As Object In items  
      builder.Append("<li>")  
      builder.Append(item)  
   Next  
   builder.Append("</ul>")  
  
   Return builder.ToString()  
End Function  
  
Function Length(ByVal items as Object()) as Integer  
   If items is Nothing Then  
      Return 0  
   End If  
   Return items.Length  
End Function  
```  
  
## <a name="example"></a><span data-ttu-id="21f71-162">示例</span><span class="sxs-lookup"><span data-stu-id="21f71-162">Example</span></span>  
 <span data-ttu-id="21f71-163">若要生成 HTML，必须调用该函数。</span><span class="sxs-lookup"><span data-stu-id="21f71-163">To generate the HTML, you must call the function.</span></span> <span data-ttu-id="21f71-164">在文本框的 Value 属性中粘贴以下表达式并将文本的标记类型设置为 HTML。</span><span class="sxs-lookup"><span data-stu-id="21f71-164">Paste the following expression in the Value property for the text box and set the markup type for text to HTML.</span></span> <span data-ttu-id="21f71-165">有关详细信息，请参阅[向报表添加 HTML（报表生成器和 SSRS）](add-html-into-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="21f71-165">For more information, see [Add HTML into a Report &#40;Report Builder and SSRS&#41;](add-html-into-a-report-report-builder-and-ssrs.md).</span></span>  
  
```  
=Code.MakeList(LookupSet(Fields!TerritoryGroupID.Value, Fields!ID.Value, Fields!StoreName.Value, "Stores"))  
```  
  
## <a name="see-also"></a><span data-ttu-id="21f71-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="21f71-166">See Also</span></span>  
 <span data-ttu-id="21f71-167">[在报表中使用表达式（报表生成器和 SSRS）](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="21f71-167">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="21f71-168">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="21f71-168">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="21f71-169">[表达式中的数据类型（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="21f71-169">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="21f71-170">总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="21f71-170">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
