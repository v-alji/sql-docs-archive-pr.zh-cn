---
title: 删除用户或组 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting groups [Master Data Services]
- groups [Master Data Services], deleting
- users [Master Data Services], deleting
- deleting users [Master Data Services]
ms.assetid: 0bbf9d2c-b826-48bb-8aa9-9905db6e717f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: be302bc974994d0f4f17a8e61244065c76fa93ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590244"
---
# <a name="delete-users-or-groups-master-data-services"></a><span data-ttu-id="3466d-102">删除用户或组 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3466d-102">Delete Users or Groups (Master Data Services)</span></span>
  <span data-ttu-id="3466d-103">在您不再希望用户或组访问 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]时删除它们。</span><span class="sxs-lookup"><span data-stu-id="3466d-103">Delete users or groups when you no longer want them to access [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
 <span data-ttu-id="3466d-104">在删除用户和组时请注意以下行为：</span><span class="sxs-lookup"><span data-stu-id="3466d-104">Note the following behavior when deleting users and groups:</span></span>  
  
-   <span data-ttu-id="3466d-105">如果您删除的用户是有权访问 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]的组的成员，则在您从 Active Directory 或本地组中删除该用户之前，该用户仍能够访问 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3466d-105">If you delete a user who is a member of a group that has access to [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], then the user can still access [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] until you remove the user from the Active Directory or local group.</span></span>  
  
-   <span data-ttu-id="3466d-106">如果您删除某一组，则该组中有权访问 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 的所有用户都将在您删除它们之前显示在 **“用户”** 列表中。</span><span class="sxs-lookup"><span data-stu-id="3466d-106">If you delete a group, all users from the group who have accessed [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] are displayed in the **Users** list until you delete them.</span></span>  
  
-   <span data-ttu-id="3466d-107">对安全性所做的更改在 20 分钟之内不会传播到 MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3466d-107">Changes to security are not propagated to the MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] for 20 minutes.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3466d-108">先决条件</span><span class="sxs-lookup"><span data-stu-id="3466d-108">Prerequisites</span></span>  
 <span data-ttu-id="3466d-109">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="3466d-109">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="3466d-110">您必须有权访问 **“用户和组权限”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="3466d-110">You must have permission to access the **Users and Group Permissions** functional area.</span></span>  
  
-   <span data-ttu-id="3466d-111">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="3466d-111">You must be a model administrator.</span></span> <span data-ttu-id="3466d-112">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3466d-112">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-users-or-groups"></a><span data-ttu-id="3466d-113">删除用户或组</span><span class="sxs-lookup"><span data-stu-id="3466d-113">To delete users or groups</span></span>  
  
1.  <span data-ttu-id="3466d-114">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“用户和组权限”**。</span><span class="sxs-lookup"><span data-stu-id="3466d-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="3466d-115">若要删除某一用户，请保持在 **“用户”** 页上。</span><span class="sxs-lookup"><span data-stu-id="3466d-115">To delete a user, remain on the **Users** page.</span></span> <span data-ttu-id="3466d-116">若要删除某一组，请从菜单栏中单击“管理组”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3466d-116">To delete a group, from the menu bar, click **ManageGroups.**</span></span>  
  
3.  <span data-ttu-id="3466d-117">在网格中，选择你要删除的用户或组所对应的行。</span><span class="sxs-lookup"><span data-stu-id="3466d-117">In the grid,select the row for the user or group that you want to delete.</span></span>  
  
4.  <span data-ttu-id="3466d-118">单击 **“删除所选用户”** 或 **“删除所选组”**。</span><span class="sxs-lookup"><span data-stu-id="3466d-118">Click **Delete selected user** or **Delete selected group**.</span></span>  
  
5.  <span data-ttu-id="3466d-119">在确认对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="3466d-119">On the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3466d-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3466d-120">See Also</span></span>  
 [<span data-ttu-id="3466d-121">安全性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3466d-121">Security &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/security-master-data-services.md)  
  
  
