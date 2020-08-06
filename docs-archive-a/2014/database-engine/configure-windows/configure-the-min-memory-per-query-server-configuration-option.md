---
title: 配置 min memory per query 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- memory [SQL Server], queries
- minimum query memory
- queries [SQL Server], memory
- min memory per query option
ms.assetid: ecd3fb79-b4a6-432f-9ef5-530e0d42d5a6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 56d85f36840f0900c8b5e986334a99ba610d3930
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588036"
---
# <a name="configure-the-min-memory-per-query-server-configuration-option"></a><span data-ttu-id="2dffe-102">配置每次查询占用的最小内存服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="2dffe-102">Configure the min memory per query Server Configuration Option</span></span>
  <span data-ttu-id="2dffe-103">本主题说明如何 `min memory per query` 使用或在中配置服务器配置选项 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2dffe-103">This topic describes how to configure the `min memory per query` server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="2dffe-104">`min memory per query`选项指定将为执行查询分配的最小内存量 (以 kb 为单位) 。</span><span class="sxs-lookup"><span data-stu-id="2dffe-104">The `min memory per query` option specifies the minimum amount of memory (in kilobytes) that will be allocated for the execution of a query.</span></span> <span data-ttu-id="2dffe-105">例如，如果 `min memory per query` 设置为 2048 KB，则保证查询至少获得这么多内存。</span><span class="sxs-lookup"><span data-stu-id="2dffe-105">For example, if `min memory per query` is set to 2,048 KB, the query is guaranteed to get at least that much total memory.</span></span> <span data-ttu-id="2dffe-106">默认值为 1,024 KB。</span><span class="sxs-lookup"><span data-stu-id="2dffe-106">The default value is 1,024 KB.</span></span> <span data-ttu-id="2dffe-107">最小值为 512 KB，最大值为 2,147,483,647 KB (2 GB)。</span><span class="sxs-lookup"><span data-stu-id="2dffe-107">The minimum value 512 KB, and the maximum is 2,147,483,647 KB (2 GB).</span></span>  
  
 <span data-ttu-id="2dffe-108">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="2dffe-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2dffe-109">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="2dffe-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2dffe-110">限制和局限</span><span class="sxs-lookup"><span data-stu-id="2dffe-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="2dffe-111">建议</span><span class="sxs-lookup"><span data-stu-id="2dffe-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="2dffe-112">安全性</span><span class="sxs-lookup"><span data-stu-id="2dffe-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2dffe-113">**若要配置每次查询占用的最小内存选项，请使用：**</span><span class="sxs-lookup"><span data-stu-id="2dffe-113">**To configure the min memory per query option, using:**</span></span>  
  
     [<span data-ttu-id="2dffe-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2dffe-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2dffe-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2dffe-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="2dffe-116">**跟进：** [在配置每次查询占用的最小内存选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="2dffe-116">**Follow Up:**  [After you configure the min memory per query option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2dffe-117">开始之前</span><span class="sxs-lookup"><span data-stu-id="2dffe-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="2dffe-118">限制和局限</span><span class="sxs-lookup"><span data-stu-id="2dffe-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="2dffe-119">每个查询的最小内存量优先于[索引创建内存选项](configure-the-index-create-memory-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="2dffe-119">The amount of min memory per query has precedence over the [index create memory Option](configure-the-index-create-memory-server-configuration-option.md).</span></span> <span data-ttu-id="2dffe-120">如果改变这两个选项，并且索引创建内存小于每次查询占用的最小内存，则将收到警告消息，但仍会设置值。</span><span class="sxs-lookup"><span data-stu-id="2dffe-120">If you modify both options and the index create memory is less than min memory per query, you receive a warning message, but the value is set.</span></span> <span data-ttu-id="2dffe-121">在查询执行期间还会收到一个类似的警告。</span><span class="sxs-lookup"><span data-stu-id="2dffe-121">During query execution you receive another similar warning.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="2dffe-122">建议</span><span class="sxs-lookup"><span data-stu-id="2dffe-122">Recommendations</span></span>  
  
-   <span data-ttu-id="2dffe-123">此选项是一个高级选项，仅应由有经验的数据库管理员或认证的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技术人员更改。</span><span class="sxs-lookup"><span data-stu-id="2dffe-123">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="2dffe-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 查询处理器尝试确定要分配给查询的最佳内存量。</span><span class="sxs-lookup"><span data-stu-id="2dffe-124">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] query processor tries to determine the optimal amount of memory to allocate to a query.</span></span> <span data-ttu-id="2dffe-125">min memory per query 选项允许管理员指定任何单个查询收到的最小内存量。</span><span class="sxs-lookup"><span data-stu-id="2dffe-125">The min memory per query option lets the administrator specify the minimum amount of memory any single query receives.</span></span> <span data-ttu-id="2dffe-126">如果查询需要对大量数据执行哈希和排序操作，则这些查询获得的内存通常比该选项指定的最小内存多。</span><span class="sxs-lookup"><span data-stu-id="2dffe-126">Queries generally receive more memory than this if they have hash and sort operations on a large volume of data.</span></span> <span data-ttu-id="2dffe-127">对于一些小型查询和中等大小的查询，增大 min memory per query 的值可能提高性能，但会导致内存资源争夺加剧。</span><span class="sxs-lookup"><span data-stu-id="2dffe-127">Increasing the value of min memory per query may improve performance for some small to medium-sized queries, but doing so could lead to increased competition for memory resources.</span></span> <span data-ttu-id="2dffe-128">每次查询占用的最小内存选项包括为排序分配的内存。</span><span class="sxs-lookup"><span data-stu-id="2dffe-128">The min memory per query option includes memory allocated for sorting.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2dffe-129">Security</span><span class="sxs-lookup"><span data-stu-id="2dffe-129">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2dffe-130">权限</span><span class="sxs-lookup"><span data-stu-id="2dffe-130">Permissions</span></span>  
 <span data-ttu-id="2dffe-131">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="2dffe-131">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="2dffe-132">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="2dffe-132">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="2dffe-133">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="2dffe-133">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2dffe-134">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2dffe-134">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-min-memory-per-query-option"></a><span data-ttu-id="2dffe-135">配置每次查询占用的最小内存选项</span><span class="sxs-lookup"><span data-stu-id="2dffe-135">To configure the min memory per query option</span></span>  
  
1.  <span data-ttu-id="2dffe-136">在对象资源管理器中，右键单击服务器并选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="2dffe-136">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="2dffe-137">单击 **“内存”** 节点。</span><span class="sxs-lookup"><span data-stu-id="2dffe-137">Click the **Memory** node.</span></span>  
  
3.  <span data-ttu-id="2dffe-138">在“每次查询占用的最小内存”框中，输入将分配给查询执行时所需要的最小内存量 (KB)。</span><span class="sxs-lookup"><span data-stu-id="2dffe-138">In the **Minimum memory per query** box, enter the minimum amount of memory (in kilobytes) that will be allocated for the execution of a query.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2dffe-139">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2dffe-139">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-min-memory-per-query-option"></a><span data-ttu-id="2dffe-140">配置每次查询占用的最小内存选项</span><span class="sxs-lookup"><span data-stu-id="2dffe-140">To configure the min memory per query option</span></span>  
  
1.  <span data-ttu-id="2dffe-141">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2dffe-141">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2dffe-142">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="2dffe-142">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2dffe-143">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="2dffe-143">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="2dffe-144">本示例演示如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将 `min memory per query` 选项的值设置为 `3500` KB。</span><span class="sxs-lookup"><span data-stu-id="2dffe-144">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `min memory per query` option to `3500` KB.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'min memory per query', 3500 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
##  <a name="follow-up-after-you-configure-the-min-memory-per-query-option"></a><a name="FollowUp"></a> <span data-ttu-id="2dffe-145">跟进：在配置每次查询占用的最小内存选项之后</span><span class="sxs-lookup"><span data-stu-id="2dffe-145">Follow Up: After you configure the min memory per query option</span></span>  
 <span data-ttu-id="2dffe-146">该设置将立即生效，无需重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="2dffe-146">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dffe-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2dffe-147">See Also</span></span>  
 <span data-ttu-id="2dffe-148">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2dffe-148">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="2dffe-149">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2dffe-149">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="2dffe-150">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2dffe-150">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="2dffe-151">配置 index create memory 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="2dffe-151">Configure the index create memory Server Configuration Option</span></span>](configure-the-index-create-memory-server-configuration-option.md)  
  
  
