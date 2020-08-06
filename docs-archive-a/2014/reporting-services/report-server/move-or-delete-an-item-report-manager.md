---
title: 移动或删除项（报表管理器）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- moving items
- items [Reporting Services], moving
ms.assetid: 980a66c7-a18b-4af7-8954-45726fa517d6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3a61ad56ea9e20e7fdf38d5acf05529b685ee896
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682672"
---
# <a name="move-or-delete-an-item-report-manager"></a><span data-ttu-id="daa4a-102">移动或删除项（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="daa4a-102">Move or Delete an Item (Report Manager)</span></span>
  <span data-ttu-id="daa4a-103">发布到报表服务器的报表和与报表相关的项将存储在文件夹中。</span><span class="sxs-lookup"><span data-stu-id="daa4a-103">Reports and report-related items that you publish to a report server are stored in folders.</span></span> <span data-ttu-id="daa4a-104">您可以将这些项移动到不同文件夹，并且报表服务器自动维护对这些项的引用。</span><span class="sxs-lookup"><span data-stu-id="daa4a-104">You can move items to a different folder and references to those items are maintained automatically by the report server.</span></span> <span data-ttu-id="daa4a-105">在删除项之前，请注意是否有其他项依赖它。</span><span class="sxs-lookup"><span data-stu-id="daa4a-105">Before you delete an item, consider whether other items depend on it.</span></span>  
  
## <a name="move-an-item"></a><span data-ttu-id="daa4a-106">移动项</span><span class="sxs-lookup"><span data-stu-id="daa4a-106">Move an Item</span></span>  
 <span data-ttu-id="daa4a-107">您可以将报表服务器项移动到报表服务器文件夹层次结构中的不同位置。</span><span class="sxs-lookup"><span data-stu-id="daa4a-107">You can move report server items to different folder locations in the report server folder hierarchy.</span></span> <span data-ttu-id="daa4a-108">移动项时，所有属性（包括安全设置）也随之移至新的位置。</span><span class="sxs-lookup"><span data-stu-id="daa4a-108">When you move an item, all properties (including security settings) move with the item to the new location.</span></span> <span data-ttu-id="daa4a-109">移动文件夹时，文件夹中的所有项也随之移动。</span><span class="sxs-lookup"><span data-stu-id="daa4a-109">When you move a folder, all the items in the folder move with it.</span></span>  
  
 <span data-ttu-id="daa4a-110">在报表管理器中，可以移动的项会在文件夹层次结构中指明。</span><span class="sxs-lookup"><span data-stu-id="daa4a-110">In Report Manager, the items that you can move are indicated in the folder hierarchy.</span></span> <span data-ttu-id="daa4a-111">下表列出了每种可移动项的图标。</span><span class="sxs-lookup"><span data-stu-id="daa4a-111">The following table shows the icon for each movable item.</span></span>  
  
|<span data-ttu-id="daa4a-112">图标</span><span class="sxs-lookup"><span data-stu-id="daa4a-112">Icon</span></span>|<span data-ttu-id="daa4a-113">可移动项</span><span class="sxs-lookup"><span data-stu-id="daa4a-113">Moveable item</span></span>|  
|----------|-------------------|  
|<span data-ttu-id="daa4a-114">![Report icon](../media/hlp-16doc.gif "报表图标")</span><span class="sxs-lookup"><span data-stu-id="daa4a-114">![Report icon](../media/hlp-16doc.gif "Report icon")</span></span>|<span data-ttu-id="daa4a-115">报表</span><span class="sxs-lookup"><span data-stu-id="daa4a-115">Report</span></span>|  
|<span data-ttu-id="daa4a-116">![链接报表图标](../media/hlp-16linked.gif "链接报表图标")</span><span class="sxs-lookup"><span data-stu-id="daa4a-116">![Linked report icon](../media/hlp-16linked.gif "Linked report icon")</span></span>|<span data-ttu-id="daa4a-117">链接报表</span><span class="sxs-lookup"><span data-stu-id="daa4a-117">Linked report</span></span>|  
|<span data-ttu-id="daa4a-118">![文件夹图标](../media/hlp-16folder.gif "文件夹图标")</span><span class="sxs-lookup"><span data-stu-id="daa4a-118">![Folder icon](../media/hlp-16folder.gif "Folder icon")</span></span>|<span data-ttu-id="daa4a-119">Folder</span><span class="sxs-lookup"><span data-stu-id="daa4a-119">Folder</span></span>|  
|<span data-ttu-id="daa4a-120">![通用资源图标](../media/hlp-16file.gif "通用资源图标")</span><span class="sxs-lookup"><span data-stu-id="daa4a-120">![generic resource icon](../media/hlp-16file.gif "generic resource icon")</span></span>|<span data-ttu-id="daa4a-121">一般资源</span><span class="sxs-lookup"><span data-stu-id="daa4a-121">Generic resource</span></span>|  
|<span data-ttu-id="daa4a-122">![Shared data source icon](../media/hlp-16datasource.png "共享数据源图标")</span><span class="sxs-lookup"><span data-stu-id="daa4a-122">![Shared data source icon](../media/hlp-16datasource.png "Shared data source icon")</span></span>|<span data-ttu-id="daa4a-123">共享数据源</span><span class="sxs-lookup"><span data-stu-id="daa4a-123">Shared data source</span></span>|  
||<span data-ttu-id="daa4a-124">共享数据集</span><span class="sxs-lookup"><span data-stu-id="daa4a-124">Shared dataset</span></span>|  
  
 <span data-ttu-id="daa4a-125">并非所有使用的项都可以移动。</span><span class="sxs-lookup"><span data-stu-id="daa4a-125">Not all items that you work with can be moved.</span></span> <span data-ttu-id="daa4a-126">不能移动与报表相关联的项，例如订阅或报表历史记录。</span><span class="sxs-lookup"><span data-stu-id="daa4a-126">You cannot move items that are associated with a report, such as subscriptions or report history.</span></span> <span data-ttu-id="daa4a-127">这些项随其关联报表一起移动。</span><span class="sxs-lookup"><span data-stu-id="daa4a-127">Those items move with their associated reports.</span></span> <span data-ttu-id="daa4a-128">同样，也不能移动文件夹层次结构之外的项（如共享计划）。</span><span class="sxs-lookup"><span data-stu-id="daa4a-128">Similarly, you cannot move items, such as shared schedules, that exist outside of the folder hierarchy.</span></span> <span data-ttu-id="daa4a-129">不具备相应权限时不能移动项。</span><span class="sxs-lookup"><span data-stu-id="daa4a-129">You cannot move items if you lack permission to do so.</span></span> <span data-ttu-id="daa4a-130">如果您对相关项的角色分配选择了以下任务，则说明已被授予移动相应项的权限：“管理报表”、“管理模型”、“管理文件夹”和“管理数据源”。</span><span class="sxs-lookup"><span data-stu-id="daa4a-130">Permission to move an item is conveyed when the following tasks are selected in your role assignment for the item in question: "Manage reports," "Manage models", "Manage folders," and "Manage data sources."</span></span>  
  
#### <a name="to-move-an-item-from-within-the-contents-page"></a><span data-ttu-id="daa4a-131">从“内容”页中移动项</span><span class="sxs-lookup"><span data-stu-id="daa4a-131">To move an item from within the Contents page</span></span>  
  
1.  <span data-ttu-id="daa4a-132">启动 [报表管理器 &#40;SSRS 本机模式下&#41;].。report-manager-ssrs-native-mode.md) 。</span><span class="sxs-lookup"><span data-stu-id="daa4a-132">Start [Report Manager  &#40;SSRS Native Mode&#41;]../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="daa4a-133">在报表管理器中，导航到 **“内容”** 页，然后找到要移动的项。</span><span class="sxs-lookup"><span data-stu-id="daa4a-133">In Report Manager, navigate to the **Contents** page, and locate the item that you want to move.</span></span>  
  
3.  <span data-ttu-id="daa4a-134">悬停在该项之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="daa4a-134">Hover over the item, and click the drop-down arrow.</span></span>  
  
4.  <span data-ttu-id="daa4a-135">在下拉菜单中，单击 **“移动”** 。</span><span class="sxs-lookup"><span data-stu-id="daa4a-135">In the drop-down menu, click **Move**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="daa4a-136">在 **“位置”** 中，指定要将该项移动到的文件夹。</span><span class="sxs-lookup"><span data-stu-id="daa4a-136">For **Location**, specify the folder you want to move the item to.</span></span> <span data-ttu-id="daa4a-137">可以键入完全限定文件夹名称，或使用树控件导航到相应的文件夹。</span><span class="sxs-lookup"><span data-stu-id="daa4a-137">You can type the fully qualified folder name or use the tree control to navigate to the folder.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="daa4a-138">或者，您也可以导航到要移动的对象，单击 **“属性”** ，再单击该页顶部的 **“移动”** 。</span><span class="sxs-lookup"><span data-stu-id="daa4a-138">Alternatively, you can navigate to the object you want to move, click **Properties**, and then click **Move** at the top of the page.</span></span>  
  
## <a name="delete-an-item"></a><span data-ttu-id="daa4a-139">删除项</span><span class="sxs-lookup"><span data-stu-id="daa4a-139">Delete an item</span></span>  
 <span data-ttu-id="daa4a-140">在删除项之前，确定是否有其他项使用该项。</span><span class="sxs-lookup"><span data-stu-id="daa4a-140">Before you delete an item, determine if it is used by other items.</span></span> <span data-ttu-id="daa4a-141">例如，如果您删除了一个共享数据源，则使用该数据源的报表和模型将无法再运行。</span><span class="sxs-lookup"><span data-stu-id="daa4a-141">For example, if you delete a shared data source, reports and models that use that data source will no longer run.</span></span> <span data-ttu-id="daa4a-142">删除报表时，也将删除与该报表关联的订阅和报表历史记录。</span><span class="sxs-lookup"><span data-stu-id="daa4a-142">If you delete a report, subscriptions and report history associated with that report are also deleted.</span></span> <span data-ttu-id="daa4a-143">若要查找项的依赖项，请参阅 [依赖项页 &#40;报表管理器&#41;]。dependent-items-page-report-manager.md) 。</span><span class="sxs-lookup"><span data-stu-id="daa4a-143">To find dependent items for an item, see [Dependent Items Page &#40;Report Manager&#41;]../dependent-items-page-report-manager.md).</span></span>  
  
#### <a name="to-delete-a-report-or-item"></a><span data-ttu-id="daa4a-144">删除报表或项</span><span class="sxs-lookup"><span data-stu-id="daa4a-144">To delete a report or item</span></span>  
  
1.  <span data-ttu-id="daa4a-145">启动 [报表管理器 &#40;SSRS 本机模式下&#41;].。report-manager-ssrs-native-mode.md) 。</span><span class="sxs-lookup"><span data-stu-id="daa4a-145">Start [Report Manager  &#40;SSRS Native Mode&#41;]../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="daa4a-146">在报表管理器中，导航到 **“内容”** 页，然后找到要删除的项。</span><span class="sxs-lookup"><span data-stu-id="daa4a-146">In Report Manager, navigate to the **Contents** page, and locate the item that you want to delete.</span></span>  
  
3.  <span data-ttu-id="daa4a-147">悬停在该项之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="daa4a-147">Hover over the item, and click the drop-down arrow.</span></span>  
  
4.  <span data-ttu-id="daa4a-148">在下拉菜单中，单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="daa4a-148">In the drop-down menu, click **Delete**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="daa4a-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="daa4a-149">See Also</span></span>  
 <span data-ttu-id="daa4a-150">[内容页 &#40;报表管理器&#41;] .。。/contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="daa4a-150">[Contents Page &#40;Report Manager&#41;]../contents-page-report-manager.md)</span></span>   
 [<span data-ttu-id="daa4a-151">查找、查看和管理报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="daa4a-151">Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;</span></span>](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
