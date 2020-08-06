---
title: 示例：使用 OPENXML | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- ColPattern [XML in SQL Server]
- XML [SQL Server], mapping data
- OPENXML statement, about OPENXML statement
- overflow in XML document [SQL Server]
- mapping XML data [SQL Server]
- combining attribute-centric and element centric mapping
- unconsumed data
- attribute-centric mapping
- column patterns [XML in SQL Server]
- XML [SQL Server], overflow handling
- row patterns [XML in SQL Server]
- rowpattern [XML in SQL Server]
- flags parameter
- element-centric mapping [SQL Server]
- edge tables
ms.assetid: 689297f3-adb0-4d8d-bf62-cfda26210164
author: rothja
ms.author: jroth
ms.openlocfilehash: 09fc6ad073b12df2f9fbd8ebc6a59149f6154ced
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694394"
---
# <a name="examples-using-openxml"></a><span data-ttu-id="9f3ae-102">示例：使用 OPENXML</span><span class="sxs-lookup"><span data-stu-id="9f3ae-102">Examples: Using OPENXML</span></span>
  <span data-ttu-id="9f3ae-103">本主题中的示例说明如何使用 OPENXML 创建 XML 文档的行集视图。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-103">The examples in this topic show how OPENXML is used to create a rowset view of an XML document.</span></span> <span data-ttu-id="9f3ae-104">有关 OPENXML 语法的信息，请参阅 [OPENXML (Transact-SQL)](/sql/t-sql/functions/openxml-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-104">For information about the syntax of OPENXML, see [OPENXML &#40;Transact-SQL&#41;](/sql/t-sql/functions/openxml-transact-sql).</span></span> <span data-ttu-id="9f3ae-105">这些示例说明了 OPENXML 的各个方面，但不包括在 OPENXML 中指定元属性。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-105">The examples show all aspects of OPENXML, but do not specify metaproperties in OPENXML.</span></span> <span data-ttu-id="9f3ae-106">有关如何在 OPENXML 中指定元属性的详细信息，请参阅 [在 OPENXML 中指定元属性](specify-metaproperties-in-openxml.md)。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-106">For more information about how to specify metaproperties in OPENXML, see [Specify Metaproperties in OPENXML](specify-metaproperties-in-openxml.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="9f3ae-107">示例</span><span class="sxs-lookup"><span data-stu-id="9f3ae-107">Examples</span></span>  
 <span data-ttu-id="9f3ae-108">在检索数据时， *rowpattern* 可用于在确定行的 XML 文档中标识节点。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-108">In retrieving the data, *rowpattern* is used to identify the nodes in the XML document that determine the rows.</span></span> <span data-ttu-id="9f3ae-109">此外， *rowpattern* 是用实现 MSXML XPath 所采用的 XPath 模式语言表示的。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-109">Additionally, *rowpattern* is expressed in the XPath pattern language that is used in the MSXML XPath implementation.</span></span> <span data-ttu-id="9f3ae-110">例如，如果模式以元素或属性结束，则为 *rowpattern*选择的每个元素或属性节点创建一行。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-110">For example, if the pattern ends in an element or an attribute, a row is created for each element or attribute node that is selected by *rowpattern*.</span></span>  
  
 <span data-ttu-id="9f3ae-111">*flags* 值提供默认映射。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-111">The *flags* value provides default mapping.</span></span> <span data-ttu-id="9f3ae-112">如果 *SchemaDeclaration* 中没有指定 *ColPattern*，则假定使用 *flags* 所指定的映射。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-112">If no *ColPattern* is specified in the *SchemaDeclaration*, the mapping specified in *flags* is assumed.</span></span> <span data-ttu-id="9f3ae-113">如果在 *SchemaDeclaration* 中指定了 *ColPattern* ，则忽略 *flags*值。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-113">The *flags* value is ignored if *ColPattern* is specified in *SchemaDeclaration*.</span></span> <span data-ttu-id="9f3ae-114">指定的 *ColPattern* 决定了映射是以属性为中心还是以元素为中心，还决定了在处理溢出数据和未用完数据时的行为。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-114">The specified *ColPattern* determines the mapping, attribute-centric or element-centric, and also the behavior in dealing with overflow and unconsumed data.</span></span>  
  
### <a name="a-executing-a-simple-select-statement-with-openxml"></a><span data-ttu-id="9f3ae-115">A.</span><span class="sxs-lookup"><span data-stu-id="9f3ae-115">A.</span></span> <span data-ttu-id="9f3ae-116">使用 OPENXML 执行简单的 SELECT 语句</span><span class="sxs-lookup"><span data-stu-id="9f3ae-116">Executing a simple SELECT statement with OPENXML</span></span>  
 <span data-ttu-id="9f3ae-117">此示例中的 XML 文档由 <`Customer`>、<`Order`> 和 <`OrderDetail`> 元素组成。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-117">The XML document in this example is made up of the <`Customer`>, <`Order`>, and <`OrderDetail`> elements.</span></span> <span data-ttu-id="9f3ae-118">OPENXML 语句从 XML 文档中检索两列行集（ **CustomerID** 和 **ContactName**）中的客户信息。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-118">The OPENXML statement retrieves customer information in a two-column rowset, **CustomerID** and **ContactName**, from the XML document.</span></span>  
  
 <span data-ttu-id="9f3ae-119">首先调用 **sp_xml_preparedocument** 存储过程以获得文档句柄。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-119">First, the **sp_xml_preparedocument** stored procedure is called to obtain a document handle.</span></span> <span data-ttu-id="9f3ae-120">此文档句柄传递给 OPENXML。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-120">This document handle is passed to OPENXML.</span></span>  
  
 <span data-ttu-id="9f3ae-121">OPENXML 语句说明了以下信息：</span><span class="sxs-lookup"><span data-stu-id="9f3ae-121">The OPENXML statement illustrates the following:</span></span>  
  
-   <span data-ttu-id="9f3ae-122">*rowpattern* (/ROOT/Customer) 标识要处理的 <`Customer`> 节点。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-122">*rowpattern* (/ROOT/Customer) identifies the <`Customer`> nodes to process.</span></span>  
  
-   <span data-ttu-id="9f3ae-123">*flags* 参数值设置为 **1** ，表示以属性为中心的映射。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-123">The *flags* parameter value is set to **1** and indicates attribute-centric mapping.</span></span> <span data-ttu-id="9f3ae-124">因此，XML 属性映射到 *SchemaDeclaration*中所定义的行集中的列。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-124">As a result, the XML attributes map to the columns in the rowset defined in *SchemaDeclaration*.</span></span>  
  
-   <span data-ttu-id="9f3ae-125">在 WITH 子句的 *SchemaDeclaration*中所指定的 *ColName* 值与相应的 XML 属性名称相匹配。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-125">In *SchemaDeclaration*, in the WITH clause, the specified *ColName* values match the corresponding XML attribute names.</span></span> <span data-ttu-id="9f3ae-126">因此，在 *SchemaDeclaration* 中不指定 *ColPattern*参数。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-126">Therefore, the *ColPattern* parameter is not specified in *SchemaDeclaration*.</span></span>  
  
 <span data-ttu-id="9f3ae-127">SELECT 语句随后将检索 OPENXML 所提供的行集中的所有列。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-127">The SELECT statement then retrieves all the columns in the rowset provided by OPENXML.</span></span>  
  
```  
DECLARE @DocHandle int  
DECLARE @XmlDocument nvarchar(1000)  
SET @XmlDocument = N'<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order OrderID="10248" CustomerID="VINET" EmployeeID="5"   
          OrderDate="1996-07-04T00:00:00">  
      <OrderDetail ProductID="11" Quantity="12"/>  
      <OrderDetail ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order OrderID="10283" CustomerID="LILAS" EmployeeID="3"   
          OrderDate="1996-08-16T00:00:00">  
      <OrderDetail ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @DocHandle OUTPUT, @XmlDocument  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@DocHandle, '/ROOT/Customer',1)  
      WITH (CustomerID  varchar(10),  
            ContactName varchar(20))  
EXEC sp_xml_removedocument @DocHandle  
```  
  
 <span data-ttu-id="9f3ae-128">结果如下：</span><span class="sxs-lookup"><span data-stu-id="9f3ae-128">This is the result:</span></span>  
  
```  
CustomerID ContactName            
---------- --------------------   
VINET      Paul Henriot  
LILAS      Carlos Gonzlez  
```  
  
 <span data-ttu-id="9f3ae-129">由于 <`Customer`> 元素没有任何子元素，因而如果在 *flags* 设置为**2** 时（表示以元素为中心的映射）执行上述 SELECT 语句，则两个客户的 **CustomerID** 和 **ContactName** 值将返回 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-129">Because the <`Customer`> elements do not have any subelements, if the same SELECT statement is executed with *flags* set to **2** to indicate element-centric mapping, the values of **CustomerID** and **ContactName** for both the customers are returned as NULL.</span></span>  
  
 <span data-ttu-id="9f3ae-130">@xmlDocument 也可以是 **xml** 类型或 **(n)varchar(max)** 类型。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-130">The @xmlDocument can also be of **xml** type or of **(n)varchar(max)** type.</span></span>  
  
 <span data-ttu-id="9f3ae-131">如果 XML 文档中的 <`CustomerID`> 和 <`ContactName`> 是子元素，则以元素为中心的映射将检索值。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-131">If <`CustomerID`> and <`ContactName`> in the XML document are subelements, the element-centric mapping retrieves the values.</span></span>  
  
```  
DECLARE @XmlDocumentHandle int  
DECLARE @XmlDocument nvarchar(1000)  
SET @XmlDocument = N'<ROOT>  
<Customer>  
   <CustomerID>VINET</CustomerID>  
   <ContactName>Paul Henriot</ContactName>  
   <Order OrderID="10248" CustomerID="VINET" EmployeeID="5" OrderDate="1996-07-04T00:00:00">  
      <OrderDetail ProductID="11" Quantity="12"/>  
      <OrderDetail ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer>     
   <CustomerID>LILAS</CustomerID>  
   <ContactName>Carlos Gonzlez</ContactName>  
   <Order OrderID="10283" CustomerID="LILAS" EmployeeID="3" OrderDate="1996-08-16T00:00:00">  
      <OrderDetail ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @XmlDocumentHandle OUTPUT, @XmlDocument  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT    *  
FROM      OPENXML (@XmlDocumentHandle, '/ROOT/Customer',2)  
           WITH (CustomerID  varchar(10),  
                 ContactName varchar(20))  
EXEC sp_xml_removedocument @XmlDocumentHandle  
```  
  
 <span data-ttu-id="9f3ae-132">结果如下：</span><span class="sxs-lookup"><span data-stu-id="9f3ae-132">This is the result:</span></span>  
  
```  
CustomerID ContactName            
---------- --------------------   
VINET      Paul Henriot  
LILAS      Carlos Gonzlez  
```  
  
 <span data-ttu-id="9f3ae-133">请注意， **sp_xml_preparedocument** 返回的文档句柄在批处理持续时间（而非会话持续时间）内有效。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-133">Note that the document handle returned by **sp_xml_preparedocument** is valid for the duration of the batch and not the session.</span></span>  
  
### <a name="b-specifying-colpattern-for-mapping-between-rowset-columns-and-the-xml-attributes-and-elements"></a><span data-ttu-id="9f3ae-134">B.</span><span class="sxs-lookup"><span data-stu-id="9f3ae-134">B.</span></span> <span data-ttu-id="9f3ae-135">为行集列与 XML 属性及元素之间的映射指定 ColPattern</span><span class="sxs-lookup"><span data-stu-id="9f3ae-135">Specifying ColPattern for mapping between rowset columns and the XML attributes and elements</span></span>  
 <span data-ttu-id="9f3ae-136">此示例说明如何在可选的 *ColPattern* 参数中指定 XPath 模式，以提供行集列和 XML 属性以及元素之间的映射。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-136">This example shows how the XPath pattern is specified in the optional *ColPattern* parameter to provide mapping between rowset columns and the XML attributes and elements.</span></span>  
  
 <span data-ttu-id="9f3ae-137">此示例中的 XML 文档由 <`Customer`>、<`Order`> 和 <`OrderDetail`> 元素组成。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-137">The XML document in this example is made up of the <`Customer`>, <`Order`>, and <`OrderDetail`> elements.</span></span> <span data-ttu-id="9f3ae-138">OPENXML 语句从该 XML 文档中检索客户和订单信息作为行集（**CustomerID**、 **OrderDate**、 **ProdID**和 **Qty**）。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-138">The OPENXML statement retrieves customer and order information as a rowset (**CustomerID**, **OrderDate**, **ProdID**, and **Qty**) from the XML document.</span></span>  
  
 <span data-ttu-id="9f3ae-139">首先调用 **sp_xml_preparedocument** 存储过程以获得文档句柄。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-139">First, the **sp_xml_preparedocument** stored procedure is called to obtain a document handle.</span></span> <span data-ttu-id="9f3ae-140">此文档句柄传递给 OPENXML。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-140">This document handle is passed to OPENXML.</span></span>  
  
 <span data-ttu-id="9f3ae-141">OPENXML 语句说明了以下信息：</span><span class="sxs-lookup"><span data-stu-id="9f3ae-141">The OPENXML statement illustrates the following:</span></span>  
  
-   <span data-ttu-id="9f3ae-142">*rowpattern* (/ROOT/Customer/Order/OrderDetail) 标识要处理的 <`OrderDetail`> 节点。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-142">*rowpattern* (/ROOT/Customer/Order/OrderDetail) identifies the <`OrderDetail`> nodes to process.</span></span>  
  
 <span data-ttu-id="9f3ae-143">为了举例说明，将 *flags* 参数值设置为 **2** ，表示以元素为中心的映射。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-143">For illustration, the *flags* parameter value is set to **2** and indicates element-centric mapping.</span></span> <span data-ttu-id="9f3ae-144">但是， *ColPattern* 中指定的映射覆盖了此映射。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-144">However, the mapping specified in *ColPattern* overwrites this mapping.</span></span> <span data-ttu-id="9f3ae-145">即 *ColPattern* 中指定的 XPath 模式将行集中的列映射到属性。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-145">That is, the XPath pattern specified in *ColPattern* maps the columns in the rowset to attributes.</span></span> <span data-ttu-id="9f3ae-146">这将产生以属性为中心的映射。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-146">This results in attribute-centric mapping.</span></span>  
  
 <span data-ttu-id="9f3ae-147">在 WITH 子句内的 *SchemaDeclaration*中，也可以用 *ColName* 和 *ColType* 参数指定 *ColPattern* 。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-147">In *SchemaDeclaration*, in the WITH clause, *ColPattern* is also specified with the *ColName* and *ColType* parameters.</span></span> <span data-ttu-id="9f3ae-148">可选的 *ColPattern* 是指定的 XPath 模式，表示以下内容：</span><span class="sxs-lookup"><span data-stu-id="9f3ae-148">The optional *ColPattern* is the XPath pattern specified and indicates the following:</span></span>  
  
-   <span data-ttu-id="9f3ae-149">行集中的 **OrderID**、 **CustomerID** 和 **OrderDate** 列映射到 *rowpattern* 所标识节点的父节点的属性，同时，*rowpattern* 还标识 <`OrderDetail`> 节点。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-149">The **OrderID**, **CustomerID**, and **OrderDate** columns in the rowset map to the attributes of the parent of the nodes identified by *rowpattern*, and *rowpattern* identifies the <`OrderDetail`> nodes.</span></span> <span data-ttu-id="9f3ae-150">因此，**CustomerID** 和 **OrderDate** 列映射到 <`Order`> 元素的**CustomerID** 和 **OrderDate** 属性。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-150">Therefore, the **CustomerID** and **OrderDate** columns map to **CustomerID** and **OrderDate** attributes of the <`Order`> element.</span></span>  
  
-   <span data-ttu-id="9f3ae-151">行集中的 **ProdID** 和 **Qty** 列映射到 **rowpattern** 所标识节点的 **ProductID** 和 *Quantity*属性。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-151">The **ProdID** and **Qty** columns in the rowset map to the **ProductID** and **Quantity** attributes of the nodes identified in *rowpattern*.</span></span>  
  
 <span data-ttu-id="9f3ae-152">SELECT 语句随后将检索 OPENXML 所提供的行集中的所有列。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-152">The SELECT statement then retrieves all the columns in the rowset provided by OPENXML.</span></span>  
  
```  
DECLARE @XmlDocumentHandle int  
DECLARE @XmlDocument nvarchar(1000)  
SET @XmlDocument = N'<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order OrderID="10248" CustomerID="VINET" EmployeeID="5"   
           OrderDate="1996-07-04T00:00:00">  
      <OrderDetail ProductID="11" Quantity="12"/>  
      <OrderDetail ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order OrderID="10283" CustomerID="LILAS" EmployeeID="3"   
           OrderDate="1996-08-16T00:00:00">  
      <OrderDetail ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @XmlDocumentHandle OUTPUT, @XmlDocument  
-- Execute a SELECT stmt using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@XmlDocumentHandle, '/ROOT/Customer/Order/OrderDetail',2)  
WITH (OrderID     int         '../@OrderID',  
      CustomerID  varchar(10) '../@CustomerID',  
      OrderDate   datetime    '../@OrderDate',  
      ProdID      int         '@ProductID',  
      Qty         int         '@Quantity')  
EXEC sp_xml_removedocument @XmlDocumentHandle  
```  
  
 <span data-ttu-id="9f3ae-153">结果如下：</span><span class="sxs-lookup"><span data-stu-id="9f3ae-153">This is the result:</span></span>  
  
```  
OrderID CustomerID        OrderDate          ProdID    Qty  
-------------------------------------------------------------  
10248    VINET     1996-07-04 00:00:00.000     11       12  
10248    VINET     1996-07-04 00:00:00.000     42       10  
10283    LILAS     1996-08-16 00:00:00.000     72        3  
```  
  
 <span data-ttu-id="9f3ae-154">也可以对已指定为 *ColPattern* 的 XPath 模式重新指定，以将 XML 元素映射到行集列。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-154">The XPath pattern specified as *ColPattern* can also be specified to map the XML elements to the rowset columns.</span></span> <span data-ttu-id="9f3ae-155">这将产生以元素为中心的映射。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-155">This results in element-centric mapping.</span></span> <span data-ttu-id="9f3ae-156">在下例中，XML 文档 <`CustomerID`> 和 <`OrderDate`> 是 <`Orders`> 元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-156">In the following example, the XML document <`CustomerID`> and <`OrderDate`> are subelements of the <`Orders`> element.</span></span> <span data-ttu-id="9f3ae-157">由于 *ColPattern* 覆盖 *flags* 参数中所指定的映射，所以在 OPENXML 中没有指定 *flags* 参数。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-157">Because *ColPattern* overwrites the mapping specified in the *flags* parameter, the *flags* parameter is not specified in OPENXML.</span></span>  
  
```  
DECLARE @docHandle int  
DECLARE @XmlDocument nvarchar(1000)  
SET @XmlDocument = N'<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order EmployeeID="5" >  
      <OrderID>10248</OrderID>  
      <CustomerID>VINET</CustomerID>  
      <OrderDate>1996-07-04T00:00:00</OrderDate>  
      <OrderDetail ProductID="11" Quantity="12"/>  
      <OrderDetail ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order  EmployeeID="3" >  
      <OrderID>10283</OrderID>  
      <CustomerID>LILAS</CustomerID>  
      <OrderDate>1996-08-16T00:00:00</OrderDate>  
      <OrderDetail ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @docHandle OUTPUT, @XmlDocument  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@docHandle, '/ROOT/Customer/Order/OrderDetail')  
WITH (CustomerID  varchar(10)   '../CustomerID',  
      OrderDate   datetime      '../OrderDate',  
      ProdID      int           '@ProductID',  
      Qty         int           '@Quantity')  
EXEC sp_xml_removedocument @docHandle  
```  
  
### <a name="c-combining-attribute-centric-and-element-centric-mapping"></a><span data-ttu-id="9f3ae-158">C.</span><span class="sxs-lookup"><span data-stu-id="9f3ae-158">C.</span></span> <span data-ttu-id="9f3ae-159">组合以属性为中心的映射和以元素为中心的映射</span><span class="sxs-lookup"><span data-stu-id="9f3ae-159">Combining attribute-centric and element-centric mapping</span></span>  
 <span data-ttu-id="9f3ae-160">在此示例中， *flags* 参数设置为 **3** ，表示将应用以属性为中心的映射和以元素为中心的映射。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-160">In this example, the *flags* parameter is set to **3** and indicates that both attribute-centric and element-centric mapping will be applied.</span></span> <span data-ttu-id="9f3ae-161">在这种情况下，首先应用以属性为中心的映射，然后对所有未处理的列应用以元素为中心的映射。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-161">In this case, the attribute-centric mapping is applied first, and then element-centric mapping is applied for all the columns not yet dealt with.</span></span>  
  
```  
DECLARE @docHandle int  
DECLARE @XmlDocument nvarchar(1000)  
SET @XmlDocument =N'<ROOT>  
<Customer CustomerID="VINET"  >  
     <ContactName>Paul Henriot</ContactName>  
   <Order OrderID="10248" CustomerID="VINET" EmployeeID="5"   
          OrderDate="1996-07-04T00:00:00">  
      <OrderDetail ProductID="11" Quantity="12"/>  
      <OrderDetail ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" >   
     <ContactName>Carlos Gonzlez</ContactName>  
   <Order OrderID="10283" CustomerID="LILAS" EmployeeID="3"   
          OrderDate="1996-08-16T00:00:00">  
      <OrderDetail ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @docHandle OUTPUT, @XmlDocument  
  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@docHandle, '/ROOT/Customer',3)  
      WITH (CustomerID  varchar(10),  
            ContactName varchar(20))  
EXEC sp_xml_removedocument @docHandle  
```  
  
 <span data-ttu-id="9f3ae-162">下面是查询结果。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-162">This is the result</span></span>  
  
```  
CustomerID ContactName            
---------- --------------------   
VINET      Paul Henriot  
LILAS      Carlos Gonzlez  
```  
  
 <span data-ttu-id="9f3ae-163">以属性为中心的映射应用于 **CustomerID**。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-163">The attribute-centric mapping is applied for **CustomerID**.</span></span> <span data-ttu-id="9f3ae-164">在 <`Customer`> 元素中不存在 **ContactName** 属性。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-164">There is no **ContactName** attribute in the <`Customer`> element.</span></span> <span data-ttu-id="9f3ae-165">因此，应用以元素为中心的映射。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-165">Therefore, element-centric mapping is applied.</span></span>  
  
### <a name="d-specifying-the-text-xpath-function-as-colpattern"></a><span data-ttu-id="9f3ae-166">D.</span><span class="sxs-lookup"><span data-stu-id="9f3ae-166">D.</span></span> <span data-ttu-id="9f3ae-167">指定 text() XPath 函数作为 ColPattern</span><span class="sxs-lookup"><span data-stu-id="9f3ae-167">Specifying the text() XPath function as ColPattern</span></span>  
 <span data-ttu-id="9f3ae-168">此示例中的 XML 文档由 <`Customer`> 和 <`Order`> 元素组成。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-168">The XML document in this example is made up of the <`Customer`> and <`Order`> elements.</span></span> <span data-ttu-id="9f3ae-169">OPENXML 语句从 <`Order`> 元素、*rowpattern* 所标识节点的父节点 ID 和元素内容的叶值字符串中检索由 **oid** 属性组成的行集。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-169">The OPENXML statement retrieves a rowset that is made up of the **oid** attribute from the <`Order`> element, the ID of the parent of the node identified by *rowpattern*, and the leaf-value string of the element content.</span></span>  
  
 <span data-ttu-id="9f3ae-170">首先调用 **sp_xml_preparedocument** 存储过程以获得文档句柄。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-170">First, the **sp_xml_preparedocument** stored procedure is called to obtain a document handle.</span></span> <span data-ttu-id="9f3ae-171">此文档句柄传递给 OPENXML。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-171">This document handle is passed to OPENXML.</span></span>  
  
 <span data-ttu-id="9f3ae-172">OPENXML 语句说明了以下信息：</span><span class="sxs-lookup"><span data-stu-id="9f3ae-172">The OPENXML statement illustrates the following:</span></span>  
  
-   <span data-ttu-id="9f3ae-173">*rowpattern* (/root/Customer/Order) 标识要处理的 <`Order`> 节点。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-173">*rowpattern* (/root/Customer/Order) identifies the <`Order`> nodes to process.</span></span>  
  
-   <span data-ttu-id="9f3ae-174">*flags* 参数值设置为 **1** ，表示以属性为中心的映射。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-174">The *flags* parameter value is set to **1** and indicates attribute-centric mapping.</span></span> <span data-ttu-id="9f3ae-175">因此，XML 属性映射到 *SchemaDeclaration*中定义的行集列。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-175">As a result, the XML attributes map to the rowset columns defined in *SchemaDeclaration*.</span></span>  
  
-   <span data-ttu-id="9f3ae-176">在 WITH 子句的 *SchemaDeclaration* 中， **oid** 和 **amount** 行集列名与相应的 XML 属性名称相匹配。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-176">In *SchemaDeclaration* in the WITH clause, the **oid** and **amount** rowset column names match the corresponding XML attribute names.</span></span> <span data-ttu-id="9f3ae-177">因此，没有指定 *ColPattern* 参数。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-177">Therefore, the *ColPattern* parameter is not specified.</span></span> <span data-ttu-id="9f3ae-178">对于行集中的 **comment** 列，XPath 函数 **text()** 将被指定为 *ColPattern*。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-178">For the **comment** column in the rowset, the XPath function, **text()**, is specified as *ColPattern*.</span></span> <span data-ttu-id="9f3ae-179">这将覆盖在 *flags*参数中指定的以属性为中心的映射，而且列将包含元素内容的叶值字符串。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-179">This overwrites the attribute-centric mapping specified in *flags*, and the column contains the leaf-value string of the element content.</span></span>  
  
 <span data-ttu-id="9f3ae-180">SELECT 语句随后将检索 OPENXML 所提供的行集中的所有列。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-180">The SELECT statement then retrieves all the columns in the rowset provided by OPENXML.</span></span>  
  
```  
DECLARE @docHandle int  
DECLARE @xmlDocument nvarchar(1000)  
--sample XML document  
SET @xmlDocument =N'<root>  
  <Customer cid= "C1" name="Janine" city="Issaquah">  
      <Order oid="O1" date="1/20/1996" amount="3.5" />  
      <Order oid="O2" date="4/30/1997" amount="13.4">Customer was very satisfied  
      </Order>  
   </Customer>  
   <Customer cid="C2" name="Ursula" city="Oelde" >  
      <Order oid="O3" date="7/14/1999" amount="100" note="Wrap it blue   
             white red">  
            <Urgency>Important</Urgency>  
            Happy Customer.  
      </Order>  
      <Order oid="O4" date="1/20/1996" amount="10000"/>  
   </Customer>  
</root>'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @docHandle OUTPUT, @xmlDocument  
  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@docHandle, '/root/Customer/Order', 1)  
     WITH (oid     char(5),   
           amount  float,   
           comment ntext 'text()')  
EXEC sp_xml_removedocument @docHandle  
```  
  
 <span data-ttu-id="9f3ae-181">结果如下：</span><span class="sxs-lookup"><span data-stu-id="9f3ae-181">This is the result:</span></span>  
  
```  
oid   amount        comment  
----- -----------   -----------------------------  
O1    3.5           NULL  
O2    13.4          Customer was very satisfied  
O3    100.0         Happy Customer.  
O4    10000.0       NULL  
```  
  
### <a name="e-specifying-tablename-in-the-with-clause"></a><span data-ttu-id="9f3ae-182">E.</span><span class="sxs-lookup"><span data-stu-id="9f3ae-182">E.</span></span> <span data-ttu-id="9f3ae-183">在 WITH 子句中指定 TableName</span><span class="sxs-lookup"><span data-stu-id="9f3ae-183">Specifying TableName in the WITH clause</span></span>  
 <span data-ttu-id="9f3ae-184">此示例在 WITH 子句中指定 *TableName* ，而不指定 *SchemaDeclaration*。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-184">This example specifies *TableName* in the WITH clause instead of *SchemaDeclaration*.</span></span> <span data-ttu-id="9f3ae-185">当表具有想要的结构而不具备列模式（ *ColPattern* 参数）时，这非常有用。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-185">This is useful if you have a table that has the structure you want and no column patterns, *ColPattern* parameter, are required.</span></span>  
  
 <span data-ttu-id="9f3ae-186">此示例中的 XML 文档由 <`Customer`> 和 <`Order`> 元素组成。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-186">The XML document in this example is made up of the <`Customer`> and <`Order`> elements.</span></span> <span data-ttu-id="9f3ae-187">OPENXML 语句从 XML 文档中检索三列行集（**oid**、 **date**和 **amount**）中的订单信息。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-187">The OPENXML statement retrieves order information in a three-column rowset (**oid**, **date**, and **amount**) from the XML document.</span></span>  
  
 <span data-ttu-id="9f3ae-188">首先调用 **sp_xml_preparedocument** 存储过程以获得文档句柄。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-188">First, the **sp_xml_preparedocument** stored procedure is called to obtain a document handle.</span></span> <span data-ttu-id="9f3ae-189">此文档句柄传递给 OPENXML。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-189">This document handle is passed to OPENXML.</span></span>  
  
 <span data-ttu-id="9f3ae-190">OPENXML 语句说明了以下信息：</span><span class="sxs-lookup"><span data-stu-id="9f3ae-190">The OPENXML statement illustrates the following:</span></span>  
  
-   <span data-ttu-id="9f3ae-191">*rowpattern* (/root/Customer/Order) 标识要处理的 <`Order`> 节点。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-191">*rowpattern* (/root/Customer/Order) identifies the <`Order`> nodes to process.</span></span>  
  
-   <span data-ttu-id="9f3ae-192">在 WITH 子句中没有 *SchemaDeclaration* 。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-192">There is no *SchemaDeclaration* in the WITH clause.</span></span> <span data-ttu-id="9f3ae-193">而是指定了一个表名。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-193">Instead, a table name is specified.</span></span> <span data-ttu-id="9f3ae-194">因此，表架构将用作行集架构。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-194">Therefore, the table schema is used as the rowset schema.</span></span>  
  
-   <span data-ttu-id="9f3ae-195">*flags* 参数值设置为 **1** ，表示以属性为中心的映射。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-195">The *flags* parameter value is set to **1** and indicates attribute-centric mapping.</span></span> <span data-ttu-id="9f3ae-196">因此， *rowpattern*所标识的元素属性将映射到同名的行集列。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-196">Therefore, attributes of the elements, identified by *rowpattern*, map to the rowset columns with the same name.</span></span>  
  
 <span data-ttu-id="9f3ae-197">SELECT 语句随后将检索 OPENXML 所提供的行集中的所有列。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-197">The SELECT statement then retrieves all the columns in the rowset provided by OPENXML.</span></span>  
  
```  
-- Create a test table. This table schema is used by OPENXML as the  
-- rowset schema.  
CREATE TABLE T1(oid char(5), date datetime, amount float)  
GO  
DECLARE @docHandle int  
DECLARE @xmlDocument nvarchar(1000)  
-- Sample XML document  
SET @xmlDocument =N'<root>  
  <Customer cid= "C1" name="Janine" city="Issaquah">  
      <Order oid="O1" date="1/20/1996" amount="3.5" />  
      <Order oid="O2" date="4/30/1997" amount="13.4">Customer was very   
             satisfied</Order>  
   </Customer>  
   <Customer cid="C2" name="Ursula" city="Oelde" >  
      <Order oid="O3" date="7/14/1999" amount="100" note="Wrap it blue   
             white red">  
          <Urgency>Important</Urgency>  
      </Order>  
      <Order oid="O4" date="1/20/1996" amount="10000"/>  
   </Customer>  
</root>'  
--Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @docHandle OUTPUT, @xmlDocument  
  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@docHandle, '/root/Customer/Order', 1)  
     WITH T1  
EXEC sp_xml_removedocument @docHandle  
```  
  
 <span data-ttu-id="9f3ae-198">结果如下：</span><span class="sxs-lookup"><span data-stu-id="9f3ae-198">This is the result:</span></span>  
  
```  
oid   date                        amount  
----- --------------------------- ----------  
O1    1996-01-20 00:00:00.000     3.5  
O2    1997-04-30 00:00:00.000     13.4  
O3    1999-07-14 00:00:00.000     100.0  
O4    1996-01-20 00:00:00.000     10000.0  
```  
  
### <a name="f-obtaining-the-result-in-an-edge-table-format"></a><span data-ttu-id="9f3ae-199">F.</span><span class="sxs-lookup"><span data-stu-id="9f3ae-199">F.</span></span> <span data-ttu-id="9f3ae-200">获得边缘表格式的结果</span><span class="sxs-lookup"><span data-stu-id="9f3ae-200">Obtaining the result in an edge table format</span></span>  
 <span data-ttu-id="9f3ae-201">在下例中，在 OPENXML 语句中未指定 WITH 子句。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-201">In this example, the WITH clause is not specified in the OPENXML statement.</span></span> <span data-ttu-id="9f3ae-202">因此，OPENXML 所生成的行集具有边缘表格式。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-202">As a result, the rowset generated by OPENXML has an edge table format.</span></span> <span data-ttu-id="9f3ae-203">SELECT 语句将返回边缘表中的所有列。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-203">The SELECT statement returns all the columns in the edge table.</span></span>  
  
 <span data-ttu-id="9f3ae-204">示例中的示例 XML 文档由 <`Customer`>、<`Order`> 和 <`OrderDetail`> 元素组成。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-204">The sample XML document in the example is made up of the <`Customer`>, <`Order`>, and <`OrderDetail`> elements.</span></span>  
  
 <span data-ttu-id="9f3ae-205">首先调用 **sp_xml_preparedocument** 存储过程以获得文档句柄。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-205">First, the **sp_xml_preparedocument** stored procedure is called to obtain a document handle.</span></span> <span data-ttu-id="9f3ae-206">此文档句柄传递给 OPENXML。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-206">This document handle is passed to OPENXML.</span></span>  
  
 <span data-ttu-id="9f3ae-207">OPENXML 语句说明了以下信息：</span><span class="sxs-lookup"><span data-stu-id="9f3ae-207">The OPENXML statement illustrates the following:</span></span>  
  
-   <span data-ttu-id="9f3ae-208">*rowpattern* (/ROOT/Customer) 标识要处理的 <`Customer`> 节点。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-208">*rowpattern* (/ROOT/Customer) identifies the <`Customer`> nodes to process.</span></span>  
  
-   <span data-ttu-id="9f3ae-209">不带 WITH 子句。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-209">The WITH clause is not provided.</span></span> <span data-ttu-id="9f3ae-210">因此，OPENXML 将以边缘表格式返回行集。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-210">Therefore, OPENXML returns the rowset in an edge table format.</span></span>  
  
 <span data-ttu-id="9f3ae-211">继而，SELECT 语句将检索边缘表中的所有列。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-211">The SELECT statement then retrieves all the columns in the edge table.</span></span>  
  
```  
DECLARE @docHandle int  
DECLARE @xmlDocument nvarchar(1000)  
SET @xmlDocument = N'<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order CustomerID="VINET" EmployeeID="5" OrderDate=  
           "1996-07-04T00:00:00">  
      <OrderDetail OrderID="10248" ProductID="11" Quantity="12"/>  
      <OrderDetail OrderID="10248" ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order CustomerID="LILAS" EmployeeID="3" OrderDate=  
           "1996-08-16T00:00:00">  
      <OrderDetail OrderID="10283" ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>'  
--Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @docHandle OUTPUT, @xmlDocument  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@docHandle, '/ROOT/Customer')  
  
EXEC sp_xml_removedocument @docHandle  
```  
  
 <span data-ttu-id="9f3ae-212">结果作为边缘表返回。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-212">The result is returned as an edge table.</span></span> <span data-ttu-id="9f3ae-213">您可以对边缘表编写查询以获得信息。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-213">You can write queries against the edge table to obtain information.</span></span> <span data-ttu-id="9f3ae-214">例如：</span><span class="sxs-lookup"><span data-stu-id="9f3ae-214">For example:</span></span>  
  
-   <span data-ttu-id="9f3ae-215">下面的查询返回文档中的 **Customer** 节点数。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-215">The following query returns the number of **Customer** nodes in the document.</span></span> <span data-ttu-id="9f3ae-216">因为未指定 WITH 子句，所以 OPENXML 将返回边缘表。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-216">Because the WITH clause is not specified, OPENXML returns an edge table.</span></span> <span data-ttu-id="9f3ae-217">SELECT 语句将查询此边缘表。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-217">The SELECT statement queries the edge table.</span></span>  
  
    ```  
    SELECT count(*)  
    FROM OPENXML(@docHandle, '/')  
    WHERE localname = 'Customer'  
    ```  
  
-   <span data-ttu-id="9f3ae-218">以下查询返回元素类型的 XML 节点的本地名称。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-218">The following query returns the local names of XML nodes of element type.</span></span>  
  
    ```  
    SELECT distinct localname   
    FROM OPENXML(@docHandle, '/')   
    WHERE nodetype = 1   
    ORDER BY localname  
    ```  
  
### <a name="g-specifying-rowpattern-ending-with-an-attribute"></a><span data-ttu-id="9f3ae-219">G.</span><span class="sxs-lookup"><span data-stu-id="9f3ae-219">G.</span></span> <span data-ttu-id="9f3ae-220">指定以属性结束的 rowpattern</span><span class="sxs-lookup"><span data-stu-id="9f3ae-220">Specifying rowpattern ending with an attribute</span></span>  
 <span data-ttu-id="9f3ae-221">此示例中的 XML 文档由 <`Customer`>、<`Order`> 和 <`OrderDetail`> 元素组成。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-221">The XML document in this example is made up of the <`Customer`>, <`Order`>, and <`OrderDetail`> elements.</span></span> <span data-ttu-id="9f3ae-222">OPENXML 语句从 XML 文档中检索三列行集（**ProductID**、 **Quantity**和 **OrderID**）中的订单详细信息。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-222">The OPENXML statement retrieves information about the order details in a three-column rowset (**ProductID**, **Quantity**, and **OrderID**) from the XML document.</span></span>  
  
 <span data-ttu-id="9f3ae-223">首先调用 **sp_xml_preparedocument** 存储过程以获得文档句柄。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-223">First, the **sp_xml_preparedocument** is called to obtain a document handle.</span></span> <span data-ttu-id="9f3ae-224">此文档句柄传递给 OPENXML。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-224">This document handle is passed to OPENXML.</span></span>  
  
 <span data-ttu-id="9f3ae-225">OPENXML 语句说明了以下信息：</span><span class="sxs-lookup"><span data-stu-id="9f3ae-225">The OPENXML statement illustrates the following:</span></span>  
  
-   <span data-ttu-id="9f3ae-226">rowpattern (/ROOT/Customer/Order/OrderDetail/\@ProductID) 以 XML 属性 ProductID 结尾。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-226">*rowpattern* (/ROOT/Customer/Order/OrderDetail/\@ProductID) ends with an XML attribute, **ProductID**.</span></span> <span data-ttu-id="9f3ae-227">在所得到的行集中，为在 XML 文档中选定的每个属性节点都创建一行。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-227">In the resulting rowset, a row is created for each attribute node selected in the XML document.</span></span>  
  
-   <span data-ttu-id="9f3ae-228">在下例中未指定 *flags* 参数。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-228">In this example, the *flags* parameter is not specified.</span></span> <span data-ttu-id="9f3ae-229">相反，由 *ColPattern* 参数指定映射。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-229">Instead, the mappings are specified by the *ColPattern* parameter.</span></span>  
  
 <span data-ttu-id="9f3ae-230">在 WITH 子句的 *SchemaDeclaration* 中，还可以用 *ColName* 和 *ColType* 参数指定 *ColPattern* 。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-230">In *SchemaDeclaration* in the WITH clause, *ColPattern* is also specified with the *ColName* and *ColType* parameters.</span></span> <span data-ttu-id="9f3ae-231">可选的 *ColPattern* 是指定的 XPath 模式，用以表示以下内容：</span><span class="sxs-lookup"><span data-stu-id="9f3ae-231">The optional *ColPattern* is the XPath pattern specified to indicate the following:</span></span>  
  
-   <span data-ttu-id="9f3ae-232">在行集中为**ProdID**列指定为 *ColPattern* 的 XPath 模式 ( **.** ) 将标识上下文节点（当前节点）。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-232">The XPath pattern (**.**) specified as *ColPattern* for the **ProdID** column in the rowset identifies the context node, current node.</span></span> <span data-ttu-id="9f3ae-233">按照指定的 *rowpattern*，它是 <`OrderDetail`> 元素的 **ProductID** 属性。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-233">As per the *rowpattern* specified, it is the **ProductID** attribute of the <`OrderDetail`> element.</span></span>  
  
-   <span data-ttu-id="9f3ae-234">为行集中的 Qty 列指定的 ColPattern（即 ../\@Quantity）标识上下文节点 \<ProductID> 的父节点 <`OrderDetail`> 的 Quantity 属性。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-234">The *ColPattern*, **../\@Quantity**, specified for the **Qty** column in the rowset identifies the **Quantity** attribute of the parent, <`OrderDetail`>, node of the context node, \<ProductID>.</span></span>  
  
-   <span data-ttu-id="9f3ae-235">同样，为行集中的 OID 列指定的 ColPattern（即 ../../\@OrderID）标识上下文节点的父节点的父级 <`Order`> 的 OrderID 属性。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-235">Similarly, the *ColPattern*, **../../\@OrderID**, specified for the **OID** column in the rowset identifies the **OrderID** attribute of the parent, <`Order`>, of the parent node of the context node.</span></span> <span data-ttu-id="9f3ae-236">该父节点是 <`OrderDetail`>，上下文节点是 <`ProductID`>。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-236">The parent node is <`OrderDetail`>, and the context node is <`ProductID`>.</span></span>  
  
 <span data-ttu-id="9f3ae-237">SELECT 语句随后将检索 OPENXML 所提供的行集中的所有列。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-237">The SELECT statement then retrieves all the columns in the rowset provided by OPENXML.</span></span>  
  
```  
DECLARE @docHandle int  
DECLARE @xmlDocument nvarchar(1000)  
--Sample XML document  
SET @xmlDocument =N'<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order OrderID="10248" CustomerID="VINET" EmployeeID="5" OrderDate=  
           "1996-07-04T00:00:00">  
      <OrderDetail ProductID="11" Quantity="12"/>  
      <OrderDetail ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order OrderID="10283" CustomerID="LILAS" EmployeeID="3" OrderDate=  
           "1996-08-16T00:00:00">  
      <OrderDetail ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @docHandle OUTPUT, @xmlDocument  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@docHandle, '/ROOT/Customer/Order/OrderDetail/@ProductID')  
       WITH ( ProdID  int '.',  
              Qty     int '../@Quantity',  
              OID     int '../../@OrderID')  
EXEC sp_xml_removedocument @docHandle  
```  
  
 <span data-ttu-id="9f3ae-238">结果如下：</span><span class="sxs-lookup"><span data-stu-id="9f3ae-238">This is the result:</span></span>  
  
```  
ProdID      Qty         OID  
----------- ----------- -------   
11          12          10248  
42          10          10248  
72          3           10283  
```  
  
### <a name="h-specifying-an-xml-document-that-has-multiple-text-nodes"></a><span data-ttu-id="9f3ae-239">H.</span><span class="sxs-lookup"><span data-stu-id="9f3ae-239">H.</span></span> <span data-ttu-id="9f3ae-240">指定具有多个文本节点的 XML 文档</span><span class="sxs-lookup"><span data-stu-id="9f3ae-240">Specifying an XML document that has multiple text nodes</span></span>  
 <span data-ttu-id="9f3ae-241">如果在 XML 文档中有多个文本节点，则包含 *ColPattern*, **text()** 的 SELECT 语句只返回第一个文本节点，而不是返回所有节点。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-241">If you have multiple text nodes in an XML document, a SELECT statement with a *ColPattern*, **text()**, returns only the first text node, instead of all of them.</span></span> <span data-ttu-id="9f3ae-242">例如：</span><span class="sxs-lookup"><span data-stu-id="9f3ae-242">For example:</span></span>  
  
```  
DECLARE @h int  
EXEC sp_xml_preparedocument @h OUTPUT,  
         N'<root xmlns:a="urn:1">  
           <a:Elem abar="asdf">  
             T<a>a</a>U  
           </a:Elem>  
         </root>',  
         '<ns xmlns:b="urn:1" />'  
  
SELECT * FROM openxml(@h, '/root/b:Elem')  
      WITH (Col1 varchar(20) 'text()')  
EXEC sp_xml_removedocument @h  
```  
  
 <span data-ttu-id="9f3ae-243">SELECT 语句返回 **T** 作为结果，而不是返回 **TaU**。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-243">The SELECT statement returns **T** as the result, and not **TaU**.</span></span>  
  
### <a name="i-specifying-the-xml-data-type-in-the-with-clause"></a><span data-ttu-id="9f3ae-244">I.</span><span class="sxs-lookup"><span data-stu-id="9f3ae-244">I.</span></span> <span data-ttu-id="9f3ae-245">在 WITH 子句中指定 xml 数据类型</span><span class="sxs-lookup"><span data-stu-id="9f3ae-245">Specifying the xml data type in the WITH clause</span></span>  
 <span data-ttu-id="9f3ae-246">在 WITH 子句中，映射到 **xml** 数据类型列的列模式（不论是类型化的还是非类型化的）必须返回一个空序列，或者元素、处理指令、文本节点和注释的序列。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-246">In the WITH clause, a column pattern that is mapped to the **xml** data type column, whether typed or untyped, must return either an empty sequence or a sequence of elements, processing instructions, text nodes, and comments.</span></span> <span data-ttu-id="9f3ae-247">数据将转换为 **xml** 数据类型。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-247">The data is cast to an **xml** data type.</span></span>  
  
 <span data-ttu-id="9f3ae-248">在下例中，WITH 子句中的表架构声明包括 **xml** 类型列。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-248">In the following example, the table schema declaration in the WITH clause includes **xml** type columns.</span></span>  
  
```  
DECLARE @h int  
DECLARE @x xml  
set @x = '<Root>  
  <row id="1"><lname>Duffy</lname>  
   <Address>  
            <Street>111 Maple</Street>  
            <City>Seattle</City>  
   </Address>  
  </row>  
  <row id="2"><lname>Wang</lname>  
   <Address>  
            <Street>222 Pine</Street>  
            <City>Bothell</City>  
   </Address>  
  </row>  
</Root>'  
  
EXEC sp_xml_preparedocument @h output, @x  
SELECT *  
FROM   OPENXML (@h, '/Root/row', 10)  
      WITH (id int '@id',  
  
            lname    varchar(30),  
            xmlname  xml 'lname',  
            OverFlow xml '@mp:xmltext')  
EXEC sp_xml_removedocument @h  
```  
  
 <span data-ttu-id="9f3ae-249">具体而言，是将 xml 类型变量 (\@x) 传递给 sp_xml_preparedocument() 函数。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-249">Specifically, you are passing an **xml** type variable (\@x) to the **sp_xml_preparedocument()** function.</span></span>  
  
 <span data-ttu-id="9f3ae-250">结果如下：</span><span class="sxs-lookup"><span data-stu-id="9f3ae-250">This is the result:</span></span>  
  
```  
id  lname   xmlname                   OverFlow  
--- ------- ------------------------------ -------------------------------  
1   Duffy   <lname>Duffy</lname>  <row><Address>  
                                   <Street>111 Maple</Street>  
                                   <City>Seattle</City>  
                                  </Address></row>  
2   Wang    <lname>Wang</lname>   <row><Address>  
                                    <Street>222 Pine</Street>  
                                    <City>Bothell</City>  
                                   </Address></row>  
```  
  
 <span data-ttu-id="9f3ae-251">请注意结果中的以下内容：</span><span class="sxs-lookup"><span data-stu-id="9f3ae-251">Note the following from the result:</span></span>  
  
-   <span data-ttu-id="9f3ae-252">对于 **varchar(30)** 类型的 **lname** 列，从对应的 <`lname`> 元素检索它的值。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-252">For the **lname** column of **varchar(30)** type, its value is retrieved from the corresponding <`lname`> element.</span></span>  
  
-   <span data-ttu-id="9f3ae-253">对于 **xml** 类型的 **xmlname** 列，返回相同的名称元素作为它的值。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-253">For the **xmlname** column of **xml** type, the same name element is returned as its value.</span></span>  
  
-   <span data-ttu-id="9f3ae-254">标志设置为 10。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-254">The flag is set to 10.</span></span> <span data-ttu-id="9f3ae-255">10 表示 2 + 8，其中 2 表示以元素为中心的映射，8 表示应该仅将未用完的 XML 数据添加到 WITH 子句中定义的 OverFlow 列。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-255">The 10 means 2 + 8, where 2 indicates element-centric mapping and 8 indicates that only unconsumed XML data should be added to the OverFlow column defined in the WITH clause.</span></span> <span data-ttu-id="9f3ae-256">如果将标志设置为 2，则整个 XML 文档将复制到 WITH 子句中指定的 OverFlow 列。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-256">If you set the flag to 2, the whole XML document is copied to the OverFlow column that is specified in the WITH clause.</span></span>  
  
-   <span data-ttu-id="9f3ae-257">如果 WITH 子句中的列是类型化的 XML 列并且 XML 实例不符合架构，将返回错误。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-257">In case the column in the WITH clause is a typed XML column and the XML instance does not confirm to the schema, an error is returned.</span></span>  
  
### <a name="j-retrieving-individual-values-from-multivalued-attributes"></a><span data-ttu-id="9f3ae-258">J.</span><span class="sxs-lookup"><span data-stu-id="9f3ae-258">J.</span></span> <span data-ttu-id="9f3ae-259">从多值属性中检索单值</span><span class="sxs-lookup"><span data-stu-id="9f3ae-259">Retrieving individual values from multivalued attributes</span></span>  
 <span data-ttu-id="9f3ae-260">XML 文档会含有多值属性。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-260">An XML document can have attributes that are multivalued.</span></span> <span data-ttu-id="9f3ae-261">例如， **IDREFS** 属性可以是多值属性。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-261">For example, the **IDREFS** attribute can be multivalued.</span></span> <span data-ttu-id="9f3ae-262">在 XML 文档内，多值属性值被指定为一个字符串，并用空格分隔值。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-262">In an XML document, the multivalued attribute values are specified as a string, with the values separated by a space.</span></span> <span data-ttu-id="9f3ae-263">在以下 XML 文档中，\<Student> 元素的 attends 属性与 \<Class> 的 attendedBy 属性都是多值属性。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-263">In the following XML document, the **attends** attribute of the \<Student> element and the **attendedBy** attribute of \<Class> are multivalued.</span></span> <span data-ttu-id="9f3ae-264">从多值 XML 属性中检索单值并将每个值存储到数据库中的不同行中，这要求额外的工作。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-264">Retrieving individual values from a multivalued XML attribute and storing each value in a separate row in the database requires additional work.</span></span> <span data-ttu-id="9f3ae-265">下例显示了此过程。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-265">This example shows the process.</span></span>  
  
 <span data-ttu-id="9f3ae-266">此示例 XML 文档由以下元素组成：</span><span class="sxs-lookup"><span data-stu-id="9f3ae-266">This sample XML document is made up of the following elements:</span></span>  
  
-   \<Student>  
  
     <span data-ttu-id="9f3ae-267">**id** （学生 ID）、 **name**和 **attends** 属性。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-267">The **id** (student ID), **name**, and **attends** attributes.</span></span> <span data-ttu-id="9f3ae-268">**attends** 属性是多值属性。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-268">The **attends** attribute is a multivalued attribute.</span></span>  
  
-   \<Class>  
  
     <span data-ttu-id="9f3ae-269">**id** （班级 ID）、 **name**和 **attendedBy** 属性。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-269">The **id** (class ID), **name**, and **attendedBy** attributes.</span></span> <span data-ttu-id="9f3ae-270">**attendedBy** 属性是多值属性。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-270">The **attendedBy** attribute is a multivalued attribute.</span></span>  
  
 <span data-ttu-id="9f3ae-271">\<Student> 中的 attends 属性和 \<Class> 中的 attendedBy 属性表示 Student 表与 Class 表之间的 m:n 关系。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-271">The **attends** attribute in \<Student> and the **attendedBy** attribute in \<Class> represent a **m:n** relationship between the Student and Class tables.</span></span> <span data-ttu-id="9f3ae-272">一个学生可在很多班上课，而一个班也可有很多学生。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-272">A student can take many classes and a class can have many students.</span></span>  
  
 <span data-ttu-id="9f3ae-273">假设希望拆分此文档，并将它保存到下列数据库中：</span><span class="sxs-lookup"><span data-stu-id="9f3ae-273">Assume that you want to shred this document and save it in the database as shown in the following:</span></span>  
  
-   <span data-ttu-id="9f3ae-274">将 \<Student> 数据保存到 Students 表中。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-274">Save the \<Student> data in the Students table.</span></span>  
  
-   <span data-ttu-id="9f3ae-275">将 \<Class> 数据保存到 Courses 表中。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-275">Save the \<Class> data in the Courses table.</span></span>  
  
-   <span data-ttu-id="9f3ae-276">将 Student 与 Class 之间的 **m:n** 关系数据保存到 CourseAttendence 表中。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-276">Save the **m:n** relationship data, between Student and Class, in the CourseAttendence table.</span></span> <span data-ttu-id="9f3ae-277">提取这些值需要做额外的工作。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-277">Additional work is required to extract the values.</span></span> <span data-ttu-id="9f3ae-278">若要检索该信息并将其存储到表中，请使用下列存储过程：</span><span class="sxs-lookup"><span data-stu-id="9f3ae-278">To retrieve this information and store it in the table, use these stored procedures:</span></span>  
  
    -   <span data-ttu-id="9f3ae-279">**Insert_Idrefs_Values**</span><span class="sxs-lookup"><span data-stu-id="9f3ae-279">**Insert_Idrefs_Values**</span></span>  
  
         <span data-ttu-id="9f3ae-280">将课程 ID 和学生 ID 的值插入 CourseAttendence 表中。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-280">Inserts the values of course ID and student ID in the CourseAttendence table.</span></span>  
  
    -   <span data-ttu-id="9f3ae-281">**Extract_idrefs_values**</span><span class="sxs-lookup"><span data-stu-id="9f3ae-281">**Extract_idrefs_values**</span></span>  
  
         <span data-ttu-id="9f3ae-282">从每个 \<Course> 元素中提取单个学生 ID。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-282">Extracts the individual student IDs from each \<Course> element.</span></span> <span data-ttu-id="9f3ae-283">用边缘表检索这些值。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-283">An edge table is used to retrieve these values.</span></span>  
  
 <span data-ttu-id="9f3ae-284">以下是具体步骤：</span><span class="sxs-lookup"><span data-stu-id="9f3ae-284">Here are the steps:</span></span>  
  
```  
-- Create these tables:  
DROP TABLE CourseAttendance  
DROP TABLE Students  
DROP TABLE Courses  
GO  
CREATE TABLE Students(  
                id   varchar(5) primary key,  
                name varchar(30)  
                )  
GO  
CREATE TABLE Courses(  
               id       varchar(5) primary key,  
               name     varchar(30),  
               taughtBy varchar(5)  
)  
GO  
CREATE TABLE CourseAttendance(  
             id         varchar(5) references Courses(id),  
             attendedBy varchar(5) references Students(id),  
             constraint CourseAttendance_PK primary key (id, attendedBy)  
)  
go  
-- Create these stored procedures:  
DROP PROCEDURE f_idrefs  
GO  
CREATE PROCEDURE f_idrefs  
    @t      varchar(500),  
    @idtab  varchar(50),  
    @id     varchar(5)  
AS  
DECLARE @sp int  
DECLARE @att varchar(5)  
SET @sp = 0  
WHILE (LEN(@t) > 0)  
BEGIN   
    SET @sp = CHARINDEX(' ', @t+ ' ')  
    SET @att = LEFT(@t, @sp-1)  
    EXEC('INSERT INTO '+@idtab+' VALUES ('''+@id+''', '''+@att+''')')  
    SET @t = SUBSTRING(@t+ ' ', @sp+1, LEN(@t)+1-@sp)  
END  
Go  
  
DROP PROCEDURE fill_idrefs  
GO  
CREATE PROCEDURE fill_idrefs   
    @xmldoc     int,  
    @xpath      varchar(100),  
    @from       varchar(50),  
    @to         varchar(50),  
    @idtable    varchar(100)  
AS  
DECLARE @t varchar(500)  
DECLARE @id varchar(5)  
  
/* Temporary edge table */  
SELECT *   
INTO #TempEdge   
FROM OPENXML(@xmldoc, @xpath)  
  
DECLARE fillidrefs_cursor CURSOR FOR  
    SELECT CAST(iv.text AS nvarchar(200)) AS id,  
           CAST(av.text AS nvarchar(4000)) AS refs  
    FROM   #TempEdge c, #TempEdge i,  
           #TempEdge iv, #TempEdge a, #TempEdge av  
    WHERE  c.id = i.parentid  
    AND    UPPER(i.localname) = UPPER(@from)  
    AND    i.id = iv.parentid  
    AND    c.id = a.parentid  
    AND    UPPER(a.localname) = UPPER(@to)  
    AND    a.id = av.parentid  
  
OPEN fillidrefs_cursor  
FETCH NEXT FROM fillidrefs_cursor INTO @id, @t  
WHILE (@@FETCH_STATUS <> -1)  
BEGIN  
    IF (@@FETCH_STATUS <> -2)  
    BEGIN  
        execute f_idrefs @t, @idtable, @id  
    END  
    FETCH NEXT FROM fillidrefs_cursor INTO @id, @t  
END  
CLOSE fillidrefs_cursor  
DEALLOCATE fillidrefs_cursor  
Go  
-- This is the sample document that is shredded and the data is stored in the preceding tables.  
DECLARE @h int  
EXECUTE sp_xml_preparedocument @h OUTPUT, N'<Data>  
  <Student id = "s1" name = "Student1"  attends = "c1 c3 c6"  />  
  <Student id = "s2" name = "Student2"  attends = "c2 c4" />  
  <Student id = "s3" name = "Student3"  attends = "c2 c4 c6" />  
  <Student id = "s4" name = "Student4"  attends = "c1 c3 c5" />  
  <Student id = "s5" name = "Student5"  attends = "c1 c3 c5 c6" />  
  <Student id = "s6" name = "Student6" />  
  
  <Class id = "c1" name = "Intro to Programming"   
         attendedBy = "s1 s4 s5" />  
  <Class id = "c2" name = "Databases"   
         attendedBy = "s2 s3" />  
  <Class id = "c3" name = "Operating Systems"   
         attendedBy = "s1 s4 s5" />  
  <Class id = "c4" name = "Networks" attendedBy = "s2 s3" />  
  <Class id = "c5" name = "Algorithms and Graphs"   
         attendedBy =  "s4 s5"/>  
  <Class id = "c6" name = "Power and Pragmatism"   
         attendedBy = "s1 s3 s5" />  
</Data>'  
  
INSERT INTO Students SELECT * FROM OPENXML(@h, '//Student') WITH Students  
  
INSERT INTO Courses SELECT * FROM OPENXML(@h, '//Class') WITH Courses  
/* Using the edge table */  
EXECUTE fill_idrefs @h, '//Class', 'id', 'attendedby', 'CourseAttendance'  
  
SELECT * FROM Students  
SELECT * FROM Courses  
SELECT * FROM CourseAttendance  
  
EXECUTE sp_xml_removedocument @h  
```  
  
### <a name="k-retrieving-binary-from-base64-encoded-data-in-xml"></a><span data-ttu-id="9f3ae-285">K.</span><span class="sxs-lookup"><span data-stu-id="9f3ae-285">K.</span></span> <span data-ttu-id="9f3ae-286">从 XML 中的 base64 编码数据中检索二进制数据</span><span class="sxs-lookup"><span data-stu-id="9f3ae-286">Retrieving binary from base64 encoded data in XML</span></span>  
 <span data-ttu-id="9f3ae-287">二进制数据经常包括在使用 base64 编码的 XML 中。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-287">Binary data is frequently included in XML using base64 encoding.</span></span> <span data-ttu-id="9f3ae-288">当使用 OPENXML 拆分此 XML 时，将接收到 base64 编码数据。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-288">When you shred this XML by using OPENXML, you receive the base64 encoded data.</span></span> <span data-ttu-id="9f3ae-289">本示例说明如何将 base64 编码数据转换回二进制。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-289">This example shows how you can convert the base64 encoded data back to binary.</span></span>  
  
-   <span data-ttu-id="9f3ae-290">创建包含示例二进制数据的表。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-290">Create a table with sample binary data.</span></span>  
  
-   <span data-ttu-id="9f3ae-291">使用 FOR XML 查询和 BINARY BASE64 选项来构造将二进制数据按照 base64 进行编码的 XML。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-291">Use a FOR XML query and the BINARY BASE64 option to construct XML that has the binary data encoded as base64.</span></span>  
  
-   <span data-ttu-id="9f3ae-292">使用 OPENXML 拆分 XML。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-292">Shred the XML by using OPENXML.</span></span> <span data-ttu-id="9f3ae-293">OPENXML 返回的数据将是 base64 编码的数据。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-293">The data returned by OPENXML will be base64 encoded data.</span></span> <span data-ttu-id="9f3ae-294">接下来，调用 .value 函数将其转换回二进制。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-294">Next, call the .value function to convert it back to binary.</span></span>  
  
```  
CREATE TABLE T (Col1 int primary key, Col2 varbinary(100))  
go  
-- Insert sample binary data  
INSERT T VALUES(1, 0x1234567890)   
go  
 -- Create test XML document that has base64 encoded binary data (use FOR XML query and specify BINARY BASE64 option)  
SELECT * FROM T  
FOR XML AUTO, BINARY BASE64  
go  
-- result  
-- <T Col1="1" Col2="EjRWeJA="/>  
  
-- Now shredd the sample XML using OPENXML.   
-- Call the .value function to convert   
-- the base64 encoded data returned by OPENXML to binary.  
DECLARE @h int ;  
EXEC sp_xml_preparedocument @h OUTPUT, '<T Col1="1" Col2="EjRWeJA="/>' ;  
SELECT Col1,   
CAST('<binary>' + Col2 + '</binary>' AS XML).value('.', 'varbinary(max)') AS BinaryCol   
FROM openxml(@h, '/T')   
WITH (Col1 integer, Col2 varchar(max)) ;  
EXEC sp_xml_removedocument @h ;  
GO  
```  
  
 结果如下： <span data-ttu-id="9f3ae-296">返回的二进制数据是表 T 的原始二进制数据。</span><span class="sxs-lookup"><span data-stu-id="9f3ae-296">The binary data returned is the original binary data in table T.</span></span>  
  
```  
Col1        BinaryCol  
----------- ---------------------  
1           0x1234567890  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f3ae-297">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9f3ae-297">See Also</span></span>  
 <span data-ttu-id="9f3ae-298">[sp_xml_preparedocument (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9f3ae-298">[sp_xml_preparedocument &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql) </span></span>  
 <span data-ttu-id="9f3ae-299">[sp_xml_removedocument (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-xml-removedocument-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9f3ae-299">[sp_xml_removedocument &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-xml-removedocument-transact-sql) </span></span>  
 <span data-ttu-id="9f3ae-300">[OPENXML (Transact-SQL)](/sql/t-sql/functions/openxml-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9f3ae-300">[OPENXML &#40;Transact-SQL&#41;](/sql/t-sql/functions/openxml-transact-sql) </span></span>  
 [<span data-ttu-id="9f3ae-301">OPENXML (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9f3ae-301">OPENXML &#40;SQL Server&#41;</span></span>](openxml-sql-server.md)  
  
  
