---
title: 配置 user options 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- global default for all users [SQL Server]
- users [SQL Server], global defaults
- user options option [SQL Server]
ms.assetid: cfed8f86-6bcf-4b90-88eb-9656e22d5dc5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d7ee40d0f6de532b93ce9d8075b609c80f09df7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693087"
---
# <a name="configure-the-user-options-server-configuration-option"></a><span data-ttu-id="775c6-102">配置 user options 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="775c6-102">Configure the user options Server Configuration Option</span></span>
  <span data-ttu-id="775c6-103">本主题说明如何使用 **或** 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中配置 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] user options [!INCLUDE[tsql](../../includes/tsql-md.md)]服务器配置选项。</span><span class="sxs-lookup"><span data-stu-id="775c6-103">This topic describes how to configure the **user options** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="775c6-104">**user options** 选项指定了适用于所有用户的全局默认值。</span><span class="sxs-lookup"><span data-stu-id="775c6-104">The **user options** option specifies global defaults for all users.</span></span> <span data-ttu-id="775c6-105">将建立一个用户工作会话期间使用的默认查询处理选项的列表。</span><span class="sxs-lookup"><span data-stu-id="775c6-105">A list of default query processing options is established for the duration of a user's work session.</span></span> <span data-ttu-id="775c6-106">**user options** 选项允许您更改 SET 选项的默认值（如果服务器的默认设置不合适）。</span><span class="sxs-lookup"><span data-stu-id="775c6-106">The **user options** option allows you to change the default values of the SET options (if the server's default settings are not appropriate).</span></span>  
  
 <span data-ttu-id="775c6-107">用户可以使用 SET 语句覆盖这些默认值。</span><span class="sxs-lookup"><span data-stu-id="775c6-107">A user can override these defaults by using the SET statement.</span></span> <span data-ttu-id="775c6-108">可以为新登录名动态配置 **user options** 。</span><span class="sxs-lookup"><span data-stu-id="775c6-108">You can configure **user options** dynamically for new logins.</span></span> <span data-ttu-id="775c6-109">更改 **user options**的设置后，新的登录名会话将使用新的设置，当前登录名会话受不影响。</span><span class="sxs-lookup"><span data-stu-id="775c6-109">After you change the setting of **user options**, new login sessions use the new setting; current login sessions are not affected.</span></span>  
  
 <span data-ttu-id="775c6-110">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="775c6-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="775c6-111">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="775c6-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="775c6-112">建议</span><span class="sxs-lookup"><span data-stu-id="775c6-112">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="775c6-113">安全性</span><span class="sxs-lookup"><span data-stu-id="775c6-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="775c6-114">**若要配置 user options 配置选项，可使用：**</span><span class="sxs-lookup"><span data-stu-id="775c6-114">**To configure the user options configuration option, using:**</span></span>  
  
     [<span data-ttu-id="775c6-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="775c6-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="775c6-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="775c6-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="775c6-117">**跟进：** [在配置用户选项配置选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="775c6-117">**Follow Up:**  [After you configure the user options configuration option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="775c6-118">开始之前</span><span class="sxs-lookup"><span data-stu-id="775c6-118">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="775c6-119">建议</span><span class="sxs-lookup"><span data-stu-id="775c6-119">Recommendations</span></span>  
  
-   <span data-ttu-id="775c6-120">下表列出并说明了 **user options**的配置值。</span><span class="sxs-lookup"><span data-stu-id="775c6-120">The following table lists and describes the configuration values for **user options**.</span></span> <span data-ttu-id="775c6-121">并非所有配置值都是相互兼容的。</span><span class="sxs-lookup"><span data-stu-id="775c6-121">Not all configuration values are compatible with each other.</span></span> <span data-ttu-id="775c6-122">例如，不能同时设置 ANSI_NULL_DFLT_ON 和 ANSI_NULL_DFLT_OFF。</span><span class="sxs-lookup"><span data-stu-id="775c6-122">For example, ANSI_NULL_DFLT_ON and ANSI_NULL_DFLT_OFF cannot be set at the same time.</span></span>  
  
    |<span data-ttu-id="775c6-123">值</span><span class="sxs-lookup"><span data-stu-id="775c6-123">Value</span></span>|<span data-ttu-id="775c6-124">配置</span><span class="sxs-lookup"><span data-stu-id="775c6-124">Configuration</span></span>|<span data-ttu-id="775c6-125">说明</span><span class="sxs-lookup"><span data-stu-id="775c6-125">Description</span></span>|  
    |-----------|-------------------|-----------------|  
    |<span data-ttu-id="775c6-126">1</span><span class="sxs-lookup"><span data-stu-id="775c6-126">1</span></span>|<span data-ttu-id="775c6-127">DISABLE_DEF_CNST_CHK</span><span class="sxs-lookup"><span data-stu-id="775c6-127">DISABLE_DEF_CNST_CHK</span></span>|<span data-ttu-id="775c6-128">控制执行期间或延迟的约束检查。</span><span class="sxs-lookup"><span data-stu-id="775c6-128">Controls interim or deferred constraint checking.</span></span>|  
    |<span data-ttu-id="775c6-129">2</span><span class="sxs-lookup"><span data-stu-id="775c6-129">2</span></span>|<span data-ttu-id="775c6-130">IMPLICIT_TRANSACTIONS</span><span class="sxs-lookup"><span data-stu-id="775c6-130">IMPLICIT_TRANSACTIONS</span></span>|<span data-ttu-id="775c6-131">对于 DBLIB 网络库连接，控制执行语句时是否隐式启动事务。</span><span class="sxs-lookup"><span data-stu-id="775c6-131">For dblib network library connections, controls whether a transaction is started implicitly when a statement is executed.</span></span> <span data-ttu-id="775c6-132">IMPLICIT_TRANSACTIONS 设置对 ODBC 或 OLEDB 连接没有影响。</span><span class="sxs-lookup"><span data-stu-id="775c6-132">The IMPLICIT_TRANSACTIONS setting has no effect on ODBC or OLEDB connections.</span></span>|  
    |<span data-ttu-id="775c6-133">4</span><span class="sxs-lookup"><span data-stu-id="775c6-133">4</span></span>|<span data-ttu-id="775c6-134">CURSOR_CLOSE_ON_COMMIT</span><span class="sxs-lookup"><span data-stu-id="775c6-134">CURSOR_CLOSE_ON_COMMIT</span></span>|<span data-ttu-id="775c6-135">控制执行提交操作后游标的行为。</span><span class="sxs-lookup"><span data-stu-id="775c6-135">Controls behavior of cursors after a commit operation has been performed.</span></span>|  
    |<span data-ttu-id="775c6-136">8</span><span class="sxs-lookup"><span data-stu-id="775c6-136">8</span></span>|<span data-ttu-id="775c6-137">ANSI_WARNINGS</span><span class="sxs-lookup"><span data-stu-id="775c6-137">ANSI_WARNINGS</span></span>|<span data-ttu-id="775c6-138">控制聚合警告中的截断和 NULL。</span><span class="sxs-lookup"><span data-stu-id="775c6-138">Controls truncation and NULL in aggregate warnings.</span></span>|  
    |<span data-ttu-id="775c6-139">16</span><span class="sxs-lookup"><span data-stu-id="775c6-139">16</span></span>|<span data-ttu-id="775c6-140">ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="775c6-140">ANSI_PADDING</span></span>|<span data-ttu-id="775c6-141">控制固定长度变量的填充。</span><span class="sxs-lookup"><span data-stu-id="775c6-141">Controls padding of fixed-length variables.</span></span>|  
    |<span data-ttu-id="775c6-142">32</span><span class="sxs-lookup"><span data-stu-id="775c6-142">32</span></span>|<span data-ttu-id="775c6-143">ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="775c6-143">ANSI_NULLS</span></span>|<span data-ttu-id="775c6-144">使用相等运算符时控制 NULL 处理。</span><span class="sxs-lookup"><span data-stu-id="775c6-144">Controls NULL handling when using equality operators.</span></span>|  
    |<span data-ttu-id="775c6-145">64</span><span class="sxs-lookup"><span data-stu-id="775c6-145">64</span></span>|<span data-ttu-id="775c6-146">ARITHABORT</span><span class="sxs-lookup"><span data-stu-id="775c6-146">ARITHABORT</span></span>|<span data-ttu-id="775c6-147">在查询执行过程中发生溢出或被零除错误时终止查询。</span><span class="sxs-lookup"><span data-stu-id="775c6-147">Terminates a query when an overflow or divide-by-zero error occurs during query execution.</span></span>|  
    |<span data-ttu-id="775c6-148">128</span><span class="sxs-lookup"><span data-stu-id="775c6-148">128</span></span>|<span data-ttu-id="775c6-149">ARITHIGNORE</span><span class="sxs-lookup"><span data-stu-id="775c6-149">ARITHIGNORE</span></span>|<span data-ttu-id="775c6-150">在查询过程中出现溢出或被零除错误时返回 NULL。</span><span class="sxs-lookup"><span data-stu-id="775c6-150">Returns NULL when an overflow or divide-by-zero error occurs during a query.</span></span>|  
    |<span data-ttu-id="775c6-151">256</span><span class="sxs-lookup"><span data-stu-id="775c6-151">256</span></span>|<span data-ttu-id="775c6-152">QUOTED_IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="775c6-152">QUOTED_IDENTIFIER</span></span>|<span data-ttu-id="775c6-153">对表达式进行求值时区别单引号和双引号。</span><span class="sxs-lookup"><span data-stu-id="775c6-153">Differentiates between single and double quotation marks when evaluating an expression.</span></span>|  
    |<span data-ttu-id="775c6-154">512</span><span class="sxs-lookup"><span data-stu-id="775c6-154">512</span></span>|<span data-ttu-id="775c6-155">NOCOUNT</span><span class="sxs-lookup"><span data-stu-id="775c6-155">NOCOUNT</span></span>|<span data-ttu-id="775c6-156">关闭执行每个语句后返回的报告受影响的行数的消息。</span><span class="sxs-lookup"><span data-stu-id="775c6-156">Turns off the message returned at the end of each statement that states how many rows were affected.</span></span>|  
    |<span data-ttu-id="775c6-157">1024</span><span class="sxs-lookup"><span data-stu-id="775c6-157">1024</span></span>|<span data-ttu-id="775c6-158">ANSI_NULL_DFLT_ON</span><span class="sxs-lookup"><span data-stu-id="775c6-158">ANSI_NULL_DFLT_ON</span></span>|<span data-ttu-id="775c6-159">将会话的行为更改为使用 ANSI 兼容的空性。</span><span class="sxs-lookup"><span data-stu-id="775c6-159">Alters the session's behavior to use ANSI compatibility for nullability.</span></span> <span data-ttu-id="775c6-160">未显式定义为空性的新列允许使用空值。</span><span class="sxs-lookup"><span data-stu-id="775c6-160">New columns defined without explicit nullability are defined to allow nulls.</span></span>|  
    |<span data-ttu-id="775c6-161">2048</span><span class="sxs-lookup"><span data-stu-id="775c6-161">2048</span></span>|<span data-ttu-id="775c6-162">ANSI_NULL_DFLT_OFF</span><span class="sxs-lookup"><span data-stu-id="775c6-162">ANSI_NULL_DFLT_OFF</span></span>|<span data-ttu-id="775c6-163">将会话的行为更改为不使用 ANSI 兼容的空性。</span><span class="sxs-lookup"><span data-stu-id="775c6-163">Alters the session's behavior not to use ANSI compatibility for nullability.</span></span> <span data-ttu-id="775c6-164">未显式定义为空性的新列不允许使用空值。</span><span class="sxs-lookup"><span data-stu-id="775c6-164">New columns defined without explicit nullability do not allow nulls.</span></span>|  
    |<span data-ttu-id="775c6-165">4096</span><span class="sxs-lookup"><span data-stu-id="775c6-165">4096</span></span>|<span data-ttu-id="775c6-166">CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="775c6-166">CONCAT_NULL_YIELDS_NULL</span></span>|<span data-ttu-id="775c6-167">将 NULL 值与字符串串联时返回 NULL。</span><span class="sxs-lookup"><span data-stu-id="775c6-167">Returns NULL when concatenating a NULL value with a string.</span></span>|  
    |<span data-ttu-id="775c6-168">8192</span><span class="sxs-lookup"><span data-stu-id="775c6-168">8192</span></span>|<span data-ttu-id="775c6-169">NUMERIC_ROUNDABORT</span><span class="sxs-lookup"><span data-stu-id="775c6-169">NUMERIC_ROUNDABORT</span></span>|<span data-ttu-id="775c6-170">表达式中出现精度降低时生成错误。</span><span class="sxs-lookup"><span data-stu-id="775c6-170">Generates an error when a loss of precision occurs in an expression.</span></span>|  
    |<span data-ttu-id="775c6-171">16384</span><span class="sxs-lookup"><span data-stu-id="775c6-171">16384</span></span>|<span data-ttu-id="775c6-172">XACT_ABORT</span><span class="sxs-lookup"><span data-stu-id="775c6-172">XACT_ABORT</span></span>|<span data-ttu-id="775c6-173">如果 Transact-SQL 语句引发运行时错误，则回滚事务。</span><span class="sxs-lookup"><span data-stu-id="775c6-173">Rolls back a transaction if a Transact-SQL statement raises a run-time error.</span></span>|  
  
-   <span data-ttu-id="775c6-174">**user options** 中位的位置与 @@OPTIONS 中位的位置相同。</span><span class="sxs-lookup"><span data-stu-id="775c6-174">The bit positions in **user options** are identical to those in @@OPTIONS.</span></span> <span data-ttu-id="775c6-175">每个连接都有自己的 @@OPTIONS 函数，该函数表示配置环境。</span><span class="sxs-lookup"><span data-stu-id="775c6-175">Each connection has its own @@OPTIONS function, which represents the configuration environment.</span></span> <span data-ttu-id="775c6-176">登录到 \ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例时，用户会收到将当前 **user options** 值指定为 @@OPTIONS 的默认环境。</span><span class="sxs-lookup"><span data-stu-id="775c6-176">When logging in to an instance of \ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a user receives a default environment that assigns the current **user options** value to @@OPTIONS.</span></span> <span data-ttu-id="775c6-177">对 **user options** 执行 SET 语句会影响会话的 @@OPTIONS 函数的相应值。</span><span class="sxs-lookup"><span data-stu-id="775c6-177">Executing SET statements for **user options** affects the corresponding value in the session's @@OPTIONS function.</span></span> <span data-ttu-id="775c6-178">在此设置更改后创建的所有连接都将收到新值。</span><span class="sxs-lookup"><span data-stu-id="775c6-178">All connections created after this setting is changed receive the new value.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="775c6-179">Security</span><span class="sxs-lookup"><span data-stu-id="775c6-179">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="775c6-180">权限</span><span class="sxs-lookup"><span data-stu-id="775c6-180">Permissions</span></span>  
 <span data-ttu-id="775c6-181">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="775c6-181">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="775c6-182">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="775c6-182">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="775c6-183">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="775c6-183">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="775c6-184">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="775c6-184">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-user-options-configuration-option"></a><span data-ttu-id="775c6-185">配置 user options 配置选项</span><span class="sxs-lookup"><span data-stu-id="775c6-185">To configure the user options configuration option</span></span>  
  
1.  <span data-ttu-id="775c6-186">在对象资源管理器中，右键单击服务器并选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="775c6-186">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="775c6-187">单击 **“连接”** 节点。</span><span class="sxs-lookup"><span data-stu-id="775c6-187">Click the **Connections** node.</span></span>  
  
3.  <span data-ttu-id="775c6-188">在 **“默认连接选项”** 框中，选择一个或多个属性以便为所有已连接的用户配置默认查询处理选项。</span><span class="sxs-lookup"><span data-stu-id="775c6-188">In the **Default connection options** box, select one or more attributes to configure the default query-processing options for all connected users.</span></span>  
  
     <span data-ttu-id="775c6-189">默认情况下，不配置用户选项。</span><span class="sxs-lookup"><span data-stu-id="775c6-189">By default, no user options are configured.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="775c6-190">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="775c6-190">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-user-options-configuration-option"></a><span data-ttu-id="775c6-191">配置 user options 配置选项</span><span class="sxs-lookup"><span data-stu-id="775c6-191">To configure the user options configuration option</span></span>  
  
1.  <span data-ttu-id="775c6-192">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="775c6-192">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="775c6-193">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="775c6-193">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="775c6-194">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="775c6-194">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="775c6-195">此示例说明如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 配置 `user options` 以更改 ANSI_WARNINGS 服务器选项的设置。</span><span class="sxs-lookup"><span data-stu-id="775c6-195">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the `user options` to change the setting for the ANSI_WARNINGS server option.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'user options', 8 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
##  <a name="follow-up-after-you-configure-the-user-options-configuration-option"></a><a name="FollowUp"></a> <span data-ttu-id="775c6-196">跟进：在配置用户选项配置选项之后</span><span class="sxs-lookup"><span data-stu-id="775c6-196">Follow Up: After you configure the user options configuration option</span></span>  
 <span data-ttu-id="775c6-197">该设置将立即生效，无需重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="775c6-197">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="775c6-198">另请参阅</span><span class="sxs-lookup"><span data-stu-id="775c6-198">See Also</span></span>  
 <span data-ttu-id="775c6-199">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="775c6-199">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="775c6-200">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="775c6-200">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="775c6-201">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="775c6-201">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="775c6-202">SET 语句 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="775c6-202">SET Statements &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-statements-transact-sql)  
  
  
