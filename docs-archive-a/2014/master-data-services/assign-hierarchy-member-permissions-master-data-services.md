---
title: 分配层次结构成员权限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], assigning member permissions
- members [Master Data Services], assigning permissions
ms.assetid: e1b8b46a-7cd1-4a7d-9345-dd7df081e145
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 4a1602f9fe351f826b63d4447f90dcf02a10f49e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587478"
---
# <a name="assign-hierarchy-member-permissions-master-data-services"></a><span data-ttu-id="b965f-102">分配层次结构成员权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b965f-102">Assign Hierarchy Member Permissions (Master Data Services)</span></span>
  <span data-ttu-id="b965f-103">向层次结构成员分配权限，以便使用户或组具有在 **的** “资源管理器” [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]功能区域中查看数据的权限。</span><span class="sxs-lookup"><span data-stu-id="b965f-103">Assign permissions to hierarchy members to give users or groups access to view data in the **Explorer** functional area of [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
 <span data-ttu-id="b965f-104">层次结构成员权限是可选的。</span><span class="sxs-lookup"><span data-stu-id="b965f-104">Hierarchy member permissions are optional.</span></span> <span data-ttu-id="b965f-105">它们增加了模型对象权限所需的粒度。</span><span class="sxs-lookup"><span data-stu-id="b965f-105">They provide added granularity to model object permissions, which are required.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b965f-106">必备条件</span><span class="sxs-lookup"><span data-stu-id="b965f-106">Prerequisites</span></span>  
 <span data-ttu-id="b965f-107">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="b965f-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="b965f-108">您必须有权访问 **“用户和组权限”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="b965f-108">You must have permission to access the **Users and Group Permissions** functional area.</span></span>  
  
-   <span data-ttu-id="b965f-109">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="b965f-109">You must be a model administrator.</span></span> <span data-ttu-id="b965f-110">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b965f-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-assign-hierarchy-member-permissions"></a><span data-ttu-id="b965f-111">分配层次结构成员权限</span><span class="sxs-lookup"><span data-stu-id="b965f-111">To assign hierarchy member permissions</span></span>  
  
1.  <span data-ttu-id="b965f-112">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“用户和组权限”**。</span><span class="sxs-lookup"><span data-stu-id="b965f-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="b965f-113">在 **“用户”** 或 **“组”** 页上，选择要编辑的用户或组所对应的行。</span><span class="sxs-lookup"><span data-stu-id="b965f-113">On the **Users** or **Groups** page, select the row for the user or group that you want to edit.</span></span>  
  
3.  <span data-ttu-id="b965f-114">单击 **“编辑所选用户”**。</span><span class="sxs-lookup"><span data-stu-id="b965f-114">Click **Edit selected user**.</span></span>  
  
4.  <span data-ttu-id="b965f-115">单击 **“层次结构成员”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="b965f-115">Click the **Hierarchy Members** tab.</span></span>  
  
5.  <span data-ttu-id="b965f-116">从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="b965f-116">From the **Model** list, select a model.</span></span>  
  
6.  <span data-ttu-id="b965f-117">\*\*\*\* 从“版本”列表中，选择某一版本。</span><span class="sxs-lookup"><span data-stu-id="b965f-117">From the **Version** list, select a version.</span></span>  
  
7.  <span data-ttu-id="b965f-118">从 **“层次结构”** 列表中，选择某一层次结构。</span><span class="sxs-lookup"><span data-stu-id="b965f-118">From the **Hierarchy** list, select a hierarchy.</span></span>  
  
8.  <span data-ttu-id="b965f-119">单击 **“编辑”** 。</span><span class="sxs-lookup"><span data-stu-id="b965f-119">Click **Edit**.</span></span>  
  
9. <span data-ttu-id="b965f-120">展开树，单击要向其分配权限的层次结构节点。</span><span class="sxs-lookup"><span data-stu-id="b965f-120">Expand the tree, and click the hierarchy node you want to assign permissions to.</span></span>  
  
10. <span data-ttu-id="b965f-121">从菜单中，选择 "**只读**"、"**更新**" 或 "**拒绝**"。</span><span class="sxs-lookup"><span data-stu-id="b965f-121">From the menu, select **Read-only**, **Update**, or **Deny**.</span></span>  
  
11. <span data-ttu-id="b965f-122">单击 **“保存”** 。</span><span class="sxs-lookup"><span data-stu-id="b965f-122">Click **Save**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b965f-123">层次结构成员权限不立即生效。</span><span class="sxs-lookup"><span data-stu-id="b965f-123">Hierarchy member permissions do not take effect immediately.</span></span> <span data-ttu-id="b965f-124">有关详细信息，请参阅[立即应用成员权限 (Master Data Services)](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b965f-124">See [Immediately Apply Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md) for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b965f-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b965f-125">See Also</span></span>  
 <span data-ttu-id="b965f-126">[Master Data Services &#40;删除层次结构成员权限&#41;](../../2014/master-data-services/delete-hierarchy-member-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="b965f-126">[Delete Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/delete-hierarchy-member-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="b965f-127">[&#40;Master Data Services 分配模型对象权限&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="b965f-127">[Assign Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="b965f-128">层次结构成员权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b965f-128">Hierarchy Member Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
