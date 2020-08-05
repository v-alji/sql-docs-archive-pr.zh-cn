---
title: 升级 Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- upgrading databases
- databases [Analysis Services], upgrading
- installing Analysis Services, side-by-side installations
- Analysis Services upgrades
- Analysis Services upgrades, about upgrading Analysis Services
- SSAS, database migration
- upgrading Analysis Services
- installing Analysis Services, upgrading
- SSAS, upgrading
ms.assetid: a131d329-386e-4470-aaa9-ffcde4e5ec0c
author: Minewiskan
ms.author: owend
ms.openlocfilehash: 78bf7f27233bcfd46bc1f189324eddc72adcc961
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580358"
---
# <a name="upgrade-analysis-services"></a><span data-ttu-id="35197-102">升级 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="35197-102">Upgrade Analysis Services</span></span>
  <span data-ttu-id="35197-103">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序升级 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="35197-103">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup to upgrade [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="35197-104">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在 SharePoint 模式下升级的详细信息，请参阅[Upgrade PowerPivot for SharePoint](upgrade-power-pivot-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="35197-104">For detailed information on upgrading [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in SharePoint mode, see [Upgrade PowerPivot for SharePoint](upgrade-power-pivot-for-sharepoint.md).</span></span> <span data-ttu-id="35197-105">有关升级现有 SQL Server 实例的详细信息，请参阅[使用安装向导 &#40;安装&#41;升级到 SQL Server 2014 ](upgrade-sql-server-using-the-installation-wizard-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="35197-105">For more information about upgrading an existing SQL Server instance, see [Upgrade to SQL Server 2014 Using the Installation Wizard &#40;Setup&#41;](upgrade-sql-server-using-the-installation-wizard-setup.md).</span></span>  
  
## <a name="known-upgrade-issues"></a><span data-ttu-id="35197-106">已知升级问题</span><span class="sxs-lookup"><span data-stu-id="35197-106">Known Upgrade Issues</span></span>  
 <span data-ttu-id="35197-107">升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]之前，请先查看以下内容：</span><span class="sxs-lookup"><span data-stu-id="35197-107">Before upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], review the following:</span></span>  
  
-   <span data-ttu-id="35197-108">[SQL Server 2014 发行说明](https://go.microsoft.com/fwlink/?LinkID=296445)。</span><span class="sxs-lookup"><span data-stu-id="35197-108">[SQL Server 2014 Release Notes](https://go.microsoft.com/fwlink/?LinkID=296445).</span></span>  
  
-   <span data-ttu-id="35197-109">若要了解哪些 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 特性和功能已中止、不推荐使用或已更改，请参阅[Analysis Services 向后兼容性](https://docs.microsoft.com/analysis-services/analysis-services-backward-compatibility)。</span><span class="sxs-lookup"><span data-stu-id="35197-109">To learn which [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] features and functionality have been discontinued, deprecated, or changed see [Analysis Services Backward Compatibility](https://docs.microsoft.com/analysis-services/analysis-services-backward-compatibility).</span></span>  
  
## <a name="pre-upgrade-checklist"></a><span data-ttu-id="35197-110">升级准备一览表</span><span class="sxs-lookup"><span data-stu-id="35197-110">Pre-Upgrade Checklist</span></span>  
 <span data-ttu-id="35197-111">升级之前，请先查看以下信息：</span><span class="sxs-lookup"><span data-stu-id="35197-111">Before upgrading, review the following information:</span></span>  
  
-   [<span data-ttu-id="35197-112">支持的版本和版本升级</span><span class="sxs-lookup"><span data-stu-id="35197-112">Supported Version and Edition Upgrades</span></span>](supported-version-and-edition-upgrades.md)  
  
-   [<span data-ttu-id="35197-113">安装 SQL Server 2014 的硬件和软件要求</span><span class="sxs-lookup"><span data-stu-id="35197-113">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
-   [<span data-ttu-id="35197-114">系统配置检查器的检查参数</span><span class="sxs-lookup"><span data-stu-id="35197-114">Check Parameters for the System Configuration Checker</span></span>](check-parameters-for-the-system-configuration-checker.md)  
  
-   [<span data-ttu-id="35197-115">安装 SQL Server 的安全注意事项</span><span class="sxs-lookup"><span data-stu-id="35197-115">Security Considerations for a SQL Server Installation</span></span>](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
-   [<span data-ttu-id="35197-116">备份和还原 Analysis Services 数据库</span><span class="sxs-lookup"><span data-stu-id="35197-116">Backup and Restore of Analysis Services Databases</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases)  
  
-   [<span data-ttu-id="35197-117">使用升级顾问来准备升级</span><span class="sxs-lookup"><span data-stu-id="35197-117">Use Upgrade Advisor to Prepare for Upgrades</span></span>](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)  
  
## <a name="upgrading-analysis-services"></a><span data-ttu-id="35197-118">升级 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="35197-118">Upgrading Analysis Services</span></span>  
 <span data-ttu-id="35197-119">您可以选择几种方法之一来升级服务器和数据：</span><span class="sxs-lookup"><span data-stu-id="35197-119">You can choose from several approaches to upgrade server and data:</span></span>  
  
-   <span data-ttu-id="35197-120">**就地升级**将使用程序文件替换现有的程序文件 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="35197-120">An **in-place upgrade** replaces the existing program files with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] program files.</span></span> <span data-ttu-id="35197-121">数据库保持在相同的位置中。</span><span class="sxs-lookup"><span data-stu-id="35197-121">Databases remain in the same location.</span></span> <span data-ttu-id="35197-122">程序文件夹将更新以反映新名称。</span><span class="sxs-lookup"><span data-stu-id="35197-122">Program folders are updated to reflect the new name.</span></span>  
  
-   <span data-ttu-id="35197-123">**并行升级**是 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在具有现有 Analysis Services 实例的同一台计算机上的新安装。</span><span class="sxs-lookup"><span data-stu-id="35197-123">A **side-by-side upgrade** is a new installation of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on the same computer that has an existing Analysis Services instance.</span></span> <span data-ttu-id="35197-124">可以将数据库移动到同一台计算机的新实例上，然后卸载旧版本（如果您不再继续使用这个旧版本）。</span><span class="sxs-lookup"><span data-stu-id="35197-124">You can move databases over to the new instance on the same computer, and then uninstall the old version if you no longer use it.</span></span>  
  
-   <span data-ttu-id="35197-125">可以也在新的硬件上安装 Analysis Services，然后将现有数据库迁移到该服务器。</span><span class="sxs-lookup"><span data-stu-id="35197-125">You can also install Analysis Services on new hardware and then migrate existing databases to that server.</span></span>  
  
## <a name="in-place-upgrade"></a><span data-ttu-id="35197-126">就地升级</span><span class="sxs-lookup"><span data-stu-id="35197-126">In-place Upgrade</span></span>  
 <span data-ttu-id="35197-127">您可以将的现有实例升级 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 到， [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 并且作为升级过程的一部分，将现有数据库从旧实例自动迁移到新实例。</span><span class="sxs-lookup"><span data-stu-id="35197-127">You can upgrade an existing instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and, as part of the upgrade process, automatically migrate existing databases from the old instance to the new instance.</span></span> <span data-ttu-id="35197-128">因为元数据和二进制数据在两个版本之间兼容，因此升级之后您可以保留该数据而不必手动迁移该数据。</span><span class="sxs-lookup"><span data-stu-id="35197-128">Because the metadata and binary data is compatible between the two versions, you will retain the data after you upgrade and you do not have to manually migrate the data.</span></span>  
  
 <span data-ttu-id="35197-129">若要升级现有实例，请运行安装程序并将现有实例的名称指定为新实例的名称。</span><span class="sxs-lookup"><span data-stu-id="35197-129">To upgrade an existing instance, run Setup and specify the name of the existing instance as the name of the new instance.</span></span>  
  
## <a name="upgrading-databases"></a><span data-ttu-id="35197-130">升级数据库</span><span class="sxs-lookup"><span data-stu-id="35197-130">Upgrading Databases</span></span>  
 <span data-ttu-id="35197-131">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的之前版本中创建的数据库基于较旧的数据库兼容性级别设置在升级的服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="35197-131">Databases that were created in previous versions of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] run on the upgraded server under an older database compatibility level setting.</span></span> <span data-ttu-id="35197-132">在以下版本中创建的数据库的数据库兼容性级别为 105。</span><span class="sxs-lookup"><span data-stu-id="35197-132">Databases created in the following versions, have a database compatibility level of 105.</span></span> <span data-ttu-id="35197-133">如果您要使用要求较新数据库兼容性级别的功能，则可以更改该兼容性级别。</span><span class="sxs-lookup"><span data-stu-id="35197-133">You can change the compatibility level if you want to use features that require a newer database compatibility level.</span></span> <span data-ttu-id="35197-134">否则，您可以使用原始设置在升级的服务器上运行数据库。</span><span class="sxs-lookup"><span data-stu-id="35197-134">Otherwise, you can run the databases on the upgraded server using the original settings.</span></span> <span data-ttu-id="35197-135">有关详细信息，请参阅[设置多维数据库 &#40;Analysis Services&#41;的兼容级别](https://docs.microsoft.com/analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services)。</span><span class="sxs-lookup"><span data-stu-id="35197-135">For more information, see [Set the Compatibility Level of a Multidimensional Database &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services).</span></span>  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="35197-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="35197-136">See Also</span></span>  
 <span data-ttu-id="35197-137">[SQL Server 2014 的各个版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="35197-137">[Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span></span>  
 <span data-ttu-id="35197-138">[计划 SQL Server 安装](../../sql-server/install/planning-a-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="35197-138">[Planning a SQL Server Installation](../../sql-server/install/planning-a-sql-server-installation.md) </span></span>  
 <span data-ttu-id="35197-139">[了解 Microsoft OLAP 体系结构](https://docs.microsoft.com/analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture) </span><span class="sxs-lookup"><span data-stu-id="35197-139">[Understanding Microsoft OLAP Architecture](https://docs.microsoft.com/analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture) </span></span>  
 <span data-ttu-id="35197-140">[升级 PowerPivot for SharePoint](upgrade-power-pivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="35197-140">[Upgrade PowerPivot for SharePoint](upgrade-power-pivot-for-sharepoint.md) </span></span>  
 <span data-ttu-id="35197-141">[在多维和数据挖掘模式下安装 Analysis Services](../../sql-server/install/install-analysis-services-in-multidimensional-and-data-mining-mode.md) </span><span class="sxs-lookup"><span data-stu-id="35197-141">[Install Analysis Services in Multidimensional and Data Mining Mode](../../sql-server/install/install-analysis-services-in-multidimensional-and-data-mining-mode.md) </span></span>  
 [<span data-ttu-id="35197-142">PowerPivot for SharePoint 2010 安装</span><span class="sxs-lookup"><span data-stu-id="35197-142">PowerPivot for SharePoint 2010 Installation</span></span>](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
