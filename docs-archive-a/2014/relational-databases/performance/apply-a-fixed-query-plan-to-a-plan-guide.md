---
title: 将固定查询计划应用到计划指南 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: bbf401f9-af7c-48e7-8a43-bf25e8af2fd7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 318955c4d0550e311873d8b4a6f79f72e04ac8af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687788"
---
# <a name="apply-a-fixed-query-plan-to-a-plan-guide"></a><span data-ttu-id="10531-102">将现有查询计划应用到计划指南</span><span class="sxs-lookup"><span data-stu-id="10531-102">Apply a Fixed Query Plan to a Plan Guide</span></span>
  <span data-ttu-id="10531-103">您可以将现有查询计划应用到 OBJECT 或 SQL 类型的计划指南。</span><span class="sxs-lookup"><span data-stu-id="10531-103">You can apply a fixed query plan to a plan guide of type OBJECT or SQL.</span></span> <span data-ttu-id="10531-104">当您注意到对于特定查询现有的执行计划比优化器选择的计划执行得更好时，应用现有查询计划的计划指南将非常有用。</span><span class="sxs-lookup"><span data-stu-id="10531-104">Plan guides that apply a fixed query plan are useful when you know about an existing execution plan that performs better than the one selected by the optimizer for a particular query.</span></span>  
  
 <span data-ttu-id="10531-105">下面的示例为简单的临时 SQL 语句创建一个计划指南。</span><span class="sxs-lookup"><span data-stu-id="10531-105">The following example creates a plan guide for a simple ad hoc SQL statement.</span></span> <span data-ttu-id="10531-106">在计划指南中，直接在 `@hints` 参数中为查询指定 XML 显示计划，从而为该语句提供了所需的查询计划。</span><span class="sxs-lookup"><span data-stu-id="10531-106">The desired query plan for this statement is provided in the plan guide by specifying the XML Showplan for the query directly in the `@hints` parameter.</span></span> <span data-ttu-id="10531-107">该示例首先通过执行 SQL 语句在计划缓存中生成一个计划。</span><span class="sxs-lookup"><span data-stu-id="10531-107">The example first executes the SQL statement to generate a plan in the plan cache.</span></span> <span data-ttu-id="10531-108">对于此示例，假定所生成的计划就是所需的计划，不需要做进一步的查询优化。</span><span class="sxs-lookup"><span data-stu-id="10531-108">For the purposes of this example, it is assumed that the generated plan is the desired plan and no additional query tuning is required.</span></span> <span data-ttu-id="10531-109">此查询的 XML 显示计划可通过查询 `sys.dm_exec_query_stats`、 `sys.dm_exec_sql_text`和 `sys.dm_exec_text_query_plan` 动态管理视图获得，并可以分配给 `@xml_showplan` 变量。</span><span class="sxs-lookup"><span data-stu-id="10531-109">The XML Showplan for the query is obtained by querying the `sys.dm_exec_query_stats`, `sys.dm_exec_sql_text`, and `sys.dm_exec_text_query_plan` dynamic management views and is assigned to the `@xml_showplan` variable.</span></span> <span data-ttu-id="10531-110">然后，将 `@xml_showplan` 变量传递给 `sp_create_plan_guide` 语句中的 `@hints` 参数。</span><span class="sxs-lookup"><span data-stu-id="10531-110">The `@xml_showplan` variable is then passed to the `sp_create_plan_guide` statement in the `@hints` parameter.</span></span> <span data-ttu-id="10531-111">也可以使用 [sp_create_plan_guide_from_handle](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) 存储过程从计划缓存中的查询计划中创建计划指南。</span><span class="sxs-lookup"><span data-stu-id="10531-111">Or, you can create a plan guide from a query plan in the plan cache by using the [sp_create_plan_guide_from_handle](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) stored procedure.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;  
GO  
DECLARE @xml_showplan nvarchar(max);  
SET @xml_showplan = (SELECT query_plan  
    FROM sys.dm_exec_query_stats AS qs   
    CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
    CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, DEFAULT, DEFAULT) AS qp  
    WHERE st.text LIKE N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;%');  
  
EXEC sp_create_plan_guide   
    @name = N'Guide1_from_XML_showplan',   
    @stmt = N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = @xml_showplan;  
GO  
```  
  
  
