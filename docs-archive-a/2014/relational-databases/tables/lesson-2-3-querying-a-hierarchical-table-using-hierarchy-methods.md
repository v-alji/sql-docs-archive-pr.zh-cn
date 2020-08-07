---
title: 使用层次结构方法查询层次结构表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 3b4f7dae-65b5-4d8d-8641-87aba9aa692d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6c86c8e8678fc821dc3796a511349c1c3498bdb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587732"
---
# <a name="querying-a-hierarchical-table-using-hierarchy-methods"></a><span data-ttu-id="fc159-102">使用层次结构方法查询层次结构表</span><span class="sxs-lookup"><span data-stu-id="fc159-102">Querying a Hierarchical Table Using Hierarchy Methods</span></span>
  <span data-ttu-id="fc159-103">由于 HumanResources.EmployeeOrg 表已完全填充，此任务将说明如何使用某些分层方法来查询层次结构。</span><span class="sxs-lookup"><span data-stu-id="fc159-103">Now that the HumanResources.EmployeeOrg table is fully populated, this task will show you how to query the hierarchy using some of the hierarchical methods.</span></span>  
  
### <a name="to-find-subordinate-nodes"></a><span data-ttu-id="fc159-104">查找从属节点</span><span class="sxs-lookup"><span data-stu-id="fc159-104">To find subordinate nodes</span></span>  
  
1.  <span data-ttu-id="fc159-105">Sariya 有一名下属雇员。</span><span class="sxs-lookup"><span data-stu-id="fc159-105">Sariya has one subordinate employee.</span></span> <span data-ttu-id="fc159-106">若要查询 Sariya 的下属，请执行使用 [IsDescendantOf](/sql/t-sql/data-types/isdescendantof-database-engine) 方法的以下查询：</span><span class="sxs-lookup"><span data-stu-id="fc159-106">To query for Sariya's subordinates, execute the following query that uses the [IsDescendantOf](/sql/t-sql/data-types/isdescendantof-database-engine) method:</span></span>  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ;  
  
    SELECT *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.IsDescendantOf(@CurrentEmployee ) = 1 ;  
    ```  
  
     <span data-ttu-id="fc159-107">结果同时列出 Sariya 和 Wanida。</span><span class="sxs-lookup"><span data-stu-id="fc159-107">The result lists both Sariya and Wanida.</span></span> <span data-ttu-id="fc159-108">Sariya 的列出原因是她是 0 级后代。</span><span class="sxs-lookup"><span data-stu-id="fc159-108">Sariya is listed because she is the descendant at the 0 level.</span></span> <span data-ttu-id="fc159-109">Wanida 是 1 级后代。</span><span class="sxs-lookup"><span data-stu-id="fc159-109">Wanida is the descendant at the 1 level.</span></span>  
  
2.  <span data-ttu-id="fc159-110">也可以使用 [GetAncestor](/sql/t-sql/data-types/getancestor-database-engine) 方法查询此信息。</span><span class="sxs-lookup"><span data-stu-id="fc159-110">You can also query for this information by using the [GetAncestor](/sql/t-sql/data-types/getancestor-database-engine) method.</span></span> <span data-ttu-id="fc159-111">`GetAncestor` 对尝试返回的级别采用了一个参数。</span><span class="sxs-lookup"><span data-stu-id="fc159-111">`GetAncestor` takes an argument for the level that you are trying to return.</span></span> <span data-ttu-id="fc159-112">由于 Wanida 位于 Sariya 下面一级，因此使用 `GetAncestor(1)` ，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="fc159-112">Since Wanida is one level underneath Sariya, use `GetAncestor(1)` as demonstrated in the following code:</span></span>  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ;  
  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(1) = @CurrentEmployee  
    ```  
  
     <span data-ttu-id="fc159-113">这次，结果仅列出 Wanida。</span><span class="sxs-lookup"><span data-stu-id="fc159-113">This time the result lists only Wanida.</span></span>  
  
3.  <span data-ttu-id="fc159-114">现在，将 `@CurrentEmployee` 更改为 David (EmployeeID 6)，并将级别更改为 2。</span><span class="sxs-lookup"><span data-stu-id="fc159-114">Now change the `@CurrentEmployee` to David (EmployeeID 6) and the level to 2.</span></span> <span data-ttu-id="fc159-115">执行以下过程也会返回 Wanida：</span><span class="sxs-lookup"><span data-stu-id="fc159-115">Execute the following to also return Wanida:</span></span>  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 6 ;  
  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(2) = @CurrentEmployee  
    ```  
  
     <span data-ttu-id="fc159-116">这次，还收到向 David 报告的位于两个级别之下的 Mary。</span><span class="sxs-lookup"><span data-stu-id="fc159-116">This time, you also receive Mary who also reports to David, two levels down.</span></span>  
  
### <a name="to-use-getroot-and-getlevel"></a><span data-ttu-id="fc159-117">使用 GetRoot 和 GetLevel</span><span class="sxs-lookup"><span data-stu-id="fc159-117">To use GetRoot, and GetLevel</span></span>  
  
1.  <span data-ttu-id="fc159-118">随着层次结构不断扩大，更加难于确定成员在层次结构中的位置。</span><span class="sxs-lookup"><span data-stu-id="fc159-118">As the hierarchy grows larger it is more difficult to determine where the members are in the hierarchy.</span></span> <span data-ttu-id="fc159-119">使用 [GetLevel](/sql/t-sql/data-types/getlevel-database-engine) 方法可查明每一行下方有多少个级别处于层次结构中。</span><span class="sxs-lookup"><span data-stu-id="fc159-119">Use the [GetLevel](/sql/t-sql/data-types/getlevel-database-engine) method to find how many levels down each row is in the hierarchy.</span></span> <span data-ttu-id="fc159-120">执行下面的代码以查看所有行的下属级别：</span><span class="sxs-lookup"><span data-stu-id="fc159-120">Execute the following code to view the levels of all the rows:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode.GetLevel() AS EmpLevel, *  
    FROM HumanResources.EmployeeOrg ;  
    GO  
  
    ```  
  
2.  <span data-ttu-id="fc159-121">使用 [GetRoot](/sql/t-sql/data-types/getroot-database-engine) 方法查找层次结构中的根节点。</span><span class="sxs-lookup"><span data-stu-id="fc159-121">Use the [GetRoot](/sql/t-sql/data-types/getroot-database-engine) method to find the root node in the hierarchy.</span></span> <span data-ttu-id="fc159-122">下面的代码返回一个作为根的行：</span><span class="sxs-lookup"><span data-stu-id="fc159-122">The following code returns the single row which is the root:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode = hierarchyid::GetRoot() ;  
    GO  
  
    ```  
  
 <span data-ttu-id="fc159-123">下一个任务将重新组织层次结构。</span><span class="sxs-lookup"><span data-stu-id="fc159-123">The next task will reorganize the hierarchy.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="fc159-124">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="fc159-124">Next Task in Lesson</span></span>  
 [<span data-ttu-id="fc159-125">使用分层方法对层次结构表中的数据重新排序</span><span class="sxs-lookup"><span data-stu-id="fc159-125">Reordering Data in a Hierarchical Table Using Hierarchical Methods</span></span>](lesson-2-4-reordering-data-in-a-hierarchical-table-using-hierarchical-methods.md)  
  
  
