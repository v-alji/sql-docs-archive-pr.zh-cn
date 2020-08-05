---
title: 使用可用性组向导 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.newagwizard.f1
- sql12.swb.newavgroupwiz.f1
helpviewer_keywords:
- New Availability Group Wizard, availability replicas
- Availability Groups [SQL Server], wizards
- Availability Groups [SQL Server], creating
ms.assetid: e1f1dccc-9e65-471d-8fd1-b45085c9484a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c88bc60b4aeab12b3c55d23d1fe7b2b033a962f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579784"
---
# <a name="use-the-availability-group-wizard-sql-server-management-studio"></a><span data-ttu-id="9cfc0-102">使用可用性组向导 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="9cfc0-102">Use the Availability Group Wizard (SQL Server Management Studio)</span></span>
  <span data-ttu-id="9cfc0-103">本主题说明如何使用新建可用性组向导（位于 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中）在 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中创建和配置 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-103">This topic describes how to use the New Availability Group Wizard (in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]) to create and configure an AlwaysOn availability group in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="9cfc0-104">“可用性组”  定义一组用户数据库，这些用户数据库将以支持故障转移的单个单元和一组故障转移伙伴（称作“可用性副本” ）的形式进行故障转移。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-104">An *availability group* defines a set of user databases that will fail over as a single unit and a set of failover partners, known as *availability replicas*, that support failover.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9cfc0-105">有关可用性组的简介，请参阅 [AlwaysOn 可用性组概述 (SQL Server)](overview-of-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-105">For an introduction to availability groups, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="9cfc0-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="9cfc0-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9cfc0-107">先决条件、限制和建议</span><span class="sxs-lookup"><span data-stu-id="9cfc0-107">Prerequisites, Restrictions, and Recommendations</span></span>](#PrerequisitesRestrictions)  
  
     [<span data-ttu-id="9cfc0-108">安全性</span><span class="sxs-lookup"><span data-stu-id="9cfc0-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9cfc0-109">**创建和配置可用性组，使用：**  [新建可用性组向导 (SQL Server Management Studio)](#RunAGwiz)</span><span class="sxs-lookup"><span data-stu-id="9cfc0-109">**To create and configure an availability group, using:**  [New Availability Group Wizard (SQL Server Management Studio)](#RunAGwiz)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9cfc0-110">除了使用新建可用性组向导之外，您还可以使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-110">As an alternative to using the New Availability Group Wizard, you can use [!INCLUDE[tsql](../../../includes/tsql-md.md)] or [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell cmdlets.</span></span> <span data-ttu-id="9cfc0-111">有关详细信息，请参阅 [创建可用性组 (Transact-SQL)](create-an-availability-group-transact-sql.md) 或 [创建可用性组 (SQL Server PowerShell)](../../../powershell/sql-server-powershell.md)中创建和配置 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-111">For more information, see [Create an Availability Group &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md) or [Create an Availability Group &#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9cfc0-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="9cfc0-112">Before You Begin</span></span>  
 <span data-ttu-id="9cfc0-113">我们强烈建议您首先阅读此部分，再尝试创建您的第一个可用性组。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-113">We strongly recommend that you read this section before attempting to create your first availability group.</span></span>  
  
###  <a name="prerequisites-restrictions-and-recommendations"></a><a name="PrerequisitesRestrictions"></a><span data-ttu-id="9cfc0-114">先决条件、限制和建议</span><span class="sxs-lookup"><span data-stu-id="9cfc0-114">Prerequisites, Restrictions, and Recommendations</span></span>  
 <span data-ttu-id="9cfc0-115">在大多数情况下，可以使用新建可用性组向导来完成创建和配置可用性组所需的所有任务。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-115">In most cases, you can use the New Availability Group Wizard to complete all of the tasks require to create and configure an availability group.</span></span> <span data-ttu-id="9cfc0-116">但是，您可能需要手动完成一些任务。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-116">However, you might need to complete some of the tasks manually.</span></span>  
  
-   <span data-ttu-id="9cfc0-117">创建可用性组之前，请先验证承载可用性副本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例位于同一 WSFC 故障转移群集内的不同 Windows Server 故障转移群集 (WSFC) 节点上。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-117">Before creating an availability group, verify that the instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that host availability replicas reside on different Windows Server Failover Clustering (WSFC) node within the same WSFC failover cluster.</span></span> <span data-ttu-id="9cfc0-118">此外，还请验证每个服务器实例是否都满足所有其他 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 先决条件。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-118">Also, verify that each of the server instance meets all other [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] prerequisites.</span></span> <span data-ttu-id="9cfc0-119">有关详细信息，我们强烈建议你参阅[针对 AlwaysOn 可用性组的先决条件、限制和建议 (SQL Server)](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-119">For more information, we strongly recommend that you read [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
-   <span data-ttu-id="9cfc0-120">如果您选择承载可用性副本的服务器实例正在以域用户帐户运行并且尚不具有数据库镜像端点，则此向导可以创建该端点并将 CONNECT 权限授予服务器实例的服务帐户。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-120">If a server instance that you select to host an availability replica is running under a domain user account and does not yet have a database mirroring endpoint, the wizard can create the endpoint and grant CONNECT permission to the server instance service account.</span></span> <span data-ttu-id="9cfc0-121">但是，如果 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务正在以内置帐户（例如 Local System、Local Service 或 Network Service）或非域帐户运行，您必须使用证书来进行端点身份验证，并且该向导将无法在服务器实例上创建数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-121">However, if the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service is running as a built-in account, such as Local System, Local Service, or Network Service, or a nondomain account, you must use certificates for endpoint authentication, and the wizard will be unable to create a database mirroring endpoint on the server instance.</span></span> <span data-ttu-id="9cfc0-122">在此情况下，我们建议您首先手动创建数据库镜像端点，然后启动新建可用性组向导。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-122">In this case, we recommend that you create the database mirroring endpoints manually before you launch the New Availability Group Wizard.</span></span>  
  
     `To use certificates for a database mirroring endpoint:`  
  
     [<span data-ttu-id="9cfc0-123">CREATE ENDPOINT (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9cfc0-123">CREATE ENDPOINT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-endpoint-transact-sql)  
  
     [<span data-ttu-id="9cfc0-124">使用数据库镜像终结点证书 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9cfc0-124">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   <span data-ttu-id="9cfc0-125">SQL Server 故障转移群集实例 (FCI) 不支持通过可用性组来自动进行故障转移，因此，只能为手动故障转移配置任何由 FCI 承载的可用性副本。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-125">SQL Server Failover Cluster Instances (FCIs) do not support automatic failover by availability groups, so any availability replica that is hosted by an FCI can only be configured for manual failover.</span></span>  
  
-   <span data-ttu-id="9cfc0-126">如果数据库进行了加密或者数据库甚至包含数据库加密密钥 (DEK)，则您无法使用 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] 或 [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] 将该数据库添加到某一可用性组。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-126">If a database is encrypted or even contains a Database Encryption Key (DEK), you cannot use the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] or [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] to add the database to an availability group.</span></span> <span data-ttu-id="9cfc0-127">即使已对加密的数据库进行了解密，其日志备份也可能包含加密的数据。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-127">Even if an encrypted database has been decrypted, its log backups might contain encrypted data.</span></span> <span data-ttu-id="9cfc0-128">在此情况下，在该数据库上完整的初始数据同步可能会失败。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-128">In this case, full initial data synchronization could fail on the database.</span></span> <span data-ttu-id="9cfc0-129">其原因在于，还原日志操作可能要求数据库加密密钥 (DEK) 使用的证书，但该证书可能不可用。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-129">This is because the restore log operation might require the certificate that was used by the database encryption keys (DEKs), and that certificate might be unavailable.</span></span>  
  
     <span data-ttu-id="9cfc0-130">为使解密的数据库可添加到某一可用性组，请使用向导：</span><span class="sxs-lookup"><span data-stu-id="9cfc0-130">To make a decrypted database eligible to add to an availability group using the wizard:</span></span>  
  
    1.  <span data-ttu-id="9cfc0-131">创建主数据库的日志备份。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-131">Create a log backup of the primary database.</span></span>  
  
    2.  <span data-ttu-id="9cfc0-132">创建主数据库的完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-132">Create a full database backup of the primary database.</span></span>  
  
    3.  <span data-ttu-id="9cfc0-133">在承载辅助副本的服务器实例上，还原数据库备份。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-133">Restore the database backup on the server instance that hosts the secondary replica.</span></span>  
  
    4.  <span data-ttu-id="9cfc0-134">从主数据库创建新的日志备份。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-134">Create a new log backup from primary database.</span></span>  
  
    5.  <span data-ttu-id="9cfc0-135">在辅助数据库上还原此日志备份。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-135">Restore this log backup on the secondary database.</span></span>  
  
-   <span data-ttu-id="9cfc0-136">**向导执行完全初始数据同步的先决条件**</span><span class="sxs-lookup"><span data-stu-id="9cfc0-136">**Prerequisites for the wizard to perform full initial data synchronization**</span></span>  
  
    -   <span data-ttu-id="9cfc0-137">在承载可用性组的副本的每个服务器实例上，所有数据库文件路径都必须完全相同。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-137">All the database-file paths must be identical on every server instance that hosts a replica for the availability group.</span></span>  
  
    -   <span data-ttu-id="9cfc0-138">没有任何主数据库名称可存在于承载辅助副本的任何服务器实例上。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-138">No primary database name can exist on any server instance that hosts a secondary replica.</span></span> <span data-ttu-id="9cfc0-139">这意味着尚没有任何新的辅助数据库可以存在。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-139">This means that none of the new secondary databases can exist yet.</span></span>  
  
    -   <span data-ttu-id="9cfc0-140">为了使该向导创建并访问备份，需要指定网络共享。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-140">You will need to specify a network share in order for the wizard to create and access backups.</span></span> <span data-ttu-id="9cfc0-141">对于主副本，用于启动 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的帐户必须对网络共享具有读写文件系统权限。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-141">For the primary replica, the account used to start the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must have read and write file-system permissions on a network share.</span></span> <span data-ttu-id="9cfc0-142">对于辅助副本，该帐户必须具有对网络共享区的读权限。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-142">For secondary replicas, the account must have read permission on the network share.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="9cfc0-143">日志备份将是您的日志备份链的一部分。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-143">The log backups will be part of your log backup chain.</span></span> <span data-ttu-id="9cfc0-144">适当地存储日志备份文件。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-144">Store the log backup files appropriately.</span></span>  
  
     <span data-ttu-id="9cfc0-145">如果您无法使用该向导执行完全初始数据同步，则需要手动准备您的辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-145">If you are unable to use the wizard to perform full initial data synchronization, you need to prepare your secondary databases manually.</span></span> <span data-ttu-id="9cfc0-146">您可以在运行该向导之前或之后进行准备。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-146">You can do this before or after running the wizard.</span></span> <span data-ttu-id="9cfc0-147">有关详细信息，请参阅 [为可用性组手动准备辅助数据库 (SQL Server)](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)或 PowerShell 将辅助数据库联接到 Always On 可用性组。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-147">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9cfc0-148">Security</span><span class="sxs-lookup"><span data-stu-id="9cfc0-148">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9cfc0-149">权限</span><span class="sxs-lookup"><span data-stu-id="9cfc0-149">Permissions</span></span>  
 <span data-ttu-id="9cfc0-150">需要 **sysadmin** 固定服务器角色的成员资格，以及 CREATE AVAILABILITY GROUP 服务器权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-150">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
 <span data-ttu-id="9cfc0-151">如果要允许可用性组向导管理数据库镜像端点，还需要 CONTROL ON ENDPOINT 权限。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-151">Also requires CONTROL ON ENDPOINT permission if you want to allow Availability Group Wizard to manage the database mirroring endpoint.</span></span>  
  
##  <a name="using-the-new-availability-group-wizard"></a><a name="RunAGwiz"></a> <span data-ttu-id="9cfc0-152">使用新建可用性组向导</span><span class="sxs-lookup"><span data-stu-id="9cfc0-152">Using the New Availability Group Wizard</span></span>  
  
1.  <span data-ttu-id="9cfc0-153">在对象资源管理器中，连接到承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-153">In Object Explorer, connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="9cfc0-154">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-154">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="9cfc0-155">若要启动新建可用性组向导，请选择 **“新建可用性组向导”** 命令。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-155">To launch the New Availability Group Wizard, select the **New Availability Group Wizard** command.</span></span>  
  
4.  <span data-ttu-id="9cfc0-156">首次运行该向导时， **“简介”** 页将出现。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-156">The first time you run this wizard, an **Introduction** page appears.</span></span> <span data-ttu-id="9cfc0-157">若要在将来跳过此页，可单击 **“不再显示此页”**。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-157">To bypass this page in the future, you can click **Do not show this page again**.</span></span> <span data-ttu-id="9cfc0-158">在阅读了此页后，单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-158">After reading this page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="9cfc0-159">在 **“指定可用性组名称”** 页上的 **“可用性组名称”** 字段中，输入新的可用性组的名称。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-159">On the **Specify Availability Group Name** page, enter the name of the new availability group in the **Availability group name** field.</span></span> <span data-ttu-id="9cfc0-160">此名称必须是在 WSFC 故障转移群集中唯一、并且作为一个整体处于您的域中的有效 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 标识符。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-160">This name must be a valid [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] identifier that is unique on the WSFC failover cluster and in your domain as a whole.</span></span> <span data-ttu-id="9cfc0-161">可用性组名称的最大长度为 128 个字符。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-161">The maximum length for an availability group name is 128 characters.</span></span>  
  
6.  <span data-ttu-id="9cfc0-162">在 **“选择数据库”** 页上，网格中列出所连接的服务器实例上有资格成为“可用性数据库” \*\* 的用户数据库。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-162">On the **Select Databases** page, the grid lists user databases on the connected server instance that are eligible to become the *availability databases*.</span></span> <span data-ttu-id="9cfc0-163">选择一个或多个列出的数据库以参与新的可用性组。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-163">Select one or more of the listed databases to participate in the new availability group.</span></span> <span data-ttu-id="9cfc0-164">这些数据库最初将成为初始“主数据库” \*\*。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-164">These databases will initially be the initial *primary databases*.</span></span>  
  
     <span data-ttu-id="9cfc0-165">对于每个列出的数据库， **“大小”** 列显示数据库大小（如果已知）。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-165">For each listed database, the **Size** column displays the database size, if known.</span></span> <span data-ttu-id="9cfc0-166">“状态”\*\*\*\* 列指示给定的数据库是否满足可用性数据库的[先决条件](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-166">The **Status** column indicates whether a given database meets the [prerequisites](prereqs-restrictions-recommendations-always-on-availability.md)for availability databases.</span></span> <span data-ttu-id="9cfc0-167">如果未满足这些先决条件，会有简短的状态说明指出该数据库不合格的原因；例如，可能是因为它不使用完整恢复模式。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-167">It the prerequisites are not met, a brief status description indicates the reason that the database is ineligible; for example, if it does not use the full recovery model.</span></span> <span data-ttu-id="9cfc0-168">有关详细信息，请单击该状态说明。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-168">For more information, click the status description.</span></span>  
  
     <span data-ttu-id="9cfc0-169">如果数据库经过更改已经合格，请单击 **“刷新”** 以更新数据库网格。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-169">If you change a database to make it eligible, click **Refresh** to update the databases grid.</span></span>  
  
7.  <span data-ttu-id="9cfc0-170">在 **“指定副本”** 页上，为新的可用性组指定和配置一个或多个副本。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-170">On the **Specify Replicas** page, specify and configure one or more replicas for the new availability group.</span></span> <span data-ttu-id="9cfc0-171">此页包含四个选项卡。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-171">This page contains four tabs.</span></span> <span data-ttu-id="9cfc0-172">下表介绍了这些选项卡。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-172">The following table introduces these tabs.</span></span> <span data-ttu-id="9cfc0-173">有关详细信息，请参阅[“指定副本”页（新建可用性组向导：添加副本向导）](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md)主题。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-173">For more information, see the [Specify Replicas Page &#40;New Availability Group Wizard: Add Replica Wizard&#41;](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md) topic.</span></span>  
  
    |<span data-ttu-id="9cfc0-174">选项卡</span><span class="sxs-lookup"><span data-stu-id="9cfc0-174">Tab</span></span>|<span data-ttu-id="9cfc0-175">简要说明</span><span class="sxs-lookup"><span data-stu-id="9cfc0-175">Brief Description</span></span>|  
    |---------|-----------------------|  
    |<span data-ttu-id="9cfc0-176">**副本**</span><span class="sxs-lookup"><span data-stu-id="9cfc0-176">**Replicas**</span></span>|<span data-ttu-id="9cfc0-177">使用此选项卡可以指定将承载辅助副本的每个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-177">Use this tab to specify each instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that will host a secondary replica.</span></span> <span data-ttu-id="9cfc0-178">请注意，您当前连接的服务器实例必须承载主副本。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-178">Note that the server instance to which you are currently connected must host the primary replica.</span></span>|  
    |<span data-ttu-id="9cfc0-179">**端点**</span><span class="sxs-lookup"><span data-stu-id="9cfc0-179">**Endpoints**</span></span>|<span data-ttu-id="9cfc0-180">使用此选项卡可以验证任何现有数据库镜像端点，此外，如果在其服务帐户使用 Windows 身份验证的服务器实例上缺少该端点，则会自动创建该端点。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-180">Use this tab to verify any existing database mirroring endpoints and also, if this endpoint is lacking on a server instance whose service accounts use Windows Authentication, to create the endpoint automatically.</span></span> <span data-ttu-id="9cfc0-181">**注意：** 如果任何服务器实例在非域用户帐户下运行，则需要先对服务器实例进行手动更改，然后才能在向导中继续操作。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-181">**Note:**  If any server instance is running under a non-domain user account, you need to do make a manual change to your server instance before you can proceed in the wizard.</span></span> <span data-ttu-id="9cfc0-182">有关详细信息，请参阅本主题前面的 [先决条件](#PrerequisitesRestrictions)。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-182">For more information, see [Prerequisites](#PrerequisitesRestrictions), earlier in this topic.</span></span>|  
    |<span data-ttu-id="9cfc0-183">**备份首选项**</span><span class="sxs-lookup"><span data-stu-id="9cfc0-183">**Backup Preferences**</span></span>|<span data-ttu-id="9cfc0-184">使用此选项卡可以整体为可用性组指定您的备份首选项，并为各个可用性副本指定备份优先级。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-184">Use this tab to specify your backup preference for the availability group as a whole and your backup priorities for the individual availability replicas.</span></span>|  
    |<span data-ttu-id="9cfc0-185">**侦听器**</span><span class="sxs-lookup"><span data-stu-id="9cfc0-185">**Listener**</span></span>|<span data-ttu-id="9cfc0-186">使用此选项卡可以创建可用性组侦听器。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-186">Use this tab to create an availability group listener.</span></span> <span data-ttu-id="9cfc0-187">默认情况下，该向导不创建侦听器。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-187">By default, the wizard does not create a listener.</span></span>|  
  
8.  <span data-ttu-id="9cfc0-188">在 **“选择初始数据同步”** 页上，选择如何创建新的辅助数据库并将其联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-188">On the **Select Initial Data Synchronization** page, choose how you want your new secondary databases to be created and joined to the availability group.</span></span> <span data-ttu-id="9cfc0-189">选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="9cfc0-189">Choose one of the following options:</span></span>  
  
    -   <span data-ttu-id="9cfc0-190">**完整**</span><span class="sxs-lookup"><span data-stu-id="9cfc0-190">**Full**</span></span>  
  
         <span data-ttu-id="9cfc0-191">如果你的环境满足自动启动初始数据同步的要求，则选择此选项（有关详细信息，请参阅本主题前面的 [先决条件、限制和建议](#PrerequisitesRestrictions)）。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-191">Select this option if your environment meets the requirements for automatically starting initial data synchronization (for more information, see [Prerequisites, Restrictions, and Recommendations](#PrerequisitesRestrictions), earlier in this topic).</span></span>  
  
         <span data-ttu-id="9cfc0-192">如果选择 **“完全”**，则在创建可用性组后，向导会将每个主数据库及其事务日志备份到网络共享，并在每个承载辅助副本的服务器实例上还原备份。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-192">If you select **Full**, after creating the availability group, the wizard will back up every primary database and its transaction log to a network share and restore the backups on every server instance that hosts an secondary replica.</span></span> <span data-ttu-id="9cfc0-193">然后，该向导将每个辅助数据库联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-193">The wizard will then join every secondary database to the availability group.</span></span>  
  
         <span data-ttu-id="9cfc0-194">在“指定可由所有副本访问的共享网络位置”字段中，指定承载副本的所有服务器都具有读写访问权限的备份共享。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-194">In the **Specify a shared network location accessible by all replicas:** field, specify a backup share to which all of the server instance that host replicas have read-write access.</span></span> <span data-ttu-id="9cfc0-195">有关详细信息，请参阅本主题前面的 [先决条件](#PrerequisitesRestrictions)。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-195">For more information, see [Prerequisites](#PrerequisitesRestrictions), earlier in this topic.</span></span>  
  
    -   <span data-ttu-id="9cfc0-196">**仅联接**</span><span class="sxs-lookup"><span data-stu-id="9cfc0-196">**Join only**</span></span>  
  
         <span data-ttu-id="9cfc0-197">如果在将承载辅助副本的服务器实例上手动准备了辅助数据库，则可以选择此选项。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-197">If you have manually prepared secondary databases on the server instances that will host the secondary replicas, you can select this option.</span></span> <span data-ttu-id="9cfc0-198">该向导将每个现有辅助数据库联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-198">The wizard will join the existing secondary databases to the availability group.</span></span>  
  
    -   <span data-ttu-id="9cfc0-199">**跳过初始数据同步**</span><span class="sxs-lookup"><span data-stu-id="9cfc0-199">**Skip initial data synchronization**</span></span>  
  
         <span data-ttu-id="9cfc0-200">如果要使用您自己的数据库和主数据库的日志备份，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-200">Select this option if you want to use your own database and log backups of your primary databases.</span></span> <span data-ttu-id="9cfc0-201">有关详细信息，请参阅[启动 AlwaysOn 辅助数据库的数据移动 (SQL Server)](start-data-movement-on-an-always-on-secondary-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-201">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
9. <span data-ttu-id="9cfc0-202">**“验证”** 页验证在此向导中指定的值是否满足新建可用性组向导的要求。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-202">The **Validation** page verifies whether the values you specified in this Wizard meet the requirements of the New Availability Group Wizard.</span></span> <span data-ttu-id="9cfc0-203">若要进行更改，请单击 **“上一页”** 以返回前面的向导页，更改一个或多个值。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-203">To make a change, click **Previous** to return to an earlier wizard page to change one or more values.</span></span> <span data-ttu-id="9cfc0-204">单击 **“下一步”** 返回到 **“验证”** 页，然后单击 **“重新运行验证”** 。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-204">The click **Next** to return to the **Validation** page, and click **Re-run Validation**.</span></span>  
  
10. <span data-ttu-id="9cfc0-205">在 **“摘要”** 页上，查看您为新的可用性组进行的选择。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-205">On the **Summary** page, review your choices for the new availability group.</span></span> <span data-ttu-id="9cfc0-206">若要进行更改，请单击 **“上一步”** 以返回到相应页。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-206">To make a change, click **Previous** to return to the relevant page.</span></span> <span data-ttu-id="9cfc0-207">在进行更改后，单击 **“下一步”** 以返回到 **“摘要”** 页。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-207">After making the change, click **Next** to return to the **Summary** page.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="9cfc0-208">如果将要承载新的可用性副本的服务器实例的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务帐户未作为登录名存在，则新建可用性组向导需要创建一个登录名。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-208">When the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account of a server instance that will host a new availability replica does not already exist as a login, the New Availability Group Wizard needs to create the login.</span></span> <span data-ttu-id="9cfc0-209">在 **“摘要”** 页上，该向导将显示要创建的登录名的信息。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-209">On the **Summary** page, the wizard displays the information for the login that is to be created.</span></span> <span data-ttu-id="9cfc0-210">如果单击 **“完成”**，则该向导将为 SQL Server 服务帐户创建该登录名，并授予该登录名 CONNECT 权限。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-210">If you click **Finish**, the wizard creates this login for the SQL Server service account and grants the login CONNECT permission.</span></span>  
  
     <span data-ttu-id="9cfc0-211">如果您满意所做的选择，可以选择单击 **“脚本”** 以创建向导将执行的步骤的脚本。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-211">If you are satisfied with your selections, optionally click **Script** to create a script of the steps the wizard will execute.</span></span> <span data-ttu-id="9cfc0-212">然后，若要创建和配置新的可用性组，请单击 **“完成”** 。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-212">Then, to create and configure the new availability group, click **Finish**.</span></span>  
  
11. <span data-ttu-id="9cfc0-213">**“进度”** 页将显示创建可用性组的各步骤（配置端点、创建可用性组和将辅助副本联接到该组）的进度。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-213">The **Progress** page displays the progress of the steps for creating the availability group (configuring endpoints, creating the availability group, and joining the secondary replica to the group).</span></span>  
  
12. <span data-ttu-id="9cfc0-214">在这些步骤完成后， **“结果”** 页将显示各步骤的结果。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-214">When these steps complete, the **Results** page displays the result of each step.</span></span> <span data-ttu-id="9cfc0-215">如果所有这些步骤都成功，则新的可用性组得到了完全配置。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-215">If all these steps succeed, the new availability group is completely configured.</span></span> <span data-ttu-id="9cfc0-216">如果任何步骤导致错误，您可能需要手动完成配置或对失败的步骤使用向导。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-216">If any of the steps result in an error, you might need to manually complete the configuration or use a wizard for the failed step.</span></span> <span data-ttu-id="9cfc0-217">有关给定错误的原因的信息，请单击 **“结果”** 列中关联的“错误”链接。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-217">For information about the cause of a given error, click the associated "Error" link in the **Result** column.</span></span>  
  
     <span data-ttu-id="9cfc0-218">完成向导后，单击 **“关闭”** 以退出安装向导。</span><span class="sxs-lookup"><span data-stu-id="9cfc0-218">When the wizard completes, click **Close** to exit.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="9cfc0-219">相关任务</span><span class="sxs-lookup"><span data-stu-id="9cfc0-219">Related Tasks</span></span>  
 <span data-ttu-id="9cfc0-220">**完成可用性组配置**</span><span class="sxs-lookup"><span data-stu-id="9cfc0-220">**To complete availability group configuration**</span></span>  
  
-   [<span data-ttu-id="9cfc0-221">将辅助副本联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9cfc0-221">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="9cfc0-222">为可用性组手动准备辅助数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9cfc0-222">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="9cfc0-223">将辅助数据库联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9cfc0-223">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="9cfc0-224">创建或配置可用性组侦听程序 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9cfc0-224">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 <span data-ttu-id="9cfc0-225">**用于创建可用性组的其他方法**</span><span class="sxs-lookup"><span data-stu-id="9cfc0-225">**Alternative ways to create an availability group**</span></span>  
  
-   [<span data-ttu-id="9cfc0-226">使用“新建可用性组”对话框 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="9cfc0-226">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="9cfc0-227">创建可用性组 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9cfc0-227">Create an Availability Group &#40;Transact-SQL&#41;</span></span>](create-an-availability-group-transact-sql.md)  
  
-   [<span data-ttu-id="9cfc0-228">创建可用性组 (SQL Server PowerShell)</span><span class="sxs-lookup"><span data-stu-id="9cfc0-228">Create an Availability Group &#40;SQL Server PowerShell&#41;</span></span>](../../../powershell/sql-server-powershell.md)  
  
 <span data-ttu-id="9cfc0-229">**启用 AlwaysOn 可用性组**</span><span class="sxs-lookup"><span data-stu-id="9cfc0-229">**To enable AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="9cfc0-230">启用和禁用 AlwaysOn 可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9cfc0-230">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 <span data-ttu-id="9cfc0-231">**配置数据库镜像端点**</span><span class="sxs-lookup"><span data-stu-id="9cfc0-231">**To configure a database mirroring endpoint**</span></span>  
  
-   [<span data-ttu-id="9cfc0-232">为 AlwaysOn 可用性组 &#40;SQL Server PowerShell 创建数据库镜像端点&#41;</span><span class="sxs-lookup"><span data-stu-id="9cfc0-232">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="9cfc0-233">为 Windows 身份验证创建数据库镜像终结点 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9cfc0-233">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="9cfc0-234">使用数据库镜像终结点证书 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9cfc0-234">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   [<span data-ttu-id="9cfc0-235">在添加或修改可用性副本时指定终结点 URL (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9cfc0-235">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 <span data-ttu-id="9cfc0-236">**解决 AlwaysOn 可用性组配置问题**</span><span class="sxs-lookup"><span data-stu-id="9cfc0-236">**To troubleshoot AlwaysOn Availability Groups configuration**</span></span>  
  
-   [<span data-ttu-id="9cfc0-237">&#41;删除 AlwaysOn 可用性组配置 &#40;SQL Server 的疑难解答</span><span class="sxs-lookup"><span data-stu-id="9cfc0-237">Troubleshoot AlwaysOn Availability Groups Configuration &#40;SQL Server&#41;deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [<span data-ttu-id="9cfc0-238">排除失败的添加文件操作 &#40;AlwaysOn 可用性组&#41;</span><span class="sxs-lookup"><span data-stu-id="9cfc0-238">Troubleshoot a Failed Add-File Operation &#40;AlwaysOn Availability Groups&#41;</span></span>](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="9cfc0-239">相关内容</span><span class="sxs-lookup"><span data-stu-id="9cfc0-239">Related Content</span></span>  
  
-   <span data-ttu-id="9cfc0-240">**博客：**</span><span class="sxs-lookup"><span data-stu-id="9cfc0-240">**Blogs:**</span></span>  
  
     [<span data-ttu-id="9cfc0-241">AlwaysON - HADRON 学习系列：启用了 HADRON 的数据库的工作线程池用法</span><span class="sxs-lookup"><span data-stu-id="9cfc0-241">AlwaysON - HADRON Learning Series: Worker Pool Usage for HADRON Enabled Databases</span></span>](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [<span data-ttu-id="9cfc0-242">SQL Server AlwaysOn 团队博客：SQL Server AlwaysOn 官方团队博客</span><span class="sxs-lookup"><span data-stu-id="9cfc0-242">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="9cfc0-243">CSS SQL Server 工程师博客</span><span class="sxs-lookup"><span data-stu-id="9cfc0-243">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="9cfc0-244">**视频：**</span><span class="sxs-lookup"><span data-stu-id="9cfc0-244">**Videos:**</span></span>  
  
     [<span data-ttu-id="9cfc0-245">Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第一部分：介绍下一代高可用性解决方案</span><span class="sxs-lookup"><span data-stu-id="9cfc0-245">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 1: Introducing the Next Generation High Availability Solution</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [<span data-ttu-id="9cfc0-246">Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第二部分：使用 AlwaysOn 生成关键任务高可用性解决方案</span><span class="sxs-lookup"><span data-stu-id="9cfc0-246">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 2: Building a Mission-Critical High Availability Solution Using AlwaysOn</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   <span data-ttu-id="9cfc0-247">**白皮书：**</span><span class="sxs-lookup"><span data-stu-id="9cfc0-247">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="9cfc0-248">用于高可用性和灾难恢复的 Microsoft SQL Server AlwaysOn 解决方案指南</span><span class="sxs-lookup"><span data-stu-id="9cfc0-248">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [<span data-ttu-id="9cfc0-249">针对 SQL Server 2012 的 Microsoft 白皮书</span><span class="sxs-lookup"><span data-stu-id="9cfc0-249">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="9cfc0-250">SQL Server 客户咨询团队白皮书</span><span class="sxs-lookup"><span data-stu-id="9cfc0-250">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="9cfc0-251">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9cfc0-251">See Also</span></span>  
 <span data-ttu-id="9cfc0-252">[数据库镜像终结点 (SQL Server)](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9cfc0-252">[The Database Mirroring Endpoint &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="9cfc0-253">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9cfc0-253">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="9cfc0-254">AlwaysOn 可用性组 &#40;SQL Server 的先决条件、限制和建议&#41;</span><span class="sxs-lookup"><span data-stu-id="9cfc0-254">Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-restrictions-recommendations-always-on-availability.md)  
  
