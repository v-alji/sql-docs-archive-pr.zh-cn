---
title: 模型 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], about models
- models [Master Data Services]
ms.assetid: 9f862a3d-25ab-41e9-b833-1db99959e825
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1d5a4a431d3ca7b6fa499de68a2bc4c5033cd086
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590873"
---
# <a name="models-master-data-services"></a><span data-ttu-id="374aa-102">模型 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="374aa-102">Models (Master Data Services)</span></span>
  <span data-ttu-id="374aa-103">模型是 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中最高级别的数据组织。</span><span class="sxs-lookup"><span data-stu-id="374aa-103">Models are the highest level of data organization in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span></span> <span data-ttu-id="374aa-104">模型定义了您的主数据管理解决方案中的数据结构。</span><span class="sxs-lookup"><span data-stu-id="374aa-104">A model defines the structure of data in your master data management solution.</span></span> <span data-ttu-id="374aa-105">模型包含以下对象：</span><span class="sxs-lookup"><span data-stu-id="374aa-105">A model contains the following objects:</span></span>  
  
-   <span data-ttu-id="374aa-106">实体</span><span class="sxs-lookup"><span data-stu-id="374aa-106">Entities</span></span>  
  
-   <span data-ttu-id="374aa-107">属性和属性组</span><span class="sxs-lookup"><span data-stu-id="374aa-107">Attributes and attribute groups</span></span>  
  
-   <span data-ttu-id="374aa-108">显式层次结构和派生层次结构</span><span class="sxs-lookup"><span data-stu-id="374aa-108">Explicit and derived hierarchies</span></span>  
  
-   <span data-ttu-id="374aa-109">集合</span><span class="sxs-lookup"><span data-stu-id="374aa-109">Collections</span></span>  
  
 <span data-ttu-id="374aa-110">模型组织您的主数据的结构。</span><span class="sxs-lookup"><span data-stu-id="374aa-110">Models organize the structure of your master data.</span></span> <span data-ttu-id="374aa-111">你的 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 实现可能有一个或多个模型，每个模型都会将相似类型的数据组合在一起。</span><span class="sxs-lookup"><span data-stu-id="374aa-111">Your [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] implementation can have one or many models that each group similar kinds of data.</span></span> <span data-ttu-id="374aa-112">通常，可通过以下四种方式之一划分主数据：人员、地点、事件或概念。</span><span class="sxs-lookup"><span data-stu-id="374aa-112">In general, master data can be categorized in one of four ways: people, places, things, or concepts.</span></span> <span data-ttu-id="374aa-113">例如，可以创建 Product 模型来包含与产品有关的数据，或创建 Customer 模型来包含与客户有关的数据。</span><span class="sxs-lookup"><span data-stu-id="374aa-113">For example, you can create a Product model to contain product-related data or a Customer model to contain customer-related data.</span></span>  
  
 <span data-ttu-id="374aa-114">可以分配用户和组权限来查看和更新模型中的对象。</span><span class="sxs-lookup"><span data-stu-id="374aa-114">You can assign users and groups permission to view and update objects within the model.</span></span> <span data-ttu-id="374aa-115">如果您不授予对模型的权限，则它不显示。</span><span class="sxs-lookup"><span data-stu-id="374aa-115">If you do not give permission to the model, it is not displayed.</span></span>  
  
 <span data-ttu-id="374aa-116">您随时都可以创建模型中主数据的副本。</span><span class="sxs-lookup"><span data-stu-id="374aa-116">At any given time, you can create copies of the master data within a model.</span></span> <span data-ttu-id="374aa-117">这些副本称为版本。</span><span class="sxs-lookup"><span data-stu-id="374aa-117">These copies are called versions.</span></span>  
  
 <span data-ttu-id="374aa-118">在测试环境中定义一个模型后，可以带或不带相应数据将它从测试环境部署到生产环境。</span><span class="sxs-lookup"><span data-stu-id="374aa-118">When you have defined a model in a test environment, you can deploy it, with or without the corresponding data, from the test environment to a production environment.</span></span> <span data-ttu-id="374aa-119">这样就不必在生产环境中重新创建您的模型。</span><span class="sxs-lookup"><span data-stu-id="374aa-119">This eliminates the need to recreate your models in your production environment.</span></span>  
  
## <a name="how-models-relate-to-other-objects"></a><span data-ttu-id="374aa-120">模型如何与其他对象关联</span><span class="sxs-lookup"><span data-stu-id="374aa-120">How Models Relate to Other Objects</span></span>  
 <span data-ttu-id="374aa-121">模型包含实体。</span><span class="sxs-lookup"><span data-stu-id="374aa-121">A model contains entities.</span></span> <span data-ttu-id="374aa-122">实体包含属性、显式层次结构和集合。</span><span class="sxs-lookup"><span data-stu-id="374aa-122">Entities contain attributes, explicit hierarchies, and collections.</span></span> <span data-ttu-id="374aa-123">属性可以包含在属性组中。</span><span class="sxs-lookup"><span data-stu-id="374aa-123">Attributes can be contained in attribute groups.</span></span> <span data-ttu-id="374aa-124">在某一实体用作其他实体的属性时，存在基于域的属性。</span><span class="sxs-lookup"><span data-stu-id="374aa-124">Domain-based attributes exist when an entity is used as an attribute for another entity.</span></span>  
  
 <span data-ttu-id="374aa-125">下图显示模型中对象之间的关系。</span><span class="sxs-lookup"><span data-stu-id="374aa-125">This image shows the relationships among the objects in a model.</span></span>  
  
 <span data-ttu-id="374aa-126">![Master Data Services 模型中的对象](../../2014/master-data-services/media/mds-conc-model-circles.gif "Master Data Services 模型中的对象")</span><span class="sxs-lookup"><span data-stu-id="374aa-126">![Objects in a Master Data Services Model](../../2014/master-data-services/media/mds-conc-model-circles.gif "Objects in a Master Data Services Model")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="374aa-127">派生层次结构也是模型对象，但它们不显示在图像中。</span><span class="sxs-lookup"><span data-stu-id="374aa-127">Derived hierarchies are also model objects, but they are not shown in the image.</span></span> <span data-ttu-id="374aa-128">派生层次结构从在实体之间存在的基于域的属性关系中派生。</span><span class="sxs-lookup"><span data-stu-id="374aa-128">Derived hierarchies are derived from the domain-based attribute relationships that exist between entities.</span></span> <span data-ttu-id="374aa-129">有关详细信息，请参阅[派生层次结构 &#40;Master Data Services&#41;](derived-hierarchies-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="374aa-129">See [Derived Hierarchies &#40;Master Data Services&#41;](derived-hierarchies-master-data-services.md) for more information.</span></span>  
  
 <span data-ttu-id="374aa-130">主数据是在模型对象中包含的数据。</span><span class="sxs-lookup"><span data-stu-id="374aa-130">Master data is the data that is contained in the model objects.</span></span> <span data-ttu-id="374aa-131">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，主数据作为实体中的成员存储。</span><span class="sxs-lookup"><span data-stu-id="374aa-131">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], master data is stored as members in an entity.</span></span>  
  
 <span data-ttu-id="374aa-132">模型对象在 **用户界面的** “系统管理” [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 功能区域中维护。</span><span class="sxs-lookup"><span data-stu-id="374aa-132">Model objects are maintained in the **System Administration** functional area of the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] user interface.</span></span>  
  
## <a name="model-example"></a><span data-ttu-id="374aa-133">模型示例</span><span class="sxs-lookup"><span data-stu-id="374aa-133">Model Example</span></span>  
 <span data-ttu-id="374aa-134">在下面的示例中，Product 模型中的对象以逻辑方式对与产品相关的数据进行分组。</span><span class="sxs-lookup"><span data-stu-id="374aa-134">In the following example, the objects in the Product model logically group product-related data.</span></span>  
  
 <span data-ttu-id="374aa-135">![产品模型主数据示例](../../2014/master-data-services/media/mds-conc-model.gif "产品模型主数据示例")</span><span class="sxs-lookup"><span data-stu-id="374aa-135">![Product Model Master Data Example](../../2014/master-data-services/media/mds-conc-model.gif "Product Model Master Data Example")</span></span>  
  
 <span data-ttu-id="374aa-136">其他常见的模型有：</span><span class="sxs-lookup"><span data-stu-id="374aa-136">Other common models are:</span></span>  
  
-   <span data-ttu-id="374aa-137">科目，它可能包含资产负债表科目、损益表科目、统计信息和科目类型等实体。</span><span class="sxs-lookup"><span data-stu-id="374aa-137">Accounts, which could include entities such as balance sheet accounts, income statement accounts, statistics, and account type.</span></span>  
  
-   <span data-ttu-id="374aa-138">客户，它可能包含性别、教育、职业和婚姻状况等实体。</span><span class="sxs-lookup"><span data-stu-id="374aa-138">Customer, which could include entities such as gender, education, occupation, and marital status.</span></span>  
  
-   <span data-ttu-id="374aa-139">地理信息，它可能包含邮政编码、城市、县、州、省、区域、国家/地区和洲等实体。</span><span class="sxs-lookup"><span data-stu-id="374aa-139">Geography, which could include entities such as postal codes, cities, counties, states, provinces, regions, territories, countries, and continents.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="374aa-140">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="374aa-140">Related Tasks</span></span>  
  
|<span data-ttu-id="374aa-141">任务说明</span><span class="sxs-lookup"><span data-stu-id="374aa-141">Task Description</span></span>|<span data-ttu-id="374aa-142">主题</span><span class="sxs-lookup"><span data-stu-id="374aa-142">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="374aa-143">创建模型来组织您的主数据。</span><span class="sxs-lookup"><span data-stu-id="374aa-143">Create a model to organize your master data.</span></span>|[<span data-ttu-id="374aa-144">创建模型 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="374aa-144">Create a Model &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-model-master-data-services.md)|  
|<span data-ttu-id="374aa-145">更改现有模型的名称。</span><span class="sxs-lookup"><span data-stu-id="374aa-145">Change the name of an existing model.</span></span>|[<span data-ttu-id="374aa-146">更改模型名称 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="374aa-146">Change a Model Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-model-name-master-data-services.md)|  
|<span data-ttu-id="374aa-147">删除现有模型。</span><span class="sxs-lookup"><span data-stu-id="374aa-147">Delete an existing model.</span></span>|[<span data-ttu-id="374aa-148">删除模型 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="374aa-148">Delete a Model &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-model-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="374aa-149">相关内容</span><span class="sxs-lookup"><span data-stu-id="374aa-149">Related Content</span></span>  
  
-   [<span data-ttu-id="374aa-150">Master Data Services 概述</span><span class="sxs-lookup"><span data-stu-id="374aa-150">Master Data Services Overview</span></span>](master-data-services-overview-mds.md)  
  
-   [<span data-ttu-id="374aa-151">实体 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="374aa-151">Entities &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/entities-master-data-services.md)  
  
-   [<span data-ttu-id="374aa-152">属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="374aa-152">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)  
  
-   [<span data-ttu-id="374aa-153">部署模型 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="374aa-153">Deploying Models &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
-   [<span data-ttu-id="374aa-154">模型对象权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="374aa-154">Model Object Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/model-object-permissions-master-data-services.md)  
  
  
