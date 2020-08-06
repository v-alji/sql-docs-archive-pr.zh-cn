---
title: "\"依赖项\" 页 (报表管理器) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4dcfb311-e9c3-4c5d-b2e0-018d79f37d2e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 488b10d7d7985972274340897ee3975618a12639
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578726"
---
# <a name="dependent-items-page-report-manager"></a><span data-ttu-id="e7be3-102">“依赖项”页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="e7be3-102">Dependent Items Page (Report Manager)</span></span>
  <span data-ttu-id="e7be3-103">使用“依赖项”页可以查看引用共享数据源的报表和模型的列表。</span><span class="sxs-lookup"><span data-stu-id="e7be3-103">Use the Dependent Items page to view a list of reports and models that reference a shared data source.</span></span> <span data-ttu-id="e7be3-104">每个项类型的图标指明该项是报表还是模型。</span><span class="sxs-lookup"><span data-stu-id="e7be3-104">The icon for each item type indicates whether it is a report or a model.</span></span> <span data-ttu-id="e7be3-105">在列表视图或详细信息视图中可以查看此页。</span><span class="sxs-lookup"><span data-stu-id="e7be3-105">This page can be viewed in list view or details view.</span></span> <span data-ttu-id="e7be3-106">使用详细信息视图可以显示每个项的详细信息。</span><span class="sxs-lookup"><span data-stu-id="e7be3-106">Use details view to show more information about each item.</span></span> <span data-ttu-id="e7be3-107">详细信息视图中还有其他页选项。</span><span class="sxs-lookup"><span data-stu-id="e7be3-107">Additional page options are available in details view.</span></span> <span data-ttu-id="e7be3-108">为了帮助您管理共享数据源，此页提供了一些指向使用该数据源的报表和模型的链接、有关报表或模型的上次运行或修改时间的指标，以及“删除”和“移动”按钮，以便您可以方便地删除不再使用的报表和模型，或者将其移至另一个位置以待您确定是否仍然需要它们。</span><span class="sxs-lookup"><span data-stu-id="e7be3-108">To help you manage the shared data source, this page provides links to reports and models that use the data source, metrics on when the report or model was last run or modified, and Delete and Move buttons so that you can easily remove reports and models that are no longer used, or move them to a different location while you determine whether they are still needed.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="e7be3-109">导航</span><span class="sxs-lookup"><span data-stu-id="e7be3-109">Navigation</span></span>  
 <span data-ttu-id="e7be3-110">使用以下过程导航到用户界面 (UI) 中的这一位置。</span><span class="sxs-lookup"><span data-stu-id="e7be3-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-dependent-items-page"></a><span data-ttu-id="e7be3-111">打开“依赖项”页</span><span class="sxs-lookup"><span data-stu-id="e7be3-111">To open the Dependent Items page</span></span>  
  
1.  <span data-ttu-id="e7be3-112">打开报表管理器，找到您要查看其依赖项的共享数据源。</span><span class="sxs-lookup"><span data-stu-id="e7be3-112">Open Report Manager, and locate the shared data source for which you want to view dependent items.</span></span>  
  
2.  <span data-ttu-id="e7be3-113">悬停在该项之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="e7be3-113">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="e7be3-114">在下拉菜单中，单击 **“管理”**。</span><span class="sxs-lookup"><span data-stu-id="e7be3-114">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="e7be3-115">这会打开该数据源的“常规属性”页。</span><span class="sxs-lookup"><span data-stu-id="e7be3-115">This opens the General properties page for the data source.</span></span>  
  
4.  <span data-ttu-id="e7be3-116">选择 **“依赖项”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="e7be3-116">Select the **Dependent Items** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e7be3-117">选项</span><span class="sxs-lookup"><span data-stu-id="e7be3-117">Options</span></span>  
 <span data-ttu-id="e7be3-118">**名称**</span><span class="sxs-lookup"><span data-stu-id="e7be3-118">**Name**</span></span>  
 <span data-ttu-id="e7be3-119">显示报表或模型的名称。</span><span class="sxs-lookup"><span data-stu-id="e7be3-119">Shows the name of the report or model.</span></span> <span data-ttu-id="e7be3-120">单击报表的名称即可打开该报表。</span><span class="sxs-lookup"><span data-stu-id="e7be3-120">Click the name of the report to open it.</span></span> <span data-ttu-id="e7be3-121">单击模型的名称可以打开其属性页。</span><span class="sxs-lookup"><span data-stu-id="e7be3-121">Click the name of the model to open its property pages.</span></span>  
  
 <span data-ttu-id="e7be3-122">**说明**</span><span class="sxs-lookup"><span data-stu-id="e7be3-122">**Description**</span></span>  
 <span data-ttu-id="e7be3-123">显示报表或模型的说明。</span><span class="sxs-lookup"><span data-stu-id="e7be3-123">Shows the description of the report or model.</span></span>  
  
 <span data-ttu-id="e7be3-124">**删除**</span><span class="sxs-lookup"><span data-stu-id="e7be3-124">**Delete**</span></span>  
 <span data-ttu-id="e7be3-125">单击此选项可从报表服务器数据库中删除报表或模型。</span><span class="sxs-lookup"><span data-stu-id="e7be3-125">Click to delete the report or model from the report server database.</span></span> <span data-ttu-id="e7be3-126">单击 **“删除”** 之前，请选中要删除的每个项旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="e7be3-126">Before clicking **Delete**, select the check box next to each item that you want to delete.</span></span>  
  
 <span data-ttu-id="e7be3-127">**移动**</span><span class="sxs-lookup"><span data-stu-id="e7be3-127">**Move**</span></span>  
 <span data-ttu-id="e7be3-128">单击此选项可在文件夹层次结构中重新定位报表或模型。</span><span class="sxs-lookup"><span data-stu-id="e7be3-128">Click to relocate a report or model within the folder hierarchy.</span></span> <span data-ttu-id="e7be3-129">单击 **“移动”** 之前，请选中要移动的每个项旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="e7be3-129">Before clicking **Move**, select the check box next to each item that you want to move.</span></span> <span data-ttu-id="e7be3-130">这将打开“移动项”页，可以在此页上浏览文件夹以选择新的位置。</span><span class="sxs-lookup"><span data-stu-id="e7be3-130">This opens the Move Items page, where you can browse through folders to select a new location.</span></span>  
  
 <span data-ttu-id="e7be3-131">**编辑**</span><span class="sxs-lookup"><span data-stu-id="e7be3-131">**Edit**</span></span>  
 <span data-ttu-id="e7be3-132">单击“属性”图标可以访问报表或模型的属性页。</span><span class="sxs-lookup"><span data-stu-id="e7be3-132">Click the Property icon to access the property pages of a report, or model.</span></span>  
  
 <span data-ttu-id="e7be3-133">**Type**</span><span class="sxs-lookup"><span data-stu-id="e7be3-133">**Type**</span></span>  
 <span data-ttu-id="e7be3-134">显示项类型的图标。</span><span class="sxs-lookup"><span data-stu-id="e7be3-134">Shows the icon of the item type.</span></span>  
  
 <span data-ttu-id="e7be3-135">**修改日期**</span><span class="sxs-lookup"><span data-stu-id="e7be3-135">**Modified Date**</span></span>  
 <span data-ttu-id="e7be3-136">显示报表或模型的上次修改日期和时间。</span><span class="sxs-lookup"><span data-stu-id="e7be3-136">Shows the date and time when the report or model was last modified.</span></span>  
  
 <span data-ttu-id="e7be3-137">**修改者**</span><span class="sxs-lookup"><span data-stu-id="e7be3-137">**Modified By**</span></span>  
 <span data-ttu-id="e7be3-138">显示上次修改项属性的用户名。</span><span class="sxs-lookup"><span data-stu-id="e7be3-138">Shows the name of the user who last modified the item properties.</span></span>  
  
 <span data-ttu-id="e7be3-139">**运行时间**</span><span class="sxs-lookup"><span data-stu-id="e7be3-139">**When Run**</span></span>  
 <span data-ttu-id="e7be3-140">对于以报表执行快照形式运行的报表，此属性用于显示上次刷新报表的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="e7be3-140">For reports that run as report execution snapshots, displays the date and time at which the report was last refreshed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7be3-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7be3-141">See Also</span></span>  
 <span data-ttu-id="e7be3-142">[报表管理器 F1 帮助](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="e7be3-142">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="e7be3-143">[报表管理器（SSRS 本机模式）](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="e7be3-143">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="e7be3-144">["内容" 页 &#40;报表管理器&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="e7be3-144">[Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span></span>  
 [<span data-ttu-id="e7be3-145">报表管理器的 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="e7be3-145">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
