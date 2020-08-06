---
title: 数据库要求 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: fe731839-c5c4-4884-bb6a-644eca28bb30
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b17c04db6805ea412b70644d2ee2c0b7da93b2a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590243"
---
# <a name="database-requirements-master-data-services"></a><span data-ttu-id="67273-102">数据库要求 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="67273-102">Database Requirements (Master Data Services)</span></span>
  <span data-ttu-id="67273-103">所有主数据都存储于 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 数据库中。</span><span class="sxs-lookup"><span data-stu-id="67273-103">All master data is stored in a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="67273-104">承载此数据库的计算机必须运行的实例 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="67273-104">The computer that hosts this database must run an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="67273-105">使用 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] 在本地或远程计算机上创建和配置 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="67273-105">Use [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] to create and configure the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database on either a local or a remote computer.</span></span> <span data-ttu-id="67273-106">如果您将数据库从一个环境移到另一个环境，则可以通过将 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web 服务和 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 与其新位置中的数据库相关联，在新环境中维护这些信息。</span><span class="sxs-lookup"><span data-stu-id="67273-106">If you move the database from one environment to another, you can maintain the information in a new environment by associating the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web service and [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] to the database in its new location.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="67273-107">您安装 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 组件的任何计算机必须具有许可证。</span><span class="sxs-lookup"><span data-stu-id="67273-107">Any computer on which you install components of [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] must be licensed.</span></span> <span data-ttu-id="67273-108">有关详细信息，请参阅“最终用户许可协议 (EULA)”。</span><span class="sxs-lookup"><span data-stu-id="67273-108">For more information, refer to the End User License Agreement (EULA).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67273-109">要求</span><span class="sxs-lookup"><span data-stu-id="67273-109">Requirements</span></span>  
 <span data-ttu-id="67273-110">在创建 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 数据库之前，请确保满足以下要求。</span><span class="sxs-lookup"><span data-stu-id="67273-110">Before you create a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database, ensure the following requirements are met.</span></span>  
  
### <a name="sql-server-edition"></a><span data-ttu-id="67273-111">SQL Server 版本</span><span class="sxs-lookup"><span data-stu-id="67273-111">SQL Server Edition</span></span>  
 <span data-ttu-id="67273-112">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 数据库可以承载在以下版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]上：</span><span class="sxs-lookup"><span data-stu-id="67273-112">The [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database can be hosted on the following editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="67273-113">Business Intelligence（64 位）x64</span><span class="sxs-lookup"><span data-stu-id="67273-113">Business Intelligence (64-bit) x64</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="67273-114">Enterprise（64 位）x64</span><span class="sxs-lookup"><span data-stu-id="67273-114">Enterprise (64-bit) x64</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="67273-115">Developer（64 位）x64</span><span class="sxs-lookup"><span data-stu-id="67273-115">Developer (64-bit) x64</span></span>  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="67273-116">Business Intelligence（64 位）x64</span><span class="sxs-lookup"><span data-stu-id="67273-116">Business Intelligence (64-bit) x64</span></span>  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="67273-117">Enterprise（64 位）x64 - 仅可从 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Enterprise 升级</span><span class="sxs-lookup"><span data-stu-id="67273-117">Enterprise (64-bit) x64 - Upgrade from [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Enterprise only</span></span>  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="67273-118">Developer（64 位）x64</span><span class="sxs-lookup"><span data-stu-id="67273-118">Developer (64-bit) x64</span></span>  
  
-   <span data-ttu-id="67273-119">Microsoft SQL Server 2008 R2 Enterprise（64 位）x64</span><span class="sxs-lookup"><span data-stu-id="67273-119">Microsoft SQL Server 2008 R2 Enterprise (64-bit) x64</span></span>  
  
-   <span data-ttu-id="67273-120">Microsoft SQL Server 2008 R2 Developer (64-bit) x64</span><span class="sxs-lookup"><span data-stu-id="67273-120">Microsoft SQL Server 2008 R2 Developer (64-bit) x64</span></span>  
  
 <span data-ttu-id="67273-121">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="67273-121">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
### <a name="operating-system"></a><span data-ttu-id="67273-122">操作系统</span><span class="sxs-lookup"><span data-stu-id="67273-122">Operating System</span></span>  
 <span data-ttu-id="67273-123">有关支持的 Windows 操作系统和其他要求的信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] ，请参阅[安装 SQL Server 2014 的硬件和软件要求](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="67273-123">For information about the supported Windows operating systems and other requirements for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)], see [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
### <a name="accounts-and-permissions"></a><span data-ttu-id="67273-124">帐户和权限</span><span class="sxs-lookup"><span data-stu-id="67273-124">Accounts and Permissions</span></span>  
  
|<span data-ttu-id="67273-125">类型</span><span class="sxs-lookup"><span data-stu-id="67273-125">Type</span></span>|<span data-ttu-id="67273-126">说明</span><span class="sxs-lookup"><span data-stu-id="67273-126">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="67273-127">用户帐户</span><span class="sxs-lookup"><span data-stu-id="67273-127">User account</span></span>|<span data-ttu-id="67273-128">在 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]中，可以使用 Windows 帐户或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例以承载 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="67273-128">In [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)], you can use a Windows account or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account to connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to host the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="67273-129">用户帐户必须属于 \*\*\*\* 实例上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span><span class="sxs-lookup"><span data-stu-id="67273-129">The user account must belong to the **sysadmin** server role on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="67273-130">有关 **sysadmin** 角色的详细信息，请参阅 [服务器级别角色](../../relational-databases/security/authentication-access/server-level-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="67273-130">For more information about the **sysadmin** role, see [Server-Level Roles](../../relational-databases/security/authentication-access/server-level-roles.md).</span></span>|  
|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] <span data-ttu-id="67273-131">管理员帐户</span><span class="sxs-lookup"><span data-stu-id="67273-131">administrator account</span></span>|<span data-ttu-id="67273-132">创建 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 数据库时，必须指定要作为 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 系统管理员的域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="67273-132">When you create a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database, you must specify a domain user account to be the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] system administrator.</span></span> <span data-ttu-id="67273-133">对于与此数据库关联的所有 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 应用程序，此用户可以更新所有模型以及所有功能区域中的所有数据。</span><span class="sxs-lookup"><span data-stu-id="67273-133">For all [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web applications associated with this database, this user can update all models and all data in all functional areas.</span></span> <span data-ttu-id="67273-134">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](../administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="67273-134">For more information, see [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md).</span></span>|  
  
### <a name="database-backup"></a><span data-ttu-id="67273-135">数据库备份</span><span class="sxs-lookup"><span data-stu-id="67273-135">Database Backup</span></span>  
 <span data-ttu-id="67273-136">最佳做法是每天在活动较少时进行完整数据库备份，并根据环境需要更频繁地备份事务日志。</span><span class="sxs-lookup"><span data-stu-id="67273-136">As a best practice, back up the full database daily at a time of low activity and back up transaction logs more frequently depending on the needs of your environment.</span></span> <span data-ttu-id="67273-137">有关数据库备份的详细信息，请参阅[备份概述 (SQL Server)](../../relational-databases/backup-restore/backup-overview-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="67273-137">For more information about database backups, see [Backup Overview &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67273-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="67273-138">See Also</span></span>  
 <span data-ttu-id="67273-139">[安装 Master Data Services](install-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="67273-139">[Install Master Data Services](install-master-data-services.md) </span></span>  
 <span data-ttu-id="67273-140">[创建 Master Data Services 数据库](create-a-master-data-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="67273-140">[Create a Master Data Services Database](create-a-master-data-services-database.md) </span></span>  
 <span data-ttu-id="67273-141">[Master Data Services 数据库](../master-data-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="67273-141">[Master Data Services Database](../master-data-services-database.md) </span></span>  
 <span data-ttu-id="67273-142">["连接到 Master Data Services 数据库" 对话框](../connect-to-a-master-data-services-database-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="67273-142">[Connect to a Master Data Services Database Dialog Box](../connect-to-a-master-data-services-database-dialog-box.md) </span></span>  
 [<span data-ttu-id="67273-143">创建数据库向导（Master Data Services 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="67273-143">Create Database Wizard &#40;Master Data Services Configuration Manager&#41;</span></span>](../create-database-wizard-master-data-services-configuration-manager.md)  
  
  
