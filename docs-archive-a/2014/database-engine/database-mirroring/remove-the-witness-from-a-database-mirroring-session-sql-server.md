---
title: 从数据库镜像会话删除见证服务器 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- witness [SQL Server], turning off
- witness [SQL Server], removing
- database mirroring [SQL Server], witness
ms.assetid: f3ce7afc-8936-4d35-80ce-d0f8fbc318d3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d5ede54aca3588a6fcd7cee8759112b606eac752
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690110"
---
# <a name="remove-the-witness-from-a-database-mirroring-session-sql-server"></a><span data-ttu-id="ef391-102">从数据库镜像会话删除见证服务器 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ef391-102">Remove the Witness from a Database Mirroring Session (SQL Server)</span></span>
  <span data-ttu-id="ef391-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中从数据库镜像会话中删除见证服务器。</span><span class="sxs-lookup"><span data-stu-id="ef391-103">This topic describes how to remove a witness from a database mirroring session in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="ef391-104">在数据库镜像会话期间的任何时候，数据库所有者都可以关闭数据库镜像会话的见证服务器。</span><span class="sxs-lookup"><span data-stu-id="ef391-104">At any time during a database mirroring session, the database owner can turn off the witness for a database mirroring session.</span></span>  
  
 <span data-ttu-id="ef391-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="ef391-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ef391-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="ef391-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ef391-107">安全性</span><span class="sxs-lookup"><span data-stu-id="ef391-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ef391-108">**删除见证服务器，使用：**</span><span class="sxs-lookup"><span data-stu-id="ef391-108">**To Replace remove the witness, using:**</span></span>  
  
     [<span data-ttu-id="ef391-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ef391-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ef391-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ef391-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="ef391-111">**跟进：**  [删除见证服务器之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="ef391-111">**Follow Up:**  [After Removing the Witness](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ef391-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="ef391-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ef391-113">Security</span><span class="sxs-lookup"><span data-stu-id="ef391-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ef391-114">权限</span><span class="sxs-lookup"><span data-stu-id="ef391-114">Permissions</span></span>  
 <span data-ttu-id="ef391-115">需要对数据库拥有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="ef391-115">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ef391-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ef391-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-remove-the-witness"></a><span data-ttu-id="ef391-117">删除见证服务器</span><span class="sxs-lookup"><span data-stu-id="ef391-117">To remove the witness</span></span>  
  
1.  <span data-ttu-id="ef391-118">连接至主体服务器实例，在 **对象资源管理器** 窗格中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="ef391-118">Connect to the principal server instance and, in the **Object Explorer** pane, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="ef391-119">展开 **“数据库”**，并选择要删除其见证服务器的数据库。</span><span class="sxs-lookup"><span data-stu-id="ef391-119">Expand **Databases**, and select the database whose witness you want to remove.</span></span>  
  
3.  <span data-ttu-id="ef391-120">右键单击数据库，选择 **“任务”** ，再单击 **“镜像”** 。</span><span class="sxs-lookup"><span data-stu-id="ef391-120">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="ef391-121">这样便可打开 **“数据库属性”** 对话框的 **“镜像”** 页。</span><span class="sxs-lookup"><span data-stu-id="ef391-121">This opens the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="ef391-122">若要删除见证服务器，请从 **“见证服务器”** 字段中删除它的服务器网络地址。</span><span class="sxs-lookup"><span data-stu-id="ef391-122">To remove the witness, delete its server network address from the **Witness** field.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ef391-123">如果从具有自动故障转移功能的高安全性模式切换到高性能模式，则将自动清除“见证服务器”字段。</span><span class="sxs-lookup"><span data-stu-id="ef391-123">If you switch from high-safety mode with automatic failover to high-performance mode, the **Witness** field is automatically cleared.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ef391-124">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ef391-124">Using Transact-SQL</span></span>  
  
#### <a name="to-remove-the-witness"></a><span data-ttu-id="ef391-125">删除见证服务器</span><span class="sxs-lookup"><span data-stu-id="ef391-125">To remove the witness</span></span>  
  
1.  <span data-ttu-id="ef391-126">连接到任一伙伴服务器实例上的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ef391-126">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on either partner server instance.</span></span>  
  
2.  <span data-ttu-id="ef391-127">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="ef391-127">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ef391-128">发出以下语句：</span><span class="sxs-lookup"><span data-stu-id="ef391-128">Issue the following statement:</span></span>  
  
     <span data-ttu-id="ef391-129">[ALTER DATABASE database_name SET WITNESS OFF](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) \*\*</span><span class="sxs-lookup"><span data-stu-id="ef391-129">[ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) *database_name* SET WITNESS OFF</span></span>  
  
     <span data-ttu-id="ef391-130">其中， *database_name* 为镜像数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="ef391-130">where *database_name* is the name of the mirrored database.</span></span>  
  
     <span data-ttu-id="ef391-131">以下示例从 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库中删除见证服务器。</span><span class="sxs-lookup"><span data-stu-id="ef391-131">The following example removes the witness from the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET WITNESS OFF ;  
    ```  
  
##  <a name="follow-up-after-removing-the-witness"></a><a name="FollowUp"></a><span data-ttu-id="ef391-132">跟进：在删除见证服务器之后</span><span class="sxs-lookup"><span data-stu-id="ef391-132">Follow Up: After Removing the Witness</span></span>  
 <span data-ttu-id="ef391-133">关闭见证服务器将根据事务安全设置更改 [运行模式](database-mirroring-operating-modes.md)：</span><span class="sxs-lookup"><span data-stu-id="ef391-133">Turning off the witness changes the [operating mode](database-mirroring-operating-modes.md)in accordance with the transaction-safety setting:</span></span>  
  
-   <span data-ttu-id="ef391-134">如果事务安全设置为 FULL（默认值），则会话将使用不带自动故障转移的高安全同步模式。</span><span class="sxs-lookup"><span data-stu-id="ef391-134">If transaction safety is set to FULL (the default), the session uses high-safety, synchronous mode without automatic failover.</span></span>  
  
-   <span data-ttu-id="ef391-135">如果事务安全设置为 OFF，则会话将异步运行（在高性能模式下），而无需仲裁。</span><span class="sxs-lookup"><span data-stu-id="ef391-135">If transaction safety is set to OFF, the session operates asynchronously (in high-performance mode) without requiring quorum.</span></span> <span data-ttu-id="ef391-136">强烈建议您只要事务安全关闭，就也应当关闭见证服务器。</span><span class="sxs-lookup"><span data-stu-id="ef391-136">Whenever transaction safety is turned off, we strongly recommend also turning the witness off.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="ef391-137">数据库的事务安全性设置记录在每个伙伴的 [sys.database_mirroring](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql) 目录视图中的 **mirroring_safety_level** 和 **mirroring_safety_level_desc** 列内。</span><span class="sxs-lookup"><span data-stu-id="ef391-137">The transaction safety setting of the database is recorded on each partner in the [sys.database_mirroring](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql) catalog view in the **mirroring_safety_level** and **mirroring_safety_level_desc** columns.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="ef391-138">相关任务</span><span class="sxs-lookup"><span data-stu-id="ef391-138">Related Tasks</span></span>  
  
-   [<span data-ttu-id="ef391-139">使用 Windows 身份验证添加数据库镜像见证服务器 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ef391-139">Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="ef391-140">添加或替换数据库镜像见证服务器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="ef391-140">Add or Replace a Database Mirroring Witness &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="ef391-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ef391-141">See Also</span></span>  
 <span data-ttu-id="ef391-142">[ALTER DATABASE 数据库镜像 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="ef391-142">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="ef391-143">[&#40;Transact-sql&#41;更改数据库镜像会话中的事务安全](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="ef391-143">[Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md) </span></span>  
 <span data-ttu-id="ef391-144">[使用 Windows 身份验证添加数据库镜像见证服务器 &#40;Transact-sql&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="ef391-144">[Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md) </span></span>  
 [<span data-ttu-id="ef391-145">数据库镜像见证服务器</span><span class="sxs-lookup"><span data-stu-id="ef391-145">Database Mirroring Witness</span></span>](database-mirroring-witness.md)  
  
  
