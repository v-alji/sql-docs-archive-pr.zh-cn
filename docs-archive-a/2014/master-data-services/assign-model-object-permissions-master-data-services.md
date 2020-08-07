---
title: 分配模型对象权限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], assigning object permissions
- permissions [Master Data Services], assigning model object permissions
ms.assetid: 4b80148d-2318-415c-9479-28c240e48bcd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 92ac8ef3ac63b7128c4cbb7e9305ee6bd56ca010
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587462"
---
# <a name="assign-model-object-permissions-master-data-services"></a><span data-ttu-id="3fd9e-102">分配模型对象权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3fd9e-102">Assign Model Object Permissions (Master Data Services)</span></span>
  <span data-ttu-id="3fd9e-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，当您需要授予用户或组在 **的** “资源管理器” [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]功能区域中访问数据的权限时，或者当您需要将用户或组指定为管理员时，可以向模型对象分配权限。</span><span class="sxs-lookup"><span data-stu-id="3fd9e-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], assign permissions to model objects when you need to give a user or group access to data in the **Explorer** functional area of [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], or when you need to make a user or group an administrator.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3fd9e-104">将权限分配给模型时，针对所有其他模型的权限被隐式拒绝。</span><span class="sxs-lookup"><span data-stu-id="3fd9e-104">When you assign permission to a model, permission to all other models is implicitly denied.</span></span> <span data-ttu-id="3fd9e-105">如果未分配模型对象权限，则用户或组将无法在 **“资源管理器”** 中访问任何数据。</span><span class="sxs-lookup"><span data-stu-id="3fd9e-105">If you do not assign model object permissions, the user or group cannot access any data in **Explorer**.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3fd9e-106">必备条件</span><span class="sxs-lookup"><span data-stu-id="3fd9e-106">Prerequisites</span></span>  
 <span data-ttu-id="3fd9e-107">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="3fd9e-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="3fd9e-108">您必须有权访问 **“用户和组权限”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="3fd9e-108">You must have permission to access the **Users and Group Permissions** functional area.</span></span>  
  
-   <span data-ttu-id="3fd9e-109">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="3fd9e-109">You must be a model administrator.</span></span> <span data-ttu-id="3fd9e-110">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3fd9e-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-assign-model-object-permissions"></a><span data-ttu-id="3fd9e-111">分配模型对象权限</span><span class="sxs-lookup"><span data-stu-id="3fd9e-111">To assign model object permissions</span></span>  
  
1.  <span data-ttu-id="3fd9e-112">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“用户和组权限”**。</span><span class="sxs-lookup"><span data-stu-id="3fd9e-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="3fd9e-113">在 **“用户”** 或 **“组”** 页上，选择要编辑的用户或组所对应的行。</span><span class="sxs-lookup"><span data-stu-id="3fd9e-113">On the **Users** or **Groups** page, select the row for the user or group that you want to edit.</span></span>  
  
3.  <span data-ttu-id="3fd9e-114">单击 **“编辑所选用户”**。</span><span class="sxs-lookup"><span data-stu-id="3fd9e-114">Click **Edit selected user**.</span></span>  
  
4.  <span data-ttu-id="3fd9e-115">单击 **“模型”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="3fd9e-115">Click the **Models** tab.</span></span>  
  
5.  <span data-ttu-id="3fd9e-116">也可以从 **“模型”** 列表中选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="3fd9e-116">Optionally, select a model from the **Model** list.</span></span>  
  
6.  <span data-ttu-id="3fd9e-117">单击 **“编辑”** 。</span><span class="sxs-lookup"><span data-stu-id="3fd9e-117">Click **Edit**.</span></span>  
  
7.  <span data-ttu-id="3fd9e-118">展开树，单击要向其分配权限的模型对象。</span><span class="sxs-lookup"><span data-stu-id="3fd9e-118">Expand the tree, and click the model object you want to assign permissions to.</span></span>  
  
8.  <span data-ttu-id="3fd9e-119">从菜单中，选择 "**只读**"、"**更新**" 或 "**拒绝**"。</span><span class="sxs-lookup"><span data-stu-id="3fd9e-119">From the menu, select **Read-only**, **Update**, or **Deny**.</span></span>  
  
9. <span data-ttu-id="3fd9e-120">单击 **“保存”** 。</span><span class="sxs-lookup"><span data-stu-id="3fd9e-120">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="3fd9e-121">后续步骤</span><span class="sxs-lookup"><span data-stu-id="3fd9e-121">Next Steps</span></span>  
  
-   <span data-ttu-id="3fd9e-122">（可选）[分配层次结构成员权限 (Master Data Services)](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="3fd9e-122">(Optional) [Assign Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fd9e-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3fd9e-123">See Also</span></span>  
 <span data-ttu-id="3fd9e-124">[删除模型对象权限 &#40;Master Data Services&#41;](../../2014/master-data-services/delete-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="3fd9e-124">[Delete Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/delete-model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="3fd9e-125">[&#40;Master Data Services 的模型对象权限&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="3fd9e-125">[Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="3fd9e-126">创建模型管理员 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3fd9e-126">Create a Model Administrator &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-model-administrator-master-data-services.md)  
  
  
