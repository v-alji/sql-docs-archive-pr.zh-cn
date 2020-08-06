---
title: 配置 index create memory 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- index create memory option
ms.assetid: 3d722d9b-bada-4bf5-a9d7-bfc556bb4915
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6cd0aeb93d3fb68089338335068fdaaae19919fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689583"
---
# <a name="configure-the-index-create-memory-server-configuration-option"></a><span data-ttu-id="0fe11-102">配置 index create memory 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="0fe11-102">Configure the index create memory Server Configuration Option</span></span>
  <span data-ttu-id="0fe11-103">本主题说明如何使用 **或** 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中配置 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] index create memory [!INCLUDE[tsql](../../includes/tsql-md.md)]服务器配置选项。</span><span class="sxs-lookup"><span data-stu-id="0fe11-103">This topic describes how to configure the **index create memory** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="0fe11-104">**index create memory** 选项控制最初为创建索引分配的最大内存量。</span><span class="sxs-lookup"><span data-stu-id="0fe11-104">The **index create memory** option controls the maximum amount of memory initially allocated for creating indexes.</span></span> <span data-ttu-id="0fe11-105">此选项的默认值为 0（自动配置）。</span><span class="sxs-lookup"><span data-stu-id="0fe11-105">The default value for this option is 0 (self-configuring).</span></span> <span data-ttu-id="0fe11-106">如果随后创建索引时需要更多内存，而且有内存可供使用，服务器将使用可用的内存，从而超出此选项的设置。</span><span class="sxs-lookup"><span data-stu-id="0fe11-106">If more memory is later needed for index creation and the memory is available, the server will use it; thereby, exceeding the setting of this option.</span></span> <span data-ttu-id="0fe11-107">如果没有内存可供使用，则继续使用已分配的内存来创建索引。</span><span class="sxs-lookup"><span data-stu-id="0fe11-107">If additional memory is not available, the index creation will continue using the memory already allocated.</span></span>  
  
 <span data-ttu-id="0fe11-108">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="0fe11-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0fe11-109">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="0fe11-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0fe11-110">限制和局限</span><span class="sxs-lookup"><span data-stu-id="0fe11-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="0fe11-111">建议</span><span class="sxs-lookup"><span data-stu-id="0fe11-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="0fe11-112">安全性</span><span class="sxs-lookup"><span data-stu-id="0fe11-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0fe11-113">**配置 index create memory 选项，使用：**</span><span class="sxs-lookup"><span data-stu-id="0fe11-113">**To configure the index create memory option, using:**</span></span>  
  
     [<span data-ttu-id="0fe11-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0fe11-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0fe11-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0fe11-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="0fe11-116">**跟进：** [在配置 index create memory 选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="0fe11-116">**Follow Up:**  [After you configure the index create memory option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0fe11-117">开始之前</span><span class="sxs-lookup"><span data-stu-id="0fe11-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0fe11-118">限制和局限</span><span class="sxs-lookup"><span data-stu-id="0fe11-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="0fe11-119">"**每次查询占用的最小内存**" 选项的设置优先于**索引创建内存**选项。</span><span class="sxs-lookup"><span data-stu-id="0fe11-119">The setting of the **min memory per query** option has precedence over the **index create memory** option.</span></span> <span data-ttu-id="0fe11-120">如果更改这些选项，使 **index create memory** 小于 **min memory per query**，则会收到警告消息，但设置的值仍会生效。</span><span class="sxs-lookup"><span data-stu-id="0fe11-120">If you change both options and the **index create memory** is less than **min memory per query**, you receive a warning message, but the value is set.</span></span> <span data-ttu-id="0fe11-121">而且，在查询执行过程中，您还会收到类似的警告。</span><span class="sxs-lookup"><span data-stu-id="0fe11-121">During query execution, you receive a similar warning.</span></span>  
  
-   <span data-ttu-id="0fe11-122">使用已分区表和已分区索引时，如果出现非对齐的已分区索引且并行度很高，则创建索引时的最低内存要求将显著提高。</span><span class="sxs-lookup"><span data-stu-id="0fe11-122">When using partitioned tables and indexes, the minimum memory requirements for index creation may increase significantly if there are non-aligned partitioned indexes and a high degree of parallelism.</span></span> <span data-ttu-id="0fe11-123">此选项控制在单一索引创建操作中为所有索引分区分配的初始内存总量。</span><span class="sxs-lookup"><span data-stu-id="0fe11-123">This option controls the total initial amount of memory allocated for all index partitions in a single index creation operation.</span></span> <span data-ttu-id="0fe11-124">如果此选项设置的内存量小于运行查询所需的最小内存，查询将终止并显示错误消息。</span><span class="sxs-lookup"><span data-stu-id="0fe11-124">The query will terminate with an error message if the amount set by this option is less than the minimum required to run the query.</span></span>  
  
-   <span data-ttu-id="0fe11-125">此选项的运行值不会超过用于运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的操作系统和硬件平台的实际内存量。</span><span class="sxs-lookup"><span data-stu-id="0fe11-125">The run value for this option will not exceed the actual amount of memory that can be used for the operating system and hardware platform on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span> <span data-ttu-id="0fe11-126">在 32 位操作系统中，运行值将小于 3 GB。</span><span class="sxs-lookup"><span data-stu-id="0fe11-126">On 32-bit operating systems, the run value will be less than 3 gigabytes (GB).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="0fe11-127">建议</span><span class="sxs-lookup"><span data-stu-id="0fe11-127">Recommendations</span></span>  
  
-   <span data-ttu-id="0fe11-128">此选项是一个高级选项，仅应由有经验的数据库管理员或认证的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技术人员更改。</span><span class="sxs-lookup"><span data-stu-id="0fe11-128">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="0fe11-129">**index create memory** 选项是自行配置的，通常不需要调整即可工作。</span><span class="sxs-lookup"><span data-stu-id="0fe11-129">The **index create memory** option is self-configuring and usually works without requiring adjustment.</span></span> <span data-ttu-id="0fe11-130">但如果在创建索引时遇到困难，可以考虑提高此选项的运行值。</span><span class="sxs-lookup"><span data-stu-id="0fe11-130">However, if you experience difficulties creating indexes, consider increasing the value of this option from its run value.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0fe11-131">Security</span><span class="sxs-lookup"><span data-stu-id="0fe11-131">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0fe11-132">权限</span><span class="sxs-lookup"><span data-stu-id="0fe11-132">Permissions</span></span>  
 <span data-ttu-id="0fe11-133">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="0fe11-133">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="0fe11-134">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="0fe11-134">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="0fe11-135">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="0fe11-135">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0fe11-136">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0fe11-136">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-index-create-memory-option"></a><span data-ttu-id="0fe11-137">配置 index create memory 选项</span><span class="sxs-lookup"><span data-stu-id="0fe11-137">To configure the index create memory option</span></span>  
  
1.  <span data-ttu-id="0fe11-138">在对象资源管理器中，右键单击服务器并选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="0fe11-138">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="0fe11-139">单击 **“内存”** 节点。</span><span class="sxs-lookup"><span data-stu-id="0fe11-139">Click the **Memory** node.</span></span>  
  
3.  <span data-ttu-id="0fe11-140">在 **“创建索引占用的内存”** 下，为 index create memory 选项键入或选择所需的值。</span><span class="sxs-lookup"><span data-stu-id="0fe11-140">Under **Index creation memory**, type or select the desired value for the index create memory option.</span></span>  
  
     <span data-ttu-id="0fe11-141">**index create memory** 选项用于控制索引创建排序时所需的内存量。</span><span class="sxs-lookup"><span data-stu-id="0fe11-141">Use the **index create memory** option to control the amount of memory used by index creation sorts.</span></span> <span data-ttu-id="0fe11-142">**index create memory** 选项是自配置选项，在大多数情况下不需调整即可正常工作。</span><span class="sxs-lookup"><span data-stu-id="0fe11-142">The **index create memory** option is self-configuring and should work in most cases without requiring adjustment.</span></span> <span data-ttu-id="0fe11-143">但如果在创建索引时遇到困难，可以考虑提高此选项的运行值。</span><span class="sxs-lookup"><span data-stu-id="0fe11-143">However, if you experience difficulties creating indexes, consider increasing the value of this option from its run value.</span></span> <span data-ttu-id="0fe11-144">查询排序由 **min memory per query** 选项控制。</span><span class="sxs-lookup"><span data-stu-id="0fe11-144">Query sorts are controlled through the **min memory per query** option.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0fe11-145">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0fe11-145">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-index-create-memory-option"></a><span data-ttu-id="0fe11-146">配置 index create memory 选项</span><span class="sxs-lookup"><span data-stu-id="0fe11-146">To configure the index create memory option</span></span>  
  
1.  <span data-ttu-id="0fe11-147">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0fe11-147">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0fe11-148">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="0fe11-148">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0fe11-149">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="0fe11-149">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="0fe11-150">此示例说明如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将 `index create memory` 选项的值设置为 `4096`。</span><span class="sxs-lookup"><span data-stu-id="0fe11-150">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `index create memory` option to `4096`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
EXEC sp_configure 'index create memory', 4096  
GO  
RECONFIGURE;  
GO  
```  
  
 <span data-ttu-id="0fe11-151">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="0fe11-151">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-index-create-memory-option"></a><a name="FollowUp"></a> <span data-ttu-id="0fe11-152">跟进：在配置 index create memory 选项之后</span><span class="sxs-lookup"><span data-stu-id="0fe11-152">Follow Up: After you configure the index create memory option</span></span>  
 <span data-ttu-id="0fe11-153">该设置将立即生效，无需重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="0fe11-153">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fe11-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0fe11-154">See Also</span></span>  
 <span data-ttu-id="0fe11-155">[sys.configurations (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0fe11-155">[sys.configurations &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) </span></span>  
 <span data-ttu-id="0fe11-156">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0fe11-156">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="0fe11-157">[“服务器内存”服务器配置选项](server-memory-server-configuration-options.md) </span><span class="sxs-lookup"><span data-stu-id="0fe11-157">[Server Memory Server Configuration Options](server-memory-server-configuration-options.md) </span></span>  
 <span data-ttu-id="0fe11-158">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0fe11-158">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="0fe11-159">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0fe11-159">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
