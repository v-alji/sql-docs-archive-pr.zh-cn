---
title: XML 架构集合 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XSD schemas [SQL Server]
- xml_schema_namespace function
- XML schema collections [SQL Server], about XML schema collections
- metadata [SQL Server], XML schema collections
- queries [XML in SQL Server], XML schema collections
- schema collections [SQL Server]
- schemas [SQL Server], XML
- XML [SQL Server], schema collections
- XML schema collections [SQL Server]
- schema collections [SQL Server], about XML schema collections
ms.assetid: 659d41aa-ccec-4554-804a-722a96ef25c2
author: rothja
ms.author: jroth
ms.openlocfilehash: 3ee4757f1353278447ee55e97c8d4ba23aa2d649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588373"
---
# <a name="xml-schema-collections-sql-server"></a><span data-ttu-id="fbfe4-102">XML 架构集合 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="fbfe4-102">XML Schema Collections (SQL Server)</span></span>
  <span data-ttu-id="fbfe4-103">如主题[xml &#40;transact-sql&#41;](/sql/t-sql/xml/xml-transact-sql)中所述，SQL Server 通过数据类型提供 xml 数据的本机存储 `xml` 。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-103">As described in the topic, [xml &#40;Transact-SQL&#41;](/sql/t-sql/xml/xml-transact-sql), SQL Server provides native storage of XML data through the `xml` data type.</span></span> <span data-ttu-id="fbfe4-104">您可以选择 `xml` 通过 XML 架构集合将 XSD 架构与类型的变量或列关联。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-104">You can optionally associate XSD schemas with a variable or a column of `xml` type through an XML schema collection.</span></span> <span data-ttu-id="fbfe4-105">XML 架构集合存储导入的 XML 架构，然后用于执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="fbfe4-105">The XML schema collection stores the imported XML schemas and is then used to do the following:</span></span>  
  
-   <span data-ttu-id="fbfe4-106">验证 XML 实例</span><span class="sxs-lookup"><span data-stu-id="fbfe4-106">Validate XML instances</span></span>  
  
-   <span data-ttu-id="fbfe4-107">类型化在数据库中存储的 XML 数据</span><span class="sxs-lookup"><span data-stu-id="fbfe4-107">Type the XML data as it is stored in the database</span></span>  
  
 <span data-ttu-id="fbfe4-108">请注意，XML 架构集合是一个类似于数据库表的元数据实体。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-108">Note that the XML schema collection is a metadata entity like a table in the database.</span></span> <span data-ttu-id="fbfe4-109">您可以创建、修改和删除它们。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-109">You can create, modify, and drop them.</span></span> <span data-ttu-id="fbfe4-110">[CREATE XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/create-xml-schema-collection-transact-sql) 语句中指定的架构将自动导入到新建的 XML 架构集合对象中。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-110">Schemas specified in a [CREATE XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/create-xml-schema-collection-transact-sql) statement are automatically imported into the newly created XML schema collection object.</span></span> <span data-ttu-id="fbfe4-111">通过使用 [ALTER XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/alter-xml-schema-collection-transact-sql) 语句，可以将其他架构或架构组件导入到数据库中的现有集合对象。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-111">You can import additional schemas or schema components into an existing collection object in the database by using the [ALTER XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/alter-xml-schema-collection-transact-sql) statement.</span></span>  
  
 <span data-ttu-id="fbfe4-112">如主题[类型化与非类型化的 XML](../xml/compare-typed-xml-to-untyped-xml.md) 中所述，存储在与架构关联的列或变量中的 XML 称为**类型化的** XML，因为该架构为实例数据提供了必要的数据类型信息。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-112">As described in the topic, [Typed vs. Untyped XML](../xml/compare-typed-xml-to-untyped-xml.md), the XML stored in a column or variable that a schema is associated with is referred to as **typed** XML, because the schema provides the necessary data type information for the instance data.</span></span> <span data-ttu-id="fbfe4-113">SQL Server 使用此类型信息优化数据存储。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-113">SQL Server uses this type information to optimize data storage.</span></span>  
  
 <span data-ttu-id="fbfe4-114">查询处理引擎也使用该架构进行类型检查并优化查询和数据修改。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-114">The query-processing engine also uses the schema for type checking and to optimize queries and data modification.</span></span>  
  
 <span data-ttu-id="fbfe4-115">此外，SQL Server 使用关联的 XML 架构集合（在类型化的情况下） `xml` 来验证 XML 实例。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-115">Also, SQL Server uses the associated XML schema collection, in the case of typed `xml`, to validate the XML instance.</span></span> <span data-ttu-id="fbfe4-116">如果 XML 实例符合架构，则数据库允许该实例存储在包含其类型信息的系统中。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-116">If the XML instance complies with the schema, the database allows the instance to be stored in the system with their type information.</span></span> <span data-ttu-id="fbfe4-117">否则，它将拒绝该实例。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-117">Otherwise, it rejects the instance.</span></span>  
  
 <span data-ttu-id="fbfe4-118">可以使用内部函数 XML_SCHEMA_NAMESPACE 检索数据库中存储的架构集合。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-118">You can use the intrinsic function XML_SCHEMA_NAMESPACE to retrieve the schema collection that is stored in the database.</span></span> <span data-ttu-id="fbfe4-119">有关详细信息，请参阅 [查看存储 XML 架构集合](../xml/view-a-stored-xml-schema-collection.md)。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-119">For more information, see [View a Stored XML Schema Collection](../xml/view-a-stored-xml-schema-collection.md).</span></span>  
  
 <span data-ttu-id="fbfe4-120">还可以使用 XML 架构集合类型化 XML 变量、参数和列。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-120">You can also use the XML schema collection to type XML variables, parameters, and columns.</span></span>  
  
##  <a name="ddl-for-managing-schema-collections"></a><a name="ddl"></a> <span data-ttu-id="fbfe4-121">用于管理架构集合的 DDL</span><span class="sxs-lookup"><span data-stu-id="fbfe4-121">DDL for Managing Schema Collections</span></span>  
 <span data-ttu-id="fbfe4-122">可以在数据库中创建 XML 架构集合，并将它们与 `xml` 类型的变量和列相关联。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-122">You can create XML schema collections in the database and associate them with variables and columns of `xml` type.</span></span> <span data-ttu-id="fbfe4-123">为了管理数据库中的架构集合， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供了下列 DDL 语句：</span><span class="sxs-lookup"><span data-stu-id="fbfe4-123">To manage schema collections in the database, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides the following DDL statements:</span></span>  
  
-   <span data-ttu-id="fbfe4-124">[CREATE XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/create-xml-schema-collection-transact-sql) 可将架构组件导入到数据库。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-124">[CREATE XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-xml-schema-collection-transact-sql) Imports schema components into a database.</span></span>  
  
-   <span data-ttu-id="fbfe4-125">[ALTER XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/alter-xml-schema-collection-transact-sql) 修改现有 XML 架构集合中的架构组件。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-125">[ALTER XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-xml-schema-collection-transact-sql) Modifies the schema components in an existing XML schema collection.</span></span>  
  
-   <span data-ttu-id="fbfe4-126">[DROP XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/drop-xml-schema-collection-transact-sql) 删除整个 XML 架构集合及其所有组件。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-126">[DROP XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-xml-schema-collection-transact-sql) Deletes a complete XML schema collection and all its components.</span></span>  
  
 <span data-ttu-id="fbfe4-127">若要使用 XML 架构集合及其包含的架构，必须首先使用 CREATE XML SCHEMA COLLECTION 语句创建架构集合及其包含的架构。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-127">To use an XML schema collection and the schemas it contains, you must first create the collection and the schemas by using the CREATE XML SCHEMA COLLECTION statement.</span></span> <span data-ttu-id="fbfe4-128">创建架构集合之后，您可以创建 `xml` 类型的变量和列，并将其与架构集合进行关联。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-128">After the schema collection is created, you can then create variables and columns of `xml` type and associate the schema collection with them.</span></span> <span data-ttu-id="fbfe4-129">注意，创建架构集合之后，各种架构组件存储在元数据中。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-129">Note that after a schema collection is created, various schema components are stored in the metadata.</span></span> <span data-ttu-id="fbfe4-130">还可以使用 ALTER XML SCHEMA COLLECTION 向现有架构添加更多组件或向现有集合添加新架构。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-130">You can also use the ALTER XML SCHEMA COLLECTION to add more components to the existing schemas or add new schemas to an existing collection.</span></span>  
  
 <span data-ttu-id="fbfe4-131">若要删除架构集合，请使用 DROP XML SCHEMA COLLECTION 语句。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-131">To drop the schema collection, use the DROP XML SCHEMA COLLECTION statement.</span></span> <span data-ttu-id="fbfe4-132">它将删除包含在集合中的所有架构并删除集合对象。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-132">This drops all schemas that are contained in the collection and removes the collection object.</span></span> <span data-ttu-id="fbfe4-133">请注意，只有在满足 [DROP XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/drop-xml-schema-collection-transact-sql) 中所述的条件时，才能删除架构集合。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-133">Note that before you can drop a schema collection, the conditions described in [DROP XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-xml-schema-collection-transact-sql)must be met.</span></span>  
  
##  <a name="understanding-schema-components"></a><a name="components"></a> <span data-ttu-id="fbfe4-134">了解架构组件</span><span class="sxs-lookup"><span data-stu-id="fbfe4-134">Understanding Schema Components</span></span>  
 <span data-ttu-id="fbfe4-135">使用 CREATE XML SCHEMA COLLECTION 语句时，将把各种架构组件导入数据库中。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-135">When you use the CREATE XML SCHEMA COLLECTION statement, various schema components are imported into the database.</span></span> <span data-ttu-id="fbfe4-136">架构组件包括架构元素、属性和类型定义。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-136">Schema components include schema elements, attributes, and type definitions.</span></span> <span data-ttu-id="fbfe4-137">使用 DROP XML SCHEMA COLLECTION 语句时，将删除整个集合。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-137">When you use the DROP XML SCHEMA COLLECTION statement, you remove the complete collection.</span></span>  
  
 <span data-ttu-id="fbfe4-138">CREATE XML SCHEMA COLLECTION 将把架构组件保存到各种系统表中。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-138">CREATE XML SCHEMA COLLECTION saves the schema components into various system tables.</span></span>  
  
 <span data-ttu-id="fbfe4-139">例如，请看下面的架构：</span><span class="sxs-lookup"><span data-stu-id="fbfe4-139">For example, consider the following schema:</span></span>  
  
```  
<?xml version="1.0"?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            targetNamespace="uri:Cust_Orders2"  
            xmlns="uri:Cust_Orders2" >  
  <xsd:attribute name="SomeAttribute" type="xsd:int" />  
  <xsd:complexType name="SomeType" />  
  <xsd:complexType name="OrderType" >  
    <xsd:sequence>  
      <xsd:element name="OrderDate" type="xsd:date" />  
      <xsd:element name="RequiredDate" type="xsd:date" />  
      <xsd:element name="ShippedDate" type="xsd:date" />  
    </xsd:sequence>  
    <xsd:attribute name="OrderID" type="xsd:ID" />  
    <xsd:attribute name="CustomerID"  />  
    <xsd:attribute name="EmployeeID"  />  
  </xsd:complexType>  
  <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order" type="OrderType"  
                     maxOccurs="unbounded" />  
       </xsd:sequence>  
      <xsd:attribute name="CustomerID" type="xsd:string" />  
      <xsd:attribute name="OrderIDList" type="xsd:IDREFS" />  
  </xsd:complexType>  
  <xsd:element name="Customer" type="CustomerType" />  
</xsd:schema>  
```  
  
 <span data-ttu-id="fbfe4-140">以上架构显示了可以存储在数据库中的不同类型的组件。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-140">The previous schema shows the different types of components that can be stored in the database.</span></span> <span data-ttu-id="fbfe4-141">其中包括 `SomeAttribute`、 `SomeType`、 `OrderType`、 `CustomerType`、 `Customer`、 `Order`、 `CustomerID`、 `OrderID`、 `OrderDate`、 `RequiredDate`以及 `ShippedDate`。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-141">These include `SomeAttribute`, `SomeType`, `OrderType`, `CustomerType`, `Customer`, `Order`, `CustomerID`, `OrderID`, `OrderDate`, `RequiredDate`, and `ShippedDate`.</span></span>  
  
### <a name="component-categories"></a><span data-ttu-id="fbfe4-142">组件类别</span><span class="sxs-lookup"><span data-stu-id="fbfe4-142">Component Categories</span></span>  
 <span data-ttu-id="fbfe4-143">数据库中存储的架构组件分为下列类别：</span><span class="sxs-lookup"><span data-stu-id="fbfe4-143">The Schema components stored in the database fall into the following categories:</span></span>  
  
-   <span data-ttu-id="fbfe4-144">ELEMENT</span><span class="sxs-lookup"><span data-stu-id="fbfe4-144">ELEMENT</span></span>  
  
-   <span data-ttu-id="fbfe4-145">ATTRIBUTE</span><span class="sxs-lookup"><span data-stu-id="fbfe4-145">ATTRIBUTE</span></span>  
  
-   <span data-ttu-id="fbfe4-146">TYPE（用于简单或复杂类型）</span><span class="sxs-lookup"><span data-stu-id="fbfe4-146">TYPE (for simple or complex types)</span></span>  
  
-   <span data-ttu-id="fbfe4-147">ATTRIBUTEGROUP</span><span class="sxs-lookup"><span data-stu-id="fbfe4-147">ATTRIBUTEGROUP</span></span>  
  
-   <span data-ttu-id="fbfe4-148">MODELGROUP</span><span class="sxs-lookup"><span data-stu-id="fbfe4-148">MODELGROUP</span></span>  
  
 <span data-ttu-id="fbfe4-149">例如：</span><span class="sxs-lookup"><span data-stu-id="fbfe4-149">For example:</span></span>  
  
-   <span data-ttu-id="fbfe4-150">**SomeAttribute** 是 ATTRIBUTE 组件。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-150">**SomeAttribute** is an ATTRIBUTE component.</span></span>  
  
-   <span data-ttu-id="fbfe4-151">**SomeType**、 **OrderType**和 **CustomerType** 是 TYPE 组件。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-151">**SomeType**, **OrderType**, and **CustomerType** are TYPE components.</span></span>  
  
-   <span data-ttu-id="fbfe4-152">**Customer** 是 ELEMENT 组件。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-152">**Customer** is an ELEMENT component.</span></span>  
  
 <span data-ttu-id="fbfe4-153">将架构导入数据库时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不会存储架构本身。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-153">When you import a schema into the database, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not store the schema itself.</span></span> <span data-ttu-id="fbfe4-154">相反， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会存储各种不同的组件。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-154">Instead, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stores the various individual components.</span></span> <span data-ttu-id="fbfe4-155">也就是说，不存储 \<Schema> 标记，仅保存在其中定义的组件。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-155">That is, the \<Schema> tag is not stored, only the components that are defined within it are preserved.</span></span> <span data-ttu-id="fbfe4-156">不存储所有的架构元素。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-156">All schema elements are not preserved.</span></span> <span data-ttu-id="fbfe4-157">如果 \<Schema> 标记包含指定其组件默认行为的属性，则在导入过程中，将把这些属性移动到其中的架构组件，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-157">If the \<Schema> tag contains attributes that specify default behavior of its components, these attributes are moved to the schema components within it during the import process, as shown in the following table.</span></span>  
  
|<span data-ttu-id="fbfe4-158">属性名称</span><span class="sxs-lookup"><span data-stu-id="fbfe4-158">Attribute name</span></span>|<span data-ttu-id="fbfe4-159">行为</span><span class="sxs-lookup"><span data-stu-id="fbfe4-159">Behavior</span></span>|  
|--------------------|--------------|  
|<span data-ttu-id="fbfe4-160">**attributeFormDefault**</span><span class="sxs-lookup"><span data-stu-id="fbfe4-160">**attributeFormDefault**</span></span>|<span data-ttu-id="fbfe4-161">应用于架构中所有属性声明的 **form** 属性，此架构中不存在此属性并且将值设置为 **attributeFormDefault** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-161">The **form** attribute applied to all attribute declarations in the schema where it is not already present and the value is set to the value of the **attributeFormDefault** attribute.</span></span>|  
|<span data-ttu-id="fbfe4-162">**elementFormDefault**</span><span class="sxs-lookup"><span data-stu-id="fbfe4-162">**elementFormDefault**</span></span>|<span data-ttu-id="fbfe4-163">应用于架构中所有元素声明的 **form** 属性，此架构中不存在此属性并且将值设置为 **elementFormDefault** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-163">The **form** attribute applied to all element declarations in the schema where it is not already present and the value is set to the value of the **elementFormDefault** attribute.</span></span>|  
|<span data-ttu-id="fbfe4-164">**blockDefault**</span><span class="sxs-lookup"><span data-stu-id="fbfe4-164">**blockDefault**</span></span>|<span data-ttu-id="fbfe4-165">应用于所有元素声明和类型定义的 **block** 属性，这些声明和定义中不存在此属性并且将值设置为 **blockDefault** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-165">The **block** attribute applied to all element declarations and type definitions where it is not already present and the value is set to the value of the **blockDefault** attribute.</span></span>|  
|<span data-ttu-id="fbfe4-166">**finalDefault**</span><span class="sxs-lookup"><span data-stu-id="fbfe4-166">**finalDefault**</span></span>|<span data-ttu-id="fbfe4-167">应用于所有元素声明和类型定义的 **final** 属性，这些声明和定义中不存在此属性并且将值设置为 **finalDefault** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-167">The **final** attribute applied to all element declarations and type definitions where it is not already present and the value is set to the value of the **finalDefault** attribute.</span></span>|  
|<span data-ttu-id="fbfe4-168">**targetNamespace**</span><span class="sxs-lookup"><span data-stu-id="fbfe4-168">**targetNamespace**</span></span>|<span data-ttu-id="fbfe4-169">有关属于目标命名空间的组件的信息存储在元数据中。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-169">Information about the components that belong to the target namespace is stored in the metadata.</span></span>|  
  
##  <a name="permissions-on-an-xml-schema-collection"></a><a name="perms"></a> <span data-ttu-id="fbfe4-170">XML 架构集合的权限</span><span class="sxs-lookup"><span data-stu-id="fbfe4-170">Permissions on an XML Schema Collection</span></span>  
 <span data-ttu-id="fbfe4-171">您必须具有必要的权限才能执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="fbfe4-171">You must have the necessary permissions to do the following:</span></span>  
  
-   <span data-ttu-id="fbfe4-172">创建/加载 XML 架构集合</span><span class="sxs-lookup"><span data-stu-id="fbfe4-172">Create/load the XML schema collection</span></span>  
  
-   <span data-ttu-id="fbfe4-173">修改 XML 架构集合</span><span class="sxs-lookup"><span data-stu-id="fbfe4-173">Modify the XML schema collection</span></span>  
  
-   <span data-ttu-id="fbfe4-174">删除 XML 架构集合</span><span class="sxs-lookup"><span data-stu-id="fbfe4-174">Drop the XML schema collection</span></span>  
  
-   <span data-ttu-id="fbfe4-175">使用 XML 架构集合键入 `xml` 类型列、变量和参数，或者在表或列约束中使用它</span><span class="sxs-lookup"><span data-stu-id="fbfe4-175">Use the XML schema collection to type `xml` type columns, variables, and parameters, or use it in table or column constraints</span></span>  
  
 <span data-ttu-id="fbfe4-176">SQL Server 安全模式允许对每个对象使用 CONTROL 权限。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-176">The SQL Server security model allows CONTROL permission on every object.</span></span> <span data-ttu-id="fbfe4-177">此权限的被授权者将获得对象的其他所有权限。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-177">The grantee of this permission obtains all other permissions on the object.</span></span> <span data-ttu-id="fbfe4-178">对象的所有者也拥有对象的所有权限。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-178">The owner of the object also has all the permissions on the object.</span></span>  
  
 <span data-ttu-id="fbfe4-179">对象上的 CONTROL 权限的所有者和被授权者可以授予对象的任何权限。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-179">The owner and the grantee of the CONTROL permission on an object can grant any permission on the object.</span></span> <span data-ttu-id="fbfe4-180">指定 WITH GRANT OPTION 后，不是所有者并且没有 CONTROL 权限的用户也可以授予对象的权限。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-180">A user who is not the owner and does not have CONTROL permission can still grant permission on an object when WITH GRANT OPTION is specified.</span></span> <span data-ttu-id="fbfe4-181">例如，假定用户 A 通过 WITH GRANT OPTION 对 XML 架构集合 S 具有 REFERENCES 权限，但对 S 没有其他任何权限。用户 A 可以授予用户 B 架构集合 S 的 REFERENCES 权限。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-181">For example, assume User A has REFERENCES permission on XML schema collection S, through WITH GRANT OPTION, but no other permissions on S. User A could grant User B REFERENCES permission on schema collection S.</span></span>  
  
 <span data-ttu-id="fbfe4-182">安全模式也允许使用这些权限来创建和使用 XML 架构集合或将所有权从一个用户传递到另一个用户。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-182">The security model also allows permissions to create and use XML schema collections or transfer ownership from one user to another.</span></span> <span data-ttu-id="fbfe4-183">下列主题说明了 XML 架构集合权限。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-183">The following topics describe the XML schema collection permissions.</span></span>  
  
-   [<span data-ttu-id="fbfe4-184">授予对 XML 架构集合的权限</span><span class="sxs-lookup"><span data-stu-id="fbfe4-184">Grant Permissions on an XML Schema Collection</span></span>](../xml/grant-permissions-on-an-xml-schema-collection.md)  
  
     <span data-ttu-id="fbfe4-185">本主题讨论了如何授予创建 XML 架构集合的权限和如何授予 XML 架构集合对象的权限。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-185">This topic discussess how to grant permissions to create an XML schema collection and how to grant permissions on an XML schema collection object.</span></span>  
  
-   [<span data-ttu-id="fbfe4-186">吊销对 XML 架构集合的权限</span><span class="sxs-lookup"><span data-stu-id="fbfe4-186">Revoke Permissions on an XML Schema Collection</span></span>](../xml/revoke-permissions-on-an-xml-schema-collection.md)  
  
     <span data-ttu-id="fbfe4-187">本主题讨论了如何使用撤消权限来防止创建 XML 架构集合和如何撤消 XML 架构集合对象的权限。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-187">This topic discusses how revoking permissions can be used to prevent the creation of an XML schema collection and how to revoke permissions on an XML schema collection object.</span></span>  
  
-   [<span data-ttu-id="fbfe4-188">拒绝对 XML 架构集合的权限</span><span class="sxs-lookup"><span data-stu-id="fbfe4-188">Deny Permissions on an XML Schema Collection</span></span>](../xml/deny-permissions-on-an-xml-schema-collection.md)  
  
     <span data-ttu-id="fbfe4-189">本主题讨论了如何拒绝创建 XML 架构集合的权限和如何拒绝 XML 架构集合对象的权限。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-189">This topic discusses how to deny permissions to create an XML schema collection and deny permission on an XML schema collection object.</span></span>  
  
##  <a name="getting-information-about-xml-schemas-and-schema-collections"></a><a name="info"></a> <span data-ttu-id="fbfe4-190">获取有关 XML 架构和架构集合的信息</span><span class="sxs-lookup"><span data-stu-id="fbfe4-190">Getting Information about XML Schemas and Schema Collections</span></span>  
 <span data-ttu-id="fbfe4-191">XML 架构集合在目录视图 sys.xml_schema_collections 中枚举出来。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-191">XML schema collections are enumerated in the catalog view, sys.xml_schema_collections.</span></span> <span data-ttu-id="fbfe4-192">XML 架构集合“sys”由系统定义。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-192">The XML schema collection "sys" is defined by the system.</span></span> <span data-ttu-id="fbfe4-193">它包含无需显式加载即可在所有用户定义的 XML 架构集合中使用的预定义命名空间。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-193">It contains the predefined namespaces that can be used in all user-defined XML schema collections without having to load them explicitly.</span></span> <span data-ttu-id="fbfe4-194">此列表包含 xml、xs、xsi、fn 和 xdt 的命名空间。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-194">This list contains the namespaces for xml, xs, xsi, fn, and xdt.</span></span> <span data-ttu-id="fbfe4-195">另外两个目录视图是 sys.xml_schema_namespaces（它枚举每个 XML 架构集合中的所有命名空间）和 sys.xml_components（它枚举每个 XML 架构中的所有 XML 架构组件）。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-195">Two other catalog views are sys.xml_schema_namespaces, which enumerates all namespaces within each XML schema collection, and sys.xml_components, which enumerates all XML schema components within each XML schema.</span></span>  
  
 <span data-ttu-id="fbfe4-196">内置函数**XML_SCHEMA_NAMESPACE**、 *schemaName、XmlSchemacollectionName、命名空间 uri*生成 `xml` 数据类型实例。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-196">The built-in function **XML_SCHEMA_NAMESPACE**, *schemaName, XmlSchemacollectionName, namespace-uri*, yields an `xml` data type instance..</span></span> <span data-ttu-id="fbfe4-197">此实例包含在 XML 架构集合中所包含架构（预定义的 XML 架构除外）的 XML 架构片段。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-197">This instance contains XML schema fragments for schemas that are contained in an XML schema collection, except the predefined XML schemas.</span></span>  
  
 <span data-ttu-id="fbfe4-198">可以按下列方式枚举 XML 架构集合的内容：</span><span class="sxs-lookup"><span data-stu-id="fbfe4-198">You can enumerate the contents of an XML schema collection in the following ways:</span></span>  
  
-   <span data-ttu-id="fbfe4-199">编写对 XML 架构集合的相应目录视图的 Transact-SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-199">Write Transact-SQL queries on the appropriate catalog views for XML schema collections.</span></span>  
  
-   <span data-ttu-id="fbfe4-200">使用内置函数 **XML_SCHEMA_NAMESPACE()** 。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-200">Use the built-in function **XML_SCHEMA_NAMESPACE()**.</span></span> <span data-ttu-id="fbfe4-201">您可以 `xml` 对此函数的输出应用数据类型方法。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-201">You can apply `xml` data type methods on the output of this function.</span></span> <span data-ttu-id="fbfe4-202">但不能修改基础 XML 架构。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-202">However, you cannot modify the underlying XML schemas.</span></span>  
  
 <span data-ttu-id="fbfe4-203">这些在下列示例中进行了说明。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-203">These are illustrated in the following examples.</span></span>  
  
### <a name="example-enumerate-the-xml-namespaces-in-an-xml-schema-collection"></a><span data-ttu-id="fbfe4-204">示例：枚举 XML 架构集合中的 XML 命名空间</span><span class="sxs-lookup"><span data-stu-id="fbfe4-204">Example: Enumerate the XML Namespaces in an XML Schema Collection</span></span>  
 <span data-ttu-id="fbfe4-205">对 XML 架构集合“myCollection”使用下面的查询：</span><span class="sxs-lookup"><span data-stu-id="fbfe4-205">Use the following query for the XML schema collection "myCollection":</span></span>  
  
```  
SELECT XSN.name  
FROM    sys.xml_schema_collections XSC JOIN sys.xml_schema_namespaces XSN  
    ON (XSC.xml_collection_id = XSN.xml_collection_id)  
WHERE    XSC.name = 'myCollection'     
```  
  
### <a name="example-enumerate-the-contents-of-an-xml-schema-collection"></a><span data-ttu-id="fbfe4-206">示例：枚举 XML 架构集合的内容</span><span class="sxs-lookup"><span data-stu-id="fbfe4-206">Example: Enumerate the Contents of an XML Schema Collection</span></span>  
 <span data-ttu-id="fbfe4-207">以下语句枚举关系架构 dbo 中的 XML 架构集合“myCollection”的内容。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-207">The following statement enumerates the contents of the XML schema collection "myCollection" within the relational schema, dbo.</span></span>  
  
```  
SELECT XML_SCHEMA_NAMESPACE (N'dbo', N'myCollection')  
```  
  
 <span data-ttu-id="fbfe4-208">可以 `xml` 通过将目标命名空间指定为**XML_SCHEMA_NAMESPACE ( # B1**的第三个参数，将集合中的单个 XML 架构作为数据类型实例获取。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-208">Individual XML schemas within the collection can be obtained as `xml` data type instances by specifying the target namespace as the third argument to **XML_SCHEMA_NAMESPACE()**.</span></span> <span data-ttu-id="fbfe4-209">下面的示例说明了这一点。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-209">This is shown in the following example.</span></span>  
  
### <a name="example-output-a-specified-schema-from-an-xml-schema-collection"></a><span data-ttu-id="fbfe4-210">示例：从 XML 架构集合输出指定的架构</span><span class="sxs-lookup"><span data-stu-id="fbfe4-210">Example: Output a Specified Schema from an XML Schema Collection</span></span>  
 <span data-ttu-id="fbfe4-211">以下语句从关系架构 dbo 中的 XML 架构集合“myCollection”输出目标命名空间为“<https://www.microsoft.com/books>”的 XML 架构。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-211">The following statement outputs the XML schema with the target namespace "<https://www.microsoft.com/books>" from the XML schema collection "myCollection" within the relational schema, dbo.</span></span>  
  
```  
SELECT XML_SCHEMA_NAMESPACE (N'dbo', N'myCollection',   
N'https://www.microsoft.com/books')  
```  
  
### <a name="querying-xml-schemas"></a><span data-ttu-id="fbfe4-212">查询 XML 架构</span><span class="sxs-lookup"><span data-stu-id="fbfe4-212">Querying XML Schemas</span></span>  
 <span data-ttu-id="fbfe4-213">可以按下列方式查询加载到 XML 架构集合的 XML 架构：</span><span class="sxs-lookup"><span data-stu-id="fbfe4-213">You can query XML schemas that you have loaded into XML schema collections in the following ways:</span></span>  
  
-   <span data-ttu-id="fbfe4-214">编写对 XML 架构命名空间的目录视图的 Transact-SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-214">Write Transact-SQL queries on catalog views for XML schema namespaces.</span></span>  
  
-   <span data-ttu-id="fbfe4-215">创建包含 `xml` 数据类型列的表以存储 XML 架构并将它们加载到 XML 类型系统。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-215">Create a table that contains an `xml` data type column to store your XML schemas and also load them into the XML type system.</span></span> <span data-ttu-id="fbfe4-216">可以使用 `xml` 数据类型方法查询 XML 列。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-216">You can query the XML column by using the `xml` data type methods.</span></span> <span data-ttu-id="fbfe4-217">另外，还可以对此列生成 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-217">Also, you can build an XML index on this column.</span></span> <span data-ttu-id="fbfe4-218">但是，使用此方法时，应用程序必须保持 XML 列中存储的 XML 架构和 XML 类型系统之间的一致性。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-218">However, with this approach, the application must maintain consistency between the XML schemas stored in the XML column and the XML type system.</span></span> <span data-ttu-id="fbfe4-219">例如，如果从 XML 类型系统中删除 XML 架构命名空间，还必须从表中删除它以保持一致性。</span><span class="sxs-lookup"><span data-stu-id="fbfe4-219">For example, if you drop the XML schema namespace from the XML type system, you also have to drop it from the table in order to preserve consistency.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbfe4-220">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fbfe4-220">See Also</span></span>  
 <span data-ttu-id="fbfe4-221">[查看存储 XML 架构集合](../xml/view-a-stored-xml-schema-collection.md) </span><span class="sxs-lookup"><span data-stu-id="fbfe4-221">[View a Stored XML Schema Collection](../xml/view-a-stored-xml-schema-collection.md) </span></span>  
 <span data-ttu-id="fbfe4-222">[预处理架构以便合并包括的架构](../xml/preprocess-a-schema-to-merge-included-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="fbfe4-222">[Preprocess a Schema to Merge Included Schemas](../xml/preprocess-a-schema-to-merge-included-schemas.md) </span></span>  
 [<span data-ttu-id="fbfe4-223">在服务器上使用 XML 架构集合的要求和限制</span><span class="sxs-lookup"><span data-stu-id="fbfe4-223">Requirements and Limitations for XML Schema Collections on the Server</span></span>](../xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
