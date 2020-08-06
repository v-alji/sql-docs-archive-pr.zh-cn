---
title: " (MDX) 使用成员属性 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DIMENSION PROPERTIES keyword
- Properties function
- member properties [MDX]
- members [MDX], properties
ms.assetid: 26b5ad08-3799-4a5e-89f3-dca25e637d45
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5b7fdf989fc23ea70be7d7863f5d4c6ac0b61d8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689051"
---
# <a name="using-member-properties-mdx"></a><span data-ttu-id="3ce2d-102">使用成员属性 (MDX)</span><span class="sxs-lookup"><span data-stu-id="3ce2d-102">Using Member Properties (MDX)</span></span>
  <span data-ttu-id="3ce2d-103">成员属性提供有关各个元组中的每个成员的基本信息。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-103">Member properties cover the basic information about each member in each tuple.</span></span> <span data-ttu-id="3ce2d-104">此基本信息包括成员名、父级别、子成员数目等等。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-104">This basic information includes the member name, parent level, the number of children, and so on.</span></span> <span data-ttu-id="3ce2d-105">成员属性适用于给定级别的所有成员。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-105">Member properties are available for all members at a given level.</span></span> <span data-ttu-id="3ce2d-106">就组织结构而言，成员属性可视为存储在单个维度上按维度组织的数据。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-106">In terms of organization, member properties are treated as dimensionally organized data, stored on a single dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ce2d-107">在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中，成员属性被称为“属性关系”。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-107">In [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], member properties are know as attribute relationships.</span></span> <span data-ttu-id="3ce2d-108">有关详细信息，请参阅 [属性关系](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-108">For more information, see [Attribute Relationships](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).</span></span>  
  
 <span data-ttu-id="3ce2d-109">成员属性可以是“内部” \*\* 的，也可以是“自定义” \*\* 的：</span><span class="sxs-lookup"><span data-stu-id="3ce2d-109">Member properties are either *intrinsic* or *custom*:</span></span>  
  
 <span data-ttu-id="3ce2d-110">内部成员属性</span><span class="sxs-lookup"><span data-stu-id="3ce2d-110">Intrinsic member properties</span></span>  
 <span data-ttu-id="3ce2d-111">所有成员都支持内部成员属性，如成员的格式化值；而维度和级别提供附加的内部维度和级别成员属性，如成员的 ID。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-111">All members support intrinsic member properties, such as the formatted value of a member, while dimensions and levels supply additional intrinsic dimension and level member properties, such as the ID of a member.</span></span>  
  
 <span data-ttu-id="3ce2d-112">有关详细信息，请参阅[内部成员属性 (MDX)](mdx-member-properties-intrinsic-member-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-112">For more information, see [Intrinsic Member Properties &#40;MDX&#41;](mdx-member-properties-intrinsic-member-properties.md).</span></span>  
  
 <span data-ttu-id="3ce2d-113">用户定义成员属性</span><span class="sxs-lookup"><span data-stu-id="3ce2d-113">User-defined member properties</span></span>  
 <span data-ttu-id="3ce2d-114">成员通常还与其他属性相关联。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-114">Members often have additional properties associated with them.</span></span> <span data-ttu-id="3ce2d-115">例如，Products 级别可为每件产品提供 SKU、SRP、Weight 和 Volume 属性。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-115">For example, the Products level may offer the SKU, SRP, Weight, and Volume properties for each product.</span></span> <span data-ttu-id="3ce2d-116">这些属性不是成员，但包含有关 Products 级别的成员的附加信息。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-116">These properties are not members, but contain additional information about members at the Products level.</span></span>  
  
 <span data-ttu-id="3ce2d-117">有关详细信息，请参阅[用户定义的成员属性 (MDX)](mdx-member-properties-user-defined-member-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-117">For more information, see [User-Defined Member Properties &#40;MDX&#41;](mdx-member-properties-user-defined-member-properties.md).</span></span>  
  
 <span data-ttu-id="3ce2d-118">内部成员属性和用户定义成员属性都可以通过使用 `PROPERTIES` 关键字或[properties](/sql/mdx/properties-mdx)函数进行检索。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-118">Both intrinsic and user-defined member properties can be retrieved through the use of the `PROPERTIES` keyword or the [Properties](/sql/mdx/properties-mdx) function.</span></span>  
  
## <a name="using-the-properties-keyword"></a><span data-ttu-id="3ce2d-119">使用 PROPERTIES 关键字</span><span class="sxs-lookup"><span data-stu-id="3ce2d-119">Using the PROPERTIES Keyword</span></span>  
 <span data-ttu-id="3ce2d-120">`PROPERTIES` 关键字指定要用于给定轴维度的成员属性。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-120">The `PROPERTIES` keyword specifies the member properties that are to be used for a given axis dimension.</span></span> <span data-ttu-id="3ce2d-121">`PROPERTIES`关键字隐藏在 `<axis specification>` MDX [SELECT](/sql/mdx/mdx-data-manipulation-select)语句的子句中：</span><span class="sxs-lookup"><span data-stu-id="3ce2d-121">The `PROPERTIES` keyword is buried within the `<axis specification>` clause of the MDX [SELECT](/sql/mdx/mdx-data-manipulation-select) statement:</span></span>  
  
```  
SELECT [<axis_specification>  
       [, <axis_specification>...]]  
  FROM [<cube_specification>]  
[WHERE [<slicer_specification>]]  
```  
  
 <span data-ttu-id="3ce2d-122">`<axis_specification>` 子句包含可选的 `<dim_props>` 子句，如下列语法所示：</span><span class="sxs-lookup"><span data-stu-id="3ce2d-122">The `<axis_specification>` clause includes an optional `<dim_props>` clause, as shown in the following syntax:</span></span>  
  
```  
<axis_specification> ::= <set> [<dim_props>] ON <axis_name>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="3ce2d-123">有关 `<set>` 和 `<axis_name>` 值的详细信息，请参阅[指定查询轴的内容 (MDX)](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-123">For more information about the `<set>` and `<axis_name>` values, see [Specifying the Contents of a Query Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).</span></span>  
  
 <span data-ttu-id="3ce2d-124">`<dim_props>` 子句允许您使用 `PROPERTIES` 关键字查询维度、级别和成员属性。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-124">The `<dim_props>` clause lets you query dimension, level, and member properties using the `PROPERTIES` keyword.</span></span> <span data-ttu-id="3ce2d-125">下列语法显示了 `<dim_props>` 子句的格式：</span><span class="sxs-lookup"><span data-stu-id="3ce2d-125">The following syntax shows the formatting of the `<dim_props>` clause:</span></span>  
  
```  
<dim_props> ::= [DIMENSION] PROPERTIES <property> [,<property>...]  
```  
  
 <span data-ttu-id="3ce2d-126">`<property>` 语法的细分因要查询的属性而异：</span><span class="sxs-lookup"><span data-stu-id="3ce2d-126">The breakdown of the `<property>` syntax varies depending on the property that you are querying:</span></span>  
  
-   <span data-ttu-id="3ce2d-127">上下文相关的内部成员属性前必须是维度或级别的名称。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-127">Context sensitive intrinsic member properties must be preceded with the name of the dimension or level.</span></span> <span data-ttu-id="3ce2d-128">但是，非上下文相关的内部成员属性不能由维度或级别的名称限定。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-128">However, non-context sensitive intrinsic member properties cannot be qualified by the dimension or level name.</span></span> <span data-ttu-id="3ce2d-129">有关如何将 `PROPERTIES` 关键字与内部成员属性一起使用的详细信息，请参阅[&#40;MDX&#41;的内部成员属性](mdx-member-properties-intrinsic-member-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-129">For more information about how to use the `PROPERTIES` keyword with intrinsic member properties, see [Intrinsic Member Properties &#40;MDX&#41;](mdx-member-properties-intrinsic-member-properties.md).</span></span>  
  
-   <span data-ttu-id="3ce2d-130">用户定义成员属性前应是其所在级别的名称。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-130">User-defined member properties should be preceded by the name of the level in which they reside.</span></span> <span data-ttu-id="3ce2d-131">有关如何将 `PROPERTIES` 关键字与用户定义的成员属性一起使用的详细信息，请参阅[&#40;MDX&#41;的用户定义的成员属性](mdx-member-properties-user-defined-member-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-131">For more information about how to use the `PROPERTIES` keyword with user-defined member properties, see [User-Defined Member Properties &#40;MDX&#41;](mdx-member-properties-user-defined-member-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ce2d-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3ce2d-132">See Also</span></span>  
 [<span data-ttu-id="3ce2d-133">创建和使用属性值 (MDX)</span><span class="sxs-lookup"><span data-stu-id="3ce2d-133">Creating and Using Property Values &#40;MDX&#41;</span></span>](../../creating-and-using-property-values-mdx.md)  
  
  
