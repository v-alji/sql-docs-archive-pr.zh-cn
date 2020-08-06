---
title: 删除层次结构成员权限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting member permissions [Master Data Services]
- members [Master Data Services], deleting permissions
- permissions [Master Data Services], deleting member permissions
ms.assetid: 7f22d5e2-70c1-422c-99c2-e995a47d812a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8b6e7fbfc4379733d5cb809ce4d46d2c12d05a48
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689496"
---
# <a name="delete-hierarchy-member-permissions-master-data-services"></a><span data-ttu-id="7fc94-102">删除层次结构成员权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="7fc94-102">Delete Hierarchy Member Permissions (Master Data Services)</span></span>
  <span data-ttu-id="7fc94-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，删除模型对象权限可以删除已进行的任何分配。</span><span class="sxs-lookup"><span data-stu-id="7fc94-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete model object permissions to remove any assignments that have been made.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7fc94-104">先决条件</span><span class="sxs-lookup"><span data-stu-id="7fc94-104">Prerequisites</span></span>  
 <span data-ttu-id="7fc94-105">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="7fc94-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="7fc94-106">您必须有权访问 **“用户和组权限”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="7fc94-106">You must have permission to access the **Users and Group Permissions** functional area.</span></span>  
  
-   <span data-ttu-id="7fc94-107">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="7fc94-107">You must be a model administrator.</span></span> <span data-ttu-id="7fc94-108">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7fc94-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-hierarchy-member-permissions"></a><span data-ttu-id="7fc94-109">删除层次结构成员权限</span><span class="sxs-lookup"><span data-stu-id="7fc94-109">To delete hierarchy member permissions</span></span>  
  
1.  <span data-ttu-id="7fc94-110">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“用户和组权限”**。</span><span class="sxs-lookup"><span data-stu-id="7fc94-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="7fc94-111">在 **“用户”** 或 **“组”** 页上，选择要编辑的用户或组所对应的行。</span><span class="sxs-lookup"><span data-stu-id="7fc94-111">On the **Users** or **Groups** page, select the row for the user or group that you want to edit.</span></span>  
  
3.  <span data-ttu-id="7fc94-112">单击 **“编辑所选用户”**。</span><span class="sxs-lookup"><span data-stu-id="7fc94-112">Click **Edit selected user**.</span></span>  
  
4.  <span data-ttu-id="7fc94-113">单击 **“层次结构成员”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="7fc94-113">Click the **Hierarchy Members** tab.</span></span>  
  
5.  <span data-ttu-id="7fc94-114">从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="7fc94-114">From the **Model** list, select a model.</span></span>  
  
6.  <span data-ttu-id="7fc94-115">\*\*\*\* 从“版本”列表中，选择某一版本。</span><span class="sxs-lookup"><span data-stu-id="7fc94-115">From the **Version** list, select a version.</span></span>  
  
7.  <span data-ttu-id="7fc94-116">在 "**层次结构成员权限摘要**" 窗格中，选择要删除的权限所在的行。</span><span class="sxs-lookup"><span data-stu-id="7fc94-116">In the **Hierarchy Member Permission Summary** pane, select the row for the permission that you want to delete.</span></span>  
  
8.  <span data-ttu-id="7fc94-117">单击 "**删除所选权限**"。</span><span class="sxs-lookup"><span data-stu-id="7fc94-117">Click **Delete selected permission**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7fc94-118">如果权限继承自一个组，则不能从用户删除该权限。</span><span class="sxs-lookup"><span data-stu-id="7fc94-118">You cannot remove a permission from a user if the permission is inherited from a group.</span></span> <span data-ttu-id="7fc94-119">而是必须从该组删除该权限。</span><span class="sxs-lookup"><span data-stu-id="7fc94-119">You must remove the permission from the group instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fc94-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7fc94-120">See Also</span></span>  
 <span data-ttu-id="7fc94-121">[层次结构成员权限 &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="7fc94-121">[Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="7fc94-122">分配层次结构成员权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="7fc94-122">Assign Hierarchy Member Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)  
  
  
