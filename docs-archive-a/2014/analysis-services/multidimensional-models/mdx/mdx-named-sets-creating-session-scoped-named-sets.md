---
title: " (MDX) 创建会话作用域的命名集 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- CREATE SET statement
- session-scoped named sets [MDX]
ms.assetid: b751e1e4-6d4c-4d36-a28d-ffdaaee0f1c7
author: minewiskan
ms.author: owend
ms.openlocfilehash: d35bd61dcc59eca8bcb920ed99f2e791631047c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690824"
---
# <a name="creating-session-scoped-named-sets-mdx"></a><span data-ttu-id="35be7-102">创建会话作用域的命名集 (MDX)</span><span class="sxs-lookup"><span data-stu-id="35be7-102">Creating Session-Scoped Named Sets (MDX)</span></span>
  <span data-ttu-id="35be7-103">若要创建在整个多维表达式 (MDX) 会话期间都可用的命名集，请使用 [CREATE SET](/sql/mdx/mdx-data-definition-create-set) 语句。</span><span class="sxs-lookup"><span data-stu-id="35be7-103">To create a named set that is available throughout a Multidimensional Expressions (MDX) session, you use the [CREATE SET](/sql/mdx/mdx-data-definition-create-set) statement.</span></span> <span data-ttu-id="35be7-104">直到 MDX 会话关闭后才会删除使用 CREATE SET 语句创建的命名集。</span><span class="sxs-lookup"><span data-stu-id="35be7-104">A named set that is created by using the CREATE SET statement will not be removed until after the MDX session closes.</span></span>  
  
 <span data-ttu-id="35be7-105">如本主题中所介绍，WITH 关键字的语法很直观且易于使用。</span><span class="sxs-lookup"><span data-stu-id="35be7-105">As discussed in this topic, the syntax of the WITH keyword is straightforward and easy to use.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="35be7-106">有关命名集的详细信息，请参阅[在 MDX 中生成命名集 (MDX)](mdx-named-sets-building-named-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="35be7-106">For more information about named sets, see [Building Named Sets in MDX &#40;MDX&#41;](mdx-named-sets-building-named-sets.md).</span></span>  
  
## <a name="create-set-syntax"></a><span data-ttu-id="35be7-107">CREATE SET 语法</span><span class="sxs-lookup"><span data-stu-id="35be7-107">CREATE SET Syntax</span></span>  
 <span data-ttu-id="35be7-108">CREATE SET 语句的语法如下：</span><span class="sxs-lookup"><span data-stu-id="35be7-108">Use the following syntax for the CREATE SET statement:</span></span>  
  
```  
CREATE SESSION SET [CURRENTCUBE. | <cube name>.]<Set Identifier> AS <Set Expression>  
```  
  
 <span data-ttu-id="35be7-109">在 CREATE SET 语法中， `cube name` 参数包含多维数据集的名称，该多维数据集包含命名集的成员。</span><span class="sxs-lookup"><span data-stu-id="35be7-109">In the CREATE SET syntax, the `cube name` parameter contains the name of the cube that contains the members for the named set.</span></span> <span data-ttu-id="35be7-110">如果未指定 `cube name` 参数，则当前的多维数据集将用作包含命名集的成员的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="35be7-110">If the `cube name` parameter is not specified, the current cube will be used as the cube that contains the member for the named set.</span></span> <span data-ttu-id="35be7-111">另外， `Set_Identifier` 参数包含命名集的别名， `Set_Expression` 参数包含命名集别名引用的集表达式。</span><span class="sxs-lookup"><span data-stu-id="35be7-111">Also, the `Set_Identifier` parameter contains the alias for the named set, and the `Set_Expression` parameter contains the set expression to which the named set alias will refer.</span></span>  
  
## <a name="create-set-example"></a><span data-ttu-id="35be7-112">CREATE SET 示例</span><span class="sxs-lookup"><span data-stu-id="35be7-112">CREATE SET Example</span></span>  
 <span data-ttu-id="35be7-113">下面的示例使用 CREATE SET 语句创建基于 Store 多维数据集的 `SetCities_2_3` 命名集。</span><span class="sxs-lookup"><span data-stu-id="35be7-113">The following example uses the CREATE SET statement to create the `SetCities_2_3` named set based on the Store cube.</span></span> <span data-ttu-id="35be7-114">`SetCities_2_3` 命名集的成员是位于 City 2 和 City 3 的商店。</span><span class="sxs-lookup"><span data-stu-id="35be7-114">The members of the `SetCities_2_3` named set are the stores within City 2 and City 3.</span></span>  
  
```  
create Session set [Store].[SetCities_2_3] as  
{[Data Stores].[ByLocation].[State].&[CA].&[City 02],  
[Data Stores].[ByLocation].[State].&[NH].&[City 03]}  
```  
  
 <span data-ttu-id="35be7-115">通过使用 CREATE SET 语句定义 `SetCities_2_3` 命名集，此命名集在当前 MDX 会话期间将始终可用。</span><span class="sxs-lookup"><span data-stu-id="35be7-115">By using the CREATE SET statement to define the `SetCities_2_3` named set, this named set remains available for the length of the current MDX session.</span></span> <span data-ttu-id="35be7-116">下面的示例是一个将返回 City 2 和 City 3 成员的有效查询，该查询可在创建 `SetCities_2_3` 命名集后、结束会话前的任何时间运行。</span><span class="sxs-lookup"><span data-stu-id="35be7-116">The following example is a valid query that would return City 2 and City 3 members, and that could be run anytime after you create the `SetCities_2_3` named set and before the session closes.</span></span>  
  
```  
select SetCities_2_3 on 0 from [Store]  
```  
  
## <a name="see-also"></a><span data-ttu-id="35be7-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="35be7-117">See Also</span></span>  
 [<span data-ttu-id="35be7-118">创建查询作用域的命名集 (MDX)</span><span class="sxs-lookup"><span data-stu-id="35be7-118">Creating Query-Scoped Named Sets &#40;MDX&#41;</span></span>](mdx-named-sets-creating-query-scoped-named-sets.md)  
  
  
