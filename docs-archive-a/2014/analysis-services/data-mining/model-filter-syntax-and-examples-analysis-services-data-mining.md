---
title: 模型筛选器语法和示例 (Analysis Services 数据挖掘) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- model filter [data mining]
- filter syntax [data mining]
- filters [data mining]
- filters [Analysis Services]
ms.assetid: c729d9b3-8fda-405e-9497-52b2d7493eae
author: minewiskan
ms.author: owend
ms.openlocfilehash: f7ca200d179c0fe81b948793a4b4478f71502657
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687372"
---
# <a name="model-filter-syntax-and-examples-analysis-services---data-mining"></a><span data-ttu-id="67166-102">模型筛选器语法和示例（Analysis Services – 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="67166-102">Model Filter Syntax and Examples (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="67166-103">本节提供有关模型筛选器语法的详细信息以及示例表达式。</span><span class="sxs-lookup"><span data-stu-id="67166-103">This section provides detailed information about the syntax for model filters, together with sample expressions.</span></span>  
  
 
  
##  <a name="filter-syntax"></a><a name="bkmk_Syntax"></a><span data-ttu-id="67166-104">筛选器语法</span><span class="sxs-lookup"><span data-stu-id="67166-104">Filter Syntax</span></span>  
 <span data-ttu-id="67166-105">筛选表达式通常等同于 WHERE 子句的内容。</span><span class="sxs-lookup"><span data-stu-id="67166-105">Filter expressions generally are equivalent to the content of a WHERE clause.</span></span> <span data-ttu-id="67166-106">您可以使用逻辑运算符 `AND`、`OR` 和 `NOT` 连接多个条件。</span><span class="sxs-lookup"><span data-stu-id="67166-106">You can connect multiple conditions by using the logical operators `AND`, `OR`, and `NOT`.</span></span>  
  
 <span data-ttu-id="67166-107">在嵌套表中，您还可以使用 `EXISTS` 和 `NOT EXISTS` 运算符。</span><span class="sxs-lookup"><span data-stu-id="67166-107">In nested tables, you can also use the `EXISTS` and `NOT EXISTS` operators.</span></span> <span data-ttu-id="67166-108">如果子查询至少返回一行，则 `EXISTS` 条件的计算结果为 `true`。</span><span class="sxs-lookup"><span data-stu-id="67166-108">An `EXISTS` condition evaluates to `true` if the subquery returns at least one row.</span></span> <span data-ttu-id="67166-109">当您要将模型限制为包含嵌套表中的特殊值的事例时，这将非常有用。例如，客户至少购买过一次某种物品。</span><span class="sxs-lookup"><span data-stu-id="67166-109">This is useful in cases where you want to restrict the model to cases that contain a particular value in the nested table: for example, customers who have purchased an item at least once.</span></span>  
  
 <span data-ttu-id="67166-110">如果在子查询中指定的 `NOT EXISTS` 条件不存在，则该条件的计算结果为 `true`。</span><span class="sxs-lookup"><span data-stu-id="67166-110">A `NOT EXISTS` condition evaluates to `true` if the condition specified in the subquery does not exist.</span></span> <span data-ttu-id="67166-111">其中一个例子就是您要将模型限制为从未购买过某种特殊物品的客户。</span><span class="sxs-lookup"><span data-stu-id="67166-111">An example is when you want to restrict the model to customers who have never purchased a particular item.</span></span>  
  
 <span data-ttu-id="67166-112">常规语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="67166-112">The general syntax is as follows:</span></span>  
  
```  
<filter>::=<predicate list>  | ( <predicate list> )  
<predicate list>::= <predicate> | [<logical_operator> <predicate list>]   
<logical_operator::= AND| OR  
<predicate>::= NOT <predicate>|( <predicate> ) <avPredicate> | <nestedTablePredicate> | ( <predicate> )   
<avPredicate>::= <columnName> <operator> <scalar> | <columnName> IS [NOT] NULL  
<operator>::= = | != | <> | > | >= | < | <=  
<nestedTablePredicate>::= EXISTS (<subquery>)  
<subquery>::=SELECT * FROM <columnName>[ WHERE  <predicate list> ]  
```  
  
 <span data-ttu-id="67166-113">*filter*</span><span class="sxs-lookup"><span data-stu-id="67166-113">*filter*</span></span>  
 <span data-ttu-id="67166-114">包含由逻辑运算符连接的一个或多个谓词。</span><span class="sxs-lookup"><span data-stu-id="67166-114">Contains one or more predicates, connected by logical operators.</span></span>  
  
 <span data-ttu-id="67166-115">*谓词列表*</span><span class="sxs-lookup"><span data-stu-id="67166-115">*predicate list*</span></span>  
 <span data-ttu-id="67166-116">用逻辑运算符分隔的一个或多个有效的筛选表达式。</span><span class="sxs-lookup"><span data-stu-id="67166-116">One or more valid filter expressions, separated by logical operators.</span></span>  
  
 <span data-ttu-id="67166-117">*columnName*</span><span class="sxs-lookup"><span data-stu-id="67166-117">*columnName*</span></span>  
 <span data-ttu-id="67166-118">挖掘结构列的名称。</span><span class="sxs-lookup"><span data-stu-id="67166-118">The name of a mining structure column.</span></span>  
  
 <span data-ttu-id="67166-119">逻辑运算符</span><span class="sxs-lookup"><span data-stu-id="67166-119">logical operator</span></span>  
 <span data-ttu-id="67166-120">`AND`, `OR`, `NOT`</span><span class="sxs-lookup"><span data-stu-id="67166-120">`AND`, `OR`, `NOT`</span></span>  
  
 <span data-ttu-id="67166-121">*avPredicate*</span><span class="sxs-lookup"><span data-stu-id="67166-121">*avPredicate*</span></span>  
 <span data-ttu-id="67166-122">只能应用到标量挖掘结构列的筛选表达式。</span><span class="sxs-lookup"><span data-stu-id="67166-122">Filter expression that can be applied to scalar mining structure column only.</span></span> <span data-ttu-id="67166-123">*avPredicate* 表达式既可用于模型筛选器中，也可用于嵌套表筛选器中。</span><span class="sxs-lookup"><span data-stu-id="67166-123">An *avPredicate* expression can be used in both model filters or nested table filters.</span></span>  
  
 <span data-ttu-id="67166-124">使用以下任何运算符的表达式只能应用到连续列中。</span><span class="sxs-lookup"><span data-stu-id="67166-124">An expression that uses any of the following operators can only be applied to a continuous column.</span></span> <span data-ttu-id="67166-125">:</span><span class="sxs-lookup"><span data-stu-id="67166-125">:</span></span>  
  
-   <span data-ttu-id="67166-126">**\<** (小于) </span><span class="sxs-lookup"><span data-stu-id="67166-126">**\<** (less than)</span></span>  
  
-   <span data-ttu-id="67166-127">**>** (大于) </span><span class="sxs-lookup"><span data-stu-id="67166-127">**>** (greater than)</span></span>  
  
-   <span data-ttu-id="67166-128">**>=** (大于或等于) </span><span class="sxs-lookup"><span data-stu-id="67166-128">**>=** (greater than or equal to)</span></span>  
  
-   <span data-ttu-id="67166-129">**\<=** (小于或等于) </span><span class="sxs-lookup"><span data-stu-id="67166-129">**\<=** (less than or equal to)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="67166-130">无论是什么数据类型，这些运算符都不能应用到类型为 `Discrete`、`Discretized` 或 `Key` 的列。</span><span class="sxs-lookup"><span data-stu-id="67166-130">Regardless of the data type, these operators cannot be applied to a column that has the type `Discrete`, `Discretized`, or `Key`.</span></span>  
  
 <span data-ttu-id="67166-131">使用以下任何运算符的表达式可以应用到连续、离散、离散化或键列中：</span><span class="sxs-lookup"><span data-stu-id="67166-131">An expression that uses any of the following operators can be applied to a continuous, discrete, discretized, or key column:</span></span>  
  
-   <span data-ttu-id="67166-132">**=** (等于) </span><span class="sxs-lookup"><span data-stu-id="67166-132">**=** (equals)</span></span>  
  
-   <span data-ttu-id="67166-133">**！ =** (不等于) </span><span class="sxs-lookup"><span data-stu-id="67166-133">**!=** (not equal to)</span></span>  
  
-   <span data-ttu-id="67166-134">**为 NULL**</span><span class="sxs-lookup"><span data-stu-id="67166-134">**IS NULL**</span></span>  
  
 <span data-ttu-id="67166-135">如果 *avPredicate*参数应用到离散化列中，则筛选器中所用的值可以是特定的存储桶中的任何值。</span><span class="sxs-lookup"><span data-stu-id="67166-135">If the argument, *avPredicate*, applies to a discretized column, the value used in the filter can be any value in a specific bucket.</span></span>  
  
 <span data-ttu-id="67166-136">换句话说，你没有将条件定义为 `AgeDisc = '25-35'`，而是计算并使用该区间的值。</span><span class="sxs-lookup"><span data-stu-id="67166-136">In other words, you do not define the condition as `AgeDisc = '25-35'`, but instead compute and then use a value from that interval.</span></span>  
  
 <span data-ttu-id="67166-137">例如，  `AgeDisc = 27`  表示与 27 位于同一区间的任何值，在本例中为 25-35。</span><span class="sxs-lookup"><span data-stu-id="67166-137">Example:  `AgeDisc = 27`  means any value in the same interval as 27, which in this case is 25-35.</span></span>  
  
 <span data-ttu-id="67166-138">*nestedTablePredicate*</span><span class="sxs-lookup"><span data-stu-id="67166-138">*nestedTablePredicate*</span></span>  
 <span data-ttu-id="67166-139">应用到嵌套表中的筛选表达式。</span><span class="sxs-lookup"><span data-stu-id="67166-139">Filter expression that applies to a nested table.</span></span> <span data-ttu-id="67166-140">只能用于模型筛选器中。</span><span class="sxs-lookup"><span data-stu-id="67166-140">Can be used in model filters only.</span></span>  
  
 <span data-ttu-id="67166-141">参数的子查询参数 *nestedTablePredicate*能应用到表挖掘结构列中</span><span class="sxs-lookup"><span data-stu-id="67166-141">The sub-query argument of the argument, *nestedTablePredicate*, can only apply to a table mining structure column</span></span>  
  
 <span data-ttu-id="67166-142">子查询</span><span class="sxs-lookup"><span data-stu-id="67166-142">subquery</span></span>  
 <span data-ttu-id="67166-143">后面跟随有效的谓词或谓词列表的 SELECT 语句。</span><span class="sxs-lookup"><span data-stu-id="67166-143">A SELECT statement followed by a valid predicate or list of predicates.</span></span>  
  
 <span data-ttu-id="67166-144">所有谓词必须为 *avPredicates*中描述的类型。</span><span class="sxs-lookup"><span data-stu-id="67166-144">All the predicates must be of the type described in *avPredicates*.</span></span> <span data-ttu-id="67166-145">而且，谓词只能是由 *columnName*参数标识的当前嵌套表中包含的列。</span><span class="sxs-lookup"><span data-stu-id="67166-145">Furthermore, the predicates can refer only to columns that are included in the current nested table, identified by the argument, *columnName*.</span></span>  
  
### <a name="limitations-on-filter-syntax"></a><span data-ttu-id="67166-146">筛选器语法限制</span><span class="sxs-lookup"><span data-stu-id="67166-146">Limitations on Filter Syntax</span></span>  
 <span data-ttu-id="67166-147">下面的限制适用于筛选器：</span><span class="sxs-lookup"><span data-stu-id="67166-147">The following restrictions apply to filters:</span></span>  
  
-   <span data-ttu-id="67166-148">筛选器只能包含简单的谓词。</span><span class="sxs-lookup"><span data-stu-id="67166-148">A filter can contain only simple predicates.</span></span> <span data-ttu-id="67166-149">其中包括数学运算符、标量和列名称。</span><span class="sxs-lookup"><span data-stu-id="67166-149">These include mathematical operators, scalars, and column names.</span></span>  
  
-   <span data-ttu-id="67166-150">筛选器语法中不支持用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="67166-150">User-defined functions are not supported in the filter syntax.</span></span>  
  
-   <span data-ttu-id="67166-151">筛选器语法中不支持非布尔运算符，如加号或减号。</span><span class="sxs-lookup"><span data-stu-id="67166-151">Non-Boolean operators, such as the plus or minus signs, are not supported in the filter syntax.</span></span>  
  
## <a name="examples-of-filters"></a><span data-ttu-id="67166-152">筛选器示例</span><span class="sxs-lookup"><span data-stu-id="67166-152">Examples of Filters</span></span>  
 <span data-ttu-id="67166-153">下面的示例演示应用到挖掘模型中的筛选器的用法。</span><span class="sxs-lookup"><span data-stu-id="67166-153">The following examples demonstrate the use of filters applied to a mining model.</span></span> <span data-ttu-id="67166-154">如果使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]在筛选器对话框的 **“属性”** 窗口和 **“表达式”** 窗格创建筛选表达式，您将只能看到显示在 WITH FILTER 关键字之后的字符串。</span><span class="sxs-lookup"><span data-stu-id="67166-154">If you create the filter expression by using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in the **Property** window and the **Expression** pane of the filter dialog box, you would see only the string that appears after the WITH FILTER keywords.</span></span> <span data-ttu-id="67166-155">此处包括挖掘结构的定义，从而更易于理解列类型和用法。</span><span class="sxs-lookup"><span data-stu-id="67166-155">Here, the definition of the mining structure is included to make it easier to understand the column type and usage.</span></span>  
  
###  <a name="example-1-typical-case-level-filtering"></a><a name="bkmk_Ex1"></a> <span data-ttu-id="67166-156">示例 1：典型的事例级筛选</span><span class="sxs-lookup"><span data-stu-id="67166-156">Example 1: Typical Case-Level Filtering</span></span>  
 <span data-ttu-id="67166-157">以下示例显示一个简单的筛选器，它将模型中使用的事例限制为其职业为建筑师并且年龄在 30 岁以上的客户。</span><span class="sxs-lookup"><span data-stu-id="67166-157">This example shows a simple filter that restricts the cases used in the model to customers whose occupation is architect and whose age is over 30.</span></span>  
  
```  
ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_1  
(  
CustomerId,  
Age,  
Occupation,  
MaritalStatus PREDICT  
)  
WITH FILTER (Age > 30 AND Occupation='Architect')  
```  
  

  
###  <a name="example-2-case-level-filtering-using-nested-table-attributes"></a><a name="bkmk_Ex2"></a> <span data-ttu-id="67166-158">示例 2：使用嵌套表属性的事例级筛选</span><span class="sxs-lookup"><span data-stu-id="67166-158">Example 2: Case-Level Filtering using Nested Table Attributes</span></span>  
 <span data-ttu-id="67166-159">如果您的挖掘结构包含嵌套表，则您可以对嵌套表中某个值的存在性进行筛选，还可以对包含特定值的嵌套表行进行筛选。</span><span class="sxs-lookup"><span data-stu-id="67166-159">If your mining structure contains nested tables, you can either filter on the existence of a value in a nested table, or filter on nested table rows that contain a specific value.</span></span> <span data-ttu-id="67166-160">下面的示例将模型所用的事例限制为年龄在 30 岁以上并且至少购买过一次包含牛奶在内的产品的客户。</span><span class="sxs-lookup"><span data-stu-id="67166-160">This example restricts the cases used for the model to customers over the age of 30 who made at least one purchase that included milk.</span></span>  
  
 <span data-ttu-id="67166-161">如下面的示例所示，不要求筛选器仅使用模型中包含的列。</span><span class="sxs-lookup"><span data-stu-id="67166-161">As this example shows, it is not necessary that the filter use only columns that are included in the model.</span></span> <span data-ttu-id="67166-162">嵌套表 **产品** 是挖掘结构的一部分，但没有包含在挖掘模型内。</span><span class="sxs-lookup"><span data-stu-id="67166-162">The nested table **Products** is part of the mining structure, but is not included in the mining model.</span></span> <span data-ttu-id="67166-163">但是，您仍然可以对嵌套表中的值和属性进行筛选。</span><span class="sxs-lookup"><span data-stu-id="67166-163">However, you can still filter on values and attributes in the nested table.</span></span> <span data-ttu-id="67166-164">若要查看这些事例的详细信息，必须启用钻取功能。</span><span class="sxs-lookup"><span data-stu-id="67166-164">To view the details of these cases, drillthrough must be enabled.</span></span>  
  
```  
ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_2  
(  
CustomerId,  
Age,  
Occupation,  
MaritalStatus PREDICT  
)  
WITH DRILLTHROUGH,   
FILTER (Age > 30 AND EXISTS (SELECT * FROM Products WHERE ProductName='Milk')  
)  
```  
  
 
  
###  <a name="example-3-case-level-filtering-on-multiple-nested-table-attributes"></a><a name="bkmk_Ex3"></a> <span data-ttu-id="67166-165">示例 3：对多个嵌套表属性的事例级筛选</span><span class="sxs-lookup"><span data-stu-id="67166-165">Example 3: Case-Level Filtering on Multiple Nested Table Attributes</span></span>  
 <span data-ttu-id="67166-166">下面的示例显示一个由三个条件构成的筛选器：第一个条件应用到事例表，第二个条件应用到嵌套表中的一个属性，第三个条件应用到嵌套表列中某一列的特定值。</span><span class="sxs-lookup"><span data-stu-id="67166-166">This example shows a three-part filter: a condition applies to the case table, another condition to an attribute in the nested table, and another condition on a specific value in one of the nested table columns.</span></span>  
  
 <span data-ttu-id="67166-167">筛选器中的第一个条件 `Age > 30`应用到事例表中的某一列。</span><span class="sxs-lookup"><span data-stu-id="67166-167">The first condition in the filter, `Age > 30`, applies to a column in the case table.</span></span> <span data-ttu-id="67166-168">其他条件都应用到嵌套表。</span><span class="sxs-lookup"><span data-stu-id="67166-168">The remaining conditions apply to the nested table.</span></span>  
  
 <span data-ttu-id="67166-169">第二个条件 `EXISTS (SELECT * FROM Products WHERE ProductName='Milk'`检查嵌套表中是否至少存在一次包含牛奶在内的产品购买活动。</span><span class="sxs-lookup"><span data-stu-id="67166-169">The second condition, `EXISTS (SELECT * FROM Products WHERE ProductName='Milk'`, checks for the presence of at least one purchase in the nested table that included milk.</span></span> <span data-ttu-id="67166-170">第三个条件 `Quantity>=2`意味着客户在单次交易中至少购买了两单位的牛奶。</span><span class="sxs-lookup"><span data-stu-id="67166-170">The third condition, `Quantity>=2`, means that the customer must have purchased at least two units of milk in a single transaction.</span></span>  
  
```  
ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_3  
(  
CustomerId,  
Age,  
Occupation,  
MaritalStatus PREDICT,  
Products PREDICT  
(  
ProductName KEY,  
Quantity        
)  
)  
FILTER (Age > 30 AND EXISTS (SELECT * FROM Products WHERE ProductName='Milk'  AND Quantity >= 2)   
)  
```  
  

  
###  <a name="example-4-case-level-filtering-on-absence-of-nested-table-attributes"></a><a name="bkmk_Ex4"></a> <span data-ttu-id="67166-171">示例 4：对嵌套表属性缺失的事例级筛选</span><span class="sxs-lookup"><span data-stu-id="67166-171">Example 4: Case-Level Filtering On Absence of Nested Table Attributes</span></span>  
 <span data-ttu-id="67166-172">下面的示例显示如何通过对嵌套表中属性的缺失进行筛选将事例限制为没有购买过特定物品的客户。</span><span class="sxs-lookup"><span data-stu-id="67166-172">This example shows how to limit cases to customer who did not purchase a specific item, by filtering on the absence of an attribute in the nested table.</span></span> <span data-ttu-id="67166-173">在下面的示例中，使用年龄在 30 岁以上并且从未购买过牛奶的客户对模型进行定型。</span><span class="sxs-lookup"><span data-stu-id="67166-173">In this example, the model is trained using customers over the age of 30 who have never bought milk.</span></span>  
  
```  
ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_4  
(  
CustomerId,  
Age,  
Occupation,  
MaritalStatus PREDICT,  
Products PREDICT  
(  
ProductName  
)  
)  
FILTER (Age > 30 AND NOT EXISTS (SELECT * FROM Products WHERE ProductName='Milk') )  
```  
  

  
###  <a name="example-5-filtering-on-multiple-nested-table-values"></a><a name="bkmk_Ex5"></a> <span data-ttu-id="67166-174">示例 5：对多个嵌套表值进行筛选</span><span class="sxs-lookup"><span data-stu-id="67166-174">Example 5: Filtering on Multiple Nested Table Values</span></span>  
 <span data-ttu-id="67166-175">下面的示例的目的旨在显示嵌套表筛选。</span><span class="sxs-lookup"><span data-stu-id="67166-175">The purpose of the example is to show nested table filtering.</span></span> <span data-ttu-id="67166-176">嵌套表筛选器是在事例筛选器之后应用的，并且仅用于限制嵌套表行。</span><span class="sxs-lookup"><span data-stu-id="67166-176">The nested table filter is applied after the case filter, and only restricts nested table rows.</span></span>  
  
 <span data-ttu-id="67166-177">由于没有指定 EXISTS，因此该模型包含多个嵌套表为空的事例。</span><span class="sxs-lookup"><span data-stu-id="67166-177">This model could contain multiple cases with empty nested tables because EXISTS is not specified.</span></span>  
  
```  
ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_5  
(  
CustomerId,  
Age,  
Occupation,  
MaritalStatus PREDICT,  
Products PREDICT  
(  
ProductName KEY,  
Quantity        
) WITH FILTER(ProductName='Milk' OR ProductName='bottled water')  
)  
WITH DRILLTHROUGH  
```  
  

  
###  <a name="example-6-filtering-on-nested-table-attributes-and-exists"></a><a name="bkmk_Ex6"></a> <span data-ttu-id="67166-178">示例 6：对嵌套表属性和 EXISTS 的筛选</span><span class="sxs-lookup"><span data-stu-id="67166-178">Example 6: Filtering on Nested Table Attributes and EXISTS</span></span>  
 <span data-ttu-id="67166-179">在下面的示例中，嵌套表上的筛选器将行限制为包含牛奶或瓶装水的行。</span><span class="sxs-lookup"><span data-stu-id="67166-179">In this example, the filter on the nested table restricts the rows to those that contain either milk or bottled water.</span></span> <span data-ttu-id="67166-180">然后，使用 `EXISTS` 语句对模型中的事例进行限制。</span><span class="sxs-lookup"><span data-stu-id="67166-180">Then, the cases in the model are restricted by using an `EXISTS` statement.</span></span> <span data-ttu-id="67166-181">这样即可保证嵌套表不为空。</span><span class="sxs-lookup"><span data-stu-id="67166-181">This makes sure that the nested table is not empty.</span></span>  
  
```  
ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_6  
(  
CustomerId,  
Age,  
Occupation,  
MaritalStatus PREDICT,  
Products PREDICT  
(  
ProductName KEY,  
Quantity        
) WITH FILTER(ProductName='Milk' OR ProductName='bottled water')  
)  
FILTER (EXISTS (Products))  
```  
  

  
###  <a name="example-7-complex-filter-combinations"></a><a name="bkmk_Ex7"></a> <span data-ttu-id="67166-182">示例 7：复杂的筛选器组合</span><span class="sxs-lookup"><span data-stu-id="67166-182">Example 7: Complex Filter Combinations</span></span>  
 <span data-ttu-id="67166-183">此模型的应用场景类似于示例 4，但比示例 4 要复杂得多。</span><span class="sxs-lookup"><span data-stu-id="67166-183">The scenario for this model resembles that of Example 4, but is far more complex.</span></span> <span data-ttu-id="67166-184">嵌套表**ProductsOnSale**具有筛选条件， `(OnSale)` 这意味着**OnSale**的值必须 `true` 为**ProductName**中列出的产品。</span><span class="sxs-lookup"><span data-stu-id="67166-184">The nested table, **ProductsOnSale**, has the filter condition `(OnSale)` meaning that the value of **OnSale** must be `true` for the product listed in **ProductName**.</span></span> <span data-ttu-id="67166-185">此处 **OnSale** 是一个结构列。</span><span class="sxs-lookup"><span data-stu-id="67166-185">Here, **OnSale** is a structure column.</span></span>  
  
 <span data-ttu-id="67166-186">筛选器的第二部分（对于**ProductsNotOnSale**）重复此语法，但筛选**OnSale**的值为的产品 `not true``(!OnSale)` 。</span><span class="sxs-lookup"><span data-stu-id="67166-186">The second part of the filter, for **ProductsNotOnSale**, repeats this syntax, but filters on products for which the value of **OnSale** is `not true``(!OnSale)`.</span></span>  
  
 <span data-ttu-id="67166-187">最后，这些条件将组合在一起，同时另一个限制将添加到事例表中。</span><span class="sxs-lookup"><span data-stu-id="67166-187">Finally, the conditions are combined and one additional restriction is added to the case table.</span></span> <span data-ttu-id="67166-188">结果是可以对年龄在 25 岁以上的所有客户根据在 **ProductsOnSale** 列表中包含的事例预测其在 **ProductsNotOnSale** 列表中的产品的购买情况。</span><span class="sxs-lookup"><span data-stu-id="67166-188">The result is to predict purchases of products in the **ProductsNotOnSale** list, based on the cases that are included in the **ProductsOnSale** list, for all customers over the age of 25.</span></span>  
  
 `ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_7`  
  
 `(`  
  
 `CustomerId,`  
  
 `Age,`  
  
 `Occupation,`  
  
 `MaritalStatus,`  
  
 `ProductsOnSale`  
  
 `(`  
  
 `ProductName KEY`  
  
 `) WITH FILTER(OnSale),`  
  
 `ProductsNotOnSale PREDICT ONLY`  
  
 `(`  
  
 `ProductName KEY`  
  
 `) WITH FILTER(!OnSale)`  
  
 `)`  
  
 `WITH DRILLTHROUGH,`  
  
 `FILTER (EXISTS (ProductsOnSale) AND EXISTS(ProductsNotOnSale) AND Age > 25)`  
  
  
  
###  <a name="example-8-filtering-on-dates"></a><a name="bkmk_Ex8"></a> <span data-ttu-id="67166-189">示例 8：对日期进行筛选</span><span class="sxs-lookup"><span data-stu-id="67166-189">Example 8: Filtering on Dates</span></span>  
 <span data-ttu-id="67166-190">您可以像对任何其他数据一样，按日期筛选输入列。</span><span class="sxs-lookup"><span data-stu-id="67166-190">You can filter input columns on dates, as you would any other data.</span></span> <span data-ttu-id="67166-191">在日期/时间类型的列中包含的日期是连续值；因此，您可以通过使用大于号 (>) 或小于号 (<) 之类的运算符指定日期范围。</span><span class="sxs-lookup"><span data-stu-id="67166-191">Dates contained in a column of type date/time are continuous values; therefore, you can specify a date range by using operators such as greater than (>) or less than (<).</span></span> <span data-ttu-id="67166-192">如果您的数据源不是按连续数据类型表示日期的，而是将日期表示为离散值或文本值，则不能对日期范围进行筛选，而必须指定单独的离散值。</span><span class="sxs-lookup"><span data-stu-id="67166-192">If your data source does not represent dates by a Continuous data type, but as discrete or text values, you cannot filter on a date range, but must specify individual discrete values.</span></span>  
  
 <span data-ttu-id="67166-193">但是，如果用于筛选器的日期列也是用于模型的键列，则不能对时序模型中的日期列创建筛选器。</span><span class="sxs-lookup"><span data-stu-id="67166-193">However, you cannot create a filter on the date column in a time series model if the date column used for the filter is also the key column for the model.</span></span> <span data-ttu-id="67166-194">其原因在于，在时序模型以及顺序分析和聚类分析模型中，日期列可作为 `KeyTime` 或 `KeySequence` 类型处理。</span><span class="sxs-lookup"><span data-stu-id="67166-194">That is because, in time series models and sequence clustering models, the date column might be handled as type `KeyTime` or `KeySequence`.</span></span>  
  
 <span data-ttu-id="67166-195">如果您需要对时序模型中的连续日期进行筛选，则可以在挖掘结构中创建该列的一个副本，然后对这个新列筛选该模型。</span><span class="sxs-lookup"><span data-stu-id="67166-195">If you need to filter on continuous dates in a time series model, you can create a copy of the column in the mining structure, and filter the model on the new column.</span></span>  
  
 <span data-ttu-id="67166-196">例如，以下表达式表示针对已添加到 Forecasting 模型的 `Continuous` 类型的日期列的筛选器。</span><span class="sxs-lookup"><span data-stu-id="67166-196">For example, the following expression represents a filter on a date column of type `Continuous` that has been added to the Forecasting model.</span></span>  
  
 `=[DateCopy] > '12:31:2003:00:00:00'`  
  
> [!NOTE]  
>  <span data-ttu-id="67166-197">请注意，添加到模型的任何附加列都可能会影响结果。</span><span class="sxs-lookup"><span data-stu-id="67166-197">Note that any extra columns that you add to the model might affect the results.</span></span> <span data-ttu-id="67166-198">因此，如果您不希望该列用于序列的计算，则应该仅将该列添加到挖掘结构，而不是添加到模型。</span><span class="sxs-lookup"><span data-stu-id="67166-198">Therefore, if you do not want the column to be used in computation of the series, you should add the column only to the mining structure, and not to the model.</span></span> <span data-ttu-id="67166-199">您还可以将针对该列的模型标志设置为 `PredictOnly` 或 `Ignore`。</span><span class="sxs-lookup"><span data-stu-id="67166-199">You can also set the model flag on the column to `PredictOnly` or to `Ignore`.</span></span> <span data-ttu-id="67166-200">有关详细信息，请参阅[建模标志（数据挖掘）](modeling-flags-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="67166-200">For more information, see [Modeling Flags &#40;Data Mining&#41;](modeling-flags-data-mining.md).</span></span>  
  
 <span data-ttu-id="67166-201">对于其他模型类型，您可以将日期用作输入条件或筛选条件，将像在任何其他列中一样。</span><span class="sxs-lookup"><span data-stu-id="67166-201">For other model types, you can use dates as input criteria or filter criteria just like you would in any other column.</span></span> <span data-ttu-id="67166-202">但是，如果您需要使用 `Continuous` 数据类型不支持的特定级别的粒度，则可以通过使用表达式提取要在筛选和分析中使用的单位，在数据源中创建派生值。</span><span class="sxs-lookup"><span data-stu-id="67166-202">However, if you need to use a specific level of granularity that is not supported by a `Continuous` data type, you can create a derived value in the data source by using expressions to extract the unit to use in filtering and analysis.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="67166-203">指定日期作为筛选条件时，必须使用以下格式，而与当前操作系统的日期格式无关： `mm/dd/yyyy`。</span><span class="sxs-lookup"><span data-stu-id="67166-203">When you specify a dates as filter criteria, you must use the following format, regardless of the date format for the current OS: `mm/dd/yyyy`.</span></span> <span data-ttu-id="67166-204">其他任何格式都会导致错误。</span><span class="sxs-lookup"><span data-stu-id="67166-204">Any other format results in an error.</span></span>  
  
 <span data-ttu-id="67166-205">例如，如果要筛选呼叫中心结果以便只显示周末，则可以在数据源视图中创建一个表达式，该表达式提取每个日期的工作日名称，然后将该工作日名称值用作输入或者在筛选中用作离散值。</span><span class="sxs-lookup"><span data-stu-id="67166-205">For example, if you want to filter your call center results to show only weekends, you can create an expression in the data source view that extracts the weekday name for each date, and then use that weekday name value for input or as a discrete value in filtering.</span></span> <span data-ttu-id="67166-206">只需记住的是，重复值可能会影响模型，因此，您应该只使用某一列，而不是日期列加上派生值。</span><span class="sxs-lookup"><span data-stu-id="67166-206">Just remember that repeating values can affect the model, so you should use only one of the columns, not the date column plus the derived value.</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="67166-207">另请参阅</span><span class="sxs-lookup"><span data-stu-id="67166-207">See Also</span></span>  
 <span data-ttu-id="67166-208">[挖掘模型的筛选器 &#40;Analysis Services 数据挖掘&#41;](mining-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="67166-208">[Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](mining-models-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="67166-209">测试和验证（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="67166-209">Testing and Validation &#40;Data Mining&#41;</span></span>](testing-and-validation-data-mining.md)  
  
  
