---
title: 配置电子邮件通知 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- e-mail [Master Data Services], configuring
- notifications [Master Data Services], configuring notifications
ms.assetid: 4241a6ab-7465-471b-9890-57c6b572037e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: baf60677435122af00f5ee5492e47bafaa45a3ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591939"
---
# <a name="configure-email-notifications-master-data-services"></a><span data-ttu-id="0d97c-102">配置电子邮件通知 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0d97c-102">Configure Email Notifications (Master Data Services)</span></span>
  <span data-ttu-id="0d97c-103">当您希望 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 自动发送电子邮件时，请配置通知电子邮件。</span><span class="sxs-lookup"><span data-stu-id="0d97c-103">Configure notification emails when you want [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] to send email messages automatically.</span></span>  
  
### <a name="to-configure-notifications"></a><span data-ttu-id="0d97c-104">配置通知</span><span class="sxs-lookup"><span data-stu-id="0d97c-104">To configure notifications</span></span>  
  
1.  <span data-ttu-id="0d97c-105">在 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]中的 **“数据库”** 页上，选择您的 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="0d97c-105">In [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], on the **Database** page, select your [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="0d97c-106">在 **“系统设置”** 部分中，单击 **“创建配置文件”**。</span><span class="sxs-lookup"><span data-stu-id="0d97c-106">In the **System Settings** section, click **Create Profile**.</span></span>  
  
3.  <span data-ttu-id="0d97c-107">填写所有必填字段。</span><span class="sxs-lookup"><span data-stu-id="0d97c-107">Complete all required fields.</span></span> <span data-ttu-id="0d97c-108">有关详细信息，请参阅[“创建数据库邮件配置文件和帐户”对话框（Master Data Services 配置管理器）](../../2014/master-data-services/create-database-mail-profile-and-account-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="0d97c-108">For more information, see [Create Database Mail Profile and Account Dialog Box &#40;Master Data Services Configuration Manager&#41;](../../2014/master-data-services/create-database-mail-profile-and-account-dialog-box.md).</span></span>  
  
4.  <span data-ttu-id="0d97c-109">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="0d97c-109">Click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0d97c-110">在配置通知之后，您无法使用 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 进行更改。</span><span class="sxs-lookup"><span data-stu-id="0d97c-110">After you configure notifications, you cannot use [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] to make changes.</span></span> <span data-ttu-id="0d97c-111">必须直接在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库中直接进行更改。</span><span class="sxs-lookup"><span data-stu-id="0d97c-111">You must make changes directly in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="0d97c-112">有关详细信息，请参阅 [Database Mail Configuration Objects](../relational-databases/database-mail/database-mail-configuration-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="0d97c-112">For more information, see [Database Mail Configuration Objects](../relational-databases/database-mail/database-mail-configuration-objects.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="0d97c-113">后续步骤</span><span class="sxs-lookup"><span data-stu-id="0d97c-113">Next Steps</span></span>  
  
-   <span data-ttu-id="0d97c-114">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 中有多个设置可以影响通知。</span><span class="sxs-lookup"><span data-stu-id="0d97c-114">There are settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] that affect notifications.</span></span> <span data-ttu-id="0d97c-115">可以在 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 中或直接在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库的“系统设置”表中调整这些设置。</span><span class="sxs-lookup"><span data-stu-id="0d97c-115">You can adjust these settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] or directly in the System Settings table in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="0d97c-116">有关详细信息，请参阅[系统设置 (Master Data Services)](system-settings-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="0d97c-116">For more information, see [System Settings &#40;Master Data Services&#41;](system-settings-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d97c-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0d97c-117">See Also</span></span>  
 <span data-ttu-id="0d97c-118">[通知 &#40;Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="0d97c-118">[Notifications &#40;Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md) </span></span>  
 <span data-ttu-id="0d97c-119">[ (Master Data Services 的电子邮件通知疑难解答) ](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-email-notifications-master-data-services.aspx) </span><span class="sxs-lookup"><span data-stu-id="0d97c-119">[Troubleshooting Email Notifications (Master Data Services)](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-email-notifications-master-data-services.aspx) </span></span>  
 [<span data-ttu-id="0d97c-120">配置业务规则以发送通知 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0d97c-120">Configure Business Rules to Send Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  
