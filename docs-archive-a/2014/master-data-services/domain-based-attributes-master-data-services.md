---
title: 基于域的属性 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- domain-based attributes [Master Data Services], about domain-based attributes
- domain-based attributes [Master Data Services]
- attributes [Master Data Services], domain-based attributes
ms.assetid: df6f33ff-97f6-466c-af74-9780b2247473
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9182974923848d49ed3e9ecfb58a14949784a2c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591914"
---
# <a name="domain-based-attributes-master-data-services"></a><span data-ttu-id="cdd0a-102">基于域的属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cdd0a-102">Domain-Based Attributes (Master Data Services)</span></span>
  <span data-ttu-id="cdd0a-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，基于域的属性是具有另一个实体成员填充的值的属性。</span><span class="sxs-lookup"><span data-stu-id="cdd0a-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a domain-based attribute is an attribute with values that are populated by members from another entity.</span></span> <span data-ttu-id="cdd0a-104">可以将基于域的属性视为受限制列表，基于域的属性防止用户输入无效的属性值。</span><span class="sxs-lookup"><span data-stu-id="cdd0a-104">You can think of a domain-based attribute as a constrained list; domain-based attributes prevent users from entering attribute values that are not valid.</span></span> <span data-ttu-id="cdd0a-105">若要选择某一属性值，用户必须从列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="cdd0a-105">To select an attribute value, the user must pick from a list.</span></span>

## <a name="domain-based-attribute-example"></a><span data-ttu-id="cdd0a-106">基于域的属性示例</span><span class="sxs-lookup"><span data-stu-id="cdd0a-106">Domain-Based Attribute Example</span></span>
 <span data-ttu-id="cdd0a-107">在下图中，Product 实体具有名为 Subcategory 的基于域的属性。</span><span class="sxs-lookup"><span data-stu-id="cdd0a-107">In the following image, the Product entity has a domain-based attribute called Subcategory.</span></span> <span data-ttu-id="cdd0a-108">该 Subcategory 属性用来自 Subcategory 实体的值填充。</span><span class="sxs-lookup"><span data-stu-id="cdd0a-108">The Subcategory attribute is populated by values from the Subcategory entity.</span></span>

 <span data-ttu-id="cdd0a-109">Subcategory 实体具有名为 Category 的基于域的属性。</span><span class="sxs-lookup"><span data-stu-id="cdd0a-109">The Subcategory entity has a domain-based attribute called Category.</span></span> <span data-ttu-id="cdd0a-110">该 Category 属性用来自 Category 实体的值填充。</span><span class="sxs-lookup"><span data-stu-id="cdd0a-110">The Category attribute is populated by values from the Category entity.</span></span>

 <span data-ttu-id="cdd0a-111">![实体中基于域的属性](../../2014/master-data-services/media/mds-conc-domain-based-attribute-conceptual.gif "实体中基于域的属性")</span><span class="sxs-lookup"><span data-stu-id="cdd0a-111">![Domain-Based Attributes in an Entity](../../2014/master-data-services/media/mds-conc-domain-based-attribute-conceptual.gif "Domain-Based Attributes in an Entity")</span></span>

## <a name="use-same-entity-for-multiple-domain-based-attributes"></a><span data-ttu-id="cdd0a-112">将同一实体用于多个基于域的属性</span><span class="sxs-lookup"><span data-stu-id="cdd0a-112">Use Same Entity for Multiple Domain-Based Attributes</span></span>
 <span data-ttu-id="cdd0a-113">您可以将同一实体用作多个实体的基于域的属性。</span><span class="sxs-lookup"><span data-stu-id="cdd0a-113">You can use the same entity as a domain-based attribute of multiple entities.</span></span> <span data-ttu-id="cdd0a-114">例如，您可以创建名为 YesNoIndicator 的一个实体，该实体具有成员 Yes、No 和 Maybe。</span><span class="sxs-lookup"><span data-stu-id="cdd0a-114">For example, you can create an entity called YesNoIndicator with the members: Yes, No, and Maybe.</span></span> <span data-ttu-id="cdd0a-115">您可以创建名为 InStock 的基于域的属性并且使用 YesNoIndicator 实体作为源。</span><span class="sxs-lookup"><span data-stu-id="cdd0a-115">You can create a domain-based attribute named InStock and use the YesNoIndicator entity as the source.</span></span> <span data-ttu-id="cdd0a-116">还可以创建名为 Approved 的另一个基于域的属性并且使用 YesNoIndicator 实体作为源。</span><span class="sxs-lookup"><span data-stu-id="cdd0a-116">You can also create another domain-based attribute named Approved and use the YesNoIndicator entity as a source.</span></span> <span data-ttu-id="cdd0a-117">只要您希望用户从 YesNoIndicator 实体的成员列表中进行选择，就可以将该实体用作基于域的属性。</span><span class="sxs-lookup"><span data-stu-id="cdd0a-117">Any time you want users to choose from a list of the YesNoIndicator entity's members, you can use the entity as a domain-based attribute.</span></span>

## <a name="domain-based-attributes-form-derived-hierarchies"></a><span data-ttu-id="cdd0a-118">基于域的属性构成派生层次结构</span><span class="sxs-lookup"><span data-stu-id="cdd0a-118">Domain-Based Attributes Form Derived Hierarchies</span></span>
 <span data-ttu-id="cdd0a-119">基于域的属性关系是用于派生层次结构的基础。</span><span class="sxs-lookup"><span data-stu-id="cdd0a-119">Domain-based attribute relationships are the basis for derived hierarchies.</span></span> <span data-ttu-id="cdd0a-120">有关详细信息，请参阅 [派生层次结构 (Master Data Services)](derived-hierarchies-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="cdd0a-120">For more information, see [Derived Hierarchies &#40;Master Data Services&#41;](derived-hierarchies-master-data-services.md).</span></span>

## <a name="related-tasks"></a><span data-ttu-id="cdd0a-121">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="cdd0a-121">Related Tasks</span></span>

|<span data-ttu-id="cdd0a-122">任务说明</span><span class="sxs-lookup"><span data-stu-id="cdd0a-122">Task Description</span></span>|<span data-ttu-id="cdd0a-123">主题</span><span class="sxs-lookup"><span data-stu-id="cdd0a-123">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="cdd0a-124">创建来自现有实体的基于域的新属性。</span><span class="sxs-lookup"><span data-stu-id="cdd0a-124">Create a new domain-based attribute that is sourced from an existing entity.</span></span>|[<span data-ttu-id="cdd0a-125">创建基于域的属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cdd0a-125">Create a Domain-Based Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)|
|<span data-ttu-id="cdd0a-126">创建新实体。</span><span class="sxs-lookup"><span data-stu-id="cdd0a-126">Create a new entity.</span></span>|[<span data-ttu-id="cdd0a-127">创建实体 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cdd0a-127">Create an Entity &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-entity-master-data-services.md)|

## <a name="related-content"></a><span data-ttu-id="cdd0a-128">相关内容</span><span class="sxs-lookup"><span data-stu-id="cdd0a-128">Related Content</span></span>

-   [<span data-ttu-id="cdd0a-129">派生层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cdd0a-129">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](derived-hierarchies-master-data-services.md)

-   [<span data-ttu-id="cdd0a-130">属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cdd0a-130">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)

-   [<span data-ttu-id="cdd0a-131">实体 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cdd0a-131">Entities &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/entities-master-data-services.md)


