---
title: 配置业务规则以发送通知 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], configuring notifications
- e-mail [Master Data Services], configuring business rules
- notifications [Master Data Services], configuring business rules
ms.assetid: b24f7b11-ab53-4642-999c-e17b543b3558
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cb1a12167dffe123e55760f031e21499fe22a945
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591940"
---
# <a name="configure-business-rules-to-send-notifications-master-data-services"></a><span data-ttu-id="87b0d-102">配置业务规则以发送通知 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="87b0d-102">Configure Business Rules to Send Notifications (Master Data Services)</span></span>
  <span data-ttu-id="87b0d-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，当您要向用户通知有关属性值更改时，请配置业务规则以发送通知。</span><span class="sxs-lookup"><span data-stu-id="87b0d-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], configure business rules to send notifications when you want to notify users about attribute value changes.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="87b0d-104">先决条件</span><span class="sxs-lookup"><span data-stu-id="87b0d-104">Prerequisites</span></span>  
 <span data-ttu-id="87b0d-105">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="87b0d-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="87b0d-106">您必须有权访问 **“系统管理”** 功能区域和 **“用户和组权限”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="87b0d-106">You must have permission to access the **System Administration** and **User and Group Permissions** functional areas.</span></span> <span data-ttu-id="87b0d-107">如果您对 **“用户和组权限”** 功能区域没有权限，则无法查看要向其发送通知的用户和组的列表。</span><span class="sxs-lookup"><span data-stu-id="87b0d-107">If you do not have permission to the **User and Group Permissions** functional area, you cannot view the list of users and groups to send notifications to.</span></span>  
  
-   <span data-ttu-id="87b0d-108">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="87b0d-108">You must be a model administrator.</span></span> <span data-ttu-id="87b0d-109">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="87b0d-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="87b0d-110">使用验证操作的业务规则必须已经存在。</span><span class="sxs-lookup"><span data-stu-id="87b0d-110">A business rule that uses a validation action must already exist.</span></span> <span data-ttu-id="87b0d-111">有关详细信息，请参阅[创建和发布业务规则 (Master Data Services)](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="87b0d-111">For more information, see [Create and Publish a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="87b0d-112">接收通知的用户或组对未能通过验证的属性必须至少具有“只读”权限。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="87b0d-112">The user or group that receives the notification must have at least **Read-only** permission to the attribute that fails validation.</span></span> <span data-ttu-id="87b0d-113">显式或隐式拒绝对属性的权限的用户或组将接收电子邮件，但将无法访问 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中的属性。</span><span class="sxs-lookup"><span data-stu-id="87b0d-113">Users or groups that are explicitly or implicitly denied permission to the attribute will receive the email but will not be able to access the attribute in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
-   <span data-ttu-id="87b0d-114">如果将邮件发送到组，则组中只有已访问了 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 的成员才会获得电子邮件。</span><span class="sxs-lookup"><span data-stu-id="87b0d-114">If mail is sent to a group, only members of the group that have accessed [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] will get the email.</span></span>  
  
### <a name="to-configure-business-rules-to-send-notifications"></a><span data-ttu-id="87b0d-115">配置业务规则以发送通知</span><span class="sxs-lookup"><span data-stu-id="87b0d-115">To configure business rules to send notifications</span></span>  
  
1.  <span data-ttu-id="87b0d-116">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="87b0d-116">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="87b0d-117">从菜单栏中，指向 **“管理”** ，然后单击 **“业务规则”**。</span><span class="sxs-lookup"><span data-stu-id="87b0d-117">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="87b0d-118">在 **“业务规则维护”** 页上，从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="87b0d-118">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="87b0d-119">从 **“实体”** 列表中，选择某一实体。</span><span class="sxs-lookup"><span data-stu-id="87b0d-119">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="87b0d-120">从 "**成员类型**" 列表中，选择成员的类型。</span><span class="sxs-lookup"><span data-stu-id="87b0d-120">From the **Member Type** list, select a type of member.</span></span>  
  
6.  <span data-ttu-id="87b0d-121">从 **“属性”** 列表中，选择某一属性或保持默认值 **“全部”**。</span><span class="sxs-lookup"><span data-stu-id="87b0d-121">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="87b0d-122">在网格中的业务规则行中，双击**通知**字段。</span><span class="sxs-lookup"><span data-stu-id="87b0d-122">In the grid, in the row for the business rule, double-click the **Notification** field.</span></span>  
  
8.  <span data-ttu-id="87b0d-123">从子菜单中，单击要向其发送电子邮件通知的用户或组。</span><span class="sxs-lookup"><span data-stu-id="87b0d-123">From the sub-menu, click a user or group to send the email notification to.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="87b0d-124">后续步骤</span><span class="sxs-lookup"><span data-stu-id="87b0d-124">Next Steps</span></span>  
  
-   <span data-ttu-id="87b0d-125">通过以下过程之一将业务规则应用到数据：</span><span class="sxs-lookup"><span data-stu-id="87b0d-125">Apply business rules to data by following one of these procedures:</span></span>  
  
    -   [<span data-ttu-id="87b0d-126">针对业务规则验证特定成员 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="87b0d-126">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [<span data-ttu-id="87b0d-127">针对业务规则验证版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="87b0d-127">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   <span data-ttu-id="87b0d-128">按如下方式配置电子邮件协议：</span><span class="sxs-lookup"><span data-stu-id="87b0d-128">Configure the email protocol as follows:</span></span>  
  
    -   [<span data-ttu-id="87b0d-129">配置电子邮件通知 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="87b0d-129">Configure Email Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-email-notifications-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="87b0d-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="87b0d-130">See Also</span></span>  
 <span data-ttu-id="87b0d-131">[通知 &#40;Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="87b0d-131">[Notifications &#40;Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md) </span></span>  
 [<span data-ttu-id="87b0d-132">配置电子邮件通知 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="87b0d-132">Configure Email Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-email-notifications-master-data-services.md)  
  
  
