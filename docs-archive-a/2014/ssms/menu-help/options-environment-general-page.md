---
title: 选项 (环境-常规页面) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.SQLEnvironmentOptions
ms.assetid: c32ccdb8-2cf8-4c78-b474-a3abd3dbbd13
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7712c568b478bd2ba958237ba3204246657b3a72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591709"
---
# <a name="options-environment-general-page"></a><span data-ttu-id="645b4-102">选项（“环境”-“常规”页）</span><span class="sxs-lookup"><span data-stu-id="645b4-102">Options (Environment-General Page)</span></span>
  <span data-ttu-id="645b4-103">使用“选项”  对话框可以配置 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 启动操作、常规窗口管理选项和其他常规设置。</span><span class="sxs-lookup"><span data-stu-id="645b4-103">Use the **Options** dialog box to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] startup actions, general window management options, and other general settings.</span></span> <span data-ttu-id="645b4-104">在“工具”  菜单上，单击“选项”  ，展开“环境”  文件夹，再单击“常规”  。</span><span class="sxs-lookup"><span data-stu-id="645b4-104">On the **Tools** menu, click **Options**, expand the **Environment** folder, and then click **General**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="645b4-105">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="645b4-105">UI element list</span></span>  
 <span data-ttu-id="645b4-106">**启动时**</span><span class="sxs-lookup"><span data-stu-id="645b4-106">**At startup**</span></span>  
 <span data-ttu-id="645b4-107">选择 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在启动时执行的操作。</span><span class="sxs-lookup"><span data-stu-id="645b4-107">Select the action for [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to perform when it is started.</span></span> <span data-ttu-id="645b4-108">选项包括：</span><span class="sxs-lookup"><span data-stu-id="645b4-108">The options are:</span></span>  
  
-   <span data-ttu-id="645b4-109">“打开对象资源管理器”  ，如果选择此选项，将在启动时提示输入连接信息，然后打开对象资源管理器。</span><span class="sxs-lookup"><span data-stu-id="645b4-109">**Open Object Explorer** prompts for a connection and then opens Object Explorer.</span></span>  
  
-   <span data-ttu-id="645b4-110">“打开新查询窗口”  ，如果选择此选项，将在启动时提示输入连接信息，然后打开 SQL 查询编辑器。</span><span class="sxs-lookup"><span data-stu-id="645b4-110">**Open new query window** prompts for a connection and then opens SQL Query Editor.</span></span>  
  
-   <span data-ttu-id="645b4-111">“打开对象资源管理器和新查询”\*\*\*\*，如果选择此选项，将在启动时提示输入连接信息，然后利用该连接打开对象资源管理器和 SQL 查询编辑器。</span><span class="sxs-lookup"><span data-stu-id="645b4-111">**Open Object Explorer and new query** prompts for a connection, then opens both Object Explorer and SQL Query Editor with that connection.</span></span>  
  
-   <span data-ttu-id="645b4-112">“打开空环境”  ，如果选择此选项，将在启动时打开 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，但不打开 SQL 查询编辑器窗口，并且不会将对象资源管理器连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="645b4-112">**Open empty environment** opens [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] without a SQL Query editor window and without connecting Object Explorer to a server.</span></span>  
  
 <span data-ttu-id="645b4-113">**在对象资源管理器中隐藏系统对象**</span><span class="sxs-lookup"><span data-stu-id="645b4-113">**Hide system objects in Object Explorer**</span></span>  
 <span data-ttu-id="645b4-114">如果选中此复选框，将从对象资源管理器内的树视图中删除系统数据库、系统表、系统视图和系统存储过程。</span><span class="sxs-lookup"><span data-stu-id="645b4-114">Select this check box to remove the system databases, system tables, system views, and system stored procedures from tree view in Object Explorer.</span></span> <span data-ttu-id="645b4-115">系统函数和系统数据类型将不隐藏。</span><span class="sxs-lookup"><span data-stu-id="645b4-115">System functions and system data types are not hidden.</span></span> <span data-ttu-id="645b4-116">此选项仅适用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例，并且不会影响对象资源管理器中已连接的服务器。</span><span class="sxs-lookup"><span data-stu-id="645b4-116">This option only applies to instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and does not affect servers already connected in Object Explorer.</span></span>  
  
## <a name="environment-layout"></a><span data-ttu-id="645b4-117">环境布局</span><span class="sxs-lookup"><span data-stu-id="645b4-117">Environment Layout</span></span>  
 <span data-ttu-id="645b4-118">您必须关闭并重新打开 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，才能在选项卡式文档和多文档界面 (MDI) 环境模式之间切换。</span><span class="sxs-lookup"><span data-stu-id="645b4-118">You must close and reopen [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to change between tabbed document and multiple-document interface (MDI) environment mode.</span></span>  
  
 <span data-ttu-id="645b4-119">**选项卡式文档**</span><span class="sxs-lookup"><span data-stu-id="645b4-119">**Tabbed documents**</span></span>  
 <span data-ttu-id="645b4-120">如果选择此选项，文档窗口将在编辑器内以选项卡形式显示在一起。</span><span class="sxs-lookup"><span data-stu-id="645b4-120">Select this option to display document windows that are tabbed together within editors.</span></span> <span data-ttu-id="645b4-121">在多个打开的文档之间进行组织和切换时，选项卡式文档窗口非常有用。</span><span class="sxs-lookup"><span data-stu-id="645b4-121">Tabbed document windows are useful for organizing and switching between multiple open documents.</span></span>  
  
 <span data-ttu-id="645b4-122">**MDI 环境**</span><span class="sxs-lookup"><span data-stu-id="645b4-122">**MDI environment**</span></span>  
 <span data-ttu-id="645b4-123">选择此选项将在 MDI 环境中打开文档。</span><span class="sxs-lookup"><span data-stu-id="645b4-123">Select this option to open documents in a MDI environment.</span></span> <span data-ttu-id="645b4-124">使用 MDI 文档窗口对于节省屏幕空间非常有用，而在选项卡式文档环境下，其中的选项卡会占用这些屏幕空间。</span><span class="sxs-lookup"><span data-stu-id="645b4-124">MDI document windows are useful for gaining the screen space that is otherwise taken up by the tabs in the tabbed documents environment.</span></span> <span data-ttu-id="645b4-125">在 MDI 模式下，可以通过按 Ctrl+Tab 在文档之间进行切换，也可以使用“窗口”\*\*\*\* 菜单上的磁贴选项。</span><span class="sxs-lookup"><span data-stu-id="645b4-125">When working in MDI mode, you can switch between documents by pressing CTRL+TAB, or you can use the tile options located on the **Window** menu.</span></span>  
  
## <a name="docked-tool-window-behavior"></a><span data-ttu-id="645b4-126">停靠工具窗口行为</span><span class="sxs-lookup"><span data-stu-id="645b4-126">Docked Tool Window Behavior</span></span>  
 <span data-ttu-id="645b4-127">**“关闭”按钮只影响活动选项卡**</span><span class="sxs-lookup"><span data-stu-id="645b4-127">**Close button affects active tab only**</span></span>  
 <span data-ttu-id="645b4-128">指定在选中此复选框时，仅关闭当前具有焦点的工具窗口，而非关闭停靠的所有工具窗口。</span><span class="sxs-lookup"><span data-stu-id="645b4-128">Specifies that when this check box is selected, only the tool window that has focus currently is closed and not all of the tool windows in the docked set.</span></span> <span data-ttu-id="645b4-129">默认情况下，此复选框处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="645b4-129">By default, this check box is selected.</span></span>  
  
 <span data-ttu-id="645b4-130">**“自动隐藏”按钮只影响活动选项卡**</span><span class="sxs-lookup"><span data-stu-id="645b4-130">**Auto Hide button affects active tab only**</span></span>  
 <span data-ttu-id="645b4-131">指定在选中此复选框时，仅自动隐藏当前具有焦点的工具窗口，而非自动隐藏停靠的所有工具窗口。</span><span class="sxs-lookup"><span data-stu-id="645b4-131">Specifies that when this check box is selected, only the tool window that has focus currently is hidden automatically, not all of the tool windows in the docked set.</span></span> <span data-ttu-id="645b4-132">默认情况下，此复选框处于未选中状态。</span><span class="sxs-lookup"><span data-stu-id="645b4-132">By default, this check box is cleared.</span></span>  
  
## <a name="display"></a><span data-ttu-id="645b4-133">显示</span><span class="sxs-lookup"><span data-stu-id="645b4-133">Display</span></span>  
 <span data-ttu-id="645b4-134">**显示 n 个文件(在最近使用的列表中)**</span><span class="sxs-lookup"><span data-stu-id="645b4-134">**Display n files in recently used list**</span></span>  
 <span data-ttu-id="645b4-135">自定义“文件”\*\*\*\* 菜单上显示的最近所使用项目和文件的数量。</span><span class="sxs-lookup"><span data-stu-id="645b4-135">Customizes the number of recent projects and recent files that appear on the **File** menu.</span></span> <span data-ttu-id="645b4-136">键入一个介于 1 和 24 之间的数字。</span><span class="sxs-lookup"><span data-stu-id="645b4-136">Type a number between 1 and 24.</span></span> <span data-ttu-id="645b4-137">默认值为 4。</span><span class="sxs-lookup"><span data-stu-id="645b4-137">The default is 4.</span></span> <span data-ttu-id="645b4-138">通过此方法可以轻松地检索最近使用的脚本项目和文件。</span><span class="sxs-lookup"><span data-stu-id="645b4-138">This is an easy way to retrieve recently used script projects and files and script projects.</span></span>  
  
  
