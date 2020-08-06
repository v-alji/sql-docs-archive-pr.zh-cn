---
title: 具有显式顶端的派生层次结构 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Master Data Services], derived hierarchies with explicit caps
- explicit hierarchies, derived hierarchies with explicit caps
- derived hierarchies, derived hierarchies with explicit caps
ms.assetid: 6a82ff66-c137-4757-99bb-787d189b4295
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d2460ddf098f0547c2876dd9689f5d2bf9b461a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578917"
---
# <a name="derived-hierarchies-with-explicit-caps-master-data-services"></a><span data-ttu-id="cc411-102">具有显式顶端的派生层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cc411-102">Derived Hierarchies with Explicit Caps (Master Data Services)</span></span>
  <span data-ttu-id="cc411-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，当来自显式层次结构的级别用作派生层次结构的顶级时，该级别称作具有显式顶端的派生层次结构。</span><span class="sxs-lookup"><span data-stu-id="cc411-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], when the levels from an explicit hierarchy are used as the top levels of a derived hierarchy, this is called a derived hierarchy with an explicit cap.</span></span>

 <span data-ttu-id="cc411-104">此显式层次结构必须基于与派生层次结构顶部的实体相同的实体。</span><span class="sxs-lookup"><span data-stu-id="cc411-104">The explicit hierarchy must be based on the same entity as the entity at the top of the derived hierarchy.</span></span>

 <span data-ttu-id="cc411-105">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 用户界面 (UI) 中，通过将显式层次结构拖到派生层次结构的顶部来创建此类型的层次结构。</span><span class="sxs-lookup"><span data-stu-id="cc411-105">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] user interface (UI), you create this type of hierarchy by dragging an explicit hierarchy to the top of a derived hierarchy.</span></span>

 <span data-ttu-id="cc411-106">![mds_conc_explicit_cap_UI_structure](../../2014/master-data-services/media/mds-conc-explicit-cap-ui-structure.gif "mds_conc_explicit_cap_UI_structure")</span><span class="sxs-lookup"><span data-stu-id="cc411-106">![mds_conc_explicit_cap_UI_structure](../../2014/master-data-services/media/mds-conc-explicit-cap-ui-structure.gif "mds_conc_explicit_cap_UI_structure")</span></span>

## <a name="derived-hierarchy-with-explicit-cap-example"></a><span data-ttu-id="cc411-107">具有显式顶端的派生层次结构示例</span><span class="sxs-lookup"><span data-stu-id="cc411-107">Derived Hierarchy with Explicit Cap Example</span></span>
 <span data-ttu-id="cc411-108">在此示例中，该显式层次结构中的成员来自 Subcategory 实体。</span><span class="sxs-lookup"><span data-stu-id="cc411-108">In this example, the members in the explicit hierarchy are from the Subcategory entity.</span></span> <span data-ttu-id="cc411-109">在派生层次结构中，顶级成员也来自 Subcategory 实体。</span><span class="sxs-lookup"><span data-stu-id="cc411-109">In the derived hierarchy, the top-level members are also from the Subcategory entity.</span></span>

 <span data-ttu-id="cc411-110">![mds_conc_explicit_cap_UI_example](../../2014/master-data-services/media/mds-conc-explicit-cap-ui-example.gif "mds_conc_explicit_cap_UI_example")</span><span class="sxs-lookup"><span data-stu-id="cc411-110">![mds_conc_explicit_cap_UI_example](../../2014/master-data-services/media/mds-conc-explicit-cap-ui-example.gif "mds_conc_explicit_cap_UI_example")</span></span>

 <span data-ttu-id="cc411-111">通过在某一派生层次结构的顶部使用显式层次结构，该派生层次结构将成为不规则层次结构。</span><span class="sxs-lookup"><span data-stu-id="cc411-111">By using the explicit hierarchy at the top of a derived hierarchy, the derived hierarchy becomes ragged.</span></span>

## <a name="rules"></a><span data-ttu-id="cc411-112">规则</span><span class="sxs-lookup"><span data-stu-id="cc411-112">Rules</span></span>

-   <span data-ttu-id="cc411-113">不能在具有显式顶端的派生层次结构中具有多个显式层次结构。</span><span class="sxs-lookup"><span data-stu-id="cc411-113">You cannot have more than one explicit hierarchy in a derived hierarchy with explicit cap.</span></span>

-   <span data-ttu-id="cc411-114">可以将相同的显式层次结构用作多个派生层次结构的顶端。</span><span class="sxs-lookup"><span data-stu-id="cc411-114">You can use the same explicit hierarchy as a cap for multiple derived hierarchies.</span></span>

-   <span data-ttu-id="cc411-115">不能将层次结构成员权限分配给具有显式顶端的派生层次结构。</span><span class="sxs-lookup"><span data-stu-id="cc411-115">You cannot assign hierarchy member permissions to derived hierarchies with explicit caps.</span></span> <span data-ttu-id="cc411-116">如果您单独将权限分配给显式层次结构或派生层次结构，则这些权限将影响这两种层次结构。</span><span class="sxs-lookup"><span data-stu-id="cc411-116">If you assign permissions to either the explicit hierarchy or the derived hierarchy individually, the permissions affect both hierarchies.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="cc411-117">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="cc411-117">Related Tasks</span></span>

|<span data-ttu-id="cc411-118">任务说明</span><span class="sxs-lookup"><span data-stu-id="cc411-118">Task Description</span></span>|<span data-ttu-id="cc411-119">主题</span><span class="sxs-lookup"><span data-stu-id="cc411-119">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="cc411-120">创建派生层次结构。</span><span class="sxs-lookup"><span data-stu-id="cc411-120">Create a derived hierarchy.</span></span>|[<span data-ttu-id="cc411-121">创建派生层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cc411-121">Create a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](create-a-derived-hierarchy-master-data-services.md)|
|<span data-ttu-id="cc411-122">创建显式层次结构。</span><span class="sxs-lookup"><span data-stu-id="cc411-122">Create an explicit hierarchy.</span></span>|[<span data-ttu-id="cc411-123">创建显式层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cc411-123">Create an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)|
|<span data-ttu-id="cc411-124">删除现有派生层次结构。</span><span class="sxs-lookup"><span data-stu-id="cc411-124">Delete an existing derived hierarchy.</span></span>|[<span data-ttu-id="cc411-125">删除派生层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cc411-125">Delete a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-derived-hierarchy-master-data-services.md)|
|||

## <a name="related-content"></a><span data-ttu-id="cc411-126">相关内容</span><span class="sxs-lookup"><span data-stu-id="cc411-126">Related Content</span></span>

-   [<span data-ttu-id="cc411-127">派生层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cc411-127">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)

-   [<span data-ttu-id="cc411-128">显式层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cc411-128">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)


