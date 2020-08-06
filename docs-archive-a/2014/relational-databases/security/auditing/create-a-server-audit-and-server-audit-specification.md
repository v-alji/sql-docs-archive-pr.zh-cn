---
title: 创建服务器审核和服务器审核规范 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.SQLAUDIT.FILTER.F1
- sql12.swb.sqlaudit.srvaudit.general.f1
- sql12.swb.sqlaudit.general.f1
helpviewer_keywords:
- server audit [SQL Server]
- audits [SQL Server], specification
ms.assetid: 6624b1ab-7ec8-44ce-8292-397edf644394
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: a648a975ae9f2c4139a8ebd584f6998f4d0fa1a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689831"
---
# <a name="create-a-server-audit-and-server-audit-specification"></a><span data-ttu-id="f638c-102">创建服务器审核和服务器审核规范</span><span class="sxs-lookup"><span data-stu-id="f638c-102">Create a Server Audit and Server Audit Specification</span></span>
  <span data-ttu-id="f638c-103">本主题介绍如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中创建服务器审核和服务器审核规范。</span><span class="sxs-lookup"><span data-stu-id="f638c-103">This topic describes how to create a server audit and server audit specification in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="f638c-104">“  审核” [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的实例或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库涉及到跟踪和记录系统中发生的事件。</span><span class="sxs-lookup"><span data-stu-id="f638c-104">*Auditing* an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database involves tracking and logging events that occur on the system.</span></span> <span data-ttu-id="f638c-105">*SQL Server Audit* 对象收集单个服务器实例或数据库级操作和操作组以进行监视。</span><span class="sxs-lookup"><span data-stu-id="f638c-105">The *SQL Server Audit* object collects a single instance of server- or database-level actions and groups of actions to monitor.</span></span> <span data-ttu-id="f638c-106">这种审核处于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例级别。</span><span class="sxs-lookup"><span data-stu-id="f638c-106">The audit is at the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance level.</span></span> <span data-ttu-id="f638c-107">每个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例可以具有多个审核。</span><span class="sxs-lookup"><span data-stu-id="f638c-107">You can have multiple audits per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="f638c-108">“服务器审核规范”  对象属于审核。</span><span class="sxs-lookup"><span data-stu-id="f638c-108">The *Server Audit Specification* object belongs to an audit.</span></span> <span data-ttu-id="f638c-109">您可以为每个审核创建一个服务器审核规范，因为它们都是在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例范围内创建的。</span><span class="sxs-lookup"><span data-stu-id="f638c-109">You can create one server audit specification per audit, because both are created at the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance scope.</span></span> <span data-ttu-id="f638c-110">有关详细信息，请参阅 [SQL Server Audit（数据库引擎）](sql-server-audit-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="f638c-110">For more information, see [SQL Server Audit &#40;Database Engine&#41;](sql-server-audit-database-engine.md).</span></span>  
  
 <span data-ttu-id="f638c-111">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="f638c-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f638c-112">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="f638c-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f638c-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="f638c-113">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f638c-114">安全性</span><span class="sxs-lookup"><span data-stu-id="f638c-114">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f638c-115">**若要创建服务器审核和服务器审核规范，请使用：**</span><span class="sxs-lookup"><span data-stu-id="f638c-115">**To create a server audit and server audit specification, using:**</span></span>  
  
     [<span data-ttu-id="f638c-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f638c-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f638c-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f638c-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f638c-118">开始之前</span><span class="sxs-lookup"><span data-stu-id="f638c-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f638c-119">限制和局限</span><span class="sxs-lookup"><span data-stu-id="f638c-119">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="f638c-120">审核必须已存在，才能为它创建服务器审核规范。</span><span class="sxs-lookup"><span data-stu-id="f638c-120">An audit must exist before creating a server audit specification for it.</span></span> <span data-ttu-id="f638c-121">服务器审核规范在创建之后处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="f638c-121">When a server audit specification is created, it is in a disabled state.</span></span>  
  
-   <span data-ttu-id="f638c-122">CREATE SERVER AUDIT 语句位于事务范围内。</span><span class="sxs-lookup"><span data-stu-id="f638c-122">The CREATE SERVER AUDIT statement is in a transaction's scope.</span></span> <span data-ttu-id="f638c-123">如果对事务进行回滚，也将对该语句进行回滚。</span><span class="sxs-lookup"><span data-stu-id="f638c-123">If the transaction is rolled back, the statement is also rolled back.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f638c-124">Security</span><span class="sxs-lookup"><span data-stu-id="f638c-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f638c-125">权限</span><span class="sxs-lookup"><span data-stu-id="f638c-125">Permissions</span></span>  
  
-   <span data-ttu-id="f638c-126">若要创建、更改或删除服务器审核，主体需要拥有 ALTER ANY SERVER AUDIT 或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="f638c-126">To create, alter, or drop a server audit, principals require the ALTER ANY SERVER AUDIT or the CONTROL SERVER permission.</span></span>  
  
-   <span data-ttu-id="f638c-127">具有 ALTER ANY SERVER AUDIT 权限的用户可以创建服务器审核规范并将其绑定到任何审核。</span><span class="sxs-lookup"><span data-stu-id="f638c-127">Users with the ALTER ANY SERVER AUDIT permission can create server audit specifications and bind them to any audit.</span></span>  
  
-   <span data-ttu-id="f638c-128">创建服务器审核规范后，具有 CONTROL SERVER 或 ALTER ANY SERVER AUDIT 权限的主体、sysadmin 帐户或具有对审核的明确访问权的主体即可查看该规范。</span><span class="sxs-lookup"><span data-stu-id="f638c-128">After a server audit specification is created, it can be viewed by principals with the CONTROL SERVER or ALTER ANY SERVER AUDIT permissions, the sysadmin account, or principals having explicit access to the audit.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f638c-129">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f638c-129">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-server-audit"></a><span data-ttu-id="f638c-130">创建服务器审核</span><span class="sxs-lookup"><span data-stu-id="f638c-130">To create a server audit</span></span>  
  
1.  <span data-ttu-id="f638c-131"> 在对象资源管理器中，展开“安全性”文件夹。</span><span class="sxs-lookup"><span data-stu-id="f638c-131">In Object Explorer, expand the **Security** folder.</span></span>  
  
2.  <span data-ttu-id="f638c-132">右键单击“审核”文件夹，然后选择“新建审核…”   。</span><span class="sxs-lookup"><span data-stu-id="f638c-132">Right-click the **Audits** folder and select **New Audit...**.</span></span>  
  
     <span data-ttu-id="f638c-133">在 **“创建审核”** 对话框的 **“常规”** 页上提供以下选项。</span><span class="sxs-lookup"><span data-stu-id="f638c-133">The following options are available on the **General** page of the **Create Audit** dialog box.</span></span>  
  
     <span data-ttu-id="f638c-134">**审核名称**</span><span class="sxs-lookup"><span data-stu-id="f638c-134">**Audit name**</span></span>  
     <span data-ttu-id="f638c-135">审核的名称。</span><span class="sxs-lookup"><span data-stu-id="f638c-135">The name of the audit.</span></span> <span data-ttu-id="f638c-136">这是在创建新审核时自动生成的，但是您可以对其进行编辑。</span><span class="sxs-lookup"><span data-stu-id="f638c-136">This is generated automatically when you create a new audit but is editable.</span></span>  
  
     <span data-ttu-id="f638c-137">**队列延迟(毫秒)**</span><span class="sxs-lookup"><span data-stu-id="f638c-137">**Queue delay (in milliseconds)**</span></span>  
     <span data-ttu-id="f638c-138">指定在强制处理审核操作之前可以等待的时间（毫秒）。</span><span class="sxs-lookup"><span data-stu-id="f638c-138">Specifies the amount of time in milliseconds that can elapse before audit actions are forced to be processed.</span></span>  <span data-ttu-id="f638c-139">值 0 指示同步传递。</span><span class="sxs-lookup"><span data-stu-id="f638c-139">A value of 0 indicates synchronous delivery.</span></span> <span data-ttu-id="f638c-140">默认的最小值为 **1000** （1 秒）。</span><span class="sxs-lookup"><span data-stu-id="f638c-140">The default minimum value is **1000** (1 second).</span></span> <span data-ttu-id="f638c-141">最大值为 2,147,483,647（2,147,483.647 秒或者 24 天 20 小时 31 分钟 23.647 秒）。</span><span class="sxs-lookup"><span data-stu-id="f638c-141">The maximum is 2,147,483,647 (2,147,483.647 seconds or 24 days, 20 hours, 31 minutes, 23.647 seconds).</span></span>  
  
     <span data-ttu-id="f638c-142">**在审核日志失败时：**</span><span class="sxs-lookup"><span data-stu-id="f638c-142">**On Audit Log Failure:**</span></span>  
     <span data-ttu-id="f638c-143">**继续**</span><span class="sxs-lookup"><span data-stu-id="f638c-143">**Continue**</span></span>  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="f638c-144">操作将继续。</span><span class="sxs-lookup"><span data-stu-id="f638c-144">operations continue.</span></span> <span data-ttu-id="f638c-145">审核记录将不会保留。</span><span class="sxs-lookup"><span data-stu-id="f638c-145">Audit records are not retained.</span></span> <span data-ttu-id="f638c-146">审核将继续尝试将事件记入日志，并且在故障条件得到解决后将恢复。</span><span class="sxs-lookup"><span data-stu-id="f638c-146">The audit continues to attempt to log events and will resume if the failure condition is resolved.</span></span> <span data-ttu-id="f638c-147">选择 **“继续”** 选项可以允许未经审核的活动，这可能违反了您的安全策略。</span><span class="sxs-lookup"><span data-stu-id="f638c-147">Selecting the **Continue** option can allow unaudited activity which could violate your security policies.</span></span> <span data-ttu-id="f638c-148">在 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的继续操作比维护完整审核更重要时，选择此选项。</span><span class="sxs-lookup"><span data-stu-id="f638c-148">Select this option when continuing operation of the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] is more important than maintaining a complete audit.</span></span> <span data-ttu-id="f638c-149">这是默认选项。</span><span class="sxs-lookup"><span data-stu-id="f638c-149">This is the default selection.</span></span>  
  
     <span data-ttu-id="f638c-150">**关闭服务器**</span><span class="sxs-lookup"><span data-stu-id="f638c-150">**Shut down server**</span></span>  
     <span data-ttu-id="f638c-151">在写入目标的服务器实例无法将数据写入审核目标时，强制关闭服务器。</span><span class="sxs-lookup"><span data-stu-id="f638c-151">Forces a server shut down when the server instance writing to the target cannot write data to the audit target.</span></span> <span data-ttu-id="f638c-152">发出此命令的登录名必须具有 `SHUTDOWN` 权限。</span><span class="sxs-lookup"><span data-stu-id="f638c-152">The login issuing this must have the `SHUTDOWN` permission.</span></span> <span data-ttu-id="f638c-153">如果该登录名没有此权限，则该函数将失败并将引发错误消息。</span><span class="sxs-lookup"><span data-stu-id="f638c-153">If the logon does not have this permission, this function will fail and an error message will be raised.</span></span> <span data-ttu-id="f638c-154">将不会发生审核的事件。</span><span class="sxs-lookup"><span data-stu-id="f638c-154">No audited events occur.</span></span> <span data-ttu-id="f638c-155">在审核失败可能损害系统的安全或完整性时，选择此选项。</span><span class="sxs-lookup"><span data-stu-id="f638c-155">Select this option when an audit failure could compromise the security or integrity of the system.</span></span>  
  
     <span data-ttu-id="f638c-156">**失败操作**</span><span class="sxs-lookup"><span data-stu-id="f638c-156">**Fail operation**</span></span>  
     <span data-ttu-id="f638c-157">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit 无法写入审核日志的情况下，如果数据库操作将导致审核的事件，则此选项将导致数据库操作失败。</span><span class="sxs-lookup"><span data-stu-id="f638c-157">In cases where the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit cannot write to the audit log this option causes database actions to fail if they would otherwise cause audited events.</span></span> <span data-ttu-id="f638c-158">将不会发生审核的事件。</span><span class="sxs-lookup"><span data-stu-id="f638c-158">No audited events occur.</span></span> <span data-ttu-id="f638c-159">不会导致审核的事件的操作可以继续。</span><span class="sxs-lookup"><span data-stu-id="f638c-159">Actions which do not cause audited events can continue.</span></span> <span data-ttu-id="f638c-160">审核将继续尝试将事件记入日志，并且在故障条件得到解决后将恢复。</span><span class="sxs-lookup"><span data-stu-id="f638c-160">The audit continues to attempt to log events and will resume if the failure condition is resolved.</span></span> <span data-ttu-id="f638c-161">在维护完整审核比对 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的完全访问权限更重要时，选择此选项。</span><span class="sxs-lookup"><span data-stu-id="f638c-161">Select this option when maintaining a complete audit is more important than full access to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f638c-162">在审核处于失败状态时，专用管理员连接可继续执行审核的事件。</span><span class="sxs-lookup"><span data-stu-id="f638c-162">When the audit is in a failed state, the Dedicated Administrator Connection can continue to perform audited events.</span></span>  
  
     <span data-ttu-id="f638c-163">“审核目标”  列表</span><span class="sxs-lookup"><span data-stu-id="f638c-163">**Audit destination** list</span></span>  
     <span data-ttu-id="f638c-164">指定数据的审核目标。</span><span class="sxs-lookup"><span data-stu-id="f638c-164">Specifies the target for auditing data.</span></span> <span data-ttu-id="f638c-165">可用选项包括二进制文件、Windows 应用程序日志或 Windows 安全日志。</span><span class="sxs-lookup"><span data-stu-id="f638c-165">The available options are a binary file, the Windows Application log, or the Windows Security log.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="f638c-166">写入到 Windows 安全日志。</span><span class="sxs-lookup"><span data-stu-id="f638c-166">cannot write to the Windows Security log without configuring additional settings in Windows.</span></span> <span data-ttu-id="f638c-167">有关详细信息，请参阅 [将 SQL Server 审核事件写入安全日志](write-sql-server-audit-events-to-the-security-log.md)。</span><span class="sxs-lookup"><span data-stu-id="f638c-167">For more information, see [Write SQL Server Audit Events to the Security Log](write-sql-server-audit-events-to-the-security-log.md).</span></span>  
  
     <span data-ttu-id="f638c-168">**文件路径**</span><span class="sxs-lookup"><span data-stu-id="f638c-168">**File path**</span></span>  
     <span data-ttu-id="f638c-169">指定当“审核目标”  是文件时，要将审核数据写入的文件夹所在的位置。</span><span class="sxs-lookup"><span data-stu-id="f638c-169">Specifies the location of the folder where audit data is written when the **Audit destination** is a file.</span></span>  
  
     <span data-ttu-id="f638c-170">**省略号 (...)**</span><span class="sxs-lookup"><span data-stu-id="f638c-170">**Ellipsis (...)**</span></span>  
     <span data-ttu-id="f638c-171">打开 "**定位文件夹**_server_name_ " 对话框，以指定文件路径或创建要写入审核文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="f638c-171">Opens the **Locate Folder -**_server_name_ dialog box to specify a file path or create a folder where the audit file is written.</span></span>  
  
     <span data-ttu-id="f638c-172">**审核文件最大限制：**</span><span class="sxs-lookup"><span data-stu-id="f638c-172">**Audit File Maximum Limit:**</span></span>  
     <span data-ttu-id="f638c-173">**最大滚动更新文件数**</span><span class="sxs-lookup"><span data-stu-id="f638c-173">**Maximum rollover files**</span></span>  
     <span data-ttu-id="f638c-174">指定在达到审核文件的最大数目时，新的文件内容将覆盖最旧的审核文件。</span><span class="sxs-lookup"><span data-stu-id="f638c-174">Specifies that, when the maximum number of audit files is reached, the oldest audit files are overwritten by new file content.</span></span>  
  
     <span data-ttu-id="f638c-175">**最大文件数**</span><span class="sxs-lookup"><span data-stu-id="f638c-175">**Maximum files**</span></span>  
     <span data-ttu-id="f638c-176">指定在达到最大审核文件数时，导致生成附加审核事件的任何操作都将失败并报告错误。</span><span class="sxs-lookup"><span data-stu-id="f638c-176">Specifies that, when the maximum number of audit files is reached, any action that causes additional audit events to be generated will fail with an error.</span></span>  
  
     <span data-ttu-id="f638c-177">“无限制”  复选框</span><span class="sxs-lookup"><span data-stu-id="f638c-177">**Unlimited** check box</span></span>  
     <span data-ttu-id="f638c-178">在选中了“最大滚动更新文件数”  下的“无限制”  复选框后，可创建的审核文件数不受任何限制。</span><span class="sxs-lookup"><span data-stu-id="f638c-178">When the **Unlimited** check box under **Maximum rollover files** is selected, there is no limit imposed on the number of audit files that will be created.</span></span> <span data-ttu-id="f638c-179">**“无限制”** 复选框默认被选中并且适用于 **“最大滚动更新文件数”** 和 **“最大文件数”** 选择。</span><span class="sxs-lookup"><span data-stu-id="f638c-179">The **Unlimited** check box is selected by default and applies to both the **Maximum rollover files** and **Maximum files** selections.</span></span>  
  
     <span data-ttu-id="f638c-180">“文件数”  框</span><span class="sxs-lookup"><span data-stu-id="f638c-180">**Number of files** box</span></span>  
     <span data-ttu-id="f638c-181">指定要创建的审核文件的数目，最高为 2,147,483,647。</span><span class="sxs-lookup"><span data-stu-id="f638c-181">Specifies the number of audit files to be created, up to 2,147,483,647.</span></span> <span data-ttu-id="f638c-182">只有取消选中 **“无限制”** 时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="f638c-182">This option is only available if **Unlimited** is unchecked.</span></span>  
  
     <span data-ttu-id="f638c-183">**最大文件大小**</span><span class="sxs-lookup"><span data-stu-id="f638c-183">**Maximum file size**</span></span>  
     <span data-ttu-id="f638c-184">指定审核文件的最大大小，可以兆字节 (MB)、千兆字节 (GB) 或百万兆字节 (TB) 为单位。</span><span class="sxs-lookup"><span data-stu-id="f638c-184">Specifies the maximum size for an audit file in either megabytes (MB), gigabytes (GB), or terabytes (TB).</span></span> <span data-ttu-id="f638c-185">您可以指定 1024 MB 至 2,147,483,647 TB 之间的值。</span><span class="sxs-lookup"><span data-stu-id="f638c-185">You can specify between 1024 MB and 2,147,483,647 TB.</span></span> <span data-ttu-id="f638c-186">选中 **“无限制”** 复选框将不会对文件大小施加限制。</span><span class="sxs-lookup"><span data-stu-id="f638c-186">Selecting the **Unlimited** check box does not place a limit on the size of the file.</span></span> <span data-ttu-id="f638c-187">指定一个小于 1024 MB 的值将失败，并且返回错误。</span><span class="sxs-lookup"><span data-stu-id="f638c-187">Specifying a value lower than 1024 MB will fail, returning an error.</span></span> <span data-ttu-id="f638c-188">默认情况下， **“无限制”** 复选框为选中状态。</span><span class="sxs-lookup"><span data-stu-id="f638c-188">The **Unlimited** check box is selected by default.</span></span>  
  
     <span data-ttu-id="f638c-189">“保留磁盘空间”  复选框</span><span class="sxs-lookup"><span data-stu-id="f638c-189">**Reserve disk space** check box</span></span>  
     <span data-ttu-id="f638c-190">指定在磁盘上预先分配与指定的最大文件大小相等的空间。</span><span class="sxs-lookup"><span data-stu-id="f638c-190">Specifies that space is pre-allocated on the disk equal to the specified maximum file size.</span></span> <span data-ttu-id="f638c-191">只有在 **“最大文件大小”** 下未选中 **“无限制”** 复选框的情况下，才能使用此设置。</span><span class="sxs-lookup"><span data-stu-id="f638c-191">This setting can only be used if the **Unlimited** check box under **Maximum file size** is not selected.</span></span> <span data-ttu-id="f638c-192">默认情况下，不选中此复选框。</span><span class="sxs-lookup"><span data-stu-id="f638c-192">This check box is not selected by default.</span></span>  
  
3.  <span data-ttu-id="f638c-193">或者，在 **“筛选器”** 页上，对服务器审核输入一个谓词或 `WHERE` 子句，以便指定在 **“常规”** 页上未提供的附加选项。</span><span class="sxs-lookup"><span data-stu-id="f638c-193">Optionally, on the **Filter** page, enter a predicate, or `WHERE` clause, to the server audit to specify additional options not available from the **General** page.</span></span> <span data-ttu-id="f638c-194">用小括号将该谓词括起来，例如 `(object_name = 'EmployeesTable')`。</span><span class="sxs-lookup"><span data-stu-id="f638c-194">Enclose the predicate in parentheses; for example: `(object_name = 'EmployeesTable')`.</span></span>  
  
4.  <span data-ttu-id="f638c-195">在完成选项选择后，请单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="f638c-195">When you are finished selecting options, click **OK**.</span></span>  
  
#### <a name="to-create-a-server-audit-specification"></a><span data-ttu-id="f638c-196">创建服务器审核规范</span><span class="sxs-lookup"><span data-stu-id="f638c-196">To create a server audit specification</span></span>  
  
1.  <span data-ttu-id="f638c-197">在对象资源管理器中，右键单击加号以展开 **“安全性”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="f638c-197">In Object Explorer, click the plus sign to expand the **Security** folder.</span></span>  
  
2.  <span data-ttu-id="f638c-198">右键单击“服务器审核规范”文件夹，然后选择“新建服务器审核规范…”   。</span><span class="sxs-lookup"><span data-stu-id="f638c-198">Right-click the **Server Audit Specifications** folder and select **New Server Audit Specification...**.</span></span>  
  
     <span data-ttu-id="f638c-199">**“创建服务器审核规范”** 对话框中提供了以下选项。</span><span class="sxs-lookup"><span data-stu-id="f638c-199">The following options are available on the **Create Server Audit Specification** dialog box.</span></span>  
  
     <span data-ttu-id="f638c-200">**名称**</span><span class="sxs-lookup"><span data-stu-id="f638c-200">**Name**</span></span>  
     <span data-ttu-id="f638c-201">服务器审核规范的名称。</span><span class="sxs-lookup"><span data-stu-id="f638c-201">The name of the server audit specification.</span></span> <span data-ttu-id="f638c-202">这是在创建新服务器审核规范时自动生成的，但是您可以对其进行编辑。</span><span class="sxs-lookup"><span data-stu-id="f638c-202">This is generated automatically when you create a new server audit specification but is editable.</span></span>  
  
     <span data-ttu-id="f638c-203">**审核**</span><span class="sxs-lookup"><span data-stu-id="f638c-203">**Audit**</span></span>  
     <span data-ttu-id="f638c-204">现有服务器审核的名称。</span><span class="sxs-lookup"><span data-stu-id="f638c-204">The name of an existing server audit.</span></span> <span data-ttu-id="f638c-205">或者键入审核的名称，或者从列表中选择一个名称。</span><span class="sxs-lookup"><span data-stu-id="f638c-205">Either type in the name of the audit or select it from the list.</span></span>  
  
     <span data-ttu-id="f638c-206">**审核操作类型**</span><span class="sxs-lookup"><span data-stu-id="f638c-206">**Audit Action Type**</span></span>  
     <span data-ttu-id="f638c-207">指定要捕获的服务器级别审核操作组和审核操作。</span><span class="sxs-lookup"><span data-stu-id="f638c-207">Specifies the server-level audit action groups and audit actions to capture.</span></span> <span data-ttu-id="f638c-208">有关服务器级别审核操作组和审核操作的列表以及它们所包含事件的说明，请参阅 [SQL Server 审核操作组和操作](sql-server-audit-action-groups-and-actions.md)。</span><span class="sxs-lookup"><span data-stu-id="f638c-208">For the list of server-level audit action groups and audit actions and a description of the events they contain, see [SQL Server Audit Action Groups and Actions](sql-server-audit-action-groups-and-actions.md).</span></span>  
  
     <span data-ttu-id="f638c-209">**对象架构**</span><span class="sxs-lookup"><span data-stu-id="f638c-209">**Object Schema**</span></span>  
     <span data-ttu-id="f638c-210">显示具有指定“对象名称”  的对象的架构。</span><span class="sxs-lookup"><span data-stu-id="f638c-210">Displays the schema for the specified **Object Name**.</span></span>  
  
     <span data-ttu-id="f638c-211">**Object Name**</span><span class="sxs-lookup"><span data-stu-id="f638c-211">**Object Name**</span></span>  
     <span data-ttu-id="f638c-212">要审核的对象的名称。</span><span class="sxs-lookup"><span data-stu-id="f638c-212">The name of the object to audit.</span></span> <span data-ttu-id="f638c-213">这仅适用于审核操作，而不适用于审核组。</span><span class="sxs-lookup"><span data-stu-id="f638c-213">This is only available for audit actions; it does not apply to audit groups.</span></span>  
  
     <span data-ttu-id="f638c-214">**省略号 (...)**</span><span class="sxs-lookup"><span data-stu-id="f638c-214">**Ellipsis (...)**</span></span>  
     <span data-ttu-id="f638c-215">打开 **“选择对象”** 对话框，以便基于指定的 **“审核操作类型”** 浏览和选择可用对象。</span><span class="sxs-lookup"><span data-stu-id="f638c-215">Opens the **Select Objects** dialog to browse for and select an available object, based on the specified **Audit Action Type**.</span></span>  
  
     <span data-ttu-id="f638c-216">**主体名称**</span><span class="sxs-lookup"><span data-stu-id="f638c-216">**Principal Name**</span></span>  
     <span data-ttu-id="f638c-217">对于所审核的对象，要作为审核筛选依据的帐户。</span><span class="sxs-lookup"><span data-stu-id="f638c-217">The account to filter the audit by for the object being audited.</span></span>  
  
     <span data-ttu-id="f638c-218">**省略号 (...)**</span><span class="sxs-lookup"><span data-stu-id="f638c-218">**Ellipsis (...)**</span></span>  
     <span data-ttu-id="f638c-219">打开 **“选择对象”** 对话框以基于指定的 **“对象名称”** 浏览和选择可用对象。</span><span class="sxs-lookup"><span data-stu-id="f638c-219">Opens the **Select Objects** dialog to browse for and select an available object, based on the specified **Object Name**.</span></span>  
  
3.  <span data-ttu-id="f638c-220">完成后，单击“**确定**”。</span><span class="sxs-lookup"><span data-stu-id="f638c-220">When you are finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f638c-221">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f638c-221">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-server-audit"></a><span data-ttu-id="f638c-222">创建服务器审核</span><span class="sxs-lookup"><span data-stu-id="f638c-222">To create a server audit</span></span>  
  
1.  <span data-ttu-id="f638c-223">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="f638c-223">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f638c-224">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="f638c-224">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f638c-225">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="f638c-225">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates a server audit called "HIPAA_Audit" with a binary file as the target and no options.  
    CREATE SERVER AUDIT HIPAA_Audit  
        TO FILE ( FILEPATH ='\\SQLPROD_1\Audit\' );  
    ```  
  
#### <a name="to-create-a-server-audit-specification"></a><span data-ttu-id="f638c-226">创建服务器审核规范</span><span class="sxs-lookup"><span data-stu-id="f638c-226">To create a server audit specification</span></span>  
  
1.  <span data-ttu-id="f638c-227">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="f638c-227">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f638c-228">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="f638c-228">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f638c-229">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="f638c-229">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    /*Creates a server audit specification called "HIPAA_Audit_Specification" that audits failed logins for the SQL Server audit "HIPAA_Audit" created above.  
    */  
  
    CREATE SERVER AUDIT SPECIFICATION HIPAA_Audit_Specification  
    FOR SERVER AUDIT HIPAA_Audit  
        ADD (FAILED_LOGIN_GROUP);  
    GO  
    -- Enables the audit.   
  
    ALTER SERVER AUDIT HIPAA_Audit  
    WITH (STATE = ON);  
    GO  
    ```  
  
 <span data-ttu-id="f638c-230">有关详细信息，请参阅 [CREATE SERVER AUDIT (Transact-SQL)](/sql/t-sql/statements/create-server-audit-transact-sql) 和 [CREATE SERVER AUDIT SPECIFICATION (Transact-SQL)](/sql/t-sql/statements/create-server-audit-specification-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f638c-230">For more information, see [CREATE SERVER AUDIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-transact-sql) and [CREATE SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-specification-transact-sql).</span></span>  
  
  
