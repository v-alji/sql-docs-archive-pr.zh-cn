---
title: Reporting Services 的备份和还原操作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- databases [Reporting Services], backing up
- databases [Reporting Services], restoring
- databases [Reporting Services], moving
- backing up databases [Reporting Services]
- moving databases
- restoring databases [Reporting Services]
- files [Reporting Services], restoring
- files [Reporting Services], backing up
ms.assetid: 157bc376-ab72-4c99-8bde-7b12db70843a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e895733457fe0c8892294540bbe8345cb121f2a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589448"
---
# <a name="backup-and-restore-operations-for-reporting-services"></a><span data-ttu-id="99275-102">Reporting Services 的备份和还原操作</span><span class="sxs-lookup"><span data-stu-id="99275-102">Backup and Restore Operations for Reporting Services</span></span>
  <span data-ttu-id="99275-103">本主题概述 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装中使用的所有数据文件，并介绍应在何时以及如何备份这些文件。</span><span class="sxs-lookup"><span data-stu-id="99275-103">This topic provides an overview of all data files used in a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation and describes when and how you should back up the files.</span></span> <span data-ttu-id="99275-104">为报表服务器数据库文件制定备份和还原计划是恢复策略中最重要的一部分。</span><span class="sxs-lookup"><span data-stu-id="99275-104">Developing a backup and restore plan for the report server database files is the most important part of a recovery strategy.</span></span> <span data-ttu-id="99275-105">但是，更全面的恢复策略应包括备份加密密钥、自定义程序集或扩展插件、配置文件，以及报表和模型的源文件。</span><span class="sxs-lookup"><span data-stu-id="99275-105">However, a more comprehensive recovery strategy would include backups of the encryption keys, custom assemblies or extensions, configuration files, and source files for reports and models.</span></span>  
  
 <span data-ttu-id="99275-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 本机模式 | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="99275-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native Mode | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint Mode</span></span>  
  
 <span data-ttu-id="99275-107">备份和还原操作通常用于移动所有或部分 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装：</span><span class="sxs-lookup"><span data-stu-id="99275-107">Backup and restore operations are often used to move all or part of a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation:</span></span>  
  
-   <span data-ttu-id="99275-108">如果只移动报表服务器数据库，则可以使用备份和还原或附加和分离功能在其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中重新定位数据库。</span><span class="sxs-lookup"><span data-stu-id="99275-108">If you are moving just the report server databases, you can use backup and restore or attach and detach to relocate the databases on a different [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="99275-109">有关详细信息，请参阅 [将报表服务器数据库移至其他计算机（SSRS 本机模式）](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="99275-109">For more information, see [Moving the Report Server Databases to Another Computer &#40;SSRS Native Mode&#41;](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md).</span></span>  
  
-   <span data-ttu-id="99275-110">将 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装移到新计算机的过程称为迁移。</span><span class="sxs-lookup"><span data-stu-id="99275-110">Moving a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation to a new computer is called a migration.</span></span> <span data-ttu-id="99275-111">在迁移安装时，需要运行安装程序以安装新的报表服务器实例，然后将实例数据复制到新计算机上。</span><span class="sxs-lookup"><span data-stu-id="99275-111">When you migrate an installation, you run Setup to install a new report server instance and then copy instance data to the new computer.</span></span> <span data-ttu-id="99275-112">有关迁移 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装的详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="99275-112">For more information about migrating a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation, see the following topics:</span></span>  
  
    -   [<span data-ttu-id="99275-113">升级和迁移 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="99275-113">Upgrade and Migrate Reporting Services</span></span>](upgrade-and-migrate-reporting-services.md)  
  
    -   [<span data-ttu-id="99275-114">迁移 Reporting Services 安装（SharePoint 模式）</span><span class="sxs-lookup"><span data-stu-id="99275-114">Migrate a Reporting Services Installation &#40;SharePoint Mode&#41;</span></span>](migrate-a-reporting-services-installation-sharepoint-mode.md)  
  
    -   [<span data-ttu-id="99275-115">迁移 Reporting Services 安装（本机模式）</span><span class="sxs-lookup"><span data-stu-id="99275-115">Migrate a Reporting Services Installation &#40;Native Mode&#41;</span></span>](migrate-a-reporting-services-installation-native-mode.md)  
  
## <a name="backing-up-the-report-server-databases"></a><span data-ttu-id="99275-116">备份和还原报表服务器数据库</span><span class="sxs-lookup"><span data-stu-id="99275-116">Backing Up the Report Server Databases</span></span>  
 <span data-ttu-id="99275-117">由于报表服务器是无状态服务器，因此所有应用程序数据都存储于在 **实例上运行的** reportserver **和** reportservertempdb [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 数据库中。</span><span class="sxs-lookup"><span data-stu-id="99275-117">Because a report server is a stateless server, all application data is stored in the **reportserver** and **reportservertempdb** databases that run on a [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] instance.</span></span> <span data-ttu-id="99275-118">可以使用支持的备份 **数据库的方法之一备份** reportserver **和** reportservertempdb [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="99275-118">You can backup the **reportserver** and **reportservertempdb** databases using one of the supported methods for backing up [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span> <span data-ttu-id="99275-119">特定于报表服务器数据库的建议包括以下几项：</span><span class="sxs-lookup"><span data-stu-id="99275-119">Recommendations that are specific to the report server databases include the following:</span></span>  
  
-   <span data-ttu-id="99275-120">应使用完整恢复模式备份 **reportserver** 数据库。</span><span class="sxs-lookup"><span data-stu-id="99275-120">Use the full recovery model to backup the **reportserver** database.</span></span>  
  
-   <span data-ttu-id="99275-121">应使用简单恢复模式备份 **reportservertempdb** 数据库。</span><span class="sxs-lookup"><span data-stu-id="99275-121">Use the simple recovery model to backup the **reportservertempdb** database.</span></span>  
  
-   <span data-ttu-id="99275-122">可以对每个数据库使用不同的备份计划。</span><span class="sxs-lookup"><span data-stu-id="99275-122">You can use different backup schedules for each database.</span></span> <span data-ttu-id="99275-123">备份 **reportservertempdb** 只是为了在发生硬件故障时避免重新创建该数据库。</span><span class="sxs-lookup"><span data-stu-id="99275-123">The only reason to backup the **reportservertempdb** is to avoid having to recreate it if there is a hardware failure.</span></span> <span data-ttu-id="99275-124">在发生硬件故障时，不必恢复 **reportservertempdb**中的数据，但需要使用表结构。</span><span class="sxs-lookup"><span data-stu-id="99275-124">In the event of hardware failure, it is not necessary to recover the data in **reportservertempdb**, but you do need the table structure.</span></span> <span data-ttu-id="99275-125">如果 **reportservertempdb**丢失，重新获得它的唯一方法是重新创建报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="99275-125">If you lose **reportservertempdb**, the only way to get it back is to recreate the report server database.</span></span> <span data-ttu-id="99275-126">如果重新创建 **reportservertempdb**，应使其名称与主报表服务器数据库的名称相同，这一点非常重要。</span><span class="sxs-lookup"><span data-stu-id="99275-126">If you recreate the **reportservertempdb**, it is important that it have the same name as the primary report server database.</span></span>  
  
 <span data-ttu-id="99275-127">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 关系数据库的备份和恢复的详细信息，请参阅 [SQL Server 数据库的备份和还原](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="99275-127">For more information about backup and recovery of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] relational databases, see [Back Up and Restore of SQL Server Databases](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="99275-128">如果您的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 报表服务器处于 SharePoint 模式下，则会有其他一些数据库需要加以注意，包括 SharePoint 配置数据库和 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 警报数据库。</span><span class="sxs-lookup"><span data-stu-id="99275-128">If your [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] report server is in SharePoint mode, there are additional databases to be concerned with, including SharePoint configuration databases and the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] alerting database.</span></span> <span data-ttu-id="99275-129">在 SharePoint 模式下，对于每个 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序将创建三个数据库。</span><span class="sxs-lookup"><span data-stu-id="99275-129">In SharePoint mode, three databases are created for each [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="99275-130">**reportserver**、 **reportservertempdb**和 **dataalerting** 数据库。</span><span class="sxs-lookup"><span data-stu-id="99275-130">The **reportserver**, **reportservertempdb**, and **dataalerting** databases.</span></span> <span data-ttu-id="99275-131">有关详细信息，请参阅 [备份和还原 Reporting Services SharePoint 服务应用程序](../backup-and-restore-reporting-services-sharepoint-service-applications.md)</span><span class="sxs-lookup"><span data-stu-id="99275-131">For more information see [Backup and Restore Reporting Services SharePoint Service Applications](../backup-and-restore-reporting-services-sharepoint-service-applications.md)</span></span>  
  
## <a name="backing-up-the-encryption-keys"></a><span data-ttu-id="99275-132">备份加密密钥</span><span class="sxs-lookup"><span data-stu-id="99275-132">Backing Up the Encryption Keys</span></span>  
 <span data-ttu-id="99275-133">首次配置 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装时，应备份加密密钥。</span><span class="sxs-lookup"><span data-stu-id="99275-133">You should backup the encryption keys when you configure a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation for the first time.</span></span> <span data-ttu-id="99275-134">此外，任何时候更改服务帐户标识或重命名计算机时，都应备份密钥。</span><span class="sxs-lookup"><span data-stu-id="99275-134">You should also backup the keys any time you change the identity of the service accounts or rename the computer.</span></span> <span data-ttu-id="99275-135">有关详细信息，请参阅 [Back Up and Restore Reporting Services Encryption Keys](ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="99275-135">For more information, see [Back Up and Restore Reporting Services Encryption Keys](ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).</span></span> <span data-ttu-id="99275-136">对于 SharePoint 模式报表服务器，请参阅[管理 Reporting Services SharePoint 服务应用程序](../manage-a-reporting-services-sharepoint-service-application.md)的 "密钥管理" 部分。</span><span class="sxs-lookup"><span data-stu-id="99275-136">For SharePoint mode report servers, see the "Key Management" section of [Manage a Reporting Services SharePoint Service Application](../manage-a-reporting-services-sharepoint-service-application.md).</span></span>  
  
## <a name="backing-up-the-configuration-files"></a><span data-ttu-id="99275-137">备份配置文件</span><span class="sxs-lookup"><span data-stu-id="99275-137">Backing Up the Configuration Files</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="99275-138">使用配置文件来存储应用程序设置。</span><span class="sxs-lookup"><span data-stu-id="99275-138">uses configuration files to store application settings.</span></span> <span data-ttu-id="99275-139">首次配置服务器时和部署任何自定义扩展插件之后，都应备份文件。</span><span class="sxs-lookup"><span data-stu-id="99275-139">You should backup the files when you first configure the server and after you deploy any custom extensions.</span></span> <span data-ttu-id="99275-140">要备份的文件包括：</span><span class="sxs-lookup"><span data-stu-id="99275-140">Files to back up include:</span></span>  
  
-   <span data-ttu-id="99275-141">RSReportServer.config</span><span class="sxs-lookup"><span data-stu-id="99275-141">Rsreportserver.config</span></span>  
  
-   <span data-ttu-id="99275-142">Rssvrpolicy.config</span><span class="sxs-lookup"><span data-stu-id="99275-142">Rssvrpolicy.config</span></span>  
  
-   <span data-ttu-id="99275-143">Rsmgrpolicy.config</span><span class="sxs-lookup"><span data-stu-id="99275-143">Rsmgrpolicy.config</span></span>  
  
-   <span data-ttu-id="99275-144">Reportingservicesservice.exe.config</span><span class="sxs-lookup"><span data-stu-id="99275-144">Reportingservicesservice.exe.config</span></span>  
  
-   <span data-ttu-id="99275-145">报表服务器和报表管理器 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 应用程序的 Web.config</span><span class="sxs-lookup"><span data-stu-id="99275-145">Web.config for both the Report Server and Report Manager [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] applications</span></span>  
  
-   <span data-ttu-id="99275-146">针对 的 Machine.config [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99275-146">Machine.config for [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]</span></span>  
  
## <a name="backing-up-data-files"></a><span data-ttu-id="99275-147">备份数据文件</span><span class="sxs-lookup"><span data-stu-id="99275-147">Backing Up Data Files</span></span>  
 <span data-ttu-id="99275-148">备份在报表设计器和模型设计器中创建和维护的文件。</span><span class="sxs-lookup"><span data-stu-id="99275-148">Backup the files that you create and maintain in Report Designer and Model Designer.</span></span> <span data-ttu-id="99275-149">这些文件包括报表定义 (.rdl) 文件、报表模型 (.smdl) 文件、共享数据源 (.rds) 文件、数据视图 (.dv) 文件、数据源 (.ds) 文件、报表服务器项目 (.rptproj) 文件以及报表解决方案 (.sln) 文件。</span><span class="sxs-lookup"><span data-stu-id="99275-149">These include report definition (.rdl) files, report model (.smdl) files, shared data source (.rds) files, data view (.dv) files, data source (.ds) files, report server project (.rptproj) files, and report solution (.sln) files.</span></span>  
  
 <span data-ttu-id="99275-150">请记住备份为管理或部署任务创建的所有脚本文件 (.rss)。</span><span class="sxs-lookup"><span data-stu-id="99275-150">Remember to backup any script files (.rss) that you created for administration or deployment tasks.</span></span>  
  
 <span data-ttu-id="99275-151">确认具有所使用的所有自定义扩展插件和自定义程序集的备份副本。</span><span class="sxs-lookup"><span data-stu-id="99275-151">Verify that you have a backup copy of any custom extensions and custom assemblies you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99275-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="99275-152">See Also</span></span>  
 <span data-ttu-id="99275-153">[报表服务器数据库 &#40;SSRS 本机模式&#41;](../report-server/report-server-database-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="99275-153">[Report Server Database &#40;SSRS Native Mode&#41;](../report-server/report-server-database-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="99275-154">[Reporting Services 配置文件](../report-server/reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="99275-154">[Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) </span></span>  
 <span data-ttu-id="99275-155">[rskeymgmt 实用工具 &#40;SSRS&#41;](../tools/rskeymgmt-utility-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="99275-155">[rskeymgmt Utility &#40;SSRS&#41;](../tools/rskeymgmt-utility-ssrs.md) </span></span>  
 <span data-ttu-id="99275-156">[通过备份和还原来复制数据库](../../relational-databases/databases/copy-databases-with-backup-and-restore.md) </span><span class="sxs-lookup"><span data-stu-id="99275-156">[Copy Databases with Backup and Restore](../../relational-databases/databases/copy-databases-with-backup-and-restore.md) </span></span>  
 <span data-ttu-id="99275-157">[&#40;SSRS 本机模式下管理报表服务器数据库&#41;](../report-server/administer-a-report-server-database-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="99275-157">[Administer a Report Server Database &#40;SSRS Native Mode&#41;](../report-server/administer-a-report-server-database-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="99275-158">配置和管理加密密钥（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="99275-158">Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-manage-encryption-keys.md)  
  
  
