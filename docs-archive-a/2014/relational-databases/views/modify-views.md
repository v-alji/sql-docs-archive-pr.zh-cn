---
title: 修改视图 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], renaming
- views [SQL Server], modifying
- modifying views
- renaming views
ms.assetid: 2d3c14dc-43e5-4324-b8fb-f2692d330b16
author: stevestein
ms.author: sstein
ms.openlocfilehash: 10cf9ecc860d8f9b46a06ac679b0f1a8241000bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586557"
---
# <a name="modify-views"></a><span data-ttu-id="e7bfc-102">修改视图</span><span class="sxs-lookup"><span data-stu-id="e7bfc-102">Modify Views</span></span>
  <span data-ttu-id="e7bfc-103">视图定义之后，您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中修改其定义而无需删除并重新创建视图。</span><span class="sxs-lookup"><span data-stu-id="e7bfc-103">After you define a view, you can modify its definition in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] without dropping and re-creating the view by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="e7bfc-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="e7bfc-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e7bfc-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="e7bfc-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e7bfc-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="e7bfc-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="e7bfc-107">安全性</span><span class="sxs-lookup"><span data-stu-id="e7bfc-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e7bfc-108">**修改视图，使用：**</span><span class="sxs-lookup"><span data-stu-id="e7bfc-108">**To modify a view, using:**</span></span>  
  
     [<span data-ttu-id="e7bfc-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e7bfc-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e7bfc-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e7bfc-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e7bfc-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="e7bfc-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="e7bfc-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="e7bfc-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="e7bfc-113">修改视图并不会影响相关对象（例如，存储过程或触发器），除非对视图定义的更改使得该相关对象不再有效。</span><span class="sxs-lookup"><span data-stu-id="e7bfc-113">Modifying a view does not affect any dependent objects, such as stored procedures or triggers, unless the definition of the view changes in such a way that the dependent object is no longer valid.</span></span>  
  
-   <span data-ttu-id="e7bfc-114">如果当前所用的视图使用 ALTER VIEW 来修改，则 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 使用对该视图的排他架构锁。</span><span class="sxs-lookup"><span data-stu-id="e7bfc-114">If a view currently used is modified by using ALTER VIEW, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] takes an exclusive schema lock on the view.</span></span> <span data-ttu-id="e7bfc-115">在授予锁时，如果该视图没有活动用户，则 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 将从过程缓存中删除该视图的所有副本。</span><span class="sxs-lookup"><span data-stu-id="e7bfc-115">When the lock is granted, and there are no active users of the view, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] deletes all copies of the view from the procedure cache.</span></span> <span data-ttu-id="e7bfc-116">引用该视图的现有计划将继续保留在缓存中，但一旦被调用就会重新编译。</span><span class="sxs-lookup"><span data-stu-id="e7bfc-116">Existing plans referencing the view remain in the cache but are recompiled when invoked.</span></span>  
  
-   <span data-ttu-id="e7bfc-117">ALTER VIEW 可应用于索引视图；但是，ALTER VIEW 会无条件地删除视图的所有索引。</span><span class="sxs-lookup"><span data-stu-id="e7bfc-117">ALTER VIEW can be applied to indexed views; however, ALTER VIEW unconditionally drops all indexes on the view.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e7bfc-118">Security</span><span class="sxs-lookup"><span data-stu-id="e7bfc-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e7bfc-119">权限</span><span class="sxs-lookup"><span data-stu-id="e7bfc-119">Permissions</span></span>  
 <span data-ttu-id="e7bfc-120">若要执行 ALTER VIEW，至少需要具有对 OBJECT 的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="e7bfc-120">To execute ALTER VIEW, at a minimum, ALTER permission on OBJECT is required.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e7bfc-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e7bfc-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-view"></a><span data-ttu-id="e7bfc-122">修改视图</span><span class="sxs-lookup"><span data-stu-id="e7bfc-122">To modify a view</span></span>  
  
1.  <span data-ttu-id="e7bfc-123">在 **“对象资源管理器”** 中，单击视图所在的数据库旁边的加号，然后单击 **“视图”** 文件夹旁边的加号。</span><span class="sxs-lookup"><span data-stu-id="e7bfc-123">In **Object Explorer**, click the plus sign next to the database where your view is located and then click the plus sign next to the **Views** folder.</span></span>  
  
2.  <span data-ttu-id="e7bfc-124">右键单击要修改的视图，然后选择“设计”  。</span><span class="sxs-lookup"><span data-stu-id="e7bfc-124">Right-click on the view you wish to modify and select **Design**.</span></span>  
  
3.  <span data-ttu-id="e7bfc-125">在查询设计器的关系图窗格中，通过以下一种或多种方式更改视图：</span><span class="sxs-lookup"><span data-stu-id="e7bfc-125">In the diagram pane of the query designer, make changes to the view in one or more of the following ways:</span></span>  
  
    1.  <span data-ttu-id="e7bfc-126">选中或清除要添加或删除的任何元素的复选框。</span><span class="sxs-lookup"><span data-stu-id="e7bfc-126">Select or clear the check boxes of any elements you wish to add or remove.</span></span>  
  
    2.  <span data-ttu-id="e7bfc-127">在关系图窗格中右键单击，选择“添加表…”，然后从“添加表”对话框选择要添加到视图的其他列   。</span><span class="sxs-lookup"><span data-stu-id="e7bfc-127">Right-click within the diagram pane, select **Add Table...**, and then select the additional columns you want to add to the view from the **Add Table** dialog box.</span></span>  
  
    3.  <span data-ttu-id="e7bfc-128">右键单击要删除的表的标题栏，然后选择“删除”  。</span><span class="sxs-lookup"><span data-stu-id="e7bfc-128">Right-click the title bar of the table you wish to remove and select **Remove**.</span></span>  
  
4.  <span data-ttu-id="e7bfc-129">在“文件”  菜单上，单击“保存”  以保存_视图名称_。</span><span class="sxs-lookup"><span data-stu-id="e7bfc-129">On the **File** menu, click **Save**_view name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e7bfc-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e7bfc-130">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-a-view"></a><span data-ttu-id="e7bfc-131">修改视图</span><span class="sxs-lookup"><span data-stu-id="e7bfc-131">To modify a view</span></span>  
  
1.  <span data-ttu-id="e7bfc-132">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="e7bfc-132">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e7bfc-133">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="e7bfc-133">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e7bfc-134">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="e7bfc-134">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e7bfc-135">此示例首先创建一个视图，然后使用 ALTER VIEW 修改该视图。</span><span class="sxs-lookup"><span data-stu-id="e7bfc-135">The example first creates a view and then modifies the view by using ALTER VIEW.</span></span> <span data-ttu-id="e7bfc-136">将一个 WHERE 子句添加到该视图定义。</span><span class="sxs-lookup"><span data-stu-id="e7bfc-136">A WHERE clause is added to the view definition.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    -- Create a view.  
    CREATE VIEW HumanResources.EmployeeHireDate  
    AS  
    SELECT p.FirstName, p.LastName, e.HireDate  
    FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
    ON e.BusinessEntityID = p.BusinessEntityID ;   
  
    -- Modify the view by adding a WHERE clause to limit the rows returned.  
    ALTER VIEW HumanResources.EmployeeHireDate  
    AS  
    SELECT p.FirstName, p.LastName, e.HireDate  
    FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
    ON e.BusinessEntityID = p.BusinessEntityID  
    WHERE HireDate < CONVERT(DATETIME,'20020101',101) ;   
    GO  
    ```  
  
 <span data-ttu-id="e7bfc-137">有关详细信息，请参阅 [ALTER VIEW (Transact-SQL)](/sql/t-sql/statements/alter-view-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e7bfc-137">For more information, see [ALTER VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-view-transact-sql).</span></span>  
  
  
