---
title: 验证 Reporting Services 安装 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- checking report server installations
- verifying report server installations
- Report Designer [Reporting Services], verifying installations
- installing Reporting Services, verifying installations
- Report Manager [Reporting Services], verifying installations
- report servers [Reporting Services], verifying installations
- Setup [Reporting Services], verifying installations
ms.assetid: 82a51a99-66f0-4b0c-b05b-07d22387adb0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5b90f997f99cfc9d3f8625eb4e08d193af52d7f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577378"
---
# <a name="verify-a-reporting-services-installation"></a><span data-ttu-id="78192-102">Verify a Reporting Services Installation</span><span class="sxs-lookup"><span data-stu-id="78192-102">Verify a Reporting Services Installation</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="78192-103">报表服务器。</span><span class="sxs-lookup"><span data-stu-id="78192-103">report servers can be installed in one of two modes, Native or SharePoint.</span></span> <span data-ttu-id="78192-104">验证安装时应遵循的步骤取决于报表服务器的模式。</span><span class="sxs-lookup"><span data-stu-id="78192-104">The steps you should follow for verifying the installation depend on the report server mode.</span></span>  
  
 <span data-ttu-id="78192-105">本主题包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="78192-105">This topic contains the following information:</span></span>  
  
-   [<span data-ttu-id="78192-106">验证 SharePoint 模式安装</span><span class="sxs-lookup"><span data-stu-id="78192-106">Verify SharePoint Mode Installation</span></span>](#bkmk_sharepointmode)  
  
-   [<span data-ttu-id="78192-107">验证本机模式安装</span><span class="sxs-lookup"><span data-stu-id="78192-107">Verify a Native Mode Installation</span></span>](#bkmk_nativemode)  
  
##  <a name="verify-sharepoint-mode-installation"></a><a name="bkmk_sharepointmode"></a> <span data-ttu-id="78192-108">验证 SharePoint 模式安装</span><span class="sxs-lookup"><span data-stu-id="78192-108">Verify SharePoint Mode Installation</span></span>  
  
#### <a name="to-verify-the-reporting-services-service"></a><span data-ttu-id="78192-109">验证 Reporting Services 服务</span><span class="sxs-lookup"><span data-stu-id="78192-109">To verify the Reporting Services Service</span></span>  
  
1.  <span data-ttu-id="78192-110">在 SharePoint 管理中心中，单击 **“系统设置”** 组中的 **“管理服务器上的服务”** 。</span><span class="sxs-lookup"><span data-stu-id="78192-110">From SharePoint central administration, click **Manage services on server** in the **System Settings** group.</span></span>  
  
2.  <span data-ttu-id="78192-111">验证是否已经安装了 **“SQL Server Reporting Services 服务”** 且该服务处于 **“运行”** 状态。</span><span class="sxs-lookup"><span data-stu-id="78192-111">Verify the **SQL Server Reporting Services Service** is installed and in the **Running** state.</span></span>  
  
     <span data-ttu-id="78192-112">如果您在列表中看不到 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务，则验证是否已安装该服务。</span><span class="sxs-lookup"><span data-stu-id="78192-112">If you do not see the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service in the list, verify the service is installed.</span></span> <span data-ttu-id="78192-113">有关详细信息，请参阅[安装用于 sharepoint 2010 Reporting Services Sharepoint 模式](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)的 "安装并启动 Reporting Services sharepoint 服务" 部分。</span><span class="sxs-lookup"><span data-stu-id="78192-113">For more information, see the "Install and start the Reporting Services SharePoint Service" section of [Install Reporting Services SharePoint Mode for SharePoint 2010](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).</span></span>  
  
#### <a name="to-verify-the-service-application"></a><span data-ttu-id="78192-114">验证服务应用程序</span><span class="sxs-lookup"><span data-stu-id="78192-114">To verify the Service Application</span></span>  
  
1.  <span data-ttu-id="78192-115">若要验证您在管理中心中至少有一种 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序，请单击 **“应用程序管理”** 组中的 **“管理服务应用程序”** 。</span><span class="sxs-lookup"><span data-stu-id="78192-115">To verify from Central Administration you have at least one [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application, click **Manage Service Applications** in the **Application Management** group.</span></span>  
  
2.  <span data-ttu-id="78192-116">验证是否有 **“SQL Server Reporting Services 服务应用程序”** 类型的服务应用程序和相应的应用程序代理。</span><span class="sxs-lookup"><span data-stu-id="78192-116">Verify there is a service application of type **SQL Server Reporting Services Service Application** and a corresponding application proxy.</span></span>  
  
3.  <span data-ttu-id="78192-117">单击服务应用程序名称 **旁边** ，然后单击 SharePoint 工具栏中的 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="78192-117">Click **near** the name of the service application and then click **Properties** in the SharePoint toolbar.</span></span>  <span data-ttu-id="78192-118">如果单击服务应用程序的名称，将打开服务应用程序的“管理”页，而非属性页。</span><span class="sxs-lookup"><span data-stu-id="78192-118">If you click the name of the service application it will open the Management pages of the service application, not the properties page.</span></span>  
  
4.  <span data-ttu-id="78192-119">验证是否将 **“Web 应用程序关联”** 配置为指向所需的 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="78192-119">Verify the **Web Application Association** is configured to point to the desired web application.</span></span>  
  
#### <a name="to-verify-the-site-collection-feature"></a><span data-ttu-id="78192-120">验证网站集功能</span><span class="sxs-lookup"><span data-stu-id="78192-120">To verify the Site collection Feature</span></span>  
  
1.  <span data-ttu-id="78192-121">在网站设置中，单击 **“网站集管理”** 组中的 **“网站集功能”** 。</span><span class="sxs-lookup"><span data-stu-id="78192-121">In site settings, click **Site collection Features** in the **Site Collection Administration** group.</span></span>  
  
2.  <span data-ttu-id="78192-122">验证是否激活了 **“报表服务器集成功能”** 。</span><span class="sxs-lookup"><span data-stu-id="78192-122">Verify the **Report Server Integration Feature** is active.</span></span>  
  
#### <a name="to-verify-reporting-server-content-types"></a><span data-ttu-id="78192-123">验证报表服务器内容类型</span><span class="sxs-lookup"><span data-stu-id="78192-123">To Verify Reporting Server content types</span></span>  
  
1.  <span data-ttu-id="78192-124">若要验证或添加 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Report Server 内容类型，请参阅[将报表服务器内容类型添加到 Reporting Services SharePoint 集成模式下的库 &#40;&#41;](../add-reporting-services-content-types-to-a-sharepoint-library.md)。</span><span class="sxs-lookup"><span data-stu-id="78192-124">To verify or add [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server content types, see [Add Report Server Content Types to a Library &#40;Reporting Services in SharePoint Integrated Mode&#41;](../add-reporting-services-content-types-to-a-sharepoint-library.md).</span></span>  
  
#### <a name="to-verify-you-can-launch-report-builder"></a><span data-ttu-id="78192-125">验证是否可以启动报表生成器</span><span class="sxs-lookup"><span data-stu-id="78192-125">To verify you can launch Report Builder</span></span>  
  
1.  <span data-ttu-id="78192-126">从文档库中，单击 SharePoint 功能区中的 **“文档”** 。</span><span class="sxs-lookup"><span data-stu-id="78192-126">From a document library, click **Documents** in the SharePoint ribbon.</span></span>  
  
2.  <span data-ttu-id="78192-127">单击 **“新建文档”** ，然后单击 **“报表生成器报表”**。</span><span class="sxs-lookup"><span data-stu-id="78192-127">Click **New Document** and click **Report Builder Report**.</span></span> <span data-ttu-id="78192-128">如果看不到此选项，请回顾以前向库中添加报表服务器内容类型的过程。</span><span class="sxs-lookup"><span data-stu-id="78192-128">If you do not see this option, review the previous procedure on adding the report server content types to a library.</span></span>  
  
#### <a name="create-a-basic-report"></a><span data-ttu-id="78192-129">创建基本报表</span><span class="sxs-lookup"><span data-stu-id="78192-129">Create a basic report</span></span>  
  
1.  <span data-ttu-id="78192-130">在 SharePoint 文档库中，创建一个仅包含文本框的基本 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表，例如标题。</span><span class="sxs-lookup"><span data-stu-id="78192-130">In a SharePoint document library, create a basic [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report that only contains a text box, for example a title.</span></span> <span data-ttu-id="78192-131">该报表不包含任何数据源或数据集。</span><span class="sxs-lookup"><span data-stu-id="78192-131">The report does not contain any data sources or datasets.</span></span> <span data-ttu-id="78192-132">目的是验证能否打开报表生成器和预览基本报表。</span><span class="sxs-lookup"><span data-stu-id="78192-132">The goal is to verify you can open Report Builder and a basic report will preview.</span></span>  
  
2.  <span data-ttu-id="78192-133">将报表保存到文档库并从库中运行该报表。</span><span class="sxs-lookup"><span data-stu-id="78192-133">Save the report to the document library and the run the report from the library.</span></span> <span data-ttu-id="78192-134">有关使用报表生成器创建报表的详细信息，请参阅 [启动报表生成器（报表生成器）](https://technet.microsoft.com/library/ms159221.aspx)。</span><span class="sxs-lookup"><span data-stu-id="78192-134">For more information on creating reports with Report Builder, see [Start Report Builder (Report Builder)](https://technet.microsoft.com/library/ms159221.aspx).</span></span>  
  
#### <a name="reporting-services-samples"></a><span data-ttu-id="78192-135">Reporting Services 示例</span><span class="sxs-lookup"><span data-stu-id="78192-135">Reporting Services samples</span></span>  
  
1.  <span data-ttu-id="78192-136">完成 Reporting Services 教程之一。</span><span class="sxs-lookup"><span data-stu-id="78192-136">Complete one of the Reporting Services tutorials.</span></span> <span data-ttu-id="78192-137">有关详细信息，请参阅 [Reporting Services 教程 (SSRS)](../reporting-services-tutorials-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="78192-137">For more information, see [Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="78192-138">从 CodePlex 下载 Adventure Works 示例数据库和 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 示例报告。</span><span class="sxs-lookup"><span data-stu-id="78192-138">Download the Adventure works sample database and the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sample reports from CodePlex.</span></span> <span data-ttu-id="78192-139">有关详细信息，请参阅 [AdventureWorks 报表示例](https://msftrsprodsamples.codeplex.com/wikipage?title=SS2012!AdventureWorks2012%20Report%20Samples&referringTitle=Home)。</span><span class="sxs-lookup"><span data-stu-id="78192-139">For more information, see [AdventureWorks Report Samples](https://msftrsprodsamples.codeplex.com/wikipage?title=SS2012!AdventureWorks2012%20Report%20Samples&referringTitle=Home).</span></span>  
  
##  <a name="verify-a-native-mode-installation"></a><a name="bkmk_nativemode"></a> <span data-ttu-id="78192-140">验证本机模式安装</span><span class="sxs-lookup"><span data-stu-id="78192-140">Verify a Native Mode Installation</span></span>  
 <span data-ttu-id="78192-141">如果使用默认配置安装本机模式的报表服务器，安装程序将安装并部署该服务器。</span><span class="sxs-lookup"><span data-stu-id="78192-141">When you install a Native mode report server using the default configuration, Setup installs and deploys the server.</span></span> <span data-ttu-id="78192-142">可以执行几个简单的测试来验证安装程序是否部署了报表服务器。</span><span class="sxs-lookup"><span data-stu-id="78192-142">You can verify whether Setup deployed the report server by performing a few simple tests.</span></span> <span data-ttu-id="78192-143">只有本地管理员才能执行这些步骤。</span><span class="sxs-lookup"><span data-stu-id="78192-143">You must be a local administrator to perform these steps.</span></span> <span data-ttu-id="78192-144">若要让其他用户执行测试，必须为这些用户配置报表服务器访问权限。</span><span class="sxs-lookup"><span data-stu-id="78192-144">To enable other users to perform testing, you must configure report server access for those users.</span></span>  
  
#### <a name="to-verify-that-the-report-server-is-installed-and-running"></a><span data-ttu-id="78192-145">验证报表服务器已安装并正常运行</span><span class="sxs-lookup"><span data-stu-id="78192-145">To verify that the report server is installed and running</span></span>  
  
1.  <span data-ttu-id="78192-146">运行 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置工具，然后连接到您刚安装的报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="78192-146">Run the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and connect to the report server instance you just installed.</span></span> <span data-ttu-id="78192-147">“Web 服务 URL”页包括指向报表服务器 Web 服务的链接。</span><span class="sxs-lookup"><span data-stu-id="78192-147">The Web Service URL page includes a link to the Report Server Web service.</span></span> <span data-ttu-id="78192-148">单击该链接可验证您是否可以访问该服务器。</span><span class="sxs-lookup"><span data-stu-id="78192-148">Click the link to verify you can access the server.</span></span> <span data-ttu-id="78192-149">如果未配置报表服务器数据库，请先进行配置，再单击该链接。</span><span class="sxs-lookup"><span data-stu-id="78192-149">If the report server database is not configured, do that first before clicking the link.</span></span>  
  
2.  <span data-ttu-id="78192-150">打开“服务”控制台应用程序并验证报表服务器服务是否正在运行。</span><span class="sxs-lookup"><span data-stu-id="78192-150">Open the Services console applications and verify that the Report Server service is running.</span></span> <span data-ttu-id="78192-151">若要查看报表服务器服务的状态，请单击“开始”，指向“控制面板”，双击“管理工具”，再双击“服务”\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="78192-151">To view the status of the Report Server service, click **Start**, point to **Control Panel**, double-click **Administrative Tools**, and then double-click **Services**.</span></span> <span data-ttu-id="78192-152">出现服务列表后，滚动到“报表服务器 (MSSQLSERVER)”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="78192-152">When the list of services appears, scroll to **Report Server (MSSQLSERVER)**.</span></span> <span data-ttu-id="78192-153">该服务的状态应为 **“已启动”**。</span><span class="sxs-lookup"><span data-stu-id="78192-153">The status should be **Started**.</span></span>  
  
3.  <span data-ttu-id="78192-154">打开浏览器，在地址栏中键入报表服务器的 URL。</span><span class="sxs-lookup"><span data-stu-id="78192-154">Open a browser and type the report server URL in the address bar.</span></span> <span data-ttu-id="78192-155">该地址由安装过程中为报表服务器指定的服务器名称和虚拟目录名组成。</span><span class="sxs-lookup"><span data-stu-id="78192-155">The address consists of the server name and the virtual directory name that you specified for the report server during setup.</span></span> <span data-ttu-id="78192-156">默认情况下，报表服务器虚拟目录的名称为 **ReportServer**。</span><span class="sxs-lookup"><span data-stu-id="78192-156">By default, the report server virtual directory is named **ReportServer**.</span></span> <span data-ttu-id="78192-157">你可以使用以下 URL 来验证 Report Server 安装： http:// *\<computer name>* /ReportServer *\<_instance name>* 。</span><span class="sxs-lookup"><span data-stu-id="78192-157">You can use the following URL to verify report server installation: http://*\<computer name>*/ReportServer*\<_instance name>*.</span></span> <span data-ttu-id="78192-158">如果将报表服务器安装为命名实例，URL 将有所不同。</span><span class="sxs-lookup"><span data-stu-id="78192-158">The URL will be different if you installed the report server as a named instance.</span></span> <span data-ttu-id="78192-159">有关 URL 格式的详细信息，请参阅[配置报表服务器 URL（SSRS 配置管理器）](configure-report-server-urls-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="78192-159">For more information about the URL format, see [Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](configure-report-server-urls-ssrs-configuration-manager.md).</span></span> <span data-ttu-id="78192-160">如果你在 Windows Vista 或 Windows Server 2008 上是本地管理员，请参阅[为本地管理配置本机模式报表服务器 (SSRS)](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="78192-160">If you are a local administrator on Windows Vista or Windows Server 2008, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
4.  <span data-ttu-id="78192-161">运行报表以测试报表服务器的操作。</span><span class="sxs-lookup"><span data-stu-id="78192-161">Run reports to test report server operations.</span></span> <span data-ttu-id="78192-162">对于此步骤，您可以从教程创建一个示例报表。</span><span class="sxs-lookup"><span data-stu-id="78192-162">For this step, you can create a sample report from a tutorial.</span></span> <span data-ttu-id="78192-163">有关详细信息，请参阅[创建基本表报表（SSRS 教程）](../create-a-basic-table-report-ssrs-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="78192-163">For more information, see [Create a Basic Table Report &#40;SSRS Tutorial&#41;](../create-a-basic-table-report-ssrs-tutorial.md).</span></span>  
  
#### <a name="to-verify-that-report-manager-is-installed-and-running"></a><span data-ttu-id="78192-164">验证报表管理器已安装并正常运行</span><span class="sxs-lookup"><span data-stu-id="78192-164">To verify that Report Manager is installed and running</span></span>  
  
1.  <span data-ttu-id="78192-165">打开浏览器，在地址栏中键入报表服务器的 URL。</span><span class="sxs-lookup"><span data-stu-id="78192-165">Open a browser and type the Report Manager URL in the address bar.</span></span> <span data-ttu-id="78192-166">该地址由您在安装过程中或在 Reporting Services 配置工具的“报表管理器 URL”页中为报表管理器指定的服务器名称和虚拟目录名称组成。</span><span class="sxs-lookup"><span data-stu-id="78192-166">The address consists of the server name and the virtual directory name that you specified for the Report Manager during setup or in the Report Manager URL page in the Reporting Services Configuration tool.</span></span> <span data-ttu-id="78192-167">默认情况下，报表管理器虚拟目录的名称为 **Reports**。</span><span class="sxs-lookup"><span data-stu-id="78192-167">By default, the Report Manager virtual directory is **Reports**.</span></span> <span data-ttu-id="78192-168">可以使用以下 URL 验证报表管理器安装：</span><span class="sxs-lookup"><span data-stu-id="78192-168">You can use the following URL to verify Report Manager installation:</span></span>  
  
     <span data-ttu-id="78192-169">http:// *\<computer name>* /Reports *\<_instance name>* 。</span><span class="sxs-lookup"><span data-stu-id="78192-169">http://*\<computer name>*/Reports*\<_instance name>*.</span></span>  
  
2.  <span data-ttu-id="78192-170">使用报表管理器创建新文件夹或上载文件，以测试定义是否传回报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="78192-170">Use Report Manager to create a new folder or upload a file to test whether definitions are passed back to the report server database.</span></span> <span data-ttu-id="78192-171">如果上述操作成功，则表明连接正常。</span><span class="sxs-lookup"><span data-stu-id="78192-171">If these operations are successful, the connection is functional.</span></span>  
  
     <span data-ttu-id="78192-172">有关详细信息，请参阅[报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="78192-172">For more information, see [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
#### <a name="to-verify-that-report-designer-is-installed-and-running"></a><span data-ttu-id="78192-173">验证报表设计器已安装并正常运行</span><span class="sxs-lookup"><span data-stu-id="78192-173">To verify that Report Designer is installed and running</span></span>  
  
1.  <span data-ttu-id="78192-174">打开 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]，然后创建基于报表服务器项目类型的新项目。</span><span class="sxs-lookup"><span data-stu-id="78192-174">Open [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], and create a new project based on a Report Server project type.</span></span> <span data-ttu-id="78192-175">有关使用报表服务器项目向导的详细信息，请参阅 SQL Server 联机丛书中的 [SQL Server Data Tools 中的 Reporting Services (SSDT)](../tools/reporting-services-in-sql-server-data-tools-ssdt.md)。</span><span class="sxs-lookup"><span data-stu-id="78192-175">For more information on using the Report Server Project Wizard, see [Reporting Services in SQL Server Data Tools &#40;SSDT&#41;](../tools/reporting-services-in-sql-server-data-tools-ssdt.md) in SQL Server Books Online.</span></span>  
  
2.  <span data-ttu-id="78192-176">如果安装了报表示例，请打开示例报表项目文件并将报表发布到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="78192-176">If you installed report samples, open the sample report project files and publish the reports to a report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78192-177">另请参阅</span><span class="sxs-lookup"><span data-stu-id="78192-177">See Also</span></span>  
 <span data-ttu-id="78192-178">[排查 Reporting Services 安装问题](troubleshoot-a-reporting-services-installation.md) </span><span class="sxs-lookup"><span data-stu-id="78192-178">[Troubleshoot a Reporting Services Installation](troubleshoot-a-reporting-services-installation.md) </span></span>  
 [<span data-ttu-id="78192-179">Reporting Services 错误的原因和解决方法</span><span class="sxs-lookup"><span data-stu-id="78192-179">Cause and Resolution of Reporting Services Errors</span></span>](../troubleshooting/cause-and-resolution-of-reporting-services-errors.md)  
  
  
