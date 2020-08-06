---
title: 设置和检索版本信息 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- historical information [SQL Server]
- source controls [SQL Server Management Studio], version information
- retrieving version information
- current file version information
- version control services [SQL Server], retrieving version information
- version control services [SQL Server], setting version information
- status information [SQL Server], source control files
- historical information [SQL Server], source control files
ms.assetid: c3f253c4-4e3d-48e8-8d90-bd6ee899faf7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: eff3d40ba9b663ba8611508c5b9f0c9961005b81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683043"
---
# <a name="set-and-retrieve-version-information"></a><span data-ttu-id="69222-102">设置和检索版本信息</span><span class="sxs-lookup"><span data-stu-id="69222-102">Set and Retrieve Version Information</span></span>
  <span data-ttu-id="69222-103">版本信息包括源代码管理的文件的历史记录和当前状态。</span><span class="sxs-lookup"><span data-stu-id="69222-103">Version information includes the history and current status of a source-controlled file.</span></span> <span data-ttu-id="69222-104">对于每个源代码管理的文件，[!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe 都将会维护其全面的历史记录，这样，您就可以跟踪一个或多个文件随时间变化的情况。</span><span class="sxs-lookup"><span data-stu-id="69222-104">For every source-controlled file, [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe maintains a comprehensive history, so you can track the evolution of one or more files over time.</span></span> <span data-ttu-id="69222-105">还可以使用该信息检索任何文件版本的本地副本，或比较任何两个文件版本。</span><span class="sxs-lookup"><span data-stu-id="69222-105">You can also use this information to retrieve a local copy of any version of the file or to compare any two file versions.</span></span>  
  
 <span data-ttu-id="69222-106">文件的历史记录包括：</span><span class="sxs-lookup"><span data-stu-id="69222-106">The history of a file includes:</span></span>  
  
-   <span data-ttu-id="69222-107">版本号，用来标识该版本在相同文件的其他版本中的序列。</span><span class="sxs-lookup"><span data-stu-id="69222-107">The version number, which identifies its sequence among other versions of the same file.</span></span>  
  
-   <span data-ttu-id="69222-108">已执行的操作。</span><span class="sxs-lookup"><span data-stu-id="69222-108">The action performed.</span></span> <span data-ttu-id="69222-109">跟踪的操作包括文件创建、签入和删除。</span><span class="sxs-lookup"><span data-stu-id="69222-109">Tracked operations include file creation, check in, and deletion.</span></span>  
  
-   <span data-ttu-id="69222-110">执行涉及该文件操作的人员的用户名。</span><span class="sxs-lookup"><span data-stu-id="69222-110">The user name of the person who performed an action involving the file.</span></span>  
  
-   <span data-ttu-id="69222-111">执行操作时的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="69222-111">The date and time when the operation was performed.</span></span>  
  
 <span data-ttu-id="69222-112">Visual SourceSafe 还维护有关当前已加载解决方案的当前状态信息。</span><span class="sxs-lookup"><span data-stu-id="69222-112">Visual SourceSafe also maintains current status information on the currently loaded solution.</span></span> <span data-ttu-id="69222-113">该信息提供了文件当前状态的快照，包括：</span><span class="sxs-lookup"><span data-stu-id="69222-113">This information provides a snapshot of the current state of the file, including:</span></span>  
  
-   <span data-ttu-id="69222-114">签出文件的用户标识。</span><span class="sxs-lookup"><span data-stu-id="69222-114">The identity of the user who has the file checked out.</span></span>  
  
-   <span data-ttu-id="69222-115">所选文件的最新版本号。</span><span class="sxs-lookup"><span data-stu-id="69222-115">The latest version number of the selected file.</span></span>  
  
-   <span data-ttu-id="69222-116">版本的创建日期。</span><span class="sxs-lookup"><span data-stu-id="69222-116">The date when the version was created.</span></span>  
  
-   <span data-ttu-id="69222-117">与版本关联的用户注释。</span><span class="sxs-lookup"><span data-stu-id="69222-117">The user comment associated with the version.</span></span>  
  
-   <span data-ttu-id="69222-118">用于共享文件的项目的路径。</span><span class="sxs-lookup"><span data-stu-id="69222-118">The paths to the projects with which the file is shared.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="69222-119">本节内容</span><span class="sxs-lookup"><span data-stu-id="69222-119">In This Section</span></span>  
  
-   [<span data-ttu-id="69222-120">查看文件历史记录</span><span class="sxs-lookup"><span data-stu-id="69222-120">View File History</span></span>](../../2014/database-engine/view-file-history.md)  
  
-   [<span data-ttu-id="69222-121">查看项目历史</span><span class="sxs-lookup"><span data-stu-id="69222-121">View Project History</span></span>](../../2014/database-engine/view-project-history.md)  
  
-   [<span data-ttu-id="69222-122">查看文件状态</span><span class="sxs-lookup"><span data-stu-id="69222-122">View File Status</span></span>](../../2014/database-engine/view-file-status.md)  
  
-   [<span data-ttu-id="69222-123">检索文件</span><span class="sxs-lookup"><span data-stu-id="69222-123">Retrieve Files</span></span>](../../2014/database-engine/retrieve-files.md)  
  
-   [<span data-ttu-id="69222-124">将版本指定为最新版本</span><span class="sxs-lookup"><span data-stu-id="69222-124">Specify a Version as the Latest Version</span></span>](../../2014/database-engine/specify-a-version-as-the-latest-version.md)  
  
-   [<span data-ttu-id="69222-125">比较文件</span><span class="sxs-lookup"><span data-stu-id="69222-125">Compare Files</span></span>](../../2014/database-engine/compare-files.md)  
  
-   [<span data-ttu-id="69222-126">共享文件</span><span class="sxs-lookup"><span data-stu-id="69222-126">Share Files</span></span>](../../2014/database-engine/share-files.md)  
  
-   [<span data-ttu-id="69222-127">创建历史记录和状态报表</span><span class="sxs-lookup"><span data-stu-id="69222-127">Create History and Status Reports</span></span>](../../2014/database-engine/create-history-and-status-reports.md)  
  
## <a name="see-also"></a><span data-ttu-id="69222-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="69222-128">See Also</span></span>  
 [<span data-ttu-id="69222-129">源代码管理基础</span><span class="sxs-lookup"><span data-stu-id="69222-129">Source Control Basics</span></span>](../../2014/database-engine/source-control-basics.md)  
  
  
