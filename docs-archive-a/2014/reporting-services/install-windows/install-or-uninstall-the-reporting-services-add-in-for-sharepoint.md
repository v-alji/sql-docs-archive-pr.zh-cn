---
title: 安装或卸载用于 SharePoint (SharePoint 2010 和 SharePoint 2013) 的 Reporting Services 外接程序 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c2804a9a-08ea-4f4a-805d-a2c19c68733d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e30014ec823e89172b36f35d7f313568432a26f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588336"
---
# <a name="install-or-uninstall-the-reporting-services-add-in-for-sharepoint-sharepoint-2010-and-sharepoint-2013"></a><span data-ttu-id="a9537-102">安装或卸载用于 SharePoint 的 Reporting Services 外接程序（SharePoint 2010 和 SharePoint 2013）</span><span class="sxs-lookup"><span data-stu-id="a9537-102">Install or Uninstall the Reporting Services Add-in for SharePoint (SharePoint 2010 and SharePoint 2013)</span></span>
  <span data-ttu-id="a9537-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 在 sharepoint 服务器上运行用于 sharepoint 产品的安装包外接程序 ( # A0) ，以在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sharepoint 部署中启用功能。</span><span class="sxs-lookup"><span data-stu-id="a9537-103">Run the installation package [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in for SharePoint products (rsSharePoint.msi) on SharePoint servers to enable [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features within a SharePoint deployment.</span></span> <span data-ttu-id="a9537-104">这些功能包括 Power View、一个报表查看器 Web 部件、一个 URL 代理端点、一些内容类型和一些应用程序页，使用它们可以创建、查看及管理 SharePoint 站点上的报表、报表模型、数据源和其他报表服务器内容。</span><span class="sxs-lookup"><span data-stu-id="a9537-104">Features include Power View, a Report Viewer Web Part, a URL proxy endpoint, content types, and application pages so that you can create, view, and manage reports, report models, data sources and other report server content on a SharePoint site.</span></span> <span data-ttu-id="a9537-105">用于 SharePoint 产品的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序是在 SharePoint 模式下运行的报表服务器的必需组件。</span><span class="sxs-lookup"><span data-stu-id="a9537-105">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in for SharePoint products is a required component for a report server that runs in SharePoint mode.</span></span> <span data-ttu-id="a9537-106">可以从 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安装向导或通过从 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 功能包下载 rsSharePoint.msi 来安装此外接程序。</span><span class="sxs-lookup"><span data-stu-id="a9537-106">The add-in can be installed from either the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] setup wizard or by downloading the rsSharePoint.msi from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] feature pack.</span></span> <span data-ttu-id="a9537-107">有关外接程序和下载页的版本列表，请参阅 [在何处查找用于 SharePoint 产品的 Reporting Services 外接程序](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)。</span><span class="sxs-lookup"><span data-stu-id="a9537-107">For a list of the versions of the add-in and download pages, see [Where to find the Reporting Services add-in for SharePoint Products](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).</span></span>

||
|-|
|<span data-ttu-id="a9537-108">**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="a9537-108">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010</span></span>|

 <span data-ttu-id="a9537-109">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="a9537-109">**In this topic:**</span></span>

-   [<span data-ttu-id="a9537-110">先决条件</span><span class="sxs-lookup"><span data-stu-id="a9537-110">Prerequisites</span></span>](#bkmk_prereq)

-   [<span data-ttu-id="a9537-111">外接程序安装执行哪些操作？</span><span class="sxs-lookup"><span data-stu-id="a9537-111">What Does The Add-in Install?</span></span>](#bkmk_whatinstalled)

-   [<span data-ttu-id="a9537-112">安装方法概述</span><span class="sxs-lookup"><span data-stu-id="a9537-112">Overview of the Installation Methods</span></span>](#bkmk_3ways_to_install)

-   [<span data-ttu-id="a9537-113">使用安装文件 rsSharePoint.msi 安装外接程序</span><span class="sxs-lookup"><span data-stu-id="a9537-113">Install the add-in using the installation file rsSharePoint.msi</span></span>](#bkmk_install_rssharepoint)

    -   [<span data-ttu-id="a9537-114">“仅文件”安装</span><span class="sxs-lookup"><span data-stu-id="a9537-114">Files-only installation</span></span>](#bkmk_files_only_installation)

-   [<span data-ttu-id="a9537-115">如何删除 Reporting Services 外接程序</span><span class="sxs-lookup"><span data-stu-id="a9537-115">How to Remove the Reporting Services Add-in</span></span>](#bkmk_remove_addin)

-   [<span data-ttu-id="a9537-116">如何从命令行修复 rssharepoint.msi</span><span class="sxs-lookup"><span data-stu-id="a9537-116">How to Repair rssharepoint.msi from the Command Line</span></span>](#bkmk_repair)

-   [<span data-ttu-id="a9537-117">安装程序日志文件</span><span class="sxs-lookup"><span data-stu-id="a9537-117">Setup Log Files</span></span>](#bkmk_logfiles)

-   [<span data-ttu-id="a9537-118">Upgrade</span><span class="sxs-lookup"><span data-stu-id="a9537-118">Upgrade</span></span>](#bkmk_upgrade)

-   [<span data-ttu-id="a9537-119">rsCustomAction.exe</span><span class="sxs-lookup"><span data-stu-id="a9537-119">RsCustomAction.exe</span></span>](#bkmk_rscustomaction)

##  <a name="prerequisites"></a><a name="bkmk_prereq"></a><span data-ttu-id="a9537-120">先决条件</span><span class="sxs-lookup"><span data-stu-id="a9537-120">Prerequisites</span></span>
 <span data-ttu-id="a9537-121">将报表服务器与 SharePoint 产品的实例集成需要若干步骤，安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序是其中的一步。</span><span class="sxs-lookup"><span data-stu-id="a9537-121">Installing the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in is one of several steps that are necessary for integrating a report server with an instance of a SharePoint product.</span></span> <span data-ttu-id="a9537-122">有关针对使用 SharePoint 模式全套要求的详细信息，请参阅 [Hardware and Software Requirements for Reporting Services in SharePoint Mode](../../../2014/sql-server/install/hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="a9537-122">For more information about the complete set of requirements for using SharePoint mode, see [Hardware and Software Requirements for Reporting Services in SharePoint Mode](../../../2014/sql-server/install/hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode.md).</span></span> <span data-ttu-id="a9537-123">有关安装和配置的详细信息 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，请参阅[Install Reporting Services sharepoint Mode for sharepoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)。</span><span class="sxs-lookup"><span data-stu-id="a9537-123">For more information on installing and configuring [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Install Reporting Services SharePoint Mode for SharePoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md).</span></span>

-   <span data-ttu-id="a9537-124">如果将 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 与具有多个 Web 前端应用程序的 SharePoint 场集成，则将该外接程序安装到场中每台具有 Web 服务器前端的计算机上。</span><span class="sxs-lookup"><span data-stu-id="a9537-124">If you are integrating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] with a SharePoint farm that has multiple Web front end applications, install the add-in to each computer in the farm that has a Web server front-end.</span></span> <span data-ttu-id="a9537-125">仅对将要用于访问报表服务器内容的 Web 前端执行此操作。</span><span class="sxs-lookup"><span data-stu-id="a9537-125">Do this only for Web front ends that will be used to access report server content.</span></span>

-   <span data-ttu-id="a9537-126">若要安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序，您必须是计算机上的管理员。</span><span class="sxs-lookup"><span data-stu-id="a9537-126">To install the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in, you must be an administrator on the computer.</span></span> <span data-ttu-id="a9537-127">例如，如果要在命令提示符下运行 rsSharePoint.msi，应使用“以管理员身份运行” \*\*\*\* 选项用管理员权限打开命令提示符。</span><span class="sxs-lookup"><span data-stu-id="a9537-127">For example if you are going to run the rsSharePoint.msi at the command prompt, you should open the command prompt with administrator privileges by using the **Run as administrator** option.</span></span>

-   <span data-ttu-id="a9537-128">若要安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序，您必须是 SharePoint 场 Administrators 组的成员。</span><span class="sxs-lookup"><span data-stu-id="a9537-128">To install the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in, you must be a member of the SharePoint Farm Administrators group.</span></span>

-   <span data-ttu-id="a9537-129">您必须是网站集管理员才能激活 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 集成功能。</span><span class="sxs-lookup"><span data-stu-id="a9537-129">You must be a Site Collection administrator to activate the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] integration feature.</span></span>

-   <span data-ttu-id="a9537-130">有关包含外接程序的示例部署的关系图，请参阅[SharePoint 中 SQL SERVER BI 功能的部署拓扑](../../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="a9537-130">For diagrams of example deployments with the add-in, see [Deployment Topologies for SQL Server BI Features in SharePoint](../../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md).</span></span>

##  <a name="what-does-the-add-in-install"></a><a name="bkmk_whatinstalled"></a><span data-ttu-id="a9537-131">外接程序的安装内容是什么？</span><span class="sxs-lookup"><span data-stu-id="a9537-131">What Does The Add-in Install?</span></span>
 <span data-ttu-id="a9537-132">外接程序安装过程由两个阶段组成，完成标准安装时将自动完成这两个阶段：</span><span class="sxs-lookup"><span data-stu-id="a9537-132">The add-in setup process is composed of two phases, both are completed automatically when you complete a standard installation:</span></span>

-   <span data-ttu-id="a9537-133">第一个阶段是将文件安装到适当的文件夹。</span><span class="sxs-lookup"><span data-stu-id="a9537-133">The first phase is to install files to the proper folders.</span></span> <span data-ttu-id="a9537-134">这些文件夹是 SharePoint 部署的标准文件夹。</span><span class="sxs-lookup"><span data-stu-id="a9537-134">The folders are standard for SharePoint deployments.</span></span> <span data-ttu-id="a9537-135">要安装的文件之一是 rsCustomAction.exe。</span><span class="sxs-lookup"><span data-stu-id="a9537-135">One of the files that is installed is rsCustomAction.exe.</span></span>

-   <span data-ttu-id="a9537-136">安装的第二个阶段是运行一组自定义操作以便向 SharePoint 注册 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 文件。</span><span class="sxs-lookup"><span data-stu-id="a9537-136">The second portion of the installation is to run a set of custom actions to register the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] files with SharePoint.</span></span> <span data-ttu-id="a9537-137">从 rsCustomAction.exe 运行这些自定义操作。</span><span class="sxs-lookup"><span data-stu-id="a9537-137">The custom actions are run from rsCustomAction.exe.</span></span> <span data-ttu-id="a9537-138">在整个两个安装阶段都完成后，该 exe 将被删除。</span><span class="sxs-lookup"><span data-stu-id="a9537-138">The exe is removed when the full two phase installation completes.</span></span> <span data-ttu-id="a9537-139">您可以运行“仅文件” \*\*\*\* 安装，在安装结束时不运行 rsCustomAction.exe 并且该文件将保留在驱动器上。</span><span class="sxs-lookup"><span data-stu-id="a9537-139">You can run a **files only** installation and rsCustomAction.exe is not run at the end of installation and it is left on the drive.</span></span>

## <a name="the-reporting-services-installation-order"></a><span data-ttu-id="a9537-140">Reporting Services 安装顺序</span><span class="sxs-lookup"><span data-stu-id="a9537-140">The Reporting Services Installation order</span></span>
 <span data-ttu-id="a9537-141">外接程序可在安装 SharePoint 之前安装，也可在安装 SharePoint 之后安装。</span><span class="sxs-lookup"><span data-stu-id="a9537-141">The add-in can be installed before installing SharePoint or after SharePoint installation.</span></span> <span data-ttu-id="a9537-142">此外接程序遵循 SharePoint 预部署标准，将文件安装到 SharePoint 安装所用的位置中。</span><span class="sxs-lookup"><span data-stu-id="a9537-142">The add-in follows SharePoint pre-deployment standards and installs files in locations used by the SharePoint installation.</span></span>

> [!NOTE]
>  <span data-ttu-id="a9537-143">在安装 SharePoint 产品之前安装外接程序的好处是：当新的服务器添加到场后，SharePoint 场会配置并激活 Reporting Services 外接程序。</span><span class="sxs-lookup"><span data-stu-id="a9537-143">The advantage of installing the add-in prior to the SharePoint product is that as new servers are added to the farm, the Reporting Services Add-in will be configured and activated by the SharePoint farm.</span></span>

 <span data-ttu-id="a9537-144">**SharePoint 2010**</span><span class="sxs-lookup"><span data-stu-id="a9537-144">**SharePoint 2010**</span></span>

-   <span data-ttu-id="a9537-145">SharePoint 2010 产品准备工具安装 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 外接程序的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="a9537-145">The SharePoint 2010 Products Preparation tool installs the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] version of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in.</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="a9537-146">包括 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 功能所需的外接程序的新版本。</span><span class="sxs-lookup"><span data-stu-id="a9537-146">includes a new version of the add-in that is required for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] features.</span></span>

     <span data-ttu-id="a9537-147">如果您运行 SharePoint 产品准备工具，仍需要安装 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 外接程序的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="a9537-147">If you run the SharePoint Products Preparation Tool, you still need to install the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in.</span></span>

-   <span data-ttu-id="a9537-148">如果您是第一次安装 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 外接程序的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 版本，则在运行 SharePoint 产品准备工具时，将会看到以下对话框，指示该准备工具未安装该外接程序的较旧版本，因为已检测到了较新版本。</span><span class="sxs-lookup"><span data-stu-id="a9537-148">If you install [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in first, then when you run the SharePoint Products preparation tool you will see the following dialog indicating the preparation tool did not install the older version of the add-in as the newer version was detected.</span></span> <span data-ttu-id="a9537-149">这是预期行为</span><span class="sxs-lookup"><span data-stu-id="a9537-149">This is expected behavior</span></span>

     <span data-ttu-id="a9537-150">![SSRS 外接程序已安装。](../../../2014/sql-server/install/media/rs-sharepointprereq-complete.gif "SSRS 外接程序已安装。")</span><span class="sxs-lookup"><span data-stu-id="a9537-150">![SSRS add-in is already installed.](../../../2014/sql-server/install/media/rs-sharepointprereq-complete.gif "SSRS add-in is already installed.")</span></span>

 <span data-ttu-id="a9537-151">**SharePoint 2013**</span><span class="sxs-lookup"><span data-stu-id="a9537-151">**SharePoint 2013**</span></span>

 <span data-ttu-id="a9537-152">SharePoint 20103 产品准备**工具不会安装** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 用于 SharePoint 产品的外接程序。</span><span class="sxs-lookup"><span data-stu-id="a9537-152">The SharePoint 20103 Products Preparation tool does **Not** install the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint products.</span></span>

##  <a name="overview-of-the-installation-methods"></a><a name="bkmk_3ways_to_install"></a> <span data-ttu-id="a9537-153">安装方法概述</span><span class="sxs-lookup"><span data-stu-id="a9537-153">Overview of the Installation Methods</span></span>
 <span data-ttu-id="a9537-154">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 使用以下两种方法之一可以安装用于 SharePoint 产品的外接程序：</span><span class="sxs-lookup"><span data-stu-id="a9537-154">The [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in for SharePoint products can be installed using one of the following two methods:</span></span>

-   <span data-ttu-id="a9537-155">**安装向导：** 使用 "新建"![注释](../../../2014/reporting-services/media/rs-fyinote.png "注意") [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，外接程序可以通过 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装向导进行安装。</span><span class="sxs-lookup"><span data-stu-id="a9537-155">**The installation wizard:** ![note](../../../2014/reporting-services/media/rs-fyinote.png "note")New with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the add-in can be installed by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation wizard.</span></span> <span data-ttu-id="a9537-156">在向导的“功能选择”\*\*\*\* 页上，选择“用于 SharePoint 产品的 Reporting Services 外接程序”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a9537-156">Choose **Reporting Services Add-in for SharePoint Products** on the **Feature Selection** page of the wizard.</span></span>

-   <span data-ttu-id="a9537-157">**rsSharepoint.msi：** 外接程序可从安装介质直接安装，也可以通过下载安装。</span><span class="sxs-lookup"><span data-stu-id="a9537-157">**rsSharepoint.msi:** The add-in can be installed directly from the installation media or downloaded and installed.</span></span> <span data-ttu-id="a9537-158">rsSharepoint.msi 同时支持图形用户界面和命令行安装。</span><span class="sxs-lookup"><span data-stu-id="a9537-158">The rsSharepoint.msi supports both a graphical user interface and a command line installation.</span></span> <span data-ttu-id="a9537-159">您必须以管理员权限来运行 .msi：首先使用提升权限打开命令提示符，然后从命令行运行 rsSharepoint.msi。</span><span class="sxs-lookup"><span data-stu-id="a9537-159">You must run the .msi with administrator privileges by first opening a command prompt with elevated permissions, and then running the rsSharepoint.msi from the command line.</span></span> <span data-ttu-id="a9537-160">有关如何下载外接程序的详细信息，请参阅 [在何处查找用于 SharePoint 产品的 Reporting Services 外接程序](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)。</span><span class="sxs-lookup"><span data-stu-id="a9537-160">For more information on downloading the add-in, see [Where to find the Reporting Services add-in for SharePoint Products](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).</span></span>

    > [!NOTE]
    >  <span data-ttu-id="a9537-161">如果你将 **/q** 开关用于无提示命令行安装，将不显示最终用户许可协议。</span><span class="sxs-lookup"><span data-stu-id="a9537-161">If you use the **/q** switch for a silent command line installation, the end-user license agreement will not be displayed.</span></span> <span data-ttu-id="a9537-162">对此软件的使用受到许可协议控制并且由您负责遵守该许可协议，而与安装方法无关。</span><span class="sxs-lookup"><span data-stu-id="a9537-162">Regardless of the installation method, the use of this software is governed by a license agreement and you are responsible for complying with the license agreement.</span></span>

##  <a name="install-the-add-in-using-the-installation-file-rssharepointmsi"></a><a name="bkmk_install_rssharepoint"></a><span data-ttu-id="a9537-163">使用安装文件安装外接程序 rsSharePoint.msi</span><span class="sxs-lookup"><span data-stu-id="a9537-163">Install the add-in using the installation file rsSharePoint.msi</span></span>
 <span data-ttu-id="a9537-164">本节介绍如何通过运行 .msi 安装向导或命令行安装，直接安装 rssharepoint.msi。</span><span class="sxs-lookup"><span data-stu-id="a9537-164">This section is related to installing the rssharepoint.msi directly, by either running the .msi installation wizard or a command line installation.</span></span> <span data-ttu-id="a9537-165">如果您使用 SQL Server 安装向导安装了该外接程序，则无需执行这些步骤。</span><span class="sxs-lookup"><span data-stu-id="a9537-165">If you installed the add-in using the SQL Server installation Wizard, you do not need to follow these steps.</span></span>

 <span data-ttu-id="a9537-166">您可以通过运行以下命令，看到命令行开关的完整列表：</span><span class="sxs-lookup"><span data-stu-id="a9537-166">You can see a full list of command line switches by running the following command:</span></span>

```
Rssharepoint.msi /?
```

1.  <span data-ttu-id="a9537-167">下载 `rsSharepoint.msi` 加载项 () 的安装程序 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a9537-167">Download the Setup program (`rsSharepoint.msi`) for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in.</span></span> <span data-ttu-id="a9537-168">有关如何下载外接程序的详细信息，请参阅 [在何处查找用于 SharePoint 产品的 Reporting Services 外接程序](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)。</span><span class="sxs-lookup"><span data-stu-id="a9537-168">For more information on downloading the add-in, see [Where to find the Reporting Services add-in for SharePoint Products](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).</span></span>

2.  <span data-ttu-id="a9537-169">以管理员身份运行 `rsSharepoint.msi` 以启动安装向导。</span><span class="sxs-lookup"><span data-stu-id="a9537-169">As an administrator, run `rsSharepoint.msi` to run the Installation Wizard.</span></span> <span data-ttu-id="a9537-170">向导将显示“欢迎”页、软件许可条款和注册信息页。</span><span class="sxs-lookup"><span data-stu-id="a9537-170">The wizard displays a Welcome page, the Software license terms, and a registration information page.</span></span> <span data-ttu-id="a9537-171">安装程序将在以下路径下创建文件夹，并将文件复制到该文件夹中：</span><span class="sxs-lookup"><span data-stu-id="a9537-171">Setup creates folders under the following path and copies files to the folders:</span></span>

     `%program files%\common files\Microsoft Shared\Web Server Extensions\14\`

     <span data-ttu-id="a9537-172">or</span><span class="sxs-lookup"><span data-stu-id="a9537-172">or</span></span>

     `%program files%\common files\Microsoft Shared\Web Server Extensions\15\`

3.  <span data-ttu-id="a9537-173">在 SharePoint 管理中心配置报表服务器设置和功能激活。</span><span class="sxs-lookup"><span data-stu-id="a9537-173">Configure the report server settings and feature activation in SharePoint Central Administration.</span></span> <span data-ttu-id="a9537-174">.</span><span class="sxs-lookup"><span data-stu-id="a9537-174">.</span></span> <span data-ttu-id="a9537-175">有关安装和配置 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式的详细信息，请参阅 [安装用于 SharePoint 2010 的 Reporting Services SharePoint 模式](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)。</span><span class="sxs-lookup"><span data-stu-id="a9537-175">For more information on installing and configuring [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode, see [Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).</span></span>

###  <a name="files-only-installation"></a><a name="bkmk_files_only_installation"></a><span data-ttu-id="a9537-176">仅文件安装</span><span class="sxs-lookup"><span data-stu-id="a9537-176">Files-only installation</span></span>
 <span data-ttu-id="a9537-177">若要安装文件但跳过自定义操作安装阶段，则可以从命令行中使用 SKIPCA 选项来运行 rssharepoint.msi：</span><span class="sxs-lookup"><span data-stu-id="a9537-177">To install the files but skip the custom action phase of installation, run the rssharepoint.msi from the command line with the SKIPCA option:</span></span>

1.  <span data-ttu-id="a9537-178">**使用管理员权限**打开命令提示符。</span><span class="sxs-lookup"><span data-stu-id="a9537-178">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="a9537-179">运行下面的命令：</span><span class="sxs-lookup"><span data-stu-id="a9537-179">Run the following command:</span></span>

    ```cmd
    Msiexec.exe /i rsSharePoint.msi SKIPCA=1
    ```

 <span data-ttu-id="a9537-180">安装用户界面将打开并正常运行，`rsCustomAction.exe` 文件将安装。</span><span class="sxs-lookup"><span data-stu-id="a9537-180">The installation user interface will open and run as normal and the `rsCustomAction.exe` file is installed.</span></span> <span data-ttu-id="a9537-181">但是，该 .exe 将不会在安装结束时运行，并且在安装完成后 `rsCustomAction.exe` 将保留在计算机中。</span><span class="sxs-lookup"><span data-stu-id="a9537-181">However, the .exe will not run at the end of the installation and `rsCustomAction.exe` will remain on the computer when the installation is completed.</span></span>

### <a name="use-a-two-step-installation-to-troubleshoot-installation-issues-or-install-the-content-types"></a><span data-ttu-id="a9537-182">使用两步骤安装解决安装问题或安装内容类型</span><span class="sxs-lookup"><span data-stu-id="a9537-182">Use a two-step installation to troubleshoot installation issues or install the content types</span></span>
 <span data-ttu-id="a9537-183">如果安装期间出现错误或文档库设置中不显示 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 内容类型，可以从命令行分两个步骤运行安装程序：</span><span class="sxs-lookup"><span data-stu-id="a9537-183">If you get errors during installation or the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] content types do not appear in the document library settings, you can run Setup as a two-step process from the command line:</span></span>

1.  <span data-ttu-id="a9537-184">使用管理员权限 \*\*\*\* 打开命令提示符，根据前一节中所述运行仅文件安装。</span><span class="sxs-lookup"><span data-stu-id="a9537-184">Open a command prompt **with administrator permissions** and run a files only installation as described in the previous section.</span></span>

2.  <span data-ttu-id="a9537-185">运行自定义操作可执行文件：</span><span class="sxs-lookup"><span data-stu-id="a9537-185">Run the custom actions executable:</span></span>

    1.  <span data-ttu-id="a9537-186">导航到包含文件 `rsCustomAction.exe` 的文件夹。</span><span class="sxs-lookup"><span data-stu-id="a9537-186">Navigate to the folder that contains the file `rsCustomAction.exe`.</span></span> <span data-ttu-id="a9537-187">此文件通过外接程序的“仅文件”安装复制到您的计算机。</span><span class="sxs-lookup"><span data-stu-id="a9537-187">This file is copied to your computer by the files only installation of the add-in.</span></span> <span data-ttu-id="a9537-188">`rsCustomAction.exe`位于 **% Temp%** 目录中。</span><span class="sxs-lookup"><span data-stu-id="a9537-188">`rsCustomAction.exe` is located in the **%Temp%** directory.</span></span> <span data-ttu-id="a9537-189">要导航到此文件，请从命令提示符键入以下信息：</span><span class="sxs-lookup"><span data-stu-id="a9537-189">To navigate to the file, type the following from the command prompt:</span></span>

         <span data-ttu-id="a9537-190">**CD %temp%**。</span><span class="sxs-lookup"><span data-stu-id="a9537-190">**CD %temp%**.</span></span>

         <span data-ttu-id="a9537-191">该文件应位于：**\Users\\<你的姓名\>\AppData\Local\Temp**</span><span class="sxs-lookup"><span data-stu-id="a9537-191">The file should be located in: **\Users\\<your name\>\AppData\Local\Temp**</span></span>

    2.  <span data-ttu-id="a9537-192">键入以下命令。</span><span class="sxs-lookup"><span data-stu-id="a9537-192">Type the following command.</span></span> <span data-ttu-id="a9537-193">完成该配置步骤需要几分钟时间。</span><span class="sxs-lookup"><span data-stu-id="a9537-193">This configuration step will take several minutes to finish.</span></span> <span data-ttu-id="a9537-194">在此过程中，将重新启动 W3SVC 服务。</span><span class="sxs-lookup"><span data-stu-id="a9537-194">The W3SVC service will be restarted during this process.</span></span> <span data-ttu-id="a9537-195">在程序复制文件、注册组件和运行 SharePoint 产品配置向导时，将显示若干状态消息。</span><span class="sxs-lookup"><span data-stu-id="a9537-195">Several Status messages will be displayed as the program copies files, registers components, and runs the SharePoint Product Configuration Wizard.</span></span>

        ```cmd
        rsCustomAction.exe /i
        ```

    3.  <span data-ttu-id="a9537-196">更改生效所需的时间可能因您的服务器环境而异。</span><span class="sxs-lookup"><span data-stu-id="a9537-196">The amount of time it takes for the changes to take effect may vary, depending on your server environment.</span></span> <span data-ttu-id="a9537-197">您还可以运行 **iisreset** 以强制实施更快的更新。</span><span class="sxs-lookup"><span data-stu-id="a9537-197">You can also run **iisreset** to force a quicker update.</span></span>

### <a name="quiet-installation-for-scripting"></a><span data-ttu-id="a9537-198">用于脚本撰写的静默安装</span><span class="sxs-lookup"><span data-stu-id="a9537-198">Quiet installation for scripting</span></span>
 <span data-ttu-id="a9537-199">对于不会显示任何对话框或警告的 "静默" 安装，可以使用 **/q**或 **/quiet**开关。</span><span class="sxs-lookup"><span data-stu-id="a9537-199">You can use the **/q** or **/quiet** switches for a "quiet" installation that will not display any dialogs or warnings.</span></span> <span data-ttu-id="a9537-200">如果您想要编写外接程序安装的脚本，静默安装将很有用。</span><span class="sxs-lookup"><span data-stu-id="a9537-200">The quiet installation is useful if you want to script the installation of the add-in.</span></span>

> [!NOTE]
>  <span data-ttu-id="a9537-201">如果你将 **/q** 开关用于无提示命令行安装，将不显示最终用户许可协议。</span><span class="sxs-lookup"><span data-stu-id="a9537-201">If you use the **/q** switch for a silent command line installation, the end-user license agreement will not be displayed.</span></span> <span data-ttu-id="a9537-202">对此软件的使用受到许可协议控制并且由您负责遵守该许可协议，而与安装方法无关。</span><span class="sxs-lookup"><span data-stu-id="a9537-202">Regardless of the installation method, the use of this software is governed by a license agreement and you are responsible for complying with the license agreement.</span></span>

 <span data-ttu-id="a9537-203">执行静默安装：</span><span class="sxs-lookup"><span data-stu-id="a9537-203">To perform a quiet installation:</span></span>

1.  <span data-ttu-id="a9537-204">**使用管理员权限**打开命令提示符。</span><span class="sxs-lookup"><span data-stu-id="a9537-204">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="a9537-205">运行下面的命令：</span><span class="sxs-lookup"><span data-stu-id="a9537-205">Run the following command:</span></span>

    ```cmd
    Msiexec.exe /i rsSharePoint.msi /q
    ```

##  <a name="how-to-remove-the-reporting-services-add-in"></a><a name="bkmk_remove_addin"></a><span data-ttu-id="a9537-206">如何删除 Reporting Services 外接程序</span><span class="sxs-lookup"><span data-stu-id="a9537-206">How to Remove the Reporting Services Add-in</span></span>
 <span data-ttu-id="a9537-207">可以从 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Windows 控制面板或命令行卸载用于 SharePoint 产品的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 外接程序。</span><span class="sxs-lookup"><span data-stu-id="a9537-207">You can uninstall the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in for SharePoint Products from [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows control panel or the command line.</span></span>

1.  <span data-ttu-id="a9537-208">使用控制面板将在当前计算机上完全卸载文件， **并且** 将从 SharePoint 场中删除 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 对象和功能。</span><span class="sxs-lookup"><span data-stu-id="a9537-208">Using control panel will run a complete uninstall of the files on the current computer **AND** it will remove the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] object and features from the SharePoint farm.</span></span> <span data-ttu-id="a9537-209">删除 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 对象和功能后，您将不再能查看和更新报表。</span><span class="sxs-lookup"><span data-stu-id="a9537-209">When the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] object and features are removed you can no longer review and update reports.</span></span>

2.  <span data-ttu-id="a9537-210">使用命令行方法卸载外接程序时，您可以使用 LocalOnly 参数仅从本地计算机删除外接程序文件，场中的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 对象和功能将保持不变。</span><span class="sxs-lookup"><span data-stu-id="a9537-210">The command line method to uninstall the add-in allows you to use the LocalOnly parameter to only remove the add-in files from the local computer and the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] object and features in the farm will not be changed.</span></span>

 <span data-ttu-id="a9537-211">卸载外接程序会删除用于在报表服务器上处理报表的服务器集成功能。</span><span class="sxs-lookup"><span data-stu-id="a9537-211">Uninstalling the add-in will remove server integration features that are used to process reports on a report server.</span></span> <span data-ttu-id="a9537-212">它还将从 SharePoint 管理中心删除 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 页和其他自定义 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 页。</span><span class="sxs-lookup"><span data-stu-id="a9537-212">It will also remove the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pages from SharePoint Central Administration and other custom [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pages.</span></span> <span data-ttu-id="a9537-213">您可能还想删除在受影响的 SharePoint 站点上不再使用的所有报表和其他报表服务器项。</span><span class="sxs-lookup"><span data-stu-id="a9537-213">You may also want to remove any reports and other report server items that you no longer use on the affected SharePoint sites.</span></span> <span data-ttu-id="a9537-214">在删除 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序后，它们不会再运行。</span><span class="sxs-lookup"><span data-stu-id="a9537-214">They will not run after the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in is removed.</span></span>

 <span data-ttu-id="a9537-215">若要卸载 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序，必须使 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] 或 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 安装仍处于运行状态。</span><span class="sxs-lookup"><span data-stu-id="a9537-215">To uninstall the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in, you must have a [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] installation still running.</span></span> <span data-ttu-id="a9537-216">如果先卸载 SharePoint 2010，则必须重新安装该产品才能卸载 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序。</span><span class="sxs-lookup"><span data-stu-id="a9537-216">If you uninstall the SharePoint 2010 first, you must reinstall it to uninstall the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in.</span></span>

 <span data-ttu-id="a9537-217">卸载外接程序的步骤与卸载独立服务器和服务器场的步骤相同。</span><span class="sxs-lookup"><span data-stu-id="a9537-217">The steps for uninstalling the add-in are the same for both stand-alone servers and server farms.</span></span> <span data-ttu-id="a9537-218">安装程序将删除在安装过程中添加的程序文件和所有配置设置。</span><span class="sxs-lookup"><span data-stu-id="a9537-218">Setup will remove program files and any configuration settings that were added during installation.</span></span>

 <span data-ttu-id="a9537-219">卸载外接程序将不删除以下内容：</span><span class="sxs-lookup"><span data-stu-id="a9537-219">Uninstalling the add-in will not remove the following:</span></span>

-   <span data-ttu-id="a9537-220">为用于访问 SharePoint 配置和内容数据库的报表服务器服务帐户创建的登录名。</span><span class="sxs-lookup"><span data-stu-id="a9537-220">Logins created for the Report Server service account that is used to access the SharePoint configuration and content databases.</span></span> <span data-ttu-id="a9537-221">您必须从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 用于承载 SharePoint 数据库的实例中删除报表服务器服务帐户的所有登录名。</span><span class="sxs-lookup"><span data-stu-id="a9537-221">You must delete any logins for the Report Server service account from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance used to host the SharePoint databases.</span></span>

-   <span data-ttu-id="a9537-222">为报表用户创建的权限或组。</span><span class="sxs-lookup"><span data-stu-id="a9537-222">Permissions or groups that you created for report users.</span></span> <span data-ttu-id="a9537-223">如果创建了自定义权限级别或 SharePoint 组来授予访问报表服务器功能的权限，则应撤销不再需要的任何权限。</span><span class="sxs-lookup"><span data-stu-id="a9537-223">If you created custom permission levels or SharePoint groups to grant access to report server features, you should revoke any permissions that are no longer required.</span></span>

-   <span data-ttu-id="a9537-224">上载到 SharePoint 库的数据文件，包括报表定义 (.rdl)、共享数据源 (.rsds) 和已发布报表项 (.rsc) 文件。</span><span class="sxs-lookup"><span data-stu-id="a9537-224">Data files that you uploaded to a SharePoint library, including report definition (.rdl), shared data source (.rsds), and published report items (.rsc) files.</span></span> <span data-ttu-id="a9537-225">不会删除这些文件，但它们将不再运行。</span><span class="sxs-lookup"><span data-stu-id="a9537-225">They are not deleted, but they will no longer run.</span></span> <span data-ttu-id="a9537-226">必须手动删除这些文件。</span><span class="sxs-lookup"><span data-stu-id="a9537-226">You must delete the files manually.</span></span>

-   <span data-ttu-id="a9537-227">安装程序将不删除报表服务器数据库，也不修改用于集成操作的报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="a9537-227">Setup will not delete the report server database or modify the report server instance that was used for integrated operations.</span></span>

### <a name="to-uninstall-from-windows-control-panel"></a><span data-ttu-id="a9537-228">从 Windows 控制面板卸载</span><span class="sxs-lookup"><span data-stu-id="a9537-228">To Uninstall from Windows Control Panel</span></span>
 <span data-ttu-id="a9537-229">从 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 控制面板启动向导并删除外接程序：</span><span class="sxs-lookup"><span data-stu-id="a9537-229">To start the wizard from [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Control Panel and remove the add-in:</span></span>

1.  <span data-ttu-id="a9537-230">在控制面板的 **“程序”** 中，选择 **“卸载程序”**。</span><span class="sxs-lookup"><span data-stu-id="a9537-230">In Control Panel, in **Programs**, select **Uninstall a Program**</span></span>

2.  <span data-ttu-id="a9537-231">选择“用于 SharePoint 的 Microsoft SQL Server RS 外接程序”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a9537-231">Select **Microsoft SQL Server RS Add-in for SharePoint**.</span></span> <span data-ttu-id="a9537-232">还可以从命令提示符运行不带开关的 **rssharepoint.msi** 来启动卸载向导。</span><span class="sxs-lookup"><span data-stu-id="a9537-232">You can also start the uninstall wizard by running **rssharepoint.msi** from the command prompt with no switches.</span></span>

3.  <span data-ttu-id="a9537-233">单击“删除”。</span><span class="sxs-lookup"><span data-stu-id="a9537-233">Click **Remove**.</span></span>

### <a name="uninstall-from-the-command-line"></a><span data-ttu-id="a9537-234">从命令行卸载</span><span class="sxs-lookup"><span data-stu-id="a9537-234">Uninstall from the command line</span></span>
 <span data-ttu-id="a9537-235">从命令行卸载外接程序：</span><span class="sxs-lookup"><span data-stu-id="a9537-235">To uninstall the add-in from the command line:</span></span>

1.  <span data-ttu-id="a9537-236">**使用管理员权限**打开命令提示符。</span><span class="sxs-lookup"><span data-stu-id="a9537-236">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="a9537-237">运行下面的命令：</span><span class="sxs-lookup"><span data-stu-id="a9537-237">Run the following command:</span></span>

    ```cmd
    msiexec.exe /uninstall rsSharePoint.msi
    ```

3.  <span data-ttu-id="a9537-238">您将看到一个确认消息框。</span><span class="sxs-lookup"><span data-stu-id="a9537-238">You will see a confirmation message box.</span></span> <span data-ttu-id="a9537-239">单击 **“是”** 。</span><span class="sxs-lookup"><span data-stu-id="a9537-239">Click **Yes**.</span></span>

### <a name="uninstall-the-add-in-from-the-local-server-only"></a><span data-ttu-id="a9537-240">仅从本地服务器卸载外接程序</span><span class="sxs-lookup"><span data-stu-id="a9537-240">Uninstall the add-in from the local server only</span></span>
 <span data-ttu-id="a9537-241">卸载外接程序的以前方法会从场中删除 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 功能和对象。</span><span class="sxs-lookup"><span data-stu-id="a9537-241">The previous methods of uninstalling the add-in will remove the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features and object from the farm.</span></span> <span data-ttu-id="a9537-242">如果具有多服务器场且只想从本地计算机卸载外接程序而使 SharePoint 场正常工作，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="a9537-242">If you have a multi-server farm and want to uninstall the add-in from only the local computer and leave the SharePoint farm in a functional state, complete the following steps:</span></span>

1.  <span data-ttu-id="a9537-243">**使用管理员权限**打开命令提示符。</span><span class="sxs-lookup"><span data-stu-id="a9537-243">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="a9537-244">运行下面的命令：</span><span class="sxs-lookup"><span data-stu-id="a9537-244">Run the following command:</span></span>

    ```cmd
    Msiexec.exe /uninstall rsSharePoint.msi LocalOnly=1
    ```

 <span data-ttu-id="a9537-245">这将从 SharePoint 撤消注册 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 组件并且删除文件，但仅限本地计算机。</span><span class="sxs-lookup"><span data-stu-id="a9537-245">This will unregister the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components from SharePoint and remove the files, but for the local computer only.</span></span>

 <span data-ttu-id="a9537-246">如果您想要从 SharePoint 撤消注册 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 功能，但在磁盘上保留这些文件以供以后使用，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="a9537-246">If you want to unregister the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features from SharePoint but leave the files on the disk for use later, complete the following steps:</span></span>

1.  <span data-ttu-id="a9537-247">**使用管理员权限**打开命令提示符。</span><span class="sxs-lookup"><span data-stu-id="a9537-247">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="a9537-248">运行下面的命令：</span><span class="sxs-lookup"><span data-stu-id="a9537-248">Run the following command:</span></span>

    ```cmd
    rsCustomAction.exe /p
    ```

 <span data-ttu-id="a9537-249">上述步骤假定您使用 SkipCA=1 完成了 .msi 安装并且 rscusstomaction.exe 可用。</span><span class="sxs-lookup"><span data-stu-id="a9537-249">The above steps assume you completed an installation of the .msi with SkipCA=1 and the rscusstomaction.exe is available.</span></span> <span data-ttu-id="a9537-250">有关详细信息，请参阅描述仅文件安装的部分。</span><span class="sxs-lookup"><span data-stu-id="a9537-250">For more information, see the section describing the files only installation.</span></span>

##  <a name="how-to-repair-rssharepointmsi-from-the-command-line"></a><a name="bkmk_repair"></a><span data-ttu-id="a9537-251">如何从命令行修复 rssharepoint.msi</span><span class="sxs-lookup"><span data-stu-id="a9537-251">How to Repair rssharepoint.msi from the Command Line</span></span>
 <span data-ttu-id="a9537-252">若要使用命令行修复或卸载 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="a9537-252">To repair or uninstall the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in using the command line, complete the following steps:</span></span>

1.  <span data-ttu-id="a9537-253">**使用管理员权限**打开命令提示符。</span><span class="sxs-lookup"><span data-stu-id="a9537-253">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="a9537-254">运行下面的命令：</span><span class="sxs-lookup"><span data-stu-id="a9537-254">Run the following command:</span></span>

    ```cmd
    msiexec.exe /f rssharepoint.msi
    ```

##  <a name="setup-log-files"></a><a name="bkmk_logfiles"></a><span data-ttu-id="a9537-255">安装日志文件</span><span class="sxs-lookup"><span data-stu-id="a9537-255">Setup Log Files</span></span>
 <span data-ttu-id="a9537-256">安装程序在运行期间，会为安装 **外接程序的用户将相应信息记录到** %temp% [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 文件夹下的一个日志文件中。</span><span class="sxs-lookup"><span data-stu-id="a9537-256">When Setup runs, it logs information to a log file in the **%temp%** folder for the user who installed the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in.</span></span> <span data-ttu-id="a9537-257">例如， **c:\Users \\<username \> \AppData\Local\Temp** 。文件名为**RS_SP_ \<number> .log**，例如**RS_SP_0 .log**。</span><span class="sxs-lookup"><span data-stu-id="a9537-257">For example **c:\Users\\<username\>\AppData\Local\Temp** .The file name is **RS_SP_\<number>.log**, for example **RS_SP_0.log**.</span></span> <span data-ttu-id="a9537-258">日志中的每个错误都以字符串“SSRSCustomActionError”开头。</span><span class="sxs-lookup"><span data-stu-id="a9537-258">Each error in the log starts with the string "SSRSCustomActionError".</span></span>

> [!NOTE]
>  <span data-ttu-id="a9537-259">AppData 是 Windows 操作系统中隐藏的文件夹。</span><span class="sxs-lookup"><span data-stu-id="a9537-259">AppData is a hidden folder in the Windows operating system.</span></span> <span data-ttu-id="a9537-260">您可能需要修改您的 Windows 资源管理器的文件夹设置，以便可以看到隐藏的文件和文件夹。</span><span class="sxs-lookup"><span data-stu-id="a9537-260">You may need to modify your Windows Explorer folder settings so you can see hidden files and folders.</span></span>

#### <a name="view-a-log-file-with-windows-notepad"></a><span data-ttu-id="a9537-261">使用 Windows 记事本查看日志文件</span><span class="sxs-lookup"><span data-stu-id="a9537-261">View a log file with Windows Notepad</span></span>

1.  <span data-ttu-id="a9537-262">下面的命令将更改命令提示符路径，列出 rs 日志文件，然后使用 Windows 记事本打开这些文件之一：</span><span class="sxs-lookup"><span data-stu-id="a9537-262">The following commands will change the command prompt path, list the rs log files and then open one of the files with Windows Notepad:</span></span>

    ```cmd
    cd %temp%
    ```

    ```cmd
    dir rs_sp*.log
    ```

    ```cmd
    notepad rs_sp_3.log
    ```

#### <a name="view-a-log-file-with-powershell"></a><span data-ttu-id="a9537-263">使用 PowerShell 查看日志文件</span><span class="sxs-lookup"><span data-stu-id="a9537-263">View a Log file with PowerShell</span></span>

1.  <span data-ttu-id="a9537-264">从 SharePoint Management Shell 键入以下命令，以便从该文件中返回包含“ssrscustomactionerror”的行的筛选后列表：</span><span class="sxs-lookup"><span data-stu-id="a9537-264">Type the following command from the SharePoint Management Shell to return a filtered list of rows from the file, that contain "ssrscustomactionerror":</span></span>

    ```powershell
    Get-Content -Path C:\Users\<UserName\AppData\Local\Temp\rs_sp_0.log | Select-String "ssrscustomactionerror"
    ```

2.  <span data-ttu-id="a9537-265">输出将类似于以下内容：</span><span class="sxs-lookup"><span data-stu-id="a9537-265">The output will look similar to the following:</span></span>

     <span data-ttu-id="a9537-266">`2011-05-23 12:40:12: SSRSCustomActionError: SharePoint is installed, but not configured`.</span><span class="sxs-lookup"><span data-stu-id="a9537-266">`2011-05-23 12:40:12: SSRSCustomActionError: SharePoint is installed, but not configured`.</span></span>

##  <a name="upgrade"></a><a name="bkmk_upgrade"></a><span data-ttu-id="a9537-267">升级</span><span class="sxs-lookup"><span data-stu-id="a9537-267">Upgrade</span></span>
 <span data-ttu-id="a9537-268">如果具有 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序的现有安装，则可以升级到当前版本。</span><span class="sxs-lookup"><span data-stu-id="a9537-268">If you have an existing installation of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in, you can upgrade to the current version.</span></span> <span data-ttu-id="a9537-269">外接程序安装程序将检测现有版本并提示您确认是否更新。</span><span class="sxs-lookup"><span data-stu-id="a9537-269">The add-in setup will detect the existing version and prompt you to confirm the update.</span></span> <span data-ttu-id="a9537-270">将显示如下的消息：</span><span class="sxs-lookup"><span data-stu-id="a9537-270">The message will be similar to the following:</span></span>

 <span data-ttu-id="a9537-271">**在您的系统上检测到此产品的较低版本。是否要升级现有安装？**</span><span class="sxs-lookup"><span data-stu-id="a9537-271">**A Lower version of this product has been detected on your system. Would you like to upgrade your existing installation?**</span></span>

 <span data-ttu-id="a9537-272">如果确认更新，则旧版本的外接程序将被删除，然后安装新版本。</span><span class="sxs-lookup"><span data-stu-id="a9537-272">If you confirm, the older version of the add-in will be removed and then the new version will be installed.</span></span>

 <span data-ttu-id="a9537-273">请注意， [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序不能识别实例。</span><span class="sxs-lookup"><span data-stu-id="a9537-273">Note that the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in is not instance-aware.</span></span> <span data-ttu-id="a9537-274">一台计算机上只能有一个外接程序实例。</span><span class="sxs-lookup"><span data-stu-id="a9537-274">You can only have one instance of the add-in on a computer.</span></span> <span data-ttu-id="a9537-275">不能并行运行不同版本和当前版本。</span><span class="sxs-lookup"><span data-stu-id="a9537-275">You cannot run different versions side-by-side the current version.</span></span>

##  <a name="rscustomactionexe"></a><a name="bkmk_rscustomaction"></a><span data-ttu-id="a9537-276">RsCustomAction.exe</span><span class="sxs-lookup"><span data-stu-id="a9537-276">RsCustomAction.exe</span></span>
 <span data-ttu-id="a9537-277">下表概述了 rscustomaction.exe 的各个开关：</span><span class="sxs-lookup"><span data-stu-id="a9537-277">The following table summarizes the rscustomaction.exe switches:</span></span>

|<span data-ttu-id="a9537-278">开关</span><span class="sxs-lookup"><span data-stu-id="a9537-278">Switch</span></span>|<span data-ttu-id="a9537-279">说明</span><span class="sxs-lookup"><span data-stu-id="a9537-279">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="a9537-280">i</span><span class="sxs-lookup"><span data-stu-id="a9537-280">i</span></span>|<span data-ttu-id="a9537-281">安装自定义操作。</span><span class="sxs-lookup"><span data-stu-id="a9537-281">Install the custom actions.</span></span> <span data-ttu-id="a9537-282">这将在 SharePoint 中注册 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 组件。</span><span class="sxs-lookup"><span data-stu-id="a9537-282">This will register the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components in SharePoint.</span></span> <span data-ttu-id="a9537-283">并且将重新启动 W3SVCservice。</span><span class="sxs-lookup"><span data-stu-id="a9537-283">This will restart the W3SVCservice.</span></span>|
|<span data-ttu-id="a9537-284">r</span><span class="sxs-lookup"><span data-stu-id="a9537-284">r</span></span>|<span data-ttu-id="a9537-285">修复</span><span class="sxs-lookup"><span data-stu-id="a9537-285">Repair</span></span>|
|<span data-ttu-id="a9537-286">u</span><span class="sxs-lookup"><span data-stu-id="a9537-286">u</span></span>|<span data-ttu-id="a9537-287">卸载。</span><span class="sxs-lookup"><span data-stu-id="a9537-287">Uninstall.</span></span> <span data-ttu-id="a9537-288">这将从整个 SharePoint 撤消注册 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 组件，但在磁盘上保留文件。</span><span class="sxs-lookup"><span data-stu-id="a9537-288">This will unregister the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components from the entire SharePoint farm but leave the files on disk.</span></span> <span data-ttu-id="a9537-289">并且将重新启动 W3SVCservice。</span><span class="sxs-lookup"><span data-stu-id="a9537-289">This will restart the W3SVCservice.</span></span>|
|<span data-ttu-id="a9537-290">p</span><span class="sxs-lookup"><span data-stu-id="a9537-290">p</span></span>|<span data-ttu-id="a9537-291">本地卸载。</span><span class="sxs-lookup"><span data-stu-id="a9537-291">Local uninstall.</span></span> <span data-ttu-id="a9537-292">这将仅从本地计算机撤消注册 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 组件。</span><span class="sxs-lookup"><span data-stu-id="a9537-292">This will unregister the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components from only the local computer.</span></span> <span data-ttu-id="a9537-293">文件将保留在磁盘上。</span><span class="sxs-lookup"><span data-stu-id="a9537-293">The files will remain on disk.</span></span> <span data-ttu-id="a9537-294">并且将重新启动 W3SVCservice。</span><span class="sxs-lookup"><span data-stu-id="a9537-294">This will restart the W3SVCservice.</span></span>|
|<span data-ttu-id="a9537-295">t</span><span class="sxs-lookup"><span data-stu-id="a9537-295">t</span></span>|<span data-ttu-id="a9537-296">仅限 SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 2005。</span><span class="sxs-lookup"><span data-stu-id="a9537-296">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 2005 only.</span></span> <span data-ttu-id="a9537-297">此开关测试报表服务器与报表服务器数据库之间是否具有有效的连接。</span><span class="sxs-lookup"><span data-stu-id="a9537-297">The switch tests if the report server has a working connection to the report server database.</span></span>|

## <a name="configuring-reporting-services"></a><span data-ttu-id="a9537-298">配置 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="a9537-298">Configuring Reporting Services</span></span>
 <span data-ttu-id="a9537-299">在所有所需计算机上都安装了外接程序之后，您需要从 SharePoint 管理中心来配置报表服务器。</span><span class="sxs-lookup"><span data-stu-id="a9537-299">After you have installed the add-in on all the necessary computers, you need to configure the report server from SharePoint Central Administration.</span></span> <span data-ttu-id="a9537-300">所需步骤取决于安装不同技术的顺序。</span><span class="sxs-lookup"><span data-stu-id="a9537-300">The steps that are needed depend on the order which the different technologies were installed.</span></span> <span data-ttu-id="a9537-301">有关详细信息，请参阅[Install Reporting Services Sharepoint mode For sharepoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)和[Reporting Services Report Server &#40;sharepoint 模式&#41;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md)</span><span class="sxs-lookup"><span data-stu-id="a9537-301">For more information, see [Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) and [Reporting Services Report Server &#40;SharePoint Mode&#41;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="a9537-302">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a9537-302">See Also</span></span>
 <span data-ttu-id="a9537-303">[Reporting Services sharepoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) [Reporting Services 报表服务器 &#40;Sharepoint 模式](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md)下安装 sharepoint 模式&#41;</span><span class="sxs-lookup"><span data-stu-id="a9537-303">[Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) [Reporting Services Report Server &#40;SharePoint Mode&#41;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md)</span></span>
