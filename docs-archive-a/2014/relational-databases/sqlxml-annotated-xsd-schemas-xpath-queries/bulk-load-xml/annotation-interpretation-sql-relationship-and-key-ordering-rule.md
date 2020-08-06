---
title: sql：关系和键排序规则 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:relationship
- key ordering rules [SQLXML]
- relationship annotation
ms.assetid: 914cb152-09f5-4b08-b35d-71940e4e9986
author: rothja
ms.author: jroth
ms.openlocfilehash: 716e911676dc81539fc641bee139d92e29dc49db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588454"
---
# <a name="sqlrelationship-and-the-key-ordering-rule-sqlxml-40"></a><span data-ttu-id="9623d-102">sql:relationship 和键排序规则 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="9623d-102">sql:relationship and the Key Ordering Rule (SQLXML 4.0)</span></span>
  <span data-ttu-id="9623d-103">由于 XML 大容量加载在其节点进入作用域时会生成记录，并在其节点退出作用域时会将这些记录发送到 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，因此，有关记录的数据必须存在于节点的作用域中。</span><span class="sxs-lookup"><span data-stu-id="9623d-103">Because XML Bulk Load generates records as their nodes enter into scope and sends those records to Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as their nodes exit scope, the data for the record must be present within the scope of the node.</span></span>  
  
 <span data-ttu-id="9623d-104">请考虑下面的 XSD 架构，其中，和元素之间的一对多关系 **\<Customer>** **\<Order>** (一个客户可以将多个订单) 使用 `<sql:relationship>` 元素指定：</span><span class="sxs-lookup"><span data-stu-id="9623d-104">Consider the following XSD schema, in which the one-to-many relationship between **\<Customer>** and **\<Order>** elements (one customer can place many orders) is specified by using the `<sql:relationship>` element:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"<>   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustCustOrder"  
          parent="Cust"  
          parent-key="CustomerID"  
          child="CustOrder"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customers" sql:relation="Cust" >  
   <xsd:complexType>  
     <xsd:sequence>  
       <xsd:element name="CustomerID"  type="xsd:integer" />  
       <xsd:element name="CompanyName" type="xsd:string" />  
       <xsd:element name="City"        type="xsd:string" />  
       <xsd:element name="Order"   
                          sql:relation="CustOrder"  
                          sql:relationship="CustCustOrder" >  
         <xsd:complexType>  
          <xsd:attribute name="OrderID" type="xsd:integer" />  
         </xsd:complexType>  
       </xsd:element>  
     </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="9623d-105">当 **\<Customer>** 元素节点进入作用域时，XML 大容量加载将生成一个客户记录。</span><span class="sxs-lookup"><span data-stu-id="9623d-105">As the **\<Customer>** element node enters into scope, XML Bulk Load generates a customer record.</span></span> <span data-ttu-id="9623d-106">此记录一直保持到 XML 大容量加载读取 **\</Customer>** 。</span><span class="sxs-lookup"><span data-stu-id="9623d-106">This record stays until XML Bulk Load reads **\</Customer>**.</span></span> <span data-ttu-id="9623d-107">在处理 **\<Order>** 元素节点时，XML 大容量加载使用 `<sql:relationship>` 从父元素中获取 CustOrder 表的 CustomerID 外键列的值 **\<Customer>** ，因为该 **\<Order>** 元素未指定**customerid**属性。</span><span class="sxs-lookup"><span data-stu-id="9623d-107">In processing the **\<Order>** element node, XML Bulk Load uses `<sql:relationship>` to obtain the value of the CustomerID foreign key column of the CustOrder table from the **\<Customer>** parent element, because the **\<Order>** element does not specify the **CustomerID** attribute.</span></span> <span data-ttu-id="9623d-108">这意味着在定义 **\<Customer>** 元素时，必须在指定之前在架构中指定**CustomerID**属性 `<sql:relationship>` 。</span><span class="sxs-lookup"><span data-stu-id="9623d-108">This means that in defining the **\<Customer>** element, you must specify the **CustomerID** attribute in the schema before you specify `<sql:relationship>`.</span></span> <span data-ttu-id="9623d-109">否则，当 **\<Order>** 元素进入作用域时，Xml 大容量加载为 CustOrder 表生成一条记录，并且当 XML 大容量加载到达 **\</Order>** 结束标记时，它会将该记录发送到， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 而不会出现 CustomerID 外键列值。</span><span class="sxs-lookup"><span data-stu-id="9623d-109">Otherwise, when an **\<Order>** element enters into scope, XML Bulk Load generates a record for the CustOrder table, and when the XML Bulk Load reaches the **\</Order>** end tag, it sends the record to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] without the CustomerID foreign key column value.</span></span>  
  
 <span data-ttu-id="9623d-110">将在该示例中提供的架构另存为 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="9623d-110">Save the schema that is provided in this example as SampleSchema.xml.</span></span>  
  
### <a name="to-test-a-working-sample"></a><span data-ttu-id="9623d-111">测试工作示例</span><span class="sxs-lookup"><span data-stu-id="9623d-111">To test a working sample</span></span>  
  
1.  <span data-ttu-id="9623d-112">创建以下表：</span><span class="sxs-lookup"><span data-stu-id="9623d-112">Create these tables:</span></span>  
  
    ```  
    CREATE TABLE Cust (  
                  CustomerID     int          PRIMARY KEY,  
               CompanyName    varchar(20)  NOT NULL,  
                  City           varchar(20)  DEFAULT 'Seattle')  
    GO  
    CREATE TABLE CustOrder (  
                  OrderID        varchar(10) PRIMARY KEY,  
               CustomerID     int         FOREIGN KEY REFERENCES                                          Cust(CustomerID))  
    GO  
    ```  
  
2.  <span data-ttu-id="9623d-113">将下面的示例数据另存为 SampleXMLData.xml：</span><span class="sxs-lookup"><span data-stu-id="9623d-113">Save the following sample data as SampleXMLData.xml:</span></span>  
  
    ```  
    <ROOT>    
      <Customers>  
        <CompanyName>Hanari Carnes</CompanyName>  
        <City>NY</City>  
        <Order OrderID="1" />  
        <Order OrderID="2" />  
        <CustomerID>1111</CustomerID>  
      </Customers>  
      <Customers>  
        <CompanyName>Toms Spezialitten</CompanyName>  
         <City>LA</City>    
        <Order OrderID="3" />  
        <CustomerID>1112</CustomerID>  
      </Customers>  
      <Customers>  
        <CompanyName>Victuailles en stock</CompanyName>  
        <Order OrderID="4" />  
        <CustomerID>1113</CustomerID>  
      </Customers>  
    </ROOT>  
    ```  
  
3.  <span data-ttu-id="9623d-114">若要执行 XML 大容量加载，请将下面的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) 示例另存为 MySample.vbs，并执行它：</span><span class="sxs-lookup"><span data-stu-id="9623d-114">To execute XML Bulk Load, save and execute the following [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) example as MySample.vbs:</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Transaction=True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
     <span data-ttu-id="9623d-115">结果是 XML 大容量加载在 CustOrder 表的 CustomerID 外键列中插入一个 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="9623d-115">The result is that XML Bulk Load inserts a NULL value in the CustomerID foreign key column of the CustOrder table.</span></span> <span data-ttu-id="9623d-116">如果修改 XML 示例数据，使 **\<CustomerID>** 子元素出现在 **\<Order>** 子元素之前，则会获得预期结果： XML 大容量加载将指定的外键值插入到列中。</span><span class="sxs-lookup"><span data-stu-id="9623d-116">If you revise the XML sample data so that the **\<CustomerID>** child element appears before the **\<Order>** child element, you get the expected result: XML Bulk Load inserts the specified foreign key value into the column.</span></span>  
  
 <span data-ttu-id="9623d-117">这是等效的 XDR 架构：</span><span class="sxs-lookup"><span data-stu-id="9623d-117">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >   
   <ElementType name="CustomerID"  />  
   <ElementType name="CompanyName" />  
   <ElementType name="City"        />  
  
   <ElementType name="root" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust" >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
      <element type="Order" >  
                 <sql:relationship  
                        key-relation    ="Cust"  
                        key             ="CustomerID"  
                        foreign-key     ="CustomerID"  
                        foreign-relation="CustOrder" />  
      </element>  
   </ElementType>  
    <ElementType name="Order" sql:relation="CustOrder" >  
      <AttributeType name="OrderID" />  
      <AttributeType name="CustomerID" />  
      <attribute type="OrderID" />  
      <attribute type="CustomerID" />  
    </ElementType>  
</Schema>  
```  
  
  
