---
title: 选择与值不匹配的行 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search conditions [SQL Server], rows not matching value
- row not matching value [SQL Server]
- NOT operator [Visual Database Tools]
- search criteria [SQL Server], rows not matching value
ms.assetid: 19898578-7b2f-401c-bb8f-9f2a017efdf7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 412ec93cbfedc87e92da9e86c7e4c7455919722a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691001"
---
# <a name="select-rows-that-do-not-match-a-value-visual-database-tools"></a><span data-ttu-id="ea55a-102">选择与值不匹配的行 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="ea55a-102">Select Rows That Do Not Match a Value (Visual Database Tools)</span></span>
  <span data-ttu-id="ea55a-103">若要查找与某值不匹配的行，可以使用 NOT 运算符。</span><span class="sxs-lookup"><span data-stu-id="ea55a-103">To find rows that do not match a value, use the NOT operator.</span></span>  
  
### <a name="to-find-rows-that-do-not-match-a-value"></a><span data-ttu-id="ea55a-104">查找与某值不匹配的行</span><span class="sxs-lookup"><span data-stu-id="ea55a-104">To find rows that do not match a value</span></span>  
  
1.  <span data-ttu-id="ea55a-105">如果尚未指定搜索条件，请将要在搜索条件内使用的列或表达式添加到 [“条件”窗格](visual-database-tools.md)中。</span><span class="sxs-lookup"><span data-stu-id="ea55a-105">If you have not done so already, add the columns or expressions that you want to use within your search condition to the [Criteria pane](visual-database-tools.md).</span></span>  
  
2.  <span data-ttu-id="ea55a-106">找到包含要搜索的数据列或表达式的行，然后在“筛选器”  网格列中，顺序输入 NOT 运算符和搜索值。</span><span class="sxs-lookup"><span data-stu-id="ea55a-106">Locate the row containing the data column or expression to search, and then in the **Filter** grid column, enter the NOT operator followed by a search value.</span></span>  
  
 <span data-ttu-id="ea55a-107">例如，若要在 `products` 表中查找产品代码列中的值以“A”之外的其他字符开头的所有行，则可以输入如下搜索条件：</span><span class="sxs-lookup"><span data-stu-id="ea55a-107">For example, to find all the rows in a `products` table where the values in the product code column begin with a character other than "A," you can enter a search condition such as the following:</span></span>  
  
```  
NOT LIKE 'A%'  
```  
  
## <a name="see-also"></a><span data-ttu-id="ea55a-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ea55a-108">See Also</span></span>  
 <span data-ttu-id="ea55a-109">[&#40;Visual Database Tools&#41;中输入搜索值的规则](rules-for-entering-search-values-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ea55a-109">[Rules for Entering Search Values &#40;Visual Database Tools&#41;](rules-for-entering-search-values-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="ea55a-110">指定搜索条件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="ea55a-110">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
