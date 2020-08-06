---
title: 查看数据库快照 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- database snapshots [SQL Server], viewing
- displaying database snapshots
- viewing database snapshots
ms.assetid: 123f19b2-0850-4033-8507-59ebdfb368ee
author: stevestein
ms.author: sstein
ms.openlocfilehash: 92c5c557656e87be562e9d5477f14f66b2c39e7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693375"
---
# <a name="view-a-database-snapshot-sql-server"></a><span data-ttu-id="f5aa7-102">查看数据库快照 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f5aa7-102">View a Database Snapshot (SQL Server)</span></span>
  <span data-ttu-id="f5aa7-103">本主题说明如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 查看 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]数据库快照。</span><span class="sxs-lookup"><span data-stu-id="f5aa7-103">This topic explains how to view a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database snapshot using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f5aa7-104">若要创建、恢复到或删除数据库快照，必须使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f5aa7-104">To create, revert to, or delete a database snapshot, you must use [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="f5aa7-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="f5aa7-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f5aa7-106">**查看数据库快照，使用：**</span><span class="sxs-lookup"><span data-stu-id="f5aa7-106">**To view a database snapshot, using:**</span></span>  
  
     [<span data-ttu-id="f5aa7-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f5aa7-107">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f5aa7-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f5aa7-108">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f5aa7-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f5aa7-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="f5aa7-110">**查看数据库快照**</span><span class="sxs-lookup"><span data-stu-id="f5aa7-110">**To view a database snapshot**</span></span>  
  
1.  <span data-ttu-id="f5aa7-111">在对象资源管理器中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="f5aa7-111">In Object Explorer, connect to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="f5aa7-112">展开 **“数据库”** 。</span><span class="sxs-lookup"><span data-stu-id="f5aa7-112">Expand **Databases.**</span></span>  
  
3.  <span data-ttu-id="f5aa7-113">展开 **“数据库快照”** ，然后选择要查看的快照。</span><span class="sxs-lookup"><span data-stu-id="f5aa7-113">Expand **Database Snapshots**, and select the snapshot you want to view.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f5aa7-114">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f5aa7-114">Using Transact-SQL</span></span>  
 <span data-ttu-id="f5aa7-115">**查看数据库快照**</span><span class="sxs-lookup"><span data-stu-id="f5aa7-115">**To view a database snapshot**</span></span>  
  
1.  <span data-ttu-id="f5aa7-116">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f5aa7-116">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f5aa7-117">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="f5aa7-117">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f5aa7-118">若要列出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的数据库快照，对于非 NULL 值请查询 **sys.databases** 目录视图的 [source_database_id](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 列。</span><span class="sxs-lookup"><span data-stu-id="f5aa7-118">To list the database snapshots of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], query the **source_database_id** column of the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view for non-NULL values.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f5aa7-119">相关任务</span><span class="sxs-lookup"><span data-stu-id="f5aa7-119">Related Tasks</span></span>  
  
-   [<span data-ttu-id="f5aa7-120">创建数据库快照 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f5aa7-120">Create a Database Snapshot &#40;Transact-SQL&#41;</span></span>](create-a-database-snapshot-transact-sql.md)  
  
-   [<span data-ttu-id="f5aa7-121">将数据库恢复到数据库快照</span><span class="sxs-lookup"><span data-stu-id="f5aa7-121">Revert a Database to a Database Snapshot</span></span>](revert-a-database-to-a-database-snapshot.md)  
  
-   [<span data-ttu-id="f5aa7-122">删除数据库快照 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f5aa7-122">Drop a Database Snapshot &#40;Transact-SQL&#41;</span></span>](drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="f5aa7-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f5aa7-123">See Also</span></span>  
 [<span data-ttu-id="f5aa7-124">数据库快照 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f5aa7-124">Database Snapshots &#40;SQL Server&#41;</span></span>](database-snapshots-sql-server.md)  
  
  
