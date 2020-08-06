---
title: " (SQLXML 4.0) 使用 XPath 查询简介 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], about XPath queries
- W3C XPath specification
- XPath queries [SQLXML], functionality
ms.assetid: 01050a8e-0ccc-4a02-a4eb-b48be5c3f4f3
author: rothja
ms.author: jroth
ms.openlocfilehash: dd173f16ee0e97dac1c45039f75022bbf2dc0782
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577502"
---
# <a name="introduction-to-using-xpath-queries-sqlxml-40"></a><span data-ttu-id="308ba-102">XPath 查询使用简介 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="308ba-102">Introduction to Using XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="308ba-103">XML Path 语言 (XPath) 查询可以指定作为 URL 的一部分，或在模板内指定。</span><span class="sxs-lookup"><span data-stu-id="308ba-103">An XML Path Language (XPath) query can be specified as part of a URL or within a template.</span></span> <span data-ttu-id="308ba-104">映射架构决定生成的此片段的结构，值从数据库中进行检索。</span><span class="sxs-lookup"><span data-stu-id="308ba-104">The mapping schema determines the structure of this resulting fragment, and the values are retrieved from the database.</span></span> <span data-ttu-id="308ba-105">从概念上来说，此过程类似于使用 CREATE VIEW 语句创建视图，然后根据视图编写 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="308ba-105">This process is conceptually similar to creating views using the CREATE VIEW statement and writing SQL queries against them.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="308ba-106">若要了解 SQLXML 4.0 中的 XPath 查询，必须熟悉 XML 视图和相关的概念，如模板和映射架构。</span><span class="sxs-lookup"><span data-stu-id="308ba-106">To understand XPath queries in SQLXML 4.0, you must be familiar with XML views and related concepts such as templates and mapping schema.</span></span> <span data-ttu-id="308ba-107">有关详细信息，请参阅[批注的 XSD 架构简介 &#40;SQLXML 4.0&#41;](../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)，以及由万维网联合会 (W3C) 定义的 XPath 标准。</span><span class="sxs-lookup"><span data-stu-id="308ba-107">For more information, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md), and the XPath standard defined by the World Wide Web Consortium (W3C).</span></span>  
  
 <span data-ttu-id="308ba-108">XML 文档由多个节点构成，如元素节点、属性节点、文本节点等。</span><span class="sxs-lookup"><span data-stu-id="308ba-108">An XML document consists of nodes such as an element node, attribute node, text node, and so on.</span></span> <span data-ttu-id="308ba-109">例如，考虑以下 XML 文档：</span><span class="sxs-lookup"><span data-stu-id="308ba-109">For example, consider this XML document:</span></span>  
  
```  
<root>  
  <Customer cid= "C1" name="Janine" city="Issaquah">  
      <Order oid="O1" date="1/20/1996" amount="3.5" />  
      <Order oid="O2" date="4/30/1997" amount="13.4">Customer was  
          very satisfied</Order>  
   </Customer>  
   <Customer cid="C2" name="Ursula" city="Oelde" >  
      <Order oid="O3" date="7/14/1999" amount="100" note="Wrap it blue white red">  
          <Urgency>Important</Urgency>  
      </Order>  
      <Order oid="O4" date="1/20/1996" amount="10000"/>  
   </Customer>  
</root>  
```  
  
 <span data-ttu-id="308ba-110">在本文档中， **\<Customer>** 是元素节点， **cid**是属性节点， **"重要"** 是文本节点。</span><span class="sxs-lookup"><span data-stu-id="308ba-110">In this document, **\<Customer>** is an element node, **cid** is an attribute node, and **"Important"** is a text node.</span></span>  
  
 <span data-ttu-id="308ba-111">XPath 是图形导航语言，用于从 XML 文档中选择节点集。</span><span class="sxs-lookup"><span data-stu-id="308ba-111">XPath is a graph navigation language used to select a set of nodes from an XML document.</span></span> <span data-ttu-id="308ba-112">每个 XPath 运算符根据前一个 XPath 运算符所选择的节点集来选择节点集。</span><span class="sxs-lookup"><span data-stu-id="308ba-112">Each XPath operator selects a node-set based on a node-set selected by a previous XPath operator.</span></span> <span data-ttu-id="308ba-113">例如，给定一组 **\<Customer>** 节点，XPath 可以选择 **\<Order>** **日期**属性值为 **"7/14/1999"** 的所有节点。</span><span class="sxs-lookup"><span data-stu-id="308ba-113">For example, given a set of **\<Customer>** nodes, XPath can select all **\<Order>** nodes with the **date** attribute value of **"7/14/1999"**.</span></span> <span data-ttu-id="308ba-114">生成的节点集包含订单日期为 7/14/1999 的所有订单。</span><span class="sxs-lookup"><span data-stu-id="308ba-114">The resulting node-set contains all the orders with order date 7/14/1999.</span></span>  
  
 <span data-ttu-id="308ba-115">万维网联盟 (W3C) 将 XPath 语言规定为标准导航语言。</span><span class="sxs-lookup"><span data-stu-id="308ba-115">The XPath language is defined by the World Wide Web Consortium (W3C) as a standard navigation language.</span></span> <span data-ttu-id="308ba-116">SQLXML 4.0 实现了位于的 W3C XPath 规范的子集 http://www.w3.org/TR/1999/PR-xpath-19991008.html 。</span><span class="sxs-lookup"><span data-stu-id="308ba-116">SQLXML 4.0 implements a subset of the W3C XPath specification, which is located at http://www.w3.org/TR/1999/PR-xpath-19991008.html.</span></span>  
  
 <span data-ttu-id="308ba-117">以下是 W3C XPath 实现与 SQLXML 4.0 实现之间的主要差异。</span><span class="sxs-lookup"><span data-stu-id="308ba-117">The following are key differences between the W3C XPath implementation and the SQLXML 4.0 implementation.</span></span>  
  
-   <span data-ttu-id="308ba-118">**根查询**</span><span class="sxs-lookup"><span data-stu-id="308ba-118">**Root queries**</span></span>  
  
     <span data-ttu-id="308ba-119">SQLXML 4.0 不支持根查询 (/)。</span><span class="sxs-lookup"><span data-stu-id="308ba-119">SQLXML 4.0 does not support the root query (/).</span></span> <span data-ttu-id="308ba-120">每个 XPath 查询必须在架构的顶级开始 **\<ElementType>** 。</span><span class="sxs-lookup"><span data-stu-id="308ba-120">Every XPath query must begin at a top-level **\<ElementType>** in the schema.</span></span>  
  
-   <span data-ttu-id="308ba-121">**报告错误**</span><span class="sxs-lookup"><span data-stu-id="308ba-121">**Reporting errors**</span></span>  
  
     <span data-ttu-id="308ba-122">W3C XPath 规范定义了无错误条件。</span><span class="sxs-lookup"><span data-stu-id="308ba-122">The W3C XPath specification defines no error conditions.</span></span> <span data-ttu-id="308ba-123">选择任意节点失败的 XPath 查询将返回空节点集。</span><span class="sxs-lookup"><span data-stu-id="308ba-123">XPath queries that fail to select any nodes return an empty node-set.</span></span> <span data-ttu-id="308ba-124">在 SQLXML 4.0 中，查询可能返回多种类型的错误消息。</span><span class="sxs-lookup"><span data-stu-id="308ba-124">In SQLXML 4.0, a query can return many types of error messages.</span></span>  
  
-   <span data-ttu-id="308ba-125">**文档顺序**</span><span class="sxs-lookup"><span data-stu-id="308ba-125">**Document order**</span></span>  
  
     <span data-ttu-id="308ba-126">在 SQLXML 4.0 中，文档顺序并不总是确定的。</span><span class="sxs-lookup"><span data-stu-id="308ba-126">In SQLXML 4.0, document order is not always determined.</span></span> <span data-ttu-id="308ba-127">因此，无法实现使用文档顺序（如 `following`）的数值谓词和轴。</span><span class="sxs-lookup"><span data-stu-id="308ba-127">Therefore, numeric predicates and axes that use document order (such as `following`) are not implemented.</span></span>  
  
     <span data-ttu-id="308ba-128">缺少文档顺序还表示，只有在节点映射到单行中的单列时，才能计算该节点的字符串值。</span><span class="sxs-lookup"><span data-stu-id="308ba-128">The lack of document order also means that the string value of a node can be evaluated only when that node maps to a single column in a single row.</span></span> <span data-ttu-id="308ba-129">包含子元素的元素或 IDREFS 或 NMTOKENS 节点无法转换为字符串。</span><span class="sxs-lookup"><span data-stu-id="308ba-129">An element with child elements or an IDREFS or NMTOKENS node cannot be converted to string.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="308ba-130">在某些情况下，`key-fields` 批注或 `relationship` 批注中的关键字可以生成确定的文档顺序。</span><span class="sxs-lookup"><span data-stu-id="308ba-130">In some cases, the `key-fields` annotation or keys from the `relationship` annotation can result in a deterministic document order.</span></span> <span data-ttu-id="308ba-131">但是，这并不是这些批注的主要用途。有关详细信息，请参阅[使用 sql：键字段标识键列 &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)并[使用 sql： relationship &#40;SQLXML 4.0&#41;指定关系](../sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="308ba-131">However, this is not the primary use of these annotations For more information, see [Identifying Key Columns Using sql:key-fields &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md) and [Specifying Relationships Using sql:relationship &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md).</span></span>  
  
-   <span data-ttu-id="308ba-132">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="308ba-132">**Data types**</span></span>  
  
     <span data-ttu-id="308ba-133">SQLXML 4.0 在实现 XPath `string`、`number` 和 `boolean` 数据类型时存在局限性。</span><span class="sxs-lookup"><span data-stu-id="308ba-133">SQLXML 4.0 has limitations in implementing the XPath `string`, `number`, and `boolean` data types.</span></span> <span data-ttu-id="308ba-134">有关详细信息，请参阅[&#40;SQLXML 4.0&#41;的 XPath 数据类型](xpath-data-types-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="308ba-134">For more information, see [XPath Data Types &#40;SQLXML 4.0&#41;](xpath-data-types-sqlxml-4-0.md).</span></span>  
  
-   <span data-ttu-id="308ba-135">**叉积查询**</span><span class="sxs-lookup"><span data-stu-id="308ba-135">**Cross-product queries**</span></span>  
  
     <span data-ttu-id="308ba-136">SQLXML 4.0 不支持叉积 XPath 查询，如 `Customers[Order/@OrderDate=Order/@ShipDate]`。</span><span class="sxs-lookup"><span data-stu-id="308ba-136">SQLXML 4.0 does not support cross-product XPath queries, such as `Customers[Order/@OrderDate=Order/@ShipDate]`.</span></span> <span data-ttu-id="308ba-137">此查询用于选择其任意订单的 OrderDate 等于任意订单的 ShipDate 的所有客户。</span><span class="sxs-lookup"><span data-stu-id="308ba-137">This query selects all Customers with any Order for which the OrderDate equals the ShipDate of any Order.</span></span>  
  
     <span data-ttu-id="308ba-138">不过，SQLXML 4.0 支持诸如 `Customer[Order[@OrderDate=@ShippedDate]]` 的查询，此查询用于选择其任意订单的 OrderDate 等于其 ShipDate 的客户。</span><span class="sxs-lookup"><span data-stu-id="308ba-138">However, SQLXML 4.0 does support queries such as `Customer[Order[@OrderDate=@ShippedDate]]`, which selects Customers with any Order for which the OrderDate equals its ShipDate.</span></span>  
  
-   <span data-ttu-id="308ba-139">**错误处理和安全性**</span><span class="sxs-lookup"><span data-stu-id="308ba-139">**Error handling and security**</span></span>  
  
     <span data-ttu-id="308ba-140">根据所用架构和 XPath 查询表达式的不同，[!INCLUDE[tsql](../../includes/tsql-md.md)] 错误可以在某些条件下向用户公开。</span><span class="sxs-lookup"><span data-stu-id="308ba-140">Depending on the schema and XPath query expression that are used, [!INCLUDE[tsql](../../includes/tsql-md.md)] errors could be exposed to users under certain conditions.</span></span>  
  
 <span data-ttu-id="308ba-141">以下部分中的表格详细列出了 SQLXML 4.0 中的 XPath 查询实现与 W3C 规范在这些方面的不同之处。</span><span class="sxs-lookup"><span data-stu-id="308ba-141">The tables in the following sections provide details about how the implementation of XPath queries in SQLXML 4.0 differs from the W3C specification in these areas.</span></span>  
  
## <a name="supported-functionality"></a><span data-ttu-id="308ba-142">支持的功能</span><span class="sxs-lookup"><span data-stu-id="308ba-142">Supported Functionality</span></span>  
 <span data-ttu-id="308ba-143">下表显示了 SQLXML 4.0 中实现的 XPath 语言功能。</span><span class="sxs-lookup"><span data-stu-id="308ba-143">The following table shows the features of the XPath language that are implemented in SQLXML 4.0.</span></span>  
  
|<span data-ttu-id="308ba-144">功能</span><span class="sxs-lookup"><span data-stu-id="308ba-144">Feature</span></span>|<span data-ttu-id="308ba-145">项</span><span class="sxs-lookup"><span data-stu-id="308ba-145">Item</span></span>|<span data-ttu-id="308ba-146">示例查询链接</span><span class="sxs-lookup"><span data-stu-id="308ba-146">Link to sample queries</span></span>|  
|-------------|----------|----------------------------|  
|<span data-ttu-id="308ba-147">Axes</span><span class="sxs-lookup"><span data-stu-id="308ba-147">Axes</span></span>|<span data-ttu-id="308ba-148">`attribute`、`child`、`parent` 和 `self` 轴</span><span class="sxs-lookup"><span data-stu-id="308ba-148">`attribute`, `child`, `parent`, and `self` axes</span></span>|[<span data-ttu-id="308ba-149">&#40;SQLXML 4.0&#41;在 XPath 查询中指定轴</span><span class="sxs-lookup"><span data-stu-id="308ba-149">Specifying Axes in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-axes-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="308ba-150">包含连续谓词和嵌套谓词的布尔值谓词</span><span class="sxs-lookup"><span data-stu-id="308ba-150">Boolean-valued predicates including successive and nested predicates</span></span>||[<span data-ttu-id="308ba-151">&#40;SQLXML 4.0&#41;在 XPath 查询中指定算术运算符</span><span class="sxs-lookup"><span data-stu-id="308ba-151">Specifying Arithmetic Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="308ba-152">所有关系运算符</span><span class="sxs-lookup"><span data-stu-id="308ba-152">All relational operators</span></span>|<span data-ttu-id="308ba-153">=、！ =、<、 \<=, > >=</span><span class="sxs-lookup"><span data-stu-id="308ba-153">=, !=, <, \<=, >, >=</span></span>|[<span data-ttu-id="308ba-154">&#40;SQLXML 4.0&#41;在 XPath 查询中指定关系运算符</span><span class="sxs-lookup"><span data-stu-id="308ba-154">Specifying Relational Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-relational-operators-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="308ba-155">算术运算符</span><span class="sxs-lookup"><span data-stu-id="308ba-155">Arithmetic operators</span></span>|<span data-ttu-id="308ba-156">+、-、\*、div</span><span class="sxs-lookup"><span data-stu-id="308ba-156">+, -, \*, div</span></span>|[<span data-ttu-id="308ba-157">&#40;SQLXML 4.0&#41;在 XPath 查询中指定算术运算符</span><span class="sxs-lookup"><span data-stu-id="308ba-157">Specifying Arithmetic Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="308ba-158">显式转换函数</span><span class="sxs-lookup"><span data-stu-id="308ba-158">Explicit conversion functions</span></span>|<span data-ttu-id="308ba-159">`number()`, `string()`, `Boolean()`</span><span class="sxs-lookup"><span data-stu-id="308ba-159">`number()`, `string()`, `Boolean()`</span></span>|[<span data-ttu-id="308ba-160">&#40;SQLXML 4.0&#41;在 XPath 查询中指定显式转换函数</span><span class="sxs-lookup"><span data-stu-id="308ba-160">Specifying Explicit Conversion Functions in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="308ba-161">布尔运算符</span><span class="sxs-lookup"><span data-stu-id="308ba-161">Boolean operators</span></span>|<span data-ttu-id="308ba-162">AND、OR</span><span class="sxs-lookup"><span data-stu-id="308ba-162">AND, OR</span></span>|[<span data-ttu-id="308ba-163">在 &#40;SQLXML 4.0&#41;的 XPath 查询中指定布尔运算符</span><span class="sxs-lookup"><span data-stu-id="308ba-163">Specifying Boolean Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-boolean-operators-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="308ba-164">布尔函数</span><span class="sxs-lookup"><span data-stu-id="308ba-164">Boolean functions</span></span>|<span data-ttu-id="308ba-165">`true()`, `false()`, `not()`</span><span class="sxs-lookup"><span data-stu-id="308ba-165">`true()`, `false()`, `not()`</span></span>|[<span data-ttu-id="308ba-166">&#40;SQLXML 4.0&#41;在 XPath 查询中指定布尔函数</span><span class="sxs-lookup"><span data-stu-id="308ba-166">Specifying Boolean Functions in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-boolean-functions-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="308ba-167">XPath 变量</span><span class="sxs-lookup"><span data-stu-id="308ba-167">XPath variables</span></span>||[<span data-ttu-id="308ba-168">在 &#40;SQLXML 4.0&#41;的 XPath 查询中指定 XPath 变量</span><span class="sxs-lookup"><span data-stu-id="308ba-168">Specifying XPath Variables in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-xpath-variables-in-xpath-queries-sqlxml-4-0.md)|  
  
## <a name="unsupported-functionality"></a><span data-ttu-id="308ba-169">不支持的功能</span><span class="sxs-lookup"><span data-stu-id="308ba-169">Unsupported Functionality</span></span>  
 <span data-ttu-id="308ba-170">下表显示了 SQLXML 4.0 中未实现的 XPath 语言功能。</span><span class="sxs-lookup"><span data-stu-id="308ba-170">The following table shows the features of the XPath language that are not implemented in SQLXML 4.0.</span></span>  
  
|<span data-ttu-id="308ba-171">功能</span><span class="sxs-lookup"><span data-stu-id="308ba-171">Feature</span></span>|<span data-ttu-id="308ba-172">项</span><span class="sxs-lookup"><span data-stu-id="308ba-172">Item</span></span>|  
|-------------|----------|  
|<span data-ttu-id="308ba-173">Axes</span><span class="sxs-lookup"><span data-stu-id="308ba-173">Axes</span></span>|<span data-ttu-id="308ba-174">`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`</span><span class="sxs-lookup"><span data-stu-id="308ba-174">`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`</span></span>|  
|<span data-ttu-id="308ba-175">数值谓词</span><span class="sxs-lookup"><span data-stu-id="308ba-175">Numeric-valued predicates</span></span>||  
|<span data-ttu-id="308ba-176">算术运算符</span><span class="sxs-lookup"><span data-stu-id="308ba-176">Arithmetic operators</span></span>|<span data-ttu-id="308ba-177">mod</span><span class="sxs-lookup"><span data-stu-id="308ba-177">mod</span></span>|  
|<span data-ttu-id="308ba-178">节点函数</span><span class="sxs-lookup"><span data-stu-id="308ba-178">Node functions</span></span>|<span data-ttu-id="308ba-179">`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`</span><span class="sxs-lookup"><span data-stu-id="308ba-179">`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`</span></span>|  
|<span data-ttu-id="308ba-180">字符串函数</span><span class="sxs-lookup"><span data-stu-id="308ba-180">String functions</span></span>|<span data-ttu-id="308ba-181">`string()`, `concat()`, `starts-with()`, `contains()`, `substring-before()`, `substring-after()`, `substring()`, `string-length()`, `normalize()`, `translate()`</span><span class="sxs-lookup"><span data-stu-id="308ba-181">`string()`, `concat()`, `starts-with()`, `contains()`, `substring-before()`, `substring-after()`, `substring()`, `string-length()`, `normalize()`, `translate()`</span></span>|  
|<span data-ttu-id="308ba-182">布尔函数</span><span class="sxs-lookup"><span data-stu-id="308ba-182">Boolean functions</span></span>|`lang()`|  
|<span data-ttu-id="308ba-183">数字函数</span><span class="sxs-lookup"><span data-stu-id="308ba-183">Numeric functions</span></span>|<span data-ttu-id="308ba-184">`sum()`, `floor()`, `ceiling()`, `round()`</span><span class="sxs-lookup"><span data-stu-id="308ba-184">`sum()`, `floor()`, `ceiling()`, `round()`</span></span>|  
|<span data-ttu-id="308ba-185">Union 运算符</span><span class="sxs-lookup"><span data-stu-id="308ba-185">Union operator</span></span>|<span data-ttu-id="308ba-186">&#124;</span><span class="sxs-lookup"><span data-stu-id="308ba-186">&#124;</span></span>|  
  
 <span data-ttu-id="308ba-187">在模板中指定 XPath 查询时，请注意以下行为：</span><span class="sxs-lookup"><span data-stu-id="308ba-187">When you specify XPath queries in a template, note the following behavior:</span></span>  
  
-   <span data-ttu-id="308ba-188">XPath 可以包含某些字符，如 < 或 & 在 XML (中具有特殊含义，模板是 XML 文档) 。</span><span class="sxs-lookup"><span data-stu-id="308ba-188">XPath can contain characters such as < or & that have special meanings in XML (and template is an XML document).</span></span> <span data-ttu-id="308ba-189">必须使用 XML & 编码对这些字符进行转义，或在 URL 中指定 XPath。</span><span class="sxs-lookup"><span data-stu-id="308ba-189">You must escape these characters using XML &-encoding, or specify the XPath in the URL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="308ba-190">另请参阅</span><span class="sxs-lookup"><span data-stu-id="308ba-190">See Also</span></span>  
 [<span data-ttu-id="308ba-191">在 SQLXML 4.0 中使用 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="308ba-191">Using XPath Queries in SQLXML 4.0</span></span>](using-xpath-queries-in-sqlxml-4-0.md)  
  
  
