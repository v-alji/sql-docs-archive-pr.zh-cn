---
title: 启用、禁用和删除断点
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 357b5874-273f-43a9-8e30-83872bdea5dc
author: rothja
ms.author: jroth
ms.openlocfilehash: 17e83c6488b9d9026fb78e5fb8f50e22533fa61e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590723"
---
# <a name="enable-disable-and-delete-breakpoints"></a><span data-ttu-id="9dc1b-102">启用、禁用和删除断点</span><span class="sxs-lookup"><span data-stu-id="9dc1b-102">Enable, Disable, and Delete Breakpoints</span></span>
  <span data-ttu-id="9dc1b-103">若要查看和管理所有打开的断点，可以使用 **“断点”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="9dc1b-103">To view and manage all the open breakpoints, you can use the **Breakpoints** window.</span></span> <span data-ttu-id="9dc1b-104">使用此窗口可以查看断点信息，并且执行一些诸如删除、禁用或启用断点之类的操作。</span><span class="sxs-lookup"><span data-stu-id="9dc1b-104">Use the window to view breakpoint information and to take actions such as deleting, disabling, or enabling breakpoints.</span></span>  
  
## <a name="the-breakpoints-window"></a><span data-ttu-id="9dc1b-105">“断点”窗口</span><span class="sxs-lookup"><span data-stu-id="9dc1b-105">The Breakpoints Window</span></span>  
 <span data-ttu-id="9dc1b-106">**“断点”** 窗口列出了一些信息，例如断点处于哪个代码行。</span><span class="sxs-lookup"><span data-stu-id="9dc1b-106">The **Breakpoints** window lists information such as which line of code the breakpoint is located on.</span></span> <span data-ttu-id="9dc1b-107">在 **“断点”** 窗口中，还可以删除、禁用和启用断点。</span><span class="sxs-lookup"><span data-stu-id="9dc1b-107">In the **Breakpoints** window, you can also delete, disable, and enable breakpoints.</span></span> <span data-ttu-id="9dc1b-108">有关 **“断点”** 窗口的详细信息，请参阅 [“断点” Window](transact-sql-debugger-breakpoints-window.md)。</span><span class="sxs-lookup"><span data-stu-id="9dc1b-108">For more information about the **Breakpoints** window, see [Breakpoints Window](transact-sql-debugger-breakpoints-window.md)</span></span>  
  
 <span data-ttu-id="9dc1b-109">禁用断点可以暂停断点执行，但会保留其定义，以便以后启用该断点。</span><span class="sxs-lookup"><span data-stu-id="9dc1b-109">Disabling a breakpoint prevents it from pausing execution, but leaves the definition in place in case you want to enable the breakpoint later.</span></span> <span data-ttu-id="9dc1b-110">删除断点将会永久删除此断点。</span><span class="sxs-lookup"><span data-stu-id="9dc1b-110">Deleting a breakpoint removes it permanently.</span></span> <span data-ttu-id="9dc1b-111">您必须切换一个新断点，以对该语句暂停执行。</span><span class="sxs-lookup"><span data-stu-id="9dc1b-111">You must toggle a new breakpoint to pause execution on the statement.</span></span>  
  
## <a name="to-open-the-breakpoints-window"></a><span data-ttu-id="9dc1b-112">打开“断点”窗口</span><span class="sxs-lookup"><span data-stu-id="9dc1b-112">To Open the Breakpoints Window</span></span>  
 <span data-ttu-id="9dc1b-113">**To open the Breakpoints window**</span><span class="sxs-lookup"><span data-stu-id="9dc1b-113">**To open the Breakpoints window**</span></span>  
  
 <span data-ttu-id="9dc1b-114">可以使用以下方式之一打开 **“断点”** 窗口：</span><span class="sxs-lookup"><span data-stu-id="9dc1b-114">You can open the **Breakpoints** window in one of the following ways:</span></span>  
  
-   <span data-ttu-id="9dc1b-115">在 **“调试”** 菜单上单击 **“窗口”** ，然后单击 **“断点”** 。</span><span class="sxs-lookup"><span data-stu-id="9dc1b-115">On the **Debug** menu, click **Windows**, and then click **Breakpoints**.</span></span>  
  
-   <span data-ttu-id="9dc1b-116">在 **“调试”** 工具栏上，单击 **“断点”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="9dc1b-116">On the **Debug** toolbar, click the **Breakpoints** button.</span></span>  
  
-   <span data-ttu-id="9dc1b-117">按 Ctrl+Alt+B。</span><span class="sxs-lookup"><span data-stu-id="9dc1b-117">Press CTRL+ALT+B.</span></span>  
  
## <a name="to-disable-a-single-breakpoint"></a><span data-ttu-id="9dc1b-118">禁用单个断点</span><span class="sxs-lookup"><span data-stu-id="9dc1b-118">To Disable a Single Breakpoint</span></span>  
 <span data-ttu-id="9dc1b-119">**To disable a single breakpoint**</span><span class="sxs-lookup"><span data-stu-id="9dc1b-119">**To disable a single breakpoint**</span></span>  
  
 <span data-ttu-id="9dc1b-120">可以使用以下方式之一禁用单个断点：</span><span class="sxs-lookup"><span data-stu-id="9dc1b-120">You can disable a single breakpoint in one of the following ways:</span></span>  
  
-   <span data-ttu-id="9dc1b-121">在查询编辑器窗口中，右键单击所需断点，然后单击“禁用断点”  。</span><span class="sxs-lookup"><span data-stu-id="9dc1b-121">In the Query Editor window, right-click the breakpoint, and then click **Disable Breakpoint**.</span></span>  
  
-   <span data-ttu-id="9dc1b-122">在“断点”窗口中，清除断点左侧的复选框。</span><span class="sxs-lookup"><span data-stu-id="9dc1b-122">In the Breakpoints window, clear the check box to the left of the breakpoint.</span></span>  
  
## <a name="to-disable-all-breakpoints"></a><span data-ttu-id="9dc1b-123">禁用所有断点</span><span class="sxs-lookup"><span data-stu-id="9dc1b-123">To Disable All Breakpoints</span></span>  
 <span data-ttu-id="9dc1b-124">**To disable all breakpoints**</span><span class="sxs-lookup"><span data-stu-id="9dc1b-124">**To disable all breakpoints**</span></span>  
  
 <span data-ttu-id="9dc1b-125">可以使用以下方式之一禁用所有断点：</span><span class="sxs-lookup"><span data-stu-id="9dc1b-125">You can disable all breakpoints in one of the following ways:</span></span>  
  
-   <span data-ttu-id="9dc1b-126">在 **“调试”** 菜单上单击 **“禁用所有断点”** 。</span><span class="sxs-lookup"><span data-stu-id="9dc1b-126">On the **Debug** menu, click **Disable All Breakpoints**.</span></span>  
  
-   <span data-ttu-id="9dc1b-127">在 **“断点”** 窗口的工具栏上，单击 **“禁用所有断点”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="9dc1b-127">On the toolbar of the **Breakpoints** window, click the **Disable All Breakpoints** button.</span></span>  
  
## <a name="to-enable-a-single-breakpoint"></a><span data-ttu-id="9dc1b-128">启用单个断点</span><span class="sxs-lookup"><span data-stu-id="9dc1b-128">To Enable a Single Breakpoint</span></span>  
 <span data-ttu-id="9dc1b-129">**To enable a single breakpoint**</span><span class="sxs-lookup"><span data-stu-id="9dc1b-129">**To enable a single breakpoint**</span></span>  
  
 <span data-ttu-id="9dc1b-130">可以使用以下方式之一启用单个断点：</span><span class="sxs-lookup"><span data-stu-id="9dc1b-130">You can enable a single breakpoint in one of the following ways:</span></span>  
  
-   <span data-ttu-id="9dc1b-131">在查询编辑器窗口中，右键单击所需断点，然后单击“启用断点”  。</span><span class="sxs-lookup"><span data-stu-id="9dc1b-131">In the Query Editor window, right-click the breakpoint, and then click **Enable Breakpoint**.</span></span>  
  
-   <span data-ttu-id="9dc1b-132">在“断点”窗口中，单击断点左侧的框。</span><span class="sxs-lookup"><span data-stu-id="9dc1b-132">In the Breakpoints window, click the box to the left of the breakpoint.</span></span>  
  
## <a name="to-enable-all-breakpoints"></a><span data-ttu-id="9dc1b-133">启用所有断点</span><span class="sxs-lookup"><span data-stu-id="9dc1b-133">To Enable All Breakpoints</span></span>  
 <span data-ttu-id="9dc1b-134">**To enable all breakpoints**</span><span class="sxs-lookup"><span data-stu-id="9dc1b-134">**To enable all breakpoints**</span></span>  
  
 <span data-ttu-id="9dc1b-135">可以使用以下方式之一启用所有断点：</span><span class="sxs-lookup"><span data-stu-id="9dc1b-135">You can enable all breakpoints in one of the following ways:</span></span>  
  
-   <span data-ttu-id="9dc1b-136">在 **“调试”** 菜单上单击 **“启用所有断点”** 。</span><span class="sxs-lookup"><span data-stu-id="9dc1b-136">On the **Debug** menu, click **Enable All Breakpoints**.</span></span>  
  
-   <span data-ttu-id="9dc1b-137">在 **“断点”** 窗口的工具栏上，单击 **“启用所有断点”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="9dc1b-137">On the toolbar of the **Breakpoints** window, click the **Enable All Breakpoints** button.</span></span>  
  
## <a name="to-delete-a-single-breakpoint"></a><span data-ttu-id="9dc1b-138">删除单个断点</span><span class="sxs-lookup"><span data-stu-id="9dc1b-138">To Delete a Single Breakpoint</span></span>  
 <span data-ttu-id="9dc1b-139">**To delete a single breakpoint**</span><span class="sxs-lookup"><span data-stu-id="9dc1b-139">**To delete a single breakpoint**</span></span>  
  
 <span data-ttu-id="9dc1b-140">可以使用以下方式之一删除单个断点：</span><span class="sxs-lookup"><span data-stu-id="9dc1b-140">You can delete a single breakpoint in one of the following ways:</span></span>  
  
-   <span data-ttu-id="9dc1b-141">在查询编辑器窗口中，右键单击所需断点，然后单击“删除断点”  。</span><span class="sxs-lookup"><span data-stu-id="9dc1b-141">In the Query Editor window, right-click the breakpoint, and then click **Delete Breakpoint**.</span></span>  
  
-   <span data-ttu-id="9dc1b-142">在断点窗口中，右键单击所需断点，然后在快捷菜单上单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="9dc1b-142">In the Breakpoints window, right-click the breakpoint, and then click **Delete** on the shortcut menu.</span></span>  
  
-   <span data-ttu-id="9dc1b-143">在“断点”窗口中，选择所需断点，然后按 Delete。</span><span class="sxs-lookup"><span data-stu-id="9dc1b-143">In the Breakpoints window, select the breakpoint, and then press DELETE.</span></span>  
  
## <a name="to-delete-all-breakpoints"></a><span data-ttu-id="9dc1b-144">删除所有断点</span><span class="sxs-lookup"><span data-stu-id="9dc1b-144">To Delete All Breakpoints</span></span>  
 <span data-ttu-id="9dc1b-145">**To delete all breakpoints**</span><span class="sxs-lookup"><span data-stu-id="9dc1b-145">**To delete all breakpoints**</span></span>  
  
 <span data-ttu-id="9dc1b-146">可以使用以下方式之一删除所有断点：</span><span class="sxs-lookup"><span data-stu-id="9dc1b-146">You can delete all breakpoints in one of the following ways:</span></span>  
  
-   <span data-ttu-id="9dc1b-147">在 **“调试”** 菜单上单击 **“删除所有断点”** 。</span><span class="sxs-lookup"><span data-stu-id="9dc1b-147">On the **Debug** menu, cllick **Delete All Breakpoints**.</span></span>  
  
-   <span data-ttu-id="9dc1b-148">在 **“断点”** 窗口的工具栏上，单击 **“删除所有断点”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="9dc1b-148">On the toolbar of the **Breakpoints** window, click the **Delete All Breakpoints** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dc1b-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9dc1b-149">See Also</span></span>  
 [<span data-ttu-id="9dc1b-150">切换断点</span><span class="sxs-lookup"><span data-stu-id="9dc1b-150">Toggle a Breakpoint</span></span>](../spatial/point.md)  
  
  
