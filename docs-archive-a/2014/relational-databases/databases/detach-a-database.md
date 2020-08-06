---
title: 分离数据库 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.detachdatabase.f1
helpviewer_keywords:
- database detaching [SQL Server]
- detaching databases [SQL Server]
ms.assetid: f63d4107-13e4-4bfe-922d-5e4f712e472d
author: stevestein
ms.author: sstein
ms.openlocfilehash: b8acc809b881012d18f78995bb8e521337fb02ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591367"
---
# <a name="detach-a-database"></a><span data-ttu-id="76b94-102">分离数据库</span><span class="sxs-lookup"><span data-stu-id="76b94-102">Detach a Database</span></span>
  <span data-ttu-id="76b94-103">本主题介绍如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中分离数据库。</span><span class="sxs-lookup"><span data-stu-id="76b94-103">This topic describes how to detach a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="76b94-104">分离的文件将会予以保留，并且可以使用带有 FOR ATTACH 或 FOR ATTACH_REBUILD_LOG 选项的 CREATE DATABASE 重新附加它们。</span><span class="sxs-lookup"><span data-stu-id="76b94-104">The detached files remain and can be reattached by using CREATE DATABASE with the FOR ATTACH or FOR ATTACH_REBUILD_LOG option.</span></span> <span data-ttu-id="76b94-105">这些文件可以移动并附加到其他服务器上。</span><span class="sxs-lookup"><span data-stu-id="76b94-105">The files can be moved to another server and attached there.</span></span>  
  
 <span data-ttu-id="76b94-106">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="76b94-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="76b94-107">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="76b94-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="76b94-108">限制和局限</span><span class="sxs-lookup"><span data-stu-id="76b94-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="76b94-109">安全性</span><span class="sxs-lookup"><span data-stu-id="76b94-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="76b94-110">**若要分离数据库，可使用：**</span><span class="sxs-lookup"><span data-stu-id="76b94-110">**To detach a database, using:**</span></span>  
  
     [<span data-ttu-id="76b94-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="76b94-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="76b94-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="76b94-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="76b94-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="76b94-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="76b94-114">限制和局限</span><span class="sxs-lookup"><span data-stu-id="76b94-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="76b94-115">有关限制和局限的列表，请参阅 [数据库分离和附加 (SQL Server)](database-detach-and-attach-sql-server.md)中分离数据库。</span><span class="sxs-lookup"><span data-stu-id="76b94-115">For a list of limitations and restrictions, see [Database Detach and Attach &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="76b94-116">Security</span><span class="sxs-lookup"><span data-stu-id="76b94-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="76b94-117">权限</span><span class="sxs-lookup"><span data-stu-id="76b94-117">Permissions</span></span>  
 <span data-ttu-id="76b94-118">要求具有 db_owner 固定数据库角色中的成员资格。</span><span class="sxs-lookup"><span data-stu-id="76b94-118">Requires membership in the db_owner fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="76b94-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="76b94-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-detach-a-database"></a><span data-ttu-id="76b94-120">分离数据库</span><span class="sxs-lookup"><span data-stu-id="76b94-120">To detach a database</span></span>  
  
1.  <span data-ttu-id="76b94-121">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 对象资源管理器中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="76b94-121">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer, connect to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand the instance.</span></span>  
  
2.  <span data-ttu-id="76b94-122">展开 **“数据库”** ，并选择要分离的用户数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="76b94-122">Expand **Databases**, and select the name of the user database you want to detach.</span></span>  
  
3.  <span data-ttu-id="76b94-123">右键单击数据库名称，指向“任务”，再单击“分离”。</span><span class="sxs-lookup"><span data-stu-id="76b94-123">Right-click the database name, point to **Tasks**, and then click **Detach**.</span></span> <span data-ttu-id="76b94-124">将出现 **“分离数据库”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="76b94-124">The **Detach Database** dialog box appears.</span></span>  
  
     <span data-ttu-id="76b94-125">**要分离的数据库**</span><span class="sxs-lookup"><span data-stu-id="76b94-125">**Databases to detach**</span></span>  
     <span data-ttu-id="76b94-126">列出要分离的数据库。</span><span class="sxs-lookup"><span data-stu-id="76b94-126">Lists the databases to detach.</span></span>  
  
     <span data-ttu-id="76b94-127">**Database Name**</span><span class="sxs-lookup"><span data-stu-id="76b94-127">**Database Name**</span></span>  
     <span data-ttu-id="76b94-128">显示要分离的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="76b94-128">Displays the name of the database to be detached.</span></span>  
  
     <span data-ttu-id="76b94-129">**删除连接**</span><span class="sxs-lookup"><span data-stu-id="76b94-129">**Drop Connections**</span></span>  
     <span data-ttu-id="76b94-130">断开与指定数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="76b94-130">Disconnect connections to the specified database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="76b94-131">不能分离连接为活动状态的数据库。</span><span class="sxs-lookup"><span data-stu-id="76b94-131">You cannot detach a database with active connections.</span></span>  
  
     <span data-ttu-id="76b94-132">**更新统计信息**</span><span class="sxs-lookup"><span data-stu-id="76b94-132">**Update Statistics**</span></span>  
     <span data-ttu-id="76b94-133">默认情况下，分离操作将在分离数据库时保留过期的优化统计信息；若要更新现有的优化统计信息，请单击此复选框。</span><span class="sxs-lookup"><span data-stu-id="76b94-133">By default, the detach operation retains any out-of-date optimization statistics when detaching the database; to update the existing optimization statistics, click this check box.</span></span>  
  
     <span data-ttu-id="76b94-134">**保留全文目录**</span><span class="sxs-lookup"><span data-stu-id="76b94-134">**Keep Full-Text Catalogs**</span></span>  
     <span data-ttu-id="76b94-135">默认情况下，分离操作保留所有与数据库关联的全文目录。</span><span class="sxs-lookup"><span data-stu-id="76b94-135">By default, the detach operation keeps any full-text catalogs that are associated with the database.</span></span> <span data-ttu-id="76b94-136">若要删除全文目录，请清除 **“保留全文目录”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="76b94-136">To remove them, clear the **Keep Full-Text Catalogs** check box.</span></span> <span data-ttu-id="76b94-137">只有从 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]升级数据库时，才会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="76b94-137">This option appears only when you are upgrading a database from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
     <span data-ttu-id="76b94-138">**Status**</span><span class="sxs-lookup"><span data-stu-id="76b94-138">**Status**</span></span>  
     <span data-ttu-id="76b94-139">显示以下状态之一：“就绪”或“未就绪” 。</span><span class="sxs-lookup"><span data-stu-id="76b94-139">Displays one of the following states: **Ready** or **Not ready**.</span></span>  
  
     <span data-ttu-id="76b94-140">**消息**</span><span class="sxs-lookup"><span data-stu-id="76b94-140">**Message**</span></span>  
     <span data-ttu-id="76b94-141">**“消息”** 列可显示关于数据库的如下信息：</span><span class="sxs-lookup"><span data-stu-id="76b94-141">The **Message** column may display information about the database, as follows:</span></span>  
  
    -   <span data-ttu-id="76b94-142">当数据库进行了复制操作，则 **“状态”** 为 **“未就绪”** ， **“消息”** 列将显示 **“已复制数据库”** 。</span><span class="sxs-lookup"><span data-stu-id="76b94-142">When a database is involved with replication, the **Status** is **Not ready** and the **Message** column displays **Database replicated**.</span></span>  
  
    -   <span data-ttu-id="76b94-143">如果数据库有一个或多个活动连接，则“状态”为“未就绪”，“消息”列显示“<number_of_active_connections> 个活动连接”，例如  ：“1 个活动连接”。</span><span class="sxs-lookup"><span data-stu-id="76b94-143">When a database has one or more active connections, the **Status** is **Not ready** and the **Message** column displays _<number_of_active_connections>_**Active connection(s)** - for example: **1 Active connection(s)**.</span></span> <span data-ttu-id="76b94-144">在分离数据库之前，需要通过选择 **“删除连接”** 断开所有活动连接。</span><span class="sxs-lookup"><span data-stu-id="76b94-144">Before you can detach the database, you need to disconnect any active connections by selecting **Drop Connections**.</span></span>  
  
     <span data-ttu-id="76b94-145">若要获取有关消息的详细信息，请单击相应的超链接文本打开活动监视器。</span><span class="sxs-lookup"><span data-stu-id="76b94-145">To obtain more information about a message, click the hyperlinked text to open Activity Monitor.</span></span>  
  
4.  <span data-ttu-id="76b94-146">分离数据库准备就绪后，请单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="76b94-146">When you are ready to detach the database, click **OK**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="76b94-147">新分离的数据库将一直显示在对象资源管理器的 **“数据库”** 节点中，直到刷新该视图。</span><span class="sxs-lookup"><span data-stu-id="76b94-147">The newly detached database will remain visible in the **Databases** node of Object Explorer until the view is refreshed.</span></span> <span data-ttu-id="76b94-148">可以随时刷新视图：单击“对象资源管理器”窗格，然后从菜单栏依次选择“视图”和“刷新” 。</span><span class="sxs-lookup"><span data-stu-id="76b94-148">You can refresh the view at any time: Click in the Object Explorer pane, and from the menu bar select **View** and then **Refresh**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="76b94-149">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="76b94-149">Using Transact-SQL</span></span>  
  
#### <a name="to-detach-a-database"></a><span data-ttu-id="76b94-150">分离数据库</span><span class="sxs-lookup"><span data-stu-id="76b94-150">To detach a database</span></span>  
  
1.  <span data-ttu-id="76b94-151">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="76b94-151">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="76b94-152">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="76b94-152">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="76b94-153">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="76b94-153">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="76b94-154">此示例将分离 AdventureWorks2012 数据库，同时将 skipchecks 设置为 true。</span><span class="sxs-lookup"><span data-stu-id="76b94-154">This example detaches the AdventureWorks2012 database with skipchecks set to true.</span></span>  
  
```  
EXEC sp_detach_db 'AdventureWorks2012', 'true';  
```  
  
## <a name="see-also"></a><span data-ttu-id="76b94-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="76b94-155">See Also</span></span>  
 <span data-ttu-id="76b94-156">[数据库分离和附加 (SQL Server)](database-detach-and-attach-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="76b94-156">[Database Detach and Attach &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md) </span></span>  
 [<span data-ttu-id="76b94-157">sp_detach_db (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="76b94-157">sp_detach_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql)  
  
  
