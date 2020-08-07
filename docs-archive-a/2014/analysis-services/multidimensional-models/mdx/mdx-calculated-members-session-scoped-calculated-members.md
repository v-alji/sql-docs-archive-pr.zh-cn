---
title: " (MDX) 创建会话作用域的计算成员 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- CREATE MEMBER statement
- session-scoped calculated members [MDX]
ms.assetid: 2875ed89-2c26-4645-8ed9-8848479d110f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8fe7a9f137d8b74eaa5bad104dbfdb471dd14588
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589315"
---
# <a name="creating-session-scoped-calculated-members-mdx"></a><span data-ttu-id="50567-102">创建会话作用域的计算成员 (MDX)</span><span class="sxs-lookup"><span data-stu-id="50567-102">Creating Session-Scoped Calculated Members (MDX)</span></span>
  <span data-ttu-id="50567-103">若要创建在整个多维表达式 (MDX) 会话中都可用的计算成员，请使用 [CREATE MEMBER](/sql/mdx/mdx-data-definition-create-member) 语句。</span><span class="sxs-lookup"><span data-stu-id="50567-103">To create a calculated member that is available throughout a Multidimensional Expressions (MDX) session, you use the [CREATE MEMBER](/sql/mdx/mdx-data-definition-create-member) statement.</span></span> <span data-ttu-id="50567-104">直到 MDX 会话关闭才会删除使用 CREATE MEMBER 语句创建的计算成员。</span><span class="sxs-lookup"><span data-stu-id="50567-104">A calculated member that is created by using the CREATE MEMBER statement will not be removed until after the MDX session closes.</span></span>  
  
 <span data-ttu-id="50567-105">如本主题中所介绍，CREATE MEMBER 语句的语法很直观且易于使用。</span><span class="sxs-lookup"><span data-stu-id="50567-105">As discussed in this topic, the syntax of the CREATE MEMBER statement is straightforward and easy to use.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="50567-106">有关计算成员的详细信息，请参阅[在 MDX 中生成计算成员 (MDX)](mdx-calculated-members-building-calculated-members.md)。</span><span class="sxs-lookup"><span data-stu-id="50567-106">For more information about calculated members, see [Building Calculated Members in MDX &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md).</span></span>  
  
## <a name="create-member-syntax"></a><span data-ttu-id="50567-107">CREATE MEMBER 语法</span><span class="sxs-lookup"><span data-stu-id="50567-107">CREATE MEMBER Syntax</span></span>  
 <span data-ttu-id="50567-108">使用下列语法将 CREATE MEMBER 语句添加到 MDX 语句中：</span><span class="sxs-lookup"><span data-stu-id="50567-108">Use the following syntax to add the CREATE MEMBER statement to the MDX statement:</span></span>  
  
```  
CREATE [SESSION] MEMBER [<cube-name>.]<fully-qualified-member-name> AS <expression> [,<property-definition-list>]  
<cube name> ::= CURRENTCUBE | <Cube Name>  
<property-definition-list> ::= <property-definition>  
  | <property-definition>, <property-definition-list>  
<property-definition> ::= <property-identifier> = <property-value>  
<property-identifier> ::= VISIBLE | SOLVEORDER | SOLVE_ORDER | FORMAT_STRING | NON_EMPTY_BEHAVIOR <ole db member properties>  
```  
  
 <span data-ttu-id="50567-109">在 CREATE MEMBER 语句的语法中， `fully-qualified-member-name` 值是计算成员的完全限定名。</span><span class="sxs-lookup"><span data-stu-id="50567-109">In the syntax for the CREATE MEMBER statement, the `fully-qualified-member-name` value is the fully qualified name of the calculated member.</span></span> <span data-ttu-id="50567-110">完全限定名包含计算成员关联的维度或级别。</span><span class="sxs-lookup"><span data-stu-id="50567-110">The fully qualified name includes the dimension or level to which the calculated member is associated.</span></span> <span data-ttu-id="50567-111">计算表达式值后， `expression` 值将返回计算成员的值。</span><span class="sxs-lookup"><span data-stu-id="50567-111">The `expression` value returns the value of the calculated member after the expression value has been evaluated,.</span></span>  
  
## <a name="create-member-example"></a><span data-ttu-id="50567-112">CREATE MEMBER 示例</span><span class="sxs-lookup"><span data-stu-id="50567-112">CREATE MEMBER Example</span></span>  
 <span data-ttu-id="50567-113">下面的示例使用 CREATE MEMBER 语句创建 `LastFourStores` 计算成员。</span><span class="sxs-lookup"><span data-stu-id="50567-113">The following example uses the CREATE MEMBER statement to create the `LastFourStores` calculated member.</span></span> <span data-ttu-id="50567-114">此计算成员返回最后四家商店售出的部件总和，并且在多维数据集的整个会话中都可用。</span><span class="sxs-lookup"><span data-stu-id="50567-114">This calculated member returns the sum of units sold for the last four stores, and will be available throughout the whole session of the cube.</span></span>  
  
```  
Create Session Member [Store].[Measures].LastFourStores as   
sum(([Stores].[ByLocation].Lag(3) :  
[Stores].[ByLocation].NextMember), [Measures].[Units Sold])  
```  
  
## <a name="see-also"></a><span data-ttu-id="50567-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="50567-115">See Also</span></span>  
 [<span data-ttu-id="50567-116">创建查询作用域的计算成员 (MDX)</span><span class="sxs-lookup"><span data-stu-id="50567-116">Creating Query-Scoped Calculated Members &#40;MDX&#41;</span></span>](mdx-calculated-members-query-scoped-calculated-members.md)  
  
  
