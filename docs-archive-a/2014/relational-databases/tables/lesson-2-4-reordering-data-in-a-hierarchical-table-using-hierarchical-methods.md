---
title: 使用分层方法对层次结构表中的数据重新排序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 7b8064c7-62c6-488d-84d2-57a5828fb907
author: stevestein
ms.author: sstein
ms.openlocfilehash: ac6c93f359a81a80af81182120f213564680de0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577465"
---
# <a name="reordering-data-in-a-hierarchical-table-using-hierarchical-methods"></a><span data-ttu-id="f06fd-102">使用分层方法对层次结构表中的数据重新排序</span><span class="sxs-lookup"><span data-stu-id="f06fd-102">Reordering Data in a Hierarchical Table Using Hierarchical Methods</span></span>
  <span data-ttu-id="f06fd-103">重新组织层次结构是一项常见的维护任务。</span><span class="sxs-lookup"><span data-stu-id="f06fd-103">Reorganizing a hierarchy is a common maintenance task.</span></span> <span data-ttu-id="f06fd-104">在此任务中，使用包含 [GetReparentedValue](/sql/t-sql/data-types/getreparentedvalue-database-engine) 方法的 UPDATE 语句首先将一行移到层次结构的新位置。</span><span class="sxs-lookup"><span data-stu-id="f06fd-104">In this task, we will use an UPDATE statement with the [GetReparentedValue](/sql/t-sql/data-types/getreparentedvalue-database-engine) method to first move a single row to a new location in the hierarchy.</span></span> <span data-ttu-id="f06fd-105">然后，我们会将整个子树移到一个新位置。</span><span class="sxs-lookup"><span data-stu-id="f06fd-105">Then we will move an entire sub-tree to a new location.</span></span>  
  
 <span data-ttu-id="f06fd-106">`GetReparentedValue` 方法使用两个参数。</span><span class="sxs-lookup"><span data-stu-id="f06fd-106">The `GetReparentedValue` method takes two arguments.</span></span> <span data-ttu-id="f06fd-107">第一个参数用于描述要修改的层次结构部分。</span><span class="sxs-lookup"><span data-stu-id="f06fd-107">The first argument describes the part of the hierarchy to be modified.</span></span> <span data-ttu-id="f06fd-108">例如，如果层次结构为 **/1/4/2/3/** ，希望更改 **/1/4/** 部分，将层次结构变为 **/2/1/2/3/**，后两个节点 (**2/3/**) 保持不变，则必须提供要更改的节点 (**/1/4/**) 作为第一个参数。</span><span class="sxs-lookup"><span data-stu-id="f06fd-108">For example, if a hierarchy is **/1/4/2/3/** and you want to change the **/1/4/** section, the hierarchy becomes **/2/1/2/3/**, leaving the last two nodes (**2/3/**) unchanged, you must provide the changing nodes (**/1/4/**) as the first argument.</span></span> <span data-ttu-id="f06fd-109">第二个参数提供新的层次结构级别，在示例中为 **/2/1/**。</span><span class="sxs-lookup"><span data-stu-id="f06fd-109">The second argument provides the new hierarchy level, in our example **/2/1/**.</span></span> <span data-ttu-id="f06fd-110">这两个参数无须包含相同的级别数。</span><span class="sxs-lookup"><span data-stu-id="f06fd-110">The two arguments do not have to contain the same number of levels.</span></span>  
  
### <a name="to-move-a-single-row-to-a-new-location-in-the-hierarchy"></a><span data-ttu-id="f06fd-111">将一行移到层次结构中的新位置上</span><span class="sxs-lookup"><span data-stu-id="f06fd-111">To move a single row to a new location in the hierarchy</span></span>  
  
1.  <span data-ttu-id="f06fd-112">当前，Wanida 向 Sariya 报告。</span><span class="sxs-lookup"><span data-stu-id="f06fd-112">Currently Wanida reports to Sariya.</span></span> <span data-ttu-id="f06fd-113">在此过程中，将 Wanida 从其当前的节点 **/1/1/** 移出，使她可以向 Jill 报告。</span><span class="sxs-lookup"><span data-stu-id="f06fd-113">In this procedure, you move Wanida from her current node **/1/1/,** so that she reports to Jill.</span></span> <span data-ttu-id="f06fd-114">她的新节点将变为 **/3/1/** ，而 **/1/** 成为第一个参数， **/3/** 成为第二个参数。</span><span class="sxs-lookup"><span data-stu-id="f06fd-114">Her new node will become **/3/1/** so **/1/** is the first argument and **/3/** is the second.</span></span> <span data-ttu-id="f06fd-115">这些值与 Sariya 和 Jill 的 **OrgNode** 值相对应。</span><span class="sxs-lookup"><span data-stu-id="f06fd-115">These correspond to the **OrgNode** values of Sariya and Jill.</span></span> <span data-ttu-id="f06fd-116">执行下列代码将 Wanida 从 Sariya 的组织移到 Jill 的组织中：</span><span class="sxs-lookup"><span data-stu-id="f06fd-116">Execute the following code to move Wanida from Sariya's organization to Jill's:</span></span>  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid , @OldParent hierarchyid, @NewParent hierarchyid  
    SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 269 ;   
    SELECT @OldParent = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 46 ;   
    SELECT @NewParent = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 119 ;   
  
    UPDATE HumanResources.EmployeeOrg  
    SET OrgNode = @CurrentEmployee. GetReparentedValue(@OldParent, @NewParent)   
    WHERE OrgNode = @CurrentEmployee ;  
    GO  
    ```  
  
2.  <span data-ttu-id="f06fd-117">执行下面的代码以查看结果：</span><span class="sxs-lookup"><span data-stu-id="f06fd-117">Execute the following code to see the result:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
     <span data-ttu-id="f06fd-118">现在，Wanida 位于节点 **/3/1/**。</span><span class="sxs-lookup"><span data-stu-id="f06fd-118">Wanida is now at node **/3/1/**.</span></span>  
  
### <a name="to-reorganize-a-section-of-a-hierarchy"></a><span data-ttu-id="f06fd-119">重新组织层次结构中的某一部分</span><span class="sxs-lookup"><span data-stu-id="f06fd-119">To reorganize a section of a hierarchy</span></span>  
  
1.  <span data-ttu-id="f06fd-120">为了演示如何同时移动大量人员，请先执行下列代码，添加一个向 Wanida 报告的实习生：</span><span class="sxs-lookup"><span data-stu-id="f06fd-120">To demonstrate how to move a larger number of people at the same time, first execute the following code to add an intern reporting to Wanida:</span></span>  
  
    ```  
    EXEC AddEmp 269, 291, 'Kevin', 'Marketing Intern'  ;  
    GO  
    ```  
  
2.  <span data-ttu-id="f06fd-121">现在，Kevin 向 Wanida 报告，Wanida 向 Jill 报告，而 Jill 向 David 报告。</span><span class="sxs-lookup"><span data-stu-id="f06fd-121">Now Kevin reports to Wanida, who reports to Jill, who reports to David.</span></span> <span data-ttu-id="f06fd-122">也就是说，Kevin 位于级别 **/3/1/1/**。</span><span class="sxs-lookup"><span data-stu-id="f06fd-122">That means that Kevin is at level **/3/1/1/**.</span></span> <span data-ttu-id="f06fd-123">若要将 Jill 的所有下属都移到一位新经理之下，需要将 **OrgNode** 为 **/3/** 的所有节点更新为新值。</span><span class="sxs-lookup"><span data-stu-id="f06fd-123">To move all of Jill's subordinates to a new manager, we will update all nodes that have **/3/** as their **OrgNode** to a new value.</span></span> <span data-ttu-id="f06fd-124">执行下列代码以便将 Wanida 更新为向 Sariya 负责，但 Kevin 仍向 Wanida 负责：</span><span class="sxs-lookup"><span data-stu-id="f06fd-124">Execute the following code to update Wanida to report to Sariya, but keep  Kevin reporting to Wanida:</span></span>  
  
    ```  
    DECLARE @OldParent hierarchyid, @NewParent hierarchyid  
    SELECT @OldParent = OrgNode FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 119 ; -- Jill  
    SELECT @NewParent = OrgNode FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ; -- Sariya  
    DECLARE children_cursor CURSOR FOR  
    SELECT OrgNode FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(1) = @OldParent;  
    DECLARE @ChildId hierarchyid;  
    OPEN children_cursor  
    FETCH NEXT FROM children_cursor INTO @ChildId;  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
    START:  
        DECLARE @NewId hierarchyid;  
        SELECT @NewId = @NewParent.GetDescendant(MAX(OrgNode), NULL)  
        FROM HumanResources.EmployeeOrg WHERE OrgNode.GetAncestor(1) = @NewParent;  
  
        UPDATE HumanResources.EmployeeOrg  
        SET OrgNode = OrgNode.GetReparentedValue(@ChildId, @NewId)  
        WHERE OrgNode.IsDescendantOf(@ChildId) = 1;  
        IF @@error <> 0 GOTO START -- On error, retry  
            FETCH NEXT FROM children_cursor INTO @ChildId;  
    END  
    CLOSE children_cursor;  
    DEALLOCATE children_cursor;  
  
    ```  
  
3.  <span data-ttu-id="f06fd-125">执行下面的代码以查看结果：</span><span class="sxs-lookup"><span data-stu-id="f06fd-125">Execute the following code to see the result:</span></span>  
  
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
/1/1//2      0x5AD0  3        291        Kevin   Marketing Intern  
/2/          0x68    1        271        John    Marketing Specialist  
/2/1/        0x6AC0  2        272        Mary    Marketing Assistant  
/3/          0x78    1        119        Jill    Marketing Specialist  
```  
  
 <span data-ttu-id="f06fd-126">之前向 Jill 报告的整个组织树（Wanida 和 Kevin）现在均向 Sariya 报告。</span><span class="sxs-lookup"><span data-stu-id="f06fd-126">The entire organizational tree that had reported to Jill (both Wanida and Kevin) now reports to Sariya.</span></span>  
  
 <span data-ttu-id="f06fd-127">有关重新组织层次结构中的某一部分的存储过程，请参阅 [移动子树](../hierarchical-data-sql-server.md#BKMK_MovingSubtrees)的“移动子树”部分。</span><span class="sxs-lookup"><span data-stu-id="f06fd-127">For a stored procedure to reorganize a section of a hierarchy, see the "Moving Subtrees" section of [Moving Subtrees](../hierarchical-data-sql-server.md#BKMK_MovingSubtrees).</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="f06fd-128">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="f06fd-128">Next Task in Lesson</span></span>  
 [<span data-ttu-id="f06fd-129">摘要：管理层次结构表中的数据</span><span class="sxs-lookup"><span data-stu-id="f06fd-129">Summary: Managing Data in a Hierarchical Table</span></span>](lesson-2-5-summary-managing-data-in-a-hierarchical-table.md)  
  
  
