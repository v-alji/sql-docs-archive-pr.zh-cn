---
title: 查看已修改文件的列表 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VisualStudio.SourceControl.CheckinWindow
helpviewer_keywords:
- listing modified files
- modified files list [SQL Server]
- checking in files
ms.assetid: 1b053719-8500-4300-a169-fffca5801dd0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a2899ab9889908089d17b3c929e7bf4b2dfe2185
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589203"
---
# <a name="view-a-list-of-modified-files"></a><span data-ttu-id="478b6-102">查看已修改的文件列表</span><span class="sxs-lookup"><span data-stu-id="478b6-102">View a List of Modified Files</span></span>
  <span data-ttu-id="478b6-103">您可以使用 "**挂起签入**" 窗口显示当前解决方案中的已签出文件的列表，并通过单击一次按钮签入这些文件。</span><span class="sxs-lookup"><span data-stu-id="478b6-103">You can use the **Pending Checkins** window to display at all times a list of the checked-out files in the current solution, and to check in these files with a single button click.</span></span>  
  
### <a name="to-view-a-list-of-modified-files"></a><span data-ttu-id="478b6-104">查看已修改文件的列表</span><span class="sxs-lookup"><span data-stu-id="478b6-104">To view a list of modified files</span></span>  
  
1.  <span data-ttu-id="478b6-105">在 "**视图**" 菜单上，单击 "**挂起签入**"。</span><span class="sxs-lookup"><span data-stu-id="478b6-105">On the **View** menu, click **Pending Checkins**.</span></span>  
  
2.  <span data-ttu-id="478b6-106">若要签入选定的文件，请单击 "**签入**"。</span><span class="sxs-lookup"><span data-stu-id="478b6-106">To check in the selected files, click **Check In**.</span></span> <span data-ttu-id="478b6-107">或者，您可以将**挂起的签入**窗口停靠在环境的右侧， [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 以便您可以在完成工作时签入文件。</span><span class="sxs-lookup"><span data-stu-id="478b6-107">Alternatively, you can dock the **Pending Checkins** window on the right side of the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment so that you can check in the files when you are finished working.</span></span>  
  
     <span data-ttu-id="478b6-108">**登记**</span><span class="sxs-lookup"><span data-stu-id="478b6-108">**Check In**</span></span>  
     <span data-ttu-id="478b6-109">签入解决方案。</span><span class="sxs-lookup"><span data-stu-id="478b6-109">Checks in the solution.</span></span>  
  
     <span data-ttu-id="478b6-110">**注释**</span><span class="sxs-lookup"><span data-stu-id="478b6-110">**Comments**</span></span>  
     <span data-ttu-id="478b6-111">将纯文本注释与挂起的签入相关联。</span><span class="sxs-lookup"><span data-stu-id="478b6-111">Associates a plain text comment with the pending check in.</span></span> <span data-ttu-id="478b6-112">对于项目的每一个版本，都会创建一个与之关联的注释，该注释存储在源代码管理数据库中。</span><span class="sxs-lookup"><span data-stu-id="478b6-112">A comment is created and associated with each version of a project, and stored in the source control database.</span></span>  
  
     <span data-ttu-id="478b6-113">**选项**</span><span class="sxs-lookup"><span data-stu-id="478b6-113">**Options**</span></span>  
     <span data-ttu-id="478b6-114">指定在单击 "**签入**" 按钮时源控件应执行的操作。</span><span class="sxs-lookup"><span data-stu-id="478b6-114">Specifies the actions that source control should take when you click the **Check In** button.</span></span>  
  
    -   <span data-ttu-id="478b6-115">**保持所有签出**</span><span class="sxs-lookup"><span data-stu-id="478b6-115">**Keep All Checked Out**</span></span>  
  
         <span data-ttu-id="478b6-116">指定应将所做的更改写入源代码管理提供程序，但是这些文件应保持签出状态。</span><span class="sxs-lookup"><span data-stu-id="478b6-116">Specifies that your changes should be written to the source control provider but that the files should remain checked out.</span></span>  
  
     <span data-ttu-id="478b6-117">**Sort**</span><span class="sxs-lookup"><span data-stu-id="478b6-117">**Sort**</span></span>  
     <span data-ttu-id="478b6-118">指定“项”列表中所显示的列的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="478b6-118">Specifies the sort order for the columns displayed in the Items list.</span></span>  
  
     <span data-ttu-id="478b6-119">**“列”**</span><span class="sxs-lookup"><span data-stu-id="478b6-119">**Columns**</span></span>  
     <span data-ttu-id="478b6-120">显示可添加到窗口“项”列表中的列的列表。</span><span class="sxs-lookup"><span data-stu-id="478b6-120">Displays a list of the columns you can add to the window's Items list.</span></span>  
  
     <span data-ttu-id="478b6-121">**树视图**</span><span class="sxs-lookup"><span data-stu-id="478b6-121">**Tree View**</span></span>  
     <span data-ttu-id="478b6-122">显示要签入的解决方案或项目的文件夹和文件层次结构。</span><span class="sxs-lookup"><span data-stu-id="478b6-122">Displays the folder and file hierarchy for the solution or project you are checking in.</span></span>  
  
     <span data-ttu-id="478b6-123">**平面视图**</span><span class="sxs-lookup"><span data-stu-id="478b6-123">**Flat View**</span></span>  
     <span data-ttu-id="478b6-124">在其源代码管理连接下显示要签入的文件。</span><span class="sxs-lookup"><span data-stu-id="478b6-124">Displays the files you are checking in as flat lists under their source control connection.</span></span>  
  
     <span data-ttu-id="478b6-125">**版本比较**</span><span class="sxs-lookup"><span data-stu-id="478b6-125">**Compare Versions**</span></span>  
     <span data-ttu-id="478b6-126">打开 "Visual SourceSafe**差异选项**" 对话框，该对话框将您的开发环境项目中的选定文件与任何其他所选文件进行比较，并显示差异（如果有）。</span><span class="sxs-lookup"><span data-stu-id="478b6-126">Opens the Visual SourceSafe **Difference Options** dialog box, which compares a selected file in your development environment project to any other selected file and shows you the differences, if any.</span></span>  
  
     <span data-ttu-id="478b6-127">**撤消签出**</span><span class="sxs-lookup"><span data-stu-id="478b6-127">**Undo checkout**</span></span>  
     <span data-ttu-id="478b6-128">反转 "**挂起签入**" 窗口中选定的所有项的签出。</span><span class="sxs-lookup"><span data-stu-id="478b6-128">Reverses the checkout of all items selected in the **Pending Checkins** window.</span></span>  
  
     <span data-ttu-id="478b6-129">**名称**</span><span class="sxs-lookup"><span data-stu-id="478b6-129">**Name**</span></span>  
     <span data-ttu-id="478b6-130">显示可签入的项的列表。</span><span class="sxs-lookup"><span data-stu-id="478b6-130">Displays a list of the items available for check in.</span></span> <span data-ttu-id="478b6-131">这些项旁边所显示的复选框将处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="478b6-131">Items appear with the check box next to them selected.</span></span> <span data-ttu-id="478b6-132">如果您不希望签入特定项，请清除其旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="478b6-132">If you do not want to check in a particular item, clear the check box next to it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="478b6-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="478b6-133">See Also</span></span>  
 <span data-ttu-id="478b6-134">[管理签入](../../2014/database-engine/manage-checkins.md) </span><span class="sxs-lookup"><span data-stu-id="478b6-134">[Manage Checkins](../../2014/database-engine/manage-checkins.md) </span></span>  
 [<span data-ttu-id="478b6-135">管理签出</span><span class="sxs-lookup"><span data-stu-id="478b6-135">Manage Checkouts</span></span>](../../2014/database-engine/manage-checkouts.md)  
  
  
