---
title: 选择性 XML 索引 (SXI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
ms.assetid: 598ecdcd-084b-4032-81b2-eed6ae9f5d44
author: rothja
ms.author: jroth
ms.openlocfilehash: 37dd72c5de2892672dc9f63066075ab5e770d758
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591152"
---
# <a name="selective-xml-indexes-sxi"></a><span data-ttu-id="6204f-102">选择性 XML 索引 (SXI)</span><span class="sxs-lookup"><span data-stu-id="6204f-102">Selective XML Indexes (SXI)</span></span>
  <span data-ttu-id="6204f-103">选择性 XML 索引是除了普通 XML 索引之外可供您使用的另外一种 XML 索引类型。</span><span class="sxs-lookup"><span data-stu-id="6204f-103">Selective XML indexes are another type of XML index that is available to you in addition to ordinary XML indexes.</span></span> <span data-ttu-id="6204f-104">选择性 XML 索引功能的目标如下：</span><span class="sxs-lookup"><span data-stu-id="6204f-104">The goals of the selective XML index feature are the following:</span></span>  
  
-   <span data-ttu-id="6204f-105">改进对在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中存储的 XML 数据的查询性能。</span><span class="sxs-lookup"><span data-stu-id="6204f-105">To improve the performance of queries over XML data stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="6204f-106">支持更快速地对较大的 XML 数据工作负荷建立索引。</span><span class="sxs-lookup"><span data-stu-id="6204f-106">To support faster indexing of large XML data workloads.</span></span>  
  
-   <span data-ttu-id="6204f-107">通过减少 XML 索引的存储成本提高可伸缩性。</span><span class="sxs-lookup"><span data-stu-id="6204f-107">To improve scalability by reducing the storage costs of XML indexes.</span></span>  
  
 <span data-ttu-id="6204f-108">普通 XML 索引的主要限制是要对整个 XML 文档建立索引。</span><span class="sxs-lookup"><span data-stu-id="6204f-108">The main limitation with ordinary XML indexes is that they index the entire XML document.</span></span> <span data-ttu-id="6204f-109">这导致了主要与索引的存储成本相关的几大缺点，例如降低了查询性能和增加了索引维护成本。</span><span class="sxs-lookup"><span data-stu-id="6204f-109">This leads to several significant drawbacks, such as decreased query performance and increased index maintenance cost, mostly related to the storage costs of the index.</span></span>  
  
 <span data-ttu-id="6204f-110">通过选择性 XML 索引功能，您可以从要建立索引的 XML 文档仅提升某些路径。</span><span class="sxs-lookup"><span data-stu-id="6204f-110">The selective XML index feature lets you promote only certain paths from the XML documents to index.</span></span> <span data-ttu-id="6204f-111">在创建索引时，将对这些路径进行评估，这些路径所指向的节点将被拆分并存储于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中的关系表内。</span><span class="sxs-lookup"><span data-stu-id="6204f-111">At index creation time, these paths are evaluated, and the nodes that they point to are shredded and stored inside a relational table in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6204f-112">该功能采用了 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 研究院与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 产品团队合作开发的高效的映射算法。</span><span class="sxs-lookup"><span data-stu-id="6204f-112">This feature uses an efficient mapping algorithm developed by [!INCLUDE[msCoName](../../includes/msconame-md.md)] Research in collaboration with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] product team.</span></span> <span data-ttu-id="6204f-113">该算法将 XML 节点映射到单个关系表，实现了不同凡响的性能且只要求有限的存储空间。</span><span class="sxs-lookup"><span data-stu-id="6204f-113">This algorithm maps the XML nodes to a single relational table, and achieves exceptional performance while requiring only modest storage space.</span></span>  
  
 <span data-ttu-id="6204f-114">该选择性 XML 索引功能还支持针对已按选择性 XML 索引建立索引的节点的辅助选择性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="6204f-114">The selective XML index feature also supports secondary selective XML indexes over nodes that have been indexed by a selective XML index.</span></span> <span data-ttu-id="6204f-115">这些辅助选择性索引是高效的并且进一步改进了查询性能。</span><span class="sxs-lookup"><span data-stu-id="6204f-115">These secondary selective indexes are efficient and further improve the performance of queries.</span></span>  
  
##  <a name="benefits-of-selective-xml-indexes"></a><a name="benefits"></a> <span data-ttu-id="6204f-116">选择性 XML 索引的优点</span><span class="sxs-lookup"><span data-stu-id="6204f-116">Benefits of Selective XML Indexes</span></span>  
 <span data-ttu-id="6204f-117">选择性 XML 索引具有下列优点：</span><span class="sxs-lookup"><span data-stu-id="6204f-117">Selective XML indexes provide the following benefits:</span></span>  
  
1.  <span data-ttu-id="6204f-118">极大改进了针对典型查询负荷的 XML 数据类型的查询性能。</span><span class="sxs-lookup"><span data-stu-id="6204f-118">Greatly improved query performance over the XML data type for typical query loads.</span></span>  
  
2.  <span data-ttu-id="6204f-119">与普通 XML 索引相比，降低了存储要求。</span><span class="sxs-lookup"><span data-stu-id="6204f-119">Reduced storage requirements compared to ordinary XML indexes.</span></span>  
  
3.  <span data-ttu-id="6204f-120">与普通 XML 索引相比，降低了索引维护成本。</span><span class="sxs-lookup"><span data-stu-id="6204f-120">Reduced index maintenance costs compared to ordinary XML indexes.</span></span>  
  
4.  <span data-ttu-id="6204f-121">无需更新应用程序即可享有选择性 XML 索引所带来的好处。</span><span class="sxs-lookup"><span data-stu-id="6204f-121">No need to update applications to benefit from selective XML indexes.</span></span>  
  

  
##  <a name="selective-xml-indexes-and-primary-xml-indexes"></a><a name="compare"></a> <span data-ttu-id="6204f-122">选择性 XML 索引和主 XML 索引</span><span class="sxs-lookup"><span data-stu-id="6204f-122">Selective XML Indexes and Primary XML Indexes</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6204f-123">在大多数情况下，通过创建选择性 XML 索引而不是普通 XML 索引，可以改善性能和提高存储效率。</span><span class="sxs-lookup"><span data-stu-id="6204f-123">Create a selective XML index instead of an ordinary XML index in most cases for better performance and more efficient storage.</span></span>  
  
 <span data-ttu-id="6204f-124">但在以下条件之一成立时，不推荐使用选择性 XML 索引：</span><span class="sxs-lookup"><span data-stu-id="6204f-124">However, a selective XML index is not recommended when either of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="6204f-125">您要映射大量节点路径。</span><span class="sxs-lookup"><span data-stu-id="6204f-125">You map a large number of node paths.</span></span>  
  
-   <span data-ttu-id="6204f-126">您要为未知元素或文档结构内未知位置中的元素支持查询。</span><span class="sxs-lookup"><span data-stu-id="6204f-126">You support queries for unknown elements or elements in an unknown location in the document structure.</span></span>  
  

  
##  <a name="simple-example-of-a-selective-xml-index"></a><a name="example"></a> <span data-ttu-id="6204f-127">选择性 XML 索引的简单示例</span><span class="sxs-lookup"><span data-stu-id="6204f-127">Simple Example of a Selective XML Index</span></span>  
 <span data-ttu-id="6204f-128">请将下面的 XML 片段视为由大约 500,000 行构成的表中的一个 XML 文档：</span><span class="sxs-lookup"><span data-stu-id="6204f-128">Consider the following XML fragment as an XML document in a table of approximately 500,000 rows:</span></span>  
  
```xml  
<book>  
    <created>2004-03-01</created>   
    <authors>Various</authors>  
    <subjects>  
        <subject>English wit and humor -- Periodicals</subject>  
        <subject>AP</subject>   
    </subjects>  
    <title>Punch, or the London Charivari, Volume 156, April 2, 1919</title>  
    <id>etext11617</id>  
</book>  
```  
  
 <span data-ttu-id="6204f-129">对由这么多行构成的这个简单架构创建主 XML 索引会用较长的时间。</span><span class="sxs-lookup"><span data-stu-id="6204f-129">Creating a primary XML index over so many rows of this simple schema takes a long time.</span></span> <span data-ttu-id="6204f-130">对此数据进行查询还面临这样一个问题，即主 XML 索引不支持选择性索引。</span><span class="sxs-lookup"><span data-stu-id="6204f-130">Querying this data also suffers from the fact that a primary XML index does not support selective indexing.</span></span>  
  
 <span data-ttu-id="6204f-131">如果您仅需要对 `/book/title` 路径和 `/book/subjects` 路径查询此数据，则可以创建以下选择性 XML 索引：</span><span class="sxs-lookup"><span data-stu-id="6204f-131">If you only need to query this data over the `/book/title` path and the `/book/subjects` path, you can create the following selective XML index:</span></span>  
  
```sql  
CREATE SELECTIVE XML INDEX SXI_index  
ON Tbl(xmlcol)  
FOR   
(  
    pathTitle = '/book/title/text()' AS XQUERY 'xs:string',   
    pathAuthors = '/book/authors' AS XQUERY 'node()',  
    pathId = '/book/id' AS SQL NVARCHAR(100)  
)  
```  
  
 <span data-ttu-id="6204f-132">前面的语句是您在创建选择性 XML 索引时使用的 CREATE 语法的一个很好的例子。</span><span class="sxs-lookup"><span data-stu-id="6204f-132">The preceding statement is a good example of the CREATE syntax that you use when you create a selective XML index.</span></span> <span data-ttu-id="6204f-133">在 CREATE 语句中，您首先为索引提供名称，并且标识要建立索引的表和 XML 列。</span><span class="sxs-lookup"><span data-stu-id="6204f-133">In the CREATE statement, first you provide a name for the index and identify the table and the XML column to index.</span></span> <span data-ttu-id="6204f-134">然后，您提供要建立索引的路径。</span><span class="sxs-lookup"><span data-stu-id="6204f-134">Then you provide the paths to index.</span></span> <span data-ttu-id="6204f-135">一个路径由三个部分构成：</span><span class="sxs-lookup"><span data-stu-id="6204f-135">A path has three parts:</span></span>  
  
1.  <span data-ttu-id="6204f-136">唯一标识该路径的名称。</span><span class="sxs-lookup"><span data-stu-id="6204f-136">A name that uniquely identifies the path.</span></span>  
  
2.  <span data-ttu-id="6204f-137">描述该路径的 XQuery 表达式。</span><span class="sxs-lookup"><span data-stu-id="6204f-137">An XQuery expression that describes the path.</span></span>  
  
3.  <span data-ttu-id="6204f-138">可选的优化提示。</span><span class="sxs-lookup"><span data-stu-id="6204f-138">Optional optimization hints.</span></span>  
  
 <span data-ttu-id="6204f-139">有关这些元素的详细信息，请参阅 [相关任务](#reltasks)。</span><span class="sxs-lookup"><span data-stu-id="6204f-139">For more information about these elements, see [Related Tasks](#reltasks).</span></span>  
  

  
## <a name="supported-features-prerequisites-and-limitations"></a><span data-ttu-id="6204f-140">支持的功能、先决条件和限制</span><span class="sxs-lookup"><span data-stu-id="6204f-140">Supported Features, Prerequisites, and Limitations</span></span>  
  
###  <a name="supported-xml-features"></a><a name="features"></a> <span data-ttu-id="6204f-141">支持的 XML 功能</span><span class="sxs-lookup"><span data-stu-id="6204f-141">Supported XML Features</span></span>  
 <span data-ttu-id="6204f-142">选择性 XML 索引在 exist()、value() 和 nodes() 方法内支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所支持的 XQuery。</span><span class="sxs-lookup"><span data-stu-id="6204f-142">Selective XML indexes support the XQuery supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inside the exist(), value() and nodes() methods.</span></span>  
  
-   <span data-ttu-id="6204f-143">对于 exist()、value() 和 nodes() 方法，选择性 XML 索引包含用于转换整个表达式的足够信息。</span><span class="sxs-lookup"><span data-stu-id="6204f-143">For the exist(), value() and nodes() methods, selective XML indexes contain enough information to transform the entire expression.</span></span>  
  
-   <span data-ttu-id="6204f-144">对于 query() 和 modify() 方法，选择性 XML 索引只能用于节点筛选。</span><span class="sxs-lookup"><span data-stu-id="6204f-144">For the query() and modify() methods, selective XML indexes may be used for node filtering only.</span></span>  
  
-   <span data-ttu-id="6204f-145">对于 query() 方法，选择性 XML 索引不用于检索结果。</span><span class="sxs-lookup"><span data-stu-id="6204f-145">For the query() method, selective XML indexes are not used to retrieve results.</span></span>  
  
-   <span data-ttu-id="6204f-146">对于 modify() 方法，选择性 XML 索引不用于更新 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="6204f-146">For the modify() method, selective XML indexes are not used to update XML documents.</span></span>  
  

  
###  <a name="unsupported-xml-features"></a><a name="unsupported"></a> <span data-ttu-id="6204f-147">不支持的 XML 功能</span><span class="sxs-lookup"><span data-stu-id="6204f-147">Unsupported XML Features</span></span>  
 <span data-ttu-id="6204f-148">选择性 XML 索引不支持在 XML 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实现中支持的以下功能：</span><span class="sxs-lookup"><span data-stu-id="6204f-148">Selective XML indexes do not support the following features that are supported in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implementation of XML:</span></span>  
  
-   <span data-ttu-id="6204f-149">对具有复杂 XS 类型的节点建立索引：联合类型、序列类型和列表类型。</span><span class="sxs-lookup"><span data-stu-id="6204f-149">Indexing of nodes with complex XS types: union types, sequence types, and list types.</span></span>  
  
-   <span data-ttu-id="6204f-150">对具有二进制 XS 类型的节点建立索引：例如 base64Binary 和 hexBinary。</span><span class="sxs-lookup"><span data-stu-id="6204f-150">Indexing of nodes with binary XS types: for example, base64Binary and hexBinary.</span></span>  
  
-   <span data-ttu-id="6204f-151">使用在末尾包含通配符 `*` 的 XPath 表达式指定要建立索引的节点：例如，`/a/b/c/*`、`/a//b/*` 或 `/a/b/*:c`。</span><span class="sxs-lookup"><span data-stu-id="6204f-151">Specifying the nodes to index with XPath expressions that contain the wildcard character `*` at the end: For example,  `/a/b/c/*`, `/a//b/*`, or `/a/b/*:c`.</span></span>  
  
-   <span data-ttu-id="6204f-152">对子级、属性或后代以外的任何轴建立索引。</span><span class="sxs-lookup"><span data-stu-id="6204f-152">Indexing any axis other than child, attribute, or descendant.</span></span> <span data-ttu-id="6204f-153">`//<step>` 的情况允许作为特例。</span><span class="sxs-lookup"><span data-stu-id="6204f-153">The `//<step>` case is allowed as a special case.</span></span>  
  
-   <span data-ttu-id="6204f-154">对 XML 处理指令和注释建立索引。</span><span class="sxs-lookup"><span data-stu-id="6204f-154">Indexing of XML processing instructions and comments.</span></span>  
  
-   <span data-ttu-id="6204f-155">通过使用 id() 函数为节点指定和检索标识符。</span><span class="sxs-lookup"><span data-stu-id="6204f-155">Specifying and retrieving the identifier for a node by using the id() function.</span></span>  
  

  
###  <a name="prerequisites"></a><a name="prereq"></a><span data-ttu-id="6204f-156">先决条件</span><span class="sxs-lookup"><span data-stu-id="6204f-156">Prerequisites</span></span>  
 <span data-ttu-id="6204f-157">必须首先满足以下先决条件，然后才能对用户表中的 XML 列创建选择性 XML 索引：</span><span class="sxs-lookup"><span data-stu-id="6204f-157">The following prerequisites must exist before you can create a selective XML index over an XML column in a user table:</span></span>  
  
-   <span data-ttu-id="6204f-158">聚集索引必须存在于用户表的主键上。</span><span class="sxs-lookup"><span data-stu-id="6204f-158">A clustered index must exist on the primary key of the user table.</span></span>  
  
-   <span data-ttu-id="6204f-159">在用于选择性 XML 索引时，用户表的主键限制为 128 字节大小。</span><span class="sxs-lookup"><span data-stu-id="6204f-159">The primary key of the user table is limited to a size of 128 bytes when used with selective XML indexes.</span></span>  
  
-   <span data-ttu-id="6204f-160">在用于选择性 XML 索引时，用户表的聚集键限制为 15 列。</span><span class="sxs-lookup"><span data-stu-id="6204f-160">The clustering key of the user table is limited to 15 columns when used with selective XML indexes.</span></span>  
  

  
###  <a name="limitations"></a><a name="limits"></a> <span data-ttu-id="6204f-161">限制</span><span class="sxs-lookup"><span data-stu-id="6204f-161">Limitations</span></span>  
 <span data-ttu-id="6204f-162">**一般要求和限制**</span><span class="sxs-lookup"><span data-stu-id="6204f-162">**General requirements and limitations**</span></span>  
  
-   <span data-ttu-id="6204f-163">只能对单个 XML 列创建各个选择性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="6204f-163">Each selective XML index can only be created on a single XML column.</span></span>  
  
-   <span data-ttu-id="6204f-164">不能对非 XML 列创建选择性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="6204f-164">You cannot create a selective XML index on a non-XML column.</span></span>  
  
-   <span data-ttu-id="6204f-165">表中的每个 XML 列只能具有一个选择性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="6204f-165">Each XML column in a table can have only one selective XML index.</span></span>  
  
-   <span data-ttu-id="6204f-166">每个表最多可具有 249 个选择性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="6204f-166">Each table can have up to 249 selective XML indexes.</span></span>  
  
 <span data-ttu-id="6204f-167">**对支持的对象的限制**</span><span class="sxs-lookup"><span data-stu-id="6204f-167">**Limitations on supported objects**</span></span>  
  
 <span data-ttu-id="6204f-168">不能对以下对象创建选择性 XML 索引：</span><span class="sxs-lookup"><span data-stu-id="6204f-168">You cannot create selective XML indexes on the following objects:</span></span>  
  
1.  <span data-ttu-id="6204f-169">视图中的 XML 列。</span><span class="sxs-lookup"><span data-stu-id="6204f-169">XML columns in a view.</span></span>  
  
2.  <span data-ttu-id="6204f-170">具有 XML 列的表值变量。</span><span class="sxs-lookup"><span data-stu-id="6204f-170">Table-valued variable with XML columns.</span></span>  
  
3.  <span data-ttu-id="6204f-171">XML 类型变量。</span><span class="sxs-lookup"><span data-stu-id="6204f-171">XML type variables.</span></span>  
  
4.  <span data-ttu-id="6204f-172">计算出的 XML 列。</span><span class="sxs-lookup"><span data-stu-id="6204f-172">Computed XML columns.</span></span>  
  
5.  <span data-ttu-id="6204f-173">深度超过 128 个嵌套节点的 XML 列。</span><span class="sxs-lookup"><span data-stu-id="6204f-173">XML columns with a depth of more than 128 nested nodes.</span></span>  
  
 <span data-ttu-id="6204f-174">**与存储相关的限制**</span><span class="sxs-lookup"><span data-stu-id="6204f-174">**Limitations related to storage**</span></span>  
  
 <span data-ttu-id="6204f-175">对于可添加到索引中的 XML 文档中的节点数有一定的限制。</span><span class="sxs-lookup"><span data-stu-id="6204f-175">There is a finite limit on the number of nodes from the XML document that can be added to the index.</span></span> <span data-ttu-id="6204f-176">选择性 XML 索引将 XML 文档映射到单个关系表。</span><span class="sxs-lookup"><span data-stu-id="6204f-176">A selective XML index maps XML documents to a single relational table.</span></span> <span data-ttu-id="6204f-177">因此，在表的任何给定行中，选择性 XML 索引不能具有超过 1024 个非 Null 列。</span><span class="sxs-lookup"><span data-stu-id="6204f-177">Therefore it cannot have more than 1024 non-null columns in any given row of the table.</span></span> <span data-ttu-id="6204f-178">此外，针对稀疏列的许多限制也适用于选择性 XML 索引，因为这些索引使用稀疏列来进行存储。</span><span class="sxs-lookup"><span data-stu-id="6204f-178">Furthermore, many of the limitations of sparse columns also apply to selective XML indexes, because the indexes use sparse columns for storage.</span></span>  
  
 <span data-ttu-id="6204f-179">在任何给定行中支持的非 Null 列的最大数目依赖于列中的数据大小：</span><span class="sxs-lookup"><span data-stu-id="6204f-179">The maximum number of non-null columns supported in any given row depends on the size of the data in the columns:</span></span>  
  
-   <span data-ttu-id="6204f-180">在最佳情形下，在所有列的类型均为 **bit**时支持 1024 个非 Null 列。</span><span class="sxs-lookup"><span data-stu-id="6204f-180">In the best case, 1024 non-null columns are supported when all columns are of type **bit**.</span></span>  
  
-   <span data-ttu-id="6204f-181">在最差情形下，在所有列均为 **varchar**类型的大型对象时仅支持 236 个非 Null 列。</span><span class="sxs-lookup"><span data-stu-id="6204f-181">In the worst case, only 236 non-null columns are supported when all columns are large objects of type **varchar**.</span></span>  
  
 <span data-ttu-id="6204f-182">选择性 XML 索引为建立索引的每个节点路径在内部使用一到四个列。</span><span class="sxs-lookup"><span data-stu-id="6204f-182">Selective XML indexes use from one to four columns internally for every node path that is indexed.</span></span> <span data-ttu-id="6204f-183">可建立索引的节点总数从 60 个节点到几百个节点不等，具体数目取决于已建立索引的路径中数据的实际大小。</span><span class="sxs-lookup"><span data-stu-id="6204f-183">The total number of nodes that can be indexed ranges from 60 to several hundred nodes, depending on the actual size of the data in the indexed paths.</span></span>  
  
-   <span data-ttu-id="6204f-184">在最差情形下，在节点路径定义中使用 `//` 映射某些或所有节点时，已建立索引的节点的最大数目是 60。</span><span class="sxs-lookup"><span data-stu-id="6204f-184">In the worst case, when some or all nodes are mapped using `//` in the node path definition, the maximum number of indexed nodes is 60.</span></span>  
  
-   <span data-ttu-id="6204f-185">在最佳情形下，在节点路径定义中未使用 `//` 映射节点时，已建立索引的节点的最大数目是 200。</span><span class="sxs-lookup"><span data-stu-id="6204f-185">In the best case, when nodes are mapped without using `//` in the node path definition, the maximum number of indexed nodes is 200.</span></span>  
  
 <span data-ttu-id="6204f-186">**在您使用 CREATE 或 ALTER 语句对索引执行操作时，将重新生成选择性 XML 索引。**</span><span class="sxs-lookup"><span data-stu-id="6204f-186">**Selective XML indexes are rebuilt when you CREATE or ALTER the index.**</span></span>  
  
 <span data-ttu-id="6204f-187">在您使用 CREATE 或 ALTER 语句对选择性 XML 索引执行操作时，将在单线程的脱机模式下重新生成该索引。</span><span class="sxs-lookup"><span data-stu-id="6204f-187">When you CREATE or ALTER a selective XML index, it is rebuilt in a single-threaded, offline mode.</span></span> <span data-ttu-id="6204f-188">频繁使用 ALTER 语句会对针对已建立索引的 XML 文档执行的查询的性能造成负面影响。</span><span class="sxs-lookup"><span data-stu-id="6204f-188">Frequently ALTER statements negatively affect the performance of queries over the indexed XML documents.</span></span>  
  
 <span data-ttu-id="6204f-189">**其他限制**</span><span class="sxs-lookup"><span data-stu-id="6204f-189">**Other limitations**</span></span>  
  
-   <span data-ttu-id="6204f-190">在查询提示中不支持选择性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="6204f-190">Selective XML indexes are not supported in query hints.</span></span>  
  
-   <span data-ttu-id="6204f-191">在数据库优化顾问中不支持选择性 XML 索引和辅助选择性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="6204f-191">Selective XML indexes and secondary selective XML indexes are not supported in Database Tuning Advisor.</span></span>  
  

  
##  <a name="related-tasks"></a><a name="reltasks"></a> <span data-ttu-id="6204f-192">相关任务</span><span class="sxs-lookup"><span data-stu-id="6204f-192">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6204f-193">**任务**</span><span class="sxs-lookup"><span data-stu-id="6204f-193">**Task**</span></span>|<span data-ttu-id="6204f-194">**主题**</span><span class="sxs-lookup"><span data-stu-id="6204f-194">**Topic**</span></span>|  
|<span data-ttu-id="6204f-195">在创建或更改选择性 XML 索引时，指定要建立索引的节点路径以及可选的优化提示。</span><span class="sxs-lookup"><span data-stu-id="6204f-195">Specify the node paths that you want to index and optional optimization hints when you create or alter a selective XML index.</span></span>|[<span data-ttu-id="6204f-196">为选择性 XML 索引指定路径和优化提示</span><span class="sxs-lookup"><span data-stu-id="6204f-196">Specify Paths and Optimization Hints for Selective XML Indexes</span></span>](specify-paths-and-optimization-hints-for-selective-xml-indexes.md)|  
|<span data-ttu-id="6204f-197">创建、更改或删除选择性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="6204f-197">Create, alter, or drop a selective XML index.</span></span>|[<span data-ttu-id="6204f-198">创建、更改和删除选择性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="6204f-198">Create, Alter, and Drop Selective XML Indexes</span></span>](create-alter-and-drop-selective-xml-indexes.md)|  
|<span data-ttu-id="6204f-199">创建、更改或删除辅助选择性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="6204f-199">Create, alter, or drop a secondary selective XML index.</span></span>|[<span data-ttu-id="6204f-200">创建、更改和删除辅助选择性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="6204f-200">Create, Alter, and Drop Secondary Selective XML Indexes</span></span>](create-alter-and-drop-secondary-selective-xml-indexes.md)|  
  

  
  
