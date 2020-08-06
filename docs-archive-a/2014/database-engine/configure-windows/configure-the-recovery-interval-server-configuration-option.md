---
title: 配置 recovery interval 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- restoring recovery interval [SQL Server]
- checkpoints [SQL Server]
- recovery interval option [SQL Server]
- default recovery interval option
- time [SQL Server], recovery interval
- interval for recovery [SQL Server]
- maximum number of minutes per database recovery
- recovery [SQL Server], recovery interval option
ms.assetid: e4734b3b-8fbe-4b65-9c48-91b5a3dd18e1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 560d514ba8dd1503b59b3b59ecf404d876e24cd2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578431"
---
# <a name="configure-the-recovery-interval-server-configuration-option"></a><span data-ttu-id="33d41-102">配置恢复间隔服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="33d41-102">Configure the recovery interval Server Configuration Option</span></span>
  <span data-ttu-id="33d41-103">本主题说明了如何使用 **或** 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中配置 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] “恢复间隔” [!INCLUDE[tsql](../../includes/tsql-md.md)]服务器配置选项。</span><span class="sxs-lookup"><span data-stu-id="33d41-103">This topic describes how to configure the **recovery interval** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="33d41-104">**“恢复间隔”** 选项定义恢复某一数据库所需时间的上限。</span><span class="sxs-lookup"><span data-stu-id="33d41-104">The **recovery interval** option defines an upper limit on the time recovering a database should take.</span></span> <span data-ttu-id="33d41-105">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 使用为该选项指定的值确定 [自动检查点](../../relational-databases/logs/database-checkpoints-sql-server.md) 对给定数据库发出自动检查点的大致频率。</span><span class="sxs-lookup"><span data-stu-id="33d41-105">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uses the value specified for this option to determine approximately how often [automatic checkpoints](../../relational-databases/logs/database-checkpoints-sql-server.md) to issue automatic checkpoints on a given database.</span></span>  
  
 <span data-ttu-id="33d41-106">默认恢复间隔值为 0，这将允许 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 自动配置恢复间隔。</span><span class="sxs-lookup"><span data-stu-id="33d41-106">The default recovery-interval value is 0, which allows the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to automatically configure the recovery interval.</span></span> <span data-ttu-id="33d41-107">通常，对于活动数据库，该默认恢复间隔将导致大约一分钟执行一次自动检查点检查，并且导致不到一分钟的恢复时间。</span><span class="sxs-lookup"><span data-stu-id="33d41-107">Typically, the default recovery interval results in automatic checkpoints occurring approximately once a minute for active databases and a recovery time of less than one minute.</span></span> <span data-ttu-id="33d41-108">较高的值表示近似的最大恢复时间，以分钟为单位。</span><span class="sxs-lookup"><span data-stu-id="33d41-108">Higher values indicate the approximate maximum recovery time, in minutes.</span></span> <span data-ttu-id="33d41-109">例如，将恢复间隔设置为 3 指示最大恢复时间大约为 3 分钟。</span><span class="sxs-lookup"><span data-stu-id="33d41-109">For example, setting the recovery interval to 3 indicates a maximum recovery time of approximately three minutes.</span></span>  
  
 <span data-ttu-id="33d41-110">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="33d41-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="33d41-111">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="33d41-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="33d41-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="33d41-112">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="33d41-113">建议</span><span class="sxs-lookup"><span data-stu-id="33d41-113">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="33d41-114">安全性</span><span class="sxs-lookup"><span data-stu-id="33d41-114">Security</span></span>](#Security)  
  
-   <span data-ttu-id="33d41-115">**若要配置恢复间隔服务器配置选项，可使用：**</span><span class="sxs-lookup"><span data-stu-id="33d41-115">**To Configure the recovery interval Server Configuration Option, using:**</span></span>  
  
     [<span data-ttu-id="33d41-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="33d41-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="33d41-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="33d41-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="33d41-118">**跟进：** [在配置恢复间隔选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="33d41-118">**Follow Up:**  [After you configure the recovery interval option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="33d41-119">开始之前</span><span class="sxs-lookup"><span data-stu-id="33d41-119">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="33d41-120">限制和局限</span><span class="sxs-lookup"><span data-stu-id="33d41-120">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="33d41-121">恢复间隔仅影响使用默认目标恢复时间 (0) 的数据库。</span><span class="sxs-lookup"><span data-stu-id="33d41-121">The recovery interval affects only databases that use the default target recovery time (0).</span></span> <span data-ttu-id="33d41-122">若要覆盖数据库上的服务器恢复间隔，请对该数据库配置非默认目标恢复时间。</span><span class="sxs-lookup"><span data-stu-id="33d41-122">To override the server recovery interval on a database, configure a non-default target recovery time on the database.</span></span> <span data-ttu-id="33d41-123">有关详细信息，请参阅 [更改数据库的目标恢复时间 (SQL Server)](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md)服务器配置选项。</span><span class="sxs-lookup"><span data-stu-id="33d41-123">For more information, see [Change the Target Recovery Time of a Database &#40;SQL Server&#41;](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="33d41-124">建议</span><span class="sxs-lookup"><span data-stu-id="33d41-124">Recommendations</span></span>  
  
-   <span data-ttu-id="33d41-125">此选项是一个高级选项，仅应由有经验的数据库管理员或认证的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技术人员更改。</span><span class="sxs-lookup"><span data-stu-id="33d41-125">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="33d41-126">通常，我们建议您将恢复间隔保持为 0，除非您遇到了性能问题。</span><span class="sxs-lookup"><span data-stu-id="33d41-126">Typically, we recommend that you keep the recovery interval at 0, unless you experience performance problems.</span></span> <span data-ttu-id="33d41-127">如果您决定增大恢复间隔设置，我们建议一点一点逐渐增大该值并评估每次增大对恢复性能的影响。</span><span class="sxs-lookup"><span data-stu-id="33d41-127">If you decide to increase the recovery-interval setting, we recommend increasing it gradually by small increments and evaluating the effect of each incremental increase on recovery performance.</span></span>  
  
-   <span data-ttu-id="33d41-128">如果您使用 **sp_configure** 将 **“恢复间隔”** 选项的值更改为超过 60（分钟），则指定 RECONFIGURE WITH OVERRIDE。</span><span class="sxs-lookup"><span data-stu-id="33d41-128">If you use **sp_configure** to change the value of the **recovery interval** option to more than 60 (minutes), specify RECONFIGURE WITH OVERRIDE.</span></span> <span data-ttu-id="33d41-129">WITH OVERRIDE 将禁用配置值检查（检查无效的值或并非推荐的值）。</span><span class="sxs-lookup"><span data-stu-id="33d41-129">WITH OVERRIDE disables configuration value checking (for values that are not valid or are nonrecommended values).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="33d41-130">Security</span><span class="sxs-lookup"><span data-stu-id="33d41-130">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="33d41-131">权限</span><span class="sxs-lookup"><span data-stu-id="33d41-131">Permissions</span></span>  
 <span data-ttu-id="33d41-132">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="33d41-132">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="33d41-133">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="33d41-133">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="33d41-134">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="33d41-134">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="33d41-135">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="33d41-135">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="33d41-136">**设置恢复间隔**</span><span class="sxs-lookup"><span data-stu-id="33d41-136">**To set the recovery interval**</span></span>  
  
1.  <span data-ttu-id="33d41-137">在对象资源管理器中，右键单击服务器实例，再选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="33d41-137">In Object Explorer, right-click server instance and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="33d41-138">单击 **“数据库设置”** 节点。</span><span class="sxs-lookup"><span data-stu-id="33d41-138">Click the **Database settings** node.</span></span>  
  
3.  <span data-ttu-id="33d41-139">在 **“恢复”** 下的 **“恢复间隔(分钟)”** 框中，键入或选择一个介于 0 到 32767 之间的值，以设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在启动时用于恢复每个数据库花费的最长时间（分钟）。</span><span class="sxs-lookup"><span data-stu-id="33d41-139">Under **Recovery**, in the **Recovery interval (minutes)** box, type or select a value from 0 through 32767 to set the maximum amount of time, in minutes, that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should spend recovering each database at startup.</span></span> <span data-ttu-id="33d41-140">默认值为 0，指示由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]自动配置。</span><span class="sxs-lookup"><span data-stu-id="33d41-140">The default is 0, indicating automatic configuration by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="33d41-141">实际上，这表示每个数据库的恢复时间不超过 1 分钟，对于活动的数据库大约每 1 分钟有一个检查点。</span><span class="sxs-lookup"><span data-stu-id="33d41-141">In practice, this means a recovery time of less than one minute and a checkpoint approximately every one minute for active databases.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="33d41-142">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="33d41-142">Using Transact-SQL</span></span>  
  
#### <a name="to-set-the-recovery-interval"></a><span data-ttu-id="33d41-143">设置恢复间隔</span><span class="sxs-lookup"><span data-stu-id="33d41-143">To set the recovery interval</span></span>  
  
1.  <span data-ttu-id="33d41-144">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="33d41-144">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="33d41-145">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="33d41-145">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="33d41-146">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="33d41-146">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="33d41-147">此示例说明如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将 `recovery interval` 选项的值设置为 `3` 分钟。</span><span class="sxs-lookup"><span data-stu-id="33d41-147">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `recovery interval` option to `3` minutes.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'recovery interval', 3 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="33d41-148">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="33d41-148">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-recovery-internal-option"></a><a name="FollowUp"></a> <span data-ttu-id="33d41-149">跟进：在配置恢复间隔选项之后</span><span class="sxs-lookup"><span data-stu-id="33d41-149">Follow Up: After you configure the recovery internal option</span></span>  
 <span data-ttu-id="33d41-150">该设置将立即生效，无需重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="33d41-150">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33d41-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="33d41-151">See Also</span></span>  
 <span data-ttu-id="33d41-152">[更改数据库的目标恢复时间 (SQL Server)](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="33d41-152">[Change the Target Recovery Time of a Database &#40;SQL Server&#41;](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md) </span></span>  
 <span data-ttu-id="33d41-153">[数据库检查点 (SQL Server)](../../relational-databases/logs/database-checkpoints-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="33d41-153">[Database Checkpoints &#40;SQL Server&#41;](../../relational-databases/logs/database-checkpoints-sql-server.md) </span></span>  
 <span data-ttu-id="33d41-154">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="33d41-154">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="33d41-155">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="33d41-155">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="33d41-156">[show advanced options 服务器配置选项](show-advanced-options-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="33d41-156">[show advanced options Server Configuration Option](show-advanced-options-server-configuration-option.md) </span></span>  
 [<span data-ttu-id="33d41-157">RECONFIGURE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="33d41-157">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
