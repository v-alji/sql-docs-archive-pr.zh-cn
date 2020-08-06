---
title: 使用 sql： prefix 创建有效的 ID、IDREF 和 IDREFS 类型属性 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- IDREFS relationships [SQLXML]
- annotated XSD schemas, ID type attribute
- IDREF type attribute [SQLXML]
- annotated XSD schemas, IDREFS type attribute
- ID type attribute [SQLXML]
- sql:prefix
- prefix annotation
- IDREF relationships [SQLXML]
- IDREFS type attribute [SQLXML]
- annotated XSD schemas, IDREF type attribute
- ID relationships [SQLXML]
ms.assetid: 1c7f77d3-81f3-4820-bb63-c4aaa4ea9aa1
author: rothja
ms.author: jroth
ms.openlocfilehash: cb9e63bebd0cebbfeed75ea5cbe2ea62683234fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586601"
---
# <a name="creating-valid-id-idref-and-idrefs-type-attributes-using-sqlprefix-sqlxml-40"></a><span data-ttu-id="faef5-102">使用 sql:prefix 创建有效的 ID、IDREF 和 IDREFS 类型属性 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="faef5-102">Creating Valid ID, IDREF, and IDREFS Type Attributes Using sql:prefix (SQLXML 4.0)</span></span>
  <span data-ttu-id="faef5-103">可以将属性指定为 ID 类型属性。</span><span class="sxs-lookup"><span data-stu-id="faef5-103">An attribute can be specified to be an ID type attribute.</span></span> <span data-ttu-id="faef5-104">然后，可以用指定为 IDREF 或 IDREFS 的属性引用 ID 类型属性，从而启用文档之间的链接。</span><span class="sxs-lookup"><span data-stu-id="faef5-104">Attributes specified as IDREF or IDREFS can then be used to refer to the ID type attributes, enabling links between documents.</span></span>  
  
 <span data-ttu-id="faef5-105">ID、IDREF 和 IDREFS 大体上对应于数据库中的 PK/FK（主键/外键）关系。</span><span class="sxs-lookup"><span data-stu-id="faef5-105">ID, IDREF, and IDREFS correspond to PK/FK (primary key/foreign key) relationships in the database, with few differences.</span></span> <span data-ttu-id="faef5-106">在 XML 文档中，ID 类型属性的值必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="faef5-106">In an XML document, the values of ID type attributes must be distinct.</span></span> <span data-ttu-id="faef5-107">如果在 XML 文档中将**CustomerID**和**订单**ID 属性指定为 ID 类型，则这些值必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="faef5-107">If **CustomerID** and **OrderID** attributes are specified as ID type in an XML document, these values must be distinct.</span></span> <span data-ttu-id="faef5-108">但是，在数据库中，CustomerID 和 OrderID 列可以具有相同值。</span><span class="sxs-lookup"><span data-stu-id="faef5-108">However, in a database, CustomerID and OrderID columns can have the same values.</span></span> <span data-ttu-id="faef5-109">（例如，CustomerID = 1 和 OrderID = 1 在数据库中都是有效的）。</span><span class="sxs-lookup"><span data-stu-id="faef5-109">(For example, CustomerID = 1 and OrderID = 1 are valid in the database).</span></span>  
  
 <span data-ttu-id="faef5-110">若要使 ID、IDREF 和 IDREFS 属性有效：</span><span class="sxs-lookup"><span data-stu-id="faef5-110">For the ID, IDREF, and IDREFS attributes to be valid:</span></span>  
  
-   <span data-ttu-id="faef5-111">ID 的值必须在 XML 文档内是唯一的。</span><span class="sxs-lookup"><span data-stu-id="faef5-111">The value of ID must be unique within the XML document.</span></span>  
  
-   <span data-ttu-id="faef5-112">对于每个 IDREF 和 IDREFS，被引用的 ID 值必须在 XML 文档中。</span><span class="sxs-lookup"><span data-stu-id="faef5-112">For every IDREF and IDREFS, the referenced ID values must be in the XML document.</span></span>  
  
-   <span data-ttu-id="faef5-113">ID、IDREF 和 IDREFS 的值必须是命名标记。</span><span class="sxs-lookup"><span data-stu-id="faef5-113">The value of an ID, IDREF, and IDREFS must be a named token.</span></span> <span data-ttu-id="faef5-114">（例如，整数值 101 不能是 ID 值。）</span><span class="sxs-lookup"><span data-stu-id="faef5-114">(For example, the integer value 101 cannot be an ID value.)</span></span>  
  
-   <span data-ttu-id="faef5-115">ID、IDREF 和 IDREFS 类型的属性不能映射到类型为、或的列，也不能映射到 `text` `ntext` `image` 任何其他二进制数据类型 (例如 `timestamp`) 。</span><span class="sxs-lookup"><span data-stu-id="faef5-115">The attributes of ID, IDREF, and IDREFS type cannot be mapped to columns of the type `text`, `ntext`, or `image` or any other binary data type (for example, `timestamp`).</span></span>  
  
 <span data-ttu-id="faef5-116">如果 XML 文档包含多个 ID，则使用 `sql:prefix` 批注以确保值是唯一的。</span><span class="sxs-lookup"><span data-stu-id="faef5-116">If an XML document contains multiple IDs, use the `sql:prefix` annotation to ensure that the values are unique.</span></span>  
  
 <span data-ttu-id="faef5-117">请注意，`sql:prefix` 批注不能与 XSD 固定属性一起使用。</span><span class="sxs-lookup"><span data-stu-id="faef5-117">Note that `sql:prefix` annotation cannot be used with XSD fixed attribute.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="faef5-118">示例</span><span class="sxs-lookup"><span data-stu-id="faef5-118">Examples</span></span>  
 <span data-ttu-id="faef5-119">若要创建使用以下示例的工作示例，必须满足某些要求。</span><span class="sxs-lookup"><span data-stu-id="faef5-119">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="faef5-120">有关详细信息，请参阅[运行 SQLXML 示例的要求](../sqlxml/requirements-for-running-sqlxml-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="faef5-120">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-id-and-idrefs-types"></a><span data-ttu-id="faef5-121">A.</span><span class="sxs-lookup"><span data-stu-id="faef5-121">A.</span></span> <span data-ttu-id="faef5-122">指定 ID 和 IDREFS 类型</span><span class="sxs-lookup"><span data-stu-id="faef5-122">Specifying ID and IDREFS types</span></span>  
 <span data-ttu-id="faef5-123">在下面的架构中， **\<Customer>** 元素由 **\<Order>** 子元素组成。</span><span class="sxs-lookup"><span data-stu-id="faef5-123">In the following schema, the **\<Customer>** element consists of the **\<Order>** child element.</span></span> <span data-ttu-id="faef5-124">**\<Order>** 元素还有一个子元素，即 **\<OrderDetail>** 元素。</span><span class="sxs-lookup"><span data-stu-id="faef5-124">The **\<Order>** element also has a child element, the **\<OrderDetail>** element.</span></span>  
  
 <span data-ttu-id="faef5-125">的**OrderIDList**属性 **\<Customer>** 是一个 IDREFS 类型属性，该属性引用元素的 "**订单 id** " 属性 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="faef5-125">The **OrderIDList** attribute of **\<Customer>** is an IDREFS type attribute that refers to the **OrderID** attribute of the **\<Order>** element.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
                 parent="Sales.Customer"  
                 parent-key="CustomerID"  
                 child="Sales.SalesOrderHeader"  
                 child-key="CustomerID" />  
    <sql:relationship name="OrderOrderDetail"  
                 parent="Sales.SalesOrderHeader"  
                 parent-key="SalesOrderID"  
                 child="Sales.SalesOrderDetail"  
                 child-key="SalesOrderID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"    
               sql:relationship="CustOrders" maxOccurs="unbounded" >  
          <xsd:complexType>  
              <xsd:sequence>  
                <xsd:element name="OrderDetail"   
                             sql:relation="Sales.SalesOrderDetail"   
                   sql:relationship="OrderOrderDetail"   
                   maxOccurs="unbounded" >  
                  <xsd:complexType>  
                   <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                   <xsd:attribute name="ProductID" type="xsd:string" />  
                   <xsd:attribute name="OrderQty" type="xsd:integer" />  
                  </xsd:complexType>  
               </xsd:element>  
             </xsd:sequence>  
             <xsd:attribute name="SalesOrderID"   
                            type="xsd:ID" sql:prefix="ord-" />  
             <xsd:attribute name="OrderDate" type="xsd:date" />  
             <xsd:attribute name="CustomerID" type="xsd:string" />  
          </xsd:complexType>  
      </xsd:element>  
    </xsd:sequence>  
    <xsd:attribute name="CustomerID" type="xsd:string" />  
    <xsd:attribute name="OrderIDList" type="xsd:IDREFS"   
                   sql:relation="Sales.SalesOrderHeader" sql:field="SalesOrderID"  
                   sql:relationship="CustOrders" sql:prefix="ord-">  
    </xsd:attribute>  
  </xsd:complexType>  
</xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="faef5-126">针对架构测试示例 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="faef5-126">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="faef5-127">复制上面的架构代码，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="faef5-127">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="faef5-128">将该文件另存为 sqlPrefix.xml。</span><span class="sxs-lookup"><span data-stu-id="faef5-128">Save the file as sqlPrefix.xml.</span></span>  
  
2.  <span data-ttu-id="faef5-129">复制以下模板，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="faef5-129">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="faef5-130">在保存 sqlPrefix.xml 的相同目录中将该文件另存为 sqlPrefixT.xml。</span><span class="sxs-lookup"><span data-stu-id="faef5-130">Save the file as sqlPrefixT.xml in the same directory where you saved sqlPrefix.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="sqlPrefix.xml">  
        /Customer[@CustomerID=1]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="faef5-131">为映射架构 (sqlPrefix.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="faef5-131">The directory path specified for the mapping schema (sqlPrefix.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="faef5-132">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="faef5-132">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\sqlPrefix.xml"  
    ```  
  
3.  <span data-ttu-id="faef5-133">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="faef5-133">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="faef5-134">有关详细信息，请参阅[使用 ADO 执行 SQLXML 查询](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="faef5-134">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="faef5-135">下面是部分结果：</span><span class="sxs-lookup"><span data-stu-id="faef5-135">This is the partial result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="1" OrderIDList="ord-43860 ord-44501 ord-45283 ord-46042">  
    <Order SalesOrderID="ord-43860" OrderDate="2001-08-01" CustomerID="1">  
      <OrderDetail SalesOrderID="43860" ProductID="729" OrderQty="1" />   
      <OrderDetail SalesOrderID="43860" ProductID="732" OrderQty="1" />   
      <OrderDetail SalesOrderID="43860" ProductID="738" OrderQty="1" />   
      <OrderDetail SalesOrderID="43860" ProductID="753" OrderQty="2" />   
      ...  
    </Order>  
    ...  
 </Customer>  
</ROOT>  
```  
  
  
