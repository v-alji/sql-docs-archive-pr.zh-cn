---
title: Microsoft 复制冲突查看器（事务复制）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replconflictviewer.cvqueued.f1
ms.assetid: eec59d8e-cadb-4623-a31f-9f42ec09c97f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8cc3f2ea3d1d2b29fba9c9d9121e23bf4bcd88bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576674"
---
# <a name="microsoft-replication-conflict-viewer-transactional-replication"></a><span data-ttu-id="c43d1-102">Microsoft 复制冲突查看器（事务复制）</span><span class="sxs-lookup"><span data-stu-id="c43d1-102">Microsoft Replication Conflict Viewer (Transactional Replication)</span></span>
  <span data-ttu-id="c43d1-103">利用复制冲突查看器，您可以查看同步期间对等事务复制和具有排队更新订阅的事务复制发生的冲突。</span><span class="sxs-lookup"><span data-stu-id="c43d1-103">The Replication Conflict Viewer enables you to view conflicts that have occurred during synchronization for peer-to-peer transactional replication and transactional replication with queued updating subscriptions.</span></span> <span data-ttu-id="c43d1-104">有关详细信息，请参阅[查看事务发布的数据冲突 (SQL Server Management Studio)](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="c43d1-104">For more information, see [View Data Conflicts for Transactional Publications &#40;SQL Server Management Studio&#41;](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c43d1-105">复制冲突查看器显示在合并复制和事务复制中发生的冲突。</span><span class="sxs-lookup"><span data-stu-id="c43d1-105">The Replication Conflict Viewer displays conflicts that occur in merge replication and in transactional replication.</span></span> <span data-ttu-id="c43d1-106">对于事务复制，可以使用复制冲突查看器查看冲突数据，但无法为冲突选择不同的解决方法。</span><span class="sxs-lookup"><span data-stu-id="c43d1-106">For transactional replication, you can use Replication Conflict Viewer to view conflict data, but you cannot choose a different resolution for the conflict.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c43d1-107">选项</span><span class="sxs-lookup"><span data-stu-id="c43d1-107">Options</span></span>  
 <span data-ttu-id="c43d1-108">复制冲突查看器划分为两个部分。</span><span class="sxs-lookup"><span data-stu-id="c43d1-108">The Replication Conflict Viewer is divided into two sections.</span></span> <span data-ttu-id="c43d1-109">对话框的上半部分显示所选表的冲突列表。</span><span class="sxs-lookup"><span data-stu-id="c43d1-109">The upper section of the dialog box shows the conflict list for the selected table.</span></span> <span data-ttu-id="c43d1-110">单击冲突列表中的项时，将在对话框的下半部分显示该冲突的详细信息。</span><span class="sxs-lookup"><span data-stu-id="c43d1-110">When you click an item in the conflict list, the details of the conflict are displayed in the lower section of the dialog box.</span></span>  
  
 <span data-ttu-id="c43d1-111">在下半部分中，冲突数据显示在两个相对应的列（**“冲突解决入选方”** 和 **“冲突解决落选方”**）中。</span><span class="sxs-lookup"><span data-stu-id="c43d1-111">The conflict data in the lower section is displayed in two corresponding columns (**Conflict Winner** and **Conflict Loser**).</span></span> <span data-ttu-id="c43d1-112">如果冲突发生在更新的数据和删除的数据之间，则对于冲突中删除的一方来说，可能没有可显示的数据。</span><span class="sxs-lookup"><span data-stu-id="c43d1-112">If the conflict is between updated and deleted data, there may be no data to show for the deleted side of the conflict.</span></span> <span data-ttu-id="c43d1-113">在这种情况下，复制冲突查看器会在其中一列中显示一条消息，指示在一个位置删除了该行，在另一个位置更新了该行。</span><span class="sxs-lookup"><span data-stu-id="c43d1-113">In this case, the Replication Conflict Viewer displays a message in one of the columns, indicating the row was deleted at one location and updated at another.</span></span> <span data-ttu-id="c43d1-114">此外，它还会指出建议的解决方法。</span><span class="sxs-lookup"><span data-stu-id="c43d1-114">It also indicates the suggested resolution.</span></span>  
  
 <span data-ttu-id="c43d1-115">**Database**</span><span class="sxs-lookup"><span data-stu-id="c43d1-115">**Database**</span></span>  
 <span data-ttu-id="c43d1-116">选择包含具有冲突的发布的数据库。</span><span class="sxs-lookup"><span data-stu-id="c43d1-116">Choose a database that includes publications with conflicts.</span></span>  
  
 <span data-ttu-id="c43d1-117">**发布**</span><span class="sxs-lookup"><span data-stu-id="c43d1-117">**Publication**</span></span>  
 <span data-ttu-id="c43d1-118">选择包含具有冲突的表的发布。</span><span class="sxs-lookup"><span data-stu-id="c43d1-118">Choose a publication that includes tables with conflicts.</span></span>  
  
 <span data-ttu-id="c43d1-119">**表**</span><span class="sxs-lookup"><span data-stu-id="c43d1-119">**Table**</span></span>  
 <span data-ttu-id="c43d1-120">选择包含冲突的表。</span><span class="sxs-lookup"><span data-stu-id="c43d1-120">Choose a table that includes conflicts.</span></span>  
  
 <span data-ttu-id="c43d1-121">**定义筛选器**</span><span class="sxs-lookup"><span data-stu-id="c43d1-121">**Define Filter**</span></span>  
 <span data-ttu-id="c43d1-122">单击此项可打开 **“定义筛选器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="c43d1-122">Click to open the **Define Filters** dialog box.</span></span>  
  
 <span data-ttu-id="c43d1-123">**应用或删除筛选器**</span><span class="sxs-lookup"><span data-stu-id="c43d1-123">**Apply or Remove Filter**</span></span>  
 <span data-ttu-id="c43d1-124">单击此项可应用或删除在 **“定义筛选器”** 对话框中定义的筛选器。</span><span class="sxs-lookup"><span data-stu-id="c43d1-124">Click to apply or remove a filter that has been defined in the **Define Filters** dialog box.</span></span>  
  
 <span data-ttu-id="c43d1-125">**全选**</span><span class="sxs-lookup"><span data-stu-id="c43d1-125">**Select All**</span></span>  
 <span data-ttu-id="c43d1-126">单击此项可选择网格中列出的所有冲突。</span><span class="sxs-lookup"><span data-stu-id="c43d1-126">Click to select all conflicts listed in the grid.</span></span>  
  
 <span data-ttu-id="c43d1-127">**选择无**</span><span class="sxs-lookup"><span data-stu-id="c43d1-127">**Select None**</span></span>  
 <span data-ttu-id="c43d1-128">单击此项可取消选择网格中列出的所有冲突。</span><span class="sxs-lookup"><span data-stu-id="c43d1-128">Click to deselect all conflicts listed in the grid.</span></span>  
  
 <span data-ttu-id="c43d1-129">**移除**</span><span class="sxs-lookup"><span data-stu-id="c43d1-129">**Remove**</span></span>  
 <span data-ttu-id="c43d1-130">单击此项可从查看器中删除所选冲突，并从复制系统表中删除与冲突关联的元数据。</span><span class="sxs-lookup"><span data-stu-id="c43d1-130">Click to remove selected conflicts from the viewer and their associated metadata from the replication system tables.</span></span>  
  
 <span data-ttu-id="c43d1-131">**显示所有列**</span><span class="sxs-lookup"><span data-stu-id="c43d1-131">**Show all columns**</span></span>  
 <span data-ttu-id="c43d1-132">选择此选项可显示表中的所有列。</span><span class="sxs-lookup"><span data-stu-id="c43d1-132">Select to show all columns of the table.</span></span>  
  
 <span data-ttu-id="c43d1-133">**显示前五列以及包含冲突数据的其他列**</span><span class="sxs-lookup"><span data-stu-id="c43d1-133">**Show first five columns and other columns with conflicting data**</span></span>  
 <span data-ttu-id="c43d1-134">选择此选项可显示前五列以及所有包含冲突的列。</span><span class="sxs-lookup"><span data-stu-id="c43d1-134">Select to display the first five columns and any columns that have conflicts.</span></span> <span data-ttu-id="c43d1-135">当表包含很多列，而您只想查看与解决冲突最相关的列时，这非常有用。</span><span class="sxs-lookup"><span data-stu-id="c43d1-135">This is helpful when the table has a large number of columns, but you want to see only the columns most relevant to resolving the conflict.</span></span> <span data-ttu-id="c43d1-136">前五列始终包含在此视图中，因为标识行的字段（如主键或名称字段）通常位于表的前几列中。</span><span class="sxs-lookup"><span data-stu-id="c43d1-136">The first five columns are always included in this view, as fields that identify a row, such as the primary key or name fields, are often among the first columns of the table.</span></span>  
  
 <span data-ttu-id="c43d1-137">**显示列信息** (**…**)</span><span class="sxs-lookup"><span data-stu-id="c43d1-137">**Display Column Information** (**...**)</span></span>  
 <span data-ttu-id="c43d1-138">单击此项可查看列信息： **“表名”**、 **“列名”**、 **“数据类型”** 和 **“列值”**。</span><span class="sxs-lookup"><span data-stu-id="c43d1-138">Click to view column information: **Table Name**, **Column Name**, **Data Type**, and **Column Value**.</span></span>  
  
 <span data-ttu-id="c43d1-139">**记录冲突详细信息**</span><span class="sxs-lookup"><span data-stu-id="c43d1-139">**Log the details of the conflict**</span></span>  
 <span data-ttu-id="c43d1-140">选中此框可将冲突的详细信息记录到文件。</span><span class="sxs-lookup"><span data-stu-id="c43d1-140">Check this box to log the details of the conflict to a file.</span></span> <span data-ttu-id="c43d1-141">若要指定文件的位置，请指向 **“视图”** 菜单，再单击 **“选项”**。</span><span class="sxs-lookup"><span data-stu-id="c43d1-141">To specify a location for the file, point to the **View** menu and click **Options**.</span></span> <span data-ttu-id="c43d1-142">输入一个值，或单击 **“浏览(...)”**，然后导航到相应的文件。</span><span class="sxs-lookup"><span data-stu-id="c43d1-142">Enter a value, or click the browse (**...**) and navigate to the appropriate file.</span></span> <span data-ttu-id="c43d1-143">单击 **“确定”** 可退出 **“选项”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="c43d1-143">Click **OK** to exit the **Options** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c43d1-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c43d1-144">See Also</span></span>  
 <span data-ttu-id="c43d1-145">[对等复制中的冲突检测](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md) </span><span class="sxs-lookup"><span data-stu-id="c43d1-145">[Conflict Detection in Peer-to-Peer Replication](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md) </span></span>  
 [<span data-ttu-id="c43d1-146">查看事务发布的数据冲突 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="c43d1-146">View Data Conflicts for Transactional Publications &#40;SQL Server Management Studio&#41;</span></span>](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)  
  
  
