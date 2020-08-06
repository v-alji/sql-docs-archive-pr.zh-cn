---
title: 唯一粒子归属约束 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
f1_keywords:
- unique particle attribution
helpviewer_keywords:
- schema collections [SQL Server], unique particle attribution
- XML schema collections [SQL Server], unique particle attribution
- UPA constraint rule
- unique particle attribution constraint rule
ms.assetid: 6bb879e9-a5ee-402e-94e4-fe8cec5966b0
author: rothja
ms.author: jroth
ms.openlocfilehash: 7416aa4ea14539f3bf633207768783aa439ec818
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682759"
---
# <a name="unique-particle-attribution-constraint"></a><span data-ttu-id="67b55-102">唯一粒子归属约束</span><span class="sxs-lookup"><span data-stu-id="67b55-102">Unique Particle Attribution Constraint</span></span>
  <span data-ttu-id="67b55-103">在 XSD 中，复杂内容模型受唯一粒子归属 (UPA) 约束规则的约束。</span><span class="sxs-lookup"><span data-stu-id="67b55-103">In XSD, complex content models are constrained by the unique particle attribution (UPA) constraint rule.</span></span> <span data-ttu-id="67b55-104">此规则要求实例文档中的每个元素明确地完全对应于其父级的内容模型中的一个 `<xsd:element>` 或 `<xsd:any>` 粒子。</span><span class="sxs-lookup"><span data-stu-id="67b55-104">This rule requires that each element in an instance document correspond unambiguously to exactly one `<xsd:element>` or `<xsd:any>` particle in its parent's content model.</span></span> <span data-ttu-id="67b55-105">任何包含具有可能不明确的内容模型的类型的架构都将被拒绝。</span><span class="sxs-lookup"><span data-stu-id="67b55-105">Any schema that contains a type with a potentially ambiguous content model is rejected.</span></span>  
  
 <span data-ttu-id="67b55-106">导致不明确的最常见原因是具有可变出现范围（例如 minOccurs < maxOccurs）的 `<xsd:any>` 通配符字符和粒子。</span><span class="sxs-lookup"><span data-stu-id="67b55-106">The most common causes of ambiguity are `<xsd:any>` wildcard characters and particles that have variable occurrence ranges, such as minOccurs < maxOccurs.</span></span> <span data-ttu-id="67b55-107">例如，以下内容模型是不明确的，因为 <`e1`> 元素既可以与 `<xsd:element>` 元素匹配，也可以与 `<xsd:any>` 元素匹配。</span><span class="sxs-lookup"><span data-stu-id="67b55-107">For example, the following content model is ambiguous, because an <`e1`> element could match either the `<xsd:element>` or the `<xsd:any>` element.</span></span>  
  
```  
<xsd:element name="root">  
    <xsd:complexType>  
        <xsd:choice>  
            <xsd:element name="e1"/>  
            <xsd:any namespace="##any"/>  
        </xsd:choice>  
    </xsd:complexType>  
</xsd:element>  
```  
  
 <span data-ttu-id="67b55-108">以下内容模型也是不明确的：</span><span class="sxs-lookup"><span data-stu-id="67b55-108">The following content model is also ambiguous:</span></span>  
  
```  
<xsd:element name="root">  
    <xsd:complexType>  
        <xsd:sequence>  
            <xsd:element name="e1" maxOccurs="2"/>  
            <xsd:element name="e2" minOccurs="0"/>  
            <xsd:element name="e1"/>  
        </xsd:sequence>  
    </xsd:complexType>  
</xsd:element>  
```  
  
 <span data-ttu-id="67b55-109">虽然可以明确验证像 `<root><e1/><e2/><e1/></root>` 这样的文档，但无法明确验证像 `<root><e1/><e1/></root>` 这样的文档，因为不清楚第二个 `<xsd:element>` 对应于哪一个 `<e1/>` 。</span><span class="sxs-lookup"><span data-stu-id="67b55-109">Although a document such as `<root><e1/><e2/><e1/></root>` can be validated unambiguously, a document such as `<root><e1/><e1/></root>` cannot, because it is not clear to which `<xsd:element>` the second `<e1/>` corresponds.</span></span> <span data-ttu-id="67b55-110">即使可以明确验证某些文档，此架构也将被拒绝，因为这些文档有可能是不明确的。</span><span class="sxs-lookup"><span data-stu-id="67b55-110">Even though some documents can be validated unambiguously, the schema will be rejected, because of the potential for ambiguity.</span></span>  
  
 <span data-ttu-id="67b55-111">请注意，对于有效的内容模型，必须能够在不向下查看的情况下明确验证任何实例。</span><span class="sxs-lookup"><span data-stu-id="67b55-111">Note that for a content model to be valid, it must be possible to validate any instance unambiguously without looking ahead.</span></span> <span data-ttu-id="67b55-112">例如，请思考下面的内容模型：</span><span class="sxs-lookup"><span data-stu-id="67b55-112">For example, consider the following content model:</span></span>  
  
```  
<xsd:element name="root">  
    <xsd:complexType>  
        <xsd:choice>  
           <xsd:sequence>  
               <xsd:element name="e1"/>  
               <xsd:element name="e2"/>  
           </xsd:sequence>  
           <xsd:sequence>  
               <xsd:element name="e1"/>  
               <xsd:element name="e3"/>  
           </xsd:sequence>  
       </xsd:choice>  
    </xsd:complexType>  
</xsd:element>  
```  
  
 <span data-ttu-id="67b55-113">对于像 `<root><e1/><e3/></root>`这样的文档，序列 `<e1/><e3/>` 明确与第二个 `<xsd:sequence>`匹配。</span><span class="sxs-lookup"><span data-stu-id="67b55-113">For a document such as `<root><e1/><e3/></root>`, the sequence `<e1/><e3/>` unambiguously matches the second `<xsd:sequence>`.</span></span> <span data-ttu-id="67b55-114">但是，由于在不向下查看 `<xsd:element>` 情况下无法确定 `<e1/>` 所对应的 `<e3/>`，因此该内容模型违反了 UPA 约束规则。</span><span class="sxs-lookup"><span data-stu-id="67b55-114">However, because the `<xsd:element>` to which `<e1/>` corresponds cannot be determined without looking ahead to `<e3/>`, the content model violates the UPA constraint rule.</span></span>  
  
## <a name="finding-more-information"></a><span data-ttu-id="67b55-115">查找详细信息</span><span class="sxs-lookup"><span data-stu-id="67b55-115">Finding More Information</span></span>  
 <span data-ttu-id="67b55-116">以下文档由 World Wide Web 联合会 (W3C) 发布，其中包含唯一粒子归属约束的技术说明：</span><span class="sxs-lookup"><span data-stu-id="67b55-116">The following document is published by the World Wide Web Consortium (W3C) and contains the technical description of the unique particle attribution constraint:</span></span>  
  
 <span data-ttu-id="67b55-117">“XML 架构第 1 部分：结构第二版 - W3C 已修正的提议推荐”：</span><span class="sxs-lookup"><span data-stu-id="67b55-117">"XML Schema Part 1: Structures Second Edition, W3C Proposed Edited Recommendation":</span></span>  
  
-   <span data-ttu-id="67b55-118">第 3.8.6 节：模型组架构组件的相关约束</span><span class="sxs-lookup"><span data-stu-id="67b55-118">Section 3.8.6: Constraints on Model Group Schema Components</span></span>  
  
-   <span data-ttu-id="67b55-119">附录 H：唯一粒子归属约束（非标准）的分析</span><span class="sxs-lookup"><span data-stu-id="67b55-119">Appendix H: Analysis of the Unique Particle Attribution Constraint (non-normative)</span></span>  
  
 <span data-ttu-id="67b55-120">若要查看该文档，请访问 [http://www.w3.org/TR/xmlschema-1](https://go.microsoft.com/fwlink/?linkid=48881)。</span><span class="sxs-lookup"><span data-stu-id="67b55-120">To see the document, visit [http://www.w3.org/TR/xmlschema-1](https://go.microsoft.com/fwlink/?linkid=48881).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67b55-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="67b55-121">See Also</span></span>  
 [<span data-ttu-id="67b55-122">XML 架构集合 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="67b55-122">XML Schema Collections &#40;SQL Server&#41;</span></span>](xml-schema-collections-sql-server.md)  
  
  
