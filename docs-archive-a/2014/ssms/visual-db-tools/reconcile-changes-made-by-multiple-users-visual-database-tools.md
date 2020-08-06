---
title: 协调多个用户所做的更改 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- table modifications [SQL Server], multiple users
- reconciling changes made by multiple users
- modifications made by multiple users
ms.assetid: fc7ed4f2-ad3d-47fc-a3ef-51e5bb069ef0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 337d505fce474a33301c18313fe6137f6bc0ec1b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688375"
---
# <a name="reconcile-changes-made-by-multiple-users-visual-database-tools"></a><span data-ttu-id="99777-102">协调多个用户所做的更改 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="99777-102">Reconcile Changes Made by Multiple Users (Visual Database Tools)</span></span>
  <span data-ttu-id="99777-103">在多用户环境中，多个用户可以同时对同一个对象进行更改。</span><span class="sxs-lookup"><span data-stu-id="99777-103">In a multiuser environment, changes can be made on the same object by multiple users at once.</span></span> <span data-ttu-id="99777-104">当您在表或数据库关系图设计器中处理对象的结构时，可能会出现这种情况；对于查询和视图设计器的“结果”窗格内所返回结果中的值，也会出现这种情况。</span><span class="sxs-lookup"><span data-stu-id="99777-104">This can happen when you're working on the structure of the object in the Table or Database Diagram designers or it can happen to values in the results returned in the Query and View designer's Results pane.</span></span> <span data-ttu-id="99777-105">这可能导致您需要解决的冲突。</span><span class="sxs-lookup"><span data-stu-id="99777-105">This can cause conflicts that you'll want to resolve.</span></span>  
  
## <a name="conflicts-in-the-table-or-database-diagram-designers"></a><span data-ttu-id="99777-106">表设计器或数据库关系图设计器中的冲突</span><span class="sxs-lookup"><span data-stu-id="99777-106">Conflicts in the Table or Database Diagram Designers</span></span>  
 <span data-ttu-id="99777-107">例如，当您在表设计器中处理某个表时，另一个用户可能会删除或重命名同一个表或相关的表。</span><span class="sxs-lookup"><span data-stu-id="99777-107">For example, another user might delete or rename a table while you are working with the same or a related table in Table Designer.</span></span> <span data-ttu-id="99777-108">尝试保存表时， [“检测到数据库更改”对话框 (Visual Database Tools)](visual-database-tools.md) 会通知你，在打开该表之后数据库已经更新。</span><span class="sxs-lookup"><span data-stu-id="99777-108">When you attempt to save your table, the [Database Changes Detected Dialog Box &#40;Visual Database Tools&#41;](visual-database-tools.md) notifies you that the database has been updated since you opened the table.</span></span>  
  
 <span data-ttu-id="99777-109">该对话框还会显示一个列表，列出在您保存表时将受到影响的数据库对象。</span><span class="sxs-lookup"><span data-stu-id="99777-109">This dialog box also displays a list of database objects that will be affected as a result of saving your table.</span></span> <span data-ttu-id="99777-110">此时，您可以执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="99777-110">At this point, you can take one of these actions:</span></span>  
  
-   <span data-ttu-id="99777-111">选择“是”  保存表并使用列表中的所有更改更新数据库。</span><span class="sxs-lookup"><span data-stu-id="99777-111">Choose **Yes** to save your table and update the database with all the changes in the list.</span></span>  
  
     <span data-ttu-id="99777-112">此操作将影响共用相同数据库对象的表。</span><span class="sxs-lookup"><span data-stu-id="99777-112">This action could affect tables that share the same database objects.</span></span> <span data-ttu-id="99777-113">例如，假设编辑 `au`表中的`id` _ `titleauthors` 列，而另一个用户正在处理 `authors` 表，该表通过 `titleauthors` 列与 `au`\_`id` 表相关。</span><span class="sxs-lookup"><span data-stu-id="99777-113">For example, suppose you edit the `au`_`id` column in the `titleauthors` table while another user is working on the `authors` table which is related to the `titleauthors` table by the `au`\_`id` column.</span></span> <span data-ttu-id="99777-114">保存您的表将影响另一个用户的表。</span><span class="sxs-lookup"><span data-stu-id="99777-114">Saving your table will affect the other user's table.</span></span> <span data-ttu-id="99777-115">与此类似，假设另一个用户为 `qty` 表中的 `sales` 列定义了一个 CHECK 约束。</span><span class="sxs-lookup"><span data-stu-id="99777-115">Similarly, suppose that another user defined a check constraint for the `qty` column in the `sales` table.</span></span> <span data-ttu-id="99777-116">如果您删除 `qty` 列并保存 `sales` 表，则另一个用户的 CHECK 约束将受到影响。</span><span class="sxs-lookup"><span data-stu-id="99777-116">If you delete the `qty` column and save the `sales` table, the other user's check constraint will be affected.</span></span>  
  
-   <span data-ttu-id="99777-117">选择“否”  取消保存操作。</span><span class="sxs-lookup"><span data-stu-id="99777-117">Choose **No** to cancel the save action.</span></span>  
  
     <span data-ttu-id="99777-118">您随后即可关闭该表而不进行保存。</span><span class="sxs-lookup"><span data-stu-id="99777-118">You can then close the table without saving it.</span></span> <span data-ttu-id="99777-119">当您重新打开该表时，它将与数据库中的相应内容匹配。</span><span class="sxs-lookup"><span data-stu-id="99777-119">When you reopen the table it will match what is in the database.</span></span>  
  
-   <span data-ttu-id="99777-120">选择“保存文本文件”  保存更改列表。</span><span class="sxs-lookup"><span data-stu-id="99777-120">Choose **Save Text File** to save a list of the changes.</span></span>  
  
     <span data-ttu-id="99777-121">可以将“检测到数据库更改”  对话框中显示的一系列数据库更改保存为文本文件，以便调查其他用户的更改原因。</span><span class="sxs-lookup"><span data-stu-id="99777-121">You can save the list of database changes shown in the **Database Changes Detected** dialog box to a text file so that you can investigate the cause of other users' changes.</span></span> <span data-ttu-id="99777-122">例如，如果另一个用户编辑了您标记为删除的表，则您可能希望研究在更新数据库之前是否应删除该表。</span><span class="sxs-lookup"><span data-stu-id="99777-122">For example, if another user edited a table that you marked for deletion, you may want to research whether the table should be deleted before updating the database.</span></span>  
  
## <a name="conflicts-in-the-query-and-view-designer"></a><span data-ttu-id="99777-123">查询和视图设计器中的冲突</span><span class="sxs-lookup"><span data-stu-id="99777-123">Conflicts in the Query and View Designer</span></span>  
 <span data-ttu-id="99777-124">如果运行查询或返回某视图的结果，则会在 [“结果”窗格](results-pane-visual-database-tools.md)中显示数据。</span><span class="sxs-lookup"><span data-stu-id="99777-124">If you run a query or return the results of a view, the data is shown in the [Results Pane](results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="99777-125">多个用户可以同时对同一组数据进行操作，这便可能导致冲突。</span><span class="sxs-lookup"><span data-stu-id="99777-125">Multiple users can work on the same set of data at the same time, which can cause conflicts.</span></span>  
  
 <span data-ttu-id="99777-126">例如，假设您和同事分别运行查询以显示 `titleauthors` 表中的所有数据。</span><span class="sxs-lookup"><span data-stu-id="99777-126">For example, lets say you and a colleague each run a query to show all the data in the `titleauthors` table.</span></span> <span data-ttu-id="99777-127">您的同事将返回的第一个记录中的名字由 Barb 改为 Barbara。</span><span class="sxs-lookup"><span data-stu-id="99777-127">Your colleague changes the first name in the first record returned from Barb to Barbara.</span></span> <span data-ttu-id="99777-128">此时，数据库的相应字段将包含 Barbara，而您的结果集中仍会显示 Barb。</span><span class="sxs-lookup"><span data-stu-id="99777-128">At this point the database has Barbara in that field, while your result set still shows Barb.</span></span> <span data-ttu-id="99777-129">现在您键入 Barbara，然后在行外单击。</span><span class="sxs-lookup"><span data-stu-id="99777-129">Now you type in Barbara and click off of the row.</span></span> <span data-ttu-id="99777-130">您将收到一条消息，询问要如何解决冲突。</span><span class="sxs-lookup"><span data-stu-id="99777-130">You will receive a message asking you how you want to resolve the conflict.</span></span>  
  
-   <span data-ttu-id="99777-131">单击“是”  可以用你的更改来更新数据库。</span><span class="sxs-lookup"><span data-stu-id="99777-131">Click **Yes** to update the database with your changes.</span></span>  
  
     <span data-ttu-id="99777-132">这将重写您的同事的更改。</span><span class="sxs-lookup"><span data-stu-id="99777-132">This will override your colleague's changes.</span></span>  
  
-   <span data-ttu-id="99777-133">单击“否”  可将结果集更新为数据库中的当前相应内容。</span><span class="sxs-lookup"><span data-stu-id="99777-133">Click **No** to have your result set updated to what's currently in the database.</span></span>  
  
     <span data-ttu-id="99777-134">这将用您的同事的更改重写您的更改。</span><span class="sxs-lookup"><span data-stu-id="99777-134">This will override your changes with those of your colleague's.</span></span>  
  
-   <span data-ttu-id="99777-135">单击“取消”  可继续编辑而不解决冲突。</span><span class="sxs-lookup"><span data-stu-id="99777-135">Click **Cancel** to continue to edit without resolving the conflict.</span></span>  
  
     <span data-ttu-id="99777-136">在这种情况下，您将无法将更改提交到数据库。</span><span class="sxs-lookup"><span data-stu-id="99777-136">In this case you will not be able to commit your changes to the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99777-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="99777-137">See Also</span></span>  
 [<span data-ttu-id="99777-138">“检测到数据库更改”对话框 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="99777-138">Database Changes Detected Dialog Box &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
