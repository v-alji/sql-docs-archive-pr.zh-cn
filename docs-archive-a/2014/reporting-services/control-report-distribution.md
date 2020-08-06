---
title: 控制报表分发 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], report distribution
- subscriptions [Reporting Services], e-mail
- subscriptions [Reporting Services], file share delivery
- file share delivery [Reporting Services]
- e-mail [Reporting Services]
- subscriptions [Reporting Services], security
- mail [Reporting Services]
ms.assetid: 8f15e2c6-a647-4b05-a519-1743b5d8654c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: de8a27801ef89f10bf303cee17d1c2d0e1081c5a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576544"
---
# <a name="control-report-distribution"></a><span data-ttu-id="b2a4b-102">控制报表分发</span><span class="sxs-lookup"><span data-stu-id="b2a4b-102">Control Report Distribution</span></span>
  <span data-ttu-id="b2a4b-103">您可以配置报表服务器，以降低电子邮件和文件共享分发引起的安全风险。</span><span class="sxs-lookup"><span data-stu-id="b2a4b-103">You can configure a report server to reduce the security risks associated with e-mail and file share distribution.</span></span>  
  
## <a name="securing-reports"></a><span data-ttu-id="b2a4b-104">保护报表</span><span class="sxs-lookup"><span data-stu-id="b2a4b-104">Securing Reports</span></span>  
 <span data-ttu-id="b2a4b-105">控制报表分发的第一步是保护报表，以防止未经授权的访问。</span><span class="sxs-lookup"><span data-stu-id="b2a4b-105">The first step in controlling report distribution is to secure the report against unauthorized access.</span></span> <span data-ttu-id="b2a4b-106">报表必须使用对所有传递都相同的一组存储凭据，才可以在订阅中使用。</span><span class="sxs-lookup"><span data-stu-id="b2a4b-106">To be used in a subscription, a report must use a stored set of credentials that do not vary for individual deliveries.</span></span> <span data-ttu-id="b2a4b-107">任何可以访问报表服务器上报表的用户都可以运行报表，并且有可能分发报表。</span><span class="sxs-lookup"><span data-stu-id="b2a4b-107">Any user who can access the report on the report server can run it and possibly distribute it.</span></span> <span data-ttu-id="b2a4b-108">为了防止发生这种情况，您必须限制报表访问，只允许需要报表的用户访问报表。</span><span class="sxs-lookup"><span data-stu-id="b2a4b-108">To prevent this from occurring, you must limit report access to only those users who require it.</span></span> <span data-ttu-id="b2a4b-109">有关详细信息，请参阅[保护报表和资源](security/secure-reports-and-resources.md)和[安全文件夹](security/secure-folders.md)。</span><span class="sxs-lookup"><span data-stu-id="b2a4b-109">For more information, see [Secure Reports and Resources](security/secure-reports-and-resources.md) and [Secure Folders](security/secure-folders.md).</span></span>  
  
 <span data-ttu-id="b2a4b-110">不能通过订阅的方式分发使用数据库安全性授予访问权限的高度机密报表。</span><span class="sxs-lookup"><span data-stu-id="b2a4b-110">Highly confidential reports that use database security to authorize access cannot be distributed by way of subscription.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b2a4b-111">报表以文件的形式传输。</span><span class="sxs-lookup"><span data-stu-id="b2a4b-111">Reports are transported as files.</span></span> <span data-ttu-id="b2a4b-112">适用于文件的风险和安全措施同样适用于保存到磁盘或以附件形式发送的报表。</span><span class="sxs-lookup"><span data-stu-id="b2a4b-112">The risks and safeguards that apply to files apply equally to reports that are saved to disk or sent as attachments.</span></span> <span data-ttu-id="b2a4b-113">具有文件访问权的任何用户都可以根据自己的需要分发或使用相应的文件。</span><span class="sxs-lookup"><span data-stu-id="b2a4b-113">Any user who has access to a file can distribute or use the file at his or her discretion.</span></span>  
  
## <a name="controlling-e-mail-delivery"></a><span data-ttu-id="b2a4b-114">控制电子邮件传递</span><span class="sxs-lookup"><span data-stu-id="b2a4b-114">Controlling E-Mail Delivery</span></span>  
 <span data-ttu-id="b2a4b-115">您可以配置报表服务器，使电子邮件分发仅限于特定主机域。</span><span class="sxs-lookup"><span data-stu-id="b2a4b-115">You can configure a report server to limit e-mail distribution to specific host domains.</span></span> <span data-ttu-id="b2a4b-116">例如，您可以防止报表服务器将报表传递到所有域，而只传递到 RSReportServer 配置文件所列出的域。</span><span class="sxs-lookup"><span data-stu-id="b2a4b-116">For example, you can prevent a report server from delivering a report to all domains except those listed in the RSReportServer configuration file.</span></span>  
  
 <span data-ttu-id="b2a4b-117">还可以设置配置设置，以在订阅中隐藏 **“收件人”** 字段。</span><span class="sxs-lookup"><span data-stu-id="b2a4b-117">You can also set configuration settings to hide the **To** field in a subscription.</span></span> <span data-ttu-id="b2a4b-118">在这种情况下，报表只能传递给定义订阅的用户。</span><span class="sxs-lookup"><span data-stu-id="b2a4b-118">In this case, reports are delivered only to the user defining the subscription.</span></span> <span data-ttu-id="b2a4b-119">但是，报表发送给用户后，您无法有效地防止转发报表。</span><span class="sxs-lookup"><span data-stu-id="b2a4b-119">However, after a report is sent to a user, you cannot explicitly prevent it from being forwarded.</span></span>  
  
 <span data-ttu-id="b2a4b-120">控制报表分发的最有效的方式是，将报表服务器配置为只发送报表服务器 URL。</span><span class="sxs-lookup"><span data-stu-id="b2a4b-120">The most effective way to control report distribution is to configure a report server to send only a report server URL.</span></span> <span data-ttu-id="b2a4b-121">报表服务器使用 Windows 身份验证和基于角色的授权模型来控制报表的访问权限。</span><span class="sxs-lookup"><span data-stu-id="b2a4b-121">The report server uses Windows Authentication and a role-based authorization model to control access to a report.</span></span> <span data-ttu-id="b2a4b-122">如果用户意外地通过电子邮件收到无权查看的报表，报表服务器不会显示该报表。</span><span class="sxs-lookup"><span data-stu-id="b2a4b-122">If a user accidentally receives through e-mail a report that he or she is not authorized to view, the report server will not display the report.</span></span>  
  
## <a name="controlling-file-share-delivery"></a><span data-ttu-id="b2a4b-123">控制文件共享传递</span><span class="sxs-lookup"><span data-stu-id="b2a4b-123">Controlling File Share Delivery</span></span>  
 <span data-ttu-id="b2a4b-124">文件共享传递用于将报表发送到硬盘上的文件。</span><span class="sxs-lookup"><span data-stu-id="b2a4b-124">File share delivery is used to send a report to a file on a hard disk.</span></span> <span data-ttu-id="b2a4b-125">文件保存到磁盘后，就不再受报表服务器用于控制用户访问权限的基于角色安全模式的限制。</span><span class="sxs-lookup"><span data-stu-id="b2a4b-125">After the file has been saved to disk, it is no longer subject to the role-based security model that the report server uses to control user access.</span></span> <span data-ttu-id="b2a4b-126">若要保护已传递到磁盘的报表，可以对文件本身或报表所在的文件夹设置访问控制列表 (ACL)。</span><span class="sxs-lookup"><span data-stu-id="b2a4b-126">To secure a report that has been delivered to disk, you can place Access Control Lists (ACLs) on the file itself or on the folder that contains it.</span></span> <span data-ttu-id="b2a4b-127">根据您的操作系统情况，可能还会有其他可用的安全选项。</span><span class="sxs-lookup"><span data-stu-id="b2a4b-127">Additional security options might be available, depending on your operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2a4b-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b2a4b-128">See Also</span></span>  
 <span data-ttu-id="b2a4b-129">[配置报表服务器，以便 &#40;SSRS Configuration Manager 发送电子邮件&#41;](../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="b2a4b-129">[Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="b2a4b-130">[订阅和传递 (Reporting Services)](subscriptions/subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="b2a4b-130">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md) </span></span>  
 [<span data-ttu-id="b2a4b-131">创建和管理本机模式报表服务器的订阅</span><span class="sxs-lookup"><span data-stu-id="b2a4b-131">Create and Manage Subscriptions for Native Mode Report Servers</span></span>](../../2014/reporting-services/create-manage-subscriptions-native-mode-report-servers.md)  
  
  
