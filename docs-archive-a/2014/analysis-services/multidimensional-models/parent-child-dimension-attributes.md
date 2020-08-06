---
title: 父子层次结构中的属性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data members [Analysis Services]
- nonleaf members
- MembersWithDataCaption property
- members [Analysis Services]
- members [Analysis Services], data
- leaf members
- parent-child dimensions [Analysis Services]
- MembersWithData property
ms.assetid: 249971cc-4bcd-44f1-8241-bdacc04d3d38
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5c4a7e8ba43ac8ede0bd60409f84a6fa233ce182
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689049"
---
# <a name="attributes-in-parent-child-hierarchies"></a><span data-ttu-id="d7df7-102">父子层次结构中的属性</span><span class="sxs-lookup"><span data-stu-id="d7df7-102">Attributes in Parent-Child Hierarchies</span></span>
  <span data-ttu-id="d7df7-103">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ，通常假设是对维度中成员的内容进行一般假设。</span><span class="sxs-lookup"><span data-stu-id="d7df7-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], a general assumption is usually made about the content of members in a dimension.</span></span> <span data-ttu-id="d7df7-104">叶成员包含直接派生自基础数据源的数据；非叶成员包含派生自对子成员所执行的聚合的数据。</span><span class="sxs-lookup"><span data-stu-id="d7df7-104">Leaf members contain data derived directly from underlying data sources; nonleaf members contain data derived from aggregations performed on child members.</span></span>  
  
 <span data-ttu-id="d7df7-105">但是在父子层次结构中，一些非叶成员除包含通过子成员聚合的数据外，还可能包含派生自基础数据源的数据。</span><span class="sxs-lookup"><span data-stu-id="d7df7-105">In a parent-child hierarchy, however, some nonleaf members may also have data derived from underlying data sources, in addition to data aggregated from child members.</span></span> <span data-ttu-id="d7df7-106">对于父子层次结构中的这些非叶成员，可创建包含基础事实数据表数据的系统生成的特殊子成员。</span><span class="sxs-lookup"><span data-stu-id="d7df7-106">For these nonleaf members in a parent-child hierarchy, special system-generated child members are created that contain the underlying fact table data.</span></span> <span data-ttu-id="d7df7-107">这些成员称为“数据成员 \*\*”，它们包含与非叶成员直接相关的值，而非叶成员独立于通过该非叶成员的后代计算的汇总值。</span><span class="sxs-lookup"><span data-stu-id="d7df7-107">Referred to as *data members*, they contain a value directly associated with a nonleaf member that is independent of the summary value calculated from the descendants of the nonleaf member.</span></span>  
  
 <span data-ttu-id="d7df7-108">数据成员仅可用于具有父子层次结构的维度，并且仅当父属性允许时才可见。</span><span class="sxs-lookup"><span data-stu-id="d7df7-108">Data members are available only to dimensions with parent-child hierarchies, and are visible only if allowed by the parent attribute.</span></span> <span data-ttu-id="d7df7-109">可以使用维度设计器来控制数据成员的可见性。</span><span class="sxs-lookup"><span data-stu-id="d7df7-109">You can use Dimension Designer to control the visibility of data members.</span></span> <span data-ttu-id="d7df7-110">若要公开数据成员，请将父特性的 `MembersWithData` 属性设置为 `NonLeafDataVisible.`。若要隐藏父特性所包含的数据成员，请将父特性的 `MembersWithData` 属性设置为 `NonLeafDataHidden`。</span><span class="sxs-lookup"><span data-stu-id="d7df7-110">To expose data members, set the `MembersWithData` property for the parent attribute to `NonLeafDataVisible.` To hide data members contained by the parent attribute, set the `MembersWithData` property on the parent attribute to `NonLeafDataHidden`.</span></span>  
  
 <span data-ttu-id="d7df7-111">此设置不会覆盖非叶成员的正常聚合行为；为了进行聚合，将始终包括作为子成员的数据成员。</span><span class="sxs-lookup"><span data-stu-id="d7df7-111">This setting does not override the normal aggregation behavior for nonleaf members; the data member is always included as a child member for the purposes of aggregation.</span></span> <span data-ttu-id="d7df7-112">但是，可以用自定义汇总公式来覆盖正常聚合行为。</span><span class="sxs-lookup"><span data-stu-id="d7df7-112">However, a custom rollup formula can be used to override the normal aggregation behavior.</span></span> <span data-ttu-id="d7df7-113">多维表达式 (MDX) [DataMember](/sql/mdx/datamember-mdx)函数使你能够访问关联数据成员的值，而不考虑属性的值 `MembersWithData` 。</span><span class="sxs-lookup"><span data-stu-id="d7df7-113">The Multidimensional Expressions (MDX) [DataMember](/sql/mdx/datamember-mdx) function gives you the ability to access the value of the associated data member regardless of the value of the `MembersWithData` property.</span></span>  
  
 <span data-ttu-id="d7df7-114">父特性的 `MembersWithDataCaption` 属性为 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 提供了用于生成数据成员名称的命名模板。</span><span class="sxs-lookup"><span data-stu-id="d7df7-114">The `MembersWithDataCaption` property of the parent attribute provides [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] with the naming template used to generate member names for data members.</span></span>  
  
## <a name="using-data-members"></a><span data-ttu-id="d7df7-115">使用数据成员</span><span class="sxs-lookup"><span data-stu-id="d7df7-115">Using Data Members</span></span>  
 <span data-ttu-id="d7df7-116">根据有父子层次结构的组织维度聚合度量值时，数据成员将非常有用。</span><span class="sxs-lookup"><span data-stu-id="d7df7-116">Data members are useful when aggregating measures along organizational dimensions that have parent-child hierarchies.</span></span> <span data-ttu-id="d7df7-117">例如，以下关系图显示了有三个级别的维度，用于表示产品的总销售量。</span><span class="sxs-lookup"><span data-stu-id="d7df7-117">For example, the following diagram shows a dimension that has three levels, representing the gross sales volume of products.</span></span> <span data-ttu-id="d7df7-118">第一个级别显示所有销售人员的总销售量。</span><span class="sxs-lookup"><span data-stu-id="d7df7-118">The first level shows the gross sales volume for all salespersons.</span></span> <span data-ttu-id="d7df7-119">第二个级别包括按销售经理分组的全体销售职员的总销售量，第三个级别包括按销售人员分组的全体销售职员的总销售量。</span><span class="sxs-lookup"><span data-stu-id="d7df7-119">The second level contains the gross sales volume for all sales staff grouped by sales manager, and the third level contains the gross sales volume for all sales staff grouped by salesperson.</span></span>  
  
 <span data-ttu-id="d7df7-120">![具有三个级别的总销售量维度](../media/agdatamember1.gif "具有三个级别的总销售量维度")</span><span class="sxs-lookup"><span data-stu-id="d7df7-120">![Gross sales volume dimension with three levels](../media/agdatamember1.gif "Gross sales volume dimension with three levels")</span></span>  
  
 <span data-ttu-id="d7df7-121">通常，销售经理 1 成员的值派生自 Salesperson 1 和 Salesperson 2 成员的聚合值。</span><span class="sxs-lookup"><span data-stu-id="d7df7-121">Ordinarily, the value of the Sales Manager 1 member would be derived by aggregating the values of the Salesperson 1 and Salesperson 2 members.</span></span> <span data-ttu-id="d7df7-122">但是，因为销售经理 1 也可销售产品，所以该成员也可能包含从事实数据表派生的数据，原因是其中可能存在与销售经理 1 相关的总销售额。</span><span class="sxs-lookup"><span data-stu-id="d7df7-122">However, because Sales Manager 1 also can sell products, that member may also contain data derived from the fact table, because there may be gross sales associated with Sales Manager 1.</span></span>  
  
 <span data-ttu-id="d7df7-123">此外，每个销售职员成员的个人佣金可能不同。</span><span class="sxs-lookup"><span data-stu-id="d7df7-123">Moreover, the individual commissions for each sales staff member can vary.</span></span> <span data-ttu-id="d7df7-124">在这种情况下，与其下属销售人员所产生的总销售额的合计相对比，将使用两种不同的计数法来计算销售经理的个人总销售额的佣金。</span><span class="sxs-lookup"><span data-stu-id="d7df7-124">In this case, two different scales are used to compute commissions for the individual gross sales of the sales managers, as opposed to the total of gross sales generated by their salespersons.</span></span> <span data-ttu-id="d7df7-125">因此，能够访问非叶成员的基础事实数据表数据非常重要。</span><span class="sxs-lookup"><span data-stu-id="d7df7-125">Therefore, it is important to be able to access the underlying fact table data for nonleaf members.</span></span> <span data-ttu-id="d7df7-126">MDX `DataMember` 函数可用来检索销售经理 1 成员的个人总销售量，并且自定义汇总表达式可用来将数据成员从销售经理 1 成员的聚合值中排除，从而提供与该成员相关的销售人员总销售量。</span><span class="sxs-lookup"><span data-stu-id="d7df7-126">The MDX `DataMember` function can be used to retrieve the individual gross sales volume of the Sales Manager 1 member, and a custom rollup expression can be used to exclude the data member from the aggregated value of the Sales Manager 1 member, providing the gross sales volume of the salespersons associated with that member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7df7-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d7df7-127">See Also</span></span>  
 <span data-ttu-id="d7df7-128">[维度特性属性参考](dimension-attribute-properties-reference.md) </span><span class="sxs-lookup"><span data-stu-id="d7df7-128">[Dimension Attribute Properties Reference](dimension-attribute-properties-reference.md) </span></span>  
 [<span data-ttu-id="d7df7-129">父子层次结构</span><span class="sxs-lookup"><span data-stu-id="d7df7-129">Parent-Child Hierarchy</span></span>](parent-child-dimension.md)  
  
  
