---
title: 创建 XML 数据的实例 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- type casting string instances [XML in SQL Server]
- XML [SQL Server], typed
- xml data type [SQL Server], generating instances
- casting string instances [XML in SQL Server]
- typed XML
- generating XML instances [SQL Server]
- XML [SQL Server], generating instances
- white space [XML in SQL Server]
ms.assetid: dbd6c06f-db6e-44a7-855a-6a55bf374907
author: rothja
ms.author: jroth
ms.openlocfilehash: c857b9ebbe559de34fdac925642f9270d9cbf936
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694395"
---
# <a name="create-instances-of-xml-data"></a><span data-ttu-id="5ac22-102">创建 XML 数据的实例</span><span class="sxs-lookup"><span data-stu-id="5ac22-102">Create Instances of XML Data</span></span>
  <span data-ttu-id="5ac22-103">本主题说明了如何生成 XML 实例。</span><span class="sxs-lookup"><span data-stu-id="5ac22-103">This topic describes how to generate XML instances.</span></span>  
  
 <span data-ttu-id="5ac22-104">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，可以按照下列方式生成 XML 实例：</span><span class="sxs-lookup"><span data-stu-id="5ac22-104">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can generate XML instances in the following ways:</span></span>  
  
-   <span data-ttu-id="5ac22-105">对字符串实例进行类型转换。</span><span class="sxs-lookup"><span data-stu-id="5ac22-105">Type casting string instances.</span></span>  
  
-   <span data-ttu-id="5ac22-106">将 SELECT 语句与 FOR XML 子句结合使用。</span><span class="sxs-lookup"><span data-stu-id="5ac22-106">Using the SELECT statement with the FOR XML clause.</span></span>  
  
-   <span data-ttu-id="5ac22-107">使用常量赋值。</span><span class="sxs-lookup"><span data-stu-id="5ac22-107">Using constant assignments.</span></span>  
  
-   <span data-ttu-id="5ac22-108">使用大容量加载。</span><span class="sxs-lookup"><span data-stu-id="5ac22-108">Using bulk load.</span></span>  
  
## <a name="type-casting-string-and-binary-instances"></a><span data-ttu-id="5ac22-109">类型转换字符串实例和二进制实例</span><span class="sxs-lookup"><span data-stu-id="5ac22-109">Type Casting String and Binary Instances</span></span>  
 <span data-ttu-id="5ac22-110">可以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 通过将字符串数据类型（如 [**n**] [**var**]**char**、 **[n] text**、 **varbinary**和**image**）转换为数据类型，将其转换为 `xml` 数据类型 (强制转换) 或转换 (将字符串) 转换为 `xml` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="5ac22-110">You can parse any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] string data types, such as [**n**][**var**]**char**, **[n]text**, **varbinary**,and **image**, into the `xml` data type by casting (CAST) or converting (CONVERT) the string to the `xml` data type.</span></span> <span data-ttu-id="5ac22-111">对非类型化的 XML 进行检查以确认其格式是否正确。</span><span class="sxs-lookup"><span data-stu-id="5ac22-111">Untyped XML is checked to confirm that it is well formed.</span></span> <span data-ttu-id="5ac22-112">如果存在与类型关联的架构 `xml` ，则还会执行验证。</span><span class="sxs-lookup"><span data-stu-id="5ac22-112">If there is a schema associated with the `xml` type, validation is also performed.</span></span> <span data-ttu-id="5ac22-113">有关详细信息，请参阅 [类型化的 XML 与非类型化的 XML 的比较](compare-typed-xml-to-untyped-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="5ac22-113">For more information, see [Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md).</span></span>  
  
 <span data-ttu-id="5ac22-114">XML 文档可以采用不同的编码方式（例如，UTF-8、UTF-16 和 windows-1252）进行编码。</span><span class="sxs-lookup"><span data-stu-id="5ac22-114">XML documents can be encoded with different encodings (for example, UTF-8, UTF-16, windows-1252).</span></span> <span data-ttu-id="5ac22-115">下面概述了有关字符串和二进制源类型与 XML 文档编码进行交互的方式以及分析器行为方式的规则。</span><span class="sxs-lookup"><span data-stu-id="5ac22-115">The following outlines the rules on how the string and binary source types interact with the XML document encoding and how the parser behaves.</span></span>  
  
 <span data-ttu-id="5ac22-116">由于 **nvarchar** 采用为双字节 Unicode 编码（例如 UTF-16 或 UCS-2），因此 XML 分析器会将字符串值作为双字节 Unicode 编码 XML 文档或片断来处理。</span><span class="sxs-lookup"><span data-stu-id="5ac22-116">Since **nvarchar** assumes a two-byte unicode encoding such as UTF-16 or UCS-2, the XML parser will treat the string value as a two-byte Unicode encoded XML document or fragment.</span></span> <span data-ttu-id="5ac22-117">这意味着该 XML 文档需要以双字节 Unicode 编码方式进行编码，同时需要与源数据类型兼容。</span><span class="sxs-lookup"><span data-stu-id="5ac22-117">This means that the XML document needs to be encoded in a two-byte Unicode encoding as well to be compatible with the source data type.</span></span> <span data-ttu-id="5ac22-118">UTF-16 编码 XML 文档可以具有 UTF-16 字节顺序标记 (BOM)，但是它不需要，因为源类型的上下文显式指出 UTF-16 编码 XML 文档只能是双字节 Unicode 编码文档。</span><span class="sxs-lookup"><span data-stu-id="5ac22-118">A UTF-16 encoded XML document can have a UTF-16 byte order mark (BOM), but it does not need to, since the context of the source type makes it clear that it can only be a two-byte Unicode encoded document.</span></span>  
  
 <span data-ttu-id="5ac22-119">**varchar** 字符串的内容被 XML 分析器视为单字节编码 XML 文档/片断。</span><span class="sxs-lookup"><span data-stu-id="5ac22-119">The content of a **varchar** string is treated as a one-byte encoded XML document/fragment by the XML parser.</span></span> <span data-ttu-id="5ac22-120">由于 **varchar** 源字符串具有相关联的代码页，因此如果 XML 本身没有明确指定编码方式，分析器将使用该代码页。如果 XML 实例具有 BOM 或编码声明，则该 BOM 或声明应当与代码页一致，否则分析器将会报告一个错误。</span><span class="sxs-lookup"><span data-stu-id="5ac22-120">Since the **varchar** source string has a code page associated, the parser will use that code page for the encoding if no explicit encoding is specified in the XML itself If an XML instance has a BOM or an encoding declaration, the BOM or declaration needs to be consistent with the code page, otherwise the parser will report an error.</span></span>  
  
 <span data-ttu-id="5ac22-121">**varbinary** 的内容被视为码位流，它将直接被传递到 XML 分析器。</span><span class="sxs-lookup"><span data-stu-id="5ac22-121">The content of **varbinary** is treated as a codepoint stream that is passed directly to the XML parser.</span></span> <span data-ttu-id="5ac22-122">这样，XML 文档或片断就需要提供 BOM 或其他内联编码信息。</span><span class="sxs-lookup"><span data-stu-id="5ac22-122">Thus, the XML document or fragment needs to provide the BOM or other encoding information inline.</span></span> <span data-ttu-id="5ac22-123">分析器将仅查看该流来确定编码方式。</span><span class="sxs-lookup"><span data-stu-id="5ac22-123">The parser will only look at the stream to determine the encoding.</span></span> <span data-ttu-id="5ac22-124">这意味着 UTF-16 编码 XML 需要提供 UTF-16 BOM，不带 BOM 和编码声明的实例将被解释为 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="5ac22-124">This means that UTF-16 encoded XML needs to provide the UTF-16 BOM and an instance without BOM and without a declaration encoding will be interpreted as UTF-8.</span></span>  
  
 <span data-ttu-id="5ac22-125">如果事先不知道 XML 文档的编码方式，并且数据在转换到 XML 之前被作为字符串或二进制数据而不是 XML 数据来传递，则建议将数据作为 **varbinary**处理。</span><span class="sxs-lookup"><span data-stu-id="5ac22-125">If the encoding of the XML document is not known in advance and the data is passed as string or binary data instead of XML data before casting to XML, it is recommended to treat the data as **varbinary**.</span></span> <span data-ttu-id="5ac22-126">例如，当使用 OpenRowset() 从 XML 文件读取数据时，应该指定将数据作为 **varbinary(max)** 值读取：</span><span class="sxs-lookup"><span data-stu-id="5ac22-126">For example, when reading data from an XML file using OpenRowset(), one should specify the data to be read as a **varbinary(max)** value:</span></span>  
  
```  
select CAST(x as XML)   
from OpenRowset(BULK 'filename.xml', SINGLE_BLOB) R(x)  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5ac22-127">在内部以一种使用 UTF-16 编码的有效二进制表示形式来表示 XML。</span><span class="sxs-lookup"><span data-stu-id="5ac22-127">internally represents XML in an efficient binary representation that uses UTF-16 encoding.</span></span> <span data-ttu-id="5ac22-128">用户提供的编码不会保留下来，但在分析过程中会考虑。</span><span class="sxs-lookup"><span data-stu-id="5ac22-128">User-provided encoding is not preserved, but is considered during the parse process.</span></span>  
  
### <a name="type-casting-clr-user-defined-types"></a><span data-ttu-id="5ac22-129">类型转换 CLR 用户定义类型</span><span class="sxs-lookup"><span data-stu-id="5ac22-129">Type Casting CLR user-defined types</span></span>  
 <span data-ttu-id="5ac22-130">如果 CLR 用户定义类型具有 XML 序列化，则该类型的实例可以显式转换为 XML 数据类型。</span><span class="sxs-lookup"><span data-stu-id="5ac22-130">If a CLR user-defined type has an XML Serialization, instances of that type can be explicitly cast to an XML datatype.</span></span> <span data-ttu-id="5ac22-131">有关 CLR 用户定义类型的 XML 序列化的详细信息，请参 [从 CLR 数据库对象进行 XML 序列化](../../database-engine/dev-guide/xml-serialization-from-clr-database-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="5ac22-131">For more details about the XML serialization of a CLR user-defined typed, see [XML Serialization from CLR Database Objects](../../database-engine/dev-guide/xml-serialization-from-clr-database-objects.md).</span></span>  
  
### <a name="white-space-handling-in-typed-xml"></a><span data-ttu-id="5ac22-132">类型化的 XML 中的空格处理</span><span class="sxs-lookup"><span data-stu-id="5ac22-132">White Space Handling in Typed XML</span></span>  
 <span data-ttu-id="5ac22-133">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，如果元素内容中的空格出现在一组只有空格并由标记（如开始或结束标记）分隔的字符数据中，则认为其无关紧要，因此不对其进行实体化。</span><span class="sxs-lookup"><span data-stu-id="5ac22-133">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], white space inside element content is considered insignificant if it occurs inside a sequence of white-space-only character data delimited by markup, such as begin or end tags, and is not entitized.</span></span> <span data-ttu-id="5ac22-134">（忽略 CDATA 部分。）这种空格处理方式与万维网联盟 (W3C) 发布的 XML 1.0 规格中介绍的空格处理方式不同。</span><span class="sxs-lookup"><span data-stu-id="5ac22-134">(CDATA sections are ignored.) This handling of white space handling is different from how white space is described in the XML 1.0 specification published by the World Wide Web Consortium (W3C).</span></span> <span data-ttu-id="5ac22-135">这是因为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 XML 分析器只识别有限数量的 DTD 子集（在 XML 1.0 中定义）。</span><span class="sxs-lookup"><span data-stu-id="5ac22-135">This is because the XML parser in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recognizes only a limited number of DTD subsets, as defined in XML 1.0.</span></span> <span data-ttu-id="5ac22-136">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中支持的有限 DTD 子集的详细信息，请参阅 [CAST 和 CONVERT (Transact-SQL)](/sql/t-sql/functions/cast-and-convert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5ac22-136">For more information about the limited DTD subsets supported in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span>  
  
 <span data-ttu-id="5ac22-137">默认情况下，在 XML 分析器将字符串数据转换为 XML 时，如果存在下列任何一种情况，则 XML 分析器将丢弃无关紧要的空格：</span><span class="sxs-lookup"><span data-stu-id="5ac22-137">By default, the XML parser discards insignificant white space when it converts string data to XML if either of the following is true:</span></span>  
  
-   <span data-ttu-id="5ac22-138">`The xml:space` 属性。</span><span class="sxs-lookup"><span data-stu-id="5ac22-138">`The xml:space` attribute is not defined on an element or its ancestor elements.</span></span>  
  
-   <span data-ttu-id="5ac22-139">某元素或其某一祖先元素上有效的 `xml:space` 属性具有默认值。</span><span class="sxs-lookup"><span data-stu-id="5ac22-139">The `xml:space` attribute in effect on an element, or one of its ancestor elements, has the value of default.</span></span>  
  
 <span data-ttu-id="5ac22-140">例如：</span><span class="sxs-lookup"><span data-stu-id="5ac22-140">For example:</span></span>  
  
```  
declare @x xml  
set @x = '<root>      <child/>     </root>'  
select @x   
```  
  
 <span data-ttu-id="5ac22-141">结果如下：</span><span class="sxs-lookup"><span data-stu-id="5ac22-141">This is the result:</span></span>  
  
```  
<root><child/></root>  
```  
  
 <span data-ttu-id="5ac22-142">不过，您可以更改此行为。</span><span class="sxs-lookup"><span data-stu-id="5ac22-142">However, you can change this behavior.</span></span> <span data-ttu-id="5ac22-143">若要为 xml DT 实例保留空格，请使用 CONVERT 运算符，并将其可选的 *style* 参数的值设置为 1。</span><span class="sxs-lookup"><span data-stu-id="5ac22-143">To preserve white space for an xml DT instance, use the CONVERT operator and its optional *style* parameter set to a value of 1.</span></span> <span data-ttu-id="5ac22-144">例如：</span><span class="sxs-lookup"><span data-stu-id="5ac22-144">For example:</span></span>  
  
```  
SELECT CONVERT(xml, N'<root>      <child/>     </root>', 1)  
```  
  
 <span data-ttu-id="5ac22-145">如果未使用 *style* 参数，或将其值设置为 0，则转换 xml DT 实例时不保留无关紧要的空格。</span><span class="sxs-lookup"><span data-stu-id="5ac22-145">If the *style* parameter is either not used or its value is set to 0, insignificant white space is not preserved for the conversion of the xml DT instance.</span></span> <span data-ttu-id="5ac22-146">有关在将字符串数据转换为 xml DT 实例时如何使用 CONVERT 运算符及其 *style* 参数的详细信息，请参阅 [CAST 和 CONVERT (Transact-SQL)](/sql/t-sql/functions/cast-and-convert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5ac22-146">For more information about how to use the CONVERT operator and its *style* parameter when converting string data to xml DT instances, see [CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span>  
  
### <a name="example-cast-a-string-value-to-typed-xml-and-assign-it-to-a-column"></a><span data-ttu-id="5ac22-147">示例：将字符串值转换为类型化的 xml 并将它分配给某列</span><span class="sxs-lookup"><span data-stu-id="5ac22-147">Example: Cast a string value to typed xml and assign it to a column</span></span>  
 <span data-ttu-id="5ac22-148">下面的示例将包含 XML 片段的字符串变量转换为 `xml` 数据类型，然后将其存储在 `xml` 类型列中：</span><span class="sxs-lookup"><span data-stu-id="5ac22-148">The following example casts a string variable that contains an XML fragment to the `xml` data type and then stores it in the `xml` type column:</span></span>  
  
```  
CREATE TABLE T(c1 int primary key, c2 xml)  
go  
DECLARE  @s varchar(100)  
SET @s = '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>'   
```  
  
 <span data-ttu-id="5ac22-149">以下插入操作将字符串隐式转换为 `xml` 类型：</span><span class="sxs-lookup"><span data-stu-id="5ac22-149">The following insert operation implicitly converts from a string to the `xml` type:</span></span>  
  
```  
INSERT INTO T VALUES (3, @s)   
```  
  
 <span data-ttu-id="5ac22-150">可以显式将字符串 ( # A1 强制转换为 `xml` 类型：</span><span class="sxs-lookup"><span data-stu-id="5ac22-150">You can explicitly cast() the string to the `xml` type:</span></span>  
  
```  
INSERT INTO T VALUES (3, cast (@s as xml))  
```  
  
 <span data-ttu-id="5ac22-151">另外，也可以使用 convert()，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5ac22-151">Or you can use convert(), as shown in the following:</span></span>  
  
```  
INSERT INTO T VALUES (3, convert (xml, @s))   
```  
  
### <a name="example-convert-a-string-to-typed-xml-and-assign-it-to-a-variable"></a><span data-ttu-id="5ac22-152">示例：将字符串转换为类型化的 xml 并将其分配给某个变量</span><span class="sxs-lookup"><span data-stu-id="5ac22-152">Example: Convert a string to typed xml and assign it to a variable</span></span>  
 <span data-ttu-id="5ac22-153">在下面的示例中，将字符串转换为 `xml` 类型，并将其分配给 `xml` 数据类型的变量：</span><span class="sxs-lookup"><span data-stu-id="5ac22-153">In the following example, a string is converted to `xml` type and assigned to a variable of the `xml` data type:</span></span>  
  
```  
declare @x xml  
declare  @s varchar(100)  
SET @s = '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>'   
set @x =convert (xml, @s)  
select @x  
```  
  
## <a name="using-the-select-statement-with-a-for-xml-clause"></a><span data-ttu-id="5ac22-154">将 SELECT 语句与 FOR XML 子句结合使用</span><span class="sxs-lookup"><span data-stu-id="5ac22-154">Using the SELECT Statement with a FOR XML Clause</span></span>  
 <span data-ttu-id="5ac22-155">可以在 SELECT 语句中使用 FOR XML 子句以返回 XML 形式的结果。</span><span class="sxs-lookup"><span data-stu-id="5ac22-155">You can use the FOR XML clause in a SELECT statement to return results as XML.</span></span> <span data-ttu-id="5ac22-156">例如：</span><span class="sxs-lookup"><span data-stu-id="5ac22-156">For example:</span></span>  
  
```  
DECLARE @xmlDoc xml  
SET @xmlDoc = (SELECT Column1, Column2  
               FROM   Table1, Table2  
               WHERE   Some condition  
               FOR XML AUTO)  
 ...  
```  
  
 <span data-ttu-id="5ac22-157">SELECT 语句返回文本 XML 片段，该片段在赋值到数据类型变量的过程中进行分析 `xml` 。</span><span class="sxs-lookup"><span data-stu-id="5ac22-157">The SELECT statement returns a textual XML fragment that is then parsed during the assignment to the `xml` data type variable.</span></span>  
  
 <span data-ttu-id="5ac22-158">你还可以在 FOR XML 子句中使用[type 指令](type-directive-in-for-xml-queries.md)，该子句直接将 for xml 查询结果作为 `xml` 类型返回：</span><span class="sxs-lookup"><span data-stu-id="5ac22-158">You can also use the [TYPE directive](type-directive-in-for-xml-queries.md) in the FOR XML clause that directly returns a FOR XML query result as `xml` type:</span></span>  
  
```  
Declare @xmlDoc xml  
SET @xmlDoc = (SELECT ProductModelID, Name  
               FROM   Production.ProductModel  
               WHERE  ProductModelID=19  
               FOR XML AUTO, TYPE)  
SELECT @xmlDoc  
```  
  
 <span data-ttu-id="5ac22-159">结果如下：</span><span class="sxs-lookup"><span data-stu-id="5ac22-159">This is the result:</span></span>  
  
```  
<Production.ProductModel ProductModelID="19" Name="Mountain-100" />...  
```  
  
 <span data-ttu-id="5ac22-160">在下面的示例中，将 `xml` FOR XML 查询的类型化结果插入到 `xml` 类型列中：</span><span class="sxs-lookup"><span data-stu-id="5ac22-160">In the following example, the typed `xml` result of a FOR XML query is inserted into an `xml` type column:</span></span>  
  
```  
CREATE TABLE T1 (c1 int, c2 xml)  
go  
INSERT T1(c1, c2)  
SELECT 1, (SELECT ProductModelID, Name  
           FROM Production.ProductModel  
           WHERE ProductModelID=19  
           FOR XML AUTO, TYPE)  
SELECT * FROM T1  
go  
```  
  
 <span data-ttu-id="5ac22-161">有关 FOR XML 的详细信息，请参阅 [FOR XML (SQL Server)](for-xml-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="5ac22-161">For more information about FOR XML, see [FOR XML &#40;SQL Server&#41;](for-xml-sql-server.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5ac22-162">将 `xml` 数据类型实例作为不同服务器构造（例如使用 TYPE 指令或在其中使用 `xml` 数据类型从 SQL 列、变量和输出参数返回 XML 的 FOR XML 查询）的结果返回到客户端。</span><span class="sxs-lookup"><span data-stu-id="5ac22-162">returns `xml` data type instances to the client as a result of different server constructs such as FOR XML queries that use the TYPE directive, or where the `xml` data type is used to return XML from SQL columns, variables, and output parameters.</span></span> <span data-ttu-id="5ac22-163">在客户端应用程序代码中，ADO.NET 访问接口请求以二进制编码形式从服务器发送此 `xml` 数据类型信息。</span><span class="sxs-lookup"><span data-stu-id="5ac22-163">In client application code, the ADO.NET provider requests that this `xml` data type information be sent in a binary encoding from the server.</span></span> <span data-ttu-id="5ac22-164">但是，如果使用的是不带 TYPE 指令的 FOR XML，则 XML 数据将作为字符串类型返回。</span><span class="sxs-lookup"><span data-stu-id="5ac22-164">However, if you are using FOR XML without the TYPE directive, the XML data returns as a string type.</span></span> <span data-ttu-id="5ac22-165">在任何情况下，客户端访问接口都始终能够处理其中任一种形式的 XML 内容。</span><span class="sxs-lookup"><span data-stu-id="5ac22-165">In any case, the client provider will always be able to handle either form of XML.</span></span>  
  
## <a name="using-constant-assignments"></a><span data-ttu-id="5ac22-166">使用常量赋值</span><span class="sxs-lookup"><span data-stu-id="5ac22-166">Using Constant Assignments</span></span>  
 <span data-ttu-id="5ac22-167">如果需要数据类型的实例，可以使用字符串常量 `xml` 。</span><span class="sxs-lookup"><span data-stu-id="5ac22-167">A string constant can be used where an instance of the `xml` data type is expected.</span></span> <span data-ttu-id="5ac22-168">这与将字符串隐式 CAST 为 XML 相同。</span><span class="sxs-lookup"><span data-stu-id="5ac22-168">This is the same as an implied CAST of string to XML.</span></span> <span data-ttu-id="5ac22-169">例如：</span><span class="sxs-lookup"><span data-stu-id="5ac22-169">For example:</span></span>  
  
```  
DECLARE @xmlDoc xml  
SET @xmlDoc = '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>'   
-- Or  
SET @xmlDoc = N'<?xml version="1.0" encoding="ucs-2"?><doc/>'  
```  
  
 <span data-ttu-id="5ac22-170">前面的示例将字符串隐式转换为 `xml` 数据类型，并将其分配给 `xml` 类型变量。</span><span class="sxs-lookup"><span data-stu-id="5ac22-170">The previous example implicitly converts the string to the `xml` data type and assigns it to an `xml` type variable.</span></span>  
  
 <span data-ttu-id="5ac22-171">下面的示例将常量字符串插入到 `xml` 类型列中：</span><span class="sxs-lookup"><span data-stu-id="5ac22-171">The following example inserts a constant string into an `xml` type column:</span></span>  
  
```  
CREATE TABLE T(c1 int primary key, c2 xml)  
INSERT INTO T VALUES (3, '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>')   
```  
  
> [!NOTE]  
>  <span data-ttu-id="5ac22-172">对于类型化的 XML，是针对指定的架构来验证 XML。</span><span class="sxs-lookup"><span data-stu-id="5ac22-172">For typed XML, the XML is validated against the specified schema.</span></span> <span data-ttu-id="5ac22-173">有关详细信息，请参阅 [类型化的 XML 与非类型化的 XML 的比较](compare-typed-xml-to-untyped-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="5ac22-173">For more information, see [Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md).</span></span>  
  
## <a name="using-bulk-load"></a><span data-ttu-id="5ac22-174">使用大容量加载</span><span class="sxs-lookup"><span data-stu-id="5ac22-174">Using Bulk Load</span></span>  
 <span data-ttu-id="5ac22-175">通过增强的 [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) 功能，可以在数据库中大容量加载 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="5ac22-175">The enhanced [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) functionality allows you to bulk load XML documents in the database.</span></span> <span data-ttu-id="5ac22-176">可以将文件中的 XML 实例大容量加载到 `xml` 数据库中的类型列。</span><span class="sxs-lookup"><span data-stu-id="5ac22-176">You can bulk load XML instances from files into the `xml` type columns in the database.</span></span> <span data-ttu-id="5ac22-177">有关工作示例，请参阅[批量导入和导出 XML 文档的示例 (SQL Server);](../import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="5ac22-177">For working samples, see [Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;](../import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md).</span></span> <span data-ttu-id="5ac22-178">有关加载 XML 文档的详细信息，请参阅 [加载 XML 数据](load-xml-data.md)。</span><span class="sxs-lookup"><span data-stu-id="5ac22-178">For more information about loading XML documents, see [Load XML Data](load-xml-data.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ac22-179">本节内容</span><span class="sxs-lookup"><span data-stu-id="5ac22-179">In This Section</span></span>  
  
|<span data-ttu-id="5ac22-180">主题</span><span class="sxs-lookup"><span data-stu-id="5ac22-180">Topic</span></span>|<span data-ttu-id="5ac22-181">说明</span><span class="sxs-lookup"><span data-stu-id="5ac22-181">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5ac22-182">检索和查询 XML 数据</span><span class="sxs-lookup"><span data-stu-id="5ac22-182">Retrieve and Query XML Data</span></span>](retrieve-and-query-xml-data.md)|<span data-ttu-id="5ac22-183">介绍了当 XML 实例存储在数据库中时未保留的部分。</span><span class="sxs-lookup"><span data-stu-id="5ac22-183">Describes the parts of XML instances that are not preserved when they are stored in databases.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ac22-184">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5ac22-184">See Also</span></span>  
 <span data-ttu-id="5ac22-185">[类型化的 XML 与非类型化的 XML 的比较](compare-typed-xml-to-untyped-xml.md) </span><span class="sxs-lookup"><span data-stu-id="5ac22-185">[Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md) </span></span>  
 <span data-ttu-id="5ac22-186">[xml 数据类型方法](/sql/t-sql/xml/xml-data-type-methods) </span><span class="sxs-lookup"><span data-stu-id="5ac22-186">[xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods) </span></span>  
 <span data-ttu-id="5ac22-187">[XML 数据修改语言 (XML DML)](/sql/t-sql/xml/xml-data-modification-language-xml-dml) </span><span class="sxs-lookup"><span data-stu-id="5ac22-187">[XML Data Modification Language &#40;XML DML&#41;](/sql/t-sql/xml/xml-data-modification-language-xml-dml) </span></span>  
 [<span data-ttu-id="5ac22-188">XML 数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5ac22-188">XML Data &#40;SQL Server&#41;</span></span>](xml-data-sql-server.md)  
  
  
