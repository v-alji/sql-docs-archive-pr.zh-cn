---
title: 排除重复行 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- row duplicates [SQL Server]
- duplicate rows
- row excluded in search [SQL Server]
- result sets [SQL Server], duplicate values
- excluding rows
ms.assetid: ab35a363-421d-4665-946b-ae3f6397af50
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3b396f2738f6895684d828884d4822ea9165e0a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590497"
---
# <a name="exclude-duplicate-rows-visual-database-tools"></a><span data-ttu-id="7f2ca-102">排除重复行 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="7f2ca-102">Exclude Duplicate Rows (Visual Database Tools)</span></span>
  <span data-ttu-id="7f2ca-103">如果希望在结果集中看到的值都是唯一的，则可指定要从结果集中排除重复项。</span><span class="sxs-lookup"><span data-stu-id="7f2ca-103">If you want to see only unique values in a result set, you can specify that you want to exclude duplicates from the result set.</span></span>  
  
### <a name="to-exclude-duplicate-rows-from-the-result-set"></a><span data-ttu-id="7f2ca-104">从结果集中排除重复行</span><span class="sxs-lookup"><span data-stu-id="7f2ca-104">To exclude duplicate rows from the result set</span></span>  
  
1.  <span data-ttu-id="7f2ca-105">右键单击“关系图”窗格的背景，再从快捷菜单中选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="7f2ca-105">Right-click the background of the Diagram pane, then choose **Properties** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="7f2ca-106">在“属性”窗口，单击“DISTINCT 值”  ，再将其值设置为“是”  。</span><span class="sxs-lookup"><span data-stu-id="7f2ca-106">In the Property window, click **Distinct values** and set the value to **Yes**.</span></span>  
  
     <span data-ttu-id="7f2ca-107">查询和视图设计器将在 SQL 语句中显示列的列表之前插入关键字 DISTINCT。</span><span class="sxs-lookup"><span data-stu-id="7f2ca-107">The Query and View Designer inserts the keyword DISTINCT in front of the list of display columns in the SQL statement.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7f2ca-108">如果使用 DISTINCT 关键字，则可能无法在结果窗格中修改结果集。</span><span class="sxs-lookup"><span data-stu-id="7f2ca-108">If you use the DISTINCT keyword you may not be able to modify the result set in the results pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f2ca-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7f2ca-109">See Also</span></span>  
 <span data-ttu-id="7f2ca-110">[指定 Visual Database Tools &#40;搜索条件&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="7f2ca-110">[Specify Search Criteria &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="7f2ca-111">对查询结果进行排序和分组 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="7f2ca-111">Sort and Group Query Results &#40;Visual Database Tools&#41;</span></span>](sort-and-group-query-results-visual-database-tools.md)  
  
  
