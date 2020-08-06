---
title: " (Master Data Services) 的合并权限 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], consolidated member attribute permissions
- consolidated members [Master Data Services], attribute permissions
- permissions [Master Data Services], consolidated members
- members [Master Data Services], consolidated member permissions
ms.assetid: 084055a3-5fd3-43f3-b620-ac6afab42a3d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c4c93e74acc84d6e742139263bedc011c4028efb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591937"
---
# <a name="consolidated-permissions-master-data-services"></a><span data-ttu-id="39dba-102">合并的权限（主数据服务）</span><span class="sxs-lookup"><span data-stu-id="39dba-102">Consolidated Permissions (Master Data Services)</span></span>
  <span data-ttu-id="39dba-103">合并权限应用到实体的所有合并成员的属性值。</span><span class="sxs-lookup"><span data-stu-id="39dba-103">Consolidated permissions apply to the attribute values for all consolidated members of an entity.</span></span>  
  
 <span data-ttu-id="39dba-104">合并的权限仅应用到为显式层次结构和集合启用的实体。</span><span class="sxs-lookup"><span data-stu-id="39dba-104">Consolidated permissions apply only to entities that are enabled for explicit hierarchies and collections.</span></span>  
  
 <span data-ttu-id="39dba-105">注意：</span><span class="sxs-lookup"><span data-stu-id="39dba-105">**Notes:**</span></span>  
  
-   <span data-ttu-id="39dba-106">叶权限仅应用到用户界面的 **“资源管理器”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="39dba-106">Leaf permissions apply to the **Explorer** functional area of the user interface only.</span></span>  
  
-   <span data-ttu-id="39dba-107">不强制向 **Name** 和 **Code** 属性分配权限。</span><span class="sxs-lookup"><span data-stu-id="39dba-107">Permissions assigned to **Name** and **Code** attributes are not enforced.</span></span>  
  
|<span data-ttu-id="39dba-108">权限</span><span class="sxs-lookup"><span data-stu-id="39dba-108">Permission</span></span>|<span data-ttu-id="39dba-109">说明</span><span class="sxs-lookup"><span data-stu-id="39dba-109">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="39dba-110">**只读**</span><span class="sxs-lookup"><span data-stu-id="39dba-110">**Read-only**</span></span>|<span data-ttu-id="39dba-111">显示合并成员，但是用户不能添加、删除或更改它们。</span><span class="sxs-lookup"><span data-stu-id="39dba-111">Consolidated members are displayed but the user cannot add, remove, or change them.</span></span>|  
|<span data-ttu-id="39dba-112">**更新**</span><span class="sxs-lookup"><span data-stu-id="39dba-112">**Update**</span></span>|<span data-ttu-id="39dba-113">显示合并成员，用户可以添加、删除和更改它们。</span><span class="sxs-lookup"><span data-stu-id="39dba-113">Consolidated members are displayed and the user can add, remove, and change them.</span></span>|  
|<span data-ttu-id="39dba-114">**拒绝**</span><span class="sxs-lookup"><span data-stu-id="39dba-114">**Deny**</span></span>|<span data-ttu-id="39dba-115">不显示实体的合并成员。</span><span class="sxs-lookup"><span data-stu-id="39dba-115">Consolidated members for the entity are not displayed.</span></span>|  
  
## <a name="attribute-permissions"></a><span data-ttu-id="39dba-116">属性权限</span><span class="sxs-lookup"><span data-stu-id="39dba-116">Attribute Permissions</span></span>  
 <span data-ttu-id="39dba-117">属性权限应用到该属性用于特定实体的值。</span><span class="sxs-lookup"><span data-stu-id="39dba-117">Attribute permissions apply to the attribute's values for the specific entity.</span></span> <span data-ttu-id="39dba-118">仅具有属性权限的用户不能添加或删除成员。</span><span class="sxs-lookup"><span data-stu-id="39dba-118">Users with only attribute permissions cannot add or remove members.</span></span>  
  
|<span data-ttu-id="39dba-119">权限</span><span class="sxs-lookup"><span data-stu-id="39dba-119">Permission</span></span>|<span data-ttu-id="39dba-120">说明</span><span class="sxs-lookup"><span data-stu-id="39dba-120">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="39dba-121">**只读**</span><span class="sxs-lookup"><span data-stu-id="39dba-121">**Read-only**</span></span>|<span data-ttu-id="39dba-122">显示属性，但是用户不能更改属性值。</span><span class="sxs-lookup"><span data-stu-id="39dba-122">The attribute is displayed but the user cannot change attribute values.</span></span>|  
|<span data-ttu-id="39dba-123">**更新**</span><span class="sxs-lookup"><span data-stu-id="39dba-123">**Update**</span></span>|<span data-ttu-id="39dba-124">显示属性，用户可以更改属性值。</span><span class="sxs-lookup"><span data-stu-id="39dba-124">The attribute is displayed and the user can change attribute values.</span></span>|  
|<span data-ttu-id="39dba-125">**拒绝**</span><span class="sxs-lookup"><span data-stu-id="39dba-125">**Deny**</span></span>|<span data-ttu-id="39dba-126">不显示属性。</span><span class="sxs-lookup"><span data-stu-id="39dba-126">The attribute is not displayed.</span></span><br /><br /> <span data-ttu-id="39dba-127">注意：不能明确拒绝对 Name 和 Code 属性的访问权限。</span><span class="sxs-lookup"><span data-stu-id="39dba-127">Note: You cannot explicitly deny access to Name and Code attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="39dba-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="39dba-128">See Also</span></span>  
 <span data-ttu-id="39dba-129">[&#40;Master Data Services 分配模型对象权限&#41;](assign-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="39dba-129">[Assign Model Object Permissions &#40;Master Data Services&#41;](assign-model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="39dba-130">[叶权限 &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="39dba-130">[Leaf Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="39dba-131">[&#40;Master Data Services 的模型对象权限&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="39dba-131">[Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="39dba-132">[成员 &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="39dba-132">[Members &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span></span>  
 [<span data-ttu-id="39dba-133">属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="39dba-133">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
