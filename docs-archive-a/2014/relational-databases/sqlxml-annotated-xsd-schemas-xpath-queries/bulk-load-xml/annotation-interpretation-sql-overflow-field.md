---
title: sql：溢出-字段 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- overflow-field annotation
- unconsumed data
- overflow data [SQLXML]
- sql:overflow-field
ms.assetid: f005182b-6151-432d-ab22-3bc025742cd3
author: rothja
ms.author: jroth
ms.openlocfilehash: ea52eb642964844a03304d082632c2b7157f723b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588456"
---
# <a name="sqloverflow-field-sqlxml-40"></a><span data-ttu-id="803bf-102">sql:overflow-field (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="803bf-102">sql:overflow-field (SQLXML 4.0)</span></span>
  <span data-ttu-id="803bf-103">在架构中，可以将某列标识为溢出列，以接收 XML 文档中所有未用完的数据。</span><span class="sxs-lookup"><span data-stu-id="803bf-103">In a schema, you can identify a column as an overflow column to receive all unconsumed data from the XML document.</span></span> <span data-ttu-id="803bf-104">通过使用 `sql:overflow-field` 批注在架构中指定此列。</span><span class="sxs-lookup"><span data-stu-id="803bf-104">This column is specified in the schema by using the `sql:overflow-field` annotation.</span></span> <span data-ttu-id="803bf-105">可能有多个溢出列。</span><span class="sxs-lookup"><span data-stu-id="803bf-105">It is possible to have multiple overflow columns.</span></span>  
  
 <span data-ttu-id="803bf-106">一旦有定义了 `sql:overflow-field` 批注的 XML 节点（元素或属性）进入了作用域，溢出列即被激活并会接收未用完的数据。</span><span class="sxs-lookup"><span data-stu-id="803bf-106">Whenever an XML node (element or attribute) for which there is a `sql:overflow-field` annotation defined enters into scope, the overflow column is activated and receives unconsumed data.</span></span> <span data-ttu-id="803bf-107">节点离开作用域时，溢出列将不再活动，XML 大容量加载将激活上一个溢出字段（如果有）。</span><span class="sxs-lookup"><span data-stu-id="803bf-107">When the node goes out of scope, the overflow column is no longer active and XML Bulk Load makes the previous overflow field (if any) active.</span></span>  
  
 <span data-ttu-id="803bf-108">在将数据存储在溢出列中的过程中，XML 大容量加载还会存储定义了 `sql:overflow-field` 的父元素的开始标记和结束标记。</span><span class="sxs-lookup"><span data-stu-id="803bf-108">As it stores data in the overflow column, XML Bulk Load also stores the opening and closing tags of the parent element for which `sql:overflow-field` is defined.</span></span>  
  
 <span data-ttu-id="803bf-109">例如，下面的架构描述了 **\<Customers>** 和 **\<CustOrder>** 元素。</span><span class="sxs-lookup"><span data-stu-id="803bf-109">For example, the following schema describes the **\<Customers>** and **\<CustOrder>** elements.</span></span> <span data-ttu-id="803bf-110">上述每个元素都标识一个溢出列：</span><span class="sxs-lookup"><span data-stu-id="803bf-110">Each of these elements identifies an overflow column:</span></span>  
  
```  
<?xml version="1.0" ?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
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
 <xsd:element name="ROOT" sql:is-constant="1">  
  <xsd:complexType>  
    <xsd:sequence>   
      <xsd:element name="Customers"   
                   sql:relation="Cust"  
                   sql:overflow-field="OverflowColumn">  
        <xsd:complexType>  
             <xsd:sequence>   
             <xsd:element name="CustomerID" type="xsd:integer"/>  
             <xsd:element name="CompanyName"  type="xsd:string"/>  
             <xsd:element name="City" type="xsd:string"/>  
             <xsd:element name="Order"  
                          sql:relation="CustOrder"  
                          sql:relationship="CustCustOrder"  
                          sql:overflow-field="OverflowColumn">  
               <xsd:complexType>  
                 <xsd:attribute name="OrderID"/>  
                 <xsd:attribute name="CustomerID"/>  
               </xsd:complexType>  
             </xsd:element>  
          </xsd:sequence>   
        </xsd:complexType>  
      </xsd:element>  
    </xsd:sequence>  
  </xsd:complexType>  
 </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="803bf-111">在架构中， **\<Customer>** 元素映射到 "参与表" 表， **\<Order>** 元素映射到 CustOrder 表。</span><span class="sxs-lookup"><span data-stu-id="803bf-111">In the schema, the **\<Customer>** element maps to the Cust table and the **\<Order>** element maps to the CustOrder table.</span></span>  
  
 <span data-ttu-id="803bf-112">**\<Customer>** 和元素都 **\<Order>** 标识溢出列。</span><span class="sxs-lookup"><span data-stu-id="803bf-112">Both the **\<Customer>** and **\<Order>** elements identify an overflow column.</span></span> <span data-ttu-id="803bf-113">因此，XML 大容量加载会将元素的所有未用完的子元素和属性保存 **\<Customer>** 在 "参与表" 的 "溢出" 列中，并将元素的所有未用完的子元素和属性保存 **\<Order>** 在 CustOrder 表的溢出列中。</span><span class="sxs-lookup"><span data-stu-id="803bf-113">Thus, XML Bulk Load saves all the unconsumed child elements and attributes of the **\<Customer>** element in the overflow column of the Cust table, and all the unconsumed child elements and attributes of the **\<Order>** element in the overflow column of the CustOrder table.</span></span>  
  
### <a name="to-test-a-working-sample"></a><span data-ttu-id="803bf-114">测试工作示例</span><span class="sxs-lookup"><span data-stu-id="803bf-114">To test a working sample</span></span>  
  
1.  <span data-ttu-id="803bf-115">将在该示例中提供的架构另存为 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="803bf-115">Save the schema that is provided in this example as SampleSchema.xml.</span></span>  
  
2.  <span data-ttu-id="803bf-116">创建以下表：</span><span class="sxs-lookup"><span data-stu-id="803bf-116">Create these tables:</span></span>  
  
    ```  
    CREATE TABLE Cust (  
              CustomerID     int         PRIMARY KEY,  
              CompanyName    varchar(20) NOT NULL,  
              City           varchar(20) DEFAULT 'Seattle',  
              OverflowColumn nvarchar(200))  
    GO  
    CREATE TABLE CustOrder (  
              OrderID        int         PRIMARY KEY,  
              CustomerID     int         FOREIGN KEY REFERENCES  
                                              Cust(CustomerID),  
              OverflowColumn nvarchar(200))  
    GO  
    ```  
  
3.  <span data-ttu-id="803bf-117">将以下示例 XML 数据另存为 SampleXMLData.xml：</span><span class="sxs-lookup"><span data-stu-id="803bf-117">Save the following sample XML data as SampleXMLData.xml:</span></span>  
  
    ```  
    <ROOT>  
      <Customers>  
        <CustomerID>1111</CustomerID>  
        <CompanyName>Hanari Carnes</CompanyName>  
        <City><![CDATA[NY]]> </City>  
          <Junk>garbage in overflow</Junk>  
        <Order OrderID="1" />  
        <Order OrderID="2" />  
     </Customers>  
     <Customers>  
       <CustomerID>1112</CustomerID>  
       <CompanyName>Toms Spezialitten</CompanyName>  
       <City><![CDATA[LA]]> </City>  
       <xyz><address>111 Maple, Seattle</address></xyz>     
       <Order OrderID="3" />  
     </Customers>  
       <Customers>  
       <CustomerID>1113</CustomerID>  
       <CompanyName>Victuailles en stock</CompanyName>  
       <Order OrderID="4" />  
      </Customers>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="803bf-118">若要执行 XML 大容量加载，将此 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) 示例另存为 Sample.vbs 并执行该示例：</span><span class="sxs-lookup"><span data-stu-id="803bf-118">To execute XML Bulk Load, save and execute this [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) example as Sample.vbs:</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
  
