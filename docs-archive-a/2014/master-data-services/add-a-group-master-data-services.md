---
title: 添加组 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- groups [Master Data Services], adding
- adding groups [Master Data Services]
ms.assetid: c7a88381-3b2c-4af7-9cf7-3a930c1abdee
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8f9da1d558ccb648af8fbc0dd3b802751bd5ae44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691774"
---
# <a name="add-a-group-master-data-services"></a><span data-ttu-id="3dfa2-102">添加组 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3dfa2-102">Add a Group (Master Data Services)</span></span>
  <span data-ttu-id="3dfa2-103">在 **中将某一组添加到** “组” [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 列表中，以便开始向 Web 应用程序分配权限。</span><span class="sxs-lookup"><span data-stu-id="3dfa2-103">Add a group to the **Groups** list in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] to begin the process of assigning permission to the Web application.</span></span> <span data-ttu-id="3dfa2-104">在该组中的某一用户可以访问 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]之前，必须为该组提供针对一个或多个功能区域和模型对象的权限。</span><span class="sxs-lookup"><span data-stu-id="3dfa2-104">Before a user in the group can access [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], you must give the group permission to one or more functional areas and model objects.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3dfa2-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="3dfa2-105">Prerequisites</span></span>  
 <span data-ttu-id="3dfa2-106">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="3dfa2-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="3dfa2-107">您必须有权访问 **“用户和组权限”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="3dfa2-107">You must have permission to access the **Users and Group Permissions** functional area.</span></span>  
  
### <a name="to-add-a-group"></a><span data-ttu-id="3dfa2-108">添加组</span><span class="sxs-lookup"><span data-stu-id="3dfa2-108">To add a group</span></span>  
  
1.  <span data-ttu-id="3dfa2-109">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“用户和组权限”**。</span><span class="sxs-lookup"><span data-stu-id="3dfa2-109">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="3dfa2-110">在 **“用户”** 页上，从菜单栏中，单击 **“管理组”**。</span><span class="sxs-lookup"><span data-stu-id="3dfa2-110">On the **Users** page, from the menu bar, click **Manage Groups**.</span></span>  
  
3.  <span data-ttu-id="3dfa2-111">单击 **“添加组”**。</span><span class="sxs-lookup"><span data-stu-id="3dfa2-111">Click **Add groups**.</span></span>  
  
4.  <span data-ttu-id="3dfa2-112">输入该组的名称，组名之前应放置 Active Directory 域名或服务器计算机的名称，例如 *domain\group_name* 或 *computer\group_name*。</span><span class="sxs-lookup"><span data-stu-id="3dfa2-112">Type the group's name preceded by the Active Directory domain name or by the server computer's name, as in *domain\group_name* or *computer\group_name*.</span></span>  
  
5.  <span data-ttu-id="3dfa2-113">或者单击 **“检查名称”**。</span><span class="sxs-lookup"><span data-stu-id="3dfa2-113">Optionally, click **Check names**.</span></span>  
  
6.  <span data-ttu-id="3dfa2-114">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="3dfa2-114">Click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3dfa2-115">当用户第一次访问 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]时，将用户的名称添加到 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 用户列表。</span><span class="sxs-lookup"><span data-stu-id="3dfa2-115">When the user first accesses [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], the user's name is added to the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] list of users.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="3dfa2-116">后续步骤</span><span class="sxs-lookup"><span data-stu-id="3dfa2-116">Next Steps</span></span>  
  
-   [<span data-ttu-id="3dfa2-117">分配功能区域权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3dfa2-117">Assign Functional Area Permissions &#40;Master Data Services&#41;</span></span>](assign-functional-area-permissions-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="3dfa2-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3dfa2-118">See Also</span></span>  
 [<span data-ttu-id="3dfa2-119">安全性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3dfa2-119">Security &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/security-master-data-services.md)  
  
  
