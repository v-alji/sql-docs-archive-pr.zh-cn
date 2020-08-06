---
title: 使用 sql 创建常量元素：是常量 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- element does not map [SQLXML]
- sql:is-constant
- XSD schemas [SQLXML], constant elements
- element mapping [SQLXML], constant elements
- is-constant annotation
- constant elements [SQLXML]
- annotated XSD schemas, constant elements
ms.assetid: 940eea1b-54f5-445f-b844-c894d9f3941b
author: rothja
ms.author: jroth
ms.openlocfilehash: 8deedd8547d6bc3f0154eedb889ad908750f071a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690437"
---
# <a name="creating-constant-elements-using-sqlis-constant-sqlxml-40"></a><span data-ttu-id="82f87-102">使用 sql:is-constant 创建常量元素 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="82f87-102">Creating Constant Elements Using sql:is-constant (SQLXML 4.0)</span></span>
  <span data-ttu-id="82f87-103">若要指定常量元素，即 XSD 架构中未映射到任何数据库表或列的元素-可以使用 `sql:is-constant` 批注。</span><span class="sxs-lookup"><span data-stu-id="82f87-103">To specify a constant element-that is, an element in the XSD schema that does not map to any database table or column-you can use the `sql:is-constant` annotation.</span></span> <span data-ttu-id="82f87-104">该批注取布尔值（0 = false，1 = true）。</span><span class="sxs-lookup"><span data-stu-id="82f87-104">This annotation takes a Boolean value (0 = false, 1 = true).</span></span> <span data-ttu-id="82f87-105">可接受的值为 0、1、true 和 false。</span><span class="sxs-lookup"><span data-stu-id="82f87-105">The acceptable values are 0, 1, true, and false.</span></span> <span data-ttu-id="82f87-106">可以在不具有任何属性的元素中指定 `sql:is-constant` 批注。</span><span class="sxs-lookup"><span data-stu-id="82f87-106">The `sql:is-constant` annotation can be specified on an element that does not have any attributes.</span></span> <span data-ttu-id="82f87-107">如果使用值 true（或 1）在元素中指定该批注，则该元素不会被映射到数据库，但仍出现在 XML 文档中。</span><span class="sxs-lookup"><span data-stu-id="82f87-107">If it is specified on an element with the value true (or 1), that element is not mapped to the database but still appears in the XML document.</span></span>  
  
 <span data-ttu-id="82f87-108">`sql:is-constant` 批注可以用于以下操作：</span><span class="sxs-lookup"><span data-stu-id="82f87-108">The `sql:is-constant` annotation can be used for:</span></span>  
  
-   <span data-ttu-id="82f87-109">将顶级元素添加到 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="82f87-109">Adding a top-level element to the XML document.</span></span> <span data-ttu-id="82f87-110">XML 要求为文档提供一个顶级元素（根元素）。</span><span class="sxs-lookup"><span data-stu-id="82f87-110">XML requires a single top-level element (root element) for the document.</span></span>  
  
-   <span data-ttu-id="82f87-111">创建容器元素，例如 **\<Orders>** 包装所有订单的元素。</span><span class="sxs-lookup"><span data-stu-id="82f87-111">Creating container elements, such as an **\<Orders>** element that wraps all orders.</span></span>  
  
 <span data-ttu-id="82f87-112">`sql:is-constant`批注可以添加到 **\<complexType>** 元素。</span><span class="sxs-lookup"><span data-stu-id="82f87-112">The `sql:is-constant` annotation can be added to a **\<complexType>** element.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="82f87-113">示例</span><span class="sxs-lookup"><span data-stu-id="82f87-113">Examples</span></span>  
 <span data-ttu-id="82f87-114">若要创建使用以下示例的工作示例，必须满足某些要求。</span><span class="sxs-lookup"><span data-stu-id="82f87-114">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="82f87-115">有关详细信息，请参阅[运行 SQLXML 示例的要求](../sqlxml/requirements-for-running-sqlxml-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="82f87-115">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-sqlis-constant-to-add-a-container-element"></a><span data-ttu-id="82f87-116">A.</span><span class="sxs-lookup"><span data-stu-id="82f87-116">A.</span></span> <span data-ttu-id="82f87-117">指定 sql:is-constant 以添加容器元素</span><span class="sxs-lookup"><span data-stu-id="82f87-117">Specifying sql:is-constant to add a container element</span></span>  
 <span data-ttu-id="82f87-118">在此带批注的 XSD 架构中， **\<CustomerOrders>** 通过指定值为1的属性，将定义为常量元素 `sql:is-constant` 。</span><span class="sxs-lookup"><span data-stu-id="82f87-118">In this annotated XSD schema, **\<CustomerOrders>** is defined as a constant element by specifying the `sql:is-constant` attribute with a value of 1.</span></span> <span data-ttu-id="82f87-119">因此， **\<CustomerOrders>** 不会映射到任何数据库表或列。</span><span class="sxs-lookup"><span data-stu-id="82f87-119">Therefore, **\<CustomerOrders>** is not mapped to any database table or column.</span></span> <span data-ttu-id="82f87-120">此常量元素由 **\<Order>** 子元素组成。</span><span class="sxs-lookup"><span data-stu-id="82f87-120">This constant element consists of the **\<Order>** child elements.</span></span>  
  
 <span data-ttu-id="82f87-121">尽管不 **\<CustomerOrders>** 会映射到任何数据库表或列，但它仍将作为包含子元素的容器元素出现在生成的 XML 中 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="82f87-121">Although **\<CustomerOrders>** does not map to any database table or column, it still appears in the resulting XML as a container element containing the **\<Order>** child elements.</span></span>  
  
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
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="CustomerOrders" sql:is-constant="1" >  
          <xsd:complexType>  
            <xsd:sequence>  
              <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"  
                           sql:relationship="CustOrders"   
                           maxOccurs="unbounded" >  
                <xsd:complexType>  
                   <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                   <xsd:attribute name="OrderDate" type="xsd:date" />  
                   <xsd:attribute name="CustomerID" type="xsd:string" />  
                </xsd:complexType>  
              </xsd:element>  
            </xsd:sequence>  
           </xsd:complexType>  
          </xsd:element>  
         </xsd:sequence>  
          <xsd:attribute name="CustomerID" type="xsd:string" />  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="82f87-122">针对架构测试示例 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="82f87-122">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="82f87-123">复制上面的架构代码，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="82f87-123">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="82f87-124">将该文件另存为 isConstant.xml。</span><span class="sxs-lookup"><span data-stu-id="82f87-124">Save the file as isConstant.xml.</span></span>  
  
2.  <span data-ttu-id="82f87-125">复制以下模板，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="82f87-125">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="82f87-126">在保存 isConstant.xml 的同一目录中将该文件另存为 isConstantT.xml。</span><span class="sxs-lookup"><span data-stu-id="82f87-126">Save the file as isConstantT.xml in the same directory where you saved isConstant.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="isConstant.xml">  
            Customer[@CustomerID=1]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="82f87-127">为映射架构 (isConstant.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="82f87-127">The directory path specified for the mapping schema (isConstant.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="82f87-128">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="82f87-128">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\isConstant.xml"  
    ```  
  
3.  <span data-ttu-id="82f87-129">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="82f87-129">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="82f87-130">有关详细信息，请参阅[使用 ADO 执行 SQLXML 查询](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="82f87-130">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="82f87-131">部分结果集如下：</span><span class="sxs-lookup"><span data-stu-id="82f87-131">This is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
<Customer CustomerID="1">   
  <CustomerOrders>   
    <Order SalesOrderID="43860" OrderDate="2001-08-01" CustomerID="1" />   
    <Order SalesOrderID="44501" OrderDate="2001-11-01" CustomerID="1" />   
    <Order SalesOrderID="45283" OrderDate="2002-02-01" CustomerID="1" />   
    <Order SalesOrderID="46042" OrderDate="2002-05-01" CustomerID="1" />   
    ...  
  </CustomerOrders>   
</Customer>   
</ROOT>  
```  
  
  
