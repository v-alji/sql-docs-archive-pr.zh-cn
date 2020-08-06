---
title: 配置 remote access 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 10/19/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote servers [SQL Server], stored procedure execution
ms.assetid: f5de748d-1c55-4714-9661-38fe62e5095f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: eef18ec48ede59544b13545e49dc105909cfac16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578427"
---
# <a name="configure-the-remote-access-server-configuration-option"></a><span data-ttu-id="07f78-102">配置远程访问服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="07f78-102">Configure the remote access Server Configuration Option</span></span>
  <span data-ttu-id="07f78-103">本主题说明了如何使用 **或** 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中配置 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] “远程访问” [!INCLUDE[tsql](../../includes/tsql-md.md)]服务器配置选项。</span><span class="sxs-lookup"><span data-stu-id="07f78-103">This topic describes how to configure the **remote access** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="07f78-104">**“远程访问”** 选项从运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的本地或远程服务器上控制存储过程的执行。</span><span class="sxs-lookup"><span data-stu-id="07f78-104">The **remote access** option controls the execution of stored procedures from local or remote servers on which instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are running.</span></span> <span data-ttu-id="07f78-105">该选项的默认值为 1。</span><span class="sxs-lookup"><span data-stu-id="07f78-105">This default value for this option is 1.</span></span> <span data-ttu-id="07f78-106">这将授权允许从远程服务器执行本地存储过程或从本地服务器执行远程存储过程。</span><span class="sxs-lookup"><span data-stu-id="07f78-106">This grants permission to run local stored procedures from remote servers or remote stored procedures from the local server.</span></span> <span data-ttu-id="07f78-107">若要阻止本地存储过程在远程服务器上执行或远程存储过程在本地服务器上执行，请将此选项设置为 0。</span><span class="sxs-lookup"><span data-stu-id="07f78-107">To prevent local stored procedures from being run from a remote server or remote stored procedures from being run on the local server, set the option to 0.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] <span data-ttu-id="07f78-108">改用 [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="07f78-108">Use [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) instead.</span></span>  
  
 <span data-ttu-id="07f78-109">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="07f78-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="07f78-110">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="07f78-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="07f78-111">限制和局限</span><span class="sxs-lookup"><span data-stu-id="07f78-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="07f78-112">安全性</span><span class="sxs-lookup"><span data-stu-id="07f78-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="07f78-113">**若要配置远程访问选项，请使用：**</span><span class="sxs-lookup"><span data-stu-id="07f78-113">**To configure the remote access option, using:**</span></span>  
  
     [<span data-ttu-id="07f78-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="07f78-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="07f78-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="07f78-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="07f78-116">**跟进：** [在配置远程访问选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="07f78-116">**Follow Up:**  [After you configure the remote access option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="07f78-117">开始之前</span><span class="sxs-lookup"><span data-stu-id="07f78-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="07f78-118">限制和局限</span><span class="sxs-lookup"><span data-stu-id="07f78-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="07f78-119">“远程访问”选项仅适用于使用 [sp_addserver](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql) 添加的服务器，包括此选项是为了向后兼容。</span><span class="sxs-lookup"><span data-stu-id="07f78-119">The **remote access** option only applies to servers that are added by using [sp_addserver](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql), and is included for backward compatibility.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="07f78-120">Security</span><span class="sxs-lookup"><span data-stu-id="07f78-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="07f78-121">权限</span><span class="sxs-lookup"><span data-stu-id="07f78-121">Permissions</span></span>  
 <span data-ttu-id="07f78-122">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="07f78-122">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="07f78-123">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="07f78-123">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="07f78-124">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="07f78-124">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="07f78-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="07f78-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-remote-access-option"></a><span data-ttu-id="07f78-126">配置远程访问选项</span><span class="sxs-lookup"><span data-stu-id="07f78-126">To configure the remote access option</span></span>  
  
1.  <span data-ttu-id="07f78-127">在对象资源管理器中，右键单击服务器并选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="07f78-127">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="07f78-128">单击 **“连接”** 节点。</span><span class="sxs-lookup"><span data-stu-id="07f78-128">Click the **Connections** node.</span></span>  
  
3.  <span data-ttu-id="07f78-129">在 **“远程服务器连接”** 下，选中或清除 **“允许远程连接到此服务器”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="07f78-129">Under **Remote server connections**, select or clear the **Allow remote connections to this server** check box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="07f78-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="07f78-130">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-remote-access-option"></a><span data-ttu-id="07f78-131">配置远程访问选项</span><span class="sxs-lookup"><span data-stu-id="07f78-131">To configure the remote access option</span></span>  
  
1.  <span data-ttu-id="07f78-132">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="07f78-132">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="07f78-133">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="07f78-133">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="07f78-134">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="07f78-134">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="07f78-135">此示例说明如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将 `remote access` 选项的值设置为 `0`。</span><span class="sxs-lookup"><span data-stu-id="07f78-135">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `remote access` option to `0`.</span></span>  
  
```sql  
EXEC sp_configure 'remote access', 0 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 <span data-ttu-id="07f78-136">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="07f78-136">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-remote-access-option"></a><a name="FollowUp"></a> <span data-ttu-id="07f78-137">跟进：在配置远程访问选项之后</span><span class="sxs-lookup"><span data-stu-id="07f78-137">Follow Up: After you configure the remote access option</span></span>  
 <span data-ttu-id="07f78-138">此设置将在重启 SQL Server 之后生效。</span><span class="sxs-lookup"><span data-stu-id="07f78-138">This setting does not take effect until you restart SQL Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07f78-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="07f78-139">See Also</span></span>  
 <span data-ttu-id="07f78-140">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="07f78-140">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="07f78-141">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="07f78-141">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="07f78-142">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="07f78-142">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
