---
title: 用户和组 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- users [Master Data Services]
- groups [Master Data Services]
- users [Master Data Services], about users
- groups [Master Data Services], about groups
ms.assetid: ed08dd2d-248e-4b68-91d4-e9961cb50eed
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: efad65bf273d58b4f60b98d050a8b99705cb00ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694500"
---
# <a name="users-and-groups-master-data-services"></a><span data-ttu-id="d0001-102">用户和组 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d0001-102">Users and Groups (Master Data Services)</span></span>
  <span data-ttu-id="d0001-103">若要访问 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 应用程序，用户必须具有 Windows 域帐户或者安装了 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 的服务器计算机上的帐户。</span><span class="sxs-lookup"><span data-stu-id="d0001-103">To access the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application a user must have a Windows domain account or an account on the server computer where [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] is installed.</span></span> <span data-ttu-id="d0001-104">要授予对 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 的访问权限，可以执行以下任一操作：</span><span class="sxs-lookup"><span data-stu-id="d0001-104">To grant access to [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] you can either:</span></span>  
  
-   <span data-ttu-id="d0001-105">将用户帐户添加到域组或本地组，再将该组添加到 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中的组列表。</span><span class="sxs-lookup"><span data-stu-id="d0001-105">Add the user account to a domain or local group and then add the group to the list of groups in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
-   <span data-ttu-id="d0001-106">将用户帐户添加到 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中的用户列表。</span><span class="sxs-lookup"><span data-stu-id="d0001-106">Add the user account to the list of users in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d0001-107">如果用户属于具有对 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]的访问权限的组，当该用户第一次访问 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 或 MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]时，自动将其名称添加到用户列表。</span><span class="sxs-lookup"><span data-stu-id="d0001-107">When a user belongs to a group that has access to [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], the user's name is automatically added to the list of users the first time the user accesses [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] or the MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].</span></span>  
  
 <span data-ttu-id="d0001-108">若要在用户界面的 **“资源管理器”** 功能区域中执行操作，必须为组或用户分配对 **“资源管理器”** 功能区域的访问权限以及对模型对象的相应权限。</span><span class="sxs-lookup"><span data-stu-id="d0001-108">To take action within the **Explorer** functional area of the UI, the group or user must be assigned access to the **Explorer** functional area and assigned permission to model objects.</span></span>  
  
 <span data-ttu-id="d0001-109">如果用户或组需要访问其他功能区域，该用户或组必须是管理员。</span><span class="sxs-lookup"><span data-stu-id="d0001-109">If a user or group needs access to other functional areas, the user or group must be an administrator.</span></span> <span data-ttu-id="d0001-110">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d0001-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
## <a name="best-practice"></a><span data-ttu-id="d0001-111">最佳做法</span><span class="sxs-lookup"><span data-stu-id="d0001-111">Best Practice</span></span>  
 <span data-ttu-id="d0001-112">为了简化管理，请创建组并为每个组分配针对功能区域和模型对象的权限。</span><span class="sxs-lookup"><span data-stu-id="d0001-112">To simplify administration, create groups and assign each group permission to functional areas and model objects.</span></span> <span data-ttu-id="d0001-113">然后，您可以从这些组中添加和删除用户，而无需访问 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 用户界面。</span><span class="sxs-lookup"><span data-stu-id="d0001-113">You can then add and remove users from the groups without accessing the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] UI.</span></span>  
  
 <span data-ttu-id="d0001-114">不要向单个用户分配其他权限，也不要将一个用户包括在对 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]具有访问权限的多个组中。</span><span class="sxs-lookup"><span data-stu-id="d0001-114">Do not assign additional permissions to an individual user, and do not include a user in multiple groups that have access to [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span> <span data-ttu-id="d0001-115">此外，不要使用层次结构成员权限，除非您希望某个组对特定成员具有受限的访问权限。</span><span class="sxs-lookup"><span data-stu-id="d0001-115">In addition, do not use hierarchy member permissions unless you want a group to have limited access to specific members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0001-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d0001-116">See Also</span></span>  
 <span data-ttu-id="d0001-117">[添加用户 &#40;Master Data Services&#41;](../../2014/master-data-services/add-a-user-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d0001-117">[Add a User &#40;Master Data Services&#41;](../../2014/master-data-services/add-a-user-master-data-services.md) </span></span>  
 <span data-ttu-id="d0001-118">[添加组 &#40;Master Data Services&#41;](../../2014/master-data-services/add-a-group-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d0001-118">[Add a Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-a-group-master-data-services.md) </span></span>  
 <span data-ttu-id="d0001-119">[删除用户或组 &#40;Master Data Services&#41;](../../2014/master-data-services/delete-users-or-groups-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d0001-119">[Delete Users or Groups &#40;Master Data Services&#41;](../../2014/master-data-services/delete-users-or-groups-master-data-services.md) </span></span>  
 [<span data-ttu-id="d0001-120">测试用户权限 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d0001-120">Test a User's Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/test-a-user-s-permissions-master-data-services.md)  
  
  
