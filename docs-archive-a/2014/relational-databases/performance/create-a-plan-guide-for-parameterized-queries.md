---
title: 为参数化查询创建计划指南 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- parameterized queries, plan guides for
- plan guides [SQL Server], parameterized queries
ms.assetid: b532ae16-66e7-4641-9bc8-b0d805853477
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 565610826f704274724ea05d821205a5b3391060
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591310"
---
# <a name="create-a-plan-guide-for-parameterized-queries"></a><span data-ttu-id="21585-102">为参数化查询创建计划指南</span><span class="sxs-lookup"><span data-stu-id="21585-102">Create a Plan Guide for Parameterized Queries</span></span>
  <span data-ttu-id="21585-103">TEMPLATE 计划指南与参数化为指定形式的独立查询匹配。</span><span class="sxs-lookup"><span data-stu-id="21585-103">A TEMPLATE plan guide matches stand-alone queries that parameterize to a specified form.</span></span>  
  
 <span data-ttu-id="21585-104">以下示例创建一个计划指南，它与被参数化为指定格式的任何查询匹配，并使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 强制执行查询参数化。</span><span class="sxs-lookup"><span data-stu-id="21585-104">The following example creates a plan guide that matches any query that parameterizes to a specified form, and directs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to force parameterization of the query.</span></span> <span data-ttu-id="21585-105">下列两个查询在语法上是等价的，差别只是它们的常量文字值。</span><span class="sxs-lookup"><span data-stu-id="21585-105">The following two queries are syntactically equivalent, but differ only in their constant literal values.</span></span>  
  
```  
SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
    ON h.SalesOrderID = d.SalesOrderID  
WHERE h.SalesOrderID = 45639;  
  
SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
    ON h.SalesOrderID = d.SalesOrderID  
WHERE h.SalesOrderID = 45640;  
```  
  
 <span data-ttu-id="21585-106">下面是参数化格式的查询的计划指南：</span><span class="sxs-lookup"><span data-stu-id="21585-106">Here is the plan guide on the parameterized form of the query:</span></span>  
  
```  
EXEC sp_create_plan_guide   
    @name = N'TemplateGuide1',  
    @stmt = N'SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
              INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
                  ON h.SalesOrderID = d.SalesOrderID  
              WHERE h.SalesOrderID = @0',  
    @type = N'TEMPLATE',  
    @module_or_batch = NULL,  
    @params = N'@0 int',  
    @hints = N'OPTION(PARAMETERIZATION FORCED)';  
```  
  
 <span data-ttu-id="21585-107">在上一个示例中， `@stmt` 参数的值是参数化格式的查询。</span><span class="sxs-lookup"><span data-stu-id="21585-107">In the previous example, the value for the `@stmt` parameter is the parameterized form of the query.</span></span> <span data-ttu-id="21585-108">获取此值以在 sp_create_plan_guide 中使用的唯一可靠方法是使用 [sp_get_query_template](/sql/relational-databases/system-stored-procedures/sp-get-query-template-transact-sql) 系统存储过程。</span><span class="sxs-lookup"><span data-stu-id="21585-108">The only reliable way to obtain this value for use in sp_create_plan_guide is to use the [sp_get_query_template](/sql/relational-databases/system-stored-procedures/sp-get-query-template-transact-sql) system stored procedure.</span></span> <span data-ttu-id="21585-109">以下脚本既可用来获得参数化查询，又可用来为它创建计划指南。</span><span class="sxs-lookup"><span data-stu-id="21585-109">The following script can be used both to obtain the parameterized query and then create a plan guide on it.</span></span>  
  
```  
DECLARE @stmt nvarchar(max);  
DECLARE @params nvarchar(max);  
EXEC sp_get_query_template   
    N'SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
      INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
          ON h.SalesOrderID = d.SalesOrderID  
      WHERE h.SalesOrderID = 45639;',  
    @stmt OUTPUT,   
    @params OUTPUT  
EXEC sp_create_plan_guide N'TemplateGuide1',   
    @stmt,   
    N'TEMPLATE',   
    NULL,   
    @params,   
    N'OPTION(PARAMETERIZATION FORCED)';  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="21585-110">传递到 `@stmt` 的 `sp_get_query_template` 参数中的常量文字值可能会影响为替换该文字的参数选择的数据类型。</span><span class="sxs-lookup"><span data-stu-id="21585-110">The value of the constant literals in the `@stmt` parameter passed to `sp_get_query_template` might affect the data type that is chosen for the parameter that replaces the literal.</span></span> <span data-ttu-id="21585-111">这将影响计划指南的匹配。</span><span class="sxs-lookup"><span data-stu-id="21585-111">This will affect plan guide matching.</span></span> <span data-ttu-id="21585-112">可能必须创建多个计划指南，以处理不同的参数值范围。</span><span class="sxs-lookup"><span data-stu-id="21585-112">You may have to create more than one plan guide to handle different parameter value ranges.</span></span>  
  
 <span data-ttu-id="21585-113">还可以将 TEMPLATE 计划指南与 SQL 计划指南一起使用。</span><span class="sxs-lookup"><span data-stu-id="21585-113">You can also use TEMPLATE plan guides together with SQL plan guides.</span></span> <span data-ttu-id="21585-114">例如，可以创建 TEMPLATE 计划指南以确保参数化查询类。</span><span class="sxs-lookup"><span data-stu-id="21585-114">For example, you can create a TEMPLATE plan guide to make sure that a class of queries is parameterized.</span></span> <span data-ttu-id="21585-115">然后，可以对该参数化形式的查询创建 SQL 计划指南。</span><span class="sxs-lookup"><span data-stu-id="21585-115">You can then create an SQL plan guide on the parameterized form of that query.</span></span>  
  
  
