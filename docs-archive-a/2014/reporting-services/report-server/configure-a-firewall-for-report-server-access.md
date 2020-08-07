---
title: 将防火墙配置为允许报表服务器访问 | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- firewall systems [Reporting Services]
- configuring servers [Reporting Services]
ms.assetid: 04dae07a-a3a4-424c-9bcb-a8000e20dc93
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b578c980522d24f5a24a73fdfd080ec425335aac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588306"
---
# <a name="configure-a-firewall-for-report-server-access"></a><span data-ttu-id="1e7ae-102">Configure a Firewall for Report Server Access</span><span class="sxs-lookup"><span data-stu-id="1e7ae-102">Configure a Firewall for Report Server Access</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="1e7ae-103">可以通过指定 IP 地址、端口和虚拟目录的 URL 访问报表服务器应用程序和已发布的报表。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-103">Report server applications and published reports are accessed through URLs that specify an IP address, port, and virtual directory.</span></span> <span data-ttu-id="1e7ae-104">如果 Windows 防火墙已开启，配置为报表服务器使用的端口很可能已关闭。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-104">If Windows Firewall is turned on, the port that the report server is configured to use is most likely closed.</span></span> <span data-ttu-id="1e7ae-105">表明端口可能已关闭的迹象包括请求报表后出现空白网页，或尝试从远程客户端计算机打开报表管理器时出现空白页。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-105">Indications that a port might be closed are the appearance of a blank Web page after requesting a report, or a blank page when you attempt to open Report Manager from a remote client computer.</span></span>  
  
 <span data-ttu-id="1e7ae-106">若要打开端口，必须在报表服务器计算机上使用 Windows 防火墙实用工具。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-106">To open a port, you must use the Windows Firewall utility on the report server computer.</span></span> <span data-ttu-id="1e7ae-107">Reporting Services 不会帮您打开端口，您必须手动执行该步骤。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-107">Reporting Services will not open ports for you; you must perform this step manually.</span></span>  
  
 <span data-ttu-id="1e7ae-108">默认情况下，报表服务器侦听端口 80 的 HTTP 请求。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-108">By default, the report server listens for HTTP requests on port 80.</span></span> <span data-ttu-id="1e7ae-109">因此，以下操作说明包括用来指定该端口的步骤。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-109">As such, the following instructions include steps that specify that port.</span></span> <span data-ttu-id="1e7ae-110">如果将报表服务器 URL 配置为使用其他端口，则在按照以下说明进行操作时必须指定相应的端口号。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-110">If you configured the report server URLs to use a different port, you must specify that port number when following the instructions below.</span></span>  
  
 <span data-ttu-id="1e7ae-111">如果要访问外部计算机上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 关系数据库，或者如果报表服务器数据库在外部 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上，则必须在外部计算机上打开端口 1433 和 1434。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-111">If you are accessing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] relational databases on external computers, or if the report server database is on an external [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, you must open port 1433 and 1434 on the external computer.</span></span> <span data-ttu-id="1e7ae-112">有关详细信息，请参阅 [联机丛书中的](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) 为数据库引擎访问配置 Windows 防火墙 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-112">For more information, see [Configure a Windows Firewall for Database Engine Access](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="1e7ae-113">有关默认 Windows 防火墙设置的详细信息，以及有关影响 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]和 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]的 TCP 端口的说明，请参阅 [联机丛书中的](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md) 配置 Windows 防火墙以允许 SQL Server 访问 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-113">For more information about the default Windows firewall settings, and a description of the TCP ports that affect the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], see [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1e7ae-114">必备条件</span><span class="sxs-lookup"><span data-stu-id="1e7ae-114">Prerequisites</span></span>  
 <span data-ttu-id="1e7ae-115">这些操作说明假定您已经配置了服务帐户，创建了报表服务器数据库，并为报表服务器 Web 服务和报表管理器配置了 URL。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-115">These instructions assume that you already configured the service account, created the report server database, and configured URLs for the Report Server Web service and Report Manager.</span></span> <span data-ttu-id="1e7ae-116">有关详细信息，请参阅 [管理 Reporting Services 本机模式报表服务器](manage-a-reporting-services-native-mode-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-116">For more information, see [Manage a Reporting Services Native Mode Report Server](manage-a-reporting-services-native-mode-report-server.md).</span></span>  
  
 <span data-ttu-id="1e7ae-117">您还应验证是否可以通过将本地 Web 浏览器连接到本地报表服务器实例来访问报表服务器。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-117">You should also have verified that the report server is accessible over a local Web browser connection to the local report server instance.</span></span> <span data-ttu-id="1e7ae-118">此步骤可确保您拥有有效的安装。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-118">This step establishes that you have a working installation.</span></span> <span data-ttu-id="1e7ae-119">开始打开端口之前，应验证是否已对安装进行了正确的配置。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-119">You should verify that the installation is configured correctly before you begin opening ports.</span></span> <span data-ttu-id="1e7ae-120">若要在 Windows Server 中完成该步骤，还必须将报表服务器站点添加到“受信任的站点”中。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-120">To complete this step on  Windows Server, you must have also added the report server site to Trusted Sites.</span></span> <span data-ttu-id="1e7ae-121">有关详细信息，请参阅 [为本地管理配置本机模式报表服务器 (SSRS)](configure-a-native-mode-report-server-for-local-administration-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-121">For more information, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
## <a name="opening-ports-in-windows-firewall"></a><span data-ttu-id="1e7ae-122">在 Windows 防火墙中打开端口</span><span class="sxs-lookup"><span data-stu-id="1e7ae-122">Opening Ports in Windows Firewall</span></span>  
 <span data-ttu-id="1e7ae-123">针对不同版本的 Windows 防火墙分别有不同的说明。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-123">There are separate instructions for different versions of Windows Firewall.</span></span>  
  
#### <a name="to-open-port-80-on-windows-7-windows-server-2008-r2-windows-server-2012-and-2012-r2"></a><span data-ttu-id="1e7ae-124">要在 Windows 7、Windows Server 2008 R2、Windows Server 2012 和 2012 R2 中打开端口 80</span><span class="sxs-lookup"><span data-stu-id="1e7ae-124">To open port 80 on Windows 7, Windows Server 2008 R2, Windows Server 2012 and 2012 R2</span></span>  
  
1.  <span data-ttu-id="1e7ae-125">在 **“开始”** 菜单上单击 **“控制面板”**，单击 **“系统和安全”**，然后单击 **“Windows 防火墙”**。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-125">From the **Start** menu, click **Control Panel**, click **System and Security**, and then click **Windows Firewall**.</span></span> <span data-ttu-id="1e7ae-126">不为“类别”视图配置控制面板，您只需要选择 **“Windows 防火墙”**。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-126">Control Panel is not configured for 'Category' view, you only need to select **Windows Firewall.**</span></span>  
  
2.  <span data-ttu-id="1e7ae-127">单击“高级设置”  。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-127">Click **Advanced Settings**.</span></span>  
  
3.  <span data-ttu-id="1e7ae-128">单击 **“入站规则”**。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-128">Click **Inbound Rules.**</span></span>  
  
4.  <span data-ttu-id="1e7ae-129">在 **“操作”** 窗口中单击 **“新建规则”** 。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1e7ae-129">Click **New Rule** in the **Actions** window **.**</span></span>  
  
5.  <span data-ttu-id="1e7ae-130">单击 **“端口”** 的 **“规则类型”**。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-130">Click **Rule Type** of **Port.**</span></span>  
  
6.  <span data-ttu-id="1e7ae-131">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-131">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="1e7ae-132">在 **“协议和端口”** 页上，单击 **TCP**。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-132">On the **Protocol and Ports** page click **TCP**.</span></span>  
  
8.  <span data-ttu-id="1e7ae-133">选择 **“特定本地端口”** ，然后键入值 **80**。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-133">Select **Specific Local Ports** and type a value of **80**.</span></span>  
  
9. <span data-ttu-id="1e7ae-134">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-134">Click **Next**.</span></span>  
  
10. <span data-ttu-id="1e7ae-135">在 **“操作”** 页上，单击 **“允许连接”**。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-135">On the **Action** page click **Allow the connection**.</span></span>  
  
11. <span data-ttu-id="1e7ae-136">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-136">Click **Next**.</span></span>  
  
12. <span data-ttu-id="1e7ae-137">在 **“配置文件”** 页上，单击适合您的环境的选项。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-137">On the **Profile** page click the appropriate options for your environment.</span></span>  
  
13. <span data-ttu-id="1e7ae-138">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-138">Click **Next**.</span></span>  
  
14. <span data-ttu-id="1e7ae-139">在“名称”页上，输入名称“ReportServer (TCP on port 80)”\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="1e7ae-139">On the **Name** page enter a name of**ReportServer (TCP on port 80)**</span></span>  
  
15. <span data-ttu-id="1e7ae-140">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-140">Click **Finish**.</span></span>  
  
16. <span data-ttu-id="1e7ae-141">重新启动计算机。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-141">Restart the computer.</span></span>  
  
#### <a name="to-open-port-80-on-windows-vista-or-windows-server-2008"></a><span data-ttu-id="1e7ae-142">在 Windows Vista 或 Windows Server 2008 中打开端口 80</span><span class="sxs-lookup"><span data-stu-id="1e7ae-142">To open port 80 on Windows Vista or Windows Server 2008</span></span>  
  
1.  <span data-ttu-id="1e7ae-143">从 "**开始**" 菜单中，单击 "**控制面板**"，单击 "**安全**"，然后单击 " **Windows 防火墙**"。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-143">From the **Start** menu, click **Control Panel**, click **Security**, and then click **Windows Firewall**.</span></span>  
  
2.  <span data-ttu-id="1e7ae-144">单击“允许程序通过 Windows 防火墙”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-144">Click **Allow a program through Windows Firewall**.</span></span>  
  
3.  <span data-ttu-id="1e7ae-145">单击 **“继续”** 。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-145">Click **Continue**.</span></span>  
  
4.  <span data-ttu-id="1e7ae-146">在 "例外" 选项卡上，单击 "**添加端口**"。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-146">On the Exceptions tab, click **Add Port**.</span></span>  
  
5.  <span data-ttu-id="1e7ae-147">在 "名称" 中，键入\*\*端口80上的 ReportServer (TCP) \*\*。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-147">In Name, type **ReportServer (TCP on port 80)**.</span></span>  
  
6.  <span data-ttu-id="1e7ae-148">在 "端口号" 中，键入**80**。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-148">In Port number, type **80**.</span></span>  
  
7.  <span data-ttu-id="1e7ae-149">验证是否选择了 " **TCP** "。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-149">Verify that **TCP** is selected.</span></span>  
  
8.  <span data-ttu-id="1e7ae-150">单击 "**更改范围**"。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-150">Click **Change Scope**.</span></span>  
  
9. <span data-ttu-id="1e7ae-151">单击 "\*\*我的网络 (子网) \*\*，然后单击 **" 确定 "**。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-151">Click **My network (subnet) only**, and then click **OK**.</span></span>  
  
10. <span data-ttu-id="1e7ae-152">单击 **“确定”** 关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-152">Click **OK** to close the dialog box.</span></span>  
  
11. <span data-ttu-id="1e7ae-153">重新启动计算机。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-153">Restart the computer.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="1e7ae-154">后续步骤</span><span class="sxs-lookup"><span data-stu-id="1e7ae-154">Next Steps</span></span>  
 <span data-ttu-id="1e7ae-155">打开端口后，必须在确认远程用户是否可以通过所打开的端口访问报表服务器之前，通过主文件夹或站点级别的角色分配授予用户访问报表服务器的权限。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-155">After you open the port and before you confirm whether remote users can access the report server on the port that you open, you must grant user access to the report server through role assignments on Home and at the site level.</span></span> <span data-ttu-id="1e7ae-156">如果用户不具有足够的权限，那么虽然可以正确地打开端口，但报表服务器连接仍会失败。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-156">You can open a port correctly and still have report server connections fail if users do not have sufficient permissions.</span></span> <span data-ttu-id="1e7ae-157">有关详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的[授予用户对报表服务器的访问权限（报表管理器）](../security/grant-user-access-to-a-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-157">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](../security/grant-user-access-to-a-report-server.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="1e7ae-158">您还可以通过在其他计算机上启动报表管理器来验证是否正确打开了端口。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-158">You can also verify that the port is opened correctly by starting Report Manager on a different computer.</span></span> <span data-ttu-id="1e7ae-159">有关详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的[报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="1e7ae-159">For more information, see [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e7ae-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1e7ae-160">See Also</span></span>  
 <span data-ttu-id="1e7ae-161">[配置报表服务器服务帐户（SSRS 配置管理器）](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="1e7ae-161">[Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="1e7ae-162">[配置报表服务器 URL（SSRS 配置管理器）](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="1e7ae-162">[Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="1e7ae-163">[&#40;SSRS Configuration Manager 创建报表服务器数据库&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="1e7ae-163">[Create a Report Server Database  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="1e7ae-164">[配置报表服务器服务帐户（SSRS 配置管理器）](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="1e7ae-164">[Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="1e7ae-165">管理 Reporting Services 本机模式报表服务器</span><span class="sxs-lookup"><span data-stu-id="1e7ae-165">Manage a Reporting Services Native Mode Report Server</span></span>](manage-a-reporting-services-native-mode-report-server.md)  
  
  
