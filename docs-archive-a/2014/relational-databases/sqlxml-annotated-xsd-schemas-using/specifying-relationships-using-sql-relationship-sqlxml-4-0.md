---
title: 使用 sql： relationship 指定关系 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- IDREFS relationships [SQLXML]
- parent attribute [SQLXML]
- element relationships [SQLXML]
- multiple element relationships
- attribute relationships [SQLXML]
- sql:relationship
- relationship chains [SQLXML]
- IDREF relationships [SQLXML]
- parent-child relationships [SQLXML]
- relationship annotation
- XSD schemas [SQLXML], relationships
- annotated XSD schemas, relationships
- relationships [SQLXML], specifying
- unnamed relationships
- ID relationships [SQLXML]
- hierarchical relationships [SQLXML]
- named relationships [SQLXML]
ms.assetid: 98820afa-74e1-4e62-b336-6111a3dede4c
author: rothja
ms.author: jroth
ms.openlocfilehash: 42c703de9d564580eb0baa1349a45b193109c87a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586597"
---
# <a name="specifying-relationships-using-sqlrelationship-sqlxml-40"></a><span data-ttu-id="412fc-102">使用 sql:relationship 指定关系 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="412fc-102">Specifying Relationships Using sql:relationship (SQLXML 4.0)</span></span>
  <span data-ttu-id="412fc-103">可以对 XML 文档中的元素建立相关性。</span><span class="sxs-lookup"><span data-stu-id="412fc-103">The elements in an XML document can be related.</span></span> <span data-ttu-id="412fc-104">元素可以按层次结构方式嵌套，并且可以在元素之间指定 ID、IDREF 或 IDREFS 关系。</span><span class="sxs-lookup"><span data-stu-id="412fc-104">The elements can be nested hierarchically, and ID, IDREF, or IDREFS relationships can be specified between the elements.</span></span>  
  
 <span data-ttu-id="412fc-105">例如，在 XSD 架构中， **\<Customer>** 元素包含 **\<Order>** 子元素。</span><span class="sxs-lookup"><span data-stu-id="412fc-105">For example, in an XSD schema, a **\<Customer>** element contains **\<Order>** child elements.</span></span> <span data-ttu-id="412fc-106">将架构映射到 AdventureWorks 数据库后， **\<Customer>** 元素映射到 Customer 表， **\<Order>** 元素映射到 SalesOrderHeader 表。</span><span class="sxs-lookup"><span data-stu-id="412fc-106">When the schema is mapped to the AdventureWorks database, the **\<Customer>** element maps to the Sales.Customer table and the **\<Order>** element maps to the Sales.SalesOrderHeader table.</span></span> <span data-ttu-id="412fc-107">由于是由客户下订单，因此，基础表 Sales.Customer 和 Sales.SalesOrderHeader 是相关的。</span><span class="sxs-lookup"><span data-stu-id="412fc-107">These underlying tables, Sales.Customer and Sales.SalesOrderHeader, are related because customers place orders.</span></span> <span data-ttu-id="412fc-108">Sales.SalesOrderHeader 表中的 CustomerID 是外键，它引用 Sales.Customer 表中的 CustomerID 主键。</span><span class="sxs-lookup"><span data-stu-id="412fc-108">The CustomerID in the Sales.SalesOrderHeader table is a foreign key referring to the CustomerID primary key in the Sales.Customer table.</span></span> <span data-ttu-id="412fc-109">可以通过使用批注在映射架构元素之间建立这些关系 `sql:relationship` 。</span><span class="sxs-lookup"><span data-stu-id="412fc-109">You can establish these relationships among mapping schema elements by using the `sql:relationship` annotation.</span></span>  
  
 <span data-ttu-id="412fc-110">在带批注的 XSD 架构中，`sql:relationship` 批注用于根据元素所映射到的各基础表之间的主键和外键关系，按层次结构方式嵌套架构元素。</span><span class="sxs-lookup"><span data-stu-id="412fc-110">In the annotated XSD schema, the `sql:relationship` annotation is used to nest the schema elements hierarchically, on the basis of primary key and foreign key relationships among the underlying tables to which the elements map.</span></span> <span data-ttu-id="412fc-111">在指定 `sql:relationship` 批注时，必须标识以下内容：</span><span class="sxs-lookup"><span data-stu-id="412fc-111">In specifying the `sql:relationship` annotation, you must identify the following:</span></span>  
  
-   <span data-ttu-id="412fc-112">父表 (Sales.Customer) 和子表 (Sales.SalesOrderHeader)。</span><span class="sxs-lookup"><span data-stu-id="412fc-112">The parent table (Sales.Customer) and the child table (Sales.SalesOrderHeader).</span></span>  
  
-   <span data-ttu-id="412fc-113">组成父表与子表间关系的一列或多列。</span><span class="sxs-lookup"><span data-stu-id="412fc-113">The column or columns that compose the relationship between the parent and child tables.</span></span> <span data-ttu-id="412fc-114">例如，CustomerID 列，该列同时出现在父表和子表中。</span><span class="sxs-lookup"><span data-stu-id="412fc-114">For example, the CustomerID column, which appears in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="412fc-115">此信息用于生成适当的层次结构。</span><span class="sxs-lookup"><span data-stu-id="412fc-115">This information is used to generate the proper hierarchy.</span></span>  
  
 <span data-ttu-id="412fc-116">为了提供表名和必需的联接信息，应针对 `sql:relationship` 批注指定以下属性。</span><span class="sxs-lookup"><span data-stu-id="412fc-116">To provide the table names and the necessary join information, the following attributes are specified on the `sql:relationship` annotation.</span></span> <span data-ttu-id="412fc-117">这些属性仅对于 **\<sql:relationship>** 元素有效：</span><span class="sxs-lookup"><span data-stu-id="412fc-117">These attributes are valid only with the **\<sql:relationship>** element:</span></span>  
  
 <span data-ttu-id="412fc-118">**名称**</span><span class="sxs-lookup"><span data-stu-id="412fc-118">**Name**</span></span>  
 <span data-ttu-id="412fc-119">指定关系的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="412fc-119">Specifies the unique name of the relationship.</span></span>  
  
 <span data-ttu-id="412fc-120">**Parent**</span><span class="sxs-lookup"><span data-stu-id="412fc-120">**Parent**</span></span>  
 <span data-ttu-id="412fc-121">指定父关系（表）。</span><span class="sxs-lookup"><span data-stu-id="412fc-121">Specifies the parent relation (table).</span></span> <span data-ttu-id="412fc-122">这是一个可选属性；如果未指定此属性，将从文档的子层次结构中的信息获得父表名称。</span><span class="sxs-lookup"><span data-stu-id="412fc-122">This is an optional attribute; if the attribute is not specified, the parent table name is obtained from information in the child hierarchy in the document.</span></span> <span data-ttu-id="412fc-123">如果架构指定了两个父子层次结构，它们使用相同 **\<sql:relationship>** 但不同的父元素，则不在中指定父属性 **\<sql:relationship>** 。</span><span class="sxs-lookup"><span data-stu-id="412fc-123">If the schema specifies two parent-child hierarchies that use the same **\<sql:relationship>** but different parent elements, you do not specify the parent attribute in **\<sql:relationship>**.</span></span> <span data-ttu-id="412fc-124">此信息将从架构的层次结构中获得。</span><span class="sxs-lookup"><span data-stu-id="412fc-124">This information is obtained from the hierarchy in the schema.</span></span>  
  
 <span data-ttu-id="412fc-125">**parent-key**</span><span class="sxs-lookup"><span data-stu-id="412fc-125">**parent-key**</span></span>  
 <span data-ttu-id="412fc-126">指定父项的父键。</span><span class="sxs-lookup"><span data-stu-id="412fc-126">Specifies the parent key of the parent.</span></span> <span data-ttu-id="412fc-127">如果父键由多列组成，则指定值时应在各值之间使用空格。</span><span class="sxs-lookup"><span data-stu-id="412fc-127">If the parent key is composed of multiple columns, values are specified with a space between them.</span></span> <span data-ttu-id="412fc-128">在为多列键指定的值与为对应的子键指定的值之间存在位置映射。</span><span class="sxs-lookup"><span data-stu-id="412fc-128">There is a positional mapping between the values that are specified for the multicolumn key and for the corresponding child key.</span></span>  
  
 <span data-ttu-id="412fc-129">**子代**</span><span class="sxs-lookup"><span data-stu-id="412fc-129">**Child**</span></span>  
 <span data-ttu-id="412fc-130">指定子关系（表）。</span><span class="sxs-lookup"><span data-stu-id="412fc-130">Specifies the child relation (table).</span></span>  
  
 <span data-ttu-id="412fc-131">**child-key**</span><span class="sxs-lookup"><span data-stu-id="412fc-131">**child-key**</span></span>  
 <span data-ttu-id="412fc-132">在引用父项中父键的子项中指定子键。</span><span class="sxs-lookup"><span data-stu-id="412fc-132">Specifies the child key in the child referring to parent-key in parent.</span></span> <span data-ttu-id="412fc-133">如果子键由多个属性（列）组成，则指定子键值时应在各值之间使用空格。</span><span class="sxs-lookup"><span data-stu-id="412fc-133">If the child key is composed of multiple attributes (columns), the child-key values are specified with a space between them.</span></span> <span data-ttu-id="412fc-134">在为多列键指定的值与为对应的父键指定的值之间存在位置映射。</span><span class="sxs-lookup"><span data-stu-id="412fc-134">There is a positional mapping between the values that are specified for the multicolumn key and for the corresponding parent key.</span></span>  
  
 <span data-ttu-id="412fc-135">**反转**</span><span class="sxs-lookup"><span data-stu-id="412fc-135">**Inverse**</span></span>  
 <span data-ttu-id="412fc-136">此上指定的属性 **\<sql:relationship>** 由 updategram 使用。</span><span class="sxs-lookup"><span data-stu-id="412fc-136">This attribute specified on **\<sql:relationship>** is used by updategrams.</span></span> <span data-ttu-id="412fc-137">有关详细信息，请参阅[在 sql： relationship 上指定 sql：反向特性](specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="412fc-137">For more information, see [Specifying the sql:inverse Attribute on sql:relationship](specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="412fc-138">`sql:key-fields`必须在包含子元素的元素中指定批注，该元素具有在 **\<sql:relationship>** 元素和子元素之间定义的，并且不提供父元素中指定的表的主键。</span><span class="sxs-lookup"><span data-stu-id="412fc-138">The `sql:key-fields` annotation must be specified in an element that contains a child element, that has a **\<sql:relationship>** defined between the element and the child, and that does not provide the primary key of the table specified in the parent element.</span></span> <span data-ttu-id="412fc-139">即使架构未指定 **\<sql:relationship>** ，也必须指定 `sql:key-fields` 来生成适当的层次结构。</span><span class="sxs-lookup"><span data-stu-id="412fc-139">Even if the schema does not specify **\<sql:relationship>**, you must specify `sql:key-fields` to produce the proper hierarchy.</span></span> <span data-ttu-id="412fc-140">有关详细信息，请参阅[使用 sql： key-字段标识键列](identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="412fc-140">For more information, see [Identifying Key Columns by Using sql:key-fields](identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="412fc-141">为了在结果中生成适当的嵌套，建议在所有架构中指定 `sql:key-fields`。</span><span class="sxs-lookup"><span data-stu-id="412fc-141">To produce proper nesting in the result, it is recommended that `sql:key-fields` are specified in all schemas.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="412fc-142">示例</span><span class="sxs-lookup"><span data-stu-id="412fc-142">Examples</span></span>  
 <span data-ttu-id="412fc-143">若要创建使用以下示例的工作示例，必须满足某些要求。</span><span class="sxs-lookup"><span data-stu-id="412fc-143">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="412fc-144">有关详细信息，请参阅[运行 SQLXML 示例的要求](../sqlxml/requirements-for-running-sqlxml-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="412fc-144">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-the-sqlrelationship-annotation-on-an-element"></a><span data-ttu-id="412fc-145">A.</span><span class="sxs-lookup"><span data-stu-id="412fc-145">A.</span></span> <span data-ttu-id="412fc-146">针对元素指定 sql:relationship 批注</span><span class="sxs-lookup"><span data-stu-id="412fc-146">Specifying the sql:relationship annotation on an element</span></span>  
 <span data-ttu-id="412fc-147">以下带批注的 XSD 架构包含 **\<Customer>** 和 **\<Order>** 元素。</span><span class="sxs-lookup"><span data-stu-id="412fc-147">The following annotated XSD schema includes **\<Customer>** and **\<Order>** elements.</span></span> <span data-ttu-id="412fc-148">**\<Order>** 元素是元素的子元素 **\<Customer>** 。</span><span class="sxs-lookup"><span data-stu-id="412fc-148">The **\<Order>** element is a child element of the **\<Customer>** element.</span></span>  
  
 <span data-ttu-id="412fc-149">在架构中，在 `sql:relationship` 子元素上指定批注 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="412fc-149">In the schema, the `sql:relationship` annotation is specified on the **\<Order>** child element.</span></span> <span data-ttu-id="412fc-150">关系本身是在元素中定义的 **\<xsd:appinfo>** 。</span><span class="sxs-lookup"><span data-stu-id="412fc-150">The relationship itself is defined in the **\<xsd:appinfo>** element.</span></span>  
  
 <span data-ttu-id="412fc-151">**\<relationship>** 元素将 SalesOrderHeader 表中的 CustomerID 标识为一个外键，该外键引用 Customer 表中的 customerid 主键。</span><span class="sxs-lookup"><span data-stu-id="412fc-151">The **\<relationship>** element identifies CustomerID in the Sales.SalesOrderHeader table as a foreign key that refers to the CustomerID primary key in the Sales.Customer table.</span></span> <span data-ttu-id="412fc-152">因此，属于某个客户的订单将显示为该元素的子元素 **\<Customer>** 。</span><span class="sxs-lookup"><span data-stu-id="412fc-152">Therefore, orders that belong to a customer appear as a child element of that **\<Customer>** element.</span></span>  
  
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
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" type="CustomerType" />  
   <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                    sql:relationship="CustOrders" >  
           <xsd:complexType>  
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
           </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
    </xsd:complexType>  
  
</xsd:schema>  
```  
  
 <span data-ttu-id="412fc-153">前一个架构使用命名关系。</span><span class="sxs-lookup"><span data-stu-id="412fc-153">The previous schema uses a named relationship.</span></span> <span data-ttu-id="412fc-154">还可以指定未命名关系。</span><span class="sxs-lookup"><span data-stu-id="412fc-154">You can also specify an unnamed relationship.</span></span> <span data-ttu-id="412fc-155">结果是相同的。</span><span class="sxs-lookup"><span data-stu-id="412fc-155">The results are same.</span></span>  
  
 <span data-ttu-id="412fc-156">这是一个经修订的架构，在其中指定未命名关系：</span><span class="sxs-lookup"><span data-stu-id="412fc-156">This is the revised schema in which an unnamed relationship is specified:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer"  type="CustomerType" />  
   <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader">  
           <xsd:annotation>  
            <xsd:appinfo>  
              <sql:relationship   
                parent="Sales.Customer"  
                parent-key="CustomerID"  
                child="Sales.SalesOrderHeader"  
                child-key="CustomerID" />  
            </xsd:appinfo>  
           </xsd:annotation>  
           <xsd:complexType>  
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
           </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
    </xsd:complexType>  
  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="412fc-157">针对架构测试示例 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="412fc-157">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="412fc-158">复制上面的架构代码，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="412fc-158">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="412fc-159">将文件另存为 sql-relationship.xml。</span><span class="sxs-lookup"><span data-stu-id="412fc-159">Save the file as sql-relationship.xml.</span></span>  
  
2.  <span data-ttu-id="412fc-160">复制下面的模板，然后将其粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="412fc-160">Copy the following template below and paste it into a text file.</span></span> <span data-ttu-id="412fc-161">在您保存 sql-relationship.xml 的相同目录中将该文件另存为 sql-relationshipT.xml。</span><span class="sxs-lookup"><span data-stu-id="412fc-161">Save the file as sql-relationshipT.xml in the same directory where you saved sql-relationship.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sql-relationship.xml">  
            /Customer[@CustomerID=1]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="412fc-162">为映射架构 (sql-relationship.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="412fc-162">The directory path specified for the mapping schema (sql-relationship.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="412fc-163">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="412fc-163">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\sql-relationship.xml"  
    ```  
  
3.  <span data-ttu-id="412fc-164">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="412fc-164">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="412fc-165">有关详细信息，请参阅[使用 ADO 执行 SQLXML 查询](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="412fc-165">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="412fc-166">下面是结果集：</span><span class="sxs-lookup"><span data-stu-id="412fc-166">Here is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Customer CustomerID="1">   
    <Order OrderID="43860" CustomerID="1" />   
    <Order OrderID="44501" CustomerID="1" />   
    <Order OrderID="45283" CustomerID="1" />   
    <Order OrderID="46042" CustomerID="1" />   
  </Customer>   
</ROOT>  
```  
  
### <a name="b-specifying-a-relationship-chain"></a><span data-ttu-id="412fc-167">B.</span><span class="sxs-lookup"><span data-stu-id="412fc-167">B.</span></span> <span data-ttu-id="412fc-168">指定关系链</span><span class="sxs-lookup"><span data-stu-id="412fc-168">Specifying a relationship chain</span></span>  
 <span data-ttu-id="412fc-169">对于本示例，假定您需要以下 XML 文档，该文档使用从 AdventureWorks 数据库获得的数据：</span><span class="sxs-lookup"><span data-stu-id="412fc-169">For this example, assume that you want the following XML document using data obtained from the AdventureWorks database:</span></span>  
  
```  
<Order SalesOrderID="43659">  
  <Product Name="Mountain Bike Socks, M"/>   
  <Product Name="Sport-100 Helmet, Blue"/>  
  ...  
</Order>  
...  
```  
  
 <span data-ttu-id="412fc-170">对于 SalesOrderHeader 表中的每个订单，XML 文档都有一个 **\<Order>** 元素。</span><span class="sxs-lookup"><span data-stu-id="412fc-170">For each order in the Sales.SalesOrderHeader table, the XML document has one **\<Order>** element.</span></span> <span data-ttu-id="412fc-171">每个 **\<Order>** 元素都有一个 **\<Product>** 子元素列表，每个元素对应于按顺序请求的每个产品。</span><span class="sxs-lookup"><span data-stu-id="412fc-171">And each **\<Order>** element has a list of **\<Product>** child elements, one for each product requested in the order.</span></span>  
  
 <span data-ttu-id="412fc-172">若要指定将生成此层次结构的 XSD 架构，您必须指定两个关系：OrderOD 和 ODProduct。</span><span class="sxs-lookup"><span data-stu-id="412fc-172">To specify an XSD schema that will produce this hierarchy, you must specify two relationships: OrderOD and ODProduct.</span></span> <span data-ttu-id="412fc-173">OrderOD 关系在 Sales.SalesOrderHeader 表与 Sales.SalesOrderDetail 表之间指定父子关系。</span><span class="sxs-lookup"><span data-stu-id="412fc-173">The OrderOD relationship specifies the parent-child relationship between the Sales.SalesOrderHeader and Sales.SalesOrderDetail tables.</span></span> <span data-ttu-id="412fc-174">ODProduct 关系指定 Sales.SalesOrderDetail 表与 Production.Product 表之间的关系。</span><span class="sxs-lookup"><span data-stu-id="412fc-174">The ODProduct relationship specifies the relationship between the Sales.SalesOrderDetail and Production.Product tables.</span></span>  
  
 <span data-ttu-id="412fc-175">在下面的架构中， `msdata:relationship` 元素上的批注 **\<Product>** 指定了两个值： OrderOD 和 ODProduct。</span><span class="sxs-lookup"><span data-stu-id="412fc-175">In the following schema, the `msdata:relationship` annotation on the **\<Product>** element specifies two values: OrderOD and ODProduct.</span></span> <span data-ttu-id="412fc-176">指定这些值的顺序非常重要。</span><span class="sxs-lookup"><span data-stu-id="412fc-176">The order in which these values are specified is important.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:msdata="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <msdata:relationship name="OrderOD"  
          parent="Sales.SalesOrderHeader"  
          parent-key="SalesOrderID"  
          child="Sales.SalesOrderDetail"  
          child-key="SalesOrderID" />  
  
    <msdata:relationship name="ODProduct"  
          parent="Sales.SalesOrderDetail"  
          parent-key="ProductID"  
          child="Production.Product"  
          child-key="ProductID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Order" msdata:relation="Sales.SalesOrderHeader"   
               msdata:key-fields="SalesOrderID" type="OrderType" />  
   <xsd:complexType name="OrderType" >  
     <xsd:sequence>  
        <xsd:element name="Product" msdata:relation="Production.Product"   
                     msdata:key-fields="ProductID"  
                     msdata:relationship="OrderOD ODProduct">  
          <xsd:complexType>  
             <xsd:attribute name="Name" type="xsd:string" />  
          </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="SalesOrderID"   type="xsd:integer" />   
    </xsd:complexType>  
</xsd:schema>  
```  
  
 <span data-ttu-id="412fc-177">您可以指定匿名关系，而不指定命名关系。</span><span class="sxs-lookup"><span data-stu-id="412fc-177">Instead of specifying a named relationship, you can specify an anonymous relationship.</span></span> <span data-ttu-id="412fc-178">在这种情况下， **\<annotation>** **\</annotation>** 描述两个关系的全部内容将显示为的子元素 **\<Product>** 。</span><span class="sxs-lookup"><span data-stu-id="412fc-178">In this case, the entire contents of **\<annotation>**...**\</annotation>**, which describes the two relationships, appear as a child element of **\<Product>**.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:msdata="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="Order" msdata:relation="Sales.SalesOrderHeader"   
               msdata:key-fields="SalesOrderID" type="OrderType" />  
  
   <xsd:complexType name="OrderType" >  
     <xsd:sequence>  
        <xsd:element name="Product" msdata:relation="Production.Product"   
                     msdata:key-fields="ProductID" >  
         <xsd:annotation>  
          <xsd:appinfo>  
           <msdata:relationship   
               parent="Sales.SalesOrderHeader"  
               parent-key="SalesOrderID"  
               child="Sales.SalesOrderDetail"  
               child-key="SalesOrderID" />  
  
           <msdata:relationship   
               parent="Sales.SalesOrderDetail"  
               parent-key="ProductID"  
               child="Production.Product"  
               child-key="ProductID" />  
         </xsd:appinfo>  
       </xsd:annotation>  
       <xsd:complexType>  
          <xsd:attribute name="Name" type="xsd:string" />  
       </xsd:complexType>  
     </xsd:element>  
   </xsd:sequence>  
   <xsd:attribute name="SalesOrderID"   type="xsd:integer" />   
  </xsd:complexType>  
 </xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="412fc-179">针对架构测试示例 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="412fc-179">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="412fc-180">复制上面的架构代码，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="412fc-180">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="412fc-181">将文件另存为 relationshipChain.xml。</span><span class="sxs-lookup"><span data-stu-id="412fc-181">Save the file as relationshipChain.xml.</span></span>  
  
2.  <span data-ttu-id="412fc-182">复制下面的模板，然后将其粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="412fc-182">Copy the following template below and paste it into a text file.</span></span> <span data-ttu-id="412fc-183">在您保存 relationshipChain.xml 的相同目录中将该文件另存为 relationshipChainT.xml。</span><span class="sxs-lookup"><span data-stu-id="412fc-183">Save the file as relationshipChainT.xml in the same directory where you saved relationshipChain.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="relationshipChain.xml">  
            /Order  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="412fc-184">为映射架构 (relationshipChain.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="412fc-184">The directory path specified for the mapping schema (relationshipChain.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="412fc-185">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="412fc-185">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\relationshipChain.xml"  
    ```  
  
3.  <span data-ttu-id="412fc-186">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="412fc-186">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="412fc-187">有关详细信息，请参阅[使用 ADO 执行 SQLXML 查询](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="412fc-187">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="412fc-188">下面是结果集：</span><span class="sxs-lookup"><span data-stu-id="412fc-188">Here is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Order SalesOrderID="43659">  
    <Product Name="Mountain Bike Socks, M" />   
    <Product Name="Sport-100 Helmet, Blue" />   
    <Product Name="AWC Logo Cap" />   
    <Product Name="Long-Sleeve Logo Jersey, M" />   
    <Product Name="Long-Sleeve Logo Jersey, XL" />   
    ...  
  </Order>  
  ...  
</ROOT>  
```  
  
### <a name="c-specifying-the-relationship-annotation-on-an-attribute"></a><span data-ttu-id="412fc-189">C.</span><span class="sxs-lookup"><span data-stu-id="412fc-189">C.</span></span> <span data-ttu-id="412fc-190">针对属性指定关系批注</span><span class="sxs-lookup"><span data-stu-id="412fc-190">Specifying the relationship annotation on an attribute</span></span>  
 <span data-ttu-id="412fc-191">此示例中的架构包含一个 \<Customer> 元素，该元素具有一个 \<CustomerID> 子元素和一个 IDREFS 类型的 OrderIDList 属性。</span><span class="sxs-lookup"><span data-stu-id="412fc-191">The schema in this example includes a \<Customer> element with a \<CustomerID> child element and an OrderIDList attribute of IDREFS type.</span></span> <span data-ttu-id="412fc-192">\<Customer>元素映射到 AdventureWorks 数据库中的 Customer 表。</span><span class="sxs-lookup"><span data-stu-id="412fc-192">The \<Customer> element maps to the Sales.Customer table in the AdventureWorks database.</span></span> <span data-ttu-id="412fc-193">默认情况下，此映射的作用域应用于所有子元素或属性 `sql:relation` ，除非对子元素或属性指定了，在这种情况下，必须使用元素定义相应的主键/外键关系 \<relationship> 。</span><span class="sxs-lookup"><span data-stu-id="412fc-193">By default, the scope of this mapping applies to all the child elements or attributes unless `sql:relation` is specified on the child element or attribute, in which case, the appropriate primary-key/foreign-key relationship must be defined using the \<relationship> element.</span></span> <span data-ttu-id="412fc-194">并且，子元素或属性（使用 `relation` 批注指定不同的表）还必须指定 `relationship` 批注。</span><span class="sxs-lookup"><span data-stu-id="412fc-194">And the child element or attribute, which specifies the different table using the `relation` annotation, must also specify the `relationship` annotation.</span></span>  
  
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
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" type="CustomerType" />  
   <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="CustomerID"   type="xsd:string" />   
     </xsd:sequence>  
     <xsd:attribute name="OrderIDList"   
                     type="xsd:IDREFS"   
                     sql:relation="Sales.SalesOrderHeader"   
                     sql:field="SalesOrderID"  
                     sql:relationship="CustOrders" >  
        </xsd:attribute>  
    </xsd:complexType>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="412fc-195">针对架构测试示例 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="412fc-195">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="412fc-196">复制上面的架构代码，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="412fc-196">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="412fc-197">将文件另存为 relationship-on-attribute.xml。</span><span class="sxs-lookup"><span data-stu-id="412fc-197">Save the file as relationship-on-attribute.xml.</span></span>  
  
2.  <span data-ttu-id="412fc-198">复制以下模板并将其粘贴到文件中。</span><span class="sxs-lookup"><span data-stu-id="412fc-198">Copy the following template and paste it into a file.</span></span> <span data-ttu-id="412fc-199">在您保存 relationship-on-attribute.xml 的相同目录中将该文件另存为 relationship-on-attributeT.xml。</span><span class="sxs-lookup"><span data-stu-id="412fc-199">Save the file as relationship-on-attributeT.xml in the same directory where you saved relationship-on-attribute.xml.</span></span> <span data-ttu-id="412fc-200">模板中的查询选择 CustomerID 为 1 的客户。</span><span class="sxs-lookup"><span data-stu-id="412fc-200">The query in the template selects a customer with the CustomerID of 1.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="relationship-on-attribute.xml">  
        /Customer[CustomerID=1]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="412fc-201">为映射架构 (relationship-on-attribute.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="412fc-201">The directory path specified for the mapping schema (relationship-on-attribute.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="412fc-202">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="412fc-202">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\relationship-on-attribute.xml"  
    ```  
  
3.  <span data-ttu-id="412fc-203">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="412fc-203">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="412fc-204">有关详细信息，请参阅[使用 ADO 执行 SQLXML 查询](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="412fc-204">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="412fc-205">下面是结果集：</span><span class="sxs-lookup"><span data-stu-id="412fc-205">Here is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Customer OrderIDList="43860 44501 45283 46042">  
    <CustomerID>1</CustomerID>   
  </Customer>  
</ROOT>  
```  
  
### <a name="d-specifying-sqlrelationship-on-multiple-elements"></a><span data-ttu-id="412fc-206">D.</span><span class="sxs-lookup"><span data-stu-id="412fc-206">D.</span></span> <span data-ttu-id="412fc-207">针对多个元素指定 sql:relationship</span><span class="sxs-lookup"><span data-stu-id="412fc-207">Specifying sql:relationship on multiple elements</span></span>  
 <span data-ttu-id="412fc-208">在此示例中，带批注的 XSD 架构包含 **\<Customer>** 、 **\<Order>** 和 **\<OrderDetail>** 元素。</span><span class="sxs-lookup"><span data-stu-id="412fc-208">In this example, the annotated XSD schema contains the **\<Customer>**, **\<Order>**, and **\<OrderDetail>** elements.</span></span>  
  
 <span data-ttu-id="412fc-209">**\<Order>** 元素是元素的子元素 **\<Customer>** 。</span><span class="sxs-lookup"><span data-stu-id="412fc-209">The **\<Order>** element is a child element of the **\<Customer>** element.</span></span> <span data-ttu-id="412fc-210">**\<sql:relationship>** 在 **\<Order>** 子元素上指定，因此，属于某个客户的订单将显示为的子元素 **\<Customer>** 。</span><span class="sxs-lookup"><span data-stu-id="412fc-210">**\<sql:relationship>** is specified on the **\<Order>** child element; therefore, orders that belong to a customer appear as child elements of **\<Customer>**.</span></span>  
  
 <span data-ttu-id="412fc-211">**\<Order>** 元素包含 **\<OrderDetail>** 子元素。</span><span class="sxs-lookup"><span data-stu-id="412fc-211">The **\<Order>** element includes the **\<OrderDetail>** child element.</span></span> <span data-ttu-id="412fc-212">**\<sql:relationship>** 在 **\<OrderDetail>** 子元素上指定，因此，属于某个订单的订单详细信息将显示为该元素的子元素 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="412fc-212">**\<sql:relationship>** is specified on **\<OrderDetail>** child element, so the order details that pertain to an order appear as child elements of that **\<Order>** element.</span></span>  
  
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
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="OrderDate" type="xsd:date" />  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
          </xsd:complexType>  
        </xsd:element>  
      </xsd:sequence>  
      <xsd:attribute name="CustomerID" type="xsd:string" />  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="412fc-213">针对架构测试示例 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="412fc-213">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="412fc-214">复制上面的架构代码，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="412fc-214">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="412fc-215">将文件另存为 relationship-multiple-elements.xml。</span><span class="sxs-lookup"><span data-stu-id="412fc-215">Save the file as relationship-multiple-elements.xml.</span></span>  
  
2.  <span data-ttu-id="412fc-216">复制以下模板，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="412fc-216">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="412fc-217">在您保存 relationship-multiple-elements.xml 的相同目录中将该文件另存为 relationship-multiple-elementsT.xml。</span><span class="sxs-lookup"><span data-stu-id="412fc-217">Save the file as relationship-multiple-elementsT.xml in the same directory where you saved relationship-multiple-elements.xml.</span></span> <span data-ttu-id="412fc-218">模板中的查询将返回 CustomerID 为 1 且 SalesOrderID 为 43860 的客户的订单信息。</span><span class="sxs-lookup"><span data-stu-id="412fc-218">The query in the template returns order information for a customer with the CustomerID of 1 and SalesOrderID of 43860.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="relationship-multiple-elements.xml">  
        /Customer[@CustomerID=1]/Order[@SalesOrderID=43860]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="412fc-219">为映射架构 (relationship-multiple-elements.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="412fc-219">The directory path specified for the mapping schema (relationship-multiple-elements.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="412fc-220">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="412fc-220">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\relationship-multiple-elements.xml"  
    ```  
  
3.  <span data-ttu-id="412fc-221">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="412fc-221">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="412fc-222">有关详细信息，请参阅[使用 ADO 执行 SQLXML 查询](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="412fc-222">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="412fc-223">下面是结果集：</span><span class="sxs-lookup"><span data-stu-id="412fc-223">Here is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="43860" OrderDate="2001-08-01" CustomerID="1">  
     <OrderDetail SalesOrderID="43860" ProductID="761" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="770" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="758" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="765" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="732" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="762" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="738" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="768" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="753" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="729" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="763" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="756" OrderQty="1" />   
  </Order>  
</ROOT>  
```  
  
### <a name="e-specifying-the-sqlrelationship-without-the-parent-attribute"></a><span data-ttu-id="412fc-224">E.</span><span class="sxs-lookup"><span data-stu-id="412fc-224">E.</span></span> <span data-ttu-id="412fc-225">指定 \<sql:relationship> 无父属性</span><span class="sxs-lookup"><span data-stu-id="412fc-225">Specifying the \<sql:relationship> without the parent attribute</span></span>  
 <span data-ttu-id="412fc-226">此示例阐释了如何指定， **\<sql:relationship>** 而没有**父**属性。</span><span class="sxs-lookup"><span data-stu-id="412fc-226">This example illustrates specifying the **\<sql:relationship>** without the **parent** attribute.</span></span> <span data-ttu-id="412fc-227">例如，假设您具有以下员工表：</span><span class="sxs-lookup"><span data-stu-id="412fc-227">For example, assume you have the following employee tables:</span></span>  
  
```  
Emp1(SalesPersonID, FirstName, LastName, ReportsTo)  
Emp2(SalesPersonID, FirstName, LastName, ReportsTo)  
```  
  
 <span data-ttu-id="412fc-228">下面的 XML 视图具有 **\<Emp1>** **\<Emp2>** 映射到 Emp1 和 Emp2 表的和元素：</span><span class="sxs-lookup"><span data-stu-id="412fc-228">The following XML view has the **\<Emp1>** and **\<Emp2>** elements mapping to the Sales.Emp1 and Sales.Emp2 tables:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="EmpOrders"  
          parent-key="SalesPersonID"  
          child="Sales.SalesOrderHeader"  
          child-key="SalesPersonID" />  
     </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Emp1" sql:relation="Sales.Emp1" type="EmpType" />  
  <xsd:element name="Emp2" sql:relation="Sales.Emp2" type="EmpType" />  
   <xsd:complexType name="EmpType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"   
                     sql:relationship="EmpOrders" >  
          <xsd:complexType>  
             <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
             <xsd:attribute name="CustomerID" type="xsd:string" />  
          </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="SalesPersonID"   type="xsd:integer" />   
        <xsd:attribute name="LastName"   type="xsd:string" />   
    </xsd:complexType>  
  
</xsd:schema>  
```  
  
 <span data-ttu-id="412fc-229">在架构中， **\<Emp1>** 元素和 **\<Emp2>** 元素都是类型 `EmpType` 。</span><span class="sxs-lookup"><span data-stu-id="412fc-229">In the schema, both the **\<Emp1>** element and **\<Emp2>** element are of type `EmpType`.</span></span> <span data-ttu-id="412fc-230">该类型 `EmpType` 描述了一个 **\<Order>** 子元素和相应的 **\<sql:relationship>** 。</span><span class="sxs-lookup"><span data-stu-id="412fc-230">The type `EmpType` describes an **\<Order>** child element and the corresponding **\<sql:relationship>**.</span></span> <span data-ttu-id="412fc-231">在这种情况下，不存在可以 **\<sql:relationship>** 使用**parent**属性在中标识的单个父。</span><span class="sxs-lookup"><span data-stu-id="412fc-231">In this case, there is no single parent that can be identified in **\<sql:relationship>** by using the **parent** attribute.</span></span> <span data-ttu-id="412fc-232">在这种情况下，你不能在中指定**父**属性，而 **\<sql:relationship>** 是从架构的层次结构中获取**父**属性信息。</span><span class="sxs-lookup"><span data-stu-id="412fc-232">In this situation, you don't specify the **parent** attribute in **\<sql:relationship>**; the **parent** attribute information is obtained from the hierarchy in the schema.</span></span>  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="412fc-233">针对架构测试示例 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="412fc-233">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="412fc-234">在 AdventureWorks 数据库中创建这些表：</span><span class="sxs-lookup"><span data-stu-id="412fc-234">Create these tables in the AdventureWorks database:</span></span>  
  
    ```  
    USE AdventureWorks  
    CREATE TABLE Sales.Emp1 (  
           SalesPersonID int primary key,   
           FirstName  varchar(20),   
           LastName   varchar(20),   
           ReportsTo int)  
    Go  
    CREATE TABLE Sales.Emp2 (  
           SalesPersonID int primary key,   
           FirstName  varchar(20),   
           LastName   varchar(20),   
           ReportsTo int)  
    Go  
    ```  
  
2.  <span data-ttu-id="412fc-235">在这些表中添加此示例数据：</span><span class="sxs-lookup"><span data-stu-id="412fc-235">Add this sample data in the tables:</span></span>  
  
    ```  
    INSERT INTO Sales.Emp1 values (279, 'Nancy', 'Devolio',NULL)  
    INSERT INTO Sales.Emp1 values (282, 'Andrew', 'Fuller',1)  
    INSERT INTO Sales.Emp1 values (276, 'Janet', 'Leverling',1)  
    INSERT INTO Sales.Emp2 values (277, 'Margaret', 'Peacock',3)  
    INSERT INTO Sales.Emp2 values (283, 'Steven', 'Devolio',4)  
    INSERT INTO Sales.Emp2 values (275, 'Nancy', 'Buchanan',5)  
    INSERT INTO Sales.Emp2 values (281, 'Michael', 'Suyama',6)  
    ```  
  
3.  <span data-ttu-id="412fc-236">复制上面的架构代码，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="412fc-236">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="412fc-237">将文件另存为 relationship-noparent.xml。</span><span class="sxs-lookup"><span data-stu-id="412fc-237">Save the file as relationship-noparent.xml.</span></span>  
  
4.  <span data-ttu-id="412fc-238">复制以下模板，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="412fc-238">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="412fc-239">在您保存 relationship-noparent.xml 的相同目录中将该文件另存为 relationship-noparentT.xml。</span><span class="sxs-lookup"><span data-stu-id="412fc-239">Save the file as relationship-noparentT.xml in the same directory where you saved relationship-noparent.xml.</span></span> <span data-ttu-id="412fc-240">模板中的查询选择 (的所有 \<Emp1> 元素，父项为 Emp1) 。</span><span class="sxs-lookup"><span data-stu-id="412fc-240">The query in the template selects all the \<Emp1> elements (therefore, the parent is Emp1).</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="relationship-noparent.xml">  
            /Emp1  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="412fc-241">为映射架构 (relationship-noparent.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="412fc-241">The directory path specified for the mapping schema (relationship-noparent.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="412fc-242">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="412fc-242">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\relationship-noparent.xml"  
    ```  
  
5.  <span data-ttu-id="412fc-243">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="412fc-243">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="412fc-244">有关详细信息，请参阅[使用 ADO 执行 SQLXML 查询](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="412fc-244">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="412fc-245">以下为部分结果集：</span><span class="sxs-lookup"><span data-stu-id="412fc-245">Here is a partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<Emp1 SalesPersonID="276" LastName="Leverling">  
  <Order SalesOrderID="43663" CustomerID="510" />   
  <Order SalesOrderID="43666" CustomerID="511" />   
  <Order SalesOrderID="43859" CustomerID="259" />  
  ...  
</Emp1>  
```  
  
  
