---
title: 创建本机模式报表服务器数据库（SSRS 配置管理器）| Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], databases
- databases [Reporting Services], creating
ms.assetid: 81b9f4ad-800b-4688-8b47-a5a83dc8ff10
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 06ad4afe3b8d70899d7299f3b4eb7b97eef6ab66
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694301"
---
# <a name="create-a-native-mode-report-server-database--ssrs-configuration-manager"></a><span data-ttu-id="e7d52-102">创建本机模式报表服务器数据库（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="e7d52-102">Create a Native Mode Report Server Database  (SSRS Configuration Manager)</span></span>
  <span data-ttu-id="e7d52-103">本机模式的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库用于内部存储。</span><span class="sxs-lookup"><span data-stu-id="e7d52-103">Native Mode [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] uses a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database for internal storage.</span></span> <span data-ttu-id="e7d52-104">该数据库是必需的，它用于存储已发布的报表、模型、共享数据源、会话数据、资源和服务器元数据。</span><span class="sxs-lookup"><span data-stu-id="e7d52-104">The database is required and it is used to store published reports, models, shared data sources, session data, resources, and server metadata.</span></span>  
  
 <span data-ttu-id="e7d52-105">若要创建报表服务器数据库或更改连接字符串或凭据，请使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器的“数据库”页中的选项。</span><span class="sxs-lookup"><span data-stu-id="e7d52-105">To create a report server database or to change the connection string or credentials, use the options in the Database page in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span>  
  
||  
|-|  
|<span data-ttu-id="e7d52-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]本机模式</span><span class="sxs-lookup"><span data-stu-id="e7d52-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native Mode</span></span>|  
  
## <a name="when-to-create-or-configure-the-report-server-databases"></a><span data-ttu-id="e7d52-107">何时创建或配置报表服务器数据库</span><span class="sxs-lookup"><span data-stu-id="e7d52-107">When to Create or Configure the Report Server Databases</span></span>  
 <span data-ttu-id="e7d52-108">如果在“仅文件”模式下安装报表服务器，则必须创建和配置报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="e7d52-108">You must create and configure the report server database if you installed the report server in files-only mode.</span></span>  
  
 <span data-ttu-id="e7d52-109">如果在本机模式的默认配置下安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，则安装报表服务器实例时会自动创建和配置报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="e7d52-109">If you installed [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in either the default configuration for native mode, the report server database was created and configured automatically when the report server instance was installed.</span></span> <span data-ttu-id="e7d52-110">可以使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器查看或修改安装程序为您配置的设置。</span><span class="sxs-lookup"><span data-stu-id="e7d52-110">You can use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager to view or modify the settings that Setup configured for you.</span></span>  
  
##  <a name="before-you-start"></a><a name="rsdbrequirements"></a> <span data-ttu-id="e7d52-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="e7d52-111">Before You Start</span></span>  
 <span data-ttu-id="e7d52-112">创建或配置报表服务器数据库是一个多步骤过程。</span><span class="sxs-lookup"><span data-stu-id="e7d52-112">Creating or configuring a report server database is a multi-step process.</span></span> <span data-ttu-id="e7d52-113">创建报表服务器数据库之前，请考虑要如何指定下列各项：</span><span class="sxs-lookup"><span data-stu-id="e7d52-113">Before you create the report server database, consider how you want to specify the following items:</span></span>  
  
 <span data-ttu-id="e7d52-114">选择数据库服务器</span><span class="sxs-lookup"><span data-stu-id="e7d52-114">Select a database server</span></span>  
 <span data-ttu-id="e7d52-115">查看支持的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 版本，以及主题[创建报表服务器数据库（SSRS 配置管理器）](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)中支持的版本。</span><span class="sxs-lookup"><span data-stu-id="e7d52-115">Review the supported versions of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and review the supported editions in the topic, [Create a Report Server Database  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="e7d52-116">启用 TCP/IP 连接</span><span class="sxs-lookup"><span data-stu-id="e7d52-116">Enable TCP/IP connections</span></span>  
 <span data-ttu-id="e7d52-117">启用 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的 TCP/IP 连接。</span><span class="sxs-lookup"><span data-stu-id="e7d52-117">Enable TCP/IP connections for the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="e7d52-118">默认情况下，某些 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 版本不启用 TCP/IP。</span><span class="sxs-lookup"><span data-stu-id="e7d52-118">Some editions of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] do not enable TCP/IP by default.</span></span> <span data-ttu-id="e7d52-119">本主题中提供了相关说明。</span><span class="sxs-lookup"><span data-stu-id="e7d52-119">Instructions are provided in this topic.</span></span>  
  
 <span data-ttu-id="e7d52-120">打开 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的端口</span><span class="sxs-lookup"><span data-stu-id="e7d52-120">Open port for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 <span data-ttu-id="e7d52-121">对于远程服务器，如果使用的是防火墙软件，则必须打开 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 侦听的端口。</span><span class="sxs-lookup"><span data-stu-id="e7d52-121">For a remote server, if you are using firewall software, you must open the port that the [!INCLUDE[ssDE](../../includes/ssde-md.md)] listens on.</span></span>  
  
 <span data-ttu-id="e7d52-122">确定报表服务器凭据</span><span class="sxs-lookup"><span data-stu-id="e7d52-122">Decide on report server credentials</span></span>  
 <span data-ttu-id="e7d52-123">确定报表服务器与报表服务器数据库的连接方式。</span><span class="sxs-lookup"><span data-stu-id="e7d52-123">Decide how the report server will connect to the report server databases.</span></span> <span data-ttu-id="e7d52-124">凭据类型包括域用户帐户、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库用户帐户或报表服务器服务帐户。</span><span class="sxs-lookup"><span data-stu-id="e7d52-124">Credential types include domain user account, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database user account, or the Report Server service account.</span></span>  
  
 <span data-ttu-id="e7d52-125">这些凭据经过加密并存储在 RSReportServer.config 文件中。</span><span class="sxs-lookup"><span data-stu-id="e7d52-125">These credentials are encrypted and stored in the RSReportServer.config file.</span></span> <span data-ttu-id="e7d52-126">报表服务器将这些凭据用于与报表服务器数据库进行的连接。</span><span class="sxs-lookup"><span data-stu-id="e7d52-126">The report server uses these credentials for ongoing connections to the report server database.</span></span> <span data-ttu-id="e7d52-127">如果您要使用 Windows 用户帐户或数据库用户帐户，请确保指定已经存在的帐户。</span><span class="sxs-lookup"><span data-stu-id="e7d52-127">If you want to use a Windows user account or a database user account, be sure to specify one that already exists.</span></span> <span data-ttu-id="e7d52-128">尽管 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器将创建登录名并设置必要的权限，但不会为您创建帐户。</span><span class="sxs-lookup"><span data-stu-id="e7d52-128">Although the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager will create a login and set the necessary permissions, it will not create an account for you.</span></span> <span data-ttu-id="e7d52-129">有关详细信息，请参阅[配置报表服务器数据库连接 &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="e7d52-129">For more information, see [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="e7d52-130">确定报表服务器语言</span><span class="sxs-lookup"><span data-stu-id="e7d52-130">Decide on a report server language</span></span>  
 <span data-ttu-id="e7d52-131">选择要为报表服务器指定的语言。</span><span class="sxs-lookup"><span data-stu-id="e7d52-131">Choose a language to specify for the report server.</span></span> <span data-ttu-id="e7d52-132">当用户使用不同语言版本的浏览器连接到服务器时，预定义的角色名称、说明和“我的报表”文件夹不会以不同的语言显示。</span><span class="sxs-lookup"><span data-stu-id="e7d52-132">Predefined role names, descriptions, and the My Reports folders do not appear in different languages when users connect to the server using different language versions of a browser.</span></span>  
  
 <span data-ttu-id="e7d52-133">检查凭据以创建和设置数据库</span><span class="sxs-lookup"><span data-stu-id="e7d52-133">Check credentials to create and provision the database</span></span>  
 <span data-ttu-id="e7d52-134">确保您拥有的帐户凭据具有在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例上创建数据库的权限。</span><span class="sxs-lookup"><span data-stu-id="e7d52-134">Verify that you have account credentials that have permission to create databases on the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance.</span></span> <span data-ttu-id="e7d52-135">这些凭据用于一次性连接以创建报表服务器数据库和 **RSExecRole**。</span><span class="sxs-lookup"><span data-stu-id="e7d52-135">These credentials are used for a one-time connection to create the report server database and **RSExecRole**.</span></span> <span data-ttu-id="e7d52-136">如果登录名尚不存在，将为报表服务器所用的帐户创建一个数据库用户登录名以连接到该数据库。</span><span class="sxs-lookup"><span data-stu-id="e7d52-136">If a login does not already exist, a database user login will be created for the account used by the report server to connect to the database.</span></span> <span data-ttu-id="e7d52-137">您可以用您登录时所用的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帐户进行连接，也可以输入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库登录名。</span><span class="sxs-lookup"><span data-stu-id="e7d52-137">You can connect under the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account you are logged in as, or you can enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database login.</span></span>  
  
### <a name="to-enable-access-to-a-remote-report-server-database"></a><span data-ttu-id="e7d52-138">启用对远程报表服务器数据库的访问</span><span class="sxs-lookup"><span data-stu-id="e7d52-138">To enable access to a remote report server database</span></span>  
  
1.  <span data-ttu-id="e7d52-139">如果您使用的是远程 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例，请登录到此数据库服务器以验证或启用 TCP/IP 连接。</span><span class="sxs-lookup"><span data-stu-id="e7d52-139">If you are using a remote [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance, log on to the database server to verify or enable TCP/IP connections.</span></span>  
  
2.  <span data-ttu-id="e7d52-140">依次指向 **“开始”**、 **“所有程序”**、 **Microsoft SQL Server**、 **“配置工具”**，再单击 **“SQL Server 配置管理器”**。</span><span class="sxs-lookup"><span data-stu-id="e7d52-140">Point to **Start**, point to **All Programs**, point to **Microsoft SQL Server**, point to **Configuration Tools**, and click **SQL Server Configuration Manager**.</span></span>  
  
3.  <span data-ttu-id="e7d52-141">打开**SQL Server 网络配置**。</span><span class="sxs-lookup"><span data-stu-id="e7d52-141">Open **SQL Server Network Configuration**.</span></span>  
  
4.  <span data-ttu-id="e7d52-142">选择实例。</span><span class="sxs-lookup"><span data-stu-id="e7d52-142">Select the instance.</span></span>  
  
5.  <span data-ttu-id="e7d52-143">右键单击 " **tcp/ip** "，然后单击 "**启用**"。</span><span class="sxs-lookup"><span data-stu-id="e7d52-143">Right-click **TCP/IP** and click **Enabled**.</span></span>  
  
6.  <span data-ttu-id="e7d52-144">重启服务。</span><span class="sxs-lookup"><span data-stu-id="e7d52-144">Restart the service.</span></span>  
  
7.  <span data-ttu-id="e7d52-145">打开防火墙软件并打开 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 侦听的端口。</span><span class="sxs-lookup"><span data-stu-id="e7d52-145">Open your firewall software and open the port that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] listens on.</span></span> <span data-ttu-id="e7d52-146">对于默认实例，此端口通常为用于 TCP/IP 连接的 1433 端口。</span><span class="sxs-lookup"><span data-stu-id="e7d52-146">For the default instance, this is typically port 1433 for TCP/IP connections.</span></span> <span data-ttu-id="e7d52-147">有关详细信息，请参阅 [联机丛书中的](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) 为数据库引擎访问配置 Windows 防火墙 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e7d52-147">For more information, see [Configure a Windows Firewall for Database Engine Access](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
### <a name="to-create-a-local-report-server-database"></a><span data-ttu-id="e7d52-148">创建本地报表服务器数据库</span><span class="sxs-lookup"><span data-stu-id="e7d52-148">To create a local report server database</span></span>  
  
1.  <span data-ttu-id="e7d52-149">启动 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器并连接到要为其创建数据库的报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="e7d52-149">Start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager and connect to the report server instance for which you are creating the database.</span></span> <span data-ttu-id="e7d52-150">有关详细信息，请参阅 [Reporting Services Configuration Manager（本机模式）](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="e7d52-150">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="e7d52-151">在“数据库”页上，单击 **“更改数据库”**。</span><span class="sxs-lookup"><span data-stu-id="e7d52-151">On the Database page, click **Change Database**.</span></span>  
  
3.  <span data-ttu-id="e7d52-152">单击 **“创建新的报表服务器数据库”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="e7d52-152">Click **Create a new report server database**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="e7d52-153">连接到您将用于创建和承载报表服务器数据库的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例：</span><span class="sxs-lookup"><span data-stu-id="e7d52-153">Connect to the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that you will use to create and host the report server database:</span></span>  
  
    1.  <span data-ttu-id="e7d52-154">键入要使用的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="e7d52-154">Type the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] instance that you want to use.</span></span> <span data-ttu-id="e7d52-155">向导将显示作为默认实例（如果可用）运行的本地 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e7d52-155">The wizard will display a local [!INCLUDE[ssDE](../../includes/ssde-md.md)] that runs as the default instance if it is available.</span></span> <span data-ttu-id="e7d52-156">否则，您必须键入要使用的服务器和实例。</span><span class="sxs-lookup"><span data-stu-id="e7d52-156">Otherwise, you must type the server and instance to use.</span></span> <span data-ttu-id="e7d52-157">命名实例按以下格式指定： \<servername> \\<instancename \> 。</span><span class="sxs-lookup"><span data-stu-id="e7d52-157">Named instances are specified in this format: \<servername>\\<instancename\>.</span></span>  
  
    2.  <span data-ttu-id="e7d52-158">输入用于一次性连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的凭据以创建报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="e7d52-158">Enter the credentials used for a one-time connection to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] for the purpose of creating the report server databases.</span></span> <span data-ttu-id="e7d52-159">有关如何使用这些凭据的详细信息，请参阅本主题中的 [开始之前](#rsdbrequirements) 。</span><span class="sxs-lookup"><span data-stu-id="e7d52-159">For more information about how these credentials are used, see [Before You Start](#rsdbrequirements) in this topic.</span></span>  
  
    3.  <span data-ttu-id="e7d52-160">单击 **“测试连接”** 以验证与服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="e7d52-160">Click **Test Connection** to validate the connection to the server.</span></span>  
  
    4.  <span data-ttu-id="e7d52-161">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="e7d52-161">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="e7d52-162">指定用于创建数据库的属性。</span><span class="sxs-lookup"><span data-stu-id="e7d52-162">Specify properties used to create the database.</span></span> <span data-ttu-id="e7d52-163">有关如何使用这些属性的详细信息，请参阅本主题中的 [开始之前](#rsdbrequirements) ：</span><span class="sxs-lookup"><span data-stu-id="e7d52-163">For more information about how these properties are used, see [Before You Start](#rsdbrequirements) in this topic:</span></span>  
  
    1.  <span data-ttu-id="e7d52-164">键入报表服务器数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="e7d52-164">Type the name of the report server database.</span></span> <span data-ttu-id="e7d52-165">创建主数据库时，会同时为其创建一个临时数据库。</span><span class="sxs-lookup"><span data-stu-id="e7d52-165">A temporary database is created along with the primary database.</span></span> <span data-ttu-id="e7d52-166">请考虑使用一个说明性名称来帮助记忆数据库的使用方式。</span><span class="sxs-lookup"><span data-stu-id="e7d52-166">Consider using a descriptive name to help you remember how the database is used.</span></span> <span data-ttu-id="e7d52-167">请注意，您指定的名称将在数据库的生存期内使用。</span><span class="sxs-lookup"><span data-stu-id="e7d52-167">Note that the name you specify will be used for the lifetime of the database.</span></span> <span data-ttu-id="e7d52-168">在创建报表服务器数据库之后，不能对其进行重命名。</span><span class="sxs-lookup"><span data-stu-id="e7d52-168">You cannot rename a report server database after it is created.</span></span>  
  
    2.  <span data-ttu-id="e7d52-169">选择要显示角色定义和“我的报表”所用的语言。</span><span class="sxs-lookup"><span data-stu-id="e7d52-169">Select the language in which you want role definitions and My Reports to appear.</span></span>  
  
    3.  <span data-ttu-id="e7d52-170">报表服务器模式始终设置为 **“本机”**。</span><span class="sxs-lookup"><span data-stu-id="e7d52-170">The Report Server Mode is always set to **Native**.</span></span>  
  
    4.  <span data-ttu-id="e7d52-171">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="e7d52-171">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="e7d52-172">指定报表服务器用来连接到报表服务器数据库的凭据。</span><span class="sxs-lookup"><span data-stu-id="e7d52-172">Specify the credentials used by the report server to connect to the report server database.</span></span>  
  
    1.  <span data-ttu-id="e7d52-173">指定身份验证类型：</span><span class="sxs-lookup"><span data-stu-id="e7d52-173">Specify the authentication type:</span></span>  
  
         <span data-ttu-id="e7d52-174">选择 **“数据库凭据”** 以使用已定义的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库登录名进行连接。</span><span class="sxs-lookup"><span data-stu-id="e7d52-174">Select **Database Credentials** to connect using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database login that is already defined.</span></span> <span data-ttu-id="e7d52-175">如果报表服务器位于不同域、不可信域或装有防火墙的计算机中，则建议使用数据库凭据。</span><span class="sxs-lookup"><span data-stu-id="e7d52-175">Using database credentials is recommended if the report server is on a computer that is in a different domain, a non-trusted domain, or behind a firewall.</span></span>  
  
         <span data-ttu-id="e7d52-176">如果你拥有的最低特权域用户帐户具有登录到该计算机和数据库服务器的权限，请选择“Windows 凭据”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e7d52-176">Select **Windows Credentials** if you have a least-privileged domain user account that has permission to log on to the computer and the database server.</span></span>  
  
         <span data-ttu-id="e7d52-177">如果希望报表服务器使用其自身的服务帐户进行连接，则选择 **“服务凭据”** 。</span><span class="sxs-lookup"><span data-stu-id="e7d52-177">Select **Service Credentials** if you want the report server to connect using its service account.</span></span> <span data-ttu-id="e7d52-178">使用此选项，该服务器将使用集成安全性进行连接；凭据不进行加密或存储。</span><span class="sxs-lookup"><span data-stu-id="e7d52-178">With this option, the server connects using integrated security; credentials are not encrypted or stored.</span></span>  
  
    2.  <span data-ttu-id="e7d52-179">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="e7d52-179">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="e7d52-180">检查“摘要”页上的信息以确保设置正确，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="e7d52-180">Review the information on the Summary page to verify the settings are correct, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="e7d52-181">单击“报表服务器 URL”页或“报表管理器 URL”页上的 URL，验证连接。</span><span class="sxs-lookup"><span data-stu-id="e7d52-181">Verify the connection by clicking a URL on the Report Server URL page or Report Manager URL page.</span></span> <span data-ttu-id="e7d52-182">必须定义这些 URL 才能进行此测试。</span><span class="sxs-lookup"><span data-stu-id="e7d52-182">The URLs must be defined in order for this test to work.</span></span> <span data-ttu-id="e7d52-183">如果报表服务器数据库连接有效，您会在浏览器窗口中看到报表服务器文件夹层次结构或报表管理器。</span><span class="sxs-lookup"><span data-stu-id="e7d52-183">If the report server database connection is valid, you will see either the report server folder hierarchy or Report Manager in a browser window.</span></span> <span data-ttu-id="e7d52-184">有关详细信息，请参阅 [联机丛书中的](verify-a-reporting-services-installation.md) 验证 Reporting Services 安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e7d52-184">For more information, see [Verify a Reporting Services Installation](verify-a-reporting-services-installation.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7d52-185">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7d52-185">See Also</span></span>  
 <span data-ttu-id="e7d52-186">[&#40;SSRS Configuration Manager 配置报表服务器数据库连接&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="e7d52-186">[Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="e7d52-187">[数据库 &#40;SSRS 本机模式&#41;](../../sql-server/install/database-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="e7d52-187">[Database &#40;SSRS Native Mode&#41;](../../sql-server/install/database-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="e7d52-188">[管理 Reporting Services 本机模式报表服务器](../report-server/manage-a-reporting-services-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="e7d52-188">[Manage a Reporting Services Native Mode Report Server](../report-server/manage-a-reporting-services-native-mode-report-server.md) </span></span>  
 [<span data-ttu-id="e7d52-189">Reporting Services Configuration Manager（本机模式）</span><span class="sxs-lookup"><span data-stu-id="e7d52-189">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
