---
title: 使用“结果”窗格中的数据 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- queries [Visual Database Tools]
- result sets [SQL Server], queries
- Query Designer [SQL Server], Results pane
- results [SQL Server], query
- Visual Database Tools [SQL Server], queries
- queries [SQL Server], results
- Results pane
ms.assetid: 4f8a0080-91ef-4442-83ae-53be2f478c54
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1c914b924ee477c3a59d78ae3ec114c88497726a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587116"
---
# <a name="work-with-data-in-the-results-pane-visual-database-tools"></a><span data-ttu-id="4b2fe-102">使用“结果”窗格中的数据 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="4b2fe-102">Work with Data in the Results Pane (Visual Database Tools)</span></span>
  <span data-ttu-id="4b2fe-103">在运行查询或视图之后，将在“结果”窗格中显示结果。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-103">After you run a query or view, the results are shown in the Results pane.</span></span> <span data-ttu-id="4b2fe-104">然后您就可以对这些结果进行处理。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-104">You can then work with those results.</span></span> <span data-ttu-id="4b2fe-105">例如，您可以添加和删除行、输入或更改数据以及在大型结果集中轻松导航。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-105">For example, you can add and delete rows, input or change data, and easily navigate through large results sets.</span></span>  
  
 <span data-ttu-id="4b2fe-106">以下信息可以帮助您避免问题并提高处理结果集的效率：</span><span class="sxs-lookup"><span data-stu-id="4b2fe-106">The following information can help you avoid problems and work effectively with your results sets.</span></span>  
  
## <a name="returning-the-results-set"></a><span data-ttu-id="4b2fe-107">返回结果集</span><span class="sxs-lookup"><span data-stu-id="4b2fe-107">Returning the results set</span></span>  
 <span data-ttu-id="4b2fe-108">您可以从查询或视图返回结果，并且可以选择是仅打开“结果”窗格还是打开所有窗格。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-108">You can return results from either a query or a view and can choose whether to open just the results pane or all panes.</span></span> <span data-ttu-id="4b2fe-109">在这两种情况下，都会在查询和视图设计器中打开该查询或视图。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-109">In either case the query or view will open in Query and View Designer.</span></span> <span data-ttu-id="4b2fe-110">两者之间的区别是：一个打开时仅显示“结果”窗格，另一个打开时则显示“选项”对话框中选择的所有窗口。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-110">The difference is that one opens with only the Results pane showing and the other opens with all windows that have been selected in the Options dialog box.</span></span> <span data-ttu-id="4b2fe-111">默认为所有四个窗格（“结果”、SQL、“关系图”和“条件”）。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-111">The default is all four panes (Results, SQL, Diagram, and Criteria).</span></span>  
  
 <span data-ttu-id="4b2fe-112">有关详细信息，请参阅[打开查询 (Visual Database Tools)](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-112">For more information see [Open Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="4b2fe-113">若要更改查询或视图的设计，以使其返回不同的结果集或以不同的顺序返回记录，请参阅[设计查询和视图操作指南主题 (Visual Database Tools)](design-queries-and-views-how-to-topics-visual-database-tools.md) 中所列的主题。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-113">To change the design of the query or view so it returns a different set of results or returns records in a different order see the topics listed in [Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="4b2fe-114">您还可以通过以下两种方式来决定是返回全部结果集还是返回部分结果集：在查询运行时停止查询或在查询运行前选择返回的结果数量。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-114">You can also determine whether to return all or part of the results set in two ways--stop the query as it runs or choose how much of results to return before the query is run.</span></span>  
  
## <a name="navigating-in-the-results-pane"></a><span data-ttu-id="4b2fe-115">在“结果”窗格中导航</span><span class="sxs-lookup"><span data-stu-id="4b2fe-115">Navigating in the results pane</span></span>  
 <span data-ttu-id="4b2fe-116">您可以使用“结果”窗格底部的导航栏在记录之间快速导航。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-116">You can quickly navigate through the records using the navigation bar at the bottom of the Results pane.</span></span>  
  
 <span data-ttu-id="4b2fe-117">导航栏中提供了多个按钮，可分别用于跳转到第一个记录、最后一个记录、下一个记录、上一个记录以及某个特定记录。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-117">There are buttons for going to the first and last records, the next and previous records, and for going to a particular record.</span></span>  
  
 <span data-ttu-id="4b2fe-118">若要转到特定的记录，请在导航栏的文本框中键入行号，然后按 Enter。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-118">To go to a particular record, type the number of the row in the text box in the navigation bar and then press ENTER.</span></span>  
  
 <span data-ttu-id="4b2fe-119">有关在查询和视图设计器中使用键盘快捷方式的信息，请参阅[在查询和视图设计器中导航 (Visual Database Tools)](navigate-in-the-query-and-view-designer-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-119">For information about using keyboard shortcuts in the Query and View Designer see [Navigate in the Query and View Designer &#40;Visual Database Tools&#41;](navigate-in-the-query-and-view-designer-visual-database-tools.md).</span></span>  
  
## <a name="committing-changes-to-the-database"></a><span data-ttu-id="4b2fe-120">将更改提交到数据库</span><span class="sxs-lookup"><span data-stu-id="4b2fe-120">Committing changes to the database</span></span>  
 <span data-ttu-id="4b2fe-121">“结果”窗格使用开放式并发控制，因此该网格显示的是数据库中数据的副本而不是完全实时的视图。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-121">The Results pane uses optimistic concurrency control so the grid shows a copy of the data in the database rather than an entirely live view.</span></span> <span data-ttu-id="4b2fe-122">这样，只有当您离开行时，才会将更改提交给数据库。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-122">This way changes are only committed to the database after you move off of a row.</span></span> <span data-ttu-id="4b2fe-123">这允许一个以上的用户同时使用数据库。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-123">This allows more than one user to work with the database at the same time.</span></span> <span data-ttu-id="4b2fe-124">如果存在冲突（例如，如果另一个用户更改了您更改的相同的行，并在您提交前将其提交给了数据库），您将收到一条消息，告诉您该冲突并提供解决方案。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-124">If there are conflicts (for example if another user changed the same row you changed and committed it to the database before you did) you will receive a message telling you of the conflict and offering resolutions.</span></span>  
  
## <a name="undo-changes-using-esc"></a><span data-ttu-id="4b2fe-125">使用 Esc 撤消更改</span><span class="sxs-lookup"><span data-stu-id="4b2fe-125">Undo changes using ESC</span></span>  
 <span data-ttu-id="4b2fe-126">只有在更改尚未提交到数据库时，才能撤消更改。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-126">You can only undo a change if it hasn't yet been committed to the database.</span></span> <span data-ttu-id="4b2fe-127">如果您尚未离开记录或者当离开记录时收到错误信息，指出无法提交该更改，则不会提交数据。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-127">The data is not committed if you haven't moved off of the record or if once you do move off the record you get an error message indicating the change won't be committed.</span></span> <span data-ttu-id="4b2fe-128">如果尚未提交更改，则可以使用 Esc 键来撤消更改。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-128">If it hasn't been committed you can undo the change by using the ESC key.</span></span>  
  
 <span data-ttu-id="4b2fe-129">若要撤消对某一行的所有更改，请移动到该行中尚未编辑过的单元格，然后按 Esc 键。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-129">To undo all changes in a row, move to a cell in that row that you have not edited and press the ESC key.</span></span>  
  
 <span data-ttu-id="4b2fe-130">若要撤消对已编辑的特定单元格的更改，请移动到该单元格，然后按 Esc 键。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-130">To undo changes to a particular cell that you have edited, move to that cell press the ESC key.</span></span>  
  
## <a name="adding-or-deleting-data-in-the-database"></a><span data-ttu-id="4b2fe-131">在数据库中添加或删除数据</span><span class="sxs-lookup"><span data-stu-id="4b2fe-131">Adding or deleting data in the database</span></span>  
 <span data-ttu-id="4b2fe-132">为了了解数据库设计的工作情况，可能需要向数据库中添加示例数据。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-132">To see how your database design is working you may need to add sample data to the database.</span></span> <span data-ttu-id="4b2fe-133">您可以直接向“结果”窗格中输入示例数据，也可以从其他程序（如“记事本”或 Excel）复制示例数据，然后将其粘贴到“结果”窗格中。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-133">You can enter it into the results pane directly or you can copy it from another program, such as notepad or Excel, and paste it into the results pane.</span></span>  
  
 <span data-ttu-id="4b2fe-134">除了可以向“结果”窗格中复制行之外，您还可以添加新记录或者修改或删除现有记录。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-134">In addition to copying rows into the Results pane you can add new records or modify or delete existing ones.</span></span> <span data-ttu-id="4b2fe-135">有关详细信息，请参阅[在“结果”窗格中添加新行 (Visual Database Tools)](results-pane-visual-database-tools.md)、[在“结果”窗格中删除行 (Visual Database Tools)](delete-rows-in-the-results-pane-visual-database-tools.md) 和[在“结果”窗格中编辑行 (Visual Database Tools)](edit-rows-in-the-results-pane-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-135">For more information see [Add New Rows in the Results Pane &#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md), [Delete Rows in the Results Pane &#40;Visual Database Tools&#41;](delete-rows-in-the-results-pane-visual-database-tools.md), and [Edit Rows in the Results Pane &#40;Visual Database Tools&#41;](edit-rows-in-the-results-pane-visual-database-tools.md).</span></span>  
  
## <a name="tips-for-working-with-null-values-and-empty-cells"></a><span data-ttu-id="4b2fe-136">关于处理 NULL 值和空单元格的提示</span><span class="sxs-lookup"><span data-stu-id="4b2fe-136">Tips for working with NULL values and empty cells</span></span>  
 <span data-ttu-id="4b2fe-137">单击一个空行以添加新记录时，所有列的初始值均为 NULL  。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-137">When you click on an empty row to add a new record, the initial value for all columns is *NULL*.</span></span> <span data-ttu-id="4b2fe-138">如果列允许空值，则可将保留空值。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-138">If a column allows null values you can leave it as is.</span></span>  
  
 <span data-ttu-id="4b2fe-139">若要使用空值替换非空值，请键入大写字母的 NULL。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-139">If you want to replace a non-null value with null, type NULL in capital letters.</span></span> <span data-ttu-id="4b2fe-140">“结果”窗格将对该词应用倾斜格式，以表示它将被识别为空值而不是字符串。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-140">The Results pane will give the word italic formatting to indicate that it is to be recognized as a null value rather than as a string.</span></span>  
  
 <span data-ttu-id="4b2fe-141">若要键入字符串“null”，请键入这些字母（不包括引号）。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-141">To type in the string "null" type the letters without quotes.</span></span> <span data-ttu-id="4b2fe-142">只要有一个字母是小写字母，该值就会被视为字符串而不是空值。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-142">As long as at least one of the letters is in lower case, the value will be treated as a string rather than a null value.</span></span>  
  
 <span data-ttu-id="4b2fe-143">对于数据类型为 binary 的列，默认情况下其值为 NULL。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-143">Values for columns with a binary data type will have NULL values by default.</span></span> <span data-ttu-id="4b2fe-144">这些值不能在“结果”窗格中进行更改。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-144">These values can't be changed in the Results pane.</span></span>  
  
 <span data-ttu-id="4b2fe-145">若要输入空格而不是使用空值，请删除现有的文本并离开该单元格。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-145">To input an empty space instead of using null, delete the existing text and move off of the cell.</span></span>  
  
## <a name="validating-data"></a><span data-ttu-id="4b2fe-146">验证数据</span><span class="sxs-lookup"><span data-stu-id="4b2fe-146">Validating data</span></span>  
 <span data-ttu-id="4b2fe-147">查询和视图设计器可以根据列属性来验证某些类型的数据。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-147">The Query and View Designer can validate some kinds of data against the columns properties.</span></span> <span data-ttu-id="4b2fe-148">例如，如果您在数据类型为 float 的列中输入“abc”，您将收到错误，并且该更改不会提交到数据库。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-148">For example, if you enter "abc" into a column with a float data type, you will receive an error and the change will not be committed to the database.</span></span>  
  
 <span data-ttu-id="4b2fe-149">在“结果”窗格中，查看列的数据类型的最快捷的方法是：打开“关系图”窗格并悬停在表或表值对象中列的名称上。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-149">The quickest way to see the data type of a column when you're in the Results pane is to open the Diagram pane and hover over the name of the column in the table or table-valued object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4b2fe-150">“结果”窗格可以为 text 数据类型显示的最大长度为 2,147,483,647。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-150">The maximum length the Results pane can show for a text data type is 2,147,483,647.</span></span>  
  
## <a name="keeping-the-results-set-synchronized-with-the-query-definition"></a><span data-ttu-id="4b2fe-151">使结果集与查询定义保持同步</span><span class="sxs-lookup"><span data-stu-id="4b2fe-151">Keeping the results set synchronized with the query definition</span></span>  
 <span data-ttu-id="4b2fe-152">当您处理查询或视图的结果时，可能会出现“结果”窗格中的记录与查询定义不同步的情况。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-152">While you're working on the results of a query or view it is possible for the records in the results pane to get out of synchronization with the queries definition.</span></span> <span data-ttu-id="4b2fe-153">例如，如果您用查询搜索出表的五列中的四列，然后使用“关系图”窗格将第五列添加到查询的定义中，则第五列的数据不会自动添加到“结果”窗格中。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-153">For example, if you ran a query for four out of five columns in a table, then used the Diagram pane to add the fifth column to the definition of the query, that fifth column's data will not automatically be added to the results pane.</span></span> <span data-ttu-id="4b2fe-154">若要使“结果”窗格反映新的查询定义，请再次运行该查询。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-154">To make the results pane reflect the new query definition, run the query again.</span></span>  
  
 <span data-ttu-id="4b2fe-155">您可以这样来判断：“结果”窗格的右下角出现一个警报图标和文本“查询已更改”，并且该图标在窗格的左上角反复出现。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-155">You can tell if this happens--an alert icon and the text "Query Changed" appears in the lower-right corner of the results pane and the icon is repeated in the upper-left corner of the pane.</span></span>  
  
## <a name="reconciling-changes-made-by-multiple-users"></a><span data-ttu-id="4b2fe-156">协调多个用户所做的更改</span><span class="sxs-lookup"><span data-stu-id="4b2fe-156">Reconciling changes made by multiple users</span></span>  
 <span data-ttu-id="4b2fe-157">在处理查询或视图的结果时，所处理的记录可能会被另一个也在处理数据库的用户所更改。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-157">While you're working on the results of a query or view it is possible fore the records to be changed by a different user who is also working with the database.</span></span>  
  
 <span data-ttu-id="4b2fe-158">如果出现此情况，当您离开发生冲突的单元格时，将会立即收到通知。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-158">If this happens you will receive a notice as soon as you move off of the cell with the conflict.</span></span> <span data-ttu-id="4b2fe-159">然后您可以重写其他用户的更改，用其他用户的更改更新您的“结果”窗格或者仍然编辑您的“结果”窗格而不协调差异。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-159">You will then be able to override the other user's change, update your results pane with the other user's change, or keep editing your results pane without reconciling the differences.</span></span> <span data-ttu-id="4b2fe-160">如果选择不协调差异，则不会将您所做的更改提交到数据库。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-160">If you choose not to reconcile the differences your changes will not be committed to the database.</span></span>  
  
## <a name="limitations-in-the-results-pane"></a><span data-ttu-id="4b2fe-161">“结果”窗格中的限制</span><span class="sxs-lookup"><span data-stu-id="4b2fe-161">Limitations in the Results pane</span></span>  
  
### <a name="what-can-not-be-updated"></a><span data-ttu-id="4b2fe-162">不能更新的内容</span><span class="sxs-lookup"><span data-stu-id="4b2fe-162">What can not be updated</span></span>  
 <span data-ttu-id="4b2fe-163">以下提示可能有助于您成功地处理“结果”窗格中的数据。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-163">These tips may help you work successfully with data in the Results pane.</span></span>  
  
-   <span data-ttu-id="4b2fe-164">如果查询中包括的列来自多个表或视图，则不能更新该查询。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-164">Queries that include columns from more than one table or view can't be updated.</span></span>  
  
-   <span data-ttu-id="4b2fe-165">只有当数据库约束允许更新视图时，才能更新视图。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-165">Views can only be updated if the database constraints allow it.</span></span>  
  
-   <span data-ttu-id="4b2fe-166">不能更新存储过程返回的结果。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-166">Results returned by a stored procedure can't be updated.</span></span>  
  
-   <span data-ttu-id="4b2fe-167">不能更新使用 GROUP BY、DISTINCT 或 TO XML 子句的查询或视图。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-167">Queries or views using the GROUP BY, DISTINCT, or TO XML clauses are not updatable.</span></span>  
  
-   <span data-ttu-id="4b2fe-168">表值函数返回的结果只有在某些情况下才能更新。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-168">Results returned by table-valued functions can only be updated in some cases.</span></span>  
  
-   <span data-ttu-id="4b2fe-169">由查询中的表达式生成的列中的数据。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-169">Data in columns that result from an expression in the query.</span></span>  
  
-   <span data-ttu-id="4b2fe-170">提供程序未成功转换的数据。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-170">Data that was not successfully translated by the provider.</span></span>  
  
### <a name="what-can-not-be-represented-fully"></a><span data-ttu-id="4b2fe-171">不能完全呈现的内容</span><span class="sxs-lookup"><span data-stu-id="4b2fe-171">What can not be represented fully</span></span>  
 <span data-ttu-id="4b2fe-172">从数据库返回“结果”窗格的内容很大程度上受您所使用的数据源的提供程序控制。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-172">What is returned to the Results pane from the database is greatly controlled by the provider for the data source you are using.</span></span> <span data-ttu-id="4b2fe-173">“结果”窗格并不总是能转换所有数据库管理系统中的数据。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-173">The Results pane can't always translate the data from all database management systems.</span></span> <span data-ttu-id="4b2fe-174">在以下情况下便是如此。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-174">Here are come cases where this is so.</span></span>  
  
-   <span data-ttu-id="4b2fe-175">Binary 数据类型对于在“结果”窗格中执行操作的人来说通常没什么用处，并且可能需要很长时间才能下载。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-175">Binary data types are often not useful for people working in the Results pane and they can take a very long time to download.</span></span> <span data-ttu-id="4b2fe-176">因此它们由 \<Binary data> 或 Null 表示。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-176">So they are represented by *\<Binary data>* or *Null*.</span></span>  
  
-   <span data-ttu-id="4b2fe-177">并不能始终保留精度和小数位数。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-177">Precision and scale can not always be preserved.</span></span> <span data-ttu-id="4b2fe-178">例如，结果窗格支持的精度为 27。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-178">For example, the Results pane supports a precision of 27.</span></span> <span data-ttu-id="4b2fe-179">如果数据的数据类型的精度比这个值大，数据可能会截断或可能由 *\<Unable to read data>* 表示。</span><span class="sxs-lookup"><span data-stu-id="4b2fe-179">If data is of a data type with a greater precision, the data may be truncated or may be represented by *\<Unable to read data>*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b2fe-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4b2fe-180">See Also</span></span>  
 <span data-ttu-id="4b2fe-181">[在 Visual Database Tools &#40;执行基本的查询操作&#41;](perform-basic-operations-with-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="4b2fe-181">[Perform Basic Operations with Queries &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="4b2fe-182">指定搜索条件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="4b2fe-182">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
