---
title: 企业范围的自动化管理 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- enterprise automatic administration [SQL Server]
- multiserver administration [SQL Server]
- SQL Server Agent jobs, multiserver administration
- jobs [SQL Server Agent], multiserver administration
- master servers [SQL Server], about master servers
- target servers [SQL Server], about target servers
- master servers [SQL Server]
- multiple instances of SQL Server
- target servers [SQL Server]
ms.assetid: 44d8365b-42bd-4955-b5b2-74a8a9f4a75f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8df3e34c2c70c81f9710ade0d6855446b930fb50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588249"
---
# <a name="automated-administration-across-an-enterprise"></a><span data-ttu-id="619cb-102">企业范围的自动化管理</span><span class="sxs-lookup"><span data-stu-id="619cb-102">Automated Administration Across an Enterprise</span></span>
  <span data-ttu-id="619cb-103">跨多个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的自动化管理称为“多服务器管理”\*\*。</span><span class="sxs-lookup"><span data-stu-id="619cb-103">Automating administration across multiple instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is called *multiserver administration*.</span></span> <span data-ttu-id="619cb-104">使用多服务器管理可以执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="619cb-104">Use multiserver administration to do the following:</span></span>  
  
-   <span data-ttu-id="619cb-105">管理两台或多台服务器。</span><span class="sxs-lookup"><span data-stu-id="619cb-105">Manage two or more servers.</span></span>  
  
-   <span data-ttu-id="619cb-106">在企业服务器之间安排数据仓库的信息流。</span><span class="sxs-lookup"><span data-stu-id="619cb-106">Schedule information flows between enterprise servers for data warehousing.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="619cb-107">作为 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 不断降低总拥有成本的一项工作的一部分， [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 引入了两项功能：管理称为基于策略的管理的服务器的方法，以及使用配置服务器和服务器组的多服务器查询。</span><span class="sxs-lookup"><span data-stu-id="619cb-107">As part of [!INCLUDE[msCoName](../../includes/msconame-md.md)] ongoing efforts to reduce the total cost of ownership, [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] introduced two features:  a method of managing servers that is called Policy-Based Management, and multiserver queries that use configuration servers and server groups.</span></span> <span data-ttu-id="619cb-108">这些功能可以与本主题中介绍的某些功能一起使用，也可能会替代这些功能。</span><span class="sxs-lookup"><span data-stu-id="619cb-108">These features can be used with, or instead of, some of the features that are described in this topic.</span></span> <span data-ttu-id="619cb-109">有关详细信息，请参阅使用[基于策略的管理来管理服务器](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)和[使用中央管理服务器管理多台服务器](../../relational-databases/administer-multiple-servers-using-central-management-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="619cb-109">For more information, see [Administer Servers by Using Policy-Based Management](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md) and [Administer Multiple Servers Using Central Management Servers](../../relational-databases/administer-multiple-servers-using-central-management-servers.md).</span></span>  
  
 <span data-ttu-id="619cb-110">若要利用多服务器管理，您必须至少有一台主服务器且至少有一台目标服务器。</span><span class="sxs-lookup"><span data-stu-id="619cb-110">To take advantage of multiserver administration, you must have at least one master server and at least one target server.</span></span> <span data-ttu-id="619cb-111">主服务器将作业分发到目标服务器并从它那里接收事件。</span><span class="sxs-lookup"><span data-stu-id="619cb-111">A master server distributes jobs to, and receives events from, target servers.</span></span> <span data-ttu-id="619cb-112">主服务器还存储在目标服务器上运行的作业的作业定义的中央副本。</span><span class="sxs-lookup"><span data-stu-id="619cb-112">A master server also stores the central copy of job definitions for jobs that are run on target servers.</span></span> <span data-ttu-id="619cb-113">目标服务器定期连接到主服务器来更新它们的作业计划。</span><span class="sxs-lookup"><span data-stu-id="619cb-113">Target servers connect periodically to the master server to update their schedule of jobs.</span></span> <span data-ttu-id="619cb-114">如果主服务器上存在新作业，目标服务器将下载该作业。</span><span class="sxs-lookup"><span data-stu-id="619cb-114">If a new job exists on the master server, the target server downloads the job.</span></span> <span data-ttu-id="619cb-115">目标服务器在完成作业后，会重新连接到主服务器并报告作业状态。</span><span class="sxs-lookup"><span data-stu-id="619cb-115">After the target server completes the job, it reconnects to the master server and reports the status of the job.</span></span>  
  
 <span data-ttu-id="619cb-116">以下图例显示了主服务器与目标服务器之间的关系。</span><span class="sxs-lookup"><span data-stu-id="619cb-116">The following illustration shows the relationship between master and target servers:</span></span>  
  
 <span data-ttu-id="619cb-117">![多服务器管理配置](../../database-engine/media/multisvr.gif "多服务器管理配置")</span><span class="sxs-lookup"><span data-stu-id="619cb-117">![Multiserver administration configuration](../../database-engine/media/multisvr.gif "Multiserver administration configuration")</span></span>  
  
 <span data-ttu-id="619cb-118">如果管理大公司内的部门服务器，则可以定义以下内容：</span><span class="sxs-lookup"><span data-stu-id="619cb-118">If you administer departmental servers across a large corporation, you can define the following:</span></span>  
  
-   <span data-ttu-id="619cb-119">一个包含作业步骤的备份作业。</span><span class="sxs-lookup"><span data-stu-id="619cb-119">One backup job with job steps.</span></span>  
  
-   <span data-ttu-id="619cb-120">备份失败时通知的操作员。</span><span class="sxs-lookup"><span data-stu-id="619cb-120">Operators to notify in case of backup failure.</span></span>  
  
-   <span data-ttu-id="619cb-121">备份作业的执行计划。</span><span class="sxs-lookup"><span data-stu-id="619cb-121">An execution schedule for the backup job.</span></span>  
  
 <span data-ttu-id="619cb-122">将该备份作业一次性写入主服务器，然后将部门服务器登记为目标服务器。</span><span class="sxs-lookup"><span data-stu-id="619cb-122">Write this backup job one time on the master server and then enlist each departmental server as a target server.</span></span> <span data-ttu-id="619cb-123">从它们登记时刻起，所有部门服务器将运行相同的备份作业，而您只需定义一次作业。</span><span class="sxs-lookup"><span data-stu-id="619cb-123">From the time of their enlistment, all the departmental servers run the same backup job, yet you defined the job only once.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="619cb-124">多服务器管理功能用于 sysadmin 角色成员。</span><span class="sxs-lookup"><span data-stu-id="619cb-124">Multiserver administration features are intended for members of the sysadmin role.</span></span> <span data-ttu-id="619cb-125">然而，目标服务器上的 sysadmin 角色成员无法编辑目标服务器上由主服务器执行的操作。</span><span class="sxs-lookup"><span data-stu-id="619cb-125">However, a member of the sysadmin role on the target server cannot edit the operations that are performed on the target server by the master server.</span></span> <span data-ttu-id="619cb-126">这项安全措施可防止意外删除作业步骤，并可防止目标服务器上的操作中断。</span><span class="sxs-lookup"><span data-stu-id="619cb-126">This security measure prevents job steps from being accidentally deleted and operations on the target server from being interrupted.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="619cb-127">本节内容</span><span class="sxs-lookup"><span data-stu-id="619cb-127">In This Section</span></span>  
 [<span data-ttu-id="619cb-128">创建多服务器环境</span><span class="sxs-lookup"><span data-stu-id="619cb-128">Create a Multiserver Environment</span></span>](create-a-multiserver-environment.md)  
 <span data-ttu-id="619cb-129">包含有关如何创建和管理主服务器和目标服务器的信息。</span><span class="sxs-lookup"><span data-stu-id="619cb-129">Contains information about how to create and manage master and target servers.</span></span>  
  
 [<span data-ttu-id="619cb-130">为多服务器环境选择正确的 SQL Server 代理服务帐户</span><span class="sxs-lookup"><span data-stu-id="619cb-130">Choose the Right SQL Server Agent Service Account for Multiserver Environments</span></span>](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)  
 <span data-ttu-id="619cb-131">包含有关使用非管理 Windows 帐户或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理服务的本地系统帐户如何影响多服务器环境的信息。</span><span class="sxs-lookup"><span data-stu-id="619cb-131">Contains information about how using nonadministrative Windows accounts or the Local System account for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent service can affect multiserver environments.</span></span>  
  
 [<span data-ttu-id="619cb-132">在目标服务器上设置加密选项</span><span class="sxs-lookup"><span data-stu-id="619cb-132">Set Encryption Options on Target Servers</span></span>](set-encryption-options-on-target-servers.md)  
 <span data-ttu-id="619cb-133">包含有关在目标服务器上设置 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理注册表子项 MsxEncryptChannelOptions 的信息。</span><span class="sxs-lookup"><span data-stu-id="619cb-133">Contains information about setting the MsxEncryptChannelOptions [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent registry subkey on target servers.</span></span>  
  
 [<span data-ttu-id="619cb-134">管理整个企业内的作业</span><span class="sxs-lookup"><span data-stu-id="619cb-134">Manage Jobs Across an Enterprise</span></span>](manage-jobs-across-an-enterprise.md)  
 <span data-ttu-id="619cb-135">包含有关检查作业状态、更改作业的目标服务器、同步目标服务器时钟以及轮询主服务器以获取当前作业状态的信息。</span><span class="sxs-lookup"><span data-stu-id="619cb-135">Contains information about checking job status, changing target servers for jobs, synchronizing target server clocks, and polling master servers for their current job status.</span></span>  
  
 [<span data-ttu-id="619cb-136">排除使用代理的多服务器作业的故障</span><span class="sxs-lookup"><span data-stu-id="619cb-136">Troubleshoot Multiserver Jobs That Use Proxies</span></span>](troubleshoot-multiserver-jobs-that-use-proxies.md)  
 <span data-ttu-id="619cb-137">包含有关排除使用失败代理的多服务器作业故障的信息。</span><span class="sxs-lookup"><span data-stu-id="619cb-137">Contains information about troubleshooting multiserver jobs that use proxies which fail.</span></span>  
  
 [<span data-ttu-id="619cb-138">轮询服务器</span><span class="sxs-lookup"><span data-stu-id="619cb-138">Poll Servers</span></span>](poll-servers.md)  
 <span data-ttu-id="619cb-139">包含有关如何隐式和显式使目标服务器轮询主服务器以同步作业信息的信息。</span><span class="sxs-lookup"><span data-stu-id="619cb-139">Contains information about how to implicitly and explicitly make target servers poll master servers to synchronize jobs information.</span></span>  
  
 [<span data-ttu-id="619cb-140">管理事件</span><span class="sxs-lookup"><span data-stu-id="619cb-140">Manage Events</span></span>](manage-events.md)  
 <span data-ttu-id="619cb-141">包含有关将事件从目标服务器转发到主服务器的信息。</span><span class="sxs-lookup"><span data-stu-id="619cb-141">Contains information about event forwarding from target servers to master servers.</span></span>  
  
 [<span data-ttu-id="619cb-142">在企业中优化自动化管理</span><span class="sxs-lookup"><span data-stu-id="619cb-142">Tune Automated Administration Across an Enterprise</span></span>](tune-automated-administration-across-an-enterprise.md)  
 <span data-ttu-id="619cb-143">包含有关多服务器环境中的自动化管理如何利用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]自我优化功能的信息。</span><span class="sxs-lookup"><span data-stu-id="619cb-143">Contains information about how automated administration in a multiserver environment takes advantage of the self-tuning features of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="619cb-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="619cb-144">See Also</span></span>  
 <span data-ttu-id="619cb-145">[SQL Server 数据库引擎的向后兼容性](../../database-engine/sql-server-database-engine-backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="619cb-145">[SQL Server Database Engine Backward Compatibility](../../database-engine/sql-server-database-engine-backward-compatibility.md) </span></span>  
 <span data-ttu-id="619cb-146">[注册服务器](../register-servers/register-servers.md) </span><span class="sxs-lookup"><span data-stu-id="619cb-146">[Register Servers](../register-servers/register-servers.md) </span></span>  
 <span data-ttu-id="619cb-147">[sp_add_targetservergroup &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="619cb-147">[sp_add_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql) </span></span>  
 <span data-ttu-id="619cb-148">[sp_delete_targetserver &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="619cb-148">[sp_delete_targetserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql) </span></span>  
 <span data-ttu-id="619cb-149">[sp_delete_targetservergroup &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="619cb-149">[sp_delete_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql) </span></span>  
 <span data-ttu-id="619cb-150">[sp_help_downloadlist &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-downloadlist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="619cb-150">[sp_help_downloadlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-downloadlist-transact-sql) </span></span>  
 <span data-ttu-id="619cb-151">[sp_help_jobserver &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobserver-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="619cb-151">[sp_help_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobserver-transact-sql) </span></span>  
 <span data-ttu-id="619cb-152">[sp_help_targetservergroup &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="619cb-152">[sp_help_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql) </span></span>  
 <span data-ttu-id="619cb-153">[sp_resync_targetserver &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="619cb-153">[sp_resync_targetserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql) </span></span>  
 <span data-ttu-id="619cb-154">[sp_update_targetservergroup &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="619cb-154">[sp_update_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql) </span></span>  
 <span data-ttu-id="619cb-155">[dbo.sysjobservers &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/dbo-sysjobservers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="619cb-155">[dbo.sysjobservers &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobservers-transact-sql) </span></span>  
 <span data-ttu-id="619cb-156">[Transact-sql&#41;sys.sys登录名 &#40;](/sql/relational-databases/system-compatibility-views/sys-syslogins-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="619cb-156">[sys.syslogins &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-syslogins-transact-sql) </span></span>  
 [<span data-ttu-id="619cb-157">dbo.systargetservers &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="619cb-157">dbo.systargetservers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/dbo-systargetservers-transact-sql)  
  
  
