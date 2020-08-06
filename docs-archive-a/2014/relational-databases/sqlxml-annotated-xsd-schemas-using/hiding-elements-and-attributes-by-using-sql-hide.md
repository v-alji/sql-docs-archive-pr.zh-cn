---
title: 使用 sql： hide | 隐藏元素和属性Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- hiding elements
- element mapping [SQLXML], hiding attributes and elements
- hide annotation
- sql:hide
- table/view mapping [SQLXML], hiding attributes and elements
- table mapping [SQLXML], hiding attributes and elements
- hiding attributes
- annotated XSD schemas, hiding attributes and elements
- attribute mapping [SQLXML], hiding attributes and elements
- column mapping [SQLXML]
- element hiding [SQLXML]
- XSD schemas [SQLXML], hiding attributes and elements
- attribute hiding [SQLXML]
ms.assetid: 0978301b-f068-46b6-82b9-dc555161f52e
author: rothja
ms.author: jroth
ms.openlocfilehash: 5a3beb48be1d9809b170faeafa964ba45156ac28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693673"
---
# <a name="hiding-elements-and-attributes-by-using-sqlhide"></a><span data-ttu-id="713f3-102">使用 sql:hide 隐藏元素和属性</span><span class="sxs-lookup"><span data-stu-id="713f3-102">Hiding Elements and Attributes by Using sql:hide</span></span>
  <span data-ttu-id="713f3-103">针对 XSD 架构执行 XPath 查询时，生成的 XML 文档具有在架构中指定的元素和属性。</span><span class="sxs-lookup"><span data-stu-id="713f3-103">When an XPath query is executed against an XSD schema, the resulting XML document has elements and attributes that are specified in the schema.</span></span> <span data-ttu-id="713f3-104">可以使用 `sql:hide` 批注来指定隐藏架构中的某些元素和属性。</span><span class="sxs-lookup"><span data-stu-id="713f3-104">You can specify that some elements and attributes be hidden in the schema by using the `sql:hide` annotation.</span></span> <span data-ttu-id="713f3-105">当查询的选择条件需要架构中的特定元素或属性，但是不希望在生成的 XML 文档中返回这些元素或属性时，该批注很有用。</span><span class="sxs-lookup"><span data-stu-id="713f3-105">This is useful when the selection criteria of the query require particular elements or attributes in the schema, but you do not want them returned in the XML document that is generated.</span></span>  
  
 <span data-ttu-id="713f3-106">`sql:hide` 批注采用布尔值（0 = FALSE，1 = TRUE）。</span><span class="sxs-lookup"><span data-stu-id="713f3-106">The `sql:hide` annotation takes a Boolean value (0=false, 1=true).</span></span> <span data-ttu-id="713f3-107">可接受的值为 0、1、true 和 false。</span><span class="sxs-lookup"><span data-stu-id="713f3-107">The acceptable values are 0, 1, true, and false.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="713f3-108">示例</span><span class="sxs-lookup"><span data-stu-id="713f3-108">Examples</span></span>  
 <span data-ttu-id="713f3-109">若要创建使用以下示例的工作示例，必须满足某些要求。</span><span class="sxs-lookup"><span data-stu-id="713f3-109">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="713f3-110">有关详细信息，请参阅[运行 SQLXML 示例的要求](../sqlxml/requirements-for-running-sqlxml-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="713f3-110">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-sqlhide-on-an-attribute"></a><span data-ttu-id="713f3-111">A.</span><span class="sxs-lookup"><span data-stu-id="713f3-111">A.</span></span> <span data-ttu-id="713f3-112">对属性指定 sql:hide</span><span class="sxs-lookup"><span data-stu-id="713f3-112">Specifying sql:hide on an attribute</span></span>  
 <span data-ttu-id="713f3-113">本例中的 XSD 架构由 **\<Person.Contact>** 具有**ContactID**、 **FirstName**和**LastName**属性的元素组成。</span><span class="sxs-lookup"><span data-stu-id="713f3-113">The XSD schema in this example consists of an **\<Person.Contact>** element with **ContactID**, **FirstName**, and **LastName** attributes.</span></span>  
  
 <span data-ttu-id="713f3-114">**\<Person.Contact>** 元素属于复杂类型，因此映射到 (默认映射) 相同的名称的表。</span><span class="sxs-lookup"><span data-stu-id="713f3-114">The **\<Person.Contact>** element is of complex type and, therefore, maps to the table of the same name (default mapping).</span></span> <span data-ttu-id="713f3-115">元素的所有属性 **\<Person.Contact>** 都属于简单类型，并且映射到 AdventureWorks 数据库的 Contacttable 中具有相同名称的列。</span><span class="sxs-lookup"><span data-stu-id="713f3-115">All the attributes of **\<Person.Contact>** element are of simple type and map to columns with the same names in the Person.Contacttable in the AdventureWorks database.</span></span> <span data-ttu-id="713f3-116">在架构中， `sql:hide` 批注是在**ContactID**属性中指定的。</span><span class="sxs-lookup"><span data-stu-id="713f3-116">In the schema, the `sql:hide` annotation is specified on the **ContactID** attribute.</span></span> <span data-ttu-id="713f3-117">针对此架构指定 XPath 查询时，XML 文档中将不会返回**ContactID** 。</span><span class="sxs-lookup"><span data-stu-id="713f3-117">When an XPath query is specified against this schema, the **ContactID** is not returned in the XML document.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact" >  
     <xsd:complexType>  
       <xsd:attribute name="ContactID"  sql:hide="true" />   
       <xsd:attribute name="FirstName"   type="xsd:string" />   
       <xsd:attribute name="LastName"    type="xsd:string" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="713f3-118">针对架构测试示例 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="713f3-118">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="713f3-119">复制上面的架构代码，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="713f3-119">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="713f3-120">将文件另存为 Hide.xml。</span><span class="sxs-lookup"><span data-stu-id="713f3-120">Save the file as Hide.xml.</span></span>  
  
2.  <span data-ttu-id="713f3-121">复制以下模板，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="713f3-121">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="713f3-122">在保存 Hide.xml 的相同目录中将该文件另存为 HideT.xml。</span><span class="sxs-lookup"><span data-stu-id="713f3-122">Save the file as HideT.xml in the same directory where you saved Hide.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="Hide.xml">  
            /Person.Contact[@ContactID="1"]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="713f3-123">为映射架构 (Hide.xml) 指定的目录路径是保存模板目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="713f3-123">The directory path specified for the mapping schema (Hide.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="713f3-124">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="713f3-124">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\Hide.xml"  
    ```  
  
3.  <span data-ttu-id="713f3-125">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="713f3-125">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="713f3-126">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="713f3-126">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="713f3-127">下面是结果集：</span><span class="sxs-lookup"><span data-stu-id="713f3-127">Here is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <Person.Contact FirstName="Gustavo" LastName="Achong" />   
</ROOT>  
```  
  
 <span data-ttu-id="713f3-128">如果对元素指定 `sql:hide`，则该元素及其属性或子元素都不会出现在生成的 XML 文档中。</span><span class="sxs-lookup"><span data-stu-id="713f3-128">When `sql:hide` is specified on an element, the element and its attributes or child elements do not appear in the XML document that is generated.</span></span> <span data-ttu-id="713f3-129">下面是在元素上指定的另一个 XSD 架构 `sql:hide` **\<OD>** ：</span><span class="sxs-lookup"><span data-stu-id="713f3-129">Here is another XSD schema in which `sql:hide` is specified on the **\<OD>** element:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:annotation>  
    <xsd:documentation>  
      Sales.Customer-Sales.SalesOrderHeader-Sales.SalesOrderDetail Schema  
      Copyright 2004 Microsoft. All rights reserved.  
    </xsd:documentation>  
    <xsd:appinfo>  
      <sql:relationship name="CustomerOrder"  
         parent="Sales.Customer"  
                  parent-key="CustomerID"  
                  child-key="CustomerID"  
                  child="Sales.SalesOrderHeader" />  
       <sql:relationship name="OrderOrderDetails"  
                  parent="Sales.SalesOrderHeader"  
                  parent-key="SalesOrderID"  
                  child-key="SalesOrderID"  
                  child="Sales.SalesOrderDetail"/>  
    </xsd:appinfo>  
  </xsd:annotation>  
  
  <xsd:element name="Customers" sql:relation="Sales.Customer">  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"   
                     maxOccurs="unbounded"   
                     sql:relationship="CustomerOrder">  
          <xsd:complexType>  
            <xsd:sequence>  
               <xsd:element name="OD" sql:relation="Sales.SalesOrderDetail"                                       maxOccurs="unbounded"                                       sql:relationship="OrderOrderDetails"                                       sql:hide="1">  
                  <xsd:complexType>  
                    <xsd:attribute name="SalesOrderID" type="xsd:string"/>  
                    <xsd:attribute name="ProductID" type="xsd:string"/>  
                  </xsd:complexType>  
               </xsd:element>  
            </xsd:sequence>  
          <xsd:attribute name="CustomerID" type="xsd:string"/>  
          <xsd:attribute name="OID" sql:field="SalesOrderID"   
                                    type="xsd:string"/>  
          <xsd:attribute name="OrderDate" type="xsd:date"/>   
        </xsd:complexType>  
      </xsd:element>  
    </xsd:sequence>  
    <xsd:attribute name="CID" sql:field="CustomerID"   
                                type="xsd:string"/>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="713f3-130">当 `/Customers[@CID="1"]` 针对此架构指定 XPath 查询 (例如) 时，生成的 XML 文档不包含 **\<OD>** 元素及其子级，如下面的部分结果所示：</span><span class="sxs-lookup"><span data-stu-id="713f3-130">When an XPath query (for example `/Customers[@CID="1"]`) is specified against this schema, the XML document that is generated does not include the **\<OD>** element and its children, as shown in this partial result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customers CID="1">  
    <Order CustomerID="1" OID="43860" OrderDate="2001-08-01" />   
    <Order CustomerID="1" OID="44501" OrderDate="2001-11-01" />   
    <Order CustomerID="1" OID="45283" OrderDate="2002-02-01" />   
    <Order CustomerID="1" OID="46042" OrderDate="2002-05-01" />   
  </Customers>  
</ROOT>  
```  
  
  
