---
title: 管理签入 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- checkins [SQL Server Management Studio]
- checking in files
- source controls [SQL Server Management Studio], checkins
ms.assetid: 293e60f3-15e3-4258-b73a-8baabe15c760
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a868aafff6d9bd389671544b5f1898e82707d933
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591521"
---
# <a name="manage-checkins"></a><span data-ttu-id="0608f-102">管理签入</span><span class="sxs-lookup"><span data-stu-id="0608f-102">Manage Checkins</span></span>
  <span data-ttu-id="0608f-103">要将对源代码管理文件所做的更改应用于其他用户，必须签入此文件。</span><span class="sxs-lookup"><span data-stu-id="0608f-103">To make changes to a source-controlled file available to other users, you must check in the file.</span></span> <span data-ttu-id="0608f-104">签入文件时，已创建的版本将复制到源代码管理提供程序，并成为文件的最新版本。具有相应权限的用户通常可使用此版本。</span><span class="sxs-lookup"><span data-stu-id="0608f-104">When you check in a file, the version you have created is copied to the source control provider, becomes the latest version of the file, and is generally available to users who have the appropriate permissions.</span></span>  
  
 <span data-ttu-id="0608f-105">使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 签入文件。</span><span class="sxs-lookup"><span data-stu-id="0608f-105">Use [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to check in files.</span></span> <span data-ttu-id="0608f-106">如果您不但需要定期更新源代码管理存储区，而且需要控制一组文件，则可以指定签入的文件仍对您保持签出状态。</span><span class="sxs-lookup"><span data-stu-id="0608f-106">When you need to update the source control store periodically, but also need to maintain control over a set of files, you can specify that files you check in remain checked out to you.</span></span>  
  
 <span data-ttu-id="0608f-107">下表对本部分的主题进行了说明：</span><span class="sxs-lookup"><span data-stu-id="0608f-107">The following table describes the topics in this section.</span></span>  
  
|<span data-ttu-id="0608f-108">主题</span><span class="sxs-lookup"><span data-stu-id="0608f-108">Topic</span></span>|<span data-ttu-id="0608f-109">说明</span><span class="sxs-lookup"><span data-stu-id="0608f-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="0608f-110">签入文件</span><span class="sxs-lookup"><span data-stu-id="0608f-110">Check In Files</span></span>](../../2014/database-engine/check-in-files.md)|<span data-ttu-id="0608f-111">介绍如何签入已修改的文件。</span><span class="sxs-lookup"><span data-stu-id="0608f-111">Provides instructions on how to check in a file you have modified.</span></span>|  
|[<span data-ttu-id="0608f-112">查看已修改的文件列表</span><span class="sxs-lookup"><span data-stu-id="0608f-112">View a List of Modified Files</span></span>](../../2014/database-engine/view-a-list-of-modified-files.md)|<span data-ttu-id="0608f-113">介绍如何在完成工作时显示一个可以一起签入的已修改文件列表。</span><span class="sxs-lookup"><span data-stu-id="0608f-113">Explains how to display a list of modified files that you can check in together when you are finished working.</span></span>|  
|[<span data-ttu-id="0608f-114">编辑签入文件</span><span class="sxs-lookup"><span data-stu-id="0608f-114">Edit Checked-In Files</span></span>](../../2014/database-engine/edit-checked-in-files.md)|<span data-ttu-id="0608f-115">介绍如何配置 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 环境，以便修改未签出的文件。</span><span class="sxs-lookup"><span data-stu-id="0608f-115">Explains how to configure the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] environment so that you can modify files that are not checked out.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0608f-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0608f-116">See Also</span></span>  
 [<span data-ttu-id="0608f-117">管理签出</span><span class="sxs-lookup"><span data-stu-id="0608f-117">Manage Checkouts</span></span>](../../2014/database-engine/manage-checkouts.md)  
  
  
