---
title: 配置 priority boost 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- priority boost option
ms.assetid: 765f1e83-dd52-44fb-b0c8-1078f213607b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f42d7d2022e07dcac3039557295dc70e4500583d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580365"
---
# <a name="configure-the-priority-boost-server-configuration-option"></a><span data-ttu-id="750ef-102">配置 priority boost 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="750ef-102">Configure the priority boost Server Configuration Option</span></span>
  <span data-ttu-id="750ef-103">本主题说明如何使用 **或** 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中配置 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] priority boost [!INCLUDE[tsql](../../includes/tsql-md.md)]配置选项。</span><span class="sxs-lookup"><span data-stu-id="750ef-103">This topic describes how to configure the **priority boost** configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="750ef-104">使用 priority boost 选项可以指定 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是否应当以比相同计算机上的其他进程更高的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2008 或 Windows 2008 R2 计划优先级运行。</span><span class="sxs-lookup"><span data-stu-id="750ef-104">Use the **priority boost** option to specify whether [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should run at a higher [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2008 or Windows 2008 R2 scheduling priority than other processes on the same computer.</span></span> <span data-ttu-id="750ef-105">如果将此选项设置为 1， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将以优先级基数 13 在 Windows 2008 或 Windows Server 2008 R2 计划程序中运行。</span><span class="sxs-lookup"><span data-stu-id="750ef-105">If you set this option to 1, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] runs at a priority base of 13 in the Windows 2008 or Windows Server 2008 R2 scheduler.</span></span> <span data-ttu-id="750ef-106">默认值为 0，其优先级基数为 7。</span><span class="sxs-lookup"><span data-stu-id="750ef-106">The default is 0, which is a priority base of 7.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 <span data-ttu-id="750ef-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="750ef-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="750ef-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="750ef-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="750ef-109">限制和局限</span><span class="sxs-lookup"><span data-stu-id="750ef-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="750ef-110">安全性</span><span class="sxs-lookup"><span data-stu-id="750ef-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="750ef-111">**配置 priority boost 选项，使用：**</span><span class="sxs-lookup"><span data-stu-id="750ef-111">**To configure the priority boost option, using:**</span></span>  
  
     [<span data-ttu-id="750ef-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="750ef-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="750ef-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="750ef-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="750ef-114">**跟进：** [在配置优先级提升选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="750ef-114">**Follow Up:**  [After you configure the priority boost option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="750ef-115">开始之前</span><span class="sxs-lookup"><span data-stu-id="750ef-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="750ef-116">限制和局限</span><span class="sxs-lookup"><span data-stu-id="750ef-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="750ef-117">若将优先级提升过高，将会耗尽基本操作系统和网络功能的资源，导致关闭 SQL Server 或在该服务器上使用其他操作系统任务时出现问题。</span><span class="sxs-lookup"><span data-stu-id="750ef-117">Raising the priority too high may drain resources from essential operating system and network functions, resulting in problems shutting down SQL Server or using other operating system tasks on the server.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="750ef-118">Security</span><span class="sxs-lookup"><span data-stu-id="750ef-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="750ef-119">权限</span><span class="sxs-lookup"><span data-stu-id="750ef-119">Permissions</span></span>  
 <span data-ttu-id="750ef-120">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="750ef-120">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="750ef-121">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="750ef-121">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="750ef-122">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="750ef-122">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="750ef-123">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="750ef-123">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-priority-boost-option"></a><span data-ttu-id="750ef-124">配置 priority boost 选项</span><span class="sxs-lookup"><span data-stu-id="750ef-124">To configure the priority boost option</span></span>  
  
1.  <span data-ttu-id="750ef-125">在对象资源管理器中，右键单击服务器并选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="750ef-125">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="750ef-126">单击 **“处理器”** 节点。</span><span class="sxs-lookup"><span data-stu-id="750ef-126">Click the **Processors** node.</span></span>  
  
3.  <span data-ttu-id="750ef-127">在 **“线程”** 下，选中 **“提升 SQL Server 的优先级”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="750ef-127">Under **Threads**, select the **Boost SQL Server priority** check box.</span></span>  
  
4.  <span data-ttu-id="750ef-128">停止并重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="750ef-128">Stop and restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="750ef-129">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="750ef-129">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-priority-boost-option"></a><span data-ttu-id="750ef-130">配置 priority boost 选项</span><span class="sxs-lookup"><span data-stu-id="750ef-130">To configure the priority boost option</span></span>  
  
1.  <span data-ttu-id="750ef-131">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="750ef-131">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="750ef-132">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="750ef-132">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="750ef-133">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="750ef-133">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="750ef-134">此示例说明如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将 `priority boost` 选项的值设置为 `1`。</span><span class="sxs-lookup"><span data-stu-id="750ef-134">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `priority boost` option to `1`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'priority boost', 1 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="750ef-135">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="750ef-135">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-priority-boost-option"></a><a name="FollowUp"></a> <span data-ttu-id="750ef-136">跟进：在配置优先级提升选项之后</span><span class="sxs-lookup"><span data-stu-id="750ef-136">Follow Up: After you configure the priority boost option</span></span>  
 <span data-ttu-id="750ef-137">必须重新启动服务器，设置才会生效。</span><span class="sxs-lookup"><span data-stu-id="750ef-137">The server must be restarted before the setting can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="750ef-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="750ef-138">See Also</span></span>  
 <span data-ttu-id="750ef-139">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="750ef-139">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="750ef-140">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="750ef-140">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="750ef-141">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="750ef-141">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
