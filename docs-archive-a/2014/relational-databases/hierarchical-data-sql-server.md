---
title: 层次结构数据 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [SQL Server], tables to support
- hierarchyid [Database Engine], concepts
- hierarchical tables [Database Engine]
- SqlHierarchyId
- hierarchyid [Database Engine]
- hierarchical queries [SQL Server], using hierarchyid data type
ms.assetid: 19aefa9a-fbc2-4b22-92cf-67b8bb01671c
author: rothja
ms.author: jroth
ms.openlocfilehash: 351a5a4aa6bc1655b8da5fced3e51385dd498bdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581193"
---
# <a name="hierarchical-data-sql-server"></a><span data-ttu-id="a314e-102">层次结构数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a314e-102">Hierarchical Data (SQL Server)</span></span>
  <span data-ttu-id="a314e-103">内置 `hierarchyid` 数据类型使存储和查询层次结构数据变得更加容易。</span><span class="sxs-lookup"><span data-stu-id="a314e-103">The built-in `hierarchyid` data type makes it easier to store and query hierarchical data.</span></span> <span data-ttu-id="a314e-104">`hierarchyid`针对表示树（这是最常见的分层数据类型）进行了优化。</span><span class="sxs-lookup"><span data-stu-id="a314e-104">`hierarchyid` is optimized for representing trees, which are the most common type of hierarchical data.</span></span>  
  
 <span data-ttu-id="a314e-105">层次结构数据定义为一组通过层次结构关系互相关联的数据项。</span><span class="sxs-lookup"><span data-stu-id="a314e-105">Hierarchical data is defined as a set of data items that are related to each other by hierarchical relationships.</span></span> <span data-ttu-id="a314e-106">在层次结构关系中，一个数据项是另一个项的父级。</span><span class="sxs-lookup"><span data-stu-id="a314e-106">Hierarchical relationships exist where one item of data is the parent of another item.</span></span> <span data-ttu-id="a314e-107">通常存储在数据库中的层次结构数据示例包括以下内容：</span><span class="sxs-lookup"><span data-stu-id="a314e-107">Examples of the hierarchical data that is commonly stored in databases include the following:</span></span>  
  
-   <span data-ttu-id="a314e-108">组织结构</span><span class="sxs-lookup"><span data-stu-id="a314e-108">An organizational structure</span></span>  
  
-   <span data-ttu-id="a314e-109">文件系统</span><span class="sxs-lookup"><span data-stu-id="a314e-109">A file system</span></span>  
  
-   <span data-ttu-id="a314e-110">项目中的一组任务</span><span class="sxs-lookup"><span data-stu-id="a314e-110">A set of tasks in a project</span></span>  
  
-   <span data-ttu-id="a314e-111">语言术语分类</span><span class="sxs-lookup"><span data-stu-id="a314e-111">A taxonomy of language terms</span></span>  
  
-   <span data-ttu-id="a314e-112">网页间链接图</span><span class="sxs-lookup"><span data-stu-id="a314e-112">A graph of links between Web pages</span></span>  
  
 <span data-ttu-id="a314e-113">使用 [hierarchyid](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) 作为数据类型来创建具有层次结构的表，或描述存储在另一个位置的数据层次结构。</span><span class="sxs-lookup"><span data-stu-id="a314e-113">Use [hierarchyid](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) as a data type to create tables with a hierarchical structure, or to describe the hierarchical structure of data that is stored in another location.</span></span> <span data-ttu-id="a314e-114">在 [中使用](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) hierarchyid 函数 [!INCLUDE[tsql](../includes/tsql-md.md)] 查询和管理层次结构数据。</span><span class="sxs-lookup"><span data-stu-id="a314e-114">Use the [hierarchyid functions](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) in [!INCLUDE[tsql](../includes/tsql-md.md)] to query and manage hierarchical data.</span></span>  
  
##  <a name="key-properties-of-hierarchyid"></a><a name="keyprops"></a> <span data-ttu-id="a314e-115">hierarchyid 的关键属性</span><span class="sxs-lookup"><span data-stu-id="a314e-115">Key Properties of hierarchyid</span></span>  
 <span data-ttu-id="a314e-116">`hierarchyid` 数据类型的值表示树层次结构中的位置。</span><span class="sxs-lookup"><span data-stu-id="a314e-116">A value of the `hierarchyid` data type represents a position in a tree hierarchy.</span></span> <span data-ttu-id="a314e-117">`hierarchyid` 的值具有以下属性：</span><span class="sxs-lookup"><span data-stu-id="a314e-117">Values for `hierarchyid` have the following properties:</span></span>  
  
-   <span data-ttu-id="a314e-118">非常紧凑</span><span class="sxs-lookup"><span data-stu-id="a314e-118">Extremely compact</span></span>  
  
     <span data-ttu-id="a314e-119">在具有 *n* 个节点的树中，表示一个节点所需的平均位数取决于平均端数（节点的平均子级数）。</span><span class="sxs-lookup"><span data-stu-id="a314e-119">The average number of bits that are required to represent a node in a tree with *n* nodes depends on the average fanout (the average number of children of a node).</span></span> <span data-ttu-id="a314e-120">端数较小时 (0-7)，大小约为 6\*logA*n* 位，其中 A 是平均端数。</span><span class="sxs-lookup"><span data-stu-id="a314e-120">For small fanouts, (0-7) the size is about 6\*logA*n* bits, where A is the average fanout.</span></span> <span data-ttu-id="a314e-121">对于平均端数为 6 级、包含 100,000 个人的组织层次结构，一个节点大约占 38 位。</span><span class="sxs-lookup"><span data-stu-id="a314e-121">A node in an organizational hierarchy of 100,000 people with an average fanout of 6 levels takes about 38 bits.</span></span> <span data-ttu-id="a314e-122">存储时，此值向上舍入为 40 位，即 5 字节。</span><span class="sxs-lookup"><span data-stu-id="a314e-122">This is rounded up to 40 bits, or 5 bytes, for storage.</span></span>  
  
-   <span data-ttu-id="a314e-123">按深度优先顺序进行比较</span><span class="sxs-lookup"><span data-stu-id="a314e-123">Comparison is in depth-first order</span></span>  
  
     <span data-ttu-id="a314e-124">假设有两个 `hierarchyid` 值**a**和**b**， **a<b**表示在树的深度优先遍历中，a 位于 b 之前。</span><span class="sxs-lookup"><span data-stu-id="a314e-124">Given two `hierarchyid` values **a** and **b**, **a<b** means a comes before b in a depth-first traversal of the tree.</span></span> <span data-ttu-id="a314e-125">`hierarchyid` 数据类型的索引按深度优先顺序排序，在深度优先遍历中相邻的节点的存储位置也相邻。</span><span class="sxs-lookup"><span data-stu-id="a314e-125">Indexes on `hierarchyid` data types are in depth-first order, and nodes close to each other in a depth-first traversal are stored near each other.</span></span> <span data-ttu-id="a314e-126">例如，一条记录的子级的存储位置与该记录的存储位置是相邻的。</span><span class="sxs-lookup"><span data-stu-id="a314e-126">For example, the children of a record are stored adjacent to that record.</span></span>  
  
-   <span data-ttu-id="a314e-127">支持任意插入和删除</span><span class="sxs-lookup"><span data-stu-id="a314e-127">Support for arbitrary insertions and deletions</span></span>  
  
     <span data-ttu-id="a314e-128">使用 [GetDescendant](/sql/t-sql/data-types/getdescendant-database-engine) 方法，始终可以在任意给定节点的右侧、左侧或任意两个同级节点之间生成同级节点。</span><span class="sxs-lookup"><span data-stu-id="a314e-128">By using the [GetDescendant](/sql/t-sql/data-types/getdescendant-database-engine) method, it is always possible to generate a sibling to the right of any given node, to the left of any given node, or between any two siblings.</span></span> <span data-ttu-id="a314e-129">在层次结构中插入或删除任意数目的节点时，该比较属性保持不变。</span><span class="sxs-lookup"><span data-stu-id="a314e-129">The comparison property is maintained when an arbitrary number of nodes is inserted or deleted from the hierarchy.</span></span> <span data-ttu-id="a314e-130">大多数插入和删除操作都保留了紧凑性属性。</span><span class="sxs-lookup"><span data-stu-id="a314e-130">Most insertions and deletions preserve the compactness property.</span></span> <span data-ttu-id="a314e-131">但是，对于在两个节点之间执行的插入操作，所产生的 hierarchyid 值的表示形式在紧凑性方面将稍微降低。</span><span class="sxs-lookup"><span data-stu-id="a314e-131">However, insertions between two nodes will produce hierarchyid values with a slightly less compact representation.</span></span>  
  
  
##  <a name="limitations-of-hierarchyid"></a><a name="limits"></a> <span data-ttu-id="a314e-132">hierarchyid 的局限性</span><span class="sxs-lookup"><span data-stu-id="a314e-132">Limitations of hierarchyid</span></span>  
 <span data-ttu-id="a314e-133">`hierarchyid`数据类型具有以下限制：</span><span class="sxs-lookup"><span data-stu-id="a314e-133">The `hierarchyid` data type has the following limitations:</span></span>  
  
-   <span data-ttu-id="a314e-134">类型为 `hierarchyid` 的列不会自动表示树。</span><span class="sxs-lookup"><span data-stu-id="a314e-134">A column of type `hierarchyid` does not automatically represent a tree.</span></span> <span data-ttu-id="a314e-135">由应用程序来生成和分配 `hierarchyid` 值，使行与行之间的所需关系反映在这些值中。</span><span class="sxs-lookup"><span data-stu-id="a314e-135">It is up to the application to generate and assign `hierarchyid` values in such a way that the desired relationship between rows is reflected in the values.</span></span> <span data-ttu-id="a314e-136">某些应用程序可能具有 `hierarchyid` 类型的列，该列指示在另一个表中定义的层次结构中的位置。</span><span class="sxs-lookup"><span data-stu-id="a314e-136">Some applications might have a column of type `hierarchyid` that indicates the location in a hierarchy defined in another table.</span></span>  
  
-   <span data-ttu-id="a314e-137">由应用程序来管理生成和分配 `hierarchyid` 值时的并发情况。</span><span class="sxs-lookup"><span data-stu-id="a314e-137">It is up to the application to manage concurrency in generating and assigning `hierarchyid` values.</span></span> <span data-ttu-id="a314e-138">不能保证列中的 `hierarchyid` 值是唯一的，除非应用程序使用唯一键约束或应用程序自身通过自己的逻辑来强制实现唯一性。</span><span class="sxs-lookup"><span data-stu-id="a314e-138">There is no guarantee that `hierarchyid` values in a column are unique unless the application uses a unique key constraint or enforces uniqueness itself through its own logic.</span></span>  
  
-   <span data-ttu-id="a314e-139">由 `hierarchyid` 值表示的层次结构关系不是像外键关系那样强制实现的。</span><span class="sxs-lookup"><span data-stu-id="a314e-139">Hierarchical relationships represented by `hierarchyid` values are not enforced like a foreign key relationship.</span></span> <span data-ttu-id="a314e-140">可能会出现下面这种层次结构关系而且有时这种关系是合理的：A 具有子级 B，然后删除了 A，导致 B 与一条不存在的记录之间存在关系。</span><span class="sxs-lookup"><span data-stu-id="a314e-140">It is possible and sometimes appropriate to have a hierarchical relationship where A has a child B, and then A is deleted leaving B with a relationship to a nonexistent record.</span></span> <span data-ttu-id="a314e-141">如果这种行为不可接受，应用程序在删除父级之前必须先查询其是否有后代。</span><span class="sxs-lookup"><span data-stu-id="a314e-141">If this behavior is unacceptable, the application must query for descendants before deleting parents.</span></span>  
  
  
##  <a name="when-to-use-alternatives-to-hierarchyid"></a><a name="alternatives"></a> <span data-ttu-id="a314e-142">何时使用 hierarchyid 的替代项</span><span class="sxs-lookup"><span data-stu-id="a314e-142">When to Use Alternatives to hierarchyid</span></span>  
 <span data-ttu-id="a314e-143">用于表示层次结构数据的两个 `hierarchyid` 替代项为：</span><span class="sxs-lookup"><span data-stu-id="a314e-143">Two alternatives to `hierarchyid` for representing hierarchical data are:</span></span>  
  
-   <span data-ttu-id="a314e-144">父/子</span><span class="sxs-lookup"><span data-stu-id="a314e-144">Parent/Child</span></span>  
  
-   <span data-ttu-id="a314e-145">XML</span><span class="sxs-lookup"><span data-stu-id="a314e-145">XML</span></span>  
  
 <span data-ttu-id="a314e-146">`hierarchyid` 通常优于这些替代项。</span><span class="sxs-lookup"><span data-stu-id="a314e-146">`hierarchyid` is generally superior to these alternatives.</span></span> <span data-ttu-id="a314e-147">但是，在下面详述的特定情况下，使用这些替代项可能更好。</span><span class="sxs-lookup"><span data-stu-id="a314e-147">However, there are specific situations detailed below where the alternatives are likely superior.</span></span>  
  
### <a name="parentchild"></a><span data-ttu-id="a314e-148">父/子</span><span class="sxs-lookup"><span data-stu-id="a314e-148">Parent/Child</span></span>  
 <span data-ttu-id="a314e-149">使用父/子方法时，每一行都包含对父级的引用。</span><span class="sxs-lookup"><span data-stu-id="a314e-149">When using the Parent/Child approach, each row contains a reference to the parent.</span></span> <span data-ttu-id="a314e-150">下表定义了一个用于在父/子关系中包含父行和子行的典型表：</span><span class="sxs-lookup"><span data-stu-id="a314e-150">The following table defines a typical table used to contain the parent and the child rows in a Parent/Child relationship:</span></span>  
  
```  
USE AdventureWorks2012 ;  
GO  
  
CREATE TABLE ParentChildOrg  
   (  
    BusinessEntityID int PRIMARY KEY,  
    ManagerId int REFERENCES ParentChildOrg(BusinessEntityID),  
    EmployeeName nvarchar(50)   
   ) ;  
GO  
```  
  
 <span data-ttu-id="a314e-151">针对一些常见操作比较父/子与 `hierarchyid`</span><span class="sxs-lookup"><span data-stu-id="a314e-151">Comparing Parent/Child and `hierarchyid` for Common Operations</span></span>  
  
-   <span data-ttu-id="a314e-152">使用 `hierarchyid` 进行子树查询时速度明显加快。</span><span class="sxs-lookup"><span data-stu-id="a314e-152">Subtree queries are significantly faster with `hierarchyid`.</span></span>  
  
-   <span data-ttu-id="a314e-153">使用 `hierarchyid` 进行直接后代查询时速度稍慢。</span><span class="sxs-lookup"><span data-stu-id="a314e-153">Direct descendant queries are slightly slower with `hierarchyid`.</span></span>  
  
-   <span data-ttu-id="a314e-154">使用 `hierarchyid` 移动非叶节点时速度明显减慢。</span><span class="sxs-lookup"><span data-stu-id="a314e-154">Moving non-leaf nodes is slower with `hierarchyid`.</span></span>  
  
-   <span data-ttu-id="a314e-155">使用 `hierarchyid` 插入非叶节点和插入或移动叶节点具有相同的复杂度。</span><span class="sxs-lookup"><span data-stu-id="a314e-155">Inserting non-leaf nodes and inserting or moving leaf nodes has the same complexity with `hierarchyid`.</span></span>  
  
 <span data-ttu-id="a314e-156">当存在以下情况时，使用父/子可能更好：</span><span class="sxs-lookup"><span data-stu-id="a314e-156">Parent/Child might be superior when the following conditions exist:</span></span>  
  
-   <span data-ttu-id="a314e-157">键的大小非常重要。</span><span class="sxs-lookup"><span data-stu-id="a314e-157">The size of the key is critical.</span></span> <span data-ttu-id="a314e-158">在节点数相同的情况下，`hierarchyid` 值等于或大于整型系列（`smallint`、`int`、`bigint`）的值。</span><span class="sxs-lookup"><span data-stu-id="a314e-158">For the same number of nodes, a `hierarchyid` value is equal to or larger than an integer-family (`smallint`, `int`, `bigint`) value.</span></span> <span data-ttu-id="a314e-159">这只是在很少情况下使用父/子的一个原因，因为 `hierarchyid` 在 I/O 局部实用性和 CPU 复杂性方面明显优于使用父/子结构时所需的公用表表达式。</span><span class="sxs-lookup"><span data-stu-id="a314e-159">This is only a reason to use Parent/Child in rare cases, because `hierarchyid` has significantly better locality of I/O and CPU complexity than the common table expressions required when you are using a Parent/Child structure.</span></span>  
  
-   <span data-ttu-id="a314e-160">很少跨层次结构的不同部分执行查询。</span><span class="sxs-lookup"><span data-stu-id="a314e-160">Queries rarely query across sections of the hierarchy.</span></span> <span data-ttu-id="a314e-161">也就是说，通常仅对层次结构中的单个点进行查询。</span><span class="sxs-lookup"><span data-stu-id="a314e-161">In other words, queries usually address only a single point in the hierarchy.</span></span> <span data-ttu-id="a314e-162">在这些情况下，存储在一起并不重要。</span><span class="sxs-lookup"><span data-stu-id="a314e-162">In these cases co-location is not important.</span></span> <span data-ttu-id="a314e-163">例如，如果组织表仅用于为各个雇员处理工资单，则使用父/子更好。</span><span class="sxs-lookup"><span data-stu-id="a314e-163">For example, Parent/Child is superior when the organization table is only used to process payroll for individual employees.</span></span>  
  
-   <span data-ttu-id="a314e-164">非叶子树移动频繁并且性能非常重要。</span><span class="sxs-lookup"><span data-stu-id="a314e-164">Non-leaf subtrees move frequently and performance is very important.</span></span> <span data-ttu-id="a314e-165">在父/子表示形式中，更改层次结构中行的位置将影响单个行。</span><span class="sxs-lookup"><span data-stu-id="a314e-165">In a parent/child representation changing the location of a row in a hierarchy affects a single row.</span></span> <span data-ttu-id="a314e-166">更改使用中某行的位置将 `hierarchyid` 影响*n*行，其中*n*是要移动的子树中的节点数。</span><span class="sxs-lookup"><span data-stu-id="a314e-166">Changing the location of a row in a `hierarchyid` usage affects *n* rows, where *n* is number of nodes in the sub-tree being moved.</span></span>  
  
     <span data-ttu-id="a314e-167">如果非叶子树移动频繁并且性能非常重要，但多数移动操作都是在比较明确的层次结构级别上进行的，请考虑将较高和较低的级别拆分成两个层次结构。</span><span class="sxs-lookup"><span data-stu-id="a314e-167">If the non-leaf subtrees move frequently and performance is important, but most of the moves are at a well-defined level of the hierarchy, consider splitting the higher and lower levels into two hierarchies.</span></span> <span data-ttu-id="a314e-168">这样，所有的移动操作都是移到较高层次结构的叶级。</span><span class="sxs-lookup"><span data-stu-id="a314e-168">This makes all moves into leaf-levels of the higher hierarchy.</span></span> <span data-ttu-id="a314e-169">例如，假设有一个由服务承载的网站的层次结构。</span><span class="sxs-lookup"><span data-stu-id="a314e-169">For instance, consider a hierarchy of Web sites hosted by a service.</span></span> <span data-ttu-id="a314e-170">各网站包含许多以分层方式排列的页面。</span><span class="sxs-lookup"><span data-stu-id="a314e-170">Sites contain many pages arranged in a hierarchical manner.</span></span> <span data-ttu-id="a314e-171">承载的网站可能移动到网站层次结构中的其他位置，但是从属的页面很少会重新排列。</span><span class="sxs-lookup"><span data-stu-id="a314e-171">Hosted sites might be moved to other locations in the site hierarchy, but the subordinate pages are rarely re-arranged.</span></span> <span data-ttu-id="a314e-172">这种情况可表示如下：</span><span class="sxs-lookup"><span data-stu-id="a314e-172">This could be represented via:</span></span>  
  
    ```  
    CREATE TABLE HostedSites   
       (  
        SiteId hierarchyid, PageId hierarchyid  
       ) ;  
    GO  
    ```  
  
  
### <a name="xml"></a><span data-ttu-id="a314e-173">XML</span><span class="sxs-lookup"><span data-stu-id="a314e-173">XML</span></span>  
 <span data-ttu-id="a314e-174">XML 文档是一个树，因此单个 XML 数据类型实例可以表示一个完整的层次结构。</span><span class="sxs-lookup"><span data-stu-id="a314e-174">An XML document is a tree, and therefore a single XML data type instance can represent a complete hierarchy.</span></span> <span data-ttu-id="a314e-175">在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 创建 XML 索引时，在 `hierarchyid` 内部使用值来表示层次结构中的位置。</span><span class="sxs-lookup"><span data-stu-id="a314e-175">In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] when an XML index is created, `hierarchyid` values are used internally to represent the position in the hierarchy.</span></span>  
  
 <span data-ttu-id="a314e-176">当满足以下所有条件时，使用 XML 数据类型会更好：</span><span class="sxs-lookup"><span data-stu-id="a314e-176">Using XML data type can be superior when all the following are true:</span></span>  
  
-   <span data-ttu-id="a314e-177">始终存储并检索整个层次结构。</span><span class="sxs-lookup"><span data-stu-id="a314e-177">The complete hierarchy is always stored and retrieved.</span></span>  
  
-   <span data-ttu-id="a314e-178">应用程序以 XML 格式使用数据。</span><span class="sxs-lookup"><span data-stu-id="a314e-178">The data is consumed in XML format by the application.</span></span>  
  
-   <span data-ttu-id="a314e-179">谓词搜索有极大的局限性，并且性能不是特别重要。</span><span class="sxs-lookup"><span data-stu-id="a314e-179">Predicate searches are extremely limited and not performance critical.</span></span>  
  
 <span data-ttu-id="a314e-180">例如，如果应用程序跟踪多个组织，始终存储并检索整个组织层次结构，并且不在单个组织内部进行查询，则使用如下形式的表可能较为合适：</span><span class="sxs-lookup"><span data-stu-id="a314e-180">For example, if an application tracks multiple organizations, always stores and retrieves the complete organizational hierarchy, and does not query into a single organization, a table of the following form might make sense:</span></span>  
  
```  
CREATE TABLE XMLOrg   
    (  
    Orgid int,  
    Orgdata xml  
    ) ;  
GO  
```  
  
  
##  <a name="indexing-strategies-for-hierarchical-data"></a><a name="indexing"></a> <span data-ttu-id="a314e-181">层次结构数据的索引策略</span><span class="sxs-lookup"><span data-stu-id="a314e-181">Indexing Strategies for Hierarchical Data</span></span>  
 <span data-ttu-id="a314e-182">用于对层次结构数据进行索引的策略有两种：</span><span class="sxs-lookup"><span data-stu-id="a314e-182">There are two strategies for indexing hierarchical data:</span></span>  
  
-   <span data-ttu-id="a314e-183">**深度优先**</span><span class="sxs-lookup"><span data-stu-id="a314e-183">**Depth-first**</span></span>  
  
     <span data-ttu-id="a314e-184">深度优先索引在子树中相邻位置存储行。</span><span class="sxs-lookup"><span data-stu-id="a314e-184">A depth-first index stores the rows in a subtree near each other.</span></span> <span data-ttu-id="a314e-185">例如，一位经理管理的所有雇员都存储在其经理的记录附近。</span><span class="sxs-lookup"><span data-stu-id="a314e-185">For example, all employees that report through a manager are stored near their managers' record.</span></span>  
  
     <span data-ttu-id="a314e-186">在深度优先索引中，一个节点的子树中的所有节点存储在一起。</span><span class="sxs-lookup"><span data-stu-id="a314e-186">In a depth-first index, all nodes in the subtree of a node are co-located.</span></span> <span data-ttu-id="a314e-187">因此，深度优先索引能高效地响应有关子树的查询，“查找此文件夹及其子文件夹中的所有文件”就是这样的一个示例。</span><span class="sxs-lookup"><span data-stu-id="a314e-187">Depth-first indexes are therefore efficient for answering queries about subtrees, such as "Find all files in this folder and its subfolders".</span></span>  
  
-   <span data-ttu-id="a314e-188">**广度优先**</span><span class="sxs-lookup"><span data-stu-id="a314e-188">**Breadth-first**</span></span>  
  
     <span data-ttu-id="a314e-189">广度优先将层次结构中每个级别的各行存储在一起。</span><span class="sxs-lookup"><span data-stu-id="a314e-189">A breadth-first stores the rows each level of the hierarchy together.</span></span> <span data-ttu-id="a314e-190">例如，同一经理直属的各雇员的记录存储在相邻位置。</span><span class="sxs-lookup"><span data-stu-id="a314e-190">For example, the records of employees who directly report to the same manager are stored near each other.</span></span>  
  
     <span data-ttu-id="a314e-191">在广度优先索引中，一个节点的所有直属子级存储在一起。</span><span class="sxs-lookup"><span data-stu-id="a314e-191">In a breadth-first index all direct children of a node are co-located.</span></span> <span data-ttu-id="a314e-192">因此，广度优先索引在响应有关直属子级的查询方面效率很高，“查找此经理直属的所有雇员”就属于这类查询。</span><span class="sxs-lookup"><span data-stu-id="a314e-192">Breadth-first indexes are therefore efficient for answering queries about immediate children, such as "Find all employees who report directly to this manager".</span></span>  
  
 <span data-ttu-id="a314e-193">采用深度优先、广度优先还是结合使用这两种索引，以及将哪一种设为聚集键（如果有），取决于上述两种查询类型的相对重要性以及 SELECT 与DML 操作的相对重要性。</span><span class="sxs-lookup"><span data-stu-id="a314e-193">Whether to have depth-first, breadth-first, or both, and which to make the clustering key (if any), depends on the relative importance of the above types of queries, and the relative importance of SELECT vs. DML operations.</span></span> <span data-ttu-id="a314e-194">有关索引策略的详细示例，请参阅 [Tutorial: Using the hierarchyid Data Type](../relational-databases/tables/tutorial-using-the-hierarchyid-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="a314e-194">For a detailed example of indexing strategies, see [Tutorial: Using the hierarchyid Data Type](../relational-databases/tables/tutorial-using-the-hierarchyid-data-type.md).</span></span>  
  
  
### <a name="creating-indexes"></a><span data-ttu-id="a314e-195">创建索引</span><span class="sxs-lookup"><span data-stu-id="a314e-195">Creating Indexes</span></span>  
 <span data-ttu-id="a314e-196">GetLevel() 方法可用于创建广度优先排序。</span><span class="sxs-lookup"><span data-stu-id="a314e-196">The GetLevel() method can be used to create a breadth first ordering.</span></span> <span data-ttu-id="a314e-197">在下例中，既创建了广度优先索引，又创建了深度优先索引：</span><span class="sxs-lookup"><span data-stu-id="a314e-197">In the following example, both breadth-first and depth-first indexes are created:</span></span>  
  
```wmimof  
USE AdventureWorks2012 ;   
GO  
  
CREATE TABLE Organization  
   (  
    BusinessEntityID hierarchyid,  
    OrgLevel as BusinessEntityID.GetLevel(),   
    EmployeeName nvarchar(50) NOT NULL  
   ) ;  
GO  
  
CREATE CLUSTERED INDEX Org_Breadth_First   
ON Organization(OrgLevel,BusinessEntityID) ;  
GO  
  
CREATE UNIQUE INDEX Org_Depth_First   
ON Organization(BusinessEntityID) ;  
GO  
```  
  
  
## <a name="examples"></a><span data-ttu-id="a314e-198">示例</span><span class="sxs-lookup"><span data-stu-id="a314e-198">Examples</span></span>  
  
### <a name="simple-example"></a><span data-ttu-id="a314e-199">简单示例</span><span class="sxs-lookup"><span data-stu-id="a314e-199">Simple Example</span></span>  
 <span data-ttu-id="a314e-200">以下示例特意进行了简化，以帮助您入门。</span><span class="sxs-lookup"><span data-stu-id="a314e-200">The following example is intentionally simplistic to help you get started.</span></span> <span data-ttu-id="a314e-201">首先创建一个表以保存一些地理数据。</span><span class="sxs-lookup"><span data-stu-id="a314e-201">First create a table to hold some geography data.</span></span>  
  
```  
CREATE TABLE SimpleDemo  
(Level hierarchyid NOT NULL,  
Location nvarchar(30) NOT NULL,  
LocationType nvarchar(9) NULL);  
```  
  
 <span data-ttu-id="a314e-202">现在插入一些洲、国家/地区、州和城市的数据。</span><span class="sxs-lookup"><span data-stu-id="a314e-202">Now insert data for some continents, countries, states, and cities.</span></span>  
  
```  
INSERT SimpleDemo  
VALUES   
('/1/', 'Europe', 'Continent'),  
('/2/', 'South America', 'Continent'),  
('/1/1/', 'France', 'Country'),  
('/1/1/1/', 'Paris', 'City'),  
('/1/2/1/', 'Madrid', 'City'),  
('/1/2/', 'Spain', 'Country'),  
('/3/', 'Antarctica', 'Continent'),  
('/2/1/', 'Brazil', 'Country'),  
('/2/1/1/', 'Brasilia', 'City'),  
('/2/1/2/', 'Bahia', 'State'),  
('/2/1/2/1/', 'Salvador', 'City'),  
('/3/1/', 'McMurdo Station', 'City');  
```  
  
 <span data-ttu-id="a314e-203">选择数据，从而添加将级别数据转换为易于理解的文本值的列。</span><span class="sxs-lookup"><span data-stu-id="a314e-203">Select the data, adding a column that converts the Level data into a text value that is easy to understand.</span></span> <span data-ttu-id="a314e-204">此查询还按 `hierarchyid` 数据类型对结果排序。</span><span class="sxs-lookup"><span data-stu-id="a314e-204">This query also orders the result by the `hierarchyid` data type.</span></span>  
  
```  
SELECT CAST(Level AS nvarchar(100)) AS [Converted Level], *   
FROM SimpleDemo ORDER BY Level;  
```  
  
 [!INCLUDE[ssResult](../includes/ssresult-md.md)]  
  
```  
Converted Level  Level     Location         LocationType  
/1/              0x58      Europe           Continent  
/1/1/            0x5AC0    France           Country  
/1/1/1/          0x5AD6    Paris            City  
/1/2/            0x5B40    Spain            Country  
/1/2/1/          0x5B56    Madrid           City  
/2/              0x68      South America    Continent  
/2/1/            0x6AC0    Brazil           Country  
/2/1/1/          0x6AD6    Brasilia         City  
/2/1/2/          0x6ADA    Bahia            State  
/2/1/2/1/        0x6ADAB0  Salvador         City  
/3/              0x78      Antarctica       Continent  
/3/1/            0x7AC0    McMurdo Station  City  
```  
  
 <span data-ttu-id="a314e-205">请注意，层次结构是有效的结构，即使它在内部不一致。</span><span class="sxs-lookup"><span data-stu-id="a314e-205">Notice that the hierarchy is has a valid structure, even though it is not internally consistent.</span></span> <span data-ttu-id="a314e-206">Bahia 是唯一的州。</span><span class="sxs-lookup"><span data-stu-id="a314e-206">Bahia is the only state.</span></span> <span data-ttu-id="a314e-207">它作为城市 Brasilia 的对等方出现在层次结构中。</span><span class="sxs-lookup"><span data-stu-id="a314e-207">It appears in the hierarchy as a peer of the city Brasilia.</span></span> <span data-ttu-id="a314e-208">同样，McMurdo Station 没有父国家/地区。</span><span class="sxs-lookup"><span data-stu-id="a314e-208">Similarly, McMurdo Station does not have a parent country.</span></span> <span data-ttu-id="a314e-209">用户必须确定此类型的层次结构是否适合于其用途。</span><span class="sxs-lookup"><span data-stu-id="a314e-209">Users must decide if this type of hierarchy is appropriate for their use.</span></span>  
  
 <span data-ttu-id="a314e-210">添加另一行并选择结果。</span><span class="sxs-lookup"><span data-stu-id="a314e-210">Add another row and select the results.</span></span>  
  
```  
INSERT SimpleDemo  
VALUES ('/1/3/1/', 'Kyoto', 'City'), ('/1/3/1/', 'London', 'City');  
SELECT CAST(Level AS nvarchar(100)) AS [Converted Level], * FROM SimpleDemo ORDER BY Level;  
```  
  
 <span data-ttu-id="a314e-211">这演示更多可能的问题。</span><span class="sxs-lookup"><span data-stu-id="a314e-211">This demonstrates more possible problems.</span></span> <span data-ttu-id="a314e-212">Kyoto 可以作为级别 `/1/3/1/` 插入，即使没有父级别 `/1/3/`。</span><span class="sxs-lookup"><span data-stu-id="a314e-212">Kyoto can be inserted as level `/1/3/1/` even though there is no parent level `/1/3/`.</span></span> <span data-ttu-id="a314e-213">London 和 Kyoto 具有相同的 `hierarchyid` 值。</span><span class="sxs-lookup"><span data-stu-id="a314e-213">And both London and Kyoto have the same value for the `hierarchyid`.</span></span> <span data-ttu-id="a314e-214">用户必须再次确定此类型的层次结构是否适合于其用途，并阻止对其用途无效的值。</span><span class="sxs-lookup"><span data-stu-id="a314e-214">Again, users must decide if this type of hierarchy is appropriate for their use, and block values that are invalid for their usage.</span></span>  
  
 <span data-ttu-id="a314e-215">此外，此表未使用层次结构顶层 `'/'`。</span><span class="sxs-lookup"><span data-stu-id="a314e-215">Also, this table did not use the top of the hierarchy `'/'`.</span></span> <span data-ttu-id="a314e-216">该层被省略，因为没有所有州的公共父级。</span><span class="sxs-lookup"><span data-stu-id="a314e-216">It was omitted because there is no common parent of all the continents.</span></span> <span data-ttu-id="a314e-217">可以通过添加整个星球来添加一个顶层。</span><span class="sxs-lookup"><span data-stu-id="a314e-217">You can add one by adding the whole planet.</span></span>  
  
```  
INSERT SimpleDemo  
VALUES ('/', 'Earth', 'Planet');  
```  
  
##  <a name="related-tasks"></a><a name="tasks"></a> <span data-ttu-id="a314e-218">相关任务</span><span class="sxs-lookup"><span data-stu-id="a314e-218">Related Tasks</span></span>  
  
###  <a name="migrating-from-parentchild-to-hierarchyid"></a><a name="migrating"></a> <span data-ttu-id="a314e-219">从父/子迁移到 hierarchyid</span><span class="sxs-lookup"><span data-stu-id="a314e-219">Migrating from Parent/Child to hierarchyid</span></span>  
 <span data-ttu-id="a314e-220">大多数树都使用父/子结构来表示。</span><span class="sxs-lookup"><span data-stu-id="a314e-220">Most trees are represented using Parent/Child.</span></span> <span data-ttu-id="a314e-221">从父/子结构迁移到使用的表的最简单方法 `hierarchyid` 是使用临时列或临时表来跟踪层次结构中每个级别的节点数。</span><span class="sxs-lookup"><span data-stu-id="a314e-221">The easiest way to migrate from a Parent/Child structure to a table using `hierarchyid` is to use a temporary column or a temporary table to keep track of the number of nodes at each level of the hierarchy.</span></span> <span data-ttu-id="a314e-222">有关迁移父/子表的示例，请参阅 [教程：使用 hierarchyid 数据类型](../relational-databases/tables/tutorial-using-the-hierarchyid-data-type.md)的第 1 课。</span><span class="sxs-lookup"><span data-stu-id="a314e-222">For an example of migrating a Parent/Child table, see lesson 1 of [Tutorial: Using the hierarchyid Data Type](../relational-databases/tables/tutorial-using-the-hierarchyid-data-type.md).</span></span>  
  
  
###  <a name="managing-a-tree-using-hierarchyid"></a><a name="BKMK_ManagingTrees"></a> <span data-ttu-id="a314e-223">使用 hierarchyid 管理树</span><span class="sxs-lookup"><span data-stu-id="a314e-223">Managing a Tree Using hierarchyid</span></span>  
 <span data-ttu-id="a314e-224">尽管 `hierarchyid` 列不一定表示树，但应用程序可以很容易地确保此列表示树。</span><span class="sxs-lookup"><span data-stu-id="a314e-224">Although a `hierarchyid` column does not necessarily represent a tree, an application can easily ensure that it does.</span></span>  
  
-   <span data-ttu-id="a314e-225">生成新的值时，请执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="a314e-225">When generating new values, do one of the following:</span></span>  
  
    -   <span data-ttu-id="a314e-226">跟踪父行中的最后一个子级编号。</span><span class="sxs-lookup"><span data-stu-id="a314e-226">Keep track of the last child number in the parent row.</span></span>  
  
    -   <span data-ttu-id="a314e-227">计算最后一个子级。</span><span class="sxs-lookup"><span data-stu-id="a314e-227">Compute the last child.</span></span> <span data-ttu-id="a314e-228">若要高效地执行此操作，需要使用广度优先索引。</span><span class="sxs-lookup"><span data-stu-id="a314e-228">Doing this efficiently requires a breadth-first index.</span></span>  
  
-   <span data-ttu-id="a314e-229">通过对列创建可能属于聚集键的唯一索引，强制实现唯一性。</span><span class="sxs-lookup"><span data-stu-id="a314e-229">Enforce uniqueness by creating a unique index on the column, perhaps as part of a clustering key.</span></span> <span data-ttu-id="a314e-230">若要确保插入的值是唯一的，请执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="a314e-230">To ensure that unique values are inserted, do one of the following:</span></span>  
  
    -   <span data-ttu-id="a314e-231">检测唯一键冲突故障并重试。</span><span class="sxs-lookup"><span data-stu-id="a314e-231">Detect unique key violation failures and retry.</span></span>  
  
    -   <span data-ttu-id="a314e-232">确定每个新子节点的唯一性，并将其作为可序列化事务的一部分插入。</span><span class="sxs-lookup"><span data-stu-id="a314e-232">Determine the uniqueness of each new child node, and insert it as part of a serializable transaction.</span></span>  
  
  
#### <a name="example-using-error-detection"></a><span data-ttu-id="a314e-233">使用错误检测的示例</span><span class="sxs-lookup"><span data-stu-id="a314e-233">Example Using Error Detection</span></span>  
 <span data-ttu-id="a314e-234">在下例中，示例代码计算新子级的 **EmployeeId** 值，接着检测有无键冲突，然后返回 **INS_EMP** 标记以便重新计算新行的 **EmployeeId** 值：</span><span class="sxs-lookup"><span data-stu-id="a314e-234">In the following example, the sample code computes the new child **EmployeeId** value, and then detects any key violation and returns to **INS_EMP** marker to recompute the **EmployeeId** value for the new row:</span></span>  
  
```  
USE AdventureWorks ;  
GO  
  
CREATE TABLE Org_T1  
   (  
    EmployeeId hierarchyid PRIMARY KEY,  
    OrgLevel AS EmployeeId.GetLevel(),  
    EmployeeName nvarchar(50)   
   ) ;  
GO  
  
CREATE INDEX Org_BreadthFirst ON Org_T1(OrgLevel, EmployeeId)  
GO  
  
CREATE PROCEDURE AddEmp(@mgrid hierarchyid, @EmpName nvarchar(50) )   
AS  
BEGIN  
    DECLARE @last_child hierarchyid  
INS_EMP:   
    SELECT @last_child = MAX(EmployeeId) FROM Org_T1   
    WHERE EmployeeId.GetAncestor(1) = @mgrid  
INSERT Org_T1 (EmployeeId, EmployeeName)  
SELECT @mgrid.GetDescendant(@last_child, NULL), @EmpName   
-- On error, return to INS_EMP to recompute @last_child  
IF @@error <> 0 GOTO INS_EMP   
END ;  
GO  
```  
  
  
#### <a name="example-using-a-serializable-transaction"></a><span data-ttu-id="a314e-235">使用可序列化事务的示例</span><span class="sxs-lookup"><span data-stu-id="a314e-235">Example Using a Serializable Transaction</span></span>  
 <span data-ttu-id="a314e-236">该 **Org_BreadthFirst** 索引可确保确定 **@last_child** 使用范围查找。</span><span class="sxs-lookup"><span data-stu-id="a314e-236">The **Org_BreadthFirst** index ensures that determining **@last_child** uses a range seek.</span></span> <span data-ttu-id="a314e-237">除了应用程序可能需要检查的其他错误情况之外，插入后出现重复键冲突表示试图添加具有同一 id 的多个雇员，因此 **@last_child** 必须重新计算。</span><span class="sxs-lookup"><span data-stu-id="a314e-237">In addition to other error cases an application might want to check, a duplicate key violation after the insert indicates an attempt to add multiple employees with the same id, and therefore **@last_child** must be recomputed.</span></span> <span data-ttu-id="a314e-238">下面的代码使用可序列化事务和广度优先索引来计算新节点的值：</span><span class="sxs-lookup"><span data-stu-id="a314e-238">The following code uses a serializable transaction and a breadth-first index to compute the new node value:</span></span>  
  
```  
CREATE TABLE Org_T2  
    (  
    EmployeeId hierarchyid PRIMARY KEY,  
    LastChild hierarchyid,   
    EmployeeName nvarchar(50)   
    ) ;  
GO  
  
CREATE PROCEDURE AddEmp(@mgrid hierarchyid, @EmpName nvarchar(50))   
AS  
BEGIN  
DECLARE @last_child hierarchyid  
SET TRANSACTION ISOLATION LEVEL SERIALIZABLE  
BEGIN TRANSACTION   
  
UPDATE Org_T2   
SET @last_child = LastChild = EmployeeId.GetDescendant(LastChild,NULL)  
WHERE EmployeeId = @mgrid  
INSERT Org_T2 (EmployeeId, EmployeeName)   
    VALUES(@last_child, @EmpName)  
COMMIT  
END ;  
```  
  
 <span data-ttu-id="a314e-239">下面的代码使用三行数据填充表，并返回结果：</span><span class="sxs-lookup"><span data-stu-id="a314e-239">The following code populates the table with three rows and returns the results:</span></span>  
  
```  
INSERT Org_T2 (EmployeeId, EmployeeName)   
    VALUES(hierarchyid::GetRoot(), 'David') ;  
GO  
AddEmp 0x , 'Sariya'  
GO  
AddEmp 0x58 , 'Mary'  
GO  
SELECT * FROM Org_T2  
```  
  
 [!INCLUDE[ssResult](../includes/ssresult-md.md)]  
  
```  
EmployeeId LastChild EmployeeName  
---------- --------- ------------  
0x        0x58       David  
0x58      0x5AC0     Sariya  
0x5AC0    NULL       Mary  
```  
  
  
###  <a name="enforcing-a-tree"></a><a name="BKMK_EnforcingTrees"></a> <span data-ttu-id="a314e-240">强制表示树</span><span class="sxs-lookup"><span data-stu-id="a314e-240">Enforcing a tree</span></span>  
 <span data-ttu-id="a314e-241">以上示例说明了应用程序如何确保树得到维护。</span><span class="sxs-lookup"><span data-stu-id="a314e-241">The above examples illustrate how an application can ensure that a tree is maintained.</span></span> <span data-ttu-id="a314e-242">若要通过使用约束强制表示树，创建定义各节点父级的计算列时可以为它创建一个反过来约束主键 ID 的外键。</span><span class="sxs-lookup"><span data-stu-id="a314e-242">To enforce a tree by using constraints, a computed column that defines the parent of each node can be created with a foreign key constraint back to the primary key id.</span></span>  
  
```  
CREATE TABLE Org_T3  
(  
   EmployeeId hierarchyid PRIMARY KEY,  
   ParentId AS EmployeeId.GetAncestor(1) PERSISTED    
      REFERENCES Org_T3(EmployeeId),  
   LastChild hierarchyid,   
   EmployeeName nvarchar(50)  
)  
GO  
```  
  
 <span data-ttu-id="a314e-243">当用于维护层次结构树的不可信代码对表拥有直接 DML 访问权限时，将优先采用这种强制关系的方法。</span><span class="sxs-lookup"><span data-stu-id="a314e-243">This method of enforcing a relationship is preferred when code that is not trusted to maintain the hierarchical tree has direct DML access to the table.</span></span> <span data-ttu-id="a314e-244">但是，这种方法可能会降低性能，因为必须针对每个 DML 操作检查约束。</span><span class="sxs-lookup"><span data-stu-id="a314e-244">However this method might reduce performance because the constraint must be checked on every DML operation.</span></span>  
  
  
###  <a name="finding-ancestors-by-using-the-clr"></a><a name="findclr"></a> <span data-ttu-id="a314e-245">使用 CLR 查找祖先</span><span class="sxs-lookup"><span data-stu-id="a314e-245">Finding Ancestors by Using the CLR</span></span>  
 <span data-ttu-id="a314e-246">查找级别最低的共同祖先就是一项涉及层次结构中两个节点的常用操作。</span><span class="sxs-lookup"><span data-stu-id="a314e-246">A common operation involving two nodes in a hierarchy is to find the lowest common ancestor.</span></span> <span data-ttu-id="a314e-247">这可以用 [!INCLUDE[tsql](../includes/tsql-md.md)] 或 CLR 编写，因为这两种 `hierarchyid` 类型都可用。</span><span class="sxs-lookup"><span data-stu-id="a314e-247">This can be written in either [!INCLUDE[tsql](../includes/tsql-md.md)] or CLR, because the `hierarchyid` type is available in both.</span></span> <span data-ttu-id="a314e-248">建议用 CLR，因为用它时查找速度会更快。</span><span class="sxs-lookup"><span data-stu-id="a314e-248">CLR is recommended because performance will be faster.</span></span>  
  
 <span data-ttu-id="a314e-249">使用下面的 CLR 代码来列出祖先，并查找级别最低的共同祖先：</span><span class="sxs-lookup"><span data-stu-id="a314e-249">Use the following CLR code to list ancestors and to find the lowest common ancestor:</span></span>  
  
```  
using System;  
using System.Collections;  
using System.Text;  
using Microsoft.SqlServer.Server;  
using Microsoft.SqlServer.Types;  
  
public partial class HierarchyId_Operations  
{  
    [SqlFunction(FillRowMethodName = "FillRow_ListAncestors")]  
    public static IEnumerable ListAncestors(SqlHierarchyId h)  
    {  
        while (!h.IsNull)  
        {  
            yield return (h);  
            h = h.GetAncestor(1);  
        }  
    }  
    public static void FillRow_ListAncestors(Object obj, out SqlHierarchyId ancestor)  
    {  
        ancestor = (SqlHierarchyId)obj;  
    }  
  
    public static HierarchyId CommonAncestor(SqlHierarchyId h1, HierarchyId h2)  
    {  
        while (!h1.IsDescendant(h2))  
            h1 = h1.GetAncestor(1);  
  
        return h1;  
    }  
}  
```  
  
 <span data-ttu-id="a314e-250">若要在以下 **示例中使用** ListAncestor **和** CommonAncestor [!INCLUDE[tsql](../includes/tsql-md.md)] 方法，请在 **中通过执行如下代码生成 DLL 并创建** HierarchyId_Operations [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 程序集：</span><span class="sxs-lookup"><span data-stu-id="a314e-250">To use the **ListAncestor** and **CommonAncestor** methods in the following [!INCLUDE[tsql](../includes/tsql-md.md)] examples, build the DLL and create the **HierarchyId_Operations** assembly in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by executing code similar to the following:</span></span>  
  
```  
CREATE ASSEMBLY HierarchyId_Operations   
FROM '<path to DLL>\ListAncestors.dll'  
GO  
```  
  
  
###  <a name="listing-ancestors"></a><a name="ancestors"></a> <span data-ttu-id="a314e-251">列出祖先</span><span class="sxs-lookup"><span data-stu-id="a314e-251">Listing Ancestors</span></span>  
 <span data-ttu-id="a314e-252">创建节点的祖先列表是一项常用操作，例如可用于显示组织中的职位。</span><span class="sxs-lookup"><span data-stu-id="a314e-252">Creating a list of ancestors of a node is a common operation, for instance to show position in an organization.</span></span> <span data-ttu-id="a314e-253">此操作的其中一种实现方式就是使用表值函数和上面定义的 **HierarchyId_Operations** 类：</span><span class="sxs-lookup"><span data-stu-id="a314e-253">One way of doing this is by using a table-valued-function using the **HierarchyId_Operations** class defined above:</span></span>  
  
 <span data-ttu-id="a314e-254">使用 [!INCLUDE[tsql](../includes/tsql-md.md)]：</span><span class="sxs-lookup"><span data-stu-id="a314e-254">Using [!INCLUDE[tsql](../includes/tsql-md.md)]:</span></span>  
  
```  
CREATE FUNCTION ListAncestors (@node hierarchyid)  
RETURNS TABLE (node hierarchyid)  
AS  
EXTERNAL NAME HierarchyId_Operations.HierarchyId_Operations.ListAncestors  
GO  
```  
  
 <span data-ttu-id="a314e-255">用法示例：</span><span class="sxs-lookup"><span data-stu-id="a314e-255">Example of usage:</span></span>  
  
```  
DECLARE @h hierarchyid  
SELECT @h = OrgNode   
FROM HumanResources.EmployeeDemo    
WHERE LoginID = 'adventure-works\janice0' -- /1/1/5/2/  
  
SELECT LoginID, OrgNode.ToString() AS LogicalNode  
FROM HumanResources.EmployeeDemo AS ED  
JOIN ListAncestors(@h) AS A   
   ON ED.OrgNode = A.Node  
GO  
```  
  
  
###  <a name="finding-the-lowest-common-ancestor"></a><a name="lowestcommon"></a> <span data-ttu-id="a314e-256">查找级别最低的共同祖先</span><span class="sxs-lookup"><span data-stu-id="a314e-256">Finding the Lowest Common Ancestor</span></span>  
 <span data-ttu-id="a314e-257">使用上面定义的 **HierarchyId_Operations** 类创建以下 [!INCLUDE[tsql](../includes/tsql-md.md)] 函数，以便查找涉及层次结构中两个节点的最低级别的共同祖先：</span><span class="sxs-lookup"><span data-stu-id="a314e-257">Using the **HierarchyId_Operations** class defined above, create the following [!INCLUDE[tsql](../includes/tsql-md.md)] function to find the lowest common ancestor involving two nodes in a hierarchy:</span></span>  
  
```  
CREATE FUNCTION CommonAncestor (@node1 hierarchyid, @node2 hierarchyid)  
RETURNS hierarchyid  
AS  
EXTERNAL NAME HierarchyId_Operations.HierarchyId_Operations.CommonAncestor  
GO  
```  
  
 <span data-ttu-id="a314e-258">用法示例：</span><span class="sxs-lookup"><span data-stu-id="a314e-258">Example of usage:</span></span>  
  
```  
DECLARE @h1 hierarchyid, @h2 hierarchyid  
  
SELECT @h1 = OrgNode   
FROM  HumanResources.EmployeeDemo   
WHERE LoginID = 'adventure-works\jossef0' -- Node is /1/1/3/  
  
SELECT @h2 = OrgNode   
FROM HumanResources.EmployeeDemo    
WHERE LoginID = 'adventure-works\janice0' -- Node is /1/1/5/2/  
  
SELECT OrgNode.ToString() AS LogicalNode, LoginID   
FROM HumanResources.EmployeeDemo    
WHERE OrgNode = dbo.CommonAncestor(@h1, @h2) ;  
```  
  
 <span data-ttu-id="a314e-259">最终得到的节点为 /1/1/</span><span class="sxs-lookup"><span data-stu-id="a314e-259">The resultant node is /1/1/</span></span>  
  
  
###  <a name="moving-subtrees"></a><a name="BKMK_MovingSubtrees"></a> <span data-ttu-id="a314e-260">移动子树</span><span class="sxs-lookup"><span data-stu-id="a314e-260">Moving Subtrees</span></span>  
 <span data-ttu-id="a314e-261">另一项常用操作是移动子树。</span><span class="sxs-lookup"><span data-stu-id="a314e-261">Another common operation is moving subtrees.</span></span> <span data-ttu-id="a314e-262">下面的过程将获取的子树 **@oldMgr** ，并使其 (包括 **@oldMgr**) 的子树 **@newMgr** 。</span><span class="sxs-lookup"><span data-stu-id="a314e-262">The procedure below takes the subtree of **@oldMgr** and makes it (including **@oldMgr**) a subtree of **@newMgr**.</span></span>  
  
```  
CREATE PROCEDURE MoveOrg(@oldMgr nvarchar(256), @newMgr nvarchar(256) )  
AS  
BEGIN  
DECLARE @nold hierarchyid, @nnew hierarchyid  
SELECT @nold = OrgNode FROM HumanResources.EmployeeDemo WHERE LoginID = @oldMgr ;  
  
SET TRANSACTION ISOLATION LEVEL SERIALIZABLE  
BEGIN TRANSACTION  
SELECT @nnew = OrgNode FROM HumanResources.EmployeeDemo WHERE LoginID = @newMgr ;  
  
SELECT @nnew = @nnew.GetDescendant(max(OrgNode), NULL)   
FROM HumanResources.EmployeeDemo WHERE OrgNode.GetAncestor(1)=@nnew ;  
  
UPDATE HumanResources.EmployeeDemo    
SET OrgNode = OrgNode.GetReparentedValue(@nold, @nnew)  
WHERE OrgNode.IsDescendantOf(@nold) = 1 ;  
  
COMMIT TRANSACTION  
END ;  
GO  
```  
  
  
## <a name="see-also"></a><span data-ttu-id="a314e-263">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a314e-263">See Also</span></span>  
 <span data-ttu-id="a314e-264">[hierarchyid 数据类型方法引用](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) </span><span class="sxs-lookup"><span data-stu-id="a314e-264">[hierarchyid Data Type Method Reference](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) </span></span>  
 <span data-ttu-id="a314e-265">[Tutorial: Using the hierarchyid Data Type](../relational-databases/tables/tutorial-using-the-hierarchyid-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="a314e-265">[Tutorial: Using the hierarchyid Data Type](../relational-databases/tables/tutorial-using-the-hierarchyid-data-type.md) </span></span>  
 [<span data-ttu-id="a314e-266">hierarchyid (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a314e-266">hierarchyid &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/hierarchyid-data-type-method-reference)  
  
  
