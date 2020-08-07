---
title: 更改凭据向导 (SSRS 本机模式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.changecredentialswizard.F1
helpviewer_keywords:
- Change Credentials Wizard
- report server database, reconfigure
ms.assetid: 9eb4060a-9c3e-41e0-8767-3cfaebc45de7
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0f2e84ec59f1241a10ce52e597920827f3afbc06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586225"
---
# <a name="change-credentials-wizard-ssrs-native-mode"></a><span data-ttu-id="bd612-102">更改凭据向导（SSRS 本机模式）</span><span class="sxs-lookup"><span data-stu-id="bd612-102">Change Credentials Wizard (SSRS Native Mode)</span></span>
  <span data-ttu-id="bd612-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器提供了更改凭据向导，可引导您完成重新配置报表服务器用于连接到报表服务器数据库的帐户的步骤。</span><span class="sxs-lookup"><span data-stu-id="bd612-103">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager provides the Change Credentials Wizard to guide you through the steps of reconfiguring the account that the report server uses to connect to the report server database.</span></span> <span data-ttu-id="bd612-104">更改凭据时，配置管理器将为报表服务器当前使用的报表服务器数据库更新数据库服务器的所有权限和数据库登录信息。</span><span class="sxs-lookup"><span data-stu-id="bd612-104">When you change credentials, the Configuration Manager will update all permissions and database login information on the database server for the report server database that is actively used by the report server.</span></span>  
  
 <span data-ttu-id="bd612-105">若要启动此向导，请在 **配置管理器中的“数据库”页上单击** “更改凭据” [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="bd612-105">To start the wizard, click **Change Credentials** on the Database page in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="bd612-106">有关如何启动 Configuration Manager 的说明 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，请参阅[Reporting Services 配置管理器 &#40;本机模式&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="bd612-106">For instructions on how to start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="bd612-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]本机模式。</span><span class="sxs-lookup"><span data-stu-id="bd612-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
## <a name="options"></a><span data-ttu-id="bd612-108">选项</span><span class="sxs-lookup"><span data-stu-id="bd612-108">Options</span></span>  
 <span data-ttu-id="bd612-109">**数据库服务器**</span><span class="sxs-lookup"><span data-stu-id="bd612-109">**Database Server**</span></span>  
 <span data-ttu-id="bd612-110">指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 运行 Report Server 数据库的实例的名称。</span><span class="sxs-lookup"><span data-stu-id="bd612-110">Specifies the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance that runs the report server database.</span></span>  
  
 <span data-ttu-id="bd612-111">若要连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例，必须使用有权登录到服务器并更新数据库信息的凭据。</span><span class="sxs-lookup"><span data-stu-id="bd612-111">To connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance, you must use credentials that have permission to log on to the server and update database information.</span></span> <span data-ttu-id="bd612-112">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器使用您当前的 Windows 凭据，但如果您没有登录名或数据库权限，可以指定一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库登录名。</span><span class="sxs-lookup"><span data-stu-id="bd612-112">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager uses your current Windows credentials, but if you do not have a login or database permissions, you can specify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database login.</span></span>  
  
 <span data-ttu-id="bd612-113">您不能指定其他 Windows 凭据。</span><span class="sxs-lookup"><span data-stu-id="bd612-113">You cannot specify different Windows credentials.</span></span> <span data-ttu-id="bd612-114">如果您希望以其他 Windows 用户身份连接，请以该用户身份登录，然后启动 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器。</span><span class="sxs-lookup"><span data-stu-id="bd612-114">If you want to connect as a different Windows user, login as that user and then start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span>  
  
 <span data-ttu-id="bd612-115">**凭据**</span><span class="sxs-lookup"><span data-stu-id="bd612-115">**Credentials**</span></span>  
 <span data-ttu-id="bd612-116">指定用于将报表服务器连接到报表服务器数据库的帐户。</span><span class="sxs-lookup"><span data-stu-id="bd612-116">Specifies the account by which the report server connects to the report server database.</span></span> <span data-ttu-id="bd612-117">有效值包括报表服务器 Web 服务的服务帐户、在您要用来承载报表服务器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上定义的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 数据库登录名，或 Windows 帐户。</span><span class="sxs-lookup"><span data-stu-id="bd612-117">Valid values include the service account of the Report Server Web service, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database login defined on the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance you are using to host the report server, or a Windows account.</span></span> <span data-ttu-id="bd612-118">如果你使用的是 Windows 帐户，则可以指定本地帐户 (\* \<computername> \\<用户名 \> *) 如果 Report Server 和数据库位于同一台计算机上，或者如果域用户帐户在同一个域中的不同计算机上 (<* \<domain> \\ 用户名 \> \*) ，则可以指定该帐户。</span><span class="sxs-lookup"><span data-stu-id="bd612-118">If you are using a Windows account, you can specify a local account (*\<computername>\\<username\>*) if the report server and the database are on the same computer, or a domain user account (*\<domain>\\<username\>*) if they are on different computers in the same domain.</span></span>  
  
 <span data-ttu-id="bd612-119">报表服务器将创建一个数据库登录名，并为您指定的帐户分配数据库权限。</span><span class="sxs-lookup"><span data-stu-id="bd612-119">The report server will create a database login and assign database permissions for the account you specify.</span></span>  
  
 <span data-ttu-id="bd612-120">报表服务器自身不创建帐户。</span><span class="sxs-lookup"><span data-stu-id="bd612-120">The report server does not create the account itself.</span></span> <span data-ttu-id="bd612-121">您指定的帐户必须已经存在，并且对于部署配置而言必须是有效的。</span><span class="sxs-lookup"><span data-stu-id="bd612-121">The account you specify must already exist and it must be valid for your deployment configuration.</span></span> <span data-ttu-id="bd612-122">具体来说，如果数据库位于远程计算机上并且您希望使用 Windows 帐户，则您必须指定对该计算机拥有登录权限的帐户。</span><span class="sxs-lookup"><span data-stu-id="bd612-122">Specifically, if the database is on a remote computer and you want to use a Windows account, you must specify an account that has log on permissions on that computer.</span></span>  
  
 <span data-ttu-id="bd612-123">如果计算机位于其他域或不可信域中，请考虑使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库登录名。</span><span class="sxs-lookup"><span data-stu-id="bd612-123">If the computer is in a different or non-trusted domain, consider using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database login.</span></span> <span data-ttu-id="bd612-124">有关选择帐户的详细信息，请参阅[配置报表服务器数据库连接 &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="bd612-124">For more information about choosing an account, see [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="bd612-125">**摘要**</span><span class="sxs-lookup"><span data-stu-id="bd612-125">**Summary**</span></span>  
 <span data-ttu-id="bd612-126">在向导运行之前验证设置。</span><span class="sxs-lookup"><span data-stu-id="bd612-126">Verify the settings before the wizard runs.</span></span>  
  
 <span data-ttu-id="bd612-127">**进度和完成**</span><span class="sxs-lookup"><span data-stu-id="bd612-127">**Progress and Finish**</span></span>  
 <span data-ttu-id="bd612-128">监视每个任务的进度。</span><span class="sxs-lookup"><span data-stu-id="bd612-128">Monitor the progress of each task.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd612-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bd612-129">See Also</span></span>  
 <span data-ttu-id="bd612-130">[数据库 &#40;SSRS 本机模式&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="bd612-130">[Database &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="bd612-131">[更改数据库向导 &#40;SSRS 本机模式&#41;](../../../2014/sql-server/install/change-database-wizard-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="bd612-131">[Change Database Wizard &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/change-database-wizard-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="bd612-132">[&#40;SSRS Configuration Manager 创建本机模式报表服务器数据库&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md) </span><span class="sxs-lookup"><span data-stu-id="bd612-132">[Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md) </span></span>  
 <span data-ttu-id="bd612-133">[Reporting Services 配置管理器的 F1 帮助主题 &#40;SSRS 本机模式&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="bd612-133">[Reporting Services Configuration Manager F1 Help Topics &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="bd612-134">配置报表服务器数据库连接（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="bd612-134">Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;</span></span>](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
