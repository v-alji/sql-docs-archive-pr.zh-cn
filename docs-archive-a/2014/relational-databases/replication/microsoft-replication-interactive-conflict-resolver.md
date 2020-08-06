---
title: Microsoft 复制交互式冲突解决程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replconflictviewer.interactiveresolver.f1
ms.assetid: d3d4a480-782b-4b1d-b839-565c8cf6cb24
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c8cbd2231ab1ab357321f9887bced986e182e608
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693760"
---
# <a name="microsoft-replication-interactive-conflict-resolver"></a><span data-ttu-id="1d761-102">Microsoft Replication Interactive Conflict Resolver</span><span class="sxs-lookup"><span data-stu-id="1d761-102">Microsoft Replication Interactive Conflict Resolver</span></span>
  <span data-ttu-id="1d761-103">Microsoft Replication Interactive Conflict Resolver 可以用于使用 Windows 同步管理器进行同步的合并订阅。</span><span class="sxs-lookup"><span data-stu-id="1d761-103">The Interactive Conflict Resolver can be used for merge subscriptions that are synchronized using Windows Synchronization Manager.</span></span> <span data-ttu-id="1d761-104">使用它可以查看、比较、编辑和选择数据冲突的结果。</span><span class="sxs-lookup"><span data-stu-id="1d761-104">It allows you to view, compare, edit, and select the outcome for data conflicts.</span></span> <span data-ttu-id="1d761-105">复制还包括冲突查看器，使用冲突查看器可以提交冲突结果之后查看和修改冲突结果。</span><span class="sxs-lookup"><span data-stu-id="1d761-105">Replication also includes the Conflict Viewer, which allows you to view and modify conflict outcomes after they have been committed.</span></span> <span data-ttu-id="1d761-106">Microsoft Replication Interactive Conflict Resolver 允许您在同步期间选择结果。</span><span class="sxs-lookup"><span data-stu-id="1d761-106">The Interactive Conflict Resolver allows you to select the outcome during synchronization.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1d761-107">包含逻辑记录的冲突不会显示在交互式冲突解决程序中。</span><span class="sxs-lookup"><span data-stu-id="1d761-107">Conflicts that involve logical records are not displayed in the Interactive Resolver.</span></span> <span data-ttu-id="1d761-108">若要查看有关这些冲突的信息，请使用复制存储过程。</span><span class="sxs-lookup"><span data-stu-id="1d761-108">To view information about these conflicts, use replication stored procedures.</span></span> <span data-ttu-id="1d761-109">有关详细信息，请参阅[查看合并发布的冲突信息（复制 Transact-SQL 编程）](view-conflict-information-for-merge-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="1d761-109">For more information, see [View Conflict Information for Merge Publications &#40;Replication Transact-SQL Programming&#41;](view-conflict-information-for-merge-publications.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="1d761-110">选项</span><span class="sxs-lookup"><span data-stu-id="1d761-110">Options</span></span>  
 <span data-ttu-id="1d761-111">**列名**</span><span class="sxs-lookup"><span data-stu-id="1d761-111">**Column name**</span></span>  
 <span data-ttu-id="1d761-112">表中所有列的名称。</span><span class="sxs-lookup"><span data-stu-id="1d761-112">The name of all columns in the table.</span></span> <span data-ttu-id="1d761-113">一个或多个列可能包含冲突的数据。</span><span class="sxs-lookup"><span data-stu-id="1d761-113">One or more columns might have conflicting data.</span></span> <span data-ttu-id="1d761-114">不管哪些列发生冲突，整个入选行将覆盖整个落选行。</span><span class="sxs-lookup"><span data-stu-id="1d761-114">Regardless of which columns conflict, the entire winning row will overwrite the entire losing row.</span></span>  
  
 <span data-ttu-id="1d761-115">**建议的解决方法**</span><span class="sxs-lookup"><span data-stu-id="1d761-115">**Suggested Resolution**</span></span>  
 <span data-ttu-id="1d761-116">项目的冲突解决程序所提供的建议解决方法。</span><span class="sxs-lookup"><span data-stu-id="1d761-116">The suggested resolution provided by the conflict resolver for the article.</span></span>  
  
 <span data-ttu-id="1d761-117">**发布者**</span><span class="sxs-lookup"><span data-stu-id="1d761-117">**Publisher**</span></span>  
 <span data-ttu-id="1d761-118">发布服务器中的数据值。</span><span class="sxs-lookup"><span data-stu-id="1d761-118">The data value at the Publisher.</span></span>  
  
 <span data-ttu-id="1d761-119">**订阅服务器**</span><span class="sxs-lookup"><span data-stu-id="1d761-119">**Subscriber**</span></span>  
 <span data-ttu-id="1d761-120">订阅服务器中的数据值。</span><span class="sxs-lookup"><span data-stu-id="1d761-120">The data value at the Subscriber.</span></span>  
  
 <span data-ttu-id="1d761-121">**“接受建议”** 、 **“接受发布服务器”** 和 **“接受订阅服务器”**</span><span class="sxs-lookup"><span data-stu-id="1d761-121">**Accept Suggested**, **Accept Publisher**, and **Accept Subscriber**</span></span>  
 <span data-ttu-id="1d761-122">单击此项可以接受将在发布服务器或订阅服务器上应用的行，具体取决于哪个服务器在冲突中落选。</span><span class="sxs-lookup"><span data-stu-id="1d761-122">Click to accept the row that will be applied at either the Publisher or the Subscriber, depending on which one lost the conflict.</span></span> <span data-ttu-id="1d761-123">如果发布服务器在冲突中落选，则其他所有订阅服务器将在下次与发布服务器同步时接收入选行。</span><span class="sxs-lookup"><span data-stu-id="1d761-123">If the Publisher lost the conflict, all other Subscribers will receive the winning row the next time they synchronize with the Publisher.</span></span>  
  
 <span data-ttu-id="1d761-124">**自动解决剩余冲突**</span><span class="sxs-lookup"><span data-stu-id="1d761-124">**Resolve remaining conflicts automatically**</span></span>  
 <span data-ttu-id="1d761-125">使用项目的冲突解决程序所提供的建议解决方法来解决所有剩余的冲突。</span><span class="sxs-lookup"><span data-stu-id="1d761-125">Resolve all remaining conflicts using the suggested resolution provided by the conflict resolver for the article.</span></span>  
  
 <span data-ttu-id="1d761-126">**记录此冲突的详细信息供今后参考**</span><span class="sxs-lookup"><span data-stu-id="1d761-126">**Log the details of the conflict for later reference**</span></span>  
 <span data-ttu-id="1d761-127">在系统表中记录冲突的详细内容。</span><span class="sxs-lookup"><span data-stu-id="1d761-127">Logs the details of the conflict in system tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d761-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1d761-128">See Also</span></span>  
 <span data-ttu-id="1d761-129">[交互式冲突解决方法](merge/advanced-merge-replication-conflict-interactive-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="1d761-129">[Interactive Conflict Resolution](merge/advanced-merge-replication-conflict-interactive-resolution.md) </span></span>  
 <span data-ttu-id="1d761-130">[查看和解决合并发布的数据冲突 (SQL Server Management Studio)](view-and-resolve-data-conflicts-for-merge-publications.md) </span><span class="sxs-lookup"><span data-stu-id="1d761-130">[View and Resolve Data Conflicts for Merge Publications &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md) </span></span>  
 <span data-ttu-id="1d761-131">[使用 Windows 同步管理器同步订阅（Windows 同步管理器）](synchronize-a-subscription-using-windows-synchronization-manager.md) </span><span class="sxs-lookup"><span data-stu-id="1d761-131">[Synchronize a Subscription Using Windows Synchronization Manager &#40;Windows Synchronization Manager&#41;](synchronize-a-subscription-using-windows-synchronization-manager.md) </span></span>  
 [<span data-ttu-id="1d761-132">Advanced Merge Replication Conflict Detection and Resolution</span><span class="sxs-lookup"><span data-stu-id="1d761-132">Advanced Merge Replication Conflict Detection and Resolution</span></span>](merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
