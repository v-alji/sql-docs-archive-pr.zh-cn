---
title: 版本 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- version flags [Master Data Services], about version flags
- versions [Master Data Services]
- version flags [Master Data Services]
- versions [Master Data Services], version flags
ms.assetid: 752ec96d-53d7-4160-8ed2-92e0324645f3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6f8b55a32cdf2a5aabad38ee3d0d4154c2ad6a6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577744"
---
# <a name="versions-master-data-services"></a><span data-ttu-id="f2260-102">版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f2260-102">Versions (Master Data Services)</span></span>
  <span data-ttu-id="f2260-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，您可以创建模型中主数据的多个版本。</span><span class="sxs-lookup"><span data-stu-id="f2260-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can create multiple versions of the master data within a model.</span></span> <span data-ttu-id="f2260-104">在验证数据时可以锁定版本，并在验证数据之后提交。</span><span class="sxs-lookup"><span data-stu-id="f2260-104">Versions can be locked while you validate your data and committed after the data is validated.</span></span> <span data-ttu-id="f2260-105">提交的版本组成可审核的更改记录。</span><span class="sxs-lookup"><span data-stu-id="f2260-105">Committed versions form an auditable record of changes.</span></span> <span data-ttu-id="f2260-106">创建的每个版本包含模型的所有成员、属性值、层次结构成员、层次结构关系和集合。</span><span class="sxs-lookup"><span data-stu-id="f2260-106">Each version you create contains all members, attribute values, hierarchy members, hierarchy relationships, and collections for the model.</span></span>  
  
## <a name="when-to-use-versions"></a><span data-ttu-id="f2260-107">何时使用版本</span><span class="sxs-lookup"><span data-stu-id="f2260-107">When to Use Versions</span></span>  
 <span data-ttu-id="f2260-108">使用版本可以：</span><span class="sxs-lookup"><span data-stu-id="f2260-108">Use versions to:</span></span>  
  
-   <span data-ttu-id="f2260-109">维护主数据随时间变化的可审核记录。</span><span class="sxs-lookup"><span data-stu-id="f2260-109">Maintain an auditable record of your master data as it changes over time.</span></span>  
  
-   <span data-ttu-id="f2260-110">防止用户更改，确保所有数据已根据业务规则成功验证。</span><span class="sxs-lookup"><span data-stu-id="f2260-110">Prevent users from making changes while you ensure all data validates successfully against business rules.</span></span>  
  
-   <span data-ttu-id="f2260-111">锁定模型供订阅系统使用。</span><span class="sxs-lookup"><span data-stu-id="f2260-111">Lock down a model for use by subscribing systems.</span></span>  
  
-   <span data-ttu-id="f2260-112">测试不同的层次结构，而不必立即将其实现。</span><span class="sxs-lookup"><span data-stu-id="f2260-112">Test different hierarchies without implementing them right away.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f2260-113">更改模型的结构时，例如创建新实体或基于域的属性时，更改应用到所有版本。</span><span class="sxs-lookup"><span data-stu-id="f2260-113">When you change the structure of your model, such as when you create a new entity or domain-based attribute, the change applies to all versions.</span></span> <span data-ttu-id="f2260-114">如果您查看模型的早期版本，将显示实体或属性，但数据不存在。</span><span class="sxs-lookup"><span data-stu-id="f2260-114">If you view an earlier version of the model, the entity or attribute is displayed, but no data exists.</span></span>  
  
## <a name="version-flags"></a><span data-ttu-id="f2260-115">版本标志</span><span class="sxs-lookup"><span data-stu-id="f2260-115">Version Flags</span></span>  
 <span data-ttu-id="f2260-116">版本可用于用户或订阅系统时，可以设置一个标志来标识该版本。</span><span class="sxs-lookup"><span data-stu-id="f2260-116">When a version is ready for users or for a subscribing system, you can set a flag to identify the version.</span></span> <span data-ttu-id="f2260-117">可以根据需要在版本间移动此标志。</span><span class="sxs-lookup"><span data-stu-id="f2260-117">You can move this flag from version to version as needed.</span></span> <span data-ttu-id="f2260-118">标志帮助用户和订阅系统确定要使用模型的哪个版本。</span><span class="sxs-lookup"><span data-stu-id="f2260-118">Flags help users and subscribing systems identify which version of a model to use.</span></span>  
  
## <a name="workflow-for-version-management"></a><span data-ttu-id="f2260-119">版本管理的工作流</span><span class="sxs-lookup"><span data-stu-id="f2260-119">Workflow for Version Management</span></span>  
 <span data-ttu-id="f2260-120">使用以下工作流进行版本管理：</span><span class="sxs-lookup"><span data-stu-id="f2260-120">Use the following workflow for version management:</span></span>  
  
1.  <span data-ttu-id="f2260-121">创建模型并使用公司的主数据填充 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库时，自动创建初始版本。</span><span class="sxs-lookup"><span data-stu-id="f2260-121">An initial version is created automatically when you create a model and populate the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database with your company's master data.</span></span> <span data-ttu-id="f2260-122">用户基于权限在需要时可以更改此版本。</span><span class="sxs-lookup"><span data-stu-id="f2260-122">Based on permissions, users can make changes to this version as needed.</span></span>  
  
2.  <span data-ttu-id="f2260-123">当您要提交模型的一个版本时，锁定该版本，以便只有模型管理员可以更新数据。</span><span class="sxs-lookup"><span data-stu-id="f2260-123">When you want to commit a version of a model, lock the version so that only model administrators can update the data.</span></span> <span data-ttu-id="f2260-124">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f2260-124">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span> <span data-ttu-id="f2260-125">如果配置了通知，则每次版本的状态发生更改时，电子邮件通知都会发送给模型管理员。</span><span class="sxs-lookup"><span data-stu-id="f2260-125">If notifications are configured, an email notification is sent to model administrators each time the version's status changes.</span></span> <span data-ttu-id="f2260-126">有关详细信息，请参阅[配置电子邮件通知 (Master Data Services)](../../2014/master-data-services/configure-email-notifications-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f2260-126">For more information, see [Configure Email Notifications &#40;Master Data Services&#41;](../../2014/master-data-services/configure-email-notifications-master-data-services.md).</span></span>  
  
3.  <span data-ttu-id="f2260-127">将业务规则应用于锁定的版本的数据并查看任何验证问题。</span><span class="sxs-lookup"><span data-stu-id="f2260-127">Apply business rules to the locked version's data and review any validation issues.</span></span> <span data-ttu-id="f2260-128">如有必要，可以填写缺少的信息或恢复导致问题的事务。</span><span class="sxs-lookup"><span data-stu-id="f2260-128">If necessary, you can fill in missing information or revert the transaction that caused the issue.</span></span> <span data-ttu-id="f2260-129">还可以解锁该版本，以便用户进行更改。</span><span class="sxs-lookup"><span data-stu-id="f2260-129">You can also unlock the version for users to make changes.</span></span>  
  
4.  <span data-ttu-id="f2260-130">在所有数据通过验证后，提交该版本并将其标记为可供订阅系统使用。</span><span class="sxs-lookup"><span data-stu-id="f2260-130">When all the data passes validation, commit the version and flag it for use by subscribing systems.</span></span> <span data-ttu-id="f2260-131">无法更改已提交的版本。</span><span class="sxs-lookup"><span data-stu-id="f2260-131">Changes cannot be made to a committed version.</span></span>  
  
5.  <span data-ttu-id="f2260-132">复制已提交的版本，并通知用户他们可以开始使用模型的新版本。</span><span class="sxs-lookup"><span data-stu-id="f2260-132">Copy the committed version and notify users that they can begin working in a new version of the model.</span></span>  
  
## <a name="sequential-or-simultaneous-versions"></a><span data-ttu-id="f2260-133">顺序版本或同时版本</span><span class="sxs-lookup"><span data-stu-id="f2260-133">Sequential or Simultaneous Versions</span></span>  
 <span data-ttu-id="f2260-134">可以创建模型的顺序版本或同时版本。</span><span class="sxs-lookup"><span data-stu-id="f2260-134">You can create sequential or simultaneous versions of your model.</span></span>  
  
-   <span data-ttu-id="f2260-135">**顺序版本：**</span><span class="sxs-lookup"><span data-stu-id="f2260-135">**Sequential versions.**</span></span> <span data-ttu-id="f2260-136">每次提交版本时，可以创建新的副本并为版本提供下一个序列号。</span><span class="sxs-lookup"><span data-stu-id="f2260-136">Each time you commit a version, create a new copy and give the version the next sequential number.</span></span> <span data-ttu-id="f2260-137">例如，可以复制 **“版本 7”** 的模型，并将副本命名为 **“版本 8”**。</span><span class="sxs-lookup"><span data-stu-id="f2260-137">For example, you can copy **Version 7** of your model and name the copy **Version 8**.</span></span>  
  
-   <span data-ttu-id="f2260-138">**同时版本：**</span><span class="sxs-lookup"><span data-stu-id="f2260-138">**Simultaneous versions.**</span></span> <span data-ttu-id="f2260-139">要同时使用数据的两个或多个版本时，可以创建模型的同时版本。</span><span class="sxs-lookup"><span data-stu-id="f2260-139">Create simultaneous versions of your model when you want to work on two or more versions of your data at once.</span></span> <span data-ttu-id="f2260-140">如果您的公司存在与正常业务流程相符的重组或合并行为，并且您要确定如何使新的主数据适应现有结构，同时版本将非常有用。</span><span class="sxs-lookup"><span data-stu-id="f2260-140">This is useful when your company has reorganizations or mergers that coincide with the normal course of business and you want to determine how the new master data might fit into your existing structures.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f2260-141">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 中的设置确定是复制所有版本还是仅复制那些已提交的版本。</span><span class="sxs-lookup"><span data-stu-id="f2260-141">A setting in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] determines whether or not you can copy all versions or only those that are committed.</span></span> <span data-ttu-id="f2260-142">若要创建同时版本，必须配置 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 以允许您复制所有版本。</span><span class="sxs-lookup"><span data-stu-id="f2260-142">To create simultaneous versions you must configure [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] to allow you to copy all versions.</span></span> <span data-ttu-id="f2260-143">此设置在“系统设置”表中也提供。</span><span class="sxs-lookup"><span data-stu-id="f2260-143">This setting is also available in the System Settings table.</span></span> <span data-ttu-id="f2260-144">有关详细信息，请参阅[系统设置 (Master Data Services)](../../2014/master-data-services/system-settings-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f2260-144">For more information, see [System Settings &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="f2260-145">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="f2260-145">Related Tasks</span></span>  
  
|<span data-ttu-id="f2260-146">任务说明</span><span class="sxs-lookup"><span data-stu-id="f2260-146">Task Description</span></span>|<span data-ttu-id="f2260-147">主题</span><span class="sxs-lookup"><span data-stu-id="f2260-147">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="f2260-148">更改现有版本的名称。</span><span class="sxs-lookup"><span data-stu-id="f2260-148">Change the name of an existing version.</span></span>|[<span data-ttu-id="f2260-149">更改版本名称 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f2260-149">Change a Version Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-version-name-master-data-services.md)|  
|<span data-ttu-id="f2260-150">锁定版本，以便只有管理员才能编辑其数据。</span><span class="sxs-lookup"><span data-stu-id="f2260-150">Lock a version so only administrators can edit its data.</span></span>|[<span data-ttu-id="f2260-151">锁定版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f2260-151">Lock a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/lock-a-version-master-data-services.md)|  
|<span data-ttu-id="f2260-152">取消锁定版本，以便用户可以编辑其数据。</span><span class="sxs-lookup"><span data-stu-id="f2260-152">Unlock a version so users can edit its data.</span></span>|[<span data-ttu-id="f2260-153">取消锁定版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f2260-153">Unlock a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/unlock-a-version-master-data-services.md)|  
|<span data-ttu-id="f2260-154">验证所有数据后，提交版本。</span><span class="sxs-lookup"><span data-stu-id="f2260-154">Commit a version after all data is validated.</span></span>|[<span data-ttu-id="f2260-155">提交版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f2260-155">Commit a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/commit-a-version-master-data-services.md)|  
|<span data-ttu-id="f2260-156">创建新的标志来标记版本。</span><span class="sxs-lookup"><span data-stu-id="f2260-156">Create a new flag to mark a version.</span></span>|[<span data-ttu-id="f2260-157">创建版本标志 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f2260-157">Create a Version Flag &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-version-flag-master-data-services.md)|  
|<span data-ttu-id="f2260-158">更改现有版本标志的名称。</span><span class="sxs-lookup"><span data-stu-id="f2260-158">Change the name of an existing version flag.</span></span>|[<span data-ttu-id="f2260-159">更改版本标志名称 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f2260-159">Change a Version Flag Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-version-flag-name-master-data-services.md)|  
|<span data-ttu-id="f2260-160">将现有标志分配给版本。</span><span class="sxs-lookup"><span data-stu-id="f2260-160">Assign an existing flag to a version.</span></span>|[<span data-ttu-id="f2260-161">向版本分配标志 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f2260-161">Assign a Flag to a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-a-flag-to-a-version-master-data-services.md)|  
|<span data-ttu-id="f2260-162">创建现有版本的新副本</span><span class="sxs-lookup"><span data-stu-id="f2260-162">Create a new copy of an existing version</span></span>|[<span data-ttu-id="f2260-163">复制版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f2260-163">Copy a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/copy-a-version-master-data-services.md)|  
|<span data-ttu-id="f2260-164">删除现有版本。</span><span class="sxs-lookup"><span data-stu-id="f2260-164">Delete an existing version.</span></span>|[<span data-ttu-id="f2260-165">删除版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f2260-165">Delete a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-version-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="f2260-166">相关内容</span><span class="sxs-lookup"><span data-stu-id="f2260-166">Related Content</span></span>  
  
-   [<span data-ttu-id="f2260-167">撤消事务 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f2260-167">Reverse a Transaction &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/reverse-a-transaction-master-data-services.md)  
  
-   [<span data-ttu-id="f2260-168">通知 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f2260-168">Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/notifications-master-data-services.md)  
  
-   [<span data-ttu-id="f2260-169">业务规则 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f2260-169">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
