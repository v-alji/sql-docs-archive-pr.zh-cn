---
title: " (SQLXML 4.0) 的带批注的 XSD 架构简介 |Microsoft Docs"
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- namespaces [SQLXML], annotated XSD schemas
- mapping schema [SQLXML], about mapping schema
- views [SQLXML]
- valid XSD schemas [SQLXML]
- annotations [SQLXML]
- XSD schemas [SQLXML], creating XML views
- annotated XSD schemas, creating XML views
- minimum XSD schema
- annotated XSD schemas, examples
- XML views [SQLXML]
ms.assetid: 15282db1-65c4-43be-bdb7-e9ef49cb33a2
author: rothja
ms.author: jroth
ms.openlocfilehash: b91be71569daa9e5bf4143be9f652617ba7c5b01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588419"
---
# <a name="introduction-to-annotated-xsd-schemas-sqlxml-40"></a><span data-ttu-id="f3502-102">带批注的 XSD 架构简介 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="f3502-102">Introduction to Annotated XSD Schemas (SQLXML 4.0)</span></span>
  <span data-ttu-id="f3502-103">您可以通过使用 XML 架构定义 (XSD) 语言创建关系数据的 XML 视图。</span><span class="sxs-lookup"><span data-stu-id="f3502-103">You can create XML views of relational data by using the XML Schema Definition (XSD) language.</span></span> <span data-ttu-id="f3502-104">然后可通过使用 XML Path 语言 (XPath) 查询对这些视图进行查询。</span><span class="sxs-lookup"><span data-stu-id="f3502-104">These views can then be queried by using XML Path language (XPath) queries.</span></span> <span data-ttu-id="f3502-105">这类似于使用 CREATE VIEW 语句创建视图，然后针对视图指定 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="f3502-105">This is similar to creating views by using CREATE VIEW statements and then specifying SQL queries against the view.</span></span>  
  
 <span data-ttu-id="f3502-106">XML 架构描述了 XML 文档的结构并且还描述了对文档中数据的各种约束。</span><span class="sxs-lookup"><span data-stu-id="f3502-106">An XML schema describes the structure of an XML document and also describes the various constraints on the data in the document.</span></span> <span data-ttu-id="f3502-107">针对该架构指定 XPath 查询时，返回的 XML 文档的结构由对其执行 XPath 查询的架构确定。</span><span class="sxs-lookup"><span data-stu-id="f3502-107">When you specify XPath queries against the schema, the structure of the XML document returned is determined by the schema against which the XPath query is executed.</span></span>  
  
 <span data-ttu-id="f3502-108">在 XSD 架构中， **\<xsd:schema>** 元素包含整个架构; 所有元素声明都必须包含在 **\<xsd:schema>** 元素中。</span><span class="sxs-lookup"><span data-stu-id="f3502-108">In an XSD schema, the **\<xsd:schema>** element encloses the entire schema; all element declarations must be contained within the **\<xsd:schema>** element.</span></span> <span data-ttu-id="f3502-109">您可以描述定义架构所在的命名空间的属性，以及架构中用作元素属性的命名空间 **\<xsd:schema>** 。</span><span class="sxs-lookup"><span data-stu-id="f3502-109">You can describe attributes that define the namespace in which the schema resides and the namespaces that are used in the schema as properties of the **\<xsd:schema>** element.</span></span>  
  
 <span data-ttu-id="f3502-110">有效的 XSD 架构必须包含 **\<xsd:schema>** 定义的元素，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f3502-110">A valid XSD schema must contain the **\<xsd:schema>** element defined as follows:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<!-- additional schema definitions here -->  
</xsd:schema>  
```  
  
 <span data-ttu-id="f3502-111">**\<xsd:schema>** 元素派生自中的 XML 架构命名空间规范 http://www.w3.org/2001/XMLSchema 。</span><span class="sxs-lookup"><span data-stu-id="f3502-111">The **\<xsd:schema>** element is derived from the XML Schema namespace specification at http://www.w3.org/2001/XMLSchema.</span></span>  
  
## <a name="annotations-to-the-xsd-schema"></a><span data-ttu-id="f3502-112">XSD 架构的批注</span><span class="sxs-lookup"><span data-stu-id="f3502-112">Annotations to the XSD Schema</span></span>  
 <span data-ttu-id="f3502-113">您可以对 XSD 架构使用批注来描述数据库映射、查询数据库并返回 XML 文档形式的结果。</span><span class="sxs-lookup"><span data-stu-id="f3502-113">You can use an XSD schema with annotations that describe the mapping to a database, query the database, and return the results in the form of an XML document.</span></span> <span data-ttu-id="f3502-114">使用批注可将 XSD 架构映射到数据库表和列。</span><span class="sxs-lookup"><span data-stu-id="f3502-114">Annotations are provided to map an XSD schema to database tables and columns.</span></span> <span data-ttu-id="f3502-115">可以对 XSD 架构创建的 XML 视图指定 XPath 查询来查询数据库并获取 XML 形式的结果。</span><span class="sxs-lookup"><span data-stu-id="f3502-115">XPath queries can be specified against the XML view created by the XSD schema to query the database and obtain results as an XML.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3502-116">在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 中，XSD 架构语言支持随 [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] 中带批注的 XML-Data Reduced (XDR) 架构语言引入的批注。</span><span class="sxs-lookup"><span data-stu-id="f3502-116">In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0, the XSD schema language supports the annotations introduced with annotated XML-Data Reduced (XDR) schema language in [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)].</span></span> <span data-ttu-id="f3502-117">SQLXML 4.0 中不推荐使用带批注的 XDR。</span><span class="sxs-lookup"><span data-stu-id="f3502-117">Annotated XDR is deprecated in SQLXML 4.0.</span></span>  
  
 <span data-ttu-id="f3502-118">在关系数据库上下文中，将任意 XSD 架构映射到关系存储区很有用。</span><span class="sxs-lookup"><span data-stu-id="f3502-118">In the context of the relational database, it is useful to map the arbitrary XSD schema to a relational store.</span></span> <span data-ttu-id="f3502-119">实现这种映射的一种方法是对 XSD 架构进行批注。</span><span class="sxs-lookup"><span data-stu-id="f3502-119">One way to achieve this is to annotate the XSD schema.</span></span> <span data-ttu-id="f3502-120">带有批注的 XSD 架构称为*映射架构*，它提供有关如何将 XML 数据映射到关系存储区的信息。</span><span class="sxs-lookup"><span data-stu-id="f3502-120">An XSD schema with the annotations is referred to as a *mapping schema*, which provides information pertaining to how XML data is to be mapped to the relational store.</span></span> <span data-ttu-id="f3502-121">实际上，映射架构是关系数据的 XML 视图。</span><span class="sxs-lookup"><span data-stu-id="f3502-121">A mapping schema is, in effect, an XML view of the relational data.</span></span> <span data-ttu-id="f3502-122">使用这些映射能够以 XML 文档形式检索关系数据。</span><span class="sxs-lookup"><span data-stu-id="f3502-122">These mappings can be used to retrieve relational data as an XML document.</span></span>  
  
## <a name="namespace-for-annotations"></a><span data-ttu-id="f3502-123">批注的命名空间</span><span class="sxs-lookup"><span data-stu-id="f3502-123">Namespace for Annotations</span></span>  
 <span data-ttu-id="f3502-124">在 XSD 架构中，批注通过使用命名空间**urn： schema-microsoft-com： mapping-schema**来指定。</span><span class="sxs-lookup"><span data-stu-id="f3502-124">In an XSD schema, annotations are specified by using the namespace **urn:schemas-microsoft-com:mapping-schema**.</span></span> <span data-ttu-id="f3502-125">如下面的示例中所示，指定命名空间的最简单方法是在标记中指定它 **\<xsd:schema>** 。</span><span class="sxs-lookup"><span data-stu-id="f3502-125">As shown in the following example, the easiest way to specify the namespace is to specify it in the **\<xsd:schema>** tag.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
...  
</xsd:schema>  
```  
  
 <span data-ttu-id="f3502-126">命名空间可采用任意前缀。</span><span class="sxs-lookup"><span data-stu-id="f3502-126">The namespace prefix that is used is arbitrary.</span></span> <span data-ttu-id="f3502-127">在本文档中， **sql**前缀用于表示批注命名空间，并将此命名空间中的批注与其他命名空间中的批注区分开来。</span><span class="sxs-lookup"><span data-stu-id="f3502-127">In this documentation, the **sql** prefix is used to denote the annotation namespace and to distinguish annotations in this namespace from those in other namespaces.</span></span>  
  
## <a name="example-of-an-annotated-xsd-schema"></a><span data-ttu-id="f3502-128">带批注的 XSD 架构的示例</span><span class="sxs-lookup"><span data-stu-id="f3502-128">Example of an Annotated XSD Schema</span></span>  
 <span data-ttu-id="f3502-129">在下面的示例中，XSD 架构由元素组成 **\<Person.Contact>** 。</span><span class="sxs-lookup"><span data-stu-id="f3502-129">In the following example, the XSD schema consists of an **\<Person.Contact>** element.</span></span> <span data-ttu-id="f3502-130">**\<Employee>** 元素具有**ContactID**特性和 **\<FirstName>** 和 **\<LastName>** 子元素：</span><span class="sxs-lookup"><span data-stu-id="f3502-130">The **\<Employee>** element has a **ContactID** attribute and **\<FirstName>** and **\<LastName>** child elements:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <xsd:element name="Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"    
                     type="xsd:string" />   
        <xsd:element name="LName"  
                     type="xsd:string" />  
     </xsd:sequence>  
        <xsd:attribute name="ConID" type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="f3502-131">向该 XSD 架构添加批注以将其元素和属性映射到数据库表和列：</span><span class="sxs-lookup"><span data-stu-id="f3502-131">Annotations are added to this XSD schema to map its elements and attributes to the database tables and columns:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Contact" sql:relation="Person.Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"  
                     sql:field="FirstName"   
                     type="xsd:string" />   
        <xsd:element name="LName"    
                     sql:field="LastName"    
                     type="xsd:string" />  
     </xsd:sequence>  
        <xsd:attribute name="ConID"   
                       sql:field="ContactID"   
                       type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="f3502-132">在映射架构中， **\<Contact>** 使用批注将元素映射到示例 AdventureWorks 数据库中的 Contact 表。 `sql:relation`</span><span class="sxs-lookup"><span data-stu-id="f3502-132">In the mapping schema, the **\<Contact>** element is mapped to the Person.Contact table in the sample AdventureWorks database by using the `sql:relation` annotation.</span></span> <span data-ttu-id="f3502-133">通过使用 `sql:field` 批注，将属性 ConID、FName 和 LName 映射到 Person.Contact 表中的 ContactID、FirstName 和 LastName 列。</span><span class="sxs-lookup"><span data-stu-id="f3502-133">The attributes ConID, FName, and LName are mapped to the ContactID, FirstName, and LastName columns in the Person.Contact table by using the `sql:field` annotations.</span></span>  
  
 <span data-ttu-id="f3502-134">此带有批注的 XSD 架构提供了关系数据的 XML 视图。</span><span class="sxs-lookup"><span data-stu-id="f3502-134">This annotated XSD schema provides the XML view of the relational data.</span></span> <span data-ttu-id="f3502-135">可使用 XPath 语言查询此 XML 视图。</span><span class="sxs-lookup"><span data-stu-id="f3502-135">This XML view can be queried using the XPath language.</span></span> <span data-ttu-id="f3502-136">XPath 查询返回的结果是一个 XML 文档，而 SQL 查询返回的结果是行集。</span><span class="sxs-lookup"><span data-stu-id="f3502-136">An XPath query returns an XML document as a result, instead of the rowset that is returned by SQL queries.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3502-137">在映射架构中，指定关系值（如表名和列名）是否区分大小写取决于 SQL Server 是否使用区分大小写的排序规则设置。</span><span class="sxs-lookup"><span data-stu-id="f3502-137">In the mapping schema, case-sensitivity for the specified relational values (such as table name and column name) depends upon if SQL Server is using case-sensitive collation settings.</span></span> <span data-ttu-id="f3502-138">有关详细信息，请参阅 [排序规则和 Unicode 支持](../../collations/collation-and-unicode-support.md)。</span><span class="sxs-lookup"><span data-stu-id="f3502-138">For more information, see [Collation and Unicode Support](../../collations/collation-and-unicode-support.md).</span></span>  
  
## <a name="other-resources"></a><span data-ttu-id="f3502-139">其他资源</span><span class="sxs-lookup"><span data-stu-id="f3502-139">Other Resources</span></span>  
 <span data-ttu-id="f3502-140">有关 XML 架构定义语言 (XSD)、XML Path 语言 (XPath) 和可扩展样式表语言转换 (XSLT) 的详细信息，请访问以下网站：</span><span class="sxs-lookup"><span data-stu-id="f3502-140">You can find more information about XML Schema Definition language (XSD), XML Path language (XPath), and Extensible Stylesheet Language Transformations (XSLT) at the following Web sites:</span></span>  
  
-   <span data-ttu-id="f3502-141">XML 架构第0部分：入门、W3C 建议 (http://www.w3.org/TR/xmlschema-0/)</span><span class="sxs-lookup"><span data-stu-id="f3502-141">XML Schema Part 0: Primer, W3C Recommendation (http://www.w3.org/TR/xmlschema-0/)</span></span>  
  
-   <span data-ttu-id="f3502-142">XML 架构第1部分：结构、W3C 建议 (http://www.w3.org/TR/xmlschema-1/)</span><span class="sxs-lookup"><span data-stu-id="f3502-142">XML Schema Part 1: Structures, W3C Recommendation (http://www.w3.org/TR/xmlschema-1/)</span></span>  
  
-   <span data-ttu-id="f3502-143">XML 架构第2部分：数据类型、W3C 建议 (http://www.w3.org/TR/xmlschema-2/)</span><span class="sxs-lookup"><span data-stu-id="f3502-143">XML Schema Part 2:Datatypes, W3C Recommendation (http://www.w3.org/TR/xmlschema-2/)</span></span>  
  
-   <span data-ttu-id="f3502-144">XML 路径语言 (XPath)  (http://www.w3.org/TR/xpath)</span><span class="sxs-lookup"><span data-stu-id="f3502-144">XML Path Language (XPath) (http://www.w3.org/TR/xpath)</span></span>  
  
-   <span data-ttu-id="f3502-145"> (XSLT) 的 XSL 转换 (http://www.w3.org/TR/xslt)</span><span class="sxs-lookup"><span data-stu-id="f3502-145">XSL Transformations (XSLT) (http://www.w3.org/TR/xslt)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3502-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f3502-146">See Also</span></span>  
 <span data-ttu-id="f3502-147">[&#40;SQLXML 4.0 的批注的架构安全注意事项&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="f3502-147">[Annotated Schema Security Considerations &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="f3502-148">SQLXML 4.0 中 &#40;弃用的带批注 XDR 架构&#41;</span><span class="sxs-lookup"><span data-stu-id="f3502-148">Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;</span></span>](annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)  
  
  
