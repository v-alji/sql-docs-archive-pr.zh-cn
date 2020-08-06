---
title: 创建模型管理员 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], creating
ms.assetid: dae17afc-3b39-490e-b51f-2d8da26d429e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 24efc3961e6ed5b9f41b2321dfcc4fbf16632270
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591453"
---
# <a name="create-a-model-administrator-master-data-services"></a><span data-ttu-id="9c08c-102">创建模型管理员 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="9c08c-102">Create a Model Administrator (Master Data Services)</span></span>
  <span data-ttu-id="9c08c-103">在中 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ，当你希望某个组或用户对一个或多个模型中的所有对象具有 "**更新**" 权限时，可以创建模型管理员。</span><span class="sxs-lookup"><span data-stu-id="9c08c-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a model administrator when you want a group or user to have **Update** permission to all objects in one or more models.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="9c08c-104">为了简化管理，请创建一个 Windows 组或本地组并将其配置为模型管理员。</span><span class="sxs-lookup"><span data-stu-id="9c08c-104">To simplify administration, create a Windows or local group and configure it as a model administrator.</span></span> <span data-ttu-id="9c08c-105">然后，您可以从该组中添加和删除用户，而无需访问 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9c08c-105">You can then add and remove users from the group without accessing [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9c08c-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="9c08c-106">Prerequisites</span></span>  
 <span data-ttu-id="9c08c-107">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="9c08c-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="9c08c-108">您必须有权访问 **“用户和组权限”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="9c08c-108">You must have permission to access the **User and Group Permissions** functional area.</span></span>  
  
-   <span data-ttu-id="9c08c-109">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="9c08c-109">You must be a model administrator.</span></span> <span data-ttu-id="9c08c-110">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="9c08c-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-create-a-model-administrator"></a><span data-ttu-id="9c08c-111">创建模型管理员</span><span class="sxs-lookup"><span data-stu-id="9c08c-111">To create a model administrator</span></span>  
  
1.  <span data-ttu-id="9c08c-112">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“用户和组权限”**。</span><span class="sxs-lookup"><span data-stu-id="9c08c-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="9c08c-113">在 **“用户”** 或 **“组”** 页上，选择要编辑的用户或组所对应的行。</span><span class="sxs-lookup"><span data-stu-id="9c08c-113">On the **Users** or **Groups** page, select the row for the user or group that you want to edit.</span></span>  
  
3.  <span data-ttu-id="9c08c-114">单击 **“编辑所选用户”**。</span><span class="sxs-lookup"><span data-stu-id="9c08c-114">Click **Edit selected user**.</span></span>  
  
4.  <span data-ttu-id="9c08c-115">单击 **“模型”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="9c08c-115">Click the **Models** tab.</span></span>  
  
5.  <span data-ttu-id="9c08c-116">也可以从 **“模型”** 列表中选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="9c08c-116">Optionally, select a model from the **Model** list.</span></span>  
  
6.  <span data-ttu-id="9c08c-117">单击 **“编辑”** 。</span><span class="sxs-lookup"><span data-stu-id="9c08c-117">Click **Edit**.</span></span>  
  
7.  <span data-ttu-id="9c08c-118">单击要授予对其权限的模型。</span><span class="sxs-lookup"><span data-stu-id="9c08c-118">Click the model you want to grant permission to.</span></span>  
  
8.  <span data-ttu-id="9c08c-119">从菜单中选择 "**更新**"。</span><span class="sxs-lookup"><span data-stu-id="9c08c-119">From the menu, select **Update**.</span></span>  
  
9. <span data-ttu-id="9c08c-120">对希望组或用户成为其管理员的每个模型，完成步骤 7 和 8。</span><span class="sxs-lookup"><span data-stu-id="9c08c-120">Complete steps 7 and 8 for each model you want the group or user to be an administrator for.</span></span>  
  
10. <span data-ttu-id="9c08c-121">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="9c08c-121">Click **Save**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c08c-122">备注</span><span class="sxs-lookup"><span data-stu-id="9c08c-122">Remarks</span></span>  
 <span data-ttu-id="9c08c-123">不要分配对模型对象或层次结构成员的任何其他权限。</span><span class="sxs-lookup"><span data-stu-id="9c08c-123">Do not assign any other permissions to model objects or hierarchy members.</span></span> <span data-ttu-id="9c08c-124">如果执行此操作，用户将不再是管理员，并且不能在**资源管理器**之外的任何功能区域中查看模型。</span><span class="sxs-lookup"><span data-stu-id="9c08c-124">If you do, the user is no longer an administrator and cannot view the model in any functional area other than **Explorer**.</span></span>  
  
 <span data-ttu-id="9c08c-125">有一个例外：如果用户对**层次结构 "成员**" 选项卡上的层次结构**根**分配了 "**更新**" 权限，则该用户仍被视为模型管理员。</span><span class="sxs-lookup"><span data-stu-id="9c08c-125">There is one exception: if the user has **Update** permission assigned to a hierarchy **Root** on the **Hierarchy Members** tab, the user is still considered a model administrator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c08c-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9c08c-126">See Also</span></span>  
 <span data-ttu-id="9c08c-127">[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="9c08c-127">[Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md) </span></span>  
 <span data-ttu-id="9c08c-128">[&#40;Master Data Services 分配模型对象权限&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="9c08c-128">[Assign Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="9c08c-129">[将层次结构成员权限分配 &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="9c08c-129">[Assign Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="9c08c-130">[&#40;Master Data Services 的模型对象权限&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="9c08c-130">[Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="9c08c-131">层次结构成员权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="9c08c-131">Hierarchy Member Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
