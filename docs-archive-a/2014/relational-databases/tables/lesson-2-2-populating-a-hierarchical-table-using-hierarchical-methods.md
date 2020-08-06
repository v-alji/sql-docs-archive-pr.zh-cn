---
title: 使用分层方法填充层次结构表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- HierarchyID
helpviewer_keywords:
- HierarchyID
ms.assetid: 2c95fa60-5b8e-4a05-ac09-cffe2b05900a
author: stevestein
ms.author: sstein
ms.openlocfilehash: ef99d711a772a075f568a83f5d56fcecaaa598f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588397"
---
# <a name="populating-a-hierarchical-table-using-hierarchical-methods"></a><span data-ttu-id="8c485-102">使用分层方法填充层次结构表</span><span class="sxs-lookup"><span data-stu-id="8c485-102">Populating a Hierarchical Table Using Hierarchical Methods</span></span>
  [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] <span data-ttu-id="8c485-103">有 8 名在市场营销部门工作的雇员。</span><span class="sxs-lookup"><span data-stu-id="8c485-103">has 8 employees working in the Marketing department.</span></span> <span data-ttu-id="8c485-104">雇员的层次结构如下所示：</span><span class="sxs-lookup"><span data-stu-id="8c485-104">The employee hierarchy looks like this:</span></span>  
  
 <span data-ttu-id="8c485-105">**David**（ **EmployeeID** 为 6）是市场营销经理。</span><span class="sxs-lookup"><span data-stu-id="8c485-105">**David**, **EmployeeID** 6, is the Marketing Manager.</span></span> <span data-ttu-id="8c485-106">**David**下辖三名市场营销专员，他们分别是：</span><span class="sxs-lookup"><span data-stu-id="8c485-106">Three Marketing Specialists report to **David**:</span></span>  
  
-   <span data-ttu-id="8c485-107">**Sariya**， **EmployeeID** 46</span><span class="sxs-lookup"><span data-stu-id="8c485-107">**Sariya**, **EmployeeID** 46</span></span>  
  
-   <span data-ttu-id="8c485-108">**John**， **EmployeeID** 271</span><span class="sxs-lookup"><span data-stu-id="8c485-108">**John**, **EmployeeID** 271</span></span>  
  
-   <span data-ttu-id="8c485-109">**Jill**， **EmployeeID** 119</span><span class="sxs-lookup"><span data-stu-id="8c485-109">**Jill**, **EmployeeID** 119</span></span>  
  
 <span data-ttu-id="8c485-110">销售助理 **Wanida** (**EmployeeID** 269)，是 **Sariya**的下属；销售助理 **Mary** (**EmployeeID** 272)，是 **John**的下属。</span><span class="sxs-lookup"><span data-stu-id="8c485-110">Marketing Assistant **Wanida** (**EmployeeID** 269), reports to **Sariya**, and Marketing Assistant **Mary** (**EmployeeID** 272), reports to **John**.</span></span>  
  
### <a name="to-insert-the-root-of-the-hierarchy-tree"></a><span data-ttu-id="8c485-111">插入层次结构树的根</span><span class="sxs-lookup"><span data-stu-id="8c485-111">To insert the root of the hierarchy tree</span></span>  
  
1.  <span data-ttu-id="8c485-112">下例将市场营销经理 **David** 插入层次结构的根处的表中。</span><span class="sxs-lookup"><span data-stu-id="8c485-112">The following example inserts **David** the Marketing Manager into the table at the root of the hierarchy.</span></span> <span data-ttu-id="8c485-113">**OrdLevel** 列是一个计算列。</span><span class="sxs-lookup"><span data-stu-id="8c485-113">The **OrdLevel** column is a computed column.</span></span> <span data-ttu-id="8c485-114">因此，它不是 INSERT 语句的一部分。</span><span class="sxs-lookup"><span data-stu-id="8c485-114">Therefore, it is not part of the INSERT statement.</span></span> <span data-ttu-id="8c485-115">第一条记录使用 [GetRoot()](/sql/t-sql/data-types/getroot-database-engine) 方法将其自身填充为层次结构的根。</span><span class="sxs-lookup"><span data-stu-id="8c485-115">This first record uses the [GetRoot()](/sql/t-sql/data-types/getroot-database-engine) method to populate this first record as the root of the hierarchy.</span></span>  
  
    ```  
    INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
    VALUES (hierarchyid::GetRoot(), 6, 'David', 'Marketing Manager') ;  
    GO  
    ```  
  
2.  <span data-ttu-id="8c485-116">执行以下代码来检查表中的初始行：</span><span class="sxs-lookup"><span data-stu-id="8c485-116">Execute the following code to examine initial row in the table:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    ```  
  
 <span data-ttu-id="8c485-117">如上一课所述，使用 `ToString()` 方法将 `hierarchyid` 数据类型转换成更易于理解的格式。</span><span class="sxs-lookup"><span data-stu-id="8c485-117">As in the previous lesson, we use the `ToString()` method to convert the `hierarchyid` data type to a format that is more easily understood.</span></span>  
  
### <a name="to-insert-a-subordinate-employee"></a><span data-ttu-id="8c485-118">插入下属雇员</span><span class="sxs-lookup"><span data-stu-id="8c485-118">To insert a subordinate employee</span></span>  
  
1.  <span data-ttu-id="8c485-119">**Sariya** 是 **David**的下属。</span><span class="sxs-lookup"><span data-stu-id="8c485-119">**Sariya** reports to **David**.</span></span> <span data-ttu-id="8c485-120">若要插入**Sariya 的**节点，必须创建相应的数据类型的**OrgNode**值 `hierarchyid` 。</span><span class="sxs-lookup"><span data-stu-id="8c485-120">To insert **Sariya's** node, you must create an appropriate **OrgNode** value of data type `hierarchyid`.</span></span> <span data-ttu-id="8c485-121">下面的代码创建一个数据类型为 `hierarchyid` 的变量，并用表的根 OrgNode 值填充此变量。</span><span class="sxs-lookup"><span data-stu-id="8c485-121">The following code creates a variable of data type `hierarchyid` and populates it with the root OrgNode value of the table.</span></span> <span data-ttu-id="8c485-122">然后使用该变量和 [GetDescendant()](/sql/t-sql/data-types/getdescendant-database-engine) 方法插入从属节点行。</span><span class="sxs-lookup"><span data-stu-id="8c485-122">Then uses that variable with the [GetDescendant()](/sql/t-sql/data-types/getdescendant-database-engine) method to insert row that is a subordinate node.</span></span> <span data-ttu-id="8c485-123">`GetDescendant` 采用两个参数。</span><span class="sxs-lookup"><span data-stu-id="8c485-123">`GetDescendant` takes two arguments.</span></span> <span data-ttu-id="8c485-124">检查以下选项的参数值：</span><span class="sxs-lookup"><span data-stu-id="8c485-124">Review the following options for the argument values:</span></span>  
  
    -   <span data-ttu-id="8c485-125">如果父级为 NULL， `GetDescendant` 返回 NULL。</span><span class="sxs-lookup"><span data-stu-id="8c485-125">If parent is NULL, `GetDescendant` returns NULL.</span></span>  
  
    -   <span data-ttu-id="8c485-126">如果父级不为 NULL，并且 child1 和 child2 为 NULL， `GetDescendant` 返回父级的子级。</span><span class="sxs-lookup"><span data-stu-id="8c485-126">If parent is not NULL, and both child1 and child2 are NULL, `GetDescendant` returns a child of parent.</span></span>  
  
    -   <span data-ttu-id="8c485-127">如果父级和 child1 不为 NULL，而 child2 为 NULL， `GetDescendant` 返回一个大于 child1 的父级的子级。</span><span class="sxs-lookup"><span data-stu-id="8c485-127">If parent and child1 are not NULL, and child2 is NULL, `GetDescendant` returns a child of parent greater than child1.</span></span>  
  
    -   <span data-ttu-id="8c485-128">如果父级和 child2 不为 NULL，而 child1 为 NULL， `GetDescendant` 返回一个小于 child2 的父级的子级。</span><span class="sxs-lookup"><span data-stu-id="8c485-128">If parent and child2 are not NULL and child1 is NULL, `GetDescendant` returns a child of parent less than child2.</span></span>  
  
    -   <span data-ttu-id="8c485-129">如果父级、child1 和 child2 都不为 NULL， `GetDescendant` 返回一个大于 child1 且小于 child2 的父级的子级。</span><span class="sxs-lookup"><span data-stu-id="8c485-129">If parent, child1, and child2 are all not NULL, `GetDescendant` returns a child of parent greater than child1 and less than child2.</span></span>  
  
     <span data-ttu-id="8c485-130">下面的代码使用根父级的 `(NULL, NULL)` 参数，因为除了根外，表中尚未存在其他行。</span><span class="sxs-lookup"><span data-stu-id="8c485-130">The following code uses the `(NULL, NULL)` arguments of the root parent because there are not yet any rows in the table except the root.</span></span> <span data-ttu-id="8c485-131">执行下面的代码以插入 **Sariya**：</span><span class="sxs-lookup"><span data-stu-id="8c485-131">Execute the following code to insert **Sariya**:</span></span>  
  
    ```  
    DECLARE @Manager hierarchyid   
    SELECT @Manager = hierarchyid::GetRoot()  
    FROM HumanResources.EmployeeOrg ;  
  
    INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
    VALUES  
    (@Manager.GetDescendant(NULL, NULL), 46, 'Sariya', 'Marketing Specialist') ;  
  
    ```  
  
2.  <span data-ttu-id="8c485-132">从第一个过程重复查询来对表进行查询并查看项的显示方式：</span><span class="sxs-lookup"><span data-stu-id="8c485-132">Repeat the query from the first procedure to query the table and see how the entries appear:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    /1/          0x58    1        46         Sariya  Marketing Specialist  
    ```  
  
### <a name="to-create-a-procedure-for-entering-new-nodes"></a><span data-ttu-id="8c485-133">创建输入新节点的过程</span><span class="sxs-lookup"><span data-stu-id="8c485-133">To create a procedure for entering new nodes</span></span>  
  
1.  <span data-ttu-id="8c485-134">若要简化数据的输入，请创建下面的存储过程以向 **EmployeeOrg** 表添加雇员。</span><span class="sxs-lookup"><span data-stu-id="8c485-134">To simplify entering data, create the following stored procedure to add employees to the **EmployeeOrg** table.</span></span> <span data-ttu-id="8c485-135">该过程接受有关将要添加的雇员的输入值。</span><span class="sxs-lookup"><span data-stu-id="8c485-135">The procedure accepts input values about the employee being added.</span></span> <span data-ttu-id="8c485-136">这包括新雇员的上司的 **EmployeeID** 、新雇员的 **EmployeeID** 号以及他们的名字和职位。</span><span class="sxs-lookup"><span data-stu-id="8c485-136">This includes the **EmployeeID** of the new employee's manager, the new employee's **EmployeeID** number, and their first name and title.</span></span> <span data-ttu-id="8c485-137">该过程使用 `GetDescendant()` 和 [GetAncestor()](/sql/t-sql/data-types/getancestor-database-engine) 方法。</span><span class="sxs-lookup"><span data-stu-id="8c485-137">The procedure uses `GetDescendant()` and also the [GetAncestor()](/sql/t-sql/data-types/getancestor-database-engine) method.</span></span> <span data-ttu-id="8c485-138">执行下面的代码以创建此过程：</span><span class="sxs-lookup"><span data-stu-id="8c485-138">Execute the following code to create the procedure:</span></span>  
  
    ```  
    CREATE PROC AddEmp(@mgrid int, @empid int, @e_name varchar(20), @title varchar(20))   
    AS   
    BEGIN  
       DECLARE @mOrgNode hierarchyid, @lc hierarchyid  
       SELECT @mOrgNode = OrgNode   
       FROM HumanResources.EmployeeOrg   
       WHERE EmployeeID = @mgrid  
       SET TRANSACTION ISOLATION LEVEL SERIALIZABLE  
       BEGIN TRANSACTION  
          SELECT @lc = max(OrgNode)   
          FROM HumanResources.EmployeeOrg   
          WHERE OrgNode.GetAncestor(1) =@mOrgNode ;  
  
          INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
          VALUES(@mOrgNode.GetDescendant(@lc, NULL), @empid, @e_name, @title)  
       COMMIT  
    END ;  
    GO  
    ```  
  
2.  <span data-ttu-id="8c485-139">以下示例添加作为 **David**的直接或非直接下属的其余 4 名雇员。</span><span class="sxs-lookup"><span data-stu-id="8c485-139">The following example adds the remaining 4 employees that report directly or indirectly to **David**.</span></span>  
  
    ```  
    EXEC AddEmp 6, 271, 'John', 'Marketing Specialist' ;  
    EXEC AddEmp 6, 119, 'Jill', 'Marketing Specialist' ;  
    EXEC AddEmp 46, 269, 'Wanida', 'Marketing Assistant' ;  
    EXEC AddEmp 271, 272, 'Mary', 'Marketing Assistant' ;  
    ```  
  
3.  <span data-ttu-id="8c485-140">再次执行下面的查询以检查 **EmployeeOrg** 表中的行：</span><span class="sxs-lookup"><span data-stu-id="8c485-140">Again, execute the following query examine the rows in the **EmployeeOrg** table:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    /1/          0x58    1        46         Sariya  Marketing Specialist  
    /1/1/        0x5AC0  2        269        Wanida  Marketing Assistant  
    /2/          0x68    1        271        John    Marketing Specialist  
    /2/1/        0x6AC0  2        272        Mary    Marketing Assistant  
    /3/          0x78    1        119        Jill    Marketing Specialist  
    ```  
  
 <span data-ttu-id="8c485-141">现在，市场营销组织已完全填充在表中。</span><span class="sxs-lookup"><span data-stu-id="8c485-141">The table is now fully populated with the Marketing organization.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="8c485-142">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="8c485-142">Next Task in Lesson</span></span>  
 [<span data-ttu-id="8c485-143">使用层次结构方法查询层次结构表</span><span class="sxs-lookup"><span data-stu-id="8c485-143">Querying a Hierarchical Table Using Hierarchy Methods</span></span>](lesson-2-3-querying-a-hierarchical-table-using-hierarchy-methods.md)  
  
  
