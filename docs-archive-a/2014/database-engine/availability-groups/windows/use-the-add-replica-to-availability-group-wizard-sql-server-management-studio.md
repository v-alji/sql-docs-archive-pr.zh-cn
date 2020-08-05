---
title: 使用“将副本添加到可用性组向导”(SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.addreplicawizard.f1
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], wizards
ms.assetid: 60d962b6-2af4-4394-9190-61939a102bc0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e4d75372cd2388e88fcb3d3ce95975bdefa54c5c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579789"
---
# <a name="use-the-add-replica-to-availability-group-wizard-sql-server-management-studio"></a><span data-ttu-id="96ffd-102">使用“将副本添加到可用性组向导”(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="96ffd-102">Use the Add Replica to Availability Group Wizard (SQL Server Management Studio)</span></span>
  <span data-ttu-id="96ffd-103">使用“将副本添加到可用性组向导”可帮助您将新的辅助副本添加到现有 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="96ffd-103">Use the Add Replica to Availability Group Wizard to help you a add new secondary replica to an existing AlwaysOn availability group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="96ffd-104">有关使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 或 PowerShell 将辅助副本添加到可用性组的详细信息，请参阅 [将辅助副本添加到可用性组 (SQL Server)](add-a-secondary-replica-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="96ffd-104">For information about using [!INCLUDE[tsql](../../../includes/tsql-md.md)] or PowerShell to add a secondary replica to an availability group, see [Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="96ffd-105">开始之前</span><span class="sxs-lookup"><span data-stu-id="96ffd-105">Before You Begin</span></span>  
 <span data-ttu-id="96ffd-106">如果你从未向可用性组添加过任何可用性副本，请参阅[针对 AlwaysOn 可用性组 &#40;SQL Server&#41;的先决条件、限制和建议](prereqs-restrictions-recommendations-always-on-availability.md)中的 "服务器实例" 和 "可用性组和副本" 部分。</span><span class="sxs-lookup"><span data-stu-id="96ffd-106">If you have never added any availability replica to an availability group, see the "Server instances" and "Availability groups and replicas" sections in [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="96ffd-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="96ffd-107">Prerequisites</span></span>  
  
-   <span data-ttu-id="96ffd-108">您必须连接到承载当前主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="96ffd-108">You must be connected to the server instance that hosts the current primary replica.</span></span>  
  
-   <span data-ttu-id="96ffd-109">在添加辅助副本前，请验证 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的主机实例与现有副本位于相同的 Windows Server 故障转移群集 (WSFC) 群集中，但驻留在不同的群集节点上。</span><span class="sxs-lookup"><span data-stu-id="96ffd-109">Before adding a secondary replica, verify that the host instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is in the same Windows Server Failover Clustering (WSFC) cluster as the existing replicas but resides on a different cluster node.</span></span> <span data-ttu-id="96ffd-110">此外，还请验证此服务器实例满足所有其他 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 先决条件。</span><span class="sxs-lookup"><span data-stu-id="96ffd-110">Also, verify that this server instance meets all other [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] prerequisites.</span></span> <span data-ttu-id="96ffd-111">有关详细信息，请参阅[针对 AlwaysOn 可用性组的先决条件、限制和建议 (SQL Server)](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="96ffd-111">For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
-   <span data-ttu-id="96ffd-112">如果您选择承载可用性副本的服务器实例正在以域用户帐户运行并且尚不具有数据库镜像端点，则此向导可以创建该端点并将 CONNECT 权限授予服务器实例的服务帐户。</span><span class="sxs-lookup"><span data-stu-id="96ffd-112">If a server instance that you select to host an availability replica is running under a domain user account and does not yet have a database mirroring endpoint, the wizard can create the endpoint and grant CONNECT permission to the server instance service account.</span></span> <span data-ttu-id="96ffd-113">但是，如果 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务正在以内置帐户（例如 Local System、Local Service 或 Network Service）或非域帐户运行，您必须使用证书来进行端点身份验证，并且该向导将无法在服务器实例上创建数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="96ffd-113">However, if the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service is running as a built-in account, such as Local System, Local Service, or Network Service, or a nondomain account, you must use certificates for endpoint authentication, and the wizard will be unable to create a database mirroring endpoint on the server instance.</span></span> <span data-ttu-id="96ffd-114">在此情况下，我们建议您首先手动创建数据库镜像端点，然后启动“将副本添加到可用性组向导”。</span><span class="sxs-lookup"><span data-stu-id="96ffd-114">In this case, we recommend that you create the database mirroring endpoints manually before you launch the Add Replica to Availability Group Wizard.</span></span>  
  
     `To use certificates for a database mirroring endpoint:`  
  
     [<span data-ttu-id="96ffd-115">CREATE ENDPOINT (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="96ffd-115">CREATE ENDPOINT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-endpoint-transact-sql)  
  
     [<span data-ttu-id="96ffd-116">使用数据库镜像终结点证书 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="96ffd-116">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   <span data-ttu-id="96ffd-117">**使用完全初始数据同步的先决条件**</span><span class="sxs-lookup"><span data-stu-id="96ffd-117">**Prerequisites for using full initial data synchronization**</span></span>  
  
    -   <span data-ttu-id="96ffd-118">在承载可用性组的副本的每个服务器实例上，所有数据库文件路径都必须完全相同。</span><span class="sxs-lookup"><span data-stu-id="96ffd-118">All the database-file paths must be identical on every server instance that hosts a replica for the availability group.</span></span>  
  
    -   <span data-ttu-id="96ffd-119">没有任何主数据库名称可存在于承载辅助副本的任何服务器实例上。</span><span class="sxs-lookup"><span data-stu-id="96ffd-119">No primary database name can exist on any server instance that hosts a secondary replica.</span></span> <span data-ttu-id="96ffd-120">这意味着尚没有任何新的辅助数据库可以存在。</span><span class="sxs-lookup"><span data-stu-id="96ffd-120">This means that none of the new secondary databases can exist yet.</span></span>  
  
    -   <span data-ttu-id="96ffd-121">为了使该向导创建并访问备份，需要指定网络共享。</span><span class="sxs-lookup"><span data-stu-id="96ffd-121">You will need to specify a network share in order for the wizard to create and access backups.</span></span> <span data-ttu-id="96ffd-122">对于主副本，用于启动 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的帐户必须对网络共享具有读写文件系统权限。</span><span class="sxs-lookup"><span data-stu-id="96ffd-122">For the primary replica, the account used to start the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must have read and write file-system permissions on a network share.</span></span> <span data-ttu-id="96ffd-123">对于辅助副本，该帐户必须具有对网络共享区的读权限。</span><span class="sxs-lookup"><span data-stu-id="96ffd-123">For secondary replicas, the account must have read permission on the network share.</span></span>  
  
     <span data-ttu-id="96ffd-124">如果您无法使用该向导执行完全初始数据同步，则需要手动准备您的辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="96ffd-124">If you are unable to use the wizard to perform full initial data synchronization, you need to prepare your secondary databases manually.</span></span> <span data-ttu-id="96ffd-125">您可以在运行该向导之前或之后进行准备。</span><span class="sxs-lookup"><span data-stu-id="96ffd-125">You can do this before or after running the wizard.</span></span> <span data-ttu-id="96ffd-126">有关详细信息，请参阅 [为可用性组手动准备辅助数据库 (SQL Server)](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)或 PowerShell 将辅助数据库联接到 Always On 可用性组。</span><span class="sxs-lookup"><span data-stu-id="96ffd-126">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="96ffd-127">Security</span><span class="sxs-lookup"><span data-stu-id="96ffd-127">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="96ffd-128">权限</span><span class="sxs-lookup"><span data-stu-id="96ffd-128">Permissions</span></span>  
 <span data-ttu-id="96ffd-129">对可用性组要求 ALTER AVAILABILITY GROUP 权限、CONTROL AVAILABILITY GROUP 权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="96ffd-129">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
 <span data-ttu-id="96ffd-130">如果要允许“将副本添加到可用性组向导”管理数据库镜像端点，还需要 CONTROL ON ENDPOINT 权限。</span><span class="sxs-lookup"><span data-stu-id="96ffd-130">Also requires CONTROL ON ENDPOINT permission if you want to allow Add Replica to Availability Group Wizard to manage the database mirroring endpoint.</span></span>  
  

  
##  <a name="using-the-add-replica-to-availability-group-wizard-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="96ffd-131">使用“将副本添加到可用性组向导”(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="96ffd-131">Using the Add Replica to Availability Group Wizard (SQL Server Management Studio)</span></span>  
 <span data-ttu-id="96ffd-132">**使用“将副本添加到可用性组向导”**</span><span class="sxs-lookup"><span data-stu-id="96ffd-132">**To Use the Add Replica to Availability Group Wizard**</span></span>  
  
1.  <span data-ttu-id="96ffd-133">在对象资源管理器中，连接到承载可用性组的主副本的服务器实例，然后展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="96ffd-133">In Object Explorer, connect to the server instance that hosts the primary replica of the availability group, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="96ffd-134">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="96ffd-134">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="96ffd-135">右键单击要向其添加辅助副本的可用性组，然后选择“添加副本”命令。</span><span class="sxs-lookup"><span data-stu-id="96ffd-135">Right-click the availability group to which you are adding a secondary replica, and select the **Add Replica** command.</span></span> <span data-ttu-id="96ffd-136">这将启动“将副本添加到可用性组向导”。</span><span class="sxs-lookup"><span data-stu-id="96ffd-136">This launches the Add Replica to Availability Group Wizard.</span></span>  
  
4.  <span data-ttu-id="96ffd-137">在 **“连接到现有的辅助副本”** 页上，连接到可用性组中的每个辅助副本。</span><span class="sxs-lookup"><span data-stu-id="96ffd-137">On the **Connect to Existing Secondary Replicas** page, connect to every secondary replica in the availability group.</span></span> <span data-ttu-id="96ffd-138">有关详细信息，请参阅[连接到现有辅助副本页 &#40;添加副本向导和添加数据库向导&#41;](connect-to-existing-secondary-replicas-page.md)。</span><span class="sxs-lookup"><span data-stu-id="96ffd-138">For more information, see [Connect to Existing Secondary Replicas Page &#40;Add Replica Wizard and Add Databases Wizard&#41;](connect-to-existing-secondary-replicas-page.md).</span></span>  
  
5.  <span data-ttu-id="96ffd-139">在 **“指定副本”** 页上，为可用性组指定和配置一个或多个新的辅助副本。</span><span class="sxs-lookup"><span data-stu-id="96ffd-139">On the **Specify Replicas** page, specify and configure one or more new secondary replicas for the availability group.</span></span> <span data-ttu-id="96ffd-140">此页包含三个选项卡。</span><span class="sxs-lookup"><span data-stu-id="96ffd-140">This page contains three tabs.</span></span> <span data-ttu-id="96ffd-141">下表介绍了这些选项卡。</span><span class="sxs-lookup"><span data-stu-id="96ffd-141">The following table introduces these tabs.</span></span> <span data-ttu-id="96ffd-142">有关详细信息，请参阅[“指定副本”页（新建可用性组向导：添加副本向导）](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="96ffd-142">For more information, see [Specify Replicas Page &#40;New Availability Group Wizard: Add Replica Wizard&#41;](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md).</span></span>  
  
    |<span data-ttu-id="96ffd-143">选项卡</span><span class="sxs-lookup"><span data-stu-id="96ffd-143">Tab</span></span>|<span data-ttu-id="96ffd-144">简要说明</span><span class="sxs-lookup"><span data-stu-id="96ffd-144">Brief Description</span></span>|  
    |---------|-----------------------|  
    |<span data-ttu-id="96ffd-145">**副本**</span><span class="sxs-lookup"><span data-stu-id="96ffd-145">**Replicas**</span></span>|<span data-ttu-id="96ffd-146">使用此选项卡可以指定将承载新的辅助副本的每个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="96ffd-146">Use this tab to specify each instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that will host a new secondary replica.</span></span>|  
    |<span data-ttu-id="96ffd-147">**端点**</span><span class="sxs-lookup"><span data-stu-id="96ffd-147">**Endpoints**</span></span>|<span data-ttu-id="96ffd-148">使用此选项卡可验证每个新的辅助副本的现有数据库镜像端点（如果有）。</span><span class="sxs-lookup"><span data-stu-id="96ffd-148">Use this tab to verify the existing database mirroring endpoint, if any, for each new secondary replica.</span></span> <span data-ttu-id="96ffd-149">如果在其服务帐户使用 Windows 身份验证的服务器实例上缺少该端点，则该向导会自动创建该端点。</span><span class="sxs-lookup"><span data-stu-id="96ffd-149">If this endpoint is lacking on a server instance whose service accounts use Windows Authentication, the wizard will attempt to create the endpoint automatically.</span></span> <span data-ttu-id="96ffd-150">**注意：** 如果任何服务器实例在非域用户帐户下运行，则需要先对服务器实例进行手动更改，然后才能在向导中继续操作。</span><span class="sxs-lookup"><span data-stu-id="96ffd-150">**Note:**  If any server instance is running under a non-domain user account, you need to do make a manual change to your server instance before you can proceed in the wizard.</span></span> <span data-ttu-id="96ffd-151">有关详细信息，请参阅本主题前面的 [先决条件](#Prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="96ffd-151">For more information, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>|  
    |<span data-ttu-id="96ffd-152">**备份首选项**</span><span class="sxs-lookup"><span data-stu-id="96ffd-152">**Backup Preferences**</span></span>|<span data-ttu-id="96ffd-153">使用此选项卡可以整体为可用性组指定您的备份首选项；如果您想要修改当前设置，还可为各个可用性副本指定备份优先级。</span><span class="sxs-lookup"><span data-stu-id="96ffd-153">Use this tab to specify your backup preference for the availability group as a whole, if you wish to modify the current setting, and to specify your backup priorities for the individual availability replicas.</span></span>|  
  
6.  <span data-ttu-id="96ffd-154">在 **“选择初始数据同步”** 页上，选择如何创建新的辅助数据库并将其联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="96ffd-154">On the **Select Initial Data Synchronization** page, choose how you want your new secondary databases to be created and joined to the availability group.</span></span> <span data-ttu-id="96ffd-155">选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="96ffd-155">Choose one of the following options:</span></span>  
  
    -   <span data-ttu-id="96ffd-156">**完整**</span><span class="sxs-lookup"><span data-stu-id="96ffd-156">**Full**</span></span>  
  
         <span data-ttu-id="96ffd-157">如果你的环境满足自动启动初始数据同步的要求，则选择此选项（有关详细信息，请参阅本主题前面的 [先决条件、限制和建议](#Prerequisites)）。</span><span class="sxs-lookup"><span data-stu-id="96ffd-157">Select this option if your environment meets the requirements for automatically starting initial data synchronization (for more information, see [Prerequisites, Restrictions, and Recommendations](#Prerequisites), earlier in this topic).</span></span>  
  
         <span data-ttu-id="96ffd-158">如果选择 **“完全”** ，则在创建可用性组后，向导会将每个主数据库及其事务日志备份到网络共享，并在每个承载新的辅助副本的服务器实例上还原备份。</span><span class="sxs-lookup"><span data-stu-id="96ffd-158">If you select **Full**, after creating the availability group, the wizard will back up every primary database and its transaction log to a network share and restore the backups on every server instance that hosts a new secondary replica.</span></span> <span data-ttu-id="96ffd-159">然后，该向导将每个新的辅助数据库联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="96ffd-159">The wizard will then join every new secondary database to the availability group.</span></span>  
  
         <span data-ttu-id="96ffd-160">在“指定可由所有副本访问的共享网络位置”字段中，指定承载副本的所有服务器都具有读写访问权限的备份共享。</span><span class="sxs-lookup"><span data-stu-id="96ffd-160">In the **Specify a shared network location accessible by all replicas:** field, specify a backup share to which all of the server instance that host replicas have read-write access.</span></span> <span data-ttu-id="96ffd-161">日志备份将是您的日志备份链的一部分。</span><span class="sxs-lookup"><span data-stu-id="96ffd-161">The log backups will be part of your log backup chain.</span></span> <span data-ttu-id="96ffd-162">适当地存储日志备份文件。</span><span class="sxs-lookup"><span data-stu-id="96ffd-162">Store the log backup files appropriately.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="96ffd-163">有关所需文件系统权限的详细信息，请参阅本主题中前面的 [先决条件](#Prerequisites)部分。</span><span class="sxs-lookup"><span data-stu-id="96ffd-163">For information about the required file-system permissions, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>  
  
    -   <span data-ttu-id="96ffd-164">**仅联接**</span><span class="sxs-lookup"><span data-stu-id="96ffd-164">**Join only**</span></span>  
  
         <span data-ttu-id="96ffd-165">如果在将承载新的辅助副本的服务器实例上手动准备了辅助数据库，则可以选择此选项。</span><span class="sxs-lookup"><span data-stu-id="96ffd-165">If you have manually prepared secondary databases on the server instances that will host the new secondary replicas, you can select this option.</span></span> <span data-ttu-id="96ffd-166">该向导将这些新的现有辅助数据库联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="96ffd-166">The wizard will join these new secondary databases to the availability group.</span></span>  
  
    -   <span data-ttu-id="96ffd-167">**跳过初始数据同步**</span><span class="sxs-lookup"><span data-stu-id="96ffd-167">**Skip initial data synchronization**</span></span>  
  
         <span data-ttu-id="96ffd-168">如果要使用您自己的数据库和主数据库的日志备份，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="96ffd-168">Select this option if you want to use your own database and log backups of your primary databases.</span></span> <span data-ttu-id="96ffd-169">有关详细信息，请参阅[启动 AlwaysOn 辅助数据库的数据移动 (SQL Server)](start-data-movement-on-an-always-on-secondary-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="96ffd-169">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
7.  <span data-ttu-id="96ffd-170">**“验证”** 页验证在此向导中指定的值是否满足“将副本添加到可用性组向导”的要求。</span><span class="sxs-lookup"><span data-stu-id="96ffd-170">The **Validation** page verifies whether the values you specified in this Wizard meet the requirements of the Add Replica to Availability Group Wizard.</span></span> <span data-ttu-id="96ffd-171">若要进行更改，请单击 **“上一页”** 以返回前面的向导页，更改一个或多个值。</span><span class="sxs-lookup"><span data-stu-id="96ffd-171">To make a change, click **Previous** to return to an earlier wizard page to change one or more values.</span></span> <span data-ttu-id="96ffd-172">单击 **“下一步”** 返回到 **“验证”** 页，然后单击 **“重新运行验证”** 。</span><span class="sxs-lookup"><span data-stu-id="96ffd-172">The click **Next** to return to the **Validation** page, and click **Re-run Validation**.</span></span>  
  
8.  <span data-ttu-id="96ffd-173">在 **“摘要”** 页上，查看您为新的可用性组进行的选择。</span><span class="sxs-lookup"><span data-stu-id="96ffd-173">On the **Summary** page, review your choices for the new availability group.</span></span> <span data-ttu-id="96ffd-174">若要进行更改，请单击 **“上一步”** 以返回到相应页。</span><span class="sxs-lookup"><span data-stu-id="96ffd-174">To make a change, click **Previous** to return to the relevant page.</span></span> <span data-ttu-id="96ffd-175">在进行更改后，单击 **“下一步”** 以返回到 **“摘要”** 页。</span><span class="sxs-lookup"><span data-stu-id="96ffd-175">After making the change, click **Next** to return to the **Summary** page.</span></span>  
  
     <span data-ttu-id="96ffd-176">如果您满意所做的选择，可以选择单击“脚本”以创建向导将执行的步骤的脚本。</span><span class="sxs-lookup"><span data-stu-id="96ffd-176">If you are satisfied with your selections, optionally click Script to create a script of the steps the wizard will execute.</span></span> <span data-ttu-id="96ffd-177">然后，若要创建和配置新的可用性组，请单击 **“完成”** 。</span><span class="sxs-lookup"><span data-stu-id="96ffd-177">Then, to create and configure the new availability group, click **Finish**.</span></span>  
  
9. <span data-ttu-id="96ffd-178">**“进度”** 页将显示创建可用性组的各步骤（配置端点、创建可用性组和将辅助副本联接到该组）的进度。</span><span class="sxs-lookup"><span data-stu-id="96ffd-178">The **Progress** page displays the progress of the steps for creating the availability group (configuring endpoints, creating the availability group, and joining the secondary replica to the group).</span></span>  
  
10. <span data-ttu-id="96ffd-179">在这些步骤完成后， **“结果”** 页将显示各步骤的结果。</span><span class="sxs-lookup"><span data-stu-id="96ffd-179">When these steps complete, the **Results** page displays the result of each step.</span></span> <span data-ttu-id="96ffd-180">如果所有这些步骤都成功，则新的可用性组得到了完全配置。</span><span class="sxs-lookup"><span data-stu-id="96ffd-180">If all these steps succeed, the new availability group is completely configured.</span></span> <span data-ttu-id="96ffd-181">如果任何步骤导致错误，您可能需要手动完成配置。</span><span class="sxs-lookup"><span data-stu-id="96ffd-181">If any of the steps result in an error, you might need to manually complete the configuration.</span></span> <span data-ttu-id="96ffd-182">有关给定错误的原因的信息，请单击 **“结果”** 列中关联的“错误”链接。</span><span class="sxs-lookup"><span data-stu-id="96ffd-182">For information about the cause of a given error, click the associated "Error" link in the **Result** column.</span></span>  
  
     <span data-ttu-id="96ffd-183">完成向导后，单击 **“关闭”** 以退出安装向导。</span><span class="sxs-lookup"><span data-stu-id="96ffd-183">When the wizard completes, click **Close** to exit.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="96ffd-184">添加副本后，请参阅[将次要副本添加到可用性组 (SQL Server)](add-a-secondary-replica-to-an-availability-group-sql-server.md) 中的“跟进：添加副本后”部分。</span><span class="sxs-lookup"><span data-stu-id="96ffd-184">After adding a replica, see the "Follow Up: After Adding a Replica" section in [Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  

  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="96ffd-185">相关任务</span><span class="sxs-lookup"><span data-stu-id="96ffd-185">Related Tasks</span></span>  
  
-   [<span data-ttu-id="96ffd-186">将辅助副本添加到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="96ffd-186">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="96ffd-187">另请参阅</span><span class="sxs-lookup"><span data-stu-id="96ffd-187">See Also</span></span>  
 <span data-ttu-id="96ffd-188">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="96ffd-188">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="96ffd-189">[AlwaysOn 可用性组 &#40;SQL Server 的先决条件、限制和建议&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="96ffd-189">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 [<span data-ttu-id="96ffd-190">将辅助副本添加到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="96ffd-190">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
  
