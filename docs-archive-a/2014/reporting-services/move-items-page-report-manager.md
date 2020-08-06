---
title: ) 移动项页 (报表管理器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fc83b8d2-bc79-4b56-8970-34a1cbbcc176
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 98ff306caf634a5f0478e2eba03c2313b24be274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692788"
---
# <a name="move-items-page-report-manager"></a><span data-ttu-id="935a3-102">“移动项”页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="935a3-102">Move Items Page (Report Manager)</span></span>
  <span data-ttu-id="935a3-103">使用“移动项”页可以将报表、文件夹或其他项移至报表服务器上的新位置。</span><span class="sxs-lookup"><span data-stu-id="935a3-103">Use the Move Items page to move a report, folder, or other item to a new location on the report server.</span></span> <span data-ttu-id="935a3-104">您可以键入新位置的路径，也可以使用树视图找到报表服务器命名空间中的新位置。</span><span class="sxs-lookup"><span data-stu-id="935a3-104">You can type the path of the new location or use a tree view to browse to a new location in the report server namespace.</span></span> <span data-ttu-id="935a3-105">只能移动您有权移动并且存储在当前报表服务器中的项。</span><span class="sxs-lookup"><span data-stu-id="935a3-105">You can only move items that you have permission to move and that are stored on the current report server.</span></span>  
  
 <span data-ttu-id="935a3-106">移动其他项所引用的项（例如，由许多报表引用的共享数据源或模型）时，该项的路径信息将自动更新。</span><span class="sxs-lookup"><span data-stu-id="935a3-106">When you move an item that is referenced by another item (for example, a shared data source or model that is referenced by many reports), the path information for that item is updated automatically.</span></span> <span data-ttu-id="935a3-107">移动共享数据源不会中断与使用它的报表和模型的数据源连接。</span><span class="sxs-lookup"><span data-stu-id="935a3-107">Moving a shared data source does not disrupt a data source connection to the reports and models that use it.</span></span> <span data-ttu-id="935a3-108">如果将共享数据源或模型移至用户无权访问的文件夹，则用户仍能够运行任何引用该数据源或模型的报表，但是用户在文件层次结构中看不到该项。</span><span class="sxs-lookup"><span data-stu-id="935a3-108">If you move a shared data source or model to a folder for which users do not have permission, they will still be able to run any report that references the data source or model, however the item will not be visible to them in the folder hierarchy.</span></span>  
  
 <span data-ttu-id="935a3-109">对于 **“位置”**，请指定文件夹的完整路径（以根文件夹名称开头）。</span><span class="sxs-lookup"><span data-stu-id="935a3-109">For **Location**, specify the full path to folder, beginning with the root folder name.</span></span> <span data-ttu-id="935a3-110">您可以键入路径名或使用树视图定位至所需的文件夹。</span><span class="sxs-lookup"><span data-stu-id="935a3-110">You can type the path name or use the tree view to navigate to the folder you want.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="935a3-111">并非所有的项都可以移动。</span><span class="sxs-lookup"><span data-stu-id="935a3-111">Not all items are movable.</span></span> <span data-ttu-id="935a3-112">您不能移动保留文件夹，例如主文件夹、我的报表或用户文件夹。</span><span class="sxs-lookup"><span data-stu-id="935a3-112">You cannot move reserved folders such as Home, My Reports, or Users Folders.</span></span> <span data-ttu-id="935a3-113">也不能将报表历史记录或快照移至其他位置。</span><span class="sxs-lookup"><span data-stu-id="935a3-113">You cannot move report history or snapshots to different locations.</span></span> <span data-ttu-id="935a3-114">历史记录和快照应始终与它们所基于的报表位于相同的位置中，并且可以通过该报表进行访问。</span><span class="sxs-lookup"><span data-stu-id="935a3-114">History and snapshots are always located with, and accessed through, the report on which they are based.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="935a3-115">导航</span><span class="sxs-lookup"><span data-stu-id="935a3-115">Navigation</span></span>  
 <span data-ttu-id="935a3-116">使用以下过程导航到用户界面 (UI) 中的这一位置。</span><span class="sxs-lookup"><span data-stu-id="935a3-116">Use the following procedures to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-move-items-page-from-the-contents-page-in-details-view"></a><span data-ttu-id="935a3-117">从“详细信息视图”中的“内容”页打开“移动项”页</span><span class="sxs-lookup"><span data-stu-id="935a3-117">To open the Move Items page from the Contents page in Details View</span></span>  
  
1.  <span data-ttu-id="935a3-118">打开报表管理器，导航到包含要移动的项的文件夹。</span><span class="sxs-lookup"><span data-stu-id="935a3-118">Open Report Manager, and navigate to the folder that contains an item you want to move.</span></span> <span data-ttu-id="935a3-119">您还可以移动报表管理器主页中的项。</span><span class="sxs-lookup"><span data-stu-id="935a3-119">You can also move items from the Report Manager Home page.</span></span>  
  
2.  <span data-ttu-id="935a3-120">在工具栏中，单击 **“详细信息视图”**。</span><span class="sxs-lookup"><span data-stu-id="935a3-120">In the toolbar, click **Details View**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="935a3-121">如果您只看到 **“平铺视图”**，则您已在 **“详细信息视图”** 中。</span><span class="sxs-lookup"><span data-stu-id="935a3-121">If you see only **Tiles View**, you are already in **Details View**.</span></span>  
  
3.  <span data-ttu-id="935a3-122">选择项旁边的框，然后单击工具栏中的 **“移动”** 。</span><span class="sxs-lookup"><span data-stu-id="935a3-122">Select the box next to an item, and then click **Move** in the toolbar.</span></span> <span data-ttu-id="935a3-123">如果您要将多个项移到同一个新位置，则可以选择多个框。</span><span class="sxs-lookup"><span data-stu-id="935a3-123">You can select more than one box if you want to move multiple items to the same new location.</span></span>  
  
###### <a name="to-open-the-move-items-page-from-the-contents-page-in-tiles-view"></a><span data-ttu-id="935a3-124">从“平铺视图”中的“内容”页打开“移动项”页</span><span class="sxs-lookup"><span data-stu-id="935a3-124">To open the Move Items page from the Contents page in Tiles View</span></span>  
  
1.  <span data-ttu-id="935a3-125">打开报表管理器，导航到包含要移动的项的文件夹。</span><span class="sxs-lookup"><span data-stu-id="935a3-125">Open Report Manager, and navigate to the folder that contains an item you want to move.</span></span> <span data-ttu-id="935a3-126">您还可以移动报表管理器主页中的项。</span><span class="sxs-lookup"><span data-stu-id="935a3-126">You can also move items from the Report Manager Home page.</span></span>  
  
2.  <span data-ttu-id="935a3-127">在工具栏中，单击 **“平铺视图”**。</span><span class="sxs-lookup"><span data-stu-id="935a3-127">In the toolbar, click **Tiles View**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="935a3-128">如果您只看到 **“详细信息视图”**，则您已在 **“平铺视图”** 中。</span><span class="sxs-lookup"><span data-stu-id="935a3-128">If you see only **Details View**, you are already in **Tiles View**.</span></span>  
  
3.  <span data-ttu-id="935a3-129">悬停在该项之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="935a3-129">Hover over an item, and click the drop-down arrow.</span></span>  
  
4.  <span data-ttu-id="935a3-130">在下拉菜单中，单击 **“移动”**。</span><span class="sxs-lookup"><span data-stu-id="935a3-130">In the drop-down menu, click **Move**.</span></span>  
  
###### <a name="to-open-the-move-items-page-from-the-general-properties-page-of-an-item"></a><span data-ttu-id="935a3-131">从项的“常规属性”页打开“移动项”页</span><span class="sxs-lookup"><span data-stu-id="935a3-131">To open the Move Items page from the General Properties page of an item</span></span>  
  
1.  <span data-ttu-id="935a3-132">打开报表管理器，导航到包含要移动的项的文件夹。</span><span class="sxs-lookup"><span data-stu-id="935a3-132">Open Report Manager, and navigate to the folder that contains an item you want to move.</span></span> <span data-ttu-id="935a3-133">您还可以移动报表管理器主页中的项。</span><span class="sxs-lookup"><span data-stu-id="935a3-133">You can also move items from the Report Manager Home page.</span></span>  
  
2.  <span data-ttu-id="935a3-134">悬停在该项之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="935a3-134">Hover over an item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="935a3-135">在下拉菜单中，单击 **“管理”**。</span><span class="sxs-lookup"><span data-stu-id="935a3-135">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="935a3-136">这会打开项的“常规属性”页。</span><span class="sxs-lookup"><span data-stu-id="935a3-136">This opens the General properties page for an item.</span></span>  
  
4.  <span data-ttu-id="935a3-137">在项工具栏中，单击 **“移动”**。</span><span class="sxs-lookup"><span data-stu-id="935a3-137">In the item toolbar, click **Move**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="935a3-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="935a3-138">See Also</span></span>  
 <span data-ttu-id="935a3-139">[报表管理器（SSRS 本机模式）](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="935a3-139">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="935a3-140">["常规属性" 页，文件夹 &#40;报表管理器&#41;](../../2014/reporting-services/general-properties-page-folders-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="935a3-140">[General Properties Page, Folders &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-folders-report-manager.md) </span></span>  
 <span data-ttu-id="935a3-141">[报表 &#40;报表管理器的 "常规属性" 页&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="935a3-141">[General Properties Page, Reports &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span></span>  
 <span data-ttu-id="935a3-142">["常规属性" 页，报表管理器的资源 &#40;&#41;](../../2014/reporting-services/general-properties-page-resources-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="935a3-142">[General Properties Page, Resources &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-resources-report-manager.md) </span></span>  
 <span data-ttu-id="935a3-143">["常规属性" 页，"共享数据源" &#40;报表管理器&#41;](../../2014/reporting-services/general-properties-page-shared-data-sources-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="935a3-143">[General Properties Page, Shared Data Sources &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-shared-data-sources-report-manager.md) </span></span>  
 [<span data-ttu-id="935a3-144">报表管理器的 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="935a3-144">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
