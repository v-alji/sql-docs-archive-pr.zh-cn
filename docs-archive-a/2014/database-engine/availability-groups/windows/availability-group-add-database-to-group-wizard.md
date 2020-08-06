---
title: 使用 "将数据库添加到可用性组向导" (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.adddatabasewizard.f1
helpviewer_keywords:
- Availability Groups [SQL Server], wizards
- Availability Groups [SQL Server], databases
ms.assetid: 81e5e36d-735d-4731-8017-2654673abb88
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a093bb23687d4e49d311b46a7bb0bd211016a0ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577869"
---
# <a name="use-the-add-database-to-availability-group-wizard-sql-server-management-studio"></a><span data-ttu-id="82d58-102">使用“将数据库添加到可用性组向导”(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="82d58-102">Use the Add Database to Availability Group Wizard (SQL Server Management Studio)</span></span>
  <span data-ttu-id="82d58-103">使用“将数据库添加到可用性组向导”可帮助您将一个或多个数据库添加到现有的 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="82d58-103">Use the Add Database to Availability Group Wizard to help you add one or more databases to an existing AlwaysOn availability group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="82d58-104">有关使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 或 PowerShell 将次要副本添加到数据库的信息，请参阅 [将数据库添加到可用性组 (SQL Server)](availability-group-add-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="82d58-104">For information about using [!INCLUDE[tsql](../../../includes/tsql-md.md)] or PowerShell to add a database, see [Add a Database to an Availability Group &#40;SQL Server&#41;](availability-group-add-a-database.md).</span></span>  
  
 <span data-ttu-id="82d58-105">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="82d58-105">**In This Topic:**</span></span>  
  
-   <span data-ttu-id="82d58-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="82d58-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="82d58-107">先决条件和限制</span><span class="sxs-lookup"><span data-stu-id="82d58-107">Prerequisites and Restrictions</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="82d58-108">安全性</span><span class="sxs-lookup"><span data-stu-id="82d58-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="82d58-109">**若要添加数据库，请使用：**  [将数据库添加到可用性组向导 (SQL Server Management Studio)](#SSMSProcedure)</span><span class="sxs-lookup"><span data-stu-id="82d58-109">**To add a database, using:**  [Add Database to Availability Group Wizard (SQL Server Management Studio)](#SSMSProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="82d58-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="82d58-110">Before You Begin</span></span>  
 <span data-ttu-id="82d58-111">如果你从未向可用性组添加过数据库，请参阅[先决条件、限制和建议](prereqs-restrictions-recommendations-always-on-availability.md)中的 "可用性数据库" 部分 AlwaysOn 可用性组 &#40;SQL Server&#41;。</span><span class="sxs-lookup"><span data-stu-id="82d58-111">If you have never added a database to an availability group, see the "Availability Databases" section in [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="prerequisites-restrictions-and-recommendations"></a><a name="Prerequisites"></a><span data-ttu-id="82d58-112">先决条件、限制和建议</span><span class="sxs-lookup"><span data-stu-id="82d58-112">Prerequisites, Restrictions, and Recommendations</span></span>  
  
-   <span data-ttu-id="82d58-113">您必须连接到承载当前主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="82d58-113">You must be connected to the server instance that hosts the current primary replica.</span></span>  
  
-   <span data-ttu-id="82d58-114">如果数据库进行了加密或者数据库甚至包含数据库加密密钥 (DEK)，则您无法使用 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] 或 [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] 将该数据库添加到某一可用性组。</span><span class="sxs-lookup"><span data-stu-id="82d58-114">If a database is encrypted or even contains a Database Encryption Key (DEK), you cannot use the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] or [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] to add the database to an availability group.</span></span> <span data-ttu-id="82d58-115">即使已对加密的数据库进行了解密，其日志备份也可能包含加密的数据。</span><span class="sxs-lookup"><span data-stu-id="82d58-115">Even if an encrypted database has been decrypted, its log backups might contain encrypted data.</span></span> <span data-ttu-id="82d58-116">在此情况下，在该数据库上完整的初始数据同步可能会失败。</span><span class="sxs-lookup"><span data-stu-id="82d58-116">In this case, full initial data synchronization could fail on the database.</span></span> <span data-ttu-id="82d58-117">其原因在于，还原日志操作可能要求数据库加密密钥 (DEK) 使用的证书，但该证书可能不可用。</span><span class="sxs-lookup"><span data-stu-id="82d58-117">This is because the restore log operation might require the certificate that was used by the database encryption keys (DEKs), and that certificate might be unavailable.</span></span>  
  
     <span data-ttu-id="82d58-118">**为使解密的数据库可添加到某一可用性组，请使用向导：**</span><span class="sxs-lookup"><span data-stu-id="82d58-118">**To make a decrypted database eligible to add to an availability group using the wizard:**</span></span>  
  
    1.  <span data-ttu-id="82d58-119">创建主数据库的日志备份。</span><span class="sxs-lookup"><span data-stu-id="82d58-119">Create a log backup of the primary database.</span></span>  
  
    2.  <span data-ttu-id="82d58-120">创建主数据库的完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="82d58-120">Create a full database backup of the primary database.</span></span>  
  
    3.  <span data-ttu-id="82d58-121">在承载辅助副本的服务器实例上，还原数据库备份。</span><span class="sxs-lookup"><span data-stu-id="82d58-121">Restore the database backup on the server instance that hosts the secondary replica.</span></span>  
  
    4.  <span data-ttu-id="82d58-122">从主数据库创建新的日志备份。</span><span class="sxs-lookup"><span data-stu-id="82d58-122">Create a new log backup from primary database.</span></span>  
  
    5.  <span data-ttu-id="82d58-123">在辅助数据库上还原此日志备份。</span><span class="sxs-lookup"><span data-stu-id="82d58-123">Restore this log backup on the secondary database.</span></span>  
  
-   <span data-ttu-id="82d58-124">**使用完全初始数据同步的先决条件**</span><span class="sxs-lookup"><span data-stu-id="82d58-124">**Prerequisites for using full initial data synchronization**</span></span>  
  
    -   <span data-ttu-id="82d58-125">在承载可用性组的副本的每个服务器实例上，所有数据库文件路径都必须完全相同。</span><span class="sxs-lookup"><span data-stu-id="82d58-125">All the database-file paths must be identical on every server instance that hosts a replica for the availability group.</span></span>  
  
    -   <span data-ttu-id="82d58-126">没有任何主数据库名称可存在于承载辅助副本的任何服务器实例上。</span><span class="sxs-lookup"><span data-stu-id="82d58-126">No primary database name can exist on any server instance that hosts a secondary replica.</span></span> <span data-ttu-id="82d58-127">这意味着尚没有任何新的辅助数据库可以存在。</span><span class="sxs-lookup"><span data-stu-id="82d58-127">This means that none of the new secondary databases can exist yet.</span></span>  
  
    -   <span data-ttu-id="82d58-128">为了使该向导创建并访问备份，需要指定网络共享。</span><span class="sxs-lookup"><span data-stu-id="82d58-128">You will need to specify a network share in order for the wizard to create and access backups.</span></span> <span data-ttu-id="82d58-129">对于主副本，用于启动 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的帐户必须对网络共享具有读写文件系统权限。</span><span class="sxs-lookup"><span data-stu-id="82d58-129">For the primary replica, the account used to start the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must have read and write file-system permissions on a network share.</span></span> <span data-ttu-id="82d58-130">对于辅助副本，该帐户必须具有对网络共享区的读权限。</span><span class="sxs-lookup"><span data-stu-id="82d58-130">For secondary replicas, the account must have read permission on the network share.</span></span>  
  
     <span data-ttu-id="82d58-131">如果您无法使用该向导执行完全初始数据同步，则需要手动准备您的辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="82d58-131">If you are unable to use the wizard to perform full initial data synchronization, you need to prepare your secondary databases manually.</span></span> <span data-ttu-id="82d58-132">您可以在运行该向导之前或之后进行准备。</span><span class="sxs-lookup"><span data-stu-id="82d58-132">You can do this before or after running the wizard.</span></span> <span data-ttu-id="82d58-133">有关详细信息，请参阅 [为可用性组手动准备辅助数据库 (SQL Server)](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)或 PowerShell 将辅助数据库联接到 Always On 可用性组。</span><span class="sxs-lookup"><span data-stu-id="82d58-133">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="82d58-134">Security</span><span class="sxs-lookup"><span data-stu-id="82d58-134">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="82d58-135">权限</span><span class="sxs-lookup"><span data-stu-id="82d58-135">Permissions</span></span>  
 <span data-ttu-id="82d58-136">对可用性组要求 ALTER AVAILABILITY GROUP 权限、CONTROL AVAILABILITY GROUP 权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="82d58-136">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-the-add-database-to-availability-group-wizard-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="82d58-137">使用“将数据库添加到可用性组向导”(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="82d58-137">Using the Add Database to Availability Group Wizard (SQL Server Management Studio)</span></span>  
 <span data-ttu-id="82d58-138">**使用“将数据库添加到可用性组向导”**</span><span class="sxs-lookup"><span data-stu-id="82d58-138">**To Use the Add Database to Availability Group Wizard**</span></span>  
  
1.  <span data-ttu-id="82d58-139">在对象资源管理器中，连接到承载可用性组的主副本的服务器实例，然后展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="82d58-139">In Object Explorer, connect to the server instance that hosts the primary replica of the availability group, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="82d58-140">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="82d58-140">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="82d58-141">右键单击要向其添加数据库的可用性组，然后选择“添加数据库”\*\*\*\* 命令。</span><span class="sxs-lookup"><span data-stu-id="82d58-141">Right-click the availability group to which you are adding a database, and select the **Add Database** command.</span></span> <span data-ttu-id="82d58-142">该命令将启动“将数据库添加到可用性组向导”。</span><span class="sxs-lookup"><span data-stu-id="82d58-142">This command launches the Add Database to Availability Group Wizard.</span></span>  
  
4.  <span data-ttu-id="82d58-143">在 **“选择数据库”** 页上，选择一个或多个数据库。</span><span class="sxs-lookup"><span data-stu-id="82d58-143">On the **Select Databases** page, select one or more databases.</span></span> <span data-ttu-id="82d58-144">有关详细信息，请参阅[&#40;新建可用性组向导中的 "选择数据库" 页-添加数据库向导&#41;](select-databases-page-new-availability-group-wizard-and-add-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="82d58-144">For more information, see [Select Databases Page &#40;New Availability Group Wizard-Add Database Wizard&#41;](select-databases-page-new-availability-group-wizard-and-add-database-wizard.md).</span></span>  
  
5.  <span data-ttu-id="82d58-145">在 **“选择初始数据同步”** 页上，选择如何创建新的辅助数据库并将其联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="82d58-145">On the **Select Initial Data Synchronization** page, choose how you want your new secondary databases to be created and joined to the availability group.</span></span> <span data-ttu-id="82d58-146">选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="82d58-146">Choose one of the following options:</span></span>  
  
    -   <span data-ttu-id="82d58-147">**完整**</span><span class="sxs-lookup"><span data-stu-id="82d58-147">**Full**</span></span>  
  
         <span data-ttu-id="82d58-148">如果你的环境满足自动启动初始数据同步的要求，则选择此选项（有关详细信息，请参阅本主题前面的 [先决条件、限制和建议](#Prerequisites)）。</span><span class="sxs-lookup"><span data-stu-id="82d58-148">Select this option if your environment meets the requirements for automatically starting initial data synchronization (for more information, see [Prerequisites, Restrictions, and Recommendations](#Prerequisites), earlier in this topic).</span></span>  
  
         <span data-ttu-id="82d58-149">如果选择 **“完全”**，则在创建可用性组后，向导会尝试将每个主数据库及其事务日志备份到网络共享，并在每个承载辅助副本的服务器实例上还原备份。</span><span class="sxs-lookup"><span data-stu-id="82d58-149">If you select **Full**, after creating the availability group, the wizard will attempt to back up every primary database and its transaction log to a network share and restore the backups on every server instance that hosts an secondary replica.</span></span> <span data-ttu-id="82d58-150">然后，该向导将每个辅助数据库联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="82d58-150">The wizard will then join every secondary database to the availability group.</span></span>  
  
         <span data-ttu-id="82d58-151">在“指定可由所有副本访问的共享网络位置”字段中，指定承载副本的所有服务器都具有读写访问权限的备份共享。</span><span class="sxs-lookup"><span data-stu-id="82d58-151">In the **Specify a shared network location accessible by all replicas:** field, specify a backup share to which all of the server instance that host replicas have read-write access.</span></span> <span data-ttu-id="82d58-152">日志备份将是您的日志备份链的一部分。</span><span class="sxs-lookup"><span data-stu-id="82d58-152">The log backups will be part of your log backup chain.</span></span> <span data-ttu-id="82d58-153">适当地存储日志备份文件。</span><span class="sxs-lookup"><span data-stu-id="82d58-153">Store the log backup files appropriately.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="82d58-154">有关所需文件系统权限的详细信息，请参阅本主题中前面的 [先决条件](#Prerequisites)部分。</span><span class="sxs-lookup"><span data-stu-id="82d58-154">For information about the required file-system permissions, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>  
  
    -   <span data-ttu-id="82d58-155">**仅联接**</span><span class="sxs-lookup"><span data-stu-id="82d58-155">**Join only**</span></span>  
  
         <span data-ttu-id="82d58-156">如果在将承载辅助副本的服务器实例上手动准备了辅助数据库，则可以选择此选项。</span><span class="sxs-lookup"><span data-stu-id="82d58-156">If you have manually prepared secondary databases on the server instances that will host the secondary replicas, you can select this option.</span></span> <span data-ttu-id="82d58-157">该向导将每个现有辅助数据库联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="82d58-157">The wizard will join the existing secondary databases to the availability group.</span></span>  
  
    -   <span data-ttu-id="82d58-158">**跳过初始数据同步**</span><span class="sxs-lookup"><span data-stu-id="82d58-158">**Skip initial data synchronization**</span></span>  
  
         <span data-ttu-id="82d58-159">如果要使用您自己的数据库和主数据库的日志备份，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="82d58-159">Select this option if you want to use your own database and log backups of your primary databases.</span></span> <span data-ttu-id="82d58-160">有关详细信息，请参阅[启动 AlwaysOn 辅助数据库的数据移动 (SQL Server)](start-data-movement-on-an-always-on-secondary-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="82d58-160">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
     <span data-ttu-id="82d58-161">有关详细信息，请参阅[&#41;&#40;AlwaysOn 可用性组向导中的 "选择初始数据同步" 页](select-initial-data-synchronization-page-always-on-availability-group-wizards.md)。</span><span class="sxs-lookup"><span data-stu-id="82d58-161">For more information, see [Select Initial Data Synchronization Page &#40;AlwaysOn Availability Group Wizards&#41;](select-initial-data-synchronization-page-always-on-availability-group-wizards.md).</span></span>  
  
6.  <span data-ttu-id="82d58-162">在 **“连接到现有的辅助副本”** 页上，如果承载该可用性组的可用性副本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例全部作为相同用户帐户中的某个服务运行，则单击 **“全部连接”**。</span><span class="sxs-lookup"><span data-stu-id="82d58-162">On the **Connect to Existing Secondary Replicas** page, if the instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that host the availability replicas for this availability group are all running as a service in the same user account, click **Connect all**.</span></span> <span data-ttu-id="82d58-163">如果任何服务器实例作为不同帐户下的某个服务运行，则单击每个服务器实例名称右侧的各个 **“连接”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="82d58-163">If any of the server instances are running as a service under different accounts, click the individual **Connect** button to the right of each server instance name.</span></span>  
  
     <span data-ttu-id="82d58-164">有关详细信息，请参阅[连接到现有辅助副本页 &#40;添加副本向导和添加数据库向导&#41;](connect-to-existing-secondary-replicas-page.md)。</span><span class="sxs-lookup"><span data-stu-id="82d58-164">For more information, see [Connect to Existing Secondary Replicas Page &#40;Add Replica Wizard and Add Databases Wizard&#41;](connect-to-existing-secondary-replicas-page.md).</span></span>  
  
7.  <span data-ttu-id="82d58-165">**“验证”** 页验证在此向导中指定的值是否满足新建可用性组向导的要求。</span><span class="sxs-lookup"><span data-stu-id="82d58-165">The **Validation** page verifies whether the values you specified in this Wizard meet the requirements of the New Availability Group Wizard.</span></span> <span data-ttu-id="82d58-166">若要进行更改，可以单击 **“上一页”** 以返回前面的向导页，更改一个或多个值。</span><span class="sxs-lookup"><span data-stu-id="82d58-166">To make a change, you can click **Previous** to return to an earlier wizard page to change one or more values.</span></span> <span data-ttu-id="82d58-167">单击 **“下一步”** 返回到 **“验证”** 页，然后单击 **“重新运行验证”** 。</span><span class="sxs-lookup"><span data-stu-id="82d58-167">The click **Next** to return to the **Validation** page, and click **Re-run Validation**.</span></span>  
  
     <span data-ttu-id="82d58-168">有关详细信息，请参阅[&#40;AlwaysOn 可用性组向导&#41;的验证页](validation-page-always-on-availability-group-wizards.md)。</span><span class="sxs-lookup"><span data-stu-id="82d58-168">For more information, see [Validation Page &#40;AlwaysOn Availability Group Wizards&#41;](validation-page-always-on-availability-group-wizards.md).</span></span>  
  
8.  <span data-ttu-id="82d58-169">在 **“摘要”** 页上，查看您为新的可用性组进行的选择。</span><span class="sxs-lookup"><span data-stu-id="82d58-169">On the **Summary** page, review your choices for the new availability group.</span></span> <span data-ttu-id="82d58-170">若要进行更改，请单击 **“上一步”** 以返回到相应页。</span><span class="sxs-lookup"><span data-stu-id="82d58-170">To make a change, click **Previous** to return to the relevant page.</span></span> <span data-ttu-id="82d58-171">在进行更改后，单击 **“下一步”** 以返回到 **“摘要”** 页。</span><span class="sxs-lookup"><span data-stu-id="82d58-171">After making the change, click **Next** to return to the **Summary** page.</span></span>  
  
     <span data-ttu-id="82d58-172">有关详细信息，请参阅[&#41;&#40;AlwaysOn 可用性组向导](summary-page-always-on-availability-group-wizards.md)的 "摘要" 页。</span><span class="sxs-lookup"><span data-stu-id="82d58-172">For more information, see [Summary Page &#40;AlwaysOn Availability Group Wizards&#41;](summary-page-always-on-availability-group-wizards.md).</span></span>  
  
     <span data-ttu-id="82d58-173">如果您满意所做的选择，可以选择单击“脚本”以创建向导将执行的步骤的脚本。</span><span class="sxs-lookup"><span data-stu-id="82d58-173">If you are satisfied with your selections, optionally click Script to create a script of the steps the wizard will execute.</span></span> <span data-ttu-id="82d58-174">然后，若要创建和配置新的可用性组，请单击 **“完成”** 。</span><span class="sxs-lookup"><span data-stu-id="82d58-174">Then, to create and configure the new availability group, click **Finish**.</span></span>  
  
9. <span data-ttu-id="82d58-175">**“进度”** 页将显示创建可用性组的各步骤（配置端点、创建可用性组和将辅助副本联接到该组）的进度。</span><span class="sxs-lookup"><span data-stu-id="82d58-175">The **Progress** page displays the progress of the steps for creating the availability group (configuring endpoints, creating the availability group, and joining the secondary replica to the group).</span></span>  
  
     <span data-ttu-id="82d58-176">有关详细信息，请参阅 "[进度" 页 &#40;AlwaysOn 可用性组向导 "&#41;](progress-page-always-on-availability-group-wizards.md)。</span><span class="sxs-lookup"><span data-stu-id="82d58-176">For more information, see [Progress Page &#40;AlwaysOn Availability Group Wizards&#41;](progress-page-always-on-availability-group-wizards.md).</span></span>  
  
10. <span data-ttu-id="82d58-177">在这些步骤完成后， **“结果”** 页将显示各步骤的结果。</span><span class="sxs-lookup"><span data-stu-id="82d58-177">When these steps complete, the **Results** page displays the result of each step.</span></span> <span data-ttu-id="82d58-178">如果所有这些步骤都成功，则新的可用性组得到了完全配置。</span><span class="sxs-lookup"><span data-stu-id="82d58-178">If all these steps succeed, the new availability group is completely configured.</span></span> <span data-ttu-id="82d58-179">如果任何步骤导致错误，您可能需要手动完成配置。</span><span class="sxs-lookup"><span data-stu-id="82d58-179">If any of the steps result in an error, you might need to manually complete the configuration.</span></span> <span data-ttu-id="82d58-180">有关给定错误的原因的信息，请单击 **“结果”** 列中关联的“错误”链接。</span><span class="sxs-lookup"><span data-stu-id="82d58-180">For information about the cause of a given error, click the associated "Error" link in the **Result** column.</span></span>  
  
     <span data-ttu-id="82d58-181">完成向导后，单击 **“关闭”** 以退出安装向导。</span><span class="sxs-lookup"><span data-stu-id="82d58-181">When the wizard completes, click **Close** to exit.</span></span>  
  
     <span data-ttu-id="82d58-182">有关详细信息，请参阅[“结果”页（AlwaysOn 可用性组向导）](results-page-always-on-availability-group-wizards.md)。</span><span class="sxs-lookup"><span data-stu-id="82d58-182">For more information, see [Results Page &#40;AlwaysOn Availability Group Wizards&#41;](results-page-always-on-availability-group-wizards.md).</span></span>  
  
11. <span data-ttu-id="82d58-183">如果在所有辅助数据库上未自动启动初始数据同步，则需要配置任何尚未加入的辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="82d58-183">If initial data synchronization was not automatically started on all of you secondary database, you need to configure any not-yet-joined secondary databases.</span></span> <span data-ttu-id="82d58-184">有关详细信息，请参阅[启动 AlwaysOn 辅助数据库的数据移动 (SQL Server)](start-data-movement-on-an-always-on-secondary-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="82d58-184">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="82d58-185">相关任务</span><span class="sxs-lookup"><span data-stu-id="82d58-185">Related Tasks</span></span>  
  
-   [<span data-ttu-id="82d58-186">为可用性组手动准备辅助数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="82d58-186">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="82d58-187">将辅助数据库联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="82d58-187">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="82d58-188">另请参阅</span><span class="sxs-lookup"><span data-stu-id="82d58-188">See Also</span></span>  
 <span data-ttu-id="82d58-189">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="82d58-189">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="82d58-190">[AlwaysOn 可用性组 &#40;SQL Server 的先决条件、限制和建议&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="82d58-190">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 <span data-ttu-id="82d58-191">[将数据库添加到可用性组 &#40;SQL Server&#41;](availability-group-add-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="82d58-191">[Add a Database to an Availability Group &#40;SQL Server&#41;](availability-group-add-a-database.md) </span></span>  
 <span data-ttu-id="82d58-192">[启动 AlwaysOn 辅助数据库的数据移动 &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="82d58-192">[Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md) </span></span>  
 [<span data-ttu-id="82d58-193">将数据库添加到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="82d58-193">Add a Database to an Availability Group &#40;SQL Server&#41;</span></span>](availability-group-add-a-database.md)  
  
  
