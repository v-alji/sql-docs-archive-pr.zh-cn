---
title: 在查询 (MDX) 中建立多维数据集上下文 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], MDX
- MDX [Analysis Services], cube context
- SELECT statement [MDX]
- Multidimensional Expressions [Analysis Services], cube context
- queries [MDX], cube context
ms.assetid: 79d6a1e8-2825-4eb9-97df-5071aecae8f0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 72ae6e19f879651feb47841d70b444e9f845c74e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682407"
---
# <a name="establishing-cube-context-in-a-query-mdx"></a><span data-ttu-id="7d711-102">在查询中建立多维数据集上下文 (MDX)</span><span class="sxs-lookup"><span data-stu-id="7d711-102">Establishing Cube Context in a Query (MDX)</span></span>
  <span data-ttu-id="7d711-103">每个 MDX 查询都是在指定的多维数据集上下文中运行的。</span><span class="sxs-lookup"><span data-stu-id="7d711-103">Every MDX query runs within a specified cube context.</span></span> <span data-ttu-id="7d711-104">此上下文定义了查询中的表达式求值的成员。</span><span class="sxs-lookup"><span data-stu-id="7d711-104">This context defines the members that are evaluated by the expressions within the query.</span></span>  
  
 <span data-ttu-id="7d711-105">在 SELECT 语句中，FROM 子句用于确定多维数据集上下文。</span><span class="sxs-lookup"><span data-stu-id="7d711-105">In the SELECT statement, the FROM clause determines the cube context.</span></span> <span data-ttu-id="7d711-106">此上下文可以是整个多维数据集，也可以只是该多维数据集的一个子多维数据集。</span><span class="sxs-lookup"><span data-stu-id="7d711-106">This context can be the whole cube or just a subcube from that cube.</span></span> <span data-ttu-id="7d711-107">如果通过 FROM 子句指定了多维数据集上下文，就可以使用其他函数来扩展或限制该上下文。</span><span class="sxs-lookup"><span data-stu-id="7d711-107">Having specified cube context through the FROM clause, you can use additional functions to expand or restrict that context.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7d711-108">也可以使用 SCOPE 和 CALCULATE 语句在 MDX 脚本中管理多维数据集上下文。</span><span class="sxs-lookup"><span data-stu-id="7d711-108">The SCOPE and CALCULATE statements also let you manage cube context from within an MDX script.</span></span> <span data-ttu-id="7d711-109">有关详细信息，请参阅 [MDX 脚本编写基础知识 (Analysis Services)](mdx-scripting-fundamentals-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7d711-109">For more information, see [MDX Scripting Fundamentals &#40;Analysis Services&#41;](mdx-scripting-fundamentals-analysis-services.md).</span></span>  
  
## <a name="from-clause-syntax"></a><span data-ttu-id="7d711-110">FROM 子句的语法</span><span class="sxs-lookup"><span data-stu-id="7d711-110">FROM Clause Syntax</span></span>  
 <span data-ttu-id="7d711-111">以下语法说明了 FROM 子句：</span><span class="sxs-lookup"><span data-stu-id="7d711-111">The following syntax describes the FROM clause:</span></span>  
  
```  
<SELECT subcube clause> ::=  
   Cube_Identifier |   
   (SELECT [  
      * |   
      ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]   
   FROM <SELECT subcube clause> <SELECT slicer axis clause> )  
```  
  
 <span data-ttu-id="7d711-112">请注意，在此语法中， `<SELECT subcube clause>` 子句说明了执行 SELECT 语句时所在的多维数据集或子多维数据集。</span><span class="sxs-lookup"><span data-stu-id="7d711-112">In this syntax, notice that it is the `<SELECT subcube clause>` clause that describes the cube or subcube on which the SELECT statement is executed.</span></span>  
  
 <span data-ttu-id="7d711-113">FROM 子句的一个简单例子为针对整个 Adventure Works 示例多维数据集执行的子句。</span><span class="sxs-lookup"><span data-stu-id="7d711-113">A simple example of a FROM clause would be one that runs against the entire Adventure Works sample cube.</span></span> <span data-ttu-id="7d711-114">这样的 FROM 子句将具有以下格式：</span><span class="sxs-lookup"><span data-stu-id="7d711-114">Such a FROM clause would have the following format:</span></span>  
  
```  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="7d711-115">有关 MDX SELECT 语句中的 FROM 子句的详细信息，请参阅 [SELECT 语句 (MDX)](/sql/mdx/mdx-data-manipulation-select)。</span><span class="sxs-lookup"><span data-stu-id="7d711-115">For more information about the FROM clause in the MDX SELECT statement, see [SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select).</span></span>  
  
## <a name="refining-the-context"></a><span data-ttu-id="7d711-116">完善上下文</span><span class="sxs-lookup"><span data-stu-id="7d711-116">Refining the Context</span></span>  
 <span data-ttu-id="7d711-117">虽然 FROM 子句指定的多维数据集上下文在单个多维数据集中，但这并不会造成您无法一次处理多个多维数据集中的数据。</span><span class="sxs-lookup"><span data-stu-id="7d711-117">Although the FROM clause specifies the cube context as within a single cube, this does not have to limit you from working with data from more than one cube at a time.</span></span>  
  
 <span data-ttu-id="7d711-118">您可以使用 MDX [LookupCube](/sql/mdx/lookupcube-mdx) 函数从多维数据集上下文以外的多维数据集中检索数据。</span><span class="sxs-lookup"><span data-stu-id="7d711-118">You can use the MDX [LookupCube](/sql/mdx/lookupcube-mdx) function to retrieve data from cubes outside the cube context.</span></span> <span data-ttu-id="7d711-119">另外，可以使用诸如 [Filter](/sql/mdx/filter-mdx) 之类的函数在对查询求值时对上下文进行临时限制。</span><span class="sxs-lookup"><span data-stu-id="7d711-119">Additionally, functions such as the [Filter](/sql/mdx/filter-mdx) function, are available that allow temporary restriction of the context while evaluating the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d711-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7d711-120">See Also</span></span>  
 [<span data-ttu-id="7d711-121">MDX 查询基础知识 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="7d711-121">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
