---
title: 使用现有层次结构数据填充表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: fd943d84-dbe6-4a05-912b-c88164998d80
author: stevestein
ms.author: sstein
ms.openlocfilehash: 966548b11ad4697abc06de5c5c239a511f80b7af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687747"
---
# <a name="populating-a-table-with-existing-hierarchical-data"></a><span data-ttu-id="ccca6-102">使用现有层次结构数据填充表</span><span class="sxs-lookup"><span data-stu-id="ccca6-102">Populating a Table with Existing Hierarchical Data</span></span>
  <span data-ttu-id="ccca6-103">此任务将创建新表，然后使用 EmployeeDemo\*\*\*\* 表中的数据填充该表。</span><span class="sxs-lookup"><span data-stu-id="ccca6-103">This task creates a new table and populates it with the data in the **EmployeeDemo** table.</span></span> <span data-ttu-id="ccca6-104">此任务包含以下步骤：</span><span class="sxs-lookup"><span data-stu-id="ccca6-104">This task has the following steps:</span></span>  
  
-   <span data-ttu-id="ccca6-105">创建一个包含 `hierarchyid` 列的新表。</span><span class="sxs-lookup"><span data-stu-id="ccca6-105">Create a new table that contains a `hierarchyid` column.</span></span> <span data-ttu-id="ccca6-106">此列可替换现有的 **EmployeeID** 和 **ManagerID** 列。</span><span class="sxs-lookup"><span data-stu-id="ccca6-106">This column could replace the existing **EmployeeID** and **ManagerID** columns.</span></span> <span data-ttu-id="ccca6-107">但是，您将保留这些列。</span><span class="sxs-lookup"><span data-stu-id="ccca6-107">However, you will retain those columns.</span></span> <span data-ttu-id="ccca6-108">这是因为现有应用程序可能会引用这些列，而且它们还有助于您了解传输后的数据。</span><span class="sxs-lookup"><span data-stu-id="ccca6-108">This is because existing applications might refer to those columns, and also to help you understand the data after the transfer.</span></span> <span data-ttu-id="ccca6-109">表定义将 **OrgNode** 指定为主键，这就要求该列包含唯一值。</span><span class="sxs-lookup"><span data-stu-id="ccca6-109">The table definition specifies that **OrgNode** is the primary key, which requires the column to contain unique values.</span></span> <span data-ttu-id="ccca6-110">**OrgNode** 列的聚集索引将使用 **OrgNode** 序列存储日期。</span><span class="sxs-lookup"><span data-stu-id="ccca6-110">The clustered index on the **OrgNode** column will store the date in **OrgNode** sequence.</span></span>  
  
-   <span data-ttu-id="ccca6-111">创建一个用于跟踪直接向每个经理报告的雇员人数的临时表。</span><span class="sxs-lookup"><span data-stu-id="ccca6-111">Create a temporary table that is used to track how many employees report directly to each manager.</span></span>  
  
-   <span data-ttu-id="ccca6-112">使用 **EmployeeDemo** 表中的数据填充新表。</span><span class="sxs-lookup"><span data-stu-id="ccca6-112">Populate the new table by using data from the **EmployeeDemo** table.</span></span>  
  
### <a name="to-create-a-new-table-named-neworg"></a><span data-ttu-id="ccca6-113">创建一个名为 NewOrg 的新表</span><span class="sxs-lookup"><span data-stu-id="ccca6-113">To create a new table named NewOrg</span></span>  
  
-   <span data-ttu-id="ccca6-114">在查询编辑器窗口中，运行下列代码以创建名为 **HumanResources.NewOrg**的新表：</span><span class="sxs-lookup"><span data-stu-id="ccca6-114">In a Query Editor window, run the following code to create a new table named **HumanResources.NewOrg**:</span></span>  
  
    ```  
    CREATE TABLE NewOrg  
    (  
      OrgNode hierarchyid,  
      EmployeeID int,  
      LoginID nvarchar(50),  
      ManagerID int  
    CONSTRAINT PK_NewOrg_OrgNode  
      PRIMARY KEY CLUSTERED (OrgNode)  
    );  
    GO  
    ```  
  
### <a name="to-create-a-temporary-table-named-children"></a><span data-ttu-id="ccca6-115">创建一个名为 #Children 的临时表</span><span class="sxs-lookup"><span data-stu-id="ccca6-115">To create a temporary table named #Children</span></span>  
  
1.  <span data-ttu-id="ccca6-116">创建一个名为 **#Children** 的临时表，其中有一个名为 **Num** 的列，该列将包含每个节点的子级数：</span><span class="sxs-lookup"><span data-stu-id="ccca6-116">Create a temporary table named **#Children** with a column named **Num** that will contain the number of children for each node:</span></span>  
  
    ```  
    CREATE TABLE #Children   
       (  
        EmployeeID int,  
        ManagerID int,  
        Num int  
    );  
    GO  
    ```  
  
2.  <span data-ttu-id="ccca6-117">添加一个索引，该索引将显著提高用于填充 **NewOrg** 表的查询的速度：</span><span class="sxs-lookup"><span data-stu-id="ccca6-117">Add an index that will significantly speed up the query that populates the **NewOrg** table:</span></span>  
  
    ```  
    CREATE CLUSTERED INDEX tmpind ON #Children(ManagerID, EmployeeID);  
    GO  
    ```  
  
### <a name="to-populate-the-neworg-table"></a><span data-ttu-id="ccca6-118">填充 NewOrg 表</span><span class="sxs-lookup"><span data-stu-id="ccca6-118">To populate the NewOrg table</span></span>  
  
1.  <span data-ttu-id="ccca6-119">递归查询禁止使用聚合进行子查询。</span><span class="sxs-lookup"><span data-stu-id="ccca6-119">Recursive queries forbid subqueries with aggregates.</span></span> <span data-ttu-id="ccca6-120">而是使用下列代码填充 **#Children** 表，此代码使用 [ROW_NUMBER()](/sql/t-sql/functions/row-number-transact-sql) 方法填充 **Num** 列：</span><span class="sxs-lookup"><span data-stu-id="ccca6-120">Instead, populate the **#Children** table with the following code, which uses the [ROW_NUMBER()](/sql/t-sql/functions/row-number-transact-sql) method to populate the **Num** column:</span></span>  
  
    ```  
    INSERT #Children (EmployeeID, ManagerID, Num)  
    SELECT EmployeeID, ManagerID,  
      ROW_NUMBER() OVER (PARTITION BY ManagerID ORDER BY ManagerID)   
    FROM EmployeeDemo  
    GO  
  
    ```  
  
2.  <span data-ttu-id="ccca6-121">查看 **#Children** 表。</span><span class="sxs-lookup"><span data-stu-id="ccca6-121">Review the **#Children** table.</span></span> <span data-ttu-id="ccca6-122">请注意 **Num** 列包含每个经理的序号的方式。</span><span class="sxs-lookup"><span data-stu-id="ccca6-122">Note how the **Num** column contains sequential numbers for each manager.</span></span>  
  
    ```  
    SELECT * FROM #Children ORDER BY ManagerID, Num  
    GO  
  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
     `EmployeeID ManagerID Num`  
  
     `---------- --------- ---`  
  
     `1        NULL       1`  
  
     `2         1         1`  
  
     `3         1         2`  
  
     `4         2         1`  
  
     `5         2         2`  
  
     `6         2         3`  
  
     `7         3         1`  
  
     `8         3         2`  
  
     `9         4         1`  
  
     `10        4         2`  
  
3.  <span data-ttu-id="ccca6-123">填充**NewOrg**表。</span><span class="sxs-lookup"><span data-stu-id="ccca6-123">Populate the **NewOrg** table.</span></span> <span data-ttu-id="ccca6-124">使用 GetRoot 和 ToString 方法将**Num**值连接到 `hierarchyid` 格式，然后使用生成的分层值更新**OrgNode**列：</span><span class="sxs-lookup"><span data-stu-id="ccca6-124">Use the GetRoot and ToString methods to concatenate the **Num** values into the `hierarchyid` format, and then update the **OrgNode** column with the resultant hierarchical values:</span></span>  
  
    ```  
    WITH paths(path, EmployeeID)   
    AS (  
    -- This section provides the value for the root of the hierarchy  
    SELECT hierarchyid::GetRoot() AS OrgNode, EmployeeID   
    FROM #Children AS C   
    WHERE ManagerID IS NULL   
  
    UNION ALL   
    -- This section provides values for all nodes except the root  
    SELECT   
    CAST(p.path.ToString() + CAST(C.Num AS varchar(30)) + '/' AS hierarchyid),   
    C.EmployeeID  
    FROM #Children AS C   
    JOIN paths AS p   
       ON C.ManagerID = P.EmployeeID   
    )  
    INSERT NewOrg (OrgNode, O.EmployeeID, O.LoginID, O.ManagerID)  
    SELECT P.path, O.EmployeeID, O.LoginID, O.ManagerID  
    FROM EmployeeDemo AS O   
    JOIN Paths AS P   
       ON O.EmployeeID = P.EmployeeID  
    GO  
  
    ```  
  
4.  <span data-ttu-id="ccca6-125">将 `hierarchyid` 列转换为字符格式会更易于理解。</span><span class="sxs-lookup"><span data-stu-id="ccca6-125">A `hierarchyid` column is more understandable when you convert it to character format.</span></span> <span data-ttu-id="ccca6-126">执行下列代码查看 **NewOrg** 表中的数据，该表包含 **OrgNode** 列的两种表示形式：</span><span class="sxs-lookup"><span data-stu-id="ccca6-126">Review the data in the **NewOrg** table by executing the following code, which contains two representations of the **OrgNode** column:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS LogicalNode, *   
    FROM NewOrg   
    ORDER BY LogicalNode;  
    GO  
  
    ```  
  
     <span data-ttu-id="ccca6-127">**LogicalNode**列将该列转换 `hierarchyid` 为表示层次结构的更易读的文本形式。</span><span class="sxs-lookup"><span data-stu-id="ccca6-127">The **LogicalNode** column converts the `hierarchyid` column into a more readable text form that represents the hierarchy.</span></span> <span data-ttu-id="ccca6-128">在其余的任务中，您将使用 `ToString()` 方法显示 `hierarchyid` 列的逻辑格式。</span><span class="sxs-lookup"><span data-stu-id="ccca6-128">In the remaining tasks, you will use the `ToString()` method to show the logical format of the `hierarchyid` columns.</span></span>  
  
5.  <span data-ttu-id="ccca6-129">删除不再需要的临时表：</span><span class="sxs-lookup"><span data-stu-id="ccca6-129">Drop the temporary table, which is no longer needed:</span></span>  
  
    ```  
    DROP TABLE #Children  
    GO  
    ```  
  
 <span data-ttu-id="ccca6-130">下一个任务将创建索引以支持层次结构。</span><span class="sxs-lookup"><span data-stu-id="ccca6-130">The next task will create indexes to support the hierarchical structure.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="ccca6-131">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="ccca6-131">Next Task in Lesson</span></span>  
 [<span data-ttu-id="ccca6-132">优化 NewOrg 表</span><span class="sxs-lookup"><span data-stu-id="ccca6-132">Optimizing the NewOrg Table</span></span>](lesson-1-3-optimizing-the-neworg-table.md)  
  
  
