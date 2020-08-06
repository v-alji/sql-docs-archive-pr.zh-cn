---
title: 配置“最大文本 REPL 大小”服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- max text repl size option
ms.assetid: 3056cf64-621d-4996-9162-3913f6bc6d5b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2af0cf426583ee328f0a484de1c3539836c0d8af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588041"
---
# <a name="configure-the-max-text-repl-size-server-configuration-option"></a><span data-ttu-id="58007-102">配置 max text repl size 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="58007-102">Configure the max text repl size Server Configuration Option</span></span>
  <span data-ttu-id="58007-103">本主题说明如何使用 **或** 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中配置 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] max text repl size [!INCLUDE[tsql](../../includes/tsql-md.md)]服务器配置选项。</span><span class="sxs-lookup"><span data-stu-id="58007-103">This topic describes how to configure the **max text repl size** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="58007-104">"**最大文本复制大小**" 选项指定 `text` `ntext` `varchar(max)` `nvarchar(max)` `varbinary(max)` `xml` `image` 可通过单个 INSERT、UPDATE、WRITETEXT 或 UPDATETEXT 语句添加到复制列或捕获列的、、、、、和数据的最大 (字节) 。</span><span class="sxs-lookup"><span data-stu-id="58007-104">The **max text repl size** option specifies the maximum size (in bytes) of `text`, `ntext`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, `xml`, and `image` data that can be added to a replicated column or captured column in a single INSERT, UPDATE, WRITETEXT, or UPDATETEXT statement.</span></span> <span data-ttu-id="58007-105">默认值为 65536 个字节。</span><span class="sxs-lookup"><span data-stu-id="58007-105">The default value is 65536 bytes.</span></span> <span data-ttu-id="58007-106">值为 -1 表示除了数据类型指定的限制之外，没有大小限制。</span><span class="sxs-lookup"><span data-stu-id="58007-106">A value of -1 indicates that there is no size limit, other than the limit imposed by the data type.</span></span>  
  
 <span data-ttu-id="58007-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="58007-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="58007-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="58007-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="58007-109">限制和局限</span><span class="sxs-lookup"><span data-stu-id="58007-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="58007-110">安全性</span><span class="sxs-lookup"><span data-stu-id="58007-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="58007-111">**配置 max text repl size 选项，使用：**</span><span class="sxs-lookup"><span data-stu-id="58007-111">**To configure the max text repl size option, using:**</span></span>  
  
     [<span data-ttu-id="58007-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="58007-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="58007-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="58007-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="58007-114">**跟进：** [在配置 max text repl size 选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="58007-114">**Follow Up:**  [After you configure the max text repl size option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="58007-115">开始之前</span><span class="sxs-lookup"><span data-stu-id="58007-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="58007-116">限制和局限</span><span class="sxs-lookup"><span data-stu-id="58007-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="58007-117">此选项适用于事务复制和变更数据捕获。</span><span class="sxs-lookup"><span data-stu-id="58007-117">This option applies to transactional replication and Change Data Capture.</span></span> <span data-ttu-id="58007-118">当将服务器配置为具有事务复制功能和变更数据捕获功能时，指定的值将适用于这两项功能。</span><span class="sxs-lookup"><span data-stu-id="58007-118">When a server is configured for both transactional replication and Change Data Capture, the specified value applies to both features.</span></span> <span data-ttu-id="58007-119">快照复制和合并复制将会忽略此选项。</span><span class="sxs-lookup"><span data-stu-id="58007-119">This option is ignored by snapshot replication and merge replication.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="58007-120">Security</span><span class="sxs-lookup"><span data-stu-id="58007-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="58007-121">权限</span><span class="sxs-lookup"><span data-stu-id="58007-121">Permissions</span></span>  
 <span data-ttu-id="58007-122">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="58007-122">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="58007-123">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="58007-123">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="58007-124">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="58007-124">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="58007-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="58007-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-max-text-repl-size-option"></a><span data-ttu-id="58007-126">配置 max text repl size 选项</span><span class="sxs-lookup"><span data-stu-id="58007-126">To configure the max text repl size option</span></span>  
  
1.  <span data-ttu-id="58007-127">在对象资源管理器中，右键单击服务器并选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="58007-127">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="58007-128">单击 **“高级”** 节点。</span><span class="sxs-lookup"><span data-stu-id="58007-128">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="58007-129">在 **“杂项”** 下，将 **“最大文本复制大小”** 选项更改为所需的值。</span><span class="sxs-lookup"><span data-stu-id="58007-129">Under **Miscellaneous**, change the **Max Text Replication Size** option to the desired value.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="58007-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="58007-130">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-max-text-repl-size-option"></a><span data-ttu-id="58007-131">配置 max text repl size 选项</span><span class="sxs-lookup"><span data-stu-id="58007-131">To configure the max text repl size option</span></span>  
  
1.  <span data-ttu-id="58007-132">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="58007-132">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="58007-133">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="58007-133">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="58007-134">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="58007-134">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="58007-135">此示例说明如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将 `max text repl size` 选项的值配置为 `-1`。</span><span class="sxs-lookup"><span data-stu-id="58007-135">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the `max text repl size` option to `-1`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;   
RECONFIGURE ;   
GO  
EXEC sp_configure 'max text repl size', -1 ;   
GO  
RECONFIGURE;   
GO  
  
```  
  
 <span data-ttu-id="58007-136">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="58007-136">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-max-text-repl-size-option"></a><a name="FollowUp"></a> <span data-ttu-id="58007-137">跟进：在配置 max text repl size 选项之后</span><span class="sxs-lookup"><span data-stu-id="58007-137">Follow Up: After you configure the max text repl size option</span></span>  
 <span data-ttu-id="58007-138">该设置将立即生效，无需重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="58007-138">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58007-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="58007-139">See Also</span></span>  
 <span data-ttu-id="58007-140">[SQL Server 复制](../../relational-databases/replication/sql-server-replication.md) </span><span class="sxs-lookup"><span data-stu-id="58007-140">[SQL Server Replication](../../relational-databases/replication/sql-server-replication.md) </span></span>  
 <span data-ttu-id="58007-141">[INSERT (Transact-SQL)](/sql/t-sql/statements/insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="58007-141">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span></span>  
 <span data-ttu-id="58007-142">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="58007-142">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="58007-143">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="58007-143">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="58007-144">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="58007-144">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="58007-145">[UPDATE (Transact-SQL)](/sql/t-sql/queries/update-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="58007-145">[UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) </span></span>  
 <span data-ttu-id="58007-146">[UPDATETEXT (Transact-SQL)](/sql/t-sql/queries/updatetext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="58007-146">[UPDATETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/updatetext-transact-sql) </span></span>  
 [<span data-ttu-id="58007-147">WRITETEXT (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="58007-147">WRITETEXT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/writetext-transact-sql)  
  
  
