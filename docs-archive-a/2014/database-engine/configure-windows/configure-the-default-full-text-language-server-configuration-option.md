---
title: 配置“默认全文语言”服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- languages [full-text search]
- default full-text language option
ms.assetid: 0fa8785b-0830-4a52-aff5-fcf8268b72fc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ec0736326a4da0708d125bfc480996d54bb86c8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577839"
---
# <a name="configure-the-default-full-text-language-server-configuration-option"></a><span data-ttu-id="ba831-102">配置 default full-text language 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="ba831-102">Configure the default full-text language Server Configuration Option</span></span>
  <span data-ttu-id="ba831-103">本主题说明如何 `default full-text language` 使用或在中配置服务器配置选项 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ba831-103">This topic describes how to configure the `default full-text language` server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="ba831-104">`default full-text language`选项指定全文索引的默认语言值。</span><span class="sxs-lookup"><span data-stu-id="ba831-104">The `default full-text language` option specifies a default language value for full-text indexes.</span></span> <span data-ttu-id="ba831-105">语言分析将对全文索引的所有数据执行，并且取决于数据的语言。</span><span class="sxs-lookup"><span data-stu-id="ba831-105">Linguistic analysis is performed on all data that is full-text indexed and is dependent on the language of the data.</span></span> <span data-ttu-id="ba831-106">该选项的默认值为服务器的语言。</span><span class="sxs-lookup"><span data-stu-id="ba831-106">The default value of this option is the language of the server.</span></span> <span data-ttu-id="ba831-107">对于的本地化版本 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序会将 `default full-text language` 选项设置为服务器的语言（如果存在合适的匹配项）。</span><span class="sxs-lookup"><span data-stu-id="ba831-107">For a localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup sets the `default full-text language` option to the language of the server if an appropriate match exists.</span></span> <span data-ttu-id="ba831-108">对于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的非本地化版本，`default full-text language` 选项为“英语”。</span><span class="sxs-lookup"><span data-stu-id="ba831-108">For a non-localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the `default full-text language` option is English.</span></span>  
  
 <span data-ttu-id="ba831-109">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="ba831-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ba831-110">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="ba831-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ba831-111">限制和局限</span><span class="sxs-lookup"><span data-stu-id="ba831-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ba831-112">建议</span><span class="sxs-lookup"><span data-stu-id="ba831-112">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="ba831-113">安全性</span><span class="sxs-lookup"><span data-stu-id="ba831-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ba831-114">**配置 default full-text language 选项，使用：**</span><span class="sxs-lookup"><span data-stu-id="ba831-114">**To configure the default full-text language option, using:**</span></span>  
  
     [<span data-ttu-id="ba831-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ba831-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ba831-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ba831-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="ba831-117">**跟进：** [在配置默认全文语言选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="ba831-117">**Follow Up:**  [After you configure the default full-text language option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ba831-118">开始之前</span><span class="sxs-lookup"><span data-stu-id="ba831-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ba831-119">限制和局限</span><span class="sxs-lookup"><span data-stu-id="ba831-119">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="ba831-120">`default full-text language`如果未通过 "创建全文索引" 或 "更改全文索引" 语句中的 "语言" **language_term**选项为列指定语言，则将在全文索引中使用此选项的值。</span><span class="sxs-lookup"><span data-stu-id="ba831-120">The value of the `default full-text language` option is used in a full-text index when no language is specified for a column through the LANGUAGE **language_term** option in the CREATE FULLTEXT INDEX or ALTER FULLTEXT INDEX statements.</span></span> <span data-ttu-id="ba831-121">如果不支持默认全文语言，或者语言分析包不可用，则 CREATE 或 ALTER 操作将失败，并且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将返回说明指定语言无效的错误消息。</span><span class="sxs-lookup"><span data-stu-id="ba831-121">If the default full-text language is not supported or the linguistic analysis package is not available, the CREATE or ALTER operation will fail and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will return an error message stating that the language specified is not valid.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="ba831-122">建议</span><span class="sxs-lookup"><span data-stu-id="ba831-122">Recommendations</span></span>  
  
-   <span data-ttu-id="ba831-123">此选项是一个高级选项，仅应由有经验的数据库管理员或认证的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技术人员更改。</span><span class="sxs-lookup"><span data-stu-id="ba831-123">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="ba831-124">`default full-text language`选项要求 LCID 值。</span><span class="sxs-lookup"><span data-stu-id="ba831-124">The `default full-text language` option requires an LCID value.</span></span> <span data-ttu-id="ba831-125">有关支持的 LCID 及其相关语言的列表，请参阅 [sys.fulltext_languages (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ba831-125">For a list of supported LCIDs and their related languages, see [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql).</span></span> <span data-ttu-id="ba831-126">例如，独立的软件供应商还可提供其他语言。</span><span class="sxs-lookup"><span data-stu-id="ba831-126">Other languages may also be available from independent software vendors, for example.</span></span> <span data-ttu-id="ba831-127">如果找不到特定区域语言，则全文引擎将自动切换到主要语言。</span><span class="sxs-lookup"><span data-stu-id="ba831-127">If no specific language dialect is found, the Full-Text Engine will automatically switch to the primary language.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ba831-128">Security</span><span class="sxs-lookup"><span data-stu-id="ba831-128">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ba831-129">权限</span><span class="sxs-lookup"><span data-stu-id="ba831-129">Permissions</span></span>  
 <span data-ttu-id="ba831-130">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="ba831-130">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="ba831-131">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="ba831-131">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="ba831-132">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="ba831-132">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ba831-133">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ba831-133">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-default-full-text-language-option"></a><span data-ttu-id="ba831-134">配置 default full-text language 选项</span><span class="sxs-lookup"><span data-stu-id="ba831-134">To configure the default full-text language option</span></span>  
  
1.  <span data-ttu-id="ba831-135">在对象资源管理器中，右键单击服务器并选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="ba831-135">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="ba831-136">单击 **“高级”** 节点。</span><span class="sxs-lookup"><span data-stu-id="ba831-136">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="ba831-137">在“杂项”下，使用 **“默认全文语言”** 指定全文索引列的默认语言值。</span><span class="sxs-lookup"><span data-stu-id="ba831-137">Under Miscellaneous, use **Default Full Text Language** to specify a default language value for full-text indexed columns.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ba831-138">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ba831-138">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-default-full-text-language-option"></a><span data-ttu-id="ba831-139">配置 default full-text language 选项</span><span class="sxs-lookup"><span data-stu-id="ba831-139">To configure the default full-text language option</span></span>  
  
1.  <span data-ttu-id="ba831-140">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ba831-140">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ba831-141">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="ba831-141">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ba831-142">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="ba831-142">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="ba831-143">此示例说明如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将 `default full-text` 选项的值设置为荷兰语 (`1043`)。</span><span class="sxs-lookup"><span data-stu-id="ba831-143">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `default full-text` option to Dutch (`1043`).</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'default full-text language', 1043 ;  
GO  
RECONFIGURE  
GO  
  
```  
  
 <span data-ttu-id="ba831-144">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="ba831-144">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-default-full-text-language-option"></a><a name="FollowUp"></a> <span data-ttu-id="ba831-145">跟进：在配置默认全文语言选项之后</span><span class="sxs-lookup"><span data-stu-id="ba831-145">Follow Up: After you configure the default full-text language option</span></span>  
 <span data-ttu-id="ba831-146">该设置将立即生效，无需重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="ba831-146">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba831-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ba831-147">See Also</span></span>  
 <span data-ttu-id="ba831-148">[sys.fulltext_languages (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ba831-148">[sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) </span></span>  
 <span data-ttu-id="ba831-149">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ba831-149">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="ba831-150">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ba831-150">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="ba831-151">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ba831-151">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="ba831-152">[CREATE FULLTEXT INDEX (Transact-SQL)](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ba831-152">[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span></span>  
 [<span data-ttu-id="ba831-153">ALTER FULLTEXT INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ba831-153">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-index-transact-sql)  
  
  
