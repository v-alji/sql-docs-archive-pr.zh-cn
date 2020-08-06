---
title: 日志传送事务日志备份设置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.logshipping.settings.tlogback.f1
ms.assetid: 9a6e6c16-7f71-412b-bba6-7bffac001277
author: stevestein
ms.author: sstein
ms.openlocfilehash: b5420f3032cd2477d23028a2e27c1ce89c4e0525
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693929"
---
# <a name="log-shipping-transaction-log-backup-settings"></a><span data-ttu-id="842bf-102">日志传送事务日志备份设置</span><span class="sxs-lookup"><span data-stu-id="842bf-102">Log Shipping Transaction Log Backup Settings</span></span>
  <span data-ttu-id="842bf-103">使用此对话框可以配置和修改日志传送配置的事务日志备份设置。</span><span class="sxs-lookup"><span data-stu-id="842bf-103">Use this dialog box to configure and modify the transaction log backup settings for a log shipping configuration.</span></span>  
  
 <span data-ttu-id="842bf-104">有关日志传送概念的说明，请参阅 [关于日志传送 (SQL Server)](../../database-engine/log-shipping/about-log-shipping-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="842bf-104">For an explanation of log shipping concepts, see [About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="842bf-105">选项</span><span class="sxs-lookup"><span data-stu-id="842bf-105">Options</span></span>  
 <span data-ttu-id="842bf-106">**备份文件夹的网络路径**</span><span class="sxs-lookup"><span data-stu-id="842bf-106">**Network path to the backup folder**</span></span>  
 <span data-ttu-id="842bf-107">在此框中键入备份文件夹的网络共享位置。</span><span class="sxs-lookup"><span data-stu-id="842bf-107">Type the network share to your backup folder in this box.</span></span> <span data-ttu-id="842bf-108">用于保存事务日志备份的本地文件夹必须处于共享状态，以便日志传送复制作业可以将这些文件复制到辅助服务器。</span><span class="sxs-lookup"><span data-stu-id="842bf-108">The local folder where your transaction log backups are saved must be shared so that the log shipping copy jobs can copy these files to the secondary server.</span></span> <span data-ttu-id="842bf-109">必须向代理帐户授予此网络共享的读取权限，复制作业将在辅助服务器实例上的该帐户下运行。</span><span class="sxs-lookup"><span data-stu-id="842bf-109">You must grant read permissions on this network share to the proxy account under which the copy job will run at the secondary server instance.</span></span> <span data-ttu-id="842bf-110">默认情况下，这是辅助服务器实例的 SQLServerAgent 服务帐户，但是管理员可以为该作业选择另一个代理帐户。</span><span class="sxs-lookup"><span data-stu-id="842bf-110">By default, this is the SQLServerAgent service account of the secondary server instance, but an administrator can choose another proxy account for the job.</span></span>  
  
 <span data-ttu-id="842bf-111">**如果备份文件夹位于主服务器上，则键入该文件夹的本地路径**</span><span class="sxs-lookup"><span data-stu-id="842bf-111">**If the backup folder is located on the primary server, type the local path to the folder**</span></span>  
 <span data-ttu-id="842bf-112">如果备份文件夹位于主服务器上，则键入备份文件夹的本地驱动器号和路径。</span><span class="sxs-lookup"><span data-stu-id="842bf-112">Type the local drive letter and path to the backup folder if the backup folder is located on the primary server.</span></span> <span data-ttu-id="842bf-113">如果备份文件夹不在主服务器上，则可以保留此选项为空白。</span><span class="sxs-lookup"><span data-stu-id="842bf-113">If the backup folder is not located on the primary server, you can leave this blank.</span></span>  
  
 <span data-ttu-id="842bf-114">如果您在此处指定本地路径，则 BACKUP 命令将使用此路径来创建事务日志备份；否则，如果未指定本地路径，则 BACKUP 命令将使用在 **“备份文件夹的网络路径”** 框中指定的网络路径。</span><span class="sxs-lookup"><span data-stu-id="842bf-114">If you specify a local path here, the BACKUP command will use this path to create the transaction log backups; otherwise, if no local path is specified, the BACKUP command will use the network path specified in the **Network path to the backup folder** box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="842bf-115">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务帐户在主服务器上的本地系统帐户下运行，则必须在主服务器上创建备份文件夹，并在此处指定该文件夹的本地路径。</span><span class="sxs-lookup"><span data-stu-id="842bf-115">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account is running under the local system account on the primary server, you must create the backup folder on the primary server and specify the local path to that folder here.</span></span> <span data-ttu-id="842bf-116">主服务器实例的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务帐户必须对此文件夹具有读写权限。</span><span class="sxs-lookup"><span data-stu-id="842bf-116">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account of the primary server instance must have Read and Write permissions on this folder.</span></span>  
  
 <span data-ttu-id="842bf-117">**删除文件，如果其保留时间超过**</span><span class="sxs-lookup"><span data-stu-id="842bf-117">**Delete files older than**</span></span>  
 <span data-ttu-id="842bf-118">指定事务日志备份在删除前在备份目录中保留的时间。</span><span class="sxs-lookup"><span data-stu-id="842bf-118">Specify the length of time you want transaction log backups to remain in your backup directory before being deleted.</span></span>  
  
 <span data-ttu-id="842bf-119">**在以下时间内没有执行备份时报警**</span><span class="sxs-lookup"><span data-stu-id="842bf-119">**Alert if no backup occurs within**</span></span>  
 <span data-ttu-id="842bf-120">指定在引发警报以报告未执行事务日志备份之前，希望日志传送等待的时间。</span><span class="sxs-lookup"><span data-stu-id="842bf-120">Specify the amount of time you want log shipping to wait before raising an alert that no transaction log backups have occurred.</span></span>  
  
 <span data-ttu-id="842bf-121">**作业名称**</span><span class="sxs-lookup"><span data-stu-id="842bf-121">**Job name**</span></span>  
 <span data-ttu-id="842bf-122">显示 SQL Server 代理作业的名称，该作业用于为日志传送创建事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="842bf-122">Displays the name of the SQL Server Agent job that is used to create the transaction log backups for log shipping.</span></span> <span data-ttu-id="842bf-123">首次创建作业时，可以通过在该框中键入内容来修改名称。</span><span class="sxs-lookup"><span data-stu-id="842bf-123">When first creating the job, you can modify the name by typing in the box.</span></span>  
  
 <span data-ttu-id="842bf-124">**“计划”**</span><span class="sxs-lookup"><span data-stu-id="842bf-124">**Schedule**</span></span>  
 <span data-ttu-id="842bf-125">显示用来备份主数据库的事务日志的当前计划。</span><span class="sxs-lookup"><span data-stu-id="842bf-125">Displays the current schedule for backing up the transaction logs of the primary database.</span></span> <span data-ttu-id="842bf-126">在创建备份作业之前，可以通过单击 **“计划...”** 来修改此计划。在创建备份作业之后，可以通过单击 **“编辑作业...”** 来修改此计划。</span><span class="sxs-lookup"><span data-stu-id="842bf-126">Before the backup job has been created, You can modify this schedule by clicking **Schedule...**. After the job has been created, you can modify this schedule by clicking **Edit Job...**.</span></span>  
  
### <a name="backup-job"></a><span data-ttu-id="842bf-127">备份作业</span><span class="sxs-lookup"><span data-stu-id="842bf-127">Backup Job</span></span>  
 <span data-ttu-id="842bf-128">**“计划...”**</span><span class="sxs-lookup"><span data-stu-id="842bf-128">**Schedule...**</span></span>  
 <span data-ttu-id="842bf-129">修改在创建 SQL Server 代理作业时创建的计划。</span><span class="sxs-lookup"><span data-stu-id="842bf-129">Modify the schedule that is created when the SQL Server Agent job is created.</span></span>  
  
 <span data-ttu-id="842bf-130">**“编辑作业...”**</span><span class="sxs-lookup"><span data-stu-id="842bf-130">**Edit Job...**</span></span>  
 <span data-ttu-id="842bf-131">为在主数据库中执行事务日志备份的作业修改 SQL Server 代理作业参数。</span><span class="sxs-lookup"><span data-stu-id="842bf-131">Modify the SQL Server Agent job parameters for the job that performs transaction log backups on the primary database.</span></span>  
  
 <span data-ttu-id="842bf-132">**禁用此作业**</span><span class="sxs-lookup"><span data-stu-id="842bf-132">**Disable this job**</span></span>  
 <span data-ttu-id="842bf-133">禁止 SQL Server 代理作业创建事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="842bf-133">Disable the SQL Server Agent job from creating transaction log backups.</span></span>  
  
### <a name="compression"></a><span data-ttu-id="842bf-134">压缩</span><span class="sxs-lookup"><span data-stu-id="842bf-134">Compression</span></span>  
 [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="842bf-135">（或更高版本）支持 [备份压缩](../backup-restore/backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="842bf-135">(or a later version) supports [backup compression](../backup-restore/backup-compression-sql-server.md).</span></span>  
  
 <span data-ttu-id="842bf-136">**设置备份压缩**</span><span class="sxs-lookup"><span data-stu-id="842bf-136">**Set backup compression**</span></span>  
 <span data-ttu-id="842bf-137">在 [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] （或更高版本）中，为此日志传送配置的日志备份选择以下其中一个备份压缩值。</span><span class="sxs-lookup"><span data-stu-id="842bf-137">In [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (or a later version), select one the following backup compression values for the log backups of this log shipping configuration:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="842bf-138">**使用默认服务器设置**</span><span class="sxs-lookup"><span data-stu-id="842bf-138">**Use the default server setting**</span></span>|<span data-ttu-id="842bf-139">单击此选项可使用服务器级别默认值。</span><span class="sxs-lookup"><span data-stu-id="842bf-139">Click to use the server-level default.</span></span><br /><br /> <span data-ttu-id="842bf-140">此默认值可通过 **backup compression default** 服务器配置选项进行设置。</span><span class="sxs-lookup"><span data-stu-id="842bf-140">This default is set by the **backup compression default** server-configuration option.</span></span> <span data-ttu-id="842bf-141">有关如何查看此选项当前设置的信息，请参阅 [查看或配置 backup compression default 服务器配置选项](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="842bf-141">For information about how to view the current setting of this option, see [View or Configure the backup compression default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).</span></span>|  
|<span data-ttu-id="842bf-142">**压缩备份**</span><span class="sxs-lookup"><span data-stu-id="842bf-142">**Compress backup**</span></span>|<span data-ttu-id="842bf-143">单击此选项可压缩备份，而不考虑服务器级别默认值。</span><span class="sxs-lookup"><span data-stu-id="842bf-143">Click to compress the backup, regardless of the server-level default.</span></span><br /><br /> <span data-ttu-id="842bf-144">**\*\* 重要提示 \*\*** 默认情况下，压缩会大大提高 CPU 使用率，但压缩进程占用的额外 CPU 可能会对并发操作造成不利影响。</span><span class="sxs-lookup"><span data-stu-id="842bf-144">**\*\* Important \*\*** By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely impact concurrent operations.</span></span> <span data-ttu-id="842bf-145">因此，你可能需要在会话中创建低优先级的压缩备份，其 CPU 使用率受 [资源调控器](../resource-governor/resource-governor.md)限制。</span><span class="sxs-lookup"><span data-stu-id="842bf-145">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by the [Resource Governor](../resource-governor/resource-governor.md).</span></span> <span data-ttu-id="842bf-146">有关详细信息，请参阅本主题后面的 [使用资源调控器限制备份压缩的 CPU 使用量 (Transact-SQL)](../backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)限制。</span><span class="sxs-lookup"><span data-stu-id="842bf-146">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>|  
|<span data-ttu-id="842bf-147">**不压缩备份**</span><span class="sxs-lookup"><span data-stu-id="842bf-147">**Do not compress backup**</span></span>|<span data-ttu-id="842bf-148">单击此选项可创建未压缩的备份，而不考虑服务器级别默认值。</span><span class="sxs-lookup"><span data-stu-id="842bf-148">Click to create an uncompressed backup, regardless of the server-level default.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="842bf-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="842bf-149">See Also</span></span>  
 <span data-ttu-id="842bf-150">[配置帐户以创建和管理 SQL Server 代理作业](../../ssms/agent/configure-a-user-to-create-and-manage-sql-server-agent-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="842bf-150">[Configure a User to Create and Manage SQL Server Agent Jobs](../../ssms/agent/configure-a-user-to-create-and-manage-sql-server-agent-jobs.md) </span></span>  
 [<span data-ttu-id="842bf-151">关于日志传送 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="842bf-151">About Log Shipping &#40;SQL Server&#41;</span></span>](../../database-engine/log-shipping/about-log-shipping-sql-server.md)  
  
  
