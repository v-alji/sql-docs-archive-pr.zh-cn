---
title: 签出文件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- Visual Studio.SourceControl.CheckOutDialog
helpviewer_keywords:
- checking out files
ms.assetid: cc033727-51bb-4b58-a12b-8977ce61ff56
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 151f554742bd6c381b27b58155d3f0e40e9eeb0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588063"
---
# <a name="check-out-files"></a><span data-ttu-id="c4c3c-102">签出文件</span><span class="sxs-lookup"><span data-stu-id="c4c3c-102">Check Out Files</span></span>
  <span data-ttu-id="c4c3c-103">除非已经将 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 环境配置为允许编辑已签入的文件，否则，必须先签出该文件后才可以进行修改。</span><span class="sxs-lookup"><span data-stu-id="c4c3c-103">Unless you have configured the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] environment to permit checked-in files to be edited, you must check out a file before you can modify it.</span></span> <span data-ttu-id="c4c3c-104">签出文件时，该文件版本的副本将复制到本地磁盘，并删除文件的只读属性。</span><span class="sxs-lookup"><span data-stu-id="c4c3c-104">When you check out a file, a copy of the file version is copied to your local disk, and the read-only attribute of the file is removed.</span></span>  
  
 <span data-ttu-id="c4c3c-105">可以独占或以共享模式签出文件。</span><span class="sxs-lookup"><span data-stu-id="c4c3c-105">You can check files out either exclusively or in shared mode.</span></span> <span data-ttu-id="c4c3c-106">如果以独占模式签出文件，则其他任何用户均不能签出该文件，直到您将该文件签入。</span><span class="sxs-lookup"><span data-stu-id="c4c3c-106">When you check out a file exclusively, no other user can check out the file until you check it in.</span></span> <span data-ttu-id="c4c3c-107">当以共享模式签出文件时，其他用户可以签出并修改该文件，当您签入文件时，可能需要将您已经签出的版本与其他用户创建的版本进行合并。</span><span class="sxs-lookup"><span data-stu-id="c4c3c-107">When you check out a file in shared mode, other users can check out and modify the file, and when you check it in, you may need to merge the version you have checked out with the versions created by other users.</span></span>  
  
 <span data-ttu-id="c4c3c-108">使用 "**签出**" 命令签出源代码管理的项目和文件。</span><span class="sxs-lookup"><span data-stu-id="c4c3c-108">Use the **Check Out** command to check out source-controlled projects and files.</span></span> <span data-ttu-id="c4c3c-109">如果使用此命令签出解决方案或项目，则也将签出解决方案或项目中的所有文件。但是，签出单个源代码文件不会导致签出它所属的项目或解决方案。</span><span class="sxs-lookup"><span data-stu-id="c4c3c-109">If you use this command to check out a solution or project, all the files in the solution or project are also checked out. However, checking out an individual source code file does not result in the check out of the project or solution to which it belongs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c4c3c-110">如果 [!INCLUDE[msCoName](../includes/msconame-md.md)] 你的项目的 Visual SourceSafe 数据库配置为允许多次签出，并且你想要以独占方式签出文件，则必须先清除 "**高级签出选项**" 对话框中的 "**允许多个签**出" 选项，然后才能签出该文件。</span><span class="sxs-lookup"><span data-stu-id="c4c3c-110">If the [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe database for your project is configured to allow multiple checkouts, and you want to check out a file exclusively, you must clear the **Allow multiple checkouts** option in the **Advanced Check Out Options** dialog box before checking out the file.</span></span> <span data-ttu-id="c4c3c-111">必须重新启动 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]，该设置才能生效。</span><span class="sxs-lookup"><span data-stu-id="c4c3c-111">You must restart the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] for this setting to take effect.</span></span>  
  
### <a name="to-check-out-a-file"></a><span data-ttu-id="c4c3c-112">签出文件</span><span class="sxs-lookup"><span data-stu-id="c4c3c-112">To check out a file</span></span>  
  
1.  <span data-ttu-id="c4c3c-113">在解决方案资源管理器中，选择项目或文件。</span><span class="sxs-lookup"><span data-stu-id="c4c3c-113">In Solution Explorer, select the project or file.</span></span>  
  
2.  <span data-ttu-id="c4c3c-114">在 "**文件**" 菜单上，指向 "**源代码管理**"，然后单击 "**签出以进行编辑**"。</span><span class="sxs-lookup"><span data-stu-id="c4c3c-114">On the **File** menu, point to **Source Control**, and then click **Check Out for Edit**.</span></span>  
  
3.  <span data-ttu-id="c4c3c-115">如果显示 "**签出以进行编辑**" 对话框，请选择所需的项，然后单击 "**签出**"。如果已将环境配置 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 为不显示 "**签出**" 对话框，则会立即签出在解决方案资源管理器中选择的项以及它们可能具有的任何子项。</span><span class="sxs-lookup"><span data-stu-id="c4c3c-115">If the **Check Out for Edit** dialog box is displayed, select the items you want, and click **Check Out**. If you have configured the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment not to display the **Check Out** dialog box, the items selected in Solution Explorer and any children they might have are checked out immediately.</span></span>  
  
     <span data-ttu-id="c4c3c-116">**退房**</span><span class="sxs-lookup"><span data-stu-id="c4c3c-116">**Check Out**</span></span>  
     <span data-ttu-id="c4c3c-117">签出所有选定项。</span><span class="sxs-lookup"><span data-stu-id="c4c3c-117">Check out all the selected items.</span></span>  
  
     <span data-ttu-id="c4c3c-118">**“列”**</span><span class="sxs-lookup"><span data-stu-id="c4c3c-118">**Columns**</span></span>  
     <span data-ttu-id="c4c3c-119">标识要显示的列及其显示顺序。</span><span class="sxs-lookup"><span data-stu-id="c4c3c-119">Identify the columns to display and the order in which they are displayed.</span></span>  
  
     <span data-ttu-id="c4c3c-120">**注释**</span><span class="sxs-lookup"><span data-stu-id="c4c3c-120">**Comments**</span></span>  
     <span data-ttu-id="c4c3c-121">指定与该签出操作关联的注释。</span><span class="sxs-lookup"><span data-stu-id="c4c3c-121">Specify a comment to associate with the checkout operation.</span></span>  
  
     <span data-ttu-id="c4c3c-122">**签出项时不显示“签出”对话框**</span><span class="sxs-lookup"><span data-stu-id="c4c3c-122">**Don't Show Check Out dialog box when checking out items**</span></span>  
     <span data-ttu-id="c4c3c-123">在签出操作过程中取消该对话框。</span><span class="sxs-lookup"><span data-stu-id="c4c3c-123">Suppress the dialog box during checkout operations.</span></span>  
  
     <span data-ttu-id="c4c3c-124">**平面视图**</span><span class="sxs-lookup"><span data-stu-id="c4c3c-124">**Flat View**</span></span>  
     <span data-ttu-id="c4c3c-125">将签出的项在其源代码管理连接下显示为平面列表。</span><span class="sxs-lookup"><span data-stu-id="c4c3c-125">Display the items you are checking out as flat lists under their source control connection.</span></span>  
  
     <span data-ttu-id="c4c3c-126">**编辑**</span><span class="sxs-lookup"><span data-stu-id="c4c3c-126">**Edit**</span></span>  
     <span data-ttu-id="c4c3c-127">修改项但不将其签出。仅**Edit**当你已将 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 配置为支持编辑签入文件时，才会显示 "编辑" 按钮。</span><span class="sxs-lookup"><span data-stu-id="c4c3c-127">Modify an item without checking it out. The **Edit** button appears only if you have [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] configured to support the editing of checked-in files.</span></span>  
  
     <span data-ttu-id="c4c3c-128">**名称**</span><span class="sxs-lookup"><span data-stu-id="c4c3c-128">**Name**</span></span>  
     <span data-ttu-id="c4c3c-129">显示可签出的项的名称。</span><span class="sxs-lookup"><span data-stu-id="c4c3c-129">Displays the names of the items available for checkout.</span></span> <span data-ttu-id="c4c3c-130">选定的项旁边还会显示复选框。</span><span class="sxs-lookup"><span data-stu-id="c4c3c-130">Items that are selected appear with check boxes next to them.</span></span> <span data-ttu-id="c4c3c-131">如果不希望签出特定的项，请清除其复选框。</span><span class="sxs-lookup"><span data-stu-id="c4c3c-131">If you do not want to check out a particular item, clear its check box.</span></span>  
  
     <span data-ttu-id="c4c3c-132">**选项**</span><span class="sxs-lookup"><span data-stu-id="c4c3c-132">**Options**</span></span>  
     <span data-ttu-id="c4c3c-133">单击按钮右侧的箭头时，显示源代码管理插件特定的签出选项。</span><span class="sxs-lookup"><span data-stu-id="c4c3c-133">Displays source control plug-in-specific checkout options when the arrow to the right of the button is clicked.</span></span>  
  
     <span data-ttu-id="c4c3c-134">**Sort**</span><span class="sxs-lookup"><span data-stu-id="c4c3c-134">**Sort**</span></span>  
     <span data-ttu-id="c4c3c-135">对显示的列进行排序。</span><span class="sxs-lookup"><span data-stu-id="c4c3c-135">Sort the order of the displayed columns.</span></span>  
  
     <span data-ttu-id="c4c3c-136">**树视图**</span><span class="sxs-lookup"><span data-stu-id="c4c3c-136">**Tree View**</span></span>  
     <span data-ttu-id="c4c3c-137">显示所签出项的文件夹和文件层次结构。</span><span class="sxs-lookup"><span data-stu-id="c4c3c-137">Display the folder and file hierarchy for the item you are checking out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4c3c-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c4c3c-138">See Also</span></span>  
 <span data-ttu-id="c4c3c-139">[编辑签入的文件](../../2014/database-engine/edit-checked-in-files.md) </span><span class="sxs-lookup"><span data-stu-id="c4c3c-139">[Edit Checked-In Files](../../2014/database-engine/edit-checked-in-files.md) </span></span>  
 <span data-ttu-id="c4c3c-140">[编辑时自动签出文件](../../2014/database-engine/automatically-check-out-files-upon-edit.md) </span><span class="sxs-lookup"><span data-stu-id="c4c3c-140">[Automatically Check Out Files Upon Edit](../../2014/database-engine/automatically-check-out-files-upon-edit.md) </span></span>  
 <span data-ttu-id="c4c3c-141">[撤消签出](../../2014/database-engine/undo-checkouts.md) </span><span class="sxs-lookup"><span data-stu-id="c4c3c-141">[Undo Checkouts](../../2014/database-engine/undo-checkouts.md) </span></span>  
 [<span data-ttu-id="c4c3c-142">管理签出</span><span class="sxs-lookup"><span data-stu-id="c4c3c-142">Manage Checkouts</span></span>](../../2014/database-engine/manage-checkouts.md)  
  
  
