---
title: 使用 hierarchyid 数据类型创建表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 0d1f361f-336c-4571-99d1-f4813b2d9fc4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2c9b59795949e11cabd21b0be8de844b33d73c37
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693232"
---
# <a name="creating-a-table-using-the-hierarchyid-data-type"></a><span data-ttu-id="1feaf-102">使用 hierarchyid 数据类型创建表</span><span class="sxs-lookup"><span data-stu-id="1feaf-102">Creating a Table Using the hierarchyid Data Type</span></span>
  <span data-ttu-id="1feaf-103">下例创建了一个名为 EmployeeOrg 的表，该表包含雇员数据及其报告层次结构。</span><span class="sxs-lookup"><span data-stu-id="1feaf-103">The following example creates a table named EmployeeOrg, which includes employee data together with their reporting hierarchy.</span></span> <span data-ttu-id="1feaf-104">本例在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库中创建该表，但这是可选操作。</span><span class="sxs-lookup"><span data-stu-id="1feaf-104">The example creates the table in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, but that is optional.</span></span> <span data-ttu-id="1feaf-105">为了简化该示例，此表仅包含五列：</span><span class="sxs-lookup"><span data-stu-id="1feaf-105">To keep the example simple, this table includes only five columns:</span></span>  
  
-   <span data-ttu-id="1feaf-106">OrgNode 是一个存储层次结构关系的 `hierarchyid` 列。</span><span class="sxs-lookup"><span data-stu-id="1feaf-106">OrgNode is a `hierarchyid` column that stores the hierarchical relationship.</span></span>  
  
-   <span data-ttu-id="1feaf-107">OrgLevel 是一个计算列，它基于存储层次结构中的各节点级别的 OrgNode 列。</span><span class="sxs-lookup"><span data-stu-id="1feaf-107">OrgLevel is a computed column, based on the OrgNode column that stores each nodes level in the hierarchy.</span></span> <span data-ttu-id="1feaf-108">它将用于广度优先索引。</span><span class="sxs-lookup"><span data-stu-id="1feaf-108">It will be used for a breadth-first index.</span></span>  
  
-   <span data-ttu-id="1feaf-109">EmployeeID 包含用于诸如工资单等应用程序的典型雇员标识号。</span><span class="sxs-lookup"><span data-stu-id="1feaf-109">EmployeeID contains the typical employee identification number that is used for applications such as payroll.</span></span> <span data-ttu-id="1feaf-110">在新应用程序的开发过程中，应用程序可以使用 OrgNode 列，不需要这个单独的 EmployeeID 列。</span><span class="sxs-lookup"><span data-stu-id="1feaf-110">In new application development, applications can use the OrgNode column and this separate EmployeeID column is not needed.</span></span>  
  
-   <span data-ttu-id="1feaf-111">EmpName 包含雇员的姓名。</span><span class="sxs-lookup"><span data-stu-id="1feaf-111">EmpName contains the name of the employee.</span></span>  
  
-   <span data-ttu-id="1feaf-112">Title 包含雇员的职位。</span><span class="sxs-lookup"><span data-stu-id="1feaf-112">Title contains the title of the employee.</span></span>  
  
### <a name="to-create-the-employeeorg-table"></a><span data-ttu-id="1feaf-113">创建 EmployeeOrg 表</span><span class="sxs-lookup"><span data-stu-id="1feaf-113">To create the EmployeeOrg table</span></span>  
  
1.  <span data-ttu-id="1feaf-114">在“查询编辑器”窗口中，运行以下代码来创建 `EmployeeOrg` 表。</span><span class="sxs-lookup"><span data-stu-id="1feaf-114">In a Query Editor window, run the following code to create the `EmployeeOrg` table.</span></span> <span data-ttu-id="1feaf-115">将 `OrgNode` 列指定为具有聚集索引的主键，即创建了深度优先索引：</span><span class="sxs-lookup"><span data-stu-id="1feaf-115">Specifying the `OrgNode` column as the primary key with a clustered index will create a depth-first index:</span></span>  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    CREATE TABLE HumanResources.EmployeeOrg  
    (  
       OrgNode hierarchyid PRIMARY KEY CLUSTERED,  
       OrgLevel AS OrgNode.GetLevel(),  
       EmployeeID int UNIQUE NOT NULL,  
       EmpName varchar(20) NOT NULL,  
       Title varchar(20) NULL  
    ) ;  
    GO  
    ```  
  
2.  <span data-ttu-id="1feaf-116">运行下面的代码，对 `OrgLevel` 和 `OrgNode` 列创建组合索引，以便支持高效的广度优先搜索：</span><span class="sxs-lookup"><span data-stu-id="1feaf-116">Run the following code to create a composite index on the `OrgLevel` and `OrgNode` columns to support efficient breadth-first searches:</span></span>  
  
    ```  
    CREATE UNIQUE INDEX EmployeeOrgNc1   
    ON HumanResources.EmployeeOrg(OrgLevel, OrgNode) ;  
    GO  
    ```  
  
 <span data-ttu-id="1feaf-117">现在即可为该表填充数据。</span><span class="sxs-lookup"><span data-stu-id="1feaf-117">The table is now ready for data.</span></span> <span data-ttu-id="1feaf-118">下一个任务将通过使用分层方法来填充该表。</span><span class="sxs-lookup"><span data-stu-id="1feaf-118">The next task will populate the table by using hierarchical methods.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="1feaf-119">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="1feaf-119">Next Task in Lesson</span></span>  
 [<span data-ttu-id="1feaf-120">使用分层方法填充层次结构表</span><span class="sxs-lookup"><span data-stu-id="1feaf-120">Populating a Hierarchical Table Using Hierarchical Methods</span></span>](lesson-2-2-populating-a-hierarchical-table-using-hierarchical-methods.md)  
  
  
