---
title: 配置报表服务器服务帐户（SSRS 配置管理器）| Microsoft Docs
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: ''
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/10/2018
ms.openlocfilehash: b860a9c916f7dd9c1bdef4f5218845c66239ebe2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687520"
---
# <a name="configure-the-report-server-service-account-ssrs-configuration-manager"></a><span data-ttu-id="a7935-102">配置报表服务器服务帐户（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="a7935-102">Configure the Report Server Service Account (SSRS Configuration Manager)</span></span>

  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="a7935-103">是作为单个服务实现的，其中包含报表服务器 Web 服务、报表管理器以及用于计划的报告处理和订阅传递的后台处理应用程序。</span><span class="sxs-lookup"><span data-stu-id="a7935-103">is implemented as a single service that contains a Report Server Web service, Report Manager, and a background processing application that is used for scheduled report processing and subscription delivery.</span></span> <span data-ttu-id="a7935-104">本主题说明最初如何配置服务帐户以及如何使用 Reporting Services 配置工具修改帐户或密码。</span><span class="sxs-lookup"><span data-stu-id="a7935-104">This topic explains how the service account is initially configured and how to modify the account or password using the Reporting Services Configuration tool.</span></span>  
  
## <a name="initial-configuration"></a><span data-ttu-id="a7935-105">初始配置</span><span class="sxs-lookup"><span data-stu-id="a7935-105">Initial Configuration</span></span>

 <span data-ttu-id="a7935-106">报表服务器服务帐户是在安装过程中定义的。</span><span class="sxs-lookup"><span data-stu-id="a7935-106">The Report Server service account is defined during Setup.</span></span> <span data-ttu-id="a7935-107">可以在域用户帐户或内置帐户（如 `NetworkService` 帐户）下运行服务。</span><span class="sxs-lookup"><span data-stu-id="a7935-107">You can run the service under a domain user account or a built-in such as `NetworkService` account.</span></span> <span data-ttu-id="a7935-108">没有默认帐户;安装向导的 "[服务器配置-服务帐户](../../sql-server/install/server-configuration-service-accounts.md)" 页中指定的任何帐户都将成为报表服务器服务的初始帐户。</span><span class="sxs-lookup"><span data-stu-id="a7935-108">There is no default account; whatever account you specify in the [Server Configuration - Service Accounts](../../sql-server/install/server-configuration-service-accounts.md) page of the Installation Wizard becomes the initial account of the Report Server service.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a7935-109">尽管报表服务器 Web 服务和报表管理器均为 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 应用程序，但它们不在 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 帐户下运行。</span><span class="sxs-lookup"><span data-stu-id="a7935-109">Although the Report Server Web service and Report Manager are [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] applications, they do not run under the [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] account.</span></span> <span data-ttu-id="a7935-110">由单个服务体系结构在同一个报表服务器进程标识下运行这两个 ASP.NET 应用程序。</span><span class="sxs-lookup"><span data-stu-id="a7935-110">The single service architecture runs both ASP.NET applications within the same Report Server process identity.</span></span> <span data-ttu-id="a7935-111">与先前版本相比，这是一个重大的更改，在先前版本中，报表服务器 Web 服务和报表管理器均在 IIS 中指定的 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 辅助进程标识下运行。</span><span class="sxs-lookup"><span data-stu-id="a7935-111">This is an important change from previous releases, where both the Report Server Web service and Report Manager ran under the [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] worker process identity specified in IIS.</span></span>
  
## <a name="changing-the-service-account"></a><span data-ttu-id="a7935-112">更改服务帐户</span><span class="sxs-lookup"><span data-stu-id="a7935-112">Changing the Service Account</span></span>

 <span data-ttu-id="a7935-113">若要查看和重新配置服务帐户信息，请始终使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置工具。</span><span class="sxs-lookup"><span data-stu-id="a7935-113">To view and reconfigure service account information, always use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool.</span></span> <span data-ttu-id="a7935-114">服务标识信息在内部存储在多个位置上。</span><span class="sxs-lookup"><span data-stu-id="a7935-114">Service identity information is stored internally in multiple locations.</span></span> <span data-ttu-id="a7935-115">使用该工具可确保在更改帐户或密码的同时相应地更新所有引用。</span><span class="sxs-lookup"><span data-stu-id="a7935-115">Using the tool ensures that all references are updated accordingly whenever you change the account or password.</span></span> <span data-ttu-id="a7935-116">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置工具将执行以下附加步骤以确保报表服务器仍然可用：</span><span class="sxs-lookup"><span data-stu-id="a7935-116">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool performs the following additional steps to ensure the report server remains available:</span></span>  
  
- <span data-ttu-id="a7935-117">自动将新帐户添加到本地计算机上创建的报表服务器组中。</span><span class="sxs-lookup"><span data-stu-id="a7935-117">Automatically adds the new account to the report server group created on the local computer.</span></span> <span data-ttu-id="a7935-118">此组是在用于保护 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 文件的访问控制列表 (ACL) 中指定的。</span><span class="sxs-lookup"><span data-stu-id="a7935-118">This group is specified in the access control lists (ACLs) that secure [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] files.</span></span>  
  
- <span data-ttu-id="a7935-119">自动更新用于托管报表服务器数据库的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例的登录权限。</span><span class="sxs-lookup"><span data-stu-id="a7935-119">Automatically updates the login permissions on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance used to host the report server database.</span></span> <span data-ttu-id="a7935-120">新帐户将添加到 **RSExecRole**。</span><span class="sxs-lookup"><span data-stu-id="a7935-120">The new account will be added to the **RSExecRole**.</span></span>  
  
     <span data-ttu-id="a7935-121">旧帐户的数据库登录名不会被自动删除。</span><span class="sxs-lookup"><span data-stu-id="a7935-121">The database login for the old account will not be removed automatically.</span></span> <span data-ttu-id="a7935-122">请务必删除不再使用的帐户。</span><span class="sxs-lookup"><span data-stu-id="a7935-122">Be sure to remove accounts that are no longer in use.</span></span> <span data-ttu-id="a7935-123">有关详细信息，请参阅 SQL Server 联机丛书中的[管理报表服务器数据库（SSRS 本机模式）](../report-server/report-server-database-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="a7935-123">For more information, see [Administer a Report Server Database &#40;SSRS Native Mode&#41;](../report-server/report-server-database-ssrs-native-mode.md) in SQL Server Books Online.</span></span>  
  
     <span data-ttu-id="a7935-124">只有在首先将报表服务器数据库连接配置为使用新服务帐户的情况下，才需要将数据库权限授予该服务帐户。</span><span class="sxs-lookup"><span data-stu-id="a7935-124">Granting database permissions to new service account only occurs if you configured the report server database connection to use the service account in the first place.</span></span> <span data-ttu-id="a7935-125">如果将报表服务器数据库连接配置为使用域用户帐户或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库登录名，连接信息将不受服务帐户更新的影响。</span><span class="sxs-lookup"><span data-stu-id="a7935-125">If you configured the report server database connection to use a domain user account or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database login, the connection information is not affected by the service account update.</span></span>  
  
- <span data-ttu-id="a7935-126">自动更新加密密钥，以包括新帐户的配置文件信息。</span><span class="sxs-lookup"><span data-stu-id="a7935-126">Automatically updates the encryption key to include the profile information of the new account.</span></span>  
  
    > [!NOTE]  
    > <span data-ttu-id="a7935-127">如果报表服务器是扩展部署的一部分，则只有正在更新的报表服务器会受到影响。</span><span class="sxs-lookup"><span data-stu-id="a7935-127">If the report server is part of the scale-out deployment, only the report server that you are updating is affected.</span></span> <span data-ttu-id="a7935-128">该部署中的其他报表服务器的加密密钥不会受到服务帐户更改的影响。</span><span class="sxs-lookup"><span data-stu-id="a7935-128">The encryption keys for other report servers in the deployment are unaffected by the service account change.</span></span>  
  
 <span data-ttu-id="a7935-129">有关如何设置帐户的说明，请参阅[&#40;SSRS Configuration Manager&#41;中配置服务帐户](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="a7935-129">For instructions on how to set the account, see [Configure a Service Account &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md).</span></span>  
  
## <a name="choosing-an-account"></a><span data-ttu-id="a7935-130">选择帐户</span><span class="sxs-lookup"><span data-stu-id="a7935-130">Choosing an Account</span></span>

 <span data-ttu-id="a7935-131">可以将报表服务器服务配置为在以下任何帐户类型下运行：</span><span class="sxs-lookup"><span data-stu-id="a7935-131">You can configure the Report Server service to run under any of these account types:</span></span>  
  
- <span data-ttu-id="a7935-132">具有最小权限的 Windows 用户帐户</span><span class="sxs-lookup"><span data-stu-id="a7935-132">Least-privileged Windows user account</span></span>  
  
- <span data-ttu-id="a7935-133">NetworkService</span><span class="sxs-lookup"><span data-stu-id="a7935-133">NetworkService</span></span>  
  
- <span data-ttu-id="a7935-134">LocalSystem</span><span class="sxs-lookup"><span data-stu-id="a7935-134">LocalSystem</span></span>  
  
- <span data-ttu-id="a7935-135">LocalService</span><span class="sxs-lookup"><span data-stu-id="a7935-135">LocalService</span></span>  
  
 <span data-ttu-id="a7935-136">没有用来选择帐户类型的唯一最佳方法。</span><span class="sxs-lookup"><span data-stu-id="a7935-136">There is no single best approach for choosing an account type.</span></span> <span data-ttu-id="a7935-137">每个帐户都有优点和缺点，选择时必须予以考虑。</span><span class="sxs-lookup"><span data-stu-id="a7935-137">Each account has advantages and disadvantages that you must consider.</span></span> <span data-ttu-id="a7935-138">如果在生产服务器上部署 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，则最好将服务配置为在域用户帐户下运行，以避免共享帐户遭恶意用户破坏后造成大范围的损害。</span><span class="sxs-lookup"><span data-stu-id="a7935-138">If you are deploying [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] on a production server, best practices suggest that you configure the service to run under a domain user account so that you can avoid widespread damage if a shared account is compromised by a malicious user.</span></span> <span data-ttu-id="a7935-139">这样做还能更轻松地审核该帐户的登录活动。</span><span class="sxs-lookup"><span data-stu-id="a7935-139">It also makes it easier to audit the logon activity for this account.</span></span> <span data-ttu-id="a7935-140">使用 Windows 用户帐户的折中方案为：如果在使用 Kerberos 身份验证的网络中部署 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]，则必须用该用户帐户来注册服务。</span><span class="sxs-lookup"><span data-stu-id="a7935-140">A trade-off to using a Windows user account is that if you are deploying [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in a network that uses Kerberos authentication, you must register the service with the user account.</span></span> <span data-ttu-id="a7935-141">有关详细信息，请参阅[为报表服务器注册服务主体名称 (SPN)](../report-server/register-a-service-principal-name-spn-for-a-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a7935-141">For more information, see [Register a Service Principal Name &#40;SPN&#41; for a Report Server](../report-server/register-a-service-principal-name-spn-for-a-report-server.md).</span></span>  
  
 <span data-ttu-id="a7935-142">本部分中的下列指南和链接可以帮助您确定部署的最佳方法。</span><span class="sxs-lookup"><span data-stu-id="a7935-142">The following guidelines and links in this section can help you decide on an approach that is best for your deployment.</span></span>  
  
- <span data-ttu-id="a7935-143">[服务帐户 &#40;SSRS 本机模式&#41;](../../sql-server/install/service-account-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="a7935-143">[Service Account &#40;SSRS Native Mode&#41;](../../sql-server/install/service-account-ssrs-native-mode.md).</span></span>  
  
- <span data-ttu-id="a7935-144">SQL Server 联机丛书中的[配置 Windows 服务帐户和权限](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) 。</span><span class="sxs-lookup"><span data-stu-id="a7935-144">[Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) in SQL Server Books Online.</span></span>  
  
- <span data-ttu-id="a7935-145">[服务和服务帐户安全计划指南](http://usergroup.doubletake.com/file_cabinet/download/0x000021733)。</span><span class="sxs-lookup"><span data-stu-id="a7935-145">[The Services and Service Accounts Security Planning Guide](http://usergroup.doubletake.com/file_cabinet/download/0x000021733).</span></span>  
  
## <a name="updating-an-expired-password"></a><span data-ttu-id="a7935-146">更新过期密码</span><span class="sxs-lookup"><span data-stu-id="a7935-146">Updating an Expired Password</span></span>

 <span data-ttu-id="a7935-147">如果报表服务器服务在域帐户下运行，并且密码还未在 Reporting Services 配置工具中更新就已过期，则指定新密码之前，该服务将无法启动。</span><span class="sxs-lookup"><span data-stu-id="a7935-147">If the Report Server service runs under a domain account and the password expires before you can update it in the Reporting Services Configuration tool, the service will not start until you specify a new password.</span></span> <span data-ttu-id="a7935-148">如果服务无法启动，则不能使用 Reporting Services 配置工具连接到该服务器以更新帐户。</span><span class="sxs-lookup"><span data-stu-id="a7935-148">If the service cannot be started, you cannot use the Reporting Services Configuration tool to connect to that server to update the account.</span></span> <span data-ttu-id="a7935-149">在这种情况下，必须使用多种工具来使服务器恢复联机状态。</span><span class="sxs-lookup"><span data-stu-id="a7935-149">In this case, you must use a combination of tools to bring the server back online.</span></span>  
  
 <span data-ttu-id="a7935-150">若要重置密码，请执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="a7935-150">To reset the password, do the following:</span></span>  
  
1. <span data-ttu-id="a7935-151">在 "**开始**" 菜单上，指向 **"控制面板**"，指向 "**管理员工具**"，然后单击 "**服务**"。</span><span class="sxs-lookup"><span data-stu-id="a7935-151">On the **Start** menu, point to **Control Panel**, point to **Administrator Tools**, and click **Services**.</span></span>  
  
2. <span data-ttu-id="a7935-152">右键单击**SQL Server Reporting Services**，选择 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="a7935-152">Right-click **SQL Server Reporting Services**, select **Properties**.</span></span>  
  
3. <span data-ttu-id="a7935-153">单击 "**登录**"，然后键入新密码。</span><span class="sxs-lookup"><span data-stu-id="a7935-153">Click **Log On**, and type the new password.</span></span>  
  
4. <span data-ttu-id="a7935-154">更新密码后，启动 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置工具并在“服务帐户”页中更新密码。</span><span class="sxs-lookup"><span data-stu-id="a7935-154">After you update the password, start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and update the password in the Service Account page.</span></span> <span data-ttu-id="a7935-155">若要更新由报表服务器存储在内部的帐户信息，必须执行此附加步骤。</span><span class="sxs-lookup"><span data-stu-id="a7935-155">This additional step is necessary to update the account information that is stored internally by the report server.</span></span>  
  
 <span data-ttu-id="a7935-156">如果[!INCLUDE[ssDE](../../includes/ssde-md.md)]的服务帐户密码已过期，则尝试连接到报表服务器时，将出现 `rsReportServerDatabaseUnavailable` 错误。</span><span class="sxs-lookup"><span data-stu-id="a7935-156">If the service account password for the [!INCLUDE[ssDE](../../includes/ssde-md.md)] expires, the `rsReportServerDatabaseUnavailable` error occurs when you try to connect to the report server.</span></span> <span data-ttu-id="a7935-157">重置密码可以解决此错误。</span><span class="sxs-lookup"><span data-stu-id="a7935-157">Resetting the password resolves this error.</span></span>  
  
## <a name="configuring-the-report-server-service-for-a-sharepoint-integrated-report-server"></a><span data-ttu-id="a7935-158">为 SharePoint 集成报表服务器配置报表服务器服务</span><span class="sxs-lookup"><span data-stu-id="a7935-158">Configuring the Report Server Service for a SharePoint Integrated Report Server</span></span>

 <span data-ttu-id="a7935-159">如果在 SharePoint 集成模式下运行报表服务器，且符合下列条件之一，则必须更新存储在 SharePoint 配置数据库中的服务帐户信息。</span><span class="sxs-lookup"><span data-stu-id="a7935-159">If you are running a report server in SharePoint integrated mode, you must update the service account information that is stored in the SharePoint configuration database if either of the following conditions are true:</span></span>  
  
- <span data-ttu-id="a7935-160">修改 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务帐户（例如，从 NetworkService 帐户切换到域用户帐户）。</span><span class="sxs-lookup"><span data-stu-id="a7935-160">Modifying the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service account (for example, switching from NetworkService to a domain user account).</span></span>  
  
- <span data-ttu-id="a7935-161">扩展 SharePoint 场以包含其他 SharePoint Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="a7935-161">Extending a SharePoint farm to include an additional SharePoint Web application.</span></span> <span data-ttu-id="a7935-162">如果服务器场是针对报表服务器集成配置的，且配置的用于运行新添加的应用程序的用户帐户与用于运行该场中其他应用程序的用户帐户不同，则必须更新数据库访问信息。</span><span class="sxs-lookup"><span data-stu-id="a7935-162">If the server farm is configured for report server integration, and newly added application is configured to run under a different user account than other applications in the farm, you must update the database access information.</span></span>  
  
 <span data-ttu-id="a7935-163">重置数据库访问信息后，应当重新启动 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 服务以确保不再使用旧连接。</span><span class="sxs-lookup"><span data-stu-id="a7935-163">After you reset the database access information, you should then restart the [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] service to ensure that the old connection is no longer used.</span></span>  
  
1. <span data-ttu-id="a7935-164">在 "**管理工具**" 中，单击 " **SharePoint 2010 管理中心**"。</span><span class="sxs-lookup"><span data-stu-id="a7935-164">In **Administrative Tools**, click **SharePoint 2010 Central Administration**.</span></span>  
  
2. <span data-ttu-id="a7935-165">单击 "**应用程序管理**"。</span><span class="sxs-lookup"><span data-stu-id="a7935-165">Click **Application Management**.</span></span>  
  
3. <span data-ttu-id="a7935-166">在 Reporting Services 部分中，单击 "**授予数据库访问权限**"。</span><span class="sxs-lookup"><span data-stu-id="a7935-166">In the Reporting Services section, click **Grant Database Access**.</span></span>  
  
4. <span data-ttu-id="a7935-167">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="a7935-167">Click **OK**.</span></span> <span data-ttu-id="a7935-168">将出现“输入凭据”对话框。</span><span class="sxs-lookup"><span data-stu-id="a7935-168">The Enter Credentials dialog box appears.</span></span>  
  
5. <span data-ttu-id="a7935-169">输入用户凭据，该用户必须是报表服务器所在的计算机上本地管理员组的成员。</span><span class="sxs-lookup"><span data-stu-id="a7935-169">Enter the credentials of a user who is a member of the Local Administrator's group on the computer that hosts the report server.</span></span> <span data-ttu-id="a7935-170">这些凭据将用于一次性连接到报表服务器计算机以便检索服务帐户信息。</span><span class="sxs-lookup"><span data-stu-id="a7935-170">The credentials will be used for a one-time connection to the report server computer for the purpose of retrieving service account information.</span></span> <span data-ttu-id="a7935-171">在 SharePoint 数据库中将对为每个服务帐户创建的数据库登录名进行更新。</span><span class="sxs-lookup"><span data-stu-id="a7935-171">The database login that is created for each service account will be updated in SharePoint databases.</span></span>  
  
6. <span data-ttu-id="a7935-172">若要重新启动该服务，请单击 "**操作**"。</span><span class="sxs-lookup"><span data-stu-id="a7935-172">To restart the service, click **Operations**.</span></span>  
  
7. <span data-ttu-id="a7935-173">在 "拓扑和服务" 中，单击 "**服务器上的服务**"。</span><span class="sxs-lookup"><span data-stu-id="a7935-173">In Topology and Services, click **Services on Server**.</span></span>  
  
8. <span data-ttu-id="a7935-174">对于 Windows SharePoint Services Web 应用程序，单击 "**停止**"。</span><span class="sxs-lookup"><span data-stu-id="a7935-174">For Windows SharePoint Services Web Application, click **Stop**.</span></span>  
  
9. <span data-ttu-id="a7935-175">等待服务停止。</span><span class="sxs-lookup"><span data-stu-id="a7935-175">Wait for the service stop.</span></span>  
  
10. <span data-ttu-id="a7935-176">单击“启动”。</span><span class="sxs-lookup"><span data-stu-id="a7935-176">Click **Start**.</span></span>  
  
> [!NOTE]  
> <span data-ttu-id="a7935-177">SharePoint 产品和技术需要域帐户来完成服务配置，如报表服务 SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="a7935-177">SharePoint products and technologies require domain accounts for service configuration like reporting services SharePoint mode.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a7935-178">后续步骤</span><span class="sxs-lookup"><span data-stu-id="a7935-178">Next Steps</span></span>

 <span data-ttu-id="a7935-179">[将服务帐户配置 &#40;ssrs Configuration Manager&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md) [服务帐户 &#40;ssrs 本机模式&#41;](../../sql-server/install/service-account-ssrs-native-mode.md) [将报表服务器 url &#40;Ssrs](configure-report-server-urls-ssrs-configuration-manager.md) Configuration Manager&#41;Reporting Services 配置管理器 &#40;[纯模式](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="a7935-179">[Configure a Service Account &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md) [Service Account &#40;SSRS Native Mode&#41;](../../sql-server/install/service-account-ssrs-native-mode.md) [Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](configure-report-server-urls-ssrs-configuration-manager.md) [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)</span></span>
