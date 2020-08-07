---
title: 属性组 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services]
- attribute groups [Master Data Services], about attribute groups
ms.assetid: 648b3d0b-e15a-45f9-8292-3a54a072e62c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 390b402489799639e66a44992da1e20b0d0c1bbf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587461"
---
# <a name="attribute-groups-master-data-services"></a><span data-ttu-id="abad2-102">属性组 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="abad2-102">Attribute Groups (Master Data Services)</span></span>
  <span data-ttu-id="abad2-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，属性组帮助组织实体中的属性。</span><span class="sxs-lookup"><span data-stu-id="abad2-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], attribute groups help organize attributes in an entity.</span></span> <span data-ttu-id="abad2-104">如果实体具有很多属性，属性组可以改进实体在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 应用程序中显示的方式。</span><span class="sxs-lookup"><span data-stu-id="abad2-104">When an entity has lots of attributes, attribute groups improve the way an entity is displayed in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application.</span></span>  
  
## <a name="how-attribute-groups-change-the-display"></a><span data-ttu-id="abad2-105">属性组如何更改显示方式</span><span class="sxs-lookup"><span data-stu-id="abad2-105">How Attribute Groups Change the Display</span></span>  
 <span data-ttu-id="abad2-106">属性组显示为 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 的“资源管理器”\*\*\*\* 功能区域的网格上的选项卡。</span><span class="sxs-lookup"><span data-stu-id="abad2-106">Attribute groups are displayed as tabs above the grid in the **Explorer** functional area of [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
 <span data-ttu-id="abad2-107">在某一实体具有大量属性并且您在 **“资源管理器”** 的网格中查看该实体时，必须向右滚动以便查看所有属性。</span><span class="sxs-lookup"><span data-stu-id="abad2-107">When an entity has a large number of attributes and you view that entity in a grid in **Explorer**, you must scroll to the right to view all of the attributes.</span></span> <span data-ttu-id="abad2-108">若要禁止这一滚动，您可以创建属性组。</span><span class="sxs-lookup"><span data-stu-id="abad2-108">To prevent this scrolling, you can create attribute groups.</span></span>  
  
-   <span data-ttu-id="abad2-109">属性组始终包括 Name 和 Code 属性。</span><span class="sxs-lookup"><span data-stu-id="abad2-109">Attribute groups always include the Name and Code attributes.</span></span>  
  
-   <span data-ttu-id="abad2-110">一个实体的每个属性都可以属于一个或多个属性组。</span><span class="sxs-lookup"><span data-stu-id="abad2-110">Each attribute for an entity can belong to one or more attribute groups.</span></span>  
  
-   <span data-ttu-id="abad2-111">所有属性将自动包含在 **“资源管理器”** 的 **“所有属性”** 选项卡上。</span><span class="sxs-lookup"><span data-stu-id="abad2-111">All attributes are automatically included on the **All Attributes** tab in **Explorer**.</span></span>  
  
-   <span data-ttu-id="abad2-112">没有办法隐藏 **“所有属性”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="abad2-112">There is no way to hide the **All Attributes** tab.</span></span>  
  
 <span data-ttu-id="abad2-113">属性组在 **的** “系统管理” [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]功能区域中进行管理。</span><span class="sxs-lookup"><span data-stu-id="abad2-113">Attribute groups are administered in the **System Administration** functional area of [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
## <a name="show-or-hide-attribute-groups"></a><span data-ttu-id="abad2-114">显示或隐藏属性组</span><span class="sxs-lookup"><span data-stu-id="abad2-114">Show or Hide Attribute Groups</span></span>  
 <span data-ttu-id="abad2-115">创建属性组时，对除创建者之外的所有用户自动隐藏它。</span><span class="sxs-lookup"><span data-stu-id="abad2-115">When you create an attribute group, it is automatically hidden from all users except the one who created it.</span></span> <span data-ttu-id="abad2-116">有关使组可见的详细信息，请参阅 [使属性组对用户可见 (Master Data Services)](make-an-attribute-group-visible-to-users-master-data-services.md)选项卡上。</span><span class="sxs-lookup"><span data-stu-id="abad2-116">For more information about making the group visible, see [Make an Attribute Group Visible to Users &#40;Master Data Services&#41;](make-an-attribute-group-visible-to-users-master-data-services.md).</span></span>  
  
 <span data-ttu-id="abad2-117">如果要隐藏组中的特定属性，可以将 **“拒绝”** 权限分配给该属性。</span><span class="sxs-lookup"><span data-stu-id="abad2-117">If you want to hide a specific attribute within a group, you can assign **Deny** permission to the attribute.</span></span> <span data-ttu-id="abad2-118">有关详细信息，请参阅[叶权限 (Master Data Services)](../../2014/master-data-services/leaf-permissions-master-data-services.md)或[合并的权限 (Master Data Services)](../../2014/master-data-services/consolidated-permissions-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="abad2-118">For more information, see [Leaf Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md) or [Consolidated Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="abad2-119">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="abad2-119">Related Tasks</span></span>  
  
|<span data-ttu-id="abad2-120">任务说明</span><span class="sxs-lookup"><span data-stu-id="abad2-120">Task Description</span></span>|<span data-ttu-id="abad2-121">主题</span><span class="sxs-lookup"><span data-stu-id="abad2-121">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="abad2-122">创建新的属性组并向其中添加属性。</span><span class="sxs-lookup"><span data-stu-id="abad2-122">Create a new attribute group and add attributes to it.</span></span>|[<span data-ttu-id="abad2-123">创建属性组 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="abad2-123">Create an Attribute Group &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)|  
|<span data-ttu-id="abad2-124">使属性组对用户可见。</span><span class="sxs-lookup"><span data-stu-id="abad2-124">Make an attribute group visible to users.</span></span>|[<span data-ttu-id="abad2-125">使属性组对用户可见 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="abad2-125">Make an Attribute Group Visible to Users &#40;Master Data Services&#41;</span></span>](make-an-attribute-group-visible-to-users-master-data-services.md)|  
|<span data-ttu-id="abad2-126">更改现有属性组的名称。</span><span class="sxs-lookup"><span data-stu-id="abad2-126">Change the name of an existing attribute group.</span></span>|[<span data-ttu-id="abad2-127">更改属性组名称 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="abad2-127">Change an Attribute Group Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-an-attribute-group-name-master-data-services.md)|  
|<span data-ttu-id="abad2-128">删除现有属性组。</span><span class="sxs-lookup"><span data-stu-id="abad2-128">Delete an existing attribute group.</span></span>|[<span data-ttu-id="abad2-129">删除属性组 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="abad2-129">Delete an Attribute Group &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-attribute-group-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="abad2-130">相关内容</span><span class="sxs-lookup"><span data-stu-id="abad2-130">Related Content</span></span>  
  
-   [<span data-ttu-id="abad2-131">属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="abad2-131">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
