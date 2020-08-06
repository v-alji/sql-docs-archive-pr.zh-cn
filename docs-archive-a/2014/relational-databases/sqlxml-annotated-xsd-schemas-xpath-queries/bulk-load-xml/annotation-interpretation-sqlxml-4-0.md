---
title: SQLXML 4.0) 的批注解释 (|Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, XML Bulk Load
- XML Bulk Load [SQLXML], annotation intepretations
- annotations [SQLXML]
- bulk load [SQLXML], annotation interpretations
- annotated XDR schemas, XML Bulk Load
ms.assetid: 1c46bdb6-2812-4a13-b60b-7101c04b299f
author: rothja
ms.author: jroth
ms.openlocfilehash: c31d56f7dd577b4b5a5b582eb0e3b1db312109a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588453"
---
# <a name="annotation-interpretation-sqlxml-40"></a><span data-ttu-id="1e131-102">批注解释 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="1e131-102">Annotation Interpretation (SQLXML 4.0)</span></span>
  <span data-ttu-id="1e131-103">本节中的主题介绍 XML 大容量加载如何解释 XSD 架构中的批注。</span><span class="sxs-lookup"><span data-stu-id="1e131-103">The topics in this section describe how XML Bulk Load interprets annotations in the XSD schema.</span></span> <span data-ttu-id="1e131-104">这里描述的行为也适用于 XDR 架构中的批注。</span><span class="sxs-lookup"><span data-stu-id="1e131-104">The behavior described here also applies to the annotations in the XDR schema.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1e131-105">这些主题中的信息仅说明了 XML 大容量加载在其处理过程中使用的批注。</span><span class="sxs-lookup"><span data-stu-id="1e131-105">The information in these topics describes only the annotations used by XML Bulk Load in its processing.</span></span> <span data-ttu-id="1e131-106">有关 SQLXML 4.0 支持的 XSD 架构的完整批注列表，请参阅[在 Xsd 架构中使用批注 &#40;sqlxml 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/using-annotations-in-xsd-schemas-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="1e131-106">For a complete list of annotations for the XSD schema that are supported by SQLXML 4.0, see [Using Annotations in XSD Schemas &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/using-annotations-in-xsd-schemas-sqlxml-4-0.md).</span></span> <span data-ttu-id="1e131-107">有关 XDR 架构支持的批注的列表，请参阅[SQLXML 4.0&#41;中 &#40;弃用的带批注 XDR 架构](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="1e131-107">For a list of supported annotations for XDR schemas, see [Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1e131-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="1e131-108">In This Section</span></span>  
 [<span data-ttu-id="1e131-109">sql：关系和键排序规则 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="1e131-109">sql:relationship and the Key Ordering Rule &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-sql-relationship-and-key-ordering-rule.md)  
 <span data-ttu-id="1e131-110">介绍在 XML 大容量加载中如何解释 `sql:relationship` 批注。</span><span class="sxs-lookup"><span data-stu-id="1e131-110">Describes how the `sql:relationship` annotation is interpreted in XML Bulk Load.</span></span>  
  
 [<span data-ttu-id="1e131-111">sql：映射 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="1e131-111">sql:mapped &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-sql-mapped.md)  
 <span data-ttu-id="1e131-112">介绍在 XML 大容量加载中如何解释 `sql:mapped` 批注。</span><span class="sxs-lookup"><span data-stu-id="1e131-112">Describes how the `sql:mapped` annotation is interpreted in XML Bulk Load.</span></span>  
  
 [<span data-ttu-id="1e131-113">sql：限制字段和 sql： &#40;SQLXML 4.0&#41;的限制值</span><span class="sxs-lookup"><span data-stu-id="1e131-113">sql:limit-field and sql:limit-value &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 <span data-ttu-id="1e131-114">介绍在 XML 大容量加载中如何解释 `sql:limit-field` 和 `sql:limit-value` 批注。</span><span class="sxs-lookup"><span data-stu-id="1e131-114">Describes how the `sql:limit-field` and `sql:limit-value` annotations are interpreted in XML Bulk Load.</span></span>  
  
 [<span data-ttu-id="1e131-115">sql：溢出-字段 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="1e131-115">sql:overflow-field &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-sql-overflow-field.md)  
 <span data-ttu-id="1e131-116">介绍在 XML 大容量加载中如何解释 `sql:overflow` 批注。</span><span class="sxs-lookup"><span data-stu-id="1e131-116">Describes how the `sql:overflow` annotation is interpreted in XML Bulk Load.</span></span>  
  
 [<span data-ttu-id="1e131-117">SQLXML 4.0&#41;的其他批注 &#40;</span><span class="sxs-lookup"><span data-stu-id="1e131-117">Other Annotations &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-other-annotations.md)  
 <span data-ttu-id="1e131-118">介绍在 XML 大容量加载中如何解释以下批注：`sql:id-prefix`，`sql:use-cdata`，`sql:url-encode`，`sql:is-mapping-schema`，`sql:key-fields`。</span><span class="sxs-lookup"><span data-stu-id="1e131-118">Describes how the following annotations are interpreted in XML Bulk Load: `sql:id-prefix`, `sql:use-cdata`, `sql:url-encode`, `sql:is-mapping-schema`, `sql:key-fields`.</span></span>  
  
  
