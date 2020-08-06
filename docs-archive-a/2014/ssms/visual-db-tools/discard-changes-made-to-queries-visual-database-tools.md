---
title: 放弃对查询所做的更改 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- reverting queries
- queries [SQL Server], discarding changes
- discarding query changes
ms.assetid: 7bb17ece-1222-4622-b476-5789d7641c64
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9ec712f0a8a708db79d054833180776d604e58dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590502"
---
# <a name="discard-changes-made-to-queries-visual-database-tools"></a><span data-ttu-id="22341-102">放弃对查询所做的更改 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="22341-102">Discard Changes Made to Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="22341-103">在保存之前，可以放弃对查询定义所做的更改。</span><span class="sxs-lookup"><span data-stu-id="22341-103">You can discard changes made to a query definition prior to saving them.</span></span> <span data-ttu-id="22341-104">在保存之后，查询将无法还原到先前的状态。</span><span class="sxs-lookup"><span data-stu-id="22341-104">Once they have been saved, they cannot be returned to a previous state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="22341-105">若要撤消对“结果”窗格中的值所做的更改，请在离开该记录之前按 Esc 键。</span><span class="sxs-lookup"><span data-stu-id="22341-105">To undo a change you've made to values in the Results pane, press the ESC key before you move off of the record.</span></span> <span data-ttu-id="22341-106">如果在离开记录时收到更改无法提交到数据库的通知，您也可以按 Esc 键恢复到先前的值。</span><span class="sxs-lookup"><span data-stu-id="22341-106">If you move off of a record and receive a notice that the changes will not be committed to the database you can also press the ESC key to revert to the previous value.</span></span>  
  
### <a name="to-discard-changes-made-to-a-query-definition"></a><span data-ttu-id="22341-107">放弃对查询定义所做的更改</span><span class="sxs-lookup"><span data-stu-id="22341-107">To discard changes made to a query definition</span></span>  
  
1.  <span data-ttu-id="22341-108">如果该查询已经在查询和视图设计器中打开，请在“文件”  菜单中，单击“关闭”  。</span><span class="sxs-lookup"><span data-stu-id="22341-108">With the query open in Query and View Designer, from the **File** menu, click **Close**.</span></span>  
  
2.  <span data-ttu-id="22341-109">在“Microsoft SQL Server Management Studio”  对话框中，单击“否”  。</span><span class="sxs-lookup"><span data-stu-id="22341-109">In the **Microsoft SQL Server Management Studio** dialog box, click **No**.</span></span>  
  
     <span data-ttu-id="22341-110">查询定义将返回到上次保存时的状态。</span><span class="sxs-lookup"><span data-stu-id="22341-110">The query definition will return to the state it was in at the last save.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22341-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="22341-111">See Also</span></span>  
 <span data-ttu-id="22341-112">[&#40;Visual Database Tools 保存查询&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="22341-112">[Save Queries &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="22341-113">[&#40;Visual Database Tools 的设计查询和视图操作指南主题&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="22341-113">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 <span data-ttu-id="22341-114">[在 Visual Database Tools &#40;执行基本的查询操作&#41;](perform-basic-operations-with-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="22341-114">[Perform Basic Operations with Queries &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="22341-115">使用“结果”窗格中的数据 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="22341-115">Work with Data in the Results Pane &#40;Visual Database Tools&#41;</span></span>](results-pane-visual-database-tools.md)  
  
  
