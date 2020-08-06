---
title: XML 索引 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- removing indexes
- deleting indexes
- secondary indexes [XML in SQL Server]
- xml data type [SQL Server], indexes
- dropping indexes
- PATH index
- DROP_EXISTING clause
- XML [SQL Server], indexes
- primary indexes [XML in SQL Server]
- indexes [SQL Server], XML
- XML indexes [SQL Server], secondary
- BLOBs, XML indexes
- disabling indexes
- XML indexes [SQL Server], modifying
- XML indexes [SQL Server]
- XML indexes [SQL Server], primary
- modifying indexes
- XML indexes [SQL Server], dropping
- VALUE index
- XML indexes [SQL Server], xml data type
- PROPERTY index
- XML indexes [SQL Server], creating
ms.assetid: f5c9209d-b3f3-4543-b30b-01365a5e7333
author: rothja
ms.author: jroth
ms.openlocfilehash: bf9a33bc18790bf8821d778746a708f78bbb3d8f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588374"
---
# <a name="xml-indexes-sql-server"></a><span data-ttu-id="5be39-102">XML 索引 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5be39-102">XML Indexes (SQL Server)</span></span>
  <span data-ttu-id="5be39-103">可以对 `xml` 数据类型列创建 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="5be39-103">XML indexes can be created on `xml` data type columns.</span></span> <span data-ttu-id="5be39-104">它们对列中 XML 实例的所有标记、值和路径进行索引，从而提高查询性能。</span><span class="sxs-lookup"><span data-stu-id="5be39-104">They index all tags, values and paths over the XML instances in the column and benefit query performance.</span></span> <span data-ttu-id="5be39-105">在下列情况下，您的应用程序可以从 XML 索引中获益：</span><span class="sxs-lookup"><span data-stu-id="5be39-105">Your application may benefit from an XML index in the following situations:</span></span>  
  
-   <span data-ttu-id="5be39-106">对 XML 列进行查询在您的工作负荷中很常见。</span><span class="sxs-lookup"><span data-stu-id="5be39-106">Queries on XML columns are common in your workload.</span></span> <span data-ttu-id="5be39-107">必须考虑数据修改过程中的 XML 索引维护开销。</span><span class="sxs-lookup"><span data-stu-id="5be39-107">XML index maintenance cost during data modification must be considered.</span></span>  
  
-   <span data-ttu-id="5be39-108">XML 值相对较大，而检索的部分相对较小。</span><span class="sxs-lookup"><span data-stu-id="5be39-108">Your XML values are relatively large and the retrieved parts are relatively small.</span></span> <span data-ttu-id="5be39-109">生成索引避免了在运行时分析所有数据，并能实现高效的查询处理，从而使索引查找受益。</span><span class="sxs-lookup"><span data-stu-id="5be39-109">Building the index avoids parsing the whole data at run time and benefits index lookups for efficient query processing.</span></span>  
  
 <span data-ttu-id="5be39-110">XML 索引分为下列类别：</span><span class="sxs-lookup"><span data-stu-id="5be39-110">XML indexes fall into the following categories:</span></span>  
  
-   <span data-ttu-id="5be39-111">主 XML 索引</span><span class="sxs-lookup"><span data-stu-id="5be39-111">Primary XML index</span></span>  
  
-   <span data-ttu-id="5be39-112">辅助 XML 索引</span><span class="sxs-lookup"><span data-stu-id="5be39-112">Secondary XML index</span></span>  
  
 <span data-ttu-id="5be39-113">`xml` 类型列的第一个索引必须是主 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="5be39-113">The first index on the `xml` type column must be the primary XML index.</span></span> <span data-ttu-id="5be39-114">使用主 XML 索引时，支持以下类型的辅助索引：PATH、VALUE 和 PROPERTY。</span><span class="sxs-lookup"><span data-stu-id="5be39-114">Using the primary XML index, the following types of secondary indexes are supported: PATH, VALUE, and PROPERTY.</span></span> <span data-ttu-id="5be39-115">根据查询类型的不同，这些辅助索引可能有助于改善查询性能。</span><span class="sxs-lookup"><span data-stu-id="5be39-115">Depending on the type of queries, these secondary indexes might help improve query performance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5be39-116">除非为使用 `xml` 数据类型正确设置了数据库选项，否则无法创建或修改 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="5be39-116">You cannot create or modify an XML index unless the database options are set correctly for working with the `xml` data type.</span></span> <span data-ttu-id="5be39-117">有关详细信息，请参阅 [结合使用具有全文搜索和 XML 列](use-full-text-search-with-xml-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="5be39-117">For more information, see [Use Full-Text Search with XML Columns](use-full-text-search-with-xml-columns.md).</span></span>  
  
 <span data-ttu-id="5be39-118">XML 实例作为二进制大型对象 (BLOB) 存储在 `xml` 类型列中。</span><span class="sxs-lookup"><span data-stu-id="5be39-118">XML instances are stored in `xml` type columns as large binary objects (BLOBs).</span></span> <span data-ttu-id="5be39-119">这些 XML 实例可以很大，并且存储的 `xml` 数据类型实例的二进制表示形式最大可以为 2 GB。</span><span class="sxs-lookup"><span data-stu-id="5be39-119">These XML instances can be large, and the stored binary representation of `xml` data type instances can be up to 2 GB.</span></span> <span data-ttu-id="5be39-120">如果没有索引，则运行时将拆分这些二进制大型对象以计算查询。</span><span class="sxs-lookup"><span data-stu-id="5be39-120">Without an index, these binary large objects are shredded at run time to evaluate a query.</span></span> <span data-ttu-id="5be39-121">此拆分可能非常耗时。</span><span class="sxs-lookup"><span data-stu-id="5be39-121">This shredding can be time-consuming.</span></span> <span data-ttu-id="5be39-122">例如，请看以下查询：</span><span class="sxs-lookup"><span data-stu-id="5be39-122">For example, consider the following query:</span></span>  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS "PD")  
  
SELECT CatalogDescription.query('  
  /PD:ProductDescription/PD:Summary  
') as Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist ('/PD:ProductDescription/@ProductModelID[.="19"]') = 1  
```  
  
 <span data-ttu-id="5be39-123">为了选择满足 `WHERE` 子句中条件的 XML 实例，表 `Production.ProductModel` 的每行中的 XML 二进制大型对象 (BLOB) 将在运行时拆分。</span><span class="sxs-lookup"><span data-stu-id="5be39-123">To select the XML instances that satisfy the condition in the `WHERE` clause, the XML binary large object (BLOB) in each row of table `Production.ProductModel` is shredded at run time.</span></span> <span data-ttu-id="5be39-124">然后，计算 `(/PD:ProductDescription/@ProductModelID[.="19"]`方法中的表达式 `exist()` )。</span><span class="sxs-lookup"><span data-stu-id="5be39-124">Then, the expression `(/PD:ProductDescription/@ProductModelID[.="19"]`) in the `exist()` method is evaluated.</span></span> <span data-ttu-id="5be39-125">此运行时拆分有可能开销较大，这取决于存储在列中的实例的大小和数目。</span><span class="sxs-lookup"><span data-stu-id="5be39-125">This run-time shredding can be costly, depending on the size and number of instances stored in the column.</span></span>  
  
 <span data-ttu-id="5be39-126">如果在应用程序环境中经常查询 XML 二进制大型对象 (BLOB)，则对 `xml` 类型列创建索引很有用。</span><span class="sxs-lookup"><span data-stu-id="5be39-126">If querying XML binary large objects (BLOBs) is common in your application environment, it helps to index the `xml` type columns.</span></span> <span data-ttu-id="5be39-127">但是，在数据修改过程中维护索引会带来开销。</span><span class="sxs-lookup"><span data-stu-id="5be39-127">However, there is a cost associated with maintaining the index during data modification.</span></span>  
  
## <a name="primary-xml-index"></a><span data-ttu-id="5be39-128">主 XML 索引</span><span class="sxs-lookup"><span data-stu-id="5be39-128">Primary XML Index</span></span>  
 <span data-ttu-id="5be39-129">主 XML 索引对 XML 列中 XML 实例内的所有标记、值和路径进行索引。</span><span class="sxs-lookup"><span data-stu-id="5be39-129">The primary XML index indexes all tags, values, and paths within the XML instances in an XML column.</span></span> <span data-ttu-id="5be39-130">若要创建主 XML 索引，相应 XML 列所在的表必须对该表的主键创建了聚集索引。</span><span class="sxs-lookup"><span data-stu-id="5be39-130">To create a primary XML index, the table in which the XML column occurs must have a clustered index on the primary key of the table.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5be39-131">使用此主键将主 XML 索引中的行与包含此 XML 列的表中的行关联起来。</span><span class="sxs-lookup"><span data-stu-id="5be39-131">uses this primary key to correlate rows in the primary XML index with rows in the table that contains the XML column.</span></span>  
  
 <span data-ttu-id="5be39-132">主 XML 索引是 `xml` 数据类型列中的 XML BLOB 的已拆分和持久的表示形式。</span><span class="sxs-lookup"><span data-stu-id="5be39-132">The primary XML index is a shredded and persisted representation of the XML BLOBs in the `xml` data type column.</span></span> <span data-ttu-id="5be39-133">对于列中的每个 XML 二进制大型对象 (BLOB)，索引将创建数个数据行。</span><span class="sxs-lookup"><span data-stu-id="5be39-133">For each XML binary large object (BLOB) in the column, the index creates several rows of data.</span></span> <span data-ttu-id="5be39-134">该索引中的行数大约等于 XML 二进制大型对象中的节点数。</span><span class="sxs-lookup"><span data-stu-id="5be39-134">The number of rows in the index is approximately equal to the number of nodes in the XML binary large object.</span></span> <span data-ttu-id="5be39-135">当查询检索完整的 XML 实例时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会提供此 XML 列中的实例。</span><span class="sxs-lookup"><span data-stu-id="5be39-135">When a query retrieves the full XML instance, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides the instance from the XML column.</span></span> <span data-ttu-id="5be39-136">XML 实例中的查询使用主 XML 索引，并可以通过使用索引本身返回标量值或 XML 子树。</span><span class="sxs-lookup"><span data-stu-id="5be39-136">Queries within XML instances use the primary XML index, and can return scalar values or XML subtrees by using the index itself.</span></span>  
  
 <span data-ttu-id="5be39-137">每行存储以下节点信息：</span><span class="sxs-lookup"><span data-stu-id="5be39-137">Each row stores the following node information:</span></span>  
  
-   <span data-ttu-id="5be39-138">标记名（如元素名称或属性名称）。</span><span class="sxs-lookup"><span data-stu-id="5be39-138">Tag name such as an element or attribute name.</span></span>  
  
-   <span data-ttu-id="5be39-139">节点值。</span><span class="sxs-lookup"><span data-stu-id="5be39-139">Node value.</span></span>  
  
-   <span data-ttu-id="5be39-140">节点类型（如元素节点、属性节点或文本节点）。</span><span class="sxs-lookup"><span data-stu-id="5be39-140">Node type such as an element node, attribute node, or text node.</span></span>  
  
-   <span data-ttu-id="5be39-141">文档顺序信息（由内部节点标识符表示）。</span><span class="sxs-lookup"><span data-stu-id="5be39-141">Document order information, represented by an internal node identifier.</span></span>  
  
-   <span data-ttu-id="5be39-142">从每个节点到 XML 树的根的路径。</span><span class="sxs-lookup"><span data-stu-id="5be39-142">Path from each node to the root of the XML tree.</span></span> <span data-ttu-id="5be39-143">搜索此列可获得查询中的路径表达式。</span><span class="sxs-lookup"><span data-stu-id="5be39-143">This column is searched for path expressions in the query.</span></span>  
  
-   <span data-ttu-id="5be39-144">基表的主键。</span><span class="sxs-lookup"><span data-stu-id="5be39-144">Primary key of the base table.</span></span> <span data-ttu-id="5be39-145">基表的主键将复制到主 XML 索引中，用于向后和基表进行联接，并且基表的主键中的最大列数限制为 15。</span><span class="sxs-lookup"><span data-stu-id="5be39-145">The primary key of the base table is duplicated in the primary XML index for a back join with the base table, and the maximum number of columns in the primary key of the base table is limited to 15.</span></span>  
  
 <span data-ttu-id="5be39-146">此节点信息用于计算和构造指定查询的 XML 结果。</span><span class="sxs-lookup"><span data-stu-id="5be39-146">This node information is used to evaluate and construct XML results for a specified query.</span></span> <span data-ttu-id="5be39-147">出于优化的需要，标记名和节点类型信息编码为整数值，且 Path 列使用同样的编码。</span><span class="sxs-lookup"><span data-stu-id="5be39-147">For optimization purposes, the tag name and the node type information are encoded as integer values, and the Path column uses the same encoding.</span></span> <span data-ttu-id="5be39-148">另外，路径以相反的顺序存储，以便在仅知道路径后缀的情况下能够匹配路径。</span><span class="sxs-lookup"><span data-stu-id="5be39-148">Also, paths are stored in reverse order to allow matching paths when only the path suffix is known.</span></span> <span data-ttu-id="5be39-149">例如：</span><span class="sxs-lookup"><span data-stu-id="5be39-149">For example:</span></span>  
  
-   <span data-ttu-id="5be39-150">`//ContactRecord/PhoneNumber` ，其中只有最后两个步骤是已知的</span><span class="sxs-lookup"><span data-stu-id="5be39-150">`//ContactRecord/PhoneNumber` where only the last two steps are known</span></span>  
  
 <span data-ttu-id="5be39-151">OR</span><span class="sxs-lookup"><span data-stu-id="5be39-151">OR</span></span>  
  
-   <span data-ttu-id="5be39-152">`/Book/*/Title` 其中，通配符 (`*`) 是指定在表达式中间的。</span><span class="sxs-lookup"><span data-stu-id="5be39-152">`/Book/*/Title` where the wildcard character (`*`) is specified in the middle of the expression.</span></span>  
  
 <span data-ttu-id="5be39-153">对于涉及 [xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods) 的查询，查询处理器使用主 XML 索引，并返回主索引自身中的标量值或 XML 子树。</span><span class="sxs-lookup"><span data-stu-id="5be39-153">The query processor uses the primary XML index for queries that involve [xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods) and returns either scalar values or the XML subtrees from the primary index itself.</span></span> <span data-ttu-id="5be39-154">（此索引存储重新构造 XML 实例所需的所有信息。）</span><span class="sxs-lookup"><span data-stu-id="5be39-154">(This index stores all the necessary information to reconstruct the XML instance.)</span></span>  
  
 <span data-ttu-id="5be39-155">例如，以下查询将返回表的 "类型" 列中存储的摘要信息 `CatalogDescription``xml` `ProductModel` 。</span><span class="sxs-lookup"><span data-stu-id="5be39-155">For example, the following query returns summary information stored in the `CatalogDescription``xml` type column in the `ProductModel` table.</span></span> <span data-ttu-id="5be39-156">只有当产品型号的目录说明中还存储 <`Features`> 说明时，该查询才会返回 <`Summary`> 信息。</span><span class="sxs-lookup"><span data-stu-id="5be39-156">The query returns <`Summary`> information only for product models whose catalog description also stores the <`Features`> description.</span></span>  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS "PD")SELECT CatalogDescription.query('  /PD:ProductDescription/PD:Summary') as ResultFROM Production.ProductModelWHERE CatalogDescription.exist ('/PD:ProductDescription/PD:Features') = 1  
```  
  
 <span data-ttu-id="5be39-157">关于主 XML 索引，为 `exist()` 方法中指定的表达式按顺序搜索与每个 XML 二进制大型对象相对应的索引中的行，而不是拆分基表中的每个 XML 二进制大型对象实例。</span><span class="sxs-lookup"><span data-stu-id="5be39-157">With regard to the primary XML index, instead of shredding each XML binary large object instance in the base table, the rows in the index that correspond to each XML binary large object are searched sequentially for the expression specified in the `exist()` method.</span></span> <span data-ttu-id="5be39-158">如果路径是在索引中的 Path 列中找到的，则从主 XML 索引检索 <`Summary`> 元素及其子树，并将它们转换为 XML 二进制大型对象以作为 `query()` 方法的结果。</span><span class="sxs-lookup"><span data-stu-id="5be39-158">If the path is found in the Path column in the index, the <`Summary`> element together with its subtrees is retrieved from the primary XML index and converted into an XML binary large object as the result of the `query()` method.</span></span>  
  
 <span data-ttu-id="5be39-159">注意，检索完整的 XML 实例时不使用主 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="5be39-159">Note that the primary XML index is not used when retrieving a full XML instance.</span></span> <span data-ttu-id="5be39-160">例如，下面的查询从表中检索描述了特定产品型号的生产说明的整个 XML 实例。</span><span class="sxs-lookup"><span data-stu-id="5be39-160">For example, the following query retrieves from the table the whole XML instance that describes the manufacturing instructions for a specific product model.</span></span>  
  
```  
USE AdventureWorks2012;SELECT InstructionsFROM Production.ProductModel WHERE ProductModelID=7;  
```  
  
## <a name="secondary-xml-indexes"></a><span data-ttu-id="5be39-161">辅助 XML 索引</span><span class="sxs-lookup"><span data-stu-id="5be39-161">Secondary XML Indexes</span></span>  
 <span data-ttu-id="5be39-162">为了增强搜索性能，可以创建辅助 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="5be39-162">To enhance search performance, you can create secondary XML indexes.</span></span> <span data-ttu-id="5be39-163">必须有了主 XML 索引才能创建辅助索引。</span><span class="sxs-lookup"><span data-stu-id="5be39-163">A primary XML index must first exist before you can create secondary indexes.</span></span> <span data-ttu-id="5be39-164">辅助索引的类型如下：</span><span class="sxs-lookup"><span data-stu-id="5be39-164">These are the types:</span></span>  
  
-   <span data-ttu-id="5be39-165">PATH 辅助 XML 索引</span><span class="sxs-lookup"><span data-stu-id="5be39-165">PATH secondary XML index</span></span>  
  
-   <span data-ttu-id="5be39-166">VALUE 辅助 XML 索引</span><span class="sxs-lookup"><span data-stu-id="5be39-166">VALUE secondary XML index</span></span>  
  
-   <span data-ttu-id="5be39-167">PROPERTY 辅助 XML 索引</span><span class="sxs-lookup"><span data-stu-id="5be39-167">PROPERTY secondary XML index</span></span>  
  
 <span data-ttu-id="5be39-168">以下为创建一个或多个辅助索引的一些准则：</span><span class="sxs-lookup"><span data-stu-id="5be39-168">Following are some guidelines for creating one or more secondary indexes:</span></span>  
  
-   <span data-ttu-id="5be39-169">如果工作负荷对 XML 列大量使用路径表达式，则 PATH 辅助 XML 索引可能会提高工作负荷的处理速度。</span><span class="sxs-lookup"><span data-stu-id="5be39-169">If your workload uses path expressions significantly on XML columns, the PATH secondary XML index is likely to speed up your workload.</span></span> <span data-ttu-id="5be39-170">最常见的情况是在 Transact-SQL 的 WHERE 子句中对 XML 列使用 **exist()** 方法。</span><span class="sxs-lookup"><span data-stu-id="5be39-170">The most common case is the use of the **exist()** method on XML columns in the WHERE clause of Transact-SQL.</span></span>  
  
-   <span data-ttu-id="5be39-171">如果工作负荷通过使用路径表达式从单个 XML 实例中检索多个值，则在 PROPERTY 索引中聚集各个 XML 实例中的路径可能会很有用。</span><span class="sxs-lookup"><span data-stu-id="5be39-171">If your workload retrieves multiple values from individual XML instances by using path expressions, clustering paths within each XML instance in the PROPERTY index may be helpful.</span></span> <span data-ttu-id="5be39-172">这种情况通常出现在属性包方案中，此时提取对象的属性并且已知其主键值。</span><span class="sxs-lookup"><span data-stu-id="5be39-172">This scenario typically occurs in a property bag scenario when properties of an object are fetched and its primary key value is known.</span></span>  
  
-   <span data-ttu-id="5be39-173">如果工作负荷涉及查询 XML 实例中的值，但不知道包含那些值的元素名称或属性名称，则您可能希望创建 VALUE 索引。</span><span class="sxs-lookup"><span data-stu-id="5be39-173">If your workload involves querying for values within XML instances without knowing the element or attribute names that contain those values, you may want to create the VALUE index.</span></span> <span data-ttu-id="5be39-174">这通常出现在 descendant 轴查找中，例如 //author[last-name="Howard"]，其中 \<author> 元素可以出现在层次结构的任何级别上。</span><span class="sxs-lookup"><span data-stu-id="5be39-174">This typically occurs with descendant axes lookups, such as //author[last-name="Howard"], where \<author> elements can occur at any level of the hierarchy.</span></span> <span data-ttu-id="5be39-175">这种情况也出现在通配符查询中，例如 /book [@\* = "novel"]，其中查询将查找具有某个值为“novel”的属性的 \<book> 元素。</span><span class="sxs-lookup"><span data-stu-id="5be39-175">It also occurs in wildcard queries, such as /book [@\* = "novel"], where the query looks for \<book> elements that have some attribute having the value "novel".</span></span>  
  
### <a name="path-secondary-xml-index"></a><span data-ttu-id="5be39-176">PATH 辅助 XML 索引</span><span class="sxs-lookup"><span data-stu-id="5be39-176">PATH Secondary XML Index</span></span>  
 <span data-ttu-id="5be39-177">如果查询通常对 `xml` 类型列指定路径表达式，则 PATH 辅助索引可以提高搜索的速度。</span><span class="sxs-lookup"><span data-stu-id="5be39-177">If your queries generally specify path expressions on `xml` type columns, a PATH secondary index may be able to speed up the search.</span></span> <span data-ttu-id="5be39-178">如本主题前面所述，当查询在 WHERE 子句中指定 **exist()** 方法时主索引非常有用。</span><span class="sxs-lookup"><span data-stu-id="5be39-178">As described earlier in this topic, the primary index is helpful when you have queries that specify **exist()** method in the WHERE clause.</span></span> <span data-ttu-id="5be39-179">如果添加 PATH 辅助索引，则您还可以改善此类查询的搜索性能。</span><span class="sxs-lookup"><span data-stu-id="5be39-179">If you add a PATH secondary index, you may also improve the search performance in such queries.</span></span>  
  
 <span data-ttu-id="5be39-180">虽然主 XML 索引避免了在运行时拆分 XML 二进制大型对象，但是它不会为基于路径表达式的查询提供最好的性能。</span><span class="sxs-lookup"><span data-stu-id="5be39-180">Although a primary XML index avoids having to shred the XML binary large objects at run time, it may not provide the best performance for queries based on path expressions.</span></span> <span data-ttu-id="5be39-181">由于是按顺序在与 XML 二进制大型对象相对应的主 XML 索引中的所有行中搜索大 XML 实例，所以按顺序搜索可能会很慢。</span><span class="sxs-lookup"><span data-stu-id="5be39-181">Because all rows in the primary XML index corresponding to an XML binary large object are searched sequentially for large XML instances, the sequential search may be slow.</span></span> <span data-ttu-id="5be39-182">这种情况下，对主索引中的路径值和节点值生成辅助索引可以有效地提高索引搜索的速度。</span><span class="sxs-lookup"><span data-stu-id="5be39-182">In this case, having a secondary index built on the path values and node values in the primary index can significantly speed up the index search.</span></span> <span data-ttu-id="5be39-183">在 PATH 辅助索引中，路径值和节点值是允许在搜索路径时使用更高效的查找功能的键列。</span><span class="sxs-lookup"><span data-stu-id="5be39-183">In the PATH secondary index, the path and node values are key columns that allow for more efficient seeks when searching for paths.</span></span> <span data-ttu-id="5be39-184">查询优化器可以将 PATH 索引用于如下所示的表达式：</span><span class="sxs-lookup"><span data-stu-id="5be39-184">The query optimizer may use the PATH index for expressions such as those shown in the following:</span></span>  
  
-   <span data-ttu-id="5be39-185">`/root/Location` ，仅指定一个路径</span><span class="sxs-lookup"><span data-stu-id="5be39-185">`/root/Location` which specify only a path</span></span>  
  
 <span data-ttu-id="5be39-186">OR</span><span class="sxs-lookup"><span data-stu-id="5be39-186">OR</span></span>  
  
-   <span data-ttu-id="5be39-187">`/root/Location/@LocationID[.="10"]` ，其中路径和节点值均指定。</span><span class="sxs-lookup"><span data-stu-id="5be39-187">`/root/Location/@LocationID[.="10"]` where both the path and the node value are specified.</span></span>  
  
 <span data-ttu-id="5be39-188">以下查询介绍了适用 PATH 索引的情形：</span><span class="sxs-lookup"><span data-stu-id="5be39-188">The following query shows where the PATH index is helpful:</span></span>  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS "PD")  
  
SELECT CatalogDescription.query('  
  /PD:ProductDescription/PD:Summary  
') AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist ('/PD:ProductDescription/@ProductModelID[.="19"]') = 1  
```  
  
 <span data-ttu-id="5be39-189">在该查询中， `/PD:ProductDescription/@ProductModelID` 方法中的路径表达式 `"19"` 和值 `exist()` 对应于 PATH 索引的键字段。</span><span class="sxs-lookup"><span data-stu-id="5be39-189">In the query, the path expression `/PD:ProductDescription/@ProductModelID` and value `"19"` in the `exist()` method correspond to the key fields of the PATH index.</span></span> <span data-ttu-id="5be39-190">这便允许在 PATH 索引中直接查找，并为主索引中的路径值提供优于顺序搜索的搜索性能。</span><span class="sxs-lookup"><span data-stu-id="5be39-190">This allows for direct seek in the PATH index and provides better search performance than the sequential search for path values in the primary index.</span></span>  
  
### <a name="value-secondary-xml-index"></a><span data-ttu-id="5be39-191">VALUE 辅助 XML 索引</span><span class="sxs-lookup"><span data-stu-id="5be39-191">VALUE Secondary XML Index</span></span>  
 <span data-ttu-id="5be39-192">如果查询是基于值的查询，例如 `/Root/ProductDescription/@*[. = "Mountain Bike"]` 或 `//ProductDescription[@Name = "Mountain Bike"]`，且没有完全指定路径或路径包含有通配符，则生成基于主 XML 索引中的节点值所创建的辅助 XML 索引可以更快地获得结果。</span><span class="sxs-lookup"><span data-stu-id="5be39-192">If queries are value based, for example, `/Root/ProductDescription/@*[. = "Mountain Bike"]` or `//ProductDescription[@Name = "Mountain Bike"]`, and the path is not fully specified or it includes a wildcard, you might obtain faster results by building a secondary XML index that is built on node values in the primary XML index.</span></span>  
  
 <span data-ttu-id="5be39-193">VALUE 索引的键列是主 XML 索引的节点值和路径。</span><span class="sxs-lookup"><span data-stu-id="5be39-193">The key columns of the VALUE index are (node value and path) of the primary XML index.</span></span> <span data-ttu-id="5be39-194">如果您的工作负荷涉及到查询 XML 实例中的值，但不知道包含这些值的元素名称或属性名称，则 VALUE 索引可能会很有用。</span><span class="sxs-lookup"><span data-stu-id="5be39-194">If your workload involves querying for values from XML instances without knowing the element or attribute names that contain the values, a VALUE index may be useful.</span></span> <span data-ttu-id="5be39-195">例如，以下表达式受益于 VALUE 索引：</span><span class="sxs-lookup"><span data-stu-id="5be39-195">For example, the following expression will benefit from having a VALUE index:</span></span>  
  
-   <span data-ttu-id="5be39-196">`//author[LastName="someName"]`，其中 <`LastName`> 元素的值已知，但是 <`author`> 父级可以出现在任何地方。</span><span class="sxs-lookup"><span data-stu-id="5be39-196">`//author[LastName="someName"]` where you know the value of the <`LastName`> element, but the <`author`> parent can occur anywhere.</span></span>  
  
-   <span data-ttu-id="5be39-197">`/book[@* = "someValue"]`，其中查询将查找包含值为 `"someValue"` 的属性的 <`book`> 元素。</span><span class="sxs-lookup"><span data-stu-id="5be39-197">`/book[@* = "someValue"]` where the query looks for the <`book`> element that has some attribute having the value `"someValue"`.</span></span>  
  
 <span data-ttu-id="5be39-198">以下查询从 `ContactID` 表中返回 `Contact` 。</span><span class="sxs-lookup"><span data-stu-id="5be39-198">The following query returns `ContactID` from the `Contact` table.</span></span> <span data-ttu-id="5be39-199">`WHERE`子句指定一个在 "类型" 列中查找值的筛选器 `AdditionalContactInfo``xml` 。</span><span class="sxs-lookup"><span data-stu-id="5be39-199">The `WHERE` clause specifies a filter that looks for values in the `AdditionalContactInfo``xml` type column.</span></span> <span data-ttu-id="5be39-200">只有当相应的其他联系信息 XML 二进制大型对象包含具体的电话号码时，才会返回联系 ID。</span><span class="sxs-lookup"><span data-stu-id="5be39-200">The contact IDs are returned only if the corresponding additional contact information XML binary large object includes a specific telephone number.</span></span> <span data-ttu-id="5be39-201">由于 <`telephoneNumber`> 元素可以显示在 XML 中的任意位置，因而路径表达式指定 descendent-or-self 轴。</span><span class="sxs-lookup"><span data-stu-id="5be39-201">Because the <`telephoneNumber`> element may appear anywhere in the XML, the path expression specifies the descendent-or-self axis.</span></span>  
  
```  
WITH XMLNAMESPACES (  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo' AS CI,  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes' AS ACT)  
  
SELECT ContactID   
FROM   Person.Contact  
WHERE  AdditionalContactInfo.exist('//ACT:telephoneNumber/ACT:number[.="111-111-1111"]') = 1  
```  
  
 <span data-ttu-id="5be39-202">在这种情况下，<`number`> 的搜索值是已知的，但是它可以作为 <`telephoneNumber`> 元素的子级在 XML 实例中的任意位置出现。</span><span class="sxs-lookup"><span data-stu-id="5be39-202">In this situation, the search value for <`number`> is known, but it can appear anywhere in the XML instance as a child of the <`telephoneNumber`> element.</span></span> <span data-ttu-id="5be39-203">这种查询可能受益于基于特定值的索引查找。</span><span class="sxs-lookup"><span data-stu-id="5be39-203">This kind of query might benefit from an index lookup based on a specific value.</span></span>  
  
### <a name="property-secondary-index"></a><span data-ttu-id="5be39-204">PROPERTY 辅助索引</span><span class="sxs-lookup"><span data-stu-id="5be39-204">PROPERTY Secondary Index</span></span>  
 <span data-ttu-id="5be39-205">从单个 XML 实例检索一个或多个值的查询适用 PROPERTY 索引。</span><span class="sxs-lookup"><span data-stu-id="5be39-205">Queries that retrieve one or more values from individual XML instances might benefit from a PROPERTY index.</span></span> <span data-ttu-id="5be39-206">如果使用类型\*\* ( # B1\*\*方法的值检索对象属性 `xml` ，并且对象的主键值已知，则会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="5be39-206">This scenario occurs when you retrieve object properties by using the **value()** method of the `xml` type and when the primary key value of the object is known.</span></span>  
  
 <span data-ttu-id="5be39-207">PROPERTY 索引是对主 XML 索引的列（PK、Path 和节点值）创建的，其中 PK 是基表的主键。</span><span class="sxs-lookup"><span data-stu-id="5be39-207">The PROPERTY index is built on columns (PK, Path and node value) of the primary XML index where PK is the primary key of the base table.</span></span>  
  
 <span data-ttu-id="5be39-208">例如，对于产品样式 `19`，以下查询使用 `ProductModelID` 方法检索 `ProductModelName` 属性值和 `value()` 属性值。</span><span class="sxs-lookup"><span data-stu-id="5be39-208">For example, for product model `19`, the following query retrieves the `ProductModelID` and `ProductModelName` attribute values using the `value()` method.</span></span> <span data-ttu-id="5be39-209">使用 PROPERTY 索引代替主 XML 索引或其他辅助 XML 索引可以使执行速度更快。</span><span class="sxs-lookup"><span data-stu-id="5be39-209">Instead of using the primary XML index or the other secondary XML indexes, the PROPERTY index may provide faster execution.</span></span>  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS "PD")  
  
SELECT CatalogDescription.value('(/PD:ProductDescription/@ProductModelID)[1]', 'int') as ModelID,  
       CatalogDescription.value('(/PD:ProductDescription/@ProductModelName)[1]', 'varchar(30)') as ModelName          
FROM Production.ProductModel     
WHERE ProductModelID = 19  
```  
  
 <span data-ttu-id="5be39-210">除了本主题后面所述的区别之外，对类型列创建 XML 索引 `xml` 与对非类型列创建索引类似 `xml` 。</span><span class="sxs-lookup"><span data-stu-id="5be39-210">Except for the differences described later in this topic, creating an XML index on an`xml` type column is similar to creating an index on a non-`xml` type column.</span></span> <span data-ttu-id="5be39-211">可以使用下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] DDL 语句创建和管理 XML 索引：</span><span class="sxs-lookup"><span data-stu-id="5be39-211">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] DDL statements can be used to create and manage XML indexes:</span></span>  
  
-   [<span data-ttu-id="5be39-212">CREATE INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5be39-212">CREATE INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-index-transact-sql)  
  
-   [<span data-ttu-id="5be39-213">ALTER INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5be39-213">ALTER INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-index-transact-sql)  
  
-   [<span data-ttu-id="5be39-214">DROP INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5be39-214">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
## <a name="getting-information-about-xml-indexes"></a><span data-ttu-id="5be39-215">获取有关 XML 索引的信息</span><span class="sxs-lookup"><span data-stu-id="5be39-215">Getting Information about XML Indexes</span></span>  
 <span data-ttu-id="5be39-216">XML 索引项位于目录视图 sys.indexes 中，索引“type”为 3。</span><span class="sxs-lookup"><span data-stu-id="5be39-216">XML index entries appear in the catalog view, sys.indexes, with the index "type" 3.</span></span> <span data-ttu-id="5be39-217">名称列包含 XML 索引的名称。</span><span class="sxs-lookup"><span data-stu-id="5be39-217">The name column contains the name of the XML index.</span></span>  
  
 <span data-ttu-id="5be39-218">另外，XML 索引还记录在目录视图 sys.xml_indexes 中。</span><span class="sxs-lookup"><span data-stu-id="5be39-218">XML indexes are also recorded in the catalog view, sys.xml_indexes.</span></span> <span data-ttu-id="5be39-219">此视图包含 sys.indexes 的所有列以及对 XML 索引有用的某些特定列。</span><span class="sxs-lookup"><span data-stu-id="5be39-219">This contains all the columns of sys.indexes and some specific ones that are useful for XML indexes.</span></span> <span data-ttu-id="5be39-220">secondary_type 列中的值 NULL 表示主 XML 索引；值“P”、“R”和“V”分别表示 PATH、PROPERTY 和 VALUE 辅助 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="5be39-220">The value NULL in the column, secondary_type, indicates a primary XML index; the values 'P', 'R' and 'V' stand for PATH, PROPERTY, and VALUE secondary XML indexes, respectively.</span></span>  
  
 <span data-ttu-id="5be39-221">可以在表值函数 [sys.dm_db_index_physical_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql)中找到 XML 索引的空间使用情况。</span><span class="sxs-lookup"><span data-stu-id="5be39-221">The space use of XML indexes can be found in the table-valued function [sys.dm_db_index_physical_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql).</span></span> <span data-ttu-id="5be39-222">它提供了所有索引类型的相关信息，例如，占用的磁盘页数、平均行大小（字节）和记录数。</span><span class="sxs-lookup"><span data-stu-id="5be39-222">It provides information, such as the number of disk pages occupied, average row size in bytes, and number of records, for all index types..</span></span> <span data-ttu-id="5be39-223">其中也包括 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="5be39-223">This also includes XML indexes.</span></span> <span data-ttu-id="5be39-224">对于每个数据库分区，都提供此信息。</span><span class="sxs-lookup"><span data-stu-id="5be39-224">This information is available for each database partition.</span></span> <span data-ttu-id="5be39-225">XML 索引使用基表的相同分区方案和分区函数。</span><span class="sxs-lookup"><span data-stu-id="5be39-225">XML indexes use the same partitioning scheme and partitioning function of the base table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5be39-226">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5be39-226">See Also</span></span>  
 <span data-ttu-id="5be39-227">[sys.dm_db_index_physical_stats (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5be39-227">[sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql) </span></span>  
 [<span data-ttu-id="5be39-228">XML 数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5be39-228">XML Data &#40;SQL Server&#41;</span></span>](../xml/xml-data-sql-server.md)  
  
  
