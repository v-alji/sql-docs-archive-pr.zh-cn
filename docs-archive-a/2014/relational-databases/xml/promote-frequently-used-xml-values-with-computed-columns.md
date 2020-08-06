---
title: 使用计算列提升常用的 XML 值 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- promoting properties [XML in SQL Server]
- property promotion [XML in SQL Server]
ms.assetid: f5111896-c2fd-4209-b500-f2baa45489ad
author: rothja
ms.author: jroth
ms.openlocfilehash: bfb83b7772ffd92eab7087db11e4c3ffd96afa47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690409"
---
# <a name="promote-frequently-used-xml-values-with-computed-columns"></a><span data-ttu-id="5dec3-102">使用计算列提升常用的 XML 值</span><span class="sxs-lookup"><span data-stu-id="5dec3-102">Promote Frequently Used XML Values with Computed Columns</span></span>
  <span data-ttu-id="5dec3-103">如果主要是对少数元素和属性值进行查询，您可能希望将这些数量提升到关系列。</span><span class="sxs-lookup"><span data-stu-id="5dec3-103">If queries are made principally on a small number of element and attribute values, you may want to promote those quantities into relational columns.</span></span> <span data-ttu-id="5dec3-104">检索整个 XML 实例，但只对一小部分 XML 数据进行查询时，这很有用。</span><span class="sxs-lookup"><span data-stu-id="5dec3-104">This is helpful when queries are issued on a small part of the XML data while the whole XML instance is retrieved.</span></span> <span data-ttu-id="5dec3-105">不必对 XML 列创建 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="5dec3-105">Creating an XML index on the XML column is not required.</span></span> <span data-ttu-id="5dec3-106">但可以对提升的列进行索引。</span><span class="sxs-lookup"><span data-stu-id="5dec3-106">Instead, the promoted column can be indexed.</span></span> <span data-ttu-id="5dec3-107">必须编写查询才能使用提升的列。</span><span class="sxs-lookup"><span data-stu-id="5dec3-107">Queries must be written to use the promoted column.</span></span> <span data-ttu-id="5dec3-108">也就是说，查询优化器不会将对 XML 列的查询再定向到提升的列。</span><span class="sxs-lookup"><span data-stu-id="5dec3-108">That is, the query optimizer does not target again the queries on the XML column to the promoted column.</span></span>  
  
 <span data-ttu-id="5dec3-109">提升的列可以是同一个表中的计算列，也可以是表中用户维护的单独列。</span><span class="sxs-lookup"><span data-stu-id="5dec3-109">The promoted column can be a computed column in the same table or it can be a separate, user-maintained column in a table.</span></span> <span data-ttu-id="5dec3-110">从每个 XML 实例提升单一值时，这就足够了。</span><span class="sxs-lookup"><span data-stu-id="5dec3-110">This is sufficient when singleton values are promoted from each XML instance.</span></span> <span data-ttu-id="5dec3-111">但是，对于多值属性，则必须为属性创建单独的表，如下节所述。</span><span class="sxs-lookup"><span data-stu-id="5dec3-111">However, for multi-valued properties, you have to create a separate table for the property, as described in the following section.</span></span>  
  
## <a name="computed-column-based-on-the-xml-data-type"></a><span data-ttu-id="5dec3-112">基于 xml 数据类型的计算列</span><span class="sxs-lookup"><span data-stu-id="5dec3-112">Computed Column Based on the xml Data Type</span></span>  
 <span data-ttu-id="5dec3-113">可以通过使用调用数据类型方法的用户定义函数来创建计算列 `xml` 。</span><span class="sxs-lookup"><span data-stu-id="5dec3-113">A computed column can be created by using a user-defined function that invokes `xml` data type methods.</span></span> <span data-ttu-id="5dec3-114">计算列的类型可以是任何 SQL 类型，包括 XML。</span><span class="sxs-lookup"><span data-stu-id="5dec3-114">The type of the computed column can be any SQL type, including XML.</span></span> <span data-ttu-id="5dec3-115">下面的示例说明了这一点。</span><span class="sxs-lookup"><span data-stu-id="5dec3-115">This is illustrated in the following example.</span></span>  
  
### <a name="example-computed-column-based-on-the-xml-data-type-method"></a><span data-ttu-id="5dec3-116">示例：基于 xml 数据类型方法的计算列</span><span class="sxs-lookup"><span data-stu-id="5dec3-116">Example: Computed Column Based on the xml Data Type Method</span></span>  
 <span data-ttu-id="5dec3-117">为书的 ISBN 号创建用户定义函数：</span><span class="sxs-lookup"><span data-stu-id="5dec3-117">Create the user-defined function for a book ISBN number:</span></span>  
  
```  
CREATE FUNCTION udf_get_book_ISBN (@xData xml)  
RETURNS varchar(20)  
BEGIN  
   DECLARE @ISBN   varchar(20)  
   SELECT @ISBN = @xData.value('/book[1]/@ISBN', 'varchar(20)')  
   RETURN @ISBN   
END  
```  
  
 <span data-ttu-id="5dec3-118">在表中为 ISBN 添加计算列：</span><span class="sxs-lookup"><span data-stu-id="5dec3-118">Add a computed column to the table for the ISBN:</span></span>  
  
```  
ALTER TABLE      T  
ADD   ISBN AS dbo.udf_get_book_ISBN(xCol)  
```  
  
 <span data-ttu-id="5dec3-119">可以按通常的方式对计算列创建索引。</span><span class="sxs-lookup"><span data-stu-id="5dec3-119">The computed column can be indexed in the usual way.</span></span>  
  
### <a name="example-queries-on-a-computed-column-based-on-xml-data-type-methods"></a><span data-ttu-id="5dec3-120">示例：针对基于 xml 数据类型方法的计算列的查询</span><span class="sxs-lookup"><span data-stu-id="5dec3-120">Example: Queries on a Computed Column Based on xml Data Type Methods</span></span>  
 <span data-ttu-id="5dec3-121">若要获得其 ISBN 为 0-7356-1588-2 的 <`book`>：</span><span class="sxs-lookup"><span data-stu-id="5dec3-121">To obtain the <`book`> whose ISBN is 0-7356-1588-2:</span></span>  
  
```  
SELECT xCol  
FROM   T  
WHERE  xCol.exist('/book/@ISBN[. = "0-7356-1588-2"]') = 1  
```  
  
 <span data-ttu-id="5dec3-122">可以重新编写对 XML 列的查询以使用计算列，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5dec3-122">The query on the XML column can be rewritten to use the computed column as follows:</span></span>  
  
```  
SELECT xCol  
FROM   T  
WHERE  ISBN = '0-7356-1588-2'  
```  
  
 <span data-ttu-id="5dec3-123">您可以使用用户定义函数创建用户定义函数以返回 `xml` 数据类型和计算列。</span><span class="sxs-lookup"><span data-stu-id="5dec3-123">You can create a user-defined function to return the `xml` data type and a computed column by using the user-defined function.</span></span> <span data-ttu-id="5dec3-124">但是，不能对 XML 计算列创建 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="5dec3-124">However, you cannot create an XML index on the computed, XML column.</span></span>  
  
## <a name="creating-property-tables"></a><span data-ttu-id="5dec3-125">创建属性表</span><span class="sxs-lookup"><span data-stu-id="5dec3-125">Creating Property Tables</span></span>  
 <span data-ttu-id="5dec3-126">您可能希望将 XML 数据中的某些多值属性提升到一个或多个表中，对那些表创建索引，并再次定向查询以使用这些表。</span><span class="sxs-lookup"><span data-stu-id="5dec3-126">You may want to promote some of the multivalued properties from your XML data into one or more tables, create indexes on those tables, and target again your queries to use them.</span></span> <span data-ttu-id="5dec3-127">典型的情况是少数属性占了大部分查询工作负荷。</span><span class="sxs-lookup"><span data-stu-id="5dec3-127">A typical scenario is one in which a small number of properties covers most of your query workload.</span></span> <span data-ttu-id="5dec3-128">您可以执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="5dec3-128">You can do the following:</span></span>  
  
-   <span data-ttu-id="5dec3-129">创建一个或多个表来保存多值属性。</span><span class="sxs-lookup"><span data-stu-id="5dec3-129">Create one or more tables to hold the multivalued properties.</span></span> <span data-ttu-id="5dec3-130">您会发现可以很方便做到：每个表存储一个属性，以及在属性表中复制基表的主键以便与基表进行后向联接。</span><span class="sxs-lookup"><span data-stu-id="5dec3-130">You may find it convenient to store one property per table and duplicate the primary key of the base table in the property tables for back joining with the base table.</span></span>  
  
-   <span data-ttu-id="5dec3-131">如果希望维护属性的相对顺序，必须为相对顺序引入一个单独的列。</span><span class="sxs-lookup"><span data-stu-id="5dec3-131">If you want to maintain the relative order of the properties, you have to introduce a separate column for the relative order.</span></span>  
  
-   <span data-ttu-id="5dec3-132">为 XML 列创建触发器以维护属性表。</span><span class="sxs-lookup"><span data-stu-id="5dec3-132">Create triggers on the XML column to maintain the property tables.</span></span> <span data-ttu-id="5dec3-133">在触发器中，执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="5dec3-133">Within the triggers, do one of the following:</span></span>  
  
    -   <span data-ttu-id="5dec3-134">使用 `xml` 数据类型方法（如**节点 ( # B1**和\*\*value ( # B3 \*\*）来插入和删除属性表的行。</span><span class="sxs-lookup"><span data-stu-id="5dec3-134">Use `xml` data type methods, such as **nodes()** and **value()**, to insert and delete rows of the property tables.</span></span>  
  
    -   <span data-ttu-id="5dec3-135">在公共语言运行时 (CLR) 中创建流式表值函数来插入和删除属性表的行。</span><span class="sxs-lookup"><span data-stu-id="5dec3-135">Create streaming table-valued functions in the common language runtime (CLR) to insert and delete rows of the property tables.</span></span>  
  
    -   <span data-ttu-id="5dec3-136">编写对属性表进行 SQL 访问的查询和对基表中的 XML 列进行 XML 访问的查询，这些表之间通过主键联接起来。</span><span class="sxs-lookup"><span data-stu-id="5dec3-136">Write queries for SQL access to the property tables and for XML access to the XML column in the base table, with joins between the tables by using their primary key.</span></span>  
  
### <a name="example-create-a-property-table"></a><span data-ttu-id="5dec3-137">示例：创建属性表</span><span class="sxs-lookup"><span data-stu-id="5dec3-137">Example: Create a Property Table</span></span>  
 <span data-ttu-id="5dec3-138">为了进行说明，假定您希望提升作者的名字。</span><span class="sxs-lookup"><span data-stu-id="5dec3-138">For illustration, assume that you want to promote the first name of the authors.</span></span> <span data-ttu-id="5dec3-139">书有一个或多个作者，因此名字为多值属性。</span><span class="sxs-lookup"><span data-stu-id="5dec3-139">Books have one or more authors, so that first name is a multivalued property.</span></span> <span data-ttu-id="5dec3-140">每个名字都存储在属性表的单独行中。</span><span class="sxs-lookup"><span data-stu-id="5dec3-140">Each first name is stored in a separate row of a property table.</span></span> <span data-ttu-id="5dec3-141">在属性表中复制基表的主键以便进行后向联接。</span><span class="sxs-lookup"><span data-stu-id="5dec3-141">The primary key of the base table is duplicated in the property table for back join.</span></span>  
  
```  
create table tblPropAuthor (propPK int, propAuthor varchar(max))  
```  
  
### <a name="example-create-a-user-defined-function-to-generate-a-rowset-from-an-xml-instance"></a><span data-ttu-id="5dec3-142">示例：创建用户定义函数以从 XML 实例生成行集</span><span class="sxs-lookup"><span data-stu-id="5dec3-142">Example: Create a User-defined Function to Generate a Rowset from an XML Instance</span></span>  
 <span data-ttu-id="5dec3-143">以下表值函数 udf_XML2Table 接受主键值和 XML 实例。</span><span class="sxs-lookup"><span data-stu-id="5dec3-143">The following table-valued function, udf_XML2Table, accepts a primary key value and an XML instance.</span></span> <span data-ttu-id="5dec3-144">它检索 <`book`> 元素的所有作者的名字，然后返回主键-名字对行集。</span><span class="sxs-lookup"><span data-stu-id="5dec3-144">It retrieves the first name of all authors of the <`book`> elements and returns a rowset of primary key, first name pairs.</span></span>  
  
```  
create function udf_XML2Table (@pk int, @xCol xml)  
returns @ret_Table table (propPK int, propAuthor varchar(max))  
with schemabinding  
as  
begin  
      insert into @ret_Table   
      select @pk, nref.value('.', 'varchar(max)')  
      from   @xCol.nodes('/book/author/first-name') R(nref)  
      return  
end  
```  
  
### <a name="example-create-triggers-to-populate-a-property-table"></a><span data-ttu-id="5dec3-145">示例：创建触发器以填充属性表</span><span class="sxs-lookup"><span data-stu-id="5dec3-145">Example: Create Triggers to Populate a Property Table</span></span>  
 <span data-ttu-id="5dec3-146">插入触发器将行插入属性表：</span><span class="sxs-lookup"><span data-stu-id="5dec3-146">The insert trigger inserts rows into the property table:</span></span>  
  
```  
create trigger trg_docs_INS on T for insert  
as  
      declare @wantedXML xml  
      declare @FK int  
      select @wantedXML = xCol from inserted  
      select @FK = PK from inserted  
  
   insert into tblPropAuthor  
   select * from dbo.udf_XML2Table(@FK, @wantedXML)  
```  
  
 <span data-ttu-id="5dec3-147">删除触发器根据删除行的主键值删除属性表中的行：</span><span class="sxs-lookup"><span data-stu-id="5dec3-147">The delete trigger deletes the rows from the property table based on the primary key value of the deleted rows:</span></span>  
  
```  
create trigger trg_docs_DEL on T for delete  
as  
   declare @FK int  
   select @FK = PK from deleted  
   delete tblPropAuthor where propPK = @FK  
```  
  
 <span data-ttu-id="5dec3-148">更新触发器删除与更新的 XML 实例对应的属性表中的现有行，然后将新行插入属性表：</span><span class="sxs-lookup"><span data-stu-id="5dec3-148">The update trigger deletes the existing rows in the property table corresponding to the updated XML instance and inserts new rows into the property table:</span></span>  
  
```  
create trigger trg_docs_UPD  
on T  
for update  
as  
if update(xCol) or update(pk)  
begin  
      declare @FK int  
      declare @wantedXML xml  
      select @FK = PK from deleted  
      delete tblPropAuthor where propPK = @FK  
  
   select @wantedXML = xCol from inserted  
   select @FK = pk from inserted  
  
   insert into tblPropAuthor   
      select * from dbo.udf_XML2Table(@FK, @wantedXML)  
end  
```  
  
### <a name="example-find-xml-instances-whose-authors-have-the-same-first-name"></a><span data-ttu-id="5dec3-149">示例：查找其作者名字相同的 XML 实例</span><span class="sxs-lookup"><span data-stu-id="5dec3-149">Example: Find XML Instances Whose Authors Have the Same First Name</span></span>  
 <span data-ttu-id="5dec3-150">可以对 XML 列执行此查询。</span><span class="sxs-lookup"><span data-stu-id="5dec3-150">The query can be formed on the XML column.</span></span> <span data-ttu-id="5dec3-151">此外，它也可以在属性表中搜索名字“David”，然后与基表进行后向联接以返回 XML 实例。</span><span class="sxs-lookup"><span data-stu-id="5dec3-151">Alternatively, it can search the property table for first name "David" and perform a back join with the base table to return the XML instance.</span></span> <span data-ttu-id="5dec3-152">例如：</span><span class="sxs-lookup"><span data-stu-id="5dec3-152">For example:</span></span>  
  
```  
SELECT xCol   
FROM     T JOIN tblPropAuthor ON T.pk = tblPropAuthor.propPK  
WHERE    tblPropAuthor.propAuthor = 'David'  
```  
  
### <a name="example-solution-using-the-clr-streaming-table-valued-function"></a><span data-ttu-id="5dec3-153">示例：使用 CLR 流式处理表值函数的解决方案</span><span class="sxs-lookup"><span data-stu-id="5dec3-153">Example: Solution Using the CLR Streaming Table-valued Function</span></span>  
 <span data-ttu-id="5dec3-154">此解决方案包括下列步骤：</span><span class="sxs-lookup"><span data-stu-id="5dec3-154">This solution is made up of the following steps:</span></span>  
  
1.  <span data-ttu-id="5dec3-155">定义 CLR 类 SqlReaderBase，它实现 ISqlReader，并通过在 XML 实例上应用路径表达式来生成流式表值输出。</span><span class="sxs-lookup"><span data-stu-id="5dec3-155">Define a CLR class, SqlReaderBase, that implements ISqlReader and generates a streaming, table-valued output by applying a path expression on an XML instance.</span></span>  
  
2.  <span data-ttu-id="5dec3-156">创建程序集和 Transact-SQL 用户定义函数来启动该 CLR 类。</span><span class="sxs-lookup"><span data-stu-id="5dec3-156">Create an assembly and a Transact-SQL user-defined function to start the CLR class.</span></span>  
  
3.  <span data-ttu-id="5dec3-157">通过使用用户定义函数来定义插入、更新和删除触发器，以维护属性表。</span><span class="sxs-lookup"><span data-stu-id="5dec3-157">Define the insert, update, and delete triggers by using the user-defined function to maintain a property tables.</span></span>  
  
 <span data-ttu-id="5dec3-158">若要如此，首先创建流式 CLR 函数。</span><span class="sxs-lookup"><span data-stu-id="5dec3-158">To do this, you first create the streaming CLR function.</span></span> <span data-ttu-id="5dec3-159">`xml`数据类型在 ADO.NET 中作为托管类 SqlXml 公开，并且支持返回 XmlReader 的**CreateReader ( # B1**方法。</span><span class="sxs-lookup"><span data-stu-id="5dec3-159">The `xml` data type is exposed as a managed class SqlXml in ADO.NET and supports the **CreateReader()** method that returns an XmlReader.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5dec3-160">本部分中的示例代码使用了 XPathDocument 和 XPathNavigator。</span><span class="sxs-lookup"><span data-stu-id="5dec3-160">The example code in this section uses XPathDocument and XPathNavigator.</span></span> <span data-ttu-id="5dec3-161">这些都强制要求您将所有 XML 文档加载到内存中。</span><span class="sxs-lookup"><span data-stu-id="5dec3-161">These force you to load all the XML documents into memory.</span></span> <span data-ttu-id="5dec3-162">如果您要在您的应用程序中使用类似代码来处理多个大型 XML 文档，此代码并不可伸缩。</span><span class="sxs-lookup"><span data-stu-id="5dec3-162">If you are using similar code in your application to process several large XML documents, this code is not scalable.</span></span> <span data-ttu-id="5dec3-163">而是应尽可能保持较小的内存分配并使用流式接口。</span><span class="sxs-lookup"><span data-stu-id="5dec3-163">Instead, keep memory allocations small and use streaming interfaces whenever possible.</span></span> <span data-ttu-id="5dec3-164">有关性能的详细信息，请参阅 [CLR 集成体系结构](../../database-engine/dev-guide/architecture-of-clr-integration.md)。</span><span class="sxs-lookup"><span data-stu-id="5dec3-164">For more information about performance, see [Architecture of CLR Integration](../../database-engine/dev-guide/architecture-of-clr-integration.md).</span></span>  
  
```  
public class c_streaming_xml_tvf {  
   public static ISqlReader streaming_xml_tvf   
(SqlXml xmlDoc, string pathExpression) {  
      return (new TestSqlReaderBase (xmlDoc, pathExpression));  
   }  
}  
  
// Class that implements ISqlReader  
public class TestSqlReaderBase : ISqlReader {  
XPathNodeIterator m_iterator;           
   public SqlChars FirstName;  
// Metadata for current resultset  
private SqlMetaData[] m_rgSqlMetaData;        
  
   public TestSqlReaderBase (SqlXml xmlDoc, string pathExpression) {     
      // Variables for XPath navigation  
      XPathDocument xDoc;  
      XPathNavigator xNav;  
      XPathExpression xPath;  
  
      // Set sql metadata  
      m_rgSqlMetaData = new SqlMetaData[1];  
      m_rgSqlMetaData[0] = new SqlMetaData ("FirstName",    
SqlDbType.NVarChar,50);     
  
      //Set up the Navigator  
      if (!xmlDoc.IsNull)  
          xDoc = new XPathDocument (xmlDoc.CreateReader());  
      else  
          xDoc = new XPathDocument ();  
      xNav = xDoc.CreateNavigator();  
      xPath = xNav.Compile (pathExpression);  
      m_iterator = xNav.Select(xPath);  
   }  
   public bool Read() {  
      bool moreRows = true;  
      if (moreRows = m_iterator.MoveNext())  
         FirstName = new SqlChars (m_iterator.Current.Value);  
      return moreRows;  
   }  
}  
```  
  
 <span data-ttu-id="5dec3-165">然后，创建一个程序集以及一个对应于 CLR 函数 streaming_xml_tvf 的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 用户定义函数 SQL_streaming_xml_tvf（未显示）。</span><span class="sxs-lookup"><span data-stu-id="5dec3-165">Next, create an assembly and a [!INCLUDE[tsql](../../includes/tsql-md.md)] user-defined function, SQL_streaming_xml_tvf (not shown), that corresponds to the CLR function, streaming_xml_tvf.</span></span> <span data-ttu-id="5dec3-166">该用户定义函数用于定义表值函数 CLR_udf_XML2Table 以便生成行集：</span><span class="sxs-lookup"><span data-stu-id="5dec3-166">The user-defined function is used to define the table-valued function, CLR_udf_XML2Table, for rowset generation:</span></span>  
  
```  
create function CLR_udf_XML2Table (@pk int, @xCol xml)  
returns @ret_Table table (FK int, FirstName varchar(max))  
with schemabinding  
as  
begin  
      insert into @ret_Table   
   select @pk, FirstName   
   FROM   SQL_streaming_xml_tvf (@xCol, '/book/author/first-name')  
      return  
end  
```  
  
 <span data-ttu-id="5dec3-167">最后，定义触发器，如“创建触发器以填充属性表”示例中所示，但用 CLR_udf_XML2Table 函数替换了 udf_XML2Table。</span><span class="sxs-lookup"><span data-stu-id="5dec3-167">Finally, define triggers as shown in the example, "Create triggers to populate a property table", but replace udf_XML2Table with the CLR_udf_XML2Table function.</span></span> <span data-ttu-id="5dec3-168">下面的示例中显示了插入触发器：</span><span class="sxs-lookup"><span data-stu-id="5dec3-168">The insert trigger is shown in the following example:</span></span>  
  
```  
create trigger CLR_trg_docs_INS on T for insert  
as  
   declare @wantedXML xml  
   declare @FK int  
   select @wantedXML = xCol from inserted  
   select @FK = PK from inserted  
  
   insert into tblPropAuthor  
      select *  
   from    dbo.CLR_udf_XML2Table(@FK, @wantedXML)  
```  
  
 <span data-ttu-id="5dec3-169">删除触发器与非 CLR 版本相同。</span><span class="sxs-lookup"><span data-stu-id="5dec3-169">The delete trigger is identical to the non-CLR version.</span></span> <span data-ttu-id="5dec3-170">但是，更新触发器只是用 CLR_udf_XML2Table() 函数替换了函数 udf_XML2Table()。</span><span class="sxs-lookup"><span data-stu-id="5dec3-170">However, the update trigger just replaces the function udf_XML2Table() with CLR_udf_XML2Table().</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dec3-171">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5dec3-171">See Also</span></span>  
 [<span data-ttu-id="5dec3-172">在计算列中使用 XML</span><span class="sxs-lookup"><span data-stu-id="5dec3-172">Use XML in Computed Columns</span></span>](use-xml-in-computed-columns.md)  
  
  
