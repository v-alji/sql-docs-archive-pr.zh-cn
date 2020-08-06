---
title: 重叠的模型和成员权限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], effective permissions
- permissions [Master Data Services], model and member overlaps
- members [Master Data Services], effective permissions
ms.assetid: 9fd7a555-43bf-4796-a8b6-1ca63a291216
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ec5f4019f25a777e4c70433bd9a7e72fca2277e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578276"
---
# <a name="overlapping-model-and-member-permissions-master-data-services"></a><span data-ttu-id="6bc82-102">重叠的模型和成员权限（主数据服务）</span><span class="sxs-lookup"><span data-stu-id="6bc82-102">Overlapping Model and Member Permissions (Master Data Services)</span></span>
  <span data-ttu-id="6bc82-103">分配给成员的权限可与分配给模型对象的权限重叠。</span><span class="sxs-lookup"><span data-stu-id="6bc82-103">Permission assigned to a member can overlap with permission assigned to a model object.</span></span> <span data-ttu-id="6bc82-104">出现重叠时，限制性更强的权限将生效。</span><span class="sxs-lookup"><span data-stu-id="6bc82-104">When overlaps occur, the more restrictive permission takes effect.</span></span>  
  
 <span data-ttu-id="6bc82-105">如果成员具有不同于其相应模型对象的权限，适用以下规则：</span><span class="sxs-lookup"><span data-stu-id="6bc82-105">If a member has permission that is different than its corresponding model object, the following rules apply:</span></span>  
  
-   <span data-ttu-id="6bc82-106">**“拒绝”** 覆盖所有其他权限。</span><span class="sxs-lookup"><span data-stu-id="6bc82-106">**Deny** overrides all other permissions.</span></span>  
  
-   <span data-ttu-id="6bc82-107">**只读**替代**更新**。</span><span class="sxs-lookup"><span data-stu-id="6bc82-107">**Read-only** overrides **Update**.</span></span>  
  
 <span data-ttu-id="6bc82-108">下图显示在属性权限不同于成员权限时，哪些权限对单个属性值有效。</span><span class="sxs-lookup"><span data-stu-id="6bc82-108">The following image shows which permissions take effect on an individual attribute value when attribute permissions are different than member permissions.</span></span>  
  
 <span data-ttu-id="6bc82-109">![mds_conc_security_member_overlap_table](../../2014/master-data-services/media/mds-conc-security-member-overlap-table.gif "mds_conc_security_member_overlap_table")</span><span class="sxs-lookup"><span data-stu-id="6bc82-109">![mds_conc_security_member_overlap_table](../../2014/master-data-services/media/mds-conc-security-member-overlap-table.gif "mds_conc_security_member_overlap_table")</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="6bc82-110">示例 1</span><span class="sxs-lookup"><span data-stu-id="6bc82-110">Example 1</span></span>  
 <span data-ttu-id="6bc82-111">![mds_conc_overlap_model_1](../../2014/master-data-services/media/mds-conc-overlap-model-1.gif "mds_conc_overlap_model_1")</span><span class="sxs-lookup"><span data-stu-id="6bc82-111">![mds_conc_overlap_model_1](../../2014/master-data-services/media/mds-conc-overlap-model-1.gif "mds_conc_overlap_model_1")</span></span>  
  
 <span data-ttu-id="6bc82-112">在 **“模型”** 选项卡上，Product 实体分配有 **“更新”** 权限。</span><span class="sxs-lookup"><span data-stu-id="6bc82-112">On the **Models** tab, the Product entity has **Update** permission assigned.</span></span> <span data-ttu-id="6bc82-113">该实体中的所有属性都继承该权限。</span><span class="sxs-lookup"><span data-stu-id="6bc82-113">All attributes in the entity inherit that permission.</span></span>  
  
 <span data-ttu-id="6bc82-114">在 **“层次结构成员”** 选项卡上，派生的层次结构中的“山地车”子类别节点分配有 **“更新”** 权限。</span><span class="sxs-lookup"><span data-stu-id="6bc82-114">On the **Hierarchy Members** tab, the Mountain Bikes subcategory node in a derived hierarchy has **Update** permission assigned.</span></span>  
  
 <span data-ttu-id="6bc82-115">结果：在 **“资源管理器”** 中，用户对“山地车”节点中所有成员的所有属性值都具有 **“更新”** 权限。</span><span class="sxs-lookup"><span data-stu-id="6bc82-115">Result: In **Explorer**, the user has **Update** permission to all attribute values for all members in the Mountain Bikes node.</span></span> <span data-ttu-id="6bc82-116">所有其他成员和属性均隐藏。</span><span class="sxs-lookup"><span data-stu-id="6bc82-116">All other members and attributes are hidden.</span></span>  
  
 <span data-ttu-id="6bc82-117">![mds_conc_overlap_model_example_1](../../2014/master-data-services/media/mds-conc-overlap-model-example-1.gif "mds_conc_overlap_model_example_1")</span><span class="sxs-lookup"><span data-stu-id="6bc82-117">![mds_conc_overlap_model_example_1](../../2014/master-data-services/media/mds-conc-overlap-model-example-1.gif "mds_conc_overlap_model_example_1")</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="6bc82-118">示例 2</span><span class="sxs-lookup"><span data-stu-id="6bc82-118">Example 2</span></span>  
 <span data-ttu-id="6bc82-119">![mds_conc_overlap_model_2](../../2014/master-data-services/media/mds-conc-overlap-model-2.gif "mds_conc_overlap_model_2")</span><span class="sxs-lookup"><span data-stu-id="6bc82-119">![mds_conc_overlap_model_2](../../2014/master-data-services/media/mds-conc-overlap-model-2.gif "mds_conc_overlap_model_2")</span></span>  
  
 <span data-ttu-id="6bc82-120">在 **“模型”** 选项卡上，Subcategory 属性分配有 **“更新”** 权限。</span><span class="sxs-lookup"><span data-stu-id="6bc82-120">On the **Models** tab, the Subcategory attribute has **Update** permission assigned.</span></span>  
  
 <span data-ttu-id="6bc82-121">在 "**层次结构成员**" 选项卡上，派生层次结构中的 "山地自行车" 子类别节点显式分配有**只读**权限。</span><span class="sxs-lookup"><span data-stu-id="6bc82-121">On the **Hierarchy Members** tab, the Mountain Bikes subcategory node in a derived hierarchy is explicitly assigned **Read-only** permission.</span></span>  
  
 <span data-ttu-id="6bc82-122">结果：在 "**资源管理器**" 中，用户对 "山地车" 节点中成员的子类别属性值具有**只读**权限。</span><span class="sxs-lookup"><span data-stu-id="6bc82-122">Result: In **Explorer**, the user has **Read-only** permission to the Subcategory attribute values for the members in the Mountain Bikes node.</span></span> <span data-ttu-id="6bc82-123">所有其他成员和属性均隐藏。</span><span class="sxs-lookup"><span data-stu-id="6bc82-123">All other members and attributes are hidden.</span></span>  
  
 <span data-ttu-id="6bc82-124">![mds_conc_overlap_model_example_2](../../2014/master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")</span><span class="sxs-lookup"><span data-stu-id="6bc82-124">![mds_conc_overlap_model_example_2](../../2014/master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")</span></span>  
  
## <a name="example-3"></a><span data-ttu-id="6bc82-125">示例 3</span><span class="sxs-lookup"><span data-stu-id="6bc82-125">Example 3</span></span>  
 <span data-ttu-id="6bc82-126">![mds_conc_overlap_model_3](../../2014/master-data-services/media/mds-conc-overlap-model-3.gif "mds_conc_overlap_model_3")</span><span class="sxs-lookup"><span data-stu-id="6bc82-126">![mds_conc_overlap_model_3](../../2014/master-data-services/media/mds-conc-overlap-model-3.gif "mds_conc_overlap_model_3")</span></span>  
  
 <span data-ttu-id="6bc82-127">在 "**模型**" 选项卡上，"子类别" 属性分配有**只读**权限。</span><span class="sxs-lookup"><span data-stu-id="6bc82-127">On the **Models** tab, the Subcategory attribute has **Read-only** permission assigned.</span></span>  
  
 <span data-ttu-id="6bc82-128">在 **“层次结构成员”** 选项卡上，派生的层次结构中的“山地车”子类别显式分配有 **“更新”** 权限。</span><span class="sxs-lookup"><span data-stu-id="6bc82-128">On the **Hierarchy Members** tab, the Mountain Bikes subcategory in a derived hierarchy is explicitly assigned **Update** permission.</span></span>  
  
 <span data-ttu-id="6bc82-129">结果：在 "**资源管理器**" 中，用户对属性值具有**只读**权限。</span><span class="sxs-lookup"><span data-stu-id="6bc82-129">Result: In **Explorer**, the user has **Read-only** permission to the attribute values.</span></span> <span data-ttu-id="6bc82-130">所有其他成员和属性均隐藏。</span><span class="sxs-lookup"><span data-stu-id="6bc82-130">All other members and attributes are hidden.</span></span>  
  
 <span data-ttu-id="6bc82-131">![mds_conc_overlap_model_example_2](../../2014/master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")</span><span class="sxs-lookup"><span data-stu-id="6bc82-131">![mds_conc_overlap_model_example_2](../../2014/master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bc82-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6bc82-132">See Also</span></span>  
 <span data-ttu-id="6bc82-133">[如何 Master Data Services &#40;确定权限&#41;](how-permissions-are-determined-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="6bc82-133">[How Permissions Are Determined &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md) </span></span>  
 [<span data-ttu-id="6bc82-134">重叠的用户和组权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="6bc82-134">Overlapping User and Group Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md)  
  
  
