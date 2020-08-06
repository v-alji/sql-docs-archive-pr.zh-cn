---
title: 将版本指定为最新版本 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- version control services [SQL Server], latest version
- latest file version specified
- file versions [SQL Server]
ms.assetid: 407dffb1-3ecf-461e-835d-124781f26ee7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: dafe4f757e33a5db63340c3d3cc7c9151871d438
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577810"
---
# <a name="specify-a-version-as-the-latest-version"></a><span data-ttu-id="697a6-102">将版本指定为最新版本</span><span class="sxs-lookup"><span data-stu-id="697a6-102">Specify a Version as the Latest Version</span></span>
  <span data-ttu-id="697a6-103">将文件签入源代码管理中时，您签入的版本会成为最新版本；签出或检索最新版本的用户将接收到最近签入项的本地副本。</span><span class="sxs-lookup"><span data-stu-id="697a6-103">When you check a file into source control, the version you check in becomes the latest version; users who check out or retrieve the latest version receive local copies of the item most recently checked in.</span></span>  
  
 <span data-ttu-id="697a6-104">但在某些情况下，您可能要把某项的早期版本指定为最新版本。</span><span class="sxs-lookup"><span data-stu-id="697a6-104">However, in some situations, you may want to designate an earlier version of an item as the latest version.</span></span> <span data-ttu-id="697a6-105">例如，您先签出文件、修改文件，然后又签入文件。</span><span class="sxs-lookup"><span data-stu-id="697a6-105">For example, you check out a file, modify the file, and then check the file in.</span></span> <span data-ttu-id="697a6-106">但后来又决定放弃所做的修改。</span><span class="sxs-lookup"><span data-stu-id="697a6-106">You later decide to discard your modifications.</span></span> <span data-ttu-id="697a6-107">因为您已签入该项，所以不能选择撤消原来的签出。</span><span class="sxs-lookup"><span data-stu-id="697a6-107">Because you have checked in the item, undoing your original checkout is not an option.</span></span> <span data-ttu-id="697a6-108">在此情况下，可以将最初签出的版本指定为该项的最新版本。</span><span class="sxs-lookup"><span data-stu-id="697a6-108">In this situation, you can designate the version you originally checked out as the latest version of the item.</span></span>  
  
 <span data-ttu-id="697a6-109">指定最新版本的方法包括：</span><span class="sxs-lookup"><span data-stu-id="697a6-109">You can designate the latest version by:</span></span>  
  
-   <span data-ttu-id="697a6-110">**固定版本**。</span><span class="sxs-lookup"><span data-stu-id="697a6-110">**Pinning a version**.</span></span> <span data-ttu-id="697a6-111">驻留文件版本时，将不会删除比驻留版本更新的版本。</span><span class="sxs-lookup"><span data-stu-id="697a6-111">When you pin a file version, versions that are more recent than the pinned version are not deleted.</span></span> <span data-ttu-id="697a6-112">此外，可以对以前驻留的文件取消驻留。</span><span class="sxs-lookup"><span data-stu-id="697a6-112">In addition, you can unpin a file that you have previously pinned.</span></span> <span data-ttu-id="697a6-113">执行此操作时，最近签入的文件版本将成为最新版本。</span><span class="sxs-lookup"><span data-stu-id="697a6-113">When you do this, the most recently checked in version of the file becomes the latest version.</span></span> <span data-ttu-id="697a6-114">但不能签出已驻留的文件。</span><span class="sxs-lookup"><span data-stu-id="697a6-114">However, you cannot check out a pinned file.</span></span>  
  
-   <span data-ttu-id="697a6-115">回退**到指定的版本**。</span><span class="sxs-lookup"><span data-stu-id="697a6-115">**Rolling back to a specified version**.</span></span> <span data-ttu-id="697a6-116">回滚到某版本时，将会从源代码管理中删除比所回滚版本更新的所有版本。</span><span class="sxs-lookup"><span data-stu-id="697a6-116">When you roll back to a version, all versions more recent than the one to which you have rolled back are deleted from source control.</span></span> <span data-ttu-id="697a6-117">然后，您可以签出其余版本中的最新版本。</span><span class="sxs-lookup"><span data-stu-id="697a6-117">You can then check out the latest remaining version.</span></span>  
  
### <a name="to-pin-a-version"></a><span data-ttu-id="697a6-118">驻留版本</span><span class="sxs-lookup"><span data-stu-id="697a6-118">To pin a version</span></span>  
  
1.  <span data-ttu-id="697a6-119">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中，打开该解决方案。</span><span class="sxs-lookup"><span data-stu-id="697a6-119">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], open the solution.</span></span>  
  
2.  <span data-ttu-id="697a6-120">在解决方案资源管理器中，选择要指定为最新版本的文件。</span><span class="sxs-lookup"><span data-stu-id="697a6-120">In Solution Explorer, select the file that you want to specify as the latest version.</span></span>  
  
3.  <span data-ttu-id="697a6-121">在 "**文件**" 菜单上，指向 "**源代码管理**"，然后单击 " **ViewHistory**"。</span><span class="sxs-lookup"><span data-stu-id="697a6-121">On the **File** menu, point to **Source Control** and click **ViewHistory**.</span></span>  
  
4.  <span data-ttu-id="697a6-122">在 "**历史记录**" \<file> 对话框中，选择要指定为最新版本的版本，然后单击 "**固定**"。</span><span class="sxs-lookup"><span data-stu-id="697a6-122">In the **History of** \<file> dialog box, select the version that you want to specify as the latest, and click **Pin**.</span></span>  
  
     <span data-ttu-id="697a6-123">所选版本旁边会显示一个驻留符号，表示该版本是当前文件版本。</span><span class="sxs-lookup"><span data-stu-id="697a6-123">A pin symbol appears next to the version you have selected, indicating that it is the current file version.</span></span> <span data-ttu-id="697a6-124">如果在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中加载了其他版本，则会提示您重新加载该文件。</span><span class="sxs-lookup"><span data-stu-id="697a6-124">If you have a different version loaded in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], you are prompted to reload the file.</span></span>  
  
### <a name="to-roll-back-to-a-version"></a><span data-ttu-id="697a6-125">回滚到某一版本</span><span class="sxs-lookup"><span data-stu-id="697a6-125">To roll back to a version</span></span>  
  
1.  <span data-ttu-id="697a6-126">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中，打开该解决方案。</span><span class="sxs-lookup"><span data-stu-id="697a6-126">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], open the solution.</span></span>  
  
2.  <span data-ttu-id="697a6-127">在解决方案资源管理器中，选择要指定作为最新版本的项。</span><span class="sxs-lookup"><span data-stu-id="697a6-127">In Solution Explorer, select the item that you want to specify as the latest version.</span></span>  
  
3.  <span data-ttu-id="697a6-128">在 "**文件**" 菜单上，指向 "**源代码管理**"，然后单击 "**历史记录**"。</span><span class="sxs-lookup"><span data-stu-id="697a6-128">On the **File** menu, point to **Source Control** and click **History**.</span></span>  
  
4.  <span data-ttu-id="697a6-129">在 "**历史记录选项**" 对话框中，单击 **"确定"** 以显示 "**文件的历史记录**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="697a6-129">In the **History Options** dialog box, click **OK** to display the **History of File** dialog box.</span></span>  
  
5.  <span data-ttu-id="697a6-130">在 "**文件的历史记录**" 框中，选择要指定为最新版本的版本，然后单击 "**回滚**"。</span><span class="sxs-lookup"><span data-stu-id="697a6-130">In the **History of File** box, select the version you want to specify as the latest version, and click **Rollback**.</span></span>  
  
     <span data-ttu-id="697a6-131">此时屏幕上显示一条消息，提示选定版本之后的所有版本都将被删除。</span><span class="sxs-lookup"><span data-stu-id="697a6-131">A message appears notifying you that all versions subsequent to the one you have selected will be deleted.</span></span>  
  
6.  <span data-ttu-id="697a6-132">单击 **"是"** 以回滚到选定版本。</span><span class="sxs-lookup"><span data-stu-id="697a6-132">Click **Yes** to roll back to the selected version.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="697a6-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="697a6-133">See Also</span></span>  
 <span data-ttu-id="697a6-134">[管理签入](../../2014/database-engine/manage-checkins.md) </span><span class="sxs-lookup"><span data-stu-id="697a6-134">[Manage Checkins](../../2014/database-engine/manage-checkins.md) </span></span>  
 [<span data-ttu-id="697a6-135">签入文件</span><span class="sxs-lookup"><span data-stu-id="697a6-135">Check In Files</span></span>](../../2014/database-engine/check-in-files.md)  
  
  
