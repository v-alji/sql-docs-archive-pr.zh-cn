---
title: 实体 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], about entities
- entities [Master Data Services]
ms.assetid: 0af057d5-6b73-472b-99eb-9f5eb61a9b5b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 220dfd87622f2f976070279dd44bd0732917f952
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682905"
---
# <a name="entities-master-data-services"></a><span data-ttu-id="f1381-102">实体 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f1381-102">Entities (Master Data Services)</span></span>
  <span data-ttu-id="f1381-103">实体是 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 模型中包含的对象。</span><span class="sxs-lookup"><span data-stu-id="f1381-103">Entities are objects that are contained in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] models.</span></span> <span data-ttu-id="f1381-104">每个实体都包含成员，它们是您管理的主数据的行。</span><span class="sxs-lookup"><span data-stu-id="f1381-104">Each entity contains members, which are the rows of master data that you manage.</span></span>  
  
## <a name="how-many-entities-are-appropriate"></a><span data-ttu-id="f1381-105">多少实体比较合适？</span><span class="sxs-lookup"><span data-stu-id="f1381-105">How Many Entities are Appropriate?</span></span>  
 <span data-ttu-id="f1381-106">模型可以包含想要管理的任意多个实体。</span><span class="sxs-lookup"><span data-stu-id="f1381-106">Models can contain as many entities as you want to manage.</span></span> <span data-ttu-id="f1381-107">每个实体应将相似类型的数据分组。</span><span class="sxs-lookup"><span data-stu-id="f1381-107">Each entity should group a similar kind of data.</span></span> <span data-ttu-id="f1381-108">例如，您可能希望将一个实体用于您的所有公司帐户，或将一个实体用于雇员的主列表。</span><span class="sxs-lookup"><span data-stu-id="f1381-108">For example, you might want an entity for all of your corporate accounts, or an entity for your master list of employees.</span></span>  
  
 <span data-ttu-id="f1381-109">通常，有一个或多个中心实体对于您的业务非常重要，它们与模型中的其他对象关联。</span><span class="sxs-lookup"><span data-stu-id="f1381-109">Typically, there are one or more central entities that are important to your business, and to which other objects in the model relate.</span></span> <span data-ttu-id="f1381-110">例如，在 Product 模型中，可能有一个名为 Product 的中心实体和与 Product 实体关联的名为 Subcategory 和 Category 的实体。</span><span class="sxs-lookup"><span data-stu-id="f1381-110">For example, in a Product model, you could have a central entity called Product and entities called Subcategory and Category that relate to the Product entity.</span></span> <span data-ttu-id="f1381-111">但是，您不需要一定有中心实体。</span><span class="sxs-lookup"><span data-stu-id="f1381-111">However, you do not need to have a central entity.</span></span> <span data-ttu-id="f1381-112">根据您的需要，可能希望有几个同等重要的实体。</span><span class="sxs-lookup"><span data-stu-id="f1381-112">Depending on your needs, you might have several entities that you consider to be of equal importance.</span></span>  
  
## <a name="how-entities-relate-to-other-model-objects"></a><span data-ttu-id="f1381-113">实体如何与其他模型对象关联</span><span class="sxs-lookup"><span data-stu-id="f1381-113">How Entities Relate to Other Model Objects</span></span>  
 <span data-ttu-id="f1381-114">您可以将实体看作包含主数据的一个表，其中行表示成员，列表示属性。</span><span class="sxs-lookup"><span data-stu-id="f1381-114">You can think of an entity as a table that contains master data, where the rows represent members and the columns represent attributes.</span></span>  
  
 <span data-ttu-id="f1381-115">![表示为表的 Master Data Services 实体](../../2014/master-data-services/media/mds-conc-entity-table.gif "表示为表的 Master Data Services 实体")</span><span class="sxs-lookup"><span data-stu-id="f1381-115">![Master Data Services Entity Represented as Table](../../2014/master-data-services/media/mds-conc-entity-table.gif "Master Data Services Entity Represented as Table")</span></span>  
  
 <span data-ttu-id="f1381-116">使用要管理的主数据的列表填充该实体。</span><span class="sxs-lookup"><span data-stu-id="f1381-116">You populate the entity with a list of master data that you want to manage.</span></span>  
  
 <span data-ttu-id="f1381-117">实体可用于生成派生层次结构，它们是基于多个实体的基于级别的层次结构。</span><span class="sxs-lookup"><span data-stu-id="f1381-117">Entities can be used to build derived hierarchies, which are level-based hierarchies based on multiple entities.</span></span> <span data-ttu-id="f1381-118">有关详细信息，请参阅 [派生层次结构 (Master Data Services)](derived-hierarchies-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f1381-118">For more information, see [Derived Hierarchies &#40;Master Data Services&#41;](derived-hierarchies-master-data-services.md).</span></span>  
  
 <span data-ttu-id="f1381-119">还允许实体包含显示层次结构（基于单个实体的不规则结构）和集合（成员子集的一次性组合）。</span><span class="sxs-lookup"><span data-stu-id="f1381-119">Entities can also be enabled to contain explicit hierarchies (ragged structures based on a single entity) and collections (one-off combinations of subsets of members).</span></span> <span data-ttu-id="f1381-120">有关详细信息，请参阅[显式层次结构 (Master Data Services)](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) 和[集合 (Master Data Services)](../../2014/master-data-services/collections-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f1381-120">For more information, see [Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) and [Collections &#40;Master Data Services&#41;](../../2014/master-data-services/collections-master-data-services.md).</span></span>  
  
## <a name="using-entities-as-constrained-lists"></a><span data-ttu-id="f1381-121">将实体用作受限制列表</span><span class="sxs-lookup"><span data-stu-id="f1381-121">Using Entities as Constrained Lists</span></span>  
 <span data-ttu-id="f1381-122">用户将属性分配给实体中的成员时，可以从值的受限制列表中选择它们。</span><span class="sxs-lookup"><span data-stu-id="f1381-122">When users are assigning attributes to the members in an entity, you can have them choose from a constrained list of values.</span></span> <span data-ttu-id="f1381-123">为此，您使用一个实体来填充该属性的值列表。</span><span class="sxs-lookup"><span data-stu-id="f1381-123">To do this, you use an entity to populate the list of values for the attribute.</span></span> <span data-ttu-id="f1381-124">这称为基于域的属性。</span><span class="sxs-lookup"><span data-stu-id="f1381-124">This is called a domain-based attribute.</span></span> <span data-ttu-id="f1381-125">有关详细信息，请参阅 [基于域的属性 (Master Data Services)](../../2014/master-data-services/domain-based-attributes-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f1381-125">For more information, see [Domain-Based Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md).</span></span>  
  
## <a name="base-entities"></a><span data-ttu-id="f1381-126">基实体</span><span class="sxs-lookup"><span data-stu-id="f1381-126">Base Entities</span></span>  
 <span data-ttu-id="f1381-127">在模型中浏览对象时，基实体是用户的起始点。</span><span class="sxs-lookup"><span data-stu-id="f1381-127">A base entity is a starting point for users when navigating objects in the model.</span></span> <span data-ttu-id="f1381-128">基实体确定当用户打开 **“资源管理器”** 功能区域并单击菜单栏上的 **“资源管理器”** 时屏幕的布局。</span><span class="sxs-lookup"><span data-stu-id="f1381-128">A base entity determines the layout of the screen when a user opens the **Explorer** functional area and clicks **Explorer** on the menu bar.</span></span> <span data-ttu-id="f1381-129">要将实体指定为基实体，请导航到 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="f1381-129">To specify an entity as a base entity, navigate to the **System Administration** functional area.</span></span> <span data-ttu-id="f1381-130">在 **“模型视图”** 页中，将实体从右侧的树控件拖到左侧树控件中的模型名称。</span><span class="sxs-lookup"><span data-stu-id="f1381-130">On the **Model View** page, drag the entity from the tree control on the right to the name of the model in the tree control on the left.</span></span>  
  
## <a name="entity-security"></a><span data-ttu-id="f1381-131">实体安全性</span><span class="sxs-lookup"><span data-stu-id="f1381-131">Entity Security</span></span>  
 <span data-ttu-id="f1381-132">可以授予用户对实体（包括相关模型对象）的权限。</span><span class="sxs-lookup"><span data-stu-id="f1381-132">You can give users permission to an entity, which includes related model objects.</span></span> <span data-ttu-id="f1381-133">有关详细信息，请参阅[实体权限 (Master Data Services)](../../2014/master-data-services/entity-permissions-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f1381-133">For more information, see [Entity Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/entity-permissions-master-data-services.md).</span></span>  
  
## <a name="entity-examples"></a><span data-ttu-id="f1381-134">实体示例</span><span class="sxs-lookup"><span data-stu-id="f1381-134">Entity Examples</span></span>  
 <span data-ttu-id="f1381-135">在下面的示例中，显示具有以下属性的实体：Name、Code、Subcategory、StandardCost、ListPrice 和 FilePhoto。</span><span class="sxs-lookup"><span data-stu-id="f1381-135">The following example shows an entity that has these attributes: Name, Code, Subcategory, StandardCost, ListPrice, and FilePhoto.</span></span> <span data-ttu-id="f1381-136">这些属性描述成员。</span><span class="sxs-lookup"><span data-stu-id="f1381-136">These attributes describe the members.</span></span> <span data-ttu-id="f1381-137">每个成员由一行属性值表示。</span><span class="sxs-lookup"><span data-stu-id="f1381-137">Each member is represented by a single row of attribute values.</span></span>  
  
 <span data-ttu-id="f1381-138">![自行车产品实体表](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "自行车产品实体表")</span><span class="sxs-lookup"><span data-stu-id="f1381-138">![Bike Product Entity Table](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "Bike Product Entity Table")</span></span>  
  
 <span data-ttu-id="f1381-139">在下面的示例中，Product 实体是中心实体。</span><span class="sxs-lookup"><span data-stu-id="f1381-139">In the following example, the Product entity is the central entity.</span></span> <span data-ttu-id="f1381-140">Subcategory 实体是 Product 实体的基于域的属性。</span><span class="sxs-lookup"><span data-stu-id="f1381-140">The Subcategory entity is a domain-based attribute of the Product entity.</span></span> <span data-ttu-id="f1381-141">Category 实体是 Subcategory 实体的基于域的属性。</span><span class="sxs-lookup"><span data-stu-id="f1381-141">The Category entity is a domain-based attribute of the Subcategory entity.</span></span> <span data-ttu-id="f1381-142">StandardCost 和 ListPrice 是 Product 实体的自由格式的属性，FilePhoto 是 Product 实体的文件属性。</span><span class="sxs-lookup"><span data-stu-id="f1381-142">StandardCost and ListPrice are free-form attributes of the Product entity, and FilePhoto is a file attribute of the Product entity.</span></span>  
  
 <span data-ttu-id="f1381-143">![产品实体树结构](../../2014/master-data-services/media/mds-conc-entity-ui.gif "产品实体树结构")</span><span class="sxs-lookup"><span data-stu-id="f1381-143">![Product Entity Tree Structure](../../2014/master-data-services/media/mds-conc-entity-ui.gif "Product Entity Tree Structure")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f1381-144">这是基于 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 用户界面 (UI) 的一个示例。</span><span class="sxs-lookup"><span data-stu-id="f1381-144">This is an example based on the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] user interface (UI).</span></span> <span data-ttu-id="f1381-145">树状层次结构显示实体和基于域的属性之间的关系。</span><span class="sxs-lookup"><span data-stu-id="f1381-145">The hierarchical tree structure shows relationships between entities and domain-based attributes.</span></span> <span data-ttu-id="f1381-146">它旨在显示关系而不是表示重要性级别。</span><span class="sxs-lookup"><span data-stu-id="f1381-146">It is intended to show relationships rather than represent levels of importance.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="f1381-147">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="f1381-147">Related Tasks</span></span>  
  
|<span data-ttu-id="f1381-148">任务说明</span><span class="sxs-lookup"><span data-stu-id="f1381-148">Task Description</span></span>|<span data-ttu-id="f1381-149">主题</span><span class="sxs-lookup"><span data-stu-id="f1381-149">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="f1381-150">创建新实体。</span><span class="sxs-lookup"><span data-stu-id="f1381-150">Create a new entity.</span></span>|[<span data-ttu-id="f1381-151">创建实体 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f1381-151">Create an Entity &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-entity-master-data-services.md)|  
|<span data-ttu-id="f1381-152">指定一个实体可以包含显式层次结构和集合。</span><span class="sxs-lookup"><span data-stu-id="f1381-152">Specify that an entity can contain explicit hierarchies and collections.</span></span>|[<span data-ttu-id="f1381-153">为显式层次结构和集合启用实体 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f1381-153">Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)|  
|<span data-ttu-id="f1381-154">更改现有实体的名称。</span><span class="sxs-lookup"><span data-stu-id="f1381-154">Change the name of an existing entity.</span></span>|[<span data-ttu-id="f1381-155">更改实体名称 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f1381-155">Change an Entity Name &#40;Master Data Services&#41;</span></span>](edit-an-entity-master-data-services.md)|  
|<span data-ttu-id="f1381-156">删除现有实体。</span><span class="sxs-lookup"><span data-stu-id="f1381-156">Delete an existing entity.</span></span>|[<span data-ttu-id="f1381-157">删除实体 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f1381-157">Delete an Entity &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-entity-master-data-services.md)|  
|<span data-ttu-id="f1381-158">将权限分配给实体。</span><span class="sxs-lookup"><span data-stu-id="f1381-158">Assign permission to entities.</span></span>|[<span data-ttu-id="f1381-159">分配模型对象权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f1381-159">Assign Model Object Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="f1381-160">相关内容</span><span class="sxs-lookup"><span data-stu-id="f1381-160">Related Content</span></span>  
  
-   [<span data-ttu-id="f1381-161">模型 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f1381-161">Models &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/models-master-data-services.md)  
  
-   [<span data-ttu-id="f1381-162">成员 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f1381-162">Members &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/members-master-data-services.md)  
  
-   [<span data-ttu-id="f1381-163">属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f1381-163">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
