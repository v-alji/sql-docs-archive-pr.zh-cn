---
title: 叶权限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services], permissions
- members [Master Data Services], leaf member permissions
- permissions [Master Data Services], leaf members
- leaf members [Master Data Services], attribute permissions
- attributes [Master Data Services], leaf member attribute permissions
ms.assetid: bde16e8c-bcd4-4041-8130-55c5450e5f72
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 794e1d138b91e896b8df16765ae8984c6e60aca7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692433"
---
# <a name="leaf-permissions-master-data-services"></a><span data-ttu-id="052d2-102">叶权限（主数据服务）</span><span class="sxs-lookup"><span data-stu-id="052d2-102">Leaf Permissions (Master Data Services)</span></span>
  <span data-ttu-id="052d2-103">叶权限应用到实体的所有叶成员的属性值。</span><span class="sxs-lookup"><span data-stu-id="052d2-103">Leaf permissions apply to the attribute values for all leaf members of an entity.</span></span>  
  
 <span data-ttu-id="052d2-104">对于未启用显式层次结构的实体，将权限分配给 **“叶”** 等同于将权限分配给实体。</span><span class="sxs-lookup"><span data-stu-id="052d2-104">For entities without explicit hierarchies enabled, assigning permission to **Leaf** is the same as assigning permission to the entity.</span></span>  
  
 <span data-ttu-id="052d2-105">注意：</span><span class="sxs-lookup"><span data-stu-id="052d2-105">**Notes:**</span></span>  
  
-   <span data-ttu-id="052d2-106">叶权限仅应用到用户界面的 **“资源管理器”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="052d2-106">Leaf permissions apply to the **Explorer** functional area of the user interface only.</span></span>  
  
-   <span data-ttu-id="052d2-107">不强制向 **Name** 和 **Code** 属性分配权限。</span><span class="sxs-lookup"><span data-stu-id="052d2-107">Permissions assigned to **Name** and **Code** attributes are not enforced.</span></span>  
  
|<span data-ttu-id="052d2-108">权限</span><span class="sxs-lookup"><span data-stu-id="052d2-108">Permission</span></span>|<span data-ttu-id="052d2-109">说明</span><span class="sxs-lookup"><span data-stu-id="052d2-109">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="052d2-110">**只读**</span><span class="sxs-lookup"><span data-stu-id="052d2-110">**Read-only**</span></span>|<span data-ttu-id="052d2-111">显示叶成员，但是用户不能添加、删除或更改它们。</span><span class="sxs-lookup"><span data-stu-id="052d2-111">Leaf members are displayed but the user cannot add, remove, or change them.</span></span><br /><br /> <span data-ttu-id="052d2-112">如果存在合并成员，则显示名称和代码，但是用户不能添加、删除或更改它们。</span><span class="sxs-lookup"><span data-stu-id="052d2-112">If consolidated members exist, the names and codes are displayed but the user cannot add, remove, or change them.</span></span>|  
|<span data-ttu-id="052d2-113">**更新**</span><span class="sxs-lookup"><span data-stu-id="052d2-113">**Update**</span></span>|<span data-ttu-id="052d2-114">显示叶成员，用户可以添加、删除和更改它们。</span><span class="sxs-lookup"><span data-stu-id="052d2-114">Leaf members are displayed and the user can add, remove, and change them.</span></span><br /><br /> <span data-ttu-id="052d2-115">如果存在合并成员，则显示名称和代码，但是用户不能添加、删除或更改它们。</span><span class="sxs-lookup"><span data-stu-id="052d2-115">If consolidated members exist, the names and codes are displayed but the user cannot add, remove, or change them.</span></span>|  
|<span data-ttu-id="052d2-116">**拒绝**</span><span class="sxs-lookup"><span data-stu-id="052d2-116">**Deny**</span></span>|<span data-ttu-id="052d2-117">不显示实体的叶成员。</span><span class="sxs-lookup"><span data-stu-id="052d2-117">Leaf members for the entity are not displayed.</span></span>|  
  
## <a name="attribute-permissions"></a><span data-ttu-id="052d2-118">属性权限</span><span class="sxs-lookup"><span data-stu-id="052d2-118">Attribute Permissions</span></span>  
 <span data-ttu-id="052d2-119">属性权限应用到该属性用于特定实体的值。</span><span class="sxs-lookup"><span data-stu-id="052d2-119">Attribute permissions apply to the attribute's values for the specific entity.</span></span> <span data-ttu-id="052d2-120">仅具有属性权限的用户不能添加或删除成员。</span><span class="sxs-lookup"><span data-stu-id="052d2-120">Users with attribute permissions only cannot add or remove members.</span></span>  
  
|<span data-ttu-id="052d2-121">权限</span><span class="sxs-lookup"><span data-stu-id="052d2-121">Permission</span></span>|<span data-ttu-id="052d2-122">说明</span><span class="sxs-lookup"><span data-stu-id="052d2-122">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="052d2-123">**只读**</span><span class="sxs-lookup"><span data-stu-id="052d2-123">**Read-only**</span></span>|<span data-ttu-id="052d2-124">显示属性，但是用户不能更改属性值。</span><span class="sxs-lookup"><span data-stu-id="052d2-124">The attribute is displayed but the user cannot change attribute values.</span></span>|  
|<span data-ttu-id="052d2-125">**更新**</span><span class="sxs-lookup"><span data-stu-id="052d2-125">**Update**</span></span>|<span data-ttu-id="052d2-126">显示属性，用户可以更改属性值。</span><span class="sxs-lookup"><span data-stu-id="052d2-126">The attribute is displayed and the user can change attribute values.</span></span>|  
|<span data-ttu-id="052d2-127">**拒绝**</span><span class="sxs-lookup"><span data-stu-id="052d2-127">**Deny**</span></span>|<span data-ttu-id="052d2-128">不显示属性。</span><span class="sxs-lookup"><span data-stu-id="052d2-128">The attribute is not displayed.</span></span><br /><br /> <span data-ttu-id="052d2-129">注意：不能明确拒绝对 Name 和 Code 属性的访问权限。</span><span class="sxs-lookup"><span data-stu-id="052d2-129">Note: You cannot explicitly deny access to Name and Code attributes.</span></span>|  
  
### <a name="example"></a><span data-ttu-id="052d2-130">示例</span><span class="sxs-lookup"><span data-stu-id="052d2-130">Example</span></span>  
 <span data-ttu-id="052d2-131">对于 Product 实体，将 **“更新”** 权限分配给 Subcategory 属性。</span><span class="sxs-lookup"><span data-stu-id="052d2-131">For the Product entity, assign **Update** permission to Subcategory attribute.</span></span> <span data-ttu-id="052d2-132">向所有其他属性分配“拒绝”权限。</span><span class="sxs-lookup"><span data-stu-id="052d2-132">Deny permission to all other attributes.</span></span>  
  
|<span data-ttu-id="052d2-133">名称</span><span class="sxs-lookup"><span data-stu-id="052d2-133">Name</span></span>|<span data-ttu-id="052d2-134">代码</span><span class="sxs-lookup"><span data-stu-id="052d2-134">Code</span></span>|<span data-ttu-id="052d2-135">Subcategory（更新）</span><span class="sxs-lookup"><span data-stu-id="052d2-135">Subcategory (Update)</span></span>|  
|----------|----------|----------------------------|  
|<span data-ttu-id="052d2-136">Mountain-100</span><span class="sxs-lookup"><span data-stu-id="052d2-136">Mountain-100</span></span>|<span data-ttu-id="052d2-137">BK-M101</span><span class="sxs-lookup"><span data-stu-id="052d2-137">BK-M101</span></span>|<span data-ttu-id="052d2-138">{5}山地自行车</span><span class="sxs-lookup"><span data-stu-id="052d2-138">{5} Mountain Bikes</span></span>|  
|<span data-ttu-id="052d2-139">Mountain-100</span><span class="sxs-lookup"><span data-stu-id="052d2-139">Mountain-100</span></span>|<span data-ttu-id="052d2-140">BK-M201</span><span class="sxs-lookup"><span data-stu-id="052d2-140">BK-M201</span></span>|<span data-ttu-id="052d2-141">{5}山地自行车</span><span class="sxs-lookup"><span data-stu-id="052d2-141">{5} Mountain Bikes</span></span>|  
  
 <span data-ttu-id="052d2-142">在 **“资源管理器”** 中，可以更新 Subcategory 列中的任何属性值。</span><span class="sxs-lookup"><span data-stu-id="052d2-142">In **Explorer**, you can update any attribute value in the Subcategory column.</span></span> <span data-ttu-id="052d2-143">如果您没有对属性的权限，则不显示该属性。</span><span class="sxs-lookup"><span data-stu-id="052d2-143">If you do not have permission to an attribute, the attribute is not displayed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="052d2-144">在本示例中，Subcategory 是基于域的属性，基于 SubcategoryList 实体。</span><span class="sxs-lookup"><span data-stu-id="052d2-144">In this example, Subcategory is a domain-based attribute, based on the SubcategoryList entity.</span></span> <span data-ttu-id="052d2-145">可以为 Mountain-100 选择不同子类别，但是不能向 SubcategoryList 实体添加成员或从中删除成员。</span><span class="sxs-lookup"><span data-stu-id="052d2-145">You can select a different subcategory for Mountain-100 but you cannot add members to or delete members from the SubcategoryList entity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="052d2-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="052d2-146">See Also</span></span>  
 <span data-ttu-id="052d2-147">[&#40;Master Data Services 分配模型对象权限&#41;](assign-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="052d2-147">[Assign Model Object Permissions &#40;Master Data Services&#41;](assign-model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="052d2-148">[&#40;Master Data Services 的合并权限&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="052d2-148">[Consolidated Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="052d2-149">[&#40;Master Data Services 的模型对象权限&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="052d2-149">[Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="052d2-150">[成员 &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="052d2-150">[Members &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span></span>  
 [<span data-ttu-id="052d2-151">属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="052d2-151">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
