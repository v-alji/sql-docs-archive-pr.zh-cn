---
title: 升级数据库引擎 | Microsoft Docs
ms.custom: ''
ms.date: 10/26/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- compatibility [SQL Server], databases
- compatibility levels [SQL Server], after upgrade
- Database Engine [SQL Server], upgrading
ms.assetid: 3c036813-36cf-4415-a0c9-248d0a433859
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ed13712678ab599e55b539d6226142b686106fe5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580355"
---
# <a name="upgrade-database-engine"></a><span data-ttu-id="79794-102">升级数据库引擎</span><span class="sxs-lookup"><span data-stu-id="79794-102">Upgrade Database Engine</span></span>
  <span data-ttu-id="79794-103">本主题提供了为升级过程进行准备和了解升级过程所需的信息，其中包括：</span><span class="sxs-lookup"><span data-stu-id="79794-103">This topic provides the information that you will need to prepare for and understand the upgrade process; it covers:</span></span>  
  
-   <span data-ttu-id="79794-104">已知升级问题。</span><span class="sxs-lookup"><span data-stu-id="79794-104">Known upgrade issues.</span></span>  
  
-   <span data-ttu-id="79794-105">升级前的任务和注意事项。</span><span class="sxs-lookup"><span data-stu-id="79794-105">Pre-upgrade tasks and considerations.</span></span>  
  
-   <span data-ttu-id="79794-106">有关升级 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的过程主题的链接。</span><span class="sxs-lookup"><span data-stu-id="79794-106">Links to procedural topics for upgrading the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="79794-107">将数据库迁移至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的过程主题的链接。</span><span class="sxs-lookup"><span data-stu-id="79794-107">Links to procedural topics for migrating databases to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="79794-108">故障转移群集的注意事项。</span><span class="sxs-lookup"><span data-stu-id="79794-108">Considerations for failover clusters.</span></span>  
  
-   <span data-ttu-id="79794-109">升级后的任务和注意事项。</span><span class="sxs-lookup"><span data-stu-id="79794-109">Post-upgrade tasks and considerations.</span></span>  
  
## <a name="known-upgrade-issues"></a><span data-ttu-id="79794-110">已知升级问题</span><span class="sxs-lookup"><span data-stu-id="79794-110">Known Upgrade issues</span></span>  
 <span data-ttu-id="79794-111">升级 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 之前，请查看 [SQL Server 数据库引擎的向后兼容性](../sql-server-database-engine-backward-compatibility.md)。</span><span class="sxs-lookup"><span data-stu-id="79794-111">Before upgrading the [!INCLUDE[ssDE](../../includes/ssde-md.md)], review [SQL Server Database Engine Backward Compatibility](../sql-server-database-engine-backward-compatibility.md).</span></span> <span data-ttu-id="79794-112">有关支持的升级方案和已知升级问题的信息，请参阅[支持的版本升级](supported-version-and-edition-upgrades.md)。</span><span class="sxs-lookup"><span data-stu-id="79794-112">For information about supported upgrade scenarios and upgrade known issues, see [Supported Version and Edition Upgrades](supported-version-and-edition-upgrades.md).</span></span> <span data-ttu-id="79794-113">有关其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件的向后兼容性的内容，请参阅[向后兼容性](../../getting-started/backward-compatibility.md)。</span><span class="sxs-lookup"><span data-stu-id="79794-113">For backward compatibility content for other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components, see [Backward Compatibility](../../getting-started/backward-compatibility.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="79794-114">在从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的某一版本升级到另一版本之前，请验证要升级到的版本是否支持当前使用的功能。</span><span class="sxs-lookup"><span data-stu-id="79794-114">Before you upgrade from one edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to another, verify that the functionality that you are currently using is supported in the edition to which you are upgrading.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="79794-115">在从 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise 版的之前版本升级到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时，在“Enterprise Edition：基于内核授予许可”和 Enterprise Edition 之间进行选择。</span><span class="sxs-lookup"><span data-stu-id="79794-115">When you upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] from a prior version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise edition, choose between Enterprise Edition: Core-based Licensing and Enterprise Edition.</span></span> <span data-ttu-id="79794-116">这些 Enterprise 版本仅在许可模式方面存在不同。</span><span class="sxs-lookup"><span data-stu-id="79794-116">These Enterprise editions differ only with respect to the licensing modes.</span></span> <span data-ttu-id="79794-117">有关详细信息，请参阅 [Compute Capacity Limits by Edition of SQL Server](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="79794-117">For more information, see [Compute Capacity Limits by Edition of SQL Server](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).</span></span>  
  
## <a name="pre-upgrade-checklist"></a><span data-ttu-id="79794-118">升级准备一览表</span><span class="sxs-lookup"><span data-stu-id="79794-118">Pre-Upgrade Checklist</span></span>  
 <span data-ttu-id="79794-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序支持从早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进行升级。</span><span class="sxs-lookup"><span data-stu-id="79794-119">Upgrading [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from an earlier version is supported by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup program.</span></span> <span data-ttu-id="79794-120">也可以迁移早期 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本中的数据库。</span><span class="sxs-lookup"><span data-stu-id="79794-120">You can also migrate databases from previous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions.</span></span> <span data-ttu-id="79794-121">可以从一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例迁移至同一台计算机上的另一个实例，也可以从另一台计算机上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例迁移。</span><span class="sxs-lookup"><span data-stu-id="79794-121">Migration can be from one [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to another on the same computer, or from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance on another computer.</span></span> <span data-ttu-id="79794-122">迁移选项包括使用复制数据库向导、备份和还原功能、使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 导入和导出向导，以及批量导出/批量导入方法。</span><span class="sxs-lookup"><span data-stu-id="79794-122">Migration options include use of the Copy Database Wizard, Backup and restore functionality, use of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Import and Export Wizard, and bulk export/bulk import methods.</span></span>  
  
 <span data-ttu-id="79794-123">升级 [!INCLUDE[ssDE](../../includes/ssde-md.md)]之前，请先查看以下主题：</span><span class="sxs-lookup"><span data-stu-id="79794-123">Before upgrading the [!INCLUDE[ssDE](../../includes/ssde-md.md)], review the following:</span></span>  
  
-   <span data-ttu-id="79794-124">阅读 [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="79794-124">Review [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
-   <span data-ttu-id="79794-125">阅读 [Check Parameters for the System Configuration Checker](check-parameters-for-the-system-configuration-checker.md)。</span><span class="sxs-lookup"><span data-stu-id="79794-125">Review [Check Parameters for the System Configuration Checker](check-parameters-for-the-system-configuration-checker.md).</span></span>  
  
-   <span data-ttu-id="79794-126">阅读 [Security Considerations for a SQL Server Installation](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)。</span><span class="sxs-lookup"><span data-stu-id="79794-126">Review [Security Considerations for a SQL Server Installation](../../sql-server/install/security-considerations-for-a-sql-server-installation.md).</span></span>  
  
-   <span data-ttu-id="79794-127">查看[支持的版本升级](supported-version-and-edition-upgrades.md)。</span><span class="sxs-lookup"><span data-stu-id="79794-127">Review [Supported Version and Edition Upgrades](supported-version-and-edition-upgrades.md).</span></span>  
  
-   <span data-ttu-id="79794-128">查看[使用升级顾问来准备升级](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)。</span><span class="sxs-lookup"><span data-stu-id="79794-128">Review [Use Upgrade Advisor to Prepare for Upgrades](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).</span></span>  
  
-   <span data-ttu-id="79794-129">查看[使用分布式重播实用工具准备升级](../../sql-server/install/use-the-distributed-replay-utility-to-prepare-for-upgrades.md)。</span><span class="sxs-lookup"><span data-stu-id="79794-129">Review [Use the Distributed Replay Utility to Prepare for Upgrades](../../sql-server/install/use-the-distributed-replay-utility-to-prepare-for-upgrades.md).</span></span>  
  
-   <span data-ttu-id="79794-130">查看 [SQL Server 数据库引擎的向后兼容性](../sql-server-database-engine-backward-compatibility.md)。</span><span class="sxs-lookup"><span data-stu-id="79794-130">Review [SQL Server Database Engine Backward Compatibility](../sql-server-database-engine-backward-compatibility.md).</span></span>  
  
-   <span data-ttu-id="79794-131">查看[迁移查询计划](change-the-database-compatibility-mode-and-use-the-query-store.md)。</span><span class="sxs-lookup"><span data-stu-id="79794-131">Review [Migrate Query Plans](change-the-database-compatibility-mode-and-use-the-query-store.md).</span></span>  
  
 <span data-ttu-id="79794-132">请在升级 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之前检查下列问题并做出更改：</span><span class="sxs-lookup"><span data-stu-id="79794-132">Review the following issues and make changes before you upgrade [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="79794-133">当升级在 MSX/TSX 关系中登记了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例时，应在升级主服务器之前升级目标服务器。</span><span class="sxs-lookup"><span data-stu-id="79794-133">When upgrading instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is enlisted in MSX/TSX relationships, upgrade target servers before you upgrade master servers.</span></span> <span data-ttu-id="79794-134">如果您在升级目标服务器之前升级主服务器，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理将无法连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的主实例。</span><span class="sxs-lookup"><span data-stu-id="79794-134">If you upgrade master servers before target servers, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent will not be able to connect to master instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="79794-135">从 64 位版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 升级到 64 位版本的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]时，必须在升级 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 之前先升级 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="79794-135">When upgrading from a 64-bit edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to a 64-bit edition of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you must upgrade [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] before you upgrade the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="79794-136">如有必要，请备份要升级的实例中的所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库文件，以便可以还原这些文件。</span><span class="sxs-lookup"><span data-stu-id="79794-136">Back up all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database files from the instance to be upgraded, so that you can restore them, if it is required.</span></span>  
  
-   <span data-ttu-id="79794-137">在要升级的数据库上运行适当的数据库控制台命令 (DBCC)，以确保这些数据库处于一致状态。</span><span class="sxs-lookup"><span data-stu-id="79794-137">Run the appropriate Database Console Commands (DBCC) on databases to be upgraded to ensure that they are in a consistent state.</span></span>  
  
-   <span data-ttu-id="79794-138">估计升级 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件以及用户数据库所需的磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="79794-138">Estimate the disk space that is required to upgrade [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components, in addition to user databases.</span></span> <span data-ttu-id="79794-139">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件所需磁盘空间的信息，请参阅[安装 SQL Server 2014 的硬件和软件要求](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="79794-139">For disk space that is required by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components, see [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
-   <span data-ttu-id="79794-140">确保将现有的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统数据库（master、model、msdb 和 tempdb）配置为自动增长，并确保它们具有足够的硬盘空间。</span><span class="sxs-lookup"><span data-stu-id="79794-140">Ensure that existing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases - master, model, msdb, and tempdb - are configured to autogrow, and ensure that they have sufficient hard disk space.</span></span>  
  
-   <span data-ttu-id="79794-141">确保所有数据库服务器的 master 数据库中都有登录信息。</span><span class="sxs-lookup"><span data-stu-id="79794-141">Ensure that all database servers have logon information in the master database.</span></span> <span data-ttu-id="79794-142">这对还原数据库很重要，因为 master 数据库中有系统登录信息。</span><span class="sxs-lookup"><span data-stu-id="79794-142">This is important for restoring a database, as system logon information resides in master.</span></span>  
  
-   <span data-ttu-id="79794-143">禁用所有启动存储过程，因为升级过程在升级 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例时将停止然后再启动服务。</span><span class="sxs-lookup"><span data-stu-id="79794-143">Disable all startup stored procedures, as the upgrade process will stop and start services on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance being upgraded.</span></span> <span data-ttu-id="79794-144">在启动时进行处理的存储过程可能会阻塞升级过程。</span><span class="sxs-lookup"><span data-stu-id="79794-144">Stored procedures processed at startup time might block the upgrade process.</span></span>  
  
-   <span data-ttu-id="79794-145">确保复制正在进行，然后停止复制。</span><span class="sxs-lookup"><span data-stu-id="79794-145">Make sure that Replication is current and then stop Replication.</span></span>  
  
-   <span data-ttu-id="79794-146">退出所有应用程序，包括所有依赖 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的服务。</span><span class="sxs-lookup"><span data-stu-id="79794-146">Quit all applications, including all services that have [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dependencies.</span></span> <span data-ttu-id="79794-147">如果有本地应用程序连接到要升级的实例，则升级可能会失败。</span><span class="sxs-lookup"><span data-stu-id="79794-147">Upgrade might fail if local applications are connected to the instance being upgraded.</span></span>  
  
-   <span data-ttu-id="79794-148">如果使用数据库镜像，请参阅[在升级服务器实例时最大限度地减少镜像数据库的停机时间](../database-mirroring/upgrading-mirrored-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="79794-148">If you use Database Mirroring, see [Minimize Downtime for Mirrored Databases When Upgrading Server Instances](../database-mirroring/upgrading-mirrored-instances.md).</span></span>  
  
## <a name="upgrading-the-database-engine"></a><span data-ttu-id="79794-149">升级数据库引擎</span><span class="sxs-lookup"><span data-stu-id="79794-149">Upgrading the Database Engine</span></span>  
 <span data-ttu-id="79794-150">可以用升级版本覆盖 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更高版本的安装。</span><span class="sxs-lookup"><span data-stu-id="79794-150">You can overwrite an installation of [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later with a version upgrade.</span></span> <span data-ttu-id="79794-151">如果在运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序时检测到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的早期版本，将升级所有早期 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 程序文件，并且保留早期 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中存储的所有数据。</span><span class="sxs-lookup"><span data-stu-id="79794-151">If an earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is detected when you run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup, all previous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] program files are upgraded, and all data stored in the previous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance is preserved.</span></span> <span data-ttu-id="79794-152">此外，计算机上早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书将保持不变。</span><span class="sxs-lookup"><span data-stu-id="79794-152">In addition, earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online will remain intact on the computer.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="79794-153">运行 SQL Server 2014 安装程序时，作为运行预升级检查的一部分，将停止并重启 SQL Server 实例。</span><span class="sxs-lookup"><span data-stu-id="79794-153">When running the SQL Server 2014 setup program, the SQL Server instance is stopped and restarted as part of running the pre-upgrade checks.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="79794-154">在升级 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]后，早期的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例将被覆盖，在计算机中不再存在。</span><span class="sxs-lookup"><span data-stu-id="79794-154">When you upgrade [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the previous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance will be overwritten and will no longer exist on your computer.</span></span> <span data-ttu-id="79794-155">因此在升级前，请备份 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库以及与早期的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例相关的其他对象。</span><span class="sxs-lookup"><span data-stu-id="79794-155">Before upgrading, back up [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases and other objects associated with the previous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="79794-156">可以使用 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 安装向导升级 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="79794-156">You can upgrade the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard.</span></span>  
  
### <a name="database-compatibility-level-after-upgrade"></a><span data-ttu-id="79794-157">升级后的数据库兼容级别</span><span class="sxs-lookup"><span data-stu-id="79794-157">Database Compatibility Level After Upgrade</span></span>  
 <span data-ttu-id="79794-158">`tempdb` `model` `msdb` 升级后，、和**资源**数据库的兼容级别将设置为120。</span><span class="sxs-lookup"><span data-stu-id="79794-158">The compatibility levels of the `tempdb`, `model`, `msdb` and **Resource** databases are set to 120 after upgrade.</span></span> <span data-ttu-id="79794-159">`master` 系统数据库保留它在升级之前的兼容级别。</span><span class="sxs-lookup"><span data-stu-id="79794-159">The `master` system database retains the compatibility level it had before upgrade.</span></span>  
  
 <span data-ttu-id="79794-160">如果升级前用户数据库的兼容级别为 100 或更高，升级后将保持相应级别。</span><span class="sxs-lookup"><span data-stu-id="79794-160">If the compatibility level of a user database was 100 or higher before the upgrade, it remains the same after upgrade.</span></span> <span data-ttu-id="79794-161">如果升级前兼容级别为 90，则在升级后的数据库中，兼容级别将设置为 100，该级别为 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]支持的最低兼容级别。</span><span class="sxs-lookup"><span data-stu-id="79794-161">If the compatibility level was 90 before upgrade, in the upgraded database, the compatibility level is set to 100, which is the lowest supported compatibility level in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="79794-162">新的用户数据库将继承 `model` 数据库的兼容级别。</span><span class="sxs-lookup"><span data-stu-id="79794-162">New user databases will inherit the compatibility level of the `model` database.</span></span>  
  
## <a name="migrating-databases"></a><span data-ttu-id="79794-163">迁移数据库</span><span class="sxs-lookup"><span data-stu-id="79794-163">Migrating Databases</span></span>  
 <span data-ttu-id="79794-164">可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的备份和还原功能或分离和附加功能将用户数据库移动到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="79794-164">You can move user databases to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using backup and restore or detach and attach functionalities in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="79794-165">有关详细信息，请参阅[通过备份和还原来复制数据库](../../relational-databases/databases/copy-databases-with-backup-and-restore.md)或[数据库分离和附加 (SQL Server)](../../relational-databases/databases/database-detach-and-attach-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="79794-165">For more information, see [Copy Databases with Backup and Restore](../../relational-databases/databases/copy-databases-with-backup-and-restore.md) or [Database Detach and Attach &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="79794-166">数据库在源服务器和目的服务器上的名称相同时，不能进行移动或复制。</span><span class="sxs-lookup"><span data-stu-id="79794-166">A database that has the identical name on both source and destination servers cannot be moved or copied.</span></span> <span data-ttu-id="79794-167">在这种情况下，它被标记为“已存在”。</span><span class="sxs-lookup"><span data-stu-id="79794-167">In this case, it will be noted as "Already exists."</span></span>  
  
 <span data-ttu-id="79794-168">有关详细信息，请参阅 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="79794-168">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="after-upgrading-the-database-engine"></a><span data-ttu-id="79794-169">升级数据库引擎后</span><span class="sxs-lookup"><span data-stu-id="79794-169">After Upgrading the Database Engine</span></span>  
 <span data-ttu-id="79794-170">升级 [!INCLUDE[ssDE](../../includes/ssde-md.md)]后，请完成以下任务：</span><span class="sxs-lookup"><span data-stu-id="79794-170">After upgrading the [!INCLUDE[ssDE](../../includes/ssde-md.md)], complete the following tasks:</span></span>  
  
-   <span data-ttu-id="79794-171">重新注册服务器。</span><span class="sxs-lookup"><span data-stu-id="79794-171">Re-register your servers.</span></span> <span data-ttu-id="79794-172">有关注册服务器的详细信息，请参阅[注册服务器](../../ssms/register-servers/register-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="79794-172">For more information about registering servers, see [Register Servers](../../ssms/register-servers/register-servers.md).</span></span>  
  
-   <span data-ttu-id="79794-173">重新填充全文目录以便确保查询结果中的语义一致性。</span><span class="sxs-lookup"><span data-stu-id="79794-173">Re-populate full-text catalogs to ensure semantic consistency in query results.</span></span>  
  
     [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="79794-174">将安装新的断字符以供全文和语义搜索使用。</span><span class="sxs-lookup"><span data-stu-id="79794-174">installs new word breakers for use by Full-Text and Semantic Search.</span></span> <span data-ttu-id="79794-175">在建立索引时和查询时均使用断字符。</span><span class="sxs-lookup"><span data-stu-id="79794-175">The word breakers are used both at indexing time and at query time.</span></span> <span data-ttu-id="79794-176">如果您没有重新生成全文目录，搜索结果可能不一致。</span><span class="sxs-lookup"><span data-stu-id="79794-176">If you do not rebuild the full-text catalogs, your search results may be inconsistent.</span></span> <span data-ttu-id="79794-177">如果您发出查找某一短语的全文查询和当前断字符，该短语是由以前的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本中的断字符以不同方式进行断字的，则可能不会检索包含该短语的文档或行。</span><span class="sxs-lookup"><span data-stu-id="79794-177">If you issue a full-text query that looks for a phrase that is broken differently by the word breaker in a previous version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the current word breaker, a document or row containing the phrase might not be retrieved.</span></span> <span data-ttu-id="79794-178">其原因在于，建立了索引的短语是使用与正使用的查询不同的逻辑进行断字的。</span><span class="sxs-lookup"><span data-stu-id="79794-178">This is because the indexed phrases were broken using different logic than the query is using.</span></span> <span data-ttu-id="79794-179">解决方法是使用新的断字符来重新填充（重新生成）全文目录，以便索引时行为和查询时行为完全相同。</span><span class="sxs-lookup"><span data-stu-id="79794-179">The solution is to repopulate (rebuild) the full-text catalogs with the new word breakers so that index time and query time behavior are identical.</span></span>  
  
     <span data-ttu-id="79794-180">有关详细信息，请参阅 [sp_fulltext_catalog (Transact SQL)](/sql/relational-databases/system-stored-procedures/sp-fulltext-catalog-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="79794-180">For more information, see [sp_fulltext_catalog &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-catalog-transact-sql).</span></span>  
  
-   <span data-ttu-id="79794-181">配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装。</span><span class="sxs-lookup"><span data-stu-id="79794-181">Configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span> <span data-ttu-id="79794-182">为了减少系统的可攻击外围应用， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 有选择地安装和启用了一些关键服务和功能。</span><span class="sxs-lookup"><span data-stu-id="79794-182">To reduce the attackable surface area of a system, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] selectively installs and enables key services and features.</span></span>  
  
-   <span data-ttu-id="79794-183">验证或删除 USE PLAN 提示，这些提示由 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 生成并应用于对已分区表和索引的查询。</span><span class="sxs-lookup"><span data-stu-id="79794-183">Validate or remove USE PLAN hints that are generated by [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and applied to queries on partitioned tables and indexes.</span></span>  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="79794-184">更改了对已分区表和索引的查询方式。</span><span class="sxs-lookup"><span data-stu-id="79794-184">changes the way queries on partitioned tables and indexes are processed.</span></span> <span data-ttu-id="79794-185">如果已分区对象将 USE PLAN 提示用于 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 生成的计划，针对这些对象的查询可能会包含不可在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中使用的计划。</span><span class="sxs-lookup"><span data-stu-id="79794-185">Queries on partitioned objects that use the USE PLAN hint for a plan that is generated by [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] might contain a plan that is not usable in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="79794-186">建议升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]后，执行下列过程。</span><span class="sxs-lookup"><span data-stu-id="79794-186">We recommend the following procedures after you upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
     <span data-ttu-id="79794-187">**如果在查询中直接指定 USE PLAN 提示：**</span><span class="sxs-lookup"><span data-stu-id="79794-187">**When the USE PLAN hint is specified directly in a query:**</span></span>  
  
    1.  <span data-ttu-id="79794-188">从查询删除 USE PLAN 提示。</span><span class="sxs-lookup"><span data-stu-id="79794-188">Remove the USE PLAN hint from the query.</span></span>  
  
    2.  <span data-ttu-id="79794-189">测试查询。</span><span class="sxs-lookup"><span data-stu-id="79794-189">Test the query.</span></span>  
  
    3.  <span data-ttu-id="79794-190">如果优化器未选择相应的计划并优化查询，请考虑使用所需的查询计划指定 USE PLAN 提示。</span><span class="sxs-lookup"><span data-stu-id="79794-190">If the optimizer does not select an appropriate plan, tune the query, and then consider specifying the USE PLAN hint with the desired query plan.</span></span>  
  
     <span data-ttu-id="79794-191">**如果在计划指南中指定 USE PLAN 提示：**</span><span class="sxs-lookup"><span data-stu-id="79794-191">**When the USE PLAN hint is specified in a plan guide:**</span></span>  
  
    1.  <span data-ttu-id="79794-192">使用 sys.fn_validate_plan_guide 函数来检查计划指南的有效性。</span><span class="sxs-lookup"><span data-stu-id="79794-192">Use the sys.fn_validate_plan_guide function to check the validity of the plan guide.</span></span> <span data-ttu-id="79794-193">或者，可以使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]中的 Plan Guide Unsuccessful 事件检查是否存在无效计划。</span><span class="sxs-lookup"><span data-stu-id="79794-193">Alternatively, you can check for invalid plans by using the Plan Guide Unsuccessful event in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
    2.  <span data-ttu-id="79794-194">如果计划指南无效，则删除该计划指南。</span><span class="sxs-lookup"><span data-stu-id="79794-194">If the plan guide is not valid, drop the plan guide.</span></span> <span data-ttu-id="79794-195">如果优化器未选择相应的计划并优化查询，则考虑使用所需查询计划指定 USE PLAN 提示。</span><span class="sxs-lookup"><span data-stu-id="79794-195">If the optimizer does not select an appropriate plan, tune the query, and then consider specifying the USE PLAN hint with the query plan that you want.</span></span>  
  
     <span data-ttu-id="79794-196">当在计划指南中指定 USE PLAN 提示时，无效的计划将不会导致查询失败。</span><span class="sxs-lookup"><span data-stu-id="79794-196">A plan that is not valid will not cause the query to fail when the USE PLAN hint is specified in a plan guide.</span></span> <span data-ttu-id="79794-197">相反，仍可在不使用 USE PLAN 提示的情况下对计划进行编译。</span><span class="sxs-lookup"><span data-stu-id="79794-197">Instead, the query is compiled without using the USE PLAN hint.</span></span>  
  
 <span data-ttu-id="79794-198">在升级前标记为启用或禁用全文的数据库，在升级后也将保持该状态。</span><span class="sxs-lookup"><span data-stu-id="79794-198">Any databases that were marked full-text enabled or disabled before the upgrade will maintain that status after upgrade.</span></span> <span data-ttu-id="79794-199">升级后，将为所有启用全文的数据库自动重新生成并填充全文目录。</span><span class="sxs-lookup"><span data-stu-id="79794-199">After the upgrade, the full-text catalogs will be rebuilt and populated automatically for all full-text enabled databases.</span></span> <span data-ttu-id="79794-200">此项操作既耗时又耗费资源。</span><span class="sxs-lookup"><span data-stu-id="79794-200">This is a time-consuming and resource-consuming operation.</span></span> <span data-ttu-id="79794-201">可以通过运行以下语句暂停全文索引操作：</span><span class="sxs-lookup"><span data-stu-id="79794-201">You can pause the full-text indexing operation temporarily by running the following statement:</span></span>  
  
```  
EXEC sp_fulltext_service 'pause_indexing', 1;  
```  
  
 <span data-ttu-id="79794-202">若要恢复全文索引填充，请运行以下语句：</span><span class="sxs-lookup"><span data-stu-id="79794-202">To resume full-text index population, run the following statement:</span></span>  
  
```  
EXEC sp_fulltext_service 'pause_indexing', 0;  
```  
  
## <a name="see-also"></a><span data-ttu-id="79794-203">另请参阅</span><span class="sxs-lookup"><span data-stu-id="79794-203">See Also</span></span>  
 <span data-ttu-id="79794-204">[支持的版本升级](supported-version-and-edition-upgrades.md) </span><span class="sxs-lookup"><span data-stu-id="79794-204">[Supported Version and Edition Upgrades](supported-version-and-edition-upgrades.md) </span></span>  
 <span data-ttu-id="79794-205">[使用 SQL Server 的多个版本和实例](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="79794-205">[Work with Multiple Versions and Instances of SQL Server](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md) </span></span>  
 <span data-ttu-id="79794-206">[向后兼容性](../../getting-started/backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="79794-206">[Backward Compatibility](../../getting-started/backward-compatibility.md) </span></span>  
 [<span data-ttu-id="79794-207">升级复制的数据库</span><span class="sxs-lookup"><span data-stu-id="79794-207">Upgrade Replicated Databases</span></span>](upgrade-replicated-databases.md)  
  
  
