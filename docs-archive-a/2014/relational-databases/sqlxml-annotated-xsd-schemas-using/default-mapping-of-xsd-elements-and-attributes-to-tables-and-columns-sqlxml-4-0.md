---
title: XSD 元素和属性到表和列的默认映射 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XSD schemas [SQLXML], mapping attributes and elements
- mapping schema [SQLXML], default mapping
- element mapping [SQLXML], default mapping
- element mapping [SQLXML]
- table mapping [SQLXML]
- annotated XSD schemas, mapping attributes and elements
- table/view mapping [SQLXML]
- column mapping [SQLXML]
- attribute mapping [SQLXML], default mapping
- default schema mapping
- table mapping [SQLXML], default mapping
- testing XPath query against schema
- xml data type [SQL Server], SQLXML
- table/view mapping [SQLXML], default mapping
- element/attribute mapping [SQLXML]
ms.assetid: 9a18e92a-6cfb-4a14-993a-663a95aabb63
author: rothja
ms.author: jroth
ms.openlocfilehash: 0bccec2413e8a0a6e13283a0f3e5f63ab61e934b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586599"
---
# <a name="default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-40"></a><span data-ttu-id="e9875-102">XSD 元素和属性到表和列的默认映射 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="e9875-102">Default Mapping of XSD Elements and Attributes to Tables and Columns (SQLXML 4.0)</span></span>
  <span data-ttu-id="e9875-103">默认情况下，XSD 带批注的架构中复杂类型的元素映射到指定数据库中具有相同名称的表（视图），而简单类型的元素或属性映射到表中具有相同名称的列。</span><span class="sxs-lookup"><span data-stu-id="e9875-103">By default, an element of complex type in an XSD annotated schema maps to the table (view) with the same name in the specified database, and an element or attribute of simple type maps to the column with the same name in the table.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e9875-104">示例</span><span class="sxs-lookup"><span data-stu-id="e9875-104">Examples</span></span>  
 <span data-ttu-id="e9875-105">若要创建使用以下示例的工作示例，必须满足某些要求。</span><span class="sxs-lookup"><span data-stu-id="e9875-105">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="e9875-106">有关详细信息，请参阅[运行 SQLXML 示例的要求](../sqlxml/requirements-for-running-sqlxml-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="e9875-106">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-default-mapping"></a><span data-ttu-id="e9875-107">A.</span><span class="sxs-lookup"><span data-stu-id="e9875-107">A.</span></span> <span data-ttu-id="e9875-108">指定默认映射</span><span class="sxs-lookup"><span data-stu-id="e9875-108">Specifying default mapping</span></span>  
 <span data-ttu-id="e9875-109">在本示例中，不在 XSD 架构中指定任何批注。</span><span class="sxs-lookup"><span data-stu-id="e9875-109">In this example, no annotations are specified in the XSD schema.</span></span> <span data-ttu-id="e9875-110">**\<Person.Contact>** 元素属于复杂类型，因此默认情况下映射到 AdventureWorks 数据库中的 Person 表。</span><span class="sxs-lookup"><span data-stu-id="e9875-110">The **\<Person.Contact>** element is of complex type and, therefore, maps by default to the Person.Contact table in the AdventureWorks database.</span></span> <span data-ttu-id="e9875-111">元素 (ContactID、FirstName、LastName) 的所有属性 **\<Person.Contact>** 都属于简单类型，并且默认映射为 Person 表中具有相同名称的列。</span><span class="sxs-lookup"><span data-stu-id="e9875-111">All the attributes (ContactID, FirstName, LastName) of the **\<Person.Contact>** element are of simple type and map by default to columns with the same names in the Person.Contact table.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact" >  
     <xsd:complexType>  
       <xsd:attribute name="ContactID"  type="xsd:string" />   
       <xsd:attribute name="FirstName"   type="xsd:string" />   
       <xsd:attribute name="LastName"    type="xsd:string" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="e9875-112">针对架构测试示例 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="e9875-112">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="e9875-113">复制上面的架构代码，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="e9875-113">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="e9875-114">将文件另存为 MySchema.xml。</span><span class="sxs-lookup"><span data-stu-id="e9875-114">Save the file as MySchema.xml.</span></span>  
  
2.  <span data-ttu-id="e9875-115">复制以下模板，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="e9875-115">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="e9875-116">在您保存 MySchema.xml 的相同目录中将该文件另存为 MySchemaT.xml。</span><span class="sxs-lookup"><span data-stu-id="e9875-116">Save the file as MySchemaT.xml in the same directory where you saved MySchema.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="MySchema.xml">  
            /Person.Contact  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="e9875-117">为映射架构 (MySchema.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="e9875-117">The directory path specified for the mapping schema (MySchema.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="e9875-118">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="e9875-118">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchema.xml"  
    ```  
  
3.  <span data-ttu-id="e9875-119">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="e9875-119">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="e9875-120">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="e9875-120">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="e9875-121">下面是部分结果集：</span><span class="sxs-lookup"><span data-stu-id="e9875-121">Here is the partial result set:</span></span>  
  
```  
<?xml version="1.0" encoding="UTF-8" ?>  
<ROOT>  
  <Person.Contact ContactID="1" FirstName="Gustavo" LastName="Achong"/>  
  <Person.Contact ContactID="2" FirstName="Catherine" LastName="Abel"/>  
   ...  
</ROOT>  
```  
  
### <a name="b-mapping-an-xml-element-to-a-database-column"></a><span data-ttu-id="e9875-122">B.</span><span class="sxs-lookup"><span data-stu-id="e9875-122">B.</span></span> <span data-ttu-id="e9875-123">将 XML 元素映射到数据库列</span><span class="sxs-lookup"><span data-stu-id="e9875-123">Mapping an XML element to a database column</span></span>  
 <span data-ttu-id="e9875-124">在本示例中，由于不使用批注，因此还会发生默认映射。</span><span class="sxs-lookup"><span data-stu-id="e9875-124">In this example, default mapping also takes place because no annotations are used.</span></span> <span data-ttu-id="e9875-125">**\<Person.Contact>** 元素属于复杂类型，并且映射到数据库中具有相同名称的表。</span><span class="sxs-lookup"><span data-stu-id="e9875-125">The **\<Person.Contact>** element is of complex type and maps to the table with the same name in the database.</span></span> <span data-ttu-id="e9875-126">元素 **\<FirstName>** 和 **\<LastName>** "**雇员 id** " 属性属于简单类型，因此，映射到具有相同名称的列。</span><span class="sxs-lookup"><span data-stu-id="e9875-126">The elements **\<FirstName>** and **\<LastName>** and the **EmployeeID** attribute are of simple type and, therefore, map to the columns with the same names.</span></span> <span data-ttu-id="e9875-127">本示例与前一示例的唯一差别在于本示例使用元素来映射 FirstName 和 LastName 字段。</span><span class="sxs-lookup"><span data-stu-id="e9875-127">The only difference between this and the previous example are that elements are used for mapping the FirstName and LastName fields.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact">  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="FirstName" type="xsd:string" />   
        <xsd:element name="LastName" type="xsd:string" />   
      </xsd:sequence>  
      <xsd:attribute name="ContactID" type="xsd:integer" />   
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="e9875-128">针对架构测试示例 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="e9875-128">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="e9875-129">复制上面的架构代码，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="e9875-129">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="e9875-130">将文件另存为 MySchemaElements.xml。</span><span class="sxs-lookup"><span data-stu-id="e9875-130">Save the file as MySchemaElements.xml.</span></span>  
  
2.  <span data-ttu-id="e9875-131">创建以下模板 (MySchemaElementsT.xml) 并将其保存到上一步中使用的相同目录中。</span><span class="sxs-lookup"><span data-stu-id="e9875-131">Create the following template (MySchemaElementsT.xml), and save it in the same directory used in the previous step.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="MySchemaElements.xml">  
            /Person.Contact  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="e9875-132">为此映射架构指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="e9875-132">The directory path specified for the mapping schema is relative to the directory where the template is saved.</span></span> <span data-ttu-id="e9875-133">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="e9875-133">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchemaElements.xml"  
    ```  
  
3.  <span data-ttu-id="e9875-134">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="e9875-134">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="e9875-135">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="e9875-135">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="e9875-136">下面是部分结果集：</span><span class="sxs-lookup"><span data-stu-id="e9875-136">Here is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact ContactID="1">  
    <FirstName>Gustavo</FirstName>  
    <LastName>Achong</LastName>  
  </Person.Contact>  
   ...  
</ROOT>  
```  
  
### <a name="c-mapping-an-xml-element-to-an-xml-data-type-column"></a><span data-ttu-id="e9875-137">C.</span><span class="sxs-lookup"><span data-stu-id="e9875-137">C.</span></span> <span data-ttu-id="e9875-138">将 XML 元素映射到 XML 数据类型列</span><span class="sxs-lookup"><span data-stu-id="e9875-138">Mapping an XML element to an XML data type column</span></span>  
 <span data-ttu-id="e9875-139">在本示例中，由于不使用批注，因此还会发生默认映射。</span><span class="sxs-lookup"><span data-stu-id="e9875-139">In this example, default mapping also takes place because no annotations are used.</span></span> <span data-ttu-id="e9875-140">**\<Production.ProductModel>** 元素属于复杂类型，并且映射到数据库中具有相同名称的表。</span><span class="sxs-lookup"><span data-stu-id="e9875-140">The **\<Production.ProductModel>** element is of complex type and maps to the table with the same name in the database.</span></span> <span data-ttu-id="e9875-141">**ProductModelID**属性属于简单类型，因此，映射到具有相同名称的列。</span><span class="sxs-lookup"><span data-stu-id="e9875-141">The **ProductModelID** attribute is of simple type and, therefore, map to the columns with the same names.</span></span> <span data-ttu-id="e9875-142">此示例与前一个示例的唯一区别在于，该 **\<Instructions>** 元素 `xml` 通过使用类型映射到使用数据类型的列 `xsd:anyType` 。</span><span class="sxs-lookup"><span data-stu-id="e9875-142">The only difference between this and the previous examples is that the **\<Instructions>** element is mapping to a column that uses the `xml` data type by using the `xsd:anyType` type.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Production.ProductModel">  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="Instructions" type="xsd:anyType" />   
      </xsd:sequence>  
      <xsd:attribute name="ProductModelID" type="xsd:integer" />   
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="e9875-143">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中已引入了 `xml` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="e9875-143">The `xml` data type was introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="e9875-144">针对架构测试示例 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="e9875-144">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="e9875-145">复制上面的架构代码，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="e9875-145">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="e9875-146">将文件另存为 MySchemaXmlAnyElements.xml。</span><span class="sxs-lookup"><span data-stu-id="e9875-146">Save the file as MySchemaXmlAnyElements.xml.</span></span>  
  
2.  <span data-ttu-id="e9875-147">创建以下模板 (MySchemaXmlAnyElementsT.xml) 并将其保存到上一步中使用的相同目录中。</span><span class="sxs-lookup"><span data-stu-id="e9875-147">Create the following template (MySchemaXmlAnyElementsT.xml), and save it in the same directory used in the previous step.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="MySchemaXmlAnyElements.xml">  
            /Production.ProductModel[@ProductModelID=7]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="e9875-148">为此映射架构指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="e9875-148">The directory path specified for the mapping schema is relative to the directory where the template is saved.</span></span> <span data-ttu-id="e9875-149">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="e9875-149">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchemaXmlAnyElements.xml"  
    ```  
  
3.  <span data-ttu-id="e9875-150">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="e9875-150">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="e9875-151">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="e9875-151">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="e9875-152">下面是部分结果集：</span><span class="sxs-lookup"><span data-stu-id="e9875-152">Here is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Production.ProductModel ProductModelID="7">  
    <Instructions>  
      <root xmlns="http:  
//schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstru  
ctions">  
...  
      </root>  
    <Instructions>  
  </Production.ProductModel>  
</ROOT>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e9875-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e9875-153">See Also</span></span>  
 <span data-ttu-id="e9875-154">[&#40;SQLXML 4.0 的批注的架构安全注意事项&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="e9875-154">[Annotated Schema Security Considerations &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="e9875-155">[XML 数据 (SQL Server)](../xml/xml-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e9875-155">[XML Data &#40;SQL Server&#41;](../xml/xml-data-sql-server.md) </span></span>  
 [<span data-ttu-id="e9875-156">SQLXML 4.0 中的 xml 数据类型支持</span><span class="sxs-lookup"><span data-stu-id="e9875-156">xml Data Type Support in SQLXML 4.0</span></span>](../sqlxml/xml-data-type-support-in-sqlxml-4-0.md)  
  
  
