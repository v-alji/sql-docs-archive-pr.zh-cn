---
title: PowerPivot for SharePoint 2013 安装 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: d3310562-82c1-454f-9c48-33a241749238
author: minewiskan
ms.author: owend
ms.openlocfilehash: 74d0e1cc78b4004a832a312f9f8ae8deb23904f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688351"
---
# <a name="powerpivot-for-sharepoint-2013-installation"></a><span data-ttu-id="e54bf-102">PowerPivot for SharePoint 2013 安装</span><span class="sxs-lookup"><span data-stu-id="e54bf-102">PowerPivot for SharePoint 2013 Installation</span></span>
  <span data-ttu-id="e54bf-103">本主题中的过程将指导您以 SharePoint 部署模式在单台服务器上安装 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="e54bf-103">The procedures in this topic guide you through a single server installation of a [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint deployment mode.</span></span> <span data-ttu-id="e54bf-104">涉及的步骤包括运行 SQL Server 安装向导以及使用 SharePoint 2013 管理中心的配置任务。</span><span class="sxs-lookup"><span data-stu-id="e54bf-104">The steps include running the SQL Server installation wizard as well as configuration tasks that use SharePoint 2013 Central Administration.</span></span>  
  
 <span data-ttu-id="e54bf-105">**[!INCLUDE[applies](../../../includes/applies-md.md)]** SharePoint 2013 |SharePoint 201</span><span class="sxs-lookup"><span data-stu-id="e54bf-105">**[!INCLUDE[applies](../../../includes/applies-md.md)]**  SharePoint 2013 | SharePoint 201</span></span>  
  
 <span data-ttu-id="e54bf-106">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="e54bf-106">**In this topic:**</span></span>  
  
 [<span data-ttu-id="e54bf-107">背景</span><span class="sxs-lookup"><span data-stu-id="e54bf-107">Background</span></span>](#bkmk_background)  
  
 [<span data-ttu-id="e54bf-108">先决条件</span><span class="sxs-lookup"><span data-stu-id="e54bf-108">Prerequisites</span></span>](#bkmk_prereq)  
  
 [<span data-ttu-id="e54bf-109">步骤 1：安装 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="e54bf-109">Step 1: Install PowerPivot for SharePoint</span></span>](#InstallSQL)  
  
 [<span data-ttu-id="e54bf-110">步骤 2：配置基本 Analysis Services SharePoint 集成</span><span class="sxs-lookup"><span data-stu-id="e54bf-110">Step 2: Configure Basic Analysis Services SharePoint Integration</span></span>](#bkmk_config)  
  
 [<span data-ttu-id="e54bf-111">步骤 3：验证集成</span><span class="sxs-lookup"><span data-stu-id="e54bf-111">Step 3: Verify the Integration</span></span>](#bkmk_verify)  
  
 [<span data-ttu-id="e54bf-112">配置 Windows 防火墙以允许 Analysis Services 访问</span><span class="sxs-lookup"><span data-stu-id="e54bf-112">Configure the Windows Firewall to Allow Analysis Services Access</span></span>](#bkmk_firewall)  
  
 [<span data-ttu-id="e54bf-113">升级工作簿和计划的数据刷新</span><span class="sxs-lookup"><span data-stu-id="e54bf-113">Upgrade Workbooks and Scheduled Data Refresh</span></span>](#bkmk_upgrade_workbook)  
  
 [<span data-ttu-id="e54bf-114">除单服务器安装之外-PowerPivot for Microsoft SharePoint</span><span class="sxs-lookup"><span data-stu-id="e54bf-114">Beyond the Single-Server Installation -PowerPivot for Microsoft SharePoint</span></span>](#bkmk_multiple_servers)  
  
##  <a name="background"></a><a name="bkmk_background"></a> <span data-ttu-id="e54bf-115">背景</span><span class="sxs-lookup"><span data-stu-id="e54bf-115">Background</span></span>  
 <span data-ttu-id="e54bf-116">PowerPivot for SharePoint 是在 SharePoint 2013 场中提供 PowerPivot 数据访问的中间层和后端服务的集合。</span><span class="sxs-lookup"><span data-stu-id="e54bf-116">PowerPivot for SharePoint is a collection of middle-tier and backend services that provide PowerPivot data access in a SharePoint 2013 farm.</span></span>  
  
-   <span data-ttu-id="e54bf-117">**后端服务：** 如果您使用 PowerPivot for Excel 来创建包含分析数据的工作簿，则必须具有 PowerPivot for SharePoint 才能在服务器环境中访问这些数据。</span><span class="sxs-lookup"><span data-stu-id="e54bf-117">**Backend services:** If you use PowerPivot for Excel to create workbooks that contain analytical data, you must have PowerPivot for SharePoint to access that data in a server environment.</span></span> <span data-ttu-id="e54bf-118">您可在安装了 SharePoint Server 2013 的计算机上或没有 SharePoint 软件的其他计算机上运行 SQL Server 安装程序。</span><span class="sxs-lookup"><span data-stu-id="e54bf-118">You can run SQL Server Setup on a computer that has SharePoint Server 2013 installed, or on a different computer that has no SharePoint software.</span></span> <span data-ttu-id="e54bf-119">Analysis Services 对 SharePoint 没有任何依赖关系。</span><span class="sxs-lookup"><span data-stu-id="e54bf-119">Analysis Services does not have any dependencies on SharePoint.</span></span>  
  
     <span data-ttu-id="e54bf-120">**注意：** 本主题介绍 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 服务器和后端服务的安装。</span><span class="sxs-lookup"><span data-stu-id="e54bf-120">**Note:** This topic describes the installation of the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server and the backend services.</span></span>  
  
-   <span data-ttu-id="e54bf-121">**中间层：** 增强 SharePoint 中 PowerPivot 体验的各项功能，包括 PowerPivot 库、计划数据刷新、管理面板和数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="e54bf-121">**Middle-tier:** Enhancements to the PowerPivot experiences in SharePoint including PowerPivot Gallery, Schedule data refresh, Management dashboard, and data providers.</span></span> <span data-ttu-id="e54bf-122">有关安装和配置中间层的详细信息，请参阅下面的内容：</span><span class="sxs-lookup"><span data-stu-id="e54bf-122">For more information on installing and configuring the middle-tier, see the following:</span></span>  
  
    -   [<span data-ttu-id="e54bf-123">在 SharePoint 2013 &#40;安装或卸载 PowerPivot for SharePoint 加载项&#41;</span><span class="sxs-lookup"><span data-stu-id="e54bf-123">Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)  
  
    -   [<span data-ttu-id="e54bf-124">&#40;SharePoint 2013&#41;配置 PowerPivot 和部署解决方案</span><span class="sxs-lookup"><span data-stu-id="e54bf-124">Configure PowerPivot and Deploy Solutions &#40;SharePoint 2013&#41;</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013)  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq"></a><span data-ttu-id="e54bf-125">先决条件</span><span class="sxs-lookup"><span data-stu-id="e54bf-125">Prerequisites</span></span>  
  
1.  <span data-ttu-id="e54bf-126">您必须是本地管理员才能运行 SQL Server 安装程序。</span><span class="sxs-lookup"><span data-stu-id="e54bf-126">You must be a local administrator to run SQL Server Setup.</span></span>  
  
2.  <span data-ttu-id="e54bf-127">SharePoint Server 2013 企业版是 PowerPivot for SharePoint 所必需的。</span><span class="sxs-lookup"><span data-stu-id="e54bf-127">SharePoint Server 2013 enterprise edition is required for PowerPivot for SharePoint.</span></span> <span data-ttu-id="e54bf-128">您也可以使用评估企业版。</span><span class="sxs-lookup"><span data-stu-id="e54bf-128">You can also use the evaluation enterprise edition.</span></span>  
  
3.  <span data-ttu-id="e54bf-129">计算机必须加入与 Excel Services 相同的 Active Directory 林中的域。</span><span class="sxs-lookup"><span data-stu-id="e54bf-129">The computer must be joined to a domain in the same Active Directory forest as Excel Services.</span></span>  
  
4.  <span data-ttu-id="e54bf-130">必须提供 PowerPivot 实例名称。</span><span class="sxs-lookup"><span data-stu-id="e54bf-130">The PowerPivot instance name must be available.</span></span> <span data-ttu-id="e54bf-131">在您要在其上以 SharePoint 模式安装 Analysis Services 的计算机上，您无法拥有现有的 PowerPivot 命名实例。</span><span class="sxs-lookup"><span data-stu-id="e54bf-131">You cannot have an existing PowerPivot-named instance on the computer on which you are installing Analysis Services in SharePoint mode.</span></span>  
  
5.  <span data-ttu-id="e54bf-132">[在 SharePoint 模式下查看 Analysis Services 服务器的硬件和软件要求 &#40;SQL Server 2014&#41;](../../../sql-server/install/hardware-software-requirements-analysis-services-server-sharepoint-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="e54bf-132">Review [Hardware and Software Requirements for Analysis Services Server in SharePoint Mode &#40;SQL Server 2014&#41;](../../../sql-server/install/hardware-software-requirements-analysis-services-server-sharepoint-mode.md).</span></span>  
  
6.  <span data-ttu-id="e54bf-133">查看[SQL Server 2012 Service Pack 1 发行说明](https://go.microsoft.com/fwlink/?LinkID=248389) (上的发行说明 https://go.microsoft.com/fwlink/?LinkID=248389) 。</span><span class="sxs-lookup"><span data-stu-id="e54bf-133">Review the release notes at [SQL Server 2012 Service Pack 1 Release Notes](https://go.microsoft.com/fwlink/?LinkID=248389) (https://go.microsoft.com/fwlink/?LinkID=248389).</span></span>  
  
###  <a name="sql-server-edition-requirements"></a><a name="bkmk_sqleditions"></a> <span data-ttu-id="e54bf-134">SQL Server 版本要求</span><span class="sxs-lookup"><span data-stu-id="e54bf-134">SQL Server Edition Requirements</span></span>  
 <span data-ttu-id="e54bf-135">并不是所有的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]版本中都提供了商业智能功能。</span><span class="sxs-lookup"><span data-stu-id="e54bf-135">Business intelligence features are not all available in all editions of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="e54bf-136">有关详细信息，请参阅 SQL Server 2014 的版本[SQL Server 2012 (https://go.microsoft.com/fwlink/?linkid=232473) ](https://go.microsoft.com/fwlink/?linkid=232473)和[版本和组件](../../../sql-server/editions-and-components-of-sql-server-2016.md)支持的功能。</span><span class="sxs-lookup"><span data-stu-id="e54bf-136">For details, see [Features Supported by the Editions of SQL Server 2012 (https://go.microsoft.com/fwlink/?linkid=232473)](https://go.microsoft.com/fwlink/?linkid=232473) and [Editions and Components of SQL Server 2014](../../../sql-server/editions-and-components-of-sql-server-2016.md).</span></span>  
  
 <span data-ttu-id="e54bf-137">可在[SQL Server 2012 SP1 发行说明](https://go.microsoft.com/fwlink/?LinkID=248389) (找到当前发行说明 https://go.microsoft.com/fwlink/?LinkID=248389) 。</span><span class="sxs-lookup"><span data-stu-id="e54bf-137">The current release notes can be found at [SQL Server 2012 SP1 Release Notes](https://go.microsoft.com/fwlink/?LinkID=248389) (https://go.microsoft.com/fwlink/?LinkID=248389).</span></span>  
  
 <span data-ttu-id="e54bf-138">[Microsoft SQL Server 2012 发行说明 (https://go.microsoft.com/fwlink/?LinkId=236893) ](https://go.microsoft.com/fwlink/?LinkId=236893)。</span><span class="sxs-lookup"><span data-stu-id="e54bf-138">[Microsoft SQL Server 2012 Release Notes (https://go.microsoft.com/fwlink/?LinkId=236893)](https://go.microsoft.com/fwlink/?LinkId=236893).</span></span>  
  
##  <a name="step-1-install-powerpivot-for-sharepoint"></a><a name="InstallSQL"></a><span data-ttu-id="e54bf-139">步骤1：安装 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="e54bf-139">Step 1: Install PowerPivot for SharePoint</span></span>  
 <span data-ttu-id="e54bf-140">在此步骤中，您将运行 SQL Server 安装程序以便在 SharePoint 模式下安装 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e54bf-140">In this step, you run SQL Server Setup to install an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode.</span></span> <span data-ttu-id="e54bf-141">在后续步骤中，将 Excel Services 配置为使用此服务器的工作簿数据模型。</span><span class="sxs-lookup"><span data-stu-id="e54bf-141">In a subsequent step, you configure Excel Services to use this server for workbook data models.</span></span>  
  
1.  <span data-ttu-id="e54bf-142">运行 SQL Server 安装向导 (Setup.exe)。</span><span class="sxs-lookup"><span data-stu-id="e54bf-142">Run the SQL Server Installation Wizard (Setup.exe).</span></span>  
  
2.  <span data-ttu-id="e54bf-143">在左侧导航中，单击 **“安装”** 。</span><span class="sxs-lookup"><span data-stu-id="e54bf-143">Click **Installation** in the left navigation.</span></span>  
  
3.  <span data-ttu-id="e54bf-144">单击 **“全新 SQL Server 独立安装或向现有安装添加功能”**。</span><span class="sxs-lookup"><span data-stu-id="e54bf-144">Click **New SQL Server stand-alone installation or add features to an existing installation**.</span></span>  
  
4.  <span data-ttu-id="e54bf-145">如果看到 **“产品密钥”** 页，请指定 Evaluation Edition 或者为 Enterprise Edition 的许可副本输入产品密钥。</span><span class="sxs-lookup"><span data-stu-id="e54bf-145">If you see the **Product Key** page, specify the evaluation edition or enter a product key for a licensed copy of the enterprise edition.</span></span> <span data-ttu-id="e54bf-146">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="e54bf-146">Click **Next**.</span></span> <span data-ttu-id="e54bf-147">有关版本的详细信息，请参阅 [Editions and Components of SQL Server 2014](../../../sql-server/editions-and-components-of-sql-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="e54bf-147">For more information on editions, see [Editions and Components of SQL Server 2014](../../../sql-server/editions-and-components-of-sql-server-2016.md).</span></span>  
  
5.  <span data-ttu-id="e54bf-148">查看并接受 Microsoft 软件许可协议条款，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="e54bf-148">Review and accept the Microsoft Software License Terms of agreement, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="e54bf-149">如果显示 **“全局规则”** 页，请查看安装向导显示的所有规则信息。</span><span class="sxs-lookup"><span data-stu-id="e54bf-149">If you see the **Global Rules** page, review any rules information the setup wizard displays.</span></span>  
  
7.  <span data-ttu-id="e54bf-150">在 **“Microsoft Update”** 页上，建议您使用 Microsoft Update 检查更新，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="e54bf-150">On the **Microsoft Update** page, it is recommended you use Microsoft Update to check for updates, then click **Next**.</span></span>  
  
8.  <span data-ttu-id="e54bf-151">**“安装安装程序文件”** 页将运行几分钟。</span><span class="sxs-lookup"><span data-stu-id="e54bf-151">The **Install Setup Files** page runs for several minutes.</span></span> <span data-ttu-id="e54bf-152">查看所有规则警告或失败的规则，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="e54bf-152">Review any rule warnings or failed rules, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="e54bf-153">如果看到其他 **“安装程序支持规则”**，请查看所有警告并单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="e54bf-153">If you see another **Setup Support Rules**, review any warnings and click **Next**.</span></span>  
  
     <span data-ttu-id="e54bf-154">**注意：** 因为启用了 Windows 防火墙，所以您将看到打开端口以便允许进行远程访问的警告。</span><span class="sxs-lookup"><span data-stu-id="e54bf-154">**Note:** Because Windows Firewall is enabled, you see a warning to open ports to enable remote access.</span></span>  
  
10. <span data-ttu-id="e54bf-155">在 **“设置角色”** 页中，选择 **“SQL Server PowerPivot for SharePoint”**。</span><span class="sxs-lookup"><span data-stu-id="e54bf-155">On the **Setup Role** page, select **SQL Server PowerPivot for SharePoint**.</span></span> <span data-ttu-id="e54bf-156">此选项将在 SharePoint 模式下安装 Analysis Services。</span><span class="sxs-lookup"><span data-stu-id="e54bf-156">This option installs Analysis Services in SharePoint mode.</span></span>  
  
     <span data-ttu-id="e54bf-157">或者，您可以向您的安装添加数据库引擎的实例。</span><span class="sxs-lookup"><span data-stu-id="e54bf-157">Optionally, you can add an instance of the Database Engine to your installation.</span></span> <span data-ttu-id="e54bf-158">设置新场时，可以添加数据库引擎，并需要数据库服务器来运行该场的配置和内容数据库。</span><span class="sxs-lookup"><span data-stu-id="e54bf-158">You might add the Database Engine when setting up a new farm and need a database server to run the farm's configuration and content databases.</span></span> <span data-ttu-id="e54bf-159">此选项也将安装 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e54bf-159">This option also installs [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
     <span data-ttu-id="e54bf-160">如果添加数据库引擎，则将其作为 **PowerPivot** 命名实例安装。</span><span class="sxs-lookup"><span data-stu-id="e54bf-160">If you add the Database Engine, it is installed as a **PowerPivot** named instance.</span></span> <span data-ttu-id="e54bf-161">在指定此实例的连接时，按以下格式输入数据库名称：[`servername`]\PowerPivot。</span><span class="sxs-lookup"><span data-stu-id="e54bf-161">Whenever you specify a connection to this instance, enter the database name in this format: [`servername`]\PowerPivot.</span></span>  
  
     <span data-ttu-id="e54bf-162">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="e54bf-162">Click **Next**.</span></span>  
  
     <span data-ttu-id="e54bf-163">![设置角色](../../../sql-server/install/media/gmni-setupui-featurerole-sql2012sp1.gif "安装角色")</span><span class="sxs-lookup"><span data-stu-id="e54bf-163">![Setup Role](../../../sql-server/install/media/gmni-setupui-featurerole-sql2012sp1.gif "Setup Role")</span></span>  
  
11. <span data-ttu-id="e54bf-164">“功能选择”中会显示功能的只读列表以便供您参考。</span><span class="sxs-lookup"><span data-stu-id="e54bf-164">In Feature Selection, a read-only list of the features is displayed for informational purposes.</span></span> <span data-ttu-id="e54bf-165">不能添加或删除为此角色预先选择的项。</span><span class="sxs-lookup"><span data-stu-id="e54bf-165">You cannot add or remove items the preselected items for this role.</span></span> <span data-ttu-id="e54bf-166">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="e54bf-166">Click **Next**.</span></span>  
  
12. <span data-ttu-id="e54bf-167">在 **“实例配置”** 页中，将显示“PowerPivot”的只读实例名称供您参考。</span><span class="sxs-lookup"><span data-stu-id="e54bf-167">On the **Instance Configuration** page, a read-only instance name of 'PowerPivot' is displayed for informational purposes.</span></span> <span data-ttu-id="e54bf-168">该实例名称是必需的并且不能修改。</span><span class="sxs-lookup"><span data-stu-id="e54bf-168">This instance name is required and it cannot be modified.</span></span> <span data-ttu-id="e54bf-169">但是，您可以输入唯一的实例 ID 以便指定说明性的目录名称和注册表项。</span><span class="sxs-lookup"><span data-stu-id="e54bf-169">However, you can enter a unique Instance ID to specify a descriptive directory name and registry keys.</span></span> <span data-ttu-id="e54bf-170">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="e54bf-170">Click **Next**.</span></span>  
  
13. <span data-ttu-id="e54bf-171">在 **“服务器配置”** 页上，为自动的 **启动类型**配置所有服务。</span><span class="sxs-lookup"><span data-stu-id="e54bf-171">On the **Server Configuration** page, configure all of the services for Automatic **Startup Type**.</span></span> <span data-ttu-id="e54bf-172">为 **SQL Server Analysis Services**指定所需的域帐户和密码，即下图中的 **(1)** 。</span><span class="sxs-lookup"><span data-stu-id="e54bf-172">Specify the desired domain account and password for **SQL Server Analysis Services**, **(1)** in the following diagram.</span></span>  
  
    -   <span data-ttu-id="e54bf-173">对于 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]，您可使用 **域用户** 帐户或 **NetworkService** 帐户。</span><span class="sxs-lookup"><span data-stu-id="e54bf-173">For [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], you can use a **domain user** account or **NetworkService** account.</span></span> <span data-ttu-id="e54bf-174">请勿使用 LocalSystem 或 LocalService 帐户。</span><span class="sxs-lookup"><span data-stu-id="e54bf-174">Do not use LocalSystem or LocalService accounts.</span></span>  
  
    -   <span data-ttu-id="e54bf-175">如果您添加了 SQL Server 数据库引擎和 SQL Server 代理，则可以将服务配置为在域用户帐户或者默认虚拟帐户下运行。</span><span class="sxs-lookup"><span data-stu-id="e54bf-175">If you added the SQL Server Database Engine and SQL Server Agent, you can configure the services to run under domain user accounts or under the default virtual account.</span></span>  
  
    -   <span data-ttu-id="e54bf-176">切勿使用您自己的域用户帐户来设置服务帐户。</span><span class="sxs-lookup"><span data-stu-id="e54bf-176">Never provision service accounts with your own domain user account.</span></span> <span data-ttu-id="e54bf-177">这样做会向服务器授予您在网络中对资源拥有的相同权限。</span><span class="sxs-lookup"><span data-stu-id="e54bf-177">Doing so grants the server the same permissions that you have to the resources in your network.</span></span> <span data-ttu-id="e54bf-178">如果恶意用户威胁服务器，则该用户将基于您的域凭据登录。</span><span class="sxs-lookup"><span data-stu-id="e54bf-178">If a malicious user compromises the server, that user is logged in under your domain credentials.</span></span> <span data-ttu-id="e54bf-179">并且该用户有权下载或使用您所能下载或使用的相同数据和应用程序。</span><span class="sxs-lookup"><span data-stu-id="e54bf-179">The user has the permissions to download or use the same data and applications that you do.</span></span>  
  
     <span data-ttu-id="e54bf-180">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="e54bf-180">Click **Next**.</span></span>  
  
     <span data-ttu-id="e54bf-181">![SSAS Server 配置](../../../sql-server/install/media/ssas-powerpivotsetupsql2012sp1-serverconfiguration.gif "SSAS Server 配置")</span><span class="sxs-lookup"><span data-stu-id="e54bf-181">![SSAS Server Configuration](../../../sql-server/install/media/ssas-powerpivotsetupsql2012sp1-serverconfiguration.gif "SSAS Server Configuration")</span></span>  
  
14. <span data-ttu-id="e54bf-182">如果安装 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]，则将显示 **“数据库引擎配置”** 页。</span><span class="sxs-lookup"><span data-stu-id="e54bf-182">If you are installing the [!INCLUDE[ssDE](../../../includes/ssde-md.md)], the **Database Engine Configuration** page appears.</span></span> <span data-ttu-id="e54bf-183">在“ [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 配置”中，单击 **“添加当前用户”** 以便授予您的用户帐户对数据库引擎实例的管理员权限。</span><span class="sxs-lookup"><span data-stu-id="e54bf-183">In [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Configuration, click **Add Current User** to grant your user account administrator permissions on the Database Engine instance.</span></span>  
  
     <span data-ttu-id="e54bf-184">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="e54bf-184">Click **Next**.</span></span>  
  
15. <span data-ttu-id="e54bf-185">在 **“Analysis Services 配置”** 页中，单击 **“添加当前用户”** 以便向您的用户帐户授予管理权限。</span><span class="sxs-lookup"><span data-stu-id="e54bf-185">On the **Analysis Services Configuration** page, click **Add Current User** to grant your user account administrative permissions.</span></span> <span data-ttu-id="e54bf-186">在完成安装程序后，您将需要管理权限以便对服务器进行配置。</span><span class="sxs-lookup"><span data-stu-id="e54bf-186">You will need administrative permission to configure the server after Setup is finished.</span></span>  
  
    -   <span data-ttu-id="e54bf-187">在同一页中，添加也要求管理权限的任何人士的 Windows 用户帐户。</span><span class="sxs-lookup"><span data-stu-id="e54bf-187">In the same page, add the Windows user account of any person who also requires administrative permissions.</span></span> <span data-ttu-id="e54bf-188">例如，如果用户想要在 [!INCLUDE[ssGeminiSrv](../../../includes/ssgeminisrv-md.md)] 中连接到 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 实例以便排除数据库连接问题，则任何此类用户都必须具有系统管理员权限。</span><span class="sxs-lookup"><span data-stu-id="e54bf-188">For example, any user who wants to connect to the [!INCLUDE[ssGeminiSrv](../../../includes/ssgeminisrv-md.md)] instance in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] to troubleshoot database connection problems must have system administrator permissions.</span></span> <span data-ttu-id="e54bf-189">添加可能需要立即排除服务器问题或管理服务器的任何人士的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="e54bf-189">Add the user account of any person who might need to troubleshoot or administer the server now.</span></span>  
  
    -   > [!NOTE]  
        >  <span data-ttu-id="e54bf-190">所有需要具有对 Analysis Services 服务器实例的访问权限的服务应用程序均需要具有 Analysis Services 管理权限。</span><span class="sxs-lookup"><span data-stu-id="e54bf-190">All service applications that require access to the Analysis Services server instance need to have Analysis Services Administrative permissions.</span></span> <span data-ttu-id="e54bf-191">例如，分别为 Excel Services、Power View 和 Performance Point Services 添加服务帐户。</span><span class="sxs-lookup"><span data-stu-id="e54bf-191">For example, add the service accounts for Excel Services, Power View, and Performance Point Services.</span></span> <span data-ttu-id="e54bf-192">此外，添加 SharePoint 场帐户，该帐户用作承载管理中心的 Web 应用程序的标识。</span><span class="sxs-lookup"><span data-stu-id="e54bf-192">Also, add the SharePoint farm account, which is used as the identity of the web application that hosts Central Administration.</span></span>  
  
     <span data-ttu-id="e54bf-193">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="e54bf-193">Click **Next**.</span></span>  
  
16. <span data-ttu-id="e54bf-194">在“错误报告”\*\*\*\* 页上，单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e54bf-194">On the **Error Reporting** page, click **Next**.</span></span>  
  
17. <span data-ttu-id="e54bf-195">在 "**准备安装**" 页上，单击 "**安装**"。</span><span class="sxs-lookup"><span data-stu-id="e54bf-195">On the **Ready to Install** page, click **Install**.</span></span>  
  
18. <span data-ttu-id="e54bf-196">如果您看到 **“需要重新启动计算机”** 对话框，请单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="e54bf-196">If you see the dialog **Computer Restart Required**, click **OK**.</span></span>  
  
19. <span data-ttu-id="e54bf-197">安装完成后，单击 **“关闭”**。</span><span class="sxs-lookup"><span data-stu-id="e54bf-197">When the installation is complete, click **Close**.</span></span>  
  
20. <span data-ttu-id="e54bf-198">重新启动计算机。</span><span class="sxs-lookup"><span data-stu-id="e54bf-198">Restart the computer.</span></span>  
  
21. <span data-ttu-id="e54bf-199">如果您的环境中有防火墙，请阅读 SQL Server 联机丛书主题 [Configure the Windows Firewall to Allow Analysis Services Access](../configure-the-windows-firewall-to-allow-analysis-services-access.md)。</span><span class="sxs-lookup"><span data-stu-id="e54bf-199">If you have a firewall in your environment, review the SQL Server Books Online topic, [Configure the Windows Firewall to Allow Analysis Services Access](../configure-the-windows-firewall-to-allow-analysis-services-access.md).</span></span>  
  
### <a name="verify-the-sql-server-installation"></a><span data-ttu-id="e54bf-200">验证 SQL Server 安装</span><span class="sxs-lookup"><span data-stu-id="e54bf-200">Verify the SQL Server Installation</span></span>  
 <span data-ttu-id="e54bf-201">验证 Analysis Services 服务是否正在运行。</span><span class="sxs-lookup"><span data-stu-id="e54bf-201">Verify that the Analysis Services Service is running.</span></span>  
  
1.  <span data-ttu-id="e54bf-202">在 Microsoft Windows 中，依次单击 **“开始”**、 **“所有程序”** 和 **“Microsoft SQL Server 2012”** 组。</span><span class="sxs-lookup"><span data-stu-id="e54bf-202">In Microsoft Windows click **Start**, click **All Programs**, and click the **Microsoft SQL Server 2012** group.</span></span>  
  
2.  <span data-ttu-id="e54bf-203">单击 **“SQL Server Management Studio”**。</span><span class="sxs-lookup"><span data-stu-id="e54bf-203">Click **SQL Server Management Studio**.</span></span>  
  
3.  <span data-ttu-id="e54bf-204">连接到 Analysis Services 实例，例如 **[你的服务器名称]\POWERPIVOT**。</span><span class="sxs-lookup"><span data-stu-id="e54bf-204">Connect to the Analysis Services instance, for example **[your server name]\POWERPIVOT**.</span></span> <span data-ttu-id="e54bf-205">如果您可连接到该实例，则验证服务是否正在运行。</span><span class="sxs-lookup"><span data-stu-id="e54bf-205">If you can connect to the instance, you have verified the Service is running.</span></span>  
  
##  <a name="step-2-configure-basic-analysis-services-sharepoint-integration"></a><a name="bkmk_config"></a><span data-ttu-id="e54bf-206">步骤2：配置基本 Analysis Services SharePoint 集成</span><span class="sxs-lookup"><span data-stu-id="e54bf-206">Step 2: Configure Basic Analysis Services SharePoint Integration</span></span>  
 <span data-ttu-id="e54bf-207">下列步骤介绍与 SharePoint 文档库中的 Excel 高级数据模型交互所需的配置更改。</span><span class="sxs-lookup"><span data-stu-id="e54bf-207">The following steps describe configuration changes needed so you can interact with Excel advanced data models inside a SharePoint document library.</span></span> <span data-ttu-id="e54bf-208">在安装 SharePoint Server 2013 和 SQL Server Analysis Services 之后完成这些步骤。</span><span class="sxs-lookup"><span data-stu-id="e54bf-208">Complete these steps after you install SharePoint Server 2013 and SQL Server Analysis Services.</span></span>  
  
### <a name="grant-excel-services-server-administration-rights-on-analysis-services"></a><span data-ttu-id="e54bf-209">授予对 Analysis Services 的 Excel Services 服务器管理权限</span><span class="sxs-lookup"><span data-stu-id="e54bf-209">Grant Excel Services Server Administration Rights on Analysis Services</span></span>  
 <span data-ttu-id="e54bf-210">如果在 Analysis Services 安装过程中，您将 Excel Services 应用程序服务帐户添加为 Analysis Services 管理员，则无需完成此部分。</span><span class="sxs-lookup"><span data-stu-id="e54bf-210">You do not need to complete this section if during the Analysis Services installation; you added the Excel Services Application service account as an Analysis Services administrator.</span></span>  
  
1.  <span data-ttu-id="e54bf-211">在 Analysis Services 服务器上，启动 SQL Server Management Studio 并连接到 Analysis Services 实例，例如 `[MyServer]\POWERPIVOT`。</span><span class="sxs-lookup"><span data-stu-id="e54bf-211">On the Analysis Services server, start SQL Server Management Studio and connect to the Analysis Services instance, for example `[MyServer]\POWERPIVOT`.</span></span>  
  
2.  <span data-ttu-id="e54bf-212">在对象资源管理器中，右键单击实例名称，再单击 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="e54bf-212">In Object Explorer, Right-click the instance name and click **Properties**.</span></span>  
  
     <span data-ttu-id="e54bf-213">![查看 SSAS 服务器的属性](../../../sql-server/install/media/as-ssms-proeprties.gif "查看 SSAS 服务器的属性")</span><span class="sxs-lookup"><span data-stu-id="e54bf-213">![View Properties of an SSAS server](../../../sql-server/install/media/as-ssms-proeprties.gif "View Properties of an SSAS server")</span></span>  
  
3.  <span data-ttu-id="e54bf-214">在左窗格中，单击 **“安全性”**。</span><span class="sxs-lookup"><span data-stu-id="e54bf-214">In the left pane, click **Security**.</span></span> <span data-ttu-id="e54bf-215">添加您在步骤 1 中为 Excel Services 应用程序配置的域登录名。</span><span class="sxs-lookup"><span data-stu-id="e54bf-215">Add the domain login you configured for the Excel Services Application in step 1.</span></span>  
  
     <span data-ttu-id="e54bf-216">![SSAS 服务器的安全设置](../../../sql-server/install/media/as-ssms-security.gif "SSAS 服务器的安全设置")</span><span class="sxs-lookup"><span data-stu-id="e54bf-216">![Security Settings of an SSAS Server](../../../sql-server/install/media/as-ssms-security.gif "Security Settings of an SSAS Server")</span></span>  
  
### <a name="configure-excel-services-for-analysis-services-integration"></a><span data-ttu-id="e54bf-217">为 Analysis Services 集成配置 Excel Services</span><span class="sxs-lookup"><span data-stu-id="e54bf-217">Configure Excel Services for Analysis Services integration</span></span>  
  
1.  <span data-ttu-id="e54bf-218">在 SharePoint 管理中心的“应用程序管理”组中，单击 **“管理服务应用程序”**。</span><span class="sxs-lookup"><span data-stu-id="e54bf-218">In SharePoint Central Administration, in the Application Management group, click **Manage Service Applications**.</span></span>  
  
2.  <span data-ttu-id="e54bf-219">单击服务应用程序的名称，默认名称为 **“Excel 服务应用程序”**。</span><span class="sxs-lookup"><span data-stu-id="e54bf-219">Click the name of your service application, the default is **Excel Services Application**.</span></span>  
  
3.  <span data-ttu-id="e54bf-220">在 **“管理 Excel Services 应用程序”** 页上，单击 **“数据模型设置”**。</span><span class="sxs-lookup"><span data-stu-id="e54bf-220">On the **Manage Excel Services Application page**, click **Data Model Settings**.</span></span>  
  
4.  <span data-ttu-id="e54bf-221">单击 **“添加服务器”**。</span><span class="sxs-lookup"><span data-stu-id="e54bf-221">Click **Add Server**.</span></span>  
  
5.  <span data-ttu-id="e54bf-222">在 **“服务器名称”** 中，键入 Analysis Services 服务器名称和 PowerPivot 实例名称。</span><span class="sxs-lookup"><span data-stu-id="e54bf-222">In **Server Name**, type the Analysis Services server name and the PowerPivot instance name.</span></span> <span data-ttu-id="e54bf-223">例如 `MyServer\POWERPIVOT`。</span><span class="sxs-lookup"><span data-stu-id="e54bf-223">For example `MyServer\POWERPIVOT`.</span></span> <span data-ttu-id="e54bf-224">需要 PowerPivot 实例名称。</span><span class="sxs-lookup"><span data-stu-id="e54bf-224">The PowerPivot instance name is required.</span></span>  
  
     <span data-ttu-id="e54bf-225">键入说明。</span><span class="sxs-lookup"><span data-stu-id="e54bf-225">Type a description.</span></span>  
  
6.  <span data-ttu-id="e54bf-226">单击“确定” 。</span><span class="sxs-lookup"><span data-stu-id="e54bf-226">Click **Ok**.</span></span>  
  
7.  <span data-ttu-id="e54bf-227">更改将在几分钟后生效，您也可以 **“停止”** 和 **“启动”** 服务 **“Excel Calculation Services”**。</span><span class="sxs-lookup"><span data-stu-id="e54bf-227">The changes will take effect in a few minutes or you can **Stop** and **Start** the service **Excel Calculation Services**.</span></span> <span data-ttu-id="e54bf-228">功能</span><span class="sxs-lookup"><span data-stu-id="e54bf-228">To</span></span>  
  
     <span data-ttu-id="e54bf-229">另一个选项是使用管理权限打开命令提示符，并键入 `iisreset /noforce`。</span><span class="sxs-lookup"><span data-stu-id="e54bf-229">Another option is to open a command prompt with administrative privileges, and type `iisreset /noforce`.</span></span>  
  
     <span data-ttu-id="e54bf-230">您可通过查看 ULS 日志中的条目来验证 Excel Services 是否能识别服务器。</span><span class="sxs-lookup"><span data-stu-id="e54bf-230">You can verify the server is recognized by Excel Services by reviewing entries in the ULS log.</span></span> <span data-ttu-id="e54bf-231">您将看到类似于以下内容的条目：</span><span class="sxs-lookup"><span data-stu-id="e54bf-231">You will see entries similar to the following:</span></span>  
  
    ```  
    Excel Services Application            Data Model        27           Medium                Check Administrator Access ([ServerName]\POWERPIVOT): Pass.        f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
    Excel Services Application            Data Model        27           Medium                Check Server Version ([ServerName]\POWERPIVOT): Pass (11.0.2809.24 >= 11.0.2800.0).         f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
    Excel Services Application            Data Model        27           Medium                Check Deployment Mode ([ServerName]\POWERPIVOT): Pass.            f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
  
    ```  
  
##  <a name="step-3-verify-the-integration"></a><a name="bkmk_verify"></a><span data-ttu-id="e54bf-232">步骤3：验证集成</span><span class="sxs-lookup"><span data-stu-id="e54bf-232">Step 3: Verify the Integration</span></span>  
 <span data-ttu-id="e54bf-233">下列步骤指导你创建和上载新的工作簿以验证 Analysis Services 集成。</span><span class="sxs-lookup"><span data-stu-id="e54bf-233">The following steps walk you through creating and uploading a new workbook to verify the Analysis Services integration.</span></span> <span data-ttu-id="e54bf-234">您将需要 SQL Server 数据库才能完成这些步骤。</span><span class="sxs-lookup"><span data-stu-id="e54bf-234">You will need a SQL Server database to complete the steps.</span></span>  
  
1.  <span data-ttu-id="e54bf-235">**注意：** 如果您已具有包含切片器或筛选器的高级工作簿，则可将其上载到 SharePoint 文档库并验证您是否能通过文档库视图与切片器和筛选器进行交互。</span><span class="sxs-lookup"><span data-stu-id="e54bf-235">**Note:** If you already have an advanced workbook with slicers or filters, you can upload it to your SharePoint document library and verify you are able to interact with the slicers and filters from the document library view.</span></span>  
  
2.  <span data-ttu-id="e54bf-236">在 Excel 中启动新的工作簿。</span><span class="sxs-lookup"><span data-stu-id="e54bf-236">Start a new workbook in Excel.</span></span>  
  
3.  <span data-ttu-id="e54bf-237">在“数据”选项卡上，单击 **“获取外部数据”** 中功能区上的 **“从其他源”**。</span><span class="sxs-lookup"><span data-stu-id="e54bf-237">On the Data tab, click **From Other Sources** on the ribbon in the **Get External Data**.</span></span>  
  
4.  <span data-ttu-id="e54bf-238">选择 **“从 SQL Server”**。</span><span class="sxs-lookup"><span data-stu-id="e54bf-238">Select **From SQL Server**.</span></span>  
  
5.  <span data-ttu-id="e54bf-239">在 **“数据连接向导”** 中，输入包含您要使用的数据库的 SQL Server 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="e54bf-239">In the **Data Connection Wizard**, enter the name of the SQL Server instance that has the database you want to use.</span></span>  
  
6.  <span data-ttu-id="e54bf-240">或使用凭据登录，验证是否选择了 **“使用 Windows 身份验证”** ，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="e54bf-240">or Log on credentials, verify that **Use Windows Authentication** is selected, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="e54bf-241">选择要使用的数据库。</span><span class="sxs-lookup"><span data-stu-id="e54bf-241">Select the database you want to use.</span></span>  
  
8.  <span data-ttu-id="e54bf-242">验证是否选中了 **“连接到特定表”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="e54bf-242">Verify that the **Connect to specific table** checkbox is selected.</span></span>  
  
9. <span data-ttu-id="e54bf-243">单击 **“启用多表选择并将表添加到 Excel 数据模型”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="e54bf-243">Click the **Enable selection of multiple tables and add tables to the Excel Data Model** checkbox.</span></span>  
  
10. <span data-ttu-id="e54bf-244">选择要导入的表。</span><span class="sxs-lookup"><span data-stu-id="e54bf-244">Select the tables you want to import.</span></span>  
  
11. <span data-ttu-id="e54bf-245">单击 **“导入所选表之间的关系”** 复选框，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="e54bf-245">Click the checkbox **Import relationships between selected tables**, and then click **Next**.</span></span> <span data-ttu-id="e54bf-246">从关系数据库中导入多个表使您可使用已关联的表。</span><span class="sxs-lookup"><span data-stu-id="e54bf-246">Importing multiple tables from a relational database lets you work with tables that are already related.</span></span> <span data-ttu-id="e54bf-247">您可省略步骤，因为您无需手动构建关系。</span><span class="sxs-lookup"><span data-stu-id="e54bf-247">You save steps because you don't have to build the relationships manually.</span></span>  
  
12. <span data-ttu-id="e54bf-248">在向导的 **“保存数据连接文件并完成”** 页中，键入连接的名称并单击 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="e54bf-248">In the **Save Data Connection File and Finish** page of the wizard,, type a dame for your connection and click **Finish**.</span></span>  
  
13. <span data-ttu-id="e54bf-249">将出现 **“导入数据”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="e54bf-249">The **Import Data** dialog box will appear.</span></span> <span data-ttu-id="e54bf-250">选择 **“数据透视表”**，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="e54bf-250">Choose **PivotTable Report**, and then click **Ok**.</span></span>  
  
14. <span data-ttu-id="e54bf-251">数据透视表字段列表将出现在工作簿中。</span><span class="sxs-lookup"><span data-stu-id="e54bf-251">A PivotTable Field List appears in the workbook.</span></span>   
    <span data-ttu-id="e54bf-252">在该字段列表上，单击 **“全部”** 选项卡</span><span class="sxs-lookup"><span data-stu-id="e54bf-252">On the field list, click the **All** tab</span></span>  
  
15. <span data-ttu-id="e54bf-253">向该字段列表的行、列和值区域添加字段。</span><span class="sxs-lookup"><span data-stu-id="e54bf-253">Add fields to the Row, Columns, and Value areas in the field list.</span></span>  
  
16. <span data-ttu-id="e54bf-254">将切片器或筛选器添加到数据透视表。</span><span class="sxs-lookup"><span data-stu-id="e54bf-254">Add a slicer or a filter to the PivotTable.</span></span> <span data-ttu-id="e54bf-255">**不要跳过此步骤**。</span><span class="sxs-lookup"><span data-stu-id="e54bf-255">**Do not skip this step**.</span></span> <span data-ttu-id="e54bf-256">切片器或筛选器是将帮助您验证 Analysis Services 安装的元素。</span><span class="sxs-lookup"><span data-stu-id="e54bf-256">A slicer or filter is the element that will help you verify your Analysis Services installation.</span></span>  
  
17. <span data-ttu-id="e54bf-257">将工作簿保存到已配置 Excel Services 的 SharePoint Server 2013 上的文档库中。</span><span class="sxs-lookup"><span data-stu-id="e54bf-257">Save the workbook to a document library on a SharePoint Server 2013 that has Excel Services configured.</span></span> <span data-ttu-id="e54bf-258">您还可将工作簿保存到文件共享，然后将其上载到 SharePoint Server 2013 文档库。</span><span class="sxs-lookup"><span data-stu-id="e54bf-258">You can also save the workbook to a file share and then upload it to the SharePoint Server 2013 document library.</span></span>  
  
18. <span data-ttu-id="e54bf-259">单击工作簿的名称以在 SharePoint 中查看它，单击切片器或更改之前添加的筛选器。</span><span class="sxs-lookup"><span data-stu-id="e54bf-259">Click the name of your workbook to view it in SharePoint and click the slicer or change the filter that you previously added.</span></span> <span data-ttu-id="e54bf-260">如果出现数据更新，则您将知道 Analysis Services 已安装并且可用于 Excel Services。</span><span class="sxs-lookup"><span data-stu-id="e54bf-260">If a data update occurs, you know that Analysis Services is installed and available to Excel Services.</span></span> <span data-ttu-id="e54bf-261">如果在 Excel 中打开工作簿，您将使用缓存副本，而不使用 Analysis Services 服务器。</span><span class="sxs-lookup"><span data-stu-id="e54bf-261">If you open the workbook in Excel you will be using a cached copy and not using the Analysis Services server.</span></span>  
  
##  <a name="configure-the-windows-firewall-to-allow-analysis-services-access"></a><a name="bkmk_firewall"></a><span data-ttu-id="e54bf-262">将 Windows 防火墙配置为允许 Analysis Services 访问</span><span class="sxs-lookup"><span data-stu-id="e54bf-262">Configure the Windows Firewall to Allow Analysis Services Access</span></span>  
 <span data-ttu-id="e54bf-263">使用主题 [Configure the Windows Firewall to Allow Analysis Services Access](../configure-the-windows-firewall-to-allow-analysis-services-access.md) 中的信息可以确定您是否需要在防火墙中取消阻止端口，以便允许对 Analysis Services 或 PowerPivot for SharePoint 的访问。</span><span class="sxs-lookup"><span data-stu-id="e54bf-263">Use the information in the topic [Configure the Windows Firewall to Allow Analysis Services Access](../configure-the-windows-firewall-to-allow-analysis-services-access.md) to determine whether you need to unblock ports in a firewall to allow access to Analysis Services or PowerPivot for SharePoint.</span></span> <span data-ttu-id="e54bf-264">您可以采用本主题中提供的步骤来配置端口和防火墙设置。</span><span class="sxs-lookup"><span data-stu-id="e54bf-264">You can follow the steps provided in the topic to configure both port and firewall settings.</span></span> <span data-ttu-id="e54bf-265">实际上，您应该一起执行这些步骤以便能够访问您的 Analysis Services 服务器。</span><span class="sxs-lookup"><span data-stu-id="e54bf-265">In practice, you should perform these steps together to allow access to your Analysis Services server.</span></span>  
  
##  <a name="upgrade-workbooks-and-scheduled-data-refresh"></a><a name="bkmk_upgrade_workbook"></a><span data-ttu-id="e54bf-266">升级工作簿和计划的数据刷新</span><span class="sxs-lookup"><span data-stu-id="e54bf-266">Upgrade Workbooks and Scheduled Data Refresh</span></span>  
 <span data-ttu-id="e54bf-267">升级在以前版本的 PowerPivot 中创建的工作簿所需的步骤取决于创建了该工作簿的 PowerPivot 的版本。</span><span class="sxs-lookup"><span data-stu-id="e54bf-267">The steps required to upgrade workbooks created in previous versions of PowerPivot depend on what version of PowerPivot created the workbook.</span></span> <span data-ttu-id="e54bf-268">有关详细信息，请参阅 [升级工作簿和计划的数据刷新 (SharePoint 2013)](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013)。</span><span class="sxs-lookup"><span data-stu-id="e54bf-268">For more information, see [Upgrade Workbooks and Scheduled Data Refresh &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013).</span></span>  
  
##  <a name="beyond-the-single-server-installation--powerpivot-for-microsoft-sharepoint"></a><a name="bkmk_multiple_servers"></a><span data-ttu-id="e54bf-269">除单服务器安装之外-PowerPivot for Microsoft SharePoint</span><span class="sxs-lookup"><span data-stu-id="e54bf-269">Beyond the Single-Server Installation -PowerPivot for Microsoft SharePoint</span></span>  
 <span data-ttu-id="e54bf-270">**Web 前端 (WFE)** 或 **中间层**：若要在更大的 SharePoint 场中在 SharePoint 模式下使用 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 服务器，以及将其他 PowerPivot 功能安装到场中，请在每台 SharePoint 服务器上运行安装程序包 **spPowerPivot.msi** 。</span><span class="sxs-lookup"><span data-stu-id="e54bf-270">**Web front-end (WFE)** or **Middle-tier:**: To use an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode in a larger SharePoint farm and to install additional PowerPivot features into the farm, run the installer package **spPowerPivot.msi** on each of the SharePoint servers.</span></span> <span data-ttu-id="e54bf-271">spPowerPivot.msi 安装所需的数据访问接口以及 PowerPivot for SharePoint 2013 配置工具。</span><span class="sxs-lookup"><span data-stu-id="e54bf-271">The spPowerPivot.msi installs required data providers and the PowerPivot for SharePoint 2013 Configuration tool.</span></span>  
  
 <span data-ttu-id="e54bf-272">有关安装和配置中间层的详细信息，请参阅下面的内容：</span><span class="sxs-lookup"><span data-stu-id="e54bf-272">For more information on installing and configuring the middle-tier, see the following:</span></span>  
  
-   [<span data-ttu-id="e54bf-273">在 SharePoint 2013 &#40;安装或卸载 PowerPivot for SharePoint 加载项&#41;</span><span class="sxs-lookup"><span data-stu-id="e54bf-273">Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)  
  
-   <span data-ttu-id="e54bf-274">要下载 .msi，请参阅 [Microsoft SQL Server 2014 PowerPivot for Microsoft SharePoint 2013](https://go.microsoft.com/fwlink/?LinkID=324854)</span><span class="sxs-lookup"><span data-stu-id="e54bf-274">To download the .msi, see [Microsoft SQL Server 2014 PowerPivot for Microsoft SharePoint 2013](https://go.microsoft.com/fwlink/?LinkID=324854)</span></span>  
  
-   [<span data-ttu-id="e54bf-275">&#40;SharePoint 2013&#41;配置 PowerPivot 和部署解决方案</span><span class="sxs-lookup"><span data-stu-id="e54bf-275">Configure PowerPivot and Deploy Solutions &#40;SharePoint 2013&#41;</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013)  
  
 <span data-ttu-id="e54bf-276">**冗余性和服务器负荷：** 在 SharePoint 模式下安装第二台或更多的 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 服务器将提供 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 服务器功能的冗余性。</span><span class="sxs-lookup"><span data-stu-id="e54bf-276">**Redundancy and server load:** Installing a second, or more [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] servers in SharePoint mode will provide redundancy of the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server functionality.</span></span> <span data-ttu-id="e54bf-277">附加的服务器还将在各服务器上分散负荷。</span><span class="sxs-lookup"><span data-stu-id="e54bf-277">Additional servers will also spread the load across servers.</span></span> <span data-ttu-id="e54bf-278">有关详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="e54bf-278">For more information, see the following:</span></span>  
  
-   <span data-ttu-id="e54bf-279">[配置 Analysis Services 以便在 Excel Services (中处理数据模型](https://technet.microsoft.com/library/jj614437\(v=office.15\)) https://technet.microsoft.com/library/jj614437(v=office.15)) 。</span><span class="sxs-lookup"><span data-stu-id="e54bf-279">[Configure Analysis Services for processing data models in Excel Services](https://technet.microsoft.com/library/jj614437\(v=office.15\)) (https://technet.microsoft.com/library/jj614437(v=office.15)).</span></span>  
  
-   <span data-ttu-id="e54bf-280">[ (SharePoint Server 2013)  (管理 Excel Services 数据模型设置](https://technet.microsoft.com/library/jj219780\(v=office.15\)) https://technet.microsoft.com/library/jj219780(v=office.15)) 。</span><span class="sxs-lookup"><span data-stu-id="e54bf-280">[Manage Excel Services data model settings (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780\(v=office.15\)) (https://technet.microsoft.com/library/jj219780(v=office.15)).</span></span>  
  
 <span data-ttu-id="e54bf-281">![SharePoint 设置](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint 设置")[通过 Microsoft SQL Server 连接 (来提交反馈和联系信息](https://connect.microsoft.com/SQLServer/Feedback) https://connect.microsoft.com/SQLServer/Feedback) 。</span><span class="sxs-lookup"><span data-stu-id="e54bf-281">![SharePoint Settings](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint Settings") [Submit feedback and contact information through Microsoft SQL Server Connect](https://connect.microsoft.com/SQLServer/Feedback) (https://connect.microsoft.com/SQLServer/Feedback).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e54bf-282">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e54bf-282">See Also</span></span>  
 <span data-ttu-id="e54bf-283">[将 PowerPivot 迁移到 SharePoint 2013](https://docs.microsoft.com/analysis-services/instances/install-windows/migrate-power-pivot-to-sharepoint-2013) </span><span class="sxs-lookup"><span data-stu-id="e54bf-283">[Migrate PowerPivot to SharePoint 2013](https://docs.microsoft.com/analysis-services/instances/install-windows/migrate-power-pivot-to-sharepoint-2013) </span></span>  
 <span data-ttu-id="e54bf-284">[在 SharePoint 2013 &#40;安装或卸载 PowerPivot for SharePoint 加载项&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) </span><span class="sxs-lookup"><span data-stu-id="e54bf-284">[Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) </span></span>  
 [<span data-ttu-id="e54bf-285">&#40;SharePoint 2013&#41;升级工作簿和计划的数据刷新</span><span class="sxs-lookup"><span data-stu-id="e54bf-285">Upgrade Workbooks and Scheduled Data Refresh &#40;SharePoint 2013&#41;</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013)  
  
  
