---
title: 配置“查询调控器开销限制”服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], time to execute
- query governor cost limit option [SQL Server]
- time [SQL Server], query run time
ms.assetid: e7b8f084-1052-4133-959b-cebf4add790f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4d4f8420bf8ed8c08d3626c797968c041a40f7c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578432"
---
# <a name="configure-the-query-governor-cost-limit-server-configuration-option"></a><span data-ttu-id="75c96-102">配置查询调控器开销限制服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="75c96-102">Configure the query governor cost limit Server Configuration Option</span></span>
  <span data-ttu-id="75c96-103">本主题说明如何 `query governor cost limit` 使用或在中配置服务器配置选项 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="75c96-103">This topic describes how to configure the `query governor cost limit` server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="75c96-104">查询调控器开销限制选项指定查询可以运行的时间段上限。</span><span class="sxs-lookup"><span data-stu-id="75c96-104">The query governor cost limit option specifies an upper limit on the time period in which a query can run.</span></span> <span data-ttu-id="75c96-105">查询开销是指在特定硬件配置中完成查询所需的估计占用时间（秒）。</span><span class="sxs-lookup"><span data-stu-id="75c96-105">Query cost refers to the estimated elapsed time, in seconds, that is required to complete a query on a specific hardware configuration.</span></span> <span data-ttu-id="75c96-106">此选项的默认值为 0，将设置为关闭查询调控器。</span><span class="sxs-lookup"><span data-stu-id="75c96-106">The default value for this option is 0, which sets the query governor to off.</span></span> <span data-ttu-id="75c96-107">这将允许所有查询在没有任何时间限制下运行。</span><span class="sxs-lookup"><span data-stu-id="75c96-107">This allows all queries to run without any time limitation.</span></span> <span data-ttu-id="75c96-108">如果为该选项指定一个非零、非负的数值，则查询调控器将不允许执行估计开销超过该值的查询。</span><span class="sxs-lookup"><span data-stu-id="75c96-108">If you specify a nonzero, nonnegative value, the query governor disallows execution of any query that has an estimated cost that exceeds that value.</span></span>  
  
 <span data-ttu-id="75c96-109">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="75c96-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="75c96-110">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="75c96-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="75c96-111">建议</span><span class="sxs-lookup"><span data-stu-id="75c96-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="75c96-112">安全性</span><span class="sxs-lookup"><span data-stu-id="75c96-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="75c96-113">**若要设置查询调控器开销限制选项，请使用：**</span><span class="sxs-lookup"><span data-stu-id="75c96-113">**To configure the query governor cost limit option, using:**</span></span>  
  
     [<span data-ttu-id="75c96-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="75c96-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="75c96-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="75c96-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="75c96-116">**跟进：** [在配置查询调控器开销限制选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="75c96-116">**Follow Up:**  [After you configure the query governor cost limit option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="75c96-117">开始之前</span><span class="sxs-lookup"><span data-stu-id="75c96-117">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="75c96-118">建议</span><span class="sxs-lookup"><span data-stu-id="75c96-118">Recommendations</span></span>  
  
-   <span data-ttu-id="75c96-119">此选项是一个高级选项，仅应由有经验的数据库管理员或认证的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技术人员更改。</span><span class="sxs-lookup"><span data-stu-id="75c96-119">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="75c96-120">若要在每个连接基础上更改查询调控器开销限制值，请使用 [SET QUERY_GOVERNOR_COST_LIMIT](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql) 语句。</span><span class="sxs-lookup"><span data-stu-id="75c96-120">To change the value query governor cost limit on a per-connection basis, use the [SET QUERY_GOVERNOR_COST_LIMIT](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql) statement.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="75c96-121">Security</span><span class="sxs-lookup"><span data-stu-id="75c96-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="75c96-122">权限</span><span class="sxs-lookup"><span data-stu-id="75c96-122">Permissions</span></span>  
 <span data-ttu-id="75c96-123">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="75c96-123">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="75c96-124">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="75c96-124">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="75c96-125">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="75c96-125">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="75c96-126">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="75c96-126">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-query-governor-cost-limit-option"></a><span data-ttu-id="75c96-127">配置查询调控器开销限制选项</span><span class="sxs-lookup"><span data-stu-id="75c96-127">To configure the query governor cost limit option</span></span>  
  
1.  <span data-ttu-id="75c96-128">在对象资源管理器中，右键单击服务器并选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="75c96-128">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="75c96-129">单击 **“连接”** 页面。</span><span class="sxs-lookup"><span data-stu-id="75c96-129">Click the **Connections** page.</span></span>  
  
3.  <span data-ttu-id="75c96-130">选中或清除“使用查询调控器防止查询长时间运行”复选框。</span><span class="sxs-lookup"><span data-stu-id="75c96-130">Select or clear the **Use query governor to prevent long-running queries** check box.</span></span>  
  
     <span data-ttu-id="75c96-131">如果选中此复选框，请在下面的框中输入一个正值，查询调控器将禁止执行运行长度超过该值的所有查询。</span><span class="sxs-lookup"><span data-stu-id="75c96-131">If you select this check box, in the box below, enter a positive value, which the query governor uses to disallow execution of any query with a running length exceeding that value.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="75c96-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="75c96-132">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-query-governor-cost-limit-option"></a><span data-ttu-id="75c96-133">配置查询调控器开销限制选项</span><span class="sxs-lookup"><span data-stu-id="75c96-133">To configure the query governor cost limit option</span></span>  
  
1.  <span data-ttu-id="75c96-134">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="75c96-134">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="75c96-135">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="75c96-135">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="75c96-136">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="75c96-136">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="75c96-137">此示例说明如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将 `query governor cost limit` 选项的值设置为 `120` 秒。</span><span class="sxs-lookup"><span data-stu-id="75c96-137">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `query governor cost limit` option to `120` seconds.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'query governor cost limit', 120 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="75c96-138">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="75c96-138">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-query-governor-cost-limit-option"></a><a name="FollowUp"></a> <span data-ttu-id="75c96-139">跟进：在配置查询调控器开销限制选项之后</span><span class="sxs-lookup"><span data-stu-id="75c96-139">Follow Up: After you configure the query governor cost limit option</span></span>  
 <span data-ttu-id="75c96-140">该设置将立即生效，无需重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="75c96-140">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75c96-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="75c96-141">See Also</span></span>  
 <span data-ttu-id="75c96-142">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="75c96-142">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="75c96-143">[SET QUERY_GOVERNOR_COST_LIMIT (Transact-SQL)](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="75c96-143">[SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql) </span></span>  
 <span data-ttu-id="75c96-144">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="75c96-144">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="75c96-145">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="75c96-145">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
