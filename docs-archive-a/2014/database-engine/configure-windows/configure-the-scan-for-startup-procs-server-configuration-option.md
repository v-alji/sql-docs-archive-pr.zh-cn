---
title: 配置 scan for startup procs 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- scan for startup procs option
ms.assetid: 6bf9d252-e766-458d-9dcd-23d895f032a2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fbf46fc7476e6e879991cfe3f649fd5617f3275e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580361"
---
# <a name="configure-the-scan-for-startup-procs-server-configuration-option"></a><span data-ttu-id="ec4af-102">配置 scan for startup procs 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="ec4af-102">Configure the scan for startup procs Server Configuration Option</span></span>
  <span data-ttu-id="ec4af-103">本主题说明如何使用 **或** 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中配置 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] scan for startup procs [!INCLUDE[tsql](../../includes/tsql-md.md)]服务器配置选项。</span><span class="sxs-lookup"><span data-stu-id="ec4af-103">This topic describes how to configure the **scan for startup procs** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="ec4af-104">使用 **scan for startup procs** 选项扫描在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 启动时自动执行的存储过程。</span><span class="sxs-lookup"><span data-stu-id="ec4af-104">Use the **scan for startup procs** option to scan for automatic execution of stored procedures at [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] startup time.</span></span> <span data-ttu-id="ec4af-105">如果将此选项设置为 1，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将扫描服务器上定义的所有自动运行的存储过程，并运行这些过程。</span><span class="sxs-lookup"><span data-stu-id="ec4af-105">If this option is set to 1, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] scans for and runs all automatically run stored procedures that are defined on the server.</span></span> <span data-ttu-id="ec4af-106">**scan for startup procs** 的默认值为 0（不扫描）。</span><span class="sxs-lookup"><span data-stu-id="ec4af-106">The default value for **scan for startup procs** is 0 (do not scan).</span></span>  
  
 <span data-ttu-id="ec4af-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="ec4af-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ec4af-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="ec4af-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ec4af-109">建议</span><span class="sxs-lookup"><span data-stu-id="ec4af-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="ec4af-110">安全性</span><span class="sxs-lookup"><span data-stu-id="ec4af-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ec4af-111">**若要配置 scan for startup procs 选项，请使用：**</span><span class="sxs-lookup"><span data-stu-id="ec4af-111">**To configure the scan for startup procs option, using:**</span></span>  
  
     [<span data-ttu-id="ec4af-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ec4af-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ec4af-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ec4af-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="ec4af-114">**跟进：** [在配置 scan for startup procs 选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="ec4af-114">**Follow Up:**  [After you configure the scan for startup procs option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ec4af-115">开始之前</span><span class="sxs-lookup"><span data-stu-id="ec4af-115">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="ec4af-116">建议</span><span class="sxs-lookup"><span data-stu-id="ec4af-116">Recommendations</span></span>  
  
-   <span data-ttu-id="ec4af-117">此选项是一个高级选项，仅应由有经验的数据库管理员或认证的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技术人员更改。</span><span class="sxs-lookup"><span data-stu-id="ec4af-117">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="ec4af-118">此选项的值可以使用 **sp_configure**进行设置；但是，如果使用 **sp_procoption**（用于标记或取消标记自动执行的存储过程），则会自动进行设置。</span><span class="sxs-lookup"><span data-stu-id="ec4af-118">The value for this option can be set by using **sp_configure**; however, it will be set automatically if you use **sp_procoption**, which is used to mark or unmark automatically run stored procedures.</span></span> <span data-ttu-id="ec4af-119">使用 **sp_procoption** 将第一个存储过程标记为自动执行过程后，此选项的值自动设置为 1。</span><span class="sxs-lookup"><span data-stu-id="ec4af-119">When **sp_procoption** is used to mark the first stored procedure as an autoproc, this option is set automatically to a value of 1.</span></span> <span data-ttu-id="ec4af-120">使用 **sp_procoption** 将最后一个存储过程标记为自动执行过程后，此选项的值自动设置为 0。</span><span class="sxs-lookup"><span data-stu-id="ec4af-120">When **sp_procoption** is used to unmark the last stored procedure as an autoproc, this option is automatically set to a value of 0.</span></span> <span data-ttu-id="ec4af-121">如果使用 **sp_procoption** 标记或取消标记自动执行过程，并且始终在删除自动执行过程之前进行取消标记，则无需手动设置此选项。</span><span class="sxs-lookup"><span data-stu-id="ec4af-121">If you use **sp_procoption** to mark and unmark autoprocs, and if you always unmark autoprocs before dropping them, there is no need to set this option manually.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ec4af-122">Security</span><span class="sxs-lookup"><span data-stu-id="ec4af-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ec4af-123">权限</span><span class="sxs-lookup"><span data-stu-id="ec4af-123">Permissions</span></span>  
 <span data-ttu-id="ec4af-124">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="ec4af-124">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="ec4af-125">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="ec4af-125">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="ec4af-126">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="ec4af-126">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ec4af-127">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ec4af-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-scan-for-startup-procs-option"></a><span data-ttu-id="ec4af-128">配置 scan for startup procs 选项</span><span class="sxs-lookup"><span data-stu-id="ec4af-128">To configure the scan for startup procs option</span></span>  
  
1.  <span data-ttu-id="ec4af-129">在对象资源管理器中，右键单击服务器并选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="ec4af-129">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="ec4af-130">单击 **“高级”** 节点。</span><span class="sxs-lookup"><span data-stu-id="ec4af-130">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="ec4af-131">在“杂项”下，通过从下拉列表框中选择所需值将“启动时扫描存储过程”选项更改为 True 或 False。</span><span class="sxs-lookup"><span data-stu-id="ec4af-131">Under **Miscellaneous**, change the **Scan for Startup Procs** option to True or False by selecting the value you want from the drop-down list box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ec4af-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ec4af-132">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-scan-for-startup-procs-option"></a><span data-ttu-id="ec4af-133">配置 scan for startup procs 选项</span><span class="sxs-lookup"><span data-stu-id="ec4af-133">To configure the scan for startup procs option</span></span>  
  
1.  <span data-ttu-id="ec4af-134">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ec4af-134">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ec4af-135">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="ec4af-135">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ec4af-136">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="ec4af-136">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="ec4af-137">此示例说明如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将 `scan for startup procs` 选项的值设置为 `1`。</span><span class="sxs-lookup"><span data-stu-id="ec4af-137">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `scan for startup procs` option to `1`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'scan for startup procs', 1 ;  
GO  
RECONFIGURE  
GO  
  
```  
  
##  <a name="follow-up-after-you-configure-the-scan-for-startup-procs-option"></a><a name="FollowUp"></a> <span data-ttu-id="ec4af-138">跟进：在配置 scan for startup procs 选项之后</span><span class="sxs-lookup"><span data-stu-id="ec4af-138">Follow Up: After you configure the scan for startup procs option</span></span>  
 <span data-ttu-id="ec4af-139">必须重新启动服务器，设置才会生效。</span><span class="sxs-lookup"><span data-stu-id="ec4af-139">The server must be restarted before the setting can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec4af-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ec4af-140">See Also</span></span>  
 <span data-ttu-id="ec4af-141">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ec4af-141">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="ec4af-142">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ec4af-142">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="ec4af-143">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ec4af-143">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="ec4af-144">sp_procoption (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ec4af-144">sp_procoption &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql)  
  
  
