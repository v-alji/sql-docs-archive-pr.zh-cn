---
title: 多维数据集空间 |Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c3a012b4-9ca0-4fb8-9c26-5ecc0e2e2b2b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0a6a6da73815f06aa5ab80f6ad5a9d06227ed842
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580936"
---
# <a name="cube-space"></a><span data-ttu-id="a9157-102">多维数据集空间</span><span class="sxs-lookup"><span data-stu-id="a9157-102">Cube Space</span></span>
  <span data-ttu-id="a9157-103">“多维数据集空间”是多维数据集属性层次结构的成员与多维数据集的度量值的乘积。</span><span class="sxs-lookup"><span data-stu-id="a9157-103">Cube space is the product of the members of a cube's attribute hierarchies with the cube's measures.</span></span> <span data-ttu-id="a9157-104">因此，多维数据集空间由多维数据集中所有属性层次结构成员和多维数据集的度量值的组合乘积确定，并且定义多维数据集的最大大小。</span><span class="sxs-lookup"><span data-stu-id="a9157-104">Therefore, the cube space is determined by the combinatorial product of all attribute hierarchy members in the cube and the cube's measures and defines the maximum size of the cube.</span></span> <span data-ttu-id="a9157-105">需要特别注意的是，此空间包括属性层次结构成员的所有可能组合；甚至包括在真实世界可能会认定为不可能的组合，例如城市是巴黎而国家/地区是英国、西班牙、日本、印度或其他地方的组合。</span><span class="sxs-lookup"><span data-stu-id="a9157-105">It is important to note that this space includes all possible combinations of attribute hierarchy members; even combinations that might be deem as impossible in the real world i.e. combinations where the city is Paris and the countries are England or Spain or Japan or India or elsewhere.</span></span>  
  
## <a name="autoexists-and-cube-space"></a><span data-ttu-id="a9157-106">Autoexists 和多维数据集空间</span><span class="sxs-lookup"><span data-stu-id="a9157-106">Autoexists and cube space</span></span>  
 <span data-ttu-id="a9157-107">\*\* “autoexists”的概念将此多维数据集空间限制为那些实际存在的单元。</span><span class="sxs-lookup"><span data-stu-id="a9157-107">The concept of *autoexists* limits this cube space to those cells that actually exist.</span></span> <span data-ttu-id="a9157-108">维度中属性层次结构的成员可能不与相同维度中其他属性层次结构的成员共存。</span><span class="sxs-lookup"><span data-stu-id="a9157-108">Members of an attribute hierarchy in a dimension may not exist with members of another attribute hierarchy in the same dimension.</span></span>  
  
 <span data-ttu-id="a9157-109">例如，某多维数据集具有 City 属性层次结构、Country 属性层次结构和 Internet Sales Amount 度量值，则此多维数据集的空间仅包含那些共存的成员。</span><span class="sxs-lookup"><span data-stu-id="a9157-109">For example, if you have a cube that has a City attribute hierarchy, a Country attribute hierarchy, and an Internet Sales Amount measure, the space of this cube only includes those members that exist with each other.</span></span> <span data-ttu-id="a9157-110">例如，如果 City 属性层次结构包含城市 New York、London、Paris、Tokyo 和 Melbourne，而 Country 属性层次结构包含国家（地区）United States、United Kingdom、France、Japan 和 Australia，则该多维数据集的空间不包含 Paris 和 United States 相交处的空间（单元）。</span><span class="sxs-lookup"><span data-stu-id="a9157-110">For example, if the City attribute hierarchy includes the cities New York, London, Paris, Tokyo, and Melbourne; and the Country attribute hierarchy includes the countries United States, United Kingdom, France, Japan, and Australia; then the space of the cube does not include the space (cell) at the intersection of Paris and United States.</span></span>  
  
 <span data-ttu-id="a9157-111">当查询单元不存在时，不存在的单元返回空，即它们无法包含计算结果，并且您不能定义写入此空间的计算。</span><span class="sxs-lookup"><span data-stu-id="a9157-111">When querying cells that do not exist, non-existing cells return nulls; that is, they cannot contain calculations and you cannot define a calculation that writes to this space.</span></span> <span data-ttu-id="a9157-112">例如，下面的语句包含不存在的单元。</span><span class="sxs-lookup"><span data-stu-id="a9157-112">For example, the following statement includes cells that do not exist.</span></span>  
  
```  
SELECT [Customer].[Gender].[Gender].Members ON COLUMNS,  
{[Customer].[Customer].[Aaron A. Allen]  
   ,[Customer].[Customer].[Abigail Clark]} ON ROWS   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="a9157-113">此查询使用 [Members (Set) (MDX)](/sql/mdx/members-set-mdx) 函数返回列轴上 Gender 属性层次结构的成员集，并将此集与行轴上 Customer 属性层次结构的指定成员集相交。</span><span class="sxs-lookup"><span data-stu-id="a9157-113">This query uses the [Members (Set) (MDX)](/sql/mdx/members-set-mdx) function to return the set of members of the Gender attribute hierarchy on the column axis, and crosses this set with the specified set of members from the Customer attribute hierarchy on the row axis.</span></span>  
  
 <span data-ttu-id="a9157-114">执行前面的查询时，Aaron A. Allen 与 Female 相交处的单元将显示空。</span><span class="sxs-lookup"><span data-stu-id="a9157-114">When you execute the previous query, the cell at the intersection of Aaron A. Allen and Female displays a null.</span></span> <span data-ttu-id="a9157-115">同样，Abigail Clark 与 Male 相交处的单元也将显示空。</span><span class="sxs-lookup"><span data-stu-id="a9157-115">Similarly, the cell at the intersection of Abigail Clark and Male displays a null.</span></span> <span data-ttu-id="a9157-116">这些单元不存在并且不能包含值，但不存在的单元可出现在查询返回的结果中。</span><span class="sxs-lookup"><span data-stu-id="a9157-116">These cells do not exist and cannot contain a value, but cells that do not exist can appear in the result returned by a query.</span></span>  
  
 <span data-ttu-id="a9157-117">如果使用 [Crossjoin (MDX)](/sql/mdx/crossjoin-mdx) 函数返回同一维度中属性层次结构中的属性层次结构成员的叉积，自动共存将限制只返回那些实际存在的元组集，而不是返回整个笛卡尔乘积的元组。</span><span class="sxs-lookup"><span data-stu-id="a9157-117">When you use the [Crossjoin (MDX)](/sql/mdx/crossjoin-mdx) function to return the cross-product of attribute hierarchy members from attribute hierarchies in the same dimension, auto-exists limits those tuples being returned to the set of tuples that actually exist, rather than returning a full Cartesian product.</span></span> <span data-ttu-id="a9157-118">例如，运行以下查询并检查其结果。</span><span class="sxs-lookup"><span data-stu-id="a9157-118">For example, run and then examine the results from the execution of the following query.</span></span>  
  
```  
SELECT CROSSJOIN  
   (  
      {[Customer].[Country].[United States]},  
         [Customer].[State-Province].Members  
  ) ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="a9157-119">请注意 0 用于表示列轴的名称，它是列轴“axis(0)”的简称。</span><span class="sxs-lookup"><span data-stu-id="a9157-119">Notice that 0 is used to designate the column axis, which is shorthand for axis(0) - which is the column axis.</span></span>  
  
 <span data-ttu-id="a9157-120">前面的查询仅为查询中每个属性层次结构的共存成员返回单元。</span><span class="sxs-lookup"><span data-stu-id="a9157-120">The previous query only returns cells for members from each attribute hierarchy in the query that exist with each other.</span></span> <span data-ttu-id="a9157-121">前面的查询还可以使用[ \* (交叉结合) ](/sql/mdx/crossjoin-mdx)的新 \* 变体写入 (MDX) 函数。</span><span class="sxs-lookup"><span data-stu-id="a9157-121">The previous query can also be written using the new \* variant of the [\* (Crossjoin) (MDX)](/sql/mdx/crossjoin-mdx) function.</span></span>  
  
```  
SELECT   
   [Customer].[Country].[United States] *   
      [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
 <span data-ttu-id="a9157-122">前面的查询还可以通过以下方式来编写：</span><span class="sxs-lookup"><span data-stu-id="a9157-122">The previous query could also be written in the following manner:</span></span>  
  
```  
SELECT [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE (Measures.[Internet Sales Amount],  
   [Customer].[Country].[United States])  
```  
  
 <span data-ttu-id="a9157-123">虽然结果集中的元数据将不同，但返回的单元值将是相同的。</span><span class="sxs-lookup"><span data-stu-id="a9157-123">The cells values returned will be identical, although the metadata in the result set will be different.</span></span> <span data-ttu-id="a9157-124">例如，在前面的查询中，Country 层次结构已移到切片器轴（在 WHERE 子句中），因此没有显式显示在结果集中。</span><span class="sxs-lookup"><span data-stu-id="a9157-124">For example, with the previous query, the Country hierarchy was moved to the slicer axis (in the WHERE clause) and therefore does not appear explicitly in the result set.</span></span>  
  
 <span data-ttu-id="a9157-125">这三个前面的查询都说明了中的自动共存行为的影响 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a9157-125">Each of these three previous queries demonstrates the effect of the auto-exists behavior in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="user-defined-hierarchies-and-cube-space"></a><span data-ttu-id="a9157-126">用户定义的层次结构和多维数据集空间</span><span class="sxs-lookup"><span data-stu-id="a9157-126">User-Defined Hierarchies and Cube Space</span></span>  
 <span data-ttu-id="a9157-127">本主题前面的示例使用属性层次结构定义了多维数据集空间中的位置。</span><span class="sxs-lookup"><span data-stu-id="a9157-127">The previous examples in this topic define positions in cube space by using attribute hierarchies.</span></span> <span data-ttu-id="a9157-128">不过，您还可以使用根据维度中属性层次结构所定义的用户定义的层次结构来定义多维数据集空间中的位置。</span><span class="sxs-lookup"><span data-stu-id="a9157-128">However, you can also define a position in cube space by using user-defined hierarchies that have been defined based on attribute hierarchies in a dimension.</span></span> <span data-ttu-id="a9157-129">用户定义的层次结构是属性层次结构的层次结构，旨在帮助用户浏览多维数据集数据。</span><span class="sxs-lookup"><span data-stu-id="a9157-129">A user-defined hierarchy is a hierarchy of attribute hierarchies designed to facilitate browsing of cube data by users.</span></span>  
  
 <span data-ttu-id="a9157-130">例如，上节中的 `CROSSJOIN` 查询也可以按照如下方式编写：</span><span class="sxs-lookup"><span data-stu-id="a9157-130">For example, the `CROSSJOIN` query in the previous section could also have been written as follows:</span></span>  
  
```  
SELECT CROSSJOIN  
   (  
      {[Customer].[Country].[United States]},  
         [Customer].[Customer Geography].[State-Province].Members  
   )   
ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
 <span data-ttu-id="a9157-131">在前面的查询中，Customer 维度中的 Customer Geography 用户定义的层次结构用于定义先前使用属性层次结构定义的多维数据集空间中的位置。</span><span class="sxs-lookup"><span data-stu-id="a9157-131">In the previous query, the Customer Geography user-defined hierarchy within the Customer dimension is used to define the position in cube space that was previously defined by using an attribute hierarchy.</span></span> <span data-ttu-id="a9157-132">可以使用属性层次结构或用户定义的层次结构来定义多维数据集空间中的同一个位置。</span><span class="sxs-lookup"><span data-stu-id="a9157-132">The identical position in cube space can be defined by using either attribute hierarchies or user-defined hierarchies.</span></span>  
  
##  <a name="attribute-relationships-and-cube-space"></a><a name="AttribRelationships"></a><span data-ttu-id="a9157-133">属性关系和多维数据集空间</span><span class="sxs-lookup"><span data-stu-id="a9157-133">Attribute Relationships and Cube Space</span></span>  
 <span data-ttu-id="a9157-134">定义相关属性间的属性关系（通过促进相应聚合的创建）将提高查询性能，并影响与属性层次结构成员一同显示的相关属性层次结构的成员。</span><span class="sxs-lookup"><span data-stu-id="a9157-134">Defining attribute relationships between related attributes improves query performance (by facilitating the creation of appropriate aggregations) and affects the member of a related attribute hierarchy that appears with an attribute hierarchy member.</span></span> <span data-ttu-id="a9157-135">例如，您定义了包含 City 属性层次结构的成员的元组并且该元组未显式定义 Country 属性层次结构成员时，您可能希望默认 Country 属性层次结构成员是 Country 属性层次结构的相关成员。</span><span class="sxs-lookup"><span data-stu-id="a9157-135">For example, when you define a tuple that includes a member from the City attribute hierarchy and the tuple does not explicitly define the Country attribute hierarchy member, you might expect that the default Country attribute hierarchy member would be the related member of the Country attribute hierarchy.</span></span> <span data-ttu-id="a9157-136">不过，只有定义了 City 属性层次结构和 Country 属性层次结构之间的属性关系时，才会出现上述预期结果。</span><span class="sxs-lookup"><span data-stu-id="a9157-136">However, this is only true if an attribute relationship is defined between the City attribute hierarchy and the Country attribute hierarchy.</span></span>  
  
 <span data-ttu-id="a9157-137">以下示例返回未显式包含在查询中的相关属性层次结构的成员。</span><span class="sxs-lookup"><span data-stu-id="a9157-137">The following example returns the member of a related attribute hierarchy that is not included explicitly in the query.</span></span>  
  
```  
WITH MEMBER Measures.x AS   
   Customer.Country.CurrentMember.Name  
SELECT Measures.x ON 0,  
Customer.City.Members ON 1  
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="a9157-138">请注意， `WITH` 关键字与[CURRENTMEMBER (mdx) ](/sql/mdx/current-mdx)和[名称 (mdx) ](/sql/mdx/members-string-mdx)函数一起使用，以创建用于查询的计算成员。</span><span class="sxs-lookup"><span data-stu-id="a9157-138">Notice that the `WITH` keyword is used with the [CurrentMember (MDX)](/sql/mdx/current-mdx) and [Name (MDX)](/sql/mdx/members-string-mdx) functions to create a calculated member for use in the query.</span></span> <span data-ttu-id="a9157-139">有关详细信息，请参阅[基本 MDX 查询 (MDX)](mdx-query-the-basic-query.md)。</span><span class="sxs-lookup"><span data-stu-id="a9157-139">For more information, see [The Basic MDX Query &#40;MDX&#41;](mdx-query-the-basic-query.md).</span></span>  
  
 <span data-ttu-id="a9157-140">在前面的查询中，返回了与 State 属性层次结构各成员相关联的 Country 属性层次结构的成员名称。</span><span class="sxs-lookup"><span data-stu-id="a9157-140">In the previous query, the name of the member of the Country attribute hierarchy that is associated with each member of the State attribute hierarchy is returned.</span></span> <span data-ttu-id="a9157-141">出现了预期的 Country 成员（因为定义了 City 和 Country 属性之间的属性关系）。</span><span class="sxs-lookup"><span data-stu-id="a9157-141">The expected Country member appears (because an attribute relationship is defined between the City and Country attributes).</span></span> <span data-ttu-id="a9157-142">不过，如果在同一维度中没有定义属性层次结构间的任何属性关系，将返回“(全部)”成员，如以下查询所示。</span><span class="sxs-lookup"><span data-stu-id="a9157-142">However, if no attribute relationship were defined between attribute hierarchies in the same dimension, the (All) member would be returned, as illustrated in the following query.</span></span>  
  
```  
WITH MEMBER Measures.x AS   
   Customer.Education.Currentmember.Name  
SELECT Measures.x  ON 0,   
Customer.City.Members ON 1  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="a9157-143">在前面的查询中，返回了“(全部)”成员（“All Customers”），因为 Education 和 City 间不存在任何关系。</span><span class="sxs-lookup"><span data-stu-id="a9157-143">In the previous query, the (All) member ("All Customers") is returned, because there is no relationship between Education and City.</span></span> <span data-ttu-id="a9157-144">因此，Education 属性层次结构的“(全部)”成员将是任何涉及 City 属性层次结构（未在其中显式提供 Education 成员）的元组中使用的 Education 属性层次结构的默认成员。</span><span class="sxs-lookup"><span data-stu-id="a9157-144">Therefore, the (All) member of the Education attribute hierarchy would be the default member of the Education attribute hierarchy used in any tuple involving the City attribute hierarchy where an Education member is not explicitly provided.</span></span>  
  
## <a name="calculation-context"></a><span data-ttu-id="a9157-145">计算上下文</span><span class="sxs-lookup"><span data-stu-id="a9157-145">Calculation Context</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9157-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a9157-146">See Also</span></span>  
 <span data-ttu-id="a9157-147">[MDX &#40;Analysis Services 中的关键概念&#41;](../key-concepts-in-mdx-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="a9157-147">[Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span></span>  
 <span data-ttu-id="a9157-148">[元](tuples.md) </span><span class="sxs-lookup"><span data-stu-id="a9157-148">[Tuples](tuples.md) </span></span>  
 <span data-ttu-id="a9157-149">[Autoexists](autoexists.md) </span><span class="sxs-lookup"><span data-stu-id="a9157-149">[Autoexists](autoexists.md) </span></span>  
 <span data-ttu-id="a9157-150">[使用成员、元组和集 &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="a9157-150">[Working with Members, Tuples, and Sets &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md) </span></span>  
 <span data-ttu-id="a9157-151">[直观合计和非直观合计](visual-totals-and-non-visual-totals.md) </span><span class="sxs-lookup"><span data-stu-id="a9157-151">[Visual Totals and Non Visual Totals](visual-totals-and-non-visual-totals.md) </span></span>  
 <span data-ttu-id="a9157-152">[Mdx 语言参考 &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="a9157-152">[MDX Language Reference &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span></span>  
 [<span data-ttu-id="a9157-153">多维表达式 (MDX) 参考</span><span class="sxs-lookup"><span data-stu-id="a9157-153">Multidimensional Expressions &#40;MDX&#41; Reference</span></span>](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
