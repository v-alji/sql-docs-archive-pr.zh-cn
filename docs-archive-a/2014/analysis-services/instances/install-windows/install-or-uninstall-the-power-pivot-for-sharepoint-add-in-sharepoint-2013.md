---
title: 安装或卸载 (SharePoint 2013) 的 PowerPivot for SharePoint 外接程序 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: fe13ce8b-9369-4126-928a-9426f9119424
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7df54d11021163167149e5b0c1edd960fee1a2ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688323"
---
# <a name="install-or-uninstall-the-powerpivot-for-sharepoint-add-in-sharepoint-2013"></a><span data-ttu-id="a0ed5-102">安装或卸载 PowerPivot for SharePoint 外接程序 (SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="a0ed5-102">Install or Uninstall the PowerPivot for SharePoint Add-in (SharePoint 2013)</span></span>
  [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] <span data-ttu-id="a0ed5-103">是在 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 场中提供 [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] 数据访问的应用程序服务器组件和后端服务的集合。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-103">is a collection of application server components and back-end services that provide [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] data access in a [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] farm.</span></span> <span data-ttu-id="a0ed5-104">[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 外接程序 (**spPowerpivot.msi**) 是用于安装应用程序服务器组件的安装程序包。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-104">The [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint add-in (**spPowerpivot.msi**) is an installer package used to install the application server components.</span></span>

-   <span data-ttu-id="a0ed5-105">该外接程序对于 SharePoint 2010 部署不是必需的。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-105">The add-in is not required for SharePoint 2010 deployments.</span></span>

-   <span data-ttu-id="a0ed5-106">在包含 SharePoint 2013 和 SharePoint 模式下的 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 的单一服务器部署中，此外接程序不是必需的。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-106">The add-in is not required on a single server deployment that includes SharePoint 2013 and [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="a0ed5-107">在 SharePoint 模式下安装 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 服务器时，将包括由此外接程序安装的组件。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-107">The components installed by the add-in are included when you install an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode.</span></span> <span data-ttu-id="a0ed5-108">有关包含外接程序的示例部署的关系图，请参阅[SharePoint 中 SQL SERVER BI 功能的部署拓扑](../../../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-108">For diagrams of example deployments with the add-in, see [Deployment Topologies for SQL Server BI Features in SharePoint](../../../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md).</span></span>

 <span data-ttu-id="a0ed5-109">**注意：** 本主题介绍如何安装 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 解决方案文件和 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013 配置工具。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-109">**Note:** This topic describes installing the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] solution files and [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013 Configuration tool.</span></span> <span data-ttu-id="a0ed5-110">安装完成后，请参阅以下主题，了解有关配置工具和附加功能的信息、[配置 PowerPivot 和部署解决方案 &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013)。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-110">After the installation, see the following topic for information on the configuration tool and additional features, [Configure PowerPivot and Deploy Solutions &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013).</span></span>

 <span data-ttu-id="a0ed5-111">有关如何下载 **spPowerPivot.msi**的信息，请参阅 [Microsoft® SQL Server® 2014 PowerPivot® for Microsoft SharePoint®](https://go.microsoft.com/fwlink/?LinkID=324854)。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-111">For information on how to download **spPowerPivot.msi**, see [Microsoft® SQL Server® 2014 PowerPivot® for Microsoft SharePoint®](https://go.microsoft.com/fwlink/?LinkID=324854).</span></span>

 <span data-ttu-id="a0ed5-112">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="a0ed5-112">**In this topic:**</span></span>

-   [<span data-ttu-id="a0ed5-113">背景</span><span class="sxs-lookup"><span data-stu-id="a0ed5-113">Background</span></span>](#bkmk_background)

-   [<span data-ttu-id="a0ed5-114">在何处安装 spPowerPivot.msi？</span><span class="sxs-lookup"><span data-stu-id="a0ed5-114">Where to Install spPowerPivot.msi?</span></span>](#bkmk_where_to_install)

-   [<span data-ttu-id="a0ed5-115">要求和先决条件</span><span class="sxs-lookup"><span data-stu-id="a0ed5-115">Requirements and Prerequisites</span></span>](#bkmk_prereq)

-   [<span data-ttu-id="a0ed5-116">安装 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="a0ed5-116">To Install PowerPivot for SharePoint</span></span>](#bkmk_install)

-   [<span data-ttu-id="a0ed5-117">使用 PowerPivot for SharePoint 2013 配置工具部署 SharePoint 解决方案文件</span><span class="sxs-lookup"><span data-stu-id="a0ed5-117">Deploy the SharePoint Solution Files with the PowerPivot for SharePoint 2013 Configuration Tool</span></span>](#bkmk_deploy_solution)

-   [<span data-ttu-id="a0ed5-118">卸载或修复外接程序</span><span class="sxs-lookup"><span data-stu-id="a0ed5-118">Uninstall or repair the add-in</span></span>](#bkmk_remove_addin)

##  <a name="background"></a><a name="bkmk_background"></a> <span data-ttu-id="a0ed5-119">背景</span><span class="sxs-lookup"><span data-stu-id="a0ed5-119">Background</span></span>

-   <span data-ttu-id="a0ed5-120">**应用程序服务器：** [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 功能包括将工作簿用作数据源、计划数据刷新以及 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 管理仪表板。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-120">**Application Server:** [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] functionality in SharePoint 2013 includes using workbooks as a data source, scheduled data refresh, and the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Management Dashboard.</span></span>

     [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)]<span data-ttu-id="a0ed5-121">是 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] **spPowerpivot.msi**) 的 Windows Installer 包 (，它部署 Analysis Services 的客户端库并将 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] 安装文件复制到计算机。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-121">is a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows Installer package (**spPowerpivot.msi**) that deploys Analysis Services client libraries and copies [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] installation files to the computer.</span></span> <span data-ttu-id="a0ed5-122">此安装程序不会在 SharePoint 中部署或配置 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-122">The installer does not deploy or configure [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] features in SharePoint.</span></span> <span data-ttu-id="a0ed5-123">默认情况下将安装下列组件：</span><span class="sxs-lookup"><span data-stu-id="a0ed5-123">The following components install by default:</span></span>

    -   [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] <span data-ttu-id="a0ed5-124">2013。此组件包括 PowerShell 脚本（.ps1 文件）、SharePoint 解决方案包 (.wsp) 和 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 2013 配置工具，用于在 SharePoint 2013 服务器场中部署 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-124">2013. This component includes PowerShell scripts (.ps1 files), SharePoint solution packages (.wsp), and the [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 2013 configuration tool to deploy [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] in a SharePoint 2013 farm.</span></span>

    -   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="a0ed5-125">Analysis Services OLE DB 访问接口 (MSOLAP)。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-125">OLE DB Provider for Analysis Services (MSOLAP).</span></span>

    -   <span data-ttu-id="a0ed5-126">ADOMD.NET 数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-126">ADOMD.NET data provider.</span></span>

    -   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="a0ed5-127">分析管理对象。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-127">Analysis Management Objects.</span></span>

-   <span data-ttu-id="a0ed5-128">**后端服务：** 如果您使用 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for Excel 来创建包含分析数据的工作簿，则必须为 Excel Services 配置在 SharePoint 模式下运行 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 的 BI 服务器才能访问服务器环境中的这些数据。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-128">**Backend services:** If you use [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for Excel to create workbooks that contain analytical data, you must have Excel Services configured with a BI server running [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] in SharePoint mode to access that data in a server environment.</span></span> <span data-ttu-id="a0ed5-129">您可在安装了 SharePoint Server 2013 的计算机上或没有 SharePoint 软件的其他计算机上运行 SQL Server 安装程序。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-129">You can run SQL Server Setup on a computer that has SharePoint Server 2013 installed, or on a different computer that has no SharePoint software.</span></span> <span data-ttu-id="a0ed5-130">Analysis Services 对 SharePoint 没有任何依赖关系。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-130">Analysis Services does not have any dependencies on SharePoint.</span></span>

     <span data-ttu-id="a0ed5-131">有关安装、卸载和配置后端服务的详细信息，请参阅以下文章：</span><span class="sxs-lookup"><span data-stu-id="a0ed5-131">For more information on installing, uninstalling, and configuring the backend services, see the following:</span></span>

    -   [<span data-ttu-id="a0ed5-132">PowerPivot for SharePoint 2013 安装</span><span class="sxs-lookup"><span data-stu-id="a0ed5-132">PowerPivot for SharePoint 2013 Installation</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)

    -   [<span data-ttu-id="a0ed5-133">卸载 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="a0ed5-133">Uninstall PowerPivot for SharePoint</span></span>](../../../sql-server/install/uninstall-power-pivot-for-sharepoint.md)

##  <a name="where-to-install-sppowerpivotmsi"></a><a name="bkmk_where_to_install"></a> <span data-ttu-id="a0ed5-134">spPowerPivot.msi 的安装位置</span><span class="sxs-lookup"><span data-stu-id="a0ed5-134">Where to Install spPowerPivot.msi?</span></span>
 <span data-ttu-id="a0ed5-135">建议的最佳做法是在 SharePoint 场中的所有服务器上安装 **spPowerPivot.msi** 以实现配置一致性，包括应用程序服务器和 Web 前端服务器。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-135">A recommended best practice is to install **spPowerPivot.msi** on all servers in the SharePoint farm for configuration consistency, including application servers and web-front end servers.</span></span> <span data-ttu-id="a0ed5-136">此安装程序包包含 Analysis Services 数据访问接口以及 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] 配置工具。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-136">The installer package includes the Analysis Services data providers as well as the [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] configuration tool.</span></span> <span data-ttu-id="a0ed5-137">安装 **spPowerPivot.msi** 时，您可通过排除个别组件来自定义安装。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-137">When you install **spPowerPivot.msi** you can customize the installation by excluding individual components.</span></span>

 <span data-ttu-id="a0ed5-138">**数据访问接口：** 一些 SharePoint 和 SQL Server 技术使用 Analysis Services 数据访问接口，这些技术包括 Excel Services、PerformancePoint Services 和 Power View。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-138">**Data providers:** Several SharePoint and SQL Server technologies use the Analysis Services data providers including Excel Services, PerformancePoint Services, and Power View.</span></span> <span data-ttu-id="a0ed5-139">在所有 SharePoint 服务器上安装 **spPowerPivot.msi** 将确保全套 Analysis Services 数据访问接口和 PowerPivot 连接在服务器场中一致可用。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-139">Installing **spPowerPivot.msi** on all SharePoint servers ensures the full set of Analysis Services data providers and PowerPivot connectivity is consistently available across the farm.</span></span>

> [!NOTE]
>  <span data-ttu-id="a0ed5-140">您必须使用 **spPowerPivot.msi**在 SharePoint 2013 服务器上安装 Analysis Services 数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-140">You must install the Analysis Services data providers on a SharePoint 2013 server using **spPowerPivot.msi**.</span></span> <span data-ttu-id="a0ed5-141">不支持 [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] 功能包中提供的其他安装程序包，因为这些包中未包含数据访问接口在此环境中所需的 SharePoint 2013 支持文件。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-141">Other installer packages available in the [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] Feature Pack are not supported because these packages do not include the SharePoint 2013 support files that the data providers require in this environment.</span></span>

 <span data-ttu-id="a0ed5-142">**配置工具：** 仅 SharePoint 服务器之一需要 PowerPivot for SharePoint 2013 配置工具。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-142">**Configuration Tool:** The PowerPivot for SharePoint 2013 configuration tool is required on only one of the SharePoint servers.</span></span> <span data-ttu-id="a0ed5-143">但是，在多服务器场中，建议的最佳做法是在至少两台服务器上安装此配置工具，以便两台服务器中的一台脱机时，您具有访问此配置工具的权限。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-143">However a recommended best practice in multi-server farms is to install the configuration tool on at least two servers so you have access to the configuration tool if one of the two servers is offline.</span></span>

##  <a name="requirements-and-prerequisites"></a><a name="bkmk_prereq"></a><span data-ttu-id="a0ed5-144">要求和先决条件</span><span class="sxs-lookup"><span data-stu-id="a0ed5-144">Requirements and Prerequisites</span></span>

-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="a0ed5-145">SharePoint Server 2013。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-145">SharePoint Server 2013.</span></span>

-   <span data-ttu-id="a0ed5-146">**spPowerPivot.msi** 只有 64 位版，以符合 SharePoint 产品和技术的要求。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-146">**spPowerPivot.msi** is 64-bit only, in accordance with the requirements of SharePoint products and technologies.</span></span>

-   <span data-ttu-id="a0ed5-147">PowerPivot 模式下的 [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-147">A [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] server in PowerPivot mode.</span></span> <span data-ttu-id="a0ed5-148">Excel Services 将使用 SQL Server Analysis Services 实例作为 PowerPivot 服务器。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-148">Excel Services will use the SQL Server Analysis Services instance as a PowerPivot server.</span></span> <span data-ttu-id="a0ed5-149">Analysis Services 可在本地或远程计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-149">Analysis Services can run on the local or a remote computer.</span></span>

-   <span data-ttu-id="a0ed5-150">**权限：** 若要安装 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)]，当前用户需要是计算机上的管理员和 SharePoint 场 Administrators 组的成员。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-150">**Permissions:** To install [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)], the current user is required to be an administrator on the computer and a SharePoint Farm Administrators group.</span></span>

-   <span data-ttu-id="a0ed5-151">有关 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 要求和先决条件的详细信息，请参阅[SharePoint 模式下 Analysis Services 服务器的硬件和软件要求 &#40;SQL Server 2014&#41;](../../../sql-server/install/hardware-software-requirements-analysis-services-server-sharepoint-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-151">For more information on [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] requirements and pre-requisites, go to [Hardware and Software Requirements for Analysis Services Server in SharePoint Mode &#40;SQL Server 2014&#41;](../../../sql-server/install/hardware-software-requirements-analysis-services-server-sharepoint-mode.md).</span></span>

##  <a name="to-install-powerpivot-for-sharepoint"></a><a name="bkmk_install"></a><span data-ttu-id="a0ed5-152">安装 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="a0ed5-152">To Install PowerPivot for SharePoint</span></span>
 <span data-ttu-id="a0ed5-153">**spPowerpivot.msi** 安装程序包同时支持图形用户界面和命令行模式。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-153">The **spPowerpivot.msi** installer package supports both a graphical user interface and a command-line mode.</span></span> <span data-ttu-id="a0ed5-154">这两种安装方法都要求您使用管理员特权运行 .msi。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-154">Both methods of installation require that you run the .msi with administrator privileges.</span></span> <span data-ttu-id="a0ed5-155">安装完成后，请参阅以下主题，了解有关配置工具和附加功能的信息、[配置 PowerPivot 和部署解决方案 &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013)。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-155">After the installation, see the following topic for information on the configuration tool and additional features, [Configure PowerPivot and Deploy Solutions &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013).</span></span>

### <a name="user-interface-installation"></a><span data-ttu-id="a0ed5-156">用户界面安装</span><span class="sxs-lookup"><span data-stu-id="a0ed5-156">User interface installation</span></span>
 <span data-ttu-id="a0ed5-157">若要使用图形用户界面安装 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] ，请完成下列步骤：</span><span class="sxs-lookup"><span data-stu-id="a0ed5-157">To install [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] with the graphical user interface, complete the following steps:</span></span>

1.  <span data-ttu-id="a0ed5-158">运行 **SpPowerPivot.msi**。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-158">Run **SpPowerPivot.msi**.</span></span>

2.  <span data-ttu-id="a0ed5-159">在“欢迎”页上单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-159">Click **Next** on the Welcome page.</span></span>

3.  <span data-ttu-id="a0ed5-160">查看并接受许可协议，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-160">Review and accept the license agreement, then click **Next**.</span></span>

4.  <span data-ttu-id="a0ed5-161">在 "**功能选择**" 页上，默认情况下将选择所有功能。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-161">On the **Feature Selection** page, all of the features are selected by default.</span></span>

5.  <span data-ttu-id="a0ed5-162">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-162">Click **Next**.</span></span>

6.  <span data-ttu-id="a0ed5-163">单击 "**安装**" 以安装以完成安装。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-163">Click **Install** to install to finish the installation.</span></span>

### <a name="command-line-installation"></a><span data-ttu-id="a0ed5-164">命令行安装</span><span class="sxs-lookup"><span data-stu-id="a0ed5-164">Command Line Installation</span></span>
 <span data-ttu-id="a0ed5-165">对于命令行安装，请使用管理权限打开命令提示符，然后运行 **spPowerPivot.msi**。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-165">For a command-line installation, open a command prompt with administrative permissions, and then run the **spPowerPivot.msi**.</span></span> <span data-ttu-id="a0ed5-166">例如：</span><span class="sxs-lookup"><span data-stu-id="a0ed5-166">For example:</span></span>

 <span data-ttu-id="a0ed5-167">`Msiexec.exe /i SpPowerPivot.msi`.</span><span class="sxs-lookup"><span data-stu-id="a0ed5-167">`Msiexec.exe /i SpPowerPivot.msi`.</span></span>

 <span data-ttu-id="a0ed5-168">若要创建安装日志，请使用标准 MsiExec 日志记录开关。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-168">To create an installation log, use the standard MsiExec logging switches.</span></span> <span data-ttu-id="a0ed5-169">下面的示例使用 "v" 详细日志记录开关创建日志文件 "Install_Log.txt"。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-169">The following example creates the log file "Install_Log.txt" using the "v" verbose logging switch.</span></span>

```cmd
Msiexec.exe /i SpPowerPivot.msi /L v c:\test\Install_Log.txt
```

### <a name="quiet-command-line-installation-for-scripting"></a><span data-ttu-id="a0ed5-170">用于脚本编写的静默命令行安装</span><span class="sxs-lookup"><span data-stu-id="a0ed5-170">Quiet Command Line Installation for scripting</span></span>
 <span data-ttu-id="a0ed5-171">对于不会显示任何对话框或警告的 "静默" 安装，可以使用 **/q**或 **/quiet**开关。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-171">You can use the **/q** or **/quiet** switches for a "quiet" installation that will not display any dialogs or warnings.</span></span> <span data-ttu-id="a0ed5-172">如果您想要编写外接程序安装的脚本，静默安装将很有用。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-172">The quiet installation is useful if you want to script the installation of the add-in.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="a0ed5-173">如果你将 **/q** 开关用于无提示命令行安装，将不显示最终用户许可协议。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-173">If you use the **/q** switch for a silent command line installation, the end-user license agreement will not be displayed.</span></span> <span data-ttu-id="a0ed5-174">对此软件的使用受到许可协议控制并且由您负责遵守该许可协议，而与安装方法无关。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-174">Regardless of the installation method, the use of this software is governed by a license agreement and you are responsible for complying with the license agreement.</span></span>

#### <a name="to-perform-a-quiet-installation"></a><span data-ttu-id="a0ed5-175">执行静默安装</span><span class="sxs-lookup"><span data-stu-id="a0ed5-175">To perform a quiet installation</span></span>

1.  <span data-ttu-id="a0ed5-176">**使用管理员权限**打开命令提示符。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-176">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="a0ed5-177">运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="a0ed5-177">Run the following command:</span></span>

    ```cmd
    Msiexec.exe /i spPowerPivot.msi /q
    ```

### <a name="command-line-installation-to-include-specific-components"></a><span data-ttu-id="a0ed5-178">包含特定组件的命令行安装</span><span class="sxs-lookup"><span data-stu-id="a0ed5-178">Command Line Installation to include specific components</span></span>
 <span data-ttu-id="a0ed5-179">并不是所有 SharePoint 服务器上都需要 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] 配置工具，但建议在至少两台服务器上安装此配置工具，以便在需要时可以使用它。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-179">The [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] Configuration tool is not required on every SharePoint server, however it is recommended to install it on at least two servers so the configuration tool is available when you need it.</span></span>

 <span data-ttu-id="a0ed5-180">在安装 spPowerPivot.msi 时，可使用命令行选项来安装特定项目（如数据访问接口）而不安装 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] 配置工具。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-180">When you install the spPowerPivot.msi, you can use the command line options to install specific items, such as the data providers and not the [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] Configuration tool.</span></span> <span data-ttu-id="a0ed5-181">下面的命令行是安装该配置工具之外的所有组件的示例：</span><span class="sxs-lookup"><span data-stu-id="a0ed5-181">The following command line is an example of installing all components except the configuration tool:</span></span>

```
Msiexec /i spPowerPivot.msi AGREETOLICENSE="yes" ADDLOCAL=" SQL_OLAPDM,SQL_ADOMD,SQL_AMO,SQLAS_SP_Common"
```

|<span data-ttu-id="a0ed5-182">选项</span><span class="sxs-lookup"><span data-stu-id="a0ed5-182">Option</span></span>|<span data-ttu-id="a0ed5-183">说明</span><span class="sxs-lookup"><span data-stu-id="a0ed5-183">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="a0ed5-184">Analysis_Server_SP_addin</span><span class="sxs-lookup"><span data-stu-id="a0ed5-184">Analysis_Server_SP_addin</span></span>|<span data-ttu-id="a0ed5-185">PowerPivot 配置</span><span class="sxs-lookup"><span data-stu-id="a0ed5-185">PowerPivot Configuration</span></span>|
|<span data-ttu-id="a0ed5-186">SQL_OLAPDM</span><span class="sxs-lookup"><span data-stu-id="a0ed5-186">SQL_OLAPDM</span></span>|<span data-ttu-id="a0ed5-187">MSOLAP</span><span class="sxs-lookup"><span data-stu-id="a0ed5-187">MSOLAP</span></span>|
|<span data-ttu-id="a0ed5-188">SQL_ADOMD</span><span class="sxs-lookup"><span data-stu-id="a0ed5-188">SQL_ADOMD</span></span>|<span data-ttu-id="a0ed5-189">ADOMD.net 提供程序</span><span class="sxs-lookup"><span data-stu-id="a0ed5-189">ADOMD.net provider</span></span>|
|<span data-ttu-id="a0ed5-190">SQL_AMO</span><span class="sxs-lookup"><span data-stu-id="a0ed5-190">SQL_AMO</span></span>|<span data-ttu-id="a0ed5-191">AMO 提供程序</span><span class="sxs-lookup"><span data-stu-id="a0ed5-191">AMO provider</span></span>|
|<span data-ttu-id="a0ed5-192">SQLAS_SP_Common</span><span class="sxs-lookup"><span data-stu-id="a0ed5-192">SQLAS_SP_Common</span></span>|<span data-ttu-id="a0ed5-193">SharePoint 2013 的 Analysis Services 常用组件</span><span class="sxs-lookup"><span data-stu-id="a0ed5-193">Analysis Services common components for SharePoint 2013</span></span>|

##  <a name="deploy-the-sharepoint-solution-files-with-the-powerpivot-for-sharepoint-2013-configuration-tool"></a><a name="bkmk_deploy_solution"></a><span data-ttu-id="a0ed5-194">通过 PowerPivot for SharePoint 2013 配置工具部署 SharePoint 解决方案文件</span><span class="sxs-lookup"><span data-stu-id="a0ed5-194">Deploy the SharePoint Solution Files with the PowerPivot for SharePoint 2013 Configuration Tool</span></span>
 <span data-ttu-id="a0ed5-195">spPowerPivot.msi 复制到硬盘的三个文件均是 SharePoint 解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-195">Three of the files copied to the hard drive by spPowerPivot.msi are SharePoint solution files.</span></span> <span data-ttu-id="a0ed5-196">一个解决方案文件的作用域是 Web 应用程序级别，而其他文件的作用域是场级别。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-196">The scope of one solution file is the Web application level while the scope of the other files is the farm level.</span></span> <span data-ttu-id="a0ed5-197">这三个文件分别是：</span><span class="sxs-lookup"><span data-stu-id="a0ed5-197">The files are the following:</span></span>

-   `PowerPivotFarmSolution.wsp`

-   `PowerPivotFarm14Solution.wsp`

-   `PowerPivotWebApplicationSolution.wsp`

 <span data-ttu-id="a0ed5-198">解决方案文件将复制到以下文件夹：</span><span class="sxs-lookup"><span data-stu-id="a0ed5-198">The solution files are copied to the following folder:</span></span>

 `C:\Program Files\Microsoft SQL Server\120\Tools\PowerPivotTools\SPAddinConfiguration\Resources`

 <span data-ttu-id="a0ed5-199">在 .msi 安装之后，运行 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] 配置工具以在 SharePoint 场中配置和部署解决方案。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-199">Following the .msi installation, run the [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] Configuration Tool to configure and deploy the solutions in the SharePoint farm.</span></span>

### <a name="to-start-the-configuration-tool"></a><span data-ttu-id="a0ed5-200">启动配置工具</span><span class="sxs-lookup"><span data-stu-id="a0ed5-200">To start the configuration tool</span></span> 

 <span data-ttu-id="a0ed5-201">在 Windows 的 "开始" 屏幕上，键入 "power"，然后在 "应用" 搜索结果中，单击 " **PowerPivot for SharePoint 2013 配置**"。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-201">From the Windows Start screen type "power" and in the Apps search results, click **PowerPivot for SharePoint 2013 Configuration**.</span></span> <span data-ttu-id="a0ed5-202">请注意，搜索结果可能包含两个链接，因为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安装程序为 SharePoint 2010 和 SharePoint 2013 安装单独的 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 配置工具。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-202">Note that the search results may include two links because [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] setup installs separate [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] configuration tools for SharePoint 2010 and SharePoint 2013.</span></span> <span data-ttu-id="a0ed5-203">确保您启动了 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013 配置工具。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-203">Make sure you start the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013 Configuration tool.</span></span>

 <span data-ttu-id="a0ed5-204">![两个 powerpivot 配置工具](../../media/as-powerpivot-configtools-bothicons.gif "两个 powerpivot 配置工具")</span><span class="sxs-lookup"><span data-stu-id="a0ed5-204">![two powerpivot configuration tools](../../media/as-powerpivot-configtools-bothicons.gif "two powerpivot configuration tools")</span></span>

 <span data-ttu-id="a0ed5-205">**Or**</span><span class="sxs-lookup"><span data-stu-id="a0ed5-205">**Or**</span></span>

1.  <span data-ttu-id="a0ed5-206">转到 **“开始”**、 **“所有程序”**。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-206">Go to **Start**, **All Programs**.</span></span>

2.  <span data-ttu-id="a0ed5-207">单击 **“Microsoft SQL Server 2014”**。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-207">Click **Microsoft SQL Server 2014**.</span></span>

3.  <span data-ttu-id="a0ed5-208">单击 **“配置工具”**。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-208">Click **Configuration Tools**.</span></span>

4.  <span data-ttu-id="a0ed5-209">单击 **“PowerPivot for SharePoint 2013 配置”**。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-209">Click **PowerPivot for SharePoint 2013 Configuration**.</span></span>

 <span data-ttu-id="a0ed5-210">有关配置工具的详细信息，请参阅 [PowerPivot Configuration Tools](../../power-pivot-sharepoint/power-pivot-configuration-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-210">For more information on the configuration tool, see [PowerPivot Configuration Tools](../../power-pivot-sharepoint/power-pivot-configuration-tools.md).</span></span>

##  <a name="uninstall-or-repair-the-add-in"></a><a name="bkmk_remove_addin"></a><span data-ttu-id="a0ed5-211">卸载或修复外接程序</span><span class="sxs-lookup"><span data-stu-id="a0ed5-211">Uninstall or repair the add-in</span></span>

> [!CAUTION]
>  <span data-ttu-id="a0ed5-212">如果卸载 **spPowerPivot.msi** ，则将卸载数据访问接口和配置工具。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-212">If you uninstall **spPowerPivot.msi** the data providers and the configuration tool are uninstalled.</span></span> <span data-ttu-id="a0ed5-213">卸载数据访问接口将导致服务器无法连接到 PowerPivot。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-213">Uninstalling the data providers will cause the server to be unable to connect to PowerPivot.</span></span>

 <span data-ttu-id="a0ed5-214">您可通过下列方式之一卸载或修复 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="a0ed5-214">You can uninstall or repair [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] using one of the following methods:</span></span>

1.  <span data-ttu-id="a0ed5-215">**Windows 控制面板：** 选择 **“Microsoft SQL Server 2012 PowerPivot for SharePoint 2013”**。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-215">**Windows control panel:** Select **Microsoft SQL Server 2012 PowerPivot for SharePoint 2013**.</span></span> <span data-ttu-id="a0ed5-216">单击 **“卸载”** 或 **“修复”**。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-216">Click either **Uninstall** or **Repair**.</span></span>

2.  <span data-ttu-id="a0ed5-217">运行 spPowerPivot.msi 并选择 **“删除”** 选项或 **“修复”** 选项。</span><span class="sxs-lookup"><span data-stu-id="a0ed5-217">Run the spPowerPivot.msi and select the **Remove** option or the **Repair** option.</span></span>

 <span data-ttu-id="a0ed5-218">**命令行：** 若要使用命令行修复或卸载 PowerPivot for SharePoint 2013，请 **使用管理员权限** 打开命令提示符，然后运行下列命令之一：</span><span class="sxs-lookup"><span data-stu-id="a0ed5-218">**Command Line:** To repair or uninstall PowerPivot for SharePoint 2013 using the command line, open a command prompt **with administrator permissions** and run one of the following commands:</span></span>

-   <span data-ttu-id="a0ed5-219">若要修复，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="a0ed5-219">To Repair, run the following command:</span></span>

    ```cmd
    msiexec.exe /f spPowerPivot.msi
    ```

 <span data-ttu-id="a0ed5-220">或者</span><span class="sxs-lookup"><span data-stu-id="a0ed5-220">OR</span></span>

-   <span data-ttu-id="a0ed5-221">若要卸载，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="a0ed5-221">To uninstall, run the following command:</span></span>

    ```cmd
    msiexec.exe /uninstall spPowerPivot.msi
    ```
