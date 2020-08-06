---
title: 配置 locks 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- locks option [SQL Server]
ms.assetid: b0cf0f86-7652-4574-a9fb-908e10d03973
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e45f4cc539be585966eb0beb30d4938b504c3419
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693462"
---
# <a name="configure-the-locks-server-configuration-option"></a><span data-ttu-id="47e3c-102">配置 locks 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="47e3c-102">Configure the locks Server Configuration Option</span></span>
  <span data-ttu-id="47e3c-103">本主题说明如何使用 **或** 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中配置 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] locks [!INCLUDE[tsql](../../includes/tsql-md.md)]服务器配置选项。</span><span class="sxs-lookup"><span data-stu-id="47e3c-103">This topic describes how to configure the **locks** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="47e3c-104">**locks** 选项设置可用锁的最大数目，以限制 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 为锁分配的内存量。</span><span class="sxs-lookup"><span data-stu-id="47e3c-104">The **locks** option sets the maximum number of available locks, thereby limiting the amount of memory the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uses for them.</span></span> <span data-ttu-id="47e3c-105">默认设置为 0，即允许 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 根据不断变化的系统要求动态地分配和释放锁结构。</span><span class="sxs-lookup"><span data-stu-id="47e3c-105">The default setting is 0, which allows the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to allocate and deallocate lock structures dynamically, based on changing system requirements.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 <span data-ttu-id="47e3c-106">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="47e3c-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="47e3c-107">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="47e3c-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="47e3c-108">建议</span><span class="sxs-lookup"><span data-stu-id="47e3c-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="47e3c-109">安全性</span><span class="sxs-lookup"><span data-stu-id="47e3c-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="47e3c-110">**配置 locks 选项，使用：**</span><span class="sxs-lookup"><span data-stu-id="47e3c-110">**To configure the locks option, using:**</span></span>  
  
     [<span data-ttu-id="47e3c-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="47e3c-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="47e3c-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="47e3c-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="47e3c-113">**跟进：** [在配置锁选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="47e3c-113">**Follow Up:**  [After you configure the locks option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="47e3c-114">开始之前</span><span class="sxs-lookup"><span data-stu-id="47e3c-114">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="47e3c-115">建议</span><span class="sxs-lookup"><span data-stu-id="47e3c-115">Recommendations</span></span>  
  
-   <span data-ttu-id="47e3c-116">此选项是一个高级选项，仅应由有经验的数据库管理员或认证的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技术人员更改。</span><span class="sxs-lookup"><span data-stu-id="47e3c-116">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="47e3c-117">如果服务器启动时 **locks** 设置为 0，锁管理器将从 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 中获取足够的内存，用于包含 2,500 个锁结构的初始池。</span><span class="sxs-lookup"><span data-stu-id="47e3c-117">When the server is started with **locks** set to 0, the lock manager acquires sufficient memory from the [!INCLUDE[ssDE](../../includes/ssde-md.md)] for an initial pool of 2,500 lock structures.</span></span> <span data-ttu-id="47e3c-118">当锁池用完时，将另外为该池获取内存。</span><span class="sxs-lookup"><span data-stu-id="47e3c-118">As the lock pool is exhausted, additional memory is acquired for the pool.</span></span>  
  
     <span data-ttu-id="47e3c-119">通常情况下，如果锁池需要的内存比 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 内存池中可用的内存多，而具有更多可用的计算机内存（尚未达到 **max server memory** 的阈值），则 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 将动态分配内存以满足锁的请求。</span><span class="sxs-lookup"><span data-stu-id="47e3c-119">Generally, if more memory is required for the lock pool than is available in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] memory pool, and more computer memory is available (the **max server memory** threshold has not been reached), the [!INCLUDE[ssDE](../../includes/ssde-md.md)] allocates memory dynamically to satisfy the request for locks.</span></span> <span data-ttu-id="47e3c-120">但是，如果内存分配导致操作系统级的分页（例如，如果另一个应用程序与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例在同一台计算机上运行并使用该计算机的内存），则不会分配更多的锁空间。</span><span class="sxs-lookup"><span data-stu-id="47e3c-120">However, if allocating that memory would cause paging at the operating system level (for example, if another application is running on the same computer as an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and using that memory), more lock space is not allocated.</span></span> <span data-ttu-id="47e3c-121">动态锁池获取的内存不会超过分配给 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的内存的 60%。</span><span class="sxs-lookup"><span data-stu-id="47e3c-121">The dynamic lock pool does not acquire more than 60 percent of the memory allocated to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="47e3c-122">如果锁池获取的内存达到了 [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例所获取内存的 60%，或计算机上没有更多的可用内存，则再发出针对锁的请求将生成错误。</span><span class="sxs-lookup"><span data-stu-id="47e3c-122">After the lock pool has reached 60 percent of the memory acquired by an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], or no more memory is available on the computer, further requests for locks generate an error.</span></span>  
  
     <span data-ttu-id="47e3c-123">推荐的配置是允许 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 动态地使用锁。</span><span class="sxs-lookup"><span data-stu-id="47e3c-123">Allowing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to use locks dynamically is the recommended configuration.</span></span> <span data-ttu-id="47e3c-124">但是，可以通过设置 **locks** 来替代 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 动态分配锁资源的能力。</span><span class="sxs-lookup"><span data-stu-id="47e3c-124">However, you can set **locks** and override the ability of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to allocate lock resources dynamically.</span></span> <span data-ttu-id="47e3c-125">将 **locks** 设置为 0 以外的值后， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 分配的锁的数量不能大于在 **locks**中指定的值。</span><span class="sxs-lookup"><span data-stu-id="47e3c-125">When **locks** is set to a value other than 0, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] cannot allocate more locks than the value specified in **locks**.</span></span> <span data-ttu-id="47e3c-126">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 显示消息说明超过了可用锁数，请增大此值。</span><span class="sxs-lookup"><span data-stu-id="47e3c-126">Increase this value if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] displays a message that you have exceeded the number of available locks.</span></span> <span data-ttu-id="47e3c-127">由于每一个锁都需要消耗内存（每一个锁需 96 字节），增加此值将增加服务器对内存的需求。</span><span class="sxs-lookup"><span data-stu-id="47e3c-127">Because each lock consumes memory (96 bytes per lock), increasing this value can require increasing the amount of memory dedicated to the server.</span></span>  
  
-   <span data-ttu-id="47e3c-128">**locks** 选项也会影响何时进行锁升级。</span><span class="sxs-lookup"><span data-stu-id="47e3c-128">The **locks** option also affects when lock escalation occurs.</span></span> <span data-ttu-id="47e3c-129">如果 **locks** 设置为 0，则当前锁结构使用的内存达到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 内存池的 40% 时将进行锁升级。</span><span class="sxs-lookup"><span data-stu-id="47e3c-129">When **locks** is set to 0, lock escalation occurs when the memory used by the current lock structures reaches 40 percent of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] memory pool.</span></span> <span data-ttu-id="47e3c-130">如果 **locks** 未设置为 0，则当锁的数量达到 **locks**的指定值的 40% 时将进行锁升级。</span><span class="sxs-lookup"><span data-stu-id="47e3c-130">When **locks** is not set to 0, lock escalation occurs when the number of locks reaches 40 percent of the value specified for **locks**.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="47e3c-131">Security</span><span class="sxs-lookup"><span data-stu-id="47e3c-131">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="47e3c-132">权限</span><span class="sxs-lookup"><span data-stu-id="47e3c-132">Permissions</span></span>  
 <span data-ttu-id="47e3c-133">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="47e3c-133">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="47e3c-134">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="47e3c-134">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="47e3c-135">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="47e3c-135">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="47e3c-136">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="47e3c-136">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-locks-option"></a><span data-ttu-id="47e3c-137">配置 locks 选项</span><span class="sxs-lookup"><span data-stu-id="47e3c-137">To configure the locks option</span></span>  
  
1.  <span data-ttu-id="47e3c-138">在对象资源管理器中，右键单击服务器并选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="47e3c-138">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="47e3c-139">单击 **“高级”** 节点。</span><span class="sxs-lookup"><span data-stu-id="47e3c-139">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="47e3c-140">在 **“并行”** 之下，键入想要的 **locks** 选项的值。</span><span class="sxs-lookup"><span data-stu-id="47e3c-140">Under **Parallelism**, type the desired value for the **locks** option.</span></span>  
  
     <span data-ttu-id="47e3c-141">使用 **locks** 选项设置可用锁的最大数目，以限制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 为锁分配的内存量。</span><span class="sxs-lookup"><span data-stu-id="47e3c-141">Use the **locks** option to set the maximum number of available locks, thereby limiting the amount of memory [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses for them.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="47e3c-142">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="47e3c-142">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-locks-option"></a><span data-ttu-id="47e3c-143">配置 locks 选项</span><span class="sxs-lookup"><span data-stu-id="47e3c-143">To configure the locks option</span></span>  
  
1.  <span data-ttu-id="47e3c-144">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="47e3c-144">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="47e3c-145">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="47e3c-145">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="47e3c-146">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="47e3c-146">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="47e3c-147">此示例说明如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 设置 `locks` 选项的值，将所有用户可用的锁数设置为 `20000`。</span><span class="sxs-lookup"><span data-stu-id="47e3c-147">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `locks` option to set the number of locks available for all users to `20000`.</span></span>  
  
```sql  
Use AdventureWorks2012 ;  
GO  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'locks', 20000;  
GO  
RECONFIGURE;  
GO  
```  
  
 <span data-ttu-id="47e3c-148">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="47e3c-148">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-locks-option"></a><a name="FollowUp"></a> <span data-ttu-id="47e3c-149">跟进：在配置锁选项之后</span><span class="sxs-lookup"><span data-stu-id="47e3c-149">Follow Up: After you configure the locks option</span></span>  
 <span data-ttu-id="47e3c-150">必须重新启动服务器，设置才会生效。</span><span class="sxs-lookup"><span data-stu-id="47e3c-150">The server must be restarted before the setting can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47e3c-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="47e3c-151">See Also</span></span>  
 <span data-ttu-id="47e3c-152">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="47e3c-152">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="47e3c-153">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="47e3c-153">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="47e3c-154">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="47e3c-154">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
