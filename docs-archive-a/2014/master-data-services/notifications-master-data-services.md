---
title: 通知 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- notifications [Master Data Services]
- notifications [Master Data Services], about notifications
- e-mail [Master Data Services]
- e-mail [Master Data Services], about e-mail notifications
ms.assetid: d7ad32d5-9fe5-48fd-8c61-0b00c0aff082
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a61825f9450dd5b708aff8c3fc72f0f12732337b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590870"
---
# <a name="notifications-master-data-services"></a><span data-ttu-id="f36d1-102">通知 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f36d1-102">Notifications (Master Data Services)</span></span>
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]<span data-ttu-id="f36d1-103">可以配置为在业务规则验证失败时发送电子邮件通知或模型版本的状态发生更改。</span><span class="sxs-lookup"><span data-stu-id="f36d1-103">can be configured to send an email notification when business rule validation fails or the status of a model version changes.</span></span>  
  
## <a name="how-notifications-are-sent"></a><span data-ttu-id="f36d1-104">如何发送通知</span><span class="sxs-lookup"><span data-stu-id="f36d1-104">How Notifications Are Sent</span></span>  
 <span data-ttu-id="f36d1-105">在 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]中配置通知。</span><span class="sxs-lookup"><span data-stu-id="f36d1-105">You configure notifications in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].</span></span> <span data-ttu-id="f36d1-106">通知通过使用承载数据库的实例上的数据库邮件发送电子邮件 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f36d1-106">Notifications send email messages by using Database Mail on the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] that hosts the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="f36d1-107">有关数据库邮件的详细信息，请参阅 [机丛书中的](../relational-databases/database-mail/database-mail-configuration-objects.md) 数据库邮件配置对象 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 部分。</span><span class="sxs-lookup"><span data-stu-id="f36d1-107">For more information about Database Mail, see [Database Mail Configuration Objects](../relational-databases/database-mail/database-mail-configuration-objects.md) in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="when-notifications-are-sent"></a><span data-ttu-id="f36d1-108">何时发送通知</span><span class="sxs-lookup"><span data-stu-id="f36d1-108">When Notifications Are Sent</span></span>  
 <span data-ttu-id="f36d1-109">配置通知后，可以在以下实例中发送自动化的电子邮件通知。</span><span class="sxs-lookup"><span data-stu-id="f36d1-109">After notifications are configured, automated email notifications can be sent in the following instances.</span></span>  
  
|<span data-ttu-id="f36d1-110">实例</span><span class="sxs-lookup"><span data-stu-id="f36d1-110">Instance</span></span>|<span data-ttu-id="f36d1-111">说明</span><span class="sxs-lookup"><span data-stu-id="f36d1-111">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="f36d1-112">数据未能通过业务规则验证</span><span class="sxs-lookup"><span data-stu-id="f36d1-112">Data fails business rule validation</span></span>|<span data-ttu-id="f36d1-113">各个业务规则还必须配置为在属性值未能通过业务规则验证时发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="f36d1-113">Individual business rules must be configured to send email when an attribute value fails business rule validation.</span></span> <span data-ttu-id="f36d1-114">有关详细信息，请参阅 [配置业务规则以发送通知 (Master Data Services)](configure-business-rules-to-send-notifications-master-data-services.md)中配置通知。</span><span class="sxs-lookup"><span data-stu-id="f36d1-114">For more information, see [Configure Business Rules to Send Notifications &#40;Master Data Services&#41;](configure-business-rules-to-send-notifications-master-data-services.md).</span></span>|  
|<span data-ttu-id="f36d1-115">模型版本状态更改</span><span class="sxs-lookup"><span data-stu-id="f36d1-115">Model version status changes</span></span>|<span data-ttu-id="f36d1-116">每当模型版本的状态更改时，作为模型管理员的用户将自动收到通知。</span><span class="sxs-lookup"><span data-stu-id="f36d1-116">Each time a model version's status changes, users that are model administrators receive notifications automatically.</span></span> <span data-ttu-id="f36d1-117">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f36d1-117">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>|  
  
## <a name="system-settings"></a><span data-ttu-id="f36d1-118">系统设置</span><span class="sxs-lookup"><span data-stu-id="f36d1-118">System Settings</span></span>  
 <span data-ttu-id="f36d1-119">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 中有多个设置可以影响通知。</span><span class="sxs-lookup"><span data-stu-id="f36d1-119">There are settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] that affect notifications.</span></span> <span data-ttu-id="f36d1-120">可以在 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 中或直接在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库的“系统设置”表中调整这些设置。</span><span class="sxs-lookup"><span data-stu-id="f36d1-120">You can adjust these settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] or directly in the System Settings table in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="f36d1-121">有关详细信息，请参阅[系统设置 (Master Data Services)](../../2014/master-data-services/system-settings-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f36d1-121">For more information, see [System Settings &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="f36d1-122">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="f36d1-122">Related Tasks</span></span>  
  
|<span data-ttu-id="f36d1-123">任务说明</span><span class="sxs-lookup"><span data-stu-id="f36d1-123">Task Description</span></span>|<span data-ttu-id="f36d1-124">主题</span><span class="sxs-lookup"><span data-stu-id="f36d1-124">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="f36d1-125">配置 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 以发送电子邮件通知。</span><span class="sxs-lookup"><span data-stu-id="f36d1-125">Configure [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] to send email notifications.</span></span>|[<span data-ttu-id="f36d1-126">配置电子邮件通知 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f36d1-126">Configure Email Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-email-notifications-master-data-services.md)|  
|<span data-ttu-id="f36d1-127">配置 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 以在属性值更改时发送通知。</span><span class="sxs-lookup"><span data-stu-id="f36d1-127">Configure [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] to send notifications when attribute values change.</span></span>|[<span data-ttu-id="f36d1-128">配置业务规则以发送通知 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f36d1-128">Configure Business Rules to Send Notifications &#40;Master Data Services&#41;</span></span>](configure-business-rules-to-send-notifications-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="f36d1-129">相关内容</span><span class="sxs-lookup"><span data-stu-id="f36d1-129">Related Content</span></span>  
  
-   [<span data-ttu-id="f36d1-130">业务规则 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f36d1-130">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
-   [<span data-ttu-id="f36d1-131">版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f36d1-131">Versions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/versions-master-data-services.md)  
  
-   [<span data-ttu-id="f36d1-132">电子邮件通知故障排除 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f36d1-132">Troubleshooting Email Notifications (Master Data Services)</span></span>](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-email-notifications-master-data-services.aspx)  
  
  
