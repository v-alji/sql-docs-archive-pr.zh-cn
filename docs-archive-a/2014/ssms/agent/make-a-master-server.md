---
title: 设置主服务器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.msxwiz.complete.f1
- sql12.ag.msxwiz.target.f1
- sql12.ag.msxwiz.login.f1
- sql12.ag.msxwiz.cover.f1
- sql12.ag.msxwiz.operator.f1
helpviewer_keywords:
- master servers [SQL Server], creating
- wizards [SQL Server Management Studio], Master Server Wizard
- SQL Server Agent jobs, master servers
- Master Server Wizard
ms.assetid: 05739a73-1fdf-4d9d-92a6-70f328380322
author: stevestein
ms.author: sstein
ms.openlocfilehash: ce8e7428aaf8ba459bcf6831988c61da3f192bac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586055"
---
# <a name="make-a-master-server"></a><span data-ttu-id="bb2d4-102">Make a Master Server</span><span class="sxs-lookup"><span data-stu-id="bb2d4-102">Make a Master Server</span></span>
  <span data-ttu-id="bb2d4-103">本主题描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 设置主服务器 [!INCLUDE[tsql](../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-103">This topic describes how to make a master server [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="bb2d4-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="bb2d4-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="bb2d4-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="bb2d4-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="bb2d4-106">安全性</span><span class="sxs-lookup"><span data-stu-id="bb2d4-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="bb2d4-107">**若要设置主服务器，请使用：**</span><span class="sxs-lookup"><span data-stu-id="bb2d4-107">**To make a master server, using:**</span></span>  
  
     [<span data-ttu-id="bb2d4-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bb2d4-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="bb2d4-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bb2d4-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="bb2d4-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="bb2d4-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="bb2d4-111">Security</span><span class="sxs-lookup"><span data-stu-id="bb2d4-111">Security</span></span>  
 <span data-ttu-id="bb2d4-112">如果分布式作业的步骤与某个代理相关联，则该作业将在目标服务器上该代理帐户的上下文下运行。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-112">Distributed jobs that have steps which are associated with a proxy run under the context of the proxy account on the target server.</span></span> <span data-ttu-id="bb2d4-113">请确保满足以下条件，否则与代理关联的作业步骤将不会从主服务器下载到目标服务器上：</span><span class="sxs-lookup"><span data-stu-id="bb2d4-113">Make sure that the following conditions are met or job steps that are associated with a proxy will not be downloaded from the master server to the target:</span></span>  
  
-   <span data-ttu-id="bb2d4-114">主服务器注册表子项**\ HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL Server \\ < *instance_name*> \sql server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) 设置为 1 () 为 true。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-114">The master server registry subkey **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<*instance_name*>\SQL Server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) is set to 1 (true).</span></span> <span data-ttu-id="bb2d4-115">默认情况下，此子项设置为 0 (False)。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-115">By default, this subkey is set to 0 (false).</span></span>  
  
-   <span data-ttu-id="bb2d4-116">目标服务器上已存在与运行作业步骤的主服务器代理帐户同名的代理帐户。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-116">A proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.</span></span>  
  
 <span data-ttu-id="bb2d4-117">从主服务器将使用代理帐户的作业步骤下载到目标服务器时，如果作业步骤失败，可以检查 **msdb** 数据库中 **sysdownloadlist** 表的 **error_message** 列是否存在以下错误消息：</span><span class="sxs-lookup"><span data-stu-id="bb2d4-117">If job steps that use proxy accounts fail when downloading them from the master server to the target server, you can check the **error_message** column in the **sysdownloadlist** table in the **msdb** database for the following error messages:</span></span>  
  
-   <span data-ttu-id="bb2d4-118">“该作业步骤需要代理帐户，但是目标服务器上禁用了代理匹配功能。”</span><span class="sxs-lookup"><span data-stu-id="bb2d4-118">"The job step requires a proxy account, however proxy matching is disabled on the target server."</span></span>  
  
     <span data-ttu-id="bb2d4-119">若要解决此错误，请将 **AllowDownloadedJobsToMatchProxyName** 注册表子项设置为 1。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-119">To resolve this error, set the **AllowDownloadedJobsToMatchProxyName** registry subkey to 1.</span></span>  
  
-   <span data-ttu-id="bb2d4-120">“找不到代理。”</span><span class="sxs-lookup"><span data-stu-id="bb2d4-120">"Proxy not found."</span></span>  
  
     <span data-ttu-id="bb2d4-121">若要解决此错误，请确保目标服务器上已存在与运行作业步骤的主服务器代理帐户同名的代理帐户。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-121">To resolve this error, make sure a proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="bb2d4-122">权限</span><span class="sxs-lookup"><span data-stu-id="bb2d4-122">Permissions</span></span>  
 <span data-ttu-id="bb2d4-123">默认情况下授予  固定服务器角色的成员执行此过程的权限。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-123">Permissions to execute this procedure default to members of the `sysadmin` fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="bb2d4-124">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bb2d4-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-make-a-master-server"></a><span data-ttu-id="bb2d4-125">设置主服务器</span><span class="sxs-lookup"><span data-stu-id="bb2d4-125">To make a master server</span></span>  
  
1.  <span data-ttu-id="bb2d4-126">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-126">In **Object Explorer,** connect to an instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="bb2d4-127">右键单击“SQL Server 代理”\*\*\*\*，指向“多服务器管理”\*\*\*\*，再单击“将其设置为主服务器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-127">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Make this a Master**.</span></span> <span data-ttu-id="bb2d4-128">**主服务器向导** 将引导您完成设置主服务器和添加目标服务器的过程。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-128">The **Master Server Wizard** guides you through the process of making a master server and adding target servers.</span></span>  
  
3.  <span data-ttu-id="bb2d4-129">从“主服务器操作员”\*\*\*\* 中，配置主服务器的操作员。若要通过电子邮件或寻呼程序向操作员发送通知，必须配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理以发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-129">From the **Master Server Operator** page, configure an operator for the master server To send notifications to operators by using e-mail or pagers, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to send e-mail.</span></span> <span data-ttu-id="bb2d4-130">若要使用 **net send**向操作员发送通知，必须在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理所在的服务器上运行 Messenger 服务。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-130">To send notifications to operators by using **net send**, the Messenger service must be running on the server where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent resides.</span></span>  
  
     <span data-ttu-id="bb2d4-131">**电子邮件地址**</span><span class="sxs-lookup"><span data-stu-id="bb2d4-131">**E-mail address**</span></span>  
     <span data-ttu-id="bb2d4-132">设置操作员的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-132">Sets the e-mail address for the operator.</span></span>  
  
     <span data-ttu-id="bb2d4-133">**寻呼地址**</span><span class="sxs-lookup"><span data-stu-id="bb2d4-133">**Pager address**</span></span>  
     <span data-ttu-id="bb2d4-134">设置操作员的寻呼电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-134">Sets the pager e-mail address for the operator.</span></span>  
  
     <span data-ttu-id="bb2d4-135">**Net send 地址**</span><span class="sxs-lookup"><span data-stu-id="bb2d4-135">**Net send address**</span></span>  
     <span data-ttu-id="bb2d4-136">设置操作员的 **net send** 地址。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-136">Sets the **net send** address for the operator.</span></span>  
  
4.  <span data-ttu-id="bb2d4-137">从 **“目标服务器”** 页中，为主服务器选择目标服务器。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-137">From the **Target Server** page, select target servers for the master server.</span></span>  
  
     <span data-ttu-id="bb2d4-138">**已注册的服务器**</span><span class="sxs-lookup"><span data-stu-id="bb2d4-138">**Registered Servers**</span></span>  
     <span data-ttu-id="bb2d4-139">列出已在 Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中注册但尚未成为目标服务器的服务器。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-139">Lists the servers registered in Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] that are not already target servers.</span></span>  
  
     <span data-ttu-id="bb2d4-140">**目标服务器**</span><span class="sxs-lookup"><span data-stu-id="bb2d4-140">**Target Servers**</span></span>  
     <span data-ttu-id="bb2d4-141">列出已经为目标服务器的服务器。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-141">Lists the servers that are target servers.</span></span>  
  
     **>**  
     <span data-ttu-id="bb2d4-142">将所选服务器移动到目标服务器列表中。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-142">Move the selected server to the target server list.</span></span>  
  
     **>>**  
     <span data-ttu-id="bb2d4-143">将所有服务器移动到目标服务器列表中。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-143">Move all servers to the target server list.</span></span>  
  
     **<**  
     <span data-ttu-id="bb2d4-144">从目标服务器列表中删除所选服务器。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-144">Remove the selected server from the target server list.</span></span>  
  
     **<<**  
     <span data-ttu-id="bb2d4-145">从目标服务器列表中删除所有服务器。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-145">Remove all servers from the target server list.</span></span>  
  
     <span data-ttu-id="bb2d4-146">**添加连接**</span><span class="sxs-lookup"><span data-stu-id="bb2d4-146">**Add connection**</span></span>  
     <span data-ttu-id="bb2d4-147">向目标服务器列表中添加服务器，但不注册该服务器。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-147">Add a server to the target server list without registering the server.</span></span>  
  
     <span data-ttu-id="bb2d4-148">**Connection**</span><span class="sxs-lookup"><span data-stu-id="bb2d4-148">**Connection**</span></span>  
     <span data-ttu-id="bb2d4-149">更改所选服务器的连接属性。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-149">Change the connection properties for the selected server.</span></span>  
  
5.  <span data-ttu-id="bb2d4-150">从 **“主服务器登录凭据”** 页中，指定是否要在必要时为目标服务器创建新的登录名，并为其分配针对主服务器的权限。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-150">From the **Master Server Login Credentials** page to specify if you want to create a new login for the target server, if necessary, and assign it rights to the master server.</span></span>  
  
     <span data-ttu-id="bb2d4-151">**在必要时创建新登录名，并为其分配针对 MSX 的权限**</span><span class="sxs-lookup"><span data-stu-id="bb2d4-151">**Create a new login if necessary and assign it rights to the MSX**</span></span>  
     <span data-ttu-id="bb2d4-152">如果指定的登录名不存在，则在目标服务器上创建新登录名。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-152">Create a new login on the target server if the login specified does not already exist.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="bb2d4-153">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bb2d4-153">Using Transact-SQL</span></span>  
  
#### <a name="to-make-a-master-server"></a><span data-ttu-id="bb2d4-154">设置主服务器</span><span class="sxs-lookup"><span data-stu-id="bb2d4-154">To make a master server</span></span>  
  
1.  <span data-ttu-id="bb2d4-155">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-155">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="bb2d4-156">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-156">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="bb2d4-157">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-157">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="bb2d4-158">本示例将当前服务器登记到 AdventureWorks1 主服务器中。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-158">This example enlists the current server into the AdventureWorks1 master server.</span></span> <span data-ttu-id="bb2d4-159">当前服务器的位置是 Building 21、Room 309、Rack 5。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-159">The location for the current server is Building 21, Room 309, Rack 5.</span></span>  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_msx_enlist N'AdventureWorks1',   
    N'Building 21, Room 309, Rack 5' ;   
GO;  
```  
  
 <span data-ttu-id="bb2d4-160">有关详细信息，请参阅[&#40;transact-sql&#41;sp_msx_enlist ](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="bb2d4-160">For more information, see [sp_msx_enlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb2d4-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bb2d4-161">See Also</span></span>  
 <span data-ttu-id="bb2d4-162">[创建多服务器环境](create-a-multiserver-environment.md) </span><span class="sxs-lookup"><span data-stu-id="bb2d4-162">[Create a Multiserver Environment](create-a-multiserver-environment.md) </span></span>  
 [<span data-ttu-id="bb2d4-163">企业范围的自动化管理</span><span class="sxs-lookup"><span data-stu-id="bb2d4-163">Automated Administration Across an Enterprise</span></span>](automated-administration-across-an-enterprise.md)  
  
  
