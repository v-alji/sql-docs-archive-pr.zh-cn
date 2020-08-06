---
title: 联接筛选器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server replication], join
- publications [SQL Server replication], join filters
- merge replication join filters [SQL Server replication]
- join filters
ms.assetid: dd78fd8f-56e3-4582-9abd-6bc25c91e075
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b97e7d7b53e6a3fdb242d1272e013bbd45f0ed17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576684"
---
# <a name="join-filters"></a><span data-ttu-id="4c9af-102">Join Filters</span><span class="sxs-lookup"><span data-stu-id="4c9af-102">Join Filters</span></span>
  <span data-ttu-id="4c9af-103">联接筛选器允许根据发布中相关表的筛选方式对表进行筛选。</span><span class="sxs-lookup"><span data-stu-id="4c9af-103">A join filter allows a table to be filtered based on how a related table in the publication is filtered.</span></span> <span data-ttu-id="4c9af-104">通常用参数化筛选器筛选父表，然后采用与定义各表之间联接完全相同的方式来定义联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="4c9af-104">Typically a parent table is filtered using a parameterized filter; then one or more join filters are defined in much the same way that you define a join between tables.</span></span> <span data-ttu-id="4c9af-105">联接筛选器扩展了参数化筛选器，以便仅复制与联接筛选器子句匹配的相关表中的数据。</span><span class="sxs-lookup"><span data-stu-id="4c9af-105">The join filters extend the parameterized filter so that the data in the related tables is only replicated if it matches the join filter clause.</span></span>  
  
 <span data-ttu-id="4c9af-106">联接筛选器通常遵循为其应用到的表定义的主键/外键关系，但并不严格受限于主键/外键关系。</span><span class="sxs-lookup"><span data-stu-id="4c9af-106">Join filters typically follow the primary key/foreign key relationships defined for the tables to which they are applied, but they are not limited strictly to primary key/foreign key relationships.</span></span> <span data-ttu-id="4c9af-107">联接筛选器可以基于任何逻辑比较两表中相关数据。</span><span class="sxs-lookup"><span data-stu-id="4c9af-107">The join filter can be based on any logic that compares related data in two tables.</span></span>  
  
 <span data-ttu-id="4c9af-108">请考虑下列 [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)] 示例数据库中的表，这些表通过主键与外键的关系相互关联：</span><span class="sxs-lookup"><span data-stu-id="4c9af-108">Consider the following tables in the [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)] sample database, which are related through primary key to foreign key relationships:</span></span>  
  
-   <span data-ttu-id="4c9af-109">**HumanResources.Employee**</span><span class="sxs-lookup"><span data-stu-id="4c9af-109">**HumanResources.Employee**</span></span>  
  
-   <span data-ttu-id="4c9af-110">**Sales.SalesOrderHeader**</span><span class="sxs-lookup"><span data-stu-id="4c9af-110">**Sales.SalesOrderHeader**</span></span>  
  
-   <span data-ttu-id="4c9af-111">**Sales.SalesOrderDetail**</span><span class="sxs-lookup"><span data-stu-id="4c9af-111">**Sales.SalesOrderDetail**</span></span>  
  
 <span data-ttu-id="4c9af-112">这些表可用在支持移动销售队伍的应用程序中，但必须经过筛选，以使 **HumanResources.Employee** 表中的各销售人员只接收与其客户订单相关的数据。</span><span class="sxs-lookup"><span data-stu-id="4c9af-112">These tables could be used in an application to support a mobile sales force, but they must be filtered so that each sales person in the **HumanResources.Employee** table receives only the data relevant to their customers' orders.</span></span>  
  
 <span data-ttu-id="4c9af-113">第一个步骤是在父表上定义参数化筛选器。本例中的父表是 **HumanResources.Employee** 表。</span><span class="sxs-lookup"><span data-stu-id="4c9af-113">The first step is to define a parameterized filter on the parent table, which in this example is the **HumanResources.Employee** table.</span></span> <span data-ttu-id="4c9af-114">这个表包括 **LoginID**列，该列包含 *domain\login*格式的各个雇员登录名。</span><span class="sxs-lookup"><span data-stu-id="4c9af-114">This table includes the column **LoginID**, which contains the login for each employee in the form *domain\login*.</span></span> <span data-ttu-id="4c9af-115">若要筛选该表以使每个雇员只接收与他们相关的数据，请指定一个参数化筛选器子句：</span><span class="sxs-lookup"><span data-stu-id="4c9af-115">To filter this table so that each employee receives only the data related to them, specify a parameterized filter clause of:</span></span>  
  
```  
LoginID = SUSER_SNAME()  
```  
  
 <span data-ttu-id="4c9af-116">此筛选器确保每个雇员的订阅仅包含 **HumanResources.Employee** 表中与该雇员相关的数据（这在本例中是一个单行）。</span><span class="sxs-lookup"><span data-stu-id="4c9af-116">This filter ensures that each employee's subscription only contains data from the **HumanResources.Employee** table that is relevant to that employee (which in this case is a single row).</span></span> <span data-ttu-id="4c9af-117">有关详细信息，请参阅 [参数化行筛选器](parameterized-filters-parameterized-row-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="4c9af-117">For more information, see [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 <span data-ttu-id="4c9af-118">下一步是将此筛选器扩展到各相关表，所使用的语法类似于指定两表间联接所使用的语法。</span><span class="sxs-lookup"><span data-stu-id="4c9af-118">The next step is to extend this filter to each of the related tables, using syntax similar to that used to specify a join between two tables.</span></span> <span data-ttu-id="4c9af-119">第一个联接筛选器子句是：</span><span class="sxs-lookup"><span data-stu-id="4c9af-119">The first join filter clause is:</span></span>  
  
```  
Employee.EmployeeID = SalesOrderHeader.SalesPersonID  
```  
  
 <span data-ttu-id="4c9af-120">这个子句确保订阅仅包含与每个销售人员相关的订单数据。</span><span class="sxs-lookup"><span data-stu-id="4c9af-120">This ensures the subscription contains only the order data relevant to each sales person.</span></span> <span data-ttu-id="4c9af-121">第二个联接筛选器子句是：</span><span class="sxs-lookup"><span data-stu-id="4c9af-121">The second join filter clause is:</span></span>  
  
```  
SalesOrderHeader.SalesOrderID = SalesOrderDetail.SalesOrderID  
```  
  
 <span data-ttu-id="4c9af-122">这个子句确保订阅仅包含与每个销售人员订单数据相关的详细信息数据。</span><span class="sxs-lookup"><span data-stu-id="4c9af-122">This ensures the subscription contains only the detail data related to the order data for each sales person.</span></span> <span data-ttu-id="4c9af-123">此例说明的是在各点处联接的单个表。也可以在各点联接多个表。</span><span class="sxs-lookup"><span data-stu-id="4c9af-123">This example shows a single table being joined at each point; it is also possible to join more than one table at each point.</span></span>  
  
 <span data-ttu-id="4c9af-124">通过新建发布向导和 **“发布属性”** 对话框可一次一个地添加联接筛选器，也可用编程的方式添加它们。</span><span class="sxs-lookup"><span data-stu-id="4c9af-124">Join filters can be added one at a time through the New Publication Wizard and the **Publication Properties** dialog box, or they can be added programmatically.</span></span> <span data-ttu-id="4c9af-125">也可用新建发布向导自动生成联接筛选器：为一个表指定一个行筛选器，并将联接筛选器应用于所有相关表。</span><span class="sxs-lookup"><span data-stu-id="4c9af-125">They can also be generated automatically through the New Publication Wizard: you specify a row filter for a table and join filters are applied to all related tables.</span></span> <span data-ttu-id="4c9af-126">有关详细信息，请参阅[定义和修改合并项目间的联接筛选器](../publish/define-and-modify-a-join-filter-between-merge-articles.md)，[自动生成合并项目间的一组联接筛选器 (SQL Server Management Studio)](../publish/automatically-generate-join-filters-between-merge-articles.md)和[定义项目](../publish/define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="4c9af-126">For more information, see [Define and Modify a Join Filter Between Merge Articles](../publish/define-and-modify-a-join-filter-between-merge-articles.md), [Automatically Generate a Set of Join Filters Between Merge Articles &#40;SQL Server Management Studio&#41;](../publish/automatically-generate-join-filters-between-merge-articles.md), and [Define an Article](../publish/define-an-article.md).</span></span>  
  
## <a name="optimizing-join-filter-performance"></a><span data-ttu-id="4c9af-127">优化联接筛选器性能</span><span class="sxs-lookup"><span data-stu-id="4c9af-127">Optimizing Join Filter Performance</span></span>  
 <span data-ttu-id="4c9af-128">可以按照以下指南来优化联接筛选器性能：</span><span class="sxs-lookup"><span data-stu-id="4c9af-128">Join filter performance can be optimized by following these guidelines:</span></span>  
  
-   <span data-ttu-id="4c9af-129">限制联接筛选器层次结构中的表数。</span><span class="sxs-lookup"><span data-stu-id="4c9af-129">Limit the number of tables in the join filter hierarchy.</span></span>  
  
     <span data-ttu-id="4c9af-130">联接筛选器可关联的表数目不限，但有大量表的筛选器会严重影响合并处理过程的性能。</span><span class="sxs-lookup"><span data-stu-id="4c9af-130">Join Filters can involve an unlimited number of tables, but filters with a large number of tables can significantly impact performance during merge processing.</span></span> <span data-ttu-id="4c9af-131">如果要生成五个或更多表的联接筛选器，请考虑其他解决方案：不筛选小表、不会发生更改的表或主要是查找表的表。</span><span class="sxs-lookup"><span data-stu-id="4c9af-131">If you are generating join filters of five or more tables, consider other solutions: do not filter tables that are small, not subject to change, or are primarily lookup tables.</span></span> <span data-ttu-id="4c9af-132">仅在必须在订阅中分区的表之间使用联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="4c9af-132">Use join filters only between tables that must be partitioned among subscriptions.</span></span>  
  
-   <span data-ttu-id="4c9af-133">在适当处将“联接唯一键”  选项设置为 **True** 。</span><span class="sxs-lookup"><span data-stu-id="4c9af-133">Set the **join unique key** option to **True** where appropriate.</span></span>  
  
     <span data-ttu-id="4c9af-134">如果父级中的联接列是唯一的，则合并进程的性能有较大的优化空间。</span><span class="sxs-lookup"><span data-stu-id="4c9af-134">The merge process has special performance optimizations available if the joined column in the parent is unique.</span></span> <span data-ttu-id="4c9af-135">如果联接条件是依据某个唯一列，请为联接筛选器设置“联接唯一键”  选项。</span><span class="sxs-lookup"><span data-stu-id="4c9af-135">If the join condition is based on a unique column, set the **join unique key** option for the join filter.</span></span> <span data-ttu-id="4c9af-136">有关设置此选项的详细信息，请参阅前一部分中列出的操作指南主题。</span><span class="sxs-lookup"><span data-stu-id="4c9af-136">For information about setting this option, see the how-to topics listed in the previous section.</span></span>  
  
-   <span data-ttu-id="4c9af-137">确保为联接筛选器中引用的列建立索引。</span><span class="sxs-lookup"><span data-stu-id="4c9af-137">Ensure that the columns referenced in join filters are indexed.</span></span>  
  
     <span data-ttu-id="4c9af-138">如果为筛选器中引用的列建立了索引，复制就可以更高效地处理筛选器。</span><span class="sxs-lookup"><span data-stu-id="4c9af-138">If the columns referenced in the filter are indexed, replication can process the filters more efficiently.</span></span>  
  
-   <span data-ttu-id="4c9af-139">请不要模仿联接筛选器创建行筛选器。</span><span class="sxs-lookup"><span data-stu-id="4c9af-139">Do not create row filters that mimic join filters.</span></span>  
  
     <span data-ttu-id="4c9af-140">使用 WHERE 子句中的子查询来模仿联接筛选器创建行筛选器是有可能的，例如：</span><span class="sxs-lookup"><span data-stu-id="4c9af-140">It is possible to create row filters that mimic join filters by using a subquery in a WHERE clause, such as:</span></span>  
  
    ```  
    WHERE Customer.SalesPersonID IN (SELECT EmployeeID FROM Employee WHERE LoginID = SUSER_SNAME())   
    ```  
  
     <span data-ttu-id="4c9af-141">强烈建议在联接筛选器中而不要在子查询中表示所有这类逻辑。</span><span class="sxs-lookup"><span data-stu-id="4c9af-141">It is strongly recommended that all such logic be expressed in a join filter rather than a subquery.</span></span> <span data-ttu-id="4c9af-142">如果您的应用程序要求行筛选器使用子查询，请确保子查询仅引用不发生更改的查找数据。</span><span class="sxs-lookup"><span data-stu-id="4c9af-142">If your application requires a row filter to use a subsquery, ensure that the subquery only references lookup data that does not change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c9af-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4c9af-143">See Also</span></span>  
 <span data-ttu-id="4c9af-144">[为合并复制筛选已发布数据](filter-published-data-for-merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="4c9af-144">[Filter Published Data for Merge Replication](filter-published-data-for-merge-replication.md) </span></span>  
 [<span data-ttu-id="4c9af-145">参数化行筛选器</span><span class="sxs-lookup"><span data-stu-id="4c9af-145">Parameterized Row Filters</span></span>](parameterized-filters-parameterized-row-filters.md)  
  
  
