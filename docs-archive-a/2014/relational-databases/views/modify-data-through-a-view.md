---
title: 通过视图修改数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- data modifications [SQL Server], views
- views [SQL Server], modifying data through
- modifying data [SQL Server], views
ms.assetid: 410e2812-4ebe-48b2-b95f-c7784f1c4336
author: stevestein
ms.author: sstein
ms.openlocfilehash: df1eb4a33d1d10e63363e52760dad805b20c0a8f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577451"
---
# <a name="modify-data-through-a-view"></a><span data-ttu-id="3b8d0-102">通过视图修改数据</span><span class="sxs-lookup"><span data-stu-id="3b8d0-102">Modify Data Through a View</span></span>
  <span data-ttu-id="3b8d0-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中修改基础基表的数据。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-103">You can modify the data of an underlying base table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="3b8d0-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="3b8d0-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3b8d0-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="3b8d0-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3b8d0-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="3b8d0-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="3b8d0-107">安全性</span><span class="sxs-lookup"><span data-stu-id="3b8d0-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="3b8d0-108">**通过视图修改表数据，使用：**</span><span class="sxs-lookup"><span data-stu-id="3b8d0-108">**To modify table data through a view, using:**</span></span>  
  
     [<span data-ttu-id="3b8d0-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3b8d0-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="3b8d0-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3b8d0-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3b8d0-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="3b8d0-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="3b8d0-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="3b8d0-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="3b8d0-113">请参阅 [CREATE VIEW (Transact-SQL)](/sql/t-sql/statements/create-view-transact-sql) 中的“可更新的视图”一节。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-113">See the section 'Updatable Views' in [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3b8d0-114">Security</span><span class="sxs-lookup"><span data-stu-id="3b8d0-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3b8d0-115">权限</span><span class="sxs-lookup"><span data-stu-id="3b8d0-115">Permissions</span></span>  
 <span data-ttu-id="3b8d0-116">需要对目标表的 UPDATE、INSERT 或 DELETE 权限（取决于执行的操作）。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-116">Requires UPDATE, INSERT, or DELETE permissions on the target table, depending on the action being performed.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3b8d0-117">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3b8d0-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-table-data-through-a-view"></a><span data-ttu-id="3b8d0-118">通过视图修改表数据</span><span class="sxs-lookup"><span data-stu-id="3b8d0-118">To modify table data through a view</span></span>  
  
1.  <span data-ttu-id="3b8d0-119">在 **“对象资源管理器”** 中，展开包含视图的数据库，然后展开 **“视图”** 。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-119">In **Object Explorer**, expand the database that contains the view and then expand **Views**.</span></span>  
  
2.  <span data-ttu-id="3b8d0-120">右键单击该视图，然后选择“编辑前 200 行”  。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-120">Right-click the view and select **Edit Top 200 Rows**.</span></span>  
  
3.  <span data-ttu-id="3b8d0-121">可能需要在 **SQL** 窗格中修改 SELECT 语句以返回要修改的行。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-121">You may need to modify the SELECT statement in the **SQL** pane to return the rows to be modified.</span></span>  
  
4.  <span data-ttu-id="3b8d0-122">在 **“结果”** 窗格中，找到要更改或删除的行。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-122">In the **Results** pane, locate the row to be changed or deleted.</span></span> <span data-ttu-id="3b8d0-123">若要删除行，请右键单击该行，然后选择“删除”  。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-123">To delete the row, right-click the row and select **Delete**.</span></span> <span data-ttu-id="3b8d0-124">若要更改一个或多个列中的数据，请修改列中的数据。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-124">To change data in one or more columns, modify the data in the column.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="3b8d0-125">如果视图引用多个基表，则不能删除行。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-125">You cannot delete a row if the view references more than one base table.</span></span> <span data-ttu-id="3b8d0-126">只能更新属于单个基表的列。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-126">You can only update columns that belong to a single base table.</span></span>  
  
5.  <span data-ttu-id="3b8d0-127">若要插入行，请向下滚动到行的结尾并插入新值。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-127">To insert a row, scroll down to the end of the rows and insert the new values.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="3b8d0-128">如果视图引用多个基表，则不能插入行。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-128">You cannot insert a row if the view references more than one base table.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3b8d0-129">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3b8d0-129">Using Transact-SQL</span></span>  
  
#### <a name="to-update-table-data-through-a-view"></a><span data-ttu-id="3b8d0-130">通过视图更新表数据</span><span class="sxs-lookup"><span data-stu-id="3b8d0-130">To update table data through a view</span></span>  
  
1.  <span data-ttu-id="3b8d0-131">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-131">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3b8d0-132">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-132">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3b8d0-133">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-133">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="3b8d0-134">此示例通过引用视图 `StartDate` 中的列为特定雇员更改 `EndDate` 和 `HumanResources.vEmployeeDepartmentHistory`列中的值。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-134">This example changes the value in the `StartDate` and `EndDate` columns for a specific employee by referencing columns in the view `HumanResources.vEmployeeDepartmentHistory`.</span></span> <span data-ttu-id="3b8d0-135">此视图从两个表返回值。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-135">This view returns values from two tables.</span></span> <span data-ttu-id="3b8d0-136">此语句会成功，因为修改的列都来自一个基表。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-136">This statement succeeds because the columns being modified are from only one of the base tables.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;   
    GO  
    UPDATE HumanResources.vEmployeeDepartmentHistory  
    SET StartDate = '20110203', EndDate = GETDATE()   
    WHERE LastName = N'Smith' AND FirstName = 'Samantha';   
    GO  
    ```  
  
 <span data-ttu-id="3b8d0-137">有关详细信息，请参阅 [UPDATE (Transact-SQL)](/sql/t-sql/queries/update-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-137">For more information, see [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql).</span></span>  
  
#### <a name="to-insert-table-data-through-a-view"></a><span data-ttu-id="3b8d0-138">通过视图插入表数据</span><span class="sxs-lookup"><span data-stu-id="3b8d0-138">To insert table data through a view</span></span>  
  
1.  <span data-ttu-id="3b8d0-139">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-139">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3b8d0-140">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-140">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3b8d0-141">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-141">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="3b8d0-142">此示例通过指定视图 `HumanResouces.Department` 中的相关列，将一个新行插入到基表 `HumanResources.vEmployeeDepartmentHistory`。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-142">The example inserts a new row into the base table `HumanResouces.Department` by specifying the relevant columns from the view `HumanResources.vEmployeeDepartmentHistory`.</span></span> <span data-ttu-id="3b8d0-143">该语句会成功，因为只指定了一个基表中的列，基表中的其他列具有默认值。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-143">The statement succeeds because only columns from a single base table are specified and the other columns in the base table have default values.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    INSERT INTO HumanResources.vEmployeeDepartmentHistory (Department, GroupName)   
    VALUES ('MyDepartment', 'MyGroup');   
    GO  
    ```  
  
 <span data-ttu-id="3b8d0-144">有关详细信息，请参阅 [INSERT (Transact-SQL)](/sql/t-sql/statements/insert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3b8d0-144">For more information, see [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql).</span></span>  
  
  
