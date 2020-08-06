---
title: " (SQLXML 4.0) 的 XML 大容量加载的指导原则和限制 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XML Bulk Load [SQLXML], about XML Bulk Load
- bulk load [SQLXML], about bulk load
ms.assetid: c5885d14-c7c1-47b3-a389-455e99a7ece1
author: rothja
ms.author: jroth
ms.openlocfilehash: 08c0020ac7b28702f5a573c6158ec9d50c735b2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588451"
---
# <a name="guidelines-and-limitations-of-xml-bulk-load-sqlxml-40"></a><span data-ttu-id="390aa-102">XML 大容量加载的指导原则和限制 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="390aa-102">Guidelines and Limitations of XML Bulk Load (SQLXML 4.0)</span></span>
  <span data-ttu-id="390aa-103">在使用 XML 大容量加载时，您应该熟悉以下指导原则和限制：</span><span class="sxs-lookup"><span data-stu-id="390aa-103">When you use XML Bulk Load, you should be familiar with the following guidelines and limitations:</span></span>  
  
-   <span data-ttu-id="390aa-104">不支持内联架构。</span><span class="sxs-lookup"><span data-stu-id="390aa-104">Inline schemas are not supported.</span></span>  
  
     <span data-ttu-id="390aa-105">如果在源 XML 文档中具有某一内联架构，则 XML 大容量加载将忽略该架构。</span><span class="sxs-lookup"><span data-stu-id="390aa-105">If you have an inline schema in the source XML document, XML Bulk Load ignores that schema.</span></span> <span data-ttu-id="390aa-106">您为 XML 数据外部的 XML 大容量加载指定该映射架构。</span><span class="sxs-lookup"><span data-stu-id="390aa-106">You specify the mapping schema for XML Bulk Load external to the XML data.</span></span> <span data-ttu-id="390aa-107">不能使用**xmlns = "x:schema"** 属性在节点上指定映射架构。</span><span class="sxs-lookup"><span data-stu-id="390aa-107">You cannot specify the mapping schema at a node by using the **xmlns="x:schema"** attribute.</span></span>  
  
-   <span data-ttu-id="390aa-108">将检查 XML 文档是否格式正确，但不对其进行验证。</span><span class="sxs-lookup"><span data-stu-id="390aa-108">An XML document is checked for being well-formed, but it is not validated.</span></span>  
  
     <span data-ttu-id="390aa-109">XML 大容量加载检查 XML 文档以确定该文档的格式是否正确，即确保 XML 符合万维网联合会的 XML 1.0 建议的语法要求。</span><span class="sxs-lookup"><span data-stu-id="390aa-109">XML Bulk Load checks the XML document to determine whether it is well-formed-that is, to ensure that the XML conforms to the syntax requirements of the World Wide Web Consortium's XML 1.0 recommendation.</span></span> <span data-ttu-id="390aa-110">如果该文档的格式不正确，则 XML 大容量加载将取消处理并返回错误。</span><span class="sxs-lookup"><span data-stu-id="390aa-110">If the document is not well-formed, XML Bulk Load cancels processing and returns an error.</span></span> <span data-ttu-id="390aa-111">对这一要求的唯一例外是在文档为片断时（例如，在文档没有单个根元素时），在此情况下 XML 大容量加载将加载文档。</span><span class="sxs-lookup"><span data-stu-id="390aa-111">The only exception to this is when the document is a fragment (for example, the document has no single root element), in which case XML Bulk Load will load the document.</span></span>  
  
     <span data-ttu-id="390aa-112">XML 大容量加载不针对在 XML 数据文件中定义或引用的任何 XML 数据或 DTD 架构对文档进行验证。</span><span class="sxs-lookup"><span data-stu-id="390aa-112">XML Bulk Load does not validate the document with respect to any XML-Data or DTD schema that is defined or referenced within the XML data file.</span></span> <span data-ttu-id="390aa-113">此外，XML 大容量加载不针对提供的映射架构对 XML 数据文件进行验证。</span><span class="sxs-lookup"><span data-stu-id="390aa-113">In addition, XML Bulk Load does not validate the XML data file against the mapping schema supplied.</span></span>  
  
-   <span data-ttu-id="390aa-114">忽视所有 XML prolog 信息。</span><span class="sxs-lookup"><span data-stu-id="390aa-114">Any XML prolog information is ignored.</span></span>  
  
     <span data-ttu-id="390aa-115">XML 大容量加载将忽略 XML 文档中的元素之前和之后的所有信息 \<root> 。</span><span class="sxs-lookup"><span data-stu-id="390aa-115">XML Bulk Load ignores all the information before and after the \<root> element in the XML document.</span></span> <span data-ttu-id="390aa-116">例如，XML 大容量加载将忽视所有 XML 声明、内部 DTD 定义、外部 DTD 引用和注释等。</span><span class="sxs-lookup"><span data-stu-id="390aa-116">For example, XML Bulk Load ignores any XML declarations, internal DTD definitions, external DTD references, comments, and so on.</span></span>  
  
-   <span data-ttu-id="390aa-117">如果您具有定义两个表之间（例如 Customer 和 CustOrder 之间）的主键/外键关系的映射架构，则必须在该架构中首先描述具有主键的表。</span><span class="sxs-lookup"><span data-stu-id="390aa-117">If you have a mapping schema that defines a primary key/foreign key relationship between two tables (such as between Customer and CustOrder), the table with the primary key must be described first in the schema.</span></span> <span data-ttu-id="390aa-118">具有外键列的表必须出现在该架构中的后面。</span><span class="sxs-lookup"><span data-stu-id="390aa-118">The table with the foreign key column must appear later in the schema.</span></span> <span data-ttu-id="390aa-119">这样做的原因是，架构中的表标识顺序是用于将它们加载到数据库中的顺序。例如，下面的 XDR 架构将在 XML 大容量加载中使用时产生错误，因为在 **\<Order>** 元素前面介绍了元素 **\<Customer>** 。</span><span class="sxs-lookup"><span data-stu-id="390aa-119">The reason for this is that the order in which the tables are identified in the schema is the order that is used to load them into the database.For example, the following XDR schema will produce an error when it is used in XML Bulk Load because the **\<Order>** element is described before the **\<Customer>** element.</span></span> <span data-ttu-id="390aa-120">CustOrder 中的 CustomerID 列是引用 Cust 表中 CustomerID 主键列的外键列。</span><span class="sxs-lookup"><span data-stu-id="390aa-120">The CustomerID column in CustOrder is a foreign key column that refers to the CustomerID primary key column in the Cust table.</span></span>  
  
    ```  
    <?xml version="1.0" ?>  
    <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
            xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
            xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
  
        <ElementType name="Order" sql:relation="CustOrder" >  
          <AttributeType name="OrderID" />  
          <AttributeType name="CustomerID" />  
          <attribute type="OrderID" />  
          <attribute type="CustomerID" />  
        </ElementType>  
  
       <ElementType name="CustomerID" dt:type="int" />  
       <ElementType name="CompanyName" dt:type="string" />  
       <ElementType name="City" dt:type="string" />  
  
       <ElementType name="root" sql:is-constant="1">  
          <element type="Customers" />  
       </ElementType>  
       <ElementType name="Customers" sql:relation="Cust"   
                         sql:overflow-field="OverflowColumn"  >  
          <element type="CustomerID" sql:field="CustomerID" />  
          <element type="CompanyName" sql:field="CompanyName" />  
          <element type="City" sql:field="City" />  
          <element type="Order" >   
               <sql:relationship  
                   key-relation="Cust"  
                    key="CustomerID"  
                    foreign-key="CustomerID"  
                    foreign-relation="CustOrder" />  
          </element>  
       </ElementType>  
    </Schema>  
    ```  
  
-   <span data-ttu-id="390aa-121">如果该架构未通过使用 `sql:overflow-field` 批注指定溢出列，则 XML 大容量加载将忽略在 XML 文档中提供、但未在该映射架构中描述的所有数据。</span><span class="sxs-lookup"><span data-stu-id="390aa-121">If the schema does not specify overflow columns by using the `sql:overflow-field` annotation, XML Bulk Load ignores any data that is present in the XML document but is not described in the mapping schema.</span></span>  
  
     <span data-ttu-id="390aa-122">XML 大容量加载只要在 XML 数据流中遇到已知标记，就会应用您指定的映射架构。</span><span class="sxs-lookup"><span data-stu-id="390aa-122">XML Bulk Load applies the mapping schema that you have specified whenever it encounters known tags in the XML data stream.</span></span> <span data-ttu-id="390aa-123">它将忽略在 XML 文档中提供、但未在该架构中描述的数据。</span><span class="sxs-lookup"><span data-stu-id="390aa-123">It ignores data that is present in the XML document but is not described in the schema.</span></span> <span data-ttu-id="390aa-124">例如，假设您有一个描述元素的映射架构 **\<Customer>** 。</span><span class="sxs-lookup"><span data-stu-id="390aa-124">For example, assume you have a mapping schema that describes a **\<Customer>** element.</span></span> <span data-ttu-id="390aa-125">XML 数据文件有一个 **\<AllCustomers>** 根标记 (这在包含所有元素的架构) 中未进行描述 **\<Customer>** ：</span><span class="sxs-lookup"><span data-stu-id="390aa-125">The XML data file has an **\<AllCustomers>** root tag (which is not described in the schema) that encloses all the **\<Customer>** elements:</span></span>  
  
    ```  
    <AllCustomers>  
      <Customer>...</Customer>  
      <Customer>...</Customer>  
       ...  
    </AllCustomers>  
    ```  
  
     <span data-ttu-id="390aa-126">在这种情况下，XML 大容量加载将忽略 **\<AllCustomers>** 元素，并在元素处开始映射 **\<Customer>** 。</span><span class="sxs-lookup"><span data-stu-id="390aa-126">In this case, XML Bulk Load ignores the **\<AllCustomers>** element and begins mapping at the **\<Customer>** element.</span></span> <span data-ttu-id="390aa-127">XML 大容量将加载忽略在该架构中未描述、但在 XML 文档中出现的元素。</span><span class="sxs-lookup"><span data-stu-id="390aa-127">XML Bulk Load ignores the elements that are not described in the schema but are present in the XML document.</span></span>  
  
     <span data-ttu-id="390aa-128">请考虑包含元素的另一个 XML 源数据文件 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="390aa-128">Consider another XML source data file that contains **\<Order>** elements.</span></span> <span data-ttu-id="390aa-129">以下元素在映射架构中未描述：</span><span class="sxs-lookup"><span data-stu-id="390aa-129">These elements are not described in the mapping schema:</span></span>  
  
    ```  
    <AllCustomers>  
      <Customer>...</Customer>  
        <Order> ... </Order>  
        <Order> ... </Order>  
         ...  
      <Customer>...</Customer>  
        <Order> ... </Order>  
        <Order> ... </Order>  
         ...  
      ...  
    </AllCustomers>  
    ```  
  
     <span data-ttu-id="390aa-130">XML 大容量加载将忽略这些 **\<Order>** 元素。</span><span class="sxs-lookup"><span data-stu-id="390aa-130">XML Bulk Load ignores these **\<Order>** elements.</span></span> <span data-ttu-id="390aa-131">但是，如果在 `sql:overflow-field` 架构中使用批注将列标识为溢出列，则 XML 大容量加载会将所有未用完的数据存储在此列中。</span><span class="sxs-lookup"><span data-stu-id="390aa-131">But if you use the `sql:overflow-field`annotation in the schema to identify a column as an overflow column, XML Bulk Load stores all unconsumed data in this column.</span></span>  
  
-   <span data-ttu-id="390aa-132">CDATA 部分和实体引用在存储到数据库中之前将转换为等效的字符串。</span><span class="sxs-lookup"><span data-stu-id="390aa-132">CDATA sections and entity references are translated to their string equivalents before they are stored in the database.</span></span>  
  
     <span data-ttu-id="390aa-133">在此示例中，CDATA 节包装元素的值 **\<City>** 。</span><span class="sxs-lookup"><span data-stu-id="390aa-133">In this example, a CDATA section wraps the value for the **\<City>** element.</span></span> <span data-ttu-id="390aa-134">XML 大容量加载会在将元素插入到数据库之前，提取 ( "NY" ) 的字符串值 **\<City>** 。</span><span class="sxs-lookup"><span data-stu-id="390aa-134">XML Bulk Load extracts the string value ("NY") before it inserts the **\<City>** element into the database.</span></span>  
  
    ```  
    <City><![CDATA[NY]]> </City>  
    ```  
  
     <span data-ttu-id="390aa-135">XML 大容量加载不保留实体引用。</span><span class="sxs-lookup"><span data-stu-id="390aa-135">XML Bulk Load does not preserve entity references.</span></span>  
  
-   <span data-ttu-id="390aa-136">如果映射架构指定某一属性的默认值并且 XML 源数据不包含该属性，则 XML 大容量加载将使用该默认值。</span><span class="sxs-lookup"><span data-stu-id="390aa-136">If the mapping schema specifies the default value for an attribute and the XML source data does not contain that attribute, XML Bulk Load uses the default value.</span></span>  
  
     <span data-ttu-id="390aa-137">下面的示例 XDR 架构将默认值分配给 "**雇佣**日期" 属性：</span><span class="sxs-lookup"><span data-stu-id="390aa-137">The following sample XDR schema assigns a default value to the **HireDate** attribute:</span></span>  
  
    ```  
    <?xml version="1.0" ?>  
    <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
            xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
            xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
       <ElementType name="root" sql:is-constant="1">  
          <element type="Customers" />  
       </ElementType>  
  
       <ElementType name="Customers" sql:relation="Cust3" >  
          <AttributeType name="CustomerID" dt:type="int"  />  
          <AttributeType name="HireDate"  default="2000-01-01" />  
          <AttributeType name="Salary"   />  
  
          <attribute type="CustomerID" sql:field="CustomerID" />  
          <attribute type="HireDate"   sql:field="HireDate"  />  
          <attribute type="Salary"     sql:field="Salary"    />  
       </ElementType>  
    </Schema>  
    ```  
  
     <span data-ttu-id="390aa-138">在此 XML 数据中，第二个元素缺少 "**雇佣**日期" 属性 **\<Customers>** 。</span><span class="sxs-lookup"><span data-stu-id="390aa-138">In this XML data, the **HireDate** attribute is missing from the second **\<Customers>** element.</span></span> <span data-ttu-id="390aa-139">当 XML 大容量加载向数据库中插入第二个 **\<Customers>** 元素时，它将使用在该架构中指定的默认值。</span><span class="sxs-lookup"><span data-stu-id="390aa-139">When XML Bulk Load inserts the second **\<Customers>** element into the database, it uses the default value that is specified in the schema.</span></span>  
  
    ```  
    <ROOT>  
      <Customers CustomerID="1" HireDate="1999-01-01" Salary="10000" />  
      <Customers CustomerID="2" Salary="10000" />  
    </ROOT>  
    ```  
  
-   <span data-ttu-id="390aa-140">不支持 `sql:url-encode` 批注：</span><span class="sxs-lookup"><span data-stu-id="390aa-140">The `sql:url-encode` annotation is not supported:</span></span>  
  
     <span data-ttu-id="390aa-141">无法在 XML 数据输入中指定某一 URL 后期望大容量加载从该位置读取数据。</span><span class="sxs-lookup"><span data-stu-id="390aa-141">You cannot specify a URL in the XML data input and expect Bulk Load to read data from that location.</span></span>  
  
     <span data-ttu-id="390aa-142">创建在映射架构中标识的表（数据库必须存在）。</span><span class="sxs-lookup"><span data-stu-id="390aa-142">The tables that are identified in the mapping schema are created (the database must exist).</span></span> <span data-ttu-id="390aa-143">如果数据库中已存在一个或多个表，则 SGDropTables 属性将确定是否删除并重新创建这些预先存在的表。</span><span class="sxs-lookup"><span data-stu-id="390aa-143">If one or more of the tables already exists in the database, the SGDropTables property determines whether these preexisting tables are to be dropped and re-created.</span></span>  
  
-   <span data-ttu-id="390aa-144">如果指定 SchemaGen 属性 (例如，SchemaGen = true) ，则将创建在映射架构中标识的表。</span><span class="sxs-lookup"><span data-stu-id="390aa-144">If you specify the SchemaGen property (for example, SchemaGen = true), the tables that are identified in the mapping schema are created.</span></span> <span data-ttu-id="390aa-145">但 SchemaGen 不会为这些表中的主键/外键约束)  (创建任何约束，但有一个例外：如果构成关系中的主键的 XML 节点定义为具有 XML 类型的 ID (即， `type="xsd:ID"` 对于 XSD) 并且 SchemaGen 的 SGUseID 属性设置为 True，则不仅是从 ID 类型化节点创建的主键，而且主键/外键关系是从映射架构关系创建的。</span><span class="sxs-lookup"><span data-stu-id="390aa-145">But SchemaGen does not create any constraints (such as the PRIMARY KEY/FOREIGN KEY constraints) on these tables with one exception: If the XML nodes that constitute the primary key in a relationship are defined as having an XML type of ID (that is, `type="xsd:ID"` for XSD) AND the SGUseID property is set to True for SchemaGen, then not only are primary keys created from the ID typed nodes, but primary key/foreign key relationships are created from mapping schema relationships.</span></span>  
  
-   <span data-ttu-id="390aa-146">SchemaGen 不使用 XSD 架构方面和扩展来生成关系 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 架构。</span><span class="sxs-lookup"><span data-stu-id="390aa-146">SchemaGen does not use XSD schema facets and extensions to generate the relational [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] schema.</span></span>  
  
-   <span data-ttu-id="390aa-147">如果在大容量加载时指定 SchemaGen 属性 (例如，SchemaGen = true) ，则只会更新指定的共享名称) 的表 (和非视图。</span><span class="sxs-lookup"><span data-stu-id="390aa-147">If you specify the SchemaGen property (for example, SchemaGen = true) on Bulk Load, only tables (and not views of shared name) that are specified are updated.</span></span>  
  
-   <span data-ttu-id="390aa-148">SchemaGen 仅提供用于从带批注的 XSD 生成关系架构的基本功能。</span><span class="sxs-lookup"><span data-stu-id="390aa-148">SchemaGen only provides basic functionality for generating the relational schema from annotated XSD.</span></span> <span data-ttu-id="390aa-149">如果需要，用户应手动修改生成的表。</span><span class="sxs-lookup"><span data-stu-id="390aa-149">The user should modify the generated tables manually, if needed.</span></span>  
  
-   <span data-ttu-id="390aa-150">在表之间存在多个关系的情况下，SchemaGen 会尝试创建单个关系，其中包括这两个表之间涉及的所有键。</span><span class="sxs-lookup"><span data-stu-id="390aa-150">Where more than relationship exists between tables,SchemaGen tries to create a single relationship that includes all the keys involved between the two tables.</span></span> <span data-ttu-id="390aa-151">这一限制可能是由于 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 错误导致的。</span><span class="sxs-lookup"><span data-stu-id="390aa-151">This limitation might be the cause of a [!INCLUDE[tsql](../../../includes/tsql-md.md)] error.</span></span>  
  
-   <span data-ttu-id="390aa-152">当您将 XML 数据大容量加载到某一数据库中时，在映射架构中必须至少有一个元素或子元素映射到某一数据库列。</span><span class="sxs-lookup"><span data-stu-id="390aa-152">When you are bulk loading XML data into a database, there must be at least one attribute or child element in the mapping schema that is mapped to a database column.</span></span>  
  
-   <span data-ttu-id="390aa-153">如果您在通过使用 XML 大容量加载插入数据值，则必须以 (-)CCYY-MM-DD((+-)TZ) 格式指定这些值。</span><span class="sxs-lookup"><span data-stu-id="390aa-153">If you are inserting date values by using XML Bulk Load, the values must be specified in the (-)CCYY-MM-DD((+-)TZ) format.</span></span> <span data-ttu-id="390aa-154">这是针对日期的标准 XSD 格式。</span><span class="sxs-lookup"><span data-stu-id="390aa-154">This is the standard XSD format for the date.</span></span>  
  
-   <span data-ttu-id="390aa-155">某些属性标志与其他属性标志不兼容。</span><span class="sxs-lookup"><span data-stu-id="390aa-155">Some property flags are not compatible with other property flags.</span></span> <span data-ttu-id="390aa-156">例如，大容量加载不支持 `Ignoreduplicatekeys=true` 与 `Keepidentity=false` 一起使用。</span><span class="sxs-lookup"><span data-stu-id="390aa-156">For example, bulk load does not support `Ignoreduplicatekeys=true` together with `Keepidentity=false`.</span></span> <span data-ttu-id="390aa-157">在 `Keepidentity=false` 时，大容量加载需要服务器生成键值。</span><span class="sxs-lookup"><span data-stu-id="390aa-157">When `Keepidentity=false`, bulk load expects the server to generate the key values.</span></span> <span data-ttu-id="390aa-158">表对该键应该具有 `IDENTITY` 约束。</span><span class="sxs-lookup"><span data-stu-id="390aa-158">Tables should have an `IDENTITY` constraint on the key.</span></span> <span data-ttu-id="390aa-159">服务器将不生成重复键，这意味着无需将 `Ignoreduplicatekeys` 设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="390aa-159">The server will not generate duplicate keys, which means there is no need for `Ignoreduplicatekeys` to be set to `true`.</span></span> <span data-ttu-id="390aa-160">只有在将来自传入数据的主键值上载到具有多行的表中且这些主键值可能存在冲突时，`Ignoreduplicatekeys` 才应设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="390aa-160">`Ignoreduplicatekeys` should be set to `true` only when uploading primary key values from the incoming data into a table that has rows and there is a potential for conflict of primary key values.</span></span>  
  
  
