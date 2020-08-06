---
title: 通配符组成部分和内容验证 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- wildcard components [XML]
- content validation [XML]
ms.assetid: ffa7d974-3645-446c-8425-f0b22b6b060a
author: rothja
ms.author: jroth
ms.openlocfilehash: 76ff2b48efb8cff0b98827fe8522405682c294e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578745"
---
# <a name="wildcard-components-and-content-validation"></a><span data-ttu-id="44a7c-102">通配符组成部分和内容验证</span><span class="sxs-lookup"><span data-stu-id="44a7c-102">Wildcard Components and Content Validation</span></span>
  <span data-ttu-id="44a7c-103">通配符组成部分用于更加灵活地在内容模型中显示内容。</span><span class="sxs-lookup"><span data-stu-id="44a7c-103">Wildcard components are used to increase flexibility in what is allowed to appear in a content model.</span></span> <span data-ttu-id="44a7c-104">在 XSD 语言中按照以下方式支持这些组成部分：</span><span class="sxs-lookup"><span data-stu-id="44a7c-104">These components are supported in the XSD language in the following ways:</span></span>  
  
-   <span data-ttu-id="44a7c-105">元素通配符组成部分。</span><span class="sxs-lookup"><span data-stu-id="44a7c-105">Element wildcard components.</span></span> <span data-ttu-id="44a7c-106">这些组成部分通过 \<xsd:any> 元素表示。</span><span class="sxs-lookup"><span data-stu-id="44a7c-106">These are represented by the **\<xsd:any>** element.</span></span>  
  
-   <span data-ttu-id="44a7c-107">属性通配符组成部分。</span><span class="sxs-lookup"><span data-stu-id="44a7c-107">Attribute wildcard components.</span></span> <span data-ttu-id="44a7c-108">这些组成部分通过 \<xsd:anyAttribute> 元素表示。</span><span class="sxs-lookup"><span data-stu-id="44a7c-108">These are represented by the **\<xsd:anyAttribute>** element.</span></span>  
  
 <span data-ttu-id="44a7c-109">这两个通配符元素（\<xsd:any> 和 \<xsd:anyAttribute>）都支持使用 processContents 属性  。</span><span class="sxs-lookup"><span data-stu-id="44a7c-109">Both wildcard character elements, **\<xsd:any>** and **\<xsd:anyAttribute>**, support the use of a **processContents** attribute.</span></span> <span data-ttu-id="44a7c-110">这将允许您指定特定的值，该值指示 XML 应用程序如何处理与这些通配符元素关联的文档内容的验证。</span><span class="sxs-lookup"><span data-stu-id="44a7c-110">This lets you specify a value that indicates how XML applications handle the validation of document content associated with these wildcard character elements.</span></span> <span data-ttu-id="44a7c-111">以下是不同的值及其作用：</span><span class="sxs-lookup"><span data-stu-id="44a7c-111">These are the different values and their effect:</span></span>  
  
-   <span data-ttu-id="44a7c-112">**strict** 值指定对内容进行完整的验证。</span><span class="sxs-lookup"><span data-stu-id="44a7c-112">The **strict** value specifies that the contents are fully validated.</span></span>  
  
-   <span data-ttu-id="44a7c-113">**skip** 值指定不对内容进行验证。</span><span class="sxs-lookup"><span data-stu-id="44a7c-113">The **skip** value specifies that the contents are not validated.</span></span>  
  
-   <span data-ttu-id="44a7c-114">**lax** 值指定仅对具有可用架构定义的元素和属性进行验证。</span><span class="sxs-lookup"><span data-stu-id="44a7c-114">The **lax** value specifies that only elements and attributes for which schema definitions are available are validated.</span></span>  
  
## <a name="lax-validation-and-xsanytype-elements"></a><span data-ttu-id="44a7c-115">宽松验证与 xs:anyType 元素</span><span class="sxs-lookup"><span data-stu-id="44a7c-115">Lax Validation and xs:anyType Elements</span></span>  
 <span data-ttu-id="44a7c-116">XML 架构规范对 **anyType** 类型的元素进行 **宽松** 验证。</span><span class="sxs-lookup"><span data-stu-id="44a7c-116">The XML Schema specification uses **lax** validation for elements of the **anyType** type.</span></span> <span data-ttu-id="44a7c-117">因为 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 不支持宽松验证，所以对 **anyType**类型的元素进行严格验证。</span><span class="sxs-lookup"><span data-stu-id="44a7c-117">Because [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] did not support lax validation, strict validation was applied for elements of the **anyType**.</span></span> <span data-ttu-id="44a7c-118">从 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]开始，支持宽松验证。</span><span class="sxs-lookup"><span data-stu-id="44a7c-118">Beginning with [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], lax validation is supported.</span></span> <span data-ttu-id="44a7c-119">**anyType** 类型的元素的内容将使用宽松验证方式进行验证。</span><span class="sxs-lookup"><span data-stu-id="44a7c-119">Content of elements of type **anyType** will be validated using lax validation.</span></span>  
  
 <span data-ttu-id="44a7c-120">下面的示例说明了宽松验证。</span><span class="sxs-lookup"><span data-stu-id="44a7c-120">The following example illustrates the lax validation.</span></span> <span data-ttu-id="44a7c-121">架构元素 `e` 属于 **anyType** 类型。</span><span class="sxs-lookup"><span data-stu-id="44a7c-121">The schema element `e` is of the **anyType** type.</span></span> <span data-ttu-id="44a7c-122">此示例创建了类型化的 **xml** 变量并说明了 **anyType** 类型的元素的宽松验证。</span><span class="sxs-lookup"><span data-stu-id="44a7c-122">The example creates typed **xml** variables and illustrates the lax validation of the element of the **anyType** type.</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"   
        targetNamespace="http://ns">  
   <element name="e" type="anyType"/>  
   <element name="a" type="byte"/>  
   <element name="b" type="string"/>  
 </schema>'  
GO  
```  
  
 <span data-ttu-id="44a7c-123">下面的示例将成功执行，因为 `<e>` 的验证会成功：</span><span class="sxs-lookup"><span data-stu-id="44a7c-123">The following example succeeds, because the validation of `<e>` is successful:</span></span>  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="http://ns"><a>1</a><b>data</b></e>'  
GO  
```  
  
 <span data-ttu-id="44a7c-124">下面的示例将成功执行。</span><span class="sxs-lookup"><span data-stu-id="44a7c-124">The following example succeeds.</span></span> <span data-ttu-id="44a7c-125">尽管架构中未定义 `<c>` 元素，仍会接受此实例：</span><span class="sxs-lookup"><span data-stu-id="44a7c-125">The instance is accepted, even though no element `<c>` is defined in the schema:</span></span>  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="http://ns"><a>1</a><c>Wrong</c><b>data</b></e>'  
GO  
```  
  
 <span data-ttu-id="44a7c-126">下面的示例中的 XML 实例将被拒绝，原因是 `<a>` 元素的定义不允许使用字符串值。</span><span class="sxs-lookup"><span data-stu-id="44a7c-126">The XML instance in the following example is rejected, because the definition of the `<a>` element does not allow a string value.</span></span>  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="http://ns"><a>Wrong</a><b>data</b></e>'  
SELECT @var  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="44a7c-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="44a7c-127">See Also</span></span>  
 [<span data-ttu-id="44a7c-128">在服务器上使用 XML 架构集合的要求和限制</span><span class="sxs-lookup"><span data-stu-id="44a7c-128">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
