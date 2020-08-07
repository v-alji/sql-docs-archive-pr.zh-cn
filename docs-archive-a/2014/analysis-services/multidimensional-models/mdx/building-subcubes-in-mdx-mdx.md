---
title: 在 MDX (MDX) 中生成子多维数据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- queries [MDX], subcubes
- subcubes [MDX]
- filtered views [MDX]
- MDX [Analysis Services], subcubes
- Multidimensional Expressions [Analysis Services], subcubes
- CREATE SUBCUBE statement
ms.assetid: 5403a62b-99ac-4d83-b02a-89bf78bf0f46
author: minewiskan
ms.author: owend
ms.openlocfilehash: 653b4d30aa86f52179c7b13619ac4347aa65c339
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588114"
---
# <a name="building-subcubes-in-mdx-mdx"></a><span data-ttu-id="8aa1b-102">在 MDX 中生成子多维数据集 (MDX)</span><span class="sxs-lookup"><span data-stu-id="8aa1b-102">Building Subcubes in MDX (MDX)</span></span>
  <span data-ttu-id="8aa1b-103">子多维数据集是多维数据集的子集，用于表示基础数据的筛选视图。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-103">A subcube is a subset of a cube on representing a filtered view of the underlying data.</span></span> <span data-ttu-id="8aa1b-104">通过将多维数据集限制为一个子多维数据集，可以改善查询的性能。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-104">By limiting the cube to a subcube, you can improve query performance.</span></span>  
  
 <span data-ttu-id="8aa1b-105">若要定义子多维数据集，请按照本主题所述使用 [CREATE SUBCUBE](/sql/mdx/mdx-data-definition-create-subcube) 语句。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-105">To define a subcube, you use the [CREATE SUBCUBE](/sql/mdx/mdx-data-definition-create-subcube) statement, as described in this topic.</span></span>  
  
## <a name="create-subcube-syntax"></a><span data-ttu-id="8aa1b-106">CREATE SUBCUBE 语法</span><span class="sxs-lookup"><span data-stu-id="8aa1b-106">CREATE SUBCUBE Syntax</span></span>  
 <span data-ttu-id="8aa1b-107">使用下列语法创建子多维数据集：</span><span class="sxs-lookup"><span data-stu-id="8aa1b-107">Use the following syntax to create a subcube:</span></span>  
  
```  
CREATE SUBCUBE Subcube_Identifier AS Subcube_Expression  
```  
  
 <span data-ttu-id="8aa1b-108">CREATE SUBCUBE 语法非常简单。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-108">The CREATE SUBCUBE syntax is fairly simple.</span></span> <span data-ttu-id="8aa1b-109">*Subcube_Identifier* 参数标识子多维数据集所基于的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-109">The *Subcube_Identifier* parameter identifies the cube on which the subcube will be based.</span></span> <span data-ttu-id="8aa1b-110">*Subcube_Expression* 参数选择将成为子多维数据集的多维数据集中部分。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-110">The *Subcube_Expression* parameter selects the part of the cube that will become the subcube</span></span>  
  
 <span data-ttu-id="8aa1b-111">创建子多维数据集后，该子多维数据集将成为所有 MDX 查询的上下文，直到会话结束或运行 [DROP SUBCUBE](/sql/mdx/mdx-data-definition-drop-subcube) 语句。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-111">After you create a subcube, that subcube becomes the context for all MDX queries until either the session closes or you run the [DROP SUBCUBE](/sql/mdx/mdx-data-definition-drop-subcube) statement.</span></span>  
  
### <a name="what-a-subcube-contains"></a><span data-ttu-id="8aa1b-112">子多维数据集包含的内容</span><span class="sxs-lookup"><span data-stu-id="8aa1b-112">What a Subcube Contains</span></span>  
 <span data-ttu-id="8aa1b-113">尽管 CREATE SUBCUBE 语句使用起来非常简单，但是该语句本身并不明确显示构成子多维数据集的所有成员。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-113">Although the CREATE SUBCUBE statement is fairly simple to use, the statement itself does not explicitly show all the members that become part of a subcube.</span></span> <span data-ttu-id="8aa1b-114">在定义子多维数据集时，需遵循下列规则：</span><span class="sxs-lookup"><span data-stu-id="8aa1b-114">In defining a subcube, the following rules apply:</span></span>  
  
-   <span data-ttu-id="8aa1b-115">如果包含某个层次结构的 `(All)` 成员，则包含该层次结构的每个成员。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-115">If you include the `(All)` member of a hierarchy, you include every member of that hierarchy.</span></span>  
  
-   <span data-ttu-id="8aa1b-116">如果包含任一成员，则包含该成员的祖先和后代。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-116">If you include any member, you include that member's ascendants and descendants.</span></span>  
  
-   <span data-ttu-id="8aa1b-117">如果包含某个级别的每个成员，则包含该层次结构的所有成员。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-117">If you include every member from a level, you include all members from the hierarchy.</span></span> <span data-ttu-id="8aa1b-118">如果其他层次结构的成员不与此级别的成员共存，它们将被排除（例如，不对称的层次结构，如不包含客户的城市）。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-118">Members from other hierarchies will be excluded if those members do not exist with members from the level (for example, an unbalanced hierarchy such as a city that does not contain customers).</span></span>  
  
-   <span data-ttu-id="8aa1b-119">子多维数据集将始终包含多维数据集的每个 `(All)` 成员。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-119">A subcube will always contain every `(All)` member from the cube.</span></span>  
  
 <span data-ttu-id="8aa1b-120">另外，子多维数据集中的聚合数据将进行可视求和。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-120">Additionally, aggregate values within the subcube are visually totaled.</span></span> <span data-ttu-id="8aa1b-121">例如，一个子多维数据集包含 `USA`、 `WA`和 `OR`。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-121">For example, a subcube contains `USA`, `WA`, and `OR`.</span></span> <span data-ttu-id="8aa1b-122">`USA` 的聚合值将是 `{WA,OR}` 的和，因为该子多维数据集只定义了 `WA` 和 `OR` 这两个州。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-122">The aggregate value for `USA` will be the sum of `{WA,OR}` because `WA` and `OR` are the only states defined by the subcube.</span></span> <span data-ttu-id="8aa1b-123">所有其他州将被忽略。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-123">All other states will be ignored.</span></span>  
  
 <span data-ttu-id="8aa1b-124">另外，显式引用子多维数据集外的单元将返回在整个多维数据集的上下文中计算的单元值。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-124">Also, explicit references to cells outside the subcube return cell values that are evaluated in the context of the whole cube.</span></span> <span data-ttu-id="8aa1b-125">例如，创建一个限制为本年度的子多维数据集。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-125">For example, you create a subcube that is limited to the current year.</span></span> <span data-ttu-id="8aa1b-126">然后使用 [ParallelPeriod](/sql/mdx/parallelperiod-mdx) 函数将本年度与去年相比较。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-126">You then use the [ParallelPeriod](/sql/mdx/parallelperiod-mdx) function to compare the current year to the previous year.</span></span> <span data-ttu-id="8aa1b-127">即使上一年的值位于子多维数据集之外，也会返回值的差异。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-127">The difference in values will be returned even though the previous year's value lies outside the subcube.</span></span>  
  
 <span data-ttu-id="8aa1b-128">最后，如果原始上下文没有被覆盖，在嵌套 select 语句中计算的集函数将在嵌套 select 语句的上下文中计算。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-128">Finally, if the original context is not overwritten, set functions evaluated in a subselect are evaluated in the context of the subselect.</span></span> <span data-ttu-id="8aa1b-129">如果上下文被覆盖，集函数将在整个多维数据集的上下文中计算。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-129">If the context is overwritten, set functions are evaluated in the context of the whole cube.</span></span>  
  
## <a name="create-subcube-example"></a><span data-ttu-id="8aa1b-130">CREATE SUBCUBE 示例</span><span class="sxs-lookup"><span data-stu-id="8aa1b-130">CREATE SUBCUBE Example</span></span>  
 <span data-ttu-id="8aa1b-131">下面的示例创建的子多维数据集将 Budget 多维数据集仅限制到帐户 4200 和 4300：</span><span class="sxs-lookup"><span data-stu-id="8aa1b-131">The following example creates a subcube that restricts the Budget cube to only accounts 4200 and 4300:</span></span>  
  
 `CREATE SUBCUBE Budget AS SELECT {[Account].[Account].&[4200], [Account].[Account].&[4300] } ON 0 FROM Budget`  
  
 <span data-ttu-id="8aa1b-132">为会话创建子多维数据集后，后续的查询将针对该子多维数据集，而不是整个多维数据集。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-132">Having created a subcube for the session, any subsequent queries will be against the subcube, not the whole cube.</span></span> <span data-ttu-id="8aa1b-133">例如，运行下列查询。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-133">For example, you run the following query.</span></span> <span data-ttu-id="8aa1b-134">此查询将只返回帐户 4200 和 4300 中的成员。</span><span class="sxs-lookup"><span data-stu-id="8aa1b-134">This query will only return members from accounts 4200 and 4300.</span></span>  
  
 `SELECT [Account].[Account].Members ON 0, Measures.Members ON 1 FROM Budget`  
  
## <a name="see-also"></a><span data-ttu-id="8aa1b-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8aa1b-135">See Also</span></span>  
 <span data-ttu-id="8aa1b-136">[在查询 &#40;MDX&#41;中建立多维数据集上下文](establishing-cube-context-in-a-query-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="8aa1b-136">[Establishing Cube Context in a Query &#40;MDX&#41;](establishing-cube-context-in-a-query-mdx.md) </span></span>  
 [<span data-ttu-id="8aa1b-137">MDX 查询基础知识 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="8aa1b-137">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
