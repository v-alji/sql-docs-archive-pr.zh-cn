---
title: 数据库 (SSRS 本机模式) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.databasesetup.F1
ms.assetid: 8c9bb3b3-ea77-4a5b-ba35-7451ed11083d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: bb8f1841e980279d6051e3393efdf06df238f41f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591119"
---
# <a name="database-ssrs-native-mode"></a><span data-ttu-id="de4d2-102">数据库（SSRS 本机模式）</span><span class="sxs-lookup"><span data-stu-id="de4d2-102">Database (SSRS Native Mode)</span></span>
  <span data-ttu-id="de4d2-103">使用“数据库”页创建和配置为一个或多个报表服务器实例提供内部存储的报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="de4d2-103">Use the Database page to create and configure the report server databases that provide internal storage for one or more report server instances.</span></span> <span data-ttu-id="de4d2-104">如果要配置报表服务器以使用远程报表服务器数据库，则必须使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器来创建该数据库。</span><span class="sxs-lookup"><span data-stu-id="de4d2-104">If you are configuring a report server to use a remote report server database, you must use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager to create the database.</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="de4d2-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]本机模式。</span><span class="sxs-lookup"><span data-stu-id="de4d2-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
 <span data-ttu-id="de4d2-106">创建报表服务器数据库和配置连接是一个多步骤过程。</span><span class="sxs-lookup"><span data-stu-id="de4d2-106">Creating a report server database and configuring the connection is a multi-step process.</span></span> <span data-ttu-id="de4d2-107">为了指导您完成各个步骤，此页为每种类型的任务都提供了向导。</span><span class="sxs-lookup"><span data-stu-id="de4d2-107">To guide you through the steps, this page provides Wizards for each type of task.</span></span> <span data-ttu-id="de4d2-108">还将为您创建或更新权限和登录名。</span><span class="sxs-lookup"><span data-stu-id="de4d2-108">Permissions and logins are created or updated for you.</span></span> <span data-ttu-id="de4d2-109">您可以在“进度”页中监视每个步骤的状态。</span><span class="sxs-lookup"><span data-stu-id="de4d2-109">You can monitor the status of each step in the Progress page.</span></span> <span data-ttu-id="de4d2-110">如果出现错误，您可以单击该错误以获取如何解决该错误的相关信息。</span><span class="sxs-lookup"><span data-stu-id="de4d2-110">If an error occurs, you can click the error for information on how to resolve it.</span></span>  
  
 <span data-ttu-id="de4d2-111">报表服务器数据库必须支持特定服务器模式。</span><span class="sxs-lookup"><span data-stu-id="de4d2-111">A report server database must support a specific server mode.</span></span> <span data-ttu-id="de4d2-112">默认模式为本机模式，但如果是在较大的 SharePoint 产品或技术部署中运行报表服务器，则也可以创建 SharePoint 集成模式下的报表服务器。</span><span class="sxs-lookup"><span data-stu-id="de4d2-112">The default mode is native mode, but you can also create a report server database for SharePoint integrated mode if you are running a report server in a larger deployment of a SharePoint product or technology.</span></span> <span data-ttu-id="de4d2-113">有关详细信息，请参阅[创建本机模式报表服务器数据库（SSRS 配置管理器）](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)。</span><span class="sxs-lookup"><span data-stu-id="de4d2-113">For more information, see [Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md).</span></span>  
  
 <span data-ttu-id="de4d2-114">若要打开此页，请启动 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器，然后单击导航窗格中的 **“数据库”** 。</span><span class="sxs-lookup"><span data-stu-id="de4d2-114">To open this page, start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager and click **Database** in the navigation pane.</span></span> <span data-ttu-id="de4d2-115">有关详细信息，请参阅 [Reporting Services Configuration Manager（本机模式）](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="de4d2-115">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="de4d2-116">选项</span><span class="sxs-lookup"><span data-stu-id="de4d2-116">Options</span></span>  
 <span data-ttu-id="de4d2-117">**SQL Server 名称**</span><span class="sxs-lookup"><span data-stu-id="de4d2-117">**SQL Server Name**</span></span>  
 <span data-ttu-id="de4d2-118">在“当前报表服务器数据库”中， **“SQL Server 名称”** 指定运行报表服务器数据库的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的名称。</span><span class="sxs-lookup"><span data-stu-id="de4d2-118">In Current Report Server Database, **SQL Server Name** specifies the name of the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] that runs the report server database.</span></span> <span data-ttu-id="de4d2-119">可以使用本地或远程计算机上的默认或命名实例。</span><span class="sxs-lookup"><span data-stu-id="de4d2-119">You can use a default or named instance on a local or remote computer.</span></span>  
  
 <span data-ttu-id="de4d2-120">**Database Name**</span><span class="sxs-lookup"><span data-stu-id="de4d2-120">**Database Name**</span></span>  
 <span data-ttu-id="de4d2-121">指定存储服务器数据的报表服务器数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="de4d2-121">Specifies the name of the report server database that stores server data.</span></span>  
  
 <span data-ttu-id="de4d2-122">**报表服务器模式**</span><span class="sxs-lookup"><span data-stu-id="de4d2-122">**Report Server Mode**</span></span>  
 <span data-ttu-id="de4d2-123">指示报表服务器数据库是支持本机模式还是支持 SharePoint 集成模式。</span><span class="sxs-lookup"><span data-stu-id="de4d2-123">Indicates whether the report server database supports native mode or SharePoint integrated mode.</span></span> <span data-ttu-id="de4d2-124">有关详细信息，请参阅[Reporting Services 报表服务器](../../../2014/reporting-services/reporting-services-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="de4d2-124">For more information, see [Reporting Services Report Server](../../../2014/reporting-services/reporting-services-report-server.md).</span></span>  
  
 <span data-ttu-id="de4d2-125">**更改数据库**</span><span class="sxs-lookup"><span data-stu-id="de4d2-125">**Change Database**</span></span>  
 <span data-ttu-id="de4d2-126">启动一个向导以指导您完成创建或选择报表服务器数据库所需的所有步骤。</span><span class="sxs-lookup"><span data-stu-id="de4d2-126">Start a wizard that guides you through all of the steps required for creating or selecting a report server database.</span></span>  
  
 <span data-ttu-id="de4d2-127">凭据类型</span><span class="sxs-lookup"><span data-stu-id="de4d2-127">**Credential Type**</span></span>  
 <span data-ttu-id="de4d2-128">指定报表服务器用来连接报表服务器数据库的凭据。</span><span class="sxs-lookup"><span data-stu-id="de4d2-128">Specifies credentials that the report server uses to connect to the report server database.</span></span> <span data-ttu-id="de4d2-129">可以指定的凭据类型包括服务帐户、Windows 域用户、Windows 本地用户或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库登录名。</span><span class="sxs-lookup"><span data-stu-id="de4d2-129">Credential types you can specify include the service account, a Windows domain user, Windows local user, or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database login.</span></span> <span data-ttu-id="de4d2-130">有关选择凭据的详细信息，请参阅[配置报表服务器数据库连接 &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="de4d2-130">For more information about selecting credentials, see [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="de4d2-131">**用户名**</span><span class="sxs-lookup"><span data-stu-id="de4d2-131">**User Name**</span></span>  
 <span data-ttu-id="de4d2-132">如果使用的是 Windows 凭据，请指定域用户帐户；如果使用的是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 凭据，则指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="de4d2-132">Specifies a domain user account if you are using Windows credentials, or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login if you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] credentials.</span></span> <span data-ttu-id="de4d2-133">如果使用的是 Windows 凭据，请按以下格式指定： \* \<domain> \\<帐户 \> \*。</span><span class="sxs-lookup"><span data-stu-id="de4d2-133">If you are using Windows credentials, specify them in this format: *\<domain>\\<account\>*.</span></span>  
  
 <span data-ttu-id="de4d2-134">**密码**</span><span class="sxs-lookup"><span data-stu-id="de4d2-134">**Password**</span></span>  
 <span data-ttu-id="de4d2-135">指定帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="de4d2-135">Specifies the password for the account.</span></span>  
  
 <span data-ttu-id="de4d2-136">**更改凭据**</span><span class="sxs-lookup"><span data-stu-id="de4d2-136">**Change Credentials**</span></span>  
 <span data-ttu-id="de4d2-137">启动可指导您完成以下操作所需的所有步骤的向导，这些操作包括选择不同的帐户或更新用于连接到报表服务器数据库的帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="de4d2-137">Start a wizard that guides you through all of the steps required for selecting a different account or updating the password on the account that is used to connect to the report server database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de4d2-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="de4d2-138">See Also</span></span>  
 <span data-ttu-id="de4d2-139">[&#40;SSRS Configuration Manager 创建本机模式报表服务器数据库&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md) </span><span class="sxs-lookup"><span data-stu-id="de4d2-139">[Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md) </span></span>  
 <span data-ttu-id="de4d2-140">[Reporting Services 配置管理器的 F1 帮助主题 &#40;SSRS 本机模式&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="de4d2-140">[Reporting Services Configuration Manager F1 Help Topics &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="de4d2-141">[报表服务器数据库 &#40;SSRS 本机模式&#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="de4d2-141">[Report Server Database &#40;SSRS Native Mode&#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="de4d2-142">配置报表服务器数据库连接（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="de4d2-142">Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;</span></span>](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
