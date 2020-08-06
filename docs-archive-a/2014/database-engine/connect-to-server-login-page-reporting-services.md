---
title: 连接到服务器（“登录”页）(Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttors.login.f1
helpviewer_keywords:
- Connect to Server dialog box, Reporting Services
ms.assetid: d312c740-19d7-4931-84a2-88b805ec8439
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 16c1a4f8b5560e2d49d9eb13ca3bdd5594461517
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693066"
---
# <a name="connect-to-server-login-page-reporting-services"></a><span data-ttu-id="1b003-102">连接到服务器（“登录”页）(Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="1b003-102">Connect to Server (Login Page) Reporting Services</span></span>
  <span data-ttu-id="1b003-103">在连接到时，使用此选项卡可以查看或指定以下选项 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1b003-103">Use this tab to view or specify the following options when connecting to [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="1b003-104">选项</span><span class="sxs-lookup"><span data-stu-id="1b003-104">Options</span></span>  
 <span data-ttu-id="1b003-105">**服务器类型**</span><span class="sxs-lookup"><span data-stu-id="1b003-105">**Server type**</span></span>  
 <span data-ttu-id="1b003-106">从对象资源管理器进行服务器注册时，请选择要连接到何种类型的服务器： [!INCLUDE[ssDE](../includes/ssde-md.md)]、Analysis Services、Reporting Services 或 Integration Services。</span><span class="sxs-lookup"><span data-stu-id="1b003-106">When registering a server from Object Explorer, select the type of server to connect to: [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services.</span></span> <span data-ttu-id="1b003-107">对话框的其余部分只显示适用于所选服务器类型的选项。</span><span class="sxs-lookup"><span data-stu-id="1b003-107">The rest of the dialog shows only the options that apply to the selected server type.</span></span> <span data-ttu-id="1b003-108">从“已注册的服务器”注册某服务器时，“服务器类型”  框是只读的，并且与“已注册的服务器”组件中显示的服务器类型匹配。</span><span class="sxs-lookup"><span data-stu-id="1b003-108">When registering a server from Registered Servers, the **Server type** box is read-only, and matches the type of server displayed in the Registered Servers component.</span></span> <span data-ttu-id="1b003-109">若要注册其他类型的服务器，请在开始注册新服务器之前，从“已注册的服务器”工具栏中选择[!INCLUDE[ssDE](../includes/ssde-md.md)]、Analysis Services、Reporting Services 或 Integration Services。</span><span class="sxs-lookup"><span data-stu-id="1b003-109">To register a different type of server, select [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services from the Registered Servers toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="1b003-110">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="1b003-110">**Server name**</span></span>  
 <span data-ttu-id="1b003-111">您要连接到的报表服务器实例的服务器模式决定了必须输入的值。</span><span class="sxs-lookup"><span data-stu-id="1b003-111">The server mode of the report server instance you are connecting to determines the value you must enter.</span></span>  
  
 <span data-ttu-id="1b003-112">对于在本机模式下运行的报表服务器，指定要连接到的报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="1b003-112">For a report server that runs in native mode, specify the report server instance to connect to.</span></span> <span data-ttu-id="1b003-113">如果使用默认实例，服务器名通常是计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="1b003-113">If you are using the default instance, the server name is typically the name of the computer.</span></span> <span data-ttu-id="1b003-114">如果安装了命名实例，请按以下格式将实例名称附加到服务器名称： \<servername> \\<InstanceName \> 。</span><span class="sxs-lookup"><span data-stu-id="1b003-114">If you installed a named instance, append the instance name to the server name in this format: \<servername>\\<InstanceName\>.</span></span> <span data-ttu-id="1b003-115">Reporting Services 使用反斜杠字符分隔实例名。</span><span class="sxs-lookup"><span data-stu-id="1b003-115">Reporting Services uses the backslash character to delimit the instance name.</span></span>  
  
 <span data-ttu-id="1b003-116">对于在 SharePoint 集成模式下运行的报表服务器，必须指定 SharePoint 站点。</span><span class="sxs-lookup"><span data-stu-id="1b003-116">For a report server that runs in SharePoint integrated mode, you must specify a SharePoint site.</span></span> <span data-ttu-id="1b003-117">可以指定与 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]集成的站点集合中的任意站点。</span><span class="sxs-lookup"><span data-stu-id="1b003-117">You can specify any site in a site collection that is integrated with [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="1b003-118">您提供的 URL 必须包含 HTTP 或 HTTPS 前缀。</span><span class="sxs-lookup"><span data-stu-id="1b003-118">The URL that you provide must include the HTTP or HTTPS prefix.</span></span> <span data-ttu-id="1b003-119">您必须有权访问 SharePoint 站点，才能在 Management Studio 中连接到该站点。</span><span class="sxs-lookup"><span data-stu-id="1b003-119">You must have permission to access the SharePoint site in order to connect to it in Management Studio.</span></span> <span data-ttu-id="1b003-120">分配给您的权限级别将决定您可以查看和管理的项目。</span><span class="sxs-lookup"><span data-stu-id="1b003-120">The permission level you are assigned to will determine which items you can view and manage.</span></span> <span data-ttu-id="1b003-121">有关详细信息，请参阅[连接到 Management Studio 中的报表服务器](../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="1b003-121">For more information, see [Connect to a Report Server in Management Studio](../reporting-services/tools/connect-to-a-report-server-in-management-studio.md).</span></span>  
  
 <span data-ttu-id="1b003-122">**身份验证**</span><span class="sxs-lookup"><span data-stu-id="1b003-122">**Authentication**</span></span>  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="1b003-123">可以配置为接受由你提供的自定义身份验证扩展插件处理的 Windows 身份验证请求或窗体身份验证请求。</span><span class="sxs-lookup"><span data-stu-id="1b003-123">can be configured to accept Windows Authentication requests or Forms authentication requests that are handled by a custom authentication extension that you provide.</span></span> <span data-ttu-id="1b003-124">请从以下身份验证模式中选择一个，以便在连接到 Reporting Services 时使用：</span><span class="sxs-lookup"><span data-stu-id="1b003-124">Select from one of the following authentication modes when connecting to Reporting Services:</span></span>  
  
 <span data-ttu-id="1b003-125">**Windows 身份验证模式（Windows 身份验证）**</span><span class="sxs-lookup"><span data-stu-id="1b003-125">**Windows Authentication Mode (Windows Authentication)**</span></span>  
 <span data-ttu-id="1b003-126">使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 凭据连接到报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="1b003-126">Connect to the report server instance using your [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows credentials.</span></span>  
  
 <span data-ttu-id="1b003-127">**基本身份验证**</span><span class="sxs-lookup"><span data-stu-id="1b003-127">**Basic Authentication**</span></span>  
 <span data-ttu-id="1b003-128">如果将 Reporting Services 安装配置为使用基本身份验证，则使用“基本身份验证”\*\*\*\* 进行连接。</span><span class="sxs-lookup"><span data-stu-id="1b003-128">Connect using **Basic Authentication** if your Reporting Services installation is configured to use Basic Authentication.</span></span>  
  
 <span data-ttu-id="1b003-129">**窗体身份验证**</span><span class="sxs-lookup"><span data-stu-id="1b003-129">**Forms Authentication**</span></span>  
 <span data-ttu-id="1b003-130">如果将 Reporting Services 安装配置为使用自定义身份验证扩展插件，则使用“窗体身份验证”\*\*\*\* 进行连接。</span><span class="sxs-lookup"><span data-stu-id="1b003-130">Connect using **Forms Authentication** if your Reporting Services installation is configured to use a custom authentication extension.</span></span>  
  
 <span data-ttu-id="1b003-131">**用户名**</span><span class="sxs-lookup"><span data-stu-id="1b003-131">**User Name**</span></span>  
 <span data-ttu-id="1b003-132">输入用于连接的登录名。</span><span class="sxs-lookup"><span data-stu-id="1b003-132">Enter the login name to use for the connection.</span></span> <span data-ttu-id="1b003-133">只有在选择了 **“基本身份验证”** 或 **“窗体身份验证”** 时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="1b003-133">This option is only available if you have selected **Basic** or **Forms Authentication**.</span></span>  
  
 <span data-ttu-id="1b003-134">**密码**</span><span class="sxs-lookup"><span data-stu-id="1b003-134">**Password**</span></span>  
 <span data-ttu-id="1b003-135">输入用户名的密码。</span><span class="sxs-lookup"><span data-stu-id="1b003-135">Enter the password for the user name.</span></span> <span data-ttu-id="1b003-136">只有在选择了 **“基本身份验证”** 或 **“窗体身份验证”** 时，此选项才可编辑。</span><span class="sxs-lookup"><span data-stu-id="1b003-136">This option is only editable if you have selected **Basic** or **Forms Authentication**.</span></span>  
  
 <span data-ttu-id="1b003-137">**记住密码**</span><span class="sxs-lookup"><span data-stu-id="1b003-137">**Remember password**</span></span>  
 <span data-ttu-id="1b003-138">存储已经输入的密码。</span><span class="sxs-lookup"><span data-stu-id="1b003-138">Store the password you have entered.</span></span> <span data-ttu-id="1b003-139">仅当单击“选项”\*\*\*\* 时才显示此选项，而且仅当选择了使用“基本身份验证”\*\*\*\* 或“窗体身份验证”\*\*\*\* 进行连接时，它才是可编辑的。</span><span class="sxs-lookup"><span data-stu-id="1b003-139">This option is only displayed if you click **Options**, and it is only editable if you have selected to connect using **Basic** or **Forms Authentication**.</span></span>  
  
 <span data-ttu-id="1b003-140">**“连接”**</span><span class="sxs-lookup"><span data-stu-id="1b003-140">**Connect**</span></span>  
 <span data-ttu-id="1b003-141">连接到所选服务器。</span><span class="sxs-lookup"><span data-stu-id="1b003-141">Connect to the selected server.</span></span>  
  
 <span data-ttu-id="1b003-142">**选项**</span><span class="sxs-lookup"><span data-stu-id="1b003-142">**Options**</span></span>  
 <span data-ttu-id="1b003-143">显示其他服务器连接选项，例如记住密码。</span><span class="sxs-lookup"><span data-stu-id="1b003-143">Display additional server connection options, such as remembering the password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b003-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1b003-144">See Also</span></span>  
 <span data-ttu-id="1b003-145">[&#40;SSRS Configuration Manager 配置报表服务器数据库连接&#41;](../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="1b003-145">[Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="1b003-146">[在 Management Studio 中连接到报表服务器](../reporting-services/tools/connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="1b003-146">[Connect to a Report Server in Management Studio](../reporting-services/tools/connect-to-a-report-server-in-management-studio.md) </span></span>  
 [<span data-ttu-id="1b003-147">针对报表服务器的身份验证</span><span class="sxs-lookup"><span data-stu-id="1b003-147">Authentication with the Report Server</span></span>](../reporting-services/security/authentication-with-the-report-server.md)  
  
  
