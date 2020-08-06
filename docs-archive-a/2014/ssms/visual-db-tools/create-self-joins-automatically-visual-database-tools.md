---
title: 自动创建自联接 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- automatic joins
- self-joins
- joins [SQL Server], self
ms.assetid: f9ec90e8-3aad-415c-a5c4-8dfa9540e37f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a428a44d33b5990e849772b43841df472ca7f6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577191"
---
# <a name="create-self-joins-automatically-visual-database-tools"></a><span data-ttu-id="e9e4a-102">自动创建自联接 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e9e4a-102">Create Self-Joins Automatically (Visual Database Tools)</span></span>
  <span data-ttu-id="e9e4a-103">如果表在数据库中有自反关系，则可自动将其与自身联接。</span><span class="sxs-lookup"><span data-stu-id="e9e4a-103">If a table has a reflexive relationship in the database, you can join it to itself automatically.</span></span>  
  
### <a name="to-create-a-self-join-automatically"></a><span data-ttu-id="e9e4a-104">自动创建自联接</span><span class="sxs-lookup"><span data-stu-id="e9e4a-104">To create a self-join automatically</span></span>  
  
1.  <span data-ttu-id="e9e4a-105">将要处理的表添加到 [“关系图”窗格](visual-database-tools.md) 中。</span><span class="sxs-lookup"><span data-stu-id="e9e4a-105">Add to the [Diagram pane](visual-database-tools.md) the table you want to work with.</span></span>  
  
2.  <span data-ttu-id="e9e4a-106">再次添加同一表，以便“关系图”窗格显示同一表两次。</span><span class="sxs-lookup"><span data-stu-id="e9e4a-106">Add the same table again, so that the Diagram pane shows the same table twice within the Diagram pane.</span></span>  
  
     <span data-ttu-id="e9e4a-107">[查询和视图设计器](query-and-view-designer-tools-visual-database-tools.md) 将通过为表名添加一个顺序号来为第二个实例分配别名。</span><span class="sxs-lookup"><span data-stu-id="e9e4a-107">The [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md) assigns an alias to the second instance by adding a sequential number to the table name.</span></span> <span data-ttu-id="e9e4a-108">此外，查询和视图设计器还会在表示该表参与查询的两种不同方式的两个矩形之间创建联接线。</span><span class="sxs-lookup"><span data-stu-id="e9e4a-108">In addition, the Query and View Designer creates a join line between the two rectangles representing the two different ways the table participates in the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9e4a-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e9e4a-109">See Also</span></span>  
 [<span data-ttu-id="e9e4a-110">使用联接进行查询 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e9e4a-110">Query with Joins &#40;Visual Database Tools&#41;</span></span>](query-with-joins-visual-database-tools.md)  
  
  
