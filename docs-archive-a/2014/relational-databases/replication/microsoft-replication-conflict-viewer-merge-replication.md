---
title: Microsoft 复制冲突查看器（合并复制）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replconflictviewer.cvmerge.f1
ms.assetid: bfef5e21-ac04-4bc5-a55e-595421e34923
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1354a35e06f58b56f9678267338917a272ff8b19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577562"
---
# <a name="microsoft-replication-conflict-viewer-merge-replication"></a><span data-ttu-id="b216b-102">Microsoft 复制冲突查看器（合并复制）</span><span class="sxs-lookup"><span data-stu-id="b216b-102">Microsoft Replication Conflict Viewer (Merge Replication)</span></span>
  <span data-ttu-id="b216b-103">使用复制冲突查看器，可以查看在复制同步过程中发生的所有冲突。</span><span class="sxs-lookup"><span data-stu-id="b216b-103">The Replication Conflict Viewer allows you to view any conflicts that have occurred during replication synchronization.</span></span> <span data-ttu-id="b216b-104">在两个不同的服务器上（例如，在发布服务器和订阅服务器上，或在两个不同的订阅服务器上）同时修改相同的数据时会发生冲突。</span><span class="sxs-lookup"><span data-stu-id="b216b-104">Conflicts occur when the same data is modified at two separate servers, for example, at a Publisher and Subscriber, or at two different Subscribers.</span></span> <span data-ttu-id="b216b-105">使用在创建时选择的冲突解决程序，复制可以自动解决冲突。</span><span class="sxs-lookup"><span data-stu-id="b216b-105">Replication automatically resolves conflicts using the conflict resolver you selected when the article was created.</span></span> <span data-ttu-id="b216b-106">不过，使用复制冲突查看器可以在必要时选择不同的冲突解决方法。</span><span class="sxs-lookup"><span data-stu-id="b216b-106">However, the Replication Conflict Viewer allows you to choose a different resolution for the conflict when necessary.</span></span> <span data-ttu-id="b216b-107">可能会发生下列冲突：</span><span class="sxs-lookup"><span data-stu-id="b216b-107">The following conflicts can occur:</span></span>  
  
-   <span data-ttu-id="b216b-108">更新冲突。</span><span class="sxs-lookup"><span data-stu-id="b216b-108">Update conflicts.</span></span> <span data-ttu-id="b216b-109">在两个位置更改相同的数据时会发生更新冲突。</span><span class="sxs-lookup"><span data-stu-id="b216b-109">Update conflicts occur when the same data is changed at two locations.</span></span> <span data-ttu-id="b216b-110">一个更改入选，而另一个更改落选。</span><span class="sxs-lookup"><span data-stu-id="b216b-110">One change wins, and the other one loses.</span></span> <span data-ttu-id="b216b-111">您可以选择保留现有数据（入选数据），使用与现有数据冲突的数据（落选数据）来覆盖现有数据，或合并入选数据和落选数据并更新现有数据。</span><span class="sxs-lookup"><span data-stu-id="b216b-111">You have the option to keep the existing data (the data that won), overwrite the existing data with the data that conflicted with it (the losing data), or merge the winning and losing data and update the existing data.</span></span>  
  
-   <span data-ttu-id="b216b-112">插入冲突。</span><span class="sxs-lookup"><span data-stu-id="b216b-112">Insert conflicts.</span></span> <span data-ttu-id="b216b-113">在一个位置插入行，当与其他位置所做的更改进行合并时，如果违反数据一致性规则，则会发生插入冲突。</span><span class="sxs-lookup"><span data-stu-id="b216b-113">Insert conflicts occur when a row is inserted at one location that violates some data consistency rule when merged with changes at other locations.</span></span> <span data-ttu-id="b216b-114">您可以选择保留现有数据（入选数据），使用与现有数据冲突的数据（落选数据）来覆盖现有数据，或合并入选数据和落选数据并更新现有数据。</span><span class="sxs-lookup"><span data-stu-id="b216b-114">You have the option to keep the existing data (the data that won), overwrite the existing data with the data that conflicted with it (the losing data), or merge the winning and losing data and update the existing data.</span></span>  
  
-   <span data-ttu-id="b216b-115">删除冲突。</span><span class="sxs-lookup"><span data-stu-id="b216b-115">Delete conflicts.</span></span> <span data-ttu-id="b216b-116">当在一个位置删除某行而在另一个位置更改同一行时，则会发生此冲突。</span><span class="sxs-lookup"><span data-stu-id="b216b-116">This conflict occurs when the same row is deleted at one location and changed at the other.</span></span>  
  
 <span data-ttu-id="b216b-117">在同步过程中解决冲突后，落选行的数据将写入冲突表中。</span><span class="sxs-lookup"><span data-stu-id="b216b-117">When conflicts are resolved during synchronization, the data from the losing row is written to a conflict table.</span></span> <span data-ttu-id="b216b-118">无论是接受原始解决方法还是选择其他解决方法来解决冲突，都将从冲突表中删除记录的冲突行。</span><span class="sxs-lookup"><span data-stu-id="b216b-118">Whether you accept the original resolution or choose a different resolution for the conflict, the logged conflict row is deleted from the conflict table.</span></span> <span data-ttu-id="b216b-119">应定期检查冲突以减小冲突跟踪表的大小。</span><span class="sxs-lookup"><span data-stu-id="b216b-119">You should periodically review conflicts to help reduce the size of the conflict tracking tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b216b-120">包含逻辑记录的冲突不会显示在冲突查看器中。</span><span class="sxs-lookup"><span data-stu-id="b216b-120">Conflicts that involve logical records are not displayed in Conflict Viewer.</span></span> <span data-ttu-id="b216b-121">若要查看有关这些冲突的信息，请使用复制存储过程。</span><span class="sxs-lookup"><span data-stu-id="b216b-121">To view information about these conflicts, use replication stored procedures.</span></span> <span data-ttu-id="b216b-122">有关详细信息，请参阅[查看合并发布的冲突信息（复制 Transact-SQL 编程）](view-conflict-information-for-merge-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="b216b-122">For more information, see [View Conflict Information for Merge Publications &#40;Replication Transact-SQL Programming&#41;](view-conflict-information-for-merge-publications.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="b216b-123">选项</span><span class="sxs-lookup"><span data-stu-id="b216b-123">Options</span></span>  
 <span data-ttu-id="b216b-124">复制冲突查看器划分为两个部分。</span><span class="sxs-lookup"><span data-stu-id="b216b-124">The Replication Conflict Viewer is divided into two sections.</span></span> <span data-ttu-id="b216b-125">对话框的上半部分显示所选表的冲突列表。</span><span class="sxs-lookup"><span data-stu-id="b216b-125">The upper section of the dialog box shows the conflict list for the selected table.</span></span> <span data-ttu-id="b216b-126">单击冲突列表中的项时，将在对话框的下半部分显示该冲突的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b216b-126">When you click an item in the conflict list, the details of the conflict are displayed in the lower section of the dialog box.</span></span>  
  
 <span data-ttu-id="b216b-127">在对话框的下半部分会显示相关信息，描述发生冲突的原因（例如，在发布服务器和订阅服务器上更新了同一行）。</span><span class="sxs-lookup"><span data-stu-id="b216b-127">Information describing why the conflict occurred (for example, the same row was updated at both the Publisher and the Subscriber) is displayed in the lower section of the dialog box.</span></span> <span data-ttu-id="b216b-128">在下半部分中，冲突数据显示在两个相对应的列（**“冲突解决入选方”** 和 **“冲突解决落选方”**）中。</span><span class="sxs-lookup"><span data-stu-id="b216b-128">The conflict data in the lower section is displayed in two corresponding columns (**Conflict Winner** and **Conflict Loser**).</span></span> <span data-ttu-id="b216b-129">如果冲突发生在更新的数据和删除的数据之间，则对于冲突中删除的一方来说，可能没有可显示的数据。</span><span class="sxs-lookup"><span data-stu-id="b216b-129">If the conflict is between updated and deleted data, there may be no data to show for the deleted side of the conflict.</span></span> <span data-ttu-id="b216b-130">在这种情况下，复制冲突查看器会在其中一列中显示一条消息，指示在一个位置删除了该行，在另一个位置更新了该行。</span><span class="sxs-lookup"><span data-stu-id="b216b-130">In this case, the Replication Conflict Viewer displays a message in one of the columns, indicating that the row was deleted at one location and updated at another.</span></span> <span data-ttu-id="b216b-131">此外，它还会指出建议的解决方法。</span><span class="sxs-lookup"><span data-stu-id="b216b-131">It also indicates the suggested resolution.</span></span>  
  
 <span data-ttu-id="b216b-132">不能在复制冲突查看器中编辑的数据（例如， **rowguid** 数据）以只读方式显示（方框带有阴影）。</span><span class="sxs-lookup"><span data-stu-id="b216b-132">Data that cannot be edited in the Replication Conflict Viewer (for example, **rowguid** data) is displayed read-only with the box shaded.</span></span>  
  
 <span data-ttu-id="b216b-133">**Database**</span><span class="sxs-lookup"><span data-stu-id="b216b-133">**Database**</span></span>  
 <span data-ttu-id="b216b-134">选择包含具有冲突的发布的数据库。</span><span class="sxs-lookup"><span data-stu-id="b216b-134">Choose a database that includes publications with conflicts.</span></span>  
  
 <span data-ttu-id="b216b-135">**发布**</span><span class="sxs-lookup"><span data-stu-id="b216b-135">**Publication**</span></span>  
 <span data-ttu-id="b216b-136">选择包含具有冲突的表的发布。</span><span class="sxs-lookup"><span data-stu-id="b216b-136">Choose a publication that includes tables with conflicts.</span></span>  
  
 <span data-ttu-id="b216b-137">**表**</span><span class="sxs-lookup"><span data-stu-id="b216b-137">**Table**</span></span>  
 <span data-ttu-id="b216b-138">选择包含冲突的表。</span><span class="sxs-lookup"><span data-stu-id="b216b-138">Choose a table that includes conflicts.</span></span>  
  
 <span data-ttu-id="b216b-139">**定义筛选器**</span><span class="sxs-lookup"><span data-stu-id="b216b-139">**Define Filter**</span></span>  
 <span data-ttu-id="b216b-140">单击此项可打开 **“定义筛选器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="b216b-140">Click to open the **Define Filters** dialog box.</span></span>  
  
 <span data-ttu-id="b216b-141">**应用或删除筛选器**</span><span class="sxs-lookup"><span data-stu-id="b216b-141">**Apply or Remove Filter**</span></span>  
 <span data-ttu-id="b216b-142">单击此项可应用或删除在 **“定义筛选器”** 对话框中定义的筛选器。</span><span class="sxs-lookup"><span data-stu-id="b216b-142">Click to apply or remove a filter that has been defined in the **Define Filters** dialog box.</span></span>  
  
 <span data-ttu-id="b216b-143">**全选**</span><span class="sxs-lookup"><span data-stu-id="b216b-143">**Select All**</span></span>  
 <span data-ttu-id="b216b-144">单击此项可选择网格中列出的所有冲突。</span><span class="sxs-lookup"><span data-stu-id="b216b-144">Click to select all conflicts listed in the grid.</span></span>  
  
 <span data-ttu-id="b216b-145">**选择无**</span><span class="sxs-lookup"><span data-stu-id="b216b-145">**Select None**</span></span>  
 <span data-ttu-id="b216b-146">单击此项可取消选择网格中列出的所有冲突。</span><span class="sxs-lookup"><span data-stu-id="b216b-146">Click to deselect all conflicts listed in the grid.</span></span>  
  
 <span data-ttu-id="b216b-147">**移除**</span><span class="sxs-lookup"><span data-stu-id="b216b-147">**Remove**</span></span>  
 <span data-ttu-id="b216b-148">单击此项可从查看器中删除所选冲突，并从复制系统表中删除与冲突关联的元数据。</span><span class="sxs-lookup"><span data-stu-id="b216b-148">Click to remove selected conflicts from the viewer and their associated metadata from the replication system tables.</span></span> <span data-ttu-id="b216b-149">等同于为所选的每个冲突单击“提交入选方”按钮（不对数据进行任何更改）。</span><span class="sxs-lookup"><span data-stu-id="b216b-149">Equivalent to clicking the Submit Winner button (without making any changes to the data) for each selected conflict.</span></span>  
  
 <span data-ttu-id="b216b-150">**显示所有列**</span><span class="sxs-lookup"><span data-stu-id="b216b-150">**Show all columns**</span></span>  
 <span data-ttu-id="b216b-151">选择此选项可显示表中的所有列。</span><span class="sxs-lookup"><span data-stu-id="b216b-151">Select to show all columns of the table.</span></span>  
  
 <span data-ttu-id="b216b-152">**显示前五列以及包含冲突数据的其他列**</span><span class="sxs-lookup"><span data-stu-id="b216b-152">**Show first five columns and other columns with conflicting data**</span></span>  
 <span data-ttu-id="b216b-153">选择此选项可显示前五列以及所有包含冲突的列。</span><span class="sxs-lookup"><span data-stu-id="b216b-153">Select to display the first five columns and any columns that have conflicts.</span></span> <span data-ttu-id="b216b-154">当表包含很多列，而您只想查看与解决冲突最相关的列时，这非常有用。</span><span class="sxs-lookup"><span data-stu-id="b216b-154">This is helpful when the table has a large number of columns, but you want to see only the columns most relevant to resolving the conflict.</span></span> <span data-ttu-id="b216b-155">前五列始终包含在此视图中，因为标识行的字段（如主键或名称字段）通常位于表的前几列中。</span><span class="sxs-lookup"><span data-stu-id="b216b-155">The first five columns are always included in this view, as fields that identify a row, such as the primary key or name fields, are often among the first columns of the table.</span></span>  
  
 <span data-ttu-id="b216b-156">**显示列信息** (**…**)</span><span class="sxs-lookup"><span data-stu-id="b216b-156">**Display Column Information** (**...**)</span></span>  
 <span data-ttu-id="b216b-157">单击此项可查看列信息： **“表名”**、 **“列名”**、 **“数据类型”** 和 **“列值”**。</span><span class="sxs-lookup"><span data-stu-id="b216b-157">Click to view column information: **Table Name**, **Column Name**, **Data Type**, and **Column Value**.</span></span> <span data-ttu-id="b216b-158">除非值显示为只读，否则 **“列值”** 是可编辑的。</span><span class="sxs-lookup"><span data-stu-id="b216b-158">**Column Value** is editable unless the value is displayed as read-only.</span></span>  
  
 <span data-ttu-id="b216b-159">**提交入选方**</span><span class="sxs-lookup"><span data-stu-id="b216b-159">**Submit Winner**</span></span>  
 <span data-ttu-id="b216b-160">单击此项可将冲突解决程序确定的行保留为入选方。</span><span class="sxs-lookup"><span data-stu-id="b216b-160">Click to keep the row the conflict resolver determined to be the winner.</span></span> <span data-ttu-id="b216b-161">在单击此按钮之前，可以更改未显示为只读的任何列的值。</span><span class="sxs-lookup"><span data-stu-id="b216b-161">The value of any column that is not displayed as read-only can be changed prior to clicking this button.</span></span>  
  
 <span data-ttu-id="b216b-162">**提交落选方**</span><span class="sxs-lookup"><span data-stu-id="b216b-162">**Submit Loser**</span></span>  
 <span data-ttu-id="b216b-163">单击此项可将冲突解决程序确定的行接受为落选方。</span><span class="sxs-lookup"><span data-stu-id="b216b-163">Click to accept the row the conflict resolver determined to be the loser.</span></span> <span data-ttu-id="b216b-164">在单击此按钮之前，可以更改未显示为只读的任何列的值。</span><span class="sxs-lookup"><span data-stu-id="b216b-164">The value of any column that is not displayed as read-only can be changed prior to clicking this button.</span></span>  
  
 <span data-ttu-id="b216b-165">**记录冲突详细信息**</span><span class="sxs-lookup"><span data-stu-id="b216b-165">**Log the details of the conflict**</span></span>  
 <span data-ttu-id="b216b-166">选中此框可将冲突的详细信息记录到文件。</span><span class="sxs-lookup"><span data-stu-id="b216b-166">Check this box to log the details of the conflict to a file.</span></span> <span data-ttu-id="b216b-167">若要指定文件的位置，请指向 **“视图”** 菜单，再单击 **“选项”**。</span><span class="sxs-lookup"><span data-stu-id="b216b-167">To specify a location for the file, point to the **View** menu and click **Options**.</span></span> <span data-ttu-id="b216b-168">输入一个值，或单击 **“浏览(...)”**，然后导航到相应的文件。</span><span class="sxs-lookup"><span data-stu-id="b216b-168">Enter a value, or click the browse (**...**) and navigate to the appropriate file.</span></span> <span data-ttu-id="b216b-169">单击 **“确定”** 可退出 **“选项”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="b216b-169">Click **OK** to exit the **Options** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b216b-170">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b216b-170">See Also</span></span>  
 <span data-ttu-id="b216b-171">[查看和解决合并发布的数据冲突 &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md) </span><span class="sxs-lookup"><span data-stu-id="b216b-171">[View and Resolve Data Conflicts for Merge Publications &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md) </span></span>  
 [<span data-ttu-id="b216b-172">Advanced Merge Replication Conflict Detection and Resolution</span><span class="sxs-lookup"><span data-stu-id="b216b-172">Advanced Merge Replication Conflict Detection and Resolution</span></span>](merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
