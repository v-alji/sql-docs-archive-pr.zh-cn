---
title: ORDER BY 子句中的列别名不能以表别名作为前缀 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- aliases [SQL Server], columns
ms.assetid: fee7328f-6e8d-4005-930b-56fb6f17e0b2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 44333d778753a2f8761d32d181681b798e3bc409
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586192"
---
# <a name="column-aliases-in-order-by-clause-cannot-be-prefixed-by-table-alias"></a><span data-ttu-id="e194b-102">ORDER BY 子句中的列别名不能以表别名作为前缀</span><span class="sxs-lookup"><span data-stu-id="e194b-102">Column aliases in ORDER BY clause cannot be prefixed by table alias</span></span>
  <span data-ttu-id="e194b-103">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更高版本中，ORDER BY 子句中的列别名不能以表别名作为前缀。</span><span class="sxs-lookup"><span data-stu-id="e194b-103">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later, column aliases in the ORDER BY clause cannot be prefixed by the table alias.</span></span>  
  
## <a name="component"></a><span data-ttu-id="e194b-104">组件</span><span class="sxs-lookup"><span data-stu-id="e194b-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="e194b-105">说明</span><span class="sxs-lookup"><span data-stu-id="e194b-105">Description</span></span>  
 <span data-ttu-id="e194b-106">例如，以下查询可在 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 中正常执行，而在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 中却返回错误。</span><span class="sxs-lookup"><span data-stu-id="e194b-106">For example, the following query executes in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], but returns an error in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY p.l  
```  
  
 <span data-ttu-id="e194b-107">[!INCLUDE[ssDEversion10](../../includes/ssdeversion10-md.md)] 不会将 `p.l` 子句中的 `ORDER BY` 与表中的某个有效列匹配。</span><span class="sxs-lookup"><span data-stu-id="e194b-107">The [!INCLUDE[ssDEversion10](../../includes/ssdeversion10-md.md)] does not match `p.l` in the `ORDER BY` clause to a valid column in the table.</span></span>  
  
### <a name="exception"></a><span data-ttu-id="e194b-108">异常</span><span class="sxs-lookup"><span data-stu-id="e194b-108">Exception</span></span>  
 <span data-ttu-id="e194b-109">如果 ORDER BY 子句中指定的带有前缀的列别名在指定的表中是有效的列名，则该查询在执行时不会出错；在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中，该语句的语义可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="e194b-109">If the prefixed column alias that is specified in the ORDER BY clause is a valid column name in the specified table, the query executes without error; in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the semantics of the statement might be different.</span></span> <span data-ttu-id="e194b-110">例如，下面的语句中指定的列别名 (`id`) 在 `sysobjects` 表中是有效的列名。</span><span class="sxs-lookup"><span data-stu-id="e194b-110">For example, the column alias (`id`) specified in the following statement is a valid column name in the `sysobjects` table.</span></span> <span data-ttu-id="e194b-111">在 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 中执行该语句时，对结果集排序之后将执行 `CAST` 操作。</span><span class="sxs-lookup"><span data-stu-id="e194b-111">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], when the statement executes, the `CAST` operation is performed after the result set is sorted.</span></span> <span data-ttu-id="e194b-112">也就是说，在排序操作中使用了 `name` 列。</span><span class="sxs-lookup"><span data-stu-id="e194b-112">This means the `name` column is used in the sort operation.</span></span> <span data-ttu-id="e194b-113">在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 中，`CAST` 操作是在排序操作之前执行的。</span><span class="sxs-lookup"><span data-stu-id="e194b-113">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the `CAST` operation occurs before the sort operation.</span></span> <span data-ttu-id="e194b-114">也就是说，在排序操作中使用了表中的 `id` 列，并以意外顺序返回了结果集。</span><span class="sxs-lookup"><span data-stu-id="e194b-114">This means the `id` column in the table is used in the sort operation and returns the result set in an unexpected order.</span></span>  
  
```  
SELECT CAST (o.name AS char(128)) AS id  
FROM sysobjects AS o  
ORDER BY o.id;  
```  
  
## <a name="corrective-action"></a><span data-ttu-id="e194b-115">纠正措施</span><span class="sxs-lookup"><span data-stu-id="e194b-115">Corrective Action</span></span>  
 <span data-ttu-id="e194b-116">可通过下面两种方式之一修改在 ORDER BY 子句中将表别名作为列别名前缀的查询：</span><span class="sxs-lookup"><span data-stu-id="e194b-116">Modify queries that use column aliases prefixed by table aliases in the ORDER BY clause in either of the following ways:</span></span>  
  
-   <span data-ttu-id="e194b-117">尽量不要对 ORDER BY 子句中的列别名加前缀。</span><span class="sxs-lookup"><span data-stu-id="e194b-117">Do not prefix the column alias in the ORDER BY clause, if possible.</span></span>  
  
-   <span data-ttu-id="e194b-118">用列名替换列别名。</span><span class="sxs-lookup"><span data-stu-id="e194b-118">Replace the column alias with the column name.</span></span>  
  
 <span data-ttu-id="e194b-119">例如，下面这两个查询在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 中执行时均不会出错：</span><span class="sxs-lookup"><span data-stu-id="e194b-119">For example, both of the following queries execute without error in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY l  
  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY p.LastName  
```  
  
## <a name="see-also"></a><span data-ttu-id="e194b-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e194b-120">See Also</span></span>  
 <span data-ttu-id="e194b-121">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="e194b-121">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="e194b-122">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="e194b-122">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
