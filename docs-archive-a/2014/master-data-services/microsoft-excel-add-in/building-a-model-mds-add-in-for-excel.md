---
title: 生成模型 (MDS Add-in for Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 8ae26ec3-c5d5-4c4f-a810-2951a7454439
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f509fb81711d0eda5318fa2525e7f6e9e23485ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688975"
---
# <a name="building-a-model-mds-add-in-for-excel"></a><span data-ttu-id="b3527-102">生成模型（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="b3527-102">Building a Model (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="b3527-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，管理员可以执行在 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 应用程序中提供的一部分管理功能。</span><span class="sxs-lookup"><span data-stu-id="b3527-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], administrators can perform a subset of the administrative functions available in the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span>  
  
 <span data-ttu-id="b3527-104">管理员可以在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 中执行的模型生成任务是：</span><span class="sxs-lookup"><span data-stu-id="b3527-104">The model building tasks administrators can do in the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] are:</span></span>  
  
-   <span data-ttu-id="b3527-105">创建实体。</span><span class="sxs-lookup"><span data-stu-id="b3527-105">Create entities.</span></span> <span data-ttu-id="b3527-106">有关实体的详细信息，请参阅 [实体 (Master Data Services)](../entities-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b3527-106">For more information about entities, see [Entities &#40;Master Data Services&#41;](../entities-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="b3527-107">创建所有类型的属性，包括基于域的属性。</span><span class="sxs-lookup"><span data-stu-id="b3527-107">Create attributes of all types, including domain-based attributes.</span></span> <span data-ttu-id="b3527-108">有关属性的详细信息，请参阅 [属性 (Master Data Services)](../attributes-master-data-services.md) 和 [基于域的属性 (Master Data Services)](../domain-based-attributes-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b3527-108">For more information about attributes, see [Attributes &#40;Master Data Services&#41;](../attributes-master-data-services.md) and [Domain-Based Attributes &#40;Master Data Services&#41;](../domain-based-attributes-master-data-services.md).</span></span>  
  
 <span data-ttu-id="b3527-109">作为管理员，您必须通过使用 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 应用程序或 Web 服务来创建模型。</span><span class="sxs-lookup"><span data-stu-id="b3527-109">As an administrator, you must create the model by using the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application or the web service.</span></span> <span data-ttu-id="b3527-110">然后，您可以使用 [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 在模型中创建实体和属性。</span><span class="sxs-lookup"><span data-stu-id="b3527-110">Then you can use the [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] to create entities and attributes within the model.</span></span> <span data-ttu-id="b3527-111">有关模型对象的详细信息，请参阅 [模型 (Master Data Services)](../models-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b3527-111">For more information about model objects, see [Models &#40;Master Data Services&#41;](../models-master-data-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="b3527-112">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="b3527-112">Related Tasks</span></span>  
 <span data-ttu-id="b3527-113">大多数管理任务仍必须在 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 应用程序中或通过使用 Web 服务完成。</span><span class="sxs-lookup"><span data-stu-id="b3527-113">Most administrative tasks must still be done in the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application or by using the web service.</span></span> <span data-ttu-id="b3527-114">下表显示管理员可用于在 MDS 中完成任务的工具。</span><span class="sxs-lookup"><span data-stu-id="b3527-114">The following table shows which tools administrators can use to complete tasks in MDS.</span></span>  
  
|<span data-ttu-id="b3527-115">任务说明</span><span class="sxs-lookup"><span data-stu-id="b3527-115">Task Description</span></span>|<span data-ttu-id="b3527-116">工具</span><span class="sxs-lookup"><span data-stu-id="b3527-116">Tool</span></span>|<span data-ttu-id="b3527-117">主题</span><span class="sxs-lookup"><span data-stu-id="b3527-117">Topic</span></span>|  
|----------------------|----------|-----------|  
|<span data-ttu-id="b3527-118">创建模型。</span><span class="sxs-lookup"><span data-stu-id="b3527-118">Create models.</span></span>|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] <span data-ttu-id="b3527-119">Web 应用程序或 Web 服务</span><span class="sxs-lookup"><span data-stu-id="b3527-119">web application or web service</span></span>|[<span data-ttu-id="b3527-120">创建模型 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b3527-120">Create a Model &#40;Master Data Services&#41;</span></span>](../create-a-model-master-data-services.md)|  
|<span data-ttu-id="b3527-121">创建一个实体。</span><span class="sxs-lookup"><span data-stu-id="b3527-121">Create an entity.</span></span>|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] <span data-ttu-id="b3527-122">Web 应用程序、Web 服务或 [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3527-122">web application, web service, or the [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]</span></span>|[<span data-ttu-id="b3527-123">创建实体（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="b3527-123">Create an Entity &#40;MDS Add-in for Excel&#41;</span></span>](create-an-entity-mds-add-in-for-excel.md)|  
|<span data-ttu-id="b3527-124">创建基于域的属性。</span><span class="sxs-lookup"><span data-stu-id="b3527-124">Create a domain-based attribute.</span></span>|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] <span data-ttu-id="b3527-125">Web 应用程序、Web 服务或 [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3527-125">web application, web service, or the [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]</span></span>|[<span data-ttu-id="b3527-126">创建基于域的属性（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="b3527-126">Create a Domain-based Attribute &#40;MDS Add-in for Excel&#41;</span></span>](create-a-domain-based-attribute-mds-add-in-for-excel.md)|  
|<span data-ttu-id="b3527-127">创建属性组。</span><span class="sxs-lookup"><span data-stu-id="b3527-127">Create attribute groups.</span></span>|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] <span data-ttu-id="b3527-128">Web 应用程序或 Web 服务</span><span class="sxs-lookup"><span data-stu-id="b3527-128">web application or web service</span></span>|[<span data-ttu-id="b3527-129">创建属性组 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b3527-129">Create an Attribute Group &#40;Master Data Services&#41;</span></span>](../create-an-attribute-group-master-data-services.md)|  
|<span data-ttu-id="b3527-130">创建业务规则。</span><span class="sxs-lookup"><span data-stu-id="b3527-130">Create business rules.</span></span>|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] <span data-ttu-id="b3527-131">Web 应用程序或 Web 服务</span><span class="sxs-lookup"><span data-stu-id="b3527-131">web application or web service</span></span>|[<span data-ttu-id="b3527-132">创建和发布业务规则 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b3527-132">Create and Publish a Business Rule &#40;Master Data Services&#41;</span></span>](../create-and-publish-a-business-rule-master-data-services.md)|  
|<span data-ttu-id="b3527-133">创建订阅视图。</span><span class="sxs-lookup"><span data-stu-id="b3527-133">Create subscription views.</span></span>|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] <span data-ttu-id="b3527-134">Web 应用程序或 Web 服务</span><span class="sxs-lookup"><span data-stu-id="b3527-134">web application or web service</span></span>|[<span data-ttu-id="b3527-135">&#40;Master Data Services 创建订阅视图&#41;</span><span class="sxs-lookup"><span data-stu-id="b3527-135">Create a Subscription View &#40;Master Data Services&#41;</span></span>](../create-a-subscription-view-to-export-data-master-data-services.md)|  
|<span data-ttu-id="b3527-136">创建层次结构。</span><span class="sxs-lookup"><span data-stu-id="b3527-136">Create hierarchies.</span></span>|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] <span data-ttu-id="b3527-137">Web 应用程序或 Web 服务</span><span class="sxs-lookup"><span data-stu-id="b3527-137">web application or web service</span></span>|[<span data-ttu-id="b3527-138">创建派生层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b3527-138">Create a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../create-a-derived-hierarchy-master-data-services.md)<br /><br /> [<span data-ttu-id="b3527-139">创建显式层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b3527-139">Create an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../create-an-explicit-hierarchy-master-data-services.md)|  
|<span data-ttu-id="b3527-140">创建集合。</span><span class="sxs-lookup"><span data-stu-id="b3527-140">Create collections.</span></span>|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] <span data-ttu-id="b3527-141">Web 应用程序或 Web 服务</span><span class="sxs-lookup"><span data-stu-id="b3527-141">web application or web service</span></span>|[<span data-ttu-id="b3527-142">创建集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b3527-142">Create a Collection &#40;Master Data Services&#41;</span></span>](../create-a-collection-master-data-services.md)|  
|<span data-ttu-id="b3527-143">创建数据版本。</span><span class="sxs-lookup"><span data-stu-id="b3527-143">Create versions of data.</span></span>|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] <span data-ttu-id="b3527-144">Web 应用程序或 Web 服务</span><span class="sxs-lookup"><span data-stu-id="b3527-144">web application or web service</span></span>|[<span data-ttu-id="b3527-145">锁定版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b3527-145">Lock a Version &#40;Master Data Services&#41;</span></span>](../lock-a-version-master-data-services.md)|  
|<span data-ttu-id="b3527-146">部署模型。</span><span class="sxs-lookup"><span data-stu-id="b3527-146">Deploy models.</span></span>|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] <span data-ttu-id="b3527-147">Web 应用程序、Web 服务或 MDSModelDeploy 工具。</span><span class="sxs-lookup"><span data-stu-id="b3527-147">web application, web service, or MDSModelDeploy tool.</span></span>|[<span data-ttu-id="b3527-148">使用 MDSModelDeploy 创建模型部署包</span><span class="sxs-lookup"><span data-stu-id="b3527-148">Create a Model Deployment Package by Using MDSModelDeploy</span></span>](../create-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
  
## <a name="related-content"></a><span data-ttu-id="b3527-149">相关内容</span><span class="sxs-lookup"><span data-stu-id="b3527-149">Related Content</span></span>  
  
-   [<span data-ttu-id="b3527-150">模型 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b3527-150">Models &#40;Master Data Services&#41;</span></span>](../models-master-data-services.md)  
  
-   [<span data-ttu-id="b3527-151">实体 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b3527-151">Entities &#40;Master Data Services&#41;</span></span>](../entities-master-data-services.md)  
  
-   [<span data-ttu-id="b3527-152">属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b3527-152">Attributes &#40;Master Data Services&#41;</span></span>](../attributes-master-data-services.md)  
  
-   [<span data-ttu-id="b3527-153">基于域的属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b3527-153">Domain-Based Attributes &#40;Master Data Services&#41;</span></span>](../domain-based-attributes-master-data-services.md)  
  
-   [<span data-ttu-id="b3527-154">属性组 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b3527-154">Attribute Groups &#40;Master Data Services&#41;</span></span>](../attribute-groups-master-data-services.md)  
  
-   [<span data-ttu-id="b3527-155">业务规则 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b3527-155">Business Rules &#40;Master Data Services&#41;</span></span>](../business-rules-master-data-services.md)  
  
-   [<span data-ttu-id="b3527-156">将数据导出 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="b3527-156">Exporting Data &#40;Master Data Services&#41;</span></span>](../overview-exporting-data-master-data-services.md)  
  
-   [<span data-ttu-id="b3527-157">层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b3527-157">Hierarchies &#40;Master Data Services&#41;</span></span>](../hierarchies-master-data-services.md)  
  
-   [<span data-ttu-id="b3527-158">集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b3527-158">Collections &#40;Master Data Services&#41;</span></span>](../collections-master-data-services.md)  
  
-   [<span data-ttu-id="b3527-159">版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b3527-159">Versions &#40;Master Data Services&#41;</span></span>](../versions-master-data-services.md)  
  
-   [<span data-ttu-id="b3527-160">安全性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b3527-160">Security &#40;Master Data Services&#41;</span></span>](../security-master-data-services.md)  
  
-   [<span data-ttu-id="b3527-161">部署模型 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b3527-161">Deploying Models &#40;Master Data Services&#41;</span></span>](../deploying-models-master-data-services.md)  
  
  
