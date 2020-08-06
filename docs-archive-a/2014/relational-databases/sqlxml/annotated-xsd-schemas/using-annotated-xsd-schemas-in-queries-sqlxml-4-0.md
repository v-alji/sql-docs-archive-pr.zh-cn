---
title: 在查询中使用带批注的 XSD 架构 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- queries [SQLXML]
- inline schemas [SQLXML]
- XPath queries [SQLXML], annotated XSD schemas in queries
- queries [SQLXML], annotated XSD schemas
- retrieving data
- mapping schema [SQLXML], queries
- multiple inline schemas
- annotated XSD schemas, queries
- XSD schemas [SQLXML], queries
- templates [SQLXML], annotated XSD schemas in queries
ms.assetid: 927a30a2-eae8-420d-851d-551c5f884f3c
author: rothja
ms.author: jroth
ms.openlocfilehash: c3038ea234f707da7a87a030cb4110510f5a77c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588422"
---
# <a name="using-annotated-xsd-schemas-in-queries-sqlxml-40"></a><span data-ttu-id="9f2b2-102">在查询中使用带批注的 XSD 架构 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="9f2b2-102">Using Annotated XSD Schemas in Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="9f2b2-103">通过在模板中针对 XSD 架构指定 XPath 查询，可以针对带批注的架构指定查询以从数据库检索数据。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-103">You can specify queries against an annotated schema to retrieve data from the database by specifying XPath queries in a template against the XSD schema.</span></span>  
  
 <span data-ttu-id="9f2b2-104">**\<sql:xpath-query>** 元素允许你为带有批注的架构所定义的 XML 视图指定 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-104">The **\<sql:xpath-query>** element allows you to specify an XPath query against the XML view that is defined by the annotated schema.</span></span> <span data-ttu-id="9f2b2-105">使用元素的属性标识要对其执行 XPath 查询的带批注的架构 `mapping-schema` **\<sql:xpath-query>** 。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-105">The annotated schema against which the XPath query is to be executed is identified by using the `mapping-schema` attribute of the **\<sql:xpath-query>** element.</span></span>  
  
 <span data-ttu-id="9f2b2-106">模板是包含一个或多个查询的有效 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-106">Templates are valid XML documents that contain one or more queries.</span></span> <span data-ttu-id="9f2b2-107">FOR XML 和 XPath 查询返回文档片段。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-107">The FOR XML and XPath queries return a document fragment.</span></span> <span data-ttu-id="9f2b2-108">模板用作文档片段的容器；因此，模板提供了一种指定单个顶级元素的方法。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-108">Templates act as containers for the document fragments; templates thus provide a way to specify a single, top-level element.</span></span>  
  
 <span data-ttu-id="9f2b2-109">本主题中的示例使用模板针对带批注的架构指定 XPath 查询以从数据库检索数据。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-109">The examples in this topic use templates to specify an XPath query against an annotated schema to retrieve data from the database.</span></span>  
  
 <span data-ttu-id="9f2b2-110">例如，请看下面这个带批注的架构：</span><span class="sxs-lookup"><span data-stu-id="9f2b2-110">For example, consider this annotated schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact" >  
     <xsd:complexType>  
       <xsd:attribute name="ContactID" type="xsd:string" />   
       <xsd:attribute name="FirstName" type="xsd:string" />   
       <xsd:attribute name="LastName"  type="xsd:string" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="9f2b2-111">为了便于说明，此 XSD 架构存储在一个名为 Schema2.xml 的文件中。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-111">For the purpose of illustration, this XSD schema is stored in file named Schema2.xml.</span></span> <span data-ttu-id="9f2b2-112">这样，就可以在下面的模板文件 (Schema2T.xml) 中指定针对带批注的架构的 XPath 查询：</span><span class="sxs-lookup"><span data-stu-id="9f2b2-112">You could then have an XPath query against the annotated schema specified in the following template file (Schema2T.xml):</span></span>  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql"  
     >  
          Person.Contact[@ContactID="1"]  
</sql:xpath-query>  
```  
  
 <span data-ttu-id="9f2b2-113">然后，您可以创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 以将此查询作为模板文件的一部分执行。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-113">You can then create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the query as part of a template file.</span></span> <span data-ttu-id="9f2b2-114">有关详细信息，请参阅[SQLXML 4.0&#41;中 &#40;弃用的带批注 XDR 架构](annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-114">For more information, see [Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;](annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).</span></span>  
  
## <a name="using-inline-mapping-schemas"></a><span data-ttu-id="9f2b2-115">使用内联映射架构</span><span class="sxs-lookup"><span data-stu-id="9f2b2-115">Using Inline Mapping Schemas</span></span>  
 <span data-ttu-id="9f2b2-116">可以在模板中直接包含带批注的架构，这样就可以在模板中针对内联架构指定 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-116">An annotated schema can be included directly in a template, and then an XPath query can be specified in the template against the inline schema.</span></span> <span data-ttu-id="9f2b2-117">模板也可以是一个 updategram。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-117">The template can also be an updategram.</span></span>  
  
 <span data-ttu-id="9f2b2-118">模板中可包含多个内联架构。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-118">A template can include multiple inline schemas.</span></span> <span data-ttu-id="9f2b2-119">若要使用模板中包含的内联架构，请在元素上指定具有唯一值的**id**属性 **\<xsd:schema>** ，然后使用 **#idvalue**引用内联架构。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-119">To use an inline schema that is included in a template, specify the **id** attribute with a unique value on the **\<xsd:schema>** element, and then use **#idvalue** to reference the inline schema.</span></span> <span data-ttu-id="9f2b2-120">**Id**属性在行为上与在 XDR 架构中使用的**sql： id** ( {urn：2]。sql：) id 相同。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-120">The **id** attribute is identical in behavior to the **sql:id** ({urn:schemas-microsoft-com:xml-sql}id) used in XDR schemas.</span></span>  
  
 <span data-ttu-id="9f2b2-121">例如，下面的模板指定两个带批注的内联架构：</span><span class="sxs-lookup"><span data-stu-id="9f2b2-121">For example, the following template specifies two inline-annotated schemas:</span></span>  
  
```  
<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'>  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
        xmlns:ms='urn:schemas-microsoft-com:mapping-schema'  
        id='InLineSchema1' sql:is-mapping-schema='1'>  
  <xsd:element name='Employees' ms:relation='HumanResources.Employee'>  
    <xsd:complexType>  
      <xsd:attribute name='LoginID'   
                     type='xsd:string'/>  
      <xsd:attribute name='Title'   
                     type='xsd:string'/>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
        xmlns:ms='urn:schemas-microsoft-com:mapping-schema'  
        id='InLineSchema2' sql:is-mapping-schema='1'>  
  <xsd:element name='Contacts' ms:relation='Person.Contact'>  
    <xsd:complexType>  
  
      <xsd:attribute name='ContactID'   
                     type='xsd:string' />  
      <xsd:attribute name='FirstName'   
                     type='xsd:string' />  
      <xsd:attribute name='LastName'   
                     type='xsd:string' />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
  
<sql:xpath-query xmlns:sql='urn:schemas-microsoft-com:xml-sql'   
        mapping-schema='#InLineSchema1'>  
    /Employees[@LoginID='adventure-works\guy1']  
</sql:xpath-query>  
  
<sql:xpath-query xmlns:sql='urn:schemas-microsoft-com:xml-sql'   
        mapping-schema='#InLineSchema2'>  
    /Contacts[@ContactID='1']  
</sql:xpath-query>  
</ROOT>  
```  
  
 <span data-ttu-id="9f2b2-122">该模板还指定了两个 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-122">The template also specifies two XPath queries.</span></span> <span data-ttu-id="9f2b2-123">每个 **\<xpath-query>** 元素都通过指定属性来唯一标识映射架构 `mapping-schema` 。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-123">Each of the **\<xpath-query>** elements uniquely identifies the mapping schema by specifying the `mapping-schema` attribute.</span></span>  
  
 <span data-ttu-id="9f2b2-124">在模板中指定内联架构时， `sql:is-mapping-schema` 还必须在元素上指定批注 **\<xsd:schema>** 。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-124">When you specify an inline schema in the template, the `sql:is-mapping-schema` annotation must also be specified on the **\<xsd:schema>** element.</span></span> <span data-ttu-id="9f2b2-125">`sql:is-mapping-schema` 取布尔值（0=false，1=true）。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-125">The `sql:is-mapping-schema` takes a Boolean value (0=false, 1=true).</span></span> <span data-ttu-id="9f2b2-126">带有 sql：的内联架构**为-映射-schema = "1"** 被视为内联批注的架构，不在 XML 文档中返回。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-126">An inline schema with **sql:is-mapping-schema="1"** is treated as inline annotated schema and is not returned in the XML document.</span></span>  
  
 <span data-ttu-id="9f2b2-127">`sql:is-mapping-schema` 批注属于模板命名空间 `urn:schemas-microsoft-com:xml-sql`。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-127">The `sql:is-mapping-schema` annotation belongs to the template namespace `urn:schemas-microsoft-com:xml-sql`.</span></span>  
  
 <span data-ttu-id="9f2b2-128">若要测试该示例，请在本地目录中保存该模板 (InlineSchemaTemplate.xml)，然后创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 以执行该模板。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-128">To test this example, save the template (InlineSchemaTemplate.xml) in a local directory and then create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span> <span data-ttu-id="9f2b2-129">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-129">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="9f2b2-130">除了在 `mapping-schema` 模板中的元素上指定属性外 **\<sql:xpath-query>** (当存在 XPath 查询) 或 **\<updg:sync>** updategram 中的元素时，你可以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="9f2b2-130">In addition to specifying the `mapping-schema` attribute on the **\<sql:xpath-query>** element in a template (when there is an XPath query), or on **\<updg:sync>** element in an updategram, you can do the following:</span></span>  
  
-   <span data-ttu-id="9f2b2-131">在 `mapping-schema` **\<ROOT>** 模板 (全局声明) 的元素上指定属性。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-131">Specify the `mapping-schema` attribute on the **\<ROOT>** element (global declaration) in the template.</span></span> <span data-ttu-id="9f2b2-132">这样，该映射架构就成为默认架构，并将由无显式 `mapping-schema` 批注的所有 XPath 和 updategram 节点使用。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-132">This mapping schema then becomes the default schema that will be used by all XPath and updategram nodes that have no explicit `mapping-schema` annotation.</span></span>  
  
-   <span data-ttu-id="9f2b2-133">使用 ADO `mapping schema` 对象指定 `Command` 属性。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-133">Specify the `mapping schema` attribute by using the ADO `Command` object.</span></span>  
  
 <span data-ttu-id="9f2b2-134">`mapping-schema`或元素上指定的特性 **\<xpath-query>** **\<updg:sync>** 具有最高优先级; ADO `Command` 对象的优先级最低。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-134">The `mapping-schema` attribute that is specified on the **\<xpath-query>** or **\<updg:sync>** element has the highest precedence; the ADO `Command` object has the lowest precedence.</span></span>  
  
 <span data-ttu-id="9f2b2-135">请注意，如果在模板中指定 XPath 查询，但未指定用于执行 XPath 查询的映射架构，则 XPath 查询将被视为**dbobject**类型的查询。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-135">Note that if you specify an XPath query in a template and do not specify a mapping schema against which the XPath query is executed, the XPath query is treated as a **dbobject** type query.</span></span> <span data-ttu-id="9f2b2-136">例如，考虑以下模板：</span><span class="sxs-lookup"><span data-stu-id="9f2b2-136">For example, consider this template:</span></span>  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql">  
          Production.ProductPhoto[@ProductPhotoID='100']/@LargePhoto  
</sql:xpath-query>  
```  
  
 <span data-ttu-id="9f2b2-137">该模板指定了一个 XPath 查询，但未指定映射架构。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-137">The template specifies an XPath query but it does not specify a mapping schema.</span></span> <span data-ttu-id="9f2b2-138">因此，此查询将被视为**dbobject**类型的查询，其中 ProductPhoto 是表名称， @ProductPhotoID = ' 100 ' 是一个谓词，用于查找 ID 值为100的产品照片。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-138">Therefore, this query is treated as a **dbobject** type query in which Production.ProductPhoto is the table name and @ProductPhotoID='100' is a predicate that finds a product photo with the ID value of 100.</span></span> <span data-ttu-id="9f2b2-139">@LargePhoto要从中检索值的列。</span><span class="sxs-lookup"><span data-stu-id="9f2b2-139">@LargePhoto is the column from which to retrieve the value.</span></span>  
  
  
