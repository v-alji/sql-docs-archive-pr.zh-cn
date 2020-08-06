---
title: 使用未命名参数创建查询 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- unnamed parameters
- parameters [SQL Server], unnamed
ms.assetid: 5f4b664b-3d3d-4d07-a0e7-791d78743504
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0ea53afd1fa4d44390f5805d6b28494428608b90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577192"
---
# <a name="create-queries-with-unnamed-parameters-visual-database-tools"></a><span data-ttu-id="00849-102">使用未命名参数创建查询 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="00849-102">Create Queries with Unnamed Parameters (Visual Database Tools)</span></span>
  <span data-ttu-id="00849-103">可通过将问号 (?) 指定为文字值的占位符来使用未命名参数创建查询。</span><span class="sxs-lookup"><span data-stu-id="00849-103">You can create a query with an unnamed parameter by specifying a question mark (?) as a placeholder for a literal value.</span></span> <span data-ttu-id="00849-104">查询和视图设计器将为未命名参数指定临时名称。</span><span class="sxs-lookup"><span data-stu-id="00849-104">Query and View Designer will give it a temporary name.</span></span> <span data-ttu-id="00849-105">可根据需要在查询中指定任意数目的未命名参数。</span><span class="sxs-lookup"><span data-stu-id="00849-105">You can specify as many unnamed parameters in the query as you need.</span></span>  
  
 <span data-ttu-id="00849-106">在查询和视图设计器中运行查询时，将显示“查询参数”对话框，同时显示临时名称。</span><span class="sxs-lookup"><span data-stu-id="00849-106">When you run the query in the Query and View Designer, the Query Parameters Dialog Box is displayed with the temporary name.</span></span>  
  
### <a name="to-specify-an-unnamed-parameter"></a><span data-ttu-id="00849-107">指定未命名参数</span><span class="sxs-lookup"><span data-stu-id="00849-107">To specify an unnamed parameter</span></span>  
  
1.  <span data-ttu-id="00849-108">将要搜索的列或表达式添加到 [“条件”窗格](visual-database-tools.md)中。</span><span class="sxs-lookup"><span data-stu-id="00849-108">Add the columns or expressions that you want to search to the [Criteria pane](visual-database-tools.md).</span></span> <span data-ttu-id="00849-109">如果不希望搜索列或表达式出现在查询输出中，则将其从输出列中移除。</span><span class="sxs-lookup"><span data-stu-id="00849-109">If you do not want the search columns or expressions to appear in the query output, remove them as output columns.</span></span>  
  
2.  <span data-ttu-id="00849-110">找到包含要搜索的数据列或表达式的行，然后在“筛选器”  网格列中输入一个问号 (?)。</span><span class="sxs-lookup"><span data-stu-id="00849-110">Locate the row containing the data column or expression to search, and then in the **Filter** grid column, enter a question mark (?).</span></span>  
  
     <span data-ttu-id="00849-111">默认情况下，查询和视图设计器将添加“=”运算符。</span><span class="sxs-lookup"><span data-stu-id="00849-111">By default, the Query and View Designer adds the "=" operator.</span></span> <span data-ttu-id="00849-112">不过，您可以对该单元格进行编辑，以替换“>”、“<”或任何其他 SQL 比较运算符。</span><span class="sxs-lookup"><span data-stu-id="00849-112">However, you can edit the cell to substitute ">", "<", or any other SQL comparison operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00849-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="00849-113">See Also</span></span>  
 [<span data-ttu-id="00849-114">使用参数进行查询 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="00849-114">Query with Parameters &#40;Visual Database Tools&#41;</span></span>](query-with-parameters-visual-database-tools.md)  
  
  
