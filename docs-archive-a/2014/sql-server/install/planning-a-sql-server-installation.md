---
title: 计划 SQL Server 安装 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- installing SQL Server, planning
ms.assetid: b1d56f2f-603f-48f2-b902-c715f14a6db9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e5b1dae9d2ef32298a9ddf2eeed1530e5ae97683
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589419"
---
# <a name="planning-a-sql-server-installation"></a><span data-ttu-id="534dd-102">计划 SQL Server 安装</span><span class="sxs-lookup"><span data-stu-id="534dd-102">Planning a SQL Server Installation</span></span>
  <span data-ttu-id="534dd-103">若要安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，请按下列步骤操作：</span><span class="sxs-lookup"><span data-stu-id="534dd-103">To install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], follow these steps:</span></span>  
  
-   <span data-ttu-id="534dd-104">查看 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装的安装要求、系统配置检查和安全注意事项。</span><span class="sxs-lookup"><span data-stu-id="534dd-104">Review installation requirements, system configuration checks, and security considerations for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span>  
  
-   <span data-ttu-id="534dd-105">运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序以安装或升级到更高版本。</span><span class="sxs-lookup"><span data-stu-id="534dd-105">Run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup to install or upgrade to a later version.</span></span>  
  
-   <span data-ttu-id="534dd-106">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="534dd-106">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilities to configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="534dd-107">无论使用哪种安装方法，您都需要作为个人或代表实体确认接受软件许可条款，除非您对于软件的使用受单独的协议（如 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 批量许可协议或与 ISV 或 OEM 之间的第三方协议）管辖。</span><span class="sxs-lookup"><span data-stu-id="534dd-107">Regardless of the installation method, you are required to confirm acceptance of the software license terms as an individual or on behalf of an entity, unless your use of the software is governed by a separate agreement such as a [!INCLUDE[msCoName](../../includes/msconame-md.md)] volume licensing agreement or a third-party agreement with an ISV or OEM.</span></span>  
  
 <span data-ttu-id="534dd-108">将在安装程序用户界面中显示许可条款，供您审核审阅和接受。</span><span class="sxs-lookup"><span data-stu-id="534dd-108">The license terms are displayed for review and acceptance in the Setup user interface.</span></span> <span data-ttu-id="534dd-109">使用 /Q 或 /QS 参数进行无人参与安装时，必须包含 /IAcceptSQLServerLicenseTerms 参数。</span><span class="sxs-lookup"><span data-stu-id="534dd-109">Unattended installations (using the /Q or /QS parameters) must include the /IAcceptSQLServerLicenseTerms parameter.</span></span> <span data-ttu-id="534dd-110">可以通过 [Microsoft Software License Terms](https://go.microsoft.com/fwlink/?LinkID=148209)（Microsoft 软件许可条款）单独查看许可条款。</span><span class="sxs-lookup"><span data-stu-id="534dd-110">You can review the license terms separately at [Microsoft Software License Terms](https://go.microsoft.com/fwlink/?LinkID=148209).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="534dd-111">根据您接收软件的方式（例如，通过 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 批量许可），您对软件的使用可能受其他条款和条件约束。</span><span class="sxs-lookup"><span data-stu-id="534dd-111">Depending on how you received the software (for example, through [!INCLUDE[msCoName](../../includes/msconame-md.md)] volume licensing), your use of the software may be subject to additional terms and conditions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="534dd-112">本节内容</span><span class="sxs-lookup"><span data-stu-id="534dd-112">In This Section</span></span>  
 [<span data-ttu-id="534dd-113">SQL Server 安装中的新增功能</span><span class="sxs-lookup"><span data-stu-id="534dd-113">What's New in SQL Server Installation</span></span>](../../../2014/sql-server/install/what-s-new-in-sql-server-installation.md)  
 <span data-ttu-id="534dd-114">本主题介绍有关这一版本的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中新增或改进的安装功能的详细信息。</span><span class="sxs-lookup"><span data-stu-id="534dd-114">This topic describes the details about the new or improved features of installation in this version of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 [<span data-ttu-id="534dd-115">安装 SQL Server 2014 的硬件和软件要求</span><span class="sxs-lookup"><span data-stu-id="534dd-115">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](hardware-and-software-requirements-for-installing-sql-server.md)  
 <span data-ttu-id="534dd-116">本主题列出了安装和运行 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]安装的最低硬件和软件要求。</span><span class="sxs-lookup"><span data-stu-id="534dd-116">This topic lists the minimum hardware and software requirements to install and run an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 [<span data-ttu-id="534dd-117">安装 SQL Server 的安全注意事项</span><span class="sxs-lookup"><span data-stu-id="534dd-117">Security Considerations for a SQL Server Installation</span></span>](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
 <span data-ttu-id="534dd-118">本主题介绍安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 前和安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之后应考虑采用的一些最佳安全做法。</span><span class="sxs-lookup"><span data-stu-id="534dd-118">This topic describes some security best practices that you should consider before you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and after you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="534dd-119">配置 Windows 服务帐户和权限</span><span class="sxs-lookup"><span data-stu-id="534dd-119">Configure Windows Service Accounts and Permissions</span></span>](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)  
 <span data-ttu-id="534dd-120">本主题介绍此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本中服务的默认配置，以及可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装过程中以及安装之后设置的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务的配置选项。</span><span class="sxs-lookup"><span data-stu-id="534dd-120">This topic describes the default configuration of services in this release of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and configuration options for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services that you can set during and after [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span>  
  
 [<span data-ttu-id="534dd-121">网络协议和网络库</span><span class="sxs-lookup"><span data-stu-id="534dd-121">Network Protocols and Network Libraries</span></span>](../../../2014/sql-server/install/network-protocols-and-network-libraries.md)  
 <span data-ttu-id="534dd-122">本主题介绍这一版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中网络协议的默认配置，以及可用的配置选项。</span><span class="sxs-lookup"><span data-stu-id="534dd-122">This topic describes the default configuration of network protocols in this release of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and the configuration options available.</span></span>  
  
 [<span data-ttu-id="534dd-123">使用 SQL Server 的多个版本和实例</span><span class="sxs-lookup"><span data-stu-id="534dd-123">Work with Multiple Versions and Instances of SQL Server</span></span>](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md)  
 <span data-ttu-id="534dd-124">本主题介绍安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的多个版本和实例时的注意事项。</span><span class="sxs-lookup"><span data-stu-id="534dd-124">This topic describes the considerations for installing multiple versions and instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="534dd-125">SQL Server 中的本地语言版本</span><span class="sxs-lookup"><span data-stu-id="534dd-125">Local Language Versions in SQL Server</span></span>](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
 <span data-ttu-id="534dd-126">本主题介绍了 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的本地化版本。</span><span class="sxs-lookup"><span data-stu-id="534dd-126">This topic describes about the localized versions of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="534dd-127">相关章节</span><span class="sxs-lookup"><span data-stu-id="534dd-127">Related Sections</span></span>  
 [<span data-ttu-id="534dd-128">安装 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="534dd-128">Install SQL Server 2014</span></span>](../../database-engine/install-windows/install-sql-server.md)  
 <span data-ttu-id="534dd-129">本节概要介绍用于安装 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的不同安装选项。</span><span class="sxs-lookup"><span data-stu-id="534dd-129">This section provides an overview of different installation options we have for installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 [<span data-ttu-id="534dd-130">安装 SQL Server 2014 BI 功能</span><span class="sxs-lookup"><span data-stu-id="534dd-130">Install SQL Server 2014 BI Features</span></span>](install-sql-server-business-intelligence-features.md)  
 <span data-ttu-id="534dd-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装文档中的本节说明如何安装属于 Microsoft BI 平台一部分的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="534dd-131">This section of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup documentation explains how to install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features that are part of the Microsoft BI platform.</span></span>  
  
 [<span data-ttu-id="534dd-132">升级到 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="534dd-132">Upgrade to SQL Server 2014</span></span>](../../database-engine/install-windows/upgrade-sql-server.md)  
 <span data-ttu-id="534dd-133">本节概要说明如何将以前的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本的实例升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="534dd-133">The section provides an overview of upgrading instances of previous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 [<span data-ttu-id="534dd-134">卸载 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="534dd-134">Uninstall SQL Server 2014</span></span>](uninstall-sql-server.md)  
 <span data-ttu-id="534dd-135">参照本节可以完全卸载 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的现有实例，并且对系统进行准备以便您可以重新安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="534dd-135">Refer this section to uninstall an existing instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] completely, and prepare the system so that you can reinstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="534dd-136">SQL Server 故障转移群集安装</span><span class="sxs-lookup"><span data-stu-id="534dd-136">SQL Server Failover Cluster Installation</span></span>](../failover-clusters/install/sql-server-failover-cluster-installation.md)  
 <span data-ttu-id="534dd-137">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装文档中的本节介绍了如何安装和配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集。</span><span class="sxs-lookup"><span data-stu-id="534dd-137">This section of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup documentation explains how to install, and configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="534dd-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="534dd-138">See Also</span></span>  
 <span data-ttu-id="534dd-139">[快速开始安装 SQL Server 2014](../../../2014/getting-started/quick-start-installation-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="534dd-139">[Quick-Start Installation of SQL Server 2014](../../../2014/getting-started/quick-start-installation-of-sql-server-2014.md) </span></span>  
 <span data-ttu-id="534dd-140">[从命令提示符安装 SQL Server 2014](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md) </span><span class="sxs-lookup"><span data-stu-id="534dd-140">[Install SQL Server 2014 from the Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md) </span></span>  
 <span data-ttu-id="534dd-141">[高可用性解决方案 (SQL Server)](../failover-clusters/high-availability-solutions-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="534dd-141">[High Availability Solutions &#40;SQL Server&#41;](../failover-clusters/high-availability-solutions-sql-server.md) </span></span>  
 <span data-ttu-id="534dd-142">[安装故障转移群集之前](../failover-clusters/install/before-installing-failover-clustering.md) </span><span class="sxs-lookup"><span data-stu-id="534dd-142">[Before Installing Failover Clustering](../failover-clusters/install/before-installing-failover-clustering.md) </span></span>  
 [<span data-ttu-id="534dd-143">使用安装向导 &#40;安装程序升级到 SQL Server 2014&#41;</span><span class="sxs-lookup"><span data-stu-id="534dd-143">Upgrade to SQL Server 2014 Using the Installation Wizard &#40;Setup&#41;</span></span>](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  
