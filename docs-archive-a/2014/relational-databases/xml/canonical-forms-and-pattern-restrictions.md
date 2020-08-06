---
title: 规范格式和模式限制 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- pattern restrictions
- canonical forms
ms.assetid: 088314ec-7d0b-4a05-8a33-f35da5bfe59c
author: rothja
ms.author: jroth
ms.openlocfilehash: 569e8c4a01ed1eb9ae26ea9e2f6d471b9aad9fe0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577439"
---
# <a name="canonical-forms-and-pattern-restrictions"></a><span data-ttu-id="76941-102">规范格式和模式限制</span><span class="sxs-lookup"><span data-stu-id="76941-102">Canonical Forms and Pattern Restrictions</span></span>
  <span data-ttu-id="76941-103">XSD 模式方面允许对简单类型的词法空间进行限制。</span><span class="sxs-lookup"><span data-stu-id="76941-103">The XSD pattern facet allows for the restriction of the lexical space of simple types.</span></span> <span data-ttu-id="76941-104">当把模式限制加在存在多个可能的词法表示形式的类型上时，某些值可能引起对验证的意外行为。</span><span class="sxs-lookup"><span data-stu-id="76941-104">When a pattern restriction is put on a type for which there is more than one possible lexical representation, some values could cause unexpected behavior upon validation.</span></span>  
  
 <span data-ttu-id="76941-105">因为这些值的词法表示形式未存储在数据库中，所以出现此行为。</span><span class="sxs-lookup"><span data-stu-id="76941-105">This behavior occurs because lexical representations of these values are not stored in the database.</span></span> <span data-ttu-id="76941-106">因此，当这些值作为输出序列化时将其转换为它们的规范表示形式。</span><span class="sxs-lookup"><span data-stu-id="76941-106">Therefore, the values are converted to their canonical representations when serialized as output.</span></span> <span data-ttu-id="76941-107">如果文档包含的值的规范格式不符合其类型的模式限制，则当用户尝试重新插入该文档时，将拒绝该文档。</span><span class="sxs-lookup"><span data-stu-id="76941-107">If a document contains a value whose canonical form does not comply with the pattern restriction for its type, the document is rejected if a user tries to reinsert it.</span></span>  
  
 <span data-ttu-id="76941-108">为了避免这种情况， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 拒绝任何包含无法重新插入的值的 XML 文档，由于它们的规范格式违反了模式限制。</span><span class="sxs-lookup"><span data-stu-id="76941-108">To prevent this, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rejects any XML document that contains values that cannot be reinserted, because of the violation of pattern restrictions by their canonical forms.</span></span> <span data-ttu-id="76941-109">例如，值“33.000”不对从 **xs:decimal** 派生的带有“33\\.0+”的模式限制的类型进行验证。</span><span class="sxs-lookup"><span data-stu-id="76941-109">For example, the value "33.000" does not validate against a type derived from **xs:decimal** with a pattern restriction of "33\\.0+".</span></span> <span data-ttu-id="76941-110">尽管“33.000”符合此模式，但规范格式“33”不符合。</span><span class="sxs-lookup"><span data-stu-id="76941-110">Although "33.000" complies with this pattern, the canonical form, "33", does not.</span></span>  
  
 <span data-ttu-id="76941-111">因此，将模式方面应用到从以下基元类型派生的类型时应当小心：`boolean`、`decimal`、`float`、`double`、`dateTime`、`time`、`date`、`hexBinary` 和 `base64Binary`。</span><span class="sxs-lookup"><span data-stu-id="76941-111">Therefore, you should be careful when you apply pattern facets to types derived from the following primitive types: `boolean`, `decimal`, `float`, `double`, `dateTime`, `time`, `date`, `hexBinary`, and `base64Binary`.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="76941-112">将发出警告。</span><span class="sxs-lookup"><span data-stu-id="76941-112">issues a warning when you add any such components to a schema collection.</span></span>  
  
 <span data-ttu-id="76941-113">浮点值的不精确序列化有类似的问题。</span><span class="sxs-lookup"><span data-stu-id="76941-113">Imprecise serialization of floating-point values has a similar problem.</span></span> <span data-ttu-id="76941-114">由于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用的浮点序列化算法，相似值可能共享相同的规范格式。</span><span class="sxs-lookup"><span data-stu-id="76941-114">Because of the floating-point serialization algorithm used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], it is possible for similar values to share the same canonical form.</span></span> <span data-ttu-id="76941-115">当序列化浮点值然后重新插入浮点值时，它的值可能发生轻微变化。</span><span class="sxs-lookup"><span data-stu-id="76941-115">When a floating-point value is serialized and then reinserted, its value may change slightly.</span></span> <span data-ttu-id="76941-116">在极个别的情况下，重新插入时这可能导致一个违反其类型的以下任何方面的值： **enumeration**、 **minInclusive**、 **minExclusive**、 **maxInclusive**或 **maxExclusive**。</span><span class="sxs-lookup"><span data-stu-id="76941-116">In rare cases, this may result in a value that violates any of the following facets for its type on reinsertion: **enumeration**, **minInclusive**, **minExclusive**, **maxInclusive**, or **maxExclusive**.</span></span> <span data-ttu-id="76941-117">为了避免这种情况， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 拒绝任何从 `xs:float` 或 `xs:double` 派生的类型的值，这些值无法序列化和重新插入。</span><span class="sxs-lookup"><span data-stu-id="76941-117">To prevent this, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rejects any values of types derived from `xs:float` or `xs:double` that cannot be serialized and reinserted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76941-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="76941-118">See Also</span></span>  
 [<span data-ttu-id="76941-119">在服务器上使用 XML 架构集合的要求和限制</span><span class="sxs-lookup"><span data-stu-id="76941-119">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
