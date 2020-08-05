---
title: 配置 remote proc trans 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote proc trans option
- distributed transactions [SQL Server], enforcing
ms.assetid: cfbc6158-ab96-44b4-87eb-ea278c1b0c6b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 54fcaafa51eef33acb1ae8d1e2f36022840b76a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580362"
---
# <a name="configure-the-remote-proc-trans-server-configuration-option"></a><span data-ttu-id="98cd1-102">配置远程过程事务服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="98cd1-102">Configure the remote proc trans Server Configuration Option</span></span>
  <span data-ttu-id="98cd1-103">本主题说明了如何使用 **或** 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中配置 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] remote proc trans [!INCLUDE[tsql](../../includes/tsql-md.md)]服务器配置选项。</span><span class="sxs-lookup"><span data-stu-id="98cd1-103">This topic describes how to configure the **remote proc trans** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="98cd1-104">**remote proc trans** 选项可通过 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分布式事务处理协调器 (MS DTC) 事务，帮助保护服务器到服务器过程的操作。</span><span class="sxs-lookup"><span data-stu-id="98cd1-104">The **remote proc trans** option helps protect the actions of a server-to-server procedure through a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) transaction.</span></span>  
  
 <span data-ttu-id="98cd1-105">将 **remote proc trans** 的值设置为 1 以提供一个由 MS DTC 协调的分布式事务，该事务保护事务的 ACID（原子、一致、隔离和持久）属性。</span><span class="sxs-lookup"><span data-stu-id="98cd1-105">Set the value of **remote proc trans** to 1 to provide an MS DTC-coordinated distributed transaction that protects the ACID (atomic, consistent, isolated, and durable) properties of transactions.</span></span> <span data-ttu-id="98cd1-106">该选项设置为 1 后开始的会话将继承该配置设置并将其作为默认值。</span><span class="sxs-lookup"><span data-stu-id="98cd1-106">Sessions begun after setting this option to 1 inherit the configuration setting as their default.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
 <span data-ttu-id="98cd1-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="98cd1-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="98cd1-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="98cd1-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="98cd1-109">先决条件</span><span class="sxs-lookup"><span data-stu-id="98cd1-109">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="98cd1-110">建议</span><span class="sxs-lookup"><span data-stu-id="98cd1-110">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="98cd1-111">安全性</span><span class="sxs-lookup"><span data-stu-id="98cd1-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="98cd1-112">**若要配置 remote proc trans 选项，请使用：**</span><span class="sxs-lookup"><span data-stu-id="98cd1-112">**To configure the remote proc trans option, using:**</span></span>  
  
     [<span data-ttu-id="98cd1-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="98cd1-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="98cd1-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="98cd1-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="98cd1-115">**跟进：** [在配置远程过程事务选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="98cd1-115">**Follow Up:**  [After you configure the remote proc trans option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="98cd1-116">开始之前</span><span class="sxs-lookup"><span data-stu-id="98cd1-116">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="98cd1-117">先决条件</span><span class="sxs-lookup"><span data-stu-id="98cd1-117">Prerequisites</span></span>  
  
-   <span data-ttu-id="98cd1-118">在设定此值前，必须允许远程服务器连接。</span><span class="sxs-lookup"><span data-stu-id="98cd1-118">Remote server connections must be allowed before this value can be set.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="98cd1-119">建议</span><span class="sxs-lookup"><span data-stu-id="98cd1-119">Recommendations</span></span>  
  
-   <span data-ttu-id="98cd1-120">提供该选项是为了与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 早期版本兼容，以支持使用远程存储过程的应用程序。</span><span class="sxs-lookup"><span data-stu-id="98cd1-120">This option is provided for compatibility with earlier versions of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for applications that use remote stored procedures.</span></span> <span data-ttu-id="98cd1-121">不发出远程存储过程调用，而是使用引用链接服务器的分布式查询，这些服务器是使用 [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)定义的。</span><span class="sxs-lookup"><span data-stu-id="98cd1-121">Instead of issuing remote stored procedure calls, use distributed queries that reference linked servers, which are defined by using [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="98cd1-122">Security</span><span class="sxs-lookup"><span data-stu-id="98cd1-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="98cd1-123">权限</span><span class="sxs-lookup"><span data-stu-id="98cd1-123">Permissions</span></span>  
 <span data-ttu-id="98cd1-124">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="98cd1-124">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="98cd1-125">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="98cd1-125">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="98cd1-126">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="98cd1-126">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="98cd1-127">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="98cd1-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-remote-proc-trans-option"></a><span data-ttu-id="98cd1-128">配置 remote proc trans 选项</span><span class="sxs-lookup"><span data-stu-id="98cd1-128">To configure the remote proc trans option</span></span>  
  
1.  <span data-ttu-id="98cd1-129">在对象资源管理器中，右键单击服务器并选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="98cd1-129">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="98cd1-130">单击 **“连接”** 节点。</span><span class="sxs-lookup"><span data-stu-id="98cd1-130">Click the **Connections** node.</span></span>  
  
3.  <span data-ttu-id="98cd1-131">在 **“远程服务器连接”** 下，选中 **“需要将分布式事务用于服务器到服务器的通信”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="98cd1-131">Under **Remote server connections**, select the **Require Distributed Transactions for server to server communication** check box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="98cd1-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="98cd1-132">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-remote-proc-trans-option"></a><span data-ttu-id="98cd1-133">配置 remote proc trans 选项</span><span class="sxs-lookup"><span data-stu-id="98cd1-133">To configure the remote proc trans option</span></span>  
  
1.  <span data-ttu-id="98cd1-134">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="98cd1-134">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="98cd1-135">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="98cd1-135">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="98cd1-136">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="98cd1-136">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="98cd1-137">此示例说明如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将 `remote proc trans` 选项的值设置为 `1`。</span><span class="sxs-lookup"><span data-stu-id="98cd1-137">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `remote proc trans` option to `1`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'remote proc trans', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 <span data-ttu-id="98cd1-138">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="98cd1-138">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-remote-proc-trans-option"></a><a name="FollowUp"></a> <span data-ttu-id="98cd1-139">跟进：在配置远程过程事务选项之后</span><span class="sxs-lookup"><span data-stu-id="98cd1-139">Follow Up: After you configure the remote proc trans option</span></span>  
 <span data-ttu-id="98cd1-140">该设置将立即生效，无需重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="98cd1-140">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98cd1-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="98cd1-141">See Also</span></span>  
 <span data-ttu-id="98cd1-142">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="98cd1-142">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="98cd1-143">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="98cd1-143">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="98cd1-144">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="98cd1-144">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
