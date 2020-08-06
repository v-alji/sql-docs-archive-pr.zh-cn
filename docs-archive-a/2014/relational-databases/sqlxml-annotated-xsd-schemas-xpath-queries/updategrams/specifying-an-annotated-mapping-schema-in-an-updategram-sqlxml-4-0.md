---
title: 在 Updategram 中指定带批注的映射架构 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, updategrams
- data types [SQLXML], mapping schema in updategrams
- updategrams [SQLXML], annotated mapping schemas
- annotated XDR schemas, updategrams
- inverse attribute
- parent-child relationships [SQLXML]
- mapping-schema attribute
- mapping schema [SQLXML], updategrams
- sql:inverse
ms.assetid: 2e266ed9-4cfb-434a-af55-d0839f64bb9a
author: rothja
ms.author: jroth
ms.openlocfilehash: a181b3081b51cca160709703364c248e495e0214
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588437"
---
# <a name="specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-40"></a><span data-ttu-id="fa46a-102">在 updategram 中指定带批注的映射架构 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="fa46a-102">Specifying an Annotated Mapping Schema in an Updategram (SQLXML 4.0)</span></span>
  <span data-ttu-id="fa46a-103">本主题说明如何使用在 updategram 中指定的映射架构（XSD 或 XDR）来处理更新。</span><span class="sxs-lookup"><span data-stu-id="fa46a-103">This topic explains how the mapping schema (XSD or XDR) that is specified in an updategram is used to process the updates.</span></span> <span data-ttu-id="fa46a-104">在 updategram 中，你可以提供要在将 updategram 中的元素和属性映射到中的表和列时使用的已注释映射架构的名称 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fa46a-104">In an updategram, you can provide the name of an annotated mapping schema to use in mapping the elements and attributes in the updategram to tables and columns in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="fa46a-105">在 updategram 中指定映射架构时，updategram 中指定的元素和属性名称必须映射为该映射架构的元素和属性。</span><span class="sxs-lookup"><span data-stu-id="fa46a-105">When a mapping schema is specified in an updategram, the element and attribute names that are specified in the updategram must map to the elements and attributes in the mapping schema.</span></span>  
  
 <span data-ttu-id="fa46a-106">若要指定映射架构，请使用 `mapping-schema` 元素的属性 **\<sync>** 。</span><span class="sxs-lookup"><span data-stu-id="fa46a-106">To specify a mapping schema, you use the `mapping-schema` attribute of the **\<sync>** element.</span></span> <span data-ttu-id="fa46a-107">以下示例显示两个 updategram：其中一个使用简单映射架构，而另一个使用较复杂的架构。</span><span class="sxs-lookup"><span data-stu-id="fa46a-107">The following examples show two updategrams: one that uses a simple mapping schema, and one that uses a more complex schema.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fa46a-108">本文档假定您熟悉 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的模板和映射架构支持。</span><span class="sxs-lookup"><span data-stu-id="fa46a-108">This documentation assumes that you are familiar with templates and mapping schema support in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="fa46a-109">有关详细信息，请参阅[&#40;SQLXML 4.0&#41;中带批注的 XSD 架构简介](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="fa46a-109">For more information, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md).</span></span> <span data-ttu-id="fa46a-110">对于使用 XDR 的旧版应用程序，请参阅[SQLXML 4.0&#41;中 &#40;弃用的带批注 XDR 架构](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="fa46a-110">For legacy applications that use XDR, see [Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).</span></span>  
  
## <a name="dealing-with-data-types"></a><span data-ttu-id="fa46a-111">处理数据类型</span><span class="sxs-lookup"><span data-stu-id="fa46a-111">Dealing with Data Types</span></span>  
 <span data-ttu-id="fa46a-112">如果架构 `image` 使用) 指定、 `binary` 或 `varbinary` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据类型 (`sql:datatype` 并且未指定 xml 数据类型，则 updategram 将假定 xml 数据类型为 `binary base 64` 。</span><span class="sxs-lookup"><span data-stu-id="fa46a-112">If the schema specifies the `image`, `binary`, or `varbinary`[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type (by using `sql:datatype`) and does not specify an XML data type, the updategram assumes that the XML data type is `binary base 64`.</span></span> <span data-ttu-id="fa46a-113">如果数据类型为 `bin.base`，则必须显式指定类型（`dt:type=bin.base` 或 `type="xsd:hexBinary"`）。</span><span class="sxs-lookup"><span data-stu-id="fa46a-113">If your data is `bin.base` type, you must explicitly specify the type (`dt:type=bin.base` or `type="xsd:hexBinary"`).</span></span>  
  
 <span data-ttu-id="fa46a-114">如果架构指定了 `dateTime`、`date` 或 `time` XSD 数据类型，则还必须使用 `sql:datatype="dateTime"` 指定对应的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据类型。</span><span class="sxs-lookup"><span data-stu-id="fa46a-114">If the schema specifies the `dateTime`, `date`, or `time` XSD data type, you must also specify the corresponding [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type by using `sql:datatype="dateTime"`.</span></span>  
  
 <span data-ttu-id="fa46a-115">处理类型的参数时 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `money` ，必须在 `sql:datatype="money"` 映射架构中的相应节点上显式指定。</span><span class="sxs-lookup"><span data-stu-id="fa46a-115">When handling parameters of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `money` type, you must explicitly specify `sql:datatype="money"` on the appropriate node in the mapping schema.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="fa46a-116">示例</span><span class="sxs-lookup"><span data-stu-id="fa46a-116">Examples</span></span>  
 <span data-ttu-id="fa46a-117">若要创建使用以下示例的工作示例，必须满足[运行 SQLXML 示例的要求](../../sqlxml/requirements-for-running-sqlxml-examples.md)中指定的要求。</span><span class="sxs-lookup"><span data-stu-id="fa46a-117">To create working samples using the following examples, you must meet the requirements specified in [Requirements for Running SQLXML Examples](../../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-creating-an-updategram-with-a-simple-mapping-schema"></a><span data-ttu-id="fa46a-118">A.</span><span class="sxs-lookup"><span data-stu-id="fa46a-118">A.</span></span> <span data-ttu-id="fa46a-119">创建采用简单映射架构的 Updategram</span><span class="sxs-lookup"><span data-stu-id="fa46a-119">Creating an updategram with a simple mapping schema</span></span>  
 <span data-ttu-id="fa46a-120">以下 XSD 架构 ( # A0) 是将 **\<Customer>** 元素映射到 Customer 表的映射架构：</span><span class="sxs-lookup"><span data-stu-id="fa46a-120">The following XSD schema (SampleSchema.xml) is a mapping schema that maps the **\<Customer>** element to the Sales.Customer table:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
        <xsd:attribute name="CustID"    
                       sql:field="CustomerID"   
                       type="xsd:string" />  
        <xsd:attribute name="RegionID"    
                       sql:field="TerritoryID"    
                       type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="fa46a-121">以下 updategram 在 Sales.Customer 表中插入一条记录，并使用前面的映射架构将此数据正确映射到表。</span><span class="sxs-lookup"><span data-stu-id="fa46a-121">The following updategram inserts a record into the Sales.Customer table and relies on the previous mapping schema to properly map this data to the table.</span></span> <span data-ttu-id="fa46a-122">请注意，updategram 使用架构中定义的相同元素名称 **\<Customer>** 。</span><span class="sxs-lookup"><span data-stu-id="fa46a-122">Notice that the updategram uses the same element name, **\<Customer>**, as defined in the schema.</span></span> <span data-ttu-id="fa46a-123">这是强制性的，因为 updategram 会指定特定的架构。</span><span class="sxs-lookup"><span data-stu-id="fa46a-123">This is mandatory because the updategram specifies a particular schema.</span></span>  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="fa46a-124">测试 updategram</span><span class="sxs-lookup"><span data-stu-id="fa46a-124">To test the updategram</span></span>  
  
1.  <span data-ttu-id="fa46a-125">复制上面的架构代码，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="fa46a-125">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="fa46a-126">将文件另存为 SampleUpdateSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="fa46a-126">Save the file as SampleUpdateSchema.xml.</span></span>  
  
2.  <span data-ttu-id="fa46a-127">复制下面的 updategram 模板，然后将其粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="fa46a-127">Copy the updategram template below and paste it into a text file.</span></span> <span data-ttu-id="fa46a-128">在您保存 SampleUpdateSchema.xml 的相同目录中将文件另存为 SampleUpdategram.xml。</span><span class="sxs-lookup"><span data-stu-id="fa46a-128">Save the file as SampleUpdategram.xml in the same directory where you saved SampleUpdateSchema.xml.</span></span>  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleUpdateSchema.xml">  
        <updg:before>  
          <Customer CustID="1" RegionID="1"  />  
        </updg:before>  
        <updg:after>  
          <Customer CustID="1" RegionID="2" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="fa46a-129">为映射架构 (SampleUpdateSchema.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="fa46a-129">The directory path specified for the mapping schema (SampleUpdateSchema.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="fa46a-130">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="fa46a-130">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\SampleUpdateSchema.xml"  
    ```  
  
3.  <span data-ttu-id="fa46a-131">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="fa46a-131">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="fa46a-132">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="fa46a-132">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="fa46a-133">这是等效的 XDR 架构：</span><span class="sxs-lookup"><span data-stu-id="fa46a-133">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
   <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
         xmlns:dt="urn:schemas-microsoft-com:datatypes"   
         xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
     <ElementType name="Customer" sql:relation="Sales.Customer" >  
       <AttributeType name="CustID" />  
       <AttributeType name="RegionID" />  
  
       <attribute type="CustID" sql:field="CustomerID" />  
       <attribute type="RegionID" sql:field="TerritoryID" />  
     </ElementType>  
   </Schema>   
```  
  
### <a name="b-inserting-a-record-by-using-the-parent-child-relationship-specified-in-the-mapping-schema"></a><span data-ttu-id="fa46a-134">B.</span><span class="sxs-lookup"><span data-stu-id="fa46a-134">B.</span></span> <span data-ttu-id="fa46a-135">使用在映射架构中指定的父子关系插入记录</span><span class="sxs-lookup"><span data-stu-id="fa46a-135">Inserting a record by using the parent-child relationship specified in the mapping schema</span></span>  
 <span data-ttu-id="fa46a-136">架构元素可以相互关联。</span><span class="sxs-lookup"><span data-stu-id="fa46a-136">Schema elements can be related.</span></span> <span data-ttu-id="fa46a-137">**\<sql:relationship>** 元素指定架构元素之间的父子关系。</span><span class="sxs-lookup"><span data-stu-id="fa46a-137">The **\<sql:relationship>** element specifies the parent-child relationship between the schema elements.</span></span> <span data-ttu-id="fa46a-138">此信息用于更新具有主键/外键关系的相应表。</span><span class="sxs-lookup"><span data-stu-id="fa46a-138">This information is used to update corresponding tables that have primary-key/foreign-key relationship.</span></span>  
  
 <span data-ttu-id="fa46a-139">以下映射架构 ( # A0) 包含两个元素 **\<Order>** **\<OD>** ：</span><span class="sxs-lookup"><span data-stu-id="fa46a-139">The following mapping schema (SampleSchema.xml) consists of two elements, **\<Order>** and **\<OD>**:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="OrderOD"  
          parent="Sales.SalesOrderHeader"  
          parent-key="SalesOrderID"  
          child="Sales.SalesOrderDetail"  
          child-key="SalesOrderID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="OD"   
                     sql:relation="Sales.SalesOrderDetail"  
                     sql:relationship="OrderOD" >  
           <xsd:complexType>  
              <xsd:attribute name="SalesOrderID"   type="xsd:integer" />  
              <xsd:attribute name="ProductID" type="xsd:integer" />  
             <xsd:attribute name="UnitPrice"  type="xsd:decimal" />  
             <xsd:attribute name="OrderQty"   type="xsd:integer" />  
             <xsd:attribute name="UnitPriceDiscount"   type="xsd:decimal" />  
  
           </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
        <xsd:attribute name="SalesOrderID"  type="xsd:integer" />  
        <xsd:attribute name="OrderDate"  type="xsd:date" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="fa46a-140">以下 updategram 使用此 XSD 架构为订单43860添加新的订单详细记录 (**\<OD>** 块) 中的元素 **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="fa46a-140">The following updategram uses this XSD schema to add a new order detail record (an **\<OD>** element in the **\<after>** block) for order 43860.</span></span> <span data-ttu-id="fa46a-141">`mapping-schema` 属性用于指定 updategram 中的映射架构。</span><span class="sxs-lookup"><span data-stu-id="fa46a-141">The `mapping-schema` attribute is used to specify the mapping schema in the updategram.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema="SampleUpdateSchema.xml" >  
    <updg:before>  
       <Order SalesOrderID="43860" />  
    </updg:before>  
    <updg:after>  
      <Order SalesOrderID="43860" >  
           <OD ProductID="753" UnitPrice="$10.00"  
               Quantity="5" Discount="0.0" />  
      </Order>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="fa46a-142">测试 updategram</span><span class="sxs-lookup"><span data-stu-id="fa46a-142">To test the updategram</span></span>  
  
1.  <span data-ttu-id="fa46a-143">复制上面的架构代码，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="fa46a-143">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="fa46a-144">将文件另存为 SampleUpdateSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="fa46a-144">Save the file as SampleUpdateSchema.xml.</span></span>  
  
2.  <span data-ttu-id="fa46a-145">复制上面的 Updategram 模板，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="fa46a-145">Copy the updategram template above and paste it into a text file.</span></span> <span data-ttu-id="fa46a-146">在您保存 SampleUpdateSchema.xml 的相同目录中将文件另存为 SampleUpdategram.xml。</span><span class="sxs-lookup"><span data-stu-id="fa46a-146">Save the file as SampleUpdategram.xml in the same directory where you saved SampleUpdateSchema.xml.</span></span>  
  
     <span data-ttu-id="fa46a-147">为映射架构 (SampleUpdateSchema.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="fa46a-147">The directory path specified for the mapping schema (SampleUpdateSchema.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="fa46a-148">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="fa46a-148">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\SampleUpdateSchema.xml"  
    ```  
  
3.  <span data-ttu-id="fa46a-149">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="fa46a-149">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="fa46a-150">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="fa46a-150">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="fa46a-151">这是等效的 XDR 架构：</span><span class="sxs-lookup"><span data-stu-id="fa46a-151">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  
<ElementType name="OD" sql:relation="Sales.SalesOrderDetail" >  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="ProductID" />  
    <AttributeType name="UnitPrice"  dt:type="fixed.14.4" />  
    <AttributeType name="OrderQty" />  
    <AttributeType name="UnitPriceDiscount" />  
  
    <attribute type="SalesOrderID" />  
    <attribute type="ProductID" />  
    <attribute type="UnitPrice" />  
    <attribute type="OrderQty" />  
    <attribute type="UnitPriceDiscount" />  
</ElementType>  
  
<ElementType name="Order" sql:relation="Sales.SalesOrderHeader" >  
    <AttributeType name="CustomerID" />  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="OrderDate" />  
  
    <attribute type="CustomerID" />  
    <attribute type="SalesOrderID" />  
    <attribute type="OrderDate" />  
    <element type="OD" >  
             <sql:relationship   
                   key-relation="Sales.SalesOrderHeader"  
                   key="SalesOrderID"  
                   foreign-key="SalesOrderID"  
                   foreign-relation="Sales.SalesOrderDetail" />  
    </element>  
</ElementType>  
</Schema>  
```  
  
### <a name="c-inserting-a-record-by-using-the-parent-child-relationship-and-inverse-annotation-specified-in-the-xsd-schema"></a><span data-ttu-id="fa46a-152">C.</span><span class="sxs-lookup"><span data-stu-id="fa46a-152">C.</span></span> <span data-ttu-id="fa46a-153">使用在 XSD 架构中指定的父子关系和反转批注插入记录</span><span class="sxs-lookup"><span data-stu-id="fa46a-153">Inserting a record by using the parent-child relationship and inverse annotation specified in the XSD schema</span></span>  
 <span data-ttu-id="fa46a-154">此示例说明 updategram 逻辑如何使用在 XSD 中指定的父子关系来处理更新以及如何使用 `inverse` 批注。</span><span class="sxs-lookup"><span data-stu-id="fa46a-154">This example illustrates how the updategram logic uses the parent-child relationship specified in the XSD to process updates, and how the `inverse` annotation is used.</span></span> <span data-ttu-id="fa46a-155">有关批注的详细信息 `inverse` ，请参阅[在 sql： Relationship 上指定 sql：反向特性 &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="fa46a-155">For more information about the `inverse` annotation, see [Specifying the sql:inverse Attribute on sql:relationship &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="fa46a-156">此示例假设以下表位于**tempdb**数据库中：</span><span class="sxs-lookup"><span data-stu-id="fa46a-156">This example assumes that the following tables are in the **tempdb** database:</span></span>  
  
-   <span data-ttu-id="fa46a-157">`Cust (CustomerID, CompanyName)`，其中 `CustomerID` 为主键。</span><span class="sxs-lookup"><span data-stu-id="fa46a-157">`Cust (CustomerID, CompanyName)`, where `CustomerID` is the primary key</span></span>  
  
-   <span data-ttu-id="fa46a-158">`Ord (OrderID, CustomerID)`，其中 `CustomerID` 是引用 `CustomerID` 表中的 `Cust` 主键的外键。</span><span class="sxs-lookup"><span data-stu-id="fa46a-158">`Ord (OrderID, CustomerID)`, where `CustomerID` is a foreign key that refers to the `CustomerID` primary key in the `Cust` table.</span></span>  
  
 <span data-ttu-id="fa46a-159">updategram 使用以下 XSD 架构将记录插入到 Cust 和 Ord 表中：</span><span class="sxs-lookup"><span data-stu-id="fa46a-159">The updategram uses the following XSD schema to insert records into the Cust and Ord tables :</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
       <sql:relationship name="OrdCust" inverse="true"  
                  parent="Ord"  
                  parent-key="CustomerID"  
                  child-key="CustomerID"  
                  child="Cust"/>  
  </xsd:appinfo>  
</xsd:annotation>  
  
<xsd:element name="Order" sql:relation="Ord">  
  <xsd:complexType>  
    <xsd:sequence>  
      <xsd:element ref="Customer" sql:relationship="OrdCust"/>  
    </xsd:sequence>  
    <xsd:attribute name="OrderID"   type="xsd:int"/>  
    <xsd:attribute name="CustomerID" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:element>  
  
<xsd:element name="Customer" sql:relation="Cust">  
  <xsd:complexType>  
     <xsd:attribute name="CustomerID"  type="xsd:string"/>  
    <xsd:attribute name="CompanyName" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:element>  
  
</xsd:schema>  
```  
  
 <span data-ttu-id="fa46a-160">此示例中的 XSD 架构包含 **\<Customer>** 和 **\<Order>** 元素，它指定两个元素之间的父子关系。</span><span class="sxs-lookup"><span data-stu-id="fa46a-160">The XSD schema in this example has **\<Customer>** and **\<Order>** elements, and it specifies a parent-child relationship between the two elements.</span></span> <span data-ttu-id="fa46a-161">它将标识 **\<Order>** 为父元素和 **\<Customer>** 子元素。</span><span class="sxs-lookup"><span data-stu-id="fa46a-161">It identifies **\<Order>** as the parent element and **\<Customer>** as the child element.</span></span>  
  
 <span data-ttu-id="fa46a-162">updategram 处理逻辑使用父子关系相关信息来确定将记录插入到表中的顺序。</span><span class="sxs-lookup"><span data-stu-id="fa46a-162">The updategram processing logic uses the information about the parent-child relationship to determine the order in which records are inserted into tables.</span></span> <span data-ttu-id="fa46a-163">在此示例中，updategram 逻辑将首先尝试将记录插入到 Ord 表中 (因为 **\<Order>** 是父级) ，然后尝试将记录插入到 "加入" 表中 (因为 **\<Customer>** 是子) 。</span><span class="sxs-lookup"><span data-stu-id="fa46a-163">In this example, the updategram logic first attempts to insert a record into the Ord table (because **\<Order>** is the parent) and then attempts to insert a record into the Cust table (because **\<Customer>** is the child).</span></span> <span data-ttu-id="fa46a-164">但是，鉴于数据库表架构中包含的主键/外键信息，此插入操作将导致在数据库中的外键冲突，继而导致插入失败。</span><span class="sxs-lookup"><span data-stu-id="fa46a-164">However, because of the primary key/foreign key information that is contained in the database table schema, this insert operation causes a foreign key violation in the database and the insert fails.</span></span>  
  
 <span data-ttu-id="fa46a-165">若要指示 updategram 逻辑在更新操作过程中反转父子关系，请 `inverse` 在元素上指定批注 **\<relationship>** 。</span><span class="sxs-lookup"><span data-stu-id="fa46a-165">To instruct the updategram logic to reverse the parent-child relationship during the update operation, the `inverse` annotation is specified on the **\<relationship>** element.</span></span> <span data-ttu-id="fa46a-166">这会导致首先向 Cust 表添加记录，然后再向 Ord 表添加记录，并且该操作将成功。</span><span class="sxs-lookup"><span data-stu-id="fa46a-166">As a result, records are added first in the Cust table and then in the Ord table, and the operation succeeds.</span></span>  
  
 <span data-ttu-id="fa46a-167">以下 updategram 使用指定的 XSD 架构向 Ord 表插入订单 (OrderID=2)，并向 Cust 表插入客户 (CustomerID='AAAAA')：</span><span class="sxs-lookup"><span data-stu-id="fa46a-167">The following updategram inserts an order (OrderID=2) in the Ord table and a customer (CustomerID='AAAAA') in the Cust table by using the specified XSD schema:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema="SampleUpdateSchema.xml" >  
    <updg:before/>  
    <updg:after>  
      <Order OrderID="2" CustomerID="AAAAA" >  
        <Customer CustomerID="AAAAA" CompanyName="AAAAA Company" />  
      </Order>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="fa46a-168">测试 updategram</span><span class="sxs-lookup"><span data-stu-id="fa46a-168">To test the updategram</span></span>  
  
1.  <span data-ttu-id="fa46a-169">在**tempdb**数据库中创建以下表：</span><span class="sxs-lookup"><span data-stu-id="fa46a-169">Create these tables in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Cust(CustomerID varchar(5) primary key,   
                      CompanyName varchar(20))  
    GO  
    CREATE TABLE Ord (OrderID int primary key,   
                      CustomerID varchar(5) references Cust(CustomerID))  
    GO  
    ```  
  
2.  <span data-ttu-id="fa46a-170">复制上面的架构代码，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="fa46a-170">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="fa46a-171">将文件另存为 SampleUpdateSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="fa46a-171">Save the file as SampleUpdateSchema.xml.</span></span>  
  
3.  <span data-ttu-id="fa46a-172">复制上面的 Updategram 模板，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="fa46a-172">Copy the updategram template above and paste it into a text file.</span></span> <span data-ttu-id="fa46a-173">在您保存 SampleUpdateSchema.xml 的相同目录中将文件另存为 SampleUpdategram.xml。</span><span class="sxs-lookup"><span data-stu-id="fa46a-173">Save the file as SampleUpdategram.xml in the same directory where you saved SampleUpdateSchema.xml.</span></span>  
  
     <span data-ttu-id="fa46a-174">为映射架构 (SampleUpdateSchema.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="fa46a-174">The directory path specified for the mapping schema (SampleUpdateSchema.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="fa46a-175">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="fa46a-175">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\SampleUpdateSchema.xml"  
    ```  
  
4.  <span data-ttu-id="fa46a-176">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="fa46a-176">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="fa46a-177">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="fa46a-177">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa46a-178">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fa46a-178">See Also</span></span>  
 [<span data-ttu-id="fa46a-179">&#40;SQLXML 4.0&#41;的 Updategram 安全注意事项</span><span class="sxs-lookup"><span data-stu-id="fa46a-179">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
