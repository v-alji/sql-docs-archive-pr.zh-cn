---
title: 设置目标服务器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.tsxwiz.msx.f1
- sql12.ag.tsxwiz.cover.f1
- sql12.ag.tsxwiz.credentials.f1
- sql12.ag.tsxwiz.complete.f1
helpviewer_keywords:
- Target Server Wizard
- SQL Server Agent jobs, target servers
- target servers [SQL Server], creating
ms.assetid: 13aabe2d-67fe-4c67-8d49-2928dd705b7a
author: stevestein
ms.author: sstein
ms.openlocfilehash: bd60a19234d186bb0912978589fa60fd8e8a8c22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682660"
---
# <a name="make-a-target-server"></a><span data-ttu-id="4be73-102">设置目标服务器</span><span class="sxs-lookup"><span data-stu-id="4be73-102">Make a Target Server</span></span>
  <span data-ttu-id="4be73-103">本主题说明如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 SQL Server 管理对象 (SMO) 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中生成目标服务器。</span><span class="sxs-lookup"><span data-stu-id="4be73-103">This topic describes how to make a target server in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects (SMO).</span></span>  
  
 <span data-ttu-id="4be73-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="4be73-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4be73-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="4be73-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4be73-106">安全性</span><span class="sxs-lookup"><span data-stu-id="4be73-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4be73-107">**若要生成目标服务器，请使用：**</span><span class="sxs-lookup"><span data-stu-id="4be73-107">**To make a target server, using:**</span></span>  
  
     [<span data-ttu-id="4be73-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4be73-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4be73-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4be73-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="4be73-110">SMO</span><span class="sxs-lookup"><span data-stu-id="4be73-110">SMO</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4be73-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="4be73-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4be73-112">Security</span><span class="sxs-lookup"><span data-stu-id="4be73-112">Security</span></span>  
 <span data-ttu-id="4be73-113">如果分布式作业的步骤与某个代理相关联，则该作业将在目标服务器上该代理帐户的上下文下运行。</span><span class="sxs-lookup"><span data-stu-id="4be73-113">Distributed jobs that have steps which are associated with a proxy run under the context of the proxy account on the target server.</span></span> <span data-ttu-id="4be73-114">请确保满足以下条件，否则与代理关联的作业步骤将不会从主服务器下载到目标服务器上：</span><span class="sxs-lookup"><span data-stu-id="4be73-114">Make sure that the following conditions are met or job steps that are associated with a proxy will not be downloaded from the master server to the target:</span></span>  
  
-   <span data-ttu-id="4be73-115">主服务器注册表子项**\ HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL Server \\ < *instance_name*> \sql server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) 设置为 1 () 为 true。</span><span class="sxs-lookup"><span data-stu-id="4be73-115">The master server registry subkey **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<*instance_name*>\SQL Server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) is set to 1 (true).</span></span> <span data-ttu-id="4be73-116">默认情况下，此子项设置为 0 (False)。</span><span class="sxs-lookup"><span data-stu-id="4be73-116">By default, this subkey is set to 0 (false).</span></span>  
  
-   <span data-ttu-id="4be73-117">目标服务器上已存在与运行作业步骤的主服务器代理帐户同名的代理帐户。</span><span class="sxs-lookup"><span data-stu-id="4be73-117">A proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.</span></span>  
  
 <span data-ttu-id="4be73-118">从主服务器将使用代理帐户的作业步骤下载到目标服务器时，如果作业步骤失败，可以检查 **msdb** 数据库中 **sysdownloadlist** 表的 **error_message** 列是否存在以下错误消息：</span><span class="sxs-lookup"><span data-stu-id="4be73-118">If job steps that use proxy accounts fail when downloading them from the master server to the target server, you can check the **error_message** column in the **sysdownloadlist** table in the **msdb** database for the following error messages:</span></span>  
  
-   <span data-ttu-id="4be73-119">“该作业步骤需要代理帐户，但是目标服务器上禁用了代理匹配功能。”</span><span class="sxs-lookup"><span data-stu-id="4be73-119">"The job step requires a proxy account, however proxy matching is disabled on the target server."</span></span>  
  
     <span data-ttu-id="4be73-120">若要解决此错误，请将 **AllowDownloadedJobsToMatchProxyName** 注册表子项设置为 1。</span><span class="sxs-lookup"><span data-stu-id="4be73-120">To resolve this error, set the **AllowDownloadedJobsToMatchProxyName** registry subkey to 1.</span></span>  
  
-   <span data-ttu-id="4be73-121">“找不到代理。”</span><span class="sxs-lookup"><span data-stu-id="4be73-121">"Proxy not found."</span></span>  
  
     <span data-ttu-id="4be73-122">若要解决此错误，请确保目标服务器上已存在与运行作业步骤的主服务器代理帐户同名的代理帐户。</span><span class="sxs-lookup"><span data-stu-id="4be73-122">To resolve this error, make sure a proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4be73-123">权限</span><span class="sxs-lookup"><span data-stu-id="4be73-123">Permissions</span></span>  
 <span data-ttu-id="4be73-124">默认情况下授予  固定服务器角色的成员执行此过程的权限。</span><span class="sxs-lookup"><span data-stu-id="4be73-124">Permissions to execute this procedure default to members of the `sysadmin` fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4be73-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4be73-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-make-a-target-server"></a><span data-ttu-id="4be73-126">生成目标服务器</span><span class="sxs-lookup"><span data-stu-id="4be73-126">To make a target server</span></span>  
  
1.  <span data-ttu-id="4be73-127">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="4be73-127">In **Object Explorer,** connect to an instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="4be73-128">右键单击“SQL Server 代理”\*\*\*\*，指向“多服务器管理”\*\*\*\*，然后单击“使其成为目标服务器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4be73-128">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Make this a Target**.</span></span> <span data-ttu-id="4be73-129">**“目标服务器向导”** 会指导您完成生成目标服务器的过程。</span><span class="sxs-lookup"><span data-stu-id="4be73-129">The **Target Server Wizard** guides you through the process of making a target server.</span></span>  
  
3.  <span data-ttu-id="4be73-130">从 **“选择主服务器”** 页中，选择此目标服务器将从中接收作业的主服务器。</span><span class="sxs-lookup"><span data-stu-id="4be73-130">From the **Select a Master Server** page, select the master server that this target server will receive jobs from.</span></span>  
  
     <span data-ttu-id="4be73-131">**选取服务器**</span><span class="sxs-lookup"><span data-stu-id="4be73-131">**Pick Server**</span></span>  
     <span data-ttu-id="4be73-132">连接到主服务器。</span><span class="sxs-lookup"><span data-stu-id="4be73-132">Connect to the master server.</span></span>  
  
     <span data-ttu-id="4be73-133">**此服务器的说明**</span><span class="sxs-lookup"><span data-stu-id="4be73-133">**Description of this server**</span></span>  
     <span data-ttu-id="4be73-134">键入此目标服务器的说明。</span><span class="sxs-lookup"><span data-stu-id="4be73-134">Type a description for this target server.</span></span> <span data-ttu-id="4be73-135">目标服务器将此说明上载到主服务器。</span><span class="sxs-lookup"><span data-stu-id="4be73-135">The target server uploads this description to the master server.</span></span>  
  
4.  <span data-ttu-id="4be73-136">从 **“主服务器登录凭据”** 页中，在目标服务器上创建新的登录（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="4be73-136">From the **Master Server Login Credentials** page, create a new login on the target server, if necessary.</span></span>  
  
     <span data-ttu-id="4be73-137">**在必要时创建新登录名，并为其分配针对 MSX 的权限**</span><span class="sxs-lookup"><span data-stu-id="4be73-137">**Create a new login if necessary and assign it rights to the MSX**</span></span>  
     <span data-ttu-id="4be73-138">如果指定的登录名不存在，则在目标服务器上创建新登录名。</span><span class="sxs-lookup"><span data-stu-id="4be73-138">Create a new login on the target server if the login specified does not already exist.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4be73-139">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4be73-139">Using Transact-SQL</span></span>  
  
#### <a name="to-make-a-target-server"></a><span data-ttu-id="4be73-140">生成目标服务器</span><span class="sxs-lookup"><span data-stu-id="4be73-140">To make a target server</span></span>  
  
1.  <span data-ttu-id="4be73-141">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4be73-141">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4be73-142">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="4be73-142">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4be73-143">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="4be73-143">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="4be73-144">本示例将当前服务器登记到 AdventureWorks1 主服务器中。</span><span class="sxs-lookup"><span data-stu-id="4be73-144">This example enlists the current server into the AdventureWorks1 master server.</span></span> <span data-ttu-id="4be73-145">当前服务器的位置是 Building 21、Room 309、Rack 5。</span><span class="sxs-lookup"><span data-stu-id="4be73-145">The location for the current server is Building 21, Room 309, Rack 5.</span></span>  
  
    ```sql
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_msx_enlist N'AdventureWorks1',   
        N'Building 21, Room 309, Rack 5' ;   
    GO;  
    ```  
  
     <span data-ttu-id="4be73-146">有关详细信息，请参阅[&#40;transact-sql&#41;sp_msx_enlist ](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4be73-146">For more information, see [sp_msx_enlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects-smo"></a><a name="PowerShellProcedure"></a><span data-ttu-id="4be73-147">使用 SQL Server 管理对象 (SMO) </span><span class="sxs-lookup"><span data-stu-id="4be73-147">Using SQL Server Management Objects (SMO)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4be73-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4be73-148">See Also</span></span>  
 [<span data-ttu-id="4be73-149">企业范围的自动化管理</span><span class="sxs-lookup"><span data-stu-id="4be73-149">Automated Administration Across an Enterprise</span></span>](automated-administration-across-an-enterprise.md)  
