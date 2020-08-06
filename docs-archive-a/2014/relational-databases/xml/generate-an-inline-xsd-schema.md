---
title: 生成内联 XSD 架构 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XSD schemas [SQL Server]
- XMLSCHEMA option
- schemas [SQL Server], XML
- XDR schemas
- FOR XML clause, inline XSD schema generation
- inline XSD schema generation [SQL Server]
- XMLDATA option
ms.assetid: 04b35145-1cca-45f4-9eb7-990abf2e647d
author: rothja
ms.author: jroth
ms.openlocfilehash: 2af748d4fc6ae67f57568be58ec7f59876098f52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694374"
---
# <a name="generate-an-inline-xsd-schema"></a><span data-ttu-id="caedc-102">生成内联 XSD 架构</span><span class="sxs-lookup"><span data-stu-id="caedc-102">Generate an Inline XSD Schema</span></span>
  <span data-ttu-id="caedc-103">在 FOR XML 子句中，可以请求在查询返回查询结果的同时返回一个内联架构。</span><span class="sxs-lookup"><span data-stu-id="caedc-103">In a FOR XML clause, you can request that your query return an inline schema together with the query results.</span></span> <span data-ttu-id="caedc-104">如果需要 XDR 架构，可以在 FOR XML 子句中使用 XMLDATA 关键字。</span><span class="sxs-lookup"><span data-stu-id="caedc-104">If you want an XDR schema, you use the XMLDATA keyword in the FOR XML clause.</span></span> <span data-ttu-id="caedc-105">如果需要 XSD 架构，可以使用 XMLSCHEMA 关键字。</span><span class="sxs-lookup"><span data-stu-id="caedc-105">If you want an XSD schema, you use the XMLSCHEMA keyword.</span></span>  
  
 <span data-ttu-id="caedc-106">本主题将介绍 XMLSCHEMA 关键字并解释所产生的内联 XSD 架构的结构。</span><span class="sxs-lookup"><span data-stu-id="caedc-106">This topic describes the XMLSCHEMA keyword and explains the structure of the resulting inline XSD schema.</span></span> <span data-ttu-id="caedc-107">下面是您请求返回内联架构时的一些限制：</span><span class="sxs-lookup"><span data-stu-id="caedc-107">Following are the limitations when you are requesting inline schemas:</span></span>  
  
-   <span data-ttu-id="caedc-108">只能在 RAW 和 AUTO 模式中，而不能在 EXPLICIT 模式中指定 XMLSCHEMA。</span><span class="sxs-lookup"><span data-stu-id="caedc-108">You can specify XMLSCHEMA only in RAW and AUTO mode, not in EXPLICIT mode.</span></span>  
  
-   <span data-ttu-id="caedc-109">如果嵌套的 FOR XML 查询指定了 TYPE 指令，查询结果则属于 `xml` 类型，并且此结果将被视为非类型化的 XML 数据的实例。</span><span class="sxs-lookup"><span data-stu-id="caedc-109">If a nested FOR XML query specifies the TYPE directive, the query result is of `xml` type, and this result is treated as an instance of untyped XML data.</span></span> <span data-ttu-id="caedc-110">有关详细信息，请参阅 [XML 数据 (SQL Server)](xml-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="caedc-110">For more information, see [XML Data &#40;SQL Server&#41;](xml-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="caedc-111">在 FOR XML 查询中指定 XMLSCHEMA 后，查询结果中便同时包含架构和 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="caedc-111">When you specify XMLSCHEMA in a FOR XML query, you receive both a schema and XML data, the query result.</span></span> <span data-ttu-id="caedc-112">数据的每个顶级元素都通过使用默认命名空间声明来引用前一个架构，而默认命名空间又引用内联架构的目标命名空间。</span><span class="sxs-lookup"><span data-stu-id="caedc-112">Each top-level element of the data refers to the previous schema by using a default namespace declaration that, in turn, refers to the target namespace of the inline schema.</span></span>  
  
 <span data-ttu-id="caedc-113">例如：</span><span class="sxs-lookup"><span data-stu-id="caedc-113">For example:</span></span>  
  
```  
<xsd:schema targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:schema="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">  
  <xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" schemaLocation="https://schemas.microsoft.com/sqlserver/2004/sqltypes/sqltypes.xsd" />  
  <xsd:element name="Production.ProductModel">  
    <xsd:complexType>  
      <xsd:attribute name="ProductModelID" type="sqltypes:int" use="required" />  
      <xsd:attribute name="Name" use="required">  
        <xsd:simpleType sqltypes:sqlTypeAlias="[AdventureWorks2012].[dbo].[Name]">  
          <xsd:restriction base="sqltypes:nvarchar" sqltypes:localeId="1033" sqltypes:sqlCompareOptions="IgnoreCase IgnoreKanaType IgnoreWidth" sqltypes:sqlSortId="52">  
            <xsd:maxLength value="50" />  
          </xsd:restriction>  
        </xsd:simpleType>  
      </xsd:attribute>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
<Production.ProductModel xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1" ProductModelID="1" Name="Classic Vest" />  
```  
  
 <span data-ttu-id="caedc-114">结果包含 XML 架构和 XML 结果。</span><span class="sxs-lookup"><span data-stu-id="caedc-114">The result includes XML schema and the XML result.</span></span> <span data-ttu-id="caedc-115">结果中的 <`ProductModel`> 顶级元素通过使用默认命名空间声明 xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1" 来引用该架构。</span><span class="sxs-lookup"><span data-stu-id="caedc-115">The <`ProductModel`> top-level element in the result refers to the schema by using the default namespace declaration, xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1" .</span></span>  
  
 <span data-ttu-id="caedc-116">结果的架构部分可能包含说明多个命名空间的多个架构文档。</span><span class="sxs-lookup"><span data-stu-id="caedc-116">The schema part of the result may contain multiple schema documents that describe multiple namespaces.</span></span> <span data-ttu-id="caedc-117">至少将返回下列两个架构文档：</span><span class="sxs-lookup"><span data-stu-id="caedc-117">At a minimum, the following two schema documents are returned:</span></span>  
  
-   <span data-ttu-id="caedc-118">一个是说明 **Sqltypes** 命名空间的架构文档，并为其返回基本 SQL 类型。</span><span class="sxs-lookup"><span data-stu-id="caedc-118">One schema document for the **Sqltypes** namespace, and for which the base SQL types are being returned.</span></span>  
  
-   <span data-ttu-id="caedc-119">另一个是说明 FOR XML 查询结果形状的架构文档。</span><span class="sxs-lookup"><span data-stu-id="caedc-119">Another schema document that describes the shape of the FOR XML query result.</span></span>  
  
 <span data-ttu-id="caedc-120">而且，如果查询结果中包含了任何类型化的 `xml` 数据类型，则与这些类型化的 `xml` 数据类型相关联的架构也包含在查询结果中。</span><span class="sxs-lookup"><span data-stu-id="caedc-120">Also, if any typed `xml` data types are included in the query result, the schemas associated with those typed `xml` data types are included.</span></span>  
  
 <span data-ttu-id="caedc-121">说明 FOR XML 结果形状的架构文档的目标命名空间包含一个固定部分和一个自动递增的数值部分。</span><span class="sxs-lookup"><span data-stu-id="caedc-121">The target namespace of the schema document that describes the shape of the FOR XML result contains a fixed portion and a numeric portion that increments automatically.</span></span> <span data-ttu-id="caedc-122">此命名空间的格式如下所示，其中 *n* 是一个正整数。</span><span class="sxs-lookup"><span data-stu-id="caedc-122">The format of this namespace is shown in the following where *n* is a positive integer.</span></span> <span data-ttu-id="caedc-123">例如，在前一个查询中，urn:schemas-microsoft-com:sql:SqlRowSet1 是目标命名空间。</span><span class="sxs-lookup"><span data-stu-id="caedc-123">For example, in the previous query, urn:schemas-microsoft-com:sql:SqlRowSet1 is the target namespace.</span></span>  
  
```  
urn:schemas-microsoft-com:sql:SqlRowSetn  
```  
  
 <span data-ttu-id="caedc-124">您可能希望两次执行的结果中的目标命名空间相同。</span><span class="sxs-lookup"><span data-stu-id="caedc-124">The change in the target namespaces in the result that occurred from one execution to another may not be desirable.</span></span> <span data-ttu-id="caedc-125">例如，如果对产生的 XML 进行查询，则假如目标命名空间发生更改，将需要更新查询。</span><span class="sxs-lookup"><span data-stu-id="caedc-125">For example, if you query the resulting XML, the change in target namespace will require that you update your query.</span></span> <span data-ttu-id="caedc-126">通过在 FOR XML 子句中添加 XMLSCHEMA 选项，可以指定目标命名空间。</span><span class="sxs-lookup"><span data-stu-id="caedc-126">You can optionally specify a target namespace when the XMLSCHEMA option is added in the FOR XML clause.</span></span> <span data-ttu-id="caedc-127">产生的 XML 将包含您提供的命名空间，而且无论运行该查询多少次，该命名空间都将保持不变。</span><span class="sxs-lookup"><span data-stu-id="caedc-127">The resulting XML will include the namespace you provided and will remain the same, regardless of how many times you run the query.</span></span>  
  
```  
SELECT ProductModelID, Name  
FROM   Production.ProductModel  
WHERE ProductModelID=1  
FOR XML AUTO, XMLSCHEMA ('MyURI')  
```  
  
## <a name="entity-elements"></a><span data-ttu-id="caedc-128">实体元素</span><span class="sxs-lookup"><span data-stu-id="caedc-128">Entity Elements</span></span>  
 <span data-ttu-id="caedc-129">为了讨论为查询结果生成的 XSD 架构结构的详细信息，必须首先介绍实体元素。</span><span class="sxs-lookup"><span data-stu-id="caedc-129">In order to discuss the details of the XSD schema structure generated for the query result, the entity element has to first be described</span></span>  
  
 <span data-ttu-id="caedc-130">由 FOR XML 查询返回的 XML 数据中的实体元素是从表而不是从列生成的。</span><span class="sxs-lookup"><span data-stu-id="caedc-130">An entity element in the XML data returned by FOR XML query is an element that is generated from a table and not from a column.</span></span> <span data-ttu-id="caedc-131">例如，下列 FOR XML 查询将返回 `Person` 数据库的 `AdventureWorks2012` 表中的联系人信息。</span><span class="sxs-lookup"><span data-stu-id="caedc-131">For example, the following FOR XML query returns contact information from the `Person` table in the `AdventureWorks2012` database.</span></span>  
  
```  
SELECT BusinessEntityID, FirstName  
FROM Person.Person  
WHERE BusinessEntityID = 1  
FOR XML AUTO, ELEMENTS  
```  
  
 <span data-ttu-id="caedc-132">结果如下：</span><span class="sxs-lookup"><span data-stu-id="caedc-132">This is the result:</span></span>  
  
 `<Person>`  
  
 `<BusinessEntityID>1</BusinessEntityID>`  
  
 `<FirstName>Ken</FirstName>`  
  
 `</Person>`  
  
 <span data-ttu-id="caedc-133">在此结果中，<`Person`> 是实体元素。</span><span class="sxs-lookup"><span data-stu-id="caedc-133">In this result, <`Person`> is the entity element.</span></span> <span data-ttu-id="caedc-134">在 XML 结果中可以有多个实体元素，并且每个实体元素在内联 XSD 架构中都具有全局声明。</span><span class="sxs-lookup"><span data-stu-id="caedc-134">There can be multiple entity elements in the XML result and each of these has a global declaration in the inline XSD schema.</span></span> <span data-ttu-id="caedc-135">例如，下面的查询将检索某个特定订单的销售订单标题和详细信息。</span><span class="sxs-lookup"><span data-stu-id="caedc-135">For example, the following query retrieves sales order header and detail information for a specific order.</span></span>  
  
```  
SELECT  SalesOrderHeader.SalesOrderID, ProductID, OrderQty  
FROM    Sales.SalesOrderHeader, Sales.SalesOrderDetail  
WHERE   SalesOrderHeader.SalesOrderID = SalesOrderDetail.SalesOrderID  
AND     SalesOrderHeader.SalesOrderID=5001  
FOR XML AUTO, ELEMENTS, XMLSCHEMA  
```  
  
 <span data-ttu-id="caedc-136">由于该查询指定了 ELEMENTS 指令，所以产生的 XML 是以元素为中心的。</span><span class="sxs-lookup"><span data-stu-id="caedc-136">Because the query specifies the ELEMENTS directive, the resulting XML is element-centric.</span></span> <span data-ttu-id="caedc-137">该查询还指定了 XMLSCHEMA 指令。</span><span class="sxs-lookup"><span data-stu-id="caedc-137">The query also specifies the XMLSCHEMA directive.</span></span> <span data-ttu-id="caedc-138">因此，将返回一个内联 XSD 架构。</span><span class="sxs-lookup"><span data-stu-id="caedc-138">Therefore, an inline XSD schema is returned.</span></span> <span data-ttu-id="caedc-139">结果如下：</span><span class="sxs-lookup"><span data-stu-id="caedc-139">This is the result:</span></span>  
  
 `<xsd:schema targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:schema="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">`  
  
 `<xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" schemaLocation="https://schemas.microsoft.com/sqlserver/2004/sqltypes/sqltypes.xsd" />`  
  
 `<xsd:element name="Sales.SalesOrderHeader">`  
  
 `<xsd:complexType>`  
  
 `<xsd:sequence>`  
  
 `<xsd:element name="SalesOrderID" type="sqltypes:int" />`  
  
 `<xsd:element ref="schema:Sales.SalesOrderDetail" minOccurs="0" maxOccurs="unbounded" />`  
  
 `</xsd:sequence>`  
  
 `</xsd:complexType>`  
  
 `</xsd:element>`  
  
 `<xsd:element name="Sales.SalesOrderDetail">`  
  
 `<xsd:complexType>`  
  
 `<xsd:sequence>`  
  
 `<xsd:element name="ProductID" type="sqltypes:int" />`  
  
 `<xsd:element name="OrderQty" type="sqltypes:smallint" />`  
  
 `</xsd:sequence>`  
  
 `</xsd:complexType>`  
  
 `</xsd:element>`  
  
 `</xsd:schema>`  
  
 <span data-ttu-id="caedc-140">请注意上述查询的以下方面：</span><span class="sxs-lookup"><span data-stu-id="caedc-140">Note the following from the previous query:</span></span>  
  
-   <span data-ttu-id="caedc-141">在结果中，<`SalesOrderHeader`> 和 <`SalesOrderDetail`> 是实体元素。</span><span class="sxs-lookup"><span data-stu-id="caedc-141">In the result, <`SalesOrderHeader`> and <`SalesOrderDetail`> are entity elements.</span></span> <span data-ttu-id="caedc-142">因此，它们在架构中是以全局的方式声明的。</span><span class="sxs-lookup"><span data-stu-id="caedc-142">Because of this, they are globally declared in the schema.</span></span> <span data-ttu-id="caedc-143">也就是说，声明显示在 <`Schema`> 元素内的顶级。</span><span class="sxs-lookup"><span data-stu-id="caedc-143">That is, the declaration appears at the top level inside the <`Schema`> element.</span></span>  
  
-   <span data-ttu-id="caedc-144"><`SalesOrderID`>、<`ProductID`> 和 <`OrderQty`> 不是实体元素，因为它们映射到一些列。</span><span class="sxs-lookup"><span data-stu-id="caedc-144">The <`SalesOrderID`>, <`ProductID`>, and <`OrderQty`> are not entity elements, because they map to columns.</span></span> <span data-ttu-id="caedc-145">由于指定了 ELEMENTS 指令，列数据将作为 XML 中的元素返回。</span><span class="sxs-lookup"><span data-stu-id="caedc-145">The column data is returned as elements in the XML, because of the ELEMENTS directive.</span></span> <span data-ttu-id="caedc-146">它们被映射到实体元素的复杂类型的本地元素。</span><span class="sxs-lookup"><span data-stu-id="caedc-146">These are mapped to local elements of the entity element's complex type.</span></span> <span data-ttu-id="caedc-147">请注意，如果没有指定 ELEMENTS 指令，则 `SalesOrderID`、 `ProductID` 和 `OrderQty` 值将被映射到相应实体元素的复杂类型的本地属性。</span><span class="sxs-lookup"><span data-stu-id="caedc-147">Note that if the ELEMENTS directive is not specified, the `SalesOrderID`, `ProductID` and `OrderQty` values are mapped to local attributes of the corresponding entity element's complex type.</span></span>  
  
## <a name="attribute-name-clashes"></a><span data-ttu-id="caedc-148">属性名称冲突</span><span class="sxs-lookup"><span data-stu-id="caedc-148">Attribute Name Clashes</span></span>  
 <span data-ttu-id="caedc-149">下面的论述基于 `CustOrder` 和 `CustOrderDetail` 表。</span><span class="sxs-lookup"><span data-stu-id="caedc-149">The following discussion is based on the `CustOrder` and `CustOrderDetail` tables.</span></span> <span data-ttu-id="caedc-150">若要测试下列示例，请创建这些表并添加自己的示例数据：</span><span class="sxs-lookup"><span data-stu-id="caedc-150">To test the following samples, create these tables and add your own sample data:</span></span>  
  
```  
CREATE TABLE CustOrder (OrderID int primary key, CustomerID int)  
GO  
CREATE TABLE CustOrderDetail (OrderID int, ProductID int, Qty int)  
GO  
```  
  
 <span data-ttu-id="caedc-151">在 FOR XML 中，同一个名称有时用来表示不同的属性、特性。</span><span class="sxs-lookup"><span data-stu-id="caedc-151">In FOR XML, the same name is sometimes used to indicate different properties, attributes.</span></span> <span data-ttu-id="caedc-152">例如，下面的以属性为中心的 RAW 模式查询将生成具有相同名称 (OrderID) 的两个属性。</span><span class="sxs-lookup"><span data-stu-id="caedc-152">For example, the following attribute-centric RAW mode query generates two attributes that have the same name, OrderID.</span></span> <span data-ttu-id="caedc-153">这将生成一个错误。</span><span class="sxs-lookup"><span data-stu-id="caedc-153">This generates an error.</span></span>  
  
```  
SELECT CustOrder.OrderID,   
       CustOrderDetail.ProductID,   
       CustOrderDetail.OrderID  
FROM   dbo.CustOrder, dbo.CustOrderDetail  
WHERE  CustOrder.OrderID = CustOrderDetail.OrderID  
FOR XML RAW, XMLSCHEMA  
```  
  
 <span data-ttu-id="caedc-154">但是，由于两个元素具有相同的名称是可以接受的，因此可以通过添加 ELEMENTS 指令来消除该问题。</span><span class="sxs-lookup"><span data-stu-id="caedc-154">However, because it is acceptable to have two elements that have the same name, you can eliminate the problem by adding the ELEMENTS directive:</span></span>  
  
```  
SELECT CustOrder.OrderID,  
       CustOrderDetail.ProductID,   
       CustOrderDetail.OrderID  
from   dbo.CustOrder, dbo.CustOrderDetail  
where  CustOrder.OrderID = CustOrderDetail.OrderID  
FOR XML RAW, XMLSCHEMA, ELEMENTS  
```  
  
 <span data-ttu-id="caedc-155">结果如下：</span><span class="sxs-lookup"><span data-stu-id="caedc-155">This is the result.</span></span> <span data-ttu-id="caedc-156">请注意，在内联 XSD 架构中，OrderID 元素被定义了两次。</span><span class="sxs-lookup"><span data-stu-id="caedc-156">Note in the inline XSD schema, the OrderID element is defined two times.</span></span> <span data-ttu-id="caedc-157">一个声明将 minOccurs 设置为 0（对应于 CustOrderDetail 表的 OrderID）；另一个声明映射到 `CustOrder` 表的 OrderID 主键列，在这种情况下，minOccurs 默认设置为 1。</span><span class="sxs-lookup"><span data-stu-id="caedc-157">One of the declarations has minOccurs set to 0, corresponding to the OrderID from the CustOrderDetail table, and the second one maps to the OrderID primary key column of the `CustOrder` table where minOccurs is 1 by default.</span></span>  
  
 `<xsd:schema targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">`  
  
 `<xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" schemaLocation="https://schemas.microsoft.com/sqlserver/2004/sqltypes/sqltypes.xsd" />`  
  
 `<xsd:element name="row">`  
  
 `<xsd:complexType>`  
  
 `<xsd:sequence>`  
  
 `<xsd:element name="OrderID" type="sqltypes:int" />`  
  
 `<xsd:element name="ProductID" type="sqltypes:int" minOccurs="0" />`  
  
 `<xsd:element name="OrderID" type="sqltypes:int" minOccurs="0" />`  
  
 `</xsd:sequence>`  
  
 `</xsd:complexType>`  
  
 `</xsd:element>`  
  
 `</xsd:schema>`  
  
## <a name="element-name-clashes"></a><span data-ttu-id="caedc-158">元素名称冲突</span><span class="sxs-lookup"><span data-stu-id="caedc-158">Element Name Clashes</span></span>  
 <span data-ttu-id="caedc-159">在 FOR XML 中，同一个名称可以用来表示两个子元素。</span><span class="sxs-lookup"><span data-stu-id="caedc-159">In FOR XML, the same name can be used to indicate two subelements.</span></span> <span data-ttu-id="caedc-160">例如，下面的查询将检索产品的 ListPrice 和 DealerPrice 值，但为这两列指定了同一别名 (Price)。</span><span class="sxs-lookup"><span data-stu-id="caedc-160">For example, the following query retrieves ListPrice and DealerPrice values of products, but the query specifies the same alias, Price, for these two columns.</span></span> <span data-ttu-id="caedc-161">因此，产生的行集将具有名称相同的两列。</span><span class="sxs-lookup"><span data-stu-id="caedc-161">Therefore, the resulting rowset will have two columns with same name.</span></span>  
  
### <a name="case-1-both-subelements-are-nonkey-columns-of-the-same-type-and-can-be-null"></a><span data-ttu-id="caedc-162">事例 1：两个子元素是相同类型的非键列而且可以为 NULL</span><span class="sxs-lookup"><span data-stu-id="caedc-162">Case 1: Both subelements are nonkey columns of the same type and can be NULL</span></span>  
 <span data-ttu-id="caedc-163">在下面的查询中，两个子元素是相同类型的非键列而且可以为 NULL。</span><span class="sxs-lookup"><span data-stu-id="caedc-163">In the following query, both subelements are nonkey columns of the same type and can be NULL.</span></span>  
  
```  
DROP TABLE T  
go  
CREATE TABLE T (ProductID int primary key, ListPrice money, DealerPrice money)  
go  
INSERT INTO T values (1, 1.25, null)  
go  
  
SELECT ProductID, ListPrice Price, DealerPrice Price  
FROM   T  
for    XML RAW, ELEMENTS, XMLSCHEMA  
```  
  
 <span data-ttu-id="caedc-164">下面是生成的相应 XML。</span><span class="sxs-lookup"><span data-stu-id="caedc-164">This is the corresponding XML generated.</span></span> <span data-ttu-id="caedc-165">仅显示了一部分内联 XSD：</span><span class="sxs-lookup"><span data-stu-id="caedc-165">Only a fraction of the inline XSD is shown:</span></span>  
  
 `...`  
  
 `<xsd:schema targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">`  
  
 `<xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" />`  
  
 `<xsd:element name="row">`  
  
 `<xsd:complexType>`  
  
 `<xsd:sequence>`  
  
 `<xsd:element name="ProductID" type="sqltypes:int" />`  
  
 `<xsd:element name="Price" type="sqltypes:money" minOccurs="0" maxOccurs="2" />`  
  
 `</xsd:sequence>`  
  
 `</xsd:complexType>`  
  
 `</xsd:element>`  
  
 `</xsd:schema>`  
  
 `<row xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1">`  
  
 `<ProductID>1</ProductID>`  
  
 `<Price>1.2500</Price>`  
  
 `</row>`  
  
 <span data-ttu-id="caedc-166">请注意该内联 XSD 架构的以下方面：</span><span class="sxs-lookup"><span data-stu-id="caedc-166">Note the following in the inline XSD schema:</span></span>  
  
-   <span data-ttu-id="caedc-167">ListPrice 和 DealerPrice 属于同一类型 ( `money`)，在表中都可以为 NULL。</span><span class="sxs-lookup"><span data-stu-id="caedc-167">Both the ListPrice and DealerPrice are of the same type, `money`, and both can be NULL in the table.</span></span> <span data-ttu-id="caedc-168">因此，由于产生的 XML 中可能不返回它们，所以在 minOccurs=0 且 maxOccurs=2 的 <`row`> 元素的复杂类型声明中仅有一个 <`Price`> 子元素。</span><span class="sxs-lookup"><span data-stu-id="caedc-168">Therefore, because they may not be returned in the resulting XML, there is only one <`Price`> child element in the complex type declaration of the <`row`> element that has minOccurs=0 and maxOccurs=2.</span></span>  
  
-   <span data-ttu-id="caedc-169">在结果中，由于表中的 `DealerPrice` 值为 NULL，所以只有 `ListPrice` 被作为一个 <`Price`> 元素返回。</span><span class="sxs-lookup"><span data-stu-id="caedc-169">In the result, because the `DealerPrice` value is NULL in the table, only `ListPrice` is returned as a <`Price`> element.</span></span> <span data-ttu-id="caedc-170">如果将 `XSINIL` 参数添加到 ELEMENTS 指令，则假如将对应于 DealerPrice 的 <`Price`> 元素的 `xsi:nil` 值设置为 TRUE，返回的结果中将包括这两个元素。</span><span class="sxs-lookup"><span data-stu-id="caedc-170">If you add the `XSINIL` parameter to the ELEMENTS directive, you will receive both of the elements that have the `xsi:nil` value set to TRUE for the<`Price`> element that corresponds to DealerPrice.</span></span> <span data-ttu-id="caedc-171">如果将两个元素的 `nillable` 属性设置为 TRUE，还将收到内联 XSD 架构的 <`row`> 复杂类型定义中的两个 <`Price`> 子元素。</span><span class="sxs-lookup"><span data-stu-id="caedc-171">You will also receive two <`Price`> child elements in the <`row`> complex type definition in the inline XSD schema with the `nillable` attribute set to TRUE for both.</span></span> <span data-ttu-id="caedc-172">下面是部分结果：</span><span class="sxs-lookup"><span data-stu-id="caedc-172">This fragment is a partial result:</span></span>  
  
 `...`  
  
 `<xsd:schema targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">`  
  
 `<xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" />`  
  
 `<xsd:element name="row">`  
  
 `<xsd:complexType>`  
  
 `<xsd:sequence>`  
  
 `<xsd:element name="ProductID" type="sqltypes:int" nillable="1" />`  
  
 `<xsd:element name="Price" type="sqltypes:money" nillable="1" />`  
  
 `<xsd:element name="Price" type="sqltypes:money" nillable="1" />`  
  
 `</xsd:sequence>`  
  
 `</xsd:complexType>`  
  
 `</xsd:element>`  
  
 `</xsd:schema>`  
  
 `<row xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">`  
  
 `<ProductID>1</ProductID>`  
  
 `<Price>1.2500</Price>`  
  
 `<Price xsi:nil="true" />`  
  
 `</row>`  
  
### <a name="case-2-one-key-and-one-nonkey-column-of-the-same-type"></a><span data-ttu-id="caedc-173">事例 2：相同类型的一个键列和一个非键列</span><span class="sxs-lookup"><span data-stu-id="caedc-173">Case 2: One key and one nonkey column of the same type</span></span>  
 <span data-ttu-id="caedc-174">下面的查询说明了相同类型的一个键列和一个非键列。</span><span class="sxs-lookup"><span data-stu-id="caedc-174">The following query illustrates one key and one nonkey column of the same type.</span></span>  
  
```  
CREATE TABLE T (Col1 int primary key, Col2 int, Col3 nvarchar(20))  
go  
INSERT INTO T VALUES (1, 1, 'test')  
go   
```  
  
 <span data-ttu-id="caedc-175">下面对表 **T** 的查询为 Col1 和 Col2 指定了相同的别名，其中 Col1 是主键，不能为空，而 Col2 可以为空。</span><span class="sxs-lookup"><span data-stu-id="caedc-175">The following query against table **T** specifies the same alias for Col1 and Col2, where Col1 is a primary key and cannot be null, and Col2 can be null.</span></span> <span data-ttu-id="caedc-176">这将生成两个同级元素，它们都是 <`row`> 元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="caedc-176">This generates two sibling elements that are children of the <`row`> element.</span></span>  
  
```  
SELECT Col1 as Col, Col2 as Col, Col3  
FROM T  
FOR XML RAW, ELEMENTS, XMLSCHEMA  
```  
  
 <span data-ttu-id="caedc-177">结果如下：</span><span class="sxs-lookup"><span data-stu-id="caedc-177">This is the result.</span></span> <span data-ttu-id="caedc-178">仅显示了一部分内联 XSD 架构。</span><span class="sxs-lookup"><span data-stu-id="caedc-178">Only a fragment of the inline XSD schema is shown.</span></span>  
  
 `...`  
  
 `<xsd:schema targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">`  
  
 `<xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" />`  
  
 `<xsd:element name="row">`  
  
 `<xsd:complexType>`  
  
 `<xsd:sequence>`  
  
 `<xsd:element name="Col" type="sqltypes:int" />`  
  
 `<xsd:element name="Col" type="sqltypes:int" minOccurs="0" />`  
  
 `<xsd:element name="Col3" minOccurs="0">`  
  
 `<xsd:simpleType>`  
  
 `<xsd:restriction base="sqltypes:nvarchar"`  
  
 `sqltypes:localeId="1033"`  
  
 `sqltypes:sqlCompareOptions="IgnoreCase`  
  
 `IgnoreKanaType IgnoreWidth"`  
  
 `sqltypes:sqlSortId="52">`  
  
 `<xsd:maxLength value="20" />`  
  
 `</xsd:restriction>`  
  
 `</xsd:simpleType>`  
  
 `</xsd:element>`  
  
 `</xsd:sequence>`  
  
 `</xsd:complexType>`  
  
 `</xsd:element>`  
  
 `</xsd:schema>`  
  
 `<row xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1">`  
  
 `<Col>1</Col>`  
  
 `<Col>1</Col>`  
  
 `<Col3>test</Col3>`  
  
 `</row>`  
  
 <span data-ttu-id="caedc-179">请注意，在内联 XSD 架构中，对应于 Col2 的 <`Col`> 元素的 minOccurs 被设置为 0。</span><span class="sxs-lookup"><span data-stu-id="caedc-179">Note in the inline XSD schema that the <`Col`> element corresponding to the Col2 has minOccurs set to 0.</span></span>  
  
### <a name="case-3-both-elements-of-different-types-and-corresponding-columns-can-be-null"></a><span data-ttu-id="caedc-180">事例 3：两个元素都属于不同的类型而且对应的列可以为 NULL</span><span class="sxs-lookup"><span data-stu-id="caedc-180">Case 3: Both elements of different types and corresponding columns can be NULL</span></span>  
 <span data-ttu-id="caedc-181">对情况 2 中显示的示例表进行下面的查询：</span><span class="sxs-lookup"><span data-stu-id="caedc-181">The following query is specified against the sample table shown in case 2:</span></span>  
  
```  
SELECT Col1, Col2 as Col, Col3 as Col  
FROM T  
FOR XML RAW, ELEMENTS, XMLSCHEMA  
```  
  
 <span data-ttu-id="caedc-182">在下面的查询中，Col2 和 Col3 被给予相同的别名。</span><span class="sxs-lookup"><span data-stu-id="caedc-182">In the following query, Col2 and Col3 are given the same aliases.</span></span> <span data-ttu-id="caedc-183">这将生成两个具有相同名称的同级元素，而且它们都是结果中 <`raw`> 元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="caedc-183">This generates two sibling elements that have the same name and that are both children of the <`raw`> element in the result.</span></span> <span data-ttu-id="caedc-184">这两列类型不同，而且都可以为 NULL。</span><span class="sxs-lookup"><span data-stu-id="caedc-184">Both of these columns are of different types and both can be NULL.</span></span> <span data-ttu-id="caedc-185">结果如下：</span><span class="sxs-lookup"><span data-stu-id="caedc-185">This is the result.</span></span> <span data-ttu-id="caedc-186">仅显示了部分内联 XSD 架构。</span><span class="sxs-lookup"><span data-stu-id="caedc-186">Only partial inline XSD schema is shown.</span></span>  
  
 `...`  
  
 `<xsd:schema targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">`  
  
 `<xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" />`  
  
 `<xsd:simpleType name="Col1">`  
  
 `<xsd:restriction base="sqltypes:int" />`  
  
 `</xsd:simpleType>`  
  
 `<xsd:simpleType name="Col2">`  
  
 `<xsd:restriction base="sqltypes:nvarchar" sqltypes:localeId="1033"`  
  
 `sqltypes:sqlCompareOptions="IgnoreCase`  
  
 `IgnoreKanaType IgnoreWidth" sqltypes:sqlSortId="52">`  
  
 `<xsd:maxLength value="20" />`  
  
 `</xsd:restriction>`  
  
 `</xsd:simpleType>`  
  
 `<xsd:element name="row">`  
  
 `<xsd:complexType>`  
  
 `<xsd:sequence>`  
  
 `<xsd:element name="Col1" type="sqltypes:int" />`  
  
 `<xsd:element name="Col" minOccurs="0" maxOccurs="2" type="xsd:anySimpleType" />`  
  
 `</xsd:sequence>`  
  
 `</xsd:complexType>`  
  
 `</xsd:element>`  
  
 `</xsd:schema>`  
  
 `<row xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1">`  
  
 `<Col1>1</Col1>`  
  
 `<Col xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"`  
  
 `xsi:type="Col1">1</Col>`  
  
 `<Col xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"`  
  
 `xsi:type="Col2">test</Col>`  
  
 `</row>`  
  
 <span data-ttu-id="caedc-187">请注意该内联 XSD 架构的以下方面：</span><span class="sxs-lookup"><span data-stu-id="caedc-187">Note the following in the inline XSD schema:</span></span>  
  
-   <span data-ttu-id="caedc-188">由于 Col2 和 Col3 都可以为 NULL，所以 <`Col`> 元素声明将 minOccurs 指定为 0，将 maxOccurs 指定为 2。</span><span class="sxs-lookup"><span data-stu-id="caedc-188">Because both Col2 and Col3 can be NULL, the <`Col`> element declaration specifies the minOccurs as 0 and maxOccurs as 2.</span></span>  
  
-   <span data-ttu-id="caedc-189">由于两个 <`Col`> 元素是同级元素，所以在架构中只有一个元素声明。</span><span class="sxs-lookup"><span data-stu-id="caedc-189">Because both the <`Col`> elements are siblings, there is one element declaration in the schema.</span></span> <span data-ttu-id="caedc-190">而且，还由于两个元素类型不同，所以尽管都是简单类型，架构中元素的类型仍为 `xsd:anySimpleType`。</span><span class="sxs-lookup"><span data-stu-id="caedc-190">Also, because both of the elements are also of different types, though both are simple types, the type of the element in the schema is `xsd:anySimpleType`.</span></span> <span data-ttu-id="caedc-191">在结果中，每个实例类型都由 `xsi:type` 属性标识。</span><span class="sxs-lookup"><span data-stu-id="caedc-191">In the result, each instance type is identified by the `xsi:type` attribute.</span></span>  
  
-   <span data-ttu-id="caedc-192">在结果中，<`Col`> 元素的每个实例都通过使用 `xsi:type` 属性来引用其实例类型。</span><span class="sxs-lookup"><span data-stu-id="caedc-192">In the result, every instance of the <`Col`> element refers to its instance type by using the `xsi:type` attribute.</span></span>  
  
  
