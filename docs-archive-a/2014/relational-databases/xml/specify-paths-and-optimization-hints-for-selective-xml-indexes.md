---
title: 为选择性 XML 索引指定路径和优化提示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
ms.assetid: 486ee339-165b-4aeb-b760-d2ba023d7d0a
author: rothja
ms.author: jroth
ms.openlocfilehash: 1a9d683fe57d489fdb9922b53d2c5c6825835216
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691141"
---
# <a name="specify-paths-and-optimization-hints-for-selective-xml-indexes"></a><span data-ttu-id="ae9d3-102">为选择性 XML 索引指定路径和优化提示</span><span class="sxs-lookup"><span data-stu-id="ae9d3-102">Specify Paths and Optimization Hints for Selective XML Indexes</span></span>
  <span data-ttu-id="ae9d3-103">本主题介绍如何在创建或更改选择性 XML 索引时，如何指定要建立索引的节点路径以及用于索引的优化提示。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-103">This topic describes how to specify node paths to index and optimization hints for indexing when you create or alter selective XML indexes.</span></span>  
  
 <span data-ttu-id="ae9d3-104">您可以在以下语句之一中同时指定节点路径和优化提示：</span><span class="sxs-lookup"><span data-stu-id="ae9d3-104">You specify node paths and optimization hints at the same time in one of the following statements:</span></span>  
  
-   <span data-ttu-id="ae9d3-105">在 **CREATE** 语句的 **FOR** 子句中。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-105">In the **FOR** clause of a **CREATE** statement.</span></span> <span data-ttu-id="ae9d3-106">有关详细信息，请参阅 [CREATE SELECTIVE XML INDEX (Transact-SQL)](/sql/t-sql/statements/create-selective-xml-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-106">For more information, see [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql).</span></span>  
  
-   <span data-ttu-id="ae9d3-107">在 **ALTER** 语句的 **ADD** 子句中。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-107">In the **ADD** clause of an **ALTER** statement.</span></span> <span data-ttu-id="ae9d3-108">有关详细信息，请参阅 [ALTER INDEX（选择性 XML 索引）](../indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-108">For more information, see [ALTER INDEX &#40;Selective XML Indexes&#41;](../indexes/indexes.md).</span></span>  
  
 <span data-ttu-id="ae9d3-109">有关选择性 XML 索引的详细信息，请参阅 [选择性 XML 索引 (SXI)](../xml/selective-xml-indexes-sxi.md)。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-109">For more information about selective XML indexes, see [Selective XML Indexes &#40;SXI&#41;](../xml/selective-xml-indexes-sxi.md).</span></span>  
  
##  <a name="understanding-xquery-and-sql-server-types-in-untyped-xml"></a><a name="untyped"></a> <span data-ttu-id="ae9d3-110">了解非类型化 XML 中的 XQuery 和 SQL Server 类型</span><span class="sxs-lookup"><span data-stu-id="ae9d3-110">Understanding XQuery and SQL Server Types in Untyped XML</span></span>  
 <span data-ttu-id="ae9d3-111">选择性 XML 索引支持两种类型的系统：XQuery 类型和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 类型。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-111">Selective XML indexes support two type systems: XQuery types and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types.</span></span> <span data-ttu-id="ae9d3-112">已建立索引的路径可用于匹配 XQuery 表达式，或者用于匹配 XML 数据类型的 value() 方法的返回值。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-112">The indexed path can be used either to match an XQuery expression, or to match the return type of the value() method of the XML data type.</span></span>  
  
-   <span data-ttu-id="ae9d3-113">在未对要建立索引的路径加批注时，或者使用 XQUERY 关键字进行批注时，该路径匹配 XQuery 表达式。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-113">When a path to index is not annotated, or is annotated with the XQUERY keyword, the path matches an XQuery expression.</span></span> <span data-ttu-id="ae9d3-114">对于 XQUERY 批注的节点路径有两种变化形式：</span><span class="sxs-lookup"><span data-stu-id="ae9d3-114">There are two variations for XQUERY-annotated node paths:</span></span>  
  
    -   <span data-ttu-id="ae9d3-115">如果没有指定 XQUERY 关键字和 XQuery 数据类型，则使用默认映射。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-115">If you do not specify the XQUERY keyword and the XQuery data type, then default mappings are used.</span></span> <span data-ttu-id="ae9d3-116">通常，性能和存储并非最佳。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-116">Typically performance and storage are not optimal.</span></span>  
  
    -   <span data-ttu-id="ae9d3-117">如果指定 XQUERY 关键字和 XQuery 数据类型以及可选的其他优化提示，则您可以实现可能最佳的性能以及可能最高效的存储。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-117">If you specify the XQUERY keyword and the XQuery data type, and optionally other optimization hints, then you can achieve the best possible performance and the most efficient possible storage.</span></span> <span data-ttu-id="ae9d3-118">但是，转换可能会失败。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-118">However, a cast can fail.</span></span>  
  
-   <span data-ttu-id="ae9d3-119">在使用 SQL 关键字对要建立索引的路径加批注时，该路径匹配 XML 数据类型的 value() 方法的返回值。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-119">When a path to index is annotated with the SQL keyword, the path matches the return type of the value() method of the XML data type.</span></span> <span data-ttu-id="ae9d3-120">指定相应的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型，该数据类型是预期从 value() 方法的返回类型。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-120">Specify the appropriate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type, which is the return type that you expect from the value() method.</span></span>  
  
 <span data-ttu-id="ae9d3-121">在应用于 XML 数据类型的 value() 方法的 XQuery 表达式 XML 类型系统和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 类型系统之间存在细微的差异。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-121">There are subtle differences between the XQuery expressions XML type system and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type system applied to the value() method of the XML data type.</span></span> <span data-ttu-id="ae9d3-122">这些差异如下：</span><span class="sxs-lookup"><span data-stu-id="ae9d3-122">These differences include the following:</span></span>  
  
-   <span data-ttu-id="ae9d3-123">XQuery 类型系统知道尾随空格。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-123">The XQuery type system is aware of trailing spaces.</span></span> <span data-ttu-id="ae9d3-124">例如，根据 XQuery 类型语义，字符串“abc”和“abc ”不相等；而在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，这两个字符串是相等的。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-124">For example, according to XQuery type semantics, the strings "abc" and "abc " are not equal, while in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] these strings are equal.</span></span>  
  
-   <span data-ttu-id="ae9d3-125">XQuery 浮点数据类型支持 +/- 零和 +/- 无穷大的特殊值。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-125">XQuery floating point data types support special values of +/- zero and +/- infinity.</span></span> <span data-ttu-id="ae9d3-126">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 浮点数据类型中不支持这些特殊值。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-126">These special values are not supported in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] floating point data types.</span></span>  
  
### <a name="xquery-types-in-untyped-xml"></a><span data-ttu-id="ae9d3-127">非类型化 XML 中的 XQuery 类型</span><span class="sxs-lookup"><span data-stu-id="ae9d3-127">XQuery Types in Untyped XML</span></span>  
  
-   <span data-ttu-id="ae9d3-128">XQuery 类型匹配 XML 数据类型的所有方法（包括 value() 方法）中的 XQuery 表达式。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-128">XQuery types match XQuery expressions in all methods of the XML data type including the value() method.</span></span>  
  
-   <span data-ttu-id="ae9d3-129">XQuery 类型支持以下优化提示：node()、SINGLETON、DATA TYPE 和 MAXLENGTH。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-129">XQuery types support these optimization hints: node(), SINGLETON, DATA TYPE, and MAXLENGTH.</span></span>  
  
 <span data-ttu-id="ae9d3-130">对于针对非类型化 XML 的 XQuery 表达式，您可以在以下两个操作模式之间进行选择：</span><span class="sxs-lookup"><span data-stu-id="ae9d3-130">For XQuery expressions over untyped XML, you can choose between two modes of operation:</span></span>  
  
-   <span data-ttu-id="ae9d3-131">**默认的映射模式**。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-131">**Default mapping mode**.</span></span> <span data-ttu-id="ae9d3-132">在这个模式中，您在创建选择性 XML 索引时仅指定路径。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-132">In this mode, you specify only the path when creating a selective XML index.</span></span>  
  
-   <span data-ttu-id="ae9d3-133">**用户指定的映射模式**。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-133">**User-specified mapping mode**.</span></span> <span data-ttu-id="ae9d3-134">在这个模式中，您既指定路径，也指定可选的优化提示。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-134">In this mode, you specify both the path and optional optimization hints.</span></span>  
  
 <span data-ttu-id="ae9d3-135">默认映射模式使用一个保守的存储选项，这个选项始终是安全和一般性的。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-135">The default mapping mode uses a conservative storage option which is always safe and general.</span></span> <span data-ttu-id="ae9d3-136">该模式可以匹配任何表达式类型。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-136">It can match any expression type.</span></span> <span data-ttu-id="ae9d3-137">默认映射模式的一个限制就是逊色于最佳性能，因为需要增加运行时转换的数目，并且辅助索引不可用。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-137">A limitation of the default mapping mode is less than optimal performance, because an increased number of runtime casts are required, and secondary indexes are not available.</span></span>  
  
 <span data-ttu-id="ae9d3-138">下面是使用默认映射创建的一个选择性 XML 索引的示例。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-138">Here is an example of a selective XML index created with default mappings.</span></span> <span data-ttu-id="ae9d3-139">对于所有三个路径，使用默认节点类型 (**xs:untypedAtomic**) 和基数。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-139">For all three paths, the default node type (**xs:untypedAtomic**) and cardinality are used.</span></span>  
  
```sql  
CREATE SELECTIVE XML INDEX example_sxi_UX_default  
ON Tbl(xmlcol)  
FOR  
(  
mypath01 =  '/a/b',  
mypath02 = '/a/b/c',  
mypath03 = '/a/b/d'  
)  
```  
  
 <span data-ttu-id="ae9d3-140">通过用户指定的映射模式，您可以为节点指定类型和基数以便实现更好的性能。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-140">The user-specified mapping mode lets you specify a type and cardinality for the node to obtain better performance.</span></span> <span data-ttu-id="ae9d3-141">但是，这一性能的提升是通过放弃安全性（因为转换可能会失败）和一般性（因为只有指定的类型与选择性 XML 索引匹配）来实现的。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-141">However, this improved performance is achieved by giving up safety - because a cast can fail - and generality - because only the specified type is matched with the selective XML index.</span></span>  
  
 <span data-ttu-id="ae9d3-142">支持非类型化 XML 事例的 XQuery 类型包括：</span><span class="sxs-lookup"><span data-stu-id="ae9d3-142">The XQuery types supported for untyped XML case are:</span></span>  
  
-   <span data-ttu-id="ae9d3-143">**xs: boolean**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-143">**xs:boolean**</span></span>  
  
-   <span data-ttu-id="ae9d3-144">**xs:double**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-144">**xs:double**</span></span>  
  
-   <span data-ttu-id="ae9d3-145">**xs:string**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-145">**xs:string**</span></span>  
  
-   <span data-ttu-id="ae9d3-146">**xs:date**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-146">**xs:date**</span></span>  
  
-   <span data-ttu-id="ae9d3-147">**xs:time**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-147">**xs:time**</span></span>  
  
-   <span data-ttu-id="ae9d3-148">**xs:dateTime**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-148">**xs:dateTime**</span></span>  
  
 <span data-ttu-id="ae9d3-149">如果未指定该类型，则认为节点属于 **xs:untypedAtomic** 数据类型。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-149">If the type is not specified, the node is assumed to be of the **xs:untypedAtomic** data type.</span></span>  
  
 <span data-ttu-id="ae9d3-150">您可以优化以下方式中所示的选择性 XML 索引：</span><span class="sxs-lookup"><span data-stu-id="ae9d3-150">You can optimize the selective XML index shown in the following manner:</span></span>  
  
```sql  
CREATE SELECTIVE XML INDEX example_sxi_UX_optimized  
ON Tbl(xmlcol)  
FOR  
(  
mypath= '/a/b' as XQUERY 'node()',  
pathX = '/a/b/c' as XQUERY 'xs:double' SINGLETON,  
pathY = '/a/b/d' as XQUERY 'xs:string' MAXLENGTH(200) SINGLETON  
)  
-- mypath - Only the node value is needed; storage is saved.  
-- pathX - Performance is improved; secondary indexes are possible.  
-- pathY - Performance is improved; secondary indexes are possible; storage is saved.  
```  
  
### <a name="sql-server-types-in-untyped-xml"></a><span data-ttu-id="ae9d3-151">非类型化 XML 中的 SQL Server 类型</span><span class="sxs-lookup"><span data-stu-id="ae9d3-151">SQL Server Types in Untyped XML</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ae9d3-152">类型匹配 value() 方法的返回值。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-152">types match the return value of the value() method.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ae9d3-153">类型支持此优化提示：SINGLETON。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-153">types support this optimization hint: SINGLETON.</span></span>  
  
 <span data-ttu-id="ae9d3-154">对于返回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 类型的路径，必须指定某一类型。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-154">Specifying a type is mandatory for paths that return [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types.</span></span> <span data-ttu-id="ae9d3-155">使用您要在 value() 方法中使用的相同的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 类型。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-155">Use the same [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type that you would use in the value() method.</span></span>  
  
 <span data-ttu-id="ae9d3-156">请考虑下列查询：</span><span class="sxs-lookup"><span data-stu-id="ae9d3-156">Consider the following query:</span></span>  
  
```sql  
SELECT T.record,  
    T.xmldata.value('(/a/b/d)[1]', 'NVARCHAR(200)')  
FROM myXMLTable T  
```  
  
 <span data-ttu-id="ae9d3-157">该指定的查询从打包到 NVARCHAR(200) 数据类型中的路径 `/a/b/d` 返回一个值，因此，要为该节点指定的数据类型十分明显。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-157">The specified query returns a value from the path `/a/b/d` packed into an NVARCHAR(200) data type, so the data type to specify for the node is obvious.</span></span> <span data-ttu-id="ae9d3-158">但是，没有用于在非类型化 XML 中指定节点基数的架构。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-158">However there is no schema to specify the cardinality of the node in untyped XML.</span></span> <span data-ttu-id="ae9d3-159">若要指定节点 `d` 在其父节点 `b`下最多出现一次，请创建一个选择性 XML 索引，该索引使用 SINGLETON 优化提示，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ae9d3-159">To specify that node `d` appears at most once under its parent node `b`, create a selective XML index that uses the SINGLETON optimization hint as follows:</span></span>  
  
```sql  
CREATE SELECTIVE XML INDEX example_sxi_US  
ON Tbl(xmlcol)  
FOR  
(  
node1223 = '/a/b/d' as SQL NVARCHAR(200) SINGLETON  
)  
```  
  

  
##  <a name="understanding-selective-xml-index-support-for-typed-xml"></a><a name="typed"></a> <span data-ttu-id="ae9d3-160">了解对类型化 XML 的选择性 XML 索引支持</span><span class="sxs-lookup"><span data-stu-id="ae9d3-160">Understanding Selective XML Index support for typed XML</span></span>  
 <span data-ttu-id="ae9d3-161">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的类型化 XML 是与某一给定 XML 文档相关联的架构。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-161">Typed XML in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is a schema associated with a given XML document.</span></span> <span data-ttu-id="ae9d3-162">该架构定义文档的整体结构以及节点的类型。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-162">The schema defines overall document structure and types of nodes.</span></span> <span data-ttu-id="ae9d3-163">如果某一架构存在，则在用户提升路径时选择性 XML 索引将应用该架构结构，因此，无需为路径指定 XQUERY 类型。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-163">If a schema exists, Selective XML Index applies the schema structure when the user promotes paths, so there is no need to specify the XQUERY types for paths.</span></span>  
  
 <span data-ttu-id="ae9d3-164">选择性 XML 索引支持以下 XSD 类型：</span><span class="sxs-lookup"><span data-stu-id="ae9d3-164">Selective XML Index supports following XSD types:</span></span>  
  
-   <span data-ttu-id="ae9d3-165">**xs:anyUri**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-165">**xs:anyUri**</span></span>  
  
-   <span data-ttu-id="ae9d3-166">**xs: boolean**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-166">**xs:boolean**</span></span>  
  
-   <span data-ttu-id="ae9d3-167">**xs:date**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-167">**xs:date**</span></span>  
  
-   <span data-ttu-id="ae9d3-168">**xs:dateTime**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-168">**xs:dateTime**</span></span>  
  
-   <span data-ttu-id="ae9d3-169">**xs:day**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-169">**xs:day**</span></span>  
  
-   <span data-ttu-id="ae9d3-170">**xs:decimal**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-170">**xs:decimal**</span></span>  
  
-   <span data-ttu-id="ae9d3-171">**xs:double**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-171">**xs:double**</span></span>  
  
-   <span data-ttu-id="ae9d3-172">**xs:float**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-172">**xs:float**</span></span>  
  
-   <span data-ttu-id="ae9d3-173">**xs:int**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-173">**xs:int**</span></span>  
  
-   <span data-ttu-id="ae9d3-174">**xs:integer**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-174">**xs:integer**</span></span>  
  
-   <span data-ttu-id="ae9d3-175">**xs:language**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-175">**xs:language**</span></span>  
  
-   <span data-ttu-id="ae9d3-176">**xs:long**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-176">**xs:long**</span></span>  
  
-   <span data-ttu-id="ae9d3-177">**xs:name**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-177">**xs:name**</span></span>  
  
-   <span data-ttu-id="ae9d3-178">**xs:NCName**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-178">**xs:NCName**</span></span>  
  
-   <span data-ttu-id="ae9d3-179">**xs:negativeInteger**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-179">**xs:negativeInteger**</span></span>  
  
-   <span data-ttu-id="ae9d3-180">**xs:nmtoken**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-180">**xs:nmtoken**</span></span>  
  
-   <span data-ttu-id="ae9d3-181">**xs:nonNegativeInteger**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-181">**xs:nonNegativeInteger**</span></span>  
  
-   <span data-ttu-id="ae9d3-182">**xs:nonPositiveInteger**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-182">**xs:nonPositiveInteger**</span></span>  
  
-   <span data-ttu-id="ae9d3-183">**xs:positiveInteger**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-183">**xs:positiveInteger**</span></span>  
  
-   <span data-ttu-id="ae9d3-184">**xs:qname**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-184">**xs:qname**</span></span>  
  
-   <span data-ttu-id="ae9d3-185">**xs:short**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-185">**xs:short**</span></span>  
  
-   <span data-ttu-id="ae9d3-186">**xs:string**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-186">**xs:string**</span></span>  
  
-   <span data-ttu-id="ae9d3-187">**xs:time**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-187">**xs:time**</span></span>  
  
-   <span data-ttu-id="ae9d3-188">**xs:token**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-188">**xs:token**</span></span>  
  
-   <span data-ttu-id="ae9d3-189">**xs:unsignedByte**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-189">**xs:unsignedByte**</span></span>  
  
-   <span data-ttu-id="ae9d3-190">**xs:unsignedInt**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-190">**xs:unsignedInt**</span></span>  
  
-   <span data-ttu-id="ae9d3-191">**xs:unsignedLong**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-191">**xs:unsignedLong**</span></span>  
  
-   <span data-ttu-id="ae9d3-192">**xs:unsignedShort**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-192">**xs:unsignedShort**</span></span>  
  
 <span data-ttu-id="ae9d3-193">在对具有与其相关联的架构的文档创建选择性 XML 索引时，在创建或更改索引时指定 XQUERY 类型会返回错误。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-193">When Selective XML Index is created over a document that has schema associated with it, specifying a XQUERY type at index creation or altering returns an error.</span></span> <span data-ttu-id="ae9d3-194">用户可以在路径提升部分中使用 SQL 类型批注。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-194">The user can use SQL type annotations in the path promotion part.</span></span> <span data-ttu-id="ae9d3-195">该 SQL 类型必须是从该架构中定义的 XSD 类型的有效转换，否则将引发错误。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-195">The SQL type must be a valid conversion from the XSD type defined in the schema, or an error is thrown.</span></span> <span data-ttu-id="ae9d3-196">支持在 XSD 中具有足够的表示形式的几乎所有 SQL 类型，只有日期/时间类型除外。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-196">All SQL types that have adequate representation in XSD are supported, with an exception of date/time types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ae9d3-197">如果在选择性 XML 索引路径提升中指定的类型与 value() 方法返回值相同，则使用选择性索引。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-197">The selective index is used if the type specified in the Selective XML Index path promotion is the same as the value() method return value.</span></span>  
  
 <span data-ttu-id="ae9d3-198">下面的优化提示可用于类型化 XML 文档：</span><span class="sxs-lookup"><span data-stu-id="ae9d3-198">The following optimization hints can be used with typed XML documents:</span></span>  
  
-   <span data-ttu-id="ae9d3-199">node() 优化提示。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-199">node() optimization hint.</span></span>  
  
-   <span data-ttu-id="ae9d3-200">MAXLENGTH 优化提示可用于 xs:string 类型，以便缩短索引值。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-200">MAXLENGTH optimization hint can be used with xs:string types to shorten the indexed value.</span></span>  
  
 <span data-ttu-id="ae9d3-201">有关优化提示的详细信息，请参阅 [指定优化提示](#hints)。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-201">For more information about optimization hints, see [Specifying Optimization Hints](#hints).</span></span>  
  
##  <a name="specifying-paths"></a><a name="paths"></a> <span data-ttu-id="ae9d3-202">指定路径</span><span class="sxs-lookup"><span data-stu-id="ae9d3-202">Specifying Paths</span></span>  
 <span data-ttu-id="ae9d3-203">通过选择性 XML 索引，您可以从您预期要运行的查询相关的已存储 XML 数据仅对节点的子集建立索引。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-203">A selective XML index lets you index only a subset of nodes from the stored XML data that are relevant for the queries that you expect to run.</span></span> <span data-ttu-id="ae9d3-204">在相关节点的子集远小于 XML 文档中节点的总数时，选择性 XML 索引将仅存储相关节点。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-204">When the subset of relevant nodes is much smaller than the total number of nodes in the XML document, the selective XML index stores only the relevant nodes.</span></span> <span data-ttu-id="ae9d3-205">为了从选择性 XML 索引中受益，请标识要建立索引的正确的节点子集。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-205">To benefit from a selective XML index, identify the correct subset of nodes to index.</span></span>  
  
### <a name="choosing-the-nodes-to-index"></a><span data-ttu-id="ae9d3-206">选择要建立索引的节点</span><span class="sxs-lookup"><span data-stu-id="ae9d3-206">Choosing the nodes to index</span></span>  
 <span data-ttu-id="ae9d3-207">您可以使用以下两个简单的原则来标识要添加到选择性 XML 索引的正确的节点子集。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-207">You can use the following two simple principles to identify the correct subset of nodes to add to a selective XML index.</span></span>  
  
1.  <span data-ttu-id="ae9d3-208">**原则 1**：若要评估某一给定的 XQuery 表达式，请对需要检查的所有节点建立索引。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-208">**Principle 1**: To evaluate a given XQuery expression, index all nodes that you need to examine.</span></span>  
  
    -   <span data-ttu-id="ae9d3-209">对其本身或值用于 XQuery 表达式中的所有节点建立索引。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-209">Index all nodes whose existence or value is used in the XQuery expression.</span></span>  
  
    -   <span data-ttu-id="ae9d3-210">对应用了 XQuery 谓词的 XQuery 表达式中的所有节点建立索引。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-210">Index all nodes in the XQuery expression on which XQuery predicates are applied.</span></span>  
  
     <span data-ttu-id="ae9d3-211">请考虑以下简单查询，它针对本文中的 [示例 XML 文档](#sample) ：</span><span class="sxs-lookup"><span data-stu-id="ae9d3-211">Consider the following simple query over the [sample XML document](#sample) in this topic:</span></span>  
  
    ```sql  
    SELECT T.record FROM myXMLTable T  
    WHERE T.xmldata.exist('/a/b[./c = "43"]') = 1  
    ```  
  
     <span data-ttu-id="ae9d3-212">为了返回满足此查询的 XML 实例，选择性 XML 索引需要在每个 XML 实例中都检查两个节点：</span><span class="sxs-lookup"><span data-stu-id="ae9d3-212">In order to return the XML instances that satisfy this query, a selective XML index needs to examine two nodes in every XML instance:</span></span>  
  
    -   <span data-ttu-id="ae9d3-213">节点 `c`，因为其值用于 XQuery 表达式中。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-213">Node `c`, because its value is used in the XQuery expression.</span></span>  
  
    -   <span data-ttu-id="ae9d3-214">节点 `b`，因为在 XQuery 表达式中一个谓词应用于节点`b` 。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-214">Node `b`, because a predicate is applied over node`b` in the XQuery expression.</span></span>  
  
2.  <span data-ttu-id="ae9d3-215">**原则 2**：为了获得最佳性能，请为针对某一给定 XQuery 表达式进行求值所需的所有节点建立索引。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-215">**Principle 2**: For best performance, index all nodes that are required to evaluate a given XQuery expression.</span></span> <span data-ttu-id="ae9d3-216">如果您仅对其中某些节点建立索引，则选择性 XML 索引将改进只包含已建立索引的节点的子表达式的求值。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-216">If you index only some of the nodes, then the selective XML index improves the evaluation of sub-expressions that include only indexed nodes.</span></span>  
  
 <span data-ttu-id="ae9d3-217">为了提高上面所示的 SELECT 语句的性能，您可以创建以下选择性 XML 索引：</span><span class="sxs-lookup"><span data-stu-id="ae9d3-217">To improve the performance of the SELECT statement shown above, you can create the following selective XML index:</span></span>  
  
```sql  
CREATE SELECTIVE XML INDEX simple_sxi  
ON Tbl(xmlcol)  
FOR  
(  
    path123 =  '/a/b',  
    path124 =  '/a/b/c'  
)  
```  
  
### <a name="indexing-identical-paths"></a><span data-ttu-id="ae9d3-218">对完全相同的路径建立索引</span><span class="sxs-lookup"><span data-stu-id="ae9d3-218">Indexing identical paths</span></span>  
 <span data-ttu-id="ae9d3-219">您不能将基于不同路径名称的完全相同的路径提升为相同的数据类型。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-219">You cannot promote identical paths as the same data type under different path names.</span></span> <span data-ttu-id="ae9d3-220">例如，以下查询将会引发错误，因为 `pathOne` 和 `pathTwo` 完全相同：</span><span class="sxs-lookup"><span data-stu-id="ae9d3-220">For example, the following query raises an error, because `pathOne` and `pathTwo` are identical:</span></span>  
  
```sql  
CREATE SELECTIVE INDEX test_simple_sxi ON T1(xmlCol)  
FOR  
(  
    pathOne = 'book/authors/authorID' AS XQUERY 'xs:string',  
    pathTwo = 'book/authors/authorID' AS XQUERY 'xs:string'  
)  
```  
  
 <span data-ttu-id="ae9d3-221">但是，您可以将完全相同的路径提升为具有不同名称的不同数据类型。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-221">However, you can promote identical paths as different data types with different names.</span></span> <span data-ttu-id="ae9d3-222">例如，下面的查询现在是可接受的，因为数据类型不同：</span><span class="sxs-lookup"><span data-stu-id="ae9d3-222">For example, the following query is now acceptable, because the data types are different:</span></span>  
  
```sql  
CREATE SELECTIVE INDEX test_simple_sxi ON T1(xmlCol)  
FOR  
(  
    pathOne = 'book/authors/authorID' AS XQUERY 'xs:double',  
    pathTwo = 'book/authors/authorID' AS XQUERY 'xs:string'  
)  
```  
  
### <a name="examples"></a><span data-ttu-id="ae9d3-223">示例</span><span class="sxs-lookup"><span data-stu-id="ae9d3-223">Examples</span></span>  
 <span data-ttu-id="ae9d3-224">下面是其他一些示例，说明如何为不同的 XQuery 类型选择要建立索引的正确节点。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-224">Here are some additional examples of selecting the correct nodes to index for different XQuery types.</span></span>  
  
 <span data-ttu-id="ae9d3-225">**示例 1**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-225">**Example 1**</span></span>  
  
 <span data-ttu-id="ae9d3-226">下面是使用 exist() 方法的一个简单的 XQuery：</span><span class="sxs-lookup"><span data-stu-id="ae9d3-226">Here is a simple XQuery that uses the exist() method:</span></span>  
  
```sql  
SELECT T.record FROM myXMLTable T  
WHERE T.xmldata.exist('/a/b/c/d/e/h') = 1  
```  
  
 <span data-ttu-id="ae9d3-227">下表显示应建立索引以便让此查询使用选择性 XML 索引的节点。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-227">The following table shows the nodes that should be indexed to let this query use the selective XML index.</span></span>  
  
|<span data-ttu-id="ae9d3-228">要包含在索引中的节点</span><span class="sxs-lookup"><span data-stu-id="ae9d3-228">Node to include in the index</span></span>|<span data-ttu-id="ae9d3-229">为此节点建立索引的原因</span><span class="sxs-lookup"><span data-stu-id="ae9d3-229">Reason for indexing this node</span></span>|  
|----------------------------------|-----------------------------------|  
|<span data-ttu-id="ae9d3-230">**/a/b/c/d/e/h**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-230">**/a/b/c/d/e/h**</span></span>|<span data-ttu-id="ae9d3-231">在 exist() 方法中为存在的节点 `h` 进行求值。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-231">The existence of node `h` is evaluated in the exist() method.</span></span>|  
  
 <span data-ttu-id="ae9d3-232">**示例 2**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-232">**Example 2**</span></span>  
  
 <span data-ttu-id="ae9d3-233">下面是应用了谓词的前面的 XQuery 的更复杂变化形式：</span><span class="sxs-lookup"><span data-stu-id="ae9d3-233">Here is a more complex variation of the previous XQuery, with a predicate applied:</span></span>  
  
```sql  
SELECT T.record FROM myXMLTable T  
WHERE T.xmldata.exist('/a/b/c/d/e[./f = "SQL"]') = 1  
```  
  
 <span data-ttu-id="ae9d3-234">下表显示应建立索引以便让此查询使用选择性 XML 索引的节点。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-234">The following table shows the nodes that should be indexed to let this query use the selective XML index.</span></span>  
  
|<span data-ttu-id="ae9d3-235">要包含在索引中的节点</span><span class="sxs-lookup"><span data-stu-id="ae9d3-235">Node to include in the index</span></span>|<span data-ttu-id="ae9d3-236">为此节点建立索引的原因</span><span class="sxs-lookup"><span data-stu-id="ae9d3-236">Reason for indexing this node</span></span>|  
|----------------------------------|-----------------------------------|  
|<span data-ttu-id="ae9d3-237">**/a/b/c/d/e**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-237">**/a/b/c/d/e**</span></span>|<span data-ttu-id="ae9d3-238">一个谓词应用于节点 `e`。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-238">A predicate is applied over node `e`.</span></span>|  
|<span data-ttu-id="ae9d3-239">**/a/b/c/d/e/f**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-239">**/a/b/c/d/e/f**</span></span>|<span data-ttu-id="ae9d3-240">在该谓词内对节点 `f` 的值进行求值。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-240">The value of node `f` is evaluated inside the predicate.</span></span>|  
  
 <span data-ttu-id="ae9d3-241">**示例 3**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-241">**Example 3**</span></span>  
  
 <span data-ttu-id="ae9d3-242">下面是具有 value() 子句的更复杂查询：</span><span class="sxs-lookup"><span data-stu-id="ae9d3-242">Here is a more complex query with a value() clause:</span></span>  
  
```sql  
SELECT T.record,  
    T.xmldata.value('(/a/b/c/d/e[./f = "SQL"]/g)[1]', 'nvarchar(100)')  
FROM myXMLTable T  
```  
  
 <span data-ttu-id="ae9d3-243">下表显示应建立索引以便让此查询使用选择性 XML 索引的节点。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-243">The following table shows the nodes that should be indexed to let this query use the selective XML index.</span></span>  
  
|<span data-ttu-id="ae9d3-244">要包含在索引中的节点</span><span class="sxs-lookup"><span data-stu-id="ae9d3-244">Node to include in the index</span></span>|<span data-ttu-id="ae9d3-245">为此节点建立索引的原因</span><span class="sxs-lookup"><span data-stu-id="ae9d3-245">Reason for indexing this node</span></span>|  
|----------------------------------|-----------------------------------|  
|<span data-ttu-id="ae9d3-246">**/a/b/c/d/e**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-246">**/a/b/c/d/e**</span></span>|<span data-ttu-id="ae9d3-247">一个谓词应用于节点 `e`。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-247">A predicate is applied over node `e`.</span></span>|  
|<span data-ttu-id="ae9d3-248">**/a/b/c/d/e/f**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-248">**/a/b/c/d/e/f**</span></span>|<span data-ttu-id="ae9d3-249">在该谓词内对节点 `f` 的值进行求值。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-249">The value of node `f` is evaluated inside the predicate.</span></span>|  
|<span data-ttu-id="ae9d3-250">**/a/b/c/d/e/g**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-250">**/a/b/c/d/e/g**</span></span>|<span data-ttu-id="ae9d3-251">value() 方法返回节点 `g` 的值。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-251">The value of node `g` is returned by the value() method.</span></span>|  
  
 <span data-ttu-id="ae9d3-252">**示例 4**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-252">**Example 4**</span></span>  
  
 <span data-ttu-id="ae9d3-253">下面是在 exist() 子句内使用 FLWOR 子句的查询。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-253">Here is a query that uses a FLWOR clause inside an exist() clause.</span></span> <span data-ttu-id="ae9d3-254">（FLWOR 这个名称来自于可构成一个 XQuery FLWOR 表达式的五个子句：for、let、where、order by 和 return。）</span><span class="sxs-lookup"><span data-stu-id="ae9d3-254">(The name FLWOR comes from the five clauses that can make up an XQuery FLWOR expression: for, let, where, order by, and return.)</span></span>  
  
```sql  
SELECT T.record FROM myXMLTable T  
WHERE T.xmldata.exist('  
  For $x in /a/b/c/d/e  
  Where $x/f = "SQL"  
  Return $x/g  
') = 1  
```  
  
 <span data-ttu-id="ae9d3-255">下表显示应建立索引以便让此查询使用选择性 XML 索引的节点。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-255">The following table shows the nodes that should be indexed to let this query use the selective XML index.</span></span>  
  
|<span data-ttu-id="ae9d3-256">要包含在索引中的节点</span><span class="sxs-lookup"><span data-stu-id="ae9d3-256">Node to include in the index</span></span>|<span data-ttu-id="ae9d3-257">为此节点建立索引的原因</span><span class="sxs-lookup"><span data-stu-id="ae9d3-257">Reason for indexing this node</span></span>|  
|----------------------------------|-----------------------------------|  
|<span data-ttu-id="ae9d3-258">**/a/b/c/d/e**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-258">**/a/b/c/d/e**</span></span>|<span data-ttu-id="ae9d3-259">在 FLWOR 子句中为存在的节点 `e` 进行求值。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-259">The existence of node `e` is evaluated in the FLWOR clause.</span></span>|  
|<span data-ttu-id="ae9d3-260">**/a/b/c/d/e/f**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-260">**/a/b/c/d/e/f**</span></span>|<span data-ttu-id="ae9d3-261">在 FLWOR 子句中为节点 `f` 的值进行求值。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-261">The value of node `f` is evaluated in the FLWOR clause.</span></span>|  
|<span data-ttu-id="ae9d3-262">**/a/b/c/d/e/g**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-262">**/a/b/c/d/e/g**</span></span>|<span data-ttu-id="ae9d3-263">通过 exist() 方法为存在的节点 `g` 进行求值。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-263">The existence of node `g` is evaluated by the exist() method.</span></span>|  
  

  
##  <a name="specifying-optimization-hints"></a><a name="hints"></a> <span data-ttu-id="ae9d3-264">指定优化提示</span><span class="sxs-lookup"><span data-stu-id="ae9d3-264">Specifying Optimization Hints</span></span>  
 <span data-ttu-id="ae9d3-265">您可以使用可选的优化提示为按选择性 XML 索引建立索引的节点指定附加的映射详细信息。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-265">You can use optional optimization hints to specify additional mapping details for a node indexed by a selective XML index.</span></span> <span data-ttu-id="ae9d3-266">例如，可以指定节点的数据类型和基数，以及与数据结构有关的某些信息。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-266">For example, you can specify the data type and cardinality of the node, and certain information about the structure of the data.</span></span> <span data-ttu-id="ae9d3-267">这些附加信息支持更好的映射。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-267">This additional information supports better mapping.</span></span> <span data-ttu-id="ae9d3-268">它还可以导致改进性能和/或节约存储空间。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-268">It also results in improvements in performance or savings in storage, or both.</span></span>  
  
 <span data-ttu-id="ae9d3-269">是否使用优化提示是可选的。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-269">The use of optimization hints is optional.</span></span> <span data-ttu-id="ae9d3-270">您可以始终接受默认映射，这样做是可靠的，但无法提供最佳性能和存储。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-270">You can always accept the default mappings, which are reliable but may not provide optimal performance and storage.</span></span>  
  
 <span data-ttu-id="ae9d3-271">某些优化提示（例如 SINGLETON 提示）会引入针对您的数据的约束。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-271">Some optimization hints - for example, the SINGLETON hint - introduce constraints over your data.</span></span> <span data-ttu-id="ae9d3-272">在某些情况下，在未满足这些约束时可能会引发错误。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-272">In some cases, errors may be raised when those constraints are not met.</span></span>  
  
### <a name="benefits-of-optimization-hints"></a><span data-ttu-id="ae9d3-273">优化提示的好处</span><span class="sxs-lookup"><span data-stu-id="ae9d3-273">Benefits of Optimization Hints</span></span>  
 <span data-ttu-id="ae9d3-274">下表标识支持更高效的存储或改进的性能的优化提示。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-274">The following table identifies the optimization hints that support more efficient storage or improved performance.</span></span>  
  
|<span data-ttu-id="ae9d3-275">优化提示</span><span class="sxs-lookup"><span data-stu-id="ae9d3-275">Optimization hint</span></span>|<span data-ttu-id="ae9d3-276">更高效的存储</span><span class="sxs-lookup"><span data-stu-id="ae9d3-276">More efficient storage</span></span>|<span data-ttu-id="ae9d3-277">提高了性能</span><span class="sxs-lookup"><span data-stu-id="ae9d3-277">Improved performance</span></span>|  
|-----------------------|----------------------------|--------------------------|  
|<span data-ttu-id="ae9d3-278">**node()**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-278">**node()**</span></span>|<span data-ttu-id="ae9d3-279">是</span><span class="sxs-lookup"><span data-stu-id="ae9d3-279">Yes</span></span>|<span data-ttu-id="ae9d3-280">否</span><span class="sxs-lookup"><span data-stu-id="ae9d3-280">No</span></span>|  
|<span data-ttu-id="ae9d3-281">**SINGLETON**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-281">**SINGLETON**</span></span>|<span data-ttu-id="ae9d3-282">否</span><span class="sxs-lookup"><span data-stu-id="ae9d3-282">No</span></span>|<span data-ttu-id="ae9d3-283">是</span><span class="sxs-lookup"><span data-stu-id="ae9d3-283">Yes</span></span>|  
|<span data-ttu-id="ae9d3-284">**DATA TYPE**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-284">**DATA TYPE**</span></span>|<span data-ttu-id="ae9d3-285">是</span><span class="sxs-lookup"><span data-stu-id="ae9d3-285">Yes</span></span>|<span data-ttu-id="ae9d3-286">是</span><span class="sxs-lookup"><span data-stu-id="ae9d3-286">Yes</span></span>|  
|<span data-ttu-id="ae9d3-287">**MAXLENGTH**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-287">**MAXLENGTH**</span></span>|<span data-ttu-id="ae9d3-288">是</span><span class="sxs-lookup"><span data-stu-id="ae9d3-288">Yes</span></span>|<span data-ttu-id="ae9d3-289">是</span><span class="sxs-lookup"><span data-stu-id="ae9d3-289">Yes</span></span>|  
  
### <a name="optimization-hints-and-data-types"></a><span data-ttu-id="ae9d3-290">优化提示和数据类型</span><span class="sxs-lookup"><span data-stu-id="ae9d3-290">Optimization Hints and Data Types</span></span>  
 <span data-ttu-id="ae9d3-291">您可以将节点作为 XQuery 数据类型或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型建立索引。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-291">You can index nodes as XQuery data types or as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span> <span data-ttu-id="ae9d3-292">下表显示了每种数据类型支持的优化提示。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-292">The following table shows which optimization hints are supported with each data type.</span></span>  
  
|<span data-ttu-id="ae9d3-293">优化提示</span><span class="sxs-lookup"><span data-stu-id="ae9d3-293">Optimization hint</span></span>|<span data-ttu-id="ae9d3-294">XQuery 数据类型</span><span class="sxs-lookup"><span data-stu-id="ae9d3-294">XQuery data types</span></span>|<span data-ttu-id="ae9d3-295">SQL 数据类型</span><span class="sxs-lookup"><span data-stu-id="ae9d3-295">SQL data types</span></span>|  
|-----------------------|-----------------------|--------------------|  
|<span data-ttu-id="ae9d3-296">**node()**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-296">**node()**</span></span>|<span data-ttu-id="ae9d3-297">是</span><span class="sxs-lookup"><span data-stu-id="ae9d3-297">Yes</span></span>|<span data-ttu-id="ae9d3-298">否</span><span class="sxs-lookup"><span data-stu-id="ae9d3-298">No</span></span>|  
|<span data-ttu-id="ae9d3-299">**SINGLETON**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-299">**SINGLETON**</span></span>|<span data-ttu-id="ae9d3-300">是</span><span class="sxs-lookup"><span data-stu-id="ae9d3-300">Yes</span></span>|<span data-ttu-id="ae9d3-301">是</span><span class="sxs-lookup"><span data-stu-id="ae9d3-301">Yes</span></span>|  
|<span data-ttu-id="ae9d3-302">**DATA TYPE**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-302">**DATA TYPE**</span></span>|<span data-ttu-id="ae9d3-303">是</span><span class="sxs-lookup"><span data-stu-id="ae9d3-303">Yes</span></span>|<span data-ttu-id="ae9d3-304">否</span><span class="sxs-lookup"><span data-stu-id="ae9d3-304">No</span></span>|  
|<span data-ttu-id="ae9d3-305">**MAXLENGTH**</span><span class="sxs-lookup"><span data-stu-id="ae9d3-305">**MAXLENGTH**</span></span>|<span data-ttu-id="ae9d3-306">是</span><span class="sxs-lookup"><span data-stu-id="ae9d3-306">Yes</span></span>|<span data-ttu-id="ae9d3-307">否</span><span class="sxs-lookup"><span data-stu-id="ae9d3-307">No</span></span>|  
  
### <a name="node-optimization-hint"></a><span data-ttu-id="ae9d3-308">node() 优化提示</span><span class="sxs-lookup"><span data-stu-id="ae9d3-308">node() optimization hint</span></span>  
 <span data-ttu-id="ae9d3-309">适用对象：XQuery 数据类型</span><span class="sxs-lookup"><span data-stu-id="ae9d3-309">Applies to: XQuery data types</span></span>  
  
 <span data-ttu-id="ae9d3-310">您可以使用 node() 优化指定其值无需用于对典型查询进行求值的节点。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-310">You can use the node() optimization to specify a node whose value is not required to evaluate the typical query.</span></span> <span data-ttu-id="ae9d3-311">在典型查询仅需要为存在的节点进行求值时，此提示可降低存储要求。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-311">This hint reduces storage requirements when the typical query only has to evaluate the existence of the node.</span></span> <span data-ttu-id="ae9d3-312">（默认情况下，选择性 XML 查询将存储几乎所有提升的节点的值，只有复杂节点类型除外。）</span><span class="sxs-lookup"><span data-stu-id="ae9d3-312">(By default, a selective XML index stores the value for all promoted nodes, except complex node types.)</span></span>  
  
 <span data-ttu-id="ae9d3-313">请考虑以下示例：</span><span class="sxs-lookup"><span data-stu-id="ae9d3-313">Consider the following example:</span></span>  
  
```sql  
SELECT T.record FROM myXMLTable T  
WHERE T.xmldata.exist('/a/b[./c=5]') = 1  
```  
  
 <span data-ttu-id="ae9d3-314">若要使用选择性 XML 索引对此查询进行求值，请提升节点 `b` 和 `c`。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-314">To use a selective XML index to evaluate this query, promote nodes `b` and `c`.</span></span> <span data-ttu-id="ae9d3-315">但是，因为节点 `b` 的值不是必需的，所以，您可以将 node() 提示用于以下语法：</span><span class="sxs-lookup"><span data-stu-id="ae9d3-315">However, since the value of node `b` is not required, you can use the node() hint with the following syntax:</span></span>  
  
 `/a/b/ as node()`  
  
 <span data-ttu-id="ae9d3-316">如果某个查询要求已使用 node() 提示建立索引的节点值，则不能使用选择性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-316">If a query requires the value of a node that has been indexed with the node() hint, then the selective XML index cannot be used.</span></span>  
  
### <a name="singleton-optimization-hint"></a><span data-ttu-id="ae9d3-317">SINGLETON 优化提示</span><span class="sxs-lookup"><span data-stu-id="ae9d3-317">SINGLETON optimization hint</span></span>  
 <span data-ttu-id="ae9d3-318">适用对象：XQuery 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型</span><span class="sxs-lookup"><span data-stu-id="ae9d3-318">Applies to: XQuery or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types</span></span>  
  
 <span data-ttu-id="ae9d3-319">SINGLETON 优化提示指定节点的基数。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-319">The SINGLETON optimization hint specifies the cardinality of a node.</span></span> <span data-ttu-id="ae9d3-320">此提示将改进查询性能，因为提前知道节点在其父节点或祖先节点内最多出现一次。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-320">This hint improves query performance since it is known in advance that a node appears at most one time within its parent or ancestor.</span></span>  
  
 <span data-ttu-id="ae9d3-321">请考虑本主题中的 [示例 XML 文档](#sample) 。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-321">Consider the [sample XML document](#sample) in this topic.</span></span>  
  
 <span data-ttu-id="ae9d3-322">若要使用选择性 XML 索引对此文档进行查询，您可为节点 `d` 指定 SINGLETON 提示，因为该节点在其父节点内最多出现一次。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-322">To use a selective XML index to query this document, you can specify the SINGLETON hint for node `d` since it appears at most one time within its parent.</span></span>  
  
 <span data-ttu-id="ae9d3-323">如果已指定 SINGLETON 提示，但某一节点在其父节点或祖先节点内出现多次，则在您创建索引（为现有数据）或运行查询（为新数据）时将引发错误。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-323">If the SINGLETON hint has been specified, but a node appears more than one time within its parent or ancestor, then an error is raised when you create the index (for existing data) or when you run a query (for new data).</span></span>  
  
### <a name="data-type-optimization-hint"></a><span data-ttu-id="ae9d3-324">DATA TYPE 优化提示</span><span class="sxs-lookup"><span data-stu-id="ae9d3-324">DATA TYPE optimization hint</span></span>  
 <span data-ttu-id="ae9d3-325">适用对象：XQuery 数据类型</span><span class="sxs-lookup"><span data-stu-id="ae9d3-325">Applies to: XQuery data types</span></span>  
  
 <span data-ttu-id="ae9d3-326">通过 DATA TYPE 优化提示，您可以为已建立索引的节点指定 XQuery 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-326">The DATA TYPE optimization hint lets you specify an XQuery or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type for the indexed node.</span></span> <span data-ttu-id="ae9d3-327">该数据类型用于与选择性 XML 索引的数据表中与已建立索引的节点相对应的列。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-327">The data type is used for the column in the data table of the selective XML index that corresponds to the indexed node.</span></span>  
  
 <span data-ttu-id="ae9d3-328">在将现有值转换为指定的数据类型失败时，插入操作（插入到索引中）不会失败；但是，一个 null 值将插入到索引的数据表中。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-328">When casting an existing value to the specified data type fails, the insert operation (into the index) does not fail; however, a null value is inserted into the data table of the index.</span></span>  
  
### <a name="maxlength-optimization-hint"></a><span data-ttu-id="ae9d3-329">MAXLENGTH 优化提示</span><span class="sxs-lookup"><span data-stu-id="ae9d3-329">MAXLENGTH optimization hint</span></span>  
 <span data-ttu-id="ae9d3-330">适用对象：XQuery 数据类型</span><span class="sxs-lookup"><span data-stu-id="ae9d3-330">Applies to: XQuery data types</span></span>  
  
 <span data-ttu-id="ae9d3-331">通过 MAXLENGTH 优化提示，您可以限制 xs:string 数据的长度。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-331">The MAXLENGTH optimization hint lets you limit the length of xs:string data.</span></span> <span data-ttu-id="ae9d3-332">MAXLENGTH 与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型不相关，因为您在指定 VARCHAR 或 NVARCHAR 日期类型时指定长度。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-332">MAXLENGTH is not relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types since you specify the length when you specify the VARCHAR or NVARCHAR date types.</span></span>  
  
 <span data-ttu-id="ae9d3-333">在现有字符串长于指定的 MAXLENGTH 时，将该值插入到索引中将失败。</span><span class="sxs-lookup"><span data-stu-id="ae9d3-333">When an existing string is longer than the specified MAXLENGTH, then inserting that value into the index fails.</span></span>  
  

  
##  <a name="sample-xml-document-for-examples"></a><a name="sample"></a> <span data-ttu-id="ae9d3-334">针对示例的示例 XML 文档</span><span class="sxs-lookup"><span data-stu-id="ae9d3-334">Sample XML Document for Examples</span></span>  
 <span data-ttu-id="ae9d3-335">下面的示例 XML 文档在本主题的示例中引用：</span><span class="sxs-lookup"><span data-stu-id="ae9d3-335">The following sample XML document is referenced in the examples in this topic:</span></span>  
  
```xml  
<a>  
    <b>  
         <c atc="aa">10</c>  
         <c atc="bb">15</c>  
         <d atd1="dd" atd2="ddd">md </d>  
    </b>  
     <b>  
        <c></c>  
        <c atc="">117</c>  
     </b>  
</a>  
```  
  

  
## <a name="see-also"></a><span data-ttu-id="ae9d3-336">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ae9d3-336">See Also</span></span>  
 <span data-ttu-id="ae9d3-337">[选择性 XML 索引 (SXI)](../xml/selective-xml-indexes-sxi.md) </span><span class="sxs-lookup"><span data-stu-id="ae9d3-337">[Selective XML Indexes &#40;SXI&#41;](../xml/selective-xml-indexes-sxi.md) </span></span>  
 [<span data-ttu-id="ae9d3-338">创建、更改和删除选择性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="ae9d3-338">Create, Alter, and Drop Selective XML Indexes</span></span>](../xml/create-alter-and-drop-selective-xml-indexes.md)  
  
  
