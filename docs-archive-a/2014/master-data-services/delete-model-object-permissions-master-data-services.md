---
title: 删除模型对象权限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting model object permissions [Master Data Services]
- permissions [Master Data Services], deleting model object permissions
- models [Master Data Services], deleting object permissions
ms.assetid: 859c5952-f600-4940-8064-1afd13f7f6dc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 98da869476e597d76a83b0b86cc9e6e4274a25e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689495"
---
# <a name="delete-model-object-permissions-master-data-services"></a><span data-ttu-id="c15df-102">删除模型对象权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="c15df-102">Delete Model Object Permissions (Master Data Services)</span></span>
  <span data-ttu-id="c15df-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，删除模型对象权限可以删除已进行的任何分配。</span><span class="sxs-lookup"><span data-stu-id="c15df-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete model object permissions to remove any assignments that have been made.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c15df-104">先决条件</span><span class="sxs-lookup"><span data-stu-id="c15df-104">Prerequisites</span></span>  
 <span data-ttu-id="c15df-105">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="c15df-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="c15df-106">您必须有权访问 **“用户和组权限”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="c15df-106">You must have permission to access the **Users and Group Permissions** functional area.</span></span>  
  
-   <span data-ttu-id="c15df-107">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="c15df-107">You must be a model administrator.</span></span> <span data-ttu-id="c15df-108">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="c15df-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-model-object-permissions"></a><span data-ttu-id="c15df-109">删除模型对象权限</span><span class="sxs-lookup"><span data-stu-id="c15df-109">To delete model object permissions</span></span>  
  
1.  <span data-ttu-id="c15df-110">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“用户和组权限”**。</span><span class="sxs-lookup"><span data-stu-id="c15df-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="c15df-111">在 **“用户”** 或 **“组”** 页上，选择要编辑的用户或组所对应的行。</span><span class="sxs-lookup"><span data-stu-id="c15df-111">On the **Users** or **Groups** page, select the row for the user or group that you want to edit.</span></span>  
  
3.  <span data-ttu-id="c15df-112">单击 **“编辑所选用户”**。</span><span class="sxs-lookup"><span data-stu-id="c15df-112">Click **Edit selected user**.</span></span>  
  
4.  <span data-ttu-id="c15df-113">单击 **“模型”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="c15df-113">Click the **Models** tab.</span></span>  
  
5.  <span data-ttu-id="c15df-114">也可以从 **“模型”** 列表中选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="c15df-114">Optionally, select a model from the **Model** list.</span></span>  
  
6.  <span data-ttu-id="c15df-115">在 "**模型权限摘要**" 窗格中，选择要删除的权限所在的行。</span><span class="sxs-lookup"><span data-stu-id="c15df-115">In the **Model Permission Summary** pane, select the row for the permission that you want to delete.</span></span>  
  
7.  <span data-ttu-id="c15df-116">单击 "**删除所选权限**"。</span><span class="sxs-lookup"><span data-stu-id="c15df-116">Click **Delete selected permission**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c15df-117">如果权限继承自一个组，则不能从用户删除该权限。</span><span class="sxs-lookup"><span data-stu-id="c15df-117">You cannot remove a permission from a user if the permission is inherited from a group.</span></span> <span data-ttu-id="c15df-118">而是必须从该组删除该权限。</span><span class="sxs-lookup"><span data-stu-id="c15df-118">You must remove the permission from the group instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c15df-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c15df-119">See Also</span></span>  
 <span data-ttu-id="c15df-120">[&#40;Master Data Services 的模型对象权限&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="c15df-120">[Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="c15df-121">分配模型对象权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="c15df-121">Assign Model Object Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)  
  
  
