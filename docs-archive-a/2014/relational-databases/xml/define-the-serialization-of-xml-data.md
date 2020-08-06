---
title: 定义 XML 数据的序列化 | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- entitization rules [XML in SQL Server]
- serialization
- reparsing serialized XML structures
- encoding [XML in SQL Server]
- XML [SQL Server], serialization
- xml data type [SQL Server], serialization
- typed XML
ms.assetid: 42b0b5a4-bdd6-4a60-b451-c87f14758d4b
author: rothja
ms.author: jroth
ms.openlocfilehash: df87dddd9fd4cf067125314c9d798eaa42523576
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591154"
---
# <a name="define-the-serialization-of-xml-data"></a><span data-ttu-id="2a054-102">定义 XML 数据的序列化</span><span class="sxs-lookup"><span data-stu-id="2a054-102">Define the Serialization of XML Data</span></span>
  <span data-ttu-id="2a054-103">将 xml 数据类型显式或隐式转换为 SQL 字符串或二进制类型时，将根据本主题中所述的规则对 xml 数据类型的内容进行序列化。</span><span class="sxs-lookup"><span data-stu-id="2a054-103">When casting the xml data type explicitly or implicitly to a SQL string or binary type, the content of the xml data type will be serialized according to the rules outlined in this topic.</span></span>  
  
## <a name="serialization-encoding"></a><span data-ttu-id="2a054-104">序列化编码</span><span class="sxs-lookup"><span data-stu-id="2a054-104">Serialization Encoding</span></span>  
 <span data-ttu-id="2a054-105">如果 SQL 目标类型是 VARBINARY，则将使用前面具有 UTF-16 字节顺序标记且没有 XML 声明的 UTF-16 对结果进行序列化。</span><span class="sxs-lookup"><span data-stu-id="2a054-105">If the SQL target type is VARBINARY, the result is serialized in UTF-16 with a UTF-16-byte order mark in front, but without an XML declaration.</span></span> <span data-ttu-id="2a054-106">如果目标类型太小，将会引发错误。</span><span class="sxs-lookup"><span data-stu-id="2a054-106">If the target type is too small, an error is raised.</span></span>  
  
 <span data-ttu-id="2a054-107">例如：</span><span class="sxs-lookup"><span data-stu-id="2a054-107">For example:</span></span>  
  
```sql
select CAST(CAST(N'<Δ/>' as XML) as VARBINARY(MAX))  
```  
  
 <span data-ttu-id="2a054-108">结果如下：</span><span class="sxs-lookup"><span data-stu-id="2a054-108">This is the result:</span></span>  
  
```  
0xFFFE3C0094032F003E00  
```  
  
 <span data-ttu-id="2a054-109">如果 SQL 目标类型是 NVARCHAR 或 NCHAR，则使用前面没有字节顺序标记且没有 XML 声明的 UTF-16 对结果进行序列化。</span><span class="sxs-lookup"><span data-stu-id="2a054-109">If the SQL target type is NVARCHAR or NCHAR, the result is serialized in UTF-16 without the byte order mark in front and without an XML declaration.</span></span> <span data-ttu-id="2a054-110">如果目标类型太小，将会引发错误。</span><span class="sxs-lookup"><span data-stu-id="2a054-110">If the target type is too small, an error is raised.</span></span>  
  
 <span data-ttu-id="2a054-111">例如：</span><span class="sxs-lookup"><span data-stu-id="2a054-111">For example:</span></span>  
  
```sql
select CAST(CAST(N'<Δ/>' as XML) as NVARCHAR(MAX))  
```  
  
 <span data-ttu-id="2a054-112">结果如下：</span><span class="sxs-lookup"><span data-stu-id="2a054-112">This is the result:</span></span>  
  
```  
<Δ/>  
```  
  
 <span data-ttu-id="2a054-113">如果 SQL 目标类型是 VARCHAR 或 NCHAR，则使用与数据库的排序规则代码页对应的编码（既没有字节顺序标记，也没有 XML 声明）对结果进行序列化。</span><span class="sxs-lookup"><span data-stu-id="2a054-113">If the SQL target type is VARCHAR or NCHAR, the result is serialized in the encoding that corresponds to the database's collation code page without a byte order mark or XML declaration.</span></span> <span data-ttu-id="2a054-114">如果目标类型太小或无法将值映射到目标排序规则代码页，将产生错误。</span><span class="sxs-lookup"><span data-stu-id="2a054-114">If the target type is too small or the value cannot be mapped to the target collation code page, an error is raised.</span></span>  
  
 <span data-ttu-id="2a054-115">例如：</span><span class="sxs-lookup"><span data-stu-id="2a054-115">For example:</span></span>  
  
```sql
select CAST(CAST(N'<Δ/>' as XML) as VARCHAR(MAX))  
```  
  
 <span data-ttu-id="2a054-116">如果当前排序规则的代码页不能表示 & # x10300; 的 Unicode 字符，这可能会导致错误，否则将用特定编码来表示该字符。</span><span class="sxs-lookup"><span data-stu-id="2a054-116">This may result in an error, if the current collation's code page cannot represent the Unicode character &#x10300;, or it will represent it in the specific encoding.</span></span>  
  
 <span data-ttu-id="2a054-117">将 XML 结果返回到客户端时，将用 UTF-16 编码发送数据。</span><span class="sxs-lookup"><span data-stu-id="2a054-117">When returning XML results to the client side, the data will be sent in UTF-16 encoding.</span></span> <span data-ttu-id="2a054-118">然后，客户端提供程序将根据 API 规则显示该数据。</span><span class="sxs-lookup"><span data-stu-id="2a054-118">The client-side provider will then expose the data according to its API rules.</span></span>  
  
## <a name="serialization-of-the-xml-structures"></a><span data-ttu-id="2a054-119">XML 结构的序列化</span><span class="sxs-lookup"><span data-stu-id="2a054-119">Serialization of the XML Structures</span></span>  
 <span data-ttu-id="2a054-120">用通常的方式对 **xml** 数据类型的内容进行序列化。</span><span class="sxs-lookup"><span data-stu-id="2a054-120">The content of an **xml** data type is serialized in the usual way.</span></span> <span data-ttu-id="2a054-121">确切地说，就是将元素节点映射到元素标记，将文本节点映射到文本内容。</span><span class="sxs-lookup"><span data-stu-id="2a054-121">Specifically, element nodes are mapped to element markup, and text nodes are mapped to text content.</span></span> <span data-ttu-id="2a054-122">不过，对字符进行实体化的环境以及对类型化的原子值进行序列化的方法将在下面两节中进行介绍。</span><span class="sxs-lookup"><span data-stu-id="2a054-122">However, the circumstances under which characters are entitized and how typed atomic values are serialized are described in the following sections.</span></span>  
  
## <a name="entitization-of-xml-characters-during-serialization"></a><span data-ttu-id="2a054-123">序列化期间 XML 字符的实体化</span><span class="sxs-lookup"><span data-stu-id="2a054-123">Entitization of XML Characters During Serialization</span></span>  
 <span data-ttu-id="2a054-124">应该能够对每个序列化的 XML 结构进行重新分析。</span><span class="sxs-lookup"><span data-stu-id="2a054-124">Every serialized XML structure should be capable of being reparsed.</span></span> <span data-ttu-id="2a054-125">因此，必须以实体化方式对某些字符进行序列化，从而在整个 XML 分析器的规范化阶段保留这些字符的往返能力。</span><span class="sxs-lookup"><span data-stu-id="2a054-125">Therefore, some characters have to be serialized in an entitized way to preserve the round-trip capability of the characters through the XML parser's normalization phase .</span></span> <span data-ttu-id="2a054-126">不过，还必须对某些字符进行实体化，以便文档的格式正确并能够被分析。</span><span class="sxs-lookup"><span data-stu-id="2a054-126">However, some characters have to be entitized so that the document is well-formed and, therefore, able to be parsed.</span></span> <span data-ttu-id="2a054-127">下面是序列化期间应用的实体化规则：</span><span class="sxs-lookup"><span data-stu-id="2a054-127">Following are the entitization rules that apply during serialization:</span></span>  
  
-   <span data-ttu-id="2a054-128">如果字符 &、\<, and > 出现在属性值或元素内容中，始终将它们分别实体化为 &amp;、&lt; 和 &gt;。</span><span class="sxs-lookup"><span data-stu-id="2a054-128">The characters &, \<, and > are always entitized to &amp;, &lt;, and &gt; respectively, if they occur inside an attribute value or element content.</span></span>  
  
-   <span data-ttu-id="2a054-129">因为 SQL Server 使用引号 (U+0022) 来闭合属性值，所以将属性值中的引号实体化为 &quot;。</span><span class="sxs-lookup"><span data-stu-id="2a054-129">Because SQL Server uses a quotation mark (U+0022) for enclosing attribute values, the quotation mark in attribute values is entitized as &quot;.</span></span>  
  
-   <span data-ttu-id="2a054-130">仅在服务器上进行转换时，将代理项对实体化为单个数字字符引用。</span><span class="sxs-lookup"><span data-stu-id="2a054-130">A surrogate pair is entitized as a single numeric character reference, when casting on the server only.</span></span> <span data-ttu-id="2a054-131">例如，将代理项对 U+D800 U+DF00 实体化为数字字符引用 &\#x00010300;。</span><span class="sxs-lookup"><span data-stu-id="2a054-131">For example the surrogate pair U+D800 U+DF00 is entitized to the numeric character reference &\#x00010300;.</span></span>  
  
-   <span data-ttu-id="2a054-132">为了防止 TAB (U+0009) 和换行符 (LF, U+000A) 在分析期间被规范化，在属性值内，将它们分别实体化为它们的数字字符引用 &\#x9; 和 &\#xA;。</span><span class="sxs-lookup"><span data-stu-id="2a054-132">To protect a TAB (U+0009) and a linefeed (LF, U+000A) from being normalized during parsing, they are entitized to their numeric character references &\#x9; and &\#xA; respectively, inside attribute values.</span></span>  
  
-   <span data-ttu-id="2a054-133">为了防止回车符 (CR, U+000D) 在分析期间被规范化，在属性值和元素内容中，将它实体化为它的数字字符引用 &\#xD;。</span><span class="sxs-lookup"><span data-stu-id="2a054-133">To prevent a carriage return (CR, U+000D) from being normalized during parsing, it is entitized to its numeric character reference, &\#xD; inside both attribute values and element content.</span></span>  
  
-   <span data-ttu-id="2a054-134">为了保护仅包含空格的文本节点，将其中一个空格字符（通常是最后一个）实体化为它的数字字符引用。</span><span class="sxs-lookup"><span data-stu-id="2a054-134">To protect text nodes that only contain white space, one of the white-space characters, generally the last one, is entitized as its numeric character reference.</span></span> <span data-ttu-id="2a054-135">这样，重新分析将保留空格文本节点，而不考虑分析期间空格处理的设置。</span><span class="sxs-lookup"><span data-stu-id="2a054-135">In this way, reparsing preserves the white-space text node, regardless of the setting of the white-space handling during parsing.</span></span>  
  
 <span data-ttu-id="2a054-136">例如：</span><span class="sxs-lookup"><span data-stu-id="2a054-136">For example:</span></span>  
  
```sql
declare @u NVARCHAR(50)  
set @u = N'<a a="  
    '+NCHAR(0xD800)+NCHAR(0xDF00)+N'>">   '+NCHAR(0xA)+N'</a>'  
select CAST(CONVERT(XML,@u,1) as NVARCHAR(50))  
```  
  
 <span data-ttu-id="2a054-137">结果如下：</span><span class="sxs-lookup"><span data-stu-id="2a054-137">This is the result:</span></span>  
  
```  
<a a="  
    𐌀>">     
</a>  
```  
  
 <span data-ttu-id="2a054-138">如果不想应用最后空格保护规则，可以在将 **xml** 转换为字符串或二进制类型时使用显式 CONVERT 选项 1。</span><span class="sxs-lookup"><span data-stu-id="2a054-138">If you do not want to apply the last white-space protection rule, you can use the explicit CONVERT option 1 when casting from **xml** to a string or binary type.</span></span> <span data-ttu-id="2a054-139">例如，为避免实体化，可以执行以下语句：</span><span class="sxs-lookup"><span data-stu-id="2a054-139">For example, to avoid entitization, you can do the following:</span></span>  
  
```sql
select CONVERT(NVARCHAR(50), CONVERT(XML, '<a>   </a>', 1), 1)  
```  
  
 <span data-ttu-id="2a054-140">请注意， [query() 方法（xml 数据类型）](/sql/t-sql/xml/query-method-xml-data-type) 会产生 xml 数据类型实例。</span><span class="sxs-lookup"><span data-stu-id="2a054-140">Note that, the [query() Method (xml Data Type)](/sql/t-sql/xml/query-method-xml-data-type) results in an xml data type instance.</span></span> <span data-ttu-id="2a054-141">因此，将根据前面介绍的规则对转换为字符串或二进制类型的 **query()** 方法的任何结果进行实体化。</span><span class="sxs-lookup"><span data-stu-id="2a054-141">Therefore, any result of the **query()** method that is cast to a string or binary type is entitized according to the previously described rules.</span></span> <span data-ttu-id="2a054-142">如果要获取不经过实体化的字符串值，则应改用 [value() 方法（xml 数据类型）](/sql/t-sql/xml/value-method-xml-data-type) 。</span><span class="sxs-lookup"><span data-stu-id="2a054-142">If you want to obtain the string values that are not entitized, you should use the [value() Method (xml Data Type)](/sql/t-sql/xml/value-method-xml-data-type) instead.</span></span> <span data-ttu-id="2a054-143">下面是使用 **query()** 方法的示例：</span><span class="sxs-lookup"><span data-stu-id="2a054-143">Following is an example of using the **query()** method:</span></span>  
  
```sql
declare @x xml  
set @x = N'<a>This example contains an entitized char: <.</a>'  
select @x.query('/a/text()')  
```  
  
 <span data-ttu-id="2a054-144">结果如下：</span><span class="sxs-lookup"><span data-stu-id="2a054-144">This is the result:</span></span>  
  
```  
This example contains an entitized char: <.  
```  
  
 <span data-ttu-id="2a054-145">下面是使用 **value()** 方法的示例：</span><span class="sxs-lookup"><span data-stu-id="2a054-145">Following is an example of using the **value()** method:</span></span>  
  
```sql
select @x.value('(/a/text())[1]', 'nvarchar(100)')  
```  
  
 <span data-ttu-id="2a054-146">结果如下：</span><span class="sxs-lookup"><span data-stu-id="2a054-146">This is the result:</span></span>  
  
```  
This example contains an entitized char: <.  
```  
  
## <a name="serializing-a-typed-xml-data-type"></a><span data-ttu-id="2a054-147">对类型化的 xml 数据类型进行序列化</span><span class="sxs-lookup"><span data-stu-id="2a054-147">Serializing a Typed xml Data Type</span></span>  
 <span data-ttu-id="2a054-148">类型化的 **xml** 数据类型实例包括根据其 XML 架构类型类型化的值。</span><span class="sxs-lookup"><span data-stu-id="2a054-148">A typed **xml** data type instance contains values that are typed according to their XML schema types.</span></span> <span data-ttu-id="2a054-149">根据这些值的 XML 架构类型对这些值进行序列化，使用的格式与 XQuery 转换为 xs:string 所产生的格式相同。</span><span class="sxs-lookup"><span data-stu-id="2a054-149">These values are serialized according to their XML schema type in the same format as the XQuery cast to xs:string produces.</span></span> <span data-ttu-id="2a054-150">有关详细信息，请参阅 [XQuery 中的类型转换规则](/sql/xquery/type-casting-rules-in-xquery)。</span><span class="sxs-lookup"><span data-stu-id="2a054-150">For more information, see [Type Casting Rules in XQuery](/sql/xquery/type-casting-rules-in-xquery).</span></span>  
  
 <span data-ttu-id="2a054-151">例如，下面的示例显示了将 xs:double 值 1.34e1 序列化为 13.4：</span><span class="sxs-lookup"><span data-stu-id="2a054-151">For example, the xs:double value 1.34e1 is serialized to 13.4 as shown in the following example:</span></span>  
  
```sql
declare @x xml  
set @x =''  
select CAST(@x.query('1.34e1') as nvarchar(50))  
```  
  
 <span data-ttu-id="2a054-152">将返回字符串值 13.4。</span><span class="sxs-lookup"><span data-stu-id="2a054-152">This returns the string value 13.4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a054-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2a054-153">See Also</span></span>  
 <span data-ttu-id="2a054-154">[XQuery 中的类型转换规则](/sql/xquery/type-casting-rules-in-xquery) </span><span class="sxs-lookup"><span data-stu-id="2a054-154">[Type Casting Rules in XQuery](/sql/xquery/type-casting-rules-in-xquery) </span></span>  
 [<span data-ttu-id="2a054-155">CAST 和 CONVERT (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2a054-155">CAST and CONVERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/cast-and-convert-transact-sql)  
  
  
