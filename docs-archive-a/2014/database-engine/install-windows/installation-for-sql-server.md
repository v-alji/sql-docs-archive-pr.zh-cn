---
title: SQL Server 2014 的安装 |Microsoft Docs
ms.custom: ''
ms.date: 09/09/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
f1_keywords:
- sql12.portal.Installation.f1
helpviewer_keywords:
- installing SQL Server, initial installation
- installation [SQL Server]
- initial installation [SQL Server]
ms.assetid: edd75f68-dc62-4479-a596-57ce8ad632e5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 62630400f276b00de8acfa875244558cdb39e47b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688151"
---
# <a name="installation-for-sql-server-2014"></a><span data-ttu-id="e7ff7-102">SQL Server 2014 安装</span><span class="sxs-lookup"><span data-stu-id="e7ff7-102">Installation for SQL Server 2014</span></span>
 ## <a name="download-sql-server-2014-express"></a>[<span data-ttu-id="e7ff7-103">下载 SQL Server 2014 Express</span><span class="sxs-lookup"><span data-stu-id="e7ff7-103">Download SQL Server 2014 Express</span></span>](http://www.hanselman.com/blog/DownloadSQLServerExpress.aspx)
  <span data-ttu-id="e7ff7-104">**感谢您在一个位置收集所有安装程序包链接的[Hanselman](http://www.hanselman.com/) 。**</span><span class="sxs-lookup"><span data-stu-id="e7ff7-104">**Thank you to [Scott Hanselman](http://www.hanselman.com/) for collecting all of the installer package links in one place!**</span></span>
  
  <span data-ttu-id="e7ff7-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装向导提供一个功能树以用来安装所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件：</span><span class="sxs-lookup"><span data-stu-id="e7ff7-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard provides a single feature tree to install all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components:</span></span>  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]  
  
-   [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]  
  
-   <span data-ttu-id="e7ff7-106">管理工具</span><span class="sxs-lookup"><span data-stu-id="e7ff7-106">Management tools</span></span>  
  
-   <span data-ttu-id="e7ff7-107">连接组件</span><span class="sxs-lookup"><span data-stu-id="e7ff7-107">Connectivity components</span></span>  
  
 <span data-ttu-id="e7ff7-108">您可以单独安装每个组件，也可以选择上面列出的组件的组合。</span><span class="sxs-lookup"><span data-stu-id="e7ff7-108">You can install each component individually or select a combination of the components listed above.</span></span> <span data-ttu-id="e7ff7-109">若要在中提供的版本和组件中做出最佳选择 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅[SQL Server 2014 的版本和组件](../../sql-server/editions-and-components-of-sql-server-2016.md)和[SQL Server 2014 各个版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="e7ff7-109">To make the best choice among the editions and components available in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Editions and Components of SQL Server 2014](../../sql-server/editions-and-components-of-sql-server-2016.md) and [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="e7ff7-110">有 32 位和 64 位两种版本可用。</span><span class="sxs-lookup"><span data-stu-id="e7ff7-110">is available in 32-bit and 64-bit editions.</span></span>
 
 <span data-ttu-id="e7ff7-111">**试用：**</span><span class="sxs-lookup"><span data-stu-id="e7ff7-111">**Try it out:**</span></span>  
  
-   <span data-ttu-id="e7ff7-112">已经拥有 Azure 帐户？</span><span class="sxs-lookup"><span data-stu-id="e7ff7-112">Have an Azure account?</span></span>  <span data-ttu-id="e7ff7-113">然后转到**[此处](https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2016RTMEnterpriseWindowsServer2012R2)** 以启动已安装 SQL Server 2014 Service Pack 1 (SP1) 的虚拟机。</span><span class="sxs-lookup"><span data-stu-id="e7ff7-113">Then go **[Here](https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2016RTMEnterpriseWindowsServer2012R2)** to spin up a Virtual Machine with SQL Server 2014 Service Pack 1 (SP1) already installed.</span></span> <span data-ttu-id="e7ff7-114">有关 SQL Server 2014 (SP1) 的详细信息，请参阅[SQL Server 2014 Service Pack 1 版本信息](https://support.microsoft.com/kb/3058865)。</span><span class="sxs-lookup"><span data-stu-id="e7ff7-114">For more information on SQL Server 2014 (SP1), see [SQL Server 2014 Service Pack 1 release information](https://support.microsoft.com/kb/3058865).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e7ff7-115">本节内容</span><span class="sxs-lookup"><span data-stu-id="e7ff7-115">In This Section</span></span>  
 <span data-ttu-id="e7ff7-116">无论使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装向导还是命令提示符安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，安装都包括下列步骤：</span><span class="sxs-lookup"><span data-stu-id="e7ff7-116">Regardless of whether you use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard or the command prompt to install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Setup involves the following steps:</span></span>  
  
 [<span data-ttu-id="e7ff7-117">计划 SQL Server 安装</span><span class="sxs-lookup"><span data-stu-id="e7ff7-117">Planning a SQL Server Installation</span></span>](../../sql-server/install/planning-a-sql-server-installation.md)  
 <span data-ttu-id="e7ff7-118">说明如何为安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]而准备计算机：</span><span class="sxs-lookup"><span data-stu-id="e7ff7-118">Describes how to prepare your computer for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="e7ff7-119">硬件和软件要求。</span><span class="sxs-lookup"><span data-stu-id="e7ff7-119">Hardware and software requirements.</span></span>  
  
-   <span data-ttu-id="e7ff7-120">系统配置检查器的要求和妨碍性问题。</span><span class="sxs-lookup"><span data-stu-id="e7ff7-120">System Configuration Checker requirements and blocking issues.</span></span>  
  
-   <span data-ttu-id="e7ff7-121">安全注意事项。</span><span class="sxs-lookup"><span data-stu-id="e7ff7-121">Security considerations.</span></span>  
  
 [<span data-ttu-id="e7ff7-122">安装 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="e7ff7-122">Install SQL Server 2014</span></span>](install-sql-server.md)  
 <span data-ttu-id="e7ff7-123">说明 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的安装选项。</span><span class="sxs-lookup"><span data-stu-id="e7ff7-123">Describes installation options for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="e7ff7-124">升级到 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="e7ff7-124">Upgrade to SQL Server 2014</span></span>](upgrade-sql-server.md)  
 <span data-ttu-id="e7ff7-125">介绍用于升级到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的选项。</span><span class="sxs-lookup"><span data-stu-id="e7ff7-125">Describes options for upgrading to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="e7ff7-126">卸载 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="e7ff7-126">Uninstall SQL Server 2014</span></span>](../../sql-server/install/uninstall-sql-server.md)  
 <span data-ttu-id="e7ff7-127">说明卸载 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]的过程。</span><span class="sxs-lookup"><span data-stu-id="e7ff7-127">Describes procedures to uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].</span></span>  
  
 [<span data-ttu-id="e7ff7-128">SQL Server 故障转移群集安装</span><span class="sxs-lookup"><span data-stu-id="e7ff7-128">SQL Server Failover Cluster Installation</span></span>](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 <span data-ttu-id="e7ff7-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装文档中的本节介绍了如何安装和配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集。</span><span class="sxs-lookup"><span data-stu-id="e7ff7-129">This section of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup documentation explains how to install, and configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster.</span></span>  
  
 [<span data-ttu-id="e7ff7-130">安装 SQL Server 2014 BI 功能</span><span class="sxs-lookup"><span data-stu-id="e7ff7-130">Install SQL Server 2014 BI Features</span></span>](../../sql-server/install/install-sql-server-business-intelligence-features.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e7ff7-131">Microsoft BI 平台的部分功能包括： [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]，以及用于创建或使用分析数据的若干客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="e7ff7-131">features that are part of the Microsoft BI platform include [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and several client applications used for creating or working with analytical data.</span></span> <span data-ttu-id="e7ff7-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装文档中的本节说明如何安装 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 和 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e7ff7-132">This section of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup documentation explains how to install [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e7ff7-133">相关章节</span><span class="sxs-lookup"><span data-stu-id="e7ff7-133">Related Sections</span></span>  
 [<span data-ttu-id="e7ff7-134">安装操作指南主题</span><span class="sxs-lookup"><span data-stu-id="e7ff7-134">Installation How-to Topics</span></span>](../../sql-server/install/installation-how-to-topics.md)  
 <span data-ttu-id="e7ff7-135">提供 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的各种安装方法的过程主题链接，这些方法包括使用安装向导、命令提示符、配置文件或 SysPrep。</span><span class="sxs-lookup"><span data-stu-id="e7ff7-135">Provides links to procedural topics for installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] from the installation wizard, from the command prompt, by using configuration files, and by using SysPrep.</span></span>  
  
 [<span data-ttu-id="e7ff7-136">通过 SharePoint &#40;PowerPivot 和 Reporting Services 安装 SQL Server BI 功能&#41;</span><span class="sxs-lookup"><span data-stu-id="e7ff7-136">Install SQL Server BI Features with SharePoint &#40;PowerPivot and Reporting Services&#41;</span></span>](../../sql-server/install/install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md)  
 <span data-ttu-id="e7ff7-137">本节介绍如何在 SharePoint 环境中安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="e7ff7-137">This section explains how to install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features in a SharePoint environment.</span></span> <span data-ttu-id="e7ff7-138">它标识对于特定版本的 SharePoint，提供了哪些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="e7ff7-138">It identifies which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features are available given a specific version and edition of SharePoint.</span></span> <span data-ttu-id="e7ff7-139">本节还包含在 SharePoint 模式下安装 PowerPivot for SharePoint 和 Reporting Services 的过程。</span><span class="sxs-lookup"><span data-stu-id="e7ff7-139">It also includes installation procedures for PowerPivot for SharePoint and Reporting Services in SharePoint mode.</span></span>  
  
 [<span data-ttu-id="e7ff7-140">安装 SQL Server 示例和示例数据库</span><span class="sxs-lookup"><span data-stu-id="e7ff7-140">Installing SQL Server Samples and Sample Databases</span></span>](https://sqlserversamples.codeplex.com/)  
 <span data-ttu-id="e7ff7-141">说明如何安装和配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 示例和示例数据库。</span><span class="sxs-lookup"><span data-stu-id="e7ff7-141">Describes how to install and configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] samples and sample databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7ff7-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7ff7-142">See Also</span></span>  
 <span data-ttu-id="e7ff7-143">[SQL Server 安装中的新增功能](../../sql-server/install/what-s-new-in-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="e7ff7-143">[What's New in SQL Server Installation](../../sql-server/install/what-s-new-in-sql-server-installation.md) </span></span>  
 [<span data-ttu-id="e7ff7-144">安装 SQL Server 2014 的硬件和软件要求</span><span class="sxs-lookup"><span data-stu-id="e7ff7-144">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
