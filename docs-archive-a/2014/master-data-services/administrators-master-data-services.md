---
title: 管理员 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], about administrators
- administrators [Master Data Services]
- models [Master Data Services], administrators
ms.assetid: d330aa4e-6ade-4b09-b376-1b15d6c78f7d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 52e16d4e77acc0a6b50b87e00184918cb9ce64b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690694"
---
# <a name="administrators-master-data-services"></a><span data-ttu-id="118b1-102">管理员 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="118b1-102">Administrators (Master Data Services)</span></span>
  <span data-ttu-id="118b1-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中有两种类型的管理员：模型管理员和 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 系统管理员。</span><span class="sxs-lookup"><span data-stu-id="118b1-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], there are two types of administrators: model administrators, and the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] system administrator.</span></span>  
  
## <a name="model-administrators"></a><span data-ttu-id="118b1-104">模型管理员</span><span class="sxs-lookup"><span data-stu-id="118b1-104">Model Administrators</span></span>  
 <span data-ttu-id="118b1-105">在中 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ，模型管理员是对 "**模型对象**" 选项卡上的顶级模型对象具有 "**更新**" 权限且未分配其他任何权限的用户。</span><span class="sxs-lookup"><span data-stu-id="118b1-105">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a model administrator is a user who has **Update** permission assigned to the top-level model object on the **Model Objects** tab and no other assigned permissions.</span></span>  
  
-   <span data-ttu-id="118b1-106">如果用户具有对 **“资源管理器”** 功能区域的访问权限，此用户可以添加、删除和更新此区域中的所有主数据。</span><span class="sxs-lookup"><span data-stu-id="118b1-106">If the user has access to the **Explorer** functional area, the user can add, delete, and update all master data in this area.</span></span>  
  
-   <span data-ttu-id="118b1-107">如果用户具有对其他功能区域的访问权限，则此用户可以执行该功能区域中的所有管理任务。</span><span class="sxs-lookup"><span data-stu-id="118b1-107">If the user has access to other functional areas, the user can perform all administrative tasks available in the functional area.</span></span>  
  
 <span data-ttu-id="118b1-108">每个模型可以有多个管理员。</span><span class="sxs-lookup"><span data-stu-id="118b1-108">Each model can have multiple administrators.</span></span> <span data-ttu-id="118b1-109">每个用户可以是 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 部署中一个、多个或所有模型的模型管理员。</span><span class="sxs-lookup"><span data-stu-id="118b1-109">Each user can be a model administrator for one, several, or all models in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] deployment.</span></span>  
  
 <span data-ttu-id="118b1-110">可以在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 中或通过编程方式将用户配置为模型管理员。</span><span class="sxs-lookup"><span data-stu-id="118b1-110">A user can be configured as a model administrator either in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] or programmatically.</span></span> <span data-ttu-id="118b1-111">有关详细信息，请参阅 [创建模型管理员 (Master Data Services)](create-a-model-administrator-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="118b1-111">For more information, see [Create a Model Administrator &#40;Master Data Services&#41;](create-a-model-administrator-master-data-services.md).</span></span>  
  
## <a name="master-data-services-system-administrator"></a><span data-ttu-id="118b1-112">Master Data Services 系统管理员</span><span class="sxs-lookup"><span data-stu-id="118b1-112">Master Data Services System Administrator</span></span>  
 <span data-ttu-id="118b1-113">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 系统管理员只有一个。</span><span class="sxs-lookup"><span data-stu-id="118b1-113">There is only one [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] system administrator.</span></span> <span data-ttu-id="118b1-114">系统管理员是在创建数据库时为**管理员帐户**指定的用户 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="118b1-114">The system administrator is the user specified for the **Administrator Account** when you create the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
 <span data-ttu-id="118b1-115">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 系统管理员：</span><span class="sxs-lookup"><span data-stu-id="118b1-115">The [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] system administrator:</span></span>  
  
-   <span data-ttu-id="118b1-116">自动对所有功能区域具有访问权限。</span><span class="sxs-lookup"><span data-stu-id="118b1-116">Automatically has access to all functional areas.</span></span>  
  
-   <span data-ttu-id="118b1-117">可以添加、删除和更新 "**资源管理器**" 功能区域中所有模型的所有主数据。</span><span class="sxs-lookup"><span data-stu-id="118b1-117">Can add, delete, and update all master data for all models in the **Explorer** functional area.</span></span>  
  
 <span data-ttu-id="118b1-118">您可以更改指派为系统管理员的用户。</span><span class="sxs-lookup"><span data-stu-id="118b1-118">You can change the user who is assigned as the system administrator.</span></span> <span data-ttu-id="118b1-119">有关详细信息，请参阅[&#40;Master Data Services&#41;更改系统管理员帐户](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="118b1-119">For more information, see [Change the System Administrator Account &#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md).</span></span>  
  
## <a name="comparing-administrator-types"></a><span data-ttu-id="118b1-120">比较管理员类型</span><span class="sxs-lookup"><span data-stu-id="118b1-120">Comparing Administrator Types</span></span>  
  
|<span data-ttu-id="118b1-121">管理员类型</span><span class="sxs-lookup"><span data-stu-id="118b1-121">Administrator Type</span></span>|<span data-ttu-id="118b1-122">说明</span><span class="sxs-lookup"><span data-stu-id="118b1-122">Description</span></span>|  
|------------------------|-----------------|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] <span data-ttu-id="118b1-123">系统管理员</span><span class="sxs-lookup"><span data-stu-id="118b1-123">system administrator</span></span>|<span data-ttu-id="118b1-124">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 中分配的权限对于管理员的访问权限没有影响。</span><span class="sxs-lookup"><span data-stu-id="118b1-124">Permissions assigned in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] have no effect on the administrator's access.</span></span><br /><br /> <span data-ttu-id="118b1-125">自动对所有模型具有 "**更新**" 权限。</span><span class="sxs-lookup"><span data-stu-id="118b1-125">Automatically has **Update** permission to all models.</span></span><br /><br /> <span data-ttu-id="118b1-126">自动对所有功能区域具有访问权限。</span><span class="sxs-lookup"><span data-stu-id="118b1-126">Automatically has access to all functional areas.</span></span><br /><br /> <span data-ttu-id="118b1-127">在 tblUser 中， **ID**列中的值为**1**。</span><span class="sxs-lookup"><span data-stu-id="118b1-127">In mdm.tblUser, the value in the **ID** column is **1**.</span></span>|  
|<span data-ttu-id="118b1-128">模型管理员</span><span class="sxs-lookup"><span data-stu-id="118b1-128">Model administrator</span></span>|<span data-ttu-id="118b1-129">在[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中分配的权限确定用户是否为模型管理员。</span><span class="sxs-lookup"><span data-stu-id="118b1-129">Permissions assigned in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] determine whether or not the user is a model administrator.</span></span><br /><br /> <span data-ttu-id="118b1-130">基于显式分配的权限或者从组继承的权限，用户可以是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="118b1-130">Can be a model administrator based on permissions assigned explicitly or permissions inherited from a group.</span></span><br /><br /> <span data-ttu-id="118b1-131">仅适用于具有分配给顶级模型对象的 "**更新**" 权限且没有其他权限的模型的管理员。</span><span class="sxs-lookup"><span data-stu-id="118b1-131">Is an administrator only for models that have **Update** permission assigned to top-level model object, and no other permissions.</span></span><br /><br /> <span data-ttu-id="118b1-132">仅对向其分配访问权限的功能区域具有访问权限。</span><span class="sxs-lookup"><span data-stu-id="118b1-132">Has access only to functional areas that access is granted to.</span></span><br /><br /> <span data-ttu-id="118b1-133">在 tblUser 中， **ID**列中的值不是**1**。</span><span class="sxs-lookup"><span data-stu-id="118b1-133">In mdm.tblUser, the value in the **ID** column is not **1**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="118b1-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="118b1-134">See Also</span></span>  
 <span data-ttu-id="118b1-135">[创建模型管理员 &#40;Master Data Services&#41;](create-a-model-administrator-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="118b1-135">[Create a Model Administrator &#40;Master Data Services&#41;](create-a-model-administrator-master-data-services.md) </span></span>  
 <span data-ttu-id="118b1-136">[更改系统管理员帐户 &#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="118b1-136">[Change the System Administrator Account &#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md) </span></span>  
 <span data-ttu-id="118b1-137">[创建 Master Data Services 数据库](install-windows/create-a-master-data-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="118b1-137">[Create a Master Data Services Database](install-windows/create-a-master-data-services-database.md) </span></span>  
 [<span data-ttu-id="118b1-138">通知 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="118b1-138">Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/notifications-master-data-services.md)  
  
  
