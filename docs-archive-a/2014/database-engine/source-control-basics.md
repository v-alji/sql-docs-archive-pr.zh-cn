---
title: 源代码管理基础知识 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- source controls [SQL Server Management Studio], providers
- source controls [SQL Server Management Studio]
- source controls [SQL Server Management Studio], about source controls
- source controls [SQL Server Management Studio], clients
ms.assetid: ca35b67a-104a-41fb-ac58-a61be06fe114
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 1112dcd8cfdec429b27b22ea3853de859553af0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577811"
---
# <a name="source-control-basics"></a><span data-ttu-id="395ab-102">源代码管理基础</span><span class="sxs-lookup"><span data-stu-id="395ab-102">Source Control Basics</span></span>
  <span data-ttu-id="395ab-103">源代码管理是指以下系统：在该系统中，使用中心服务器软件存储和跟踪文件版本，并控制对文件的访问。</span><span class="sxs-lookup"><span data-stu-id="395ab-103">Source control refers to a system in which a central piece of server software stores and tracks file versions, and also controls access to files.</span></span> <span data-ttu-id="395ab-104">典型的源代码管理系统包括源代码管理提供程序以及两个或多个源代码管理客户端。</span><span class="sxs-lookup"><span data-stu-id="395ab-104">A typical source control system includes a source control provider and two or more source control clients.</span></span>  
  
## <a name="source-control-benefits"></a><span data-ttu-id="395ab-105">源代码管理的优点</span><span class="sxs-lookup"><span data-stu-id="395ab-105">Source Control Benefits</span></span>  
 <span data-ttu-id="395ab-106">如果将文件放置在源代码管理中，可以完成以下工作</span><span class="sxs-lookup"><span data-stu-id="395ab-106">Placing your files under source control makes it possible to</span></span>  
  
-   <span data-ttu-id="395ab-107">管理项的控制权在人员之间传递的过程。</span><span class="sxs-lookup"><span data-stu-id="395ab-107">Manage the process by which the control of items passes from one person to another.</span></span> <span data-ttu-id="395ab-108">源代码管理提供程序支持共享和独占文件访问。</span><span class="sxs-lookup"><span data-stu-id="395ab-108">Source control providers support both shared and exclusive file access.</span></span> <span data-ttu-id="395ab-109">如果对项目文件的访问是独占的，则源代码管理提供程序一次只允许一个用户签出文件并对其进行修改。</span><span class="sxs-lookup"><span data-stu-id="395ab-109">If access to project files is exclusive, the source control provider allows only one user at a time to check files out and modify them.</span></span> <span data-ttu-id="395ab-110">如果访问是共享的，则多个用户可以签出脚本文件。并且，源代码管理提供程序提供了一种机制，可以在各版本签入时对其进行合并。</span><span class="sxs-lookup"><span data-stu-id="395ab-110">If access is shared, more than one user can check out the script file, and the source control provider provides a mechanism for merging the versions as they are checked in.</span></span>  
  
-   <span data-ttu-id="395ab-111">将连续版本的源代码管理项存档。</span><span class="sxs-lookup"><span data-stu-id="395ab-111">Archive successive versions of source-controlled items.</span></span> <span data-ttu-id="395ab-112">源代码管理提供程序可以存储将两个版本的源代码管理项区分开的数据。</span><span class="sxs-lookup"><span data-stu-id="395ab-112">A source control provider stores the data that distinguishes one version of a source-controlled item from another.</span></span> <span data-ttu-id="395ab-113">提供程序将存储版本之间的差异，以及有关版本的重要信息：何时创建、何时修改，以及由谁创建。</span><span class="sxs-lookup"><span data-stu-id="395ab-113">The provider stores the differences between versions, as well as crucial information about the version: when it was created, when it was modified, and by whom.</span></span> <span data-ttu-id="395ab-114">几个人共同处理相同文件时，他们必须使用相同的代码页，以能够准确地比较版本。</span><span class="sxs-lookup"><span data-stu-id="395ab-114">When several people are working on the same file, they must use the same code page, so that versions can be accurately compared.</span></span> <span data-ttu-id="395ab-115">因而，可以检索任何版本的源代码管理项。</span><span class="sxs-lookup"><span data-stu-id="395ab-115">Consequently, you can retrieve any version of a source-controlled item.</span></span> <span data-ttu-id="395ab-116">还可以将任一版本指定为该项的最新版本。</span><span class="sxs-lookup"><span data-stu-id="395ab-116">You can also designate any version to be the latest version of that item.</span></span>  
  
-   <span data-ttu-id="395ab-117">维护有关源代码管理项的历史和版本详细信息。</span><span class="sxs-lookup"><span data-stu-id="395ab-117">Maintain detailed historical and version information on source-controlled items.</span></span> <span data-ttu-id="395ab-118">源代码管理可以存储项的创建日期和时间、签出或签入时间以及执行操作的用户。</span><span class="sxs-lookup"><span data-stu-id="395ab-118">Source control stores the date and time on which the item was created, when it was checked out or checked in, and the user who performed the action.</span></span>  
  
-   <span data-ttu-id="395ab-119">跨项目协作。</span><span class="sxs-lookup"><span data-stu-id="395ab-119">Collaborate across projects.</span></span> <span data-ttu-id="395ab-120">通过文件共享，多个项目可以共享源代码管理项。</span><span class="sxs-lookup"><span data-stu-id="395ab-120">File sharing makes it possible for multiple projects to share source-controlled items.</span></span> <span data-ttu-id="395ab-121">某个共享项的更改将反映到共享该项的所有项目中。</span><span class="sxs-lookup"><span data-stu-id="395ab-121">Changes to a shared item are reflected in all the projects that share the item.</span></span>  
  
-   <span data-ttu-id="395ab-122">自动执行经常重复的源代码管理操作。</span><span class="sxs-lookup"><span data-stu-id="395ab-122">Automate frequently repeated source control operations.</span></span> <span data-ttu-id="395ab-123">源代码管理提供程序可以在命令提示符中定义一个接口，用于支持源代码管理的主要功能。</span><span class="sxs-lookup"><span data-stu-id="395ab-123">A source control provider may define an interface from the command prompt that supports the key features of source control.</span></span> <span data-ttu-id="395ab-124">可以在批处理文件中使用此接口，以实现自动定期执行源代码管理任务。</span><span class="sxs-lookup"><span data-stu-id="395ab-124">You can use this interface in batch files to automate the source control tasks that you perform regularly.</span></span>  
  
-   <span data-ttu-id="395ab-125">从意外删除中恢复。</span><span class="sxs-lookup"><span data-stu-id="395ab-125">Recover from accidental deletions.</span></span> <span data-ttu-id="395ab-126">可以还原签入源代码管理的最新文件版本。</span><span class="sxs-lookup"><span data-stu-id="395ab-126">You can restore the latest file version checked into source control.</span></span>  
  
-   <span data-ttu-id="395ab-127">节省源代码管理客户端和服务器上的磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="395ab-127">Conserve disk space on both the source control client and server.</span></span> <span data-ttu-id="395ab-128">有些源代码管理提供程序（如 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe）可以通过存储文件的最新版本以及各个版本与其前后版本之间的差异来节省服务器上的磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="395ab-128">Some source control providers, such as [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe, support disk space conservation on the server by storing the latest version of a file and the differences between each version and the version that precedes or follows it.</span></span> <span data-ttu-id="395ab-129">在客户端上，Visual SourceSafe 支持节省磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="395ab-129">On the client, Visual SourceSafe supports disk space conservation.</span></span> <span data-ttu-id="395ab-130">可以隐藏文件夹和文件，以便不将其下载到本地磁盘。</span><span class="sxs-lookup"><span data-stu-id="395ab-130">You can cloak folders and files so that they are not downloaded to your local disk.</span></span>  
  
 <span data-ttu-id="395ab-131">实际上，文件签出、签入和其他源代码管理操作都是通过源代码管理客户端（如 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]）完成的。</span><span class="sxs-lookup"><span data-stu-id="395ab-131">File check outs, check ins, and other source control operations are actually accomplished through a source control client, such as [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="395ab-132">客户端能够与提供程序进行交互，以使提供程序的功能可用于一组分散的用户。</span><span class="sxs-lookup"><span data-stu-id="395ab-132">The client is designed to interact with the provider to make the provider's capabilities available to a distributed group of users.</span></span> <span data-ttu-id="395ab-133">通过源代码管理客户端，用户可以浏览提供程序所存储的文件；添加和删除文件；签入和签出文件；以及检索本地文件的副本。</span><span class="sxs-lookup"><span data-stu-id="395ab-133">Using a source control client, users can browse the files stored by the provider; add and delete files; check files in and out; and retrieve copies of local files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="395ab-134">本文档假定您使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe 作为源代码管理提供程序。</span><span class="sxs-lookup"><span data-stu-id="395ab-134">This documentation assumes that you are using [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe as your source control provider.</span></span> <span data-ttu-id="395ab-135">如果使用的是其他源代码管理提供程序，您可能会发现本文档与正在运行的软件之间存在差异。</span><span class="sxs-lookup"><span data-stu-id="395ab-135">If you are using a different source control provider, you might see differences between this documentation and the software you are running.</span></span> <span data-ttu-id="395ab-136">如果发现差异，请查阅源代码管理提供程序的文档。</span><span class="sxs-lookup"><span data-stu-id="395ab-136">If you see differences, consult the documentation for your source control provider.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="395ab-137">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="395ab-137">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="395ab-138">**任务**</span><span class="sxs-lookup"><span data-stu-id="395ab-138">**Task**</span></span>|<span data-ttu-id="395ab-139">**主题**</span><span class="sxs-lookup"><span data-stu-id="395ab-139">**Topic**</span></span>|  
|<span data-ttu-id="395ab-140">设置源代码管理选项</span><span class="sxs-lookup"><span data-stu-id="395ab-140">Set Source Control options</span></span>|[<span data-ttu-id="395ab-141">设置源代码管理选项</span><span class="sxs-lookup"><span data-stu-id="395ab-141">Set Source Control Options</span></span>](../../2014/database-engine/set-source-control-options.md)|  
|<span data-ttu-id="395ab-142">更改源代码管理连接</span><span class="sxs-lookup"><span data-stu-id="395ab-142">Change source control Connections</span></span>|[<span data-ttu-id="395ab-143">更改源代码管理连接</span><span class="sxs-lookup"><span data-stu-id="395ab-143">Change Source Control Connections</span></span>](../../2014/database-engine/change-source-control-connections.md)|  
|<span data-ttu-id="395ab-144">从源代码管理中排除文件</span><span class="sxs-lookup"><span data-stu-id="395ab-144">Exclude files from source control</span></span>|[<span data-ttu-id="395ab-145">从源代码管理中排除文件</span><span class="sxs-lookup"><span data-stu-id="395ab-145">Exclude Files from Source Control</span></span>](../../2014/database-engine/exclude-files-from-source-control.md)|  
  
  
