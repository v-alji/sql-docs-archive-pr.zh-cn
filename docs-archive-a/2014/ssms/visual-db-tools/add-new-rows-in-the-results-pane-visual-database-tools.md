---
title: 在“结果”窗格中添加新行 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- inserting rows
- Query Designer [SQL Server], Results pane
- Results pane
- adding rows
- row additions [SQL Server], Results pane
ms.assetid: 59891c84-3f54-4ab9-8b86-72c59627b480
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3137da106279e09305261c6c7cb7fd06d254b4fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579957"
---
# <a name="add-new-rows-in-the-results-pane-visual-database-tools"></a><span data-ttu-id="5615e-102">在“结果”窗格中添加新行 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="5615e-102">Add New Rows in the Results Pane (Visual Database Tools)</span></span>
  <span data-ttu-id="5615e-103">若要添加新数据，既可以在其中键入数据也可以从其他程序（如“记事本”或 Excel）粘贴数据。</span><span class="sxs-lookup"><span data-stu-id="5615e-103">You can add new data either by typing it in or by pasting it from another program such as Notepad or Excel.</span></span> <span data-ttu-id="5615e-104">要粘贴的行必须与要粘贴到的表中列的数目和类型完全一致。</span><span class="sxs-lookup"><span data-stu-id="5615e-104">A row to be pasted must have exactly the same number and types of columns as the table into which you are pasting.</span></span> <span data-ttu-id="5615e-105">可以在“结果”窗格中一次粘贴多行。</span><span class="sxs-lookup"><span data-stu-id="5615e-105">You can paste multiple rows into the Results pane at once.</span></span>  
  
 <span data-ttu-id="5615e-106">有关如何输入数据的信息，请参阅[更新结果的规则 (Visual Database Tools)](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="5615e-106">For information about how to enter data see [Rules for Updating Results &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
### <a name="to-add-a-new-data-row"></a><span data-ttu-id="5615e-107">添加新数据行</span><span class="sxs-lookup"><span data-stu-id="5615e-107">To add a new data row</span></span>  
  
1.  <span data-ttu-id="5615e-108">定位到“结果”窗格底部，此处有一个可用于添加新数据行的空白行。</span><span class="sxs-lookup"><span data-stu-id="5615e-108">Navigate to the bottom of the Results pane, where a blank row is available for adding a new data row.</span></span>  
  
     <span data-ttu-id="5615e-109">所有列的初始值都将为 NULL  。</span><span class="sxs-lookup"><span data-stu-id="5615e-109">The initial values for all columns will be *NULL*.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="5615e-110">若要直接转到第一个空行，请使用“结果”窗格底部的导航栏。</span><span class="sxs-lookup"><span data-stu-id="5615e-110">To go directly to the first empty row use the navigation bar at the bottom of the Results pane.</span></span>  
  
2.  <span data-ttu-id="5615e-111">如果从剪贴板中粘贴多行，请通过单击新行左侧的按钮选择新行。</span><span class="sxs-lookup"><span data-stu-id="5615e-111">If you are pasting rows from the Clipboard, select the new row by clicking the button to its left.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5615e-112">如果所粘贴的一行或多行无法提交到数据库，则您将收到消息，指示哪些行不能提交。</span><span class="sxs-lookup"><span data-stu-id="5615e-112">If one or more of the rows you're pasting can't be committed to the database you will receive a message telling you which row(s) couldn't be committed.</span></span>  
  
3.  <span data-ttu-id="5615e-113">为新行输入数据。</span><span class="sxs-lookup"><span data-stu-id="5615e-113">Enter the data for the new row.</span></span> <span data-ttu-id="5615e-114">如果要粘贴数据，请从“编辑”  菜单中选择“粘贴”  。</span><span class="sxs-lookup"><span data-stu-id="5615e-114">If you are pasting, choose **Paste** from the **Edit** menu.</span></span>  
  
4.  <span data-ttu-id="5615e-115">离开该行可以将其提交到数据库。</span><span class="sxs-lookup"><span data-stu-id="5615e-115">Leave that row to commit it to the database.</span></span>  
  
 <span data-ttu-id="5615e-116">如果在保存行时出错，查询和视图数据库设计器将显示一条消息，然后返回到您所编辑的行。</span><span class="sxs-lookup"><span data-stu-id="5615e-116">If an error occurs when you save the row the Query and View Designer displays a message and then returns you to the row you were editing.</span></span> <span data-ttu-id="5615e-117">然后，可以：</span><span class="sxs-lookup"><span data-stu-id="5615e-117">You can then:</span></span>  
  
-   <span data-ttu-id="5615e-118">通过对该行进行进一步的编辑以解决错误。</span><span class="sxs-lookup"><span data-stu-id="5615e-118">Resolve the error by making further edits in the row.</span></span>  
  
-   <span data-ttu-id="5615e-119">按 Esc 取消编辑。</span><span class="sxs-lookup"><span data-stu-id="5615e-119">Cancel the edit by pressing ESC.</span></span> <span data-ttu-id="5615e-120">如果在已经进行了更改的某个单元格中按 Esc，则将取消对该单元格所做的更改。</span><span class="sxs-lookup"><span data-stu-id="5615e-120">If you press ESC while in a cell that you changed, the changes for that cell are canceled.</span></span> <span data-ttu-id="5615e-121">如果在未进行更改的单元格中按 Esc，则将取消对整个行所做的更改。</span><span class="sxs-lookup"><span data-stu-id="5615e-121">If you press ESC while in a cell you have not changed, the changes for the entire row are canceled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5615e-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5615e-122">See Also</span></span>  
 <span data-ttu-id="5615e-123">[使用 Visual Database Tools &#40;的 "结果" 窗格中的数据&#41;](results-pane-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="5615e-123">[Work with Data in the Results Pane &#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="5615e-124">执行基本的查询操作 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="5615e-124">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
