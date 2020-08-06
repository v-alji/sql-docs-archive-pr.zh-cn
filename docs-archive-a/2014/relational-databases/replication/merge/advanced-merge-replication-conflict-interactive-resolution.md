---
title: 交互式冲突解决方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- interactive conflict resolution [SQL Server replication]
- interactive resolver [SQL Server replication]
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 172c60c7-f605-4eb5-b185-54ae9e9d3c60
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 57d0de17c4d958a1b842748810ba24717e6866e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576707"
---
# <a name="interactive-conflict-resolution"></a><span data-ttu-id="397a1-102">Interactive Conflict Resolution</span><span class="sxs-lookup"><span data-stu-id="397a1-102">Interactive Conflict Resolution</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="397a1-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 复制提供交互式冲突解决程序，可用于 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 同步管理器中在按需同步过程期间手动解决冲突。</span><span class="sxs-lookup"><span data-stu-id="397a1-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication provides an Interactive Resolver, which allows you to resolve conflicts manually during on-demand synchronization in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows Synchronization Manager.</span></span> <span data-ttu-id="397a1-104">该交互式冲突解决程序为图形界面，在运行时激活后，显示每个冲突行的数据，并提供用于查看和编辑冲突数据以及逐个解决冲突的选项。</span><span class="sxs-lookup"><span data-stu-id="397a1-104">Activated at run time, the Interactive Resolver is a graphical interface that displays data for each conflicting row, and provides options for viewing and editing the conflict data, and resolving each conflict individually.</span></span>  
  
 <span data-ttu-id="397a1-105">交互式冲突解决程序与冲突查看器类似。</span><span class="sxs-lookup"><span data-stu-id="397a1-105">The Interactive Resolver resembles the Conflict Viewer.</span></span> <span data-ttu-id="397a1-106">不同的是，冲突查看器显示合并同步后已解决的冲突的结果，而交互式冲突解决程序显示解决前的每个冲突，使用户可以在合并同步过程中确定每个冲突的结果。</span><span class="sxs-lookup"><span data-stu-id="397a1-106">However, the Conflict Viewer displays the results of conflicts that are already resolved after merge synchronization, and the Interactive Resolver displays each conflict prior to resolution, allowing you to determine the outcome of each conflict during merge synchronization.</span></span> <span data-ttu-id="397a1-107">冲突发生时，应该有人监视交互式冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="397a1-107">Someone should be available to monitor the Interactive Resolver when a conflict occurs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="397a1-108">交互式解决方法需要 Windows 同步管理器。</span><span class="sxs-lookup"><span data-stu-id="397a1-108">Interactive Resolution requires Windows Synchronization Manager.</span></span> <span data-ttu-id="397a1-109">如果在 Windows 同步管理器的外部执行同步（作为 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 或复制监视器中的计划同步或按需同步），系统会根据为项目指定的冲突解决程序自动解决冲突，无需用户干预。</span><span class="sxs-lookup"><span data-stu-id="397a1-109">If a synchronization is performed outside of Windows Synchronization Manager (as a scheduled synchronization or an on demand synchronization in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or Replication Monitor), conflicts are resolved automatically without user intervention, according to the resolver specified for the article.</span></span> <span data-ttu-id="397a1-110">包含逻辑记录的冲突不会显示在交互式冲突解决程序中。</span><span class="sxs-lookup"><span data-stu-id="397a1-110">Conflicts that involve logical records are not displayed in the Interactive Resolver.</span></span> <span data-ttu-id="397a1-111">若要查看有关这些冲突的信息，请使用复制存储过程。</span><span class="sxs-lookup"><span data-stu-id="397a1-111">To view information about these conflicts, use replication stored procedures.</span></span> <span data-ttu-id="397a1-112">有关详细信息，请参阅[查看合并发布的冲突信息（复制 Transact-SQL 编程）](../view-conflict-information-for-merge-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="397a1-112">For more information, see [View Conflict Information for Merge Publications &#40;Replication Transact-SQL Programming&#41;](../view-conflict-information-for-merge-publications.md).</span></span>  
  
## <a name="article-resolvers-and-the-interactive-resolver"></a><span data-ttu-id="397a1-113">项目冲突解决程序和交互式冲突解决程序</span><span class="sxs-lookup"><span data-stu-id="397a1-113">Article Resolvers and the Interactive Resolver</span></span>  
 <span data-ttu-id="397a1-114">冲突解决程序（默认冲突解决程序、业务逻辑处理程序或自定义冲突解决程序）将在创建发布时分配给特定项目，并使用一组规则确定输入冲突行数据时应使用哪组数据。</span><span class="sxs-lookup"><span data-stu-id="397a1-114">Conflict resolvers (either the default resolver, a business logic handler, or a custom resolver) are assigned to specific articles when a publication is created, and use a set of rules to determine which set of data should be used when conflicting row data is entered.</span></span> <span data-ttu-id="397a1-115">交互式冲突解决程序不是具有确定冲突入选方与落选方规则的独立冲突解决程序，而是与默认和自定义冲突解决程序一起使用的工具。</span><span class="sxs-lookup"><span data-stu-id="397a1-115">The Interactive Resolver is not a separate conflict resolver with rules for determining conflict winners and losers, but a tool used in conjunction with default and custom resolvers.</span></span> <span data-ttu-id="397a1-116">项目冲突解决程序仍确定入选行和落选行，而交互式冲突解决程序则允许用户干预接受、拒绝或修改结果。</span><span class="sxs-lookup"><span data-stu-id="397a1-116">The article resolver still determines the winning and losing row, but the Interactive Resolver allows user intervention to accept, reject, or modify the results.</span></span>  
  
 <span data-ttu-id="397a1-117">若要使用交互式冲突解决程序，必须为每个要求使用该程序的项目和订阅启用交互式解决方法。</span><span class="sxs-lookup"><span data-stu-id="397a1-117">To use the Interactive Resolver, interactive resolution must be enabled for each article and subscription that requires it.</span></span> <span data-ttu-id="397a1-118">为一个或多个项目和订阅启用交互式解决方法后，在合并同步过程中检测到冲突时，将使用交互式冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="397a1-118">After it is enabled for one or more articles and subscriptions, the Interactive Resolver is used when a conflict is detected during merge synchronization.</span></span>  
  
 <span data-ttu-id="397a1-119">若要使用交互式冲突解决程序，请参阅[指定合并项目的交互式冲突解决方法](..//publish/specify-merge-replication-properties.md#interactive-conflict-resolution)和[使用 Windows 同步管理器同步订阅（Windows 同步管理器）](../synchronize-a-subscription-using-windows-synchronization-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="397a1-119">To use the Interactive Resolver, see [Specify Interactive Conflict Resolution for Merge Articles](..//publish/specify-merge-replication-properties.md#interactive-conflict-resolution) and [Synchronize a Subscription Using Windows Synchronization Manager &#40;Windows Synchronization Manager&#41;](../synchronize-a-subscription-using-windows-synchronization-manager.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="397a1-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="397a1-120">See Also</span></span>  
 [<span data-ttu-id="397a1-121">Advanced Merge Replication Conflict Detection and Resolution</span><span class="sxs-lookup"><span data-stu-id="397a1-121">Advanced Merge Replication Conflict Detection and Resolution</span></span>](advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
