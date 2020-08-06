---
title: SQL Server 2014 中的废止数据库引擎功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: release-landing
ms.topic: conceptual
helpviewer_keywords:
- VIA protocol
- unsupported features [SQL Server]
- SQL Mail
- discontinued functionality [SQL Server]
- RESTORE WITH DBO_ONLY
- BACKUP WITH PASSWORD
- user instances enabled
- BACKUP WITH MEDIAPASSWORD
- AWE
- SQL-DMO
- '*= and =*'
- 80 compatibility levels
- COMPUTE BY
- user instance timeout
- sp_dropalias
- COMPUTE
- WITH APPEND
- sys.database_principal_aliases
- sp_dboption
- DATABASEPROPERTY
- FASTFIRSTROW hint
- SET DISABLE_DEF_CNST_CHK
ms.assetid: d686cdf0-d11d-4dba-9ec8-de1a5f189f25
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e7fbc371526c4623cf289019b506aa01eb683ad0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690059"
---
# <a name="discontinued-database-engine-functionality-in-sql-server-2014"></a><span data-ttu-id="bfe9b-102">SQL Server 2014 中废止的数据库引擎功能</span><span class="sxs-lookup"><span data-stu-id="bfe9b-102">Discontinued Database Engine Functionality in SQL Server 2014</span></span>
  <span data-ttu-id="bfe9b-103">本主题介绍 [!INCLUDE[ssDE](../includes/ssde-md.md)] 中不再可用的 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-103">This topic describes the [!INCLUDE[ssDE](../includes/ssde-md.md)] features that are no longer available in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
## <a name="discontinued-features-in-sssql14"></a><a name="SQL14"></a><span data-ttu-id="bfe9b-104">中废止的功能[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfe9b-104">Discontinued Features in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]</span></span>  
 <span data-ttu-id="bfe9b-105">下表列出了 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]中移除的功能。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-105">The following table lists features that were removed in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span>  
  
|<span data-ttu-id="bfe9b-106">类别</span><span class="sxs-lookup"><span data-stu-id="bfe9b-106">Category</span></span>|<span data-ttu-id="bfe9b-107">已不再使用的功能</span><span class="sxs-lookup"><span data-stu-id="bfe9b-107">Discontinued feature</span></span>|<span data-ttu-id="bfe9b-108">Replacement</span><span class="sxs-lookup"><span data-stu-id="bfe9b-108">Replacement</span></span>|  
|--------------|--------------------------|-----------------|  
|<span data-ttu-id="bfe9b-109">兼容性级别</span><span class="sxs-lookup"><span data-stu-id="bfe9b-109">Compatibility level</span></span>|<span data-ttu-id="bfe9b-110">90 兼容性级别</span><span class="sxs-lookup"><span data-stu-id="bfe9b-110">90 compatibility level</span></span>|<span data-ttu-id="bfe9b-111">必须将数据库的兼容性级别至少设置为 100。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-111">Databases must be set to at least compatibility level 100.</span></span> <span data-ttu-id="bfe9b-112">当兼容性级别低于 100 的数据库升级到 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]时，在升级操作过程中数据库的兼容性级别将设置为 100。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-112">When a database with a compatibility level of less than 100 is upgraded to [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], the compatibility level of the database is set to 100 during the upgrade operation.</span></span>|  
  
## <a name="discontinued-features-in-sssql11"></a><a name="Denali"></a><span data-ttu-id="bfe9b-113">中废止的功能[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfe9b-113">Discontinued Features in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]</span></span>  
 <span data-ttu-id="bfe9b-114">下表列出了 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]中移除的功能。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-114">The following table lists features that were removed in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span>  
  
|<span data-ttu-id="bfe9b-115">类别</span><span class="sxs-lookup"><span data-stu-id="bfe9b-115">Category</span></span>|<span data-ttu-id="bfe9b-116">已不再使用的功能</span><span class="sxs-lookup"><span data-stu-id="bfe9b-116">Discontinued feature</span></span>|<span data-ttu-id="bfe9b-117">Replacement</span><span class="sxs-lookup"><span data-stu-id="bfe9b-117">Replacement</span></span>|  
|--------------|--------------------------|-----------------|  
|<span data-ttu-id="bfe9b-118">备份和还原</span><span class="sxs-lookup"><span data-stu-id="bfe9b-118">Backup and Restore</span></span>|<span data-ttu-id="bfe9b-119">已停止使用 PASSWORD 和**backup {database &#124; log}** 的**backup {database &#124; log}** MEDIAPASSWORD。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-119">**BACKUP { DATABASE &#124; LOG } WITH PASSWORD** and **BACKUP { DATABASE &#124; LOG } WITH MEDIAPASSWORD** are discontinued.</span></span> <span data-ttu-id="bfe9b-120">**RESTORE {DATABASE &#124; LOG} WITH [MEDIA] PASSWORD**仍不推荐使用。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-120">**RESTORE { DATABASE &#124; LOG } WITH [MEDIA]PASSWORD**continues to be deprecated.</span></span>|<span data-ttu-id="bfe9b-121">无</span><span class="sxs-lookup"><span data-stu-id="bfe9b-121">None</span></span>|  
|<span data-ttu-id="bfe9b-122">备份和还原</span><span class="sxs-lookup"><span data-stu-id="bfe9b-122">Backup and Restore</span></span>|<span data-ttu-id="bfe9b-123">**还原 {数据库 &#124; 日志} .。。与 DBO_ONLY**</span><span class="sxs-lookup"><span data-stu-id="bfe9b-123">**RESTORE { DATABASE &#124; LOG } ... WITH DBO_ONLY**</span></span>|<span data-ttu-id="bfe9b-124">**还原 {DATABASE &#124; LOG} ... .。。与 RESTRICTED_USER**</span><span class="sxs-lookup"><span data-stu-id="bfe9b-124">**RESTORE { DATABASE &#124; LOG } ... ... WITH RESTRICTED_USER**</span></span>|  
|<span data-ttu-id="bfe9b-125">兼容性级别</span><span class="sxs-lookup"><span data-stu-id="bfe9b-125">Compatibility level</span></span>|<span data-ttu-id="bfe9b-126">80 兼容级别</span><span class="sxs-lookup"><span data-stu-id="bfe9b-126">80 compatibility level</span></span>|<span data-ttu-id="bfe9b-127">必须将数据库的兼容级别至少设置为 90。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-127">Databases must be set to at least compatibility level 90.</span></span>|  
|<span data-ttu-id="bfe9b-128">配置选项</span><span class="sxs-lookup"><span data-stu-id="bfe9b-128">Configuration Options</span></span>|<span data-ttu-id="bfe9b-129">`sp_configure 'user instance timeout'` 和 `'user instances enabled'`</span><span class="sxs-lookup"><span data-stu-id="bfe9b-129">`sp_configure 'user instance timeout'` and `'user instances enabled'`</span></span>|<span data-ttu-id="bfe9b-130">使用本地数据库功能。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-130">Use the Local Database feature.</span></span> <span data-ttu-id="bfe9b-131">有关详细信息，请参阅[SqlLocalDB 实用工具](../tools/sqllocaldb-utility.md)</span><span class="sxs-lookup"><span data-stu-id="bfe9b-131">For more information, see [SqlLocalDB Utility](../tools/sqllocaldb-utility.md)</span></span>|  
|<span data-ttu-id="bfe9b-132">连接协议</span><span class="sxs-lookup"><span data-stu-id="bfe9b-132">Connection protocols</span></span>|<span data-ttu-id="bfe9b-133">不再支持 VIA 协议。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-133">Support for the VIA protocol is discontinued.</span></span>|<span data-ttu-id="bfe9b-134">请改用 TCP。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-134">Use TCP instead.</span></span>|  
|<span data-ttu-id="bfe9b-135">数据库对象</span><span class="sxs-lookup"><span data-stu-id="bfe9b-135">Database objects</span></span>|<span data-ttu-id="bfe9b-136">有关触发器的 `WITH APPEND` 子句</span><span class="sxs-lookup"><span data-stu-id="bfe9b-136">`WITH APPEND` clause on triggers</span></span>|<span data-ttu-id="bfe9b-137">重新创建整个触发器。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-137">Re-create the whole trigger.</span></span>|  
|<span data-ttu-id="bfe9b-138">数据库选项</span><span class="sxs-lookup"><span data-stu-id="bfe9b-138">Database options</span></span>|`sp_dboption`|`ALTER DATABASE`|  
|<span data-ttu-id="bfe9b-139">Mail</span><span class="sxs-lookup"><span data-stu-id="bfe9b-139">Mail</span></span>|<span data-ttu-id="bfe9b-140">SQL Mail</span><span class="sxs-lookup"><span data-stu-id="bfe9b-140">SQL Mail</span></span>|<span data-ttu-id="bfe9b-141">使用数据库邮件。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-141">Use Database Mail.</span></span> <span data-ttu-id="bfe9b-142">有关详细信息，请参阅 [Database Mail](../relational-databases/database-mail/database-mail.md) 和  [Use Database Mail Instead of SQL Mail](../relational-databases/policy-based-management/use-database-mail-instead-of-sql-mail.md)。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-142">For more information, see [Database Mail](../relational-databases/database-mail/database-mail.md) and  [Use Database Mail Instead of SQL Mail](../relational-databases/policy-based-management/use-database-mail-instead-of-sql-mail.md).</span></span>|  
|<span data-ttu-id="bfe9b-143">内存管理</span><span class="sxs-lookup"><span data-stu-id="bfe9b-143">Memory Management</span></span>|<span data-ttu-id="bfe9b-144">32 位地址窗口化扩展插件 (AWE) 和 32 位热添加内存支持。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-144">32-bit Address Windowing Extensions (AWE) and 32-bit Hot Add memory support.</span></span>|<span data-ttu-id="bfe9b-145">使用 64 位操作系统。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-145">Use a 64-bit operating system.</span></span>|  
|<span data-ttu-id="bfe9b-146">元数据</span><span class="sxs-lookup"><span data-stu-id="bfe9b-146">Metadata</span></span>|`DATABASEPROPERTY`|`DATABASEPROPERTYEX`|  
|<span data-ttu-id="bfe9b-147">可编程性</span><span class="sxs-lookup"><span data-stu-id="bfe9b-147">Programmability</span></span>|<span data-ttu-id="bfe9b-148">SQL Server 分布式管理对象 (SQL-DMO)</span><span class="sxs-lookup"><span data-stu-id="bfe9b-148">SQL Server Distributed Management Objects (SQL-DMO)</span></span>|<span data-ttu-id="bfe9b-149">SQL Server 管理对象 (SMO)</span><span class="sxs-lookup"><span data-stu-id="bfe9b-149">SQL Server Management Objects (SMO)</span></span>|  
|<span data-ttu-id="bfe9b-150">查询提示</span><span class="sxs-lookup"><span data-stu-id="bfe9b-150">Query hints</span></span>|<span data-ttu-id="bfe9b-151">`FASTFIRSTROW` 提示</span><span class="sxs-lookup"><span data-stu-id="bfe9b-151">`FASTFIRSTROW` hint</span></span>|<span data-ttu-id="bfe9b-152">`OPTION (FAST`*n* `)` 。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-152">`OPTION (FAST` *n* `)`.</span></span>|  
|<span data-ttu-id="bfe9b-153">远程服务器</span><span class="sxs-lookup"><span data-stu-id="bfe9b-153">Remote servers</span></span>|<span data-ttu-id="bfe9b-154">用户通过 `sp_addserver` 创建新的远程服务器的功能已停止使用。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-154">The ability for users to create new remote servers by using `sp_addserver` is discontinued.</span></span> <span data-ttu-id="bfe9b-155">带有“local”选项的 `sp_addserver` 保持可用。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-155">`sp_addserver` with the 'local' option remains available.</span></span> <span data-ttu-id="bfe9b-156">可以使用在升级过程中保留或由复制创建的远程服务器。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-156">Remote servers preserved during upgrade or created by replication can be used.</span></span>|<span data-ttu-id="bfe9b-157">用链接服务器替代远程服务器。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-157">Replace remote servers by using linked servers.</span></span>|  
|<span data-ttu-id="bfe9b-158">安全性</span><span class="sxs-lookup"><span data-stu-id="bfe9b-158">Security</span></span>|`sp_dropalias`|<span data-ttu-id="bfe9b-159">请将别名替换为用户帐户和数据库角色的组合。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-159">Replace aliases with a combination of user accounts and database roles.</span></span> <span data-ttu-id="bfe9b-160">请使用 `sp_dropalias` 删除已升级数据库中的别名。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-160">Use `sp_dropalias` to remove aliases in upgraded databases.</span></span>|  
|<span data-ttu-id="bfe9b-161">安全性</span><span class="sxs-lookup"><span data-stu-id="bfe9b-161">Security</span></span>|<span data-ttu-id="bfe9b-162">表示来自早于 **2000 的登录值的** PWDCOMPARE [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的版本参数不再使用。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-162">The version parameter of **PWDCOMPARE** representing a value from a login earlier than [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2000 is discontinued.</span></span>|<span data-ttu-id="bfe9b-163">无</span><span class="sxs-lookup"><span data-stu-id="bfe9b-163">None</span></span>|  
|<span data-ttu-id="bfe9b-164">SMO 中的 Service Broker 可编程性</span><span class="sxs-lookup"><span data-stu-id="bfe9b-164">Service Broker programmability in SMO</span></span>|<span data-ttu-id="bfe9b-165">**Microsoft.SqlServer.Management.Smo.Broker.BrokerPriority** 类不再实现 **Microsoft.SqlServer.Management.Smo.IObjectPermission** 接口。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-165">The **Microsoft.SqlServer.Management.Smo.Broker.BrokerPriority** class no longer implements the **Microsoft.SqlServer.Management.Smo.IObjectPermission** interface.</span></span>||  
|<span data-ttu-id="bfe9b-166">SET 选项</span><span class="sxs-lookup"><span data-stu-id="bfe9b-166">SET options</span></span>|`SET DISABLE_DEF_CNST_CHK`|<span data-ttu-id="bfe9b-167">无。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-167">None.</span></span>|  
|<span data-ttu-id="bfe9b-168">系统表</span><span class="sxs-lookup"><span data-stu-id="bfe9b-168">System tables</span></span>|<span data-ttu-id="bfe9b-169">sys.database_principal_aliases</span><span class="sxs-lookup"><span data-stu-id="bfe9b-169">sys.database_principal_aliases</span></span>|<span data-ttu-id="bfe9b-170">请使用角色而不是别名。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-170">Use roles instead of aliases.</span></span>|  
|<span data-ttu-id="bfe9b-171">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bfe9b-171">Transact-SQL</span></span>|<span data-ttu-id="bfe9b-172">格式为 `RAISERROR` 的 `RAISERROR integer 'string'` 不再使用。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-172">`RAISERROR` in the format `RAISERROR integer 'string'` is discontinued.</span></span>|<span data-ttu-id="bfe9b-173">使用当前的\*\*RAISERROR ( ... ) \*\*语法重写语句。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-173">Rewrite the statement using the current **RAISERROR(...)** syntax.</span></span>|  
|<span data-ttu-id="bfe9b-174">Transact-SQL 语法</span><span class="sxs-lookup"><span data-stu-id="bfe9b-174">Transact-SQL syntax</span></span>|`COMPUTE / COMPUTE BY`|<span data-ttu-id="bfe9b-175">使用 `ROLLUP`</span><span class="sxs-lookup"><span data-stu-id="bfe9b-175">Use `ROLLUP`</span></span>|  
|<span data-ttu-id="bfe9b-176">Transact-SQL 语法</span><span class="sxs-lookup"><span data-stu-id="bfe9b-176">Transact-SQL syntax</span></span>|<span data-ttu-id="bfe9b-177">使用 **\*=** and **=&#42;**</span><span class="sxs-lookup"><span data-stu-id="bfe9b-177">Use of **\*=** and **=&#42;**</span></span>|<span data-ttu-id="bfe9b-178">使用 ANSI 联接语法。</span><span class="sxs-lookup"><span data-stu-id="bfe9b-178">Use ANSI join syntax.</span></span> <span data-ttu-id="bfe9b-179">有关详细信息，请参阅 [FROM (Transact-SQL).](https://msdn.microsoft.com/library/ms177634\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="bfe9b-179">For more information, see [FROM (Transact-SQL).](https://msdn.microsoft.com/library/ms177634\(SQL.105\).aspx)</span></span>|  
|<span data-ttu-id="bfe9b-180">XEvents</span><span class="sxs-lookup"><span data-stu-id="bfe9b-180">XEvents</span></span>|<span data-ttu-id="bfe9b-181">databases_data_file_size_changed、databases_log_file_size_changed</span><span class="sxs-lookup"><span data-stu-id="bfe9b-181">databases_data_file_size_changed, databases_log_file_size_changed</span></span><br /><br /> <span data-ttu-id="bfe9b-182">eventdatabases_log_file_used_size_changed</span><span class="sxs-lookup"><span data-stu-id="bfe9b-182">eventdatabases_log_file_used_size_changed</span></span><br /><br /> <span data-ttu-id="bfe9b-183">locks_lock_timeouts_greater_than_0</span><span class="sxs-lookup"><span data-stu-id="bfe9b-183">locks_lock_timeouts_greater_than_0</span></span><br /><br /> <span data-ttu-id="bfe9b-184">locks_lock_timeouts</span><span class="sxs-lookup"><span data-stu-id="bfe9b-184">locks_lock_timeouts</span></span>|<span data-ttu-id="bfe9b-185">替换为 database_file_size_change event、database_file_size_change</span><span class="sxs-lookup"><span data-stu-id="bfe9b-185">Replaced by database_file_size_change event, database_file_size_change</span></span><br /><br /> <span data-ttu-id="bfe9b-186">database_file_size_change event</span><span class="sxs-lookup"><span data-stu-id="bfe9b-186">database_file_size_change event</span></span><br /><br /> <span data-ttu-id="bfe9b-187">lock_timeout_greater_than_0</span><span class="sxs-lookup"><span data-stu-id="bfe9b-187">lock_timeout_greater_than_0</span></span><br /><br /> <span data-ttu-id="bfe9b-188">lock_timeout</span><span class="sxs-lookup"><span data-stu-id="bfe9b-188">lock_timeout</span></span>|  
  
 <span data-ttu-id="bfe9b-189">**其他 XEvent 更改**</span><span class="sxs-lookup"><span data-stu-id="bfe9b-189">**Additional XEvent changes**</span></span>  
  
 <span data-ttu-id="bfe9b-190">**resource_monitor_ring_buffer_record**：</span><span class="sxs-lookup"><span data-stu-id="bfe9b-190">**resource_monitor_ring_buffer_record**:</span></span>  
  
-   <span data-ttu-id="bfe9b-191">删除的字段：single_pages_kb、multiple_pages_kb</span><span class="sxs-lookup"><span data-stu-id="bfe9b-191">Fields removed: single_pages_kb, multiple_pages_kb</span></span>  
  
-   <span data-ttu-id="bfe9b-192">添加的字段：target_kb、pages_kb</span><span class="sxs-lookup"><span data-stu-id="bfe9b-192">Fields added: target_kb, pages_kb</span></span>  
  
 <span data-ttu-id="bfe9b-193">**memory_node_oom_ring_buffer_recorded**：</span><span class="sxs-lookup"><span data-stu-id="bfe9b-193">**memory_node_oom_ring_buffer_recorded**:</span></span>  
  
-   <span data-ttu-id="bfe9b-194">删除的字段：single_pages_kb、multiple_pages_kb</span><span class="sxs-lookup"><span data-stu-id="bfe9b-194">Fields removed: single_pages_kb, multiple_pages_kb</span></span>  
  
-   <span data-ttu-id="bfe9b-195">添加的字段：target_kb、pages_kb</span><span class="sxs-lookup"><span data-stu-id="bfe9b-195">Fields added: target_kb, pages_kb</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfe9b-196">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bfe9b-196">See Also</span></span>  
 [<span data-ttu-id="bfe9b-197">SQL Server 2014 中不推荐使用的数据库引擎功能</span><span class="sxs-lookup"><span data-stu-id="bfe9b-197">Deprecated Database Engine Features in SQL Server 2014</span></span>](deprecated-database-engine-features-in-sql-server-2016.md?view=sql-server-2014)  
  
  
