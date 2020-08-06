---
title: 配置备份压缩 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 430905eb-d218-458c-bd48-aeee6fbb7446
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f70994eb64cb6a50b538fd87f03ce7ea2fafe857
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591416"
---
# <a name="configure-backup-compression-sql-server"></a><span data-ttu-id="bfe59-102">配置备份压缩 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bfe59-102">Configure Backup Compression (SQL Server)</span></span>
  <span data-ttu-id="bfe59-103">安装时，默认情况下关闭了备份压缩。</span><span class="sxs-lookup"><span data-stu-id="bfe59-103">At installation, backup compression is off by default.</span></span> <span data-ttu-id="bfe59-104">备份压缩的默认行为是由“备份压缩默认值”选项服务器级配置选项定义的。</span><span class="sxs-lookup"><span data-stu-id="bfe59-104">The default behavior for backup compression is defined by the **backup compression default** Option server-level configuration option.</span></span> <span data-ttu-id="bfe59-105">但是，您可以在创建单个备份或计划一系列例行备份时覆盖服务器级默认设置。</span><span class="sxs-lookup"><span data-stu-id="bfe59-105">However, you can override the server-level default when creating a single backup or scheduling a series of routine backups.</span></span> <span data-ttu-id="bfe59-106">若要更改服务器级默认设置，请参阅 [查看或配置备份压缩默认值服务器配置选项](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="bfe59-106">To change the server-level default, see [View or Configure the backup compression default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).</span></span>  
  
## <a name="override-the-backup-compression-default"></a><span data-ttu-id="bfe59-107">覆盖备份压缩默认设置</span><span class="sxs-lookup"><span data-stu-id="bfe59-107">Override the Backup Compression Default</span></span>  
 <span data-ttu-id="bfe59-108">您可以更改单个备份、备份作业或日志传送配置的备份压缩行为。</span><span class="sxs-lookup"><span data-stu-id="bfe59-108">You can change the backup compression behavior for an individual backup, backup job, or log shipping configuration.</span></span>  
  
-   **[!INCLUDE[tsql](../../includes/tsql-md.md)]**  
  
     <span data-ttu-id="bfe59-109">若要在创建备份时覆盖服务器备份压缩默认值，请在 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 语句中使用 WITH NO_COMPRESSION 或 WITH COMPRESSION。</span><span class="sxs-lookup"><span data-stu-id="bfe59-109">To override the server backup-compression default when creating a backup, use either WITH NO_COMPRESSION or WITH COMPRESSION in you [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement.</span></span>  
  
     <span data-ttu-id="bfe59-110">对于日志传送配置，可以使用 [sp_add_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql)[sp_change_log_shipping_primary_database (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-change-log-shipping-primary-database-transact-sql) 控制日志备份的备份压缩行为。</span><span class="sxs-lookup"><span data-stu-id="bfe59-110">For a log shipping configuration, you can control the backup compression behavior of log backups by using [sp_add_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql)[sp_change_log_shipping_primary_database &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-log-shipping-primary-database-transact-sql).</span></span>  
  
-   **[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
     <span data-ttu-id="bfe59-111">有关如何为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例查看或配置备份压缩默认值选项的信息，请参阅[查看或配置备份压缩默认值服务器配置选项](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="bfe59-111">For information about how to view or configure the backup compression default option for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [View or Configure the backup compression default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).</span></span>  
  
     <span data-ttu-id="bfe59-112">你可以通过在以下任意对话框中指定“压缩备份”或“不压缩备份”以在创建备份时覆盖服务器备份压缩默认值：</span><span class="sxs-lookup"><span data-stu-id="bfe59-112">You can override the server backup-compression default when creating a backup by specifying **Compress backup** or **Do not compress backup** in any of the following dialog boxes:</span></span>  
  
    -   [<span data-ttu-id="bfe59-113">备份数据库（“选项”页）</span><span class="sxs-lookup"><span data-stu-id="bfe59-113">Back Up Database (Options Page)</span></span>](back-up-database-backup-options-page.md)  
  
         <span data-ttu-id="bfe59-114">备份数据库时，可以控制单个数据库、文件或日志备份的备份压缩。</span><span class="sxs-lookup"><span data-stu-id="bfe59-114">When backing up a database, you can control backup compression for an individual database, file, or log backup.</span></span>  
  
    -   [<span data-ttu-id="bfe59-115">使用维护计划向导</span><span class="sxs-lookup"><span data-stu-id="bfe59-115">Use the Maintenance Plan Wizard</span></span>](../maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
         <span data-ttu-id="bfe59-116">通过维护计划向导，您可以控制所计划的每组类型为完全或差异的数据库备份或日志备份的备份压缩。</span><span class="sxs-lookup"><span data-stu-id="bfe59-116">The Maintenance Plan Wizard enables you to control backup compression for each set full or differential database backups or log backups that you schedule.</span></span>  
  
    -   <span data-ttu-id="bfe59-117">Integration Services (SSIS) [备份数据库任务](../../integration-services/control-flow/back-up-database-task.md)</span><span class="sxs-lookup"><span data-stu-id="bfe59-117">Integration Services (SSIS) [Back Up Database task](../../integration-services/control-flow/back-up-database-task.md)</span></span>  
  
         <span data-ttu-id="bfe59-118">您可以在创建用于备份单个数据库或多个数据库的包时控制备份压缩行为。</span><span class="sxs-lookup"><span data-stu-id="bfe59-118">You can control the backup compression behavior when creating a package for backing up a single database or multiple databases.</span></span>  
  
    -   [<span data-ttu-id="bfe59-119">日志传送事务日志备份设置</span><span class="sxs-lookup"><span data-stu-id="bfe59-119">Log Shipping Transaction Log Backup Settings</span></span>](../databases/log-shipping-transaction-log-backup-settings.md)  
  
         <span data-ttu-id="bfe59-120">您可以控制日志备份的备份压缩行为。</span><span class="sxs-lookup"><span data-stu-id="bfe59-120">You can control the backup compression behavior of log backups.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="bfe59-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bfe59-121">See Also</span></span>  
 [<span data-ttu-id="bfe59-122">备份压缩 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bfe59-122">Backup Compression &#40;SQL Server&#41;</span></span>](backup-compression-sql-server.md)  
  
  
