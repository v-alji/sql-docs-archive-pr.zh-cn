---
title: FOR XML AUTO 查询在90或更高版本的兼容模式下返回派生表引用 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- FOR XML AUTO [SQL Server]
ms.assetid: 10c32f06-f7e1-40e0-8f79-6d921f2bef1d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 702cb2ca1d437dff03cee09c98d72082500709d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591745"
---
# <a name="for-xml-auto-queries-return-derived-table-references-in-90-or-later-compatibility-modes"></a><span data-ttu-id="50c3e-102">在 90 或更高的兼容模式下，FOR XML AUTO 查询返回派生表引用</span><span class="sxs-lookup"><span data-stu-id="50c3e-102">FOR XML AUTO queries return derived table references in 90 or later compatibility modes</span></span>
  <span data-ttu-id="50c3e-103">当数据库兼容级别设置为 90 或更高时，在 AUTO 模式下执行的 FOR XML 查询将返回针对派生表别名的引用。</span><span class="sxs-lookup"><span data-stu-id="50c3e-103">When the database compatibility level is set to 90 or later, FOR XML queries that execute in AUTO mode return references to derived table aliases.</span></span> <span data-ttu-id="50c3e-104">当兼容级别设置为 80 时，FOR XML AUTO 查询将返回针对定义派生表的基表的引用。</span><span class="sxs-lookup"><span data-stu-id="50c3e-104">When the compatibility level is set to 80, FOR XML AUTO queries return references to the base tables that define a derived table.</span></span>  
  
## <a name="component"></a><span data-ttu-id="50c3e-105">组件</span><span class="sxs-lookup"><span data-stu-id="50c3e-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="50c3e-106">说明</span><span class="sxs-lookup"><span data-stu-id="50c3e-106">Description</span></span>  
 <span data-ttu-id="50c3e-107">例如，请考虑下表：</span><span class="sxs-lookup"><span data-stu-id="50c3e-107">For example, consider the following table:</span></span>  
  
```  
CREATE TABLE Test(id int);  
INSERT INTO Test VALUES(1);  
INSERT INTO Test VALUES(2);  
```  
  
 <span data-ttu-id="50c3e-108">下面包括派生表的查询在兼容级别分别为 80、90 或更高时产生不同的结果：</span><span class="sxs-lookup"><span data-stu-id="50c3e-108">The following query, which includes a derived table, produces different results under compatibility levels 80, 90, or later:</span></span>  
  
```  
SELECT * FROM   
   (SELECT a.id AS a, b.id AS b   
    FROM Test a JOIN Test b ON a.id=b.id)  
AS DerivedTest   
FOR XML AUTO;  
```  
  
 <span data-ttu-id="50c3e-109">当兼容级别为 80 时，查询返回以下结果。</span><span class="sxs-lookup"><span data-stu-id="50c3e-109">Under compatibility level 80, the query returns the following results.</span></span> <span data-ttu-id="50c3e-110">结果引用派生表的基表别名 `a` 和 `b`，而非派生表别名。</span><span class="sxs-lookup"><span data-stu-id="50c3e-110">The results reference the base table aliases `a` and `b` of the derived table instead of the derived table alias.</span></span>  
  
```  
<a a="1"><b b="1"/></a><a a="2"><b b="2"/></a>  
```  
  
 <span data-ttu-id="50c3e-111">当兼容级别为 90 或更高时，查询返回针对派生表别名 `DerivedTest` 的引用，而非针对派生表基表的引用。</span><span class="sxs-lookup"><span data-stu-id="50c3e-111">Under compatibility level 90 or later, the query returns references to the derived table alias `DerivedTest` instead of to the derived table's base tables.</span></span>  
  
```  
<DerivedTest a="1" b="1"/><DerivedTest a="2" b="2"/>  
```  
  
## <a name="corrective-action"></a><span data-ttu-id="50c3e-112">纠正措施</span><span class="sxs-lookup"><span data-stu-id="50c3e-112">Corrective Action</span></span>  
 <span data-ttu-id="50c3e-113">根据要求修改应用程序，以解决 FOR XML AUTO 查询（包括派生表并且在 90 或更高的兼容级别下运行）的结果发生变化这一问题。</span><span class="sxs-lookup"><span data-stu-id="50c3e-113">Modify your application as required to account for the changes in results of FOR XML AUTO queries that include derived tables and that run under compatibility level 90 or later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50c3e-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="50c3e-114">See Also</span></span>  
 <span data-ttu-id="50c3e-115">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="50c3e-115">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="50c3e-116">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="50c3e-116">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
