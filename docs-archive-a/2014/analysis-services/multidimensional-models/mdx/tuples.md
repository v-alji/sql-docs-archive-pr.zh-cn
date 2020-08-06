---
title: 元组 |Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 35b629ae-b1ef-44b1-b556-96956aeb56e7
author: minewiskan
ms.author: owend
ms.openlocfilehash: c39d03d60cb66f3b2e26b2e660bd85f4e5e9d4ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691944"
---
# <a name="tuples"></a><span data-ttu-id="f0f3e-102">元组</span><span class="sxs-lookup"><span data-stu-id="f0f3e-102">Tuples</span></span>
  <span data-ttu-id="f0f3e-103">一个元组唯一标识多维数据集中数据的一个切片。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-103">A tuple uniquely identifies a slice of data from a cube.</span></span> <span data-ttu-id="f0f3e-104">只要没有两个或多个成员属于相同的层次结构，元组就由维度成员的组合构成。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-104">The tuple is formed by a combination of dimension members, as long as there are no two or more members that belong to the same hierarchy.</span></span>  
  
## <a name="implicit-or-default-attribute-members-in-a-tuple"></a><span data-ttu-id="f0f3e-105">元组中的隐式或默认属性成员</span><span class="sxs-lookup"><span data-stu-id="f0f3e-105">Implicit or default attribute members in a tuple</span></span>  
 <span data-ttu-id="f0f3e-106">在 MDX 查询或表达式中定义元组时，不必显式包含每个属性层次结构中的属性成员。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-106">When defining a tuple in an MDX query or expression, you do not need to explicitly include the attribute member from every attribute hierarchy.</span></span> <span data-ttu-id="f0f3e-107">如果属性层次结构中的成员未显式包含在查询或表达式中，则该属性层次结构的默认成员为隐式包含在元组中的属性成员。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-107">If a member from an attribute hierarchy is not explicitly included in a query or an expression, the default member for that attribute hierarchy is the attribute member implicitly included in the tuple.</span></span> <span data-ttu-id="f0f3e-108">除非在多维数据集中进行显式定义，否则每个属性层次结构的默认成员均为“(全部)”成员（如果存在“(全部)”成员）。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-108">Unless otherwise explicitly defined in a cube, the default member for every attribute hierarchy is the (All) member, if an (All) member exists.</span></span> <span data-ttu-id="f0f3e-109">如果属性层次结构中不存在“(全部)”成员，则默认成员为属性层次结构中的顶级成员。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-109">If an (All) member does not exist within an attribute hierarchy, the default member is a member of the attribute hierarchy's top level.</span></span> <span data-ttu-id="f0f3e-110">除非显式定义了默认度量值，否则默认度量值为多维数据集中指定的第一个度量值。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-110">The default measure is the first measure specified in the cube, unless a default measure is explicitly defined.</span></span> <span data-ttu-id="f0f3e-111">有关详细信息，请参阅[定义默认成员](../attribute-properties-define-a-default-member.md)和 [DefaultMember (MDX)](/sql/mdx/defaultmember-mdx)。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-111">For more information, see [Define a Default Member](../attribute-properties-define-a-default-member.md) and [DefaultMember &#40;MDX&#41;](/sql/mdx/defaultmember-mdx).</span></span>  
  
 <span data-ttu-id="f0f3e-112">例如，以下元组通过仅显式定义 Measures 维度的一个成员来标识 Adventure Works 数据库中的一个单元。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-112">For example, the following tuple identifies a single cell in the Adventure Works database by explicitly defining only a single member of the Measures dimension.</span></span>  
  
```  
(Measures.[Reseller Sales Amount])  
```  
  
 <span data-ttu-id="f0f3e-113">上面的示例唯一标识了由 Measures 维度的 Reseller Sales Amount 成员和多维数据集各属性层次结构的默认成员组成的单元。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-113">The previous example uniquely identifies the cell consisting of the Reseller Sales Amount member from the Measures dimension and the default member from every attribute hierarchy in the cube.</span></span> <span data-ttu-id="f0f3e-114">默认成员为除 Destination Currency 属性层次结构之外的各个属性层次结构的“(全部)”成员。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-114">The default member is the (All) member for every attribute hierarchy other than the Destination Currency attribute hierarchy.</span></span> <span data-ttu-id="f0f3e-115">Destination Currency 层次结构的默认成员为 US Dollar 成员（此默认成员是在 MDX 脚本中为 Adventure Works 多维数据集定义的）。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-115">The default member for the Destination Currency hierarchy is the US Dollar member (this default member is defined in the MDX script for the Adventure Works cube).</span></span>  
  
 <span data-ttu-id="f0f3e-116">以下查询将返回前面示例指定元组所引用的单元的值 ($80,450.596.98)。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-116">The following query returns the value for the cell referenced by the tuple specified in the previous example, ($80,450.596.98).</span></span>  
  
```  
SELECT   
Measures.[Reseller Sales Amount] ON COLUMNS   
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="f0f3e-117">为查询中的集（此处由单个元组构成）指定轴时，必须在为行轴指定集之前先为列轴指定集。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-117">When you specify an axis for a set (in this case composed of a single tuple) in a query, you must begin by specifying a set for the column axis before specifying a set for the row axis.</span></span> <span data-ttu-id="f0f3e-118">列轴也可称为“axis(0)”或简称“0”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-118">The column axis can also be referred to as *axis(0)* or simply *0*.</span></span> <span data-ttu-id="f0f3e-119">有关 MDX 查询的详细信息，请参阅[基本 MDX 查询 (MDX)](mdx-query-the-basic-query.md)。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-119">For more information about MDX queries, see [The Basic MDX Query &#40;MDX&#41;](mdx-query-the-basic-query.md).</span></span>  
  
### <a name="tuples-as-values-or-member-references"></a><span data-ttu-id="f0f3e-120">作为值或成员引用的元组</span><span class="sxs-lookup"><span data-stu-id="f0f3e-120">Tuples as values or member references</span></span>  
 <span data-ttu-id="f0f3e-121">如前面的示例所示，您可以在查询中使用元组返回该元组所引用的单元的值。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-121">You can use a tuple in a query to return the value in the cell that is referenced by the tuple, as in the previous example.</span></span> <span data-ttu-id="f0f3e-122">或者您也可以在表达式中使用元组显式引用该元组中指定的成员。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-122">Or you can use a tuple in an expression to explicitly refer to the members specified in the tuple.</span></span> <span data-ttu-id="f0f3e-123">查询或表达式可使用返回元组或获取元组的函数。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-123">The query or the expression can utilize functions that either return or consume tuples.</span></span> <span data-ttu-id="f0f3e-124">元组可用来引用它所指定的单元的值，或者用来指定成员组合（当元组用在函数中时）。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-124">A tuple can be used to either refer to the value of the cell that the tuple specifies, or to specify a combination of members when utilized in a function.</span></span>  
  
### <a name="tuple-dimensionality"></a><span data-ttu-id="f0f3e-125">元组维数</span><span class="sxs-lookup"><span data-stu-id="f0f3e-125">Tuple dimensionality</span></span>  
 <span data-ttu-id="f0f3e-126">元组的 \*\* “维数”指元组中成员的序列或顺序。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-126">The *dimensionality* of a tuple refers to the sequence or order of the members in the tuple.</span></span> <span data-ttu-id="f0f3e-127">由于隐式成员总是以相同的顺序出现，因此维数通常是针对元组的显式定义成员而言。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-127">Since the implicit members always occur in the same order, dimensionality is most often thought of in terms of the explicitly defined members of the tuple.</span></span> <span data-ttu-id="f0f3e-128">定义元组集时，元组成员的顺序非常重要。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-128">The ordering of the members of the tuple is important when you define a set of tuples.</span></span> <span data-ttu-id="f0f3e-129">以下示例在列轴上的一个元组中包含了两个成员。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-129">The following example includes two members in a tuple on the column axis.</span></span>  
  
```  
SELECT   
([Measures].[Reseller Sales Amount],[Date].[Calendar Year].[CY 2004]) ON COLUMNS   
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="f0f3e-130">从多个维度显式指定元组中的成员时，必须将整个元组包含在括号中。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-130">When you explicitly specify a member in a tuple from more than one dimension, you must include the entire tuple in parentheses.</span></span> <span data-ttu-id="f0f3e-131">如果仅指定元组中的一个成员，则括号是可选的。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-131">When only specifying a single member in a tuple, parentheses are optional.</span></span>  
  
 <span data-ttu-id="f0f3e-132">在前面的示例中，查询中的元组指定返回位于 Measures 维度的 Reseller Sales Amount Measure 与 Date 维度中 Calendar Year 属性层次结构的 CY 2004 成员相交处的多维数据集单元。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-132">The tuple in the query in the previous example specifies the return of the cube cell at the intersection of the Reseller Sales Amount Measure of the Measures dimension and the CY 2004 member of the Calendar Year attribute hierarchy in the Date dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f0f3e-133">属性成员可以按成员名称或成员键引用。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-133">An attribute member can be referred by either its member name or its member key.</span></span> <span data-ttu-id="f0f3e-134">在前面的示例中，您可以将对 [CY 2004] 的引用替换为对 &[2004] 的引用。</span><span class="sxs-lookup"><span data-stu-id="f0f3e-134">In the previous example, you could replace the reference to [CY 2004] with &[2004].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0f3e-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f0f3e-135">See Also</span></span>  
 <span data-ttu-id="f0f3e-136">[MDX &#40;Analysis Services 中的关键概念&#41;](../key-concepts-in-mdx-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="f0f3e-136">[Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span></span>  
 <span data-ttu-id="f0f3e-137">[多维数据集空间](cube-space.md) </span><span class="sxs-lookup"><span data-stu-id="f0f3e-137">[Cube Space](cube-space.md) </span></span>  
 <span data-ttu-id="f0f3e-138">[Autoexists](autoexists.md) </span><span class="sxs-lookup"><span data-stu-id="f0f3e-138">[Autoexists](autoexists.md) </span></span>  
 [<span data-ttu-id="f0f3e-139">使用成员、元组和集 (MDX)</span><span class="sxs-lookup"><span data-stu-id="f0f3e-139">Working with Members, Tuples, and Sets &#40;MDX&#41;</span></span>](working-with-members-tuples-and-sets-mdx.md)  
  
  
