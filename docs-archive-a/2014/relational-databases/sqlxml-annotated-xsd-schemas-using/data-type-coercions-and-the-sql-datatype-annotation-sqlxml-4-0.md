---
title: 数据类型强制转换和 sql： datatype 批注 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping data types [SQLXML]
- type attribute
- sql:datatype
- data types [SQLXML], converting
- annotated XSD schemas, mapping data types
- xsd:type
- datatype annotation
- converting data types [SQLXML]
- data types [SQLXML], mapping data types
- XSD schemas [SQLXML], mapping data types
ms.assetid: db192105-e8aa-4392-b812-9d727918c005
author: rothja
ms.author: jroth
ms.openlocfilehash: 22f1b0af93e3b596d74bc107ab6947b9855a2cf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586602"
---
# <a name="data-type-coercions-and-the-sqldatatype-annotation-sqlxml-40"></a><span data-ttu-id="c7f67-102">数据类型强制和 sql:datatype 批注 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="c7f67-102">Data Type Coercions and the sql:datatype Annotation (SQLXML 4.0)</span></span>
  <span data-ttu-id="c7f67-103">在 XSD 架构中，`xsd:type` 属性指定元素或属性的 XSD 数据类型。</span><span class="sxs-lookup"><span data-stu-id="c7f67-103">In an XSD schema, the `xsd:type` attribute specifies the XSD data type of an element or attribute.</span></span> <span data-ttu-id="c7f67-104">在 XSD 架构用于从数据库中提取数据时，指定的数据类型用于将数据格式化。</span><span class="sxs-lookup"><span data-stu-id="c7f67-104">When an XSD schema is used to extract data from the database, the data type specified is used to format the data.</span></span>  
  
 <span data-ttu-id="c7f67-105">除了在架构中指定 XSD 类型之外，还可以使用 `sql:datatype` 批注来指定 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型。</span><span class="sxs-lookup"><span data-stu-id="c7f67-105">In addition to specifying an XSD type in a schema, you can also specify a Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type by using the `sql:datatype` annotation.</span></span> <span data-ttu-id="c7f67-106">`xsd:type` 和 `sql:datatype` 属性控制 XSD 数据类型和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型之间的映射。</span><span class="sxs-lookup"><span data-stu-id="c7f67-106">The `xsd:type` and `sql:datatype` attributes control the mapping between XSD data types and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span>  
  
## <a name="xsdtype-attribute"></a><span data-ttu-id="c7f67-107">xsd:type 属性</span><span class="sxs-lookup"><span data-stu-id="c7f67-107">xsd:type Attribute</span></span>  
 <span data-ttu-id="c7f67-108">可以使用 `xsd:type` 属性指定映射到某列的属性或元素的 XML 数据类型。</span><span class="sxs-lookup"><span data-stu-id="c7f67-108">You can use the `xsd:type` attribute to specify the XML data type of an attribute or element that maps to a column.</span></span> <span data-ttu-id="c7f67-109">`xsd:type` 影响从服务器返回的文档以及执行的 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="c7f67-109">The `xsd:type` affects the document that is returned from the server and also the XPath query that is executed.</span></span> <span data-ttu-id="c7f67-110">针对包含 `xsd:type` 的映射架构执行 XPath 查询时，XPath 使用在处理该查询时指定的数据类型。</span><span class="sxs-lookup"><span data-stu-id="c7f67-110">When an XPath query is executed against a mapping schema that contains `xsd:type`, XPath uses the specified data type when it processes the query.</span></span> <span data-ttu-id="c7f67-111">有关 XPath 使用方式的详细信息 `xsd:type` ，请参阅[将 XSD 数据类型映射到 Xpath 数据类型 &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="c7f67-111">For more information about how XPath uses `xsd:type`, see [Mapping XSD Data Types to XPath Data Types &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="c7f67-112">在返回的文档中，所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型都转换为字符串表示形式。</span><span class="sxs-lookup"><span data-stu-id="c7f67-112">In a returned document, all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types are converted into string representations.</span></span> <span data-ttu-id="c7f67-113">某些数据类型需要其他转换。</span><span class="sxs-lookup"><span data-stu-id="c7f67-113">Some data types require additional conversions.</span></span> <span data-ttu-id="c7f67-114">下表列出用于各种 `xsd:type` 值的转换。</span><span class="sxs-lookup"><span data-stu-id="c7f67-114">The following table lists the conversions that are used for various `xsd:type` values.</span></span>  
  
|<span data-ttu-id="c7f67-115">XSD 数据类型</span><span class="sxs-lookup"><span data-stu-id="c7f67-115">XSD data type</span></span>|<span data-ttu-id="c7f67-116">SQL Server 转换</span><span class="sxs-lookup"><span data-stu-id="c7f67-116">SQL Server conversion</span></span>|  
|-------------------|---------------------------|  
|<span data-ttu-id="c7f67-117">Boolean</span><span class="sxs-lookup"><span data-stu-id="c7f67-117">Boolean</span></span>|<span data-ttu-id="c7f67-118">CONVERT(bit, COLUMN)</span><span class="sxs-lookup"><span data-stu-id="c7f67-118">CONVERT(bit, COLUMN)</span></span>|  
|<span data-ttu-id="c7f67-119">Date</span><span class="sxs-lookup"><span data-stu-id="c7f67-119">Date</span></span>|<span data-ttu-id="c7f67-120">LEFT(CONVERT(nvarchar(4000), COLUMN, 126), 10)</span><span class="sxs-lookup"><span data-stu-id="c7f67-120">LEFT(CONVERT(nvarchar(4000), COLUMN, 126), 10)</span></span>|  
|<span data-ttu-id="c7f67-121">Decimal</span><span class="sxs-lookup"><span data-stu-id="c7f67-121">decimal</span></span>|<span data-ttu-id="c7f67-122">CONVERT(money, COLUMN)</span><span class="sxs-lookup"><span data-stu-id="c7f67-122">CONVERT(money, COLUMN)</span></span>|  
|<span data-ttu-id="c7f67-123">id/idref/idrefs</span><span class="sxs-lookup"><span data-stu-id="c7f67-123">id/idref/idrefs</span></span>|<span data-ttu-id="c7f67-124">id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)</span><span class="sxs-lookup"><span data-stu-id="c7f67-124">id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)</span></span>|  
|<span data-ttu-id="c7f67-125">nmtoken/nmtokens</span><span class="sxs-lookup"><span data-stu-id="c7f67-125">nmtoken/nmtokens</span></span>|<span data-ttu-id="c7f67-126">id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)</span><span class="sxs-lookup"><span data-stu-id="c7f67-126">id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)</span></span>|  
|<span data-ttu-id="c7f67-127">时间</span><span class="sxs-lookup"><span data-stu-id="c7f67-127">Time</span></span>|<span data-ttu-id="c7f67-128">SUBSTRING(CONVERT(nvarchar(4000), COLUMN, 126), 1+CHARINDEX(N'T', CONVERT(nvarchar(4000), COLUMN, 126)), 24)</span><span class="sxs-lookup"><span data-stu-id="c7f67-128">SUBSTRING(CONVERT(nvarchar(4000), COLUMN, 126), 1+CHARINDEX(N'T', CONVERT(nvarchar(4000), COLUMN, 126)), 24)</span></span>|  
|<span data-ttu-id="c7f67-129">所有其他</span><span class="sxs-lookup"><span data-stu-id="c7f67-129">All others</span></span>|<span data-ttu-id="c7f67-130">无其他转换</span><span class="sxs-lookup"><span data-stu-id="c7f67-130">No additional conversion</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="c7f67-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回的某些值可能与使用 `xsd:type` 指定的 XML 数据类型不兼容，这可能是由于无法转换（例如无法将 "XYZ" 转换为 `decimal` 数据类型），或是由于值超出了该数据类型的范围（例如，将 -100000 转换为 `UnsignedShort` XSD 类型）。</span><span class="sxs-lookup"><span data-stu-id="c7f67-131">Some of the values returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might not be compatible with the XML data types that are specified by using `xsd:type`, either because the conversion is not possible (for example, converting "XYZ" to a `decimal` data type) or because the value exceeds the range of that data type (for example, -100000 converted to an `UnsignedShort` XSD type).</span></span> <span data-ttu-id="c7f67-132">不兼容的类型转换可能导致无效的 XML 文档或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误。</span><span class="sxs-lookup"><span data-stu-id="c7f67-132">Incompatible type conversions might result in XML documents that are not valid, or in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] errors.</span></span>  
  
## <a name="mapping-from-sql-server-data-types-to-xsd-data-types"></a><span data-ttu-id="c7f67-133">从 SQL Server 数据类型映射到 XSD 数据类型</span><span class="sxs-lookup"><span data-stu-id="c7f67-133">Mapping from SQL Server Data Types to XSD Data Types</span></span>  
 <span data-ttu-id="c7f67-134">下表显示从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型到 XSD 数据类型的显式映射。</span><span class="sxs-lookup"><span data-stu-id="c7f67-134">The following table shows an obvious mapping from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types to XSD data types.</span></span> <span data-ttu-id="c7f67-135">如果您知道 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 类型，此表将提供可以在 XSD 架构中指定的相应 XSD 类型。</span><span class="sxs-lookup"><span data-stu-id="c7f67-135">If you know the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type, this table provides the corresponding XSD type that you can specify in the XSD schema.</span></span>  
  
|<span data-ttu-id="c7f67-136">SQL Server 数据类型</span><span class="sxs-lookup"><span data-stu-id="c7f67-136">SQL Server data type</span></span>|<span data-ttu-id="c7f67-137">XSD 数据类型</span><span class="sxs-lookup"><span data-stu-id="c7f67-137">XSD data type</span></span>|  
|--------------------------|-------------------|  
|`bigint`|`long`|  
|`binary`|`base64Binary`|  
|`bit`|`boolean`|  
|`char`|`string`|  
|`datetime`|`dateTime`|  
|`decimal`|`decimal`|  
|`float`|`double`|  
|`image`|`base64Binary`|  
|`int`|`int`|  
|`money`|`decimal`|  
|`nchar`|`string`|  
|`ntext`|`string`|  
|`nvarchar`|`string`|  
|`numeric`|`decimal`|  
|`real`|`float`|  
|`smalldatetime`|`dateTime`|  
|`smallint`|`short`|  
|`smallmoney`|`decimal`|  
|`sql_variant`|`string`|  
|`sysname`|`string`|  
|`text`|`string`|  
|`timestamp`|`dateTime`|  
|`tinyint`|`unsignedByte`|  
|`varbinary`|`base64Binary`|  
|`varchar`|`string`|  
|`uniqueidentifier`|`string`|  
  
## <a name="sqldatatype-annotation"></a><span data-ttu-id="c7f67-138">sql:datatype 批注</span><span class="sxs-lookup"><span data-stu-id="c7f67-138">sql:datatype Annotation</span></span>  
 <span data-ttu-id="c7f67-139">`sql:datatype` 批注用于指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型；在以下情况下必须指定此批注：</span><span class="sxs-lookup"><span data-stu-id="c7f67-139">The `sql:datatype` annotation is used to specify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type; this annotation must be specified when:</span></span>  
  
-   <span data-ttu-id="c7f67-140">`dateTime` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 从 XSD `dateTime` 、 `date` 或 `time` 类型大容量加载到列中。</span><span class="sxs-lookup"><span data-stu-id="c7f67-140">You are bulk loading into a `dateTime`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] column from an XSD `dateTime`, `date`, or `time` type.</span></span> <span data-ttu-id="c7f67-141">在这种情况下，必须使用 `sql:datatype="dateTime"` 标识 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列数据类型。</span><span class="sxs-lookup"><span data-stu-id="c7f67-141">In this case, you must identify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] column data type by using `sql:datatype="dateTime"`.</span></span> <span data-ttu-id="c7f67-142">此规则也适用于 updategram。</span><span class="sxs-lookup"><span data-stu-id="c7f67-142">This rule also applies to updategrams.</span></span>  
  
-   <span data-ttu-id="c7f67-143">要大容量加载到类型为的列 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `uniqueidentifier` ，而 XSD 值是包含大括号 ( {and} ) 的 GUID。</span><span class="sxs-lookup"><span data-stu-id="c7f67-143">You are bulk loading into a column of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `uniqueidentifier` type and the XSD value is a GUID that includes braces ({ and }).</span></span> <span data-ttu-id="c7f67-144">指定 `sql:datatype="uniqueidentifier"` 时，在将值插入列之前从值中删除大括号。</span><span class="sxs-lookup"><span data-stu-id="c7f67-144">When you specify `sql:datatype="uniqueidentifier"`, the braces are removed from the value before it is inserted in the column.</span></span> <span data-ttu-id="c7f67-145">如果未指定 `sql:datatype`，将发送包含大括号的值并且插入或更新失败。</span><span class="sxs-lookup"><span data-stu-id="c7f67-145">If `sql:datatype` is not specified, the value is sent with the braces, and the insert or update fails.</span></span>  
  
-   <span data-ttu-id="c7f67-146">XML 数据类型 `base64Binary` 映射到各种 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型（`binary`、`image` 或 `varbinary`）。</span><span class="sxs-lookup"><span data-stu-id="c7f67-146">The XML data type `base64Binary` maps to various [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types (`binary`, `image`, or `varbinary`).</span></span> <span data-ttu-id="c7f67-147">若要将 XML 数据类型 `base64Binary` 映射到特定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型，请使用 `sql:datatype` 批注。</span><span class="sxs-lookup"><span data-stu-id="c7f67-147">To map the XML data type `base64Binary` to a specific [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type, use the `sql:datatype` annotation.</span></span> <span data-ttu-id="c7f67-148">此批注指定属性要映射到的列的显式 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型。</span><span class="sxs-lookup"><span data-stu-id="c7f67-148">This annotation specifies the explicit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type of the column to which the attribute maps.</span></span> <span data-ttu-id="c7f67-149">当正在数据库中存储数据时，这很有用。</span><span class="sxs-lookup"><span data-stu-id="c7f67-149">This is useful when data is being stored in the databases.</span></span> <span data-ttu-id="c7f67-150">通过指定 `sql:datatype` 批注，可以标识显式 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型。</span><span class="sxs-lookup"><span data-stu-id="c7f67-150">By specifying the `sql:datatype` annotation, you can identify the explicit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span>  
  
 <span data-ttu-id="c7f67-151">一般建议在架构中指定 `sql:datatype`。</span><span class="sxs-lookup"><span data-stu-id="c7f67-151">It is generally recommended that you specify `sql:datatype` in the schema.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c7f67-152">示例</span><span class="sxs-lookup"><span data-stu-id="c7f67-152">Examples</span></span>  
 <span data-ttu-id="c7f67-153">若要创建使用以下示例的工作示例，必须满足某些要求。</span><span class="sxs-lookup"><span data-stu-id="c7f67-153">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="c7f67-154">有关详细信息，请参阅[运行 SQLXML 示例的要求](../sqlxml/requirements-for-running-sqlxml-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="c7f67-154">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-xsdtype"></a><span data-ttu-id="c7f67-155">A.</span><span class="sxs-lookup"><span data-stu-id="c7f67-155">A.</span></span> <span data-ttu-id="c7f67-156">指定 xsd:type</span><span class="sxs-lookup"><span data-stu-id="c7f67-156">Specifying xsd:type</span></span>  
 <span data-ttu-id="c7f67-157">此示例显示在架构中使用 `date` 属性指定的 XSD `xsd:type` 类型如何影响生成的 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="c7f67-157">This example shows how an XSD `date` type that is specified by using the `xsd:type` attribute in the schema affects the resulting XML document.</span></span> <span data-ttu-id="c7f67-158">该架构提供 AdventureWorks 数据库中 Sales.SalesOrderHeader 表的 XML 视图。</span><span class="sxs-lookup"><span data-stu-id="c7f67-158">The schema provides an XML view of the Sales.SalesOrderHeader table in the AdventureWorks database.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader">  
     <xsd:complexType>  
       <xsd:attribute name="SalesOrderID" type="xsd:string" />   
       <xsd:attribute name="CustomerID"   type="xsd:string" />   
       <xsd:attribute name="OrderDate"    type="xsd:date" />   
       <xsd:attribute name="DueDate"  />   
       <xsd:attribute name="ShipDate"  type="xsd:time" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="c7f67-159">在该 XSD 架构中，有三个从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回日期值的属性。</span><span class="sxs-lookup"><span data-stu-id="c7f67-159">In this XSD schema, there are three attributes that return a date value from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c7f67-160">当该架构：</span><span class="sxs-lookup"><span data-stu-id="c7f67-160">When the schema:</span></span>  
  
-   <span data-ttu-id="c7f67-161">指定 " `xsd:type=date` **订购**日期" 属性，将显示 "订货日期" 属性返回的值的日期部分 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 **OrderDate**</span><span class="sxs-lookup"><span data-stu-id="c7f67-161">Specifies `xsd:type=date` on the **OrderDate** attribute, the date part of the value returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the **OrderDate** attribute is displayed.</span></span>  
  
-   <span data-ttu-id="c7f67-162">`xsd:type=time`在**ShipDate**特性上指定，将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 显示为**ShipDate**属性返回的值的时间部分。</span><span class="sxs-lookup"><span data-stu-id="c7f67-162">Specifies `xsd:type=time` on the **ShipDate** attribute, the time part of the value that is returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the **ShipDate** attribute is displayed.</span></span>  
  
-   <span data-ttu-id="c7f67-163">未 `xsd:type` 在**DueDate**特性上指定，则将显示返回的相同值 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c7f67-163">Does not specify `xsd:type` on the **DueDate** attribute, the same value that is returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is displayed.</span></span>  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="c7f67-164">针对架构测试示例 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="c7f67-164">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="c7f67-165">复制上面的架构代码，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="c7f67-165">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="c7f67-166">将该文件另存为 xsdType.xml。</span><span class="sxs-lookup"><span data-stu-id="c7f67-166">Save the file as xsdType.xml.</span></span>  
  
2.  <span data-ttu-id="c7f67-167">复制以下模板，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="c7f67-167">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="c7f67-168">在保存 xsdType.xml 的相同目录中将文件另存为 xsdTypeT.xml。</span><span class="sxs-lookup"><span data-stu-id="c7f67-168">Save the file as xsdTypeT.xml in the same directory where you saved xsdType.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="xsdType.xml">  
        /Order  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="c7f67-169">为映射架构 (xsdType.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="c7f67-169">The directory path specified for the mapping schema (xsdType.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="c7f67-170">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="c7f67-170">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\xsdType.xml"  
    ```  
  
3.  <span data-ttu-id="c7f67-171">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="c7f67-171">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="c7f67-172">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="c7f67-172">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="c7f67-173">下面是部分结果集：</span><span class="sxs-lookup"><span data-stu-id="c7f67-173">Here is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="43659"   
         CustomerID="676"   
         OrderDate="2001-07-01"   
         DueDate="2001-07-13T00:00:00"   
         ShipDate="00:00:00" />   
  <Order SalesOrderID="43660"   
         CustomerID="117"   
         OrderDate="2001-07-01"   
         DueDate="2001-07-13T00:00:00"   
         ShipDate="00:00:00" />   
 ...  
</ROOT>  
```  
  
 <span data-ttu-id="c7f67-174">这是等效的 XDR 架构：</span><span class="sxs-lookup"><span data-stu-id="c7f67-174">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  
<ElementType name="Order" sql:relation="Sales.SalesOrderHeader">  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="CustomerID"  />  
    <AttributeType name="OrderDate" dt:type="date" />  
    <AttributeType name="DueDate" />  
    <AttributeType name="ShipDate" dt:type="time" />  
  
    <attribute type="SalesOrderID" sql:field="OrderID" />  
    <attribute type="CustomerID" sql:field="CustomerID" />  
    <attribute type="OrderDate" sql:field="OrderDate" />  
    <attribute type="DueDate" sql:field="DueDate" />  
    <attribute type="ShipDate" sql:field="ShipDate" />  
</ElementType>  
</Schema>  
```  
  
### <a name="b-specifying-sql-data-type-using-sqldatatype"></a><span data-ttu-id="c7f67-175">B.</span><span class="sxs-lookup"><span data-stu-id="c7f67-175">B.</span></span> <span data-ttu-id="c7f67-176">使用 sql:datatype 指定 SQL 数据类型</span><span class="sxs-lookup"><span data-stu-id="c7f67-176">Specifying SQL data type using sql:datatype</span></span>  
 <span data-ttu-id="c7f67-177">有关工作示例，请参阅 XML 大容量加载示例中的示例 G [&#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="c7f67-177">For a working sample, see Example G in [XML Bulk Load Examples &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md).</span></span> <span data-ttu-id="c7f67-178">在此示例中，大容量加载包含“{”和“}”的 GUID 值。</span><span class="sxs-lookup"><span data-stu-id="c7f67-178">In this example, a GUID value including "{" and "}" is bulk loaded.</span></span> <span data-ttu-id="c7f67-179">此示例中的架构指定 `sql:datatype` 以将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型标识为 `uniqueidentifier`。</span><span class="sxs-lookup"><span data-stu-id="c7f67-179">The schema in this example specifies `sql:datatype` to identify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type as `uniqueidentifier`.</span></span> <span data-ttu-id="c7f67-180">此示例说明何时必须在架构中指定 `sql:datatype`。</span><span class="sxs-lookup"><span data-stu-id="c7f67-180">This example illustrate when `sql:datatype` must be specified in the schema.</span></span>  
  
  
