---
title: " (SSIS 服务连接到远程 Integration Services 服务器) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- service [Integration Services], remote instance
- Integration Services service, connecting
- Integration Services service, remote instance
- service [Integration Services], connecting
ms.assetid: 9487aff1-44d8-42c1-8176-bb9891d4632d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 03c9c4f1c94e4599c2c14f407996431dabd493dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692478"
---
# <a name="connect-to-a-remote-integration-services-server-ssis-service"></a><span data-ttu-id="06434-102">连接到远程 Integration Services 服务器（SSIS 服务）</span><span class="sxs-lookup"><span data-stu-id="06434-102">Connect to a Remote Integration Services Server (SSIS Service)</span></span>
    
> [!IMPORTANT] 
> <span data-ttu-id="06434-103">本主题论述 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务，该服务是用于管理 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包的一种 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="06434-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="06434-104">支持该服务以便与 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]的早期版本向后兼容。</span><span class="sxs-lookup"><span data-stu-id="06434-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="06434-105">从 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]开始，您可以在 Integration Services 服务器上管理诸如包之类的对象。</span><span class="sxs-lookup"><span data-stu-id="06434-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 <span data-ttu-id="06434-106">若要从 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 或其他管理应用程序连接到远程服务器上的 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 实例，应用程序的用户需要拥有服务器上的一组特定权限。</span><span class="sxs-lookup"><span data-stu-id="06434-106">Connecting to an instance of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] on a remote server, from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or another management application, requires a specific set of rights on the server for the users of the application.</span></span>  
  
> [!IMPORTANT] 
> <span data-ttu-id="06434-107">若要管理存储在某远程服务器上的包，您不必连接到该远程服务器上 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务的实例。</span><span class="sxs-lookup"><span data-stu-id="06434-107">To manage packages that are stored on a remote server, you do not have to connect to the instance of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service on that remote server.</span></span> <span data-ttu-id="06434-108">只需编辑 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务的配置文件，以便 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 显示存储在远程服务器上的包。</span><span class="sxs-lookup"><span data-stu-id="06434-108">Instead, edit the configuration file for the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service so that [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] displays the packages that are stored on the remote server.</span></span> <span data-ttu-id="06434-109">有关详细信息，请参阅 [配置 Integration Services 服务（SSIS 服务）](service/integration-services-service-ssis-service.md)的早期版本向后兼容。</span><span class="sxs-lookup"><span data-stu-id="06434-109">For more information, see [Configuring the Integration Services Service &#40;SSIS Service&#41;](service/integration-services-service-ssis-service.md).</span></span>  
  
## <a name="connecting-to-integration-services-on-a-remote-server"></a><span data-ttu-id="06434-110">连接到远程服务器上的 Integration Services</span><span class="sxs-lookup"><span data-stu-id="06434-110">Connecting to Integration Services on a Remote Server</span></span>  
  
#### <a name="to-connect-to-integration-services-on-a-remote-server"></a><span data-ttu-id="06434-111">连接到远程服务器上的 Integration Services</span><span class="sxs-lookup"><span data-stu-id="06434-111">To connect to Integration Services on a Remote Server</span></span>  
  
1.  <span data-ttu-id="06434-112">打开 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="06434-112">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="06434-113">选择 **“文件”** 菜单上的 **“连接对象资源管理器”** 以显示 **“连接到服务器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="06434-113">Select **File**, **Connect Object Explorer** to display the **Connect to Server** dialog box.</span></span>  
  
3.  <span data-ttu-id="06434-114">在 **“服务器类型”** 列表中选择 **Integration Services** 。</span><span class="sxs-lookup"><span data-stu-id="06434-114">Select **Integration Services** in the **Server type** list.</span></span>  
  
4.  <span data-ttu-id="06434-115">在“服务器名称”文本框中键入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务器的名称\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="06434-115">Type the name of a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server in the **Server name** text box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="06434-116">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务是不特定于实例的。</span><span class="sxs-lookup"><span data-stu-id="06434-116">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is not instance-specific.</span></span> <span data-ttu-id="06434-117">通过使用正运行 Integration Services 服务的计算机的名称连接到该服务。</span><span class="sxs-lookup"><span data-stu-id="06434-117">You connect to the service by using the name of the computer on which the Integration Services service is running.</span></span>  
  
5.  <span data-ttu-id="06434-118">单击“连接” 。</span><span class="sxs-lookup"><span data-stu-id="06434-118">Click **Connect**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="06434-119">**“查找服务器”** 对话框中不显示 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]的远程实例。</span><span class="sxs-lookup"><span data-stu-id="06434-119">The **Browse for Servers** dialog box does not display remote instances of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="06434-120">此外， **“连接到服务器”** 对话框中的 **“连接选项”** 选项卡上的选项不适用于 **连接（该选项卡在单击** “选项” [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 按钮后显示）。</span><span class="sxs-lookup"><span data-stu-id="06434-120">In addition, the options available on the **Connection Options** tab of the **Connect to Server** dialog box, which is displayed by clicking the **Options** button, are not applicable to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] connections.</span></span>  
  
## <a name="eliminating-the-access-is-denied-error"></a><span data-ttu-id="06434-121">消除“拒绝访问”错误</span><span class="sxs-lookup"><span data-stu-id="06434-121">Eliminating the "Access Is Denied" Error</span></span>  
 <span data-ttu-id="06434-122">当没有足够权限的用户尝试连接到远程服务器上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 实例时，服务器将以“拒绝访问”错误消息进行响应。</span><span class="sxs-lookup"><span data-stu-id="06434-122">When a user without sufficient rights attempts to connect to an instance of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] on a remote server, the server responds with an "Access is denied" error message.</span></span> <span data-ttu-id="06434-123">确保用户具有所需的 DCOM 权限可避免出现此错误消息。</span><span class="sxs-lookup"><span data-stu-id="06434-123">You can avoid this error message by ensuring that users have the required DCOM permissions.</span></span>  
  
#### <a name="to-configure-rights-for-remote-users-on-windows-server-2003-or-windows-xp"></a><span data-ttu-id="06434-124">在 Windows Server 2003 或 Windows XP 上配置远程用户的权限</span><span class="sxs-lookup"><span data-stu-id="06434-124">To configure rights for remote users on Windows Server 2003 or Windows XP</span></span>  
  
1.  <span data-ttu-id="06434-125">如果用户不是本地 Administrators 组的成员，请将用户添加至 Distributed COM Users 组。</span><span class="sxs-lookup"><span data-stu-id="06434-125">If the user is not a member of the local Administrators group, add the user to the Distributed COM Users group.</span></span> <span data-ttu-id="06434-126">可以从“管理工具”\*\*\*\* 菜单访问“计算机管理”MMC 管理单元完成此操作。</span><span class="sxs-lookup"><span data-stu-id="06434-126">You can do this in the Computer Management MMC snap-in accessed from the **Administrative Tools** menu.</span></span>  
  
2.  <span data-ttu-id="06434-127">打开“控制面板”，双击“管理工具”\*\*\*\*，然后双击“组件服务”\*\*\*\* 以启动组件服务 MMC 管理单元。</span><span class="sxs-lookup"><span data-stu-id="06434-127">Open Control Panel, double-click **Administrative Tools,** and then double-click **Component Services** to start the Component Services MMC snap-in.</span></span>  
  
3.  <span data-ttu-id="06434-128">展开控制台左侧窗格中的 **“组件服务”** 节点。</span><span class="sxs-lookup"><span data-stu-id="06434-128">Expand the **Component Services** node in the left pane of the console.</span></span> <span data-ttu-id="06434-129">展开 **“计算机”** 节点，展开 **“我的电脑”**，然后单击 **“DCOM 配置”** 节点。</span><span class="sxs-lookup"><span data-stu-id="06434-129">Expand the **Computers** node, expand **My Computer**, and then click the **DCOM Config** node.</span></span>  
  
4.  <span data-ttu-id="06434-130">选中 **“DCOM 配置”** 节点，然后在可以配置的应用程序列表中选择“SQL Server Integration Services 11.0”。</span><span class="sxs-lookup"><span data-stu-id="06434-130">Select the **DCOM Config** node, and then select SQL Server Integration Services 11.0 in the list of applications that can be configured.</span></span>  
  
5.  <span data-ttu-id="06434-131">右键单击 SQL Server Integration Services 11.0，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="06434-131">Right-click on SQL Server Integration Services 11.0 and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="06434-132">在 **“SQL Server Integration Services 11.0 属性”** 对话框中，选择 **“安全性”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="06434-132">In the **SQL Server Integration Services 11.0 Properties** dialog box, select the **Security** tab.</span></span>  
  
7.  <span data-ttu-id="06434-133">在 **“启动和激活权限”** 下，选择 **“自定义”**，然后单击 **“编辑”** 以打开 **“启动权限”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="06434-133">Under **Launch and Activation Permissions**, select **Customize**, then click **Edit** to open the **Launch Permission** dialog box.</span></span>  
  
8.  <span data-ttu-id="06434-134">在 **“启动权限”** 对话框中，添加或删除用户，并为适当的用户和组分配相应的权限。</span><span class="sxs-lookup"><span data-stu-id="06434-134">In the **Launch Permission** dialog box, add or delete users, and assign the appropriate permissions to the appropriate users and groups.</span></span> <span data-ttu-id="06434-135">可用的权限为“本地启动”、“远程启动”、“本地激活”和“远程激活”。</span><span class="sxs-lookup"><span data-stu-id="06434-135">The available permissions are Local Launch, Remote Launch, Local Activation, and Remote Activation.</span></span> <span data-ttu-id="06434-136">启动权限可授予或拒绝启动和停止服务的权限；激活权限可授予或拒绝连接到服务的权限。</span><span class="sxs-lookup"><span data-stu-id="06434-136">The Launch rights grant or deny permission to start and stop the service; the Activation rights grant or deny permission to connect to the service.</span></span>  
  
9. <span data-ttu-id="06434-137">单击“确定”关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="06434-137">Click OK to close the dialog box.</span></span>  
  
10. <span data-ttu-id="06434-138">在 **“访问权限”** 下，重复步骤 7 和步骤 8 以为适当的用户和组分配适当的权限。</span><span class="sxs-lookup"><span data-stu-id="06434-138">Under **Access Permissions**, repeat steps 7 and 8 to assign the appropriate permissions to the appropriate users and groups.</span></span>  
  
11. <span data-ttu-id="06434-139">关闭 MMC 管理单元。</span><span class="sxs-lookup"><span data-stu-id="06434-139">Close the MMC snap-in.</span></span>  
  
12. <span data-ttu-id="06434-140">重新启动 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="06434-140">Restart the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span>  
  
#### <a name="to-configure-rights-for-remote-users-on-windows-2000-with-the-latest-service-packs"></a><span data-ttu-id="06434-141">在带有最新 Service Pack 的 Windows 2000 上为远程用户配置权限</span><span class="sxs-lookup"><span data-stu-id="06434-141">To configure rights for remote users on Windows 2000 with the latest service packs</span></span>  
  
1.  <span data-ttu-id="06434-142">在命令提示符下运行 **dcomcnfg.exe** 。</span><span class="sxs-lookup"><span data-stu-id="06434-142">Run **dcomcnfg.exe** at the command prompt.</span></span>  
  
2.  <span data-ttu-id="06434-143">在 **“分布式 COM 配置属性”** 对话框的 **“应用程序”** 页上，选择“SQL Server Integration Services 11.0”，再单击 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="06434-143">On the **Applications** page of the **Distributed COM Configuration Properties** dialog box, select SQL Server Integration Services 11.0 and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="06434-144">选择 **“安全性”** 页。</span><span class="sxs-lookup"><span data-stu-id="06434-144">Select the **Security** page.</span></span>  
  
4.  <span data-ttu-id="06434-145">使用两个单独的对话框来分别配置 **“访问权限”** 和 **“启动权限”**。</span><span class="sxs-lookup"><span data-stu-id="06434-145">Use the two separate dialog boxes to configure **Access Permissions** and **Launch Permissions**.</span></span> <span data-ttu-id="06434-146">您无法区分远程访问和本地访问 - 访问权限包括了本地访问和远程访问，启动权限也包括了本地启动和远程启动。</span><span class="sxs-lookup"><span data-stu-id="06434-146">You cannot distinguish between remote and local access - Access permissions include local and remote access, and Launch permissions include local and remote launch.</span></span>  
  
5.  <span data-ttu-id="06434-147">关闭对话框和 **dcomcnfg.exe**。</span><span class="sxs-lookup"><span data-stu-id="06434-147">Close the dialog boxes and **dcomcnfg.exe**.</span></span>  
  
6.  <span data-ttu-id="06434-148">重新启动 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="06434-148">Restart the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span>  
  
## <a name="connecting-by-using-a-local-account"></a><span data-ttu-id="06434-149">使用本地帐户连接</span><span class="sxs-lookup"><span data-stu-id="06434-149">Connecting by using a Local Account</span></span>  
 <span data-ttu-id="06434-150">如果您是在客户端计算机上使用本地 Windows 帐户工作，则只有远程计算机上存在与客户端计算机上的本地帐户的帐户名和密码相同并且具有相应权限的本地帐户时，才可以连接到远程计算机上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="06434-150">If you are working in a local Windows account on a client computer, you can connect to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service on a remote computer only if a local account that has the same name and password and the appropriate rights exists on the remote computer.</span></span>  
  
## <a name="by-default-the-ssis-service-does-not-support-delegation"></a><span data-ttu-id="06434-151">默认情况下，SSIS 服务不支持委派</span><span class="sxs-lookup"><span data-stu-id="06434-151">By default the SSIS service does not support delegation</span></span>  
<span data-ttu-id="06434-152">默认情况下，该 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务不支持委托凭据，或有时称为双跃点。</span><span class="sxs-lookup"><span data-stu-id="06434-152">By default the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service does not support the delegation of credentials, or what is sometimes referred to as a double hop.</span></span> <span data-ttu-id="06434-153">在此方案中，你在客户端计算机上工作， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务在第二台计算机上运行和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 在第三台计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="06434-153">In this scenario, you are working on a client computer, the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is running on a second computer, and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is running on a third computer.</span></span> <span data-ttu-id="06434-154">首先， [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 成功地将你的凭据从客户端计算机传递到第二台计算机上， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务正在这台计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="06434-154">First, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] successfully passes your credentials from the client computer to the second computer on which the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is running.</span></span> <span data-ttu-id="06434-155">但是， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务不能将你的凭据从第二台计算机委派到正在运行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的第三台计算机上。</span><span class="sxs-lookup"><span data-stu-id="06434-155">Then, however, the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service cannot delegate your credentials from the second computer to the third computer on which [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is running.</span></span>

<span data-ttu-id="06434-156">可通过将“信任此用户对任何服务的委派(仅 Kerberos)”\*\*\*\* 的权限授予 SQL Server 服务帐户（它将 Integration Services 服务 (ISServerExec.exe) 作为子进程启动），从而启用凭据委派。</span><span class="sxs-lookup"><span data-stu-id="06434-156">You can enable delegation of credentials by granting the **Trust this user for delegation to any service (Kerberos Only)** right to the SQL Server service account, which launches the Integration Services service (ISServerExec.exe) as a child process.</span></span> <span data-ttu-id="06434-157">在授予此权限之前，请考虑它是否符合组织的安全要求。</span><span class="sxs-lookup"><span data-stu-id="06434-157">Before you grant this right, consider whether it meets the security requirements of your organization.</span></span>

<span data-ttu-id="06434-158">有关详细信息，请参阅 [Getting Cross Domain Kerberos and Delegation working with SSIS Package](https://blogs.msdn.microsoft.com/psssql/2014/06/26/getting-cross-domain-kerberos-and-delegation-working-with-ssis-package/)（获取跨域 Kerberos 和委派使用 SSIS 包）。</span><span class="sxs-lookup"><span data-stu-id="06434-158">For more info, see [Getting Cross Domain Kerberos and Delegation working with SSIS Package](https://blogs.msdn.microsoft.com/psssql/2014/06/26/getting-cross-domain-kerberos-and-delegation-working-with-ssis-package/).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="06434-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="06434-159">See Also</span></span>  
 [<span data-ttu-id="06434-160">为访问 SSIS 服务配置 Windows 防火墙</span><span class="sxs-lookup"><span data-stu-id="06434-160">Configure a Windows Firewall for Access to the SSIS Service</span></span>](../../2014/integration-services/configure-a-windows-firewall-for-access-to-the-ssis-service.md)  
  
  
