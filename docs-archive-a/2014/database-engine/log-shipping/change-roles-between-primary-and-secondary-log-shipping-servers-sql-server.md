---
title: 交换主日志传送服务器和辅助日志传送服务器的角色 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], role changes
- secondary data files [SQL Server], roles changed between
- primary databases [SQL Server]
- initial role changes [SQL Server]
- log shipping [SQL Server], failover
- failover [SQL Server], log shipping
ms.assetid: 2d7cc40a-47e8-4419-9b2b-7c69f700e806
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 52ddb89bfd18eef4cd2140bc67cf93d1800138f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690785"
---
# <a name="change-roles-between-primary-and-secondary-log-shipping-servers-sql-server"></a><span data-ttu-id="ee259-102">交换主日志传送服务器和辅助日志传送服务器的角色 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ee259-102">Change Roles Between Primary and Secondary Log Shipping Servers (SQL Server)</span></span>
  <span data-ttu-id="ee259-103">在将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日志传送配置故障转移到辅助服务器后，可以将辅助数据库配置为主数据库。</span><span class="sxs-lookup"><span data-stu-id="ee259-103">After you have failed over a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log shipping configuration to a secondary server, you can configure your secondary database to act as the primary database.</span></span> <span data-ttu-id="ee259-104">然后，就可以根据需要交换主数据库和辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="ee259-104">Then, you will be able to swap primary and secondary databases as needed.</span></span>  
  
## <a name="performing-the-initial-role-change"></a><span data-ttu-id="ee259-105">执行初始角色交换</span><span class="sxs-lookup"><span data-stu-id="ee259-105">Performing the Initial Role Change</span></span>  
 <span data-ttu-id="ee259-106">当初次将故障转移到辅助数据库并将其用作新的主数据库时，必须执行一系列步骤。</span><span class="sxs-lookup"><span data-stu-id="ee259-106">The first time you want to fail over to the secondary database and make it your new primary database, there is a series of steps you must take.</span></span> <span data-ttu-id="ee259-107">按照这些初始步骤操作后，就可以轻松地交换主数据库和辅助数据库的角色。</span><span class="sxs-lookup"><span data-stu-id="ee259-107">After you have followed these initial steps, you will be able to swap roles between the primary database and the secondary database easily.</span></span>  
  
1.  <span data-ttu-id="ee259-108">手动从主数据库故障转移到辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="ee259-108">Manually fail over from the primary database to a secondary database.</span></span> <span data-ttu-id="ee259-109">请确保用 NORECOVERY 备份主服务器上的活动事务日志。</span><span class="sxs-lookup"><span data-stu-id="ee259-109">Be sure to back up the active transaction log on your primary server with NORECOVERY.</span></span> <span data-ttu-id="ee259-110">有关详细信息，请参阅 [故障转移到日志传送辅助服务器 (SQL Server)](fail-over-to-a-log-shipping-secondary-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ee259-110">For more information, see [Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;](fail-over-to-a-log-shipping-secondary-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="ee259-111">禁用原始主服务器上的日志传送备份作业以及原始辅助服务器上的复制和还原作业。</span><span class="sxs-lookup"><span data-stu-id="ee259-111">Disable the log shipping backup job on the original primary server, and the copy and restore jobs on the original secondary server.</span></span>  
  
3.  <span data-ttu-id="ee259-112">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在辅助数据库（要用作新的主数据库的数据库）上配置日志传送。</span><span class="sxs-lookup"><span data-stu-id="ee259-112">On your secondary database (the database you want to be the new primary), configure log shipping using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="ee259-113">有关详细信息，请参阅[配置日志传送 (SQL Server)](configure-log-shipping-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ee259-113">For more information, see [Configure Log Shipping &#40;SQL Server&#41;](configure-log-shipping-sql-server.md).</span></span> <span data-ttu-id="ee259-114">包括下列步骤：</span><span class="sxs-lookup"><span data-stu-id="ee259-114">Include the following steps:</span></span>  
  
    1.  <span data-ttu-id="ee259-115">使用同一个共享来创建为原来的主服务器所创建的备份。</span><span class="sxs-lookup"><span data-stu-id="ee259-115">Use the same share for creating backups that you created for the original primary server.</span></span>  
  
    2.  <span data-ttu-id="ee259-116">添加辅助数据库时，在 **“辅助数据库设置”** 对话框的 **“辅助数据库”** 框中输入原来的主数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="ee259-116">When adding the secondary database, in the **Secondary Database Settings** dialog box, enter the name of the original primary database in the **Secondary database** box.</span></span>  
  
    3.  <span data-ttu-id="ee259-117">在 **“辅助数据库设置”** 对话框中，选中 **“否，辅助数据库已初始化”**。</span><span class="sxs-lookup"><span data-stu-id="ee259-117">In the **Secondary Database Settings** dialog box, select **No, the secondary database is initialized**.</span></span>  
  
4.  <span data-ttu-id="ee259-118">如果对于您之前的日志传送配置启用了日志传送监视，则重新配置日志传送监视以便监视新的日志传送配置。</span><span class="sxs-lookup"><span data-stu-id="ee259-118">If log shipping monitoring was enabled on your former log shipping configuration, reconfigure log shipping monitoring to monitor the new log shipping configuration.</span></span>  <span data-ttu-id="ee259-119">执行以下命令，将 *database_name* 替换为你的数据库的名称：</span><span class="sxs-lookup"><span data-stu-id="ee259-119">Execute the following commands, replacing *database_name* with the name of your database:</span></span>  
  
    1.  <span data-ttu-id="ee259-120">**在新的主服务器上**</span><span class="sxs-lookup"><span data-stu-id="ee259-120">**On the new primary server**</span></span>  
  
         <span data-ttu-id="ee259-121">执行以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="ee259-121">Execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
        ```  
        -- Statement to execute on the new primary server  
        USE msdb  
        GO  
        EXEC master.dbo.sp_change_log_shipping_secondary_database @secondary_database = N'database_name', @threshold_alert_enabled = 0;  
        GO  
        ```  
  
    2.  <span data-ttu-id="ee259-122">**在新的辅助服务器上**</span><span class="sxs-lookup"><span data-stu-id="ee259-122">**On the new secondary server**</span></span>  
  
         <span data-ttu-id="ee259-123">执行以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="ee259-123">Execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
        ```  
        -- Statement to execute on the new secondary server  
        USE msdb  
        GO  
        EXEC master.dbo.sp_change_log_shipping_primary_database @database=N'database_name', @threshold_alert_enabled = 0;  
        GO  
        ```  
  
## <a name="swapping-roles"></a><span data-ttu-id="ee259-124">交换角色</span><span class="sxs-lookup"><span data-stu-id="ee259-124">Swapping Roles</span></span>  
 <span data-ttu-id="ee259-125">完成以上步骤执行初始角色交换后，就可以按照本节的下列步骤交换主数据库和辅助数据库的角色。</span><span class="sxs-lookup"><span data-stu-id="ee259-125">After you have completed the steps above for the initial role change, you can change roles between the primary database and the secondary database by following the steps in this section.</span></span> <span data-ttu-id="ee259-126">若要执行角色交换，请执行下列常规步骤：</span><span class="sxs-lookup"><span data-stu-id="ee259-126">To perform a role change, follow these general steps:</span></span>  
  
1.  <span data-ttu-id="ee259-127">使辅助数据库联机，用 NORECOVERY 备份主服务器上的事务日志。</span><span class="sxs-lookup"><span data-stu-id="ee259-127">Bring the secondary database online, backing up the transaction log on the primary server with NORECOVERY.</span></span>  
  
2.  <span data-ttu-id="ee259-128">禁用原始主服务器上的日志传送备份作业以及原始辅助服务器上的复制和还原作业。</span><span class="sxs-lookup"><span data-stu-id="ee259-128">Disable the log shipping backup job on the original primary server, and the copy and restore jobs on the original secondary server.</span></span>  
  
3.  <span data-ttu-id="ee259-129">在辅助服务器（新的主服务器）上启用日志传送备份作业，在主服务器（新的辅助服务器）上启用复制和还原作业。</span><span class="sxs-lookup"><span data-stu-id="ee259-129">Enable the log shipping backup job on the secondary server (the new primary server), and the copy and restore jobs on the primary server (the new secondary server).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ee259-130">将辅助数据库更改为主数据库时，为了给用户和应用程序提供一致的体验，您可能需要在新的主服务器实例中为数据库重新创建部分或全部元数据（例如登录和作业）。</span><span class="sxs-lookup"><span data-stu-id="ee259-130">When you change a secondary database to the primary database, to provide a consistent experience to users and applications, you might have to re-create some or all of the metadata for the database, such as logins and jobs, on the new primary server instance.</span></span> <span data-ttu-id="ee259-131">有关详细信息，请参阅 [当数据库在其他服务器实例上可用时管理元数据 (SQL Server)](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ee259-131">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="ee259-132">相关任务</span><span class="sxs-lookup"><span data-stu-id="ee259-132">Related Tasks</span></span>  
  
-   [<span data-ttu-id="ee259-133">故障转移到日志传送辅助服务器 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ee259-133">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
-   [<span data-ttu-id="ee259-134">角色切换后登录名和作业的管理 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ee259-134">Management of Logins and Jobs After Role Switching &#40;SQL Server&#41;</span></span>](../../sql-server/failover-clusters/management-of-logins-and-jobs-after-role-switching-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="ee259-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ee259-135">See Also</span></span>  
 [<span data-ttu-id="ee259-136">日志传送表和存储过程</span><span class="sxs-lookup"><span data-stu-id="ee259-136">Log Shipping Tables and Stored Procedures</span></span>](log-shipping-tables-and-stored-procedures.md)  
  
  
