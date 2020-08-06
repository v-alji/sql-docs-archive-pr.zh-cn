---
title: “查询定义不同”对话框 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69639
- vdtsql.chm:69640
- vdt.dlgbox.querydefinitionsdiffer
ms.assetid: 90383473-2922-40e5-9682-3850849aa856
author: stevestein
ms.author: sstein
ms.openlocfilehash: b9a39d5d6b739fa4ab1a96ea95b513ecb7f6682f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691484"
---
# <a name="query-definitions-differ-dialog-box-visual-database-tools"></a><span data-ttu-id="b4fcc-102">“查询定义不同”对话框 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="b4fcc-102">Query Definitions Differ Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="b4fcc-103">此对话框可通知您查询无法以图形形式显示在“关系图”窗格和“条件”窗格中，因此您只能在 SQL 窗格中编辑查询。</span><span class="sxs-lookup"><span data-stu-id="b4fcc-103">This dialog box notifies you that your query cannot be represented graphically in the Diagram and Criteria panes, and that you can edit your query only in the SQL pane.</span></span>  
  
 <span data-ttu-id="b4fcc-104">在 SQL 窗格中输入或编辑 SQL 语句，然后移动到另一个窗格，验证查询或尝试执行查询，并且符合以下条件之一时，将显示此对话框：</span><span class="sxs-lookup"><span data-stu-id="b4fcc-104">This dialog box may appear when you enter or edit an SQL statement in the SQL pane; you then move to another pane, verify the query, or attempt to execute the query; and one of the following conditions applies:</span></span>  
  
-   <span data-ttu-id="b4fcc-105">SQL 语句不完整或者包含一个或多个语法错误。</span><span class="sxs-lookup"><span data-stu-id="b4fcc-105">The SQL statement is incomplete or contains one or more syntax errors.</span></span>  
  
-   <span data-ttu-id="b4fcc-106">SQL 语句有效但在图形窗格中不支持（如联合查询）。</span><span class="sxs-lookup"><span data-stu-id="b4fcc-106">The SQL statement is valid but is not supported in the graphical panes (for example, a Union query).</span></span>  
  
-   <span data-ttu-id="b4fcc-107">SQL 语句有效但包含特定于所使用数据连接的语法。</span><span class="sxs-lookup"><span data-stu-id="b4fcc-107">The SQL statement is valid but contains syntax specific to the data connection you are using.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="b4fcc-108">可以使用“查询”工具栏上的“验证 SQL 语句”按钮来检查语句是否有效。</span><span class="sxs-lookup"><span data-stu-id="b4fcc-108">You can check whether a statement is valid using the **Verify SQL Statement** button on the **Query** toolbar.</span></span>  
  
 <span data-ttu-id="b4fcc-109">该对话框将显示一条消息，指示不能显示 SQL 语句的原因，并询问如何继续。</span><span class="sxs-lookup"><span data-stu-id="b4fcc-109">The dialog box displays a message with the reason that the SQL statement cannot be represented, and then asks how you want to proceed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b4fcc-110">如果已经隐藏了“关系图”窗格和“条件”窗格，则不会显示“查询定义不同”  对话框。</span><span class="sxs-lookup"><span data-stu-id="b4fcc-110">The **Query Definitions Differ** dialog box does not appear if you have hidden the Diagram and Criteria panes.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b4fcc-111">选项</span><span class="sxs-lookup"><span data-stu-id="b4fcc-111">Options</span></span>  
 <span data-ttu-id="b4fcc-112">**“忽略”按钮**</span><span class="sxs-lookup"><span data-stu-id="b4fcc-112">**Ignore Button**</span></span>  
 <span data-ttu-id="b4fcc-113">选择此按钮可指定接受 SQL 语句，以进一步编辑语句或执行语句。</span><span class="sxs-lookup"><span data-stu-id="b4fcc-113">Choose this button to specify that you want to accept the SQL statement, either to edit it further or to execute it.</span></span> <span data-ttu-id="b4fcc-114">如果接受语句，“关系图”窗格和“条件”窗格将显示为灰色，以指示不能它们显示 SQL 窗格中的语句。</span><span class="sxs-lookup"><span data-stu-id="b4fcc-114">If you accept the statement, the Diagram and Criteria panes appear dimmed to indicate that they do not represent the statement in the SQL pane.</span></span>  
  
 <span data-ttu-id="b4fcc-115">**“撤消”按钮**</span><span class="sxs-lookup"><span data-stu-id="b4fcc-115">**Undo Button**</span></span>  
 <span data-ttu-id="b4fcc-116">选择此按钮可放弃对 SQL 窗格中内容所做的更改。</span><span class="sxs-lookup"><span data-stu-id="b4fcc-116">Choose this button to discard your changes to the SQL pane.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b4fcc-117">如果语句正确但不支持以图形形式在查询和视图设计器中显示，那么即使语句不能在“关系图”窗格和“条件”窗格中显示，您也可以执行它。</span><span class="sxs-lookup"><span data-stu-id="b4fcc-117">If the statement is correct but not supported graphically by the Query and View Designer, you can execute it even though it cannot be represented in the Diagram and Criteria panes.</span></span> <span data-ttu-id="b4fcc-118">例如，如果输入联合查询，该语句可以执行，但不能在其他窗格中显示。</span><span class="sxs-lookup"><span data-stu-id="b4fcc-118">For example, if you enter a Union query, the statement can be executed but not represented in the other panes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4fcc-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b4fcc-119">See Also</span></span>  
 [<span data-ttu-id="b4fcc-120">查询和视图设计器工具 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="b4fcc-120">Query and View Designer Tools &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
