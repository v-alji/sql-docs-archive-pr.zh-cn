---
title: 管理签出 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- source controls [SQL Server Management Studio], checkouts
- checkouts [SQL Server Management Studio]
- checking out files
ms.assetid: ddd4adba-d432-4005-9cb2-bb9ee3163d8e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cdfa25cdc27e707d4be705e66b215130c9d70ce1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591516"
---
# <a name="manage-checkouts"></a><span data-ttu-id="3c703-102">管理签出</span><span class="sxs-lookup"><span data-stu-id="3c703-102">Manage Checkouts</span></span>
  <span data-ttu-id="3c703-103">在将文件添加到源代码管理后，您必须签出该文件才能对其进行修改。</span><span class="sxs-lookup"><span data-stu-id="3c703-103">After a file has been added to source control, you must check out the file before you can modify it.</span></span> <span data-ttu-id="3c703-104">将文件签出源代码管理时，源代码管理提供程序会在本地磁盘中创建最新版本的副本并删除该文件的只读属性。</span><span class="sxs-lookup"><span data-stu-id="3c703-104">When you check a file out of source control, the source control provider creates a copy of the latest version on your local disk and removes the read-only attribute of the file.</span></span> <span data-ttu-id="3c703-105">在某些情况下，您可能需要在不签出文件的情况下编辑该文件。</span><span class="sxs-lookup"><span data-stu-id="3c703-105">In some circumstances you might need to edit a file without checking out the file.</span></span> <span data-ttu-id="3c703-106">有关在不签出文件的情况下编辑文件的详细信息，请参阅[编辑签入的文件](../../2014/database-engine/edit-checked-in-files.md)。</span><span class="sxs-lookup"><span data-stu-id="3c703-106">For more information about editing a file without checking the file out, see [Edit Checked-In Files](../../2014/database-engine/edit-checked-in-files.md).</span></span>  
  
 <span data-ttu-id="3c703-107">您可以使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 手动或自动签出文件。</span><span class="sxs-lookup"><span data-stu-id="3c703-107">You can use [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to check out files manually or automatically.</span></span> <span data-ttu-id="3c703-108">您可以通过在环境中打开包含文件的解决方案 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] ，然后单击 "**签出**" 命令来手动签出文件。</span><span class="sxs-lookup"><span data-stu-id="3c703-108">You check out files manually by opening the solution that contains the files in the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment, and then clicking the **Check Out** command.</span></span> <span data-ttu-id="3c703-109">如果将 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 环境配置为自动签出文件，则可以自动签出文件。</span><span class="sxs-lookup"><span data-stu-id="3c703-109">You can check out files automatically if you configure the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment to do so.</span></span>  
  
 <span data-ttu-id="3c703-110">根据管理员在源代码管理提供程序中设置的选项，还可以使用独占模式或共享模式签出文件。</span><span class="sxs-lookup"><span data-stu-id="3c703-110">Depending on the options that your administrator sets on your source control provider, you can also check out files in exclusive or shared mode.</span></span> <span data-ttu-id="3c703-111">当您以独占模式签出文件时，只有您能修改文件，在您将文件签入之前，其他任何用户都不能签出该文件。</span><span class="sxs-lookup"><span data-stu-id="3c703-111">When you check out a file exclusively, only you can modify it, and no other user can check out the file until you check it in.</span></span> <span data-ttu-id="3c703-112">当您以共享模式签出文件时，任何用户都可以签出同一文件。</span><span class="sxs-lookup"><span data-stu-id="3c703-112">When you check out a file in shared mode, any number of users can check out the same file.</span></span> <span data-ttu-id="3c703-113">每个用户签入文件时，源代码管理提供程序都会尝试将该文件与文件的最新服务器版本进行合并。</span><span class="sxs-lookup"><span data-stu-id="3c703-113">As each user checks in the file, the source control provider attempts to merge the file with the latest server version of the file.</span></span> <span data-ttu-id="3c703-114">如果在签入版本和最新版本之间存在冲突，源代码管理提供程序会提示用户解决这些冲突。</span><span class="sxs-lookup"><span data-stu-id="3c703-114">If conflicts arise between the version that is being checked in and the latest version, the source control provider prompts the user to resolve the conflicts.</span></span>  
  
 <span data-ttu-id="3c703-115">下表对本部分的主题进行了说明：</span><span class="sxs-lookup"><span data-stu-id="3c703-115">The following table describes the topics in this section.</span></span>  
  
|<span data-ttu-id="3c703-116">主题</span><span class="sxs-lookup"><span data-stu-id="3c703-116">Topic</span></span>|<span data-ttu-id="3c703-117">说明</span><span class="sxs-lookup"><span data-stu-id="3c703-117">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="3c703-118">签出文件</span><span class="sxs-lookup"><span data-stu-id="3c703-118">Check Out Files</span></span>](../../2014/database-engine/check-out-files.md)|<span data-ttu-id="3c703-119">提供了有关如何签出文件以便进行修改的说明。</span><span class="sxs-lookup"><span data-stu-id="3c703-119">Provides instructions on how to check out a file so you can modify it.</span></span>|  
|[<span data-ttu-id="3c703-120">撤消签出</span><span class="sxs-lookup"><span data-stu-id="3c703-120">Undo Checkouts</span></span>](../../2014/database-engine/undo-checkouts.md)|<span data-ttu-id="3c703-121">介绍如何取消现有的签出。</span><span class="sxs-lookup"><span data-stu-id="3c703-121">Explains how to cancel an existing checkout.</span></span>|  
|[<span data-ttu-id="3c703-122">在编辑时自动签出</span><span class="sxs-lookup"><span data-stu-id="3c703-122">Automatically Check Out Files Upon Edit</span></span>](../../2014/database-engine/automatically-check-out-files-upon-edit.md)|<span data-ttu-id="3c703-123">介绍如何配置源代码管理，以便在开始编辑文件时将其签出。</span><span class="sxs-lookup"><span data-stu-id="3c703-123">Explains how to configure source control to check out a file when you start to edit it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3c703-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3c703-124">See Also</span></span>  
 <span data-ttu-id="3c703-125">[管理签入](../../2014/database-engine/manage-checkins.md) </span><span class="sxs-lookup"><span data-stu-id="3c703-125">[Manage Checkins](../../2014/database-engine/manage-checkins.md) </span></span>  
 [<span data-ttu-id="3c703-126">编辑签入文件</span><span class="sxs-lookup"><span data-stu-id="3c703-126">Edit Checked-In Files</span></span>](../../2014/database-engine/edit-checked-in-files.md)  
  
  
