---
title: XSD 元素和属性到表和列的显式映射 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- explicit schema mapping [SQLXML]
- XPath queries [SQLXML], annotated XSD schemas in queries
- sql:field
- row mapping [SQLXML]
- attribute mapping [SQLXML], explicit mapping
- field annotation
- XSD schemas [SQLXML], mapping attributes and elements
- names [SQLXML]
- relation annotation
- table/view mapping [SQLXML], explicit mapping
- sql:relation
- mapping schema [SQLXML], explicit mapping
- annotated XSD schemas, mapping attributes and elements
- column mapping [SQLXML]
- element mapping [SQLXML], explicit mapping
- table mapping [SQLXML], explicit mapping
- element/attribute mapping [SQLXML]
ms.assetid: 7a5ebeb6-7322-4141-a307-ebcf95976146
author: rothja
ms.author: jroth
ms.openlocfilehash: f3400682b5f28835ca039912aab058691929a6c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578746"
---
# <a name="explicit-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-40"></a><span data-ttu-id="16fa4-102">XSD 元素和属性到表和列的显式映射 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="16fa4-102">Explicit Mapping of XSD Elements and Attributes to Tables and Columns (SQLXML 4.0)</span></span>
  <span data-ttu-id="16fa4-103">当使用 XSD 架构提供关系数据库的 XML 视图时，必须将该架构的元素和属性映射至数据库的表和列。</span><span class="sxs-lookup"><span data-stu-id="16fa4-103">When using an XSD schema to provide an XML view of the relational database , the elements and attributes of the schema must be mapped to tables and columns of the database.</span></span> <span data-ttu-id="16fa4-104">数据库表/视图中的行将映射至 XML 文档中的元素。</span><span class="sxs-lookup"><span data-stu-id="16fa4-104">The rows in the database table/view will map to elements in the XML document.</span></span> <span data-ttu-id="16fa4-105">数据库中的列值映射到属性或元素。</span><span class="sxs-lookup"><span data-stu-id="16fa4-105">The column values in the database map to attributes or elements.</span></span>  
  
 <span data-ttu-id="16fa4-106">当针对带批注的 XSD 架构指定 XPath 查询时，将从该架构中的元素和属性的数据映射到的表和列中检索这些数据。</span><span class="sxs-lookup"><span data-stu-id="16fa4-106">When XPath queries are specified against the annotated XSD schema, the data for the elements and attributes in the schema is retrieved from the tables and columns to which they map.</span></span> <span data-ttu-id="16fa4-107">若要从数据库中获取单个值，XSD 架构中指定的映射必须同时具备关系和字段规范。</span><span class="sxs-lookup"><span data-stu-id="16fa4-107">To obtain a single value from the database, the mapping specified in the XSD schema must have both relation and field specification.</span></span> <span data-ttu-id="16fa4-108">如果元素/属性的名称与其映射到的表/视图或列的名称不相同，则使用 `sql:relation` 和 `sql:field` 批注指定 XML 文档中的元素或属性和数据库中的表（视图）或列之间的映射。</span><span class="sxs-lookup"><span data-stu-id="16fa4-108">If the name of an element/attribute is not the same name as the table/view or column name to which it maps, the `sql:relation` and `sql:field` annotations are used to specify the mapping between an element or attribute in an XML document and the table (view) or column in a database.</span></span>  
  
## <a name="sql-relation"></a><span data-ttu-id="16fa4-109">sql-relation</span><span class="sxs-lookup"><span data-stu-id="16fa4-109">sql-relation</span></span>  
 <span data-ttu-id="16fa4-110">添加 `sql:relation` 批注，以便将 XSD 架构中的 XML 节点映射至数据库表。</span><span class="sxs-lookup"><span data-stu-id="16fa4-110">The `sql:relation` annotation is added to map an XML node in the XSD schema to a database table.</span></span> <span data-ttu-id="16fa4-111">将表（视图）名称指定为 `sql:relation` 批注的值。</span><span class="sxs-lookup"><span data-stu-id="16fa4-111">The name of a table (view) is specified as the value of the `sql:relation` annotation.</span></span>  
  
 <span data-ttu-id="16fa4-112">当在元素上指定 `sql:relation` 时，此批注的范围适用于在该元素的复杂类型定义中描述的所有属性和子元素，因而提供了一种编写批注的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="16fa4-112">When `sql:relation` is specified on an element, the scope of this annotation applies to all attributes and child elements that are described in the complex type definition of that element, therefore providing a shortcut in writing annotations.</span></span>  
  
 <span data-ttu-id="16fa4-113">`sql:relation`当中有效的标识符 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 在 XML 中无效时，批注也很有用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="16fa4-113">The `sql:relation` annotation is also useful when identifiers that are valid in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are not valid in XML.</span></span> <span data-ttu-id="16fa4-114">例如，“Order Details”是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的有效表名，但该名称在 XML 中无效。</span><span class="sxs-lookup"><span data-stu-id="16fa4-114">For example, "Order Details" is a valid table name in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] but not in XML.</span></span> <span data-ttu-id="16fa4-115">在这种情况下，可以使用 `sql:relation` 批注指定映射，例如：</span><span class="sxs-lookup"><span data-stu-id="16fa4-115">In such cases, the `sql:relation` annotation can be used to specify the mapping, for example:</span></span>  
  
```  
<xsd:element name="OD" sql:relation="[Order Details]">  
```  
  
## <a name="sql-field"></a><span data-ttu-id="16fa4-116">sql-field</span><span class="sxs-lookup"><span data-stu-id="16fa4-116">sql-field</span></span>  
 <span data-ttu-id="16fa4-117">`sql-field` 批注将元素或属性映射至数据库列。</span><span class="sxs-lookup"><span data-stu-id="16fa4-117">The `sql-field` annotation maps an element or attribute to a database column.</span></span> <span data-ttu-id="16fa4-118">添加 `sql:field` 批注，以便将架构中的 XML 节点映射至数据库列。</span><span class="sxs-lookup"><span data-stu-id="16fa4-118">The `sql:field` annotation is added to map an XML node in the schema to a database column.</span></span> <span data-ttu-id="16fa4-119">不能在空内容元素上指定 `sql:field`。</span><span class="sxs-lookup"><span data-stu-id="16fa4-119">You cannot specify `sql:field` on an empty content element.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="16fa4-120">示例</span><span class="sxs-lookup"><span data-stu-id="16fa4-120">Examples</span></span>  
 <span data-ttu-id="16fa4-121">若要创建使用以下示例的工作示例，必须满足某些要求。</span><span class="sxs-lookup"><span data-stu-id="16fa4-121">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="16fa4-122">有关详细信息，请参阅[运行 SQLXML 示例的要求](../sqlxml/requirements-for-running-sqlxml-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="16fa4-122">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-the-sqlrelation-and-sqlfield-annotations"></a><span data-ttu-id="16fa4-123">A.</span><span class="sxs-lookup"><span data-stu-id="16fa4-123">A.</span></span> <span data-ttu-id="16fa4-124">指定 sql:relation 和 sql:field 批注</span><span class="sxs-lookup"><span data-stu-id="16fa4-124">Specifying the sql:relation and sql:field annotations</span></span>  
 <span data-ttu-id="16fa4-125">在此示例中，XSD 架构包含 **\<Contact>** 带有和子元素的复杂类型的元素 **\<FName>** **\<LName>** 和**ContactID**属性。</span><span class="sxs-lookup"><span data-stu-id="16fa4-125">In this example, the XSD schema consists of an **\<Contact>** element of complex type with **\<FName>** and **\<LName>** child elements and the **ContactID** attribute.</span></span>  
  
 <span data-ttu-id="16fa4-126">`sql:relation`批注将元素映射 **\<Contact>** 到 AdventureWorks 数据库中的 Person 表。</span><span class="sxs-lookup"><span data-stu-id="16fa4-126">The `sql:relation` annotation maps the **\<Contact>** element to the Person.Contact table in the AdventureWorks database.</span></span> <span data-ttu-id="16fa4-127">`sql:field`批注将元素映射 **\<FName>** 到 FirstName 列，并将 **\<LName>** 元素映射到 LastName 列。</span><span class="sxs-lookup"><span data-stu-id="16fa4-127">The `sql:field` annotation maps the **\<FName>** element to the FirstName column and the **\<LName>** element to the LastName column.</span></span>  
  
 <span data-ttu-id="16fa4-128">没有为**ContactID**属性指定批注。</span><span class="sxs-lookup"><span data-stu-id="16fa4-128">No annotation is specified for the **ContactID** attribute.</span></span> <span data-ttu-id="16fa4-129">这导致将属性默认映射为具有相同名称的列。</span><span class="sxs-lookup"><span data-stu-id="16fa4-129">This results in a default mapping of the attribute to the column with the same name.</span></span>  
  
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
        <xsd:attribute name="ContactID"   
                       type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="16fa4-130">针对架构测试示例 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="16fa4-130">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="16fa4-131">复制上面的架构代码，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="16fa4-131">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="16fa4-132">将文件另存为 MySchema-annotated.xml。</span><span class="sxs-lookup"><span data-stu-id="16fa4-132">Save the file as MySchema-annotated.xml.</span></span>  
  
2.  <span data-ttu-id="16fa4-133">复制下面的模板，然后将其粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="16fa4-133">Copy the following template below and paste it into a text file.</span></span> <span data-ttu-id="16fa4-134">在您保存 MySchema-annotated.xml 的相同目录中将该文件另存为 MySchema-annotatedT.xml。</span><span class="sxs-lookup"><span data-stu-id="16fa4-134">Save the file as MySchema-annotatedT.xml in the same directory where you saved MySchema-annotated.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="MySchema-annotated.xml">  
        /Contact  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="16fa4-135">为映射架构 (MySchema-annotated.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="16fa4-135">The directory path specified for the mapping schema (MySchema-annotated.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="16fa4-136">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="16fa4-136">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchema-annotated.xml"  
    ```  
  
3.  <span data-ttu-id="16fa4-137">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="16fa4-137">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="16fa4-138">有关详细信息，请参阅[使用 ADO 执行 SQLXML 查询](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="16fa4-138">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="16fa4-139">下面是部分结果集：</span><span class="sxs-lookup"><span data-stu-id="16fa4-139">Here is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
 <Contact ContactID="1">   
    <FName>Gustavo</FName>   
    <LName>Achong</LName>   
 </Contact>   
  .....  
</ROOT>  
```  
  
  
