---
title: 配置“默认语言”服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default language option
ms.assetid: c08c26d8-5a62-487e-a4ee-4c529e4f9287
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b0e62fef112dad2c6c307946bc720adf1f14d82b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693464"
---
# <a name="configure-the-default-language-server-configuration-option"></a><span data-ttu-id="ab973-102">配置默认语言服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="ab973-102">Configure the default language Server Configuration Option</span></span>
  <span data-ttu-id="ab973-103">本主题说明了如何使用 **或** 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中配置 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] “默认语言” [!INCLUDE[tsql](../../includes/tsql-md.md)]服务器配置选项。</span><span class="sxs-lookup"><span data-stu-id="ab973-103">This topic describes how to configure the **default language** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="ab973-104">**“默认语言”** 选项指定所有新创建的登录名的默认语言。</span><span class="sxs-lookup"><span data-stu-id="ab973-104">The **default language** option specifies the default language for all newly created logins.</span></span> <span data-ttu-id="ab973-105">若要设置默认语言，请指定所需语言的 **langid** 值。</span><span class="sxs-lookup"><span data-stu-id="ab973-105">To set default language, specify the **langid** value of the language you want.</span></span> <span data-ttu-id="ab973-106">可通过查询 **sys.syslanguages** 兼容性视图来获取 **langid** 值。</span><span class="sxs-lookup"><span data-stu-id="ab973-106">The **langid** value can be obtained by querying the **sys.syslanguages** compatibility view.</span></span>  
  
 <span data-ttu-id="ab973-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="ab973-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ab973-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="ab973-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ab973-109">建议</span><span class="sxs-lookup"><span data-stu-id="ab973-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="ab973-110">安全性</span><span class="sxs-lookup"><span data-stu-id="ab973-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ab973-111">**要配置默认语言选项，请使用：**</span><span class="sxs-lookup"><span data-stu-id="ab973-111">**To configure the default language option, using:**</span></span>  
  
     [<span data-ttu-id="ab973-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ab973-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ab973-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ab973-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="ab973-114">**跟进：** [在配置默认语言选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="ab973-114">**Follow Up:**  [After you configure the default language option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ab973-115">开始之前</span><span class="sxs-lookup"><span data-stu-id="ab973-115">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="ab973-116">建议</span><span class="sxs-lookup"><span data-stu-id="ab973-116">Recommendations</span></span>  
  
-   <span data-ttu-id="ab973-117">可以使用 CREATE LOGIN 或 ALTER LOGIN 替代登录的默认语言。</span><span class="sxs-lookup"><span data-stu-id="ab973-117">The default language for a login can be overridden by using CREATE LOGIN or ALTER LOGIN.</span></span> <span data-ttu-id="ab973-118">会话的默认语言是该会话登录的语言，除非使用开放式数据库连接 (ODBC) 或 OLE DB API 替代每个会话的默认语言。</span><span class="sxs-lookup"><span data-stu-id="ab973-118">The default language for a session is the language for that session's login, unless overridden on a per-session basis by using the Open Database Connectivity (ODBC) or OLE DB APIs.</span></span> <span data-ttu-id="ab973-119">请注意，只能将“默认语言”选项设置为 [sys.syslanguages](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql) 中定义的语言 ID (0-32)。</span><span class="sxs-lookup"><span data-stu-id="ab973-119">Note that you can only set the **default language** option to a language ID defined in [sys.syslanguages](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql) (0-32).</span></span> <span data-ttu-id="ab973-120">在使用包含数据库时，可使用 CREATE DATABASE 或 ALTER DATABASE 设置数据库的默认语言，使用 CREATE USER 或 ALTER USER 设置包含数据库用户的默认语言。</span><span class="sxs-lookup"><span data-stu-id="ab973-120">When you are using contained databases, a default language can be set for a database by using CREATE DATABASE or ALTER DATABASE, and for contained database users by using CREATE USER or ALTER USER.</span></span> <span data-ttu-id="ab973-121">在包含数据库中设置默认语言时，接受 **sys.syslanguages** 中所列的 **langid**值、语言名称或语言别名。</span><span class="sxs-lookup"><span data-stu-id="ab973-121">Setting default languages in a contained database accepts **langid** value, the language name, or a language alias as listed in **sys.syslanguages**.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ab973-122">Security</span><span class="sxs-lookup"><span data-stu-id="ab973-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ab973-123">权限</span><span class="sxs-lookup"><span data-stu-id="ab973-123">Permissions</span></span>  
 <span data-ttu-id="ab973-124">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="ab973-124">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="ab973-125">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="ab973-125">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="ab973-126">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="ab973-126">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ab973-127">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ab973-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-default-language-option"></a><span data-ttu-id="ab973-128">配置默认语言选项</span><span class="sxs-lookup"><span data-stu-id="ab973-128">To configure the default language option</span></span>  
  
1.  <span data-ttu-id="ab973-129">在对象资源管理器中，右键单击服务器并选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="ab973-129">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="ab973-130">单击 **“杂项服务器设置”** 节点。</span><span class="sxs-lookup"><span data-stu-id="ab973-130">Click the **Misc server settings** node.</span></span>  
  
3.  <span data-ttu-id="ab973-131">在 **“用户的默认语言”** 框中，选择 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 显示系统消息所用的语言。</span><span class="sxs-lookup"><span data-stu-id="ab973-131">In the **Default language for users** box, choose the language in which [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should display system messages.</span></span>  
  
     <span data-ttu-id="ab973-132">默认语言为英语。</span><span class="sxs-lookup"><span data-stu-id="ab973-132">The default language is English.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ab973-133">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ab973-133">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-default-language-option"></a><span data-ttu-id="ab973-134">配置默认语言选项</span><span class="sxs-lookup"><span data-stu-id="ab973-134">To configure the default language option</span></span>  
  
1.  <span data-ttu-id="ab973-135">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ab973-135">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ab973-136">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="ab973-136">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ab973-137">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="ab973-137">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="ab973-138">此示例说明如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将 `default language` 选项配置为 French (`2`)。</span><span class="sxs-lookup"><span data-stu-id="ab973-138">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the `default language` option to French (`2`).</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'default language', 2 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
 <span data-ttu-id="ab973-139">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="ab973-139">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-default-language-option"></a><a name="FollowUp"></a> <span data-ttu-id="ab973-140">跟进：在配置默认语言选项之后</span><span class="sxs-lookup"><span data-stu-id="ab973-140">Follow Up: After you configure the default language option</span></span>  
 <span data-ttu-id="ab973-141">该设置将立即生效，无需重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="ab973-141">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab973-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab973-142">See Also</span></span>  
 <span data-ttu-id="ab973-143">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab973-143">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span></span>  
 <span data-ttu-id="ab973-144">[ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab973-144">[ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) </span></span>  
 <span data-ttu-id="ab973-145">[CREATE USER (Transact-SQL)](/sql/t-sql/statements/create-user-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab973-145">[CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql) </span></span>  
 <span data-ttu-id="ab973-146">[ALTER USER (Transact-SQL)](/sql/t-sql/statements/alter-user-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab973-146">[ALTER USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-user-transact-sql) </span></span>  
 <span data-ttu-id="ab973-147">[CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab973-147">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 <span data-ttu-id="ab973-148">[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab973-148">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="ab973-149">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab973-149">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="ab973-150">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ab973-150">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="ab973-151">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ab973-151">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
