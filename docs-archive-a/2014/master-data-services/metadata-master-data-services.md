---
title: Master Data Services) 的元数据 (|Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- user-defined metadata [Master Data Services], about user-defined metadata
- metadata [Master Data Services], about metadata
- metadata [Master Data Services]
- user-defined metadata [Master Data Services]
ms.assetid: ac1aabe3-d8d4-4d7a-8954-50ee3c185d81
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 39ab95b7925306febb551962495da7ec9751589b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688979"
---
# <a name="metadata-master-data-services"></a><span data-ttu-id="6eab5-102">元数据 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="6eab5-102">Metadata (Master Data Services)</span></span>
  <span data-ttu-id="6eab5-103">在[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，用户定义元数据是您用于描述模型对象的信息。</span><span class="sxs-lookup"><span data-stu-id="6eab5-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], user-defined metadata is information that you use to describe model objects.</span></span> <span data-ttu-id="6eab5-104">例如，您可能要跟踪特定模型或实体的所有者，或者跟踪向实体提供数据的源系统。</span><span class="sxs-lookup"><span data-stu-id="6eab5-104">For example, you may want to track the owners of a particular model or entity, or track the source systems that supply data to an entity.</span></span>  
  
 <span data-ttu-id="6eab5-105">用户定义元数据由名为**元数据**的模型管理。</span><span class="sxs-lookup"><span data-stu-id="6eab5-105">User-defined metadata is managed by a model called **Metadata**.</span></span> <span data-ttu-id="6eab5-106">此模型在安装时自动包含 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ，并且与所有其他 MDS 模型相似，不同之处在于你不能创建它的版本。</span><span class="sxs-lookup"><span data-stu-id="6eab5-106">This model is automatically included when [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] is installed, and it is similar to all other MDS models, except that you cannot create versions of it.</span></span>  
  
 <span data-ttu-id="6eab5-107">在使用用户定义元数据填充元数据模型之后，可以在订阅视图中包含该模型，以便它可由订阅系统使用。</span><span class="sxs-lookup"><span data-stu-id="6eab5-107">After you populate the Metadata model with user-defined metadata, you can include it in subscription views, so it can be consumed by subscribing systems.</span></span>  
  
## <a name="metadata-entities"></a><span data-ttu-id="6eab5-108">元数据实体</span><span class="sxs-lookup"><span data-stu-id="6eab5-108">Metadata Entities</span></span>  
 <span data-ttu-id="6eab5-109">“元数据”模型包括五个实体，每个实体都表示支持用户定义元数据的一种主数据模型对象。</span><span class="sxs-lookup"><span data-stu-id="6eab5-109">The Metadata model includes five entities, each of which represents a type of master data model object that supports user-defined metadata.</span></span> <span data-ttu-id="6eab5-110">例如，"**模型元数据定义**" 实体包含表示模型的成员，而 "**属性元数据定义**" 实体包含表示所有模型中所有属性的成员。</span><span class="sxs-lookup"><span data-stu-id="6eab5-110">For example, the **Model Metadata Definition** entity contains members that represent models, and the **Attribute Metadata Definition** entity has members that represent all attributes in all models.</span></span>  
  
 <span data-ttu-id="6eab5-111">为了定义某一模型对象的元数据，您填充其中一个成员的属性。</span><span class="sxs-lookup"><span data-stu-id="6eab5-111">To define metadata for a model object, you populate one of these member's attributes.</span></span> <span data-ttu-id="6eab5-112">例如，在 "**实体元数据定义**" 实体中，可以使用以下文本填充 Price 成员的 Description 属性：**销售给客户时的产品价格**。</span><span class="sxs-lookup"><span data-stu-id="6eab5-112">For example, in the **Entity Metadata Definition** entity, you can populate the Price member's Description attribute with the text: **The product price when sold to a customer**.</span></span>  
  
 <span data-ttu-id="6eab5-113">只要添加或删除支持用户定义元数据的模型对象，元数据模型中的成员就会自动更新。</span><span class="sxs-lookup"><span data-stu-id="6eab5-113">The members in the Metadata model are automatically updated whenever model objects that support user-defined metadata are added or deleted.</span></span>  
  
 <span data-ttu-id="6eab5-114">不能对元数据模型进行版本控制，添加或更改版本标志，也不能将该模型另存为模型部署包。</span><span class="sxs-lookup"><span data-stu-id="6eab5-114">The Metadata model cannot be versioned, have version flags added or changed, or be saved as a model deployment package.</span></span> <span data-ttu-id="6eab5-115">但是，该模型具有可用于其他主数据模型的其他所有功能。</span><span class="sxs-lookup"><span data-stu-id="6eab5-115">However, it has all the same other functionality available to other master data models.</span></span> <span data-ttu-id="6eab5-116">例如，您可以对元数据模型实现一组业务规则，以便强制执行数据策略。</span><span class="sxs-lookup"><span data-stu-id="6eab5-116">For example, you might implement a set of business rules on the Metadata model to enforce data policies.</span></span>  
  
## <a name="customizing-your-metadata-model"></a><span data-ttu-id="6eab5-117">自定义元数据模型</span><span class="sxs-lookup"><span data-stu-id="6eab5-117">Customizing Your Metadata Model</span></span>  
 <span data-ttu-id="6eab5-118">每个元数据定义实体都包括 Name、Code 和 Description 属性。</span><span class="sxs-lookup"><span data-stu-id="6eab5-118">Each metadata definition entity includes Name, Code, and Description attributes.</span></span> <span data-ttu-id="6eab5-119">您可能要创建附加的属性以便进一步描述您的模型对象。</span><span class="sxs-lookup"><span data-stu-id="6eab5-119">You may want to create additional attributes to further describe your model objects.</span></span>  
  
 <span data-ttu-id="6eab5-120">例如，您可以创建：</span><span class="sxs-lookup"><span data-stu-id="6eab5-120">For example, you might create:</span></span>  
  
-   <span data-ttu-id="6eab5-121">名为 Owner 的基于域的属性，可用于跟踪各模型对象的所有者。</span><span class="sxs-lookup"><span data-stu-id="6eab5-121">A domain-based attribute named Owner, which you use to track the owner of each model object.</span></span>  
  
-   <span data-ttu-id="6eab5-122">名为 Last Review Date 的自由格式的属性，可用于跟踪所有者上次审核某一对象的日期。</span><span class="sxs-lookup"><span data-stu-id="6eab5-122">A free-form attribute named Last Review Date, which you use to track the date that an object was last reviewed by the owner.</span></span>  
  
-   <span data-ttu-id="6eab5-123">一个名为 "源" 的基于域的属性，可用于跟踪和管理与实例交互的源系统 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6eab5-123">A domain-based attribute named Sources, which you use to track and manage the source systems that interact with the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] instance.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="6eab5-124">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="6eab5-124">Related Tasks</span></span>  
  
|<span data-ttu-id="6eab5-125">任务说明</span><span class="sxs-lookup"><span data-stu-id="6eab5-125">Task Description</span></span>|<span data-ttu-id="6eab5-126">主题</span><span class="sxs-lookup"><span data-stu-id="6eab5-126">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="6eab5-127">向模型对象添加元数据。</span><span class="sxs-lookup"><span data-stu-id="6eab5-127">Add metadata to a model object.</span></span>|[<span data-ttu-id="6eab5-128">Master Data Services&#41;添加元数据 &#40;</span><span class="sxs-lookup"><span data-stu-id="6eab5-128">Add Metadata &#40;Master Data Services&#41;</span></span>](add-metadata-master-data-services.md)
|&nbsp;|&nbsp;|
  
## <a name="related-content"></a><span data-ttu-id="6eab5-129">相关内容</span><span class="sxs-lookup"><span data-stu-id="6eab5-129">Related Content</span></span>  
  
-   [<span data-ttu-id="6eab5-130">将数据导出 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6eab5-130">Exporting Data &#40;Master Data Services&#41;</span></span>](overview-exporting-data-master-data-services.md)  
  
  
