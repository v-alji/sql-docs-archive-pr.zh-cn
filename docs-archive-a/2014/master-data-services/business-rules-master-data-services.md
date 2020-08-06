---
title: 业务规则 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], about business rules
- business rules [Master Data Services]
ms.assetid: a9f9e41a-2461-4845-b947-58b3a205543f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 00ac4b7d8970978ef111d56e5a809ada36362583
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591464"
---
# <a name="business-rules-master-data-services"></a><span data-ttu-id="3f04e-102">业务规则 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3f04e-102">Business Rules (Master Data Services)</span></span>
  <span data-ttu-id="3f04e-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，业务规则是您用于确保主数据的质量和准确性的规则。</span><span class="sxs-lookup"><span data-stu-id="3f04e-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a business rule is a rule that you use to ensure the quality and accuracy of your master data.</span></span> <span data-ttu-id="3f04e-104">可以使用业务规则自动更新数据、发送邮件或启用业务流程或工作流。</span><span class="sxs-lookup"><span data-stu-id="3f04e-104">You can use a business rule to automatically update data, to send email, or to start a business process or workflow.</span></span>  
  
## <a name="create-and-publish-business-rules"></a><span data-ttu-id="3f04e-105">创建和发布业务规则</span><span class="sxs-lookup"><span data-stu-id="3f04e-105">Create and Publish Business Rules</span></span>  
 <span data-ttu-id="3f04e-106">业务规则是您在[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中创建的 `If/Then` 语句。</span><span class="sxs-lookup"><span data-stu-id="3f04e-106">Business rules are `If/Then` statements that you create in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span> <span data-ttu-id="3f04e-107">如果某一属性值满足指定的条件，则执行操作。</span><span class="sxs-lookup"><span data-stu-id="3f04e-107">If an attribute value meets a specified condition, then an action is taken.</span></span> <span data-ttu-id="3f04e-108">可能的操作包括设置默认值或更改值。</span><span class="sxs-lookup"><span data-stu-id="3f04e-108">Possible actions include setting a default value or changing a value.</span></span> <span data-ttu-id="3f04e-109">这些操作可与发送电子邮件通知这一操作结合使用。</span><span class="sxs-lookup"><span data-stu-id="3f04e-109">These actions can be combined with sending an email notification.</span></span>  
  
 <span data-ttu-id="3f04e-110">业务规则可以基于特定属性值（例如，如果 Color=Blue，则执行操作），或在属性值发生更改时（例如，如果 Color 属性的值发生更改，则执行操作）应用。</span><span class="sxs-lookup"><span data-stu-id="3f04e-110">Business rules can be based on specific attribute values (for example, take action if Color=Blue), or when attribute values change (for example, take action if the value of the Color attribute changes).</span></span> <span data-ttu-id="3f04e-111">有关跟踪非特定更改的详细信息，请参阅[更改跟踪 &#40;Master Data Services&#41;](change-tracking-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3f04e-111">For more information about tracking non-specific changes, see [Change Tracking &#40;Master Data Services&#41;](change-tracking-master-data-services.md).</span></span>  
  
 <span data-ttu-id="3f04e-112">若要使用业务规则，您必须首先创建和发布规则，然后将已发布的规则应用于数据。</span><span class="sxs-lookup"><span data-stu-id="3f04e-112">To use business rules you must first create and publish your rules, then apply the published rules to data.</span></span> <span data-ttu-id="3f04e-113">您可以通过验证某一版本，将规则应用于该版本的数据的子级或全部数据。</span><span class="sxs-lookup"><span data-stu-id="3f04e-113">You can apply rules to subsets of data or to all data for a version by validating the version.</span></span> <span data-ttu-id="3f04e-114">在所有属性都通过业务规则验证前，不能提交版本。</span><span class="sxs-lookup"><span data-stu-id="3f04e-114">A version cannot be committed until all attributes pass business rule validation.</span></span>  
  
 <span data-ttu-id="3f04e-115">如果用户尝试添加未通过业务规则验证的某一属性值，仍可以保存该值。</span><span class="sxs-lookup"><span data-stu-id="3f04e-115">If a user attempts to add an attribute value that doesn't pass business rule validation, the value can still be saved.</span></span> <span data-ttu-id="3f04e-116">您可以查看并纠正在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中显示的验证问题。</span><span class="sxs-lookup"><span data-stu-id="3f04e-116">You can review and correct validation issues, which are displayed in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
 <span data-ttu-id="3f04e-117">在您创建模型部署包时，如果想要包括业务规则，则必须包括来自该包中版本的数据。</span><span class="sxs-lookup"><span data-stu-id="3f04e-117">When you create a model deployment package, if you want to include business rules you must include data from the version in the package.</span></span>  
  
 <span data-ttu-id="3f04e-118">如果您创建使用 **OR** 运算符的业务规则，应为可以独立进行计算的每个条件语句创建单独的规则。</span><span class="sxs-lookup"><span data-stu-id="3f04e-118">If you create a business rule that uses the **OR** operator, you should create a separate rule for each conditional statement that can be evaluated independently.</span></span> <span data-ttu-id="3f04e-119">然后，您可以根据需要排除规则，提供更高的灵活性以及更便于排除故障。</span><span class="sxs-lookup"><span data-stu-id="3f04e-119">You can then exclude rules as needed, providing more flexibility and easier troubleshooting.</span></span>  
  
## <a name="how-business-rules-are-applied"></a><span data-ttu-id="3f04e-120">如何应用业务规则</span><span class="sxs-lookup"><span data-stu-id="3f04e-120">How Business Rules Are Applied</span></span>  
 <span data-ttu-id="3f04e-121">可以设置运行规则的优先级顺序。</span><span class="sxs-lookup"><span data-stu-id="3f04e-121">You can set priority order for rules to run in.</span></span> <span data-ttu-id="3f04e-122">但是，在考虑优先级前，基于规则执行的操作类型应用业务规则。</span><span class="sxs-lookup"><span data-stu-id="3f04e-122">However, before priority is taken into account, business rules are applied based on the type of action the rule takes.</span></span> <span data-ttu-id="3f04e-123">该顺序如下所示：</span><span class="sxs-lookup"><span data-stu-id="3f04e-123">The order is as follows:</span></span>  
  
1.  <span data-ttu-id="3f04e-124">**默认值**</span><span class="sxs-lookup"><span data-stu-id="3f04e-124">**Default Value**</span></span>  
  
2.  <span data-ttu-id="3f04e-125">**更改值**</span><span class="sxs-lookup"><span data-stu-id="3f04e-125">**Change Value**</span></span>  
  
3.  <span data-ttu-id="3f04e-126">**验证**</span><span class="sxs-lookup"><span data-stu-id="3f04e-126">**Validation**</span></span>  
  
4.  <span data-ttu-id="3f04e-127">**外部操作**</span><span class="sxs-lookup"><span data-stu-id="3f04e-127">**External Action**</span></span>  
  
 <span data-ttu-id="3f04e-128">在这些组内，操作按从最低到最高的优先级顺序应用。</span><span class="sxs-lookup"><span data-stu-id="3f04e-128">Within these groups, actions are applied in priority order, from lowest to highest.</span></span> <span data-ttu-id="3f04e-129">因此，例如，四个单独的规则可能有 **“默认值”** 操作。</span><span class="sxs-lookup"><span data-stu-id="3f04e-129">So for example, four separate rules might have **Default Value** actions.</span></span> <span data-ttu-id="3f04e-130">根据 Web 用户界面中指定的优先级顺序，首先执行 **“默认值”** 操作。</span><span class="sxs-lookup"><span data-stu-id="3f04e-130">The **Default Value** action that occurs first depends on the priority order specified in the web UI.</span></span>  
  
 <span data-ttu-id="3f04e-131">其他有关应用规则的重要说明：</span><span class="sxs-lookup"><span data-stu-id="3f04e-131">Other important notes about applying rules:</span></span>  
  
-   <span data-ttu-id="3f04e-132">如果某一业务规则被排除或者未以 **“活动”** 状态发布，该规则仍可用，但在应用业务规则时不包括它。</span><span class="sxs-lookup"><span data-stu-id="3f04e-132">If a business rule is excluded or is not published with a status of **Active**, the rule is still available but is not included when business rules are applied.</span></span>  
  
-   <span data-ttu-id="3f04e-133">业务规则适用于所有叶成员或所有合并成员的属性值，但不能同时适用于这两者。</span><span class="sxs-lookup"><span data-stu-id="3f04e-133">Business rules apply to the attribute values for all leaf or all consolidated members, not both.</span></span>  
  
-   <span data-ttu-id="3f04e-134">业务规则可以应用于模型的所有 **“打开”** 或 **“已锁定”** 版本。</span><span class="sxs-lookup"><span data-stu-id="3f04e-134">Business rules can be applied to any version of a model that is **Open** or **Locked**.</span></span>  
  
-   <span data-ttu-id="3f04e-135">应用业务规则时对数据所做的更改不记录为事务。</span><span class="sxs-lookup"><span data-stu-id="3f04e-135">Changes made to data when business rules are applied are not logged as transactions.</span></span>  
  
-   <span data-ttu-id="3f04e-136">一个业务规则不能包含多个 **“启动工作流”** 操作。</span><span class="sxs-lookup"><span data-stu-id="3f04e-136">A business rule cannot contain more than one **start workflow** action.</span></span>  
  
## <a name="system-settings"></a><span data-ttu-id="3f04e-137">系统设置</span><span class="sxs-lookup"><span data-stu-id="3f04e-137">System Settings</span></span>  
 <span data-ttu-id="3f04e-138">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 中有两个会影响业务规则的设置。</span><span class="sxs-lookup"><span data-stu-id="3f04e-138">There are two settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] that affect business rules.</span></span> <span data-ttu-id="3f04e-139">可以在 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 中或直接在“系统设置”表中调整这些设置。</span><span class="sxs-lookup"><span data-stu-id="3f04e-139">You can adjust these settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] or directly in the System Settings table.</span></span> <span data-ttu-id="3f04e-140">有关详细信息，请参阅[系统设置 (Master Data Services)](../../2014/master-data-services/system-settings-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3f04e-140">For more information, see [System Settings &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="3f04e-141">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="3f04e-141">Related Tasks</span></span>  
  
|<span data-ttu-id="3f04e-142">任务说明</span><span class="sxs-lookup"><span data-stu-id="3f04e-142">Task Description</span></span>|<span data-ttu-id="3f04e-143">主题</span><span class="sxs-lookup"><span data-stu-id="3f04e-143">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="3f04e-144">创建和发布新的业务规则。</span><span class="sxs-lookup"><span data-stu-id="3f04e-144">Create and publish a new business rule.</span></span>|[<span data-ttu-id="3f04e-145">创建和发布业务规则 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3f04e-145">Create and Publish a Business Rule &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)|  
|<span data-ttu-id="3f04e-146">向业务规则添加多个条件。</span><span class="sxs-lookup"><span data-stu-id="3f04e-146">Add multiple conditions to a business rule.</span></span>|[<span data-ttu-id="3f04e-147">向业务规则添加多个条件 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="3f04e-147">Add Multiple Conditions to a Business Rule &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md)|  
|<span data-ttu-id="3f04e-148">创建业务规则来要求属性具有值。</span><span class="sxs-lookup"><span data-stu-id="3f04e-148">Create a business rule to require that attributes have values.</span></span>|[<span data-ttu-id="3f04e-149">要求属性值 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="3f04e-149">Require Attribute Values &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/require-attribute-values-master-data-services.md)|  
|<span data-ttu-id="3f04e-150">创建业务规则以便基于对属性值的更改执行操作。</span><span class="sxs-lookup"><span data-stu-id="3f04e-150">Create a business rule to take an action based on changes to attribute values.</span></span>|[<span data-ttu-id="3f04e-151">基于属性值更改启动操作 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3f04e-151">Initiate Actions Based on Attribute Value Changes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
|<span data-ttu-id="3f04e-152">更改现有业务规则的名称。</span><span class="sxs-lookup"><span data-stu-id="3f04e-152">Change the name of an existing business rule.</span></span>|[<span data-ttu-id="3f04e-153">更改业务规则名称 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="3f04e-153">Change a Business Rule Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md)|  
|<span data-ttu-id="3f04e-154">将 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 配置为在应用业务规则时发送通知。</span><span class="sxs-lookup"><span data-stu-id="3f04e-154">Configure [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] to send notifications when business rules are applied.</span></span>|[<span data-ttu-id="3f04e-155">配置业务规则以发送通知 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3f04e-155">Configure Business Rules to Send Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)|  
|<span data-ttu-id="3f04e-156">将业务规则应用于特定成员。</span><span class="sxs-lookup"><span data-stu-id="3f04e-156">Apply business rules to specific members.</span></span>|[<span data-ttu-id="3f04e-157">针对业务规则验证特定成员 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3f04e-157">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)|  
|<span data-ttu-id="3f04e-158">排除业务规则以便不使用该规则。</span><span class="sxs-lookup"><span data-stu-id="3f04e-158">Exclude a business rule so it is not used.</span></span>|[<span data-ttu-id="3f04e-159">排除业务规则 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3f04e-159">Exclude a Business Rule &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/exclude-a-business-rule-master-data-services.md)|  
|<span data-ttu-id="3f04e-160">删除现有业务规则。</span><span class="sxs-lookup"><span data-stu-id="3f04e-160">Delete an existing business rule.</span></span>|[<span data-ttu-id="3f04e-161">删除业务规则 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3f04e-161">Delete a Business Rule &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-business-rule-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="3f04e-162">相关内容</span><span class="sxs-lookup"><span data-stu-id="3f04e-162">Related Content</span></span>  
  
-   [<span data-ttu-id="3f04e-163">Master Data Services 概述</span><span class="sxs-lookup"><span data-stu-id="3f04e-163">Master Data Services Overview</span></span>](master-data-services-overview-mds.md)  
  
-   [<span data-ttu-id="3f04e-164">版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3f04e-164">Versions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/versions-master-data-services.md)  
  
-   [<span data-ttu-id="3f04e-165">验证 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3f04e-165">Validation &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validation-master-data-services.md)  
  
-   [<span data-ttu-id="3f04e-166">更改跟踪 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="3f04e-166">Change Tracking &#40;Master Data Services&#41;</span></span>](change-tracking-master-data-services.md)  
  
  
