---
title: 更新统计信息 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- updating statistics
- statistics [SQL Server], updating
ms.assetid: 4b97c0b4-03ff-4cfb-9c3f-3b33290b7a2c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 28491dda23c2ba9402e91dc051249f5bdcdf28d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590105"
---
# <a name="update-statistics"></a><span data-ttu-id="7aea4-102">更新统计信息</span><span class="sxs-lookup"><span data-stu-id="7aea4-102">Update Statistics</span></span>
  <span data-ttu-id="7aea4-103">您可以通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 更新 [!INCLUDE[tsql](../../includes/tsql-md.md)]中表或索引视图的查询优化统计信息。</span><span class="sxs-lookup"><span data-stu-id="7aea4-103">You can update query optimization statistics on a table or indexed view in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="7aea4-104">默认情况下，查询优化器已根据需要更新统计信息以改进查询计划；但在某些情况下，您可以通过使用 UPDATE STATISTICS 或存储过程 `sp_updatestats` 来比默认更新更频繁地更新统计信息，提高查询性能。</span><span class="sxs-lookup"><span data-stu-id="7aea4-104">By default, the query optimizer already updates statistics as necessary to improve the query plan; in some cases you can improve query performance by using UPDATE STATISTICS or the stored procedure `sp_updatestats` to update statistics more frequently than the default updates.</span></span>  
  
 <span data-ttu-id="7aea4-105">更新统计信息可确保查询使用最新的统计信息进行编译。</span><span class="sxs-lookup"><span data-stu-id="7aea4-105">Updating statistics ensures that queries compile with up-to-date statistics.</span></span> <span data-ttu-id="7aea4-106">不过，更新统计信息会导致查询重新编译。</span><span class="sxs-lookup"><span data-stu-id="7aea4-106">However, updating statistics causes queries to recompile.</span></span> <span data-ttu-id="7aea4-107">我们建议不要太频繁地更新统计信息，因为需要在改进查询计划和重新编译查询所用时间之间权衡性能。</span><span class="sxs-lookup"><span data-stu-id="7aea4-107">We recommend not updating statistics too frequently because there is a performance tradeoff between improving query plans and the time it takes to recompile queries.</span></span> <span data-ttu-id="7aea4-108">具体的折衷方案取决于你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="7aea4-108">The specific tradeoffs depend on your application.</span></span> <span data-ttu-id="7aea4-109">UPDATE STATISTICS 可以使用 tempdb 对行样本进行排序以生成统计信息。</span><span class="sxs-lookup"><span data-stu-id="7aea4-109">UPDATE STATISTICS can use tempdb to sort the sample of rows for building statistics.</span></span>  
  
 <span data-ttu-id="7aea4-110">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="7aea4-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7aea4-111">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="7aea4-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7aea4-112">安全性</span><span class="sxs-lookup"><span data-stu-id="7aea4-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="7aea4-113">**若要更新统计信息对象，请使用：**</span><span class="sxs-lookup"><span data-stu-id="7aea4-113">**To update a statistics object, using:**</span></span>  
  
     [<span data-ttu-id="7aea4-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7aea4-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="7aea4-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7aea4-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7aea4-116">开始之前</span><span class="sxs-lookup"><span data-stu-id="7aea4-116">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7aea4-117">Security</span><span class="sxs-lookup"><span data-stu-id="7aea4-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7aea4-118">权限</span><span class="sxs-lookup"><span data-stu-id="7aea4-118">Permissions</span></span>  
 <span data-ttu-id="7aea4-119">如果使用 UPDATE STATISTICS 或通过 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]进行更改，则要求对表或视图具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="7aea4-119">If using UPDATE STATISTICS or making changes through [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], requires ALTER permission on the table or view.</span></span> <span data-ttu-id="7aea4-120">如果使用 `sp_updatestats`，则要求具有 **sysadmin** 固定服务器角色的成员身份或数据库 (**dbo**) 的所有者身份。</span><span class="sxs-lookup"><span data-stu-id="7aea4-120">If using `sp_updatestats`, requires membership in the **sysadmin** fixed server role, or ownership of the database (**dbo**).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7aea4-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7aea4-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-update-a-statistics-object"></a><span data-ttu-id="7aea4-122">更新统计信息对象</span><span class="sxs-lookup"><span data-stu-id="7aea4-122">To update a statistics object</span></span>  
  
1.  <span data-ttu-id="7aea4-123">在 **“对象资源管理器”** 中，单击加号以便展开要更新统计信息的数据库。</span><span class="sxs-lookup"><span data-stu-id="7aea4-123">In **Object Explorer**, click the plus sign to expand the database in which you want to update the statistic.</span></span>  
  
2.  <span data-ttu-id="7aea4-124">单击加号以便展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="7aea4-124">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="7aea4-125">单击加号以便展开要更新统计信息的表。</span><span class="sxs-lookup"><span data-stu-id="7aea4-125">Click the plus sign to expand the table in which you want to update the statistic.</span></span>  
  
4.  <span data-ttu-id="7aea4-126">单击加号以便展开 **“统计信息”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="7aea4-126">Click the plus sign to expand the **Statistics** folder.</span></span>  
  
5.  <span data-ttu-id="7aea4-127">右键单击要更新的统计信息对象，然后选择“属性”。</span><span class="sxs-lookup"><span data-stu-id="7aea4-127">Right-click the statistics object you wish to update and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="7aea4-128">在 "**统计信息属性-**_statistics_name_ " 对话框中，选中 "**更新这些列的统计信息**" 复选框，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="7aea4-128">In the **Statistics Properties -**_statistics_name_ dialog box, select the **Update statistics for these columns** check box and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7aea4-129">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7aea4-129">Using Transact-SQL</span></span>  
  
#### <a name="to-update-a-specific-statistics-object"></a><span data-ttu-id="7aea4-130">更新特定的统计信息对象</span><span class="sxs-lookup"><span data-stu-id="7aea4-130">To update a specific statistics object</span></span>  
  
1.  <span data-ttu-id="7aea4-131">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="7aea4-131">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7aea4-132">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="7aea4-132">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7aea4-133">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="7aea4-133">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- The following example updates the statistics for the AK_SalesOrderDetail_rowguid index of the SalesOrderDetail table.   
    UPDATE STATISTICS Sales.SalesOrderDetail AK_SalesOrderDetail_rowguid;   
    GO  
    ```  
  
#### <a name="to-update-all-statistics-in-a-table"></a><span data-ttu-id="7aea4-134">更新表中的所有统计信息</span><span class="sxs-lookup"><span data-stu-id="7aea4-134">To update all statistics in a table</span></span>  
  
1.  <span data-ttu-id="7aea4-135">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="7aea4-135">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7aea4-136">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="7aea4-136">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7aea4-137">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="7aea4-137">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- The following example updates the statistics for all indexes on the SalesOrderDetail table.   
    UPDATE STATISTICS Sales.SalesOrderDetail;   
    GO  
    ```  
  
 <span data-ttu-id="7aea4-138">有关详细信息，请参阅 [更新统计信息 (Transact-SQL)](/sql/t-sql/statements/update-statistics-transact-sql)创建的数据库维护计划。</span><span class="sxs-lookup"><span data-stu-id="7aea4-138">For more information, see [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql).</span></span>  
  
#### <a name="to-update-all-statistics-in-a-database"></a><span data-ttu-id="7aea4-139">更新数据库中的所有统计信息</span><span class="sxs-lookup"><span data-stu-id="7aea4-139">To update all statistics in a database</span></span>  
  
1.  <span data-ttu-id="7aea4-140">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="7aea4-140">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7aea4-141">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="7aea4-141">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7aea4-142">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="7aea4-142">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- The following example updates the statistics for all tables in the database.   
    EXEC sp_updatestats;  
    ```  
  
 <span data-ttu-id="7aea4-143">有关详细信息，请参阅 [sp_updatestats (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7aea4-143">For more information, see [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql).</span></span>  
  
  
