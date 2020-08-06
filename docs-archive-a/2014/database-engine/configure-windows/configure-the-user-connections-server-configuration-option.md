---
title: 配置 user connections 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 12/02/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- simultaneous connections [SQL Server]
- user connections option [SQL Server]
- users [SQL Server], simultaneous connections
- maximum number of simultaneous user connections
- connections [SQL Server], simultaneous
ms.assetid: 53beee6e-59fe-4276-9abb-8f1cec2a3508
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 68fbb4a17de131c128b5b1bb7cfb35a33b9d0037
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577833"
---
# <a name="configure-the-user-connections-server-configuration-option"></a><span data-ttu-id="d7992-102">配置 user connections 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="d7992-102">Configure the user connections Server Configuration Option</span></span>
  <span data-ttu-id="d7992-103">本主题说明如何使用 **或** 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中设置 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] user connections [!INCLUDE[tsql](../../includes/tsql-md.md)]服务器配置选项。</span><span class="sxs-lookup"><span data-stu-id="d7992-103">This topic describes how to set the **user connections** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="d7992-104">**user connections** 选项指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例上允许同时建立的最大用户连接数。</span><span class="sxs-lookup"><span data-stu-id="d7992-104">The **user connections** option specifies the maximum number of simultaneous user connections that are allowed on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d7992-105">实际允许的用户连接数还取决于正使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本以及应用程序和硬件的限制。</span><span class="sxs-lookup"><span data-stu-id="d7992-105">The actual number of user connections allowed also depends on the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you are using, and also the limits of your application or applications and hardware.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d7992-106">允许的最大用户连接数为 32767。</span><span class="sxs-lookup"><span data-stu-id="d7992-106">allows a maximum of 32,767 user connections.</span></span> <span data-ttu-id="d7992-107">由于 **user connections** 是动态（自动配置）选项， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将根据需要自动调整最大用户连接数，最大不超过允许的最大值。</span><span class="sxs-lookup"><span data-stu-id="d7992-107">Because **user connections** is a dynamic (self-configuring) option, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] adjusts the maximum number of user connections automatically as needed, up to the maximum value allowable.</span></span> <span data-ttu-id="d7992-108">例如，如果仅有 10 个用户登录，则要分配 10 个用户连接对象。</span><span class="sxs-lookup"><span data-stu-id="d7992-108">For example, if only 10 users are logged in, 10 user connection objects are allocated.</span></span> <span data-ttu-id="d7992-109">在大多数情况下，没有必要更改此选项的值。</span><span class="sxs-lookup"><span data-stu-id="d7992-109">In most cases, you do not have to change the value for this option.</span></span> <span data-ttu-id="d7992-110">默认值为 0，表示允许的最多用户连接数为 (32,767) 。</span><span class="sxs-lookup"><span data-stu-id="d7992-110">The default is 0, which means that the maximum (32,767) user connections are allowed.</span></span>  
  
 <span data-ttu-id="d7992-111">若要确定系统允许的最大用户连接数，可以执行 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 或查询 [sys.configuration](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) 目录视图。</span><span class="sxs-lookup"><span data-stu-id="d7992-111">To determine the maximum number of user connections that your system allows, you can execute [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) or query the [sys.configuration](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="d7992-112">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="d7992-112">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d7992-113">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="d7992-113">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d7992-114">建议</span><span class="sxs-lookup"><span data-stu-id="d7992-114">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="d7992-115">安全性</span><span class="sxs-lookup"><span data-stu-id="d7992-115">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d7992-116">**配置 user connections 选项，使用：**</span><span class="sxs-lookup"><span data-stu-id="d7992-116">**To configure the user connections option, using:**</span></span>  
  
     [<span data-ttu-id="d7992-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d7992-117">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d7992-118">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d7992-118">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="d7992-119">**跟进：** [在配置用户连接选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="d7992-119">**Follow Up:**  [After you configure the user connections option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d7992-120">开始之前</span><span class="sxs-lookup"><span data-stu-id="d7992-120">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="d7992-121">建议</span><span class="sxs-lookup"><span data-stu-id="d7992-121">Recommendations</span></span>  
  
-   <span data-ttu-id="d7992-122">此选项是一个高级选项，仅应由有经验的数据库管理员或认证的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技术人员更改。</span><span class="sxs-lookup"><span data-stu-id="d7992-122">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="d7992-123">使用 **user connections** 选项有助于避免由于过多并发连接而使服务器超载。</span><span class="sxs-lookup"><span data-stu-id="d7992-123">Using the **user connections** option helps avoid overloading the server with too many concurrent connections.</span></span> <span data-ttu-id="d7992-124">可以根据系统和用户要求估计连接数。</span><span class="sxs-lookup"><span data-stu-id="d7992-124">You can estimate the number of connections based on system and user requirements.</span></span> <span data-ttu-id="d7992-125">例如，在很多用户的系统上，每个用户通常不要求唯一的连接。</span><span class="sxs-lookup"><span data-stu-id="d7992-125">For example, on a system with many users, each user would not usually require a unique connection.</span></span> <span data-ttu-id="d7992-126">可以在用户间共享连接。</span><span class="sxs-lookup"><span data-stu-id="d7992-126">Connections can be shared among users.</span></span> <span data-ttu-id="d7992-127">对于运行 OLE DB 应用程序的用户，每个打开的连接对象需要一个连接；对于运行开放式数据库连接 (ODBC) 应用程序的用户，每个活动连接句柄需要一个连接；对于运行 DB-Library 应用程序的用户，每个调用 DB-Library **dbopen** 函数启动的进程需要一个连接。</span><span class="sxs-lookup"><span data-stu-id="d7992-127">Users running OLE DB applications need a connection for each open connection object, users running Open Database Connectivity (ODBC) applications need a connection for each active connection handle in the application, and users running DB-Library applications need one connection for each process started that calls the DB-Library **dbopen** function.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d7992-128">如果必须使用此选项，请不要将值设置得太高，这是因为不管是否使用连接，每个连接都会产生开销。</span><span class="sxs-lookup"><span data-stu-id="d7992-128">If you must use this option, do not set the value too high, because each connection has overhead regardless of whether the connection is being used.</span></span> <span data-ttu-id="d7992-129">如果超过了用户连接的最大允许值，将收到一条错误消息，而且直到出现一个可用连接之后才能建立连接。</span><span class="sxs-lookup"><span data-stu-id="d7992-129">If you exceed the maximum number of user connections, you receive an error message and are not able to connect until another connection becomes available.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d7992-130">Security</span><span class="sxs-lookup"><span data-stu-id="d7992-130">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d7992-131">权限</span><span class="sxs-lookup"><span data-stu-id="d7992-131">Permissions</span></span>  
 <span data-ttu-id="d7992-132">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="d7992-132">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="d7992-133">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="d7992-133">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="d7992-134">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="d7992-134">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d7992-135">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d7992-135">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-user-connections-option"></a><span data-ttu-id="d7992-136">配置 user connections 选项</span><span class="sxs-lookup"><span data-stu-id="d7992-136">To configure the user connections option</span></span>  
  
1.  <span data-ttu-id="d7992-137">在对象资源浏览器中，右键单击某个服务器，然后单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="d7992-137">In Object Explorer, right-click a server and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="d7992-138">单击 **“连接”** 节点。</span><span class="sxs-lookup"><span data-stu-id="d7992-138">Click the **Connections** node.</span></span>  
  
3.  <span data-ttu-id="d7992-139">在 **“连接”** 下面的 **“最大并发连接数”** 框中，键入或选择一个介于 0 到 32767 之间的值，以设置允许与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例同时连接的最大用户数量。</span><span class="sxs-lookup"><span data-stu-id="d7992-139">Under **Connections**, in the **Max number of concurrent connections** box, type or select a value from 0 through 32767 to set the maximum number of users that are allowed to connect simultaneously to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
4.  <span data-ttu-id="d7992-140">重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d7992-140">Restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d7992-141">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d7992-141">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-user-connections-option"></a><span data-ttu-id="d7992-142">配置 user connections 选项</span><span class="sxs-lookup"><span data-stu-id="d7992-142">To configure the user connections option</span></span>  
  
1.  <span data-ttu-id="d7992-143">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d7992-143">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d7992-144">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="d7992-144">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d7992-145">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="d7992-145">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="d7992-146">此示例显示如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将 `user connections` 选项的值配置为 `325` 个用户。</span><span class="sxs-lookup"><span data-stu-id="d7992-146">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the value of the `user connections` option to `325` users.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'user connections', 325 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="d7992-147">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="d7992-147">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-user-connections-option"></a><a name="FollowUp"></a> <span data-ttu-id="d7992-148">跟进：在配置用户连接选项之后</span><span class="sxs-lookup"><span data-stu-id="d7992-148">Follow Up: After you configure the user connections option</span></span>  
 <span data-ttu-id="d7992-149">必须重新启动服务器，设置才会生效。</span><span class="sxs-lookup"><span data-stu-id="d7992-149">The server must be restarted before the setting can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7992-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d7992-150">See Also</span></span>  
 <span data-ttu-id="d7992-151">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d7992-151">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="d7992-152">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d7992-152">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="d7992-153">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d7992-153">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
