---
title: 递归层次结构 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- recursive hierarchies [Master Data Services]
- hierarchies [Master Data Services], recursive hierarchies
ms.assetid: 9408c6ea-d9c4-4a0b-8a1b-1457fb6944af
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3c149d500ce1499ad36247d5e32bb6f2d55b4250
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590236"
---
# <a name="recursive-hierarchies-master-data-services"></a><span data-ttu-id="93a66-102">递归层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="93a66-102">Recursive Hierarchies (Master Data Services)</span></span>
  <span data-ttu-id="93a66-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，递归层次结构是包括递归关系的派生层次结构。</span><span class="sxs-lookup"><span data-stu-id="93a66-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a recursive hierarchy is a derived hierarchy that includes a recursive relationship.</span></span> <span data-ttu-id="93a66-104">在实体具有基于域的属性，且该属性基于实体本身时，存在递归关系。</span><span class="sxs-lookup"><span data-stu-id="93a66-104">A recursive relationship exists when an entity has a domain-based attribute based on the entity itself.</span></span>

## <a name="recursive-hierarchy-example"></a><span data-ttu-id="93a66-105">递归层次结构样本</span><span class="sxs-lookup"><span data-stu-id="93a66-105">Recursive Hierarchy Example</span></span>
 <span data-ttu-id="93a66-106">典型的递归层次结构样本是组织结构。</span><span class="sxs-lookup"><span data-stu-id="93a66-106">A typical recursive hierarchy example is an organizational structure.</span></span> <span data-ttu-id="93a66-107">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，可以通过创建一个 Employee 实体（该实体具有名为 Manager 的基于域的属性）来说明这一点。</span><span class="sxs-lookup"><span data-stu-id="93a66-107">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you would do this by creating an Employee entity with a domain-based attribute called Manager.</span></span> <span data-ttu-id="93a66-108">该 Manager 属性通过雇员列表填充。</span><span class="sxs-lookup"><span data-stu-id="93a66-108">The Manager attribute is populated from the list of employees.</span></span> <span data-ttu-id="93a66-109">在这个示例组织中，所有雇员都可以是经理。</span><span class="sxs-lookup"><span data-stu-id="93a66-109">In this sample organization, all employees can be managers.</span></span>

 <span data-ttu-id="93a66-110">![mds_conc_recursive_table_w_data](../../2014/master-data-services/media/mds-conc-recursive-table-w-data.gif "mds_conc_recursive_table_w_data")</span><span class="sxs-lookup"><span data-stu-id="93a66-110">![mds_conc_recursive_table_w_data](../../2014/master-data-services/media/mds-conc-recursive-table-w-data.gif "mds_conc_recursive_table_w_data")</span></span>

 <span data-ttu-id="93a66-111">您可以创建一个派生层次结构，该层次结构突出显示 Employee 实体和 Manager 基于域的属性之间的关系。</span><span class="sxs-lookup"><span data-stu-id="93a66-111">You can create a derived hierarchy that highlights the relationship between the Employee entity and the Manager domain-based attribute.</span></span>

 <span data-ttu-id="93a66-112">![mds_conc_recursive_UI_structure](../../2014/master-data-services/media/mds-conc-recursive-ui-structure.gif "mds_conc_recursive_UI_structure")</span><span class="sxs-lookup"><span data-stu-id="93a66-112">![mds_conc_recursive_UI_structure](../../2014/master-data-services/media/mds-conc-recursive-ui-structure.gif "mds_conc_recursive_UI_structure")</span></span>

 <span data-ttu-id="93a66-113">若要在层次结构中仅包括每个成员一次，您可以定位 Null 关系。</span><span class="sxs-lookup"><span data-stu-id="93a66-113">To include each member in the hierarchy only once, you can anchor null relationships.</span></span> <span data-ttu-id="93a66-114">在您进行定位时，具有空的基于域的属性值的成员显示在层次结构的顶级。</span><span class="sxs-lookup"><span data-stu-id="93a66-114">When you do, members with blank domain-based attribute values are displayed at the top level of the hierarchy.</span></span>

 <span data-ttu-id="93a66-115">![mds_conc_recursive_UI_example_anchored](../../2014/master-data-services/media/mds-conc-recursive-ui-example-anchored.gif "mds_conc_recursive_UI_example_anchored")</span><span class="sxs-lookup"><span data-stu-id="93a66-115">![mds_conc_recursive_UI_example_anchored](../../2014/master-data-services/media/mds-conc-recursive-ui-example-anchored.gif "mds_conc_recursive_UI_example_anchored")</span></span>

 <span data-ttu-id="93a66-116">如果没有定位 Null 关系，成员将包含多次。</span><span class="sxs-lookup"><span data-stu-id="93a66-116">If you do not anchor null relationships, members are included multiple times.</span></span> <span data-ttu-id="93a66-117">所有成员都显示在顶级。</span><span class="sxs-lookup"><span data-stu-id="93a66-117">All members are displayed at the top level.</span></span> <span data-ttu-id="93a66-118">它们还显示在自己是其属性的成员之下。</span><span class="sxs-lookup"><span data-stu-id="93a66-118">They are also displayed under members of which they are attributes.</span></span>

 <span data-ttu-id="93a66-119">![mds_conc_recursive_UI_example_nonanchored](../../2014/master-data-services/media/mds-conc-recursive-ui-example-nonanchored.gif "mds_conc_recursive_UI_example_nonanchored")</span><span class="sxs-lookup"><span data-stu-id="93a66-119">![mds_conc_recursive_UI_example_nonanchored](../../2014/master-data-services/media/mds-conc-recursive-ui-example-nonanchored.gif "mds_conc_recursive_UI_example_nonanchored")</span></span>

 <span data-ttu-id="93a66-120">在本示例中，Marcia 处于顶级。</span><span class="sxs-lookup"><span data-stu-id="93a66-120">In this example, Marcia is at the top level.</span></span> <span data-ttu-id="93a66-121">她不是任何雇员的经理，因为她未用作任何其他 Employee 成员的基于域的属性值。</span><span class="sxs-lookup"><span data-stu-id="93a66-121">She is not the manager of any employees because she is not used as a domain-based attribute value for any other Employee members.</span></span> <span data-ttu-id="93a66-122">而相反，Robert 在其下具有一个级别，因为 Marcia 将 Robert 作为其 Manager 属性值。</span><span class="sxs-lookup"><span data-stu-id="93a66-122">Robert, in contrast, has a level beneath him because Marcia has Robert as her Manager attribute value.</span></span>

## <a name="rules"></a><span data-ttu-id="93a66-123">规则</span><span class="sxs-lookup"><span data-stu-id="93a66-123">Rules</span></span>

-   <span data-ttu-id="93a66-124">派生层次结构不能包含多个递归关系。</span><span class="sxs-lookup"><span data-stu-id="93a66-124">A derived hierarchy cannot contain more than one recursive relationship.</span></span> <span data-ttu-id="93a66-125">但是，它可以具有其他派生关系（例如，包含“经理到雇员”递归关系的派生层次结构还可以具有“国家/地区到经理”关系和“雇员到商店”关系）。</span><span class="sxs-lookup"><span data-stu-id="93a66-125">It can, however, have other derived relationships (for example, a derived hierarchy that contains a recursive Manager to Employee relationship can also have Country to Manager and Employee to Store relationships).</span></span>

-   <span data-ttu-id="93a66-126">不能将成员权限（在“层次结构成员”\*\*\*\* 选项卡上）分配给递归层次结构中的成员。</span><span class="sxs-lookup"><span data-stu-id="93a66-126">You cannot assign member permissions (on the **Hierarchy Members** tab) to members in a recursive hierarchy.</span></span>

-   <span data-ttu-id="93a66-127">递归层次结构不能包括循环关系。</span><span class="sxs-lookup"><span data-stu-id="93a66-127">Recursive hierarchies cannot include circular relationships.</span></span> <span data-ttu-id="93a66-128">例如，如果 Sandeep 是 Katherine 的经理，则 Katherine 不能是 Sandeep 的经理。</span><span class="sxs-lookup"><span data-stu-id="93a66-128">For example, Katherine cannot be Sandeep's manager if Sandeep is her manager.</span></span> <span data-ttu-id="93a66-129">此外，Katherine 不能管理她自己。</span><span class="sxs-lookup"><span data-stu-id="93a66-129">Also, Katherine cannot manage herself.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="93a66-130">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="93a66-130">Related Tasks</span></span>

|<span data-ttu-id="93a66-131">任务说明</span><span class="sxs-lookup"><span data-stu-id="93a66-131">Task Description</span></span>|<span data-ttu-id="93a66-132">主题</span><span class="sxs-lookup"><span data-stu-id="93a66-132">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="93a66-133">创建派生层次结构。</span><span class="sxs-lookup"><span data-stu-id="93a66-133">Create a derived hierarchy.</span></span>|[<span data-ttu-id="93a66-134">创建派生层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="93a66-134">Create a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](create-a-derived-hierarchy-master-data-services.md)|
|<span data-ttu-id="93a66-135">更改现有派生层次结构的名称。</span><span class="sxs-lookup"><span data-stu-id="93a66-135">Change the name of an existing derived hierarchy.</span></span>|[<span data-ttu-id="93a66-136">更改派生层次结构名称 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="93a66-136">Change a Derived Hierarchy Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-derived-hierarchy-name-master-data-services.md)|
|<span data-ttu-id="93a66-137">删除现有派生层次结构。</span><span class="sxs-lookup"><span data-stu-id="93a66-137">Delete an existing derived hierarchy.</span></span>|[<span data-ttu-id="93a66-138">删除派生层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="93a66-138">Delete a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-derived-hierarchy-master-data-services.md)|

## <a name="related-content"></a><span data-ttu-id="93a66-139">相关内容</span><span class="sxs-lookup"><span data-stu-id="93a66-139">Related Content</span></span>

-   [<span data-ttu-id="93a66-140">基于域的属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="93a66-140">Domain-Based Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/domain-based-attributes-master-data-services.md)

-   [<span data-ttu-id="93a66-141">派生层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="93a66-141">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)


