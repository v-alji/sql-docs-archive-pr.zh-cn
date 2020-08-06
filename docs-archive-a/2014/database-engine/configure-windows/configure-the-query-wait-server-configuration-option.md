---
title: 配置 query wait 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], timing out
- time [SQL Server], query wait time
- query wait option [SQL Server]
ms.assetid: 0fc4aa01-65a3-4a33-9ef4-caca41add238
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 638afff2aa05a9fc4e61bc71e8610dba1dda8cf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588033"
---
# <a name="configure-the-query-wait-server-configuration-option"></a><span data-ttu-id="84f2b-102">配置查询等待值服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="84f2b-102">Configure the query wait Server Configuration Option</span></span>
  <span data-ttu-id="84f2b-103">本主题说明如何使用 **或** 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中配置 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] “查询等待值” [!INCLUDE[tsql](../../includes/tsql-md.md)]服务器配置选项。</span><span class="sxs-lookup"><span data-stu-id="84f2b-103">This topic describes how to configure the **query wait** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="84f2b-104">当没有足够的内存来运行查询时，大量占用内存的查询（如那些涉及排序和哈希操作的查询）将排队等待。</span><span class="sxs-lookup"><span data-stu-id="84f2b-104">Memory-intensive queries (such as those involving sorting and hashing) are queued when there is not enough memory available to run the query.</span></span> <span data-ttu-id="84f2b-105">**“查询等待值”** 选项指定一个查询在超时前等待所需资源的时间（以秒为单位，范围从 0 到 2147483647）。该选项的默认值为 -1。</span><span class="sxs-lookup"><span data-stu-id="84f2b-105">The **query wait** option specifies the time, in seconds (from 0 through 2147483647), that a query waits for resources before it times out. The default value for this option is -1.</span></span> <span data-ttu-id="84f2b-106">这意味着超时值计算为估计的查询开销的 25 倍。</span><span class="sxs-lookup"><span data-stu-id="84f2b-106">This means the time-out is calculated as 25 times the estimated query cost.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="84f2b-107">包含等待查询的事务在查询等待内存时可能会持有锁。</span><span class="sxs-lookup"><span data-stu-id="84f2b-107">A transaction that contains the waiting query might hold locks while the query waits for memory.</span></span> <span data-ttu-id="84f2b-108">在极个别的情况下，可能会发生无法检测到的死锁。</span><span class="sxs-lookup"><span data-stu-id="84f2b-108">In rare situations, it is possible for an undetectable deadlock to occur.</span></span> <span data-ttu-id="84f2b-109">减少查询等待时间可降低这类死锁的概率。</span><span class="sxs-lookup"><span data-stu-id="84f2b-109">Decreasing the query wait time lowers the probability of such deadlocks.</span></span> <span data-ttu-id="84f2b-110">最终，等待的查询将被终止并且事务锁将被释放。</span><span class="sxs-lookup"><span data-stu-id="84f2b-110">Eventually, a waiting query will be terminated and the transaction locks released.</span></span> <span data-ttu-id="84f2b-111">但是，增加最大等待时间将增大该类查询被终止的时间。</span><span class="sxs-lookup"><span data-stu-id="84f2b-111">However, increasing the maximum wait time may increase the amount of time for the query to be terminated.</span></span> <span data-ttu-id="84f2b-112">不建议改变该选项。</span><span class="sxs-lookup"><span data-stu-id="84f2b-112">Changes to this option are not recommended.</span></span>  
  
 <span data-ttu-id="84f2b-113">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="84f2b-113">**In This Topic**</span></span>  
  
-   <span data-ttu-id="84f2b-114">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="84f2b-114">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="84f2b-115">建议</span><span class="sxs-lookup"><span data-stu-id="84f2b-115">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="84f2b-116">安全性</span><span class="sxs-lookup"><span data-stu-id="84f2b-116">Security</span></span>](#Security)  
  
-   <span data-ttu-id="84f2b-117">**若要配置查询等待值选项，请使用：**</span><span class="sxs-lookup"><span data-stu-id="84f2b-117">**To configure the query wait option, using:**</span></span>  
  
     [<span data-ttu-id="84f2b-118">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="84f2b-118">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="84f2b-119">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="84f2b-119">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="84f2b-120">**跟进：** [在配置查询等待值选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="84f2b-120">**Follow Up:**  [After you configure the query wait option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="84f2b-121">开始之前</span><span class="sxs-lookup"><span data-stu-id="84f2b-121">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="84f2b-122">建议</span><span class="sxs-lookup"><span data-stu-id="84f2b-122">Recommendations</span></span>  
  
-   <span data-ttu-id="84f2b-123">此选项是一个高级选项，仅应由有经验的数据库管理员或认证的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技术人员更改。</span><span class="sxs-lookup"><span data-stu-id="84f2b-123">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="84f2b-124">Security</span><span class="sxs-lookup"><span data-stu-id="84f2b-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="84f2b-125">权限</span><span class="sxs-lookup"><span data-stu-id="84f2b-125">Permissions</span></span>  
 <span data-ttu-id="84f2b-126">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="84f2b-126">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="84f2b-127">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="84f2b-127">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="84f2b-128">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="84f2b-128">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="84f2b-129">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="84f2b-129">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-query-wait-option"></a><span data-ttu-id="84f2b-130">配置 query wait 选项</span><span class="sxs-lookup"><span data-stu-id="84f2b-130">To configure the query wait option</span></span>  
  
1.  <span data-ttu-id="84f2b-131">在对象资源管理器中，右键单击服务器并选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="84f2b-131">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="84f2b-132">单击 **“高级”** 节点。</span><span class="sxs-lookup"><span data-stu-id="84f2b-132">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="84f2b-133">在 **“并行”** 中，为“查询等待值”  选项键入所需的值。</span><span class="sxs-lookup"><span data-stu-id="84f2b-133">Under **Parallelism**, type the desired value for the **query wait** option.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="84f2b-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="84f2b-134">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-query-wait-option"></a><span data-ttu-id="84f2b-135">配置 query wait 选项</span><span class="sxs-lookup"><span data-stu-id="84f2b-135">To configure the query wait option</span></span>  
  
1.  <span data-ttu-id="84f2b-136">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="84f2b-136">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="84f2b-137">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="84f2b-137">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="84f2b-138">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="84f2b-138">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="84f2b-139">此示例说明如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将 `query wait` 选项的值设置为 `7500` 秒。</span><span class="sxs-lookup"><span data-stu-id="84f2b-139">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `query wait` option to `7500` seconds.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'query wait', 7500 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="84f2b-140">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="84f2b-140">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-query-wait-option"></a><a name="FollowUp"></a> <span data-ttu-id="84f2b-141">跟进：在配置查询等待值选项之后</span><span class="sxs-lookup"><span data-stu-id="84f2b-141">Follow Up: After you configure the query wait option</span></span>  
 <span data-ttu-id="84f2b-142">该设置将立即生效，无需重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="84f2b-142">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84f2b-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="84f2b-143">See Also</span></span>  
 <span data-ttu-id="84f2b-144">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="84f2b-144">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="84f2b-145">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="84f2b-145">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="84f2b-146">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="84f2b-146">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
