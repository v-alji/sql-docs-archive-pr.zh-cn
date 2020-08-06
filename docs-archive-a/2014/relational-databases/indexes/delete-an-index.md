---
title: 删除索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- removing indexes
- deleting indexes
- dropping indexes
- indexes [SQL Server], dropping
- index deletions [SQL Server]
ms.assetid: fd38a0ed-26c4-4c76-9ef7-e0a16147329d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4552ba701782e5790f95f54c0c1c66f82573f1e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693304"
---
# <a name="delete-an-index"></a><span data-ttu-id="9fc2a-102">删除索引</span><span class="sxs-lookup"><span data-stu-id="9fc2a-102">Delete an Index</span></span>
  <span data-ttu-id="9fc2a-103">本主题将说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中删除索引。</span><span class="sxs-lookup"><span data-stu-id="9fc2a-103">This topic describes how to delete (drop) an index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="9fc2a-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="9fc2a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9fc2a-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="9fc2a-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9fc2a-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="9fc2a-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="9fc2a-107">安全性</span><span class="sxs-lookup"><span data-stu-id="9fc2a-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9fc2a-108">**若要删除索引，请使用：**</span><span class="sxs-lookup"><span data-stu-id="9fc2a-108">**To delete an index, using:**</span></span>  
  
     [<span data-ttu-id="9fc2a-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9fc2a-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="9fc2a-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9fc2a-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9fc2a-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="9fc2a-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="9fc2a-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="9fc2a-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="9fc2a-113">不能使用此方法删除作为 PRIMARY KEY 或 UNIQUE 约束的结果而创建的索引。</span><span class="sxs-lookup"><span data-stu-id="9fc2a-113">Indexes created as the result of a PRIMARY KEY or UNIQUE constraint cannot be deleted by using this method.</span></span> <span data-ttu-id="9fc2a-114">而必须删除该约束。</span><span class="sxs-lookup"><span data-stu-id="9fc2a-114">Instead, the constraint must be deleted.</span></span> <span data-ttu-id="9fc2a-115">若要删除该约束和相应的索引，请在 [中使用带有 DROP CONSTRAINT 子句的](/sql/t-sql/statements/alter-table-transact-sql) ALTER TABLE [!INCLUDE[tsql](../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9fc2a-115">To remove the constraint and corresponding index, use [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) with the DROP CONSTRAINT clause in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="9fc2a-116">有关详细信息，请参阅 [Delete Primary Keys](../tables/delete-primary-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="9fc2a-116">For more information, see [Delete Primary Keys](../tables/delete-primary-keys.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9fc2a-117">Security</span><span class="sxs-lookup"><span data-stu-id="9fc2a-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9fc2a-118">权限</span><span class="sxs-lookup"><span data-stu-id="9fc2a-118">Permissions</span></span>  
 <span data-ttu-id="9fc2a-119">要求对表或视图具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="9fc2a-119">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="9fc2a-120">默认情况下，将向 **sysadmin** 固定服务器角色以及 **db_ddladmin** 和 **db_owner** 固定数据库角色授予此权限。</span><span class="sxs-lookup"><span data-stu-id="9fc2a-120">This permission is granted by default to the **sysadmin** fixed server role and the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9fc2a-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9fc2a-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-an-index-by-using-object-explorer"></a><span data-ttu-id="9fc2a-122">通过使用对象资源管理器删除索引</span><span class="sxs-lookup"><span data-stu-id="9fc2a-122">To delete an index by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="9fc2a-123">在“对象资源管理器”中，展开包含您要删除索引的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="9fc2a-123">In Object Explorer, expand the database that contains the table on which you want to delete an index.</span></span>  
  
2.  <span data-ttu-id="9fc2a-124">展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="9fc2a-124">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="9fc2a-125">展开包含您要删除的索引的表。</span><span class="sxs-lookup"><span data-stu-id="9fc2a-125">Expand the table that contains the index you want to delete.</span></span>  
  
4.  <span data-ttu-id="9fc2a-126">展开 **“索引”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="9fc2a-126">Expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="9fc2a-127">右键单击要删除的索引，然后选择“删除”  。</span><span class="sxs-lookup"><span data-stu-id="9fc2a-127">Right-click the index you want to delete and select **Delete**.</span></span>  
  
6.  <span data-ttu-id="9fc2a-128">在 **“删除对象”** 对话框中，确认正确的索引位于 **“要重删除的对象”** 网格中，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="9fc2a-128">In the **Delete Object** dialog box, verify that the correct index is in the **Object to be deleted** grid and click **OK**.</span></span>  
  
#### <a name="to-delete-an-index-using-table-designer"></a><span data-ttu-id="9fc2a-129">使用表设计器删除索引</span><span class="sxs-lookup"><span data-stu-id="9fc2a-129">To delete an index using Table Designer</span></span>  
  
1.  <span data-ttu-id="9fc2a-130">在“对象资源管理器”中，展开包含您要删除索引的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="9fc2a-130">In Object Explorer, expand the database that contains the table on which you want to delete an index.</span></span>  
  
2.  <span data-ttu-id="9fc2a-131">展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="9fc2a-131">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="9fc2a-132">右键单击包含您要删除的索引的表，然后单击“设计”。</span><span class="sxs-lookup"><span data-stu-id="9fc2a-132">Right-click the table that contains the index you want to delete and click Design.</span></span>  
  
4.  <span data-ttu-id="9fc2a-133">在“表设计器”  菜单上，单击“索引/键”  。</span><span class="sxs-lookup"><span data-stu-id="9fc2a-133">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="9fc2a-134">在“索引/键”  对话框中，选择要删除的索引。</span><span class="sxs-lookup"><span data-stu-id="9fc2a-134">In the **Indexes/Keys** dialog box, select the index you want to delete.</span></span>  
  
6.  <span data-ttu-id="9fc2a-135">单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="9fc2a-135">Click **Delete**.</span></span>  
  
7.  <span data-ttu-id="9fc2a-136">单击“关闭”  。</span><span class="sxs-lookup"><span data-stu-id="9fc2a-136">Click **Close**.</span></span>  
  
8.  <span data-ttu-id="9fc2a-137">在“文件”  菜单上，选择“保存”  以保存 _table_name_。</span><span class="sxs-lookup"><span data-stu-id="9fc2a-137">On the **File** menu, select **Save**_table_name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9fc2a-138">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9fc2a-138">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-an-index"></a><span data-ttu-id="9fc2a-139">删除索引</span><span class="sxs-lookup"><span data-stu-id="9fc2a-139">To delete an index</span></span>  
  
1.  <span data-ttu-id="9fc2a-140">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="9fc2a-140">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9fc2a-141">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="9fc2a-141">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9fc2a-142">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="9fc2a-142">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- delete the IX_ProductVendor_BusinessEntityID index  
    -- from the Purchasing.ProductVendor table  
    DROP INDEX IX_ProductVendor_BusinessEntityID   
        ON Purchasing.ProductVendor;  
    GO  
    ```  
  
 <span data-ttu-id="9fc2a-143">有关详细信息，请参阅 [DROP INDEX (Transact-SQL)](/sql/t-sql/statements/drop-index-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="9fc2a-143">For more information, see [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql).</span></span>  
  
  
