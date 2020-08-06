---
title: 配置属性层次结构的所有) 级别 (|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- All members
- IsAggregatable property
- topmost levels [Analysis Services]
- (All) levels
- AttributeAllMemberName property
- levels [Analysis Services]
- members [Analysis Services], All
- AllMemberName property
ms.assetid: 0cb35e6f-b10f-483d-b893-78f6ca3979fd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9874a8c8a6861bc7d9e44271b089e8af3a4c0ae2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689076"
---
# <a name="configure-the-all-level-for-attribute-hierarchies"></a><span data-ttu-id="563cf-102">配置属性层次结构的“(全部)”级别</span><span class="sxs-lookup"><span data-stu-id="563cf-102">Configure the (All) Level for Attribute Hierarchies</span></span>
  <span data-ttu-id="563cf-103">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ， (所有) 级别是一个系统生成的可选级别。</span><span class="sxs-lookup"><span data-stu-id="563cf-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the (All) level is an optional, system-generated level.</span></span> <span data-ttu-id="563cf-104">该级别只包含一个成员，该成员的值是直接从属级别中所有成员值的聚合。</span><span class="sxs-lookup"><span data-stu-id="563cf-104">It contains only one member whose value is the aggregation of the values of all members in the immediately subordinate level.</span></span> <span data-ttu-id="563cf-105">该成员称为“全部”成员。</span><span class="sxs-lookup"><span data-stu-id="563cf-105">This member is called the All member.</span></span> <span data-ttu-id="563cf-106">该成员是系统生成的成员，在维度表中不包含该成员。</span><span class="sxs-lookup"><span data-stu-id="563cf-106">It is a system-generated member that is not contained in the dimension table.</span></span> <span data-ttu-id="563cf-107">由于“(全部)”级别中的成员位于层次结构的顶层，因此成员的值是层次结构中所有成员值合并计算的聚合。</span><span class="sxs-lookup"><span data-stu-id="563cf-107">Because the member in the (All) level is at the top of the hierarchy, the member's value is the consolidated aggregation of the values of all members in the hierarchy.</span></span> <span data-ttu-id="563cf-108">“全部”成员通常作为层次结构的默认成员。</span><span class="sxs-lookup"><span data-stu-id="563cf-108">The All member often serves as the default member of a hierarchy.</span></span>  
  
 <span data-ttu-id="563cf-109">属性层次结构中是否存在“(全部)”级别取决于特性的 `IsAggregatable` 属性设置，用户定义层次结构中是否存在“(全部)”级别取决于用户定义层次结构最顶层级别的特性的 `IsAggregatable` 属性。</span><span class="sxs-lookup"><span data-stu-id="563cf-109">The presence of an (All) level in an attribute hierarchy depends on the `IsAggregatable` property setting for the attribute and the presence of an (All) level in a user-defined hierarchy depends on the `IsAggregatable` property of the attribute at the top-most level of user-defined hierarchy.</span></span> <span data-ttu-id="563cf-110">如果将 `IsAggregatable` 属性设置为 `True`，则会存在“(全部)”级别。</span><span class="sxs-lookup"><span data-stu-id="563cf-110">If the `IsAggregatable` property is set to `True`, an (All) level will exist.</span></span> <span data-ttu-id="563cf-111">如果将 `IsAggregatable` 属性设置为 `False`，则层次结构中没有“(全部)”级别。</span><span class="sxs-lookup"><span data-stu-id="563cf-111">A hierarchy has no (All) level if the `IsAggregatable` property is set to `False`.</span></span>  
  
## <a name="establishing-the-topmost-level"></a><span data-ttu-id="563cf-112">建立最顶层级别</span><span class="sxs-lookup"><span data-stu-id="563cf-112">Establishing the Topmost Level</span></span>  
 <span data-ttu-id="563cf-113">如果在层次结构中将某级别的源特性的 `IsAggregatable` 属性设置为 `False`，则该级别上面的层次结构中不会出现可聚合级别。</span><span class="sxs-lookup"><span data-stu-id="563cf-113">If the `IsAggregatable` property is set to `False` on the source attribute of a level in a hierarchy, then no aggregatable level can appear in the hierarchy above that level.</span></span> <span data-ttu-id="563cf-114">不可聚合的级别必须是任意层次结构的最顶层级别，或者该级别上面的所有级别的源特性的 `IsAggregatable` 属性必须也设置为 `False`。</span><span class="sxs-lookup"><span data-stu-id="563cf-114">A non-aggregatable level must be the topmost level of any hierarchy or the `IsAggregatable` property of the source attributes for any levels above it must also be set to `False`.</span></span>  
  
## <a name="all-member-and-all-level"></a><span data-ttu-id="563cf-115">“全部”成员和“(全部)”级别</span><span class="sxs-lookup"><span data-stu-id="563cf-115">All Member and (All) Level</span></span>  
 <span data-ttu-id="563cf-116">“(全部)”级别中的单个成员称为“全部”成员。</span><span class="sxs-lookup"><span data-stu-id="563cf-116">The single member of the (All) level is called the All member.</span></span> <span data-ttu-id="563cf-117">`AttributeAllMemberName`维度的属性指定维度中属性的 "全部" 成员的名称。</span><span class="sxs-lookup"><span data-stu-id="563cf-117">The `AttributeAllMemberName`property on a dimension specifies the name of the All member for attributes in a dimension.</span></span> <span data-ttu-id="563cf-118">层次结构的 `AllMemberName` 属性指定层次结构的“全部”成员的名称。</span><span class="sxs-lookup"><span data-stu-id="563cf-118">The `AllMemberName` property on a hierarchy specifies the name of the All member for the hierarchy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="563cf-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="563cf-119">See Also</span></span>  
 [<span data-ttu-id="563cf-120">定义默认成员</span><span class="sxs-lookup"><span data-stu-id="563cf-120">Define a Default Member</span></span>](attribute-properties-define-a-default-member.md)  
  
  
