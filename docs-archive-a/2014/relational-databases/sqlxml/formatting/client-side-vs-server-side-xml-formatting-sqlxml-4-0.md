---
title: 客户端与服务器端 XML 格式 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- NESTED mode
- FOR XML clause, formatting
- client-side XML formatting
- server-side XPath
- server-side XML formatting
- AUTO mode
- client-side XPath
ms.assetid: f807ab7a-c5f8-4e61-9b00-23aebfabc47e
author: rothja
ms.author: jroth
ms.openlocfilehash: fa155fc6d346cb90de54e5599aca1c296623faa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588410"
---
# <a name="client-side-vs-server-side-xml-formatting-sqlxml-40"></a><span data-ttu-id="1090b-102">客户端与服务器端 XML 格式 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="1090b-102">Client-side vs. Server-side XML Formatting (SQLXML 4.0)</span></span>
  <span data-ttu-id="1090b-103">本主题说明在 SQLXML 中客户端与服务器端 XML 格式的一般差异。</span><span class="sxs-lookup"><span data-stu-id="1090b-103">This topic describes the general differences between client-side and server-side XML formatting in SQLXML.</span></span>  
  
## <a name="multiple-rowset-queries-not-supported-in-client-side-formatting"></a><span data-ttu-id="1090b-104">客户端格式中不支持多行集查询</span><span class="sxs-lookup"><span data-stu-id="1090b-104">Multiple Rowset Queries Not Supported in Client-side Formatting</span></span>  
 <span data-ttu-id="1090b-105">使用客户端 XML 格式时不支持生成多个行集的查询。</span><span class="sxs-lookup"><span data-stu-id="1090b-105">Queries that generate multiple rowsets are not supported when you use client-side XML formatting.</span></span> <span data-ttu-id="1090b-106">例如，假定您有一个虚拟目录，在其中指定了客户端格式。</span><span class="sxs-lookup"><span data-stu-id="1090b-106">For example, assume you have a virtual directory in which you have client-side formatting specified.</span></span> <span data-ttu-id="1090b-107">请考虑此示例模板，该模板在块中包含两个 SELECT 语句 **\<sql:query>** ：</span><span class="sxs-lookup"><span data-stu-id="1090b-107">Consider this sample template, which has two SELECT statements in a **\<sql:query>** block:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>  
     SELECT FirstName FROM Person.Contact FOR XML Nested;   
     SELECT LastName FROM Person.Contact FOR XML Nested    
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="1090b-108">您可以在应用程序代码中执行此模板，但会返回错误，因为客户端 XML 格式不支持多个行集的格式。</span><span class="sxs-lookup"><span data-stu-id="1090b-108">You can execute this template in application code and an error is returned, because client-side XML formatting does not support formatting of multiple rowsets.</span></span> <span data-ttu-id="1090b-109">如果在两个单独的块中指定查询 **\<sql:query>** ，则会获得所需的结果。</span><span class="sxs-lookup"><span data-stu-id="1090b-109">If you specify the queries in two separate **\<sql:query>** blocks, you will get the desired results.</span></span>  
  
## <a name="timestamp-maps-differently-in-client--vs-server-side-formatting"></a><span data-ttu-id="1090b-110">timestamp 在客户端与服务器端格式中的映射方式不同</span><span class="sxs-lookup"><span data-stu-id="1090b-110">timestamp Maps Differently in Client- vs. Server-side Formatting</span></span>  
 <span data-ttu-id="1090b-111">在服务器端 XML 格式中，`timestamp` 类型的数据库列映射为 i8 XDR 类型（如果在查询中指定了 XMLDATA 选项）。</span><span class="sxs-lookup"><span data-stu-id="1090b-111">In server-side XML formatting, the database column of `timestamp` type maps to the i8 XDR type (when the XMLDATA option is specified in the query).</span></span>  
  
 <span data-ttu-id="1090b-112">在客户端 XML 格式中，`timestamp` 类型的数据库列映射为 `uri` 或 `bin.base64` XDR 类型（取决于是否在查询中指定了二进制 base64 选项）。</span><span class="sxs-lookup"><span data-stu-id="1090b-112">In client-side XML formatting, the database column of `timestamp` type maps to either the `uri` or the `bin.base64` XDR type (depending on whether the binary base64 option is specified in the query).</span></span> <span data-ttu-id="1090b-113">`bin.base64`如果使用 updategram 和 bulkload 功能，XDR 类型会很有用，因为此类型被转换为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `timestamp` 类型。</span><span class="sxs-lookup"><span data-stu-id="1090b-113">The `bin.base64` XDR type is useful if you use the updategram and bulkload features, because this type is converted to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `timestamp` type.</span></span> <span data-ttu-id="1090b-114">这样即可成功执行插入、更新或删除操作。</span><span class="sxs-lookup"><span data-stu-id="1090b-114">This way, the insert, update, or delete operation succeeds.</span></span>  
  
## <a name="deep-variants-are-used-in-server-side-formatting"></a><span data-ttu-id="1090b-115">服务器端 XML 格式使用深层 VARIANT</span><span class="sxs-lookup"><span data-stu-id="1090b-115">Deep VARIANTs Are Used in Server-side Formatting</span></span>  
 <span data-ttu-id="1090b-116">在服务器端 XML 格式中，使用深层类型的 VARIANT 类型。</span><span class="sxs-lookup"><span data-stu-id="1090b-116">In server-side XML formatting, the deep types of a VARIANT type are used.</span></span> <span data-ttu-id="1090b-117">如果使用客户端 XML 格式，变量将转换为 Unicode 字符串，并且不使用 VARIANT 的子类型。</span><span class="sxs-lookup"><span data-stu-id="1090b-117">If you use client-side XML formatting, the variants are converted to Unicode string, and the subtypes of VARIANT are not used.</span></span>  
  
## <a name="nested-mode-vs-auto-mode"></a><span data-ttu-id="1090b-118">NESTED 模式与 AUTO 模式</span><span class="sxs-lookup"><span data-stu-id="1090b-118">NESTED Mode vs. AUTO Mode</span></span>  
 <span data-ttu-id="1090b-119">客户端 FOR XML 的 NESTED 模式类似于服务器端 FOR XML 的 AUTO 模式，不过以下方面除外：</span><span class="sxs-lookup"><span data-stu-id="1090b-119">The NESTED mode of the client-side FOR XML is similar to the AUTO mode of server-side FOR XML, with the following exceptions:</span></span>  
  
### <a name="when-you-query-views-using-auto-mode-on-the-server-side-the-view-name-is-returned-as-the-element-name-in-the-resulting-xml"></a><span data-ttu-id="1090b-120">使用服务器端的 AUTO 模式查询视图时，在生成的 XML 中将视图名称返回为元素名称。</span><span class="sxs-lookup"><span data-stu-id="1090b-120">When you query views using AUTO mode on the server-side, the view name is returned as the element name in the resulting XML.</span></span>  
 <span data-ttu-id="1090b-121">例如，假定在 AdventureWorksdatabase 中的 Person 表上创建了以下视图：</span><span class="sxs-lookup"><span data-stu-id="1090b-121">For example, assume that the following view is created on the Person.Contact table in the AdventureWorksdatabase:</span></span>  
  
```  
CREATE VIEW ContactView AS (SELECT ContactID as CID,  
                               FirstName  as FName,  
                               LastName  as LName  
                        FROM Person.Contact)  
```  
  
 <span data-ttu-id="1090b-122">以下模板指定针对 ContactView 视图的查询，同时指定了服务器端 XML 格式：</span><span class="sxs-lookup"><span data-stu-id="1090b-122">The following template specifies a query against the ContactView view, and also specifies server-side XML formatting:</span></span>  
  
```  
 <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="0">  
    SELECT *  
    FROM   ContactView  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="1090b-123">执行该模板时，将返回以下 XML。</span><span class="sxs-lookup"><span data-stu-id="1090b-123">When you execute the template, the following XML is returned.</span></span> <span data-ttu-id="1090b-124"> (仅显示部分结果。 ) 请注意，元素名称是执行查询所依据的视图的名称。</span><span class="sxs-lookup"><span data-stu-id="1090b-124">(Only partial results are shown.) Note that the element names are the names of the views against which the query is executed.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <ContactView CID="1" FName="Gustavo" LName="Achong" />   
  <ContactView CID="2" FName="Catherine" LName="Abel" />   
...  
</ROOT>  
```  
  
 <span data-ttu-id="1090b-125">使用对应的 NESTED 模式指定客户端 XML 格式时，在生成的 XML 中将基表名称返回为元素名称。</span><span class="sxs-lookup"><span data-stu-id="1090b-125">When you specify client-side XML formatting by using the corresponding NESTED mode, the base table name(s) are returned as the element name(s) in the resulting XML.</span></span> <span data-ttu-id="1090b-126">例如，以下修改后的模板执行相同的 SELECT 语句，但 XML 格式是在客户端 (上执行的，在模板) 中，**客户端-xml**设置为 true：</span><span class="sxs-lookup"><span data-stu-id="1090b-126">For example, the following revised template executes the same SELECT statement, but the XML formatting is performed on the client-side (that is, **client-side-xml** is set to true in the template):</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    SELECT *  
    FROM   ContactView  
    FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="1090b-127">执行此模板将生成以下 XML。</span><span class="sxs-lookup"><span data-stu-id="1090b-127">Executing this template produces the following XML.</span></span> <span data-ttu-id="1090b-128">请注意，在此情况下的元素名称就是基表名称。</span><span class="sxs-lookup"><span data-stu-id="1090b-128">Note that the element name is the base table name in this case.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact CID="1" FName="Gustavo" LName="Achong" />   
  <Person.Contact CID="2" FName="Catherine" LName="Abel" />   
...  
</ROOT>  
```  
  
### <a name="when-you-use-auto-mode-of-the-server-side-for-xml-the-table-aliases-specified-in-the-query-are-returned-as-element-names-in-the-resulting-xml"></a><span data-ttu-id="1090b-129">使用服务器端 FOR XML 的 AUTO 模式时，在生成的 XML 中将查询中指定的表别名返回为元素名称。</span><span class="sxs-lookup"><span data-stu-id="1090b-129">When you use AUTO mode of the server-side FOR XML, the table aliases specified in the query are returned as element names in the resulting XML.</span></span>  
 <span data-ttu-id="1090b-130">例如，考虑以下模板：</span><span class="sxs-lookup"><span data-stu-id="1090b-130">For example, consider this template:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="0">  
    SELECT FirstName as fname,  
           LastName as lname  
    FROM   Person.Contact C  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="1090b-131">执行此模板将生成以下 XML：</span><span class="sxs-lookup"><span data-stu-id="1090b-131">Executing the template produces the following XML:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <C fname="Gustavo" lname="Achong" />   
  <C fname="Catherine" lname="Abel" />   
...  
</ROOT>   
```  
  
 <span data-ttu-id="1090b-132">使用客户端 FOR XML 的 NESTED 模式时，在生成的 XML 中将表名返回为元素名称。</span><span class="sxs-lookup"><span data-stu-id="1090b-132">When you use the NESTED mode of the client-side FOR XML, the table names are returned as element names in the resulting XML.</span></span> <span data-ttu-id="1090b-133">不使用查询中指定 (表别名。 ) 例如，请考虑以下模板：</span><span class="sxs-lookup"><span data-stu-id="1090b-133">(Table aliases that are specified in the query are not used.) For example, consider this template:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    SELECT FirstName as fname,  
           LastName as lname  
    FROM   Person.Contact C  
    FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="1090b-134">执行此模板将生成以下 XML：</span><span class="sxs-lookup"><span data-stu-id="1090b-134">Executing the template produces the following XML:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact fname="Gustavo" lname="Achong" />   
  <Person.Contact fname="Catherine" lname="Abel" />   
...  
</ROOT>  
```  
  
### <a name="if-you-have-a-query-that-returns-columns-as-dbobject-queries-you-cannot-use-aliases-for-these-columns"></a><span data-ttu-id="1090b-135">如果您的查询将列返回为 dbobject 查询，则无法对这些列使用别名。</span><span class="sxs-lookup"><span data-stu-id="1090b-135">If you have a query that returns columns as dbobject queries, you cannot use aliases for these columns.</span></span>  
 <span data-ttu-id="1090b-136">例如，考虑下面的模板，该模板执行的查询返回员工 ID 和照片。</span><span class="sxs-lookup"><span data-stu-id="1090b-136">For example, consider the following template, which executes a query that returns an employee ID and a photo.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<sql:query client-side-xml="1">  
   SELECT ProductPhotoID, LargePhoto as P  
   FROM   Production.ProductPhoto  
   WHERE  ProductPhotoID=5  
   FOR XML NESTED, elements  
</sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="1090b-137">执行此模板将返回作为 dbobject 查询的 Photo 列。</span><span class="sxs-lookup"><span data-stu-id="1090b-137">Executing this template returns the Photo column as a dbobject query.</span></span> <span data-ttu-id="1090b-138">在这个 dbobject 查询中，`@P` 指不存在的列名。</span><span class="sxs-lookup"><span data-stu-id="1090b-138">In this dbobject query, `@P` refers to a column name that does not exist.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Production.ProductPhoto>  
    <ProductPhotoID>5</ProductPhotoID>  
    <LargePhoto>dbobject/Production.ProductPhoto[@ProductPhotoID='5']/@P</LargePhoto>  
  </Production.ProductPhoto>  
</ROOT>  
```  
  
 <span data-ttu-id="1090b-139">如果在服务器 (的**客户端-xml = "0"**) 上执行 XML 格式设置，则可以使用返回 dbobject 查询的列的别名，这些查询将返回实际的表和列名称 (即使已指定了别名) 也是如此。</span><span class="sxs-lookup"><span data-stu-id="1090b-139">If the XML formatting is done on the server (**client-side-xml="0"**), you can use the alias for the columns that return dbobject queries in which actual table and column names are returned (even if you have aliases specified).</span></span> <span data-ttu-id="1090b-140">例如，下面的模板执行一个查询，并在服务器上执行 XML 格式设置， (未指定**客户端-XML**选项，并且没有为虚拟根) 选择 "**在客户端上运行**" 选项。</span><span class="sxs-lookup"><span data-stu-id="1090b-140">For example, the following template executes a query, and the XML formatting is done on the server (the **client-side-xml** option is not specified and the **Run On Client** option is not selected for the virtual root).</span></span> <span data-ttu-id="1090b-141">该查询还指定了 AUTO 模式（而不是客户端 NESTED 模式）。</span><span class="sxs-lookup"><span data-stu-id="1090b-141">The query also specifies AUTO mode (not the client-side NESTED mode).</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<sql:query   
   SELECT ProductPhotoID, LargePhoto as P  
   FROM   Production.ProductPhoto  
   WHERE  ProductPhotoID=5  
   FOR XML AUTO, elements  
</sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="1090b-142">执行此模板时，将返回以下 XML 文档（请注意，没有在针对 LargePhoto 列的 dbobject 查询中使用别名）：</span><span class="sxs-lookup"><span data-stu-id="1090b-142">When this template is executed, the following XML document is returned (note that aliases are not used in the dbobject query for the LargePhoto column):</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Production.ProductPhoto>  
    <ProductPhotoID>5</ProductPhotoID>  
    <LargePhoto>dbobject/Production.ProductPhoto[@ProductPhotoID='5']/@LargePhoto</LargePhoto>  
  </Production.ProductPhoto>  
</ROOT>  
```  
  
### <a name="client-side-vs-server-side-xpath"></a><span data-ttu-id="1090b-143">客户端与服务器端 XPath</span><span class="sxs-lookup"><span data-stu-id="1090b-143">Client-side vs. Server-side XPath</span></span>  
 <span data-ttu-id="1090b-144">客户端 XPath 与服务器端 XPath 的工作方式相同，以下几点除外：</span><span class="sxs-lookup"><span data-stu-id="1090b-144">Client-side XPath and server-side XPath work the same except for these differences:</span></span>  
  
-   <span data-ttu-id="1090b-145">使用客户端 XPath 查询时所应用的数据转换与使用服务器端 XPath 查询时所应用的数据转换有所不同。</span><span class="sxs-lookup"><span data-stu-id="1090b-145">The data conversions that are applied when you use client-side XPath queries are different from those that are applied when you use server-side XPath queries.</span></span> <span data-ttu-id="1090b-146">客户端 XPath 使用 CAST 而不是 CONVERT 模式 126。</span><span class="sxs-lookup"><span data-stu-id="1090b-146">Client-side XPath uses CAST instead of CONVERT mode 126.</span></span>  
  
-   <span data-ttu-id="1090b-147">如果在模板中指定**客户端-xml = "0"** (false) ，则会请求服务器端 xml 格式。</span><span class="sxs-lookup"><span data-stu-id="1090b-147">When you specify **client-side-xml="0"** (false) in a template, you are requesting server-side XML formatting.</span></span> <span data-ttu-id="1090b-148">因此，不能指定 FOR XML NESTED，因为服务器不识别 NESTED 选项。</span><span class="sxs-lookup"><span data-stu-id="1090b-148">Therefore, you cannot specify FOR XML NESTED because the server does not recognize the NESTED option.</span></span> <span data-ttu-id="1090b-149">这将生成一个错误。</span><span class="sxs-lookup"><span data-stu-id="1090b-149">This generates an error.</span></span> <span data-ttu-id="1090b-150">必须使用服务器确实可以识别的 AUTO、RAW 或 EXPLICIT 模式。</span><span class="sxs-lookup"><span data-stu-id="1090b-150">You must use the AUTO, RAW, or EXPLICIT modes, which the server does recognize.</span></span>  
  
-   <span data-ttu-id="1090b-151">如果在模板中指定**客户端-xml = "1"** (true) ，则会请求客户端 xml 格式。</span><span class="sxs-lookup"><span data-stu-id="1090b-151">When you specify **client-side-xml="1"** (true) in a template, you are requesting client-side XML formatting.</span></span> <span data-ttu-id="1090b-152">在这种情况下，可以指定 FOR XML NESTED。</span><span class="sxs-lookup"><span data-stu-id="1090b-152">In this case, you can specify FOR XML NESTED.</span></span> <span data-ttu-id="1090b-153">如果指定 FOR XML AUTO，则 XML 格式将在服务器端进行，但在模板中指定了**客户端-XML = "1"** 。</span><span class="sxs-lookup"><span data-stu-id="1090b-153">If you specify FOR XML AUTO, the XML formatting occurs on the server side although **client-side-xml="1"** is specified in the template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1090b-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1090b-154">See Also</span></span>  
 <span data-ttu-id="1090b-155">[有关 &#40;SQLXML 4.0 的 XML 安全注意事项&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/for-xml-security-considerations-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="1090b-155">[FOR XML Security Considerations &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/for-xml-security-considerations-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="1090b-156">[&#40;SQLXML 4.0&#41;的客户端 XML 格式](client-side-xml-formatting-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="1090b-156">[Client-side XML Formatting &#40;SQLXML 4.0&#41;](client-side-xml-formatting-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="1090b-157">服务器端 XML 格式 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="1090b-157">Server-side XML Formatting &#40;SQLXML 4.0&#41;</span></span>](server-side-xml-formatting-sqlxml-4-0.md)  
  
  
