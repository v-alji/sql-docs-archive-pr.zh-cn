---
title: " (SQLXML 4.0) 的 XPath 数据类型 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping XDR types to XPath types [SQLXML]
- data types [XPath]
- arithmetic operators
- mapping data types [SQLXML]
- relational operators [SQLXML]
- node-set [SQLXML]
- data types [SQLXML], XPath
- XPath operators [SQLXML]
- XDR data type [SQLXML]
- equality operators [SQLXML]
- XPath conversions [SQLXML]
- converting data types [SQLXML]
- Boolean operators
- XPath queries [SQLXML], data types
- XPath data types [SQLXML]
- operators [SQLXML]
ms.assetid: a90374bf-406f-4384-ba81-59478017db68
author: rothja
ms.author: jroth
ms.openlocfilehash: 846fc5a17ac97d30b6f0ab65fee176ac459c20cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588432"
---
# <a name="xpath-data-types-sqlxml-40"></a><span data-ttu-id="4e761-102">XPath 数据类型 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="4e761-102">XPath Data Types (SQLXML 4.0)</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="4e761-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、XPath 和 XML 架构 (XSD) 的数据类型非常不同。</span><span class="sxs-lookup"><span data-stu-id="4e761-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], XPath, and XML Schema (XSD) have very different data types.</span></span> <span data-ttu-id="4e761-104">例如，XPath 没有整数或日期数据类型，但 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 XSD 则具有许多此类数据类型。</span><span class="sxs-lookup"><span data-stu-id="4e761-104">For example, XPath does not have integer or date data types, but [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and XSD have many.</span></span> <span data-ttu-id="4e761-105">XSD 可将纳秒精度用于时间值，而 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 最高只能使用 1/300 秒的精度。</span><span class="sxs-lookup"><span data-stu-id="4e761-105">XSD uses nanosecond precision for time values, and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses at most 1/300-second precision.</span></span> <span data-ttu-id="4e761-106">因此，将一种数据类型映射到另一种数据类型并不是始终可行的。</span><span class="sxs-lookup"><span data-stu-id="4e761-106">Consequently, mapping one data type to another is not always possible.</span></span> <span data-ttu-id="4e761-107">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将数据类型映射到 XSD 数据类型的详细信息，请参阅[数据类型强制转换和 sql： datatype 批注 &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="4e761-107">For more information about mapping [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types to XSD data types, see [Data Type Coercions and the sql:datatype Annotation &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="4e761-108">XPath 具有三种数据类型：`string`、`number` 和 `boolean`。</span><span class="sxs-lookup"><span data-stu-id="4e761-108">XPath has three data types: `string`, `number`, and `boolean`.</span></span> <span data-ttu-id="4e761-109">`number` 数据类型始终是 IEEE 754 双精度浮点。</span><span class="sxs-lookup"><span data-stu-id="4e761-109">The `number` data type is always an IEEE 754 double-precision floating-point.</span></span> <span data-ttu-id="4e761-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `float(53)` 数据类型是最接近的 XPath `number` 。</span><span class="sxs-lookup"><span data-stu-id="4e761-110">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`float(53)` data type is the closest to XPath `number`.</span></span> <span data-ttu-id="4e761-111">但是，`float(53)` 与 IEEE 754 并不完全相同。</span><span class="sxs-lookup"><span data-stu-id="4e761-111">However, `float(53)` is not exactly IEEE 754.</span></span> <span data-ttu-id="4e761-112">例如，NaN（非数字）和 infinity 均未使用。</span><span class="sxs-lookup"><span data-stu-id="4e761-112">For example, neither NaN (Not-a-Number) nor infinity is used.</span></span> <span data-ttu-id="4e761-113">尝试将非数字字符串转换为 `number` 和尝试以零作除数将导致错误。</span><span class="sxs-lookup"><span data-stu-id="4e761-113">Attempting to convert a nonnumeric string to `number` and trying to divide by zero results in an error.</span></span>  
  
## <a name="xpath-conversions"></a><span data-ttu-id="4e761-114">XPath 转换</span><span class="sxs-lookup"><span data-stu-id="4e761-114">XPath Conversions</span></span>  
 <span data-ttu-id="4e761-115">在您使用 `OrderDetail[@UnitPrice > "10.0"]` 之类的 XPath 查询时，隐式和显式数据类型转换可能会对查询的意义产生细微的变化。</span><span class="sxs-lookup"><span data-stu-id="4e761-115">When you use an XPath query such as `OrderDetail[@UnitPrice > "10.0"]`, implicit and explicit data type conversions can change the meaning of the query in subtle ways.</span></span> <span data-ttu-id="4e761-116">因此，理解 XPath 数据类型的实现方式十分重要。</span><span class="sxs-lookup"><span data-stu-id="4e761-116">Therefore, it is important to understand how XPath data types are implemented.</span></span> <span data-ttu-id="4e761-117">有关 XPath 语言规范，XML 路径语言 (XPath) 版本 1.0 W3C 建议的建议8年10月1999，可在 W3C 网站上找到 http://www.w3.org/TR/1999/PR-xpath-19991008.html 。</span><span class="sxs-lookup"><span data-stu-id="4e761-117">The XPath language specification, XML Path Language (XPath) version 1.0 W3C Proposed Recommendation 8 October 1999, can be found at the W3C Web site at http://www.w3.org/TR/1999/PR-xpath-19991008.html.</span></span>  
  
 <span data-ttu-id="4e761-118">XPath 运算符分为四个类别：</span><span class="sxs-lookup"><span data-stu-id="4e761-118">XPath operators are divided into four categories:</span></span>  
  
-   <span data-ttu-id="4e761-119">布尔运算符（and、or）</span><span class="sxs-lookup"><span data-stu-id="4e761-119">Boolean operators (and, or)</span></span>  
  
-   <span data-ttu-id="4e761-120">关系运算符 (\<, > ， \<=, > =) </span><span class="sxs-lookup"><span data-stu-id="4e761-120">Relational operators (\<, >, \<=, >=)</span></span>  
  
-   <span data-ttu-id="4e761-121">相等运算符（=、!=）</span><span class="sxs-lookup"><span data-stu-id="4e761-121">Equality operators (=, !=)</span></span>  
  
-   <span data-ttu-id="4e761-122">算术运算符（+、-、\*、div、mod）</span><span class="sxs-lookup"><span data-stu-id="4e761-122">Arithmetic operators (+, -, \*, div, mod)</span></span>  
  
 <span data-ttu-id="4e761-123">每个运算符类别都以不同方式转换其操作数。</span><span class="sxs-lookup"><span data-stu-id="4e761-123">Each category of operator converts its operands differently.</span></span> <span data-ttu-id="4e761-124">XPath 运算符根据需要隐式转换其操作数。</span><span class="sxs-lookup"><span data-stu-id="4e761-124">XPath operators implicitly convert their operands if necessary.</span></span> <span data-ttu-id="4e761-125">算术运算符将其操作数转换为 `number`，并且产生数值。</span><span class="sxs-lookup"><span data-stu-id="4e761-125">Arithmetic operators convert their operands to `number`, and result in a number value.</span></span> <span data-ttu-id="4e761-126">布尔运算符将其操作数转换为 `boolean`，并且产生布尔值。</span><span class="sxs-lookup"><span data-stu-id="4e761-126">Boolean operators convert their operands to `boolean`, and result in a Boolean value.</span></span> <span data-ttu-id="4e761-127">关系运算符和相等运算符产生布尔值。</span><span class="sxs-lookup"><span data-stu-id="4e761-127">Relational operators and equality operators result in a Boolean value.</span></span> <span data-ttu-id="4e761-128">但是，根据其操作数的原始数据类型，这两种运算符具有不同的转换规则，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="4e761-128">However, they have different conversion rules depending on the original data types of their operands, as shown in this table.</span></span>  
  
|<span data-ttu-id="4e761-129">操作数</span><span class="sxs-lookup"><span data-stu-id="4e761-129">Operand</span></span>|<span data-ttu-id="4e761-130">关系运算符</span><span class="sxs-lookup"><span data-stu-id="4e761-130">Relational operator</span></span>|<span data-ttu-id="4e761-131">相等运算符</span><span class="sxs-lookup"><span data-stu-id="4e761-131">Equality operator</span></span>|  
|-------------|-------------------------|-----------------------|  
|<span data-ttu-id="4e761-132">这两种操作数均为节点集。</span><span class="sxs-lookup"><span data-stu-id="4e761-132">Both operands are node-sets.</span></span>|<span data-ttu-id="4e761-133">当且仅当在一个集合中存在某一节点并且在第二个集合中存在某一节点时为 TRUE，这样，其 `string` 值的比较为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="4e761-133">TRUE if and only if there is a node in one set and a node in the second set such that the comparison of their `string` values is TRUE.</span></span>|<span data-ttu-id="4e761-134">相同.</span><span class="sxs-lookup"><span data-stu-id="4e761-134">Same.</span></span>|  
|<span data-ttu-id="4e761-135">一个是节点集，另一个是 `string`。</span><span class="sxs-lookup"><span data-stu-id="4e761-135">One is a node-set, the other a `string`.</span></span>|<span data-ttu-id="4e761-136">当且仅当在该节点集中存在某一节点时为 TRUE，这样在转换为 `number` 时，它与转换为 `string` 的 `number` 的比较为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="4e761-136">TRUE if and only if there is a node in the node-set such that when converted to `number`, the comparison of it with the `string` converted to `number` is TRUE.</span></span>|<span data-ttu-id="4e761-137">当且仅当在该节点集中存在某一节点时为 TRUE，这样在转换为 `string` 时，它与 `string` 的比较为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="4e761-137">TRUE if and only if there is a node in the node-set such that when converted to `string`, the comparison of it with the `string` is TRUE.</span></span>|  
|<span data-ttu-id="4e761-138">一个是节点集，另一个是 `number`。</span><span class="sxs-lookup"><span data-stu-id="4e761-138">One is a node-set, the other a `number`.</span></span>|<span data-ttu-id="4e761-139">当且仅当在该节点集中存在某一节点时为 TRUE，这样在转换为 `number` 时，它与 `number` 的比较为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="4e761-139">TRUE if and only if there is a node in the node-set such that when converted to `number`, the comparison of it with the `number` is TRUE.</span></span>|<span data-ttu-id="4e761-140">相同.</span><span class="sxs-lookup"><span data-stu-id="4e761-140">Same.</span></span>|  
|<span data-ttu-id="4e761-141">一个是节点集，另一个是 `boolean`。</span><span class="sxs-lookup"><span data-stu-id="4e761-141">One is a node-set, the other a `boolean`.</span></span>|<span data-ttu-id="4e761-142">当且仅当在该节点集中存在某一节点时为 TRUE，这样在转换为 `boolean` 然后转换为 `number` 时，它与转换为 `boolean` 的 `number` 的比较为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="4e761-142">TRUE if and only if there is a node in the node-set such that when converted to `boolean` and then to `number`, the comparison of it with the `boolean` converted to `number` is TRUE.</span></span>|<span data-ttu-id="4e761-143">当且仅当在该节点集中存在某一节点时为 TRUE，这样在转换为 `boolean` 时，它与 `boolean` 的比较为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="4e761-143">TRUE if and only if there is a node in the node-set such that when converted to `boolean`, the comparison of it with the `boolean` is TRUE.</span></span>|  
|<span data-ttu-id="4e761-144">两者均不是节点集。</span><span class="sxs-lookup"><span data-stu-id="4e761-144">Neither is a node-set.</span></span>|<span data-ttu-id="4e761-145">将两个操作数均转换为 `number`，然后进行比较。</span><span class="sxs-lookup"><span data-stu-id="4e761-145">Convert both operands to `number` and then compare.</span></span>|<span data-ttu-id="4e761-146">将两个操作数均转换为常见类型，然后进行比较。</span><span class="sxs-lookup"><span data-stu-id="4e761-146">Convert both operands to a common type and then compare.</span></span> <span data-ttu-id="4e761-147">转换为 `boolean`（如果其中一个是 `boolean`）或转换为 `number`（如果其中一个是 `number`）；否则，转换为 `string`。</span><span class="sxs-lookup"><span data-stu-id="4e761-147">Convert to `boolean` if either is `boolean`, `number` if either is `number`; otherwise, convert to `string`.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="4e761-148">因为 XPath 关系运算符始终将其操作数转换为 `number`，所以，不可能执行 `string` 比较。</span><span class="sxs-lookup"><span data-stu-id="4e761-148">Because XPath relational operators always convert their operands to `number`, `string` comparisons are not possible.</span></span> <span data-ttu-id="4e761-149">为了包括日期比较，SQL Server 2000 向 XPath 规范提供以下变化形式：在关系运算符将 `string` 与 `string` 进行比较、将节点集与 `string` 进行比较或将字符串值的节点集与字符串值的节点集进行比较时，执行 `string` 比较（而非 `number` 比较）。</span><span class="sxs-lookup"><span data-stu-id="4e761-149">To include date comparisons, SQL Server 2000 offers this variation to the XPath specification: When a relational operator compares a `string` to a `string`, a node-set to a `string`, or a string-valued node-set to a string-valued node-set, a `string` comparison (not a `number` comparison) is performed.</span></span>  
  
## <a name="node-set-conversions"></a><span data-ttu-id="4e761-150">节点集转换</span><span class="sxs-lookup"><span data-stu-id="4e761-150">Node-Set Conversions</span></span>  
 <span data-ttu-id="4e761-151">节点集转换并非始终都是直观的。</span><span class="sxs-lookup"><span data-stu-id="4e761-151">Node-set conversions are not always intuitive.</span></span> <span data-ttu-id="4e761-152">一个节点集通过只取该节点集中第一个节点的字符串值，转换为 `string`。</span><span class="sxs-lookup"><span data-stu-id="4e761-152">A node-set is converted to a `string` by taking the string value of only the first node in the set.</span></span> <span data-ttu-id="4e761-153">通过将某一节点集转换为 `number`，然后将 `string` 转换为 `string`，将该节点集转换为 `number`。</span><span class="sxs-lookup"><span data-stu-id="4e761-153">A node-set is converted to `number` by converting it to `string`, and then converting `string` to `number`.</span></span> <span data-ttu-id="4e761-154">节点集将通过测试其是否存在，转换为 `boolean`。</span><span class="sxs-lookup"><span data-stu-id="4e761-154">A node-set is converted to `boolean` by testing for its existence.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4e761-155">不执行针对节点集的位置选择：例如，XPath 查询 `Customer[3]` 意味着第三个客户；但在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中不支持此类型的位置选择。</span><span class="sxs-lookup"><span data-stu-id="4e761-155">does not perform positional selection on node-sets: for example, the XPath query `Customer[3]` means the third customer; this type of positional selection is not supported in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4e761-156">因此，无法实现 XPath 规范所述的节点集到 `string` 转换或者节点集到 `number` 转换。</span><span class="sxs-lookup"><span data-stu-id="4e761-156">Therefore, the node-set-to-`string` or node-set-to-`number` conversions as described by the XPath specification are not implemented.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4e761-157">使用“任何”语义，而 XPath 规范指定“第一个”语义。</span><span class="sxs-lookup"><span data-stu-id="4e761-157">uses "any" semantics wherever the XPath specification specifies "first" semantics.</span></span> <span data-ttu-id="4e761-158">例如，根据 W3C XPath 规范，XPath 查询 `Order[OrderDetail/@UnitPrice > 10.0]` 会选择包含**单价**大于10.0 的第一个**OrderDetail**的订单。</span><span class="sxs-lookup"><span data-stu-id="4e761-158">For example, based on the W3C XPath specification, the XPath query `Order[OrderDetail/@UnitPrice > 10.0]` selects those orders with the first **OrderDetail** that has a **UnitPrice** greater than 10.0.</span></span> <span data-ttu-id="4e761-159">在中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，此 XPath 查询选择具有**单价**大于10.0 的所有**OrderDetail**的订单。</span><span class="sxs-lookup"><span data-stu-id="4e761-159">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this XPath query selects those orders with any **OrderDetail** that has a **UnitPrice** greater than 10.0.</span></span>  
  
 <span data-ttu-id="4e761-160">转换为 `boolean` 将产生存在测试；因此，XPath 查询 `Products[@Discontinued=true()]` 等效于 SQL 表达式“Products.Discontinued is not null”，而非 SQL 表达式“Products.Discontinued = 1”。</span><span class="sxs-lookup"><span data-stu-id="4e761-160">Conversion to `boolean` generates an existence test; therefore, the XPath query `Products[@Discontinued=true()]` is equivalent to the SQL expression "Products.Discontinued is not null", not the SQL expression "Products.Discontinued = 1".</span></span> <span data-ttu-id="4e761-161">若要使该查询等效于后一个 SQL 表达式，请首先将节点集转换为非 `boolean` 类型，如 `number`。</span><span class="sxs-lookup"><span data-stu-id="4e761-161">To make the query equivalent to the latter SQL expression, first convert the node-set to a non-`boolean` type, such as `number`.</span></span> <span data-ttu-id="4e761-162">例如 `Products[number(@Discontinued) = true()]`。</span><span class="sxs-lookup"><span data-stu-id="4e761-162">For example, `Products[number(@Discontinued) = true()]`.</span></span>  
  
 <span data-ttu-id="4e761-163">因为如果运算符对于节点集中任一节点为 TRUE，则大多数运算符均定义为 TRUE；所以，在节点集为空时，这些运算的计算结果始终为 FALSE。</span><span class="sxs-lookup"><span data-stu-id="4e761-163">Because most operators are defined to be TRUE if they are TRUE for any or one of the nodes in the node-set, these operations always evaluate to FALSE if the node-set is empty.</span></span> <span data-ttu-id="4e761-164">因此，如果 A 为空，则 `A = B` 和 `A != B` 均为 FALSE，并且 `not(A=B)` 和 `not(A!=B)` 均为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="4e761-164">Thus, if A is empty, both `A = B` and `A != B` are FALSE, and `not(A=B)` and `not(A!=B)` are TRUE.</span></span>  
  
 <span data-ttu-id="4e761-165">通常，如果数据库中某一列的值不是 `null`，则映射到该列的属性或元素将存在。</span><span class="sxs-lookup"><span data-stu-id="4e761-165">Usually, an attribute or element that maps to a column exists if the value of that column in the database is not `null`.</span></span> <span data-ttu-id="4e761-166">如果元素的任何子集存在，则映射到行的元素将存在。</span><span class="sxs-lookup"><span data-stu-id="4e761-166">Elements that map to rows exist if any of their children exist.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4e761-167">使用 `is-constant` 批注的元素始终存在。</span><span class="sxs-lookup"><span data-stu-id="4e761-167">Elements annotated with `is-constant` always exist.</span></span> <span data-ttu-id="4e761-168">因此，XPath 谓词不能用于 `is-constant` 元素。</span><span class="sxs-lookup"><span data-stu-id="4e761-168">Consequently, XPath predicates cannot be used on `is-constant` elements.</span></span>  
  
 <span data-ttu-id="4e761-169">在某一节点集转换为 `string` 或 `number` 时，在带批注的架构中检查其 XDR 类型（如果有）并且该类型用于确定该转换是否是必需的。</span><span class="sxs-lookup"><span data-stu-id="4e761-169">When a node-set is converted to `string` or `number`, its XDR type (if any) is inspected in the annotated schema and that type is used to determine the conversion that is required.</span></span>  
  
## <a name="mapping-xdr-data-types-to-xpath-data-types"></a><span data-ttu-id="4e761-170">将 XDR 数据类型映射到 XPath 数据类型</span><span class="sxs-lookup"><span data-stu-id="4e761-170">Mapping XDR Data Types to XPath Data Types</span></span>  
 <span data-ttu-id="4e761-171">节点的 XPath 数据类型从架构中的 XDR 数据类型派生，如下表所示 (节点**雇员 id**用于说明用途) 。</span><span class="sxs-lookup"><span data-stu-id="4e761-171">The XPath data type of a node is derived from the XDR data type in the schema, as shown in the following table (the node **EmployeeID** is used for illustrative purpose).</span></span>  
  
|<span data-ttu-id="4e761-172">XDR 数据类型</span><span class="sxs-lookup"><span data-stu-id="4e761-172">XDR data type</span></span>|<span data-ttu-id="4e761-173">等效</span><span class="sxs-lookup"><span data-stu-id="4e761-173">Equivalent</span></span><br /><br /> <span data-ttu-id="4e761-174">XPath 数据类型</span><span class="sxs-lookup"><span data-stu-id="4e761-174">XPath data type</span></span>|<span data-ttu-id="4e761-175">使用的 SQL Server 转换</span><span class="sxs-lookup"><span data-stu-id="4e761-175">SQL Server conversion used</span></span>|  
|-------------------|------------------------------------|--------------------------------|  
|<span data-ttu-id="4e761-176">Nonebin.base64bin.hex</span><span class="sxs-lookup"><span data-stu-id="4e761-176">Nonebin.base64bin.hex</span></span>|<span data-ttu-id="4e761-177">空值</span><span class="sxs-lookup"><span data-stu-id="4e761-177">N/A</span></span>|<span data-ttu-id="4e761-178">NoneEmployeeID</span><span class="sxs-lookup"><span data-stu-id="4e761-178">NoneEmployeeID</span></span>|  
|<span data-ttu-id="4e761-179">boolean</span><span class="sxs-lookup"><span data-stu-id="4e761-179">boolean</span></span>|<span data-ttu-id="4e761-180">boolean</span><span class="sxs-lookup"><span data-stu-id="4e761-180">boolean</span></span>|<span data-ttu-id="4e761-181">CONVERT(bit, EmployeeID)</span><span class="sxs-lookup"><span data-stu-id="4e761-181">CONVERT(bit, EmployeeID)</span></span>|  
|<span data-ttu-id="4e761-182">number、int、float、i1、i2、i4、i8、r4、r8、ui1、ui2、ui4、ui8</span><span class="sxs-lookup"><span data-stu-id="4e761-182">number, int, float,i1, i2, i4, i8,r4, r8ui1, ui2, ui4, ui8</span></span>|<span data-ttu-id="4e761-183">number</span><span class="sxs-lookup"><span data-stu-id="4e761-183">number</span></span>|<span data-ttu-id="4e761-184">CONVERT(float(53), EmployeeID)</span><span class="sxs-lookup"><span data-stu-id="4e761-184">CONVERT(float(53), EmployeeID)</span></span>|  
|<span data-ttu-id="4e761-185">id、idref、idrefsentity、entities、enumerationnotation、nmtoken、nmtokens、chardate、Timedate、Time.tz、string、uri、uuid</span><span class="sxs-lookup"><span data-stu-id="4e761-185">id, idref, idrefsentity, entities, enumerationnotation, nmtoken, nmtokens, chardate, Timedate, Time.tz, string, uri, uuid</span></span>|<span data-ttu-id="4e761-186">字符串</span><span class="sxs-lookup"><span data-stu-id="4e761-186">string</span></span>|<span data-ttu-id="4e761-187">CONVERT(nvarchar(4000), EmployeeID, 126)</span><span class="sxs-lookup"><span data-stu-id="4e761-187">CONVERT(nvarchar(4000), EmployeeID, 126)</span></span>|  
|<span data-ttu-id="4e761-188">fixed14.4</span><span class="sxs-lookup"><span data-stu-id="4e761-188">fixed14.4</span></span>|<span data-ttu-id="4e761-189">无（在 XPath 中没有等效于 fixed14.4 XDR 数据类型的数据类型）</span><span class="sxs-lookup"><span data-stu-id="4e761-189">N/A(There is no data type in XPath that is equivalent to the fixed14.4 XDR data type)</span></span>|<span data-ttu-id="4e761-190">CONVERT(money, EmployeeID)</span><span class="sxs-lookup"><span data-stu-id="4e761-190">CONVERT(money, EmployeeID)</span></span>|  
|<span data-ttu-id="4e761-191">date</span><span class="sxs-lookup"><span data-stu-id="4e761-191">date</span></span>|<span data-ttu-id="4e761-192">字符串</span><span class="sxs-lookup"><span data-stu-id="4e761-192">string</span></span>|<span data-ttu-id="4e761-193">LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)</span><span class="sxs-lookup"><span data-stu-id="4e761-193">LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)</span></span>|  
|<span data-ttu-id="4e761-194">time</span><span class="sxs-lookup"><span data-stu-id="4e761-194">time</span></span><br /><br /> <span data-ttu-id="4e761-195">time.tz</span><span class="sxs-lookup"><span data-stu-id="4e761-195">time.tz</span></span>|<span data-ttu-id="4e761-196">字符串</span><span class="sxs-lookup"><span data-stu-id="4e761-196">string</span></span>|<span data-ttu-id="4e761-197">SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)</span><span class="sxs-lookup"><span data-stu-id="4e761-197">SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)</span></span>|  
  
 <span data-ttu-id="4e761-198">日期和时间转换的设计目的是使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `datetime` 数据类型还是将值存储在数据库中 `string` 。</span><span class="sxs-lookup"><span data-stu-id="4e761-198">The date and time conversions are designed to work whether the value is stored in the database using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`datetime` data type or a `string`.</span></span> <span data-ttu-id="4e761-199">请注意， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `datetime` 数据类型不使用 `timezone` ，并且其精度小于 XML `time` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="4e761-199">Note that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`datetime` data type does not use `timezone` and has a smaller precision than the XML `time` data type.</span></span> <span data-ttu-id="4e761-200">若要包括 `timezone` 数据类型或附加的精度，请使用 `string` 类型在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中存储数据。</span><span class="sxs-lookup"><span data-stu-id="4e761-200">To include the `timezone` data type or additional precision, store the data in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using a `string` type.</span></span>  
  
 <span data-ttu-id="4e761-201">在某一节点从其 XDR 数据类型转换为 XPath 数据类型时，有时候可能需要执行附加的转换（从一个 XPath 数据类型转换为另一个 XPath 数据类型）。</span><span class="sxs-lookup"><span data-stu-id="4e761-201">When a node is converted from its XDR data type to the XPath data type, additional conversion is sometimes necessary (from one XPath data type to another XPath data type).</span></span> <span data-ttu-id="4e761-202">例如，请考虑下面的 XPath 查询：</span><span class="sxs-lookup"><span data-stu-id="4e761-202">For example, consider this XPath query:</span></span>  
  
```  
(@m + 3) = 4  
```  
  
 <span data-ttu-id="4e761-203">如果 @m 的 `fixed14.4` 数据类型为 xdr，则使用以下内容完成从 xdr 数据类型到 XPath 数据类型的转换：</span><span class="sxs-lookup"><span data-stu-id="4e761-203">If @m is of the `fixed14.4` XDR data type, the conversion from XDR data type to XPath data type is accomplished using:</span></span>  
  
```  
CONVERT(money, m)  
```  
  
 <span data-ttu-id="4e761-204">在此转换中，节点 `m` 从 `fixed14.4` 转换到 `money`。</span><span class="sxs-lookup"><span data-stu-id="4e761-204">In this conversion, the node `m` is converted from `fixed14.4` to `money`.</span></span> <span data-ttu-id="4e761-205">但如果添加值 3，则要求附加的转换：</span><span class="sxs-lookup"><span data-stu-id="4e761-205">However, adding the value of 3, requires additional conversion:</span></span>  
  
```  
CONVERT(float(CONVERT(money, m))  
```  
  
 <span data-ttu-id="4e761-206">该 XPath 表达式计算为：</span><span class="sxs-lookup"><span data-stu-id="4e761-206">The XPath expression is evaluated as:</span></span>  
  
```  
CONVERT(float(CONVERT(money, m)) + CONVERT(float(53), 3) = CONVERT(float(53), 3)  
```  
  
 <span data-ttu-id="4e761-207">如下表中所示，这一转换同样适用于其他 XPath 表达式（例如文字表达式或复合表达式）。</span><span class="sxs-lookup"><span data-stu-id="4e761-207">As shown in the following table, this is the same conversion that is applied for other XPath expressions (such as literals or compound expressions).</span></span>  
  
||||||  
|-|-|-|-|-|  
||<span data-ttu-id="4e761-208">X 未知</span><span class="sxs-lookup"><span data-stu-id="4e761-208">X is unknown</span></span>|<span data-ttu-id="4e761-209">X 是 `string`</span><span class="sxs-lookup"><span data-stu-id="4e761-209">X is `string`</span></span>|<span data-ttu-id="4e761-210">X 是 `number`</span><span class="sxs-lookup"><span data-stu-id="4e761-210">X is `number`</span></span>|<span data-ttu-id="4e761-211">X 是 `boolean`</span><span class="sxs-lookup"><span data-stu-id="4e761-211">X is `boolean`</span></span>|  
|<span data-ttu-id="4e761-212">string(X)</span><span class="sxs-lookup"><span data-stu-id="4e761-212">string(X)</span></span>|<span data-ttu-id="4e761-213">CONVERT (nvarchar(4000), X, 126)</span><span class="sxs-lookup"><span data-stu-id="4e761-213">CONVERT (nvarchar(4000), X, 126)</span></span>|-|<span data-ttu-id="4e761-214">CONVERT (nvarchar(4000), X, 126)</span><span class="sxs-lookup"><span data-stu-id="4e761-214">CONVERT (nvarchar(4000), X, 126)</span></span>|<span data-ttu-id="4e761-215">CASE WHEN X THEN N'true' ELSE N'false' END</span><span class="sxs-lookup"><span data-stu-id="4e761-215">CASE WHEN X THEN N'true' ELSE N'false' END</span></span>|  
|<span data-ttu-id="4e761-216">number(X)</span><span class="sxs-lookup"><span data-stu-id="4e761-216">number(X)</span></span>|<span data-ttu-id="4e761-217">CONVERT (float(53), X)</span><span class="sxs-lookup"><span data-stu-id="4e761-217">CONVERT (float(53), X)</span></span>|<span data-ttu-id="4e761-218">CONVERT (float(53), X)</span><span class="sxs-lookup"><span data-stu-id="4e761-218">CONVERT (float(53), X)</span></span>|-|<span data-ttu-id="4e761-219">CASE WHEN X THEN 1 ELSE 0 END</span><span class="sxs-lookup"><span data-stu-id="4e761-219">CASE WHEN X THEN 1 ELSE 0 END</span></span>|  
|<span data-ttu-id="4e761-220">boolean(X)</span><span class="sxs-lookup"><span data-stu-id="4e761-220">boolean(X)</span></span>|-|<span data-ttu-id="4e761-221">LEN (X) > 0</span><span class="sxs-lookup"><span data-stu-id="4e761-221">LEN(X) > 0</span></span>|<span data-ttu-id="4e761-222">X != 0</span><span class="sxs-lookup"><span data-stu-id="4e761-222">X != 0</span></span>|-|  
  
## <a name="examples"></a><span data-ttu-id="4e761-223">示例</span><span class="sxs-lookup"><span data-stu-id="4e761-223">Examples</span></span>  
  
### <a name="a-convert-a-data-type-in-an-xpath-query"></a><span data-ttu-id="4e761-224">A.</span><span class="sxs-lookup"><span data-stu-id="4e761-224">A.</span></span> <span data-ttu-id="4e761-225">在 XPath 查询中转换数据类型</span><span class="sxs-lookup"><span data-stu-id="4e761-225">Convert a data type in an XPath query</span></span>  
 <span data-ttu-id="4e761-226">在针对带批注的 XSD 架构指定的以下 XPath 查询中，该查询选择**雇员 id**属性值为 E-1 的所有**雇员**节点，其中，"E-" 是使用批注指定的前缀 `sql:id-prefix` 。</span><span class="sxs-lookup"><span data-stu-id="4e761-226">In the following XPath query specified against an annotated XSD schema, the query selects all **Employee** nodes with the **EmployeeID** attribute value of E-1, where "E-" is the prefix specified using the `sql:id-prefix` annotation.</span></span>  
  
 `Employee[@EmployeeID="E-1"]`  
  
 <span data-ttu-id="4e761-227">该查询中的谓词等效于 SQL 表达式：</span><span class="sxs-lookup"><span data-stu-id="4e761-227">The predicate in the query is equivalent to the SQL expression:</span></span>  
  
 `N'E-' + CONVERT(nvarchar(4000), Employees.EmployeeID, 126) = N'E-1'`  
  
 <span data-ttu-id="4e761-228">因为**雇员 id**是 `id` `idref` `idrefs` `nmtoken` XSD 架构中) 数据类型值的 (、、、等之一， `nmtokens` 所以使用前面所述的转换规则将**雇员 id**转换为 `string` XPath 数据类型。</span><span class="sxs-lookup"><span data-stu-id="4e761-228">Because **EmployeeID** is one of the `id` (`idref`, `idrefs`, `nmtoken`, `nmtokens`, and so on) data type values in the XSD schema, **EmployeeID** is converted to the `string` XPath data type using the conversion rules described previously.</span></span>  
  
 `CONVERT(nvarchar(4000), Employees.EmployeeID, 126)`  
  
 <span data-ttu-id="4e761-229">“E-”前缀将添加到字符串，然后结果将与 `N'E-1'` 进行比较。</span><span class="sxs-lookup"><span data-stu-id="4e761-229">The "E-" prefix is added to the string, and the result is then compared with `N'E-1'`.</span></span>  
  
### <a name="b-perform-several-data-type-conversions-in-an-xpath-query"></a><span data-ttu-id="4e761-230">B.</span><span class="sxs-lookup"><span data-stu-id="4e761-230">B.</span></span> <span data-ttu-id="4e761-231">在 XPath 查询中执行若干数据类型转换</span><span class="sxs-lookup"><span data-stu-id="4e761-231">Perform several data type conversions in an XPath query</span></span>  
 <span data-ttu-id="4e761-232">考虑以下根据带批注的 XSD 架构指定的 XPath 查询：`OrderDetail[@UnitPrice * @OrderQty > 98]`</span><span class="sxs-lookup"><span data-stu-id="4e761-232">Consider this XPath query specified against an annotated XSD schema: `OrderDetail[@UnitPrice * @OrderQty > 98]`</span></span>  
  
 <span data-ttu-id="4e761-233">此 XPath 查询返回 **\<OrderDetail>** 满足该谓词的所有元素 `@UnitPrice * @OrderQty > 98` 。</span><span class="sxs-lookup"><span data-stu-id="4e761-233">This XPath query returns all the **\<OrderDetail>** elements satisfying the predicate `@UnitPrice * @OrderQty > 98`.</span></span> <span data-ttu-id="4e761-234">如果使用**UnitPrice** `fixed14.4` 带批注的架构中的数据类型对单价进行批注，则此谓词等效于 SQL 表达式：</span><span class="sxs-lookup"><span data-stu-id="4e761-234">If the **UnitPrice** is annotated with a `fixed14.4` data type in the annotated schema, this predicate is equivalent to the SQL expression:</span></span>  
  
 `CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice)) * CONVERT(float(53), OrderDetail.OrderQty) > CONVERT(float(53), 98)`  
  
 <span data-ttu-id="4e761-235">在 XPath 查询中转换值时，第一个转换将 XDR 数据类型转换为 XPath 数据类型。</span><span class="sxs-lookup"><span data-stu-id="4e761-235">In converting the values in the XPath query, the first conversion converts the XDR data type to the XPath data type.</span></span> <span data-ttu-id="4e761-236">因为 "**单价**" 的 XSD 数据类型是 `fixed14.4` ，如上表中所述，这是使用的第一个转换：</span><span class="sxs-lookup"><span data-stu-id="4e761-236">Because the XSD data type of **UnitPrice** is `fixed14.4`, as described in the previous table, this is the first conversion that is used:</span></span>  
  
```  
CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 <span data-ttu-id="4e761-237">因为算术运算符将其操作数转换为 `number` XPath 数据类型，所以，第二个转换（从一个 XPath 数据类型到另一个 XPath 数据类型）将应用于其值转换为 `float(53)` 的情况（`float(53)` 类似于 XPath `number` 数据类型）：</span><span class="sxs-lookup"><span data-stu-id="4e761-237">Because the arithmetic operators convert their operands to the `number` XPath data type, the second conversion (from one XPath data type to another XPath data type) is applied in which the value is converted to `float(53)` (`float(53)` is close to the XPath `number` data type):</span></span>  
  
```  
CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 <span data-ttu-id="4e761-238">假设**orderqty**特性没有 XSD 数据类型，则在单个转换中将**orderqty**转换为 `number` XPath 数据类型：</span><span class="sxs-lookup"><span data-stu-id="4e761-238">Assuming the **OrderQty** attribute has no XSD data type, **OrderQty** is converted to a `number` XPath data type in a single conversion:</span></span>  
  
```  
CONVERT(float(53), OrderDetail.OrderQty)  
```  
  
 <span data-ttu-id="4e761-239">与此类似，值 98 将转换为 `number` XPath 数据类型：</span><span class="sxs-lookup"><span data-stu-id="4e761-239">Similarly, the value 98 is converted to the `number` XPath data type:</span></span>  
  
```  
CONVERT(float(53), 98)  
```  
  
> [!NOTE]  
>  <span data-ttu-id="4e761-240">如果在该架构中使用的 XSD 数据类型与数据库中的基础 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型不兼容，或者不可能执行 XPath 数据类型转换，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可能会返回错误。</span><span class="sxs-lookup"><span data-stu-id="4e761-240">If the XSD data type used in the schema is incompatible with the underlying [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type in the database, or if an impossible XPath data type conversion is performed, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] may return an error.</span></span> <span data-ttu-id="4e761-241">例如，如果为 "**雇员 id** " 属性加 `id-prefix` 上批注批注，则 XPath 将 `Employee[@EmployeeID=1]` 生成一个错误，因为**雇员 id**具有 `id-prefix` 批注，无法转换为 `number` 。</span><span class="sxs-lookup"><span data-stu-id="4e761-241">For example, if the **EmployeeID** attribute is annotated with `id-prefix` annotation, the XPath `Employee[@EmployeeID=1]` generates an error, because **EmployeeID** has the `id-prefix` annotation and cannot be converted to `number`.</span></span>  
  
  
