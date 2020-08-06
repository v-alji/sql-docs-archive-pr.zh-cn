---
title: 优化 NewOrg 表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- optimizing tables
ms.assetid: 89ff6d37-94c0-4773-8be9-dde943fff023
author: stevestein
ms.author: sstein
ms.openlocfilehash: 39c09a3a73051e7a61f3a62a125232d83d1570c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576589"
---
# <a name="optimizing-the-neworg-table"></a><span data-ttu-id="6ef96-102">优化 NewOrg 表</span><span class="sxs-lookup"><span data-stu-id="6ef96-102">Optimizing the NewOrg Table</span></span>
  <span data-ttu-id="6ef96-103">在使用[现有层次结构数据填充表](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)任务中创建的**NewOrd**表包含所有雇员信息，并使用数据类型表示层次结构 `hierarchyid` 。</span><span class="sxs-lookup"><span data-stu-id="6ef96-103">The **NewOrd** table that you created in the [Populating a Table with Existing Hierarchical Data](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md) task contains all the employee information, and represents the hierarchical structure by using a `hierarchyid` data type.</span></span> <span data-ttu-id="6ef96-104">此任务添加了新的索引，以便支持对 `hierarchyid` 列的搜索。</span><span class="sxs-lookup"><span data-stu-id="6ef96-104">This task adds new indexes to support searches on the `hierarchyid` column.</span></span>  
  
## <a name="clustered-index"></a><span data-ttu-id="6ef96-105">聚集索引</span><span class="sxs-lookup"><span data-stu-id="6ef96-105">Clustered Index</span></span>  
 <span data-ttu-id="6ef96-106">`hierarchyid` **OrgNode**)  (列是**NewOrg**表的主键。</span><span class="sxs-lookup"><span data-stu-id="6ef96-106">The `hierarchyid` column (**OrgNode**) is the primary key for the **NewOrg** table.</span></span> <span data-ttu-id="6ef96-107">此表创建时，其内包含了一个名为 **PK_NewOrg_OrgNode** 的聚集索引，用于强制实现“OrgNode”\*\*\*\* 列的唯一性。</span><span class="sxs-lookup"><span data-stu-id="6ef96-107">When the table was created, it contained a clustered index named **PK_NewOrg_OrgNode** to enforce the uniqueness of the **OrgNode** column.</span></span> <span data-ttu-id="6ef96-108">此聚集索引还支持对表进行深度优先搜索。</span><span class="sxs-lookup"><span data-stu-id="6ef96-108">This clustered index also supports a depth-first search of the table.</span></span>  
  
## <a name="nonclustered-index"></a><span data-ttu-id="6ef96-109">非聚集索引</span><span class="sxs-lookup"><span data-stu-id="6ef96-109">Nonclustered Index</span></span>  
 <span data-ttu-id="6ef96-110">此步骤将创建两个非聚集索引，用于支持典型搜索。</span><span class="sxs-lookup"><span data-stu-id="6ef96-110">This step creates two nonclustered indexes to support typical searches.</span></span>  
  
#### <a name="to-index-the-neworg-table-for-efficient-searches"></a><span data-ttu-id="6ef96-111">为 NewOrg 表创建索引以提高搜索效率</span><span class="sxs-lookup"><span data-stu-id="6ef96-111">To index the NewOrg table for efficient searches</span></span>  
  
1.  <span data-ttu-id="6ef96-112">若要改善在层次结构中同一级别的查询，可以使用 [GetLevel](/sql/t-sql/data-types/getlevel-database-engine) 方法创建一个包含此层次结构中的此级别的计算列。</span><span class="sxs-lookup"><span data-stu-id="6ef96-112">To help queries at the same level in the hierarchy, use the [GetLevel](/sql/t-sql/data-types/getlevel-database-engine) method to create a computed column that contains the level in the hierarchy.</span></span> <span data-ttu-id="6ef96-113">然后，对此级别和 `Hierarchyid` 创建一个组合索引。</span><span class="sxs-lookup"><span data-stu-id="6ef96-113">Then, create a composite index on the level and the `Hierarchyid`.</span></span> <span data-ttu-id="6ef96-114">运行下列代码以创建计算列和广度优先索引：</span><span class="sxs-lookup"><span data-stu-id="6ef96-114">Run the following code to create the computed column and the breadth-first index:</span></span>  
  
    ```  
    ALTER TABLE NewOrg   
       ADD H_Level AS OrgNode.GetLevel() ;  
    CREATE UNIQUE INDEX EmpBFInd   
       ON NewOrg(H_Level, OrgNode) ;  
    GO  
    ```  
  
2.  <span data-ttu-id="6ef96-115">对“EmployeeID”\*\*\*\* 列创建一个唯一索引。</span><span class="sxs-lookup"><span data-stu-id="6ef96-115">Create a unique index on the **EmployeeID** column.</span></span> <span data-ttu-id="6ef96-116">即采用传统方式通过 **EmployeeID** 号单独查找一个雇员。</span><span class="sxs-lookup"><span data-stu-id="6ef96-116">This is the traditional singleton lookup of a single employee by **EmployeeID** number.</span></span> <span data-ttu-id="6ef96-117">运行下列代码以便对 **EmployeeID**创建索引：</span><span class="sxs-lookup"><span data-stu-id="6ef96-117">Run the following code to create an index on **EmployeeID**:</span></span>  
  
    ```  
    CREATE UNIQUE INDEX EmpIDs_unq ON NewOrg(EmployeeID) ;  
    GO  
    ```  
  
3.  <span data-ttu-id="6ef96-118">运行下列代码以分别按照三个索引的顺序从表中检索数据：</span><span class="sxs-lookup"><span data-stu-id="6ef96-118">Run the following code to retrieve data from the table in the order of each of the three indexes:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID  
    FROM NewOrg   
    ORDER BY OrgNode;  
  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM NewOrg   
    ORDER BY H_Level, OrgNode;  
  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM NewOrg   
    ORDER BY EmployeeID;  
    GO  
    ```  
  
4.  <span data-ttu-id="6ef96-119">比较结果集以查看每类索引中的存储顺序。</span><span class="sxs-lookup"><span data-stu-id="6ef96-119">Compare the result sets to see how the order is stored in each type of index.</span></span> <span data-ttu-id="6ef96-120">下面只显示了各输出的前四行。</span><span class="sxs-lookup"><span data-stu-id="6ef96-120">Only the first four rows of each output follow.</span></span>  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
     <span data-ttu-id="6ef96-121">深度优先索引：雇员记录存储在与相应经理的记录相邻的位置。</span><span class="sxs-lookup"><span data-stu-id="6ef96-121">Depth-first index: Employee records are stored adjacent to their manager.</span></span>  
  
     `LogicalNode OrgNode    H_Level EmployeeID LoginID`  
  
     `/             0x         0         1      zarifin`  
  
     `/1/          0x58        1         2      tplate`  
  
     `/1/1/       0x5AC0       2         4      schai`  
  
     `/1/1/1/     0x5AD6       3         9      jwang`  
  
     `/1/1/2/     0x5ADA       3        10      malexander`  
  
     `/1/2/       0x5B40       2         5      elang`  
  
     `/1/3/       0x5BC0       2         6      gsmits`  
  
     `/2/         0x68         1         3      hjensen`  
  
     `/2/1/       0x6AC0       2         7      sdavis`  
  
     `/2/2/       0x6B40       2         8      norint`  
  
     <span data-ttu-id="6ef96-122">**EmployeeID**优先索引：各行按照 **EmployeeID** 顺序存储。</span><span class="sxs-lookup"><span data-stu-id="6ef96-122">**EmployeeID**-first index: Rows are stored in **EmployeeID** sequence.</span></span>  
  
     `LogicalNode OrgNode    H_Level EmployeeID LoginID`  
  
     `/             0x         0         1      zarifin`  
  
     `/1/          0x58        1         2      tplate`  
  
     `/2/         0x68         1         3      hjensen`  
  
     `/1/1/       0x5AC0       2         4      schai`  
  
     `/1/2/       0x5B40       2         5      elang`  
  
     `/1/3/       0x5BC0       2         6      gsmits`  
  
     `/2/1/       0x6AC0       2         7      sdavis`  
  
     `/2/2/       0x6B40       2         8      norint`  
  
     `/1/1/1/     0x5AD6       3         9      jwang`  
  
     `/1/1/2/     0x5ADA       3        10      malexander`  
  
> [!NOTE]  
>  <span data-ttu-id="6ef96-123">有关显示深度优先索引和广度优先索引之间差异的关系图，请参阅[分层数据 (SQL Server)](../hierarchical-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="6ef96-123">For diagrams that show the difference between a depth-first index and a breadth-first index, see [Hierarchical Data &#40;SQL Server&#41;](../hierarchical-data-sql-server.md).</span></span>  
  
#### <a name="to-drop-the-unnecessary-columns"></a><span data-ttu-id="6ef96-124">删除不需要的列</span><span class="sxs-lookup"><span data-stu-id="6ef96-124">To drop the unnecessary columns</span></span>  
  
1.  <span data-ttu-id="6ef96-125">“ManagerID”\*\*\*\* 列用于表示雇员/经理关系，现在由“OrgNode”\*\*\*\* 列来表示。</span><span class="sxs-lookup"><span data-stu-id="6ef96-125">The **ManagerID** column represents the employee/manager relationship, which is now represented by the **OrgNode** column.</span></span> <span data-ttu-id="6ef96-126">如果其他应用程序不需要“ManagerID”\*\*\*\* 列，可以考虑使用下列语句删除该列：</span><span class="sxs-lookup"><span data-stu-id="6ef96-126">If other applications do not need the **ManagerID** column, consider dropping it by using the following statement:</span></span>  
  
    ```  
    ALTER TABLE NewOrg DROP COLUMN ManagerID ;  
    GO  
    ```  
  
2.  <span data-ttu-id="6ef96-127">“EmployeeID”\*\*\*\* 列也是冗余列。</span><span class="sxs-lookup"><span data-stu-id="6ef96-127">The **EmployeeID** column is also redundant.</span></span> <span data-ttu-id="6ef96-128">“OrgNode”\*\*\*\* 列可以唯一标识每个雇员。</span><span class="sxs-lookup"><span data-stu-id="6ef96-128">The **OrgNode** column uniquely identifies each employee.</span></span> <span data-ttu-id="6ef96-129">如果其他应用程序不需要“EmployeeID”\*\*\*\* 列，可以考虑使用下列代码先删除索引再删除该列：</span><span class="sxs-lookup"><span data-stu-id="6ef96-129">If other applications do not need the **EmployeeID** column, consider dropping the index and then the column by using the following code:</span></span>  
  
    ```  
    DROP INDEX EmpIDs_unq ON NewOrg ;  
    ALTER TABLE NewOrg DROP COLUMN EmployeeID ;  
    GO  
    ```  
  
#### <a name="to-replace-the-original-table-with-the-new-table"></a><span data-ttu-id="6ef96-130">使用新表替换原始表</span><span class="sxs-lookup"><span data-stu-id="6ef96-130">To replace the original table with the new table</span></span>  
  
1.  <span data-ttu-id="6ef96-131">如果原始表包含任何其他索引或约束，请将它们添加到“NewOrg”\*\*\*\* 表中。</span><span class="sxs-lookup"><span data-stu-id="6ef96-131">If your original table contained any additional indexes or constraints, add them to the **NewOrg** table.</span></span>  
  
2.  <span data-ttu-id="6ef96-132">将旧的“EmployeeDemo”\*\*\*\* 表替换为新表。</span><span class="sxs-lookup"><span data-stu-id="6ef96-132">Replace the old **EmployeeDemo** table with the new table.</span></span> <span data-ttu-id="6ef96-133">运行下列代码以删除旧表，然后使用旧表的名称重新命名新表：</span><span class="sxs-lookup"><span data-stu-id="6ef96-133">Run the following code to drop the old table, and then rename the new table with the old name:</span></span>  
  
    ```  
    DROP TABLE EmployeeDemo ;  
    GO  
    sp_rename 'NewOrg', EmployeeDemo ;  
    GO  
    ```  
  
3.  <span data-ttu-id="6ef96-134">运行下列代码以检查最终表：</span><span class="sxs-lookup"><span data-stu-id="6ef96-134">Run the following code to examine the final table:</span></span>  
  
    ```  
    SELECT * FROM EmployeeDemo ;  
    ```  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="6ef96-135">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="6ef96-135">Next Task in Lesson</span></span>  
 [<span data-ttu-id="6ef96-136">摘要：将表转换为层次结构</span><span class="sxs-lookup"><span data-stu-id="6ef96-136">Summary: Converting a Table to a Hierarchical Structure</span></span>](lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
  
