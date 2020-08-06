---
title: 创建用户定义的层次结构 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- user-defined hierarchies [Analysis Services]
ms.assetid: 16715b85-0630-4a8e-99b0-c0d213cade26
author: minewiskan
ms.author: owend
ms.openlocfilehash: 17e870a2b20125132342db1845689b7c2481d623
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689619"
---
# <a name="create-user-defined-hierarchies"></a><span data-ttu-id="6af62-102">创建用户定义层次结构</span><span class="sxs-lookup"><span data-stu-id="6af62-102">Create User-Defined Hierarchies</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="6af62-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]允许您创建用户定义的层次结构。</span><span class="sxs-lookup"><span data-stu-id="6af62-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] lets you create user-defined hierarchies.</span></span> <span data-ttu-id="6af62-104">层次结构是基于属性的级别集合。</span><span class="sxs-lookup"><span data-stu-id="6af62-104">A hierarchy is a collection of levels based on attributes.</span></span> <span data-ttu-id="6af62-105">例如，时间层次结构可能包含年、季、月、周和日级别。</span><span class="sxs-lookup"><span data-stu-id="6af62-105">For example, a time hierarchy might contain the Year, Quarter, Month, Week, and Day levels.</span></span> <span data-ttu-id="6af62-106">在某些层次结构中，每个成员属性唯一对应于它上面的成员属性。</span><span class="sxs-lookup"><span data-stu-id="6af62-106">In some hierarchies, each member attribute uniquely implies the member attribute above it.</span></span> <span data-ttu-id="6af62-107">这有时也称为自然层次结构。</span><span class="sxs-lookup"><span data-stu-id="6af62-107">This is sometimes referred to as a natural hierarchy.</span></span> <span data-ttu-id="6af62-108">最终用户可使用层次结构来浏览多维数据集数据。</span><span class="sxs-lookup"><span data-stu-id="6af62-108">A hierarchy can be used by end users to browse cube data.</span></span> <span data-ttu-id="6af62-109">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，可使用维度设计器的“层次结构”窗格定义层次结构。</span><span class="sxs-lookup"><span data-stu-id="6af62-109">Define hierarchies by using the Hierarchies pane of Dimension Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="6af62-110">创建用户定义的层次结构时，该层次结构可能是 *不规则*的。</span><span class="sxs-lookup"><span data-stu-id="6af62-110">When you create a user-defined hierarchy, the hierarchy might become *ragged*.</span></span> <span data-ttu-id="6af62-111">在不规则层次结构中，至少一个成员的逻辑父成员不在该成员的直接上一级中。</span><span class="sxs-lookup"><span data-stu-id="6af62-111">A ragged hierarchy is where the logical parent member of at least one member is not in the level immediately above the member.</span></span> <span data-ttu-id="6af62-112">层次结构不规则时，可使用一些设置控制缺少的成员是否可见以及如何显示这些缺少的成员。</span><span class="sxs-lookup"><span data-stu-id="6af62-112">If you have a ragged hierarchy, there are settings that control whether the missing members are visible and how to display the missing members.</span></span> <span data-ttu-id="6af62-113">有关详细信息，请参阅 [不规则层次结构](user-defined-hierarchies-ragged-hierarchies.md)。</span><span class="sxs-lookup"><span data-stu-id="6af62-113">For more information, see [Ragged Hierarchies](user-defined-hierarchies-ragged-hierarchies.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6af62-114">有关与设计和配置用户定义的层次结构相关的性能问题的详细信息，请参阅 [SQL Server 2005 Analysis Services 性能指南](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide)。</span><span class="sxs-lookup"><span data-stu-id="6af62-114">For more information about performance issues related to the design and configuration of user-defined hierarchies, see the [SQL Server 2005 Analysis Services Performance Guide](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6af62-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6af62-115">See Also</span></span>  
 <span data-ttu-id="6af62-116">[用户层次结构属性](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md) </span><span class="sxs-lookup"><span data-stu-id="6af62-116">[User Hierarchy Properties](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md) </span></span>  
 <span data-ttu-id="6af62-117">[级别属性 &#91;Paved Over&#93;](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md) </span><span class="sxs-lookup"><span data-stu-id="6af62-117">[Level Properties &#91;Paved Over&#93;](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md) </span></span>  
 [<span data-ttu-id="6af62-118">父子层次结构</span><span class="sxs-lookup"><span data-stu-id="6af62-118">Parent-Child Hierarchy</span></span>](parent-child-dimension.md)  
  
  
