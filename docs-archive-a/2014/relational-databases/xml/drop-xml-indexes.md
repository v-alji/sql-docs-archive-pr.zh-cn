---
title: 删除 XML 索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- removing indexes
- dropping indexes
- XML indexes [SQL Server], dropping
ms.assetid: 7591ebea-34af-4925-8553-b2adb5b487c2
author: rothja
ms.author: jroth
ms.openlocfilehash: b7d4621cf2182b4587b12665a1cfe10ddbe0db3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577426"
---
# <a name="drop-xml-indexes"></a><span data-ttu-id="2e7d6-102">删除 XML 索引</span><span class="sxs-lookup"><span data-stu-id="2e7d6-102">Drop XML Indexes</span></span>
  <span data-ttu-id="2e7d6-103">[DROP INDEX (Transact-SQL)](/sql/t-sql/statements/drop-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] 语句可用于删除现有的主（或辅助）XML 索引和非 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="2e7d6-103">The [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] statement can be used to drop existing primary or secondary XML and non-XML indexes.</span></span> <span data-ttu-id="2e7d6-104">但是，任何 DROP INDEX 选项都不会应用于 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="2e7d6-104">However, no options of DROP INDEX apply to XML indexes.</span></span> <span data-ttu-id="2e7d6-105">如果删除主 XML 索引，则会删除任何现有的辅助索引。</span><span class="sxs-lookup"><span data-stu-id="2e7d6-105">If you drop the primary XML index, any secondary indexes that are present are also deleted.</span></span>  
  
 <span data-ttu-id="2e7d6-106">以后将逐步停止使用带有 *TableName.IndexName* 的 DROP 语法，并且 XML 索引不支持该语法。</span><span class="sxs-lookup"><span data-stu-id="2e7d6-106">The DROP syntax with *TableName.IndexName* is being phased out and is not supported for XML indexes.</span></span>  
  
## <a name="example-creating-and-dropping-a-primary-xml-index"></a><span data-ttu-id="2e7d6-107">示例：创建和删除主 XML 索引</span><span class="sxs-lookup"><span data-stu-id="2e7d6-107">Example: Creating and Dropping a Primary XML Index</span></span>  
 <span data-ttu-id="2e7d6-108">在以下示例中，XML 索引是对 `xml` 类型列创建的。</span><span class="sxs-lookup"><span data-stu-id="2e7d6-108">In the following example, an XML index is created on an `xml` type column.</span></span>  
  
```  
DROP TABLE T  
GO  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML)  
GO  
-- Create Primary XML index   
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlCol)  
GO  
-- Verify the index creation.   
-- Note index type is 3 for xml indexes.  
-- Note the type 3 is index on XML type.  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T')  
AND name='PIdx_T_XmlCol'   
-- Drop the index.  
DROP INDEX PIdx_T_XmlCol ON T  
```  
  
 <span data-ttu-id="2e7d6-109">删除表后，也将自动删除其所有的 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="2e7d6-109">When a table is dropped, all the XML indexes on it are also automatically dropped.</span></span> <span data-ttu-id="2e7d6-110">但是，如果 XML 列存在 XML 索引，则不会从表中删除该列。</span><span class="sxs-lookup"><span data-stu-id="2e7d6-110">However, an XML column cannot be dropped from a table if an XML index exists on the column.</span></span>  
  
 <span data-ttu-id="2e7d6-111">在以下示例中，XML 索引是对 `xml` 类型列创建的。</span><span class="sxs-lookup"><span data-stu-id="2e7d6-111">In the following example, an XML index is created on an `xml` type column.</span></span> <span data-ttu-id="2e7d6-112">有关详细信息，请参阅 [类型化的 XML 与非类型化的 XML 的比较](../xml/compare-typed-xml-to-untyped-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="2e7d6-112">For more information, see [Compare Typed XML to Untyped XML](../xml/compare-typed-xml-to-untyped-xml.md).</span></span>  
  
```  
CREATE TABLE TestTable(  
 Col1 int primary key,   
 Col2 xml (Production.ProductDescriptionSchemaCollection))   
GO  
```  
  
 <span data-ttu-id="2e7d6-113">此时，可以对 `Co12`创建主 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="2e7d6-113">Now, you can create a primary XML index on `Co12`.</span></span>  
  
```  
CREATE PRIMARY XML INDEX PIdx_TestTable_Col2   
ON TestTable(Col2)  
GO  
```  
  
## <a name="example-creating-an-xml-index-by-using-the-drop_existing-index-option"></a><span data-ttu-id="2e7d6-114">示例：使用 DROP_EXISTING 索引选项创建 XML 索引</span><span class="sxs-lookup"><span data-stu-id="2e7d6-114">Example: Creating an XML Index by Using the DROP_EXISTING Index Option</span></span>  
 <span data-ttu-id="2e7d6-115">在以下示例中，XML 索引是针对列 (`XmlColx`) 创建的。</span><span class="sxs-lookup"><span data-stu-id="2e7d6-115">In the following example, an XML index is created on a column (`XmlColx`).</span></span> <span data-ttu-id="2e7d6-116">然后，针对不同的列 (`XmlColy`) 创建同名的另一个 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="2e7d6-116">Then, another XML index with the same name is created on a different column, (`XmlColy`).</span></span> <span data-ttu-id="2e7d6-117">由于指定了 `DROP_EXISTING` 选项，因此将删除 (`XmlColx)` 现有的 XML 索引并为 (`XmlColy`) 创建新的 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="2e7d6-117">Because the `DROP_EXISTING` option is specified, the existing XML index on (`XmlColx)` is dropped and a new XML index on (`XmlColy`) is created.</span></span>  
  
```  
DROP TABLE T  
GO  
CREATE TABLE T(Col1 int primary key, XmlColx xml, XmlColy xml)  
GO  
-- Create XML index on XmlColx.  
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlColx)  
GO  
-- Create same name XML index on XmlColy.  
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlColy)   
WITH (DROP_EXISTING = ON)  
-- Verify the index is created on XmlColy.d.  
SELECT sc.name   
FROM   sys.xml_indexes si inner join sys.index_columns sic   
ON     sic.object_id=si.object_id and sic.index_id=si.index_id  
INNER  join sys.columns sc on sc.object_id=sic.object_id   
AND    sc.column_id=sic.column_id  
WHERE  si.name='PIdx_T_XmlCol'   
AND    si.object_id=object_id('T')  
```  
  
 <span data-ttu-id="2e7d6-118">此查询返回对其创建指定的 XML 索引的列的名称。</span><span class="sxs-lookup"><span data-stu-id="2e7d6-118">This query returns the column name on which the specified XML index is created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e7d6-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2e7d6-119">See Also</span></span>  
 [<span data-ttu-id="2e7d6-120">XML 索引 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2e7d6-120">XML Indexes &#40;SQL Server&#41;</span></span>](xml-indexes-sql-server.md)  
  
  
