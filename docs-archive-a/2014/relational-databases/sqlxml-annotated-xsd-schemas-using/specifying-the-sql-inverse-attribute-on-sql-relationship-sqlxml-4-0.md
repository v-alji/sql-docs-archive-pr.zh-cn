---
title: 在 sql： relationship 上指定 sql：反向特性 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:relationship
- bulk load [SQLXML]
- inverse attribute
- relationships [SQLXML], inverse orders
- relationship annotation
- XSD schemas [SQLXML], relationships
- annotated XSD schemas, relationships
- updategrams [SQLXML], relationships
- sql:inverse
ms.assetid: 08904cbd-9c86-493d-90c3-f5e1d13ce59d
author: rothja
ms.author: jroth
ms.openlocfilehash: 5b0781102371b98cced72a5a0edee70c9567c372
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586598"
---
# <a name="specifying-the-sqlinverse-attribute-on-sqlrelationship-sqlxml-40"></a><span data-ttu-id="51708-102">在 sql:relationship 上指定 sql:inverse 属性 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="51708-102">Specifying the sql:inverse Attribute on sql:relationship (SQLXML 4.0)</span></span>
  <span data-ttu-id="51708-103">`sql:inverse` 属性只有在 XSD 架构用于大容量加载或用于 updategram 时才有用。</span><span class="sxs-lookup"><span data-stu-id="51708-103">The `sql:inverse` attribute is useful only when the XSD schema is used for either bulk load or by an updategram.</span></span> <span data-ttu-id="51708-104">`sql:inverse`可在元素上指定属性 **\<sql:relationship>** 。</span><span class="sxs-lookup"><span data-stu-id="51708-104">The `sql:inverse` attribute can be specified on the **\<sql:relationship>** element.</span></span> <span data-ttu-id="51708-105">在 updategram 中，updategram 逻辑在确定由 updategram 操作更新的表和列时会解释架构。</span><span class="sxs-lookup"><span data-stu-id="51708-105">In updategrams, the updategram logic interprets the schema in determining the tables and columns that are updated by the updategram operation.</span></span> <span data-ttu-id="51708-106">架构中所指定的父子关系决定了修改（插入或删除）记录的顺序。</span><span class="sxs-lookup"><span data-stu-id="51708-106">The parent-child relationships that are specified in the schema determine the order in which the records are modified (inserted or deleted).</span></span>  
  
 <span data-ttu-id="51708-107">如果在 XSD 架构中指定的父子关系与相应数据库列之间的主键/外键关系顺序相反，则插入或删除 updategram 操作将因主键/外键冲突而失败。</span><span class="sxs-lookup"><span data-stu-id="51708-107">If you have an XSD schema in which the parent-child relationship is specified in the inverse order of the primary-key/foreign-key relationship between the corresponding database columns, the insert or delete updategram operation will fail because of the primary-key/foreign-key violation.</span></span> <span data-ttu-id="51708-108">在这种情况下， `sql:inverse` 属性在 `sql:inverse="true"` 元素中指定 () **\<sql:relationship>** ，而 updategram 逻辑逆其对架构中指定的父子关系的解释。</span><span class="sxs-lookup"><span data-stu-id="51708-108">In such cases, the `sql:inverse` attribute is specified (`sql:inverse="true"`) in the **\<sql:relationship>** element, and the updategram logic inverses its interpretation of the parent-child relationship specified in the schema.</span></span>  
  
 <span data-ttu-id="51708-109">`sql:inverse` 属性采用布尔值（0 = FALSE，1 = TRUE）。</span><span class="sxs-lookup"><span data-stu-id="51708-109">The `sql:inverse` attribute takes a Boolean value (0=false, 1=true).</span></span> <span data-ttu-id="51708-110">可接受的值为 0、1、true 和 false。</span><span class="sxs-lookup"><span data-stu-id="51708-110">The acceptable values are 0, 1, true, and false.</span></span>  
  
 <span data-ttu-id="51708-111">有关使用批注的工作示例 `sql:inverse` ，请参阅[在 Updategram 中指定带批注的映射架构](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="51708-111">For a working sample using the `sql:inverse` annotation, see [Specifying an Annotated Mapping Schema in an Updategram](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51708-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="51708-112">See Also</span></span>  
 [<span data-ttu-id="51708-113">使用 sql： relationship 指定关系 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="51708-113">Specifying Relationships Using sql:relationship &#40;SQLXML 4.0&#41;</span></span>](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
  
  
