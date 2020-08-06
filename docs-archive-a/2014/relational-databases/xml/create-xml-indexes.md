---
title: 创建 XML 索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- indexes [XML in SQL Server]
- XML indexes [SQL Server], creating
ms.assetid: 6ecac598-355d-4408-baf7-1b2e8d4cf7c1
author: rothja
ms.author: jroth
ms.openlocfilehash: 9e7800193222b8c9060fee1b247cc5585654cde4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692299"
---
# <a name="create-xml-indexes"></a><span data-ttu-id="a802f-102">创建 XML 索引</span><span class="sxs-lookup"><span data-stu-id="a802f-102">Create XML Indexes</span></span>
  <span data-ttu-id="a802f-103">本主题介绍如何创建主 XML 索引和辅助 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="a802f-103">This topic describes how to create primary and secondary XML indexes.</span></span>  
  
## <a name="creating-a-primary-xml-index"></a><span data-ttu-id="a802f-104">创建主 XML 索引</span><span class="sxs-lookup"><span data-stu-id="a802f-104">Creating a Primary XML Index</span></span>  
 <span data-ttu-id="a802f-105">若要创建主 XML 索引，请使用 [CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] DDL 语句。</span><span class="sxs-lookup"><span data-stu-id="a802f-105">To create a primary XML index, use the [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] DDL statement.</span></span> <span data-ttu-id="a802f-106">XML 索引不完全支持可用于非 XML 索引的所有选项。</span><span class="sxs-lookup"><span data-stu-id="a802f-106">Not all options available for non-XML indexes are supported on XML indexes.</span></span>  
  
 <span data-ttu-id="a802f-107">创建 XML 索引时注意下列事项：</span><span class="sxs-lookup"><span data-stu-id="a802f-107">Note the following when you are creating an XML index:</span></span>  
  
-   <span data-ttu-id="a802f-108">若要创建主 XML 索引，含有被索引的 XML 列的表（称为基表）必须具有主键的聚集索引。</span><span class="sxs-lookup"><span data-stu-id="a802f-108">To create a primary XML index, the table that contains the XML column being indexed, called the base table, must have a clustered index on the primary key.</span></span> <span data-ttu-id="a802f-109">这确保了在对基表进行了分区的情况下，可以使用相同的分区方案和分区函数对主 XML 索引进行分区。</span><span class="sxs-lookup"><span data-stu-id="a802f-109">This makes sure that if the base table is partitioned, the primary XML index can be partitioned by using the same partitioning scheme and partitioning function.</span></span>  
  
-   <span data-ttu-id="a802f-110">如果存在 XML 索引，则不能修改基表的聚集主键。</span><span class="sxs-lookup"><span data-stu-id="a802f-110">If an XML index exists, the clustered, primary key of the table cannot be modified.</span></span> <span data-ttu-id="a802f-111">在修改主键之前，必须删除表的所有 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="a802f-111">You will have to drop all XML indexes on the table before modifying the primary key.</span></span>  
  
-   <span data-ttu-id="a802f-112">您可以对单个 `xml` 类型列创建主 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="a802f-112">A primary XML index can be created on a single `xml` type column.</span></span> <span data-ttu-id="a802f-113">您无法将 XML 类型列作为键列来创建任何其他类型的索引。</span><span class="sxs-lookup"><span data-stu-id="a802f-113">You cannot create any other type of index with the XML type column as a key column.</span></span> <span data-ttu-id="a802f-114">但是，可以在非 XML 索引中包含 `xml` L 类型列。</span><span class="sxs-lookup"><span data-stu-id="a802f-114">However, you can include the `xml` L type column in a non-XML index.</span></span> <span data-ttu-id="a802f-115">表中的每个 `xml` 类型列都可以有自己的主 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="a802f-115">Each `xml` type column in a table can have its own primary XML index.</span></span> <span data-ttu-id="a802f-116">但是，一个 `xml` 类型列只允许有一个主 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="a802f-116">However, only one primary XML index per `xml` type column is permitted.</span></span>  
  
-   <span data-ttu-id="a802f-117">XML 索引和非 XML 索引存在于相同的命名空间中。</span><span class="sxs-lookup"><span data-stu-id="a802f-117">XML indexes exist in the same namespace as non-XML indexes.</span></span> <span data-ttu-id="a802f-118">因此，同一表的 XML 索引和非 XML 索引不能具有相同的名称。</span><span class="sxs-lookup"><span data-stu-id="a802f-118">Therefore, you cannot have an XML index and a non-XML index on the same table with the same name.</span></span>  
  
-   <span data-ttu-id="a802f-119">对于 XML 索引，IGNORE_DUP_KEY 选项和 ONLINE 选项始终设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="a802f-119">IGNORE_DUP_KEY and ONLINE options of are always set to OFF for XML indexes.</span></span> <span data-ttu-id="a802f-120">您可以将这些选项的值指定为 OFF。</span><span class="sxs-lookup"><span data-stu-id="a802f-120">You can specify these options with a value of OFF.</span></span>  
  
-   <span data-ttu-id="a802f-121">将用户表的文件组和分区信息应用于 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="a802f-121">The filegroup or partitioning information of the user table is applied to the XML index.</span></span> <span data-ttu-id="a802f-122">用户无法单独为 XML 索引指定这些信息。</span><span class="sxs-lookup"><span data-stu-id="a802f-122">Users cannot specify these separately on an XML index.</span></span>  
  
-   <span data-ttu-id="a802f-123">DROP_EXISTING 索引选项可以删除主 XML 索引并创建一个新的主 XML 索引，或者删除辅助 XML 索引并创建一个新的辅助 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="a802f-123">The DROP_EXISTING index option can drop a primary XML index and create a new primary XML index, or drop a secondary XML index and create a new secondary XML index.</span></span> <span data-ttu-id="a802f-124">但是，此选项不能通过删除辅助 XML 索引来创建新的主 XML 索引，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="a802f-124">However, this option cannot drop a secondary XML index to create a new primary XML index or vice versa.</span></span>  
  
-   <span data-ttu-id="a802f-125">主 XML 索引名称与视图名称有相同的限制。</span><span class="sxs-lookup"><span data-stu-id="a802f-125">Primary XML index names have the same restrictions as view names.</span></span>  
  
 <span data-ttu-id="a802f-126">不能对 `xml` 视图中的类型列、具有类型列的**表**值变量 `xml` 或类型变量创建 XML 索引 `xml` 。</span><span class="sxs-lookup"><span data-stu-id="a802f-126">You cannot create an XML index on an `xml` type column in a view, on a **table** valued variable with `xml` type columns, or `xml` type variables.</span></span>  
  
-   <span data-ttu-id="a802f-127">若要使用 ALTER TABLE ALTER COLUMN 选项将 `xml` 类型列从非类型化的 XML 更改为类型化的 XML，或者从类型化的 XML 更改为非类型化的 XML，则列不应存在 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="a802f-127">To change an `xml` type column from untyped to typed XML, or vice versa, by using the ALTER TABLE ALTER COLUMN option, no XML index on the column should exist.</span></span> <span data-ttu-id="a802f-128">如果确实存在，则在尝试更改列类型之前必须删除该索引。</span><span class="sxs-lookup"><span data-stu-id="a802f-128">If one does exist, it must be dropped before the column type change is tried.</span></span>  
  
-   <span data-ttu-id="a802f-129">创建 XML 索引时必须将选项 ARITHABORT 设置为 ON。</span><span class="sxs-lookup"><span data-stu-id="a802f-129">The option ARITHABORT must be set to ON when an XML index is created.</span></span> <span data-ttu-id="a802f-130">若要使用 XML 数据类型方法查询、删除、更新 XML 列中的值或向 XML 列中插入值，则必须对连接设置相同的选项。</span><span class="sxs-lookup"><span data-stu-id="a802f-130">To query, insert, delete, or update values in the XML column using XML data type methods, the same option must be set on the connection.</span></span> <span data-ttu-id="a802f-131">如果没有设置，则 XML 数据类型方法将会失败。</span><span class="sxs-lookup"><span data-stu-id="a802f-131">If it is not, the XML data type methods will fail.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a802f-132">有关 XML 索引的信息可以在目录视图中找到。</span><span class="sxs-lookup"><span data-stu-id="a802f-132">Information about an XML index can be found in catalog views.</span></span> <span data-ttu-id="a802f-133">但是，不支持 **sp_helpindex** 。</span><span class="sxs-lookup"><span data-stu-id="a802f-133">However, **sp_helpindex** is not supported.</span></span> <span data-ttu-id="a802f-134">本主题后面部分提供的示例说明了如何查询目录视图以查找 XML 索引信息。</span><span class="sxs-lookup"><span data-stu-id="a802f-134">Examples provided later in this topic show how to query the catalog views to find XML index information.</span></span>  
  
 <span data-ttu-id="a802f-135">如果 XML 数据类型列包含类型为 XML 架构类型 **xs:date** 或 **xs:dateTime** （或这些类型的任何子类型）的值且这些值中的年份小于 1，则在对这样的 XML 数据类型列创建或重新创建主 XML 索引时，索引创建操作在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 和更高版本中将失败。</span><span class="sxs-lookup"><span data-stu-id="a802f-135">When creating or recreating a primary XML index on an XML data type column that contains values of the XML Schema types **xs:date** or **xs:dateTime** (or any subtypes of these types) that have a year of less than 1, the index creation will fail in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions.</span></span> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="a802f-136">允许使用这些值，因此在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]中生成的数据库中创建索引时可能会出现这种问题。</span><span class="sxs-lookup"><span data-stu-id="a802f-136">allowed these values, so this problem can occur when creating indexes in a database generated in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="a802f-137">有关详细信息，请参阅 [类型化的 XML 与非类型化的 XML 的比较](../xml/compare-typed-xml-to-untyped-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="a802f-137">For more information, see [Compare Typed XML to Untyped XML](../xml/compare-typed-xml-to-untyped-xml.md).</span></span>  
  
### <a name="example-creating-a-primary-xml-index"></a><span data-ttu-id="a802f-138">示例：创建主 XML 索引</span><span class="sxs-lookup"><span data-stu-id="a802f-138">Example: Creating a Primary XML Index</span></span>  
 <span data-ttu-id="a802f-139">在大多数示例中，使用的是包含非类型化的 XML 列的表 T (pk INT PRIMARY KEY, xCol XML)。</span><span class="sxs-lookup"><span data-stu-id="a802f-139">Table T (pk INT PRIMARY KEY, xCol XML) with an untyped XML column is used in most of the examples.</span></span> <span data-ttu-id="a802f-140">可以采用简单的方式将它们扩展为类型化的 XML。</span><span class="sxs-lookup"><span data-stu-id="a802f-140">These can be extended to typed XML in a straightforward way.</span></span> <span data-ttu-id="a802f-141">为简化起见，针对 XML 数据实例说明了查询，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a802f-141">For simplicity, queries are described for XML data instances as shown in the following:</span></span>  
  
```  
<book genre="security" publicationdate="2002" ISBN="0-7356-1588-2">  
   <title>Writing Secure Code</title>  
   <author>  
      <first-name>Michael</first-name>  
      <last-name>Howard</last-name>  
   </author>  
   <author>  
      <first-name>David</first-name>  
      <last-name>LeBlanc</last-name>  
   </author>  
   <price>39.99</price>  
</book>  
```  
  
 <span data-ttu-id="a802f-142">下面的语句对表 T 的 XML 列 xCol 创建一个名为 idx_xCol 的 XML 索引：</span><span class="sxs-lookup"><span data-stu-id="a802f-142">The following statement creates an XML index, called idx_xCol, on the XML column xCol of table T:</span></span>  
  
```  
CREATE PRIMARY XML INDEX idx_xCol on T (xCol)  
```  
  
## <a name="creating-a-secondary-xml-index"></a><span data-ttu-id="a802f-143">创建辅助 XML 索引</span><span class="sxs-lookup"><span data-stu-id="a802f-143">Creating a Secondary XML Index</span></span>  
 <span data-ttu-id="a802f-144">使用 [CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] DDL 语句可创建辅助 XML 索引并且可指定所需的辅助 XML 索引的类型。</span><span class="sxs-lookup"><span data-stu-id="a802f-144">Use the [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] DDL statement to create secondary XML indexes and specify the type of the secondary XML index that you want.</span></span>  
  
 <span data-ttu-id="a802f-145">创建辅助 XML 索引时注意下列事项：</span><span class="sxs-lookup"><span data-stu-id="a802f-145">Note the following when you are creating secondary XML indexes:</span></span>  
  
-   <span data-ttu-id="a802f-146">除了 IGNORE_DUP_KEY 和 ONLINE 之外，允许对辅助 XML 索引使用所有适用于非聚集索引的索引选项。</span><span class="sxs-lookup"><span data-stu-id="a802f-146">All indexing options that apply to a nonclustered index, except IGNORE_DUP_KEY and ONLINE, are permitted on secondary XML indexes.</span></span> <span data-ttu-id="a802f-147">对于辅助 XML 索引，这两个选项必须始终设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="a802f-147">The two options must always be set to OFF for secondary XML indexes.</span></span>  
  
-   <span data-ttu-id="a802f-148">辅助索引的分区方式类似于主 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="a802f-148">The secondary indexes are partitioned just like the primary XML index.</span></span>  
  
-   <span data-ttu-id="a802f-149">DROP_EXISTING 可以删除用户表的辅助索引并为用户表创建其他辅助索引。</span><span class="sxs-lookup"><span data-stu-id="a802f-149">DROP_EXISTING can drop a secondary index on the user table and create another secondary index on the user table.</span></span>  
  
 <span data-ttu-id="a802f-150">可以查询 **sys.xml_indexes** 目录视图来检索 XML 索引信息。</span><span class="sxs-lookup"><span data-stu-id="a802f-150">You can query the **sys.xml_indexes** catalog view to retrieve XML index information.</span></span> <span data-ttu-id="a802f-151">请注意， **sys.xml_indexes** 目录视图中的 **secondary_type_desc** 列中提供了辅助索引的类型：</span><span class="sxs-lookup"><span data-stu-id="a802f-151">Note that the **secondary_type_desc** column in the **sys.xml_indexes** catalog view provides the type of secondary index:</span></span>  
  
```  
SELECT  *   
FROM    sys.xml_indexes;  
```  
  
 <span data-ttu-id="a802f-152">**secondary_type_desc** 列中返回的值可以是 NULL、PATH、VALUE 或 PROPERTY。</span><span class="sxs-lookup"><span data-stu-id="a802f-152">The values returned in the **secondary_type_desc** column can be NULL, PATH, VALUE, or PROPERTY.</span></span> <span data-ttu-id="a802f-153">对于主 XML 索引而言，返回的值为 NULL。</span><span class="sxs-lookup"><span data-stu-id="a802f-153">For the primary XML index, the value returned is NULL.</span></span>  
  
### <a name="example-creating-secondary-xml-indexes"></a><span data-ttu-id="a802f-154">示例：创建辅助 XML 索引</span><span class="sxs-lookup"><span data-stu-id="a802f-154">Example: Creating Secondary XML Indexes</span></span>  
 <span data-ttu-id="a802f-155">下面的示例说明了如何创建辅助 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="a802f-155">The following example illustrates how secondary XML indexes are created.</span></span> <span data-ttu-id="a802f-156">此示例还显示了有关您创建的 XML 索引的信息。</span><span class="sxs-lookup"><span data-stu-id="a802f-156">The example also shows information about the XML indexes that you created.</span></span>  
  
```  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML);  
GO  
-- Create primary index.  
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlCol);  
GO  
-- Create secondary indexes (PATH, VALUE, PROPERTY).  
CREATE XML INDEX PIdx_T_XmlCol_PATH ON T(XmlCol)  
USING XML INDEX PIdx_T_XmlCol  
FOR PATH;  
GO  
CREATE XML INDEX PIdx_T_XmlCol_VALUE ON T(XmlCol)  
USING XML INDEX PIdx_T_XmlCol  
FOR VALUE;  
GO  
CREATE XML INDEX PIdx_T_XmlCol_PROPERTY ON T(XmlCol)  
USING XML INDEX PIdx_T_XmlCol  
FOR PROPERTY;  
GO  
```  
  
 <span data-ttu-id="a802f-157">您可以查询 `sys.xml_indexes` 来检索 XML 索引信息。</span><span class="sxs-lookup"><span data-stu-id="a802f-157">You can query the `sys.xml_indexes` to retrieve XML indexes information.</span></span> <span data-ttu-id="a802f-158">`secondary_type_desc` 列提供了辅助索引类型。</span><span class="sxs-lookup"><span data-stu-id="a802f-158">The `secondary_type_desc` column provides the secondary index type.</span></span>  
  
```  
SELECT  *   
FROM    sys.xml_indexes;  
```  
  
 <span data-ttu-id="a802f-159">您还可以在目录视图中查询索引信息。</span><span class="sxs-lookup"><span data-stu-id="a802f-159">You can also query the catalog view for index information.</span></span>  
  
```  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T');  
```  
  
 <span data-ttu-id="a802f-160">您可以添加示例数据然后查看 XML 索引信息。</span><span class="sxs-lookup"><span data-stu-id="a802f-160">You can add sample data and then review the XML index information.</span></span>  
  
```  
INSERT INTO T VALUES (1,  
'<doc id="123">  
<sections>  
<section num="2">  
<heading>Background</heading>  
</section>  
<section num="3">  
<heading>Sort</heading>  
</section>  
<section num="4">  
<heading>Search</heading>  
</section>  
</sections>  
</doc>');  
GO  
-- Check XML index information.  
SELECT *  
FROM   sys.dm_db_index_physical_stats (db_id(), object_id('T'), NULL, NULL, 'DETAILED');  
GO  
-- Space usage of primary XML index  
DECLARE @index_id int;  
SELECT  @index_id = i.index_id  
FROM    sys.xml_indexes i   
WHERE   i.name = 'PIdx_T_XmlCol' and object_name(i.object_id) = 'T';  
  
SELECT *  
FROM sys.dm_db_index_physical_stats (db_id(), object_id('T') , @index_id, DEFAULT, 'DETAILED');  
go  
--- Space usage of secondary XML index (for example PATH secondary index)  PIdx_T_XmlCol_PATH  
DECLARE @index_id int;  
SELECT  @index_id = i.index_id   
FROM    sys.xml_indexes i   
WHERE  i.name = 'PIdx_T_XmlCol_PATH' and object_name(i.object_id) = 'T';  
  
SELECT *  
FROM sys.dm_db_index_physical_stats (db_id(), object_id('T') , @index_id, DEFAULT, 'DETAILED');  
go  
  
-- Space usage of all secondary XML indexes for a particular table  
SELECT i.name, object_name(i.object_id), stats.*   
FROM   sys.dm_db_index_physical_stats (db_id(), object_id('T'), NULL, DEFAULT, 'DETAILED') stats  
JOIN sys.xml_indexes i ON (stats.object_id = i.object_id and stats.index_id = i.index_id)  
WHERE secondary_type is not null;  
-- Drop secondary indexes.  
DROP INDEX PIdx_T_XmlCol_PATH ON T;  
GO  
DROP INDEX PIdx_T_XmlCol_VALUE ON T;  
GO  
DROP INDEX PIdx_T_XmlCol_PROPERTY ON T;  
GO  
-- Drop primary index.  
DROP INDEX PIdx_T_XmlCol ON T;  
-- Drop table T.  
DROP TABLE T;  
Go  
```  
  
## <a name="see-also"></a><span data-ttu-id="a802f-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a802f-161">See Also</span></span>  
 <span data-ttu-id="a802f-162">[XML 索引 (SQL Server)](xml-indexes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a802f-162">[XML Indexes &#40;SQL Server&#41;](xml-indexes-sql-server.md) </span></span>  
 [<span data-ttu-id="a802f-163">XML 数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a802f-163">XML Data &#40;SQL Server&#41;</span></span>](xml-data-sql-server.md)  
  
  
