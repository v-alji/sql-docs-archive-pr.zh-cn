---
title: 层次结构成员权限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- members [Master Data Services], permissions
- permissions [Master Data Services], members
ms.assetid: b3880eed-1bf6-4f65-ab23-b08c194cc858
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 81716dbd0ad08b6e92a2edb8f1d142b46bf3d24d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587879"
---
# <a name="hierarchy-member-permissions-master-data-services"></a><span data-ttu-id="eb131-102">层次结构成员权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="eb131-102">Hierarchy Member Permissions (Master Data Services)</span></span>
  <span data-ttu-id="eb131-103">层次结构成员权限是可选的，仅当您希望某个用户对特定成员具有受限的访问权限时才应使用。</span><span class="sxs-lookup"><span data-stu-id="eb131-103">Hierarchy member permissions are optional and should be used only when you want a user to have limited access to specific members.</span></span> <span data-ttu-id="eb131-104">如果您未在 **“层次结构成员”** 选项卡上分配权限，则用户的权限仅基于在 **“模型”** 选项卡上分配的权限。</span><span class="sxs-lookup"><span data-stu-id="eb131-104">If you do not assign permissions on the **Hierarchy Members** tab, then the user's permissions are based solely on the permissions assigned on the **Models** tab.</span></span>  
  
 <span data-ttu-id="eb131-105">层次结构成员权限在 " [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **层次结构成员**" 选项卡上的 "**用户和组权限**" 功能区域 (UI) 中分配。这些权限确定用户在用户界面的 "**资源管理器**" 功能区域中可以访问哪些成员。</span><span class="sxs-lookup"><span data-stu-id="eb131-105">Hierarchy member permissions are assigned in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] user interface (UI), in the **User and Group Permissions** functional area on the **Hierarchy Members** tab. These permissions determine which members a user can access in the **Explorer** functional area of the UI.</span></span>  
  
 <span data-ttu-id="eb131-106">在 **“层次结构成员”** 选项卡上，每个层次结构均表示为一个树形结构。</span><span class="sxs-lookup"><span data-stu-id="eb131-106">On the **Hierarchy Members** tab, each hierarchy is represented as a tree structure.</span></span> <span data-ttu-id="eb131-107">将权限分配给树中的节点时，所有子节点都将继承该权限，除非在更低级别显式分配权限。</span><span class="sxs-lookup"><span data-stu-id="eb131-107">When you assign permission to a node in the tree, all children inherit that permission unless permission is explicitly assigned at a lower level.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="eb131-108">如果向层次结构中的节点分配权限，则处于同一级别或更高级别的其他节点中的所有成员都将被隐式拒绝。</span><span class="sxs-lookup"><span data-stu-id="eb131-108">When you assign permission to a node in a hierarchy, all members in other nodes at the same level or higher are implicitly denied.</span></span>  
  
 <span data-ttu-id="eb131-109">在 **“资源管理器”** 中，将成员权限应用到显示成员的任何位置。</span><span class="sxs-lookup"><span data-stu-id="eb131-109">In **Explorer**, the member permissions are applied everywhere the member is displayed.</span></span> <span data-ttu-id="eb131-110">例如，具有**只读**权限的成员在它所属的任何实体、层次结构和集合中都是只读的。</span><span class="sxs-lookup"><span data-stu-id="eb131-110">For example, a member with **Read-only** permission is read-only in any entities, hierarchies, and collections to which it belongs.</span></span>  
  
 <span data-ttu-id="eb131-111">层次结构权限应用于您向其分配权限的模型版本，并应用于版本的任何将来副本。</span><span class="sxs-lookup"><span data-stu-id="eb131-111">Hierarchy member permissions apply to the model version you assign them to, and to any future copies of the version.</span></span> <span data-ttu-id="eb131-112">它们不应用于比您向其分配权限的版本更早的版本。</span><span class="sxs-lookup"><span data-stu-id="eb131-112">They do not apply to versions earlier than the one you assign them to.</span></span>  
  
|<span data-ttu-id="eb131-113">权限</span><span class="sxs-lookup"><span data-stu-id="eb131-113">Permission</span></span>|<span data-ttu-id="eb131-114">说明</span><span class="sxs-lookup"><span data-stu-id="eb131-114">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="eb131-115">**只读**</span><span class="sxs-lookup"><span data-stu-id="eb131-115">**Read-only**</span></span>|<span data-ttu-id="eb131-116">显示成员，但是用户不能更改它们。</span><span class="sxs-lookup"><span data-stu-id="eb131-116">The members are displayed but the user cannot change them.</span></span> <span data-ttu-id="eb131-117">用户也无法在成员所属的任何显式层次结构或集合中移动成员。</span><span class="sxs-lookup"><span data-stu-id="eb131-117">The user also cannot move the members in any explicit hierarchies or collections that the members belong to.</span></span><br /><br /> <span data-ttu-id="eb131-118">注意：如果将**只读**权限分配给**Root**，则**root**下的成员是只读的;但是，在显式层次结构和集合中，用户可以将成员移到**根节点**，并可以将新成员添加到**根**。</span><span class="sxs-lookup"><span data-stu-id="eb131-118">Note: If you assign **Read-only** permission to **Root**, the members under **Root** are read-only; however, in explicit hierarchies and collections, the user can move members to **Root** and can add new members to **Root**.</span></span>|  
|<span data-ttu-id="eb131-119">**更新**</span><span class="sxs-lookup"><span data-stu-id="eb131-119">**Update**</span></span>|<span data-ttu-id="eb131-120">显示成员，用户可以更改它们。</span><span class="sxs-lookup"><span data-stu-id="eb131-120">The members are displayed and the user can change them.</span></span> <span data-ttu-id="eb131-121">用户还可以在成员所属的任何显式层次结构或集合中移动成员。</span><span class="sxs-lookup"><span data-stu-id="eb131-121">The user can also move the members in any explicit hierarchies or collections the members belong to.</span></span>|  
|<span data-ttu-id="eb131-122">**拒绝**</span><span class="sxs-lookup"><span data-stu-id="eb131-122">**Deny**</span></span>|<span data-ttu-id="eb131-123">不显示成员。</span><span class="sxs-lookup"><span data-stu-id="eb131-123">The members are not displayed.</span></span>|  
  
 <span data-ttu-id="eb131-124">在 **“层次结构成员”** 选项卡上，分配的权限不立即生效。</span><span class="sxs-lookup"><span data-stu-id="eb131-124">On the **Hierarchy Members** tab, the permissions you assign do not take effect immediately.</span></span> <span data-ttu-id="eb131-125">应用该权限的频率取决于 **数据库中“系统设置”表的** “成员安全处理间隔设置” [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="eb131-125">The frequency that the permissions are applied depends on the **Member security processing interval setting** in the System Settings table in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="eb131-126">可以按照 [立即应用成员权限 (Master Data Services)](immediately-apply-member-permissions-master-data-services.md)中的以下步骤立即应用成员权限。</span><span class="sxs-lookup"><span data-stu-id="eb131-126">You can apply member permissions immediately by following the steps in [Immediately Apply Member Permissions &#40;Master Data Services&#41;](immediately-apply-member-permissions-master-data-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="eb131-127">不能将层次结构成员权限分配给递归层次结构、具有显式顶端的派生层次结构和具有隐藏级别的层次结构。</span><span class="sxs-lookup"><span data-stu-id="eb131-127">You cannot assign hierarchy member permissions to recursive hierarchies, derived hierarchies with explicit caps, and derived hierarchies with hidden levels.</span></span>  
  
## <a name="possible-overlapping-permissions"></a><span data-ttu-id="eb131-128">可能重叠的权限</span><span class="sxs-lookup"><span data-stu-id="eb131-128">Possible Overlapping Permissions</span></span>  
 <span data-ttu-id="eb131-129">给成员分配权限时，必须解决重叠的权限问题。</span><span class="sxs-lookup"><span data-stu-id="eb131-129">When assigning permission to members, you may have to resolve overlapping permissions.</span></span>  
  
### <a name="when-a-member-belongs-to-multiple-hierarchies"></a><span data-ttu-id="eb131-130">成员属于多个层次结构时</span><span class="sxs-lookup"><span data-stu-id="eb131-130">When a member belongs to multiple hierarchies</span></span>  
 <span data-ttu-id="eb131-131">两个或多个层次结构可以包含同一成员。</span><span class="sxs-lookup"><span data-stu-id="eb131-131">Two or more hierarchies can contain the same member.</span></span>  
  
-   <span data-ttu-id="eb131-132">如果为一个层次结构节点分配了 "**更新**" 权限，而另一个层次结构节点分配了 "**只读**"，则该节点中的成员为**只读**。</span><span class="sxs-lookup"><span data-stu-id="eb131-132">If one hierarchy node is assigned **Update** permission and another is assigned **Read-only**, then the members in the node are **Read-only**.</span></span>  
  
-   <span data-ttu-id="eb131-133">如果为一个层次结构节点分配了 "**更新**" 或 "**只读**" 权限，并且向另一个节点分配了 "**拒绝**" 权限，则不会显示该节点中的成员。</span><span class="sxs-lookup"><span data-stu-id="eb131-133">If one hierarchy node is assigned **Update** or **Read-only** permission and another node is assigned **Deny**, then the members in the node are not displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb131-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eb131-134">See Also</span></span>  
 <span data-ttu-id="eb131-135">[将层次结构成员权限分配 &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="eb131-135">[Assign Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="eb131-136">[如何 Master Data Services &#40;确定权限&#41;](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="eb131-136">[How Permissions Are Determined &#40;Master Data Services&#41;](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md) </span></span>  
 <span data-ttu-id="eb131-137">[成员 &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="eb131-137">[Members &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span></span>  
 <span data-ttu-id="eb131-138">[层次结构 &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="eb131-138">[Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchies-master-data-services.md) </span></span>  
 [<span data-ttu-id="eb131-139">立即应用成员权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="eb131-139">Immediately Apply Member Permissions &#40;Master Data Services&#41;</span></span>](immediately-apply-member-permissions-master-data-services.md)  
  
  
