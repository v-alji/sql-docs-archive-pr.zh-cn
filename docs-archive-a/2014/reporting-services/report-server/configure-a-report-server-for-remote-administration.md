---
title: 配置报表服务器以进行远程管理 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services Configuration tool
- WMI provider [Reporting Services], remote configuration
- configuration management [WMI]
- report servers [Reporting Services], configuring
- remote server administration [Reporting Services]
ms.assetid: 8c7f145f-3ac2-4203-8cd6-2a4694395d09
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2c34db5299fc1b82a7896a41519e55466c3b3b79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588302"
---
# <a name="configure-a-report-server-for-remote-administration"></a><span data-ttu-id="9dc1e-102">配置报表服务器以进行远程管理</span><span class="sxs-lookup"><span data-stu-id="9dc1e-102">Configure a Report Server for Remote Administration</span></span>
  <span data-ttu-id="9dc1e-103">在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]中，您可以通过本地或远程方式配置报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-103">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can configure report server instances locally or remotely.</span></span> <span data-ttu-id="9dc1e-104">若要配置远程报表服务器实例，可以使用 Reporting Services 配置工具或编写使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Windows Management Instrumentation (WMI) 提供程序的自定义代码。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-104">To configure a remote report server instance, you can use the Reporting Services Configuration tool or write custom code that uses the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Windows Management Instrumentation (WMI) provider.</span></span> <span data-ttu-id="9dc1e-105">Reporting Services 配置工具为 WMI 提供程序提供了一个图形界面，这样您便可以直接配置报表服务器，而不必编写代码。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-105">The Reporting Services Configuration tool provides a graphical interface to the WMI provider so that you can configure a report server without having to write code.</span></span> <span data-ttu-id="9dc1e-106">启动该工具时，可以指定要连接的远程服务器。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-106">When you start the tool, you can specify a remote server to connect to.</span></span>  
  
 <span data-ttu-id="9dc1e-107">在可以使用该工具配置远程报表服务器之前，必须按照本主题中的说明在 Windows 防火墙中启用端口、启用远程连接并启用远程 WMI 请求。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-107">Before you can use the tool to configure a remote report server, you must follow the instructions in this topic to enable ports in Windows Firewall, enable remote connections, and enable remote WMI requests.</span></span>  
  
 <span data-ttu-id="9dc1e-108">正确的配置可帮助您避免出现以下错误：</span><span class="sxs-lookup"><span data-stu-id="9dc1e-108">Proper configuration helps you avoid the following error:</span></span>  
  
 `The machine could not be found.`  
  
 `"The RPC server is unavailable. (Exception from HRESULT: 0x800706BA)".`  
  
## <a name="prerequisites"></a><span data-ttu-id="9dc1e-109">必备条件</span><span class="sxs-lookup"><span data-stu-id="9dc1e-109">Prerequisites</span></span>  
 <span data-ttu-id="9dc1e-110">若要修改防火墙设置，必须从本地登录，并且您必须是本地 Administrators 组的成员。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-110">To modify firewall settings, you must be logged on locally and you must be a member of the local Administrators group.</span></span> <span data-ttu-id="9dc1e-111">不能通过远程连接来修改远程计算机的 Windows 防火墙设置。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-111">You cannot modify the Windows firewall settings of a remote computer over a remote connection.</span></span>  
  
 <span data-ttu-id="9dc1e-112">如果要为非管理员用户启用远程管理，则必须为该帐户授予对分布式组件对象模型 (DCOM) 的远程激活权限。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-112">If you want to enable remote administration for a non-administrator user, you must grant the account Distributed Component Object Model (DCOM) Remote Activation permissions.</span></span> <span data-ttu-id="9dc1e-113">本主题提供了有关配置服务器以供非管理员访问的说明。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-113">Instructions for configuring the server for non-administrator access are provided in this topic.</span></span>  
  
 <span data-ttu-id="9dc1e-114">某些组织的组策略阻止某些操作系统或用户进行远程服务器管理。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-114">Some organizations have group policies that prevent remote server administration for certain operating systems or users.</span></span> <span data-ttu-id="9dc1e-115">开始修改防火墙设置之前，请与网络管理员进行核实，以确认是否存在对远程管理的限制。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-115">Before you begin modifying firewall settings, check with your network administrator to verify whether there are restrictions on remote administration.</span></span>  
  
 <span data-ttu-id="9dc1e-116">有关详细信息，请参阅 MSDN 上 Platform SDK 文档中的 [Connecting Through Windows Firewall](https://go.microsoft.com/fwlink/?LinkId=63615) （通过 Windows 防火墙连接）。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-116">For more information, see [Connecting Through Windows Firewall](https://go.microsoft.com/fwlink/?LinkId=63615) in the Platform SDK documentation on MSDN.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="9dc1e-117">任务</span><span class="sxs-lookup"><span data-stu-id="9dc1e-117">Tasks</span></span>  
 <span data-ttu-id="9dc1e-118">启用远程报表服务器配置的任务包括：</span><span class="sxs-lookup"><span data-stu-id="9dc1e-118">Tasks that enable remote report server configuration include the following:</span></span>  
  
-   <span data-ttu-id="9dc1e-119">在 Windows 防火墙中启用端口以允许报表服务器和 SQL Server 数据库引擎实例所使用的端口的请求。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-119">Enable ports in Windows Firewall to allow requests on ports used by the report server and by the SQL Server Database Engine instance.</span></span>  
  
-   <span data-ttu-id="9dc1e-120">启用与承载报表服务器数据库的数据库引擎实例之间的远程连接。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-120">Enable remote connections to the instance of the Database Engine instance that hosts the report server database.</span></span> <span data-ttu-id="9dc1e-121">远程连接是配置报表服务器数据库连接和管理加密密钥所必需的。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-121">A remote connection is necessary for configuring the report server database connection and managing the encryption keys.</span></span>  
  
-   <span data-ttu-id="9dc1e-122">启用远程 WMI 请求以通过 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 防火墙。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-122">Enable remote WMI requests to pass through the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows firewall.</span></span>  
  
-   <span data-ttu-id="9dc1e-123">如果要配置远程报表服务器以便由非管理用户进行管理，则必须设置 DCOM 权限以启用对标准 Windows 用户帐户的远程 WMI 访问。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-123">If you are configuring a remote report server for administration by a non-administrative user, you must set DCOM permissions to enable remote WMI access to a standard Windows user account.</span></span> <span data-ttu-id="9dc1e-124">由于 WMI 使用 DCOM 作为远程调用传输方式，因此必须设置 DCOM 权限，以使不是以本地管理员身份登录的用户可以配置服务器。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-124">Because WMI uses DCOM as transport for remote calls, you must set the DCOM permissions so that users who are not logged on as the local administrator can configure the server.</span></span>  
  
-   <span data-ttu-id="9dc1e-125">如果要配置远程报表服务器以便由非管理用户进行管理，则还必须设置对报表服务器 WMI 命名空间的 WMI 权限。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-125">If you are configuring a remote report server for administration by a non-administrative user, you must also set WMI permissions on the report server WMI namespace.</span></span> <span data-ttu-id="9dc1e-126">默认情况下，本地管理员组的所有成员都有权访问报表服务器 WMI 命名空间。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-126">By default, all members of the local Administrator group have access to the report server WMI namespace.</span></span> <span data-ttu-id="9dc1e-127">如果要对非管理员授予访问权限，则必须设置权限。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-127">If you want to grant access to non-administrators, you must set permissions.</span></span>  
  
 <span data-ttu-id="9dc1e-128">本主题中提供了有关如何执行这些任务的说明。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-128">Instructions on how to perform these tasks are provided in this topic.</span></span>  
  
### <a name="to-open-ports-in-windows-firewall"></a><span data-ttu-id="9dc1e-129">在 Windows 防火墙中打开端口</span><span class="sxs-lookup"><span data-stu-id="9dc1e-129">To open ports in Windows Firewall</span></span>  
  
1.  <span data-ttu-id="9dc1e-130">[为数据库引擎访问配置 Windows 防火墙](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-130">[Configure a Windows Firewall for Database Engine Access](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md).</span></span>  
  
2.  <span data-ttu-id="9dc1e-131">[为报表服务器访问配置防火墙](configure-a-firewall-for-report-server-access.md)。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-131">[Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md).</span></span>  
  
### <a name="to-configure-remote-connections-to-the-report-server-database"></a><span data-ttu-id="9dc1e-132">配置与报表服务器数据库的远程连接</span><span class="sxs-lookup"><span data-stu-id="9dc1e-132">To configure remote connections to the report server database</span></span>  
  
1.  <span data-ttu-id="9dc1e-133">单击 **“开始”**，依次指向 **“程序”**、 [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]、 **“配置工具”**，然后单击 **“SQL Server 配置管理器”**。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-133">Click **Start**, point to **Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="9dc1e-134">在左窗格中，展开“SQL Server 网络配置”，然后针对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例单击“协议”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-134">In the left pane, expand **SQL Server Network Configuration**, and then click **Protocols** for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="9dc1e-135">在详细信息窗格中，启用“TCP/IP”和“命名管道”协议，然后重启 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-135">In the details pane, enable the TCP/IP and Named Pipes protocols, and then restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
### <a name="to-enable-remote-administration-in-windows-firewall"></a><span data-ttu-id="9dc1e-136">在 Windows 防火墙中启用远程管理</span><span class="sxs-lookup"><span data-stu-id="9dc1e-136">To enable remote administration in Windows Firewall</span></span>  
  
1.  <span data-ttu-id="9dc1e-137">以本地管理员身份登录要启用远程管理功能的计算机。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-137">Log on as a local administrator to the computer for which you want to enable remote administration.</span></span>  
  
2.  <span data-ttu-id="9dc1e-138">如果 Report Server 在 Windows Vista 上运行，请右键单击 "**命令提示符**"，然后选择 "以**管理员身份运行**"。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-138">If the report server is running on Windows Vista, right-click **Command Prompt** and select **Run as administrator**.</span></span> <span data-ttu-id="9dc1e-139">对于其他操作系统，请打开一个命令提示符窗口。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-139">For other operating systems, open a command prompt window.</span></span>  
  
3.  <span data-ttu-id="9dc1e-140">运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="9dc1e-140">Run the following command:</span></span>  
  
    ```  
    netsh.exe firewall set service type=REMOTEADMIN mode=ENABLE scope=ALL  
    ```  
  
     <span data-ttu-id="9dc1e-141">可以指定不同的作用域选项。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-141">You can specify different options for Scope.</span></span> <span data-ttu-id="9dc1e-142">有关详细信息，请参阅 Windows 防火墙产品文档。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-142">For more information, see the Windows Firewall product documentation.</span></span>  
  
4.  <span data-ttu-id="9dc1e-143">验证是否已启用远程管理。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-143">Verify that remote administration is enabled.</span></span> <span data-ttu-id="9dc1e-144">可以运行以下命令以显示状态：</span><span class="sxs-lookup"><span data-stu-id="9dc1e-144">You can run the following command to show the status:</span></span>  
  
    ```  
    netsh.exe firewall show state  
    ```  
  
5.  <span data-ttu-id="9dc1e-145">重新启动计算机。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-145">Reboot the computer.</span></span>  
  
### <a name="to-set-dcom-permissions-to-enable-remote-wmi-access-for-non-administrators"></a><span data-ttu-id="9dc1e-146">设置 DCOM 权限为非管理员启用远程 WMI 访问</span><span class="sxs-lookup"><span data-stu-id="9dc1e-146">To set DCOM permissions to enable remote WMI access for non-administrators</span></span>  
  
1.  <span data-ttu-id="9dc1e-147">在“开始”菜单中，指向 **“管理工具”**，单击 **“组件服务”**。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-147">On the Start menu, point to **Administrative Tools**, click **Component Services**.</span></span>  
  
     <span data-ttu-id="9dc1e-148">对于 Windows Vista，在 "开始" 菜单上，依次单击 "**所有程序**"、"**运行**"，然后输入 `mmc comexp.msc` 。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-148">For Windows Vista, on the Start menu, click **All Programs**, click **Run**, and then enter `mmc comexp.msc`.</span></span>  
  
2.  <span data-ttu-id="9dc1e-149">打开“组件服务”文件夹。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-149">Open the Component Services folder.</span></span>  
  
3.  <span data-ttu-id="9dc1e-150">打开“计算机”文件夹。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-150">Open the Computers folder.</span></span>  
  
4.  <span data-ttu-id="9dc1e-151">选择“我的电脑”。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-151">Select My Computer.</span></span>  
  
5.  <span data-ttu-id="9dc1e-152">在 **“操作”** 菜单中，选择 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-152">On the **Action** menu, and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="9dc1e-153">单击 **“COM 安全”**。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-153">Click **COM Security**.</span></span>  
  
7.  <span data-ttu-id="9dc1e-154">在 **“启动和激活权限”** 中单击 **“编辑限制”**。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-154">In **Launch and Activation Permissions**, click **Edit Limits**.</span></span>  
  
8.  <span data-ttu-id="9dc1e-155">如果在 **“启动权限”** 中没有看到您的名称，请单击 **“添加”**。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-155">If you do not see your name in **Launch Permission**, click **Add**.</span></span>  
  
9. <span data-ttu-id="9dc1e-156">键入您的用户帐户名，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-156">Type the name of your user account, and then click **OK**.</span></span>  
  
10. <span data-ttu-id="9dc1e-157">在 "**权限 \<User or Group> **" 的 "**允许**" 列中，选择 "**远程启动**和**远程激活**"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-157">In **Permissions for \<User or Group>**, in the **Allow** column, select **Remote Launch** and **Remote Activation**, and then click **OK**.</span></span>  
  
### <a name="to-set-permissions-on-the-report-server-wmi-namespace-for-non-administrators"></a><span data-ttu-id="9dc1e-158">为非管理员设置报表服务器 WMI 命名空间的权限</span><span class="sxs-lookup"><span data-stu-id="9dc1e-158">To set permissions on the report server WMI namespace for non-administrators</span></span>  
  
1.  <span data-ttu-id="9dc1e-159">在“开始”菜单中，指向 **“管理工具”**，单击 **“计算机管理”**。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-159">On the Start menu, point to **Administrative Tools**, click **Computer Management**.</span></span>  
  
2.  <span data-ttu-id="9dc1e-160">打开“服务和应用程序”文件夹。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-160">Open the Services and Applications folder.</span></span>  
  
3.  <span data-ttu-id="9dc1e-161">右键单击“WMI 控件”，然后选择“属性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-161">Right-click **WMI Control**, and select **Properties**.</span></span>  
  
4.  <span data-ttu-id="9dc1e-162">单击 **“安全性”** 。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-162">Click **Security**.</span></span>  
  
5.  <span data-ttu-id="9dc1e-163">打开 Root 文件夹。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-163">Open the Root folder.</span></span>  
  
6.  <span data-ttu-id="9dc1e-164">打开 Microsoft 文件夹。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-164">Open the Microsoft folder.</span></span>  
  
7.  <span data-ttu-id="9dc1e-165">打开 SQLServer 文件夹。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-165">Open the SQLServer folder.</span></span>  
  
8.  <span data-ttu-id="9dc1e-166">打开 ReportServer 文件夹。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-166">Open the ReportServer folder.</span></span>  
  
9. <span data-ttu-id="9dc1e-167">打开实例文件夹。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-167">Open instance folder.</span></span> <span data-ttu-id="9dc1e-168">如果安装了默认实例，则文件夹为 MSSQLSERVER。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-168">If you installed the default instance, the folder is MSSQLSERVER.</span></span>  
  
10. <span data-ttu-id="9dc1e-169">打开 v10 文件夹。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-169">Open the v10 folder.</span></span>  
  
11. <span data-ttu-id="9dc1e-170">选中 Admin 文件夹，然后单击 **“安全性”**。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-170">Select the Admin folder, and then click **Security**.</span></span>  
  
12. <span data-ttu-id="9dc1e-171">单击 **“添加”**，然后键入将用于管理服务器的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-171">Click **Add**, and then type the user account you will use to manage the server.</span></span>  
  
13. <span data-ttu-id="9dc1e-172">在 **“允许”** 列中，选择 **“启用帐户”**、 **“远程启用”** 和 **“读取安全”**，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="9dc1e-172">In the **Allow** column, select **Enable Account**, **Remote Enable**, and **Read Security**, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dc1e-173">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9dc1e-173">See Also</span></span>  
 [<span data-ttu-id="9dc1e-174">Reporting Services Configuration Manager（本机模式）</span><span class="sxs-lookup"><span data-stu-id="9dc1e-174">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
