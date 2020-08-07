---
title: 签入文件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VisualStudio.SourceControl.CheckInDialog
helpviewer_keywords:
- checking in files
ms.assetid: 0657a387-8411-4406-bef9-d262a5bfa269
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 070c1dfa5dd057cf777980f7022752a97a4dc84c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588064"
---
# <a name="check-in-files"></a><span data-ttu-id="37a45-102">签入文件</span><span class="sxs-lookup"><span data-stu-id="37a45-102">Check In Files</span></span>
  <span data-ttu-id="37a45-103">若要将已修改的源代码管理文件用于其他用户，必须将这些文件签入到源代码管理中。</span><span class="sxs-lookup"><span data-stu-id="37a45-103">To make source-controlled files that you have modified available to other users, you must check the files into source control.</span></span> <span data-ttu-id="37a45-104">签入文件时，所签入的版本将写入源代码管理提供程序，并成为文件的最新版本。</span><span class="sxs-lookup"><span data-stu-id="37a45-104">When you check in a file, the version you check in is written to the source control provider and becomes the latest version of the file.</span></span>  
  
 <span data-ttu-id="37a45-105">您可以使用 "**签入**" 命令签入文件。</span><span class="sxs-lookup"><span data-stu-id="37a45-105">You can use the **Check In** command to check in files.</span></span> <span data-ttu-id="37a45-106">如果使用该命令签入解决方案或项目，将同时签入该解决方案或项目中的所有文件。</span><span class="sxs-lookup"><span data-stu-id="37a45-106">If you use this command to check in a solution or project, all the files in the solution or project are also checked in.</span></span> <span data-ttu-id="37a45-107">但是，签入单个源代码文件则不会将其所属的项目或解决方案一起签入。</span><span class="sxs-lookup"><span data-stu-id="37a45-107">However, checking in an individual source code file does not result in the check-in of the project or solution to which it belongs.</span></span>  
  
### <a name="to-check-in-a-file"></a><span data-ttu-id="37a45-108">签入文件</span><span class="sxs-lookup"><span data-stu-id="37a45-108">To check in a file</span></span>  
  
1.  <span data-ttu-id="37a45-109">在解决方案资源管理器中，右键单击要签入的文件，然后单击 "**签入**"。</span><span class="sxs-lookup"><span data-stu-id="37a45-109">In Solution Explorer, right-click the file to check in, and then click **Check In**.</span></span>  
  
2.  <span data-ttu-id="37a45-110">如果出现 "**签入**" 对话框，请选择相应的选项，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="37a45-110">If the **Check In** dialog box appears, select the appropriate options, and then click **OK**.</span></span>  
  
     <span data-ttu-id="37a45-111">**登记**</span><span class="sxs-lookup"><span data-stu-id="37a45-111">**Check In**</span></span>  
     <span data-ttu-id="37a45-112">签入所有选定项。</span><span class="sxs-lookup"><span data-stu-id="37a45-112">Check in all the selected items.</span></span>  
  
     <span data-ttu-id="37a45-113">**“列”**</span><span class="sxs-lookup"><span data-stu-id="37a45-113">**Columns**</span></span>  
     <span data-ttu-id="37a45-114">标识要显示的列及其显示顺序。</span><span class="sxs-lookup"><span data-stu-id="37a45-114">Identify the columns to display and the order in which they are displayed.</span></span>  
  
     <span data-ttu-id="37a45-115">**注释**</span><span class="sxs-lookup"><span data-stu-id="37a45-115">**Comments**</span></span>  
     <span data-ttu-id="37a45-116">为签入操作添加相关注释。</span><span class="sxs-lookup"><span data-stu-id="37a45-116">Add a comment to associate with the check-in operation.</span></span>  
  
     <span data-ttu-id="37a45-117">**签入项时不显示“签入”对话框**</span><span class="sxs-lookup"><span data-stu-id="37a45-117">**Don't show Check in dialog box when checking in items**</span></span>  
     <span data-ttu-id="37a45-118">在签入操作过程中取消该对话框。</span><span class="sxs-lookup"><span data-stu-id="37a45-118">Suppress the dialog box during check-in operations.</span></span>  
  
     <span data-ttu-id="37a45-119">**平面视图**</span><span class="sxs-lookup"><span data-stu-id="37a45-119">**Flat View**</span></span>  
     <span data-ttu-id="37a45-120">将签入的文件在其源代码管理连接下显示为平面列表。</span><span class="sxs-lookup"><span data-stu-id="37a45-120">Display the files you are checking in as flat lists under their source control connection.</span></span>  
  
     <span data-ttu-id="37a45-121">**名称**</span><span class="sxs-lookup"><span data-stu-id="37a45-121">**Name**</span></span>  
     <span data-ttu-id="37a45-122">显示要签入的项的名称。</span><span class="sxs-lookup"><span data-stu-id="37a45-122">Displays the names of the items to check in.</span></span> <span data-ttu-id="37a45-123">所显示项旁边的复选框处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="37a45-123">Items appear with the check boxes next to them selected.</span></span> <span data-ttu-id="37a45-124">如果不希望签入特定的项，请清除其复选框。</span><span class="sxs-lookup"><span data-stu-id="37a45-124">If you do not want to check in a particular item, clear its check box.</span></span>  
  
     <span data-ttu-id="37a45-125">**选项**</span><span class="sxs-lookup"><span data-stu-id="37a45-125">**Options**</span></span>  
     <span data-ttu-id="37a45-126">单击按钮右侧的箭头时，显示源代码管理插件特定的签入选项。</span><span class="sxs-lookup"><span data-stu-id="37a45-126">Displays source control plug-in-specific check-in options when the arrow to the right of the button is clicked.</span></span>  
  
     <span data-ttu-id="37a45-127">**Sort**</span><span class="sxs-lookup"><span data-stu-id="37a45-127">**Sort**</span></span>  
     <span data-ttu-id="37a45-128">对显示列进行排序。</span><span class="sxs-lookup"><span data-stu-id="37a45-128">Sort the order of the display columns.</span></span>  
  
     <span data-ttu-id="37a45-129">**树视图**</span><span class="sxs-lookup"><span data-stu-id="37a45-129">**Tree View**</span></span>  
     <span data-ttu-id="37a45-130">显示所签入项的文件夹和文件层次结构。</span><span class="sxs-lookup"><span data-stu-id="37a45-130">Display the folder and file hierarchy for the items you are checking in.</span></span>  
  
 <span data-ttu-id="37a45-131">如果已签入的文件不是以共享方式签出的文件的一部分，则 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 环境将立即签入该文件。</span><span class="sxs-lookup"><span data-stu-id="37a45-131">If the file you have checked in is not part of a shared checkout, the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] environment checks in the file immediately.</span></span> <span data-ttu-id="37a45-132">否则，它可能提示您将您的版本与其他用户创建的版本合并。</span><span class="sxs-lookup"><span data-stu-id="37a45-132">Otherwise, it may prompt you to merge your version with versions created by other users.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37a45-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="37a45-133">See Also</span></span>  
 <span data-ttu-id="37a45-134">[查看已修改文件的列表](../../2014/database-engine/view-a-list-of-modified-files.md) </span><span class="sxs-lookup"><span data-stu-id="37a45-134">[View a List of Modified Files](../../2014/database-engine/view-a-list-of-modified-files.md) </span></span>  
 [<span data-ttu-id="37a45-135">管理签入</span><span class="sxs-lookup"><span data-stu-id="37a45-135">Manage Checkins</span></span>](../../2014/database-engine/manage-checkins.md)  
  
  
