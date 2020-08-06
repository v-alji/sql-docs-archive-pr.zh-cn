---
title: 删除成员或集合 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], deleting
- leaf members [Master Data Services], deleting
- deleting members [Master Data Services]
- members [Master Data Services], deleting
- consolidated members [Master Data Services], deleting
ms.assetid: 519130a7-4226-4d71-9124-d2ee0ce7e5bd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9b248750c0e755c3fc9e32d45068c754e64957b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682920"
---
# <a name="delete-a-member-or-collection-master-data-services"></a><span data-ttu-id="9a73a-102">删除成员或集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="9a73a-102">Delete a Member or Collection (Master Data Services)</span></span>
  <span data-ttu-id="9a73a-103">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，当您不再需要某个成员或集合时，可以将其删除。</span><span class="sxs-lookup"><span data-stu-id="9a73a-103">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], delete a member or collection when you no longer need it.</span></span> <span data-ttu-id="9a73a-104">若要大批量删除成员，可以改用临时过程。</span><span class="sxs-lookup"><span data-stu-id="9a73a-104">If you want to delete members in bulk, use the staging process instead.</span></span> <span data-ttu-id="9a73a-105">有关详细信息，请参阅[&#41;&#40;Master Data Services 停用或删除成员](add-update-and-delete-data-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="9a73a-105">For more information, see [Deactivate or Delete Members by Using the Staging Process &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9a73a-106">如果某一成员用作另一个成员的基于域的属性值，则不能删除该成员。</span><span class="sxs-lookup"><span data-stu-id="9a73a-106">You cannot delete a member if it is used as a domain-based attribute value for another member.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9a73a-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="9a73a-107">Prerequisites</span></span>  
 <span data-ttu-id="9a73a-108">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="9a73a-108">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="9a73a-109">\*\*\*\* 您必须有权访问“资源管理器”功能区域。</span><span class="sxs-lookup"><span data-stu-id="9a73a-109">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="9a73a-110">对于成员，您必须对要从中删除成员的叶模型对象至少具有 "**更新**" 权限。</span><span class="sxs-lookup"><span data-stu-id="9a73a-110">For members, you must have a minimum of **Update** permission to the leaf model object you are deleting a member from.</span></span>  
  
-   <span data-ttu-id="9a73a-111">对于集合，您必须对要删除的叶集合对象至少具有 **“更新”** 权限。</span><span class="sxs-lookup"><span data-stu-id="9a73a-111">For collections, you must have a minimum of **Update** permission to the leaf collection object you are deleting.</span></span>  
  
### <a name="to-delete-a-member-or-collection"></a><span data-ttu-id="9a73a-112">删除成员或集合</span><span class="sxs-lookup"><span data-stu-id="9a73a-112">To delete a member or collection</span></span>  
  
1.  <span data-ttu-id="9a73a-113">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 在 \*\*\*\* 主页上，从“模型”列表中，选择模型。</span><span class="sxs-lookup"><span data-stu-id="9a73a-113">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="9a73a-114">\*\*\*\* 从“版本”列表中，选择某一版本。</span><span class="sxs-lookup"><span data-stu-id="9a73a-114">From the **Version** list, select a version.</span></span>  
  
3.  <span data-ttu-id="9a73a-115">单击 **“资源管理器”**。</span><span class="sxs-lookup"><span data-stu-id="9a73a-115">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="9a73a-116">若要删除：</span><span class="sxs-lookup"><span data-stu-id="9a73a-116">To delete:</span></span>  
  
    -   <span data-ttu-id="9a73a-117">叶成员，请从菜单栏中指向 **“实体”** ，然后单击包含该成员的实体的名称。</span><span class="sxs-lookup"><span data-stu-id="9a73a-117">A leaf member, from the menu bar, point to **Entities** and click the name of the entity that contains the member.</span></span>  
  
    -   <span data-ttu-id="9a73a-118">合并成员，请从菜单栏中指向 **“层次结构”** ，然后单击包含该成员的层次结构的名称。</span><span class="sxs-lookup"><span data-stu-id="9a73a-118">A consolidated member, from the menu bar, point to **Hierarchies** and click the name of the hierarchy that contains the member.</span></span> <span data-ttu-id="9a73a-119">接着单击包含成员的层次结构中的节点。</span><span class="sxs-lookup"><span data-stu-id="9a73a-119">Then click the node in the hierarchy that contains the member.</span></span>  
  
    -   <span data-ttu-id="9a73a-120">集合，请从菜单栏中指向 **“集合”** ，然后单击包含该集合的实体的名称。</span><span class="sxs-lookup"><span data-stu-id="9a73a-120">A collection, from the menu bar, point to **Collections** and click the name of the entity that contains the collection.</span></span>  
  
5.  <span data-ttu-id="9a73a-121">在网格中，单击要删除的成员或集合所对应的行。</span><span class="sxs-lookup"><span data-stu-id="9a73a-121">In the grid, click the row of the member or collection you want to delete.</span></span>  
  
6.  <span data-ttu-id="9a73a-122">单击 **“删除成员”**、 **“删除”** 或 **“删除集合”**。</span><span class="sxs-lookup"><span data-stu-id="9a73a-122">Click **Delete Member**, **Delete**, or **Delete Collection**.</span></span>  
  
7.  <span data-ttu-id="9a73a-123">在确认对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="9a73a-123">In the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a73a-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9a73a-124">See Also</span></span>  
 <span data-ttu-id="9a73a-125">[重新激活成员或集合 &#40;Master Data Services&#41;](../../2014/master-data-services/reactivate-a-member-or-collection-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="9a73a-125">[Reactivate a Member or Collection &#40;Master Data Services&#41;](../../2014/master-data-services/reactivate-a-member-or-collection-master-data-services.md) </span></span>  
 <span data-ttu-id="9a73a-126">[成员 &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="9a73a-126">[Members &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span></span>  
 [<span data-ttu-id="9a73a-127">集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="9a73a-127">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)  
  
  
