---
title: 管理编辑器和视图模式
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Query Editor [SQL Server Management Studio], managing window behavior
- workbench view modes [SQL Server Management Studio]
- full screen mode [SQL Server Management Studio]
- fonts [SQL Server Management Studio]
- word wraps [SQL Server Management Studio]
- virtual space mode [SQL Server Management Studio]
- splitting document views
- displaying line numbers
- view modes [SQL Server Management Studio]
ms.assetid: 25c58a14-9f94-4296-9770-7d84c6bc3969
author: rothja
ms.author: jroth
ms.openlocfilehash: 36788b1fe831a6c15c4aa0668d1759c088fcaa73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590164"
---
# <a name="manage-the-editor-and-view-mode"></a><span data-ttu-id="ad0cd-102">管理编辑器和视图模式</span><span class="sxs-lookup"><span data-stu-id="ad0cd-102">Manage the Editor and View Mode</span></span>
  <span data-ttu-id="ad0cd-103">利用编辑器，您可以通过多种方法来控制代码视图。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-103">The Editor gives you a number of ways to control the view of your code.</span></span>  
  
## <a name="changing-the-view-mode"></a><span data-ttu-id="ad0cd-104">更改视图模式</span><span class="sxs-lookup"><span data-stu-id="ad0cd-104">Changing the View Mode</span></span>  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="ad0cd-105">提供了一种名为 **“选项卡式文档”** 的视图模式。通过这种视图模式，您可以同时打开多个编辑器和文档，并通过编辑器顶部的选项卡来对其进行访问。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-105">features a view mode called **Tabbed Documents**, which allows you to open multiple editors and documents simultaneously and access them through tabs at the top of the Editor.</span></span> <span data-ttu-id="ad0cd-106">另外，您也可以在多文档界面 (MDI) 模式下打开 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 环境，这种模式将不带选项卡的窗口联接起来，并允许对每个窗口执行平铺、最小化等操作。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-106">You can alternatively open the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] environment in Multiple Document Interface (MDI) mode, which joins windows without the tabs, and allows each window to be tiled, minimized, and so on.</span></span>  
  
#### <a name="to-switch-between-view-modes"></a><span data-ttu-id="ad0cd-107">切换视图模式</span><span class="sxs-lookup"><span data-stu-id="ad0cd-107">To switch between view modes</span></span>  
  
1.  <span data-ttu-id="ad0cd-108">在 **“工具”** 菜单上单击 **“选项”** 。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-108">Click **Options** on the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="ad0cd-109">单击 **“环境”** 。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-109">Click **Environment**.</span></span> <span data-ttu-id="ad0cd-110">单击 **“常规”** 。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-110">Click **General**.</span></span>  
  
3.  <span data-ttu-id="ad0cd-111">单击 **“选项卡式文档”** 或 **“MDI 环境”** 。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-111">Click **Tabbed documents** or **MDI environment**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ad0cd-112">直到重新启动 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 时，更改才会生效。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-112">The changes will not take effect until [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is restarted.</span></span>  
  
## <a name="splitting-the-view"></a><span data-ttu-id="ad0cd-113">拆分视图</span><span class="sxs-lookup"><span data-stu-id="ad0cd-113">Splitting the View</span></span>  
 <span data-ttu-id="ad0cd-114">为了便于编辑，可以将“编辑器”窗口拆分为两个单独的部分。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-114">An Editor window can be split into two separate parts for easier editing.</span></span>  
  
#### <a name="to-split-a-window"></a><span data-ttu-id="ad0cd-115">拆分窗口</span><span class="sxs-lookup"><span data-stu-id="ad0cd-115">To split a window</span></span>  
  
1.  <span data-ttu-id="ad0cd-116">单击拆分栏（位于滚动条的上方）。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-116">Click the splitter bar (located above the scroll bar).</span></span>  
  
2.  <span data-ttu-id="ad0cd-117">向下拖动拆分栏。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-117">Drag the splitter bar downward.</span></span>  
  
3.  <span data-ttu-id="ad0cd-118">若要恢复到单一窗格，可双击分隔两窗格的拆分栏。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-118">To go back to a single pane, double-click the splitter bar dividing the two panes.</span></span>  
  
 <span data-ttu-id="ad0cd-119">新窗格中包含与旧窗格相同的文档，只要两个窗格显示的是文档中的同一位置，则对一个窗格所做的任何更改都会反映到另一个窗格中。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-119">The new pane contains the same document, and any changes made to one pane are reflected in the other pane as long as that pane displays the same place in the document.</span></span>  
  
## <a name="word-wrap"></a><span data-ttu-id="ad0cd-120">自动换行</span><span class="sxs-lookup"><span data-stu-id="ad0cd-120">Word Wrap</span></span>  
 <span data-ttu-id="ad0cd-121">激活自动换行功能时，水平滚动条将消失，且当代码行的长度超过编辑器的窗口宽度时，会自动转到下一个显示行，而不会滚动到窗口之外。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-121">When you activate Word Wrap, the horizontal scrollbar is removed and lines of code that exceed the width of the Editor's window size automatically wraps to the next displayed line rather than scrolling off the side of the window.</span></span>  
  
#### <a name="to-activate-word-wrap"></a><span data-ttu-id="ad0cd-122">激活自动换行功能</span><span class="sxs-lookup"><span data-stu-id="ad0cd-122">To activate word wrap</span></span>  
  
1.  <span data-ttu-id="ad0cd-123">在 **“工具”** 菜单上单击 **“选项”** 。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-123">Click **Options** on the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="ad0cd-124">单击 **“文本编辑器”** 。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-124">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="ad0cd-125">打开相应的语言文件夹（或打开“所有语言”  以使操作对所有语言生效）。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-125">Open the appropriate language folder (or **All Languages** to affect all languages).</span></span>  
  
4.  <span data-ttu-id="ad0cd-126">选择 **“自动换行”** 。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-126">Select **Word wrap**.</span></span>  
  
## <a name="enabling-virtual-space-mode"></a><span data-ttu-id="ad0cd-127">启用虚拟空间模式</span><span class="sxs-lookup"><span data-stu-id="ad0cd-127">Enabling Virtual Space Mode</span></span>  
 <span data-ttu-id="ad0cd-128">在 **“虚拟空间”** 模式下，编辑器看起来就像在每行末尾都包含无数的空间，这样，代码行的长度就可以超出屏幕可视区域的范围。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-128">In **Virtual Space** mode, the Editor acts as if the space past the end of each line is filled with an infinite number of spaces, allowing code lines to continue off the side of the visible screen area.</span></span>  
  
#### <a name="to-enable-virtual-space-mode"></a><span data-ttu-id="ad0cd-129">启用虚拟空间模式</span><span class="sxs-lookup"><span data-stu-id="ad0cd-129">To enable Virtual Space mode</span></span>  
  
1.  <span data-ttu-id="ad0cd-130">在 **“工具”** 菜单上单击 **“选项”** 。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-130">Click **Options** on the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="ad0cd-131">单击 **“文本编辑器”** 。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-131">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="ad0cd-132">打开相应的语言文件夹（或打开“所有语言”  以使操作对所有语言生效）。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-132">Open the appropriate language folder (or **All Languages** to affect all languages).</span></span>  
  
4.  <span data-ttu-id="ad0cd-133">选择 **“启用虚拟空间”** 。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-133">Select **Enable virtual space**.</span></span>  
  
 <span data-ttu-id="ad0cd-134">如果未启用虚拟空间模式，则光标会在到达一行的结尾时转到下一行的第一个字符（或相反）。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-134">When Virtual Space mode is not enabled, the cursor wraps from the end of one line to the first character of the next line and vice-versa.</span></span>  
  
## <a name="displaying-line-numbers"></a><span data-ttu-id="ad0cd-135">显示行号</span><span class="sxs-lookup"><span data-stu-id="ad0cd-135">Displaying Line Numbers</span></span>  
 <span data-ttu-id="ad0cd-136">您可以在代码中打开编号功能。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-136">You can turn on line numbering in your code.</span></span> <span data-ttu-id="ad0cd-137">行号在代码定位时非常有用。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-137">Line numbers are useful for navigating code.</span></span> <span data-ttu-id="ad0cd-138">有关详细信息，请参阅 [导航代码和文本](navigate-code-and-text.md)。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-138">For more information, see [Navigate Code and Text](navigate-code-and-text.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ad0cd-139">打开编号功能并不意味着在打印文档时会打印行号。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-139">Turning on line numbering does not mean that the document will print with line numbers.</span></span> <span data-ttu-id="ad0cd-140">若要打印行号，则必须在 **“文件”** 菜单上的 **“页面设置”** 命令中选中 **“行号”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-140">For line numbers to print, you must select the **Line numbers** check box in the **Page Setup** command on the **File** menu.</span></span>  
  
#### <a name="to-display-line-numbers-in-code"></a><span data-ttu-id="ad0cd-141">在代码中显示行号</span><span class="sxs-lookup"><span data-stu-id="ad0cd-141">To display line numbers in code</span></span>  
  
1.  <span data-ttu-id="ad0cd-142">在 **“工具”** 菜单上单击 **“选项”** 。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-142">Click **Options** on the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="ad0cd-143">单击 **“文本编辑器”** 。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-143">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="ad0cd-144">单击 **“所有语言”** 。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-144">Click **All Languages**.</span></span>  
  
4.  <span data-ttu-id="ad0cd-145">单击 **“常规”** 。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-145">Click **General**.</span></span>  
  
5.  <span data-ttu-id="ad0cd-146">选择 **“行号”** 。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-146">Select **Line numbers**.</span></span>  
  
 <span data-ttu-id="ad0cd-147">若仅为某些编程语言指定编号，则可在相应文件夹中选择 **“行号”** 。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-147">To specify line numbering for only some programming languages, select **Line Numbers** in the appropriate folder.</span></span>  
  
## <a name="enabling-full-screen-mode"></a><span data-ttu-id="ad0cd-148">启用全屏显示模式</span><span class="sxs-lookup"><span data-stu-id="ad0cd-148">Enabling Full Screen Mode</span></span>  
 <span data-ttu-id="ad0cd-149">通过启用全屏显示模式，可以选择隐藏所有工具窗口，而只查看文档窗口。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-149">You can choose to hide all tool windows and view only document windows by enabling Full Screen mode.</span></span>  
  
#### <a name="to-enable-full-screen-mode"></a><span data-ttu-id="ad0cd-150">启用全屏显示模式</span><span class="sxs-lookup"><span data-stu-id="ad0cd-150">To enable Full Screen mode</span></span>  
  
1.  <span data-ttu-id="ad0cd-151">按 Alt+Shift+Enter 可切换到全屏显示模式。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-151">Press ALT+SHIFT+ENTER to toggle Full Screen mode.</span></span>  
  
## <a name="using-auto-hide-all"></a><span data-ttu-id="ad0cd-152">使用“全部自动隐藏”</span><span class="sxs-lookup"><span data-stu-id="ad0cd-152">Using Auto Hide All</span></span>  
  
#### <a name="to-hide-all-the-tool-windows-at-once"></a><span data-ttu-id="ad0cd-153">同时隐藏所有工具窗口</span><span class="sxs-lookup"><span data-stu-id="ad0cd-153">To hide all the tool windows at once</span></span>  
  
1.  <span data-ttu-id="ad0cd-154">选择 **“窗口”** 菜单上的 **“全部自动隐藏”** 。</span><span class="sxs-lookup"><span data-stu-id="ad0cd-154">Select **Auto Hide All** on the **Window** menu.</span></span>  
  
  
