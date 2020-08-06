---
title: 电子邮件设置-Configuration Manager (SSRS 本机模式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.rsconfigtool.emailsettings.f1
helpviewer_keywords:
- SQL11.rsconfigtool.emailsettings.F1
ms.assetid: cdad1529-bfa6-41fb-9863-d9ff1b802577
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8c5f276f8d6566e052ee291118eb1d1c12fbddc9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689793"
---
# <a name="e-mail-settings---configuration-manager-ssrs-native-mode"></a><span data-ttu-id="c9dde-102">电子邮件设置 - 配置管理器（SSRS 本机模式）</span><span class="sxs-lookup"><span data-stu-id="c9dde-102">E-mail Settings - Configuration Manager (SSRS Native Mode)</span></span>
  <span data-ttu-id="c9dde-103">使用此页可指定简单邮件传输协议 (SMTP) 设置，这些设置用于启用报表服务器的报表服务器电子邮件传递功能。</span><span class="sxs-lookup"><span data-stu-id="c9dde-103">Use this page to specify Simple Mail Transport Protocol (SMTP) settings that enable report server e-mail delivery from the report server.</span></span> <span data-ttu-id="c9dde-104">可使用报表服务器电子邮件传递扩展插件通过电子邮件订阅来分发报表或报表处理通知。</span><span class="sxs-lookup"><span data-stu-id="c9dde-104">You can use the Report Server E-Mail delivery extension to distribute reports or report processing notifications through e-mail subscriptions.</span></span> <span data-ttu-id="c9dde-105">报表服务器电子邮件传递扩展插件需要使用 SMTP 服务器并在“发件人:”字段中使用电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="c9dde-105">The Report Server E-Mail delivery extension requires an SMTP server and an e-mail address to use in the From: field.</span></span>  
  
 <span data-ttu-id="c9dde-106">其他的配置设置（包括限制邮件服务器主机和呈现扩展插件可用性的设置）可用于进一步自定义电子邮件订阅。</span><span class="sxs-lookup"><span data-stu-id="c9dde-106">Additional configuration settings can be used to further customize e-mail subscriptions, including settings that restrict mail server hosts and rendering extension availability.</span></span> <span data-ttu-id="c9dde-107">不能在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器中指定这些设置。</span><span class="sxs-lookup"><span data-stu-id="c9dde-107">You cannot specify these settings in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="c9dde-108">若要配置其他设置，必须手动编辑 RSReportServer.config 文件。</span><span class="sxs-lookup"><span data-stu-id="c9dde-108">To configure the additional settings, you must manually edit the RSReportServer.config file.</span></span> <span data-ttu-id="c9dde-109">有关详细信息，请参阅联机丛书中的[配置报表服务器以进行电子邮件传递 &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)和[Reporting Services 配置文件](../report-server/reporting-services-configuration-files.md) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c9dde-109">For more information, see [Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) and [Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="c9dde-110">若要打开此页，请启动 Reporting Services 配置管理器并在导航窗格中单击 "**电子邮件设置**"。</span><span class="sxs-lookup"><span data-stu-id="c9dde-110">To open this page, start the Reporting Services Configuration Manager and click **E-mail Settings** in the navigation pane.</span></span> <span data-ttu-id="c9dde-111">有关详细信息，请参阅 [Reporting Services Configuration Manager（本机模式）](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="c9dde-111">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="c9dde-112">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]本机模式。</span><span class="sxs-lookup"><span data-stu-id="c9dde-112">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c9dde-113">选项</span><span class="sxs-lookup"><span data-stu-id="c9dde-113">Options</span></span>  
 <span data-ttu-id="c9dde-114">**发件人地址**</span><span class="sxs-lookup"><span data-stu-id="c9dde-114">**Sender Address**</span></span>  
 <span data-ttu-id="c9dde-115">指定要在所生成电子邮件的“发件人:”字段中使用的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="c9dde-115">Specifies the e-mail address to use in the From: field of a generated e-mail.</span></span> <span data-ttu-id="c9dde-116">您必须指定一个有权从 SMTP 服务器中发送邮件的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="c9dde-116">You must specify a user account that has permission to send mail from the SMTP server.</span></span>  
  
 <span data-ttu-id="c9dde-117">**当前 SMTP 传递方法**</span><span class="sxs-lookup"><span data-stu-id="c9dde-117">**Current SMTP Delivery Method**</span></span>  
 <span data-ttu-id="c9dde-118">指定报表服务器电子邮件通过 SMTP 服务器进行路由。</span><span class="sxs-lookup"><span data-stu-id="c9dde-118">Specifies that report server e-mail is routed through an SMTP server.</span></span> <span data-ttu-id="c9dde-119">这是可以在 Reporting Services 配置管理器中指定的唯一传递方法。</span><span class="sxs-lookup"><span data-stu-id="c9dde-119">This is the only delivery method that you can specify in the Reporting Services Configuration Manager.</span></span>  
  
 <span data-ttu-id="c9dde-120">另一种传递方法是使用本地 SMTP 服务拾取目录。</span><span class="sxs-lookup"><span data-stu-id="c9dde-120">An alternative delivery method is to use a local SMTP service pickup directory.</span></span> <span data-ttu-id="c9dde-121">如果网络 SMTP 服务不可用，则可以使用此传递方法。</span><span class="sxs-lookup"><span data-stu-id="c9dde-121">You can use this delivery method if a network SMTP service is not available.</span></span> <span data-ttu-id="c9dde-122">若要指定本地 SMTP 服务拾取目录，必须编辑 RSReportServer.config 文件。</span><span class="sxs-lookup"><span data-stu-id="c9dde-122">To specify a local SMTP service pickup directory, you must edit the RSReportServer.config file.</span></span> <span data-ttu-id="c9dde-123">如果您编辑配置文件以使用本地 SMTP 服务拾取目录，Reporting Services 配置管理器会将 **“传递方法”** 选项设置为“自定义”，以指示传递方法在配置文件中指定。 \*\*</span><span class="sxs-lookup"><span data-stu-id="c9dde-123">If you edit the configuration file to use a local SMTP service pickup directory, the Reporting Services Configuration Manager sets the **Delivery method** option to *custom* to indicate that the delivery method is specified in the configuration file.</span></span>  
  
 <span data-ttu-id="c9dde-124">在配置文件中，可以通过 `SendUsing` 配置设置来设置传递方法。</span><span class="sxs-lookup"><span data-stu-id="c9dde-124">In the configuration file, the delivery method is set through the `SendUsing` configuration setting.</span></span> <span data-ttu-id="c9dde-125">有关指定设置的详细信息 `SendUsing` ，请参阅[为电子邮件传递配置报表服务器 &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="c9dde-125">For more information about specifying the `SendUsing` setting, see [Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="c9dde-126">**SMTP 服务器**</span><span class="sxs-lookup"><span data-stu-id="c9dde-126">**SMTP Server**</span></span>  
 <span data-ttu-id="c9dde-127">指定要使用的 SMTP 服务器或网关。</span><span class="sxs-lookup"><span data-stu-id="c9dde-127">Specify the SMTP server or gateway to use.</span></span> <span data-ttu-id="c9dde-128">可以使用网络中的本地服务器或 SMTP 服务器。</span><span class="sxs-lookup"><span data-stu-id="c9dde-128">You can use a local server or an SMTP server on your network.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9dde-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c9dde-129">See Also</span></span>  
 <span data-ttu-id="c9dde-130">[配置报表服务器，以便 &#40;SSRS Configuration Manager 发送电子邮件&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="c9dde-130">[Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="c9dde-131">Reporting Services 配置管理器的 F1 帮助主题 &#40;SSRS 本机模式&#41;</span><span class="sxs-lookup"><span data-stu-id="c9dde-131">Reporting Services Configuration Manager F1 Help Topics &#40;SSRS Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)  
  
  
