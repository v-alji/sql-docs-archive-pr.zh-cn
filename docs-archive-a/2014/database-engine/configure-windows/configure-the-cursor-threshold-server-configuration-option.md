---
title: 配置“游标阈值”服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- cursor threshold option
ms.assetid: 189f2067-c6c4-48bd-9bd9-65f6b2021c12
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0d7fd9ecafda270a02f1fba9f5dd74adc9e299d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591588"
---
# <a name="configure-the-cursor-threshold-server-configuration-option"></a><span data-ttu-id="a5697-102">配置 cursor threshold 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="a5697-102">Configure the cursor threshold Server Configuration Option</span></span>
  <span data-ttu-id="a5697-103">本主题说明如何使用 **或** 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中配置 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] cursor threshold [!INCLUDE[tsql](../../includes/tsql-md.md)]服务器配置选项。</span><span class="sxs-lookup"><span data-stu-id="a5697-103">This topic describes how to configure the **cursor threshold** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="a5697-104">**cursor threshold** 选项指定游标集中的行数，超过此行数，将异步生成游标键集。</span><span class="sxs-lookup"><span data-stu-id="a5697-104">The **cursor threshold** option specifies the number of rows in the cursor set at which cursor keysets are generated asynchronously.</span></span> <span data-ttu-id="a5697-105">当游标为结果集生成键集时，查询优化器会估算将为该结果集返回的行数。</span><span class="sxs-lookup"><span data-stu-id="a5697-105">When cursors generate a keyset for a result set, the query optimizer estimates the number of rows that will be returned for that result set.</span></span> <span data-ttu-id="a5697-106">如果查询优化器估算出的返回行数大于此阈值，则将异步生成游标，使用户能够在继续填充游标的同时从该游标中提取行。</span><span class="sxs-lookup"><span data-stu-id="a5697-106">If the query optimizer estimates that the number of returned rows is greater than this threshold, the cursor is generated asynchronously, allowing the user to fetch rows from the cursor while the cursor continues to be populated.</span></span> <span data-ttu-id="a5697-107">否则，同步生成游标，查询将一直等待到返回所有行。</span><span class="sxs-lookup"><span data-stu-id="a5697-107">Otherwise, the cursor is generated synchronously, and the query waits until all rows are returned.</span></span>  
  
 <span data-ttu-id="a5697-108">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="a5697-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a5697-109">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="a5697-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a5697-110">限制和局限</span><span class="sxs-lookup"><span data-stu-id="a5697-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a5697-111">建议</span><span class="sxs-lookup"><span data-stu-id="a5697-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="a5697-112">安全性</span><span class="sxs-lookup"><span data-stu-id="a5697-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a5697-113">**配置 cursor threshold 选项，使用：**</span><span class="sxs-lookup"><span data-stu-id="a5697-113">**To configure the cursor threshold option, using:**</span></span>  
  
     [<span data-ttu-id="a5697-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a5697-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a5697-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a5697-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="a5697-116">**跟进：** [在配置游标阈值选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="a5697-116">**Follow Up:**  [After you configure the cursor threshold option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a5697-117">开始之前</span><span class="sxs-lookup"><span data-stu-id="a5697-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a5697-118">限制和局限</span><span class="sxs-lookup"><span data-stu-id="a5697-118">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a5697-119">不支持异步生成由键集驱动的或静态的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 游标。</span><span class="sxs-lookup"><span data-stu-id="a5697-119">does not support generating keyset-driven or static [!INCLUDE[tsql](../../includes/tsql-md.md)] cursors asynchronously.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="a5697-120">游标操作（如 OPEN 或 FETCH）均为批处理，所以无需异步生成 [!INCLUDE[tsql](../../includes/tsql-md.md)] 游标。</span><span class="sxs-lookup"><span data-stu-id="a5697-120">cursor operations such as OPEN or FETCH are batched, so there is no need for the asynchronous generation of [!INCLUDE[tsql](../../includes/tsql-md.md)] cursors.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a5697-121">由于每个游标操作都需要进行客户端往返，因此继续支持异步的由键集驱动的或静态的应用程序编程接口 (API) 服务器游标，对于这些游标，OPEN 实现低延迟时间很重要。</span><span class="sxs-lookup"><span data-stu-id="a5697-121">continues to support asynchronous keyset-driven or static application programming interface (API) server cursors where low latency OPEN is a concern, due to client round trips for each cursor operation.</span></span>  
  
-   <span data-ttu-id="a5697-122">查询优化器估计键集中行数的准确性取决于游标中每个表统计信息的当前值。</span><span class="sxs-lookup"><span data-stu-id="a5697-122">The accuracy of the query optimizer to determine an estimate for the number of rows in a keyset depends on the currency of the statistics for each of the tables in the cursor.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="a5697-123">建议</span><span class="sxs-lookup"><span data-stu-id="a5697-123">Recommendations</span></span>  
  
-   <span data-ttu-id="a5697-124">此选项是一个高级选项，仅应由有经验的数据库管理员或认证的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技术人员更改。</span><span class="sxs-lookup"><span data-stu-id="a5697-124">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="a5697-125">如果将 **游标阙值** 设置为 -1，则所有游标键集将同步生成，这对于小游标集很有用。</span><span class="sxs-lookup"><span data-stu-id="a5697-125">If you set **cursor threshold** to -1, all keysets are generated synchronously, which benefits small cursor sets.</span></span> <span data-ttu-id="a5697-126">如果将 **cursor threshold** 设置为 0，则所有游标键集将异步生成。</span><span class="sxs-lookup"><span data-stu-id="a5697-126">If you set **cursor threshold** to 0, all cursor keysets are generated asynchronously.</span></span> <span data-ttu-id="a5697-127">如果 **cursor threshold**为其他值，则查询优化器将比较该值与游标集中的所需行数，如果后者大于前者，则将异步生成键集。</span><span class="sxs-lookup"><span data-stu-id="a5697-127">With other values, the query optimizer compares the number of expected rows in the cursor set and builds the keyset asynchronously if it exceeds the number set in **cursor threshold**.</span></span> <span data-ttu-id="a5697-128">不要将 **cursor threshold** 的值设置得过低，因为最好以同步方式创建小结果集。</span><span class="sxs-lookup"><span data-stu-id="a5697-128">Do not set **cursor threshold** too low, because small result sets are better built synchronously.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a5697-129">Security</span><span class="sxs-lookup"><span data-stu-id="a5697-129">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a5697-130">权限</span><span class="sxs-lookup"><span data-stu-id="a5697-130">Permissions</span></span>  
 <span data-ttu-id="a5697-131">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="a5697-131">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="a5697-132">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="a5697-132">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="a5697-133">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="a5697-133">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a5697-134">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a5697-134">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-cursor-threshold-option"></a><span data-ttu-id="a5697-135">配置 cursor threshold 选项</span><span class="sxs-lookup"><span data-stu-id="a5697-135">To configure the cursor threshold option</span></span>  
  
1.  <span data-ttu-id="a5697-136">在对象资源管理器中，右键单击服务器并选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="a5697-136">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="a5697-137">单击 **“高级”** 节点。</span><span class="sxs-lookup"><span data-stu-id="a5697-137">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="a5697-138">在 **“杂项”** 下，将 **“游标阈值”** 选项更改为所需的值。</span><span class="sxs-lookup"><span data-stu-id="a5697-138">Under **Miscellaneous**, change the **Cursor Threshold** option to the value you want.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a5697-139">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a5697-139">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-cursor-threshold-option"></a><span data-ttu-id="a5697-140">配置 cursor threshold 选项</span><span class="sxs-lookup"><span data-stu-id="a5697-140">To configure the cursor threshold option</span></span>  
  
1.  <span data-ttu-id="a5697-141">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a5697-141">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a5697-142">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="a5697-142">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a5697-143">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="a5697-143">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="a5697-144">此示例说明如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将 `cursor threshold` 选项设置为 `0` ，以便异步生成游标键集。</span><span class="sxs-lookup"><span data-stu-id="a5697-144">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the `cursor threshold` option to `0` so that cursor keysets are generated asynchronously.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'cursor threshold', 0 ;  
GO  
RECONFIGURE  
GO  
  
```  
  
 <span data-ttu-id="a5697-145">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="a5697-145">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-cursor-threshold-option"></a><a name="FollowUp"></a> <span data-ttu-id="a5697-146">跟进：在配置游标阈值选项之后</span><span class="sxs-lookup"><span data-stu-id="a5697-146">Follow Up: After you configure the cursor threshold option</span></span>  
 <span data-ttu-id="a5697-147">该设置将立即生效，无需重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="a5697-147">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5697-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a5697-148">See Also</span></span>  
 <span data-ttu-id="a5697-149">[@@CURSOR_ROWS (Transact-SQL)](/sql/t-sql/functions/cursor-rows-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a5697-149">[@@CURSOR_ROWS &#40;Transact-SQL&#41;](/sql/t-sql/functions/cursor-rows-transact-sql) </span></span>  
 <span data-ttu-id="a5697-150">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a5697-150">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="a5697-151">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a5697-151">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="a5697-152">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a5697-152">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="a5697-153">更新统计信息 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a5697-153">UPDATE STATISTICS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/update-statistics-transact-sql)  
  
  
