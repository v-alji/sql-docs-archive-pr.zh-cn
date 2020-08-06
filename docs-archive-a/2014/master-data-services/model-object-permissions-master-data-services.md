---
title: 模型对象权限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], model objects
- models [Master Data Services], object permissions
ms.assetid: fab6335b-4cae-47de-ae7c-6c4743e0680f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 4cc64d753b680cfabc3707a29c6d9de631708c20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590242"
---
# <a name="model-object-permissions-master-data-services"></a><span data-ttu-id="d6478-102">模型对象权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d6478-102">Model Object Permissions (Master Data Services)</span></span>
  <span data-ttu-id="d6478-103">模型对象权限是必需的。</span><span class="sxs-lookup"><span data-stu-id="d6478-103">Model object permissions are mandatory.</span></span> <span data-ttu-id="d6478-104">这些权限确定用户在用户界面的 **“资源管理器”** 功能区域中可以访问哪些属性。</span><span class="sxs-lookup"><span data-stu-id="d6478-104">They determine the attributes a user can access in the **Explorer** functional area of the UI.</span></span>  
  
 <span data-ttu-id="d6478-105">例如，如果向某个用户分配对 Product 实体的 **“更新”** 权限，则该用户可以更新 Product 实体的所有属性。</span><span class="sxs-lookup"><span data-stu-id="d6478-105">For example, if you assign a user **Update** permission to the Product entity, the user can update all of the attributes of the Product entity.</span></span> <span data-ttu-id="d6478-106">如果分配对单个属性的 **“更新”** 权限，则该用户只能更新该属性。</span><span class="sxs-lookup"><span data-stu-id="d6478-106">If you assign **Update** permission to a single attribute, the user can update that attribute only.</span></span>  
  
 <span data-ttu-id="d6478-107">若要确定通过每个属性值分配的安全设置，可以将模型对象权限与层次结构成员权限组合，从而确定用户可以访问哪些成员。</span><span class="sxs-lookup"><span data-stu-id="d6478-107">To determine security assigned on each individual attribute value, model object permissions are combined with hierarchy member permissions, which determine the members a user can access.</span></span>  
  
 <span data-ttu-id="d6478-108">若要授予用户访问 "**资源管理器**" 之外的功能区域的权限，该用户必须是模型管理员，这也会涉及分配模型对象权限。</span><span class="sxs-lookup"><span data-stu-id="d6478-108">To give a user access to a functional area other than **Explorer**, the user must be a model administrator, which also involves assigning model object permissions.</span></span> <span data-ttu-id="d6478-109">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d6478-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
 <span data-ttu-id="d6478-110">模型对象权限是在用户界面中分配的 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] (UI) ，在 "**模型**" 选项卡上的 "**用户和组权限**" 功能区域中。在此选项卡上，模型表示为树状结构。</span><span class="sxs-lookup"><span data-stu-id="d6478-110">Model object permissions are assigned in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] user interface (UI), in the **User and Group Permissions** functional area on the **Models** tab. On this tab, the model is represented as a tree structure.</span></span> <span data-ttu-id="d6478-111">将权限分配给树中的对象时，下面的所有对象都将继承该权限。</span><span class="sxs-lookup"><span data-stu-id="d6478-111">When you assign permission to an object in the tree, all objects below inherit that permission.</span></span> <span data-ttu-id="d6478-112">可以通过为单个对象分配权限来覆盖此类继承。</span><span class="sxs-lookup"><span data-stu-id="d6478-112">You can override that inheritance by assigning permission to individual objects.</span></span>  
  
 <span data-ttu-id="d6478-113">您可以为模型对象分配**只读**、**更新**或**拒绝**权限。</span><span class="sxs-lookup"><span data-stu-id="d6478-113">You can assign **Read-only**, **Update**, or **Deny** permission to model objects.</span></span> <span data-ttu-id="d6478-114">如果没有在 **“模型”** 选项卡上分配任何权限，用户就不能在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中查看任何模型或数据。</span><span class="sxs-lookup"><span data-stu-id="d6478-114">If you do not assign any permissions on the **Models** tab, the user cannot view any models or data in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
## <a name="best-practice"></a><span data-ttu-id="d6478-115">最佳做法</span><span class="sxs-lookup"><span data-stu-id="d6478-115">Best Practice</span></span>  
 <span data-ttu-id="d6478-116">通常，应将 "**更新**" 权限分配给模型对象，然后将权限显式分配给下的对象。</span><span class="sxs-lookup"><span data-stu-id="d6478-116">In general, you should assign **Update** permission to the model object, and then explicitly assign permission to objects underneath.</span></span> <span data-ttu-id="d6478-117">如果没有分配对模型对象之下对象的权限，将继承权限且用户作为管理员。</span><span class="sxs-lookup"><span data-stu-id="d6478-117">If you do not assign permission to objects underneath, the permissions are inherited and the user is an administrator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6478-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d6478-118">See Also</span></span>  
 <span data-ttu-id="d6478-119">[&#40;Master Data Services 分配模型对象权限&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d6478-119">[Assign Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="d6478-120">[&#40;Master Data Services 的模型权限&#41;](../../2014/master-data-services/model-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d6478-120">[Model Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="d6478-121">[功能区域权限 &#40;Master Data Services&#41;](../../2014/master-data-services/functional-area-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d6478-121">[Functional Area Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/functional-area-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="d6478-122">[层次结构成员权限 &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d6478-122">[Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="d6478-123">如何确定权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d6478-123">How Permissions Are Determined &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
