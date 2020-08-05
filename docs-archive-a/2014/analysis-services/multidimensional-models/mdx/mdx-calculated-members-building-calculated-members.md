---
title: 在 MDX 中生成计算成员 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], calculated members
- calculated members [MDX]
- Multidimensional Expressions [Analysis Services], calculated members
- queries [MDX], calculated members
ms.assetid: 9322e8b8-43e1-4e02-a7d1-e41a586a5bb8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 30dc6562ec394065cf2f177608d4e5679cbd7df3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580928"
---
# <a name="building-calculated-members-in-mdx-mdx"></a><span data-ttu-id="a66df-102">在 MDX 中生成计算成员 (MDX)</span><span class="sxs-lookup"><span data-stu-id="a66df-102">Building Calculated Members in MDX (MDX)</span></span>
  <span data-ttu-id="a66df-103">在多维表达式 (MDX) 中，计算成员是通过以下方式解析的成员：计算 MDX 表达式以返回值。</span><span class="sxs-lookup"><span data-stu-id="a66df-103">In Multidimensional Expressions (MDX), a calculated member is a member that is resolved by calculating an MDX expression to return a value.</span></span> <span data-ttu-id="a66df-104">这种泛泛的定义所包括的范围十分惊人。</span><span class="sxs-lookup"><span data-stu-id="a66df-104">This innocuous definition covers an incredible amount of ground.</span></span> <span data-ttu-id="a66df-105">由于能在 MDX 查询中构造和使用计算成员，使得人们能够更有力地驾驭多维数据。</span><span class="sxs-lookup"><span data-stu-id="a66df-105">The ability to construct and use calculated members in an MDX query provides a great deal of manipulation capability for multidimensional data.</span></span>  
  
 <span data-ttu-id="a66df-106">可以在层次结构中的任意位置创建计算成员。</span><span class="sxs-lookup"><span data-stu-id="a66df-106">You can create calculated members at any point within a hierarchy.</span></span> <span data-ttu-id="a66df-107">也可以创建不仅依赖于多维数据集中的现有成员、而且依赖于同一 MDX 表达式中定义的其他计算成员的计算成员。</span><span class="sxs-lookup"><span data-stu-id="a66df-107">You can also create calculated members that depend not only on existing members in a cube, but also on other calculated members defined in the same MDX expression.</span></span>  
  
 <span data-ttu-id="a66df-108">可以指定让计算成员使用下列上下文之一：</span><span class="sxs-lookup"><span data-stu-id="a66df-108">You can define a calculated member to have one of the following contexts:</span></span>  
  
-   <span data-ttu-id="a66df-109">**查询作用域** ：若要创建一个计算成员，该计算成员被定义为 MDX 查询的一部分并且其作用域因此被限制在该查询内，请使用 WITH 关键字。</span><span class="sxs-lookup"><span data-stu-id="a66df-109">**Query-scoped** To create a calculated member that is defined as part of an MDX query, and therefore whose scope is limited to the query, you use the WITH keyword.</span></span> <span data-ttu-id="a66df-110">然后，就可以在 MDX SELECT 语句中使用该计算成员。</span><span class="sxs-lookup"><span data-stu-id="a66df-110">You can then use the calculated member within an MDX SELECT statement.</span></span> <span data-ttu-id="a66df-111">通过这种方法，更改用 WITH 关键字创建的计算成员时就不会打乱 SELECT 语句。</span><span class="sxs-lookup"><span data-stu-id="a66df-111">Using this approach, the calculated member created by using the WITH keyword can be changed without disturbing the SELECT statement.</span></span>  
  
     <span data-ttu-id="a66df-112">有关如何使用 WITH 关键字创建计算成员的详细信息，请参阅[创建查询作用域的计算成员 (MDX)](mdx-calculated-members-query-scoped-calculated-members.md)。</span><span class="sxs-lookup"><span data-stu-id="a66df-112">For more information about how to use the WITH keyword to create calculated members, see [Creating Query-Scoped Calculated Members &#40;MDX&#41;](mdx-calculated-members-query-scoped-calculated-members.md).</span></span>  
  
-   <span data-ttu-id="a66df-113">**会话作用域** ：若要创建一个计算成员，使其作用域比查询上下文更广（即，其作用域为 MDX 会话的生存期），请使用 CREATE MEMBER 语句。</span><span class="sxs-lookup"><span data-stu-id="a66df-113">**Session-scoped** To create a calculated member whose scope is wider than the context of the query, that is, whose scope is the lifetime of the MDX session, you use the CREATE MEMBER statement.</span></span> <span data-ttu-id="a66df-114">使用 CREATE MEMBER 语句定义的计算成员可供该会话中的所有 MDX 查询使用。</span><span class="sxs-lookup"><span data-stu-id="a66df-114">A calculated member defined by using the CREATE MEMBER statement is available to all MDX queries in that session.</span></span> <span data-ttu-id="a66df-115">例如，CREATE MEMBER 语句对于需要在多种查询中大量重用同一个集的客户端应用程序会非常有用。</span><span class="sxs-lookup"><span data-stu-id="a66df-115">The CREATE MEMBER statement makes sense, for example, in a client application that consistently reuses the same set in a variety of queries.</span></span>  
  
     <span data-ttu-id="a66df-116">有关如何使用 CREATE MEMBER 语句在会话中创建计算成员的详细信息，请参阅[创建会话作用域的计算成员 (MDX)](mdx-calculated-members-session-scoped-calculated-members.md)。</span><span class="sxs-lookup"><span data-stu-id="a66df-116">For more information about how to use the CREATE MEMBER statement to create calculated members in a session, see [Creating Session-Scoped Calculated Members &#40;MDX&#41;](mdx-calculated-members-session-scoped-calculated-members.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a66df-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a66df-117">See Also</span></span>  
 <span data-ttu-id="a66df-118">[CREATE MEMBER 语句 &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) </span><span class="sxs-lookup"><span data-stu-id="a66df-118">[CREATE MEMBER Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) </span></span>  
 <span data-ttu-id="a66df-119">[Mdx 函数引用 &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="a66df-119">[MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span></span>  
 [<span data-ttu-id="a66df-120">SELECT 语句 (MDX)</span><span class="sxs-lookup"><span data-stu-id="a66df-120">SELECT Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-manipulation-select)  
  
  
