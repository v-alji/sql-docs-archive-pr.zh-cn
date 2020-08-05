---
title: " (MDX) 创建查询作用域的计算成员 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- WITH keyword
- query-scoped calculated members [MDX]
ms.assetid: c4507149-e67b-4e5d-9192-cc911acd9adc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9c0b3e7184f3cc6abd189344bbce1b6e1f948ebb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580932"
---
# <a name="creating-query-scoped-calculated-members-mdx"></a><span data-ttu-id="75caa-102">创建查询作用域的计算成员 (MDX)</span><span class="sxs-lookup"><span data-stu-id="75caa-102">Creating Query-Scoped Calculated Members (MDX)</span></span>
  <span data-ttu-id="75caa-103">如果某个计算成员仅用于单个多维表达式 (MDX) 查询，则可以使用 WITH 关键字定义该计算成员。</span><span class="sxs-lookup"><span data-stu-id="75caa-103">If a calculated member is only required for a single Multidimensional Expressions (MDX) query, you can define that calculated member by using the WITH keyword.</span></span> <span data-ttu-id="75caa-104">使用 WITH 关键字创建的计算成员在执行完查询之后就不再存在。</span><span class="sxs-lookup"><span data-stu-id="75caa-104">A calculated member that is created by using the WITH keyword no longer exists after the query has finished running.</span></span>  
  
 <span data-ttu-id="75caa-105">如本主题中所述，WITH 关键字的语法非常灵活，甚至允许一个计算成员基于另一个计算成员。</span><span class="sxs-lookup"><span data-stu-id="75caa-105">As discussed in this topic, the syntax of the WITH keyword is quite flexible, even allowing a calculated member to be based on another calculated member.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="75caa-106">有关计算成员的详细信息，请参阅[在 MDX 中生成计算成员 (MDX)](mdx-calculated-members-building-calculated-members.md)。</span><span class="sxs-lookup"><span data-stu-id="75caa-106">For more information about calculated members, see [Building Calculated Members in MDX &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md).</span></span>  
  
## <a name="with-keyword-syntax"></a><span data-ttu-id="75caa-107">WITH 关键字语法</span><span class="sxs-lookup"><span data-stu-id="75caa-107">WITH Keyword Syntax</span></span>  
 <span data-ttu-id="75caa-108">使用以下语法将 WITH 关键字添加到 MDX SELECT 语句：</span><span class="sxs-lookup"><span data-stu-id="75caa-108">Use the following syntax to add the WITH keyword to an MDX SELECT statement:</span></span>  
  
```  
[ WITH <SELECT WITH clause> [ , <SELECT WITH clause> ... ] ] SELECT [ * | ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]FROM <SELECT subcube clause> [ <SELECT slicer axis clause> ][ <SELECT cell property list clause> ]  
<SELECT WITH clause> ::=  
   ( [ CALCULATED ] MEMBER <CREATE MEMBER body clause>) | <CREATE MEMBER body clause> ::= Member_Identifier AS 'MDX_Expression'  
   [ <CREATE MEMBER property clause> [ , <CREATE MEMBER property clause> ... ] ]  
<CREATE MEMBER property clause> ::=  
   ( MemberProperty_Identifier = Scalar_Expression )  
  
```  
  
 <span data-ttu-id="75caa-109">在 WITH 关键字的语法中， `Member_Identifier` 值是计算成员的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="75caa-109">In the syntax for the WITH keyword, the `Member_Identifier` value is the fully qualified name of the calculated member.</span></span> <span data-ttu-id="75caa-110">此完全限定名称包括计算成员所关联的维度或级别。</span><span class="sxs-lookup"><span data-stu-id="75caa-110">This fully qualified name includes the dimension or level to which the calculated member is associated.</span></span> <span data-ttu-id="75caa-111">对 `MDX_Expression` 表达式求值以后，将返回计算成员的值。</span><span class="sxs-lookup"><span data-stu-id="75caa-111">The `MDX_Expression` value returns the value of the calculated member after the expression value has been evaluated.</span></span> <span data-ttu-id="75caa-112">另外，可以通过在 `MemberProperty_Identifier` 值中提供单元属性的名称以及在 `Scalar_Expression` 值中提供单元属性的值，指定计算成员内部单元属性的值。</span><span class="sxs-lookup"><span data-stu-id="75caa-112">The values of intrinsic cell properties for a calculated member can be optionally specified by supplying the name of the cell property in the `MemberProperty_Identifier` value and the value of the cell property in the `Scalar_Expression` value.</span></span>  
  
## <a name="with-keyword-examples"></a><span data-ttu-id="75caa-113">WITH 关键字示例</span><span class="sxs-lookup"><span data-stu-id="75caa-113">WITH Keyword Examples</span></span>  
 <span data-ttu-id="75caa-114">下面的 MDX 查询定义了计算成员 `[Measures].[Special Discount]`，用来基于原始折扣金额来计算特殊折扣。</span><span class="sxs-lookup"><span data-stu-id="75caa-114">The following MDX query defines a calculated member, `[Measures].[Special Discount]`, calculating a special discount based on the original discount amount.</span></span>  
  
```  
WITH   
   MEMBER [Measures].[Special Discount] AS  
   [Measures].[Discount Amount] * 1.5  
SELECT   
   [Measures].[Special Discount] on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
```  
  
 <span data-ttu-id="75caa-115">还可以在层次结构中的任意位置创建计算成员。</span><span class="sxs-lookup"><span data-stu-id="75caa-115">You can also create calculated members at any point within a hierarchy.</span></span> <span data-ttu-id="75caa-116">例如，下面的 MDX 查询为某个假设的“销售额”多维数据集定义计算成员 `[BigSeller]` 。</span><span class="sxs-lookup"><span data-stu-id="75caa-116">For example, the following MDX query defines the `[BigSeller]` calculated member for a hypothetical Sales cube.</span></span> <span data-ttu-id="75caa-117">此计算成员用于确定指定商店的啤酒和葡萄酒的单位销售额是否不少于 100.00。</span><span class="sxs-lookup"><span data-stu-id="75caa-117">This calculated member determines whether a specified store has at least 100.00 in unit sales for beer and wine.</span></span> <span data-ttu-id="75caa-118">但是，此查询所创建的 `[BigSeller]` 计算成员不是 `[Product]` 维度的子成员，而是 `[Beer and Wine]` 成员的子成员。</span><span class="sxs-lookup"><span data-stu-id="75caa-118">However, the query creates the `[BigSeller]` calculated member not as a child member of the `[Product]` dimension, but instead as a child member of the `[Beer and Wine]` member.</span></span>  
  
```  
WITH   
   MEMBER [Product].[Beer and Wine].[BigSeller] AS  
  IIf([Product].[Beer and Wine] > 100, "Yes","No")  
SELECT  
   {[Product].[BigSeller]} ON COLUMNS,  
   Store.[Store Name].Members ON ROWS  
FROM Sales  
  
```  
  
 <span data-ttu-id="75caa-119">计算成员并非只能依赖于多维数据集中的现有成员。</span><span class="sxs-lookup"><span data-stu-id="75caa-119">Calculated members do not have to depend only on existing members in a cube.</span></span> <span data-ttu-id="75caa-120">计算成员还可以基于在同一 MDX 表达式中定义的其他计算成员。</span><span class="sxs-lookup"><span data-stu-id="75caa-120">Calculated member can also be based on other calculated members defined in the same MDX expression.</span></span> <span data-ttu-id="75caa-121">例如，下面的 MDX 查询使用在第一个计算成员 `[Measures].[Special Discount]`中创建的值来生成第二个计算成员 `[Measures].[Special Discounted Amount]`的值。</span><span class="sxs-lookup"><span data-stu-id="75caa-121">For example, the following MDX query uses the value created in the first calculated member, `[Measures].[Special Discount]`, to generate the value of the second calculated member, `[Measures].[Special Discounted Amount]`.</span></span>  
  
```  
WITH   
   MEMBER [Measures].[Special Discount] AS  
   [Measures].[Discount Percentage] * 1.5,   
   FORMAT_STRING = 'Percent'  
  
   MEMBER [Measures].[Special Discounted Amount] AS  
   [Measures].[Reseller Average Unit Price] * [Measures].[Special Discount],   
   FORMAT_STRING = 'Currency'  
  
SELECT   
   {[Measures].[Special Discount], [Measures].[Special Discounted Amount]} on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="75caa-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="75caa-122">See Also</span></span>  
 <span data-ttu-id="75caa-123">[Mdx 函数引用 &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="75caa-123">[MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span></span>  
 <span data-ttu-id="75caa-124">[SELECT 语句 &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select) </span><span class="sxs-lookup"><span data-stu-id="75caa-124">[SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select) </span></span>  
 [<span data-ttu-id="75caa-125">创建会话作用域的计算成员 (MDX)</span><span class="sxs-lookup"><span data-stu-id="75caa-125">Creating Session-Scoped Calculated Members &#40;MDX&#41;</span></span>](mdx-calculated-members-session-scoped-calculated-members.md)  
  
  
