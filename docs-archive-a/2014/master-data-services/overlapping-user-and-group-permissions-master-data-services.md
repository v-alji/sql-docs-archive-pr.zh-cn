---
title: 重叠的用户和组权限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- users [Master Data Services], resolving permissions
- permissions [Master Data Services], user and group overlaps
- groups [Master Data Services], resolving permissions
ms.assetid: 31c3cf7d-17d4-4474-b6a7-ffcb9fc45b37
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7044bf6260170cbc598719ec204ddb6f861f6301
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688964"
---
# <a name="overlapping-user-and-group-permissions-master-data-services"></a><span data-ttu-id="0705d-102">重叠的用户和组权限（主数据服务）</span><span class="sxs-lookup"><span data-stu-id="0705d-102">Overlapping User and Group Permissions (Master Data Services)</span></span>
  <span data-ttu-id="0705d-103">用户的权限基于：</span><span class="sxs-lookup"><span data-stu-id="0705d-103">A user's permissions are based on:</span></span>  
  
-   <span data-ttu-id="0705d-104">来自组成员身份的权限。</span><span class="sxs-lookup"><span data-stu-id="0705d-104">Permissions from group memberships.</span></span>  
  
-   <span data-ttu-id="0705d-105">显式分配给用户的权限。</span><span class="sxs-lookup"><span data-stu-id="0705d-105">Permissions assigned explicitly to the user.</span></span>  
  
 <span data-ttu-id="0705d-106">如果用户是多个组的成员，并且这些组有权访问主数据管理器，则适用以下规则：</span><span class="sxs-lookup"><span data-stu-id="0705d-106">If a user is a member of multiple groups, and those groups have access to Master Data Manager, the following rules apply:</span></span>  
  
-   <span data-ttu-id="0705d-107">**“拒绝”** 覆盖所有其他权限。</span><span class="sxs-lookup"><span data-stu-id="0705d-107">**Deny** overrides all other permissions.</span></span>  
  
-   <span data-ttu-id="0705d-108">**更新**替代**为只读**。</span><span class="sxs-lookup"><span data-stu-id="0705d-108">**Update** overrides **Read-only**.</span></span>  
  
 <span data-ttu-id="0705d-109">这些规则应用到 **“模型”** 和 **“层次结构成员”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="0705d-109">These rules apply to both the **Models** and **Hierarchy Members** tabs.</span></span> <span data-ttu-id="0705d-110">先为每个选项卡确定权限，再将权限进行组合。</span><span class="sxs-lookup"><span data-stu-id="0705d-110">Permissions are resolved for each tab and then combined.</span></span> <span data-ttu-id="0705d-111">有关详细信息，请参阅 [如何确定权限 (Master Data Services)](how-permissions-are-determined-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="0705d-111">For more information, see [How Permissions Are Determined &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0705d-112">可以在用户界面中查看用户和组的重叠权限的解决方法。</span><span class="sxs-lookup"><span data-stu-id="0705d-112">You can view the resolution of user and group overlapping permissions in the user interface.</span></span> <span data-ttu-id="0705d-113">“模型”\*\*\*\* 和“层次结构成员”\*\*\*\* 选项卡都具有下拉列表，可以从中选择“有效”\*\*\*\*，查看有效权限。</span><span class="sxs-lookup"><span data-stu-id="0705d-113">Both the **Models** and **Hierarchy Members** tab have a drop-down list from which you can choose **Effective** to view effective permissions.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="0705d-114">示例 1</span><span class="sxs-lookup"><span data-stu-id="0705d-114">Example 1</span></span>  
 <span data-ttu-id="0705d-115">![mds_conc_user_group_ex_1](../../2014/master-data-services/media/mds-conc-user-group-ex-1.gif "mds_conc_user_group_ex_1")</span><span class="sxs-lookup"><span data-stu-id="0705d-115">![mds_conc_user_group_ex_1](../../2014/master-data-services/media/mds-conc-user-group-ex-1.gif "mds_conc_user_group_ex_1")</span></span>  
  
 <span data-ttu-id="0705d-116">用户同时属于组 1 和组 2。</span><span class="sxs-lookup"><span data-stu-id="0705d-116">The user belongs to Group 1 and Group 2.</span></span>  
  
 <span data-ttu-id="0705d-117">用户对 Product 实体具有 "**只读**" 权限。</span><span class="sxs-lookup"><span data-stu-id="0705d-117">The user has **Read-only** permission to the Product entity.</span></span>  
  
 <span data-ttu-id="0705d-118">组 1 对 Product 实体具有 **“更新”** 权限。</span><span class="sxs-lookup"><span data-stu-id="0705d-118">Group 1 has **Update** permission to the Product entity.</span></span>  
  
 <span data-ttu-id="0705d-119">组2对 Product 实体具有 "**只读**" 权限。</span><span class="sxs-lookup"><span data-stu-id="0705d-119">Group 2 has **Read-only** permission to the Product entity.</span></span>  
  
 <span data-ttu-id="0705d-120">结果：用户对 Product 实体的有效权限是 **“更新”** 。</span><span class="sxs-lookup"><span data-stu-id="0705d-120">Result: The user's effective permission is **Update** to the Product entity.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="0705d-121">示例 2</span><span class="sxs-lookup"><span data-stu-id="0705d-121">Example 2</span></span>  
 <span data-ttu-id="0705d-122">![mds_conc_user_group_ex_2](../../2014/master-data-services/media/mds-conc-user-group-ex-2.gif "mds_conc_user_group_ex_2")</span><span class="sxs-lookup"><span data-stu-id="0705d-122">![mds_conc_user_group_ex_2](../../2014/master-data-services/media/mds-conc-user-group-ex-2.gif "mds_conc_user_group_ex_2")</span></span>  
  
 <span data-ttu-id="0705d-123">用户同时属于组 1 和组 2。</span><span class="sxs-lookup"><span data-stu-id="0705d-123">The user belongs to Group 1 and Group 2.</span></span>  
  
 <span data-ttu-id="0705d-124">用户对 Product 实体具有 "**只读**" 权限。</span><span class="sxs-lookup"><span data-stu-id="0705d-124">The user has **Read-only** permission to the Product entity.</span></span>  
  
 <span data-ttu-id="0705d-125">组 1 对 Product 实体具有 **“更新”** 权限。</span><span class="sxs-lookup"><span data-stu-id="0705d-125">Group 1 has **Update** permission to Product entity.</span></span>  
  
 <span data-ttu-id="0705d-126">组 2 对 Product 实体具有 **“拒绝”** 权限。</span><span class="sxs-lookup"><span data-stu-id="0705d-126">Group 2 has **Deny** permission to the Product entity.</span></span>  
  
 <span data-ttu-id="0705d-127">结果：用户对 Product 实体的有效权限是 **“拒绝”** 。</span><span class="sxs-lookup"><span data-stu-id="0705d-127">Result: The user's effective permission is **Deny** to the Product entity.</span></span>  
  
## <a name="example-3"></a><span data-ttu-id="0705d-128">示例 3</span><span class="sxs-lookup"><span data-stu-id="0705d-128">Example 3</span></span>  
 <span data-ttu-id="0705d-129">![mds_conc_user_group_ex_3](../../2014/master-data-services/media/mds-conc-user-group-ex-3.gif "mds_conc_user_group_ex_3")</span><span class="sxs-lookup"><span data-stu-id="0705d-129">![mds_conc_user_group_ex_3](../../2014/master-data-services/media/mds-conc-user-group-ex-3.gif "mds_conc_user_group_ex_3")</span></span>  
  
 <span data-ttu-id="0705d-130">用户同时属于组 1 和组 2。</span><span class="sxs-lookup"><span data-stu-id="0705d-130">The user belongs to Group 1 and Group 2.</span></span>  
  
 <span data-ttu-id="0705d-131">用户对层次结构节点中的一组成员具有 **“更新”** 权限。</span><span class="sxs-lookup"><span data-stu-id="0705d-131">The user has **Update** permission to a group of members in a hierarchy node.</span></span>  
  
 <span data-ttu-id="0705d-132">组1对层次结构节点中的一组成员具有**只读**权限。</span><span class="sxs-lookup"><span data-stu-id="0705d-132">Group 1 has **Read-only** permission to a group of members in a hierarchy node.</span></span>  
  
 <span data-ttu-id="0705d-133">组2对层次结构节点中的一组成员具有**只读**权限。</span><span class="sxs-lookup"><span data-stu-id="0705d-133">Group 2 has **Read-only** permission to a group of members in a hierarchy node.</span></span>  
  
 <span data-ttu-id="0705d-134">结果：用户对这些成员的有效权限是 **“更新”** 。</span><span class="sxs-lookup"><span data-stu-id="0705d-134">Result: The user's effective permission is **Update** to the members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0705d-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0705d-135">See Also</span></span>  
 <span data-ttu-id="0705d-136">[如何 Master Data Services &#40;确定权限&#41;](how-permissions-are-determined-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="0705d-136">[How Permissions Are Determined &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md) </span></span>  
 [<span data-ttu-id="0705d-137">重叠的模型和成员权限 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0705d-137">Overlapping Model and Member Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md)  
  
  
