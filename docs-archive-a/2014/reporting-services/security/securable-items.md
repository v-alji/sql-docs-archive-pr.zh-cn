---
title: 安全对象项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- securable items [Reporting Services]
- roles [Reporting Services], securable items
- security [Reporting Services], securable items listed
- role-based security [Reporting Services], securable items
ms.assetid: 27f58d4c-5c7b-4947-af5b-0f1fa60faf5f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f2f9fa5108831cb6c469710a71439bf3cfb6194a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589434"
---
# <a name="securable-items"></a><span data-ttu-id="189a9-102">安全对象</span><span class="sxs-lookup"><span data-stu-id="189a9-102">Securable Items</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="189a9-103">使用基于角色的安全性来控制对报表服务器上存储的项的访问权限。</span><span class="sxs-lookup"><span data-stu-id="189a9-103">uses role-based security to control access to items that are stored on a report server.</span></span> <span data-ttu-id="189a9-104">通常通过创建一对角色分配来向用户授予对报表服务器的访问权限：</span><span class="sxs-lookup"><span data-stu-id="189a9-104">When you grant a user access to a report server, you typically do so by creating a pair of role assignments:</span></span>  
  
-   <span data-ttu-id="189a9-105">在站点级</span><span class="sxs-lookup"><span data-stu-id="189a9-105">At the site level</span></span>  
  
-   <span data-ttu-id="189a9-106">在主文件夹，它是报表服务器文件夹层次结构的根节点</span><span class="sxs-lookup"><span data-stu-id="189a9-106">On Home, which is the root node of the report server folder hierarchy</span></span>  
  
 <span data-ttu-id="189a9-107">安全性可在报表服务器文件夹层次结构中继承。</span><span class="sxs-lookup"><span data-stu-id="189a9-107">Security is inherited within the report server folder hierarchy.</span></span> <span data-ttu-id="189a9-108">可通过在站点级和主文件夹上创建角色分配来设置权限继承，该继承将扩展到报表服务器上所有项和操作。</span><span class="sxs-lookup"><span data-stu-id="189a9-108">Creating role assignments at the site level and on the Home folder sets permission inheritance that extends to all items and operations on a report server.</span></span>  
  
 <span data-ttu-id="189a9-109">您可以通过为各个项定义安全性来覆盖权限继承。</span><span class="sxs-lookup"><span data-stu-id="189a9-109">You can override permission inheritance by defining security for individual items.</span></span> <span data-ttu-id="189a9-110">可以单独保护的项包括：</span><span class="sxs-lookup"><span data-stu-id="189a9-110">Items that you can secure individually include:</span></span>  
  
-   <span data-ttu-id="189a9-111">Folders</span><span class="sxs-lookup"><span data-stu-id="189a9-111">Folders</span></span>  
  
-   <span data-ttu-id="189a9-112">报表</span><span class="sxs-lookup"><span data-stu-id="189a9-112">Reports</span></span>  
  
-   <span data-ttu-id="189a9-113">报表模型</span><span class="sxs-lookup"><span data-stu-id="189a9-113">Report models</span></span>  
  
-   <span data-ttu-id="189a9-114">资源</span><span class="sxs-lookup"><span data-stu-id="189a9-114">Resources</span></span>  
  
-   <span data-ttu-id="189a9-115">共享数据源</span><span class="sxs-lookup"><span data-stu-id="189a9-115">Shared data sources</span></span>  
  
-   <span data-ttu-id="189a9-116">共享数据集</span><span class="sxs-lookup"><span data-stu-id="189a9-116">Shared datasets</span></span>  
  
 <span data-ttu-id="189a9-117">其他构造（例如计划和订阅）不能明确地定义安全性。</span><span class="sxs-lookup"><span data-stu-id="189a9-117">Other constructs, such as schedules and subscriptions, are not explicitly secured.</span></span> <span data-ttu-id="189a9-118">计划和订阅是在报表的安全性之下运行的。</span><span class="sxs-lookup"><span data-stu-id="189a9-118">Schedules and subscriptions operate within the security of a report.</span></span>  
  
## <a name="item-descriptions"></a><span data-ttu-id="189a9-119">项说明</span><span class="sxs-lookup"><span data-stu-id="189a9-119">Item Descriptions</span></span>  
 <span data-ttu-id="189a9-120">下表列出了安全对象并对其特征进行了说明：</span><span class="sxs-lookup"><span data-stu-id="189a9-120">The following table lists securable items and describes their characteristics.</span></span>  
  
|<span data-ttu-id="189a9-121">Item</span><span class="sxs-lookup"><span data-stu-id="189a9-121">Item</span></span>|<span data-ttu-id="189a9-122">特征</span><span class="sxs-lookup"><span data-stu-id="189a9-122">Characteristics</span></span>|  
|----------|---------------------|  
|<span data-ttu-id="189a9-123">Folders</span><span class="sxs-lookup"><span data-stu-id="189a9-123">Folders</span></span>|<span data-ttu-id="189a9-124">文件夹的安全性应用于文件夹本身及其包含的项。</span><span class="sxs-lookup"><span data-stu-id="189a9-124">Folder security applies to the folder itself and the items it contains.</span></span> <span data-ttu-id="189a9-125">主文件夹是文件夹层次结构的根节点。</span><span class="sxs-lookup"><span data-stu-id="189a9-125">The Home folder is the root node of the folder hierarchy.</span></span> <span data-ttu-id="189a9-126">对这一文件夹设置的安全性为文件夹层次结构中的所有从属文件夹、报表、资源和共享数据源建立了初始安全设置。</span><span class="sxs-lookup"><span data-stu-id="189a9-126">Security that you set for this folder establishes the initial security settings for all subordinate folders, reports, resources, and shared data sources in the folder hierarchy.</span></span> <span data-ttu-id="189a9-127">有关详细信息，请参阅 [保护文件](secure-folders.md)。</span><span class="sxs-lookup"><span data-stu-id="189a9-127">For more information, see [Secure Folders](secure-folders.md).</span></span><br /><br /> <span data-ttu-id="189a9-128">“我的报表”是一种特殊用途的文件夹，通过基于专用角色的隐含角色分配来设置安全性。</span><span class="sxs-lookup"><span data-stu-id="189a9-128">My Reports is a special-purpose folder that is secured through an implied role assignment based on a dedicated role.</span></span> <span data-ttu-id="189a9-129">有关详细信息，请参阅 [保护我的报表](secure-my-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="189a9-129">For more information, see [Secure My Reports](secure-my-reports.md).</span></span>|  
|<span data-ttu-id="189a9-130">报表</span><span class="sxs-lookup"><span data-stu-id="189a9-130">Reports</span></span>|<span data-ttu-id="189a9-131">您可以设置报表和链接报表的安全性，以控制用户可执行的操作的范围，如更改给定报表的属性。</span><span class="sxs-lookup"><span data-stu-id="189a9-131">Reports and linked reports can be secured to control the range of actions that users can perform, such as changing the properties of a given report.</span></span><br /><br /> <span data-ttu-id="189a9-132">报表历史记录通过包含相应历史记录的报表来设置安全性。</span><span class="sxs-lookup"><span data-stu-id="189a9-132">Report history is secured through the report that contains the history.</span></span> <span data-ttu-id="189a9-133">您不能对报表历史记录中的单个快照设置安全性。</span><span class="sxs-lookup"><span data-stu-id="189a9-133">You cannot secure individual snapshots within report history.</span></span><br /><br /> <span data-ttu-id="189a9-134">有关报表安全的详细信息，请参阅 [保护报表和资源](secure-reports-and-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="189a9-134">For more information about report security, see [Secure Reports and Resources](secure-reports-and-resources.md).</span></span>|  
|<span data-ttu-id="189a9-135">报表模型</span><span class="sxs-lookup"><span data-stu-id="189a9-135">Report models</span></span>|<span data-ttu-id="189a9-136">您可为整个或部分报表模型指定角色分配。</span><span class="sxs-lookup"><span data-stu-id="189a9-136">You can specify role assignment on all or part of a report model.</span></span> <span data-ttu-id="189a9-137">因为报表模型可能非常大，您可能会需要为映射到机密数据的模型项设置安全性。</span><span class="sxs-lookup"><span data-stu-id="189a9-137">Because report models can be quite extensive, you might want to secure the model items that map to confidential data.</span></span>|  
|<span data-ttu-id="189a9-138">资源</span><span class="sxs-lookup"><span data-stu-id="189a9-138">Resources</span></span>|<span data-ttu-id="189a9-139">您可以设置资源的安全性，以控制对资源本身及其属性的访问。</span><span class="sxs-lookup"><span data-stu-id="189a9-139">Resources can be secured to control access to the resource itself and its properties.</span></span><br /><br /> <span data-ttu-id="189a9-140">只有独立的资源才能作为单独的项设置安全性。</span><span class="sxs-lookup"><span data-stu-id="189a9-140">Only stand-alone resources can be secured as separate items.</span></span> <span data-ttu-id="189a9-141">嵌入到报表中的资源不能独立于报表之外单独设置安全性。</span><span class="sxs-lookup"><span data-stu-id="189a9-141">Resources that are embedded within a report cannot be secured separately from that report.</span></span><br /><br /> <span data-ttu-id="189a9-142">有关资源安全的详细信息，请参阅 [保护报表和资源](secure-reports-and-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="189a9-142">For more information about resource security, see [Secure Reports and Resources](secure-reports-and-resources.md).</span></span>|  
|<span data-ttu-id="189a9-143">共享数据源</span><span class="sxs-lookup"><span data-stu-id="189a9-143">Shared data sources</span></span>|<span data-ttu-id="189a9-144">您可以设置共享数据源的安全性，以限制对该项及其属性页的访问。</span><span class="sxs-lookup"><span data-stu-id="189a9-144">Shared data sources can be secured to limit access to the item and its property pages.</span></span> <span data-ttu-id="189a9-145">有关详细信息，请参阅 [保护共享数据源项](secure-shared-data-source-items.md)。</span><span class="sxs-lookup"><span data-stu-id="189a9-145">For more information, see [Secure Shared Data Source Items](secure-shared-data-source-items.md).</span></span>|  
|<span data-ttu-id="189a9-146">共享数据集</span><span class="sxs-lookup"><span data-stu-id="189a9-146">Shared datasets</span></span>|<span data-ttu-id="189a9-147">您可以设置共享数据集的安全性，以控制用户可执行的操作的范围，例如查看或更改定义，或者更改给定共享数据集的属性。</span><span class="sxs-lookup"><span data-stu-id="189a9-147">Shared datasets can be secured to control the range of actions that users can perform, such as viewing or changing the definition, or changing the properties of a given shared dataset.</span></span><br /><br /> <span data-ttu-id="189a9-148">有关详细信息，请参阅 [保护共享数据集项](secure-shared-dataset-items.md)。</span><span class="sxs-lookup"><span data-stu-id="189a9-148">For more information, see [Secure Shared Dataset Items](secure-shared-dataset-items.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="189a9-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="189a9-149">See Also</span></span>  
 <span data-ttu-id="189a9-150">[授予对本机模式报表服务器的权限](granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="189a9-150">[Granting Permissions on a Native Mode Report Server](granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="189a9-151">[创建、删除或修改角色 (Management Studio)](role-definitions-create-delete-or-modify.md) </span><span class="sxs-lookup"><span data-stu-id="189a9-151">[Create, Delete, or Modify a Role &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md) </span></span>  
 <span data-ttu-id="189a9-152">[授予用户对报表服务器的访问权限（报表管理器）](grant-user-access-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="189a9-152">[Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md) </span></span>  
 [<span data-ttu-id="189a9-153">修改或删除角色分配（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="189a9-153">Modify or Delete a Role Assignment &#40;Report Manager&#41;</span></span>](role-assignments-modify-or-delete.md)  
  
  
