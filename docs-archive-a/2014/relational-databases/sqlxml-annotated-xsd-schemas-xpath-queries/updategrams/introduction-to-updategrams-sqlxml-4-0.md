---
title: " (SQLXML 4.0) 的 Updategram 简介 |Microsoft Docs"
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- explicit schema mapping [SQLXML]
- updategrams [SQLXML], mapping schema specifying
- namespaces [SQLXML]
- updategrams [SQLXML], about updategrams
- attribute-centric mapping
- invalid characters [SQLXML]
- element-centric mapping [SQLXML]
- mapping schema [SQLXML], updategrams
- namespaces [SQLXML], updategrams
- executing updategrams [SQLXML]
- implicit schema mapping
ms.assetid: cfe24e82-a645-4f93-ab16-39c21f90cce6
author: rothja
ms.author: jroth
ms.openlocfilehash: eb2f29d7f5d86d28254dacb9c55cceb9b4c72d8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689797"
---
# <a name="introduction-to-updategrams-sqlxml-40"></a><span data-ttu-id="bf896-102">Updategram 简介 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="bf896-102">Introduction to Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="bf896-103">您可以 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 通过使用 UPDATEGRAM 或 OPENXML 函数，从现有的 XML 文档中修改) 中的数据库 (插入、更新或删除 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="bf896-103">You can modify (insert, update, or delete) a database in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] from an existing XML document by using an updategram or the OPENXML [!INCLUDE[tsql](../../../includes/tsql-md.md)] function.</span></span>  
  
 <span data-ttu-id="bf896-104">OPENXML 函数通过拆分现有 XML 文档并提供可以传递给 INSERT、UPDATE 或 DELETE 语句的行集来修改数据库。</span><span class="sxs-lookup"><span data-stu-id="bf896-104">The OPENXML function modifies a database by shredding the existing XML document and providing a rowset that can be passed to an INSERT, UPDATE, or DELETE statement.</span></span> <span data-ttu-id="bf896-105">使用 OPENXML 时，直接针对数据库表进行操作。</span><span class="sxs-lookup"><span data-stu-id="bf896-105">With OPENXML, operations are performed directly against the database tables.</span></span> <span data-ttu-id="bf896-106">因此，在行集提供程序（如表）可以显示为源时，最适合使用 OPENXML。</span><span class="sxs-lookup"><span data-stu-id="bf896-106">Therefore, OPENXML is most appropriate wherever rowset providers, such as a table, can appear as a source.</span></span>  
  
 <span data-ttu-id="bf896-107">与 OPENXML 一样，updategram 允许您在数据库中插入、更新或删除数据；不过，updategram 针对带批注的 XSD（或 XDR）架构提供的 XML 视图进行操作，例如将更新应用于映射架构提供的 XML 视图。</span><span class="sxs-lookup"><span data-stu-id="bf896-107">Like OPENXML, an updategram allows you to insert, update, or delete data in the database; however, an updategram works against the XML views provided by the annotated XSD (or an XDR) schema; for example, the updates are applied to the XML view provided by the mapping schema.</span></span> <span data-ttu-id="bf896-108">而映射架构则具有将 XML 元素和属性映射到相应的数据库表和列所需的信息。</span><span class="sxs-lookup"><span data-stu-id="bf896-108">The mapping schema, in turn, has the necessary information to map XML elements and attributes to the corresponding database tables and columns.</span></span> <span data-ttu-id="bf896-109">updategram 使用此映射信息更新数据库表和列。</span><span class="sxs-lookup"><span data-stu-id="bf896-109">The updategram uses this mapping information to update the database tables and columns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bf896-110">本文档假定您熟悉 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的模板和映射架构支持。</span><span class="sxs-lookup"><span data-stu-id="bf896-110">This documentation assumes that you are familiar with templates and mapping schema support in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bf896-111">有关详细信息，请参阅[&#40;SQLXML 4.0&#41;中带批注的 XSD 架构简介](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="bf896-111">For more information, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md).</span></span> <span data-ttu-id="bf896-112">对于使用 XDR 的旧版应用程序，请参阅[SQLXML 4.0&#41;中 &#40;弃用的带批注 XDR 架构](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="bf896-112">For legacy applications that use XDR, see [Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).</span></span>  
  
## <a name="required-namespaces-in-the-updategram"></a><span data-ttu-id="bf896-113">Updategram 中必需的命名空间</span><span class="sxs-lookup"><span data-stu-id="bf896-113">Required Namespaces in the Updategram</span></span>  
 <span data-ttu-id="bf896-114">Updategram 中的关键字（如 **\<sync>** 、 **\<before>** 和 **\<after>** ）存在于 `urn:schemas-microsoft-com:xml-updategram` 命名空间中。</span><span class="sxs-lookup"><span data-stu-id="bf896-114">The keywords in an updategram, such as **\<sync>**, **\<before>**, and **\<after>**, exist in the `urn:schemas-microsoft-com:xml-updategram` namespace.</span></span> <span data-ttu-id="bf896-115">您可以为该命名空间使用任意前缀。</span><span class="sxs-lookup"><span data-stu-id="bf896-115">The namespace prefix that you use is arbitrary.</span></span> <span data-ttu-id="bf896-116">在本文档中，用 `updg` 前缀指示 `updategram` 命名空间。</span><span class="sxs-lookup"><span data-stu-id="bf896-116">In this documentation, the `updg` prefix denotes the `updategram` namespace.</span></span>  
  
## <a name="reviewing-syntax"></a><span data-ttu-id="bf896-117">检查语法</span><span class="sxs-lookup"><span data-stu-id="bf896-117">Reviewing Syntax</span></span>  
 <span data-ttu-id="bf896-118">Updategram 是一个具有 **\<sync>** 、 **\<before>** 和 **\<after>** 块的模板，它们构成了 updategram 的语法。</span><span class="sxs-lookup"><span data-stu-id="bf896-118">An updategram is a template with **\<sync>**, **\<before>**, and **\<after>** blocks that form the syntax of the updategram.</span></span> <span data-ttu-id="bf896-119">以下代码显示了此语法的最简单形式：</span><span class="sxs-lookup"><span data-stu-id="bf896-119">The following code shows this syntax in its simplest form:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema= "AnnotatedSchemaFile.xml"] >  
    <updg:before>  
        ...  
    </updg:before>  
    <updg:after>  
        ...  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="bf896-120">以下定义描述了其中每个块的作用：</span><span class="sxs-lookup"><span data-stu-id="bf896-120">The following definitions describe the role of each of these blocks:</span></span>  
  
 **\<before>**  
 <span data-ttu-id="bf896-121">标识记录实例的现有状态（也称为“以前状态”）。</span><span class="sxs-lookup"><span data-stu-id="bf896-121">Identifies the existing state (also called "the before state") of the record instance.</span></span>  
  
 **\<after>**  
 <span data-ttu-id="bf896-122">标识要将数据更改到的新状态。</span><span class="sxs-lookup"><span data-stu-id="bf896-122">Identifies the new state to which data is to be changed.</span></span>  
  
 **\<sync>**  
 <span data-ttu-id="bf896-123">包含 **\<before>** 和 **\<after>** 块。</span><span class="sxs-lookup"><span data-stu-id="bf896-123">Contains the **\<before>** and **\<after>** blocks.</span></span> <span data-ttu-id="bf896-124">**\<sync>** 块可以包含多组 **\<before>** 和 **\<after>** 块。</span><span class="sxs-lookup"><span data-stu-id="bf896-124">A **\<sync>** block can contain more than one set of **\<before>** and **\<after>** blocks.</span></span> <span data-ttu-id="bf896-125">如果有多个 **\<before>** 和 **\<after>** 块，则这些块 (即使为空) 也必须指定为成对。</span><span class="sxs-lookup"><span data-stu-id="bf896-125">If there is more than one set of **\<before>** and **\<after>** blocks, these blocks (even if they are empty) must be specified as pairs.</span></span> <span data-ttu-id="bf896-126">此外，updategram 可以有多个 **\<sync>** 块。</span><span class="sxs-lookup"><span data-stu-id="bf896-126">Furthermore, an updategram can have more than one **\<sync>** block.</span></span> <span data-ttu-id="bf896-127">每个 **\<sync>** 块都是一个事务单元 (这意味着块中的所有内容 **\<sync>** 均已完成或未完成任何操作) 。</span><span class="sxs-lookup"><span data-stu-id="bf896-127">Each **\<sync>** block is one unit of transaction (which means that either everything in the **\<sync>** block is done or nothing is done).</span></span> <span data-ttu-id="bf896-128">如果 **\<sync>** 在 updategram 中指定多个块，则一个块的失败不 **\<sync>** 会影响其他 **\<sync>** 块。</span><span class="sxs-lookup"><span data-stu-id="bf896-128">If you specify multiple **\<sync>** blocks in an updategram, the failure of one **\<sync>** block does not affect the other **\<sync>** blocks.</span></span>  
  
 <span data-ttu-id="bf896-129">Updategram 是删除、插入还是更新记录实例取决于 **\<before>** 和块的内容 **\<after>** ：</span><span class="sxs-lookup"><span data-stu-id="bf896-129">Whether an updategram deletes, inserts, or updates a record instance depends on the contents of the **\<before>** and **\<after>** blocks:</span></span>  
  
-   <span data-ttu-id="bf896-130">如果记录实例只出现在块中 **\<before>** ，而在块中没有对应的实例 **\<after>** ，则 updategram 将执行删除操作。</span><span class="sxs-lookup"><span data-stu-id="bf896-130">If a record instance appears only in the **\<before>** block with no corresponding instance in the **\<after>** block, the updategram performs a delete operation.</span></span>  
  
-   <span data-ttu-id="bf896-131">如果记录实例只出现在块中 **\<after>** ，而在块中没有对应的实例 **\<before>** ，则是插入操作。</span><span class="sxs-lookup"><span data-stu-id="bf896-131">If a record instance appears only in the **\<after>** block with no corresponding instance in the **\<before>** block, it is an insert operation.</span></span>  
  
-   <span data-ttu-id="bf896-132">如果记录实例出现在块中 **\<before>** 并且在块中具有相应的实例 **\<after>** ，则是更新操作。</span><span class="sxs-lookup"><span data-stu-id="bf896-132">If a record instance appears in the **\<before>** block and has a corresponding instance in the **\<after>** block, it is an update operation.</span></span> <span data-ttu-id="bf896-133">在这种情况下，updategram 会将记录实例更新为在块中指定的值 **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="bf896-133">In this case, the updategram updates the record instance to the values that are specified in the **\<after>** block.</span></span>  
  
## <a name="specifying-a-mapping-schema-in-the-updategram"></a><span data-ttu-id="bf896-134">在 Updategram 中指定映射架构</span><span class="sxs-lookup"><span data-stu-id="bf896-134">Specifying a Mapping Schema in the Updategram</span></span>  
 <span data-ttu-id="bf896-135">在 updategram 中，映射架构（支持 XSD 和 XDR 架构）所提供的 XML 抽象可以是隐式的，也可以是显式的（即无论是否指定映射架构，updategram 都可以工作）。</span><span class="sxs-lookup"><span data-stu-id="bf896-135">In an updategram, the XML abstraction that is provided by a mapping schema (both XSD and XDR schemas are supported) can be implicit or explicit (that is, an updategram can work with or without a specified mapping schema).</span></span> <span data-ttu-id="bf896-136">如果未指定映射架构，则 updategram 将采用默认映射)  (隐式映射，其中块或块中的每个元素都 **\<before>** **\<after>** 映射到表，每个元素的子元素或属性映射到数据库中的列。</span><span class="sxs-lookup"><span data-stu-id="bf896-136">If you do not specify a mapping schema, the updategram assumes an implicit mapping (the default mapping), where each element in the **\<before>** block or **\<after>** block maps to a table and each element's child element or attribute maps to a column in the database.</span></span> <span data-ttu-id="bf896-137">如果显式指定映射架构，updategram 中的元素和属性必须与映射架构中的元素和属性匹配。</span><span class="sxs-lookup"><span data-stu-id="bf896-137">If you explicitly specify a mapping schema, the elements and attributes in the updategram must match the elements and attributes in the mapping schema.</span></span>  
  
### <a name="implicit-default-mapping"></a><span data-ttu-id="bf896-138">隐式（默认）映射</span><span class="sxs-lookup"><span data-stu-id="bf896-138">Implicit (default) Mapping</span></span>  
 <span data-ttu-id="bf896-139">在大多数情况下，执行简单更新的 updategram 可能不需要映射架构。</span><span class="sxs-lookup"><span data-stu-id="bf896-139">In most cases, an updategram that performs simple updates might not require a mapping schema.</span></span> <span data-ttu-id="bf896-140">此时 updategram 依赖于默认映射架构。</span><span class="sxs-lookup"><span data-stu-id="bf896-140">In this case, the updategram relies on the default mapping schema.</span></span>  
  
 <span data-ttu-id="bf896-141">以下 updategram 演示隐式映射。</span><span class="sxs-lookup"><span data-stu-id="bf896-141">The following updategram demonstrates implicit mapping.</span></span> <span data-ttu-id="bf896-142">在此示例中，updategram 在 Sales.Customer 表中插入一个新客户。</span><span class="sxs-lookup"><span data-stu-id="bf896-142">In this example, the updategram inserts a new customer in the Sales.Customer table.</span></span> <span data-ttu-id="bf896-143">由于此 updategram 使用隐式映射，因此 \<Sales.Customer> 元素映射到 customer 表，CustomerID 和 SalesPersonID 属性映射到 customer 表中的相应列。</span><span class="sxs-lookup"><span data-stu-id="bf896-143">Because this updategram uses implicit mapping, the \<Sales.Customer> element maps to the Sales.Customer table, and the CustomerID and SalesPersonID attributes map to the corresponding columns in the Sales.Customer table.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
<updg:before>  
</updg:before>  
<updg:after>  
    <Sales.Customer CustomerID="1" SalesPersonID="277" />  
    </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
### <a name="explicit-mapping"></a><span data-ttu-id="bf896-144">显式映射</span><span class="sxs-lookup"><span data-stu-id="bf896-144">Explicit Mapping</span></span>  
 <span data-ttu-id="bf896-145">如果指定映射架构（XSD 或 XDR），则 updategram 使用该架构确定要更新的数据库表和列。</span><span class="sxs-lookup"><span data-stu-id="bf896-145">If you specify a mapping schema (either XSD or XDR), the updategram uses the schema to determine the database tables and columns that are to be updated.</span></span>  
  
 <span data-ttu-id="bf896-146">如果 updategram 执行复杂更新（例如根据在映射架构中指定的父-子关系在多个表中插入记录），必须通过使用要针对其执行 updategram 的 `mapping-schema` 属性明确提供映射架构。</span><span class="sxs-lookup"><span data-stu-id="bf896-146">If the updategram performs a complex update (for example, inserting records in multiple tables on the basis of the parent-child relationship that is specified in the mapping schema), you must explicitly provide the mapping schema by using the `mapping-schema` attribute against which the updategram executes.</span></span>  
  
 <span data-ttu-id="bf896-147">由于 updategram 是模板，因此为 updategram 中的映射架构指定的路径是相对于模板文件的位置而言（即相对于存储 updategram 的位置而言）。</span><span class="sxs-lookup"><span data-stu-id="bf896-147">Because an updategram is a template, the path specified for the mapping schema in the updategram is relative to the location of the template file (relative to where the updategram is stored).</span></span> <span data-ttu-id="bf896-148">有关详细信息，请参阅[在 Updategram 中指定带批注的映射架构 &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="bf896-148">For more information, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
## <a name="element-centric-and-attribute-centric-mapping-in-updategrams"></a><span data-ttu-id="bf896-149">Updategram 中以元素为中心的映射和以属性为中心的映射</span><span class="sxs-lookup"><span data-stu-id="bf896-149">Element-centric and Attribute-centric Mapping in Updategrams</span></span>  
 <span data-ttu-id="bf896-150">使用默认映射（在 updategram 中未指定映射架构）时，如果是以元素为中心的映射，则 updategram 元素映射到表并且子元素映射到列。如果是以属性为中心的映射，则属性映射到列。</span><span class="sxs-lookup"><span data-stu-id="bf896-150">With default mapping (when the mapping schema is not specified in the updategram), the updategram elements map to tables and the  child elements (in the case of element-centric mapping) and the attributes (in the case of attribute-centric mapping) map to columns.</span></span>  
  
### <a name="element-centric-mapping"></a><span data-ttu-id="bf896-151">以元素为中心的映射</span><span class="sxs-lookup"><span data-stu-id="bf896-151">Element-centric Mapping</span></span>  
 <span data-ttu-id="bf896-152">在以元素为中心的 updategram 中，元素包含指示元素属性的子元素。</span><span class="sxs-lookup"><span data-stu-id="bf896-152">In an element-centric updategram, an element contains child elements that denote the properties of the element.</span></span> <span data-ttu-id="bf896-153">请参阅以下 updategram 示例。</span><span class="sxs-lookup"><span data-stu-id="bf896-153">As an example, refer to the following updategram.</span></span> <span data-ttu-id="bf896-154">**\<Person.Contact>** 元素包含 **\<FirstName>** 和 **\<LastName>** 子元素。</span><span class="sxs-lookup"><span data-stu-id="bf896-154">The **\<Person.Contact>** element contains the **\<FirstName>** and **\<LastName>** child elements.</span></span> <span data-ttu-id="bf896-155">这些子元素是元素的属性 **\<Person.Contact>** 。</span><span class="sxs-lookup"><span data-stu-id="bf896-155">These child elements are properties of the **\<Person.Contact>** element.</span></span>  
  
 <span data-ttu-id="bf896-156">由于此 updategram 未指定映射架构，因此 updategram 将使用隐式映射，其中 **\<Person.Contact>** 元素映射到 Person 表，而其子元素映射到 FirstName 和 LastName 列。</span><span class="sxs-lookup"><span data-stu-id="bf896-156">Because this updategram does not specify a mapping schema, the updategram uses implicit mapping, where the **\<Person.Contact>** element maps to the Person.Contact table and its child elements map to the FirstName and LastName columns.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:after>  
    <Person.Contact>  
       <FirstName>Catherine</FirstName>  
       <LastName>Abel</LastName>  
    </Person.Contact>  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
### <a name="attribute-centric-mapping"></a><span data-ttu-id="bf896-157">以属性为中心的映射</span><span class="sxs-lookup"><span data-stu-id="bf896-157">Attribute-centric Mapping</span></span>  
 <span data-ttu-id="bf896-158">在以属性为中心的映射中，元素具有属性。</span><span class="sxs-lookup"><span data-stu-id="bf896-158">In an attribute-centric mapping, the elements have attributes.</span></span> <span data-ttu-id="bf896-159">以下 updategram 使用以属性为中心的映射。</span><span class="sxs-lookup"><span data-stu-id="bf896-159">The following updategram uses attribute-centric mapping.</span></span> <span data-ttu-id="bf896-160">在此示例中， **\<Person.Contact>** 元素包含**FirstName**和**LastName**属性。</span><span class="sxs-lookup"><span data-stu-id="bf896-160">In this example, the **\<Person.Contact>** element consists of the **FirstName** and **LastName** attributes.</span></span> <span data-ttu-id="bf896-161">这些属性是元素的属性 **\<Person.Contact>** 。</span><span class="sxs-lookup"><span data-stu-id="bf896-161">These attributes are the properties of the **\<Person.Contact>** element.</span></span> <span data-ttu-id="bf896-162">如前面的示例所示，此 updategram 不指定任何映射架构，因此它依赖于隐式映射来将元素映射到 **\<Person.Contact>** 表中的相应列。</span><span class="sxs-lookup"><span data-stu-id="bf896-162">As in the previous example, this updategram specifies no mapping schema, so it relies on implicit mapping to map the **\<Person.Contact>** element to the Person.Contact table and the element's attributes to the respective columns in the table.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:before>  
  </updg:before>  
  <updg:after>  
    <Person.Contact FirstName="Catherine" LastName="Abel" />  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
### <a name="using-both-element-centric-and-attribute-centric-mapping"></a><span data-ttu-id="bf896-163">同时使用以元素为中心的映射和以属性为中心的映射</span><span class="sxs-lookup"><span data-stu-id="bf896-163">Using Both Element-centric and Attribute-centric Mapping</span></span>  
 <span data-ttu-id="bf896-164">可以组合使用以元素为中心的映射和以属性为中心的映射，如以下 updategram 中所示。</span><span class="sxs-lookup"><span data-stu-id="bf896-164">You can specify a mix of element-centric and attribute-centric mapping, as shown in the following updategram.</span></span> <span data-ttu-id="bf896-165">请注意， **\<Person.Contact>** 元素同时包含特性和子元素。</span><span class="sxs-lookup"><span data-stu-id="bf896-165">Notice that the **\<Person.Contact>** element contains both an attribute and a child element.</span></span> <span data-ttu-id="bf896-166">此 updategram 也依赖于隐式映射。</span><span class="sxs-lookup"><span data-stu-id="bf896-166">Also, this updategram relies on implicit mapping.</span></span> <span data-ttu-id="bf896-167">因此， **FirstName**属性和 **\<LastName>** 子元素映射到 Person 表中的相应列。</span><span class="sxs-lookup"><span data-stu-id="bf896-167">Thus, the **FirstName** attribute and the **\<LastName>** child element map to corresponding columns in the Person.Contact table.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:before>  
  </updg:before>  
  <updg:after>  
    <Person.Contact FirstName="Catherine" >  
       <LastName>Abel</LastName>  
    </Person.Contact>  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
## <a name="working-with-characters-valid-in-sql-server-but-not-valid-in-xml"></a><span data-ttu-id="bf896-168">使用在 SQL Server 中有效但在 XML 中无效的字符</span><span class="sxs-lookup"><span data-stu-id="bf896-168">Working with Characters Valid in SQL Server but Not Valid in XML</span></span>  
 <span data-ttu-id="bf896-169">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，表名称可以包含空格。</span><span class="sxs-lookup"><span data-stu-id="bf896-169">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], table names can include a space.</span></span> <span data-ttu-id="bf896-170">但是，此类表名称在 XML 中无效。</span><span class="sxs-lookup"><span data-stu-id="bf896-170">However, this type of table name is not valid in XML.</span></span>  
  
 <span data-ttu-id="bf896-171">若要对是有效 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 标识符，但不是有效 XML 标识符的字符进行编码，请使用 "__xHHHH \_ \_ " 作为编码值，其中 HHHH 代表最高有效位第一次的字符的四位十六进制 UCS-2 代码。</span><span class="sxs-lookup"><span data-stu-id="bf896-171">To encode characters that are valid [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] identifiers but are not valid XML identifiers, use '__xHHHH\_\_' as the encoding value, where HHHH stands for the four-digit hexadecimal UCS-2 code for the character in the most significant bit-first order.</span></span> <span data-ttu-id="bf896-172">使用此编码方案时，空格字符将被替换为一个空格字符的四位数十六进制代码) 的 (x0020;因此，中的表名 [Order Details] 在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] \_ XML 中变为 _x005B_Order_x0020_Details_x005D。</span><span class="sxs-lookup"><span data-stu-id="bf896-172">Using this encoding scheme, a space character gets replaced with x0020 (the four-digit hexadecimal code for a space character); thus, the table name [Order Details] in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] becomes _x005B_Order_x0020_Details_x005D\_ in XML.</span></span>  
  
 <span data-ttu-id="bf896-173">同样，你可能需要指定由三个部分组成的元素名称，如 \<[database].[owner].[table]> 。</span><span class="sxs-lookup"><span data-stu-id="bf896-173">Similarly, you might need to specify three-part element names, such as \<[database].[owner].[table]>.</span></span> <span data-ttu-id="bf896-174">由于方括号 ( [and] ) 在 XML 中无效，因此您必须将其指定为 \<_x005B_database_x005D\_._x005B_owner_x005D\_._x005B_table_x005D\_> ，其中 _x005B \_ 是左括号的编码 ( [) ，_x005D \_ 是右大括号的编码 (] ) 。</span><span class="sxs-lookup"><span data-stu-id="bf896-174">Because the bracket characters ([ and ]) are not valid in XML, you must specify this as \<_x005B_database_x005D\_._x005B_owner_x005D\_._x005B_table_x005D\_>, where _x005B\_ is the encoding for the left bracket ([) and _x005D\_ is the encoding for the right bracket (]).</span></span>  
  
## <a name="executing-updategrams"></a><span data-ttu-id="bf896-175">执行 Updategram</span><span class="sxs-lookup"><span data-stu-id="bf896-175">Executing Updategrams</span></span>  
 <span data-ttu-id="bf896-176">由于 updategram 是模板，因此模板的所有处理机制均适用于 updategram。</span><span class="sxs-lookup"><span data-stu-id="bf896-176">Because an updategram is a template, all the processing mechanisms of a template apply to the updategram.</span></span> <span data-ttu-id="bf896-177">对于 SQLXML 4.0，可以通过以下方式之一来执行 updategram：</span><span class="sxs-lookup"><span data-stu-id="bf896-177">For SQLXML 4.0, you can execute an updategram in either of the following ways:</span></span>  
  
-   <span data-ttu-id="bf896-178">在 ADO 命令中提交它。</span><span class="sxs-lookup"><span data-stu-id="bf896-178">By submitting it in an ADO command.</span></span>  
  
-   <span data-ttu-id="bf896-179">将其作为 OLE DB 命令提交。</span><span class="sxs-lookup"><span data-stu-id="bf896-179">By submitting it as an OLE DB command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf896-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bf896-180">See Also</span></span>  
 [<span data-ttu-id="bf896-181">&#40;SQLXML 4.0&#41;的 Updategram 安全注意事项</span><span class="sxs-lookup"><span data-stu-id="bf896-181">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
