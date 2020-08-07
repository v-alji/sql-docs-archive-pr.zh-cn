---
title: 配置本机模式报表服务器进行本地管理 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- UAC
- installing Reporting Services
- Windows Vista
- Localhost
- windows server 2008
- Vista
ms.assetid: 312c6bb8-b3f7-4142-a55f-c69ee15bbf52
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ad53f293ef825a382d9e39b58527a36ef291687a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588305"
---
# <a name="configure-a-native-mode-report-server-for-local-administration-ssrs"></a><span data-ttu-id="75c22-102">为本地管理配置本机模式报表服务器 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="75c22-102">Configure a Native Mode Report Server for Local Administration (SSRS)</span></span>
  <span data-ttu-id="75c22-103">如果您想要在本地管理报表服务器实例，则将 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表服务器部署到以下操作系统之一要求更多的赋值步骤。</span><span class="sxs-lookup"><span data-stu-id="75c22-103">Deploying a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server on one of the following operating systems requires more configuration steps if you want to administer the report server instance locally.</span></span> <span data-ttu-id="75c22-104">本主题说明如何配置报表服务器以进行本地管理。</span><span class="sxs-lookup"><span data-stu-id="75c22-104">This topic explains how to configure the report server for local administration.</span></span> <span data-ttu-id="75c22-105">如果尚未安装或配置 Report Server，请参阅安装[向导中的安装 SQL Server 2014 &#40;安装程序&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)并[管理 Reporting Services 的本机模式报表服务器](manage-a-reporting-services-native-mode-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="75c22-105">If you have not yet installed or configured the report server, see [Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) and [Manage a Reporting Services Native Mode Report Server](manage-a-reporting-services-native-mode-report-server.md).</span></span>  
  
||  
|-|  
|<span data-ttu-id="75c22-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 本机模式</span><span class="sxs-lookup"><span data-stu-id="75c22-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode</span></span>|  
  
-   [!INCLUDE[winblue_server_2](../../includes/winblue-server-2-md.md)]  
  
-   [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]  
  
-   [!INCLUDE[win8](../../includes/win8-md.md)]  
  
-   [!INCLUDE[win8srv](../../includes/win8srv-md.md)]  
  
-   [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]  
  
-   [!INCLUDE[win7](../../includes/win7-md.md)]  
  
-   [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)]  
  
 <span data-ttu-id="75c22-107">因为上述操作系统限制了权限，所以本地 Administrators 组的成员运行大多数应用程序时就像使用标准用户帐户时一样。</span><span class="sxs-lookup"><span data-stu-id="75c22-107">Because the noted operating systems limit permissions, members of the local Administrators group run most applications as if they are using the Standard User account.</span></span>  
  
 <span data-ttu-id="75c22-108">虽然该方法可提高系统的整体安全性，但会阻止用户使用 Reporting Services 为本地管理员创建的预定义内置角色分配。</span><span class="sxs-lookup"><span data-stu-id="75c22-108">While this practice improves the overall security of your system, it prevents you from using the predefined, built-in role assignments that Reporting Services creates for local administrators.</span></span>  
  
-   [<span data-ttu-id="75c22-109">配置更改概述</span><span class="sxs-lookup"><span data-stu-id="75c22-109">Overview of Configuration Changes</span></span>](#bkmk_configuraiton_overview)  
  
-   [<span data-ttu-id="75c22-110">配置本地报表服务器和报表管理器管理</span><span class="sxs-lookup"><span data-stu-id="75c22-110">To Configure Local Report Server and Report Manager Administration</span></span>](#bkmk_configure_local_server)  
  
-   [<span data-ttu-id="75c22-111">为本地报表服务器管理配置 SQL Server Management Studio (SSMS)</span><span class="sxs-lookup"><span data-stu-id="75c22-111">To Configure SQL Server Management Studio (SSMS) for local report server administration</span></span>](#bkmk_configure_ssms)  
  
-   [<span data-ttu-id="75c22-112">配置 SQL Server Data Tools BI (SSDT) 以便发布到本地报表服务器</span><span class="sxs-lookup"><span data-stu-id="75c22-112">To Configure SQL Server Data Tools BI (SSDT) to Publish to a Local Report Server</span></span>](#bkmk_configure_ssdt)  
  
-   [<span data-ttu-id="75c22-113">其他信息</span><span class="sxs-lookup"><span data-stu-id="75c22-113">Additional Information</span></span>](#bkmk_addiitonal_informaiton)  
  
##  <a name="overview-of-configuration-changes"></a><a name="bkmk_configuraiton_overview"></a><span data-ttu-id="75c22-114">配置更改概述</span><span class="sxs-lookup"><span data-stu-id="75c22-114">Overview of Configuration Changes</span></span>  
 <span data-ttu-id="75c22-115">下面的配置更改对服务器进行配置，以便您可以使用标准用户权限管理报表服务器内容和操作：</span><span class="sxs-lookup"><span data-stu-id="75c22-115">The following configuration changes configure the server so that you can use standard user permissions to manage report server content and operations:</span></span>  
  
-   <span data-ttu-id="75c22-116">将 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL 添加到受信任站点。</span><span class="sxs-lookup"><span data-stu-id="75c22-116">Add [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URLs to trusted sites.</span></span> <span data-ttu-id="75c22-117">默认情况下，在上列操作系统上运行的 Internet Explorer 是以 **“保护模式”** 运行的，此功能可阻止浏览器请求到达运行在同一计算机上的高级别进程。</span><span class="sxs-lookup"><span data-stu-id="75c22-117">By default, Internet Explorer running on the listed operating systems runs in **Protected Mode**, a feature that blocks browser requests from reaching high-level processes that run on the same computer.</span></span> <span data-ttu-id="75c22-118">通过将报表服务器应用程序添加为受信任站点，可以禁用这些应用程序的保护模式。</span><span class="sxs-lookup"><span data-stu-id="75c22-118">You can disable protected mode for the report server applications by adding them as Trusted Sites.</span></span>  
  
-   <span data-ttu-id="75c22-119">创建角色分配，授予您（报表服务器管理员）管理内容和操作的权限而无需使用 Internet Explorer 中的 **“以管理员的身份运行”** 功能。</span><span class="sxs-lookup"><span data-stu-id="75c22-119">Create role assignments that grant you, the report server administrator, permission to manage content and operations without having to use the **Run as administrator** feature on Internet Explorer.</span></span> <span data-ttu-id="75c22-120">通过为您的 Windows 用户帐户创建角色分配，并通过显式角色分配替换 Reporting Services 创建的预定义的内置角色分配，您将获得对报表服务器的访问权限（包括内容管理员和系统管理员权限）。</span><span class="sxs-lookup"><span data-stu-id="75c22-120">By creating role assignments for your Windows user account, you gain access to a report server with Content Manager and System Administrator permissions through explicit role assignments that replace the predefined, built-in role assignments that Reporting Services creates.</span></span>  
  
##  <a name="to-configure-local-report-server-and-report-manager-administration"></a><a name="bkmk_configure_local_server"></a><span data-ttu-id="75c22-121">配置本地报表服务器和报表管理器管理</span><span class="sxs-lookup"><span data-stu-id="75c22-121">To Configure Local Report Server and Report Manager Administration</span></span>  
 <span data-ttu-id="75c22-122">如果您浏览到本地报表服务器并且看到如下错误，请完成本节中的配置步骤：</span><span class="sxs-lookup"><span data-stu-id="75c22-122">Complete the configuration steps in this section if you are browsing to a local report server and you see errors similar to the following:</span></span>  
  
-   <span data-ttu-id="75c22-123">用户 `'Domain\[user name]`' 没有必需的权限。</span><span class="sxs-lookup"><span data-stu-id="75c22-123">User `'Domain\[user name]`' does not have required permissions.</span></span> <span data-ttu-id="75c22-124">请验证授予了足够的权限并且解决了 Windows 用户帐户控制(UAC)限制问题。</span><span class="sxs-lookup"><span data-stu-id="75c22-124">Verify that sufficient permissions have been granted and Windows User Account Control (UAC) restrictions have been addressed.</span></span>  
  
###  <a name="trusted-site-settings-in-the-browser"></a><a name="bkmk_site_settings"></a><span data-ttu-id="75c22-125">浏览器中的受信任的站点设置</span><span class="sxs-lookup"><span data-stu-id="75c22-125">Trusted Site Settings in the Browser</span></span>  
  
1.  <span data-ttu-id="75c22-126">使用“以管理员的身份运行”权限打开一个浏览器窗口。</span><span class="sxs-lookup"><span data-stu-id="75c22-126">Open a browser window with Run as administrator permissions.</span></span> <span data-ttu-id="75c22-127">从 **“开始”** 菜单上，单击 **“所有程序”**，右键单击 **Internet Explorer**，然后选择 **“以管理员的身份运行”**。</span><span class="sxs-lookup"><span data-stu-id="75c22-127">From the **Start** menu, click **All Programs**, right-click **Internet Explorer**, and select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="75c22-128">单击 **“允许”** 以继续。</span><span class="sxs-lookup"><span data-stu-id="75c22-128">Click **Allow** to continue.</span></span>  
  
3.  <span data-ttu-id="75c22-129">在 URL 地址中，输入报表管理器 URL。</span><span class="sxs-lookup"><span data-stu-id="75c22-129">In the URL address, enter the Report Manager URL.</span></span> <span data-ttu-id="75c22-130">有关说明，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的[报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="75c22-130">For instructions, see [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
4.  <span data-ttu-id="75c22-131">单击 **“工具”** 。</span><span class="sxs-lookup"><span data-stu-id="75c22-131">Click **Tools**.</span></span>  
  
5.  <span data-ttu-id="75c22-132">单击 **“Internet 选项”** 。</span><span class="sxs-lookup"><span data-stu-id="75c22-132">Click **Internet Options**.</span></span>  
  
6.  <span data-ttu-id="75c22-133">单击 **“安全性”** 。</span><span class="sxs-lookup"><span data-stu-id="75c22-133">Click **Security**.</span></span>  
  
7.  <span data-ttu-id="75c22-134">单击 **“受信任的站点”** 。</span><span class="sxs-lookup"><span data-stu-id="75c22-134">Click **Trusted Sites**.</span></span>  
  
8.  <span data-ttu-id="75c22-135">单击 **“站点”** 。</span><span class="sxs-lookup"><span data-stu-id="75c22-135">Click **Sites**.</span></span>  
  
9. <span data-ttu-id="75c22-136">添加 `http://<your-server-name>`。</span><span class="sxs-lookup"><span data-stu-id="75c22-136">Add `http://<your-server-name>`.</span></span>  
  
10. <span data-ttu-id="75c22-137">如果不将 HTTPS 用于默认站点，请清除 **“对该区域中的所有站点要求服务器验证(https:)”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="75c22-137">Clear the check box **Require server certification (https:) for all sites in this zone** if you are not using HTTPS for the default site.</span></span>  
  
11. <span data-ttu-id="75c22-138">单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="75c22-138">Click **Add**.</span></span>  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
###  <a name="report-manager-folder-settings"></a><a name="bkmk_configure_folder_settings"></a><span data-ttu-id="75c22-139">报表管理器文件夹设置</span><span class="sxs-lookup"><span data-stu-id="75c22-139">Report Manager Folder Settings</span></span>  
  
1.  <span data-ttu-id="75c22-140">在报表管理器的主页上，单击 **“文件夹设置”**。</span><span class="sxs-lookup"><span data-stu-id="75c22-140">In Report Manager, on the Home page, click **Folder Settings**.</span></span>  
  
2.  <span data-ttu-id="75c22-141">在“文件夹设置”页中，单击 **“安全性”**。</span><span class="sxs-lookup"><span data-stu-id="75c22-141">In the Folder Settings page, click **Security**.</span></span>  
  
3.  <span data-ttu-id="75c22-142">单击 **“新建角色分配”**。</span><span class="sxs-lookup"><span data-stu-id="75c22-142">Click **New Role Assignment**.</span></span>  
  
4.  <span data-ttu-id="75c22-143">在“组或用户名” \*\*\*\* 字段中，按以下格式键入 Windows 用户帐户： `<domain>\<user>`。</span><span class="sxs-lookup"><span data-stu-id="75c22-143">In the **Group or user name** field, type your Windows user account in this format: `<domain>\<user>`.</span></span>  
  
5.  <span data-ttu-id="75c22-144">选择 **“内容管理员”** 。</span><span class="sxs-lookup"><span data-stu-id="75c22-144">Select **Content Manager**.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
###  <a name="report-manager-site-settings"></a><a name="bkmk_configure_site_settings"></a><span data-ttu-id="75c22-145">报表管理器站点设置</span><span class="sxs-lookup"><span data-stu-id="75c22-145">Report Manager Site Settings</span></span>  
  
1.  <span data-ttu-id="75c22-146">使用管理权限打开浏览器并浏览到报表管理器 `http://<server name>/reports`。</span><span class="sxs-lookup"><span data-stu-id="75c22-146">Open your browser with administrative privileges and browse to report manager, `http://<server name>/reports`.</span></span>  
  
2.  <span data-ttu-id="75c22-147">单击主页上角的 **“站点设置”** 。</span><span class="sxs-lookup"><span data-stu-id="75c22-147">Click **Site Settings** in the upper corner of the Home page.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="75c22-148">**注意：** 如果您没有看到 **“站点设置”** 选项，则关闭后再重新打开您的浏览器，然后使用管理权限浏览到报表管理器。</span><span class="sxs-lookup"><span data-stu-id="75c22-148">**Note:** If you do not see the **Site Settings** option, close and reopen your browser and browse to report manager with administrative privileges.</span></span>  
  
3.  <span data-ttu-id="75c22-149">单击 "**安全**"。</span><span class="sxs-lookup"><span data-stu-id="75c22-149">Click **security**.</span></span>  
  
4.  <span data-ttu-id="75c22-150">单击 **“新建角色分配”**。</span><span class="sxs-lookup"><span data-stu-id="75c22-150">Click **New Role Assignment**.</span></span>  
  
5.  <span data-ttu-id="75c22-151">在“组或用户名” \*\*\*\* 字段中，按以下格式键入 Windows 用户帐户： `<domain>\<user>`。</span><span class="sxs-lookup"><span data-stu-id="75c22-151">In the **Group or user name** field, type your Windows user account in this format: `<domain>\<user>`.</span></span>  
  
6.  <span data-ttu-id="75c22-152">选择 **“系统管理员”**。</span><span class="sxs-lookup"><span data-stu-id="75c22-152">Select **System Administrator**.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="75c22-153">关闭报表管理器。</span><span class="sxs-lookup"><span data-stu-id="75c22-153">Close Report Manager.</span></span>  
  
9. <span data-ttu-id="75c22-154">重新在 Internet Explorer 中打开报表管理器，但不使用 **“以管理员的身份运行”**。</span><span class="sxs-lookup"><span data-stu-id="75c22-154">Re-open Report Manager in Internet Explorer, without using **Run as administrator**.</span></span>  
  
##  <a name="to-configure-sql-server-management-studio-ssms-for-local-report-server-administration"></a><a name="bkmk_configure_ssms"></a><span data-ttu-id="75c22-155">为本地 Report Server 管理配置 SQL Server Management Studio (SSMS) </span><span class="sxs-lookup"><span data-stu-id="75c22-155">To Configure SQL Server Management Studio (SSMS) for local report server administration</span></span>  
 <span data-ttu-id="75c22-156">默认情况下，您不能访问在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中提供的所有报表服务器属性，除非您使用管理权限启动 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="75c22-156">By default, you cannot access all of the report server properties available in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] unless you start [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] with administrative privileges.</span></span>  
  
 <span data-ttu-id="75c22-157">**配置 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]** 角色属性和角色分配，以便您无需每次都使用提升的权限启动 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="75c22-157">**To configure [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]** role properties and role assignments so you do not need to start [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] with elevated permissions each time:</span></span>  
  
-   <span data-ttu-id="75c22-158">在“开始”菜单，依次单击“所有程序”和“SQL Server 2014”，右键单击 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]，然后单击“以管理员身份运行”\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="75c22-158">From the **Start** menu, click **All Programs**, click **SQL Server 2014**, right-click **[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]**, and then click **Run as administrator**.</span></span>  
  
-   <span data-ttu-id="75c22-159">连接到您的本地 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="75c22-159">Connect to your local [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] server.</span></span>  
  
-   <span data-ttu-id="75c22-160">在 **“安全性”** 节点中，单击 **“系统角色”**。</span><span class="sxs-lookup"><span data-stu-id="75c22-160">In the **Security** node, click **System Roles**.</span></span>  
  
-   <span data-ttu-id="75c22-161">右键单击 **“系统管理员”** ，然后单击 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="75c22-161">Right-click **System Administrator** and then click **Properties**.</span></span>  
  
-   <span data-ttu-id="75c22-162">在 **“系统角色属性”** 页中，选择 **“查看报表服务器属性”**。</span><span class="sxs-lookup"><span data-stu-id="75c22-162">In the **System Role Properties** page, select **View report server properties**.</span></span> <span data-ttu-id="75c22-163">选择您要与系统管理员角色的成员相关联的任何其他属性。</span><span class="sxs-lookup"><span data-stu-id="75c22-163">Select any other properties you want associated with members of the system administrators role.</span></span>  
  
-   <span data-ttu-id="75c22-164">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="75c22-164">Click **OK**.</span></span>  
  
-   <span data-ttu-id="75c22-165">关闭 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75c22-165">Close [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]</span></span>  
  
-   <span data-ttu-id="75c22-166">若要将某一用户添加到系统角色“系统管理员”，请参阅本主题中前面的 [报表管理器站点设置](#bkmk_configure_site_settings) 部分。</span><span class="sxs-lookup"><span data-stu-id="75c22-166">To add a user to the system role "system administrator", see the [Report Manager Site Settings](#bkmk_configure_site_settings) section earlier in this topic.</span></span>  
  
 <span data-ttu-id="75c22-167">现在，在您打开 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 并且没有明确选择 **“以管理员身份运行”** 时，您有权访问报表服务器属性。</span><span class="sxs-lookup"><span data-stu-id="75c22-167">Now when you open [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and do not explicitly select **Run as administrator** you have access to the report server properties.</span></span>  
  
##  <a name="to-configure-sql-server-data-tools-bi-ssdt-to-publish-to-a-local-report-server"></a><a name="bkmk_configure_ssdt"></a><span data-ttu-id="75c22-168">将 SQL Server Data Tools BI (SSDT) 配置为发布到本地报表服务器</span><span class="sxs-lookup"><span data-stu-id="75c22-168">To Configure SQL Server Data Tools BI (SSDT) to Publish to a Local Report Server</span></span>  
 <span data-ttu-id="75c22-169">如果您在本主题的第一节中列出的操作系统之一上安装了 [!INCLUDE[SSDTDev11](../../includes/ssdtdev11-md.md)] ，并且希望 SSDT 与本地本机模式报表服务器交互，您将会遇到权限错误，除非您使用提升的权限打开 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 或者配置报表服务角色。</span><span class="sxs-lookup"><span data-stu-id="75c22-169">If you installed [!INCLUDE[SSDTDev11](../../includes/ssdtdev11-md.md)] on one of the operating systems listed in the first section of this topic, and you want SSDT to interact with a local Native mode report server, you will experiences permission errors unless you open [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] with elevated permissions or configure reporting services roles.</span></span> <span data-ttu-id="75c22-170">例如，如果您没有足够的权限，将遇到如下问题：</span><span class="sxs-lookup"><span data-stu-id="75c22-170">For example, if you do not have sufficient permissions, you experience issues similar to the following:</span></span>  
  
-   <span data-ttu-id="75c22-171">在您尝试将报表项部署到本地报表服务器时，您将在 **“错误列表”** 窗口中看到如下错误消息：</span><span class="sxs-lookup"><span data-stu-id="75c22-171">When you attempt to deploy report items to the local report server, you see an error message similar to the following in the **Error List** window:</span></span>  
  
    -   <span data-ttu-id="75c22-172">为用户“域\\<user name\>”授予的权限不足，无法执行此操作。</span><span class="sxs-lookup"><span data-stu-id="75c22-172">The permissions granted to user 'Domain\\<user name\>' are insufficient for performing this operation.</span></span>  
  
 <span data-ttu-id="75c22-173">**在每次打开 SSDT 时使用提升的权限运行：**</span><span class="sxs-lookup"><span data-stu-id="75c22-173">**To run with elevated permissions each time you open SSDT:**</span></span>  
  
1.  <span data-ttu-id="75c22-174">在 "开始" 屏幕上，键入 `sql server` ，然后右键单击 " **SQL Server Data Tools For Visual Studio**"。</span><span class="sxs-lookup"><span data-stu-id="75c22-174">From the start screen, type `sql server` and then right-click **SQL Server Data Tools for Visual Studio**.</span></span> <span data-ttu-id="75c22-175">单击 **“以管理员身份运行”**。</span><span class="sxs-lookup"><span data-stu-id="75c22-175">Click **Run as administrator**</span></span>  
  
     <span data-ttu-id="75c22-176">**或者**，在较早的操作系统上：</span><span class="sxs-lookup"><span data-stu-id="75c22-176">**Or**, on older operating systems:</span></span>  
  
     <span data-ttu-id="75c22-177">从 **“开始”** 菜单上，依次单击 **“所有程序”** 和 **SQL Server 2014**，右键单击 **“SQL Server Data Tools”**，然后单击 **“以管理员的身份运行”**。</span><span class="sxs-lookup"><span data-stu-id="75c22-177">From the **Start** menu, click **All Programs**, click **SQL Server 2014**, right-click **SQL Server Data Tools**, and then click **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="75c22-178">单击 **“继续”** 。</span><span class="sxs-lookup"><span data-stu-id="75c22-178">Click **Continue**.</span></span>  
  
3.  <span data-ttu-id="75c22-179">单击 **“运行程序”**。</span><span class="sxs-lookup"><span data-stu-id="75c22-179">Click **Run Program**.</span></span>  
  
 <span data-ttu-id="75c22-180">现在，您应该能够将报表和其他项部署到本地报表服务器上了。</span><span class="sxs-lookup"><span data-stu-id="75c22-180">You should now be able to deploy reports and other items to a local report server.</span></span>  
  
 <span data-ttu-id="75c22-181">**配置 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 角色分配，以便您无需每次都使用提升的权限启动 SSDT：**</span><span class="sxs-lookup"><span data-stu-id="75c22-181">**To configure [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] role assignments so you do not need to start SSDT with elevated permissions each time:**</span></span>  
  
-   <span data-ttu-id="75c22-182">请参阅本主题中前面的 [报表管理器文件夹设置](#bkmk_configure_folder_settings) 和 [报表管理器站点设置](#bkmk_configure_site_settings) 部分。</span><span class="sxs-lookup"><span data-stu-id="75c22-182">See the [Report Manager Folder Settings](#bkmk_configure_folder_settings) and [Report Manager Site Settings](#bkmk_configure_site_settings) sections earlier in this topic.</span></span>  
  
##  <a name="additional-information"></a><a name="bkmk_addiitonal_informaiton"></a><span data-ttu-id="75c22-183">附加信息</span><span class="sxs-lookup"><span data-stu-id="75c22-183">Additional Information</span></span>  
 <span data-ttu-id="75c22-184">与 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 管理相关的一个附加的常见配置步骤是在 Windows 防火墙中打开端口 80，以便允许访问报表服务器计算机。</span><span class="sxs-lookup"><span data-stu-id="75c22-184">An additional and common configuration step related to [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] administration is to open port 80 in Windows Firewall to allow access to the report server computer.</span></span> <span data-ttu-id="75c22-185">有关说明，请参阅 [Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md)。</span><span class="sxs-lookup"><span data-stu-id="75c22-185">For instructions, see [Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75c22-186">另请参阅</span><span class="sxs-lookup"><span data-stu-id="75c22-186">See Also</span></span>  
 [<span data-ttu-id="75c22-187">管理 Reporting Services 本机模式报表服务器</span><span class="sxs-lookup"><span data-stu-id="75c22-187">Manage a Reporting Services Native Mode Report Server</span></span>](manage-a-reporting-services-native-mode-report-server.md)  
  
  
