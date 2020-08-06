---
title: 在 MDX (MDX) 中生成命名集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], named sets
- named sets [MDX]
- sets [MDX]
- MDX [Analysis Services], named sets
- queries [MDX], named sets
- set expressions [MDX]
ms.assetid: 213b0035-e96d-4ba0-83f2-ded206905603
author: minewiskan
ms.author: owend
ms.openlocfilehash: 91296f8c5d47afb15c67f0b60435c7f961734573
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689060"
---
# <a name="building-named-sets-in-mdx-mdx"></a><span data-ttu-id="2c5d4-102">在 MDX 中生成命名集 (MDX)</span><span class="sxs-lookup"><span data-stu-id="2c5d4-102">Building Named Sets in MDX (MDX)</span></span>
  <span data-ttu-id="2c5d4-103">集表达式可能是较长且非常复杂的声明，因此很难理解。</span><span class="sxs-lookup"><span data-stu-id="2c5d4-103">A set expression can be a lengthy and complex declaration, and therefore be difficult to follow or understand.</span></span> <span data-ttu-id="2c5d4-104">或者，可能非常频繁地使用集表达式，以致于重复定义集成为一种负担。</span><span class="sxs-lookup"><span data-stu-id="2c5d4-104">Or, a set expression may be used so frequently that repeatedly defining the set becomes burdensome.</span></span> <span data-ttu-id="2c5d4-105">为了使长而复杂的表达式或常用的表达式更易于使用，多维表达式 (MDX) 允许使用“命名集”表达式\*\*。</span><span class="sxs-lookup"><span data-stu-id="2c5d4-105">To help make working with a lengthy, complex or commonly used expression easier, Multidimensional Expressions (MDX) lets you such an expression as a *named set*.</span></span>  
  
 <span data-ttu-id="2c5d4-106">从根本上说，命名集就是指定了别名的集表达式。</span><span class="sxs-lookup"><span data-stu-id="2c5d4-106">Basically, a named set is a set expression to which an alias has been assigned.</span></span> <span data-ttu-id="2c5d4-107">命名集可包含能正常合并到集中的任何成员或函数。</span><span class="sxs-lookup"><span data-stu-id="2c5d4-107">A named set can incorporate any members or functions that can ordinarily be incorporated into a set.</span></span> <span data-ttu-id="2c5d4-108">由于 MDX 将命名集别名视为集表达式，因此您可以在任何能使用集表达式的位置使用命名集别名。</span><span class="sxs-lookup"><span data-stu-id="2c5d4-108">Because MDX treats the named set alias as a set expression, you can use that alias anywhere a set expression is accepted.</span></span>  
  
 <span data-ttu-id="2c5d4-109">可以将命名集定义为具有下列上下文之一：</span><span class="sxs-lookup"><span data-stu-id="2c5d4-109">You can define a named set to have one of the following contexts:</span></span>  
  
-   <span data-ttu-id="2c5d4-110">**查询作用域** ：若要创建一个命名集，该命名集被定义为 MDX 查询的一部分并且其作用域因此被限制在该查询内，请使用 WITH 关键字。</span><span class="sxs-lookup"><span data-stu-id="2c5d4-110">**Query-scoped** To create a named set that is defined as part of an MDX query, and therefore whose scope is limited to the query, you use the WITH keyword.</span></span> <span data-ttu-id="2c5d4-111">然后，就可以在 MDX SELECT 语句中使用该命名集。</span><span class="sxs-lookup"><span data-stu-id="2c5d4-111">You can then use the named set within an MDX SELECT statement.</span></span> <span data-ttu-id="2c5d4-112">通过这种方法，更改用 WITH 关键字创建的命名集时就不会打乱 SELECT 语句。</span><span class="sxs-lookup"><span data-stu-id="2c5d4-112">Using this approach, the named set created by using the WITH keyword can be changed without disturbing the SELECT statement.</span></span>  
  
     <span data-ttu-id="2c5d4-113">有关如何使用 WITH 关键字创建命名集的详细信息，请参阅[创建查询作用域的命名集 (MDX)](mdx-named-sets-creating-query-scoped-named-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="2c5d4-113">For more information about how to use the WITH keyword to create named sets, see [Creating Query-Scoped Named Sets &#40;MDX&#41;](mdx-named-sets-creating-query-scoped-named-sets.md).</span></span>  
  
-   <span data-ttu-id="2c5d4-114">**会话作用域** ：若要创建一个命名集，使其作用域比查询上下文更广（即，其作用域为 MDX 会话的生存期），请使用 CREATE SET 语句。</span><span class="sxs-lookup"><span data-stu-id="2c5d4-114">**Session-scoped** To create a named set whose scope is wider than the context of the query, that is, whose scope is the lifetime of the MDX session, you use the CREATE SET statement.</span></span> <span data-ttu-id="2c5d4-115">使用 CREATE SET 语句定义的命名集对该会话中的所有 MDX 查询均可用。</span><span class="sxs-lookup"><span data-stu-id="2c5d4-115">A named set defined by using the CREATE SET statement is available to all MDX queries in that session.</span></span> <span data-ttu-id="2c5d4-116">例如，CREATE SET 语句对于需要在多种查询中大量重用某个集的客户端应用程序会非常有用。</span><span class="sxs-lookup"><span data-stu-id="2c5d4-116">The CREATE SET statement makes sense, for example, in a client application that consistently reuses a set in a variety of queries.</span></span>  
  
     <span data-ttu-id="2c5d4-117">有关如何使用 CREATE SET 语句在会话中创建命名集的详细信息，请参阅[创建会话作用域的命名集 (MDX)](mdx-named-sets-creating-session-scoped-named-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="2c5d4-117">For more information about how to use the CREATE SET statement to create named sets in a session, see [Creating Session-Scoped Named Sets &#40;MDX&#41;](mdx-named-sets-creating-session-scoped-named-sets.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c5d4-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2c5d4-118">See Also</span></span>  
 <span data-ttu-id="2c5d4-119">[SELECT 语句 &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select) </span><span class="sxs-lookup"><span data-stu-id="2c5d4-119">[SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select) </span></span>  
 <span data-ttu-id="2c5d4-120">[CREATE SET 语句 &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-set) </span><span class="sxs-lookup"><span data-stu-id="2c5d4-120">[CREATE SET Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-set) </span></span>  
 [<span data-ttu-id="2c5d4-121">MDX 查询基础知识 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="2c5d4-121">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
