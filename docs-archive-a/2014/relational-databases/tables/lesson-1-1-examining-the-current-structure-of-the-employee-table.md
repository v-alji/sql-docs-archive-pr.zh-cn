---
title: 检查 Employee 表的当前结构 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- examining the current structure of the employee
ms.assetid: d546a820-105a-417d-ac35-44a6d1d70ac6
author: stevestein
ms.author: sstein
ms.openlocfilehash: b7f63773ebc1f28fb24f8f1000c3f87ee4d50544
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576592"
---
# <a name="examining-the-current-structure-of-the-employee-table"></a><span data-ttu-id="7b8ee-102">检查 Employee 表的当前结构</span><span class="sxs-lookup"><span data-stu-id="7b8ee-102">Examining the Current Structure of the Employee Table</span></span>
  <span data-ttu-id="7b8ee-103">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 示例数据库包含基于 HumanResources\*\*\*\* 架构的 Employee\*\*\*\* 表。</span><span class="sxs-lookup"><span data-stu-id="7b8ee-103">The sample [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database contains an **Employee** table in the **HumanResources** schema.</span></span> <span data-ttu-id="7b8ee-104">为了避免更改原始表，此步骤将对名为 **EmployeeDemo** 的 **Employee**表创建一个副本。</span><span class="sxs-lookup"><span data-stu-id="7b8ee-104">To avoid changing the original table, this step makes a copy of the **Employee** table named **EmployeeDemo**.</span></span> <span data-ttu-id="7b8ee-105">若要简化此示例，你只需从原始表中复制五列数据。</span><span class="sxs-lookup"><span data-stu-id="7b8ee-105">To simplify the example, you only copy five columns from the original table.</span></span> <span data-ttu-id="7b8ee-106">然后，查询**HumanResources**表以查看表中数据的结构，而无需使用 `hierarchyid` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="7b8ee-106">Then, you query the **HumanResources.EmployeeDemo** table to review how the data is structured in a table without using the `hierarchyid` data type.</span></span>  
  
### <a name="to-copy-the-employee-table"></a><span data-ttu-id="7b8ee-107">复制 Employee 表</span><span class="sxs-lookup"><span data-stu-id="7b8ee-107">To copy the Employee table</span></span>  
  
1.  <span data-ttu-id="7b8ee-108">在查询编辑器窗口中，运行下列代码以将 **Employee** 表中的表结构和数据复制到名为 **EmployeeDemo**的新表中。</span><span class="sxs-lookup"><span data-stu-id="7b8ee-108">In a Query Editor window, run the following code to copy the table structure and data from the **Employee** table into a new table named **EmployeeDemo**.</span></span>  
  
    ```  
    USE AdventureWorks ;  
    GO  
  
    SELECT EmployeeID, LoginID, ManagerID, Title, HireDate   
    INTO HumanResources.EmployeeDemo   
    FROM HumanResources.Employee ;  
    GO  
    ```  
  
### <a name="to-examine-the-structure-and-data-of-the-employeedemo-table"></a><span data-ttu-id="7b8ee-109">检查 EmployeeDemo 表的结构和数据</span><span class="sxs-lookup"><span data-stu-id="7b8ee-109">To examine the structure and data of the EmployeeDemo table</span></span>  
  
-   <span data-ttu-id="7b8ee-110">这个新的 **EmployeeDemo** 表表示现有数据库中你可能要迁移到新结构的典型表。</span><span class="sxs-lookup"><span data-stu-id="7b8ee-110">This new **EmployeeDemo** table represents a typical table in an existing database that you might want to migrate to a new structure.</span></span> <span data-ttu-id="7b8ee-111">在查询编辑器窗口中，运行下列代码以显示表如何使用自联接来显示雇员/经理关系：</span><span class="sxs-lookup"><span data-stu-id="7b8ee-111">In a Query Editor window, run the following code to show how the table uses a self join to display the employee/manager relationships:</span></span>  
  
    ```  
    SELECT   
         Mgr.EmployeeID AS MgrID, Mgr.LoginID AS Manager,   
         Emp.EmployeeID AS E_ID, Emp.LoginID, Emp.Title  
    FROM HumanResources.EmployeeDemo AS Emp  
    LEFT JOIN HumanResources.EmployeeDemo AS Mgr  
    ON Emp.ManagerID = Mgr.EmployeeID  
    ORDER BY MgrID, E_ID  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    MgrID Manager                 E_ID LoginID                  Title  
    NULL NULL                      109 adventure-works\ken0     Chief Executive Officer  
    3    adventure-works\roberto0  4   adventure-works\rob0     Senior Tool Designer  
    3    adventure-works\roberto0  9   adventure-works\gail0    Design Engineer  
    3    adventure-works\roberto0  11  adventure-works\jossef0  Design Engineer  
    3    adventure-works\roberto0  158 adventure-works\dylan0   Research and Development Manager  
    3    adventure-works\roberto0  263 adventure-works\ovidiu0  Senior Tool Designer  
    3    adventure-works\roberto0  267 adventure-works\michael8 Senior Design Engineer  
    3    adventure-works\roberto0  270 adventure-works\sharon0  Design Engineer  
    6    adventure-works\david0    2   adventure-works\kevin0   Marketing Assistant  
    ...  
    ```  
  
     <span data-ttu-id="7b8ee-112">结果在继续，共 290 行。</span><span class="sxs-lookup"><span data-stu-id="7b8ee-112">The results continue for a total of 290 rows.</span></span>  
  
 <span data-ttu-id="7b8ee-113">请注意，`ORDER BY` 子句会使输出中的每个管理级别的直接下属都列在一起。</span><span class="sxs-lookup"><span data-stu-id="7b8ee-113">Notice that the `ORDER BY` clause caused the output to list the direct reports of each management level together.</span></span> <span data-ttu-id="7b8ee-114">例如， **MgrID** 3 (roberto0) 的所有七个直接下属都彼此紧挨着列出。</span><span class="sxs-lookup"><span data-stu-id="7b8ee-114">For instance, all seven of the direct reports of **MgrID** 3 (roberto0) are listed adjacent to each other.</span></span> <span data-ttu-id="7b8ee-115">虽然有可能实现，但是要将最终向 **MgrID** 3 负责的所有雇员进行分组将会更加困难。</span><span class="sxs-lookup"><span data-stu-id="7b8ee-115">Although not impossible, it is much more difficult to group all those who eventually report to **MgrID** 3.</span></span>  
  
 <span data-ttu-id="7b8ee-116">在下一个任务中，我们将使用 `hierarchyid` 数据类型创建一个新表，然后将数据移到该新表中。</span><span class="sxs-lookup"><span data-stu-id="7b8ee-116">In the next task, we will create a new table with a `hierarchyid` data type, and move the data into the new table.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="7b8ee-117">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="7b8ee-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="7b8ee-118">使用现有层次结构数据填充表</span><span class="sxs-lookup"><span data-stu-id="7b8ee-118">Populating a Table with Existing Hierarchical Data</span></span>](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
  
