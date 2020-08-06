---
title: 使用 XSD 架构中的批注 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, about annotated XSD schemas
- annotations [SQLXML]
- relationships [SQLXML]
- relationships [SQLXML], hierarchical relationships
- hierarchical relationships [SQLXML]
- mapping schema [SQLXML], scenarios for using
ms.assetid: 78f318a4-7a36-473b-9852-a4bae6940ce5
author: rothja
ms.author: jroth
ms.openlocfilehash: e2be94aa5815593d7a5a2e0c00bcd8849e81484e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586595"
---
# <a name="using-annotations-in-xsd-schemas-sqlxml-40"></a><span data-ttu-id="f9d5a-102">在 XSD 架构中使用批注 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="f9d5a-102">Using Annotations in XSD Schemas (SQLXML 4.0)</span></span>
  <span data-ttu-id="f9d5a-103">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML 4.0 中，XSD 架构语言对批注的支持方式与在 XML 数据简化 (XDR) 架构语言中引入的批注支持方式相似。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML 4.0, the XSD schema language supports annotations in a manner similar to the annotations introduced in the XML-Data Reduced (XDR) schema language.</span></span> <span data-ttu-id="f9d5a-104">XSD 中还引入了 XDR 不支持的其他批注。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-104">There are additional annotations introduced in XSD that are not supported in XDR.</span></span>  
  
 <span data-ttu-id="f9d5a-105">这些批注可在 XSD 架构中用于指定 XML 到关系映射。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-105">These annotations can be used within the XSD schema to specify XML-to-relational mapping.</span></span> <span data-ttu-id="f9d5a-106">这包括 XSD 架构中的元素和属性到数据库中表（视图）和列之间的映射。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-106">This includes mapping between elements and attributes in the XSD schema to tables (views) and columns in the databases.</span></span>  
  
 <span data-ttu-id="f9d5a-107">如果未指定批注，则进行默认映射。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-107">If you do not specify the annotations, default mapping takes place.</span></span> <span data-ttu-id="f9d5a-108">默认情况下，复杂类型的 XSD 元素映射为指定数据库中的表（视图）名称，而简单类型的元素或属性映射为与该元素或属性同名的列。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-108">By default, an XSD element with a complex type maps to a table (view) name in the specified database, and an element or attribute with a simple type maps to the column with the same name as the element or attribute.</span></span>  
  
 <span data-ttu-id="f9d5a-109">这些批注也可用于指定 XML 中的层次结构关系，从而表示数据库中的关系，因为 XSD 架构只是关系数据的 XML 视图。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-109">These annotations can also be used to specify the hierarchical relationships in XML-thus representing the relationships in the database, because an XSD schema is simply an XML view of relational data.</span></span>  
  
 <span data-ttu-id="f9d5a-110">此部分提供了可用于 XSD 架构的批注的描述及其用法的示例。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-110">This section provides descriptions of the annotations you can use with XSD schemas and examples of their usage.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f9d5a-111">此部分中的所有示例针对每个示例中描述的带有批注的 XSD 架构指定了简单的 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-111">All the examples in this section specify simple XPath queries against the annotated XSD schema described in each example.</span></span> <span data-ttu-id="f9d5a-112">本部分假定您熟悉 XPath 语言。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-112">Familiarity with the XPath language is assumed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f9d5a-113">本节内容</span><span class="sxs-lookup"><span data-stu-id="f9d5a-113">In This Section</span></span>  
 [<span data-ttu-id="f9d5a-114">SQLXML 4.0 &#40;的 XSD 批注&#41;</span><span class="sxs-lookup"><span data-stu-id="f9d5a-114">XSD Annotations &#40;SQLXML 4.0&#41;</span></span>](xsd-annotations-sqlxml-4-0.md)  
 <span data-ttu-id="f9d5a-115">列出了可用于 XSD 架构的批注、相关描述及等效的 XDR 批注。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-115">Lists the annotations you can use with XSD schemas, their descriptions, and the equivalent annotations for XDR.</span></span>  
  
 [<span data-ttu-id="f9d5a-116">XSD 元素和属性到表和列的默认映射 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="f9d5a-116">Default Mapping of XSD Elements and Attributes to Tables and Columns &#40;SQLXML 4.0&#41;</span></span>](default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
 <span data-ttu-id="f9d5a-117">说明默认映射，并提供与默认映射相关的任务示例。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-117">Explains default mapping and provides examples of tasks related to default mapping.</span></span>  
  
 [<span data-ttu-id="f9d5a-118">XSD 元素和属性到表和列的显式映射 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="f9d5a-118">Explicit Mapping of XSD Elements and Attributes to Tables and Columns &#40;SQLXML 4.0&#41;</span></span>](explicit-mapping-xsd-elements-and-attributes-to-tables-and-columns.md)  
 <span data-ttu-id="f9d5a-119">说明带有 `sql:relation` 和 `sql:field` 批注的显式映射，并提供示例。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-119">Explains explicit mapping with the `sql:relation` and `sql:field` annotations, and provides examples.</span></span>  
  
 [<span data-ttu-id="f9d5a-120">使用 sql： relationship 指定关系 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="f9d5a-120">Specifying Relationships Using sql:relationship &#40;SQLXML 4.0&#41;</span></span>](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
 <span data-ttu-id="f9d5a-121">介绍并提供 `sql:relationship` 批注的示例。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-121">Describes and provides examples of the `sql:relationship` annotation.</span></span>  
  
 [<span data-ttu-id="f9d5a-122">在 sql： relationship 上指定 sql：反向特性 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="f9d5a-122">Specifying the sql:inverse Attribute on sql:relationship &#40;SQLXML 4.0&#41;</span></span>](specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)  
 <span data-ttu-id="f9d5a-123">介绍 `sql:inverse` 批注。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-123">Describes the `sql:inverse` annotation.</span></span>  
  
 [<span data-ttu-id="f9d5a-124">使用 sql 创建常量元素：是常量 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="f9d5a-124">Creating Constant Elements Using sql:is-constant &#40;SQLXML 4.0&#41;</span></span>](creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)  
 <span data-ttu-id="f9d5a-125">介绍并提供 `sql:is-constant` 批注的示例。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-125">Describes and provides examples of the `sql:is-constant` annotation.</span></span>  
  
 [<span data-ttu-id="f9d5a-126">使用 sql：映射 &#40;SQLXML 4.0&#41;从生成的 XML 文档中排除架构元素</span><span class="sxs-lookup"><span data-stu-id="f9d5a-126">Excluding Schema Elements from the Resulting XML Document Using sql:mapped &#40;SQLXML 4.0&#41;</span></span>](excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)  
 <span data-ttu-id="f9d5a-127">介绍并提供 `sql:mapped` 批注的示例。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-127">Describes and provides examples of the `sql:mapped` annotation.</span></span>  
  
 [<span data-ttu-id="f9d5a-128">使用 sql： limit 字段和 sql： limit-value &#40;SQLXML 4.0&#41;筛选值</span><span class="sxs-lookup"><span data-stu-id="f9d5a-128">Filtering Values Using sql:limit-field and sql:limit-value &#40;SQLXML 4.0&#41;</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 <span data-ttu-id="f9d5a-129">介绍并提供 `sql:limit-field` 和 `sql:limit-value` 批注的示例。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-129">Describes and provides examples of the `sql:limit-field` and `sql:limit-value` annotations.</span></span>  
  
 [<span data-ttu-id="f9d5a-130">使用 sql：键字段 &#40;SQLXML 4.0&#41;标识键列</span><span class="sxs-lookup"><span data-stu-id="f9d5a-130">Identifying Key Columns Using sql:key-fields &#40;SQLXML 4.0&#41;</span></span>](identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)  
 <span data-ttu-id="f9d5a-131">介绍并提供 `sql:key-fields` 批注的示例。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-131">Describes and provides examples of the `sql:key-fields` annotation.</span></span>  
  
 [<span data-ttu-id="f9d5a-132">使用 targetNamespace 属性指定目标命名空间 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="f9d5a-132">Specifying a Target Namespace Using the targetNamespace Attribute &#40;SQLXML 4.0&#41;</span></span>](specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
 <span data-ttu-id="f9d5a-133">描述和提供**targetNamespace**特性的示例。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-133">Describes and provides examples of the **targetNamespace** attribute.</span></span>  
  
 [<span data-ttu-id="f9d5a-134">使用 sql： prefix 创建有效的 ID、IDREF 和 IDREFS 类型属性 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="f9d5a-134">Creating Valid ID, IDREF, and IDREFS Type Attributes Using sql:prefix &#40;SQLXML 4.0&#41;</span></span>](creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)  
 <span data-ttu-id="f9d5a-135">介绍并提供 `sql:prefix` 批注的示例。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-135">Describes and provides examples of the `sql:prefix` annotation.</span></span>  
  
 [<span data-ttu-id="f9d5a-136">数据类型强制转换和 sql： datatype 批注 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="f9d5a-136">Data Type Coercions and the sql:datatype Annotation &#40;SQLXML 4.0&#41;</span></span>](data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)  
 <span data-ttu-id="f9d5a-137">介绍并提供 `sql:datatype` 批注的示例。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-137">Describes and provides examples of the `sql:datatype` annotation.</span></span>  
  
 [<span data-ttu-id="f9d5a-138">将 XSD 数据类型映射到 XPath 数据类型 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="f9d5a-138">Mapping XSD Data Types to XPath Data Types &#40;SQLXML 4.0&#41;</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md)  
 <span data-ttu-id="f9d5a-139">提供比较 XSD、XDR 和 XPath 数据类型并列出相关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 转换的表。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-139">Provides a table that compares XSD, XDR, and XPath datatypes and lists the relevant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conversions.</span></span>  
  
 [<span data-ttu-id="f9d5a-140">使用 sql： use-CDATA 创建 CDATA 节 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="f9d5a-140">Creating CDATA Sections Using sql:use-cdata &#40;SQLXML 4.0&#41;</span></span>](creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)  
 <span data-ttu-id="f9d5a-141">介绍并提供 `sql:use-data` 批注的示例。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-141">Describes and provides examples of the `sql:use-data` annotation.</span></span>  
  
 [<span data-ttu-id="f9d5a-142">使用 sql：加码 &#40;SQLXML 4.0&#41;来请求对 BLOB 数据的 URL 引用</span><span class="sxs-lookup"><span data-stu-id="f9d5a-142">Requesting URL References to BLOB Data Using sql:encode &#40;SQLXML 4.0&#41;</span></span>](requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)  
 <span data-ttu-id="f9d5a-143">介绍并提供 `sql:encode` 批注的示例。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-143">Describes and provides examples of the `sql:encode` annotation.</span></span>  
  
 [<span data-ttu-id="f9d5a-144">使用 sql：溢出字段检索未用完的数据 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="f9d5a-144">Retrieving Unconsumed Data Using the sql:overflow-field &#40;SQLXML 4.0&#41;</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md)  
 <span data-ttu-id="f9d5a-145">介绍并提供 `sql:overflow-field` 批注的示例。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-145">Describes and provides examples of the `sql:overflow-field` annotation.</span></span>  
  
 [<span data-ttu-id="f9d5a-146">使用 sql:hide 隐藏元素和属性</span><span class="sxs-lookup"><span data-stu-id="f9d5a-146">Hiding Elements and Attributes by Using sql:hide</span></span>](hiding-elements-and-attributes-by-using-sql-hide.md)  
 <span data-ttu-id="f9d5a-147">介绍并提供 `sql:hide` 批注的示例。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-147">Describes and provides examples of the `sql:hide` annotation.</span></span>  
  
 [<span data-ttu-id="f9d5a-148">使用 sql:identity 和 sql:guid 批注</span><span class="sxs-lookup"><span data-stu-id="f9d5a-148">Using the sql:identity and sql:guid Annotations</span></span>](using-the-sql-identity-and-sql-guid-annotations.md)  
 <span data-ttu-id="f9d5a-149">介绍并提供 `sql:identity` 和 `sql:guid` 批注的示例。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-149">Describes and provides examples of the `sql:identity` and `sql:guid` annotations.</span></span>  
  
 [<span data-ttu-id="f9d5a-150">使用 sql:max-depth 指定递归关系中的深度</span><span class="sxs-lookup"><span data-stu-id="f9d5a-150">Specifying Depth in Recursive Relationships by Using sql:max-depth</span></span>](specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)  
 <span data-ttu-id="f9d5a-151">介绍并提供 `sql:max-depth` 批注的示例。</span><span class="sxs-lookup"><span data-stu-id="f9d5a-151">Describes and provides examples of the `sql:max-depth` annotation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9d5a-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f9d5a-152">See Also</span></span>  
 [<span data-ttu-id="f9d5a-153">&#40;SQLXML 4.0 的批注的架构安全注意事项&#41;</span><span class="sxs-lookup"><span data-stu-id="f9d5a-153">Annotated Schema Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)  
  
  
