---
title: 配置 remote query timeout 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- time limit for remote queries [SQL Server]
- remote query timeout option
ms.assetid: 888c8448-933b-41e3-8aa1-c206bc0cdb78
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 74f82d621d7f0375a6a3ca604abba00f83fc6024
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693089"
---
# <a name="configure-the-remote-query-timeout-server-configuration-option"></a><span data-ttu-id="4514a-102">配置 remote query timeout 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="4514a-102">Configure the remote query timeout Server Configuration Option</span></span>
  <span data-ttu-id="4514a-103">本主题说明如何使用 **或** 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中配置 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] remote query timeout [!INCLUDE[tsql](../../includes/tsql-md.md)]服务器配置选项。</span><span class="sxs-lookup"><span data-stu-id="4514a-103">This topic describes how to configure the **remote query timeout** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="4514a-104">**remote query timeout** 选项指定在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 超时之前远程操作可以持续的时间（秒）。此选项的默认值是 600，即允许等待 10 分钟。</span><span class="sxs-lookup"><span data-stu-id="4514a-104">The **remote query timeout** option specifies how long, in seconds, a remote operation can take before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] times out. The default value for this option is 600, which allows a 10-minute wait.</span></span> <span data-ttu-id="4514a-105">此值将应用到由作为远程查询的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 发起的发送连接。</span><span class="sxs-lookup"><span data-stu-id="4514a-105">This value applies to an outgoing connection initiated by the [!INCLUDE[ssDE](../../includes/ssde-md.md)] as a remote query.</span></span> <span data-ttu-id="4514a-106">此值不会对 [!INCLUDE[ssDE](../../includes/ssde-md.md)]接收的查询产生任何影响。</span><span class="sxs-lookup"><span data-stu-id="4514a-106">This value has no effect on queries received by the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="4514a-107">若要禁用该超时，请将此值设置为 0。</span><span class="sxs-lookup"><span data-stu-id="4514a-107">To disable the time-out, set the value to 0.</span></span> <span data-ttu-id="4514a-108">查询将一直等待，直到完成。</span><span class="sxs-lookup"><span data-stu-id="4514a-108">A query will wait until it completes.</span></span>  
  
 <span data-ttu-id="4514a-109">对于异类查询， **remote query timeout** 指定远程访问接口在查询超时前应等待结果集的秒数（由命令对象使用 DBPROP_COMMANDTIMEOUT 行集属性进行初始化）。如果远程提供程序支持该值，则该值还用于设置 DBPROP_GENERALTIMEOUT。</span><span class="sxs-lookup"><span data-stu-id="4514a-109">For heterogeneous queries, **remote query timeout** specifies the number of seconds (initialized in the command object using the DBPROP_COMMANDTIMEOUT rowset property) that a remote provider should wait for result sets before the query times out. This value is also used to set DBPROP_GENERALTIMEOUT if supported by the remote provider.</span></span> <span data-ttu-id="4514a-110">这将导致任何其他操作在指定的秒数后超时。</span><span class="sxs-lookup"><span data-stu-id="4514a-110">This will cause any other operations to time out after the specified number of seconds.</span></span>  
  
 <span data-ttu-id="4514a-111">对于远程存储过程， **remote query timeout** 指定在发送一个远程 `EXEC` 语句之后，在远程存储过程超时前必须等待的秒数。</span><span class="sxs-lookup"><span data-stu-id="4514a-111">For remote stored procedures, **remote query timeout** specifies the number of seconds that must elapse after sending a remote `EXEC` statement before the remote stored procedure times out.</span></span>  
  
 <span data-ttu-id="4514a-112">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="4514a-112">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4514a-113">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="4514a-113">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4514a-114">先决条件</span><span class="sxs-lookup"><span data-stu-id="4514a-114">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="4514a-115">安全性</span><span class="sxs-lookup"><span data-stu-id="4514a-115">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4514a-116">**配置 remote query timeout 选项，使用：**</span><span class="sxs-lookup"><span data-stu-id="4514a-116">**To configure the remote query timeout option, using:**</span></span>  
  
     [<span data-ttu-id="4514a-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4514a-117">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4514a-118">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4514a-118">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="4514a-119">**跟进：** [在配置 remote query timeout 选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="4514a-119">**Follow Up:**  [After you configure the remote query timeout option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4514a-120">开始之前</span><span class="sxs-lookup"><span data-stu-id="4514a-120">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="4514a-121">先决条件</span><span class="sxs-lookup"><span data-stu-id="4514a-121">Prerequisites</span></span>  
  
-   <span data-ttu-id="4514a-122">在设定此值前，必须允许远程服务器连接。</span><span class="sxs-lookup"><span data-stu-id="4514a-122">Remote server connections must be allowed before this value can be set.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4514a-123">Security</span><span class="sxs-lookup"><span data-stu-id="4514a-123">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4514a-124">权限</span><span class="sxs-lookup"><span data-stu-id="4514a-124">Permissions</span></span>  
 <span data-ttu-id="4514a-125">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="4514a-125">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="4514a-126">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="4514a-126">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="4514a-127">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="4514a-127">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4514a-128">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4514a-128">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-remote-query-timeout-option"></a><span data-ttu-id="4514a-129">配置 remote query timeout 选项</span><span class="sxs-lookup"><span data-stu-id="4514a-129">To configure the remote query timeout option</span></span>  
  
1.  <span data-ttu-id="4514a-130">在对象资源管理器中，右键单击服务器并选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="4514a-130">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="4514a-131">单击 **“连接”** 节点。</span><span class="sxs-lookup"><span data-stu-id="4514a-131">Click the **Connections** node.</span></span>  
  
3.  <span data-ttu-id="4514a-132">在 **“远程服务器连接”** 下的 **“远程查询超时值”** 框中，键入或选择介于 0 到 2,147,483,647 之间的值以设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在超时之前等待的最多秒数。</span><span class="sxs-lookup"><span data-stu-id="4514a-132">Under **Remote server connections**, in the **Remote query timeout** box, type or select a value from 0 through 2,147,483,647 to set the maximum number seconds for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to wait before timing out.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4514a-133">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4514a-133">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-remote-query-timeout-option"></a><span data-ttu-id="4514a-134">配置 remote query timeout 选项</span><span class="sxs-lookup"><span data-stu-id="4514a-134">To configure the remote query timeout option</span></span>  
  
1.  <span data-ttu-id="4514a-135">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4514a-135">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4514a-136">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="4514a-136">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4514a-137">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="4514a-137">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="4514a-138">此示例说明如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将 `remote query timeout` 选项的值设置为 `0` 以禁用超时。</span><span class="sxs-lookup"><span data-stu-id="4514a-138">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `remote query timeout` option to `0` to disable the time-out.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'remote query timeout', 0 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 <span data-ttu-id="4514a-139">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="4514a-139">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-remote-query-timeout-option"></a><a name="FollowUp"></a> <span data-ttu-id="4514a-140">跟进：在配置 remote query timeout 选项之后</span><span class="sxs-lookup"><span data-stu-id="4514a-140">Follow Up: After you configure the remote query timeout option</span></span>  
 <span data-ttu-id="4514a-141">该设置将立即生效，无需重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="4514a-141">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4514a-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4514a-142">See Also</span></span>  
 <span data-ttu-id="4514a-143">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4514a-143">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="4514a-144">[行集属性和行为](../../relational-databases/native-client-ole-db-rowsets/rowset-properties-and-behaviors.md) </span><span class="sxs-lookup"><span data-stu-id="4514a-144">[Rowset Properties and Behaviors](../../relational-databases/native-client-ole-db-rowsets/rowset-properties-and-behaviors.md) </span></span>  
 <span data-ttu-id="4514a-145">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4514a-145">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="4514a-146">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4514a-146">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
