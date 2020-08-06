---
title: 还原 master 数据库 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- master database [SQL Server], restoring
ms.assetid: c83d802c-e84e-4458-b3ca-173d9ba32f73
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7c9cb078b7af60fc5e060bcb144fc9cbaee8ecf7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589155"
---
# <a name="restore-the-master-database-transact-sql"></a><span data-ttu-id="d879b-102">还原 master 数据库 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d879b-102">Restore the master Database (Transact-SQL)</span></span>
  <span data-ttu-id="d879b-103">本主题介绍如何从完整数据库备份还原 **master** 数据库。</span><span class="sxs-lookup"><span data-stu-id="d879b-103">This topic explains how to restore the **master** database from a full database backup.</span></span>  
  
### <a name="to-restore-the-master-database"></a><span data-ttu-id="d879b-104">还原 master 数据库</span><span class="sxs-lookup"><span data-stu-id="d879b-104">To restore the master database</span></span>  
  
1.  <span data-ttu-id="d879b-105">在单用户模式下启动服务器实例。</span><span class="sxs-lookup"><span data-stu-id="d879b-105">Start the server instance in single-user mode.</span></span>  
  
     <span data-ttu-id="d879b-106">有关如何指定单一用户启动参数 ( **-m**) 的信息，请参阅[配置服务器启动选项（SQL Server 配置管理器）](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md)。</span><span class="sxs-lookup"><span data-stu-id="d879b-106">For information about how to specify the single-user startup parameter (**-m**), see [Configure Server Startup Options &#40;SQL Server Configuration Manager&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md).</span></span>  
  
2.  <span data-ttu-id="d879b-107">若要还原 **master**的完整数据库备份，请使用以下 [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="d879b-107">To restore a full database backup of **master**, use the following [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
     <span data-ttu-id="d879b-108">`RESTORE DATABASE master FROM`  *<backup_device>*  `WITH REPLACE`</span><span class="sxs-lookup"><span data-stu-id="d879b-108">`RESTORE DATABASE master FROM`  *<backup_device>*  `WITH REPLACE`</span></span>  
  
     <span data-ttu-id="d879b-109">REPLACE 选项指示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 即使已经存在同名数据库也要还原指定的数据库。</span><span class="sxs-lookup"><span data-stu-id="d879b-109">The REPLACE option instructs [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to restore the specified database even when a database of the same name already exists.</span></span> <span data-ttu-id="d879b-110">现有的数据库（如果存在）被删除。</span><span class="sxs-lookup"><span data-stu-id="d879b-110">The existing database, if any, is deleted.</span></span> <span data-ttu-id="d879b-111">在单用户模式下，建议在 [sqlcmd 实用工具](../../tools/sqlcmd-utility.md)中输入 RESTORE DATABASE 语句。</span><span class="sxs-lookup"><span data-stu-id="d879b-111">In single-user mode, we recommend that you enter the RESTORE DATABASE statement in the [sqlcmd utility](../../tools/sqlcmd-utility.md).</span></span> <span data-ttu-id="d879b-112">有关详细信息，请参阅 [使用 sqlcmd 实用工具](../scripting/sqlcmd-use-the-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="d879b-112">For more information, see [Use the sqlcmd Utility](../scripting/sqlcmd-use-the-utility.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d879b-113">在还原 **master** 后， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例会关闭，并终止 **sqlcmd** 进程。</span><span class="sxs-lookup"><span data-stu-id="d879b-113">After **master** is restored, the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] shuts down and terminates the **sqlcmd** process.</span></span> <span data-ttu-id="d879b-114">在重新启动服务器实例之前，请删除单用户引导参数。</span><span class="sxs-lookup"><span data-stu-id="d879b-114">Before you restart the server instance, remove the single-user startup parameter.</span></span> <span data-ttu-id="d879b-115">有关详细信息，请参阅[配置服务器启动选项（SQL Server 配置管理器）](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md)。</span><span class="sxs-lookup"><span data-stu-id="d879b-115">For more information, see [Configure Server Startup Options &#40;SQL Server Configuration Manager&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md).</span></span>  
  
3.  <span data-ttu-id="d879b-116">重新启动服务器实例并继续执行其他恢复步骤，例如还原其他数据库、附加数据库以及更正用户不匹配问题。</span><span class="sxs-lookup"><span data-stu-id="d879b-116">Restart the server instance and continue other recovery steps such as restoring other databases, attaching databases, and correcting user mismatches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d879b-117">示例</span><span class="sxs-lookup"><span data-stu-id="d879b-117">Example</span></span>  
 <span data-ttu-id="d879b-118">下面的示例将在默认服务器实例上还原 `master` 数据库。</span><span class="sxs-lookup"><span data-stu-id="d879b-118">The following example restores the `master` database on the default server instance.</span></span> <span data-ttu-id="d879b-119">该示例假定服务器实例是在单用户模式下运行。</span><span class="sxs-lookup"><span data-stu-id="d879b-119">The example assumes that the server instance is already running in single-user mode.</span></span> <span data-ttu-id="d879b-120">该示例启动 `sqlcmd` 并执行 `RESTORE DATABASE` 语句，以便从磁盘设备 `master` 还原 `Z:\SQLServerBackups\master.bak`的完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="d879b-120">The example starts `sqlcmd` and executes a `RESTORE DATABASE` statement that restores a full database backup of `master` from a disk device: `Z:\SQLServerBackups\master.bak`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d879b-121">对于命名实例，sqlcmd 命令必须指定 -S\<ComputerName>\\\<InstanceName> 选项 。</span><span class="sxs-lookup"><span data-stu-id="d879b-121">For a named instance, the **sqlcmd** command must specify the **-S**_\<ComputerName>_\\*\<InstanceName>* option.</span></span>  
  
```  
  
      C:\> sqlcmd  
1> RESTORE DATABASE master FROM DISK = 'Z:\SQLServerBackups\master.bak' WITH REPLACE;  
2> GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="d879b-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d879b-122">See Also</span></span>  
 <span data-ttu-id="d879b-123">[完整数据库还原（简单恢复模式）](complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="d879b-123">[Complete Database Restores &#40;Simple Recovery Model&#41;](complete-database-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="d879b-124">[完整数据库还原（完整恢复模式）](complete-database-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="d879b-124">[Complete Database Restores &#40;Full Recovery Model&#41;](complete-database-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="d879b-125">[孤立用户故障排除 (SQL Server)](../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d879b-125">[Troubleshoot Orphaned Users &#40;SQL Server&#41;](../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md) </span></span>  
 <span data-ttu-id="d879b-126">[数据库分离和附加 (SQL Server)](../databases/database-detach-and-attach-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d879b-126">[Database Detach and Attach &#40;SQL Server&#41;](../databases/database-detach-and-attach-sql-server.md) </span></span>  
 <span data-ttu-id="d879b-127">[重新生成系统数据库](../databases/system-databases.md) </span><span class="sxs-lookup"><span data-stu-id="d879b-127">[Rebuild System Databases](../databases/system-databases.md) </span></span>  
 <span data-ttu-id="d879b-128">[数据库引擎服务启动选项](../../database-engine/configure-windows/database-engine-service-startup-options.md) </span><span class="sxs-lookup"><span data-stu-id="d879b-128">[Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md) </span></span>  
 <span data-ttu-id="d879b-129">[SQL Server 配置管理器](../sql-server-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="d879b-129">[SQL Server Configuration Manager](../sql-server-configuration-manager.md) </span></span>  
 <span data-ttu-id="d879b-130">[备份和还原系统数据库 (SQL Server)](back-up-and-restore-of-system-databases-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d879b-130">[Back Up and Restore of System Databases &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md) </span></span>  
 <span data-ttu-id="d879b-131">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d879b-131">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="d879b-132">在单用户模式下启动 SQL Server</span><span class="sxs-lookup"><span data-stu-id="d879b-132">Start SQL Server in Single-User Mode</span></span>](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)  
  
  
