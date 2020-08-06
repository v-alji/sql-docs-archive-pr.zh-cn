---
title: 类型化的 XML 与非类型化的 XML 的比较 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xml data type [SQL Server], variables
- parameters [XML in SQL Server]
- facets [XML in SQL Server]
- xml data type [SQL Server], columns
- untyped XML
- xml data type [SQL Server], typed xml
- XML [SQL Server], typed
- variables [XML in SQL Server], creating
- xml data type [SQL Server], untyped xml
- columns [XML in SQL Server], creating
- typed XML
- document mode processing [SQL Server]
- XML [SQL Server], untyped
- xml data type [SQL Server], parameters
ms.assetid: 4bc50af9-2f7d-49df-bb01-854d080c72c7
author: rothja
ms.author: jroth
ms.openlocfilehash: fae9ca930bd8741a1332b61c8272f2133590483e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688659"
---
# <a name="compare-typed-xml-to-untyped-xml"></a><span data-ttu-id="e4e18-102">类型化的 XML 与非类型化的 XML 的比较</span><span class="sxs-lookup"><span data-stu-id="e4e18-102">Compare Typed XML to Untyped XML</span></span>
  <span data-ttu-id="e4e18-103">您可以创建 `xml` 类型的变量、参数和列。</span><span class="sxs-lookup"><span data-stu-id="e4e18-103">You can create variables, parameters, and columns of the `xml` type.</span></span> <span data-ttu-id="e4e18-104">您也可以将 XML 架构的集合与 `xml` 类型的变量、参数或列关联起来。</span><span class="sxs-lookup"><span data-stu-id="e4e18-104">You can optionally associate a collection of XML schemas with a variable, parameter, or column of `xml` type.</span></span> <span data-ttu-id="e4e18-105">在这种情况下， `xml` 数据类型实例称为*类型化*。</span><span class="sxs-lookup"><span data-stu-id="e4e18-105">In this case, the `xml` data type instance is called *typed*.</span></span> <span data-ttu-id="e4e18-106">否则，XML 实例称作“非类型化” 的实例。</span><span class="sxs-lookup"><span data-stu-id="e4e18-106">Otherwise, the XML instance is called *untyped*.</span></span>  
  
## <a name="well-formed-xml-and-the-xml-data-type"></a><span data-ttu-id="e4e18-107">格式正确的 XML 和 xml 数据类型</span><span class="sxs-lookup"><span data-stu-id="e4e18-107">Well-formed XML and the xml Data Type</span></span>  
 <span data-ttu-id="e4e18-108">`xml` 数据类型可实现 ISO 标准的 `xml` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="e4e18-108">The `xml` data type implements the ISO standard `xml` data type.</span></span> <span data-ttu-id="e4e18-109">因此，它可以在非类型化的 XML 列中存储格式正确的 XML 1.0 版的文档以及具有文本节点和任意数量顶级元素的所谓的 XML 内容片段。</span><span class="sxs-lookup"><span data-stu-id="e4e18-109">Therefore, it can store well-formed XML version 1.0 documents and also so-called XML content fragments with text nodes and an arbitrary number of top-level elements in an untyped XML column.</span></span> <span data-ttu-id="e4e18-110">系统将检查数据格式是否正确，但不要求将列绑定到 XML 架构，并且拒绝在扩展意义上格式不正确的数据。</span><span class="sxs-lookup"><span data-stu-id="e4e18-110">The system checks that the data is well-formed, does not require the column to be bound to XML schemas, and rejects data that is not well-formed in the extended sense.</span></span> <span data-ttu-id="e4e18-111">对于非类型化的 XML 变量和参数也是如此。</span><span class="sxs-lookup"><span data-stu-id="e4e18-111">This is true also of untyped XML variables and parameters.</span></span>  
  
## <a name="xml-schemas"></a><span data-ttu-id="e4e18-112">XML 架构</span><span class="sxs-lookup"><span data-stu-id="e4e18-112">XML Schemas</span></span>  
 <span data-ttu-id="e4e18-113">XML 架构提供以下信息：</span><span class="sxs-lookup"><span data-stu-id="e4e18-113">An XML schema provides the following:</span></span>  
  
-   <span data-ttu-id="e4e18-114">**验证约束。**</span><span class="sxs-lookup"><span data-stu-id="e4e18-114">**Validation constraints.**</span></span> <span data-ttu-id="e4e18-115">每当向类型化的 xml 实例赋值或修改这样的实例时，SQL Server 都将验证该实例。</span><span class="sxs-lookup"><span data-stu-id="e4e18-115">Whenever a typed xml instance is assigned to or modified, SQL Server validates the instance.</span></span>  
  
-   <span data-ttu-id="e4e18-116">**数据类型信息。**</span><span class="sxs-lookup"><span data-stu-id="e4e18-116">**Data type information.**</span></span> <span data-ttu-id="e4e18-117">架构提供有关 `xml` 数据类型实例中属性和元素的类型的信息。</span><span class="sxs-lookup"><span data-stu-id="e4e18-117">Schemas provide information about the types of attributes and elements in the `xml` data type instance.</span></span> <span data-ttu-id="e4e18-118">与非类型化的 `xml` 可以提供的操作语义相比，类型信息为实例中包含的值提供了更精确的操作语义。</span><span class="sxs-lookup"><span data-stu-id="e4e18-118">The type information provides more precise operational semantics to the values contained in the instance than is possible with untyped `xml`.</span></span> <span data-ttu-id="e4e18-119">例如，可以对十进制值执行十进制算术运算，而不能对字符串值执行十进制算术运算。</span><span class="sxs-lookup"><span data-stu-id="e4e18-119">For example, decimal arithmetic operations can be performed on a decimal value, but not on a string value.</span></span> <span data-ttu-id="e4e18-120">因此，与非类型化的 XML 相比，可以对类型化的 XML 存储进行更大程度的压缩。</span><span class="sxs-lookup"><span data-stu-id="e4e18-120">Because of this, typed XML storage can be made significantly more compact than untyped XML.</span></span>  
  
## <a name="choosing-typed-or-untyped-xml"></a><span data-ttu-id="e4e18-121">选择类型化或非类型化的 XML</span><span class="sxs-lookup"><span data-stu-id="e4e18-121">Choosing Typed or Untyped XML</span></span>  
 <span data-ttu-id="e4e18-122">在下列情况下，使用非类型化的 `xml` 数据类型：</span><span class="sxs-lookup"><span data-stu-id="e4e18-122">Use untyped `xml` data type in the following situations:</span></span>  
  
-   <span data-ttu-id="e4e18-123">您没有对应于您的 XML 数据的架构。</span><span class="sxs-lookup"><span data-stu-id="e4e18-123">You do not have a schema for your XML data.</span></span>  
  
-   <span data-ttu-id="e4e18-124">您有架构，但不希望服务器验证数据。</span><span class="sxs-lookup"><span data-stu-id="e4e18-124">You have schemas, but you do not want the server to validate the data.</span></span> <span data-ttu-id="e4e18-125">当应用程序将数据存储到服务器之前会执行客户端验证时，临时存储对该架构而言无效的 XML 数据时，或在服务器上使用不支持的架构组件时，需要如此。</span><span class="sxs-lookup"><span data-stu-id="e4e18-125">This is sometimes the case when an application performs client-side validation before storing the data at the server, or temporarily stores XML data that is invalid according to the schema, or uses schema components that are not supported at the server.</span></span>  
  
 <span data-ttu-id="e4e18-126">`xml`在以下情况下使用类型化数据类型：</span><span class="sxs-lookup"><span data-stu-id="e4e18-126">Use typed `xml` data type in the following situations:</span></span>  
  
-   <span data-ttu-id="e4e18-127">您有对应于您的 XML 数据的架构，并且希望服务器根据 XML 架构验证您的 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="e4e18-127">You have schemas for your XML data and you want the server to validate your XML data according to the XML schemas.</span></span>  
  
-   <span data-ttu-id="e4e18-128">您希望利用基于类型信息的存储和查询优化。</span><span class="sxs-lookup"><span data-stu-id="e4e18-128">You want to take advantage of storage and query optimizations based on type information.</span></span>  
  
-   <span data-ttu-id="e4e18-129">您希望在编译查询过程中更好地利用类型信息。</span><span class="sxs-lookup"><span data-stu-id="e4e18-129">You want to take better advantage of type information during compilation of your queries.</span></span>  
  
 <span data-ttu-id="e4e18-130">类型化的 XML 列、参数和变量可以存储 XML 文档或内容。</span><span class="sxs-lookup"><span data-stu-id="e4e18-130">Typed XML columns, parameters, and variables can store XML documents or content.</span></span> <span data-ttu-id="e4e18-131">但是，在声明时必须使用标志指定是存储文档还是存储内容。</span><span class="sxs-lookup"><span data-stu-id="e4e18-131">However, you have to specify with a flag whether you are storing a document or content at the time of declaration.</span></span> <span data-ttu-id="e4e18-132">此外，必须提供 XML 架构集合。</span><span class="sxs-lookup"><span data-stu-id="e4e18-132">Additionally, you have to provide the collection of XML schemas.</span></span> <span data-ttu-id="e4e18-133">如果每个 XML 实例都刚好有一个顶级元素，请指定 DOCUMENT。</span><span class="sxs-lookup"><span data-stu-id="e4e18-133">Specify DOCUMENT if each XML instance has exactly one top-level element.</span></span> <span data-ttu-id="e4e18-134">否则，请使用 CONTENT。</span><span class="sxs-lookup"><span data-stu-id="e4e18-134">Otherwise, use CONTENT.</span></span> <span data-ttu-id="e4e18-135">查询编译器在查询编译期间的类型检查过程中使用 DOCUMENT 标志来推断单独的顶级元素。</span><span class="sxs-lookup"><span data-stu-id="e4e18-135">The query compiler uses the DOCUMENT flag in type checks during query compilation to infer singleton top-level elements.</span></span>  
  
## <a name="creating-typed-xml"></a><span data-ttu-id="e4e18-136">创建类型化的 XML</span><span class="sxs-lookup"><span data-stu-id="e4e18-136">Creating Typed XML</span></span>  
 <span data-ttu-id="e4e18-137">创建类型化 `xml` 变量、参数或列之前，必须先使用[CREATE XML schema Collection &#40;transact-sql&#41;](/sql/t-sql/statements/create-xml-schema-collection-transact-sql)来注册 XML 架构集合。</span><span class="sxs-lookup"><span data-stu-id="e4e18-137">Before you can create typed `xml` variables, parameters, or columns, you must first register the XML schema collection by using [CREATE XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-xml-schema-collection-transact-sql).</span></span> <span data-ttu-id="e4e18-138">接下来，您就可以将 XML 架构集合与 `xml` 数据类型的变量、参数或列关联起来。</span><span class="sxs-lookup"><span data-stu-id="e4e18-138">You can then associate the XML schema collection with variables, parameters, or columns of the `xml` data type.</span></span>  
  
 <span data-ttu-id="e4e18-139">在下列示例中，使用由两部分组成的名称命名约定指定 XML 架构集合名称。</span><span class="sxs-lookup"><span data-stu-id="e4e18-139">In the following examples, a two-part naming convention is used for specifying the XML schema collection name.</span></span> <span data-ttu-id="e4e18-140">第一部分是架构名称，第二部分是 XML 架构集合名称。</span><span class="sxs-lookup"><span data-stu-id="e4e18-140">The first part is the schema name, and the second part is the XML schema collection name.</span></span>  
  
### <a name="example-associating-a-schema-collection-with-an-xml-type-variable"></a><span data-ttu-id="e4e18-141">示例：将架构集合与 xml 类型变量关联起来</span><span class="sxs-lookup"><span data-stu-id="e4e18-141">Example: Associating a Schema Collection with an xml Type Variable</span></span>  
 <span data-ttu-id="e4e18-142">下面的示例创建一个 `xml` 类型变量并将架构集合与其关联。</span><span class="sxs-lookup"><span data-stu-id="e4e18-142">The following example creates an`xml` type variable and associates a schema collection with it.</span></span> <span data-ttu-id="e4e18-143">该示例中指定的架构集合已导入 **AdventureWorks** 数据库。</span><span class="sxs-lookup"><span data-stu-id="e4e18-143">The schema collection specified in the example is already imported in the **AdventureWorks** database.</span></span>  
  
```  
DECLARE @x xml (Production.ProductDescriptionSchemaCollection);   
```  
  
### <a name="example-specifying-a-schema-for-an-xml-type-column"></a><span data-ttu-id="e4e18-144">示例：为 xml 类型列指定架构</span><span class="sxs-lookup"><span data-stu-id="e4e18-144">Example: Specifying a Schema for an xml Type Column</span></span>  
 <span data-ttu-id="e4e18-145">下面的示例创建一个包含 `xml` 类型列的表，并为该列指定了一个架构：</span><span class="sxs-lookup"><span data-stu-id="e4e18-145">The following example creates a table with an `xml` type column and specifies a schema for the column:</span></span>  
  
```  
CREATE TABLE T1(  
 Col1 int,   
 Col2 xml (Production.ProductDescriptionSchemaCollection)) ;  
```  
  
### <a name="example-passing-an-xml-type-parameter-to-a-stored-procedure"></a><span data-ttu-id="e4e18-146">示例：将 xml 类型参数传递给存储过程</span><span class="sxs-lookup"><span data-stu-id="e4e18-146">Example: Passing an xml Type Parameter to a Stored Procedure</span></span>  
 <span data-ttu-id="e4e18-147">下面的示例将 `xml` 类型参数传递给存储过程，并为该变量指定一个架构：</span><span class="sxs-lookup"><span data-stu-id="e4e18-147">The following example passes an `xml` type parameter to a stored procedure and specifies a schema for the variable:</span></span>  
  
```  
CREATE PROCEDURE SampleProc   
  @ProdDescription xml (Production.ProductDescriptionSchemaCollection)   
AS   
...  
```  
  
 <span data-ttu-id="e4e18-148">注意有关 XML 架构集合的以下事项：</span><span class="sxs-lookup"><span data-stu-id="e4e18-148">Note the following about the XML schema collection:</span></span>  
  
-   <span data-ttu-id="e4e18-149">XML 架构集合只有在通过 [创建 XML 架构集合](/sql/t-sql/statements/create-xml-schema-collection-transact-sql)注册该集合的数据库中才可用。</span><span class="sxs-lookup"><span data-stu-id="e4e18-149">An XML schema collection is available only in the database in which it was registered by using [Creating an XML Schema Collection](/sql/t-sql/statements/create-xml-schema-collection-transact-sql).</span></span>  
  
-   <span data-ttu-id="e4e18-150">如果从字符串转换到类型化的 `xml` 数据类型，则分析过程还将根据指定集合中的 XML 架构命名空间执行验证和类型化。</span><span class="sxs-lookup"><span data-stu-id="e4e18-150">If you cast from a string to a typed `xml` data type, the parsing also performs validation and typing, based on the XML schema namespaces in the collection specified.</span></span>  
  
-   <span data-ttu-id="e4e18-151">可以从类型化的 `xml` 数据类型转换到非类型化的 `xml` 数据类型，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="e4e18-151">You can cast from a typed `xml` data type to an untyped `xml` data type, and vice versa.</span></span>  
  
 <span data-ttu-id="e4e18-152">有关在 SQL Server 中生成 XML 的其他方法的详细信息，请参阅 [创建 XML 数据的实例](create-instances-of-xml-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e4e18-152">For more information about other ways to generate XML in SQL Server, see [Create Instances of XML Data](create-instances-of-xml-data.md).</span></span> <span data-ttu-id="e4e18-153">生成 XML 后，可以将其赋给 `xml` 数据类型变量，也可以将其存储在 `xml` 类型列中以进行其他处理。</span><span class="sxs-lookup"><span data-stu-id="e4e18-153">After XML is generated, it can be assigned either to an `xml` data type variable or stored in `xml` type columns for additional processing.</span></span>  
  
 <span data-ttu-id="e4e18-154">在数据类型层次结构中，`xml` 数据类型显示在 `sql_variant` 和用户定义类型之下，但显示在所有内置类型之上。</span><span class="sxs-lookup"><span data-stu-id="e4e18-154">In the data type hierarchy, the `xml` data type appears below `sql_variant` and user-defined types, but above any of the built-in types.</span></span>  
  
### <a name="example-specifying-facets-to-constrain-a-typed-xml-column"></a><span data-ttu-id="e4e18-155">示例：指定用于约束类型化的 xml 列的方面</span><span class="sxs-lookup"><span data-stu-id="e4e18-155">Example: Specifying Facets to Constrain a Typed xml Column</span></span>  
 <span data-ttu-id="e4e18-156">对于类型化的 `xml` 列，可以对这样的列实施约束，使之仅允许存储每个实例的单独的顶级元素。</span><span class="sxs-lookup"><span data-stu-id="e4e18-156">For typed `xml` columns, you can constrain the column to allow only single, top-level elements for each instance stored in it.</span></span> <span data-ttu-id="e4e18-157">可以在创建了表以后通过指定可选的 `DOCUMENT` 方面来进行此操作，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="e4e18-157">You do this by specifying the optional `DOCUMENT` facet when a table is created, as shown in the following example:</span></span>  
  
```  
CREATE TABLE T(Col1 xml   
   (DOCUMENT Production.ProductDescriptionSchemaCollection));  
GO  
DROP TABLE T;  
GO  
```  
  
 <span data-ttu-id="e4e18-158">默认情况下，类型化的 `xml` 列中存储的实例作为 XML 内容而非 XML 文档存储。</span><span class="sxs-lookup"><span data-stu-id="e4e18-158">By default, instances stored in the typed `xml` column are stored as XML content and not as XML documents.</span></span> <span data-ttu-id="e4e18-159">这允许存储以下内容：</span><span class="sxs-lookup"><span data-stu-id="e4e18-159">This allows for the following:</span></span>  
  
-   <span data-ttu-id="e4e18-160">零个或多个顶级元素</span><span class="sxs-lookup"><span data-stu-id="e4e18-160">Zero or many top-level elements</span></span>  
  
-   <span data-ttu-id="e4e18-161">顶级元素中的文本节点</span><span class="sxs-lookup"><span data-stu-id="e4e18-161">Text nodes in top-level elements</span></span>  
  
 <span data-ttu-id="e4e18-162">还可以通过添加 `CONTENT` 方面显式指定此行为，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="e4e18-162">You can also explicitly specify this behavior by adding `CONTENT` facet, as shown in the following example:</span></span>  
  
```  
CREATE TABLE T(Col1 xml(CONTENT Production.ProductDescriptionSchemaCollection));  
GO -- Default  
```  
  
 <span data-ttu-id="e4e18-163">请注意，可以在定义 `xml` 类型（类型化的 xml）的任何位置指定可选的 DOCUMENT/CONTENT 方面。</span><span class="sxs-lookup"><span data-stu-id="e4e18-163">Note that you can specify the optional DOCUMENT/CONTENT facets anywhere you define `xml` type (typed xml).</span></span> <span data-ttu-id="e4e18-164">例如，创建类型化的 `xml` 变量时，可以添加 DOCUMENT/CONTENT 方面，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e4e18-164">For example, when you create a typed `xml` variable, you can add the DOCUMENT/CONTENT facet, as shown in the following:</span></span>  
  
```  
declare @x xml (DOCUMENT Production.ProductDescriptionSchemaCollection);  
```  
  
## <a name="document-type-definition-dtd"></a><span data-ttu-id="e4e18-165">文档类型定义 (DTD)</span><span class="sxs-lookup"><span data-stu-id="e4e18-165">Document Type Definition (DTD)</span></span>  
 <span data-ttu-id="e4e18-166">可以使用 XML 架构类型化 `xml` 数据类型列、变量和参数，但不可使用 DTD 类型化它们。</span><span class="sxs-lookup"><span data-stu-id="e4e18-166">The `xml` data type columns, variables, and parameters can be typed by using XML schema, but not by using DTD.</span></span> <span data-ttu-id="e4e18-167">但是，内联 DTD 既可用于非类型化的 XML，也可用于类型化的 XML，以便提供默认值，并将实体引用替换为其扩展形式。</span><span class="sxs-lookup"><span data-stu-id="e4e18-167">However, inline DTD can be used for both untyped and typed XML to supply default values and to replace entity references with their expanded form.</span></span>  
  
 <span data-ttu-id="e4e18-168">可以通过使用第三方工具将 DTD 转换为 XML 架构文档，然后将 XML 架构加载到数据库中。</span><span class="sxs-lookup"><span data-stu-id="e4e18-168">You can convert DTDs to XML schema documents by using third-party tools, and load the XML schemas into the database.</span></span>  
  
## <a name="upgrading-typed-xml-from-sql-server-2005"></a><span data-ttu-id="e4e18-169">从 SQL Server 2005 升级类型化 XML</span><span class="sxs-lookup"><span data-stu-id="e4e18-169">Upgrading Typed XML from SQL Server 2005</span></span>  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] <span data-ttu-id="e4e18-170">对 XML 架构支持（包括对宽松验证的支持）进行了多项扩展，改进了对 **xs:date**、 **xs:time** 和 **xs:dateTime** 实例数据的处理，并新增了对列表和联合类型的支持。</span><span class="sxs-lookup"><span data-stu-id="e4e18-170">made several extensions to the XML Schema support, including support for lax validation, improved handling of **xs:date**, **xs:time** and **xs:dateTime** instance data, and added support for list and union types.</span></span> <span data-ttu-id="e4e18-171">大多数情况下，这些更改不会影响升级过程。</span><span class="sxs-lookup"><span data-stu-id="e4e18-171">In most cases the changes do not affect the upgrade experience.</span></span> <span data-ttu-id="e4e18-172">但是，如果你使用了 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中允许使用 **xs:date**、 **xs:time**或 **xs:dateTime** （或任何子类型）类型的值的 XML 架构集合，则在将 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 数据库附加到更高版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]时将执行以下升级步骤：</span><span class="sxs-lookup"><span data-stu-id="e4e18-172">However if you used an XML Schema collection in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] that allowed values of type **xs:date**, **xs:time**, or **xs:dateTime** (or any subtype) then the following upgrade steps occur when you attach your [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] database to a later version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
1.  <span data-ttu-id="e4e18-173">对于每个 XML 列，如果该列是使用包含特定元素或属性（这些元素或属性被类型化为 **xs:anyType**、 **xs:anySimpleType**、 **xs:date** 或其任何子类型、 **xs:time** 或其任何子类型、 **xs:dateTime** 或其任何子类型，或者属于包含上述任何类型的联合类型或列表类型）的 XML 架构集合进行类型化的，将会执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="e4e18-173">For every XML column, that is typed with an XML Schema Collection that contains elements or attributes that are typed as either **xs:anyType**, **xs:anySimpleType**, **xs:date** or any of its subtypes, **xs:time** or any subtype thereof, or **xs:dateTime** or any of its subtypes, or are union or list types containing any of these types the following occurs:</span></span>  
  
    1.  <span data-ttu-id="e4e18-174">将禁用该列的所有 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="e4e18-174">All XML indices on the column will be disabled.</span></span>  
  
    2.  <span data-ttu-id="e4e18-175">将继续采用 Z 时区表示所有 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 值，这是因为已针对 Z 时区将这些值规范化。</span><span class="sxs-lookup"><span data-stu-id="e4e18-175">All [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] values will continue to be represented in the Z timezone, because they have been normalized to the Z timezone.</span></span>  
  
    3.  <span data-ttu-id="e4e18-176">任何小于元年 1 月 1 日的 **xs:date** 或 **xs:dateTime** 值在重新生成索引或对包含该值的 XML 数据类型执行 XQuery 或 XML-DML 语句时都将导致运行时错误。</span><span class="sxs-lookup"><span data-stu-id="e4e18-176">Any **xs:date** or **xs:dateTime** values that are smaller than January 1st of year 1 will lead to a runtime error when the index gets rebuild or an XQuery or XML-DML statements gets executed against the XML data type containing that value.</span></span>  
  
2.  <span data-ttu-id="e4e18-177">**xs:date** 或 **xs:dateTime** 方面中的任何负年份或 XML 架构集合中的默认值都将自动更新为基 **xs:date** 或 **xs:dateTime** 类型允许的最小值（例如，对于 **xs:dateTime**，则更新为 0001-01-01T00:00:00.0000000Z）。</span><span class="sxs-lookup"><span data-stu-id="e4e18-177">Any negative years in **xs:date** or **xs:dateTime** facets or default values in an XML Schema collection will automatically be updated to the smallest value allowed by the base **xs:date** or **xs:dateTime** type (e.g., 0001-01-01T00:00:00.0000000Z for **xs:dateTime**).</span></span>  
  
 <span data-ttu-id="e4e18-178">请注意，即使 XML 数据类型包含负年份，仍可以使用简单的 SQL SELECT 语句来检索整个 XML 数据类型。</span><span class="sxs-lookup"><span data-stu-id="e4e18-178">Note that you can still use a simple SQL select statement to retrieve the whole XML data type, even if it contains negative years.</span></span> <span data-ttu-id="e4e18-179">建议您用新的受支持范围内的年份替代负年份，或将相应元素或属性的类型更改为 **xs:string**。</span><span class="sxs-lookup"><span data-stu-id="e4e18-179">It is recommended that you replace negative years with a year within the newly supported range or change the type of the element or attribute to **xs:string**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4e18-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e4e18-180">See Also</span></span>  
 <span data-ttu-id="e4e18-181">[创建 XML 数据的实例](create-instances-of-xml-data.md) </span><span class="sxs-lookup"><span data-stu-id="e4e18-181">[Create Instances of XML Data](create-instances-of-xml-data.md) </span></span>  
 <span data-ttu-id="e4e18-182">[xml 数据类型方法](/sql/t-sql/xml/xml-data-type-methods) </span><span class="sxs-lookup"><span data-stu-id="e4e18-182">[xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods) </span></span>  
 <span data-ttu-id="e4e18-183">[XML 数据修改语言 (XML DML)](/sql/t-sql/xml/xml-data-modification-language-xml-dml) </span><span class="sxs-lookup"><span data-stu-id="e4e18-183">[XML Data Modification Language &#40;XML DML&#41;](/sql/t-sql/xml/xml-data-modification-language-xml-dml) </span></span>  
 [<span data-ttu-id="e4e18-184">XML 数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e4e18-184">XML Data &#40;SQL Server&#41;</span></span>](xml-data-sql-server.md)  
  
  
